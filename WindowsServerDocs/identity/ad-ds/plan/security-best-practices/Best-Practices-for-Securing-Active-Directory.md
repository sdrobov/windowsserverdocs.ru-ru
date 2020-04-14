---
ms.assetid: e2651dc8-4b31-4cd8-a400-3b8123890210
title: Рекомендации по защите Active Directory
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: 8935a08b9ab8f99b5f221a14b93974872f11a091
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80821297"
---
# <a name="best-practices-for-securing-active-directory"></a>Рекомендации по защите Active Directory

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Этот документ содержит ряд практических методик, помогающих ИТ-специалистам защитить корпоративную Active Directoryную среду. Active Directory играет важную роль в ИТ-инфраструктуре и позволяет обеспечить согласованную и безопасную работу с сетевыми ресурсами в глобализированной и взаимосвязанной среде. Обсуждаемые методы основаны на опыте организации Microsoft Information Security and риски (ИСРМ), которая может быть обеспечена для защиты активов ИТ-отделов корпорации Майкрософт и других подразделений корпорации Майкрософт, а также для выбора нескольких клиентов Microsoft Global 500.  
  
-   [Краткий обзор](../../../ad-ds/manage/component-updates/Executive-Summary.md)  
  
-   [Введение](../../../ad-ds/manage/component-updates/Introduction.md)  
  
-   [Способы решения проблем](../../../ad-ds/plan/security-best-practices/Avenues-to-Compromise.md)  
  
-   [Учетные записи, подверженные риску кражи учетных данных](../../../ad-ds/plan/security-best-practices/Attractive-Accounts-for-Credential-Theft.md)  
  
-   [Сокращение Active Directory уязвимой зоны](../../../ad-ds/plan/security-best-practices/Reducing-the-Active-Directory-Attack-Surface.md)  
  
-   [Реализация административных моделей с минимальными правами доступа](../../../ad-ds/plan/security-best-practices/Implementing-Least-Privilege-Administrative-Models.md)  
  
-   [Внедрение узлов безопасного администрирования узлов](../../../ad-ds/plan/security-best-practices/Implementing-Secure-Administrative-Hosts.md)  
  
-   [Защита контроллеров домена от атак](../../../ad-ds/plan/security-best-practices/Securing-Domain-Controllers-Against-Attack.md)  
  
-   [Мониторинг Active Directory для подписывания компромисса](../../../ad-ds/plan/security-best-practices/Monitoring-Active-Directory-for-Signs-of-Compromise.md)  
  
-   [Рекомендации по политике аудита](../../../ad-ds/plan/security-best-practices/Audit-Policy-Recommendations.md)  
  
-   [Планирование компрометации](../../../ad-ds/plan/security-best-practices/Planning-for-Compromise.md)  
  
-   [Поддержка более безопасной среды](../../../ad-ds/plan/security-best-practices/Maintaining-a-More-Secure-Environment.md)  
  
-   [Приложения](../../../ad-ds/plan/security-best-practices/Appendices.md)  
   
-   [Приложение б. привилегированные учетные записи и группы в Active Directory](../../../ad-ds/plan/security-best-practices/Appendix-B--Privileged-Accounts-and-Groups-in-Active-Directory.md)  
  
-   [Приложение C. защищенные учетные записи и группы в Active Directory](../../../ad-ds/plan/security-best-practices/Appendix-C--Protected-Accounts-and-Groups-in-Active-Directory.md)  
  
-   [Приложение г. Защита встроенных учетных записей администраторов в Active Directory](../../../ad-ds/plan/security-best-practices/Appendix-D--Securing-Built-In-Administrator-Accounts-in-Active-Directory.md)  
  
-   [Приложение E. Защита групп администраторов предприятия в Active Directory](../../../ad-ds/plan/security-best-practices/Appendix-E--Securing-Enterprise-Admins-Groups-in-Active-Directory.md)  
  
-   [Приложение е. Защита групп администраторов домена в Active Directory](../../../ad-ds/plan/security-best-practices/Appendix-F--Securing-Domain-Admins-Groups-in-Active-Directory.md)  
  
-   [Приложение ж. Защита групп администраторов в Active Directory](../../../ad-ds/plan/security-best-practices/Appendix-G--Securing-Administrators-Groups-in-Active-Directory.md)  
  
-   [Приложение H. Защита учетных записей и групп локального администратора](../../../ad-ds/plan/security-best-practices/Appendix-H--Securing-Local-Administrator-Accounts-and-Groups.md)  
  
-   [Приложение I. Создание учетных записей управления для защищенных учетных записей и групп в Active Directory](../../../ad-ds/manage/component-updates/Appendix-I--Creating-Management-Accounts-for-Protected-Accounts-and-Groups-in-Active-Directory.md)   
  
-   [Приложение L. события для отслеживания](../../../ad-ds/plan/Appendix-L--Events-to-Monitor.md)  
  
-   [Приложение M. ссылки на документы и Рекомендуемые материалы для чтения](../../../ad-ds/manage/Appendix-M--Document-Links-and-Recommended-Reading.md)  
  


