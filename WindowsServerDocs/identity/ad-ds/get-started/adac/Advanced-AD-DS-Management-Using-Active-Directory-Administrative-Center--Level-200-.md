---
ms.assetid: 4d21d27d-5523-4993-ad4f-fbaa43df7576
title: "Управления Дополнительно AD DS при помощи центра администрирования Active Directory (уровень 200)"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 19e83ce0123bd484c61d5a4522ebdd90cd40241e
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="advanced-ad-ds-management-using-active-directory-administrative-center-level-200"></a>Управления Дополнительно AD DS при помощи центра администрирования Active Directory (уровень 200)

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

В более подробным, включая их архитектуру, примеры для типичных задач и сведения об устранении неполадок в этом разделе рассматривается обновленный центр администрирования Active Directory с новой корзины Active Directory, детальной политики паролей и средство просмотра журнала Windows PowerShell. Вводные сведения см. в разделе [введение в Active Directory дополнительные возможности центра администрирования & #40; Уровень 100 & #41; ](../../../ad-ds/get-started/adac/Introduction-to-Active-Directory-Administrative-Center-Enhancements--Level-100-.md).  
  
-   [Архитектура центра администрирования Active Directory](../../../ad-ds/get-started/adac/Advanced-AD-DS-Management-Using-Active-Directory-Administrative-Center--Level-200-.md#BKMK_Arch)  
  
-   [Активация и Администрирование Active Directory новой корзины через Центр администрирования Active Directory](../../../ad-ds/get-started/adac/Advanced-AD-DS-Management-Using-Active-Directory-Administrative-Center--Level-200-.md#BKMK_EnableRecycleBin)  
  
-   [Настройка и администрирование детальной политики паролей через Центр администрирования Active Directory](../../../ad-ds/get-started/adac/Advanced-AD-DS-Management-Using-Active-Directory-Administrative-Center--Level-200-.md#BKMK_FGPP)  
  
-   [С помощью просмотра журнала PowerShell Windows Центр администрирования Active Directory](../../../ad-ds/get-started/adac/Advanced-AD-DS-Management-Using-Active-Directory-Administrative-Center--Level-200-.md#BKMK_HistoryViewer)  
  
-   [Устранение неполадок управления AD DS](../../../ad-ds/get-started/adac/Advanced-AD-DS-Management-Using-Active-Directory-Administrative-Center--Level-200-.md#BKMK_Tshoot)  
  
## <a name="BKMK_Arch"></a>Архитектура центра администрирования Active Directory  
  
### <a name="adprep-executables-dlls"></a>Исполняемые файлы ADPrep, DLL  
Модуль и базовая архитектура центра администрирования Active Directory с новой корзины, детальной политики ПАРОЛЕЙ и средства просмотра журнала не изменились.  
  
-   Microsoft.ActiveDirectory.Management.UI.dll  
  
-   Microsoft.ActiveDirectory.Management.UI.resources.dll  
  
-   Microsoft.ActiveDirectory.Management.dll  
  
-   Microsoft.ActiveDirectory.Management.resources.dll  
  
-   ActiveDirectoryPowerShellResources.dll  
  
Базовый Windows PowerShell и слой операций для новых функциональных возможностей корзины представлены ниже:  
  
![Настройка управления Дополнительно AD DS](media/Advanced-AD-DS-Management-Using-Active-Directory-Administrative-Center--Level-200-/adds_adrestore.png)  
  
## <a name="BKMK_EnableRecycleBin"></a>Активация и Администрирование Active Directory новой корзины через Центр администрирования Active Directory  
  
### <a name="capabilities"></a>Возможности  
  
-   Центр в Windows Server 2012 Active Directory администратора позволяет настраивать и управлять Корзина Active Directory для любого раздела домена в лесу. Больше не нужно использовать для активации корзины Active Directory или восстановления объектов в разделы доменов Windows PowerShell или Ldp.exe.  
  
-   Центр администрирования Active Directory есть расширенные условия фильтрации, упрощающие адресное восстановление в крупных средах с большим количеством удаленных объектов.  
  
### <a name="limitations"></a>Ограничения  
  
-   Поскольку Центр администрирования Active Directory позволяет управлять только разделами доменов, он не может восстанавливать удаленные объекты из разделов конфигурации, DNS домена или леса DNS-сервера (не может удалять объекты из раздела схемы). Для восстановления объектов из разделов, не входящих в домен, используйте [Restore-ADObject](https://technet.microsoft.com/library/ee617262.aspx).  
  
-   Центр администрирования Active Directory не позволяет восстанавливать поддеревья объектов за одно действие. Например, если вы удалите организационное Подразделение с вложенные подразделения, пользователей, групп и компьютеров, восстановлении этого организационного Подразделения не дочерние объекты восстановлены.  
  
    > [!NOTE]  
    > Центр администрирования Active Directory пакетная операция восстановления включает «наилучший» сортировку удаленных объектов *в пределах сделанной выборки* , родительские объекты предшествуют дочерним в списке восстановления. В простых тестовых случаях поддеревья объектов могут быть восстановлены в рамках одной операции. Но угол случаев, например выборка содержит неполные деревья - которых отсутствуют некоторые из удаленных родительских узлов - или имеются ошибки, например пропуск дочерних объектов при невозможности восстановления родительских не удается, может не работать должным образом. По этой причине следует всегда восстанавливать поддеревья объектов как отдельное действие после восстановления родительских объектов.  
  
Корзина Active Directory требуется Windows Server 2008 R2 режим работы леса, и должен быть членом группы "Администраторы предприятия". После включения корзины Active Directory отключить нельзя. Корзина Active Directory увеличивает размер базы данных Active Directory (NTDS. DIT) на каждом контроллере домена в лесу. Дискового пространства, используемого в корзине продолжает растет со временем она занимает объектов и их данные атрибута.  
  
Дополнительные сведения см. в разделе [Active Directory Пошаговое руководство по использованию корзины](https://technet.microsoft.com/library/dd392261(v=WS.10).aspx) и [оценка аппаратных требований (для корзины Active Directory)](https://technet.microsoft.com/library/cc753439(WS.10).aspx).  
  
Вы можете *ниже* леса и домена режимы работы с Windows Server 2012 для Windows Server 2008 R2 даже после активации корзины Active Directory. Для этого необходимо использовать **Set-ADForestMode** и **Set-ADDomainMode** командлеты Active Directory.  
  
Например:  
  
```  
Set-AdForestMode -identity corp.contoso.com -server dc1.corp.contoso.com -forestmode Windows2008R2Forest  
Set-AdDomainMode -identity research.corp.contoso.com -server dc3.research.corp.contoso.com -domainmode Windows2008R2Domain  
  
```  
  
Центр администрирования Active Directory нельзя использовать для изменения — он позволяет только повысить функциональные уровни.  
  
### <a name="enabling-active-directory-recycle-bin-using-active-directory-administrative-center"></a>Включение Корзина Active Directory через Центр администрирования Active Directory  
Чтобы включить корзину Active Directory, откройте **Центр администрирования Active Directory** и щелкните имя своего леса на панели навигации. Из **задачи** панели, щелкните **включить корзину**.  
  
![Настройка управления Дополнительно AD DS](media/Advanced-AD-DS-Management-Using-Active-Directory-Administrative-Center--Level-200-/ADDS_ADAC_TR_EnableRecycleBin.png)  
  
Центр администрирования Active Directory показывает **подтверждение включения корзины** диалоговое окно. Это диалоговое окно выводится предупреждение, что операция включения корзины необратима. Нажмите кнопку **ОК** для включения корзины Active Directory. Центр администрирования Active Directory отображает другое диалоговое окно напомнить о том, что Корзина Active Directory не будет функционировать полностью, пока все контроллеры домена реплицировать изменения конфигурации.  
  
> [!IMPORTANT]  
> Параметр для включения корзины Active Directory недоступен, если:  
>   
> -   Режим работы леса меньше, чем Windows Server 2008 R2  
> -   Корзина уже включена.  
  
Эквивалентный командлет Windows PowerShell для Active Directory по-прежнему:  
  
```  
Enable-ADOptionalFeature  
```  
  
Дополнительные сведения об использовании Windows PowerShell для включения корзины Active Directory см. в разделе [Active Directory Пошаговое руководство по использованию корзины](https://technet.microsoft.com/library/dd392261(v=WS.10).aspx).  
  
### <a name="managing-active-directory-recycle-bin-using-active-directory-administrative-center"></a>Управление Корзина Active Directory через Центр администрирования Active Directory  
В этом разделе используется пример существующего домена с именем **corp.contoso.com**. Он объединяет пользователей в организационное Подразделение **UserAccounts**. **UserAccounts** Подразделение содержит три подразделения, подразделения, каждое из которых содержит свои подразделения, пользователей и групп.  
  
![Настройка управления Дополнительно AD DS](media/Advanced-AD-DS-Management-Using-Active-Directory-Administrative-Center--Level-200-/ADDS_ADAC_TR_EnableRecycleBinExampleOU.png)  
  
#### <a name="storage-and-filtering"></a>Хранение и фильтрация  
Корзина Active Directory сохраняет все объекты, удаленные в лесу. Она сохраняет объекты хранятся в соответствии **msDS-deletedObjectLifetime** атрибут, который по умолчанию соответствует **tombstoneLifetime** атрибут в лесу. В любом лесу, созданном с помощью Windows Server 2003 SP1 или более поздней версии, значение **tombstoneLifetime** по по умолчанию устанавливается равным 180 дней. В любом лесу, обновленном с Windows 2000 или установленном с помощью Windows Server 2003 (без пакета обновления) атрибут tombstoneLifetime по умолчанию не УСТАНАВЛИВАЕТСЯ, и поэтому Windows использует внутреннее значение по умолчанию 60 дней. Все это можно изменить. Центр администрирования Active Directory можно использовать для восстановления объектов, удаленных из разделов доменов в лесу. Вы должны продолжать использовать командлет **Restore-ADObject** для восстановления удаленных объектов из других разделов, например Configuration.Enabling Корзина Active Directory делает **удаленные объекты** под каждым разделом домена в центре администрирования Active Directory появляется контейнер.  
  
![Настройка управления Дополнительно AD DS](media/Advanced-AD-DS-Management-Using-Active-Directory-Administrative-Center--Level-200-/ADDS_ADAC_TR_DeletedObjectsContainer.png)  
  
**Удаленные объекты** контейнера содержит список всех доступных для восстановления объектов в этом разделе домена. Удаленные объекты старше, чем **msDS-deletedObjectLifetime** называются утилизированными. Центр администрирования Active Directory не показывает утилизированные объекты и не удается восстановить эти объекты, используя Центр администрирования Active Directory.  
  
Более подробно архитектура и принципы в корзине, в разделе [AD корзины: Общие сведения о, реализация, рекомендации и устранение неполадок](http://blogs.technet.com/b/askds/archive/2009/08/27/the-ad-recycle-bin-understanding-implementing-best-practices-and-troubleshooting.aspx).  
  
Центр администрирования Active Directory искусственно ограничивает количество объектов, возвращенных из контейнера до 20 000 штук по умолчанию. Можно увеличить этот предел, 100 000 объектов, откройте **управление** меню, а затем **параметры списка управления**.  
  
![Настройка управления Дополнительно AD DS](media/Advanced-AD-DS-Management-Using-Active-Directory-Administrative-Center--Level-200-/ADDS_ADAC_TR_MgmtList.png)  
  
#### <a name="restoration"></a>Восстановление  
  
##### <a name="filtering"></a>Фильтрация  
Центр администрирования Active Directory предлагает эффективные критерии поиска и параметры фильтрации, которые вам следует знать до того, как их использовать в реальной жизни. Домены специально удаляют множество объектов с их жизненного цикла. Время жизни вероятно, что удаленный объект 180 дней вы просто не сможете восстановить все объекты случае инцидента.  
  
![Настройка управления Дополнительно AD DS](media/Advanced-AD-DS-Management-Using-Active-Directory-Administrative-Center--Level-200-/ADDS_ADAC_TR_AddCriteria.png)  
  
Вместо того чтобы составлять сложные фильтры LDAP и конвертировать значения UTC в даты и времени, использование основных и дополнительных **фильтр** меню, чтобы вывести список соответствующих объектов. Если вы знаете дату удаления, названия объектов или другие ключевые данные, используйте их в качестве фильтра. Для переключения расширенных параметров фильтрации шевроны справа от поля поиска.  
  
Операция восстановления поддерживает все стандартные параметры фильтрации, так же, как любого поиска. Из встроенных фильтров для восстановления объектов обычно используются следующие:  
  
-   *ANR (разрешение неоднозначных имен — не отображается в меню, но используется при вводе в *** фильтр *** поле)*  
  
-   Последнее изменение между заданными датами  
  
-   Объект — пользователь или inetorgperson и компьютер, группа или организационное подразделение  
  
-   Имя  
  
-   При удалении  
  
-   Последний известный родительский объект  
  
-   Тип  
  
-   Описание  
  
-   Город  
  
-   /Region страны  
  
-   Подразделения  
  
-   Код сотрудника  
  
-   Имя  
  
-   Должность  
  
-   Фамилия  
  
-   SAMaccountname  
  
-   Область или край  
  
-   Номер телефона  
  
-   ИМЯ УЧАСТНИКА-ПОЛЬЗОВАТЕЛЯ  
  
-   Почтовый индекс  
  
Можно добавить несколько критериев. Например, можно найти все объекты-пользователи, удаленные 24 сентября<sup>th</sup> 2012 г. в Чикаго, штат Иллинойс, сотрудниками в должности менеджера.  
  
Можно также добавить, изменить или переупорядочить заголовки столбцов, чтобы получить больше данных для оценки объектов к восстановлению.  
  
![Настройка управления Дополнительно AD DS](media/Advanced-AD-DS-Management-Using-Active-Directory-Administrative-Center--Level-200-/ADDS_ADAC_TR_ColumnHeaders.png)  
  
Дополнительные сведения о разрешении неоднозначных имен см. в разделе [атрибуты ANR](https://msdn.microsoft.com/library/ms675092(VS.85).aspx).  
  
##### <a name="single-object"></a>Один объект  
Восстановление удаленных объектов всегда выполнялось одной операции.  Центр администрирования Active Directory упрощает эту операцию. Чтобы восстановить удаленный объект, например отдельного пользователя:  
  
1.  Щелкните имя домена, в области навигации центра администрирования Active Directory.  
  
2.  Дважды щелкните **удаленные объекты** в списке управления.  
  
3.  Щелкните объект правой кнопкой мыши и выберите **восстановить**, или нажмите кнопку **восстановить** из **задачи** области.  
  
Объект вернется в исходное расположение.  
  
![Настройка управления Дополнительно AD DS](media/Advanced-AD-DS-Management-Using-Active-Directory-Administrative-Center--Level-200-/ADDS_ADAC_TR_RestoreSingle.gif)  
  
Нажмите кнопку **восстановить... ** изменить расположение для восстановления. Это полезно в том случае, если родительский контейнер восстанавливаемого объекта также был удален, но восстанавливать его не требуется.  
  
![Настройка управления Дополнительно AD DS](media/Advanced-AD-DS-Management-Using-Active-Directory-Administrative-Center--Level-200-/ADDS_ADAC_TR_RestoreToSingle.gif)  
  
##### <a name="multiple-peer-objects"></a>Несколько аналогичных объектов  
Вы можете восстановить сразу несколько объектов одного уровня, например всех пользователей организационного подразделения. Удерживайте нажатой клавишу CTRL и выберите один или несколько удаленных объектов, которые вы хотите восстановить. Нажмите кнопку **восстановить** на панели задач. Можно также выбрать все указанные объекты, удерживая нажатой клавишу CTRL и клавиши или диапазон объектов, нажав клавишу SHIFT и щелкнув.  
  
![Настройка управления Дополнительно AD DS](media/Advanced-AD-DS-Management-Using-Active-Directory-Administrative-Center--Level-200-/ADDS_ADAC_TR_RestorePeers.png)  
  
##### <a name="multiple-parent-and-child-objects"></a>Несколько дочерних и родительских объектов  
Очень важно понять процесс восстановления для восстановления несколькими parent дочернего, поскольку Центр администрирования Active Directory не удается восстановить вложенные деревья удаленных объектов с помощью одного действия.  
  
1.  Восстановите верхний удаленный объект в дереве.  
  
2.  Восстановите дочерние элементы этого родительского объекта.  
  
3.  Восстановите дочерние элементы этих родительских объектов.  
  
4.  Повторяйте процедуру, пока не будут восстановлены все объекты.  
  
Не удается восстановить дочерний объект, перед восстановлением его родительского объекта. Это восстановление выдаст следующую ошибку:  
  
**Эта операция не выполнена, так как родитель объекта либо не подтвержден, либо удален.**  
  
**Последний известный родительский объект** родительские отношения каждого объекта обозначаются атрибутом. **Последний известный родительский объект** атрибут изменяет из удаленного в восстановленное расположение при обновлении Центр администрирования Active Directory после восстановления родительского объекта. Таким образом можно восстановить дочерний объект, если в расположении родительского объекта больше не указывается различающееся имя контейнера удаленных объектов.  
  
Рассмотрим сценарий, где администратор случайно удалил организационное Подразделение Sales, содержащее дочерние подразделения и пользователей.  
  
Во-первых, определите значение **последний известный родительский объект** атрибутов для всех удаленных пользователей и как она считывает * *OU = Sales\0ADEL:*< guid + контейнера удаленных объектов различающееся имя >***:  
  
![Настройка управления Дополнительно AD DS](media/Advanced-AD-DS-Management-Using-Active-Directory-Administrative-Center--Level-200-/ADDS_ADAC_TR_LastKnownParent.gif)  
  
Отфильтруйте неоднозначное имя Sales. Чтобы вернуть список удаленных Подразделений, которые затем восстановить:  
  
![Настройка управления Дополнительно AD DS](media/Advanced-AD-DS-Management-Using-Active-Directory-Administrative-Center--Level-200-/ADDS_ADAC_TR_LastKnownParentSales.png)  
  
Обновите Центр администрирования Active Directory атрибут последний известный родительский объект удаленного пользователя изменится различающееся имя восстановленного организационного Подразделения Sales.  
  
![Настройка управления Дополнительно AD DS](media/Advanced-AD-DS-Management-Using-Active-Directory-Administrative-Center--Level-200-/ADDS_ADAC_TR_LastKnownParentSalesRestored.gif)  
  
Отфильтруйте всех пользователей подразделения Sales. Нажмите комбинацию клавиш CTRL + чтобы выбрать всех удаленных пользователей подразделения Sales. Нажмите кнопку **восстановить** для перемещения объектов из **удаленные объекты** контейнера подразделение Sales с теми же атрибутами и членства в группах.  
  
![Настройка управления Дополнительно AD DS](media/Advanced-AD-DS-Management-Using-Active-Directory-Administrative-Center--Level-200-/ADDS_ADAC_TR_LastKnownParentSalesUndelete.png)  
  
Если **продажи** Подразделение включало дочерние подразделения собственный, а затем вы бы восстановите дочерние подразделения сначала их дочерние элементы и т. д.  
  
Порядок восстановления всех вложенных удаленных объектов путем указания удаленного родительского контейнера см [приложение б. Восстановление сразу нескольких, удалить объекты Active Directory (образец сценария)](https://technet.microsoft.com/library/dd379504(WS.10).aspx).  
  
Командлет Windows PowerShell для Active Directory для восстановления удаленных объектов —:  
  
```  
Restore-adobject  
  
```  
  
**Restore-ADObject** функции командлет не изменил между Windows Server 2008 R2 и Windows Server 2012.  
  
##### <a name="server-side-filtering"></a>Фильтрация на стороне сервера  
Это возможно, что со временем удаленные объекты контейнера могут накапливаться объектов до 20 000 (и даже 100 000) в средних и крупных организациях и возникнут сложности с отображением всех объектов. Поскольку механизм фильтрации в центре администрирования Active Directory использует фильтрацию на стороне клиента, он не может отображать объекты сверх. Чтобы обойти это ограничение, используйте следующие действия для выполнения поиска со стороны сервера:  
  
1.  Щелкните правой кнопкой мыши **удаленные объекты** контейнера и нажмите кнопку **искать в этом узле**.  
  
2.  Щелкните шеврон, чтобы открыть **+ добавить условие** меню, выберите и добавьте **последнее изменение между заданными датами**. Время последнего изменения ( **whenChanged** атрибут) будет приближено к времени удаления; в большинстве сред эти значения будут идентичны. Этот запрос запускает поиск на стороне сервера.  
  
3.  Найдите удаленные объекты для восстановления с помощью дополнительной фильтрации, сортировки и т. д в результатах и затем восстановите объекты как обычно.  
  
## <a name="BKMK_FGPP"></a>Настройка и администрирование детальной политики паролей через Центр администрирования Active Directory  
  
### <a name="configuring-fine-grained-password-policies"></a>Настройка детальной политики паролей  
Центр администрирования Active Directory позволяет создавать объекты и управлять ими пароль политики Детальная. Windows Server 2008 появилась функция FGPP была, но Windows Server 2012 первый интерфейс управления с графическим интерфейсом для. Применить детально настроенные политики паролей на уровне домена и позволяет перезаписывать единый пароль домена предусмотренный в Windows Server 2003. При создании различных FGPP с различными настройками, отдельные пользователи или группы получают различные политики паролей в домене.  
  
Сведения о детальной политике паролей см. в разделе [AD DS детально регулируемых паролей и пошаговое руководство по политике (Windows Server 2008 R2) учетной записи блокировки](https://technet.microsoft.com/library/cc770842(WS.10).aspx).  
  
В области навигации выберите представление в виде дерева, щелкните свой домен, щелкните **системы**, нажмите кнопку **контейнер параметров пароля**и в области задач щелкните **New** и **параметры пароля**.  
  
![Настройка управления Дополнительно AD DS](media/Advanced-AD-DS-Management-Using-Active-Directory-Administrative-Center--Level-200-/ADDS_ADAC_TR_PasswordSettings.png)  
  
### <a name="managing-fine-grained-password-policies"></a>Управление детальной политикой паролей  
Создание новой политики ПАРОЛЕЙ или редактировании уже существующей детальной открывается **параметры пароля** редактора. Здесь можно настроить все желаемые политики паролей, как в Windows Server 2008 или Windows Server 2008 R2, но только теперь в специальном редакторе.  
  
![Настройка управления Дополнительно AD DS](media/Advanced-AD-DS-Management-Using-Active-Directory-Administrative-Center--Level-200-/ADDS_ADAC_TR_CreatePasswordSettings.png)  
  
Заполните все обязательные (отмеченные звездочкой) и желаемые дополнительные поля и нажмите кнопку **добавить** для установки пользователям или группам необходимо применить эту политику. FGPP перезаписывает параметры политики домена по умолчанию для выбранных субъектов безопасности. В представленном выше рисунке максимально ограничивающая политика применяется только к встроенной учетной записи администратора, чтобы предотвратить компрометацию. Эта политика слишком сложна для обычных пользователей в соответствии с но идеально подходит для риска учетной записи, используемые ИТ-специалистов.  
  
Также необходимо указать очередность применения и выбрать пользователей и групп в данном домене для применения политики.  
  
![Настройка управления Дополнительно AD DS](media/Advanced-AD-DS-Management-Using-Active-Directory-Administrative-Center--Level-200-/ADDS_ADAC_TR_Precedence.png)  
  
Ниже приведены командлеты Windows PowerShell для Active Directory для настройки детальной политики паролей.  
  
```  
Add-ADFineGrainedPasswordPolicySubject  
Get-ADFineGrainedPasswordPolicy  
Get-ADFineGrainedPasswordPolicySubject  
New-ADFineGrainedPasswordPolicy  
Remove-ADFineGrainedPasswordPolicy  
Remove-ADFineGrainedPasswordPolicySubject  
Set-ADFineGrainedPasswordPolicy  
  
```  
  
Детальной политики паролей командлет не изменил между Windows Server 2008 R2 и Windows Server 2012. Для удобства схеме ниже обозначены соответствующие атрибуты для командлетов:  
  
![Настройка управления Дополнительно AD DS](media/Advanced-AD-DS-Management-Using-Active-Directory-Administrative-Center--Level-200-/ADDS_ADAC_TR_FGPP.gif)  
  
Центр администрирования Active Directory позволяет также найти результирующую примененную для конкретного пользователя. Щелкните правой кнопкой мыши любой пользователь и нажмите кнопку **просмотреть итоговые параметры пароля... ** открыть *параметры пароля* , назначенными пользователю напрямую или косвенно:  
  
![Настройка управления Дополнительно AD DS](media/Advanced-AD-DS-Management-Using-Active-Directory-Administrative-Center--Level-200-/ADDS_ADAC_TR_RSOP.png)  
  
Проверки **свойства** любой пользователь или группа показывает **напрямую связанные параметры пароля**, которые являются явно назначенные соответствующему:  
  
![Настройка управления Дополнительно AD DS](media/Advanced-AD-DS-Management-Using-Active-Directory-Administrative-Center--Level-200-/ADDS_ADAC_TR_FGPPSettings.gif)  
  
Неявные детальной политики ПАРОЛЕЙ не здесь на отображаются; для этого необходимо использовать **просмотреть итоговые параметры пароля... ** параметр.  
  
## <a name="BKMK_HistoryViewer"></a>С помощью просмотра журнала PowerShell Windows Центр администрирования Active Directory  
Будущее управления Windows связано с Windows PowerShell. Благодаря размещению графических средств поверх платформы автоматизации задач Управление сложнейшими распределенными системами стало последовательным и эффективным. Необходимо понять, как работает Windows PowerShell для вашей потенциал и извлечь максимальную пользу вашей инвестиций в компьютерное оборудование.  
  
Центр администрирования Active Directory теперь позволяет просматривать историю выполнения всех командлетов Windows PowerShell, включая и их аргументы и значения. Можно скопировать для дальнейшего изучения или изменения и повторного использования при этом историю командлетов. Можно создавать примечания к задачам и описывать какие ваш Центр администрирования Active Directory дали команды в Windows PowerShell. Также можно фильтровать историю на предмет интересных моментов.  
  
Active Directory администратора центра просмотра журнала Windows PowerShell предназначен для вас на основе практического опыта.  
  
![Настройка управления Дополнительно AD DS](media/Advanced-AD-DS-Management-Using-Active-Directory-Administrative-Center--Level-200-/ADDS_ADAC_TR_HistoryViewer.gif)  
  
Щелкните шеврон (стрелку), чтобы открыть средство просмотра журнала Windows PowerShell.  
  
![Настройка управления Дополнительно AD DS](media/Advanced-AD-DS-Management-Using-Active-Directory-Administrative-Center--Level-200-/ADDS_ADAC_TR_RaiseViewer.png)  
  
Затем создайте пользователя или измените членство в группе. Средство просмотра журнала постоянно обновляется — в нем появляется свернутое представление каждого командлета, выполненного центром администрирования Active Directory указываются его аргументы.  
  
Разверните любую строку интерес, чтобы увидеть значения всех аргументов командлета:  
  
![Настройка управления Дополнительно AD DS](media/Advanced-AD-DS-Management-Using-Active-Directory-Administrative-Center--Level-200-/ADDS_ADAC_TR_ViewArgs.png)  
  
Нажмите кнопку **запустить задачу** меню, чтобы создать заметку, прежде чем использовать Центр администрирования Active Directory для создания, изменения или удаления объекта. Введите свои действия.  Закончив внесение изменений, выберите **Снять задачу**. Заметке к задаче, все эти действия выполнены в виде свернутого примечания, которые можно использовать для лучшего понимания.  
  
Например, чтобы увидеть команды Windows PowerShell, используемые для изменения пароля пользователя и удаления пользователя из группы:  
  
![Настройка управления Дополнительно AD DS](media/Advanced-AD-DS-Management-Using-Active-Directory-Administrative-Center--Level-200-/ADDS_ADAC_TR_RemoveUser.gif)  
  
Флажок "Показать все" также показано, Get-* глагол командлеты Windows PowerShell, только для извлечения данных.  
  
![Настройка управления Дополнительно AD DS](media/Advanced-AD-DS-Management-Using-Active-Directory-Administrative-Center--Level-200-/ADDS_ADAC_TR_ShowAll.png)  
  
Средство просмотра журнала отображаются тексты всех команд, выполненных центром администрирования Active Directory и может показаться, что некоторые команды выполняются без причины. Например можно создать нового пользователя с:  
  
```  
new-aduser   
```  
  
и не требуется использовать.  
  
```  
set-adaccountpassword  
enable-adaccount  
set-aduser  
  
```  
  
Структура Центр администрирования Active Directory предусматривает минимальное использование кодов и модулей. Таким образом вместо набор функций для создания новых пользователей и другой набор изменения уже существующих он выполняет каждую задачу по минимуму и затем соединяет их воедино с помощью командлетов. Это помнить при изучении модуля Active Directory в Windows PowerShell. Вы можете также использовать как способ изучения, где вы видите, насколько просто можно использовать Windows PowerShell для выполнения одной задачи.  
  
## <a name="BKMK_Tshoot"></a>Устранение неполадок управления AD DS  
  
### <a name="introduction-to-troubleshooting"></a>Общие сведения об устранении неполадок  
Ввиду относительной новизны и небольшого опыта применения в реальных условиях Центр администрирования Active Directory ограниченны варианты устранения неполадок.  
  
### <a name="troubleshooting-options"></a>Способы устранения неполадок  
  
#### <a name="logging-options"></a>Параметры ведения журнала  
Центр администрирования Active Directory теперь включает встроенный журнал в Windows Server 2012, как часть конфигурации файла трассировки. Создайте или измените следующий файл в той же папке dsac.exe:  
  
**dsac.exe.config**  
  
Создайте следующее содержимое:  
  
```  
<appSettings>  
  <add key="DsacLogLevel" value="Verbose" />  
</appSettings>  
<system.diagnostics>   
 <trace autoflush="false" indentsize="4">   
  <listeners>   
   <add name="myListener"   
    type="System.Diagnostics.TextWriterTraceListener"   
    initializeData="dsac.trace.log" />   
   <remove name="Default" />   
  </listeners>   
 </trace>   
</system.diagnostics>  
  
```  
  
Уровни детализации для **DsacLogLevel** , **нет**, **ошибка**, **предупреждение**, **сведения**, и **Verbose**. Имя выходного файла можно настроить и записывает их в той же папке dsac.exe. Выходные данные можно узнать, вы больше о том, как работает adac, какими контроллерами доменов устанавливается связь, что делают команды Windows PowerShell, какие ответы были получены и Дополнительные сведения.  
  
Например при использовании уровня сведения, который возвращает все результаты, кроме детализации уровень трассировки:  
  
-   Запускает DSAC.exe  
  
-   Начинается ведение журнала.  
  
-   Запрашиваются исходные данные домена контроллера домена  
  
    ```  
    [12:42:49][TID 3][Info] Command Id, Action, Command, Time, Elapsed Time ms (output), Number objects (output)  
    [12:42:49][TID 3][Info] 1, Invoke, Get-ADDomainController, 2012-04-16T12:42:49  
    [12:42:49][TID 3][Info] Get-ADDomainController-Discover:$null-DomainName:"CORP"-ForceDiscover:$null-Service:ADWS-Writable:$null  
    ```  
  
-   Контроллер домена DC1 возвращается из домена Corp  
  
-   PS Загружается виртуальный диск AD  
  
    ```  
    [12:42:49][TID 3][Info] 1, Output, Get-ADDomainController, 2012-04-16T12:42:49, 1  
    [12:42:49][TID 3][Info] Found the domain controller 'DC1' in the domain 'CORP'.  
    [12:42:49][TID 3][Info] 2, Invoke, New-PSDrive, 2012-04-16T12:42:49  
    [12:42:49][TID 3][Info] New-PSDrive-Name:"ADDrive0"-PSProvider:"ActiveDirectory"-Root:""-Server:"dc1.corp.contoso.com"  
    [12:42:49][TID 3][Info] 2, Output, New-PSDrive, 2012-04-16T12:42:49, 1  
    [12:42:49][TID 3][Info] 3, Invoke, Get-ADRootDSE, 2012-04-16T12:42:49  
  
    ```  
  
-   Извлекаются данные домена Root DSE.  
  
    ```  
    [12:42:49][TID 3][Info] Get-ADRootDSE  
    -Server:"dc1.corp.contoso.com"  
    [12:42:49][TID 3][Info] 3, Output, Get-ADRootDSE, 2012-04-16T12:42:49, 1  
    [12:42:49][TID 3][Info] 4, Invoke, Get-ADOptionalFeature, 2012-04-16T12:42:49  
  
    ```  
  
-   Извлекаются данные корзины домену AD  
  
    ```  
    [12:42:49][TID 3][Info] Get-ADOptionalFeature  
    -LDAPFilter:"(msDS-OptionalFeatureFlags=1)"  
    -Server:"dc1.corp.contoso.com"  
    [12:42:49][TID 3][Info] 4, Output, Get-ADOptionalFeature, 2012-04-16T12:42:49, 1  
    [12:42:49][TID 3][Info] 5, Invoke, Get-ADRootDSE, 2012-04-16T12:42:49  
    [12:42:49][TID 3][Info] Get-ADRootDSE  
    -Server:"dc1.corp.contoso.com"  
    [12:42:49][TID 3][Info] 5, Output, Get-ADRootDSE, 2012-04-16T12:42:49, 1  
    [12:42:49][TID 3][Info] 6, Invoke, Get-ADRootDSE, 2012-04-16T12:42:49  
    [12:42:49][TID 3][Info] Get-ADRootDSE  
    -Server:"dc1.corp.contoso.com"  
    [12:42:49][TID 3][Info] 6, Output, Get-ADRootDSE, 2012-04-16T12:42:49, 1  
    [12:42:49][TID 3][Info] 7, Invoke, Get-ADOptionalFeature, 2012-04-16T12:42:49  
    [12:42:49][TID 3][Info] Get-ADOptionalFeature  
    -LDAPFilter:"(msDS-OptionalFeatureFlags=1)"  
    -Server:"dc1.corp.contoso.com"  
    [12:42:50][TID 3][Info] 7, Output, Get-ADOptionalFeature, 2012-04-16T12:42:50, 1  
    [12:42:50][TID 3][Info] 8, Invoke, Get-ADForest, 2012-04-16T12:42:50  
  
    ```  
  
-   Извлекается лес AD  
  
    ```  
    [12:42:50][TID 3][Info] Get-ADForest  
    -Identity:"corp.contoso.com"  
    -Server:"dc1.corp.contoso.com"  
    [12:42:50][TID 3][Info] 8, Output, Get-ADForest, 2012-04-16T12:42:50, 1  
    [12:42:50][TID 3][Info] 9, Invoke, Get-ADObject, 2012-04-16T12:42:50  
  
    ```  
  
-   Извлекаются данные схемы по поддерживаемым типам шифрования, детальная политика ПАРОЛЕЙ, данные определенных пользователей.  
  
    ```  
    [12:42:50][TID 3][Info] Get-ADObject  
    -LDAPFilter:"(|(ldapdisplayname=msDS-PhoneticDisplayName)(ldapdisplayname=msDS-PhoneticCompanyName)(ldapdisplayname=msDS-PhoneticDepartment)(ldapdisplayname=msDS-PhoneticFirstName)(ldapdisplayname=msDS-PhoneticLastName)(ldapdisplayname=msDS-SupportedEncryptionTypes)(ldapdisplayname=msDS-PasswordSettingsPrecedence))"  
    -Properties:lDAPDisplayName  
    -ResultPageSize:"100"  
    -ResultSetSize:$null  
    -SearchBase:"CN=Schema,CN=Configuration,DC=corp,DC=contoso,DC=com"  
    -SearchScope:"OneLevel"  
    -Server:"dc1.corp.contoso.com"  
    [12:42:50][TID 3][Info] 9, Output, Get-ADObject, 2012-04-16T12:42:50, 7  
    [12:42:50][TID 3][Info] 10, Invoke, Get-ADObject, 2012-04-16T12:42:50  
  
    ```  
  
-   Извлекается вся информация об объекте домена, которая будет показываться администратору при выборе заголовка домена.  
  
    ```  
    [12:42:50][TID 3][Info] Get-ADObject  
    -IncludeDeletedObjects:$false  
    -LDAPFilter:"(objectClass=*)"  
    -Properties:allowedChildClassesEffective,allowedChildClasses,lastKnownParent,sAMAccountType,systemFlags,userAccountControl,displayName,description,whenChanged,location,managedBy,memberOf,primaryGroupID,objectSid,msDS-User-Account-Control-Computed,sAMAccountName,lastLogonTimestamp,lastLogoff,mail,accountExpires,msDS-PhoneticCompanyName,msDS-PhoneticDepartment,msDS-PhoneticDisplayName,msDS-PhoneticFirstName,msDS-PhoneticLastName,pwdLastSet,operatingSystem,operatingSystemServicePack,operatingSystemVersion,telephoneNumber,physicalDeliveryOfficeName,department,company,manager,dNSHostName,groupType,c,l,employeeID,givenName,sn,title,st,postalCode,managedBy,userPrincipalName,isDeleted,msDS-PasswordSettingsPrecedence  
    -ResultPageSize:"100"  
    -ResultSetSize:"20201"  
    -SearchBase:"DC=corp,DC=contoso,DC=com"  
    -SearchScope:"Base"  
    -Server:"dc1.corp.contoso.com"  
  
    ```  
  
Выбранный уровень Verbose стеки .NET для каждой функции, но они не включают достаточно данные могут пригодиться только при устранении неполадок Dsac.exe связанных с нарушением прав доступа или аварийным сбоем.  
  
> [!IMPORTANT]  
> Существует также версия аппаратного службы с именем [Active Directory Management Gateway](https://www.microsoft.com/download/en/details.aspx?displaylang=en&id=2852), который выполняется в Windows Server 2008 с SP2 и Windows Server 2003 SP2.  
  
Две возможные причины этой проблемы являются:  
  
-   ВЕБ-служба не запущена на любой из запрашиваемых контроллеров доменов.  
  
-   Сетевые коммуникации блокируются для веб-службы в компьютере, где запущен центр администрирования Active Directory  
  
Ниже приведены ошибки, доступных экземпляры веб-служб Active Directory, не отображаются.  
  
|||  
|-|-|  
|Ошибка|Операция|  
|«Не удается подключиться к домену. Обновите состояние или попробуйте еще раз, когда подключение станет доступным»|Отображается при запуске приложения, Центр администрирования Active Directory|  
|«Не удается найти доступный сервер в * <NetBIOS domain name> * домена, на котором выполняется служба веб-Active Directory (ADWS)»|Отображается при попытке выбора узла домена в приложении Центр администрирования Active Directory|  
  
Чтобы устранить эту проблему, выполните следующие действия.  
  
1.  Проверка Active Directory веб-службы, служба запущена хотя бы один контроллер домена в домене (а лучше все контроллеры домена в лесу). Убедитесь, что настроен автоматический запуск на всех контроллерах домена также.  
  
2.  Компьютере, где запущен центр администрирования Active Directory проверьте, что можно найти на сервере веб-служба, выполнив команды NLTest.exe:  
  
    ```  
    nltest /dsgetdc:<domain NetBIOS name> /ws /force   
    nltest /dsgetdc:<domain fully qualified DNS name> /ws /force  
  
    ```  
  
    Если связь не устанавливается несмотря на то, что веб-служба работает, проблема связана с разрешением имен или LDAP и не Центр администрирования Active Directory. Эта проверка завершается ошибкой «1355 0x54B ERROR_NO_SUCH_DOMAIN» Если хотя веб-служба не работает на всех контроллерах домена, поэтому тщательно проверьте до достижения любой выводы.  
  
3.  На контроллере домена, выданный командой NLTest введите дамп списка портов прослушивания с помощью команды:  
  
    ```  
    Netstat -anob > ports.txt  
  
    ```  
  
    Изучите файл ports.txt и убедитесь, что веб-служба прослушивает порт 9389. Пример:  
  
    ```  
    TCP    0.0.0.0:9389    0.0.0.0:0    LISTENING    1828  
    [Microsoft.ActiveDirectory.WebServices.exe]  
  
    TCP    [::]:9389       [::]:0       LISTENING    1828  
    [Microsoft.ActiveDirectory.WebServices.exe]  
  
    ```  
  
    Если порт прослушивается, проверьте правила брандмауэра Windows и убедитесь, что они позволяют TCP-порту 9389 входящего трафика. По умолчанию контроллеры доменов включают правило брандмауэра «Active Directory веб-службы (TCP-входящий)». Если порт не прослушивается, еще раз проверьте, что служба запущена на этом сервере и перезапустите его. Убедитесь, что недоступны для других процессов уже прослушивает порт 9389.  
  
4.  Установите NetMon или другую утилиту для записи сети на компьютере под управлением Центр администрирования Active Directory и на контроллере домена, выданный командой NLTEST. Запустите запись сетевых данных на обоих компьютерах, где запущен центр администрирования Active Directory, посмотрите ошибки и остановите запись. Проверьте, что клиент способен отправлять и принимать данные с контроллера домена через порт TCP 9389. Если пакеты отправляются, но не поступают или поступают, а ответы контроллера домена, но они не достигают клиента, вполне вероятно, что существует брандмауэр между компьютерами в сети, который теряет пакеты в этом порту. Брандмауэр может быть программным или аппаратным и может быть частью третьих лиц (антивирус) программного обеспечения endpoint protection.  
  
#### <a name="knownlikely-issues-and-support-scenarios"></a>Известные/возможные неполадки и сценарии поддержки  
Единственная возможная проблема с центром администрирования Active Directory — это невозможность подключения к Active Directory веб-службы (ADWS) запущен на контроллере домена Windows Server 2012 или Windows Server 2008 R2.  
  
## <a name="see-also"></a>См. также:  
[Введение в дополнительные возможности центра администрирования Active Directory & #40; Уровень 100 & #41;](../../../ad-ds/get-started/adac/Introduction-to-Active-Directory-Administrative-Center-Enhancements--Level-100-.md)  
  

