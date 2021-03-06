---
ms.assetid: 777aab65-c9c7-4dc9-a807-9ab73fac87b8
title: Настройка защиты блокировки экстрасети AD FS
author: billmath
ms.author: billmath
manager: femila
ms.date: 02/01/2019
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: f49e4a7e27d5b224a86655e48f07df741f03e7b0
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86962646"
---
# <a name="configure-ad-fs-extranet-lockout-protection"></a>Настройка защиты блокировки экстрасети AD FS

В AD FS в Windows Server 2012 R2 мы предоставили функцию безопасности, называемую блокировкой экстрасети.  С помощью этой функции AD FS будет "прекращать" проверку подлинности "вредоносной" учетной записи пользователя извне в течение определенного периода времени.  Это предотвращает блокировку учетных записей пользователей в Active Directory.  Помимо защиты пользователей от блокировки учетной записи AD, AD FS блокировка экстрасети также обеспечивает защиту от атак методом подбора пароля.

> [!NOTE]
> Эта функция работает только в **экстрасети** , где запросы проверки подлинности поступают через прокси-приложение и применяются только к **проверке подлинности имени пользователя и пароля**.

## <a name="advantages-of-extranet-lockout"></a>Преимущества блокировки экстрасети
Блокировка экстрасети обеспечивает следующие основные преимущества.
- Он защищает учетные записи пользователей от **атак методом подбора** , когда злоумышленник пытается угадать пароль пользователя, постоянно отправляя запросы на проверку подлинности. В этом случае AD FS будет блокировать доступ к учетной записи злонамеренного пользователя для доступа к экстрасети.
- Он защищает учетные записи пользователей от **злонамеренной блокировки учетных записей** , когда злоумышленнику нужно заблокировать учетную запись пользователя, отправив запросы проверки подлинности с неверными паролями. В этом случае, несмотря на то, что учетная запись пользователя будет заблокирована AD FS для доступа к экстрасети, фактическая учетная запись пользователя в AD не будет заблокирована, и пользователь по-прежнему сможет получить доступ к корпоративным ресурсам в Организации. Это называется **мягкой блокировкой**.

## <a name="how-it-works"></a>Принцип работы
В AD FS необходимо настроить три параметра, чтобы включить эту функцию: 
- **Енабликстранетлоккаут &lt; Логическое &gt; ** значение true, если требуется включить блокировку экстрасети.
- **ExtranetLockoutThreshold &lt; Целое число &gt; ** , определяющее максимальное число неудачных попыток ввода пароля. После достижения порогового значения AD FS будет немедленно отклонять запросы из экстрасети без попытки обращения к контроллеру домена для проверки подлинности, независимо от того, является ли пароль хорошим или плохим, пока не будет передано окно наблюдения за экстрасетью. Это означает, что значение атрибута **badPwdCount** учетной записи AD не увеличится, пока учетная запись не будет обратимо заблокирована.
- **Екстранетобсерватионвиндов &lt; TimeSpan &gt; ** определяет, как долго учетная запись пользователя будет обратимо заблокирована. AD FS начнет повторно выполнять проверку подлинности имени пользователя и пароля при передаче окна. AD FS использует атрибут AD аргументы badPasswordTime в качестве ссылки для определения того, прошло ли окно наблюдения за экстрасетью. Окно было передано, если текущее время > аргументы badPasswordTime + Екстранетобсерватионвиндов. 

> [!NOTE]
> AD FS функции блокировки экстрасети независимо от политик блокировки AD. Однако настоятельно рекомендуется присвоить параметру **ExtranetLockoutThreshold** значение меньше порогового значения блокировки учетной записи Active Directory. Если этого не сделать, AD FS не сможет защитить учетные записи от блокировки в Active Directory. 

Пример включения функции блокировки экстрасети с максимальным числом неудачных попыток ввода пароля и 30-минутной длительностью с мягким блокировкой выглядит следующим образом:

```powershell
Set-AdfsProperties -EnableExtranetLockout $true -ExtranetLockoutThreshold 15 -ExtranetObservationWindow (new-timespan -Minutes 30)
```

