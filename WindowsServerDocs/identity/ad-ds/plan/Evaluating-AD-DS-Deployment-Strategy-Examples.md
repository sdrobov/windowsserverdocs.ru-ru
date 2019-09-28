---
ms.assetid: 4f835b82-67b9-428c-b634-ce133cca5113
title: Оценка примеров стратегии развертывания доменных служб Active Directory
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: 3d04530c53150a3222b609a80938d7fdfcdfeff7
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71402589"
---
# <a name="evaluating-ad-ds-deployment-strategy-examples"></a>Оценка примеров стратегии развертывания доменных служб Active Directory

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Рассмотрим следующий пример вымышленной компании Contoso Pharmaceuticals, которая развертывает службы домен Active Directory Services (AD DS) в своей среде. Среда Contoso состоит из четырех доменов. Функциональный уровень леса — Windows Server 2003. На следующем рисунке показана текущая структура домена для компании Contoso.  
  
![Стратегия развертывания AD DS](media/Evaluating-AD-DS-Deployment-Strategy-Examples/3dd79e00-48f8-4927-989c-c55a79caf1be.gif)  
  
После проверки существующей среды и определения целей развертывания компания Contoso установила следующую стратегию развертывания AD DS:  
  
-   Обновите домены Windows Server 2003 до доменов Windows Server 2008.  
  
-   Включение расширенных функций AD DS путем повышения функциональных уровней домена и леса до Windows Server 2008.  
  
-   Измените структуру домена africa.concorp.contoso.com в лесу, чтобы консолидировать этот домен с доменом EMEA. Corp. contoso. Con.  
  
Повышение функционального уровня леса до Windows Server 2008 позволит компании Contoso воспользоваться всеми преимуществами новых функций AD DS. При реструктуризации доменов в пределах леса, как показано на следующем рисунке, уменьшается объем администрирования, необходимый для управления доменами.  
  
![Стратегия развертывания AD DS](media/Evaluating-AD-DS-Deployment-Strategy-Examples/1c061755-413d-452d-b121-6910f8555327.gif)  
  


