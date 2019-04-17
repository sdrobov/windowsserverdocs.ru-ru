---
title: "Обновления компонентов служб домена Active Directory"
description: "В этом документе обсуждаются обновления компонентов Доменных службах Active Directory для Windows Server 2012 R2"
author: billmath
ms.author: billmath
manager: femila
ms.date: 09/08/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.assetid: a3a91034-a4da-4ad7-93f8-0cd2ec3e7824
ms.technology: identity-adds
ms.openlocfilehash: 52d3dab542b4250670067e927f42ddf1597fc852
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="active-directory-domain-services-component-updates"></a>Обновления компонентов служб домена Active Directory

>Область применения: Windows Server 2016, Windows Server 2012 R2

В этом модуле содержатся сведения о компонентах, полученных незначительными обновлениями в области служб каталогов и удостоверений.  
  
|Об авторе|  
|--------------------|  
|**Автор:**|Джастин Тернер|  
|**Биография:**|Джастин является старшим инженером эскалации со службами каталогов, находящейся в г. Ирвинг, Техас, США.  Он создал или способствовали большого количества учебных курсов и статей для базы знаний Майкрософт в течение последних 12 лет. Он обучает сотрудников Майкрософт и клиентов новыми архитектурами продуктов, имеет сертификаты Microsoft Certified Master (MCM), Microsoft Certified Trainer (MCT) и содержит Магистр степень в компьютерного образования и Когнитивных систем.|  
|**Участники**|Этот модуль обучения включает вклады *Michiko Short*, *ячейки Дин*, *Alan Jowett*, *Pushpendran меню*, *Yashar Bahman*, *Anoosh Saboori*, *Rashmi Jha*, *Джастин Холл* и *Mauerer Герберт*|  
|**Рецензенты**|Выражаем благодарность следующим специалистам, которые затраченное собственные материал и оставили отзывы: *Seifert Джои*, *Джастин Холл*|  
  
> [!NOTE]  
> Этот материал создан инженером поддержки клиентов Майкрософт и предназначен для опытных администраторов и архитекторов систем, которым нужны более глубокие технические сведения о функциях и решениях в Windows Server 2012 R2, чем обычно предоставляют разделов на TechNet. Однако он не проходил же редактирования этапах, поэтому некоторые формулировки могут быть то, что обычно станицах на сайте TechNet.  
  
### <a name="what-you-will-learn"></a>Тема обучения  
После изучения данного модуля, будут иметь возможность:  
  
-   Объяснять обновления компонентов в области технологий служб каталогов и удостоверений в Windows Server 2012 R2  
  
    -   [Уникальность имен участников-СЛУЖБ и имя участника-пользователя](../../../ad-ds/manage/component-updates/SPN-and-UPN-uniqueness.md)  
  
    -   [Winlogon автоматический перезапуск входа & #40; ARSO & #41;](../../../ad-ds/manage/component-updates/Winlogon-Automatic-Restart-Sign-On--ARSO-.md)  
  
    -   [Аттестация ключа TPM](../../../ad-ds/manage/component-updates/TPM-Key-Attestation.md)  
  
    -   [Резервное копирование ЦС и восстановить командлеты Windows PowerShell](../../../ad-ds/manage/component-updates/CA-Backup-and-Restore-Windows-PowerShell-cmdlets.md)  
  
    -   [Аудит процесса командной строки](../../../ad-ds/manage/component-updates/Command-line-process-auditing.md)  
  
    -   [Защита учетных данных и управление ими](https://technet.microsoft.com/library/dn408190.aspx)  
  
    -   [Обновления компонентов служб каталогов](../../../ad-ds/manage/component-updates/Directory-Services-component-updates.md)  
  
        -   [Режимы работы домена и леса](../../../ad-ds/manage/component-updates/../../../ad-ds/manage/component-updates/Directory-Services-component-updates.md#BKMK_FL)  
  
        -   [Устаревание NTFRS](../../../ad-ds/manage/component-updates/Directory-Services-component-updates.md#BKMK_NTFRS)  
  
        -   [Изменения в оптимизаторе запросов LDAP](../../../ad-ds/manage/component-updates/../../../ad-ds/manage/component-updates/Directory-Services-component-updates.md#BKMK_LDAPQuery)  
  
        -   [Событием 1644](../../../ad-ds/manage/component-updates/Directory-Services-component-updates.md#BKMK_1644)  
  
        -   [Повышение пропускной способности Active Directory репликации](../../../ad-ds/manage/component-updates/../../../ad-ds/manage/component-updates/Directory-Services-component-updates.md#BKMK_ADRepl)  
  


