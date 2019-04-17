---
ms.assetid: 4ae26970-e42e-4e69-887a-b16d2f8d0695
title: "Настройка клиентских компьютеров на доверие серверу федерации по учетной записи"
description: 
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: bdfb086c8177e72c074ac5b5b1a38aac49c4082c
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="configure-client-computers-to-trust-the-account-federation-server"></a>Настройка клиентских компьютеров на доверие серверу федерации по учетной записи

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Чтобы клиентские компьютеры успешно можно получить доступ к федеративным приложениям с помощью служб федерации Active Directory \(AD FS\), сначала необходимо настроить параметры Internet Explorer на каждом клиентском компьютере, чтобы браузер отношения доверия сервера федерации учетных записей. Можно этого вручную или с помощью групповой политики, в зависимости от настройку администрирования, выполнив одну из следующих процедур.  
  
## <a name="configuring-internet-explorer-settings-manually"></a>Настройка параметров Internet Explorer вручную  
Вручную настроить параметры Internet Explorer каждого пользователя на поддержку федерации через AD FS можно использовать следующую процедуру. Если нескольким пользователям использовать один компьютер, выполните эту процедуру несколько раз — один раз для каждого профиля пользователя.  
  
Для выполнения этой процедуры, войдите как пользователь, который будет осуществлять доступ к федеративным приложениям. Это параметр конкретного profile\. Таким образом необходимо вручную добавлять этот параметр для каждого профиля, который существует на определенном компьютере.  
  
#### <a name="to-manually-configure-client-computers-to-trust-the-account-federation-server"></a>Ручная настройка клиентских компьютеров доверия сервера федерации учетных записей  
  
1.  На клиентском компьютере запустите Internet Explorer.  
  
2.  На **средства** меню, нажмите кнопку **обозревателя**.  
  
3.  На **безопасности** щелкните **местной интрасети** , а затем **сайты**.  
  
4.  Нажмите кнопку **Дополнительно**и в **добавьте этот веб-сайт в зону**, введите полное имя доменных имен \(DNS\) сервер федерации учетных записей \ (например, https:\/\/fs1.fabrikam.com\), а затем нажмите кнопку **добавить**.  
  
5.  Нажмите кнопку **ОК** три раза.  
  
## <a name="configuring-internet-explorer-settings-by-using-group-policy"></a>Настройка параметров Internet Explorer с помощью групповой политики  
В большинстве случаев рекомендуется использовать групповую политику для отправки соответствующие параметры Internet Explorer на каждом клиентском компьютере.  
  
Членство в группе **"Администраторы домена"** или **"Администраторы предприятия"**, или в эквивалентной в доменных службах Active Directory \(AD DS\) минимальным требованием для выполнения этой процедуры.  Подробные сведения об использовании соответствующих учетных записей и членстве в группах в [локальные и доменные группы по умолчанию](https://go.microsoft.com/fwlink/?LinkId=83477) \ (http:///\/ go.microsoft.com\/fwlink\ /? LinkId\ = 83477\).   
  
#### <a name="to-configure-client-computers-to-trust-the-account-federation-server-by-using-group-policy"></a>Для настройки клиентских компьютеров доверия сервера федерации учетных записей с помощью групповой политики  
  
1.  На контроллере домена в лесу организации партнера по учетным записям запуска **Управление групповой политикой** оснастка.  
  
2.  Найти соответствующие \(GPO\) объекта групповой политики, щелкните правой кнопкой мыши, а затем щелкните **изменить**.  
  
3.  В дереве консоли откройте **Configuration\\Preferences\\Windows Settings\\Internet Explorer обслуживание**, а затем нажмите кнопку **безопасности**.  
  
4.  В области сведений щелкните двойном щелчке **зоны безопасности и оценка содержимого**.  
  
5.  В разделе **зоны безопасности и конфиденциальность**, нажмите кнопку **импортировать текущие безопасности и параметры конфиденциальности**, а затем нажмите кнопку **изменить параметры**.  
  
6.  Нажмите кнопку **местной интрасети**, а затем нажмите кнопку **сайты**.  
  
7.  В **добавьте этот веб-сайт в зону**, введите полное DNS-имя сервера федерации учетных записей \ (например, https:\/\/fs1.fabrikam.com\), нажмите кнопку **добавить**, а затем нажмите кнопку **закрыть**.  
  
8.  Нажмите кнопку **ОК** два раза, чтобы применить эти изменения групповой политики.  
  