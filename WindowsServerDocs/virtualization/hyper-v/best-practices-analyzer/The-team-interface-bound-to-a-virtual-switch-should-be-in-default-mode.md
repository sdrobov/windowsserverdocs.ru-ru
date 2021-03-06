---
title: Интерфейс команды, привязанный к виртуальному коммутатору, должен быть в режиме по умолчанию
description: Интернет-версия текста для этого правила анализатор соответствия рекомендациям.
ms.prod: windows-server
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: 8c118e1e-865f-4cff-acdc-7c35e45d5da9
author: kbdazure
ms.date: 8/16/2016
ms.openlocfilehash: fe19de5dd380d08c01c917da9d4e2ef9465de042
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80854607"
---
# <a name="the-team-interface-bound-to-a-virtual-switch-should-be-in-default-mode"></a>Интерфейс команды, привязанный к виртуальному коммутатору, должен быть в режиме по умолчанию

>Область применения: Windows Server 2016

Дополнительные сведения о рекомендациях и проверках см. в разделе [запуска наиболее проверок анализатором соответствия рекомендациям и Управление результатами проверок](https://go.microsoft.com/fwlink/p/?LinkID=223177).  
  
|Свойство|Подробности|  
|-|-|  
|**Операционная система**|Windows Server 2016|  
|**Продукт или функция**|Hyper-V|  
|**Серьезности**|Предупреждение|  
|**Категория**|Конфигурация|  
  
В следующих разделах курсив указывает текст пользовательского Интерфейса, который отображается в анализатор соответствия рекомендациям для этой проблемы.  
  
## <a name="issue"></a>**Проблема**  
*Некоторые виртуальные коммутаторы привязаны к командному интерфейсу, но интерфейс группы не передает трафик на все виртуальные ЛС виртуальным коммутаторам.*  
  
## <a name="impact"></a>**Благоприятн**  
*Следующие виртуальные коммутаторы не могут иметь доступ ко всем виртуальным ЛС: \n{0}*  
  
## <a name="resolution"></a>**Решение**  
*Используйте диспетчер сервера или командлет Windows PowerShell Set-Нетлбфотеамник, чтобы сбросить интерфейс группы в режим по умолчанию.*  
  


