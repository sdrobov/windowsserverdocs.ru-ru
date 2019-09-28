---
title: Команды DiskPart
ms.prod: windows-server
ms.technology: storage
author: JasonGerend
manager: elizapo
ms.author: jgerend
ms.openlocfilehash: 0826b773927f09cc846fb1cfdf4d5dfbf75d5cca
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71377826"
---
# <a name="diskpart-commands"></a>Команды DiskPart

Область применения. Windows 10, Windows 8.1, Windows 8, Windows 7, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 и Windows Server 2008 R2, Windows Server 2008

Команды DiskPart позволяют управлять дисками компьютера (дисками, разделами, томами или виртуальными жесткими дисками). Прежде чем можно будет использовать команды DiskPart, необходимо сначала вывести список, а затем выбрать объект, чтобы получить фокус. Когда объект имеет фокус, любые команды DiskPart, которые вы вводите, будут действовать для этого объекта.

Вы можете получить список доступных объектов и определить число или букву диска с помощью команд **List Disk, List Volume, list partition**и **List VDISK** . Команды List **Disk, List VDISK** и **list volume** отображают все диски и тома на компьютере. Однако команда **list partition** отображает только разделы на диске, имеющем фокус. При использовании команд **List** отображается звездочка (\*) рядом с объектом с фокусом.

При выборе объекта фокус остается на этом объекте до тех пор, пока не будет выбран другой объект. Например, если фокус установлен на диске 0 и вы выбрали том 8 на диске 2, фокус переместится с диска 0 на диск 2, том 8. Некоторые команды автоматически меняют фокус. Например, при создании новой секции фокус автоматически переключается на новую секцию.

Вы можете передать фокус только на раздел на выбранном диске. Если фокус находится на секции, соответствующий том (если он есть) также имеет фокус. Если у тома есть фокус, связанный диск и раздел также будут иметь фокус, если том сопоставляется с одним конкретным разделом. Если это не так, фокус на диске и разделе будет потерян.

## <a name="diskpart-commands"></a>Команды DiskPart

Чтобы запустить интерпретатор команд DiskPart, в командной строке введите:

`diskpart`

> [!IMPORTANT]
> Членство в группе локальных **администраторов** (или аналогичной) является минимальным требованием для запуска DiskPart. 

В интерпретаторе команд DiskPart можно выполнить следующие команды:

  - [Active](active.md)  
      
  - [Включить](add.md)  
      
  - [Назначать](assign.md)  
      
  - [Подключить виртуальный диск](attach-vdisk.md)  
      
  - [Атрибута](attributes.md)  
      
  - [Автоподключения](automount.md)  
      
  - [Разбиени](break.md)  
      
  - [Очистить](clean.md)  
      
  - [Compact VDISK](compact-vdisk.md)  
      
  - [Функция](convert.md)  
      
  - [Создание](create.md)  
      
  - [Удаление](delete.md)  
      
  - [Отсоединить виртуальный диск](detach-vdisk.md)  
      
  - [Налог](detail.md)  
      
  - [Выход](exit.md)  
      
  - [Развернуть виртуальный диск](expand-vdisk.md)  
      
  - [Расширений](extend.md)  
      
  - [Файловые системы](filesystems.md)  
      
  - [Формат](format.md)  
      
  - [ТАБЛИЦЫ](gpt.md)  
      
  - [Справка](help.md)  
      
  - [Импорт](import.md)  
      
  - [Активный](inactive.md)  
      
  - [Числ](list.md)  
      
  - [Слияние VDISK](merge-vdisk.md)  
      
  - [Работа](offline.md)  
      
  - [Онлайн](online.md)  
      
  - [Конвертер](recover.md)  
      
  - [Оставшие](rem.md)  
      
  - [Удалить](remove.md)  
      
  - [Чинить](repair.md)  
      
  - [Повторное сканирование](rescan.md)  
      
  - [Удержание](retain.md)  
      
  - [San](san.md)  
      
  - [Метьте](select.md)  
      
  - [Идентификатор набора](set-id.md)  
      
  - [Соответствии](shrink.md)  
      
  - [UniqueID](uniqueid.md)  
      

## <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

[Командлеты хранилища в Windows PowerShell](https://docs.microsoft.com/powershell/module/storage/)
