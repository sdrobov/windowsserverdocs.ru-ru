---
title: Шаг 2 Настройка серверов DirectAccess с расширенными параметрами
description: Этот раздел является частью руководства развертывание одиночного сервера DirectAccess с Дополнительные параметры для Windows Server 2016
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology:
- networking-da
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 35afec8e-39a4-463b-839a-3c300ab01174
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 0d51ac71fa2fbe4d0bb7121a9ef511524c47f4f4
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59826615"
---
# <a name="step-2-configure-advanced-directaccess-servers"></a>Шаг 2 Настройка серверов DirectAccess с расширенными параметрами

>Область применения. Windows Server (полугодовой канал), Windows Server 2016

В этом разделе описывается, как настроить параметры клиента и сервера, необходимые для расширенного развертывания службы удаленного доступа, в котором используется один сервер удаленного доступа в смешанной среде с поддержкой IPv4 и IPv6. Перед началом развертывания убедитесь, что выполнены действия по планированию, описанные в [Планирование расширенного развертывания DirectAccess](Plan-an-Advanced-DirectAccess-Deployment.md).  
  
|Задача|Описание|  
|----|--------|  
|2.1. Установка роли удаленного доступа|Установите роль удаленного доступа.|  
|2.2. Настройка типа развертывания|Настройте тип развертывания как DirectAccess и VPN, только DirectAccess или только VPN.|  
|[Планирование развертывания DirectAccess с расширенными параметрами](Plan-an-Advanced-DirectAccess-Deployment.md)|Настройте сервер удаленного доступа с использованием групп безопасности, содержащими клиенты DirectAccess.|  
|2.4. Настройка сервера удаленного доступа|Настройте параметры сервера удаленного доступа.|  
|2.5. Настройка серверов инфраструктуры|Настройте серверы инфраструктуры, используемые в организации.|  
|2.6. Настройка серверов приложений|Настройте серверы приложений так, чтобы они требовали применения проверки подлинности и шифрования.|  
|2.7. Сводка конфигурации и альтернативные объекты групповой политики|Просмотрите сводку конфигурации удаленного доступа и при необходимости измените объекты GPO.|  
|2.8. Настройка сервера удаленного доступа с помощью Windows PowerShell|Настройка удаленного доступа с помощью Windows PowerShell.|  
  
