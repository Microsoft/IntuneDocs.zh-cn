## <a name="enable-windows-10-automatic-enrollment"></a>启用 Windows 10 自动注册

通过自动注册，用户能够在将其工作帐户添加到个人所有的设备或将其企业所有的设备加入到 Azure Active Directory 时在 Intune 中注册其 Windows 10 设备。 在后台，该用户的设备进行注册并加入 Azure Active Directory。 注册后，使用 Intune 管理设备。

**必备条件**
- Azure Active Directory Premium 订阅（[试用订阅](http://go.microsoft.com/fwlink/?LinkID=816845)）
- Microsoft Intune 订阅


### <a name="configure-automatic-mdm-enrollment"></a>配置自动 MDM 注册

1. 登录到 [Azure 管理门户](https://portal.azure.com) (https://manage.windowsazure.com) ， 然后选择“Azure Active Directory”。

  ![Azure 门户的屏幕截图](../media/auto-enroll-azure-main.png)

2. 选择“移动性(MDM 和 MAM)”。

  ![Azure 门户的屏幕截图](../media/auto-enroll-mdm.png)

3. 选择“Microsoft Intune”。

  ![Azure 门户的屏幕截图](../media/auto-enroll-intune.png)

4. 配置“MDM 用户作用域”。 指定应由 Microsoft Intune 管理的用户的设备。 这些用户的 Windows 10 设备将自动注册，以使用 Microsoft Intune 进行管理。

  - **无**
  - **一些**
  - **所有**

   ![Azure 门户的屏幕截图](../media/auto-enroll-scope.png)

5. 对以下 URL 使用默认值：
    - **MDM 使用条款 URL**
    - **MDM 发现 URL**
    - **MDM 符合性 URL**

    > [!IMPORTANT]
    > 如果用户是一个组的成员，且该组会自动注册 MDM 并启用 MAM，并且用户试图在工作区加入其个人设备，则仅会启用 MAM。 

6. 选择“保存”。

默认情况下，不会为该服务启用双因素身份验证。 但是，在注册设备时，建议启用双重身份验证。 在为该服务请求双重身份验证之前，必须在 Azure Active Directory 中配置一个双重身份验证提供程序并为你的用户帐户配置多重身份验证。 请参阅[Azure 多重身份验证服务器入门](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud)。
