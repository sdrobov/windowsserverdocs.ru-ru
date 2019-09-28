---
title: Шаги по настройке лаборатории тестирования
description: 'Эта статья является частью руководства по тестовой лаборатории: демонстрация DirectAccess с проверкой подлинности OTP и RSA SecurID для Windows Server 2016.'
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-da
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0a40183c-afd1-43ca-b306-05745640a37d
ms.author: pashort
author: shortpatti
ms.openlocfilehash: ef5ce37983b8565fab8287eeaae7423be0c269f6
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71404726"
---
# <a name="steps-for-configuring-the-test-lab"></a>Шаги по настройке лаборатории тестирования

>Область применения. Windows Server (Semi-Annual Channel), Windows Server 2016

Следующие шаги описывают настройку инфраструктуры удаленного доступа, настройку сервера удаленного доступа и клиента, а также проверку подключения DirectAccess из подсетей Хоменет и Интернета.  
  
В этом руководстве по тестированию вы создадите удаленный доступ с помощью среды OTP, выполнив следующие действия:  
  
-   [Шаг 1. Завершите настройку DirectAccess @ no__t-0. Выполните все действия из руководства по [Test Lab: Демонстрация установки одиночного сервера DirectAccess с смешанными IPv4 и IPv6 @ no__t-0.  
  
-   [Шаг 2. Настройте APP1 @ no__t-0. Настройте APP1 с помощью шаблонов сертификатов OTP для использования в EDGE1.  
  
-   [Шаг 3. Настройте DC1 @ no__t-0. Проверьте имя участника-пользователя, определенное на компьютере DC1.  
  
-   [Шаг 7. Установите и настройте RSA @ no__t-0. Установите и настройте RSA, сервер RADIUS и OTP и настройте EDGE1 для OTP.  
  
-   [Шаг 11. Проверьте работоспособность OTP в EDGE1 @ no__t-0. Убедитесь, что на сервере удаленного доступа установлено состояние OTP.  
  
-   [Шаг 8. Проверьте подключение DirectAccess из подсети Хоменет @ no__t-0. Протестируйте функции OTP DirectAccess из устройства NAT.  
  
-   [Шаг 10. Проверьте подключение DirectAccess из Интернета @ no__t-0. Проверьте возможность подключения клиента DirectAccess из Интернета.  
  
-   [Шаг 12. Создание моментального снимка конфигурации @ no__t-0. После завершения лаборатории тестирования сделайте снимок рабочего DirectAccess с конфигурацией OTP, чтобы можно было вернуться к нему позже для тестирования дополнительных сценариев.  
  


