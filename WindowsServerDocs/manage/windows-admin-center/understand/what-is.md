---
title: Что такое Windows Admin Center
description: Что такое Windows Admin Center (проект Honolulu)
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.date: 06/07/2019
ms.openlocfilehash: 99f1a9a32ef69ba8322b2dba902003f8a750a4d2
ms.sourcegitcommit: 6ef4986391607bb28593852d06cc6645e548a4b3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66811643"
---
# <a name="what-is-windows-admin-center"></a>Что такое Windows Admin Center?

> Относится к: Windows Admin Center, предварительная версия Windows Admin Center

Windows Admin Center представляет собой новый развернутый локально набор средств управления на основе браузера, который позволяет управлять серверами под управлением Windows независимо от Azure и облака. Windows Admin Center предоставляет полный контроль над всеми аспектами серверной инфраструктуры и особенно полезен для управления серверами в частных сетях, которые не подключены к Интернету.

Windows Admin Center — это продукт эволюции встроенных средств управления, таких как Диспетчер серверов и MMC. Она дополняет System Center — это не является заменой.

![](../media/wac-complements.png)

## <a name="how-does-windows-admin-center-work"></a>Как работает Windows Admin Center?

Windows Admin Center выполняется в веб-браузере и управляет Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows 10 и т. д **шлюза Windows Admin Center** установить на Windows Server или Windows 10. Шлюз управляет серверами с помощью удаленной оболочки PowerShell и WMI через WinRM. Шлюз входит в состав Windows Admin Center в одном облегченном MSI-пакете, который можно [загрузить](https://aka.ms/windowsadmincenter).

Шлюз Windows Admin Center, при публикации в DNS и предоставлении доступа через соответствующие корпоративные брандмауэры, позволяет безопасно подключиться к серверам и управлять ими из любого места с помощью Microsoft Edge или Google Chrome.

![](../media/architecture.png)

## <a name="learn-how-windows-admin-center-improves-your-management-environment"></a>Узнайте, как Windows Admin Center позволяет улучшить среду управления

### <a name="familiar-functionality"></a>**Привычной функциональности**

Windows Admin Center — это результат развития устоявшихся и хорошо известных платформ управления, таких как консоль управления (MMC), созданный с нуля на основании современных стандартов создания систем и управления ими. Windows Admin Center содержит много знакомых вам средств, которые сейчас используются для управления серверами Windows и клиентами.

### <a name="easy-to-install-and-use"></a>**Легко установить и использовать**

[Установите](../deploy/install.md) его на компьютере с Windows 10 и начните работу спустя несколько минут либо установите на сервере Windows 2016, который будет действовать как шлюз, чтобы все сотрудники вашей организации могли управлять компьютерами через браузеры.

### <a name="complements-existing-solutions"></a>**Дополняет существующие решения**

Windows Admin Center работает с решений, таких как System Center и Azure управления и обеспечения безопасности, добавление в свои возможности по выполнению подробные, задачи управления на одном компьютере.

### <a name="manage-from-anywhere"></a>**Управление из любого места**

Опубликуйте сервер шлюза Windows Admin Center в общедоступном разделе Интернета, и вы сможете подключаться к серверам для управления ими из любого места в безопасном режиме.

### <a name="enhanced-security-for-your-management-platform"></a>**Расширенное управление безопасностью для вашей платформы управления**

Windows Admin Center содержит множество улучшений, которые делают управление платформой [более безопасным](../plan/user-access-options.md). Управление доступом на основе ролей позволяет точно настроить, какие администраторы имеют доступ к различным функциям управления. Параметры проверки подлинности шлюза включают локальные группы, Active Directory на основе локального домена и Azure Active Directory на основе облака.  Кроме того, можно [получить представление](../use/logging.md) о действиях по управлению, выполняемых в вашей среде.

### <a name="azure-integration"></a>**Интеграция Azure**

Windows Admin Center имеет точек [интеграция со службами Azure](../plan/azure-integration-options.md), включая Azure Active Directory, Azure Backup, Azure Site Recovery и многое другое.

### <a name="manage-hyper-converged-clusters"></a>**Управление кластерами hyper со схождением**

Windows Admin Center обеспечивает максимальное удобство для [управления гиперконвергентными кластерами](../use/manage-hyper-converged.md), включая виртуализованные компоненты для вычисления, хранения и поддержки сетевых возможностей.

### <a name="extensibility"></a>**Расширяемость**

Windows Admin Center с самого начала создавался с учетом расширения, что позволяет корпорации Майкрософт и сторонним производителям создавать средства и решения, расширяющие возможности текущих предложений. Корпорация Майкрософт предлагает [пакет SDK](../extend/extensibility-overview.md), который позволяет разработчикам создавать свои собственные средства для Windows Admin Center.

> [!Tip]
> Готовы к установке Windows Admin Center? [Скачать](https://aka.ms/windowsadmincenter)
