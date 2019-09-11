---
title: Подключение к виртуальной машине Hyper-V
description: Описание подключения к виртуальной машине, которое обеспечивает удаленный доступ к виртуальной машине. Содержит сведения о том, как выполнять общие задачи, такие как отправка Ctrl-Alt-Delete на виртуальную машину.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
manager: dongill
ms.technology: compute-hyper-v
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: deae35b9-7647-42b8-b6bf-45645a44c9c4
author: KBDAzure
ms.author: kathydav
ms.date: 10/04/2016
ms.openlocfilehash: 04f3bc581a0065c62ba8878473e45f714ce8a069
ms.sourcegitcommit: f6490192d686f0a1e0c2ebe471f98e30105c0844
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70872106"
---
# <a name="hyper-v-virtual-machine-connection"></a>Подключение к виртуальной машине Hyper-V

>Область применения. Windows Server 2016, Windows 10, Windows 8.1, Windows Server 2012 R2, Windows Server 2012, Windows 8

Подключение \(к виртуальной машине\) VMConnect — это средство, которое используется для подключения к виртуальной машине, чтобы можно было установить или взаимодействовать с гостевой операционной системой на виртуальной машине. Ниже перечислены некоторые задачи, которые можно выполнить с помощью VMConnect.  
  
-   Запуск и завершение работы виртуальной машины  
  
-   Подключение к ISO-файлу \(\) образа DVD или флэш-накопителю USB  
  
-   Создание контрольной точки  
  
-   Изменение параметров виртуальной машины  
    
## <a name="tips-for-using-vmconnect"></a>Советы по использованию VMConnect  
Для использования VMConnect могут оказаться полезными следующие сведения:  
  
