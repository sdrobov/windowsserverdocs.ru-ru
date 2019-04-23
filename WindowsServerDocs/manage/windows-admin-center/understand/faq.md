---
title: 'Вопросы и ответы: Windows Admin Center'
description: Получите ответы о Windows Admin Center (Project Honolulu)
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: 39f862485cf938981aae37e352f3448998b7c9c0
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59829575"
---
# <a name="windows-admin-center-frequently-asked-questions"></a>Вопросы и ответы: Windows Admin Center

>Область применения. Windows Admin Center, предварительная версия Windows Admin Center

Здесь приведены ответы на наиболее часто задаваемые вопросы о Windows Admin Center.

## <a name="what-is-windows-admin-center"></a>Что такое Windows Admin Center?

Windows Admin Center — это облегченная, платформа на основе браузера с графическим интерфейсом пользователя и набор средств для ИТ-администраторов по управлению Windows Server и Windows 10. Это следующий шаг в развитии знакомых встроенных средств администрирования, таких как Server Manager и консоль управления (MMC), обеспечивающих улучшенные, более удобные, интегрированные и безопасные условия работы.

## <a name="can-i-use-windows-admin-center-in-production-environments"></a>Можно ли использовать Windows Admin Center в рабочих средах?

Да. Платформа Windows Admin Center официально доступна и готова к широкому использованию в рабочих средах. Это платформа, которая будет продолжать расти и улучшаться, и выход ознакомительной версии означает, что текущие возможности платформы и основные средства отвечают стандартным требованиям Майкрософт, предъявляемым к выпуску, и нашей шкале качества в отношении удобства использования, надежности, производительности, доступности, безопасности и простоты внедрения.

## <a name="how-much-does-it-cost-to-use-windows-admin-center"></a>Сколько стоит использование Windows Admin Center?

Пользоваться Windows Admin Center можно бесплатно в рамках оплаченной лицензии на Windows. Платформу Windows Admin Center (доступна в виде отдельно скачиваемых файлов) можно использовать с действующими лицензиями на Windows Server или Windows 10 без дополнительной платы. Ее использование регламентируется дополнительным лицензионным соглашением Windows.

## <a name="what-versions-of-windows-server-can-i-manage-with-windows-admin-center"></a>Какими версиями Windows Server можно управлять с помощью Windows Admin Center?

Windows Admin Center оптимизирован для 2019 Windows Server необходимо включить ключевые темы в выпуске Windows Server 2019: гибридные облачные сценарии и гиперконвергентная инфраструктура управления в частности. Несмотря на то, что Windows Admin Center будет лучше работать с Windows Server 2019, он поддерживает управление различных версий, которые клиенты уже используют: Windows Server 2012 и более поздних версий, полностью поддерживаются. Также имеется ограниченная функциональность для управления Windows Server 2008 R2.

## <a name="is-windows-admin-center-a-complete-replacement-for-all-traditional-in-box-and-rsat-tools"></a>Является ли Windows Admin Center полноценной заменой для всех традиционных встроенных инструментов и средств удаленного администрирования сервера?

Нет. Несмотря на то что платформа Windows Admin Center поддерживает управление множеством распространенных сценариев, она не является полноценной заменой для всех традиционных средств консоли управления (MMC). Подробный обзор какие средства входят в состав Windows Admin Center, см. сведения о [управление серверами](..\use\manage-servers.md) в нашей документации. В состав диспетчера управления серверами в Windows Admin Center входят следующие основные возможности:

* Отображение ресурсов и использование ресурсов
* Управление сертификатами
* Управление устройствами
* Просмотр событий
* Проводник
* Управление брандмауэром
* Управление установленными приложениями
* Настройка локальных пользователей и групп
* Параметры сети
* Просмотр и завершение процессов и создание дампов процессов
* Изменение реестра
* Управление назначенные задачи
* Управление службами Windows
* Включение и отключение ролей и компонентов
* Управление виртуальными машинами Hyper-V и виртуальными коммутаторами
* Управление хранилищем
* Управление репликой хранилища
* Управление обновлениями Windows
* Консоль PowerShell
* Подключение к удаленному рабочему столу

