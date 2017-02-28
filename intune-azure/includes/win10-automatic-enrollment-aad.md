## <a name="set-up-windows-10-and-windows-10-mobile-automatic-enrollment-with-azure-active-directory-premium"></a>使用 Azure Active Directory Premium 设置 Windows 10 和 Windows 10 移动版自动注册

自动注册可以让用户通过添加工作或学校帐户并同意进行管理的方式，在 Intune 中注册公司所有或个人 Windows 10 电脑和 Windows 10 移动版设备。 就这么简单。 在后台，该用户的设备进行注册并加入 Azure Active Directory。 注册后，使用 Intune 管理设备。

**必备条件**
- Azure Active Directory Premium 订阅（[试用订阅](http://go.microsoft.com/fwlink/?LinkID=816845)）
- Microsoft Intune 订阅


### <a name="configure-automatic-mdm-enrollment"></a>配置自动 MDM 注册

1. 在 [Azure 管理门户](https://portal.azure.com) (https://manage.windowsazure.com) 中，导航到“**Active Directory**”节点并选择你的目录。

2. 选择“应用程序”选项卡。 **Microsoft Intune** 将出现在应用程序列表中。

    ![使用 Microsoft Intune 的 Azure AD 应用](../media/aad-intune-app.png)

3. 选择“Microsoft Intune”的箭头。 可通过打开的网页配置 Microsoft Intune。

4. 选择“配置”开始使用 Microsoft Intune 配置自动 MDM 注册。

5. 对以下 URL 使用默认值：

  - **MDM 注册**
  - **MDM 使用条款** 
  - **MDM 符合性**

6.  指定应由 Microsoft Intune 管理的用户的设备。 这些用户的 Windows 10 设备将自动注册，以使用 Microsoft Intune 进行管理。

  - **所有**
  - **组**
  - **无**

7. 选择“保存”。
