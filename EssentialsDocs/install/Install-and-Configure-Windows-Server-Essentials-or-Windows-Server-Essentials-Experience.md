---
title: "Установка и настройка Windows Server Essentials или Windows Server Essentials Experience"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 48ea6cd4-3955-4aaf-9236-2515a6c3e730
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 8a2310b178663c6ca32a4e07d11656f1aaf2a11b
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="install-and-configure-windows-server-essentials-or-windows-server-essentials-experience"></a>Установка и настройка Windows Server Essentials или Windows Server Essentials Experience

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Windows Server Essentials является идеальный сервер для малого бизнеса с максимум 25 пользователей и 50 устройств. Для организаций с до 100 пользователей и 200 устройств теперь можно использовать Windows Server 2012 R2 с установленной ролью Windows Server Essentials Experience. В этом разделе рассматриваются оба варианта.  
  
Режим Windows Server Essentials — это роль в Windows Server 2016, которая позволяет использовать преимущества всех компонентов (например, удаленный веб-доступ и резервное копирование), которые доступны в Windows Server Essentials без каких-либо блокировок и ограничений в Windows Server Essentials. Эта роль сервера также доступен в Windows Server Essentials и включено по умолчанию.
  
Перед установкой роли режим Essentials или Windows Server Essentials, учитывайте следующие ограничения.  
  
|Windows Server Essentials Experience в Windows Server Essentials|Windows Server Essentials Experience в Windows Server 2016
|----|----|
|-Должна быть контроллером домена в корне леса и домена и выполнять все роли FSMO.<br /><br /> -Не может быть установлен в среде с существующим доменом Active Directory (тем не менее, есть льготный период длительностью 21 день для осуществления миграции).|-Не требуется быть контроллером домена в том случае, если он установлен в среде с существующим доменом Active Directory.<br /><br /> -Если домена Active Directory не существует, Установка роли создаст домен Active Directory, и сервер станет контроллером домена в корне леса и домена, с ролями FSMO.  
|Можно развернуть только в одном домене.|Можно развернуть только в одном домене.  
|Контроллер домена только для чтения не может существовать в вашем домене.|Контроллер домена только для чтения не может существовать в вашем домене.

