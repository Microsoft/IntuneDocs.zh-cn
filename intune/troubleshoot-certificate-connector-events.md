---
title: 排查 Microsoft Intune 证书连接器和事件 ID 问题 | Microsoft Docs
description: 通过查看事件 ID 和说明对 Microsoft Intune 证书连接器进行故障排除，并评审 Intune 连接器服务的诊断代码。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/01/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8a282662032fe77cbf39da279c587bff31ad9e24
ms.sourcegitcommit: cf40f641af4746a1e34edd980dc6ec96fd040126
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2019
ms.locfileid: "70123219"
---
# <a name="intune-certificate-connector-events-and-diagnostic-codes"></a>Intune 证书连接器事件和诊断代码

从版本 6.1806.x.x 开始，Intune 连接器服务会在“事件查看器”（“应用程序和服务日志” > “Microsoft Intune 连接器”）中记录事件    。 使用这些事件可帮助解决 Intune 连接器配置中的潜在问题。 这些事件记录操作的成功和失败，并且还包含带有消息的诊断代码，以帮助 IT 管理员进行故障排除。

> [!TIP]  
> 若要解决问题并验证 Intune 连接器设置，请参阅[证书颁发机构脚本示例](https://aka.ms/intuneconnectorverificationscript)。

## <a name="event-ids-and-descriptions"></a>事件 ID 和说明

| 事件 ID      | 事件名称    | 事件说明 | 相关诊断代码 |
| ------------- | ------------- | -------------     | -------------            |
| 10010 | StartedConnectorService  | 连接器服务已启动 | 0x00000000, 0x0FFFFFFF |
| 10020 | StoppedConnectorService  | 连接器服务已停止 | 0x00000000, 0x0FFFFFFF |
| 10100 | CertificateRenewal_Success  | 连接器注册证书已成功更新 | 0x00000000, 0x0FFFFFFF |
| 10102 | CertificateRenewal_Failure  | 连接器注册证书更新失败。 重新安装连接器。 | 0x00000000, 0x00000405, 0x0FFFFFFF |
| 10302 | RetrieveCertificate_Error  | 未能从注册表中检索到连接器注册证书。 查看事件详细信息，获取与此事件相关的证书指纹。 | 0x00000000, 0x00000404, 0x0FFFFFFF |
| 10301 | RetrieveCertificate_Warning  | 查看事件详细信息中的诊断信息。 | 0x00000000, 0x00000403, 0x0FFFFFFF |
| 20100 | PkcsCertIssue_Success  | 已成功颁发 PKCS 证书。 查看事件详细信息，获取与此事件相关的设备 ID、用户 ID、CA 名称、证书模板名称和证书指纹。 | 0x00000000, 0x0FFFFFFF |
| 20102 | PkcsCertIssue_Failure  | 未能颁发 PKCS 证书。 查看事件详细信息，获取与此事件相关的设备 ID、用户 ID、CA 名称、证书模板名称和证书指纹。 | 0x00000000, 0x00000400, 0x00000401, 0x0FFFFFFF |
| 20200 | RevokeCert_Success  | 已成功撤销证书。 查看事件详细信息，获取与此事件相关的设备 ID、用户 ID、CA 名称和证书序列号。 | 0x00000000, 0x0FFFFFFF |
| 20202 | RevokeCert_Failure | 未能撤销证书。 查看事件详细信息，获取与此事件相关的设备 ID、用户 ID、CA 名称和证书序列号。 有关其他信息，请参阅 NDES SVC 日志。   | 0x00000000, 0x00000402, 0x0FFFFFFF |
| 20300 | Upload_Success | 已成功下载证书的请求或撤销数据。 查看事件详细信息，获取上传详细信息。 | 0x00000000, 0x0FFFFFFF |
| 20302 | Upload_Failure | 未能下载证书的请求或撤销数据。 查看“事件详细信息”>“上传状态”以确定故障点。| 0x00000000, 0x0FFFFFFF |
| 20400 | Download_Success | 已成功下载签署证书、下载客户端证书或撤销证书的请求。 查看事件详细信息，获取下载详细信息。  | 0x00000000, 0x0FFFFFFF |
| 20402 | Download_Failure | 未能下载签署证书、下载客户端证书或撤销证书的请求。 查看事件详细信息，获取下载详细信息。 | 0x00000000, 0x0FFFFFFF |
| 20500 | CRPVerifyMetric_Success  | 证书注册点已成功验证客户端质询 | 0x00000000, 0x0FFFFFFF |
| 20501 | CRPVerifyMetric_Warning  | 证书注册点已完成并拒绝了请求。 有关详细信息，请参阅诊断代码和消息。 | 0x00000000, 0x00000411, 0x0FFFFFFF |
| 20502 | CRPVerifyMetric_Failure  | 证书注册点未能验证客户端质询。 有关详细信息，请参阅诊断代码和消息。 有关与该质询相对应的设备 ID，请查看事件消息详细信息。 | 0x00000000, 0x00000408, 0x00000409, 0x00000410, 0x0FFFFFFF |
| 20600 | CRPNotifyMetric_Success  | 证书注册点已成功完成通知过程并已将证书发送到客户端设备。 | 0x00000000, 0x0FFFFFFF |
| 20602 | CRPNotifyMetric_Failure  | 证书注册点未能完成通知过程。 查看事件消息的详细信息，获取有关请求的信息。 验证 NDES 服务器和 CA 之间的连接。 | 0x00000000, 0x0FFFFFFF |

## <a name="diagnostic-codes"></a>诊断代码

| 诊断代码 | 诊断名称 | 诊断消息 |
| -------------   | -------------   | -------------      |
| 0x00000000 | 成功  | 成功 |
| 0x00000400 | PKCS_Issue_CA_Unavailable  | 证书颁发机构无效或无法访问。 验证证书颁发机构是否可用，以及服务器是否可以与之通信。 |
| 0x00000401 | Symantec_ClientAuthCertNotFound  | 在本地证书存储中找不到 Symantec 客户端身份验证证书。 请参阅文章[安装 Symantec 注册授权证书](https://docs.microsoft.com/intune/certificates-symantec-configure#install-the-symantec-registration-authorization-certificate)以获取详细信息。  |
| 0x00000402 | RevokeCert_AccessDenied  | 指定的帐户无权从 CA 撤销证书。 请参阅事件消息详情中的“CA 名称”字段以确定颁发 CA。  |
| 0x00000403 | CertThumbprint_NotFound  | 找不到与输入相匹配的证书。 注册证书连接器并重试。 |
| 0x00000404 | Certificate_NotFound  | 找不到与提供的输入相匹配的证书。 重新注册证书连接器并重试。 |
| 0x00000405 | Certificate_Expired  | 证书已过期。 重新注册证书连接器以更新证书，然后重试。 |
| 0x00000408 | CRPSCEPCert_NotFound  | 找不到 CRP 加密证书。 验证是否正确安装 NDES 和 Intune 连接器。 |
| 0x00000409 | CRPSCEPSigningCert_NotFound  | 无法检索签名证书。 验证 Intune 连接器服务配置是否正确，以及 Intune 连接器服务是否正在运行。 此外，验证证书下载事件是否成功。 |
| 0x00000410 | CRPSCEPDeserialize_Failed  | 未能反序列化 SCEP 质询请求。 验证是否正确安装 NDES 和 Intune 连接器。 |
| 0x00000411 | CRPSCEPChallenge_Expired  | 由于证书质询已过期，因此请求已被拒绝。 客户端设备可以在从管理服务器获取新的质询后重试。 |
| 0x0FFFFFFFF | Unknown_Error  | 我们无法完成你的请求，因为发生了服务器端错误。 请稍后重试。 |


## <a name="next-steps"></a>后续步骤
有关其他帮助，请使用[在 Microsoft Intune 中对 SCEP 证书配置文件部署进行故障排除](https://support.microsoft.com/help/4457481/troubleshooting-scep-certificate-profile-deployment-in-intune)指南。
