---
title: Планирование сервера политики сети как RADIUS-прокси
description: Этот раздел содержит сведения о планировании в Windows Server 2016 развертывания прокси-сервера RADIUS сервера политики сети.
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: ca77d64a-065b-4bf2-8252-3e75f71b7734
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 966e555ebcac6c7daf4a26b322f0d29f023f8539
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="plan-nps-as-a-radius-proxy"></a>Планирование сервера политики сети как RADIUS-прокси

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

При развертывании сервера политики сети (NPS) как прокси \(RADIUS\) удаленной службы проверки подлинности удаленного пользователя NPS получает запросы на подключение от клиентов RADIUS, таких как серверы доступа к сети или другие RADIUS-прокси и пересылает эти запросы на подключение к серверам под управлением сервера политики сети или другие серверы RADIUS. Эти правила планирования можно использовать для упрощения развертывания RADIUS.

Эти правила планирования следует включать ситуации, в которых вы хотите развернуть сервер политики сети как RADIUS-сервер. При развертывании сервера политики сети как RADIUS-сервер, сервер политики сети выполняет проверку подлинности, авторизации и учету запросов на подключение для локального домена и доменов, которые доверяют локального домена.

Перед развертыванием сервера политики сети как RADIUS-прокси в сети, используйте следующие рекомендации для планирования развертывания.

- Планирование конфигурации сервера NPS.

- Планирование RADIUS-клиентов.

- Планирование удаленных групп серверов RADIUS.

- Планирование правила работы с атрибутами для переадресации сообщений.

- Планирование политики запросов на подключение.

- Планирование учета сервера политики сети.

## <a name="plan-nps-server-configuration"></a>Планирование конфигурации сервера NPS

При использовании сервера политики сети как RADIUS-прокси, сервер политики сети перенаправляет запросы на подключение к серверу политики сети или другие RADIUS-серверы для обработки. По этой причине членство в домене прокси-сервер политики сети не имеет значения. Прокси необходимо зарегистрировать в доменных службах Active Directory \(AD DS\), так как доступ к свойств удаленного доступа учетных записей пользователей не требуется. Кроме того необходимо настроить политики сети на прокси-сервер политики сети, так как прокси-сервер не выполняет авторизации запросов на подключение. Прокси-сервер политики сети может быть членом домена или автономный сервер с членство в домене.

Сервер политики сети необходимо настроить для взаимодействия с RADIUS-клиентов, также называемый серверы доступа к сети, с использованием протокола RADIUS. Кроме того можно настроить типы событий, NPS записей в событии журнал и вы можно ввести описание для сервера.

### <a name="key-steps"></a>Основные шаги

При планировании конфигурации прокси-сервера политики СЕТИ, можно использовать следующие действия.

- Определение портов RADIUS, прокси-сервера политики сети используется для получения сообщений RADIUS от клиентов RADIUS и отправлять сообщения RADIUS и членов удаленных групп серверов RADIUS. Порты по умолчанию протокола передачи датаграмм пользователя (UDP), 1812 и 1645 для сообщений проверки подлинности RADIUS и UDP-порты 1813 и 1646 для сообщений учета RADIUS.

- Если прокси-сервер политики сети настроен с несколькими сетевыми адаптерами, определение адаптеров, через которое необходимо разрешить RADIUS-трафика.

- Определите типы событий, которые вы хотите NPS для записи в журнале событий. Вы можете выполнить подключение отклоненных запросов и запросы успешное подключение.

- Определите, является ли вы развертываете несколько прокси-сервера политики сети. Чтобы обеспечить отказоустойчивость, использование по крайней мере два прокси-сервера политики сети. Один прокси-сервера политики сети используется в качестве основного RADIUS-прокси и других используется в качестве резервной копии. Все клиенты RADIUS затем настраивается на обоих прокси-серверов политики сети. Если основной прокси-сервер политики сети становится недоступным, RADIUS-клиенты передать сообщения запроса доступа альтернативный прокси-сервера политики сети.

- Планирование данный сценарий используется, чтобы скопировать одну конфигурацию прокси-сервера политики сети в других прокси-сервера политики сети для сохранения на администрирование и для предотвращения неправильной конфигурацией сервера. Сервер политики сети обеспечивает команды Netsh, которые дают возможность скопировать все или часть конфигурации прокси-сервера политики сети для импорта на другой прокси-сервера политики сети. Команды в командной строке Netsh можно запустить вручную. Однако при сохранении вашей последовательность команд, как сценарий, можно запустить сценарий позже, если вы решите изменить настройки прокси-сервера.

## <a name="plan-radius-clients"></a>Планирование RADIUS-клиентов

