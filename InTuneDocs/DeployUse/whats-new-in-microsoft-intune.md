---
# required metadata

title: 新增功能 | Microsoft Intune
description:
keywords:
author: Lindavr
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune 新增功能

## 2016 年 4 月
所有这些功能也支持混合客户（与 Intune 集成的 Configuration Manager）。
### 应用管理
- **MAM 用户合规性。**
现在，你可以查看 Azure Active Directory (AAD) 租户中的任何用户的应用程序管理策略的[状态](monitor-mobile-app-management-policies-with-Microsoft-Intune.md)。 这包括：
   - 设备
   - 在设备上的应用

   状态值：

   **已签入**：指示该策略已部署到用户，以及应用已用在工作环境中且已成功接收到该策略。

    **未签入**：指示策略已部署到用户，但应用从那时起尚未在工作环境中使用。


- **防止 Outlook 联系人同步的 MAM 控件 (Android)。**
适用于[移动应用程序管理](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)而无需注册设备的新设置。 此设置可以防止应用程序将联系人同步到 Android 设备的本机通讯簿。 启用此设置后，目标应用程序将不能再将联系人保存到本机通讯簿。 禁用此设置后，目标应用程序将能够将联系人保存到本机通讯簿。 [远程擦除设备或应用](wipe-managed-company-app-data-with-Microsoft-Intune.md)后，将删除已保存到本机通讯簿的所有联系人。 最初，Android 设备上的 Outlook 应用程序支持此新设置。

### 设备管理
- **公司拥有的设备的电话号码标识。** 例如，当运行移动设备清单报表时，现在使用其完整的电话号码标识归类为“企业”的手机。 BYOD 电话号码将继续使用 **** 屏蔽，仅显示最后 4 位数字。


### 公司门户更新
Android 公司门户应用 未在 Intune 注册其设备和未安装正确证书的用户将不能登录到 Android 公司门户应用，并且会看到以下消息：“无法登录，因为设备缺少必需的证书。” 该消息包含“如何解决此问题”的链接，用户可以点击以查看关于安装证书的说明。

若要查看最终用户解决此问题的步骤，请参阅[设备缺少必需的证书](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_cert_missing) iOS 公司门户应用

已添加“下拉刷新”操作支持以刷新主页上的内容，其中包括列出的应用、设备以及 IT 联络信息。 “下列刷新”操作不会检查合规性或策略信息，这可以通过选择当前设备的磁贴，然后点击“同步”按钮来实现。 Windows 10 移动版和 Windows Phone 8.1 公司门户应用

当最终用户安装业务线应用时，现在它们将看到改进的应用安装体验。

* 如果应用安装要花很长时间，用户可以手动同步设备以强制继续同步过程。 若要查看最终用户说明，请参阅[手动同步设备以加速应用安装](https://technet.microsoft.com/library/mt427782.aspx#BKMK_win10m_wp81_sync_manually) 公司门户网站
* 当 Windows 10 移动版和 Windows Phone 8.1 用户正在安装业务线应用时，现在他们将看到以下新状态，向他们提供有关安装状态的详细信息：

**等待设备进行同步** – 用户已点击“安装”，并且设备现在尝试与 Intune 基础结构进行同步。 必须先同步，然后才能完成安装。

### “正在等待设备进行同步”消息也是一个链接，用户可以点击以查看[说明](https://technet.microsoft.com/library/mt590895.aspx#BKMK_iwp_sync_manually)，了解如果同步过程需要很长时间或已停止，如何手动将设备与 Intune 同步。

****正在下载** – 正在处理用户的下载请求，且设备正在下载并安装应用。** 添加这些状态之前，如果应用安装需要很长时间，用户将感到困惑，因为他们只能看到“正在安装”状态，而这可能会在屏幕上保持数个小时。 添加新的状态意味着，现在用户可以点击“正在等待设备进行同步”链接，并按照说明进行操作以强制继续同步过程，而不是呼叫支持部门。 即将推出  对设备注册管理器帐户的更改。 若要提高性能和可扩展性，Intune 将不再在公司门户应用的“我的设备”窗格中显示所有设备注册管理器 (DEM) 设备。  仅显示运行该应用的本地设备，且仅限该设备通过公司门户应用注册的情况下。

DEM 用户可能会在本地设备上执行操作，但只能从 Intune 管理员控制台远程管理其他已注册设备。


## 此外，Intune 将否决通过 Apple 设备注册计划或 Apple 配置器工具使用 DEM 帐户。
这两种注册方法已支持共享的 iOS 设备的无用户注册。



### 当共享设备的无用户注册不可用时，仅使用 DEM 帐户。
* [通过[云平台路线图](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)及时了解有关 Intune 即将推出的开发内容](http://go.microsoft.com/fwlink/?LinkID=273882)


<!--HONumber=May16_HO2-->


