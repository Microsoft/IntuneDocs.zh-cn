---
title: 在 Microsoft Intune 中配置终结点保护设置 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中创建 macOS 或 Windows 10 设备配置文件时，创建终结点保护设置。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
mr.reviewer: karthib
ms.openlocfilehash: 13e8c7fd0c822a2bdfbf7c183ea6752f99cf7991
ms.sourcegitcommit: d2ac912b834c4840de9cc92ba1815b6ecfbfb52b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/25/2019
ms.locfileid: "68482774"
---
# <a name="add-endpoint-protection-settings-in-intune"></a>在 Intune 中添加终结点保护设置  

使用 Intune，可以使用设备配置文件来管理设备上的公共终结点保护安全功能，包括：  
- 防火墙   
- BitLocker  
- 允许和阻止应用  
- Windows Defender 和加密  

例如，可以创建一个终结点保护配置文件，仅允许 macOS 用户安装来自 Mac App Store 的应用。 或者在 Windows 10 设备上运行应用时启用 Windows SmartScreen。  

在创建配置文件之前，请查看详细介绍 Intune 可以针对每个支持平台管理的终结点保护设置的以下文章：  
   - [macOS 设置](endpoint-protection-macos.md)  
   - [Windows 10 设置](endpoint-protection-windows-10.md)  

## <a name="create-a-device-profile-containing-endpoint-protection-settings"></a>创建包含终结点保护设置的设备配置文件  

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。  
3. 选择“设备配置” > “配置文件” > “创建配置文件”    。  
4. 输入终结点保护配置文件的“名称”和“描述”   。  
5. 从“平台”  下拉列表中，选择要应用自定义设置的设备平台。 目前，可以为设备限制设置选择以下平台之一：  
   - **macOS**  
   - **Windows 10 及更高版本**  
6. 在“配置文件类型”  下拉列表中，选择“Endpoint Protection”  。  
7. 根据所选择的平台，可配置的设置有所不同。 请参阅：  
   - [macOS 设置](endpoint-protection-macos.md)  
   - [Windows 10 设置](endpoint-protection-windows-10.md)  

8. 配置适用的设置后，选择“创建配置文件”页上的“创建”   。  

   配置文件随即创建并显示在“配置文件列表”页中。 要向组分配此配置文件，请参阅[分配设备配置文件](device-profile-assign.md)。  

## <a name="add-custom-firewall-rules-for-windows-10-devices"></a>为 Windows 10 设备添加自定义防火墙规则  
***公共预览版提供自定义防火墙规则。***  

在将 Windows Defender 防火墙配置为包含 Windows 10 Endpoint Protection 规则的配置文件的一部分后，可以为防火墙配置自定义规则。 通过自定义规则，可以扩展 Windows 10 支持的预定义防火墙规则集。  

在计划使用带自定义防火墙规则的配置文件时，请考虑以下信息，这些信息可能会影响在配置文件中对防火墙规则进行分组的方式：  
- 每个配置文件最多支持 150 个防火墙规则。 使用超过 150 个规则时，请创建其他配置文件，每个配置文件限制为 150 个规则。  
- 对于每个配置文件，如果单个规则无法使用，则该配置文件中的所有规则都无法使用，并且不会将任何规则应用于设备。  
- 如果某个规则无法使用，则配置文件中的所有规则都将报告为无法使用。 Intune 无法识别哪个单独的规则无法使用。  

Windows [防火墙配置服务提供程序]( https://docs.microsoft.com/windows/client-management/mdm/firewall-csp) (CSP) 中详细介绍了 Intune 可以管理的防火墙规则。 若要查看 Intune 支持的 Windows 10 设备自定义防火墙设置列表，请参阅[自定义防火墙规则](endpoint-protection-windows-10.md#firewall-rules)。  

### <a name="to-add-custom-firewall-rules-to-an-endpoint-protection-profile"></a>向 Endpoint Protection 配置文件添加自定义防火墙规则  

1. 在 Intune 中，转到“设备配置” > “配置文件” > “创建配置文件”    。  

2. 对于“平台”，请依次选择“Windows 10 及更高版本”、“配置文件类型”、“Endpoint Protection”     。  

3. 选择“Windows Defender 防火墙”以打开配置页，对于“防火墙规则”，选择“添加”以打开“创建规则”页     。  

4. 指定“防火墙规则”的设置，然后选择“确定”以保存该设置  。 若要查看文档中可用的自定义防火墙规则选项，请参阅[自定义防火墙规则](endpoint-protection-windows-10.md#firewall-rules)。  

5. 保存规则后，它将显示在规则列表中的“Windows Defender 防火墙”页上  。  

6. 若要修改规则，请从列表中选择规则，以打开“编辑规则”页  。  

7. 若要从配置文件中删除规则，请选择规则的省略号“(…)”，然后选择“删除”  。  

8. 若要更改规则的显示顺序，请选择规则列表顶部的向上箭头、向下箭头图标  。  


## <a name="next-steps"></a>后续步骤  

要向组分配配置文件，请参阅[分配设备配置文件](device-profile-assign.md)。  
