---
title: PowerShell
description: Узнайте, как открыть консоль PowerShell из командной строки.
ms.custom: na
ms.prod: windows-server-threshold
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
ms.openlocfilehash: 1e2ccf6187e4480f94b30632b6f8f9f092052541
ms.sourcegitcommit: 6ef4986391607bb28593852d06cc6645e548a4b3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66811076"
---
# <a name="powershell"></a>PowerShell

Windows PowerShell — это ориентированная на задачи оболочка командной строки и язык сценариев, предназначенный специально для системного администрирования. Созданная на основе .NET Framework служба Windows PowerShell помогает ИТ-специалистам и опытным пользователям в управлении и автоматизации администрирования операционной системы Windows, а также приложений, работающих под управлением Windows.

**PowerShell.exe** средство командной строки запускает сеанс Windows PowerShell в окне командной строки. При использовании **PowerShell.exe**, своих необязательных параметров можно использовать для настройки сеанса. Например можно начать сеанс, который использует политику выполнения конкретного задания, или одно, исключающее профиль Windows PowerShell. В противном случае сеанс совпадает с любой сеанс, который запускается в консоли Windows PowerShell.

## <a name="using-powershellexe"></a>С помощью PowerShell.exe

Можно использовать **PowerShell.exe** средство командной строки для запуска сеанса Windows PowerShell в окне командной строки.

- Чтобы запустить сеанс Windows PowerShell в окне командной строки, введите `PowerShell`. Объект **PS** добавляется префикс в командную строку, чтобы указать, что вы находитесь в сеансе Windows PowerShell.

- Чтобы запустить сеанс с политикой выполнения конкретного задания, используйте **ExecutionPolicy** параметра.

    ```
    PowerShell.exe -ExecutionPolicy Restricted
    ```

- Чтобы запустить сеанс Windows PowerShell без профили Windows PowerShell, используйте **NoProfile** параметра.

    ```
    PowerShell.exe -NoProfile
    ```
  
- Чтобы запустить сеанс, используйте **ExecutionPolicy** параметра.

    ```
    PowerShell.exe -ExecutionPolicy Restricted
    ```
  
- Чтобы просмотреть файл справки PowerShell.exe, используйте следующий формат команды.  
    
    ```
    PowerShell.exe -help, -?, /?
    ```

- Чтобы завершить сеанс Windows PowerShell в окне командной строки, введите `exit`. Возвращает типичный командной строки.

Полный список **PowerShell.exe** параметров командной строки, см. в разделе [about_PowerShell.Exe](https://go.microsoft.com/fwlink/?LinkID=113439).

## <a name="other-ways-to-start-windows-powershell"></a>Другие способы запуска Windows PowerShell

Сведения о других способах запуска Windows PowerShell, см. в разделе [запуск Windows PowerShell](https://go.microsoft.com/fwlink/?LinkID=135259).

## <a name="remarks"></a>Примечания

Windows PowerShell работает в варианте установки основных серверных компонентов операционных систем Windows Server. Тем не менее, функции, требующие графического пользовательского интерфейса такие как [Windows PowerShell сценарии среды Интегрированной](https://technet.microsoft.com/library/hh849182)и [Out-GridView](https://go.microsoft.com/fwlink/?LinkID=113364) и [Show-Command](https://go.microsoft.com/fwlink/?LinkID=217448)командлеты, не работают при установке ядра сервера.

## <a name="additional-references"></a>Дополнительная справка

[about_PowerShell.exe](https://go.microsoft.com/fwlink/?LinkID=113439)
[about_PowerShell_Ise.exe](https://go.microsoft.com/fwlink/?LinkId=256512)
[Windows PowerShell](https://go.microsoft.com/fwlink/?LinkID=107116)
[Создание сценариев с помощью Windows PowerShell](https://technet.microsoft.com/scriptcenter/dd742419) см. также