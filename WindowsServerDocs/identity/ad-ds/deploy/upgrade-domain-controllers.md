---
title: "Обновление контроллеров домена до Windows Server 2016"
description: "В этом документе описывается, как выполнить обновление с Windows Server 2012 R2 до Windows Server 2016"
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 187972c2f44a4d7f91b1b3ac1c905529564cfa6d
ms.sourcegitcommit: f748c6c4ce700b0787ffdd1fca620c21c4331fd2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/21/2017
---
# <a name="upgrade-domain-controllers-to-windows-server-2016"></a>Обновление контроллеров домена до Windows Server 2016

Область применения: Windows Server 2016

Этот раздел содержит справочные сведения о доменных службах Active Directory в Windows Server 2016 и пояснения к процессу обновления контроллеров домена с Windows Server 2012 или Windows Server 2012 R2. 

## <a name="pre-requisites"></a>Необходимые компоненты
Рекомендуемым способом обновления домена является повышение уровня контроллеров домена, на которых выполняются более новые версии Windows Server и понижение уровня старых контроллеров домена при необходимости. Этот метод является предпочтительным для обновления операционной системы существующего контроллера домена. Далее приведены общие действия, которые необходимо выполнить до повышения уровня контроллера домена под управлением более новой версии Windows Server. 

1.  Убедитесь, что целевой сервер отвечает системным требованиям. 
2.  Проверка совместимости приложения. 
3.  Просмотрите рекомендации по переходу на Windows Server 2016 
4.  Проверьте параметры безопасности. Дополнительные сведения см. в разделе [нерекомендуемые компоненты и изменения в поведении, связанные с AD DS в Windows Server 2016](../../../get-started\deprecated-features.md). 
5.  Проверьте подключение к целевому серверу с компьютера, на котором планируется запускать установку. 
6.  Проверьте доступность необходимых ролей хозяина операций: 
    - Для установки первого контроллера домена под управлением Windows Server 2016 в существующем домене и лесу, компьютер, на котором проводится установка должен быть подключен к **хозяин схемы** чтобы выполнять команду adprep/forestprep и хозяином инфраструктуры, чтобы выполнять команду adprep/domainprep. 
    - Для установки первого контроллера домена в домене, где схема леса уже расширена, требуется только подключение к хозяину инфраструктуры. 
    - Для установки или удаления домена в существующем лесу, требуется подключение к **хозяина именования доменов**. 
    - Для любой установки контроллера домена также требуется подключение к **хозяина RID.** 
    - При установке первого контроллера домена только для чтения в существующем лесу требуется подключение к хозяину инфраструктуры для каждого раздела каталога приложений, также известный как Недоменный контекст именования или NDNC. 

### <a name="installation-steps-and-required-administrative-levels"></a>Инструкции по установке и необходимые административные уровни
В следующей таблице приведены действия по обновлению и необходимые разрешения для выполнения этих действий

|Действие установки|Требования к учетным данным|
| ----- | ----- |
|Установка нового леса|Локальный администратор на целевом сервере|
|Установка нового домена в существующем лесу|Администраторы предприятия|
|Установка дополнительного контроллера домена в существующем домене|Администраторы домена|
|Запустите команду adprep/forestprep|"Администраторы схемы", "Администраторы предприятия" и "Администраторы домена"|
|Запустите команду adprep/domainprep|Администраторы домена|
|Запустите команду adprep/domainprep / gpprep|Администраторы домена|
|Выполнение команды adprep/rodcprep|Администраторы предприятия|

Дополнительные сведения о новых возможностях в Windows Server 2016 см. в разделе [новые возможности Windows Server 2016](../../../get-started/what-s-new-in-windows-server-2016.md).



## <a name="supported-in-place-upgrade-paths"></a>Поддерживаемые варианты обновления на месте
Контроллеры домена под управлением 64-разрядных версиях Windows Server 2012 или Windows Server 2012 R2 можно обновить до Windows Server 2016. Так как Windows Server 2016 может быть получено только в 64-разрядной версии поддерживает только 64-разрядной версии обновления.

