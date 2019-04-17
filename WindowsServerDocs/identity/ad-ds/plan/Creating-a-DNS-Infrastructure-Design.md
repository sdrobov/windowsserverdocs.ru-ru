---
ms.assetid: cd70b0aa-0a67-4966-a041-4dd3f302c98b
title: "Создание проекта инфраструктуры DNS"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 6e5093b05fd81a693cec87ddb00d39e70483df23
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="creating-a-dns-infrastructure-design"></a>Создание проекта инфраструктуры DNS

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

После создания ваши проекты леса и домена Active Directory, необходимо проектирования инфраструктуры доменных имен (DNS) для поддержки логической структуры Active Directory. DNS-сервера позволяет использовать понятные имена, которые легко запомнить, для подключения к компьютерам и другим ресурсам в IP-сетях. Доменных служб Active Directory (AD DS) в Windows Server 2008 требует DNS.  
  
Процесс проектирования DNS для поддержки Доменных службах Active Directory зависит от ли у организации уже есть существующая служба DNS-сервера или вы развертываете новые службы DNS-сервера:  
  
-   Если у вас уже есть имеющуюся инфраструктуру DNS, необходимо интегрировать имен Active Directory в этой среде. Дополнительные сведения см. в разделе [интеграция Доменных службах Active Directory в имеющуюся инфраструктуру DNS](../../ad-ds/plan/Integrating-AD-DS-into-an-Existing-DNS-Infrastructure.md).  
  
-   Если инфраструктуры DNS нет на месте, необходимо проектировать и развертывание новой инфраструктуры DNS для поддержки Доменных службах Active Directory. Дополнительные сведения см. в разделе Развертывание доменных имен (DNS) ([https://go.microsoft.com/fwlink/?LinkId=93656](https://go.microsoft.com/fwlink/?LinkId=93656)).  
  
Если ваша организация имеет имеющуюся инфраструктуру DNS, необходимо убедиться, что вы понимаете, как инфраструктуры DNS будет взаимодействовать с пространством имен Active Directory. Лист для документирования вашей существующего проекта инфраструктуры DNS можно скачайте Job_Aids_Designing_and_Deploying_Directory_and_Security_Services.zip из задания вспомогательные средства для Windows Server 2003 Deployment Kit ([https://go.microsoft.com/fwlink/?LinkID=102558](https://go.microsoft.com/fwlink/?LinkID=102558)) и откройте «DNS инвентаризацию (DSSLOGI_8.doc).  
  
> [!NOTE]  
> Помимо IP версии 4 (IPv4) адреса, адреса Windows Server 2008 также поддерживает IP версии 6 (IPv6). Лист для описания IPv6-адресов при документальной фиксации метод разрешения имен рекурсивный структуры текущего DNS-сервера, в разделе [приложение а. Инвентаризация DNS](../../ad-ds/plan/Appendix-A--DNS-Inventory.md).  
  
Перед созданием инфраструктуры DNS для поддержки Доменных службах Active Directory, могут быть полезны для чтения о иерархии DNS, процесс разрешения имени DNS-сервера и как DNS поддерживает AD DS. Дополнительные сведения о процессе разрешения иерархии и имя DNS-сервера см. в техническом справочнике по DNS ([https://go.microsoft.com/fwlink/?LinkID=48145](https://go.microsoft.com/fwlink/?LinkID=48145)). Дополнительные сведения о поддержке DNS-сервера AD DS см. поддержка DNS Технический справочник по Active Directory ([https://go.microsoft.com/fwlink/?LinkID=48147](https://go.microsoft.com/fwlink/?LinkID=48147)).  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Общие сведения о понятиях DNS](../../ad-ds/plan/Reviewing-DNS-Concepts.md)  
  
-   [DNS-сервера и Доменных службах Active Directory](../../ad-ds/plan/DNS-and-AD-DS.md)  
  
-   [Назначение DNS для роли владельца доменных служб Active Directory](../../ad-ds/deploy/Assigning-the-DNS-for-AD-DS-Owner-Role.md)  
  
-   [Интеграция Доменных службах Active Directory в имеющуюся инфраструктуру DNS](../../ad-ds/plan/../../ad-ds/plan/Integrating-AD-DS-into-an-Existing-DNS-Infrastructure.md)  
  


