---
title: Шаг 3. Проверка развертывания
description: Эта статья является частью инструкции по добавлению DirectAccess в существующее развертывание удаленного доступа (VPN) для Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-da
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 43ac612e-2e77-418c-8171-ebb2086b7cb6
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 82acca0309835149ca35676784120b3130e72a54
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71388704"
---
# <a name="step-3-verify-the-deployment"></a>Шаг 3. Проверка развертывания

>Область применения. Windows Server (Semi-Annual Channel), Windows Server 2016

В этом разделе описывается, как проверить правильность настройки развертывания DirectAccess.  
  
### <a name="to-verify-access-to-internal-resources-through-directaccess"></a>Проверка доступа к внутренним ресурсам с помощью DirectAccess  
  
1.  Подключите клиентский компьютер с DirectAccess к корпоративной сети и получите групповую политику.  
  
2.  В области уведомлений щелкните значок **Сетевые подключения** , чтобы получить доступ к диспетчеру мультимедиа DA.  
  
3.  Щелкните **Подключение DirectAccess**. Будет отображено состояние подключения — **Подключено локально**.  
  
4.  Подключите клиентский компьютер к внешней сети и попытайтесь получить доступ к внутренним ресурсам.  
  
    Вам должны быть доступны все корпоративные ресурсы.  
  


