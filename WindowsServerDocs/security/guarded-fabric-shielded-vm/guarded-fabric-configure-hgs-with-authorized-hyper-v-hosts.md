---
title: Развертывание защищенных узлов
ms.custom: na
ms.prod: windows-server
ms.topic: article
ms.assetid: 2379ca26-b32d-4055-8b4b-99d1f2df37e1
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: bc79d13b4dda96cd3e760958a6310276d2c45bae
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71386750"
---
# <a name="deploy-guarded-hosts"></a>Развертывание защищенных узлов

>Относится к: Windows Server 2019, Windows Server (половина ежегодного канала), Windows Server 2016

В подразделах этого раздела описываются шаги, необходимые администратору структуры для настройки узлов Hyper-V для работы со службой защиты узла (HGS). Прежде чем вы сможете выполнить эти действия, необходимо настроить хотя бы один узел в [кластере HGS](guarded-fabric-setting-up-the-host-guardian-service-hgs.md).

**Для аттестации, доверенной для доверенного платформенного модуля**:
1. [Настройте DNS-структуру](guarded-fabric-configuring-fabric-dns.md): Сведения о настройке сервера пересылки DNS из домена структуры в домен HGS.
2. [Запись сведений, необходимых для HGS](guarded-fabric-tpm-trusted-attestation-capturing-hardware.md): Сведения о том, как записывать идентификаторы TPM (также называемые идентификаторами платформы), создавать политику целостности кода и создавать базовые показатели TPM. Затем эти сведения будут предоставлены администратору HGS для настройки аттестации.
3. [Подтверждение аттестации защищенных узлов](guarded-fabric-confirm-hosts-can-attest-successfully.md)

**Для аттестации ключа узла**:
1. [Создайте ключ узла](guarded-fabric-create-host-key.md#create-a-host-key): Сведения о настройке сервера пересылки DNS из домена структуры в домен HGS.
2. [Добавьте ключ узла в службу аттестации](guarded-fabric-create-host-key.md#add-the-host-key-to-the-attestation-service): Сведения о настройке группы безопасности Active Directory в домене структуры, добавлении защищенных узлов в качестве членов этой группы и предоставлении этого идентификатора группы администратору HGS. 
3. [Подтверждение аттестации защищенных узлов](guarded-fabric-confirm-hosts-can-attest-successfully.md)


**Для аттестации, доверенной для администраторов**:
1. [Настройте DNS-структуру](guarded-fabric-configuring-fabric-dns.md): Сведения о настройке сервера пересылки DNS из домена структуры в домен HGS.
2. [Создайте группу безопасности](guarded-fabric-admin-trusted-attestation-creating-a-security-group.md). Сведения о настройке группы безопасности Active Directory в домене структуры, добавлении защищенных узлов в качестве членов этой группы и предоставлении этого идентификатора группы администратору HGS. 
3. [Подтверждение аттестации защищенных узлов](guarded-fabric-confirm-hosts-can-attest-successfully.md)


## <a name="see-also"></a>См. также

- [Задачи развертывания для защищенных структур и экранированных виртуальных машин](guarded-fabric-deploying-hgs-overview.md#deployment-tasks-for-guarded-fabrics-and-shielded-vms)
