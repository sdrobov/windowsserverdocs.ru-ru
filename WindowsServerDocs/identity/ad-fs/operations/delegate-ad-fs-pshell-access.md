---
title: Делегирование доступа командлета Powershell AD FS для пользователей без прав администратора
description: Descirbes документа как делегировать разрешения, не являющимся администраторами для AD FS PowerShell описана.
author: billmath
ms.author: billmath
manager: daveba
ms.reviewer: zhvolosh
ms.date: 01/31/2019
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 265d22b045011e34192e56bdb970955b601cda56
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59883565"
---
# <a name="delegate-ad-fs-powershell-commandlet-access-to-non-admin-users"></a>Делегирование доступа командлета Powershell AD FS для пользователей без прав администратора 
По умолчанию Администрирование AD FS с помощью PowerShell можно выполнить только администраторы AD FS. Для многих крупных организаций это не может быть приемлемым рабочую модель, при работе с другими пользователями, таких как персонал службы поддержки.  

С Just Enough Administration (JEA), клиенты теперь могут делегировать определенные командлеты позволяют отдельную групп.  
Хорошим примером этого варианта использования разрешает сотрудников службы поддержки для запроса службы федерации Active Directory, состояние блокировки учетной записи и сбросить состояние блокировки учетной записи в AD FS, как только пользователь проверены. В этом случае приведены командлеты, которые требуется делегировать. 
- `Get-ADFSAccountActivity`
- `Set-ADFSAccountActivity` 
- `Reset-ADFSAccountLockout` 

В этом примере мы используем в оставшейся части этого документа. Тем не менее можно настроить также разрешить делегирование задать свойства проверяющих сторон и передать этот режим для владельцев приложений в организации.  


