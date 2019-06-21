---
ms.date: 01/07/2019
contributor: damaerteMSFT
author: maertendMSFT
keywords: OpenSSH, SSH, Win32-OpenSSH
title: OpenSSH в Windows
ms.product: w10
ms.openlocfilehash: c6563fbe4fe69acad4d295a3f7fe166e92d38444
ms.sourcegitcommit: afb0602767de64a76aaf9ce6a60d2f0e78efb78b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/20/2019
ms.locfileid: "67280051"
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

Master [OpenSSH проект с открытым кодом](https://www.openssh.com) управляется разработчиков проекта OpenBSD. Вилки Microsoft этого проекта находится в [GitHub](https://github.com/PowerShell/openssh-portable).
Отзывы о Windows OpenSSH буду оно может быть указано путем создания вопросов GitHub в нашем [репозиторий OpenSSH GitHub](https://github.com/PowerShell/openssh-portable). 
