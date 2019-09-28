---
title: Приступая к работе с центром администрирования Windows
description: Приступая к работе с центром администрирования Windows
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.localizationpriority: medium
ms.prod: windows-server
ms.date: 02/15/2019
ms.openlocfilehash: 68b5c7b2c5bc8e93d653514b2664d96b97b07a9e
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71406845"
---
# <a name="get-started-with-windows-admin-center"></a>Приступая к работе с центром администрирования Windows

>Область применения. Windows Admin Center, ознакомительная версия Windows Admin Center

> [!Tip]
> Только начинаете знакомство с Windows Admin Center?
> [Узнайте дополнительные сведения о Windows Admin Center](../understand/windows-admin-center.md) или [скачайте платформу](https://aka.ms/windowsadmincenter).

## <a name="windows-admin-center-installed-on-windows-10"></a>Центр администрирования Windows, установленный в Windows 10

> [!IMPORTANT]
> Для использования центра администрирования Windows в Windows 10 необходимо быть членом группы локальных администраторов

### <a name="selecting-a-client-certificate"></a>Выбор сертификата клиента

При первом открытии центра администрирования Windows в Windows 10 необходимо выбрать сертификат *клиента центра администрирования Windows* (в противном случае вы получите ошибку HTTP 403 с сообщением "не удается перейти на эту страницу").

В Microsoft погранично при появлении запроса в этом диалоговом окне:
 
1. Щелкните **больше вариантов**

    ![](../media/launch-cert-1.png)

2. Выберите сертификат под названием **клиент центра администрирования Windows** и нажмите кнопку **ОК** .

    ![](../media/launch-cert-2.png)

3. Убедитесь, что установлен флажок **всегда разрешать доступ** , и нажмите кнопку **Разрешить** .

    ![](../media/launch-cert-3.png)

## <a name="connecting-to-managed-nodes-and-clusters"></a>Подключение к управляемым узлам и кластерам

После завершения установки центра администрирования Windows можно добавить серверы или кластеры для управления с главной страницы обзора.

 **Добавление одного сервера или кластера в качестве управляемого узла**

1. Щелкните **+ Добавить** в разделе **все подключения**.

   ![](../media/launch/addserver0.png)

2. Выберите Добавление сервера, отказоустойчивого кластера или подключения к кластеру с поддержкой Hyper-in:
    
   ![](../media/launch/addserver1.png)

3. Введите имя сервера или кластера для управления и нажмите кнопку **Отправить**. Сервер или кластер будет добавлен в список подключений на странице "Обзор".

   ![](../media/launch/addserver2.png)

   **--ИЛИ--**

**Групповое импорт нескольких серверов**

 1. На странице **Добавление соединения с сервером** перейдите на вкладку **Импорт серверов** .

    ![](../media/launch/import-servers.png)

 2. Нажмите кнопку **Обзор** и выберите текстовый файл, содержащий запятую, или новую строку с разделителями полных доменных имен для добавляемых серверов.

> [!Note]
> CSV-файл, созданный при [экспорте подключений с помощью PowerShell](#use-powershell-to-import-or-export-your-connections-with-tags) , содержит дополнительные сведения за пределами имен серверов и не совместим с этим методом импорта.

  **--ИЛИ--**

**Добавление серверов путем поиска Active Directory**

 1. На странице **Добавление соединения с сервером** перейдите на вкладку **Поиск Active Directory** .

    ![](../media/launch/search-ad.png)

 2. Введите условия поиска и нажмите кнопку **Поиск**. Поддерживаются подстановочные знаки (*).

 3. После завершения поиска выберите один или несколько результатов, при необходимости добавьте теги и нажмите кнопку **Добавить**.

## <a name="authenticate-with-the-managed-node"></a>Проверка подлинности с помощью управляемого узла ##

Центр администрирования Windows поддерживает несколько механизмов проверки подлинности с помощью управляемого узла. По умолчанию используется единый вход.

**Единый вход**

Вы можете использовать текущие учетные данные Windows для проверки подлинности на управляемом узле. Это значение по умолчанию, и центр администрирования Windows пытается войти в систему при добавлении сервера. 

**Единый вход при развертывании в качестве службы в Windows Server**

Если вы установили центр администрирования Windows в Windows Server, для единого входа требуется дополнительная настройка.  [Настройка среды для делегирования](../configure/user-access-control.md)

**--ИЛИ--**

**Используйте *Управление как* для указания учетных данных**

В разделе **все подключения**выберите сервер из списка и щелкните **Управление как** , чтобы указать учетные данные, которые будут использоваться для проверки подлинности на управляемом узле.

![](../media/launch-use-6.png)

Если центр администрирования Windows работает в режиме службы в Windows Server, но делегирование Kerberos не настроено, необходимо повторно ввести учетные данные Windows:

![](../media/launch-use-7.png)

Вы можете применить учетные данные ко всем подключениям, которые будут кэшировать их для конкретного сеанса браузера. При перезагрузке браузера необходимо повторно ввести учетные данные **управления** .

**Решение "пароль локального администратора" (Lap)**

Если в вашей среде используется [Lap](https://technet.microsoft.com/mt227395.aspx)и на компьютере под управлением Windows 10 установлен центр администрирования Windows, для проверки подлинности на управляемом узле можно использовать учетные данные Lap. **Если вы используете этот сценарий,** [оставить отзыв](http://aka.ms/WACFeedback).

## <a name="using-tags-to-organize-your-connections"></a>Использование тегов для Организации подключений

Теги можно использовать для поиска и фильтрации связанных серверов в списке подключений.  Это позволяет просматривать подмножество серверов в списке подключений.  Это особенно удобно при наличии большого числа подключений.

### <a name="edit-tags"></a>Изменить Теги

* Выберите сервер или несколько серверов в списке все подключения
* В разделе **все подключения**щелкните **изменить теги** .

![](../media/launch/tags-5.png)

Панель **изменение тегов подключения** позволяет изменять, добавлять или удалять теги выбранных соединений.

* Чтобы добавить новый тег к выбранным соединениям, выберите **Добавить тег** и введите имя тега, который вы хотите использовать.

* Чтобы пометить выбранные соединения с существующим именем тега, установите флажок рядом с именем тега, который вы хотите применить.

* Чтобы удалить тег из всех выбранных подключений, снимите флажок рядом с тегом, который вы хотите удалить.

* Если к подмножеству выбранных соединений применяется тег, флажок отображается в промежуточном состоянии. Можно щелкнуть поле, чтобы проверить его и применить тег ко всем выбранным подключениям, или щелкнуть еще раз, чтобы снять его, и удалить тег из всех выбранных подключений.

![](../media/launch/tags-6.png)

### <a name="filter-connections-by-tag"></a>Фильтрация подключений по тегу

После добавления тегов в одно или несколько подключений к серверу можно просмотреть теги в списке подключений и отфильтровать список подключений по тегам.

* Чтобы выполнить фильтрацию по тегу, щелкните значок фильтра рядом с полем поиска.
![](../media/launch/tags-7.png)
* Можно выбрать "или", "и" или "не", чтобы изменить поведение фильтра для выбранных тегов.
![](../media/launch/tags-8.png)

## <a name="use-powershell-to-import-or-export-your-connections-with-tags"></a>Использование PowerShell для импорта или экспорта подключений (с тегами)

```powershell
# Load the module
Import-Module "$env:ProgramFiles\windows admin center\PowerShell\Modules\ConnectionTools"
# Available cmdlets: Export-Connection, Import-Connection

# Export connections (including tags) to .csv files
Export-Connection "https://wac.contoso.com" -fileName "WAC-connections.csv"
# Import connections (including tags) from .csv files
Import-Connection "https://wac.contoso.com" -fileName "WAC-connections.csv"
```

### <a name="csv-file-format-for-importing-connections"></a>Формат CSV-файла для импорта подключений

Формат CSV-файла начинается с четырех заголовков ```"name","type","tags","groupId"```, за которыми следуют все соединения в новой строке.

**Name** — полное доменное имя подключения

**тип** — тип соединения. Для соединений по умолчанию, входящих в состав центра администрирования Windows, вы будете использовать один из следующих параметров:

| Тип подключения. | Строка подключения |
|------|-------------------------------|
| Windows Server | MSFT. Эксперт. Connection-Type. Server |
| ПК с Windows 10 | MSFT. Эксперт. Connection-Type. Windows-Client |
| Отказоустойчивый кластер | MSFT. Эксперт. Connection — Type. Cluster |
| Кластер с технологией Hyper-in | MSFT. Эксперт. Connection-Type. Hyper-схождения-Cluster |

**теги** разделяются вертикальной чертой.

**groupId** используется для общих соединений. Используйте значение ```global``` в этом столбце, чтобы сделать это общим соединением.

### <a name="example-csv-file-for-importing-connections"></a>Пример CSV-файла для импорта подключений

```
"name","type","tags","groupId"
"myServer.contoso.com","msft.sme.connection-type.server","hyperv"
"myDesktop.contoso.com","msft.sme.connection-type.windows-client","hyperv"
"teamcluster.contoso.com","msft.sme.connection-type.cluster","legacyCluster|WS2016","global"
"myHCIcluster.contoso.com,"msft.sme.connection-type.hyper-converged-cluster","myHCIcluster|hyperv|JIT|WS2019"
"teamclusterNode.contoso.com","msft.sme.connection-type.server","legacyCluster|WS2016","global"
"myHCIclusterNode.contoso.com","msft.sme.connection-type.server","myHCIcluster|hyperv|JIT|WS2019"
```

## <a name="import-rdcman-connections"></a>Импорт подключений Рдкман

Используйте приведенный ниже сценарий для экспорта сохраненных соединений в [рдкман](https://blogs.technet.microsoft.com/rmilne/2014/11/19/remote-desktop-connection-manager-download-rdcman-2-7/) в файл. Затем можно импортировать файл в центр администрирования Windows, сохранив иерархию группирования Рдкман с помощью тегов. Попробуйте!

1. Скопируйте приведенный ниже код и вставьте его в сеанс PowerShell:

   ```powershell
   #Helper function for RdgToWacCsv
   function AddServers {
    param (
    [Parameter(Mandatory = $true)]
    [Xml.XmlLinkedNode]
    $node,
    [Parameter()]
    [String[]]
    $tags,
    [Parameter(Mandatory = $true)]
    [String]
    $csvPath
    )
    if ($node.LocalName -eq 'server') {
        $serverName = $node.properties.name
        $tagString = $tags -join "|"
        Add-Content -Path $csvPath -Value ('"'+ $serverName + '","msft.sme.connection-type.server","'+ $tagString +'"')
    } 
    elseif ($node.LocalName -eq 'group' -or $node.LocalName -eq 'file') {
        $groupName = $node.properties.name
        $tags+=$groupName
        $currNode = $node.properties.NextSibling
        while ($currNode) {
            AddServers -node $currNode -tags $tags -csvPath $csvPath
            $currNode = $currNode.NextSibling
        }
    } 
    else {
        # Node type isn't relevant to tagging or adding connections in WAC
    }
    return
   }

   <#
   .SYNOPSIS
   Convert an .rdg file from Remote Desktop Connection Manager into a .csv that can be imported into Windows Admin Center, maintaining groups via server tags. This will not modify the existing .rdg file and will create a new .csv file

    .DESCRIPTION
    This converts an .rdg file into a .csv that can be imported into Windows Admin Center.

    .PARAMETER RDGfilepath
    The path of the .rdg file to be converted. This file will not be modified, only read.

    .PARAMETER CSVdirectory
    Optional. The directory you wish to export the new .csv file. If not provided, the new file is created in the same directory as the .rdg file.

    .EXAMPLE
    C:\PS> RdgToWacCsv -RDGfilepath "rdcmangroup.rdg"
    #>
   function RdgToWacCsv {
    param(
        [Parameter(Mandatory = $true)]
        [String]
        $RDGfilepath,
        [Parameter(Mandatory = $false)]
        [String]
        $CSVdirectory
    )
    [xml]$RDGfile = Get-Content -Path $RDGfilepath
    $node = $RDGfile.RDCMan.file
    if (!$CSVdirectory){
        $csvPath = [System.IO.Path]::GetDirectoryName($RDGfilepath) + [System.IO.Path]::GetFileNameWithoutExtension($RDGfilepath) + "_WAC.csv"
    } else {
        $csvPath = $CSVdirectory + [System.IO.Path]::GetFileNameWithoutExtension($RDGfilepath) + "_WAC.csv"
    }
    New-item -Path $csvPath
    Add-Content -Path $csvPath -Value '"name","type","tags"'
    AddServers -node $node -csvPath $csvPath
    Write-Host "Converted $RDGfilepath `nOutput: $csvPath"
   }
   ```

2. Для создания. CSV-файл, выполните следующую команду:

   ```powershell
   RdgToWacCsv -RDGfilepath "path\to\myRDCManfile.rdg"
   ```

3. Импортируйте полученный результат. CSV-файл в центре администрирования Windows, и вся иерархия группирования Рдкман будет представлена тегами в списке соединений. Дополнительные сведения см. [в статье Импорт и экспорт подключений с помощью PowerShell (с помощью тегов)](#use-powershell-to-import-or-export-your-connections-with-tags).

## <a name="view-powershell-scripts-used-in-windows-admin-center"></a>Просмотр сценариев PowerShell, используемых в центре администрирования Windows

После подключения к серверу, кластеру или ПК можно просмотреть сценарии PowerShell, которые позволяют получить доступ к действиям пользовательского интерфейса в центре администрирования Windows. В средстве щелкните значок PowerShell на верхней панели приложения. Выберите команду из раскрывающегося списка для перехода к соответствующему скрипту PowerShell.

![](../media/launch/showscript.png)