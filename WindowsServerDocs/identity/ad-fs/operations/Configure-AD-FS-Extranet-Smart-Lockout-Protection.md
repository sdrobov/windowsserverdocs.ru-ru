---
ms.assetid: 777aab65-c9c7-4dc9-a807-9ab73fac87b8
title: Настройка защиты блокировки экстрасети AD FS
description: ''
author: billmath
ms.author: billmath
manager: mtilman
ms.date: 02/20/2019
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 904b563da2f1404d873c7352db9eadb7bfe252f2
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59869765"
---
# <a name="ad-fs-extranet-lockout-and-extranet-smart-lockout"></a>AD FS экстрасети и смарт-блокировка экстрасети

# <a name="overview"></a>Обзор

>Область применения. Windows Server 2019 г., Windows Server 2016, Windows Server 2012 R2

В AD FS на Windows Server 2012 R2, мы представили функцию безопасности, называемую [экстрасети обратимо](configure-ad-fs-extranet-soft-lockout-protection.md).  С помощью этой функции AD FS останавливает проверку подлинности пользователей за пределами корпоративной сети в течение заданного времени.  Это предотвращает возможность блокируется в Active Directory учетные записи пользователей. В дополнение к защите пользователей от блокировки учетных записей AD, блокировка экстрасети AD FS также обеспечивает защиту от атак подбора пароля.

В июня 2018 г., AD FS на Windows Server 2016 появилась **экстрасети смарт-блокировки (ESL)**.  ESL позволяет различать попытки входа в систему, которые выглядят от допустимого пользователя и попытки входа с возможно злоумышленник, что AD FS. Таким образом AD FS можно заблокировать злоумышленники при этом разрешив допустимым пользователям продолжать использовать свои учетные записи. Это позволяет отказ в обслуживании пользователем и обеспечивает защиту от целенаправленных атак, такие как атаки типа «пароль Распылитель».  
ESL доступен для AD FS в Windows Server 2016 и встроена в AD FS в Windows Server 2019.

> [!NOTE]
> Эта функция работает только для **экстрасети** в какие запросы проверки подлинности были переданы через прокси веб-приложения и применяется только к **проверки подлинности имя пользователя и пароль**.

## <a name="advantages-of-extranet-smart-lockout-in-ad-fs-2016"></a>Преимущества экстрасети смарт-блокировка в AD FS 2016
Блокировка экстрасети обратимо в AD FS 2012 R2 предоставляются следующие ключевые преимущества:
- Защита учетных записей пользователей из **атак методом подбора** в которой злоумышленник пытается угадать пароль пользователя, постоянно отправляя запросы проверки подлинности и из **атаки для взлома пароля Распылитель** где злоумышленники используют распространенных простых паролей с помощью многих различных учетных записей
- Защита учетных записей пользователей из **блокировки учетных записей Active Directory** от вредоносных проверки подлинности запросов с паролями не так. Таким образом, несмотря на то, что учетная запись пользователя будет заблокирована для доступа через экстрасеть, пользователь все равно сможете входа в AD из корпоративной сети. Этот процесс называется **обратимо блокировки**.

Смарт-блокировка экстрасети сборок воспользоваться преимуществами обратимого экстрасети, добавив следующее:
- Защищает пользователей от возникают **блокировки учетной записи экстрасети** от проверки подлинности вредоносных запросов.  Смарт-блокировка предотвратит потенциально вредоносных запросов из необычного расположения, что позволяет пользователю выполнять вход из экстрасети из знакомых (расположения, из которых пользователь успешно выполнил вход перед).
- Имеется только режим журнала, таким образом, чтобы система дополнительные signon хорошие и потенциально вредоносных действий без отключения всех учетных записей

## <a name="additional-advantages-of-extranet-smart-lockout-in-ad-fs-2019"></a>Дополнительные преимущества экстрасети смарт-блокировка в AD FS 2019 г.
Блокировка экстрасети смарт-в AD FS 2019 добавляет следующие преимущества по сравнению с AD FS 2016:
- Установите пороговые значения независимых блокировки для знакомых и незнакомого расположения, таким образом, чтобы пользователи известных оптимально могут иметь дополнительные возможности для возникновения ошибок запросов, чем подозрительных расположениях
- Включить режим аудита для смарт-блокировка, продолжая предоставлять доступ для принудительного применения прежнее поведение обратимого блокировки

