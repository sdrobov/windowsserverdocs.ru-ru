---
title: Установка и удаление языковых пакетов
description: Описание использования Windows Server Essentials
ms.date: 10/03/2016
ms.prod: windows-server
ms.topic: article
ms.assetid: 98f13f63-4480-40ba-a7ef-d1d9b7582e5f
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: c1fd1d21277d32672398d1dd201e2dda24682c2d
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80820027"
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

