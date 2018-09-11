---
title: Microsoft Intune 中适用于 Android 的展台设置 - Azure | Microsoft Docs
description: 将 Android 展台设备配置为单应用和多应用展台。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 7/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cef98527ee2c281547f8046f3c6f08275d8f0807
ms.sourcegitcommit: e814cfbbefe818be3254ef6f859a7bf5f5b99123
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2018
ms.locfileid: "43329377"
---
# <a name="kiosk-settings-for-android-devices-in-intune"></a>Intune 中的适用于 Android 设备的展台设置

通过使用设备配置设置，可以将设备配置为单应用或多应用展台模式。 当设备处于展台模式时，设备的使用仅限于限制配置文件定义的应用或 Web 链接。 

## <a name="restrict-an-android-kiosk-device-to-a-single-app"></a>将 Android 展台设备限制为单应用

如果展台设备的限制配置文件设置为“展台模式” = “单应用展台”，则用户只能访问一个应用。 当以此模式配置的设备启动时，将启动特定应用。 限制用户打开新应用或更改正在运行的应用。

1. 确保要在展台设备上使用的应用已[部署到设备](apps-deploy.md)，并且已将该应用分配给为展台设备创建的设备组。
2. 转到 [Intune 门户](https://portal.azure.com)，然后选择“设备配置” > “配置文件” > “创建配置文件”。
3. 在“创建配置文件”边栏选项卡上，设置以下字段：
     - **名称**
     - **平台**：Android 企业
     - **配置文件类型**：“仅限设备所有者”>“设备限制”
4. 选择“设置” > “展台”。
5. 对于“展台模式”，请选择“单应用展台”。
6. 选择“选择托管应用”，然后选择托管 Google Play 应用，你希望对于使用此配置文件的设备而言，该应用是唯一可用的应用。
7. 选择“确定” > “确定” > “确定” > “创建”。
8. 选择刚创建的配置文件 > 然后选择“分配”。
9. 在“分配对象”下，选择“选择的组”。
10. 选择“选择要包括的组”> 选择为展台设备创建的设备组 >“选择”。

## <a name="restrict-a-kiosk-device-to-a-set-of-apps-or-web-links"></a>将展台设备限制为一组应用或 Web 链接

如果展台设备的限制配置文件设置为“展台模式” = “多应用展台”，则用户只能访问配置的有限数量的应用。 还可定义一组用户可以访问的 Web 链接。 应用策略后，用户会在主屏幕上看到允许的应用的图标。

要为多个应用设置 Android 展台设备，请执行以下主要步骤：

1. [从托管的 Google Play 导入并部署托管的主屏幕应用](#import-and -deploy-the-managed-home-screen-app)
2. [添加并分配可用于展台模式的应用](#add-and-assign-apps-that-can-be-used-in-kiosk-mode)
3. （可选）[添加可用于展台模式的 Web 链接](#add-web-links-that-can-be-used-in-kiosk-mode)

### <a name="import-and-deply-the-managed-home-screen-app"></a>导入和部署托管的主屏幕应用

1. 浏览到 [Google Play 上的托管主屏幕页](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise)，并使用用于其他托管的 Google Play 应用的相同帐户登录。
2. 选择“批准”。
3. 转到 [Intune 门户](https://portal.azure.com)，然后选择“客户端应用” > “托管的 Google Play” > “同步”。
4. 选择“应用” > “托管的主屏幕” > “分配” > “添加组”。
5. 在“分配类型”下，选择“必需”。
6. 选择“已包括的组” > “选择要包括的组”> 选择为展台设备创建的设备组 >“选择” > “确定” > “确定” > “保存”。

### <a name="add-and-assign-apps-that-can-be-used-in-kiosk-mode"></a>添加并分配可用于展台模式的应用

对于要在展台设备上使用的每个应用，请执行以下步骤：

1. [将应用添加到 Intune](store-apps-android.md)。
2. 选择“客户端应用” > “应用”> 选择应用 >“分配” > “添加组”。
3. 在“分配类型”下，选择“必需”。
4. 选择“已包括的组” > “选择要包括的组”> 选择为展台设备创建的设备组 >“选择” > “确定” > “确定” > “保存”。

### <a name="add-web-links-that-can-be-used-in-kiosk-mode"></a>添加可用于展台模式的 Web 链接

1. 转到 [Intune 门户](https://portal.azure.com)，然后选择“客户端应用” > “应用” > “添加”。
2. 在“应用类型”下，选择“Web 链接”。
3. 选择“配置”并提供所需信息。 无需添加徽标图像，因为它将自动从网站的 favicon.ico 中检索。
4. 选择“确定” > “添加”。

请确保使用“[移动应用](apps-add.md)”向展台设备部署 Web 浏览器应用。

### <a name="create-a-multi-app-kiosk-profile"></a>创建多应用展台配置文件

1. 转到 [Intune 门户](https://portal.azure.com)，然后选择“设备配置” > “配置文件” > “创建配置文件”。
3. 在“创建配置文件”边栏选项卡上，设置以下字段：
     - **名称**：键入一个直观的名称
     - **平台**：Android 企业
     - **配置文件类型**：“仅限设备所有者”>“设备限制”
4. 选择“设置” > “展台”。
5. 对于“展台模式”，请选择“多应用展台”。
6. 选择“添加”，然后选择对使用此配置文件的设备可用的应用或 Web 链接。
7. 选择“确定” > “确定” > “确定” > “创建”。
8. 选择刚创建的配置文件 > 然后选择“分配”。
9. 在“分配对象”下，选择“选择的组”。
10. 选择“选择要包括的组”> 选择为展台设备创建的设备组 >“选择” > “保存”。

## <a name="next-steps"></a>后续步骤
[分配配置文件](device-profile-assign.md)并[监视其状态](device-profile-monitor.md)。
