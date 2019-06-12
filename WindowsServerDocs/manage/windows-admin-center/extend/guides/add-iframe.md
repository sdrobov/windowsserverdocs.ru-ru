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
ms.openlocfilehash: da3850b75a0e069f9153d3c66baef9f00b67d61c
ms.sourcegitcommit: 48bb3e5c179dc520fa879b16c9afe09e07c87629
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66452595"
---
# <a name="add-an-iframe-to-a-tool-extension"></a>Добавление iFrame в расширение средства

>Область применения. Windows Admin Center, предварительная версия Windows Admin Center

В этой статье мы добавим iFrame расширение новую, пустую средство, которое мы создали с помощью интерфейса командной строки Windows Admin Center.

## <a name="prepare-your-environment"></a>Подготовка среды ##

Если это еще не сделано, следуйте указаниям, приведенным в [разрабатывать расширения средство](../develop-tool.md) для подготовки среды и создайте новый, пустой средства расширения.

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

Таким образом, вы добавили iFrame для расширения.  Далее можно [построения и стороны нагрузки](../develop-tool.md#build-and-side-load-your-extension) расширения в Windows Admin Center, чтобы просмотреть результаты.

> [!Note]
> Параметры политики безопасности (CSP) содержимого может помешать некоторые сайты подготовки к просмотру в iFrame в Windows Admin Center. Дополнительные сведения об этом [здесь](https://content-security-policy.com/). 
