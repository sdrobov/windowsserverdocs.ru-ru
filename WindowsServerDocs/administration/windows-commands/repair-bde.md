---
title: repair-bde
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 534dca1a-05f7-4ea8-ac24-4fe5f14f988a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9e2bce0c0a0f12a3a171c161a669c903044e8b4b
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59813545"
---
# <a name="repair-bde"></a>repair-bde



Обращений к зашифрованные данные на важности жесткого диска, если диск был зашифрован с помощью BitLocker. Repair-bde может восстановить критически важные части диска и спасти восстановимые данные, если для расшифровки данных используется допустимый пароль восстановления или ключ восстановления. Если метаданные BitLocker на диске повреждены, у вас должна быть возможность предоставить резервную копию пакета ключей вдобавок к паролю восстановления или ключу восстановления. Резервная копия пакета ключей создается в доменных службах Active Directory (AD DS), если вы использовали параметры по умолчанию для резервного копирования в AD DS. С помощью этого пакета ключей и пароля восстановления или ключа восстановления вы можете расшифровать части защищенного BitLocker диска, если он поврежден. Каждый пакет ключей можно использовать только для диска с соответствующим идентификатором. Можно использовать [средство просмотра пароля восстановления BitLocker для Active Directory](https://technet.microsoft.com/library/dd875531(v=ws.10).aspx) для получения этого ключа пакета из AD DS.

> [!NOTE]
> Средство просмотра пароля восстановления BitLocker включается в качестве одной из функций управления необязательные устанавливаемые с помощью сервера управления в Windows Server 2012.

Программы командной строки Repair-bde имеются следующие ограничения:
-   Repair-bde не удается восстановить диск, сбой во время шифрования или расшифровки.
-   Repair-bde предполагается, что если на диске есть какого-либо шифрования, затем диск полностью зашифрован.

Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).

## <a name="syntax"></a>Синтаксис

```
repair-bde <InputVolume> <OutputVolumeorImage> [-rk] [–rp] [-pw] [–kp] [–lf] [-f] [{-?|/?}]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|\<InputVolume >|Указывает букву диска, которую требуется восстановить зашифрованные BitLocker. Буква диска должно содержать двоеточий; Например: **C:**.|
|\<OutputVolumeorImage>|Определяет диск, на котором для хранения содержимого восстановленного диска. Все данные на диске, выходные данные будут перезаписаны.|
|-ринтерах|Расположение ключа восстановления, который должен использоваться для разблокирования тома. Эта команда также может быть указан как **- recoverykey**.|
|-rp|Определяет пароль числовой восстановления, который должен использоваться для разблокирования тома. Эта команда также может быть указан как **- recoverypassword**.|
|-пароль|Определяет пароль, который следует использовать для разблокирования тома. Эта команда также может быть указан как **-пароль**|
|-kp|Идентифицирует пакет ключа восстановления, который может использоваться для разблокирования тома. Эта команда также может быть указан как **- keypackage**.|
|-lf|Указывает путь к файлу, в которой будут храниться Repair-bde ошибки, предупреждения и информационные сообщения. Эта команда также может быть указан как **- logfile**.|
|-f|Принудительное тома требуется отключить, даже если он не может быть заблокирован. Эта команда также может быть указан как **-принудительно**.|
|-? или /?|Отображает справку в командной строке.|

## <a name="remarks"></a>Примечания

Если не указан путь пакета ключей, **repair-bde** будет поиск на диске для пакета ключей. Тем не менее, если жесткий диск поврежден, **repair-bde** не сможете найти пакет и предложит указать путь.

## <a name="BKMK_Examples"></a>Примеры

В следующем примере предпринимается попытка восстановить диск C и запись содержимого диска C диска D, используя файл ключа восстановления (RecoveryKey.bek) хранится на диске F и записывает результаты этого эта попытка в журнал (log.txt) на диск Z:.
```
repair-bde C: D: -rk F:\RecoveryKey.bek –lf Z:\log.txt
```
В следующем примере предпринимается восстановление диска C и запись содержимого на диске C диска D с помощью 48-значный цифровой пароль восстановления указан. Пароль восстановления должны вводиться в восьми блоков из шести цифр, дефис, отделение каждого блока.
```
repair-bde C: D: -rp 111111-222222-333333-444444-555555-666666-777777-888888
```
В следующем примере принудительно диска C и требуется отключить и затем пытается восстановить диск C и запись содержимого на диске C диска D, используя пакет ключа восстановления и файл ключа восстановления (RecoveryKey.bek) хранится на диске F.
```
repair-bde C: D: -kp F:\RecoveryKeyPackage -rk F:\RecoveryKey.bek -f
```
В следующем примере предпринимается восстановление диска C и запись содержимого диска C диска D, и необходимо ввести пароль для разблокировки диска C:, при появлении запроса:
```
repair-bde C: D: -pw
```

#### <a name="additional-references"></a>Дополнительная справка

-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)