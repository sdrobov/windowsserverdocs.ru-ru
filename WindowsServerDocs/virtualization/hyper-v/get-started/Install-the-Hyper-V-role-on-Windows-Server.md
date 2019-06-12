---
title: Установка роли Hyper-V в Windows Server
description: Инструкции по установке Hyper-V с помощью диспетчера серверов или Windows PowerShell
ms.prod: windows-server-threshold
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 8e871317-09d2-4314-a6ec-ced12b7aee89
author: KBDAzure
ms.author: kathydav
ms.date: 12/02/2016
ms.openlocfilehash: 80154c569701608ad190fb76eb3737578895d187
ms.sourcegitcommit: 6ef4986391607bb28593852d06cc6645e548a4b3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66812378"
---
# <a name="install-the-hyper-v-role-on-windows-server"></a>Установка роли Hyper-V в Windows Server

>Область применения. Windows Server 2016, Windows Server 2019 г.
  
Для создания и запуска виртуальных машин, установить роль Hyper-V в Windows Server с помощью диспетчера серверов или **Install-WindowsFeature** в Windows PowerShell. Windows 10, см. в разделе [Установка Hyper-V в Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).

Дополнительные сведения о Hyper-V, см. в разделе [Общие сведения о технологии Hyper-V](../Hyper-V-Technology-Overview.md). Чтобы опробовать Windows Server 2019, можно загрузить и установить пробную. См. в разделе [центре оценки программного обеспечения](https://www.microsoft.com/evalcenter/evaluate-windows-server-2019).

Перед установкой Windows Server или Добавление роли Hyper-V, убедитесь, что:
- Совместима оборудования компьютера. Дополнительные сведения см. в разделе [требования к системе для Windows Server](../../../get-started/System-Requirements.md) и [требования к системе для Hyper-V в Windows Server](../System-requirements-for-Hyper-V-on-Windows.md).
- Вы не планируете использовать виртуализации сторонних приложений, основанных на те же функции процессора, необходимых для Hyper-V. Например, VMWare Workstation и VirtualBox. Можно установить Hyper-V, не удалив эти другие приложения. Но при попытке использовать их для управления виртуальными машинами, при выполнении низкоуровневой оболочки Hyper-V, виртуальных машин может не запуститься или привести может выполняться. Дополнительные сведения и инструкции для выключения низкоуровневой оболочки Hyper-V, если необходимо использовать одно из этих приложений, см. в разделе [виртуализации приложения не работают вместе с Hyper-V, Device Guard и Credential Guard](https://support.microsoft.com/help/3204980/virtualization-applications-do-not-work-together-with-hyper-v-device-g).

Если вы хотите установить только средства управления, такие как диспетчер Hyper-V, см. в разделе [удаленно управлять узлами Hyper-V с помощью диспетчера Hyper-V](../Manage/Remotely-manage-Hyper-V-hosts.md).
  
## <a name="install-hyper-v-by-using-server-manager"></a>Установите Hyper-V с помощью диспетчера серверов  
  
1. В **диспетчере серверов** в меню **Управление** выберите **Добавить роли и компоненты**.  
  
2. На странице **Приступая к работе** убедитесь, что конечный сервер и сетевое окружение подготовлены к установке нужной вам роли или компонента. Нажмите кнопку **Далее**.  
  
3. На странице **Выбор типа установки** выберите **Установка ролей или компонентов** и нажмите кнопку **Далее**.  
  
4. На странице **Выбор целевого сервера** выберите сервер из пула серверов и нажмите кнопку **Далее**.  
  
5. На странице **Выбор ролей сервера** выберите **Hyper-V**.  
  
6. Чтобы добавить средства для создания виртуальных машин и управления ими, щелкните **Добавить компоненты**. На странице компонентов нажмите кнопку **Далее**.  
  
7. Выберите нужные параметры на страницах **Создание виртуальных коммутаторов**, **Миграция виртуальной машины** и **Хранилища по умолчанию**.  
  
8. На странице **Подтверждение выбранных элементов для установки** выберите **Автоматический перезапуск конечного сервера, если требуется** и нажмите кнопку **Установить**.  
  
9. Когда установка будет завершена, проверьте правильность установки Hyper-V. Откройте **все серверы** странице в диспетчере сервера и выберите сервер, на котором установлен Hyper-V. Проверьте **роли и компоненты** на странице для выбранного сервера.  
  
## <a name="install-hyper-v-by-using-the-install-windowsfeature-cmdlet"></a>Установите Hyper-V с помощью командлета Install-WindowsFeature  
  
1. На рабочем столе Windows нажмите кнопку "Пуск" и введите любую часть имени **Windows PowerShell**.  
  
2. Щелкните правой кнопкой мыши Windows PowerShell и выберите **Запуск от имени администратора**.  
  
3. Чтобы установить Hyper-V на сервере, на удаленном подключении, выполните следующую команду и замените `<computer_name>` с именем сервера.  
  
    ```powershell
    Install-WindowsFeature -Name Hyper-V -ComputerName <computer_name> -IncludeManagementTools -Restart  
    ```  
  
    Если вы подключены локально на сервере, выполните команду без `-ComputerName <computer_name>`.  
  
4. После перезагрузки сервера, вы увидите что роль Hyper-V установлена и узнайте, какие другие роли и компоненты установлены, выполнив следующую команду:  
  
    ```powershell
    Get-WindowsFeature -ComputerName <computer_name>  
    ```  
  
    Если вы подключены локально на сервере, выполните команду без `-ComputerName <computer_name>`.  
  
> [!NOTE]  
> Если установить эту роль на сервере под управлением параметра установки основных серверных компонентов Windows Server 2016 и используйте параметр `-IncludeManagementTools`, устанавливается только Hyper-V Module for Windows PowerShell. Можно использовать средство управления графическим интерфейсом пользователя, диспетчер Hyper-V, на другом компьютере для удаленного управления сервером Hyper-V, который выполняется на установке Server Core. Инструкции по удаленное подключение, см. в разделе [удаленно управлять узлами Hyper-V с помощью диспетчера Hyper-V](../Manage/Remotely-manage-Hyper-V-hosts.md).  
  
## <a name="see-also"></a>См. также  
  
- [Install-WindowsFeature](https://docs.microsoft.com/powershell/module/Microsoft.Windows.ServerManager.Migration/Install-WindowsFeature)  
