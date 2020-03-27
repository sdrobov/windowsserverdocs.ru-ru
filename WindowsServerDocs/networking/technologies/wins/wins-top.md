---
title: Служба имен Windows Internet (WINS)
description: В этом разделе содержатся сведения о списании WINS и использовании DNS для служб разрешения имен в сети.
manager: brianlic
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: 32eabe7d-1130-4001-a79a-8ddb31993e5b
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 54e3f69500ccb3dbf6b2dfe47f6dd035e0a20511
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "80315165"
---
#  <a name="windows-internet-name-service-wins"></a>Служба имен Windows Internet (WINS)

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

WINS — это традиционная служба регистрации и разрешения имен компьютеров, которая сопоставляет NetBIOS-имена компьютеров с IP-адресами.

Если вы еще не развернули WINS в своей сети, не развертывайте WINS-вместо этого разверните службу доменных имен \(\)DNS. Служба DNS также предоставляет службы регистрации и разрешения имен компьютеров и включает множество дополнительных преимуществ по сравнению с WINS, например интеграцию со службами домен Active Directory.

Дополнительные сведения см. в разделе [Служба доменных имен (DNS)](https://docs.microsoft.com/windows-server/networking/dns/dns-top) .

Если вы уже развернули службу WINS в сети, рекомендуется развернуть DNS, а затем списать службу WINS.
