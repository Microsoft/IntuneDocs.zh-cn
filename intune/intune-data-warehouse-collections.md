---
title: Intune 数据库仓库收集
titlesuffix: Microsoft Intune
description: Intune 数据仓库收集提供与数据仓库 API 相关的详细信息。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/19/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 29f09230-dc56-43db-b599-d961967bda49
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune
ms.openlocfilehash: 89be4d6940910df4166ec9a485b78e066f94b755
ms.sourcegitcommit: 6ff5df63a2fff291d7ac5fed9c51417fe808650d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2018
ms.locfileid: "52167563"
---
#  <a name="intune-data-warehouse-collections"></a>Intune 数据仓库收集

以下 Intune 数据仓库收集提供数据仓库 API 实体的 v1.0 集合的属性、说明和示例。 

## <a name="apprevisions"></a>appRevisions
appRevision 实体列出了应用的所有版本。

|          属性          |                                      描述                                      |                示例               |
|:--------------------------:|:-------------------------------------------------------------------------------------:|:------------------------------------:|
| AppKey                     | 应用的唯一标识符。                                                         | 123                                  |
| ApplicationId              | 应用的唯一标识符 - 类似于 AppKey，但该标识符是自然键。        | b66bc706-ffff-7437-0340-032819502773 |
| 修订                   | 上传二进制文件时管理员提到的版本。                   | 2                                    |
| 标题                      | 应用标题。                                                                     | Excel                                |
| 发布者                  | 应用发布者。                                                                 | Microsoft                            |
| UploadState                | 应用的上传状态。                                                              | 1                                    |
| AppTypeKey                 | 对下一部分中所述的 AppType 的引用。                            | 1                                    |
| VppProgramTypeKey          | 对下述 VppProgramType 的引用。                                        | 30876                                |
| CreationTime               | 创建此修订版本的时间。                                            | 2016/11/23 0:00                      |
| ModifiedTime               | 上次更改与此修订版本相关的任何内容的时间。                            | 2016/11/23 0:00                      |
| 大小                       | 二进制文件的大小（以字节为单位）。                                                          | 120,392,000                          |
| StartDateInclusiveUTC      | 在数据仓库中创建此应用修订版本时的 UTC 日期和时间。      | 2016/11/23 0:00                      |
| EndDateExclusiveUTC        | 此应用修订版本停用时的 UTC 日期和时间。                        | 2016/11/23 0:00                      |
| IsCurrent                  | 表明此应用修订版本目前是否在数据仓库中。         | True/False                           |
| RowLastModifiedDateTimeUTC | 上次在数据仓库中修改此应用版本时的 UTC 日期和时间。 | 2016/11/23 0:00                      |

## <a name="apptypes"></a>appTypes
appType 实体列出了应用的安装源。

|   属性  |        描述        |
|:-----------:|:-------------------------:|
| AppTypeID   | 类型 ID           |
| AppTypeKey  | 密钥的代理键 |
| AppTypeName | 应用类型                  |

### <a name="example"></a>示例

| AppTypeID |                名称               |                     描述                     |
|:---------:|:---------------------------------:|:---------------------------------------------------:|
| 0         | Android 应用商店应用               | Android 应用商店应用。                             |
| 1         | Android LOB 应用                 | Android 业务线应用。                  |
| 2         | 托管 Android 应用商店应用 (MAM) | 启用了管理的 Android 应用商店应用。 |
| 3         | iOS 应用商店应用                   | iOS 应用商店应用。                                 |
| 4         | iOS LOB 应用                     | iOS 业务线应用。                      |
| 5         | 托管 iOS 应用商店应用 (MAM)     | 启用了管理的 iOS 应用商店应用。       |
| 6         | O365 Pro Plus 套件             | 适用于 Windows 10 的 Office 365 Pro Plus 套件。     |
| 7         | Web 应用                         | Web 应用。                                        |
| 8         | Windows Phone 8.1 应用商店应用     | Windows Phone 8.1 应用商店应用。                    |
| 9         | Windows 应用商店应用               | Windows 应用商店应用。                              |
| 10        | Windows LOB 应用                | Windows AppX 业务线应用。              |
| 11        | Windows Mobile MSI              | MSI 业务线应用。                      |
| 12        | Windows Phone LOB 应用           | Windows Phone 业务线应用。             |

## <a name="compliancepolicystatusdeviceactivities"></a>compliancePolicyStatusDeviceActivities
下表总结了分配给设备的符合性策略的分配状态。 它列出每种符合性状态的设备的计数。

|    属性   |                                                                                      描述                                                                                     |  示例 |
|:-------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------:|
| DateKey       | 为符合性策略创建了摘要时的日期键。                                                                                                                   | 20161204 |
| Unknown       | 由于其他原因脱机或无法与 Intune 或 Azure AD 通信的设备数量。                                                                           | 5        |
| 不适用 | 对于管理员指定的设备符合性策略不适用的设备数。                                                                                     | 201      |
| 是否满足条件     | 已成功应用管理员指定的一个或多个设备符合性策略的设备数。                                                                        | 4083     |
| InGracePeriod | 不符合要求但处于管理员定义的宽限期内的设备数。                                                                                  | 57       |
| 不符合  | 为后列情况的设备数：未能应用由管理员指定的一个或多个设备符合性策略，或其用户未遵守管理员指定的策略。 | 43       |
|    错误      |    无法与 Intune 或 Azure AD 通信，以及返回了错误信息的设备数量。                                                                          |    3     |

