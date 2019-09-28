---
title: Установка HGS в новом лесу
ms.custom: na
ms.prod: windows-server
ms.topic: article
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 6dfbe24fb4d9011b48f366d7e5df92fdb80685d5
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71386590"
---
# <a name="install-hgs-in-a-new-forest"></a>Установка HGS в новом лесу 

>Относится к: Windows Server 2019, Windows Server (половина ежегодного канала), Windows Server 2016

## <a name="add-the-hgs-server-role"></a>Добавление роли сервера HGS

Выполните следующие команды в сеансе PowerShell с повышенными привилегиями, чтобы добавить роль сервера HGS и установить HGS.

[!INCLUDE [Install the HGS server role](../../../includes/guarded-fabric-install-hgs-server-role.md)] 

## <a name="install-hgs"></a>Установка HGS 

[!INCLUDE [Install HGS by default](../../../includes/install-hgs-default.md)] 

## <a name="next-steps"></a>Следующие шаги

- Дальнейшие действия по настройке аттестации на основе TPM см. в статье [Инициализация кластера HGS с помощью режима TPM в новом выделенном лесу (по умолчанию)](guarded-fabric-initialize-hgs-tpm-mode-default.md).
- Дальнейшие действия по настройке аттестации ключа узла см. в статье [Инициализация кластера HGS с помощью режима ключей в новом выделенном лесу (по умолчанию)](guarded-fabric-initialize-hgs-key-mode-default.md).
- Дальнейшие действия по настройке аттестации на основе администратора (не рекомендуется в Windows Server 2019) см. в статье [Инициализация кластера HGS с помощью режима AD в новом выделенном лесу (по умолчанию)](guarded-fabric-initialize-hgs-ad-mode-default.md).

## <a name="next-step"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Инициализация HGS](guarded-fabric-initialize-hgs.md)


