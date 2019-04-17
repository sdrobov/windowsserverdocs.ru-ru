---
title: Обзор перенаправления папок автономных файлов и перемещаемых профилей пользователей
description: Обзор технологий перенаправление папок автономных файлов и перемещаемых профилей пользователей.
ms.prod: windows-server-threshold
ms.topic: article
author: JasonGerend
ms.author: jgerend
ms.technology: storage
ms.date: 04/05/2018
ms.localizationpriority: medium
ms.openlocfilehash: 4e3cf32cd718b906f16fc09901284d8520177df8
ms.sourcegitcommit: 375e94dc70c76e7aa5679c32f0f4dbc26cf7dd83
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2018
ms.locfileid: "2233500"
---
# <a name="folder-redirection-offline-files-and-roaming-user-profiles-overview"></a>Обзор перенаправления папок автономных файлов и перемещаемых профилей пользователей

>Применимо к: Windows 10, Windows 8, Windows 8.1, Windows Server 2012, Windows Server 2012 R2, Windows Server 2016

В этом разделе рассматриваются перенаправление папок, автономные файлы (кэширование на стороне клиента или CSC) и технологий перемещаемых профилей пользователей (также известные как RUP), включая новые и где найти дополнительные сведения.

## <a name="technology-description"></a>Описание технологии

Технологии автономных файлов и перенаправления папок при совместном использовании позволяют перенаправлять путь к локальным папкам (например, к папке документов) в какое-либо место в сети. При этом для увеличения скорости и улучшения доступности кэширование содержимого производится локально. Технология перемещаемых профилей пользователей позволяет перенаправлять профиль пользователя в какое-либо место в сети. Эти функции, используемые для рассматриваться, как Intellimirror.

- **Перенаправление папок** позволяет пользователям и администраторам перенаправлять путь известной папки в новое расположение вручную или с помощью групповой политики. Новое расположение может быть папка на локальном компьютере или каталогов в общей папке. Пользователи взаимодействуют с файлы в папке перенаправления, как если бы он существовал на локальный диск. Например можно перенаправить папку «документы», которая обычно находится на локальном диске, в сетевую папку. Файлы в папке, в затем доступны пользователю с любого компьютера в сети.
- **Автономные файлы** доступны сетевых файлов для пользователей, даже в том случае, если сетевое подключение к серверу, недоступен или медленно. При работе в сети, файл доступа работает на скорости сети и сервера. При работе в автономном режиме, извлечение файлов из папки автономных файлов на скорости локального доступа. Переключает компьютер в автономном режиме при:
  - Включен режим **Всегда в автономном режиме**
  - Сервер недоступен
  - Сетевое подключение более медленными, чем настраиваемый порог
  - Пользователь вручную переключается в автономный режим с помощью кнопки **работы в автономном режиме** в проводнике Windows
- **Перемещаемые профили пользователей** перенаправляет профили пользователей в общей папке, чтобы пользователи получали же операционной системы и параметров приложения на нескольких компьютерах. При входе пользователя в систему компьютера с помощью учетной записи, которая настроена в общей папке, как путь к профилю, профиль пользователя загружается на локальный компьютер и объединить с локальным профилем (если есть). При входе пользователя из системы компьютера, локальную копию профиля, включая все изменения объединяются с копией на сервере профиля. Как правило сетевой администратор включает перемещаемых профилей пользователей для учетных записей домена.

## <a name="practical-applications"></a>Практическое применение

Администраторы могут использовать перенаправление папок, автономные файлы и перемещаемых профилей пользователей для централизации хранения для данных и параметров пользователя и предоставить пользователям возможность доступа к своим данным во время в автономном режиме или в случае отказа сети или сервера. Некоторые определенные приложения включают:

- Централизовать данные из клиентских компьютеров для административных задач, таких как с помощью средств резервного копирования на стороне сервера для резервного копирования папки пользователей и параметры.
- Позволяют пользователям продолжить доступа к файлам сети, даже если сбой сети или сервера.
- Оптимизировать использование пропускной способности и расширяют возможности пользователей в филиалах, имеющие доступ к файлы и папки, которые размещены серверы находится вне офиса.
- Включение пользователей мобильных устройств для доступа к файлам в сети при работе в автономном режиме или в медленных сетях.

