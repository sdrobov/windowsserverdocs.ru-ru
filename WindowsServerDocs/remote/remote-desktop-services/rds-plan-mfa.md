---
title: 'Службы удаленных рабочих столов: Многофакторная идентификация'
description: Сведения о планировании использования MFA в RDS.
ms.prod: windows-server
ms.technology: remote-desktop-services
ms.topic: article
ms.assetid: 09ea784e-5644-417a-a3d9-bdbcebc313f9
author: lizap
ms.author: elizapo
ms.date: 09/07/2016
manager: dongill
ms.openlocfilehash: c46ad24c62510b4a100a89b5c10a8f52c1a66151
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80857357"
---
# <a name="remote-desktop-services---multi-factor-authentication"></a>Службы удаленных рабочих столов: Многофакторная идентификация

>Применяется к: Windows Server (Semi-Annual Channel), Windows Server 2019, Windows Server 2016

Воспользуйтесь преимуществами Active Directory с Многофакторной идентификацией, чтобы обеспечить высокий уровень защиты своих коммерческих ресурсов.

Взаимодействие пользователей со своими рабочими столами и приложениями будет осуществляться практически так же, как и ранее, когда они проходили дополнительный этап аутентификации для подключения к нужному ресурсу.
- Запустите рабочий стол или удаленное приложение RemoteApp из RDP-файла или через клиентское приложение удаленного рабочего стола.
- При подключении к шлюзу удаленных рабочих столов для защиты удаленного доступа вы получите SMS или запрос защиты в мобильном приложении MFA.
- Правильно пройдите аутентификацию и подключитесь к ресурсу!

Дополнительные сведения о процессе настройки можно найти в разделе [Интеграция инфраструктуры шлюза удаленных рабочих столов с помощью расширения сервера политики сети (NPS) и Azure AD](https://docs.microsoft.com/azure/multi-factor-authentication/nps-extension-remote-desktop-gateway).