## <a name="pre-requisites-for-extranet-smart-lockout-in-ad-fs-2016"></a>Предварительные требования для экстрасети смарт-блокировка в AD FS 2016
Следующие необходимые условия являются обязательными для ESL с AD FS 2019.

### <a name="install-updates-on-all-nodes-in-the-farm"></a>Установить обновления на всех узлах фермы
Во-первых убедитесь, все серверы Windows Server 2016 AD FS обновлены начиная с июня 2018 г. обновления Windows и что на ферме AD FS 2016 работает на уровне поведения фермы 2016.

### <a name="update-artifact-database-permissions"></a>Обновить разрешения артефактов базы данных
Смарт-блокировка экстрасети требует учетной записи службы AD FS имеет разрешения на таблицу в базе данных служб федерации Active Directory артефакта.  Предоставьте это разрешение, выполнив следующую команду в командной строке PowerShell:
``` powershell
PS C:\>$cred = Get-Credential
PS C:\>Update-AdfsArtifactDatabasePermission -Credential $cred
```
Где `$cred` — это учетная запись с правами администратора службы федерации Active Directory (AD FS администратора разрешениях, необходимых для доступа к базе данных изменения.)

>[!NOTE]
>В нескольких ферму серверов, используется база данных WID указанный выше командлет требует, что Windows удаленное управление включено на каждом сервере AD FS

Если у вас нет разрешений администратора AD FS, можно настроить разрешения для базы данных вручную в SQL или внутреннюю базу данных Windows, выполнив следующую команду, при подключении к базе данных AdfsArtifactStore.
```
sp_addrolemember 'db_owner', 'db_genevaservice'
```
### <a name="ensure-ad-fs-security-audit-logging-is-enabled"></a>Убедитесь, что включен журнал аудита безопасности AD FS
Эта функция использует аудита безопасности, необходимо включить журналы, так что аудита в AD FS, а также локальной политики на всех серверах AD FS.

## <a name="pre-requisites-for-extranet-smart-lockout-in-ad-fs-2019"></a>Предварительные требования для экстрасети смарт-блокировка в AD FS 2019 г.
Следующие необходимые условия являются обязательными для ESL AD FS 2016.

### <a name="ensure-ad-fs-security-audit-logging-is-enabled"></a>Убедитесь, что включен журнал аудита безопасности AD FS
Эта функция использует аудита безопасности, необходимо включить журналы, так что аудита в AD FS, а также локальной политики на всех серверах AD FS.

## <a name="lockout-settings"></a>Параметры блокировки
Смарт-блокировка экстрасети состоит из набора новых возможностей, регулируется новых и существующих свойств службы федерации Active Directory.

### <a name="extranet-lockout-enabled"></a>Включена блокировка экстрасети
Смарт-блокировка экстрасети использует то же свойство AD FS, который ранее использовался только для элемента управления «мягкий» блокировка экстрасети.  Это свойство называется ExtranetLockoutEnabled и можно просмотреть с помощью Get-AdfsProperties.

### <a name="extranet-smart-lockout-mode"></a>Режим экстрасети смарт-блокировка
Для управления поведением смарт-vs «мягкий» блокировки области добавлено новое свойство AD FS с именем ExtranetLockoutMode.  Его можно задать с помощью Set-AdfsProperties и содержит три значения:

    - **ADPasswordCounter** – это прежних версий, в режиме «блокировка экстрасети мягкие» служб федерации Active Directory, который не делает различия на основе расположения.  Это значение по умолчанию.

    - **ADFSSmartLockoutLogOnly** — это смарт-блокировка экстрасети, но вместо отклонения запросов проверки подлинности, AD FS будут только записи события admin и аудита.

    - **ADFSSmartLockoutEnforce** — это смарт-блокировка экстрасети с полной поддержкой незнакомого запросы блокируются при достижении пороговых значений.

В AD FS 2019 значения ADPasswordCounter и ADFSSmartLockoutLogOnly могут объединяться, так что обратимо блокировки продолжает действовать при подготовке для смарт-блокировка.

### <a name="lockout-threshold-and-observation-window"></a>Пороговое значение блокировки и окно наблюдения
Смарт-блокировка в AD FS 2019 использует те же два свойства AD FS как обратимо блокировки, ранее: ExtranetObservationWindow и ExtranetLockoutThreshold.

