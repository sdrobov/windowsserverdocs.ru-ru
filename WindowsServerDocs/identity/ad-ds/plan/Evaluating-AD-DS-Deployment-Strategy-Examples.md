---
ms.assetid: 4f835b82-67b9-428c-b634-ce133cca5113
title: "Оценка примеров стратегии развертывания AD DS"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 4cac1e344cfed078927f2945048807d686deebd1
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="evaluating-ad-ds-deployment-strategy-examples"></a>Оценка примеров стратегии развертывания AD DS

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Рассмотрим следующий пример вымышленная компания Contoso Pharmaceuticals, который развертывает доменных служб Active Directory (AD DS) в своей среде. Contoso среда состоит из четырех доменов. Режим работы леса соответствует Windows Server 2003. Текущая структура домена для организации Contoso на следующем рисунке.  
  
![Стратегии развертывания AD DS](media/Evaluating-AD-DS-Deployment-Strategy-Examples/3dd79e00-48f8-4927-989c-c55a79caf1be.gif)  
  
После просмотра — в существующей среде и определения задач развертывания, Contoso установлен следующие стратегии развертывания AD DS:  
  
-   Обновление доменов Windows Server 2003, к доменам Windows Server 2008.  
  
-   Включите расширенные функции AD DS, создавая режимы работы домена и леса до Windows Server 2008.  
  
-   Реструктуризация доменов africa.concorp.contoso.com в пределах леса, чтобы консолидировать этого домена в домене emea.concorp.contoso.con.  
  
Повышение режима работы леса до Windows Server 2008 включает Contoso, чтобы воспользоваться всеми преимуществами новых функций AD DS. Реструктуризация доменов в пределах леса, как показано на следующем рисунке позволяет снизить объем администрирования, необходимые для управления доменами.  
  
![Стратегии развертывания AD DS](media/Evaluating-AD-DS-Deployment-Strategy-Examples/1c061755-413d-452d-b121-6910f8555327.gif)  
  


