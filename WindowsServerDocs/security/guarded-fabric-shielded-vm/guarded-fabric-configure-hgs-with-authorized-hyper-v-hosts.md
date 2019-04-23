---
title: Развертывание защищенных узлов
ms.custom: na
ms.prod: windows-server-threshold
ms.topic: article
ms.assetid: 2379ca26-b32d-4055-8b4b-99d1f2df37e1
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 3b20a7eb2b5097d8ddb7381fd0304581ca4e6722
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59845355"
---
# <a name="deploy-guarded-hosts"></a>Развертывание защищенных узлов

>Относится к: Windows Server 2019 г., Windows Server (полугодовой канал), Windows Server 2016

В этом разделе описываются действия, принимает администратор структуры для настройки узлов Hyper-V для работы с помощью службы Защитника узлов (HGS). Перед началом следующие действия, хотя бы один узел в [HGS кластера необходимо настроить](guarded-fabric-setting-up-the-host-guardian-service-hgs.md).

**Для аттестации доверенного платформенного МОДУЛЯ**:
1. [Настройте структуру DNS](guarded-fabric-configuring-fabric-dns.md): В этой статье описывается настройка DNS-сервера пересылки из структуры домена к домену HGS.
2. [Запись сведений, необходимых HGS](guarded-fabric-tpm-trusted-attestation-capturing-hardware.md): Указывает, как записывать идентификаторы доверенного платформенного МОДУЛЯ (также называемый идентификаторов платформы), создайте политику целостности кода и создания базовой инфраструктуры доверенного платформенного МОДУЛЯ. Затем вы укажете эти сведения администратору настраивать аттестации HGS.
3. [Подтвердите подтвердят защищенных узлов](guarded-fabric-confirm-hosts-can-attest-successfully.md)

**Для аттестации ключей узла**:
1. [Создайте ключ узла](guarded-fabric-create-host-key.md#create-a-host-key): В этой статье описывается настройка DNS-сервера пересылки из структуры домена к домену HGS.
2. [Добавить ключ узла к службе аттестации](guarded-fabric-create-host-key.md#add-the-host-key-to-the-attestation-service): Указывает, как настроить группу безопасности Active Directory в домене fabric, добавить защищенных узлов в качестве членов этой группы и укажите идентификатор группы для администратора HGS. 
3. [Подтвердите подтвердят защищенных узлов](guarded-fabric-confirm-hosts-can-attest-successfully.md)


**Для аттестацию с доверием администратора**:
1. [Настройте структуру DNS](guarded-fabric-configuring-fabric-dns.md): В этой статье описывается настройка DNS-сервера пересылки из структуры домена к домену HGS.
2. [Создайте группу безопасности](guarded-fabric-admin-trusted-attestation-creating-a-security-group.md): Указывает, как настроить группу безопасности Active Directory в домене fabric, добавить защищенных узлов в качестве членов этой группы и укажите идентификатор группы для администратора HGS. 
3. [Подтвердите подтвердят защищенных узлов](guarded-fabric-confirm-hosts-can-attest-successfully.md)


## <a name="see-also"></a>См. также

- [Задачи по развертыванию для защищенных структур и экранированных виртуальных машин](guarded-fabric-deploying-hgs-overview.md#deployment-tasks-for-guarded-fabrics-and-shielded-vms)
