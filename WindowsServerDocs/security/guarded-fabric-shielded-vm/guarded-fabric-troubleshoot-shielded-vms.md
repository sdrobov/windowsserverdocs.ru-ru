---
title: Устранение неполадок экранированных виртуальных машин
ms.prod: windows-server
ms.topic: article
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.technology: security-guarded-fabric
ms.date: 10/3/2018
ms.openlocfilehash: c80663256a2e3404666b739c0a81cd06ec3caced
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856377"
---
# <a name="troubleshoot-shielded-vms"></a>Устранение неполадок экранированных виртуальных машин

>Область применения: Windows Server 2019, Windows Server (половина ежегодного канала), Windows Server 2016

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
