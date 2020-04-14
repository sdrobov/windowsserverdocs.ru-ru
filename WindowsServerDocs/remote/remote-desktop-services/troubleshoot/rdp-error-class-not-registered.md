---
title: Клиенты не могут подключиться и получают сообщение об ошибке "Класс не зарегистрирован"
description: Узнайте, как устранить ошибку "Класс не зарегистрирован", возникающую при подключении к удаленному рабочему столу.
ms.reviewer: rklemen
ms.topic: troubleshooting
author: kaushika-msft
manager: dcscontentpm
ms.author: delhan
ms.date: 07/24/2019
ms.localizationpriority: medium
ms.openlocfilehash: 52e696bd4229b947ea63a379211192b8664a9f93
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80857187"
---
# <a name="clients-cant-connect-and-get-the-class-not-registered-error"></a>Клиенты не могут подключиться и получают сообщение об ошибке "Класс не зарегистрирован"

Когда вы пытаетесь подключиться к удаленному компьютеру с помощью клиента под управлением Windows 10 версии после 1709, клиент не сможет подключиться. Сервер узла сеансов Удаленных рабочих столов (RDSH) выдаст сообщение, содержащее код ошибки 0x80040154 (Класс не зарегистрирован).

Такая проблема возникает, если пользователь, который пытается подключиться, использует обязательный профиль пользователя. Чтобы устранить эту проблему, установите обновление Windows 10 [за 24 июля 2018 г. — KB4338817 (ОС сборки 16299.579)](https://support.microsoft.com/help/4338817/windows-10-update-kb4338817).
