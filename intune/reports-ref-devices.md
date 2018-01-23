---
title: "设备 - Intune 数据仓库 | Microsoft Docs"
description: "Intune 数据仓库 API 中实体集合的“设备”类别的参考主题。"
keywords: "Intune 数据仓库"
author: Erikre
ms.author: erikre
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6955E12D-70D7-4802-AE3B-8B276F01FA4F
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: c708361708468c544533a27a446ef33a23d88d8a
ms.sourcegitcommit: d44c32aad3e84f6c0b296bdb010981d3a818befb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/16/2018
---
# <a name="reference-for-devices-entities"></a>设备实体引用

“设备”类别包含移动设备的实体，可用于跟踪此类信息：

  -  设备类型
  -  设备登记和注册状态
  -  设备所有权
  -  设备管理状态
  -  设备 Azure AD 成员身份状态
  -  注册状态
  -  设备的历史信息
  -  设备上的应用的清单

## <a name="devicetypes"></a>DeviceTypes

DeviceTypes 实体表示由其他数据仓库实体引用的设备类型。 设备类型通常描述设备型号、制造商或同时包含这两项内容。

| 属性  | 描述 |
|---------|------------|
| DeviceTypeID |设备类型的唯一标识符 |
| DeviceTypeKey |数据仓库中设备类型的唯一标识符 - 代理键 |
| DeviceTypeName |设备类型 |

## <a name="example"></a>示例

| deviceTypeID  | 名称 | 描述 |
|---------|------------|--------|
| 0 |“桌面” |Windows 桌面设备 |
| 1 |WindowsRT |WindowsRT 设备 |
| 2 |WinMO6 |Windows Mobile 6.0 设备 |
| 3 |Nokia |Nokia 设备 |
| 4 |WindowsPhone |Windows Phone 设备 |
| 5 |Mac |Mac 设备 |
| 6 |WinCE |Windows CE 设备 |
| 7 |WinEmbedded |Windows Embedded 设备 |
| 8 |iPhone |iPhone 设备 |
| 9 |iPad |iPad 设备 |
| 10 |iPod |iPod 设备 |
| 11 |Android |使用 Device Administrator 管理的 Android 设备 |
| 12 |ISocConsumer |iSoc 使用者设备 |
| 14 |MacMDM |使用内置 MDM 代理管理的 Mac OS X 设备 |
| 15 |HoloLens |Holo Lens 设备 |
| 16 |SurfaceHub |Surface Hub 设备 |
| 17 |AndroidForWork |使用 Android for Work 配置文件所有者管理的 Android 设备 |
| 100 |Blackberry |Blackberry 设备 |
| 101 |Palm |Palm 设备 |
| 255 |Unknown |未知设备类型 |

## <a name="clientregistrationstatetypes"></a>ClientRegistrationStateTypes

ClientRegistrationStateTypes 实体表示由其他数据仓库表引用的注册类型。

| 属性  | 描述 |
|---------|------------|
| clientRegisterationStateID |注册状态的唯一标识符 |
| clientRegisterationStateKey |数据仓库中注册状态的唯一标识符 - 代理键 |
| clientRegisterationStateName |注册状态 |

## <a name="example"></a>示例

| ClientRegisterationStateID  | 名称 | 描述 |
|---------|------------|--------|
| 0 |NotRegistered |未注册 |
| 1 |SMSIDConflict |SMS ID 冲突 |
| 2 |已注册 |已注册 |
| 3 |吊销 |此状态表示 IT 管理员已阻止客户端，可取消阻止该客户端。 擦除或停用设备后，设备也可能处于“吊销”状态。 |
| 4 |KeyConflict |键冲突 |
| 5 |ApprovalPending |批准挂起 |
| 6 |ResetCert |重置证书 |
| 7 |NotRegisteredPendingEnrollment |未注册的挂起登记 |
| 8 |Unknown |未知状态 |

## <a name="enrollmenttypes"></a>EnrollmentTypes

EnrollmentTypes 实体表明设备的注册方式。 注册类型会捕获注册方式。 示例列出了不同的注册类型及其含义。

