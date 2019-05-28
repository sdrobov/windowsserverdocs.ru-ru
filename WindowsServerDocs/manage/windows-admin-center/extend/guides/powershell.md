---
title: Использование PowerShell в расширении
description: С помощью PowerShell в расширении Windows Admin Center SDK (Гонолулу проекта)
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 05/09/2019
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: 7375732fd464519cd1533043d271065e488fd46a
ms.sourcegitcommit: 7cb939320fa2613b7582163a19727d7b77debe4b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65621354"
---
# <a name="using-powershell-in-your-extension"></a>Использование PowerShell в расширении #

>Область применения. Windows Admin Center, предварительная версия Windows Admin Center

Перейдем к более подробное руководство расширения пакета SDK для Windows Admin Center — давайте поговорим о добавлении команды PowerShell в модуле.

## <a name="powershell-in-typescript"></a>PowerShell в TypeScript ##

Процесс сборки gulp имеет создать шаг, который будет использовать любую ```{!ScriptName}.ps1``` , помещается в ```\src\resources\scripts``` папку и создавать их в ```powershell-scripts``` класса в группе ```\src\generated``` папки.

>[!NOTE] 
> Не обновлять вручную ```powershell-scripts.ts``` ни ```strings.ts``` файлов. Любые вносимые изменения будут перезаписаны на Далее формирования.

## <a name="running-a-powershell-script"></a>Запуск сценария PowerShell ##
Все сценарии, которые вы хотите запустить на узле можно разместить в ```\src\resources\scripts\{!ScriptName}.ps1```. 
>[!IMPORTANT] 
> Производить любые изменения в ```{!ScriptName}.ps1``` файла не будут отражены в вашем проекте до ```gulp generate``` будет выполнено.

API работает путем создания сеанса PowerShell на узлах нацеливания, создания сценария PowerShell со всеми параметрами, которые должны быть переданы в и затем выполнения сценария на сеансы, которые были созданы.

Например, у нас есть этот сценарий ```\src\resources\scripts\Get-NodeName.ps1```:
``` ps1
Param
 (
    [String] $stringFormat
 )
 $nodeName = [string]::Format($stringFormat,$env:COMPUTERNAME)
 Write-Output $nodeName
```

Мы создадим сеанс PowerShell для нашей целевой узел:
``` ts
const session = this.appContextService.powerShell.createSession('{!TargetNode}'); 
```
Затем мы создадим сценарий PowerShell с входным параметром.
```ts
const script = PowerShell.createScript(PowerShellScripts.Get_NodeName, {stringFormat: 'The name of the node is {0}!'});
```
Наконец нам нужно запустить этот скрипт в сеансе, который мы создали:
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
Теперь нам нужно подписаться на наблюдаемые функцию, которую мы только что создали. Поместите это, когда необходимо вызвать функцию для выполнения сценария PowerShell:
```ts
this.getNodeName().subscribe(
     response => {
    console.log(response)
     }
);
```
Предоставляя имени узла, чтобы метод createSession, новый сеанс PowerShell создается, использовать и затем немедленно уничтожается после завершения вызова PowerShell. 

### <a name="key-options"></a>Параметры ключа ###
Несколько параметров доступны при вызове PowerShell API. Каждый раз при создании сеанса его могут создаваться с или без ключа. 

**Ключ:** Это создает сеанс с ключом, которую можно искать и повторно, даже через компоненты (то есть Component1 может создать сеанс с ключом «ROCKS для малых и средних Предприятий», а Component2 можно использовать в этом же сеансе). Если ключ сеанса, который создается должен быть удален с вызова dispose() как это было сделано в приведенном выше примере. Сеанс не должны храниться без удаления более 5 минут. 
```ts
  const session = this.appContextService.powerShell.createSession('{!TargetNode}', '{!Key}');
```

**Без ключей:** Ключ создается автоматически для сеанса. Этот сеанс с быть удален автоматически после 3 минуты. Использование ключа позволяет расширения к перезапуску использование любого пространства выполнения, которые уже доступны во время создания сеанса. Если нет пространства выполнения не будет создан новый. Эта функция хорошо подходит для одноразовых вызовов, но многократного использования может повлиять на производительность. Сеанс принимает примерно 1 секунда для создания, поэтому постоянно повторное использование сеансов может привести к снижению скорости.

```ts
  const session = this.appContextService.powerShell.createSession('{!TargetNodeName}');
```
или диспетчер конфигурации служб 
``` ts 
const session = this.appContextService.powerShell.createAutomaticSession('{!TargetNodeName}');
```
В большинстве случаев создания сеанса с ключом в ```ngOnInit()``` метод, а затем уничтожьте ее в ```ngOnDestroy()```. Следуйте этому шаблону, при наличии нескольких сценариев PowerShell в компоненте, но соответствующий сеанс не является общей во всех компонентах.
Для получения наилучших результатов убедитесь, созданием сеанса осуществляется внутри компонентов, а не службы — это помогает обеспечить, время существования и очистки, которые могут управляться должным образом.

Для получения наилучших результатов убедитесь, созданием сеанса осуществляется внутри компонентов, а не службы — это помогает обеспечить, время существования и очистки, которые могут управляться должным образом.

### <a name="powershell-stream"></a>Stream PowerShell ###
Если у вас есть долго выполняющиеся скриптов и данных выводится постепенно, поток PowerShell позволит обрабатывать данные без ожидания для завершения скрипта. Наблюдаемый next() вызывается сразу после получения данных.
```ts
this.appContextService.powerShellStream.run(session, script);
```

### <a name="long-running-scripts"></a>Время выполнения скриптов ###
Если у вас есть долго выполняющиеся скрипт, который вы хотите запустить в фоновом режиме, можно отправить рабочий элемент. Состояние сценария будут отслеживаться с помощью шлюза и получать сводку о могут отправляться уведомления. 
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
> Для отслеживания хода выполнения будет отображаться Write-Progress должны быть включены в скрипт, который вы написали. Пример:
> ``` ps1
>  Write-Progress -Activity ‘The script is almost done!’ -percentComplete 95
>```

#### <a name="workitem-options"></a>Параметры рабочего элемента ####

| function | Объяснение |
| ----- | ----------- |
| submit() | Отправляет рабочий элемент 
| submitAndWait() | Отправить рабочий элемент и дождитесь завершения его выполнения
| wait() | Дождитесь существующего рабочего элемента для завершения
| Query() | Запрос для существующего рабочего элемента по идентификатору
| Find() | Найдите и существующий рабочий элемент TargetNodeName, имя модуля или typeId.

### <a name="powershell-batch-apis"></a>API-интерфейсы PowerShell пакетной службы ###
Если вам нужно выполнить тот же скрипт на нескольких узлах, можно использовать сеанс PowerShell пакетной службы. Пример:
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


#### <a name="powershellbatch-options"></a>Параметры PowerShellBatch ####
| варианты | Объяснение |
| ----- | ----------- |
| runSingleCommand | Выполнить одну команду на всех узлах в массиве 
| запустить | Выполните соответствующую команду на узле парных
| Отмена | Отменить команду на всех узлах в массиве
