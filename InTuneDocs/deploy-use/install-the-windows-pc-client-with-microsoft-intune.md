---

title: "安装电脑客户端软件 | Microsoft Docs"
description: "使用本指南可帮助你使 Windows PC 由 Microsoft Intune 客户端软件进行管理。"
keywords: 
author: nathbarn
ms.author: nathbarn
ms.date: 03/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 64c11e53-8d64-41b9-9550-4b4e395e8c52
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 8b2bd3ecba0b597bc742ea08872ffe8fc58155cf
ms.openlocfilehash: 19cfb242fbd1be613b38c8aa06c12b741bc6cd74
ms.lasthandoff: 04/24/2017


---

# <a name="install-the-intune-software-client-on-windows-pcs"></a>在 Windows 电脑上安装 Intune 软件客户端
通过安装 Intune 客户端软件来注册 Windows 电脑。 Intune 客户端软件可通过以下方法安装：

- IT 管理员可使用以下方法之一：手动安装、组策略或包括在磁盘映像中的安装

- 最终用户可手动安装客户端软件

Intune 客户端软件包含向 Intune 管理注册电脑所必需的最低软件配置。 注册电脑后，Intune 客户端软件才会下载电脑管理所需的完整客户端软件。

此系列下载可降低网络带宽的影响，并尽量减少最初在 Intune 中注册电脑时所需的时间。 它还可确保第二次下载完成后，客户端将具有最新的软件。

## <a name="download-the-intune-client-software"></a>下载 Intune 客户端软件

所有方法都要求 IT 管理员先下载软件才可将其后续部署给最终用户，但用户自行安装 Intune 客户端软件的方法除外。

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com/)中，单击“管理员”&gt;“客户端软件下载”。

  ![下载 Intune PC 客户端](../media/pc-sa-client-download.png)

2.  在“客户端软件下载”页上，单击“下载客户端软件”。 然后将包含该软件的 **Microsoft_Intune_Setup.zip** 包保存到网络上的安全位置。

Intune 客户端软件安装包内附有关你的帐户的唯一特定信息（可在内嵌证书中使用）。 如果未经授权的用户获得了此安装包的访问权限，则他们可以用该包的嵌入式证书所代表的帐户注册电脑，并可能获得访问公司资源的权限。

3.  将安装程序包的内容提取到网络上的安全位置。

    > [!IMPORTANT]
    > 请不要重命名或删除提取的 **ACCOUNTCERT** 文件，否则客户端软件安装将失败。

## <a name="deploy-the-client-software-manually"></a>手动部署客户端软件

在要安装客户端软件的计算机上，转到客户端软件安装文件所在的文件夹。 然后运行 **Microsoft_Intune_Setup.exe** 安装客户端软件。

> [!NOTE]
> 将鼠标悬停在客户端电脑上任务栏中的图标上时，将显示安装的状态。

## <a name="deploy-the-client-software-by-using-group-policy"></a>使用组策略部署客户端软件

1.  在包含文件 **Microsoft_Intune_Setup.exe** 和 **MicrosoftIntune.accountcert** 的文件夹中，运行以下命令提取适用于 32 位和 64 位计算机且基于 Windows Installer 的安装程序：

    ```
    Microsoft_Intune_Setup.exe/Extract <destination folder>
    ```

2.  将 **Microsoft_Intune_x86.msi** 文件、**Microsoft_Intune_x64.msi** 文件和 **MicrosoftIntune.accountcert** 文件复制到要安装客户端软件且所有计算机都可访问的一个网络位置。

    > [!IMPORTANT]
    > 请不要分隔或重命名文件，否则客户端软件安装将失败。

