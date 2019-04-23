---
title: finger
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 907ea637-5c6c-4752-84c2-46bbf2a68a33
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 42622fdf19cdd50b76d32989769874cbd05e9f4a
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59826945"
---
# <a name="finger"></a>finger

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает сведения о пользователю или пользователям указанного удаленного компьютера (как правило, компьютером под управлением UNIX), на котором выполняется служба finger или управляющей программы. Удаленный компьютер указывает формат и вывод экрана сведений пользователя. При использовании без параметров, **палец** отображает справку. 
## <a name="syntax"></a>Синтаксис
```
finger [-l] [<User>] [@<Host>] [...]
```
### <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|-l|Отображает сведения о пользователе в форме длинного списка.|
|<User>|Указывает пользователя, для которого требуется получить сведения. Если опустить *пользователя* параметра **палец** отображает сведения обо всех пользователях на указанном компьютере.|
|@<Host>|Удаленный компьютер, запускающий службу finger, где вы ищете сведения о пользователе. Можно указать имя компьютера или IP-адрес.|
|/?|Отображение справки в командной строке.|
## <a name="remarks"></a>Примечания
Несколько User@Host параметры могут быть заданы.
Необходимо добавить **палец** параметров с дефиса (-), а не косую черту (/).
Эта команда доступна только в том случае, если протокол Интернета (TCP/IP) устанавливается как компонент в свойствах сетевого адаптера в сетевых подключений.
Windows Server 2003 не поддерживает услуга палец.
## <a name="BKMK_Examples"></a>Примеры
Чтобы отобразить сведения для пользователя user1 users.microsoft.com компьютера, введите следующую команду:
```
finger user1@users.microsoft.com
```
Чтобы отобразить сведения для всех пользователей на компьютере users.microsoft.com, введите:
```
finger @users.microsoft.com
```
## <a name="additional-references"></a>Дополнительные ссылки
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)
