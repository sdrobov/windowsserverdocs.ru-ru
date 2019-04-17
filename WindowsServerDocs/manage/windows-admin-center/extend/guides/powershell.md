---
title: Использование PowerShell в расширении
description: С помощью PowerShell в расширении Windows Admin Center SDK (проект Honolulu)
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 06/18/2018
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: b1be4fe7639d913243cc28371dff9e98e0f5827e
ms.sourcegitcommit: f1edfc6525e09dd116b106293f9260123a94de0c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "9296726"
---
# Использование PowerShell в расширении #

>Относится к: Windows Admin Center, ознакомительная версия Windows Admin Center

Давайте рассмотрим более подробно пакета SDK расширения Windows Admin Center — поговорим о добавлении команд PowerShell в расширении.

## PowerShell в TypeScript ##

В процессе сборки воспринять имеет шаг создать, которые будут принимать все ```{!ScriptName}.ps1``` , помещается в ```\src\resources\scripts``` папки и соберите их в ```powershell-scripts``` класс в разделе ```\src\generated``` папки.

>[!NOTE] 
> Не вручную обновить ```powershell-scripts.ts``` ни ```strings.ts``` файлов. Любые изменения, вносимые будут перезаписаны на следующий создать.

## Запуск сценария Powerhell ##
Все сценарии, которые необходимо выполнить на узле можно разместить в ```\src\resources\scripts\{!ScriptName}.ps1```. 
>[!IMPORTANT] 
> Внести любые изменения в ```{!ScriptName}.ps1``` файла не будут отражены в своем проекте, если создать 

API работает путем создания сеанса PowerShell на узлах предназначенных для, создание сценария PowerShell с помощью любые параметры, которые необходимо передать в и затем запуска сценария в сеансов, которые были созданы.

Например, у нас есть этот сценарий ```\src\resources\scripts\Get-NodeName.ps1```:
``` ps1
Param
 (
    [String] $stringFormat
 )
 $nodeName = [string]::Format($stringFormat,$env:COMPUTERNAME)
 Write-Output $nodeName
```

Мы создадим сеанса PowerShell для наших целевому узлу:
``` ts
const session = this.appContextService.powerShell.createSession('{!TargetNode}'); 
```
Затем мы создадим сценария PowerShell с входным параметром:
```ts
const script = PowerShell.createScript(PowerShellScripts.Get_NodeName, {stringFormat: 'The name of the node is {0}!'});
```
И наконец нам нужно запустить этот сценарий в сеанс, который мы создали:
``` ts
  public ngOnInit(): void {
    this.session = this.appContextService.powerShell.createAutomaticSession('{!TargetNode}');
  }

  public getNodeName(): Observable<any> {
    const script = PowerShell.createScript(PowerShellScripts.Get_NodeName.script, { stringFormat: 'The name of the node is {0}!'});
    return this.appContextService.powerShell.run(this.session, script)
    .pipe(
        map(
        response => {
            if (response && response.results) {
                return response.results;
            }
            return 'no response';
        }
      ) 
    );
  }

  public ngOnDestroy(): void {
    this.session.dispose()
  }

```
Теперь нам необходимо подписаться на отслеживаемую функцию, которую мы только что создали. Разместите которых необходимо вызвать функцию, чтобы запустить сценарий PowerShell:
```ts
this.getNodeName().subscribe(
     response => {
    console.log(response)
     }
);
```
Предоставляя имя узла в метод createSession, новый сеанс PowerShell создается, используется и затем немедленно удаляются после завершения вызова PowerShell. 

### Параметры ключа ###
Некоторые параметры доступны при вызове PowerShell API. Каждый раз, когда сеанс создан его можно создать с помощью или без ключа. 

**Ключ:** В результате создается ключом сеанс, который может быть поиск и используется повторно, даже на разных компонентов (это означает, что Component1 можно создать сеанс с помощью ключа «Малых и средних Предприятий-ROCKS», и Component2 можно использовать этот же сеанса). Если ключ, сеанс, который создается должны быть уничтожены путем вызова метод dispose() как было сделано в предыдущем примере. Сеанс не должны храниться без удаления более 5 минут. 
```ts
  const session = this.appContextService.powerShell.createSession('{!TargetNode}', '{!Key}');
```

