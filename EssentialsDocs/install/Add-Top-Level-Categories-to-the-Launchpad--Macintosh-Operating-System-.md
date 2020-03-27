---
title: Добавление категорий верхнего уровня в панель запуска (операционная система Macintosh)
description: Описание использования Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ee2173c3-e464-4001-9f43-6d926a575092
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 3b16cadc14999e041dc6b1661689787e434460eb
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "80310228"
---
# <a name="add-top-level-categories-to-the-launchpad-macintosh-operating-system"></a>Добавление категорий верхнего уровня в панель запуска (операционная система Macintosh)

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

На компьютерах под управлением операционной системы Macintosh можно добавить в панель запуска категории верхнего уровня. Чтобы создать надстройку панели запуска, которая добавляет категории верхнего уровня, можно использовать сочетание информации с этой страницы и из раздела «инструкции. Добавление задач и категорий» на панель запуска. в [пакете SDK для Windows Server Solutions](https://go.microsoft.com/fwlink/?LinkID=248648).  
  
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
 [Создание и Настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа к развертыванию](Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](Testing-the-Customer-Experience.md)