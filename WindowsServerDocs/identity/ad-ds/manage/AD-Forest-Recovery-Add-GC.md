---
title: "Восстановление леса AD — Добавление глобального Каталога"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 07/07/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.assetid: 5a291f65-794e-4fc3-996e-094c5845a383
ms.technology: identity-adfs
ms.openlocfilehash: 3749fd99737f61c55871f613b9feaa21090d3bae
ms.sourcegitcommit: 84a2bdcb92ba6af45781fab9727617e50fa5e911
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/07/2017
---
# <a name="ad-forest-recovery---adding-the-gc"></a>Восстановление леса AD — Добавление глобального Каталога 

>Область применения: Windows Server 2016, Windows Server 2012 и 2012 R2, Windows Server 2008 и 2008 R2

 Используйте следующую процедуру для добавления глобального каталога на контроллер домена.  
  
## <a name="to-add-the-global-catalog"></a>Чтобы добавить глобальный каталог  
  
1.  Нажмите кнопку **запустить**, наведите курсор на **все программы**, наведите курсор на **Администрирование**, а затем нажмите кнопку **Active Directory — сайты и службы**.  
2.  В дереве консоли разверните узел **сайты** контейнера, а затем выберите нужный узел, содержащий целевого сервера.  
3.  Разверните **серверы** контейнера, а затем разверните объект сервера контроллера домена, к которому следует добавить глобальный каталог.  
4.  Щелкните правой кнопкой мыши **параметров NTDS**, а затем нажмите кнопку **свойства**.  
5.  Выберите **глобального каталога** флажок.  
![Добавление глобального Каталога](media/AD-Forest-Recovery-Add-GC/addgc1.png)
  
## <a name="to-add-the-global-catalog-using-repadmin"></a>Добавление глобального каталога, с помощью Repadmin  
  
1.  Откройте командную строку с повышенными привилегиями, введите следующую команду и нажмите клавишу ВВОД:  
  
    ```  
    repadmin.exe /options DC_NAME +IS_GC  
    ```  
  
 Далее приводятся способы, чтобы ускорить процесс добавления глобального каталога на контроллер домена в корневом домене.  
  
-   В идеальном случае контроллера домена в корневом домене должен быть партнера репликации восстановленные контроллеры домена в некорневых доменах. Если это так, убедитесь, что средство проверки согласованности знаний (KCC) соответствующий **repsFrom** объект для исходного контроллера домена и раздел, в корне контроллера домена. Это можно проверить, выполнив **repadmin /showreps /v** команды.  
  
-   Если имеется не **repsFrom** создана, создайте для раздела конфигурации этого объекта. Таким образом, контроллер домена в корневом домене можно определить, какие контроллеры домена в домене некорневых были удалены. Это можно сделать с помощью следующих команд:  
  
    ```  
    repadmin /add ConfigurationNamingContext DestinationDomainController SourceDomainControllerCNAME  
    ```  
  
    ```  
    repadmin /options DSA -Disable_NTDSCONN_XLATE  
    ```  
  
     Формат *SourceDomainControllerCNAME* является:  
  
    ```  
  
    sourceDCGuid._msdcs.root domain  
    ```  
  
     Например может быть команды repadmin /add для раздела конфигурации contoso.com домена.  
  
    ```  
    repadmin /add cn=configuration,DC=contoso,DC=com DC01 937ef930-7356-43c8-88dc-8baaaa781cf6._msdcs.dDSP17A22.contoso.com  
    ```  
  
-   Если **repsFrom** объект присутствует, попробуйте синхронизировать контроллера домена в корневом домене с контроллером домена в домене некорневых следующим образом:  
  
    ```  
    Repadmin /sync DomainNamingContext DestinationDomainController SourceDomainControllerGUID  
    ```  
  
     Где *DestinationDomainController* контроллер домена в корневом домене и *SourceDomainController* восстановленный контроллер домена в домене некорневых.  
  
-   Корневой сервер DNS домена должны иметь записей ресурсов псевдонимов (CNAME) для исходного контроллера домена. Убедитесь, что в зону DNS содержит записи ресурсов делегирования (записей ресурсов узла (A) и сервера имен (NS)) для правильного контроллеров домена (контроллеры домена, которые были восстановлены из резервной копии) в дочерней зоны.  
  
-   Убедитесь, что контроллер домена в корневом домене пытается связаться с правильный центра распространения ключей (KDC) не корневого домена. Чтобы проверить это, в командной строке, введите следующую команду и нажмите клавишу ВВОД:  
  
    ```  
    nltest /dsgetdc:nonroot domain name /KDC /Force  
    ```  
## <a name="next-steps"></a>Дальнейшие действия

- [Руководство по восстановлению леса AD](AD-Forest-Recovery-Guide.md)
- [Восстановление леса AD — процедуры](AD-Forest-Recovery-Procedures.md)  