> [!NOTE]
>  Для загрузки ознакомительных версий операционных систем, посетите Центр пробного по TechNet:  
>   
>  [Скачать Windows Server 2016](https://www.microsoft.com/evalcenter/evaluate-windows-server-2016)  
>   
>  [Скачать Windows Server Essentials](https://www.microsoft.com/evalcenter/evaluate-windows-server-2016-essentials)
  
## <a name="installation-options"></a>Варианты установки  
 Этот документ содержит пошаговые инструкции по установке и настройке Windows Server Essentials. В зависимости от сетевой среды имеются следующие доступные параметры установки:  
  
-    Windows Server Essentials (с ролью интерфейса Windows Server Essentials, включена по умолчанию)  
  
-    Windows Server 2016 с установленной ролью Windows Server Essentials Experience  
 
|Среда развертывания|Описание|См. также|  
|----------------------------|-----------------|---------------------|  
|Новая среда Active Directory|Можно установить Windows Server Essentials для создания новой среды Active Directory.|[Развертывание Windows Server Essentials для настройки новой среды Active Directory](Install-and-Configure-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md#BKMK_NewAD)|  
|Существующую среду Active Directory|Можно установить Windows Server Essentials в существующей среде Active Directory.|[Развертывание Windows Server Essentials в существующей среде Active Directory](Install-and-Configure-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md#BKMK_ExistingAD)|  
|Виртуальная среда|Можно развернуть Windows Server Essentials в качестве виртуальной машины.|[Виртуализация среды](Install-and-Configure-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md#BKMK_VirtualWSE)|  
|Автоматизированное развертывание|С помощью Windows PowerShell можно автоматизировать развертывание Windows Server Essentials.|[Установка и настройка Windows Server Essentials с помощью Windows PowerShell](Install-and-Configure-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md#BKMK_PowerShell)|  
  
## <a name="before-you-begin"></a>Перед началом работы  
 Перед началом установки необходимо ознакомиться со следующей документацией:  
  
-   [Обзор продукта Windows Server Essentials](https://www.microsoft.com/server-cloud/windows-server-essentials/windows-server-2012-r2-essentials.aspx)  
  

-   [Требования к системе для Windows Server Essentials](../get-started/system-requirements.md)   

  
##  <a name="BKMK_NewAD"></a>Развертывание Windows Server Essentials для настройки новой среды Active Directory  
 Windows Server Essentials позволяет быстро настроить среду Active Directory и соответствующие серверные функции.  
  
###  <a name="BKMK_WSEDeploy"></a>Развертывание Windows Server Essentials  
 Если вы используете Windows Server Essentials, Windows Server Essentials Experience уже включен. Тем не менее необходимо выполнить некоторые действия для настройки сервера.  
  
##### <a name="to-configure-windows-server-essentials-on-a-physical-server"></a>Чтобы настроить Windows Server Essentials на физическом сервере  
  
1.  После Windows **приветствия** страницы, **мастер настройки Windows Server Essentials** отображается на рабочем столе.  
  
2.  Следуйте инструкциям для завершения работы мастера следующим образом:  
  
    1.  На **Настройка Windows Server Essentials** щелкните **Далее**.  
  
    2.  В **параметры времени**, проверьте правильность даты, время и часовой пояс и нажмите кнопку **Далее**.  
  
    3.  В **сведений о компании**, введите название вашей компании, такие как **Contoso, Ltd.**, а затем нажмите кнопку **Далее**. При необходимости можно изменить внутреннее имя домена и имя сервера.  
  
    4.  В **создать администратора сети**, введите новое имя учетной записи администратора и пароль.  
  
        > [!NOTE]
        >  Не используйте значение по умолчанию **администратора** имя и пароль учетной записи.  
  
    5.  Нажмите кнопку **Настройка**.  
  
3.  Сервер перезагрузится несколько раз во время процесса настройки и вход в систему будет производиться автоматически до завершения настройки. Этот процесс занимает примерно 20 минут.  
  
4.  На рабочем столе щелкните значок панели мониторинга для запуска панели мониторинга. На **Главная** завершите **Приступая к работе** задачи, перечисленные на **установки** вкладку.  
  
 После завершения конфигурации сервера, сервера, на котором работает Windows Server Essentials будет настраиваться как контроллер домена.  
  
###  <a name="BKMK_DeployWSERole"></a>Развертывание роли Windows Server Essentials Experience в Windows Server 2012 R2 Standard и Datacenter  
 Включение и Настройка роли Windows Server Essentials Experience в Windows Server 2012 R2 Standard или Windows Server 2012 R2 Datacenter с помощью следующей процедуры можно использовать диспетчер сервера.  
  
##### <a name="to-deploy-the-windows-server-essentials-experience-role-in-windows-server-2012-r2"></a>Развертывание роли Windows Server Essentials Experience в Windows Server 2012 R2  
  
1.  Войдите сервер с правами локального администратора.  
  
2.  Откройте **диспетчера сервера**, а затем нажмите кнопку **Добавить роли и компоненты**.  
  
3.  В **Выбор ролей сервера**выберите **Windows Server Essentials Experience** роли. В диалоговом окне выберите **добавить компоненты**, а затем нажмите кнопку **Далее**.  
  
4.  В **функции**, нажмите кнопку **Далее**.  
  
5.  Просмотрите **Windows Server Essentials Experience** описание роли, а затем щелкните **Далее**.  
  
6.  На следующих страницах, нажмите кнопку **Далее**, а затем на странице подтверждения нажмите кнопку **установить**.  
  
7.  После завершения установки Windows Server Essentials Experience должно быть указано как роль сервера в диспетчере сервера.  
  
8.  В области уведомлений в диспетчере сервера, установите соответствующий флажок и нажмите кнопку **Настройка Windows Server Essentials**.  
  
9. (Необязательно) При необходимости измените имя сервера.  
  
    > [!IMPORTANT]
    >  После настройки Windows Server Essentials нельзя изменить имя сервера.  
  

10. Следуйте инструкциям мастера настройки Windows Server Essentials, как описано ранее в [развертывание Windows Server Essentials](Install-and-Configure-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md#BKMK_WSEDeploy) раздела.  

10. Следуйте инструкциям мастера настройки Windows Server Essentials, как описано ранее в [развертывание Windows Server Essentials](Install-and-Configure-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md#BKMK_WSEDeploy) раздела.  

  
##  <a name="BKMK_ExistingAD"></a>Развертывание Windows Server Essentials в существующей среде Active Directory  
 Также можно развернуть Windows Server Essentials, если в организации уже есть существующую среду Active Directory. Кроме того можно выбрать, если требуется выполнить развертывание Windows Server Essentials в качестве контроллера домена.  
  
> [!IMPORTANT]
>  Этот параметр доступен только в том случае, если развертывание роли Windows Server Essentials Experience в Windows Server 2012 R2 Standard или Windows Server 2012 R2 Datacenter.  
  
#### <a name="to-deploy-windows-server-essentials-in-an-existing-active-directory-environment"></a>Развертывание Windows Server Essentials в существующей среде Active Directory  
  
1.  (Необязательно) При необходимости измените имя сервера.  
  
    > [!IMPORTANT]
    >  После настройки Windows Server Essentials нельзя изменить имя сервера.  
  
2.  Присоединение сервера под управлением Windows Server Essentials к существующему домену следующим образом.  
  
    1.  Если этот сервер должен быть контроллером домена, настройте сервер как реплику контроллера домена.  
  
    2.  Если вы не хотите, чтобы этот сервер должен быть контроллером домена, присоедините сервер к вашему домену с помощью собственных средств Windows.  
  
3.  Перезагрузите сервер и войдите на сервер с правами администратора домена.  
  
4.  Откройте диспетчер сервера и нажмите кнопку **Добавить роли и компоненты**.  
  
5.  На последующих страницах, нажмите кнопку **Далее**.  
  
6.  В **Выбор ролей сервера**выберите **Windows Server Essentials Experience**. В диалоговом окне выберите **добавить компоненты**, а затем нажмите кнопку **Далее**.  
  
7.  В **функции**, нажмите кнопку **Далее**.  
  
8.  Просмотрите **Windows Server Essentials Experience** описание, а затем щелкните **Далее**.  
  
9. На следующих страницах, нажмите кнопку **Далее**, а затем на странице подтверждения нажмите кнопку **установить**.  
  
10. После завершения установки Windows Server Essentials Experience будет указана в качестве роли сервера в диспетчере сервера.  
  
11. В области уведомлений в **диспетчера сервера**, установите соответствующий флажок и нажмите кнопку **Настройка Windows Server Essentials**.  
  
12. Следуйте инструкциям мастера настройки Windows Server Essentials. В зависимости от конфигурации Active Directory вы получите уведомление о настройке Windows Server Essentials на контроллере домена или члена домена. Нажмите кнопку **Настройка** Чтобы приступить к настройке. Процесс настройки занимает около 10 минут.  
  
##  <a name="BKMK_VirtualWSE"></a>Виртуализация среды  
  Виртуальные машины можно запустить Windows Server Essentials, Windows Server 2012 R2 Standard и Windows Server 2012 R2 Datacenter. Виртуальные машины запускаются с помощью средства управления Hyper-V на сервере с Hyper-V. С точки зрения лицензирования Windows Server Essentials позволяет настроить роль Hyper-V и создать виртуальную среду. Лицензия позволяет настроить другую гостевую систему под управлением Windows Server Essentials. В зависимости от поставщика системы «конфигурации s™, Windows Server Essentials позволяет легко настроить виртуальную среду.  
  
#### <a name="to-deploy-windows-server-essentials-as-a-virtual-machine"></a>Развертывание Windows Server Essentials в качестве виртуальной машины  
  
1.  После страницы приветствия Windows (в зависимости от поставщика «о s конфигурации системы) **перед началом** страницы предоставляет возможность настроить Windows Server Essentials как виртуальный экземпляр или на физическом оборудовании. Наличие данных параметров определяется поставщиком Вашей системы и при использовании обоих вариантов может быть не всегда доступны. Для установки Windows Server Essentials в качестве виртуальной машины в **Установка Windows Server Essentials**выберите **установить как виртуальный экземпляр**, а затем нажмите кнопку **Настройка**.  
  
2.  Мастер подготовит виртуальной машины, которая занимает около пяти минут.  
  

3.  Затем настройте Windows Server Essentials, как описано ранее в [развертывание Windows Server Essentials](Install-and-Configure-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md#BKMK_WSEDeploy) раздела.  

3.  Затем настройте Windows Server Essentials, как описано ранее в [развертывание Windows Server Essentials](Install-and-Configure-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md#BKMK_WSEDeploy) раздела.  

  
##  <a name="BKMK_PowerShell"></a>Установка и настройка Windows Server Essentials с помощью Windows PowerShell  
 С помощью командлетов Windows PowerShell можно автоматизировать установку Windows Server Essentials.  
  
#### <a name="to-install-windows-server-essentials-by-using-windows-powershell"></a>Установка Windows Server Essentials с помощью Windows PowerShell  
  
1.  Откройте консоль Windows PowerShell из командной строки с повышенными привилегиями.  
  
2.  Установка роли Windows Server Essentials Experience с помощью следующей команды:  
  
    ```  
    Add-WindowsFeature ServerEssentialsRole  
    ```  
  
3.  Запустите `Get-Help Start-WssConfigurationService`.  
  
    1.  Выполните следующую команду, чтобы начать настройку Windows Server Essentials в качестве контроллера домена:  
  
        ```  
        Start-WssConfigurationService -CompanyName "ContosoTest" -DNSName "ContosoTest.com" -NetBiosName "ContosoTest" -ComputerName "YourServerName  œNewAdminCredential $cred  
        ```  
  
    2.  Выполните следующую команду, чтобы начать настройку Windows Server Essentials в качестве члена домена. Необходимо быть членом группы администраторов предприятия и группы администраторов домена в Active Directory для выполнения этой задачи:  
  
        ```  
        Start-WssConfigurationService  œCredential <Your Credential>  
  
        ```  
  
4.  Отслеживайте ход выполнения установки с помощью следующих команд:  
  
    -   Состояние установки отображается индикатора выполнения выполните команду `Get-WssConfigurationStatus  œShowProgress`.  
  
    -   Для получения немедленных сведений о процессе без индикатора выполнения, выполните `Get-WssConfigurationStatus`.  
  
## <a name="see-also"></a>См. также:  
  
-   [Новые возможности Windows Server Essentials](../get-started/what-s-new.md)  
  
-   [Установка Windows Server Essentials](Install-Windows-Server-Essentials.md)  
  
-   [Начало работы с Windows Server Essentials](../get-started/get-started.md)
