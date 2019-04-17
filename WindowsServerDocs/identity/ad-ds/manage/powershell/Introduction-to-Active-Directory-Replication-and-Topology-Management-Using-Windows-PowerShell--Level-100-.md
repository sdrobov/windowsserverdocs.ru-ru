---
ms.assetid: c54b544f-cc32-4837-bb2d-a8656b22f3de
title: "Введение в Active Directory Управление репликацией и топологией с помощью Windows PowerShell (уровень 100)"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 006179bb3220f7bccfc7510e1b8ef69678321074
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="introduction-to-active-directory-replication-and-topology-management-using-windows-powershell-level-100"></a>Введение в Active Directory Управление репликацией и топологией с помощью Windows PowerShell (уровень 100)

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Windows PowerShell для Active Directory включает возможность управления репликации, сайты, домены и леса, контроллеры домена и разделов. Пользователи предыдущих средств управления, например Active Directory — сайты и службы оснастка и repadmin.exe будет Обратите внимание, что похожая функциональность теперь доступна внутри Windows PowerShell для контекста Active Directory. Кроме того командлеты совместимы с существующими Windows PowerShell для командлеты Active Directory, что приводит к созданию упрощенного взаимодействия и позволяет пользователям легко создавать сценарии автоматизации.

> [!NOTE]
> Windows PowerShell для репликации Active Directory и командлеты топологией доступны в следующих средах:
> 
> -    Контроллер домена Windows Server 2012
> -    Установленным сервером Windows Server 2012 с помощью средств удаленного администрирования сервера для AD DS и AD LDS.
> -   Windows&reg; 8 с помощью средств удаленного администрирования сервера для AD DS и AD LDS установлен.

