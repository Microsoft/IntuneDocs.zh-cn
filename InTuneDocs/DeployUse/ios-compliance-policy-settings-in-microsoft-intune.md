---
# required metadata

title: 适用于 iOS 设备的合规性策略设置 | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 4a59d24f-ed58-49b1-b874-b2d4aea3ec76

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Microsoft Intune 中适用于 iOS 设备的合规性策略设置

本主题中描述的策略设置适用于运行 iOS 6 及更高版本的设备。

如果你要查找有关其他平台的信息，请选择以下选项之一：
> [!div class="op_single_selector"]
- [适用于 Android 设备的合规性策略设置](android-compliance-policy-settings-in-microsoft-intune.md)
- [适用于 Windows 设备的合规性策略设置](windows-compliance-policy-settings-in-microsoft-intune.md)

## 系统安全设置
### Password
- **需要密码才可解锁移动设备：**    将其设置为“是”以要求用户必须输入密码 才能访问其设备。

- 使用密码的 iOS 设备已加密。

-  **允许简单密码：**    将此设置
- 为“是”以允许用户创建简单密码

- 如“**1234**”或“**1111**”。 最短密码长度：
  -   指定用户的密码必须包含的
  -   最少数字或字符数。
  -   **所需的密码类型：**指定用户是否必须创建
  -   **字母数字**密码还是**数字**密码。

  **最小字符集数：**如果“所需的密码类型”设置为

  “字母数字”，则使用此设置指定
- 密码必须包含的最小字符集数。

- 四个字符集为：

- 小写字母

- 大写字母

- 符号 数字

### 为此设置设置较大的数字将要求用户创建更复杂的密码。
- 对于 iOS 设备，此设置是指必须包括在密码中的特殊字符数（例如 !、#、&amp;）。 **需要提供密码之前处于非活动状态的分钟数：**指定用户必须重新输入其密码前的空闲时间。
  - **密码过期（天数）：**选择用户的密码过期之前的天数
  - 而且他们必须创建一个新的密码。 **记住密码历史记录：**将此设置与“防止重用以前的密码”结合使用，以限制用户 创建以前用过的密码。


- **防止重用以前的密码：**如果选择了“记住密码历史记录”，请指定 不能重复使用的以前所用密码的数量。

     当设备从空闲状态返回时需要密码：

## 此设置应该与“需要提供密码之前处于非活动状态的分钟数”设置一起使用。

- 如果设备在“需要提供密码之前处于非活动状态的分钟数”设置

##  设置指定的时间内处于非活动状态时，将提示最终用户输入密码才能访问设备。
- 电子邮件配置文件
**必须由 Intune 管理电子邮件帐户：**如果该选项设置为“是”，则设备必须使用部署到设备的不符合要求的电子邮件。 在以下情况中设备被视为不符合要求：

- 必须将电子邮件配置文件部署到与合规性策略所针对的用户组相同的用户组，否则用户的设备将被视为不符合要求。 如果用户已在设备上设置了电子邮件帐户，并且该帐户匹配部署到设备上的 Intune 电子邮件配置文件，那么设备将被报告为不符合要求。


<!--HONumber=May16_HO2-->


