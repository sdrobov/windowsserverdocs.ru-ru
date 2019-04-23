---
title: Переход с DirectAccess, чтобы всегда для VPN-ШЛЮЗА
description: Переход с DirectAccess на AlwaysOn VPN требуется конкретный процесс переноса клиентов, что помогает свести к минимуму гонки, которые возникают из-за выполнения шагов миграции по порядку.
manager: dougkim
ms.prod: windows-server
ms.technology: networking-ras
ms.topic: article
ms.assetid: eeca4cf7-90f0-485d-843c-76c5885c54b0
ms.author: pashort
author: shortpatti
ms.date: 06/07/2018
ms.openlocfilehash: 94852b33936ece0b329614f428e845f2c7a2ac6a
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59854585"
---
# <a name="migrate-to-always-on-vpn-and-decommission-directaccess"></a>Вывод профиля DirectAccess из эксплуатации и его перенос в постоянно подключенный VPN-профиль

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows 10

&#171;[ **Предыдущих:** Планирование DirectAccess для миграции AlwaysOn VPN](da-always-on-migration-planning.md)<br>

Переход с DirectAccess на AlwaysOn VPN требуется конкретный процесс переноса клиентов, что помогает свести к минимуму гонки, которые возникают из-за выполнения шагов миграции по порядку. На высоком уровне процесс миграции состоит из этих четырех основных шага:

1.  **Развертывание инфраструктуры VPN side-by-side.** После определения вашей этапы миграции и возможности, которые вы хотите включить в развертывание, вы развернете инфраструктуры VPN, параллельно с существующей инфраструктуры DirectAccess.  

2.  **Разверните сертификаты и конфигурации на клиентах.**  После подготовки инфраструктуры VPN, создания и публикации необходимые сертификаты на клиент. Когда клиенты получили сертификаты, развертывания сценария конфигурации VPN_Profile.ps1. Кроме того можно использовать Intune для настройки VPN-клиента. Использование Microsoft System Center Configuration Manager или Microsoft Intune для отслеживания успешных развертываниях конфигурации VPN.

3.  [!INCLUDE [remove-da-security-group-shortdesc-include](../includes/remove-da-security-group-shortdesc-include.md)]

4.  [!INCLUDE [decommission-da-shortdesc-include](../includes/decommission-da-shortdesc-include.md)]

Прежде чем начать процесс миграции с DirectAccess AlwaysOn VPN, убедитесь, что запланировано для миграции.  Если вы не планировали миграцию, см. в разделе [планирование DirectAccess для миграции AlwaysOn VPN](da-always-on-migration-planning.md).

>[!TIP] 
>В этом разделе не пошаговое руководство по развертыванию для AlwaysOn VPN, но вместо этого он предназначен для дополняют [AlwaysOn VPN развертывания для Windows Server и Windows 10](../vpn/always-on-vpn/deploy/always-on-vpn-deploy.md) и предоставления руководств по миграции развертывания.

## <a name="deploy-a-side-by-side-vpn-infrastructure"></a>Развертывание инфраструктуры VPN side-by-side

Вы развернуть инфраструктуру VPN параллельно с существующей инфраструктуры DirectAccess.  Пошаговые инструкции см. в разделе [AlwaysOn VPN развертывания для Windows Server и Windows 10](../vpn/always-on-vpn/deploy/always-on-vpn-deploy.md) для установки и настройки инфраструктуры AlwaysOn VPN. 

Side-by-side развертывания состоит из следующие высокоуровневые задачи:

1.  Создайте группы пользователей VPN, VPN-серверов и серверов политики сети.

2.  Создание и публикация шаблонов необходимый сертификат.

3.  Регистрация сертификатов сервера.

4.  Установка и настройка службы удаленного доступа для AlwaysOn VPN.

5.  Установка и настройка сервера политики сети.

6.  Настройте DNS и правил брандмауэра для AlwaysOn VPN.

Ниже приведена visual ссылка для изменения инфраструктуры, на протяжении DirectAccess к Always On миграции VPN.

![](../../media/DA-to-AlwaysOnVPN/6b64f322f945f837f22a32bf87a228f8.png)

## <a name="deploy-certificates-and-vpn-configuration-script-to-the-clients"></a>Развертывание сертификатов, а также скрипт конфигурации VPN для клиентов

