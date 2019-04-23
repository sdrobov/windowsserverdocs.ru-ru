---
title: Пример пакетного файла Netsh
description: В этом разделе можно использовать, чтобы узнать, как создать пакетный файл, который выполняет несколько задач, с помощью команды Netsh в Windows Server 2016.
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: c94e37a4-3637-4613-9eb5-ed604e831eca
manager: brianlic
ms.author: pashort
author: shortpatti
ms.openlocfilehash: b0528cfaef201ba30e00e30f56a763be39a6b828
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59880175"
---
# <a name="network-shell-netsh-example-batch-file"></a>Сетевой оболочки \(Netsh\) пример пакетного файла

Область применения. Windows Server 2016

В этом разделе можно использовать, чтобы узнать, как создать пакетный файл, который выполняет несколько задач с помощью Netsh в Windows Server 2016. В этом примере пакетного файла **netsh wins** используется контекст.

## <a name="example-batch-file-overview"></a>Общие сведения о примере пакетного файла

Можно использовать команды Netsh для Windows Internet Name Service \(WINS\) пакетных файлов и другие сценарии для автоматизации задач. В следующем примере пакетного файла показано, как использовать команды Netsh для WINS для выполнения широкого круга связанных задач.

В этом примере пакетного файла WINS\-A является WINS-сервер с IP-адресом 192.168.125.30 и WINS\-B является WINS-сервер с IP-адресом 192.168.0.189.

Пример пакетного файла выполняет следующие задачи.

- Добавляет запись динамическое имя с IP-адресом 192.168.0.205, MY\_записи \[04h\], в WINS\-A
- Задает WINS\-B и извещающей партнером репликации WINS\-A
- Подключается к WINS\-B, а затем WINS наборы\-объект как партнер репликации и извещающей WINS\-B
- Инициирует до принудительной репликации с помощью WINS\-объект в WINS\-B
- Подключается к WINS\-B, чтобы убедиться, что новая запись, MY\_записи, успешно реплицировано

## <a name="netsh-example-batch-file"></a>Netsh пример пакетного файла

В следующем примере пакетный файл строки, которые содержат комментарии перед «rem», для заметки. Netsh игнорирует комментарии.

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

## <a name="netsh-wins-commands-used-in-the-example-batch-file"></a>Команды Netsh для WINS, используемых в примере пакетного файла

В следующем разделе перечислены **netsh wins** команды, используемые в этом примере.

- **сервер**. Смещает текущую команду WINS\-контекст строки для сервера, указанного по его имени или IP-адрес.
- **Добавьте имя**. Регистрирует имя на сервере WINS.
- **Добавление партнера**. Добавление партнера репликации WINS-сервера.
- **init push**. Инициализирует и отправляет WINS-сервер с помощью извещающего триггера.
- **Показывать имя**. Отображает подробные сведения для конкретной записи в базе данных сервера WINS.  

Дополнительные сведения см. в разделе [сетевой оболочки (Netsh)](netsh.md).
