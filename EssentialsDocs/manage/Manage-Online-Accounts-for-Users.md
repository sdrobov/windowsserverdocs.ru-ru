---
title: "Управление записями интернет-служб для пользователей Windows Server Essentials"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c09f4cf6-4d12-49fe-9ae4-e6cb14027b9d
8author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 95f401bbec9bb503d19e2d9918a05851c04f7ef4
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="manage-online-accounts-for-windows-server-essentials-users"></a>Управление записями интернет-служб для пользователей Windows Server Essentials

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

При интеграции сервера Windows Server Essentials с Microsoft Office 365, можно управлять ваших сетевых учетных записей и учетными записями пользователей с помощью панели мониторинга. В этом разделе вы получите Узнайте, можно получить с помощью управления пользователей учетных записей Microsoft Online Services с помощью панели мониторинга, как создавать и управлять сетевыми учетными записями с помощью панели мониторинга и как управлять адресами электронной почты и группами рассылок Exchange Online с помощью панели мониторинга.  

  
> [!NOTE]
>  Для управления учетными записями Microsoft Online Services в Windows Server Essentials, необходимо интегрировать сервер с Office 365. Инструкции см. в разделе [управление Office 365](Manage-Office-365-in-Windows-Server-Essentials.md).  
  
> [!IMPORTANT]
>  Если вы Управление записями интернет-служб в Windows Server Essentials, вы привыкли учетных записей Microsoft Online Services, называется *учетных записей Office 365*. На панели мониторинга в Windows Server Essentials название было изменено на *учетные записи Microsoft Online Services*, или *учетных записей Майкрософт в Интернете* для краткости. Учетные записи и процедуры одинаковы; только для метки могут быть изменены. Использовать большинство процедур в этом разделе термин *учетной записи Интернет*.  
  
## <a name="in-this-topic"></a>В этом разделе  
  
