---
title: "Добавление оповещений о работоспособности"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 270e0aac-dc42-46f3-a20b-a68ffbded06d
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: cf0c062b92c687f5f7b33b419eafdca2dd3bbbfc
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="add-health-alerts"></a>Добавление оповещений о работоспособности

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Надстройки работоспособности предоставляет определения для оповещений, проверку работоспособности и действия по восстановлению сетевых проблем. Надстройки работоспособности состоит из XML-файлов, которые дополняют код или данные, используемые для оценки работоспособности сведения для конкретной функции. Надстройки работоспособности создаются разработчиками и установить на сервер и клиентские компьютеры, администратор.  
  
 См. в разделе [пакет SDK для решений Windows Server](https://go.microsoft.com/fwlink/?LinkID=248648) подробные сведения о создании надстройки работоспособности.  
  
## <a name="installing-health-add-in-files"></a>Установка файлов работоспособности  
 После создания XML-файлы, разработчик копия файлов необходимо поместить в правильное расположение на сервер и клиентские компьютеры.  
  
#### <a name="to-install-the-xml-files-on-the-server"></a>Установка XML-файлов на сервере  
  
1.  В **%ProgramFiles%\Windows Server\Bin\Feature определения** папки, создайте новую папку с именем **MyHealthAddIn**. В этой папке можно присвоить любое имя. Предполагается, что имя папки совпадать с именем компонента.  
  
2.  Копировать Definition.xml и Definition.xml .config файлы в новую папку.  
  
3.  Если вы создали двоичные файлы для условий или действий, следует также скопировать эти файлы в папку **%ProgramFiles%\Windows Server\Bin**.  
  
 Запланированная задача каждые 6 часов, запрашивающий XML-файлы в соответствующую папку выполняется на клиентских компьютерах. Выполнить принудительную синхронизацию между клиентским компьютером и сервером, запустив задачу вручную.  
  
#### <a name="to-install-the-xml-files-on-the-client-computer"></a>Установка XML-файлов на клиентском компьютере  
  
1.  Откройте планировщик заданий.  
  
2.  Запустите **HealthDefintionUpdateTask** в планировщике заданий.  
  
    > [!NOTE]
    >  Эта задача не устанавливаются двоичные файлы. Необходимо вручную скопировать двоичные файлы для **%ProgramFiles%\Windows Server\Bin** папки на клиентском компьютере.  
  
## <a name="see-also"></a>См. также:  
 [Создание и настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа для развертывания](Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](Testing-the-Customer-Experience.md)