| 属性  | 描述 |
|---------|------------|
| managementStateID |管理状态的唯一标识符。 |
| managementStateKey |数据仓库中管理状态的唯一标识符 - 代理键。 |
| managementStateName |表明应用于此设备的远程操作的状态。 |

## <a name="example"></a>示例

| enrollmentTypeID  | 名称 | 描述 |
|---------|------------|--------|
| 0 |Unknown |未收集注册类型 |
| 1 |UserEnrollment |用户发起的注册 |
| 2 |DeviceEnrollment |使用无用户的配置文件进行的设备注册 |
| 3 |DeviceEnrollmentWithUDA |含 UDA 配置文件的设备注册。 |
| 4 |AzureDomainJoined |用户通过 Azure Active Directory 发起的设备注册 |
| 5 |UserEnrollmentWithServiceAccount |用户通过服务帐户发起的注册 |
| 6 |DepDeviceEnrollment |使用无用户的配置文件进行的 DEP 设备注册 |
| 7 |DepDeviceEnrollmentWithUDA |含 UDA 配置文件的 DEP 设备注册 |
| 8 |AutoEnrollment |用于 BYOD 方案的 DRS 和 MDM 组合注册 |

## <a name="ownertypes"></a>OwnerTypes

OwnerTypes 实体表明拥有设备的是公司、个人还是未知对象。

| 属性  | 描述 | 示例 |
|---------|------------|--------|
| ownerTypeID |所有者类型的唯一标识符。 | |
| ownerTypeKey |数据仓库中所有者类型的唯一标识符 - 代理键。 | |
| ownerTypeName |表示设备的所有者类型：  <br>公司 - 设备为企业所有。 <br>个人 - 设备为个人所有 (BYOD)。  <br>未知 - 此设备上无此信息。 |公司 个人 未知 |

## <a name="mdmstatuses"></a>MdmStatuses

MdmStatuses 实体表明设备的符合性状态。

| 属性  | 描述 |
|---------|------------|
| MdmStatusID |符合性状态的唯一标识符 |
| MdmStatusKey |数据仓库中符合性状态的唯一标识符 - 代理键 | 
| ComplianceStatus |设备的符合性状态，应具有下表中的值之一 | 


## <a name="example"></a>示例

| MdmStatusID  | ComplianceStatus | 描述 |
|---------|------------|--------|
| 0 |Unknown |设备符合性状态未知。 |
| 1 |是否满足条件 |设备符合策略。 |
| 2 |不相容 |设备不符合策略。 |
| 3 |冲突 |设备符合性导致了冲突。 |
| 4 |错误 |读取设备的符合性状态时出错。 |


## <a name="managementstates"></a>ManagementStates

ManagementStates 实体提供有关设备状态的详细信息。 详细信息适用于应用远程操作、设备越狱或进行 root 的情况。

| 属性  | 描述 |
|---------|------------|
| managementStateID | 管理状态的唯一标识符。 |
| managementStateKey | 数据仓库中管理状态的唯一标识符 - 代理键。 |
| managementStateName | 表明应用于此设备的远程操作的状态。 |

## <a name="example"></a>示例

| managementStateID  | 名称 | 描述 |
|---------|------------|--------|
| 0 |托管 | 托管时不存在挂起的远程操作。 |
| 1 |RetirePending | 存在一个针对设备的挂起的停用命令。 |
| 2 |RetireFailed | 设备上的停用命令失败。 |
| 3 |WipePending | 存在一个针对设备的挂起的擦除命令。 |
| 4 |WipeFailed | 设备上的擦除命令失败。 |
| 5 |Unhealthy | 不正常状态。 |
| 6 |DeletePending | 存在一个针对设备的挂起的删除命令。 |
| 7 |RetireIssued | 已向设备发布停用命令。 |
| 8 |WipeIssued | 已发布擦除命令。 |
| 9 |WipeCanceled | 已取消擦除命令。 |
| 10 |RetireCanceled | 已取消停用命令。 |
| 11 |Discovered | 该设备是 Intune 新发现的设备，首次签入后，即会变为“托管”状态。 |

## <a name="workplacejoinstatetypes"></a>WorkPlaceJoinStateTypes

