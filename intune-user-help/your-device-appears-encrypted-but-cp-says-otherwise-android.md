---
title: 你的 Android 设备似乎已加密 | Microsoft Docs
description: 解析公司门户和 Microsoft Intune 应用中的加密状态
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/14/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ba593c08-1a78-4013-8525-b45a948772ec
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 13f22b66b5a0700eadda28b20e0db6edce507021
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2019
ms.locfileid: "71721167"
---
# <a name="device-encrypted-but-apps-say-otherwise"></a>设备已加密，但应用以其他方式

如果公司门户或 Microsoft Intune 应用说你的设备未加密，但你确定是，请尝试本文中的步骤。  

## <a name="add-a-startup-pin"></a>添加启动 PIN

某些 Android 设备需要创建启动 PIN，确保设备安全。 此设置的位置将在设备的 "**设置**" 应用中。 设置的名称和位置可能会有所不同。 例如，在 Samsung Galaxy S7 上，此设置称为 "**安全启动**"。 若要启用和创建密码，请在 "**设置**"  > **锁屏界面和安全** >  "**安全启动**"。  

## <a name="encrypt-the-entire-device"></a>加密整个设备

本部分仅适用于公司门户应用。 某些设备支持选择加密整个设备或仅加密已用空间。 选择加密整个设备的选项。 如果选择仅加密已用空间，则：

1. [从公司门户中删除此设备](unenroll-your-device-from-intune-android.md)。
2. 解密已用空间。  
3. 加密整个设备。  
4. 重新注册设备。  

## <a name="downgrade-your-version-of-android"></a>降级 Android 版本

本部分仅适用于公司门户应用。 如果设备提供降级到 Android 6.0 及更高版本的选项，请进行降级。 如果尝试进行设备降级，将存在数据丢失的风险。 若要避免此风险，建议联系公司支持人员解决此问题。 在[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)上获取公司支持人员的联系信息。  

## <a name="specific-manufacturer-issues"></a>特定制造商问题

一些 Android 设备（版本 7.0 及更高版本）会以与某些 Android 平台标准不同的方式加密数据。 这些加密方法将设备信息置于风险之中。 因此，这些设备不受支持。

有关受支持的 Android 设备的非详尽列表，请参阅[在 Intune 中支持的操作系统和浏览器](https://docs.microsoft.com/intune/fundamentals/supported-devices-browsers#supported-samsung-knox-standard-devices)一文。 如果未列出你的设备，请参阅设备制造商，或与你的支持人员联系。

> [!Note]
> Microsoft 将与制造商协作以解决我们在测试中发现的，或用户上报的任何问题。 每当有新的信息可用时，我们会更新本文。

## <a name="update-devices"></a>更新设备

如果尚未将设备更新到最新版本的 Android，请访问设备的 "**设置**" 应用，并选择 "**更新**"。  

## <a name="next-steps"></a>后续步骤

仍需帮助？ 请联系公司支持人员（访问[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)获取联系信息），或写邮件给 <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">Microsoft Android 团队</a>。  
