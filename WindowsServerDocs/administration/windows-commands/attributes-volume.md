---
title: Атрибуты тома
description: Раздел команд Windows для **атрибута Volume**, который отображает, устанавливает или очищает атрибуты тома.
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e40e8284-3d57-4de8-a46c-e4ade34a0d53
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 00991cdba57f0728cfa348dea2b0916ad758b34a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80851237"
---
# <a name="attributes-volume"></a>Атрибуты тома

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображает, устанавливает или очищает атрибуты тома.

## <a name="syntax"></a>Синтаксис  

```
attributes volume [{set | clear}] [{hidden | readonly | nodefaultdriveletter | shadowcopy}] [noerr]  
```  
  
### <a name="parameters"></a>Параметры  
  
| Параметр | Описание |  
| ------- | -------- |  
| set | Задает указанный атрибут тома с фокусом. |  
| очистить | Очищает указанный атрибут тома с фокусом. |  
| доступно | Указывает, что том доступен только для чтения. |  
| служеб | Указывает, что том скрыт. |  
| нодефаултдривелеттер | Указывает, что том не получает букву диска по умолчанию. |  
| SHADOWCOPY | Указывает, что том является томом теневого копирования. |  
| Noerr | Только для сценариев. При возникновении ошибки DiskPart продолжит обрабатывать команды, как если бы ошибка не возникала. Без этого параметра ошибка приводит к выходу из программы DiskPart с кодом ошибки. |  
  
## <a name="remarks"></a>Примечания  
  
- На основных дисках основной загрузочной записи (MBR) параметры **Hidden**, **ReadOnly**и **нодефаултдривелеттер** применяются ко всем томам на диске.  
  
- На основных дисках таблицы разделов GPT, а также на динамических дисках MBR и GPT параметры **Hidden**, **ReadOnly**и **нодефаултдривелеттер** применяются только к выбранному тому.  
  
- Чтобы команда **атрибутов тома** была выполнена, необходимо выбрать том. Используйте команду **выбрать том** , чтобы выбрать том и переместить фокус на него.  
  
## <a name="examples"></a><a name=BKMK_examples></a>Примеров

Чтобы отобразить текущие атрибуты выбранного тома, введите:  
  
```
attributes volume  
```  
  
Чтобы задать выбранный том как скрытый и только для чтения, введите:  
  
```
attributes volume set hidden readonly  
```  
  
Чтобы удалить скрытые и атрибуты только для чтения на выбранном томе, введите:  
  
```
attributes volume clear hidden readonly  
```  
  
## <a name="additional-references"></a>Дополнительные материалы  

- [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)