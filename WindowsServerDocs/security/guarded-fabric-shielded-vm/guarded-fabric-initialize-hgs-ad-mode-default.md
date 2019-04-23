---
title: Инициализировать кластер HGS, используя режим AD из нового выделенного леса (по умолчанию)
ms.custom: na
ms.prod: windows-server-threshold
ms.topic: article
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 4ef70ab9ce8150a9a3ed774d6df407da097880e9
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59865675"
---
# <a name="initialize-the-hgs-cluster-using-ad-mode-in-a-new-dedicated-forest-default"></a>Инициализировать кластер HGS, используя режим AD из нового выделенного леса (по умолчанию)

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

>[!IMPORTANT]
>Аттестацию с доверием администратора (режим AD) является устаревшим, начиная с Windows Server 2019. Для сред, где аттестацию доверенного платформенного МОДУЛЯ не поддерживается, Настройка [размещения Аттестация ключей](guarded-fabric-initialize-hgs-key-mode-default.md). Аттестация ключей узла обеспечивает аналогичный уверенность в режим AD и проще в настройке. 

1.  [!INCLUDE [Initialize HGS](../../../includes/guarded-fabric-initialize-hgs-default-step-one.md)] 
2.  [!INCLUDE [Obtain certificates for HGS](../../../includes/guarded-fabric-initialize-hgs-default-step-two.md)]

3.  Запустите [Initialize HgsServer](https://technet.microsoft.com/library/mt652185.aspx) в окне PowerShell с повышенными правами на первом узле HGS. Синтаксис этого командлета поддерживает множество различных входных данных, но 2 наиболее распространенные вызовы методов приведены ниже:

    -   Если вы используете PFX-файлов для сертификатов подписывания и шифрования, выполните следующие команды:

        ```powershell
        $signingCertPass = Read-Host -AsSecureString -Prompt "Signing certificate password"
        $encryptionCertPass = Read-Host -AsSecureString -Prompt "Encryption certificate password"

        Initialize-HgsServer -HgsServiceName 'MyHgsDNN' -SigningCertificatePath '.\signCert.pfx' -SigningCertificatePassword $signingCertPass -EncryptionCertificatePath '.\encCert.pfx' -EncryptionCertificatePassword $encryptionCertPass -TrustActiveDirectory
        ```

    -   Если вы используете не экспортируются сертификаты, установленные в локальном хранилище сертификатов, выполните следующую команду. Если вы не знаете отпечатки сертификатов, вы можете разместить доступных сертификатов, выполнив `Get-ChildItem Cert:\LocalMachine\My`.

        ```powershell
        Initialize-HgsServer -HgsServiceName 'MyHgsDNN' -SigningCertificateThumbprint '1A2B3C4D5E6F...' -EncryptionCertificateThumbprint '0F9E8D7C6B5A...' --TrustActiveDirectory
        ```

4.  [!INCLUDE [Initialize HGS](../../../includes/guarded-fabric-initialize-hgs-default-step-four.md)]  

5.  [!INCLUDE [Initialize HGS](../../../includes/guarded-fabric-initialize-hgs-default-step-five.md)]

## <a name="next-step"></a>Дальнейшие действия

>[!div class="nextstepaction"]
[Настройка фабрики DNS](guarded-fabric-configuring-fabric-dns-ad.md)