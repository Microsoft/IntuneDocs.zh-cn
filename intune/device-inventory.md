---
title: 使用 Microsoft Intune 查看设备详细信息 - Azure | Microsoft Docs
description: 查看设备的详细信息，包括操作系统、存储空间、制造商和型号。 在 Azure 的 Microsoft Intune 中获取已安装应用的列表、检查符合性策略和设置 TeamViewer。 类似于查看管理设备的清单。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f66c0695c7e3d1f4bb7a5ca3abceeb13f6af41f2
ms.sourcegitcommit: 3c4ea8d6809a63042705b5ed4f25ba80f522070e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/11/2018
---
# <a name="see-device-details-in-intune"></a>在 Intune 中查看设备详细信息

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

“设备”功能可提供管理设备的其他详细信息，包括其硬件和已安装的应用。

本文介绍如何在 Azure 门户中查看所有设备及其属性。

## <a name="view-the-device-details"></a>查看设备详细信息

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
3. 选择“设备” > “所有设备”，然后选择某个列出的设备以打开其详细信息：

   - “概述”显示设备名称，并列出设备的某些关键属性，包括该设备是否是自带设备办公 (BYOD) 设备和设备的签入时间等。 选择“更多”还可以：
     - 删除公司数据
     - 删除设备
     - 远程锁定设备
     - 擦除
     - 开始远程协助会话
   - 使用“属性”可以将设备分配到[你创建的设备类别](device-group-mapping.md)，并将设备的所有权更改为个人设备或公司设备。
   - “硬件”包括设备的许多详细信息，包括设备 ID、操作系统和版本、存储空间、型号和制造商、条件访问设置等详细信息。
   - “发现的应用”列出 Intune 发现的安装在设备上的所有应用以及应用版本。 还可以将应用列表导出到 .csv 文件中。
   - “设备符合性”列出分配到的所有符合性策略，以及设备是否符合要求。
   - “设备配置”显示分配给该设备的所有设备配置策略，以及该策略成功还是失败。

Intune 仅收集公司拥有的设备上的应用列表。 不检查个人设备上的应用。 对于 Windows 10 电脑，仅列出公司拥有的设备上的新型应用。 Intune 不会收集设备上的 Win32 应用的相关信息。 根据设备使用的运营商，可能并不会收集所有应用。

|平台|个人拥有设备|公司拥有设备|  
|--------------|---------------------------------|--------------------------------|  
|Windows 10（不带 Configuration Manager 客户端）|仅托管应用|仅托管应用|
|Windows 8.1（不带 Configuration Manager 客户端）|仅托管应用|仅托管应用|  
|Windows Phone 8|仅托管应用|仅托管应用|  
|Windows RT|仅托管应用|仅托管应用|  
|iOS|仅托管应用|设备上安装的所有应用|
|macOS|设备上安装的所有应用|设备上安装的所有应用|  
|Android|仅托管应用|设备上安装的所有应用|  

## <a name="next-steps"></a>后续步骤
了解使用 Intune [管理设备](device-management.md)还可以执行哪些操作。