- **ExtranetLockoutThreshold &lt;целое число&gt;**  определяет максимальное количество попытки ввода неправильного пароля. При достижении порогового значения в ADFSSmartLockoutEnforce режиме AD FS отклоняет запросы из экстрасети пока не истечет окно наблюдения.  В режиме ADFSSmartLockoutLogOnly AD FS будет записывать только записи журнала.  
- **ExtranetObservationWindow &lt;TimeSpan&gt;**  определяет, сколько имя пользователя и пароль запросы из необычного расположения будет заблокирован. AD FS начнет выполнять попытку проверки подлинности имя пользователя и пароль, при передаче окна.

> [!NOTE]
> Функции блокировки экстрасети AD FS независимо от политики блокировки AD. Мы рекомендуем установить **ExtranetLockoutThreshold** значение параметра значение меньше, чем пороговое значение блокировки учетной записи AD. Невыполнение этого действия приведет к AD FS, когда не удается, для защиты учетных записей были заблокированы в Active Directory. 

В AD FS 2019 г. Мы представили новый порог блокировки определенных известных оптимально: ExtranetLockoutThresholdFamiliarLocation.
- **ExtranetLockoutThresholdFamiliarLocation &lt;целое число&gt;**  определяет максимальное количество попытки ввода неправильного пароля из знакомых расположениях. В AD FS 2019 исходный параметр ExtranetLockoutThreshold действует для неизвестных расположений (IP-адреса не работоспособной).

### <a name="primary-domain-controller-requirement"></a>Требования контроллера основного домена
AD FS 2016 предоставляет параметр, который позволяет возвращаться к другому контроллеру домена, если основной контроллер домена недоступен.

- **ExtranetLockoutRequirePDC &lt;логическое&gt;**  при включении блокировки экстрасети требует основного контроллера домена (PDC). При отключении блокировки экстрасети будут переведены на другом контроллере домена, на случай, если основной контроллер домена недоступен.

   В следующем примере показано командлет для включения блокировки с необходимостью PDC отключены:

    ```powershell
    Set-AdfsProperties -EnableExtranetLockout $true -ExtranetLockoutThreshold 15 -ExtranetObservationWindow (new-timespan -Minutes 30) -ExtranetLockoutRequirePDC $false
    ```

## <a name="configuring-ad-fs-with-smart-lockout-in-log-only-mode"></a>Настройка AD FS с помощью смарт-блокировка в режиме только для журнала

### <a name="ad-fs-2016"></a>AD FS 2016
Мы рекомендуем настроить поведение блокировки для входа только с помощью следующего командлета:

 ```powershell
PS C:\>Set-AdfsProperties -ExtranetLockoutMode AdfsSmartlockoutLogOnly
 ```

В этом режиме AD FS заполняет сведения знакомого расположения пользователей и записывает события аудита безопасности, но не блокирует все запросы.  Этот режим используется для проверки, что смарт-блокировка работает, и чтобы включить AD FS «дополнительные» знакомый расположения для пользователей перед включением «принудительно» режим.
Как AD FS узнает, он хранит входа в систему на пользователя (следует ли в режиме только для журнала или принудительное применение). 

>[!NOTE]
>Настройка `ExtranetLockoutMode` для `AdfsSmartlockoutLogOnly` приведет к поведению предыдущих версий AD FS «мягкие блокировка экстрасети» больше не действует, даже если `EnableExtranetLockout` свойство имеет значение True.  Это означает, что пользователей, которые превышают пороговые значения блокировки из знакомых или незнакомого IP-адреса не блокируются, смарт-блокировка AD FS. Тем не менее в локальном каталоге AD может блокировки пользователя, на основе конфигурации существует.   См. в разделе [политика блокировки учетной записи](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/account-lockout-policy) дополнительные как в локальной среде AD могут блокировки пользователей.»  Это должен быть временное состояние, чтобы система можно изучить поведение входа до повторное Знакомство с принудительного применения блокировки с помощью нового поведения смарт-блокировка.

Новый режим вступили в силу перезапустите службу AD FS на всех узлах фермы
  
  ``` powershell
PS C:\>Restart-service adfssrv
  ```
Настроив режим, можно включить с помощью смарт-блокировка `EnableExtranetLockout` параметр


``` powershell
PS C:\>Set-AdfsProperties -EnableExtranetLockout $true
```

