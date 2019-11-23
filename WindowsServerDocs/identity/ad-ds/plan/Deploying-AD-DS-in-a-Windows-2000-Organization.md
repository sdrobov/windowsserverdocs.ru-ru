---
ms.assetid: 7530cafe-98d7-46c9-95d9-e49d39caa021
title: Развертывание доменных служб Active Directory в организации Windows 2000
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: cad5deb32a31f15277c3e0e985d5b7d9b07856aa
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71408913"
---
# <a name="deploying-ad-ds-in-a-windows-2000-organization"></a>Развертывание доменных служб Active Directory в организации Windows 2000

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Если ваша организация в настоящее время работает под управлением Windows 2000 Active Directory, можно развернуть Windows Server 2008 домен Active Directory Services (AD DS), выполнив обновление на месте некоторых или всех операционных систем контроллеров домена до Windows. Сервер 2008 или Познакомьтесь с контроллерами домена под управлением Windows Server 2008 в своей среде.  
  
Перед добавлением контроллера домена под управлением Windows Server 2008 в существующий домен Active Directory Windows 2000 необходимо запустить программу **adprep**, программу командной строки. Adprep расширяет схему AD DS, обновляет дескрипторы безопасности по умолчанию для выбранных объектов и добавляет новые объекты каталога в соответствии с требованиями некоторых приложений. Средство Adprep доступно на установочном диске Windows Server 2008 (\саурцес\адпреп\адпреп.ЕКСЕ). Дополнительные сведения см. в разделе Adprep ([https://go.microsoft.com/fwlink/?LinkId=99215](https://go.microsoft.com/fwlink/?LinkId=99215)).  
  
> [!NOTE]  
> Если вы хотите выполнить обновление на месте существующего контроллера домена Windows 2000 AD DS до Windows Server 2008, необходимо сначала обновить сервер до Windows Server 2003, а затем обновить его до Windows Server 2008.  
  
На следующем рисунке показаны шаги для развертывания AD DS Windows Server 2008 в сетевой среде, в которой в настоящее время работает Active Directory Windows 2000.  
  
![развертывание в Организации Windows 2000](media/Deploying-AD-DS-in-a-Windows-2000-Organization/ee51218a-a858-49d9-8b99-9986679191c1.gif)  
  
> [!NOTE]  
> Если вы хотите задать функциональный уровень домена или леса для Windows Server 2008, все контроллеры домена в среде должны работать под управлением операционной системы Windows Server 2008.  
  
Консолидация ресурсов и доменов учетных записей, которые были обновлены в среде Windows 2000 в составе развертывания AD DS Windows Server 2008, может потребовать реструктуризации домена в пределах леса или леса. Реструктуризация AD DS доменов между лесами помогает сократить сложность организации и связанные с ней административные расходы. Реструктуризация AD DS доменов в пределах леса помогает уменьшить административные издержки на организацию за счет уменьшения трафика репликации, уменьшения объема необходимого администрирования пользователей и групп, а также упрощения администрирования групповая политика. Дополнительные сведения см. в статье миграция по миграции ADMT версии 3.1 ([https://go.microsoft.com/fwlink/?LinkId=93678](https://go.microsoft.com/fwlink/?LinkId=93678)).  
  
Список подробных задач, которые можно использовать для планирования и развертывания AD DS в Организации, на которой в настоящее время работает Active Directory Windows 2000, см. [в разделе Контрольный список: развертывание AD DS в Организации windows 2000](https://technet.microsoft.com/library/cc732737.aspx).  
  


