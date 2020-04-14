---
title: Шаг 3. Проверка развертывания
description: Эта статья является частью инструкции по добавлению DirectAccess в существующее развертывание удаленного доступа (VPN) для Windows Server 2016.
manager: brianlic
ms.prod: windows-server
ms.technology: networking-da
ms.topic: article
ms.assetid: 43ac612e-2e77-418c-8171-ebb2086b7cb6
ms.author: lizross
author: eross-msft
ms.openlocfilehash: b187d017a3cf2865a92d95a8ae93bec11ff457f0
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80859537"
---
# <a name="step-3-verify-the-deployment"></a>Шаг 3. Проверка развертывания

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

В этом разделе описывается, как проверить правильность настройки развертывания DirectAccess.  
  
### <a name="to-verify-access-to-internal-resources-through-directaccess"></a>Проверка доступа к внутренним ресурсам с помощью DirectAccess  
  
1.  Подключите клиентский компьютер с DirectAccess к корпоративной сети и получите групповую политику.  
  
2.  В области уведомлений щелкните значок **Сетевые подключения** , чтобы получить доступ к диспетчеру мультимедиа DA.  
  
3.  Щелкните **Подключение DirectAccess**. Будет отображено состояние подключения — **Подключено локально**.  
  
4.  Подключите клиентский компьютер к внешней сети и попытайтесь получить доступ к внутренним ресурсам.  
  
    Вам должны быть доступны все корпоративные ресурсы.  
  