## <a name="compliancepolicystatusdeviceperpolicyactivities"></a>compliancePolicyStatusDevicePerPolicyActivities
下表按策略以及策略类型总结了分配给设备的符合性策略的分配状态。 它针对每个已分配的符合性策略，列出每种符合性状态的设备的计数。

|      属性     |                                                                                      描述                                                                                     |  示例 |
|:-----------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------:|
| DateKey           | 为符合性策略创建了摘要时的日期键。                                                                                                                   | 20161219 |
| PolicyKey         | 创建了摘要的符合性策略的键。                                                                                                                   | 10178    |
| PolicyPlatformKey | 创建了相应摘要的符合性策略的键。                                                                                            | 5        |
| Unknown           | 由于其他原因脱机或无法与 Intune 或 Azure AD 通信的设备数量。                                                                           | 13       |
| 不适用     | 对于管理员指定的设备符合性策略不适用的设备数。                                                                                     | 3        |
| 是否满足条件         | 已成功应用管理员指定的一个或多个设备符合性策略的设备数。                                                                        | 45       |
| InGracePeriod     | 不符合要求但处于管理员定义的宽限期内的设备数。                                                                                  | 3        |
| 不符合      | 为后列情况的设备数：未能应用由管理员指定的一个或多个设备符合性策略，或其用户未遵守管理员指定的策略。 | 7        |
| 错误             | 无法与 Intune 或 Azure AD 通信，以及返回了错误信息的设备数量。                                                                             | 3        |
## <a name="compliancestates"></a>complianceStates

|      属性      |                       描述                      |
|:------------------:|:------------------------------------------------------:|
| complianceStatus   | 使用 mdmStatusKey 的设备符合性状态       |
| complianceStateKey | 匹配设备和符合性状态的符合性密钥 |
| complianceStateID  | 匹配此符合性状态的 ID                |

### <a name="example"></a>示例

|  complianceStatus  |                       描述                      |
|:------------------:|:------------------------------------------------------:|
|    Unknown         |    未知。                                                                        |
|    是否满足条件       |    是否满足条件。                                                                      |
|    不相容    |       设备不相容，被公司资源阻止。             |
|    冲突        |    与其他规则冲突。                                                      |
|    错误           |       错误。                                                                       |
|    ConfigManager   |    由配置管理器管理。                                                      |
|    InGracePeriod   |       设备不相容，但仍有权访问公司资源          |

## <a name="dates"></a>日期
日期实体表示跨多个数据仓库实体引用的日期。

|     属性    |                       描述                      |    示例    |
|:---------------:|:------------------------------------------------------:|:-------------:|
| DateKey         | 数据仓库中此日期的唯一标识符。 | 20160703      |
| FullDate        | 此日期以完整日期/时间格式表示。        | 2016/7/3 0:00 |
| DayOfWeek       | 星期几                                            | 1             |
| DayOfMonth      | 几月几日                                           | 3             |
| DayOfYear       | 当年的哪天                                            | 185           |
| WeekOfYear      | 当年的哪周                                           | 28            |
| MonthOfYear     | 当年的哪月                                      | 7             |
| CalendarQuarter | 日历季度                                       | 3             |
| CalendarYear    | 日历年                                          | 2016          |
| DateKey         | 数据仓库中此日期的唯一标识符。 | 20160703      |
| FullDate        | 此日期以完整日期/时间格式表示。        | 2016/7/3 0:00 |
| DayOfWeek       | 星期几                                            | 1             |
| DayOfMonth      | 几月几日                                           | 3             |
| DayOfYear       | 当年的哪天                                            | 185           |
| WeekOfYear      | 当年的哪周                                           | 28            |
| MonthOfYear     | 当年的哪月                                      | 7             |
| CalendarQuarter | 日历季度                                       | 3             |
| CalendarYear    | 日历年                                          | 2016          |

## <a name="devicecategories"></a>deviceCategories

|      属性      |                                    描述                                   |                示例               |
|:------------------:|:--------------------------------------------------------------------------------:|:------------------------------------:|
| deviceCategoryID   | 设备类别的唯一标识符。                                       | fb415ba2-7c08-41f6-a5e5-685b50da2c4c |
| deviceCategoryKey  | 数据仓库中设备类别的唯一标识符 - 代理键 | 1                                    |
| deviceCategoryName | 设备类别的显示名称。                                            | 智能手机                          |

## <a name="deviceconfigurationprofiledeviceactivities"></a>deviceConfigurationProfileDeviceActivities
DeviceConfigurationProfileDeviceActivity 实体列出每天处于成功、挂起、失败或错误状态的设备数。 该数字反映了分配给该实体的设备配置文件。 例如，如果对于分配给某设备的所有策略，该设备均为成功状态，则当天的成功计数增加一。 如果向设备分配了两个配置文件，一个处于成功状态，另一个处于错误状态，则实体会增加成功计数，同时让设备处于错误状态。 实体列出了过去 30 天中给定某天中处于各状态的设备数。

