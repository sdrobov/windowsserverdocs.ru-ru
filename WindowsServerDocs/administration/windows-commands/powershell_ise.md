---
title: PowerShell_ise
description: Справочная статья по команде PowerShell_ise, которая запускает сеанс интегрированной среды сценариев (ISE) Windows PowerShell.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 32c41b5b-a210-47d9-bd8c-91eb9830b4f0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3f983ea5b8464748d86264108a2ee8660ca0e3f2
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85926058"
---
# <a name="powershell_ise"></a>PowerShell_ise

Интегрированная среда сценариев (ISE) Windows PowerShell — это графическое приложение, позволяющее читать, писать, выполнять, отлаживать и тестировать сценарии и модули в среде с графическим интерфейсом. Основные функции, такие как IntelliSense, команда "показывать-Command", фрагменты кода, заполнение нажатием клавиши TAB, выделение синтаксиса, визуальная отладка и контекстная справка, обеспечивают широкие возможности работы с скриптами.

## <a name="using-powershellexe"></a>Использование PowerShell.exe

Средство **PowerShell_ISE.exe** запускает сеанс интегрированной среды сценариев Windows PowerShell. При использовании **PowerShell_ISE.exe**можно использовать его необязательные параметры, чтобы открыть файлы в интегрированной среде сценариев Windows PowerShell или запустить сеанс интегрированной среды сценариев Windows PowerShell без профиля или с многопоточным апартаментом.

- Чтобы запустить сеанс интегрированной среды сценариев Windows PowerShell в окне командной строки, в Windows PowerShell или в меню " **Пуск** ", введите:

  ```powershell
  PowerShell_Ise.exe
  ```

- Чтобы открыть скрипт (PS1), модуль скрипта (PSM1), манифест модуля (. PSD1), XML-файл или любой другой поддерживаемый файл в интегрированной среде сценариев Windows PowerShell, введите:

  ```powershell
  PowerShell_Ise.exe <filepath>
  ```

  В Windows PowerShell 3,0 можно использовать необязательный параметр **File** , как показано ниже.

  ```powershell
  PowerShell_Ise.exe -file <filepath>
  ```

- Чтобы запустить сеанс интегрированной среды сценариев Windows PowerShell без профилей Windows PowerShell, используйте параметр- **Profile** . (Параметр- **Profile** появился в Windows PowerShell 3,0.) введите:

  ```powershell
  PowerShell_Ise.exe -NoProfile
  ```

- Чтобы просмотреть файл справки PowerShell_ISE.exe, введите:

    ```powershell
    PowerShell_Ise.exe -help
    PowerShell_Ise.exe -?
    PowerShell_Ise.exe /?
    ```

### <a name="remarks"></a>Комментарии

- Полный список параметров командной строки **PowerShell_ISE.exe** см. в разделе [about_PowerShell_Ise.Exe](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_ise_exe).

- Дополнительные сведения о других способах запуска Windows PowerShell см. в разделе [Запуск Windows PowerShell](https://docs.microsoft.com/powershell/scripting/windows-powershell/starting-windows-powershell).

- Windows PowerShell выполняется в варианте установки Server Core в операционных системах Windows Server. Однако, поскольку интегрированная среда сценариев Windows PowerShell требует графического пользовательского интерфейса, она не выполняется в установках Server Core.

## <a name="additional-references"></a>Дополнительные ссылки

- [about_PowerShell_Ise.exe] (https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_ise_exe

- [about_PowerShell.Exe](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_exe)

- [Windows PowerShell](https://docs.microsoft.com/powershell/)
