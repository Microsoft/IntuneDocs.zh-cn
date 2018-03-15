---
title: "Intune 向 Google 发送的数据"
titlesuffix: Azure portal
description: "Intune 向 Google 发送的数据列表。"
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a5c3bec4-18ed-11e8-accf-0ed5f89f718b
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d5f8c71115b8c3ee761fbc8d303f87e8aaabd5e1
ms.sourcegitcommit: 80a2eefc1896a42cc2bc16be23093d1abf58b088
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/27/2018
---
# <a name="data-intune-sends-to-google"></a>Intune 向 Google 发送的数据

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

当在设备上启用了 Android 设备管理时，Microsoft Intune 可与 Google 建立连接并与 Google 共享用户和设备信息。 必须先创建一个 Google 帐户，Microsoft Intune 才可建立连接。

下表列出了在设备上启用了设备管理时 Microsoft Intune 向 Google 发送的数据：


| 向 Google 发送的数据 | 详细信息 | 用途 | 示例 |
|:---:|:---:|:---:|:---:|
| 企业 ID | 在将 Gmail 帐户绑定到 Intune 时，源自 Google。 | 用于在 Intune 和 Google 之间进行通信的主要标识符。  此通信包括设置策略、管理设备以及将 Android 企业与 Intune 绑定/解除绑定。 | 唯一标识符，示例格式：LC04eik8a6 |
| 策略正文 | 在保存新应用或配置策略时，源自 Intune。 | 将策略应用于设备。 | 这是应用程序或配置策略的所有已配置设置的集合。 如果作为策略的一部分提供（例如网络名称、应用程序名称和特定于应用的设置），则可包含客户信息。 |
| 设备数据 | 对于用于工作配置文件的设备场景，从在 Intune 中注册开始。 对于用于托管设备的设备场景，从注册到 Google 开始。 | 设备数据信息在 Intune 和 Google 之间发送，用于各种操作，如应用策略、管理设备和常规报告。 | **表示设备名称的唯一标识符。** 示例：enterprises/LC04ebru7b/devices/3592d971168f9ae4<br>**表示用户名的唯一标识符。** 示例：Enterprises/LC04ebru7b/users/116838519924207449711<br>**设备状态。** 示例：活动、已禁用、预配。<br>**符合性状态。** 示例：设置不受支持、缺少必需应用<br>**软件信息。** 示例：软件版本和修补程序级别。<br>**网络信息。** 示例：IMEI、MEID、WifiMacAddress<br>**设备设置。** 示例：有关加密级别及设备是否允许未知应用的信息。<br> 有关 JSON 消息的示例，请参阅下文。 |
| newPassword | 源自 Intune。 | 重置设备密码。 | 表示新密码的字符串。 |
| Google 用户 | Google | 管理工作配置文件 (BYOD) 方案的工作配置文件。 | 表示链接的 Gmail 帐户的唯一标识符。 示例：114223373813435875042 |
| 应用程序数据 | 保存应用程序策略时，源自 Intune。 |  | 应用程序名称字符串。 示例：app:com.microsoft.windowsintune.companyportal |
| 企业服务帐户 | 在 Intune 请求时源自 Google。 | 用于针对涉及此客户的事务，在 Intune 和 Google 之间进行身份验证。 | 包括以下几个部分：<br> **企业 ID**：如前文所述。<br>**UPN**：生成的 UPN，用于代表客户进行的身份验证。<br>示例： w49d77900526190e26708c31c9e8a0@pfwp-commicrosoftonedfmdm2.google.com.iam.gserviceaccount.com<br>**密钥**：用于身份验证请求的 Base64 编码 blob，在服务中存储加密，该 blob 如下所示：<br> 表示客户密钥的唯一标识符<br>示例：a70d4d53eefbd781ce7ad6a6495c65eb15e74f1f |

**设备数据示例**

下面是来自 Google 的示例 JSON 设备消息：



```
'{
  "name": "enterprises/LC02dhxx1r/devices/3195483be017acdc",
  "userId": "114223373813435875042",
  "adminType": "DEVICE_OWNER",
  "state": "ACTIVE",
  "appliedState": "ACTIVE",
  "policyCompliant": true,
  "enrollmentTime": "2017-10-06T15:17:41.702Z",
  "lastStatusReportTime": "2017-10-06T15:18:10.325Z",
  "lastPolicyComplianceReportTime": "2017-10-06T15:18:11.665Z",
  "lastPolicySyncTime": "2017-10-06T15:18:07.852Z",
  "appliedPolicyVersion": "2",
  "apiLevel": 26,
  "enrollmentTokenData": "brew 30 day token",
  "enrollmentTokenId": "yXdtW0_0L7c7Yo9DtRhEfPi3PcMqTorF3V1bTAw_eRs",
  "softwareInfo": {
    "androidVersion": "8.0.0",
    "cloudDpcVersionCode": 55314,
    "cloudDpcVersionName": "bv00553-rc14",
    "androidBuildNumber": "OPR4.170623.009",
    "deviceKernelVersion": "3.10.73-ga51b1600b7f8",
    "bootloaderVersion": "BHZ21c",
    "androidBuildTime": "2017-08-28T18:57:48Z",
    "securityPatchLevel": "2017-10-05",
    "androidBuildType": "user",
    "buildUser": "android-build"
  },
  "hardwareInfo": {
    "brand": "google",
    "hardware": "bullhead",
    "deviceBasebandVersion": "M8994F-2.6.39.3.03",
    "manufacturer": "LGE",
    "serialNumber": "01ed07873b3c20cd",
    "model": "Nexus 5X",
    "batteryShutdownTemperatures": [60.0],
    "batteryThrottlingTemperatures": [-3.4028235E38],
    "cpuShutdownTemperatures": [115.0, 115.0, 115.0, 115.0, 115.0, 115.0],
    "cpuThrottlingTemperatures": [60.0, 60.0, 60.0, 60.0, 60.0, 60.0],
    "gpuShutdownTemperatures": [-3.4028235E38],
    "gpuThrottlingTemperatures": [-3.4028235E38],
    "skinShutdownTemperatures": [-3.4028235E38],
    "skinThrottlingTemperatures": [37.0]
  },
  "displays": [{
    "name": "Built-in Screen",
    "refreshRate": 60,
    "state": "ON",
    "width": 1080,
    "height": 1920,
    "density": 420
  }],
  "appliedPolicyName": "enterprises/LC02dhxx1r/policies/default",
  "networkInfo": {
    "imei": "353626070676775",
    "wifiMacAddress": "02:00:00:00:00:00"
  },
  "memoryInfo": {
    "totalRam": "1902936064",
    "totalInternalStorage": "3169611776"
  },
  "memoryEvents": [{
    "eventType": "EXTERNAL_STORAGE_DETECTED",
    "createTime": "2017-10-06T15:18:09.959Z",
    "byteCount": "26720919552"
  }],
  "powerManagementEvents": [{
    "eventType": "BATTERY_LEVEL_COLLECTED",
    "createTime": "2017-10-06T15:18:09.939Z",
    "batteryLevel": 95.0
  }],
  "userName": "enterprises/LC02dhxx1r/users/114223373813435875042",
  "enrollmentTokenName": "enterprises/LC02dhxx1r/enrollmentTokens/yXdtW0_0L7c7Yo9DtRhEfPi3PcMqTorF3V1bTAw_eRs"
}'
```

要停止配合使用 Android 设备管理与 Microsoft Intune 并删除数据，必须禁用 Microsoft Intune Android 设备管理并删除 Google 帐户。 请参阅 Google 帐户如何执行帐户管理。