Хотя основная часть конфигурации VPN-клиента в [развертывание AlwaysOn VPN](../vpn/always-on-vpn/deploy/always-on-vpn-deploy-deployment.md) разделе, два дополнительных действия необходимы для успешного завершения миграции с DirectAccess на AlwaysOn VPN. 

Необходимо убедиться, что **VPN_Profile.ps1** поставляется _после_ был выдан сертификат, чтобы VPN-клиент не пытается подключиться без него. Чтобы сделать это, выполните скрипт, который добавляет только тем пользователям, которые были зарегистрированы в сертификате отделу готовы развертывания VPN, который используется для развертывания конфигурации AlwaysOn VPN.

>[!NOTE] 
>Корпорация Майкрософт рекомендует провести тестирование этот процесс, прежде чем выполнять его на любом из вашей колец миграции пользователя.

1.  **Создание и публикация VPN-сертификат и включение автоматической регистрации объект групповой политики (GPO).** Для развертываний Windows 10 VPN стандартного, на основе сертификатов сертификат выдается на устройства или пользователя мог проверить подлинность подключения. При создании и публикации для автоматической регистрации нового сертификата проверки подлинности, необходимо создать и развернуть объект групповой Политики с параметром автоматической регистрации, заданным в группу пользователей VPN. Действия по настройке сертификатов и автоматической регистрации, см. в разделе [Настройка инфраструктуры сервера](../vpn/always-on-vpn/deploy/vpn-deploy-server-infrastructure.md).

2.  **Добавление пользователей в группу пользователей VPN.** Добавление независимо от пользователей, переместить группу пользователей VPN. Эти пользователи остаются в этой группе безопасности, после переноса их, чтобы они могли получать все обновления сертификата в будущем. Далее добавлять пользователей в эту группу, пока вы переместили каждого пользователя с DirectAccess AlwaysOn VPN. 

3.  **Определите пользователей, получивших сертификат проверки подлинности VPN.** Выполняется миграция с DirectAccess, поэтому необходимо добавить метод для определения, когда клиент получил требуемый сертификат и готов к получению сведений о конфигурации VPN. Запустите **GetUsersWithCert.ps1** сценарий для добавления пользователей, которые в настоящее время выдаются nonrevoked сертификаты, исходящий от имени указанного шаблона в указанной группе безопасности AD DS. Например, после выполнения команды **GetUsersWithCert.ps1** скрипт, любой пользователь, выданный действительный сертификат VPN-сертификат проверки подлинности, шаблон будет добавлен к группе готовности развертывания VPN.

    >[!NOTE] 
    >Если у вас способ определить, когда клиент получает требуемый сертификат, прежде чем был выдан сертификат для пользователя, вызывая сбой подключения VPN можно развернуть конфигурацию VPN. Чтобы избежать такой ситуации, выполните **GetUsersWithCert.ps1** сценарий в центре сертификации или по расписанию для синхронизации пользователей, получивших сертификат к группе готовности развертывания VPN. Затем используем эту группу безопасности для развертывания конфигурации VPN в System Center Configuration Manager или Intune, которая гарантирует, что управляемый клиент не получает конфигурацию VPN до получения сертификата.
    
    ### <a name="getuserswithcertps1"></a>GetUsersWithCert.ps1
    
    ```powershell
    Import-module ActiveDirectory
    Import-Module AdcsAdministration
    
    $TemplateName = 'VPNUserAuthentication'##Certificate Template Name (not the friendly name)
    $GroupName = 'VPN Deployment Ready' ##Group you will add the users to
    $CSServerName = 'localhost\corp-dc-ca' ##CA Server Information
    
    $users= @()
    $TemplateID = (get-CATemplate | Where-Object {$_.Name -like $TemplateName} | Select-Object oid).oid
    $View = New-Object -ComObject CertificateAuthority.View
    $NULL = $View.OpenConnection($CSServerName)
    $View.SetResultColumnCount(3)
    $i1 = $View.GetColumnIndex($false, "User Principal Name")
    $i2 = $View.GetColumnIndex($false, "Certificate Template")
    $i3 = $View.GetColumnIndex($false, "Revocation Date")
    $i1, $i2, $i3 | %{$View.SetResultColumn($_) }
    $Row= $View.OpenView()
    
    while ($Row.Next() -ne -1){
    $Cert = New-Object PsObject
    $Col = $Row.EnumCertViewColumn()
    [void]$Col.Next()
    do {
    $Cert | Add-Member -MemberType NoteProperty $($Col.GetDisplayName()) -Value $($Col.GetValue(1)) -Force
          }
    until ($Col.Next() -eq -1)
    $col = ''
    
    if($cert."Certificate Template" -eq $TemplateID -and $cert."Revocation Date" -eq $NULL){
       $users= $users+= $cert."User Principal Name"
    $temp = $cert."User Principal Name"
    $user = get-aduser -Filter {UserPrincipalName -eq $temp} –Property UserPrincipalName
    Add-ADGroupMember $GroupName $user
       }
      }
    ```

