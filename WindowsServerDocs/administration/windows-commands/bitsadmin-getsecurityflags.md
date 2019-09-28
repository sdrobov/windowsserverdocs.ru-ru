---
title: битсадмин жетсекуритифлагс
description: Раздел команд Windows для **битсадмин жетсекуритифлагс** . сообщает о флагах безопасности HTTP для перенаправления URL-адресов и проверках, выполняемых на сертификате сервера во время перемещения.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c2e73519-34f4-487b-af11-97d5d08ef9bb
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fb53664a6366b411ae1eb9b0fe7c93392d60b542
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381456"
---
# <a name="bitsadmin-getsecurityflags"></a>битсадмин жетсекуритифлагс

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Сообщает о флагах безопасности HTTP для перенаправления URL-адресов и проверках, выполняемых на сертификате сервера во время перемещения.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /GetSecurityFlags <Job> 
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------|--------|
|Job|Отображаемое имя задания или идентификатор GUID|

## <a name="BKMK_examples"></a>Примеров
В следующем примере извлекаются флаги секуритли из задания с именем *myJob*.

```
C:\>bitsadmin /GetSecurityFlags myJob 
```

## <a name="additional-references"></a>Дополнительные ссылки
[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)


