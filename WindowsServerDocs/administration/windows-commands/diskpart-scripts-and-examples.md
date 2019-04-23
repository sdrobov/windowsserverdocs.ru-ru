---
title: DiskPart сценарии и примеры
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 319c0795-11df-47c8-b203-eadb0577ee0d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a8bd0dfab98ca705cf64766d66285c69bd3d3129
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59862795"
---
# <a name="diskpart-scripts-and-examples"></a>DiskPart сценарии и примеры

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

С помощью Diskpart `/s` для запуска сценариев, автоматизирующих диска\-связанных задач, таких как создание томов или преобразование дисков в динамические диски. Этих задач скрипта полезно в том случае, если развертывается Windows с помощью автоматической установки или средство Sysprep, которые не поддерживают создание томов, отличный от загрузочного тома.  
  
-   Для создания сценария Diskpart, создайте текстовый файл, содержащий команды Diskpart, которые вы хотите запустить, с помощью одной команды на строку, а не пустые строки. Можно запустить строку с `rem` создать комментарий к строке.  
  
    Например здесь s скрипт, который очищает диск, а затем создает раздел 300 МБ для среды восстановления Windows:  
  
    ```  
    select disk 0  
    clean  
    convert gpt  
    create partition primary size=300  
    format quick fs=ntfs label="Windows RE tools"  
    assign letter="T"  
    ```  
  
-   Чтобы запустить сценарий DiskPart, в командной строке, введите следующую команду, где *scriptname* имя текстового файла, содержащего сценарий.  
  
    ```  
    diskpart /s scriptname.txt  
    ```  
  
-   Чтобы перенаправить вывод сценария DiskPart в файл, введите следующую команду, где *файл журнала* — это имя текстового файла, где DiskPart записывает выходные данные.  
  
    ```  
    diskpart /s scriptname.txt > logfile.txt  
    ```  
  
> [!IMPORTANT]  
> При использовании **DiskPart** команды как часть сценария, мы рекомендуем выполнить все операции DiskPart вместе как часть единого сценария DiskPart. Можно выполнять ряд сценариев DiskPart, но необходимо разрешить по крайней мере 15 секунд между сценариями для полного завершения предыдущего выполнения перед запуском **DiskPart** команду еще раз в предыдущем сценарии. В противном случае произойдет сбой. Можно добавить паузу между последовательными сценариями DiskPart, добавив `timeout /t 15` команду пакетный файл сценариев DiskPart.  
  
При запуске DiskPart версии и имя компьютера отображаются в командной строке. По умолчанию, если DiskPart, возникает ошибка при попытке выполнить задачу сценария останавливает обработку сценария DiskPart и отображает код ошибки \(Если вы не указали **успешного** параметр\). Тем не менее, DiskPart всегда возвращает ошибки, если обнаруживает синтаксические ошибки, независимо от того, используется ли **успешного** параметра. **Успешного** параметр позволяет выполнять полезных задач, таких как использование одного сценария для удаления всех разделов на всех дисках, независимо от того, общее число дисков.  
  
## <a name="see-also"></a>См. также  
[Пример: Настройка единого интерфейса EFI\/gpt\-на основе разделов жесткого диска, с помощью среды Предустановки Windows и DiskPart](https://technet.microsoft.com/library/hh825686.aspx)  
[Пример: Настроить BIOS\/MBR\-на основе разделов жесткого диска с помощью Windows PE и DiskPart](https://technet.microsoft.com/library/hh825677.aspx)  
[Командлеты хранилища в Windows PowerShell](https://technet.microsoft.com/library/hh848705.aspx)  
  

