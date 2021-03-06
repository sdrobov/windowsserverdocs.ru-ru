---
title: Управление учетными записями интернет-служб пользователей Windows Server Essentials
description: Описание использования Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: c09f4cf6-4d12-49fe-9ae4-e6cb14027b9d
author: nnamuhcs
ms.author: daveba
ms.openlocfilehash: 973e83fc02af12b63d48be98e985b2826551ce46
ms.sourcegitcommit: d99bc78524f1ca287b3e8fc06dba3c915a6e7a24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/27/2020
ms.locfileid: "87180960"
---
# <a name="manage-online-accounts-for-windows-server-essentials-users"></a>Управление учетными записями интернет-служб пользователей Windows Server Essentials

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

При интеграции сервера Windows Server Essentials с Microsoft Office 365 можно управлять учетными записями в Интернете вместе с учетными записями пользователей на панели мониторинга. В этом разделе вы узнаете, что можно получить, управляя учетными записями Microsoft Online Services на панели мониторинга, как создавать учетные записи в сети и управлять ими с панели мониторинга, а также как управлять адресами электронной почты и группами рассылки для Exchange Online с панели мониторинга.


> [!NOTE]
>  Для управления учетными записями Microsoft Online Services в Windows Server Essentials необходимо интегрировать сервер с Office 365. Инструкции см. в разделе [Manage Office 365](Manage-Office-365-in-Windows-Server-Essentials.md).

> [!IMPORTANT]
>  Если вы управляете сетевыми учетными записями в Windows Server Essentials, вы привыкли просматривать учетные записи Microsoft Online Services, которые называются *учетными записями Office 365*. На панели мониторинга в Windows Server Essentials метки были изменены на *учетные записи Microsoft Online Services*, а *учетные записи Microsoft Online* — короткими. Сами учетные записи и процесс остались без изменений, поменялись только названия. В данном разделе в основном применяется термин *учетная запись интернет-служб*.

## <a name="in-this-topic"></a>В этом разделе

