---
ms.date: 01/07/2019
contributor: damaerteMSFT
author: maertendMSFT
keywords: OpenSSH, SSH, Win32-OpenSSH
title: OpenSSH в Windows
ms.product: w10
ms.openlocfilehash: 68ced1ff133495d7658e486e7e72321e18857b21
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59843365"
---
# <a name="openssh-in-windows"></a>OpenSSH в Windows

OpenSSH — это открытая версия средств Secure Shell (SSH), используемые администраторами Linux и других отличных от Windows для управления несколькими платформами удаленных систем. OpenSSH была добавлена к Windows на момент написания осени 2018 г. и входит в Windows 10 и Windows Server 2019. 

На основе архитектуры клиент сервер, где системы, в которой он работает над является клиентом и удаленной системе, управляемый — это сервер на основе SSH. OpenSSH входят различные компоненты и средства, разработанные для обеспечивают безопасный и простой подход к удаленной системе администрирования, включая:

* SSHD.exe, который является компонент сервера SSH, которая должна быть запущена в системе, удаленное управление 
* SSH.exe, который является компонентом клиента SSH, работающей на локальном компьютере пользователя
* SSH-keygen.exe создает, управляет и преобразует ключи проверки подлинности по протоколу SSH 
* SSH-agent.exe сохраняет закрытые ключи, используемые для проверки подлинности открытого ключа
* SSH-add.exe добавляет закрытые ключи в список, разрешенное сервером
* SSH-keyscan.exe помогает в сбор открытые ключи узла SSH из нескольких узлов
* SFTP.exe — это служба, предоставляющая Secure File Transfer Protocol и выполняется по протоколу SSH
* SCP.exe — это служебная программа копирования файла, который выполняется на SSH

Документация в этом разделе рассматривается использование OpenSSH в Windows, включая установку и вариантов настройки и использования конкретных Windows. Следующие разделы:
* Установка и удаление OpenSSH для Windows Server 2019 г. и Windows 10

Дополнительные подробную документацию для общих возможностей OpenSSH доступна через Интернет в [OpenSSH.com](https://www.openssh.com/manual.html). 

Master [OpenSSH проект с открытым кодом](https://www.openssh.com) управляется разработчиков проекта OpenBSD. Вилки Microsoft этого проекта находится в [Github](https://github.com/PowerShell/openssh-portable).
Отзывы о Windows OpenSSH буду оно может быть указано путем создания вопросов Github в нашем [репозиторий OpenSSH Github](https://github.com/PowerShell/openssh-portable). 
