---
title: "Intune 术语表"
titleSuffix: Intune on Azure
description: "了解 Microsoft Intune 中使用的一些术语"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/15/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bd7b5613-ee9f-4dc3-990c-ab4c1d40720d
ms.custom: intune-azure
ms.openlocfilehash: a9b43fc1a1877a3fc8bf4c5ee00e02dfee3cdea8
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2017
---
# <a name="microsoft-intune-glossary"></a>Microsoft Intune 术语表

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="a"></a>A

|||
|-|-|
|应用分配|可让用户[查找、下载和安装](/intune/app-management)所需的应用。 该操作之前称为“应用部署”。|
|应用配置的配置文件|在运行应用之前，请使用特定设置对 [iOS](/intune/app-configuration-policies-use-ios) 或 [Android](/intune/app-configuration-policies-use-android) 应用进行配置。|
|应用监视|可让你[查看与应用分配相关的最新状态和活动](/intune/apps-monitor)。|
|应用保护数据删除任务|可从用户的设备中[删除应用数据](/intune/app-protection-policies)。|
|应用保护策略|可确保用户应用符合[公司数据保护策略](/intune/app-protection-policies)。|
|App SDK|通过 [Microsoft Intune App SDK](/intune/app-sdk)，可让你为内部编写的应用添加功能性，使其能够通过 Intune 应用保护策略进行管理。|
|应用卸载操作|可让你从用户的设备[卸载应用](/intune/apps-deploy)。|
|应用包装工具|一个[命令行应用程序](/intune/apps-prepare-mobile-application-management)，可围绕业务线应用创建包装器，使其可通过 Intune 应用保护策略进行管理。|
|分配操作|在[分配应用](/intune/apps-deploy)时所做的选择。 你可以选择强制安装应用（必需）、可选（可用），也可以卸载应用。|
|可用安装|当使用此操作分配应用时，它会显示在公司门户中，用户可以[按需安装](/intune/apps-deploy)。|
|Azure 门户|Intune 的新控制台（[阅读更多](/intune/what-is-intune)）。|

## <a name="b"></a>B
|||
|-|-|
|BYOD|[自带设备办公](/intune/device-enrollment)。 用户可在其设备上安装 Intune 公司门户应用，然后进行注册，获取对公司资源（如电子邮件、公司应用、公司数据和支持）的访问权限。|

## <a name="c"></a>C
|||
|-|-|
|证书配置文件|使用 Wi-Fi、电子邮件或 VPN 配置文件时，可使用此策略类型，通过证书[安全访问公司资源](/intune/certificates-configure)。|
|COD|可用多种方式注册[公司拥有的设备](/intune/device-enrollment)，具体可取决于组织的需求和待管理设备的类型。|
|Company Portal|一种向用户提供[公司数据和应用程序访问](/intune/company-portal-customize)的应用或网站。|
|合规性策略|确保设备[符合特定规则](/intune/device-compliance)，例如使用 PIN 访问设备，以及加密存储在设备上的数据。|
|符合和不符合要求的应用程序|[设备限制配置文件](/intune/device-restrictions-configure)的一部分，这些设置可让你定义一个应用列表，规定用户可以或不可以运行的应用。 然后，Intune 通过报告通知你， 报告安装或运行了不合规应用。 对于一些平台，Intune 可阻止安装不合规应用。|
|条件性访问|仅允许符合设定规则的设备[访问公司电子邮件、Office 365 和其他服务](/intune/conditional-access)。|
|自定义策略|常规配置策略未包含符合要求的内置设置时，可[使用这些策略](/intune/custom-settings-configure)。 可通过自定义策略使用其他方式（如 Apple Configurator 或 OMA-URI）创建设置。|

## <a name="d"></a>D
|||
|-|-|
|部署|向管理的设备或用户发送应用或策略的操作。 此操作现在称为*分配*。|
|设备注册管理器|组织可以使用 Intune 来管理大量带有单一用户帐户的移动设备。 [设备注册管理员 (DEM) 帐户](/intune/device-enrollment-program-enroll-ios)是一个特殊的 Intune 帐户，可以注册多达 1,000 台设备。|
|设备配置文件|[这些配置文件](/intune/device-profile-create)可让你在所管理的设备上配置一系列安全性、功能和访问设置。|

