---
title: Развертывание сервера политики сети
description: В этом разделе приведены ссылки на содержимое развертывания сервера политики сети для Windows Server 2016 и содержит ссылки на дополнительные руководства по NPS.
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: 6cfb50e0-7088-4295-97c5-14ff8776cbf8
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 8da8951a9c6ed5022c892bbf01b33614d38abc5f
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59814845"
---
# <a name="deploy-network-policy-server"></a>Развертывание сервера политики сети

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

Сведения о развертывании сервера политики сети можно использовать в этом разделе.

>[!NOTE]
>Дополнительную документацию сервера политики сети можно использовать в следующих разделах библиотеки.  
>- [Приступая к работе с сервером политики сети](nps-getstart-top.md)
>- [Планирование сервера политики сети](nps-plan-top.md)
>- [Управление сервером политики сети](nps-manage-top.md)

Windows Server 2016 руководства по основной сети содержит раздел по планированию и установке сервера политики сети \(NPS\), и технологий, представленных в руководстве по служить необходимые условия для развертывания сервера политики сети в домене Active Directory. Дополнительные сведения см. в разделе «Развертывание сервере NPS1» в Windows Server 2016 [руководство по основной сети](https://technet.microsoft.com/windows-server-docs/networking/core-network-guide/core-network-guide#BKMK_deployNPS1).

## <a name="deploy-nps-certificates-for-vpn-and-8021x-access"></a>Развертывание сертификатов сервера политики сети для доступа 802.1 X и VPN

Если вы хотите развернуть методы проверки подлинности, такие как протокол расширенной проверки подлинности \(EAP\) и защищенного EAP, которые требуют использования сервера сертификатов на ваш сервер политики сети, можно развернуть сертификаты сервера политики сети с помощью руководства по [ Развертывание сертификатов сервера для 802.1 X проводных и беспроводных развертываний](https://technet.microsoft.com/windows-server-docs/networking/core-network-guide/cncg/server-certs/deploy-server-certificates-for-802.1x-wired-and-wireless-deployments).

## <a name="deploy-nps-for-8021x-wireless-access"></a>Развертывание сервера политики сети для беспроводного доступа 802.1 X

Чтобы развернуть сервер политики сети для беспроводного доступа, можно использовать руководство [развертывание паролю 802.1 X беспроводной доступ с проверкой подлинности](https://technet.microsoft.com/windows-server-docs/networking/core-network-guide/cncg/wireless/a-deploy-8021x-wireless-access).

## <a name="deploy-nps-for-windows-10-vpn-access"></a>Развертывание сервера политики сети для доступа к VPN Windows 10

Сервер политики сети можно использовать для обработки запросов на подключение для всегда в виртуальной частной сети \(VPN\) подключений для удаленных сотрудников, использующих компьютеры и устройства под управлением Windows 10.

Дополнительные сведения см. в разделе [удаленного доступа всегда на VPN развертывания руководство для Windows Server 2016 и Windows 10](https://docs.microsoft.com/windows-server/remote/remote-access/vpn/always-on-vpn/deploy/always-on-vpn-deploy).