## <a name="new-and-changed-functionality"></a>Новые и измененные функции

В следующей таблице описаны некоторые из основных изменений в перенаправление папок автономных файлов и перемещаемых профилей пользователей, которые доступны в этой версии.

|Компонент или функция|Новый или обновленный компонент|Описание|
|---|---|---|
|Всегда автономный режим|Новый|Обеспечивает более быстрый доступ к файлам и снижение пропускной способности, всегда работа в автономном режиме, даже если подключены через высокоскоростное сетевое подключение.|
|Принять во внимание стоимость синхронизации|Новый|Помогает пользователям избежать затраты на использование высокой данных из синхронизации во время использования лимитным тарифным планом подключения, имеющие ограничения на использование или при роуминге сети другого поставщика.|
|Основной поддержки компьютера|Новый|Позволяет ограничить использование перенаправления папок, перемещаемых профилей пользователей и компьютеры пользователя основной.|

## <a name="always-offline-mode"></a>Всегда автономный режим

Начиная с Windows 8 и Windows Server 2012, администраторы могут настроить работы пользователей автономные файлы всегда работать в автономном режиме, даже когда они подключаются через высокоскоростное сетевое подключение. Файлы в кэше автономных файлов обновлений Windows путем синхронизации каждый час в фоновом режиме, по умолчанию.

### <a name="what-value-does-always-offline-mode-add"></a>Значения, которые означает всегда в автономном режиме Добавление режиме?

Всегда автономный режим дает следующие преимущества:

- Пользователи сталкиваются с более быстрый доступ к файлам в перенаправленных папок, таких как папку «документы».
- Уменьшается пропускная способность сети, сокращение расходов на дорогостоящих подключений по ГЛОБАЛЬНЫМ или чтобы подключений, такие как сеть мобильной 4 ГБ.

### <a name="how-has-always-offline-mode-changed-things"></a>Всегда автономный режим изменении действия?

До Windows 8, Windows Server 2012 пользователей будет перехода между режимами Online и не в сети, в зависимости от доступности сети и условия, даже в том случае, если был включен и равен 1 миллисекунды медленное подключение режиме (также известной как медленное подключение) Пороговое значение задержки.

С помощью всегда автономный режим компьютеров никогда не переход в оперативный режим при настройке параметра групповой политики **Настройте режим медленного** и пороговое значение параметра **задержки** установлено до 1 мс. Синхронизации изменений в фоновом режиме каждые 120 минут по умолчанию, но синхронизации может быть настроен с помощью параметра групповой политики **Настройки синхронизации фона** .

[Всегда автономный режим для предоставления более быстрый доступ к файлам](enable-always-offline.md)для получения дополнительных сведений см.

## <a name="cost-aware-synchronization"></a>Принять во внимание стоимость синхронизации

С поддержкой стоимость синхронизации Windows отключает синхронизацию фона, когда пользователь с помощью лимитным тарифным планом сетевое подключение, например, в сети 4 ГБ для мобильных устройств и подписчика near или через их ограничение пропускной способности или перемещения в сети другого поставщика.

>[!NOTE]
>Чтобы сетевых подключений обычно есть задержек приема-передачи сети, которые являются более медленными, чем значение задержки 35 миллисекунды по умолчанию для перевода в режим автономно (медленное подключение) в Windows 8, Windows Server 2012 и Windows Server 2016. Таким образом эти подключения обычно переход в режим автономно (медленное подключение) автоматически.

### <a name="what-value-does-cost-aware-synchronization-add"></a>Какие значение добавить принять во внимание стоимость синхронизации?

Принять во внимание стоимость синхронизации помогает пользователям избежать затрат неожиданно высокая данных об использовании во время использования лимитным тарифным планом подключения, имеющие ограничения на использование или при роуминге сети другого поставщика.

### <a name="how-has-cost-aware-synchronization-changed-things"></a>Принять во внимание стоимость синхронизации изменении действия?

