---
title: "Настройка DirectAccess в Windows Server Essentials"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c959b6fc-c67e-46cd-a9cb-cee71a42fa4c
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: cc336dcd2a5418aa79254108c941a02147112e8f
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="configure-directaccess-in-windows-server-essentials"></a>Настройка DirectAccess в Windows Server Essentials

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Этот раздел содержит пошаговые инструкции по настройке DirectAccess в Windows Server Essentials для включения вашим мобильным сотрудникам подключаться к сети s организации из любого удаленного местоположения с доступом в Интернет без необходимости подключения к виртуальной частной сети (VPN). DirectAccess обеспечивает мобильных сотрудников работать в сети внутри и вне офиса со своих компьютеров с Windows 8.1, Windows 8 и Windows 7.  
  
 В Windows Server Essentials Если в домен входит более одного сервера Windows Server Essentials DirectAccess должна быть настроена на контроллере домена.  
  
> [!NOTE]
>  Этот раздел содержит инструкции по настройке DirectAccess в случае, если сервер Windows Server Essentials является контроллером домена. Если сервер Windows Server Essentials является членом домена, следуйте инструкциям, чтобы настроить DirectAccess на члене домена в [Добавление DirectAccess в развертывании существующего удаленного доступа (VPN)](https://technet.microsoft.com/library/jj574220.aspx) вместо.  
  
## <a name="process-overview"></a>Общие сведения о процессе  
 Чтобы настроить DirectAccess в Windows Server Essentials, выполните следующие действия.  
  
> [!IMPORTANT]
>  Прежде чем использовать процедуры, описанные в данном руководстве для настройки DirectAccess в Windows Server Essentials, необходимо включить на сервере VPN. Инструкции см. в разделе [управление VPN](Manage-VPN-in-Windows-Server-Essentials.md).  
  
-   [Шаг 1: Добавьте средства управления удаленным доступом к серверу](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_AddRAM)  
  
-   [Шаг 2: Изменение адреса сетевого адаптера сервера на статический IP-адрес](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_AddStaticIP)  
  
-   [Шаг 3: Подготовка сертификата и запись DNS для сервера сетевых расположений](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_DNS)  
  
    -   [Шаг 3a: Предоставление полных разрешений для прошедших проверку пользователей для шаблона сертификата веб-сервера](#BKMK_GrantFullPermissions)  
  
    -   [Шаг 3b: регистрация сертификата для сервера сетевых расположений с общим именем, которое невозможно разрешить из внешней сети](#BKMK_EnrollaCertificate)  
  
    -   [Шаг 3c: Добавление нового узла к DNS-серверу и сопоставление его с адресом сервера Windows Server Essentials](#BKMK_MapNewHosttoServerAddress)  
  
-   [Шаг 4: Создание группы безопасности для клиентских компьютеров DirectAccess](#BKMK_AddSecurityGroup)  
  
-   [Шаг 5: Включение и настройка DirectAccess](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_EnableConfigureDA)  
  
    -   [Шаг 5а: Включение DirectAccess через консоль управления удаленным доступом](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_EnableDA)  
  
    -   [Шаг 5б: Удаление недействительного параметра IPv6Prefix в объекте групповой Политики RRAS (только для Windows Server Essentials)](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_RemoveIPv6)  
  
    -   [Шаг 5В: разрешить клиентским компьютерам под управлением Windows 7 Корпоративная для использования DirectAccess](#BKMK_Step4cWindows7Setup)  
  
    -   [Шаг 5d: Настройка сервера сетевых расположений](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_NLS)  
  
    -   [Шаг 5д: Добавление раздела реестра для обхода сертификации ЦС при установке канала IPsec](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_CA)  
  
-   [Шаг 6: Настройка параметров таблицы политики разрешения имен для сервера DirectAccess](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_NRPT)  
  
-   [Шаг 7: Настройка правил брандмауэра TCP и UDP для объектов групповой политики сервера DirectAccess](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_TCPUDP)  
  
-   [Шаг 8: Изменение конфигурации DNS64 для ожидания передачи данных интерфейса IP-HTTPS](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_DNS64)  
  
-   [Шаг 9: Резервирование портов для службы WinNat](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_ExemptPort)  
  
-   [Шаг 10: Перезапуск службы WinNat](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_WinNAT)  
  
> [!NOTE]
>  [Приложение: Установка DirectAccess с помощью Windows PowerShell](#BKMK_AppendixBPowerShellScript) предоставляет сценарий Windows PowerShell, который можно использовать для выполнения установки DirectAccess.  
  
##  <a name="BKMK_AddRAM"></a>Шаг 1: Добавьте средства управления удаленным доступом к серверу  
  
#### <a name="to-add-remote-access-management-tools"></a>Чтобы добавить средства управления удаленным доступом  
  
1.  На сервере, в левом нижнем углу начальной страницы щелкните **диспетчера сервера** значок.  
  
     В Windows Server Essentials необходимо будет поиска для диспетчера сервера, чтобы открыть его. На начальной странице введите **диспетчера сервера**, а затем нажмите кнопку **диспетчера сервера** в результатах поиска. Чтобы поместить Диспетчер серверов на начальный экран, щелкните правой кнопкой мыши диспетчера серверов в результатах поиска и нажмите кнопку **закрепить на начальном экране**.  
  
2.  Если **контроля учетных записей** отображает предупреждающее сообщение, нажмите кнопку **Да**.  
  
3.  На панели мониторинга диспетчера серверов щелкните **управление**, а затем нажмите кнопку **Добавить роли и компоненты**.  
  
4.  В мастер добавления ролей и компонентов выполните следующие действия.  
  
    1.  На **типа установки** щелкните **Установка на основе ролей или компонентов**.  
  
    2.  На **страница выбора сервера** (или **Выбор целевого сервера** страницы в Windows Server Essentials), нажмите кнопку **выберите сервер из пула серверов**.  
  
    3.  На **функции** разверните **средства удаленного администрирования сервера (установлены)**, разверните **средства управления удаленным доступом (установлены)**, разверните **средства администрирования ролей (установлены)**, разверните **средства управления удаленным доступом**и выберите **графический интерфейс пользователя удаленного доступа и программы командной строки**.  
  
    4.  Следуйте инструкциям для завершения работы мастера.  
  
##  <a name="BKMK_AddStaticIP"></a>Шаг 2: Изменение адреса сетевого адаптера сервера на статический IP-адрес  
 DirectAccess необходим адаптер со статическим IP-адресом. Необходимо изменить IP-адрес локального сетевого адаптера на сервере.  
  
#### <a name="to-add-a-static-ip-address"></a>Добавление статического IP-адреса  
  
1.  На начальной странице откройте **панели управления**.  
  
2.  Нажмите кнопку **сеть и Интернет**, а затем нажмите кнопку **Просмотр состояния сети и задач**.  
  
3.  В области задач **сетями и общим доступом**, нажмите кнопку **изменение параметров адаптера**.  
  
4.  Щелкните правой кнопкой мыши локальный сетевой адаптер, а затем нажмите кнопку **свойства**.  
  
5.  На **сети** щелкните **Internet IP версии 4 (TCP/IPv4)**, а затем нажмите кнопку **свойства**.  
  
6.  На **Общие** щелкните **использовать следующий IP-адрес**, а затем введите IP-адрес, который вы хотите использовать.  
  
     Значение по умолчанию для маски подсети автоматически отображается в **маска подсети** поле. Примите значение по умолчанию или введите нужное значение маски подсети.  
  
7.  В **шлюз по умолчанию** введите IP-адрес шлюза по умолчанию.  
  
8.  В **предпочитаемый DNS-сервер** введите IP-адрес вашего DNS-сервера.  
  
    > [!NOTE]
    >  Используйте IP-адрес, который был назначен вашему сетевому адаптеру DHCP (например, 192.168.X.X) вместо замыкания на себя сети (например, 127.0.0.1). Чтобы узнать назначенный IP-адрес, запустите **ipconfig** в командной строке.  
  
9. В **Альтернативный DNS-сервер** введите IP-адрес альтернативного DNS-сервера, при их наличии.  
  
10. Нажмите кнопку **ОК**, а затем нажмите кнопку **закрыть**.  
  
> [!IMPORTANT]
>  Убедитесь, что вы маршрутизатор настроен на перенаправление портов 80 и 443 новый статический IP-адрес сервера.  
  
##  <a name="BKMK_DNS"></a>Шаг 3: Подготовка сертификата и запись DNS для сервера сетевых расположений  
 Чтобы подготовить сертификат и запись DNS для сервера сетевых расположений, выполните следующие задачи.  
  
-   [Шаг 3a: Предоставление полных разрешений для прошедших проверку пользователей для шаблона сертификата веб-сервера](#BKMK_GrantFullPermissions)  
  
-   [Шаг 3b: регистрация сертификата для сервера сетевых расположений с общим именем, которое невозможно разрешить из внешней сети](#BKMK_EnrollaCertificate)  
  
-   [Шаг 3c: Добавление нового узла к DNS-серверу и сопоставление его с адресом сервера Windows Server Essentials.](#BKMK_MapNewHosttoServerAddress)  
  
###  <a name="BKMK_GrantFullPermissions"></a>Шаг 3a: Предоставление полных разрешений для прошедших проверку пользователей для шаблона сертификата веб-сервера  
 Первая задача — Предоставление полных разрешений для проверки подлинности пользователей для шаблона сертификата веб-сервера s, в центре сертификации.  
  
####  <a name="BKMK_ToGrantFullPermissions"></a>Предоставление полных разрешений для пользователей с проверкой подлинности для веб-сервера s шаблона сертификата  
  
1.  На **запустить** странице откройте **сертификации**.  
  
2.  В дереве консоли в разделе **центр сертификации (локальный)**, разверните **< имя_сервера > кземпляр-ЦС**, щелкните правой кнопкой мыши **шаблонов сертификатов**, а затем нажмите кнопку **управление**.  
  
3.  В **центр сертификации (локальный)**, щелкните правой кнопкой мыши **веб-сервере**, а затем нажмите кнопку **свойства**.  
  
4.  В свойствах веб-сервера на **безопасности** щелкните **прошедшие проверку**, выберите **полный доступ**, а затем нажмите кнопку **ОК**.  
  
5.  Перезапустите **службы сертификатов Active Directory**. В панели управления откройте **просмотр локальных служб**. В списке служб щелкните правой кнопкой мыши **служб сертификатов Active Directory**, а затем нажмите кнопку **перезапустите**.  
  
###  <a name="BKMK_EnrollaCertificate"></a>Шаг 3b: регистрация сертификата для сервера сетевых расположений с общим именем, которое невозможно разрешить из внешней сети  
 Затем зарегистрируйте сертификат для сервера сетевых расположений с общим именем, которое невозможно разрешить из внешней сети.  
  
####  <a name="BKMK_ToEnrollaCertificate"></a>Чтобы зарегистрировать сертификат для сервера сетевых расположений  
  
1.  На **запустить** странице откройте **mmc** (консоль управления Microsoft).  
  
2.  Если **контроля учетных записей** появится предупреждающее сообщение, нажмите кнопку **Да**.  
  
     Открытие Microsoft Management Console (MMC).  
  
3.  На **файл** меню, нажмите кнопку **Добавление или удаление оснастки**.  
  
4.  В **добавить или удалить оснастку** выберите **сертификаты**, а затем нажмите кнопку **добавить**.  
  
5.  На **сертификаты оснастки** щелкните **учетной записи компьютера**, а затем нажмите кнопку **Далее**.  
  
6.  На **Выбор компьютера** щелкните **локального компьютера**, нажмите кнопку **Готово**, а затем нажмите кнопку **ОК**.  
  
7.  В дереве консоли разверните узел **сертификаты (локальный компьютер)**, разверните **личные**, щелкните правой кнопкой мыши **сертификаты**, а затем в **все задачи**, нажмите кнопку **запросить новый сертификат**.  
  
8.  Когда откроется мастер регистрации сертификатов, щелкните **Далее**.  
  
9. На **Выбор политики регистрации сертификатов** щелкните **Далее**.  
  
10. На **запрос сертификатов** выберите **веб-сервере** флажок и нажмите кнопку **требуется больше данных для регистрации этого сертификата**.  
  
11. В **свойства сертификата** введите следующие параметры для **имя субъекта**:  
  
    1.  Для **тип**выберите **общее имя**.  
  
    2.  Для **значение**, введите имя сервера сетевых расположений (например, DirectAccess-NLS.contoso.local) и нажмите кнопку **добавить**.  
  
    3.  Нажмите кнопку **ОК**, а затем нажмите кнопку **регистрация**.  
  
12. По завершении регистрации сертификата щелкните **Готово**.  
  
###  <a name="BKMK_MapNewHosttoServerAddress"></a>Шаг 3c: Добавление нового узла к DNS-серверу и сопоставление его с адресом сервера Windows Server Essentials  
 Для завершения настройки DNS необходимо добавить новый узел к DNS-серверу и сопоставление его с адресом сервера Windows Server Essentials.  
  
####  <a name="BKMK_ToMapNewHosttoServerAddress"></a>Сопоставление нового узла с адресом сервера Windows Server Essentials  
  
1.  На начальной странице откройте диспетчер DNS. Чтобы открыть диспетчер DNS, выполните поиск **dnsmgmt.msc**, а затем нажмите кнопку **dnsmgmt.msc** в списке результатов.  
  
2.  В дереве консоли диспетчера DNS разверните локальный сервер, затем **зоны прямого просмотра**, щелкните правой кнопкой мыши зону с суффиксом домена сервера и нажмите кнопку **новый узел (A или AAAA)**.  
  
3.  Введите имя и IP-адрес сервера (например, DirectAccess-NLS.contoso.local), а также соответствующий адрес сервера (например, 192.168.x.x).  
  
4.  Нажмите кнопку **добавить узел**, нажмите кнопку **ОК**, а затем нажмите кнопку **сделать**.  
  
##  <a name="BKMK_AddSecurityGroup"></a>Шаг 4: Создание группы безопасности для клиентских компьютеров DirectAccess  
 Затем создайте группу безопасности для клиентских компьютеров DirectAccess и затем добавить учетные записи компьютеров в группу.  
  
#### <a name="to-add-a-security-group-for-client-computers-that-use-directaccess"></a>Чтобы добавить группу безопасности для клиентских компьютеров, использующих DirectAccess  
  
1.  На панели мониторинга диспетчера серверов щелкните **средства**, а затем нажмите кнопку **Active Directory-пользователи и компьютеры**.  
  
    > [!NOTE]
    >  Если вы не видите **Active Directory-пользователи и компьютеры** на **средства** меню, необходимо установить компонент. Чтобы установить Active Directory-пользователи и группы, выполните следующий командлет Windows PowerShell с правами администратора: `Install-WindowsFeature RSAT-ADDS-Tools`. Дополнительные сведения см. в разделе [установки или удаления сервера средств удаленного администрирования](https://technet.microsoft.com/library/cc730825.aspx).  
  
2.  В дереве консоли разверните сервер, щелкните правой кнопкой мыши **пользователей**, нажмите кнопку **New**, а затем нажмите кнопку **группы**.  
  
3.  Введите имя группы, область действия и тип группы (необходимо создать группу безопасности), а затем нажмите кнопку **ОК**.  
  
 Добавляется в новую группу безопасности **пользователей** папки.  
  
#### <a name="to-add-computer-accounts-to-the-security-group"></a>Добавление учетных записей компьютеров в группу безопасности  
  
1.  На панели мониторинга диспетчера серверов щелкните **средства**, а затем нажмите кнопку **Active Directory-пользователи и компьютеры**.  
  
2.  В дереве консоли разверните узел сервера и нажмите кнопку **пользователей**.  
  
3.  В списке учетных записей пользователей и групп безопасности на сервере, щелкните правой кнопкой мыши созданную вами для DirectAccess группу безопасности, а затем нажмите кнопку **свойства**.  
  
4.  На **члены** щелкните **добавить**.  
  
5.  В диалоговом окне введите имена учетных записей компьютеров, которые вы хотите добавить в группу, разделяя их точкой с запятой (;). Нажмите кнопку **проверить имена**.  
  
6.  После проверки учетных записей компьютеров щелкните **ОК**. Нажмите кнопку **ОК** еще раз.  
  
> [!NOTE]
>  Можно также использовать **членом** вкладку в свойствах учетной записи компьютера, чтобы добавить учетную запись в группу безопасности.  
  
##  <a name="BKMK_EnableConfigureDA"></a>Шаг 5: Включение и настройка DirectAccess  
 Чтобы включить и настроить DirectAccess в Windows Server Essentials, необходимо выполнить следующие действия:  
  
-   [Шаг 5а: Включение DirectAccess через консоль управления удаленным доступом](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_EnableDA)  
  
-   [Шаг 5б: Удаление недействительного параметра IPv6Prefix в объекте групповой Политики RRAS (только для Windows Server Essentials)](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_RemoveIPv6)  
  
-   [Шаг 5В: разрешить клиентским компьютерам под управлением Windows 7 Корпоративная для использования DirectAccess](#BKMK_Step4cWindows7Setup)  
  
-   [Шаг 5d: Настройка сервера сетевых расположений](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_NLS)  
  
-   [Шаг 5д: Добавление раздела реестра для обхода сертификации ЦС при установке канала IPsec](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_CA)  
  
###  <a name="BKMK_EnableDA"></a>Шаг 5а: Включение DirectAccess через консоль управления удаленным доступом  
 Этот раздел содержит пошаговые инструкции по включению DirectAccess в Windows Server Essentials. Если вы еще не настроили VPN на сервере, вам необходимо сделать перед началом этой процедуры. Инструкции см. в разделе [управление VPN](Manage-VPN-in-Windows-Server-Essentials.md).  
  
##### <a name="to-enable-directaccess-by-using-the-remote-access-management-console"></a>Включение DirectAccess через консоль управления удаленным доступом  
  
1.  На начальной странице откройте **управления удаленным доступом**.  
  
2.  В мастере установки DirectAccess выполните следующие действия.  
  
    1.  Просмотрите **требования для DirectAccess**и нажмите кнопку **Далее**.  
  
    2.  На **Выбор групп** добавьте группу безопасности, созданную вами ранее для клиентов DirectAccess. (Если вы не создали группу безопасности, см. раздел [шаг 4: Создание группы безопасности для клиентов DirectAccess компьютеры](#BKMK_AddSecurityGroup) инструкции.)  
  
    3.  На **Выбор групп** щелкните **разрешить DirectAccess только для мобильных компьютеров** Если вы хотите разрешить мобильными компьютерам использовать DirectAccess для удаленного доступа к серверу, а затем нажмите кнопку **Далее**.  
  
    4.  В **топологии сети**, выберите топологию сервера и нажмите кнопку **Далее**.  
  
    5.  В **список поиска суффиксов DNS**, при необходимости, добавьте дополнительный DNS-суффикс для клиентских компьютеров и нажмите кнопку **Далее**.  
  
        > [!NOTE]
        >  По умолчанию мастер установки DirectAccess добавляет DNS-суффикс текущего домена. Тем не менее вы можете добавить другие при необходимости.  
  
    6.  Проверьте объекты групповой политики (GPO), будут применяться и при необходимости измените их.  
  
    7.  Нажмите кнопку **Далее**, а затем нажмите кнопку **Готово**.  
  
    8.  Перезапустите службу управления удаленным доступом, выполнив следующую команду Windows PowerShell в режиме с повышенными правами:  
  
        ```powershell  
        Restart-Service RaMgmtSvc   
        ```  
  
###  <a name="BKMK_RemoveIPv6"></a>Шаг 5б: Удаление недействительного параметра IPv6Prefix в объекте групповой Политики RRAS (только для Windows Server Essentials)  
  Этот раздел относится к серверу под управлением Windows Server Essentials.  
  
 Откройте Windows PowerShell с правами администратора и выполните следующие команды:  
  
```powershell  
gpupdate  
$key = Get-ChildItem -Path HKLM:\SOFTWARE\Policies\Microsoft\Windows\RemoteAccess\config\MachineSIDs | Where-Object{$_.GetValue("IPv6RrasPrefix") -ne $null}  
Remove-GPRegistryValue -Name "DirectAccess Server Settings" -Key $key.Name -ValueName IPv6RrasPrefix  
gpupdate  
```  
  
###  <a name="BKMK_Step4cWindows7Setup"></a>Шаг 5В: разрешить клиентским компьютерам под управлением Windows 7 Корпоративная для использования DirectAccess  
 При наличии клиентских компьютеров под управлением Windows 7 Корпоративная, выполните следующую процедуру, чтобы включить DirectAccess с этих компьютеров.  
  
##### <a name="to-enable--windows-7-enterprise-computers-to-use-directaccess"></a>Чтобы разрешить компьютерам использовать DirectAccess Windows 7 Корпоративная  
  
1.  На начальной странице сервера откройте **управления удаленным доступом**.  
  
2.  В консоли управления удаленным доступом щелкните **конфигурации**. Затем в **подробности установки** области в разделе **шаг 2**, нажмите кнопку **изменить**.  
  
     Откроется мастер настройки сервера удаленного доступа.  
  
3.  На **проверки подлинности** , выберите сертификат центра сертификации (ЦС) сертификации, который будет использоваться доверенным корневым сертификатом, (вы можете выбрать сертификат ЦС для сервера Windows Server Essentials). Нажмите кнопку **клиентских компьютеров Windows 7 Включение возможностью подключения через DirectAccess**, а затем нажмите кнопку **Далее**.  
  
4.  Следуйте инструкциям для завершения работы мастера.  
  
> [!IMPORTANT]
>  Существует известная проблема с Windows 7 Корпоративная компьютеров, подключающихся через DirectAccess, если сервер Windows Server Essentials не были предустановлены с предварительно установленной UR1. Для активации подключений DirectAccess в этой среде, необходимо выполнить следующие дополнительные действия.  
>   
>  1.  Установите исправление, описанное в [статьи базы знаний Майкрософт (KB) 2796394](https://support.microsoft.com/kb/2796394) на сервере Windows Server Essentials. Перезапустите сервер.  
> 2.  Затем установите исправление, описанное в [статьи базы знаний Майкрософт (KB) 2615847](https://support.microsoft.com/kb/2615847) на каждом компьютере, Windows 7.  
>   
>      Эта проблема была решена в Windows Server Essentials.  
  
###  <a name="BKMK_NLS"></a>Шаг 5d: Настройка сервера сетевых расположений  
 Этот раздел содержит пошаговые инструкции по настройке параметров сервера сетевых расположений.  
  
> [!NOTE]
>  Прежде чем начать, скопируйте содержимое папки < SystemDrive\ > \inetpub\wwwroot в папку < SystemDrive\ > \Program Files\Windows Server\Bin\WebApps\Site\insideoutside. Также скопируйте файл default.aspx из папки < SystemDrive\ > \Program Files\Windows Server\Bin\WebApps\Site в папку < SystemDrive\ > \Program Files\Windows Server\Bin\WebApps\Site\insideoutside.  
  
##### <a name="to-configure-the-network-location-server"></a>Чтобы настроить сервер сетевых расположений  
  
1.  На начальной странице откройте **управления удаленным доступом**.  
  
2.  В консоли управления удаленным доступом щелкните **конфигурации**и в **установки удаленного доступа** области сведений **шаг 3**, нажмите кнопку **изменить**.  
  
3.  В мастере установки удаленного доступа сервера на **сервера сетевых расположений** выберите **сервер сетевых расположений развернут на сервере удаленного доступа**и затем выберите сертификат, выданный (в [шаг 3: Подготовка сертификата и запись DNS для сервера сетевых расположений](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_DNS)).  
  
4.  Следуйте инструкциям, чтобы завершить работу мастера, а затем нажмите кнопку **Готово**.  
  
###  <a name="BKMK_CA"></a>Шаг 5д: Добавление раздела реестра для обхода сертификации ЦС при установке канала IPsec  
 Следующий шаг — Настройка сервера для обхода сертификации ЦС при установке канала IPsec.  
  
##### <a name="to-add-a-registry-key-to-bypass-the-ca-certification"></a>Чтобы добавить раздел реестра для обхода сертификации ЦС  
  
1.  На начальной странице откройте **regedit** (редактор реестра).  
  
2.  В редакторе реестра перейдите в раздел **HKEY_LOCAL_MACHINE**, разверните **системы**, разверните **CurrentControlSet**, разверните **службы**и разверните **IKEEXT**.  
  
3.  В разделе **IKEEXT**, щелкните правой кнопкой мыши **параметры**, нажмите кнопку **New**, а затем нажмите кнопку **параметр DWORD (32 бита)**.  
  
4.  Переименуйте добавленное значение в **ikeflags**.  
  
5.  Дважды щелкните **ikeflags**, задайте **тип** для **шестнадцатеричное**, задайте его равным **8000**и нажмите кнопку **ОК**.  
  
> [!NOTE]
>  Можно использовать следующую команду Windows PowerShell в режиме с повышенными правами для добавления этого раздела реестра:  
>   
>  `Set-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Services\IKEEXT\Parameters -Name ikeflags -Type DWORD -Value 0x8000`  
  
##  <a name="BKMK_NRPT"></a>Шаг 6: Настройка параметров таблицы политики разрешения имен для сервера DirectAccess  
 Этот раздел содержит инструкции по изменению записей таблицы политики разрешения имен (NPRT) для внутренних адресов (например, записей с суффиксом contoso.local) для объектов групповой политики клиента DirectAccess и последующей установке адреса интерфейса IPHTTPS.  
  
#### <a name="to-configure-name-resolution-policy-table-entries"></a>Настройка записей таблицы политики разрешения имен  
  
1.  На начальной странице откройте **Управление групповой политикой**.  
  
2.  В консоли управления групповыми политиками щелкните по умолчанию лес и домен, щелкните правой кнопкой мыши **параметры клиента DirectAccess**, а затем нажмите кнопку **изменить**.  
  
3.  Нажмите кнопку **конфигурации компьютера**, нажмите кнопку **политики**, нажмите кнопку **параметры Windows**, а затем нажмите кнопку **политика разрешения имен**. Выберите запись, пространство имен которой идентично вашему DNS-суффиксу и нажмите кнопку **изменение правила**.  
  
4.  Нажмите кнопку **параметры DNS для DirectAccess** вкладке; Выберите **Разрешить параметры DNS для DirectAccess в этом правиле**. Добавьте адрес IPv6 для интерфейса IP-HTTPS в список DNS-серверов.  
  
    > [!NOTE]
    >  Для получения адреса IPv6 можно использовать следующую команду Windows PowerShell:  
    >   
    >  `(Get-NetIPInterface -InterfaceAlias IPHTTPSInterface | Get-NetIPAddress -PrefixLength 128)[1].IPAddress`  
  
##  <a name="BKMK_TCPUDP"></a>Шаг 7: Настройка правил брандмауэра TCP и UDP для объектов групповой политики сервера DirectAccess  
 Этот раздел содержит пошаговые инструкции по настройке правил брандмауэра TCP и UDP для объектов групповой политики сервера DirectAccess.  
  
#### <a name="to-configure-firewall-rules"></a>Настройка правил брандмауэра  
  
1.  На начальной странице откройте **Управление групповой политикой**.  
  
2.  В консоли управления групповыми политиками щелкните по умолчанию лес и домен, щелкните правой кнопкой мыши **параметры сервера DirectAccess**, а затем нажмите кнопку **изменить**.  
  
3.  Нажмите кнопку **Конфигурация компьютера**, нажмите кнопку **политики**, нажмите кнопку **параметры Windows**, нажмите кнопку **параметры безопасности**, нажмите кнопку **брандмауэр Windows в режиме повышенной безопасности**, щелкните следующего уровня **брандмауэр Windows в режиме повышенной безопасности**и нажмите кнопку **правила для входящих подключений**. Щелкните правой кнопкой мыши **доменное имя сервера (TCP-In)**, а затем нажмите кнопку **свойства**.  
  
4.  Нажмите кнопку **область** вкладки и в **локальный IP-адрес** добавьте адрес IPv6 интерфейса IP-HTTPS.  
  
5.  Повторите ту же процедуру для **сервера доменных имен (UDP-In)**.  
  
##  <a name="BKMK_DNS64"></a>Шаг 8: Изменение конфигурации DNS64 для ожидания передачи данных интерфейса IP-HTTPS  
 Необходимо изменить конфигурацию DNS64 для ожидания передачи данных интерфейса IP-HTTPS с помощью следующей команды Windows PowerShell.  
  
```powershell  
Set-NetDnsTransitionConfiguration  �AcceptInterface IPHTTPSInterface  
```  
  
##  <a name="BKMK_ExemptPort"></a>Шаг 9: Резервирование портов для службы WinNat  
 Чтобы зарезервировать порты для службы WinNat, используйте следующую команду Windows PowerShell. Замените «192.168.1.100» на реальный адрес IPv4 сервера Windows Server Essentials.  
  
```powershell  
Set-NetNatTransitionConfiguration  �IPv4AddressPortPool @("192.168.1.100, 10000-47000")  
```  
  
> [!IMPORTANT]
>  Чтобы избежать конфликтов с приложениями, убедитесь, что в диапазон зарезервированных для службы WinNat портов не входит порт 6602.  
  
##  <a name="BKMK_WinNAT"></a>Шаг 10: Перезапуск службы WinNat  
 Перезапустите службу драйвера NAT Windows (WinNat), выполнив следующую команду Windows PowerShell.  
  
```powershell  
Restart-Service winnat  
```  
  
##  <a name="BKMK_AppendixBPowerShellScript"></a>Приложение: Установка DirectAccess с помощью Windows PowerShell  
 В этом разделе описывается установка и настройка DirectAccess с помощью Windows PowerShell.  
  
### <a name="preparation"></a>Подготовка  
 Перед началом настройки сервера для DirectAccess, необходимо выполнить следующее:  
  
1.  Выполните процедуру, описанную в [шаг 3: Подготовка сертификата и запись DNS для сервера сетевых расположений](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_DNS) Чтобы зарегистрировать сертификат с именем **DirectAccess-NLS.contoso.com** (где **contoso.com** будет заменена фактическим внутреннее имя домена) и добавить запись DNS для сервера сетевых расположений (NLS).  
  
2.  Добавьте группу безопасности под названием **DirectAccessClients** в Active Directory, а затем добавьте клиентские компьютеры, для которых вы хотите предоставить функции DirectAccess. Дополнительные сведения см. в разделе [шаг 4: Создание группы безопасности для клиентов DirectAccess компьютеры](#BKMK_AddSecurityGroup).  
  
### <a name="commands"></a>Команды  
  
> [!IMPORTANT]
>  В Windows Server Essentials не требуется удалять ненужный префикс IPv6 в объект групповой Политики. Удалите раздел кода со следующей меткой: `# [WINDOWS SERVER 2012 ESSENTIALS ONLY] Remove the unnecessary IPv6 prefix GPO`.  
  
```powershell  
# Add Remote Access role if not installed yet  
$ra = Get-WindowsFeature RemoteAccess  
If ($ra.Installed -eq $FALSE) { Add-WindowsFeature RemoteAccess }  
  
# Server may need to restart if you installed RemoteAccess role in the above step  
  
# Set the internet domain name to access server, replace contoso.com below with your own domain name  
$InternetDomain = "www.contoso.com"  
#Set the SG name which you create for DA clients  
$DaSecurityGroup = "DirectAccessClients"  
#Set the internal domain name  
$InternalDomain = [System.DirectoryServices.ActiveDirectory.Domain]::GetCurrentDomain().Name  
  
# Set static IP and DNS settings  
$NetConfig = Get-WmiObject Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true"  
$CurrentIP = $NetConfig.IPAddress[0]  
$SubnetMask = $NetConfig.IPSubnet | Where-Object{$_ -like "*.*.*.*"}  
$NetConfig.EnableStatic($CurrentIP, $SubnetMask)  
$NetConfig.SetGateways($NetConfig.DefaultIPGateway)  
$NetConfig.SetDNSServerSearchOrder($CurrentIP)  
  
# Get physical adapter name and the certificate for NLS server  
$Adapter = (Get-WmiObject -Class Win32_NetworkAdapter -Filter "NetEnabled=$true").NetConnectionId  
$Certs = dir cert:\LocalMachine\My  
$nlscert = $certs | Where-Object{$_.Subject -like "*CN=DirectAccess-NLS*"}  
  
# Add regkey to bypass CA cert for IPsec authentication  
Set-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Services\IKEEXT\Parameters -Name ikeflags -Type DWORD -Value 0x8000  
  
# Install DirectAccess.   
Install-RemoteAccess -NoPrerequisite -DAInstallType FullInstall -InternetInterface $Adapter -InternalInterface $Adapter -ConnectToAddress $InternetDomain -nlscertificate $nlscert -force  
  
#Restart Remote Access Management service  
Restart-Service RaMgmtSvc  
  
# [WINDOWS SERVER 2012 ESSENTIALS ONLY] Remove the unnecessary IPv6 prefix GPO   
  
gpupdate  
$key = Get-ChildItem -Path HKLM:\SOFTWARE\Policies\Microsoft\Windows\RemoteAccess\config\MachineSIDs | Where-Object{$_.GetValue("IPv6RrasPrefix") -ne $null}  
Remove-GPRegistryValue -Name "DirectAccess Server Settings" -Key $key.Name -ValueName IPv6RrasPrefix  
gpupdate  
  
# Enable client computers running Windows 7 to use DirectAccess  
$allcertsinroot = dir cert:\LocalMachine\root  
$rootcert = $allcertsinroot | Where-Object{$_.Subject -like "*-CAA*"}  
Set-DAServer  �IPSecRootCertificate $rootcert[0]  
Set  �DAClient  �OnlyRemoteComputers Disabled -Downlevel Enabled  
  
#Set the appropriate security group used for DA client computers. Replace the group name below with the one you created for DA clients  
Add-DAClient -SecurityGroupNameList $DaSecurityGroup   
Remove-DAClient -SecurityGroupNameList "Domain Computers"  
  
# Gather DNS64 IP address information  
$Remoteaccess = get-remoteaccess  
$IPinterface = get-netipinterface -InterfaceAlias IPHTTPSInterface | get-netipaddress -PrefixLength 128  
$DNS64IP=$IPInterface[1].IPaddress  
$Natconfig = Get-NetNatTransitionConfiguration  
  
# Configure TCP and UDP firewall rules for the DirectAccess server GPO  
$GpoName = 'GPO:'+$InternalDomain+'\DirectAccess Server Settings'  
Get-NetFirewallRule -PolicyStore $GpoName -Displayname "Domain Name Server (TCP-IN)"|Get-NetFirewallAddressFilter | Set-NetFirewallAddressFilter -LocalAddress $DNS64IP  
Get-NetFirewallrule -PolicyStore $GpoName -Displayname "Domain Name Server (UDP-IN)"|Get-NetFirewallAddressFilter | Set-NetFirewallAddressFilter -LocalAddress $DNS64IP  
  
# Configure the name resolution policy settings for the DirectAccess server, replace the DNS suffix below with the one in your domain  
$Suffix = '.' + $InternalDomain  
set-daclientdnsconfiguration -DNSsuffix $Suffix -DNSIPAddress $DNS64IP  
  
# Change the DNS64 configuration to listen to IP-HTTPS interface  
Set-NetDnsTransitionConfiguration -AcceptInterface IPHTTPSInterface  
  
# Copy the necessary files to NLS site folder  
XCOPY 'C:\inetpub\wwwroot' 'C:\Program Files\Windows Server\Bin\WebApps\Site\insideoutside' /E /Y  
XCOPY 'C:\Program Files\Windows Server\Bin\WebApps\Site\Default.aspx' 'C:\Program Files\Windows Server\Bin\WebApps\Site\insideoutside' /Y  
  
# Reserve ports for the WinNat service  
Set-NetNatTransitionConfiguration  �IPv4AddressPortPool @("192.168.1.100, 10000-47000")  
  
# Restart the WinNat service  
Restart-Service winnat  
```  
  
## <a name="see-also"></a>См. также:  
  
-   [Управление повсеместным доступом](Manage-Anywhere-Access-in-Windows-Server-Essentials.md)  
  
-   [Управление Windows Server Essentials](Manage-Windows-Server-Essentials.md)
