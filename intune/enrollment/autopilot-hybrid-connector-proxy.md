---
title: 配置适用于 Active Directory 的 Intune 连接器的代理设置
description: 介绍如何将适用于 Active Directory 的 Intune 连接器配置为与现有本地代理服务器结合使用。
keywords: ''
author: master11218
ms.author: tanvira
manager: smantri
ms.date: 4/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tanvira
ms.suite: ems
search.appverid: ''
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 529bf4cbf3658d492776afc0433926d85535b1f8
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723354"
---
# <a name="work-with-existing-on-premises-proxy-servers"></a>与现有本地代理服务器结合使用

本文介绍如何将适用于 Active Directory 的 Intune 连接器配置为与出站代理服务器结合使用。 这适用于网络环境中已有代理的客户。

有关连接器工作方式的详细信息，请参阅[了解 Azure AD 应用程序代理连接器](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-connectors)。

## <a name="bypass-outbound-proxies"></a>不使用出站代理

连接器具有发出出站请求的基础 OS 组件。 这些组件使用 Web 代理自动发现 (WPAD) 自动尝试在网络上查找代理服务器。

OS 组件尝试通过执行针对 wpad.domainsuffix 的 DNS 查找，来查找代理服务器。 如果该查找在 DNS 中解析，系统会向 IP 地址发出针对 wpad.dat 的 HTTP 请求。 此请求会成为环境中的代理配置脚本。 连接器使用此脚本选择出站代理服务器。 但是，连接器通信流可能仍无法通过，因为代理上需要其他配置设置。

可以将连接器配置为绕过本地代理，以确保它使用与 Azure 服务的直接连接。 只要网络策略允许，我们就建议使用此方法，因为这意味着减少了一个需要维护的配置。

若要禁用连接器的出站代理，请编辑 :\Program Files\Microsoft Intune\ODJConnector\ODJConnectorUI\ODJConnectorUI.exe.config 文件，并在以下代码示例所示的部分中添加代理地址和代理端口：

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <system.net>  
        <defaultProxy>   
            <proxy proxyaddress="<PROXY ADDRESS HERE>:<PORT HERE>" bypassonlocal="True" usesystemdefault="True"/>   
        </defaultProxy>  
    </system.net>
    <runtime>
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
            <dependentAssembly>
                <assemblyIdentity name="mscorlib" publicKeyToken="b77a5c561934e089" culture="neutral"/>
                <bindingRedirect oldVersion="0.0.0.0-2.0.0.0" newVersion="4.6.0.0" />
            </dependentAssembly>
        </assemblyBinding>
    </runtime>
    <startup> 
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6" />
    </startup>
    <appSettings>
        <add key="SignInURL" value="https://portal.manage.microsoft.com/Home/ClientLogon"/>
        <add key="LocationServiceEndpoint" value="RestUserAuthLocationService/RestUserAuthLocationService/ServiceAddresses"/>
    </appSettings>
</configuration>
```

若要确保连接器更新服务也绕过代理，请对 C:\Program Files\Microsoft Intune\ODJConnector\ODJConnectorSvc\ODJConnectorSvc.exe.config 做出类似更改。

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <system.net>  
        <defaultProxy>   
            <proxy proxyaddress="<PROXY ADDRESS HERE>:<PORT HERE>" bypassonlocal="True" usesystemdefault="True"/>   
        </defaultProxy>  
    </system.net>
    <startup>
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6" />
    </startup>
    <appSettings>
        <add key="BaseServiceAddress" value="https://manage.microsoft.com/" />
    </appSettings>
</configuration>
```

请务必对原始文件进行备份，以应对需要还原到默认 .config 文件的情况。

修改配置文件之后，需要重新启动 Intune 连接器服务。 

1. 打开“services.msc”  。
2. 找到并选择“Intune ODJConnector 服务”  。
3. 选择“重启”  。

![服务重启的屏幕截图](./media/autopilot-hybrid-connector-proxy/service-restart.png)


## <a name="next-steps"></a>后续步骤

[管理设备](../remote-actions/device-management.md)