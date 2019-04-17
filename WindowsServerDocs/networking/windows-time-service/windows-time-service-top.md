---
ms.assetid: e34622ff-b2d0-4f81-8d00-dacd5d6c215e
title: Служба времени Windows
description: ''
author: shortpatti
ms.author: pashort
manager: brianlic
ms.date: 02/01/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: b997d1f26e8da82e0d595b1ce13763e0a87d6d03
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="windows-time-service-w32time"></a>Служба времени Windows (W32Time).

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Служба времени Windows (W32Time) синхронизирует дату и время для всех компьютеров, работающих в доменных службах Active Directory (AD DS). Синхронизация времени очень важно для правильной работы многих служб Windows и приложений на бизнес (LOB). Служба времени Windows использует протокола сетевого времени (NTP) для синхронизации часов компьютера в сети. NTP гарантирует, что точное значение или метку времени, могут быть назначены сетевые запросы доступа проверки и ресурсов.

В разделе службы времени Windows (W32Time) доступен следующее содержимое:
- **[Точное время в Windows 2016](accurate-time.md).** Точность синхронизация времени в Windows Server 2016 была улучшена существенно, сохраняя полностью обратно NTP совместимость с предыдущими версиями Windows.  При разумных рабочих условиях позволяет поддерживать 1 точность мс относительно времени UTC или лучше для членов домена Windows Server 2016 и Windows 10 Anniversary Update.
- **[Технический справочник службы времени Windows ](windows-time-service-tech-ref.md).** Служба W32Time предоставляет синхронизации часов сети для компьютеров без необходимости детальная настройка. Служба W32Time важно для успешной операции проверки подлинности Kerberos V5 и, следовательно, для проверки подлинности на основе доменных служб Active Directory AD.
    - **[Принцип работы службы времени Windows ](How-the-Windows-Time-Service-Works.md).** Несмотря на то, что служба времени Windows не точное реализация протокола сетевого времени (NTP), он использует сложного набора алгоритмов, определенный в спецификации NTP для обеспечения максимальной точности часы на компьютерах в сети.
    - **[Служба времени Windows средства и параметры службы ](Windows-Time-Service-Tools-and-Settings.md).** Большинство компьютеров домена имеют тип клиента времени NT5DS, это означает, что они синхронизацию времени в иерархии домена. Только типичные исключения — контроллер домена, который работает в качестве основного домена (PDC) контроллеру хозяин операций эмулятора корневого домена леса, как правило, настроенное для синхронизации времени с внешним источником времени.

## <a name="related-topics"></a>Связанные разделы
Дополнительные сведения об иерархии доменов и системы игры см. в разделе [«Что такое служба времени Windows»](https://blogs.msdn.microsoft.com/w32time/2007/07/07/what-is-windows-time-service/) записи блога.

Поставщик подключаемого модуля windows времени модель [описаны на портале TechNet](https://msdn.microsoft.com/en-us/library/windows/desktop/ms725475%28v=vs.85%29.aspx).

Дополнение ссылается статье времени точность 2016 Windows можно загрузить [здесь](http://windocs.blob.core.windows.net/windocs/WindowsTimeSyncAccuracy_Addendum.pdf)

Краткий обзор службы времени Windows, взгляните на это [общий обзор видео ](https://aka.ms/WS2016TimeVideo).

<!-- In this guide
In this guide:
Windows Accurate Time
High Accuracy
Support Boundary
Configuration for High Accuracy
Traceability for Compliance
Best Practices
Technical Reference
How the Windows Time Service Works
Windows Time Service Tools and Settings
-->

