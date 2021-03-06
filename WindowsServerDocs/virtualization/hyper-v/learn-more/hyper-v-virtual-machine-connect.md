---
title: Подключение к виртуальной машине Hyper-V
description: Сведения о подключении к виртуальной машине, которое обеспечивает удаленный доступ к виртуальной машине. Эта статья содержит сведения о выполнении общих задач, таких как отправка (Ctrl+Alt+Delete) на виртуальную машину.
ms.prod: windows-server
manager: dongill
ms.technology: compute-hyper-v
ms.topic: article
ms.assetid: deae35b9-7647-42b8-b6bf-45645a44c9c4
author: kbdazure
ms.author: kathydav
ms.date: 10/04/2016
ms.openlocfilehash: 8de3fe607eb9dc0d140fe9f494991cb917b8994f
ms.sourcegitcommit: 3a3d62f938322849f81ee9ec01186b3e7ab90fe0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2020
ms.locfileid: "80854017"
---
# <a name="hyper-v-virtual-machine-connection"></a>Подключение к виртуальной машине Hyper-V

>Область применения. Windows Server 2016, Windows 10 Windows Server 8.1, Windows Server 2012 R2, Windows Server 2012, Windows 8

Средство подключения к виртуальной машине \(VMConnect\) позволяет подключаться к виртуальной машине для установки операционной системы и взаимодействия с ней. Некоторые задачи, которые можно выполнять при помощи подключения к VMConnect, перечислены ниже:  
  
-   Запуск и завершение работы виртуальной машины.  
  
-   Подключение к \(ISO-файлу\) DVD-образа или USB-устройству флэш-памяти.  
  
-   Создание контрольной точки  
  
-   Изменение параметров виртуальной машины  
    
## <a name="tips-for-using-vmconnect"></a>Советы по использованию средства VMConnect  
Ознакомьтесь с указанными ниже сведениями об использовании VMConnect:  
  
