---
title: tskill
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 697363c91837ff675a14099fd212f4f0753b739b
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392335"
---
# <a name="tskill"></a>tskill

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Завершает процесс, выполняющийся в сеансе на сервере узла сеансов удаленный рабочий стол.
Примеры использования этой команды см. в разделе [примеры](#BKMK_examples).

> [!NOTE]
> В Windows Server 2008 R2 службы терминалов были переименованы на службы удаленных рабочих столов. Чтобы узнать о новых возможностях последней версии, см. статью [новые возможности службы удаленных рабочих столов в Windows server 2012](https://technet.microsoft.com/library/hh831527) в библиотеке TechNet по Windows Server.

## <a name="syntax"></a>Синтаксис
```
tskill {<ProcessID> | <ProcessName>} [/server:<ServerName>] [/id:<SessionID> | /a] [/v]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------|--------|
|@no__t 0ProcessID >|Указывает идентификатор процесса, который требуется завершить.|
|@no__t 0ProcessName >|Указывает имя процесса, который требуется завершить. Этот параметр может содержать подстановочные знаки.|
|/Server: @no__t 0ServerName >|Указывает сервер терминалов, содержащий процесс, который требуется завершить. Если параметр **/Server** не указан, используется текущий сервер узла сеансов удаленных рабочих столов.|
|/ID: \<SessionID >|Завершает процесс, выполняющийся в указанном сеансе.|
|/|Завершает процесс, выполняющийся во всех сеансах.|
|/v|Отображает сведения о выполняемых действиях.|
|/?|Отображение справки в командной строке.|

## <a name="remarks"></a>Примечания
- Вы можете использовать **тскилл** , чтобы завершить только те процессы, которые принадлежат вам, если вы не являетесь администратором. Администраторы имеют полный доступ ко всем функциям **тскилл** и могут завершать процессы, работающие в других пользовательских сеансах.
- При завершении всех процессов, выполняемых в сеансе, сеанс также завершается.
- Если используются параметры *processName* и **/Server:** <em>ServerName</em> , необходимо также указать параметр **/ID:** <em>SessionID</em> или **/a** .

## <a name="BKMK_examples"></a>Примеров
- Чтобы завершить процесс 6543, введите:
  ```
  tskill 6543
  ```
- Чтобы завершить процесс "Обозреватель", выполняющийся в сеансе 5, введите:
  ```
  tskill explorer /id:5
  ```
  #### <a name="additional-references"></a>Дополнительная справка
  [Ключ синтаксиса командной строки](command-line-syntax-key.md)
  [службы удаленных рабочих столов &#40;Справочник по&#41; командам служб терминалов](remote-desktop-services-terminal-services-command-reference.md)
