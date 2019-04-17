---
ms.assetid: 7671e0c9-faf0-40de-808a-62f54645f891
title: "Обновление до AD FS в Windows Server 2016"
description: 
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: ce07398a2d624a1e9b004cd35eb9228d59dc2b5b
ms.sourcegitcommit: 76e57a5453d6ee9a04dcff6a8cca087132cb1d5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/20/2018
---
# <a name="upgrading-to-ad-fs-in-windows-server-2016-using-a-wid-database"></a>Обновление до AD FS в Windows Server 2016 с помощью Внутренней базой данных Windows

>Область применения: Windows Server 2016


## <a name="moving-from-a-windows-server-2012-r2-ad-fs-farm-to-a-windows-server-2016-ad-fs-farm"></a>Перемещение из фермы Windows Server 2012 R2 AD FS в ферме Windows Server 2016 AD FS  
Следующий документ будет описано, как обновить ферму AD FS Windows Server 2012 R2 AD FS в Windows Server 2016, при использовании Внутренней базой данных.  

### <a name="upgrading-ad-fs-to-windows-server-2016-fbl"></a>Обновление до Windows Server 2016 FBL AD FS  
Новые возможности AD FS в Windows Server 2016 функция уровня поведение фермы (FBL).   Эти функции всю ферму и определяет функции, которые можно использовать в ферме AD FS.   По умолчанию FBL в ферме Windows Server 2012 R2 AD FS является Windows Server 2012 R2 FBL.  

Сервер Windows Server 2016 AD FS можно добавить в ферму Windows Server 2012 R2, и он будет работать на одном FBL как Windows Server 2012 R2.  При наличии Windows Server 2016 AD FS сервер, работающий таким образом, считается, что ферме «смешивать».  Тем не менее вы не сможете воспользоваться преимуществами новых возможностей Windows Server 2016 до возникновения FBL на Windows Server 2016.  С помощью смешанного фермы:  

-   Администраторы могут добавлять новые, Windows Server 2016 серверов федерации в существующей ферме Windows Server 2012 R2.  В результате ферма в «смешанный режим» и работает на уровне поведение Windows Server 2012 R2 фермы.  Чтобы обеспечить согласованное поведение в ферме, новые функции Windows Server 2016 не настроен или используемых в этом режиме.  

-   После того как все серверы федерации Windows Server 2012 R2 были удалены из фермы смешанном режиме и в случае ферме внутренней базы данных Windows, один из новых серверов федерации Windows Server 2016 выдвинут на роль основного узла, администратор может затем изменить FBL с Windows Server 2012 R2 на Windows Server 2016.  В результате все новые возможности AD FS Windows Server 2016 можно затем настроить и использовать.  

-   В результате функцию смешанного фермы AD FS Windows Server 2012 R2, организаций, которым для обновления до Windows Server 2016, не требуется развертывать ферму совершенно новые экспорта и импорта данных конфигурации.  Вместо этого можно добавить узлы Windows Server 2016 в существующую ферму подключенной сети и только взимается относительно небольшой простой, участвующие в повышение FBL.  

Имейте в виду, что в режиме смешанных фермы фермы AD FS не может любой новые компоненты или функциональные возможности, появившиеся в AD FS в Windows Server 2016.  Это означает, что организаций, желающих попробовать новые функции не может это сделать, до возникновения FBL.  Поэтому если организации требуется для тестирования новых компонентов до rasing FBL, будет необходимо развернуть отдельный фермы для этого.  

Оставшаяся часть является документ содержит шаги для добавления сервера федерации Windows Server 2016 в среде Windows Server 2012 R2 и затем вызова FBL на Windows Server 2016.  Эти действия были выполнены в тестовой среде, изложенным в Архитектурная схема ниже.  

