---
title: ntbackup
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6bce6b0d-646b-46b6-b833-0ff1d6f082c2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ba3aaaa192283e0e1dc1777a27fc13973949784b
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723485"
---
# <a name="ntbackup"></a>ntbackup



Команда **Ntbackup** недоступна в Windows Vista и windows Server 2008. Вместо этого следует использовать команду **Wbadmin** и подкоманды для резервного копирования и восстановления компьютера и файлов из командной строки.

Вы не можете восстановить резервные копии, созданные с помощью **Ntbackup** , при помощи **Wbadmin**. Тем не менее версия **Ntbackup** доступна для загрузки пользователям windows Server 2008 и Windows Vista, которые хотят восстановить резервные копии, созданные с помощью **Ntbackup**. Эта загружаемая версия **Ntbackup** позволяет выполнять операции восстановления только из устаревших резервных копий и не может использоваться на компьютерах под управлением windows Server 2008 или Windows Vista для создания новых резервных копий. Чтобы скачать эту версию **Ntbackup**, см. [https://go.microsoft.com/fwlink/?LinkId=82917](https://go.microsoft.com/fwlink/?LinkId=82917)раздел.

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

[Wbadmin](wbadmin.md)