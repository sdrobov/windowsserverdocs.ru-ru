---
ms.assetid: bbb5b68f-00ad-4715-8176-0c2769b706c4
title: Руководство по развертыванию служб федерации Active Directory в Windows Server 2012 R2
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 05f1ea6830237813e6fd2bd6a172f467e8d81065
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59839085"
---
# <a name="deploying-a-federation-server-farm"></a>Развертывание фермы серверов федерации

>Область применения. Windows Server 2016, Windows Server 2012 R2

Для развертывания фермы серверов федерации выполните задачи из этого контрольного списка в указанном порядке. В случае перехода по ссылке в раздел общих понятий вернитесь после его просмотра в данный контрольный список, чтобы продолжить выполнение оставшихся задач в контрольном списке.  
  
![Развертывание фермы серверов федерации](media/2b05dce3-938f-4168-9b8f-1f4398cbdb9b.gif)**контрольный список: Развертывание фермы серверов федерации**  
  
||Задача|Ссылка|  
|-|--------|-------------|  
|![Развертывание фермы серверов федерации](media/icon_checkboxo.gif)|Просмотрите основные понятия и рекомендации, как при подготовке к развертыванию служб федерации Active Directory \(AD FS\). **Примечание.**|![Развертывание фермы серверов федерации](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[руководство по проектированию AD FS в Windows Server 2012 R2](../../ad-fs/design/AD-FS-Design-Guide-in-Windows-Server-2012-R2.md)<br /><br />![Развертывание фермы серверов федерации](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Understanding Key AD FS Concepts](../../ad-fs/technical-reference/Understanding-Key-AD-FS-Concepts.md)|  
||Если вы решили использовать Microsoft SQL Server для хранилища конфигурации AD FS, убедитесь, что развернут функциональный экземпляр SQL Server.|[SQL Server](https://technet.microsoft.com/sqlserver) **предупреждение:** Если вы хотите создать ферму AD FS в Windows Server 2012 R2 и использовать SQL Server для хранения данных конфигурации, то можете использовать SQL Server 2008 или более поздние версии, включая SQL Server 2012.|  
|![Развертывание фермы серверов федерации](media/icon_checkboxo.gif)|Присоедините компьютер к домену Active Directory.|![Развертывание фермы серверов федерации](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[присоединить компьютер к домену](Join-a-Computer-to-a-Domain.md)|  
|![Развертывание фермы серверов федерации](media/icon_checkboxo.gif)|Регистрация Secure Socket Layer \(SSL\) сертификата для AD FS.|![Развертывание фермы серверов федерации](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[подачи заявки на SSL-сертификат AD FS](Enroll-an-SSL-Certificate-for-AD-FS.md)|  
|![Развертывание фермы серверов федерации](media/icon_checkboxo.gif)|Установите службу роли AD FS.|![Развертывание фермы серверов федерации](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[установить службу роли AD FS](Install-the-AD-FS-Role-Service.md)|  
|![Развертывание фермы серверов федерации](media/icon_checkboxo.gif)|Настройте сервер федерации.|![Развертывание фермы серверов федерации](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[Настройка сервера федерации](Configure-a-Federation-Server.md)|  
|![Развертывание фермы серверов федерации](media/icon_checkboxo.gif)|Дополнительный шаг: Настройка сервера федерации с помощью службы регистрации устройств \(DRS\).|![Развертывание фермы серверов федерации](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Настройка сервера федерации с помощью службы регистрации устройств](Configure-a-federation-server-with-Device-Registration-Service.md)|  
|![Развертывание фермы серверов федерации](media/icon_checkboxo.gif)|Добавление узла \(объект\) и псевдоним \(CNAME\) записи ресурса для корпоративных доменных имен \(DNS\) для службы федерации и DRS.|![Развертывание фермы серверов федерации](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Настройка корпоративной DNS для службы федерации и DRS](Configure-Corporate-DNS-for-the-Federation-Service-and-DRS.md)|  
|![Развертывание фермы серверов федерации](media/icon_checkboxo.gif)|Проверьте работоспособность сервера федерации.|![Развертывание фермы серверов федерации](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[убедитесь, что Federation Server функционирования](Verify-That-a-Federation-Server-Is-Operational.md)|  
  

## <a name="see-also"></a>См. также  
[Развертывание AD FS](../../ad-fs/AD-FS-Deployment.md)  

[Руководство по развертыванию Windows Server 2012 R2 AD FS](../../ad-fs/deployment/Windows-Server-2012-R2-AD-FS-Deployment-Guide.md)  
  

