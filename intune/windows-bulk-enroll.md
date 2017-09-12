---
title: "Windows 10 的批量注册"
titlesuffix: Azure portal
description: "为 Microsoft Intune 创建批量注册包"
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 06/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: damionw
ms.custom: intune-azure
ms.openlocfilehash: 3e374f383275b1e74e22ac037ecaec282eeaa87c
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/09/2017
---
# <a name="bulk-enrollment-for-windows-devices"></a>Windows 设备的批量注册

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

作为管理员，可以将大量新的 Windows 设备加入到 Azure Active Directory 和 Intune。 若要为你的 Azure AD 租户批量注册设备，可以使用 Windows 配置设计器 (WCD) 应用来创建配置包。 将配置包应用于企业拥有的设备可将设备加入到你的 Azure AD 租户并为其注册 Intune 管理。 应用此包后，即可供你的 Azure AD 用户登录。

Azure AD 用户是这些设备上的标准用户并接收分配的 Intune 策略和必需的应用。 目前不支持自助服务和公司门户方案。

## <a name="prerequisites-for-windows-devices-bulk-enrollment"></a>Windows 设备批量注册的先决条件

Windows 设备的批量注册需要以下条件：

- 运行 Windows 10 创意者更新或更高版本的设备
- [Windows 自动注册](https://docs.microsoft.com/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune#enable-windows-10-automatic-enrollment)

## <a name="create-a-provisioning-package"></a>创建预配包

1. 从 Microsoft 应用商店下载 [Windows 配置设计器 (WCD)](https://www.microsoft.com/store/apps/9nblggh4tx22)。
![Windows 配置设计器应用应用商店屏幕快照和说明的屏幕快照](media/bulk-enroll-store.png)

2. 打开“Windows 配置设计器”应用，然后选择“配置桌面设备”。
![在 Windows 配置设计器应用中选择配置桌面设备的屏幕快照](media/bulk-enroll-select.png)

3. 将打开一个“新项目”窗口，在此处指定以下信息：
  - **名称** - 你的项目的名称
  - **项目文件夹** - 新项目保存的位置
  - **说明** - 项目的可选说明![在 Windows 配置设计器应用中指定名称、项目文件夹和说明的屏幕快照](media/bulk-enroll-name.png)

4.  输入设备的唯一名称。 名称可以包含序列号 (%%SERIAL%%) 或一组随机的字符。 （可选）如果正在升级 Windows 版本，还可以输入产品密钥、将设备配置为共享以及删除预安装的软件。
![在 Windows 配置设计器应用中指定名称、项目文件夹和说明的屏幕快照](media/bulk-enroll-device.png)

5.  （可选）可以配置 Wi-Fi 网络设备首次启动时所连接到的网络。  如未配置此项，则在设备首次启动时，需要有线网络连接。
![在 Windows 配置设计器应用中启用包括网络 SSID 和网络类型选项的 Wi-Fi 的屏幕快照](media/bulk-enroll-network.png)

6.  选择“在 Azure AD 中注册”，输入“批量令牌到期”日期，然后选择“获取批量令牌”。
![在 Windows 配置设计器应用中指定名称、项目文件夹和说明的屏幕快照](media/bulk-enroll-account.png)

7. 提供你的 Azure AD 凭据，以获取批量令牌。
![在 Windows 配置设计器应用中指定名称、项目文件夹和说明的屏幕快照](media/bulk-enroll-cred.png)

8.  成功提取“批量令牌”后，单击“下一步”。

9. （可选）可以“添加应用程序”和“添加证书”。 将在此设备上配置应用和证书。

10. （可选）还可以使用密码保护你的配置包。  单击“创建”。
![在 Windows 配置设计器应用中指定名称、项目文件夹和说明的屏幕快照](media/bulk-enroll-create.png)

## <a name="provision-devices"></a>配置设备

1. 在应用中所指定的“项目文件夹”中访问指定位置的配置包。

2. 选择向设备应用配置包的方式。  可使用以下方法之一向设备应用配置包：
 - 将配置包置于 USB 驱动器，将 USB 驱动器插入想要进行批量注册的设备，并在初始设置时应用它
 - 将配置包置于网络文件夹，并在初始设置后将其应用于想要进行批处理注册的设备上

 有关应用配置包的分步说明，请参阅[应用配置包](https://technet.microsoft.com/itpro/windows/configure/provisioning-apply-package)。

3. 应用配置包后，设备将在 1 分钟后自动启动。
 ![在 Windows 配置设计器应用中指定名称、项目文件夹和说明的屏幕快照](media/bulk-enroll-add.png)

4. 设备重新启动时，将连接到 Azure Active Directory 并在 Microsoft Intune 中注册。

## <a name="troubleshooting-windows-bulk-enrollment"></a>Windows 批量注册的疑难解答

### <a name="provisioning-issues"></a>设置问题
配置旨在用于新的 Windows 设备上。 配置失败可能需要对设备进行恢复出厂设置或通过启动映像来恢复设备。 这些示例描述了配置失败的一些原因：

- 如果因为缺少网络连接导致域加入过程失败，则尝试加入 Active Directory 域或不创建本地帐户的 Azure Active Directory 租户的配置包可能会使设备无法访问。
- 通过配置包运行的脚本在系统上下文中运行，能够对设备文件系统和配置进行任意更改。 恶意或不正确的脚本可将设备置于仅能通过重置映像或恢复出厂设置才能将其恢复的状态。

### <a name="problems-with-bulk-enrollment-and-company-portal"></a>有关批量注册和公司门户的问题
如果用户尝试使用公司门户注册之前曾批量注册的设备，会收到警告，指示其设备需要执行进一步操作，如设置或注册。 设备已注册，但公司门户应用或站点不识别此注册。

### <a name="conditional-access"></a>条件性访问
条件性访问不适用于使用批量注册登记的 Windows 设备。
