---
title: Создайте ключ узла и добавьте его к HGS
ms.custom: na
ms.prod: windows-server-threshold
ms.topic: article
ms.assetid: a12c8494-388c-4523-8d70-df9400bbc2c0
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 82a561d51e9a396dcdc86ee3e37a8d7ffb8efd6e
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59870785"
---
# <a name="create-a-host-key-and-add-it-to-hgs"></a>Создайте ключ узла и добавьте его к HGS

>Относится к: Windows Server 2019


В этом разделе описывается, как подготовить узлы Hyper-V в качестве защищенных узлов, с помощью аттестации ключей узла (ключ режим). Будет создание пары ключей узла (или использовать существующий сертификат) и добавьте открытый ключ HGS.

## <a name="create-a-host-key"></a>Создайте ключ узла

1.  Установите Windows Server 2019 на компьютере размещения Hyper-V.
2.  Установите компоненты Hyper-V и поддержку защиты узла Hyper-V:

    ```powershell
    Install-WindowsFeature Hyper-V, HostGuardian -IncludeManagementTools -Restart
    ``` 

3.  Автоматически создать ключ узла, или выбрать существующий сертификат. Если вы используете пользовательский сертификат, он должен иметь по крайней мере 2048-разрядный ключ RSA, EKU для проверки подлинности клиента и использования ключей цифровой подписи.

    ```powershell
    Set-HgsClientHostKey
    ```

    Кроме того можно указать отпечаток, если вы хотите использовать собственный сертификат. 
    Это может быть полезно в том случае, если вы хотите совместно использовать сертификат на нескольких компьютерах, или используйте сертификат, связанный с доверенным платформенным Модулем или аппаратный модуль безопасности. Ниже приведен пример создания сертификата привязкой доверенный платформенный модуль (который предотвращает его закрытый ключ украден и использован на другом компьютере и требуется только TPM 1.2):

    ```powershell
    $tpmBoundCert = New-SelfSignedCertificate -Subject “Host Key Attestation ($env:computername)” -Provider “Microsoft Platform Crypto Provider”
    Set-HgsClientHostKey -Thumbprint $tpmBoundCert.Thumbprint
    ```

4.  Получите общедоступную половину этого раздела, чтобы указать на сервер HGS. Можно использовать следующий командлет или, при наличии сертификата, хранящегося в другом месте, укажите CER-файл, содержащий открытое половина ключа. Обратите внимание, что мы только хранение и проверка открытого ключа HGS; Мы не сохранять никаких сведений о сертификате, ни мы проверяем Дата цепочки или истечения срока действия сертификата.

    ```powershell
    Get-HgsClientHostKey -Path "C:\temp\$env:hostname-HostKey.cer"
    ```

5.  Скопируйте CER-файл на сервер HGS.

## <a name="add-the-host-key-to-the-attestation-service"></a>Добавить ключ узла к службе аттестации

Этот шаг выполняется на сервере HGS и позволяет узлу для запуска экранированных виртуальных машин. Рекомендуется, что имя присвоено полное доменное имя или идентификатор ресурса для хост-компьютере, поэтому можно легко ссылаться на какие узлов ключ устанавливается на.

```powershell
Add-HgsAttestationHostKey -Name MyHost01 -Path "C:\temp\MyHost01-HostKey.cer"
``` 

## <a name="next-step"></a>Дальнейшие действия

>[!div class="nextstepaction"]
[Убедитесь, что узлы можно оценить, требуется ли успешно](guarded-fabric-confirm-hosts-can-attest-successfully.md)

## <a name="see-also"></a>См. также

- [Развертывание службы защиты узла для защищенных узлов и экранированных виртуальных машин](guarded-fabric-deploying-hgs-overview.md)
