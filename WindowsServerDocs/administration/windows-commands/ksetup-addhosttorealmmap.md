---
title: ksetup аддхосттореалммап
description: Справочный раздел по команде ksetup аддхосттореалммап, который добавляет сопоставление имени участника-службы (SPN) между указанным узлом и областью.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 237742d5-fa68-466c-b97e-636f489248ea
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ee2639a5bb071bdd3d6ac3f6373e881c18f3bf9a
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2020
ms.locfileid: "83818114"
---
# <a name="ksetup-addhosttorealmmap"></a>ksetup аддхосттореалммап

Добавляет сопоставление имени участника-службы (SPN) между указанным узлом и областью. Эта команда также позволяет сопоставлять узел или несколько узлов, совместно использующих один и тот же DNS-суффикс к области.

Сопоставление сохраняется в реестре в разделе **HKEY_LOCAL_MACHINE \систем\куррентконтолсет\лса\керберос\хосттореалм**.

## <a name="syntax"></a>Синтаксис

```
ksetup /addhosttorealmmap <hostname> <realmname>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- |------------ |
| `<hostname>` | Имя узла — это имя компьютера, оно может быть указано в качестве полного доменного имени компьютера. |
| `<realmname>` | Имя области указывается как DNS-имя в верхнем регистре, например CORP. CONTOSO.COM. |

### <a name="examples"></a>Примеры

Чтобы подключить главный компьютер *IPops897* к сфере *contoso* , введите:

```
ksetup /addhosttorealmmap IPops897 CONTOSO
```

Проверьте реестр, чтобы убедиться, что сопоставление выполнено должным образом.

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда ksetup](ksetup.md)

- [ksetup делхосттореалммап, команда](ksetup-delhosttorealmmap.md)
