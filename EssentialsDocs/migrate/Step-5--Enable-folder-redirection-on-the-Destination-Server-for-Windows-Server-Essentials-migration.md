---
title: Шаг 5. Включение перенаправления папок на целевом сервере для миграции Windows Server Essentials
description: Описание использования Windows Server Essentials
ms.date: 10/03/2016
ms.prod: windows-server
ms.topic: article
ms.assetid: d3925f80-552d-431f-b2a6-2af202e50ca4
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 710522f52791f3ee6c1c453c883f4265d08023be
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80852347"
---
# <a name="step-5-enable-folder-redirection-on-the-destination-server-for-windows-server-essentials-migration"></a>Шаг 5. Включение перенаправления папок на целевом сервере для миграции Windows Server Essentials

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Если перенаправление папок включено на исходном сервере, его можно включить на конечном сервере и затем удалить старый параметр групповой политики "Перенаправление папок".  
  
 Сначала используйте панель мониторинга Windows Server Essentials, чтобы включить перенаправление папок на целевом сервере. Затем удалите старый параметр групповой политики перенаправления папок.  
  
### <a name="to-enable-folder-redirection-on-the-destination-server"></a>Включение перенаправления папок на конечном сервере  
  
1.  На целевом сервере откройте панель мониторинга Windows Server Essentials.  
  
2.  На панели навигации щелкните **Устройства**.  
  
3.  В области **Задачи устройств** выберите **Реализация групповой политики**.  
  
4.  На странице **Включение групповой политики перенаправления папок** выберите папки для перенаправления и нажмите кнопку **Далее**.  
  
5.  На странице **Включение параметров политики безопасности** нажмите кнопку **Готово**.  
  
### <a name="to-delete-the-old-folder-redirection-group-policy-setting"></a>Удаление старого параметра групповой политики перенаправления папок  
  
1. На конечном сервере откройте средство администрирования **Управление групповой политикой**.  
  
2. В окне **Управление групповой политикой**разверните **Лес:** <em>имя_сетевого_домена</em>разверните **Домены**разверните *имя_сетевого_домена*и **Объекты групповой политики**.  
  
3. Щелкните правой кнопкой мыши политику, которую требуется удалить, а затем щелкните **Удалить**.  
  
4. Прочтите предупреждение и нажмите кнопку **Да**.  
  
5. Закройте **Управление групповой политикой**.  
  
   Чтобы применить изменения для перенаправления папок, пользователи сети должны выйти из своих компьютеров, а затем зайти снова. Это обеспечивает передачу всех перенаправленных папок на конечный сервер.  
  
## <a name="next-steps"></a>Следующие шаги  
 Вы включили перенаправление папок на целевом сервере. Теперь перейдите к [шагу 6: понизить и удалить исходный сервер из новой сети Windows Server Essentials](Step-6--Demote-and-remove-the-Source-Server-from-the-new-Windows-Server-Essentials-network.md).  
  

Для просмотра всех шагов см. статью [Переход на Windows Server Essentials](Migrate-from-Previous-Versions-to-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md).

