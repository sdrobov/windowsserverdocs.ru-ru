---
title: Установка HGS в существующем лесу бастиона
ms.custom: na
ms.prod: windows-server-threshold
ms.topic: article
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 147610d9dcb36dfedab3aca11ee1a64731715519
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59842225"
---
# <a name="install-hgs-in-an-existing-bastion-forest"></a>Установка HGS в существующем лесу бастиона 

>Относится к: Windows Server 2019 г., Windows Server (полугодовой канал), Windows Server 2016


## <a name="join-the-hgs-server-to-the-existing-domain"></a>Присоединить к существующему домену сервер HGS

В существующем лесу бастиона необходимо добавить HGS в корневом домене. Использование диспетчера серверов или [Add-Computer](https://go.microsoft.com/fwlink/?LinkId=821564) для присоединения к серверу HGS корневым доменом.

## <a name="add-the-hgs-server-role"></a>Добавление роли сервера HGS

Выполняйте все команды в этом разделе в сеанс PowerShell с повышенными привилегиями.

[!INCLUDE [Install the HGS server role](../../../includes/guarded-fabric-install-hgs-server-role.md)] 

Если ваш центр обработки данных леса безопасного-бастиона, где требуется присоединить узлы HGS, выполните следующие действия.
Эти действия также можно настроить 2 или более независимой HGS кластеров, присоединенных к тому же домену.

## <a name="join-the-hgs-server-to-the-existing-domain"></a>Присоединить к существующему домену сервер HGS

Использование диспетчера серверов или [Add-Computer](https://go.microsoft.com/fwlink/?LinkId=821564) соединиться с серверами HGS в нужный домен.

## <a name="prepare-active-directory-objects"></a>Подготовка объектов Active Directory

Создайте Групповая управляемая учетная запись службы и 2 группы безопасности.
Можно также предварительно подготовленный кластерных объектов Если учетная запись, при инициализации HGS с не имеет разрешения на создание объектов-компьютеров в домене.

## <a name="group-managed-service-account"></a>Групповая управляемая учетная запись службы

Групповая управляемая учетная запись службы (gMSA) — это идентификатор, используемый для извлечения и использования его сертификатов HGS. Используйте [New-ADServiceAccount](https://technet.microsoft.com/itpro/powershell/windows/addsadministration/new-adserviceaccount) для создания управляемой.
Если это первый групповой управляемой учетной записи в домене, необходимо добавить корневой ключ службы распространения ключей.

Каждый узел HGS, необходимо получить доступ к пароль групповой управляемой учетной записи.
Самый простой способ настроить это — создать группу безопасности, содержащую все узлы HGS и предоставить этой группе безопасности доступ для извлечения пароля групповой управляемой учетной записи.

После его добавления в группу безопасности, чтобы убедиться, что он получает новый членство в группе необходимо перезагрузить сервер HGS.

```powershell
# Check if the KDS root key has been set up
if (-not (Get-KdsRootKey)) {
    # Adds a KDS root key effective immediately (ignores normal 10 hour waiting period)
    Add-KdsRootKey -EffectiveTime ((Get-Date).AddHours(-10))
}

# Create a security group for HGS nodes
$hgsNodes = New-ADGroup -Name 'HgsServers' -GroupScope DomainLocal -PassThru

# Add your HGS nodes to this group
# If your HGS server object is under an organizational unit, provide the full distinguished name instead of "HGS01"
Add-ADGroupMember -Identity $hgsNodes -Members "HGS01"

# Create the gMSA
New-ADServiceAccount -Name 'HGSgMSA' -DnsHostName 'HGSgMSA.yourdomain.com' -PrincipalsAllowedToRetrieveManagedPassword $hgsNodes
```

Эта учетная запись потребует право создавать события в журнале безопасности на каждом сервере HGS.
При использовании групповой политики, чтобы настроить назначение прав пользователя, убедитесь, что предоставлены учетную запись gMSA [создания привилегий события аудита](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn221956%28v=ws.11%29) на серверах HGS.

> [!NOTE]
> Групповые управляемые учетные записи будут доступны начиная с схемы Windows Server 2012 Active Directory.
> Дополнительные сведения см. в разделе [групповую управляемую требования к учетной записи службы](https://technet.microsoft.com/library/jj128431.aspx).

## <a name="jea-security-groups"></a>Группы безопасности JEA

При настройке HGS, [Just Enough Administration (JEA)](https://aka.ms/JEAdocs) PowerShell конечная точка настроена на позволяют администраторам управлять без необходимости полный локальный администратор HGS.
Вам не требуется управлять с помощью JEA HGS, но он по-прежнему должен быть настроен при запуске Initialize HgsServer.
Конфигурация конечной точки JEA состоит из обозначения 2 группы безопасности, которые содержат ваших администраторов HGS и рецензенты HGS.
Пользователям, которые входят в группу администраторов можно добавить, изменить или удалить политики на HGS; Рецензенты могут только просматривать текущую конфигурацию.

Создайте две группы безопасности для этих групп JEA с помощью средств администрирования Active Directory или [New-ADGroup](https://technet.microsoft.com/itpro/powershell/windows/addsadministration/new-adgroup).

```powershell
New-ADGroup -Name 'HgsJeaReviewers' -GroupScope DomainLocal
New-ADGroup -Name 'HgsJeaAdmins' -GroupScope DomainLocal
```

## <a name="cluster-objects"></a>Объекты кластера

Если учетная запись, которую вы используете для настройки HGS не имеет разрешения на создание новых объектов-компьютеров в домене, необходимо будет выполнить предварительную подготовку кластерных объектов.
Эти действия описаны в [Предварительная подготовка кластеризованных объектов-компьютеров в доменных службах Active Directory](https://technet.microsoft.com/library/dn466519(v=ws.11).aspx).

Чтобы настроить ваш первый узел HGS, необходимо будет создать один объект имени кластера (CNO) и один виртуальный компьютер объекта (VCO).
CNO представляет имя кластера, а в основном используется внутри отказоустойчивой кластеризации.
VCO представляет службу HGS, которая находится в верхней части кластера и будет иметь имя, зарегистрированное на DNS-сервере.

> [!IMPORTANT]
> Пользователь, запускающий `Initialize-HgsServer` требует **полный контроль** над объектами CNO и VCO в Active Directory.

Быстро предварительной подготовки к CNO и VCO, у администратора Active Directory выполните следующие команды PowerShell:

```powershell
# Create the CNO
$cno = New-ADComputer -Name 'HgsCluster' -Description 'HGS CNO' -Enabled $false -Passthru

# Create the VCO
$vco = New-ADComputer -Name 'HgsService' -Description 'HGS VCO' -Passthru

# Give the CNO full control over the VCO
$vcoPath = Join-Path "AD:\" $vco.DistinguishedName
$acl = Get-Acl $vcoPath
$ace = New-Object System.DirectoryServices.ActiveDirectoryAccessRule $cno.SID, "GenericAll", "Allow"
$acl.AddAccessRule($ace)
Set-Acl -Path $vcoPath -AclObject $acl

# Allow time for your new CNO and VCO to replicate to your other Domain Controllers before continuing
```

## <a name="security-baseline-exceptions"></a>Базовые исключения безопасности

При развертывании в среде с высокой степенью заблокированном HGS, определенных параметров групповой политики может помешать HGS двигатель нормально работает.
Проверьте объектов групповой политики для следующих параметров и следуйте указаниям, если при работе:

### <a name="network-logon"></a>Вход в сеть

**Путь политики:** Компьютер Конфигурация компьютера\Параметры Windows\Параметры безопасности\Локальные политики\Назначение прав назначений

**Имя политики:** Отказ в доступе к компьютеру из сети

**Обязательное значение:** Убедитесь, что значение не будет блокировать сетевой вход для всех локальных учетных записей. Вы можете безопасно заблокировать учетные записи локальных администраторов, тем не менее.

**Причина:** Отказоустойчивой кластеризации зависит от локальной учетной записи без прав администратора вызывается CLIUSR для управления узлами кластера. Блокировки входа в сеть для этого пользователя будет препятствовать кластер работает правильно.

### <a name="kerberos-encryption"></a>Шифрование Kerberos

**Путь политики:** Конфигурация компьютера\Параметры Windows\Параметры безопасности\Локальные политики\Параметры безопасности

**Имя политики:** Сетевая безопасность: Настройка типов шифрования, разрешенных Kerberos

**Действие**: Если эта политика настроена, необходимо обновить учетную запись gMSA с [Set-ADServiceAccount](https://docs.microsoft.com/powershell/module/addsadministration/set-adserviceaccount?view=win10-ps) для использования только поддерживаемые типы шифрования в этой политике. Например если ваша политика разрешает только AES128\_HMAC\_SHA1 и AES256\_HMAC\_SHA1, следует запустить `Set-ADServiceAccount -Identity HGSgMSA -KerberosEncryptionType AES128,AES256`.



## <a name="next-steps"></a>Следующие шаги

- Дальнейшие действия для настройки аттестации на основе доверенного платформенного МОДУЛЯ, см. в разделе [инициализировать HGS кластера с помощью режима доверенного платформенного МОДУЛЯ в существующем лесу бастиона](guarded-fabric-initialize-hgs-tpm-mode-bastion.md).
- Для выполнения следующих действий настроить аттестацию ключей узла, см. в разделе [инициализировать HGS кластера с помощью режима клавиши в существующем лесу бастиона](guarded-fabric-initialize-hgs-key-mode-bastion.md).
- Для следующего действия по настройке аттестации на основе администратора (является устаревшим в Windows Server 2019), см. в разделе [инициализировать кластер HGS, режиме AD в существующем лесу бастиона](guarded-fabric-initialize-hgs-ad-mode-bastion.md).