WorkPlaceJoinStateTypes 实体表示设备的 Azure Active Directory Workplace Join 的状态。  注册工作流可使用一个或多个证书进行验证或进行身份验证。 注册设备工作区时，这些证书用于验证设备和用户。 证书通过 SCEP（简单证书注册点）服务器颁发。 实体中的值表示设备经历此过程时可能出现的各种状态。 其中一些状态包括因所需证书颁发（来自 SCEP 服务器）失败导致的工作区加入失败。 如果设备永不经历此工作流，则该值设为“未知”。

| 属性  | 描述 |
|---------|------------|
| WorkPlaceJoinStateID | 工作区加入状态的唯一标识符 |
| WorkPlaceJoinStateKey | 数据仓库中工作区加入状态的唯一标识符 - 代理键 |
| WorkPlaceJoinStateName | 工作区加入状态 |

## <a name="example"></a>示例

| workPlaceJoinStateID  | 名称 | 描述 |
|---------|------------|--------|
| 0 |Unknown |如果某设备未加入工作区，则设备处于未知状态 |
| 1 |成功 |成功加入工作区 |
| 2 |FailureToGetScepMetadata |未能获取 SCEP 元数据 |
| 3 |FailureToGetScepChallenge |未能获取 SCEP 质询 |
| 4 |DeviceFailureToInstallScepCommand |未能在设备上安装 SCEP 命令 |
| 5 |DeviceFailureToGetCertificate |设备未能通过 SCEP 获取证书 |
| 6 |DeviceScepPending |挂起状态；设备仍在执行 SCEP |
| 7 |DeviceScepFailed |设备未能通过 SCEP 安装证书 |
| 8 |AADValidationFailed |未能验证设备存在于 AAD 上 |

## <a name="managementagenttypes"></a>ManagementAgentTypes

ManagementAgentTypes 实体表示用于管理设备的代理。

| 属性  | 描述 |
|---------|------------|
| ManagementAgentTypeID | 管理代理类型的唯一标识符。 |
| ManagementAgentTypeKey | 数据仓库中管理代理类型的唯一标识符 - 代理键。 |
| ManagementAgentTypeName |表明用于管理设备的代理类型。 |

## <a name="example"></a>示例

| ManagementAgentTypeID  | 名称 | 描述 |
|---------|------------|--------|
| 1 |EAS | 设备通过 Exchange Active Sync 管理 |
| 2 |MDM | 设备由 MDM 代理管理 |
| 3 |EasMdm | 设备由 Exchange Active Sync 和 MDM 代理共同管理 |
| 4 |IntuneClient | 设备由 Intune 电脑代理管理 |
| 5 |EasIntuneClient | 设备由 Exchange Active Sync 和 Intune 电脑代理共同管理 |
| 8 |ConfigManagerClient | 设备由 System Center Configuration Manager 代理管理 |
| 16 |Unknown | 未知的管理代理类型 |

## <a name="devices"></a>设备

设备实体列出受管理的所有已注册设备及相应属性。

