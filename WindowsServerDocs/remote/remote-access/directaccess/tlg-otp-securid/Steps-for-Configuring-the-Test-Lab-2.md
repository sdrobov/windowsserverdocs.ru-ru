---
title: Шаги по настройке лаборатории тестирования
description: Этот раздел входит руководство по лаборатории тестирования — продемонстрировать DirectAccess с проверкой подлинности OTP и RSA SecurID для Windows Server 2016
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology:
- networking-da
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0a40183c-afd1-43ca-b306-05745640a37d
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 991f06568a16f7e8bcce3bc6c86eef3467ea31e1
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59826295"
---
# <a name="steps-for-configuring-the-test-lab"></a>Шаги по настройке лаборатории тестирования

>Область применения. Windows Server (полугодовой канал), Windows Server 2016

Ниже описывается настройка инфраструктуры удаленного доступа, настройки сервера удаленного доступа и клиента и проверка подключения DirectAccess из подсетей Homenet и через Интернет.  
  
В этом руководстве вы создадите удаленного доступа с OTP среды, выполнив следующие действия:  
  
-   [ШАГ 1. Завершите настройку DirectAccess](assetId:///4dbf877f-02fb-439b-907a-f5b3f1d8afa6). Выполните все шаги в [руководство по лаборатории тестирования: Демонстрации настройки отдельного сервера DirectAccess в смешанной IPv4 и IPv6](https://go.microsoft.com/fwlink/p/?LinkId=237004).  
  
-   [ШАГ 2. Настройка APP1](assetId:///c1bb590f-91d4-4ed5-bceb-b0e36eabd4ff). Настройка APP1 с помощью шаблонов сертификатов для OTP для использования EDGE1.  
  
-   [ШАГ 3. Настройка DC1](assetId:///904a6edc-a771-45ed-9630-a34a680bb522). Убедитесь, что имя участника-пользователя, определенное на DC1.  
  
-   [ШАГ 7. Установка и настройка RSA](assetId:///baa4c28c-add7-42e2-8afd-ccc7a559406a). Установка и настройка сервера RSA, RADIUS и OTP, а также указать EDGE1 для OTP.  
  
-   [ШАГ 11. Проверьте работоспособность OTP на EDGE1](assetId:///3b397a4a-8478-47f2-a932-9e8e048c14ba). Убедитесь, что находится в состоянии OTP на сервере удаленного доступа.  
  
-   [ШАГ 8. Проверка подключения DirectAccess из подсети Homenet](assetId:///ba1652a6-0692-4add-91ca-34a84956ba14). Проверьте функциональность OTP для DirectAccess из-за устройства NAT.  
  
-   [ШАГ 10. Проверка подключения DirectAccess из Интернета](assetId:///321149eb-5f23-4a0b-b8fb-1244540126e9). Проверка подключения клиента DirectAccess из Интернета.  
  
-   [ШАГ 12. Сделайте снимок конфигурации,](assetId:///8a51ed3c-9c32-402f-85d1-617ce46845b4). После завершения лаборатории тестирования, создание снимка работу DirectAccess с OTP конфигурации, который позволит вернуться к нему позже для проверки дополнительных сценариев.  
  


