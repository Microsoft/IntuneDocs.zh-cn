---
title: 使用平台支持的加密方法加密 Microsoft Intune 中的设备
titleSuffix: Microsoft Intune
description: 使用内置加密方法（如 BitLocker 或 FileVault）加密设备，并在 Intune 门户中管理这些加密设备的恢复密钥。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: annovich
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: b7c76439b734837b5a4dd7e5fdbba5d21d0681d7
ms.sourcegitcommit: ec22a186a9cfa489a8490698e387624e480892d8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/13/2019
ms.locfileid: "68960430"
---
# <a name="use-device-encryption-with-intune"></a>使用 Intune 设备加密  

使用 Intune 管理设备内置磁盘或驱动器加密以保护设备上的数据。  

将磁盘加密配置为 Endpoint Protection 的设备配置配置文件的一部分。 Intune 支持以下平台和加密技术：  
- macOS：FileVault   
- Windows 10 及更高版本：BitLocker  

Intune 还提供内置的[加密报表](encryption-monitor.md)，其中提供了有关所有受管理设备中的设备加密状态的详细信息。  

## <a name="filevault-encryption-for-macos"></a>macOS 的 FileVault 加密  

使用 Intune 在运行 macOS 的设备上配置 FileVault 磁盘加密。 然后，使用 Intune 加密报表查看这些设备的加密详细信息和管理 FileVault 加密设备的恢复密钥。  

FileVault 是 macOS 附带的整盘加密程序。 可以使用 Intune 在运行 macOS 10.13 或更高版本的设备上配置 FileVault。  

若要配置 FileVault，请为 macOS 平台创建用于 Endpoint Protection 的[设备配置配置文件](device-profile-create.md)。 FileVault 设置是 macOS Endpoint Protection 的可用设置类别之一。  

创建使用 FileVault 加密设备的策略后，策略将分两个阶段应用于设备。 首先，准备好设备，以启用 Intune 检索和备份恢复密钥。 这被称为托管。 托管密钥后，磁盘加密便可启动。

![FileVault 设置](./media/encrypt-devices/filevault-settings.png)

如需深入了解可以使用 Intune 管理的 FileVault 设置，请参阅 Intune 文章中 macOS Endpoint Protection 设置的 [FileVault](endpoint-protection-macos.md#filevault)。  

### <a name="how-to-configure-macos-filevault"></a>如何配置 macOS FileVault 

1. 登录 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)，然后转到“设备配置” > “配置文件” > “创建配置文件”。  

2. 设置下列选项:  

   - 平台：macOS  
   - 配置文件类型：Endpoint Protection  

3. 选择“设置” > “FileVault”。  

4. 对于 FileVault，请选择“启用”。  

5. 对于“恢复密钥类型”，仅支持“个人密钥”。  

   请考虑添加一条消息，以帮助指导最终用户检索其设备的恢复密钥。 使用个人恢复密钥轮换设置时，此信息对最终用户非常有用。通过该设置，可以定期自动为设备生成新的恢复密钥。  

   例如：若要检索丢失或最近轮换的恢复密钥，请从任意设备登录 Intune 公司门户网站。 在门户中，转到“设备”并选择已启用 FileVault 的设备，然后选择“获取恢复密钥”。 系统会显示当前恢复密钥。  

6. 配置其余 [FileVault 设置](endpoint-protection-macos.md#filevault)以满足业务需求，然后选择“确定”。  

   > [!IMPORTANT]  
   > 如果将“禁止在注销时提示”设置设为“启用”，则存在一个已知问题。 设置为“启用”时，必须将“允许绕过的次数”设置设为具体值，不得设置为“未配置”。 如果设置为“未配置”，配置文件会无法在设备上运行。 在这种情况下，设备将“配置文件状态摘要”报告为“错误”，且不提供更多详细信息。
   > 
   > 如果 "**注销时禁用提示**" 设置为 "*未配置*", 则 *不能配置* **允许绕过的次数**, 也不能具有值。  
   > 
   > 此问题将在今后发布的更新中予以解决。 

7. 完成其他设置配置，然后保存配置文件。  

### <a name="manage-filevault"></a>管理 FileVault  

在 Intune 使用 FileVault 加密 macOS 设备之后，你便可在查看 Intune [加密报表](encryption-monitor.md)时查看和管理 FileVault 恢复密钥。  

## <a name="bitlocker-encryption-for-windows-10"></a>适用于 Windows 10 的 BitLocker 加密  

使用 Intune 在运行 Windows 10 的设备上配置 BitLocker 磁盘加密。 然后，使用 Intune 加密报表查看这些设备的加密详细信息。 还可以从设备访问 BitLocker 的重要信息，如 Azure Active Directory (Azure AD) 中所示。  

BitLocker 适用于运行 Windows 10 或更高版本的设备。  

为 Windows 10 或更高版本的平台创建用于 Endpoint Protection 的[设备配置配置文件](device-profile-create.md)时，请配置 BitLocker。 BitLocker 设置属于 Windows 10 Endpoint Protection 的 Windows 加密设置类别。    

![BitLocker 设置](./media/encrypt-devices/bitlocker-settings.png) 

### <a name="how-to-configure-windows-10-bitlocker"></a>如何配置 Windows 10 BitLocker  

1. 登录 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)，然后转到“设备配置”>“配置文件”>“创建配置文件”。  

2. 设置下列选项:  
   - 平台：Windows 10 及更高版本  
   - 配置文件类型：Endpoint Protection  

3. 选择“设置” > “Windows Encryption”。

4. 配置 BitLocker 的设置以满足你的业务需求，然后选择“确定”。  

5. 完成其他设置配置，然后保存配置文件。  

### <a name="manage-bitlocker"></a>管理 BitLocker  

在 Intune 使用 BitLocker 加密 Windows 10 设备之后，你便可在查看 Intune [加密报表](encryption-monitor.md)时查看和检索 BitLocker 恢复密钥。  

## <a name="next-steps"></a>后续步骤  

创建[设备符合性](compliance-policy-create-windows.md)策略  

使用加密报表管理以下内容：  
- [BitLocker 恢复密钥](encryption-monitor.md#bitlocker-recovery-keys)
- [FileVault 恢复密钥](encryption-monitor.md#filevault-recovery-keys)

查看可以使用 Intune 配置的加密设置：  
- [BitLocker](endpoint-protection-windows-10.md#windows-encryption)  
- [FileVault](endpoint-protection-macos.md#filevault)  
 
 
