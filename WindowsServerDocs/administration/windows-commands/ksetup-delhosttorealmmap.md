---
title: ksetup делхосттореалммап
description: Справочный раздел по команде ksetup делхосттореалммап, который удаляет сопоставление имени участника-службы (SPN) между указанным узлом и областью.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3faee482-a96c-4614-86fd-aaa446643ec4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 17fc30e76247c570c653d5ec38501a2199435c7f
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2020
ms.locfileid: "83817864"
---
# <a name="ksetup-delhosttorealmmap"></a>ksetup делхосттореалммап

Удаляет сопоставление имени участника-службы (SPN) между указанным узлом и областью. Эта команда также удаляет все сопоставления между узлом и областью (или несколькими узлами в сфере).

Сопоставление сохраняется в реестре в разделе `HKEY_LOCAL_MACHINE\SYSTEM\CurrentContolSet\Lsa\Kerberos\HostToRealm` . После выполнения этой команды рекомендуется убедиться, что сопоставление отображается в реестре.

## <a name="syntax"></a>Синтаксис

```
ksetup /delhosttorealmmap <hostname> <realmname>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `<hostname>` | Указывает полное доменное имя компьютера. |
| `<realmname>` | Указывает DNS-имя в верхнем регистре, например CORP. CONTOSO.COM. |

### <a name="examples"></a>Примеры

Чтобы изменить конфигурацию сферы CONTOSO и удалить сопоставление главного компьютера IPops897 с областью, введите:

```
ksetup /delhosttorealmmap IPops897 CONTOSO
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда ksetup](ksetup.md)

- [ksetup аддхосттореалммап, команда](ksetup-addhosttorealmmap.md)
