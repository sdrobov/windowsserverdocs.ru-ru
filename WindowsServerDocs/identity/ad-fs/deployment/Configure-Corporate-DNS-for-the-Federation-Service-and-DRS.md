---
ms.assetid: aca4a4fa-b12c-4eed-a499-f9aedb7d2fd6
title: Настройка корпоративной системы DNS для службы федерации и DRS
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 9f0b04f9dc050117fdefc630759c86d2b1bb1ecc
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71408446"
---
# <a name="configure-corporate-dns-for-the-federation-service-and-drs"></a>Настройка корпоративной системы DNS для службы федерации и DRS
  
## <a name="step-6-add-a-host-a-and-alias-cname-resource-record-to-corporate-dns-for-the-federation-service-and-drs"></a>Шаг 6. Добавьте узел \(A @ no__t-1 и псевдоним \(CNAME @ no__t-3 в корпоративную службу DNS для служба федерации и DRS  
Необходимо добавить следующие записи ресурсов в корпоративную систему доменных имен \(DNS @ no__t-1 для службы федерации и службы регистрации устройств, настроенной на предыдущих шагах.  
  
|Ввод|Type|Адрес|  
|---------|--------|-----------|  
|Федерация @ no__t-0service @ no__t-1name|Host \(A @ no__t-1|IP-адрес AD FS сервера или IP-адрес подсистемы балансировки нагрузки, настроенной перед фермой серверов AD FS|  
|enterpriseregistration|Alias \(CNAME @ no__t-1|Федерация @ no__t-0server\_name.contoso.com|  
  
Вы можете использовать следующую процедуру, чтобы добавить узел \(A @ no__t-1 и псевдоним \(CNAME @ no__t-3 в корпоративную службу DNS для сервера федерации и службы регистрации устройств.  
  
Членство в группах « **Администраторы**» или «эквивалентное» является минимальным требованием для выполнения этой процедуры.  Просмотрите сведения об использовании соответствующих учетных записей и членстве в группах в [локальной среде и группах домена по умолчанию](https://go.microsoft.com/fwlink/?LinkId=83477).   
  
#### <a name="to-add-a-host-a-and-alias-cname-resource-records-to-dns-for-your-federation-server"></a>Чтобы добавить узел @no__t 0A @ no__t-1 и псевдоним \(CNAME @ no__t-3 в DNS для сервера федерации  
  
1.  На контроллере домена в диспетчер сервера в меню **Сервис** щелкните **DNS** , чтобы открыть оснастку DNS Snap @ no__t-2in.  
  
2.  В дереве консоли разверните узел **domain @ no__t-1controller @ no__t-2name** , разверните узел **зоны прямого просмотра**, щелкните правой кнопкой @ no__t-4Click **домен @ no__t-6Name**, а затем выберите **создать узел \(A или AAAA @ no__t-9**.  
  
3.  В поле **имя** введите имя, которое будет использоваться для фермы AD FS.  
  
4.  В поле **IP-адрес** укажите IP-адрес сервера федерации. Нажмите кнопку **Добавить узел**.  
  
5.  Щелкните правой кнопкой @ no__t-0click узел **domain @ no__t-2name** , а затем щелкните **создать псевдоним \(CNAME @ no__t-5**.  
  
6.  В диалоговом окне **Новая запись ресурса** введите **enterpriseregistration** в поле **Имя псевдонима**.  
  
7.  В полном доменном имени \(FQDN @ no__t-1 в поле "целевой узел" введите " **Federation @ no__t-3service @ no__t-4farm @ no__t-5name. domain @ no__t-6name. com**" и нажмите кнопку " **ОК**".  
  
    > [!IMPORTANT]  
    > При развертывании в реальном мире, если в вашей компании имеется несколько суффиксов имени участника-пользователя @no__t 0UPN @ no__t-1, необходимо создать несколько записей CNAME для каждого из этих суффиксов UPN в DNS.  
  
## <a name="see-also"></a>См. также 

[Развертывание AD FS](../../ad-fs/AD-FS-Deployment.md)  

[Рекомендации по развертыванию AD FS Windows Server 2012 R2](../../ad-fs/deployment/Windows-Server-2012-R2-AD-FS-Deployment-Guide.md)  
 
[Развертывание фермы серверов федерации](../../ad-fs/deployment/Deploying-a-Federation-Server-Farm.md)  
  

