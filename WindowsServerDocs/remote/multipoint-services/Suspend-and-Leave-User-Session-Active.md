---
title: Приостановка и восстановление сеанса пользователя
description: Узнайте, как приостановить пользователя из сеанса MultiPoint, не отключая его
ms.custom: na
ms.prod: windows-server-threshold
ms.technology: multipoint-services
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5263bce3-fe92-4398-8393-2e3a4e05d530
author: lizap
manager: dongill
ms.author: elizapo
ms.date: 08/04/2016
ms.openlocfilehash: a7c94b9d1edd36efc8651e35dfabbc95239335cb
ms.sourcegitcommit: f6490192d686f0a1e0c2ebe471f98e30105c0844
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70871529"
---
# <a name="suspend-and-leave-user-session-active"></a>Приостановка и восстановление сеанса пользователя
Вы можете отключить или приостановить пользователей в системе служб MultiPoint, если не хотите завершать сеансы пользователей. Пользователь также может отключить сеанс самостоятельно. Пока сеанс пользователя приостановлен, сеанс остается активным в системной памяти компьютера служб MultiPoint, пока компьютер не будет выключен или перезагружен. В этот момент все приостановленные сеансы завершаются, а все несохраненные данные теряются.  
  
1.  Откройте диспетчер MultiPoint в режиме станции и перейдите на вкладку **станции** .  
  
2.  В столбце **Компьютер** выберите имя компьютера, сеансы которого требуется приостановить.  
  
3.  В разделе **Задачи станции** щелкните **Приостановить все станции**.  
  
После приостановки сеанса пользователь может войти на ту же или другую станцию и продолжить работу с исходным сеансом.  
  
## <a name="see-also"></a>См. также  
[Управление рабочими столами пользователей](manage-user-desktops-using-multipoint-dashboard.md)  
[Выход из сеанса пользователя или его отключение](Log-off-or-Disconnect-User-Sessions.md)