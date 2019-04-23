---
title: Восстановление леса AD — процедуры
description: ''
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 08/09/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.assetid: 47a471fb-3b0b-4aa8-8525-1c92d0d51e93
ms.technology: identity-adds
ms.openlocfilehash: da45e3b20c370a2a37b0eab31a78216434dd60be
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59827725"
---
# <a name="ad-forest-recovery---procedures"></a>Восстановление леса AD — процедуры

>Область применения. Windows Server 2016, Windows Server 2012 и 2012 R2, Windows Server 2008 и 2008 R2

Этот раздел содержит процедуры, относящиеся к процессу восстановления леса. Процедуры применимы для Windows Server 2016, 2012 R2, 2012 они также применима к Windows Server 2008 R2 и 2008 за некоторыми незначительными исключениями.

Описание процедур, включающие действия, которые различны для Windows Server 2003 можно найти в [восстановление леса с контроллерами домена Windows Server 2003](AD-Forest-Recovery-Windows-Server-2003.md).  

Ниже приведен список процедур, которые используются в резервном копировании и восстановлении контроллеров домена и Active Directory.

- [Резервное копирование полного сервера](AD-Forest-Recovery-Backing-up-a-Full-Server.md)  
- [Резервное копирование данных состояния системы](AD-Forest-Recovery-Backing-up-System-State.md)  
- [Выполнение восстановления всего сервера](AD-Forest-Recovery-Perform-a-Full-Recovery.md)  
- [Выполнение полномочного синхронизации папки SYSVOL с репликацией DFSR](AD-Forest-Recovery-Authoritative-Recovery-SYSVOL.md)
- [Выполняет принудительное восстановление доменных служб Active Directory](AD-Forest-Recovery-Nonauthoritative-Restore.md)  

Эти шаги поясняют, как для выполнения полномочного восстановления SYSVOL в то же время.  

- [Настройка службы DNS-сервера](AD-Forest-Recovery-Configure-DNS.md)  
- [Удаление глобального каталога](AD-Forest-Recovery-Remove-GC.md)  
- [Возведение значения доступных пулов RID](AD-Forest-Recovery-Raise-RID-Pool.md)  
- [Нарушение текущий пул относительных ИДЕНТИФИКАТОРОВ](AD-Forest-Recovery-Invaildate-RID-Pool.md)  
- [Захват роли хозяина операций](AD-Forest-Recovery-Seizing-Operations-Master-Role.md)  
- [После восстановления](AD-Forest-Recovery-Cleanup.md)
- [Очистка метаданных удаленных для записи контроллеров домена](AD-Forest-Recovery-Cleaning-Metadata.md)  
- [Сброс пароля учетной записи компьютера контроллера домена](AD-Forest-Recovery-Reset-Computer-Account-DC.md)  
- [Сброс пароля krbtgt](AD-Forest-Recovery-Resetting-the-krbtgt-password.md)  
- [Сброс пароля доверия на одной стороне отношения доверия](AD-Forest-Recovery-Reset-Trust.md)  
- [Добавление глобального каталога](AD-Forest-Recovery-Add-GC.md)  
- [Ресурсы для проверки работоспособности репликации](AD-Forest-Recovery-Verify-Replication.md)  

## <a name="next-steps"></a>Следующие шаги

- [Восстановление леса AD — предварительные требования](AD-Forest-Recovery-Prerequisties.md)  
- [Восстановление леса AD — составить план восстановления пользовательских леса](AD-Forest-Recovery-Devising-a-Plan.md)  
- [Восстановление леса AD — определить проблему](AD-Forest-Recovery-Identify-the-Problem.md)
- [Восстановление леса AD — определить способ восстановления](AD-Forest-Recovery-Determine-how-to-Recover.md)
- [Восстановление леса AD - начального восстановления](AD-Forest-Recovery-Perform-initial-recovery.md)  
- [Восстановление леса AD - процедуры](AD-Forest-Recovery-Procedures.md)  
- [Восстановление леса AD — часто задаваемые вопросы](AD-Forest-Recovery-FAQ.md)  
- [Восстановление леса AD — восстановление одного домена в лесу Multidomain](AD-Forest-Recovery-Single-Domain-in-Multidomain-Recovery.md)  
- [Восстановление леса AD - восстановление леса с контроллерами домена Windows Server 2003](AD-Forest-Recovery-Windows-Server-2003.md) 
