---
title: 'ksetup: ChangePassword'
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 283078e7-a88f-4875-90e6-f8605e6b7ea7
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 51be9e71c2b290e6346d23144543e0eec29f9d07
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71375178"
---
# <a name="ksetupchangepassword"></a>ksetup: ChangePassword



Использует значение пароля центр распространения ключей (KDC) (кпассвд) для изменения пароля вошедшего в систему пользователя. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /changepassword <OldPasswd> <NewPasswd>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|@no__t 0OldPasswd >|Указывает существующий пароль пользователя, вошедшего в систему.|
|@no__t 0NewPasswd >|Указывает на новый пароль пользователя, вошедшего в систему.|

## <a name="remarks"></a>Примечания

Эта команда использует пароль KDC (кпассвд) для изменения пароля вошедшего в систему пользователя. Кпассвд, если он задан, отобразится в выходных данных, выполнив команду **ksetup/думпстате** .

Новый пароль пользователя должен соответствовать всем требованиям к паролю, заданным на этом компьютере.

Если учетная запись пользователя не найдена в текущем домене, система предложит указать имя домена, в котором находится учетная запись пользователя.

Если вы хотите принудительно сменить пароль при следующем входе в систему, эта команда позволяет использовать звездочку (*), поэтому пользователю будет предложено ввести новый пароль.

Выходные данные команды уведомляют о состоянии успешного выполнения или сбоя.

## <a name="BKMK_Examples"></a>Примеров

Изменить пароль пользователя, который в данный момент вошел в систему на этом компьютере в этом домене:
```
ksetup /changepassword Pas$w0rd Pa$$w0rd
```
Изменение пароля пользователя, который в настоящее время вошел в домен contoso:
```
ksetup /domain CONTOSO /changepassword Pas$w0rd Pa$$w0rd
```
Заставить текущего пользователя изменить пароль при следующем входе в систему:
```
ksetup /changepassword Pas$w0rd *
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)