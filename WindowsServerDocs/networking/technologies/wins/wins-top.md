---
title: Служба WINS
description: Этот раздел содержит сведения о списании WINS и использовании DNS для служб разрешения имен в сети.
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: 32eabe7d-1130-4001-a79a-8ddb31993e5b
ms.author: pashort
author: shortpatti
ms.openlocfilehash: bbc1871d29021aa3c99f14368a4711dac63f4cee
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59843635"
---
#  <a name="windows-internet-name-service-wins"></a>Служба WINS

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

WINS — это традиционная служба регистрации и разрешения имен компьютеров, которая сопоставляет NetBIOS-имена компьютеров с IP-адресами.

Если у вас еще нет WINS, развернутый в вашей сети, не развертывание WINS - вместо этого, развертывание доменных имен \(DNS\). DNS также предоставляет службы регистрации и разрешения имени компьютера и включает много дополнительных преимуществ по сравнению с WINS, такие как интеграция с доменными службами Active Directory.

Дополнительные сведения см. в разделе [доменных имен (DNS)](https://docs.microsoft.com/windows-server/networking/dns/dns-top)

Если вы уже развернули WINS в сети, рекомендуется размещать DNS, а затем списать WINS.