-   [Почему следует управлять сетевых учетных записей с помощью панели мониторинга?](#BKMK_WhyManageOnlineAccounts)  
  
-   [Создание учетных записей в Интернете](#BKMK_SECTION_CreateOnlineAccounts)  
  
-   [Управление записями интернет-служб](#BKMK_SECTION_ManageOnlineAccounts)  
  
-   [Управление электронной почтой Exchange Online](#BKMK_SECTION_ManageEmailAddresses)  
  
-   [Управление группами рассылок Exchange Online](#BKMK_SECTION_ManageDistributionGroups)  
  
##  <a name="BKMK_WhyManageOnlineAccounts"></a>Почему следует управлять сетевых учетных записей с помощью панели мониторинга?  
 При использовании панели мониторинга для назначения учетной записи Microsoft Online Services для учетной записи пользователя автоматически синхронизируются пароли учетных записей, и может поддерживать две учетные записи параллельно на протяжении всего жизненного цикла s учетной записи пользователя.  
  
 Это удобно для пользователя, который можно использовать один и тот же пароль для доступа к ресурсам на сервере и в Office 365. А вы можете применить те же требования безопасности для доступа к ресурсам в Office 365, которые могут потребоваться для локальных ресурсов.  
  
### <a name="how-does-password-synchronization-work"></a>Как работает синхронизация паролей?  
 При использовании панели мониторинга для назначения учетной записи Microsoft Online Services для учетной записи пользователя, пароль учетной записи пользователя автоматически синхронизируется с учетной записи в s. Это означает, что пользователю требуется только один пароль для доступа к ресурсам на сервере и в Office 365. Кроме того можно использовать одно имя для учетной записи пользователя и идентификатор пользователя s online.  
  
 Синхронизация пароля происходит автоматически и немедленно, когда пользователь изменяет пароль для учетной записи пользователя на компьютере, присоединенном к домену или с помощью удаленного веб-доступа.  
  
> [!IMPORTANT]
>  При интеграции Office 365 с Windows Server Essentials, пользователям не следует менять пароль для своей учетной записи Microsoft online на портале Office 365. Это может нарушить синхронизацию паролей.  
  
### <a name="simplified-account-creation"></a>Упрощенное создание учетной записи  
 При создании ваших начальной сетевых учетных записей с помощью панели мониторинга есть дополнительное преимущество. Можно создать учетные записи для всех пользователей одним действием. С другой стороны Если ваши сотрудники уже используете Office 365 их настройка нового сервера Windows Server Essentials, вы можете создать все учетные записи пользователей с сетевых учетных записей с помощью одного действия. Дополнительные сведения см. в разделе [Создание учетных записей в Интернете](#BKMK_SECTION_CreateOnlineAccounts).  
  
### <a name="manage-email-addresses-and-distribution-groups-from-the-dashboard"></a>Управление электронной почтой и группами рассылок с помощью панели мониторинга  
 Можно управлять вашей электронной почтой и группами рассылок Exchange Online с помощью панели мониторинга. И, можно использовать домен Интернета вашей организации s адресов электронной почты. Все это можно сделать с помощью панели мониторинга без входа Office 365. (Вы получите потребуется использовать группами рассылок можно управлять с помощью панели мониторинга Windows Server Essentials. Эта функция не поддерживается в Windows Server Essentials.) Дополнительные сведения см. в разделе [управление электронными адресами Exchange Online](#BKMK_SECTION_ManageEmailAddresses) и [Управление группами рассылок Exchange Online](#BKMK_SECTION_ManageDistributionGroups).  
  
### <a name="manage-the-user-account-and-online-account-together"></a>Совместное управление сетевой учетной записи и учетной записи пользователя  
 И вы можете управлять учетной записью Интернет вместе с учетной записи пользователя на протяжении жизненного цикла s учетной записи. Если отключить учетную запись пользователя, эта учетная запись также будет отключена в Microsoft Online Services. Если удалить учетную запись пользователя, эта учетная запись также удаляется. Дополнительные сведения см. в разделе [с учетными записями Интернет](#BKMK_SECTION_ManageOnlineAccounts).  
  
##  <a name="BKMK_SECTION_CreateOnlineAccounts"></a>Создание учетных записей в Интернете  
 После интеграции сервера с Office 365, он имеет смысл создать учетные записи Microsoft Online Services для пользователей с помощью панели мониторинга. Вы сможете принять большую гибкость при создании учетных записей. При наличии новой подписки на Office 365, вы можете Массовое создание учетных записей в Интернете для всех пользователей. Если вы уже создали ваших сетевых учетных записей в Office 365, не волнуйтесь. Если при настройке нового сервера, можно создать учетные записи пользователей на сервере, импортировав учетные записи. И при создании учетной записи отдельного пользователя или при добавлении учетной записи Интернет к существующей учетной записи пользователя можно назначить новой или существующей учетной записи.  
  
 **Требования к лицензии** необходима лицензия пользователя для каждой сети создаваемой учетной записи. Проверьте **Office 365** на странице панели мониторинга пользовательских лицензий, доступных по подписке Office 365. Если вам необходимо увеличить количество лицензий, вы получите иметь возможность открыть подписки на Office 365 в Office 365 для этого.  
  
 **Дальнейшие действия для пользователей** после добавления учетной записи Интернет для учетной записи пользователя пользователь должен изменить пароль для своей учетной записи в следующий раз при входе в. Новый пароль будет сразу же синхронизирован с учетной записью Интернет. После этого пользователь может использовать пароль для входа Office 365 со своим идентификатором Интернет.  
  
> [!IMPORTANT]
>  Обратите внимание пользователей на том, что им не следует менять пароль учетной записи в Office 365. Изменять пароль будет автоматически всякий раз, когда пользователь изменит пароль для своей учетной записи. Если пользователь изменит пароль в Интернете в Office 365, синхронизация паролей будет нарушена.  
  
 Процедуры, описанные в этом разделе, чтобы:  
  
-   [Массовое создание учетных записей в Интернете для существующих пользовательских учетных записей](#BKMK_ToBulkCreateOnlineAccounts)  
  
-   [Импорт учетных записей пользователей с учетными записями Microsoft Online Services](#BKMK_ToImportUserAccounts)  
  
-   [Создание новой учетной записи пользователя с помощью учетной записи Интернет назначены](#BKMK_ToCreateaNewUserAccount)  
  
-   [Назначение учетной записи Интернет учетной записи пользователя](#BKMK_ToAssignAnOnlineAccount)  
  
> [!NOTE]
>  Если вы используете Windows Server Essentials, вы увидите *учетной записи Office 365* вместо *учетной записи Microsoft Online Services* на протяжении всего этих процедур. Процесс аналогичен, но терминология в Windows Server Essentials.  
  
###  <a name="BKMK_ToBulkCreateOnlineAccounts"></a>Массовое создание учетных записей в Интернете для существующих пользовательских учетных записей  
  
1.  Войдите на сервер с правами администратора и откройте панель мониторинга Windows Server Essentials.  
  
2.  На панели мониторинга откройте **пользователей** страницы.  
  
3.  В **задачи пользователей**, нажмите кнопку **записями интернет-служб Майкрософт, добавить**.  
  
     **Записями добавить Microsoft Online Services** страницы мастера отображаются все учетные записи пользователей, у которых нет учетная запись Майкрософт. По умолчанию все учетные записи выбраны и имени пользователя предложен идентификатор Microsoft online Если вы привязали настраиваемый домен Интернета к подписке Office 365, этот домен будет использоваться по умолчанию.  
  
4.  На **записями добавить Microsoft Online Services** просмотрите учетные записи, которые будут созданы. Например поиск пользователей, которые уже есть учетная запись Интернет с другим Идентификатором Интернета, а также убедитесь, что выбран домена, который вы хотите использовать адресов электронной почты. Если вы внесете все необходимые изменения, нажмите **Далее**.  
  
5.  На **лицензий назначить Microsoft Online Services** страницы, выберите службам Office 365, которые понадобятся пользователям. При нажатии кнопки **Далее**, начнется создание учетных записей.  
  
    > [!NOTE]
    >  Необходимо иметь лицензию для служб в Office 365 для каждой учетной записи Интернет. Можно проверить наличие лицензий и, если нужно, открыть подписку для добавления лицензий **Office 365** на странице панели мониторинга.  
  
6.  Уведомлять пользователей о том, что у них теперь есть учетная запись Майкрософт. Прежде чем они могут войти в Office 365, им необходимо сменить пароль учетной записи пользователя в сети. Инструкции см. в разделе [начало использования новой учетная запись Майкрософт](#BKMK_ToBeginUsingAnOnlineAccount).  
  
###  <a name="BKMK_ToBeginUsingAnOnlineAccount"></a>Чтобы начать использовать новые учетная запись Майкрософт  
  
1.  Войдите на компьютер с учетной записью пользователя сети.  
  
2.  Измените пароль для учетной записи пользователя. Чтобы начать работу, нажмите клавиши Ctrl + Alt + Delete и выберите **изменения пароля**.  
  
     При изменении пароля, то пароль синхронизируется с вашей новой учетной записи. Теперь можно использовать тот же пароль для входа Office 365.  
  
3.  [Войдите Office 365](https://login.microsoftonline.com/login.srf?wa=wsignin1.0&rpsnv=3&ct=1398981834&rver=6.1.6206.0&wp=MBI_SSL&wreply=https:%2F%2Foutlook.office365.com%2Fowa%2F&id=260563&CBCXT=out) с использованием вашего нового идентификатора Интернет и пароля вашей учетной записи.  
  
    > [!IMPORTANT]
    >  Не меняйте пароль учетной записи в Office 365. Это приведет к нарушению синхронизации паролей. Ваш пароль в Интернете будет обновляться каждый раз при смене пароля для учетной записи пользователя сети.  
  
###  <a name="BKMK_ToImportUserAccounts"></a>Импорт пользовательских учетных записей из существующих учетных записей Интернет  
  
1.  На панели мониторинга откройте **пользователей** страницы.  
  
2.  В **задачи пользователей**, нажмите кнопку **импорт учетных записей из Office 365**.  
  
     Следующая страница отображает все записями интернет-служб для подписки на Office 365, у которых нет учетной записи пользователя на сервере. По умолчанию все учетные записи выбраны и имени пользователя предложен ИД Интернет-Служб.  
  
3.  Чтобы создать учетные записи пользователей:  
  
    1.  Внесите изменения, необходимые для предложенные учетные записи.  
  
    2.  При необходимости щелкните ссылку, чтобы просмотреть временные пароли, которые будут назначены учетным записям пользователей. Необходимо будет сообщить пользователям вместе с их новыми именами учетных записей временные пароли.  
  
         (После создания учетных записей, вы получите найти эти пароли, перечисленные в этом файле: *SystemDrive*\Users\\*Office365admin*\\*NewServerUser*.txt где *Office365admin* учетная запись сети, которая используется для администрирования Office 365 на сервере и *NewServerUser* является имя учетной записи пользователя.)  
  
    3.  Нажмите кнопку **Далее** Создание учетных записей пользователей.  
  
4.  Сообщите пользователям их новые учетные записи и временные пароли, они будут использовать для входа на сервер для первого œ время, и им необходимо будет сменить эти пароли для входа на. Инструкции для пользователей см. в разделе [начало использования новой учетная запись Майкрософт](#BKMK_ToBeginUsingAnOnlineAccount).  
  
     Убедитесь, что они знают, что пароли для учетных записей Интернет будут синхронизированы с их учетными записями в дальнейшем, и им не следует менять пароль в Office 365.  
  
###  <a name="BKMK_ToCreateaNewUserAccount"></a>Для создания новой учетной записи пользователя с учетная запись Интернет к нему  
  
1.  На панели мониторинга щелкните **пользователей**.  
  
2.  В **задачи пользователей**, нажмите кнопку **добавить учетную запись пользователя**. Откроется мастер создания учетной записи пользователя добавления.  
  
3.  Следуйте инструкциям, чтобы создать учетную запись пользователя.  
  
4.  На **назначить учетную запись Microsoft Online Services** страницы, либо создать новый сети учетной записи пользователя, либо назначьте существующей учетной записи:  
  
    -   Чтобы создать учетную запись сети, нажмите кнопку **создать учетную запись Microsoft Online Services и назначить этой учетной записи пользователя**и введите имя для учетной записи Microsoft Online Services (по умолчанию используется имя пользователя для идентификатора Интернет). Нажмите кнопку **Далее**.  
  
    -   Чтобы назначить существующей учетной записи Майкрософт, нажмите кнопку **назначить этой учетной записи пользователя существующую учетную запись Microsoft Online Services**и выберите существующую учетную запись из раскрывающегося списка. Нажмите кнопку **Далее**.  
  
    > [!NOTE]
    >  В Windows Server Essentials учетные записи Microsoft Online Services называются учетные записи Office 365 в мастерах и в подписях панели мониторинга.  
  
5.  Следуйте инструкциям для завершения работы мастера.  
  
6.  Уведомите пользователя, который им потребуется изменить пароль учетной записи для входа Office 365 со своей новой учетной записи. Инструкции см. в разделе [начало использования новой учетная запись Майкрософт](#BKMK_ToBeginUsingAnOnlineAccount).  
  
#### <a name="BKMK_ToAssignAnOnlineAccount"></a>Чтобы присвоить учетной записи Интернет учетной записи пользователя  
  
1.  На панели мониторинга щелкните **пользователей**.  
  
2.  Щелкните правой кнопкой мыши учетную запись пользователя в списке и нажмите кнопку **назначить учетная запись Microsoft online**. Microsoft Online учетной записи откроется мастер присвоения Services.  
  
3.  Назначение существующей учетной записи или создать новую для пользователя. Идентификатор сети по умолчанию для новой учетной записи устанавливается имя пользователя. Нажмите кнопку **Далее** для добавления учетной записи Интернет учетной записи пользователя.  
  
4.  На последней странице мастера проверьте указанную информацию, а затем нажмите кнопку **закрыть**.  
  
5.  Уведомите пользователя, который им потребуется изменить пароль учетной записи для входа Office 365 со своей новой учетной записи. Инструкции см. в разделе [начало использования новой учетная запись Майкрософт](#BKMK_ToBeginUsingAnOnlineAccount).  
  
##  <a name="BKMK_SECTION_ManageOnlineAccounts"></a>Управление записями интернет-служб  
 При добавлении учетной записи Интернет учетной записи пользователя в Windows Server Essentials можно управлять этими учетными записями совместно на протяжении всего существования учетной записи s.  
  
###  <a name="BKMK_UnderstandingAccountStatus"></a>Общее представление о статусе учетной записи в сети  
 После присвоения учетной записи Microsoft Online Services учетной записи пользователя, адрес электронной почты для учетной записи отображается в **учетной записи Microsoft online** столбец **пользователей** страницы панели мониторинга. (В Windows Server Essentials столбец называется **учетной записи Office 365**.)  
  
-   Синий значок рядом с адресом электронной почты означает, что учетная запись Интернет активен. То есть учетная запись имеет текущей лицензии Office 365, и пользователь может использовать ИД Интернет-Служб для входа Office 365.  
  
-   Указывает, если значок затемнен адрес электронной почты учетной записи Интернет обусловлено неактивных œ либо лицензия не активна или эта учетная запись была присвоена. Если вы отмените назначение учетной записи Интернет пользователя s, лицензия будет также отменена, и пользователь не сможет войти в систему с помощью учетной записи Office 365. Тем не менее на сервере сохранится сопоставление имени учетной записи пользователя и адрес электронной почты Office 365.  
  
###  <a name="BKMK_UnassignOnlineAccount"></a>Ограничьте доступ к учетной записи Интернет  
 Что делать, если пользователь покидает компанию или вы хотите ограничить s пользователю доступ к службам Office 365? Если вы управление ваших пользователей сетевых учетных записей вместе с их учетными записями пользователей в Windows Server Essentials, у вас есть три варианта:  
  
-   **Отмена назначения учетной записи Интернет** ? Если вы хотите запретить пользователям с помощью Office 365, не ограничивая его доступ к ресурсам на сервере, вы можете отменить назначенную ему учетная запись Интернет. Лицензия Office 365 будет отозвана, и пользователь не сможет войти в Office 365. Тем не менее на сервере сохранится сопоставление имени учетной записи пользователя и адрес электронной почты Office 365. Инструкции см. в разделе [Отмена назначения учетной записи пользователя учетной записи Интернет](#BKMK_ToUnassignAnOnlineAccount).  
  
-   **Отключить учетную запись пользователя** ? При отключении учетной записи пользователя, так как сотрудник покидает временно или навсегда, s online учетной записи пользователя также будет отключена. Эта учетная запись не может использоваться, но данные пользователя, включая сообщения электронной почты, сохраняются в Microsoft Online Services. Инструкции см. в разделе [отключении учетной записи пользователя](Manage-User-Accounts-in-Windows-Server-Essentials.md#BKMK_Manage6) в [управление учетными записями пользователей](Manage-User-Accounts-in-Windows-Server-Essentials.md).  
  
-   **Удалить учетную запись пользователя** ? При удалении учетной записи пользователя, Интернет-служб тоже будет удалена из Microsoft Online Services. Инструкции см. в разделе [удалить учетную запись пользователя](Manage-User-Accounts-in-Windows-Server-Essentials.md#BKMK_Remove) в [управление учетными записями пользователей](Manage-User-Accounts-in-Windows-Server-Essentials.md).  
  
    > [!WARNING]
    >  Имейте в виду, что при удалении учетной записи Интернет данные пользователя будут подчиняются политике хранения Microsoft Online Services. Если необходимо сохранить данные пользователя s лица сотрудника после увольнения, отключите учетную запись пользователя, а отключите ее.  
  
####  <a name="BKMK_ToUnassignAnOnlineAccount"></a>Отмена назначения учетной записи Интернет учетной записи пользователя  
  
1.  На панели мониторинга щелкните **пользователей**.  
  
2.  Щелкните правой кнопкой мыши учетную запись пользователя в списке и нажмите кнопку **отменить назначение учетная запись Майкрософт** (в Windows Server Essentials щелкните **Отмена учетной записи Office 365**).  
  
3.  В окне подтверждения нажмите кнопку **Да**.  
  
##  <a name="BKMK_SECTION_ManageEmailAddresses"></a>Управление электронной почтой Exchange Online  
 Добавляя электронные адреса s online учетной записи пользователя в Windows Server Essentials, вы можете разрешить пользователю возможность получать электронную почту на несколько адресов электронной почты в Exchange Online.  
  
###  <a name="BKMK_PROC_AddEmailAliases"></a>Добавление электронной почты пользователя s учетной записи Майкрософт  
  
1.  Для мониторинга Windows Server Essentials щелкните **пользователей**.  
  
2.  Щелкните правой кнопкой мыши учетную запись пользователя в списке и нажмите кнопку **просмотреть свойства учетной записи**.  
  
3.  На **Microsoft online** свойств учетной записи (или **Office 365** вкладку в Windows Server Essentials), нажмите кнопку **добавить**.  
  
4.  Введите псевдоним электронной почты, а затем выберите домен электронной почты.  
  
5.  Нажмите кнопку **ОК** дважды.  
  
##  <a name="BKMK_SECTION_ManageDistributionGroups"></a>Управление группами рассылок Exchange Online (только для Windows Server Essentials)  
 После интеграции сервера Windows Server Essentials с Office 365, можно создать и управляйте группами рассылки Exchange Online при помощи панели мониторинга Windows Server Essentials. Вы получите это сделать на **группы рассылки** вкладка, которая добавляется в **пользователей** страницы. Эта вкладка будет доступна только в том случае, если у вас есть подписка Exchange Online. Эта функция не работает в Windows Server Essentials.  
  
 Используйте следующие процедуры для:  
  
-   [Добавление группы рассылки](#BKMK_PROCEDURE_AddDistGroup)  
  
-   [Изменение списка участников группы рассылки](#BKMK_ChangeGroupMembers)  
  
-   [Изменение пользователя s в группах рассылок](#BKMK_EditUserMemberships)  
  
-   [Удаление групп рассылок](#BKMK_RemoveDistributionGroup)  
  
###  <a name="BKMK_PROCEDURE_AddDistGroup"></a>Чтобы добавить группу рассылки  
  
1.  На панели мониторинга в Windows Server Essentials щелкните **пользователей**, а затем нажмите кнопку **группы рассылки** вкладку.  
  
2.  В **задачи групп рассылок**, нажмите кнопку **добавить группу рассылки**.  
  
     Откроется мастер создания группы распространения добавления.  
  
3.  На **добавить новую группу распространения** введите следующие сведения и нажмите кнопку **Далее**:  
  
    -   Введите имя группы, необязательное описание и псевдоним электронной почты для новой группы рассылки.  
  
    -   По умолчанию группа рассылки возможность получать электронную почту от адресатов вне организации. Если вы не хотите этого, необходимо отключите этот параметр.  
  
4.  На **добавлять члены группы** страницы, используйте **добавить** для добавления активных учетных записей пользователей, имеющих учетная запись Интернет к ним, а также других групп рассылок в новую группу распространения. Нажмите кнопку **Далее**.  
  
     Новая группа рассылки в Exchange Online создана.  
  
###  <a name="BKMK_ChangeGroupMembers"></a>Изменение списка участников группы рассылки  
  
1.  На панели мониторинга щелкните **пользователей**, а затем нажмите кнопку **группы рассылки** вкладку.  
  
2.  Щелкните правой кнопкой мыши группу рассылки в списке и нажмите кнопку **измените членство в группе**.  
  
3.  Используйте **добавить** и **удалить** кнопки, чтобы добавить или удалить из группы рассылки активных учетных записей в Интернете. Нажмите кнопку **Далее** обновить список членов группы рассылки в Exchange Online.  
  
###  <a name="BKMK_EditUserMemberships"></a>Для изменения членства в группах распространения пользователя s  
  
1.  На панели мониторинга щелкните **пользователей**.  
  
2.  Щелкните правой кнопкой мыши учетную запись пользователя в списке и нажмите кнопку **просмотреть свойства учетной записи**.  
  
3.  В свойствах учетной записи пользователя, нажмите кнопку **группы рассылки**, а затем щелкните **изменить**.  
  
4.  В **изменить членство в группе** используйте **добавить** и **удалить** кнопки, чтобы добавить или удалить группы рассылки из учетной записи и нажмите кнопку **закрыть**.  
  
5.  Нажмите кнопку **ОК** сохранить обновленные настройки свойств учетной записи.  
  
###  <a name="BKMK_RemoveDistributionGroup"></a>Удаление группы рассылки  
  
1.  На панели мониторинга щелкните **пользователей**, а затем нажмите кнопку **группы рассылки** вкладку.  
  
2.  Щелкните правой кнопкой мыши группу рассылки в списке и нажмите кнопку **удалить группу**.  
  
3.  В окне подтверждения нажмите кнопку **удалить группу**.  
  
     Группа рассылки удалена из Exchange Online.  
  
## <a name="see-also"></a>См. также:  
  
-   [Управление учетными записями пользователей](Manage-User-Accounts-in-Windows-Server-Essentials.md)  
  
-   [Управление Office 365](Manage-Office-365-in-Windows-Server-Essentials.md)  
  
-   [Управление Microsoft Online Services](Manage-Microsoft-Online-Services-in-Windows-Server-Essentials.md)