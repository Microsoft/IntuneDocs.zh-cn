---
title: 将 Android 业务线应用添加到 Microsoft Intune
description: 了解如何将 Android 业务线 (LOB) 应用添加到 Microsoft Intune。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 061d793c-c724-4cd9-9240-adb0cbda5661
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 783079786d19c0a65d44af96f9a3be9e2e817fc0
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2019
ms.locfileid: "71724784"
---
# <a name="add-an-android-line-of-business-app-to-microsoft-intune"></a>将 Android 业务线应用添加到 Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

业务线 (LOB) 应用是从应用安装文件添加到 Intune 的应用。 此类应用通常在内部编写。 Intune 在用户设备上安装 LOB 应用。 

> [!Note]
> 有关 LOB 应用和 Google Play 开发人员控制台的详细信息，请参阅[使用 Google 开发人员控制台进行托管 Google Play 专用 (LOB) 应用发布](apps-add-android-for-work.md?#managed-google-play-private-lob-app-publishing-using-the-google-developer-console)。 

> [!Note]
> 有关 Android for Work 设备，请参阅[使用 Intune 将托管 Google Play 应用添加到 Android Enterprise 设备](apps-add-android-for-work.md)。 

## <a name="step-1-specify-the-software-setup-file"></a>步骤 1：指定软件安装程序文件

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 在“Intune”窗格中，选择“客户端应用”   。
3. 在“客户端应用”工作负载中，选择“管理” > “应用”    。
4. 在应用列表上方，选择“添加”  。
5. 在“添加应用”  窗格中，选择“业务线应用”  。

## <a name="step-2-configure-the-app-package-file"></a>步骤 2：配置应用包文件

1. 在“添加应用”  窗格中，选择“应用包文件”  。
2. 在“应用包文件”  窗格中，选择“浏览”按钮。 然后选择扩展名为 .apk  的 Android 安装文件。
3. 完成后，选择“确定”  。

## <a name="step-3-configure-app-information"></a>步骤 3：配置应用信息

1. 在“添加应用”  窗格中，选择“应用信息”  。
2. 在“应用信息”  窗格中，添加应用的详细信息。 此窗格中的某些值可能已自动填充，具体取决于所选应用。
    - **名称**：输入显示在公司门户中的应用的名称。 请确保使用的所有应用名称都是唯一的。 如果同一应用名称存在两次，则公司门户中仅显示其中一个应用。
    - **说明**：输入应用的说明。 描述显示在公司门户中。
    - **发布者**：输入应用发布者的名称。
    - **最低操作系统**：从列表中选择可安装应用的最低操作系统版本。 如果将应用分配到具有较低操作系统的设备，则不会安装该应用。
    - **类别**：选择一个或多个内置应用类别，或选择你创建的类别。 “类别”可让用户在浏览公司门户时更轻松地查找应用。
    - **在公司门户中将此应用显示为特色应用**：当用户浏览应用时，在公司门户的主页上突出显示应用。
    - **信息 URL**：（可选）输入包含此应用相关信息的网站的 URL。 此 URL 显示在公司门户中。
    - **隐私 URL**：（可选）输入包含此应用相关隐私信息的网站的 URL。 此 URL 显示在公司门户中。
    - **开发者**：（可选）输入应用开发者的名称。
    - **所有者**：（可选）输入此应用的所有者的名称。 例如，“HR 部门”  。
    - **备注**：输入想与此应用关联的任何备注。
    - **徽标**：上传与应用关联的图标。 用户浏览公司门户时，此图标将与应用一同显示。
3. 完成后，选择“确定”  。

## <a name="step-4-finish-up"></a>步骤 4：完成

1. 在“添加应用”  窗格上，确认应用的详细信息正确无误。
2. 选择“添加”  将应用上传到 Intune。

你创建的应用现在显示在应用列表中。 从列表中，可以将应用分配到所选组。 如需帮助，请参阅[如何将应用分配到组](apps-deploy.md)。

## <a name="step-5-update-a-line-of-business-app"></a>步骤 5：更新业务线应用

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

如果在 Android 设备上启用了“检查来自外部源的应用”  ，则在安装更新之前，系统将提示用户。 否则，将自动安装更新。

> [!Note]
> 为了让 Intune 服务成功地将新的 APK 文件部署到设备上，必须在 APK 包的 AndroidManifest.xml 文件中递增 `android:versionCode` 字符串。

## <a name="next-steps"></a>后续步骤

- 你创建的应用显示在应用列表中。 现在，可将其分配到所选组。 如需帮助，请参阅[如何将应用分配到组](apps-deploy.md)。

- 详细了解可用于监视应用的属性和分配的方法。 请参阅[如何监视应用信息和分配](apps-monitor.md)。

- 详细了解 Intune 中应用的上下文。 请参阅[设备和应用生命周期概述](../fundamentals/device-lifecycle.md)。
