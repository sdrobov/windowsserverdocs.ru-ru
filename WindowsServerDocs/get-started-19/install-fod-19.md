---
title: Функция совместимости приложений основных серверных компонентов по требованию (FOD)
description: Установка компонентов Windows Server по запросу
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
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59866115"
---
# <a name="server-core-app-compatibility-feature-on-demand-fod"></a>Функция совместимости приложений основных серверных компонентов по требованию (FOD)

> Применяется к Windows Server 2019 и Windows Server версии 1809

**Server Core компонент совместимости приложений по запросу** — это дополнительная функция пакет, который можно добавить в установках основных серверных компонентов Windows Server 2019 г., или Windows Server версии 1809, в любое время.

Дополнительные сведения о возможностях по запросу (FOD), см. в разделе [компоненты по требованию](https://docs.microsoft.com/windows-hardware/manufacture/desktop/features-on-demand-v2--capabilities).


## <a name="why-install-the-app-compatibility-fod"></a>Почему Установка FOD совместимости приложений? 

Совместимость приложений, компонентов по требованию для основных серверных компонентов, значительно улучшает совместимость приложений вариант установки основных серверных компонентов Windows, включая подмножество двоичные файлы и пакеты из Windows Server с рабочим столом, не добавляя Windows Server Desktop Experience графическую среду. Этот дополнительный пакет на отдельном ISO или из центра обновления Windows, но могут добавляться только в установках основных серверных компонентов Windows и изображения.

Два основной FOD совместимости приложений предоставляет значения:

1.  Повышает совместимость основных серверных компонентов для серверных приложений, которые уже находятся на рынке или уже была разработки организациями и развертывания.

2.  Помогает использовать компоненты операционной системы и приложения для повышения совместимости программных средств, используемых в острой устранение неисправностей и отладка сценариев.

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

        -   Чтобы добавить, с помощью командлета Powershell `Install-WindowsFeature -NameFailover-Clustering -IncludeManagementTools`

        -   Чтобы запустить диспетчер отказоустойчивости кластеров, введите **cluadmin** в командной строке.

## <a name="installing-the-app-compatibility-fod"></a>Установка FOD совместимости приложений

 >[!IMPORTANT] 
   >FOD совместимости приложений может устанавливаться только на основных серверных компонентов. Не пытайтесь добавить приложения совместимости Server Core FOD на установку Windows Server с рабочим столом Windows Server.

### <a name="to-add-the-server-core-app-compatibility-feature-on-demand-fod-to-a-running-instance-of-server-core"></a>Чтобы добавить компонент совместимости приложения Server Core по запросу (FOD) к запущенному экземпляру ядра сервера

 >[!NOTE] 
   > Эта процедура использует обслуживания образов развертывания и управления (DISM.exe), средство командной строки. Дополнительные сведения о командах DISM см. в разделе [DISM возможности параметрах](https://docs.microsoft.com/windows-hardware/manufacture/desktop/dism-capabilities-package-servicing-command-line-options).

>[!NOTE] 
   > Те же FOD необязательно пакеты ISO можно использовать для установки основных серверных компонентов Windows Server 2019 г. или Windows Server версии 1809, установок.

>[!NOTE] 
   > Если компьютер или виртуальную машину, на котором работает Server Core сможет подключаться к центру обновления Windows, можно пропустить шаги 1 – 7 ниже. Но не забудьте оставить флажок/Source и /LimitAccess команды DISM на шаге 8.

1. Скачайте дополнительные пакеты Server FOD ISO и скопируйте его в общую папку в локальной сети:

 - Если у вас есть корпоративная лицензия, можно загрузить файл образа Server FOD ISO же портале, где получается файл образа ISO ОС: [Volume Licensing Service Center](https://www.microsoft.com/Licensing/servicecenter/default.aspx).
 - Файл образа Server FOD ISO доступен также на [Центр пробных испытаний Microsoft](https://www.microsoft.com/evalcenter/evaluate-windows-server-2019) или на [портал Visual Studio](https://visualstudio.microsoft.com) для подписчиков.


2. Войдите от имени администратора на компьютере основных серверных компонентов, которая подключена к локальной сети, и вы хотите добавить FOD для.

3. Используйте **net используйте**, или другим методом, для подключения к расположению FOD ISO-образ.

4. Скопируйте FOD ISO в локальную папку по своему выбору.

5. Запустите PowerShell, введя **powershell.exe** в командной строке.

6. Подключите ISO-образ FoD с помощью следующей команды:

        Mount-DiskImage -ImagePath drive_letter:\folder_where_ISO_is_saved\ISO_filename.iso

7. Тип **выйти из** для выхода из PowerShell.

8.  Выполните следующую команду:

        DISM /Online /Add-Capability /CapabilityName:"ServerCore.AppCompatibility~~~~0.0.1.0" /Source:drive_letter_of_mounted_ISO: /LimitAccess

9.  После завершения индикатор перезагрузку операционной системы.

### <a name="to-optionally-add-internet-explorer-11-to-server-core-after-adding-the-server-core-app-compatibility-fod"></a>При необходимости добавить Internet Explorer 11 для основных серверных компонентов (после добавления приложения совместимости Server Core FOD)

 >[!NOTE]  
   > Приложение совместимости Server Core FOD обязателен для добавления Internet Explorer 11, но Internet Explorer 11 не требуется, чтобы добавить приложение совместимости Server Core FOD.

1.  Войдите от имени администратора на компьютере основных серверных компонентов с FOD совместимости приложений уже добавлен и дополнительный пакет Server FOD, ISO, скопировать локально.

2.  Запустите PowerShell, введя **powershell.exe** в командной строке.

3.  Подключите ISO-образ FoD с помощью следующей команды:

         Mount-DiskImage -ImagePath drive_letter:\folder_where_ISO_is_saved\ISO_filename.iso

4.  Тип **выйти из** для выхода из PowerShell.


5.  Выполните следующую команду:

        Dism /online /add-package:drive_letter_of_mounted_iso:"Microsoft-Windows-InternetExplorer-Optional-Package~31bf3856ad364e35~amd64~~.cab"

6.  После завершения индикатор перезагрузку операционной системы.

 
#### <a name="release-notes-and-suggestions-for-the-server-core-app-compatibility-fod-and-internet-explorer-11-optional-package"></a>Заметки о выпуске и предложения по дополнительный пакет совместимости приложения FOD для Server Core и Internet Explorer 11

- **Важно:** прочтите заметки о выпуске Windows Server 2019 проблемы, вопросы и рекомендации, прежде чем продолжить установку и использование дополнительный пакет совместимости приложения FOD для Server Core и Internet Explorer 11.
 
 >[!NOTE] 
   > Существует возможность столкнуться мерцание в работы с консолью в Server Core, при добавлении FOD совместимости приложения после использования Центра обновления Windows для установки накопительного пакета обновлений.  Обновляет данной проблемы с декабря 2018 г.  Дополнительные сведения и инструкции по устранению, см. в разделе [4481610 статье базы знаний: Экран мерцание после установки Server Core приложения совместимости FOD в основных серверных компонентов Windows Server 2019](https://support.microsoft.com/help/4481610/screen-flickers-after-fod-installation-windows2019-server-core).

- После установки FOD совместимости приложений и перезагрузки сервера рамки окна консоли команду цвет изменится на разных оттенок синего.

- Если вы решили также установить дополнительный пакет Internet Explorer 11, обратите внимание, что двойным щелчком открыть локально сохраненному HTM-файлов не поддерживается. Тем не менее, вы можете **щелкните правой кнопкой мыши** и выберите **откройте с IE**, или его можно открыть непосредственно из Internet Explorer **файл** -> **откройте**. 

- Для дальнейшего улучшения совместимости приложения основных серверных компонентов с FOD совместимости приложения, консоль управления IIS была добавлена в Server Core как дополнительный компонент.  Тем не менее это совершенно необходимо сначала добавить FOD совместимости приложений, чтобы использовать консоль управления IIS. Консоль управления IIS использует консоль управления Майкрософт (mmc.exe), которая доступна только на основных серверных компонентов с добавлением FOD совместимости приложений.  С помощью Powershell [ **Install-WindowsFeature** ](https://docs.microsoft.com/powershell/module/microsoft.windows.servermanager.migration/install-windowsfeature?view=win10-ps) добавить консоль управления IIS.

- Так как точка Общие рекомендации, когда установку приложений на Server Core (с или без эти дополнительные пакеты) его иногда возникает необходимость использовать параметры автоматической установки и инструкции. 
    
 - Например SQL Server Management Studio для SQL Server 2016 и SQL Server 2017 может устанавливаться на основных серверных компонентов и будут обладать полной функциональностью, при наличии FOD совместимости приложений.  См. в разделе, [Установка SQL Server из командной строки](https://docs.microsoft.com/sql/database-engine/install-windows/install-sql-server-from-the-command-prompt?view=sql-server-2017).
 - Если SQL Server Management Studio не требуется, то нет необходимости для установки приложения совместимости Server Core FOD.  См. в разделе, [Установка SQL Server на Server Core](https://docs.microsoft.com/sql/database-engine/install-windows/install-sql-server-on-server-core?view=sql-server-2017).

