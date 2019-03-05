---
title: 获取用于 Intune 的 Apple MDM 推送证书
titlesuffix: ''
description: 获取用于通过 Intune 管理 iOS 设备的 Apple MDM 推送证书。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/08/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5719d1f662cc644377057b07dd632288a5c16552
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/02/2019
ms.locfileid: "57238007"
---
# <a name="get-an-apple-mdm-push-certificate"></a>获取 Apple MDM Push Certificate

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

必须拥有 Apple MDM Push Certificate 才能使用 Intune 管理 iOS 和 macOS 设备。 在将证书添加到 Intune 后，用户可以通过以下方式注册其设备：

- 使用公司门户应用。

- 使用 Apple 的批量注册方法，例如设备注册计划、Apple School Manager 或 Apple 配置器。

有关注册选项的详细信息，请参阅[选择 iOS 设备的注册方式](enrollment-method-choose-ios.md)。

推送证书到期时必须续订。 续订时，请务必使用你在首次创建推送证书时使用的同一个 Apple ID。


## <a name="steps-to-get-your-certificate"></a>获取证书的步骤
在 [Azure 门户](https://portal.azure.com)中，依次选择“设备注册” > “Apple 注册” > “Apple MDM Push Certificate”，然后在 [Azure 门户](https://portal.azure.com)中按照以下步骤进行操作。

### <a name="step-1-grant-microsoft-permission-to-send-user-and-device-information-to-apple"></a>步骤 1。 授权 Microsoft 向 Apple 发送用户和设备信息
选择“我同意” 授予 Microsoft 向 Apple 发送数据的权限。

![“配置 MDM Push Certificate”屏幕，其中尚未设置 MDM Push。](./media/create-mdm-push-certificate.png)

### <a name="step-2-download-the-intune-certificate-signing-request-required-to-create-an-apple-mdm-push-certificate"></a>步骤 2。 下载创建 Apple MDM Push Certificate 所需的 Intune 证书签名请求
选择“下载 CSR”，将请求文件下载到本地并保存。 此文件用于从 Apple Push Certificate 门户请求信任关系证书。

  ### <a name="step-3-create-an-apple-mdm-push-certificate"></a>步骤 3. 创建 Apple MDM Push Certificate
选择“创建 MDM Push Certificate”，转到 Apple Push Certificate 门户。 使用公司 Apple ID 登录，然后单击“创建证书”。 选择“选择文件”并浏览到证书签名请求文件，然后选择“上传”。 在确认页上，选择“下载”以下载证书 (.pem) 文件，并将文件保存在本地。

> [!NOTE]
> 证书与用于创建它的 Apple ID 相关联。 最好是使用公司 Apple ID 来处理管理任务，并确保邮箱由多个用户（如通讯组列表）监视。 切勿使用个人 Apple ID。

### <a name="step-4-enter-the-apple-id-used-to-create-your-apple-mdm-push-certificate"></a>步骤 4. 输入用于创建 Apple MDM Push Certificate 的 Apple ID
记录此 ID 作为需要续订此证书时的提醒。

### <a name="step-5-browse-to-your-apple-mdm-push-certificate-to-upload"></a>步骤 5. 浏览到你的 Apple MDM Push Certificate 以进行上传
转到证书 (.pem) 文件，选择“打开”，然后选择“上传”。 通过推送证书，Intune 可以注册并管理 Apple 设备。

## <a name="renew-apple-mdm-push-certificate"></a>续订 Apple MDM Push Certificate
Apple MDM Push Certificate 有效期为一年，且必须手动续订才能维持 iOS 和 macOS 设备管理。 如果证书到期，则无法联系到已注册的 Apple 设备。

证书与用于创建它的 Apple ID 相关联。 使用创建证书所用的相同 Apple ID 续订 MDM Push Certificate。

1. 在 [Azure 门户](https://portal.azure.com)中，选择“设备注册” > “Apple 注册”，然后选择详细信息区域中的“Apple MDM Push Certificate”磁贴。
2. 选择“下载 CSR”，将请求文件下载到本地并保存。 此文件用于从 Apple Push Certificate 门户请求信任关系证书。
3. 选择“创建 MDM Push Certificate”，转到 Apple Push Certificate 门户。 找到要续订的证书并选择“续订”。
4. 在“续订 Push Certificate”屏幕上，提供备注以便在将来识别证书，选择“选择文件”浏览到下载的新请求文件，然后选择“上传”。
   > [!TIP]
   > 可以按一个证书的 UID 识别它。 在证书详细信息中检查“使用者 ID”以找到 UID 的 GUID 部分。 或者，在已注册的 iOS 设备上，转至“设置” > “常规” > “设备管理” > “管理配置文件” > “更多详细信息” > “管理配置文件”。 第二行项“主题”中包含可以匹配 Apple Push Certificates 门户中的证书的唯一 GUID。
 
6. 在“确认”屏幕上，选择“下载”并本地保存 .pem 文件。
7. 在 [Azure 门户](https://portal.azure.com)中，依次选择“Apple MDM Push Certificate”浏览图标、已从 Apple 下载的 .pem 文件和“上传”。

Apple MDM Push Certificate 显示“激活”，有效期为 365 天。
