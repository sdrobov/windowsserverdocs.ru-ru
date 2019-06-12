---
title: PowerShell_ise
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 32c41b5b-a210-47d9-bd8c-91eb9830b4f0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a5619396e29b446dbc6804ece7444f355dae4c0a
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66436299"
---
# <a name="powershellise"></a>PowerShell_ise



Windows PowerShell сценарии среды (Интегрированная) — это графический ведущее приложение, которое дает возможность чтения, записи, запуска, отлаживать и тестировать сценарии и модули в среде с поддержкой график. Основные функции, такие как IntelliSense, Show-Command, фрагменты кода, нажатием клавиши TAB, выделение синтаксиса цветом, visual отладки и контекстной справки, которые предоставляют со сценариями более удобной.

**PowerShell_ISE.exe** средство запускает сеанс Windows PowerShell ISE. При использовании **PowerShell_ISE.exe**, своих необязательных параметров можно использовать для открытия файлов в интегрированной среде Сценариев Windows PowerShell или сеанса интегрированной среды Сценариев Windows PowerShell без профиля или многопотоковом подразделении.

**PowerShell_ISE.exe** был впервые появился в Windows PowerShell 2.0 и в Windows PowerShell 3.0 значительно расширены.

## <a name="using-powershelliseexe"></a>С помощью PowerShell_ISE.exe

Можно использовать **PowerShell_ISE.exe** начала и окончания сеанса Windows PowerShell следующим образом:
- Чтобы запустить сеанс интегрированной среды Сценариев Windows PowerShell в окне командной строки, в Windows PowerShell или в меню "Пуск", введите следующую команду:  
  ```
  PowerShell_Ise
  ```  
- Чтобы открыть скрипта (ps1), модуль сценария (psm1-файлы), манифеста модуля (.psd1), XML-файл или любой другой поддерживаемый файл в интегрированной среде Сценариев Windows PowerShell, используйте следующий формат:  
  ```
  PowerShell_Ise <FilePath>
  ```  
  В Windows PowerShell 3.0, можно использовать необязательный **файл** параметр следующим образом:  
  ```
  PowerShell_Ise -File <FilePath>
  ```  
- Чтобы запустить сеанс интегрированной среды Сценариев Windows PowerShell без профили Windows PowerShell, используйте **NoProfile** параметра. ( **NoProfile** параметр впервые появился в Windows PowerShell 3.0.)  
  ```
  PowerShell_Ise -NoProfile
  ```  
- Чтобы увидеть **PowerShell_ISE.exe** помочь файл в окне командной строки, используйте следующий формат:  
  ```
  PowerShell_Ise -help, -?, /?
  ```  
  Полный список **PowerShell_ISE.exe** параметров командной строки, см. в разделе [about_PowerShell_Ise.exe](https://go.microsoft.com/fwlink/?LinkId=256512).

## <a name="start-windows-powershell-ise-in-other-ways"></a>Запустите Windows PowerShell ISE другими способами

Сведения о других способах запуска интегрированной среды Сценариев Windows PowerShell, см. в разделе [запуск Windows PowerShell](https://go.microsoft.com/fwlink/?LinkID=135259).

## <a name="remarks"></a>Примечания

Windows PowerShell работает в варианте установки основных серверных компонентов операционных систем Windows Server. Тем не менее так как интегрированная среда Сценариев Windows PowerShell требуется графический пользовательский интерфейс, он не выполняется при установке ядра сервера.

## <a name="additional-references"></a>Дополнительная справка

[about_PowerShell_Ise.exe](https://go.microsoft.com/fwlink/?LinkId=256512)
[about_PowerShell.exe](https://go.microsoft.com/fwlink/?LinkID=113439)
[Windows PowerShell](https://go.microsoft.com/fwlink/?LinkID=107116)
[Создание сценариев с помощью Windows PowerShell](https://technet.microsoft.com/scriptcenter/dd742419) см. также