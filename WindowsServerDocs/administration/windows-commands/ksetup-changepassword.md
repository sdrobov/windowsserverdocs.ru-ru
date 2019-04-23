---
title: ksetup:ChangePassword
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: f629c6c7930777583df38f5af900ed380ec60f9c
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59878535"
---
# <a name="ksetupchangepassword"></a>ksetup:ChangePassword



Использует значение пароля (kpasswd) центр распространения ключей (KDC) для изменения пароля пользователя, вошедшего в систему. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
ksetup /changepassword <OldPasswd> <NewPasswd>
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<OldPasswd >|Утверждает, существующий пароль пользователя вошедшего в систему.|
|\<NewPasswd >|Утверждает, вошедших в систему на новый пароль пользователя.|

## <a name="remarks"></a>Примечания

Эта команда использует значение пароля (kpasswd) центра распространения КЛЮЧЕЙ для изменения пароля пользователя, вошедшего в систему. Kpasswd, если задан, отображается в выходных данных, выполнив **ksetup /dumpstate** команды.

Новый пароль пользователя должен соответствовать все требования к паролю, установленные на этом компьютере.

Если учетная запись пользователя не найден в текущем домене, система выдаст запрос, необходимо указать имя домена, где находится учетная запись пользователя.

Если вы хотите принудительно применить смену пароля при следующем входе в систему, эта команда позволяет использовать символ звездочки (*), поэтому пользователю предложат ввести новый пароль.

Выходные данные команды сообщает о состоянии об успехе или неудаче.

## <a name="BKMK_Examples"></a>Примеры

Изменение пароля пользователя, вошедшего в систему на этот компьютер в этом домене.
```
ksetup /changepassword Pas$w0rd Pa$$w0rd
```
Изменение пароля пользователя, вошедшего в систему в домене Contoso.
```
ksetup /domain CONTOSO /changepassword Pas$w0rd Pa$$w0rd
```
Принудительно текущего пользователя, чтобы сменить пароль при следующем входе в систему:
```
ksetup /changepassword Pas$w0rd *
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)