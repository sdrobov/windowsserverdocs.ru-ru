---
title: Настройка DirectAccess в Windows Server Essentials
description: Описывает способ использования Windows Server Essentials
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
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59860685"
---
# <a name="configure-directaccess-in-windows-server-essentials"></a>Настройка DirectAccess в Windows Server Essentials

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Этот раздел содержит пошаговые инструкции по настройке DirectAccess в Windows Server Essentials для включения вашим мобильным сотрудникам с легкостью подключаться к сети организации s из любого удаленного расположения с доступом в Интернет без использования Подключение виртуальной частной сети (VPN). DirectAccess Ваш мобильный персонал сможет единообразно работать в сети внутри и вне офиса с компьютеров Windows 8.1, Windows 8 и Windows 7.  
  
 В Windows Server Essentials Если в домен входит более одного сервера Windows Server Essentials, DirectAccess необходимо настроить на контроллере домена.  
  
> [!NOTE]
>  Этот раздел содержит инструкции по настройке DirectAccess в том случае, когда сервер Windows Server Essentials является контроллером домена. Если сервер Windows Server Essentials является членом домена, следуйте инструкциям для настройки DirectAccess в состав домена [Добавление DirectAccess в развертывание существующего удаленного доступа (VPN)](https://technet.microsoft.com/library/jj574220.aspx) вместо этого.  
  
## <a name="process-overview"></a>Общие сведения о процессе  
 Чтобы настроить DirectAccess в Windows Server Essentials, выполните следующие действия.  
  
> [!IMPORTANT]
>  Прежде чем использовать процедуры, описанные в этом руководстве для настройки DirectAccess в Windows Server Essentials, необходимо включить на сервере VPN. Инструкции см. в разделе [управление виртуальной частной СЕТЬЮ](Manage-VPN-in-Windows-Server-Essentials.md).  
  
-   [Шаг 1. Добавить средства управления удаленным доступом к серверу](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_AddRAM)  
  
-   [Шаг 2. Изменение адреса сетевого адаптера сервера на статический IP-адрес](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_AddStaticIP)  
  
-   [Шаг 3. Подготовка сертификата и запись DNS для сервера сетевых расположений](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_DNS)  
  
    -   [Шаг 3a. Предоставление полных разрешений для прошедших проверку пользователей веб-сервера s шаблона сертификата](#BKMK_GrantFullPermissions)  
  
    -   [Шаг 3b. Регистрация сертификата для сервера сетевых расположений с общим именем, которое невозможно разрешить из внешней сети](#BKMK_EnrollaCertificate)  
  
    -   [Шаг 3c. Добавление нового узла к DNS-серверу и сопоставление его с адресом сервера Windows Server Essentials](#BKMK_MapNewHosttoServerAddress)  
  
-   [Шаг 4. Создайте группу безопасности для клиентских компьютеров DirectAccess](#BKMK_AddSecurityGroup)  
  
-   [Шаг 5. Включение и настройка DirectAccess](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_EnableConfigureDA)  
  
    -   [Шаг 5а. Включение DirectAccess через консоль управления удаленным доступом](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_EnableDA)  
  
    -   [Шаг 5б. Удаление недействительного параметра IPv6Prefix в объекте групповой Политики RRAS (только для Windows Server Essentials)](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_RemoveIPv6)  
  
    -   [Шаг 5В. Включить клиентские компьютеры под управлением Windows 7 Корпоративная, для использования DirectAccess](#BKMK_Step4cWindows7Setup)  
  
    -   [Шаг 5г. Настройка сервера сетевых расположений](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_NLS)  
  
    -   [Шаг 5д. Добавление раздела реестра для обхода сертификации ЦС при установке канала IPsec](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_CA)  
  
-   [Шаг 6. Настройка параметров таблицы политики разрешения имен для сервера DirectAccess.](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_NRPT)  
  
-   [Шаг 7. Настройка правил брандмауэра TCP и UDP для объектов групповой политики сервера DirectAccess](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_TCPUDP)  
  
-   [Шаг 8. Изменить конфигурацию DNS64 для ожидания передачи данных интерфейса IP-HTTPS](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_DNS64)  
  
-   [Шаг 9. Резервирование портов для службы WinNat](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_ExemptPort)  
  
-   [Шаг 10. Перезапуск службы WinNat](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_WinNAT)  
  
> [!NOTE]
>  [Приложение: Настройка DirectAccess с помощью Windows PowerShell](#BKMK_AppendixBPowerShellScript) предоставляет сценарий Windows PowerShell, который можно использовать для выполнения установки DirectAccess.  
  
##  <a name="BKMK_AddRAM"></a> Шаг 1. Добавление на сервер средства управления удаленным доступом  
  
#### <a name="to-add-remote-access-management-tools"></a>Добавление средств управления удаленным доступом  
  
1.  На сервере щелкните значок **Диспетчер серверов** в левом нижнем углу начальной страницы.  
  
     В Windows Server Essentials потребуется сначала найти для диспетчера сервера, чтобы открыть его. На начальной странице введите **Server Manager**, после чего щелкните **Диспетчер серверов** в результатах поиска. Чтобы поместить диспетчер серверов на начальный экран, щелкните его правой кнопкой мыши в результатах поиска и нажмите **Закрепить на начальном экране**.  
  
2.  Если отобразится предупреждающее сообщение **Контроля учетных записей** , щелкните **Да**.  
  
3.  На панели мониторинга диспетчера серверов щелкните **Управление**, после чего нажмите **Добавить роли и компоненты**.  
  
4.  В мастере добавления ролей и компонентов выполите следующие действия:  
  
    1.  На странице **Тип установки** щелкните **Установка ролей или компонентов**.  
  
    2.  На **Выбор сервера** (или **Выбор целевого сервера** странице в Windows Server Essentials), нажмите кнопку **выберите сервер из пула серверов**.  
  
    3.  На странице **Возможности** разверните **Средства удаленного администрирования сервера (установлены)**, затем **Средства управления удаленным доступом (установлены)**, щелкните **Средства администрирования ролей (установлены)**, откройте **Средства управления удаленным доступом**, после чего выберите **Графический интерфейс пользователя удаленного доступа и программы командной строки**.  
  
    4.  Для завершения работы мастера следуйте инструкциям на экране.  
  
##  <a name="BKMK_AddStaticIP"></a> Шаг 2. Изменение адреса сетевого адаптера сервера на статический IP-адрес  
 Для работы компонента DirectAccess необходим адаптер со статическим IP-адресом. Следует изменить IP-адрес локального сетевого адаптера на сервере.  
  
#### <a name="to-add-a-static-ip-address"></a>Добавление статического IP-адреса  
  
1.  На начальной странице откройте **Панель управления**.  
  
2.  Щелкните **Сеть и Интернет**, а затем **Просмотр состояния сети и задач**.  
  
3.  В области задач **Центра управления сетями и общим доступом** щелкните **Изменение параметров адаптера**.  
  
4.  Щелкните правой кнопкой мыши локальный сетевой адаптер, а затем щелкните **Свойства**.  
  
5.  На вкладке **Сеть** выберите **Протокол Интернета версии 4 (TCP/IPv4)** и нажмите кнопку **Свойства**.  
  
6.  На вкладке **Общие** щелкните **Использовать следующий IP-адрес**и введите нужный IP-адрес.  
  
     В поле **Маска подсети** автоматически появится значение по умолчанию для маски подсети. Примите значение по умолчанию или введите нужное значение маски подсети.  
  
7.  В поле **Шлюз по умолчанию** введите IP-адрес шлюза по умолчанию.  
  
8.  В поле **Предпочитаемый DNS-сервер** введите IP-адрес DNS-сервера.  
  
    > [!NOTE]
    >  Вместо IP замыкаемой на себя сети (например,127.0.0.1) следует использовать IP-адрес, который был назначен вашему сетевому адаптеру DHCP (например, 192.168.X.X). Чтобы узнать назначенный IP-адрес, в командной строке введите **ipconfig** .  
  
9. В поле **Альтернативный DNS-сервер** введите IP-адрес альтернативного DNS-сервера (если есть).  
  
10. Нажмите кнопку **ОК**, а затем кнопку **Закрыть**.  
  
> [!IMPORTANT]
>  Убедитесь, что маршрутизатор настроен на перенаправление портов 80 и 443 новому статическому IP-адресу сервера.  
  
##  <a name="BKMK_DNS"></a> Шаг 3. Подготовка сертификата и запись DNS для сервера сетевых расположений  
 Чтобы подготовить сертификат и произвести запись DNS для сервера сетевых расположений, выполните следующие действия:  
  
-   [Шаг 3a. Предоставление полных разрешений для прошедших проверку пользователей веб-сервера s шаблона сертификата](#BKMK_GrantFullPermissions)  
  
-   [Шаг 3b. Регистрация сертификата для сервера сетевых расположений с общим именем, которое невозможно разрешить из внешней сети](#BKMK_EnrollaCertificate)  
  
-   [Шаг 3c. Добавление нового узла к DNS-серверу и сопоставление его с адресом сервера Windows Server Essentials.](#BKMK_MapNewHosttoServerAddress)  
  
###  <a name="BKMK_GrantFullPermissions"></a> Шаг 3a. Предоставление полных разрешений для прошедших проверку пользователей веб-сервера s шаблона сертификата  
 Первая задача — Предоставление полных разрешений для проверки подлинности пользователей для шаблона сертификата веб-сервера s, в центре сертификации.  
  
####  <a name="BKMK_ToGrantFullPermissions"></a> Необходимо предоставить полные разрешения на Authenticated Users сервера веб-шаблона сертификата s  
  
1.  На **Начальной странице** откройте **Центр сертификации**.  
  
2.  В дереве консоли в разделе **центр сертификации (локальный)**, разверните **< servername\>-CA**, щелкните правой кнопкой мыши **шаблонов сертификатов**, а затем нажмите кнопку **Управление**.  
  
3.  В разделе **Центр сертификации (Локальный)** щелкните правой кнопкой мыши **Веб-сервер**, после чего нажмите **Свойства**.  
  
4.  В свойствах веб-сервера на вкладке **Безопасность** щелкните **Прошедшие проверку**, выберите **Полный доступ**, а затем нажмите **OК**.  
  
5.  Перезапустите **Службы сертификатов Active Directory**. В панели управления выберите **Просмотр локальных служб**. В списке служб щелкните правой кнопкой мыши **Службы сертификатов Active Directory**, после чего нажмите **Перезапуск**.  
  
###  <a name="BKMK_EnrollaCertificate"></a> Шаг 3b. Регистрация сертификата для сервера сетевых расположений с общим именем, которое невозможно разрешить из внешней сети  
 После этого необходимо выполнить регистрацию сертификата для сервера сетевых расположений с общим именем, которое невозможно разрешить из внешней сети.  
  
####  <a name="BKMK_ToEnrollaCertificate"></a> Чтобы зарегистрировать сертификат для сервера сетевых расположений  
  
1.  На **Начальной странице** откройте **mmc** (консоль управления).  
  
2.  Если появится предупреждающее сообщение **Контроля учетных записей** , щелкните **Да**.  
  
     Отобразится консоль управления (MMC).  
  
3.  В меню **Файл** щелкните **Добавить или удалить оснастку**.  
  
4.  В поле **Добавить или удалить оснастку** щелкните **Сертификаты**, после чего нажмите **Добавить**.  
  
5.  На странице **Оснастка диспетчера сертификатов** щелкните **Учетная запись компьютера** и нажмите кнопку **Далее**.  
  
6.  На странице **Выбор компьютера** щелкните **Локальный компьютер**, нажмите кнопку **Готово**, а затем **ОК**.  
  
7.  В дереве консоли разверните **Сертификаты (локальный компьютер)**, затем **Личные**, щелкните правой кнопкой мыши **Сертификаты**, после чего в области **Все задачи** нажмите **Запросить новый сертификат**.  
  
8.  Когда откроется мастер регистрации сертификатов, щелкните **Далее**.  
  
9. На странице **Выбор политики регистрации сертификатов** щелкните **Далее**.  
  
10. На странице **Запросить сертификат** поставьте флажок рядом с пунктом **Веб-сервер**, после чего щелкните **Для регистрации этого сертификата необходимы дополнительные сведения**.  
  
11. В поле **Свойства сертификата** установите следующие параметры для пункта **Имя субъекта**:  
  
    1.  Для параметра **Тип** выберите **Общее имя**.  
  
    2.  Для параметра **Значение**введите имя сервера сетевых расположений (например, DirectAccess-NLS.contoso.local), а затем щелкните **Добавить**.  
  
    3.  Нажмите кнопку **ОК**, после чего щелкните **Регистрация**.  
  
12. По завершении регистрации сертификата щелкните кнопку **Готово**.  
  
###  <a name="BKMK_MapNewHosttoServerAddress"></a> Шаг 3c. Добавление нового узла к DNS-серверу и сопоставление его с адресом сервера под управлением Windows Server Essentials  
 Для завершения настройки DNS, Добавление нового узла к DNS-серверу и сопоставить его с адресом сервера Windows Server Essentials.  
  
####  <a name="BKMK_ToMapNewHosttoServerAddress"></a> Сопоставление нового узла с адресом сервера Windows Server Essentials  
  
1.  На начальной странице откройте диспетчер DNS. Чтобы открыть диспетчер DNS, введите в строке поиска **dnsmgmt.msc**и щелкните в результатах **dnsmgmt.msc** .  
  
2.  В дереве консоли диспетчера DNS разверните локальный сервер, разверните узел **зоны прямого просмотра**, щелкните правой кнопкой мыши зону с суффиксом домена сервера s и нажмите кнопку **новый узел (A или AAAA)**.  
  
3.  Введите имя и IP-адрес сервера (например, DirectAccess-NLS.contoso.local), а также соответствующий адрес сервера (например, 192.168.x.x).  
  
4.  Щелкните **Добавить узел**, после чего нажмите **OK**, а затем — **Готово**.  
  
##  <a name="BKMK_AddSecurityGroup"></a> Шаг 4. Создание группы безопасности для клиентских компьютеров DirectAccess  
 Теперь необходимо создать группу безопасности для клиентских компьютеров DirectAccess и добавить в нее учетные записи компьютеров.  
  
#### <a name="to-add-a-security-group-for-client-computers-that-use-directaccess"></a>Создание группы безопасности для клиентских компьютеров, использующих DirectAccess  
  
1.  На панели мониторинга диспетчера серверов щелкните **Сервис** и нажмите **Active Directory — пользователи и компьютеры**.  
  
    > [!NOTE]
    >  Если в меню **Сервис** отсутствует пункт **Active Directory — пользователи и компьютеры**, необходимо установить данный компонент. Для этого необходимо выполнить с правами администратора следующий командлет Windows PowerShell: `Install-WindowsFeature RSAT-ADDS-Tools`. Подробную информацию см. в статье [Установка или удаление средств удаленного администрирования сервера](https://technet.microsoft.com/library/cc730825.aspx).  
  
2.  В дереве консоли разверните сервер, щелкните правой кнопкой мыши **Пользователи**, нажмите **Создать**и выберите пункт **Группа**.  
  
3.  Укажите имя, область и тип группы (необходимо создать группу безопасности), после чего щелкните **OK**.  
  
 Новая группа безопасности будет добавлена в папку **Пользователи**.  
  
#### <a name="to-add-computer-accounts-to-the-security-group"></a>Добавление учетных записей компьютеров в группу безопасности  
  
1.  На панели мониторинга диспетчера серверов щелкните **Сервис** и нажмите **Active Directory — пользователи и компьютеры**.  
  
2.  В дереве консоли разверните сервер и щелкните **Пользователи**.  
  
3.  В списке учетных записей пользователей и групп безопасности сервера щелкните правой кнопкой мыши созданную вами для DirectAccess группу безопасности и откройте **Свойства**.  
  
4.  На вкладке **Члены группы** щелкните **Добавить**.  
  
5.  В диалоговом окне укажите через точку с запятой (;) имена учетных записей компьютеров, которые вы желаете добавить группу. После этого щелкните **Проверить имена**.  
  
6.  После проверки учетных записей компьютеров щелкните **OK**. Затем повторно нажмите **OK**.  
  
> [!NOTE]
>  Добавить учетную запись в группу безопасности также можно на вкладке **Входит в состав** в свойствах учетной записи компьютера.  
  
##  <a name="BKMK_EnableConfigureDA"></a> Шаг 5. Включение и настройка DirectAccess  
 Чтобы включить и настроить DirectAccess в Windows Server Essentials, необходимо выполнить следующие действия:  
  
-   [Шаг 5а. Включение DirectAccess через консоль управления удаленным доступом](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_EnableDA)  
  
-   [Шаг 5б. Удаление недействительного параметра IPv6Prefix в объекте групповой Политики RRAS (только для Windows Server Essentials)](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_RemoveIPv6)  
  
-   [Шаг 5В. Включить клиентские компьютеры под управлением Windows 7 Корпоративная, для использования DirectAccess](#BKMK_Step4cWindows7Setup)  
  
-   [Шаг 5г. Настройка сервера сетевых расположений](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_NLS)  
  
-   [Шаг 5д. Добавление раздела реестра для обхода сертификации ЦС при установке канала IPsec](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_CA)  
  
###  <a name="BKMK_EnableDA"></a> Шаг 5а. Включение DirectAccess через консоль управления удаленным доступом  
 Этот раздел содержит пошаговые инструкции по включению DirectAccess в Windows Server Essentials. Если вы еще не настроили VPN-сервер, необходимо сделать это до выполнения описанных действий. Инструкции см. в разделе [управление виртуальной частной СЕТЬЮ](Manage-VPN-in-Windows-Server-Essentials.md).  
  
##### <a name="to-enable-directaccess-by-using-the-remote-access-management-console"></a>Включение DirectAccess через консоль управления удаленным доступом  
  
1.  На начальной странице откройте меню **Управление удаленным доступом**.  
  
2.  В мастере включения DirectAccess выполните следующие действия.  
  
    1.  Проверьте **Требования для DirectAccess** и щелкните **Далее**.  
  
    2.  На вкладке **Выбор групп** добавьте группу безопасности, созданную вами ранее для клиентов DirectAccess (Если вы не создали группу безопасности, см. в разделе [Step 4: Создайте группу безопасности для клиента DirectAccess компьютеров](#BKMK_AddSecurityGroup) инструкции.)  
  
    3.  На вкладке **Выбор групп** щелкните **Разрешить DirectAccess только для мобильных компьютеров**, если вы хотите разрешить мобильными компьютерам использовать DirectAccess для удаленного доступа к серверу, а затем нажмите кнопку **Далее**.  
  
    4.  На странице **Топология сети**выберите топологию сервера и нажмите кнопку **Далее**.  
  
    5.  На странице **Список DNS-суффиксов**добавьте дополнительный DNS-суффикс для клиентских компьютеров, если это необходимо, и нажмите кнопку **Далее**.  
  
        > [!NOTE]
        >  Мастер DirectAccess по умолчанию добавляет DNS-суффикс текущего домена. При необходимости можно добавить и другие суффиксы.  
  
    6.  Проверьте объекты групповой политики, которые будут применяться, и при необходимости измените их.  
  
    7.  Нажмите кнопку **Далее**, а затем кнопку **Готово**.  
  
    8.  Перезапустите службу управления удаленным доступом, выполнив следующую команду Windows PowerShell в режиме с повышенными правами:  
  
        ```powershell  
        Restart-Service RaMgmtSvc   
        ```  
  
###  <a name="BKMK_RemoveIPv6"></a> Шаг 5б. Удаление недействительного параметра IPv6Prefix в объекте групповой Политики RRAS (только для Windows Server Essentials)  
  Этот раздел относится к серверу под управлением Windows Server Essentials.  
  
 Откройте Windows PowerShell от имени администратора и выполните следующие команды.  
  
```powershell  
gpupdate  
$key = Get-ChildItem -Path HKLM:\SOFTWARE\Policies\Microsoft\Windows\RemoteAccess\config\MachineSIDs | Where-Object{$_.GetValue("IPv6RrasPrefix") -ne $null}  
Remove-GPRegistryValue -Name "DirectAccess Server Settings" -Key $key.Name -ValueName IPv6RrasPrefix  
gpupdate  
```  
  
###  <a name="BKMK_Step4cWindows7Setup"></a> Шаг 5В. Включить клиентские компьютеры под управлением Windows 7 Корпоративная, для использования DirectAccess  
 При наличии клиентских компьютеров под управлением Windows 7 Enterprise, выполните следующую процедуру для включения DirectAccess с этих компьютеров.  
  
##### <a name="to-enable--windows-7-enterprise-computers-to-use-directaccess"></a>Чтобы разрешить компьютерам использовать DirectAccess Windows 7 Корпоративная  
  
1.  На начальной странице сервера s откройте **управления удаленным доступом**.  
  
2.  В консоли управления удаленным доступом щелкните **Конфигурация**. В области **Подробности установки** щелкните **Изменить** для пункта **Шаг 2**.  
  
     Откроется мастер установки сервера удаленного доступа.  
  
3.  На **проверки подлинности** вкладке, выберите сертификат центра сертификации (ЦС) сертификации, который будет использоваться в качестве доверенного корневого сертификата, (вы можете выбрать сертификат ЦС сервера Windows Server Essentials). Щелкните **Разрешить клиентским компьютерам с Windows 7 подключаться с помощью DirectAccess**, после чего нажмите **Далее**.  
  
4.  Для завершения работы мастера следуйте инструкциям на экране.  
  
> [!IMPORTANT]
>  Имеется известная проблема для Windows 7 Корпоративная компьютеров, подключающихся через DirectAccess, если серверу Windows Server Essentials поступил не с UR1 предварительно установлен. Для активации подключений DirectAccess в этой среде необходимы дополнительные действия:  
>   
>  1.  Установите исправление, описанное в [статье 2796394 базы знаний Майкрософт (KB)](https://support.microsoft.com/kb/2796394) на сервере Windows Server Essentials. Перезапустите сервер.  
> 2.  Затем установите исправление, описанное в [статьи базы знаний Майкрософт (KB) 2615847](https://support.microsoft.com/kb/2615847) на каждом компьютере Windows 7.  
>   
>      Эта проблема была решена в Windows Server Essentials.  
  
###  <a name="BKMK_NLS"></a> Шаг 5г. Настроить сервер сетевых расположений.  
 Этот раздел содержит поэтапные инструкции по настройке параметров сервера сетевых расположений.  
  
> [!NOTE]
>  Перед началом работы скопируйте содержимое < SystemDrive\>\inetpub\wwwroot в папку < системный_диск\>\Program Files\Windows Server\Bin\WebApps\Site\insideoutside folder. Также скопируйте файл default.aspx из < SystemDrive\>\Program Files\Windows server\bin\webapps\site в < SystemDrive\>\Program Files\Windows Server\Bin\WebApps\Site\insideoutside folder.  
  
##### <a name="to-configure-the-network-location-server"></a>Настройка сервера сетевых расположений  
  
1.  На начальной странице откройте меню **Управление удаленным доступом**.  
  
2.  В консоли управления удаленным доступом щелкните **Конфигурация**, после чего в области сведений **Установка удаленного доступа** нажмите **Изменить** для пункта **Шаг 3**.  
  
3.  В мастере установки удаленного доступа сервера на **сервера сетевых расположений** выберите **сервера сетевых расположений развертывается на сервере удаленного доступа**, а затем выберите сертификат, который был выданный (в [Step 3: Подготовка сертификата и запись DNS для сервера сетевых расположений](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_DNS)).  
  
4.  Выполните инструкции для завершения работы мастера и нажмите кнопку **Готово**.  
  
###  <a name="BKMK_CA"></a> Шаг 5д. Добавление раздела реестра для обхода сертификации ЦС при установке канала IPsec  
 Теперь вам следует настроить сервер на обход сертификации ЦС при установке канала IPsec.  
  
##### <a name="to-add-a-registry-key-to-bypass-the-ca-certification"></a>Добавление раздела реестра для обхода сертификации ЦС  
  
1.  На начальной странице откройте приложение **regedit** (редактор реестра).  
  
2.  В редакторе реестра перейдите в раздел **HKEY_LOCAL_MACHINE** > **System** > **CurrentControlSet** > **Services** > **IKEEXT**.  
  
3.  В разделе **IKEEXT** щелкните правой кнопкой мыши строку **Parameters**, нажмите **Создать**, после чего выберите **Параметр DWORD (32 бита)**.  
  
4.  Переименуйте созданное значение в **ikeflags**.  
  
5.  Дважды щелкните параметр **ikeflags**, в поле **Система счисления** выберите **Шестнадцатеричная**, задайте значение **8000**и нажмите **OK**.  
  
> [!NOTE]
>  Для добавления этого раздела реестра вы можете использовать следующую команду Windows PowerShell в режиме с повышенными правами:  
>   
>  `Set-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Services\IKEEXT\Parameters -Name ikeflags -Type DWORD -Value 0x8000`  
  
##  <a name="BKMK_NRPT"></a> Шаг 6. Настройка параметров таблицы политики разрешения имен для сервера DirectAccess  
 В этом разделе приведены инструкции по изменению записей таблицы политики разрешения имен (NPRT) для внутренних адресов (например, записей с суффиксом contoso.local) для объектов групповой политики клиента DirectAccess, а также по дальнейшей установке адреса интерфейса IPHTTPS.  
  
#### <a name="to-configure-name-resolution-policy-table-entries"></a>Настройка записей таблицы политики разрешения имен  
  
1.  На начальной странице откройте меню **Управление групповыми политиками**.  
  
2.  В консоли управления групповыми политиками щелкните лес и домен по умолчанию, нажмите правой кнопкой мыши **Параметры клиента DirectAccess**, а затем щелкните **Изменить**.  
  
3.  Щелкните **Конфигурации компьютера**, затем **Политики**, нажмите **Конфигурация Windows**, после чего выберите пункт **Политика разрешения имен**. Выберите запись, пространство имен которой идентично вашему DNS-суффиксу, и щелкните **Изменить правило**.  
  
4.  Щелкните вкладку **Параметры DNS для DirectAccess**, затем выберите **Разрешить параметры DNS для DirectAccess в этом правиле**. Добавьте адрес IPv6 для интерфейса IP-HTTPS в список серверов DNS.  
  
    > [!NOTE]
    >  Для получения адреса IPv6 можно использовать следующую команду Windows PowerShell:  
    >   
    >  `(Get-NetIPInterface -InterfaceAlias IPHTTPSInterface | Get-NetIPAddress -PrefixLength 128)[1].IPAddress`  
  
##  <a name="BKMK_TCPUDP"></a> Шаг 7. Настроить правила брандмауэра TCP и UDP для объектов групповой политики сервера DirectAccess.  
 В этот раздел входят пошаговые инструкции по настройке правил брандмауэра TCP и UDP для объектов групповой политики сервера DirectAccess.  
  
#### <a name="to-configure-firewall-rules"></a>Настройка правил брандмауэра  
  
1.  На начальной странице откройте меню **Управление групповыми политиками**.  
  
2.  В консоли управления групповыми политиками щелкните лес и домен по умолчанию, нажмите правой кнопкой мыши **Параметры сервера DirectAccess**, а затем щелкните **Изменить**.  
  
3.  Перейдите в раздел **Конфигурация компьютера** > **Политики** > **Конфигурация Windows** > **Параметры безопасности** > **Брандмауэр Windows в режиме повышенной безопасности**, после чего перейдите на следующий уровень меню **Брандмауэр Windows в режиме повышенной безопасности** и откройте **Правила для входящих подключений**. Щелкните правой кнопкой мыши **Сервер доменных имен (входящий трафик TCP)** и выберите **Свойства**.  
  
4.  Щелкните вкладку **Область** и в списке **Локальный IP-адрес** добавьте адрес IPv6 интерфейса IP-HTTPS.  
  
5.  Повторите ту же процедуру для **Сервера доменных имен (входящий трафик UDP)**.  
  
##  <a name="BKMK_DNS64"></a> Шаг 8. Изменить конфигурацию DNS64 для ожидания передачи данных интерфейса IP-HTTPS.  
 Чтобы выполнялось ожидание передачи данных интерфейса IP-HTTPS, конфигурацию DNS64 необходимо изменить при помощи следующей команды Windows PowerShell.  
  
```powershell  
Set-NetDnsTransitionConfiguration  �AcceptInterface IPHTTPSInterface  
```  
  
##  <a name="BKMK_ExemptPort"></a> Шаг 9. Резервирование портов для службы WinNat  
 Чтобы зарезервировать порты для службы WinNat, используйте следующие команды Windows PowerShell. Замените «192.168.1.100» на реальный адрес IPv4 сервера Windows Server Essentials.  
  
```powershell  
Set-NetNatTransitionConfiguration  �IPv4AddressPortPool @("192.168.1.100, 10000-47000")  
```  
  
> [!IMPORTANT]
>  Во избежании конфликтов с приложениями убедитесь, что в диапазон зарезервированных для службы WinNat портов не входит порт 6602.  
  
##  <a name="BKMK_WinNAT"></a> Шаг 10. Перезапуск службы WinNat  
 Перезапустите службу драйвера NAT Windows (WinNat) с помощью следующей команды Windows PowerShell.  
  
```powershell  
Restart-Service winnat  
```  
  
##  <a name="BKMK_AppendixBPowerShellScript"></a> Приложение. Установка DirectAccess с помощью Windows PowerShell  
 Этот раздел описывает установку и настройку DirectAccess с помощью Windows PowerShell.  
  
### <a name="preparation"></a>Подготовка  
 Перед началом настройки сервера для DirectAccess необходимо выполнить следующие действия.  
  
1.  Выполните процедуру, описанную в [Step 3: Подготовка сертификата и запись DNS для сервера сетевых расположений](Configure-DirectAccess-in-Windows-Server-Essentials.md#BKMK_DNS) Чтобы зарегистрировать сертификат с именем **DirectAccess-NLS.contoso.com** (где **contoso.com** заменяется реальный Имя внутреннего домена) и добавить запись DNS для сервера сетевых расположений (NLS).  
  
2.  Добавьте группу безопасности под названием **DirectAccessClients** в Active Directory, а затем добавьте клиентские компьютеры, которым следует предоставить доступ к функциям DirectAccess. Дополнительные сведения см. в разделе [Step 4: Создайте группу безопасности для клиента DirectAccess компьютеров](#BKMK_AddSecurityGroup).  
  
### <a name="commands"></a>Команды  
  
> [!IMPORTANT]
>  В Windows Server Essentials вы не обязательно для удаления ненужного префикса IPv6 объекта групповой Политики. Удалите раздел кода со следующей меткой: `# [WINDOWS SERVER 2012 ESSENTIALS ONLY] Remove the unnecessary IPv6 prefix GPO`.  
  
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
  
## <a name="see-also"></a>См. также  
  
-   [Управление повсеместным доступом](Manage-Anywhere-Access-in-Windows-Server-Essentials.md)  
  
-   [Управление Windows Server Essentials](Manage-Windows-Server-Essentials.md)
