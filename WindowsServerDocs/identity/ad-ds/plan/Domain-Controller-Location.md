---
ms.assetid: cc2834ec-8f66-4209-aba3-402d710cd1bd
title: Расположение контроллера домена
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 6b66b224278f15b6abeecbef8fe0778a98159bb7
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59872625"
---
# <a name="domain-controller-location"></a>Расположение контроллера домена

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Клиенты используют доменных имен (DNS) для поиска контроллеров домена до завершения операций, таких как обработка запросов на вход или поиск в каталоге для опубликованных ресурсов. Контроллеры домена регистрируют широкий набор записей в DNS, чтобы помочь клиентам, и их обнаруживать другие компьютеры. Эти записи Собирательно называются записей локатора.  
  
Контроллеры домена также используют DNS для обнаружения других контроллеров домена и выполнять задачи, такие как репликация. Процесс, по которому контроллеры домена обнаружения других контроллеров домена является таким же, как процесс, по которому клиенты находить контроллеры домена.  
  


