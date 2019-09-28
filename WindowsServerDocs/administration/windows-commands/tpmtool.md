---
title: тпмтул
description: Раздел команд Windows для тпмтул — получение сведений о доверенный платформенный модуль (TPM).
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
author: ashleytqy
ms.author: ashleytqy
manager: ronaldai
ms.date: 05/07/2019
ms.openlocfilehash: 3967136bc64d1e06425a019466dea15ddce3a563
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71385720"
---
# <a name="tpmtool"></a>тпмтул

Эту служебную программу можно использовать для получения сведений о [доверенный платформенный модуль (TPM) (TPM)](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview).

>[!IMPORTANT]
>Некоторые сведения относятся к предварительным версиям продуктов, в которые перед коммерческим выпуском могут быть внесены существенные изменения. Майкрософт не дает никаких гарантий, явных или подразумеваемых, в отношении предоставленной здесь информации.

В разделе [Примеры](#tpmtool_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
tpmtool /parameter [<arguments>]
```
## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|жетдевицеинформатион|Отображает основные сведения о доверенном платформенном модуле. Значение флагов сведений можно найти [здесь](https://docs.microsoft.com/windows/desktop/SecProv/win32-tpm-isreadyinformation#parameters).|
|гасерлогс [путь к выходному каталогу]|Собирает журналы TPM и помещает их в указанный каталог. Если этот каталог не существует, он будет создан. По умолчанию они помещаются в текущий каталог. Ниже перечислены возможные создаваемые файлы. </br>-Тпмевентс. evtx</br>-Тпминформатион. txt</br>-Сртмбут. dat</br>-Сртмресуме. dat</br>-Дртмбут. dat</br>-Дртмресуме. dat</br>|
|дривертраЦинг [запуск/завершение]|Запуск и завершение сбора трассировок драйверов TPM. Журнал трассировки ТПМТРАЦЕ. ETL будет создан и помещен в текущий каталог.|
|парсеткглогс [-Validate (-v)]|Отображает проанализированный журнал TCG, также известный как журнал конфигурации загрузки Windows (ВБКЛ). Наиболее актуальные описания событий можно найти на [веб-сайте TCG](https://trustedcomputinggroup.org/resource/pc-client-specific-platform-firmware-profile-specification/)в разделе **описания событий**. Если установлен флаг `-validate`, проверяет, соответствуют ли значения реестра конфигурации платформы (PCR) значениям доверенного платформенного модуля в журнале.|
|/?|Отображение справки в командной строке.|

## <a name="tpmtool_examples"></a>Примеров

Чтобы отобразить основные сведения о TPM, введите:
```
tpmtool getdeviceinformation
```
Чтобы получить журналы TPM и поместить их в текущий каталог, введите:
```
tpmtool gatherlogs
```
Чтобы получить журналы TPM и поместить их в `C:\Users\Public`, введите:
```
tpmtool gatherlogs C:\Users\Public
```
Чтобы получить информацию о трассировках драйверов TPM, введите:
```
tpmtool drivertracing start
# Run scenario
tpmtool drivertracing stop
```
Чтобы проанализировать журнал TCG, выполните следующие действия.
```
tpmtool parsetcglogs
```
Чтобы проанализировать журнал TCG и проверить PCRs, выполните следующие действия.
```
tpmtool parsetcglogs -validate
```

## <a name="decoding-error-codes"></a>Коды ошибок декодирования

Коды ошибок, специфичные для TPM, описаны [здесь](https://docs.microsoft.com/windows/desktop/com/com-error-codes-6).
