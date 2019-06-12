---
ms.assetid: 846c3680-b321-47da-8302-18472be42421
title: Развертывание утверждений между лесами (обучающий пример)
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: a6f2e5d3a227384b20735ab99ee1ab5ea77bd913
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66445841"
---
# <a name="deploy-claims-across-forests-demonstration-steps"></a>Развертывание утверждений между лесами (обучающий пример)

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

В этом разделе мы обсудим базового сценария, в которой описывается настройка преобразования утверждений между доверяющими и доверенными лесами. Вы узнаете, как объекты политики преобразования утверждений можно создавать и связанного с доверие в доверяющем лесу и доверенном лесу. Затем будет проверить сценарий.  

## <a name="scenario-overview"></a>Обзор сценария  
Adatum Corporation предоставляет финансовых услуг компании Contoso, Ltd. Каждый квартал бухгалтеров Adatum скопируйте свои электронные таблицы учетной записи в папку на файловом сервере, расположенный в компании Contoso, Ltd. Есть двустороннее отношение доверия настраиваются из Contoso Adatum. Contoso, Ltd. желает Защита общей папки, чтобы только Adatum сотрудники получают доступ к удаленной общей папки.  

Содержание сценария  

1.  [Настройка необходимых компонентов и тестовой среды](Deploy-Claims-Across-Forests--Demonstration-Steps-.md#BKMK_1.1)  

2.  [Настроить преобразование заявок в доверенном лесу (Adatum)](Deploy-Claims-Across-Forests--Demonstration-Steps-.md#BKMK_3)  

3.  [Настроить преобразование заявок в доверяющем лесу (Contoso)](Deploy-Claims-Across-Forests--Demonstration-Steps-.md#BKMK_4)  

4.  [Проверить сценарий](Deploy-Claims-Across-Forests--Demonstration-Steps-.md#BKMK_5)  

## <a name="BKMK_1.1"></a>Настройка необходимых компонентов и тестовой среды  
Конфигурация теста необходимо настроить два леса: Корпорации adatum и Contoso, Ltd и необходимости двустороннее доверие между Contoso и Adatum. доверенный лес является «adatum.com» и «contoso.com» является доверяющему лесу.  

В сценарии преобразования утверждений демонстрируется преобразование утверждения в доверенном лесу утверждений в доверяющем лесу. Чтобы сделать это, необходимо настроить новый лес с именем adatum.com и заполнить леса с тестового пользователя со значением «Adatum» компании. Затем вам нужно установить двустороннее доверие между contoso.com и adatum.com.  

> [!IMPORTANT]  
> При настройке леса Contoso и Adatum, необходимо убедиться, что корневые домены находятся в Windows Server 2012 режим работы домена для преобразования утверждений для работы.  

Необходимо настроить следующие действия для лаборатории. Эти процедуры подробно описаны в в [приложении б: Настройка тестовой среды](Appendix-B--Setting-Up-the-Test-Environment.md)  

Необходимо реализовать следующие процедуры, чтобы настроить лабораторию для этого сценария:  

1.  [Настройка Adatum как доверенные леса для Contoso](Appendix-B--Setting-Up-the-Test-Environment.md)  

2.  [Создание типа утверждения «Компания» на Contoso](Appendix-B--Setting-Up-the-Test-Environment.md#BKMK_2.8)  

3.  [Включение свойства ресурса «Компания» для Contoso](Appendix-B--Setting-Up-the-Test-Environment.md#BKMK_2.55)  

4.  [Создание правила централизованного доступа](Appendix-B--Setting-Up-the-Test-Environment.md#BKMK_2.9)  

5.  [Создание централизованной политики доступа](Appendix-B--Setting-Up-the-Test-Environment.md#BKMK_2.10)  

6.  [Публикация новой политики с помощью групповой политики](Appendix-B--Setting-Up-the-Test-Environment.md#BKMK_2.11)  

7.  [Создание папки Earnings на файловом сервере](Appendix-B--Setting-Up-the-Test-Environment.md#BKMK_2.12)  

8.  [Настройка классификации и применение централизованной политики доступа на новую папку](Appendix-B--Setting-Up-the-Test-Environment.md#BKMK_2.13)  

Используйте следующие сведения для выполнения этого сценария:  

|Объекты|Подробности|  
|-----------|-----------|  
|Пользователи|Jeff Low, Contoso|  
|Утверждения пользователей по Contoso и Adatum|Идентификатор: ad: / / ext/компании: ContosoAdatum,<br /><br />Исходный атрибут: компании<br /><br />Предлагаемые значения: Contoso и Adatum **важно:** Необходимо задать идентификатор на «Компания» тип утверждения, как Contoso и Adatum должны совпадать для преобразования утверждений для работы.|  
|Централизованное правило доступа в Contoso|AdatumEmployeeAccessRule|  
|Централизованная политика доступа на Contoso|Только политика доступа adatum|  
|Политики преобразования утверждений в Contoso и Adatum|DenyAllExcept Company|  
|Папка файлов на Contoso|D:\EARNINGS|  

## <a name="BKMK_3"></a>Настроить преобразование заявок в доверенном лесу (Adatum)  
На этом шаге вы Создание политик преобразования в Adatum, чтобы запретить все утверждения, за исключением «Компания» для передачи в Contoso.  

Модуль Active Directory для Windows PowerShell предоставляет **DenyAllExcept** аргументом, который удаляет все значения, кроме заданные утверждения в политике преобразования.  

Чтобы настроить преобразование заявок, необходимо создать политику преобразования утверждений и связать его между доверенных и доверяющих лесах.  

### <a name="BKMK_2.2"></a>Создание политики преобразования утверждений в Adatum  

##### <a name="to-create-a-transformation-policy-adatum-to-deny-all-claims-except-company"></a>Чтобы создать политику преобразования Adatum, чтобы запретить все утверждения, за исключением «Компания»  

1. Войдите на контроллер домена adatum.com как администратор с паролем <strong>pass@word1</strong>.  

2. Откройте командную строку с повышенными правами в Windows PowerShell и введите следующую команду:  

   ```  
   New-ADClaimTransformPolicy `  
   -Description:"Claims transformation policy to deny all claims except Company"`  
   -Name:"DenyAllClaimsExceptCompanyPolicy" `  
   -DenyAllExcept:company `  
   -Server:"adatum.com" `  

   ```  

### <a name="BKMK_2.3"></a>Установка связи преобразования утверждений в Adatum доверия домена объекта  
На этом шаге применения политики преобразования утверждений только что созданный объекта домена в Adatum доверия для Contoso.  

##### <a name="to-apply-the-claims-transformation-policy"></a>Для применения политики преобразования утверждений  

1. Войдите на контроллер домена adatum.com как администратор с паролем <strong>pass@word1</strong>.  

2. Откройте командную строку с повышенными правами в Windows PowerShell и введите следующую команду:  

   ```  

     Set-ADClaimTransformLink `  
   -Identity:"contoso.com" `  
   -Policy:"DenyAllClaimsExceptCompanyPolicy" `  
   '"TrustRole:Trusted `  

   ```  

## <a name="BKMK_4"></a>Настроить преобразование заявок в доверяющем лесу (Contoso)  
На этом шаге вы создадите политики преобразования утверждений в компании Contoso (доверяющим лесом), чтобы запретить все утверждения, за исключением «Компания». Необходимо создать политику преобразования утверждений и свяжите его с доверие леса.  

### <a name="BKMK_4.1"></a>Создание политики преобразования утверждений в Contoso  

##### <a name="to-create-a-transformation-policy-adatum-to-deny-all-except-company"></a>Чтобы создать политику преобразования Adatum, чтобы запретить все, кроме «Компания»  

1. Войдите в контроллер домена, домен contoso.com как администратор с паролем <strong>pass@word1</strong>.  

2. Откройте командную строку с повышенными правами в Windows PowerShell и введите следующую команду:  

   ```  
   New-ADClaimTransformPolicy `  
   -Description:"Claims transformation policy to deny all claims except company" `  
   -Name:"DenyAllClaimsExceptCompanyPolicy" `  
   -DenyAllExcept:company `  
   -Server:"contoso.com" `  

   ```  

### <a name="BKMK_4.2"></a>Установка связи преобразования утверждений в объект домене доверия Contoso  
На этом шаге можно применить только что созданный политики преобразования утверждений в домене contoso.com доверия для Adatum разрешить «Company» нужно передать в contoso.com. Объект доверия домена называется adatum.com.  

##### <a name="to-set-the-claims-transformation-policy"></a>Чтобы задать утверждения политики преобразования  

1. Войдите в контроллер домена, домен contoso.com как администратор с паролем <strong>pass@word1</strong>.  

2. Откройте командную строку с повышенными правами в Windows PowerShell и введите следующую команду:  

   ```  

     Set-ADClaimTransformLink   
   -Identity:"adatum.com" `  
   -Policy:"DenyAllClaimsExceptCompanyPolicy" `  
   -TrustRole:Trusting `  

   ```  

## <a name="BKMK_5"></a>Проверить сценарий  
На этом шаге пользователь пытается получить доступ к папке D:\EARNINGS, которая была создана на файловом сервере FILE1 для проверки того, что пользователь имеет доступ к общей папке.  

#### <a name="to-ensure-that-the-adatum-user-can-access-the-shared-folder"></a>Чтобы убедиться, что пользователь Adatum можно получить доступ к общей папке  

1. Войдите в клиент компьютер CLIENT1 с учетной записью Jeff Low с паролем <strong>pass@word1</strong>.  

2. Перейдите к папке \\\FILE1.contoso.com\Earnings.  

3. Jeff Low должен иметь возможность доступа к папке.  

## <a name="additional-scenarios-for-claims-transformation-policies"></a>Дополнительные сценарии для политик преобразования утверждений  
Ниже приведен список дополнительных распространенные сценарии, в преобразование заявок.  


|                                                 Сценарий                                                 |                                                                                                                                                                                                                                           Политика                                                                                                                                                                                                                                            |
|----------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                  Разрешить все утверждения, полученные из Adatum распространилось на Contoso Adatum                  |                                                          Кода. <br />Новый ADClaimTransformPolicy \`<br /> -Description: «Утверждений политики преобразования, чтобы разрешить все утверждения» \`<br />-Name: «AllowAllClaimsPolicy» \`<br />-AllowAll \`<br />-Server:"contoso.com» \`<br />SET-ADClaimTransformLink \`<br />-Identity:"adatum.com" \`<br />-Policy:"AllowAllClaimsPolicy" \`<br />-TrustRole: доверие \`<br />-Server:"contoso.com» \`                                                          |
|                  Запретить все утверждения, полученные из Adatum распространилось на Contoso Adatum                   |                                                            Кода. <br />Новый ADClaimTransformPolicy \`<br />-Description: «Утверждений политики преобразования, чтобы запретить все утверждения» \`<br />-Name: «DenyAllClaimsPolicy» \`<br /> -"Denyall" \`<br />-Server:"contoso.com» \`<br />SET-ADClaimTransformLink \`<br />-Identity:"adatum.com" \`<br />-Policy: «DenyAllClaimsPolicy» \`<br />-TrustRole: доверие \`<br />-Server:"contoso.com»\`                                                             |
| Разрешить все утверждения, полученные из Adatum, за исключением «Company» и «Отдел», в Contoso Adatum | Код <br />Новый ADClaimTransformationPolicy \`<br />-Description: «Утверждений политики преобразования, чтобы разрешить все утверждения, за исключением компании "и" Отдел» \`<br /> -Name: «AllowAllClaimsExceptCompanyAndDepartmentPolicy» \`<br />-AllowAllExcept: компании, отдел \`<br />-Server:"contoso.com» \`<br />SET-ADClaimTransformLink \`<br /> -Identity:"adatum.com" \`<br />-Policy:"AllowAllClaimsExceptCompanyAndDepartmentPolicy" \`<br /> -TrustRole: доверие \`<br />-Server:"contoso.com» \` |

## <a name="BKMK_Links"></a>См. также  

-   Список всех командлетов Windows PowerShell, доступных для преобразования утверждений, см. в разделе [Справочник по командлетам для Active Directory PowerShell](https://go.microsoft.com/fwlink/?LinkId=243150).  

-   Расширенные задачи, включающие экспорта и импорта данных конфигурации приложения уровня данных между двумя лесами, используйте [динамическую ссылку PowerShell управления доступом](https://go.microsoft.com/fwlink/?LinkId=243150)  

-   [Развертывание утверждений в лесах](Deploy-Claims-Across-Forests.md)  

-   [Язык правил преобразования утверждений](Claims-Transformation-Rules-Language.md)  

-   [Динамический контроль доступа. Обзор сценария](Dynamic-Access-Control--Scenario-Overview.md)  


