---
title: Удаленный рабочий стол - сравнение клиентских приложений
description: Узнайте, как различных приложений к удаленному рабочему Столу сравнения, когда речь идет о поддерживаемых возможностях и функциях.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: remote-desktop-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 12efe858-6b76-4e08-9f72-b9603aceb0fc
author: lizap
manager: dongill
ms.author: elizapo
ms.date: 06/22/2018
ms.localizationpriority: medium
ms.openlocfilehash: fc20d1a2c51abddb8ae014efc621f4f0b36c3677
ms.sourcegitcommit: d3f73936160505a40633ad8dd5931ac5fe3eccdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "9297413"
---
# Сравнение клиентских приложений

>Область применения: Windows 10, Windows 8.1, Windows Server 2019 г., Windows Server 2016, Windows Server 2012 R2

Мы часто предлагается сравнение разных приложений клиент удаленного рабочего стола друг с другом. Все они сделать то же самое? Ниже приведены ответы на эти вопросы.

## Поддержка перенаправления

Следующие таблицы сравнить поддержку устройств и других перенаправления приложения подключение к удаленному рабочему столу, универсальное приложение, Android приложения, приложение для iOS, приложения и веб-клиент macOS. В таблицах охватывают перенаправления, которые вы можете получить доступ к один раз в удаленном сеансе. 

Если вы удаленного в ваше личное рабочего стола, существуют дополнительные перенаправления, которые можно настроить **Дополнительные параметры** для сеанса. Если удаленный рабочий стол или приложений контролируются вашей организацией, ваш администратор можно включить или отключить перенаправление с помощью параметров групповой политики.

### Перенаправления ввода