Windows Admin Center также предоставляет следующие решения:

* Управление компьютером — предоставляет набор функции диспетчера серверов для управления клиентскими компьютерами с Windows 10
* Диспетчер отказоустойчивого кластера — поддержка непрерывного управления отказоустойчивыми кластерами и ресурсами кластера
* Диспетчер гиперконвергентных кластеров — совершенно новые возможности, разработанные специально для работы с локальными дисковыми пространствами и Hyper-V. В его состав входит информационная панель с диаграммами и оповещениями для мониторинга.

Windows Admin Center является дополнением к средствам удаленного администрирования сервера (RSAT) и не заменяет их, потому что роли, такие как Active Directory, DHCP, DNS и IIS, пока еще не обладают эквивалентными возможностями управления, доступными в Windows Admin Center.

## <a name="can-windows-admin-center-be-used-to-manage-the-free-microsoft-hyper-v-server"></a>Можно ли использовать Windows Admin Center для управления бесплатным сервером Microsoft Hyper-V Server?

Да. Windows Admin Center можно использовать для управления Microsoft Hyper-V Server 2016 и Microsoft Hyper-V Server 2012 R2.

## <a name="can-i-deploy-windows-admin-center-on-a-windows-10-computer"></a>Можно ли развернуть Windows Admin Center на компьютере с Windows 10

Да, Windows Admin Center можно установить на ОС Windows 10 (версия 1709 или более поздняя версия), запущенной в режиме рабочего стола.  Windows Admin Center также можно установить на сервере с Windows Server 2016 или более в режиме шлюза и затем доступны через веб-браузер на компьютере Windows 10. [Дополнительные сведения о вариантах установки](..\plan\installation-options.md).

## <a name="ive-heard-that-windows-admin-center-uses-powershell-under-the-hood-can-i-see-the-actual-scripts-that-it-uses"></a>Я слышал, что Windows Admin Center использует PowerShell за кулисами, я вижу реальных сценариев, которые он использует?

