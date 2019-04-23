---
title: Обновления компонентов доменных служб Active Directory
description: В этом документе рассматриваются обновления компонентов в Доменных службах Active Directory для Windows Server 2012 R2
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 09/08/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.assetid: a3a91034-a4da-4ad7-93f8-0cd2ec3e7824
ms.technology: identity-adds
ms.openlocfilehash: 300bf7dafe0ef0ede754302f2c0aa8c36a7adbfd
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59889885"
---
# <a name="active-directory-domain-services-component-updates"></a>Обновления компонентов доменных служб Active Directory

>Область применения. Windows Server 2016, Windows Server 2012 R2

В этом модуле содержатся сведения о незначительно обновленных компонентах в области служб каталогов и удостоверений.  
  
|Об авторе|  
|--------------------|  
|**Автор**|Джастин Тернер (Justin Turner)|  
|**Биография**|Джастин является старшим инженером по решению особо сложных проблем в группе по работе со службами каталогов, находящейся в г. Ирвинг, Техас, США.  В течение последних 12 лет он принимал участие в разработке большого количества учебных курсов и статей для базы знаний Майкрософт. Он обучает работе с сотрудниками корпорации Майкрософт и клиентов с новыми архитектурами продуктов, имеет сертификаты Microsoft Certified Master (MCM), Microsoft Certified Trainer (MCT) и содержит Магистр наук угол в компьютерного образования и Когнитивных систем.|  
|**Участники**|В разработку этого модуля обучения внесли вклад *Мичико Шорт (Michiko Short)*, *Дин Уэллс (Dean Wells)*, *Alan Jowett (Алан Жове)*, *Manu Pushpendran (Ману Пушпендран)*, *Yashar Bahman (Яшар Бахман)*, *Anoosh Saboori (Ануш Сабури)*, *Рашми Джа (Rashmi Jha)*, *Джастин Холл (Justin Hall)* и *Герберт Маурер (Herbert Mauerer)*.|  
|**Рецензенты**|Выражаем благодарность ниже, которые потратили собственное время проверки и отправки отзывов: *Джо Seifert*, *Джастин Холл*|  
  
> [!NOTE]  
> Этот материал создан инженером службы поддержки клиентов Майкрософт и предназначен для опытных администраторов и архитекторов систем, которым нужны более глубокие технические сведения о функциях и решениях в Windows Server 2012 R2, а не обычная информация, доступная в статьях на сайте TechNet. Однако он не был отредактирован согласно требованиям сайта, поэтому некоторые формулировки могут быть не такими выверенными, как на станицах TechNet.  
  
### <a name="what-you-will-learn"></a>Тема обучения  
После изучения данного модуля вы сможете:  
  
-   объяснять обновления компонентов в области технологий служб каталогов и удостоверений в Windows Server 2012 R2.  
  
    -   [Уникальность имен участников-служб и участников-пользователей](../../../ad-ds/manage/component-updates/SPN-and-UPN-uniqueness.md)  
  
    -   [Winlogon автоматический перезапуск вход &#40;ARSO&#41;](../../../ad-ds/manage/component-updates/Winlogon-Automatic-Restart-Sign-On--ARSO-.md)  
  
    -   [Аттестация ключей доверенного платформенного модуля (TPM Key) Attestation](../../../ad-ds/manage/component-updates/TPM-Key-Attestation.md)  
  
    -   [Командлеты Windows PowerShell для резервного копирования и восстановления ЦС](../../../ad-ds/manage/component-updates/CA-Backup-and-Restore-Windows-PowerShell-cmdlets.md)  
  
    -   [Аудит процесса командной строки](../../../ad-ds/manage/component-updates/Command-line-process-auditing.md)  
  
    -   [Защита учетных данных и управление ими](https://technet.microsoft.com/library/dn408190.aspx)  
  
    -   [Обновления компонентов служб каталогов](../../../ad-ds/manage/component-updates/Directory-Services-component-updates.md)  
  
        -   [Режимы работы домена и леса](../../../ad-ds/manage/component-updates/../../../ad-ds/manage/component-updates/Directory-Services-component-updates.md#BKMK_FL)  
  
        -   [Устаревание NTFRS](../../../ad-ds/manage/component-updates/Directory-Services-component-updates.md#BKMK_NTFRS)  
  
        -   [Изменения в оптимизаторе запросов LDAP](../../../ad-ds/manage/component-updates/../../../ad-ds/manage/component-updates/Directory-Services-component-updates.md#BKMK_LDAPQuery)  
  
        -   [Улучшения, связанные с событием 1644](../../../ad-ds/manage/component-updates/Directory-Services-component-updates.md#BKMK_1644)  
  
        -   [Повышение пропускной способности репликации Active Directory](../../../ad-ds/manage/component-updates/../../../ad-ds/manage/component-updates/Directory-Services-component-updates.md#BKMK_ADRepl)  
  