| Перенаправление | Удаленный рабочий стол<br> "Подключение" | Универсальный | Android | iOS | macOS | веб-клиент |
|-------------|-------------------------------|-----------|---------|-----|-------|------------|
| Клавиатура    | X                             | X         | X       | X   | X     | X          |
| Мышь       | X                             | X         | X       | X *    | X     | X          |
| Сенсорный ввод       | X                             | X         | X       | X   |       |            |
| Other       | Перо                           |           |         |     |       |            |
* Просмотрите [Список поддерживаемых устройств ввода для клиента удаленного рабочего стола iOS бета-версии](remote-desktop-ios.md#supported-input-devices).

### Перенаправление портов   

| Перенаправление | Удаленный рабочий стол <br>"Подключение" | Универсальный | Android | iOS | macOS | Веб-клиент |
|-------------|-------------------------------|-----------|---------|-----|-------|------------|
| Последовательный порт | X                             |           |         |     |       |            |
| USB         | X                             |           |         |     |       |            |

При включении перенаправление портов USB, любой USB-устройства, подключенные к USB-порту автоматически распознаются в удаленном сеансе.

### Другие перенаправления (устройства, и т. д)



| Перенаправление         | Подключение к удаленному рабочему столу | Универсальный   | Android | iOS         | macOS                                    | Веб-клиент    |
|---------------------|---------------------------|-------------|---------|-------------|------------------------------------------|---------------|
| Камеры             | X                         |             |         |             |                                          |               |
| Буфер обмена           | X                         | текст, изображения | текст    | текст, изображения | X                                        | текст          |
| Локальный диск или хранилище | X                         |             | X       |             | x                                        |               |
| Назначение            | X                         |             |         |             |                                          |               |
| Микрофоны         | X                         |X            |         |             | X                                        |               |
| Printers            | X                         |             |         |             | X (КОФЕЕН)                            | Печать PDF     |
| Сканеры            | X                         |             |         |             |                                          |               |
| Смарт-карты         | X                         |             |         |             | X (проверка подлинности Windows не поддерживается) |               |
| Speakers            | X                         | X           | X       | X           | X                                        | X (за исключением IE) |

* Для перенаправление - приложения для macOS поддерживает драйвер фотонабора "издатель" по умолчанию. Они не поддерживают перенаправление собственные драйверы.

### Параметры поддерживаемых протокола удаленного рабочего СТОЛА
Эта таблица содержит список поддерживаемых параметров файла протокола удаленного рабочего СТОЛА, которые могут использоваться с клиентами Windows и HTML. «X» в столбце "Платформа" означает, что параметр поддерживается. Обратите внимание, что это не исчерпывающий список поддерживаемых параметров для клиентов Windows и HTML5. Мы продолжим для обновления в этой таблице для включения более поддерживаемые параметры RDP для клиентов Windows и HTML5, а также macOS, iOS и Android клиентов.

| Параметр протокола удаленного рабочего СТОЛА                        | Описание            | Значения                 | Значение по умолчанию          | Виртуального рабочего стола Windows | Windows | HTML5   |
|------------------------------------|------------------------|------------------------|:----------------------:|:-----------------------:|:-------:|:-------:|
| Альтернативный полный адрес: s:value | Указывает альтернативное имя или IP-адрес удаленного компьютера. | Любое допустимое имя или IP-адрес удаленного компьютера, например, «10.10.15.15» | | x | x | x |
| Альтернативный оболочки: s:value        | Определяет, будет ли программы автоматически запускается при подключении с помощью протокола удаленного рабочего СТОЛА. Этот параметр соответствует программы путь и имя поле на вкладке "программы" подключение к удаленному рабочему столу клиента. Для указания альтернативных оболочки, введите правильный путь к исполняемому файлу для значения, например ««C:\ProgramFiles\Office\word.exe»». Этот параметр также определяет путь или псевдоним удаленного приложения для работы во время подключения, если включен RemoteApplicationMode. | например «C:\ProgramFiles\Office\word.exe» || x | x | x |
| audiocapturemode:i:value | Указывает, включена ли перенаправление звука ввода вывода. Этот параметр соответствует поле удаленного звука клиент подключения удаленного рабочего стола. | (0) отключение аудиозаписи из локального устройства; (1) включите записи звука из локального устройства и перенаправления в приложение звука в удаленном сеансе | 0 | x | x | |
| audiomode:i:value | Определяет, какой компьютер (т. е. локального или удаленного) воспроизводится звук. | (0) звуков на локальном компьютере (воспроизвести на этом компьютере); (1) воспроизвести звук на удаленном компьютере (воспроизвести на удаленном компьютере); (2) не звуки (не воспроизводятся) | 0 | x | x | x |
| уровень проверки подлинности: i:value | Определяет уровень настройки проверки подлинности сервера. | (0) при сбое проверки подлинности сервера, подключитесь к компьютеру без предупреждения (Connect и не предупреждать); (1) в случае сбоя проверки подлинности сервера, не установить соединение (не подключаться); (2) Если проверки подлинности сервера, отображения предупреждения и разрешить подключения или отказаться от подключения (Предупреждать); (3) не требуется проверка подлинности задается. | 3 | x | x ||
| autoreconnection включено: i:value | Этот параметр определяет, является ли клиентский компьютер будет автоматически пытаться подключиться к удаленному компьютеру, если выполняется сброс подключения; Например, при отключении подключения к сети. Этот параметр соответствует переподключения Если подключение отброшенных флажок на вкладке "возможности" в разделе параметров в удаленного рабочего стола (RDC).| (0) клиентский компьютер не пытается автоматически подключиться; (1) клиентский компьютер автоматически пытаться подключиться| 1 | x | x | x |
| bandwidthautodetect:i:value | Определяет, включена ли автоматическое сети тип обнаружения | Определение типа (0) отключение автоматического сети; (1) включить обнаружение тип автоматического сети | 1 | x | x | x |
| сжатие: i:value | Этот параметр определяет, включена ли массового сжатия при передаче, протокола удаленного рабочего СТОЛА на локальном компьютере.|(0) сжатия массового отключить протокола удаленного рабочего СТОЛА; (1) включить сжатие массового протокола удаленного рабочего СТОЛА | 1 | x | x | x |
| Идентификатор: i:value размер рабочего стола | Задает размеры рабочего стола удаленного сеанса из предопределенных параметров. Если указаны desktopheight или desktopwidth переопределяется этот параметр.| (0) 640 x 480; (1) 800 x 600; (2) 1024 x 768; (3) 1280 x 1024; (4) 1600 x 1200 | 0 | x | x | x |
| desktopheight:i:value | Этот параметр определяет высоту разрешение (в пикселях) на удаленном компьютере, при подключении с помощью удаленного рабочего стола (RDC). Этот параметр соответствует состоянию configurationslider установленным на underOptions theDisplaytab в RDC. | Числовое значение от 200 до 2048 | Значение по умолчанию имеет значение с разрешением на локальном компьютере | x | x | x |
| desktopwidth:i:value | Этот параметр определяет толщину разрешение (в пикселях) на удаленном компьютере, при подключении с помощью удаленного рабочего стола (RDC). Этот параметр соответствует состоянию configurationslider установленным на underOptions theDisplaytab в RDC. | Числовое значение от 200 до 4096 | Значение по умолчанию имеет значение с разрешением на локальном компьютере | x | x | x |
| disableclipboardredirection:i:value | Этот параметр определяет, включена ли перенаправление буфера обмена при подключении к удаленному компьютеру. | Включено (0) перенаправление буфера обмена; (1) перенаправление буфера обмена не включена | x | x | x |
| disableconnectionsharing:i:value | Определяет, подключается к все существующие подключения откройте клиента удаленного рабочего стола или инициировать запрос нового подключения при запуске RemoteApp или рабочего стола | (0) переподключение к любой существующей сеанса. (1) запуска нового подключения | 0 | x | x | x |
| disableprinterredirection:i:value | Этот параметр определяет, включена ли перенаправление легко печати принтера при подключении к удаленному компьютеру. | Включено (0) перенаправление печати легко печати; (1) отключено позволяет перенаправление печати | x | x | x |
| домен: s:value | Этот параметр указывает имя домена, в которой находится учетная запись пользователя, который будет использоваться для входа на удаленном компьютере с помощью удаленного рабочего стола (RDC). Значение этого параметра, вместе с параметра имя пользователя, будет отображаться в поле nametext альтернативному на theGeneraltab underOptionsin RDC. | Является допустимым именем домена, например, «CONTOSO» | Значение по умолчанию отсутствует | x | x | x |
| drivestoredirect:s:value | Определяет, какие локальные жесткие диски на клиентском компьютере перенаправленных и доступны в удаленном сеансе. | Значение не задано - не перенаправлять все диски; * - Перенаправлять все диски, в том числе диски, подключенные в более поздней версии; DynamicDrives - перенаправлять все диски, подключенные в более поздней версии; Диск и метки для одного или нескольких дисков - перенаправить указанного диски.| Значение не задано - не перенаправлять все диски | x | x    | |
| enablecredsspsupport:i:value | Этот параметр определяет, использует ли протокола удаленного рабочего СТОЛА поставщика поддержки безопасности учетных данных (CredSSP) для проверки подлинности при его наличии. | (0) протокола удаленного рабочего СТОЛА не будет использовать CredSSP, даже если операционная система поддерживает CredSSP; (1) протокола удаленного рабочего СТОЛА будет использовать CredSSP, если операционная система поддерживает CredSSP | 1 | x | x | |
| Полный адрес: s:value | Этот параметр указывает имя или IP-адрес удаленного компьютера, на котором вы хотите подключиться к | Допустимое имя компьютера, адрес IPv4 или IPv6-адрес - указывает удаленный компьютер, к которому следует подключиться. | | x | x | x |
| GatewayCredentialsSource:i:value | Указывает или получает метод проверки подлинности шлюза удаленных рабочих Столов. | (0) запрашивать пароль (NTLM); (1) использования смарт-карт; (4) позволяют пользователю выбрать более поздней версии | 0 | x | x | x |
| gatewayhostname:s:value | Задает имя узла шлюза удаленных рабочих Столов. | Допустимый адрес шлюза. ||x|x|x|
| gatewayprofileusagemethod:i:value | Указывает, следует ли использовать параметры по умолчанию шлюза удаленных рабочих Столов | (0) используйте режим профиль по умолчанию, как указано администратором; (1) использовать явные параметры, как указано пользователем. | 0 | x | x | x |
| gatewayusagemethod:i:value | Указывает, когда следует использовать сервер шлюза удаленных рабочих Столов | (0) не использовать сервер шлюза удаленных рабочих Столов; (1) всегда используйте сервер шлюза удаленных рабочих Столов; (2) используйте на сервере шлюза удаленных рабочих Столов, если не могут быть сделаны прямое подключение для узла сеансов удаленных рабочих Столов; (3) используйте параметры по умолчанию сервер шлюза удаленных рабочих Столов; (4) не использовать шлюза удаленных рабочих Столов, не использовать сервер для локальных адресов; Это значение свойства 0 или 4 — эквивалентно эффективно, но этого свойства значение 4 включен параметр для обхода локальных адресов. | | x | x | x |
| networkautodetect:i:value | Определяет, следует ли использовать обнаружение пропускной способности автоматического сети или нет. Optionbandwidthautodetectto должны быть установлены и сопоставляет withconnection type7. | (0) не используйте обнаружение пропускной способности автоматического сети; (1) используйте обнаружение пропускной способности автоматического сети | 1 | x ||x|
| PromptCredentialOnce:i:value | Определяет, является ли учетные данные пользователя сохраняются и используются для шлюза удаленных рабочих Столов и на удаленном компьютере.|(0) удаленный сеанс не будет использовать те же учетные данные; (1) удаленный сеанс будет использовать те же учетные данные|1|x|x||
| redirectclipboard:i:value | Этот параметр определяет, будет ли буфера обмена на локальном компьютере перенаправленных и доступны в удаленном сеансе. Этот параметр соответствует полю theClipboardcheck на theLocal Resourcestab underOptionsin RDC. | Буфер обмена (0) на локальном компьютере не поддерживается в удаленном сеансе. (1) буфер обмена на локальном компьютере доступен в удаленном сеансе|1|x|x|x|
| redirectdrives:i:value | Этот параметр определяет, будет ли диски на клиентском компьютере перенаправленных и доступны в удаленном сеансе. Этот параметр соответствует underOptionsin Resourcestab theLocal forDrivesunderMoreon выбранные параметры RDC.|(0) диски на локальном компьютере не доступны в удаленном сеансе; (1) диски на локальном компьютере доступны в удаленном сеансе|0|x|x| |
| redirectprinters:i:value | Этот параметр определяет, будет ли принтеров, настроенных на клиентском компьютере перенаправленных и доступны в удаленном сеансе при подключении к удаленному компьютеру с помощью удаленного рабочего стола (RDC). Этот параметр соответствует выбора в поле thePrinterscheck на theLocal Resourcestab underOptionsin RDC. | (0) принтеры на локальном компьютере не доступны в удаленном сеансе; (1 принтеры локального компьютера доступны в удаленном сеансе|1|x|x|x|
| redirectsmartcards:i:value | Этот параметр определяет, будет ли устройств смарт-карт на клиентском компьютере перенаправленных и доступны в удаленном сеансе при подключении к удаленному компьютеру с помощью удаленного рабочего стола (RDC). Этот параметр соответствует выделение в theSmart cardscheck поле underMore на theLocal Resourcestab underOptionsin RDC.|(0) устройства смарт-карт на локальном компьютере недоступна в удаленном сеансе; (1) устройства смарт-карт на локальном компьютере доступен в удаленном сеансе|1|x|x||
| remoteapplicationcmdline:s:value | Параметры необязательно командной строки для RemoteApp.||x|x|x|
| remoteapplicationexpandcmdline:i:value| Определяет, будет ли переменные среды, содержащиеся в качестве параметра командной строки RemoteApp должен быть развернут локально или удаленно.|(0) переменные среды должен быть развернут значения на локальном компьютере; (1) переменные среды должен быть развернут на удаленном компьютере значения удаленного компьютера||x|x|x|
| remoteapplicationexpandworkingdir | Определяет, будет ли переменные среды, содержащиеся в параметре RemoteApp рабочий каталог должен быть развернут локально или удаленно. | (0) переменные среды должен быть развернут значения на локальном компьютере; (1) переменные среды должен быть развернут на удаленном компьютере значения удаленного компьютера. Примечание: Рабочий каталог RemoteApp задается через параметр оболочки рабочий каталог.||x|x|x|
|remoteapplicationfile:s:value | Определяет файл для открытия, RemoteApp на удаленном компьютере. Примечание: Для локальных файлов для открытия, необходимо также включить перенаправление дисков для исходного диска.||x|x|x|
|remoteapplicationicon:s:value | Задает файл значка для отображения пользовательского интерфейса на клиенте во время запуска RemoteApp. Если имя файла не указано, клиент будет использовать стандартный значок удаленного рабочего стола. Поддерживаются только файлы «.ico».||x|x|x|
|remoteapplicationmode:i:value | Определяет, будет ли подключение RemoteApp запускается сеанс RemoteApp.| (0) не запускать сеанс RemoteApp. (1) запуска сеанса RemoteApp|1|x|x|x|
|remoteapplicationname:s:value | Указывает имя RemoteApp в интерфейсе клиента при запуске RemoteApp.| например «Excel 2016»|x|x|x|
|remoteapplicationprogram:s:value | Указывает имя псевдонима или исполняемого файла RemoteApp. | Например «EXCEL» |x|x|x|
|Идентификатор режима экрана: i:value | Этот параметр определяет, отображается ли окно удаленного сеанса полноэкранном режиме при подключении к удаленному компьютеру с помощью удаленного рабочего стола (RDC). Этот параметр соответствует состоянию configurationslider установленным на theDisplaytab underOptionsin RDC.|(1) удаленный сеанс будет отображаться в окне. (2) удаленный сеанс будет отображаться в полноэкранном режиме|2|x|x|x|
|смарт-размера: i:value | Этот параметр определяет, может ли на клиентском компьютере масштабирования содержимого на удаленном компьютере в соответствии с размером окна клиентского компьютера.|(0) не будет масштабироваться представления окна клиента при изменении размеров; (1) в окно клиент будет масштабироваться при изменении размера|0|x|x||
| Используйте multimon:i:value | Этот параметр настраивает поддержку нескольких мониторов при подключении к удаленному компьютеру с помощью удаленного рабочего стола (RDC).|(0) не включайте поддержку нескольких мониторов; (1) включить поддержку нескольких мониторов|0|x|x||
| username:s:value | Этот параметр указывает имя учетной записи пользователя, который будет использоваться для входа на удаленном компьютере с помощью удаленного рабочего стола (RDC). Значение этого параметра, вместе с параметра домена, будут отображаться в namebox альтернативному на theGeneraltab underOptionsin RDC.| Любое имя пользователя. ||x|x|x|
| videoplaybackmode:i:value| Этот параметр определяет, если удаленного рабочего стола (RDC) будет использовать протокола удаленного рабочего СТОЛА эффективный потокового мультимедиа для воспроизведения видео.|(0) не используйте протокола удаленного рабочего СТОЛА эффективный потокового мультимедиа для воспроизведения видео; (1) потоковую протокола удаленного рабочего СТОЛА эффективный мультимедиа для воспроизведения видео, когда это возможно|1|x|x||
| workspaceid:s:value | Этот параметр определяет RemoteApp и рабочего стола идентификатор, связанный с RDP-файл, содержащий этот параметр. | Допустимые RemoteApp и идентификатор подключения рабочего стола|x|x||