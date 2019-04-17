---
title: Сетевой оболочки (Netsh) пример пакетного файла
description: В этом разделе можно использовать, чтобы узнать, как создать пакетный файл, который выполняет несколько задач, с помощью Netsh в Windows Server 2016.
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: c94e37a4-3637-4613-9eb5-ed604e831eca
manager: brianlic
ms.author: pashort
author: shortpatti
ms.openlocfilehash: b0528cfaef201ba30e00e30f56a763be39a6b828
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="network-shell-netsh-example-batch-file"></a>Сетевой оболочки \(Netsh\) пример пакетного файла

Область применения: Windows Server 2016

В этом разделе можно использовать, чтобы узнать, как создать пакетный файл, который выполняет несколько задач с помощью Netsh в Windows Server 2016. В этом примере пакетный файл **netsh wins** используется контекст.

## <a name="example-batch-file-overview"></a>Общие сведения о примере пакетного файла

Можно использовать команды Netsh для \(WINS\) служба WINS в пакетных файлов и других сценариев для автоматизации задач. В следующем примере пакетного файла показано, как использовать команды Netsh для WINS для выполнения различных задач, связанных.

В этом примере пакетный файл WINS\ A WINS-сервер с IP-адресом 192.168.125.30 и WINS\-B — это сервер WINS, с IP-адресом 192.168.0.189.

Пример пакетного файла выполняет следующие задачи.

- Добавляет запись динамических имен с IP-адресом 192.168.0.205, MY\_RECORD \[04h\], в WINS\-A
- Задает WINS\ B в качестве партнера репликации и извещающей WINS\-a
- Подключается к WINS\ B, а затем устанавливает WINS\-A как партнер репликации push и pull WINS\ B
- Инициирует принудительной репликации с WINS\ WINS\ B
- Подключается к WINS\-B, чтобы проверить, успешно реплицированы новой записи MY\_RECORD,

## <a name="netsh-example-batch-file"></a>Netsh пример пакетного файла

В следующем примере файла пакета строки, содержащие комментарии перед «rem», для замечания. Netsh игнорирует комментарии.

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

## <a name="netsh-wins-commands-used-in-the-example-batch-file"></a>Команды Netsh для WINS, используемых в этом примере пакетном файле

В следующем разделе перечислены **netsh wins** команды, используемые в данном примере.

- **сервер**. Переход из текущего контекста командной строки WINS серверу, указанному в имени или IP-адрес.
- **Добавьте имя**. Регистрирует имя на сервере WINS.
- **Добавление партнера**. Добавление партнера репликации на сервере WINS.
- **init push**. Инициирует и отправляет триггер push WINS-сервера.
- **Отображение имени**. Отображает подробные сведения для конкретной записи в базе данных сервера WINS.  

Дополнительные сведения см. в разделе [сетевой оболочки (Netsh)](netsh.md).
