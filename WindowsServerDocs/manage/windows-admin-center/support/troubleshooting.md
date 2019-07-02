---
title: 'Windows Admin Center: общие действия по устранению неполадок'
description: 'Windows Admin Center: общие действия по устранению неполадок (проект Honolulu)'
ms.technology: manage
ms.topic: article
author: jwwool
ms.author: jeffrew
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.date: 06/07/2019
ms.openlocfilehash: 4d108161dd4f6b57d4a86cbcaa5852aff53f0ac3
ms.sourcegitcommit: 63926404009f9e1330a4a0aa8cb9821a2dd7187e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/29/2019
ms.locfileid: "67469515"
---
# <a name="troubleshooting-windows-admin-center"></a>Устранение неполадок в Windows Admin Center

> Относится к: Windows Admin Center, предварительная версия Windows Admin Center

> [!Important]
> Это руководство поможет вам в диагностике и разрешении проблем, которые не позволяют использовать Windows Admin Center. Если у вас возникает проблема с определенным средством, проверьте, возможно, эта проблема [уже известна.](http://aka.ms/wacknownissues)

## <a name="installer-fails-with-message-the-module-microsoftpowershelllocalaccounts-could-not-be-loaded"></a>Установщика завершается сбоем с сообщением: **_Не удалось загрузить модуль «Microsoft.PowerShell.LocalAccounts»._ **

Это может произойти, если ваш путь к модулю PowerShell по умолчанию были изменены или удалены. Чтобы устранить проблему, убедитесь, что ```%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules``` — **первый** элемента в переменной среды PSModulePath. Это можно сделать с помощью следующей строки PowerShell:

```powershell
[Environment]::SetEnvironmentVariable("PSModulePath","%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules;" + ([Environment]::GetEnvironmentVariable("PSModulePath","User")),"User")
```

## <a name="i-get-a-this-sitepage-cant-be-reached-error-in-my-web-browser"></a>В браузере появляется сообщение об ошибке **Не удается подключиться к этому сайту/странице**

### <a name="if-youve-installed-windows-admin-center-as-an-app-on-windows-10"></a>Если вы установили Windows Admin Center в качестве **приложения в Windows 10**

* Убедитесь, что Windows Admin Center запущен. Найдите значок Windows Admin Center ![](../media/trayIcon.PNG) на панели задач или **рабочий стол Windows Admin Center / SmeDesktop.exe** в диспетчере задач. Если ни того, ни другого нет, запустите **Windows Admin Center** из меню "Пуск".

> [!NOTE] 
> После перезагрузки необходимо запустить Windows Admin Center из меню "Пуск".  

* [Проверка версии Windows](#check-the-windows-version)

* Убедитесь, что вы используете браузер Microsoft Edge или Google Chrome.

* Вы выбрали правильный сертификат при [первом запуске?](../use/get-started.md#selecting-a-client-certificate)

  * Попробуйте открыть браузер в приватном режиме, и если это сработает, вам потребуется очистить кэш.

* Недавно обновления Windows 10 до новой сборки или версии?

  * Это возможно, был удален настройки доверенных узлов. [Следуйте этим инструкциям, чтобы обновить параметры доверенных узлов.](#configure-trustedhosts)

### <a name="if-youve-installed-windows-admin-center-as-a-gateway-on-windows-server"></a>Если вы установили Windows Admin Center в качестве **шлюза в Windows Server**

* Обновлении с предыдущей версии Windows Admin Center? Убедитесь, что правила брандмауэра не был удален из-за [Это известная проблема](known-issues.md#upgrade). Используйте следующую команду PowerShell, чтобы определить, существует ли правило. Если это не так, следуйте [эти инструкции](known-issues.md#upgrade) для ее восстановления.
    
    ```powershell
    Get-NetFirewallRule -DisplayName "SmeInboundOpenException"
    ```

* [Проверьте версию Windows](#check-the-windows-version) на клиенте и сервере.

* Убедитесь, что вы используете браузер Microsoft Edge или Google Chrome.

* На сервере, откройте диспетчер задач > службы и убедитесь, что **ServerManagementGateway / Windows Admin Center** запущена.
![](../media/Service-TaskMan.PNG)

* Проверьте сетевое подключение к шлюзу (Замените \<значения > сведениями из развертывания)

    ```powershell
    Test-NetConnection -Port <port> -ComputerName <gateway> -InformationLevel Detailed
    ```

### <a name="if-you-have-installed-windows-admin-center-in-an-azure-windows-server-vm"></a>Если вы установили Windows Admin Center на Машине Azure под управлением Windows Server

* [Проверка версии Windows](#check-the-windows-version)
* Добавили ли вы правило для портов входящего трафика HTTPS? 
* [Дополнительные сведения об установке Windows Admin Center на виртуальной Машине Azure](https://docs.microsoft.com/windows-server/manage/windows-admin-center/configure/azure-integration#use-a-windows-admin-center-gateway-deployed-in-azure)

### <a name="check-the-windows-version"></a>Проверьте версию Windows

* Откройте диалоговое окно "Выполнить" (клавиши Windows + R) и запустите ```winver```.

* Если вы используете Windows 10 версии 1703 или ниже, Windows Admin Center не поддерживается в вашей версии Microsoft Edge. Выполните обновление до более новой версии Windows 10, либо используйте Google Chrome.

* Если вы используете более insider preview версии Windows 10 или Server с версией сборки между 17134 и 17637, Windows возникала ошибка, вызвавшая Windows Admin Center переход на другой. Используйте текущий поддерживаемой версии Windows.

### <a name="make-sure-the-windows-remote-management-winrm-service-is-running-on-both-the-gateway-machine-and-managed-node"></a>Убедитесь, что служба удаленного управления Windows (WinRM) запущена на компьютере шлюза и на управляемом узле

* Откройте диалоговое окно запуска с клавиша с эмблемой Windows + R
* Тип ```services.msc``` и нажмите клавишу ВВОД
* В открывшемся окне, внешний вид для удаленного управления Windows (WinRM) и убедитесь, что она запущена и настроена для автоматического запуска

### <a name="did-you-upgrade-your-server-from-2016-to-2019"></a>Обновления сервера 2016 до 2019 г.?

* Это возможно, был удален настройки доверенных узлов. [Следуйте этим инструкциям, чтобы обновить параметры доверенных узлов.](#configure-trustedhosts) 

## <a name="i-get-the-message-cant-connect-securely-to-this-page-this-might-be-because-the-site-uses-outdated-or-unsafe-tls-security-settings"></a>Я получаю сообщение: «Не удается безопасно подключаться к этой странице. Возможно, сайт использует устаревшие или небезопасные параметры безопасности TLS.

Компьютер будет ограничен подключений HTTP/2. Windows Admin Center использует встроенную проверку подлинности Windows, который не поддерживается в HTTP/2. Добавьте следующие два значения в разделе ```HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Http\Parameters``` на **компьютер под управлением обозревателя** на снятие ограничения HTTP/2:

```
EnableHttp2Cleartext=dword:00000000
EnableHttp2Tls=dword:00000000
```

## <a name="im-having-trouble-with-the-remote-desktop-events-and-powershell-tools"></a>У меня возникли проблемы со средствами удаленного рабочего стола, события и PowerShell.

Эти три средства требуется протокол websocket, который обычно блокируется прокси-серверы и брандмауэры. Если вы используете Google Chrome, [известная проблема](known-issues.md#google-chrome) websockets и проверка подлинности NTLM.

## <a name="i-can-connect-to-some-servers-but-not-others"></a>Удается подключиться к некоторым серверам, но к другим нет

* Войдите на локально компьютере шлюза и попытаться ```Enter-PSSession <machine name>``` в PowerShell, заменив \<имя компьютера > с именем компьютера, который вы пытаетесь управлять в Windows Admin Center. 

* Если в вашей среде вместо домена используется рабочая группа, см. [использование Windows Admin Center в рабочей группе](#using-windows-admin-center-in-a-workgroup).

* **С помощью учетных записей локального администратора:** Если вы используете учетную запись локального пользователя, который не является встроенной учетной записи администратора, необходимо включить политику на конечном компьютере, выполнив следующую команду в PowerShell или командной строки от имени администратора на целевом компьютере:

    ```
    REG ADD HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System /v LocalAccountTokenFilterPolicy /t REG_DWORD /d 1
    ```

## <a name="using-windows-admin-center-in-a-workgroup"></a>Использование Windows Admin Center в рабочей группе

### <a name="what-account-are-you-using"></a>Какая учетная запись используется?
Убедитесь, что учетная запись, которую вы используете, входит в группу локальных администраторов на целевом сервере. В некоторых случаях WinRM также требует членство в группе "Пользователи удаленного управления". При использовании учетной записи локального пользователя, которая не является **встроенной учетной записью администратора**, необходимо включить политику на целевом компьютере, выполнив следующую команду в PowerShell или в командной строке от имени администратора на целевом компьютере:

```cmd
REG ADD HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System /v LocalAccountTokenFilterPolicy /t REG_DWORD /d 1
```
### <a name="are-you-connecting-to-a-workgroup-machine-on-a-different-subnet"></a>Подключение производится к компьютеру рабочей группы в другой подсети?

Для подключения к компьютеру рабочей группы, который находится не в одной подсети с шлюзом, убедитесь, что порт брандмауэра для WinRM (TCP 5985) пропускает входящий трафик на целевой компьютер. Вы можете выполнить следующую команду в PowerShell или в командной строке от имени администратора на целевом компьютере для создания этого правила брандмауэра:

- **Windows Server**

    ```powershell
    Set-NetFirewallRule -Name WINRM-HTTP-In-TCP-PUBLIC -RemoteAddress Any
    ```

- **Windows 10**

    ```powershell
    Set-NetFirewallRule -Name WINRM-HTTP-In-TCP -RemoteAddress Any
    ```

### <a name="configure-trustedhosts"></a>Настройка TrustedHosts

При установке Windows Admin Center пользователю предоставляется возможность задать параметр TrustedHosts шлюза через Windows Admin Center. Это обязательно в среде рабочей группы и при использовании учетных данных локального администратора в домене. Если вы решили пропустить настройку этого параметра, необходимо вручную настроить TrustedHosts.

**Изменение TrustedHosts с помощью команд PowerShell:**

1. Откройте сеанс PowerShell от имени администратора.
2. Просмотрите текущие настройки TrustedHosts:

    ```powershell
    Get-Item WSMan:\localhost\Client\TrustedHosts
    ```

   > [!WARNING]
   > Если текущий параметр TrustedHosts не является пустым, приведенные ниже команды перезапишут его. Рекомендуется сохранить текущий параметр в текстовый файл с помощью следующей команды, чтобы его можно было восстановить при необходимости.
   > 
   > `Get-Item WSMan:localhost\Client\TrustedHosts | Out-File C:\OldTrustedHosts.txt`

3. Задайте для TrustedHosts значение NetBIOS, IP-адреса или полного доменного имени компьютеров, которыми вы планируете управлять:

    ```powershell
    Set-Item WSMan:localhost\Client\TrustedHosts -Value '192.168.1.1,server01.contoso.com,server02'
    ```

   > [!TIP]
   > Простой способ задать все значения TrustedHosts за один раз заключается в использовании подстановочных знаков.
   > 
   >     Set-Item WSMan:\localhost\Client\TrustedHosts -Value '*'

4. После завершения тестирования можно выполнить следующую команду в сеансе PowerShell с повышенными привилегиями для очистки параметров TrustedHosts:

    ```powershell
    Clear-Item WSMan:localhost\Client\TrustedHosts
    ```

5. Если вы ранее экспортировали параметры, откройте файл, скопируйте значения и используйте следующую команду:

    ```powershell
    Set-Item WSMan:localhost\Client\TrustedHosts -Value '<paste values from text file>'
    ```

## <a name="i-previously-had-windows-admin-center-installed-and-now-nothing-else-can-use-the-same-tcpip-port"></a>Windows Admin Center установлен ранее, и теперь ничего можно использовать один и тот же порт TCP/IP

Вручную выполните следующие две команды в командной строке с повышенными правами:

```cmd
netsh http delete sslcert ipport=0.0.0.0:443
netsh http delete urlacl url=https://+:443/
```

## <a name="azure-features-dont-work-properly-in-edge"></a>Компоненты Azure не работают в браузере Edge

Edge имеет [известные проблемы](https://github.com/AzureAD/azure-activedirectory-library-for-js/wiki/Known-issues-on-Edge) связанного зон безопасности, которые влияют на входа в Azure в Windows Admin Center. Если у вас возникают трудности, с помощью функций Azure, при использовании Edge, попробуйте добавить https://login.microsoftonline.com, https://login.live.com и URL-адрес шлюза как надежные сайты для разрешенных сайтов для Edge параметры блокирования всплывающих окон в браузере на стороне клиента. 

Выполните указанные ниже действия.
1. Поиск **обозревателя** в Windows меню "Пуск"
2. Перейдите к **безопасности** вкладку
3. В разделе **Надежные узлы** , щелкните на **сайты** и добавьте URL-адреса в открывшемся диалоговом окне. Вам потребуется добавить URL-адрес шлюза и https://login.microsoftonline.com и https://login.live.com.
4. Перейдите к **конфиденциальности** вкладку
5. В разделе **блокирование всплывающих окон** щелкните **параметры** и добавьте URL-адреса в открывшемся диалоговом окне. Вам потребуется добавить URL-адрес шлюза и https://login.microsoftonline.com и https://login.live.com.

## <a name="having-an-issue-with-an-azure-related-feature"></a>Возникла проблема с функции связанных с Azure?

Отправьте нам электронное письмо по адресу wacFeedbackAzure@microsoft.com со следующими сведениями:
* Общие проблемы, возвращенными [приведенные ниже вопросы](#providing-feedback-on-issues).
* Опишите свою проблему и шаги, предпринятые для воспроизведения проблемы. 
* Ранее регистрации шлюза в Azure с помощью New-AadApp.ps1 загружаемый скрипт и затем обновить до версии 1807? Или вы зарегистрировали шлюза в Azure с помощью пользовательского интерфейса из шлюза параметры > Azure?
* Такое учетную запись Azure, связанные с несколькими каталогами и клиентами?
    * Если это так: При регистрации приложения Azure AD для Windows Admin Center, был каталог, используемый каталогом по умолчанию в Azure? 
* У учетной записи Azure доступ к нескольким подпискам?
* У подписку, которую вы использовали присоединенного выставления счетов?
* Были вы вошли в несколько учетных записей Azure перед возникновением проблемы?
* Требуется ли многофакторная проверка подлинности учетной записи Azure?
* — Это компьютер, который вы пытаетесь управлять виртуальной Машины Azure?
* Windows Admin Center устанавливается на виртуальной Машине Azure?

## <a name="providing-feedback-on-issues"></a>Отправка отзывов о проблемах

Перейдите в средство "Просмотр событий" > "Приложения и службы" > Microsoft-ServerManagementExperience и проверьте наличие каких-либо ошибок и предупреждений.

Отправьте сообщение об ошибке в разделе [UserVoice](https://windowsserver.uservoice.com/forums/295071/category/319162?query=%5BBug%5D) с описанием проблемы.

Укажите все ошибки и предупреждения, которые удастся найти в журнале событий, а также следующие сведения: 

* Платформа, на которой **установлен** Windows Admin Center (Windows 10 или Windows Server):
    * Если установлен на сервере, что такое Windows [версии](#check-the-windows-version) из **компьютер под управлением обозревателя** для доступа к Windows Admin Center: 
    * Вы используете самозаверяющий сертификат, созданный установщиком?
    * Если вы используете свой собственный сертификат, соответствует ли имя субъекта компьютеру?
    * Если вы используете свой собственный сертификат, указано ли в нем альтернативное имя субъекта?
* Выполнена ли установка с настройками порта по умолчанию?
    * В противном случае, какой порт был указан?
* Компьютер, где **установлен** Windows Admin Center, присоединен к домену?
* [Версия](#check-the-windows-version) Windows, где **установлен** Windows Admin Center:
* Присоединен ли компьютер, который вы **пытаетесь отладить**, к домену?
* [Версия](#check-the-windows-version) Windows AC на компьютере, который вы **пытаетесь отладить**:
* Какой браузер вы используете?
    * Если вы используете Google Chrome, какая у него версия? (Справка > О Google Chrome)