##  <a name="create-the-required-groups-necessary-to-grant-users-permissions"></a>Создать требуемые группы, необходимо предоставить пользователям разрешения на доступ 
1. Создание [группе управляемой учетной записи службы](https://docs.microsoft.com/windows-server/security/group-managed-service-accounts/group-managed-service-accounts-overview). Чтобы разрешить пользователю JEA требуется доступ к сетевым ресурсам, как другими машинами или веб-службы используется групповой управляемой учетной записи. Он предоставляет удостоверение домена, которое может использоваться для проверки подлинности ресурсов на любом компьютере в домене. Учетную запись gMSA предоставляется необходимые административные права настройки. В этом примере мы называем учетной записи **gMSAContoso**. 
2. Создание Active Directory группы могут заполняться с пользователями, которые должны быть предоставлены права, делегированные команды. В этом примере сотрудников службы поддержки имеют право на чтение, обновление и сброс состояния блокировки служб федерации Active Directory. Мы называем эту группу на протяжении всего примера как **JEAContoso**. 

### <a name="install-the-gmsa-account-on-the-adfs-server"></a>Установите учетную запись gMSA на сервере служб федерации Active Directory: 
Создайте учетную запись службы, которая имеет права администратора на серверы служб федерации Active Directory. Это можно сделать на контроллере домена или удаленно, как долго как установлен пакет AD средства удаленного администрирования сервера.  Учетная запись службы должны создаваться в том же лесу, что и сервер служб федерации Active Directory. Измените значения в качестве примера в конфигурацию фермы. 

```powershell
 # This command should only be run if this is the first time gMSA accounts are enabled in the forest 
Add-KdsRootKey -EffectiveTime ((get-date).addhours(-10))  
 
# Run this on every node that you want to have JEA configured on  
$adfsServer = Get-ADComputer server01.contoso.com  
 
# Run targeted at domain controller  
$serviceaccount = New-ADServiceAccount gMSAcontoso -DNSHostName <FQDN of the domain containing the KDS key> - PrincipalsAllowedToRetrieveManagedPassword $adfsServer –passthru 
 
# Run this on every node 
Add-ADComputerServiceAccount -Identity server01.contoso.com -ServiceAccount $ServiceAccount 
```

Установите учетную запись gMSA на сервере служб федерации Active Directory.  Это необходимо запустить на каждом узле служб федерации Active Directory в ферме. 
 
```powershell
Install-ADServiceAccount gMSAcontoso 
```

### <a name="grant-the-gmsa-account-admin-rights"></a>Предоставить права администратора учетной записи gMSA 
Если в ферме используется делегированного администрирования, этот метод предоставление прав администратора учетной записи эта учетная запись, добавьте его в существующую группу, что последний делегировал права доступа администратора.  
 
Если ферма не использует делегированного администрирования, этот метод предоставление прав администратора учетной записи gMSA, сделав ее в группу локальных администраторов на всех серверах служб федерации Active Directory. 
 
 
### <a name="create-the-jea-role-file"></a>Создайте файл ролей JEA 
 
Создание ролей JEA в Блокнот. Инструкции по созданию роли предоставляется на [возможности ролей JEA](https://docs.microsoft.com/powershell/jea/role-capabilities). 
 
Командлеты, делегировать в этом примере являются `Reset-AdfsAccountLockout, Get-ADFSAccountActivity, and Set-ADFSAccountActivity`. 

Образец JEA роли Делегирование доступа из «Reset-ADFSAccountLockout», «Get-ADFSAccountActivity» и «Set-ADFSAccountActivity» командлеты:

```powershell
@{
GUID = 'b35d3985-9063-4de5-81f8-241be1f56b52'
ModulesToImport = 'adfs'
VisibleCmdlets = 'Reset-AdfsAccountLockout', 'Get-ADFSAccountActivity', 'Set-ADFSAccountActivity'
}
```


### <a name="create-the-jea-session-configuration-file"></a>Создание файла конфигурации сеанса JEA 
Следуйте инструкциям по созданию [конфигурации сеанса JEA](https://docs.microsoft.com/powershell/jea/session-configurations) файл. Файл конфигурации определяет, кто может использовать конечную точку JEA и какие возможности они имеют доступ. 

Возможности ролей для ссылки на плоский имя (имя файла без расширения) файла возможностей ролей. Если несколько возможностей ролей доступны в системе с одинаковым плоским именем, PowerShell использует неявный порядок поиска для выбора действующего файла возможностей ролей. Эта роль не предоставляет доступ ко всем файлам возможностей ролей с тем же именем. 

Чтобы указать файл возможностей ролей с путем, используйте `RoleCapabilityFiles` аргумент. Для вложенной папки, JEA искать допустимые модули Powershell, которые содержат `RoleCapabilities` во вложенную папку, где `RoleCapabilityFiles` аргумент должен быть изменен, чтобы указывать `RoleCapabilities`. 

Пример файла конфигурации сеанса. 

```powershell
@{
SchemaVersion = '2.0.0.0'
GUID = '54c8d41b-6425-46ac-a2eb-8c0184d9c6e6'
SessionType = 'RestrictedRemoteServer'
GroupManagedServiceAccount =  'CONTOSO\gMSAcontoso'
RoleDefinitions = @{ JEAcontoso = @{ RoleCapabilityFiles = 'C:\Program Files\WindowsPowershell\Modules\AccountActivityJEA\RoleCapabilities\JEAAccountActivityResetRole.psrc' } }
}
```

Сохраните файл конфигурации сеанса. 
 
Настоятельно рекомендуется для [проверить файл конфигурации сеанса](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Test-PSSessionConfigurationFile?view=powershell-5.1) после редактирования pssc-файле вручную в текстовом редакторе, чтобы обеспечить синтаксис правильный. Если файл конфигурации сеанса не проходит эту проверку, он успешно не зарегистрирован в системе.  
 
### <a name="install-the-jea-session-configuration-on-the-ad-fs-server"></a>Установка конфигурации сеанса JEA на сервере AD FS 

Установка конфигурации сеанса JEA на сервере AD FS 
 
```powershell
Register-PSSessionConfiguration -Path .\JEASessionConfig.pssc -name "AccountActivityAdministration" -force
``` 
## <a name="operational-instructions"></a>Рабочие инструкции 
После установки JEA, ведение журнала и аудит может использоваться для определения if правильный пользователи имеют доступ к конечной точке JEA. 

Чтобы использовать делегированные команды: 

```powershell
Enter-pssession -ComputerName server01.contoso.com -ConfigurationName "AccountActivityAdministration" -Credential <User Using JEA> 
Get-AdfsAccountActivity <User> 
```
