---
ms.assetid: f74eec9a-2485-4ee0-a0d8-cce01250a294
title: "Упрощенное администрирование Доменных"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 6232e281c47f3b5b4627bc9d8ccf53269aafc390
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="ad-ds-simplified-administration"></a>Упрощенное администрирование Доменных

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

В этом разделе описываются новые возможности и преимущества развертывания контроллера домена Windows Server 2012 и администрирования и различия между предыдущего развертывания операционной системы контроллера домена и новая реализация Windows Server 2012.  
  
Windows Server 2012 представляет новое поколение Active Directory упрощенное администрирование доменных служб и является наиболее радикальную модернизацию системы управления доменами с момента выпуска Windows 2000 Server. Упрощенном администрировании AD DS принимает выводов из двенадцатилетнего Active Directory и предоставляет более простую в обслуживании более гибкими и интуитивно понятной административных возможностей для архитекторов и администраторов. Это означало, создания новых версий существующих технологий, а также для расширения возможностей компонентов, появившихся в Windows Server 2008 R2.  
  
Упрощенном администрировании AD DS представляет новый подход к развертыванию доменов.  
  
-   Развертывание роли AD DS теперь является частью архитектуры диспетчера сервера и допускает удаленную установку.  
  
-   Модуль развертывания и настройки AD DS теперь основан на Windows PowerShell, даже при использовании нового мастера настройки AD DS  
  
-   Расширение схемы, подготовка леса и домена производятся автоматически в ходе повышения роли контроллера домена и больше не требуют выполнения отдельных задач на специальных серверах, таких как хозяин схемы  
  
-   При повышении роли теперь проводится проверка предварительных требований которой подтверждается готовность леса и домена для нового контроллера домена, что снижает вероятность сбоев  
  
-   Модуль Active Directory для Windows PowerShell теперь включает командлеты для управления топологией репликации, динамического контроля доступа и других операций  
  
-   Режим работы, уровень новые функции не реализуются, а режим работы домена необходим только для подмножества новых функций Kerberos, что упрощает администраторов леса Windows Server 2012 требуется для среде с контроллером домена, чтобы осуществить однородное  
  
-   Для виртуализированных контроллеров домена, чтобы включить автоматическое развертывание и защиту от отката добавлена полная поддержка  
  