**Ключа:** Ключ будет автоматически создан для сеанса. Удалить этот сеанс с помощью автоматически через 3 минуты. С помощью ключа позволяет расширения повторное использование любого недопустимое, уже доступен во время создания сеанса. Если не недопустимое нет, чем он будет создан. Эта функция удобно применять для однократных вызовы, но повторного использования может повлиять на производительность. Сеанс занимает около 1 секунды до создания, поэтому постоянно повторное использование сеансов может привести к снижения.

```ts
  const session = this.appContextService.powerShell.createSession('{!TargetNodeName}');
```
или 
``` ts 
const session = this.appContextService.powerShell.createAutomaticSession('{!TargetNodeName}');
```
В большинстве случаев Создание сеанса с ключом в ```ngOnInit()``` метод и затем удаляет его в ```ngOnDestroy()```. Прогрессивной развертки при наличии нескольких сценариев PowerShell в компоненте, но основной сеанс, который является не передаются на другие компоненты.
Для получения наилучших результатов убедитесь, что Создание сеанса осуществляется внутри компонентов, а не службы — это позволяет избежать этой жизненным циклом и очистки можно управлять надлежащим образом.

Для получения наилучших результатов убедитесь, что Создание сеанса осуществляется внутри компонентов, а не службы — это позволяет избежать этой жизненным циклом и очистки можно управлять надлежащим образом.

### Поток PowerShell ###
При наличии длительные сценарий и данных является выхода постепенно, поток PowerShell позволяет обработки данных без необходимости долгие скрипта для завершения. Отслеживаемые next() будет вызываться сразу же после получения данных.
```ts
this.appContextService.powerShellStream.run(session, script);
```

### Длинные запуск сценариев ###
Если у вас есть длительные сценарий, который вы хотите запустить в фоновом режиме, могут отправляться рабочего элемента. Состояние выполнения сценария отслеживается шлюз и обновления состояния можно отправить уведомление. 
```ts
const workItem: WorkItemSubmitRequest = {
    typeId: 'Long Running Script',
    objectName: 'My long running service',
    powerShellScript: script,
    
    //in progress notifications
    inProgressTitle: 'Executing long running request',
    startedMessage: 'The long running request has been started',
    progressMessage: 'Working on long running script – {{ percent }} %',

    //success notification
    successTitle: 'Successfully executed a long running script!',
    successMessage: '{{objectName}} was successful',
    successLinkText: 'Bing',
    successLink: 'http://www.bing.com',
    successLinkType: NotificationLinkType.Absolute,

    //error notification
    errorTitle: 'Failed to execute long running script',
    errorMessage: 'Error: {{ message }}'

    nodeRequestOptions: {
       logAudit: true,
       logTelemetry: true
    }
};

return this.appContextService.workItem.submit('{!TargetNode}', workItem);
```

>[!NOTE] 
> Для выполнения, отображаемых текущей записи должны быть включены в сценарий, который вы написали. Пример.
> ``` ps1
>  Write-Progress -Activity ‘The script is almost done!’ -percentComplete 95
>```

#### Параметры рабочего элемента ####

| function | Объяснение |
| ----- | ----------- |
| Submit() | Отправляет рабочий элемент 
| submitAndWait() | Отправка рабочего элемента и дождитесь завершения выполнения
| wait() | Подождите, пока существующие рабочие элемент для выполнения
| Query() | Запрос для существующего рабочего элемента по идентификатору
| Find() | Найдите и существующие рабочий элемент TargetNodeName, ИмяМодуля или идентификатор типа.

### Пакетный PowerShell API -интерфейсы ###
Если вам необходимо выполнить тот же сценарий на нескольких узлах, можно использовать сеанса PowerShell пакета. Пример.
```ts
const batchSession = this.appContextService.powerShell.createBatchSession(
    ['{!TargetNode1}', '{!TargetNode2}', sessionKey);
  this.appContextService.powerShell.runBatchSingleCommand(batchSession, command).subscribe((responses: PowerShellBatchResponseItem[]) => {
    for (const response of responses) { 
      if (response.error || response.errors) {
        //handle error
      } else {
        const results = response.properties && response.properties.results;
        //response.nodeName
        //results[0]
      }
    }
     },
     Error => { /* handle error */ });  

```


#### Параметры PowerShellBatch ####
| параметр | Объяснение |
| ----- | ----------- |
| runSingleCommand | Запуск одной команды от всех узлов в массив 
| Запуск | Соответствующие команды на парах узла
| Отмена | Отмена команды на всех узлах в массиве