Да! [Showscript функция](..\use\get-started.md#view-powershell-scripts-used-in-windows-admin-center) была добавлена в предварительной версии Windows Admin Center 1806 и теперь входит в канале общедоступной версии.

## <a name="are-there-any-plans-for-windows-admin-center-to-manage-windows-server-2008-r2-or-earlier"></a>Планируется ли реализация поддержки управления Windows Server 2008 R2 или более ранних версий в Windows Admin Center?

Теперь поддерживает Windows Admin Center **ограниченной** функциональные возможности управления Windows Server 2008 R2. В основе Windows Admin Center лежат возможности PowerShell и технологии платформы, которых нет в Windows Server 2008 R2 и более ранних версиях, поэтому полная поддержка нереализуема. Windows Server 2008/2008 R2 приближается к окончанию поддержки в января 2020 г., корпорация Майкрософт рекомендует пользователям [переход на Azure или обновление до последней версии Windows Server](https://www.microsoft.com/en-us/cloud-platform/windows-server-2008).

## <a name="are-there-any-plans-for-windows-admin-center-to-manage-linux-connections"></a>Планируется ли реализация поддержки управления подключениями Linux в Windows Admin Center?

Мы изучаем из-за спроса, но в данный момент не заблокированные планируется доставлять поддержки может состоять только из подключения консоли по протоколу SSH.

## <a name="which-web-browsers-are-supported-by-windows-admin-center"></a>Какие веб-браузеры поддерживает платформа Windows Admin Center?

Последние версии Microsoft Edge (Windows 10, версия 1709 или более поздняя версия) и браузеры Google Chrome, протестированные и поддерживаемые на Windows 10. [Представление от браузера известные проблемы](..\use\known-issues.md#browser-specific-issues). Другие современные веб-браузеры или на других платформах, не входят в настоящее время наши матрицы тестирования и, следовательно, не *официально* поддерживается.

## <a name="how-does-windows-admin-center-handle-security"></a>Как в Windows Admin Center осуществляется обеспечение безопасности?

Трафик из браузера в шлюз Windows Admin Center использует протокол HTTPS. Трафик от шлюза к управляемым серверам поступает через стандартное удаленное взаимодействие PowerShell и инструментарий WMI через WinRM. Для управления целевыми серверами мы поддерживаем LAPS (диспетчер паролей локальных администраторов), ограниченное делегирование на основе ресурсов, шлюз управления доступом с помощью AD или Azure AD, а также управление доступом на основе ролей.

## <a name="are-there-any-cloud-dependencies"></a>Существует ли зависимость от облака?

Платформе Windows Admin Center не требуется доступ к Интернету и Microsoft Azure. Windows Admin Center может управлять Windows Server и экземплярами Windows в любом месте: на физических системах, в виртуальных машинах на любом гипервизоре либо в облаке. Несмотря на то что со временем будет добавлена интеграция с различными службами Azure, это будут дополнительные функции, использование которых будет необязательным для работы с Windows Admin Center.

## <a name="are-there-any-other-dependencies-or-prerequisites"></a>Существуют ли какие-либо зависимости или предварительные требования?

Windows Admin Center можно установить в среде Windows 10 с обновлением Fall Anniversary Update (1709) или более поздней версии либо в среде Windows Server 2016 или более поздней версии. Для управления Windows Server 2008 R2, 2012 или 2012 R2 на этих серверах требуется установка Windows Management Framework 5.1. Другие зависимости отсутствуют. Службы IIS не требуются, агенты не требуются, SQL Server не требуется.

## <a name="what-about-extensibility-and-3rd-party-support"></a>Существует ли расширяемость и поддержка решений сторонних производителей?

Windows Admin Center имеет Комплект, что любой пользователь может писать собственные расширения. Так как этот продукт является платформой, расширение нашей экосистемы и обеспечение поддержки решений партнеров были основным приоритетом с самого начала процесса разработки. [Более подробные сведения о пакете SDK для Windows Admin Center](..\extend\extensibility-overview.md).

## <a name="can-i-manage-hyper-converged-infrastructure-with-windows-admin-center"></a>Можно ли управлять гиперконвергентной инфраструктурой с помощью Windows Admin Center?

Да. Windows Admin Center поддерживает управление гиперконвергентной кластеров под управлением Windows Server 2016 или Windows Server 2019. Решение диспетчера гиперконвергированного кластера в Windows Admin Center был ранее на этапе предварительной версии, но теперь **общедоступная**, с помощью некоторые новые функции в предварительной версии. Дополнительные сведения [об управлении гиперконвергентной инфраструктурой](..\use\manage-hyper-converged.md).

## <a name="does-windows-admin-center-require-system-center"></a>Требуется ли для работы с Windows Admin Center пакет продуктов System Center?

Нет. Windows Admin Center представляет собой дополнение к System Center, но System Center не является обязательным. [Дополнительные сведения о Windows Admin Center и System Center](related-management.md#system-center).

## <a name="can-windows-admin-center-replace-system-center-virtual-machine-manager-scvmm"></a>Может ли Windows Admin Center заменить System Center Virtual Machine Manager (SCVMM)?

Windows Admin Center и SCVMM являются дополнительными решениями; платформа Windows Admin Center предназначена для замены традиционных оснасток консоли управления (MMC) и средств администрирования серверов.  Платформа Windows Admin Center не предназначена для замены средств мониторинга SCVMM. [Дополнительные сведения о Windows Admin Center и System Center](related-management.md#system-center).

## <a name="what-is-windows-admin-center-preview-which-version-is-right-for-me"></a>Что такое ознакомительная версия Windows Admin Center; какая версия мне подойдет?

Существует две версии Windows Admin Center, доступные для скачивания:

### <a name="windows-admin-center"></a>Windows Admin Center

* Эта версия подойдет для ИТ-администраторов, которые не могут часто выполнять обновления или которым нужно больше времени для проверки выпусков, которые они используют в производстве. Нашей текущей общедоступной версии (GA) — 1809.5 Windows Admin Center.
* Последний официальный выпуск можно [скачать здесь](https://aka.ms/WACDownload).

* Выпуски Windows Admin Center общедоступной версии поддерживаются постоянно, в зависимости от корпорации Майкрософт [политика современного жизненного цикла](https://support.microsoft.com/help/30881/modern-lifecycle-policy). Это означает, что поддерживается только для обслуживания и поддерживается в последней версии Windows Admin Center общедоступной версии, а пользователи должны «Будьте в курсе последних» выполнив обновление до последнего выпуска общедоступной версии Windows Admin Center в течение 30 дней доступности оставаться. Эта политика применяется к как саму платформу Windows Admin Center, а также любые расширения Microsoft, которые общедоступной версии и опубликованные в расширении Windows Admin Center веб-канала. Обратите внимание на то, что некоторые расширения могут обновляться чаще, чем другие, между выпусками Windows Admin Center общедоступной версии.

### <a name="windows-admin-center-preview"></a>Ознакомительная версия Windows Admin Center

* Эта версия подойдет для ИТ-администраторов, которые хотят на регулярной основе использовать самые последние и интересные возможности. Нашей целью является предоставление последующие обновления освобождает каждый месяц или около того. Базовая платформа продолжает оставаться готовой для применения в рабочей среде, а лицензия предоставляет права на использование в коммерческих целях. Тем не менее, обратите внимание, что новые средства и возможности будут отмечены как "ДЛЯ ОЗНАКОМЛЕНИЯ", и ими можно будет пользоваться для оценки их работы.
* Для получения последнего предварительного выпуска зарегистрированные участники программы предварительной оценки могут скачать ознакомительную версию Windows Admin Center непосредственно на [странице загрузки предварительных сборок Windows Server для участников программы предварительной оценки Windows](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver) в раскрывающемся списке "Дополнительные файлы для загрузки". Если вы еще не зарегистрированы как участник программы предварительной оценки, см. раздел [Начало работы с Windows Server](https://insider.windows.com/en-us/for-business-getting-started-server/) на портале программы предварительной оценки Windows для бизнеса.

## <a name="why-was-windows-admin-center-chosen-as-the-final-name-for-project-honolulu"></a>Почему в качестве конечного названия для "Project Honolulu" было выбрано название "Windows Admin Center"?

Windows Admin Center — это официальное название продукта "Project Honolulu". В нем отражается наше видение интегрированных возможностей для ИТ-администраторов, направленных на работу с целым спектром административных задач и сценариев управления. Это название также подчеркивает нашу ориентированность на клиентах в контексте потребностей ИТ-администраторов и характеризует то, во что мы стремимся инвестировать средства и какие возможности стараемся предоставлять.

## <a name="where-can-i-learn-more-about-windows-admin-center-or-get-more-details-on-the-topics-above"></a>Где можно узнать дополнительные сведения о Windows Admin Center или получить более подробные сведения по темам выше?

Наша [страница запуска](https://aka.ms/WindowsAdminCenter) лучше всего подходит для того, чтобы начать ознакомление с платформой и содержит ссылки на недавно разбитую по категориям документацию, ссылку на файлы для скачивания, сведения о том, как отправлять отзывы, ссылки на справочную информацию и другие ресурсы.

## <a name="what-is-the-version-history-of-windows-admin-center"></a>Что такое журнал версий Windows Admin Center?

[Просмотр журнала версий здесь.](..\overview.md#release-history)

## <a name="im-having-an-issue-with-windows-admin-center-where-can-i-get-help"></a>Где получить помощь при возникновении проблем в работе с Windows Admin Center?

См. наше [руководство по устранению неисправностей](..\use\troubleshooting.md) и наш список [известных проблем](..\use\known-issues.md).
