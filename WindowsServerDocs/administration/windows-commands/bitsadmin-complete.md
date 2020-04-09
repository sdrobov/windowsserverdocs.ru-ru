---
title: bitsadmin complete
description: Раздел команд Windows для **битсадмин Complete**, который завершает задание.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a5e86677-8f7b-43b3-929e-97706c57e7f1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 847f6e298ff9701064ce4e577c785f7fc78ea22c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850827"
---
# <a name="bitsadmin-complete"></a>bitsadmin complete

Завершает задание. Загруженные файлы недоступны, пока вы не используете этот параметр. Используйте этот параметр после перемещения задания в состояние "передано". В противном случае будут доступны только файлы, которые были успешно переданы.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /complete <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| задания | Отображаемое имя задания или идентификатор GUID. |

## <a name="examples"></a><a name=BKMK_examples></a>Примеров

При передаче состояния задания служба BITS успешно передала все файлы в задании. Однако файлы недоступны до тех пор, пока не будет использован параметр **/комплете** . 

Если несколько заданий используют *мидовнлоаджоб* в качестве имени, необходимо заменить *мидовнлоаджоб* на GUID задания для уникальной идентификации задания.

```
C:\>bitsadmin /complete myDownloadJob
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)