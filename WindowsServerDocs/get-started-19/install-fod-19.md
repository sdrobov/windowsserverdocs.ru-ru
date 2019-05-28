---
title: Функция совместимости приложений основных серверных компонентов по требованию (FOD)
description: Установка компонентов Windows Server по запросу
ms.prod: windows-server-threshold
ms.technology: server-general
ms.topic: article
ms.assetid: 99f7daa4-30ce-4d13-be65-0a4d55cca754
author: jasongerend
ms.author: jgerend
manager: jasgroce
ms.localizationpriority: medium
ms.date: 05/24/2019
ms.openlocfilehash: c9af38720df79918bed3404995e81a7f93a10744
ms.sourcegitcommit: 8ba2c4de3bafa487a46c13c40e4a488bf95b6c33
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/25/2019
ms.locfileid: "66222888"
---
# <a name="server-core-app-compatibility-feature-on-demand-fod"></a>Функция совместимости приложений основных серверных компонентов по требованию (FOD)

> Относится к: Windows Server 2019, Windows Server Semi-Annual Channel

**Server Core компонент совместимости приложений по запросу** — это дополнительная функция пакет, который можно добавить в установках основных серверных компонентов Windows Server 2019 г., или Windows Server Semi-Annual Channel, в любое время.

Дополнительные сведения о возможностях по запросу (FOD), см. в разделе [компоненты по требованию](https://docs.microsoft.com/windows-hardware/manufacture/desktop/features-on-demand-v2--capabilities).

## <a name="why-install-the-app-compatibility-fod"></a>Почему Установка FOD совместимости приложений?

Совместимость приложений, компонентов по требованию для основных серверных компонентов, значительно улучшает совместимость приложений вариант установки основных серверных компонентов Windows, включая подмножество двоичные файлы и пакеты из Windows Server с рабочим столом, не добавляя Windows Server Desktop Experience графическую среду. Этот дополнительный пакет на отдельном ISO или из центра обновления Windows, но могут добавляться только в установках основных серверных компонентов Windows и изображения.

Два основной FOD совместимости приложений предоставляет значения:

- Повышает совместимость основных серверных компонентов для серверных приложений, которые уже находятся на рынке или уже была разработки организациями и развертывания.
- Помогает использовать компоненты операционной системы и приложения для повышения совместимости программных средств, используемых в острой устранение неисправностей и отладка сценариев.

Компоненты операционной системы, доступные как часть приложения совместимости Server Core FOD, включая:

-   Консоль управления Майкрософт (mmc.exe)

-   Средство просмотра событий (Eventvwr.msc)

-   Системный монитор (PerfMon.exe)

-   Монитор ресурсов (Resmon.exe)

-   Диспетчер устройств (Devmgmt.msc)

-   Проводник (Explorer.exe)

-   Windows PowerShell (Powershell_ISE.exe)

-   Управление дисками (Diskmgmt.msc)

-   Диспетчер отказоустойчивости кластеров (CluAdmin.msc)

    -   Сначала требуется добавление компонента отказоустойчивого кластера Windows Server.

        -   Из сеанса PowerShell с повышенными правами: 

            ```PowerShell
            Install-WindowsFeature -NameFailover-Clustering -IncludeManagementTools
            ```

        -   Чтобы запустить диспетчер отказоустойчивости кластеров, введите **cluadmin** в командной строке.

Серверы под управлением Windows Server, версии 1903 и более поздние версии также поддерживают следующие компоненты:

- Диспетчер Hyper-V (virtmgmt.msc)
- Планировщик заданий (taskschd.msc)

## <a name="installing-the-app-compatibility-fod"></a>Установка FOD совместимости приложений

FOD совместимости приложений может устанавливаться только на основных серверных компонентов. Не пытайтесь добавить приложения совместимости Server Core FOD на установку Windows Server с рабочим столом Windows Server. Те же FOD необязательно пакеты ISO можно использовать для установки основных серверных компонентов Windows Server 2019 г. или установок Windows Server Semi-Annual Channel.

1. Если сервер может подключиться к центру обновления Windows, что необходимо сделать всего лишь выполните следующую команду из сеанса PowerShell с повышенными привилегиями и перезагрузите Windows Server, после завершения выполнения команды:

    ```PowerShell
    Add-WindowsCapability -Online -Name ServerCore.AppCompatibility~~~~0.0.1.0
    ```

2. Если серверу не удается подключиться к центру обновления Windows, вместо этого загрузить дополнительные пакеты Server FOD ISO и скопируйте его в общую папку в локальной сети:

   - Если у вас есть корпоративная лицензия, можно загрузить файл образа Server FOD ISO же портале, где получается файл образа ISO ОС: [Volume Licensing Service Center](https://www.microsoft.com/Licensing/servicecenter/default.aspx).
   - Файл образа Server FOD ISO доступен также на [Центр пробных испытаний Microsoft](https://www.microsoft.com/evalcenter/evaluate-windows-server) или на [портал Visual Studio](https://visualstudio.microsoft.com) для подписчиков.

3. Войдите с помощью учетной записи администратора на компьютере основных серверных компонентов, которая подключена к локальной сети, и вы хотите добавить FOD для.

4. Используйте **net используйте**, или другим методом, для подключения к расположению FOD ISO-образ.

5. Скопируйте FOD ISO в локальную папку по своему выбору.

6. Подключите ISO-образ FOD, используя следующую команду в сеансе PowerShell с повышенными привилегиями:

    ```PowerShell
    Mount-DiskImage -ImagePath drive_letter:\folder_where_ISO_is_saved\ISO_filename.iso
    ```

7. Выполните следующую команду:

    ```PowerShell
    Add-WindowsCapability -Online -Name ServerCore.AppCompatibility~~~~0.0.1.0 -Source <Mounted_Server_FOD_Drive> -LimitAccess
     ```

8. После завершения индикатор перезагрузку операционной системы.

 Дополнительные сведения о командах DISM см. в разделе [использование средства DISM в Windows PowerShell](https://docs.microsoft.com/windows-hardware/manufacture/desktop/use-dism-in-windows-powershell-s14)

## <a name="to-optionally-add-internet-explorer-11-to-server-core-after-adding-the-server-core-app-compatibility-fod"></a>При необходимости добавить Internet Explorer 11 для основных серверных компонентов (после добавления приложения совместимости Server Core FOD)

 >[!NOTE]  
   > Приложение совместимости Server Core FOD обязателен для добавления Internet Explorer 11, но Internet Explorer 11 не требуется, чтобы добавить приложение совместимости Server Core FOD.

1. Войдите от имени администратора на компьютере основных серверных компонентов с FOD совместимости приложений уже добавлен и дополнительный пакет Server FOD, ISO, скопировать локально.

2. Запустите PowerShell, введя **powershell.exe** в командной строке.

3. Подключите ISO-образ FOD с помощью следующей команды:

    ```PowerShell
    Mount-DiskImage -ImagePath drive_letter:\folder_where_ISO_is_saved\ISO_filename.iso
    ```

4. Выполните следующую команду, используя `$package_path` переменной ввести путь к CAB-файл Internet Explorer:

    ```PowerShell
    $package_path = "D:\Microsoft-Windows-InternetExplorer-Optional-Package~31bf3856ad364e35~amd64~~.cab"

    Add-WindowsPackage -Online -PackagePath $package_path
    ```

5. После завершения индикатор перезагрузку операционной системы.

## <a name="release-notes-and-suggestions-for-the-server-core-app-compatibility-fod-and-internet-explorer-11-optional-package"></a>Заметки о выпуске и предложения по дополнительный пакет совместимости приложения FOD для Server Core и Internet Explorer 11

> [!IMPORTANT]
> FODs, установленной в Windows Server, версии 1809 не остаются на месте после обновления на месте до Windows Server версии 1903, поэтому необходимо установить их снова после обновления. Кроме того можно добавить FODs в новый источник установки Windows Server перед обновлением. Это гарантирует, что новая версия любой FODs присутствуют после завершения обновления. Дополнительные сведения см. в разделе [Добавление возможностей и дополнительные пакеты в автономный образ WIM Server Core](install-fod-19.md#add-capabilities).

- **Важно!** Прочитайте заметки о выпуске Windows Server 2019 проблемы, вопросы и рекомендации, прежде чем продолжить установку и использование дополнительный пакет совместимости приложения FOD для Server Core и Internet Explorer 11.

- Существует возможность столкнуться мерцание в работы с консолью в Server Core, при добавлении FOD совместимости приложения после использования Центра обновления Windows для установки накопительного пакета обновлений.  Обновляет данной проблемы с декабря 2018 г.  Дополнительные сведения и инструкции по устранению, см. в разделе [4481610 статье базы знаний: Экран мерцание после установки Server Core приложения совместимости FOD в основных серверных компонентов Windows Server 2019](https://support.microsoft.com/help/4481610/screen-flickers-after-fod-installation-windows2019-server-core).

- После установки FOD совместимости приложений и перезагрузки сервера рамки окна консоли команду цвет изменится на разных оттенок синего.

- Если вы решили также установить дополнительный пакет Internet Explorer 11, обратите внимание, что двойным щелчком открыть локально сохраненному HTM-файлов не поддерживается. Тем не менее, вы можете **щелкните правой кнопкой мыши** и выберите **откройте с IE**, или его можно открыть непосредственно из Internet Explorer **файл** -> **откройте**.

- Для дальнейшего улучшения совместимости приложения основных серверных компонентов с FOD совместимости приложения, консоль управления IIS была добавлена в Server Core как дополнительный компонент.  Тем не менее это совершенно необходимо сначала добавить FOD совместимости приложений, чтобы использовать консоль управления IIS. Консоль управления IIS использует консоль управления Майкрософт (mmc.exe), которая доступна только на основных серверных компонентов с добавлением FOD совместимости приложений.  С помощью Powershell [ **Install-WindowsFeature** ](https://docs.microsoft.com/powershell/module/microsoft.windows.servermanager.migration/install-windowsfeature?view=win10-ps) добавить консоль управления IIS.

- Так как точка Общие рекомендации, когда установку приложений на Server Core (с или без эти дополнительные пакеты) его иногда возникает необходимость использовать параметры автоматической установки и инструкции. 
    
 - Например SQL Server Management Studio для SQL Server 2016 и SQL Server 2017 может устанавливаться на основных серверных компонентов и будут обладать полной функциональностью, при наличии FOD совместимости приложений.  См. в разделе, [Установка SQL Server из командной строки](https://docs.microsoft.com/sql/database-engine/install-windows/install-sql-server-from-the-command-prompt?view=sql-server-2017).
 - Если SQL Server Management Studio не требуется, то нет необходимости для установки приложения совместимости Server Core FOD.  См. в разделе, [Установка SQL Server на Server Core](https://docs.microsoft.com/sql/database-engine/install-windows/install-sql-server-on-server-core?view=sql-server-2017).

## <a name="a-idadd-capabilities-adding-capabilities-and-optional-packages-to-an-offline-wim-server-core-image"></a><a id="add-capabilities"> Добавление возможностей и дополнительные пакеты в автономный образ WIM Server Core

1. Скачайте файлы образа Windows Server и сервера FOD ISO в локальную папку на компьютере Windows.

   - Если у вас есть корпоративная лицензия можно загрузить Windows Server и сервера FOD ISO файлы изображений из [Volume Licensing Service Center](https://www.microsoft.com/Licensing/servicecenter/default.aspx).
   - Файл образа Server FOD ISO доступен также на [Центр пробных испытаний Microsoft](https://www.microsoft.com/evalcenter/evaluate-windows-server) или на [портал Visual Studio](https://visualstudio.microsoft.com) для подписчиков.

2. Откройте сеанс PowerShell с правами администратора и выполните следующие команды для подключения файлов изображений как диски.

   ```PowerShell
   Mount-DiskImage -ImagePath Path_To_ServerFOD_ISO
   Mount-DiskImage -ImagePath Path_To_Windows_Server_ISO
   ```

3. Скопируйте содержимое файла ISO-ОБРАЗА Windows Server в локальную папку (например, *C:\SetupFiles\WindowsServer*).

4. Получите имя образа, который нужно внести изменения в файл Install.wim с помощью следующей команды.<br>
Используйте `$install_wim_path` переменной ввести путь в файл Install.wim, расположенный в папке \Sources с ISO-файлом.

   ```PowerShell
   $install_wim_path = "C:\SetupFiles\WindowsServer\sources\install.wim"

   Get-WindowsImage -ImagePath $install_wim_path
   ```

5. Подключить файл Install.wim в новую папку с помощью следующей команды, заменив значения переменных в примере собственными и повторное использование `$install_wim_path` переменной из предыдущей команды.<br>

   - `$image_name` -Введите имя образа, который требуется подключить.
   - `$mount_folder variable` -Укажите папку для использования при доступе к содержимое файла Install.wim.

   ```PowerShell
   $image_name = "Windows Server Datacenter"
   $mount_folder = "c:\test\offline"

   Mount-WindowsImage -ImagePath $install_wim_path -Name $image_name -path $mount_folder
   ```

6. Добавьте возможности и пакеты, которые вы хотите подключенного образа Install.wim, используя следующие команды, заменив значения переменных в примере собственными.<br>

   - `$capability_name` -Укажите имя возможности для установки (в данном случае возможность AppCompatibility).
   - `$package_path` — Укажите путь к пакету для установки (в данном случае Internet Explorer).
   - `$fod_drive` -Укажите букву подключенного образа FOD сервера.

   ```PowerShell
   $capability_name = "ServerCore.AppCompatibility~~~~0.0.1.0"
   $package_path = "D:\Microsoft-Windows-InternetExplorer-Optional-Package~31bf3856ad364e35~amd64~~.cab"
   $fod_drive = "d:\"

   Add-WindowsCapability -Path $mount_folder -Name $capability_name -Source $fod_drive -LimitAccess
   Add-WindowsPackage -Path $mount_folder -PackagePath $package_path
   ```

7. Отключить и зафиксировать изменения в файл Install.wim, используя следующую команду, которая использует `$mount_folder` переменной из предыдущей команды:

   ```PowerShell
   Dismount-WindowsImage -Path $mount_folder -Save
   ```

Теперь вы можете обновить сервер, выполнив setup.exe из папки, созданной для файлов установки Windows Server (в этом примере: *C:\SetupFiles\WindowsServer*). Теперь эта папка содержит файлы установки Windows Server с помощью дополнительных возможностей и дополнительные пакеты включены.