---
title: Настройка параметров производительности файловых серверов
description: Настройка параметров производительности для файловых серверов под управлением Windows Server
ms.prod: windows-server-threshold
ms.technology: performance-tuning-guide
ms.topic: article
author: phstee
ms.author: NedPyle; Danlo; DKruse
ms.date: 4/14/2017
ms.openlocfilehash: dc8a845a6d352fa03517e2a092c44b6d1c1def4b
ms.sourcegitcommit: 6ef4986391607bb28593852d06cc6645e548a4b3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66811465"
---
# <a name="performance-tuning-for-file-servers"></a>Настройка параметров производительности файловых серверов

Следует правильно выбирать оборудование в соответствии с ожидаемой нагрузкой на файловый сервер и с учетом таких параметров, как средняя и пиковая нагрузка, емкость, планы развития и время отклика. Аппаратные ограничения снижают эффективность программной настройки.

## <a name="general-tuning-parameters-for-clients"></a>Общие параметры для настройки клиентов

Следующие параметры реестра REG\_DWORD могут влиять на производительность клиентских компьютеров, которые взаимодействуют с файловыми серверами SMB:

-   **ConnectionCountPerNetworkInterface**

    ```
    HKLM\System\CurrentControlSet\Services\LanmanWorkstation\Parameters\ConnectionCountPerNetworkInterface
    ```

    Область применения: Windows 10, Windows 8.1, Windows 8, Windows Server 2016, Windows Server 2012 R2 и Windows Server 2012

    По умолчанию имеет значение 1, которое мы настоятельно рекомендуем использовать. Допускаются значения от 1 до 16. Максимальное число подключений к серверу по одному интерфейсу, отличающемуся от интерфейсов RSS.


-   **ConnectionCountPerRssNetworkInterface**

    ```
    HKLM\System\CurrentControlSet\Services\LanmanWorkstation\Parameters\ConnectionCountPerRssNetworkInterface
    ```

    Область применения: Windows 10, Windows 8.1, Windows 8, Windows Server 2016, Windows Server 2012 R2 и Windows Server 2012

    По умолчанию имеет значение 4, которое мы настоятельно рекомендуем использовать. Допускаются значения от 1 до 16. Максимальное число подключений к серверу по одному интерфейсу RSS.

-   **ConnectionCountPerRdmaNetworkInterface**

    ```
    HKLM\System\CurrentControlSet\Services\LanmanWorkstation\Parameters\ConnectionCountPerRdmaNetworkInterface
    ```

    Область применения: Windows 10, Windows 8.1, Windows 8, Windows Server 2016, Windows Server 2012 R2 и Windows Server 2012

    По умолчанию имеет значение 2, которое мы настоятельно рекомендуем использовать. Допускаются значения от 1 до 16. Максимальное число подключений к серверу по одному интерфейсу RDMA.

-   **MaximumConnectionCountPerServer**

    ```
    HKLM\System\CurrentControlSet\Services\LanmanWorkstation\Parameters\MaximumConnectionCountPerServer
    ```

    Область применения: Windows 10, Windows 8.1, Windows 8, Windows Server 2016, Windows Server 2012 R2 и Windows Server 2012

    По умолчанию имеет значение 32. Допускаются значения от 1 до 64. Максимальное число подключений к серверу под управлением Windows Server 2012 по всем интерфейсам.

-   **DormantDirectoryTimeout**

    ```
    HKLM\System\CurrentControlSet\Services\LanmanWorkstation\Parameters\DormantDirectoryTimeout
    ```

    Область применения: Windows 10, Windows 8.1, Windows 8, Windows Server 2016, Windows Server 2012 R2 и Windows Server 2012

    По умолчанию имеет значение 600 секунд. Максимальное время, в течение которого сервер сохраняет открытыми дескрипторы каталогов с арендой каталогов.

-   **FileInfoCacheLifetime**

    ```
    HKLM\System\CurrentControlSet\Services\LanmanWorkstation\Parameters\FileInfoCacheLifetime
    ```

    Область применения: Windows 10, Windows 8.1, Windows 8, Windows 7, Windows Vista, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 и Windows Server 2008

    Значение по умолчанию — 10 секунд. Срок хранения в кэше сведений о файлах.