4. Развертывания конфигурации AlwaysOn VPN. Как VPN, выдаются сертификаты проверки подлинности, и вы запустите **GetUsersWithCert.ps1** скрипт, пользователи добавляются готов развертывания VPN группу безопасности.


| Если вы используете...  | То... |
| ---- | ---- |
| System Center Configuration Manager | Создайте коллекцию на основе членства в этой группе безопасности.<br><br>![](../../media/DA-to-AlwaysOnVPN/b38723b3ffcfacd697b83dd41a177f66.png)\!|
| Intune | Просто напрямую целевой группе безопасности после синхронизации. |
|
    
При каждом запуске **GetUsersWithCert.ps1** сценарий конфигурации, необходимо также выполнить правило обнаружения AD DS, чтобы обновить список членов группы безопасности в System Center Configuration Manager. Кроме того, убедитесь, что обновление членства для коллекции развертывания часто достаточно (выравнивание с правилом скрипт и обнаружения).

Дополнительные сведения о развертывании AlwaysOn VPN для клиентов Windows с помощью System Center Configuration Manager или Intune, см. в разделе [AlwaysOn VPN развертывания для Windows Server и Windows 10](../vpn/always-on-vpn/deploy/always-on-vpn-deploy.md). Следите за тем, чтобы включить эти задачи миграции конкретных.

>[!NOTE] 
>Включение этих задач, связанных с миграции есть важные отличия между простое развертывание AlwaysOn VPN и переход с DirectAccess для AlwaysOn VPN. Не забудьте правильно определение коллекции, для группы безопасности, а не с помощью метода в руководстве по развертыванию.


## <a name="remove-devices-from-the-directaccess-security-group"></a>Удалите устройства из группы безопасности DirectAccess

Как пользователи получают сертификат проверки подлинности и **VPN_Profile.ps1** сценарий конфигурации, вы увидите соответствующее успешных развертываниях скрипт конфигурации VPN в System Center Configuration Manager или Intune. После каждого развертывания удалите этого пользователя устройства из группы безопасности DirectAccess, таким образом, чтобы позже можно удалить DirectAccess. Intune и System Center Configuration Manager содержит сведения о назначении устройств пользователя для определения каждого устройства.

>[!NOTE] 
>В случае применения объектов групповой политики DirectAccess через подразделений (OU) вместо групп компьютеров, переместите объект-компьютер пользователя из Подразделения.

## <a name="decommission-the-directaccess-infrastructure"></a>Вывод из эксплуатации инфраструктуры DirectAccess

После завершения миграции всех клиентов DirectAccess в AlwaysOn VPN, можно списать инфраструктуры DirectAccess и удалить параметры DirectAccess из групповой политики. Корпорация Майкрософт рекомендует выполнять перечисленные ниже действия, чтобы корректно удалить DirectAccess из среды.

1.  [!INCLUDE [remove-config-settings-shortdesc-include](../includes/remove-config-settings-shortdesc-include.md)]

    ![](../../media/DA-to-AlwaysOnVPN/dbdc3d80e8dc1b8665f7b15d7d2ee1f6.png)

2.  [!INCLUDE [remove-da-security-group-shortdesc-include](../includes/remove-da-security-group-shortdesc-include.md)]

3.  **Очистите DNS.** Не забудьте удалить все записи из внутреннего сервера DNS и общедоступного DNS-сервера относятся к DirectAccess, например, DA.contoso.com, DAGateway.contoso.com.

4.  [!INCLUDE [decommission-da-shortdesc-include](../includes/decommission-da-shortdesc-include.md)]

5.  **Удалите все сертификаты DirectAccess из служб сертификатов Active Directory.** Если вы использовали сертификаты компьютеров для DirectAccess реализации, удалите опубликованные шаблоны из папки шаблонов сертификатов в консоли центра сертификации.

## <a name="next-step"></a>Дальнейшие действия
После миграции с DirectAccess для AlwaysOn VPN. 

---