До Windows 8 и Windows Server 2012 для отслеживания их использования данных с помощью средств от поставщика сеть мобильной имел пользователей для сведения к минимуму сборов во время использования автономных файлов на лимитным тарифным планом сетевых подключений. Пользователи могут вручную перейдите в автономном режиме, когда они перемещения, рядом с их ограничение пропускной способности или через предела.

С поддержкой стоимость синхронизации Windows автоматически отслеживает перемещения и пропускной способности ограничения на использование в лимитным тарифным планом подключений. После перемещения пользователя рядом с их ограничение пропускной способности, или через их ограничение Windows переключается в автономный режим и отключает все синхронизации. Пользователь может вручную запускать синхронизацию, и Администраторы могут переопределить принять во внимание стоимость синхронизации для конкретных пользователей, такие как руководители.

Дополнительные сведения можно [Включить синхронизацию файлов фона в сетях, чтобы](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/jj127408(v%3dws.11)).

## <a name="primary-computers-for-folder-redirection-and-roaming-user-profiles"></a>Основной компьютеров для перенаправления папок и перемещаемых профилей пользователей

Теперь можно назначить набор компьютеров, известных как основной компьютеров, для каждого пользователя домена, который позволяет контролировать, какие компьютеры использовать перенаправление папок и перемещаемых профилей пользователей. Назначение основного компьютеры — это простой и мощный метод для связи с конкретной компьютерах или устройствах, данными и параметрами пользователей упростить наблюдение администратора, повышения безопасности и защиты профили пользователей из повреждения.

### <a name="what-value-do-primary-computers-add"></a>Значения, которые следует добавлять основной компьютеров?

Существует четыре основных преимущества назначение основного компьютеров для пользователей.

- Администратор может указать компьютеры, которые пользователи могут использовать для доступа к своим перенаправления данных и параметров. Например администратор можно выбрать для смены пользователя настольных и портативных данных и параметров пользователя и не перемещать сведения при входе пользователя на любом компьютере, например, на компьютер комнаты конференции.
- Определение основного компьютеров сокращает безопасности и конфиденциальности риск оставляя остаточные данные личных или корпоративным на компьютерах, где пользователь вошел в систему. Например генеральный директор, который входит на компьютер сотрудника для временного доступа не оставляет за собой все личные или корпоративные данные.
- Основной компьютеров включить администратор может снизить риск неправильно настроенного или поврежден профиля, который может быть по-разному перемещения между настройку систем, такие как между компьютеров x86 и x64.
- Время, необходимое для пользователя первый вход на компьютере дополнительный, например, сервер, выполняется быстрее, так как пользователя перемещаемых профилей пользователей и/или перенаправленные папки не загружаются. Времени выхода также снижение, так как изменения профилей пользователей необходимо загрузить в общую папку файлов.

### <a name="how-have-primary-computers-changed-things"></a>Как основной компьютеров были изменены действия?

Чтобы ограничить загрузку личных данных пользователя на основной компьютеров, технологий перенаправление папок и перемещаемых профилей пользователей выполняются следующие проверки логики при входе пользователя в систему компьютера:

1. Новые параметры групповой политики (**файл для загрузки перемещаемых профилей основной только на компьютерах** и **перенаправления папки основного только на компьютерах**) для определения, если для атрибута **MsDS главный компьютер** в активный проверку операционной системы Windows Доменных служб Directory (AD DS) должны повлиять решение перемещаться в профиле пользователя или перенаправлять папки.
2. Если параметр политики обеспечивает поддержку основного компьютера, Windows проверяет, что схемы Доменные службы Active Directory поддерживает атрибута **MsDS главный компьютер** . В этом случае Windows определяет, если компьютер, который вход пользователя в используется в качестве основного компьютера для пользователя следующим образом:
    1. Если компьютер — это один из компьютеров основного пользователя, Windows применяет параметры перемещаемые профили пользователей и перенаправление папок.
    2. Если компьютер не является основным компьютеры пользователей, Windows загружает кэширования локального профиля пользователя, если этот параметр указан, или создает новый локальный профиль. Windows также удаляет все существующие перенаправленные папки согласно удаления действие, которое было указано ранее примененные параметр групповой политики, сохраняются в локальной конфигурации перенаправления папок.

