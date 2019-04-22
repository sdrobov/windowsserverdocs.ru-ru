---
title: Управление виртуальными машинами Windows с помощью PowerShell Direct
description: Инструкции по использованию PowerShell Direct для управления виртуальными машинами, не полагаясь на сети или удаленного подключения к ним.
ms.prod: windows-server-threshold
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b5715c02-a90f-4de9-a71e-0fc09093ba2d
author: KBDAzure
ms.author: kathydav
ms.date: 10/04/2016
ms.openlocfilehash: 4081a9737825d2f50f0d3b19b3bada3b9bbc76f1
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59814705"
---
# <a name="manage-windows-virtual-machines-with-powershell-direct"></a>Управление виртуальными машинами Windows с помощью PowerShell Direct

>Область применения. Windows 10, Windows Server 2016, Windows Server 2019 г.
  
PowerShell Direct можно использовать для удаленного управления Windows 10, Windows Server 2016 или Windows Server 2019 виртуальной машины с узла Windows 10, Windows Server 2016 или Windows Server 2019 Hyper-V. PowerShell Direct можно управлять виртуальной машиной средствами независимо от конфигурации сети и параметров удаленного управления на узле Hyper-V или виртуальной машины Windows PowerShell. Это позволяет администраторам Hyper-V автоматизировать управление и настройку виртуальных машин с помощью сценариев.  
  
Запустить PowerShell Direct можно двумя способами:  
  
- Создать и завершить сеанс PowerShell Direct с помощью командлетов PSSession
  
- Запустить сценарий или команду с помощью командлета Invoke-Command
  
Если вы управляете виртуальными машинами более ранних версий, используйте средство "Подключение к виртуальной машине" (VMConnect) или [настройте для этой машины виртуальную сеть](https://technet.microsoft.com/library/cc816585.aspx).  
  
## <a name="create-and-exit-a-powershell-direct-session-using-pssession-cmdlets"></a>Создать и завершить сеанс PowerShell Direct с помощью командлетов PSSession  
  
1. На узле Hyper-V откройте Windows PowerShell от имени администратора.  
  
2. Используйте [Enter-PSSession](https://technet.microsoft.com/library/hh849707.aspx) для подключения к виртуальной машине. Выполните одну из следующих команд, чтобы создать сеанс, используя имя виртуальной машины или GUID.  
  
    ```  
    Enter-PSSession -VMName <VMName>  
    ```  
  
    ```  
    Enter-PSSession -VMGUID <VMGUID>  
    ```  
  
3. Введите свои учетные данные для виртуальной машины.   
4. Выполните все необходимые команды. Эти команды выполняются на виртуальной машине, в которой был создан сеанс.  
  
5.  Когда все будет готово, используйте [Exit-PSSession](https://technet.microsoft.com/library/hh849743.aspx) к закрытию сеанса.   
  
    ```  
    Exit-PSSession  
    ```  
  
## <a name="run-script-or-command-with-invoke-command-cmdlet"></a>Выполнить сценарий или команду с помощью командлета Invoke-Command  
Выполнить предварительно определенный набор команд на виртуальной машине можно с помощью командлета [Invoke-Command](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Invoke-Command). Ниже приведен пример использования командлета Invoke-Command, где PSTest — это имя виртуальной машины, а сценарий, который требуется запустить,(foo.ps1) находится в папке сценария (script) на диске C:  
  
```  
Invoke-Command -VMName PSTest  -FilePath C:\script\foo.ps1  
```  
  
Чтобы выполнить одну команду, используйте параметр **-ScriptBlock**:  
  
```  
Invoke-Command -VMName PSTest  -ScriptBlock { cmdlet }  
```  
  
## <a name="whats-required-to-use-powershell-direct"></a>Что необходимо сделать для использования PowerShell Direct?  
Чтобы создать сеанс PowerShell Direct на виртуальной машине:  
  
-   Виртуальная машина должна работать на узле локально и быть загружена.  
  
-   Необходимо войти в учетную запись администратора Hyper-V на хост-компьютере.  
  
-   Необходимо указать действительные учетные данные пользователя для виртуальной машины.  
  
-   Операционной системы должна быть установлена Windows 10 или Windows Server 2016.
  
-   Виртуальная машина должна быть установлена Windows 10 или Windows Server 2016.  
  
Можно использовать [Get-VM](https://docs.microsoft.com/powershell/module/hyper-v/get-vm) командлета убедитесь, что учетные данные, вы используете роль администратора Hyper-V и получить список виртуальных машин, работающих локально на узле и загружены.  
  
## <a name="see-also"></a>См. также  
[ENTER-PSSession](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession)  
[Exit-PSSession](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession)  
[Invoke-Command](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Invoke-Command)  
  