|Для этого…|Сделайте это…|  
|---------------|------------|  
|Отправка щелчков мыши или клавиатурного ввода на виртуальную машину|Щелкните в любом месте окна виртуальной машины. При подключении к работающей виртуальной машине указатель мыши может отображаться в виде маленькой точки.|  
|Возврат щелчков мыши или клавиатурного ввода на физический компьютер|Нажмите клавиши CTRL\+ALT\+СТРЕЛКА ВЛЕВО, а затем переместите указатель мыши за пределы окна виртуальной машины. Это сочетание клавиш для отпускания кнопки мыши можно изменить в параметрах Hyper\-V в диспетчере Hyper\-V.|  
|Отправка сочетания клавиш CTRL\+ALT\+DELETE на виртуальную машину|Выберите **Действие** > **Ctrl\+Alt\+Delete** или воспользуйтесь сочетанием клавиш CTRL\+ALT\+END.|  
|Переключение из режима окна в полноэкранный режим|Выберите **Представление** > **Полноэкранный режим**. Чтобы перейти обратно в режим окна, нажмите клавиши CTRL\+ALT\+BREAK.|  
|Создание контрольной точки для получения сведений о текущем состоянии компьютера, чтобы устранить неполадки|Выберите **Действие** > **Контрольная точка** или используйте сочетание клавиш CTRL\+N.|  
|Изменение параметров виртуальной машины|Выберите **Файл** > **Параметры**.|  
|Подключение к \(ISO-файлу\) DVD-образа или к \(VFD-файлу виртуального гибкого диска\)|Выберите **Медиа**.<p>Виртуальные гибкие диски не поддерживаются для виртуальных машин 2-го поколения. Дополнительные сведения см.в статье [Should I create a generation 1 or 2 virtual machine in Hyper-V?](../plan/Should-I-create-a-generation-1-or-2-virtual-machine-in-Hyper-V.md) (Следует ли создавать виртуальные машины 1-го и 2-го поколения в Hyper-V?).|  
|Использование локальных ресурсов узла на виртуальной машине Hyper\-V, например, USB-устройства флэш-памяти|На узле Hyper-V включите режим расширенного сеанса, с помощью VMConnect подключитесь к виртуальной машине и перед подключением выберите нужный локальный ресурс. Описание конкретных шагов см. в статье [Use local resources on Hyper\-V virtual machine with VMConnect](Use-local-resources-on-Hyper-V-virtual-machine-with-VMConnect.md) (Использование локальных ресурсов на виртуальной машине Hyper-V с VMConnect).|  
|Изменение сохраненных параметров VMConnect для виртуальной машины|Выполните следующую команду в Windows PowerShell или в командной строке:<p>`VMConnect.exe <ServerName> <VMName> /edit`|  
|Запрещение пользователю VMConnect получать доступ к сеансу VMConnect другого пользователя|[Включение режима расширенного сеанса на узле Hyper-V](Use-local-resources-on-Hyper-V-virtual-machine-with-VMConnect.md#turn-on-enhanced-session-mode-on-a-hyper-v-host).<p>Отсутствие включенного режима расширенного сеанса может привести к угрозе безопасности и конфиденциальности. Если пользователь подключился и вошел на виртуальную машину через VMConnect, а другой авторизированный пользователь подключается к той же виртуальной машине, то сеанс перехватывается вторым пользователем и будет прерван у первого. Второй пользователь сможет просматривать рабочий стол, документы и приложения первого пользователя.|
|Управление службами интеграции или компонентами, которые позволяют виртуальной машине обмениваться данными с узлом Hyper-V| На узлах Hyper-V под управлением Windows 10 или Windows Server 2016 нельзя управлять службами интеграции с помощью VMConnect. Дополнительную информацию об этом см. в следующих разделах: <br />- [Turn an integration service on or off using Hyper-V Manager](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/managing_ics) (Включение или отключение службы интеграции в диспетчере Hyper-V); <br />- [Start and stop an integration service from a Windows Guest](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/managing_ics#manage-integration-services-from-guest-os-windows) (Запуск и остановка службы интеграции в гостевой учетной записи Windows);<br />- [Start and stop an integration service from a Linux guest](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/managing_ics#manage-integration-services-from-guest-os-linux) (Запуск и остановка службы интеграции в гостевой учетной записи Linux); <br />- [Keep integration services up to date](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/managing_ics#integration-service-maintenance) (Своевременное обновление служб интеграции).  <br />Сведения об узлах под управлением Windows Server 2012 или Windows Server 2012 R2 см. в статье [Службы интеграции](https://technet.microsoft.com/library/dn798297(v=ws.11).aspx).|
|Изменение размера окна VMConnect|Вы можете изменить размер окна VMConnect для виртуальных машин 2-го поколения, работающих под управлением операционной системы Windows. Для этого может потребоваться включить режим расширенного сеанса на узле Hyper-V. Дополнительные сведения см. в разделе [Включение режима расширенного сеанса на узле Hyper-V](Use-local-resources-on-Hyper-V-virtual-machine-with-VMConnect.md#turn-on-enhanced-session-mode-on-a-hyper-v-host). Сведения о виртуальных машинах под управлением Ubuntu см. в статье [Changing Ubuntu Screen Resolution in a Hyper-V VM](https://blogs.msdn.microsoft.com/virtual_pc_guy/2014/09/19/changing-ubuntu-screen-resolution-in-a-hyper-v-vm/) (Изменение разрешения экрана Ubuntu на виртуальной машине Hyper-V).|


## <a name="keyboard-shortcuts"></a>Сочетания клавиш  
По умолчанию ввод с клавиатуры и щелчки мыши отправляются на виртуальную машину. Поэтому может потребоваться нажать клавиши CTRL + ALT + СТРЕЛКА ВЛЕВО, прежде чем использовать следующие сочетания клавиш. 

|Сочетание клавиш|Описание|  
|-------------------|---------------|  
|CTRL\+ALT\+LEFT стрелка влево|Отпускание кнопки мыши|  
|CTRL\+ALT\+END|Эквивалентно сочетанию клавиш CTRL\+ALT\+DELETE на виртуальной машине|  
|CTRL\+ALT\+BREAK|Переключиться с полноэкранного режима обратно на оконный режим|  
|CTRL\+O|Открытие параметров для виртуальной машины|  
|CTRL\+S|Запуск виртуальной машины|  
|CTRL\+N|Создание контрольной точки|  
|CTRL\+E|Возврат к контрольной точке|  
|CTRL\+C|Сделайте снимок экрана|  

## <a name="see-also"></a>См. также  
-   [Use local resources on Hyper-V virtual machine with VMConnect](Use-local-resources-on-Hyper-V-virtual-machine-with-VMConnect.md) (Использование локальных ресурсов на виртуальной машине с VMConnect)  
-   [Hyper-V в Windows Server 2016](../Hyper-V-on-Windows-Server.md)  
-   [Hyper-V в Windows 10](https://msdn.microsoft.com/virtualization/hyperv_on_windows/windows_welcome)  
  
  
