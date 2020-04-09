---
title: Избегайте установки RemoteFX на компьютере, который настроен в качестве контроллера домена Active Directory
description: Интернет-версия текста для этого правила анализатор соответствия рекомендациям.
ms.prod: windows-server
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: da58694e-91f6-45d8-a599-18966db165f4
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: 597dd26d0a317ca026cd94ab29138ce679d7c3b9
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80857767"
---
# <a name="avoid-installing-remotefx-on-a-computer-that-is-configured-as-an-active-directory-domain-controller"></a>Избегайте установки RemoteFX на компьютере, который настроен в качестве контроллера домена Active Directory

>Область применения: Windows Server 2016

Дополнительные сведения о рекомендациях и проверках см. в разделе [запуска наиболее проверок анализатором соответствия рекомендациям и Управление результатами проверок](https://go.microsoft.com/fwlink/p/?LinkID=223177).  
  
|Свойство|Подробности|  
|-|-|  
|**Операционная система**|Windows Server 2016|  
|**Продукт или функция**|Hyper-V|  
|**Серьезности**|Ошибка|  
|**Категория**|Конфигурация|  
  
В следующих разделах курсив указывает текст пользовательского Интерфейса, который отображается в анализатор соответствия рекомендациям для этой проблемы.  
  
## <a name="issue"></a>**Проблема**  
*RemoteFX устанавливается на контроллере домена.*  
  
## <a name="impact"></a>**Благоприятн**  
*Виртуальные компьютеры, настроенные для RemoteFX, не могут использоваться на этих компьютерах.*  
  
## <a name="resolution"></a>**Решение**  
*Решите, следует ли настроить этот сервер с помощью RemoteFX для Hyper-V или в качестве контроллера домен Active Directory, а затем при необходимости перенастройте сервер.*  
  


