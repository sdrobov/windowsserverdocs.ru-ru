---
title: Служба WINS
description: В этом разделе содержатся сведения о списании WINS и использовании DNS для служб разрешения имен в сети.
manager: brianlic
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: 32eabe7d-1130-4001-a79a-8ddb31993e5b
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 219c313dfeb26319cd5f537df417724de7044648
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71405245"
---
#  <a name="windows-internet-name-service-wins"></a>Служба WINS

>Относится к: Windows Server (Semi-Annual Channel), Windows Server 2016

WINS — это традиционная служба регистрации и разрешения имен компьютеров, которая сопоставляет NetBIOS-имена компьютеров с IP-адресами.

Если вы еще не развернули WINS в своей сети, не развертывайте WINS-вместо этого разверните службу доменных имен \(DNS @ no__t-1. Служба DNS также предоставляет службы регистрации и разрешения имен компьютеров и включает множество дополнительных преимуществ по сравнению с WINS, например интеграцию со службами домен Active Directory.

Дополнительные сведения см. в разделе [Служба доменных имен (DNS)](https://docs.microsoft.com/windows-server/networking/dns/dns-top) .

Если вы уже развернули службу WINS в сети, рекомендуется развернуть DNS, а затем списать службу WINS.
