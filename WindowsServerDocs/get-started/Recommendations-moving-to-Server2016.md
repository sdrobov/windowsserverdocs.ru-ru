---
title: Рекомендации по переходу на Windows Server 2016
description: Рекомендации по переходу на Windows Server 2016.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.date: 10/18/2016
ms.technology: server-general
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 74aa1da3-7076-4a1f-ad5b-9e17bd46dba2
author: jaimeo
ms.author: jaimeo
manager: dongill
ms.localizationpriority: medium
ms.openlocfilehash: be63880e8a07e71aa6811f3a6979eb6e2fcd8eba
ms.sourcegitcommit: 083ff9bed4867604dfe1cb42914550da05093d25
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2020
ms.locfileid: "75947808"
---
# <a name="recommendations-for-moving-to-windows-server-2016"></a>Рекомендации по переходу на Windows Server 2016

>Область применения. Windows Server 2016


|Используемая версия|Windows Server 2012 R2 или Windows Server 2012|Windows Server 2008 R2 или Windows Server 2008|  
|-------------------|----------|--------------|--------------|---------------------------------------|  
|**Инфраструктура ролей Windows Server**|Выберите обновление или перенос согласно [руководству по конкретной роли](https://technet.microsoft.com/windowsserver/jj554790).|— Чтобы воспользоваться новыми функциями в Windows Server 2016, разверните новое оборудование или установите Windows Server 2016 на виртуальной машине существующего узла. Некоторые новые функции лучше всего работают на физическом узле Windows Server 2016 с Hyper-V. <br>— Следуйте [руководству по конкретной роли](https://technet.microsoft.com/windowsserver/jj554790).|
|**Управление сервером Microsoft и рабочие нагрузки приложений**|— Обновления приложений должны включать *перенос* в Windows Server 2016. См. [список совместимости](Server-Application-Compatibility.md). <br>— Для обновлений только до Windows Server 2016 (т. е. без обновления приложений) следует использовать руководство по конкретному приложению.|— Чтобы воспользоваться новыми функциями в Windows Server 2016, разверните новое оборудование или установите Windows Server 2016 на виртуальной машине существующего узла. Некоторые новые функции лучше всего работают на физическом узле Windows Server 2016 с Hyper-V. Следуйте указаниям соответствующего руководства по переносу. <br>— Вы также можете использовать текущую ОС, запустив ее в виртуальной машине на узле Windows Server 2016 или в Microsoft Azure. Обратитесь к торговому посреднику EA, TAM или в Майкрософт для получения расширенных вариантов поддержки по программе [Software Assurance](https://www.microsoft.com/Licensing/licensing-programs/software-assurance-default.aspx).|
|**Рабочие нагрузки приложений независимых поставщиков программного обеспечения**|— Для обновлений только до Windows Server 2016 следует использовать руководство по конкретному приложению. <br>Дополнительные сведения о совместимости Windows Server с приложениями сторонних разработчиков см. на [портале сертификации для получения логотипа совместимости с Windows Server](https://msdn.microsoft.com/enterprisecloudcertified).|— Чтобы воспользоваться новыми функциями в Windows Server 2016, разверните новое оборудование или установите Windows Server 2016 на виртуальной машине существующего узла. Некоторые новые функции лучше всего работают на физическом узле Windows Server 2016 с Hyper-V. Следуйте указаниям соответствующего руководства по переносу. <br>— Вы также можете использовать текущую ОС, запустив ее в виртуальной машине на узле Windows Server 2016 или в Microsoft Azure. Обратитесь к торговому посреднику EA, TAM или в Майкрософт для получения расширенных вариантов поддержки по программе [Software Assurance](https://www.microsoft.com/Licensing/licensing-programs/software-assurance-default.aspx).|
|**Рабочие нагрузки настраиваемых приложений**|— Обратитесь к разработчикам приложений для получения сведений о совместимости с Windows Server 2016 и руководства по обновлению. <br>— Используйте Microsoft Azure для тестирования приложения на Windows Server 2016 перед переходом на них. <br>— См. полный список вариантов в следующем разделе.|— Обратитесь к разработчикам приложений для получения сведений о совместимости с Windows Server 2016 и руководства по обновлению. <br>— Используйте Microsoft Azure для тестирования приложения на Windows Server 2016 перед переходом на них. <br>— Чтобы воспользоваться новыми функциями в Windows Server 2016, разверните новое оборудование или установите Windows Server 2016 на виртуальной машине существующего узла. Некоторые новые функции лучше всего работают на физическом узле Windows Server 2016 с Hyper-V. <br>— См. полный список вариантов в следующем разделе.|

## <a name="complete-options-for-moving-servers-running-custom-or-in-house-applications-on-older-versions-of-windows-server-to-windows-server-2016"></a>Полный перечень вариантов перехода с использования серверов, на которых работают ваши собственные приложения в более старых версиях Windows Server, на использование Windows Server 2016

Сейчас доступно множество возможностей для того, чтобы помочь вам и вашим клиентам использовать функции Windows Server 2016 с минимальными последствиями для текущих служб и рабочих нагрузок.

- Испытайте последнюю операционную систему в работе с вашим приложением, скачав ознакомительную версию [Windows Server](https://www.microsoft.com/evalcenter/evaluate-windows-server-2016) для тестирования в локальной среде. После тестирования и подтверждения ее пригодности можно легко преобразовать лицензию с помощью розничного лицензионного ключа (требуется перезапуск).

- [Microsoft Azure](https://azure.microsoft.com) также можно использовать в режиме пробной версии, чтобы убедиться в работоспособности вашего собственного приложения в последней версии серверной операционной системы. После тестирования и подтверждения качества локально [выполните перенос на последнюю версию Windows Server](https://docs.microsoft.com/windows-server/get-started/installation-and-upgrade#upgrade). 

- После тестирования и подтверждения пригодности такое можно использовать [Microsoft Azure](https://azure.microsoft.com) как постоянное расположение для вашего приложения или службы. Таким образом, старый сервер остается доступным, пока вы не будете готовы перейти на новый сервер в Azure.

    - Если вы уже используете программу Software Assurance для Windows Server, вы можете сэкономить, проведя развертывание с помощью [преимущества гибридного использования Azure](https://azure.microsoft.com/pricing/hybrid-use-benefit/). 

- Чаще всего [Microsoft Azure](https://azure.microsoft.com) можно использовать для размещения того же приложения в более ранней версии Windows Server, которая еще используется. Перенос приложения и рабочей нагрузки в виртуальную машину с необходимой операционной системой возможен с помощью образов [Azure Marketplace](https://azure.microsoft.com/marketplace/).

    - Если вы уже используете программу Software Assurance для Windows Server, вы можете сэкономить, проведя развертывание с помощью [преимущества гибридного использования Azure](https://azure.microsoft.com/pricing/hybrid-use-benefit/). 

- Программа [Software Assurance](https://www.microsoft.com/Licensing/licensing-programs/software-assurance-default.aspx) для Windows Server предоставляет новые преимущества для прав на использование версии. Помимо других преимуществ, серверы с покрытием Software Assurance могут обновляться до последней версии Windows Server в нужный момент без необходимости приобретать новую лицензию. 

## <a name="additional-resources"></a>Дополнительные ресурсы

- [Компоненты, удаленные или нерекомендуемые к использованию в Windows Server 2016](deprecated-features.md)
- Варианты общего обновления и переноса сервера см. в разделе [Варианты обновления и преобразования для Windows Server 2016](Supported-Upgrade-Paths.md).
- Дополнительные сведения о жизненном цикле продукта и уровнях поддержки см. в разделе [Часто задаваемые вопросы по политике жизненного цикла поддержки](https://support.microsoft.com/help/17140/support-lifecycle-policy-faq).

