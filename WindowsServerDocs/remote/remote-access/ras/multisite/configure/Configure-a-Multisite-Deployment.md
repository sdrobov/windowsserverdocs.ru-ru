---
title: Настройка многосайтового развертывания
description: Эта статья является частью руководств по развертыванию нескольких серверов удаленного доступа в многосайтовом развертывании в Windows Server 2016.
manager: brianlic
ms.prod: windows-server
ms.technology: networking-ras
ms.topic: article
ms.assetid: cb84920e-7cf5-4266-b071-d09e3d5e1f10
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 473d90c08e2183f32409630b698d20f79f567016
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86964596"
---
# <a name="configure-a-multisite-deployment"></a>Настройка многосайтового развертывания

>Область применения. Windows Server (Semi-Annual Channel), Windows Server 2016

 Windows Server 2016 объединяет VPN-подключение DirectAccess и службы удаленного доступа (RAS) в одну роль удаленного доступа. В этом обзоре приводятся общие сведения о шагах настройки, необходимых для развертывания одного многосайтового развертывания Windows Server 2016 или Windows Server 2012 с удаленным доступом.  
  
-   Шаг 1. [развертывание одного сервера DirectAccess с дополнительными параметрами](../../../directaccess/single-server-advanced/deploy-a-single-directaccess-server-with-advanced-settings.md). Установите и настройте отдельный сервер удаленного доступа. Для многосайтового развертывания необходимо установить один сервер перед настройкой многосайтового развертывания.  
  
-   [Шаг 2. Настройка межсайтовой инфраструктуры](Step-2-Configure-the-Multisite-Infrastructure.md). Для многосайтового развертывания необходимо настроить дополнительные Active Directory сайты и контроллеры домена. Дополнительные группы безопасности и групповая политика объекты (GPO) также необходимы, если не используются автоматически настроенные объекты групповой политики.  
  
-   [Шаг 3. Настройка многосайтового развертывания.](Step-3-Configure-the-Multisite-Deployment.md)Установка роли удаленного доступа на дополнительных серверах удаленного доступа, включение многосайтового развертывания и Настройка дополнительных серверов в качестве точек входа для развертывания.  
  
-   [Шаг 4. Проверка многосайтового развертывания](Step-4-Verify-the-Multisite-Deployment.md) 
  
