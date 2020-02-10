---
title: 在 Microsoft Intune 中使用 SCEP 时，对证书成功部署到设备的报告进行故障排除 | Microsoft Docs
description: 对有关成功部署了由 SCEP 证书配置文件预配的证书的 NDES 和 Intune 连接器报告进行故障排除。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/30/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2ccc738626efc140efca46d1b997164ed36dd37f
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2020
ms.locfileid: "76916014"
---
# <a name="troubleshoot-ndes-reporting-of-certificate-deployments-in-microsoft-intune"></a>在 Microsoft Intune 中对证书部署的 NDES 报告进行故障排除

使用以下信息确认 NDES 和 Microsoft Intune 证书连接器成功向 Intune 报告证书已传送到设备。 向 Intune 报告是使用 SCEP 证书配置文件为 Windows 设备预配证书的最后阶段。

本文适用于 [SCEP 通信工作流](troubleshoot-scep-certificate-profiles.md)的步骤 6。

## <a name="review-for-signs-of-successful-reporting"></a>检查报告是否成功

如果报告成功，将在 NDES 服务器上找到类似于以下示例的条目：

- **IIS 日志**：

  `fe80::f53d:89b8:c3e8:5fec%13 POST /CertificateRegistrationSvc/Certificate/Notify - 443 - fe80::f53d:89b8:c3e8:5fec%13 NDES_Plugin - 204 0 0 277 62`

- **NDESPlugin.log**：

  ```
  Calling Notifyrequest ...
  Sending request to certificate registration point.
  Exiting Notify with 0x0
  ```

- **CertificateRegistrationPoint.svclog**：

  ![Intune 证书连接器日志](../protect/media/troubleshoot-scep-certificate-reporting/certificate-registration-point-log.png)

- **NDESConnector.svclog**：

  ![Intune 证书连接器日志](../protect/media/troubleshoot-scep-certificate-reporting/ndesconnector-log.png)

- **CertificateRequestStatus**：

  转到 %ProgramFiles%\Microsoft Intune\CertificateRequestStatus  文件夹，在该文件夹中，你将看到包含证书请求状态文件的“失败”  、“处理”  和“成功”  文件夹。

  如果成功处理了证书请求，则会在“成功”  文件夹中看到新文件。 可以使用 Notepad.exe  打开文件，并查看 Intune 证书连接器上传到 Intune 服务的数据。 上传的数据包括 CertificateSerialNumber  、UserID  、DeviceID  和 Thumbprint  等详细信息。

### <a name="troubleshoot-stuck-files"></a>滞留文件故障排除

如果未在“成功”  文件夹中看到创建任何新文件，请检查是否有任何文件滞留在“处理”  文件夹中。

验证是否在 NDES 服务器上启动了 Intune 连接器服务，并验证 Ndesconnector.svclog 中是否没有错误。

## <a name="next-steps"></a>后续步骤

[如何获取对 Microsoft Intune 的支持](../fundamentals/get-support.md)
