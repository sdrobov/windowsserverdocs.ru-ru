---
title: Настройка HGS связь по протоколу Https
ms.custom: na
ms.prod: windows-server-threshold
ms.topic: article
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 83529a5bdb4547b9881bb307a8a4cd526552d02c
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59829005"
---
# <a name="configure-hgs-for-https-communications"></a>Настройка HGS связь по протоколу HTTPS

>Относится к: Windows Server 2019 г., Windows Server (полугодовой канал), Windows Server 2016

По умолчанию при инициализации сервера HGS он настраивает веб-сайтов IIS для взаимодействия только протокол HTTP.
Всех конфиденциальных материалов, передаваемых в и из HGS всегда шифруются с помощью шифрования на уровне сообщения, однако при желании более высокий уровень безопасности можно также включить HTTPS, настройке HGS с SSL-сертификат.

[!INCLUDE [Configure HTTPS](../../../includes/configure-hgs-for-https.md)] 

