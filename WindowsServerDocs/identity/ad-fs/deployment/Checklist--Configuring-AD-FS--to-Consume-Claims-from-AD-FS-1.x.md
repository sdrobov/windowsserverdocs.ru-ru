---
ms.assetid: e7f9e518-2d5d-4a0d-9147-34e1304f42ac
title: "Контрольный список - Настройка AD FS для использования утверждений из AD FS 1.x"
description: 
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: fe99487d3a770547af36f69722b442d0e2cbb8b1
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="checklist-configuring-ad-fs--to-consume-claims-from-ad-fs-1x"></a>Контрольный список: Настройка AD FS для использования утверждений из AD FS 1.x

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012
  
## <a name="checklist-configuring-ad-fs-to-consume-claims-from-ad-fs-1x"></a>Контрольный список: Настройка AD FS для использования утверждений из AD FS 1.x  
Этот контрольный список содержит задачи, которые необходимы для настройки вашей службы федерации Active Directory \(AD FS\) службы федерации, в Windows Server 2012 принимать утверждения, отправляемые с AD FS 1. *x* службы федерации.  
  
> [!NOTE]  
> Задачи в контрольном списке в порядке. Перехода по ссылке процедуры, вернитесь к данном разделу, после выполнения действия, описанные в этой процедуре, чтобы продолжить выполнение оставшихся задач контрольного списка.  
  
![использования утверждений из AD FS](media/2b05dce3-938f-4168-9b8f-1f4398cbdb9b.gif)**контрольный список: настройка AD FS для использования утверждений из AD FS 1.x**  
  
||Задача|Справочник по|  
|-|--------|-------------|  
|![использования утверждений из AD FS](media/icon_checkboxo.gif)|Планирование взаимодействия между AD FS в Windows Server 2012 и предыдущие версии AD FS и узнать больше о идентификатор имени типа утверждения.|![использования утверждений из AD FS](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[планирование взаимодействия с AD FS 1.x](https://technet.microsoft.com/library/ff678040.aspx)|  
|![использования утверждений из AD FS](media/icon_checkboxo.gif)|Может взаимодействовать с предыдущей версии AD FS, необходимо сначала создать отношение доверия поставщика утверждений в службу федерации AD FS. **Примечание:** не удается создать отношение доверия с AD FS 1. *x* службы федерации с помощью метаданных федерации.<br /><br />При настройке отношения доверия, выполнив процедуру в ссылку справа, необходимо выполнить следующие в мастер добавления поставщиков утверждений доверия для данного отношения доверия с взаимодействие с AD FS 1. *x* службы федерации:<br /><br />1. на **Выбор источника данных** выберите **доверия ввод данных о проверяющей стороной вручную**.<br />2. на **выберите профиль** выберите **профиль AD FS 1.0 и 1.1**.<br />3. на **настроить URL-адрес** в разделе **URL-адрес пассивного наличия WS-Federation**, тип **URL-адрес конечной точки службы федерации** согласно определению в AD FS 1. *x* службы федерации партнера.<br />4. на **Настройка идентификаторов** в разделе **идентификатор отношения доверия поставщика утверждений**, тип **URI службы федерации** согласно определению в AD FS 1. *x* службы федерации партнера.|![использования утверждений из AD FS](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[с поставщиком утверждений доверия вручную создать](../../ad-fs/operations/Create-a-Claims-Provider-Trust.md)|  
|![использования утверждений из AD FS](media/icon_checkboxo.gif)|На доверия с поставщиком утверждений, созданную ранее, необходимо создать правило для утверждений, будет выполняться утверждения, входящие в AD FS 1.x Federation Service пропуска, фильтрации и преобразования их в тип утверждения идентификатора имени.<br /><br />Когда тип утверждения идентификатора имени передается через, фильтровать или преобразовать, его можно использовать в качестве входных данных другой правило или правила, чтобы понять и используемые службой федерации AD FS в Windows Server 2012.|![использования утверждений из AD FS](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[создать правила для отправки AD FS 1.x утверждения, совместимые](../../ad-fs/operations/Create-a-Rule-to-Send-an-AD-FS-1x-Compatible-Claim.md)|  
|![использования утверждений из AD FS](media/icon_checkboxo.gif)|Обратитесь к администратору AD FS 1. *x* службы федерации и имеют администратор AD FS 1. *x* службы федерации настроить новое отношение доверия с партнером ресурсов. Также можно найти с помощью URI службы федерации, администратор \ (в properties\ службы федерации), URL-адрес конечной точки службы федерации и экспортированные token\ подписи файла сертификата \ (с помощью открытого ключа only\). Администратор должен этих элементов, чтобы настроить отношение доверия.|N\/A|  
  