Обратите внимание, что можно использовать тот же командлет для отключения блокировки

Пример. Отключение блокировки

``` powershell
PS C:\>Set-AdfsProperties -EnableExtranetLockout $false
```
### <a name="ad-fs-2019"></a>AD FS 2019 Г.
Если AD FS обратимо экстрасети в настоящее время не используется, рекомендуется выполнить то же руководство, как и для AD FS 2016 выше.
Если вы используете обратимо блокировки, но мы рекомендуем установить AD FS 2019 поведение блокировки для входа для смарт-блокировки, но сохранить применение обратимо блокировки, с помощью powershell ниже:

 ```powershell
PS C:\>Set-AdfsProperties -ExtranetLockoutMode 3
 ```

После выполнения этого командлета Get-AdfsProperties можно затем использовать для запроса значения свойства ExtranetLockoutMode AD FS.  Вы увидите, что его значение был обновлен для побитовое сочетание ADPasswordCounter и ADFSSmartLockoutLogOnly.

## <a name="observing-audit-events"></a>Наблюдение за событий аудита
AD FS будет записывать экстрасети события в журнал аудита безопасности:
-   Когда пользователь заблокировано out (достигает порогового значения блокировки для попыток неудачного входа)
-   При получении попытки входа для пользователя, который уже находится в состоянии блокировки в AD FS

В режиме журнала можно просмотреть в журнале аудита безопасности для событий блокировки.  Для любого события можно проверить состояние пользователя, с помощью командлета Get-ADFSAccountActivity, чтобы определить, если произошла блокировка из знакомых или незнакомого IP-адресов, а также тщательно проверить список знакомы IP-адреса для этого пользователя.

Пример события:
```
Log Name:      Security
Source:        AD FS Auditing
Date:          5/21/2018 12:55:59 AM
Event ID:      1210
Task Category: (3)
Level:         Information
Keywords:      Classic,Audit Failure
User:          CONTOSO\adfssvc
Computer:      ADFS2016FS1.corp.contoso.com
Description:
An extranet lockout event has occurred. See XML for failure details. 

Activity ID: fa7a8052-0694-48f0-84e2-b51cde40ac3d 

Additional Data 
XML: <?xml version="1.0" encoding="utf-16"?>
<AuditBase xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="ExtranetLockoutAudit">
  <AuditType>ExtranetLockout</AuditType>
  <AuditResult>Failure</AuditResult>
  <FailureType>ExtranetLockoutError</FailureType>
  <ErrorCode>AccountRestrictedAudit</ErrorCode>
  <ContextComponents>
    <Component xsi:type="ResourceAuditComponent">
      <RelyingParty>http://fs.contoso.com/adfs/services/trust</RelyingParty>
      <ClaimsProvider>N/A</ClaimsProvider>
      <UserId>CONTOSO\user</UserId>
    </Component>
    <Component xsi:type="RequestAuditComponent">
      <Server>N/A</Server>
      <AuthProtocol>WSFederation</AuthProtocol>
      <NetworkLocation>Extranet</NetworkLocation>
      <IpAddress>64.187.173.10</IpAddress>
      <ForwardedIpAddress>64.187.173.10</ForwardedIpAddress>
      <ProxyIpAddress>N/A</ProxyIpAddress>
      <NetworkIpAddress>N/A</NetworkIpAddress>
      <ProxyServer>ADFS2016PROXY2</ProxyServer>
      <UserAgentString>Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/66.0.3359.181 Safari/537.36</UserAgentString>
      <Endpoint>/adfs/ls/</Endpoint>
    </Component>
    <Component xsi:type="LockoutConfigAuditComponent">
      <CurrentBadPasswordCount>5</CurrentBadPasswordCount>
      <ConfigBadPasswordCount>5</ConfigBadPasswordCount>
      <LastBadAttempt>05/21/2018 00:55:05</LastBadAttempt>
      <LockoutWindowConfig>00:30:00</LockoutWindowConfig>
    </Component>
  </ContextComponents>
</AuditBase>
Event Xml:
<Event xmlns="http://schemas.microsoft.com/win/2004/08/events/event">
  <System>
    <Provider Name="AD FS Auditing" />
    <EventID Qualifiers="0">1210</EventID>
    <Level>0</Level>
    <Task>3</Task>
    <Keywords>0x8090000000000000</Keywords>
    <TimeCreated SystemTime="2018-05-21T00:55:59.921880300Z" />
    <EventRecordID>35521235</EventRecordID>
    <Channel>Security</Channel>
    <Computer>ADFS2016FS1.contoso.com</Computer>
    <Security UserID="S-1-5-21-1156273042-1594504307-2076964089-1104" />
  </System>
  <EventData>
    <Data>fa7a8052-0694-48f0-84e2-b51cde40ac3d</Data>
    <Data><?xml version="1.0" encoding="utf-16"?>
<AuditBase xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="ExtranetLockoutAudit">
  <AuditType>ExtranetLockout</AuditType>
  <AuditResult>Failure</AuditResult>
  <FailureType>ExtranetLockoutError</FailureType>
  <ErrorCode>AccountRestrictedAudit</ErrorCode>
  <ContextComponents>
    <Component xsi:type="ResourceAuditComponent">
      <RelyingParty>http://fs.contoso.com/adfs/services/trust</RelyingParty>
      <ClaimsProvider>N/A</ClaimsProvider>
      <UserId>CONTOSO\user</UserId>
    </Component>
    <Component xsi:type="RequestAuditComponent">
      <Server>N/A</Server>
      <AuthProtocol>WSFederation</AuthProtocol>
      <NetworkLocation>Extranet</NetworkLocation>
      <IpAddress>64.187.173.10</IpAddress>
      <ForwardedIpAddress>64.187.173.10</ForwardedIpAddress>
      <ProxyIpAddress>N/A</ProxyIpAddress>
      <NetworkIpAddress>N/A</NetworkIpAddress>
      <ProxyServer>ADFS2016PROXY2</ProxyServer>
      <UserAgentString>Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/66.0.3359.181 Safari/537.36</UserAgentString>
      <Endpoint>/adfs/ls/</Endpoint>
    </Component>
    <Component xsi:type="LockoutConfigAuditComponent">
      <CurrentBadPasswordCount>5</CurrentBadPasswordCount>
      <ConfigBadPasswordCount>5</ConfigBadPasswordCount>
      <LastBadAttempt>05/21/2018 00:55:05</LastBadAttempt>
      <LockoutWindowConfig>00:30:00</LockoutWindowConfig>
    </Component>
  </ContextComponents>
</AuditBase></Data>
  </EventData>
</Event>
```

