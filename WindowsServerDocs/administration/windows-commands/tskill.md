---
title: tskill
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 08986e6a-6900-4ece-85a1-8f73b14db1b3 Lizap
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b582334d7b79b2badbb86818be1093b6a5f55080
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66440812"
---
# <a name="tskill"></a>tskill

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Завершает выполнение процесса в сеанс на сервере узла сеансов удаленных рабочих столов (rd узла сеансов).
Примеры для использования этой команды, см. в разделе [примеры](#BKMK_examples).

> [!NOTE]
> В Windows Server 2008 R2 службы терминалов были переименованы на службы удаленных рабочих столов. Чтобы найти новые возможности в последней версии, см. в разделе [какие возможности служб удаленных рабочих столов в Windows Server 2012](https://technet.microsoft.com/library/hh831527) в технической библиотеке Windows Server.

## <a name="syntax"></a>Синтаксис
```
tskill {<ProcessID> | <ProcessName>} [/server:<ServerName>] [/id:<SessionID> | /a] [/v]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------|--------|
|\<ProcessID >|Указывает идентификатор процесса, который необходимо завершить.|
|\<ProcessName>|Имя процесса, который необходимо завершить. Этот параметр может содержать подстановочные знаки.|
|/ Server:\<ServerName >|Сервер терминалов, содержащий процесс, который необходимо завершить. Если **/Server** не указан, используется текущий сервер узла сеансов удаленных рабочих Столов.|
|/id:\<SessionID>|Завершает процесс, на котором выполняется в указанном сеансе.|
|/a|Завершает процесс, на котором работает во всех сеансах.|
|/v|Отображает сведения о выполненных действиях.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания
- Можно использовать **tskill** до конца только те процессы, которые принадлежат вам, если вы являетесь администратором. Администраторы имеют полный доступ ко всем **tskill** функции и могут завершать процессы, работающие в других пользовательских сеансов.
- Если завершить все процессы, запущенные в сеансе, сеанс завершен.
- Если вы используете *ProcessName* и **/Server:** <em>ServerName</em> параметров, также необходимо указать либо **/id:**  <em>SessionID</em> или **/a** параметра.

## <a name="BKMK_examples"></a>Примеры
- Чтобы завершить процесс 6543 введите:
  ```
  tskill 6543
  ```
- Чтобы завершить процесс «обозреватель», запущенный в сеансе 5, введите следующую команду:
  ```
  tskill explorer /id:5
  ```
  #### <a name="additional-references"></a>Дополнительная справка
  [Синтаксис командной строки Key](command-line-syntax-key.md)
  [служб удаленных рабочих столов &#40;служб терминалов&#41; описанием команды](remote-desktop-services-terminal-services-command-reference.md)
