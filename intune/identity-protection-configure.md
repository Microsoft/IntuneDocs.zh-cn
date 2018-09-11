---
title: 在 Microsoft Intune 中配置标识保护设置 - Azure | Microsoft Docs
description: 添加设备配置文件，以便在 Microsoft Intune 中的 Windows 10 设备上设置 Windows Hello 企业版设置
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 8/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7012479023ece83ef475431c5cefe150ab2ef342
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2018
ms.locfileid: "43318017"
---
# <a name="configure-identity-protection-settings-in-microsoft-intune"></a>在 Microsoft Intune 中配置标识保护设置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

标识保护配置文件控制 Windows Hello 企业版在托管的 Windows 10 设备上的预配和配置方式。 创建此配置文件以配置：  
* Windows Hello 企业版的设备和用户可用性。
* 设备 PIN 要求。
* 用户可用于和不可用于登录其设备的手势。  

 可以向选定用户和设备组，或向所有用户和所有设备分配此配置文件。 组签入到 Intune 时，会收到标识保护配置文件。    

使用本文中的信息来创建标识保护配置文件。 然后[将配置文件分配](device-profile-assign.md)给用户和设备组。

此功能适用于运行以下版本的设备：  
- Windows 10 及更高版本
- Windows Holographic for Business  

## <a name="create-a-device-profile-with-identity-protection-settings"></a>创建包含标识保护设置的设备配置文件

1. 登录到 [Azure 门户](https://portal.azure.com)。
2. 选择“所有服务”，筛选“Intune”，然后选择“Microsoft Intune”。
3. 选择“设备配置” > “配置文件” > “创建配置文件”。
4. 输入标识保护配置文件的“名称”和“说明”。
5. 从“平台”下拉列表中，选择“Windows 10 及更高版本”。 仅运行 Windows 10 及更高版本的设备支持 Windows Hello 企业版。
6. 在“配置文件类型”下拉列表中，选择“标识保护”。
7. 在“Windows Hello 企业版”窗格中，为“配置 Windows Hello 企业版”从下列选项中进行选择：
    * 已禁用。 如果不想要使用 Windows Hello 企业版，请选择此设置。 屏幕上的所有其他设置将不可用。
    * 已启用。 如果想要配置 Windows Hello 企业版设置，请选择此设置。  

8. 如果在上一步中选择了“启用”，请配置应用于已注册的目标 Windows 10 和 Windows 10 移动版设备及用户的必需设置。

> [!NOTE]
> 在仅向用户分配标识保护配置文件时，设备上下文将默认为“未配置”。  

   - 最小 PIN 长度/最大 PIN 长度。 将设备配置为使用你指定的最小和最大 PIN 长度，以帮助确保安全登录。 默认 PIN 长度为 6 个字符，但可以强制使用 4 个字符的最小长度。 最大 PIN 长度为 127 个字符。  

   - 在 PIN 中使用小写字母/在 PIN 中使用大写字母/在 PIN 中使用特殊字符。 你可以通过要求在 PIN 中使用大写字母、小写字母和特殊字符，从而强制实施更强的 PIN。 选择：

     - “允许”。 用户可以在其 PIN 中使用该字符类型，但不强制使用。

     - “必需”。 用户在其 PIN 中必须至少包含其中一种字符类型。 例如，常见的做法是要求包含至少一个大写字母和一个特殊字符。

     - “不允许”（默认）。 用户必须在他们的 PIN 中使用这些字符类型。 （如果未配置此设置，也会发生此行为。）<br>特殊字符包括：! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~

   - “PIN 有效期（天数）”。 比较好的一种做法是指定 PIN 的有效期，在超过此期限后，最终用户必须更改该 PIN。 默认值为 41 天。

   - “记住 PIN 历史记录”。 限制重复使用以前用过的 PIN。 默认情况下，不能重复使用最近用过的 5 个 PIN。  
   - **启用 PIN 恢复**：允许用户通过使用 Windows Hello 企业版 PIN 恢复服务更改其 PIN。 
       - “启用”。 云服务对要存储在设备上的 PIN 恢复机密进行加密。 用户可根据需要更改其 PIN。  
       - “未配置”（默认）。 未创建或存储 PIN 恢复机密。 如果忘记了用户的 PIN，获取新 PIN 的唯一方法是删除现有 PIN 并创建一个新 PIN。 用户将需要重新注册通过旧 PIN 获取其访问权限的任何服务。  
   
   - “使用受信任的平台模块 (TPM)”。 TPM 芯片额外提供了一层数据安全。 选择下列值之一：  
     - “启用”。 仅限可访问 TPM 的设备预配 Windows Hello 企业版。
     - “不配置”。 所有设备都可预配 Windows Hello 企业版，即使没有可用 TPM 也是如此。 设备将首先尝试使用 TPM，但如果 TPM 不可用，设备可使用软件加密。  

   - “允许生物识别身份验证”。 启用面部识别或指纹等生物识别身份验证作为 Windows Hello 企业版 PIN 的替代方法。 如果生物识别身份验证失败，则用户仍必须配置工作 PIN。 选择：

     - “启用”。 Windows Hello 企业版允许进行生物识别身份验证。
     - “未配置”（默认）。 Windows Hello 企业版阻止生物识别身份验证（适用于所有帐户类型）。

   - “在可用时使用增强的反电子欺骗技术”。 配置是否在支持 Windows Hello 反电子欺骗功能的设备上使用该功能（例如，检测面部照片而非真实的面部）。
       - “启用”。 Windows 将在支持反电子欺骗技术时要求所有用户对面部识别功能使用此技术。  
       - “未配置”（默认）。 Windows 尊重设备上的反电子欺骗配置。

   - “本地资源证书”。 
       - “启用”。 允许 Windows Hello 企业版使用证书对本地资源进行身份验证。
       - “未配置”（默认）。 阻止 Windows Hello 企业版使用证书对本地资源进行身份验证。  
9. 单击“确定”以保存配置文件。  

该配置文件已创建并显示在“设备配置 - 配置文件”列表中。 若要继续操作并将此配置文件分配到组，请参阅[如何分配设备配置文件](device-profile-assign.md)。  

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->
