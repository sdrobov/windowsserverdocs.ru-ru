---
title: reg add
description: Справочная статья по команде reg Add, которая добавляет новый подраздел или запись в реестр.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d9ad143e-dc10-4e2e-a229-408393c40079
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: db968e8fb55a4de73f5221f8149f794600f6884e
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85933509"
---
# <a name="reg-add"></a>reg add

Добавляет новый подраздел или запись в реестр.

## <a name="syntax"></a>Синтаксис

```
reg add <keyname> [{/v Valuename | /ve}] [/t datatype] [/s Separator] [/d Data] [/f]
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
|--|--|
| `<keyname>` | Задает полный путь к добавляемому подразделу или записи. Чтобы указать удаленный компьютер, включите имя компьютера (в формате `\\<computername>\` ) в состав имени *keyName*. Пропуск `\\<computername>\` приводит к тому, что по умолчанию операция выполняется на локальном компьютере. *KeyName* должен содержать допустимый корневой ключ. Допустимые корневые ключи для локального компьютера: **HKLM**, **HKCU**, **HKCR**, **HKU**и **хккк**. Если указан удаленный компьютер, допустимые корневые ключи: **HKLM** и **HKU**. Если имя раздела реестра содержит пробел, заключите имя ключа в кавычки. |
| /v`<Valuename>` | Указывает имя для добавления записи в реестр. |
| /ве | Указывает, что добавленная запись реестра имеет значение null. |
| /t`<Type>` | Указывает тип для записи реестра. *Тип* должен быть одним из следующих:<ul><li>REG_SZ</li><li>REG_MULTI_SZ</li><li>REG_DWORD_BIG_ENDIAN</li><li>REG_DWORD</li><li>REG_BINARY</li><li>REG_DWORD_LITTLE_ENDIAN</li><li>REG_LINK</li><li>REG_FULL_RESOURCE_DESCRIPTOR</li><li>REG_EXPAND_SZ</li></ul> |
| ключ`<Separator>` | Задает символ, используемый для разделения нескольких экземпляров данных, если указан **REG_MULTI_SZ** тип данных и указано несколько записей. Если значение не указано, разделителем по умолчанию является **\ 0**. |
| /d`<Data>` | Задает данные для новой записи реестра. |
| /f | Добавляет запись реестра без запроса подтверждения. |
| /? | Отображение справки в командной строке. |

#### <a name="remarks"></a>Комментарии

- С этой операцией нельзя добавлять поддеревья. Эта версия **reg** не запрашивает подтверждение при добавлении подраздела.

- Возвращаемые значения для операции **reg Add** :

| Значение | Описание: |
|--|--|
| 0 | Успех |
| 1 | Failure |

- Для **REG_EXPAND_SZ** типа ключа используйте символ крышки ( **^** ) с **%** параметром/d.

### <a name="examples"></a>Примеры

Чтобы добавить ключ *хклм\софтваре\мико* на удаленном компьютере *ABC*, введите:

```
reg add \\ABC\HKLM\Software\MyCo
```

Чтобы добавить запись реестра в *хклм\софтваре\мико* со значением с именем *Data*, *REG_BINARY*типа и данными *fe340ead*, введите:

```
reg add HKLM\Software\MyCo /v Data /t REG_BINARY /d fe340ead
```

Чтобы добавить многозначную запись реестра в *хклм\софтваре\мико* со значением *MRU*, Type *REG_MULTI_SZ*и Data of *fax\0mail\0\0*, введите:

```
reg add HKLM\Software\MyCo /v MRU /t REG_MULTI_SZ /d fax\0mail\0\0
```

Чтобы добавить развернутую запись реестра в *хклм\софтваре\мико* со значением *path*, *REG_EXPAND_SZ*типа и данными *% systemroot%*, введите:

```
reg add HKLM\Software\MyCo /v Path /t REG_EXPAND_SZ /d ^%systemroot^%
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
