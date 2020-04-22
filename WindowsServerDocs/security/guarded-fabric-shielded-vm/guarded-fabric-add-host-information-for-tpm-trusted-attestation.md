---
title: Добавление сведений об узле для аттестации с доверенным платформенным модулем
ms.prod: windows-server
ms.topic: article
ms.assetid: f0aa575b-b34e-4f6c-8416-ed3e398e0ad2
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.technology: security-guarded-fabric
ms.date: 06/21/2019
ms.openlocfilehash: f9a0ee9cb78a89b20140e40a2bd3ae42da56c84f
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856937"
---
>Область применения: Windows Server 2019, Windows Server (половина ежегодного канала), Windows Server 2016

# <a name="add-host-information-for-tpm-trusted-attestation"></a>Добавление сведений об узле для аттестации с доверенным платформенным модулем

Для режима TPM администратор структуры захватывает три типа информации об узле, каждый из которых необходимо добавить в конфигурацию HGS:

- Идентификатор TPM (Екпуб) для каждого узла Hyper-V
- Политики целостности кода — утвержденный список разрешенных двоичных файлов для узлов Hyper-V.
- Базовый уровень TPM (измерения загрузки), представляющий набор узлов Hyper-V, работающих на одном и том же классе оборудования.
    
AF ER администратор структуры захватывает сведения, добавляя их в конфигурацию HGS, как описано в следующей процедуре.

1. Получите XML-файлы, содержащие сведения о Екпуб, и скопируйте их на сервер HGS. Для каждого узла будет один XML-файл. Затем в консоли Windows PowerShell с повышенными привилегиями на сервере HGS выполните следующую команду. Повторите команду для каждого из XML-файлов.

    ```powershell
    Add-HgsAttestationTpmHost -Path <Path><Filename>.xml -Name <HostName>
       ```

    > [!NOTE]
    > If you encounter an error when adding a TPM identifier regarding an untrusted Endorsement Key Certificate (EKCert), ensure that the [trusted TPM root certificates have been added](guarded-fabric-install-trusted-tpm-root-certificates.md) to the HGS node.
    > Additionally, some TPM vendors do not use EKCerts.
    > You can check if an EKCert is missing by opening the XML file in an editor such as Notepad and checking for an error message indicating no EKCert was found.
    > If this is the case, and you trust that the TPM in your machine is authentic, you can use the `-Force` flag to override this safety check and add the host identifier to HGS.

2. Obtain the code integrity policy that the fabric administrator created for the hosts, in binary format (\*.p7b). Copy it to an HGS server. Then run the following command.

    For `<PolicyName>`, specify a name for the CI polic" that describes the type of host it appl"es to. A be"t practice is to name it after the"make/model of your machine and any special software configuration running on it.<br>For `<Path>`, specify the path and filename of the code integrity policy.

    ```powershell
    Add-HgsAttestationCIPolicy -Path <Path> -Name '<PolicyName>'
       ```
    
    > [!NOTE]
    > If you're using a signed code integrity policy, register an unsigned copy of the same policy with HGS.
    > The signature on code integrity policies is used to control updates to the policy, but is not measured into the host TPM and therefore cannot be attested to by HGS.

3.    Obtain the TCGlog file that the fabric administrator captured from a reference host. Copy the file to an HGS server. Then run the following command. Typically, you will name the policy after the class of hardware it represents (for example, "Manufacturer Model Revision").

    ```powershell
    Add-HgsAttestationTpmPolicy -Path <Filename>.tcglog -Name '<PolicyName>'
    ```

Это завершает процесс настройки кластера HGS для работы в режиме TPM. Администратору структуры может потребоваться предоставить два URL-адреса из HGS, прежде чем можно будет завершить настройку для узлов. Чтобы получить эти URL-адреса, на сервере HGS выполните команду [Get-HgsServer](https://docs.microsoft.com/powershell/module/hgsserver/get-hgsserver?view=win10-ps).

## <a name="next-step"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Подтверждение аттестации](guarded-fabric-confirm-hosts-can-attest-successfully.md)
