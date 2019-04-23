---
title: Действия по переносу служб MultiPoint
description: Поможет выполнить действия по переносу служб MultiPoint в Windows Server 2016
ms.custom: na
ms.date: 07/29/2016
ms.prod: windows-server-threshold
ms.technology: multipoint-services
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3ee77efa-7cc5-4ddf-aaff-b5634a717014
author: lizap
manager: dongill
ms.author: elizapo
ms.openlocfilehash: b63ef4bf63ce990aa0b0ba7624905ba8f14dde98
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59854815"
---
# <a name="migrate-to--multipoint-services-in-windows-server-2016"></a>Перенос в MultiPoint Services в Windows Server 2016

>Область применения. Windows Server 2016

Используйте следующие действия, а также сведения, собранные в журнале планирования миграции для переноса в MultiPoint Services в Windows Server 2016.

## <a name="transfer-server-settings"></a>Перенос параметров сервера
На конечном сервере откройте диспетчер MultiPoint. Нажмите кнопку **изменение параметров сервера**. Примените параметры в соответствии с журнале планирования миграции.

> [!NOTE]
> Если необходимо включить защиту диска на конечном сервере, подождите, пока после настройки MultiPoint Services.

## <a name="transfer-station-settings"></a>Перенос параметров станции
Убедитесь, что станции подключены к целевой сервер и все сопоставления, прежде чем применить параметры станции. Станции будут определяться автоматически. Следуйте инструкциям на экране каждой станции для определения сопоставления server Пользовательские станции и USB-устройств. Примените выбранные настройки предпочтительных станции, как описано в журнале планирования миграции.

## <a name="migrate-the-vdi-template"></a>Перенос шаблона VDI

Перед импортом шаблона VDI с исходного сервера, включить виртуальные рабочие столы на целевом сервере с помощью MultiPoint Manager:

1. Перейдите к **виртуальные рабочие столы** вкладка в диспетчер MultiPoint.
2. Нажмите кнопку **включить виртуальные рабочие столы**. Сервер будет Установка роли Hyper-V и перезапустить.
3. Откройте диспетчер MultiPoint и вернитесь к **виртуальные рабочие столы**.
4. Нажмите кнопку **Импорт шаблона виртуального рабочего стола**. Следуйте инструкциям, чтобы импортировать шаблон с исходного сервера.

> [!NOTE]
> При импорте шаблона виртуального рабочего стола, приведет к сбросу какой-либо настройки, применяемый к шаблону. 

## <a name="next-step"></a>Дальнейшие действия
[Проверка нового развертывания служб MultiPoint.](multipoint-services-post-migration-steps.md)