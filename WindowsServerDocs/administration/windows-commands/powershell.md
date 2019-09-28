---
title: PowerShell
description: Узнайте, как открыть консоль PowerShell из командной строки.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 694fc970-0b6c-4046-b1b5-7eb1a0d26609
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: 2c43c71fce9bb25efcf3f03284160d5534475a8a
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71372199"
---
# <a name="powershell"></a>PowerShell

Windows PowerShell — это оболочка командной строки на основе задач и язык сценариев, разработанный специально для администрирования системы. Созданная на основе .NET Framework служба Windows PowerShell помогает ИТ-специалистам и опытным пользователям в управлении и автоматизации администрирования операционной системы Windows, а также приложений, работающих под управлением Windows.

Программа командной строки **PowerShell. exe** запускает сеанс Windows PowerShell из окна командной строки. При использовании **PowerShell. exe**можно использовать его необязательные параметры для настройки сеанса. Например, можно запустить сеанс, в котором используется конкретная политика выполнения или одна из которых исключает профиль Windows PowerShell. В противном случае сеанс будет таким же, как и любой сеанс, запущенный в консоли Windows PowerShell.

## <a name="using-powershellexe"></a>Использование PowerShell. exe

Можно использовать программу командной строки **PowerShell. exe** для запуска сеанса Windows PowerShell в командной строке.

- Чтобы запустить сеанс Windows PowerShell в окне командной строки, введите `PowerShell`. В командную строку добавляется префикс **PS** , указывающий, что вы используете сеанс Windows PowerShell.

- Чтобы запустить сеанс с определенной политикой выполнения, используйте параметр **ExecutionPolicy** .

    ```
    PowerShell.exe -ExecutionPolicy Restricted
    ```

- Чтобы запустить сеанс Windows PowerShell без профилей Windows PowerShell, используйте параметр- **Profile** .

    ```
    PowerShell.exe -NoProfile
    ```
  
- Чтобы начать сеанс, используйте параметр **ExecutionPolicy** .

    ```
    PowerShell.exe -ExecutionPolicy Restricted
    ```
  
- Чтобы просмотреть файл справки PowerShell. exe, используйте следующий формат команды:  
    
    ```
    PowerShell.exe -help, -?, /?
    ```

- Чтобы завершить сеанс Windows PowerShell в окне командной строки, введите `exit`. Типичная Командная строка возвращает.

Полный список параметров командной строки **PowerShell. exe** см. в разделе [about_PowerShell. exe](https://go.microsoft.com/fwlink/?LinkID=113439).

## <a name="other-ways-to-start-windows-powershell"></a>Другие способы запуска Windows PowerShell

Дополнительные сведения о других способах запуска Windows PowerShell см. в разделе [Запуск Windows PowerShell](https://go.microsoft.com/fwlink/?LinkID=135259).

## <a name="remarks"></a>Примечания

Windows PowerShell выполняется в варианте установки Server Core в операционных системах Windows Server. Тем не менее функции, требующие графического пользовательского интерфейса, такие как [Интегрированная среда сценариев Windows PowerShell (ISE)](https://technet.microsoft.com/library/hh849182), и командлеты [Out-GridView](https://go.microsoft.com/fwlink/?LinkID=113364) и [Показывать-Command](https://go.microsoft.com/fwlink/?LinkID=217448) , не выполняются в установках Server Core.

## <a name="additional-references"></a>Дополнительная справка

[about_PowerShell. exe](https://go.microsoft.com/fwlink/?LinkID=113439)
[about_PowerShell_Ise. exe](https://go.microsoft.com/fwlink/?LinkId=256512)
[Windows PowerShell](https://go.microsoft.com/fwlink/?LinkID=107116)
[написание сценариев с помощью Windows PowerShell](https://technet.microsoft.com/scriptcenter/dd742419) см. также