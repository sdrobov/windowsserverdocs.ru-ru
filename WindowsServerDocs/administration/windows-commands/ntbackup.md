---
title: ntbackup
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6bce6b0d-646b-46b6-b833-0ff1d6f082c2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b68b4cca579a5fc27f921ce2f4fcc6976d8e5600
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80838017"
---
# <a name="ntbackup"></a>ntbackup



Команда **Ntbackup** недоступна в Windows Vista и windows Server 2008. Вместо этого следует использовать команду **Wbadmin** и подкоманды для резервного копирования и восстановления компьютера и файлов из командной строки.

Вы не можете восстановить резервные копии, созданные с помощью **Ntbackup** , при помощи **Wbadmin**. Тем не менее версия **Ntbackup** доступна для загрузки пользователям windows Server 2008 и Windows Vista, которые хотят восстановить резервные копии, созданные с помощью **Ntbackup**. Эта загружаемая версия **Ntbackup** позволяет выполнять операции восстановления только из устаревших резервных копий и не может использоваться на компьютерах под управлением windows Server 2008 или Windows Vista для создания новых резервных копий. Чтобы скачать эту версию **Ntbackup**, см. [https://go.microsoft.com/fwlink/?LinkId=82917](https://go.microsoft.com/fwlink/?LinkId=82917).

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

[Wbadmin](wbadmin.md)