-   **DirectoryCacheLifetime**

    ```
    HKLM\System\CurrentControlSet\Services\LanmanWorkstation\Parameters\DirectoryCacheLifetime
    ```

    Область применения: Windows 10, Windows 8.1, Windows 8, Windows 7, Windows Vista, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 и Windows Server 2008

    Значение по умолчанию — 10 секунд. Обозначает срок хранения кэша каталогов.

    > [!NOTE]
    > Этот параметр управляет кэшированием метаданных каталогов при отсутствии аренды каталогов.
     

-   **DirectoryCacheEntrySizeMax**

    ```
    HKLM\System\CurrentControlSet\Services\LanmanWorkstation\Parameters\DirectoryCacheEntrySizeMax
    ```

    Область применения: Windows 10, Windows 8.1, Windows 8, Windows 7, Windows Vista, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 и Windows Server 2008

    По умолчанию имеет значение 64 КБ. Обозначает максимальный размер записей в кэше каталога.

-   **FileNotFoundCacheLifetime**

    ```
    HKLM\System\CurrentControlSet\Services\LanmanWorkstation\Parameters\FileNotFoundCacheLifetime
    ```

    Область применения: Windows 10, Windows 8.1, Windows 8, Windows 7, Windows Vista, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 и Windows Server 2008

    Значение по умолчанию — 5 секунд. Обозначает срок хранения в кэше данных об отсутствии файла.

-   **CacheFileTimeout**

    ```
    HKLM\System\CurrentControlSet\Services\LanmanWorkstation\Parameters\CacheFileTimeout
    ```

    Область применения: Windows 8.1, Windows 8, Windows Server 2012, Windows Server 2012 R2 и Windows 7

    Значение по умолчанию — 10 секунд. Этот параметр определяет время (в секундах), в течение которого перенаправитель сохраняет кэшированные данные о файле после закрытия в приложении последнего дескриптора для этого файла.

-   **DisableBandwidthThrottling**

    ```
    HKLM\System\CurrentControlSet\Services\LanmanWorkstation\Parameters\DisableBandwidthThrottling
    ```

    Область применения: Windows 10, Windows 8.1, Windows 8, Windows 7, Windows Vista, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 и Windows Server 2008

    Значение по умолчанию — 0. По умолчанию перенаправитель SMB регулирует пропускную способность для сетевых подключений с высокой задержкой, что позволяет в некоторых случаях избежать превышения времени ожидания, связанного с сетью. Значение 1 для этого параметра реестра отключает такое регулирование, ускоряя передачу файлов через сетевые соединения с высокой задержкой.

-   **DisableLargeMtu**

    ```
    HKLM\System\CurrentControlSet\Services\LanmanWorkstation\Parameters\DisableLargeMtu
    ```

    Область применения: Windows 10, Windows 8.1, Windows 8, Windows 7, Windows Vista, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 и Windows Server 2008

    По умолчанию имеет значение 0 только для Windows 8. В Windows 8 перенаправитель SMB передает полезные данные размером до 1 МБ на один запрос, ускоряя передачу файлов. Значение 1 для этого параметра ограничивает запросы размером 64 КБ. Следует тщательно оценить влияние этого параметра, прежде чем применять его.

