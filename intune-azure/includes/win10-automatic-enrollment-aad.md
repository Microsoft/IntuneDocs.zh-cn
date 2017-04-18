## <a name="enable-windows-10-automatic-enrollment"></a>启用 Windows 10 自动注册

自动注册可以让用户通过添加工作或学校帐户并同意进行管理的方式，在 Intune 中注册公司所有或个人 Windows 10 电脑和 Windows 10 移动版设备。 就这么简单。 在后台，该用户的设备进行注册并加入 Azure Active Directory。 注册后，使用 Intune 管理设备。

**必备条件**
- Azure Active Directory Premium 订阅（[试用订阅](http://go.microsoft.com/fwlink/?LinkID=816845)）
- Microsoft Intune 订阅


### <a name="configure-automatic-mdm-enrollment"></a>配置自动 MDM 注册

1. 登录到 [Azure 管理门户](https://portal.azure.com) (https://manage.windowsazure.com)，然后选择“Azure Active Directory”。

  ![Azure 门户的屏幕截图](../media/auto-enroll-azure-main.png)

2. 选择“移动性(MDM 和 MAM)”。

  ![Azure 门户的屏幕截图](../media/auto-enroll-mdm.png)

3. 选择“Microsoft Intune”。

  ![Azure 门户的屏幕截图](../media/auto-enroll-intune.png)

4. 配置哪些用户将自动注册。

  ![Azure 门户的屏幕截图](../media/auto-enroll-scope.png)

  对以下 URL 使用默认值：
  - **MDM 注册**
  - **MDM 使用条款**
  - **MDM 符合性**

5. 指定应由 Microsoft Intune 管理的用户的设备。 这些用户的 Windows 10 设备将自动注册，以使用 Microsoft Intune 进行管理。

  - **所有**
  - **组**
  - **无**

6. 选择“保存”。
