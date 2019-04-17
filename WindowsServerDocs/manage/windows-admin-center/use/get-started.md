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
ms.sourcegitcommit: f1edfc6525e09dd116b106293f9260123a94de0c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "9296656"
---
# Начало работы с Windows Admin Center

>Относится к: Windows Admin Center, ознакомительная версия Windows Admin Center

> [!Tip]
> Только начинаете знакомство с Windows Admin Center?
> [Узнайте дополнительные сведения о Windows Admin Center](../understand/windows-admin-center.md) или [скачайте платформу](https://aka.ms/windowsadmincenter).

## Windows Admin Center установлен в Windows 10

> [!IMPORTANT]
> Вы должны быть членом группы локального администратора для использования Windows Admin Center в Windows 10

### Выбор сертификата клиента

При первом открытии Windows Admin Center в Windows 10, обязательно выберите Windows Admin Center сертификата *Клиента* (в противном случае отобразится ошибка HTTP 403 с сообщением «не удается получить на эту страницу»).

В Microsoft Edge, когда появится следующее диалоговое окно:
 
1. Выберите **Дополнительные варианты**

    ![](../media/launch-cert-1.png)

2. Выберите сертификат с надписью **Клиент Windows Admin Center** и нажмите кнопку **ОК**

    ![](../media/launch-cert-2.png)

3. Убедитесь, что выбран **Всегда разрешить доступ** и нажмите кнопку **Разрешить**

    ![](../media/launch-cert-3.png)

## Подключение к управляемым узлам и кластерами

После завершения установки Windows Admin Center, вы можете добавить серверами или кластерами для управления на странице основных обзора.

 **Добавление одним сервером или кластером как управляемый узел**

 1. Выберите вариант **+ Добавить** **всех подключений**.

    ![](../media/launch/addserver0.png)

 2. Выберите для добавления подключения сервера, отказоустойчивого кластера или гиперконвергированном кластере:
    
    ![](../media/launch/addserver1.png)

 3. Введите имя сервера или кластера для управления и нажмите кнопку **отправки**. Серверу или кластеру будут добавлены в список подключения на странице "Обзор".

    ![](../media/launch/addserver2.png)

   **-- ИЛИ --**

**Массовый импорт нескольких серверов**

 1. На странице **Добавить подключения к серверу** выберите вкладку **Импорта серверов** .

    ![](../media/launch/import-servers.png)

 2. Нажмите кнопку **Обзор** и выберите текстовый файл, содержащий их запятыми или новую строку запятыми, список полных доменных имен для серверов, которые вы хотите добавить.

    **-- ИЛИ --**

**Добавление серверов, выполняя поиск Active Directory**

 1. На странице **Добавить подключения к серверу** выберите вкладку **Поиска Active Directory** .

    ![](../media/launch/search-ad.png)

 2. Введите условия поиска и нажмите кнопку **поиска**. Поддерживаются подстановочных знаков (*).

 3. После завершения поиска - установите один или несколько результатов, при необходимости добавить теги и нажмите кнопку **Добавить**.

## Проверки подлинности с помощью управляемому узлу ##

Windows Admin Center поддерживает несколько механизмов для проверки подлинности с помощью управляемого узла. Единый вход в значение по умолчанию.

**Единый вход**

Ваши учетные данные Windows можно использовать для проверки подлинности с помощью управляемому узлу. Это значение по умолчанию, после чего Windows Admin Center производится попытка входа в систему при добавлении сервера. 

**Единый вход при развертывании как служба в Windows Server**

Если вы установили Windows Admin Center в Windows Server, дополнительная настройка не требуется для единого входа.  [Настройка среды для делегирования](..\configure\user-access-control.md)

**-- ИЛИ --**

**Позволяет указать учетные данные *Manage As***

В разделе **Все подключения**выберите сервер из списка и выберите **Manage As** указать учетные данные, которые вы будете использовать для проверки подлинности к управляемому узлу.

![](../media/launch-use-6.png)

Если Windows Admin Center работает в режиме службы в Windows Server, но у вас не настроено делегирование Kerberos, необходимо повторно ввести учетные данные Windows:

![](../media/launch-use-7.png)

Можно применить учетные данные для всех подключений, которые будет кэшировать их для данного сеанса указанного браузера. При перезагрузке браузера, необходимо повторно ввести учетные данные **Manage As** .

**Решение пароль локального администратора (LAP)**

Если в среде используется [LAPS](https://technet.microsoft.com/mt227395.aspx), можно использовать LAPS учетные данные для проверки подлинности с помощью управляемому узлу. **Если вы используете этот сценарий, пожалуйста** [предоставить отзыв](http://aka.ms/WACFeedback).

## С помощью тегов организовать правильность связей

Теги можно использовать для выявления и фильтрации связанных серверов в вашем списке подключения.  Это позволяет увидеть подмножество серверов в списке подключение.  Это особенно полезно, если у вас много подключений.

### Редактирование тегов

* Выберите сервер или несколько серверов в списке все подключения
* В разделе **Все подключения**нажмите кнопку **Изменить теги**

![](../media/launch/tags-5.png)

Области **Изменить теги подключения** позволяет изменить, добавить или удалить теги из вашего выбранные подключения:

* Чтобы добавить новый тег вашего выбранные подключения, выберите **Добавить тег** и введите имя метки, которое вы хотите использовать.

* Для обозначения выбранных подключений с именем существующего тега, установите флажок рядом с именем тег, который вы хотите применить.

* Чтобы удалить тег из всех выбранных подключений, снимите флажок рядом с тег, который нужно удалить.

* Если тег применяется к подмножеству выбранных подключений, флажок будет отображаться в промежуточном состоянии. Можно щелкнуть поле, чтобы проверить и применить тег для всех выбранных подключений или щелкните еще раз, чтобы снять его и удалите тег из всех выбранных подключений.

![](../media/launch/tags-6.png)

### Фильтрация подключений по тега

После добавления тегов для одного или нескольких подключений к серверу, можно просматривать теги в списке подключение и отфильтруйте список, подключение с помощью тегов.

* Для фильтрации по тег, выберите значок фильтра рядом с полем поиска.
![](../media/launch/tags-7.png)
* Вы можете выбрать «или», «и» или «не» для изменения поведения Фильтр тегов, выбранного.
![](../media/launch/tags-8.png)

## Использование PowerShell для импорта и экспорта подключений (с тегами)

> Область применения: Ознакомительная версия Windows Admin Center

Ознакомительная версия Windows Admin Center включает модуль PowerShell для импорта и экспорта списка подключения.

```powershell
# Load the module
Import-Module "$env:ProgramFiles\windows admin center\PowerShell\Modules\ConnectionTools"
# Available cmdlets: Export-Connection, Import-Connection

# Export connections (including tags) to .csv files
Export-Connection "https://wac.contoso.com" -fileName "WAC-connections.csv"
# Import connections (including tags) from .csv files
Import-Connection "https://wac.contoso.com" -fileName "WAC-connections.csv"
```

### Формат CSV-файла для импорта подключения

Формат CSV-файла начинается с четырьмя заголовки ```"name","type","tags","groupId"```, а затем каждого подключения с новой строки.

**имя** — полное доменное имя подключения

**Тип** является типом подключения. Для подключений по умолчанию, включенные в Windows Admin Center используйте одно из указанных ниже:

| Тип подключения | Строки подключения |
|------|-------------------------------|
| Windows Server | MSFT.sme.Connection type.server |
| Компьютер с Windows 10 | MSFT.sme.Connection-type.windows клиента |
| Отказоустойчивый кластер | MSFT.sme.Connection type.cluster |
| Гиперконвергентного кластера | MSFT.sme.Connection-type.hyper--кластера |

**теги** , разделенных канала.

**groupId** используется для общего подключения. Используйте значение ```global``` в этой статье, чтобы сделать это общее подключение.

### Пример CSV-файл для импорта подключения

```
"name","type","tags","groupId"
"myServer.contoso.com","msft.sme.connection-type.server","hyperv"
"myDesktop.contoso.com","msft.sme.connection-type.windows-client","hyperv"
"teamcluster.contoso.com","msft.sme.connection-type.cluster","legacyCluster|WS2016","global"
"myHCIcluster.contoso.com,"msft.sme.connection-type.hyper-converged-cluster","myHCIcluster|hyperv|JIT|WS2019"
"teamclusterNode.contoso.com","msft.sme.connection-type.server","legacyCluster|WS2016","global"
"myHCIclusterNode.contoso.com","msft.sme.connection-type.server","myHCIcluster|hyperv|JIT|WS2019"
```

## Импортировать RDCman подключения

Используйте следующий сценарий для экспорта сохраненного подключения в [RDCman](https://blogs.technet.microsoft.com/rmilne/2014/11/19/remote-desktop-connection-manager-download-rdcman-2-7/) в файл. Затем можно импортировать файл в Windows Admin Center, поддержание иерархии RDCMan группирования с помощью тегов. Попробуйте!

1. Скопируйте и вставьте приведенный ниже код в сеанс PowerShell:

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

3. Импортируйте полученные. CSV-файл в Windows Admin Center и все иерархии группирования RDCMan будут представлены тегов в списке подключение. Дополнительные сведения см. в разделе [С помощью PowerShell для импорта и экспорта подключений (с тегами)](#use-powershell-to-import-or-export-your-connections-with-tags).

## Просмотр сценарии PowerShell, используемый в Windows Admin Center

После подключения для сервера, кластера или компьютера, можно посмотреть сценариев PowerShell питание действий пользовательского интерфейса, доступных в Windows Admin Center. С в средстве, щелкните значок PowerShell на панели приложения. Выберите команду объектов из раскрывающегося списка для перехода к соответствующей сценария PowerShell.

![](../media/launch/showscript.png)