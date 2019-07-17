---
title: tpmtool
description: Раздел Windows команды для tpmtool - получает сведения о доверенный платформенный модуль.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
author: ashleytqy
ms.author: ashleytqy
manager: ronaldai
ms.date: 05/07/2019
ms.openlocfilehash: e125dbf6127b92c91e041c431f1e462e1f884168
ms.sourcegitcommit: 0ff812a80f654fa2c35b1632524e27841eca75c7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68230858"
---
# <a name="tpmtool"></a>tpmtool

Эта программа может использоваться для получения сведений о [доверенного платформенного модуля (TPM)](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview).

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
|getdeviceinformation|Основные сведения, связанные с доверенного платформенного МОДУЛЯ. Смысл значения флага сведения можно найти [здесь](https://docs.microsoft.com/windows/desktop/SecProv/win32-tpm-isreadyinformation#parameters).|
|gatherlogs [путь к выходному каталогу]|Собирает журналы доверенного платформенного МОДУЛЯ и помещает их в указанном каталоге. Если этот каталог не существует, он создается. По умолчанию они помещаются в текущем каталоге. Ниже приведены возможные файлы, созданные. </br>-TpmEvents.evtx</br>-TpmInformation.txt</br>-SRTMBoot.dat</br>-SRTMResume.dat</br>-DRTMBoot.dat</br>-DRTMResume.dat</br>|
|drivertracing [начало / остановка]|Начало / остановка сбора трассировок драйвера доверенного платформенного МОДУЛЯ. Журнал трассировки, TPMTRACE.etl, он будет сгенерирован и поместить в текущем каталоге.|
|parsetcglogs [-проверить (-v)]|Отображает проанализированный журнал TCG, также известный как Windows Boot Configuration журнала (WBCL). Наиболее актуальные описания событий можно найти на [веб-узла TCG](https://trustedcomputinggroup.org/resource/pc-client-specific-platform-firmware-profile-specification/)в разделе **описания событий**. Если `-validate` установленным флагом, проверяет, что значения Регистрация конфигурации платформы (PCR) доверенный платформенный модуль соответствуют значениям в журнале.|
|/?|Отображение справки в командной строке.|

## <a name="tpmtool_examples"></a>Примеры

Чтобы отобразить сведения доверенного платформенного модуля, введите следующую команду:
```
tpmtool getdeviceinformation
```
Чтобы собирать журналы доверенного платформенного МОДУЛЯ и помещать их в текущем каталоге, введите следующую команду:
```
tpmtool gatherlogs
```
Чтобы собирать журналы доверенного платформенного МОДУЛЯ и поместить их в `C:\Users\Public`, тип:
```
tpmtool gatherlogs C:\Users\Public
```
Для сбора данных трассировки драйвера доверенного платформенного МОДУЛЯ, введите следующую команду:
```
tpmtool drivertracing start
# Run scenario
tpmtool drivertracing stop
```
Чтобы проанализировать журнал TCG.
```
tpmtool parsetcglogs
```
Для анализа журнала TCG и проверки PCRs:
```
tpmtool parsetcglogs -validate
```

## <a name="decoding-error-codes"></a>Расшифровка кодов ошибок

Коды ошибок для конкретного доверенного платформенного МОДУЛЯ [здесь](https://docs.microsoft.com/windows/desktop/com/com-error-codes-6).
