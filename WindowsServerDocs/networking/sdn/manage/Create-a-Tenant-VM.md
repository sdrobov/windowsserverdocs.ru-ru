---
title: Создание виртуальной Машины и подключение к клиента виртуальной сети или виртуальной локальной сети
description: Этот раздел является частью программного обеспечения определены сетевые руководство о том, как управление рабочими нагрузками клиента и виртуальные сети в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: networking-sdn
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3c62f533-1815-4f08-96b1-dc271f5a2b36
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 001eb3efa073e4ffbdfad41f88949303159a7274
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="create-a-vm-and-connect-to-a-tenant-virtual-network-or-vlan"></a>Создание виртуальной Машины и подключение к клиента виртуальной сети или виртуальной локальной сети

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

В этом разделе можно использовать для создания клиента виртуальной машины \(VM\) и подключения виртуальной Машины, либо к виртуальной сети, созданный с помощью виртуализации сети Hyper-V или виртуальной локальной сети \(VLAN\). 

Этот раздел содержит следующие разделы.

- [Создайте виртуальную Машину и подключитесь к виртуальной сети с помощью командлетов Windows PowerShell сетевого контроллера](#bkmk_vn)
- [Создайте виртуальную Машину и подключитесь к виртуальной локальной сети с помощью NetworkControllerRESTWrappers](#bkmk_vlan)

## <a name="requirements"></a>Требования к
Перед выполнением процедуры, описанные в следующих разделах, помните о следующих требованиях.

1. Необходимо создать сетевым адаптерам виртуальных Машин с статических контроля доступа \(MAC\) адреса, MAC-адрес виртуальной машины не изменить во время существования виртуальных Машин. 
>[!NOTE]
>Если виртуальная машина MAC-адрес изменяется во время существования виртуальных Машин, сетевой контроллер невозможно настроить политики, необходимые для сетевого адаптера. Если политика для сетевой адаптер не настроен, сетевой адаптер, препятствующую обработки сетевого трафика и происходит сбой всех связь с сетью. 

2. Если для виртуальной Машины требуется доступ к сети при запуске, важно не запускайте виртуальной Машины до и после последний этап конфигурации - параметр идентификатор интерфейса порта сетевой адаптер на виртуальной Машине. При запуске виртуальной Машины до завершения этого шага виртуальной Машины не могут взаимодействовать по сети пока сетевой интерфейс создается в сетевой контроллер и контроллер были применены все применимые политики - политики виртуальной сети \(ACLs\) и качество службы \(QoS\) списки управления доступом.

Можно также использовать процессы, описанные в этой статье для развертывания виртуальных устройств. С помощью нескольких дополнительных шагов можно настроить устройства, обработать или проверьте данные пакеты, поступающие на или с других виртуальных машин в виртуальной сети.

>[!IMPORTANT]
>В следующих разделах приведены примеры Windows PowerShell команд, содержащих примеры значений для многих параметров. Убедитесь, замените примеры значений в этих командах со значениями, подходящими для вашего развертывания, прежде чем выполнять эти команды.  

## <a name="bkmk_vn"></a>Создайте виртуальную Машину и подключитесь к виртуальной сети с помощью командлетов Windows PowerShell сетевого контроллера

Этот раздел включает следующие разделы.

1.  [Создание виртуальной Машины с сетевым адаптером виртуальной Машины, который имеет статический MAC-адрес](#bkmk_create)
2.  [Получение виртуальную сеть, содержащую подсеть, к которому нужно подключить сетевой адаптер](#bkmk_getvn)
3.  [Создать объект сетевого интерфейса в сетевого контроллера](#bkmk_object)
4.  [Получите свойство InstanceId для сетевого интерфейса, из сетевого контроллера](#bkmk_getinstance)
5.  [Установить для идентификатора интерфейса на виртуальной Машине Hyper-V порт сетевого адаптера](#bkmk_setinstance)
6.  [Запуск виртуальной Машины](#bkmk_start)

### <a name="bkmk_create"></a>Создание виртуальной Машины с сетевым адаптером виртуальной Машины, который имеет статический MAC-адрес

Создание виртуальной Машины с сетевым адаптером, который имеет статический MAC-адрес, используйте следующий пример команды.

    
    New-VM -Generation 2 -Name "MyVM" -Path "C:\VMs\MyVM" -MemoryStartupBytes 4GB -VHDPath "c:\VMs\MyVM\Virtual Hard Disks\WindowsServer2016.vhdx" -SwitchName "SDNvSwitch" 
    
    Set-VM -Name "MyVM" -ProcessorCount 4
    
    Set-VMNetworkAdapter -VMName "MyVM" -StaticMacAddress "00-11-22-33-44-55" 
    

### <a name="bkmk_getvn"></a>Получение виртуальную сеть, содержащую подсеть, к которому нужно подключить сетевой адаптер
Убедитесь, что вы уже создали виртуальной сети перед использованием в этом примере команда. Дополнительные сведения см. в разделе [создание, удаление или обновление виртуальных сетей клиентов](https://technet.microsoft.com/windows-server-docs/networking/sdn/manage/create%2c-delete%2c-or-update-tenant-virtual-networks).

Чтобы получить виртуальной сети, используйте следующий пример команды.

    
    $vnet = get-networkcontrollervirtualnetwork -connectionuri $uri -ResourceId “Contoso_WebTier”
    

>[!NOTE]
>Если вам требуется настраиваемые списки управления доступом для данного сетевого интерфейса, необходимо создать ACL теперь согласно инструкциям в разделе [используйте списки управления доступом (ACL) для управления центра обработки данных сетевого трафика потока](../../sdn/manage/Use-Access-Control-Lists--ACLs--to-Manage-Datacenter-Network-Traffic-Flow.md)

### <a name="bkmk_object"></a>Создать объект сетевого интерфейса в сетевого контроллера

Чтобы создать объект сетевого интерфейса в сетевой контроллер, используйте следующий пример команды.

>[!NOTE]
>Если вы создали пользовательские ACL после предыдущего шага, можно использовать теперь.

    
    $vmnicproperties = new-object Microsoft.Windows.NetworkController.NetworkInterfaceProperties
    $vmnicproperties.PrivateMacAddress = "001122334455" 
    $vmnicproperties.PrivateMacAllocationMethod = "Static" 
    $vmnicproperties.IsPrimary = $true 

    $vmnicproperties.DnsSettings = new-object Microsoft.Windows.NetworkController.NetworkInterfaceDnsSettings
    $vmnicproperties.DnsSettings.DnsServers = @("24.30.1.11", "24.30.1.12")
    
    $ipconfiguration = new-object Microsoft.Windows.NetworkController.NetworkInterfaceIpConfiguration
    $ipconfiguration.resourceid = "MyVM_IP1"
    $ipconfiguration.properties = new-object Microsoft.Windows.NetworkController.NetworkInterfaceIpConfigurationProperties
    $ipconfiguration.properties.PrivateIPAddress = “24.30.1.101”
    $ipconfiguration.properties.PrivateIPAllocationMethod = "Static"
    
    $ipconfiguration.properties.Subnet = new-object Microsoft.Windows.NetworkController.Subnet
    $ipconfiguration.properties.subnet.ResourceRef = $vnet.Properties.Subnets[0].ResourceRef
    
    $vmnicproperties.IpConfigurations = @($ipconfiguration)
    New-NetworkControllerNetworkInterface –ResourceID “MyVM_Ethernet1” –Properties $vmnicproperties –ConnectionUri $uri
    

### <a name="bkmk_getinstance"></a>Получите свойство InstanceId для сетевого интерфейса, из сетевого контроллера
Чтобы получить свойство InstanceId для сетевого интерфейса, из сетевого контроллера, используйте следующий пример команды.

    
    $nic = Get-NetworkControllerNetworkInterface -ConnectionUri $uri -ResourceId "MyVM-Ethernet1"
    

### <a name="bkmk_setinstance"></a>Установить для идентификатора интерфейса на виртуальной Машине Hyper-V порт сетевого адаптера
Чтобы задать идентификатор интерфейса на виртуальной Машине Hyper-V порт сетевого адаптера, используйте следующий пример команды.

>[!NOTE]
>Вы должны выполнить эти команды на узле Hyper-V установленной виртуальной Машины.

    
    #Do not change the hardcoded IDs in this section, because they are fixed values and must not change.
    
    $FeatureId = "9940cd46-8b06-43bb-b9d5-93d50381fd56"
    
    $vmNics = Get-VMNetworkAdapter -VMName “MyVM”
    
    $CurrentFeature = Get-VMSwitchExtensionPortFeature -FeatureId $FeatureId -VMNetworkAdapter $vmNics
    
    if ($CurrentFeature -eq $null)
    {
    $Feature = Get-VMSystemSwitchExtensionPortFeature -FeatureId $FeatureId
    
    $Feature.SettingData.ProfileId = "{$($nic.InstanceId)}"
    $Feature.SettingData.NetCfgInstanceId = "{56785678-a0e5-4a26-bc9b-c0cba27311a3}"
    $Feature.SettingData.CdnLabelString = "TestCdn"
    $Feature.SettingData.CdnLabelId = 1111
    $Feature.SettingData.ProfileName = "Testprofile"
    $Feature.SettingData.VendorId = "{1FA41B39-B444-4E43-B35A-E1F7985FD548}"
    $Feature.SettingData.VendorName = "NetworkController"
    $Feature.SettingData.ProfileData = 1
    
    Add-VMSwitchExtensionPortFeature -VMSwitchExtensionFeature  $Feature -VMNetworkAdapter $vmNics
    }
    else
    {
    $CurrentFeature.SettingData.ProfileId = "{$($nic.InstanceId)}"
    $CurrentFeature.SettingData.ProfileData = 1
    
    Set-VMSwitchExtensionPortFeature -VMSwitchExtensionFeature $CurrentFeature  -VMNetworkAdapter $vmNic
    }
    

### <a name="bkmk_start"></a>Запуск виртуальной Машины
Для запуска виртуальной Машины, используйте следующий пример команды.

    
    Get-VM -Name “MyVM” | Start-VM 
    
Теперь успешно создан виртуальной Машины, подключения виртуальной Машины клиенту виртуальной сети и работы виртуальной Машины, чтобы он мог обрабатывать рабочие нагрузки клиентов.

## <a name="bkmk_vlan"></a>Создайте виртуальную Машину и подключитесь к виртуальной локальной сети с помощью NetworkControllerRESTWrappers

Этот раздел включает следующие разделы.

1. [Создание виртуальной Машины и назначьте статический MAC-адрес](#bkmk_mac)
2. [Установить для идентификатора виртуальной ЛС на сетевом адаптере виртуальной Машины](#bkmk_vid)
3. [Получение подсети логической сети и создания сетевого интерфейса](#bkmk_subnet)
4. [Задайте свойство InstanceId порту Hyper-V](#bkmk_instance)
5. [Запуск виртуальной Машины](#bkmk_startvlan)


###<a name="bkmk_mac"></a>Создание виртуальной Машины и назначьте статический MAC-адрес
Для создания виртуальной Машины и назначения статических мультимедиа \(MAC\) адреса для виртуальной Машины, можно использовать команды в следующем примере.

    New-VM -Generation 2 -Name "MyVM" -Path "C:\VMs\MyVM" -MemoryStartupBytes 4GB -VHDPath "c:\VMs\MyVM\Virtual Hard Disks\WindowsServer2016.vhdx" -SwitchName "SDNvSwitch" 

    Set-VM -Name "MyVM" -ProcessorCount 4

    Set-VMNetworkAdapter -VMName "MyVM" -StaticMacAddress "00-11-22-33-44-55" 

###<a name="bkmk_vid"></a>Установить для идентификатора виртуальной ЛС на сетевом адаптере виртуальной Машины
Чтобы задать идентификатор виртуальной ЛС сетевого адаптера, можно использовать следующий пример команды.


    Set-VMNetworkAdapterIsolation –VMName “MyVM” -AllowUntaggedTraffic $true -IsolationMode VLAN -DefaultIsolationId 123


###<a name="bkmk_subnet"></a>Получение подсети логической сети и создания сетевого интерфейса

Чтобы получить логической подсети и создать сетевой интерфейс, с помощью логической подсети, можно использовать команды в следующем примере.


    $logicalnet = get-networkcontrollerLogicalNetwork -connectionuri $uri -ResourceId "00000000-2222-1111-9999-000000000002"

    $vmnicproperties = new-object Microsoft.Windows.NetworkController.NetworkInterfaceProperties
    $vmnicproperties.PrivateMacAddress = "00-1D-C8-B7-01-02"
    $vmnicproperties.PrivateMacAllocationMethod = "Static"
    $vmnicproperties.IsPrimary = $true 
    
    $vmnicproperties.DnsSettings = new-object Microsoft.Windows.NetworkController.NetworkInterfaceDnsSettings
    $vmnicproperties.DnsSettings.DnsServers = $logicalnet.Properties.Subnets[0].DNSServers

    $ipconfiguration = new-object Microsoft.Windows.NetworkController.NetworkInterfaceIpConfiguration
    $ipconfiguration.resourceid = "MyVM_Ip1"
    $ipconfiguration.properties = new-object Microsoft.Windows.NetworkController.NetworkInterfaceIpConfigurationProperties
    $ipconfiguration.properties.PrivateIPAddress = “10.127.132.177”
    $ipconfiguration.properties.PrivateIPAllocationMethod = "Static"

    $ipconfiguration.properties.Subnet = new-object Microsoft.Windows.NetworkController.Subnet
    $ipconfiguration.properties.subnet.ResourceRef = $logicalnet.Properties.Subnets[0].ResourceRef

    $vmnicproperties.IpConfigurations = @($ipconfiguration)
    $vnic = New-NetworkControllerNetworkInterface –ResourceID “MyVM_Ethernet1” –Properties $vmnicproperties –ConnectionUri $uri

    $vnic.InstanceId
    

###<a name="bkmk_instance"></a>Задайте свойство InstanceId порту Hyper-V
Чтобы задать свойство InstanceId на порту Hyper-V, используется в следующем примере показан на узле Hyper-V где находится виртуальная машина.

  
    #The hardcoded Ids in this section are fixed values and must not change.
    $FeatureId = "9940cd46-8b06-43bb-b9d5-93d50381fd56"

    $vmNics = Get-VMNetworkAdapter -VMName “MyVM”

    $CurrentFeature = Get-VMSwitchExtensionPortFeature -FeatureId $FeatureId -VMNetworkAdapter $vmNic
        
    if ($CurrentFeature -eq $null)
    {
        $Feature = Get-VMSystemSwitchExtensionFeature -FeatureId $FeatureId
        
        $Feature.SettingData.ProfileId = "{$InstanceId}"
        $Feature.SettingData.NetCfgInstanceId = "{56785678-a0e5-4a26-bc9b-c0cba27311a3}"
        $Feature.SettingData.CdnLabelString = "TestCdn"
        $Feature.SettingData.CdnLabelId = 1111
        $Feature.SettingData.ProfileName = "Testprofile"
        $Feature.SettingData.VendorId = "{1FA41B39-B444-4E43-B35A-E1F7985FD548}"
        $Feature.SettingData.VendorName = "NetworkController"
        $Feature.SettingData.ProfileData = 1
                
        Add-VMSwitchExtensionFeature -VMSwitchExtensionFeature  $Feature -VMNetworkAdapter $vmNic
    }        
    else
    {
        $CurrentFeature.SettingData.ProfileId = "{$InstanceId}"
        $CurrentFeature.SettingData.ProfileData = 1

        Set-VMSwitchExtensionPortFeature -VMSwitchExtensionFeature $CurrentFeature  -VMNetworkAdapter $vmNic
    }


###<a name="bkmk_startvlan"></a>Запуск виртуальной Машины
Для запуска виртуальной Машины, можно использовать следующий пример команды.


    Get-VM -Name “MyVM” | Start-VM 

Теперь успешно создан виртуальной Машины, подключения виртуальной Машины для виртуальной ЛС и работы виртуальной Машины, чтобы он мог обрабатывать рабочие нагрузки клиентов.

  

