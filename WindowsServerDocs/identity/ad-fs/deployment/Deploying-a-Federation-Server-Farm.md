---
ms.assetid: bbb5b68f-00ad-4715-8176-0c2769b706c4
title: Руководство по развертыванию служб федерации Active Directory в Windows Server 2012 R2
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: e5507cd567114d17c6500655ee210b70bd9ea1ec
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71408419"
---
# <a name="deploying-a-federation-server-farm"></a>Развертывание фермы серверов федерации


Для развертывания фермы серверов федерации выполните задачи из этого контрольного списка в указанном порядке. В случае перехода по ссылке в раздел общих понятий вернитесь после его просмотра в данный контрольный список, чтобы продолжить выполнение оставшихся задач в контрольном списке.  
  
Контрольный список ![развертывания фермы федеративных серверов](media/2b05dce3-938f-4168-9b8f-1f4398cbdb9b.gif)**: развертывание фермы серверов федерации**  
  
||Задача|Справочные материалы|  
|-|--------|-------------|  
|![Развертывание федеративной фермы серверов](media/icon_checkboxo.gif)|Изучите важные понятия и рекомендации по мере подготовки к развертыванию службы федерации Active Directory (AD FS) \(AD FS\). **Примечание.**|![развертывание фермы федеративных серверов](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[AD FS руководство по проектированию в Windows server 2012 R2](../../ad-fs/design/AD-FS-Design-Guide-in-Windows-Server-2012-R2.md)<br /><br />![развертывание фермы федеративных серверов](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Общие сведения о ключевых AD FS основных понятиях](../../ad-fs/technical-reference/Understanding-Key-AD-FS-Concepts.md)|  
||Если вы решили использовать Microsoft SQL Server для хранилища конфигурации AD FS, убедитесь, что развернут функциональный экземпляр SQL Server.|Предупреждение [SQL Server](https://technet.microsoft.com/sqlserver) **.** в Windows Server 2012 R2 если вы хотите создать ферму AD FS и использовать SQL Server для хранения данных конфигурации, можно использовать SQL Server 2008 и более новые версии, включая SQL Server 2012.|  
|![Развертывание федеративной фермы серверов](media/icon_checkboxo.gif)|Присоедините компьютер к домену Active Directory.|![развертывание фермы федеративных серверов](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Присоединение компьютера к домену](Join-a-Computer-to-a-Domain.md)|  
|![Развертывание федеративной фермы серверов](media/icon_checkboxo.gif)|Зарегистрируйте безопасный уровень сокета \(сертификат SSL\) для AD FS.|![развертывании федеративной фермы серверов](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[зарегистрируйте SSL-сертификат для AD FS](Enroll-an-SSL-Certificate-for-AD-FS.md)|  
|![Развертывание федеративной фермы серверов](media/icon_checkboxo.gif)|Установите службу роли AD FS.|![развертывании федеративной фермы серверов](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[установите службу роли AD FS](Install-the-AD-FS-Role-Service.md)|  
|![Развертывание федеративной фермы серверов](media/icon_checkboxo.gif)|Настройте сервер федерации.|![развертывание фермы федеративных серверов](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[Настройка сервера федерации](Configure-a-Federation-Server.md)|  
|![Развертывание федеративной фермы серверов](media/icon_checkboxo.gif)|Необязательный шаг: Настройка сервера федерации с помощью службы регистрации устройств \(DRS\).|![развертывание федеративной фермы серверов](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Настройка сервера федерации с помощью службы регистрации устройств](Configure-a-federation-server-with-Device-Registration-Service.md)|  
|![Развертывание федеративной фермы серверов](media/icon_checkboxo.gif)|Добавьте узел \(\) и псевдоним \(запись ресурса CNAME\) в корпоративную систему доменных имен \(DNS\) для службы федерации и DRS.|![развертывании федеративной фермы серверов](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Настройте корпоративные DNS для служба Федерации и DRS](Configure-Corporate-DNS-for-the-Federation-Service-and-DRS.md)|  
|![Развертывание федеративной фермы серверов](media/icon_checkboxo.gif)|Проверьте работоспособность сервера федерации.|![развертывании федеративной фермы серверов](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Убедитесь, что сервер федерации работает](Verify-That-a-Federation-Server-Is-Operational.md)|  
  

## <a name="see-also"></a>См. также  
[Развертывание AD FS](../../ad-fs/AD-FS-Deployment.md)  

[Рекомендации по развертыванию AD FS Windows Server 2012 R2](../../ad-fs/deployment/Windows-Server-2012-R2-AD-FS-Deployment-Guide.md)  
  

