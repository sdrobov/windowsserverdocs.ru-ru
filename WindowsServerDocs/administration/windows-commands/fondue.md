---
title: fondue
description: Раздел Windows команды для ****-
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: fc4467f6-ddbb-4d6d-b51e-5a50a957b8c0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 87af579d25e52543fe03159c40688f1e7540dcc9
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80844597"
---
# <a name="fondue"></a>fondue

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Включает дополнительные компоненты Windows, загружая необходимые файлы из Центр обновления Windows или другого источника, указанного групповая политика. Файл манифеста для компонента уже должен быть установлен в образе Windows. 
## <a name="syntax"></a>Синтаксис
```
fondue.exe /enable-feature:<feature_name> [/caller-name:<program_name>] [/hide-ux:{all | rebootRequest}]
```
#### <a name="parameters"></a>Параметры

|              Параметр              |                                                                                                                                                                     Описание                                                                                                                                                                     |
|-------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  /Enable-Feature: <*feature_name*>   |                                                                               Указывает имя необязательного компонента Windows, который требуется включить. В командную строку можно включить только один компонент. Чтобы включить несколько функций, используйте фондуе. exe для каждого компонента.                                                                                |
|    /Каллер-наме: <*program_name*>    |                                                                                 Указывает имя программы или процесса при вызове фондуе. exe из скрипта или пакетного файла. Этот параметр можно использовать для добавления имени программы в отчет SQM при возникновении ошибки.                                                                                 |
| /Хиде-УКС: {ALL &#124; ребутрекуест} | Используйте **ALL** , чтобы скрыть все сообщения для пользователя, включая ход выполнения и запросы разрешений на доступ к центр обновления Windows. Если требуется разрешение, операция завершится ошибкой.<p>Используйте **ребутрекуест** , чтобы скрыть только пользовательские сообщения, запрашивающие разрешение на перезагрузку компьютера. Используйте этот параметр, если у вас есть сценарий, управляющий запросами на перезагрузку. |

## <a name="examples"></a><a name=BKMK_Examples></a>Примеров
Чтобы включить Microsoft .NET Framework 3,5, введите:
```
fondue.exe /enable-feature:NETFX3
```
Чтобы включить Microsoft .NET Framework 3,5, добавьте имя программы в отчет SQM и не выводите сообщения пользователю, введите:
```
fondue.exe /enable-feature:NETFX3 /caller-name:Admin.bat /hide-ux:all
```
## <a name="additional-references"></a>Дополнительные материалы
- - [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
  ## <a name="see-also"></a>См. также
  [Рекомендации по развертыванию Microsoft .NET Framework 3,5](https://go.microsoft.com/fwlink/?LinkId=248869)
