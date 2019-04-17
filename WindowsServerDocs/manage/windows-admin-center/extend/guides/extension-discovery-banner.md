---
title: Включение обнаружения баннер расширения
description: Включение обнаружения баннер расширения
ms.technology: manage
ms.topic: article
author: daniellee-msft
ms.author: jol
ms.date: 03/08/2019
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: 389acba6d1fe6f65320bd780c9fde6469b387e0b
ms.sourcegitcommit: e558dda2774345e9ad17ff04b759f68c59d88139
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2019
ms.locfileid: "9262964"
---
# Включение обнаружения баннер расширения #

>Относится к: Windows Admin Center, ознакомительная версия Windows Admin Center

Новая функция в 1903 года ознакомительная версия Windows Admin Center — баннер обнаружения расширения. Эта функция позволяет расширения для объявления сервера изготовителя и модели, которые они поддерживают, и при подключении пользователя к серверу или кластеру, для которых доступен расширения, объявления на уведомление будет отображаться легко установить расширение. Разработчикам расширений не смогут получить дополнительные видимость для расширения и пользователи не смогут легко найти дополнительные возможности управления для своих серверов.

![Расширение обнаружения баннеров](../../media/extend-guides-extension-discovery-banner/extension-discovery-banner.png)

## Как работает баннер обнаружения расширения ##

При запуске Windows Admin Center будет подключаться к веб-каналы, зарегистрированных расширения и получить метаданные для пакетов, доступные расширения. Затем при подключении пользователя к серверу или кластеру в Windows Admin Center, запрашивается изготовитель оборудования сервера и модель для отображения в средстве Обзор. Если мы обнаружим расширением, которое объявляет, что он поддерживает текущего сервера в изготовителя и модели, мы отобразим баннер, чтобы показать пользователю. Щелкните ссылку «Настройка теперь» перенаправления пользователя в "диспетчере расширений" где они могут установить расширение.

## Как реализовать баннер обнаружения расширения ##

Метаданные «теги» в файле .nuspec используется для объявления какой производителю оборудования и/или моделирует поддерживает ваша расширения. Теги разделяются пробелами и можно добавить производителем и метки моделью либо оба объявить поддерживаемых изготовителя и модели. Этот формат тега ``"[value type]_[value condition]"`` там, где [тип значения] либо «изготовитель» или «Модель» (с учетом регистра) и [значение условие] на [соответствие регулярному выражению Javascript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions) определения изготовителя или строка модели, а также [тип значения] и [значение условие], разделяются символом подчеркивания. Эта строка затем кодируются с помощью URI кодирования и добавить строку метаданных .nuspec «теги».

### Пример. ###

Предположим, я разработали расширением, которое поддерживает серверы компанией под названием Contoso Inc. с моделью имя R3xx и R4xx.

1. Тег для изготовителя бы ``"Manufacturer_/Contoso Inc./"``. Тег для моделей может быть ``"Model_/^R[34][0-9]{2}$/"``. В зависимости от того, насколько строго необходимо определить соответствующее условие будет различные способы для определения регулярного выражения. Теги изготовителя и модели также можно разделить на несколько тегов, например, метки моделью также может быть ``"Model_/R3../ Model_/R4../"``.
2. Вы можете протестировать регулярного выражения с помощью консоли по средствам разработчика веб-браузера. В Edge или Chrome нажмите F12, чтобы открыть окно по средствам разработчика, и на вкладке «консоль» введите следующие и нажатия:

```javascript
var regex = /^R[34][0-9]{2}$/
```

Затем при вводе и выполните следующую команду, он возвращает значение «true».

```javascript
regex.test('R300')
```

И если вы выполните следующую команду, будет возвращено значение «false».

```javascript
regex.test('R500')
```

3. Проверив соответствие регулярному выражению формат, можно зашифровать его на консоли по средствам разработчика, используя следующий метод Javascript:

```javascript
encodeURI(/^R[34][0-9]{2}$/)
```

Последний формат строки тег для добавления в файл .nuspec будет:

```
<tags>Manufacturer_/Contoso%20Inc./ Model_/%5ER%5B34%5D%5B0-9%5D%7B2%7D$/</tags>
```

> [!Tip]
> Мы понимаем, возможно, изготовитель оборудования очень широкий спектр модели имена которых некоторые может быть реализована поддержка а некоторые — нет. Имейте в виду, что эта функция предназначен для упрощения **обнаружения** расширения, но у него не будет полностью актуальные инвентарные всех моделей. Вы можете определить регулярного выражения будет проще выражение, соответствующее подмножество моделей. Пользователь может не см. в разделе баннер обнаружения при первом подключении к модели сервера соответствует условие, но рано или поздно они будут подключаться к другому серверу, и будет обнаруживать и установите расширение. Вы также можете попробовать Определение простой регулярное выражение, которое соответствует только имя изготовителя. В некоторых случаях расширения могут не поддерживать фактически конкретной модели, но можно использовать [динамичным отображения компонентов](./dynamic-tool-display.md) для определения пользовательский сценарий PowerShell для проверки поддержку модели и отображать только при наличии расширения, или предоставить ограниченные в расширении для модели, которые не поддерживают все возможности функции.