-   [Что дает управление учетными записями интернет-служб при помощи панели мониторинга?](#BKMK_WhyManageOnlineAccounts)

-   [Создание учетных записей интернет-служб](#BKMK_SECTION_CreateOnlineAccounts)

-   [Управление учетными записями интернет-служб](#BKMK_SECTION_ManageOnlineAccounts)

-   [Управление электронной почтой Exchange Online](#BKMK_SECTION_ManageEmailAddresses)

-   [Управление группами рассылок Exchange Online](#BKMK_SECTION_ManageDistributionGroups)

##  <a name="why-should-i-manage-my-online-accounts-from-the-dashboard"></a><a name="BKMK_WhyManageOnlineAccounts"></a>Зачем мне управлять учетными записями в Интернете с панели мониторинга?
 При использовании панели мониторинга для назначения учетной записи Microsoft Online Services учетной записи пользователя пароли учетной записи автоматически синхронизируются, и эти две учетные записи можно поддерживать вместе в течение жизненного цикла учетной записи пользователя.

 Это удобно для пользователя, который может использовать тот же пароль для доступа к ресурсам на сервере и в Office 365. Кроме того, можно применять те же требования к паролю для доступа к ресурсам в Office 365, которые требуются для ваших собственных ресурсов.

### <a name="how-does-password-synchronization-work"></a>Как работает синхронизация паролей?
 При использовании панели мониторинга для назначения учетной записи Microsoft Online Services учетной записи пользователя пароль учетной записи пользователя автоматически синхронизируется с учетной записью пользователя Online. Это означает, что пользователю требуется только один пароль для доступа к ресурсам на сервере и в Office 365. Кроме того, можно использовать одно и то же имя для учетной записи пользователя и идентификатор пользователя в Интернете.

 Синхронизация пароля происходит автоматически сразу после изменения пользователем пароля для учетной записи на присоединенном к домену компьютере или с помощью удаленного веб-доступа.

> [!IMPORTANT]
>  Если Office 365 интегрирован с Windows Server Essentials, пользователи не должны менять пароль учетной записи Microsoft Online с портала Office 365. Это может нарушить синхронизацию паролей.

### <a name="simplified-account-creation"></a>Упрощенное создание учетной записи
 При создании начальных учетных записей из панели мониторинга можно воспользоваться другим преимуществом. Вы можете создать учетные записи интернет-служб для всех пользователей одним действием. С другой стороны, если ваши сотрудники уже используют Office 365 и вы настроили новый сервер Windows Server Essentials, вы можете создать все учетные записи пользователей из Интернет-учетных записей с помощью одного действия. Дополнительные сведения см. в разделе [Создание учетных записей интернет-служб](#BKMK_SECTION_CreateOnlineAccounts).

### <a name="manage-email-addresses-and-distribution-groups-from-the-dashboard"></a>Управление электронной почтой и группами рассылок при помощи панели мониторинга
 Вы сможете управлять вашей электронной почтой и группами рассылок Exchange Online при помощи панели мониторинга. Вы также можете использовать домен Интернета Организации в адресах электронной почты. Все это можно выполнить на панели мониторинга без входа в Office 365. (Для управления группами распространения с панели мониторинга необходимо использовать Windows Server Essentials. Эта функция не поддерживается в Windows Server Essentials.) Дополнительные сведения см. в статьях [Управление адресами электронной почты для Exchange Online](#BKMK_SECTION_ManageEmailAddresses) и [Управление группами рассылки для Exchange Online](#BKMK_SECTION_ManageDistributionGroups).

### <a name="manage-the-user-account-and-online-account-together"></a>Совместное управление пользовательскими учетными записями и учетными записями интернет-служб
 Вы также можете управлять учетной записью в сети, а также учетной записью пользователя во время жизненного цикла учетной записи. Отключение пользовательской учетной записи приведет к отключению учетной записи в Microsoft Online Services. Удаление пользовательской учетной записи приведет к удалению учетной записи интернет-служб. См. также [Управление учетными записями интернет-служб](#BKMK_SECTION_ManageOnlineAccounts).

##  <a name="create-online-accounts"></a><a name="BKMK_SECTION_CreateOnlineAccounts"></a>Создание учетных записей в сети
 После интеграции сервера с Office 365 его можно использовать для создания учетных записей Microsoft Online Services для пользователей на панели мониторинга. Создание учетных записей в Интернете обеспечивает большую гибкость. Если у вас есть новая подписка Office 365, можно создать учетные записи в Интернете для всех пользователей. Если вы уже создали сетевые учетные записи в Office 365, не беспокойтесь. При настройке нового сервера можно создать учетные записи пользователей на сервере, импортировав сетевые учетные записи. При создании учетной записи отдельного пользователя или при добавлении учетной записи в существующую учетную запись пользователя можно назначить новую или существующую учетную запись в сети.

 **Требования к лицензии** Для каждой создаваемой учетной записи в Интернете потребуется лицензия пользователя. Проверьте страницу **office 365** на панели мониторинга, чтобы узнать, сколько пользовательских лицензий доступно в вашей подписке Office 365. Если вам нужно добавить дополнительные пользовательские лицензии, вы сможете открыть подписку Office 365 в Office 365 для этого.

 **Дальнейшие действия для пользователей** После добавления учетной записи для учетной записи пользователя пользователь должен изменить пароль для своей учетной записи пользователя при следующем входе в систему. Новый пароль будет сразу же синхронизирован с учетной записью интернет-служб. После этого они смогут использовать пароль для входа в Office 365 с помощью своего Интернет-идентификатора.

> [!IMPORTANT]
>  Обратите внимание на пользователей, что они никогда не должны изменять пароль своей учетной записи в Office 365. Этот пароль будет всегда автоматически меняться при смене пароля пользовательской учетной записи. При изменении пароля в Интернете в Office 365 синхронизация паролей будет нарушена.

 Далее приведены следующие процедуры:

-   [Массовое создание учетных записей интернет-служб для существующих пользовательских учетных записей](#BKMK_ToBulkCreateOnlineAccounts)

-   [Импорт пользовательских учетных записей из учетных записей Microsoft Online Services](#BKMK_ToImportUserAccounts)

-   [Создание новой пользовательской учетной записи вместе со связанной учетной записью интернет-служб](#BKMK_ToCreateaNewUserAccount)

-   [Назначение учетной записи интернет-служб для пользовательской учетной записи](#BKMK_ToAssignAnOnlineAccount)

> [!NOTE]
>  Если вы используете Windows Server Essentials, в рамках этих процедур вы увидите *учетную запись Office 365* вместо *учетной записи Microsoft Online Services* . Процесс аналогичен, но терминология изменилась в Windows Server Essentials.

###  <a name="to-bulk-create-online-accounts-for-your-existing-user-accounts"></a><a name="BKMK_ToBulkCreateOnlineAccounts"></a>Создание полного набора учетных записей в Интернете для существующих учетных записей пользователей

1.  Войдите на сервер с правами администратора и откройте панель мониторинга Windows Server Essentials.

2.  На панели мониторинга откройте страницу **Пользователи**.

3.  В разделе **Задачи пользователей** нажмите на **Добавление учетных записей интернет-служб Microsoft**.

     На странице мастера **Добавление учетных записей интернет-служб Microsoft** будут показаны все пользовательские учетные записи, которые не имеют учетных записей интернет-служб Microsoft. По умолчанию все учетные записи выбраны и для ИД интернет-служб Microsoft предложено имя пользователя. Если вы связали пользовательский домен Интернета с подпиской Office 365, этот домен будет использоваться по умолчанию.

4.  Проверьте учетные записи на странице **Добавление учетных записей интернет-служб Microsoft**. Например, проверьте, не включены ли пользователи, у которых уже есть учетная запись интернет-служб с другим идентификатором интернет-служб, а также, что выбран именно тот домен для электронной почты, который вы хотите использовать. После того, как вы внесете все необходимые изменения, нажмите **Далее**.

5.  На странице **Назначение лицензий Microsoft Online Services** выберите службы Office 365, которые будут использоваться вашими пользователями. Нажмите **Далее**. Начнется создание учетных записей.

    > [!NOTE]
    >  Для каждой учетной записи в Интернете необходимо иметь лицензию на службу в Office 365. Проверить наличие лицензий и, если нужно, открыть подписку для добавления лицензий, можно на странице **Office 365** панели мониторинга.

6.  Не забудьте уведомить пользователей о том, что у них теперь есть учетные записи интернет-служб Microsoft. Чтобы пользователи могли входить в Office 365, они должны изменить пароль своей учетной записи пользователя сети. Инструкции см. в разделе [Начало использования новой учетной записи интернет-служб Microsoft](#BKMK_ToBeginUsingAnOnlineAccount).

###  <a name="to-begin-using-a-new-microsoft-online-account"></a><a name="BKMK_ToBeginUsingAnOnlineAccount"></a>Начало работы с новой учетной записью Microsoft Online

1.  Войдите в свою сетевую учетную запись на компьютере.

2.  Смените пароль своей учетной записи. Для этого нажмите Ctrl+Alt+Delete и выберите **Сменить пароль**.

     После того, как вы смените свой пароль, он будет синхронизирован с вашей новой учетной записью интернет-служб. Теперь вы можете использовать тот же пароль для входа в Office 365.

3.  [Войдите в Office 365](https://login.microsoftonline.com/login.srf?wa=wsignin1.0&rpsnv=3&ct=1398981834&rver=6.1.6206.0&wp=MBI_SSL&wreply=https:%2F%2Foutlook.office365.com%2Fowa%2F&id=260563&CBCXT=out) , используя свой новый идентификатор интернет-служб и пароль учетной записи пользователя.

    > [!IMPORTANT]
    >  Не изменяйте пароль учетной записи в Интернете в Office 365. Это приведет к нарушению синхронизации паролей. Пароль вашей учетной записи интернет-служб будет автоматически обновляться каждый раз при смене вами пароля к вашей учетной записи.

###  <a name="to-import-user-accounts-from-your-existing-online-accounts"></a><a name="BKMK_ToImportUserAccounts"></a>Импорт учетных записей пользователей из существующих Интернет-учетных записей

1.  На панели мониторинга откройте страницу **Пользователи**.

2.  В разделе **Задачи пользователей**нажмите на **Импорт учетных записей из Office 365**.

     На следующей странице отображаются все учетные записи в Интернете для подписки Office 365, которые не имеют учетной записи пользователя на сервере. По умолчанию все учетные записи выбраны и в качестве имени пользователя предложен ИД интернет-служб.

3.  Чтобы создать учетные записи пользователей:

    1.  Внесите изменения, если считаете нужным, в предложенные учетные записи.

    2.  Перейдя по ссылке, просмотрите временные пароли, которые будут назначены учетным записям (это действие выполнять необязательно). Эти временные пароли необходимо будет сообщить пользователям вместе с их новыми именами учетных записей.

         (После создания учетных записей вы увидите следующие пароли, перечисленные в этом файле: *systemdrive*\Users \\ *Office365admin* \\ *Невсерверусер*. txt, где *Office365admin* — это Сетевая учетная запись, используемая для администрирования Office 365 на сервере, а *невсерверусер* — новое имя учетной записи пользователя.)

    3.  Нажмите **Далее**, чтобы завершить создание учетных записей.

4.  Сообщите пользователям о новых учетных записях пользователей и временных паролях, которые они будут использовать для входа на сервер в первый раз: и что им потребуется изменить пароль после входа. Инструкции для пользователей см. в разделе [Начало использования новой учетной записи интернет-служб Microsoft](#BKMK_ToBeginUsingAnOnlineAccount).

     Убедитесь в том, что пароли для своей учетной записи в сети будут синхронизированы с учетной записью пользователя, и они не должны изменять свой сетевой пароль в Office 365.

###  <a name="to-create-a-new-user-account-with-an-online-account-assigned-to-it"></a><a name="BKMK_ToCreateaNewUserAccount"></a>Создание новой учетной записи пользователя с назначенной учетной записью в сети

1.  На панели мониторинга откройте раздел **Пользователи**.

2.  В разделе **Задачи пользователей** нажмите **Добавить учетную запись пользователя**. Откроется мастер создания учетной записи пользователя.

3.  Следуйте инструкциям по созданию учетной записи пользователя.

4.  На странице **Назначить учетную запись Microsoft Online Services** создайте новую учетную запись интернет-служб или выберите уже существующую:

    -   Для добавления новой учетной записи нажмите **Добавить новую учетную запись Microsoft Online Services и связать ее с этой учетной записью пользователя** и введите имя учетной записи Microsoft Online Services (по умолчанию для идентификатора Интернет используется имя пользователя). Затем нажмите кнопку **Далее**.

    -   Для добавления уже существующей учетной записи интернет-служб нажмите **Назначить этой учетной записи пользователя существующую учетную запись Microsoft Online Services** и выберите из выпадающего списка существующую учетную запись. Затем нажмите кнопку **Далее**.

    > [!NOTE]
    >  В Windows Server Essentials учетные записи Microsoft Online Services называются учетными записями Office 365 в мастерах и метках панелей мониторинга.

5.  Для завершения работы мастера следуйте инструкциям на экране.

6.  Сообщите пользователям, чтоб им необходимо сменить пароль своей учетной записи прежде, чем они смогут войти в Office 365 с новой учетной записью интернет-служб. Инструкции см. в разделе [Начало использования новой учетной записи интернет-служб Microsoft](#BKMK_ToBeginUsingAnOnlineAccount).

#### <a name="to-assign-an-online-account-to-a-user-account"></a><a name="BKMK_ToAssignAnOnlineAccount"></a>Назначение учетной записи интернет-служб для пользовательской учетной записи

1.  На панели мониторинга откройте раздел **Пользователи**.

2.  Нажмите правой кнопкой мыши учетную запись пользователя в списке, затем нажмите **Присвоение учетной записи интернет-служб Microsoft**. Откроется мастер присвоения учетных записей Microsoft Online Services.

3.  Присвоение пользователю существующей учетной записи интернет-служб или создание новой. По умолчанию в качестве ИД интернет-служб для новой учетной записи устанавливается имя пользователя. Нажмите **Далее**, чтобы присвоить учетной записи пользователя учетную запись интернет-служб.

4.  На заключительной странице мастера проверьте указанную информацию, затем нажмите **Закрыть**.

5.  Сообщите пользователям, чтоб им необходимо сменить пароль своей учетной записи прежде, чем они смогут войти в Office 365 с новой учетной записью интернет-служб. Инструкции см. в разделе [Начало использования новой учетной записи интернет-служб Microsoft](#BKMK_ToBeginUsingAnOnlineAccount).

##  <a name="manage-online-accounts"></a><a name="BKMK_SECTION_ManageOnlineAccounts"></a>Управление учетными записями в сети
 При добавлении учетной записи Online к учетной записи пользователя в Windows Server Essentials можно управлять обеими учетными записями вместе в течение жизненного цикла учетной записи.

###  <a name="understanding-the-online-account-status"></a><a name="BKMK_UnderstandingAccountStatus"></a>Основные сведения о состоянии учетной записи в сети
 После присвоения учетной записи пользователя учетной записи Microsoft Online Services ее адрес электронной почты появится в колонке **Учетная запись интернет-служб Microsoft** на странице панели мониторинга **Пользователи**. (В Windows Server Essentials метка столбца — **учетная запись Office 365**.)

-   Наличие синего значка рядом с электронной почтой говорит о том, что учетная запись интернет-служб активна. Это значит, что у учетной записи есть Текущая лицензия Office 365, и пользователь может использовать идентификатор в Интернете для входа в Office 365.

-   Затененный значок рядом с адресом электронной почты означает, что Сетевая учетная запись неактивна: либо потому, что лицензия больше не активна, либо учетная запись в сети не была назначена. При отснятии назначения учетной записи пользователя Online лицензия удаляется, и пользователь не может войти в Office 365 с помощью учетной записи. Однако сервер поддерживает сопоставление между именем учетной записи пользователя и адресом электронной почты Office 365.

###  <a name="restrict-access-to-an-online-account"></a><a name="BKMK_UnassignOnlineAccount"></a>Ограничение доступа к учетной записи в сети
 Что делать, если пользователь покидает вашу организацию или вы хотите ограничить доступ пользователей к службам Office 365? Если вы управляете учетными записями пользователей в Интернете вместе с учетными записями пользователей в Windows Server Essentials, у вас есть три варианта:

-   **Отменить назначение учетной записи в сети** ? Если вы хотите запретить пользователю использовать Office 365 без запрета доступа к ресурсам на сервере, следует отменить назначение учетной записи в сети. Будет выпущена лицензия Office 365, и пользователю не удастся войти в Office 365. Однако сервер поддерживает сопоставление между именем учетной записи пользователя и адресом электронной почты Office 365. Инструкции см. [в разделе Отмена назначения учетной записи в сети учетной записи пользователя](#BKMK_ToUnassignAnOnlineAccount).

-   **Деактивировать учетную запись пользователя** ? Если отключить учетную запись пользователя из-за того, что сотрудник оставляет, временно или безвозвратно, учетная запись пользователя Online также деактивируется. Учетную запись интернет-служб нельзя будет использовать, но данные пользователя, в том числе электронная почта, будут сохранены в Microsoft Online Services. Инструкции см. в статье [Отключение учетной записи пользователя](Manage-User-Accounts-in-Windows-Server-Essentials.md#BKMK_Manage6) в разделе [Управление учетными записями пользователей](Manage-User-Accounts-in-Windows-Server-Essentials.md).

-   **Удалить учетную запись пользователя** ? При удалении учетной записи пользователя Сетевая учетная запись удаляется также из служб Microsoft Online Services. Инструкции см. в статье [Удаление учетной записи пользователя](Manage-User-Accounts-in-Windows-Server-Essentials.md#BKMK_Remove) в разделе [Управление учетными записями пользователей](Manage-User-Accounts-in-Windows-Server-Essentials.md).

    > [!WARNING]
    >  Следует учитывать, что при удалении учетной записи интернет-служб, пользовательские данные подчиняются политике хранения Microsoft Online Services. Если необходимо хранить пользовательские данные пользователя после ухода сотрудника, отключите учетную запись пользователя, а не удаляйте ее.

####  <a name="to-unassign-an-online-account-from-a-user-account"></a><a name="BKMK_ToUnassignAnOnlineAccount"></a>Отмена назначения учетной записи в сети учетной записи пользователя

1.  На панели мониторинга откройте раздел **Пользователи**.

2.  Щелкните правой кнопкой мыши учетную запись пользователя в списке и выберите **Отменить назначение учетной записи Microsoft Online** (в Windows Server Essentials щелкните **Отменить назначение учетной записи Office 365**).

3.  В окне подтверждения нажмите **Да**.

##  <a name="manage-email-addresses-for-exchange-online"></a><a name="BKMK_SECTION_ManageEmailAddresses"></a>Управление адресами электронной почты для Exchange Online
 Добавив адреса электронной почты в учетную запись пользователя Online в Windows Server Essentials, вы сможете разрешить пользователю принимать электронную почту по нескольким адресам электронной почты в Exchange Online.

###  <a name="to-add-additional-email-addresses-to-a-user-s-microsoft-online-account"></a><a name="BKMK_PROC_AddEmailAliases"></a>Добавление дополнительных адресов электронной почты в учетную запись Microsoft Online пользователя

1.  На панели мониторинга Windows Server Essentials щелкните **Пользователи**.

2.  Нажмите правой кнопкой мыши учетную запись пользователя в списке, затем нажмите **Просмотр настроек учетной записи**.

3.  На вкладке **Microsoft Online** в свойствах учетной записи (или на вкладке **Office 365** в Windows Server Essentials) нажмите кнопку **добавить**.

4.  Введите псевдоним электронной почты и выберите домен

5.  Щелкните дважды **ОК**.

##  <a name="manage-distribution-groups-for-exchange-online-windows-server-essentials-only"></a><a name="BKMK_SECTION_ManageDistributionGroups"></a>Управление группами рассылки для Exchange Online (только для Windows Server Essentials)
 После интеграции сервера Windows Server Essentials с Office 365 можно создавать группы рассылки для Exchange Online и управлять ими с помощью панели мониторинга Windows Server Essentials. Это делается на вкладке **группы рассылки** , которая добавляется на страницу **Пользователи** . Эта вкладка будет доступна только в том случае, если у вас есть подписка Exchange Online. Эта функция недоступна в Windows Server Essentials.

 Далее вы найдете следующие инструкции:

-   [Добавление групп рассылок](#BKMK_PROCEDURE_AddDistGroup)

-   [Изменение списка участников группы рассылки](#BKMK_ChangeGroupMembers)

-   [Изменение членства в группах рассылки пользователя](#BKMK_EditUserMemberships)

-   [Удаление групп рассылок](#BKMK_RemoveDistributionGroup)

###  <a name="to-add-a-distribution-group"></a><a name="BKMK_PROCEDURE_AddDistGroup"></a>Добавление группы рассылки

1.  На панели мониторинга в Windows Server Essentials щелкните **Пользователи**, а затем перейдите на вкладку **группы рассылки** .

2.  В разделе **Задачи групп рассылок** нажмите **Добавление группы рассылки**.

     Откроется мастер добавления группы рассылки.

3.  На странице **Добавление новой группы рассылки** введите указанную ниже информацию, после чего нажмите **Далее**:

    -   Введите название группы, если нужно, описание, а также псевдоним электронной почты.

    -   По умолчанию группа рассылки имеет возможность получать электронную почту от адресатов вне организации. Вы можете отключить эту функцию.

4.  На странице **Добавление членов группы** воспользуйтесь кнопкой **Добавить** для добавления в новую группу рассылки активных учетных записей пользователей, у которых есть учетная запись интернет-служб, а также других групп рассылок. Затем нажмите кнопку **Далее**.

     Новая группа рассылки в Exchange Online создана.

###  <a name="to-change-the-members-of-a-distribution-group"></a><a name="BKMK_ChangeGroupMembers"></a>Изменение членов группы рассылки

1.  На панели мониторинга выберите **Пользователи** и перейдите на вкладку **Группы рассылки**.

2.  Нажмите правой кнопкой мыши группу рассылки в списке и нажмите **Изменение списка участников группы**.

3.  С помощью кнопок **Добавить** и **Удалить** добавьте или удалите учетные записи интернет-служб. Нажмите **Далее**, чтобы обновить список членов группы рассылки в Exchange Online.

###  <a name="to-change-a-user-s-distribution-group-memberships"></a><a name="BKMK_EditUserMemberships"></a>Изменение членства в группах рассылки пользователя

1.  На панели мониторинга откройте раздел **Пользователи**.

2.  Нажмите правой кнопкой мыши учетную запись пользователя в списке, затем нажмите **Просмотр настроек учетной записи**.

3.  Выберите вкладку **Группы рассылок** и нажмите кнопку **Править**.

4.  В разделе **Правка членства в группах** с помощью кнопок **Добавить** и **Удалить** добавьте или удалите группы рассылок для этого пользователя, после чего нажмите **Закрыть**.

5.  Нажмите **OK**, чтобы сохранить обновленные настройки.

###  <a name="to-remove-a-distribution-group"></a><a name="BKMK_RemoveDistributionGroup"></a>Удаление группы рассылки

1.  На панели мониторинга выберите **Пользователи** и перейдите на вкладку **Группы рассылки**.

2.  Нажмите правой кнопкой мыши группу рассылки из списка и нажмите **Удалить группу**.

3.  В окне подтверждения нажмите **Удалить группу**.

     Группа рассылки удалена из Exchange Online.

## <a name="additional-references"></a>Дополнительные ссылки

-   [Управление учетными записями пользователей](Manage-User-Accounts-in-Windows-Server-Essentials.md)

-   [Управление Office 365](Manage-Office-365-in-Windows-Server-Essentials.md)

-   [Управление Microsoft Online Services](Manage-Microsoft-Online-Services-in-Windows-Server-Essentials.md)
