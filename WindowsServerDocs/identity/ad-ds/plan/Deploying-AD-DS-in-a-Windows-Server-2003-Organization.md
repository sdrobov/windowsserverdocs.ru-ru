---
ms.assetid: e6b72a80-e8b7-4305-be0c-0a290f468d36
title: Развертывание доменных служб Active Directory в организации Windows Server 2003
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: d377e2903d23db9b518323ae7bf5e5a39e40fade
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80822627"
---
# <a name="deploying-ad-ds-in-a-windows-server-2003-organization"></a>Развертывание доменных служб Active Directory в организации Windows Server 2003

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Если ваша организация в настоящее время работает под управлением Windows Server 2003 Active Directory, можно развернуть Windows Server 2008 домен Active Directory Services (AD DS), выполнив обновление на месте некоторых или всех операционных систем контроллеров домена до Windows Server 2008 или путем введения контроллеров домена под управлением Windows Server 2008 в вашу среду.  
  
Перед добавлением контроллера домена под управлением Windows Server 2008 в существующий домен Active Directory Windows Server 2003 необходимо запустить средство **adprep**, запускаемое из командной строки. Adprep расширяет схему AD DS, обновляет дескрипторы безопасности по умолчанию для выбранных объектов и добавляет новые объекты каталога в соответствии с требованиями некоторых приложений. Средство Adprep доступно на установочном диске Windows Server 2008 (\саурцес\адпреп\адпреп.ЕКСЕ). Дополнительные сведения см. в разделе Adprep ([https://go.microsoft.com/fwlink/?LinkId=99215](https://go.microsoft.com/fwlink/?LinkId=99215)).  
  
На следующем рисунке показаны шаги для развертывания Windows Server 2008 AD DS в сетевой среде, в которой в настоящее время работает Windows Server 2003 Active Directory.  
  
![развертывание в Организации Windows 2003](media/Deploying-AD-DS-in-a-Windows-Server-2003-Organization/900c4eee-1119-4a9a-9310-755597428b71.gif)  
  
> [!NOTE]  
> Если вы хотите задать функциональный уровень домена или леса для Windows Server 2008, все контроллеры домена в среде должны работать под управлением операционной системы Windows Server 2008.  
  
Консолидация доменов ресурсов и доменов учетных записей, которые были обновлены на месте, из среды Windows Server 2003 в составе развертывания AD DS Windows Server 2008 может потребовать реструктуризации домена в пределах леса или леса. Реструктуризация AD DS доменов между лесами помогает сократить сложность представления Организации в AD DS и помогает снизить связанные административные затраты. Реструктуризация AD DS доменов в пределах леса помогает уменьшить административные расходы на организацию за счет сокращения трафика репликации, уменьшения необходимого количества пользователей и групп, а также упрощения администрирования групповая политика. Дополнительные сведения см. в статье миграция по миграции ADMT версии 3.1 ([https://go.microsoft.com/fwlink/?LinkId=93678](https://go.microsoft.com/fwlink/?LinkId=93678)).  
  
Список подробных задач, которые можно использовать для планирования и развертывания AD DS в Организации, работающей под Windows Server 2003 Active Directory, см. [в разделе Контрольный список: развертывание AD DS в Организации Windows server 2003](https://technet.microsoft.com/library/cc771407.aspx).  
  


