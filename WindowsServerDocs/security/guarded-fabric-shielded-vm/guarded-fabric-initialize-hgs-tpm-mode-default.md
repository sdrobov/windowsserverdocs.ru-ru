---
title: Инициализировать кластер HGS, использующий режим доверенного платформенного МОДУЛЯ на нового выделенного леса (по умолчанию)
ms.custom: na
ms.prod: windows-server-threshold
ms.topic: article
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 6d4232b0b248aba8b64f31ac28db1480c14db53d
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59863875"
---
# <a name="initialize-the-hgs-cluster-using-tpm-mode-in-a-new-dedicated-forest-default"></a>Инициализировать кластер HGS, использующий режим доверенного платформенного МОДУЛЯ на нового выделенного леса (по умолчанию)

>Относится к: Windows Server 2019 г., Windows Server (полугодовой канал), Windows Server 2016

1.  [!INCLUDE [Initialize HGS](../../../includes/guarded-fabric-initialize-hgs-default-step-one.md)]

2.  [!INCLUDE [Obtain certificates for HGS](../../../includes/guarded-fabric-initialize-hgs-default-step-two.md)]

3.  Запустите [Initialize HgsServer](https://technet.microsoft.com/library/mt652185.aspx) в окне PowerShell с повышенными правами на первом узле HGS. Синтаксис этого командлета поддерживает множество различных входных данных, но 2 наиболее распространенные вызовы методов приведены ниже:

    -   Если вы используете PFX-файлов для сертификатов подписывания и шифрования, выполните следующие команды:

        ```powershell
        $signingCertPass = Read-Host -AsSecureString -Prompt "Signing certificate password"
        $encryptionCertPass = Read-Host -AsSecureString -Prompt "Encryption certificate password"

        Initialize-HgsServer -HgsServiceName 'MyHgsDNN' -SigningCertificatePath '.\signCert.pfx' -SigningCertificatePassword $signingCertPass -EncryptionCertificatePath '.\encCert.pfx' -EncryptionCertificatePassword $encryptionCertPass -TrustTpm
        ```

    -   Если вы используете не экспортируются сертификаты, установленные в локальном хранилище сертификатов, выполните следующую команду. Если вы не знаете отпечатки сертификатов, вы можете разместить доступных сертификатов, выполнив `Get-ChildItem Cert:\LocalMachine\My`.

        ```powershell
        Initialize-HgsServer -HgsServiceName 'MyHgsDNN' -SigningCertificateThumbprint '1A2B3C4D5E6F...' -EncryptionCertificateThumbprint '0F9E8D7C6B5A...' -TrustTpm
        ```

4.  [!INCLUDE [Initialize HGS](../../../includes/guarded-fabric-initialize-hgs-default-step-four.md)]

5.  [!INCLUDE [Initialize HGS](../../../includes/guarded-fabric-initialize-hgs-default-step-five.md)]

## <a name="next-step"></a>Дальнейшие действия

>[!div class="nextstepaction"]
[Установить корневые сертификаты доверенного платформенного МОДУЛЯ](guarded-fabric-install-trusted-tpm-root-certificates.md)
  