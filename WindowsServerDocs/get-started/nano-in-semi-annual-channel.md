---
title: Изменения сервера Nano Server в Semi-Annual Channel для Windows Server
description: В новой модели обслуживания Windows Server сервер Nano Server представляет собой операционную систему контейнера с определенными измененными функциями.
ms.prod: Windows Server
ms.mktglfcycl: manage
ms.sitesec: library
author: jasongerend
ms.author: jgerend
ms.localizationpriority: medium
ms.date: 05/21/2019
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: a270334d-42a7-46ff-8eed-d8656a276544
ms.openlocfilehash: c9fede02b90e285803a8bcdbc983f264d65a4589
ms.sourcegitcommit: c8cc0b25ba336a2aafaabc92b19fe8faa56be32b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/21/2019
ms.locfileid: "65976507"
---
# <a name="changes-to-nano-server-in-windows-server-semi-annual-channel"></a>Изменения сервера Nano Server в Semi-Annual Channel для Windows Server

>Область применения. Windows Server Semi-Annual Channel

Если вы уже используете Nano Server [окно Server Semi-Annual Channel](..\get-started-19\servicing-channels-19.md) модели обслуживания будет знакомой, поскольку он был ранее обслуживаемых Current Branch for Business (CBB) модели. Windows Server Semi-Annual Channel — это просто новое имя для той же модели. В этой модели обновления компонентов сервера Nano Server выходят два-три раза в год.

Тем не менее, начиная с Windows Server версии 1803, Nano Server доступен только в качестве **базовый образ ОС контейнера**. Его необходимо запускать в качестве контейнера в узле контейнера, например как установку основных серверных компонентов Windows Server. Запуск контейнера на основе сервера Nano Server в этом выпуске отличается от его запуска в более ранних выпусках.

- Сервер Nano Server был оптимизирован для приложений .NET Core.
- Сервер Nano Server меньше версии сервера Windows Server 2016.
- PowerShell Core, .NET Core и WMI больше не входят в состав сервера по умолчанию, но вы можете добавить в него пакеты контейнера [.NET Core](https://hub.docker.com/r/microsoft/dotnet/) и [PowerShell Core](https://hub.docker.com/r/microsoft/powershell/) при создании контейнера.
- Обслуживающий стек больше не входит в состав сервера Nano Server. Корпорация Майкрософт публикует обновленный контейнер Nano в Docker Hub, а вы выполняете его повторное развертывание.
- Устранение неполадок с новым контейнером Nano выполняется с помощью Docker.
- Контейнеры Nano теперь можно запускать в среде IoT Базовая.

## <a name="related-topics"></a>См. также

- [Документация по контейнерам Windows](http://aka.ms/windowscontainers)
- [Общие сведения об окне Server Semi-Annual Channel](..\get-started-19\servicing-channels-19.md)
