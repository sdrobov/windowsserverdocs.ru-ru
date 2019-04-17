---
ms.assetid: aca4a4fa-b12c-4eed-a499-f9aedb7d2fd6
title: "Настройка корпоративной системы DNS для службы федерации и DRS"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 9b66bed99cbc2ac2cdf116579adaea282c45fabe
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="configure-corporate-dns-for-the-federation-service-and-drs"></a>Настройка корпоративной системы DNS для службы федерации и DRS

>Область применения: Windows Server 2016, Windows Server 2012 R2
  
## <a name="step-6-add-a-host-a-and-alias-cname-resource-record-to-corporate-dns-for-the-federation-service-and-drs"></a>Шаг 6: Добавление узла \(A\) и псевдоним записи ресурса \(CNAME\) в корпоративную систему DNS для службы федерации и DRS  
Необходимо добавить следующие записи ресурсов в корпоративной системе доменных имен \(DNS\) для вашей службы федерации и службы регистрации устройств, настроенная в предыдущих шагах.  
  
|Запись|Тип|Адрес|  
|---------|--------|-----------|  
|federation\_service\_name|Размещения \(A\)|IP-адрес сервера AD FS или IP-адрес подсистемы балансировки нагрузки, настроенный перед фермы серверов AD FS|  
|enterpriseregistration|Псевдоним \(CNAME\)|federation\_server\_name.contoso.com|  
  
Добавление \(A\) и псевдоним \(CNAME\) записи ресурсов узла в корпоративную службу DNS для сервера федерации и службы регистрации устройств можно использовать следующую процедуру.  
  
Членство в группе **Администраторы**, или в эквивалентной минимальным требованием для выполнения этой процедуры.  Подробные сведения об использовании соответствующих учетных записей и членстве в группах в [локальные и доменные группы по умолчанию ](https://go.microsoft.com/fwlink/?LinkId=83477).   
  
#### <a name="to-add-a-host-a-and-alias-cname-resource-records-to-dns-for-your-federation-server"></a>Чтобы добавить \(A\) и псевдоним \(CNAME\) записи ресурсов узла в DNS для сервера федерации  
  
1.  На вы контроллере домена, в диспетчере сервера на **средства** меню, нажмите кнопку **DNS** чтобы открыть DNS оснастка.  
  
2.  В дереве консоли разверните узел **domain\_controller\_name** узел, разверните **зоны прямого просмотра**, щелкните правой кнопкой мыши **domain\_name**, а затем нажмите кнопку **новый узел \(A or AAAA\)**.  
  
3.  В **имя** введите имя фермы AD FS.  
  
4.  В **IP-адрес** введите IP-адрес сервера федерации. Нажмите кнопку **добавления узла**.  
  
5.  Щелкните правой кнопкой мыши **domain\_name** узел, а затем нажмите кнопку **\(CNAME\) новый псевдоним**.  
  
6.  В **новую запись ресурса** диалоговое окно, введите **enterpriseregistration** в **псевдоним** поле.  
  
7.  В полное доменное имя \(FQDN\) из целевого узла введите **federation\_service\_farm\_name.domain\_name.com**, а затем нажмите кнопку **ОК**.  
  
    > [!IMPORTANT]  
    > В реальном мире развертывании Если у компании несколько суффиксов имени участника-пользователя \(UPN\), необходимо создать несколько записей CNAME для каждого из этих суффиксов в DNS.  
  
## <a name="see-also"></a>См. также: 

[Развертывание AD FS](../../ad-fs/AD-FS-Deployment.md)  

[Руководство по развертыванию Windows Server 2012 R2 AD FS](../../ad-fs/deployment/Windows-Server-2012-R2-AD-FS-Deployment-Guide.md)  
 
[Развертывание фермы серверов федерации](../../ad-fs/deployment/Deploying-a-Federation-Server-Farm.md)  
  

