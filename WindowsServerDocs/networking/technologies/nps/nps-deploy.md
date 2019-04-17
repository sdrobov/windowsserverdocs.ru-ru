---
title: Развертывание сервера политики сети
description: В этом разделе приведены ссылки на содержимое для развертывания сервера политики сети Windows Server 2016 и содержит ссылки на дополнительные руководства по NPS.
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: 6cfb50e0-7088-4295-97c5-14ff8776cbf8
ms.author: pashort
author: shortpatti
ms.openlocfilehash: daf62e2a593014e16bcb5fd16542b2e9c75b9c1d
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="deploy-network-policy-server"></a>Развертывание сервера политики сети

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

Дополнительные сведения о развертывании сервера политики сети можно использовать в этом разделе.

>[!NOTE]
>Дополнительную документацию сервера политики сети можно использовать в следующих разделах библиотеки.  
>- [Приступая к работе с сервером политики сети](nps-getstart-top.md)
>- [Планирование сервера политики сети](nps-plan-top.md)
>- [Управление сервером политики сети](nps-manage-top.md)

Руководство по сети основных компонентов Windows Server 2016 включает раздела о планировании и установке \(NPS\) сервера политики сети и технологии, представленные в руководстве по служить предварительные требования для развертывания сервера политики сети в домене Active Directory. Дополнительные сведения см. раздел «Развернуть NPS1» в Windows Server 2016 [руководство по основной сети](https://technet.microsoft.com/windows-server-docs/networking/core-network-guide/core-network-guide#BKMK_deployNPS1).

## <a name="deploy-nps-server-certificates-for-vpn-and-8021x-access"></a>Развертывание сертификатов сервера политики сети для виртуальной частной сети и доступа 802.1 X

Если вы хотите развернуть методы проверки подлинности, как \(EAP\) расширяемого протокола проверки подлинности и защищенного EAP, требуют использования сертификатов сервера, на NPS-сервере, можно развернуть сертификаты сервера политики сети с помощью руководства по [развертывание сертификатов сервера для проводных сетей 802.1 X и беспроводных развертываний](https://technet.microsoft.com/windows-server-docs/networking/core-network-guide/cncg/server-certs/deploy-server-certificates-for-802.1x-wired-and-wireless-deployments).

## <a name="deploy-nps-for-8021x-wireless-access"></a>Развертывание сервера политики сети для беспроводного доступа 802.1 X

Чтобы развернуть сервер политики сети для доступа к беспроводной сети, вы можете использовать руководство [развертывание пароль 802.1 X с проверкой подлинности беспроводного доступа на основе](https://technet.microsoft.com/windows-server-docs/networking/core-network-guide/cncg/wireless/a-deploy-8021x-wireless-access).

## <a name="deploy-nps-for-windows-10-vpn-access"></a>Развертывание сервера политики сети для доступа через VPN в Windows 10

Сервер политики сети можно использовать для обработки запросов на подключение для подключения \(VPN\) всегда в виртуальной частной сети для удаленных сотрудников, использующих компьютеры и устройства с Windows 10.

Дополнительные сведения см. в разделе [удаленного доступа всегда на VPN развертывания руководство для Windows Server 2016 и Windows 10](https://docs.microsoft.com/windows-server/remote/remote-access/vpn/always-on-vpn/deploy/always-on-vpn-deploy).

