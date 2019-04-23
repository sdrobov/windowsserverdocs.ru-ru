---
title: vRSS часто задаваемые вопросы
description: В этом разделе вы найдете некоторые часто задаваемые вопросы и ответы об использовании vRSS.
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
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59840245"
---
# <a name="vrss-frequently-asked-questions"></a>vRSS часто задаваемые вопросы

В этом разделе вы найдете некоторые часто задаваемые вопросы и ответы об использовании vRSS.

## <a name="what-are-the-requirements-for-the-physical-network-adapters-that-i-use-with-vrss"></a>Каковы требования для физических сетевых адаптеров, использующих с vRSS?

Сетевые адаптеры должны быть совместимы с очередью виртуальной машины \(VMQ\) и должен иметь скорость 10 Гбит/с.

Дополнительные сведения см. в разделе [Планируйте использование vRSS](vrss-plan.md).

## <a name="does-vrss-work-with-hyper-threaded-processor-cores"></a>Работает с hyper vRSS\-ядра процессора?

Нет. VRSS и VMQ игнорировать hyper\-ядра процессора.

## <a name="does-vrss-work-for-host-virtual-nics-vnics"></a>VRSS работает для размещения виртуальных сетевых адаптеров \(виртуальных сетевых адаптеров\)?

Да. Используйте **- ManagementOS** параметр вместо виртуальной машины \(виртуальной Машины\) имя на **Set-VMNetworkAdapter** команду Windows PowerShell, и  **Enable-NetAdapterRss** на виртуальном сетевом адаптере узла.

Дополнительные сведения см. в разделе [команды Windows PowerShell для RSS и vRSS](vrss-wps.md).

## <a name="how-many-logical-processors-does-a-vm-need-to-use-vrss"></a>Количество логических процессоров виртуальной Машины нужно ли использовать vRSS?

Виртуальные машины должны два или более логических процессоров \(LPs\) чтобы иметь возможность использовать vRSS.

Дополнительные сведения см. в разделе [Планируйте использование vRSS](vrss-plan.md).

## <a name="is-vrss-compatible-with-nic-teaming"></a>VRSS совместима с объединением Сетевых карт?

Да. Если вы используете, объединение Сетевых карт, очень важно правильно настроить VMQ для работы с параметрами объединение Сетевых карт. Подробные сведения о развертывании, объединение Сетевых карт и управлении см. в разделе [объединение Сетевых карт](https://docs.microsoft.com/windows-server/networking/technologies/nic-teaming/nic-teaming).

## <a name="vrss-is-enabled-but-how-do-i-know-if-it-is-working"></a>vRSS включается, но как узнать, работает ли оно? 

Вы сможете сообщить, что vRSS работает, откройте диспетчер задач на виртуальной Машине и просмотрите об использовании виртуального процессора. Если есть несколько подключений к виртуальной Машине, вы увидите несколько ядер выше 0% использования.

Так как за один сеанс TCP не может быть сбалансирован между несколькими ядрами логического процессора, ВМ необходимо получать несколько TCP сеансы, прежде чем можно наблюдать, работает ли vRSS.

Если виртуальная машина принимает несколько сеансов TCP, но более одного ядра LP выше 0% использования не отображается, убедитесь, что выполнены все действия по подготовке в разделе [Планируйте использование vRSS](vrss-plan.md).

## <a name="im-looking-at-the-host-and-not-all-of-the-processors-are-being-used-it-looks-like-every-other-one-is-being-skipped"></a>Я просматриваю узел и вижу, что используются не все процессоры. Такое впечатление, что каждый второй пропускается.
  
Проверьте, включена ли технология Hyper-Threading. VMQ и vRSS предназначены пропускают\-ядра.

## <a name="are-there-different-windows-powershell-commands-for-rss-and-vrss"></a>Существуют разные команды Windows PowerShell для RSS и vRSS?

Да и нет. При использовании те же команды для RSS в собственном узлов и RSS на виртуальных машинах vRSS также требуется VMQ включена на физический сетевой Адаптер -, так и для виртуальной Машины и vRSS на порт коммутатора.

Дополнительные сведения см. в разделе [команды Windows PowerShell для RSS и vRSS](vrss-wps.md).

---
