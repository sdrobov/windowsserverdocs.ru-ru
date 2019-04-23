---
title: Инициализировать кластер HGS, используя режим AD в лесу-бастионе
ms.custom: na
ms.prod: windows-server-threshold
ms.topic: article
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 98003745823cf780a38487dff997798ebef12fc9
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59870095"
---
# <a name="initialize-the-hgs-cluster-using-ad-mode-in-an-existing-bastion-forest"></a>Инициализировать кластер HGS, режиме AD в существующем лесу бастиона

>Относится к: Windows Server (полугодовой канал), Windows Server 2016


>[!IMPORTANT]
>Аттестацию с доверием администратора (режим AD) является устаревшим, начиная с Windows Server 2019. Для сред, где аттестацию доверенного платформенного МОДУЛЯ не поддерживается, Настройка [размещения Аттестация ключей](guarded-fabric-initialize-hgs-key-mode-bastion.md). Аттестация ключей узла обеспечивает аналогичный уверенность в режим AD и проще в настройке. 

Доменные службы Active Directory устанавливается на компьютере, но должны оставаться ненастроенный.

[!INCLUDE [Obtain certificates for HGS](../../../includes/guarded-fabric-initialize-hgs-default-step-two.md)] 

Прежде чем продолжить, убедитесь, что предварительно подготовленного кластера объектов для службы защиты узла и вошедшего пользователя предоставлены **полный контроль** над объектами VCO и CNO в Active Directory.
Имя объекта виртуального компьютера необходимо передать для `-HgsServiceName` параметра и имя кластера, чтобы `-ClusterName` параметра.

> [!TIP]
> Внимательно проверьте контроллеров домена AD, чтобы обеспечить объектов кластера были реплицированы на контроллеры домена перед продолжением.

Если вы используете сертификаты на основе PFX-ФАЙЛ, выполните следующие команды на сервер HGS:

```powershell
$signingCertPass = Read-Host -AsSecureString -Prompt "Signing certificate password"
$encryptionCertPass = Read-Host -AsSecureString -Prompt "Encryption certificate password"

Install-ADServiceAccount -Identity 'HGSgMSA'

Initialize-HgsServer -UseExistingDomain -ServiceAccount 'HGSgMSA' -JeaReviewersGroup 'HgsJeaReviewers' -JeaAdministratorsGroup 'HgsJeaAdmins' -HgsServiceName 'HgsService' -ClusterName 'HgsCluster' -SigningCertificatePath '.\signCert.pfx' -SigningCertificatePassword $signPass -EncryptionCertificatePath '.\encCert.pfx' -EncryptionCertificatePassword $encryptionCertPass -TrustActiveDirectory
```

Если вы используете сертификатов, установленных на локальном компьютере (например, поддержкой HSM и не экспортируются сертификаты), используйте `-SigningCertificateThumbprint` и `-EncryptionCertificateThumbprint` параметров вместо этого.

## <a name="next-step"></a>Дальнейшие действия

>[!div class="nextstepaction"]
[Настройка фабрики DNS](guarded-fabric-configuring-fabric-dns-ad.md)

