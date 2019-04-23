---
title: Устранение неполадок в экранированных виртуальных машин
ms.custom: na
ms.prod: windows-server-threshold
ms.topic: article
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 10/3/2018
ms.openlocfilehash: 13ff0dad1519d394ce74a91efbfcc9e2f237e4a5
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59850035"
---
# <a name="troubleshoot-shielded-vms"></a>Устранение неполадок в экранированных виртуальных машин

>Относится к: Windows Server 2019 г., Windows Server (полугодовой канал), Windows Server 2016

Начиная с Windows Server версии ниже 1803, режим расширенного сеанса подключения к виртуальной машине (VMConnect) и PS Direct снова включаются для полностью экранированных виртуальных машин. Администратор виртуализации по-прежнему требуется гостевые учетные данные виртуальной Машины, чтобы получить доступ к виртуальной Машине, но это упрощает для поставщика услуг размещения для устранения неполадок экранированной виртуальной Машины при нарушении конфигурации сети.

Чтобы включить VMConnect и PS Direct для ваши экранированные виртуальные машины, просто переместите их на узел Hyper-V, выполняется Windows Server версии 1803 или более поздней версии. Виртуальные устройства, что обеспечивает эти функции будут повторно включены автоматически. Если экранированная виртуальная машина перемещается на узел под управлением и более ранней версии Windows Server, VMConnect и PS Direct будет отключена еще раз.

Конфиденциальные клиенты, беспокоиться, что поставщики услуг размещения имеют доступа к виртуальной Машине и чтобы вернуться в исходное поведение необходимо отключить следующие функции в гостевой ОС:

- Отключите службу PowerShell Direct на виртуальной машине:

  ```powershell
  Stop-Service vmicvmsession
  Set-Service vmicvmsession -StartupType Disabled
  ```

- Режим расширенного сеанса VMConnect можно отключить, только если гостевые ОС не ниже Windows Server 2019 или Windows 10, версия 1809. Добавьте следующий раздел реестра на виртуальной Машине, чтобы отключить подключения VMConnect расширенный сеанс консоли:

  ```
  reg add "HKLM\Software\Microsoft\Virtual Machine\Guest" /v DisableEnhancedSessionConsoleConnection /t REG_DWORD /d 1
  ```