Эти параметры будут применяться ко всем доменам, которые служба AD FS может проходить проверку подлинности. Таким образом, когда AD FS получает запрос на проверку подлинности, он будет получать доступ к основному контроллеру домена (PDC) через вызов LDAP и выполнять поиск атрибута **badPwdCount** для пользователя на основном контроллере домена. Если AD FS обнаружит значение параметра **badPwdCount** >= ExtranetLockoutThreshold и время, определенное в окне наблюдения экстрасети, еще не прошло, AD FS отклонит запрос немедленно, что не имеет значения, когда пользователь введет хороший или плохой пароль из экстрасети, произойдет сбой входа в систему, так как AD FS не отправляет учетные данные в AD. AD FS не поддерживает никаких состояний в отношении **badPwdCount** или заблокированных учетных записей пользователей. AD FS использует AD для отслеживания состояния. 

> [!warning]
> Если AD FS блокировка экстрасети на сервере 2012 R2 включена, все запросы проверки подлинности через WAP проверяются AD FS на основном контроллере домена. Если основной контроллер домена недоступен, пользователи не смогут пройти проверку подлинности из экстрасети.

Сервер 2016 предлагает дополнительный параметр, который позволяет AD FS переходить на другой контроллер домена, если он недоступен.

- **Екстранетлоккаутрекуирепдк &lt; Логическое &gt; значение** . при включении для блокировки экстрасети требуется основной контроллер домена (PDC). Если этот параметр отключен, блокировка экстрасети будет переключаться на другой контроллер домена в случае недоступности PDC.

Для настройки блокировки AD FS экстрасети на сервере 2016 можно использовать следующую команду Windows PowerShell:

```powershell
Set-AdfsProperties -EnableExtranetLockout $true -ExtranetLockoutThreshold 15 -ExtranetObservationWindow (new-timespan -Minutes 30) -ExtranetLockoutRequirePDC $false
```

## <a name="working-with-the-active-directory-lockout-policy"></a>Работа с политикой блокировки Active Directory
Функция блокировки экстрасети в AD FS работает независимо от политики блокировки AD. Однако необходимо убедиться, что параметры блокировки экстрасети настроены правильно, чтобы она могла использовать ее цель безопасности с политикой блокировки AD.
Сначала рассмотрим политику блокировки AD. Существует три параметра, касающихся политики блокировки в Active Directory.
- **Пороговое значение блокировки учетной записи**. Этот параметр аналогичен параметру ExtranetLockoutThreshold в AD FS. Он определяет число неудачных попыток входа в систему, которые приведут к блокировке учетной записи пользователя. Чтобы защитить учетные записи пользователей от атак с блокировкой вредоносных учетных записей, необходимо задать значение ExtranetLockoutThreshold в AD FS &lt; пороговое значение блокировки учетной записи в AD.
- **Длительность блокировки учетной записи**. Этот параметр определяет продолжительность блокировки учетной записи пользователя. Этот параметр не имеет большого значения в этом диалоге, так как блокировка экстрасети должна всегда происходить до того, как блокировка AD будет выполнена правильно.
- **Сбросить счетчик блокировки учетной записи после**: этот параметр определяет, сколько времени должно пройти при последнем сбое входа пользователя, прежде чем **badPwdCount** сбрасывается в 0. Чтобы функция блокировки экстрасети в AD FS хорошо работала с политикой блокировки AD, необходимо убедиться в том, что значение параметра Екстранетобсерватионвиндов в AD FS &gt; сбрасывает счетчик блокировки учетной записи после значения в AD. В примерах ниже объясняется, почему.  

Давайте рассмотрим два примера и посмотрим, как **badPwdCount** изменяется с течением времени на основе различных параметров и состояний. Предположим, что в обоих примерах **порог блокировки учетной записи** = 4 и **ExtranetLockoutThreshold** = 2. **Красная** стрелка представляет неудачную попытки ввода пароля, **Зеленая** стрелка — удачная попыток ввода пароля. В примере #1 **екстранетобсерватионвиндов** &gt; **сбрасывает счетчик блокировки учетной записи после**. В примере #2 **екстранетобсерватионвиндов** &lt; **сбрасывает счетчик блокировки учетной записи после**. 

