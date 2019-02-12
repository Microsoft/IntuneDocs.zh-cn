---
title: 将 iOS 日志发送给 Microsoft 开发人员 |Microsoft 文档
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 733a590e-836f-4941-bfd9-6ae53ba25e06
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9da053d0358d9b85426d75de51aeaea8beb866c1
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2019
ms.locfileid: "55843164"
---
# <a name="send-logs-to-the-company-portal-developers-for-ios-devices"></a>将日志发送给 iOS 设备的公司门户开发人员

有时，公司门户应用可能会意外关闭。 这是应用开发人员想要了解的有关问题，因为它可以帮助我们使其为你更好地工作，并阻止将来发生类似事件。 此信息保留在设备上一个名为_诊断日志_的专用文档中。

如果发生了这种情况，公司门户团队将需要一些信息来尝试诊断根本原因。 以下是需要你执行的操作：

1.  尝试使问题再次出现。 如果无法执行也没有关系，但如果能够完成，这可能会使下一步更加容易。
2.  依次转到“设置” > “隐私” > “分析” > “分析数据”。 这是已发生的应用活动的列表，涵盖从崩溃到常规使用模式的情况，并且不包含任何个人信息。 此列表以由近及远的时间顺序排序。 如果能够重现问题，这应是出现在此页应用活动列表上的第一项。 如果无法重现问题，请向下滚动，直到找到第一个以“公司门户”开头的项，然后点击打开。
3.  按住，然后上下拖动蓝色小圆点，直到选中报告中的所有文本。 点击弹出菜单中的“__复制__”。
4.  打开电子邮件应用，并将该内容粘贴到电子邮件的正文。 将该电子邮件发送到 <a href="mailto:IntuneCPiOSfeedback@microsoft.com?subject=My Company Portal App Closed Unexpectedly&body=Press and hold, then paste your copied Company Portal app logs here.">IntuneCPiOSfeedback@microsoft.com</a>。

仍需帮助？ 请与公司支持人员联系。 有关联系信息，请查看[公司门户网站](https://go.microsoft.com/fwlink/?linkid=2010980)。
