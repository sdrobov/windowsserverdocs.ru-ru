---
title: Развертывание инфраструктуры гиперконвергентном с помощью центра администрирования Windows
ms.topic: article
author: cosmosdarwin
ms.author: cosdar
ms.prod: windows-server
ms.technology: manage
ms.date: 11/04/2019
ms.openlocfilehash: 088fb7b8f03ab7e575b562572f2e29e1b5774760
ms.sourcegitcommit: 771db070a3a924c8265944e21bf9bd85350dd93c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2020
ms.locfileid: "85474491"
---
# <a name="deploy-hyperconverged-infrastructure-with-windows-admin-center"></a>Развертывание инфраструктуры гиперконвергентном с помощью центра администрирования Windows

> Применяется к: Windows Admin Center, ознакомительная версия Windows Admin Center

Для развертывания инфраструктуры гиперконвергентном с использованием двух или более подходящих серверов Windows можно использовать центр администрирования Windows [версии 1910](https://docs.microsoft.com/windows-server/manage/windows-admin-center/understand/windows-admin-center) или более поздней. Эта новая функция имеет вид многоэтапного рабочего процесса, который поможет вам установить компоненты, настроить сеть, создать кластер и развернуть Локальные дисковые пространства и (или) программно-определяемую сеть (SDN), если они выбраны.

![Снимок экрана: рабочий процесс создания кластера](../media/deploy-hyperconverged-infrastructure/deployment-workflow-screenshot.png)

  > [!Important]
  > Эта функция находится в активном режиме разработки. Он доступен в предварительной версии, поэтому вы можете испытать его на ранних этапах и поделиться своим мнением.

## <a name="preview-the-workflow"></a>Предварительный просмотр рабочего процесса

### <a name="1-prerequisites"></a>1. Предварительные требования

Рабочий процесс создания кластера в центре администрирования Windows не выполняет установку операционных систем без операционной системы, поэтому необходимо сначала установить Windows Server на каждом сервере. Поддерживаемые версии: Windows Server 2016, Windows Server 2019 и Windows Server Insider Preview. Кроме того, перед запуском рабочего процесса необходимо присоединить каждый сервер к тому же домену Active Directory, в котором работает центр администрирования Windows.

### <a name="2-install-windows-admin-center"></a>2. Установка центра администрирования Windows

Следуйте инструкциям, чтобы [скачать и установить](https://docs.microsoft.com/windows-server/manage/windows-admin-center/understand/windows-admin-center) последнюю версию центра администрирования Windows.

### <a name="3-install-the-cluster-creation-extension"></a>3. Установка расширения создания кластера

Рабочий процесс создания кластера доставляется и обновляется через веб-канал расширения центра администрирования Windows. Это значит, что мы можем решить ваши отзывы и быстрее вносить улучшения на этапе предварительной версии.

Чтобы установить расширение, запустите центр администрирования Windows, а затем выполните следующие действия.

1.  В правом верхнем углу щелкните значок параметров.
2.  Переход к расширениям
3.  Поиск расширения создания кластера
4.  Выбор установки

![Снимки экрана четырех шагов по установке расширения создания кластера](../media/deploy-hyperconverged-infrastructure/how-to-install.png)

После установки выберите расширение создания кластера в раскрывающемся списке в левом верхнем углу:

![Снимок экрана: Запуск расширения создания кластера](../media/deploy-hyperconverged-infrastructure/how-to-launch.png)

## <a name="limitations-of-the-preview-release"></a>Ограничения предварительной версии

Рабочий процесс создания кластера находится под активной разработкой. другими словами, он не завершен.

Ниже приведены некоторые ограничения текущей предварительной версии.

1.  **Требования к домену.** В настоящее время для рабочего процесса необходимо, чтобы каждый добавляемый сервер уже был присоединен к тому же домену Active Directory, что и центр администрирования Windows.
2.  **Отобразить скрипт.** В текущей предварительной версии скрипты, выполняемые рабочим процессом с помощью функции «Показать скрипт» в центре администрирования Windows, и не могут загрузить полный отчет обо всем, что произошло в конце. Мы понимаем, что это важно для многих пользователей — следите за настройкой. В то же время используйте командлеты, приведенные ниже, чтобы [узнать, что происходит](#see-whats-happening).
3.  **Возобновить или начать заново.** Несмотря на то, что вы можете выйти из попадете с помощью рабочего процесса, текущий предварительный выпуск не обрабатывает возобновление, когда вы остановились, и не можете полностью очистить его перед началом работы. Чтобы выполнить повторное развертывание на тех же серверах для тестирования, используйте приведенные ниже командлеты для [отмены и запуска](#undo-and-start-over).
4.  **Удаленный доступ к памяти (RDMA).** В текущем предварительном выпуске не удается включить сетевые подключения RDMA, которые обычно используются с инфраструктурой гиперконвергентном. Пока что Завершите рабочий процесс без включения RDMA, а затем используйте другие средства для включения RDMA точно так же, как в противном случае.

Помимо устранения этих ограничений, существует бесчисленные возможности, которые можно добавить в будущие выпуски: применение обновлений Windows, Настройка следящего сервера для кворума кластера, импорт виртуальных машин и т. д. Чтобы помочь нам определить приоритеты для нужных функций, отправьте [отзыв](#feedback) , как описано ниже.

## <a name="see-whats-happening"></a>Узнайте, что происходит

Используйте эти командлеты Windows PowerShell для отслеживания и просмотра действий, выполняемых рабочим процессом.

Чтобы узнать, какие компоненты Windows установлены, используйте `Get-WindowsFeature` командлет. Пример:

```PowerShell
Get-WindowsFeature "Hyper-V", "Failover-Clustering", "Data-Center-Bridging", "BitLocker"
```

![Снимок экрана: выходные данные PowerShell](../media/deploy-hyperconverged-infrastructure/script-out-1.png)

  > [!Note]
  > Устанавливаемые компоненты зависят от выбранного типа кластера.

Для просмотра сетевых адаптеров и их свойств, например имени, IPv4-адресов и идентификатор виртуальной локальной сети воспользуйтесь следующей командой:

```PowerShell
Get-NetAdapter | Where Status -Eq "Up" | Sort InterfaceAlias | Format-Table Name, InterfaceDescription, Status, LinkSpeed, VLANID, MacAddress
Get-NetAdapter | Where Status -Eq "Up" | Get-NetIPAddress -AddressFamily IPv4 -ErrorAction SilentlyContinue | Sort InterfaceAlias | Format-Table InterfaceAlias, IPAddress, PrefixLength
```

![Снимок экрана: выходные данные PowerShell](../media/deploy-hyperconverged-infrastructure/script-out-2.png)

Чтобы просмотреть виртуальные коммутаторы Hyper-V и определить, как объединены физические сетевые адаптеры, воспользуйтесь следующей командой:

```PowerShell
Get-VMSwitch
Get-VMSwitchTeam
```

![Снимок экрана: выходные данные PowerShell](../media/deploy-hyperconverged-infrastructure/script-out-3.png)

Чтобы увидеть виртуальные сетевые адаптеры узла, выполните:

```PowerShell
Get-VMNetworkAdapter -ManagementOS | Format-Table Name, IsManagementOS, SwitchName
Get-VMNetworkAdapterTeamMapping -ManagementOS | Format-Table NetAdapterName, ParentAdapter
```

![Снимок экрана: выходные данные PowerShell](../media/deploy-hyperconverged-infrastructure/script-out-4.png)

Чтобы просмотреть текущий отказоустойчивый кластер и его узлы членов, выполните:

```PowerShell
Get-Cluster
Get-ClusterNode
```

![Снимок экрана: выходные данные PowerShell](../media/deploy-hyperconverged-infrastructure/script-out-5.png)

Чтобы узнать, включен ли Локальные дисковые пространства и пул носителей по умолчанию, созданный автоматически:

```PowerShell
Get-ClusterStorageSpacesDirect
Get-StoragePool -IsPrimordial $False
```

![Снимок экрана: выходные данные PowerShell](../media/deploy-hyperconverged-infrastructure/script-out-6.png)

## <a name="undo-and-start-over"></a>Отменить и начать заново

Используйте эти командлеты Windows PowerShell, чтобы отменить изменения, внесенные рабочим процессом, и начать заново.

### <a name="remove-virtual-machines-or-other-clustered-resources"></a>Удаление виртуальных машин или других кластерных ресурсов

Если вы создали виртуальные машины или другие кластерные ресурсы, например сетевые контроллеры для программно-определяемой сети, сначала удалите их.

Например, чтобы удалить ресурсы по имени, используйте:

```PowerShell
Get-ClusterResource -Name "<NAME>" | Remove-ClusterResource
```

### <a name="undo-the-storage-steps"></a>Отмена действий хранилища

Если вы включили Локальные дисковые пространства, отключите ее с помощью этого сценария:

> [!Warning]
> Эти командлеты окончательно удаляют все данные в Локальные дисковые пространстваных томах. Это невозможно отменить.

```PowerShell
Get-VirtualDisk | Remove-VirtualDisk
Get-StoragePool -IsPrimordial $False | Remove-StoragePool
Disable-ClusterS2D
```

### <a name="undo-the-clustering-steps"></a>Отмена шагов кластеризации

Если вы создали кластер, удалите его с помощью этого командлета:

```PowerShell
Remove-Cluster -CleanUpAD
```

Чтобы также удалить отчеты о проверке кластера, выполните этот командлет на каждом сервере, который входит в состав кластера:

```PowerShell
Get-ChildItem C:\Windows\cluster\Reports\ | Remove-Item
```

### <a name="undo-the-networking-steps"></a>Отмена действий по работе с сетью

Выполните эти командлеты на каждом сервере, который входит в состав кластера.

Если вы создали виртуальный коммутатор Hyper-V, выполните следующие действия.

```PowerShell
Get-VMSwitch | Remove-VMSwitch
```

> [!Note]
> `Remove-VMSwitch`Командлет автоматически удаляет все виртуальные адаптеры и отменяет объединение физических адаптеров, внедренных в коммутаторы.

Если вы изменили свойства сетевого адаптера, такие как имя, IPv4-адрес и идентификатор виртуальной ЛС, выполните следующие действия.

> [!Warning]
> Эти командлеты удаляют имена сетевых адаптеров и IP-адреса. Убедитесь, что у вас есть сведения, необходимые для подключения, например адаптер для управления, который исключен из приведенного ниже сценария. Кроме того, убедитесь, что вы знаете, как соединяются серверы с точки зрения физических свойств, таких как MAC-адрес, а не только имени адаптера в Windows.

```PowerShell
Get-NetAdapter | Where Name -Ne "Management" | Rename-NetAdapter -NewName $(Get-Random)
Get-NetAdapter | Where Name -Ne "Management" | Get-NetIPAddress -ErrorAction SilentlyContinue | Where AddressFamily -Eq IPv4 | Remove-NetIPAddress
Get-NetAdapter | Where Name -Ne "Management" | Set-NetAdapter -VlanID 0
```

Теперь все готово для запуска рабочего процесса.

## <a name="feedback"></a>Обратная связь

Эта предварительная версия предназначена для вашего отзыва. Вот несколько способов достижения нашей команды:

- [Отправка и голосование запросов на функции в UserVoice](https://windowsserver.uservoice.com/forums/295071/category/319162?query=%5Bhci%5D)
- [Присоединяйтесь к форуму центра администрирования Windows в центре технического сообщества Майкрософт](https://techcommunity.microsoft.com/t5/Windows-Server-Management/bd-p/WindowsServerManagement)
- Электронная почта хЦи — развертывание [at] microsoft.com
- Твит в[@servermgmt](https://twitter.com/servermgmt)

## <a name="report-an-issue"></a>Сообщить о проблеме

Используйте приведенные выше каналы, чтобы сообщить о возникшей ошибке в рабочем процессе создания кластера.

Если возможно, включите следующие сведения, чтобы помочь нам быстро воспроизвести и устранить проблему:

- Тип выбранного кластера (например: *"гиперконвергентном"*)
- Шаг, на котором возникла ошибка (например, *"3,2 Создание кластера"*)
- Версия расширения создания кластера. Последовательно выберите **Параметры**  >  **расширения**  >  **установленные расширения** и просмотрите столбец **версия** (пример: *"1.0.30"*).
- Сообщения об ошибках (на экране или в консоли браузера), которые можно открыть, нажав клавишу **F12**.
- Любые другие важные сведения о вашей среде

## <a name="additional-references"></a>Дополнительные ссылки

- [Привет, центр администрирования Windows](https://docs.microsoft.com/windows-server/manage/windows-admin-center/understand/windows-admin-center)
- [Развертывание локальных дисковых пространств](https://docs.microsoft.com/windows-server/storage/storage-spaces/deploy-storage-spaces-direct)
