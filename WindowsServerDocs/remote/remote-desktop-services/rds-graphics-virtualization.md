---
title: 'Службы удаленных рабочих столов: ускорение с помощью GPU'
description: Сведения о планировании, помогающие выбрать правильное графическое содержимое параметра виртуализации для развертывания служб удаленных рабочих столов.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: remote-desktop-services
ms.author: elizapo
ms.date: 08/21/2019
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d6ff5b22-7695-4fee-b1bd-6c9dce5bd0e8
author: lizap
manager: scottman
ms.openlocfilehash: 914994c66be0a56856ec68d08be9dc5465df015e
ms.sourcegitcommit: 81198fbf9e46830b7f77dcd345b02abb71ae0ac2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2019
ms.locfileid: "72923848"
---
# <a name="remote-desktop-services---gpu-acceleration"></a>Службы удаленных рабочих столов: ускорение с помощью GPU

Службы удаленных рабочих столов могут использовать встроенное ускорение обработки графики, а также технологии виртуализации графики, поддерживаемые Windows Server. Сведения об этих технологиях, их отличиях и способах развертывания приведены в разделе [Планирование ускорения GPU в Windows Server](../../virtualization/hyper-v/plan/plan-for-gpu-acceleration-in-windows-server.md).

При планировании ускорения обработки графики в среде RDS выбор технологии отрисовки графики будет зависеть от числа пользователей и их рабочих нагрузок.

![Рекомендации прорисовки графики — это сравнение масштабов пользователя и требования графического процессора, чтобы определить лучшую технологию графического процессора для вашей среды.](media/rds-gpu.png)
