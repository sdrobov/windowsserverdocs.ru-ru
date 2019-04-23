---
title: AD FS Устранение неполадок — цикл обнаружения
description: В этом документе описывается устранение неполадок обнаружения цикла
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 02/21/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: cc8eeb11e44da3b8f26b1ab94143c189bca9ed38
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59830915"
---
# <a name="ad-fs-troubleshooting---loop-detection"></a>AD FS Устранение неполадок — цикл обнаружения 
 
Циклы в AD FS происходит, когда Доверяющая сторона постоянно отклоняет допустимый маркер безопасности и перенаправляет обратно в AD FS.

## <a name="loop-detection-cookie"></a>Файл cookie цикл обнаружения
Чтобы предотвратить такую ситуацию, AD FS реализовала так называемый файл cookie цикл обнаружения. По умолчанию AD FS записывает файл cookie для веб-пассивном клиентов с именем **MSISLoopDetectionCookie**. Этот файл cookie содержит значение отметки времени или число токенов, выданных значение.  Это позволяет AD FS, чтобы следить, как часто и как часто клиент посетил службы федерации в определенный период времени.

Если пассивный клиент посещает службы федерации для токена пяти (5) в течение 20 секунд, AD FS вызывает следующую ошибку:

**MSIS7042: Один клиентский сеанс браузера сделал "{0}«запросы за последние»{1}" секунд. Дополнительные сведения, обратитесь к администратору.**

Ввод в бесконечных циклов часто бывает вызвана неверным поведением, он не использует маркер, выданный AD FS успешно приложение проверяющей стороны и отправляет приложение — пассивном клиентском обратно в AD FS, новый маркер.  AD FS будет выдавать пассивном клиентском новый маркер каждый раз, до тех пор, пока они не превышают 5 запросов в течение 20 секунд. 

## <a name="adjusting-the-loop-detection-cookie"></a>Настройка обнаружения цикла куки-файл
Можно использовать PowerShell, чтобы изменить количество маркеров, выдаваемых значения и значения timespan.

```powershell
Set-AdfsProperties -LoopDetectionMaximumTokensIssuedInterval 5  -LoopDetectionTimeIntervalInSeconds 20
```
Минимальное значение для **LoopDetectionMaximumTokensIssuedInterval** -1.

Минимальное значение для **LoopDetectionTimeIntervalInSeconds** равно 5.

Можно также отключить обнаружение цикла при выполнении тестирования производительности.

```powershell
Set-AdfsProperties -EnableLoopDetection $false
```

>[!IMPORTANT]
>Рекомендуется не полностью отключить определение цикла, как это не позволяет пользователю ввести в бесконечный цикл состояний.


## <a name="next-steps"></a>Следующие шаги

- [Устранение неполадок AD FS](ad-fs-tshoot-overview.md)



