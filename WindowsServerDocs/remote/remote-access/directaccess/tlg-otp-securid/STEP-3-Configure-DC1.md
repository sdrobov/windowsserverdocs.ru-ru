---
title: Шаг 3. Настройка DC1
description: 'Эта статья является частью руководства по тестовой лаборатории: демонстрация DirectAccess с проверкой подлинности OTP и RSA SecurID для Windows Server 2016.'
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-da
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 836a2a08-3d22-48d2-873e-80d7e57ebbd6
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 7655208fb537e78839f2b459c8df0e24c0573aa7
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71367555"
---
# <a name="step-3-configure-dc1"></a>Шаг 3. Настройка DC1

>Область применения. Windows Server (Semi-Annual Channel), Windows Server 2016

DC1 выступает в качестве контроллера домена, DNS-сервера и DHCP-сервера для домена corp.contoso.com. Настройте DC1 следующим образом.  
  
## <a name="verify-user1-has-a-user-principal-name-defined-on-dc1"></a>Проверка того, что Пользователь1 имеет имя участника-пользователя, определенное на компьютере DC1  
  
1.  На компьютере DC1 откройте диспетчер сервера и в левой области щелкните **AD DS** . Щелкните правой кнопкой мыши **DC1** и выберите **Active Directory пользователи и компьютеры**. На левой панели разверните **Corp. contoso. ком\усерс**и дважды щелкните Пользователь1.  
  
2.  На вкладке **учетная запись** убедитесь, что для **имени входа пользователя** задано значение Пользователь1. В противном случае введите **Пользователь1** в поле **имя входа пользователя** .  
  
3.  Нажмите кнопку **ОК**. Закройте консоль **Active Directory — пользователи и компьютеры** .  
  