Дополнительные сведения можно [Развернуть основной компьютеров для перенаправления папок и перемещаемых профилей пользователей](deploy-primary-computers.md)

## <a name="hardware-requirements"></a>Требования к оборудованию

Перенаправление папок, автономные файлы и перемещаемых профилей пользователей требуется x64 или x86 компьютера, и они не поддерживаются операционной системой Windows на компьютерах под управлением ARM WOA.

## <a name="software-requirements"></a>Требования к программному обеспечению

Чтобы назначить основной компьютеров, среда должна соответствовать следующим требованиям:

- Схемы доменных служб Active Directory (AD DS) необходимо обновить до версии включают в себя схемы Windows Server 2012 и условия (установка Windows Server 2012 или более поздняя версия контроллера домена автоматически обновляет схему). Дополнительные сведения об обновлении схемы Доменные службы Active Directory можно [Обновление контроллеров домена для Windows Server 2016](../../identity/ad-ds/deploy/upgrade-domain-controllers.md).
- Клиентские компьютеры, необходимо запустить Windows 10, Windows 8.1, Windows 8, Windows Server 2016, Windows Server 2012 R2 или Windows Server 2012 и быть присоединен к домену Active Directory, управление которым осуществляется.

## <a name="more-information"></a>Дополнительные сведения

Дополнительные сведения по данной теме см. на следующих ресурсах.

|Тип содержимого|Ссылки|
|---|---|
|Оценка продукта|[Поддержка информационных работников с надежным файловых служб и хранилища](<https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh831495(v%3dws.11)>)<br>[Новые возможности автономных файлов](<https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ff183315(v=ws.10)>) (Windows 7 и Windows Server 2008 R2)<br>[Новые возможности в автономных файлов для Windows Vista](<https://docs.microsoft.com/previous-versions/windows/it-pro/windows-vista/cc749449(v=ws.10)>)<br>[Изменения автономных файлов в Windows Vista](<https://technet.microsoft.com/library/2007.11.offline.aspx>) (Журнал TechNet)|
|Развертывание|[Развертывание перенаправление папок, автономные файлы и перемещаемых профилей пользователей](deploy-folder-redirection.md)<br>[Реализация решения централизации данных конечных пользователей: перенаправление папок и автономные файлы технологии проверки и развертывания](http://download.microsoft.com/download/3/0/1/3019A3DA-2F41-4F2D-BBC9-A6D24C4C68C4/Implementing%20an%20End-User%20Data%20Centralization%20Solution.docx)<br>[Управление перемещения руководство по развертыванию данных пользователя](<https://docs.microsoft.com/previous-versions/windows/it-pro/windows-vista/cc766489(v=ws.10)>)<br>[Настройка новой автономной файлы компонентов для компьютеров Windows 7: пошаговое руководство](<https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ff633429(v=ws.10)>)<br>[С помощью перенаправления папок](<https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753996(v=ws.11)>)<br>[Реализация перенаправление папок](<https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc737434(v=ws.10)>) (Windows Server 2003)|
|Средства и параметры|[Автономные файлы на сайте MSDN](https://msdn.microsoft.com/library/cc296092.aspx)<br>[Справочник по автономные файлы групповой политики](https://msdn.microsoft.com/library/ms878937.aspx) (Windows 2000)|
|Ресурсы сообщества|[Форум по файловым службам и хранению](https://social.technet.microsoft.com/forums/windowsserver/home?forum=winserverfiles)<br>[Привет автор сценариев! Как работают с помощью функции автономных файлов в Windows](<https://blogs.technet.microsoft.com/heyscriptingguy/2009/06/02/hey-scripting-guy-how-can-i-enable-and-disable-offline-files/>)<br>[Привет автор сценариев! Как включить и отключить автономные файлы?](<https://blogs.technet.microsoft.com/heyscriptingguy/2009/06/02/hey-scripting-guy-how-can-i-enable-and-disable-offline-files/>)|
Связанные технологии|[Удостоверениями и доступом в Windows Server](../../identity/identity-and-access.md)<br>[Хранилище в Windows Server](../storage.md)<br>[Удаленный доступ и управление серверами](../../remote/index.md)|