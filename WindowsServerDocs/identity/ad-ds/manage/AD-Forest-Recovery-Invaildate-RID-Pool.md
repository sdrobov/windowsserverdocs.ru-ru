---
title: Восстановление леса AD — непроверяемый пул RID
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 08/09/2018
ms.topic: article
ms.prod: windows-server
ms.assetid: 2f5f84df-bd85-4ca4-bdd3-835bd1d45c11
ms.technology: identity-adds
ms.openlocfilehash: 9e693f6f30fb721897eaaac89b3d146c57e0e63f
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80823927"
---
# <a name="ad-forest-recovery---invalidating-the-current-rid-pool"></a>Восстановление леса Active Directory — непроверка текущего пула RID  

>Область применения: Windows Server 2016, Windows Server 2012 и 2012 R2, Windows Server 2008 и 2008 R2

Используйте следующую процедуру в Windows PowerShell, чтобы сделать недействительным текущий пул RID на контроллере домена. Windows PowerShell по умолчанию включен в Windows Server 2012 и Windows Server 2008 R2, но не в Windows Server 2008, где его необходимо установить с помощью **функции Добавить компоненты**. Его можно [загрузить](https://www.microsoft.com/download/details.aspx?id=20020) для запуска на Windows Server 2003.  

Чтобы убедиться, что команда выполнена успешно, проверьте наличие события с ИДЕНТИФИКАТОРом 16654 (Source-Services — SAM) в системном журнале в Просмотр событий в Windows Server 2012. В более ранних версиях Windows это событие не заносить в журнал.  
  
> [!NOTE]
> После того как пул RID станет недействительным, вы получите сообщение об ошибке при первой попытке создать субъект безопасности (пользователя, компьютер или группу). Попытка создать объект запускает запрос нового пула RID. Повторная попытка операции завершится с ошибкой, так как будет выделен новый пул RID.  
  
## <a name="to-invalidate-the-current-rid-pool"></a>Аннулирование текущего пула RID  
  
- Откройте сеанс Windows PowerShell с повышенными привилегиями, выполните следующую команду и нажмите клавишу ВВОД:  

   ```powershell
   $Domain = New-Object System.DirectoryServices.DirectoryEntry  
   $DomainSid = $Domain.objectSid  
   $RootDSE = New-Object System.DirectoryServices.DirectoryEntry("LDAP://RootDSE")  
   $RootDSE.UsePropertyCache = $false  
   $RootDSE.Put("invalidateRidPool", $DomainSid.Value)  
   $RootDSE.SetInfo()  
   ```  

## <a name="next-steps"></a>Следующие шаги

- [Руководство по восстановлению леса AD](AD-Forest-Recovery-Guide.md)
- [Восстановление леса AD — процедуры](AD-Forest-Recovery-Procedures.md)