|  属性 |                                          描述                                          |  示例 |
|:---------:|:---------------------------------------------------------------------------------------------:|:--------:|
| DateKey   | 日期键，表明在数据仓库中记录设备配置文件签入的时间。 | 20160703 |
| Pending   | 处于挂起状态的唯一设备数。                                                    | 123      |
| 成功 | 处于成功状态的唯一设备数。                                                    | 12       |
| 错误     | 处于错误状态的唯一设备数。                                                      | 10       |
| Failed    | 处于失败状态的唯一设备数。                                                     | 2        |

## <a name="deviceconfigurationprofileuseractivities"></a>deviceConfigurationProfileUserActivities 
DeviceConfigurationProfileUserActivity 实体列出每天处于成功、挂起、失败或错误状态的用户数。 该数字反映了分配给该实体的设备配置文件。 例如，如果对于分配给某用户的所有策略，该用户均为成功状态，则当天的成功计数增加一。 如果向用户分配了两个配置文件，一个处于成功状态，另一个处于错误状态，则将用户计为错误状态。 DeviceConfigurationProfileUserActivity 实体列出了过去 30 天内给定某天中处于各状态的用户数。 

| 属性  | 描述  | 示例  |
|------------|----------------------------------------------------------------------------------------------|-----------|
| DateKey  | 日期键，表明在数据仓库中记录设备配置文件签入的时间。  | 20160703  |
| Pending  | 处于挂起状态的唯一用户数。  | 123  |
| 成功  | 处于成功状态的唯一用户数。  | 12  |
| 错误  | 处于错误状态的唯一用户数。  | 10  |
| Failed  | 处于失败状态的唯一用户数。  | 2  |

## <a name="devicepropertyhistories"></a>devicePropertyHistories

|          属性          |                                                                                      描述                                                                                     |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| DateKey                    | 引用日期表格，该表格表明当日日期。                                                                                                                                          |
| DeviceKey                  | 数据仓库中设备的唯一标识符 - 代理键。 这是对包含 Intune 设备 ID 的设备表格的引用。                               |
| DeviceName                 | 允许对设备命名的平台上设备的名称。 在其他平台上，Intune 从其他属性创建名称。 此属性不可同时用于所有设备。 |
| DeviceRegistrationStateKey | 此设备的设备注册状态属性的键。                                                                                                                    |
| OwnerTypeKey               | 此设备的所有者类型属性的键：企业、个人或未知。                                                                                                  |
| ManagementStateKey         | 与此设备关联的管理状态键，表明远程操作的最新状态或设备是否越狱/获取了 root 权限。                                                |
| AzureADRegistered          | 是否在 Azure Active Directory 中注册了该设备。                                                                                                                             |
| ComplianceStateKey         | ComplianceState 的键。                                                                                                                                                            |
| OSVersion                  | 操作系统版本。                                                                                                                                                                          |
| JailBroken                 | 设备是否越狱或取得 root 权限。                                                                                                                                         |
| DeviceCategoryKey          | 此设备的设备类别属性的键。                                                                                                                                    |
## <a name="deviceregistrationstates"></a>deviceRegistrationStates
DeviceRegistrationState 实体表示由其他数据仓库收集引用的注册类型。 

|           属性          |                                     描述                                     |
|:---------------------------:|:-----------------------------------------------------------------------------------:|
| deviceRegistrationStateID   | 注册状态的唯一标识符                                            |
| deviceRegistrationStateKey  | 数据仓库中注册状态的唯一标识符 - 代理键 |
| deviceRegistrationStateName | 注册状态                                                                  |
|    NotRegistered                     |    未注册                                                                                                                                                                  |
|    已注册                        |       已注册                                                                                                                                                                   |
|    吊销                           |       此状态表示 IT 管理员已阻止客户端，可取消阻止该客户端。 擦除或停用设备后，设备也可能处于“吊销”状态。        |
|    KeyConflict                       |    键冲突                                                                                                                                                                    |
|    ApprovalPending                   |    批准挂起                                                                                                                                                                |
|    CertificateReset                  |    重置证书                                                                                                                                                               |
|    NotRegisteredPendingEnrollment    |    未注册的挂起登记                                                                                                                                               |
|    Unknown                           |    未知状态                                                                                                                                                                   |

## <a name="devices"></a>设备
设备实体列出受管理的所有已注册设备及相应属性。

