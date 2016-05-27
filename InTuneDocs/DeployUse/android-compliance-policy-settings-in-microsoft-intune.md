---
# required metadata

title: 适用于 Android 设备的合规性策略设置 | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e721c5c7-9678-4f3b-81d4-564da5efd337

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Microsoft Intune 中适用于 Android 设备的合规性策略设置

本主题中描述的策略设置适用于运行 Android 4.0 及更高版本或 Samsung KNOX 4.0 及更高版本的设备。

如果你要查找有关其他平台的信息，请选择以下选项之一：
> [!div class="op_single_selector"]
- [适用于 iOS 设备的合规性策略设置](ios-compliance-policy-settings-in-microsoft-intune.md)
- [适用于 Windows 设备的合规性策略设置](windows-compliance-policy-settings-in-microsoft-intune.md)

## 系统安全设置
### Password
- **需要密码以解锁移动设备：**将此选项设置为“是”以要求用户输入密码后

-  才能访问其设备。

- **最短密码长度：**指定用户密码必须包含的最小位数或最小字符数。 **密码质量：**启用此设置以配置 Android 设备的密码要求。
  -   **选择：**
  - **低安全性生物识别**
  -   **必需**
  -   **最少数字**
  -   **最少字母**
  -   **至少为字母数字**

- 包含符号的字母数字

- **需要提供密码之前须经历的无活动分钟数：**指定用户必须重新输入其密码前的空闲时间。

- **密码过期（天数）：**选择用户的密码过期之前的天数

- 而且他们必须创建一个新的密码。

- **记住密码历史记录：**将此设置与“防止重用以前的密码”结合使用，以限制用户 创建以前用过的密码。

### **防止重用以前的密码：**如果选择了“记住密码历史记录”，请指定
- 不能重复使用的以前所用密码的数量。 当设备从空闲状态返回时需要密码：

## 此设置应该与“需要提供密码之前处于非活动状态的分钟数”设置一起使用。

- 设备在“需要提供密码之前须经历的无活动分钟数”

## 设置指定的时间内处于非活动状态时，将提示最终用户输入密码才能访问设备。
- Encryption
  **需要对移动设备进行加密：**将此选项设置为“是”以 进行加密以连接到资源。

- 当配置设置 “需要密码以解锁移动设备”**
  **时，设备将加密


<!--HONumber=May16_HO2-->


