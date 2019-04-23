---
title: Добавление категорий верхнего уровня в панель запуска (операционная система Macintosh)
description: Описывает способ использования Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ee2173c3-e464-4001-9f43-6d926a575092
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: ae4eb5943d37b4a9d3b554af28cb425420782cf8
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59869965"
---
# <a name="add-top-level-categories-to-the-launchpad-macintosh-operating-system"></a>Добавление категорий верхнего уровня в панель запуска (операционная система Macintosh)

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

На компьютерах под управлением операционной системы Macintosh можно добавить в панель запуска категории верхнего уровня. Чтобы создать надстройку панели запуска, которая добавляет категории верхнего уровня, можно использовать информацию на этой странице и в разделе Практическое руководство: Добавление задач и категорий в панель запуска? в [Windows Server Solutions SDK](https://go.microsoft.com/fwlink/?LinkID=248648).  
  
 В следующем примере показано, каким образом можно назначить запись панели запуска категорией верхнего уровня в LAUNCHPAD-файле.  
  
```  
  
<?xml version="1.0" encoding="utf-8" ?>  
<LaunchPad resFile="Localizable">  
   <Category id="Microsoft.Launchpad.HomeCategory" name="SampleAddin"  image="SampleImage01.png">  
      <Task id="Microsoft.Launchpad.SampleAddin.Pictures"   
          name="Pictures"       
           src="smb://%ServerAddress%/Pictures"   
         image="SampleImage02.png"/>  
   </Category>  
</LaunchPad>  
```  
  
 Для назначения записи категорией верхнего уровня для атрибута Id элемента Category необходимо назначить значение «Microsoft.Launchpad.HomeCategory».  
  
## <a name="see-also"></a>См. также  
 [Создание и настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа для развертывания](Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](Testing-the-Customer-Experience.md)