|          属性          |                                                                                       描述                                                                                      |
|:--------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| DeviceKey                  | 数据仓库中设备的唯一标识符 - 代理键。                                                                                                               |
| DeviceId                   | 设备的唯一标识符。                                                                                                                                                     |
| DeviceName                 | 允许对设备命名的平台上设备的名称。 在其他平台上，Intune 从其他属性创建名称。 此属性不可同时用于所有设备。 |
| DeviceTypeKey              | 此设备的设备类型属性的键。                                                                                                                                    |
| DeviceRegistrationState    | 此设备的客户端注册状态属性的键。                                                                                                                      |
| OwnerTypeKey               | 此设备的所有者类型属性的键：企业、个人或未知。                                                                                                    |
| EnrolledDateTime           | 设备注册的日期和时间。                                                                                                                                         |
| LastSyncDateTime           | 使用 Intune 签入的上一已知设备。                                                                                                                                              |
| ManagementAgentKey         | 与此设备关联的管理代理键。                                                                                                                             |
| ManagementStateKey         | 与此设备关联的管理状态键，表明远程操作的最新状态或设备是否越狱/获取了 root 权限。                                                |
| AzureADDeviceId            | 此设备 Azure deviceID。                                                                                                                                                  |
| AzureADRegistered          | 是否在 Azure Active Directory 中注册了该设备。                                                                                                                             |
| DeviceCategoryKey          | 与此设备关联的类别的键。                                                                                                                                     |
| DeviceEnrollmentType       | 与此设备关联的注册类型的键，表明注册方法。                                                                                             |
| ComplianceStateKey         | 与此设备关联的符合性状态的键。                                                                                                                             |
| OSVersion                  | 设备的操作系统版本。                                                                                                                                                |
| EasDeviceId                | 设备的 Exchange ActiveSync Id。                                                                                                                                                  |
| SerialNumber               | SerialNumber                                                                                                                                                                           |
| UserId                     | 与设备关联的用户的唯一标识符。                                                                                                                           |
| RowLastModifiedDateTimeUTC | 上次在数据仓库中修改此设备时的 UTC 日期和时间。                                                                                                       |
| 制造商               | 设备制造商                                                                                                                                                             |
| 型号                      | 设备型号                                                                                                                                                                    |
| OperatingSystem            | 设备的操作系统。 Windows、iOS 等。                                                                                                                                   |
| IsDeleted                  | 显示设备是否被删除的二进制文件。                                                                                                                                 |
| AndroidSecurityPatchLevel  | Android 安全修补程序级别                                                                                                                                                           |
| MEID                       | MEID                                                                                                                                                                                   |
| isSupervised               | 设备受监督的状态                                                                                                                                                               |
| FreeStorageSpaceInBytes    | 可用存储（以字节为单位）。                                                                                                                                                                 |
| TotalStorageSpaceInBytes   | 总存储（以字节为单位）。                                                                                                                                                                |
| EncryptionState            | 设备的加密状态。                                                                                                                                                      |
| SubscriberCarrier          | 设备的订阅者运营商                                                                                                                                                       |
| PhoneNumber                | 设备的电话号码                                                                                                                                                             |
| IMEI                       | IMEI                                                                                                                                                                                   |
| CellularTechnology         | 设备的移动电话技术                                                                                                                                                    |
| WiFiMacAddress             | Wi-Fi MAC                                                                                                                                                                              |


## <a name="devicetypes"></a>deviceTypes
deviceType 实体表示由其他数据仓库实体引用的设备类型。 设备类型通常描述设备型号、制造商或同时包含这两项内容。

|    属性    |                                  描述                                 |
|:--------------:|:----------------------------------------------------------------------------:|
| DeviceTypeID   | 设备类型的唯一标识符                                       |
| DeviceTypeKey  | 数据仓库中设备类型的唯一标识符 - 代理键 |
| DeviceTypeName | 设备类型                                                                |

### <a name="example"></a>示例

| deviceTypeID |        名称       |                      描述                      |
|:------------:|:-----------------:|:-----------------------------------------------------:|
| -1           | 不可用   | 设备类型不可用。                     |
| 0            | “桌面”           | Windows 桌面设备                              |
| 1            | Windows           | Windows 设备                                      |
| 2            | WinMO6            | Windows Mobile 6.0 设备                           |
| 3            | Nokia             | Nokia 设备                                        |
| 4            | WindowsPhone      | Windows Phone 设备                                |
| 5            | Mac               | Mac 设备                                          |
| 6            | WinCE             | Windows CE 设备                                   |
| 7            | WinEmbedded       | Windows Embedded 设备                             |
| 8            | iPhone            | iPhone 设备                                       |
| 9            | iPad              | iPad 设备                                         |
| 10           | iPod              | iPod 设备                                         |
| 11           | Android           | 使用 Device Administrator 管理的 Android 设备   |
| 12           | ISocConsumer      | iSoc 使用者设备                                |
| 13           | Unix              | Unix 设备                                         |
| 14           | MacMDM            | 使用内置 MDM 代理管理的 Mac OS X 设备 |
| 15           | HoloLens          | Holo Lens 设备                                    |
| 16           | SurfaceHub        | Surface Hub 设备                                  |
| 17           | AndroidForWork    | 使用 Android Profile Owner 管理的 Android 设备  |
| 18           | AndroidEnterprise | Android 企业设备。                          |
| 100          | Blackberry        | Blackberry 设备                                   |
| 101          | Palm              | Palm 设备                                         |
| 255          | Unknown           | 未知设备类型                                 |

## <a name="deviceenrollmenttypes"></a>deviceEnrollmentTypes
deviceEnrollmentType 实体表明设备的注册方式。 注册类型会捕获注册方式。 示例列出了不同的注册类型及其含义。

|         属性         |                                    描述                                    |
|:------------------------:|:---------------------------------------------------------------------------------:|
| deviceEnrollmentTypeID   | 注册类型的唯一标识符。                                       |
| deviceEnrollmentTypeKey  | 数据仓库中注册类型的唯一标识符 - 代理键。 |
| deviceEnrollmentTypeName | 注册类型名称。                                                           |

