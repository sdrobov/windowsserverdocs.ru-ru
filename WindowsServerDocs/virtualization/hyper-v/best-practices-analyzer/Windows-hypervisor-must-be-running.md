---
title: Низкоуровневая оболочка Windows должна быть запущена
description: Инструкции для устранения проблемы, о которых сообщает это правило анализатора соответствия рекомендациям.
ms.prod: windows-server-threshold
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: 501a9beb-c464-46c0-88c5-e3e7e3e70101
author: KBDAzure
ms.date: 10/03/2016
ms.openlocfilehash: f34e10918c60fb602c3a88ef3434cda619b11d8d
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59884145"
---
# <a name="windows-hypervisor-must-be-running"></a>Низкоуровневая оболочка Windows должна быть запущена

>Область применения. Windows Server 2016
  
|Свойство|Подробности|  
|-|-|  
|**Операционная система**|Windows Server 2016|  
|**Продукта или компонента**|Hyper-V|  
|**Уровень серьезности**|Предупреждение|  
|**Категория**|предварительные требования|  
  
В следующих разделах курсив указывает текст пользовательского Интерфейса, который отображается в анализатор соответствия рекомендациям для этой проблемы.  
  
## <a name="issue"></a>Проблемы  
  
*Низкоуровневая оболочка Windows не запущена.*  
  
## <a name="impact"></a>Влияние  
  
*Виртуальные машины будет невозможно запустить до запуска низкоуровневой оболочки Windows.*  
  
## <a name="resolution"></a>Разрешение  
  
*Проверьте в каталоге Windows Server, чтобы увидеть, если этот сервер определен для запуска Hyper-V. Затем убедитесь, что BIOS включена аппаратная поддержка виртуализации и предотвращением выполнения данных, реализуемая оборудованием. Затем проверьте журнал событий Hyper-V-Hypervisor.*  
  
Проверьте каталог, см. в разделе [каталог Windows Server](https://go.microsoft.com/fwlink/?LinkId=111228) (https://go.microsoft.com/fwlink/?LinkId=111228).  
  
> [!CAUTION]  
> Изменение параметров, определенных в BIOS компьютера может вызвать остановить загрузку операционной системы данного компьютера или устройств, таких как жесткие диски, можно сделать недоступным. Всегда в руководстве пользователя для компьютера, чтобы определить правильный способ настроить BIOS системы. Кроме того настоятельно рекомендуется хранить список параметров, которые можно изменить и исходные значения, чтобы можно было восстановить позже при необходимости. Если возникли проблемы после изменения параметров в BIOS, попытаться загрузить параметры по умолчанию (параметр обычно доступны в настройках BIOS), или обратитесь к производителю компьютера за помощью.  
  
#### <a name="to-verify-virtualization-support-in-the-bios-or-uefi"></a>Чтобы проверить поддержку виртуализации в BIOS или UEFI  
  
1.  Перезагрузите компьютер и доступа к BIOS или UEFI через средство настройки. Доступа к этому средству обычно доступен при выходе в процессе загрузки. Сразу после включения на большинстве компьютеров, на несколько секунд, содержащий список клавиша или сочетание клавиши, чтобы открыть средство настройки появится сообщение.  
  
2.  Найдите параметры для виртуализации и предотвращение выполнения с аппаратная данных (DEP) и убедитесь, что они находятся на. Ниже приведены стандартные меню расположения для этих параметров в средстве настройки и как они могут быть назван примеры:  
  
    -   Поддержка виртуализации:  
  
        -   Как правило, доступны в разделе параметров для основного или производительности. Иногда это параметры безопасности.  
  
        -   Найдите имена параметров, которые содержат «виртуализация» или «технологии виртуализации».  
  
    -   Аппаратного Предотвращения:  
  
        -   Как правило, доступны в разделе Параметры безопасности или памяти.  
  
        -   Найдите имена параметров, которые включают «выполнение», «выполнить» или «предотвращение».  
  
3.  При необходимости включите нужные параметры, следуя инструкциям в средстве настройки. Сохранить изменения и выйти.  
  
4.  Если вы внесли изменения, отключайте питание и обратно на Готово.  
  
    > [!IMPORTANT]  
    > Рекомендуется отключить питание и затем обратно на (иногда называется питания), так как изменения не применяются на некоторых компьютерах, пока это происходит.  
  
Затем проверьте журнал событий Hyper-V-Hypervisor. При возникновении проблем, предстоит также проверить журнал системы.  
  
#### <a name="to-check-the-event-logs"></a>Чтобы проверить журналы событий  
  
1.  Откройте окно просмотра событий. Нажмите кнопку **запустить**, нажмите кнопку **Администрирование**, а затем нажмите кнопку **средство просмотра событий**.  
  
2.  Откройте журнал событий Hyper-V-Hypervisor. В области навигации разверните **журналы приложений и служб** >> **Microsoft** >> **Windows**  >>   **Hyper-V-Hypervisor**, а затем нажмите кнопку **Operational**.  
  
3.  Если выполняется низкоуровневой оболочки Windows, никаких дополнительных действий не требуется. Если низкоуровневая оболочка Windows не запущен, это сделать:  
  
4.  Откройте системный журнал. (В области навигации разверните **журналы Windows** , а затем выберите **системы**.)  
  
5.  Используйте фильтр для поиска событий Hyper-V-Hypervisor:   
    1. В **действия** панели щелкните **фильтровать текущий журнал**. Для **источники событий**, укажите «Hyper-V-Hypervisor».   
    2. Найдите события, сообщения о проблемах. Например событие с кодом 41 указывает на проблему с конфигурацией BIOS: «Не удалось запустить Hyper-V; Либо VMX отсутствует или не включена в BIOS.»  
  
### <a name="see-also"></a>См. также  
Дополнительные сведения об использовании Hyper-V в Windows 10, включая как проверить, что компьютер может работать Hyper-V, см. в разделе [требования к системе Windows 10 Hyper-V](https://msdn.microsoft.com/virtualization/hyperv_on_windows/quick_start/walkthrough_compatibility). 

