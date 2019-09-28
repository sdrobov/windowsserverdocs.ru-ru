---
title: Развертывание сервера политики сети
description: Этот раздел содержит ссылки на содержимое развертывания сервера политики сети для Windows Server 2016 и содержит ссылки на дополнительные рекомендации по NPS.
manager: brianlic
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: 6cfb50e0-7088-4295-97c5-14ff8776cbf8
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 33cada472c314088bc1485bab6d9631226b0ffaf
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71405412"
---
# <a name="deploy-network-policy-server"></a>Развертывание сервера политики сети

>Относится к: Windows Server (Semi-Annual Channel), Windows Server 2016

Этот раздел можно использовать для получения сведений о развертывании сервера политики сети.

>[!NOTE]
>Дополнительную документацию по серверу политики сети можно получить с помощью следующих разделов библиотеки.  
>- [начало работы с сервером политики сети](nps-getstart-top.md)
>- [Планирование сервера политики сети](nps-plan-top.md)
>- [Управление сервером политики сети](nps-manage-top.md)

В сетевом руководству по Windows Server 2016 Core содержится раздел, посвященный планированию и установке сервера политики сети \(NPS @ no__t-1, а технологии, представленные в этом программном обеспечении, служат предварительными требованиями для развертывания NPS в домене Active Directory. Дополнительные сведения см. в подразделе «Deploy NPS1» в [сетевом каталоге](https://technet.microsoft.com/windows-server-docs/networking/core-network-guide/core-network-guide#BKMK_deployNPS1)Windows Server 2016 Core.

## <a name="deploy-nps-certificates-for-vpn-and-8021x-access"></a>Развертывание сертификатов NPS для доступа VPN и 802.1 X

Если вы хотите развернуть методы проверки подлинности, такие как расширенный протокол проверки подлинности \(EAP @ no__t-1 и защищенный EAP, требующий использования сертификатов сервера в NPS, можно развернуть сертификаты NPS с помощью инструкции [Deploy Server Certificates for. 802.1 x проводных и беспроводных развертываний](https://technet.microsoft.com/windows-server-docs/networking/core-network-guide/cncg/server-certs/deploy-server-certificates-for-802.1x-wired-and-wireless-deployments).

## <a name="deploy-nps-for-8021x-wireless-access"></a>Развертывание NPS для беспроводного доступа 802.1 X

Чтобы развернуть NPS для беспроводного доступа, можно воспользоваться руководством [развертывание беспроводного доступа 802.1 x с проверкой подлинности на основе пароля](https://technet.microsoft.com/windows-server-docs/networking/core-network-guide/cncg/wireless/a-deploy-8021x-wireless-access).

## <a name="deploy-nps-for-windows-10-vpn-access"></a>Развертывание службы NPS для VPN-доступа Windows 10

Сервер политики сети можно использовать для обработки запросов на подключение к Always On виртуальной частной сети \(VPN @ no__t-1 для удаленных сотрудников, использующих компьютеры и устройства под управлением Windows 10.

Дополнительные сведения см. в статье [Always on удаленного доступа по развертыванию VPN для Windows Server 2016 и Windows 10](https://docs.microsoft.com/windows-server/remote/remote-access/vpn/always-on-vpn/deploy/always-on-vpn-deploy).

