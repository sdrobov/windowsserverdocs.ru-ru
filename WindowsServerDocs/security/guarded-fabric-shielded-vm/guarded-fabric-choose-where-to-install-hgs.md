---
title: Выберите, следует ли установить HGS в свой собственный нового леса или в существующем лесу бастиона
ms.custom: na
ms.prod: windows-server-threshold
ms.topic: article
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 4e02cd37391e629c9b947095fe32626bd15726ff
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59827505"
---
# <a name="choose-whether-to-install-hgs-in-its-own-dedicated-forest-or-in-an-existing-bastion-forest"></a>Выберите, следует ли установить HGS в свой собственный выделенный лес или в существующем лесу бастиона

>Относится к: Windows Server 2019 г., Windows Server (полугодовой канал), Windows Server 2016


В лесу Active Directory для HGS важна, так как его Администраторы имеют доступ к ключам, что элемент управления экранированных виртуальных машин. Установка по умолчанию будет установить новый лес выделенный для HGS и настроить другие зависимости. Этот вариант рекомендуется, поскольку среде является самодостаточным и известно для обеспечения безопасности при его создании. 

Только технические требования для установки HGS в существующем лесу будет добавляться в корневом домене; некорневых домены не поддерживаются. Но существуют также эксплуатационные требования и связанные с безопасностью рекомендации по использованию существующего леса. Подходящий лесов создаются специально для обслуживания одной конфиденциальные функции, такие как леса, используемые [Privileged Access Management для AD DS](https://docs.microsoft.com/microsoft-identity-manager/pam/privileged-identity-management-for-active-directory-domain-services) или [усиленной безопасности администратора среды (ESAE) лес](https://technet.microsoft.com/windows-server-docs/security/securing-privileged-access/securing-privileged-access-reference-material#ESAE_BM). Таких лесов обычно имеют следующие характеристики:

- У них есть несколько администраторов (отдельно от администраторов структуры)
- Они имеют небольшое количество входов
- Они не являются универсальными по своей природе 

Лесов общего назначения, такие как рабочий лес не подходят для использования с HGS. Fabric лесов также уже не годятся, поскольку HGS должен быть изолирован от администраторов структуры.

## <a name="next-step"></a>Дальнейшие действия

Выберите вариант установки, который лучше всего подходит для вашей среды:

- [Установка HGS в свой собственный выделенный лес](guarded-fabric-install-hgs-default.md)
- [Установка HGS в существующем лесу бастиона](guarded-fabric-install-hgs-in-a-bastion-forest.md)


