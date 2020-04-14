---
title: tskill
description: Раздел команд Windows для тскилл, который завершает процесс, выполняющийся в сеансе на удаленный рабочий стол сервере узла сеансов.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 08986e6a-6900-4ece-85a1-8f73b14db1b3 Lizap
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 57a3d2c9d5ea90fafeffefd0811bb9378adbe81e
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80832467"
---
# <a name="tskill"></a>tskill

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Завершает процесс, выполняющийся в сеансе на удаленный рабочий стол сервере узла сеансов.
Примеры использования этой команды см. в разделе [примеры](#BKMK_examples).

> [!NOTE]
> В Windows Server 2008 R2 службы терминалов называются службами удаленных рабочих столов. Чтобы узнать о новых возможностях последней версии, см. статью [новые возможности службы удаленных рабочих столов в Windows server 2012](https://technet.microsoft.com/library/hh831527) в библиотеке TechNet по Windows Server.

## <a name="syntax"></a>Синтаксис
```
tskill {<ProcessID> | <ProcessName>} [/server:<ServerName>] [/id:<SessionID> | /a] [/v]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------|--------|
|\<ProcessID >|Указывает идентификатор процесса, который требуется завершить.|
|\<ProcessName >|Указывает имя процесса, который требуется завершить. Этот параметр может содержать подстановочные знаки.|
|/Server:\<ServerName >|Указывает сервер терминалов, содержащий процесс, который требуется завершить. Если параметр **/Server** не указан, используется текущий сервер узла сеансов удаленных рабочих столов.|
|/ID:\<SessionID >|Завершает процесс, выполняющийся в указанном сеансе.|
|/a|Завершает процесс, выполняющийся во всех сеансах.|
|/v|Отображает сведения о выполняемых действиях.|
|/?|Отображает справку в командной строке.|

## <a name="remarks"></a>Примечания
- Вы можете использовать **тскилл** , чтобы завершить только те процессы, которые принадлежат вам, если вы не являетесь администратором. Администраторы имеют полный доступ ко всем функциям **тскилл** и могут завершать процессы, работающие в других пользовательских сеансах.
- При завершении всех процессов, выполняемых в сеансе, сеанс также завершается.
- Если используются параметры *processName* и **/Server:** <em>ServerName</em> , необходимо также указать параметр **/ID:** <em>SessionID</em> или **/a** .

## <a name="examples"></a><a name=BKMK_examples></a>Примеров
- Чтобы завершить процесс 6543, введите:
  ```
  tskill 6543
  ```
- Чтобы завершить работу обозревателя процессов в сеансе 5, введите:
  ```
  tskill explorer /id:5
  ```
  ## <a name="additional-references"></a>Дополнительные материалы
  - [Командная строка синтаксиса командной строки](command-line-syntax-key.md)
  [службы удаленных рабочих столов (службы терминалов) Справочник по командам](remote-desktop-services-terminal-services-command-reference.md)
