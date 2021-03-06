---
title: ksetup listrealmflags
description: Справочная статья по команде ksetup листреалмфлагс, в которой перечислены доступные флаги области, которые можно сообщить по ksetup.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: aa96e4da-6b98-4c05-bccf-73cbf33258c2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d094b7d627885d25313b73bb51a1bbeeec2832d6
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85933686"
---
# <a name="ksetup-listrealmflags"></a>ksetup listrealmflags

Список доступных флагов области, которые могут быть переданы по **ksetup**.

## <a name="syntax"></a>Синтаксис

```
ksetup /listrealmflags
```

### <a name="remarks"></a>Примечания

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

- Флаги сферы хранятся в реестре в разделе `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\Kerberos\Domains\<realmname>` . Эта запись не существует в реестре по умолчанию. Для заполнения реестра можно использовать [команду ksetup аддреалмфлагс](ksetup-addrealmflags.md) .

## <a name="examples"></a>Примеры

Чтобы получить список известных флагов области на этом компьютере, введите:

```
ksetup /listrealmflags
```

Чтобы установить доступные флаги области, которые **ksetup** не знает, введите:

```
ksetup /setrealmflags CORP.CONTOSO.COM sendaddress tcpsupported delete ncsupported
```

**Ни**

```
ksetup /setrealmflags CORP.CONTOSO.COM 0xF
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда ksetup](ksetup.md)

- [ksetup аддреалмфлагс, команда](ksetup-addrealmflags.md)

- [ksetup сетреалмфлагс, команда](ksetup-setrealmflags.md)

- [ksetup делреалмфлагс, команда](ksetup-delrealmflags.md)