|Если вы используете этот выпуск:|Можно обновить до следующих выпусков:|
| ----- | ----- |   
|Windows Server 2012 Standard|Windows Server 2016 Standard или Datacenter|   
|Windows Server 2012 Datacenter|Windows Server 2016 Datacenter| 
|Windows Server 2012 R2 Standard|Windows Server 2016 Standard или Datacenter|    
|Windows Server 2012 R2 Datacenter|Windows Server 2016 Datacenter|  
|Windows Server 2012 R2 Essentials|Windows Server 2016 Essentials|  
|Windows Storage Server 2012 Standard|Windows Storage Server 2016 Standard| 
|Windows Storage Server 2012 Workgroup|Windows Storage Server 2016 Workgroup|   
|Windows Storage Server 2012 R2 Standard|Windows Storage Server 2016 Standard|  
|Windows Storage Server 2012 R2 Workgroup|Windows Storage Server 2016 Workgroup|    

Дополнительные сведения о поддерживаемых путях обновления см. в разделе [поддерживаемые пути обновления](../../../get-started/supported-upgrade-paths.md)

## <a name="adprep-and-domainprep"></a>Средство Adprep и Domainprep
Если вы выполняете обновление на месте существующего контроллера домена в операционную систему Windows Server 2016, необходимо будет вручную выполнить команду adprep/forestprep и команду adprep/domainprep.  Команды adprep/forestprep необходимо выполнить только один раз в лесу.  Команды adprep/domainprep необходимо выполнить один раз в каждом домене, в котором имеется контроллеры домена, при обновлении до Windows Server 2016.

Если вы повышаете на новый сервер Windows Server 2016, необходимо запускать их вручную.  Они интегрированы в PowerShell и диспетчера сервера взаимодействия.

