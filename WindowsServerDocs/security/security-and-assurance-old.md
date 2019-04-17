---
title: Безопасность и контроль
description: Обзор обеспечения безопасности в Windows Server2016
ms.custom: na
ms.prod: windows-server-threshold
ms.technology: techgroup-security
ms.tgt_pltfrm: na
ms.topic: article
ms.date: 07/27/2018
ms.assetid: b886b2fd-3567-4f0a-8aa3-4ba7923d2d21
author: coreyp-at-msft
ms.author: coreyp
ms.localizationpriority: medium
ms.openlocfilehash: b32b4879ad454d1154c3d65dbf690cdaae73d76c
ms.sourcegitcommit: 07ac08dea2b8f2763c2614a999dc7967018aa0b4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2018
ms.locfileid: "6121453"
---
# Безопасность и контроль в Windows Server 

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

>[!TIP]
> Ищете дополнительные сведения о старых версиях Windows Server? Ознакомьтесь с нашими другими [библиотеками Windows Server](/previous-versions/windows/) на docs.microsoft.com. Кроме того, вы можете найти нужную информацию [на этом сайте](https://docs.microsoft.com/search/index?search=Windows+Server&dataSource=previousVersions).

<img src="../media/landing-icons/security.png" style='float:left; padding:.5em;' alt="Icon representing a lock"> Положитесь на новые уровни защиты, встроенные в операционную систему для дополнительной защиты от брешей в системе безопасности. Обеспечьте блокировку вредоносных атак и повысьте безопасность виртуальных машин, приложений и данных.


### [Публикация от службы безопасности Windows Server в блоге](https://blogs.technet.microsoft.com/windowsserver/2016/04/25/ten-reasons-youll-love-windows-server-2016-8-security/)
В этой публикации от службы безопасности Windows Server рассматриваются многие улучшения Windows Server, повышающие уровень безопасности в среде размещения и гибридных облачных средах.

### [Datacenter and Private Cloud Security Blog (Блог о безопасности центров обработки данных и частных облаков)](https://blogs.technet.microsoft.com/datacentersecurity/)
Это центральный сайт для блогов, в которых представлена техническая информация от специалистов Microsoft по обеспечению безопасности центров обработки данных и частных облаков.                                    

### [Addressing emerging threats and landscape shifts (Реагирование на возникающие угрозы и изменение условий)](https://www.youtube.com/watch?v=B5JMYxYWx1k&feature=youtu.be)
В этом 6-минутном видео Андерс Вайнберг (Anders Vinberg) дает общее представление о стратегии безопасности и контроля корпорации Майкрософт, а также описывает появляющиеся в отрасли тенденции, связанные с безопасностью. Затем он рассматривает ключевые инициативы корпорации Майкрософт по защите рабочих нагрузок из базовой структуры и защите от прямых атак из привилегированных учетных записей. В конце он объясняет, как новые возможности обнаружения и анализа могут способствовать лучшему определению угроз.

### [Protecting Your Datacenter and Cloud from Emerging Threats blog post (Запись блога. Защита центра обработки данных и облака от возникающих угроз)](http://blogs.technet.com/b/windowsserver/archive/2015/11/18/protecting-your-datacenter-and-cloud-november-update.aspx)
В этой публикации описываются методы применения технологий Майкрософт для защиты центров обработки данных и облачных хранилищ от возникающих угроз.                   

### [Обзорный семинар по безопасности и контролю на конференции Ignite](http://channel9.msdn.com/events/ignite/2015/brk2482)
В этом видео с конференции Ignite речь пойдет о постоянных угрозах, внутренних нарушениях системы безопасности, организованной киберпреступности, а также об обеспечении безопасности облачной платформы Майкрософт (локальных и подключенных служб в Azure). Здесь приведены сценарии для защиты рабочих нагрузок, крупных корпоративных клиентов и поставщиков услуг.                                                                   

## Безопасная виртуализация с использованием экранированных виртуальных машин

### [Экранированная виртуальная машина в Channel 9](http://channel9.msdn.com/Shows/Mechanics/Introduction-to-Shielded-Virtual-Machines-in-Windows-Server-2016)
Пошаговое описание технологии и преимуществ экранированных виртуальных машин.                           

### [Shielded VM Demo (Демонстрация экранированной виртуальной машины)](https://www.youtube.com/watch?v=xip5Qtk-7d8)
В этом 4-минутном видео описывается предназначение экранированных виртуальных машин, а также различия между экранированными и неэкранированными виртуальными машинами.                                   

### [Shielded Virtual Machines in Windows Server video walkthrough (Видеоруководство по использованию экранированных виртуальных машин в Windows Server)](http://microsoft-cloud.cloudguides.com/Guides/Shielded Virtual Machines in Windows Server.htm)
В этом пошаговом видеоруководстве показано, как служба защиты узла включает экранированные виртуальные машины, обеспечивая защиту конфиденциальных данных от несанкционированного доступа администраторов узла Hyper-V.

### [Harden the Fabric: Protecting Tenant Secrets in Hyper-V (Видео с конференции Microsoft Ignite. Усиление защиты структуры: защита секретных данных клиента в Hyper-V)](http://channel9.msdn.com/events/ignite/2015/brk3457)

В этой презентации Ignite обсуждаются дополнительные возможности Hyper-V и диспетчера виртуальных машин, а также новая роль сервера-защитника узла, запускающая экранированные виртуальные машины.                

### [Guarded Fabric Deployment Guide (Руководство по развертыванию защищенной структуры)](https://docs.microsoft.com/windows-server/virtualization/guarded-fabric-shielded-vm/guarded-fabric-deploying-hgs-overview)
В этом руководстве содержится информация об установке и проверке Windows Serverи System Center Virtual Machine Manager для узлов защищенной структуры и экранированных виртуальных машин.

### [Экранированная виртуальная машина и защищенная структура в филиалах](https://docs.microsoft.com/windows-server/virtualization/guarded-fabric-shielded-vm/guarded-fabric-manage-branch-office)
В этом руководстве содержатся советы и рекомендации по запуску экранированных виртуальных машин в филиалах, а также другие дистанционные сценарии, в которых узлы Hyper-V могут работать в условиях ограниченной возможности подключения к HGS.

### [Shielded VM and Guarded Fabric Troubleshooting Guide (Руководство по поиску и устранению неисправностей при использовании экранированной виртуальной машины и защищенной структуры)](https://docs.microsoft.com/windows-server/virtualization/guarded-fabric-shielded-vm/guarded-fabric-troubleshoot-overview)
Это руководство содержит информацию о способах решения проблем, с которыми вы можете столкнуться в среде экранированной виртуальной машины.

### [Shielded VM Article (Статья об экранированных виртуальных машинах)](http://windowsitpro.com/hyper-v/super-secure-hyper-v-environments-shielded-vms-2016)
В этом техническом документе содержатся общие сведения о том, каким образом экранированные виртуальные машины повышают общий уровень безопасности для предотвращения мошенничества.                                         

## Privileged Access Management (Защита Windows и Microsoft Azure Active Directory с помощью управления привилегированным доступом)
### [Обеспечение безопасности привилегированного доступа](https://technet.microsoft.com/windows-server-docs/security/securing-privileged-access/securing-privileged-access)
Схема по обеспечению безопасности привилегированного доступа. В этой схеме учтен совокупный опыт группы по безопасности серверов, ИТ-отдела корпорации Майкрософт, группы Azure и службы консультаций Майкрософт                           

### [Just in Time Administration with Microsoft Identity Manager (JIT-администрирование с помощью Microsoft Identity Manager)](https://technet.microsoft.com/library/mt150258.aspx)
В этой статье рассматриваются функции и возможности Microsoft Identity Manager, включая поддержку управления JIT-управления привилегированным доступом.                                                                    

### [Защита Windows и Microsoft Azure Active Directory с помощью Privileged Access Management](http://channel9.msdn.com/events/ignite/2015/brk3873)
В этой презентации Ignite описаны стратегии и инвестиции корпорации Майкрософт в Windows Server, PowerShell, Active Directory, Identity Manager и Azure Active Directory для устранения рисков доступа администратора с помощью более надежной проверки подлинности и управления доступом с использованием технологий администрирования Just in Time (JIT) и Just Enough Administration (JEA).

### [Just Enough Administration Article (Статья о технологии Just Enough Administration)](http://aka.ms/JEA)
В этом документе представлена концепция и технические детали технологии Just Enough Administration— инструментария PowerShell для предприятий, предназначенного для сокращения рисков путем ограничения доступа операторам. Доступ предоставляется только к определенным ресурсам, необходимым для решения поставленных задач.

### [Демонстрационное видео по Just Enough Administration](https://www.youtube.com/watch?v=xnBrbkY9P20)
Демонстрационное пошаговое руководство по Just Enough Administration.                                                                                                                  
## Защита учетных данных

### [Защита извлеченных учетных данных домена с помощью Credential Guard](https://docs.microsoft.com/windows/security/identity-protection/credential-guard/credential-guard)
Для защиты секретов Credential Guard использует безопасность на основе виртуализации, чтобы только привилегированное системное ПО могло получать доступ к этим данным. Несанкционированный доступ к секретам может привести к атакам, направленным на кражу учетных данных, например Pass-the-Hash или Pass-The-Ticket. Credential Guard предотвращает такие атаки, защищая хэши паролей NTLM и билеты Kerberos Ticket Granting.

### [Защита учетных данных удаленного рабочего стола с помощью Remote Credential Guard](https://docs.microsoft.com/windows/security/identity-protection/remote-credential-guard)
Remote Credential Guard позволяет защитить учетные данные через подключение к удаленному рабочему столу путем перенаправления запросов Kerberos обратно к устройству, запрашивающему соединение. Remote Credential Guard также предоставляет единый вход пользователей в систему для сеансов доступа к удаленному рабочему столу.                                                                                                        |
### [Демонстрационное видео по Credential Guard](https://www.youtube.com/watch?v=eUpKOGSl7yk)
В этом 5-минутном видео демонстрируется Credential Guard и удаленный Credential Guard.         

## Усиление защиты ОС и приложений
### [Руководство по развертыванию компонента "Управление приложениями в Защитнике Windows" (WDAC)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control)
WDAC — это политика настраиваемой целостности кода (CI), которая помогает предприятиям контролировать приложения, выполняющиеся в их средах. К этому компоненту не предъявляются особые аппаратные или программные требования, за исключением необходимости использования Windows 10.

### [Демонстрационное видео по Device Guard](https://www.youtube.com/watch?v=F-pTkesjkhI)
Device Guard — это сочетание WDAC и службы целостности кода с защищенной низкоуровневой оболочкой (HVCI). Это 7-минутное видео описывает Device Guard и его использование в Windows Server.

### [Параметры реестра безопасности транспортного уровня (протокол TLS)](https://docs.microsoft.com/windows-server/security/tls/tls-registry-settings)
Сведения о поддерживаемых параметрах реестра для реализации в Windows протокола TLS и протокола SSL.

### [Защита потока управления](https://docs.microsoft.com/windows/desktop/SecBP/control-flow-guard)
Защита потока управления обеспечивает встроенную защиту от некоторых видов атак, основанных на повреждении памяти.

### [Защитник Windows](https://technet.microsoft.com/windows-server-docs/security/windows-defender/windows-defender-overview-windows-server)
Защитник Windows обеспечивает возможности активного обнаружения для блокировки известных вредоносных программ. Защитник Windows включен по умолчанию и оптимизирован для поддержки различных ролей сервера в Windows Server.

##Обнаружение угроз и реагирование на них
### [Security Threat Analysis Using Microsoft Operations Management Suite (Анализ угроз безопасности с помощью Microsoft Operations Management Suite)](https://channel9.msdn.com/events/ignite/2015/brk3464)
В этой презентации Ignite обсуждается вопрос использования оперативной аналитики для анализа угроз безопасности.

### [Microsoft Operations Management Suite (OMS)](https://www.microsoft.com/en-us/server-cloud/operations-management-suite/overview.aspx)
Решение Microsoft Operations Management Suite (OMS) по безопасности и аудиту обрабатывает журналы безопасности и события брандмауэра, поступающие от локальных ресурсов и из облачной среды. Эти данные используются для анализа и обнаружения вредоносной деятельности.

### [OMS и Windows Server](https://www.youtube.com/watch?v=_SaDw1dRy2k)
Это 3-минутное видео показывает, как OMS может помочь в обнаружении потенциально вредоносного поведения, блокируемого Windows Server.  

### [Microsoft Advanced Threat Analytics](http://blogs.technet.com/b/ad/archive/2015/07/22/microsoft-advanced-threat-analytics-coming-next-month.aspx)
В этой записи блога рассматривается служба Microsoft Advanced Threat Analytics— локальный продукт, который использует сетевой трафик Active Directory и данные SIEM для выявления потенциальных угроз и предупреждения о них.

### [Microsoft Advanced Threat Analytics](https://www.youtube.com/watch?v=0nA9FeTRZFw&list=PL8nfc9haGeb5IZGM8HvmRozetHRpBDKSw)
В этом трехминутном видео рассказывается о новых функциях для анализа угроз безопасности в Windows Server.                                                                                 |

## Сетевая безопасность

### [Обзор брандмауэра центра обработки данных](https://technet.microsoft.com/library/dn920240.aspx)
В этом обзоре рассматривается брандмауэр центра обработки данных сетевого уровня с пятью кортежами (протокол, номера начального и конечного портов, начальный и конечный IP-адреса), с функцией отслеживания состояния и поддержкой нескольких клиентов.

### [Новые возможности управления IP-адресами (DNS) в Windows Server](https://technet.microsoft.com/windows-server-docs/networking/dns/what-s-new-in-dns-server)
В этой обзорной статье дано краткое описание новых возможностей службы DNS, а также полезные ссылки для получения дополнительных сведений.                                                                           

## Сопоставление функций безопасности с требованиями по обеспечению соответствия

Соответствие является важным аспектом реализации функций безопасности. Мы даем квалифицированный совет по обеспечению соответствия, поясняем, что значит соответствие для ваших доверенных консультантов, а также предлагаем начальное сопоставление, которое вы можете использовать при оценке Windows Server.

-   [Технический документ по сопоставлению соответствия для экранированных виртуальных машин Hyper-V](https://download.microsoft.com/download/6/D/0/6D06E149-B4C1-4EED-ACD5-DF6066E93CC0/Coalfire_Branded_Hyper_V_Shielded_VMs_Whitepaper_EN_US.pdf)

-   [Технический документ по сопоставлению соответствия для JEA и JIT](https://download.microsoft.com/download/2/7/A/27A2B5BB-6B52-4482-87C1-DA9D6B6D8C8D/Coalfire_Branded_Privileged_Identity_Manager_Whitepaper_EN_US.pdf)

-   [Технический документ по сопоставлению соответствия для Device Guard](https://download.microsoft.com/download/6/9/D/69D9E610-D23C-4F7E-A8CC-D65B87CEB4F8/Coalfire_Branded_Device_Guard_Whitepaper_EN_US.pdf)

-   [Технический документ по сопоставлению соответствия для Credential Guard](https://download.microsoft.com/download/8/1/2/812009C9-E4B8-4D4B-AADD-FDC373D0A076/Coalfire_Branded_Credential_Guard_Whitepaper_EN_US.pdf)

-   [Технический документ по сопоставлению соответствия для Защитника Windows](https://download.microsoft.com/download/C/7/7/C778B7BB-0783-42D7-93A9-B86DFB5A7BAD/Coalfire_Branded_Windows_Defender_Whitepaper_EN_US.pdf)
