---
title: "Настройка архивации сервера"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 19b2559c-6090-45af-9a08-2eefc28473c8
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: d18dca276bccdf672664a5a3c2bd28e0221fff94
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="customize-server-backup"></a>Настройка архивации сервера

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

## <a name="turn-off-server-backup-by-default"></a>Выключить резервное копирование сервера по умолчанию  
 Вы можете выключить резервное копирование сервера по умолчанию. Необходимо задать значение **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows Server\ServerBackup\ProviderDisabled** 1, чтобы включить этот параметр.  
  
 Если задать этот раздел сервера резервной копии пользовательского интерфейса не будет отображаться на панели мониторинга и панели запуска. Это позволяет использовать сторонние приложения для архивации сервера.  
  
#### <a name="to-add-serverbackupproviderdisabled-registry-key-and-set-the-value-to-1"></a>Чтобы добавить ServerBackup\ProviderDisabled? раздел реестра и возвращает значение 1  
  
1.  На сервере нажмите кнопку **запустить**, нажмите кнопку **запуска**, тип **regedit** в **откройте** textbox и нажмите кнопку **ОК**.  
  
2.  В области навигации разверните **HKEY_LOCAL_MACHINE**, разверните **программного обеспечения**, разверните **Microsoft**, разверните **Windows Server**и затем разверните **ServerBackup**.  
  
3.  Щелкните правой кнопкой мыши **ServerBackup**, нажмите кнопку **New**, а затем нажмите кнопку **значение DWORD**.  
  
4.  Имя, введите **ProviderDisabled**.  
  
5.  Щелкните правой кнопкой мыши имя, выберите **изменить**, введите **1** значение, а затем нажмите кнопку **ОК**.  
  
## <a name="turn-on-server-backup"></a>Включить резервное копирование сервера  
 Архивация сервера можно включить, если он был отключен, создав **ProviderDisabled** раздел реестра (как описано ранее в этом документе).  
  
 Необходимо удалить раздел **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows Server\ServerBackup\ProviderDisabled** Чтобы включить архивацию сервера по умолчанию, изменить тип запуска службы архивации данных сервера Windows Server и перезапустите сервер.  
  
#### <a name="to-delete-serverbackupproviderdisabled-registry-key"></a>Чтобы удалить ServerBackup\ProviderDisabled? раздел реестра  
  
1.  На сервере, переместите указатель мыши в правый верхний угол экрана, а затем нажмите кнопку **поиска**.  
  
2.  В поле поиска введите **regedit**, а затем нажмите кнопку **Regedit** приложения.  
  
3.  В области навигации разверните **HKEY_LOCAL_MACHINE**, разверните **программного обеспечения**, разверните **Microsoft**, разверните **Windows Server**и затем разверните **ServerBackup**.  
  
4.  Щелкните правой кнопкой мыши **ProviderDisabled**, а затем нажмите кнопку **удалить**.  
  
#### <a name="change-the-start-type-of-windows-server-server-backup-service"></a>Изменить тип запуска службы архивации данных сервера Windows Server  
  
1.  На сервере, переместите указатель мыши в правый верхний угол экрана, а затем нажмите кнопку **поиска**.  
  
2.  В поле поиска введите **services.msc**, а затем нажмите кнопку **службы** приложения.  
  
3.  В области служб щелкните правой кнопкой мыши **службы резервного копирования сервера Windows Server**и нажмите кнопку **свойства**.  
  
4.  В **Общие** выберите **автоматического** для **тип запуска**.  
  
5.  Нажмите кнопку **ОК** чтобы закрыть диалоговое окно.  
  
#### <a name="restart-the-server"></a>Перезапустите сервер  
  
1.  На сервере, переместите указатель мыши в правый верхний угол экрана, нажмите кнопку **параметры**, нажмите кнопку **питания**, а затем перезагрузить компьютер.