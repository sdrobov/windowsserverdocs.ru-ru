---
title: manage-bde
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 276a7841-7289-48d4-a57d-bc7c300affbb
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8923177b03f378f8252c532ec386f1808e516e1e
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59874505"
---
# <a name="manage-bde"></a>manage-bde



Чтобы включить или отключить BitLocker, укажите механизмы, обновите методы восстановления и разблокировке дисков с данными, защищенными BitLocker. Это средство командной строки можно использовать вместо **шифрования диска BitLocker** элемент панели управления. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
manage-bde [-status] [–on] [–off] [–pause] [–resume] [–lock] [–unlock] [–autounlock] [–protectors] [–tpm] 
[–SetIdentifier] [-ForceRecovery] [–changepassword] [–changepin] [–changekey] [-KeyPackage] [–upgrade] [-WipeFreeSpace] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|[готов: состояние](manage-bde-status.md)|Сведения о всех дисков на компьютере, ли они защищенными BitLocker.|
|[готов: на](manage-bde-on.md)|Шифрует диск и включает BitLocker.|
|[готов: off](manage-bde-off.md)|Расшифровывает диск и отключить BitLocker. По завершении расшифровки, удаляются все предохранители ключа.|
|[готов: Приостановка](manage-bde-pause.md)|Приостановка шифрования или расшифровки.|
|[готов: возобновление](manage-bde-resume.md)|Возобновляет шифрования или расшифровки.|
|[готов: блокировки](manage-bde-lock.md)|Запрещает доступ к данным, защищенным BitLocker.|
|[готов: разблокировки](manage-bde-unlock.md)|Разрешает доступ к данным, защищенным с помощью BitLocker, с помощью пароль восстановления или ключ восстановления.|
|[готов: автоматическое разблокирование диска](manage-bde-autounlock.md)|Управляет автоматическую разблокировку дисков с данными.|
|[готов: предохранители](manage-bde-protectors.md)|Управляет методами защиты ключа шифрования.|
|[готов: доверенного платформенного модуля](manage-bde-tpm.md)|Настройка компьютера доверенного платформенного модуля (TPM). Эта команда не поддерживается на компьютерах под управлением Windows 8 или **win8_server_2**. Для управления доверенным платформенным Модулем на этих компьютерах, используйте оснастку MMC управления доверенным платформенным Модулем или командлетов управления доверенным платформенным Модулем для Windows PowerShell.|
|[готов: setidentifier](manage-bde-setidentifier.md)|Задает поле идентификатора диска на диске к значению, указанному в **указать уникальные идентификаторы для организации** параметр групповой политики.|
|[готов: ForceRecovery](manage-bde-forcerecovery.md)|Заставляет дисков, защищенных BitLocker в режим восстановления при перезапуске. Эта команда удаляет все относящиеся к TPM предохранители ключа с диска. После перезагрузки компьютера, пароль восстановления или ключа восстановления можно использовать для разблокировки диска.|
|[готов: изменение пароля](manage-bde-changepassword.md)|Изменяет пароль для диска с данными.|
|[готов: changepin](manage-bde-changepin.md)|Изменение ПИН-код для диска операционной системы.|
|[готов: changekey](manage-bde-changekey.md)|Изменяет ключ запуска для диска операционной системы.|
|[готов: KeyPackage](manage-bde-keypackage.md)|Создает пакет ключей для диска.|
|[готов: обновление](manage-bde-upgrade.md)|Обновление версии BitLocker.|
|[готов: WipeFreeSpace](manage-bde-wipefreespace.md)|Очищает свободного места на диске.|
|-? или /?|Отображение кратких справки в командной строке.|
|-help или -h|Отображает полную справку в командной строке.|

## <a name="BKMK_Examples"></a>Примеры

В следующем примере отображаются диски на компьютере и определяет ли они защищаются BitLocker и текущее состояние шифрования.
```
manage-bde -status
```
В следующем примере показано включение BitLocker на диске C с параметром пароля восстановления. Пароль восстановления будет создан с помощью BitLocker и отображается на экране, чтобы его можно записать.
```
manage-bde –on C: -recoverypassword
```
В следующем примере показано, Разблокировка диска, защищенного BitLocker с помощью пароля восстановления.
```
manage-bde –unlock E: -recoverypassword 111111-222222-333333-444444-555555-666666-777777-888888
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)
-   [Включение BitLocker с помощью командной строки](https://technet.microsoft.com/library/dd894351(v=ws.10).aspx)
