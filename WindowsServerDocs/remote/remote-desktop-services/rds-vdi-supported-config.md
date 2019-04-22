---
title: Поддерживаемые конфигурации безопасности Windows 10 для VDI служб удаленных рабочих столов
description: Сведения о поддерживаемых конфигурациях для Windows 10 VDI с помощью служб удаленных рабочих СТОЛОВ в Windows Server 2016.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: remote-desktop-services
ms.author: elizapo
ms.date: 10/27/2016
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8f164f5d-a498-4f91-a12f-3e01d554f810
author: lizap
manager: dongill
ms.openlocfilehash: ff890150dcea30c425267dcaae9b1bdbc6d78b8c
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59820085"
---
# <a name="supported-windows-10-security-configurations-for-remote-desktop-services-vdi"></a>Поддерживаемые конфигурации безопасности Windows 10 для VDI служб удаленных рабочих столов

> Область применения. Windows Server 2016

Windows 10 и Windows Server 2016 имеют новые уровни защиты, встроенные в операционную систему для дальнейшей защиты от нарушений безопасности, помочь заблокировать атак злоумышленников и повысьте безопасность виртуальных машин, приложений и данных.

> [!NOTE]
> Не забудьте проверить [служб удаленных рабочих столов поддерживается сведения о конфигурации](rds-supported-config.md).

В следующей таблице показано, эти новые функции, поддерживаемые в развертывании VDI с помощью RDS.

|  Тип коллекции VDI               |  Управляемые в составе пула |  Управляемые личные |  Неуправляемые в составе пула                                     |  Неуправляемые personal                                    |
|-------------------------------------|------------------|--------------------|--------------------------------------------------------|--------------------------------------------------------|
| [Credential Guard](https://technet.microsoft.com/itpro/windows/keep-secure/credential-guard)                    | Да              | Да                | Да                                                    | Да                                                    |
| [Device Guard](https://technet.microsoft.com/itpro/windows/keep-secure/device-guard-deployment-guide)                        | Да              | Да                | Да                                                    | Да                                                    |
| [Удаленный Credential Guard](https://technet.microsoft.com/itpro/windows/keep-secure/remote-credential-guard)             | Нет               | Нет                 | Нет                                                     | Нет                                                     |
| [Экранированный & шифрование поддерживается виртуальных машин](../../security/guarded-fabric-shielded-vm/guarded-fabric-and-shielded-vms.md) | Нет               | Нет                 | Шифрование поддерживается виртуальных машин с помощью дополнительной настройки | Шифрование поддерживается виртуальных машин с помощью дополнительной настройки |

## <a name="remote-credential-guard"></a>Удаленный Credential Guard:

Удаленный Credential Guard поддерживается только для прямого подключения на конечные компьютеры, а не для тех, которые через посредника подключений к удаленному рабочему столу и шлюза удаленных рабочих столов.
> [!NOTE]
> Если у вас есть посредника подключений в среде с одним экземпляром, и DNS-имя соответствует имени компьютера, можно использовать удаленный Credential Guard, несмотря на то, что это не поддерживается.

## <a name="shielded-vms-and-encryption-supported-vms"></a>Экранированные виртуальные машины и шифрование поддерживаемые виртуальные машины: 

- Экранированные виртуальные машины не поддерживаются в удаленных рабочих столов VDI служб 

По использованию виртуальных машин, поддерживаемых шифрования:
- Используете неуправляемую коллекцию и подготовки технологии вне процесса создания коллекции служб удаленных рабочих столов для подготовки виртуальных машин. 
- Диски профилей пользователей не поддерживаются, так как они используют разностными дисками 

