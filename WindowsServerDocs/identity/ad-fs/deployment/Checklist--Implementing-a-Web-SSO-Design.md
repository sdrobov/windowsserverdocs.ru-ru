---
ms.assetid: 30657638-5709-48c5-87aa-98f688e07b4c
title: "Контрольный список - Implementing a Web SSO Design"
description: 
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: 265daf3acb9632aa92f85962abc44a6a9ea8dfed
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="checklist-implementing-a-web-sso-design"></a>Контрольный список: Реализация Web SSO Design

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Этот родительский контрольный список содержит cross\ ссылки на важные понятия о веб-разработки одиночных входа на \(SSO\) для \(AD FS\) служб федерации Active Directory. Он также содержит ссылки на вложенные контрольные списки, которые помогут вам выполнить задачи, необходимые для внедрения разработки.  
  
> [!NOTE]  
> Задачи в контрольном списке в порядке. Ссылка раздел общих понятий или вложенный контрольный список, вернитесь к данном разделу, после просмотрите раздел общих понятий или выполнения действий из вложенного контрольного списка, чтобы продолжить выполнение оставшихся задач контрольного списка.  
  
![веб-служба sso](media/2b05dce3-938f-4168-9b8f-1f4398cbdb9b.gif)**Checklist: Implementing a Web SSO Design**  
  
||Задача|Справочник по|  
|-|--------|-------------|  
|![веб-служба sso](media/icon_checkboxo.gif)|Изучите важные понятия о Единого входа и определите цели развертывания Служб федерации Active Directory, можно использовать для настройки этот проект в соответствии с потребностями вашей организации. **Примечание.**|![веб-служба sso](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Web SSO Design](https://technet.microsoft.com/library/dd807033.aspx)<br /><br />![веб-служба sso](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[определение целей развертывания AD FS](https://technet.microsoft.com/library/dd807053.aspx)|  
|![веб-служба sso](media/icon_checkboxo.gif)|Просмотрите оборудования, программного обеспечения, сертификат, \(DNS\) доменных имен, хранилищу атрибутов и клиентские требования для развертывания Служб федерации Active Directory в вашей организации.|![веб-служба sso](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[требования приложение а. Общие сведения об AD FS](https://technet.microsoft.com/library/ff678034.aspx)|  
|![веб-служба sso](media/icon_checkboxo.gif)|Согласно плану разработки установите один или несколько серверов федерации в корпоративной сети или в сети периметра. **Примечание:** Единого входа требуется только один сервер федерации успешно работать. Одного сервера федерации выступает в роли поставщика утверждений и в роли проверяющей стороны.|![веб-служба sso](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[Checklist: Setting Up a Federation Server](Checklist--Setting-Up-a-Federation-Server.md)|  
|![веб-служба sso](media/icon_checkboxo.gif)|\(Optional\) определите, требуется ли вашей организации требуется прокси-сервера федерации в сети периметра.|![веб-служба sso](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[Checklist: Setting Up a Proxy сервера федерации](Checklist--Setting-Up-a-Federation-Server-Proxy.md)|  
|![веб-служба sso](media/icon_checkboxo.gif)|В зависимости от вашего плана по развертыванию веб-служба SSO и как планируется его использовать добавьте соответствующее хранилище атрибутов, отношения доверия проверяющей стороны, утверждения и правила утверждений в службу федерации.|![веб-служба sso](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[контрольный список: Настройка партнерской организации по учетной записи](Checklist--Configuring-the-Account-Partner-Organization.md)|  
|![веб-служба sso](media/icon_checkboxo.gif)|Если вы являетесь администратором в организации партнера по ресурсам, включите claims\ вашего приложения веб-браузера, приложения веб-службы или приложения Microsoft® Office SharePoint® Server, с помощью WIF и WIF SDK. **Примечание.**|![веб-служба sso](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Windows Identity Foundation](https://go.microsoft.com/fwlink/?LinkId=122266)<br /><br />![веб-служба sso](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Windows Identity Foundation SDK](https://go.microsoft.com/fwlink/?LinkId=122266)| 
