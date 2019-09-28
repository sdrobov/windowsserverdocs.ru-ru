---
title: Устранение неполадок экранированных виртуальных машин
ms.custom: na
ms.prod: windows-server
ms.topic: article
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 10/3/2018
ms.openlocfilehash: b0d4338d20238eb528c19221151f380cc154a2db
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71386374"
---
# <a name="troubleshoot-shielded-vms"></a>Устранение неполадок экранированных виртуальных машин

>Относится к: Windows Server 2019, Windows Server (половина ежегодного канала), Windows Server 2016

Начиная с Windows Server версии 1803, режим расширенного сеанса подключения к виртуальной машине (VMConnect) и PS Direct повторно включены для полностью экранированных виртуальных машин. Администратору виртуализации по-прежнему требуются гостевые учетные данные ВИРТУАЛЬНОЙ машины, чтобы получить доступ к виртуальной машине, но это упрощает устранение неполадок экранированной виртуальной машины при нарушении ее конфигурации сети.

Чтобы включить VMConnect и PS Direct для экранированных виртуальных машин, просто переместите их на узел Hyper-V под управлением Windows Server версии 1803 или более поздней. Виртуальные устройства, допускающие эти функции, будут снова включены автоматически. Если экранированная виртуальная машина перемещается на узел, на котором работает и более ранняя версия Windows Server, VMConnect и PS Direct будут отключены.

Для клиентов, учитывающих безопасность, которые стремятся, если у поставщиков услуг размещения есть доступ к виртуальной машине и вы хотите вернуться к исходному поведению, в гостевой ОС должны быть отключены следующие функции:

- Отключите прямую службу PowerShell на виртуальной машине:

  ```powershell
  Stop-Service vmicvmsession
  Set-Service vmicvmsession -StartupType Disabled
  ```

- Режим расширенного сеанса VMConnect можно отключить, только если гостевая ОС установлена по меньшей мере Windows Server 2019 или Windows 10, версия 1809. Добавьте следующий раздел реестра в виртуальную машину, чтобы отключить подключения консоли расширенного сеанса VMConnect:

  ```
  reg add "HKLM\Software\Microsoft\Virtual Machine\Guest" /v DisableEnhancedSessionConsoleConnection /t REG_DWORD /d 1
  ```
