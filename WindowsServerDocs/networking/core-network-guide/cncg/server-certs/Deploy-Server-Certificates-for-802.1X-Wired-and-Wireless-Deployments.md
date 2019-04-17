---
title: Развертывание сертификатов сервера для проводных и беспроводных развертываний 802.1 X
description: Этот раздел входит руководство развертывание сервера сертификатов для развертывания беспроводных и проводных сетей 802.1 X
manager: brianlic
ms.topic: article
ms.assetid: 0a39ecae-39cc-4f26-bd6f-b71ed02fc4ad
ms.prod: windows-server-threshold
ms.technology: networking
ms.author: pashort
author: shortpatti
ms.openlocfilehash: fda9b2b53d088cc389e98cf96fecd748419bc6e2
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="deploy-server-certificates-for-8021x-wired-and-wireless-deployments"></a>Развертывание сертификатов сервера для проводных и беспроводных развертываний 802.1 X

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

В этом руководстве можно использовать, чтобы развернуть сертификаты сервера для серверов инфраструктуры удаленного доступа и сервера политики сети (NPS).   

Это руководство содержит следующие разделы.  

-   [Необходимые условия для использования в этом руководстве](#bkmk_pre)  

-   [Что это руководство не содержит](#bkmk_not)  

-   [Обзор технологий](#bkmk_tech)  

-   [Обзор развертывания сертификата сервера](Server-Certificate-Deployment-Overview.md)  

-   [Планирование развертывания сертификата сервера](Server-Certificate-Deployment-Planning.md)  

-   [Развертывание сертификатов сервера](Server-Certificate-Deployment.md)  

### **<a name="digital-server-certificates"></a>Сертификаты сервера цифровой**  
Это руководство содержит инструкции по использованию служб сертификатов Active Directory (AD CS) для автоматической регистрации сертификатов для удаленного доступа и серверов политики сети инфраструктуры. AD CS можно создать инфраструктуру открытых ключей (PKI) и предоставлять шифровании с открытым ключом, цифровые сертификаты и цифровые подписи для вашей организации.  

При использовании сервера цифровые сертификаты для проверки подлинности между компьютерами в сети, предоставьте сертификаты:   

1. Конфиденциальности с помощью шифрования.  
2. Целостности с помощью цифровых подписей.  
3. Проверка подлинности с помощью привязывания ключей сертификата учетные записи компьютера, пользователя или устройства в сети.  

### **<a name="server-types"></a>Тип сервера**  
С помощью этого руководства, можно развернуть сертификаты сервера следующие типы серверов.  
- Серверы под управлением службы удаленного доступа, которые DirectAccess или серверы стандартных виртуальной частной сети (VPN), и которые являются членами **серверы RAS и IAS** группы.  
- Серверы, на которых выполняется служба сервера политики сети (NPS), являются членами **серверы RAS и IAS** группы.  

### **<a name="advantages-of-certificate-autoenrollment"></a>Преимущества автоматической регистрации сертификатов**  
Автоматическая регистрация сертификатов сервера, также называется автоматической регистрации, предоставляет следующие преимущества.  

- AD CS центр сертификации (ЦС) автоматически регистрирует сертификат сервера для всех серверов политики сети и удаленного доступа.  
- Все компьютеры в домене автоматически получать сертификат, который устанавливается в доверенные корневые центры сертификации хранения на каждый компьютер домена. Таким образом все компьютеры в домене доверия сертификатов, выданных центром сертификации. Этого отношения доверия позволяет серверам проверки подлинности подтвердившие свои удостоверения друг к другу и привлечь безопасные подключения.  
- Кроме обновление групповой политики, изменения конфигурации вручную на каждом сервере не требуется.  
- Каждый сертификат сервера содержит проверка подлинности сервера и проверка подлинности клиента в расширений улучшенного ключа (EKU).  
- Масштабируемость. После развертывания корпоративного корневого ЦС с помощью этого руководства, можно развернуть инфраструктуру открытых ключей (PKI), добавив подчиненного ЦС предприятия.  
- Управляемость. AD CS можно управлять с помощью консоли AD CS или с помощью команд и сценариев Windows PowerShell.  
- Простота. Задать серверы, регистрацию сертификатов сервера, используя учетные записи групп Active Directory и членство в группе.   
- При развертывании сертификатов сервера, сертификаты на основе шаблона, настроенной с помощью инструкций в этом руководстве. Это означает, что вы можете настроить разные шаблоны сертификатов для определенными типами серверов, или же шаблон можно использовать для всех сертификатов сервера, которые вы хотите выдавать.  

## <a name="bkmk_pre"></a>Необходимые условия для использования в этом руководстве  

Это руководство содержит инструкции о том, как развертывание сертификатов сервера с помощью AD CS и роли сервера веб-сервер (IIS) в Windows Server 2016. Ниже перечислены компоненты, необходимые для выполнения процедур, описанных в данном руководстве.  

- Необходимо развернуть основную сеть, с помощью Windows Server 2016 руководства по основной сети, или необходимо иметь технологии, представленные в руководстве по основной сети установлены и функционируют в вашей сети должным образом. Эти технологии включают TCP/IP v4, DHCP, Active Directory доменных служб (AD DS), DNS и NPS.  
>[!NOTE]
>Windows Server 2016 руководства по основной сети можно найти в технической библиотеке Windows Server 2016. Дополнительные сведения см. в разделе [руководство по основной сети](../../../core-network-guide/Core-Network-Guide.md).

- Необходимо прочитать разделе планирования данного руководства, чтобы убедиться, что вы подготовлены для этого развертывания до выполнения развертывания.  
- Необходимо выполнить действия в данном руководстве в указанном порядке. Не перескочить и развертывании центра сертификации без выполнения действий, которые ведут к развертыванию сервера или развертывания не удастся.  
- Вам необходимо подготовить для развертывания два новых сервера в сети — один сервер, на котором будет установки служб AD CS качестве корпоративного корневого ЦС и один сервер, на котором устанавливается веб-сервер (IIS), чтобы ЦС можно опубликовать список отзыва сертификатов (CRL) на веб-сервер.   

>[!NOTE]  
>Вы готовы назначить статический IP-адрес AD CS и веб-серверы, настроенные для развертывания с помощью этого руководства, а также для имен компьютеров в соответствии с соглашения об именовании вашей организации. Кроме того необходимо присоединять компьютеры к вашему домену.  

## <a name="bkmk_not"></a>Что это руководство не содержит  
Это руководство не содержит подробных инструкций по проектированию и развертыванию инфраструктуры открытых ключей (PKI) с помощью AD CS. Рекомендуется изучить документацию AD CS и PKI разработки документации перед развертыванием технологий в данном руководстве.   

## <a name="bkmk_tech"></a>Обзор технологий  
Ниже приведены Обзор технологий для AD CS и веб-сервер (IIS).  

### <a name="active-directory-certificate-services"></a>Службы сертификатов Active Directory  
AD CS в Windows Server 2016 предоставляет настраиваемые службы для создания и управления сертификатами X.509, которые используются в программных системах безопасности, применяющих технологии открытых ключей. Организации могут использовать AD CS для повышения безопасности путем привязки удостоверения пользователя, устройства или службы, чтобы соответствующий открытый ключ. AD CS также включает функции, которые позволяют управлять регистрации сертификатов и отзыв в различных масштабируемых сред.  

Дополнительные сведения см. в разделе [Обзор служб сертификатов Active Directory](https://technet.microsoft.com/library/hh831740.aspx) и [рекомендации по проектированию открытый ключ инфраструктуры ](https://social.technet.microsoft.com/wiki/contents/articles/2901.public-key-infrastructure-design-guidance.aspx).  

### <a name="web-server-iis"></a>Веб-сервер (IIS)  

Роль веб-сервер (IIS) в Windows Server 2016 предоставляет безопасную, простую в управлении, модульную и расширяемую платформу для надежного размещения веб-сайтов, служб и приложений. Со службами IIS общий доступ к информации пользователям в Интернете, интрасети или экстрасети. IIS является унифицированной веб-платформой, которая интегрирует IIS, ASP.NET, службы FTP, PHP и Windows Communication Foundation (WCF).  

Дополнительные сведения см. в разделе [Обзор веб-сервер (IIS)](https://technet.microsoft.com/library/hh831725.aspx).  