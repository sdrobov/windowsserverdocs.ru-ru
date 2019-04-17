---
title: "Установка и удаление языковых пакетов"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 98f13f63-4480-40ba-a7ef-d1d9b7582e5f
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: a41b491bbe4b4a8ee7f9743dc85e5bdaffb08496
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="install-or-remove-language-packs"></a>Установка и удаление языковых пакетов

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

> [!NOTE]
>  Сначала необходимо создать многоязыковой образ Windows, как описано в [языковые пакеты и развертывание](https://technet.microsoft.com/library/hh824829) перед добавлением языкового пакета Windows Server Essentials.  
  
 Языковые пакеты доступны только для создания многоязычных образов. Информация в этом разделе относится только к установке и удалению языковых пакетов в Windows Server Essentials.  
  
> [!NOTE]
>  Если предполагается выполнить начальную настройку (IC) с клиентского компьютера, который не поддерживает восточноазиатские языки, например ja-jp, а английский язык не включен в многоязычный образ на сервере, веб-страницы начальной настройки будет отображаться квадратами. Для веб-страницы начальной настройки по умолчанию английский, созданный многоязыковой образ необходимо включал английский язык.  
  
## <a name="adding-language-packs-to-an-image"></a>Добавление языковых пакетов в образ  
 Языковые пакеты доступны на DVD-диске настройки OEM. Рекомендуется скопировать на обслуживающий компьютер языковые пакеты перед добавлением языковых пакетов в образ.  
  
 Для установки языковых пакетов необходимо использовать следующую команду:  
  
 **Dism.exe//online /Add-Package /PackagePath: C:\\ < полный путь к CAB-файла directory\ > \lp.cab**  
  
 Например следующая команда показывается способ добавления немецкого языкового пакета:  
  
 **Dism.exe//online /Add-Package /PackagePath: C:\Users\Administrator\Desktop\WindowsHomeServer-Product-r\de-de\lp.cab**  
  
> [!IMPORTANT]
>  Также необходимо добавить языковые пакеты для Windows Server Essentials для полной локализации этой операционной системы.  
  
## <a name="removing-language-packs-from-an-image"></a>Удаление языковых пакетов из образа  
 Чтобы удалить языковой пакет, который вы больше не хотите включать в образ, можно использовать следующую команду:  
  
 **Dism.exe//online /Remove-Package /PackagePath: C:\\ < полный путь к CAB-файла directory\ > \lp.cab**  
  
 Например следующая команда показан пример удаления немецкого языкового пакета:  
  
 **Dism.exe//online /Remove-Package /PackagePath: C:\Users\Administrator\Desktop\WindowsHomeServer-Product-r\de-de\lp.cab**  
  
## <a name="see-also"></a>См. также:  

 [Создание и настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа для развертывания](Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](Testing-the-Customer-Experience.md)

 [Создание и настройка образа](../install/Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](../install/Additional-Customizations.md)   
 [Подготовка образа для развертывания](../install/Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](../install/Testing-the-Customer-Experience.md)

