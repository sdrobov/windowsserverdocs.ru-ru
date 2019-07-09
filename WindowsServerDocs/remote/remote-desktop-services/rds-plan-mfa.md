---
title: 'Службы удаленных рабочих столов: Многофакторная идентификация'
description: Сведения о планировании использования MFA в RDS.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: remote-desktop-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 09ea784e-5644-417a-a3d9-bdbcebc313f9
author: lizap
ms.author: elizapo
ms.date: 09/07/2016
manager: dongill
ms.openlocfilehash: 5ca2a29b0287dbd940afeb4404a85f1d978447f9
ms.sourcegitcommit: 3743cf691a984e1d140a04d50924a3a0a19c3e5c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2019
ms.locfileid: "66805112"
---
# <a name="remote-desktop-services---multi-factor-authentication"></a>Службы удаленных рабочих столов: Многофакторная идентификация

>Относится к: Windows Server (Semi-Annual Channel), Windows Server 2019, Windows Server 2016

Воспользуйтесь преимуществами Active Directory с Многофакторной идентификацией, чтобы обеспечить высокий уровень защиты своих коммерческих ресурсов.

Взаимодействие пользователей со своими рабочими столами и приложениями будет осуществляться практически так же, как и ранее, когда они проходили дополнительный этап аутентификации для подключения к нужному ресурсу.
- Запустите рабочий стол или удаленное приложение RemoteApp из RDP-файла или через клиентское приложение удаленного рабочего стола.
- При подключении к шлюзу удаленных рабочих столов для защиты удаленного доступа вы получите SMS или запрос защиты в мобильном приложении MFA.
- Правильно пройдите аутентификацию и подключитесь к ресурсу!

Дополнительные сведения о процессе настройки можно найти в разделе [Интеграция инфраструктуры шлюза удаленных рабочих столов с помощью расширения сервера политики сети (NPS) и Azure AD](https://docs.microsoft.com/azure/multi-factor-authentication/nps-extension-remote-desktop-gateway).
