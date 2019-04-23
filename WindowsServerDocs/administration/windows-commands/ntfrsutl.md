---
title: ntfrsutl
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d7721a19-5a87-4ab6-b816-65d2da2c811f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2dd245b7d85d6d5668262d3800ab72e35b852246
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59836625"
---
# <a name="ntfrsutl"></a>ntfrsutl

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Создает дамп внутренних таблиц, потоков и сведения о памяти для службы репликации файлов NT \(NTFRS\). Оно работает с локальными и удаленными серверами. Параметр восстановления для NTFRS в диспетчере управления службами \(SCM\) могут быть критически важными для поиска и поддержание важные журнала событий на компьютере. Это средство предоставляет удобный способ просмотра этих параметров.   
  
## <a name="syntax"></a>Синтаксис  
  
```  
ntfrsutl[idtable|configtable|inlog|outlog][<computer>]  
ntfrsutl[memory|threads|stage][<computer>]  
ntfrsutl ds[<computer>]  
ntfrsutl [sets][<computer>]  
ntfrsutl [version][<computer>]  
ntfrsutl poll[/quickly[=[<N>]]][/slowly[=[<N>]]][/now][<computer>]  
```  
  
### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|-------|--------|  
|idtable|Идентификатор таблицы|  
|configtable|Таблица конфигурации FRS|  
|inlog|Входящий журнала|  
|outlog|Исходящий журнал сервера|  
|<computer>|Задает имя компьютера.|  
|memory.|Использование памяти|  
|Потоки||  
|разместить||  
|доменных служб Active Directory|список службу NTFRS представление доменных служб Active Directory.|  
|Наборы|Указывает наборы активной реплики|  
|version|Указывает версии службы NTFRS и API.|  
|Опрос|Указывает текущий интервалы опроса.<br /><br />Параметры:<br /><br /><ul><li>**\/быстро** \[ **\=** \[ <N> \] \] \(опрашивает быстро  \)<br /><br /><ul><li>**быстро** \- опрашивает быстро до стабильная конфигурация rectrieved</li><li>**быстро\=**  \- быстро опрашивает каждые минут по умолчанию.</li><li>**быстро\=**  <N> \- быстро опрашивает каждый *N* минут</li></ul></li><li>**\/медленно** \[ **\=** \[ <N> \] \] \(опрашивает медленно\)<br /><br /><ul><li>**медленно** \- опрашивает медленно, пока не будет получено стабильная конфигурация</li><li>**медленно\=**  \- медленно опрашивает каждые минут по умолчанию</li><li>**медленно\=**  <N> \- быстро опрашивает каждый *N* минут</li></ul></li><li>**\/Теперь** \(опрашивает теперь\)</li></ul>|  
|\/?|Отображение справки в командной строке.|  
  
## <a name="BKMK_Examples"></a>Примеры  
Чтобы определить интервал опроса для репликации файлов:  
  
```  
C:\Program Files\SupportTools>ntfrsutl poll wrkstn-1  
```  
  
Чтобы определить текущий интерфейс прикладного программирования NTFRS \(API\) версии:  
  
```  
C:\Program Files\SupportTools>ntfrsutl version  
```  
  
## <a name="additional-references"></a>Дополнительные ссылки  
  
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  
  
  
  

