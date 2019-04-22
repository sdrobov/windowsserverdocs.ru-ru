---
title: Шаг 5. Включение перенаправления папок на конечный сервер для миграции Windows Server Essentials
description: Описывает способ использования Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d3925f80-552d-431f-b2a6-2af202e50ca4
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 613ff4c80a80ed4f3207cb0c1ead6db12c723e85
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59815385"
---
# <a name="step-5-enable-folder-redirection-on-the-destination-server-for-windows-server-essentials-migration"></a>Шаг 5. Включение перенаправления папок на конечный сервер для миграции Windows Server Essentials

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Если перенаправление папок включено на исходном сервере, его можно включить на конечном сервере и затем удалить старый параметр групповой политики "Перенаправление папок".  
  
 Во-первых следует используйте панели мониторинга Windows Server Essentials для включения перенаправления папок на целевом сервере. Затем удалите старый параметр групповой политики перенаправления папок.  
  
### <a name="to-enable-folder-redirection-on-the-destination-server"></a>Включение перенаправления папок на конечном сервере  
  
1.  На конечном сервере откройте панель мониторинга Windows Server Essentials.  
  
2.  На панели навигации щелкните **Устройства**.  
  
3.  В области **Задачи устройств** выберите **Реализация групповой политики**.  
  
4.  На странице **Включение групповой политики перенаправления папок** выберите папки для перенаправления и нажмите кнопку **Далее**.  
  
5.  На странице **Включение параметров политики безопасности** нажмите кнопку **Готово**.  
  
### <a name="to-delete-the-old-folder-redirection-group-policy-setting"></a>Удаление старого параметра групповой политики перенаправления папок  
  
1.  На конечном сервере откройте средство администрирования **Управление групповой политикой**.  
  
2.  В **Управление групповой политикой**, разверните узел **леса: *** Имя_сетевого_домена*, разверните **домены**, разверните *Имя_сетевого_домена* , а затем разверните **объектов групповой политики**.  
  
3.  Щелкните правой кнопкой мыши политику, которую требуется удалить, а затем щелкните **Удалить**.  
  
4.  Прочтите предупреждение и нажмите кнопку **Да**.  
  
5.  Закройте **Управление групповой политикой**.  
  
 Чтобы применить изменения для перенаправления папок, пользователи сети должны выйти из своих компьютеров, а затем зайти снова. Это обеспечивает передачу всех перенаправленных папок на конечный сервер.  
  
## <a name="next-steps"></a>Следующие шаги  
 Вы включили перенаправление папок на целевом сервере. Теперь перейдите к [шаг 6: Понижение уровня и удаление исходного сервера из новой сети Windows Server Essentials](Step-6--Demote-and-remove-the-Source-Server-from-the-new-Windows-Server-Essentials-network.md).  
  

Чтобы просмотреть все действия, см. в разделе [миграции на Windows Server Essentials](Migrate-from-Previous-Versions-to-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md).

