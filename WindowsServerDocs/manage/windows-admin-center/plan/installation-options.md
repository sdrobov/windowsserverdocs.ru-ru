---
title: Какой тип установки подходит именно вам
description: В этом разделе описаны параметры различных установки Windows Admin Center, включая установку на ПК с Windows 10 или Windows server для использования нескольких Администраторы.
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.date: 04/12/2019
ms.openlocfilehash: cc6f9e6c2f2572618c1c5fdae00047d24fbeb3cf
ms.sourcegitcommit: f1edfc6525e09dd116b106293f9260123a94de0c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "9296666"
---
# Какой тип установки подойдет именно вам?

>Относится к: Windows Admin Center, ознакомительная версия Windows Admin Center

В этом разделе описаны параметры различных установки Windows Admin Center, включая установку на ПК с Windows 10 или Windows server для использования нескольких Администраторы. Чтобы установить Windows Admin Center на виртуальной Машине в Azure, см. в разделе [Развертывание Windows Admin Center в Azure](../azure/deploy-wac-in-azure.md).

## Поддерживаемые операционные системы: установки

Вы можете **установить** Windows Admin Center в следующих операционных системах Windows:

| **Версия** | **Режим установки** |
|-------------|-----------------------|
|Windows 10 версии 1709 или более поздней версии | Режим рабочего стола |
|Windows Server Semi-Annual Channel | Режим шлюза |
|Windows Server 2016 | Режим шлюза |
|WindowsServer2019 | Режим шлюза |

**Режим рабочего стола:** Запустите из меню "Пуск" и подключаться к шлюзу Windows Admin Center с того же компьютера, на котором оно установлено (т. е. `https://localhost:6516`)

**Режим шлюза:** Подключение к шлюзу Windows Admin Center из клиентского браузера на другом компьютере (т. е. `https://servername.contoso.com`) 

> [!WARNING]
> Установка Windows Admin Center на контроллере домена не поддерживается. [Более подробные сведения о домене контроллера рекомендации по безопасности](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/security-best-practices/securing-domain-controllers-against-attack). 

> [!IMPORTANT]
> Internet Explorer нельзя использовать для управления Windows Admin Center — вместо этого необходимо использовать [поддерживается браузера](../understand/faq.md#which-web-browsers-are-supported-by-windows-admin-center
).  Если вы устанавливаете Windows Admin Center в Windows Server, рекомендуется управление с удаленным подключение с Windows 10 и Edge.  Кроме того можно управлять локально на сервере Windows после установки поддерживаемый браузер.

## Поддерживаемые операционные системы: управление

Вы можете **управлять** следующих операционных систем Windows с помощью Windows Admin Center:

| Версия | Управление *узла* через *Диспетчер серверов* | Управление *кластера* через *Диспетчер отказоустойчивости кластеров* | Управление *HCI* через *Диспетчер кластера HCI*|
|-------------------------|---------------|-----|------------------------|
| Windows 10 версии 1709 или более поздней версии | Да (с помощью управления компьютером) | Н/Д | Н/Д |
| Windows Server Semi-Annual Channel | Да | Да | Н/Д |
| WindowsServer2019 | Да | Да | Да |
| Windows Server 2016 | Да | Да | Да, с [последний накопительный пакет обновления](../use/manage-hyper-converged.md#prepare-your-windows-server-2016-cluster-for-windows-admin-center) |
| Microsoft Hyper-V Server 2016 | Да | Да | Н/Д |
| Windows Server 2012 R2 | Да | Да | Н/Д |
| Microsoft Hyper-V Server 2012 R2 | Да | Да | Н/Д |
| Windows Server 2012 | Да | Да | Н/Д |
| Windows Server2008R2 | Да, ограниченные возможности | Н/Д | Н/Д |

> [!NOTE]
> Windows Admin Center нужны функции PowerShell, которые не включены в Windows Server 2008 R2, 2012 и 2012 R2. Если вы управляете их с помощью Windows Admin Center, необходимо установить Windows Management Framework (WMF) версии 5.1 или более поздней версии на эти серверы.

>Введите `$PSVersiontable` в PowerShell, чтобы убедиться, что платформа WMF установлена, и что используется версия 5.1 или более поздняя версия. 

>Если WMF не установлена, вы можете [скачать WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616).

## Варианты развертывания

| ![img](../media/deployment-options/W10.png) | ![img](../media/deployment-options/gateway.png) | ![img](../media/deployment-options/node.png) | ![img](../media/deployment-options/HA.png) |
|---|---|---|---|

| Локальном клиенте | Сервер шлюза | Управляемый сервер | Отказоустойчивый кластер |
| --- | --- | --- | --- |
| Установите на локальном клиенте Windows 10, подключение к управляемым серверам.  Отлично подходит для быстрого меню "Пуск", тестирование, специальное или небольших сценариев. |Установите на сервере шлюза назначенное и доступ из любого клиента браузера с подключения к серверу шлюза.  Идеально подходит для сценариев, широкомасштабные. | Установите непосредственно на управляемом сервере для управления самой или кластера, в котором она представляет собой узел члена.  Отлично подходит для распределенных сценариев. | Развертывание в отказоустойчивом кластере, обеспечение высокого уровня доступности службы шлюза. Отлично подходит для рабочих сред для обеспечения устойчивости службу управления устройствами. |

## Высокая доступность

Высокая доступность шлюза службы можно включить путем развертывания Windows Admin Center в активный — пассивный модели в отказоустойчивом кластере. В случае сбоя одного из узлов кластера Windows Admin Center корректно при сбое на другой узел приступить к ее легко управления серверами в своей среде.

[Узнайте подробнее о развертывании Windows Admin Center с высокой доступности.](../deploy/high-availability.md)

> [!Tip]
> Готовы к установке Windows Admin Center? [Скачать](https://aka.ms/windowsadmincenter)
