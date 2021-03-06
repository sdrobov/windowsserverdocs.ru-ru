---
title: Устранение неполадок на сервере DHCP
description: В этом артилцее объясняется, как устранять неполадки на DHCP-сервере и получать данные.
ms.prod: windows-server
ms.service: na
manager: dcscontentpm
ms.technology: server-general
ms.date: 5/26/2020
ms.topic: article
author: Deland-Han
ms.author: delhan
ms.openlocfilehash: 5ec2ef358cfaf7841b093843848f2ea5ee42433e
ms.sourcegitcommit: d99bc78524f1ca287b3e8fc06dba3c915a6e7a24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/27/2020
ms.locfileid: "87181900"
---
# <a name="troubleshoot-problems-on-the-dhcp-server"></a>Устранение неполадок на сервере DHCP

В этой статье описывается, как устранять неполадки, возникающие на DHCP-сервере.

## <a name="troubleshooting-checklist"></a>Контрольный список по устранению неполадок

Проверьте следующие настройки.

  - Служба DHCP-сервера запущена и запущена. Чтобы проверить этот параметр, выполните команду **net start** и найдите **DHCP-сервер**.

  - DHCP-сервер является полномочным. См. раздел [авторизация DHCP-сервера Windows в сценарии присоединения к домену](https://docs.microsoft.com/openspecs/windows_protocols/ms-dhcpe/56f8870b-a7c1-4db1-8a86-f69079fe5077).

  - Убедитесь, что аренда IP-адресов доступна в области DHCP-сервера для подсети, в которой находится клиент DHCP. Для этого см. статистику для соответствующей области в консоли управления DHCP-сервером.

  - Проверьте \_ , можно ли найти в аренде адресов НЕдопустимые списки адресов.

  - Проверьте, имеют ли устройства в сети статические IP-адреса, которые не были исключены из области DHCP.

  - Убедитесь, что IP-адрес, с которым связан DHCP-сервер, находится в подсети областей, из которых должны быть арендованы IP-адреса. Это происходит, если агент ретрансляции недоступен. Для этого выполните командлет **Get-DhcpServerv4Binding** или **Get-DhcpServerv6Binding** .

  - Убедитесь, что только DHCP-сервер прослушивает порт UDP 67 и 68. Никакие другие процессы и другие службы (такие как WDS или PXE) не должны занимать эти порты. Для этого выполните `netstat -anb` команду.

  - Убедитесь, что исключение IPsec-сервера Добавлено при работе с средой, развернутой по протоколу IPsec.

  - Убедитесь, что IP-адрес агента ретранслятора можно проверить с DHCP-сервера.

  - Перечисление и Проверка настроенных политик и фильтров DHCP.

## <a name="event-logs"></a>Журналы событий

Проверьте журналы событий службы "система и DHCP-сервер" (**журналы приложений и служб** \> **Microsoft** \> **Windows** \> **DHCP-сервер**), чтобы сообщить о проблемах, связанных с наблюдаемой проблемой.
В зависимости от типа проблемы событие заносится в журнал для одного из следующих каналов событий: DHCP- [сервер: рабочие](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn800668\(v=ws.11\))события DHCP-сервер события административных событий DHCP-сервера системные события оповещения DHCP-сервер события 
 [DHCP Server Administrative Events](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn800668\(v=ws.11\)) 
 [DHCP Server System Events](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn800668\(v=ws.11\)) 
 [DHCP Server Filter Notification Events](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn800668\(v=ws.11\)) 
 [аудита DHCP-сервера](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn800668\(v=ws.11\))

## <a name="data-collection"></a>сбор данных

### <a name="dhcp-server-log"></a>Журнал DHCP-сервера

Журналы отладки службы DHCP-сервера содержат дополнительные сведения о назначении аренды IP-адресов и динамические обновления DNS, которые выполняются DHCP-сервером. Эти журналы по умолчанию расположены в папке% WINDIR% \\ system32 \\ DHCP.
Дополнительные сведения см. в разделе [Анализ файлов журнала DHCP-сервера](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd183591\(v=ws.10\)).

### <a name="network-trace"></a>Трассировка сети

Корреляция трассировки сети может означать, что DHCP-сервер выполнялся в момент записи события в журнал. Чтобы создать такую трассировку, выполните следующие действия.

1.  Перейдите в [GitHub](https://github.com/CSS-Windows/WindowsDiag/tree/master/ALL/TSS)и скачайте файл [ \_tools.zipТсс](https://github.com/CSS-Windows/WindowsDiag/blob/master/ALL/TSS/tss_tools.zip) .

2.  Скопируйте \_ файлtools.zip Тсс и разверните его в расположении на локальном диске, например в папке C: \\ Tools.

3.  Выполните следующую команду из раздела C: \\ Tools в окне командной строки с повышенными привилегиями:
    ```console
    TSS Ron Trace <Stop:Evt:>20321:<Other:>DhcpAdminEvents NoSDP NoPSR NoProcmon NoGPresult
    ```

    >[!Note]
    >В этой команде замените \<*Stop:Evt:*\> и \<*Other:*\> идентификатором события и каналом событий, на который вы будете сосредоточиться в сеансе трассировки.
    >Файл readme ТСС. \_ cmd \_Help.docx файлы, содержащиеся в файле Тсс \_tools.zip, содержат дополнительные сведения обо всех доступных параметрах.

4.  После запуска события средство создает папку с именем C: \\ MS \_ Data. В этой папке будут содержаться полезные выходные файлы, содержащие общие сведения о конфигурации сети и домена компьютера.
    Наиболее интересным файлом в этой папке является% ComputerName% \_ Date \_ Time \_ packetcapture \_ InternetClient \_ dbg. ETL.
    С помощью приложения [сетевой монитор](https://www.microsoft.com/download/4865) можно загрузить файл и установить фильтр просмотра для протокола DHCP или DNS, чтобы проверить, что происходит в фоновом режиме.
