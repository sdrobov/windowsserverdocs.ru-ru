---
ms.assetid: e6b72a80-e8b7-4305-be0c-0a290f468d36
title: Развертывание доменных служб Active Directory в организации Windows Server 2003
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 033973ad7a726054f6c47c7154fa54a3767beab4
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59816365"
---
# <a name="deploying-ad-ds-in-a-windows-server-2003-organization"></a>Развертывание доменных служб Active Directory в организации Windows Server 2003

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Если ваша организация в настоящее время работает под управлением Windows Server 2003 Active Directory, можно развернуть службы Windows Server 2008 Active Directory домена (AD DS), либо выполнив обновление на месте некоторых или всех контроллеров домена операционных систем на  Windows Server 2008 или путем введения контроллеров домена под управлением Windows Server 2008 в вашей среде.  
  
Чтобы добавить контроллер домена под управлением Windows Server 2008 в существующий домен Windows Server 2003 Active Directory, необходимо запустить **adprep**, средство командной строки. Adprep расширяет схему AD DS, обновление дескрипторов безопасности по умолчанию выбранных объектов и добавляет новые объекты каталога, требуемые для некоторых приложений. Adprep доступен на установочном диске Windows Server 2008 (\sources\adprep\adprep.exe). Дополнительные сведения см. в разделе Adprep ([https://go.microsoft.com/fwlink/?LinkId=99215](https://go.microsoft.com/fwlink/?LinkId=99215)).  
  
Ниже показан инструкциям по развертыванию Windows Server 2008 AD DS в сетевой среде, которая выполняется в данный момент Windows Server 2003 Active Directory.  
  
![развертывание в организации windows 2003](media/Deploying-AD-DS-in-a-Windows-Server-2003-Organization/900c4eee-1119-4a9a-9310-755597428b71.gif)  
  
> [!NOTE]  
> Если вы хотите установите режим работы домена или леса до Windows Server 2008, все контроллеры домена в вашей среде необходимо запустить в операционной системе Windows Server 2008.  
  
Консолидация доменах и доменах учетных записей, которые обновляются на месте в среде Windows Server 2003, так как часть развертывания Windows Server 2008 AD DS может потребоваться между лесами или реструктуризации доменов леса. Реструктуризация доменов AD DS между лесами позволяет сократить сложность представлением организации в AD DS, и он способствует снижению административных затрат. Реструктуризация доменов AD DS в пределах леса помогает уменьшить административную нагрузку для вашей организации, сократить объем трафика репликации, уменьшая объем Администрирование пользователей и групп, является обязательным и упростив Администрирование группы Политика. Дополнительные сведения см. в разделе ADMT v3.1 руководство по миграции ([https://go.microsoft.com/fwlink/?LinkId=93678](https://go.microsoft.com/fwlink/?LinkId=93678)).  
  
Список подробных задач, которые можно использовать для планирования и развертывания AD DS в организации, на котором работает Windows Server 2003 Active Directory, см. в разделе [контрольный список: Развертывание AD DS в организации Windows Server 2003](https://technet.microsoft.com/library/cc771407.aspx).  
  


