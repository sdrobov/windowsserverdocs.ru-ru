---
title: Что нового в Windows Server 2016 Essentials
description: Описывает способ использования Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: affff774-5fa6-4944-887a-9bfde05f6a3f
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: bc83686f76c49773203d63a88894841f65ffd1d9
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66433759"
---
# <a name="whats-new-in-windows-server-2016-essentials"></a>Что нового в Windows Server 2016 Essentials

> Область применения. Windows Server2016 Essentials

Ниже перечислены новые и улучшенные возможности в Windows Server 2016 Essentials.

## <a name="integration-with-azure-site-recovery-servicesazure-site-recovery-services-integrationmd"></a>[Интеграция со службами Azure Site Recovery.](azure-site-recovery-services-integration.md)

**Назначение** --при виртуальной машины, защищенные завершается сбоем или сервера узла, который выполняется на защищенной виртуальной машине на происходит сбой, отработки отказа с помощью служб Azure Site Recovery поддерживает непрерывность бизнес-процессов, пока виртуальная машина в локальной среде или сервер узла-исправленной и доступны. 

**Принцип работы** --служб Azure Site Recovery, предлагаемых в Microsoft Azure позволяет в режиме реального времени репликации виртуальных машин (ВМ) в хранилище архивации в Azure. В случае, если сервер или сайт выходит из строя из-за аппаратного или иного рода сбоя, вам может переключиться с помощью служб Azure Site Recovery таким образом, чтобы образ виртуальной Машины, хранящиеся в хранилище резервных копий подготавливается в качестве работающей виртуальной Машины в Azure. В сочетании с Azure в виртуальной сети, клиентские компьютеры, подключенные к серверу в локальной прозрачно подключится к серверу, работающему в Azure.     
                                                                                                                                                                                                                                                                                                               

## <a name="integration-with-azure-virtual-networkazure-virtual-network-integrationmd"></a>[Интеграция с Azure в виртуальной сети](azure-virtual-network-integration.md)

**Назначение**--организаций, принимая их способ облачные вычисления, они редко перемещать все свои ресурсы за один раз. Вместо этого они перемещаются некоторые ресурсы в облаке и сохранить некоторые на локальном компьютере. Таким образом, это можно легко переместить организации в облаке на этапах со временем. Azure Интеграция виртуальной сети предоставляет инфраструктуру сети, которая делает этот процесс, эффективной и управляемой.

**Принцип работы** --Azure виртуальные сети — это служба, предлагаемых в Microsoft Azure, которая позволяет организациям создавать точка-точка (P2P) или -сайтами (S2S) виртуальной частной сети, делающий ресурсы, работающие в Azure (например, виртуальные машины и хранилище) выглядеть так, будто они находятся в локальной сети для простого приложения и доступа к ресурсам.



## <a name="support-for-larger-deploymentssupport-for-larger-deploymentsmd"></a>[Поддержка для более крупных развертываний](support-for-larger-deployments.md) 

Некоторые больших предприятий малого бизнеса требуется больше функциональных возможностей и емкости для эффективной реализации Windows Server Essentials. Windows Server 2016 Essentials предоставляет повышенную управляемость домены, пользователей и устройств, добавляя поддержку более крупных развертываний с помощью:                                                                                                                                                                                                 

 - несколько доменов
 - несколько контроллеров домена                                                                                                                                                                                                                                        
 - возможность указывать указанный контроллер домена                                                                                                                                                                                                                   
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       

<a name="see-also"></a>См. также
--------

[Начало работы с Windows Server Essentials](get-started.md)