Клиенты RADIUS — это серверы сетевого доступа, например беспроводные точки доступа, серверы виртуальных частных сетей \(VPN\), 802.1 X-коммутаторами и серверы удаленного доступа. RADIUS-прокси, которые пересылать подключения сообщения запроса RADIUS-серверов, также являются клиентами RADIUS. Сервер политики сети поддерживает все серверы доступа к сети и RADIUS-прокси, совместимые с протоколом RADIUS, как описано в см,» удаленной проверки подлинности удаленного пользователя службы \(RADIUS\),» и RFC 2866, «RADIUS бухгалтерский учет».

Кроме того точки беспроводного доступа и коммутаторы должны быть поддерживают проверку подлинности 802.1 X. Если вы хотите развернуть Extensible Authentication Protocol (EAP) или проверки подлинности протокол PEAP (Protected Extensible), точки доступа и коммутаторы должны поддерживать использование протокола EAP.

Для тестирования базового взаимодействия для подключений по протоколу PPP для точки беспроводного доступа, настройте точки доступа и доступа к клиентскому компьютеру использовать протокол проверки подлинности пароля (PAP). Используйте протоколы дополнительной проверки подлинности по протоколу PPP, такими как PEAP, пока не проверите те, которые вы планируете использовать для доступа к сети.

### <a name="key-steps"></a>Основные шаги

Во время планирования RADIUS-клиентов, можно использовать следующие действия.

- Документ атрибутов поставщика (VSA), необходимо настроить на сервере политики сети. Если серверы доступа к сети требуется VSA, VSA записывает сведения в журнал для последующего использования при настройке политики в сети на сервере политики сети.

- Документ IP-адресов клиентов RADIUS и прокси-сервера политики сети, для упрощения настройки всех устройств. При развертывании клиентов RADIUS, необходимо настроить их для использования протокола RADIUS, с IP-адрес прокси-сервера NPS, указывается как сервер проверки подлинности. И при настройке сервера политики сети для взаимодействия с RADIUS-клиентов, необходимо ввести IP-адресов клиентов RADIUS в оснастку сервера политики сети.

- Создайте общие секреты для настройки клиентов RADIUS и в оснастке сервера политики сети. RADIUS-клиентов необходимо настроить общий секрет или пароль, который вводится в оснастку сервера политики сети во время настройки RADIUS-клиентов на сервере политики сети.

## <a name="plan-remote-radius-server-groups"></a>Планирование удаленных групп серверов RADIUS

При настройке группы внешних RADIUS-сервера на прокси-сервер политики сети, вы указываете серверу политики сети куда следует отправлять некоторые или все подключения сообщения запроса, которые он получает от серверы доступа к сети и другие RADIUS-прокси или прокси-сервера политики сети.

Можно использовать сервер политики сети как RADIUS-прокси для пересылки подключения запросов к одной или более удаленных групп серверов RADIUS, а каждая группа может содержать один или несколько серверов RADIUS. Если требуется прокси-сервера политики сети на пересылку сообщений в несколько групп, Настройка одной политики запросов на подключение на каждую группу. Политика запросов на подключение содержит дополнительные сведения, такие как правила работы с атрибутами, которые сообщают серверу политики сети какие сообщения для отправки группы внешних серверов RADIUS, указанный в политике.

Группы удаленных RADIUS-серверов можно настроить с помощью команды Netsh для сервера политики сети, путем настройки групп непосредственно в оснастке "сервера политики сети" в группе удаленных групп серверов RADIUS или путем запуска мастера новой политики запросов на подключение.

### <a name="key-steps"></a>Основные шаги

Во время планирования удаленных групп серверов RADIUS, можно использовать следующие действия.

- Определите, какие домены, содержащие RADIUS-серверов, на которых требуется прокси-сервера политики сети для пересылки запросов подключения. Эти домены содержат учетные записи пользователей для пользователей, которые подключаются к сети с помощью RADIUS-клиентов, которые будут развернуты.

- Определите, необходимо ли добавить новые серверы RADIUS в доменах, где RADIUS еще не развернуто.

- Документ IP-адресов серверов RADIUS, которые вы хотите добавить для удаленных групп серверов RADIUS.

- Определите, сколько удаленных групп серверов RADIUS, необходимо создать. В некоторых случаях лучше создание одной группы внешних RADIUS-сервера в домене, а затем добавьте RADIUS-серверов для домена в группу. Тем не менее может быть случаев, в которых имеется большой объем ресурсов одного домена, включая большим числом пользователей с учетными записями пользователей в домене, большое количество контроллеров домена и большим количеством серверов RADIUS. Или домен может закрывать больших географическую область, из-за которой имеется серверы доступа к сети и RADIUS-серверы в расположениях, которые удаленные друг от друга. В этих и, возможно, других случаях можно создать несколько удаленных групп серверов RADIUS каждого домена.

- Создайте общие секреты для конфигурации прокси-сервера политики сети и в удаленных серверов RADIUS.

## <a name="plan-attribute-manipulation-rules-for-message-forwarding"></a>Планирование правила работы с атрибутами для переадресации сообщений

