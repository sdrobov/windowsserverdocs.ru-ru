---
title: Создание виртуальной машины и подключение к виртуальной сети или виртуальной локальной сети клиента
description: В этом разделе мы покажем, как создать виртуальную Машину клиента и подключить его к любой виртуальной сети, созданный с помощью виртуализации сети Hyper-V или в виртуальной локальной сети (VLAN).
manager: dougkim
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
ms.date: 08/24/2018
ms.openlocfilehash: e23e6c020c12dd4900caa368daae0cc6dbeceaf4
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59856815"
---
# <a name="create-a-vm-and-connect-to-a-tenant-virtual-network-or-vlan"></a>Создание виртуальной машины и подключение к виртуальной сети или виртуальной локальной сети клиента

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

В этом разделе создайте виртуальную Машину клиента и подключить его к каждой виртуальной сети, созданный с помощью виртуализации сети Hyper-V или в виртуальной локальной сети (VLAN). Можно использовать командлеты Windows PowerShell сетевого контроллера для подключения к виртуальной сети или NetworkControllerRESTWrappers для подключения к виртуальной локальной сети.

Используйте процессы, описанные в этом разделе для развертывания виртуальных устройств. Несколько дополнительных действий можно настроить устройства для обработки или проверки пакетов данных, которые проходят в или из других виртуальных машин в виртуальной сети.

В подразделах этого раздела включают примеры команд Windows PowerShell, которые содержат примеры значений для многих параметров. Убедитесь, что примеры значений в этих командах замените значения, которые подходят для развертывания, прежде чем вы выполните следующие команды. 


## <a name="prerequisites"></a>предварительные требования

1. Сетевым адаптерам виртуальных Машин, созданных с помощью статического MAC-адреса в течение времени существования виртуальной машины.<p>Если MAC-адрес изменяется во время существования виртуальной Машины, сетевой контроллер не удается настроить необходимые политики для этого сетевого адаптера. Конфигурация политики для сети препятствует обработки сетевого трафика сетевого адаптера, и весь обмен данными с сетью, происходит сбой.  

2. Если виртуальной Машине требуется доступ к сети при запуске, не запускаются до и после установки идентификатор интерфейса на виртуальной Машине портов сетевого адаптера виртуальной Машины. Если вы запустите виртуальную Машину перед заданием идентификатор интерфейса, и сетевой интерфейс не существует, виртуальной Машины не могут взаимодействовать в сети в сетевой контроллер и все примененные политики.

3. Если вам нужны настраиваемые списки управления доступом для данного сетевого интерфейса, затем создайте ACL теперь с помощью инструкций в разделе [используйте списки управления доступом (ACL) для управления центра обработки данных трафик потоков для сети](../../sdn/manage/Use-Access-Control-Lists--ACLs--to-Manage-Datacenter-Network-Traffic-Flow.md)

Убедитесь, что вы уже создали виртуальную сеть перед использованием в этом примере команда. Дополнительные сведения см. в разделе [Create, Delete или Update виртуальных сетей клиентов](https://technet.microsoft.com/windows-server-docs/networking/sdn/manage/create%2c-delete%2c-or-update-tenant-virtual-networks).

## <a name="create-a-vm-and-connect-to-a-virtual-network-by-using-the-windows-powershell-network-controller-cmdlets"></a>Создать виртуальную Машину и подключитесь к виртуальной сети с помощью командлетов Windows PowerShell сетевого контроллера


1. Создайте виртуальную Машину с сетевым адаптером виртуальной Машины, имеет статический MAC-адрес. 

   ```PowerShell    
   New-VM -Generation 2 -Name "MyVM" -Path "C:\VMs\MyVM" -MemoryStartupBytes 4GB -VHDPath "c:\VMs\MyVM\Virtual Hard Disks\WindowsServer2016.vhdx" -SwitchName "SDNvSwitch" 
    
   Set-VM -Name "MyVM" -ProcessorCount 4
    
   Set-VMNetworkAdapter -VMName "MyVM" -StaticMacAddress "00-11-22-33-44-55" 
   ```

2. Получите виртуальную сеть, содержащую подсеть, к которому вы хотите подключить сетевой адаптер.

   ```Powershell 
   $vnet = get-networkcontrollervirtualnetwork -connectionuri $uri -ResourceId “Contoso_WebTier”
   ```

3. Создает объект интерфейса сети на сетевом контроллере.

   >[!TIP]
   >На этом шаге используется настраиваемый список управления Доступом.

   ```PowerShell
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
   ```

4. Получите идентификатор экземпляра для сетевого интерфейса из сетевого контроллера.

   ```PowerShell 
    $nic = Get-NetworkControllerNetworkInterface -ConnectionUri $uri -ResourceId "MyVM-Ethernet1"
   ```

5. Устанавливает идентификатор интерфейса на виртуальной Машине Hyper-V портов сетевого адаптера.

   >[!NOTE]
   >Эти команды необходимо запустить на узле Hyper-V установки виртуальной Машины.

   ```PowerShell 
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
   ```

6. Запустите виртуальную Машину.

   ```PowerShell
    Get-VM -Name “MyVM” | Start-VM 
   ```

Вы успешно создали виртуальную Машину, к виртуальной Машине клиента виртуальной сети и к работе виртуальную Машину, чтобы он мог обрабатывать рабочие нагрузки клиентов.

## <a name="create-a-vm-and-connect-to-a-vlan-by-using-networkcontrollerrestwrappers"></a>Создать виртуальную Машину и подключитесь к виртуальной локальной сети с помощью NetworkControllerRESTWrappers


1. Создайте виртуальную Машину и назначьте статический MAC-адрес виртуальной Машины.

   ```PowerShell
   New-VM -Generation 2 -Name "MyVM" -Path "C:\VMs\MyVM" -MemoryStartupBytes 4GB -VHDPath "c:\VMs\MyVM\Virtual Hard Disks\WindowsServer2016.vhdx" -SwitchName "SDNvSwitch" 

   Set-VM -Name "MyVM" -ProcessorCount 4

   Set-VMNetworkAdapter -VMName "MyVM" -StaticMacAddress "00-11-22-33-44-55" 
   ```

2. Устанавливает идентификатор виртуальной ЛС на сетевом адаптере виртуальной Машины.

   ```PowerShell
   Set-VMNetworkAdapterIsolation –VMName “MyVM” -AllowUntaggedTraffic $true -IsolationMode VLAN -DefaultIsolationId 123
   ```

3. Получите логической подсети и создайте сетевой интерфейс. 

   ```PowerShell
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
   ```

4. Значение InstanceId на порт Hyper-V.

   ```PowerShell  
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
   ```

5. Запустите виртуальную Машину.

   ```PowerShell
   Get-VM -Name “MyVM” | Start-VM 
   ```

Вы успешно создали виртуальную Машину, к виртуальной Машине в виртуальной локальной сети и к работе виртуальную Машину, чтобы он мог обрабатывать рабочие нагрузки клиентов.

  