|Для этого...|Сделать это...|  
|---------------|------------|  
|Отправка щелчков мыши или ввода с клавиатуры на виртуальную машину|Щелкните в любом месте окна виртуальной машины. При подключении к работающей виртуальной машине указатель мыши может отображаться в виде маленькой точки.|  
|Возвращение щелчков мыши или ввода с клавиатуры на физический компьютер|Нажмите клавиши\+Ctrl\+Alt стрелка влево, а затем переместите указатель мыши за пределы окна виртуальной машины. Это сочетание клавиш для выпусков мыши можно изменить в\-параметрах Hyper v\-в диспетчере Hyper v.|  
|Отправка сочетания\+клавиш\+Ctrl Alt клавишу DELETE для виртуальной машины|Выберите **действие** > \+\+**CTRLAltShift\+или используйте сочетание клавиш Ctrl Alt End.\+**|  
|Переключение из режима окна в полноэкранный\-режим|Выберите режим **просмотра** > в**полноэкранном режиме**. Чтобы переключиться обратно в режим окна,\+нажмите\+клавиши CTRL ALT BREAK.|  
|Создание контрольной точки для записи текущего состояния компьютера для устранения неполадок|Выберите > **контрольная точка** действия или используйте сочетание клавиш\+CTRL N.|  
|Изменение параметров виртуальной машины|Выберите**Параметры** **файла** > .|  
|Подключение к \( \(ISO-файлу образа DVDиливиртуальномугибкомудиску.VFD\)\)|Выберите **носитель**.<br /><br />Виртуальные гибкие диски не поддерживаются для виртуальных машин версии 2. Дополнительные сведения см. [в статье Создание виртуальной машины поколения 1 или 2 в Hyper-V](../plan/Should-I-create-a-generation-1-or-2-virtual-machine-in-Hyper-V.md).|  
|Использование локальных ресурсов узла на виртуальной машине Hyper\--V, например USB-накопителе|Включите режим расширенного сеанса на узле Hyper-V, используйте VMConnect для подключения к виртуальной машине и перед подключением выберите локальный ресурс, который хотите использовать. Конкретные действия см. в статье [Использование локальных ресурсов на виртуальной\-машине Hyper V с VMConnect](Use-local-resources-on-Hyper-V-virtual-machine-with-VMConnect.md).|  
|Изменение сохраненных параметров VMConnect для виртуальной машины|Выполните следующую команду в Windows PowerShell или в командной строке:<br /><br />`VMConnect.exe <ServerName> <VMName> \/edit`|  
|Запретить пользователю VMConnect сеанс VMConnect другого пользователя|[Включите режим расширенного сеанса на узле Hyper-V](Use-local-resources-on-Hyper-V-virtual-machine-with-VMConnect.md#turn-on-enhanced-session-mode-on-a-hyper-v-host).<br /><br />Отсутствие включенного режима расширенного сеанса может представлять угрозу безопасности и конфиденциальности. Если пользователь подключен и вошел в виртуальную машину через VMConnect, а другой полномочный пользователь подключается к той же виртуальной машине, сеанс будет передаваться вторым пользователем, и первый пользователь потеряет сеанс. Второй пользователь сможет просматривать рабочий стол, документы и приложения первого пользователя.|
|Управление службами Integration Services или компонентами, которые позволяют виртуальной машине обмениваться данными с узлом Hyper-V| На узлах Hyper-V под управлением Windows 10 или Windows Server 2016 нельзя управлять службами Integration Services с помощью VMConnect. См. следующие разделы: <br />- [Включение и отключение служб Integration Services на узле Hyper-V](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/managing_ics) <br />- [Включение и отключение служб Integration Services с помощью виртуальной машины Windows](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/managing_ics#manage-integration-services-from-guest-os-windows)<br />- [Включение и отключение служб Integration Services на виртуальной машине Linux](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/managing_ics#manage-integration-services-from-guest-os-linux) <br />- [Обновление служб Integration Services для виртуальной машины](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/managing_ics#integration-service-maintenance)  <br />Сведения об узлах под управлением Windows Server 2012 или Windows Server 2012 R2 см. в разделе [Integration Services](https://technet.microsoft.com/library/dn798297(v=ws.11).aspx).|
|Изменение размера окна VMConnect|Вы можете изменить размер окна VMConnect для виртуальных машин поколения 2, работающих под управлением операционной системы Windows. Для этого может потребоваться включить режим расширенного сеанса на узле Hyper-V. Дополнительные сведения см. в разделе [Включение расширенного режима сеанса на узле Hyper-V](Use-local-resources-on-Hyper-V-virtual-machine-with-VMConnect.md#turn-on-enhanced-session-mode-on-a-hyper-v-host). Сведения о виртуальных машинах под управлением Ubuntu см. [в разделе Изменение разрешения экрана Ubuntu в виртуальной машине Hyper-V](https://blogs.msdn.microsoft.com/virtual_pc_guy/2014/09/19/changing-ubuntu-screen-resolution-in-a-hyper-v-vm/).|


## <a name="keyboard-shortcuts"></a>Сочетания клавиш  
По умолчанию ввод с клавиатуры и щелчки мыши отправляются на виртуальную машину. Поэтому может потребоваться нажать клавиши CTRL + ALT + стрелка влево, прежде чем использовать следующие сочетания клавиш. 

|Сочетание клавиш|Описание|  
|-------------------|---------------|  
|Ctrl\+Alt\+стрелка влево|Выпуск мыши|  
|CTRL\++\+КОНЕЦ|Эквивалентно клавише\+Ctrl\+Alt Delete на виртуальной машине|  
|CTRL\+ALT\+BREAK|Переключение из полноэкранного\-режима обратно в оконный режим|  
|CTRL\+O|Открывает параметры для виртуальной машины.|  
|CTRL\+S|Запуск виртуальной машины|  
|CTRL\+N|Создание контрольной точки|  
|CTRL\+E|Вернуться к контрольной точке|  
|CTRL\+C|Снимок экрана|  

## <a name="see-also"></a>См. также  
-   [Использование локальных ресурсов на виртуальной машине Hyper-V с VMConnect](Use-local-resources-on-Hyper-V-virtual-machine-with-VMConnect.md)  
-   [Hyper-V в Windows Server 2016](../Hyper-V-on-Windows-Server.md)  
-   [Hyper-V в Windows 10](https://msdn.microsoft.com/virtualization/hyperv_on_windows/windows_welcome)  
  
  
