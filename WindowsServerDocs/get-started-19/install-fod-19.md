---
title: Функция совместимости приложений основных серверных компонентов по требованию (FOD)
description: Установка возможности Windows Server по требованию
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: server-general
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 99f7daa4-30ce-4d13-be65-0a4d55cca754
author: coreyp-at-msft
ms.author: coreyp
manager: jasgroce
ms.localizationpriority: medium
ms.openlocfilehash: b8211ace56aa6565295a15adce26a8dfbc98e1e9
ms.sourcegitcommit: dbb4738fdac3b7911952ff11f1eaed9649d6567a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/07/2019
ms.locfileid: "9149904"
---
# Функция совместимости приложений основных серверных компонентов по требованию (FOD)

> Применимо к Windows Server 2019 и Windows Server, версия 1809

**Server Core приложение совместимости компонентов по требованию** — пакет дополнительных компонентов, который можно добавить в установку Windows Server 2019 Server Core или Windows Server, версия 1809, в любое время.

Дополнительные сведения о компонентов по требованию (FOD) см. в разделе [Компоненты по требованию](https://docs.microsoft.com/windows-hardware/manufacture/desktop/features-on-demand-v2--capabilities).


## Почему установить FOD совместимости приложений? 

Совместимость приложений, компонентов по требованию для Server Core, значительно повышает совместимость приложений вариант установки Windows Server Core, в том числе подмножество двоичных файлов и пакетов из Windows Server с возможностями рабочего стола, без добавления Windows Server Desktop Experience графического среды. Этот дополнительный пакет будет доступен на отдельном ISO или из центра обновления Windows, но могут быть добавлены только для установки Windows Server Core и изображения.

Два основных значения, которые предоставляет FOD совместимости приложений — это:

1.  Повышает совместимость серверных для серверных приложений, которые уже на рынке или уже были разработчик организации и развернуть.

2.  Помогает компоненты операционной системы и повышения совместимости средств программного обеспечения, используемые в акутом устранения неполадок и отладки сценариев.

Компоненты операционной системы, которые доступны как часть приложения совместимости Server Core FOD относятся:

-   Консоль управления Microsoft (mmc.exe)

-   Просмотр событий (Eventvwr.msc)

-   Системный монитор (PerfMon.exe)

-   Монитор ресурсов (Resmon.exe)

-   Диспетчер устройств (Devmgmt.msc)

-   Проводник (Explorer.exe)

-   Windows PowerShell (Powershell_ISE.exe)

-   Средство управления дисками (Diskmgmt.msc)

-   Диспетчер отказоустойчивости кластеров (CluAdmin.msc)

    -   Сначала необходимо добавление функции отказоустойчивой кластеризации Windows Server.

        -   Чтобы добавить, воспользуйтесь командлетом Powershell `Install-WindowsFeature -NameFailover-Clustering -IncludeManagementTools`

        -   Чтобы запустить диспетчер отказоустойчивости кластеров, введите **cluadmin** в командной строке.

## Установка FOD совместимости приложений

 >[!IMPORTANT] 
   >FOD совместимости приложений можно установить только на Server Core. Не пытайтесь добавить приложение совместимости Server Core FOD до установки Windows Server Windows Server с возможностями рабочего стола.

### Добавление запущенный экземпляр серверных Server Core совместимости компонентов по требованию (FOD)

 >[!NOTE] 
   > В этой процедуре используется системы обслуживания образов развертывания и управления (DISM.exe), средство командной строки. Дополнительные сведения о команды DISM см. в разделе [DISM возможности параметрах](https://docs.microsoft.com/windows-hardware/manufacture/desktop/dism-capabilities-package-servicing-command-line-options).

>[!NOTE] 
   > Же FOD дополнительных пакетов ISO можно использовать для установки Windows Server 2019 Server Core или Windows Server, версия 1809, установки.

>[!NOTE] 
   > Если компьютер или виртуальную машину под управлением Server Core подключиться к центру обновления Windows, можно пропустить шаги 1 – 7 ниже. Но не забудьте оставить/Source и /LimitAccess с помощью команды DISM в шаг 8.

1. Загрузите дополнительные пакеты Server FOD ISO и скопируйте ISO в общей папке в локальной сети:

 - При наличии корпоративную лицензию можно загрузить файл Server FOD ISO изображения из же портал, где можно получить ОС ISO-файл образа: [Volume Licensing Service Center](https://www.microsoft.com/Licensing/servicecenter/default.aspx).
 - Файл изображения ISO FOD сервера также доступен в [Центра оценки Microsoft](https://www.microsoft.com/evalcenter/evaluate-windows-server-2019) или на [портале Visual Studio](https://visualstudio.microsoft.com) для подписчиков.


2. Вход от имени администратора на компьютере Server Core, который подключен к локальной сети, и вы хотите добавить FOD для.

3. Используете **net use**или другим способом для подключения к расположению FOD ISO.

4. Скопируйте FOD ISO в локальную папку на выбор.

5. Запустите PowerShell, введя **powershell.exe** в командной строке.

6. Подключите FoD ISO с помощью следующей команды:

        Mount-DiskImage -ImagePath drive_letter:\folder_where_ISO_is_saved\ISO_filename.iso

7. Введите **exit** для выхода из PowerShell.

8.  Выполните следующую команду.

        DISM /Online /Add-Capability /CapabilityName:"ServerCore.AppCompatibility~~~~0.0.1.0" /Source:drive_letter_of_mounted_ISO: /LimitAccess

9.  После завершения индикатор перезапуска операционной системы.

### При необходимости добавить Internet Explorer 11 в Server Core (после добавления приложения совместимости Server Core FOD)

 >[!NOTE]  
   > Приложение совместимости Server Core FOD является обязательным для добавления Internet Explorer 11, но не требуется добавлять приложения совместимости Server Core FOD Internet Explorer 11.

1.  Вход от имени администратора на компьютере Server Core с FOD совместимости приложение уже добавили и дополнительный пакет Server FOD ISO копирования локально.

2.  Запустите PowerShell, введя **powershell.exe** в командной строке.

3.  Подключите FoD ISO с помощью следующей команды:

         Mount-DiskImage -ImagePath drive_letter:\folder_where_ISO_is_saved\ISO_filename.iso

4.  Введите **exit** для выхода из PowerShell.


5.  Выполните следующую команду.

        Dism /online /add-package:drive_letter_of_mounted_iso:"Microsoft-Windows-InternetExplorer-Optional-Package~31bf3856ad364e35~amd64~~.cab"

6.  После завершения индикатор перезапуска операционной системы.

 
#### Заметки о выпуске и варианты дополнительный пакет на Server Core приложение совместимости FOD и Internet Explorer 11

- **Важные:** прочитайте заметки о выпуске Windows Server 2019 для проблемы, рекомендации, руководство, прежде чем продолжить установку и использование дополнительного пакета FOD совместимости приложений Server Core и Internet Explorer 11.
 
 >[!NOTE] 
   > Это можно столкнуться мерцание с возможностями консоли Server Core при добавлении FOD совместимости приложений после установки накопительных обновлений с помощью центра обновления Windows.  Эта проблема будет решена с декабря 2018 года обновлений.  Дополнительные сведения и разрешение действия, см. в разделе [статье базы знаний 4481610: мерцание экрана после установки Server Core приложение совместимости FOD в Windows Server 2019 Server Core](https://support.microsoft.com/help/4481610/screen-flickers-after-fod-installation-windows2019-server-core).

- После установки FOD совместимости приложений и перезагрузка сервера цвет рамки окна консоли команду изменится на цвет, отличающийся синего цвета.

- Если вы решили также установить дополнительный пакет Internet Explorer 11, обратите внимание, что двойным щелчком открывать файлы локально сохраненные .htm не поддерживается. Тем не менее, вы можете, **щелкните правой кнопкой мыши** и выбрать, **открывать IE**, или его можно открыть непосредственно из Internet Explorer **файл** -> **Открыть**. 

- Чтобы расширить Совместимость серверных приложений с FOD совместимости приложений, консоль управления IIS добавлен в Server Core как дополнительный компонент.  Тем не менее это совершенно необходимо сначала добавить FOD совместимость приложений с помощью консоли управления IIS. Консоль управления IIS основывается на консоли управления Microsoft (mmc.exe), который доступен только в Server Core с добавлением FOD совместимости приложений.  Используйте Powershell [**Установки-WindowsFeature**](https://docs.microsoft.com/powershell/module/microsoft.windows.servermanager.migration/install-windowsfeature?view=win10-ps) для добавления консоль управления IIS.

- Так как точка Общие рекомендации, при установке приложений на сервере Core (независимо от этих дополнительных пакетов) его иногда возникает необходимость использования параметров автоматической установки и инструкций. 
    
 - Например SQL Server Management Studio для SQL Server 2016 и SQL Server 2017 можно установить на Server Core и является полностью работоспособным при наличии FOD совместимости приложений.  См. в разделе, [установить SQL Server из командной строки](https://docs.microsoft.com/sql/database-engine/install-windows/install-sql-server-from-the-command-prompt?view=sql-server-2017).
 - Если нет необходимости SQL Server Management Studio, он не требуется установить приложение совместимости Server Core FOD.  См. в разделе, [Установка SQL Server в Server Core](https://docs.microsoft.com/sql/database-engine/install-windows/install-sql-server-on-server-core?view=sql-server-2017).

