---
title: Обновление сервера Nano Server
description: " "
ms.prod: windows-server-threshold
ms.service: na
manager: DonGill
ms.technology: server-nano
ms.date: 09/06/2017
ms.tgt_pltfrm: na
ms.topic: get-started-article
author: jaimeo
ms.author: jaimeo
ms.localizationpriority: medium
ms.openlocfilehash: 7f74b35e93d4ddbe39b955daf7f78c4ef693aa9a
ms.sourcegitcommit: 07ac08dea2b8f2763c2614a999dc7967018aa0b4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2018
ms.locfileid: "6121473"
---
# Обновление сервера Nano Server

> [!IMPORTANT]
> Начиная с Windows Server версии 1709, сервер Nano Server будет доступен только в качестве [базового образа ОС контейнера](/virtualization/windowscontainers/quick-start/using-insider-container-images#install-base-container-image). Ознакомьтесь с разделом [Изменения сервера Nano Server](nano-in-semi-annual-channel.md), чтобы узнать, что это означает. 

Сервер Nano Server предоставляет несколько способов поддержания системы в актуальном состоянии. По сравнению с другими вариантами установки Windows Server сервер Nano Server имеет более активную модуль обслуживания, похожую на Windows10. Такие периодические выпуски называют выпусками **Current Branch for Business (CBB)**. Этот подход обеспечивает поддержку клиентов, которые желают реализовывать инновации более быстро и следовать быстрым жизненным циклам разработки облачных технологий. Дополнительные сведения о CBB доступны в блоге [Windows Server](https://blogs.technet.microsoft.com/windowsserver/2016/07/12/windows-server-2016-new-current-branch-for-business-servicing-option/).

**Между выпусками CBB** актуальное состояние сервера Nano Server поддерживается благодаря ряду *накопительных обновлений*. Например первое накопительное обновление для сервера Nano Server была выпущена 26 сентября 2016 с [KB4093120](https://support.microsoft.com/help/4093120/windows-10-update-kb4093120). Доступность этого и последующих накопительных обновлений позволяет нам предоставлять вам различные варианты установки этих обновлений на сервере Nano Server. В этой статье мы будем использовать обновление KB3192366 в качестве примера, чтобы показать получение и применение накопительных обновлений для сервера Nano Server. Дополнительные сведения о модели накопительных обновлений см. в блоге [Центра обновления Майкрософт](https://blogs.technet.microsoft.com/mu/2016/10/25/patching-with-windows-server-2016/).

> [!NOTE]
> Если устанавливается необязательный пакет Nano Server с носителя или из онлайн-репозитория, он не будет содержать последних исправлений безопасности. Чтобы избежать несоответствия версий дополнительных пакетов и базовой операционной системы, последний накопительный пакет обновления следует установить сразу после установки любых дополнительных пакетов и **перед** перезапуском сервера.

В случае накопительного обновления для Windows Server 2016 от 26 сентября 2016 г. ([KB3192366](https://support.microsoft.com/en-us/kb/3192366)): необходимо сначала установить последнее обновление служебного стека для Windows 10 версии 1607 от 23 августа 2016 г. в качестве обязательного компонента ([KB3176936](https://support.microsoft.com/en-us/kb/3176936)). Для большинства следующих вариантов потребуются MSU-файлы, содержащие CAB-пакеты обновления. Посетите каталог Центра обновления Майкрософт, чтобы загрузить каждый из этих пакетов обновления:
- [https://catalog.update.microsoft.com/v7/site/Search.aspx?q=KB3192366](https://catalog.update.microsoft.com/v7/site/Search.aspx?q=KB3192366)
- [https://catalog.update.microsoft.com/v7/site/Search.aspx?q=KB3176936](https://catalog.update.microsoft.com/v7/site/Search.aspx?q=KB3176936)

После загрузки MSU-файлов из каталога Центра обновления Майкрософт сохраните их в общей сетевой папке или локальном каталоге, например C:\ServicingPackages. Вы можете переименовать MSU-файлов, используя их номер в базе знаний, как это сделано ниже, чтобы их было легче идентифицировать. Затем воспользуйтесь служебной программой EXPAND, чтобы извлечь CAB-файлы из MSU-файлов в отдельные каталоги и копировать первые в одну папку.

```code
    mkdir C:\ServicingPackages_expanded
    mkdir C:\ServicingPackages_expanded\KB3176936
    mkdir C:\ServicingPackages_expanded\KB3192366
    Expand C:\ServicingPackages\KB3176936.msu -F:* C:\ServicingPackages_expanded\KB3176936
    Expand C:\ServicingPackages\KB3192366.msu -F:* C:\ServicingPackages_expanded\KB3192366
    mkdir C:\ServicingPackages_cabs
    copy C:\ServicingPackages_expanded\KB3176936\Windows10.0-KB3176936-x64.cab C:\ServicingPackages_cabs
    copy C:\ServicingPackages_expanded\KB3192366\Windows10.0-KB3192366-x64.cab C:\ServicingPackages_cabs
```

Теперь извлеченные CAB-файлы можно использовать для применения обновлений к образу сервера Nano Server разными способами в зависимости от ваших потребностей. Варианты ниже представлены в произвольном порядке— используйте наиболее подходящий для вашей среды.

> [!NOTE]
> При использовании средств DISM для обслуживания сервера Nano Server необходимо использовать версию DISM не ниже версии обслуживаемого сервера Nano Server. Для этого нужно запустить DISM из соответствующей версии Windows, установить подходящую версию [Комплекта средств для развертывания и оценки (ADK)](https://developer.microsoft.com/en-us/windows/hardware/windows-assessment-deployment-kit) или запустить DISM на самом сервере Nano Server.

## Вариант 1. Интеграция накопительного обновления в новый образ
Если вы создаете новый образ сервера Nano Server, можно интегрировать последнее накопительное обновление непосредственно в образ, чтобы установить все обновления при первой загрузке.

```powershell
New-NanoServerImage -ServicingPackagePath 'C:\ServicingPackages_cabs\Windows10.0-KB3176936-x64.cab', 'C:\ServicingPackages_cabs\Windows10.0-KB3192366-x64.cab' -<other parameters>
```

## Вариант 2. Интеграция накопительного обновления в существующий образ
При наличии существующего образа сервера Nano Server, который вы используете как основу для создания определенных экземпляров сервера Nano Server, можно интегрировать последнее накопительное обновление непосредственно в существующий базовый образ, чтобы все обновления устанавливались при первой загрузке машин, созданных с помощью этого образа.

```powershell
Edit-NanoServerImage -ServicingPackagePath 'C:\ServicingPackages_cabs\Windows10.0-KB3176936-x64.cab', 'C:\ServicingPackages_cabs\Windows10.0-KB3192366-x64.cab' -TargetPath .\NanoServer.wim
```

## Вариант 3. Применение накопительного обновления к существующему автономному диску VHD или VHDX.
Если у вас есть существующий виртуальный жесткий диск (VHD или VHDX), применить обновление к виртуальному жесткому диску можно с помощью средств DISM. Необходимо убедиться, что диск не используется, завершив работу всех виртуальных машин, использующих диск, или отключив файл виртуального жесткого диска.

- Использование PowerShell

   ```powershell
   Mount-WindowsImage -ImagePath .\NanoServer.vhdx -Path .\MountDir -Index 1
   Add-WindowsPackage -Path .\MountDir -PackagePath  C:\ServicingPackages_cabs
   Dismount-WindowsImage -Path .\MountDir -Save
   ```

- Использование dism.exe

   ```code
   dism.exe /Mount-Image /ImageFile:C:\NanoServer.vhdx /Index:1 /MountDir:C:\MountDir
   dism.exe /Image:C:\MountDir /Add-Package /PackagePath:C:\ServicingPackages_cabs
   dism.exe /Unmount-Image /MountDir:C:\MountDir /Commit
   ```

## Вариант 4. Применение накопительного обновления к работающему серверу Nano Server
Если у вас есть работающая виртуальная машина или физический хост Nano Server и вы загрузили CAB-файл для обновления, применить обновление к подключенной к сети системе можно с помощью средств DISM. Потребуется копировать CAB-файл локально на сервер Nano Server или в доступное сетевое расположение. Если вы применяете обновление для служебного стека, не забудьте перезапустить сервер после применения обновления для служебного стека и до применения дополнительных обновлений.

> [!NOTE]
> Если образ диска VHD или VHDX сервера Nano Server создан с использованием командлета New-NanoServerImage и вы не указали параметр MaxSize для файла виртуального жесткого диска, размер по умолчанию (4ГБ) слишком мал, чтобы применить накопительное обновление. Перед установкой обновления используйте диспетчер Hyper-V, средство управления дисками, PowerShell или другое средство для увеличения размера виртуального жесткого диска и системного тома по меньшей мере до 10ГБ или воспользуйтесь параметром ScratchDir в составе средств DISM, чтобы задать для каталога временных файлов том с объемом свободного пространства не менее 10ГБ.

```powershell
$s = New-PSSession -ComputerName (Read-Host "Enter Nano Server IP address") -Credential (Get-Credential)
Copy-Item -ToSession $s -Path C:\ServicingPackages_cabs -Destination C:\ServicingPackages_cabs -Recurse
Enter-PSSession $s
```

- Использование PowerShell

   ```powershell
   # Apply the servicing stack update first and then restart
   Add-WindowsPackage -Online -PackagePath C:\ServicingPackages_cabs\Windows10.0-KB3176936-x64.cab
   Restart-Computer; exit

   # After restarting, apply the cumulative update and then restart
   Enter-PSSession -ComputerName (Read-Host "Enter Nano Server IP address") -Credential (Get-Credential)
   Add-WindowsPackage -Online -PackagePath C:\ServicingPackages_cabs\Windows10.0-KB3192366-x64.cab
   Restart-Computer; exit
   ```

- Использование dism.exe
   ```powershell
   # Apply the servicing stack update first and then restart
   dism.exe /Online /Add-Package /PackagePath:C:\ServicingPackages_cabs\Windows10.0-KB3176936-x64.cab
   
   # After the operation completes successfully and you are prompted to restart, it's safe to
   # press Ctrl+C to cancel the pipeline and return to the prompt
   Restart-Computer; exit

   # After restarting, apply the cumulative update and then restart
   Enter-PSSession -ComputerName (Read-Host "Enter Nano Server IP address") -Credential (Get-Credential)
   dism.exe /Online /Add-Package /PackagePath:C:\ServicingPackages_cabs\Windows10.0-KB3192366-x64.cab
   Restart-Computer; exit
   ```

## Вариант 5. Загрузка и установка накопительного обновления на работающем сервере Nano Server

Если имеется работающая виртуальная машина или физический хост сервера Nano Server, можно использовать поставщика WMI Центра обновления Windows для загрузки и установки обновления в подключенной к сети операционной системе. При использовании этого метода загружать MSU-файл отдельно от каталога Центра обновления Майкрософт не требуется. Поставщик WMI обнаружит, загрузит и установит все доступные обновления одновременно.

```powershell
Enter-PSSession -ComputerName (Read-Host "Enter Nano Server IP address") -Credential (Get-Credential)
```

- Сканирование на наличие доступных обновлений
   ```powershell
   $ci = New-CimInstance -Namespace root/Microsoft/Windows/WindowsUpdate -ClassName MSFT_WUOperationsSession  
   $result = $ci | Invoke-CimMethod -MethodName ScanForUpdates -Arguments @{SearchCriteria="IsInstalled=0";OnlineScan=$true}
   $result.Updates
   ```

- Установка всех доступных обновлений
   ```powershell
   $ci = New-CimInstance -Namespace root/Microsoft/Windows/WindowsUpdate -ClassName MSFT_WUOperationsSession
   Invoke-CimMethod -InputObject $ci -MethodName ApplyApplicableUpdates
   Restart-Computer; exit
   ```

- Получение списка установленных обновлений
   ```powershell
   $ci = New-CimInstance -Namespace root/Microsoft/Windows/WindowsUpdate -ClassName MSFT_WUOperationsSession
   $result = $ci | Invoke-CimMethod -MethodName ScanForUpdates -Arguments @{SearchCriteria="IsInstalled=1";OnlineScan=$true}
   $result.Updates
   ```
   
## Дополнительные варианты
Другие методы обновления сервера Nano Server могут частично совпадать с вышеперечисленными или дополнять их. Эти варианты включают использование служб Windows Server Update Services (WSUS), диспетчера System Center Virtual Machine Manager (VMM), Планировщика задач или стороннее решение.
- [Настройте Центр обновления Windows для WSUS](https://msdn.microsoft.com/en-us/library/dd939844(v=ws.10).aspx), установив следующие разделы реестра:
  - WUServer
  - WUStatusServer (как правило, значение совпадает со значением WUServer)
  - UseWUServer
  - AUOptions
- [Управление обновлениями структуры в VMM](https://technet.microsoft.com/library/gg675084(v=sc.12).aspx)
- [Регистрация запланированной задачи](https://technet.microsoft.com/library/jj649811.aspx)