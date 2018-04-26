---
title: 将 Windows Holographic 升级为 Windows Holographic for Business
titleSuffix: Microsoft Intune
description: 了解如何将运行 Windows Holographic 的设备升级到 Windows Holographic for Business
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 08763aa527f24ff7b357603be5e3bd4da5083b45
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="upgrade-devices-running-windows-holographic-to-windows-holographic-for-business"></a>将运行 Windows Holographic 的设备升级到 Windows Holographic for Business


若要使用 Microsoft Intune 管理运行 Windows Holographic 的设备，必须将设备从 Windows Holographic 升级为 Windows Holographic for Business。 可创建版本升级配置文件来执行升级。 对于 Microsoft HoloLens，则可以通过购买商业套件来获得升级所需的许可证。 有关详细信息，请参阅[解锁 Windows Holographic for Business 功能](https://docs.microsoft.com/en-us/hololens/hololens-upgrade-enterprise)。

## <a name="to-set-up-an-edition-upgrade-device-configuration-profile"></a>设置“版本升级”设备配置文件

1. 使用管理员帐户登录 [Azure 门户](https://portal.azure.com)。


2.  依次单击“设备配置”、“配置文件”和“+ 创建配置文件”。

    ![创建配置文件](media/Holographic-create-profile.png)

3.  在“创建配置文件”页上，键入配置文件的名称，为平台选择“Windows 10 及更高版本”，然后为配置文件类型选择“版本升级”。 单击“设置配置”。

5. 在“版本升级”页上的“要升级到的版本”中，选择“Windows 10 Holographic for Business”。 在“许可证文件”上，浏览找到并选择系统提供的 XML 许可证文件。

    ![输入 XML 文件名](media/Holographic-edition-upgrade.png)
 
5.  单击“确定”，然后单击“创建”以创建配置文件。


## <a name="deploy-the-edition-upgrade-policy"></a>部署“版本升级”策略

接下来，将“版本升级”配置文件分配给所选组或设备。

1. 在前面步骤中创建的配置文件上，单击“分配”。

2. 在“分配”页上，选择想要使用该策略包括或排除的用户组和设备。

![包括和排除组](media/Holographic-groups.PNG)

在 Intune 中注册这些用户或设备时，将应用“版本升级”配置文件。 

## <a name="next-steps"></a>后续步骤

有关组的详细信息，请参阅[组入门](get-started-groups.md)。


