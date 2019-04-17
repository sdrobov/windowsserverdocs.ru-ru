---
ms.assetid: e2651dc8-4b31-4cd8-a400-3b8123890210
title: "Рекомендации по обеспечению безопасности Active Directory"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: ecef0c173677d379524189b1769d4721ab0774a8
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="best-practices-for-securing-active-directory"></a>Рекомендации по обеспечению безопасности Active Directory

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Это документе представлена точка зрения практикующего и даются практические указания, которые помогут директорам по ИТ защитить корпоративную среду Active Directory. Active Directory играет важную роль в ИТ-инфраструктуре и позволяет обеспечить согласованную и безопасности различных сетевых ресурсов в глобальной взаимосвязанной среде и. Рассматриваемые методы основываются главным образом на организации корпорация Майкрософт сведения о безопасности и управления рисками (ISRM), которая предназначена для защиты активов ИТ Майкрософт и других бизнес-подразделения Майкрософт, помимо оказания консультативной помощи выбранного количества клиентов Майкрософт из списка Global 500.  
  
-   [Foreword](https://technet.microsoft.com/library/dn487451.aspx)  
  
-   [Подтверждения](https://technet.microsoft.com/library/dn487445.aspx)  
  
-   [Краткий обзор](../../../ad-ds/manage/component-updates/Executive-Summary.md)  
  
-   [Введение](../../../ad-ds/manage/component-updates/Introduction.md)  
  
-   [Способы решения](../../../ad-ds/plan/security-best-practices/Avenues-to-Compromise.md)  
  
-   [Хороший учетные записи для кражи учетных данных](../../../ad-ds/plan/security-best-practices/Attractive-Accounts-for-Credential-Theft.md)  
  
-   [Снижение уязвимостей Active Directory](../../../ad-ds/plan/security-best-practices/Reducing-the-Active-Directory-Attack-Surface.md)  
  
-   [Реализация административных моделей с наименьшим количеством прав](../../../ad-ds/plan/security-best-practices/Implementing-Least-Privilege-Administrative-Models.md)  
  
-   [Реализация безопасного администрирования узлов](../../../ad-ds/plan/security-best-practices/Implementing-Secure-Administrative-Hosts.md)  
  
-   [Защита контроллеров домена от атак](../../../ad-ds/plan/security-best-practices/Securing-Domain-Controllers-Against-Attack.md)  
  
-   [Мониторинг Active Directory для обнаружения признаков компрометации](../../../ad-ds/plan/security-best-practices/Monitoring-Active-Directory-for-Signs-of-Compromise.md)  
  
-   [Рекомендации по политике аудита](../../../ad-ds/plan/security-best-practices/Audit-Policy-Recommendations.md)  
  
-   [Планирование при компрометации](../../../ad-ds/plan/security-best-practices/Planning-for-Compromise.md)  
  
-   [Поддержка более безопасной среды](../../../ad-ds/plan/security-best-practices/Maintaining-a-More-Secure-Environment.md)  
  
-   [Приложения](../../../ad-ds/plan/security-best-practices/Appendices.md)  
   
-   [Приложение б. привилегированные учетные записи и группы в Active Directory](../../../ad-ds/plan/security-best-practices/Appendix-B--Privileged-Accounts-and-Groups-in-Active-Directory.md)  
  
-   [Приложение в. защищенные учетные записи и группы в Active Directory](../../../ad-ds/plan/security-best-practices/Appendix-C--Protected-Accounts-and-Groups-in-Active-Directory.md)  
  
-   [Приложение г. Защита встроенных учетных записей администраторов в Active Directory](../../../ad-ds/plan/security-best-practices/Appendix-D--Securing-Built-In-Administrator-Accounts-in-Active-Directory.md)  
  
-   [Приложение д. Защита групп корпоративных администраторов в Active Directory](../../../ad-ds/plan/security-best-practices/Appendix-E--Securing-Enterprise-Admins-Groups-in-Active-Directory.md)  
  
-   [Приложение е. Защита групп администраторов домена в Active Directory](../../../ad-ds/plan/security-best-practices/Appendix-F--Securing-Domain-Admins-Groups-in-Active-Directory.md)  
  
-   [Приложение ж. Защита групп администраторов в Active Directory](../../../ad-ds/plan/security-best-practices/Appendix-G--Securing-Administrators-Groups-in-Active-Directory.md)  
  
-   [Приложение з. Защита учетных записей локального администратора и групп](../../../ad-ds/plan/security-best-practices/Appendix-H--Securing-Local-Administrator-Accounts-and-Groups.md)  
  
-   [Приложение и создание учетных записей управления для защищенных учетных записей и групп в Active Directory](../../../ad-ds/manage/component-updates/Appendix-I--Creating-Management-Accounts-for-Protected-Accounts-and-Groups-in-Active-Directory.md)   
  
-   [Приложение м. события для мониторинга](../../../ad-ds/plan/Appendix-L--Events-to-Monitor.md)  
  
-   [Приложение н. ссылки на документы и Рекомендуемая литература](../../../ad-ds/manage/Appendix-M--Document-Links-and-Recommended-Reading.md)  
  


