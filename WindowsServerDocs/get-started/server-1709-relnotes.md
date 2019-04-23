---
title: Заметки о выпуске. Важные проблемы в Windows Server версии 1709
description: Сводные данные о критических проблемах, требующих обходных действий во избежание аварийного завершения, "зависания", ошибки установки и потери данных.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.date: 04/23/2018
ms.technology: server-general
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 134aab85-664f-4d44-87ef-9e5fd389071f
author: jaimeo
ms.author: jaimeo
manager: dougkim
ms.localizationpriority: medium
ms.openlocfilehash: 4eebc498289a81c7f27fcf4b84d81ae13bc38e4f
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59861985"
---
# <a name="release-notes-important-issues-in-windows-server-version-1709"></a>Заметки о выпуске: Важные проблемы в Windows Server версии 1709

>Область применения. Windows Server Semi-Annual Channel

В этих заметках о выпуске приведены сводные данные о наиболее важных проблемах в операционной системе Windows Server&reg;, включая информацию о способах устранения или обхода этих проблем, если таковые известны. Информацию об изменениях структуры, новых компонентах и исправлениях в этом выпуске см. в статье [Новые возможности Windows Server версии 1709](whats-new-in-windows-server-1709.md) и в сообщениях групп разработчиков конкретных компонентов. Если не указано иное, эти заметки распространяются на все выпуски и варианты установки Windows Server2016.  

Этот документ постоянно обновляется. По мере обнаружения критических проблем, определения обходных путей и выпуска исправлений в документ добавляются соответствующие сведения.  
  
## <a name="storage-spaces-direct"></a>Локальные дисковые пространства
[comment]: # (Идентификатор: неизвестный; Отправитель: stevenek; Состояние: выход из)  
Локальные дисковые пространства не входят в состав Windows Server версии 1709. Если вызвать командлет *Enable-ClusterStorageSpacesDirect* или его псевдоним *Enable-ClusterS2D* на сервере с Windows Server версии 1709, отобразится сообщение об ошибке "Запрошенная операция не поддерживается".

Также она не поддерживается при добавлении серверов с Windows Server версии 1709 в среду локальных дисковых пространств Windows Server 2016.

Модель выпуска Windows Server предлагает новый вариант установки с целью обеспечения соответствия сходным моделям выпуска и обслуживания для [Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-overview) и [Office 365 профессиональный плюс](https://support.office.com/article/Overview-of-the-upcoming-changes-to-Office-365-ProPlus-update-management-78b33779-9356-4cdf-9d2c-08350ef05cca?ui=en-US&rs=en-US&ad=US). Выпуски Semi-Annual Channel предоставляют новые возможности пользователям, которым необходимы быстрые циклы обновления, и будут выходить дважды в год — весной и осенью.

Windows Server полугодовой канал предназначен для контейнеров и сценариев приложений, которые используют преимущества ускорит внедрение инноваций, см. в разделе, это [блог](https://cloudblogs.microsoft.com/windowsserver/2018/03/29/windows-server-semi-annual-channel-update) Дополнительные сведения. Клиенты, которым для ролей инфраструктуры, такие как дисковыми пространствами, следует использовать Long-Term Servicing Channel версий, например Windows Server 2016 (доступных сейчас) и [Windows Server 2019](https://cloudblogs.microsoft.com/windowsserver/2018/03/20/introducing-windows-server-2019-now-available-in-preview) (ожидается в этом году). Мы стремимся к созданию лучшей платформой для гиперконвергентной инфраструктуры, и мы продолжим для разработки новых компонентов и улучшения существующих на основе ваших отзывов. 

Локальные дисковые пространства впервые появились в Windows Server 2016 являются основанием для нашей гиперконвергентной платформы. Мы рады тому, насколько положительно пользователи приняли гиперконвергентную платформу Майкрософт, и делаем для них все возможное.

Мы прислушиваемся к вашим отзывам и работаем для доставки [следующий набор инновации](https://blogs.technet.microsoft.com/windowsserver/2017/09/07/sneak-peek-2-windows-server-version-1709-hyper-converged-infrastructure/) для нашей платформы гиперконвергентной. Эти функции доступны сегодня в [участников программы предварительной оценки Windows](https://insider.windows.com/for-business/) сборки и мы будем рады попробовать их и поделитесь своим мнением. Клиентам, которым нужно проверенное гиперконвергентное решение, мы рекомендуем программу [Windows Server Software Defined](http://microsoft.com/wssd).
