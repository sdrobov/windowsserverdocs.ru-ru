---
ms.assetid: cc2834ec-8f66-4209-aba3-402d710cd1bd
title: Расположение контроллера домена
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: 2b76f3fcad72c875a83f00e6ade37cfeb5675bf9
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80822527"
---
# <a name="domain-controller-location"></a>Расположение контроллера домена

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Клиенты используют службу доменных имен (DNS) для поиска контроллеров домена для выполнения таких операций, как обработка запросов на вход в систему или поиск опубликованных ресурсов в каталоге. Контроллеры домена регистрируют различные записи в DNS, чтобы помочь клиентам и другим компьютерам их размещать. Эти записи в совокупности называются записями локатора.  
  
Контроллеры домена также используют DNS для размещения других контроллеров домена и выполнения таких задач, как репликация. Процесс, с помощью которого контроллеры домена находят другие контроллеры домена, совпадает с процессом, с помощью которого клиенты находят контроллеры домена.  
  