## <a name="observing-user-activity"></a>Наблюдение за действиями пользователя
AD FS предоставляет командлеты powershell для просмотра и управления данных учетной записи о действиях пользователей.  Для чтения текущей учетной записи действия для учетной записи пользователя.  Используйте следующий командлет:

``` powershell
PS C:\>Get-ADFSAccountActivity user@contoso.com
```

Пример выходных данных
```
Identifier             : CONTOSO\user
BadPwdCountFamiliar    : 0
BadPwdCountUnknown     : 0
LastFailedAuthFamiliar : 1/1/0001 12:00:00 AM
LastFailedAuthUnknown  : 1/1/0001 12:00:00 AM
FamiliarLockout        : False
UnknownLockout         : False
FamiliarIps            : {}
```

Текущие выходные данные действия содержит следующие данные:

**Идентификатор**: это имя пользователя

**BadPwdCountFamiliar**: это текущее количество попыток неверного пароля входа с IP-адресов, которые были в списке «FamiliarIps» во время попытки

**BadPwdCountUnknown**: это текущее количество попыток неверного пароля входа с IP-адресов, которые не были в списке «FamiliarIps» во время попытки

**LastFailedAuthFamiliar**: это время последней попытки ввода неверного пароля имени входа с IP-адреса, который был включен в список «FamiliarIps» во время попытки

**LastFailedAuthUnknown**: это время последней попытки ввода неверного пароля имени входа с IP-адреса, который не был включен в список «FamiliarIps» во время попытки

**FamiliarLockout**: это означает, что если пользователь находится в состоянии блокировки для попытки правильный пароль из IP-адресов в список «FamiliarIps» 

**UnknownLockout**: это означает, что если пользователь находится в состоянии блокировки для попытки правильный пароль из IP-адреса не включен в список «FamiliarIps» FamiliarIps: это текущий список знакомы IP-адреса для пользователя

