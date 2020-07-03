---
title: telnet unset
description: Справочная статья для Telnet без параметров, которая отключает ранее установленные параметры.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: da9a0d99-1930-4858-93c7-0e9c3797ee09
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3efbf7d4f2507d16dbe0beb704ab0c80467a56d3
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85935289"
---
# <a name="telnet-unset"></a>Telnet: не задано

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отключает ранее установленные параметры.

## <a name="syntax"></a>Синтаксис
```
u[nset] {bsasdel | crlf | delasbs | escape | localecho | logging | ntlm} [?]
```
#### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|бсасдел|Отправляет **Backspace** в виде **Backspace**.|
|CRLF|Отправляет клавишу **Ввод** в виде CR. Также называется режимом перевода строки.|
|деласбс|Отправляет **Удаление** как **Удаление**.|
|escape-знак|Удаляет параметр escape-символа.|
|локалечо|Отключает локалечо.|
|Ведение журнала|Отключает ведение журнала.|
|NTLM|Отключает проверку подлинности NTLM.|
|?|Отображает справку для этой команды.|
## <a name="examples"></a>Примеры
Отключите ведение журнала.
```
u logging
```
## <a name="additional-references"></a>Дополнительные ссылки
- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
