---
title: Схема URI клиенты удаленного рабочего стола
description: Дополнительные сведения о схеме Uniform Resource Identifier для клиентов удаленного рабочего стола
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
ms.openlocfilehash: 86de6468e2fa45c976711aef43a1a274e04498d3
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59870505"
---
# <a name="remote-desktop-client-universal-resource-identifier-uri-scheme-support"></a>Поддерживают клиент удаленного рабочего стола универсальный идентификатор ресурса (URI) схемы

>Область применения. Windows Server версии 1803, Windows Server 2016, Windows Server 2012 R2

С помощью схемы универсального кода ресурса (URI) ИТ-специалисты и разработчики могут интегрировать функции клиентов удаленного рабочего стола на различных платформах, а пользователи получить расширенные возможности благодаря следующему: 

- Сторонние приложения могут запускать удаленный рабочий стол Майкрософт и начинать удаленные сеансы с предопределенными параметрами (указанными в строке URI).
- Конечные пользователи могут запускать удаленные подключения с помощью предварительно настроенных URL-адресов.

>[!NOTE]
> С помощью URI для подключения клиентов к удаленному рабочему Столу не поддерживается для операционных систем Windows — использовать URI с MacOS, iOS и Android.

Удаленный рабочий стол Майкрософт использует rdp://query_string схему URI для хранения параметров предварительно настроенных атрибутов, которые используются при запуске клиента. Строки запросов представляют один атрибут или набор атрибутов RDP, указываемых в URL-адресе. 

Атрибуты RDP разделяются символом амперсанда (&). Например, при подключении к ПК строка имеет следующий вид:

```
rdp://full%20address=s:mypc:3389&audiomode=i:2&disable%20themes=i:1
```

Эта таблица содержит полный список поддерживаемых атрибутов, которые могут использоваться с клиентами удаленных рабочих столов iOS, Mac и Android. ("x" в столбце платформы означает, что атрибут поддерживается. Значения, обозначенные угловыми скобками (<>), представляют значения, поддерживаемые клиентами удаленного рабочего стола.)

| **Атрибут протокола удаленного рабочего СТОЛА**                                           | **Android** | **Mac** | **iOS** |
|---------------------------------------------------------|---------|-----|-----|
| Разрешить композицию рабочего стола = i:&lt;0 или 1&gt;                    | x       | x   | x   |
| Разрешить сглаживание шрифтов = i: < 0 или 1&gt;                         | x       | x   | x   |
| Альтернативный shell = s:&lt;строка&gt;                              | x       | x   | x   |
| [audiomode = i:&lt;0, 1 или 2&gt;](https://technet.microsoft.com/library/ff393707.aspx)                                | x       | x   | x   |
| [уровень проверки подлинности = i:&lt;0 или 1&gt;](https://technet.microsoft.com/library/ff393709.aspx)                         | x       | x   | x   |
| подключение к консоли = i:&lt;0 или 1&gt;                           | x       | x   | x   |
| Отключение параметров курсора = i:&lt;0 или 1&gt;                      | x       | x   | x   |
| отключить перетаскивание окон с содержимым = i:&lt;0 или 1&gt;                     | x       | x   | x   |
| отключить меню anims = i:&lt;0 или 1&gt;                           | x       | x   | x   |
| Отключение тем = i:&lt;0 или 1&gt;                               | x       | x   | x   |
| отключить фоновый рисунок = i:&lt;0 или 1&gt;                            | x       | x   | x   |
| [drivestoredirect=s:*](https://technet.microsoft.com/library/ff393728(v=ws.10).aspx) (это единственное поддерживаемое значение) | x       | x   |     |
| [desktopheight = i:&lt;значение в пикселях&gt;](https://technet.microsoft.com/library/ff393702.aspx)                       |         | x   |     |
| [desktopwidth = i:&lt;значение в пикселях&gt;](https://technet.microsoft.com/library/ff393697.aspx)                        |         | x   |     |
| [домен = s:&lt;строка&gt;](https://technet.microsoft.com/library/ff393673.aspx)                           | x | x | x |
| [Полный адрес = s:&lt;строка&gt;](https://technet.microsoft.com/library/ff393661.aspx)                     | x | x | x |
| gatewayhostname = s:&lt;строка&gt;                  | x | x | x |
| [gatewayusagemethod = i:&lt;1 или 2&gt;](https://msdn.microsoft.com/aa381329.aspx)               | x | x | x |
| [запрос учетных данных на клиенте = i:&lt;0 или 1&gt;](https://technet.microsoft.com/library/ff393660(v=ws.10).aspx) |   | x |   |
| [loadbalanceinfo = s:&lt;строка&gt;](https://technet.microsoft.com/library/ff393684.aspx)                  | x | x | x |
| [redirectprinters = i:&lt;0 или 1&gt;](https://technet.microsoft.com/library/ff393671(v=ws.10).aspx)                 |   | x |   |
| remoteapplicationcmdline = s:&lt;строка&gt;         | x | x | x |
| remoteapplicationmode = i:&lt;0 или 1&gt;            | x | x | x |
| remoteapplicationprogram = s:&lt;строка&gt;         | x | x | x |
| рабочий каталог Shell = s:&lt;строка&gt;          | x | x | x |
| Имя сервера для использования перенаправления = i:&lt;0 или 1&gt;      | x | x | x |
| [имя пользователя = s:&lt;строка&gt;](https://technet.microsoft.com/library/ff393678.aspx)                         | x | x | x |
| [Идентификатор режима экрана = i:&lt;1 или 2&gt;](https://technet.microsoft.com/library/ff393692.aspx)                   |   | x |   |
| [сеанс bpp = i:&lt;8, 15, 16, 24 или 32&gt;](https://technet.microsoft.com/library/ff393680.aspx)        |   | x |   |
| [использовать multimon = i:&lt;0 или 1&gt;](https://technet.microsoft.com/library/ff393695(v=ws.10).aspx)          |   | x |   |