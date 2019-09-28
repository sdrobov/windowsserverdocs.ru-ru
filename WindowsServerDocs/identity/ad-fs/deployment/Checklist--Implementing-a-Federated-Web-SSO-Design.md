---
ms.assetid: 6b49cde3-d2cb-4ece-b9b7-dc600e037495
title: Контрольный список — реализация федеративного единого входа в Интернете
description: ''
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: 165471fd06031a68343a54d019357afee782d082
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71359947"
---
# <a name="checklist-implementing-a-federated-web-sso-design"></a>Контрольный список: реализация федерированного механизма единого входа в Интернете [ADFS2]

Этот родительский контрольный список содержит ссылки Cross no__t-0reference на важные понятия о федеративной веб-технологии Single @ no__t-1Sign @ no__t-2On \(SSO @ no__t-4 для службы федерации Active Directory (AD FS) \(AD FS @ no__t-6. Кроме того, в списке присутствуют ссылки на вложенные контрольные списки, которые помогут выполнить действия, необходимые для внедрения разработки.  
  
> [!NOTE]  
> Выполните по порядку задачи в контрольном списке. В случае перехода по ссылке в раздел общих понятий или вложенный контрольный список вернитесь после просмотра раздела общих понятий или выполнения действий из вложенного контрольного списка, чтобы можно было перейти к остальным задачам этого контрольного списка.  
  
@no__t 0federated Web SSO @ no__t-1Checklist: Реализация федеративного механизма единого входа через Интернет [ADFS2]**  
  
||Задача|Ссылка|  
|-|--------|-------------|  
|![Федеративная веб-служба SSO](media/icon_checkboxo.gif)|Ознакомьтесь с важными понятиями о проекте федеративного единого входа в Интернете и определите, какие AD FS цели развертывания можно использовать для настройки этого проекта в соответствии с потребностями Организации.|веб-](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Разработка федеративного единого входа веб-сайта](https://technet.microsoft.com/library/dd807050.aspx) @no__t 0federated<br /><br />@no__t 0federated Web SSO,](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[определяющий цели развертывания AD FS](https://technet.microsoft.com/library/dd807053.aspx)<br /><br />![federated Web SSO](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Планирование развертывания](https://technet.microsoft.com/library/dd807083.aspx)|  
|![Федеративная веб-служба SSO](media/icon_checkboxo.gif)|Ознакомьтесь с оборудованием, программным обеспечением, сертификатом, системой доменных имен \(DNS @ no__t-1, хранилищем атрибутов и требованиями клиента для развертывания AD FS в вашей организации.|@no__t 0federated Web SSO @ no__t-1Appendix A: Обзор требований AD FS](https://technet.microsoft.com/library/ff678034.aspx)|  
|![Федеративная веб-служба SSO](media/icon_checkboxo.gif)|Прежде чем развертывать AD FS в обеих партнерских организациях, ознакомьтесь с важными понятиями о заявках, правилах утверждений, хранилищах атрибутов и базе данных конфигурации AD FS.|@no__t 0federated Web SSO](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Общие сведения о ключевых AD FS основных понятиях](../../ad-fs/technical-reference/Understanding-Key-AD-FS-Concepts.md)|  
|![Федеративная веб-служба SSO](media/icon_checkboxo.gif)|В соответствии с планом проектирования установите один или несколько серверов федерации в каждой партнерской организации. **Примечание.** Для проектирования федеративного единого входа в Интернете требуется по крайней мере один сервер федерации в организации партнера по учетным записям и хотя бы один сервер федерации в организации партнера по ресурсам.|@no__t 0federated Web SSO @ no__t-1Checklist: Настройка сервера федерации](Checklist--Setting-Up-a-Federation-Server.md)|  
|![Федеративная веб-служба SSO](media/icon_checkboxo.gif)|\(Optional @ no__t-1 определяет, требуется ли вашей организации прокси-сервер федерации. Если ваш план разработки вызывает прокси, можно установить один или несколько прокси-серверов федерации в каждой партнерской организации.|@no__t 0federated Web SSO @ no__t-1Checklist: Настройка прокси-сервера федерации](Checklist--Setting-Up-a-Federation-Server-Proxy.md)|  
|![Федеративная веб-служба SSO](media/icon_checkboxo.gif)|Осуществите обмен сертификатами, настройте клиенты и отношения доверия в обеих партнерских организациях согласно плану разработки, чтобы организации могли обмениваться данными через доверие федерации.|@no__t 0federated Web SSO @ no__t-1Checklist: Настройка организации партнера по учетным записям @ no__t-0<br /><br />@no__t 0federated Web SSO @ no__t-1Checklist: Настройка организации партнера по ресурсам @ no__t-0|  
|![Федеративная веб-служба SSO](media/icon_checkboxo.gif)|Если вы являетесь администратором в организации партнера по ресурсам, заявка @ no__t-0enable приложение веб-браузера, приложение веб-службы или Microsoft® Office SharePoint® Server с помощью WIF и пакета SDK для WIF.|@no__t 0federated Web SSO](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Windows Identity Foundation](https://go.microsoft.com/fwlink/?LinkId=122266)<br /><br />](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[пакет SDK для Windows Identity Foundation](https://go.microsoft.com/fwlink/?LinkId=122266) для @no__t 0federated Web SSO|  
