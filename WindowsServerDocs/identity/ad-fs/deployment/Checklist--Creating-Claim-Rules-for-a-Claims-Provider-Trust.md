---
ms.assetid: 503733f8-be0c-429c-81f0-cd4205e8b118
title: Контрольный список - доверять Создание правил для утверждений для поставщика утверждений
description: ''
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: 708919691f88cc49d1f2bd74d8f4255e1a854353
ms.sourcegitcommit: 0b5fd4dc4148b92480db04e4dc22e139dcff8582
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66192387"
---
# <a name="checklist-creating-claim-rules-for-a-claims-provider-trust"></a>Контрольный список: Создание правил для утверждений для поставщика утверждений доверия


Этот контрольный список содержит задачи планирования, разработки, и развертывания правил для утверждений, которые связаны с поставщиком утверждений доверия службы федерации Active Directory \(AD FS\).  
  
> [!NOTE]  
> Выполните по порядку задачи в контрольном списке. После выполнения всех шагов процедуры, на которую указывает ссылка, следует вернуться к этому разделу и продолжить выполнение оставшихся задач контрольного списка.  
  
![Создание правил утверждений](media/2b05dce3-938f-4168-9b8f-1f4398cbdb9b.gif)**контрольный список: Создание набора правил утверждений для отношения доверия поставщика утверждений**  
  
||Задача|Ссылка|  
|-|--------|-------------|  
|![Создание правил для утверждений](media/icon_checkboxo.gif)|Просмотрите основные понятия об утверждениях, правила утверждений, утверждения наборов правил и утверждений шаблонов правил и как они связаны с федеративного отношения доверия.|![Создание правил утверждений](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[The Role of Claims](../../ad-fs/technical-reference/The-Role-of-Claims.md)<br /><br />![Создание правил утверждений](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[The Role of Claim Rules](../../ad-fs/technical-reference/The-Role-of-Claim-Rules.md)|  
|![Создание правил для утверждений](media/icon_checkboxo.gif)|Основные понятия о том, как утверждение проходит через все этапы конвейера выдачи утверждений и как правила обрабатываются подсистемой выдачи утверждений.|![Создание правил утверждений](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[The Role of the Claims Pipeline](../../ad-fs/technical-reference/The-Role-of-the-Claims-Pipeline.md)<br /><br />![Создание правил утверждений](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[The Role of the Claims Engine](../../ad-fs/technical-reference/The-Role-of-the-Claims-Engine.md)|  
|![Создание правил для утверждений](media/icon_checkboxo.gif)|Для эффективного планирования и реализации исходящие утверждения, которые будут выдаваться через это отношение доверия с поставщиком утверждений, определяют ли необходимы одно или несколько правил утверждений и также утверждение, правила, которые следует использовать с этим отношением доверия поставщика утверждений.|![Создание правил утверждений](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[определить тип из утверждения шаблон правила для использования](../../ad-fs/technical-reference/Determine-the-Type-of-Claim-Rule-Template-to-Use.md)|  
|![Создание правил для утверждений](media/icon_checkboxo.gif)|Просмотрите основные понятия о создать одно утверждение правило на другое и об использовании языка правил утверждений для предоставления более сложная логика, чем стандартные правила для обеспечения желаемого результата в выходных данных идеально утверждение набора.|![Создание правил утверждений](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[использование Pass Through or Filter правила утверждения](../../ad-fs/technical-reference/When-to-Use-a-Pass-Through-or-Filter-Claim-Rule.md)<br /><br />![Создание правил утверждений](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[когда следует использовать правила преобразования утверждения](../../ad-fs/technical-reference/When-to-Use-a-Transform-Claim-Rule.md)<br /><br />![Создание правил утверждений](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[необходимости использования Send LDAP Attributes as Claims Rule](../../ad-fs/technical-reference/When-to-Use-a-Send-LDAP-Attributes-as-Claims-Rule.md)<br /><br />![Создание правил утверждений](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[необходимости использования Send Group Membership, как правило утверждения](../../ad-fs/technical-reference/When-to-Use-a-Send-Group-Membership-as-a-Claim-Rule.md)<br /><br />![Создание правил утверждений](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[необходимости использования настраиваемого правила утверждения](../../ad-fs/technical-reference/When-to-Use-a-Custom-Claim-Rule.md)<br /><br />![Создание правил утверждений](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[роль языка правил утверждений](../../ad-fs/technical-reference/The-Role-of-the-Claim-Rule-Language.md)|  
|![Создание правил для утверждений](media/icon_checkboxo.gif)|Описания утверждения должны создаваться, если еще не существует, будет соответствовать потребностям вашей организации. AD FS поставляется со стандартным набором описаний утверждений, которые отображаются в консоли управления AD FS\-в.|![Создание правил утверждений](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Добавление описания утверждения](../../ad-fs/operations/Add-a-Claim-Description.md)|  
|![Создание правил для утверждений](media/icon_checkboxo.gif)|В зависимости от потребностей вашей организации создайте один или несколько правил для утверждений для набора правил преобразования приемки, связанный с этим отношением доверия поставщика утверждений, чтобы соответствующим образом будут выдаваться утверждений.|![Создание правил утверждений](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[создать правило, чтобы пропуск или Фильтрация входящего утверждения](../../ad-fs/operations/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim.md)<br /><br />![Создание правил утверждений](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[создать правило, чтобы отправлять атрибуты LDAP как утверждения](../../ad-fs/operations/Create-a-Rule-to-Send-LDAP-Attributes-as-Claims.md)<br /><br />![Создание правил утверждений](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[создать правило, чтобы отправлять членство в группе как утверждение](../../ad-fs/operations/Create-a-Rule-to-Send-Group-Membership-as-a-Claim.md)<br /><br />![Создание правил утверждений](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[создайте правило для преобразования входящего утверждения](../../ad-fs/operations/Create-a-Rule-to-Transform-an-Incoming-Claim.md)<br /><br />![Создание правил утверждений](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Создание правила для отправки утверждений метода проверки подлинности](../../ad-fs/operations/Create-a-Rule-to-Send-an-Authentication-Method-Claim.md)<br /><br />![Создание правил утверждений](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Создание правила для отправки с AD FS 1.x, совместимый утверждения](../../ad-fs/operations/Create-a-Rule-to-Send-an-AD-FS-1x-Compatible-Claim.md)<br /><br />![Создание правил утверждений](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[создать правило, чтобы отправлять утверждения с помощью настраиваемого правила](../../ad-fs/operations/Create-a-Rule-to-Send-Claims-Using-a-Custom-Rule.md)|  
  

