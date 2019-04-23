---
title: Устранение неполадок службы защиты узла
ms.custom: na
ms.prod: windows-server-threshold
ms.topic: article
ms.assetid: 80ea38f4-4de6-4f85-8188-33a63bb1cf81
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 7fe01039b47c36d940973fba97d25c401f5af8a7
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59851375"
---
# <a name="troubleshooting-guarded-hosts"></a>Устранение неполадок защищенных узлов

> Относится к: Windows Server 2019 г., Windows Server (полугодовой канал), Windows Server 2016

В этом разделе описываются способы устранения распространенных проблем, возникающих при развертывании, а также ОС защищенный узел Hyper-V в защищенной структуре.
Если вы не уверены на характер неполадки, предварительного выполнения try [защищенных диагностики fabric](guarded-fabric-troubleshoot-diagnostics.md) на узлах Hyper-V для сужения потенциально вызывает.

## <a name="guarded-host-feature"></a>Защищенный узел функции

Если вы столкнетесь с проблемами с узла Hyper-V, сначала убедитесь, что **поддержку защиты узла Hyper-V** компонент установлен.
Без этой функции на узле Hyper-V будет утеряна некоторых важных параметров и программного обеспечения, которые позволяют передавать аттестации и подготовки экранированных виртуальных машин.

Чтобы проверить, установлен ли компонент, с помощью диспетчера серверов или выполните следующую команду в окне PowerShell с повышенными привилегиями:

```powershell
Get-WindowsFeature HostGuardian
```

Если компонент не установлен, установите его с помощью следующей команды PowerShell:

```powershell
Install-WindowsFeature HostGuardian -Restart
```

## <a name="attestation-failures"></a>Сбои аттестации

