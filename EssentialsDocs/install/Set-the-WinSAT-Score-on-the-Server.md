---
title: Установка на сервере системы оценки WinSAT
description: Описывает способ использования Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 911dc494-0f8f-4723-93d6-2106f914b906
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 77866acccac13ac48da8779700c8654f2c7f3277
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59819955"
---
# <a name="set-the-winsat-score-on-the-server"></a>Установка на сервере системы оценки WinSAT

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Для сервера под управлением операционной системы Windows Server Essentials для оптимизации потоковой передачи разрешение следует задать оценки ЦП средства WinSAT. Для этого необходимо создать и установить XML-файл, содержащий сведения об оценках WinSAT.  
  
## <a name="obtain-the-winsat-cpu-score"></a>Получение оценки ЦП средства WinSAT  
 В состав предустановочного набора OPK входит программа WinServerSAT.exe, которая обнаруживает оценку ЦП средства WinSAT и помещает эти сведения в файл WinServerSAT.xml, считываемый операционной системой.  
  
#### <a name="to-obtain-the-winsat-cpu-score"></a>Получение оценки ЦП средства WinSAT  
  
1.  Скопируйте Resources\WinServerSAT\\* на носителе ADK на компьютере-образце.  
  
2.  На компьютере-образце откройте окно командной строки с повышенными привилегиями.  
  
3.  Если папка %ProgramFiles%\Windows Server\Bin\OEM не существует, введите следующую команду и нажмите ВВОД  
  
     **mkdir "%ProgramFiles%\Windows Server\Bin\OEM"**  
  
4.  Введите следующую команду и нажмите ВВОД.  
  
     **WinServerSAT.exe "%ProgramFiles%\Windows Server\Bin\OEM\WinServerSAT.xml"**  
  
 В примере показано содержимое XML созданного файла WinServerSAT.xml.  
  
```  
  
<?xml version="1.0" encoding="UTF-16"?>  
<WinSAT>  
   <CpuScore description="WinSAT CPU score">WinSAT_Score</CpuScore>  
</WinSAT>  
```  
  
 где *оценка_WinSAT* заменяется значением, обнаруживаемым сервером.  
  
> [!IMPORTANT]
>  Перед началом записи образа необходимо удалить файлы WinServerSAT.exe, winsat.prx, winsat.wmv и WinSATEncode.wmv с компьютера-образца.
