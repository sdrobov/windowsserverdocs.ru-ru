---
title: Изменения сервера Nano Server в Semi-Annual Channel для Windows Server
description: В новой модели обслуживания Windows Server сервер Nano Server представляет собой операционную систему контейнера с определенными измененными функциями.
ms.prod: Windows Server
ms.mktglfcycl: manage
ms.sitesec: library
author: jaimeo
ms.localizationpriority: medium
ms.date: 05/02/2018
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: a270334d-42a7-46ff-8eed-d8656a276544
ms.openlocfilehash: 7e68d292c32ce58c786a3242203330fcae985913
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59847775"
---
# <a name="changes-to-nano-server-in-windows-server-semi-annual-channel"></a>Изменения сервера Nano Server в Semi-Annual Channel для Windows Server

>Область применения. Windows Server Semi-Annual Channel


Как описано в [обзоре канала Semi-Annual Channel для Window Server](semi-annual-channel-overview.md), Windows Server версии 1803 — это последний выпуск в рамках модели обслуживания Semi-Annual Channel.

Если вы уже используете сервер Nano Server, эта модель обслуживания вам будет знакома, так как его обслуживание уже проводилось в рамках модели Current Branch for Business (CBB). Новый канал Semi-Annual Channel для Windows Server — это просто новое имя той же модели. В этой модели обновления компонентов сервера Nano Server выходят два-три раза в год.

Тем не менее, начиная с выпуска Windows Server версии 1803, сервер Nano Server будет доступен только в качестве **базового образа ОС контейнера**. Его необходимо запускать в качестве контейнера в узле контейнера, например как установку основных серверных компонентов Windows Server. Запуск контейнера на основе сервера Nano Server в этом выпуске отличается от его запуска в более ранних выпусках.

- Сервер Nano Server был оптимизирован для приложений .NET Core.
- Сервер Nano Server меньше версии сервера Windows Server 2016.
- PowerShell Core, .NET Core и WMI больше не входят в состав сервера по умолчанию, но вы можете добавить в него пакеты контейнера [.NET Core](https://hub.docker.com/r/microsoft/dotnet/) и [PowerShell Core](https://hub.docker.com/r/microsoft/powershell/) при создании контейнера.
- Обслуживающий стек больше не входит в состав сервера Nano Server. Корпорация Майкрософт публикует обновленный контейнер Nano в Docker Hub, а вы выполняете его повторное развертывание.
- Устранение неполадок с новым контейнером Nano выполняется с помощью Docker.
- Контейнеры Nano теперь можно запускать в среде IoT Базовая.

## <a name="related-topics"></a>См. также
После запуска программы предварительной оценки Windows дополнительные сведения можно найти в [документации по контейнерам Windows](http://aka.ms/windowscontainers).
