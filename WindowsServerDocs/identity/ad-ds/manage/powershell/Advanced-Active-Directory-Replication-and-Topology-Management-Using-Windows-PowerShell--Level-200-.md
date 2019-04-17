---
ms.assetid: fe05e52c-cbf8-428b-8176-63407991042f
title: "Дополнительные репликации Active Directory и управления топологией с помощью Windows PowerShell (уровень 200)"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 1e05616b4b594ae54fcaa3ec6496c0917ecde38b
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="advanced-active-directory-replication-and-topology-management-using-windows-powershell-level-200"></a>Дополнительные репликации Active Directory и управления топологией с помощью Windows PowerShell (уровень 200)

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

В этом разделе описываются новые Репликация AD DS и командлеты управления топологией более подробно и приводятся дополнительные примеры. Вводные сведения см. в разделе [введение в репликации Active Directory и управление топологией с помощью Windows PowerShell & #40; Уровень 100 & #41; ](../../../ad-ds/manage/powershell/Introduction-to-Active-Directory-Replication-and-Topology-Management-Using-Windows-PowerShell--Level-100-.md).  
  
1.  [Введение](../../../ad-ds/manage/powershell/Advanced-Active-Directory-Replication-and-Topology-Management-Using-Windows-PowerShell--Level-200-.md#BKMK_Intro)  
  
2.  [Репликация и метаданные](../../../ad-ds/manage/powershell/Advanced-Active-Directory-Replication-and-Topology-Management-Using-Windows-PowerShell--Level-200-.md#BKMK_Repl)  
  
3.  [Get-ADReplicationAttributeMetadata](../../../ad-ds/manage/powershell/Advanced-Active-Directory-Replication-and-Topology-Management-Using-Windows-PowerShell--Level-200-.md#BKMK_ReplAttrMD)  
  
4.  [Get-ADReplicationPartnerMetadata](../../../ad-ds/manage/powershell/Advanced-Active-Directory-Replication-and-Topology-Management-Using-Windows-PowerShell--Level-200-.md#BKMK_PartnerMD)  
  
5.  [Get-ADReplicationFailure](../../../ad-ds/manage/powershell/Advanced-Active-Directory-Replication-and-Topology-Management-Using-Windows-PowerShell--Level-200-.md#BKMK_ReplFail)  
  
6.  [Get-ADReplicationQueueOperation и Get-ADReplicationUpToDatenessVectorTable](../../../ad-ds/manage/powershell/Advanced-Active-Directory-Replication-and-Topology-Management-Using-Windows-PowerShell--Level-200-.md#BKMK_ReplQueue)  
  
7.  [Синхронизация ADObject](../../../ad-ds/manage/powershell/Advanced-Active-Directory-Replication-and-Topology-Management-Using-Windows-PowerShell--Level-200-.md#BKMK_Sync)  
  
8.  [Топология](../../../ad-ds/manage/powershell/Advanced-Active-Directory-Replication-and-Topology-Management-Using-Windows-PowerShell--Level-200-.md#BKMK_Topo)  
  
## <a name="BKMK_Intro"></a>Введение  
Windows Server 2012 модуль Active Directory для Windows PowerShell расширен двадцатью пятью новыми командлетами, для управления репликацией и топологией леса. До этого приходилось использовать универсальные командлеты **\*-AdObject** или вызывать функции .NET.  
  
Как и все командлеты Windows PowerShell для Active Directory, эти новые командлеты требуют установки [службы шлюза управления Active Directory](https://www.microsoft.com/download/details.aspx?displaylang=en&id=2852) по крайней мере один контроллер домена (а лучше, все контроллеры домена).  
  
В следующей таблице перечислены новые командлеты репликацией и топологией добавленные в модуль Active Directory в Windows PowerShell.  
  
|||  
|-|-|  
|Командлет|Объяснение|  
|Get-ADReplicationAttributeMetadata|Возвращает метаданные репликации атрибутов для объекта|  
|Get-ADReplicationConnection|Возвращает сведения об объекте подключения к контроллеру домена|  
|Get-ADReplicationFailure|Возвращает последнем сбое репликации для контроллера домена|  
|Get-ADReplicationPartnerMetadata|Возвращает конфигурацию репликации для контроллера домена|  
|Get-ADReplicationQueueOperation|Возвращает текущую невыполненную часть очереди репликации|  
|Get-ADReplicationSite|Возвращает сведения о сайте|  
|Get-ADReplicationSiteLink|Возвращает сведения о связи сайта|  
|Get-ADReplicationSiteLinkBridge|Возвращает сведения о мосте связей сайтов|  
|Get-ADReplicationSubnet|Возвращает сведения о подсети AD|  
|Get-ADReplicationUpToDatenessVectorTable|Возвращает сведения о векторе UTD для контроллера домена|  
|Get-ADTrust|Возвращает сведения об доверия между доменами или между лесами|  
|New-ADReplicationSite|Создает сайт.|  
|Новый ADReplicationSiteLink|Создание новой связи сайтов|  
|Новый ADReplicationSiteLinkBridge|Создание нового моста связей сайтов|  
|Новый ADReplicationSubnet|Создает подсеть AD|  
|Remove-ADReplicationSite|Удаляет сайт.|  
|Remove-ADReplicationSiteLink|Удаляет связь сайтов.|  
|Remove-ADReplicationSiteLinkBridge|Удаляет мост связей сайтов.|  
|Remove-ADReplicationSubnet|Удаляет подсеть AD|  
|SET-ADReplicationConnection|Изменяет подключение.|  
|SET-ADReplicationSite|Изменяет сайт.|  
|SET-ADReplicationSiteLink|Изменяет связь сайтов.|  
|SET-ADReplicationSiteLinkBridge|Изменяет мост связей сайтов.|  
|SET-ADReplicationSubnet|Изменяет подсеть AD|  
|Синхронизация ADObject|Принудительная репликация отдельного объекта.|  
  
Большинство этих командлетов основаны имеют в Repadmin.exe. Другие командлеты (не приведенные в списке) используют такие компоненты, как динамический контроль доступа и групповые управляемые учетные записи служб.  
  
Полный список всех командлетов Windows PowerShell для Active Directory выполните следующую команду:  
  
```  
Get-command -module ActiveDirectory  
```  
  
Полный список аргументов командлетов Windows PowerShell для Active Directory обратитесь к справке. Например:  
  
```  
Get-help New-ADReplicationSite  
  
```  
  
Используйте `Update-Help` чтобы скачать и установить файлы справки  
  
### <a name="BKMK_Repl"></a>Репликация и метаданные  
Repadmin.exe проверяет состояние и согласованность репликации Active Directory. Repadmin.exe обеспечивает простые данных манипуляции — некоторые аргументы поддерживают вывод данных в CSV, например - но автоматизации как правило, требуется разбор содержимого текстовых файлов. Модуль Active Directory для Windows PowerShell — это первая попытка обеспечить настоящий контроль над возвращаемыми данными; раньше приходилось создавать сценарии или использовать сторонние средства.  
  
Кроме того, в следующих командлетах реализован новый набор параметров **целевой**, **область**, и **EnumerationServer**:  
  
-   **Get-ADReplicationFailure**  
  
-   **Get-ADReplicationPartnerMetadata**  
  
-   **Get-ADReplicationUpToDatenessVectorTable**  
  
**Целевой** аргумент принимает разделенный запятыми список строк, которые определяют целевые серверы, сайты, домены или леса, указанные в **область** аргумент. Знак "звездочка" (\ *) также является допустимым и означает все серверы в указанной области. Если область не указана, она означает все серверы в лесу текущего пользователя. **Область** аргумент определяет диапазон поиска. Допустимые значения: **сервера**, **сайта**, **домена**, и **леса**. **EnumerationServer** определяет сервер, который перечисляет список контроллеров домена, указанных в **целевой** и **область**. Он работает так же, как **сервера** аргумент и требует на указанном сервере была запущена веб-служба Active Directory.  
  
Для знакомства с новыми командлетами, ниже приведено несколько примеров сценариев показаны возможности, недоступные в repadmin.exe; Используя эти иллюстрации, наглядно возможности для администраторов. Просмотрите справку для конкретных потребностей.  
  
### <a name="BKMK_ReplAttrMD"></a>Get-ADReplicationAttributeMetadata  
Этот командлет аналогичен **repadmin.exe/showobjmeta**. Он позволяет возвращать метаданные репликации, например время изменения атрибута, исходный контроллер домена, версию и информацию USN и данные атрибута. Этот командлет полезен для отслеживания и места после внесения изменения.  
  
В отличие от программы Repadmin Windows PowerShell предоставляет гибкий поиском и выходными данными элемента управления. Например можно выводить метаданные объекта "Администраторы домена", упорядоченные в виде упорядоченного читаемого списка:  
  
```  
Get-ADReplicationAttributeMetadata -object "cn=domain admins,cn=users,dc=corp,dc=contoso,dc=com" -server dc1.corp.contoso.com -showalllinkedvalues | format-list  
  
```  
  
![Расширенное управление с помощью powershell](media/Advanced-Active-Directory-Replication-and-Topology-Management-Using-Windows-PowerShell--Level-200-/ADDS_PSGetADReplAttrMd.png)  
  
Кроме того можно упорядочить данных выглядеть repadmin в таблице:  
  
```  
Get-ADReplicationAttributeMetadata -object "cn=domain admins,cn=users,dc=corp,dc=contoso,dc=com" -server dc1.corp.contoso.com -showalllinkedvalues | format-table -wrap  
  
```  
  
![Расширенное управление с помощью powershell](media/Advanced-Active-Directory-Replication-and-Topology-Management-Using-Windows-PowerShell--Level-200-/ADDS_PSGetADReplAttrMdTable.png)  
  
Кроме того, можно получить метаданные для всего класса объектов, по конвейеру **Get-Adobject** командлет с фильтр, например все группы - затем объединить, с определенной даты. Конвейер — это канал между несколькими командлетами для обмена данными. Чтобы просмотреть все группы, измененные каким-либо образом 13 января 2012:  
  
```  
get-adobject -filter 'objectclass -eq "group"' | Get-ADReplicationAttributeMetadata -server dc1.corp.contoso.com | where-object {$_.lastoriginatingchangetime -like "*1/13/2012*" -and $_.attributename -eq "name"} | format-table object  
```  
  
![Расширенное управление с помощью powershell](media/Advanced-Active-Directory-Replication-and-Topology-Management-Using-Windows-PowerShell--Level-200-/ADDS_PSGetADReplAttrMdClass.png)  
  
Дополнительные сведения о других операциях Windows PowerShell с конвейерами см. в разделе [конвейерная передача и конвейер в Windows PowerShell](https://technet.microsoft.com/library/ee176927.aspx).  
  
Кроме того чтобы узнать, у каждой группы, входит пользователь Tony Wang и производилось последнее изменение группы:  
  
```  
get-adobject -filter 'objectclass -eq "group"' | Get-ADReplicationAttributeMetadata -server dc1.corp.contoso.com -showalllinkedvalues | where-object {$_.attributevalue -like "*tony wang*"} | format-table object,LastOriginatingChangeTime,version -auto  
  
```  
  
![Расширенное управление с помощью powershell](media/Advanced-Active-Directory-Replication-and-Topology-Management-Using-Windows-PowerShell--Level-200-/ADDS_PSGetADReplAttrMdFilter.png)  
  
Кроме того чтобы найти все объекты восстановленные принудительно с помощью резервной копии состояния системы в домене, на основе полученной искусственно версии:  
  
```  
get-adobject -filter 'objectclass -like "*"' | Get-ADReplicationAttributeMetadata -server dc1.corp.contoso.com | where-object {$_.version -gt "100000" -and $_.attributename -eq "name"} | format-table object,LastOriginatingChangeTime  
```  
  
![Расширенное управление с помощью powershell](media/Advanced-Active-Directory-Replication-and-Topology-Management-Using-Windows-PowerShell--Level-200-/ADDS_PSGetADReplAttrMdFilter2.png)  
  
Можно также отправьте все метаданные пользователей в CSV-файл для последующего изучения в Microsoft Excel.  
  
```  
get-adobject -filter 'objectclass -eq "user"' | Get-ADReplicationAttributeMetadata -server dc1.corp.contoso.com -showalllinkedvalues | export-csv allgroupmetadata.csv  
```  
  
### <a name="BKMK_PartnerMD"></a>Get-ADReplicationPartnerMetadata  
Этот командлет возвращает сведения о конфигурации и состоянии репликации для контроллера домена, что позволяет отслеживать, инвентаризации или устранения неполадок. В отличие от Repadmin.exe с помощью Windows PowerShell означает, что вы видите только данные, которые вам важно, в нужный формат.  
  
Например для чтения состояние репликации отдельного контроллера домена:  
  
```  
Get-ADReplicationPartnerMetadata -target dc1.corp.contoso.com  
```  
  
![Расширенное управление с помощью powershell](media/Advanced-Active-Directory-Replication-and-Topology-Management-Using-Windows-PowerShell--Level-200-/ADDS_PSGetADReplPartnerMd.png)  
  
Кроме того, время последнего контроллера домена репликации входящих подключений и отформатируйте его партнеров в таблице:  
  
```  
Get-ADReplicationPartnerMetadata -target dc1.corp.contoso.com | format-table lastreplicationattempt,lastreplicationresult,partner -auto  
```  
  
![Расширенное управление с помощью powershell](media/Advanced-Active-Directory-Replication-and-Topology-Management-Using-Windows-PowerShell--Level-200-/ADDS_PSGetADReplPartnerMdTable.png)  
  
Чтобы связаться со всеми контроллерами домена в лесу и получить них которого последней попытке репликации которых произошел сбой по какой-либо причине:  
  
```  
Get-ADReplicationPartnerMetadata -target * -scope server | where {$_.lastreplicationresult -ne "0"} | ft server,lastreplicationattempt,lastreplicationresult,partner -auto  
  
```  
  
![Расширенное управление с помощью powershell](media/Advanced-Active-Directory-Replication-and-Topology-Management-Using-Windows-PowerShell--Level-200-/ADDS_PSGetADReplPartnerMdFail.png)  
  
### <a name="BKMK_ReplFail"></a>Get-ADReplicationFailure  
Этот командлет можно использовать для возвращает сведения о последних ошибках репликации. Он аналогичен **Repadmin.exe /showreplsum**, но опять же, с гораздо больший контроль благодаря среде Windows PowerShell.  
  
Например вы можете вернуться последних сбоях контроллера домена и партнерах, с которыми не удалось связаться:  
  
```  
Get-ADReplicationFailure dc1.corp.contoso.com  
```  
  
![Расширенное управление с помощью powershell](media/Advanced-Active-Directory-Replication-and-Topology-Management-Using-Windows-PowerShell--Level-200-/ADDS_PSGetADReplFail.png)  
  
Можно также получить таблицы для всех серверов в определенном сайте логических AD, упорядоченными для более удобного просмотра только наиболее важными сведениями:  
  
```  
Get-ADReplicationFailure -scope site -target default-first-site-name | format-table server,firstfailuretime,failurecount,lasterror,partner -auto  
  
```  
  
![Расширенное управление с помощью powershell](media/Advanced-Active-Directory-Replication-and-Topology-Management-Using-Windows-PowerShell--Level-200-/ADDS_PSGetADReplFailScoped.png)  
  
### <a name="BKMK_ReplQueue"></a>Get-ADReplicationQueueOperation и Get-ADReplicationUpToDatenessVectorTable  
Оба эти командлета возвращают дополнительные контроллера домена «актуальном», включая текущие репликации и сведения о вектор версии.  
  
### <a name="BKMK_Sync"></a>Синхронизация ADObject  
Этот командлет аналогичен **Repadmin.exe/replsingleobject**. Он очень полезен при внесении изменений, требующих отдельной репликации, особенно при устранении неполадок.  
  
Например если кто-то удалил учетную запись генерального Директора а затем восстановил ее с помощью корзины Active Directory, возможно, необходимо немедленно реплицировать на все контроллеры домена. Кроме того, возможно, вы хотите это сделать без принудительной репликации изменений других объектов, внесенных; в конце концов именно поэтому у вас есть расписание репликации, чтобы избежать перегружать каналы глобальной сети.  
  
```  
Get-ADDomainController -filter * | foreach {Sync-ADObject -object "cn=tony wang,cn=users,dc=corp,dc=contoso,dc=com" -source dc1 -destination $_.hostname}  
  
```  
  
![Расширенное управление с помощью powershell](media/Advanced-Active-Directory-Replication-and-Topology-Management-Using-Windows-PowerShell--Level-200-/ADDS_PSSyncAD.png)  
  
### <a name="BKMK_Topo"></a>Топология  
Хотя Repadmin.exe — это эффективное средство для получения информации о топологии репликации, включая сайты, связи сайтов, мостов связей сайтов и подключения, она не предоставляет достаточно широкий набор аргументов для внесения изменений. На самом деле никогда не было сценариев, в поле служебная программа, предназначенная специально для администраторов для создания и изменения топологии Доменных службах Active Directory. Как развития Active Directory в средах миллионов клиентов потребность в массовом изменении Active Directory сведения о логическом стала очевидной.  
  
Например после быстрого развертывания новых филиалов, сопровождающегося объединением существующих, может потребоваться сотни сайта внести изменений на основе с физическим расположением, изменения в сети и новыми требованиями к емкости. Вместо использования Dssites.msc и Adsiedit.msc, чтобы внести изменения, можно автоматизировать. Это особенно привлекательных при запуске на основе таблиц с данными, предоставленными группами вашей сети и технического обслуживания.  
  
**Get-Adreplication\ *** возвращают информацию о топологии репликации и удобно по конвейеру в командлеты **задать-Adreplication\ *** командлеты. **Получить** командлеты, которые не изменяют данные, они отображаются только данные, или для Windows PowerShell создания объектов сеансов, которые можно передавать по конвейеру в **задать-Adreplication\ *** командлетов. **New** и **удалить** командлеты полезны для создания и удаления объектов топологии Active Directory.  
  
Например можно создать новые сайты с помощью файла CSV:  
  
```  
import-csv -path C:\newsites.csv | new-adreplicationsite  
```  
  
![Расширенное управление с помощью powershell](media/Advanced-Active-Directory-Replication-and-Topology-Management-Using-Windows-PowerShell--Level-200-/ADDS_PSNewSitesCSV.png)  
  
![Расширенное управление с помощью powershell](media/Advanced-Active-Directory-Replication-and-Topology-Management-Using-Windows-PowerShell--Level-200-/ADDS_PSImportCSV.png)  
  
Кроме того можно создайте новую связь сайтов между двумя существующими сайтами с пользовательских репликации интервал и сайта затрат:  
  
```  
new-adreplicationsitelink -name "chicago<-->waukegan" -sitesincluded chicago,waukegan -cost 50 -replicationfrequencyinminutes 15  
```  
  
![Расширенное управление с помощью powershell](media/Advanced-Active-Directory-Replication-and-Topology-Management-Using-Windows-PowerShell--Level-200-/ADDS_PSNewADReplSite.png)  
  
Чтобы найти каждый сайт в лесу и заменить их **параметры** атрибуты с флагом, чтобы включить межсайтового уведомление об изменениях, целью репликации Максимальная скорость, с помощью сжатия:  
  
```  
get-adreplicationsitelink -filter * | set-adobject -replace @{options=$($_.options -bor 1)}  
```  
  
![Расширенное управление с помощью powershell](media/Advanced-Active-Directory-Replication-and-Topology-Management-Using-Windows-PowerShell--Level-200-/ADDS_PSNewADReplSiteLink.gif)  
  
> [!IMPORTANT]  
> Задайте **- bor 5** Чтобы отключить сжатие для этих связей сайтов.  
  
Чтобы найти все сайты с отсутствующими назначениями подсетей с целью сверки списка фактических подсетей для этих расположений:  
  
```  
get-adreplicationsite -filter * -property subnets | where-object {!$_.subnets -eq "*"} | format-table name  
```  
  
![Расширенное управление с помощью powershell](media/Advanced-Active-Directory-Replication-and-Topology-Management-Using-Windows-PowerShell--Level-200-/ADDS_PSNewADReplSiteFiltrer.png)  
  
## <a name="see-also"></a>См. также:  
[Введение в Active Directory Управление репликацией и топологией с помощью Windows PowerShell & #40; Уровень 100 & #41;](../../../ad-ds/manage/powershell/Introduction-to-Active-Directory-Replication-and-Topology-Management-Using-Windows-PowerShell--Level-100-.md)  
  

