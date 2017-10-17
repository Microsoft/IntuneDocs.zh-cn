---
title: "软件更新疑难解答"
description: "解决 Microsoft Intune 中的软件更新问题。"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d17b70f4-17b4-4d89-88fd-70fa4f34fbea
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1a3f5d94d5b9b902c4b07939e822076215c01d7c
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/10/2017
---
# <a name="troubleshoot-software-updates-in-microsoft-intune"></a>排查 Microsoft Intune 中的软件更新问题

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

本节中的信息有助于解决 Microsoft Intune 中的软件更新问题。

如果此信息未解决你的问题，请参阅[如何获取对 Microsoft Intune 的支持](how-to-get-support-for-microsoft-intune.md)，了解更多获得帮助的方法。

## <a name="update-agent-error-codes"></a>更新代理错误代码

下表列出了 Intune **更新代理**错误代码。 如果无法在此表中找到特定错误代码，请参阅 [Windows Update Agent Result Codes（Windows 更新代理结果代码）](http://go.microsoft.com/fwlink/?LinkID=221542)。

|错误代码|符号名称|更多信息|
|--------------|-----------------|--------------------|
|**0x00cf0001**|OM_S_SERVICE_STOP|已成功停止代理。|
|**0x00cf0003**|OM_S_UPDATE_ERROR|操作已成功完成，但是更新应用程序期间发生错误。|
|**0x00cf0004**|OM_S_MARKED_FOR_DISCONNECT|回拨被标记为稍后断开，因为运行回拨时出现了一个断开操作的请求。|
|**0x00cf0005**|OM_S_REBOOT_REQUIRED|必须重新启动系统才能完成更新安装。|
|**0x00cf0006**|OM_S_ALREADY_INSTALLED|在系统上已经安装了要安装的更新。|
|**0x00cf0007**|OM_S_ALREADY_UNINSTALLED|在系统上未安装要删除的更新。|
|**0x00cf2015**|OM_S_UH_INSTALLSTILLPENDING|正在进行更新安装。|
|**0x80cf0001**|OM_E_NO_SERVICE|代理无法提供服务。|
|**0x80cf0002**|OM_E_MAX_CAPACITY_REACHED|超出了服务的最大容量。|
|**0x80cf0003**|OM_E_UNKNOWN_ID|找不到 ID。|
|**0x80cf0004**|OM_E_NOT_INITIALIZED|无法初始化对象。|
|**0x80cf0007**|OM_E_INVALIDINDEX|集合的索引无效。|
|**0x80cf0008**|OM_E_ITEMNOTFOUND|找不到查询的项目的键。|
|**0x80cf0009**|OM_E_OPERATIONINPROGRESS|正在进行冲突的操作。 某些操作，如多个安装无法同时执行。|
|**0x80cf000B**|OM_E_CALL_CANCELLED|已经取消了操作。|
|**0x80cf000C**|OM_E_NOOP|无需进行操作。|
|**0x80cf000D**|OM_E_XML_MISSINGDATA|代理找不到更新的 XML 数据中的必需信息。|
|**0x80cf000E**|OM_E_XML_INVALID|代理发现了更新的 XML 数据中的无效信息。|
|**0x80cf000F**|OM_E_CYCLE_DETECTED|在元数据中检测到循环的更新关系。|
|**0x80cf0010**|OM_E_TOO_DEEP_RELATION|更新关系嵌套得太深而无法评估。|
|**0x80cf0011**|OM_E_INVALID_RELATIONSHIP|发现无效的更新关系。|
|**0x80cf0012**|OM_E_REG_VALUE_INVALID|读取了无效的注册表值。|
|**0x80cf0013**|OM_E_DUPLICATE_ITEM|操作已尝试向列表添加重复项目。|
|**0x80cf0014**|OM_E_INVALID_INSTALL_REQUESTED|调用程序无法对安装所请求的更新进行安装。|
|**0x80cf0016**|OM_E_INSTALL_NOT_ALLOWED|操作已尝试进行安装，但另一个安装正在进行中，或者系统正在挂起必需的重启。|
|**0x80cf0017**|OM_E_NOT_APPLICABLE|未执行操作，因为没有合适的更新。|
|**0x80cf0018**|OM_E_NO_USERTOKEN|操作失败，因为缺少所需的用户标记。|
|**0x80cf0019**|OM_E_EXCLUSIVE_INSTALL_CONFLICT|无法同时与其他更新一起安装专用更新。|
|**0x80cf001A**|OM_E_POLICY_NOT_SET|未设置策略值。|
|**0x80cf001D**|OM_E_INVALID_UPDATE|更新包含无效的元数据。|
|**0x80cf001E**|OM_E_SERVICE_STOP|无法完成操作，因为正在关闭服务或系统。|
|**0x80cf001F**|OM_E_NO_CONNECTION|无法完成操作，因为网络连接不可用。|
|**0x80cf0020**|OM_E_NO_INTERACTIVE_USER|无法完成操作，因为没有登录的交互用户。|
|**0x80cf0021**|OM_E_TIME_OUT|无法完成操作，因为操作超时。|
|**0x80cf0022**|OM_E_ALL_UPDATES_FAILED|操作针对所有更新已失败。|
|**0x80cf0024**|OM_E_NO_UPDATE|不存在更新。|
|**0x80cf0025**|OM_E_USER_ACCESS_DISABLED|组策略设置阻止访问 Windows Update。|
|**0x80cf0026**|OM_E_INVALID_UPDATE_TYPE|更新的类型无效。|
|**0x80cf0028**|OM_E_UNINSTALL_NOT_ALLOWED|无法卸载更新，因为请求并非来源于 WSUS 服务器。|
|**0x80cf0029**|OM_E_INVALID_PRODUCT_LICENSE|搜索可能已经遗漏了某些更新，或者在系统上可能存在未许可的应用程序。|
|**0x80cf002C**|OM_E_BIN_SOURCE_ABSENT|无法安装增量压缩更新，因为它需要源。|
|**0x80cf002D**|OM_E_SOURCE_ABSENT|无法安装完整文件更新，因为它需要源。|
|**0x80cf002E**|OM_E_WU_DISABLED|不允许访问非管理的服务器。|
|**0x80cf002F**|OM_E_CALL_CANCELLED_BY_POLICY|无法完成操作，因为已经设置了 **DisableWindowsUpdateAccess** 策略。|
|**0x80cf0030**|OM_E_INVALID_PROXY_SERVER|代理列表的格式无效。|
|**0x80cf0031**|OM_E_INVALID_FILE|文件的格式不正确。|
|**0x80cf0032**|OM_E_INVALID_CRITERIA|搜索条件字符串无效。|
|**0x80cf0034**|OM_E_DOWNLOAD_FAILED|无法下载更新。|
|**0x80cf0035**|OM_E_UPDATE_NOT_PROCESSED|未处理更新。|
|**0x80cf0036**|OM_E_INVALID_OPERATION|对象的当前状态不允许此操作。|
|**0x80cf0037**|OM_E_NOT_SUPPORTED|不支持该操作。|
|**0x80cf0038**|OM_E_WINHTTP_INVALID_FILE|下载的文件具有意外的内容类型。|
|**0x80cf0039**|OM_E_TOO_MANY_RESYNC|服务器请求代理重新同步次数太多。|
|**0x80cf0043**|OM_E_NO_UI_SUPPORT|不支持 WUA UI。|
|**0x80cf0044**|OM_E_PER_MACHINE_UPDATE_ACCESS_DENIED|只有管理员才能对每台计算机的更新执行此操作。|
|**0x80cf0045**|OM_E_UNSUPPORTED_SEARCHSCOPE|利用不支持的范围尝试了搜索。|
|**0x80cf0046**|OM_E_BAD_FILE_URL|URL 未指向文件。|
|**0x80cf0047**|OM_E_NOTSUPPORTED|不支持请求的操作。|
|**0x80cf0049**|OM_E_OUTOFRANGE|数据超出范围。|
|**0x80cf004A**|OM_E_INVALIDWUAVERSION|数据包含无效的版本。|
|**0x80cf004B**|OM_E_SEARCH_COMPLETED_WITH_SOME_FAILURES|搜索调用已完成，但无法检测某些更新。|
|**0x80cf004C**|OM_E_DOWNLOAD_COMPLETED_WITH_SOME_FAILURES|下载调用已完成，但无法下载某些更新。|
|**0x80cf004D**|OM_E_INSTALL_COMPLETED_WITH_SOME_FAILURES|安装调用已完成，但无法安装某些更新。|
|**0x80cf004E**|OM_E_WINUPDATE_CACHE_UNINITIALIZED|Windows Update 缓存为空，因为尚未对其进行初始化。|
|**0x80cf0436**|OM_E_PT_CATALOG_SYNC_REQUIRED|服务器不支持特定于类别的搜索。 必须改为发放完整目录搜索。|
|**0x80cf0437**|OM_E_PT_SECURITY_VERIFICATION_FAILURE|通过服务授权时出现问题。|
|**0x80cf0438**|OM_E_PT_ENDPOINT_UNREACHABLE|没有到终结点的路由或网络连接。|
|**0x80cf0439**|OM_E_PT_INVALID_FORMAT|接收的数据未达到数据协定期望。|
|**0x80cf043A**|OM_E_PT_INVALID_URL|URL 无效。|
|**0x80cf043B**|OM_E_PT_NWS_NOT_LOADED|无法加载 NWS 运行时。|
|**0x80cf043C**|OM_E_PT_PROXY_AUTH_SCHEME_NOT_SUPPORTED|不支持代理身份验证方案。|
|**0x80cf043D**|OM_E_SERVICEPROP_NOTAVAIL|请求的服务属性不可用。|
|**0x80cf043E**|OM_E_PT_ENDPOINT_REFRESH_REQUIRED|终结点提供程序插件需要联机刷新。|
|**0x80cf043F**|OM_E_PT_ENDPOINTURL_NOTAVAIL|请求的服务终结点的 URL 不可用。|
|**0x80cf0440**|OM_E_PT_ENDPOINT_DISCONNECTED|到服务终结点的连接已终止。|
|**0x80cf0441**|OM_E_PT_INVALID_OPERATION|操作无效，因为协议发话者处于不合适的状态。|
|**0x80cf0FFF**|OM_E_UNEXPECTED|由于另一个错误代码未解释的原因，操作失败。|
|**0x80cf1001**|OM_E_MSI_WRONG_VERSION|搜索可能错过了某些更新，因为 Windows Installer 早于版本 3.1。|
|**0x80cf1002**|OM_E_MSI_NOT_CONFIGURED|搜索可能错过了某些更新，因为未配置 Windows Installer。|
|**0x80cf1003**|OM_E_MSP_DISABLED|搜索可能错过了某些更新，因为策略禁用了 Windows Installer 修补。|
|**0x80cf1004**|OM_E_MSI_WRONG_APP_CONTEXT|无法应用更新，因为应用程序是按用户安装的。|
|**0x80cf2000**|OM_E_UH_REMOTEUNAVAILABLE|向远程更新处理程序提出的请求无法完成，因为远程进程不可用。|
|**0x80cf2001**|OM_E_UH_LOCALONLY|向远程更新处理程序提出的请求无法完成，因为该处理程序只是本地处理程序。|
|**0x80cf2003**|OM_E_UH_REMOTEALREADYACTIVE|无法创建远程更新处理程序，因为已经存在一个远程更新处理程序。|
|**0x80cf2004**|OM_E_UH_DOESNOTSUPPORTACTION|向处理程序提出的安装(卸载)更新的请求无法完成，因为更新不支持安装(卸载)。|
|**0x80cf2005**|OM_E_UH_WRONGHANDLER|无法完成操作，因为指定了错误的处理程序。|
|**0x80cf2006**|OM_E_UH_INVALIDMETADATA|无法完成处理程序操作，因为更新包含无效的元数据。|
|**0x80cf2007**|OM_E_UH_INSTALLERHUNG|无法完成操作，因为安装程序超出了时间限制。 检查是否已批准部署需要用户交互的更新。 在此情况下，必须修订更新安装参数，以便能够以无提示方式安装更新。|
|**0x80cf2008**|OM_E_UH_OPERATIONCANCELLED|更新处理程序执行的操作被取消。|
|**0x80cf2009**|OM_E_UH_BADHANDLERXML|无法完成操作，因为特定于处理程序的元数据无效。|
|**0x80cf200B**|OM_E_UH_INSTALLERFAILURE|安装程序无法安装(卸载)一个或多个更新。|
|**0x80cf200D**|OM_E_UH_NEEDANOTHERDOWNLOAD|更新处理程序未安装更新，因为必须重新下载该更新。|
|**0x80cf200E**|OM_E_UH_NOTIFYFAILURE|更新处理程序无法发送安装(卸载)操作的状态通知。|
|**0x80cf2014**|OM_E_UH_POSTREBOOTSTILLPENDING|更新的重新启动之后的操作仍然正在进行。|
|**0x80cf2015**|OM_E_UH_POSTREBOOTRESULTUNKNOWN|无法确定更新的重新启动之后的操作的结果。|
|**0x80cf2016**|OM_E_UH_POSTREBOOTUNEXPECTEDSTATE|在更新的重新启动之后的操作完成之后，更新的状态发生意外。|
|**0x80cf2017**|OM_E_UH_NEW_SERVICING_STACK_REQUIRED|在下载或安装此更新之前必须先更新操作系统服务堆栈。|
|**0x80cf2018**|OM_E_UH_CALLED_BACK_FAILURE|回拨安装程序进行了回拨，但出现了错误。|
|**0x80cf2019**|OM_E_UH_CUSTOMINSTALLER_INVALID_SIGNATURE|自定义安装程序签名与更新所需的签名不匹配。|
|**0x80cf201A**|OM_E_UH_UNSUPPORTED_INSTALLCONTEXT|安装程序不支持安装配置。|
|**0x80cf201B**|OM_E_UH_INVALID_TARGETSESSION|安装的目标会话无效。|
|**0x80cf2FFF**|OM_E_UH_UNEXPECTED|另一个 OM_E_UH_* 代码未涵盖更新处理程序错误。|
|**0x80cf3FFD**|OM_E_NON_UI_MODE|在非 UI 模式下无法显示 UI。 可能未安装 Windows 更新客户端 UI 模块。|
|**0x80cf3FFE**|OM_E_WUCLTUI_UNSUPPORTED_VERSION|不支持 WU 客户端 UI 导出函数的此版本。|
|**0x80cf3FFF**|OM_E_AUCLIENT_UNEXPECTED|发生了另一个 OM_E_AUCLIENT_* 错误代码未涵盖的用户界面错误。|
|**0x80cf4007**|OM_E_PT_SOAPCLIENT_SOAPFAULT|与 **SOAPCLIENT_SOAPFAULT** 相同。 SOAP 客户端失败，因为发生了 **OM_E_PT_SOAP_*** 错误代码类型的 SOAP 故障。|
|**0x80cf4008**|OM_E_PT_SOAPCLIENT_PARSEFAULT|与 **SOAPCLIENT_PARSEFAULT_ERROR** 相同。  SOAP 客户端无法分析 SOAP 故障错误。|
|**0x80cf400A**|OM_E_PT_SOAPCLIENT_PARSE|与 **SOAPCLIENT_PARSE_ERROR** 相同。  SOAP 客户端无法分析服务器的响应。|
|**0x80cf400B**|OM_E_PT_SOAP_VERSION|与 **SOAP_E_VERSION_MISMATCH** 相同。 SOAP 客户端发现 SOAP 信封的命名空间无法识别。|
|**0x80cf400C**|OM_E_PT_SOAP_MUST_UNDERSTAND|与 **SOAP_E_MUST_UNDERSTAND** 相同。 SOAP 客户端无法解释标头。|
|**0x80cf400D**|OM_E_PT_SOAP_CLIENT|与 **SOAP_E_CLIENT** 相同。 SOAP 客户端发现消息格式不正确。 请在重新发送之前先进行更正。|
|**0x80cf400E**|OM_E_PT_SOAP_SERVER|与 **SOAP_E_SERVER** 相同。 由于服务器错误的缘故而无法处理 SOAP 消息。 请稍后重新发送。|
|**0x80cf4010**|OM_E_PT_EXCEEDED_MAX_SERVER_TRIPS|到服务器的往返次数超过了最大限制。|
|**0x80cf4012**|OM_E_PT_DOUBLE_INITIALIZATION|初始化失败，因为已经初始化了对象。|
|**0x80cf4013**|OM_E_PT_INVALID_COMPUTER_NAME|无法确定计算机名。|
|**0x80cf4015**|OM_E_PT_REFRESH_CACHE_REQUIRED|服务器的回复表明服务器已发生更改或者 Cookie 无效。 请刷新内部缓存并重试。|
|**0x80cf4016**|OM_E_PT_HTTP_STATUS_BAD_REQUEST|与 **HTTP 状态 400** 相同。 服务器无法处理请求，因为语法无效。|
|**0x80cf4017**|OM_E_PT_HTTP_STATUS_DENIED|与 **HTTP 状态 401** 相同。 请求的资源需要用户身份验证。|
|**0x80cf4018**|OM_E_PT_HTTP_STATUS_FORBIDDEN|与 **HTTP 状态 403** 相同。 服务器理解此请求，但拒绝满足该请求。|
|**0x80cf4019**|OM_E_PT_HTTP_STATUS_NOT_FOUND|与 **HTTP 状态 404** 相同。 服务器找不到请求的 URI (统一资源标识符)。|
|**0x80cf401A**|OM_E_PT_HTTP_STATUS_BAD_METHOD|与 **HTTP 状态 405** 相同。 不允许使用 HTTP 方法。|
|**0x80cf401B**|OM_E_PT_HTTP_STATUS_PROXY_AUTH_REQ|与 **HTTP 状态 407** 相同。 需要进行代理身份验证。|
|**0x80cf401C**|OM_E_PT_HTTP_STATUS_REQUEST_TIMEOUT|与 **HTTP 状态 408** 相同。 服务器等待请求时超时。|
|**0x80cf401D**|OM_E_PT_HTTP_STATUS_CONFLICT|与 **HTTP 状态 409** 相同。 没有完成请求，因为与资源的当前状态有冲突。|
|**0x80cf401E**|OM_E_PT_HTTP_STATUS_GONE|与 **HTTP 状态 410** 相同。 请求的资源在服务器上不再可用。|
|**0x80cf401F**|OM_E_PT_HTTP_STATUS_SERVER_ERROR|与 **HTTP 状态 500** 相同。 服务器内部错误阻止满足请求。|
|**0x80cf4020**|OM_E_PT_HTTP_STATUS_NOT_SUPPORTED|与 **HTTP 状态 500** 相同。 服务器不支持满足请求所需的功能。|
|**0x80cf4021**|OM_E_PT_HTTP_STATUS_BAD_GATEWAY|与 **HTTP 状态 502** 相同。 服务器在当作网关或代理时收到无效的响应，此响应由服务器在尝试满足请求过程中访问的上游服务器发出。|
|**0x80cf4022**|OM_E_PT_HTTP_STATUS_SERVICE_UNAVAIL|与 **HTTP 状态 503** 相同。 服务临时过载。|
|**0x80cf4023**|OM_E_PT_HTTP_STATUS_GATEWAY_TIMEOUT|与 **HTTP 状态 503** 相同。 请求等待网关超时。|
|**0x80cf4024**|OM_E_PT_HTTP_STATUS_VERSION_NOT_SUP|与 **HTTP 状态 505** 相同。 服务器不支持用于请求的 HTTP 协议版本。|
|**0x80cf4025**|OM_E_PT_FILE_LOCATIONS_CHANGED|由于更改了文件位置，因此操作失败。 请刷新内部状态并重新发送。|
|**0x80cf4027**|OM_E_PT_NO_AUTH_PLUGINS_REQUESTED|服务器返回了空的身份验证信息列表。|
|**0x80cf4028**|OM_E_PT_NO_AUTH_COOKIES_CREATED|代理无法创建任何有效的身份验证 Cookie。|
|**0x80cf4029**|OM_E_PT_INVALID_CONFIG_PROP|配置属性值错误。|
|**0x80cf402A**|OM_E_PT_CONFIG_PROP_MISSING|缺少配置属性值。|
|**0x80cf402B**|OM_E_PT_HTTP_STATUS_NOT_MAPPED|无法完成 HTTP 请求，原因与任何 **OM_E_PT_HTTP_*** 错误代码都不对应。|
|**0x80cf402C**|OM_E_PT_WINHTTP_NAME_NOT_RESOLVED|与 **ERROR_WINHTTP_NAME_NOT_RESOLVED** 相同。 无法解析代理服务器或目标服务器的名称。|
|**0x80cf402F**|OM_E_PT_ECP_SUCCEEDED_WITH_ERRORS|外部 .cab 文件处理已完成，但出现了一些错误。|
|**0x80cf4030**|OM_E_PT_ECP_INIT_FAILED|未完成外部 .cab 处理器初始化。|
|**0x80cf4031**|OM_E_PT_ECP_INVALID_FILE_FORMAT|元数据文件的格式无效。|
|**0x80cf4032**|OM_E_PT_ECP_INVALID_METADATA|外部 Cab 处理器发现元数据无效。|
|**0x80cf4033**|OM_E_PT_ECP_FAILURE_TO_EXTRACT_DIGEST|无法从外部 .cab 文件中提取文件摘要。|
|**0x80cf4034**|OM_E_PT_ECP_FAILURE_TO_DECOMPRESS_CAB_FILE|无法解压缩外部 .cab 文件。|
|**0x80cf4035**|OM_E_PT_ECP_FILE_LOCATION_ERROR|外部 cab 处理器无法获得文件位置。|
|**0x80cf4FFF**|OM_E_PT_UNEXPECTED|发生了另一个 **OM_E_PT_*** 错误代码未涵盖的通信错误。|
|**0x80cf6001**|OM_E_DM_URLNOTAVAILABLE|无法完成下载管理器操作，因为请求的文件没有 URL。|
|**0x80cf6002**|OM_E_DM_INCORRECTFILEHASH|无法完成下载管理器操作，因为未识别文件摘要。|
|**0x80cf6003**|OM_E_DM_UNKNOWNALGORITHM|无法完成下载管理器操作，因为文件元数据请求了无法识别的哈希算法。|
|**0x80cf6005**|OM_E_DM_NONETWORK|无法完成下载管理器操作，因为网络连接不可用。|
|**0x80cf6007**|OM_E_DM_NOTDOWNLOADED|尚未下载更新。|
|**0x80cf6008**|OM_E_DM_FAILTOCONNECTTOBITS|下载管理器操作失败，因为下载管理器无法连接到后台智能传输服务 (BITS)。|
|**0x80cf6009**|OM_E_DM_BITSTRANSFERERROR|下载管理器操作失败，因为存在未指定的后台智能传输服务 (BITS) 传输错误。|
|**0x80cf600a**|OM_E_DM_DOWNLOADLOCATIONCHANGED|必须重启下载，因为下载的源的位置发生了更改。|
|**0x80cf600B**|OM_E_DM_CONTENTCHANGED|必须重启下载，因为更新内容在新版本中发生了更改。|
|**0x80cf6FFF**|OM_E_DM_UNEXPECTED|发生了另一个 **OM_E_DM_*** 错误代码未涵盖的下载管理器错误。|
|**0x80cf7003**|OM_E_INVALID_EVENT_PAYLOAD|指定了无效的事件负载。|
|**0x80cf7004**|OM_E_INVALID_EVENT_PAYLOADSIZE|提交的事件负载的大小无效。|
|**0x80cf7005**|OM_E_SERVICE_NOT_REGISTERED|服务未注册。|
|**0x80cf8000**|OM_E_DS_SHUTDOWN|操作失败，因为正在关闭代理。|
|**0x80cf8001**|OM_E_DS_INUSE|操作失败，因为正在使用数据存储。|
|**0x80cf8002**|OM_E_DS_INVALID|当前状态的数据存储和预期状态的数据存储不匹配。|
|**0x80cf8003**|OM_E_DS_TABLEMISSING|数据存储缺少表。|
|**0x80cf8004**|OM_E_DS_TABLEINCORRECT|数据存储包含一个具有意外列的表。|
|**0x80cf8005**|OM_E_DS_INVALIDTABLENAME|无法打开表，因为该表不在数据存储中。|
|**0x80cf8006**|OM_E_DS_BADVERSION|当前版本的数据存储和预期版本的数据存储不匹配。|
|**0x80cf8007**|OM_E_DS_NODATA|请求的信息不在数据存储中。|
|**0x80cf8008**|OM_E_DS_MISSINGDATA|数据存储缺少所需信息，或者在需要非 NULL 值的表列中具有 NULL。|
|**0x80cf8009**|OM_E_DS_MISSINGREF|数据存储缺少所需信息，或者引用了缺少的许可条款、文件、本地化属性或链接行。|
|**0x80cf800A**|OM_E_DS_UNKNOWNHANDLER|未处理更新，因为无法识别其更新处理程序。|
|**0x80cf800B**|OM_E_DS_CANTDELETE|未删除更新，因为一个或多个服务仍然引用该更新。|
|**0x80cf800C**|OM_E_DS_LOCKTIMEOUTEXPIRED|在分配的时间内无法锁定数据存储部分。|
|**0x80cf800E**|OM_E_DS_ROWEXISTS|未添加行，因为现有行具有相同的主键。|
|**0x80cf800F**|OM_E_DS_STOREFILELOCKED|无法初始化数据存储，因为它已被另一个进程锁定。|
|**0x80cf8010**|OM_E_DS_CANNOTREGISTER|不允许在当前进程中向 COM 注册数据存储。|
|**0x80cf8011**|OM_E_DS_UNABLETOSTART|操作无法在另一个进程中创建数据存储对象。|
|**0x80cf8013**|OM_E_DS_DUPLICATEUPDATEID|服务器将相同的更新发送给具有两个不同版本 ID 的客户端。|
|**0x80cf8014**|OM_E_DS_UNKNOWNSERVICE|无法完成操作，因为服务不在数据存储中。|
|**0x80cf8015**|OM_E_DS_SERVICEEXPIRED|无法完成操作，因为服务注册已过期。|
|**0x80cf8016**|OM_E_DS_DECLINENOTALLOWED|隐藏更新的请求被拒绝，因为此更新是强制性更新或者与截止时间一起部署。|
|**0x80cf8017**|OM_E_DS_TABLESESSIONMISMATCH|未关闭表，因为表与会话不关联。|
|**0x80cf8018**|OM_E_DS_SESSIONLOCKMISMATCH|未关闭表，因为表与会话不关联。|
|**0x80cf8019**|OM_E_DS_NEEDWINDOWSSERVICE|删除或注销此服务的请求被拒绝，因为此服务是内置服务，或者自动更新无法回滚到另一服务。|
|**0x80cf801A**|OM_E_DS_INVALIDOPERATION|已拒绝请求，因为不允许此操作。|
|**0x80cf801B**|OM_E_DS_SCHEMAMISMATCH|当前数据存储的架构和备份 XML 文档中的表架构不匹配。|
|**0x80cf801C**|OM_E_DS_RESETREQUIRED|数据存储要求重置会话。 请释放该会话并用新会话重新尝试。|
|**0x80cf801D**|OM_E_DS_IMPERSONATED|无法完成数据存储操作，因为此操作是通过模拟的标识请求的。|
|**0x80cf8FFF**|OM_E_DS_UNEXPECTED|发生了另一个 **OM_E_DS_*** 代码未涵盖的数据存储错误。|
|**0x80cfA000**|OM_E_AU_NOSERVICE|自动更新无法维护传入的请求。|
|**0x80cfA004**|OM_E_AU_PAUSED|自动更新无法处理传入的请求，因为自动更新已暂停。|
|**0x80cfA005**|OM_E_AU_NO_REGISTERED_SERVICE|未向自动更新注册非托管服务。|
|**0x80cfA006**|OM_E_AU_DETECT_SVCID_MISMATCH|向自动更新注册的默认服务在搜索过程中发生了更改。|
|**0x80cfA007**|OM_E_AU_ALREADY_PROMPTING_FOR_REBOOT|自动更新已提示用户重新启动。|
|**0x80cfAFFF**|OM_E_AU_UNEXPECTED|发生了另一个 **OM_E_AU \*** 代码未涵盖的自动更新错误。|
|**0x80cfE001**|OM_E_EE_UNKNOWN_EXPRESSION|表达式计算器运算无法完成，因为未识别表达式。|
|**0x80cfE002**|OM_E_EE_INVALID_EXPRESSION|表达式计算器运算无法完成，因为表达式无效。|
|**0x80cfE003**|OM_E_EE_MISSING_METADATA|表达式计算器运算无法完成，因为表达式包含的元数据节点的数目不正确。|
|**0x80cfE004**|OM_E_EE_INVALID_VERSION|表达式计算器运算无法完成，因为序列化表达式数据的版本无效。|
|**0x80cfE005**|OM_E_EE_NOT_INITIALIZED|无法初始化表达式计算器。|
|**0x80cfE006**|OM_E_EE_INVALID_ATTRIBUTEDATA|表达式计算器运算无法完成，因为属性无效。|
|**0x80cfE007**|OM_E_EE_CLUSTER_ERROR|表达式计算器运算无法完成，因为无法确定计算机的群集状态。|
|**0x80cfEFFF**|OM_E_EE_UNEXPECTED|发生了另一个 **OM_E_EE_*** 错误代码未涵盖的的表达式计算器错误。|
|**0x80cfF001**|OM_E_REPORTER_EVENTCACHECORRUPT|事件缓存文件有缺陷。|
|**0x80cfF002**|OM_E_REPORTER_EVENTNAMESPACEPARSEFAILED|无法分析事件命名空间描述符中的 XML。|
|**0x80cfF003**|OM_E_INVALID_EVENT|事件命名空间描述符中的 XML 无效。|
|**0x80cfF004**|OM_E_SERVER_BUSY|服务器拒绝了事件，因为服务器太忙。|
|**0x80cfFFFF**|OM_E_REPORTER_UNEXPECTED|发生了另一个错误代码未涵盖的报告错误。|
|**0x80af0005**|OMC_E_INSTALL_NOT_ALLOWED_REBOOT_REQUIRED|安装失败，因为存在待定的强制重新启动。|
|**0x80af0006**|OMC_E_DOWNLOAD_CANCELLED|已经取消了下载。|

## <a name="windows-7-based-computers-with-lots-of-superseded-updates-stop-reporting-to-the-microsoft-intune-console"></a>基于 Windows 7 且具有很多被取代更新的计算机停止向 Microsoft Intune 控制台进行报告
**问题**你可能会遇到 Microsoft Intune 客户端出现以下一种或多种表现的情况：
- 它们突然停止向 Microsoft 管理控制台进行报告。  
- 它们出现高 CPU 使用率。
- 当应用程序通过 Intune 门户安装时，安装速度缓慢。
- Microsoft Intune Center 将触发以下错误：*更新计算机时出错。发现错误：代码 0x800705b4*。
- “Intune 管理员控制台”>“组”>“所有设备”下的状态字段显示：*此计算机上安装的一个或多个代理存在错误。此计算机的信息可能不准确或不是最新的*。

如果被取代的更新（已由其他更新所取代的更新）已较长时间未遭到拒绝。 在某些进程期间（例如安装应用程序），Windows 将按顺序检查所有被取代的更新，以便可正确映射更新及其后续任务。 如果被取代的更新的列表增长过大，此检查任务可能导致 CPU 使用率过高，因为需要处理负载和时间。 此问题主要影响运行 Windows 7 的客户端，因为大量被取代的更新对 Windows 7 可用。 Windows 8 及更高版本的操作系统不具备如此多可用的被取代更新，因此不易发生此问题。

**解决方法：**若要解决此问题，请执行下列步骤：
1. 登录到 [Intune 管理控制台](https://manage.microsoft.com)。
2. 依次选择**更新**  > **所有更新**。
3. 使用上面的工具栏上的筛选器选项以筛选被取代的更新。
4. 若被取代的更新可应用到 Windows 7 或在受影响的客户端上安装的应用程序（如 Microsoft Office），则拒绝所有此类更新。
5. 重启受影响的客户端。

此外，如果你正在运行 Windows 7，请确保已安装以下更新：[3050265 Windows 更新客户端（用于 Windows 7）：2015 年 6 月](https://support.microsoft.com/kb/3050265)。

### <a name="next-steps"></a>后续步骤
如果此疑难解答信息没有帮助到你，请联系 Microsoft 支持部门，如[如何获取对 Microsoft Intune 的支持](how-to-get-support-for-microsoft-intune.md)中所述。
