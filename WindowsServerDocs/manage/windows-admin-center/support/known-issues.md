---
title: Windows Admin Center — известные проблемы
description: Windows Admin Center (Project Honolulu) — известные проблемы
ms.technology: manage
ms.topic: article
author: jwwool
ms.author: jeffrew
ms.localizationpriority: medium
ms.prod: windows-server
ms.date: 06/07/2019
ms.openlocfilehash: 23943c9567f371f7598c7dcda6db434760cabeab
ms.sourcegitcommit: 1da993bbb7d578a542e224dde07f93adfcd2f489
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "73567088"
---
# <a name="windows-admin-center-known-issues"></a>Windows Admin Center — известные проблемы

> Область применения: центр администрирования Windows, предварительная версия Windows Admin Center

Если возникнет проблема, не описанная на этой странице, [свяжитесь с нами](https://aka.ms/WACfeedback).

## <a name="installer"></a>Установщик

- При установке Windows Admin Center с использованием собственного сертификата следует помнить, что если вы скопируете отпечаток из средства MMC для управления сертификатами, [он будет содержать недопустимый символ в начале.](https://support.microsoft.com/help/2023835/certificate-thumbprint-displayed-in-mmc-certificate-snap-in-has-extra) В качестве решения введите первый символ отпечатка и скопируйте/вставьте остальные символы.

- Using port below 1024 is not supported. In service mode, you may optionally configure port 80 to redirect to your specified port.

## <a name="general"></a>"Общие"

- If you have Windows Admin Center installed as a gateway on **Windows Server 2016** under heavy use, the service may crash with an error in the event log that contains ```Faulting application name: sme.exe``` and ```Faulting module name: WsmSvc.dll```. This is due to a bug that has been fixed in Windows Server 2019. The patch for Windows Server 2016 was included the February 2019 cumulative update, [KB4480977](https://www.catalog.update.microsoft.com/Search.aspx?q=4480977).

- If you have Windows Admin Center installed as a gateway and your connection list appears to be corrupted, perform the following steps:

   > [!WARNING]
   >This will delete the connection list and settings for all Windows Admin Center users on the gateway.

  1. Удалите Windows Admin Center
  2. Удалите папку **Интерфейс управления сервером** в разделе **C:\Windows\ServiceProfiles\NetworkService\AppData\Roaming\Microsoft**
  3. Переустановите Windows Admin Center

- Если не закрыть средство и не пользоваться им в течение длительного периода времени, может возникнуть несколько ошибок **Ошибка: недопустимое состояние пространства выполнения этой операции**. В этом случае обновите окно браузера. If you encounter this, [send us feedback](https://aka.ms/WACfeedback).

- There may be minor variance between version numbers of OSS running in Windows Admin Center modules, and what is listed within the 3rd Party Software Notice.

### <a name="extension-manager"></a>Extension Manager

- When you update Windows Admin Center, you must reinstall your extensions.
- If you add an extension feed that is inaccessible, there is no warning. [14412861]

## <a name="browser-specific-issues"></a>Проблемы, связанные с браузером

### <a name="microsoft-edge"></a>Microsoft Edge

- If you have Windows Admin Center deployed as a service and you are using Microsoft Edge as your browser, connecting your gateway to Azure may fail after spawning a new browser window. Try to work around this issue by adding https://login.microsoftonline.com, https://login.live.com, and the URL of your gateway as trusted sites and allowed sites for pop-up blocker settings on your client side browser. For more guidance on fixing this in the [troubleshooting guide](troubleshooting.md#azure-features-dont-work-properly-in-edge). [17990376]

### <a name="google-chrome"></a>Google Chrome

- Prior to version 70 (released late October, 2018) Chrome had a [bug](https://bugs.chromium.org/p/chromium/issues/detail?id=423609) regarding the websockets protocol and NTLM authentication. Она влияет на работу следующих средств: "События", PowerShell, "Удаленный рабочий стол".

- Chrome может отобразить несколько запросов на ввод учетных данных, в частности, во время добавления подключения в среде **рабочей группы** (не входящей в домен).

- If you have Windows Admin Center deployed as a service, popups from the gateway URL need to be enabled for any Azure integration functionality to work.

### <a name="mozilla-firefox"></a>Mozilla Firefox

Платформа Windows Admin Center не тестировалась с Mozilla Firefox, однако большинство функций должны работать.

- Windows 10 Installation: Mozilla Firefox has it's own certificate store, so you must import the ```Windows Admin Center Client``` certificate into Firefox to use Windows Admin Center on Windows 10.

## <a name="websocket-compatibility-when-using-a-proxy-service"></a>WebSocket compatibility when using a proxy service

Модули "Удаленный рабочий стол", PowerShell и "События" в Windows Admin Center используют протокол WebSocket, который часто не поддерживается при использовании службы прокси-сервера. Поддержка WebSocket в прокси-сервере приложений Azure AD находится [на этапе тестирования](https://blogs.technet.microsoft.com/applicationproxyblog/2018/03/28/limited-websocket-support-now-in-public-preview/). В настоящий момент осуществляется сбор сведений об их совместимости.

## <a name="support-for-windows-server-versions-before-2016-2012-r2-2012-2008-r2"></a>Support for Windows Server versions before 2016 (2012 R2, 2012, 2008 R2)

> [!NOTE]
> Windows Admin Center requires PowerShell features that are not included in Windows Server 2012 R2, 2012, or 2008 R2. If you will manage Windows Server these with Windows Admin Center, you will need to install WMF version 5.1 or higher on those servers.

Введите `$PSVersiontable` в PowerShell, чтобы проверить, что платформа WMF установлена, и что используется версия 5.1 или более поздняя версия.

Если она не установлена, можно [скачать и установить WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616).

## <a name="role-based-access-control-rbac"></a>Role Based Access Control (RBAC)

- Развертывание RBAC не будет выполнено на компьютерах, которые настроены на использование функции управления приложениями в Защитнике Windows (WDAC, ранее эта функция называлась "Целостность кода".)[16568455]

- Чтобы использовать RBAC в кластере, необходимо развернуть конфигурацию на каждом элементе узла по отдельности.

- При развертывании RBAC могут возникнуть неавторизованные ошибки, которые неправильно связаны с конфигурацией RBAC. [16369238]

## <a name="server-manager-solution"></a>Решение "Диспетчер серверов"

### <a name="certificates"></a>Сертификаты

- Невозможность импорта зашифрованного сертификата PFX в хранилище текущего пользователя. [11818622]

### <a name="events"></a>Мероприятия

- На события оказывает влияние [совместимость с WebSocket при использовании службы прокси-сервера.](#websocket-compatibility-when-using-a-proxy-service)

- Возможна ошибка, ссылающаяся на "размер пакета" при экспорте больших файлов журнала.

  - To resolve this, use the following command in an elevated command prompt on the gateway machine: ```winrm set winrm/config @{MaxEnvelopeSizekb="8192"}```

### <a name="files"></a>Файлы

- Передача и скачивание больших файлов еще не поддерживаются. (\~100mb limit) [12524234]

### <a name="powershell"></a>PowerShell

- На PowerShell влияет [совместимость с WebSocket при использовании службы прокси-сервера](#websocket-compatibility-when-using-a-proxy-service)

- Вставка с помощью одного щелчка правой кнопкой мыши, как в консоли PowerShell рабочего стола, не работает. Вместо этого откроется контекстное меню браузера, в котором можно выбрать команду "Вставить". Сочетание клавиш CTRL + V также работает.

- Сочетание клавиш CTRL + C для копирования не работает. При его использовании отправляется команда BREAK на консоль. Команда "Копировать" из контекстного меню, вызываемого правой кнопкой мыши, работает.

- При уменьшении окна Windows Admin Center содержимое терминала переформатируется, однако при его обратном увеличении содержимое может не вернуться в прежнее состояние. При перемешивании элементов содержимого можно попробовать выполнить команду Clear-Host или отключиться и повторно подключиться, используя кнопку над терминалом.

### <a name="registry-editor"></a>Редактор реестра

- Возможность поиска не реализована. [13820009]

### <a name="remote-desktop"></a>Удаленный рабочий стол

- When Windows Admin Center is deployed as a service, the Remote Desktop tool may fail to load after updating the Windows Admin Center service to a new version. To work around this issue, clear your browser cache.   [23824194]

- The Remote Desktop tool may fail to connect when managing Windows Server 2012. [20258278]

- When using the Remote Desktop to connect to a machine that is not Domain joined, you must enter your account in the ```MACHINENAME\USERNAME``` format.

- Some configurations can block Windows Admin Center's remote desktop client with group policy. If you encounter this, enable ```Allow users to connect remotely by using Remote Desktop Services``` under ```Computer Configuration/Policies/Administrative Templates/Windows Components/Remote Desktop Services/Remote Desktop Session Host/Connections```

- Remote Desktop is effected by [websocket compatibility.](#websocket-compatibility-when-using-a-proxy-service)

- Средство "Удаленный рабочий стол" в настоящий момент не поддерживает копирование/вставку любого текста, изображения или файла между локальным рабочим столом и удаленным сеансом.

- Чтобы выполнить операцию копирования/вставки в рамках удаленного сеанса, можно выполнить стандартную операцию копирования (правая кнопка мыши + "Копировать" или сочетание клавиш Ctrl + C), но чтобы вставить скопированный элемент, необходимо щелкнуть правой кнопкой мыши и выбрать "Вставить" (сочетание клавиш Ctrl + V НЕ РАБОТАЕТ).

- Следующие сочетания клавиш нельзя использовать в удаленном сеансе
  - ALT + Tab
  - Функциональные клавиши
  - Клавиша Windows
  - PRINT SCREEN

### <a name="roles-and-features"></a>Роли и компоненты

- При выборе ролей и компонентов с источниками, недоступным для установки, они пропускаются. [12946914]

- Если вы решаете не выполнять автоматическую перезагрузку после установки роли, новый запрос на это действие не отображается. [13098852]

- При выборе автоматической перезагрузки она произойдет до того, как состояние обновится до 100%. [13098852]

### <a name="storage"></a>Хранилище

- Нижний уровень: DVD-диски, компакт-диски или гибкие диски не отображаются в виде тома на нижнем уровне.

- Нижний уровень: некоторые свойства томов и дисков недоступны на нижнем уровне, поэтому они отображаются как неизвестные или пустые в области сведений.

- Нижний уровень: при создании нового тома файловая система ReFS поддерживает только размер кластера в 64 КБ на компьютерах с Windows 2012 и 2012 R2 При создании тома ReFS с меньшим размером кластера на целевых компьютерах нижнего уровня форматирование файловой системы заканчивается сбоем. Использовать новый том будет невозможно. Решение: удалите том и используйте кластер размером 64 КБ.

### <a name="updates"></a>Обновления

- After installing updates, install status may be cached and require a browser refresh.

- You may encounter the error: "Keyset does not exist" when attempting to set up Azure Update management. In this case, please try the following remediation steps on the managed node -
    1. Stop ‘Cryptographic Services' service.
    2. Change folder options to show hidden files (if required).
    3. Got to “%allusersprofile%\Microsoft\Crypto\RSA\S-1-5-18” folder and delete all its contents.
    4. Restart ‘Cryptographic Services' service.
    5. Repeat setting up Update Management with Windows Admin Center

### <a name="virtual-machines"></a>Виртуальные машины

- When managing the virtual machines on a Windows Server 2012 host, the in-browser VM connect tool will fail to connect to the VM. Downloading the .rdp file to connect to the VM should still work. [20258278]

- Azure Site Recovery – If ASR is setup on the host outside of WAC, you will be unable to protect a VM from within WAC [18972276]

- Дополнительные функции, доступные в диспетчере Hyper-V, такие как "Диспетчер виртуальной SAN", "Перемещение виртуальных машин", "Экспорт виртуальных машин", "Репликация виртуальных машин", в настоящее время не поддерживаются.

### <a name="virtual-switches"></a>Виртуальные коммутаторы

- Объединение внедренных коммутаторов (SET): при добавлении сетевых адаптеров в группу они должны быть в одной подсети.

## <a name="computer-management-solution"></a>Решение "Управление компьютерами"

Решение "Управление компьютерами" содержит набор средств из решения "Диспетчер серверов", поэтому к нему относятся те же известные проблемы, а также следующие конкретные проблемы, характерные только для этого решения.

- If you use a Microsoft Account ([MSA](https://account.microsoft.com/account/)) or if you use Azure Active Directory (AAD) to log on to you Windows 10 machine, you must use "manage-as" to provide credentials for a local administrator account [16568455]

- При попытке управления локальным узлом вам будет предложено повысить уровень процесса шлюза. Если нажать кнопку **Нет** во всплывающем окне "Контроль учетных записей", Windows Admin Center не сможет его повторно отобразить. В этом случае завершите процесс шлюза, щелкнув правой кнопкой мыши значок Windows Admin Center на панели задач и выберите "Выйти", а затем перезапустите Windows Admin Center из меню "Пуск".

- Windows 10 не поддерживает удаленное взаимодействие WinRM/PowerShell по умолчанию
  
  - Чтобы включить управление клиентом Windows 10, необходимо выполнить команду ```Enable-PSRemoting``` из командной строки PowerShell с повышенными привилегиями.

  - Также может потребоваться обновить межсетевой экран, чтобы разрешить подключения вне локальной подсети с помощью команды ```Set-NetFirewallRule -Name WINRM-HTTP-In-TCP -RemoteAddress Any```. Инструкции по реализации более жестких ограничительных сценариев см. в [этой документации](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting?view=powershell-5.1).

## <a name="failover-cluster-manager-solution"></a>Решение "Диспетчер отказоустойчивости кластеров"

- При управлении кластером (гиперконвергентным или традиционным) может возникнуть ошибка **Оболочка не найдена**. В этом случае перезагрузите браузер либо перейдите к другому инструменту и обратно. [13882442]

- Проблема может возникнуть при управлении кластером нижнего уровня (Windows Server 2012 или 2012 R2), который был настроен неполностью. Чтобы устранить эту проблему, убедитесь, что компонент Windows **RSAT-Clustering-PowerShell** установлен и для кластера задано значение **каждый элемент узла**. Чтобы сделать это с помощью PowerShell, введите команду `Install-WindowsFeature -Name RSAT-Windows-PowerShell` на всех узлах кластера. [12524664]

- Может потребоваться добавить кластер с полным доменным именем, чтобы его можно было правильно обнаружить.

- При подключении к кластеру с помощью платформы Windows Admin Center, установленной в качестве шлюза, и предоставлении явных имени пользователя/пароля для проверки подлинности необходимо выбрать пункт **Использовать эти учетные данные для всех подключений**, чтобы учетные данные могли опрашивать элементы узлов.

## <a name="hyper-converged-cluster-manager-solution"></a>Решение "Диспетчер гиперконвергентных кластеров"

- Некоторые команды, например **Диски – Обновление встроенного ПО**, **Серверы – Удаление** и **Тома – Открыть** отключены и в настоящее время не поддерживаются.

## <a name="azure-services"></a>Azure services

### <a name="azure-file-sync-permissions"></a>Azure File Sync permissions

Azure File Sync requires permissions in Azure that Windows Admin Center did not provide prior to version 1910. If you registered your Windows Admin Center gateway with Azure using a version earlier than Windows Admin Center version 1910, you will need to update your Azure Active Directory application to get the correct permissions to use Azure File Sync in the latest version of Windows Admin Center. The additional permission allows Azure File Sync to perform automatic configuration of storage account access as described in this article: [Ensure Azure File Sync has access to the storage account](https://docs.microsoft.com/azure/storage/files/storage-sync-files-troubleshoot?tabs=portal1%2Cazure-portal#tabpanel_CeZOj-G++Q-5_azure-portal).

To update your Azure Active Directory app, you can do one of two things
1. Go to **Settings** > **Azure** > **Unregister**, and then register Windows Admin Center with Azure again, making sure you choose to create a new Azure Active Directory application. 
2. Go to your Azure Active Directory application and manually add the permission needed to your existing Azure Active Directory app registered with Windows Admin Center. To do this, go to **Settings** > **Azure** > **View in Azure**. From the **App Registration** blade in Azure, go to **API permissions**, select **Add a permission**. Scroll down to select **Azure Active Directory Graph**, select **Delegated permissions**, expand **Directory**, and select **Directory.AccessAsUser.All**. Click **Add permissions** to save the updates to the app.

### <a name="options-for-setting-up-azure-management-services"></a>Options for setting up Azure management services

Azure management services including Azure Monitor, Azure Update Management, and Azure Security Center, use the same agent for an on-premises server: the Microsoft Monitoring Agent. Azure Update Management has a more limited set of supported regions and requires the Log Analytics workspace to be linked to an Azure Automation account. Because of this limitation, if you wish to set up multiple services in Windows Admin Center, you must set up Azure Update Management first, and then either Azure Security Center or Azure Monitor. If you've configured any Azure management services that use the Microsoft Monitoring Agent, and then try to set up Azure Update Management using Windows Admin Center, Windows Admin Center will only allow you to configure Azure Update Management if the existing resources linked to the Microsoft Monitoring Agent support Azure Update Management. If this is not the case you have two options:

1. Go to the Control Panel > Microsoft Monitoring Agent to [disconnect your server from the existing Azure management solutions](https://docs.microsoft.com/azure/azure-monitor/platform/log-faq#q-how-do-i-stop-an-agent-from-communicating-with-log-analytics) (like Azure Monitor or Azure Security Center). Then set up Azure Update Management in Windows Admin Center. After that, you can go back to set up your other Azure management solutions through Windows Admin Center without issues.
2. You can [manually set up the Azure resources needed for Azure Update Management](https://docs.microsoft.com/azure/automation/automation-update-management) and then [manually update the Microsoft Monitoring Agent](https://docs.microsoft.com/azure/azure-monitor/platform/agent-manage#adding-or-removing-a-workspace) (outside of Windows Admin Center) to add the new workspace corresponding to the Update Management solution you wish to use.
