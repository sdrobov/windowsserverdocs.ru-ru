---
title: Протокол DHCP
description: В этом разделе содержится краткий обзор протокола DHCP в Windows Server 2016.
manager: brianlic
ms.prod: windows-server
ms.technology: networking-dhcp
ms.topic: article
ms.assetid: 0ff29ef3-c458-4432-9065-e50a7de5b4b9
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 5fc44d0f58ed73ff48f530bad3206baa675d9ac9
ms.sourcegitcommit: da7b9bce1eba369bcd156639276f6899714e279f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2020
ms.locfileid: "80312523"
---
# <a name="dynamic-host-configuration-protocol-dhcp"></a>Протокол DHCP

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

Этот раздел можно использовать для краткого обзора DHCP в Windows Server 2016.

> [!NOTE]
> Помимо этого раздела, доступна следующая документация по DHCP.
>
> - [Новые возможности DHCP](What-s-New-in-DHCP.md)
> - [Развертывание DHCP с помощью Windows PowerShell](dhcp-deploy-wps.md)

Протокол DHCP — это протокол клиента или сервера, который автоматически предоставляет узел протокола IP с его IP-адресом и другие связанные сведения о конфигурации, такие как маска подсети и шлюз по умолчанию. RFC 2131 и 2132 определяют протокол DHCP в качестве стандарта Internet Engineering Task Force (IETF), основанного на протоколе начальной загрузки (BOOTP), протокола, с помощью которого DHCP предоставляет много сведений о реализации. DHCP позволяет узлам получать необходимые сведения о конфигурации TCP/IP от DHCP-сервера.

Windows Server 2016 включает DHCP-сервер, который является необязательной ролью сервера сети, которую можно развернуть в сети для аренды IP-адресов и других сведений клиентам DHCP. Все клиентские операционные системы на основе Windows включают DHCP-клиент как часть TCP/IP, а DHCP-клиент включен по умолчанию.

## <a name="why-use-dhcp"></a>Зачем использовать DHCP?

Каждое устройство в сети на основе TCP/IP должно иметь уникальный IP-адрес одноадресной рассылки для доступа к сети и ее ресурсам. Без DHCP IP-адреса новых компьютеров или компьютеров, перемещаемых из одной подсети в другую, необходимо настроить вручную. IP-адреса для компьютеров, удаленных из сети, необходимо вручную освободить.

При использовании DHCP весь процесс автоматизирован и управляется централизованно. DHCP-сервер поддерживает пул IP-адресов и арендованный адрес любому клиенту с поддержкой DHCP при запуске в сети. Так как IP-адреса являются динамическими (арендованными), а не статическими (без постоянного назначения), адреса, которые больше не используются, автоматически возвращаются в пул для перераспределения.

Сетевой администратор устанавливает DHCP-серверы, которые сохраняют информацию о конфигурации TCP/IP и предоставляют клиентам с поддержкой DHCP в виде предложения аренды. DHCP-сервер хранит сведения о конфигурации в базе данных, которая включает в себя:

- Допустимые параметры конфигурации TCP/IP для всех клиентов в сети.

- Допустимые IP-адреса, поддерживаемые в пуле для назначения клиентам, а также исключенные адреса.

- Зарезервированный IP-адрес адреса, связанные с конкретными клиентами DHCP. Это обеспечивает единообразное назначение одного IP-адреса одному клиенту DHCP.

- Срок действия аренды или период времени, в течение которого IP-адрес может быть использован до продления срока аренды.

Клиент с поддержкой DHCP при принятии предложения аренды получает:

- Допустимый IP-адрес для подсети, к которой подключается.  
  
- Запрошенные параметры DHCP, которые являются дополнительными параметрами, настроенными DHCP-сервером для назначения клиентам. Некоторые примеры параметров DHCP: маршрутизатор (шлюз по умолчанию), DNS-серверы и доменное имя DNS.

## <a name="benefits-of-dhcp"></a>Преимущества DHCP

DHCP предоставляет следующие преимущества.

- **Конфигурация надежных IP-адресов**. DHCP свертывает ошибки конфигурации, вызванные ручной конфигурацией IP-адресов, например типографскими ошибками, или конфликты адресов, вызванные назначением IP-адреса более чем одному компьютеру одновременно.

- **Сокращенное администрирование сети**. Служба DHCP включает следующие функции для сокращения сетевого администрирования:

    - Централизованная и автоматизированная конфигурация TCP/IP.

    - Возможность определять конфигурации TCP/IP из центрального расположения.

    - Возможность назначать полный диапазон дополнительных значений конфигурации TCP/IP с помощью параметров DHCP.

    - Эффективная обработка изменений IP-адресов для клиентов, которые должны обновляться часто, например для портативных устройств, которые перемещаются в разные места в беспроводной сети.

    - Пересылка начальных сообщений DHCP с помощью агента ретранслятора DHCP, что устраняет необходимость в DHCP-сервере для каждой подсети.

