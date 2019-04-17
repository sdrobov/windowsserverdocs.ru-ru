---
title: "Обзор управления учетными записями пользователей"
description: "Безопасность Windows Server"
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: security-tpm
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1b7a39cd-fc10-4408-befd-4b2c45806732
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/12/2016
ms.openlocfilehash: 90ce72cb3d1850563d16a12d09a6872d107c0690
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="user-account-control-overview"></a>Обзор управления учетными записями пользователей
\(UAC\) контроля учетных записей пользователей является фундаментальной составной частью общей концепции безопасности Майкрософт.  Контроль учетных Записей помогает уменьшить влияние вредоносных программ.

## <a name="BKMK_OVER"></a>Описание компонентов
UAC позволяет всем пользователям для входа на свой компьютер, используя учетную запись обычного пользователя. Процессы, запущенные с использованием токена обычного пользователя, могут выполнять задачи, используя предоставленные обычному пользователю права доступа. Например проводник Windows автоматически наследует разрешения уровня обычного пользователя. Кроме того, все программы, которые выполняются с помощью проводника Windows \ (например, щелкнув двойные shortcut\ приложения) также запускать со стандартным набором разрешений пользователя. Многие приложения, включая те, которые входят в состав операционной системы, предназначены для правильной работы таким образом.

Другие приложения, особенно тех, которые не были специально разработаны с параметрами безопасности уделялось, часто требуют дополнительных разрешений для успешного выполнения. Эти типы программ называются приложений прежних версий. Кроме того действия, например установка нового по и внесение изменений конфигурации для программ, таких как брандмауэр Windows, требуют более широких разрешений, нежели доступные учетной записи обычного пользователя.

Если приложения необходимо запустить с правами более обычного пользователя, UAC может назначить дополнительных групп пользователей в токен. Это позволяет пользователю явно контролировать программ, которые вносят изменения на уровне системы для компьютера или устройства.

## <a name="BKMK_APP"></a>Практическое применение
Режим одобрения администратором в UAC позволяет предотвратить автоматическую установку без ведома администратора вредоносных программ. Он также помогает защитить от случайного изменения записи во всей. И, наконец его можно использовать для принудительного обеспечения более высокого уровня соответствия требованиям, где администраторы должны активно согласие или учетные данные для каждого административного действия.


