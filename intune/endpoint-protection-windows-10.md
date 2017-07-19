---
title: "适用于 Windows 10 的 Intune Endpoint Protection 设置"
titleSuffix: Intune on Azure
description: "了解可用来控制 Windows 10 设备上的 Endpoint Protection 设置（如 BitLocker）的 Intune 设置。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: ilwu
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4994656afcf1cdb97fdcd3877f6dabdadfb7d374
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2017
---
# <a name="endpoint-protection-settings-for-windows-10-and-later-in-microsoft-intune"></a>Microsoft Intune 中的适用于 Windows 10 及更高版本的 Endpoint Protection 设置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

通过 Endpoint Protection 配置文件可以控制 Windows 10 设备上的安全功能（如 BitLocker）。

使用本主题中的信息，了解如何创建 Endpoint Protection 配置文件。

## <a name="create-an-endpoint-protection-profile"></a>创建 Endpoint Protection 配置文件

1. 登录到 Azure 门户中。
2. 选择“更多服务” > “监视 + 管理” > “Intune”。
3. 在“Intune”边栏选项卡上，选择“设备配置”。
2. 在“设备配置”边栏选项卡上，依次选择“管理” > “配置文件”。
3. 在配置文件边栏选项卡上，选择“创建配置文件”。
4. 在“创建配置文件”边栏选项卡上，输入设备功能配置文件的“名称”和“说明”。
5. 从“平台”下拉列表中，选择“Windows 10 及更高版本”。
6. 在“配置文件类型”下拉列表中，选择“Endpoint Protection”。 
7. 在“Windows 加密”边栏选项卡上，配置所需的设置。 使用本主题中的详细信息可帮助了解每个设置的作用。 完成后，请选择“确定”。
8. 返回到“创建配置文件”边栏选项卡，然后选择“创建”。

系统将创建配置文件并在“配置文件列表”边栏选项卡上显示出来。

## <a name="endpoint-protection-profile-settings-reference"></a>Endpoint Protection 配置文件设置参考

### <a name="windows-settings"></a>Windows 设置

- “需要加密设备 (仅限桌面版)”- 如果启用，将提示用户启用设备加密。 此外，系统还会请求用户确认尚未启用来自另一个提供程序的加密。 如果 Windows 加密开启时另一种加密方法处于活动状态，设备可能会变得不稳定。
- “要求加密存储卡 (仅限移动版)”- 启用此设置以对设备使用的任何可移动存储卡进行加密。


### <a name="bitlocker-base-settings"></a>BitLocker 基本设置

- “配置加密方法”- 启用此设置以配置操作系统、数据和可移动驱动器的加密算法。
    - “操作系统驱动器的加密”- 选择操作系统驱动器的加密方法。 建议使用 XTS-AES 算法。
    - “固定数据驱动器的加密”- 选择固定（内置）数据驱动器的加密方法。 建议使用 XTS-AES 算法。
    - “可移动数据驱动器的加密”- 选择可移动数据驱动器的加密方法。 如果在不运行 Windows 10 的设备上使用可移动驱动器，建议使用 AES-CBC 算法。


### <a name="bitlocker-os-drive-settings"></a>BitLocker OS 驱动器设置

- “在启动时需要额外身份验证” - 
    - “在没有兼容的 TPM 芯片的设备上阻止 BitLocker” - 
    - “TPM 启动”- 配置是允许、不允许还是必须要求 TPM 芯片。 
    - “TPM 启动 PIN”- 配置是允许、不允许还是必须要求使用带 TPM 芯片的启动 PIN。 
    - “TPM 启动密钥”- 配置是允许、不允许还是必须要求使用带 TPM 芯片的启动密钥。 
    - “TPM 启动密钥和 PIN”- 配置是允许、不允许还是必须要求使用带 TPM 芯片的启动密钥和 PIN。
- “最小 PIN 长度”- 启用此设置以配置 TPM 启动 PIN 的最小长度。
    - “最少字符数”- 输入启动 PIN 所需的字符数（介于 **4**-**20**）。
