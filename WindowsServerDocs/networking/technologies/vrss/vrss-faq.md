---
title: vRSS вопросы и ответы
description: В этом разделе вы обнаружить некоторые часто задаваемые вопросы и ответы об использовании vRSS.
ms.prod: windows-server-threshold
ms.technology: networking
ms.topic: article
ms.assetid: 61ae242e-82a8-430d-b07d-52b86c01e686
ms.localizationpriority: medium
manager: dougkim
ms.date: 09/05/2018
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 3fafe6c39285e65a9d39a76cc6b652dac5c3efbd
ms.sourcegitcommit: e84e328c13a701e8039b16a4824a6e58a6e59b0b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2018
ms.locfileid: "4133820"
---
# vRSS вопросы и ответы

В этом разделе вы обнаружить некоторые часто задаваемые вопросы и ответы об использовании vRSS.

## Каковы требования к физическим сетевым адаптерам, использующие с vRSS?

Сетевые адаптеры должны быть совместимы с \(VMQ\) очереди виртуальной машины и должны быть скорость каналов 10 Гбит/с или более.

Дополнительные сведения см. в разделе [Планирование использования vRSS](vrss-plan.md).

## VRSS работает с ядер процессора коммутатор Hyper потокового?

Нет. VRSS и VMQ игнорировать коммутатор Hyper потокового его ядер.

## Работает ли vRSS для \(vNICs\) виртуальные сетевые карты узла?

Да. Используйте параметр **- ManagementOS** вместо \(VM\) имя виртуальной машины на команду **Set-VMNetworkAdapter** Windows PowerShell и **Включить NetAdapterRss** на сетевой адаптер узла.

Дополнительные сведения см. в разделе [Команды Windows PowerShell для RSS-Каналов и vRSS](vrss-wps.md).

## Количество логических процессоров виртуальную Машину требуется использовать vRSS?

Виртуальные машины должны двух или нескольких логических процессоров \(LPs\) иметь возможность использовать vRSS.

Дополнительные сведения см. в разделе [Планирование использования vRSS](vrss-plan.md).

## VRSS совместим с объединение Сетевых карт?

Да. Если вы используете объединение Сетевых карт, очень важно правильно настроить VMQ для работы с параметрами объединение Сетевых карт. Подробные сведения о объединение Сетевых карт развертывание и управление ими см. в разделе [Объединение Сетевых карт](https://docs.microsoft.com/windows-server/networking/technologies/nic-teaming/nic-teaming).

## vRSS включена, но как узнать, если он работает? 

Вы сможете сообщить, что vRSS работает, открыв диспетчера задач в своей виртуальной Машины и просмотр использования виртуального процессора. При наличии нескольких подключений к виртуальной Машине, вы увидите несколько основных выше 0% использования.

Из-за один сеанс TCP не может быть сбалансирована между несколькими логическими ядрами процессора, виртуальные Машины должны получение нескольких TCP сеансов, прежде чем вы заметили, работает ли vRSS.

Если виртуальная машина получает несколько сеансов TCP, но вы не видите несколько основных LP выше 0% использования, убедитесь, что вы выполнили все шаги подготовки из раздела, [Планирование использования vRSS](vrss-plan.md).

## Я смотрит на узле и не все процессоры используются. Выглядит так, будто каждые других один будет пропущен.
  
Проверьте, включен ли hyper потоков. VMQ и vRSS предназначены для пропуска коммутатор Hyper потокового ядер.

## Существуют различные команды Windows PowerShell для RSS-Каналов и vRSS?

Да и нет. Хотя использовать те же команды для RSS в собственных узлов и RSS на виртуальных машинах, vRSS также требует VMQ для включения на физический сетевой Адаптер - и для виртуальной Машины и vRSS необходимо включить порт коммутатора.

Дополнительные сведения см. в разделе [Команды Windows PowerShell для RSS-Каналов и vRSS](vrss-wps.md).

---