### <a name="example"></a>示例

| enrollmentTypeID |                名称                |                                        描述                                       |
|:----------------:|:----------------------------------:|:----------------------------------------------------------------------------------------:|
| 0                | Unknown                            | 未收集注册类型                                                      |
| 1                | UserEnrollment                     | 用户驱动的注册（通过 BYOD 通道）。                                           |
| 2                | DeviceEnrollmentManager            | 使用设备注册管理器帐户注册的用户。                              |
| 3                | AppleBulkWithUser                  | 使用用户质询的 Apple 批量注册。 （DEP、Apple 配置器）                   |
| 4                | AppleBulkWithoutUser               | Apple 批量注册，无需用户质询。   （DEP、Apple 配置器、移动配置） |
| 5                | WindowsAzureADJoin                 | Windows 10 Azure AD 联接。                                                                |
| 6                | WindowsBulkUserless                | 使用证书通过 ICD 进行 Windows 10 批量注册。                               |
| 7                | WindowsAutoEnrollment              | Windows 10 自动注册。   （添加工作帐户）                                    |
| 8                | WindowsBulkAzureDomainJoin         | Windows 10 批量 Azure AD 联接。                                                           |
| 9                | WindowsCoManagement                | AutoPilot 或组策略触发的 Windows 10 共同管理。                       |
| 10               | WindowsAzureADJoinsUsingDeviceAuth | 使用设备身份验证的 Windows 10 Azure AD 联接。                                            |


## <a name="intunemanagementextensions"></a>intuneManagementExtensions
intuneManagementExtension 列出每日在每台 Windows 10 设备上的 intuneManagementExtension 运行状况。 将保留过去 60 天内的数据。

|       属性      |                          描述                          | 示例 |
|:-------------------:|:-------------------------------------------------------------:|:-------:|
| DateKey             | 日期的唯一标识符。                                | 123     |
| TenantKey           | 租户的唯一标识符。                              | 456     |
| DeviceKey           | 设备的唯一标识符。                              | 789     |
| ExtensionVersionKey | IntuneManagementExtension 版本的唯一标识符。 | 1       |
| ExtensionStateKey   | 运行状况状态的唯一标识符。                            | 2       |

## <a name="intunemanagementextensionhealthstates"></a>intuneManagementExtensionHealthStates
IntuneManagementExtensionHealthState 列出 IntuneManagementExtension 的所有可能运行状况状态。

|      属性     |                   描述                  | 示例 |
|:-----------------:|:----------------------------------------------:|:-------:|
| ExtensionStateKey | 运行状况状态的唯一标识符。           | 2       |
| ExtensionState    | IntuneManagementExtension 的运行状况状态。 | Healthy |

## <a name="intunemanagementextensionversions"></a>intuneManagementExtensionVersions
IntuneManagementExtensionVersion 实体列出 IntuneManagementExtension 使用的所有版本。

|       属性      |                          描述                          | 示例 |
|:-------------------:|:-------------------------------------------------------------:|:-------:|
| ExtensionVersionKey | IntuneManagementExtension 版本的唯一标识符。 | 1       |
| ExtensionVersion    | 4 位版本号。                                   | 1.0.2.0 |

## <a name="managementagenttypes"></a>managementAgentTypes
managementAgentType 实体表示用于管理设备的代理。

|         属性        |                                       描述                                       |
|:-----------------------:|:---------------------------------------------------------------------------------------:|
| ManagementAgentTypeID   | 管理代理类型的唯一标识符。                                         |
| ManagementAgentTypeKey  | 数据仓库中管理代理类型的唯一标识符 - 代理键。 |
| ManagementAgentTypeName | 表明用于管理设备的代理类型。                              |

### <a name="example"></a>示例

| ManagementAgentTypeID |                名称               |                                  描述                                 |
|:---------------------:|:---------------------------------:|:----------------------------------------------------------------------------:|
| 1                     | EAS                               | 设备通过 Exchange Active Sync 管理                         |
| 2                     | MDM                               | 设备由 MDM 代理管理                                   |
| 3                     | EasMdm                            | 设备由 Exchange Active Sync 和 MDM 代理共同管理        |
| 4                     | IntuneClient                      | 设备由 Intune 电脑代理管理                               |
| 5                     | EasIntuneClient                   | 设备由 Exchange Active Sync 和 Intune 电脑代理共同管理 |
| 8                     | ConfigManagerClient               | 设备由 System Center Configuration Manager 代理管理     |
| 10                    | ConfigurationManagerClientMdm     | 设备由 Configuration Manager 和 MDM 管理。                    |
| 11                    | ConfigurationManagerCLientMdmEas  | 设备由 Configuration Manager、MDM 和 Eas 管理。               |
| 16                    | Unknown                           | 未知的管理代理类型                                              |
| 32                    | Jamf                              | 设备属性从 Jamf 提取。                               |
| 64                    | GoogleCloudDevicePolicyController |  设备由 Google 的 CloudDPC 管理。                                 |

## <a name="managementstates"></a>managementStates
ManagementState 实体提供有关设备状态的详细信息。 详细信息适用于应用远程操作、设备越狱或进行 root 的情况。

