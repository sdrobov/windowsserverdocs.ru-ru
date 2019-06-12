---
title: Установка Windows Admin Center
description: Инструкции по установке Windows Admin Center на Компьютере Windows или на сервере, позволяя нескольким пользователям получать доступ к Windows Admin Center в веб-браузере.
ms.technology: manage
ms.topic: article
author: jwwool
ms.author: jeffrew
ms.date: 06/07/2019
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: a9eb7944cd35dfa68e3c36cdc6c016f483a9f1e1
ms.sourcegitcommit: 6ef4986391607bb28593852d06cc6645e548a4b3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66811955"
---
# <a name="install-windows-admin-center"></a>Установка Windows Admin Center

> Относится к: Windows Admin Center, предварительная версия Windows Admin Center

В этом разделе описывается установка Windows Admin Center на Компьютере Windows или на сервере, позволяя нескольким пользователям получать доступ к Windows Admin Center в веб-браузере.

> [!Tip]
> Только начинаете знакомство с Windows Admin Center?
> [Узнайте дополнительные сведения о Windows Admin Center](../understand/windows-admin-center.md) или [скачайте платформу](https://aka.ms/windowsadmincenter).

## <a name="determine-your-installation-type"></a>Определить тип установки

Просмотрите [параметры установки](../plan/installation-options.md) включающее [поддерживаемые операционные системы](../plan/installation-options.md#supported-operating-systems-installation). Чтобы установить Windows Admin Center на виртуальную Машину в Azure, см. в разделе [Windows Admin Center развертывание в Azure](../azure/deploy-wac-in-azure.md).

## <a name="install-on-windows-10"></a>Установка в Windows 10

При установке в Windows 10 платформа Windows Admin Center будет использовать порт 6515 по умолчанию, однако вы можете указать другой порт. Также можно создавать ярлык для рабочего стола и разрешить Windows Admin Center управлять вашими доверенными узлами TrustedHosts.

> [!NOTE]
> Изменение доверенных узлов необходимо в среде рабочей группы или при использовании учетных данных локального администратора в домене. Если вы решили отказаться от этого параметра, необходимо [вручную настроить доверенные узлы](../support/troubleshooting.md#configure-trustedhosts).

При запуске Windows Admin Center из меню **Пуск** платформа откроется в браузере по умолчанию.

При запуске Windows Admin Center в первый раз вы увидите значок в области уведомлений на рабочем столе. Щелкните его правой кнопкой мыши и выберите команду **Открыть**, чтобы открыть инструмент в браузере по умолчанию, или выберите **Выход** для завершения фонового процесса.

## <a name="install-on-windows-server-with-desktop-experience"></a>Установка в Windows Server с рабочим столом

В среде Windows Server платформа Windows Admin Center устанавливается как сетевая служба. Необходимо указать порт для прослушивания. Кроме того, требуется сертификат для протокола HTTPS. Установщик может создать самозаверяющий сертификат для тестирования или вы можете предоставить отпечаток сертификата, уже установленного на компьютере. Если вы используете созданный сертификат, он должен соответствовать DNS-имени сервера. Если вы используете собственный сертификат, убедитесь, что имя, указанное в сертификате совпадать с именем компьютера (подстановочный знак сертификаты не поддерживаются.) Вы также есть возможность разрешить управление вашей TrustedHosts Windows Admin Center.

> [!NOTE]
> Изменение доверенных узлов необходимо в среде рабочей группы или при использовании учетных данных локального администратора в домене. Если вы решили отказаться от этого параметра, необходимо [вручную настроить доверенные узлы](../support/troubleshooting.md#configure-trustedhosts).

После завершения установки откройте браузер на удаленном компьютере и перейдите по URL-АДРЕСУ, представленные на последнем шаге установщика.

> [!WARNING]
> Срок действия автоматически созданных сертификатов — 60 дней после установки.

## <a name="install-on-server-core"></a>Установка в среде основных серверных компонентов

Если у вас есть установка основных серверных компонентов Windows Server, вы можете установить Windows Admin Center из командной строки (с правами администратора). Укажите порт и SSL-сертификат с помощью аргументов `SME_PORT` и `SSL_CERTIFICATE_OPTION` соответственно. Если вы собираетесь использовать существующий сертификат, воспользуйтесь `SME_THUMBPRINT` для указания его отпечатка.

> [!WARNING]
> Установка Windows Admin Center будет перезапустить службу WinRM, который разорвет все удаленные сеансы PowerShells. Рекомендуется установить локальный Cmd или PowerShell. Если вы устанавливаете решения автоматизации, будет нарушена при перезапуска службы WinRM, можно добавить параметр ```RESTART_WINRM=0``` по установке аргументы, но WinRM, необходимо перезапустить Windows Admin Center функции.

Выполните следующую команду, чтобы установить Windows Admin Center и автоматически создать самозаверяющий сертификат.

```   
msiexec /i <WindowsAdminCenterInstallerName>.msi /qn /L*v log.txt SME_PORT=<port> SSL_CERTIFICATE_OPTION=generate
```

Выполните следующую команду для установки Windows Admin Center с помощью существующего сертификата.

```
msiexec /i <WindowsAdminCenterInstallerName>.msi /qn /L*v log.txt SME_PORT=<port> SME_THUMBPRINT=<thumbprint> SSL_CERTIFICATE_OPTION=installed
```

> [!WARNING]
> Не вызывайте `msiexec` из PowerShell с использованием относительной нотации пути (например, `.\<WindowsAdminCenterInstallerName>.msi`). Эта нотация не поддерживается и установка завершится ошибкой. Удалите префикс `.\` или укажите полный путь к MSI-файлу.

## <a name="updating-windows-admin-center"></a>Обновление Windows Admin Center

Можно обновить без предварительных версий Windows Admin Center с помощью центра обновления Майкрософт или путем его установки вручную. 

Параметры сохраняются при обновлении до новой версии Windows Admin Center. Мы не поддерживаем официально обновления Insider Preview версии Windows Admin Center — мы думаем, что лучше выполнить чистую установку -, но мы не блокируется.