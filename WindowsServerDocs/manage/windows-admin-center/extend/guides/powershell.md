---
title: Использование PowerShell в расширении
description: С помощью PowerShell в расширении Windows Admin Center SDK (Гонолулу проекта)
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 06/18/2018
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: ae5004104150c510a56c06161c9280e029968298
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59867605"
---
# <a name="using-powershell-in-your-extension"></a>Использование PowerShell в расширении #

>Область применения. Windows Admin Center, предварительная версия Windows Admin Center

Перейдем к более подробное руководство расширения пакета SDK для Windows Admin Center — давайте поговорим о добавлении команды PowerShell в модуле.

## <a name="powershell-in-typescript"></a>PowerShell в TypeScript ##

Процесс сборки gulp содержит создать действие будет выполняться любые «.ps1», помещается в папку «/ src/ресурсы/scripts» и при их создании в класс «сценариев powershell» в папке «/ src/создан».

>[!NOTE] 
> Не обновлять вручную «powershell-scripts.ts», ни файлов «strings.ts». Любые вносимые изменения будут перезаписаны на Далее формирования.

### <a name="adding-your-own-powershell-script"></a>Добавление собственный сценарий PowerShell ##

Мы добавим Дополнительные сведения о добавлении собственный сценарий PowerShell в ближайшее время.

### <a name="managing-powershell-sessions"></a>Управление сеансами PowerShell ###

При работе с PowerShell в Windows Admin Center, сеансы являются обязательным компонентом процесс выполнения скрипта. Для запуска сценариев на удаленных серверах, управляемых PowerShell использует пространства выполнения. Windows Admin Center создает оболочку в объекте PowerShellSession для управления временем существования и включить повторное использование пространства выполнения для выполнения последовательного сценариев создания пространства выполнения и управления ими.

Каждый компонент необходимо создать ссылку на объект сеанса, созданный с помощью класса AppContextService, с помощью трех параметров:
<!-- I don't 100% get this part - it looks like you're adding 3 arguments - nodeName, <session key>, and <PowerShellSessionRequestOptions>. I got that from looking at the examples, not the text. We need to rework those paras explaining. -->
``` ts
this.psSession = this.appContextService.powerShell.createSession(this.appContextService.activeConnection.nodeName);
```

Предоставляя имени узла, чтобы метод createSession, новый сеанс PowerShell создается, использовать и затем немедленно уничтожается после завершения вызова PowerShell. Эта функция хорошо подходит для одноразовых вызовов, но многократного использования может повлиять на производительность. Сеанс принимает примерно 1 секунда для создания, поэтому постоянно повторное использование сеансов может привести к снижению скорости.

``` ts
this.psSession = this.appContextService.powerShell.createSession(this.appContextService.activeConnection.nodeName, '<session key>');
```

Первым необязательным параметром является \<сеансовый ключ\> параметра. Это создает сеанс с ключом, которую можно искать и повторно, даже через компоненты (то есть Component1 может создать сеанс с ключом «ROCKS для малых и средних Предприятий», а Component2 можно использовать в этом же сеансе).  

``` ts
this.psSession = this.appContextService.powerShell.createSession(this.appContextService.activeConnection.nodeName, '<session key>', <PowerShellSessionRequestOptions>);
```
<!-- The second optional parameter is \<PowerShellSessionRequestOptions\> that does ... ? -->
### <a name="common-patterns"></a>Общие шаблоны ###

В большинстве случаев создания сеанса с ключом в **ngOnInit** метод, а затем уничтожьте ее в **ngOnDestroy**. Следуйте этому шаблону, при наличии нескольких сценариев PowerShell в компоненте, но соответствующий сеанс не является общей во всех компонентах.

Для получения наилучших результатов убедитесь, созданием сеанса осуществляется внутри компонентов, а не службы — это помогает обеспечить, время существования и очистки, которые могут управляться должным образом.