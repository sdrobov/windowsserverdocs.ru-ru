---
title: Начало работы с Windows Admin Center
description: Начало работы с Windows Admin Center
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.date: 02/15/2019
ms.openlocfilehash: f4fd9f69e75ed80bbdb345b4041c2337c65ec2e6
ms.sourcegitcommit: 2977c707a299929c6ab0d1e0adab2e1c644b8306
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63742670"
---
# <a name="get-started-with-windows-admin-center"></a>Начало работы с Windows Admin Center

>Область применения. Windows Admin Center, предварительная версия Windows Admin Center

> [!Tip]
> Только начинаете знакомство с Windows Admin Center?
> [Узнайте дополнительные сведения о Windows Admin Center](../understand/windows-admin-center.md) или [скачайте платформу](https://aka.ms/windowsadmincenter).

## <a name="windows-admin-center-installed-on-windows-10"></a>Windows Admin Center установлена в Windows 10

> [!IMPORTANT]
> Необходимо быть членом группы локальных администраторов для использования Windows Admin Center в Windows 10

### <a name="selecting-a-client-certificate"></a>Выбор сертификата клиента

В первый раз, при открытии Windows Admin Center в Windows 10, не забудьте выбрать *клиента Windows Admin Center* сертификата (в противном случае вы получите сообщение об ошибке HTTP 403, ссылкой, «не удается получить на эту страницу»).

В Microsoft Edge, когда появится это диалоговое окно:
 
1. Нажмите кнопку **больше вариантов**

    ![](../media/launch-cert-1.png)

2. Выберите сертификат с меткой **клиента Windows Admin Center** и нажмите кнопку **ОК**

    ![](../media/launch-cert-2.png)

3. Убедитесь, что **всегда разрешения доступа к** выбран и нажмите кнопку **разрешить**

    ![](../media/launch-cert-3.png)

## <a name="connecting-to-managed-nodes-and-clusters"></a>Подключение к управляемых узлов и кластеров

После завершения установки Windows Admin Center, можно добавить серверы или кластеры для управления на главной обзорной странице.

 **Добавление одного сервера или кластера в качестве управляемого узла**

 1. Нажмите кнопку **+ добавить** под **все подключения**.

    ![](../media/launch/addserver0.png)

 2. Выберите для добавления сервера, отказоустойчивого кластера или кластера Hyper-Converged соединения:
    
    ![](../media/launch/addserver1.png)

 3. Введите имя сервера или кластера для управления и нажмите кнопку **отправить**. Сервер или кластер, будут добавляться в список соединений на странице "Обзор".

    ![](../media/launch/addserver2.png)

   **--ИЛИ--**

**Массовый импорт нескольких серверов**

 1. На **добавить соединение с сервером** выберите **импорта серверов** вкладки.

    ![](../media/launch/import-servers.png)

 2. Нажмите кнопку **Обзор** и выберите файл, содержит запятую или новой строки разделены, список полных доменных имен для серверов, которые требуется добавить.

    **--ИЛИ--**

**Добавьте серверы, поиск по Active Directory**

 1. На **добавить соединение с сервером** выберите **поиск в Active Directory** вкладки.

    ![](../media/launch/search-ad.png)

 2. Введите условия поиска и нажмите кнопку **поиска**. Поддерживаются подстановочные знаки (*).

 3. После завершения поиска - выберите один или несколько результатов, при необходимости добавить теги и нажмите кнопку **добавить**.

## <a name="authenticate-with-the-managed-node"></a>Проверка подлинности с помощью управляемого узла ##

Windows Admin Center поддерживает несколько механизмов проверки подлинности с помощью управляемого узла. Единый вход по умолчанию.

**Единый вход**

Можно использовать текущие учетные данные Windows для проверки подлинности на управляемый узел. Это значение по умолчанию, а Windows Admin Center попыток входа, при добавлении сервера. 

**Единый вход при развертывании в качестве службы на базе Windows Server**

Если вы установили Windows Admin Center в Windows Server, дополнительная настройка не требуется для единого входа.  [Настройка среды для делегирования](..\configure\user-access-control.md)

**--ИЛИ--**

**Используйте *Manage As* чтобы указать учетные данные**

В разделе **все подключения**, выберите сервер из списка и выберите **Manage As** для указания учетных данных, которые будут использоваться для проверки подлинности на управляемый узел:

![](../media/launch-use-6.png)

Если Windows Admin Center, под управлением Windows Server в режиме службы, но у вас настроен делегирование Kerberos, необходимо повторно ввести учетные данные Windows:

![](../media/launch-use-7.png)

Учетные данные могут применяться ко всем подключениям, которые будут кэшировать их для этого сеанса конкретного браузера. Если вы перезапустите браузер, необходимо повторно ввести ваш **Manage As** учетные данные.

**Решение пароль локального администратора (LAP)**

Если в среде используется [LAPS](https://technet.microsoft.com/mt227395.aspx), LAPS учетные данные можно использовать для проверки подлинности на управляемый узел. **Если вы используете этот сценарий,** [отзыв](http://aka.ms/WACFeedback).

## <a name="using-tags-to-organize-your-connections"></a>Использование тегов для организации подключений

Теги можно использовать для выявления и фильтрации связанных серверов в список соединений.  Это дает возможность просмотра подмножества этих серверов в список соединений.  Это особенно полезно в том случае, если у вас есть много подключений.

### <a name="edit-tags"></a>Изменить теги

* Выберите сервер или несколько серверов в списке всех подключений
* В разделе **все подключения**, нажмите кнопку **изменить теги**

![](../media/launch/tags-5.png)

**Изменить теги подключения** области можно изменить, добавить или удалить теги из вашей выбранные подключения:

* Чтобы добавить новый тег в выбранные подключения, выберите **добавьте тег** и введите имя тега, который вы хотите использовать.

* Пометить выбранные соединения с существующим именем тега, установите флажок рядом с именем тега, который вы хотите применить.

* Чтобы удалить тег из всех выбранных подключений, снимите флажок рядом с тег, который нужно удалить.

* Если тег применяется к подмножеству выбранные соединения, флажок отображается в промежуточном состоянии. Если щелкнуть поле, чтобы проверить его и применить тег для всех выбранных подключений или щелкните еще раз, чтобы отключить его и удалите тег из всех выбранных подключений.

![](../media/launch/tags-6.png)

### <a name="filter-connections-by-tag"></a>Фильтрация подключений по тегу

После добавления тегов к одному или нескольким подключениям сервера, можно просматривать теги на список соединений и отфильтровать список соединений по тегам.

* Чтобы отфильтровать с помощью тега, выберите значок фильтра рядом с полем поиска.
![](../media/launch/tags-7.png)
* Можно выбрать «или», «и» или «not», чтобы изменить поведение фильтра выбранных тегов.
![](../media/launch/tags-8.png)

## <a name="use-powershell-to-import-or-export-your-connections-with-tags"></a>Использование PowerShell для импорта или экспорта подключений (с тегами)

> Область применения. Ознакомительная версия Windows Admin Center

Предварительная версия Windows Admin Center включает модуль PowerShell для импорта или экспорта в список соединений.

```powershell
# Load the module
Import-Module "$env:ProgramFiles\windows admin center\PowerShell\Modules\ConnectionTools"
# Available cmdlets: Export-Connection, Import-Connection

# Export connections (including tags) to .csv files
Export-Connection "https://wac.contoso.com" -fileName "WAC-connections.csv"
# Import connections (including tags) from .csv files
Import-Connection "https://wac.contoso.com" -fileName "WAC-connections.csv"
```

### <a name="csv-file-format-for-importing-connections"></a>CSV-файл для импорта подключений

Формат CSV-файл начинается с четырьмя заголовки ```"name","type","tags","groupId"```, а затем каждое подключение в новой строке.

**имя** -полное ДОМЕННОЕ имя подключения

**Тип** является тип соединения. Для подключений по умолчанию, в состав Windows Admin Center вам понадобится использовать одно из следующих:

| Тип подключения. | Строка подключения |
|------|-------------------------------|
| Windows Server | msft.sme.connection-type.server |
| Компьютер с Windows 10 | msft.sme.connection-type.windows-client |
| Отказоустойчивый кластер | msft.sme.connection-type.cluster |
| Гиперконвергированный кластер | msft.sme.connection-type.hyper-converged-cluster |

**теги** , отделенный вертикальной чертой.

**groupId** используется для общих подключений. Используйте значение ```global``` в этом столбце, чтобы сделать общее соединение.

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

## <a name="import-rdcman-connections"></a>Импортировать RDCman подключения

Используйте приведенный ниже сценарий, чтобы экспортировать сохраненным подключениям в [RDCman](https://blogs.technet.microsoft.com/rmilne/2014/11/19/remote-desktop-connection-manager-download-rdcman-2-7/) в файл. Затем можно импортировать файл в Windows Admin Center, обслуживание иерархии RDCMan группирования с помощью тегов. Просто попробуйте!

1. Скопируйте и вставьте приведенный ниже код в окно сеанса PowerShell:

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

3. Импортируйте полученный в результате. CSV-файла в Windows Admin Center и иерархию группирования RDCMan будут представлены по тегам в список соединений. Дополнительные сведения см. в разделе [использование PowerShell для импорта или экспорта подключений (с тегами)](#use-powershell-to-import-or-export-your-connections-with-tags).

## <a name="view-powershell-scripts-used-in-windows-admin-center"></a>Просмотра скриптов PowerShell, используемых в Windows Admin Center

После подключения для сервера, кластера или ПК, можно взглянуть на сценарии PowerShell, которые действия пользовательского интерфейса, доступные в Windows Admin Center. Из этой программы, щелкните значок PowerShell на панели часто используемых приложений. Выберите команду интерес из раскрывающегося списка, чтобы перейти в соответствующий сценарий PowerShell.

![](../media/launch/showscript.png)