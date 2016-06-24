---
# required metadata

title: 根据管理员角色自定义控制台视图 | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e0783eaa-67dc-410e-9e80-4d3aa72f36d8

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 根据管理员角色自定义 Intune 控制台视图
你可以筛选 Microsoft Intune 管理控制台视图，以允许管理员仅查看根据其角色所需查看的项目。 例如，你可以只允许管理控制台操作员更新恶意软件定义或重置设备上的密码。 这可通过使用分配给特定用户的预设**指定内容**来实现。 当这些用户访问管理控制台时，他们只能看到特定于其指定内容的项。

## 如何创建自定义视图

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com)中，单击“管理” &gt; “服务管理员”

2.  从服务管理员列表中，选择要更改其指定内容的用户，然后选择“管理访问权限”

3.  在 **“管理访问权限”** 对话框中，选择要授予所选用户的访问级别。 可以选择：

    -   **完全访问**
    -   **只读访问**
    -   **支持人员 - 组节点**

    完全访问和只读访问无需加以说明。 <!--- **Helpdesk - Groups Node** allows users to choose from one of the following designations that provide custom levels of access to the [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] admin console:--->

    **支持人员 - 组节点**将管理员可以查看的内容和执行的操作限制为：

    -   查看用户和设备的列表。 管理员不能使用筛选器来修改视图。 但你可以使用组筛选来修改管理员可以看到的内容。 有关详细信息，请参阅[通过 Microsoft Intune 使用组来管理用户和设备](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)

    -   打印用户和设备的列表

    -   导出用户和设备的列表

    -   查看用户或设备的属性

    -   执行以下远程任务：

        -   运行完全恶意软件扫描

        -   运行快速恶意软件扫描

        -   重新启动计算机

        -   更新恶意软件定义

        -   刷新策略

        -   刷新清单

        -   远程锁定设备

        -   密码重置

当你配置的管理员下次打开 Intune 管理控制台时，他们将获得你指定的访问级别。


<!--HONumber=May16_HO2-->