Правила работы с атрибутами, которые настраиваются политики запросов на подключение, позволить вам идентифицировать сообщения запроса доступа, которые вы хотите отправлять определенные группы внешних серверов RADIUS.

Можно настроить сервер политики сети для пересылки всех запросов на подключение без использования правила работы с атрибутами одной группы внешних серверов RADIUS.

Если имеется более одного местоположения, к которому требуется переадресовывать запросы на подключение, тем не менее, необходимо создать политики запросов на подключение для каждого расположения, а затем настроить политику с помощью группы внешних серверов RADIUS в котором вы хотите пересылку сообщений, а также правила работы с атрибутами, указывающие NPS сообщений.

Можно создать правила для следующих атрибутов.

- Под названием станции-ИД. Номер телефона сервера доступа к сети (NAS). Значение этого атрибута — строку символов. Для задания области кодов можно использовать синтаксис соответствия шаблону.

- Идентификатор вызова станции. Номер телефона, с которого производится вызов. Значение этого атрибута — строку символов. Для задания области кодов можно использовать синтаксис соответствия шаблону.

- Имя пользователя. Имя пользователя, которое предоставляется клиентом доступа и включается NAS в сообщении запроса доступа RADIUS с. Значение этого атрибута — строку символов, который обычно содержит имя сферы и имя учетной записи пользователя.

Чтобы правильно заменить или преобразовать имена сфер в имени пользователя запроса на подключение, необходимо настроить правила работы с атрибутами для атрибута имени пользователя на политики запроса подключения.

### <a name="key-steps"></a>Основные шаги

Во время планирования правила работы с атрибутами, можно использовать следующие действия.

- Планирование маршрутизации сообщений от NAS через прокси-сервер для удаленных серверов RADIUS, убедитесь, что логический путь с помощью которого для перенаправления сообщений RADIUS-серверов.

- Определите один или несколько атрибутов, которые вы хотите использовать для каждой политики запросов на подключение.

- Документ правила манипуляции атрибутов, которые вы планируете использовать для каждой политики запроса подключения и сопоставлять правила для группы внешних серверов RADIUS, к которому будут перенаправлены сообщения.

## <a name="plan-connection-request-policies"></a>Планирование политики запросов на подключение

Политики запросов на подключение по умолчанию настраивается для сервера политики сети, при использовании в качестве RADIUS-сервера. Политики запросов на подключение, дополнительные можно определять особые условия, создать атрибут манипуляции правила, которые сообщают NPS сообщений для пересылки для удаленных групп серверов RADIUS, а также указать дополнительные атрибуты. Используйте мастер создания политики запроса подключения для создания подключения стандартных и пользовательских политик запросов.

### <a name="key-steps"></a>Основные шаги

При планировании политики запросов на подключение, можно использовать следующие действия.

- Удаление политики запросов на подключение по умолчанию на каждом сервере, которые работают под управлением NPS, выступает исключительно как RADIUS-прокси.

- Запланируйте дополнительные условия и параметры, необходимые для каждой политики, объединяя данные с группы внешних серверов RADIUS и правила работы с атрибутами планируется для политики.

- Разработайте план для распространения Общие политики запросов на подключение, чтобы все прокси-серверы политики сети. Создание политик, общие для нескольких прокси-серверов политики сети на один сервер политики сети и используйте команды Netsh для сервера политики сети для импорта конфигурация запросов на подключение политик и сервера на всех прокси.

## <a name="plan-nps-accounting"></a>Планирование учета сервера политики сети

При настройке сервера политики сети как RADIUS-прокси, можно настроить для выполнения RADIUS учета с помощью формата файлов журнала, файлы журнала формат, совместимый с базой данных или NPS SQL Server NPS ведения журнала.

Можно также пересылку сообщений учета для группы внешних серверов RADIUS, выполняющего учета с помощью одного из этих форматов ведения журнала.

### <a name="key-steps"></a>Основные шаги

Во время планирования учета сервера политики сети, можно использовать следующие действия.

- Определите, нужно ли прокси-сервер политики сети для выполнения службы учета или на пересылку сообщений учета группы внешних серверов RADIUS для учета.

- Планирование отключение локальный прокси-сервер политики сети, учет, если вы планируете пересылку сообщений учета на другие серверы.

- Планирование действий по настройке политики запроса подключения, если вы планируете пересылку сообщений учета на другие серверы. Если отключить локального учета для прокси-сервера политики сети, каждый политики запросов на подключение, настроенное на этой прокси-сервера должен быть переадресации сообщений учета включен и настроен соответствующим образом.

- Определите формат файла журнала, который вы хотите использовать: файлы журналов в формате IAS, файлы журнала формат, совместимый с базой данных или ведение журнала SQL Server сервера политики сети.

Настройка балансировки нагрузки для сервера политики сети как RADIUS-прокси, в разделе [NPS прокси-сервера сервера балансировки нагрузки](nps-manage-proxy-lb.md).
