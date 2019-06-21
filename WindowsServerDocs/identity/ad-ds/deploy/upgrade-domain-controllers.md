---
title: Обновление контроллеров домена до Windows Server 2016
description: В этом документе описывается процесс обновления с Windows Server 2012 R2 до Windows Server 2016
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 572f923c33739b854808372a826e9c9bbc6aaca3
ms.sourcegitcommit: afb0602767de64a76aaf9ce6a60d2f0e78efb78b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/20/2019
ms.locfileid: "67280855"
---
# <a name="upgrade-domain-controllers-to-windows-server-2016"></a>Обновление контроллеров домена до Windows Server 2016

Область применения. Windows Server 2016

В этом разделе содержатся сведения о доменных службах Active Directory в Windows Server 2016 и пояснения к процессу обновления контроллеров домена с Windows Server 2012 или Windows Server 2012 R2. 

## <a name="pre-requisites"></a>Предварительные требования
Рекомендуемым способом обновления домена является повышение уровня контроллеров домена, которые выполняются более новые версии Windows Server и понижение уровня старых контроллеров домена, при необходимости. Этот метод является предпочтительным для обновления операционной системы существующего контроллера домена. Далее приведены общие действия до повышения уровня контроллера домена, под управлением более новой версии Windows Server: 

1. Убедитесь, что целевой сервер отвечает требованиям к системе. 
2. Проверка совместимости приложений. 
3. Просмотрите рекомендации по переходу на Windows Server 2016 
4. Проверьте параметры безопасности. Дополнительные сведения см. в разделе [нерекомендуемые компоненты и изменения в поведении, связанные с AD DS в Windows Server 2016](https://docs.microsoft.com/windows-server/get-started/deprecated-features). 
5. Проверьте подключение к целевому серверу с компьютера, где планируется установка. 
6. Проверьте доступность необходимых ролей хозяина операций. 
   - Для установки первого контроллера домена под управлением Windows Server 2016 в существующем домене и лесу, компьютер, на котором проводится установка должен быть подключен к **хозяин схемы** , чтобы выполнять команду adprep/forestprep и хозяин инфраструктуры Чтобы выполнить команду adprep/domainprep. 
   - Для установки первого контроллера домена в домене, где схема леса уже расширена, требуется только подключение к хозяину инфраструктуры. 
   - Чтобы установить или удалить домен в существующем лесу, требуется подключение к **хозяина именования доменов**. 
   - Любой установки контроллера домена также требуется подключение к **хозяина RID.** 
   - В случае установки первого контроллера домена только для чтения в существующем лесу требуется подключение к хозяину инфраструктуры для каждого раздела каталога приложений (недоменный контекст именования, или NDNC). 

### <a name="installation-steps-and-required-administrative-levels"></a>Действия по установке и необходимые уровни администрирования
Ниже приведены действия по обновлению и необходимые разрешения для выполнения этих шагов

|Действие установки|Требования к учетным данным|
| ----- | ----- |
|Установка нового леса|Локальный администратор на целевом сервере|
|Установка нового домена в существующем лесу|Администраторы предприятия|
|Установка дополнительного контроллера домена в существующем домене|Администраторы домена|
|Выполнение команды adprep /forestprep|Администраторы схемы, администраторы предприятия и администраторы домена|
|Выполнение команды adprep /domainprep|Администраторы домена|
|Выполнение команды adprep /domainprep /gpprep|Администраторы домена|
|Выполнение команды adprep /rodcprep|Администраторы предприятия|

Дополнительные сведения о новых функциях в Windows Server 2016, см. в разделе [новые возможности в Windows Server 2016](../../../get-started/what-s-new-in-windows-server-2016.md).



## <a name="supported-in-place-upgrade-paths"></a>Поддерживаемые варианты обновления на месте
Контроллеры домена под управлением 64-разрядных версиях Windows Server 2012 или Windows Server 2012 R2 могут обновляться до Windows Server 2016. Только 64-разрядной версии обновления поддерживаются, так как Windows Server 2016 может быть получено только в 64-разрядной версии.

|Используемый выпуск|Доступно обновление до следующих выпусков|
| ----- | ----- |   
|Windows Server2012 Standard|Windows Server2016 Standard или Datacenter|   
|Windows Server 2012 Datacenter|Windows Server 2016 Datacenter| 
|Windows Server 2012 R2 Standard|Windows Server2016 Standard или Datacenter|    
|Windows Server 2012 R2 Datacenter|Windows Server 2016 Datacenter|  
|Windows Server 2012 R2 Essentials|Windows Server2016 Essentials|  
|Windows Storage Server 2012 Standard|Windows Storage Server2016 Standard| 
|Windows Storage Server 2012 Workgroup|Windows Storage Server2016 Workgroup|   
|Windows Storage Server 2012 R2 Standard|Windows Storage Server2016 Standard|  
|Windows Storage Server 2012 R2 Workgroup|Windows Storage Server2016 Workgroup|    

Дополнительные сведения о поддерживаемых способах обновления см. в разделе [поддерживаемые пути обновления](../../../get-started/supported-upgrade-paths.md)

## <a name="adprep-and-domainprep"></a>Adprep и Domainprep
Если вы выполняете обновление на месте существующего контроллера домена в операционную систему Windows Server 2016, необходимо будет вручную запустить команду adprep/forestprep и команду adprep/domainprep.  Команды adprep/forestprep необходимо запустить только один раз в лесу.  Команду adprep/domainprep необходимо запустить один раз в каждом домене, в котором у вас есть контроллеры домена, при обновлении до Windows Server 2016.

При распространении на новый сервер Windows Server 2016, не нужно запускать вручную.  Они интегрированы в PowerShell и работа диспетчера сервера.

Дополнительные сведения о запуске программы adprep см. в разделе [работа с программой Adprep.exe](https://technet.microsoft.com/library/dd464018.aspx) 


## <a name="functional-level-features-and-requirements"></a>Возможности режимов работы и требования
Windows Server 2016 требуется режим работы леса Windows Server 2003. То есть перед добавлением контроллера домена под управлением Windows Server 2016 в существующем лесу Active Directory режим работы леса должен быть Windows Server 2003 или более поздней версии. Если в лесу есть контроллеры домена под управлением Windows Server 2003 или новее, но режим работы леса соответствует Windows 2000, то установка также блокируется. 

Контроллеры домена Windows 2000 необходимо удалить перед добавлением в лес контроллеры домена Windows Server 2016. В этом случае порядок действий будет следующим. 


1. Установите контроллеры домена под управлением Windows Server 2003 или более поздней версии. Эти контроллеры домена можно развертывать в ознакомительной версии Windows Server. Этот шаг также требует выполнение adprep.exe для этого выпуска операционной системы как необходимый компонент. 
2.  Удалите контроллеры домена под управлением Windows 2000. В частности, надлежащим образом понизьте уровень контроллеров домена под управлением Windows Server 2000 или принудительно удалите их из домена и при помощи компонента "Пользователи и компьютеры Active Directory" удалите учетные записи для всех удаленных контроллеров домена. 
3.  Повысьте режим работы леса до Windows Server 2003 или выше. 
4.  Установите контроллеры домена под управлением Windows Server 2016. 
5.  Удалите контроллеры домена под управлением более ранних версий Windows Server. 

### <a name="rolling-back-functional-levels"></a>Откат режимы работы

После выбора режима работы леса (FFL) для определенного значения, нельзя откатить или понизить режим работы леса, за исключением следующих случаев: 

- Если при обновлении с Windows Server 2012 R2 FFL, его можно понизить к Windows Server 2012 R2. 
- Если при обновлении с Windows Server 2008 R2 FFL, его можно понизить обратно на Windows Server 2008 R2.

После выбора режима работы домена определенное значение, нельзя откатить или понизить режим работы домена, за исключением следующих случаев: 

- При повышении режима работы домена до Windows Server 2016 и если режим работы леса Windows Server 2012 или более ранней версии, у вас есть возможность выполнения отката режима работы домена обратно в Windows Server 2012 или Windows Server 2012 R2 

Дополнительные сведения о возможностях, доступных при более низких режимах работы, см. в разделе [Общее представление о режимах работы доменных служб Active Directory (AD DS)](../active-directory-functional-levels.md). 
 
## <a name="ad-ds-interoperability-with-other-server-roles-and-windows-operating-systems"></a>Взаимодействие доменных служб Active Directory с другими ролями сервера и операционными системами Windows
Доменные службы Active Directory не поддерживаются в следующих операционных системах Windows: 


- Windows MultiPoint Server 
- Windows Server2016 Essentials 

Доменные службы Active Directory нельзя установить на сервере, на котором выполняются следующие роли или службы ролей: 

- Microsoft Hyper-V Server 2016
- Посредник подключений к удаленному рабочему столу 

## <a name="administration-of-windows-server-2016-servers"></a>Администрирование серверов Windows Server 2016
Используйте удаленный сервер администрирования средств для Windows 10 для управления контроллерами домена и другими серверами под управлением Windows Server 2016. Windows Server 2016 средства удаленного администрирования сервера запускаются на компьютере под управлением Windows 10. 

## <a name="step-by-step-for-upgrading-to-windows-server-2016"></a>Пошаговое руководство по обновлению до Windows Server 2016
Ниже приведен простой пример обновление леса Contoso с Windows Server 2012 R2 до Windows Server 2016.

![Обновление с более ранней версии:](media/Upgrade-Domain-Controllers-to-Windows-Server-2016/upgrade1.png)

1. Присоединяйтесь к Windows Server 2016 для леса. Перезапустите при появлении запроса. 
   ![Обновление](media/Upgrade-Domain-Controllers-to-Windows-Server-2016/upgrade2.png)
2. Войдите на новый Windows Server 2016 с учетной записью администратора домена.
3. В **диспетчера серверов**в разделе **Добавить роли и компоненты**, установить **доменных служб Active Directory** в Windows Server 2016. Это будет автоматически запущена adprep на 2012 R2 леса и домена.
   ![Обновление](media/Upgrade-Domain-Controllers-to-Windows-Server-2016/upgrade3.png) 
4. В **диспетчера серверов**, щелкните желтый треугольник и в раскрывающемся списке выберите **повысить уровень сервера до контроллера домена**. 
   ![Обновление](media/Upgrade-Domain-Controllers-to-Windows-Server-2016/upgrade4.png)
5. На **конфигурация развертывания** выберите **добавить контроллер домена в существующий лес** и нажмите кнопку Далее. 
   ![Обновление](media/Upgrade-Domain-Controllers-to-Windows-Server-2016/upgrade5.png)
6. На **параметры контроллера домена** введите **режима восстановления служб каталогов (DSRM)** пароль и нажмите кнопку Далее. 
7. Для оставшейся части окна нажмите кнопку **Далее**. 
8. На **проверка готовности к** щелкните **установить**. После завершения перезагрузки Вы можете войти снова.
9. На сервере Windows Server 2012 R2 в **диспетчера серверов**, установите средства, **модуль Active Directory для Windows PowerShell**. 
   ![Обновление](media/Upgrade-Domain-Controllers-to-Windows-Server-2016/upgrade6.png)
10. В PowerShell windows используйте Move-ADDirectoryServerOperationMasterRole для перемещения роли FSMO. Можно ввести имя каждого OperationMasterRole - или числа используются для указания роли. Дополнительные сведения см. в разделе [ADDirectoryServerOperationMasterRole перемещения](https://technet.microsoft.com/library/hh852302.aspx)

    ``` powershell
    Move-ADDirectoryServerOperationMasterRole -Identity "DC-W2K16" -OperationMasterRole 0,1,2,3,4
    ```

    ![Обновление с более ранней версии:](media/Upgrade-Domain-Controllers-to-Windows-Server-2016/upgrade7.png)</br>
11. Проверка ролей были перемещены, перейдя к серверу Windows Server 2016 в **диспетчера серверов**в разделе **средства**выберите **модуль Active Directory для Windows PowerShell**. Используйте `Get-ADDomain` и `Get-ADForest` командлетов для просмотра владельцев ролей FSMO.
    ![Обновление](media/Upgrade-Domain-Controllers-to-Windows-Server-2016/upgrade8.png)
    ![обновления](media/Upgrade-Domain-Controllers-to-Windows-Server-2016/upgrade9.png)
12. Понижение уровня и удаление контроллера домена Windows Server 2012 R2. Сведения о понижении роли контроллера домена, см. в разделе [понижение уровня контроллеров домена и доменов](../../ad-ds/deploy/Demoting-Domain-Controllers-and-Domains--Level-200-.md)
13. После понижения роли сервера и удалены вы можете отправить режиме работы леса и режимы работы домена до Windows Server 2016.


## <a name="next-steps"></a>Следующие шаги
-   [Новые возможности при установке и удалении доменных служб Active Directory](../../ad-ds/deploy/What-s-New-in-Active-Directory-Domain-Services-Installation-and-Removal.md)  
-   [Установка доменных служб Active Directory &#40;уровень 100&#41;](../../ad-ds/deploy/Install-Active-Directory-Domain-Services--Level-100-.md)     
-   [Режимы работы Windows Server 2016](../../ad-ds/Windows-Server-2016-Functional-Levels.md)  
