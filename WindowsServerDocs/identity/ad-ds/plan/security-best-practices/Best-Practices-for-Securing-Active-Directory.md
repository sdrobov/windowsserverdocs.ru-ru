---
ms.assetid: e2651dc8-4b31-4cd8-a400-3b8123890210
title: Рекомендации по защите Active Directory
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 972def668634e794908a3ff2933d038ae38be5d6
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59817085"
---
# <a name="best-practices-for-securing-active-directory"></a>Рекомендации по защите Active Directory

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

В этом документе наблюдающиеся специалист-практик и содержит набор помогут ИТ-руководители защиты корпоративной среде Active Directory. Active Directory играет важную роль в ИТ-инфраструктуре и позволяет обеспечить согласованную и безопасную работу с сетевыми ресурсами в глобализированной и взаимосвязанной среде. Рассматриваемые методы основываются главным образом на возможности организации информационной безопасности корпорации Microsoft и управления рисками (ISRM), которая предназначена для защиты активов ИТ Microsoft и других бизнес-подразделения корпорации Майкрософт, а также о том, выбранное число клиентов Microsoft Global 500.  
  
-   [Краткий обзор](../../../ad-ds/manage/component-updates/Executive-Summary.md)  
  
-   [Введение](../../../ad-ds/manage/component-updates/Introduction.md)  
  
-   [Способы решения проблем](../../../ad-ds/plan/security-best-practices/Avenues-to-Compromise.md)  
  
-   [Учетные записи, подверженные риску кражи учетных данных](../../../ad-ds/plan/security-best-practices/Attractive-Accounts-for-Credential-Theft.md)  
  
-   [Снизить риск атак Active Directory](../../../ad-ds/plan/security-best-practices/Reducing-the-Active-Directory-Attack-Surface.md)  
  
-   [Реализация административных моделей минимальных привилегий](../../../ad-ds/plan/security-best-practices/Implementing-Least-Privilege-Administrative-Models.md)  
  
-   [Реализация безопасного администрирования узлов](../../../ad-ds/plan/security-best-practices/Implementing-Secure-Administrative-Hosts.md)  
  
-   [Защита контроллеров домена от атак](../../../ad-ds/plan/security-best-practices/Securing-Domain-Controllers-Against-Attack.md)  
  
-   [Мониторинг Active Directory для обнаружения признаков компрометации](../../../ad-ds/plan/security-best-practices/Monitoring-Active-Directory-for-Signs-of-Compromise.md)  
  
-   [Рекомендации по политике аудита](../../../ad-ds/plan/security-best-practices/Audit-Policy-Recommendations.md)  
  
-   [Планирование при компрометации](../../../ad-ds/plan/security-best-practices/Planning-for-Compromise.md)  
  
-   [Поддержка более безопасной среды](../../../ad-ds/plan/security-best-practices/Maintaining-a-More-Secure-Environment.md)  
  
-   [Приложения](../../../ad-ds/plan/security-best-practices/Appendices.md)  
   
-   [Приложение б. Привилегированные учетные записи и группы в Active Directory](../../../ad-ds/plan/security-best-practices/Appendix-B--Privileged-Accounts-and-Groups-in-Active-Directory.md)  
  
-   [Приложение c. Защищенные учетные записи и группы в Active Directory](../../../ad-ds/plan/security-best-practices/Appendix-C--Protected-Accounts-and-Groups-in-Active-Directory.md)  
  
-   [Приложение г. Обеспечение безопасности встроенной учетной записи администратора учетных записей в Active Directory](../../../ad-ds/plan/security-best-practices/Appendix-D--Securing-Built-In-Administrator-Accounts-in-Active-Directory.md)  
  
-   [Приложение д. Защита групп корпоративных администраторов в Active Directory](../../../ad-ds/plan/security-best-practices/Appendix-E--Securing-Enterprise-Admins-Groups-in-Active-Directory.md)  
  
-   [Приложение е. Защита групп администраторов домена в Active Directory](../../../ad-ds/plan/security-best-practices/Appendix-F--Securing-Domain-Admins-Groups-in-Active-Directory.md)  
  
-   [Приложение ж Защита групп администраторов в Active Directory](../../../ad-ds/plan/security-best-practices/Appendix-G--Securing-Administrators-Groups-in-Active-Directory.md)  
  
-   [Приложение h. Обеспечение безопасности в учетные записи локального администратора и группы](../../../ad-ds/plan/security-best-practices/Appendix-H--Securing-Local-Administrator-Accounts-and-Groups.md)  
  
-   [Приложение и: Создание управления учетных записей для защищенных учетных записей и групп в Active Directory](../../../ad-ds/manage/component-updates/Appendix-I--Creating-Management-Accounts-for-Protected-Accounts-and-Groups-in-Active-Directory.md)   
  
-   [Приложение м: События для мониторинга](../../../ad-ds/plan/Appendix-L--Events-to-Monitor.md)  
  
-   [Приложение н: Ссылки на документы и Рекомендуемая литература](../../../ad-ds/manage/Appendix-M--Document-Links-and-Recommended-Reading.md)  
  