## <a name="installing-the-active-directory-module-for-windows-powershell"></a>Установка модуля Active Directory для Windows PowerShell
Модуль Active Directory для Windows PowerShell устанавливается по умолчанию при установке роли сервера AD DS на сервере под управлением Windows Server 2012. Помимо добавления роли сервера необходимы дополнительные шаги. Можно также установить модуль Active Directory на сервер под управлением Windows Server 2012, установив средства удаленного администрирования сервера, и можно установить модуль Active Directory на компьютере под управлением Windows 8, скачав и установив [удаленного средства администрирования сервера (RSAT)](https://www.microsoft.com/download/details.aspx?id=28972). В разделе [инструкции](https://www.microsoft.com/download/details.aspx?id=28972)для действия по установке.

## <a name="scenarios-for-testing-windows-powershell-for-active-directory-replication-and-topology-management-cmdlets"></a>Сценарии для тестирования Windows PowerShell для командлетов управления репликацией и топологией Active Directory
Следующие сценарии предназначены для администраторов, чтобы ознакомиться с новыми командлетами управления:

-   Получение списка всех контроллеров домена и соответствующих сайтов

-   Управление топологией репликации

-   Просмотр состояния репликации и сведения

## <a name="lab-requirements"></a>Лабораторные требования

-   Два контроллера домена Windows Server 2012: **DC1** и **DC2**, являются частью домена contoso.com и располагающиеся на сайте CORPORATE внутри этого домена.

## <a name="view-domain-controllers-and-their-sites"></a>Просмотр контроллеров домена и соответствующих сайтов
На этом шаге будет использовать модуль Active Directory для Windows PowerShell, чтобы просмотреть существующие контроллеры домена и топологию репликации для домена.

Для выполнения действий с помощью следующих процедур необходимо быть членом группы администраторов домена или иметь аналогичные разрешения.

#### <a name="to-view-all-active-directory-sites"></a>Просмотр всех узлов Active Directory

1.  На **DC1**, нажмите кнопку **Windows PowerShell** на панели задач.

2.  Введите следующую команду:

    `Get-ADReplicationSite -Filter *`

    Эта команда возвращает подробные сведения о каждом сайте. `Filter`Используется во всех командлетах AD PowerShell для ограничения списка возвращаемых объектов. В этом случае звездочка (*) означает все объекты сайта.

    > [!TIP]
    > Можно использовать клавишу Tab для автозаполнения команд в Windows PowerShell.
    > 
    > Пример: Введите `Get-ADRep`и нажмите клавишу Tab несколько раз, чтобы пропустить команды, начинающиеся, пока не дойдете до `Get-ADReplicationSite`. Также работает автозаполнение для имен параметров например `Filter`.

    Для форматирования выходных данных `Get-ADReplicationSite`команды в виде таблицы и Показать только определенные поля, можно передать выходные значения `Format-Table`команды (или «`ft`» для краткости):

    `Get-ADReplicationSite -Filter * | ft Name`

    Эта команда возвращает краткая версия списка сайтов, включающая только поле имя.

#### <a name="to-produce-a-table-of-all-domain-controllers"></a>Создание таблицы всех контроллеров домена

-   Введите следующую команду в **модуля Active Directory для Windows PowerShell** строки:

    `Get-ADDomainController -Filter * | ft Hostname,Site`

    Эта команда возвращает контроллеры домена узла, имя, а также их связи с сайтами.

## <a name="manage-replication-topology"></a>Управление топологией репликации
На предыдущем шаге после выполнения команды `Get-ADDomainController -Filter * | ft Hostname,Site`, **DC2** было указано в списке в составе **CORPORATE** сайта. В приведенных ниже процедур вы создадите новый сайт филиала, **BRANCH1**, создание новой связи сайтов, задание сайта ссылку стоимости и частоты репликации, а затем переместите **DC2** для **BRANCH1**.

Для выполнения действий с помощью следующих процедур необходимо быть членом группы администраторов домена или иметь аналогичные разрешения.

#### <a name="to-create-a-new-site"></a>Создание нового сайта

-   Введите следующую команду в **модуля Active Directory для Windows PowerShell** строки:

    `New-ADReplicationSite BRANCH1`

    Эта команда создает новый сайт филиала branch1.

#### <a name="to-create-a-new-site-link"></a>Создание новой связи сайтов

-   Введите следующую команду в **модуля Active Directory для Windows PowerShell** строки:

    `New-ADReplicationSiteLink 'CORPORATE-BRANCH1'  -SitesIncluded CORPORATE,BRANCH1 -OtherAttributes @{'options'=1}`

    Этой команды создается связь сайтов для **BRANCH1** и включается процесс уведомления изменение об.

    > [!TIP]
    > Используйте вкладку имена параметров автозаполнения, таких как `-SitesIncluded`и `-OtherAttributes`вместо того чтобы вводить вручную.

#### <a name="to-set-the-site-link-cost-and-replication-frequency"></a>Чтобы задать сайта ссылку стоимости и частоты репликации

-   Введите следующую команду в **модуля Active Directory для Windows PowerShell** строки:

    `Set-ADReplicationSiteLink CORPORATE-BRANCH1 -Cost 100 -ReplicationFrequencyInMinutes 15`

    Эта команда задает стоимость связи сайтов **BRANCH1** в **100** и частота репликации с сайтом **15 минут **.

#### <a name="to-move-a-domain-controller-to-a-different-site"></a>Перемещение контроллера домена на другой узел

-   Введите следующую команду в **модуля Active Directory для Windows PowerShell** строки:

    `Get-ADDomainController DC2 | Move-ADDirectoryServer -Site BRANCH1`

    Эта команда перемещает контроллер домена **DC2** для **BRANCH1** сайта.

### <a name="verification"></a>Проверка

##### <a name="to-verify-site-creation-new-site-link-and-cost-and-replication-frequency"></a>Проверка создания сайта, новой связи сайтов и стоимости и частоты репликации

-   Нажмите кнопку **диспетчера сервера**, нажмите кнопку **средства** и нажмите кнопку **Active Directory — сайты и службы** и проверьте следующее:

    Убедитесь, что **BRANCH1** сайта содержит все правильные значения из команд Windows PowerShell.

    Проверка **CORPORATE-BRANCH1** связь сайтов создается и подключается **BRANCH1** и **CORPORATE** сайтов.

    Проверка **DC2** теперь находится в **BRANCH1** сайта. Кроме того, можно открыть **модуль Active Directory для Windows PowerShell** и введите следующую команду, чтобы проверить **DC2** теперь находится в **BRANCH1** сайта:`Get-ADDomainController -Filter * | ft Hostname,Site`.

## <a name="view-replication-status-information"></a>Просмотр сведений о состоянии репликации
В следующих процедурах будет использоваться один из Windows PowerShell для репликации Active Directory и командлеты управления `Get-ADReplicationUpToDatenessVectorTable DC1`, чтобы получить простой отчет о репликации с помощью векторной таблицы синхронизации, поддерживается каждым контроллером домена. Этой векторной таблице синхронизации, сохраняет сведения об наивысшего исходный USN записи, отображаемый на каждом контроллере домена в лесу.

Для выполнения действий с помощью следующих процедур необходимо быть членом группы администраторов домена или иметь аналогичные разрешения.

#### <a name="to-view-the-up-to-dateness-vector-table-for-a-single-domain-controller"></a>Просмотр векторной таблицы синхронизации для одного контроллера домена

1.  Введите следующую команду в **модуля Active Directory для Windows PowerShell** строки:

    `Get-ADReplicationUpToDatenessVectorTable DC1`

    Здесь отображается список наивысший номер последовательного обновления, отображаемый на **DC1** для каждого контроллера домена в лесу. **Сервера** значение относится к серверу, ведется таблица: в этом случае **DC1**. **Партнеров** значение ссылается на партнера репликации (прямому или непрямому), на котором были внесены изменения. Значение параметра UsnFilter является наивысшим USN, отображаемый на **DC1** от партнера. Если в лес будет добавлен новый контроллер домена, он не появится в **DC1**в таблице до **DC1** получит изменение, исходящее от нового домена.

#### <a name="to-view-the-up-to-dateness-vector-table-for-all-domain-controllers-in-a-domain"></a>Просмотр векторной таблицы синхронизации для всех контроллеров домена в домене

1.  Введите следующую команду в командной строке модуля Active Directory для Windows PowerShell:

    `Get-ADReplicationUpToDatenessVectorTable * | sort Partner,Server | ft Partner,Server,UsnFilter`

    Эта команда заменяет **DC1** с `*`, таким образом собрать данные векторной таблицы синхронизации со всех контроллеров домена. Данные сортируются по **партнеров** и **сервера** и затем отображаются в таблице.

    Сортировка позволяет легко сравнить последний номер последовательного обновления, отображаемый на каждом контроллере домена для данного партнера репликации. Это быстрый способ убедиться, что репликация проходит во всей среде. Если репликация работает правильно, значения параметра UsnFilter для данного партнера репликации должны быть похожи на всех контроллерах домена.

## <a name="see-also"></a>См. также:
[Дополнительные репликации Active Directory и управления топологией с помощью Windows PowerShell & #40; Уровень 200 & #41;](Advanced-Active-Directory-Replication-and-Topology-Management-Using-Windows-PowerShell--Level-200-.md)


