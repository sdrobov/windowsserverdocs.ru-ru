---
title: Добавление iFrame в расширение средства
description: Разработка модуля средства пакета SDK Windows Admin Center (Гонолулу проекта) - добавить iFrame в расширение средства
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 09/18/2018
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: 7cf1dcec1bc8e187b6db789c5402ca8119ca8b6c
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59850765"
---
# <a name="add-an-iframe-to-a-tool-extension"></a>Добавление iFrame в расширение средства

>Область применения. Windows Admin Center, предварительная версия Windows Admin Center

В этой статье мы добавим iFrame расширение новую, пустую средство, которое мы создали с помощью интерфейса командной строки Windows Admin Center.

## <a name="prepare-your-environment"></a>Подготовка среды ##

Если это еще не сделано, следуйте указаниям, приведенным в [разрабатывать расширения средство](..\develop-tool.md) для подготовки среды и создайте новый, пустой средства расширения.

## <a name="add-a-module-to-your-project"></a>Добавить модуль в проект ##

Добавьте новый [пустого модуля](add-module.md) в проект, к которому мы добавим iFrame на следующем шаге.  

## <a name="add-an-iframe-to-your-module"></a>Добавить iFrame в модуле ##

Теперь мы добавим iFrame на этот новый, пустой модуль, который мы только что создали.

В \src\app\, перейдите в папку модуля, а затем откройте файл ```{!module-name}.component.html```, найдено и следующие соглашения об именовании:

| Значение | Объяснение | Пример имени файла |
| ----- | ----------- | ------- |
| ```{!module-name}``` | Имя модуля (нижний регистр, пробелы заменены на тире) | ```manage-foo-works-portal.component.html``` |
    
Добавьте следующее содержимое HTML-файле:

``` html
<div>
  <iframe  style="height: 850px;" src="https://www.bing.com"></iframe>
</div>
```

Таким образом, вы добавили iFrame для расширения.  Далее можно [построения и стороны нагрузки](..\develop-tool.md#build-and-side-load-your-extension) расширения в Windows Admin Center, чтобы просмотреть результаты.

> [!Note]
> Параметры политики безопасности (CSP) содержимого может помешать некоторые сайты подготовки к просмотру в iFrame в Windows Admin Center. Дополнительные сведения об этом [здесь](https://content-security-policy.com/). 
