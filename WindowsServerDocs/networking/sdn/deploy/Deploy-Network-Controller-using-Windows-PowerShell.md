---
title: Развертывание сетевого контроллера с помощью Windows PowerShell
description: В этом разделе приводятся инструкции по использованию Windows PowerShell для развертывания сетевого контроллера на один или несколько компьютеров или виртуальных машин (ВМ), работающих под управлением Windows Server 2016.
manager: dougkim
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: networking-sdn
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 2448d381-55aa-4c14-997a-202c537c6727
ms.author: pashort
author: shortpatti
ms.date: 08/23/2018
ms.openlocfilehash: d671d044896ae9e71edad8302f06f2a21fe50772
ms.sourcegitcommit: 21165734a0f37c4cd702c275e85c9e7c42d6b3cb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2019
ms.locfileid: "65034553"
---
# <a name="deploy-network-controller-using-windows-powershell"></a>Развертывание сетевого контроллера с помощью Windows PowerShell

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

В этом разделе приводятся инструкции по использованию Windows PowerShell для развертывания сетевого контроллера на один или несколько виртуальных машин (ВМ, работающих под управлением Windows Server 2016).

>[!IMPORTANT]
>Не следует развертывать роли сервера сетевого контроллера на физических узлах. Для развертывания сетевого контроллера, необходимо установить роль сервера сетевого контроллера на виртуальной машине Hyper-V \(виртуальной Машины\) , установленной на узле Hyper-V. После установки сетевого контроллера на виртуальных машинах в трех разных Hyper\-узлов V, необходимо включить Hyper\-узлы V для программно-Конфигурируемую сеть \(SDN\) путем добавления узлов с помощью сетевого контроллера Команда Windows PowerShell **New NetworkControllerServer**. Таким образом, при включении функции подсистемы балансировки нагрузки SDN программного обеспечения. Дополнительные сведения см. в разделе [New NetworkControllerServer](https://technet.microsoft.com/itpro/powershell/windows/network-controller/new-networkcontrollerserver).

Эта статья содержит следующие разделы.

- [Установка роли сервера сетевого контроллера](#install-the-network-controller-server-role)

- [Настройка кластера сетевого контроллера](#configure-the-network-controller-cluster)

- [Настройка сетевого контроллера приложения](#configure-the-network-controller-application)

- [Сетевой контроллер проверки развертывания](#network-controller-deployment-validation)

- [Дополнительные команды Windows PowerShell для сетевого контроллера](#additional-windows-powershell-commands-for-network-controller)

- [Пример сценария конфигурации сетевого контроллера](#sample-network-controller-configuration-script)

- [Действия после развертывания для развертываний, отличных от Kerberos](#post-deployment-steps-for-non-kerberos-deployments)

## <a name="install-the-network-controller-server-role"></a>Установка роли сервера сетевого контроллера

Эту процедуру можно использовать для установки роли сервера сетевого контроллера на виртуальной машине \(виртуальной Машины\).

>[!IMPORTANT]
>Не следует развертывать роли сервера сетевого контроллера на физических узлах. Для развертывания сетевого контроллера, необходимо установить роль сервера сетевого контроллера на виртуальной машине Hyper-V \(виртуальной Машины\) , установленной на узле Hyper-V. После установки сетевого контроллера на виртуальных машинах в трех разных Hyper\-узлов V, необходимо включить Hyper\-узлы V для программно-Конфигурируемую сеть \(SDN\) путем добавления узлов на сетевом контроллере. Таким образом, при включении функции подсистемы балансировки нагрузки SDN программного обеспечения.

Для выполнения этой процедуры необходимо быть членом группы **Администраторы** или пользователем с аналогичными правами.  

>[!NOTE]
>Если вы хотите вместо Windows PowerShell с помощью диспетчера серверов для установки сетевого контроллера, см. в разделе [Установка роли сервера сетевого контроллера с помощью диспетчера сервера](https://technet.microsoft.com/library/mt403348.aspx)

Для установки сетевого контроллера с помощью Windows PowerShell, введите следующие команды в командной строке Windows PowerShell и нажмите клавишу ВВОД.

`Install-WindowsFeature -Name NetworkController -IncludeManagementTools`

Установка сетевого контроллера требует перезагрузки компьютера. Для этого введите следующую команду и нажмите клавишу ВВОД.

`Restart-Computer`

## <a name="configure-the-network-controller-cluster"></a>Настройка кластера сетевого контроллера

Сетевой контроллер кластера обеспечивает высокий уровень доступности и масштабируемости для сетевого контроллера приложения, которые можно настроить после создания кластера и разместить его на основе кластера.

>[!NOTE]
>Можно выполнить процедуры, описанные в следующих разделах либо непосредственно на виртуальной Машине, где вы установили сетевого контроллера или удаленного сервера администрирования средства для Windows Server 2016 можно использовать для выполнения процедур с удаленного компьютера, на котором выполняется Windows Server 2016 или Windows 10. Кроме того, членство в группе **Администраторы**, или эквивалентной является минимальным требованием для выполнения этой процедуры. Если компьютер или виртуальную Машину, на котором установлен сетевой контроллер присоединен к домену, учетная запись пользователя должна быть членом **пользователей домена**.

Можно создать кластер сетевого контроллера, создав объект узла и последующей настройки кластера.

### <a name="create-a-node-object"></a>Создать объект узла

Необходимо создать объект узла для каждой виртуальной Машины, которая является членом кластера сетевого контроллера.

Чтобы создать объект узла, введите следующую команду в командной строке Windows PowerShell и нажмите клавишу ВВОД. Убедитесь, что добавляемые значения для каждого параметра, которые подходят для развертывания.  

```
New-NetworkControllerNodeObject -Name <string> -Server <String> -FaultDomain <string>-RestInterface <string> [-NodeCertificate <X509Certificate2>]
```

В следующей таблице приведены описания для каждого параметра **New NetworkControllerNodeObject** команды.

|Параметр|Описание|
|-------------|---------------|
|Имя|**Имя** параметр указывает понятное имя сервера, который вы хотите добавить в кластер|
|Server (Сервер)|**Server** параметр указывает имя узла, полное доменное имя (FQDN) или IP-адрес сервера, который вы хотите добавить в кластер. Для компьютеров, присоединенных к домену полное доменное имя является обязательным.|
|FaultDomain|**FaultDomain** параметр указывает домен сбоя для сервера, который вы добавляете в кластер. Этот параметр определяет серверы, которые могут возникать сбои, в то же время, что и сервер, вы добавляете в кластер. Этот сбой может быть из-за общих физических зависимостей, например электроэнергии и сетевых источников. Домены сбоя, обычно представляют собой иерархии, которые связаны с этих общих зависимостей, путем добавления серверов, скорее всего, отрабатывают из точки выше в дереве домена сбоя. Во время выполнения сетевой контроллер анализирует домены сбоя в кластере и пытается распределить службы сетевого контроллера, чтобы они были в отдельных доменах сбоя. Этот процесс помогает сохранить, в случае сбоя какого-либо домена сбоя, обеспечить безопасность доступности для этой службы и его состояния. В иерархическом формате указаны домены сбоя. Пример: «Fd: / DC1/Rack1/Host1», где DC1 — это имя центра обработки данных, Rack1 — это имя для установки в стойку и Host1 — это имя узла, где размещается узел.|
|RestInterface|**RestInterface** параметр указывает имя интерфейса на узле, где завершается communication Representational State Transfer (REST). Этот интерфейс сетевого контроллера получает запросы Северный API-Интерфейс из управления уровня сети.|
|NodeCertificate|**NodeCertificate** параметр задает сертификат, который сетевой контроллер использует для проверки подлинности компьютера. Сертификат является обязательным, если вы используете проверку подлинности на основе сертификата для обмена данными внутри кластера; сертификат также используется для шифрования трафика между службами сетевого контроллера. Имя субъекта сертификата необходимо использовать тот же DNS-имя узла.|

### <a name="configure-the-cluster"></a>Настройка кластера

Чтобы настроить кластер, введите следующую команду в командной строке Windows PowerShell и нажмите клавишу ВВОД. Убедитесь, что добавляемые значения для каждого параметра, которые подходят для развертывания.

```
Install-NetworkControllerCluster -Node <NetworkControllerNode[]> -ClusterAuthentication <ClusterAuthentication> [-ManagementSecurityGroup <string>][-DiagnosticLogLocation <string>][-LogLocationCredential <PSCredential>] [-CredentialEncryptionCertificate <X509Certificate2>][-Credential <PSCredential>][-CertificateThumbprint <String>] [-UseSSL][-ComputerName <string>][-LogSizeLimitInMBs<UInt32>] [-LogTimeLimitInDays<UInt32>]
```

В следующей таблице приведены описания для каждого параметра **Install NetworkControllerCluster** команды.
  
|Параметр|Описание|
|-------------|---------------|
|ClusterAuthentication|**ClusterAuthentication** параметр указывает тип проверки подлинности, который используется для обеспечения безопасной связи между узлами и также используется для шифрования трафика между службами сетевого контроллера. Поддерживаемые значения: **Kerberos**, **X509** и **None**. Проверка подлинности Kerberos с использованием учетных записей домена и может использоваться только если узлы сетевого контроллера, присоединенных к домену. При выборе проверки подлинности на основе X509, необходимо предоставить сертификат в объекте NetworkControllerNode. Кроме того необходимо вручную предоставить сертификат, перед выполнением этой команды.|
|ManagementSecurityGroup|**ManagementSecurityGroup** параметр указывает имя группы безопасности, содержащую пользователей, которым разрешено выполнять командлеты управления с удаленного компьютера. Это значение применимо только если ClusterAuthentication Kerberos. Необходимо указать группу безопасности домена и не группу безопасности на локальном компьютере.|
|Узел|**Узел** параметр указывает список узлов сетевого контроллера, созданных с помощью **New NetworkControllerNodeObject** команды.|
|DiagnosticLogLocation|**DiagnosticLogLocation** параметр указывает расположение общей папки, где периодически загружаться журналы диагностики. Если значение этого параметра не указано, журналы хранятся локально на каждом узле. Журналы хранятся локально в папке % systemdrive%\Windows\tracing\SDNDiagnostics. Журналы кластера хранятся локально в папке %systemdrive%\ProgramData\Microsoft\Service Fabric\log\Traces.|
|LogLocationCredential|**LogLocationCredential** параметр задает учетные данные, которые требуются для доступа к общей папке, где хранятся журналы.|
|CredentialEncryptionCertificate|**CredentialEncryptionCertificate** параметр задает сертификат, который сетевой контроллер использует для шифрования учетных данных, которые используются для доступа к сетевым контроллером двоичные файлы и  **LogLocationCredential**, если он указан. На всех узлах сетевого контроллера, прежде чем выполнять эту команду необходимо подготовить сертификат и тот же сертификат должен быть зарегистрирован на всех узлах кластера. В рабочей среде рекомендуется использовать этот параметр для защиты сетевого контроллера двоичные файлы и журналы. Без этого параметра учетные данные хранятся в виде открытого текста и потенциально может спровоцировать злоупотребления любой несанкционированный пользователь.|
|Учетные данные|Этот параметр является обязательным только в том случае, если при выполнении этой команды на удаленном компьютере. **Учетных данных** параметр указывает учетную запись пользователя, которая имеет разрешение для выполнения этой команды на целевом компьютере.|
|CertificateThumbprint|Этот параметр является обязательным только в том случае, если при выполнении этой команды на удаленном компьютере. **CertificateThumbprint** параметр задает цифровой сертификат открытого ключа (X509) учетной записи пользователя, имеющую разрешение для выполнения этой команды на целевом компьютере.|
|UseSSL|Этот параметр является обязательным только в том случае, если при выполнении этой команды на удаленном компьютере. **UseSSL** параметр указывает протокол Secure Sockets Layer (SSL), который используется для установления подключения к удаленному компьютеру. По умолчанию SSL не используется.|
|имя_компьютера|**ComputerName** узла сетевого контроллера, на котором выполняется эта команда задает параметр. Если значение этого параметра не указано, по умолчанию используется локальный компьютер.|
|LogSizeLimitInMBs|Этот параметр указывает максимальный размер журнала, в МБ, который может хранить сетевого контроллера. Журналы хранятся в очереди. Если DiagnosticLogLocation предоставляется, значение по умолчанию этого параметра — 40 ГБ. Если DiagnosticLogLocation не указан, журналы хранятся на узлах сетевого контроллера, и значение по умолчанию этого параметра — 15 ГБ.|
|LogTimeLimitInDays|Этот параметр указывает ограничение длительности в днях, для которых хранятся журналы. Журналы хранятся в очереди. Значение по умолчанию этого параметра — 3 дня.|

## <a name="configure-the-network-controller-application"></a>Настройка сетевого контроллера приложения
Чтобы настроить приложение сетевого контроллера, введите следующую команду в командной строке Windows PowerShell и нажмите клавишу ВВОД. Убедитесь, что добавляемые значения для каждого параметра, которые подходят для развертывания.

```
Install-NetworkController -Node <NetworkControllerNode[]> -ClientAuthentication <ClientAuthentication>  [-ClientCertificateThumbprint <string[]>]  [-ClientSecurityGroup <string>] -ServerCertificate <X509Certificate2> [-RESTIPAddress <String>] [-RESTName <String>] [-Credential <PSCredential>][-CertificateThumbprint <String> ] [-UseSSL]
```

В следующей таблице приведены описания для каждого параметра **Install NetworkController** команды.

|Параметр|Описание|
|-------------|---------------|
|Проверки подлинности клиента|**ClientAuthentication** параметр указывает тип проверки подлинности, который используется для обеспечения безопасной связи между REST и сетевом контроллере. Поддерживаемые значения: **Kerberos**, **X509** и **None**. Проверка подлинности Kerberos с использованием учетных записей домена и может использоваться только если узлы сетевого контроллера, присоединенных к домену. При выборе проверки подлинности на основе X509, необходимо предоставить сертификат в объекте NetworkControllerNode. Кроме того необходимо вручную предоставить сертификат, перед выполнением этой команды.|
|Узел|**Узел** параметр указывает список узлов сетевого контроллера, созданных с помощью **New NetworkControllerNodeObject** команды.|
|ClientCertificateThumbprint|Этот параметр является обязательным только в том случае, если вы используете проверку подлинности на основе сертификата для клиентов сетевого контроллера. **ClientCertificateThumbprint** задает отпечаток сертификата, который зарегистрирован для клиентов Северный слоя.|
|ServerCertificate|**ServerCertificate** параметр задает сертификат, который сетевой контроллер использует для подтверждения его подлинности для клиентов. Сертификат сервера должен содержать проверка подлинности сервера в расширениях расширенное использование ключа и должен быть выдан центром сертификации, которому доверяют клиенты для сетевого контроллера.|
|RESTIPAddress|Необходимо указать значение для **RESTIPAddress** с одним узлом развертывания сетевого контроллера. Для развертываний с несколькими узлами **RESTIPAddress** параметр указывает IP-адрес конечной точки REST в нотации CIDR. Например 192.168.1.10/24. Значение имени субъекта **ServerCertificate** должно разрешаться как значение **RESTIPAddress** параметра. Этот параметр должен быть указан для всех развертываний несколько узлов сетевого контроллера, когда все узлы находятся в той же подсети. Если узлы находятся в разных подсетях, необходимо использовать **RestName** параметра вместо использования **RESTIPAddress**.|
|RestName|Необходимо указать значение для **RestName** с одним узлом развертывания сетевого контроллера. Единственный случай, когда необходимо указать значение для **RestName** является ситуация, когда несколько узлов развертываний узлов, которые находятся в разных подсетях. Для развертываний с несколькими узлами **RestName** параметр полное доменное имя кластера сетевого контроллера.|
|ClientSecurityGroup|**ClientSecurityGroup** параметр указывает имя группы безопасности Active Directory, членами которой являются клиентов сетевого контроллера. Этот параметр является обязательным только в том случае, если вы используете проверку подлинности Kerberos для **ClientAuthentication**. Группа безопасности может содержать учетные записи, с которых осуществляется интерфейсы REST API, и необходимо создать группу безопасности и добавить элементы перед выполнением этой команды.|
|Учетные данные|Этот параметр является обязательным только в том случае, если при выполнении этой команды на удаленном компьютере. **Учетных данных** параметр указывает учетную запись пользователя, которая имеет разрешение для выполнения этой команды на целевом компьютере.|
|CertificateThumbprint|Этот параметр является обязательным только в том случае, если при выполнении этой команды на удаленном компьютере. **CertificateThumbprint** параметр задает цифровой сертификат открытого ключа (X509) учетной записи пользователя, имеющую разрешение для выполнения этой команды на целевом компьютере.|
|UseSSL|Этот параметр является обязательным только в том случае, если при выполнении этой команды на удаленном компьютере. **UseSSL** параметр указывает протокол Secure Sockets Layer (SSL), который используется для установления подключения к удаленному компьютеру. По умолчанию SSL не используется.|

После завершения настройки сетевого контроллера приложения, развертывание сетевого контроллера будет завершена.

## <a name="network-controller-deployment-validation"></a>Сетевой контроллер проверки развертывания

Чтобы проверить развернутую службу сетевого контроллера, можно добавить учетные данные для сетевого контроллера и затем получить учетные данные.

Если вы используете Kerberos в качестве механизма проверки подлинности клиента, членство в группе **ClientSecurityGroup** , созданного является минимальным требованием для выполнения этой процедуры.

**Процедура.**

1.  На клиентском компьютере, при использовании Kerberos в качестве механизма проверки подлинности клиента, войдите с учетной записью пользователя, который является членом вашего **ClientSecurityGroup**.

2. Откройте Windows PowerShell, введите следующие команды, чтобы добавить учетные данные для сетевого контроллера и нажмите клавишу ВВОД. Убедитесь, что добавляемые значения для каждого параметра, которые подходят для развертывания.

    ```
    $cred=New-Object Microsoft.Windows.Networkcontroller.credentialproperties
    $cred.type="usernamepassword"
    $cred.username="admin"
    $cred.value="abcd"

    New-NetworkControllerCredential -ConnectionUri https://networkcontroller -Properties $cred -ResourceId cred1
    ```

3. Чтобы получить учетные данные, которые вы добавили на сетевой контроллер, введите следующую команду и нажмите клавишу ВВОД. Убедитесь, что добавляемые значения для каждого параметра, которые подходят для развертывания.

    ```
    Get-NetworkControllerCredential -ConnectionUri https://networkcontroller -ResourceId cred1  
    ```

4. Просмотрите выходные данные, который должен быть аналогичен в следующем примере выходных данных команды.

    ```
    Tags                   :
    ResourceRef     : /credentials/cred1
    CreatedTime    : 1/1/0001 12:00:00 AM
    InstanceId        : e16ffe62-a701-4d31-915e-7234d4bc5a18
    Etag                  : W/"1ec59631-607f-4d3e-ac78-94b0822f3a9d"
    ResourceMetadata :
    ResourceId       : cred1
    Properties       : Microsoft.Windows.NetworkController.CredentialProperties
    ```

    > [!NOTE]
    > При запуске **Get NetworkControllerCredential** команды выходных данных команды можно назначить переменной, используя оператор "точка", чтобы перечислить свойства учетных данных. Например, $cred. Свойства.

## <a name="additional-windows-powershell-commands-for-network-controller"></a>Дополнительные команды Windows PowerShell для сетевого контроллера

После развертывания сетевого контроллера, можно использовать команды Windows PowerShell для управления и изменения развертывания. Ниже приведены некоторые изменения, внесенные в развертывание.

- Изменения параметров приложения, кластера и узла сетевого контроллера

- Удалить сетевой контроллер кластера и приложений

- Управление узлами кластера сетевым контроллером, включая добавление, удаление, включение и отключение узлов.

Следующая таблица предоставляет синтаксис для Windows PowerShell команд, можно использовать для выполнения этих задач.

|Задача|Command|Синтаксис|
|--------|-------|----------|
|Изменение параметров кластера сетевого контроллера|SET-NetworkControllerCluster|`Set-NetworkControllerCluster [-ManagementSecurityGroup <string>][-Credential <PSCredential>] [-computerName <string>][-CertificateThumbprint <String> ] [-UseSSL]`
|Изменять настройки приложения сетевого контроллера|SET-NetworkController|`Set-NetworkController [-ClientAuthentication <ClientAuthentication>] [-Credential <PSCredential>] [-ClientCertificateThumbprint <string[]>] [-ClientSecurityGroup <string>] [-ServerCertificate <X509Certificate2>] [-RestIPAddress <String>] [-ComputerName <String>][-CertificateThumbprint <String> ] [-UseSSL]`
|Изменить параметры узла сетевого контроллера|SET-NetworkControllerNode|`Set-NetworkControllerNode -Name <string> > [-RestInterface <string>] [-NodeCertificate <X509Certificate2>] [-Credential <PSCredential>] [-ComputerName <string>][-CertificateThumbprint <String> ] [-UseSSL]`
|Изменение параметров диагностики сетевого контроллера|SET-NetworkControllerDiagnostic|`Set-NetworkControllerDiagnostic [-LogScope <string>] [-DiagnosticLogLocation <string>] [-LogLocationCredential <PSCredential>] [-UseLocalLogLocation] >] [-LogLevel <loglevel>][-LogSizeLimitInMBs <uint32>] [-LogTimeLimitInDays <uint32>] [-Credential <PSCredential>] [-ComputerName <string>][-CertificateThumbprint <String> ] [-UseSSL]`
|Удалите приложение для сетевого контроллера|Удалить NetworkController|`Uninstall-NetworkController [-Credential <PSCredential>][-ComputerName <string>] [-CertificateThumbprint <String> ] [-UseSSL]`
|Удалите кластер сетевого контроллера|Удалить NetworkControllerCluster|`Uninstall-NetworkControllerCluster [-Credential <PSCredential>][-ComputerName <string>][-CertificateThumbprint <String> ] [-UseSSL]`
|Добавить узел к кластеру сетевого контроллера|Добавить NetworkControllerNode|`Add-NetworkControllerNode -FaultDomain <String> -Name <String> -RestInterface <String> -Server <String> [-CertificateThumbprint <String> ] [-ComputerName <String> ] [-Credential <PSCredential> ] [-Force] [-NodeCertificate <X509Certificate2> ] [-PassThru] [-UseSsl]`
|Отключить сетевой контроллер узел кластера|Disable-NetworkControllerNode|`Disable-NetworkControllerNode -Name <String> [-CertificateThumbprint <String> ] [-ComputerName <String> ] [-Credential <PSCredential> ] [-PassThru] [-UseSsl]`
|Включение сетевой контроллер узел кластера|Enable-NetworkControllerNode|`Enable-NetworkControllerNode -Name <String> [-CertificateThumbprint <String> ] [-ComputerName <String> ] [-Credential <PSCredential> ] [-PassThru] [-UseSsl]`
|Удалить сетевой контроллер узел из кластера|Remove-NetworkControllerNode|`Remove-NetworkControllerNode [-CertificateThumbprint <String> ] [-ComputerName <String> ] [-Credential <PSCredential> ] [-Force] [-Name <String> ] [-PassThru] [-UseSsl]`

>[!NOTE]
>Команды Windows PowerShell для сетевого контроллера, в библиотеке TechNet по адресу [командлеты сетевого контроллера](https://technet.microsoft.com/library/mt576401.aspx).

## <a name="sample-network-controller-configuration-script"></a>Пример сценария конфигурации сетевого контроллера

Приведенный ниже пример сценария конфигурации показано, как создать кластер с несколькими узлами сетевого контроллера и установить приложение сетевого контроллера. Кроме того в переменную $cert выбирает сертификат из хранилища сертификатов локального компьютера, который соответствует строке имя субъекта «networkController.contoso.com».

```
$a = New-NetworkControllerNodeObject -Name Node1 -Server NCNode1.contoso.com -FaultDomain fd:/rack1/host1 -RestInterface Internal
$b = New-NetworkControllerNodeObject -Name Node2 -Server NCNode2.contoso.com -FaultDomain fd:/rack1/host2 -RestInterface Internal
$c = New-NetworkControllerNodeObject -Name Node3 -Server NCNode3.contoso.com -FaultDomain fd:/rack1/host3 -RestInterface Internal

$cert= get-item Cert:\LocalMachine\My | get-ChildItem | where {$_.Subject -imatch "networkController.contoso.com" }

Install-NetworkControllerCluster -Node @($a,$b,$c)  -ClusterAuthentication Kerberos -DiagnosticLogLocation \\share\Diagnostics - ManagementSecurityGroup Contoso\NCManagementAdmins -CredentialEncryptionCertificate $cert  
Install-NetworkController -Node @($a,$b,$c) -ClientAuthentication Kerberos -ClientSecurityGroup Contoso\NCRESTClients -ServerCertificate $cert -RestIpAddress 10.0.0.1/24
```

## <a name="post-deployment-steps-for-non-kerberos-deployments"></a>Действия после развертывания для развертываний, отличных от Kerberos

Если вы не используете Kerberos при развертывании сетевого контроллера, необходимо развернуть сертификаты.

Дополнительные сведения см. в разделе [действия после развертывания для сетевого контроллера](../technologies/network-controller/post-deploy-steps-nc.md).