Дополнительные сведения о виртуализированных контроллерах домена см. в разделе [введение в доменных службах Active Directory & #40; AD DS & #41; Виртуализация & #40; Уровень 100 & #41;](../../ad-ds/Introduction-to-Active-Directory-Domain-Services-AD-DS-Virtualization-Level-100.md).  
  
Кроме того, существует множество административных и улучшения обслуживания:  
  
-   Центр администрирования Active Directory включает графический Корзина Active Directory, управление детальной политикой паролей и средство просмотра журнала Windows PowerShell  
  
-   Новый диспетчер сервера имеет интерфейсов зависящие от AD DS в наблюдение за производительностью, наиболее анализ выполнения рекомендаций, критически важные службы и журналы событий  
  
-   Групповые управляемые учетные записи служб поддерживают несколько компьютеров, используя те же субъекты безопасности  
  
-   Улучшения в относительных идентификаторов (RID) выдача и мониторинг для более эффективного управления существующими доменами Active Directory  
  
Наконец в Доменных службах Active Directory используются другие новые функции, включенные в Windows Server 2012, таких как:  
  
-   Объединение сетевых КАРТ и мост для центра обработки данных  
  
-   Безопасность DNS и более быстрая доступность зон, интегрированных с AD, после загрузки  
  
-   Улучшенная надежность и масштабируемость Hyper-V  
  
-   Сетевой разблокировки BitLocker  
  
-   Дополнительные модули администрирования компонентов Windows PowerShell  
  
## <a name="technical-overview"></a>Технический обзор  
  
### <a name="adprep-integration"></a>Интеграция ADPREP  
Active Directory леса схемы расширение и подготовка домена теперь интегрировать в процесс настройки контроллера домена. При повышении роли нового контроллера домена в существующем лесу, процесс определяет состояние обновления и этапы расширения схемы и домена подготовки происходят автоматически. Пользователь, устанавливающий первый контроллер домена Windows Server 2012 по-прежнему должен быть администраторов предприятия и администраторов схемы или предоставить альтернативные действительные учетные данные.  
  
Adprep.exe остается на DVD-диске для подготовки отдельных лесов и доменов. Версия средства, включенная в Windows Server 2012 имеет обратную совместимость с Windows Server 2008 x64 и Windows Server 2008 R2. Adprep.exe также поддерживает удаленные команды forestprep и domainprep, так же как средства настройки контроллера домена на основе ADDSDeployment.  
  
Сведения о средстве Adprep и подготовке леса в предыдущих операционной системы см. в разделе [работа с программой Adprep.exe (Windows Server 2008 R2)](https://technet.microsoft.com/library/dd464018(WS.10).aspx).  
  
### <a name="server-manager-ad-ds-integration"></a>Интеграция диспетчера сервера и доменных служб Active Directory  
![упрощенное администрирование](media/AD-DS-Simplified-Administration/ADDS_SMI_TR_Dashboard.png)  
  
Диспетчер сервера выступает в качестве единой консоли для выполнения задач управления сервером. Его информационной панели периодически обновляются представления с установленными ролями и группами удаленных серверов. Диспетчер сервера обеспечивает централизованное управление локальными и удаленными серверами без необходимости доступа к консоли.  
  
Доменные службы Active Directory — это один из этих ролей; запустив диспетчер сервера на контроллере домена или средства удаленного администрирования сервера для Windows 8, появится важные события, произошедшие на контроллерах домена в лесу.  
  
Эти представления включают в себя:  
  
-   Доступность сервера  
  
-   Монитор производительности с предупреждениями о высокой ЦП и памяти  
  
-   Состояние служб Windows, относящихся к AD DS  
  
-   Последние связанные со службами каталогов предупреждения и ошибки записи в журнале событий  
  
-   Анализ выполнения рекомендаций для контроллера домена, проводимый на основе набора правил Майкрософт  
  
### <a name="active-directory-administrative-center-recycle-bin"></a>Корзина в центре администрирования Active Directory  
![упрощенное администрирование](media/AD-DS-Simplified-Administration/ADDS_SMI_TR_ADAC.png)  
  
Windows Server 2008 R2 появилась Корзина Active Directory включена, которая позволяет восстанавливать удаленные объекты Active Directory без восстановления из резервной копии, перезапуска служб AD DS или перезагрузки контроллеров домена.  
  
Windows Server 2012 расширяет существующие возможности восстановления на основе Windows PowerShell с новому графическому интерфейсу в центре администрирования Active Directory. Это позволяет администраторам включить корзину и затем найти или восстановить удаленные объекты в контексте доменов леса, все это без непосредственного использования командлетов Windows PowerShell. Центр администрирования Active Directory и Корзина Active Directory по-прежнему использовать Windows PowerShell, за кулисами, поэтому предыдущие сценарии и процедуры можно с успехом применять.  
  
Сведения о службе каталогов Active Directory [Корзина см. в разделе Корзина Active Directory Step-by-Step руководство (Windows Server 2008 R2)](https://technet.microsoft.com/library/dd392261(WS.10).aspx).  
  
### <a name="active-directory-administrative-center-fine-grained-password-policy"></a>Политика сложных паролей в центре администрирования Active Directory  
![упрощенное администрирование](media/AD-DS-Simplified-Administration/ADDS_SMI_TR_FGPP.png)  
  
Windows Server 2008 появилась детальная политика паролей, которая позволяет администраторам настроить несколько паролей и политики блокирования учетных каждого домена. Это позволяет домены решение позволило гибко управлять более или менее строгими правилами паролей на основе пользователей и групп. Он у не было отдельного интерфейса и администраторам приходилось настраивать его с помощью Ldp.exe или Adsiedit.msc. Windows Server 2008 R2 появился модуль Active Directory для Windows PowerShell, который позволил администраторам использовать интерфейс командной строки для управления детальной политикой ПАРОЛЕЙ.  
  
Windows Server 2012 реализован графический интерфейс для настройки детальной политики паролей. Центр администрирования Active Directory теперь является это новое диалоговое окно, который объединяет упрощенного управления детальной политикой ПАРОЛЕЙ для всех администраторов.  
  
Сведения о детальной политике паролей см. в разделе [AD DS детально регулируемых паролей и пошаговое руководство по политике (Windows Server 2008 R2) учетной записи блокировки](https://technet.microsoft.com/library/cc770842(WS.10).aspx).  
  
### <a name="active-directory-administrative-center-windows-powershell-history-viewer"></a>Средство просмотра журнала PowerShell Windows Центр администрирования Active Directory  
![упрощенное администрирование](media/AD-DS-Simplified-Administration/ADDS_SMI_TR_HistoryViewer.png)  
  
Windows Server 2008 R2 появился центр администрирования Active Directory, который заменяемых старых Active Directory — пользователи и компьютеры оснастки времен Windows 2000. Центр администрирования Active Directory предоставляет графический интерфейс для этого нового модуля Active Directory для Windows PowerShell.  
  
Так как модуль Active Directory содержит более ста командлетов, где администратор может легко запутаться. Поскольку Windows PowerShell тесно интегрирована в стратегию администрирования ОС Windows, Центр администрирования Active Directory теперь включает средства просмотра, которое позволяет наблюдать за выполнением командлетов в графическом интерфейсе. Можно искать, копировать, очистить журнал и добавлять заметки в простом интерфейсе. Цель состоит в том, где администратор может использовать графический интерфейс для создания и изменения объектов, а затем просматривать их в средстве просмотра журнала для получения дополнительных сведений об использовании сценариев Windows PowerShell и изменения примеры.  
  
### <a name="ad-replication-windows-powershell"></a>Windows PowerShell для репликации AD  
![упрощенное администрирование](media/AD-DS-Simplified-Administration/ADDS_PSNewADReplSite.png)  
  
Windows Server 2012 добавлены дополнительные командлеты репликации Active Directory в модуль Active Directory в Windows PowerShell. Они позволяют настраивать новые и существующие сайты, подсети, подключения, связи сайтов и мосты. Они также возвращают Active Directory метаданные репликации, состояние репликации, очереди и векторе синхронизации версий векторную информацию. Введение командлеты репликации в сочетании с другими командлетами AD DS - и развертывания позволяет администрировать весь лес, используя только Windows PowerShell. Это дает новые возможности администраторам, желающим предоставлять ресурсы и управлять Windows Server 2012 без использования графического интерфейса, что сокращает уязвимость операционной системы к атакам и требования к обслуживанию. Это особенно важно, если серверы необходимо развернуть в сетях высокого уровня безопасности, таких как маршрутизатор протокола Интернета секрет (SIPR) и корпоративные сети периметра.  
  
Дополнительные сведения о топологии сайта в Доменных службах Active Directory и репликации см. в разделе [Технический справочник по Windows Server](https://technet.microsoft.com/library/cc739127(WS.10).aspx).  
  
### <a name="rid-management-and-issuance-improvements"></a>Идентификаторов RID и управления улучшения выдачи  
Windows 2000 Active Directory появился хозяин RID, который выдавал пулы относительных идентификаторов контроллерам домена, чтобы создавать идентификаторы безопасности (SID) для субъектов безопасности, таких как пользователи, группы и компьютеры.  По умолчанию глобальное пространство RID ограничено 2<sup>30</sup> (или 1 073 741 823) можно создать общее идентификаторы безопасности в домене. Идентификаторы безопасности нельзя вернуть в пул или повторного выпуска. Со временем большом домене может привести к нехватке идентификаторов RID либо результате различных происшествий может привести к ненужные истощение RID и последующего нехватки.  
  
Windows Server 2012 решен ряд RID выдачу и управление ими проблемы, обнаруженные клиентов и поддержки пользователей Майкрософт в AD DS, когда были с момента создания первые домены Active Directory в 1999 г. К ним относятся:  
  
-   Периодические предупреждения об использовании идентификаторов RID записываются в журнал событий  
  
-   События входа, когда администратор делает недействительным пул относительных ИДЕНТИФИКАТОРОВ  
  
-   Максимальное ограничение на размер блока RID теперь устанавливается принудительно в политике RID  
  
-   Искусственный RID истощается теперь применяется принудительно и войти в систему при низком уровне, что позволяет администратору предпринять необходимые действия до исчерпания глобального пространства глобального пространства RID  
  
-   Глобальное пространство RID, теперь можно увеличить на один бит, размер в 2 раза больше<sup>31</sup> (2 147 483 648 идентификаторов безопасности)  
  
Дополнительные сведения об идентификаторах RID и хозяине RID [принципы работы идентификаторов безопасности](https://technet.microsoft.com/library/cc778824(WS.10).aspx).  
  
## <a name="new-ad-ds-deployment-architecture"></a>Новая архитектура развертывания доменных служб Active Directory  
  
### <a name="ad-ds-role-deployment-and-management-architecture"></a>Развертывание AD роли доменных служб Active Directory и архитектура управления  
Диспетчер серверов и ADDSDeployment Windows PowerShell основываются на следующими основными сборками функциональные возможности при развертывании или управлении роли AD DS:  
  
-   Microsoft.ADroles.Aspects.dll  
  
-   Microsoft.ADroles.Instrumentation.dll  
  
-   Microsoft.ADRoles.ServerManager.Common.dll  
  
-   Microsoft.ADRoles.UI. Common.dll  
  
-   Microsoft.DirectoryServices.Deployment.Types.dll  
  
-   Microsoft.DirectoryServices.ServerManager.dll  
  
-   Addsdeployment.psm1  
  
-   Addsdeployment.psd1  
  
Оба компонента используют среду Windows PowerShell и ее механизм удаленного вызова команд для установки и настройки удаленного роли.  
  
![упрощенное администрирование](media/AD-DS-Simplified-Administration/ADDS_SMI_TR_DepDLLs.png)  
  
Windows Server 2012 также перестроен входили предыдущей операции повышения роли из LSASS.EXE, как часть:  
  
-   Служба сервера с ролью DS (dsrolesvc)  
  
-   DSRoleSvc.dll (загружаемая службой DsRoleSvc).  
  
Эта служба должна быть установлена и запущена для повышения роли, понижение уровня или клонирования виртуальных контроллеров домена. Установка роли AD DS, эта служба добавляется и устанавливается тип запуска вручную, по умолчанию. Не отключайте эту службу.  
  
### <a name="adprep-and-prerequisite-checking-architecture"></a>Средство ADPrep и архитектура проверки предварительных требований  
Средство Adprep больше не обязательно запускать на хозяине схемы. Его можно запускать удаленно с компьютера под управлением Windows Server 2008 x64 или более поздней версии.  
  
> [!NOTE]  
> Средство Adprep использует протокол LDAP для импорта файлов Schxx.ldf и не переподключается автоматически, если подключение к хозяину схемы прерывается во время импорта. В рамках процесса импорта хозяин схемы переводится в специальный режим, а переподключение отключается, так как при повторном LDAP потеряна, в определенный режим не будет снова устанавливается подключение. В этом случае схема будет обновлена неправильно.  
  
Проверка предварительных требований обеспечивает соблюдение определенных условий. Эти условия необходимы для успешной установки AD DS. Если некоторые обязательные условия не выполняются, они могут быть решены перед продолжением установки. Он также определяет леса или домена не готовность автоматическому выполнению кода развертывания Adprep.  
  
#### <a name="adprep-executables-dlls-ldfs-files"></a>Исполняемые файлы, библиотеки DLL, LDF, файлы ADPrep  
  
-   ADprep.dll  
  
-   Ldifde.dll  
  
-   Csvde.dll  
  
-   Sch14.ldf - Sch56.ldf  
  
-   Schupgrade.cat  
  
-   *Dcpromo.csv  
  
Код подготовки AD, который ранее помещался в ADprep.exe, прошел рефакторинг в adprep.dll. Это позволяет как ADPrep.exe и модуля ADDSDeployment Windows PowerShell использовать библиотеку для тех же задач и имеют одинаковые возможности. Adprep.exe входит в состав установочного носителя, но автоматические процессы не обращаются к ней напрямую — администратор должен запустить ее вручную. Он может работать только в Windows Server 2008 x64 и более поздних операционных системах. Ldifde.exe и csvde.exe также имеют прошедшие рефакторинг версий библиотек DLL, которые загружаются процессом подготовки. Расширения схемы по-прежнему используются заверенные подписями LDF файлы, как в предыдущих версиях операционной системы.  
  
![упрощенное администрирование](media/AD-DS-Simplified-Administration/ADDS_SMI_TR_AdprepDLLs.png)  
  
> [!IMPORTANT]  
> Существует используемый не 32-разрядного средства Adprep32.exe для Windows Server 2012. Необходимо иметь по крайней мере один Windows Server 2008 x64, Windows Server 2008 R2 или Windows Server 2012 компьютер, работающий как контроллер домена, рядовой сервер или член рабочей группы для подготовки леса и домена. Adprep.exe не выполняет команду на Windows Server 2003 x64.  
  
#### <a name="BKMK_PrereuisiteChecking"></a>Проверка предварительных требований  
Система, встроенная в Windows PowerShell ADDSDeployment управляемый код проверки предварительных требований работает в различных режимах в зависимости от условий. В приведенных ниже таблицах описывается каждый тест, если он используется, а также объяснение того, как и она проверяет. Эти таблицы могут быть полезны при возникновении проблем, где проверка завершается неудачно, а ошибки недостаточно для устранения неполадки.  
  
Результаты этих тестов регистрируются **DirectoryServices-Deployment** канал операционного журнала событий категории задач **Core**, всегда имеют код события **103**.  
  
##### <a name="prerequisite-windows-powershell"></a>Готовности к установке Windows PowerShell  
Существуют командлеты ADDSDeployment Windows PowerShell для каждого командлета развертывания контроллера домена. Их аргументы почти полностью же аргументами проверяемых командлетов.  
  
-   Test-ADDSDomainControllerInstallation  
  
-   Test-ADDSDomainControllerUninstallation  
  
-   Test-ADDSDomainInstallation  
  
-   Test-ADDSForestInstallation  
  
-   Test-ADDSReadOnlyDomainControllerAccountCreation  
  
Нет необходимости выполнять эти командлеты обычно; они выполняются с помощью командлетов развертывания по умолчанию.  
  
##### <a name="BKMK_ADDSInstallPrerequisiteTests"></a>Проверки предварительных требований  
  
||||  
|-|-|-|  
|Имя теста|Протоколы<br /><br />использовать|Описание и примечания|  
|VerifyAdminTrusted<br /><br />ForDelegationProvider|LDAP|Проверяет, что у вас есть «Включение учетных записей компьютера и пользователя доверенным для делегирования» привилегий (SeEnableDelegationPrivilege) на существующему партнерскому контроллеру домена. Для этого требуется доступ к построенному атрибуту tokenGroups.<br /><br />Не используется при взаимодействии с контроллерами домена Windows Server 2003. Необходимо вручную подтвердить это разрешение перед повышением роли|  
|VerifyADPrep<br /><br />Предварительные требования (лес)|LDAP|Обнаруживает и связывается с помощью атрибута rootDSE namingContexts и атрибута fsmoRoleOwner контекста именования схемы хозяин схемы. Определяет, какие операции подготовки (forestprep, domainprep или rodcprep) требуются для установки AD DS. Схема проверяет правильность атрибута objectVersion и необходимость ее дальнейшего расширения.|  
|VerifyADPrep<br /><br />Предварительные требования (домен и RODC)|LDAP|Обнаруживает и связывается хозяин инфраструктуры, с помощью атрибута rootDSE namingContexts и атрибута fsmoRoleOwner контейнера инфраструктуры. В случае установки RODC этот тест обнаруживает хозяина именования доменов и убедитесь, что он находится в оперативном режиме.|  
|CheckGroup<br /><br />Членство|LDAP,<br /><br />RPC через SMB (LSARPC)|Проверка пользователь является членом группы "Администраторы домена" или "Администраторы предприятия", в зависимости от операции (DA для добавления или понижения роли контроллера домена для добавления или удаления домена)|  
|CheckForestPrep<br /><br />GroupMembership|LDAP,<br /><br />RPC через SMB (LSARPC)|Проверка пользователь является членом группы "Администраторы схемы" и групп "Администраторы предприятия" и имеет аудита управления и ведения журналов событий безопасности (SesScurityPrivilege) для существующих контроллеров домена.|  
|CheckDomainPrep<br /><br />GroupMembership|LDAP,<br /><br />RPC через SMB (LSARPC)|Проверки пользователя является членом группы администраторов домена и имеет аудита управления и ведения журналов событий безопасности (SesScurityPrivilege) для существующих контроллеров домена.|  
|CheckRODCPrep<br /><br />GroupMembership|LDAP,<br /><br />RPC через SMB (LSARPC)|Проверки пользователя является членом группы "Администраторы предприятия" и имеет аудита управления и ведения журналов событий безопасности (SesScurityPrivilege) для существующих контроллеров домена.|  
|VerifyInitSync<br /><br />AfterReboot|LDAP|Проверить, был ли хозяин схемы реплицирован хотя бы один раз после перезапуска, путем присвоения фиктивного значения атрибуту rootDSE becomeschemamaster|  
|VerifySFUHotFix<br /><br />Применить|LDAP|Проверка существующего леса схемы не содержит известные проблемы с расширением SFU2 для атрибута UID с идентификатором Объекта 1.2.840.113556.1.4.7000.187.102<br /><br />([https://support.microsoft.com/kb/821732](https://support.microsoft.com/kb/821732))|  
|VerifyExchange<br /><br />SchemaFixed|LDAP, WMI, DCOM, RPC|Проверка существующего леса схемы не по-прежнему содержать проблемы с расширениями Exchange 2000 ms-Exch-Assistant-Name, ms-Exch-LabeledURI и ms-Exch-House-Identifier ([https://support.microsoft.com/kb/314649](https://support.microsoft.com/kb/314649))|  
|VerifyWin2KSchema<br /><br />Согласованности|LDAP|Проверка существующего леса схемы имеет согласованные (не измененные неправильно третьей стороной) основные атрибуты и классы.|  
|DCPromo|DRSR через RPC,<br /><br />LDAP,<br /><br />DNS-СЕРВЕРА<br /><br />RPC через SMB (SAMR)|Проверяет синтаксис командной строки, передаваемый в код и тестовые повышения роли повышения роли. Проверить леса или домена не существует ли уже создаваемый.|  
|VerifyOutbound<br /><br />ReplicationEnabled|LDAP, DRSR через SMB, RPC через SMB (LSARPC)|Проверка существующего контроллера домена, указанном в качестве партнера репликации Исходящая репликация включена путем проверки объекта параметров NTDS атрибут параметров NTDSDSA_OPT_DISABLE_OUTBOUND_REPL (0x00000004)|  
|VerifyMachineAdmin<br /><br />Пароль|DRSR через RPC,<br /><br />LDAP,<br /><br />DNS-СЕРВЕРА<br /><br />RPC через SMB (SAMR)|Проверьте пароль безопасного режима, установленный для DSRM требованиям к сложности для домена.|  
|VerifySafeModePassword|*Н/Д*|Проверка локального администратора пароль набор соответствует компьютера безопасности политики требованиям сложности.|  
  