Дополнительные сведения о запуске программы adprep см [работа с программой Adprep.exe](https://technet.microsoft.com/library/dd464018.aspx) 


## <a name="functional-level-features-and-requirements"></a>Возможности режимов работы и требования
Windows Server 2016 требуется режим работы леса Windows Server 2003. То есть перед добавлением контроллера домена под управлением Windows Server 2016 в существующем лесу Active Directory режим работы леса должен быть Windows Server 2003 или выше. Если лес содержит контроллеры домена под управлением Windows Server 2003 или новее, но режим работы леса соответствует Windows 2000, то установка также блокируется. 

Контроллеры домена Windows 2000 необходимо удалить, прежде чем добавлять в лес контроллеры домена Windows Server 2016. В этом случае необходимо учитывайте следующие рабочего процесса: 


1. Установите контроллеры домена под управлением Windows Server 2003 или более поздней версии. Эти контроллеры домена можно развертывать в ознакомительной версии Windows Server. На этом этапе также требуется под управлением adprep.exe для этого выпуска операционной системы в качестве обязательного компонента. 
2.  Удалите контроллеры домена Windows 2000. В частности, надлежащим образом понизьте роль или принудительно удалите контроллеры домена Windows Server 2000 из домена и используемых Active Directory-пользователи и компьютеры, чтобы удалить учетные записи контроллеров домена для всех удаленных контроллеров домена. 
3.  Повышение режима работы леса до Windows Server 2003 или более поздней версии. 
4.  Установите контроллеры домена под управлением Windows Server 2016. 
5.  Удалите контроллеры домена под управлением более ранних версий Windows Server. 

### <a name="rolling-back-functional-levels"></a>Откат функциональных уровней

Установив определенное значение режима работы леса (FFL), не удается откатить или понизить режим работы леса, за исключением следующих: 

- Если вы проводите обновление с Windows Server 2012 R2 FFL, его можно понизить к Windows Server 2012 R2. 
- Если вы проводите обновление с Windows Server 2008 R2 FFL, его можно понизить к Windows Server 2008 R2.

Установив определенное значение режима работы домена, не удается откатить или понизить режим работы домена, за исключением следующих: 

- При Повышение режима работы домена до Windows Server 2016, и если режим работы леса Windows Server 2012 или менее, у вас есть возможность выполнения отката режима работы домена обратно в Windows Server 2012 или Windows Server 2012 R2 

Дополнительные сведения о возможностях, доступных при более низких функциональных уровнях см. в разделе [режимах работы доменных служб общее представление о Active Directory (AD DS)](../active-directory-functional-levels.md). 
 
## <a name="ad-ds-interoperability-with-other-server-roles-and-windows-operating-systems"></a>AD DS взаимодействия с другими ролями сервера и операционными системами Windows
AD DS не поддерживается в следующих операционных системах Windows: 


- Windows MultiPoint Server 
- Windows Server 2016 Essentials 

AD DS не удается установить на сервере, на котором выполняются следующие роли сервера или служб ролей: 

- Microsoft Hyper-V Server 2016
- Посредника подключений к удаленному рабочему столу 

## <a name="administration-of-windows-server-2016-servers"></a>Администрирование серверов Windows Server 2016
Используйте удаленный средства администрирования сервера для Windows 10 для управления контроллерами домена и другими серверами под управлением Windows Server 2016. Windows Server 2016 Server средства удаленного администрирования можно запустить на компьютере под управлением Windows 10. 

## <a name="step-by-step-for-upgrading-to-windows-server-2016"></a>Пошаговое руководство по обновлению до Windows Server 2016
Ниже приведен простой пример обновления Contoso леса Windows Server 2012 R2 до Windows Server 2016.

![Обновление](media/Upgrade-Domain-Controllers-to-Windows-Server-2016/upgrade1.png)

1.  Присоединение Windows Server 2016 в лес. Выполните перезагрузку. 
![Обновление](media/Upgrade-Domain-Controllers-to-Windows-Server-2016/upgrade2.png)
2.  Войдите на новый Windows Server 2016 с учетной записью администратора домена.
3.  В **диспетчера сервера**в разделе **Добавить роли и компоненты**, установить **доменных служб Active Directory** в Windows Server 2016. Это будет автоматически выполнения команды adprep на 2012 R2 леса и домена.
![Обновление](media/Upgrade-Domain-Controllers-to-Windows-Server-2016/upgrade3.png) 
4.  В **диспетчера сервера**, щелкните желтый треугольник и в раскрывающемся списке выберите **повысить уровень сервера до контроллера домена**. 
![Обновление](media/Upgrade-Domain-Controllers-to-Windows-Server-2016/upgrade4.png)
5.  На **конфигурации развертывания** выберите **добавить контроллер домена в существующий лес** и затем нажмите кнопку Далее. 
![Обновление](media/Upgrade-Domain-Controllers-to-Windows-Server-2016/upgrade5.png)
6.  На **параметры контроллера домена** введите **режима восстановления служб каталогов (DSRM)** пароль и нажмите кнопку Далее. 
7.  Для оставшейся части окна нажмите кнопку **Далее**. 
8.  На **проверка готовности к установке** нажмите кнопку **установить**. После завершения перезагрузки может снова войдите.
9.  На сервере Windows Server 2012 R2 в **диспетчера сервера**, установите средства, **модуль Active Directory для Windows PowerShell**. 
![Обновление](media/Upgrade-Domain-Controllers-to-Windows-Server-2016/upgrade6.png)
10. В PowerShell windows используйте Move-ADDirectoryServerOperationMasterRole для перемещения ролей FSMO. Вы можете ввести имя каждого - OperationMasterRole или числа используются для указания роли. Номера. Дополнительные сведения см. [ADDirectoryServerOperationMasterRole перемещения](https://technet.microsoft.com/library/hh852302.aspx)

``` powershell
Move-ADDirectoryServerOperationMasterRole -Identity "DC-W2K16" -OperationMasterRole 0,1,2,3,4
```

![Обновление](media/Upgrade-Domain-Controllers-to-Windows-Server-2016/upgrade7.png)</br>
11. Проверка ролей были перемещены, перейдя к серверу Windows Server 2016 в **диспетчера сервера**в разделе **средства**выберите **модуль Active Directory для Windows PowerShell**. Используйте `Get-ADDomain` и `Get-ADForest` командлетов для просмотра владельцев ролей FSMO.
![Обновление] (media/Upgrade-Domain-Controllers-to-Windows-Server-2016/upgrade8.png)
! [Обновления](media/Upgrade-Domain-Controllers-to-Windows-Server-2016/upgrade9.png)
12. Понижение уровня и удаление контроллера домена Windows Server 2012 R2. Сведения о понижении роли контроллера домена см. в разделе [понижение уровня контроллеров домена и доменов](../../ad-ds/deploy/Demoting-Domain-Controllers-and-Domains--Level-200-.md)
13. После понижения роли сервера и его удаления может повысить режим работы леса и режим работы домена до Windows Server 2016.


## <a name="next-steps"></a>Дальнейшие действия
-   [Новые возможности в домене Active Directory, службы установки и удаления](../../ad-ds/deploy/What-s-New-in-Active-Directory-Domain-Services-Installation-and-Removal.md)  
-   [Установка доменных служб Active Directory & #40; Уровень 100 & #41;](../../ad-ds/deploy/Install-Active-Directory-Domain-Services--Level-100-.md)     
-   [Режимы работы Windows Server 2016](../../ad-ds/Windows-Server-2016-Functional-Levels.md)  
