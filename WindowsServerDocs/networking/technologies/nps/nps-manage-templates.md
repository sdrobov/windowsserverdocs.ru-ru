---
title: Управление шаблонами сервера политики сети
description: Этот раздел содержит инструкции о том, как создавать, применять, экспортировать и импортировать шаблонами сервера политики сети для сервера политики сети в Windows Server 2016.
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: 989b00c5-4767-4081-ace5-6321f8b2c55e
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 0a7f4c50d87c155c1adcd445eae8df23aab7730b
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="manage-nps-templates"></a>Управление шаблонами сервера политики сети

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

Шаблоны \(NPS\) сервера политики сети можно использовать для создания элементов конфигурации, такие как клиенты \(RADIUS\) удаленной службы проверки подлинности удаленного пользователя или общие секретные данные, которые вы можете повторно использовать на локальный сервер политики сети и экспорта для использования на других серверах политики сети. 

Управление шаблонами предоставляет узел в консоли сервера политики сети, где вы можно создавать, изменять, удалить, дублировать и просматривать использование шаблонами сервера политики сети. Шаблоны NPS предназначены для сокращения времени и затрат, необходимое для настройки сервера политики сети на один или несколько серверов.

Для конфигурации в Управление шаблонами доступны следующие типы шаблонов сервера политики сети.

- **Общие секреты**. Этот тип шаблона позволяет указать общий секрет, который вы можете повторно использовать (путем выбора шаблона в соответствующее место в консоли сервера политики сети) при настройке клиенты и серверы RADIUS. 

- **RADIUS-клиенты**. Этот тип шаблона позволяет настроить параметры RADIUS-клиента, которые вы можете повторно использовать, выбрав шаблон в соответствующее место в консоли сервера политики сети.

- **Удаленных RADIUS-серверов**. Этот шаблон позволяет настроить параметры сервера удаленного RADIUS, вы можете повторно использовать, выбрав шаблон в соответствующее место в консоли сервера политики сети. 

- **IP-фильтры**. Этот шаблон позволяет создавать протокола IP версии 4 (IPv4) и протокола IP версии 6 \(IPv6\) фильтры, которые вы можете повторно использовать \ (путем выбора шаблона в соответствующее место в основанное NPS) при настройке политики сети.

## <a name="create-an-nps-template"></a>Создание шаблона политики сети

Настройка шаблона отличается от непосредственно Настройка сервера политики сети. Создание шаблона не влияет на функциональные возможности сервера политики сети. Это только когда выберите шаблон в соответствующее место в консоли сервера политики сети и применение шаблона, что шаблон влияет на функциональные возможности сервера политики сети. 

Например, если настроить RADIUS-клиента в консоли сервера политики сети в разделе **клиенты и серверы RADIUS**, изменить конфигурацию сервера политики сети и принимать первым шагом в настройке сервера политики сети для обмена данными с одним из серверы доступа к сети. \ (Следующий шаг — Настройка сервера доступа к сети \(NAS\) для связи с сервером политики сети. \) 

Тем не менее при настройке нового **RADIUS-клиенты** шаблона в консоли сервера политики сети в разделе **Управление шаблонами** вместо создания нового RADIUS-клиента в разделе **клиенты и серверы RADIUS**, созданный шаблон, но не будут изменены функциональные возможности сервера политики сети еще. Для изменения функциональности сервера политики сети, необходимо применить шаблон в соответствующем расположении в консоли сервера политики сети.

Следующая процедура содержит инструкции о том, как создать новый шаблон.

Членство в группе **Администраторы**, или в эквивалентной минимальным требованием для выполнения этой процедуры.

### <a name="to-create-an-nps-template"></a>Создание шаблона политики сети


1. На сервере политики сети, в диспетчере серверов щелкните **средства**, а затем нажмите кнопку **сервера политики сети**. Откроется консоль NPS. 

2. В консоли сервера политики сети разверните **Управление шаблонами**, например, щелкните правой кнопкой мыши тип шаблона, **RADIUS-клиенты**и нажмите кнопку **New**.

3. Новый шаблон свойства откроется диалоговое окно, можно использовать для настройки шаблона.

## <a name="apply-an-nps-template"></a>Применение шаблона NPS

Можно использовать шаблон, который вы создали в **Управление шаблонами**, перейдите в расположение в консоли сервера политики сети, где можно применить шаблон. Например если вы хотите применить шаблон общие секреты к конфигурации RADIUS-клиента, можно использовать следующую процедуру.

Членство в группе **Администраторы**, или в эквивалентной минимальным требованием для выполнения этой процедуры.

### <a name="to-apply-an-nps-template"></a>Применение шаблона NPS

1. На сервере политики сети, в диспетчере серверов щелкните **средства**, а затем нажмите кнопку **сервера политики сети**. Откроется консоль NPS.

2. В консоли сервера политики сети разверните **клиенты и серверы RADIUS**, а затем разверните **RADIUS-клиенты**.

3. в **RADIUS-клиенты**, в области сведений щелкните правой кнопкой мыши клиент RADIUS, к которому вы хотите применить шаблон политики сети и нажмите кнопку **свойства**.

4. В диалоговом окне Свойства поле для клиента RADIUS в **выбрать существующий шаблон общие секреты**, выберите шаблон, который вы хотите применить в списке шаблонов.

## <a name="export-or-import-nps-templates"></a>Экспорт и импорт шаблонов сервера политики сети

Вы можете экспортировать шаблоны для использования на других серверах политики сети также можно импортировать шаблоны в **Управление шаблонами** для использования на локальном компьютере. 

Членство в группе **Администраторы**, или в эквивалентной минимальным требованием для выполнения этой процедуры.

### <a name="to-export-or-import-nps-templates"></a>Для экспорта или импорта шаблоны NPS

1. Для экспорта шаблонами сервера политики сети, в консоли сервера политики сети, щелкните правой кнопкой мыши **Управление шаблонами**, а затем нажмите кнопку **Экспорт шаблонов в файл**.

2. Для импорта шаблонов сервера политики сети, в консоли сервера политики сети, щелкните правой кнопкой мыши **Управление шаблонами**, а затем нажмите кнопку **импортировать шаблоны с компьютера** или **импортировать шаблоны из файла**.

