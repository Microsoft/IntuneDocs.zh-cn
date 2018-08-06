---
title: 在 Microsoft Intune 中启用 eSIM 数据连接 - Azure | Microsoft Docs
description: 添加或使用 eSIM 以通过不同的流量套餐获取 Internet 和数据访问权限。 在 Intune 中，添加或导入激活码，然后使用配置文件分配这些激活码。 还可以监视 eSIM 配置文件并检查已启用 eSIM 的设备的状态。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 7/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ac3bbb4a32e86d756835d136cd3923676f022a7b
ms.sourcegitcommit: 0d08daa162212e6cdd8a6ee3ad7ed42c6e6824e4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2018
ms.locfileid: "39336016"
---
# <a name="configure-esim-cellular-profiles-in-intune---public-preview"></a>在公开预览版的 Intune 中配置 eSIM 手机网络配置文件

> [!NOTE]
> Microsoft 希望收到你的反馈。 通过向 `eSIMonIntune@microsoft.com` 发送电子邮件发送问题或开始讨论。

## <a name="introduction"></a>简介

eSIM 是一种嵌入式 SIM 芯片，可让你通过支持 eSIM 的设备（如 [Surface LTE Pro](https://www.microsoft.com/surface/business/surface-pro)）上的手机网络数据连接连接到 Internet。 使用 eSIM，你无需从移动运营商处获取 SIM 卡，并且可以在移动运营商和流量套餐之间快速切换。

例如，你有一个用于工作的手机网络流量套餐，还有另外一个私人使用的流量套餐，但由另一个移动运营商提供。 当你在旅行时，可以通过查找在该区域提供流量套餐的移动运营商来获取 Internet 访问权限。

在 Intune 中，可以导入移动运营商提供的一次性使用的激活码。 要在 eSIM 模块上配置手机网络流量套餐，请将这些激活码部署到支持 eSIM 的设备。 当 Intune 安装激活码时，eSIM 硬件模块会使用激活码中的数据联系移动运营商。 完成后，eSIM 配置文件将下载到设备上，并配置为激活手机网络。

要使用 Intune 将 eSIM 部署到设备，需要以下条件：

- 支持 eSIM 的设备（如 Surface LTE）：请参阅[设备是否支持 eSIM](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data)。 或者，请参阅[一些已知支持 eSIM 的设备](#esim-capable-devices)的列表（在本文中）。
- 已注册并且由 Intune 托管 MDM 的 Windows 10 Fall Creators Update PC（1709 或更高版本）
- 移动运营商提供的激活码。 这些一次性使用的激活码被添加到 Intune，并部署到支持 eSIM 的设备。 请联系移动运营商获取 eSIM 激活码。

## <a name="deploy-esim-to-devices---overview"></a>将 eSIM 部署到设备 - 概述

要将 eSIM 部署到设备，管理员需完成以下任务：

1. 导入移动运营商提供的激活码
2. 创建 Azure Active Directory (Azure AD) 设备组，将支持 eSIM 的设备包含在内
3. 将 Azure AD 组分配给已导入的订阅池
4. 监视部署

本文将指导你完成这些步骤。

## <a name="esim-capable-devices"></a>支持 eSIM 的设备

以下设备已宣布支持 eSIM 或已在市场上销售。 另外，请检查[设备是否支持 eSIM](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data)。

- Acer Swift 7
- Asus NovoGo TP370QL
- Asus TP401
- Asus Transformer Mini T103
- HP Elitebook G5
- HP Envy x2
- HP Probook G5
- Lenovo Miix 630
- Lenovo T480
- Samsung Galaxy Book
- Surface Pro LTE

## <a name="step-1-add-cellular-activation-codes"></a>步骤 1：添加手机网络激活码

移动运营商在以逗号分隔的文件 (csv) 中提供手机网络激活码。 如果有此文件，请使用以下步骤将其添加到 Intune：

1. 登录到 [Azure 门户](https://portal.azure.com/)。
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
3. 选择“设备配置” > “eSIM 手机网络配置文件” > “添加”。
4. 选择具有激活码的 CSV 文件。
5. 选择“确定”，保存所做更改。

#### <a name="csv-file-requirements"></a>CSV 文件要求

使用具有激活码的 csv 文件时，请确保你或你的移动运营商遵循以下要求：

- 该文件必须采用 csv 格式 (filename.csv)。
- 文件结构必须严格遵循格式要求。 否则，会导入失败。 Intune 在导入时检查文件，并且如果发现错误则会失败。
- 激活码为一次性使用。 建议不要导入先前导入过的激活码，因为在部署到相同或不同的设备时可能会导致问题。
- 每个文件应特定于单个移动运营商，并且所有激活码应特定于同一计费套餐。 Intune 将激活码随机分配给目标设备。 无法保证哪个设备会获得特定的激活码。
- 一个 csv 文件中最多可以导入 1000 个激活码。

#### <a name="csv-file-example"></a>CSV 文件示例

1. csv 的第一行和第一个单元格是移动运营商 eSIM 激活服务的 URL，称为 SM-DP +（订阅管理器数据准备服务器）。 URL 应为完全限定的域名 (FQDN)，不带任何逗号。
2. 第二行和所有后续行都是包含两个值的唯一一次性使用的激活码：

    1. 第一列是唯一的 ICCID（SIM 芯片的标识符）
    2. 第二列是匹配的 ID，只用逗号分隔它们（末尾没有逗号）。 请参阅以下示例：

        ![移动运营商激活码示例 csv 文件](./media/esim-device-configuration/url-activation-code-examples.png)

3. csv 文件名将成为 Azure 门户中的手机网络订阅池名称。 在上图中，文件名为 `UnlimitedDataSkynet.csv`。 因此，Intune 将订阅池命名为 `UnlimitedDataSkynet.csv`：

    ![手机网络订阅池被命名为激活码示例 csv 文件名](./media/esim-device-configuration/subscription-pool-name-csv-file.png)

## <a name="step-2-create-an-azure-ad-device-group"></a>步骤 2：创建 Azure AD 设备组

创建包含支持 eSIM 的设备的设备组。 [添加组](groups-add.md)列出了相关步骤。

> [!NOTE]
> - 仅针对设备，不针对用户。
> - 我们建议创建包含 eSIM 设备的静态 Azure AD 设备组。 使用组即确认仅针对 eSIM 设备。

## <a name="step-3-assign-esim-activation-codes-to-devices"></a>步骤 3：将 eSIM 激活码分配给设备

将配置文件分配给包含 eSIM 设备的 Azure AD 组。

1. 在 [Azure 门户](https://portal.azure.com/)中，选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
2. 选择“设备配置” > “eSIM 手机网络” > “配置文件”。
3. 在配置文件列表中，选择要分配的 eSIM 手机网络订阅池，然后选择“分配”。
4. 选择“包括”组或“排除”组，然后选择组。

    ![包含要分配配置文件的设备组](./media/esim-device-configuration/include-exclude-groups.png)

5. 选择组时，会选择 Azure AD 组。 要选择多个组，请使用 Ctrl 键，然后选择组。
6. 完成后，“保存”更改。

eSIM 激活码为一次性使用。 Intune 在设备上安装激活码后，eSIM 模块会联系移动运营商以下载手机网络配置文件。 该联系人会完成将设备注册到移动运营商网络。

## <a name="step-4-monitor-deployment"></a>步骤 4：监视部署

#### <a name="review-the-deployment-status"></a>查看部署状态

分配配置文件后，可以监视订阅池的部署状态。

1. 登录到 [Azure 门户](https://portal.azure.com/)。
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
3. 选择“设备配置” > “eSIM 手机网络配置文件”。 随即会列出所有现有的 eSIM 手机网络订阅池。
4. 选择订阅，然后查看“部署状态”。

#### <a name="check-the-profile-status"></a>检查配置文件状态
创建设备配置文件后，Intune 会提供图形图表。 这些图表显示配置文件的状态，例如成功分配给设备，或配置文件是否显示冲突。

1. 选择“设备配置” > “eSIM 手机网络配置文件”> 选择现有订阅。
2. 在“概述”选项卡中，顶部图形图表显示分配给特定 eSIM 手机网络订阅池部署的设备数。

    它还显示分配了相同设备配置文件的其他平台的设备数量。

    Intune 显示针对设备的激活码的发送和安装状态。

    - 设备未同步：创建 eSIM 部署策略后，目标设备未联系 Intune
    - 激活挂起：Intune 在设备上主动安装激活码时的临时状态
    - 激活：激活码安装成功
    - 激活失败：激活码安装失败 - 请参阅故障排除指南。

#### <a name="view-the-detailed-device-status"></a>查看设备状态详情

可以监视和查看可在“设备状态”中查看的设备详细列表。**

1. 选择“设备配置” > “eSIM 手机网络配置文件”> 选择现有订阅。
2. 选择“设备状态”。 Intune 会显示有关设备的其他详细信息：

  - 设备名称：目标设备的名称
  - 用户：注册设备的用户
  - ICCID：设备上安装的激活码内的唯一代码，由移动运营商提供
  - 激活状态：设备上激活码的 Intune 发送和安装状态
  - 手机网络状态：由移动运营商提供的状态。 跟进移动运营商进行故障排除。
  - 上次签入时间：设备上次与 Intune 通信的日期

#### <a name="monitor-esim-profile-details-on-the-actual-device"></a>监视实际设备上的 eSIM 配置文件详细信息

1. 在设备上，打开“设置”>转到“网络和 Internet”。
2. 选择“手机网络” > “管理 eSIM 配置文件”
3. 此时会列出 eSIM 配置文件：

    ![在设备设置中查看 eSIM 配置文件](./media/esim-device-configuration/device-settings-cellular-profiles.png)

## <a name="remove-the-esim-profile-from-device"></a>从设备中删除 eSIM 配置文件

从 Azure AD 组中删除设备时，也会删除 eSIM 配置文件。 请务必：

1. 确认使用的是 eSIM 设备 Azure AD 组。
2. 转到 Azure AD 组，然后从组中删除该设备。
3. 当删除的设备联系 Intune 时，系统会评估更新的策略，并删除 eSIM 配置文件。

当用户取消注册设备时，或者在设备上运行[删除公司数据](devices-wipe.md#remove-company-data)或[重置设备远程操作](devices-wipe.md#factory-reset)时，也会删除 eSIM 配置文件。

> [!NOTE]
> 删除配置文件可能无法停止计费。 请联系移动运营商，检查设备的计费状态。

## <a name="best-practices--troubleshooting"></a>最佳实践和疑难解答

- 确保 csv 文件格式正确。 确认该文件不包含重复代码、多个移动运营商或不同的流量套餐。 请记住，每个文件对于移动运营商和手机网络流量套餐必须是唯一的。
- 创建仅包含目标 eSIM 设备的静态设备 Azure AD 组。
- 如果部署状态存在问题，请检查以下内容：
  - 文件格式不正确：请参阅“步骤 1：添加手机网络激活码”（在本文中），了解如何正确设置文件格式。
  - 手机网络激活失败，联系移动运营商：激活码可能无法在其网络中激活。 或者，配置文件下载和手机网络激活失败。

## <a name="next-steps"></a>后续步骤
[配置设备配置文件](device-profiles.md)