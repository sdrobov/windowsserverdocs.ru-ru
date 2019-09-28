---
title: ntbackup
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6bce6b0d-646b-46b6-b833-0ff1d6f082c2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ebbe71fd5547311beb36747d32d695823e0f0059
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71372678"
---
# <a name="ntbackup"></a>ntbackup



Команда **Ntbackup** недоступна в Windows Vista и windows Server 2008. Вместо этого следует использовать команду **Wbadmin** и подкоманды для резервного копирования и восстановления компьютера и файлов из командной строки.

Вы не можете восстановить резервные копии, созданные с помощью **Ntbackup** , при помощи **Wbadmin**. Тем не менее версия **Ntbackup** доступна для загрузки пользователям windows Server 2008 и Windows Vista, которые хотят восстановить резервные копии, созданные с помощью **Ntbackup**. Эта загружаемая версия **Ntbackup** позволяет выполнять операции восстановления только из устаревших резервных копий и не может использоваться на компьютерах под управлением windows Server 2008 или Windows Vista для создания новых резервных копий. Чтобы скачать эту версию **Ntbackup**, см. раздел [https://go.microsoft.com/fwlink/?LinkId=82917](https://go.microsoft.com/fwlink/?LinkId=82917).

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

[Wbadmin](wbadmin.md)