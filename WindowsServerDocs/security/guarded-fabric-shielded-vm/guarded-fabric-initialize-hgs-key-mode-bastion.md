---
title: Инициализация кластера HGS с помощью режима ключей в лесу бастиона
ms.prod: windows-server
ms.topic: article
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 45f0f587c17e90251da2632f034fe03e2dc1c083
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856657"
---
# <a name="initialize-the-hgs-cluster-using-key-mode-in-an-existing-bastion-forest"></a>Инициализация кластера HGS с помощью режима ключей в существующем лесу бастиона

> Область применения: Windows Server 2019
> 
> [!div class="step-by-step"]
> [«Установка HGS в новом лесу](guarded-fabric-install-hgs-in-a-bastion-forest.md)
> [Создание ключа узла»](guarded-fabric-create-host-key.md)

Домен Active Directory службы будут установлены на компьютере, но должны остаться ненастроенными.

[!INCLUDE [Obtain certificates for HGS](../../../includes/guarded-fabric-initialize-hgs-default-step-two.md)] 

Прежде чем продолжить, убедитесь, что объекты кластера предварительно подготовлены для службы защиты узла и предоставил вошедшему в систему пользователю **полный контроль** над объектами VCO и CNO в Active Directory.
Имя объекта виртуального компьютера необходимо передать в параметр `-HgsServiceName`, а имя кластера — в параметр `-ClusterName`.

> [!TIP]
> Прежде чем продолжить, проверьте контроллеры доменов AD, чтобы убедиться, что объекты кластера реплицированы на все контроллеры домена.

Если вы используете сертификаты на основе PFX, выполните на сервере HGS следующие команды:

```powershell
$signingCertPass = Read-Host -AsSecureString -Prompt "Signing certificate password"
$encryptionCertPass = Read-Host -AsSecureString -Prompt "Encryption certificate password"

Install-ADServiceAccount -Identity 'HGSgMSA'

Initialize-HgsServer -UseExistingDomain -ServiceAccount 'HGSgMSA' -JeaReviewersGroup 'HgsJeaReviewers' -JeaAdministratorsGroup 'HgsJeaAdmins' -HgsServiceName 'HgsService' -ClusterName 'HgsCluster' -SigningCertificatePath '.\signCert.pfx' -SigningCertificatePassword $signPass -EncryptionCertificatePath '.\encCert.pfx' -EncryptionCertificatePassword $encryptionCertPass -TrustHostKey
```

Если вы используете сертификаты, установленные на локальном компьютере (например, сертификаты с защитой от HSM и неэкспортируемые сертификаты), используйте параметры `-SigningCertificateThumbprint` и `-EncryptionCertificateThumbprint`.