-   **RequireSecuritySignature**

    ```
    HKLM\System\CurrentControlSet\Services\LanmanWorkstation\Parameters\RequireSecuritySignature
    ```

    Область применения: Windows 10, Windows 8.1, Windows 8, Windows 7, Windows Vista, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 и Windows Server 2008

    По умолчанию имеет значение 0 и отключает подписывание SMB. Значение 1 этого параметра включает подписывание SMB для всех взаимодействий по протоколу SMB, блокируя обмен данными по протоколу SMB с компьютерами, на которых отключено подписывание SMB. Подписывание SMB может повысить нагрузку на ЦП и замедлить круговые пути, но оно также блокирует атаки "злоумышленник в середине". Если подписывание SMB не требуется, этот параметр реестра должен иметь значение 0 на всех клиентах и серверах. 
    
    См. подробнее о [подписывании SMB](https://blogs.technet.microsoft.com/josebda/2010/12/01/the-basics-of-smb-signing-covering-both-smb1-and-smb2/).

-   **FileInfoCacheEntriesMax**

    ```
    HKLM\System\CurrentControlSet\Services\LanmanWorkstation\Parameters\FileInfoCacheEntriesMax
    ```

    Область применения: Windows 10, Windows 8.1, Windows 8, Windows 7, Windows Vista, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 и Windows Server 2008

    По умолчанию имеет значение 64. Допускаются значения от 1 до 65536. Это значение используется для определения объема метаданных файла, которые могут кэшироваться клиентом. Увеличение значения позволяет сократить сетевой трафик и повысить производительность, если осуществляется доступ к большому числу файлов.

-   **DirectoryCacheEntriesMax**

    ```
    HKLM\System\CurrentControlSet\Services\LanmanWorkstation\Parameters\DirectoryCacheEntriesMax
    ```

    Область применения: Windows 10, Windows 8.1, Windows 8, Windows 7, Windows Vista, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 и Windows Server 2008

    По умолчанию имеет значение 16. Допускаются значения от 1 до 4096. Это значение используется для определения объема сведений о каталогах, которые могут кэшироваться клиентом. Увеличение значения позволяет сократить сетевой трафик и повысить производительность, если осуществляется доступ к большому числу каталогов.

-   **FileNotFoundCacheEntriesMax**

    ```
    HKLM\System\CurrentControlSet\Services\LanmanWorkstation\Parameters\FileNotFoundCacheEntriesMax
    ```

    Область применения: Windows 10, Windows 8.1, Windows 8, Windows 7, Windows Vista, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 и Windows Server 2008

    По умолчанию имеет значение 128. Допускаются значения от 1 до 65536. Это значение используется для определения объема сведений об именах файлов, которые могут кэшироваться клиентом. Увеличение значения позволяет сократить сетевой трафик и повысить производительность, если осуществляется доступ к большому числу имен файлов.

-   **MaxCmds**

    ```
    HKLM\System\CurrentControlSet\Services\LanmanWorkstation\Parameters\MaxCmds
    ```

    Область применения: Windows 10, Windows 8.1, Windows 8, Windows 7, Windows Vista, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 и Windows Server 2008

    Значение по умолчанию — 15. Этот параметр ограничивает число ожидающих запросов в одном сеансе. Увеличение этого значения приводит к повышению использования памяти, но может повысить производительность благодаря использованию более глубокого конвейера запросов. Увеличение значения в сочетании с MaxMpxCt также позволяет устранить ошибки, возникающие из-за большого числа долгосрочных ожиданий по запросам файлов, таких как вызовы FindFirstChangeNotification. Этот параметр не влияет на подключение к серверам SMB 2.0.

-   **DormantFileLimit**

    ```
    HKLM\System\CurrentControlSet\Services\LanmanWorkstation\Parameters\DormantFileLimit
    ```

    Область применения: Windows 10, Windows 8.1, Windows 8, Windows 7, Windows Vista, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 и Windows Server 2008

    Значение по умолчанию — 1023. Этот параметр определяет максимальное число файлов, которые нужно оставить открытыми в общем ресурсе после того, как приложение закроет файл.

### <a name="client-tuning-example"></a>Пример настройки клиента

Общие параметры настройки для клиентских компьютеров позволяют оптимизировать доступ к удаленным файловым ресурсам, особенно в некоторых сетях с высокой задержкой (например, при подключениях между филиалами, центрами обработки данных и домашними офисами, а также мобильных широкополосных подключениях). Предложенные значения не являются оптимальными и применимыми на всех компьютерах. Следует тщательно оценить влияние каждого параметра, прежде чем применять его.

| Параметр                   | Значение | По умолчанию |
|-----------------------------|-------|---------|
| DisableBandwidthThrottling  | 1     | 0       |
| FileInfoCacheEntriesMax     | 32768 | 64      |
| DirectoryCacheEntriesMax    | 4096  | 16      |
| FileNotFoundCacheEntriesMax | 32768 | 128     |
| MaxCmds                     | 32768 | 15      |

 

Начиная с Windows 8, вы можете настроить многие из этих параметров SMB с помощью командлетов Windows PowerShell **Set-SmbClientConfiguration** и **Set-SmbServerConfiguration**. Кроме того, Windows PowerShell позволяет настраивать параметры, доступные только в реестре.

```
Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Services\LanmanWorkstation\Parameters" RequireSecuritySignature -Value 0 -Force
```
