---
title: Репозитория программного обеспечения Linux для продуктов Майкрософт
description: В этом документе описывается, как использовать и установить пакеты программного обеспечения Linux для продуктов Майкрософт.
ms.custom: na
ms.prod: windows-server-threshold
ms.service: na
manager: szark
ms.technology: compute
ms.topic: article
ms.assetid: b5387444-595f-4f38-abb7-163a70ea1895
author: szarkos
ms.author: szark
ms.date: 10/16/2017
ms.openlocfilehash: 77b309739125a2114ef4ada4adb305f4dd169b06
ms.sourcegitcommit: 927adf32faa6052234ad08f21125906362e593dc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2019
ms.locfileid: "67033324"
---
# <a name="linux-software-repository-for-microsoft-products"></a>Репозитория программного обеспечения Linux для продуктов Майкрософт

## <a name="overview"></a>Обзор
Корпорация Майкрософт создает и поддерживает широкий набор программных продуктов для систем Linux и делает их доступными через стандартный репозиториями пакетов APT и YUM. В этом документе описывается настройка в репозитории в системе Linux, таким образом, вы можете затем установку или обновление программного обеспечения корпорации Майкрософт Linux с помощью средств управления стандартный пакет вашему дистрибутиву.

Репозитория программного обеспечения корпорации Майкрософт Linux состоит из нескольких вложенных репозиториев:

 - рабочую среду — в рабочей, вложенный репозиторий предназначен для пакетов, предназначен для использования в рабочей среде. Эти пакеты коммерчески поддерживаются корпорацией Майкрософт в соответствии с условиями договора на поддержку или программа, которая содержит с корпорацией Майкрософт.

 - MSSQL-server - эти репозитории содержат пакеты для Microsoft SQL Server на базе Linux — см. также: [SQL Server в Linux](https://www.microsoft.com/en-us/sql-server/sql-server-vnext-including-Linux).

> [!Note]
> Пакеты в репозиториях программного обеспечения Linux, распространяются условия лицензионного соглашения, расположенного в пакетах. Прочитайте условия лицензии перед использованием пакета. Установка и использование пакета означает согласие с настоящими условиями. Если вы не согласны с условиями лицензии, не используйте пакет.


## <a name="configuring-the-repositories"></a>Настройка репозиториев
Путем установки пакета Linux, к которому применяется дистрибутив Linux и версии репозиториями можно настроить автоматически. Будет установлена Конфигурация репозитория, а также открытый ключ GPG, используемый средствами, такими как apt и yum/zypper для проверки подписанных пакетов и/или метаданные репозитория.

### <a name="enterprise-linux-rhel-and-variants"></a>Enterprise Linux (RHEL и вариантов)

 - Enterprise Linux 6 (EL6)

        sudo rpm -Uvh https://packages.microsoft.com/config/rhel/6/packages-microsoft-prod.rpm

 - Enterprise Linux 7 (EL7)

        sudo rpm -Uvh https://packages.microsoft.com/config/rhel/7/packages-microsoft-prod.rpm


### <a name="ubuntu"></a>Ubuntu

 - Ubuntu 14.04 (верный)

        curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
        sudo apt-add-repository https://packages.microsoft.com/ubuntu/14.04/prod
        sudo apt-get update

 - Ubuntu 16.04 (Xenial)

        curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
        sudo apt-add-repository https://packages.microsoft.com/ubuntu/16.04/prod
        sudo apt-get update

 - Ubuntu 18.04 (Bionic)

        curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
        sudo apt-add-repository https://packages.microsoft.com/ubuntu/18.04/prod
        sudo apt-get update

 - Ubuntu 18.10 (космическая)

        curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
        sudo apt-add-repository https://packages.microsoft.com/ubuntu/18.10/prod
        sudo apt-get update

 - Ubuntu 19.04 (Disco)

        curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
        sudo apt-add-repository https://packages.microsoft.com/ubuntu/19.04/prod
        sudo apt-get update

### <a name="suse-linux-enterprise-12"></a>SUSE Linux Enterprise 12

        sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm


## <a name="manual-configuration"></a>Ручная настройка
Файлы конфигурации репозитория будут доступны из [packages.microsoft.com/config](https://packages.microsoft.com/config/). Имя и расположение этих файлов можно найти, используя следующее соглашение об именовании, URI:

        https://packages.microsoft.com/config/<Distribution>/<Version>/prod.(repo|list)

**Пакет и репозитория подписывания ключа**

 - Открытый ключ GPG корпорации Майкрософт может быть скачан здесь: [https://packages.microsoft.com/keys/microsoft.asc](https://packages.microsoft.com/keys/microsoft.asc)
 - Открытый идентификатор ключа: Microsoft (подписей выпуска) <gpgsecurity@microsoft.com>
 - Отпечаток открытого ключа: `BC52 8686 B50D 79E3 39D3 721C EB3E 94AD BE12 29CF`

### <a name="examples"></a>Примеры

 - RHEL/CentOS 7

        # Install repository configuration
        curl https://packages.microsoft.com/config/rhel/7/prod.repo > ./microsoft-prod.repo
        sudo cp ./microsoft-prod.repo /etc/yum.repos.d/

        # Install Microsoft's GPG public key
        curl https://packages.microsoft.com/keys/microsoft.asc > ./microsoft.asc
        sudo rpm --import ./microsoft.asc

 - Ubuntu 16.04

        # Install repository configuration
        curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > ./microsoft-prod.list
        sudo cp ./microsoft-prod.list /etc/apt/sources.list.d/

        # Install Microsoft GPG public key
        curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
        sudo cp ./microsoft.gpg /etc/apt/trusted.gpg.d/