> [!NOTE]  
> Перед перемещением на AD FS в Windows Server 2016 FBL, необходимо удалить все узлы Windows 2012 R2.  Нельзя просто обновление ОС Windows Server 2012 R2 до Windows Server 2016 и его становятся узел 2016.  Необходимо удалить его и замените его на новый узел 2016.
>
> Обновление FBL при использовании SQL для хранения конфигурации Служб федерации Active Directory создайте новую базу данных управления «AdfsConfigurationV3».

##### <a name="to-upgrade-your-ad-fs-farm-to-windows-server-2016-farm-behavior-level"></a>Для обновления до Windows Server 2016 фермы поведение уровень фермы AD FS  

1.  С помощью диспетчера сервера установить роль служб федерации Active Directory в Windows Server 2016  

2.  С помощью мастера конфигурации AD FS, присоединение нового сервера Windows Server 2016 к существующей ферме AD FS.  

    ![обновление](media/Upgrading-to-AD-FS-in-Windows-Server-2016/ADFS_Mixed_1.png)  

3.  На сервере федерации Windows Server 2016 откройте управления AD FS.    Обратите внимание, что ничего, отображается как этот сервер федерации не основного сервера.  

    ![обновление](media/Upgrading-to-AD-FS-in-Windows-Server-2016/ADFS_Mixed_3.png)  

4.  По завершении соединения, на сервере Windows Server 2016, откройте PowerShell и выполните следующий командлет: Set AdfsSyncProperties-PrimaryComputer роли  

    ![обновление](media/Upgrading-to-AD-FS-in-Windows-Server-2016/ADFS_Mixed_4.png)  

5.  На исходном сервере AD FS Windows Server 2012 R2, откройте PowerShell и выполните следующий командлет: Set AdfsSyncProperties-SecondaryComputer роли - PrimaryComputerName {полное доменное имя}  

    ![обновление](media/Upgrading-to-AD-FS-in-Windows-Server-2016/ADFS_Mixed_5.png)  

6.  На вашем прокси веб-приложения, откройте PowerShell и выполните командлет следующем: Install-WebApplicationProxy - CertificateThumbprint {SSLCert} - fsname fsname - TrustCred $trustcred  

7.  Теперь на сервере федерации Windows Server 2016 откройте управления AD FS.  Обратите внимание, что теперь все узлы отображаются, поскольку основная задача была передана на этом сервере.  

    ![обновление](media/Upgrading-to-AD-FS-in-Windows-Server-2016/ADFS_Mixed_6.png)  

8.  С помощью установочного носителя Windows Server 2016 откройте командную строку и перейдите в каталог support\adprep.  Выполните следующую команду: adprep/forestprep.  

    ![обновление](media/Upgrading-to-AD-FS-in-Windows-Server-2016/ADFS_Mixed_7.png)  

9. По завершении выполнения команды adprep/domainprep  

    ![обновление](media/Upgrading-to-AD-FS-in-Windows-Server-2016/ADFS_Mixed_8.png)  

10. Теперь на сервере Windows Server 2016 откройте PowerShell и выполните следующий командлет: вызова AdfsFarmBehaviorLevelRaise  

    ![обновление](media/Upgrading-to-AD-FS-in-Windows-Server-2016/ADFS_Mixed_9.png)  

11. При появлении запроса введите Y. Повышение уровня начнется.  После выполнения этой процедуры были успешно поднять FBL.  

    ![обновление](media/Upgrading-to-AD-FS-in-Windows-Server-2016/ADFS_Mixed_10.png)  

> [!NOTE]  
> Если серверов AD FS используется SQL для конфигурации, новую базу данных manamgement создан с именем «AdfsConfiguraionV3». 

12. Теперь Если вы откроете управления AD FS, вы увидите новых узлов, которые были добавлены для AD FS в Windows Server 2016  

    ![обновление](media/Upgrading-to-AD-FS-in-Windows-Server-2016/ADFS_Mixed_12.png)  

13. Аналогичным образом, можно использовать командлет PowerShell: Get-AdfsFarmInformation, показывающего текущее FBL.  

    ![обновление](media/Upgrading-to-AD-FS-in-Windows-Server-2016/ADFS_Mixed_13.png)  
