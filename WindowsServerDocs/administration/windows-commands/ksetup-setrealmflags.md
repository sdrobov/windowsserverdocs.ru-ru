---
title: ksetup сетреалмфлагс
description: Справочный раздел по команде ksetup сетреалмфлагс, который задает флаги области для указанной области.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: bcb2824e-fba7-4ebe-be62-e62b4fae5b17
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2de568ae3df522f43d7a84e22d76ee3975d8e209
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2020
ms.locfileid: "83817324"
---
# <a name="ksetup-setrealmflags"></a>ksetup сетреалмфлагс

Задает флаги области для указанной области.

## <a name="syntax"></a>Синтаксис

```
ksetup /setrealmflags <realmname> [sendaddress] [tcpsupported] [delegate] [ncsupported] [rc4]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `<realmname>` | Указывает DNS-имя в верхнем регистре, например CORP. CONTOSO.COM. |

#### <a name="remarks"></a>Замечания

- Флаги сферы задают дополнительные возможности области Kerberos, которые не основаны на операционной системе Windows Server. Компьютеры под управлением Windows Server могут использовать сервер Kerberos для администрирования проверки подлинности в области Kerberos вместо использования домена под управлением операционной системы Windows Server. Эта запись устанавливает функции области и имеет следующие значения:

| Значение | Флаг области | Описание |
| ----- | ---------- | ----------- |
| 0xF | Все | Заданы все флаги сферы. |
| 0x00 | None | Флаги области не заданы, а дополнительные функции не включены. |
| 0x01 | сендаддресс | IP-адрес будет включаться в билеты предоставления билетов. |
| 0x02 | ткпсуппортед | В этой области поддерживаются протоколы TCP и UDP (User Datagram Protocol). |
| 0x04 | delegate | Все пользователи в этой области являются доверенными для делегирования. |
| 0x08 | нксуппортед | Эта область поддерживает канонизации имен, что позволяет использовать стандарты именования DNS и областей. |
| 0x80 | RC4 | Эта область поддерживает шифрование RC4 для включения доверительных отношений между сферами, что позволяет использовать TLS. |

- Флаги сферы хранятся в реестре в разделе `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\Kerberos\Domains\<realmname>` . Эта запись не существует в реестре по умолчанию. Для заполнения реестра можно использовать команду [ksetup аддреалмфлагс](ksetup-addrealmflags.md) .

- Чтобы увидеть доступные и установленные флаги области, просмотрите выходные данные **ksetup** или `ksetup /dumpstate` .

### <a name="examples"></a>Примеры

Чтобы получить список доступных и задать флаги области для области CONTOSO, введите:

```
ksetup
```

Чтобы установить два флага, которые сейчас не заданы, введите:

```
ksetup /setrealmflags CONTOSO ncsupported delegate
```

Чтобы проверить, установлен ли флаг области, введите `ksetup` и просмотрите выходные данные, выполняя поиск текста, **Флаги области =**. Если текст не отображается, это означает, что флаг не установлен.

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда ksetup](ksetup.md)

- [ksetup листреалмфлагс, команда](ksetup-listrealmflags.md)

- [ksetup аддреалмфлагс, команда](ksetup-addrealmflags.md)

- [ksetup делреалмфлагс, команда](ksetup-delrealmflags.md)

- [ksetup думпстате, команда](ksetup-dumpstate.md)
