---
ms.assetid: 01988844-df02-4952-8535-c87aefd8a38a
title: "Развертывание автоматической классификации данных (Поэтапная Демонстрация)"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 1c5c0fa221e0d7375216426f838ba37bee852984
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="deploy-automatic-file-classification-demonstration-steps"></a>Развертывание автоматической классификации данных (Поэтапная Демонстрация)

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

This topic explains how to enable resource properties in Active Directory, create classification rules on the file server, and then assign values to the resource properties for files on the file server. For this example, the following classification rules are created:  
  
-   A content classification rule that searches a set of files for the string 'Contoso Confidential.' Если строка найдена в файле, для свойства ресурса "влияние" установлен высокий на файл.  
  
-   Правило классификации содержимого, которое ищет в наборе файлов регулярное выражение, соответствующее номеру социального страхования по крайней мере 10 раз в одном файле. Если шаблон найден, файл классифицируется как содержащий личные сведения, а для свойства ресурса "личные сведения" установлен высокий.  
  
**В этом документе**  
  
-   [Step 1: Create resource property definitions](assetId:///4a96cdaf-0081-4824-aab8-f0d51be501ac#BKMK_Step1)  
  
-   [Шаг 2: Создание правила классификации строкового содержимого](assetId:///4a96cdaf-0081-4824-aab8-f0d51be501ac#BKMK_Step2)  
  
-   [Шаг 3: Создание правила классификации содержимого регулярного выражения](assetId:///4a96cdaf-0081-4824-aab8-f0d51be501ac#BKMK_Step3)  
  
-   [Шаг 4: Проверка классификации файлов](Deploy-Automatic-File-Classification--Demonstration-Steps-.md#BKMK_Step4)  
  
> [!NOTE]  
> Этот раздел содержит пример командлеты Windows PowerShell, который можно использовать для автоматизации некоторых описанных процедур. Дополнительные сведения см. в разделе [использование командлетов](https://go.microsoft.com/fwlink/p/?linkid=230693).  
  
## <a name="BKMK_Step1"></a>Step 1: Create resource property definitions  
Свойства ресурса влияние и личные сведения включены, чтобы инфраструктура классификации файлов может их использовать для маркировки файлов, которые проверяются в общей сетевой папке.  
  
[Do this step using Windows PowerShell](assetId:///4a96cdaf-0081-4824-aab8-f0d51be501ac#BKMK_PSstep1)  
  
#### <a name="to-create-resource-property-definitions"></a>To create resource property definitions  
  
1.  On the domain controller, sign in to the server as a member of the Domain Admins security group.  
  
2.  Open Active Directory Administrative Center. В диспетчере серверов щелкните **средства**, а затем нажмите кнопку **Центр администрирования Active Directory**.  
  
3.  Expand **Dynamic Access Control**, and then click **Resource Properties**.  
  
4.  Right-click **Impact**, and then click **Enable**.  
  
5.  Right-click **Personally Identifiable Information**, and then click **Enable**.  
  
![руководства по решениям](media/Deploy-Automatic-File-Classification--Demonstration-Steps-/PowerShellLogoSmall.gif)Windows PowerShell эквивалентные команды ***  
  
Следующий командлет Windows PowerShell или командлеты выполняют ту же функцию, что и предыдущая процедура. Введите каждый командлет в отдельной строке, несмотря на то, что они могут отображаться по здесь несколько строк словам из-за ограничений форматирования.  
  
```  
Set-ADResourceProperty '"Enabled:$true '"Identity:'CN=Impact_MS,CN=Resource Properties,CN=Claims Configuration,CN=Services,CN=Configuration,DC=contoso,DC=com'   
Set-ADResourceProperty '"Enabled:$true '"Identity:'CN=PII_MS,CN=Resource Properties,CN=Claims Configuration,CN=Services,CN=Configuration,DC=contoso,DC=com'  
```  
  
## <a name="BKMK_Step2"></a>Шаг 2: Создание правила классификации строкового содержимого  
Правила классификации строкового содержимого ищет в файле определенную строку. Если строка найдена, значение свойства ресурса можно настроить. В этом примере мы каждый файл в общей сетевой папке и найдите строку «Contoso Confidential.» Если строка найдена, связанный файл классифицируется как особо важный для бизнеса.  
  
[Do this step using Windows PowerShell](assetId:///4a96cdaf-0081-4824-aab8-f0d51be501ac#BKMK_PSstep2)  
  
#### <a name="to-create-a-string-content-classification-rule"></a>Создание правила классификации строкового содержимого  
  
1.  Войдите на файловый сервер является членом группы безопасности администраторов.  
  
2.  В командной строке Windows PowerShell введите **Update-FsrmClassificationPropertyDefinition** и нажмите клавишу ВВОД. Эта команда синхронизирует определения свойств, созданные на контроллере домена, на файловом сервере.  
  
3.  Откройте диспетчер ресурсов файлового сервера. In Server Manager, click **Tools**, and then click **File Server Resource Manager**.  
  
4.  Разверните **управление классификацией**, щелкните правой кнопкой мыши **правила классификации**, а затем нажмите кнопку **настроить расписание классификации**.  
  
5.  Выберите **включить фиксированное расписание** флажок выберите **разрешить постоянную классификацию для новых файлов** флажок, выберите день недели для выполнения классификации и нажмите кнопку **ОК**.  
  
6.  Щелкните правой кнопкой мыши **правила классификации**, а затем нажмите кнопку **создать правило классификации**.  
  
7.  На **Общие** вкладке **имя правила** введите имя правила, например **Contoso Confidential**.  
  
8.  On the **Scope** tab, click **Add**, and choose the folders that should be included in this rule, such as D:\Finance Documents.  
  
    > [!NOTE]  
    > Также можно выбрать динамическое пространство имен для области. Дополнительные сведения о динамических пространствах имен для правил классификации см. в разделе [какие новые возможности диспетчера ресурсов файлового сервера Windows Server 2012 \[redirected\]](assetId:///d53c603e-6217-4b98-8508-e8e492d16083).  
  
9. На **классификации** выполните следующее:  
  
    -   В **выберите метод назначения свойства файлам** убедитесь, что **классификатор содержимого** выбран.  
  
    -   В **выбрать свойство, которое будет назначено файлам** выберите **влияние**.  
  
    -   В **указать значение** выберите **высокой**.  
  
10. В разделе **параметры** щелкните **Настройка**.  
  
11. В **тип выражения** столбец, выберите **строка**.  
  
12. В **выражение** введите **Contoso Confidential**, а затем нажмите кнопку **ОК**.  
  
13. На **тип оценки** выберите **заново определить существующие значения свойств** флажок, нажмите кнопку **заменить существующее значение**, а затем нажмите кнопку **ОК**.  
  
![руководства по решениям](media/Deploy-Automatic-File-Classification--Demonstration-Steps-/PowerShellLogoSmall.gif)Windows PowerShell эквивалентные команды ***  
  
Следующий командлет Windows PowerShell или командлеты выполняют ту же функцию, что и предыдущая процедура. Введите каждый командлет в отдельной строке, несмотря на то, что они могут отображаться по здесь несколько строк словам из-за ограничений форматирования.  
  
```  
$date = Get-Date  
$AutomaticClassificationScheduledTask = New-FsrmScheduledTask -Time $date -Weekly @(3, 2, 4, 5,1,6,0) -RunDuration 0;$AutomaticClassificationScheduledTask  
Set-FsrmClassification -Continuous -schedule $AutomaticClassificationScheduledTask  
New-FSRMClassificationRule -Name 'Contoso Confidential' -Property "Impact_MS" -PropertyValue "3000" -Namespace @('D:\Finance Documents') -ClassificationMechanism "Content Classifier" -Parameters @("StringEx=Min=1;Expr=Contoso Confidential") -ReevaluateProperty Overwrite  
```  
  
## <a name="BKMK_Step3"></a>Шаг 3: Создание правила классификации содержимого регулярного выражения  
Правило классификации регулярного выражения проверяет файл на наличие шаблона, соответствующего регулярному выражению. Если найдена строка, соответствующая регулярному выражению, значение свойства ресурса можно настроить. В этом примере мы каждый файл в общей сетевой папке и найдите строку, соответствующую шаблону номер социального страхования (XXX-XX-XXXX). Если шаблон найден, связанный файл классифицируется как содержащий личные сведения.  
  
[Do this step using Windows PowerShell](assetId:///4a96cdaf-0081-4824-aab8-f0d51be501ac#BKMK_PSstep3)  
  
#### <a name="to-create-a-regular-expression-content-classification-rule"></a>Создание правила классификации содержимого регулярного выражения  
  
1.  Sign in to the file server as a member of the Administrators security group.  
  
2.  From the Windows PowerShell command prompt, type **Update-FsrmClassificationPropertyDefinition**, and then press ENTER. This will synchronize the property definitions that are created on the domain controller to the file server.  
  
3.  Откройте диспетчер ресурсов файлового сервера. In Server Manager, click **Tools**, and then click **File Server Resource Manager**.  
  
4.  Щелкните правой кнопкой мыши **правила классификации**, а затем нажмите кнопку **создать правило классификации**.  
  
5.  На **Общие** вкладке **имя правила** введите имя для правила классификации, например "правило PII".  
  
6.  На **область** щелкните **добавить**, а затем выберите папки, которые следует включить в это правило, например D:\Finance Documents.  
  
7.  На **классификации** выполните следующее:  
  
    -   В **выберите метод назначения свойства файлам** убедитесь, что **классификатор содержимого** выбран.  
  
    -   В **выбрать свойство, которое будет назначено файлам** выберите **личные сведения**.  
  
    -   В **указать значение** выберите **высокой**.  
  
8.  В разделе **параметры** щелкните **Настройка**.  
  
9. В **тип выражения** столбец, выберите **регулярное выражение**.  
  
10. В **выражение** введите **^ (?! 000)([0-7]\d{2}|7([0-7]\d|7[012])) ([-]?) (?! 00) \d\d\3 (?! 0000) \d {4} $**  
  
11. В **минимальное число повторений** введите **10**, а затем нажмите кнопку **ОК**.  
  
12. На **тип оценки** выберите **заново определить существующие значения свойств** флажок, нажмите кнопку **заменить существующее значение**, а затем нажмите кнопку **ОК**.  
  
![руководства по решениям](media/Deploy-Automatic-File-Classification--Demonstration-Steps-/PowerShellLogoSmall.gif)Windows PowerShell эквивалентные команды ***  
  
Следующий командлет Windows PowerShell или командлеты выполняют ту же функцию, что и предыдущая процедура. Введите каждый командлет в отдельной строке, несмотря на то, что они могут отображаться по здесь несколько строк словам из-за ограничений форматирования.  
  
```  
New-FSRMClassificationRule -Name "PII Rule" -Property "PII_MS" -PropertyValue "5000" -Namespace @('D:\Finance Documents') -ClassificationMechanism "Content Classifier" -Parameters @("RegularExpressionEx=Min=10;Expr=^(?!000)([0-7]\d{2}|7([0-7]\d|7[012]))([ -]?)(?!00)\d\d\3(?!0000)\d{4}$") -ReevaluateProperty Overwrite  
```  
  
## <a name="BKMK_Step4"></a>Шаг 4: Убедитесь, что файлы классифицируются правильно  
Вы можете убедиться, что файлы классифицируются правильно, просмотрев свойства файла, который был создан в папке, указанной в правилах классификации.  
  
#### <a name="to-verify-that-the-files-are-classified-correctly"></a>Чтобы убедиться, что файлы классифицируются правильно  
  
1.  На файловом сервере примените правила классификации с помощью диспетчера ресурсов файлового сервера.  
  
    1.  Нажмите кнопку **управление классификацией**, щелкните правой кнопкой мыши **правила классификации**, а затем нажмите кнопку **запустить классификацию с все правила теперь**.  
  
    2.  Нажмите кнопку **дождаться завершения классификации**, а затем щелкните **ОК**.  
  
    3.  Закройте отчет об автоматической классификации.  
  
    4.  Это можно сделать с помощью Windows PowerShell с помощью следующей команды: **Start-FSRMClassification "«RunDuration 0 - подтверждение: $false**  
  
2.  Перейдите к папке, указанной в правилах классификации, например D:\Finance Documents.  
  
3.  Щелкните правой кнопкой мыши файл в этой папке, а затем нажмите кнопку **свойства**.  
  
4.  Нажмите кнопку **классификации** и убедитесь, что файл классифицирован правильно.  
  
## <a name="BKMK_Links"></a>См. также:  
  
-   [Сценарий: Получение четкого представления о данных с помощью классификации](Scenario--Get-Insight-into-Your-Data-by-Using-Classification.md)  
  
-   [Планирование автоматической классификации файлов](assetId:///e3c3bb4b-3034-42b7-b391-8ef5f5851955)  
  
-   [Динамического контроля доступа: Обзор сценария](Dynamic-Access-Control--Scenario-Overview.md)  
  

