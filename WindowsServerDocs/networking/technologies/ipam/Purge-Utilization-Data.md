---
title: Очистка данных об использовании
description: Этот раздел является частью в руководстве по управления IP Address Management (IPAM) в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: networking-ipam
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 45cada9e-69b9-43df-b6f5-6d3942435809
ms.author: pashort
author: shortpatti
ms.openlocfilehash: ab2bd3ad1ef8965400e09fa74c6eb89ffc5ebcef
ms.sourcegitcommit: afb0602767de64a76aaf9ce6a60d2f0e78efb78b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/20/2019
ms.locfileid: "67283846"
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
