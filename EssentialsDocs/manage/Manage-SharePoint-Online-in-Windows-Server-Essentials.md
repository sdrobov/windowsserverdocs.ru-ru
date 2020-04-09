---
title: Управление SharePoint Online в Windows Server Essentials
description: Описание использования Windows Server Essentials
ms.date: 10/03/2016
ms.prod: windows-server
ms.topic: article
ms.assetid: 282f3634-6de6-4691-803c-df6c3c16660d
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: f6f0a29759fa8bdb098576cdb32a71d8568fb465
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80852727"
---
# <a name="manage-sharepoint-online-in-windows-server-essentials"></a>Управление SharePoint Online в Windows Server Essentials

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Вы можете управлять библиотеками и сайтами групп SharePoint Online с панели мониторинга без входа в Office 365, если вы интегрируете Office 365 с сервером Windows Server Essentials. Вы получаете библиотеки SharePoint Online и сайты рабочих групп с любым бизнес-планом Office 365. [Сведения об интеграции Office 365 с сервером](Manage-Office-365-in-Windows-Server-Essentials.md)  
  
 В качестве премии пользователи смогут использовать приложение "мой сервер 2012 R2" для доступа к файлам в библиотеках SharePoint Online из любого места с помощью мобильного устройства или Windows Phone. [Где найти приложение "Мой сервер"?](../use/Use-the-My-Server-App-to-Connect-to-Windows-Server-Essentials.md)  
  
 Еще не пробовали SharePoint? [Что теперь можно сделать](https://office.microsoft.com/office365-sharepoint-online-enterprise-help/get-started-with-sharepoint-2013-HA102772778.aspx)  
  
## <a name="where-on-the-dashboard-will-i-manage-my-libraries-and-team-sites"></a>Где на панели мониторинга находится управление библиотеками и сайтами групп?  
 Вы будете использовать новую вкладку **SharePoint Online** , которая добавляется в область **хранения** панели мониторинга при интеграции Office 365 с сервером, для управления ресурсами SharePoint Online.  

  
## <a name="what-can-i-manage-from-the-dashboard"></a>Чем можно управлять с помощью панели мониторинга?  
  
### <a name="manage-your-online-libraries"></a>Управление интерактивными библиотеками  
   
|-|-|  
| Добавить библиотеку | На вкладке **библиотеки SharePoint** используйте команду **Добавить библиотеку**. Вы сможете настроить следующие стандартные параметры:<br /><br /> — Выберите сайт рабочей группы и тип библиотеки.<br />— Решите, следует ли использовать систему управления версиями.<br />— Назначение разрешений на доступ.<br /><br /> **Совет.** Чтобы узнать, какие разрешения сайта группы будут наследоваться библиотекой, если вы не назначите разрешения, используйте **Просмотр разрешений для сайта**. |  
| Открытие библиотеки | Для работы с содержимым библиотеки необходимо открыть ее в Office 365. Выберите библиотеку и нажмите **Открыть библиотеку**. То, что можно сделать с помощью содержимого, зависит от учетных данных, используемых для входа в SharePoint Online. |  
| Изменение элементов управления версиями или разрешений на доступ | С помощью окна **Просмотр свойств библиотеки** можно просмотреть или изменить элементы управления версиями или разрешения на доступ к библиотеке. |  
| Удаление библиотеки | **Предупреждение:** Перед удалением библиотеки SharePoint Online не забудьте сохранить все файлы, которые необходимо сохранить в другом расположении. При удалении библиотеки из SharePoint все удаляются без возможности восстановления. Восстановление невозможно.<br /><br /> Убедившись, что библиотека не сохраняет ничего, что потребуется позже, выберите библиотеку и щелкните **Удалить библиотеку**. |  
  
### <a name="manage-your-team-sites"></a>Управление сайтами группы  
 
|-|-|  
| Управление сайтами группы SharePoint | Действие **Manage Team Sites (Управление сайтами группы** ) позволяет входить в Office 365 и управлять сайтами групп SharePoint Online. Возможности Office 365 определяются учетной записью, с помощью которой вы выполняете вход.<br /><br /> Когда вы закроете Office 365 и вернетесь на панель мониторинга, нажмите кнопку **Обновить** , чтобы отобразить изменения. | Просмотр или изменение разрешений для сайта группы | Поскольку библиотека наследует разрешения от своего сайта группы по умолчанию, полезно иметь простой доступ к сайту группы. Чтобы просмотреть или изменить разрешения для сайта группы, выберите сайт группы или любую из его библиотек и щелкните **просмотреть разрешения сайта**.<br /><br /> **Совет.** Нужна помощь с тонкими точками разрешений для сайта группы SharePoint? Воспользуйтесь полезной ссылкой [Подробнее](https://office.microsoft.com/office365-sharepoint-online-enterprise-help/introduction-control-user-access-with-permissions-HA102771919.aspx?CTT=5&origin=HA102771924) на странице разрешений сайта группы.  
  
## <a name="tips"></a>Советы  
  
-   **Нажмите кнопку обновить, чтобы отобразить последние изменения, внесенные на портале Office 365.** После открытия Office 365 для управления SharePoint Online необходимо обновить экран. Если панель мониторинга длительные периоды времени остается открытой, нажимайте **Обновить** для отображения последних изменений.  
  
-   **Возможности SharePoint Online зависят от того, работаете ли вы с панелью мониторинга или в Office 365.** На панели мониторинга изменения SharePoint Online выполняются с использованием учетной записи администратора для интеграции Office 365. Но при входе в Office 365 с панели мониторинга разрешения на доступ к учетной записи в сети, которую вы используете, определяют, что вы можете делать.  
  
     Чтобы узнать учетную запись администратора для интеграции Office 365, откройте вкладку **office 365** на панели мониторинга.  
  
## <a name="other-things-you-might-want-to-do"></a>Дополнительные сведения  
  
-   [Использование моего серверного приложения для работы с библиотеками SharePoint Online из любого места](../use/Use-the-My-Server-App-to-Connect-to-Windows-Server-Essentials.md)  
  
-   [Дополнительные сведения о назначении разрешений для сайтов групп SharePoint](https://office.microsoft.com/office365-sharepoint-online-enterprise-help/introduction-control-user-access-with-permissions-HA102771919.aspx?CTT=5&origin=HA102771924)  
  
-   [Узнайте, что можно сделать с помощью функций SharePoint](https://office.microsoft.com/office365-sharepoint-online-enterprise-help/get-started-with-sharepoint-2013-HA102772778.aspx)  
  
-   [Ознакомьтесь с доступными корпоративными планами Office 365](https://office.microsoft.com/business/compare-office-365-for-business-plans-FX102918419.aspx?CR_CC=200061904&WT.srch=1&WT.mc_ID=PS_bing_O365Comm_what-is-office-365-for_Text)  
  
-   [Интеграция Office 365 с сервером](Manage-Office-365-in-Windows-Server-Essentials.md)  
  
-   [Управление другими веб-службы Майкрософт с панели мониторинга](Manage-Microsoft-Online-Services-in-Windows-Server-Essentials.md)
