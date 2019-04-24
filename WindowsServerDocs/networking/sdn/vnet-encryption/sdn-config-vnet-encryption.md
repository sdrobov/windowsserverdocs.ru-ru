---
title: Настройка шифрования для виртуальной сети
description: Шифрование виртуальной сети, обеспечивает шифрование трафика виртуальной сети между виртуальными машинами, которые взаимодействуют друг с другом в пределах подсетей с пометкой «Шифрование включено».
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking-hv-switch
ms.topic: get-started-article
ms.assetid: 378213f5-2d59-4c9b-9607-1fc83f8072f1
ms.author: pashort
author: shortpatti
ms.date: 08/08/2018
ms.openlocfilehash: 90fb33eb4c4b63fdd5c84bf3ffc2447fd52a809b
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59845495"
---
# <a name="configure-encryption-for-a-virtual-subnet"></a>Настройка шифрования для виртуальной подсети

>Относится к: Windows Server

Позволяет виртуальной сети шифрования для шифрования трафика виртуальной сети между виртуальными машинами, которые взаимодействуют друг с другом в пределах подсетей с пометкой «Шифрование включено». Для шифрования пакетов с помощью этой возможности также используется протокол DTLS в виртуальной подсети. Протокол DTLS обеспечивает защиту от перехвата, несанкционированных изменений и подделки со стороны любых лиц, имеющих доступ к физической сети.

Требует шифрования виртуальной сети:
- Сертификаты шифрования, который установлен на каждом узле Hyper-V, поддержкой SDN.
- Объект учетных данных в сетевом контроллере, ссылающиеся на отпечаток этого сертификата.
- Конфигурация на всех виртуальных сетей содержит подсети, когда требуется шифрование.

После включения шифрования в подсети, весь сетевой трафик в одной из подсетей шифруется автоматически, в дополнение к какого-либо шифрования уровня приложения, который также может иметь место.  Трафик, который пересекает между подсетями, даже если зашифрованной, автоматически отправляется незашифрованным. Любой трафик, который пересекает границу виртуальной сети также получает отправляются в незашифрованном виде.

>[!NOTE]
>При взаимодействии с другой виртуальной Машине в той же подсети, ли его в настоящее время подключен или подключенных в дальнейшем, трафик данные шифруются автоматически.