3.  使用组策略将软件部署到网络上的计算机。

    有关如何使用组策略自动部署软件的详细信息，请参阅[适用于新手的组策略](https://technet.microsoft.com/library/hh147307.aspx)。

## <a name="deploy-the-client-software-as-part-of-an-image"></a>将客户端软件部署为映像的一部分
通过使用以下示例过程作为指导，你可以将 Intune 客户端软件作为操作系统映像的一部分部署到计算机：

1.  将客户端安装文件 **Microsoft_Intune_Setup.exe** 和 **MicrosoftIntune.accountcert** 复制到引用计算机上的 **%Systemdrive%\Temp\Microsoft_Intune_Setup** 文件夹。

2.  通过向“SetupComplete.cmd”  脚本中添加以下命令来创建“WindowsIntuneEnrollPending”  注册表项：

    ```
    %windir%\system32\reg.exe add HKEY_LOCAL_MACHINE\Software\Microsoft\Onlinemanagement\Deployment /v
    WindowsIntuneEnrollPending /t REG_DWORD /d 1
    ```

3.  将以下命令添加到“setupcomplete.cmd”中，以使用 /PrepareEnroll 命令行参数运行注册程序包：

    ```
    %systemdrive%\temp\Microsoft_Intune_Setup\Microsoft_Intune_Setup.exe /PrepareEnroll
    ```
    > [!TIP]
    > **SetupComplete.cmd** 脚本使 Windows 安装程序能够在用户登录之前修改系统。 “/PrepareEnroll”命令行参数会将目标计算机准备就绪，以便其在 Windows 安装程序结束后在 Intune 中自动注册。

4.  将“SetupComplete.cmd”放在引用计算机的“%Windir%\Setup\Scripts”文件夹中。

5.  捕获引用计算机的映像，然后将此映像部署到目标计算机。

    完成 Windows 安装程序后重启目标计算机时，会创建“WindowsIntuneEnrollPending”  注册表项。 注册包会检查是否注册了计算机。 如果注册了计算机，则不需要采取其他操作。 如果未注册计算机，则注册程序包会创建“Microsoft Intune 自动注册任务”。

    当自动注册任务在下一个计划的时间运行时，它会检查是否存在“WindowsIntuneEnrollPending”注册表值，并尝试在 Intune 中注册目标 PC。 如果注册由于任何原因失败，则下次运行任务时会重新尝试注册。 重新尝试会持续一个月。

    注册成功后或一个月后（以先发生者为准），系统就会从目标计算机中删除 Intune 自动注册任务、**WindowsIntuneEnrollPending** 注册表值和帐户证书。

## <a name="instruct-users-to-self-enroll"></a>指示用户自行注册

用户可通过访问[公司门户网站](https://portal.manage.microsoft.com)安装 Intune 客户端软件。 用户在 Web 门户中所见的确切信息有所不同，具体取决于帐户的 MDM 机构以及用户电脑的 OS 平台和/版本。

如果用户尚未分配 Intune 许可证，或尚未将组织的 MDM 机构设置为 Intune，则不会向用户显示任何注册选项。

如果用户已分配 Intune 许可证，且已将组织的 MDM 机构设置为 Intune：

- Windows 7 或 Windows 8 电脑用户将只看到一个选项：通过下载和安装组织唯一的电脑客户端软件注册 Intune。

- Windows 10 或 Windows 8.1 电脑用户将看到两个注册选项：

  -  **将电脑注册为移动设备**：用户选择“了解注册方法”按钮并获取如何将其电脑注册为移动设备的相关说明。 此按钮将突出显示，因为 MDM 注册被视为默认的首选注册选项。 但是，MDM 选项不适用于本主题，本主题只介绍客户端软件安装。
  - **使用 Intune 客户端软件注册电脑**：请让你的用户选择“单击此处下载”链接，然后将转到客户端软件安装。

下表概述了这些选项。

  ![每个平台的默认注册选项](../media/default-enrollment-options-table.png)

以下屏幕截图显示用户使用软件客户端注册设备时将看到的内容。

首先系统将提示用户标识或注册其设备。

  ![标识或注册设备](../media/identify-device-or-enroll.png)

若要让用户安装电脑客户端软件，请让他们选择“单击此处下载”链接，这将使用户能够下载电脑客户端软件并完成安装过程。 “了解注册方法”按钮可将用户转到一个文档（与这些软件客户端说明无关），该文档说明如何使用 MDM 注册进行注册。

  ![选择“单击此处下载”链接](../media/enroll-your-windows-device.png)

用户单击此链接时将看到“下载软件”按钮，选择此按钮可启动电脑客户端软件安装。

  ![选择“下载软件”按钮](../media/download-pc-client-software.png)

然后会提示用户使用公司凭据进行登录。

  ![使用凭据登录](../media/sign-in-to-intune.png)

用户将被转到安装的欢迎页面。

  ![电脑客户端安装的欢迎页面](../media/welcome-to-pc-agent-install-wizard.png)

用户选择“下一步”，然后开始安装。

  ![电脑客户端安装的欢迎页面](../media/welcome-to-pc-agent-install-wizard.png)

安装完成后，用户选择“完成”。

  ![完成电脑客户端安装](../media/completed-the-setup-wizard.png)

如果用户在使用 Intune 电脑客户端软件注册后，尝试将其电脑注册为移动设备，则会看到以下错误屏幕。

  ![如果电脑已注册，则会显示此屏幕](../media/page-shown-if-pc-already-enrolled.png)

## <a name="monitor-and-validate-successful-client-deployment"></a>监视和验证成功的客户端部署
使用下列过程之一来帮助你监视和验证成功的客户端部署。

### <a name="to-verify-the-installation-of-the-client-software-from-the-microsoft-intune-administrator-console"></a>通过 Microsoft Intune 管理员控制台验证客户端软件的安装

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com/)中，单击“组”&gt;“所有设备”&gt;“所有计算机”。

2.  在列表中，查找与 Intune 通信的被管理的计算机，或者在“搜索设备”框中键入计算机名或任何部分名称来搜索特定被管理的计算机。

3.  在控制台的底部窗格中检查计算机的状态。 解决任何错误。

### <a name="to-create-a-computer-inventory-report-to-display-all-enrolled-computers"></a>创建显示所有注册计算机的计算机清单报表

1.  在 [Microsoft Intune 管理控制台](https://manage.microsoft.com/)中，单击“报表”&gt;“计算机清单报表”。

2.  在“创建新报表”页上，将所有字段保留为默认值（除非想要应用筛选器），并单击“查看报表”。

3.  “计算机清单报告”页面会在新窗口中打开，窗口中会显示所有已在 Intune 中成功注册的计算机。

    > [!TIP]
    > 单击报表中的任何列标题以按该列的内容对列表进行排序。

## <a name="uninstall-the-windows-client-software"></a>卸载 Windows 客户端软件

有两种方法可以取消注册 Windows 客户端软件：

- 使用 Intune 管理控制台（推荐方法）
- 使用客户端上的命令提示符

### <a name="unenroll-by-using-the-intune-admin-console"></a>通过使用 Intune 管理控制台取消注册

若要通过使用 Intune 管理控制台取消注册软件客户端，请转到“组” > “所有计算机” > “设备”。 右键单击客户端，然后选择“停用/擦除”。

### <a name="unenroll-by-using-a-command-prompt-on-the-client"></a>通过使用客户端上的命令提示符取消注册

使用提升的命令提示符运行以下命令之一。

**方法 1**：

    ```
    "C:\Program Files\Microsoft\OnlineManagement\Common\ProvisioningUtil.exe" /UninstallAgents /MicrosoftIntune
    ```

**方法 2**<br>请注意：每个 Windows SKU 上都安装了这些代理：

    ```
    wmic product where name="Microsoft Endpoint Protection Management Components" call uninstall<br>
    wmic product where name="Microsoft Intune Notification Service" call uninstall<br>
    wmic product where name="System Center 2012 - Operations Manager Agent" call uninstall<br>
    wmic product where name="Microsoft Online Management Policy Agent" call uninstall<br>
    wmic product where name="Microsoft Policy Platform" call uninstall<br>
    wmic product where name="Microsoft Security Client" call uninstall<br>
    wmic product where name="Microsoft Online Management Client" call uninstall<br>
    wmic product where name="Microsoft Online Management Client Service" call uninstall<br>
    wmic product where name="Microsoft Easy Assist v2" call uninstall<br>
    wmic product where name="Microsoft Intune Monitoring Agent" call uninstall<br>
    wmic product where name="Windows Intune Endpoint Protection Agent" call uninstall<br>
    wmic product where name="Windows Firewall Configuration Provider" call uninstall<br>
    wmic product where name="Microsoft Intune Center" call uninstall<br>
    wmic product where name="Microsoft Online Management Update Manager" call uninstall<br>
    wmic product where name="Microsoft Online Management Agent Installer" call uninstall<br>
    wmic product where name="Microsoft Intune" call uninstall<br>
    wmic product where name="Windows Endpoint Protection Management Components" call uninstall<br>
    wmic product where name="Windows Intune Notification Service" call uninstall<br>
    wmic product where name="System Center 2012 - Operations Manager Agent" call uninstall<br>
    wmic product where name="Windows Online Management Policy Agent" call uninstall<br>
    wmic product where name="Windows Policy Platform" call uninstall<br>
    wmic product where name="Windows Security Client" call uninstall<br>
    wmic product where name="Windows Online Management Client" call uninstall<br>
    wmic product where name="Windows Online Management Client Service" call uninstall<br>
    wmic product where name="Windows Easy Assist v2" call uninstall<br>
    wmic product where name="Windows Intune Monitoring Agent" call uninstall<br>
    wmic product where name="Windows Intune Endpoint Protection Agent" call uninstall<br>
    wmic product where name="Windows Firewall Configuration Provider" call uninstall<br>
    wmic product where name="Windows Intune Center" call uninstall<br>
    wmic product where name="Windows Online Management Update Manager" call uninstall<br>
    wmic product where name="Windows Online Management Agent Installer" call uninstall<br>
    wmic product where name="Windows Intune" call uninstall
    ```

> [!TIP]
> 客户端取消注册将为受影响的客户端留下过时的服务器端记录。 取消注册过程是异步过程，需要卸载 9 个代理，因此最多需要 30 分钟完成。

### <a name="check-the-unenrollment-status"></a>检查取消注册状态

检查“%ProgramFiles%\Microsoft\OnlineManagement”并确保左侧仅显示以下目录：

- AgentInstaller
- 日志
- Updates
- 公用

### <a name="remove-the-onlinemanagement-folder"></a>删除 OnlineManagement 文件夹

取消注册过程不会删除 OnlineManagement 文件夹。 卸载后等待 30 分钟，然后运行此命令。 如果过早运行，则卸载可能停留在未知状态。 若要删除该文件夹，请启用提升的提示符并运行：

    ```
    "rd /s /q %ProgramFiles%\Microsoft\OnlineManagement".
    ```

### <a name="see-also"></a>另请参阅
[使用 Microsoft Intune 管理 Windows 电脑](manage-windows-pcs-with-microsoft-intune.md)
[客户端安装程序疑难解答](../troubleshoot/troubleshoot-client-setup-in-microsoft-intune.md)

