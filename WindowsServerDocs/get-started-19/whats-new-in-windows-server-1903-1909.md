---
title: Что нового в Windows Server версий 1903 и 1909
description: В этом разделе описаны некоторые новые функции в Windows Server версий 1903 и 1909, которые являются выпусками Semi-Annual Channel.
ms.prod: windows-server
ms.technology: server-general
ms.topic: article
author: jasongerend
ms.author: jgerend
ms.date: 11/12/2019
ms.openlocfilehash: 13b9c1b004f57d46307664427f7ea3483c04c00f
ms.sourcegitcommit: b9ec35416a06854c1bc875a2b731d42a436fe313
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2019
ms.locfileid: "73962016"
---
# <a name="whats-new-in-windows-server-versions-1903-and-1909"></a>Что нового в Windows Server версий 1903 и 1909

>Относится к: Windows Server (Semi-Annual Channel)

В этом разделе описаны некоторые новые функции в Windows Server версии 1903, которая является выпуском Semi-Annual Channel. Эти функции включают в себя улучшения для запуска контейнеров и управления ими, средства для работы в установках основных серверных компонентов и возможность переноса хранилища с устройств Linux.

Windows Server версии 1909 — это следующий Semi-Annual Channel Windows Server, ориентированный на повышение надежности и производительности, а также другие общие улучшения, но не содержащий новых функций. Как и в случае с другими выпусками Semi-Annual Channel, он поддерживается в течение 18 месяцев после выпуска. Дополнительные сведения о датах поддержки выпусков Semi-Annual Channel см. в разделе [Информация о выпуске Windows Server](../get-started/windows-server-release-info.md).

Чтобы узнать о новых возможностях в последнем выпуске Windows Server (Long-Term Servicing Channel (LTSC)), обратитесь к статье [Новые возможности Windows Server 2019](../get-started-19/whats-new-19.md). Ознакомьтесь также со статьей [Новые возможности Windows 10 версии 1903 — информация для ИТ-специалистов](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1903).

Системные требования для этого выпуска совпадают с требованиями для Windows Server 2019 (см. [системные требования](../get-started-19/sys-reqs-19.md)). Дополнительные сведения об удаленных компонентах см. в статье [Удаленные или подлежащие замене компоненты в Windows Server версии 1903](../get-started-19/removed-features-1903.md).