| 属性  | 描述 |
|---------|------------|
| DeviceKey | 数据仓库中设备的唯一标识符 - 代理键。 |
| DeviceId | 设备的唯一标识符。 |
| DeviceName | 允许对设备命名的平台上设备的名称。 在其他平台上，Intune 从其他属性创建名称。 此属性不可同时用于所有设备。 |
| DeviceTypeKey | 此设备的设备类型属性的键。 |
| ClientRegisterationStateKey | 此设备的客户端注册状态属性的键。 |
| OwnerTypeKey | 此设备的所有者类型属性的键：企业、个人或未知。 |
| objectSourceKey | 忽略此列。 |
| CreatedDate | 设备注册日期。 |
| LastContact | 使用 Intune 签入的上一已知设备。 |
| LastContactNotification | Intune 上次通知设备使用 Intune 签入的时间。 |
| LastContactWorkplaceJoin | 时间戳，表明此设备的上一个已知工作区加入状态。 |
| ManagementAgentKey | 与此设备关联的管理代理键。 |
| ManagementStateKey | 与此设备关联的管理状态键，表明远程操作的最新状态或设备是否越狱／获取了 root 权限。 |
| ReferenceId | Azure Active Directory 中设备的 ID。 |
| WorkPlaceJoinStateKey | 与此设备关联的工作区加入状态的键。 |
| CategoryId | 忽略此列。 |
| EnrollmentTypeKey | 与此设备关联的注册类型的键，表明注册方法。 |
| CertExpirationDate | MDM 管理证书的到期日期。 |
| MdmStatusKey | MdmStatus 的键。 |
| OSFamily | OS 系列（Windows、iOS、Android 等。） |
| OSVersion | OS 版本 |
| OSMajorVersion | 操作系统版本（主要.次要.内部.修订）的主要版本组成部分。 |
| OSMinorVersion | 操作系统版本（主要.次要.内部.修订）的次要版本组成部分。 |
| OSBuildNumber | 操作系统版本（主要.次要.内部.修订）的内部版本组成部分。 |
| OSRevisionNumber | 操作系统版本（主要.次要.内部.修订）的修订版本组成部分。 |
| EasID | 此设备的 EAS ID（如果设备由 Exchange Active Sync 管理）。 |
| GraphDeviceIsManaged | Intune 在 Azure AD 中设置的上一管理状态。 |
| GraphDeviceIsCompliant | Intune 在 Azure AD 中设置的上一符合性状态。 |
| SerialNumber | 设备的序列号（如果可用）。 |
| EnrolledByUser | 注册此设备的用户的 ID，它引用用户表格中的用户 ID 列。 |
| RowLastModifiedDateTimeUTC | 上次修改此记录的时间。 |
| ProcessorArchitecture | 处理器体系结构。 |
| DeviceAction | 发布的上一设备操作，暂时忽略。 |
| 制造商 | 设备制造商。 |
| 型号 | 设备型号。 |
| LastPolicyUpdateUtc | 设备上策略最近一次更新的时间。 |
| LastExchangeStatusUtc | 设备上次与 Exchange 同步的时间。 |
| IsDeleted | 如果设备不再由 Intune 管理，则设置为 True。 保留上一已知状态。 |

## <a name="devicepropertyhistory"></a>DevicePropertyHistory

DevicePropertyHistory 实体具有的属性与设备表格和过去 90 天每个设备记录的每日快照的属性相同。 DateKey 列表明每行的日期。

| 属性  | 描述 |
|---------|------------|
| DateKey |引用日期表格，该表格表明当日日期。 |
| DeviceKey |数据仓库中设备的唯一标识符 - 代理键。 这是对包含 Intune 设备 ID 的设备表格的引用。 |
| DeviceName |允许对设备命名的平台上设备的名称。 在其他平台上，Intune 从其他属性创建名称。 此属性不可同时用于所有设备。 |
| DeviceTypeKey |此设备的设备类型属性的键。 |
| ClientRegisterationStateKey |此设备的客户端注册状态属性的键。 |
| OwnerTypeKey |此设备的所有者类型属性的键：企业、个人或未知。 |
| objectSourceKey |忽略此列。 |
| CreatedDate |设备注册日期。 |
| LastContact |使用 Intune 签入的上一已知设备。 |
| LastContactNotification |Intune 上次通知设备使用 Intune 签入的时间。 |
| LastContactWorkplaceJoin |时间戳，表明此设备的上一个已知工作区加入状态。 |
| ManagementAgentKey |与此设备关联的管理代理键。 |
| ManagementStateKey |与此设备关联的管理状态键，表明远程操作的最新状态或设备是否越狱／获取了 root 权限。 |
| ReferenceId |Azure Active Directory 中设备的 ID。 |
| WorkPlaceJoinStateKey |与此设备关联的工作区加入状态的键。 |
| CategoryId |忽略此列。 |
| EnrollmentTypeKey |与此设备关联的注册类型的键，表明注册方法。 |
| CertExpirationDate |MDM 管理证书的到期日期。 |
| MdmStatusKey |MdmStatus 的键。 |
| OSFamily |OS 系列（Windows、iOS、Android 等。） |
| OSVersion |操作系统版本。 |
| OSMajorVersion |操作系统版本（主要.次要.内部.修订）的主要版本组成部分。 |
| OSMinorVersion |操作系统版本（主要.次要.内部.修订）的次要版本组成部分。 |
| OSBuildNumber |操作系统版本（主要.次要.内部.修订）的内部版本组成部分。 |
| OSRevisionNumber |操作系统版本（主要.次要.内部.修订）的修订版本组成部分。 |
| EasID |此设备的 EAS ID（如果设备由 Exchange Active Sync 管理）。 |
| GraphDeviceIsManaged |Intune 在 Azure AD 中设置的上一管理状态。 |
| GraphDeviceIsCompliant |Intune 在 Azure AD 中设置的上一符合性状态。 |
| SerialNumber |设备的序列号（如果可用）。 |
| EnrolledByUser |注册此设备的用户的 ID，它引用用户表格中的用户 ID 列。 |
| RowLastModifiedDateTimeUTC |上次修改此记录的时间。 |
| ProcessorArchitecture |处理器体系结构。 |
| DeviceAction |发布的上一设备操作，暂时忽略。 |
| 制造商 |设备制造商。 |
| 型号 |设备型号。 |
| LastPolicyUpdateUtc |设备上策略最近一次更新的时间。 |
| LastExchangeStatusUtc |设备上次与 Exchange 同步的时间。 |

