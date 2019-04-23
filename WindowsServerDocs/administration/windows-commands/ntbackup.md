---
title: ntbackup
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 783f73eba2aeaf9f30c5c1e12a623f1f87f24ede
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59846345"
---
# <a name="ntbackup"></a>ntbackup



**Ntbackup** команда недоступна в Windows Vista или Windows Server 2008. Вместо этого следует использовать **wbadmin** команда и подкоманд для резервного копирования и восстановления компьютера и файлы из командной строки.

Вы не сможете восстановить резервные копии, созданные с помощью **ntbackup** с помощью **wbadmin**. Тем не менее версия **ntbackup** доступен для загрузки для Windows Server 2008 и Windows Vista пользователи, которым нужно восстановить резервные копии, которые они создали с помощью **ntbackup**. Эта загружаемая версия **ntbackup** позволяет выполнить восстановление только устаревшие резервные копии и он не может использоваться на компьютерах под управлением Windows Server 2008 или Windows Vista для создания новых резервных копий. Чтобы загрузить эту версию **ntbackup**, см. в разделе [ https://go.microsoft.com/fwlink/?LinkId=82917 ](https://go.microsoft.com/fwlink/?LinkId=82917).

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)

[WBADMIN](wbadmin.md)