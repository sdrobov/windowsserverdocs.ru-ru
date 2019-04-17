---
title: "Автоматизация установки надстройки во время установки"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2e6ff6e4-8d68-4d49-9e38-8088bc8bf95e
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: d4c547c2fec8e2b11e5c1d9bde46e55e91c9d6fa
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="automate-installation-of-add-ins-during-setup"></a>Автоматизация установки надстройки во время установки

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

##  <a name="BKMK_AddIns"></a>Автоматизация установки надстройки во время установки  
 Чтобы установить надстройки во время установки, используйте метод PostIC.cmd, описанный в [Создание файла PostIC.cmd для выполнения Post задач начальной настройки](Create-the-PostIC.cmd-File-for-Running-Post-Initial-Configuration-Tasks.md) этого документа.  
  
 Добавьте следующую запись вашего PostIC.cmd:  
  
```  
C:\Program Files\Windows Server\bin\Installaddin.exe <full path to wssx file> -q  
```  
  
 Надстройка теперь поддерживает удалить перед установкой и настраиваемые действия.  
  
 Шаг перед установкой запускается перед установкой все **.msi** файлов, указанных в addin.xml. При запуске в интерактивном режиме диалоговое окно хода выполнения будет показано, но без изменения хода выполнения. Кнопка отмены отключена на этапе предварительной установки. Реализация шага предустановки, добавьте следующее содержимое в addin.xml (непосредственно в пакете):  
  
> [!NOTE]
>  Схема xml должна точности соответствовать указанной ниже:  
  
```  
<Package xmlns="https://schemas.microsoft.com/WindowsServerSolutions/2010/03/Addins" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">  
  <Id>...</Id>  
  <Version>...</Version>  
  <Name>...</Name>  
  <Allow32BitOn64BitClients>...</Allow32BitOn64BitClients>  
  <ServerBinary>...</ServerBinary>  
  <ClientBinary32>...</ClientBinary32>  
  <ClientBinary64>...</ClientBinary64>  
  <SupportedSkus>...</SupportUrl>    
  <SupportUrl>...</SupportUrl>  
  <Location>...</Location>    
  <PrivacyStatement>...</PrivacyStatement>  
  <OtherBinaries>...</OtherBinaries>   
  <Preinstall>  
<Executable>exefile</Executable>  
<NormalArgs>args-for-interactive-mode</NormalArgs>  
<SilentArgs>args-for-silent-mode</SilentArgs>  
<IgnoreExitCode>true</IgnoreExitCode>  
  </Preinstall>  
  <UninstallConfirm>...</UninstallConfirm>      
</Package>  
<¦>  
<¦>  
```  
  
 Wherein **exefile** исполняемый файл в пакете надстройки для выполнения этого шага перед установкой и должен быть указан. **NormalArgs** указывает аргументы должны передаваться exefile в режиме командной строки, если интерактивные используется. В этом режиме exefile можно всплывающее окно, некоторые диалоговые окна для взаимодействия с пользователем. **SilentArgs** указывает, используется аргументы должны передаваться exefile в режиме командной строки, при автоматическом (-q задается при вызове installaddin.exe). Exefile следует не всплывающее окно, любой windows в этом режиме. Если **IgnoreExitCode** задано значение true, шага предустановки всегда считается успешным, в противном случае — код выхода 0 указывает на успешное выполнение, значение 1 указывает на отмену и другие значения свидетельствуют об ошибке. Теги **NormalArgs**, **SilentArgs**, и **IgnoreExitCode** , являются необязательными.  
  
 Шаг настраиваемый удаления можно использовать для любого из следующих:  
  
-   Замените диалоговое окно встроенной подтверждения.  
  
-   Заполните настраиваемый диалоговые окна до удаления.  
  
-   Выполните определенные задачи до удаления.  
  
 Реализация шага удаления, добавьте следующее содержимое в addin.xml (непосредственно в пакете):  
  
```  
<Package xmlns="https://schemas.microsoft.com/WindowsServerSolutions/2010/03/Addins" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">  
  <Id>...</Id>  
  <Version>...</Version>  
  <Name>...</Name>  
  <Allow32BitOn64BitClients>...</Allow32BitOn64BitClients>  
  <ServerBinary>...</ServerBinary>  
  <ClientBinary32>...</ClientBinary32>  
  <ClientBinary64>...</ClientBinary64>  
  <SupportedSkus>...</SupportUrl>    
  <SupportUrl>...</SupportUrl>  
  <Location>...</Location>    
  <PrivacyStatement>...</PrivacyStatement>  
  <OtherBinaries>...</OtherBinaries>   
  <Preinstall>¦</Preinstall>  
<UninstallConfirm>  
<Executable>full-path-to-exefile</Executable>  
<Arguments>command-line-arguments</Arguments>  
</UninstallConfirm>  
</Package>  
```  
  
 Wherein **полный путь к exefile** указывает exefile, уже установлено в системе. **Аргументы** является необязательным и задает аргументы командной строки для exefile. Exefile вызывается перед удалением встроенный подтверждения появляется диалоговое окно.  
  
 Exefile можно выполнять следующие задачи на этом этапе:  
  
-   Появится некоторые диалоговые окна для взаимодействия с пользователем.  
  
-   Некоторые фоновой задачи.  
  
 Код выхода exe-файла определяет, перемещение вперед процесс удаления.  
  
-   0: процесс удаления продолжается без заполнения диалоговое окно встроенной подтверждения, так же, как пользователь уже подтвердила. (этот подход можно использовать для замены диалоговое окно встроенной подтверждения);  
  
-   1: отменены процесс удаления, и наконец отмененного сообщения будут отображаться для пользователя. Все данные остаются без изменений;  
  
-   Другой: процесс удаления продолжается с диалоговое окно встроенной подтверждения, так же, как шага настраиваемый удаления отсутствует.  
  
 Любой сбой вызова exefile приведет к одинаковое поведение как exefile возвращает код, кроме 0 или 1.  
  
## <a name="see-also"></a>См. также:  
 [Создание и настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа для развертывания](Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](Testing-the-Customer-Experience.md)