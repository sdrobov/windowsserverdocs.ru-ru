---
title: Microsoft Server Performance Advisor
description: Microsoft Server Performance Advisor
ms.assetid: 468ebcb3-9eaf-477c-ab10-e3f1b3ce63dc
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: manage
ms.openlocfilehash: ab124f3efabf2ac3ae8904157a81587c0c21ebb5
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59856335"
---
# <a name="microsoft-server-performance-advisor"></a>Microsoft Server Performance Advisor

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Скачайте Microsoft Server Советник по производительности (SPA) для диагностики проблем производительности в Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 или Windows Server 2008 развертывания. SPA создает подробные диагностические отчеты и диаграммы и предоставляет рекомендации для быстрого анализа проблемы и разработки корректирующие действия.

-   [Общие сведения о Server Performance Advisor](#bkmk-aboutspa)

-   [Скачайте Server Performance Advisor](#bkmk-downloadspa)

-   [Руководство пользователя для сервера производительность ядра СУБД](server-performance-advisor-users-guide.md)

-   [Руководство по разработке пакетов в помощник по производительности сервера](server-performance-advisor-pack-development-guide.md)

## <a href="" id="bkmk-aboutspa"></a>Общие сведения о Server Performance Advisor

Server Performance Advisor состоит из двух частей платформы одностраничных ПРИЛОЖЕНИЙ и пакетов Advisor SPA.

### <a name="the-server-performance-advisor-framework"></a>Платформа Server Performance Advisor

Механизм, который отвечает за сбор данных, установленный в пакеты advisor, записи собранных данных в базу данных Microsoft SQL Server, создание среды для запуска скриптов для пакетов Advisor SPA ориентированная на ИТ и отображение финальных отчетов. Необходимо только установить платформы одностраничных ПРИЛОЖЕНИЙ на консоли SPA. Консоль SPA может быть установлен на отдельном компьютере удаленно обращаться к серверам при тестировании или установить на сервере при тестировании.

### <a name="server-performance-advisor-packs"></a>Пакеты Server Performance Advisor

Пакеты Advisor SPA находятся в центре настройки правил, которые состоят из ряда метаданные и файлы скриптов SQL. SPA поставляется с Advisor следующие пакеты:

-   Пакет операционной системы Core advisor анализирует производительность операционной системы, общие функции, независимо от специализированных серверных ролей.

-   Пакет advisor Internet Information Server (IIS) отслеживает производительность служб IIS.

-   Пакет Hyper-V Advisor анализирует общую производительность роли сервера Hyper-V.

    **Примечание** пакет помощник по Hyper-V не анализирует гостевых операционных систем.

     

-   Пакет помощник по active directory анализирует общую производительность роли active directory.

SPA также предлагает расширяемой модели для сторонних разработчиков для записи пакетов advisor в соответствии с их потребностями.

**Примечание** SPA не удалось понять все контексты сценарий оборудования и пользователем. Следует использовать рекомендации, которые предоставляются с помощью средства помогут вам принимать решения и неясны последствия любые потенциальные изменения, внесенные на серверы.

 

## <a href="" id="bkmk-downloadspa"></a>Скачайте Server Performance Advisor


Используйте следующие ссылки для загрузки сервера производительности ядра СУБД для Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 или Windows Server 2008:

-   [Microsoft Server Performance Advisor 3.1 (32-разрядная версия)](https://go.microsoft.com/fwlink/p/?linkid=327751)

-   [Microsoft Server Performance Advisor 3.1 (64-разрядная версия)](https://go.microsoft.com/fwlink/p/?linkid=327752)

Можно извлечь файлы в CAB-файл, используя следующие команды:

-   для x86 версии: `extrac32.exe /e /a /l  d:\SPA   d:\SPA\SPAPlus\_x86.cab`

-   для x64 версии: `extrac32.exe /e /a /l  d:\SPA   d:\SPA\SPAPlus\_amd64.cab`

**Внимание** при извлечении CAB-файла, одностраничного приложения должны сохранять иерархической структуре каталогов для правильной работы. В зависимости от средства CAB-файлов, установленных на сервере извлечения может привести структуру каталогов в нерабочем состоянии. Чтобы сохранить иерархической структуре каталогов, можно использовать средство извлечения служебная программа CAB-файла, который извлекает структуру каталогов файл.

Если средство извлечения CAB правильно извлечены файлы, вложенные папки будут автоматически отображаться в целевой папке извлечения.

### <a name="spa-prerequisites"></a>Предварительные требования SPA

Консоль одностраничных ПРИЛОЖЕНИЙ требуется следующее программное обеспечение:

-   Microsoft .NET Framework 4

-   SQL Server 2008 R2 Express с пакетом обновления 1 или Microsoft SQL Server 2008 R2 с пакетом обновления 1

Более новые версии могут быть совместимы. Все известные продукта несовместимости с SPA консоли будет указано.
