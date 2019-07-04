---
title: Пакет компонентов для обеспечения совместимости приложений основных серверных компонентов по требованию
description: Установка компонентов Windows Server по требованию
ms.prod: windows-server-threshold
ms.technology: server-general
ms.topic: article
ms.assetid: 99f7daa4-30ce-4d13-be65-0a4d55cca754
author: jasongerend
ms.author: jgerend
manager: jasgroce
ms.localizationpriority: medium
ms.date: 06/07/2019
ms.openlocfilehash: 441cd9593371cb7e5018a61c3d7a6af991ce8fed
ms.sourcegitcommit: afb0602767de64a76aaf9ce6a60d2f0e78efb78b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/20/2019
ms.locfileid: "67280170"
---
# <a name="server-core-app-compatibility-feature-on-demand-fod"></a>Пакет компонентов для обеспечения совместимости приложений основных серверных компонентов по требованию

> Относится к: Windows Server 2019, Windows Server Semi-Annual Channel

**Пакет компонентов для обеспечения совместимости приложений основных серверных компонентов по требованию** (FOD — пакет компонентов по требованию) — это дополнительный пакет компонентов, который можно добавить в установки основных серверных компонентов Windows Server 2019 или Windows Server Semi-Annual Channel в любое время.

Дополнительные сведения о пакетах компонентов по требованию см. в [этой статье](https://docs.microsoft.com/windows-hardware/manufacture/desktop/features-on-demand-v2--capabilities).

## <a name="why-install-the-app-compatibility-fod"></a>Зачем устанавливать FOD для обеспечения совместимости приложений?

FOD для обеспечения совместимости приложений основных серверных компонентов значительно улучшает совместимость приложений для установки основных серверных компонентов Windows за счет включения подмножества двоичных файлов и пакетов из Windows Server с возможностями рабочего стола без добавления графической среды возможностей рабочего стола Windows Server. Этот дополнительный пакет доступен в отдельном ISO-файле или в клиентском компоненте Центра обновления Windows, и его можно добавлять только в образы и установки основных серверных компонентов Windows.

FOD для обеспечения совместимости приложений предоставляет два таких основных преимущества:

- Повышает совместимость основных серверных компонентов с серверными приложениями, которые уже представлены на рынке или уже разработаны и развернуты организациями.
- Помогает в предоставлении компонентов ОС и повышает совместимость приложений с программными средствами, используемыми в сценариях оперативной диагностики и устранения неполадок.

Компоненты операционной системы, которые доступны как часть FOD для обеспечения совместимости приложений основных серверных компонентов, включают в себя:

-   Консоль управления (MMC) (mmc.exe).

-   Средство "Просмотр событий" (Eventvwr.msc).

-   Системный монитор (PerfMon.exe).

-   Монитор ресурсов (Resmon.exe).

-   Диспетчер устройств (Devmgmt.msc).

-   Проводник (Explorer.exe).

-   Windows PowerShell (Powershell_ISE.exe).

-   Средство управления дисками (Diskmgmt.msc).

-   Диспетчер отказоустойчивости кластеров (CluAdmin.msc).

    -   Сначала требуется добавить компонент отказоустойчивой кластеризации Windows Server.

        -   Откройте сеанс PowerShell с повышенными привилегиями: 

            ```PowerShell
            Install-WindowsFeature -NameFailover-Clustering -IncludeManagementTools
            ```

        -   Чтобы запустить диспетчер отказоустойчивости кластеров, введите **cluadmin** в командной строке.

Серверы под управлением Windows Server версии 1903 и более поздних также поддерживают следующие компоненты (если используется та же версия FOD для обеспечения совместимости приложений):

- Диспетчер Hyper-V (virtmgmt.msc).
- Планировщик заданий (taskschd.msc).

## <a name="installing-the-app-compatibility-fod"></a>Установка FOD для обеспечения совместимости приложений

FOD для обеспечения совместимости приложений можно установить только для основных серверных компонентов Не пытайтесь добавить FOD для обеспечения совместимости приложений основных серверных компонентов в установку Windows Server с возможностями рабочего стола. Эти же ISO-образы необязательных пакетов FOD можно использовать как для установки основных серверных компонентов Windows Server 2019, так и для установки Windows Server Semi-Annual Channel.

1. Если сервер может подключиться к клиентскому компоненту Центра обновления Windows, необходимо просто запустить приведенную ниже команду из сеанса PowerShell с повышенными правами, а затем перезапустить Windows Server после ее выполнения.

    ```PowerShell
    Add-WindowsCapability -Online -Name ServerCore.AppCompatibility~~~~0.0.1.0
    ```

2. Если сервер не может подключиться к клиентскому компоненту Центра обновления Windows, вместо этого скачайте ISO-образы необязательных пакетов FOD для сервера и скопируйте их в общую папку в вашей локальной сети:

   - Если у вас есть корпоративная лицензия, вы можете загрузить файл ISO-образа FOD для сервера с того же портала, где получен файл ISO-образа ОС: [Центр поддержки корпоративных лицензий](https://www.microsoft.com/Licensing/servicecenter/default.aspx).
   - Файл ISO-образа FOD для сервера также доступен для подписчиков в [Центре оценки Майкрософт](https://www.microsoft.com/evalcenter/evaluate-windows-server) или на [портале Visual Studio](https://visualstudio.microsoft.com).

3. Войдите в систему с использованием учетной записи администратора на компьютере с основными серверными компонентами, который подключен к локальной сети и на который вы хотите добавить FOD.

4. Используйте команду**net use** или другой метод для подключения к расположению ISO-образа FOD.

5. Скопируйте ISO-образ FOD в локальную папку на ваш выбор.

6. Подключите ISO-образ FOD с помощью следующей команды в сеансе PowerShell с повышенными правами:

    ```PowerShell
    Mount-DiskImage -ImagePath drive_letter:\folder_where_ISO_is_saved\ISO_filename.iso
    ```

7. Выполните следующую команду.

    ```PowerShell
    Add-WindowsCapability -Online -Name ServerCore.AppCompatibility~~~~0.0.1.0 -Source <Mounted_Server_FOD_Drive> -LimitAccess
     ```

8. После заполнения индикатора выполнения перезапустите операционную систему.

   Дополнительные сведения об использовании команд DISM в Windows PowerShell см. в [этой статье](https://docs.microsoft.com/windows-hardware/manufacture/desktop/use-dism-in-windows-powershell-s14).

## <a name="to-optionally-add-internet-explorer-11-to-server-core-after-adding-the-server-core-app-compatibility-fod"></a>Добавление Internet Explorer 11 в основные серверные компоненты (после добавления FOD для обеспечения совместимости приложений основных серверных компонентов)

 >[!NOTE]  
   > Чтобы добавить Internet Explorer 11, требуется FOD для обеспечения совместимости приложений основных серверных компонентов, но при добавлении этого FOD Internet Explorer 11 не требуется.

1. Войдите в систему в качестве администратора на компьютере с основными серверными компонентами, на котором уже добавлен FOD для обеспечения совместимости приложений, а необязательный пакет ISO-образа FOD для сервера скопирован локально.

2. Запустите PowerShell, введя **powershell.exe** в командной строке.

3. Подключите ISO-образ FOD с помощью следующей команды:

    ```PowerShell
    Mount-DiskImage -ImagePath drive_letter:\folder_where_ISO_is_saved\ISO_filename.iso
    ```

4. Выполните следующую команду, используя переменную `$package_path`, чтобы ввести путь к CAB-файлу Internet Explorer:

    ```PowerShell
    $package_path = "D:\Microsoft-Windows-InternetExplorer-Optional-Package~31bf3856ad364e35~amd64~~.cab"

    Add-WindowsPackage -Online -PackagePath $package_path
    ```

5. После заполнения индикатора выполнения перезапустите операционную систему.

## <a name="release-notes-and-suggestions-for-the-server-core-app-compatibility-fod-and-internet-explorer-11-optional-package"></a>Заметки о выпуске и предложения по дополнительному пакету Internet Explorer 11 и FOD для обеспечения совместимости приложений основных серверных компонентов

> [!IMPORTANT]
> Пакеты FOD для обеспечения совместимости приложений, установленные на Windows Server версии 1809, не будут оставаться в системе после обновления на месте до Windows Server версии 1903, поэтому вам придется устанавливать их снова после обновления. Кроме того, перед обновлением можно добавить пакет FOD для обеспечения совместимости приложений в новый источник установки Windows Server. Это гарантирует, что новая версия FOD для обеспечения совместимости приложений будет оставаться в системе после завершения обновления. Дополнительные сведения см. в разделе [Добавление возможностей и дополнительных пакетов в автономный образ основных серверных компонентов WIM](install-fod-19.md#add-capabilities).

- **Важно!** Прочтите примечания к выпуску Windows Server 2019, чтобы узнать о всех проблемах, решениях и рекомендациях, прежде чем приступить к установке и использованию дополнительного пакета Internet Explorer 11 и FOD для обеспечения совместимости приложений основных серверных компонентов.

- При добавлении FOD для обеспечения совместимости приложений основных серверных компонентов после использования клиентского компонента Центра обновления Windows для установки накопительных обновлений возможно мерцание консоли основных серверных компонентов.  Эта проблема решена в обновлениях за декабрь 2018 года.  Дополнительные сведения и инструкции по устранению см. в [статье 4481610 базы знаний: здесь](https://support.microsoft.com/help/4481610/screen-flickers-after-fod-installation-windows2019-server-core).

- После установки FOD для обеспечения совместимости приложений и перезагрузки сервера цвет рамки окна командной консоли изменится на другой оттенок синего.

- Если вы решили также установить дополнительный пакет Internet Explorer 11, обратите внимание, что открытие локально сохраненных HTM-файлов по двойному щелчку не поддерживается. **Щелкните правой кнопкой мыши** и выберите команду **открытия с помощью IE** или откройте файлы прямо в Internet Explorer, щелкнув пункты **Файл** -> **Открыть**.

- Чтобы еще больше повысить совместимость приложений основных серверных компонентов при наличии FOD для обеспечения совместимости приложений, в качестве дополнительного компонента в основные серверные компоненты была добавлена консоль управления IIS.  Чтобы использовать консоль управления IIS, сначала необходимо добавить FOD для обеспечения совместимости приложений. Консоль управления IIS использует консоль MMC (mmc.exe), которая доступна только в основных серверных компонентах, в которых добавлен FOD для обеспечения совместимости приложений.  Чтобы добавить консоль управления IIS, выполните команду PowerShell [**Install-WindowsFeature**](https://docs.microsoft.com/powershell/module/microsoft.windows.servermanager.migration/install-windowsfeature?view=win10-ps).

- Как правило, при установке приложений в основные серверные компоненты (с этими дополнительными пакетами или без них) иногда необходимо использовать параметры и инструкции для автономной установки. 
    
  - Например, SQL Server Management Studio для SQL Server 2016 и SQL Server 2017 можно установить в основные серверные компоненты. Эта среда полностью функциональна при наличии FOD для обеспечения совместимости приложений.  Дополнительные сведения см. в статье [Установка SQL Server из командной строки](https://docs.microsoft.com/sql/database-engine/install-windows/install-sql-server-from-the-command-prompt?view=sql-server-2017).
  - Если среда SQL Server Management Studio не требуется, необязательно устанавливать FOD для обеспечения совместимости приложений основных серверных компонентов.  Дополнительные сведения см. в статье [Установка SQL Server в Server Core](https://docs.microsoft.com/sql/database-engine/install-windows/install-sql-server-on-server-core?view=sql-server-2017).

## <a name="a-idadd-capabilities-adding-capabilities-and-optional-packages-to-an-offline-wim-server-core-image"></a><a id="add-capabilities"> Добавление возможностей и дополнительных пакетов в автономный образ основных серверных компонентов WIM

1. Скачайте файлы ISO-образов Windows Server и FOD для обеспечения совместимости приложений основных серверных компонентов в локальную папку на компьютере Windows.

   - Если у вас есть корпоративная лицензия, вы можете скачать файлы ISO-образов Windows Server и FOD для обеспечения совместимости приложений основных серверных компонентов из [Центра поддержки корпоративных лицензий](https://www.microsoft.com/Licensing/servicecenter/default.aspx).
   - Файл ISO-образа FOD для сервера также доступен для выпусков канала Long-Term Servicing Channel подписчикам в [Центре оценки Майкрософт](https://www.microsoft.com/evalcenter/evaluate-windows-server) или на [портале Visual Studio](https://visualstudio.microsoft.com).

2. Откройте сеанс PowerShell от имени администратора, а затем используйте следующие команды для подключения файлов образа в качестве дисков:

   ```PowerShell
   Mount-DiskImage -ImagePath Path_To_ServerFOD_ISO
   Mount-DiskImage -ImagePath Path_To_Windows_Server_ISO
   ```

3. Скопируйте содержимое ISO-файла Windows Server в локальную папку (например, *C:\SetupFiles\WindowsServer*).

4. Получите имя образа, который вы хотите изменить, в файле Install.wim с помощью следующей команды.<br>
Используйте переменную `$install_wim_path`, чтобы ввести путь к файлу Install.wim, расположенному в папке \Sources ISO-файла.

   ```PowerShell
   $install_wim_path = "C:\SetupFiles\WindowsServer\sources\install.wim"

   Get-WindowsImage -ImagePath $install_wim_path
   ```

5. Подключите файл Install.wim в новой папке с помощью следующей команды, заменив значения переменных в примере собственными и повторно использовав переменную `$install_wim_path` из предыдущей команды.<br>

   - `$image_name` — введите имя образа, который вы хотите подключить.
   - `$mount_folder variable` — укажите папку, которая будет использоваться при доступе к содержимому файла Install.wim.

   ```PowerShell
   $image_name = "Windows Server Datacenter"
   $mount_folder = "c:\test\offline"

   Mount-WindowsImage -ImagePath $install_wim_path -Name $image_name -path $mount_folder
   ```

6. Добавьте нужные возможности и пакеты к подключенному образу Install.wim с помощью следующих команд, заменив значения переменных в примере собственными.<br>

   - `$capability_name` — укажите имя возможности, которую необходимо установить (в данном случае возможность AppCompatibility).
   - `$package_path` — укажите путь к пакету, который необходимо установить (в данном случае Internet Explorer).
   - `$fod_drive` — укажите букву диска для подключенного образа FOD для обеспечения совместимости приложений основных серверных компонентов.

   ```PowerShell
   $capability_name = "ServerCore.AppCompatibility~~~~0.0.1.0"
   $package_path = "D:\Microsoft-Windows-InternetExplorer-Optional-Package~31bf3856ad364e35~amd64~~.cab"
   $fod_drive = "d:\"

   Add-WindowsCapability -Path $mount_folder -Name $capability_name -Source $fod_drive -LimitAccess
   Add-WindowsPackage -Path $mount_folder -PackagePath $package_path
   ```

7. Отключите образ и зафиксируйте изменения в файле Install.wim с помощью следующей команды, которая использует переменную `$mount_folder` из предыдущих команд:

   ```PowerShell
   Dismount-WindowsImage -Path $mount_folder -Save
   ```

Теперь можно обновить сервер, запустив файл setup.exe из папки, которую вы создали для файлов установки Windows Server (в этом примере: *C:\SetupFiles\WindowsServer*). Эта папка теперь содержит установочные файлы Windows Server с дополнительными возможностями и пакетами.