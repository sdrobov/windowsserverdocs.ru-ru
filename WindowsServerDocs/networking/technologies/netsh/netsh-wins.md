---
title: Пример пакетного файла Netsh
description: С помощью этого раздела вы узнаете, как создать пакетный файл, выполняющий несколько задач с помощью команды Netsh в Windows Server 2016.
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: c94e37a4-3637-4613-9eb5-ed604e831eca
manager: brianlic
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 86fbe66978f7c09a332bba16a27a13fa029cb5a6
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71401917"
---
# <a name="network-shell-netsh-example-batch-file"></a>Сетевая оболочка \(Netsh @ no__t-1 Пример пакетного файла

Область применения. Windows Server 2016

В этом разделе вы узнаете, как создать пакетный файл, выполняющий несколько задач с помощью команды Netsh в Windows Server 2016. В этом примере пакетного файла используется контекст **Netsh WINS** .

## <a name="example-batch-file-overview"></a>Пример обзорного пакетного файла

Команды Netsh для службы Windows Internet Name Service \(WINS @ no__t-1 можно использовать в пакетных файлах и других скриптах для автоматизации задач. В следующем примере пакетного файла показано, как использовать команды Netsh для WINS для выполнения различных связанных задач.

В этом примере пакетного файла WINS @ no__t-0A — это WINS-сервер с IP адресом 192.168.125.30, а WINS @ no__t-1B — WINS-сервер с адресом 192.168.0.189.

В примере пакетного файла выполняются следующие задачи.

- Добавляет запись динамического имени с IP-адресом 192.168.0.205, MY @ no__t-0RECORD \[04h @ no__t-2, в WINS @ no__t-3A
- Задает WINS @ no__t-0B в качестве партнера по извещающей или опрашивающей репликации WINS @ no__t-1A
- Подключается к WINS @ no__t-0B, а затем устанавливает WINS @ no__t-1A в качестве партнера по извещающей или опрашивающей репликации WINS @ no__t-2B
- Инициирует извещающую репликацию из WINS @ no__t-0A в WINS @ no__t-1B
- Подключается к WINS @ no__t-0B, чтобы убедиться, что новая запись, MY @ no__t-1RECORD, успешно реплицирована

## <a name="netsh-example-batch-file"></a>Пакетный файл примера Netsh

В следующем примере пакетного файла строки, содержащие комментарии, предшествуют «REM» для замечания. Команда netsh игнорирует комментарии.

    rem: Begin example batch file.
    
    rem two WINS servers:
    
    rem (WINS-A) 192.168.125.30
    
    rem (WINS-B) 192.168.0.189
    
    rem 1. Connect to (WINS-A), and add the dynamic name MY\_RECORD \[04h\] to the (WINS-A) database.
    
    netsh wins server 192.168.125.30 add name Name=MY\_RECORD EndChar=04 IP={192.168.0.205}
    
    rem 2. Connect to (WINS-A), and set (WINS-B) as a push/pull replication partner of (WINS-A).
    
    netsh wins server 192.168.125.30 add partner Server=192.168.0.189 Type=2
    
    rem 3. Connect to (WINS-B), and set (WINS-A) as a push/pull replication partner of (WINS-B).
    
    netsh wins server 192.168.0.189 add partner Server=192.168.125.30 Type=2
    
    rem 4. Connect back to (WINS-A), and initiate a push replication to (WINS-B).
    
    netsh wins server 192.168.125.30 init push Server=192.168.0.189 PropReq=0
    
    rem 5. Connect to (WINS-B), and check that the record MY\_RECORD \[04h\] was replicated successfully.
    
    netsh wins server 192.168.0.189 show name Name=MY\_RECORD EndChar=04
    
    rem 6. End example batch file.

## <a name="netsh-wins-commands-used-in-the-example-batch-file"></a>Команды Netsh WINS, используемые в примере пакетного файла

В следующем разделе перечислены команды **Netsh WINS** , которые используются в этом примере процедуры.

- **сервер**. Сдвигает текущий контекст WINS Command @ no__t-0line на сервер, указанный по имени или IP-адресу.
- **Добавить имя**. Регистрирует имя на WINS-сервере.
- **добавить партнера**. Добавляет партнера репликации на WINS-сервер.
- **init Push**. Инициирует и отправляет принудительный триггер на WINS-сервер.
- **Показывать имя**. Отображает подробные сведения о конкретной записи в базе данных WINS-сервера.  

Дополнительные сведения см. в разделе [Сетевая оболочка (Netsh)](netsh.md).
