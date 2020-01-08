---
title: 使用 Microsoft Intune 中的管理模板更新 Office 365 - Azure | Microsoft Docs
description: 使用 Microsoft Intune 中的管理模板将 Office 365 应用更新到最新版本，并选择 Office 检查更新的频率。 查看当应用 Intune 策略到 Office 更新时更新的设备注册表项。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 63ebbc22c5452c99439d34813509b5652daef1f0
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/31/2019
ms.locfileid: "75548083"
---
# <a name="use-update-channel-and-target-version-settings-to-update-office-365-with-microsoft-intune-administrative-templates"></a>使用“更新频道”和“目标版本”设置，通过 Microsoft Intune 管理模板更新 Office 365

在 Intune 中，可以使用 [Windows 10 模板配置组策略设置](administrative-templates-windows.md)。 本文介绍了如何使用 Intune 中的管理模板更新 Office 365。 它还提供有关确认是否已成功应用策略的指南。 此信息还有助于进行故障排除。

在此应用场景中，将在 Intune 中创建一个管理模板以更新设备上的 Office 365。

有关管理模板的详细信息，请参阅[使用 Windows 10 模板配置组策略设置](administrative-templates-windows.md)。

适用于：

- Windows 10 及更高版本
- Office 365

## <a name="prerequisites"></a>必备条件