> [!NOTE]  
> В этом разделе приводятся примеры командлетов Windows PowerShell, которые можно использовать для автоматизации некоторых описанных процедур. Дополнительные сведения см. в разделе [Командлеты](https://go.microsoft.com/fwlink/p/?linkid=230693).  
  
## <a name="BKMK_Role"></a>2.1. Установка роли удаленного доступа  
Для развертывания службы удаленного доступа необходимо установить роль удаленного доступа на сервере в организации, который будет действовать как сервер удаленного доступа.  
  
#### <a name="to-install-the-remote-access-role"></a>Установка роли удаленного доступа  
  
1.  На сервере удаленного доступа в консоли диспетчера сервера в **панели мониторинга**, нажмите кнопку **Добавить роли и компоненты**.  
  
2.  Нажмите кнопку **Далее** трижды, чтобы перейти на страницу **выбора роли сервера**.  
  
3.  На странице **Выбор ролей сервера** выберите **Удаленный доступ**, щелкните **Добавить компоненты**, а затем нажмите кнопку **Далее**.  
  
4.  Нажмите кнопку **Далее** пять раз.  
  
5.  На странице **Подтверждение выбранных элементов для установки** нажмите кнопку **Установить**.  
  
6.  На странице **Ход установки** убедитесь в успешном завершении установки, а затем нажмите кнопку **Закрыть**.  
  
![Ход выполнения успешной установки](../../../media/Step-2-Configuring-DirectAccess-Servers/PowerShellLogoSmall.gif)****Windows PowerShell эквивалентные команды****  
  
Следующие командлеты Windows PowerShell выполняют ту же функцию, что и предыдущая процедура. Вводите каждый командлет в одной строке, несмотря на то, что здесь они могут отображаться разбитыми на несколько строк из-за ограничений форматирования.  
  
```  
Install-WindowsFeature RemoteAccess -IncludeManagementTools  
```  
  
## <a name="BKMK_Deploy"></a>2.2. Настройка типа развертывания  
Службу удаленного доступа можно развернуть с помощью консоли управления удаленным доступом тремя способами:  
  
-   DirectAccess и VPN;  
  
-   только DirectAccess;  
  
-   только VPN.  
  
В примерах в данном руководстве используется развертывание только с DirectAccess.  
  
#### <a name="to-configure-the-deployment-type"></a>Настройка типа развертывания  
  
1.  На сервере удаленного доступа откройте консоль управления удаленным доступом: На **запустить** введите**RAMgmtUI.exe**, и нажмите клавишу ВВОД. Если появится диалоговое окно **контроля учетных записей**, подтвердите, что отображаемое в нем действие именно то, которое требуется, и нажмите кнопку **Да**.  
  
2.  В средней области консоли управления удаленным доступом щелкните **Запустить мастер настройки удаленного доступа**.  
  
3.  В диалоговом окне **Настройка удаленного доступа** выберите, будет ли развернут DirectAccess и VPN, только DirectAccess или только VPN.  
  
## <a name="BKMK_Clients"></a>2.3. Настройка клиентов DirectAccess  
Чтобы настроить клиентский компьютер для использования DirectAccess, он должен принадлежать выбранной группе безопасности. После настройки DirectAccess клиентские компьютеры в группе безопасности настраиваются для получения объекта групповой политики (GPO) DirectAccess. Вы также может настроить сценарий развертываний, позволяющий настроить DirectAccess для клиентского доступа и удаленного управления или только удаленного управления.  
  
#### <a name="to-configure-directaccess-clients"></a>Настройка клиентов DirectAccess  
  
1.  В средней области консоли управления удаленным доступом в разделе **Этап 1. Удаленные клиенты** щелкните **Настроить**.  
  
2.  В мастере настройки клиента DirectAccess на странице **Сценарий развертывания** выберите сценарий развертывания, который будет использовать в организации (**Полный DirectAccess** или **Только удаленное управление**), а затем нажмите кнопку **Далее**.  
  
3.  На странице **Выбор групп** щелкните **Добавить**.  
  
4.  В диалоговом окне **Выбор групп** выберите группы безопасности, в которые входят клиентские компьютеры DirectAccess.  
  
    > [!NOTE]  
    > Если группа безопасности расположена не в том же лесу, где находится сервер удаленного доступа, после завершения работы мастера настройки удаленного доступа щелкните **Обновить серверы управления** в области **Задачи**, чтобы найти контроллеры домена и серверы System Center Configuration Manager в новом лесу.  
  
5.  Установите флажок **Разрешить DirectAccess только для мобильных компьютеров**, чтобы предоставить доступ к внутренней сети только мобильным компьютерам.  
  
6.  При необходимости установите флажок **Использовать принудительное туннелирование**, чтобы направлять весь клиентский трафик (во внутреннюю сеть и в Интернет) через сервер удаленного доступа.  
  
7.  Нажмите кнопку **Далее**.  
  
8.  На странице **Помощник по подключению к сети**:  
  
    -   Добавьте в таблицу ресурсы, которые будут использоваться для определения возможности подключения к внутренней сети. Если другие ресурсы не настроены, веб-проба по умолчанию создается автоматически.  
  
        > [!CAUTION]  
        > При настройке расположений веб-пробы для определения возможности подключения к корпоративной сети убедитесь, настроен по крайней мере одна проба на основе HTTP. Только одной пробы **ping** будет недостаточно, это может привести к неточному определению возможности подключения. Это связано с тем, что для **ping** существует исключение в IPsec, в результате невозможно определить, правильно ли настроены туннели IPsec.  
  
    -   Добавьте адрес электронной почты службы поддержки, чтобы позволить пользователям отправлять информацию при возникновении проблем с подключением.  
  
    -   Введите понятное имя для подключения DirectAccess. Это имя отображается в списке сетей, когда пользователь щелкает значок сети в области уведомлений.  
  
    -   При необходимости установите флажок **Разрешить клиентам DirectAccess использовать локальное разрешение имен**.  
  
        > [!NOTE]  
        > Если локальное разрешение имен разрешено, пользователи, запускающие помощник по подключению к сети, могут выбрать возможность разрешения имен с помощью DNS-серверов, настроенных на клиентском компьютере DirectAccess.  
  
9. Нажмите кнопку **Готово**.  
  
## <a name="BKMK_Server"></a>2.4. Настройка сервера удаленного доступа  
Для развертывания службы удаленного доступа необходимо настроить сервер удаленного доступа с соответствующими сетевыми адаптерами, URL-адрес сервера удаленного доступа, к которому будут подключаться клиентские компьютеры (адрес ConnectTo), сертификат IP-HTTPS с субъектом, соответствующим адресу ConnectTo, параметры IPv6 и проверку подлинности клиентских компьютеров.  
  
#### <a name="to-configure-the-remote-access-server"></a>Настройка сервера удаленного доступа  
  
1.  В средней области консоли управления удаленным доступом в разделе **Этап 2. Сервер удаленного доступа** щелкните **Настроить**.  
  
2.  На странице **Топология сети** мастера настройки сервера удаленного доступа выберите топологию, которая будет использоваться в вашей организации. В поле **Введите общедоступное имя или IPv4-адрес, используемые клиентами для подключения к серверу удаленного доступа** введите общедоступное имя развертывания (оно совпадает с именем субъекта сертификата IP-HTTPS, например edge1.contoso.com), а затем нажмите кнопку **Далее**.  
  
3.  На странице **Сетевые адаптеры** мастер автоматически обнаруживает сетевые адаптеры для сетей в вашем развертывании. Если мастер не определяет правильные сетевые адаптеры, вручную выберите нужные адаптеры. Мастер также автоматически определяет сертификат IP-HTTPS на основе общедоступного имя развертывания, заданного на предыдущем шаге мастера. Если мастер не обнаруживает верный сертификат IP-HTTPS, нажмите кнопку **Обзор**, чтобы вручную выбрать правильный сертификат, и нажмите **Далее**.  
  
4.  На странице **Конфигурация префикса** (она отображается, только если во внутренней сети развернут протокол IPv6) мастер автоматически определяет параметры IPv6, используемые во внутренней сети. Если для развертывания требуются дополнительные префиксы, настройте префиксы IPv6 для внутренней сети, префикс IPv6, который будет назначен клиентским компьютерам DirectAccess, и префикс IPv6, который будет назначен клиентским компьютерам VPN.  
  
    > [!NOTE]  
    > Можно указать несколько внутренних префиксов IPv6 в списке, разделенным точкой запятой, например: 2001:db8:1::/48;2001:db8:2::/48.  
  
5.  На странице **Проверка подлинности** выполните следующие действия.  
  
    -   В разделе **Проверка подлинности пользователя** щелкните **Учетные данные Active Directory**. Чтобы настроить развертывание с использованием двухфакторной проверки подлинности, щелкните **Двухфакторная проверка подлинности**. Дополнительные сведения см. в разделе [Развертывание удаленного доступа с проверкой подлинности с помощью OTP](https://technet.microsoft.com/library/hh831379.aspx).  
  
    -   Для развертываний с несколькими сайтами и двухфакторной проверкой подлинности необходимо использовать проверку подлинности с сертификатом компьютера. Установите флажок **Использовать сертификаты компьютеры**, чтобы использовать проверку подлинности с сертификатами компьютера, и выберите корневой сертификат IPsec.  
  
    -   Чтобы предоставить клиентским компьютерам Windows 7 подключаться с помощью DirectAccess, выберите **Разрешить Windows клиентским компьютерам 7 подключаться с помощью DirectAccess** "флажок".  
  
        > [!NOTE]  
        > В этом типе развертывания также следует использовать проверку подлинности с сертификатом компьютера.  
  
6.  Нажмите кнопку **Готово**.  
  
## <a name="BKMK_Infra"></a>2.5. Настройка серверов инфраструктуры  
Для настройки серверов инфраструктуры в развертывании удаленного доступа необходимо настроить сервер сетевых расположений, параметры DNS (в том числе список поиска суффиксов DNS) и серверы управления, которые не обнаруживаются автоматически службой удаленного доступа.  
  
#### <a name="to-configure-the-infrastructure-servers"></a>Настройка серверов инфраструктуры  
  
1.  В средней области консоли управления удаленным доступом в разделе **Этап 3. Серверы инфраструктуры** щелкните **Настроить**.  
  
2.  На странице **Сервер сетевых расположений** мастера настройки серверов инфраструктуры щелкните параметр, соответствующий расположению сервера сетевых расположений в вашем развертывании. Если сервер сетевых расположений находится на удаленном веб-сервере, введите его URL-адрес и нажмите кнопку **Проверить**. Если сервер сетевых расположений размещен на сервере удаленного доступа, нажмите кнопку **Обзор**, чтобы найти соответствующий сертификат, а затем нажмите **Далее**.  
  
3.  На странице **DNS** в таблице введите любые дополнительные суффиксы имен, которые применяются как исключения таблицы NRPT. Выберите параметр локального разрешения имен и нажмите кнопку **Далее**.  
  
4.  На странице **Список DNS-суффиксов** сервер удаленного доступа автоматически обнаруживает все суффиксы в развертывании. С помощью кнопок **Добавить** и **Удалить**, чтобы добавить или удалить суффиксы доменов из списка. Чтобы добавить новый суффикс домена, в поле **Новый суффикс** введите суффикс и нажмите кнопку **Добавить**. Нажмите кнопку **Далее**.  
  
5.  На странице **Управление** добавьте все серверы управления, которые не были определены автоматически, и нажмите кнопку **Далее**. Служба удаленного доступа автоматически добавляет контроллеры домена и серверы System Center Configuration Manager.  
  
    > [!NOTE]  
    > Несмотря на то, что указанные серверы будут добавлены автоматически, они не отображаются в списке. Серверы System Center Configuration Manager будут показаны в списке после первого применения конфигурации.  
  
6.  Нажмите кнопку **Готово**.  
  
## <a name="BKMK_App"></a>2.6. Настройка серверов приложений  
В развертывании удаленного доступа настраивать серверы приложений необязательно. Служба удаленного доступа позволяет принудительно использовать проверку подлинности для выбранных серверов приложений, которые включены в группу безопасности серверов приложений. По умолчанию трафик на серверы приложений, требующие проверки подлинности, также шифруется. Однако вы можете отказаться от шифрования трафика для серверов приложений и использовать только проверку подлинности.  
  
> [!NOTE]  
> Проверка подлинности без шифрования поддерживается только на серверах приложений под управлением Windows Server 2012 R2, Windows Server 2012 или Windows Server 2008 R2.  
  
#### <a name="to-configure-application-servers"></a>Настройка серверов приложений  
  
1.  В средней области консоли управления удаленным доступом в разделе **Этап 4. Серверы приложений** щелкните **Настроить**.  
  
2.  В мастере настройки сервера приложений DirectAccess щелкните **Использовать сквозную проверку подлинности для выбранных серверов приложений**, чтобы принудительно использовать проверку подлинности для выбранных серверов приложений. Нажмите кнопку **Добавить**, чтобы выбрать группу безопасности сервера приложений.  
  
3.  Чтобы предоставить доступ только для группы безопасности серверов приложений, установите флажок **Разрешить доступ только серверам, включенным в группы безопасности**.  
  
4.  Чтобы использовать проверку подлинности без шифрования, выберите **не шифровать трафик. Использовать проверку подлинности только** "флажок".  
  
5.  Нажмите кнопку **Готово**.  
  
## <a name="BKMK_GPO"></a>2.7. Сводка конфигурации и альтернативные объекты групповой политики  
После завершения настройки удаленного доступа отображается окно **Сведения об удаленном доступе**. Вы можете просмотреть все параметры, выбранные ранее, в том числе следующие.  
  
1.  **Параметры объектов групповой политики**: отображаются имя GPO сервера DirectAccess и имя GPO клиента. Кроме того, вы можете перейти по ссылке **Изменить** рядом с заголовком **Параметры объектов групповой политики**, чтобы изменить параметры GPO.  
  
2.  **Удаленные клиенты**: отображается конфигурация клиента DirectAccess, в том числе группа безопасности, состояние принудительного туннелирования, средства проверки подключения и имя подключения DirectAccess.  
  
3.  **Сервер удаленного доступа**: отображается конфигурация DirectAccess, в том числе общедоступное имя и адрес, конфигурация сетевого адаптера, сведения о сертификате и одноразового пароля (если он настроен).  
  
4.  **Серверы инфраструктуры**: этот список содержит URL-адрес сервера сетевых расположений, DNS-суффиксы, используемые клиентами DirectAccess, и сведения о серверах управления.  
  
5.  **Серверы приложений**: отображается состояние удаленного управления DirectAccess, а также состояние сквозной проверки подлинности для определенных серверов приложений.  
  
## <a name="BKMK_PS"></a>2.8. Настройка сервера удаленного доступа с помощью Windows PowerShell  
![Windows PowerShell](../../../media/Step-2-Configuring-DirectAccess-Servers/PowerShellLogoSmall.gif)**эквивалентные команды Windows PowerShell**  
  
Следующие командлеты Windows PowerShell выполняют ту же функцию, что и предыдущая процедура. Вводите каждый командлет в одной строке, несмотря на то, что здесь они могут отображаться разбитыми на несколько строк из-за ограничений форматирования.  
  
Чтобы выполнить полную установку в пограничной топологии удаленного доступа только для DirectAccess в домене с корневым элементом **corp.contoso.com** и с использованием следующих параметров: объект GPO сервера: **DirectAccess Server Settings**, объект GPO клиента: Параметры клиента DirectAccess, адаптер внутренней сети: **Corpnet**, внешний сетевой адаптер: **Интернет**, адрес ConnectTo: **edge1.contoso.com**и сервер сетевых расположений: **nls.corp.contoso.com**:  
  
```  
Install-RemoteAccess -Force -PassThru -ServerGpoName 'corp.contoso.com\DirectAccess Server Settings' -ClientGpoName 'corp.contoso.com\DirectAccess Client Settings' -DAInstallType 'FullInstall' -InternetInterface 'Internet' -InternalInterface 'Corpnet' -ConnectToAddress 'edge1.contoso.com' -NlsUrl 'https://nls.corp.contoso.com/'  
```  
  
Чтобы настроить сервер удаленного доступа для использования проверки подлинности с сертификатом компьютера и корневым сертификатом IPsec, выданным ЦС CORP-APP1-CA, выполните следующие действия.  
  
```  
$certs = Get-ChildItem Cert:\LocalMachine\Root  
$IPsecRootCert = $certs | Where-Object {$_.Subject -Match "corp-APP1-CA"}  
Set-DAServer -IPsecRootCertificate $IPsecRootCert  
```  
  
Чтобы добавить группу безопасности, в которую входят клиенты DirectAccess, с именем **DirectAccessClients** и удалить группу безопасности "Компьютеры домена" по умолчанию, выполните следующие действия.  
  
```  
Add-DAClient -SecurityGroupNameList @('corp.contoso.com\DirectAccessClients')  
Remove-DAClient -SecurityGroupNameList @('corp.contoso.com\Domain Computers')  
```  
  
Чтобы включить удаленный доступ для всех компьютеров (не только записные книжки, так и переносные компьютеры) и позволяет клиентам удаленного доступа для 7 Windows:  
  
```  
Set-DAClient -OnlyRemoteComputers 'Disabled' -Downlevel 'Enabled'  
```  
  
Чтобы настроить работу клиентов DirectAccess, в том числе понятное имя подключения и URL-адрес веб-пробы, выполните следующие действия.  
  
```  
Set-DAClientExperienceConfiguration -FriendlyName 'Contoso DirectAccess Connection' -PreferLocalNamesAllowed $False -PolicyStore 'corp.contoso.com\DirectAccess Client Settings' -CorporateResources @('HTTP:https://directaccess-WebProbeHost.corp.contoso.com')  
```  
  
## <a name="BKMK_Links"></a>Предыдущий шаг  
  
-   [Шаг 1. Настраивать сложную инфраструктуру DirectAccess](da-adv-configure-s1-infrastructure.md)  
  
## <a name="next-step"></a>Дальнейшие действия  
  
-   [Шаг 3. Проверка развертывания](Step-3-Verify-the-Deployment.md)  
  

