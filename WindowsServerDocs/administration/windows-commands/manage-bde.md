---
title: manage-bde
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 276a7841-7289-48d4-a57d-bc7c300affbb
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 816e20152ec40ce54c1192f3075c6f4556aed3db
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80839697"
---
# <a name="manage-bde"></a>manage-bde



Используется для включения или отключения BitLocker, указания механизмов разблокировки, обновления методов восстановления и разблокировки дисков с данными, защищенными BitLocker. Это средство командной строки можно использовать вместо элемента панели управления **Шифрование диска BitLocker** . Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
manage-bde [-status] [–on] [–off] [–pause] [–resume] [–lock] [–unlock] [–autounlock] [–protectors] [–tpm] 
[–SetIdentifier] [-ForceRecovery] [–changepassword] [–changepin] [–changekey] [-KeyPackage] [–upgrade] [-WipeFreeSpace] [{-?|/?}] [{-help|-h}]
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|[Manage-bde: status](manage-bde-status.md)|Предоставляет сведения обо всех дисках на компьютере независимо от того, защищены ли они с помощью BitLocker.|
|[Manage-bde: on](manage-bde-on.md)|Шифрует диск и включает BitLocker.|
|[Manage-bde: off](manage-bde-off.md)|Расшифровывает диск и отключает BitLocker. Все предохранители ключа удаляются после завершения расшифровки.|
|[Manage-bde: pause](manage-bde-pause.md)|Приостанавливает шифрование или расшифровку.|
|[Manage-bde: resume](manage-bde-resume.md)|Возобновляет шифрование или расшифровку.|
|[Manage-bde: lock](manage-bde-lock.md)|Предотвращает доступ к данным, защищенным BitLocker.|
|[Manage-bde: unlock](manage-bde-unlock.md)|Разрешает доступ к данным, защищенным BitLocker, с помощью пароля восстановления или ключа восстановления.|
|[Manage-bde: autounlock](manage-bde-autounlock.md)|Управляет автоматическим разблокировкой дисков данных.|
|[Manage-bde: protectors](manage-bde-protectors.md)|Управляет методами защиты для ключа шифрования.|
|[Manage-bde: tpm](manage-bde-tpm.md)|Настраивает доверенный платформенный модуль (TPM) компьютера (TPM). Эта команда не поддерживается на компьютерах под управлением Windows 8 или **win8_server_2**. Для управления доверенным платформенным модулем на этих компьютерах используйте оснастку MMC "Управление TPM" или командлеты управления TPM для Windows PowerShell.|
|[Manage-bde: setidentifier](manage-bde-setidentifier.md)|Задает для поля "идентификатор диска" значение, указанное в поле **Укажите уникальные идентификаторы для вашей организации** групповая политика параметр.|
|[Manage-bde: Форцерековери](manage-bde-forcerecovery.md)|Принудительное перезагрузку диска, защищенного с помощью BitLocker, в режим восстановления. Эта команда удаляет из диска все предохранители ключей, связанные с TPM. При перезапуске компьютера для разблокировки диска можно использовать только пароль восстановления или ключ восстановления.|
|[Manage-bde: changepassword](manage-bde-changepassword.md)|Изменяет пароль для диска данных.|
|[Manage-bde: changepin](manage-bde-changepin.md)|Изменяет ПИН-код для диска операционной системы.|
|[Manage-bde: changekey](manage-bde-changekey.md)|Изменяет ключ запуска для диска операционной системы.|
|[Manage-bde: Кэйпаккаже](manage-bde-keypackage.md)|Создает пакет ключей для диска.|
|[Manage-bde: upgrade](manage-bde-upgrade.md)|Обновляет версию BitLocker.|
|[Manage-bde: Випефриспаце](manage-bde-wipefreespace.md)|Очищает свободное место на диске.|
|-? или/?|Отображает краткую справку в командной строке.|
|-Help или-h|Отображает полную справку в командной строке.|

## <a name="examples"></a><a name=BKMK_Examples></a>Примеров

В следующем примере выводятся диски на компьютере и определяется, защищены ли они с помощью BitLocker, а также текущее состояние шифрования.
```
manage-bde -status
```
В следующем примере показано включение BitLocker на диске C с параметром пароля восстановления. Пароль восстановления будет создан BitLocker и отображен на экране, чтобы его можно было записать.
```
manage-bde –on C: -recoverypassword
```
В следующем примере показано, как разблокировать диск, защищенный BitLocker, с помощью пароля восстановления.
```
manage-bde –unlock E: -recoverypassword 111111-222222-333333-444444-555555-666666-777777-888888
```

## <a name="additional-references"></a>Дополнительные материалы

-   - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
-   [Включение BitLocker с помощью командной строки](https://technet.microsoft.com/library/dd894351(v=ws.10).aspx)
