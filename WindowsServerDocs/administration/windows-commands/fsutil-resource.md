---
ms.assetid: b198d8ca-a5b7-430f-8911-5cbb9f50484c
title: fsutil ресурсов
ms.prod: windows-server-threshold
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
audience: IT Pro
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: b55063c3c5ea41b43573e6322b5efb36d2dad90e
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59828335"
---
# <a name="fsutil-resource"></a>fsutil ресурсов
>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows 10, Windows Server 2012 R2, Windows 8.1, Windows Server 2012, Windows 8, Windows Server 2008 R2, Windows 7, Windows 2008, Windows Vista

Создает дополнительный диспетчер ресурсов транзакционной, запускает или останавливает Transactional Resource Manager, или отображает сведения о Transactional Resource Manager и изменяет следующее поведение:

-   Будет ли по умолчанию диспетчер ресурсов транзакционной очистки метаданных в далее подключения

-   Указанный диспетчер ресурсов транзакционной для предпочтение согласованности и доступности

-   Указанный диспетчером ресурсов транзакций для доступность данных важнее согласованности

-   Характеристики из работающей Transactional Resource Manager

Примеры для использования этой команды, см. в разделе [примеры](#BKMK_examples) .

## <a name="syntax"></a>Синтаксис

```
fsutil resource [create] <RmRootPathname>
fsutil resource [info] <RmRootPathname>
fsutil resource [setautoreset] {true|false} <DefaultRmRootPathname>
fsutil resource [setavailable] <RmRootPathname>
fsutil resource [setconsistent] <RmRootPathname>
fsutil resource [setlog] [growth {<Containers> containers|<Percent> percent} <RmRootPathname>] [maxextents <Containers> <RmRootPathname>] [minextents <Containers> <RmRootPathname>] [mode {full|undo} <RmRootPathname>] [rename <RmRootPathname>] [shrink <percent> <RmRootPathname>] [size <Containers> <RmRootPathname>]
fsutil resource [start] <RmRootPathname> [<RmLogPathname> <TmLogPathname>
fsutil resource [stop] <RmRootPathname>

```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------------|---------------|
|создание|Создает дополнительный диспетчер ресурсов транзакций.|
|<RmRootPathname>|Указывает полный путь к корневой каталог диспетчер ресурсов транзакционной.|
|сведения|Сведения об указанной транзакций диспетчера ресурсов.|
|setautoreset|Указывает, будет ли по умолчанию диспетчер ресурсов транзакционной очистки метаданных транзакции на следующий подключения.<br /><br />— Организует **setautoreset** параметр **true** для указания, что диспетчер ресурсов транзакций очистит метаданных транзакции на следующий подключения, по умолчанию.<br />— Организует **setautoreset** параметр **false** для указания, что диспетчер ресурсов транзакций не будет очищать метаданных транзакции на следующий подключения, по умолчанию.|
|<DefaultRmRootPathname>|Указывает имя диска, за которым следует двоеточие.|
|setavailable|Указывает, что диспетчер ресурсов транзакционной предпочтут доступность через согласованность.|
|setconsistent|Указывает, что диспетчер ресурсов транзакционной будет предпочитать согласованности доступности.|
|setlog|Изменение характеристик из Transactional Resource Manager, на котором уже выполняется.|
|рост|Определяет, на который может возрастать журнал транзакций диспетчера ресурсов.<br /><br />Увеличение параметра может быть указан следующим образом:<br /><br />-Количество контейнеров в формате: *Контейнеры***контейнеры**<br />—   процент в формате: *Процент***процентов**|
|<containers>|Указывает объекты данных, которые используются транзакций диспетчером ресурсов.|
|maxextent|Указывает максимальное количество контейнеров для указанной транзакционной диспетчера ресурсов.|
|minextent|Указывает минимальное число контейнеров для указанной транзакционной диспетчера ресурсов.|
|mode {full&#124;undo}|Указывает, будут ли регистрироваться все транзакции ( **полный**) или только откат событий (**отменить**).|
|rename|Изменяет идентификатор GUID для диспетчер ресурсов транзакционной.|
|shrink|Указывает процент, по которому можно автоматически уменьшит журнал транзакций диспетчера ресурсов.|
|size|Указывает размер транзакций диспетчера ресурсов, как указанное число *контейнеры*.|
|start|Запускает указанный диспетчер ресурсов транзакционной.|
|stop|Останавливает указанный диспетчер ресурсов транзакционной.|

### <a name="BKMK_examples"></a>Примеры
В журнале для диспетчер ресурсов транзакционной, идентифицируемому c:\test, требуется автоматическое увеличение размера пять контейнеров, введите:

```
fsutil resource setlog growth 5 containers c:test
```

В журнале для диспетчер ресурсов транзакционной, идентифицируемому c:\test, требуется автоматическое увеличение размера двух процентов, введите:

```
fsutil resource setlog growth 2 percent c:test
```

Чтобы указать, что по умолчанию диспетчер ресурсов транзакционной очистит метаданных транзакции на следующий подключения на диске C, введите следующую команду:

```
fsutil resource setautoreset true c:\  
```

### <a name="additional-references"></a>Дополнительная справка
[Ключ синтаксиса командной строки](Command-Line-Syntax-Key.md)

[fsutil](Fsutil.md)

[Транзакционная NTFS](https://go.microsoft.com/fwlink/?LinkID=165402)


