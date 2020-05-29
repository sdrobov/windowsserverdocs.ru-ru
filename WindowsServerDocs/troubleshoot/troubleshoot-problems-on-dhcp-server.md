---
title: Устранение неполадок DHCP-сервера
description: В этом артилцее объясняется, как устранять неполадки на DHCP-сервере и получать данные.
ms.prod: windows-server
ms.service: na
manager: dcscontentpm
ms.technology: server-general
ms.date: 5/26/2020
ms.topic: article
author: Deland-Han
ms.author: delhan
ms.openlocfilehash: ad70b03fcb6d703a0b99435ee8715319d09af941
ms.sourcegitcommit: ef089864980a1d4793a35cbf4cbdd02ce1962054
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/28/2020
ms.locfileid: "84150202"
---
# <a name="troubleshoot-problems-on-the-dhcp-server"></a>Устранение неполадок DHCP-сервера

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
В зависимости от типа проблемы событие регистрируется в одном из следующих каналов событий:  
[Операционные события DHCP-сервера](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn800668\(v=ws.11\))  
[Административные события DHCP-сервера](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn800668\(v=ws.11\))  
[Системные события DHCP-сервера](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn800668\(v=ws.11\))  
[События уведомлений фильтра DHCP-сервера](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn800668\(v=ws.11\))  
[События аудита DHCP-сервера](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn800668\(v=ws.11\))

## <a name="data-collection"></a>сбор данных

### <a name="dhcp-server-log"></a>Журнал DHCP-сервера

Журналы отладки службы DHCP-сервера содержат дополнительные сведения о назначении аренды IP-адресов и динамические обновления DNS, которые выполняются DHCP-сервером. Эти журналы по умолчанию расположены в папке% WINDIR% \\ system32 \\ DHCP.  
Дополнительные сведения см. в разделе [Анализ файлов журнала DHCP-сервера](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd183591\(v=ws.10\)).

### <a name="network-trace"></a>Трассировка сети

Корреляция трассировки сети может означать, что DHCP-сервер выполнялся в момент записи события в журнал. Чтобы создать такую трассировку, выполните следующие действия.

1.  Перейдите в [GitHub](https://github.com/CSS-Windows/WindowsDiag/tree/master/ALL/TSS)и скачайте zip-файл [Тсс \_ Tools.](https://github.com/CSS-Windows/WindowsDiag/blob/master/ALL/TSS/tss_tools.zip)

2.  Скопируйте файл Тсс \_ Tools. zip и разверните его в расположение на локальном диске, например в папку C: \\ Tools.

3.  Выполните следующую команду из раздела C: \\ Tools в окне командной строки с повышенными привилегиями:  
    ```console
    TSS Ron Trace <Stop:Evt:>20321:<Other:>DhcpAdminEvents NoSDP NoPSR NoProcmon NoGPresult
    ```
      
    >[!Note]
    >В этой команде замените \<*Stop:Evt:*\> и \<*Other:*\> идентификатором события и каналом событий, на который вы будете сосредоточиться в сеансе трассировки.  
    >Файл readme. docx-файлы справки ТСС. cmd \_ \_ , содержащийся в \_ файле Тсс Tools. zip, содержит дополнительные сведения обо всех доступных параметрах.

4.  После запуска события средство создает папку с именем C: \\ MS \_ Data. В этой папке будут содержаться полезные выходные файлы, содержащие общие сведения о конфигурации сети и домена компьютера.  
    Наиболее интересным файлом в этой папке является% ComputerName% \_ Date \_ Time \_ packetcapture \_ InternetClient \_ dbg. ETL.
    С помощью приложения [сетевой монитор](https://www.microsoft.com/download/4865) можно загрузить файл и установить фильтр просмотра для протокола DHCP или DNS, чтобы проверить, что происходит в фоновом режиме.
