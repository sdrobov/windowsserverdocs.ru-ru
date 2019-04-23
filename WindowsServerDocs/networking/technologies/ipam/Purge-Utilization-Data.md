---
title: Очистка данных об использовании
description: Этот раздел является частью в руководстве по управления IP Address Management (IPAM) в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology:
- networking-ipam
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 45cada9e-69b9-43df-b6f5-6d3942435809
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 7b471417d4c44c22f115443f1f2dcca6f351e6f4
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59827945"
---
# <a name="purge-utilization-data"></a>Очистка данных об использовании

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

В этом разделе можно использовать, чтобы узнать, как удалить данные об использовании из базы данных IPAM.  

Необходимо быть членом **Администраторы IPAM**, локальный компьютер **Администраторы** или аналогичной группе, для выполнения этой процедуры.

## <a name="to-purge-the-ipam-database"></a>Очистка базы данных IPAM  
1. Откройте диспетчер серверов и перейдите к интерфейсу клиента IPAM.
2. Перейдите к одной из следующих папок. **Блоки IP-адресов**, **перечень IP-адресов**, или **группы диапазонов адресов IP-адрес**.  
3. Нажмите кнопку **ЗАДАЧИ**, а затем нажмите кнопку **очистить данные об использовании**. **Очистить данные об использовании** откроется диалоговое окно.
4. В **очистить все об использовании данных или совпадает с ними**, нажмите кнопку **выберите дату**.
5. Выберите дату, для которого вы хотите удалить все записи базы данных на и до этой даты.
6. Нажмите кнопку **ОК**. IPAM удаляет все записи, которые вы указали.
