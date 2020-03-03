---
title: 使用平台支持的加密方法加密设备
titleSuffix: Microsoft Intune
description: 使用内置加密方法（如 BitLocker 或 FileVault）加密设备，并在 Intune 门户中管理这些加密设备的恢复密钥。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: annovich
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: a5c844377dcd69b6caf5ef9f72fcb8dbb4ef8bd0
ms.sourcegitcommit: 29f3ba071c9348686d3ad6f3b8864d8557e05b97
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/26/2020
ms.locfileid: "77609315"
---
# <a name="use-device-encryption-with-intune"></a>使用 Intune 设备加密

使用 Intune 管理设备内置磁盘或驱动器加密以保护设备上的数据。

将磁盘加密配置为 Endpoint Protection 的设备配置配置文件的一部分。 Intune 支持以下平台和加密技术：

- macOS：FileVault
- Windows 10 及更高版本：BitLocker

Intune 还提供内置的[加密报表](encryption-monitor.md)，其中提供了有关所有受管理设备中的设备加密状态的详细信息。

## <a name="filevault-encryption-for-macos"></a>macOS 的 FileVault 加密

使用 Intune 在运行 macOS 的设备上配置 FileVault 磁盘加密。 然后，使用 Intune 加密报表查看这些设备的加密详细信息和管理 FileVault 加密设备的恢复密钥。

若要使 FileVault 在设备上运行，需要用户批准的设备注册。 用户必须手动批准系统首选项中的管理配置文件，才能将注册视为用户批准。

FileVault 是 macOS 附带的整盘加密程序。 可以使用 Intune 在运行 macOS 10.13 或更高版本的设备上配置 FileVault  。

若要配置 FileVault，请为 macOS 平台创建用于 Endpoint Protection 的[设备配置配置文件](../configuration/device-profile-create.md)。 FileVault 设置是 macOS Endpoint Protection 的可用设置类别之一。

创建使用 FileVault 加密设备的策略后，策略将分两个阶段应用于设备。 首先，准备好设备，以启用 Intune 检索和备份恢复密钥。 此操作称为“托管”。 托管密钥后，磁盘加密便可启动。

![FileVault 设置](./media/encrypt-devices/filevault-settings.png)

