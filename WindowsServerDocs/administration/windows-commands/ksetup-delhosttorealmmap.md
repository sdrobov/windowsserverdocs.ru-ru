---
title: ksetup delhosttorealmmap
description: Справочная статья по команде ksetup делхосттореалммап, которая удаляет сопоставление имени участника-службы (SPN) между указанным узлом и областью.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3faee482-a96c-4614-86fd-aaa446643ec4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c55fe25a147c23026ddf97900d6da856f04314a3
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85925496"
---
# <a name="ksetup-delhosttorealmmap"></a>ksetup delhosttorealmmap

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
