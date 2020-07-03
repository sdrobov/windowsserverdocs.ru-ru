---
title: showmount
description: Справочная статья по шовмаунт, в которой отображаются подключенные каталоги.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a6dd562e-e3bd-4ee6-be3b-6d29e29fd20e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 131ecf9dea650dd127e4dff05838245ceece1ead
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85931606"
---
# <a name="showmount"></a>showmount

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Для просмотра подключенных каталогов можно использовать **шовмаунт** .

## <a name="syntax"></a>Синтаксис
```
showmount {-e|-a|-d} <Server>
```

## <a name="description"></a>Описание
Программа командной строки **шовмаунт** \- отображает сведения о подключенных файловых системах, экспортированных сервером для NFS на компьютере, указанном *сервером*. Если *сервер* не указан, **шовмаунт** отображает сведения о компьютере, на котором выполняется команда **шовмаунт** .

Необходимо указать один из следующих параметров:

- ** \- e** — отображает все файловые системы, экспортированные на сервере.
- ** \- a** — отображает все NFS-клиенты сетевой файловой системы \( \) и каталоги на сервере, которые подключены.
- ** \- d** — отображает все каталоги на сервере, которые в настоящее время подключены клиентами NFS.

## <a name="see-also"></a>См. также
[Справочник по командам служб для NFS](services-for-network-file-system-command-reference.md)