确保为 Office 应用[启用 Office365 专业增强版自动更新](https://docs.microsoft.com/deployoffice/configure-update-settings-for-office-365-proplus)。 你可以使用组策略或 Intune Office 2016 ADMX 模板执行此操作：

![在 Intune 管理模板中，为 Office 设置“启用自动更新”设置](./media/administrative-templates-update-office/admx-enable-automatic-updates.png)

## <a name="set-the-update-channel-in-the-intune-administrative-template"></a>在 Intune 管理模板中设置“更新频道”

1. 在 [Intune 管理模板](administrative-templates-windows.md#create-a-template)中，转到“更新频道”  设置，并输入所需的频道。 例如，选择 `Semi-Annual Channel`：

    ![在 Intune 管理模板中，为 Office 设置“更新频道”设置](./media/administrative-templates-update-office/admx-enable-update-channel-setting.png)

    > [!NOTE]
    > 建议更频繁地进行更新。 半年仅用作示例。

2. 请确保向 Windows 10 设备[分配策略](device-profile-assign.md)。 若要更快地测试策略，还可以同步策略：

    - [在 Intune 中同步策略](../remote-actions/device-sync.md)
    - [手动同步设备上的策略](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows#sync-from-settings-app)

## <a name="check-the-intune-registry-keys"></a>检查 Intune 注册表项

分配策略和设备同步后，可以确认已应用策略：

1. 在设备上，打开“注册表编辑器”  应用。
2. 转到 Intune 策略路径：`Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\Providers\<Provider ID>\default\Device\office16~Policy~L_MicrosoftOfficemachine~L_Updates`。

    > [!TIP]
    > 注册表项中的 `<Provider ID>` 将更改。 若要查找设备的提供程序 ID，请打开“注册表编辑器”  应用，并转到 `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\AdmxInstalled`。 将显示提供程序 ID。

    应用策略后，会看到以下注册表项：

    - `L_UpdateBranch`
    - `L_UpdateTargetVersion`

    查看以下示例时，可以看到 `L_UpdateBranch` 的值类似于 `<enabled /><data id="L_UpdateBranchID" value="Deferred" />`。 此值表示将其设置为“半年频道”：

    ![管理模板 L_Updatebranch 注册表项示例](./media/administrative-templates-update-office/admx-update-branch-registry-key.png)

    > [!TIP]
    > [使用 Configuration Manager 管理 Office 365 专业增强版](https://docs.microsoft.com/configmgr/sum/deploy-use/manage-office-365-proplus-updates#bkmk_channel) 列出了值及其含义。 注册表值基于所选的分发频道：
    >
    >- 每月频道                - value="Current"
    >- 每月频道(定向)     - value="Current"
    >- 半年频道            - value="Current"
    >- 半年频道(定向) - value="FirstReleaseDeferred"
    >- 预览体验计划(快)                   - value="InsiderFast"

此时，Intune 策略已成功应用到设备。

## <a name="check-the-office-registry-keys"></a>检查 Office 注册表项

1. 在设备上，打开“注册表编辑器”  应用。
2. 转到 Office 策略路径：`Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Configuration`。

    你会看到以下注册表项：

    - `UpdateChannel`：动态项，根据配置的设置进行更改。
    - `CDNBaseUrl`：设置 Office 365 安装在设备上的时间。

3. 查看 `UpdateChannel` 值。 此值告诉你 Office 的更新频率。 [使用 Configuration Manager 管理 Office 365 专业增强版](https://docs.microsoft.com/configmgr/sum/deploy-use/manage-office-365-proplus-updates#bkmk_channel) 列出了值及其设置的内容。

    在下面的示例中，你将看到 `UpdateChannel` 设置为 `http://officecdn.microsoft.com/pr/492350f6-3a01-4f97-b9c0-c7c6ddf67d60`，即“每月”  ：

    ![管理模板 Office UpdateChannel 注册表项示例](./media/administrative-templates-update-office/admx-update-channel-office-registry-key.png)

    此示例表示尚未应用策略，因为它仍设置为“每月”  ，而不是“半年”  。

当“任务计划程序”   > “Office 自动更新 2.0”  运行或用户登录到设备时，将更新此注册表项。 若要确认，请打开“Office 自动更新 2.0”  任务 >“触发器”  。 根据你的触发器，在更新 `UpdateChannel` 注册表项之前，可能至少需要一天或更长时间。

## <a name="force-office-automatic-updates-to-run"></a>强制运行 Office 自动更新

若要测试策略，可以在设备上强制执行策略设置。 以下步骤将更新注册表。 与往常一样，请谨慎更新注册表。

1. 清除注册表项：

    1. 转到 `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Updates`。
    2. 双击 `UpdateDetectionLastRunTime` 项，删除数值数据 >“确定”  。

2. 运行“Office 自动更新”任务：

    1. 在设备上打开“任务计划程序”  应用。
    2. 展开“任务计划程序库”   > “Microsoft”   > “Office”  。
    3. 选择“Office 自动更新 2.0”   > “运行”  ：

        ![打开“任务计划”，并运行“Office 自动更新”](./media/administrative-templates-update-office/admx-task-scheduler-office-automatic-updates.png)

        等待任务完成，这可能需要几分钟时间。

3. 在“注册表编辑器”  应用中，转到 `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Configuration`。 检查 `UpdateChannel` 值。

    应使用策略中设置的值对其进行更新。 在我们的示例中，该值应设置为 `http://officecdn.microsoft.com/pr/7ffbc6bf-bc32-4f92-8982-f9dd17fd3114`。

此时，设备上的 Office 更新频道已成功更改。 可以为接收此更新的用户打开 Office 365 应用来检查状态。

## <a name="force-the-office-synchronization-to-update-account-information"></a>强制 Office 同步更新帐户信息  

如果要执行更多操作，可以强制 Office 获取最新版本更新。 以下步骤只能用于确认，或者当你需要设备快速从该频道获取最新版本更新时使用这些步骤。 否则，让 Office 完成其作业，并自动更新。

### <a name="step-1-force-the-office-version-to-update"></a>步骤 1：强制更新 Office 版本

1. 确认 Office 版本支持所选的更新频道。 [Office 365 专业增强版的更新历史记录](https://docs.microsoft.com/officeupdates/update-history-office365-proplus-by-date)列出了支持不同更新频道的内部版本号。

2. 在 [Intune 管理模板](administrative-templates-windows.md#create-a-template)中，转到“目标版本”  设置，并输入所需的版本。

    “目标版本”  设置类似于以下设置：

    ![在 Intune 管理模板中，为 Office 设置“目标版本”设置](./media/administrative-templates-update-office/admx-enable-target-version-setting.png)

> [!IMPORTANT]
>
> - 确保分配策略。
> - 如果更改现有策略，则所做的更改将影响所有已分配的用户。
> - 如果要测试此功能，建议创建测试策略，并将策略分配给用户的测试组。

### <a name="step-2-check-the-office-version"></a>步骤 2:检查 Office 版本

在将策略部署到所有用户之前，请考虑使用这些步骤来测试策略。

1. 在“注册表编辑器”  应用中，转到 `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\Providers\<Provider ID>\default\Device\office16~Policy~L_MicrosoftOfficemachine~L_Updates`

2. 查看 `L_UpdateTargetVersion` 值。 应用策略后，该值将设置为所输入的版本，如 `<enabled /><data id="L_UpdateTargetVersionID" value="16.0.10730.20344" />`。

    此时，Intune 策略已成功应用到设备。

3. 接下来，你可以强制更新 Office。 打开 Office 应用，如 Excel。 选择立即更新（可能在“帐户”  菜单中）。

    更新过程需要几分钟时间。 你可以确认 Office 正在尝试获取所输入的版本：

      1. 在设备上，转到 `C:\Program Files (x86)\Microsoft Office\Updates\Detection\Version`。
      2. 打开 `VersionDescriptor.xml` 文件，并转到 `<Version>` 部分。 可用版本应与你在 Intune 策略中输入的版本相同，例如：

          ![检查版本描述符 Office XML 文件中的版本部分](./media/administrative-templates-update-office/office-version-descriptor-xml-example.png)

4. 安装更新后，Office 应用将显示新版本（例如，在“帐户” **"** 菜单中）

## <a name="next-steps"></a>后续步骤

[更新 Office 365 客户端的频道值](https://docs.microsoft.com/configmgr/sum/deploy-use/manage-office-365-proplus-updates#bkmk_channel)

[适用于 Office 365 专业增强版的 Office 云策略服务概述](https://docs.microsoft.com/deployoffice/overview-office-cloud-policy-service)

[使用 Windows 10 模板在 Microsoft Intune 中配置组策略设置（ADMX 模板）](administrative-templates-windows.md)
