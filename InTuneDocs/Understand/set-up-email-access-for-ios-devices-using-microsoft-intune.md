---
# required metadata

title: 使用 Microsoft Intune 设置适用于 iOS 设备的电子邮件访问权限 | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 3853673d-290a-400f-8e45-d55e39d42acd

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 使用 Microsoft Intune 设置适用于 iOS 设备的电子邮件访问权限
当向 Intune 注册设备时，可以配置设备，以便其用户可以访问公司电子邮件。 为特定设备类型实现此功能的一个方法是创建并部署**电子邮件配置文件**。 电子邮件配置文件是一种 Intune 策略，它可以设置用户的设备并将其连接到公司的电子邮件服务。
使用电子邮件配置文件可以使已注册的设备自动访问电子邮件，而无需你手动设置设备。 电子邮件配置文件还可确保所有最终用户以相同的方法和相同的基本设置设置访问权限。

## 本演练的目标

- 为 iOS 设备创建并部署电子邮件配置文件
- 验证是否已成功应用电子邮件配置文件策略

## 开始本演练之前需要的内容

- 本地或托管在 Azure 上作为 Office/E3 订阅一部分的 Exchange Server。
- 公司 Exchange 服务器的主机名。 这是完全限定的域名 (FQDN)，例如，**contosodemo55.onmicrosoft.com**
- 要将电子邮件配置文件部署到的用户组。 如果你已完成[开始试用 Microsoft Intune 试用版并部署 iOS PIN 策略](start-a-microsoft-intune-trial-and-deploy-ios-pin-policy.md)演练，则可以使用为其创建的 **GroupDemo** 用户组。
- 要将配置文件部署到的已注册 iOS 设备。 同样，如果已完成[开始试用 Microsoft Intune 试用版并部署 iOS PIN 策略](start-a-microsoft-intune-trial-and-deploy-ios-pin-policy.md)演练，你会拥有一些已注册的 iOS 设备。

## 为 iOS 设备创建并部署电子邮件配置文件的步骤

在本演练中，我们将使用带有试用订阅的托管 Exchange 服务器。
1. 在 Intune 控制台中，单击“策略”，然后单击“添加策略”
![<add-policy>](./media/Email-Walkthrough/Email-Walkthrough-1.png)
2. 在“创建新策略”对话框中，展开“iOS”，选择“电子邮件配置文件”，然后单击“创建策略”
![<ios-email-profile-policy>](./media/Email-Walkthrough/Email-Walkthrough-2.png)
3. 在“创建策略”页面上，输入策略名称（如 **iOS 电子邮件配置文件 - 用户密码**）和说明。 你可能拥有针对不同设备类型和不同身份验证方法的多个电子邮件配置文件，因此可以使用名称来显示配置文件对应的内容。
4. 输入 Exchange 主机名。 由于我要使用托管在 Azure 上的 Exchange 服务器，因此对于主机名，我们只需输入：**outlook.office365.com**](./media/Email-Walkthrough/Email-Walkthrough-3.png)
5. <add-exchange-host-name> 输入将向设备用户显示的帐户名，以帮助他们识别电子邮件服务。
6. 例如，**Contoso Email**
7. 由于我们将使用用户名和密码对 Exchange 服务的用户进行身份验证，因此保留用户名和密码的设置不变。 调整同步设置以满足你的要求。  
8. 目前，只需使用默认设置，除非你想要更改特定设置。
9. 单击“保存策略” 将显示一个对话框，询问你是否想要立即部署该策略。
![单击“是”](./media/Email-Walkthrough/Email-Walkthrough-4.png)
10. <deploy-policy-now-dialog>
![在之后出现的窗口中，选择你想要将电子邮件配置文件部署到的用户组，单击“添加”，然后单击“确定”

## <finish-add-policy>

单击“确定”后，策略将在一到两分钟内向下传递到已注册的设备中。
1. 验证是否已成功应用配置文件的步骤
若要验证是否已成功应用配置文件，你将需要访问已将电子邮件配置文件部署到其中的一个设备。
![在 iOS 设备上，打开邮件应用。](./media/Email-Walkthrough/Email-Walkthrough-6.png)
2. 该应用将提示你输入用户的电子邮件用户名和密码。
 <verify-policy-add-password>
![输入用户的 Exchange 电子邮件帐户的用户名和密码，然后点击“确定”](./media/Email-Walkthrough/Email-Walkthrough-7.png)
3. 邮件应用将打开 Exchange 帐户，然后电子邮件开始同步到设备。
![<exchange-account-opens>
1. 为邮件应用签入帐户设置，以确保帐户名与在电子邮件配置中输入的帐户名相同（例如，**Contoso Mail**），并确认正确设置了同步设置。
2. <check-account-settings>
3. <check-email-account-name>
![如果显示未自动将电子邮件配置文件应用到设备，则可以使用设备上的公司门户应用手动应用策略。](./media/Email-Walkthrough/Email-Walkthrough-10.png)
4. 打开公司门户应用。
![点击“我的设备” 点击设备的名称。

## <tap-device-name
[点击“同步” > “检查”](get-started-with-a-30-day-trial-of-microsoft-intune.md)


<!--HONumber=May16_HO2-->


