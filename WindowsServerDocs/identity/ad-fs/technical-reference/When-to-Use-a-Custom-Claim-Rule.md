---
ms.assetid: 20d183f0-ef94-44bb-9dfc-ed93799dd1a6
title: Когда следует использовать настраиваемое правило для утверждений
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 28d22b6364b7b5f3facd9aa0f84a74f9448f7455
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86958606"
---
# <a name="when-to-use-a-custom-claim-rule"></a>Когда следует использовать настраиваемое правило для утверждений
Вы пишете настраиваемое правило утверждения в службы федерации Active Directory (AD FS) \( AD FS \) с помощью языка правил утверждений, который является платформой, используемой подсистемой выдачи утверждений для программного создания, преобразования, передачи и фильтрации утверждений. Используя настраиваемое правило, вы можете создавать правила с более сложной логикой, чем с помощью стандартного шаблона правил. Рассмотрите возможность использования настраиваемого правила, когда требуется выполнять следующее.  
  
-   Отправка утверждений на основе значений, извлеченных из \( \) хранилища атрибутов SQL язык SQL.  
  
-   Отправка утверждений на основе значений, извлеченных из \( \) хранилища атрибутов LDAP с помощью настраиваемого фильтра LDAP.  
  
-   Отправлять утверждения на основе значений, извлекаемых из настраиваемого хранилища атрибутов.  
  
-   Отправлять утверждения только в том случае, если имеется не менее двух входящих утверждений.  
  
-   Отправка утверждения только в том случае, если значение входящего утверждения соответствует сложному шаблону.  
  
-   Отправлять утверждения со сложными изменениями значения входящего утверждения.  
  
-   Создавать утверждения для использования только в последующих правилах, без фактической отправки этих утверждений.  
  
-   Строить исходящее утверждение на основе содержимого нескольких входящих утверждений.  
  
Вы также можете использовать настраиваемое правило, когда значение исходящего утверждения должно строиться на значении входящего утверждения, но с дополнительным содержимым.  
  
Язык правил для утверждений основывается на правилах. Он имеет часть условий и выполняемую часть. Используя синтаксис языка правил для утверждений, вы можете перечислять, добавлять, удалять или изменять утверждения в соответствии с потребностями вашей организации. Дополнительные сведения о том, как работает каждая из этих частей, см. [в разделе роль языка правил утверждений](The-Role-of-the-Claim-Rule-Language.md).  
  
В следующих разделах содержатся основные сведения о правилах утверждений. В них также говорится о том, когда следует использовать настраиваемые правила для утверждений.  
  
## <a name="about-claim-rules"></a>Общие сведения о правилах утверждения  
Правило утверждения представляет экземпляр бизнес-логики, который принимает входящее утверждение, применяет к нему условие, \( если x, затем y \) и создает исходящее утверждение на основе параметров условия.  
  
> [!IMPORTANT]  
> -   В оснастке управления AD FS \- в можно создавать правила утверждений только с помощью шаблонов правил утверждений.  
> -   Правила утверждений обрабатывают входящие утверждения либо непосредственно из поставщика утверждений, \( например Active Directory или другой служба Федерации, \) либо из выходных данных правил преобразования принятия в отношении доверия поставщика утверждений.  
> -   Правила утверждений обрабатываются подсистемой выдачи утверждений в хронологическом порядке в пределах заданного набора правил. Установив приоритет правил, можно дополнительно уточнять или фильтровать утверждения, созданные предыдущими правилами в данном наборе правил.  
> -   Шаблоны правил для утверждений всегда требуют указывать тип входящего утверждения. Однако вы можете обрабатывать несколько значений утверждений с одним типом утверждения, используя одно правило.  
  
Дополнительные сведения о правилах утверждений и наборах правил для утверждений см. [в разделе роль правил утверждений](The-Role-of-Claim-Rules.md). Дополнительные сведения о том, как правила обрабатываются, см. [в разделе роль подсистемы утверждений](The-Role-of-the-Claims-Engine.md). Дополнительные сведения о том, как обрабатываются наборы правил для утверждений, см. [в разделе роль конвейера утверждений](The-Role-of-the-Claims-Pipeline.md).  
  
