---
title: Использование PowerShell в расширении
description: Использование PowerShell в расширении Windows Admin Center SDK (Project Хонолулу)
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 05/09/2019
ms.localizationpriority: medium
ms.prod: windows-server
ms.openlocfilehash: 6e99fc43d4acb7a70dfd3a8ba19dae6492c41b2b
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71357053"
---
# <a name="using-powershell-in-your-extension"></a>Использование PowerShell в расширении #

>Область применения. Windows Admin Center, ознакомительная версия Windows Admin Center

Давайте более подробно рассмотрим пакет SDK для расширений центра администрирования Windows. Давайте поговорим о добавлении команд PowerShell в расширение.

## <a name="powershell-in-typescript"></a>PowerShell в TypeScript ##

Процесс сборки gulp содержит шаг создания ```{!ScriptName}.ps1``` , который принимает все, что размещается ```\src\resources\scripts``` в папке, ```powershell-scripts``` и создает их ```\src\generated``` в классе в папке.

>[!NOTE] 
> Не следует вручную обновлять ```powershell-scripts.ts``` ```strings.ts``` файлы и. Любые внесенные изменения будут перезаписаны при следующем формировании.

## <a name="running-a-powershell-script"></a>Выполнение скрипта PowerShell ##
Любые скрипты, которые необходимо выполнить на узле, можно разместить в ```\src\resources\scripts\{!ScriptName}.ps1```. 
>[!IMPORTANT] 
> Любые изменения, внесенные ```{!ScriptName}.ps1``` в файл, не будут отражены в проекте ```gulp generate``` до запуска.

Для работы с API сначала создается сеанс PowerShell на целевых узлах, создается сценарий PowerShell с параметрами, которые необходимо передать, а затем выполняется сценарий в созданных сеансах.

Например, у нас есть следующий сценарий ```\src\resources\scripts\Get-NodeName.ps1```:
``` ps1
Param
 (
    [String] $stringFormat
 )
 $nodeName = [string]::Format($stringFormat,$env:COMPUTERNAME)
 Write-Output $nodeName
```

Мы создадим сеанс PowerShell для нашего целевого узла:
``` ts
const session = this.appContextService.powerShell.createSession('{!TargetNode}'); 
```
Затем мы создадим сценарий PowerShell с входным параметром:
```ts
const script = PowerShell.createScript(PowerShellScripts.Get_NodeName, {stringFormat: 'The name of the node is {0}!'});
```
Наконец, необходимо выполнить этот скрипт в созданном сеансе:
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
Теперь нужно подписываться на только что созданную функцию. Поместите здесь, где нужно вызвать функцию, чтобы запустить сценарий PowerShell:
```ts
this.getNodeName().subscribe(
     response => {
    console.log(response)
     }
);
```
Предоставляя имя узла методу createSession, создается и используется новый сеанс PowerShell, который сразу же уничтожается после завершения вызова PowerShell. 

### <a name="key-options"></a>Ключевые параметры ###
При вызове API PowerShell доступны несколько параметров. Каждый раз при создании сеанса его можно создать с ключом или без него. 

**Раздел:** При этом создается сеанс с ключом, который может быть просмотрен и использован повторно, даже для разных компонентов (это означает, что Component1 может создать сеанс с ключом "эксперт-ROCKS", а Component2 может использовать тот же сеанс). Если указан ключ, создаваемый сеанс должен быть удален путем вызова Dispose (), как было сделано в примере выше. Сеанс не следует хранить без удаления в течение более чем 5 минут. 
```ts
  const session = this.appContextService.powerShell.createSession('{!TargetNode}', '{!Key}');
```

**Ассоциаци** Для сеанса будет автоматически создан ключ. Этот сеанс будет удален автоматически через 3 минуты. Использование ключа без ключей позволяет вашему расширению повторно использовать любое пространство выполнения, которое уже доступно во время создания сеанса. Если пространство выполнения не доступно, то будет создано новое. Эта функция хорошо подходит для одноразовых вызовов, но многократное использование может повлиять на производительность. Создание сеанса занимает около 1 секунды, поэтому сеансы непрерывного повторного запуска могут привести к замедлению.

```ts
  const session = this.appContextService.powerShell.createSession('{!TargetNodeName}');
```
или 
``` ts 
const session = this.appContextService.powerShell.createAutomaticSession('{!TargetNodeName}');
```
В большинстве случаев создайте сеанс с ключом в ```ngOnInit()``` методе, а затем удалите его в. ```ngOnDestroy()``` Используйте этот шаблон, если в компоненте имеется несколько скриптов PowerShell, но базовый сеанс не используется совместно разными компонентами.
Для достижения лучших результатов убедитесь, что создание сеанса осуществляется внутри компонентов, а не служб — это гарантирует, что время существования и очистки можно будет правильно управлять.

Для достижения лучших результатов убедитесь, что создание сеанса осуществляется внутри компонентов, а не служб — это гарантирует, что время существования и очистки можно будет правильно управлять.

### <a name="powershell-stream"></a>Поток PowerShell ###
Если используется длительный сценарий и данные выводятся последовательно, поток PowerShell позволит обработать данные, не дожидаясь завершения скрипта. Наблюдаемый далее () будет вызываться сразу после получения данных.
```ts
this.appContextService.powerShellStream.run(session, script);
```

### <a name="long-running-scripts"></a>Долго выполняющиеся скрипты ###
При наличии долго выполняющегося скрипта, который вы хотите запустить в фоновом режиме, можно отправить рабочий элемент. Состояние сценария будет контролироваться шлюзом, а обновления состояния могут быть отправлены в уведомление. 
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
> Чтобы показать ход выполнения, в написанный скрипт необходимо добавить запись о ходе выполнения. Пример:
> ``` ps1
>  Write-Progress -Activity ‘The script is almost done!' -percentComplete 95
>```

#### <a name="workitem-options"></a>Параметры рабочего элемента ####

| function | Объяснение |
| ----- | ----------- |
| Submit () | Отправляет рабочий элемент 
| Субмитандваит () | Отправка рабочего элемента и ожидание завершения его выполнения
| Wait () | Ожидание завершения существующего рабочего элемента
| Query () | Запрос существующего рабочего элемента по идентификатору
| Find () | Поиск и существующий рабочий элемент по Таржетноденаме, ModuleName или typeId.

### <a name="powershell-batch-apis"></a>API-интерфейсы пакетной службы PowerShell ###
Если необходимо выполнить один и тот же скрипт на нескольких узлах, можно использовать сеанс PowerShell для пакетной службы. Пример:
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


#### <a name="powershellbatch-options"></a>Параметры Повершеллбатч ####
| варианты | Объяснение |
| ----- | ----------- |
| рунсинглекомманд | Выполнение одной команды для всех узлов в массиве 
| запуска | Выполнение соответствующей команды на связанном узле
| cancel | Отмените команду на всех узлах в массиве.
