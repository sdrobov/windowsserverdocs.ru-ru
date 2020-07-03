---
title: regsvr32
description: Справочная статья по команде regsvr32, которая регистрирует DLL-файлы как компоненты команды в реестре.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3345e964-7d3e-42b8-abeb-42ed6edfe2b2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e7a1a9247b66e5eb1a23c1f5ef33fbcb98c53bd7
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85930976"
---
# <a name="regsvr32"></a>regsvr32

Регистрирует DLL-файлы в качестве компонентов команды в реестре.

## <a name="syntax"></a>Синтаксис

```
regsvr32 [/u] [/s] [/n] [/i[:cmdline]] <Dllname>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
|--|--|
| /U | Отменяет регистрацию сервера. |
| /s | Предотвращает отображение сообщений. |
| /n | Предотвращает вызов функции **DllRegisterServer**. Этот параметр требует также использования параметра **/i** . |
| /i`<cmdline>` | Передает необязательную строку командной строки (*cmdline*) в **DllInstall**. При использовании этого параметра с параметром **/u** вызывается **дллунинсталл**. |
| `<Dllname>` | Имя DLL-файла, который будет зарегистрирован. |
| /? | Отображение справки в командной строке. |

### <a name="examples"></a>Примеры

Чтобы зарегистрировать библиотеку. dll для схемы Active Directory, введите:

```
regsvr32 schmmgmt.dll
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
