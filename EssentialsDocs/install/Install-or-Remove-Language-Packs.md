---
title: Установка и удаление языковых пакетов
description: Описание использования Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 98f13f63-4480-40ba-a7ef-d1d9b7582e5f
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 4f7657f3ecb3450b5253d1cfe2813c12ecc2718e
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "80311723"
---
# <a name="install-or-remove-language-packs"></a>Установка и удаление языковых пакетов

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

> [!NOTE]
>  Сначала необходимо создать многоязыковой образ Windows, как описано в разделе [языковые пакеты и развертывание](https://technet.microsoft.com/library/hh824829) перед добавлением языкового пакета Windows Server Essentials.  
  
 Для создания многоязычных образов предусмотрены языковые пакеты. Сведения в этом разделе относятся к установке или удалению языковых пакетов в Windows Server Essentials.  
  
> [!NOTE]
>  Если предполагается выполнить начальную настройку (IC) с клиентского компьютера, не поддерживающего восточноазиатские языки (например, ja-jp), а английский язык не включен в многоязычный образ на сервере, веб-страница начальной настройки будет отображаться квадратами. Для отображения веб-страницы начальной настройки на английском языке по умолчанию необходимо, чтобы созданный многоязыковой образ включал английский язык.  
  
## <a name="adding-language-packs-to-an-image"></a>Добавление языковых пакетов в образ  
 Языковые пакеты доступны на DVD-диске с OEM-модулем настройки. Перед добавлением языковых пакетов в образ рекомендуется скопировать их на обслуживающий компьютер.  
  
 Для установки языковых пакетов необходимо использовать следующую команду:  
  
 **DISM. exe/Online/Add-Package/PackagePath: C:\\< полный путь к каталогу CAB-файлов\>\лп.каб**  
  
 В следующей команде показан пример добавления немецкого языкового пакета:  
  
 **DISM. exe/Online/Add-Package/PackagePath: К:\усерс\администратор\десктоп\виндовшомесервер-продукт-р\де-де\лп.каб**  
  
> [!IMPORTANT]
>  Также необходимо применить языковые пакеты для Windows Server Essentials, чтобы полностью локализовать операционную систему.  
  
## <a name="removing-language-packs-from-an-image"></a>Удаление языковых пакетов из образа  
 Чтобы удалить языковой пакет, который больше не нужно включать в образ, можно использовать следующую команду:  
  
 **DISM. exe/Online/Ремове-паккаже/PackagePath: C:\\< полный путь к каталогу CAB-файлов\>\лп.каб**  
  
 В следующей команде показан пример удаления немецкого языкового пакета:  
  
 **DISM. exe/Online/Ремове-паккаже/PackagePath: К:\усерс\администратор\десктоп\виндовшомесервер-продукт-р\де-де\лп.каб**  
  
## <a name="see-also"></a>См. также  

 [Создание и Настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа к развертыванию](Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](Testing-the-Customer-Experience.md)

 [Создание и Настройка образа](../install/Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](../install/Additional-Customizations.md)   
 [Подготовка образа к развертыванию](../install/Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](../install/Testing-the-Customer-Experience.md)