## <a name="mdmdeviceinventoryhistories"></a>MdmDeviceInventoryHistories

MdmDeviceInventoryHistories 实体包含过去 90 天内 MDM 托管设备清单数据的每日快照。 DateKey 表明行的日期。 某些属性可能不适用于所有设备或仅为一部分设备进行了填充，请查看此页面了解详细信息。 有关详细信息，请参阅[通过 Microsoft Intune 中的清单了解设备](https://docs.microsoft.com/Intune-classic/deploy-use/understand-your-devices-with-inventory-in-microsoft-Intune)。

| 属性  | 描述 |
|---------|------------|
| DateKey | 引用日期表格，该表格表明当日日期。 |
| DeviceKey |数据仓库中设备的唯一标识符 - 代理键。 这是对包含 Intune 设备 ID 的设备表格的引用。 |
| DeviceModel |设备型号。 |
| 操作系统 |设备的操作系统。 |
| DeviceName |允许对设备命名的平台上设备的名称。 在其他平台上，Intune 从其他属性创建名称。 此属性不可同时用于所有设备。 |
| SoftwareVersion |在大多数情况下，这是 OS 版本（Apple 平台除外，其中这不同于 OS 版本）。 |
| Imei |IMEI 编号 |
| HardwareInventoryTimeUtc |首次为此设备报告清单的时间。 |
| InventoryModifiedTimeUtc |上一次存储清单的时间（拍摄此快照时）。 |
| InventoryReportingTimeUtc |上次为此设备收集清单的时间。 |
| ExchangeActiveSyncId |Exchange ActiveSync 设备 ID。 |
| ComputerSystemDescription |系统描述。 |
| ComputerSystemName |系统名称。 |
| ComputerSystemManufacturer |系统制造商。 |
| ComputerSystemModel |系统型号。 |
| UserName |用户名。 |
| OSType |操作系统类型。 |
| OSCaption |操作系统描述文字。 |
| OSName |操作系统名称。 |
| OSManufacturer |操作系统制造商。 |
| OSProductSuite |操作系统产品套件。 |
| OSProductType |操作系统产品类型。 |
| 区域设置 |操作系统区域设置。 |
| PhysicalMemoryCapacity |物理内存容量（以字节为单位）。 |
| PhysicalMemoryRemovable |物理可移动内存（以字节为单位）。 |
| SystemEnclosureChassisTypesInnerText |定义此设备的系统底盘类型。 数字指示以下值：  <br>0 或空 = 未知   <br>1 = 这是台式电脑   <br>2 = 这是笔记本电脑  <br>3 = 这是工作站  <br>4 = 这是企业服务器  <br>100 = 这是手机  <br>101 = 这是平板电脑  <br>102/103 = 其他未知类型的移动设备 |
| SystemEnclosureModel |系统封装型号。 |
| SystemEnclosureSerialNumber |系统封装序列号。 |
| NetworkAdapterConfigurationText |网络适配器中的配置文本。 |
| MacAddress |MAC 地址。 |
| SmsID |Intune 设备 ID。 |
| CertExpiry |MDM 管理证书的到期日期。 |
| DeviceClientAgentVersion |客户端代理版本。 |
| DeviceClientID |设备客户端 ID。 |
| SerialNumber |序列号。 |
| DeviceManufacturer |设备制造商。 |
| DMVersion |DM 版本。 |
| FirmwareVersion |固件版本。 |
| HardwareVersion |硬件版本。 |
| PlatformType |平台类型。 |
| ProcessorLevel |处理器级别。 |
| ProcessorRevision |处理器修订版。 |
| 产品 |产品。 |
| ProductVersion |产品版本。 |
| OEM |原始设备制造商。 |
| DeviceBuildVersion |设备内部版本。 |
| Meid |移动设备标识符。 |
| PhoneNumber |电话号码。 |
| SubscriberCarrierNetwork |手机运营商网络名称。 |
| CellularTechnology |手机运营商网络类型 (CDMA/GSM)。 |
| Imsi |IMSI 号码。 |
| JailBroken |若设备已越狱或取得 root 权限，则为 True。 |
| IsActivationLockEnabled |若已启用激活锁定，则为 True |
| DeviceType |设备类型 |
| IsSupervised |受到监督 |
| DeviceDisplayNumberOfColors |设备显示的颜色数 |
| HorizontalResolution |设备水平屏幕分辨率 |
| VerticalResolution |设备垂直屏幕分辨率 |
| StorageFree |可用存储（以字节为单位） |
| StorageTotal |总存储（以字节为单位） |
| ProgramFree |可用程序内存（以字节为单位） |
| ProgramTotal |总程序内存（以字节为单位） |
| RemovableStorageFree |可用可移动存储（以字节为单位） |
| RemovableStorageTotal |总可移动存储（以字节为单位） |
| DeviceMemoryDeviceCapacity |设备内存容量 |
| DeviceMemoryAvailableDeviceCapacity |设备内存可用容量 |
| DeviceOSVersion |操作系统版本 |
| DeviceOSPlatform |OS 平台 |
| DeviceOSLanguage |OS 语言 |
| PasswordMaxAttemptsBeforeWipe |设备擦除前允许的密码尝试次数上限 |
| PasswordMinComplexChars |密码中所需的最小复杂字符数 |
| PasswordMinLength |允许的最小密码长度 |
| PasswordHistory |密码 - 不被接受的最小历史密码数 |
| PasswordEnabled |密码 - 已启用？ |
| PasswordExpiration |密码 - 到期日期。 |
| AllowRecoveryPassword |允许密码恢复。 |
| PasswordAutoLockTimeout |密码 - 自动锁定超时。 |
| PasswordType |密码类型。 |
| BacklightACTimeout |插入电源时的背光超时。 |
| BacklightBatTimeout |使用电池时的背光超时。 |
| PowerBackupPercent |电源备份百分比。 |
| BatteryPercent |剩余电池百分比。 |
| PlatformID |平台 ID。 |
| ExchangeDeviceID |Exchange 设备 ID。 |
| SmsProcessorDescription |处理器描述。 |
| OwnerEmailAddress |所有者的电子邮件地址。 |
| DeviceOSName |操作系统名称。 |
| WifiMac |WIFI MAC 地址。 |
| EthernetMac |以太网 MAC 地址。 |
| RequireEncryption |表明设备是否加密。 |
| ActivationLockBypassCode |激活锁旁路代码。 |

## <a name="applicationinventory"></a>ApplicationInventory

ApplicationInventory 实体列出了收集清单时在设备上找到的应用。

| 属性  | 描述 |
|---------|------------|
| DeviceKey |对设备表格的引用。 |
| ApplicationKey |? （从 ExchangeDeviceService\DeviceApplication 复制而来）。 |
| ApplicationName |? （从 ExchangeDeviceService\DeviceApplication 复制而来）。 |
| ApplicationVersion |? （从 ExchangeDeviceService\DeviceApplication 复制而来）。 |
| BundleSize |? （从 ExchangeDeviceService\DeviceApplication 复制而来）。 |
