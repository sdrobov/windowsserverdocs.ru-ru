---
title: Конфигурация PVLAN на виртуальном коммутаторе должна быть постоянной
description: Интернет-версия текста для этого правила анализатор соответствия рекомендациям.
ms.prod: windows-server
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: 4db63bcc-7a54-4f19-98a6-c274c3956d51
author: KBDAzure
ms.date: 8/16/2016
ms.openlocfilehash: 36616a5c4d8e57ae929cdab846db65dcdda57b85
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71364749"
---
# <a name="pvlan-configuration-on-a-virtual-switch-must-be-consistent"></a>Конфигурация PVLAN на виртуальном коммутаторе должна быть постоянной

>Область применения. Windows Server 2016

Дополнительные сведения о рекомендациях и проверках см. в разделе [запуска наиболее проверок анализатором соответствия рекомендациям и Управление результатами проверок](https://go.microsoft.com/fwlink/p/?LinkID=223177).  
  
|Свойство|Подробности|  
|-|-|  
|**Операционная система**|Windows Server 2016| 
|**Продукт или функция**|Hyper-V|  
|**Серьезности**|Ошибка|  
|**Категория**|Конфигурация|  
  
В следующих разделах курсив указывает текст пользовательского Интерфейса, который отображается в анализатор соответствия рекомендациям для этой проблемы.
  
## <a name="issue"></a>**Проблема**  
*Частная виртуальная локальная сеть (PVLAN) неправильно настроена на одном или нескольких виртуальных сетевых адаптерах.*  
  
## <a name="impact"></a>**Благоприятн**  
*PVLAN может не изолировать сетевой трафик между виртуальными машинами правильно.*  
  
## <a name="resolution"></a>**Решение**  
*Чтобы правильно настроить PVLAN, используйте командлет Windows PowerShell Set-Вмнетворкадаптервлан.*  
  


