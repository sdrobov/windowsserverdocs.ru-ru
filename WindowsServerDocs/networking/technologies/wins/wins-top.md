---
title: Служба WINS (WINS)
description: Этот раздел содержит сведения о списании WINS и с помощью DNS-сервера для службы разрешения имен в сети.
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: 32eabe7d-1130-4001-a79a-8ddb31993e5b
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 5a3d132ada7b1ede83b046499058399a9da12190
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
#  <a name="windows-internet-name-service-wins"></a>Служба WINS (WINS)

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

Службы Windows Internet Name службы (WINS) является старый компьютер имя регистрации и разрешения службой, которая сопоставляет NetBIOS-имена компьютеров в IP-адреса.

Если вы еще не содержат WINS развернута в сети, не вместо развертывание WINS -, а развертывание \(DNS\) доменных имен. DNS также обеспечивает служб регистрации и разрешения имени компьютера и включает многие дополнительные преимущества по сравнению с WINS, таких как интеграция с доменными службами Active Directory.

Дополнительные сведения см. в разделе [доменных имен (DNS)](https://docs.microsoft.com/windows-server/networking/dns/dns-top)

Если вы уже развернули WINS в сети, рекомендуется развертывать DNS и затем вывести из эксплуатации WINS.
