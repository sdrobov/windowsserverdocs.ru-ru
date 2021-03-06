---
title: TCP-подключение прервано при проверке согласования
description: В этой статье объясняется, как устранить неполадки SMB при прерывании подключения TCP во время проверки согласования.
author: Deland-Han
manager: dcscontentpm
ms.topic: article
ms.author: delhan
ms.date: 12/25/2019
ms.openlocfilehash: 762ad3b20c389771a9c0e6783d2a6fb1e73b8f0d
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86961006"
---
# <a name="tcp-connection-is-aborted-during-validate-negotiate"></a>TCP-подключение прервано при проверке согласования

В трассировке сети для проблемы SMB вы заметили, что в процессе проверки согласования произошла ошибка сброса TCP. В этой статье описывается устранение ситуации.

## <a name="cause"></a>Причина

Эта проблема может быть вызвана неудачной проверкой согласования. Обычно это происходит потому, что ускоритель WAN изменяет исходный пакет СОГЛАСОВАНия SMB.

Корпорация Майкрософт больше не разрешает вносить изменения в пакет проверки согласованности по любой причине. Это обусловлено тем, что такое поведение создает серьезную угрозу безопасности.

К пакету проверки согласованности применяются следующие требования.

- Процесс проверки согласования использует команду ФСКТЛ \_ Validate \_ \_ info.

- Ответ на проверку согласования должен быть подписан. В противном случае соединение будет прервано.

- Чтобы убедиться в том \_ \_ \_ , что ничего не изменилось, следует сравнить сообщения о проверке согласованности фсктл с сообщениями согласования.

## <a name="workaround"></a>Обходной путь

Процесс проверки согласованности можно временно отключить. Для этого откройте следующий подраздел реестра:

**\_ \_ \\ \\ \\ \\ Параметры LanmanWorkstation для CurrentControlSet служб \\ в hKey System в локальном компьютере**

В разделе **параметров** задайте для **рекуиресекуренеготиате** значение **0**.

В Windows PowerShell можно выполнить следующую команду, чтобы задать это значение:

```PowerShell
Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Services\LanmanWorkstation\Parameters" RequireSecureNegotiate -Value 0 -Force
```

> [!NOTE]
> Процесс проверки согласованности не может быть отключен в Windows 10, Windows Server 2016 или более поздних версиях Windows.

Если клиент или сервер не могут поддерживать команду "проверить согласование", эту ошибку можно обойти, задав для подписывания SMB требуемый вариант. Подписывание SMB считается более безопасным, чем проверка согласованности. Однако при необходимости подписи также может снизиться производительность.

## <a name="reference"></a>Справочник

См. сведения в следующих статьях:

[3.3.5.15.12 Обработка запроса на проверку сведений о согласовании](/openspecs/windows_protocols/ms-smb2/0b7803eb-d561-48a4-8654-327803f59ec6)

[3.2.5.14.12 Обработка ответа "проверить сведения о согласовании"](/openspecs/windows_protocols/ms-smb2/6a5bc90d-3c08-4498-905b-e7dab30b2e0e)
