---
title: 使用 Microsoft Intune 管理 Windows Holographic 设备 - Azure | Microsoft Docs
description: 通过 Microsoft Intune 可以在运行 Windows Holographic for Business 的设备上完成各种任务，包括配置公司门户、创建符合性策略、自定义 OMA-URI 设置、部署应用、将设备分类为组、创建配置文件、限制设备、进行软件更新、设置条款和条件、配置 VPN 和 Wi-Fi 设置，以及使用 Windows Hello 企业版。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 4/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 41c1ea3bf12b83a0f09c8535275ffb58e5f46931
ms.sourcegitcommit: b727b6bd6f138c5def7ac7bf1658068db30a0ec3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/06/2018
---
# <a name="customize-devices-running-windows-holographic-with-intune"></a>使用 Intune 对运行 Windows Holographic 的设备进行自定义设置

Microsoft Intune 支持运行 Windows Holographic for Business 的设备，例如 [Microsoft HoloLens](https://docs.microsoft.com/en-us/hololens/)。

若要使用 Microsoft Intune 管理运行 Windows Holographic 的设备，必须创建一个 Edition Upgrade 配置文件。 此升级配置文件能将设备从 Windows Holographic 升级至 Windows Holographic for Business。 对于 Microsoft HoloLens，则可以通过购买商业套件来获得升级所需的许可证。 有关详细信息，请参阅[将运行 Windows Holographic 的设备升级到 Windows Holographic for Business](holographic-upgrade.md)。

本文中的任务可帮助你管理和自定义运行 Windows Holographic for Business 的设备。 例如，你可以管理软件更新、配置 VPN 设置以及进行其他操作。

## <a name="company-portal"></a>Company Portal
**[配置公司门户应用](company-portal-app.md)**

Intune 中包含了公司门户，用户可在此访问公司数据、注册设备、安装应用、联系 IT 部门等。 你可以为运行 Windows Holographic for Business 的设备自定义公司门户应用。

## <a name="compliance-policy"></a>合规性策略
**[创建设备符合性策略](compliance-policy-create-windows.md)**

符合性策略即设备为符合要求必须满足的规则和设置。 可以将这些策略与条件访问结合使用，从而阻止不符合要求的设备访问公司资源。 在 Intune 中可以为运行 Windows Holographic for Business 的设备创建符合性策略，从而允许或阻止其访问权限。 例如，可以创建一个要求启用 Bitlocker 的策略。

另请参阅[设备符合性策略入门](device-compliance-get-started.md)。

## <a name="deploy-apps"></a>部署应用
**[向 Intune 添加应用](apps-add.md)**

使用 Intune 可以向运行 Windows Holographic for Business 的设备添加应用。 有多种部署应用的方法，包括：

- [添加 Microsoft Store 应用](store-apps-windows.md)
- [添加自己创建的应用](lob-apps-windows.md)
- [将应用分配给组](apps-deploy.md)

## <a name="device-categories-and-groups"></a>设备类别和组
**[将设备分类为组](device-group-mapping.md)**

使用 Intune 可以创建设备类别，例如销售、财务和人力资源等，并根据创建的类别将设备自动添加到组。 其目的是让管理运行 Windows Holographic for Business 的设备变得更轻松。

## <a name="device-configuration-profiles"></a>设备配置文件 
**[开始使用配置文件](device-profiles.md)并[创建自己的配置文件](device-profile-create.md)**

Intune 提供可在组织内的不同设备上启用或禁用的设置和功能。 这些设置和功能通过配置文件进行管理。 例如，可以创建一个在运行 Windows Holographic for Business 的设备上启用 Cortana 或使用 Windows Defender Smart Screen 的配置文件。

在配置文件中，可以使用 OMA-URI 来自定义某些设置、创建设备限制并配置虚拟专用网络 (VPN) 和 Wi-Fi。

#### <a name="custom-device-settingscustom-settings-windows-holographicmd"></a>[自定义设备设置](custom-settings-windows-holographic.md)

可通过在 Intune 中创建一个自定义配置文件来配置 OMA-URI（开放移动联盟统一资源标识符）设置。 可使用 OMA-URI 设置来控制 Windows Holographic for Business 设备上的各种功能，例如启用 VPN 或检查 Microsoft 更新上有无更新。

#### <a name="device-restrictionsdevice-restrictions-windows-holographicmd"></a>[设备限制](device-restrictions-windows-holographic.md)

通过设备限制可以控制设备上的各种设置和功能，包括要求提供密码、从 [Microsoft Store](https://www.microsoft.com/store/apps/windows?icid=CNavAppsWindowsApps) 安装应用以及启用蓝牙等。 应在 Intune 配置文件中创建这些限制。 此配置文件可应用于运行 Windows Holographic for Business 的多个设备。

#### <a name="configure-vpnvpn-settings-configuremd"></a>[配置 VPN](vpn-settings-configure.md)

虚拟专用网络 (VPN) 可让你的用户安全远程访问你的公司网络。 在 Intune 中可以创建 VPN 配置文件并使其包含针对运行 Windows Holographic for Business 的设备的特定设置。 例如可以创建一个 VPN 配置文件，让所有 Windows Holographic for Business 设备均使用 Citrix VPN 作为连接类型。

#### <a name="configure-wi-fiwi-fi-settings-configuremd"></a>[配置 Wi-Fi](wi-fi-settings-configure.md)

还可以在 Intune 中创建 Wi-Fi 配置文件，为 Windows Holographic for Business 设备分配无线网络设置。 分配 Wi-Fi 配置文件后，最终用户无需进行任何网络配置即可获得企业网络访问权限。 例如，可以创建一个仅供 Windows Holographic for Business 设备使用的 Wi-Fi 网络。

## <a name="software-updates"></a>软件更新
**[管理软件更新](windows-update-for-business-configure.md)**

Intune 提供了一个名为“更新圈”的功能供 Windows 10 设备使用。 这些更新圈包括一组用于确定更新安装方式的设置。 例如，你可以创建一个维护时段来安装更新，也可以选择在安装更新后重新启动。 更新圈可应用于运行 Windows Holographic for Business 的多个设备。

## <a name="terms-and-conditions"></a>条款和条件
**[设置公司的用户访问条款和条件](terms-and-conditions-create.md)**

可以要求用户先接受你所在公司的条款和条件，然后才能注册设备和访问公司应用，包括电子邮件。 在 Intune 中可以定义条款和条件在公司门户中的显示方式，并将这些条款和条件分配给运行 Windows Holographic for Business 的设备。

## <a name="windows-hello-for-business"></a>Windows Hello 企业版
**[使用 Windows Hello 企业版](windows-hello.md)**

Windows Hello 企业版是使用 Azure Active Directory 帐户取代密码、智能卡或虚拟智能卡进行登录的一种替代方法。 Windows Holographic for Business 可以与 Windows Hello 企业版配合使用，使用你设置的最短 PIN 进行登录。
