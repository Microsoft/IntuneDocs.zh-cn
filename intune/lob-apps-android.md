---
title: 如何将 Android 业务线应用添加到 Microsoft Intune
titlesuffix: ''
description: 了解如何将 Android 业务线 (LOB) 应用添加到 Microsoft Intune。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 061d793c-c724-4cd9-9240-adb0cbda5661
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0297cb0b399d487f548bf6fdd9fb74946bbcb7b1
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-android-line-of-business-lob-apps-to-microsoft-intune"></a>如何将 Android 业务线 (LOB) 应用添加到 Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

业务线 (LOB) 应用是从应用安装文件添加到 Intune 的应用。 这些应用类型通常为内部编写。 Intune 在用户设备上安装 LOB 应用。 

> [!Note]
> 若要深入了解来自 Google Play for Work 商店的业务线 (LOB) 应用，请参阅[处理来自 Google Play for Work 商店的业务线应用](apps-add-android-for-work.md?#working-with-a-line-of-business-app-from-the-google-play-for-work-store)。 

## <a name="step-1---specify-the-software-setup-file"></a>步骤 1 - 指定软件安装程序文件

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务” > “Intune”。 Intune 位于“监视 + 管理”部分中。
3. 在“Intune”窗格中，选择“移动应用”。
4. 在“移动应用”工作负荷中，选择“管理” > “应用”。
5. 在应用列表的上方，选择“添加”。
6. 在“添加应用”窗格中，选择“业务线应用”。

## <a name="step-2---configure-the-app-package-file"></a>步骤 2 - 配置应用包文件

1. 在“添加应用”窗格中，选择“应用包文件”。
2. 在“应用包文件”窗格中，选择浏览按钮，然后选择扩展名为 .apk 的 Android 安装文件。
3. 完成后，请选择“确定”。


## <a name="step-3---configure-app-information"></a>步骤 3 - 配置应用信息

1. 在“添加应用”窗格中，选择“应用包”文件。
2. 在“应用信息”窗格中，添加应用的详细信息。 此窗格中的某些值可能已自动填充（具体取决于所选应用）：
    - 名称 - 输入要在公司门户中显示的应用名称。 请确保使用的所有应用名称都是唯一的。 如果同一应用名称存在两次，则在公司门户中将仅向用户显示其中一个应用。
    - 说明 - 输入要在公司门户中向用户显示的应用说明。
    - **发行者** — 输入应用的发行者名称。
    - **最低操作系统** - 从列表中选择可安装应用的最低操作系统版本。 如果将应用分配到具有较低操作系统的设备，则不会安装该应用。
    - **忽略应用版本** - 如果应用是由应用开发人员自动更新的，则设置为“是”。
    - **类别** - 选择一个或多个内置应用类别或你创建的类别。 这样，可让用户在浏览公司门户时更轻松地查找应用。
    - **在公司门户中将此应用显示为特色应用** - 当用户浏览应用时，在公司门户的主页上突出显示此应用。
    - **信息 URL** -（可选）输入包含此应用相关信息的网站 URL。 在公司门户中向用户显示该 URL。
    - **隐私 URL** -（可选）输入包含此应用相关隐私信息的网站 URL。 在公司门户中向用户显示该 URL。
    - **开发者** -（可选）输入应用开发者的名称。
    - **所有者** -（可选）输入此应用的所有者的名称，例如，**HR 部门**。
    - **说明** - 输入要与此应用关联的任何备注。
    - 徽标 - 上传与应用关联的图标。 用户浏览公司门户时，此图标与应用一同显示。
3. 完成后，请选择“确定”。

## <a name="step-4---finish-up"></a>步骤 4 - 完成

1. 在“添加应用”窗格中，确认应用的详细信息。
2. 选择“添加”将应用上传到 Intune。

创建的应用将显示在应用列表中，可在该列表中将其分配到所选择的组。 如需帮助，请参阅[如何将应用分配到组](apps-deploy.md)。

## <a name="step-5---update-a-line-of-business-app"></a>步骤 5 - 更新业务线应用

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

> [!Note]
> 为了让 Intune 服务成功地将新的 APK 文件部署到设备上，你必须在 APK 包的 AndroidManifest.xml 文件中递增 android:versionCode 字符串。

## <a name="next-steps"></a>后续步骤

- 创建的应用将显示在应用列表中。 现在，可将其分配到所选组。 如需帮助，请参阅[如何将应用分配到组](apps-deploy.md)。

- 详细了解可用于监视应用的属性和分配的方法。 有关详细信息，请参阅[如何监视应用信息和分配](apps-monitor.md)。

- 详细了解 Intune 中应用的上下文。 有关详细信息，请参阅[设备和应用生命周期概述](introduction-device-app-lifecycles.md)
