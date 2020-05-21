---
title: PowerShell_ise
description: Справочный раздел по * * * *-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 32c41b5b-a210-47d9-bd8c-91eb9830b4f0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8529e19e30b72c9b9c8f8c30e1ca39c5e8f1f40e
ms.sourcegitcommit: bf887504703337f8ad685d778124f65fe8c3dc13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2020
ms.locfileid: "83436529"
---
# <a name="powershell_ise"></a>PowerShell_ise



Интегрированная среда сценариев (ISE) Windows PowerShell — это графическое приложение, позволяющее читать, писать, выполнять, отлаживать и тестировать сценарии и модули в среде с графическим интерфейсом. Основные функции, такие как IntelliSense, команда "показывать-Command", фрагменты кода, заполнение нажатием клавиши TAB, выделение синтаксиса, визуальная отладка и контекстная справка, обеспечивают широкие возможности работы с скриптами.

Средство **PowerShell_ISE. exe** запускает сеанс интегрированной среды сценариев Windows PowerShell. При использовании **PowerShell_ISE. exe**можно использовать его необязательные параметры для открытия файлов в интегрированной среде сценариев Windows PowerShell или для запуска сеанса интегрированной среды сценариев Windows PowerShell без профиля или с многопоточным апартаментом.

**PowerShell_ISE. exe** был впервые появился в windows PowerShell 2,0 и значительно увеличился в windows PowerShell 3,0.

## <a name="using-powershell_iseexe"></a>Использование PowerShell_ISE. exe

**PowerShell_ISE. exe** можно использовать для запуска и завершения сеанса Windows PowerShell следующим образом:
- Чтобы запустить сеанс интегрированной среды сценариев Windows PowerShell, в окне командной строки в Windows PowerShell или в меню "Пуск" введите:
  ```
  PowerShell_Ise
  ```
- Чтобы открыть скрипт (PS1), модуль скрипта (PSM1), манифест модуля (. PSD1), XML-файл или любой другой поддерживаемый файл в интегрированной среде сценариев Windows PowerShell, используйте следующий формат команды:
  ```
  PowerShell_Ise <FilePath>
  ```
  В Windows PowerShell 3,0 можно использовать необязательный параметр **File** , как показано ниже.
  ```
  PowerShell_Ise -File <FilePath>
  ```
- Чтобы запустить сеанс интегрированной среды сценариев Windows PowerShell без профилей Windows PowerShell, используйте параметр- **Profile** . (Параметр- **Profile** появился в Windows PowerShell 3,0.)
  ```
  PowerShell_Ise -NoProfile
  ```
- Чтобы просмотреть файл справки **PowerShell_ISE. exe** в окне командной строки, используйте следующий формат команды:
  ```
  PowerShell_Ise -help, -?, /?
  ```
  Полный список параметров командной строки **PowerShell_ISE. exe** см. в разделе [about_PowerShell_Ise. exe](https://go.microsoft.com/fwlink/?LinkId=256512).

## <a name="start-windows-powershell-ise-in-other-ways"></a>Запуск интегрированной среды сценариев Windows PowerShell другими способами

Дополнительные сведения о других способах запуска интегрированной среды сценариев Windows PowerShell см. в разделе [Запуск Windows PowerShell](https://go.microsoft.com/fwlink/?LinkID=135259).

## <a name="remarks"></a>Комментарии

Windows PowerShell выполняется в варианте установки Server Core в операционных системах Windows Server. Однако, поскольку интегрированная среда сценариев Windows PowerShell требует графического пользовательского интерфейса, она не выполняется в установках Server Core.

## <a name="additional-references"></a>Дополнительные ссылки

[about_PowerShell_Ise. exe](https://go.microsoft.com/fwlink/?LinkId=256512) 
 [about_PowerShell. exe](https://go.microsoft.com/fwlink/?LinkID=113439) 
 [Windows PowerShell](https://go.microsoft.com/fwlink/?LinkID=107116) 
 [Создание сценариев с помощью Windows PowerShell](https://technet.microsoft.com/scriptcenter/dd742419) См. также