如需深入了解可以使用 Intune 管理的 FileVault 设置，请参阅 Intune 文章中 macOS Endpoint Protection 设置的 [FileVault](endpoint-protection-macos.md#filevault)。

### <a name="permissions-to-manage-filevault"></a>用于管理 FileVault 的权限

若要在 Intune 中管理 FileVault，你的帐户必须具有适用的 Intune [基于角色的访问控制](../fundamentals/role-based-access-control.md) (RBAC) 权限。

下面是 FileVault 权限（“远程任务”类别的一部分）和授予权限的内置 RBAC 角色  ：
 
- **获取 FileVault 密钥**：
  - 支持人员操作员
  - 终结点安全管理器

- **轮换 FileVault 密钥**
  - 支持人员操作员

### <a name="how-to-configure-macos-filevault"></a>如何配置 macOS FileVault

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 选择“设备”   > “配置文件”   > “创建配置文件”  。

3. 设置下列选项:

   - 平台：macOS
   - 配置文件类型：Endpoint Protection

4. 选择“设置” > “FileVault”   。

5. 对于 FileVault，请选择“启用”   。

6. 对于“恢复密钥类型”，仅支持“个人密钥”   。

   请考虑添加一条消息，以帮助指导最终用户检索其设备的恢复密钥。 使用个人恢复密钥轮换设置时，此信息对最终用户非常有用。通过该设置，可以定期自动为设备生成新的恢复密钥。

   例如：若要检索丢失或最近轮换的恢复密钥，请从任意设备登录 Intune 公司门户网站。 在门户中，转到“设备”并选择已启用 FileVault 的设备，然后选择“获取恢复密钥”   。 系统会显示当前恢复密钥。

7. 配置其余 [FileVault 设置](endpoint-protection-macos.md#filevault)以满足业务需求，然后选择“确定”  。

  8. 完成其他设置配置，然后保存配置文件。  

### <a name="manage-filevault"></a>管理 FileVault

在 Intune 使用 FileVault 加密 macOS 设备之后，你便可在查看 Intune [加密报表](encryption-monitor.md)时查看和管理 FileVault 恢复密钥。

在 Intune 使用 FileVault 加密 macOS 设备后，你可以在任何设备上的 Web 公司门户中查看相应设备的个人恢复密钥。 在 Web 公司门户中，先选择已加密的 macOS 设备，再选择“获取恢复密钥”作为远程设备操作。

### <a name="retrieve-personal-recovery-key-from-mem-encrypted-macos-devices"></a>从 MEM 加密的 macOS 设备检索个人恢复密钥

借助 iOS 公司门户应用，最终用户可以检索其个人恢复密钥（FileVault 密钥）。 拥有个人恢复密钥的设备必须已注册 Intune，并且通过 Intune 使用 FileVault 加密。 借助 iOS 公司门户应用，最终用户可以打开包含 FileVault 个人恢复密钥的网页。 此外，还可以通过选择“设备” > “已加密和已注册的 macOS 设备” > “获取恢复密钥”，来从 Intune 检索恢复密钥。    

## <a name="bitlocker-encryption-for-windows-10"></a>适用于 Windows 10 的 BitLocker 加密

使用 Intune 在运行 Windows 10 的设备上配置 BitLocker 磁盘加密。 然后，使用 Intune 加密报表查看这些设备的加密详细信息。 还可以从设备访问 BitLocker 的重要信息，如 Azure Active Directory (Azure AD) 中所示。

BitLocker 适用于运行 Windows 10 或更高版本的设备  。

为 Windows 10 或更高版本的平台创建用于 Endpoint Protection 的[设备配置配置文件](../configuration/device-profile-create.md)时，请配置 BitLocker。 BitLocker 设置属于 Windows 10 Endpoint Protection 的 Windows 加密设置类别。

![BitLocker 设置](./media/encrypt-devices/bitlocker-settings.png)

### <a name="how-to-configure-windows-10-bitlocker"></a>如何配置 Windows 10 BitLocker

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 选择“设备”   > “配置文件”   > “创建配置文件”  。

3. 设置下列选项:

   - 平台：Windows 10 及更高版本
   - 配置文件类型：Endpoint Protection

4. 选择“设置” > “Windows Encryption”   。

5. 配置 BitLocker 的设置以满足你的业务需求，然后选择“确定”  。

6. 完成其他设置配置，然后保存配置文件。

### <a name="manage-bitlocker"></a>管理 BitLocker

在 Intune 使用 BitLocker 加密 Windows 10 设备之后，你便可在查看 Intune [加密报表](encryption-monitor.md)时查看和检索 BitLocker 恢复密钥。

### <a name="rotate-bitlocker-recovery-keys"></a>BitLocker 恢复密码轮转

可以使用 Intune 设备操作远程轮转运行 Windows 10 版本 1909 或更高版本的设备的 BitLocker 恢复密码。

#### <a name="prerequisites"></a>必备条件

设备必须满足以下先决条件才支持 BitLocker 恢复密码轮转：

- 设备必须运行 Windows 10 版本 1909 或更高版本

- Azure AD 加入和混合加入的设备必须启用密码轮转支持：

  - 客户端驱动的恢复密码轮转 

  此设置位于“Windows 加密”下，是 Windows 10 终结点保护设备配置策略的一部分  。
  
#### <a name="to-rotate-the-bitlocker-recovery-key"></a>BitLocker 恢复密码轮转

1. 登录到 [Microsoft 终结点管理器管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 选择“设备” > “所有设备”   。

3. 在所管理的设备列表中，选择一个设备，选择“更多”  ，然后选择“BitLocker 密码轮转”  设备远程操作。

## <a name="next-steps"></a>后续步骤

创建[设备符合性](compliance-policy-create-windows.md)策略。

使用加密报表管理以下内容：

- [BitLocker 恢复密钥](encryption-monitor.md#bitlocker-recovery-keys)
- [FileVault 恢复密钥](encryption-monitor.md#filevault-recovery-keys)

查看可以使用 Intune 配置的加密设置：

- [BitLocker](endpoint-protection-windows-10.md#windows-encryption)
- [FileVault](endpoint-protection-macos.md#filevault)
