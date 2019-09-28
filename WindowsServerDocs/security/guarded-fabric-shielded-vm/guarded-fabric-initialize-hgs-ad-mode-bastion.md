---
title: Инициализация кластера HGS с помощью режима AD в лесу бастиона
ms.custom: na
ms.prod: windows-server
ms.topic: article
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: c69561f7d17bb1d36d90fc66cf4c1a196072fc72
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71402367"
---
# <a name="initialize-the-hgs-cluster-using-ad-mode-in-an-existing-bastion-forest"></a>Инициализация кластера HGS с помощью режима AD в существующем лесу бастиона

>Относится к: Windows Server (Semi-Annual Channel), Windows Server 2016


>[!IMPORTANT]
>Служба аттестации, доверенная для администраторов (режим AD), устарела, начиная с Windows Server 2019. Для сред, в которых невозможно подтвердить аттестацию доверенного платформенного модуля, настройте [аттестацию ключа узла](guarded-fabric-initialize-hgs-key-mode-bastion.md). Аттестация ключа узла обеспечивает аналогичные гарантии в режиме AD и проще в настройке. 

Домен Active Directory службы будут установлены на компьютере, но должны остаться ненастроенными.

[!INCLUDE [Obtain certificates for HGS](../../../includes/guarded-fabric-initialize-hgs-default-step-two.md)] 

Прежде чем продолжить, убедитесь, что объекты кластера предварительно подготовлены для службы защиты узла и предоставил вошедшему в систему пользователю **полный контроль** над объектами VCO и CNO в Active Directory.
Имя объекта виртуального компьютера должно быть передано параметру `-HgsServiceName`, а имя кластера — параметру `-ClusterName`.

> [!TIP]
> Прежде чем продолжить, проверьте контроллеры доменов AD, чтобы убедиться, что объекты кластера реплицированы на все контроллеры домена.

Если вы используете сертификаты на основе PFX, выполните на сервере HGS следующие команды:

```powershell
$signingCertPass = Read-Host -AsSecureString -Prompt "Signing certificate password"
$encryptionCertPass = Read-Host -AsSecureString -Prompt "Encryption certificate password"

Install-ADServiceAccount -Identity 'HGSgMSA'

Initialize-HgsServer -UseExistingDomain -ServiceAccount 'HGSgMSA' -JeaReviewersGroup 'HgsJeaReviewers' -JeaAdministratorsGroup 'HgsJeaAdmins' -HgsServiceName 'HgsService' -ClusterName 'HgsCluster' -SigningCertificatePath '.\signCert.pfx' -SigningCertificatePassword $signPass -EncryptionCertificatePath '.\encCert.pfx' -EncryptionCertificatePassword $encryptionCertPass -TrustActiveDirectory
```

Если вы используете сертификаты, установленные на локальном компьютере (например, сертификаты с защитой от HSM и неэкспортируемые сертификаты), используйте параметры `-SigningCertificateThumbprint` и `-EncryptionCertificateThumbprint`.

## <a name="next-step"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Настройка DNS структуры](guarded-fabric-configuring-fabric-dns-ad.md)

