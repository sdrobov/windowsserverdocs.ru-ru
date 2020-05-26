---
title: ksetup делкдк
description: Справочный раздел по команде ksetup делкдк, который удаляет экземпляры имен центр распространения ключей (KDC) для области Kerberos.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7d6ec389-094c-4a7b-a78b-605497ddc289
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bd3901558f1cda0d2e1d4e7c12b0d2b151870fa8
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2020
ms.locfileid: "83817854"
---
# <a name="ksetup-delkdc"></a>ksetup делкдк

Удаляет экземпляры имен центр распространения ключей (KDC) для области Kerberos.

Сопоставление сохраняется в реестре в разделе `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\LSA\Kerberos\Domains` . После выполнения этой команды рекомендуется убедиться, что KDC был удален и больше не отображается в списке.

> [!NOTE]
> Чтобы удалить данные конфигурации сферы с нескольких компьютеров, используйте оснастку " **шаблон конфигурации безопасности** " с распределением политик, а не используйте команду **ksetup** явным образом на отдельных компьютерах.

## <a name="syntax"></a>Синтаксис

```
ksetup /delkdc <realmname> <KDCname>
```

### <a name="parameters"></a>Параметры

| Параметр | Описание |
| --------- | ----------- |
| `<realmname>` | Указывает DNS-имя в верхнем регистре, например CORP. CONTOSO.COM. Это область по умолчанию, которая отображается при выполнении команды **ksetup** и представляет собой область, из которой необходимо удалить KDC. |
| `<KDCname>` | Задает с учетом регистра полное доменное имя, например mitkdc.contoso.com. |

### <a name="examples"></a>Примеры

Чтобы просмотреть все связи между областью Windows и областью, отличной от Windows, и определить, какие из них нужно удалить, введите:

```
ksetup
```

Чтобы удалить связь, введите:

```
ksetup /delkdc CORP.CONTOSO.COM mitkdc.contoso.com
```

## <a name="additional-references"></a>Дополнительные ссылки

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)

- [Команда ksetup](ksetup.md)

- [ksetup аддкдк, команда](ksetup-addkdc.md)