>[!TIP]
>Если необходимо ограничить приложениям взаимодействовать только зашифрованные подсети, можно использовать списки управления доступом (ACL) только для того, чтобы разрешить обмен данными в пределах текущей подсети. Дополнительные сведения см. в разделе [используйте списки управления доступом (ACL) для управления центра обработки данных сети трафик проходит](https://docs.microsoft.com/windows-server/networking/sdn/manage/use-acls-for-traffic-flow).


## <a name="step-1-create-the-encryption-certificate"></a>Шаг 1. Создать сертификат шифрования
Каждом узле должен быть установлен сертификат шифрования. Можно использовать один сертификат для всех клиентов или создать уникальный элемент для каждого клиента. 

1.  Создание сертификата  

```
    $subjectName = "EncryptedVirtualNetworks"
    $cryptographicProviderName = "Microsoft Base Cryptographic Provider v1.0";
    [int] $privateKeyLength = 1024;
    $sslServerOidString = "1.3.6.1.5.5.7.3.1";
    $sslClientOidString = "1.3.6.1.5.5.7.3.2";
    [int] $validityPeriodInYear = 5;

    $name = new-object -com "X509Enrollment.CX500DistinguishedName.1"
    $name.Encode("CN=" + $SubjectName, 0)

    #Generate Key
    $key = new-object -com "X509Enrollment.CX509PrivateKey.1"
    $key.ProviderName = $cryptographicProviderName
    $key.KeySpec = 1 #X509KeySpec.XCN_AT_KEYEXCHANGE
    $key.Length = $privateKeyLength
    $key.MachineContext = 1
    $key.ExportPolicy = 0x2 #X509PrivateKeyExportFlags.XCN_NCRYPT_ALLOW_EXPORT_FLAG 
    $key.Create()

    #Configure Eku
    $serverauthoid = new-object -com "X509Enrollment.CObjectId.1"
    $serverauthoid.InitializeFromValue($sslServerOidString)
    $clientauthoid = new-object -com "X509Enrollment.CObjectId.1"
    $clientauthoid.InitializeFromValue($sslClientOidString)
    $ekuoids = new-object -com "X509Enrollment.CObjectIds.1"
    $ekuoids.add($serverauthoid)
    $ekuoids.add($clientauthoid)
    $ekuext = new-object -com "X509Enrollment.CX509ExtensionEnhancedKeyUsage.1"
    $ekuext.InitializeEncode($ekuoids)

    # Set the hash algorithm to sha512 instead of the default sha1
    $hashAlgorithmObject = New-Object -ComObject X509Enrollment.CObjectId
    $hashAlgorithmObject.InitializeFromAlgorithmName( $ObjectIdGroupId.XCN_CRYPT_HASH_ALG_OID_GROUP_ID, $ObjectIdPublicKeyFlags.XCN_CRYPT_OID_INFO_PUBKEY_ANY, $AlgorithmFlags.AlgorithmFlagsNone, "SHA512")


    #Request Certificate
    $cert = new-object -com "X509Enrollment.CX509CertificateRequestCertificate.1"

    $cert.InitializeFromPrivateKey(2, $key, "")
    $cert.Subject = $name
    $cert.Issuer = $cert.Subject
    $cert.NotBefore = (get-date).ToUniversalTime()
    $cert.NotAfter = $cert.NotBefore.AddYears($validityPeriodInYear);
    $cert.X509Extensions.Add($ekuext)
    $cert.HashAlgorithm = $hashAlgorithmObject
    $cert.Encode()

    $enrollment = new-object -com "X509Enrollment.CX509Enrollment.1"
    $enrollment.InitializeFromRequest($cert)
    $certdata = $enrollment.CreateRequest(0)
    $enrollment.InstallResponse(2, $certdata, 0, "")
```

После выполнения сценария появится новый сертификат в хранилище My:

    PS D:\> dir cert:\\localmachine\my


    PSParentPath: Microsoft.PowerShell.Security\Certificate::localmachine\my

    Thumbprint                                Subject
    ----------                                -------
    84857CBBE7A1C851A80AE22391EB2C39BF820CE7  CN=MyNetwork
    5EFF2CE51EACA82408572A56AE1A9BCC7E0843C6  CN=EncryptedVirtualNetworks

2.  Экспортируйте сертификат в файл.<p>Вам потребуется две копии сертификата: с закрытым ключом и без.

    $subjectName = "EncryptedVirtualNetworks" $cert = Get-ChildItem cert:\localmachine\my | ? {$_.Subject -eq "CN=$subjectName"} [System.io.file]::WriteAllBytes("c:\$subjectName.pfx", $cert.Export("PFX", "secret")) Export-Certificate -Type CERT -FilePath "c:\$subjectName.cer" -cert $cert

3.  Установка сертификатов на каждом из узлов hyper-v 

    PS C:\> dir c:\$subjectname.*


        Directory: C:\


    Имя режима LastWriteTime длина
    ----                -------------         ------ ----
    -a---9/22/2017 4:54 PM 543 EncryptedVirtualNetworks.cer ----EncryptedVirtualNetworks.pfx 1706 до 54 16:9 / 22/2017

4.  Установка на узле Hyper-V

    $server = "Server01"

    $subjectname = «EncryptedVirtualNetworks» c: копирования\$SubjectName.* \\$server\c$ invoke-command - computername $server - ArgumentList $subjectname, «секрет» {param ([string] $SubjectName, [string] $Secret) $certFullPath = «c: \$SubjectName.cer»

        # create a representation of the certificate file
        $certificate = new-object System.Security.Cryptography.X509Certificates.X509Certificate2
        $certificate.import($certFullPath)

        # import into the store
        $store = new-object System.Security.Cryptography.X509Certificates.X509Store("Root", "LocalMachine")
        $store.open("MaxAllowed")
        $store.add($certificate)
        $store.close()

        $certFullPath = "c:\$SubjectName.pfx"
        $certificate = new-object System.Security.Cryptography.X509Certificates.X509Certificate2
        $certificate.import($certFullPath, $Secret, "MachineKeySet,PersistKeySet")

        # import into the store
        $store = new-object System.Security.Cryptography.X509Certificates.X509Store("My", "LocalMachine")
        $store.open("MaxAllowed")
        $store.add($certificate)
        $store.close()

        # Important: Remove the certificate files when finished
        remove-item C:\$SubjectName.cer
        remove-item C:\$SubjectName.pfx
    }    

5.  Повторите для каждого сервера в вашей среде.<p>После повторного для каждого сервера, вы получите сертификат, установленный в корне и личном хранилище каждого узла Hyper-V. 

6.  Проверьте установку сертификата.<p>Проверьте сертификаты, проверив содержимое моей и корневое хранилища:

    PS C:\> Server1, введите pssession

    [Server1]: PS C:\> cert://localmachine/my get-childitem, cert://localmachine/root |? {$_. Тема - eq «CN = EncryptedVirtualNetworks»}

    PSParentPath: Microsoft.PowerShell.Security\Certificate::localmachine\my

    Отпечаток субъекта
    ----------                                -------
    5EFF2CE51EACA82408572A56AE1A9BCC7E0843C6 CN = EncryptedVirtualNetworks


    PSParentPath: Microsoft.PowerShell.Security\Certificate::localmachine\root

    Отпечаток субъекта
    ----------                                -------
    5EFF2CE51EACA82408572A56AE1A9BCC7E0843C6 CN = EncryptedVirtualNetworks

7.  Запишите отпечаток.<p>Запишите отпечаток необходимо, так как он необходим для создания объекта учетных данных сертификата в сетевом контроллере.

## <a name="step-2-create-the-certificate-credential"></a>Шаг 2. Создать учетные данные сертификата

После установки сертификата на каждом из узлов Hyper-V, подключенных к сетевым контроллером, теперь необходимо настроить сетевого контроллера для его использования.  Чтобы сделать это, необходимо создать объект учетных данных, содержащий отпечаток сертификата на компьютере с помощью модулей сетевого контроллера PowerShell установлен. 


    # Replace with thumbprint from your certificate
    $thumbprint = "5EFF2CE51EACA82408572A56AE1A9BCC7E0843C6"  
    
    # Replace with your Network Controller URI
    $uri = "https://nc.contoso.com"

    Import-module networkcontroller
    
    $credproperties = new-object Microsoft.Windows.NetworkController.CredentialProperties
    $credproperties.Type = "X509Certificate"
    $credproperties.Value = $thumbprint
    New-networkcontrollercredential -connectionuri $uri -resourceid "EncryptedNetworkCertificate" -properties $credproperties -force

>[!TIP]
>Вы можете повторно использовать эти учетные данные для каждого зашифрованного виртуальной сети, или можно развернуть и использовать уникальный сертификат для каждого клиента.


## <a name="step-3-configuring-a-virtual-network-for-encryption"></a>Шаг 3. Настройка виртуальной сети для шифрования

Этот шаг предполагается, что вы уже создали имени виртуальной сети «Сетевое окружение», и она содержит по крайней мере одной виртуальной подсети.  Сведения о создании виртуальных сетей, см. в разделе [Create, Delete или Update виртуальных сетей клиентов](../Manage/Create,-Delete,-or-Update-Tenant-Virtual-Networks.md).

>[!NOTE]
>При взаимодействии с другой виртуальной Машине в той же подсети, ли его в настоящее время подключен или подключенных в дальнейшем, трафик данные шифруются автоматически.

1.  Извлеките объекты виртуальной сети и учетные данные из сетевого контроллера

    $vnet = get-NetworkControllerVirtualNetwork - ConnectionUri $uri - ResourceId «MyNetwork» $certcred = Get-NetworkControllerCredential - ConnectionUri $uri - ResourceId «EncryptedNetworkCertificate»

2.  Добавьте ссылку на учетные данные сертификата и включите шифрование для отдельных подсетей

    $vnet.properties.EncryptionCredential = $certcred

    # <a name="replace-the-subnets-index-with-the-value-corresponding-to-the-subnet-you-want-encrypted"></a>Замените значение, соответствующее подсети, к которой требуется зашифрованный индекс подсети.  
    # <a name="repeat-for-each-subnet-where-encryption-is-needed"></a>Повторите для каждой подсети, когда требуется шифрование
    $vnet.properties.Subnets[0].properties. EncryptionEnabled = $true

3.  Поместить обновленный объект виртуальной сети в сетевой контроллер

    New-NetworkControllerVirtualNetwork -ConnectionUri $uri -ResourceId $vnet.ResourceId -Properties $vnet.Properties -force


_**Поздравляю!**_ После выполнения этих действий все готово. 


## <a name="next-steps"></a>Следующие шаги



