---
title: Шаг 3 Настройка DC1
description: Этот раздел входит руководство по лаборатории тестирования — продемонстрировать DirectAccess с проверкой подлинности OTP и RSA SecurID для Windows Server 2016
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: networking-da
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 836a2a08-3d22-48d2-873e-80d7e57ebbd6
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 338e214ac10796d3f9864aef74190f2d27f173b7
ms.sourcegitcommit: afb0602767de64a76aaf9ce6a60d2f0e78efb78b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/20/2019
ms.locfileid: "67281358"
---
# <a name="step-3-configure-dc1"></a>Шаг 3 Настройка DC1

>Область применения. Windows Server (полугодовой канал), Windows Server 2016

DC1 выступает в качестве контроллера домена, DNS-сервер и DHCP-сервер для домена corp.contoso.com. Настройте DC1 следующим образом:  
  
## <a name="verify-user1-has-a-user-principal-name-defined-on-dc1"></a>Убедитесь, что пользователь User1 имеет имя участника-пользователя, определенные на DC1  
  
1.  На DC1 откройте диспетчер серверов и нажмите кнопку **AD DS** в левой области. Щелкните правой кнопкой мыши **DC1** и выберите **Active Directory — пользователи и компьютеры**. В левой области разверните **corp.contoso.com\Users**и дважды щелкните пользователя User1.  
  
2.  На **учетной записи** вкладке убедитесь, что **имя входа пользователя** задано значение User1. Если это не так, затем введите **User1** в **имя входа пользователя** поля.  
  
3.  Нажмите кнопку **ОК**. Закройте консоль **Active Directory — пользователи и компьютеры** .  
  


