---
title: Установка HGS в новом лесу
ms.custom: na
ms.prod: windows-server-threshold
ms.topic: article
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 84f88d96f1e16767dec3b21b34aa226e544afaac
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66447403"
---
# <a name="install-hgs-in-a-new-forest"></a>Установка HGS в новом лесу 

>Относится к: Windows Server 2019 г., Windows Server (полугодовой канал), Windows Server 2016

## <a name="add-the-hgs-server-role"></a>Добавление роли сервера HGS

Выполните следующие команды в сеанс PowerShell с повышенными правами для добавления роли сервера HGS и установить HGS.

[!INCLUDE [Install the HGS server role](../../../includes/guarded-fabric-install-hgs-server-role.md)] 

## <a name="install-hgs"></a>Установка HGS 

[!INCLUDE [Install HGS by default](../../../includes/install-hgs-default.md)] 

## <a name="next-steps"></a>Следующие шаги

- Дальнейшие действия для настройки аттестации на основе доверенного платформенного МОДУЛЯ, см. в разделе [инициализировать кластер HGS, использующий режим доверенного платформенного МОДУЛЯ на нового выделенного леса (по умолчанию)](guarded-fabric-initialize-hgs-tpm-mode-default.md).
- Для выполнения следующих действий настроить аттестацию ключей узла, см. в разделе [инициализировать кластер HGS, используя режим ключа из нового выделенного леса (по умолчанию)](guarded-fabric-initialize-hgs-key-mode-default.md).
- Для следующего действия по настройке аттестации на основе администратора (является устаревшим в Windows Server 2019), см. в разделе [инициализировать кластер HGS, используя режим AD из нового выделенного леса (по умолчанию)](guarded-fabric-initialize-hgs-ad-mode-default.md).

## <a name="next-step"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Инициализация HGS](guarded-fabric-initialize-hgs.md)