## <a name="how-to-create-this-rule"></a>Создание правила  
Это правило создается путем создания синтаксиса, необходимого для выполнения операции, с помощью языка правил заявок, а затем вставляется результат в текстовое поле, предоставленное в разделе Отправка утверждений с помощью настраиваемого шаблона правила, в свойствах отношения доверия поставщика утверждений или отношения доверия с проверяющей стороной в оснастке управления AD FS \- в.  
  
Этот шаблон правил предоставляет следующие возможности.  
  
-   указание имени правила утверждения;  
  
-   Введите одно или несколько необязательных условий и инструкцию выдачи, используя язык правил для утверждений AD FS  
  
Дополнительные инструкции по созданию настраиваемого правила с помощью этого шаблона см. в разделе [Создание правила для отправки утверждений с помощью настраиваемого правила](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807049(v=ws.11)) в AD FSном руководством по развертыванию.  
  
Чтобы лучше понять принципы работы языка правил утверждений, просмотрите синтаксис языка правил утверждений для других правил, которые уже существуют в оснастке, \- щелкнув вкладку **язык правил** в свойствах этого правила. Используя сведения данного раздела и информацию о синтаксисе на этой вкладке, можно глубже понять процесс создания собственных настраиваемых правил.  
  
Дополнительные сведения об использовании языка правил утверждений см. [в разделе роль языка правил утверждений](The-Role-of-the-Claim-Rule-Language.md).  
  
## <a name="using-the-claim-rule-language"></a>С помощью языка правил утверждений  
  
### <a name="example-how-to-combine-first-and-last-names-based-on-a-users-name-attribute-values"></a>Пример. Объединение имен и фамилий в зависимости от значений атрибута имени пользователя  
Следующий синтаксис правила объединяет имена и фамилии из значений атрибутов в указанном хранилище атрибутов. Обработчик политик формируют декартово произведение совпадений для каждого условия. Например, результат для имени {"Федор", "Алан"} и фамилии {"Миллер", "Shen)"} — {"Федор Миллер", "Федор Shen)", "Алан Миллер", "Алан Shen)"}:  
  
```  
c1:[type == "http://exampleschema/firstname" ]  
&&  c2:[type == "http://exampleschema/lastname",]   
=> issue(type = "http://exampleschema/name", value = c1.value + "  " + c2.value);  
```  
  
### <a name="example-how-to-issue-a-manager-claim-based-on-whether-users-have-direct-reports"></a>Пример. Выдача утверждения о руководителе на основе наличия у пользователей подчиненных  
Следующее правило выдает утверждение о руководителе только в том случае, если пользователь имеет подчиненных.  
  
```  
c:[type == "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name"] => add(store = "SQL Store", types = ("http://schemas.xmlsoap.org/claims/Reports"), query = "SELECT Reports FROM dbo.DirectReports WHERE UserName = {0}", param = c.value );  
count([type == "http://schemas.xmlsoap.org/claims/Reports"] ) > 0 => issue(= "http://schemas.xmlsoap.org/claims/ismanager", value = "true");  
```  
  
### <a name="example-how-to-issue-a-ppid-claim-based-on-an-ldap-attribute"></a>Пример. Выдача утверждения PPID на основе атрибута LDAP  
Следующее правило выдает PPID утверждение частного личного \( идентификатора \) на основе атрибутов **виндовсаккаунтнаме** и **ORIGINALISSUER** пользователей в хранилище атрибутов LDAP:  
  
```  
c:[Type == "https://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname"]  
 => issue(store = "_OpaqueIdStore", types = ("http://schemas.xmlsoap.org/ws/2005/05/identity/claims/privatepersonalidentifier"), query = "{0};{1};{2}", param = "ppid", param = c.Value, param = c.OriginalIssuer);  
```  
  
Ниже перечислены общие атрибуты, которые могут использоваться для идентификации пользователя для данного запроса.  
  
-   **user SID**  
  
-   **windowsaccountname**  
  
-   **SamAccountName**  
  