|       属性      |                                     描述                                    |
|:-------------------:|:----------------------------------------------------------------------------------:|
| managementStateID   | 管理状态的唯一标识符。                                       |
| managementStateKey  | 数据仓库中管理状态的唯一标识符 - 代理键。 |
| managementStateName | 表明应用于此设备的远程操作的状态。                 |

### <a name="example"></a>示例

| managementStateID |      名称      |                                                   描述                                                   |
|:-----------------:|:--------------:|:---------------------------------------------------------------------------------------------------------------:|
| 0                 | 托管        | 托管时不存在挂起的远程操作。                                                                       |
| 1                 | RetirePending  | 存在一个针对设备的挂起的停用命令。                                                             |
| 2                 | RetireFailed   | 设备上的停用命令失败。                                                                      |
| 3                 | WipePending    | 存在一个针对设备的挂起的擦除命令。                                                               |
| 4                 | WipeFailed     | 设备上的擦除命令失败。                                                                        |
| 5                 | Unhealthy      | 不正常状态。                                                                                              |
| 6                 | DeletePending  | 存在一个针对设备的挂起的删除命令。                                                             |
| 7                 | RetireIssued   | 已向设备发布停用命令。                                                               |
| 8                 | WipeIssued     | 已发布擦除命令。                                                                               |
| 9                 | WipeCanceled   | 已取消擦除命令。                                                                               |
| 10                | RetireCanceled | 已取消停用命令。                                                                             |
| 11                | Discovered     | 该设备是 Intune 新发现的设备，首次签入后，即会变为“托管”状态。 |

## <a name="mobileappinstallstates"></a>mobileAppInstallStates
MobileAppInstallState 实体表示已分配到包含设备和/或用户的组的移动应用程序的安装状态。

|       属性      |                        描述                       |
|:-------------------:|:--------------------------------------------------------:|
| AppInstallStateKey  | 帐户的应用安装状态的唯一 ID。 |
| AppInstallState     | 应用安装状态的枚举值。                     |
| AppInstallStateName | 应用安装状态的名称。                           |

## <a name="mobileappinstallstatuscounts"></a>mobileAppInstallStatusCounts
表示通过 Microsoft Intune 使用移动应用程序管理的给定目标设备类型的移动应用安装状态。

|      属性      |                                                          描述                                                          |
|:------------------:|:-----------------------------------------------------------------------------------------------------------------------------:|
| DateKey            | 记录应用安装状态的当天日期的键。                                                                     |
| AppKey             | 用于标识 AppRevision 实例的移动应用键。                                                          |
| DeviceTypeKey      | 与移动应用程序关联的设备类型的键。                                                              |
| AppInstallStateKey | 用于标识 MobileAppInstallState 实例的应用安装状态键。                                         |
| 错误代码          | 应用安装程序、移动平台或与应用安装相关的服务返回的错误代码。 |
| 计数              | 总计数。                                                                                                                  |

## <a name="ownertypes"></a>ownerTypes
ownerType 实体表明拥有设备的是公司、个人还是未知对象。

|    属性   |                                                                                     描述                                                                                    |           示例          |
|:-------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------------------------:|
| ownerTypeID   | 所有者类型的唯一标识符。                                                                                                                                               |                            |
| ownerTypeKey  | 数据仓库中所有者类型的唯一标识符 - 代理键。                                                                                                       |                            |
| ownerTypeName | 表示设备的所有者类型：公司 - 设备为企业所有。  个人 - 设备为个人所有 (BYOD)。   未知 - 此设备上无此信息。 | 公司 个人 未知 |

## <a name="policies"></a>策略
“策略”实体列出了设备配置文件、应用配置文件和符合性策略。 可使用移动设备管理 (MDM) 将策略分配给企业中的一个组。

|          属性          |                                                                       描述                                                                      |                示例               |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------:|
| PolicyKey                  | 表示数据仓库中策略的唯一键。                                                                                              | 123                                  |
| PolicyId                   | 数据仓库中策略的唯一标识符。                                                                                                 | b66bc706-ffff-7437-0340-032819502773 |
| PolicyName                 | 策略名称。                                                                                                                                    | “Windows 10 基线”                |
| PolicyVersion              | 策略版本。 编辑或更改策略即会创建一个更新的策略版本。                                                             | 1, 2, 3                              |
| IsDeleted                  | 表明是否已更新策略记录。  True - 策略拥有新纪录，其中含有更新的字段。  False - 策略的最新记录。 | True/False                           |
| StartDateInclusiveUTC      | 在数据仓库中创建策略时的 UTC 日期和时间。                                                                              | 2016/11/23 0:00                      |
| DeletedDateUTC             | IsDeleted 更改为 True 时的 UTC 日期和时间。                                                                                                   | 2016/11/23 0:00                      |
| RowLastModifiedDateTimeUTC | 上次在数据仓库中修改策略时的 UTC 日期和时间。                                                                        | 2016/11/23 0:00                      |

