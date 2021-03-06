---
title: Рекомендации по сетевому подключению
description: Рекомендации по настройке пропускной способности для развертываний удаленного рабочего стола.
ms.prod: windows-server
ms.technology: remote-desktop-services
ms.author: helohr
ms.date: 12/12/2019
ms.topic: article
author: Heidilohr
manager: lizross
ms.openlocfilehash: ba084c58e725627e838c07b5b5b9849d131b2038
ms.sourcegitcommit: 32f810c5429804c384d788c680afac427976e351
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/12/2020
ms.locfileid: "83203551"
---
# <a name="network-guidelines"></a>Рекомендации по сетевому подключению

При использовании удаленного сеанса Windows на качество работы значительно влияет доступная пропускная способность сети. Для работы разных приложений на устройствах с разным разрешением экрана требуются разные конфигурации сети. Поэтому важно убедиться, что сеть настроена в соответствии с вашими потребностями.

>[!NOTE]
>Следующие рекомендации применяются к сетям с уровнем потерь менее 0,1 %. Эти рекомендации сохраняются независимо от того, сколько сеансов вы размещаете на виртуальных машинах.

## <a name="applications"></a>Приложения

В следующей таблице перечислены минимальные рекомендации по настройке пропускной способности для обеспечения качественного взаимодействия с пользователем. Эти рекомендации основаны на руководствах по [использованию рабочих нагрузок Удаленного рабочего стола](remote-desktop-workloads.md).

| Тип рабочей нагрузки   | Рекомендуемая пропускная способность |
|-----------------|-----------------------|
| Легкий           | 1,5 Мбит/с              |
| Средний          | 3 Мбит/с                |
| Тяжелый           | 5 Мбит/с                |
| Мощный           | 15 Мбит/с               |

На забывайте, что нагрузка на сеть зависит от частоты исходящих кадров рабочей нагрузки приложения и разрешения экрана. При увеличении частоты кадров или разрешения экрана потребность в пропускной способности также возрастает. Например, небольшая рабочая нагрузка при высоком разрешении экрана требует больше пропускной способности, чем аналогичная рабочая нагрузка при обычном или низком разрешении.

Требования к пропускной способности могут изменяться в некоторых сценариях, например:

- голосовые конференции и видеоконференции;
- связь в режиме реального времени;
- потоковое видео в разрешении 4К.

Обязательно выполните нагрузочное тестирование этих сценариев в развертывании, используя Login VSI или другие средства моделирования. Изменяйте размер нагрузки, выполняйте нагрузочные тесты и проверяйте типичные пользовательские сценарии в удаленных сеансах, чтобы лучше изучить требования к сети.

## <a name="display-resolutions"></a>Разрешение экрана

Для использования устройств с разным разрешением экрана требуется разная пропускная способность. В следующей таблице перечислены рекомендации по пропускной способности, которые обеспечивают качественное взаимодействие с пользователем при стандартном разрешении экрана с частотой 30 кадров в секунду. Эти рекомендации применимы в сценариях с одним и несколькими пользователями. Помните, что сценарии с частотой менее 30 кадров в секунду, например чтение статического текста, требуют меньше пропускной способности.

| Стандартное разрешение экрана с частотой 30 кадров в секунду    | Рекомендуемая пропускная способность |
|------------------------------------------|-----------------------|
| Примерно 1024×768 пикселей                      | 1,5 Мбит/с              |
| Примерно 1280×720 пикселей                      | 3 Мбит/с                |
| Примерно 1920×1080 пикселей                     | 5 Мбит/с                |
| Примерно 3840×2160 пикселей (4К)                | 15 Мбит/с               |

## <a name="additional-resources"></a>Дополнительные ресурсы

Регион Azure, в котором вы находитесь, может влиять на взаимодействие с пользователем не меньше, чем условия сети. См. сведения, предоставляемые [оценщиком взаимодействия между пользователем и Виртуальным рабочим столом Windows](https://azure.microsoft.com/services/virtual-desktop/assessment/).
