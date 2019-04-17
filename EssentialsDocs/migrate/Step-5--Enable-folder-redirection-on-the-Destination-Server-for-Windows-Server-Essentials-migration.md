---
title: "Шаг 5: Включение перенаправления папок на конечный сервер для миграции Windows Server Essentials"
description: "Описывается, как использовать Windows Server Essentials"
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
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="step-5-enable-folder-redirection-on-the-destination-server-for-windows-server-essentials-migration"></a>Шаг 5: Включение перенаправления папок на конечный сервер для миграции Windows Server Essentials

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Если на исходном сервере включено перенаправление папок, можно включить перенаправление папок на конечном сервере и затем удалите старый параметр групповой политики перенаправления папок.  
  
 Во-первых используйте панель мониторинга Windows Server Essentials для включения перенаправления папок на конечном сервере. Затем удалите старый параметр групповой политики перенаправления папок.  
  
### <a name="to-enable-folder-redirection-on-the-destination-server"></a>Чтобы включить перенаправление папок на конечном сервере  
  
1.  На конечном сервере откройте панель мониторинга Windows Server Essentials.  
  
2.  На панели навигации щелкните **устройств**.  
  
3.  В **задачи устройств** панели, щелкните **реализация групповой политики**.  
  
4.  На **Включение групповой политики перенаправления папок** выберите папки для перенаправления и нажмите кнопку **Далее**.  
  
5.  На **Включение параметров политики безопасности** щелкните **Готово**.  
  
### <a name="to-delete-the-old-folder-redirection-group-policy-setting"></a>Чтобы удалить старый параметр групповой политики перенаправления папок  
  
1.  На конечном сервере откройте **Управление групповой политикой** средство администрирования.  
  
2.  В **Управление групповой политикой**, разверните **леса:***Имя_сетевого_домена*, разверните **домены**, разверните *Имя_сетевого_домена*и затем разверните **объектов групповой политики**.  
  
3.  Щелкните правой кнопкой мыши политики, который требуется удалить, а затем щелкните **удалить**.  
  
4.  Прочтите предупреждение и нажмите кнопку **Да**.  
  
5.  Закрыть **Управление групповыми политиками**.  
  
 Чтобы применить изменения для перенаправления папок, пользователи сети должны выйти из своих компьютеров и снова войдите в систему. Это обеспечивает передачу всех перенаправленных папок на конечный сервер.  
  
## <a name="next-steps"></a>Дальнейшие действия  
 Вы включили перенаправление папок на конечном сервере. Теперь перейдите к [шаг 6: понижение уровня и удаление исходного сервера из новой сети Windows Server Essentials](Step-6--Demote-and-remove-the-Source-Server-from-the-new-Windows-Server-Essentials-network.md).  
  

Для просмотра всех шагов см [переход на Windows Server Essentials](Migrate-from-Previous-Versions-to-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md).

