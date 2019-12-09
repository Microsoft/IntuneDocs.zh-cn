---
title: 在 S 模式设备上启用 Win32 应用
titleSuffix: Microsoft Intune
description: 了解如何使用 Microsoft Intune 在 S 模式设备上启用 Win32 应用。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7e17972a3a87bd9c42db54753d4da3bb81703377
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563626"
---
# <a name="enable-win32-apps-on-s-mode-devices"></a>在 S 模式设备上启用 Win32 应用

[Windows 10 S 模式](https://docs.microsoft.com/windows/deployment/s-mode)是仅运行应用商店应用的锁定操作系统。 默认情况下，Windows S 模式设备不允许安装和执行 Win32 应用。 这些设备包括单个 Win 10S 基准策略，该策略会锁定 S 模式设备，阻止运行该设备上的任何 Win32 应用  。 但是，通过在 Intune 中创建和使用 S 模式补充策略，你可以在 Windows 10 S 模式托管设备上安装和运行 Win32 应用  。 通过使用 [Microsoft Defender 应用程序控制 (WDAC)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control) PowerShell 工具，你可以为 Windows S 模式创建一个或多个补充策略。 必须使用[设备保护签名服务 (DGSS)](https://go.microsoft.com/fwlink/?linkid=2095629) 或 [SignTool.exe](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/signing-policies-with-signtool) 对补充策略进行签名，然后通过 Intune 上传和分发策略。 或者，可以使用组织中的代码签名证书对补充策略进行签名，但首选方法是使用 DGSS。 在使用组织中的代码签名证书的实例中，代码签名证书链接到的根证书必须存在于设备上。

通过在 Intune 中分配 S 模式补充策略，可以使设备对设备的现有 S 模式策略引发例外，这允许已上传且已相应签名的应用目录。 此策略设置可在 S 模式设备上使用的应用的允许列表（应用目录）。

> [!NOTE]
> S 模式设备上的 Win32 应用仅在 Windows 10 2019 年 11 月更新（内部版本 18363）或更高版本上受支持。

<!-- Add WDAC tooling diagram  -->

允许 Win32 应用在 S 模式 Windows 10 设备上运行的步骤如下：

1. 在 Windows 10 S 注册过程中，通过 Intune 启用 S 模式设备。
2. 创建补充策略以允许 Win32 应用：
   - 可以使用 [Microsoft Defender 应用程序控制 (WDAC)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control) 工具来创建补充策略。 策略中的基准策略 ID 必须与 S 模式基准策略 ID（在客户端上进行了硬编码）匹配。 此外，请确保策略版本高于以前的版本。
   - 使用 DGSS 对补充策略进行签名。 有关详细信息，请参阅[使用设备保护签名对代码完整性策略进行签名](https://docs.microsoft.com/microsoft-store/sign-code-integrity-policy-with-device-guard-signing)。
   - 通过创建 Windows 10 S 模式补充策略，将已签名的补充策略上传到 Intune（见下文）。
3. 通过 Intune 允许 Win32 应用目录：
   - 创建目录文件（每个应用包含 1 个文件），并使用 DGSS 或其他证书基础结构对其进行签名。
   - 使用 [Microsoft Win32 内容准备工具](https://go.microsoft.com/fwlink/?linkid=2065730)将已签名的目录打包到 .intunewin  文件中。 有关详细信息，请参阅 [Win32 应用管理 - 准备 Win32 应用内容以进行上传](~/apps/apps-win32-app-management.md#prepare-the-win32-app-content-for-upload)。
   - Intune 应用已签名的应用目录，以使用 [Intune 管理扩展](~/apps/intune-management-extension.md)在 S 模式设备上安装 Win32 应用。

> [!NOTE]
> Windows 10 S 模式业务线 (LOB) `.appx` 和 `.appx` 捆绑将通过适用于企业的 Microsoft 应用商店 (MSFB) 签名受到支持。
>
> 应用的 S 模式补充策略必须通过 Intune 管理扩展提供  。
>
> S 模式策略是在设备级别强制执行的。 设备上将合并多个目标策略。 合并的策略将在设备上强制执行。

若要创建 Windows 10 S 模式补充策略，请执行以下步骤：

1. 登录到 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 选择“应用” > “S 模式补充策略” > “创建策略”    。
3. 在添加“策略文件”  之前，必须创建该文件并对其进行签名。 有关详情，请参阅：
    - [使用 PowerShell 工具创建 WDAC 策略并将其转换为二进制格式](https://go.microsoft.com/fwlink/?linkid=2095387)
    - [使用设备保护签名服务进行签名](https://go.microsoft.com/fwlink/?linkid=2095629)（推荐） 

4. 在“基本信息”页上，添加以下值  ：

    | 值 | 描述 |
    |--------------|------------------------------------------------|
    | 策略文件 | 包含 WDAC 策略的文件。 |
    | 名称 | 此策略的名称。 |
    | 描述 | [可选] 此策略的说明。 |

5. 单击“**下一步:** 作用域标记”。<br>
   在“作用域标记”页上，你可以选择配置作用域标记，以确定谁可以在 Intune 中查看应用策略  。 若要详细了解作用域标记，请参阅[将基于角色的访问控制和作用域标记用于分布式 IT](~/fundamentals/scope-tags.md)。

6. 单击“下一步:  分配”。<br>
   通过“分配”页面，可以将策略分配到用户和设备  。 值得注意的是，无论设备是否由 Intune 管理，都可以将策略分配到设备。
7. 单击“**下一步:查看 + 创建**”以查看你为配置文件输入的值。
8. 完成后，单击“创建”以在 Intune 中创建 S 模式补充策略  。 

创建策略后，你会看到它已添加到 Intune 中的 S 模式补充策略列表。 分配策略后，策略将部署到设备。 请注意，必须将应用部署到与补充策略相同的安全组。 可以开始定位应用并将其分配到这些设备。 这将允许最终用户在 S 模式设备上安装和执行应用。

## <a name="removal-of-s-mode-policy"></a>删除 S 模式策略

目前，若要从设备中删除 S 模式补充策略，必须分配并部署一个空策略以覆盖现有的 S 模式补充策略。

## <a name="policy-reporting"></a>策略报告

S 模式补充策略是在设备级别强制执行的，它仅具有设备级别报告。 设备级报告可用于成功和错误情况。 

Intune 控制台中显示的 S 模式报告策略的报告值：
- **成功**：S 模式补充策略生效。
- **未知**：S 模式补充策略的状态未知。
- **TokenError**：S 模式补充策略在结构上正常，但在授权令牌时出错。
- **NotAuthorizedByToken**：令牌未对此 S 模式补充策略进行授权。
- **PolicyNotFound**：找不到 S 模式补充策略。

## <a name="next-steps"></a>后续步骤

- 有关详细信息，请参阅 [S 模式 Win32 应用](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/lob-win32-apps-on-s)。
- 有关向 Intune 添加应用的详细信息，请参阅[向 Microsoft Intune 添加应用](apps-add.md)。
- 有关 Win32 应用的详细信息，请参阅 [Intune Win32 应用管理](~/apps/apps-win32-app-management.md)。
