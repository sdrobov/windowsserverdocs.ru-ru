---
ms.assetid: cc2834ec-8f66-4209-aba3-402d710cd1bd
title: Расположение контроллера домена
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: 48ea357b952738c63274d194b4a5aa5d4adcb3d8
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71408848"
---
# <a name="domain-controller-location"></a>Расположение контроллера домена

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Клиенты используют службу доменных имен (DNS) для поиска контроллеров домена для выполнения таких операций, как обработка запросов на вход в систему или поиск опубликованных ресурсов в каталоге. Контроллеры домена регистрируют различные записи в DNS, чтобы помочь клиентам и другим компьютерам их размещать. Эти записи в совокупности называются записями локатора.  
  
Контроллеры домена также используют DNS для размещения других контроллеров домена и выполнения таких задач, как репликация. Процесс, с помощью которого контроллеры домена находят другие контроллеры домена, совпадает с процессом, с помощью которого клиенты находят контроллеры домена.  
  


