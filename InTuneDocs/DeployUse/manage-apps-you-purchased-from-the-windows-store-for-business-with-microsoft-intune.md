---
# required metadata

title: 管理从适用于企业的 Windows 应用商店中购买的应用 | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8e38d47d-0c5e-40ce-b379-29d3657f5c28

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 使用 Microsoft Intune 管理从适用于企业的 Windows 应用商店中购买的应用
你可以在[适用于企业的 Windows 应用商店](https://www.microsoft.com/business-store)中为你的组织查找和购买应用，可以购买单个或批量购买。 通过将此应用商店连接到 Microsoft Intune，你可以在 Intune 控制台管理批量购买的应用，例如：
* 你可以将从应用商店中购买的应用列表与 Intune 同步。
* 在 Intune 管理控制台中将显示已同步的应用，并且你可以像部署任何其他应用那样部署这些应用
* 你可以在 Intune 管理控制台中跟踪有多少许可证可用以及使用了多少个
* 如果没有足够的许可证可用，Intune 将阻止部署和安装应用程序

## 开始之前
从适用于企业的 Windows 应用商店同步并部署应用之前，请查看以下信息：
* 你必须将 Intune 配置为你的组织的移动设备管理机构。 有关详细信息，请参阅[为在 Microsoft Intune 中注册设备做好准备](get-ready-to-enroll-devices-in-microsoft-intune.md)
* 你必须已经在适用于企业的 Windows 应用商店中注册一个帐户
* 一旦将适用于企业的 Windows 应用商店帐户与 Intune 关联，将来你将无法更改为其他帐户。
* 无法在 Intune 中手动添加或删除从应用商店购买的应用。 这些应用只能与适用于企业的 Windows 应用商店同步。
* Intune 只同步你已从适用于企业的 Windows 应用商店中购买的联机已授权应用。
* 设备必须已加入 Active Directory 域或加入工作区才可使用此功能。
* 已注册的设备必须使用 Windows 10 的 1511 版本。

## 将适用于企业的 Windows 应用商店帐户与 Intune 相关联
在 Intune 控制台中启用同步之前，必须将你的应用商店帐户配置为将 Intune 作为一种管理工具使用：
1. 确保使用与登录 Intune 相同的租户帐户登录企业应用商店。
2. 在企业应用商店中，选择**设置** > **管理工具**。
3. 在管理工具页上选择“添加管理工具”，然后选择“Microsoft Intune”。

现在可以继续，并在 Intune 控制台中设置同步。

## 配置同步

1. 在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)中，单击**管理**。
2. 在**管理**工作区中，展开**移动设备管理**，然后单击**适用于企业的应用商店**。
3. 在“适用于企业的 Windows 应用商店”页上，执行以下操作：
* 如果尚未这样做，请单击适用于企业的 Windows 应用商店的注册链接
* 一旦你已注册，请单击“配置同步”
4. 在**配置适用于企业的 Windows 应用商店的应用同步**对话框中，选择**启用适用于企业的 Windows 应用商店同步**。
5. 在“语言”下拉列表中，选择适用于企业的 Windows 应用商店的应用在 Intune 控制台中显示时使用的语言。 无论以何种语言显示，都会以最终用户的语言（如果有）进行安装。
6. 单击" **确定**"。

## 同步应用

1. 在“适用于企业的 Windows 应用商店”页上，单击“立即同步”即可将从应用商店购买的应用与 Intune 同步。
2. 在“应用”工作区中，单击“托管软件” > “许可软件”可查看可用的应用，并验证是否已正确导入已购买的应用。
该节点中的应用还显示你所拥有的许可证总数，以及你已使用的许可证数量。

## 部署应用

部署应用商店中应用的方式与部署任何其他 Intune 应用的方式相同。 有关详细信息，请参阅[在 Microsoft Intune 中部署应用](deploy-apps-in-microsoft-intune.md)。
部署适用于企业的 Windows 应用商店的应用时，安装此应用的每个用户都会使用一个许可证。 如果使用了部署应用的所有可用的许可证，则你将无法再部署任何副本，并且必须执行下列操作之一：
* 从一些设备上卸载应用
* 减小当前部署的范围，仅针对具有足够许可证的用户
* 从适用于企业的 Windows 应用商店中购买应用的更多副本


### 另请参阅
[在 Microsoft Intune 中为移动设备添加应用](add-apps-for-mobile-devices-in-microsoft-intune.md)




<!--HONumber=May16_HO2-->


