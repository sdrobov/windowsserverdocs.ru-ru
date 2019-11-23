---
title: Подтверждение аттестации защищенных узлов
ms.custom: na
ms.prod: windows-server
ms.topic: article
ms.assetid: 7485796b-b840-4678-9b33-89e9710fbbc7
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 09/25/2019
ms.openlocfilehash: 2bab2b653127ae13d27dea76225ada91b3ee8ecc
ms.sourcegitcommit: de71970be7d81b95610a0977c12d456c3917c331
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/04/2019
ms.locfileid: "71940701"
---
# <a name="confirm-guarded-hosts-can-attest"></a>Подтверждение аттестации защищенных узлов

>Область применения: Windows Server 2019, Windows Server (половина ежегодного канала), Windows Server 2016

Администратор структуры должен подтвердить, что узлы Hyper-V могут работать как защищенные узлы. Выполните следующие действия по крайней мере на одном защищенном узле:

1. Если вы еще не установили роль Hyper-V и службу защиты узла Hyper-V, установите их с помощью следующей команды:

    ```powershell
    Install-WindowsFeature Hyper-V, HostGuardian -IncludeManagementTools -Restart
    ```

2. Убедитесь, что узел Hyper-V может разрешить DNS-имя HGS и сетевое подключение, чтобы получить доступ к порту 80 (или 443, если вы настроили HTTPS) на сервере HGS.

3. Настройте URL-адреса защиты ключа и аттестации узла:

    - С **помощью Windows PowerShell**: можно настроить URL-адреса защиты ключа и аттестации, выполнив следующую команду в консоли Windows PowerShell с повышенными привилегиями. Для &lt;полного доменного имени&gt;используйте полное доменное имя кластера HGS (например, HGS. бастиона. local) или попросите администратора HGS запустить командлет **Get-HgsServer** на сервере HGS для получения URL-адресов.

        ```PowerShell
        Set-HgsClientConfiguration -AttestationServerUrl 'http://<FQDN>/Attestation' -KeyProtectionServerUrl 'http://<FQDN>/KeyProtection'
         ```

        Чтобы настроить резервный сервер HGS, повторите эту команду и укажите резервные URL-адреса для служб защиты и аттестации ключей. Дополнительные сведения см. в разделе [резервная конфигурация](guarded-fabric-manage-branch-office.md#fallback-configuration).

    - С **помощью VMM**. Если вы используете System Center 2016-Virtual Machine Manager (VMM), вы можете настроить URL-адреса аттестации и защиты ключей в VMM. Дополнительные сведения см. в статье [Настройка глобальных параметров HGS](https://technet.microsoft.com/system-center-docs/vmm/scenario/guarded-hosts#configure-global-hgs-settings) в разделе **подготавливать защищенные узлы в VMM**.

    >**Примечания**
    > - Если администратор HGS [включил протокол HTTPS на сервере HGS](guarded-fabric-configure-hgs-https.md), начните использовать URL-адреса с `https://`.
    > - Если администратор HGS включил протокол HTTPS на сервере HGS и использовал самозаверяющий сертификат, необходимо импортировать сертификат в хранилище доверенных корневых центров сертификации на каждом узле. Для этого выполните следующую команду на каждом узле:
       ```PowerShell
       Import-Certificate -FilePath "C:\temp\HttpsCertificate.cer" -CertStoreLocation Cert:\LocalMachine\Root
       ```
    > - Если вы настроили клиент HGS для использования протокола HTTPS и отключили общедоступную конфигурацию TLS 1,0, ознакомьтесь с нашим [руководством по использованию современных протоколов TLS](guarded-fabric-troubleshoot-hosts.md#modern-tls) .

4. Чтобы инициировать попытку аттестации на узле и просмотреть состояние аттестации, выполните следующую команду:

    ```powershell
    Get-HgsClientConfiguration
    ```

    Выходные данные команды указывают, прошел ли узел аттестацию, и теперь он защищен. Если `IsHostGuarded` не возвращает **значение true**, для изучения можно запустить средство диагностики HGS с помощью [Get-хгстраце](https://technet.microsoft.com/library/mt718831.aspx). Чтобы запустить диагностику, введите следующую команду в командной строке Windows PowerShell с повышенными привилегиями на узле:

    ```powershell
    Get-HgsTrace -RunDiagnostics -Detailed
    ```

    > [!IMPORTANT]
    > Если вы используете Windows Server 2019 или Windows 10 версии 1809 и используете политики целостности кода, `Get-HgsTrace` возвращать ошибку для **активной диагностики политики целостности кода** .
    > Вы можете спокойно проигнорировать этот результат, если это единственный сбой диагностики.

## <a name="next-step"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Развертывание экранированных виртуальных машин](guarded-fabric-configuration-scenarios-for-shielded-vms-overview.md)

## <a name="see-also"></a>См. также

- [Развертывание службы защиты узла (HGS)](guarded-fabric-deploying-hgs-overview.md)
- [Развертывание экранированных виртуальных машин](guarded-fabric-configuration-scenarios-for-shielded-vms-overview.md)