> [!NOTE]
> Контейнеры Windows должны использовать ту же версию Windows, что и сервер узла, или *более раннюю*. Например, сервер узла, на котором запущена выпущенная версия Windows Server 1903 (сборка 18342), может запускать контейнеры Windows Server такой же или более ранней версии с аналогичным номером сборки (даже если контейнер использует версию Windows Insider Preview). Дополнительные сведения см. в статье [Windows container version compatibility](https://docs.microsoft.com/virtualization/windowscontainers/deploy-containers/version-compatibility) (Совместимость версий контейнеров Windows).

## <a name="enhanced-support-for-non-microsoft-container-services"></a>Расширенная поддержка для служб контейнеров сторонних разработчиков

Мы расширили возможности платформы для поддержки служб контейнеров Azure и служб контейнеров сторонних разработчиков.

- Мы интегрировали CRI-контейнер со службой вычисления узлов (HCS) для поддержки модулей контейнеров Windows и Linux в Windows (LCOW) в Azure.
- Мы сотрудничали с сообществом Kubernetes, чтобы обеспечить поддержку контейнеров Windows. Начиная с выпуска Kubernetes версии 1.14, узел Windows Server официально поддерживается в стабильной версии. Дополнительные сведения см. в статье [Windows containers now supported in Kubernetes](https://cloudblogs.microsoft.com/opensource/2019/03/25/windows-server-containers-now-supported-kubernetes/) (Контейнеры Windows теперь поддерживаются в Kubernetes).
- Tigera Calico для Windows теперь общедоступна как часть подписки Tigera Essentials и предлагает как сети без наложения, так и сетевые политики, совместимые в смешанных средах Linux/Windows.
- Мы усовершенствовали масштабируемость, улучшив поддержку сети с наложением для контейнеров Windows, включая интеграцию с Kubernetes в последней версии Flannel и Kubernetes версии 1.14. Дополнительные сведения см. в статье [Intro to Windows support in Kubernetes](https://kubernetes.io/docs/setup/windows/) (Общие сведения о поддержке Windows в Kubernetes).

## <a name="directx-hardware-acceleration-in-containers"></a>Аппаратное ускорение DirectX в контейнерах

Мы реализовали поддержку аппаратного ускорения интерфейсов API DirectX в контейнерах Windows, например в сценариях машинного обучения с использованием аппаратных средств локального графического процессора. Дополнительные сведения см. в статье [Bringing GPU acceleration to Windows containers](https://techcommunity.microsoft.com/t5/Containers/Bringing-GPU-acceleration-to-Windows-containers/ba-p/393939) (Обеспечение ускорения с помощью графического процессора для контейнеров Windows).

## <a name="updated-container-identity-and-group-managed-service-account-documentation"></a>Обновления касательно идентификации контейнеров и документации о групповой управляемой учетной записи службы

Мы добавили больше примеров и сведений о совместимости в документацию о [групповой управляемой учетной записи службы](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts) и сделали [модуль PowerShell](https://www.powershellgallery.com/packages/CredentialSpec) для спецификации учетных данных доступным в коллекции PowerShell. Дополнительные сведения см. в записи блога [What's new for container identity](https://techcommunity.microsoft.com/t5/Containers/What-s-new-for-container-identity/ba-p/389151) (Новые возможности удостоверений контейнеров).

## <a name="add-task-scheduler-and-hyper-v-manager-to-server-core-installations"></a>Добавление планировщика заданий и диспетчера Hyper-V к установкам основных серверных компонентов

Как правило, при использовании Windows Server (канала Semi-Annual Channel) в рабочей среде рекомендуется применять вариант установки основных серверных компонентов. Однако в основных серверных компонентах по умолчанию отсутствует ряд полезных средств управления. Вы можете добавить многие из наиболее часто используемых средств, установив пакет компонентов для обеспечения совместимости приложений, но некоторые средства в нем все еще отсутствовали.

Основываясь на отзывах пользователей, мы добавили еще два средства в пакет компонентов для обеспечения совместимости приложений в этой версии: планировщик заданий (taskschd.msc) и диспетчер Hyper-V (virtmgmt.msc).

Дополнительные сведения см. в статье [Пакет компонентов для обеспечения совместимости приложений основных серверных компонентов по требованию](../get-started-19/install-fod-19.md).

## <a name="storage-migration-service-now-migrates-local-accounts-clusters-and-linux-servers"></a>Служба переноса хранилищ теперь переносит локальные учетные записи, кластеры и серверы Linux

Служба переноса хранилищ упрощает перенос серверов в более новую версию Windows Server. Она предоставляет графическое средство, которое выполняет инвентаризацию данных на серверах, а затем передает данные и конфигурацию на более новые серверы (без участия пользователей и приложений).

Чтобы использовать эту версию Windows Server для оркестрации переноса, мы добавили следующие возможности:

- Перенос локальных пользователей и групп на новый сервер.
- Перенос хранилища из отказоустойчивых кластеров.
- Перенос хранилища с сервера Linux, использующего Samba.
- Более простая синхронизация перенесенных общих ресурсов в Azure с помощью компонента "Синхронизация файлов Azure".
- Перенос в новые сети, такие как Azure.

Дополнительные сведения о службе переноса хранилищ см. в [этой статье](../storage/storage-migration-service/overview.md).

## <a name="system-insights-disk-anomaly-detection"></a>Обнаружение аномалий диска с помощью функции системной аналитики

[Системная аналитика](../manage/system-insights/overview.md) — это функция прогнозной аналитики, которая локально анализирует системные данные Windows Server и дает представление о функционировании сервера. Она поставляется с рядом встроенных возможностей, но мы добавили возможность устанавливать дополнительные возможности с помощью Windows Admin Center, начиная с обнаружения аномалий диска.

Обнаружение аномалий диска — это новая возможность, которая определяет, когда диски ведут себя *иначе*, чем обычно. Хотя отличия не обязательно указывают на проблемы, просмотр этих аномальных моментов может быть полезен при устранении неполадок в ваших системах.

Эта возможность также доступна для серверов под управлением Windows Server 2019.

## <a name="windows-admin-center-enhancements"></a>Улучшения Windows Admin Center

Вышел новый выпуск Windows Admin Center, добавляющий новые функции в Windows Server. Дополнительные сведения см. в статье [Привет, Windows Admin Center!](../manage/windows-admin-center/understand/windows-admin-center.md)

## <a name="security-baseline-for-windows-10-and-windows-server"></a>Базовые параметры безопасности для Windows 10 и Windows Server

Доступен черновой выпуск [базовых параметров конфигурации безопасности](https://blogs.technet.microsoft.com/secguide/2019/04/24/security-baseline-draft-for-windows-10-v1903-and-windows-server-v1903/) для Windows 10 версии 1903 и Windows Server версии 1903.

## <a name="setupdiag"></a>SetupDiag
Выпущена версия 1.4.1 средства [SetupDiag](https://docs.microsoft.com/windows/deployment/upgrade/setupdiag).

SetupDiag — это программа командной строки, которая помогает с определением причины сбоя обновления Windows. SetupDiag выполняет поиск в файлах журнала программы установки Windows. SetupDiag использует набор правил для обнаружения известных проблем. В текущей версии SetupDiag файл rules.xml содержит 53 правила, которые извлекаются при запуске SetupDiag. Файл rules.xml будет обновляться по мере выхода новых версий SetupDiag.

## <a name="update-rollback-improvements"></a>Улучшения отката обновлений

Серверы теперь могут автоматически восстанавливаться после сбоев при запуске, удаляя обновления, если сбой при запуске возник после установки последних драйверов или исправлений. Если после недавней установки исправлений драйверов устройство не может загрузиться должным образом, Windows автоматически удалит обновления, чтобы устройство снова заработало в нормальном режиме.

Эта функция требует, чтобы сервер использовал вариант установки основных серверных компонентов с [разделом среды восстановления Windows](https://docs.microsoft.com/windows-hardware/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference).

## <a name="microsoft-defender-advanced-threat-protection-atp-improvements"></a>Улучшения Advanced Threat Protection в Защитнике Windows (ATP)

Windows Server включает в себя Microsoft Advanced Thread Protection в Защитнике (дополнительные сведения см. в разделе [Windows Defender Antivirus on Windows Server 2016](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/windows-defender-antivirus-on-windows-server-2016) (Антивирусная программа "Защитник Windows" в Windows Server 2016)). Этот выпуск содержит следующие улучшения:

- [Уменьшение контактной зоны атак](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/overview-attack-surface-reduction). ИТ-администраторы могут настроить устройства с расширенной веб-защитой, которая позволяет им определять списки разрешений и запретов для конкретных URL-адресов и IP-адресов.
- [Защита следующего поколения](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/windows-defender-antivirus-in-windows-10). Элементы управления были расширены для защиты от программ-шантажистов, неправильного использования учетных данных и атак, которые совершаются через съемное хранилище.
    - Возможности принудительного применения целостности — включена удаленная аттестация во время выполнения.
    - Возможности защиты от несанкционированного доступа — используется безопасность на основе виртуализации, чтобы изолировать критические возможности безопасности ATP от ОС и злоумышленников.
- Защитные технологии нового поколения ATP в Защитнике Windows:
    - **Расширенное машинное обучение Azure**. Улучшено благодаря усовершенствованным моделям машинного обучения и искусственного интеллекта, которые позволяют защищаться от атак злоумышленников, применяющих инновационные методы использования уязвимостей, средства и вредоносные программы.
    - **Защита от эпидемий вредоносных программ**. Обеспечивает защиту от эпидемий вредоносных программ, которая автоматически обновляет устройства новыми интеллектуальными данными при обнаружении новой эпидемии.
    - **Сертификат соответствия ISO 27001**. Гарантирует, что облачная служба провела анализ на наличие угроз, уязвимостей и воздействий, а также наличие управления рисками и контроля безопасности.
    - **Поддержка службы географического положения**. Поддерживается геолокация и суверенитет примеров данных, а также настраиваемые политики хранения.