### <a name="example-1"></a>Пример 1
![Example1](media/Configure-AD-FS-Extranet-Lockout-Protection/one.png)

### <a name="example-2"></a>Пример 2
![Example1](media/Configure-AD-FS-Extranet-Lockout-Protection/two.png)

Как видно из приведенного выше, существует два условия, когда **badPwdCount** будет сброшено до 0. Одна из них — при успешном входе в систему. Второй — когда время сброса этого счетчика задается в параметре **сбросить счетчик блокировки учетной записи** . При **сбросе счетчика блокировки учетной записи после** &lt; **екстранетобсерватионвиндов**у учетной записи отсутствует риск блокировки AD. Однако при **сбросе счетчика блокировки учетной записи после** &gt; **екстранетобсерватионвиндов**существует вероятность того, что учетная запись может блокироваться AD, но в случае задержки. Получение учетной записи, заблокированной AD, может занять некоторое время в зависимости от конфигурации. AD FS будет разрешать одну неудачную попытку ввода пароля в течение периода, пока **badPwdCount** не достигнет **порогового значения блокировки учетной записи**.

Дополнительные сведения см. в разделе [Настройка блокировки учетной записи](/archive/blogs/secguide/configuring-account-lockout). 

## <a name="known-issues"></a>Известные проблемы
Существует известная ошибка, из-за которой учетная запись пользователя AD не может пройти проверку подлинности с помощью AD FS, так как атрибут **badPwdCount** не реплицируется на контроллер домена, на котором выполняется запрос ADFS. Дополнительные сведения см. в [2971171](https://support.microsoft.com/help/2971171/adfs-authentication-issue-for-active-directory-users-when-extranet-loc) . [Здесь](../deployment/updates-for-active-directory-federation-services-ad-fs.md)можно найти все AD FS QFE, выпущенные на данный момент.

## <a name="key-points-to-remember"></a>Ключевые моменты, которые следует запомнить
- Функция блокировки экстрасети работает только для **сценария экстрасети** , где запросы проверки подлинности проходят через прокси-приложение
- Функция блокировки экстрасети применима только к **имени пользователя & пароль проверка подлинности**
- AD FS не отслеживает **badPwdCount** или пользователей с мягкой блокировкой. AD FS использует AD для отслеживания состояния
- AD FS выполняет поиск атрибута **badPwdCount** по вызову LDAP для пользователя на основном контроллере домена для каждой попытки проверки подлинности.  
- AD FS более поздней версии, чем 2016, завершится ошибкой, если не сможет получить доступ к PDC. В AD FS 2016 появились улучшения, позволяющие AD FS возвращаться к другим контроллерам домена в случае, если он недоступен. 
- AD FS будет разрешать запросы проверки подлинности из экстрасети, если badPwdCount < ExtranetLockoutThreshold 
- Если **badPwdCount**  >=  **ExtranetLockoutThreshold** и **аргументы badPasswordTime**  +  **екстранетобсерватионвиндов** < текущее время, AD FS отклонит запросы проверки подлинности из экстрасети.
- Чтобы избежать блокировки вредоносных учетных записей, необходимо **ExtranetLockoutThreshold**убедиться в том, что  <  **порог блокировки учетной записи** ExtranetLockoutThreshold и **ExtranetObservationWindow**  >  **Счетчик блокировки сброса** екстранетобсерватионвиндов.


## <a name="additional-references"></a>Дополнительные ссылки  
- [Рекомендации по обеспечению безопасности службы федерации Active Directory (AD FS)](../../ad-fs/deployment/best-practices-securing-ad-fs.md)
- [Делегирование доступа к командлету Powershell AD FS пользователям без прав администратора](delegate-ad-fs-pshell-access.md)
- [Set-AdfsProperties](/powershell/module/adfs/set-adfsproperties?view=win10-ps)

[Операции AD FS](../ad-fs-operations.md)

    
