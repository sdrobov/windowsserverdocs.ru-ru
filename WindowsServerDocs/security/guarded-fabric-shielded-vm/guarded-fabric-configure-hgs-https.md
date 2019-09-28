---
title: Настройка HGS для обмена данными по протоколу HTTPS
ms.custom: na
ms.prod: windows-server
ms.topic: article
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: f0cbf6a6dc1970499758a6a48bfaadb95c464ec1
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71403679"
---
# <a name="configure-hgs-for-https-communications"></a>Настройка HGS для обмена данными по протоколу HTTPS

>Относится к: Windows Server 2019, Windows Server (половина ежегодного канала), Windows Server 2016

По умолчанию при инициализации сервера HGS он настраивает веб-сайты IIS для обмена данными только по протоколу HTTP.
Все конфиденциальные материалы, передаваемые и из HGS, всегда шифруются с помощью шифрования на уровне сообщений. Однако если требуется более высокий уровень безопасности, можно также включить протокол HTTPS, настроив для HGS SSL-сертификат.

[!INCLUDE [Configure HTTPS](../../../includes/configure-hgs-for-https.md)] 

