---
title: "获取 Apple MDM Push Certificate"
titleSuffix: Intune on Azure
description: "了解获取 Apple MDM Push Certificate 以使用 Intune 管理 iOS 设备的步骤。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 04/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3df23e1f29543701cf3806a8fecc132ef3ac4f43
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2017
---
# <a name="get-an-apple-mdm-push-certificate"></a>获取 Apple MDM Push Certificate

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune 启用了 iPad、iPhone 和 Mac 计算机的移动设备管理 (MDM)，并允许用户访问公司电子邮件和应用。 必须拥有 MDM Push Certificate 才能使用 Intune 管理 iOS 和 Mac 设备。 在将证书添加到 Intune 后，用户可以安装公司门户应用以注册其设备。 此外，你还可以设置具备 Apple 设备注册计划的公司所有的 iOS 设备管理，或使用 Apple Configurator 等注册设备。 有关注册选项的详细信息，请参阅[选择 iOS 设备的注册方式](enrollment-method-choose-ios.md)。

## <a name="steps-to-get-your-certificate"></a>获取证书的步骤
在 Intune 门户中，选择“设备注册” > “Apple 注册”“Apple MDM Push Certificate”，然后按照 Azure 门户中的编号步骤操作，如下所示。

**步骤 1.下载创建 Apple MDM Push Certificate 所需的 Intune 证书签名请求。**<br>
选择“下载 CSR”，本地下载并保存 .csr 文件。 .Csr 文件用于从 Apple 推送证书门户请求信任关系证书。

**步骤 2：创建 Apple MDM Push Certificate。**<br>
选择“创建 MDM Push Certificate”，转到 Apple Push Certificate 门户。 使用公司 Apple ID 登录，从而使用 .csr 文件创建 Push Certificate。 在 Apple Push Certificates 门户上选择“上传”后，将收到 .json 文件。 请将此文件用于 Push Certificate。 完成下载后，返回第三方服务器证书的 Apple Push Certificates 门户，然后选择“下载”。 下载 Push Certficate（.pem 文件）并在本地保存该文件。

> [!NOTE]
> 证书与用于创建它的 Apple ID 相关联。 将公司 Apple ID 用于管理工具，此为最佳做法。 切勿使用个人 Apple ID。

**步骤 3：输入用于创建 Apple MDM Push Certificate 的 Apple ID。**

**步骤 4：浏览到你的 Apple MDM Push Certificate 以进行上传。**<br>
转到证书 (.pem) 文件，选择“打开”，然后选择“上传”。 使用 Push Certificate，Intune 可通过将策略推送到已注册的移动设备来注册和管理 iOS 设备。

## <a name="renew-apple-mdm-push-certificate"></a>续订 Apple MDM Push Certificate
Apple MDM Push Certificate 有效期为一年，且必须手动续订才能维持 iOS 和 macOS 设备管理。 如果证书到期，则无法联系到已注册的 Apple 设备。

证书与用于创建它的 Apple ID 相关联。 使用创建证书所用的相同 Apple ID 续订 MDM Push Certificate。

> [!NOTE]
> 证书与用于创建它的 Apple ID 相关联。 将公司 Apple ID 用于管理工具，此为最佳做法。 切勿使用个人 Apple ID。

1. 在 Intune 门户中，选择“设备注册” > “Apple 注册”，然后选择“Apple MDM Push Certificate”。
2. 选择“下载 CSR”，本地下载并保存 .csr 文件。 .Csr 文件用于从 Apple 推送证书门户请求信任关系证书。
3. 找到要续订的证书并选择“续订”。
4. 在“续订 Push Certificate”屏幕上，提供备注以便有助于将来识别证书，选择“选择文件”浏览至要下载的新 .csr 文件，然后选择“上传”。
5. 在“确认”屏幕上，选择“下载”并本地保存 .pem 文件。
6. 在 Azure Intune 门户中，选择“Apple MDM Push Certificate”浏览图标，然后选择已从 Apple 下载的 .pem 文件，最后选择“上传”。

Apple MDM Push Certificate 显示“激活”，有效期为 365 天。
