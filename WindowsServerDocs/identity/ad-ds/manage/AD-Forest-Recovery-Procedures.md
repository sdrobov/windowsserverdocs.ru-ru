---
title: "Восстановление леса AD — процедуры"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 07/07/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.assetid: 47a471fb-3b0b-4aa8-8525-1c92d0d51e93
ms.technology: identity-adfs
ms.openlocfilehash: 91e3954c05fe3cd12d35b5db91afd29fb3a31e00
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2017
---
# <a name="ad-forest-recovery---procedures"></a>Восстановление леса AD — процедуры


>Область применения: Windows Server 2016, Windows Server 2012 и 2012 R2, Windows Server 2008 и 2008 R2

В этом разделе содержатся процедуры, связанные с процессом восстановления леса. Процедуры применимы для Windows Server 2016, 2012 R2, 2012 и также применимы к Windows Server 2008 R2 и 2008 с некоторыми незначительными исключениями. 

Процедуры, которые включают действия, которые зависят от Windows Server 2003 можно найти в [восстановления леса с контроллеров домена Windows Server 2003](AD-Forest-Recovery-Windows-Server-2003.md).  

Ниже приведен список процедур, которые используются в резервное копирование и восстановление контроллеров домена и Active Directory.
  
-   [Резервное копирование всего сервера](AD-Forest-Recovery-Backing-up-a-Full-Server.md)  
-   [Резервное копирование данных состояния системы](AD-Forest-Recovery-Backing-up-System-State.md)  
-   [Выполнение восстановления полного сервера](AD-Forest-Recovery-Perform-a-Full-Recovery.md)  
-   [Выполнение заслуживающих доверия синхронизацию SYSVOL, реплицированного DFSR](AD-Forest-Recovery-Authoritative-Recovery-SYSVOL.md)
-   [Выполнение непринудительное восстановление доменных служб Active Directory](AD-Forest-Recovery-Nonauthoritative-Restore.md)  
  
     Следующие шаги описывают выполните принудительное восстановление SYSVOL, в то же время.  
-   [Настройка службы DNS-сервера](AD-Forest-Recovery-Configure-DNS.md)  
-   [Удаление глобального каталога](AD-Forest-Recovery-Remove-GC.md)  
-   [Вызов значение доступные пулы RID](AD-Forest-Recovery-Raise-RID-Pool.md)  
-   [Прекращение действия текущий пул относительных ИДЕНТИФИКАТОРОВ](AD-Forest-Recovery-Invaildate-RID-Pool.md)  
-   [Захват роли хозяина операций](AD-Forest-Recovery-Seizing-Operations-Master-Role.md)  
-   [После восстановления](AD-Forest-Recovery-Cleanup.md)
-   [Очистка метаданных удаленных для записи контроллеров домена](AD-Forest-Recovery-Cleaning-Metadata.md)  
-   [Сброс пароля учетной записи компьютера контроллера домена](AD-Forest-Recovery-Reset-Computer-Account-DC.md)  
-   [Смена пароля krbtgt](AD-Forest-Recovery-Resetting-the-krbtgt-password.md)  
-   [Сброс пароля доверия с одной стороны отношения доверия](AD-Forest-Recovery-Reset-Trust.md)  
-   [Добавление глобального каталога](AD-Forest-Recovery-Add-GC.md)  
-   [Ресурсы, чтобы убедиться, что репликация работает](AD-Forest-Recovery-Verify-Replication.md)  
  
  
## <a name="next-steps"></a>Дальнейшие действия
-   [Восстановление леса AD - предварительные требования](AD-Forest-Recovery-Prerequisties.md)  
-   [Восстановление леса AD — разработки план восстановления пользовательских леса](AD-Forest-Recovery-Devising-a-Plan.md)  
- [Восстановление леса AD — выявление проблемы](AD-Forest-Recovery-Identify-the-Problem.md)
-   [Восстановление леса AD — определить, как восстановить](AD-Forest-Recovery-Determine-how-to-Recover.md)
-   [Восстановление леса AD — выполнения начальной восстановления](AD-Forest-Recovery-Perform-initial-recovery.md)  
-   [Восстановление леса AD — процедуры](AD-Forest-Recovery-Procedures.md)  
-   [Восстановление леса AD — вопросы и ответы](AD-Forest-Recovery-FAQ.md)  
-   [Восстановление леса AD — восстановление одного домена в лесу Multidomain](AD-Forest-Recovery-Single-Domain-in-Multidomain-Recovery.md)  
-   [Восстановление леса AD — восстановление леса с контроллеров домена Windows Server 2003](AD-Forest-Recovery-Windows-Server-2003.md) 
