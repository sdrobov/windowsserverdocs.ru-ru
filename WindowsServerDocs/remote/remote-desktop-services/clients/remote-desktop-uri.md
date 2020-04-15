---
title: Схема URI для клиентов удаленного рабочего стола
description: Дополнительные сведения о схеме URI для клиентов удаленного рабочего стола
ms.prod: windows-server
ms.technology: remote-desktop-services
ms.topic: article
ms.assetid: 0c3f1eb6-835c-4522-99ff-56c6ee4bb911
author: lizap
manager: dongill
ms.author: elizapo
ms.date: 06/11/2018
ms.localizationpriority: medium
ms.openlocfilehash: 02f970cb2e793c1e342a2818a2bca3900327fa9c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856007"
---
# <a name="remote-desktop-client-universal-resource-identifier-uri-scheme-support"></a>Поддержка схемы URI для клиентов удаленного рабочего стола

>Применяется к: Windows Server, версия 1803, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2

С помощью схемы универсального кода ресурса (URI) ИТ-специалисты и разработчики могут интегрировать функции клиентов удаленного рабочего стола на различных платформах, а пользователи получить расширенные возможности благодаря следующему: 

- Сторонние приложения могут запускать удаленный рабочий стол Майкрософт и начинать удаленные сеансы с предопределенными параметрами (указанными в строке URI).
- Конечные пользователи могут запускать удаленные подключения с помощью предварительно настроенных URL-адресов.

>[!NOTE]
> Использование URI для подключения клиентов к удаленному рабочему столу не поддерживается для операционных систем Windows; используйте URI с MacOS, iOS и Android.

Удаленный рабочий стол Майкрософт использует схему URI rdp://строка_запроса для хранения параметров предварительно настроенных атрибутов, используемых при запуске клиента. Строки запросов представляют один атрибут или набор атрибутов RDP, указываемых в URL-адресе. 

Атрибуты RDP разделяются символом амперсанда (&). Например, при подключении к ПК строка имеет следующий вид:

```
rdp://full%20address=s:mypc:3389&audiomode=i:2&disable%20themes=i:1
```

Эта таблица содержит полный список поддерживаемых атрибутов, которые могут использоваться с клиентами удаленных рабочих столов iOS, Mac и Android. (Символ x в столбце платформы означает, что атрибут поддерживается. Значения, обозначенные угловыми скобками (<>), представляют значения, поддерживаемые клиентами удаленного рабочего стола.)

| **Атрибут протокола удаленного рабочего стола**                                           | **Android** | **Mac** | **iOS** |
|---------------------------------------------------------|---------|-----|-----|
| allow desktop composition=i:&lt;0 или 1&gt;                    | x       | x   | x   |
| allow font smoothing=i:<0 или 1&gt;                         | x       | x   | x   |
| alternate shell=s:&lt;строка&gt;                              | x       | x   | x   |
| [audiomode=i:&lt;0, 1 или 2&gt;](https://technet.microsoft.com/library/ff393707.aspx)                                | x       | x   | x   |
| [authentication level=i:&lt;0 или 1&gt;](https://technet.microsoft.com/library/ff393709.aspx)                         | x       | x   | x   |
| connect to console=i:&lt;0 или 1&gt;                           | x       | x   | x   |
| disable cursor settings=i:&lt;0 или 1&gt;                      | x       | x   | x   |
| disable full window drag=i:&lt;0 или 1&gt;                     | x       | x   | x   |
| disable menu anims=i:&lt;0 или 1&gt;                           | x       | x   | x   |
| disable themes=i:&lt;0 или 1&gt;                               | x       | x   | x   |
| disable wallpaper=i:&lt;0 или 1&gt;                            | x       | x   | x   |
| [drivestoredirect=s:*](https://technet.microsoft.com/library/ff393728(v=ws.10).aspx) (это единственное поддерживаемое значение) | x       | x   |     |
| [desktopheight=i:&lt;значение в пикселях&gt;](https://technet.microsoft.com/library/ff393702.aspx)                       |         | x   |     |
| [desktopwidth=i:&lt;значение в пикселях&gt;](https://technet.microsoft.com/library/ff393697.aspx)                        |         | x   |     |
| [domain=s:&lt;строка&gt;](https://technet.microsoft.com/library/ff393673.aspx)                           | x | x | x |
| [full address=s:&lt;строка&gt;](https://technet.microsoft.com/library/ff393661.aspx)                     | x | x | x |
| gatewayhostname=s:&lt;строка&gt;                  | x | x | x |
| [gatewayusagemethod=i:&lt;1 или 2&gt;](https://msdn.microsoft.com/aa381329.aspx)               | x | x | x |
| [prompt for credentials on client=i:&lt;0 или 1&gt;](https://technet.microsoft.com/library/ff393660(v=ws.10).aspx) |   | x |   |
| [loadbalanceinfo=s:&lt;строка&gt;](https://technet.microsoft.com/library/ff393684.aspx)                  | x | x | x |
| [redirectprinters=i:&lt;0 или 1&gt;](https://technet.microsoft.com/library/ff393671(v=ws.10).aspx)                 |   | x |   |
| remoteapplicationcmdline=s:&lt;строка&gt;         | x | x | x |
| remoteapplicationmode=i:&lt;0 или 1&gt;            | x | x | x |
| remoteapplicationprogram=s:&lt;строка&gt;         | x | x | x |
| shell working directory=s:&lt;строка&gt;          | x | x | x |
| Use redirection server name=i:&lt;0 или 1&gt;      | x | x | x |
| [username=s:&lt;строка&gt;](https://technet.microsoft.com/library/ff393678.aspx)                         | x | x | x |
| [screen mode id=i:&lt;1 или 2&gt;](https://technet.microsoft.com/library/ff393692.aspx)                   |   | x |   |
| [session bpp=i:&lt;8, 15, 16, 24 или 32&gt;](https://technet.microsoft.com/library/ff393680.aspx)        |   | x |   |
| [use multimon=i:&lt;0 или 1&gt;](https://technet.microsoft.com/library/ff393695(v=ws.10).aspx)          |   | x |   |