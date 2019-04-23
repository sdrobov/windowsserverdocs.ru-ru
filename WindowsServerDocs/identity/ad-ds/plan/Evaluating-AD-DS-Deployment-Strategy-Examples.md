---
ms.assetid: 4f835b82-67b9-428c-b634-ce133cca5113
title: Оценка примеров стратегии развертывания доменных служб Active Directory
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 169d0a55f9fb167390c13ac1c89f8d68427f318d
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59842115"
---
# <a name="evaluating-ad-ds-deployment-strategy-examples"></a>Оценка примеров стратегии развертывания доменных служб Active Directory

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Рассмотрим следующий пример вымышленной компании Contoso Pharmaceuticals, который развертывается в среде доменных служб Active Directory (AD DS). The Contoso environment consists of four domains. Режим работы леса — Windows Server 2003. Ниже показана структура текущего домена для организации Contoso.  
  
![Стратегии развертывания AD DS](media/Evaluating-AD-DS-Deployment-Strategy-Examples/3dd79e00-48f8-4927-989c-c55a79caf1be.gif)  
  
После рассмотрения его существующей среды и определения задач развертывания, Contoso установить следующие стратегии развертывания AD DS:  
  
-   Домены обновления Windows Server 2003 к доменам Windows Server 2008.  
  
-   Включите дополнительные возможности AD DS, вызывая режимы работы домена и леса до Windows Server 2008.  
  
-   Измените домен africa.concorp.contoso.com в пределах леса для объединения этого домена с доменом emea.concorp.contoso.con.  
  
Повышение режима работы леса до Windows Server 2008 позволит Contoso, чтобы воспользоваться всеми преимуществами новых функций AD DS. Реструктуризация доменов в пределах леса, в том случае, как показано на следующем рисунке, сократит администрирования, необходимые для управления доменами.  
  
![Стратегии развертывания AD DS](media/Evaluating-AD-DS-Deployment-Strategy-Examples/1c061755-413d-452d-b121-6910f8555327.gif)  
  


