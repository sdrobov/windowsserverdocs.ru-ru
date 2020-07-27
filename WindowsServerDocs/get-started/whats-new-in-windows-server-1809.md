---
title: Новые возможности Windows Server версии 1809
description: Новые возможности в Windows Server версии 1809
ms.prod: windows-server
ms.technology: server-general
ms.topic: article
author: jasongerend
ms.author: jgerend
ms.date: 05/21/2019
ms.localizationpriority: high
ms.openlocfilehash: e94bb064b94c657d5e931363e2dc0a1c54ecf5e1
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86956076"
---
# <a name="whats-new-in-windows-server-version-1809"></a>Новые возможности Windows Server версии 1809

>Область применения. Windows Server (Semi-Annual Channel)

Подробные сведения о новых возможностях Windows приведены в этой [статье](whats-new-in-windows-server.md). В этом разделе описаны некоторые новые функции в Windows Server версии 1809.

## <a name="container-networking-with-kubernetes"></a>Работа с сетевыми подключениями контейнеров с помощью Kubernetes

[Средства работы с сетевыми подключениями контейнеров с использованием Kubernetes](../networking/sdn/technologies/containers/container-networking-overview.md) в Windows Server 2019 значительно повышают удобство использования Kubernetes в Windows за счет улучшения устойчивости сети платформы и поддержки подключаемых модулей сетевых подключениях контейнеров. Кроме того, встроенные инструменты позволяют обеспечить сетевую безопасность служб Linux и Windows в рабочих нагрузках, развертываемых на платформе Kubernetes.

## <a name="group-managed-service-accounts-for-containers"></a>Групповые управляемые учетные записи служб для контейнеров

В Windows Server версии 1809 улучшена масштабируемость и надежность контейнеров, которые используют групповые управляемые учетные записи служб (gMSA) для доступа к сетевым ресурсам. 

## <a name="host-device-access-for-containers"></a>Доступ к главному устройству для контейнеров

Вы можете назначать простые шины контейнерам Windows Server с изолированными процессами. Приложения, работающие в контейнерах, которым необходимо взаимодействовать по SPI, I2C, GPIO и UART/COM, теперь могут делать это.

## <a name="additional-features"></a>Дополнительные возможности
В дополнение к функциям, которые появились в Windows Server версии 1809, следующие новые функции и возможности для [Windows Server 2019](../get-started-19/get-started-19.md) также применимы к Windows Server версии 1809:

* Улучшения контейнеров
* HTTP/2
* Поддержка Kubernetes
* Контейнеры Linux в Windows
* [Передача данных с помощью алгоритма Low Extra Delay Background Transport (LEDBAT)](https://techcommunity.microsoft.com/t5/networking-blog/bg-p/NetworkingBlog)
* Повышение производительности сети для виртуальных рабочих нагрузок
* [Функция совместимости приложений основных серверных компонентов по запросу (FOD)](../get-started-19/install-fod-19.md)
* [Служба миграции хранилища (SMS)](../storage/whats-new-in-storage.md#storage-spaces-direct)
* Реплика хранилища
* Системная аналитика 
* Advanced Threat Protection в Защитнике Windows (ATP)
* Exploit Guard для ATP в Защитнике Windows
* [Служба времени Windows](../networking/windows-time-service/insider-preview.md)
