---
title: Выберите, следует ли устанавливать HGS в новом лесу или в существующем лесу бастиона.
ms.custom: na
ms.prod: windows-server
ms.topic: article
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 28c7eceefa4747a35d1b989df4a2c5e43a8d6a42
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71386788"
---
# <a name="choose-whether-to-install-hgs-in-its-own-dedicated-forest-or-in-an-existing-bastion-forest"></a>Выберите, следует ли устанавливать HGS в собственном выделенном лесу или в существующем лесу бастиона.

>Относится к: Windows Server 2019, Windows Server (половина ежегодного канала), Windows Server 2016


Лес Active Directory для HGS является конфиденциальным, так как его администраторы имеют доступ к ключам, которые управляют экранированными виртуальными машинами. При установке по умолчанию будет настроен новый лес, выделенный для HGS, и настроены другие зависимости. Этот вариант рекомендуется, так как среда самодостаточна и безопасна при ее создании. 

Единственным техническим требованием для установки HGS в существующем лесу является добавление его в корневой домен. Некорневые домены не поддерживаются. Но существуют также эксплуатационные требования и рекомендации по обеспечению безопасности для использования существующего леса. Подходящие леса предназначены специально для обслуживания одной конфиденциальной функции, такой как лес, используемый [privileged Access Management для AD DS](https://docs.microsoft.com/microsoft-identity-manager/pam/privileged-identity-management-for-active-directory-domain-services) или [леса расширенной административной среды (ЕСАЕ)](https://technet.microsoft.com/windows-server-docs/security/securing-privileged-access/securing-privileged-access-reference-material#ESAE_BM). Такие леса обычно представляют следующие характеристики:

- У них несколько администраторов (отделены от администраторов структуры)
- У них небольшое количество входов
- Они не являются универсальными по своей природе 

Леса общего назначения, такие как рабочие леса, не подходят для использования в HGS. Леса структуры также не подходят, так как HGS необходимо изолировать от администраторов структуры.

## <a name="next-step"></a>Дальнейшие действия

Выберите вариант установки, который лучше подходит для вашей среды:

- [Установка HGS в собственном выделенном лесу](guarded-fabric-install-hgs-default.md)
- [Установка HGS в существующем лесу бастиона](guarded-fabric-install-hgs-in-a-bastion-forest.md)


