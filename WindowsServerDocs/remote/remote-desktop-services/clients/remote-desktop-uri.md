---
title: Схема URI клиенты удаленного рабочего стола
description: Сведения о схему универсального кода ресурса для клиентов удаленного рабочего стола
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: remote-desktop-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0c3f1eb6-835c-4522-99ff-56c6ee4bb911
author: lizap
manager: dongill
ms.author: elizapo
ms.date: 06/11/2018
ms.localizationpriority: medium
ms.openlocfilehash: f2934fed43c8f4feec2f321d684cc3593933eb5d
ms.sourcegitcommit: d3f73936160505a40633ad8dd5931ac5fe3eccdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "9297473"
---
# Поддержка клиента удаленного рабочего стола схемы универсальный код ресурса (URI)

>Область применения: Windows Server версии 1803, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2

Схемы универсального кода ресурса (URI) предоставляет ИТ-специалистам и разработчикам возможность интегрировать функции клиентов удаленного рабочего стола на всех платформах и улучшение взаимодействия с пользователем, позволяя: 

- Приложения сторонних запуск удаленного рабочего стола Майкрософт и удаленных сеансов с предопределенных параметров (предоставляется как часть строки URI).
- Конечным пользователям запускать удаленные подключения с помощью предварительно настроенные URL-адреса.

>[!NOTE]
> С помощью URI для подключения к удаленному рабочему Столу клиенту не поддерживается в операционных системах Windows — используйте URI с помощью MacOS, iOS и Android.

Удаленного рабочего стола Майкрософт использует rdp://query_string схему URI для сохранения атрибута предварительно настроенные параметры, которые используются при запуске клиента. Строки запросов представляют одним или несколькими атрибутов протокола удаленного рабочего СТОЛА, предоставляемых URL-адрес. 

Атрибуты протокола удаленного рабочего СТОЛА разделяются символ амперсанда (&). Например при подключении к Компьютеру, строка является:

```
rdp://full%20address=s:mypc:3389&audiomode=i:2&disable%20themes=i:1
```

Эта таблица содержит полный список поддерживаемых атрибутов, которые могут использоваться с iOS, Mac и Android клиенты удаленного рабочего стола. («X» в столбце "Платформа" означает, что атрибут поддерживается. Значения обозначено шевроны (<>) представляют значения, которые поддерживаются клиентов удаленного рабочего стола).

| **Атрибут протокола удаленного рабочего СТОЛА**                                           | **Android** | **Mac** | **iOS** |
|---------------------------------------------------------|---------|-----|-----|
| Разрешить композицию рабочего стола = i:&lt;0 или 1&gt;                    | x       | x   | x   |
| Разрешить сглаживание шрифтов = i:<0 или 1&gt;                         | x       | x   | x   |
| альтернативные оболочки = s:&lt;строки&gt;                              | x       | x   | x   |
| [audiomode = i:&lt;0, 1 или 2&gt;](https://technet.microsoft.com/library/ff393707.aspx)                                | x       | x   | x   |
| [уровень проверки подлинности = i:&lt;0 или 1&gt;](https://technet.microsoft.com/library/ff393709.aspx)                         | x       | x   | x   |
| подключение к консоли = i:&lt;0 или 1&gt;                           | x       | x   | x   |
| отключить параметры курсора = i:&lt;0 или 1&gt;                      | x       | x   | x   |
| отключить перетаскивание всего окна = i:&lt;0 или 1&gt;                     | x       | x   | x   |
| Отключение меню anims: i:&lt;0 или 1&gt;                           | x       | x   | x   |
| Отключение тем = i:&lt;0 или 1&gt;                               | x       | x   | x   |
| отключить фоновый рисунок = i:&lt;0 или 1&gt;                            | x       | x   | x   |
| [drivestoredirect = s: *](https://technet.microsoft.com/library/ff393728(v=ws.10).aspx) (это единственным поддерживаемым значением) | x       | x   |     |
| [desktopheight: i:&lt;значения в пикселях&gt;](https://technet.microsoft.com/library/ff393702.aspx)                       |         | x   |     |
| [desktopwidth: i:&lt;значения в пикселях&gt;](https://technet.microsoft.com/library/ff393697.aspx)                        |         | x   |     |
| [домен = s:&lt;строки&gt;](https://technet.microsoft.com/library/ff393673.aspx)                           | x | x | x |
| [Полный адрес = s:&lt;строки&gt;](https://technet.microsoft.com/library/ff393661.aspx)                     | x | x | x |
| gatewayhostname = s:&lt;строки&gt;                  | x | x | x |
| [gatewayusagemethod = i:&lt;1 или 2&gt;](https://msdn.microsoft.com/aa381329.aspx)               | x | x | x |
| [запрос учетных данных на клиенте = i:&lt;0 или 1&gt;](https://technet.microsoft.com/library/ff393660(v=ws.10).aspx) |   | x |   |
| [loadbalanceinfo = s:&lt;строки&gt;](https://technet.microsoft.com/library/ff393684.aspx)                  | x | x | x |
| [redirectprinters: i:&lt;0 или 1&gt;](https://technet.microsoft.com/library/ff393671(v=ws.10).aspx)                 |   | x |   |
| remoteapplicationcmdline = s:&lt;строки&gt;         | x | x | x |
| remoteapplicationmode = i:&lt;0 или 1&gt;            | x | x | x |
| remoteapplicationprogram = s:&lt;строки&gt;         | x | x | x |
| оболочка рабочий каталог = s:&lt;строки&gt;          | x | x | x |
| Имя сервера использование перенаправления = i:&lt;0 или 1&gt;      | x | x | x |
| [имя пользователя = s:&lt;строки&gt;](https://technet.microsoft.com/library/ff393678.aspx)                         | x | x | x |
| [Идентификатор режима экрана = i:&lt;1 или 2&gt;](https://technet.microsoft.com/library/ff393692.aspx)                   |   | x |   |
| [бит/пкс сеанса = i:&lt;8, 15, 16, 24 или 32&gt;](https://technet.microsoft.com/library/ff393680.aspx)        |   | x |   |
| [Используйте несколько мониторов = i:&lt;0 или 1&gt;](https://technet.microsoft.com/library/ff393695(v=ws.10).aspx)          |   | x |   |