---
title: Публикация расширения для Windows Admin Center
description: Публикация расширения для Windows Admin Center (Гонолулу проекта)
ms.technology: manage
ms.topic: article
author: daniellee-msft
ms.author: jol
ms.date: 09/18/2018
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: 762bd4613fa8ad6cdfb5b44745a7ce78b331499d
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59820425"
---
# <a name="publishing-extensions"></a>Публикация расширений

>Область применения. Windows Admin Center, предварительная версия Windows Admin Center

После разработки расширения, необходимо опубликовать его и сделать его доступным для других пользователей, чтобы проверять или использовать. В зависимости от вашей аудитории и цели публикации существуют несколько вариантов, которые мы добавим ниже, а также шаги и требования для публикации.

## <a name="publishing-options"></a>Параметры публикации

Существует три основных варианта для источников пакетов можно настроить, поддерживаемых Windows Admin Center:
* Корпорации Майкрософт открытый Windows Admin Center веб-канал NuGet
* Собственный закрытый веб-канал NuGet
* Локальный или сетевой общей папке

### <a name="publishing-to-the-windows-admin-center-extension-feed"></a>Публикация в Windows Admin Center расширение веб-канала

По умолчанию Windows Admin Center подключен к NuGet веб-канал, обслуживаемых группой Windows Admin Center продукта в корпорации Microsoft. Ранних предварительных версий новые расширения, разработанный Майкрософт, возможно, опубликованные на веб-канал, так и доступные пользователям Windows Admin Center. Сторонним разработчикам, планирование для построения и выпускать публично расширения может также [запрос](#publishing-your-extension-to-the-windows-admin-center-feed) для публикации на веб-канал.

### <a name="publishing-to-a-different-nuget-feed"></a>Публикация в разных NuGet веб-канала

Можно также создать свои собственные веб-канал для публикации расширений с помощью одной из многих NuGet [различные варианты настройки частного источника или с помощью NuGet, в котором размещена служба](https://docs.microsoft.com/nuget/hosting-packages/overview). Веб-канал NuGet должен поддерживать NuGet v2 API. Поскольку Windows Admin Center в настоящее время не поддерживает проверку подлинности веб-канала, веб-канала должен разрешать доступ для чтения к любой пользователь.

### <a name="publishing-to-a-file-share"></a>Публикация в общую папку

Чтобы ограничить доступ вашего расширения, в рамках организации или ограниченной группе пользователей, можно использовать файловый ресурс SMB как расширение веб-канала. В этом случае разрешения и общей папке для файла будет применяться для предоставления доступа к веб-канала.

## <a name="preparing-your-extension-for-release"></a>Подготовка к выпуску расширения

Убедитесь, что чтение и рассмотрим в следующих разделах разработки:

- [Управлять видимостью ваше средство](guides/dynamic-tool-display.md)
- [Строки и локализации](guides/strings-localization.md)

### <a name="consider-releasing-as-a-preview-release"></a>Выпустить в виде предварительного выпуска

Если вы выпускаете предварительную версию расширения для ознакомительных целей, мы рекомендуем вам:

- Добавить «(Предварительная версия)» в конец заголовка свое расширение в файл nuspec
- Объясните, ограничения описание вашего расширения в файле nuspec

## <a name="creating-an-extension-package"></a>Создание пакета расширения

Windows Admin Center использует пакеты NuGet и веб-каналы для распространения и загрузки расширений.  Чтобы пакет к поставке необходимо создать пакет NuGet, содержащий ваши подключаемых модулей и расширений.  Один пакет может содержать расширения пользовательского интерфейса как подключаемого модуля шлюза, а следующий раздел поможет выполнить процесс.

### <a name="1-build-your-extension"></a>1. Создание расширения

Как только вы будете готовы упаковать расширение, создайте новый каталог в файловой системе, откройте консоль и компакт-диска в него.  Это будет корневой каталог, который будет использоваться для хранения всех nuspec и содержимое каталогов, составляющих нашего пакета.  Мы будет ссылаться на эту папку как «Пакет NuGet» в течение этого документа.

#### <a name="ui-extensions"></a>UI Extensions

Чтобы начать процесс сбора все содержимое, необходимое для расширения пользовательского интерфейса, запустите «gulp сборки» на ваше средство и убедитесь, что сборка выполнена успешно.  Этот процесс пакетов, все компоненты в папку с именем «объединить», расположенный в корневом каталоге вашего расширения (на том же уровне каталог src).  Скопируйте этот каталог и все его в содержимое в папку «Пакет NuGet».

#### <a name="gateway-plugins"></a>Подключаемые модули шлюза

Использование инфраструктуры сборки (это может быть сложнее, чем открыть Visual Studio и нажать кнопку сборки), компиляция и сборка подключаемого модуля.  Откройте выходном каталоге сборки и скопируйте Dll(s), представляющих подключаемого модуля и поместить их в новую папку внутри каталог «Пакет NuGet» с именем «пакет».  Необходимо скопировать dll FeatureInterface, просто Dll(s), которые представляют код.

### <a name="2-create-the-nuspec-file"></a>2. Создание файла nuspec

Чтобы создать пакет NuGet, необходимо сначала создать nuspec-файл. Nuspec-файл является XML-манифест, содержащий метаданные пакета NuGet. Этот манифест используется для предоставления информации о потребителях и для сборки пакета.  Поместите этот файл в корневой папке «Пакет NuGet».

Ниже приведен пример файла nuspec и список необходимых или рекомендованных свойств. Полную схему, см. в разделе [Справочник по файлу nuspec](https://docs.microsoft.com/nuget/reference/nuspec). Сохраните nuspec-файл в корневую папку проекта с именем файла по своему усмотрению.

> [!IMPORTANT]
> ```<id>``` Значение в файле nuspec должно соответствовать ```"name"``` значение в вашем проекте ```manifest.json``` файл, в противном случае опубликованного расширения не будет успешно загрузить в Windows Admin Center.

```xml
<?xml version="1.0" encoding="utf-8"?>
<package xmlns="http://schemas.microsoft.com/packaging/2011/08/nuspec.xsd">
  <metadata>
    <packageTypes>
      <packageType name="WindowsAdminCenterExtension" />
    </packageTypes>  
    <id>contoso.project.extension</id>
    <version>1.0.0</version>
    <title>Contoso Hello Extension</title>
    <authors>Contoso</authors>
    <owners>Contoso</owners>
    <requireLicenseAcceptance>false</requireLicenseAcceptance>
    <projectUrl>https://msft-sme.myget.org/feed/windows-admin-center-feed/package/nuget/contoso.sme.hello-extension</projectUrl>
    <licenseUrl>http://YourLicenseLink</licenseUrl>
    <iconUrl>http://YourLogoLink</iconUrl>
    <description>Hello World extension by Contoso</description>
    <copyright>(c) Contoso. All rights reserved.</copyright> 
    <tags></tags>
  </metadata>
  <files>
    <file src="bundle\**\*.*" target="ux" />
    <file src="package\**\*.*" target="gateway" />
  </files>
</package>
```

#### <a name="required-or-recommended-properties"></a>Обязательных или рекомендуемых свойства

| Имя свойства | Требуется или рекомендуется | Описание |
| ---- | ---- | ---- |
| Тип корпуса | Обязательно | Используйте «WindowsAdminCenterExtension», который является типом пакета NuGet, определенные для расширения Windows Admin Center. |
| id | Обязательно | Уникальный идентификатор пакета в потоке данных. Это значение должно совпадать со значением «name» в файле manifest.json вашего проекта.  См. в разделе [Выбор уникального идентификатора пакета](https://docs.microsoft.com/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number) рекомендации. |
| title | Необходимые для публикации Windows Admin Center веб-канала | Понятное имя для пакета, который отображается в Windows Admin Center диспетчера расширений. |
| version | Обязательно | Версия расширения. С помощью [семантическое Версионирование (SemVer соглашение)](http://semver.org/spec/v1.0.0.html) рекомендуется, но не является обязательным. |
| Авторы | Обязательно | Если публикация от имени вашей организации, используйте имя своей организации. |
| description | Обязательно | Введите описание расширения функциональности. |
| IconUrl | Рекомендуется при публикации в Windows Admin Center веб-канала | URL-адрес для значка, отображаемого в диспетчере расширений. |
| ProjectUrl | Необходимые для публикации Windows Admin Center веб-канала | URL-адрес веб-сайт вашего расширения. Если у вас отдельный веб-сайт, используйте URL-адрес веб-страницы пакета на веб-канал NuGet. |
| LicenseUrl | Необходимые для публикации Windows Admin Center веб-канала | URL-адрес вашего расширения лицензионное соглашение. |
| файлы | Обязательно | Эти два параметра, настроить структуру папок, которая ожидает Windows Admin Center для расширения пользовательского интерфейса и подключаемые модули шлюза. |

### <a name="3-build-the-extension-nuget-package"></a>3. Сборки пакета расширения NuGet

С помощью файла nuspec, созданную ранее, теперь создается файл .nupkg пакета NuGet, которую можно передать и опубликовать в канале NuGet.

1. Загрузите средство интерфейса командной строки nuget.exe из [веб-сайт средства клиента NuGet](https://docs.microsoft.com/nuget/install-nuget-client-tools).
2. Запустите «nuget.exe пакет [имя файла файлу nuspec]» для создания файла nupkg.

### <a name="4-signing-your-extension-nuget-package"></a>4. Подписывание пакета NuGet расширений

Все DLL-файлы, включенные в расширения должен быть подписан с помощью сертификата из доверенного центра сертификации. По умолчанию без знака DLL-файлов будет заблокирован выполняемой, когда Windows Admin Center выполняется в рабочем режиме.

Также настоятельно рекомендуется подписать пакет NuGet для обеспечения целостности пакета расширений, что это не обязательный шаг.

### <a name="5-test-your-extension-nuget-package"></a>5. Тестирование пакета NuGet расширений

Для тестирования пакета расширений готов! Отправка файла nupkg на веб-канал NuGet или скопируйте его в общую папку. Чтобы просмотреть и скачать пакеты из другой веб-канал или общую папку, необходимо [измените конфигурацию веб-канала](../configure/using-extensions.md#installing-extensions-from-a-different-feed) в веб-канал NuGet или файлового ресурса. При тестировании, убедитесь, что свойства правильно отображаются в диспетчере расширений, и можно успешно установить и удалить расширение.

## <a name="publishing-your-extension-to-the-windows-admin-center-feed"></a>Публикация расширения в Windows Admin Center веб-канала

Публикуя Windows Admin Center веб-канал, вы можете предоставить расширение любому пользователю Windows Admin Center. Так как пакет SDK Windows Admin Center находится на стадии предварительной версии, мы бы хотели тесного сотрудничества с вами для устранения проблем разработки, убедитесь, что вы сможете продукта и опыту других и пользователям.

Перед тем как освободить первоначальной версии расширения, рекомендуется отправить запрос проверки расширения в корпорацию Майкрософт по крайней мере 2 – 3 недель до выпуска, чтобы убедиться, что у нас есть достаточно времени для просмотра и позволяет вносить изменения для расширения, при необходимости. Когда расширение будет готово к публикации, вам потребуется отправить нам для просмотра, и если утверждено, мы опубликуем его в веб-канал для вас.

После этого Если вы хотите выпустить обновление вашего расширения, необходимо будет отправить другой запрос на проверку. Хотя в зависимости от область изменений, время обработки для проверки обновления обычно должны быть короче.

### <a name="submit-an-extension-review-request-to-microsoft"></a>Отправка запроса проверки расширения в корпорацию Майкрософт

Чтобы отправить запрос расширения проверки, введите следующие сведения и отправить как сообщение электронной почты для [ wacextensionrequest@microsoft.com ](mailto:wacextensionrequest@microsoft.com?subject=Windows%20Admin%20Center%20Extension%20Review%20Request). Мы ответит на ваш адрес электронной почты в течение недели.

```
Windows Admin Center Extension Review Request
1. Name and email address of extension owner/developer (up to 3 users). If you will be releasing an extension on behalf of your company, provide your company email address.
2. Company name (Only required if you are releasing an extension on behalf of your company):
3. Extension name:
4. Release target date (estimate):
5. For new extension submission - Extension description (early design wire frames, screen mockups or product screenshots are highly recommended):
6. For extension update review – Description of changes (include product screenshots if UI has been significantly changed):
```

### <a name="submit-your-extension-package-for-review-and-publishing"></a>Отправка пакета расширений для просмотра и публикации

Убедитесь, что, следуйте инструкциям выше касательно параметра [Создание пакета расширения](#creating-an-extension-package) файла nuspec определена правильно, и файлы подписываются. Мы также рекомендуем, что у вас есть веб-сайт проекта, включая следующие:

- Подробное описание вашего расширения, включая снимки экрана или видео
- Функция адрес или веб-сайт по электронной почте для получения комментарии или вопросы

Когда будете готовы опубликовать расширение, напишите нам по адресу [ wacextensionrequest@microsoft.com ](mailto:wacextensionrequest@microsoft.com?subject=Windows%20Admin%20Center%20Extension%20Package%20Review) и представлены инструкции о том, как отправить нам пакета расширений. Как только мы получили ваш пакет, мы и рассмотрим случае утверждения опубликовать Windows Admin Center веб-канала.