- “启用 OS 驱动器恢复”- 启用此设置以控制在所需启动信息不可用时如何恢复受 BitLocker 保护的操作系统驱动器。
    - “允许基于证书的数据恢复代理”- 如果希望数据恢复代理能够用于受 BitLocker 保护的操作系统驱动器，则启用此设置。
    - “用户创建恢复密码”- 配置是允许、不允许还是要求用户生成 48 位数的恢复密码。
    - “用户创建恢复密钥”- 配置是允许、不允许还是要求用户生成 256 位数的恢复密钥。
    - “隐藏 BitLocker 安装向导中的恢复选项”- 启用此设置以防止用户在打开 BitLocker 时看到或更改恢复选项。
    - “将 BitLocker 恢复信息保存到 AD DS”- 启用在 Active Directory 中存储 BitLocker 恢复信息。
    - “配置 BitLocker 恢复信息到 AD DS 的存储”- 配置 BitLocker 恢复信息的哪些部分存储在 Active Directory 中。 选择：
        - “备份恢复密码和密钥包”
        - “仅备份恢复密码”
    - “需要将恢复信息存储在 AD DS 后才能启用 BitLocker”- 启用此设置以阻止用户启用 BitLocker，除非设备已加入域，并且 BitLocker 恢复信息已成功存储在 Active Directory 中。
- “启用预启动恢复消息和 URL”- 启用此设置以配置预启动密钥恢复屏幕上显示的消息和 URL。
    - “预启动恢复消息”- 配置如何向用户显示预启动恢复消息。 选择：
        - “使用默认恢复消息和 URL”
        - “使用空的恢复消息和 URL”
        - “使用自定义恢复消息”
        - “使用自定义恢复 URL”


### <a name="bitlocker-fixed-data-drive-settings"></a>BitLocker 固定数据驱动器设置

- “拒绝对不受 BitLocker 保护的固定数据驱动器进行写入访问”- 如果启用，则必须在所有固定或内置数据驱动器上启用 BitLocker 保护，才能写入它们。
- “启用固定驱动器恢复”- 启用此设置以控制在所需启动信息不可用时如何恢复受 BitLocker 保护的固定驱动器。
    - “允许据恢复代理”- 如果希望数据恢复代理可用于受 BitLocker 保护的固定驱动器，则启用此设置。
    - “用户创建恢复密码”- 配置是允许、不允许还是要求用户生成 48 位数的恢复密码。  
    - “用户创建恢复密钥”- 配置是允许、不允许还是要求用户生成 256 位数的恢复密钥。
    - “隐藏 BitLocker 安装向导中的恢复选项”- 启用此设置以防止用户在打开 BitLocker 时看到或更改恢复选项。
    - “将 BitLocker 恢复信息保存到 AD DS”- 启用在 Active Directory 中存储 BitLocker 恢复信息。
    - “配置 BitLocker 恢复信息到 AD DS 的存储”- 配置 BitLocker 恢复信息的哪些部分存储在 Active Directory 中。 选择：
        - “备份恢复密码和密钥包”
        - “仅备份恢复密码”
    - “需要将恢复信息存储在 AD DS 后才能启用 BitLocker”- 启用此设置以阻止用户启用 BitLocker，除非设备已加入域，并且 BitLocker 恢复信息已成功存储在 Active Directory 中。


### <a name="bitlocker-removable-data-drive-settings"></a>BitLocker 可移动数据驱动器设置

- “拒绝对不受 BitLocker 保护的可移动数据驱动器进行写入访问”- 指定可移动存储驱动器是否需要 BitLocker 加密。
    - “阻止对另一组织中配置的设备进行写入访问”- 指定是否可以写入属于另一组织的可移动数据驱动器。



## <a name="next-steps"></a>后续步骤

如果想要继续操作并将此配置文件分配到组，请参阅[如何分配设备配置文件](device-profile-assign.md)。


