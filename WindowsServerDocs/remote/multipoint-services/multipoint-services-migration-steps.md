---
title: Действия по миграции служб MultiPoint
description: Пошаговые инструкции по переходу на службы MultiPoint в Windows Server 2016
ms.custom: na
ms.date: 07/29/2016
ms.prod: windows-server
ms.technology: multipoint-services
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3ee77efa-7cc5-4ddf-aaff-b5634a717014
author: lizap
manager: dongill
ms.author: elizapo
ms.openlocfilehash: 862e9b70cfafa9de0928a4789c5d23dfa0fbb530
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71389028"
---
# <a name="migrate-to--multipoint-services-in-windows-server-2016"></a>Переход на службы MultiPoint в Windows Server 2016

>Область применения. Windows Server 2016

Чтобы перейти к службам MultiPoint в Windows Server 2016, выполните следующие действия и сведения, собранные на листе планирования миграции.

## <a name="transfer-server-settings"></a>Параметры сервера для перемещения
На целевом сервере откройте MultiPoint Manager. Щелкните **изменить параметры сервера**. Примените параметры в соответствии с листом планирования миграции.

> [!NOTE]
> Если необходимо включить защиту диска на целевом сервере, подождите, пока вы настроите службы MultiPoint.

## <a name="transfer-station-settings"></a>Параметры станции передач
Перед применением параметров станции убедитесь, что станции подключены к целевому серверу и все они сопоставлены. Станции будут обнаружены автоматически. Следуйте инструкциям на экране каждого экрана, чтобы определить сопоставление серверов для пользовательских станций и подключенных USB-устройств. Примените параметры предпочтительной станции, как описано в журнале планирования миграции.

## <a name="migrate-the-vdi-template"></a>Перенос шаблона VDI

Перед импортом шаблона VDI с исходного сервера включите виртуальные рабочие столы на целевом сервере с помощью MultiPoint Manager:

1. Перейдите на вкладку **виртуальные рабочие столы** в диспетчере MultiPoint.
2. Щелкните **включенные виртуальные рабочие столы**. Сервер установит роль Hyper-V, а затем перезапустить.
3. Откройте диспетчер MultiPoint и вернитесь к **виртуальным рабочим столам**.
4. Щелкните **Импорт шаблона виртуального рабочего стола**. Следуйте инструкциям по импорту шаблона с исходного сервера.

> [!NOTE]
> При импорте шаблона виртуального рабочего стола все настройки, примененные к этому шаблону, будут сброшены. 

## <a name="next-step"></a>Дальнейшие действия
[Проверьте новое развертывание служб MultiPoint.](multipoint-services-post-migration-steps.md)