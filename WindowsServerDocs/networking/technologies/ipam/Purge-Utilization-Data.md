---
title: Очистка данных об использовании
description: Этот раздел является частью руководства по управлению IP-адресами (IPAM) в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-ipam
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 45cada9e-69b9-43df-b6f5-6d3942435809
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 9e1db31e4d2d714c358f2a67c2165aef91b314ba
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71405602"
---
# <a name="purge-utilization-data"></a>Очистка данных об использовании

>Относится к: Windows Server (Semi-Annual Channel), Windows Server 2016

С помощью этого раздела можно узнать, как удалить данные об использовании из базы данных IPAM.  

Для выполнения этой процедуры необходимо быть членом группы "Администраторы **IPAM**", " **Администраторы** локального компьютера" или эквивалентными.

## <a name="to-purge-the-ipam-database"></a>Очистка базы данных IPAM  
1. Откройте диспетчер сервера, а затем перейдите к интерфейсу клиента IPAM.
2. Перейдите к одной из следующих папок. Группы **IP-адресов**, **Инвентаризация IP-адресов**или **групп диапазонов IP-адресов**.  
3. Щелкните **задачи**, а затем — **Очистить данные об использовании**. Откроется диалоговое окно « **Очистка данных об использовании** ».
4. В окне **Очистить все данные об использовании на или ранее**нажмите кнопку **выбрать дату**.
5. Выберите дату, для которой необходимо удалить все записи базы данных как в, так и до этой даты.
6. Нажмите кнопку **ОК**. IPAM удаляет все указанные записи.
