---
title: Настройка HGS для обмена данными по протоколу HTTPS
ms.prod: windows-server
ms.topic: article
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: de57a4026a33561760ad36fd78d732352b3aa340
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856847"
---
# <a name="configure-hgs-for-https-communications"></a>Настройка HGS для обмена данными по протоколу HTTPS

>Область применения: Windows Server 2019, Windows Server (половина ежегодного канала), Windows Server 2016

По умолчанию при инициализации сервера HGS он настраивает веб-сайты IIS для обмена данными только по протоколу HTTP.
Все конфиденциальные материалы, передаваемые и из HGS, всегда шифруются с помощью шифрования на уровне сообщений. Однако если требуется более высокий уровень безопасности, можно также включить протокол HTTPS, настроив для HGS SSL-сертификат.

[!INCLUDE [Configure HTTPS](../../../includes/configure-hgs-for-https.md)] 

