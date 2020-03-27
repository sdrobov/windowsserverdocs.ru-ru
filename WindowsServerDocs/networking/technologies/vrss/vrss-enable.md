---
title: Включение vRSS на виртуальном сетевом адаптере
description: В этом разделе описано, как включить vRSS в Windows Server с помощью Device Manager или Windows PowerShell.
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: cb48315c-0204-4927-aa24-64f6789c2e20
manager: dougkim
ms.localizationpriority: medium
ms.date: 09/05/2018
ms.author: lizross
author: eross-msft
ms.openlocfilehash: e4be9060da4a738e3ad8e4976d037f3a05467da3
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "80315375"
---
# <a name="enable-vrss-on-a-virtual-network-adapter"></a>Включение vRSS на виртуальном сетевом адаптере

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

Для виртуальных RSS-\(\) vRSS требуется очередь виртуальной машины \(поддержка VMQ\) от физического адаптера. Если функция VMQ отключена или не поддерживается, виртуальное масштабирование на стороне приема отключено. 

Дополнительные сведения см. [в разделе Планирование использования vRSS](vrss-plan.md).

## <a name="enable-vrss-on-a-vm"></a>Включение vRSS на виртуальной машине
 
Используйте следующие процедуры для включения vRSS с помощью Windows PowerShell или Device Manager.

-   Диспетчер устройств
-   Windows PowerShell
  
### <a name="device-manager"></a>Диспетчер устройств

Эту процедуру можно использовать для включения vRSS с помощью Device Manager.

>[!NOTE]
>Первый шаг в этой процедуре относится к виртуальным машинам под Windows 10 или Windows Server 2016. Если виртуальная машина работает под управлением другой операционной системы, можно открыть Device Manager, сначала откройте панель управления, а затем найдите и откройте Device Manager.
  
1.  На панели задач виртуальной машины в поле **введите текст для поиска**введите **устройство**. 

2.  В результатах поиска щелкните **Device Manager**.

3.  В Device Manager щелкните, чтобы развернуть **Сетевые адаптеры**. 

4.  Щелкните правой кнопкой мыши сетевой адаптер, который нужно настроить, и выберите пункт **Свойства**.<p>Откроется диалоговое окно **Свойства** сетевого адаптера.

5.  В окне **Свойства**сетевого адаптера перейдите на вкладку **Дополнительно** . 

6.  В **свойстве**прокрутите вниз до и щелкните **масштабирование на стороне приема**. 

7.  Убедитесь, что выбран параметр в поле **значение** **включено**. 

8.  Нажмите кнопку **ОК**.
  
> [!NOTE]
> На вкладке **Дополнительно** некоторые сетевые адаптеры также отображают число очередей RSS, которые поддерживаются адаптером.

---

### <a name="windows-powershell"></a>Windows PowerShell

Используйте следующую процедуру, чтобы включить vRSS с помощью Windows PowerShell.

1. На виртуальной машине откройте **Windows PowerShell**.

2. Введите следующую команду, убедившись, что значение *адаптернаме* для параметра **-Name** заменяется именем сетевого адаптера, который требуется настроить, и нажмите клавишу ВВОД. 
  
   ```PowerShell
   Enable-NetAdapterRSS -Name "AdapterName"
   ```

   >[!TIP]
   >Кроме того, для включения vRSS можно использовать следующую команду.
   >```PowerShell
   >Set-NetAdapterRSS -Name "AdapterName" -Enabled $True  
   >```

Дополнительные сведения см. в разделе [команды Windows PowerShell для RSS и vRSS](vrss-wps.md).

---