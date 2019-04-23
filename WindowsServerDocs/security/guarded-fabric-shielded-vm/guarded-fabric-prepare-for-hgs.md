---
title: Проверка предварительных требований HGS
ms.custom: na
ms.prod: windows-server-threshold
ms.topic: article
ms.assetid: f4b4d1a8-bf6d-4881-9150-ddeca8b48038
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: dddf694aaceab93bd102456dbe86df17a001cb01
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59879885"
---
# <a name="review-prerequisites-for-the-host-guardian-service"></a>Обзор предварительных требований для службы защиты узла

>Относится к: Windows Server 2019 г., Windows Server (полугодовой канал), Windows Server 2016


В этом разделе рассматриваются предварительные требования HGS и начальные действия по подготовке к развертыванию HGS.

## <a name="prerequisites"></a>предварительные требования 

-   **Оборудование**: HGS, которые могут выполняться на физических компьютерах или виртуальных машин, но рекомендуется использовать физические компьютеры.

    Если вы хотите запустить HGS как физического трех узлов кластера (для доступности), необходимо иметь три физических серверов. (Рекомендуется для кластеризации, три сервера должен иметь очень похожа оборудования).
  
-   **Операционная система**: Аттестация ключей узла требует работы Windows Server 2019 Standard или Datacenter edition с [аттестации v2](guarded-fabric-tpm-trusted-attestation-capturing-hardware.md#versioned-attestation-policies). Для аттестации на основе доверенного платформенного МОДУЛЯ HGS можно запустить Windows Server 2019 или Windows Server 2016, Standard или Datacenter edition.

-   **Роли сервера**: Служба защиты узла и поддерживающих роли сервера.

-   **Конфигурации разрешений и привилегий для домена fabric (узлов)**: Необходимо будет настроить переадресацию DNS между доменами fabric (узлов) и HGS. 
    
## <a name="upgrading-hgs"></a>Обновление HGS

Если вы уже развернули HGS и для обновления операционной системы, выполните [руководства по обновлению](guarded-fabric-upgrade-to-2019.md) обновлять серверы HGS и Hyper-V на последнюю версию ОС.

## <a name="next-step"></a>Дальнейшие действия

>[!div class="nextstepaction"]
[Получение сертификатов для HGS](guarded-fabric-obtain-certs.md)