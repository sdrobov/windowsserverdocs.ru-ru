---
title: bitsadmin getreplyfilename
description: Раздел команд Windows для **битсадмин жетреплифиленаме**, который получает путь к файлу, содержащему ответ на отправку сервера для задания.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 85447184-1732-4816-a365-2e3599551bf8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 541a6e60d641405b5da2e65fecbbbe87468c8702
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850497"
---
# <a name="bitsadmin-getreplyfilename"></a>bitsadmin getreplyfilename

Возвращает путь к файлу, содержащему ответ на отправку сервера для задания.

> [!NOTE]
> Эта команда не поддерживается в БИТАХ 1,2 и более ранних версиях.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /getreplyfilename <job>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| -------------- | -------------- |
| задания | Отображаемое имя задания или идентификатор GUID. |


## <a name="examples"></a><a name=BKMK_examples></a>Примеров

В следующем примере извлекается имя файла ответа для отправки для задания с именем *мидовнлоаджоб*.

```
C:\>bitsadmin /getreplyfilename myDownloadJob
```

## <a name="additional-references"></a>Дополнительные материалы

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)