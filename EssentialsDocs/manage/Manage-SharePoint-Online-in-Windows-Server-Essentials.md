---
title: Управление SharePoint Online в Windows Server Essentials
description: Описывает способ использования Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 282f3634-6de6-4691-803c-df6c3c16660d
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: b9b12c138e6166684b4b9e87b794444febd3c247
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59830385"
---
# <a name="manage-sharepoint-online-in-windows-server-essentials"></a>Управление SharePoint Online в Windows Server Essentials

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Вы можете управлять библиотек SharePoint Online и сайты групп с помощью панели мониторинга, не подключаясь к Office 365, при интеграции Office 365 с сервера Windows Server Essentials. Вы получаете библиотеки SharePoint Online и сайты групп с любой бизнес-план Office 365. [Сведения об интеграции Office 365 с сервером](Manage-Office-365-in-Windows-Server-Essentials.md)  
  
 Кроме того ваши пользователи смогут использовать приложение My Server 2012 R2 для доступа к файлам из ваших библиотек SharePoint Online из любого места с мобильного устройства или Windows phone. [Где найти приложение "Мой сервер"?](../use/Use-the-My-Server-App-to-Connect-to-Windows-Server-Essentials.md)  
  
 Еще не пробовали SharePoint? [Что можно сделать сейчас](https://office.microsoft.com/office365-sharepoint-online-enterprise-help/get-started-with-sharepoint-2013-HA102772778.aspx)  
  
## <a name="where-on-the-dashboard-will-i-manage-my-libraries-and-team-sites"></a>Где на панели мониторинга находится управление библиотеками и сайтами групп?  
 Вы используете новую **SharePoint Online** вкладки, которая добавляется к **хранения** область на панели мониторинга при интеграции Office 365 с сервером, для управления ресурсами SharePoint Online.  

  
## <a name="what-can-i-manage-from-the-dashboard"></a>Чем можно управлять с помощью панели мониторинга?  
  
### <a name="manage-your-online-libraries"></a>Управление интерактивными библиотеками  
   
|-|-|  
| Добавление библиотеки | На **библиотеки SharePoint** вкладке **добавить библиотеку**. Вы сможете настроить следующие стандартные параметры:<br /><br /> -Выберите сайт группы и типа библиотеки.<br />— Решить, следует ли использовать систему управления версиями.<br />-Прав доступа.<br /><br /> **Совет.** Чтобы узнать, какие разрешения сайта группы библиотека унаследует в том случае, если не назначить разрешения, используйте **просмотреть разрешения сайта**. |  
| Откройте библиотеку | Для работы с содержимым библиотеки, необходимо открыть его в Office 365. Выберите библиотеку и нажмите **Открыть библиотеку**. Что делать с содержимым будет зависеть от учетные данные, используемые для входа в SharePoint Online. |  
| Изменение параметров версии и права доступа | Можно использовать **параметры библиотеки** можно просматривать и редактировать параметры версии и права доступа к библиотеке. |  
| Удаление библиотеки | **Предупреждение:** Перед удалением библиотеки SharePoint Online убедитесь, что вы сохранили все необходимые файлы. При удалении библиотеки из SharePoint, все данные удаляются без возможности восстановления. Восстановление невозможно.<br /><br /> После того вы вы убедитесь, что сохранили все необходимые более поздней версии, выберите библиотеку и нажмите кнопку **удалить библиотеку**. |  
  
### <a name="manage-your-team-sites"></a>Управление сайтами группы  
 
|-|-|  
| Управление сайтами группы SharePoint | **Управлять сайтами группы** действие позволяет войти в Office 365 и управление сайтами группы SharePoint Online. Что делать в Office 365 будет определяться online учетной записи, которой вы вошли в систему.<br /><br /> Если вы закроете Office 365 и вернитесь к панели мониторинга, щелкните **обновить** чтобы изменения отобразились. | Просмотр или изменение разрешений сайта группы | Так как библиотека наследует разрешения от сайта группы по умолчанию, полезно иметь быстрый доступ к сайту. Чтобы просмотреть или изменить разрешения для сайта группы, выберите сайт группы или любую из его библиотек и нажмите кнопку **просмотреть разрешения сайта**.<br /><br /> **Совет.** Хотите узнать подробнее о тонкостях использования разрешений сайта группы SharePoint? Воспользуйтесь полезной ссылкой [Подробнее](https://office.microsoft.com/office365-sharepoint-online-enterprise-help/introduction-control-user-access-with-permissions-HA102771919.aspx?CTT=5&origin=HA102771924) на странице разрешений сайта группы.  
  
## <a name="tips"></a>Советы  
  
-   **Щелкните "Обновить", чтобы показать последние изменения, внесенные на портале Office 365.** Необходимо обновить экран, открыв Office 365 для управления SharePoint Online. Если панель мониторинга длительные периоды времени остается открытой, нажимайте **Обновить** для отображения последних изменений.  
  
-   **Что делать в SharePoint Online зависит от того, работаете ли вы на панели мониторинга или в Office 365.** На панели мониторинга SharePoint Online изменении с помощью учетной записи администратора для интеграции Office 365. Но при входе Office 365 из панели мониторинга, разрешения на доступ online учетной записью, которую вы используете определяют, что можно делать.  
  
     Для получения учетной записи администратора для интеграции Office 365, откройте **Office 365** вкладку на панели мониторинга.  
  
## <a name="other-things-you-might-want-to-do"></a>Дополнительные сведения  
  
-   [Использование приложения My Server для работы с библиотеками SharePoint Online из любого места](../use/Use-the-My-Server-App-to-Connect-to-Windows-Server-Essentials.md)  
  
-   [Дополнительные сведения о назначении разрешений для сайтов групп SharePoint](https://office.microsoft.com/office365-sharepoint-online-enterprise-help/introduction-control-user-access-with-permissions-HA102771919.aspx?CTT=5&origin=HA102771924)  
  
-   [Узнайте, что можно сделать с помощью функций SharePoint](https://office.microsoft.com/office365-sharepoint-online-enterprise-help/get-started-with-sharepoint-2013-HA102772778.aspx)  
  
-   [Взгляните на бизнес-планов Office 365, которые доступны](https://office.microsoft.com/business/compare-office-365-for-business-plans-FX102918419.aspx?CR_CC=200061904&WT.srch=1&WT.mc_ID=PS_bing_O365Comm_what-is-office-365-for_Text)  
  
-   [Интеграции Office 365 с сервером](Manage-Office-365-in-Windows-Server-Essentials.md)  
  
-   [Управлять остальным сетевым службам Майкрософт из панели мониторинга](Manage-Microsoft-Online-Services-in-Windows-Server-Essentials.md)
