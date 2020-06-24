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
ms.openlocfilehash: 64e982f7932f8ba3ecf83ffe6443391522ad0f12
ms.sourcegitcommit: 6d6a0225b1f83b71fcb494b94d666cd5e54c7566
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/23/2020
ms.locfileid: "85267555"
---
# <a name="install-or-remove-language-packs"></a>Установка и удаление языковых пакетов

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

> [!NOTE]
>  Сначала необходимо создать многоязыковой образ Windows, как описано в разделе [языковые пакеты и развертывание](https://technet.microsoft.com/library/hh824829) перед добавлением языкового пакета Windows Server Essentials.  
  
 Для создания многоязычных образов предусмотрены языковые пакеты. Сведения в этом разделе относятся к установке или удалению языковых пакетов в Windows Server Essentials.  
  
> [!NOTE]
>  Если предполагается выполнить начальную настройку (IC) с клиентского компьютера, не поддерживающего восточноазиатские языки (например, ja-jp), а английский язык не включен в многоязычный образ на сервере, веб-страница начальной настройки будет отображаться квадратами. Для отображения веб-страницы начальной настройки на английском языке по умолчанию необходимо, чтобы созданный многоязычный образ включал английский язык.  
  
## <a name="adding-language-packs-to-an-image"></a>Добавление языковых пакетов в образ  
 Языковые пакеты доступны на DVD-диске с OEM-модулем настройки. Перед добавлением языковых пакетов в образ рекомендуется скопировать их на обслуживающий компьютер.  
  
 Для установки языковых пакетов необходимо использовать следующую команду:  
  
 **dism.exe/Online/Add-Package/PackagePath: C: \\<полный путь к каталогу CAB-файлов \>\lp.cab**  
  
 В следующей команде показан пример добавления немецкого языкового пакета:  
  
 **dism.exe /online /Add-Package /PackagePath:C:\Users\Administrator\Desktop\WindowsHomeServer-Product-r\de-de\lp.cab**  
  
> [!IMPORTANT]
>  Также необходимо применить языковые пакеты для Windows Server Essentials, чтобы полностью локализовать операционную систему.  
  
## <a name="removing-language-packs-from-an-image"></a>Удаление языковых пакетов из образа  
 Чтобы удалить языковой пакет, который больше не нужно включать в образ, можно использовать следующую команду:  
  
 **dism.exe/Online/Ремове-паккаже/PackagePath: C: \\<полный путь к каталогу CAB-файлов \>\lp.cab**  
  
 В следующей команде показан пример удаления немецкого языкового пакета:  
  
 **dism.exe /online /Remove-Package /PackagePath:C:\Users\Administrator\Desktop\WindowsHomeServer-Product-r\de-de\lp.cab**  
  
## <a name="see-also"></a>См. также  

 [Создание и Настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа к развертыванию](Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](Testing-the-Customer-Experience.md)