## <a name="adjust-threshold-and-window"></a>Настроить пороговое значение и окна
Как только вы работали в режиме только для журнала достаточное время для AD FS для получения расположения входа, вы можете настроить окно наблюдения или пороговое значение от значений по умолчанию.  Это делается с помощью `Set-AdfsProperties` как в приведенных ниже примерах:

Окно наблюдения задается с помощью `ExtranetObservationWindow`:

Пример. 

``` powershell
PS C:\>Set-AdfsProperties -ExtranetObservationWindow ( new-timespan -minutes 30 )
```

Где значение TimeSpan.

### <a name="setting-threshold-value-in-ad-fs-2016"></a>Параметр порогового значения в AD FS 2016
В AD FS 2016 пороговое значение задается с помощью ExtranetLockoutThreshold:

Пример.

``` powershell
PS C:\>Set-AdfsProperties -ExtranetLockoutThreshold 5
```

### <a name="setting-threshold-values-in-ad-fs-2019"></a>Установка пороговых значений в AD FS 2019 г.
В AD FS 2019 существуют различные пороговые значения для известных хороший и незнакомых расположений

Чтобы задать пороговое значение для неизвестных расположений, используйте то же свойство, для AD FS 2016 выше:

Пример.

``` powershell
PS C:\>Set-AdfsProperties -ExtranetLockoutThreshold 5
```

Чтобы задать пороговое значение для известных оптимально, используйте свойство ExtranetLockoutThresholdFamiliarLocation, как показано в следующем примере:

Пример.

``` powershell
PS C:\>Set-AdfsProperties -ExtranetLockoutThresholdFamiliarLocation 10
```


## <a name="enable-enforce-mode"></a>Включение Принудительный режим
После того как выполнялась в режиме только для журнала достаточно времени для AD FS для получения расположения входа и для наблюдения за любое действие блокировки, и когда вы будете готовы с окном блокировки пороговое значение и наблюдения, смарт-блокировка можно переместить в «применить», с помощью режима Следующий командлет PSH:

``` powershell
PS C:\>Set-AdfsProperties -ExtranetLockoutMode AdfsSmartLockoutEnforce
```

Новый режим вступили в силу перезапустите службу AD FS на всех узлах фермы

``` powershell
PS C:\>Restart-service adfssrv
```


## <a name="manage-user-account-activity"></a>Управление действиям в учетной записи пользователя
AD FS предоставляет 3 командлеты для управления данными действия учетной записи пользователя.  Эти командлеты автоматически подключаться к узлу в ферме, которая удерживает главную роль (хотя это поведение можно переопределить, передав параметр - Server).

> [!NOTE] 
> Дополнительные сведения о делегировании разрешениями на использование этих командлетов см. в разделе [делегат AD FS Powershell командлет доступ пользователям без прав администратора](delegate-ad-fs-pshell-access.md)

Эти командлеты находятся:

`Get-ADFSAccountActivity`

Чтение текущей учетной записи действия для учетной записи пользователя.  Командлет всегда автоматически подключается к хозяину фермы с помощью конечной точки REST учетной записи действия, чтобы все данные всегда должно быть согласовано

``` powershell
Get-ADFSAccountActivity user@contoso.com
```
`
Set-ADFSAccountActivity
`

Обновите учетную запись действия для учетной записи пользователя.  Это может использоваться для добавления новых адресов знакомы или очистить состояние для любой учетной записи

``` powershell
Set-ADFSAccountActivity user@upnsuffix.com -FamiliarLocation “1.2.3.4”
```
`Reset-ADFSAccountLockout`

Сбрасывает счетчик блокировки учетной записи пользователя

``` powershell
Reset-ADFSAccountLockout user@upnsuffix.com -Familiar
```

## <a name="troubleshooting-esl"></a>Устранение неполадок ESL
Ниже могут помочь вам в устранении неполадок функции смарт-блокировка экстрасети.

### <a name="updating-database-permissions-for-esl"></a>Обновление разрешений базы данных для ESL
Если все ошибки возвращаются из `Update-AdfsArtifactDatabasePermission` командлета, проверьте следующее

1.  Список узлов фермы является правильным.  Если узел находится в списке фермы AD FS, но больше не active patch проверка завершится ошибкой.  Это можно исправить, запустив `remove-adfsnode <node name >`
2.  Убедитесь, что пакет развертывается на всех узлах фермы
3.  Проверьте учетные данные, переданные в командлет имеет разрешения на изменение владельца схемы базы данных ad fs артефакта.  

