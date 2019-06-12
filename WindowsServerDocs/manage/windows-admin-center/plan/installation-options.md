---
title: Какой тип установки подходит для вас
description: В этом разделе описывается вариантов установки для Windows Admin Center, включая установки на Компьютере с Windows 10 или Windows server для использования с несколькими администраторами.
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.date: 06/07/2019
ms.openlocfilehash: 9b26ce28d8b3f74c26adab87e68b9985f2be5361
ms.sourcegitcommit: 6ef4986391607bb28593852d06cc6645e548a4b3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66811814"
---
# <a name="what-type-of-installation-is-right-for-you"></a>Какой тип установки подойдет именно вам?

>Область применения. Windows Admin Center, предварительная версия Windows Admin Center

В этом разделе описывается вариантов установки для Windows Admin Center, включая установки на Компьютере с Windows 10 или Windows server для использования с несколькими администраторами. Чтобы установить Windows Admin Center на виртуальную Машину в Azure, см. в разделе [Windows Admin Center развертывание в Azure](../azure/deploy-wac-in-azure.md).

## <a name="supported-operating-systems-installation"></a>Поддерживаемые операционные системы: Установка

Вы можете **установить** Windows Admin Center в следующих операционных системах Windows:

| **Version**  | **Режим установки** |
| -------------| -----------------------|
| Windows 10 версии 1709 или более поздней версии | Режим рабочего стола |
| Windows Server Semi-Annual Channel | Режим шлюза |
| Windows Server 2016 | Режим шлюза |
| Windows Server 2019 | Режим шлюза |

**Режим Desktop:** Запустите из меню "Пуск" и подключения к шлюзу Windows Admin Center на том же компьютере, на котором он установлен (т. е. `https://localhost:6516`)

**Режим шлюза:** Подключения к шлюзу Windows Admin Center из клиентского браузера на другом компьютере (т. е. `https://servername.contoso.com`) 

> [!WARNING]
> Установка Windows Admin Center на контроллере домена не поддерживается. [Дополнительные сведения о безопасности контроллера домена рекомендации](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/security-best-practices/securing-domain-controllers-against-attack). 

> [!IMPORTANT]
> Нельзя использовать Internet Explorer для управления Windows Admin Center — вместо этого необходимо использовать [поддерживаемом браузере](../understand/faq.md#which-web-browsers-are-supported-by-windows-admin-center
).  При установке Windows Admin Center в Windows Server, корпорация Майкрософт рекомендует управление с удаленного подключения в Windows 10 и Edge.  Кроме того вы можете управлять локально на сервере Windows после установки поддерживаемого браузера.

## <a name="supported-operating-systems-management"></a>Поддерживаемые операционные системы: Management

Вы можете **управление** следующих операционных систем Windows, с помощью Windows Admin Center:

| Version | Управление *узел* через *диспетчера серверов* | Управление *кластера* через *Диспетчер отказоустойчивости кластеров* | Управление *HCI* через *HCI диспетчер кластеров* |
| ------------------------- |--------------- | ----- | ------------------------ |
| Windows 10 версии 1709 или более поздней версии | Да (через управление компьютером) | Н/Д | Н/Д |
| Windows Server Semi-Annual Channel | Да | Да | Н/Д |
| Windows Server 2019 | Да | Да | Да |
| Windows Server 2016 | Да | Да | Да, с помощью [последний накопительный пакет обновления](../use/manage-hyper-converged.md#prepare-your-windows-server-2016-cluster-for-windows-admin-center) |
| Microsoft Hyper-V Server 2016 | Да | Да | Н/Д |
| Windows Server 2012 R2 | Да | Да | Н/Д |
| Microsoft Hyper-V Server 2012 R2 | Да | Да | Н/Д |
| Windows Server 2012 | Да | Да | Н/Д |
| Windows Server 2008 R2 | Да, ограниченной функциональностью | Н/Д | Н/Д |

> [!NOTE]
> Windows Admin Center требуются возможности PowerShell, которые не включены в Windows Server 2008 R2, 2012 и 2012 R2. Если вы будете управлять с помощью Windows Admin Center, необходимо установить Windows Management Framework (WMF) 5.1 или более поздней версии на этих серверах.
> 
> Введите `$PSVersiontable` в PowerShell, чтобы проверить, что платформа WMF установлена, и что используется версия 5.1 или более поздняя версия. 
> 
> Если не установлен WMF, вы можете [скачать WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616).

## <a name="deployment-options"></a>Варианты развертывания

| ![img](../media/deployment-options/W10.png) | ![img](../media/deployment-options/gateway.png) | ![img](../media/deployment-options/node.png) | ![img](../media/deployment-options/HA.png) |
| --------------------------------------------- | ------------------------------------------------- |----------------------------------------------|-------------------------------------------- |
|                                             |                                                 |                                              |                                            |

| Локальный клиент | Сервер шлюза | Управляемый сервер | Отказоустойчивый кластер |
| --- | --- | --- | --- |
| Установите на локальном клиенте Windows 10 с подключением на управляемых серверах.  Отлично подходят для быстрого запуска, тестирования, ad-hoc или небольших сценариев. |Установите на сервере, отдельный шлюз и доступ из любого клиента браузера с подключением к серверу шлюза.  Прекрасно подходит для крупномасштабных сценариях. | Установка непосредственно на управляемом сервере целью управления самостоятельно или кластер, в котором он является узлом-участником.  Отлично подходят для распределенных сценариях. | Разверните в отказоустойчивом кластере для обеспечения высокого уровня доступности службы шлюза. Отлично подходят для рабочих сред обеспечить устойчивость службы управления. |

## <a name="high-availability"></a>Высокая доступность

Вы можете включить высокий уровень доступности службы шлюза, развернув Windows Admin Center в активно пассивную модель в отказоустойчивом кластере. В случае сбоя одного из узлов в кластере Windows Admin Center корректно при сбое на другой узел, позволяя продолжить управление серверами в вашей среде без проблем.

[Сведения о развертывании Windows Admin Center с высоким уровнем доступности.](../deploy/high-availability.md)

> [!Tip]
> Готовы к установке Windows Admin Center? [Скачать](https://aka.ms/windowsadmincenter)
