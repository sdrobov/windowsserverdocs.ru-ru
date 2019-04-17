---
title: Добавьте iFrame расширения средства
description: Разработка расширения средства Windows Admin Center SDK (проект Honolulu) — добавить iFrame расширения средства
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 09/18/2018
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: 7b4a7b688e4b2d9f52e44395c19211b91b964578
ms.sourcegitcommit: be0144eb59daf3269bebea93cb1c467d67e2d2f1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/20/2018
ms.locfileid: "4080931"
---
# Добавьте iFrame расширения средства

>Относится к: Windows Admin Center, ознакомительная версия Windows Admin Center

В этой статье мы добавим iFrame расширение новый, пустой средства, которые мы создали с помощью Windows Admin Center CLI.

## Подготовка среды ##

Если вы еще не сделали этого, следуйте инструкциям в [разработке расширения средства](..\develop-tool.md) Подготовка среды и создать новый, пустой средство расширение.

## Добавление модуля в проект ##

Добавьте новый [пустой модуль](add-module.md) в свой проект, к которому мы добавим iFrame на следующем шаге.  

## Добавьте iFrame модуля ##

Теперь добавим iFrame, новый, пустой модуль, который мы только что создали.

В \src\app\, перейдите в папку модуля, а затем откройте файл ```{!module-name}.component.html```, содержащийся в следующее соглашение об именовании:

| Значение | Объяснение | Пример имени файла |
| ----- | ----------- | ------- |
| ```{!module-name}``` | Имя модуля (нижний регистр, пробелы заменены на тире) | ```manage-foo-works-portal.component.html``` |
    
На HTML-файл добавьте следующее содержимое:

``` html
<div>
  <iframe  style="height: 850px;" src="https://www.bing.com"></iframe>
</div>
```

Все готово, вы добавили iFrame в расширении.  Затем вы можете [Создание и загрузка](..\develop-tool.md#build-and-side-load-your-extension) расширения в Windows Admin Center, чтобы увидеть результат.
