---
ms.assetid: 7530cafe-98d7-46c9-95d9-e49d39caa021
title: Развертывание доменных служб Active Directory в организации Windows 2000
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 5015c0ca2c01fca966927af4207a7e3501d9cd39
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59854285"
---
# <a name="deploying-ad-ds-in-a-windows-2000-organization"></a>Развертывание доменных служб Active Directory в организации Windows 2000

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Если ваша организация в настоящее время работает под управлением Windows 2000 Active Directory, можно развернуть службы Windows Server 2008 Active Directory домена (AD DS), либо выполнив обновление на месте некоторые или все операционные системы контроллеров домена для Windows Server 2008 или путем введения контроллеров домена под управлением Windows Server 2008 в вашей среде.  
  
Чтобы добавить контроллер домена под управлением Windows Server 2008 в существующий домен Windows 2000 Active Directory, необходимо запустить **adprep**, средство командной строки. Adprep расширяет схему AD DS, обновление дескрипторов безопасности по умолчанию выбранных объектов и добавляет новые объекты каталога, требуемые для некоторых приложений. Adprep доступен на установочном диске Windows Server 2008 (\sources\adprep\adprep.exe). Дополнительные сведения см. в разделе Adprep ([https://go.microsoft.com/fwlink/?LinkId=99215](https://go.microsoft.com/fwlink/?LinkId=99215)).  
  
> [!NOTE]  
> Если вы хотите выполнить обновление на месте существующего контроллера домена Windows 2000 AD DS до Windows Server 2008, необходимо сначала обновите сервер до Windows Server 2003 и затем обновить ее до Windows Server 2008.  
  
Ниже показан инструкциям по развертыванию Windows Server 2008 AD DS в сетевой среде, которая выполняется в данный момент Windows 2000 Active Directory.  
  
![развертывание в организации windows 2000](media/Deploying-AD-DS-in-a-Windows-2000-Organization/ee51218a-a858-49d9-8b99-9986679191c1.gif)  
  
> [!NOTE]  
> Если вы хотите установите режим работы домена или леса до Windows Server 2008, все контроллеры домена в вашей среде необходимо запустить в операционной системе Windows Server 2008.  
  
Объединение доменов ресурсов и учетной записи, которые обновляются на месте в среде Windows 2000, как часть вашего AD DS Windows Server 2008 для развертывания может потребоваться между лесами или реструктуризации доменов леса. Реструктуризация доменов AD DS между лесами позволяет сократить сложность организации и связанные затраты на администрирование. Реструктуризация доменов AD DS в лесу позволяет уменьшить объем работы администраторов организации, сократить объем трафика репликации, уменьшая объем Администрирование пользователей и групп, является обязательным и упрощению администрирования Групповая политика. Дополнительные сведения см. в разделе ADMT v3.1 руководство по миграции ([https://go.microsoft.com/fwlink/?LinkId=93678](https://go.microsoft.com/fwlink/?LinkId=93678)).  
  
Список подробных задач, которые можно использовать для планирования и развертывания AD DS в организации, которая выполняется в данный момент Windows 2000 Active Directory, см. в разделе [контрольный список: Развертывание AD DS в Windows 2000 организации](https://technet.microsoft.com/library/cc732737.aspx).  
  