## <a name="policydeviceactivities"></a>policyDeviceActivities
下表列出了每天处于成功、挂起、失败或错误状态的设备数。 此数字反映每个策略类型配置文件的数据。 例如，如果对于分配给某设备的所有策略，该设备均为成功状态，则当天的成功计数增加一。 如果向设备分配了两个配置文件，一个处于成功状态，另一个处于错误状态，则实体会增加成功计数，同时让设备处于错误状态。 policyDeviceActivity 实体列出了过去 30 天中给定某天中处于各状态的设备数。

|  属性 |                                           描述                                           |        示例        |
|:---------:|:-----------------------------------------------------------------------------------------------:|:---------------------:|
| DateKey   | 日期键，表明在数据仓库中记录设备配置文件签入的时间。 | 20160703              |
| Pending   | 处于挂起状态的唯一设备数。                                                    | 123                   |
| 成功 | 处于成功状态的唯一设备数。                                                    | 12                    |
| PolicyKey | 策略键，可将其与策略相联接以获取 policyName。                                  | Windows 10 基线 |
| 错误     | 处于错误状态的唯一设备数。                                                      | 10                    |
| Failed    | 处于失败状态的唯一设备数。                                                     | 2                     |

## <a name="policyplatformtypes"></a>policyPlatformTypes

|        属性        |                      描述                      |     示例    |
|:----------------------:|:-----------------------------------------------------:|:--------------:|
| PolicyPlatformTypeKey  | 策略平台类型的唯一键。        | 20170519       |
| PolicyPlatformTypeId   | 策略平台类型的唯一标识符。 | 1              |
| PolicyPlatformTypeName | 策略平台类型的名称。              | AndroidForWork |

## <a name="policytypeactivities"></a>policyTypeActivities
PolicyTypeActivity 列出了处于成功、挂起、失败或错误状态的总设备数。 它列出了每天与设备配置文件、应用配置文件或符合性策略相关的这些状态。

|    属性   |                                          描述                                          |           示例           |
|:-------------:|:---------------------------------------------------------------------------------------------:|:---------------------------:|
| DateKey       | 日期键，表明在数据仓库中记录设备配置文件签入的时间。 | 20160703                    |
| PolicyKey     | 策略键，可将其与策略相联接以获取 policyName。                                | Windows 10 基线         |
| PolicyTypeKey | 策略键类型，可将其与策略类型相联接以获取策略类型名称。             | Windows10 符合性策略 |
| Pending       | 处于挂起状态的唯一设备数。                                                    | 123                         |
| 成功     | 处于成功状态的唯一设备数。                                                    | 12                          |
| 错误         | 处于错误状态的唯一设备数。                                                      | 10                          |
| Failed        | 处于失败状态的唯一设备数。                                                     | 2                           |

## <a name="policytypes"></a>policyTypes
PolicyType 实体列出了设备配置文件、应用配置文件和符合性策略的类型。 可使用移动设备管理 (MDM) 将策略分配给企业中的一个组。

|    属性    |                       描述                      |            示例            |
|:--------------:|:------------------------------------------------------:|:-----------------------------:|
| PolicyTypeId   | 源系统中的策略的唯一标识符。  | 123                           |
| PolicyTypeKey  | 数据仓库中策略的唯一标识符。 | 1                             |
| PolicyTypeName | 策略类型名称。                               | Windows 10 符合性策略。 |

## <a name="policyuseractivities"></a>policyUserActivities
下表列出了每天处于成功、挂起、失败或错误状态的用户数。 此数字反映每个策略类型配置文件的数据。 例如，如果对于分配给某用户的所有策略，该用户均为成功状态，则当天的成功计数增加一。 如果向用户分配了两个配置文件，一个处于成功状态，另一个处于错误状态，则将用户计为错误状态。 PolicyUserActivity 实体列出了过去 30 天中给定某天中处于各状态的用户数。

|  属性 |                                          描述                                          |       示例       |
|:---------:|:---------------------------------------------------------------------------------------------:|:-------------------:|
| DateKey   | 日期键，表明在数据仓库中记录设备配置文件签入的时间。 | 20160703            |
| Pending   | 处于挂起状态的唯一设备数。                                                    | 123                 |
| 成功 | 处于成功状态的唯一设备数。                                                    | 12                  |
| PolicyKey | 策略键，可将其与策略相联接以获取 policyName。                                | Windows 10 基线 |
| 错误     | 处于错误状态的唯一设备数。                                                      | 10                  |

## <a name="termsandconditions"></a>termsAndConditions
termsAndConditions 实体表示给定条款和条件(T&C) 策略的元数据和内容。 当用户第一次尝试注册 Intune 并随后对管理员要求重新接受的位置进行编辑时，将向其显示 T&C 策略的内容。 它们使管理员能够就用户必须同意的规定进行通信，以使设备注册到 Intune。