Если узел не прошел аттестацию с помощью службы защиты узла, он сможет запускать экранированные виртуальные машины.
Выходные данные [Get HgsClientConfiguration](https://technet.microsoft.com/library/dn914500.aspx) на этом узле показано, сведения о причине сбоя аттестации в этом узле.

В следующей таблице описаны значения, которые могут появиться в **AttestationStatus** поля и возможные дальнейшие действия, если это необходимо.

AttestationStatus         | Объяснение
--------------------------|------------
Срок действия истек                   | Узел передается аттестации ранее, но он выдан сертификат работоспособности истек. Обеспечить синхронизацию узла и время HGS.
InsecureHostConfiguration | Узел не прошел аттестацию, так как он не соответствует требованиям политики, аттестации, настроенные на HGS. Дополнительные сведения см. в таблице AttestationSubStatus.
NotConfigured             | Узел не настроен для использования аттестации и защиты ключей HGS. Он настраивается для режима локальной, вместо этого. Если этот узел находится в защищенной структуре, используйте [HgsClientConfiguration набора](https://technet.microsoft.com/library/dn914494.aspx) предоставлять его с URL-адреса для сервера HGS.
Переданный                    | Узел, переданный аттестации.
TransientError            | Не удалось последней попытки аттестации из-за с сетью, службы или других временных ошибок. Повторите последние операцию.
TpmError                  | Узел не удалось выполнить его последней попытки аттестации, из-за ошибки с помощью доверенного платформенного МОДУЛЯ. Дополнительные сведения см. в журналах доверенного платформенного МОДУЛЯ.
UnauthorizedHost          | Узел не прошел аттестацию, так как он не был авторизован для запуска экранированных виртуальных машин. Убедитесь, что узел не принадлежит к группе безопасности, доверенным для HGS для запуска экранированных виртуальных машин.
Неизвестно                   | Узел не производил попытки еще аттестации в службе HGS.


Когда **AttestationStatus** считается **InsecureHostConfiguration**, один или несколько причин, которые будут заполнены в **AttestationSubStatus** поля.
В таблице ниже приведены возможные значения для AttestationSubStatus и советы по устранению проблемы.

AttestationSubStatus       | Что значит и что делать
---------------------------|-------------------------------
BitLocker                  | Тома операционной системы узла не шифруется с помощью BitLocker. Чтобы исправить это, [включить BitLocker](https://technet.microsoft.com/itpro/windows/keep-secure/bitlocker-basic-deployment) на томе операционной системы или [отключить политику BitLocker на HGS](guarded-fabric-manage-hgs.md#review-attestation-policies).
CodeIntegrityPolicy        | Узел не настроен на использование политики целостности кода или не использует политики, доверяет сервер HGS. Убедитесь, политику целостности кода будет настроена, который перезапуска узла и политика зарегистрирован сервер HGS. Дополнительные сведения см. в разделе [создать и применить политику целостности кода](guarded-fabric-tpm-trusted-attestation-capturing-hardware.md#create-and-apply-a-code-integrity-policy).
DumpsEnabled               | Узел настроен для разрешения аварийные копии памяти или live дампы памяти, что не допускается вашими политиками HGS. Чтобы устранить эту проблему, отключите дампы на узле.
DumpEncryption             | Узел настроен так, чтобы разрешить аварийные дампы или дампов памяти в реальном времени, но не шифрует дампы. Отключите дампы на узле или [Настройте шифрование дампов](https://technet.microsoft.com/windows-server-docs/virtualization/hyper-v/manage/about-dump-encryption).
DumpEncryptionKey          | Узел настроен для разрешения и шифрования дампов, но не использует известно HGS сертификат для шифрования. Чтобы исправить это, [обновление ключа шифрования дампов](https://technet.microsoft.com/windows-server-docs/virtualization/hyper-v/manage/about-dump-encryption) на узле или [зарегистрируйте ключ в службе HGS](guarded-fabric-manage-hgs.md#authorizing-new-guarded-hosts).
FullBoot                   | Узел возобновляется из состояния сна или гибернации. Перезапустите узел, чтобы разрешить для очистки, полной загрузки.
HibernationEnabled         | Узел настроена возможность спящего режима без шифрования файл спящего режима, что не допускается вашими политиками HGS. Отключить спящий режим и перезапустите узел, или [Настройте шифрование дампов](https://technet.microsoft.com/windows-server-docs/virtualization/hyper-v/manage/about-dump-encryption).
HypervisorEnforcedCodeIntegrityPolicy | Узел не настроен на использование политики целостности кода на уровне низкоуровневой оболочки. Убедитесь, что целостность кода включена, настроены и принудительно низкоуровневой оболочкой. См. в разделе [руководство по развертыванию Device Guard](https://technet.microsoft.com/itpro/windows/keep-secure/deploy-device-guard-deploy-code-integrity-policies) Дополнительные сведения.
Iommu                      | Функции безопасности на основе виртуализации узла не настроены для нужен устройство IOMMU для защиты от атак прямого доступа к памяти, при необходимости вашими политиками HGS. Проверьте узел имеет IOMMU, что оно включено, и что Device Guard — [настроено обязательное использование средства защиты DMA](https://technet.microsoft.com/itpro/windows/keep-secure/deploy-device-guard-enable-virtualization-based-security#enable-virtualization-based-security-vbs-and-device-guard) при запуске VBS.
PagefileEncryption         | Не было включено шифрование файлов на странице на узле. Чтобы устранить эту проблему, запустите `fsutil behavior set encryptpagingfile 1` для включения шифрования файла страницы. Дополнительные сведения см. в разделе [поведение fsutil](https://technet.microsoft.com/library/cc785435.aspx).
Безопасной загрузки                 | Безопасная загрузка является либо не включена на этом узле или нет с помощью шаблона безопасной загрузки Майкрософт. [Включить безопасную загрузку](https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/disabling-secure-boot#enable_secure_boot) с помощью шаблона безопасной загрузки Майкрософт, чтобы устранить эту проблему.
SecureBootSettings         | Базовый план доверенный платформенный модуль на этом узле не соответствует ни одному из доверенных с HGS. Это может произойти при изменении вашего UEFI запуска центров, DBX переменной, флаг отладки или настраиваемых политик безопасной загрузки путем установки нового оборудования или программного обеспечения. Если вы доверяете, оборудование, встроенного по и настройки программного обеспечения этого компьютера, вы можете [записать новый базовый план доверенного платформенного МОДУЛЯ](guarded-fabric-tpm-trusted-attestation-capturing-hardware.md#capture-the-tpm-baseline-for-each-unique-class-of-hardware) и [зарегистрировать его в службе HGS](guarded-fabric-manage-hgs.md#authorizing-new-guarded-hosts).
TcgLogVerification         | Журнал TCG (базовый доверенного платформенного МОДУЛЯ) не удается получить или проверен. Это может указывать на проблему с встроенное по узла, доверенный платформенный модуль или другие компоненты оборудования. Если узел настроен предпринимается попытка загрузки PXE загрузку Windows, устаревшие Net загрузки программы (NBP) также может вызывать эту ошибку. Убедитесь, что все программы сетевой нагрузки в актуальном состоянии при включении PXE-загрузки.
VirtualSecureMode          | Функции безопасности на основе виртуализации, работающими на узле. Включить VBS и что ваша система отвечает настроенного [функции безопасности платформы](https://technet.microsoft.com/itpro/windows/keep-secure/deploy-device-guard-enable-virtualization-based-security#validate-enabled-device-guard-hardware-based-security-features). Обратитесь к [Device Guard документации](https://technet.microsoft.com/itpro/windows/keep-secure/device-guard-deployment-guide) Дополнительные сведения о требованиях к VBS.
