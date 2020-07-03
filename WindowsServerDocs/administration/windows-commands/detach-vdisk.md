---
title: detach vdisk
description: Справочная статья по команде Detach vdisk, которая останавливает выбранный виртуальный жесткий диск (VHD) в качестве локального жесткого диска на главном компьютере.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5f01dcb8-9237-4564-ad94-8a8dd0fd0cca
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bce18dcf55940ca8529e4bee21af2f09282d0e00
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85928705"
---
# <a name="detach-vdisk"></a>detach vdisk

> Область применения: Windows Server (половина ежегодного канала), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Останавливает отображение выбранного виртуального жесткого диска (VHD) в качестве локального жесткого диска на главном компьютере. При отсоединении виртуального жесткого диска его можно скопировать в другие расположения. Прежде чем начать, необходимо выбрать виртуальный жесткий диск для выполнения этой операции. Используйте команду [SELECT VDISK](select-vdisk.md) , чтобы выбрать виртуальный жесткий диск и переместить фокус на него.


## <a name="syntax"></a>Синтаксис

```
detach vdisk [noerr]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| Noerr | Только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки. |

## <a name="examples"></a>Примеры

Чтобы отсоединить выбранный виртуальный жесткий диск, введите:

```
detach vdisk
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда Attach vdisk](attach-vdisk.md)

- [Команда Compact VDISK](compact-vdisk.md)

- [Команда Detail VDISK](detail-vdisk.md)

- [Команда Expand VDISK](expand-vdisk.md)

- [Команда merge VDISK](merge-vdisk.md)

- [команда SELECT VDISK](select-vdisk.md)

- [Команда list](list.md)