## <a name="e"></a>E
|||
|-|-|
|电子邮件配置文件|此策略可用于为移动设备设置[电子邮件访问设置](/intune/email-settings-configure)，最大限度地减少最终用户必须执行的设置量。|
|EMS|Microsoft 企业移动性 + 安全性（以前称为企业移动性套件）在确保用户可[访问所需应用和内容](https://www.microsoft.com/cloud-platform/enterprise-mobility)的同时，可保护公司数据。|
|最终用户|使用 Intune 管理的[手机和电脑等设备的用户](/intune/end-user-educate)。|
|注册|Microsoft Intune 使用[注册](/intune/device-enrollment)将设备纳入管理并允许访问资源。|

## <a name="f"></a>F
|||
|-|-|
|FastTrack|适用于符合条件的计划中具有 150 个许可证的 Intune 用户的一项 [Microsoft 服务](https://technet.microsoft.com/library/mt228265.aspx)。 使用此服务，Microsoft 专家可与你一起启动并运行 Intune。|

## <a name="g"></a>G
|||
|-|-|
|组|使用组可[有序收集用户或设备](/intune/groups-get-started)。 例如，可将所有 Windows 电脑创建为一个组。 然后，你可以将应用和配置文件分配给这些组。|

## <a name="h"></a>H
|||
|-|-|
|混合|通过 System Center Configuration Manager 控制台可以管理使用 Intune 注册的设备的配置。|

## <a name="i"></a>I
|||
|-|-|
|Intune 门户|用于大多数 Intune 管理操作的 Azure 门户。|
|Intune 软件客户端|[管理一些 Windows 电脑](/intune-classic/get-started/choose-how-to-manage-devices)的备用方法，有助于决定要使用哪种方法。|
|Intune 软件发行者|使用此工具[定义想要部署的应用并将其上传至云存储空间](/intune-classic/deploy-use/add-apps)。|
|库存|用于查看[管理的设备的硬件和安装的软件](/intune/device-inventory)。|

## <a name="k"></a>K
|||
|-|-|
|展台模式|将此模式配置为[设备限制配置文件](/intune/device-restrictions-configure)的一部分，可允许你锁定设备。 例如，你可以将零售设备配置为仅允许某些应用来运行。|

## <a name="m"></a>M
|||
|-|-|
|Managed Browser|可通过使用 Intune 在组织中分配的 [Web 浏览应用程序](/intune/app-configuration-managed-browser)。 托管浏览器策略可配置允许列表或阻止列表，限制托管浏览器的用户可以访问的网站。|
|MDM 机构|[MDM 机构](/intune/mdm-authority-set)定义有权管理一组设备的管理服务。 适用于 MDM 机构的选项包括 Intune 本身以及带 Intune 的 Configuration Manager。|
|移动应用配置策略|[iOS](/intune/app-configuration-policies-use-ios) 或 [Android](/intune/app-configuration-policies-use-android) 策略，用于在运行应用时，提供设置以兼容应用（例如公司名称或服务器地址）。|
|移动应用预配策略|iOS 策略，用于帮助你确保为 iOS 应用分配的[预配配置文件](/intune/app-provisioning-profile-ios)不过期。|
|移动应用程序管理|[移动应用管理 (MAM)](/intune/app-lifecycle) 能够为用户发布、推送、配置、保护、监视和更新移动应用。
|移动设备管理|[移动设备管理 (MDM)](/intune/device-lifecycle) 能够将设备注册到 Intune 中，以便对这些设备进行预配、配置、监视和管理。



## <a name="o"></a>O
|||
|-|-|
|OMA-DM|开放性移动联盟设备管理。 这是行业标准设备管理协议，许多硬件制造商将其用于确保对移动设备和电脑功能的控制。|
|OMA-URI|开放性移动联盟统一资源标识符。 这些项目可标识符合 OMA-DM 标准的各个设备设置。 在没有符合需求的内置设置情况下，这些设置可用于 [Intune 自定义配置文件](/intune/custom-settings-configure)。|

## <a name="p"></a>P
|||
|-|-|
|密码重置|一项 Intune 功能，可强制让最终用户在受支持的设备上[重置密码](/intune/device-passcode-reset)。|

## <a name="r"></a>R
|||
|-|-|
|远程锁定|一项 Intune 功能，可让你[锁定受支持的设备](/intune/device-remote-lock)，即使设备不属于你。|
|必需安装|当使用此操作分配应用时，无需[用户干预](/intune/apps-deploy)即可完成安装。 在某些平台上，最终用户必须接受此安装。|


## <a name="s"></a>S
|||
|-|-|
|选择性擦除|[选择性擦除](/intune/device-company-data-remove)将只删除公司数据，包括设备中适用的移动应用管理 (MAM) 数据、设置和电子邮件配置文件。 选择性擦除会将用户的个人数据保留在设备上。|
|旁加载|无需从应用商店访问业务线应用即可进行安装的操作。|
|订阅|输入的协议允许你访问 Intune 租户。|

## <a name="t"></a>T
|||
|-|-|
|TeamViewer|一个第三方应用程序，可与 Intune 配合使用，为通过 Intune 进行管理的 Android 设备提供[远程协助功能](/intune/device-profile-android-teamviewer)。|
|租户|可使用订阅进行访问的 Intune 服务的单个实例。|
|条款和条件|一种分配给用户的策略类型，包含用户必须[阅读并同意](/intune/terms-and-conditions-create)的信息，之后，用户才能使用公司门户注册和访问工作。|

## <a name="v"></a>V
|||
|-|-|
|批量采购的应用和书籍|一些应用商店允许你为想要在公司使用的应用或书籍购买多个许可证。 Intune 可帮助你管理[通过此类计划购买的](/intune/vpp-apps)应用和书籍。 你可以导入来自应用商店的许可证信息，跟踪已使用的许可证数量，并防止安装的应用副本数超出你所拥有的数量。|
|VPN 配置文件|一种将 [VPN 设置](/intune/vpn-settings-configure)分配到所管理的设备的策略，可最大程度减少最终用户所需的设置。|

## <a name="w"></a>W
|||
|-|-|
|Wi-Fi 配置文件|一种将[无线网络设置](/intune/wi-fi-settings-configure)分配到设备的策略，可让用户连接到你的公司网络而无需了解或配置任何设置。