|    属性        |    描述    |    示例        |
|----------------------------------|-----------------------------------------------------------------------------------------------|-----------------------------------------------------------|
|    termsAndConditionsKey    |    对应于“userTermsAndConditionsAcceptances”集合中的项的键    |    123    |
|    termsAndCondidionsId    |    此 termsAndConditions 项的 ID    |    276edcb7-7440-4339-b6c5-8b6fc556fee6    |
|    termsAndConditionsVersion    |    此条款和条件项的版本    |    1    |
|    name    |    此 termsAndConditions 项的名称。        |    Intune 使用条款     |
|    description    |    这些条款和条件的说明。     |         |
|    title    |    这些条款和条件的标题。     |    设备管理公司策略        |
|    summaryOfTerms    |    向用户提供的条款的摘要。     |    我同意条款和条件。    |
|    termsAndConditionsBodyText    |    这些条款和条件文本的正文。       |    “设备加密”：强制执行 6 位 PIN    |
|    isDeleted    |    该值是否被删除的 True 或 False 值。     |    False    |
|    startDateInclusiveUTC    |    这些条款和条件的开始日期。     |    2018/8/23 4:01:34 AM    |
|    endDateEclusiveUTC    |    这些条款和条件的结束日期。     |    9999/12/31 12:00:00 AM    |

## <a name="userdeviceassociations"></a>userDeviceAssociations
UserDeviceAssociation 实体包含组织中的用户设备关联。

|        名称        |                                             描述                                            |     示例     |
|:------------------:|:--------------------------------------------------------------------------------------------------:|:---------------:|
| UserKey            | 数据仓库中用户的唯一标识符。   （代理键）。                            | 123             |
| DeviceKey          | 数据仓库中设备的唯一标识符。                                             | 123             |
| CreatedDateTimeUTC | 创建用户设备关联时的日期和时间。 使用 UTC 格式。                     | 2016/11/23 0:00 |
| IsDeleted          | 指示用户已取消设备注册，并且该关联不再活跃。 | True/False      |
| EndedDateTimeUTC   | IsDeleted 更改为 True 时的 UTC 日期和时间。                                               | 2017/6/23 0:00  |

## <a name="users"></a>用户
用户实体列出了企业中分配有许可证的所有 Azure Active Directory (Azure AD) 用户。

用户实体集合包含用户数据。 这些记录包含数据收集期间的用户状态（即使用户已被删除）。 例如，在上个月期间，可能将某个用户添加到 Intune 然后又将其删除。 尽管在提交报告时该用户已不存在，但在上个月的数据中仍然会显示该用户及其状态。 可以创建一个报告，该报告将显示用户的历史记录在你的数据中存在的持续时间。

|          属性          |                                                                                                           描述                                                                                                          |                示例               |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------:|
| UserKey                    | 数据仓库中用户的唯一标识符 - 代理键。                                                                                                                                                         | 123                                  |
| UserId                     | 用户的唯一标识符 - 类似于 UserKey，但该标识符是自然键。                                                                                                                                                    | b66bc706-ffff-7437-0340-032819502773 |
| UserEmail                  | 用户的电子邮件地址。                                                                                                                                                                                                     | John@constoso.com                    |
| UPN                        | 用户的用户主体名称。                                                                                                                                                                                               | John@constoso.com                    |
| DisplayName                | 用户的显示名称。                                                                                                                                                                                                      | John                                 |
| IntuneLicensed             | 指定此用户是否获得 Intune 许可。                                                                                                                                                                              | True/False                           |
| IsDeleted                  | 指示是否所有用户的许可证都已过期，以及是否因此将用户从 Intune 中删除。 对于单个记录，此标志不会更改。 相反，将为新用户状态创建新记录。 | True/False                           |
| RowLastModifiedDateTimeUTC | 上次在数据仓库中修改记录时的 UTC 日期和时间                                                                                                                                                 | 2016/11/23 0:00                      |

## <a name="usertermsandconditionsacceptances"></a>userTermsAndConditionsAcceptances
userTermsAndConditionsAcceptance 实体表示给定用户给定的条款和条件 (T&C) 策略的接受状态。 用户必须接受最新版本的条款才能继续访问公司门户。

|    属性    |    描述    |    示例    |
|-------------------------------|--------------------------------------------------------------------------------|----------------------------|
|    dateKey    |    对应于“日期”集合中的日期值的键。     |    20180823    |
|    userKey    |    映射到“用户”集合中的用户的用户键。     |    20000    |
|    termsAndConditionsKey    |    对应于“termsAndConditions”集合中的项的键    |    1    |
|    acceptedDateTimeUTC    |    用户接受这些条款和条件的时间    |    2018/8/23 4:01:34 AM    |
|    lastModifiedDateTimeUTC    |    上次修改此项的时间。     |    2018/8/23 4:01:34 AM    |

## <a name="vppprogramtypes"></a>vppProgramTypes 
vppProgramType 实体列出了应用的可能 VPP 计划类型。

|      属性      |          描述         |
|:------------------:|:----------------------------:|
| VppProgramTypeID   | 类型 ID。           |
| VppProgramTypeKey  | 密钥的代理键。 |
| VppProgramTypeName | VPP 计划类型。          |

### <a name="example"></a>示例

|             VppProgramID             |         名称        | 描述                |
|:------------------------------------:|:-------------------:|----------------------------|
| 3DDA2474-470B-4503-9830-2665C21C1945 | Microsoft           | Microsoft 的 VPP 计划。 |
| 00000000-0000-0000-0000-000000000000 | 尚未提供 | 默认值，无 VPP。   |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B | Apple               | Apple 的 VPP 计划。     |

## <a name="next-steps"></a>后续步骤

有关 Intune 数据仓库的详细信息，请参阅[数据仓库数据模型](https://docs.microsoft.com/intune/reports-ref-data-model)。

