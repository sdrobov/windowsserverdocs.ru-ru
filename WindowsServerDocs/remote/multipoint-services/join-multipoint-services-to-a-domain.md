---
title: Присоединение MultiPoint Services к домену (необязательно)
Description: Предоставляет инструкции по присоединению к домену MultiPoint Services
ms.custom: na
ms.date: 07/22/2016
ms.prod: windows-server-threshold
ms.technology: multipoint-services
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 623b7c21-dcbb-402e-8b5a-8e434cd225bd
author: evaseydl
manager: scottman
ms.author: evas
ms.openlocfilehash: af5dd1f16e011161bbcf72c21c21088721ac1243
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59827045"
---
# <a name="join-the-multipoint-services-computer-to-a-domain-optional"></a>Присоединяйтесь к компьютеру MultiPoint Services к домену (необязательно)
Если будет доступ к компьютеру MultiPoint Services через домен Active Directory, следующим шагом является для добавления компьютера к домену.  
  
> [!IMPORTANT]  
> Прежде чем присоединить компьютер к домену, необходимо проверить ваш часовой пояс. Инструкции см. в разделе [задать дату, время и часовой пояс](Set-the-date--time--and-time-zone.md).  
   
1.  На **начальном экране** откройте **Панель управления**. Нажмите кнопку **система и безопасность**, а затем нажмите кнопку **системы**.  
  
2.  В разделе **Имя компьютера, имя домена и параметры рабочей группы**нажмите кнопку **Изменить параметры**.  
  
3.  На **имя_компьютера** щелкните **изменение**.  
  
4.  В **изменение имени компьютера или домена** выберите **домена**, введите имя домена и нажмите кнопку **ОК**, а затем следуйте указаниям мастера, чтобы завершить процесс.  
  
5.  После перезагрузки компьютера войдите в систему как администратор и дождитесь MultiPoint Manager открыть.  
  
> [!IMPORTANT]  
> Чтобы убедиться, что среда домена MultiPoint Services работает правильно, необходимо настроить ряд групповые политики и обновить реестр. Сведения см. в разделе [Настройка групповых политик для развертывания домена](https://technet.microsoft.com/library/dn265982.aspx).  