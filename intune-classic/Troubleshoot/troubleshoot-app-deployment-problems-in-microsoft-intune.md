---
title: "应用部署问题疑难解答"
description: "本主题有助于解决 Microsoft Intune 中的应用部署问题。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 09/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 28ac298e-fb73-4c1c-b3fd-8336639e05e6
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 1911c8a2460a98218027c40a26d81f1ca4c482f5
ms.openlocfilehash: 4d214ea9e85d6f08ecff42555cc7fbc36512a825
ms.contentlocale: zh-cn
ms.lasthandoff: 06/13/2017


---

# <a name="troubleshoot-app-deployment-problems-in-microsoft-intune"></a>Microsoft Intune 中的应用部署问题疑难解答

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

如果在使用 Intune 部署和管理应用时出现问题，请从这里开始。 本主题包含你可能会遇到的一些常见问题以及解决方案。

## <a name="common-app-deployment-error-codes"></a>常见的应用部署错误代码

|错误代码|可能的问题|建议的解决方法|
|--------------|--------------------|------------------------|
|0x80073CFF<br /><br />0x80CF201C（客户端错误）|若要安装此应用，你必须具有支持旁加载的系统。|确保使用受信任的签名对应用包进行了签名，并且确保在已启用 AllowAllTrustedApps 策略且已加入域的设备上安装了该应用包，或者在具有 Windows 旁加载许可证且已启用 AllowAllTrustedApps 策略的设备上安装了该应用包。|
|0x80073CF0|无法打开包。|可能的原因：<br /><br />-   未对包进行签名。<br />-   发布者名称与签名证书使用者不匹配。<br /><br />有关详细信息，请检查 AppxPackagingOM 事件日志。|
|0x80073CF3|包未通过更新、依赖关系或冲突验证|可能的原因：<br /><br />-   传入的包与已安装的包冲突。<br />-   找不到指定的包依赖关系。<br />-   包不支持正确的处理器体系结构。<br /><br />有关详细信息，请检查 AppXDeployment-Server 事件日志。|
|0x80073CFB|已经安装了提供的包，阻止重新安装此包|如果你正在安装的包与已安装的包并不完全相同，则可能会收到此错误。 确认数字签名也是包的一部分。 对包进行重新构建或者重新签名时，该包与以前安装的包在位方面不再完全相同。 用于修复此错误的两个可能的选项如下所示：<br /><br />-   递增应用的版本号，然后对包进行重新构建并重新签名。<br />-   在安装新包之前，请删除系统上每个用户的旧包。|
|0x87D1041C|应用程序安装成功，但未检测到应用程序。|- 应用已通过 Intune 成功部署，随后可能由最终用户卸载了。 指示用户从公司门户重新安装应用。 在设备下次签入时，将自动重新安装所需应用。|

## <a name="troubleshooting-apps-from-the-windows-store"></a>对 Windows 应用商店中的应用进行故障排除

[排除 Windows 应用商店应用的打包、部署和查询故障](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx)主题中的信息可帮助你解决使用 Intune 或其他方式从 Windows 应用商店安装应用时可能会遇到的问题。

## <a name="troubleshooting-app-deployment-to-pcs-managed-by-the-intune-software-client"></a>对由 Intune 软件客户端管理的电脑的应用部署进行故障排除
若要解决将应用部署到由 Intune 软件客户端管理的电脑时遇到的问题，可查看以下两个日志文件：
- %ProgramFiles%\Microsoft\OnlineManagement\Logs folder
- %ProgramFiles%\Microsoft\OnlineManagement\Updates\ReportingEvents.log

此外，若需要打开 Intune 的支持案例，将这些日志发送给 Microsoft 会很有帮助。


### <a name="next-steps"></a>后续步骤
如果此疑难解答信息没有帮助到你，请联系 Microsoft 支持部门，如[如何获取对 Microsoft Intune 的支持](how-to-get-support-for-microsoft-intune.md)中所述。

