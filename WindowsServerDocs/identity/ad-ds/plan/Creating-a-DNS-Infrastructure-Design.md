---
ms.assetid: cd70b0aa-0a67-4966-a041-4dd3f302c98b
title: Создание проекта инфраструктуры DNS
description: ''
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 08/08/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 080c36f8410be4d6b1933c74730e2b55ce8d0a0b
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59856135"
---
# <a name="creating-a-dns-infrastructure-design"></a>Создание проекта инфраструктуры DNS

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

После создания проектов леса и домена Active Directory, необходимо разработать инфраструктуру доменных имен (DNS) для поддержки логической структуры Active Directory. DNS позволяет использовать понятные имена, которые легко запомнить, для подключения к компьютерам и другим ресурсам в IP-сетях. Используют DNS для доменных служб Active Directory (AD DS) в Windows Server 2008.  
  
Процесс разработки DNS, чтобы обеспечить поддержку AD DS зависит от того, имеет ли ваша организация уже существующей службы DNS-сервер, или вы развертываете новую службу DNS-сервер:  
  
- При наличии уже существующей инфраструктурой DNS, необходимо интегрировать имен Active Directory в этом окружении. Дополнительные сведения см. в разделе [интеграция AD DS в существующую инфраструктуру DNS](../../ad-ds/plan/Integrating-AD-DS-into-an-Existing-DNS-Infrastructure.md).  
- Если у вас нет инфраструктуры DNS на месте, необходимо разработать и развернуть новую инфраструктуру DNS, чтобы обеспечить поддержку AD DS. Дополнительные сведения см. в разделе [развертывание доменных имен (DNS)](https://go.microsoft.com/fwlink/?LinkId=93656).  
  
Если ваша организация имеет существующую инфраструктуру DNS, необходимо убедиться в том, что вы понимаете, как инфраструктура DNS будут взаимодействовать с пространством имен Active Directory. Лист, чтобы помочь в документировании вашей существующей инфраструктуры DNS, загрузите Job_Aids_Designing_and_Deploying_Directory_and_Security_Services.zip из [задания вспомогательные средства для Windows Server 2003 Deployment Kit](https://go.microsoft.com/fwlink/?LinkID=102558) и Откройте «Инвентаризация DNS» (DSSLOGI_8.doc).  
  
> [!NOTE]  
> В дополнение к IP версии 4 (IPv4) адреса, адреса серверов Windows также поддерживает IP версии 6 (IPv6). Лист для помощи в листинге IPv6-адресов при документировании метода разрешения имен рекурсивного структуры вашего текущего DNS, см. в разделе [приложении a. Инвентаризация DNS](../../ad-ds/plan/Appendix-A--DNS-Inventory.md).
  
До начала разработки инфраструктуры DNS, чтобы обеспечить поддержку AD DS, может быть полезно прочитать о иерархии DNS, процесс разрешения имен DNS и как DNS поддерживает AD DS. Дополнительные сведения о процессе DNS иерархии и имя разрешения, см. в разделе Технический справочник по DNS ([https://go.microsoft.com/fwlink/?LinkID=48145](https://go.microsoft.com/fwlink/?LinkID=48145)). Дополнительные сведения о том, как DNS поддерживает AD DS, см. в разделе поддержки DNS для Технический справочник по Active Directory ([https://go.microsoft.com/fwlink/?LinkID=48147](https://go.microsoft.com/fwlink/?LinkID=48147)).  
  
## <a name="in-this-section"></a>В этом разделе  

- [Изучите основные понятия DNS](../../ad-ds/plan/Reviewing-DNS-Concepts.md)  
- [DNS и AD DS](../../ad-ds/plan/DNS-and-AD-DS.md)  
- [Назначение DNS для AD DS владельца роли](../../ad-ds/deploy/Assigning-the-DNS-for-AD-DS-Owner-Role.md)  
- [Интеграция AD DS в существующую инфраструктуру DNS](../../ad-ds/plan/../../ad-ds/plan/Integrating-AD-DS-into-an-Existing-DNS-Infrastructure.md)  