### <a name="logging--auditing"></a>Ведение журнала / аудит
Если запрос на проверку подлинности отклоняется, так как объем данных превысит пороговое значение блокировки, AD FS будет записывать `ExtranetLockoutEvent` поток аудита безопасности.  

Пример события:

Произошло событие экстрасети. Дополнительные сведения об ошибке см. XML. 

**Идентификатор действия: 172332e1-1301-4e56-0e00-0080000000db**

```
Additional Data 
XML: <?xml version="1.0" encoding="utf-16"?>
<AuditBase xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="ExtranetLockoutAudit">
  <AuditType>ExtranetLockout</AuditType>
  <AuditResult>Failure</AuditResult>
  <FailureType>ExtranetLockoutError</FailureType>
  <ErrorCode>AccountRestrictedAudit</ErrorCode>
  <ContextComponents>
    <Component xsi:type="ResourceAuditComponent">
      <RelyingParty>http://contoso.com/adfs/services/trust</RelyingParty>
      <ClaimsProvider>N/A</ClaimsProvider>
      <UserId>TQDFTD\Administrator</UserId>
    </Component>
    <Component xsi:type="RequestAuditComponent">
      <Server>N/A</Server>
      <AuthProtocol>WSFederation</AuthProtocol>
      <NetworkLocation>Intranet</NetworkLocation>
      <IpAddress>4.4.4.4</IpAddress>
      <ForwardedIpAddress />
      <ProxyIpAddress>1.2.3.4</ProxyIpAddress>
      <NetworkIpAddress>1.2.3.4</NetworkIpAddress>
      <ProxyServer>N/A</ProxyServer>
      <UserAgentString>Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/63.0.3239.132 Safari/537.36</UserAgentString>
      <Endpoint>/adfs/ls</Endpoint>
    </Component>
    <Component xsi:type="LockoutConfigAuditComponent">
      <CurrentBadPasswordCount>5</CurrentBadPasswordCount>
      <ConfigBadPasswordCount>5</ConfigBadPasswordCount>
      <LastBadAttempt>02/07/2018 21:47:44</LastBadAttempt>
      <LockoutWindowConfig>00:30:00</LockoutWindowConfig>
    </Component>
  </ContextComponents>
</AuditBase>

```

## <a name="banned-ip-addresses"></a>Запрещенное IP-адресов
Помимо возможностей смарт-блокировка экстрасети, июня 2018 г. обновление AD FS можно настроить набор IP-адресов глобально в AD FS, чтобы запросы, поступающие из этих IP-адресов, или у этих IP-адресов **x-forwarded-for**  или **x-ms-forwarded--IP-адрес клиента** заголовки, будут блокироваться AD FS.

##### <a name="adding-banned-ips"></a>Добавление заблокированных IP-адресов
Чтобы добавить глобальный список заблокированных IP-адресов, используйте ниже командлет Powershell:

``` powershell
PS C:\ >Set-AdfsProperties -AddBannedIps "1.2.3.4", "::3", "1.2.3.4/16"
```

Допустимые форматы

1.  IPv4
2.  IPv6
3.  Формат CIDR с IPv4- или версии 6
4.  Диапазон IP-адресов с IPv4- или версии 6 (т. е. 1.2.3.4-1.2.3.6)

#### <a name="removing-banned-ips"></a>Удаление заблокированных IP-адресов
Чтобы удалить запрещенных IP-адресов из глобального списка, используйте ниже командлет Powershell:

``` powershell
PS C:\ >Set-AdfsProperties -RemoveBannedIps "1.2.3.4"
```

#### <a name="read-banned-ips"></a>Чтение заблокированных IP-адресов
Чтобы считать текущий набор запрещенных IP-адресов, используйте ниже командлет Powershell:

``` powershell
PS C:\ >Get-AdfsProperties 
```

Пример вывода команды:

```
BannedIpList                   : {1.2.3.4, ::3,1.2.3.4/16}
```



## <a name="additional-references"></a>Дополнительная справка  
[Рекомендации по обеспечению безопасности служб федерации Active Directory](../../ad-fs/deployment/best-practices-securing-ad-fs.md)

[Set-AdfsProperties](https://technet.microsoft.com/itpro/powershell/windows/adfs/set-adfsproperties)

[Операции AD FS](../../ad-fs/AD-FS-2016-Operations.md)

    
