---
title: "Установка на сервере системы оценки WinSAT"
description: "Описывается, как использовать Windows Server Essentials"
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
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="set-the-winsat-score-on-the-server"></a>Установка на сервере системы оценки WinSAT

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Следует задать оценку ЦП средства WinSAT для сервера под управлением операционной системы Windows Server Essentials, чтобы оптимизировать разрешение потокового видео. Для этого необходимо создать и установить XML-файл, содержащий сведения об оценке WinSAT.  
  
## <a name="obtain-the-winsat-cpu-score"></a>Получение оценки ЦП средства WinSAT  
 Программа будет предоставлен предустановочного набора OPK, называемый WinServerSAT.exe, которая обнаруживает оценку ЦП средства WinSAT и помещает эти сведения в файл WinServerSAT.xml, считываемый операционной системы.  
  
#### <a name="to-obtain-the-winsat-cpu-score"></a>Для получения оценки ЦП средства WinSAT  
  
1.  Скопируйте Resources\WinServerSAT\\ * на носителе ADK на эталонном компьютере.  
  
2.  На компьютере-образце откройте окно командной строки с повышенными привилегиями.  
  
3.  Если папка %ProgramFiles%\Windows Server\Bin\OEM не существует, введите следующую команду и нажмите клавишу ВВОД.  
  
     **mkdir «%ProgramFiles%\Windows Server\Bin\OEM»**  
  
4.  Введите следующую команду и нажмите клавишу ВВОД.  
  
     **WinServerSAT.exe «%ProgramFiles%\Windows Server\Bin\OEM\WinServerSAT.xml»**  
  
 В следующем примере показано содержимое XML созданного файла WinServerSAT.xml.  
  
```  
  
<?xml version="1.0" encoding="UTF-16"?>  
<WinSAT>  
   <CpuScore description="WinSAT CPU score">WinSAT_Score</CpuScore>  
</WinSAT>  
```  
  
 Где *WinSAT_Score* заменяется значением, обнаруживаемым сервером.  
  
> [!IMPORTANT]
>  WinServerSAT.exe, winsat.prx, winsat.wmv и WinSATEncode.wmv файлы с компьютера-образца необходимо удалить перед записью образа.
