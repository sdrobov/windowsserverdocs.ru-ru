---
title: Управление клиентскими лицензиями
description: Узнайте, как работать с клиентскими лицензиями в службах MultiPoint
ms.prod: windows-server
ms.technology: multipoint-services
ms.topic: article
ms.assetid: 675e089e-d841-401e-bba7-69f3929ef609
author: lizap
manager: dongill
ms.author: elizapo
ms.date: 08/04/2016
ms.openlocfilehash: 2981f22b2b85d90f4102c3a0b67e25901cb12395
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80853547"
---
# <a name="manage-client-access-licenses"></a>Управление клиентскими лицензиями
Каждая станция, которая подключается к системе служб MultiPoint, включая компьютер, на котором выполняются службы MultiPoint, используемые в качестве станции, должна иметь действительную удаленный рабочий стол *клиентской лицензии (CAL)* на уровне "на пользователя".

Если вместо физических станций используются виртуальные рабочие столы станции, необходимо установить клиентскую лицензию для каждого виртуального рабочего стола станции.  
  
1.  Приобретите клиентскую лицензию для каждой станции, подключенной к компьютеру или серверу служб MultiPoint. Дополнительные сведения о приобретении клиентских лицензий см. в документации по удаленный рабочий стол лицензирования. 

2.  На **начальном** экране откройте **диспетчер MultiPoint**.  
  
3.  Перейдите на вкладку **Главная** и нажмите кнопку **добавить клиентские лицензии**.  Откроется средство управления лицензированием CAL.

## <a name="set-the-licensing-mode-manually"></a>Установка режима лицензирования вручную
Если настройка служб MultiPoint не настроена должным образом, будет выдаваться уведомление о том, что срок действия льготного периода истек. Чтобы задать режим лицензирования, выполните следующие действия.

1. Запустите **редактор локальных групповых политик** (gpedit. msc).

2. На левой панели перейдите к **политике локальный компьютер — > Конфигурация компьютера-> Административные шаблоны-> компоненты Windows — > службы удаленных рабочих столов-> Удаленный рабочий стол сеансов — > лицензирования**.

3. В области справа щелкните правой кнопкой мыши **использовать указанные удаленный рабочий стол серверы лицензий** и выберите **изменить**:
   - В диалоговом окне Редактор групповой политики выберите **включено** .
   - Введите имя локального компьютера в поле **серверы лицензирования для использования** .
   - Нажмите кнопку **ОК** .
  
4. На правой панели щелкните правой кнопкой мыши параметр **Удаленный рабочий стол режим лицензирования** и выберите **изменить** .
   - В диалоговом окне Редактор групповой политики выберите **включено** .
   - Установка **режима лицензирования** "на устройство/на пользователя"
   - Нажмите кнопку **ОК** . 

  
## <a name="see-also"></a>См. также  
[Управление системными задачами с помощью диспетчера MultiPoint](Manage-System-Tasks-Using-MultiPoint-Manager.md)
