---
title: PAM 软件要求 | Microsoft Docs
description: 查找用于成功部署 Privileged Access Management 的硬件和软件要求
keywords: ''
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 09/06/2017
ms.topic: article
ms.prod: microsoft-identity-manager
ms.assetid: 82a9085c-9667-4b3b-8079-657eab1d1e58
ms.reviewer: mwahl
ms.suite: ems
ms.openlocfilehash: 4838e9e8a495866902a78e713bb3b226eaf9def1
ms.sourcegitcommit: 44a2293ff17c50381a59053303311d7db8b25249
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50379805"
---
# <a name="hardware-and-software-requirements"></a>硬件和软件要求

Privileged Access Management 没有超出基础软件平台所需的任何硬件要求。 只需确保你拥有足够的内存或磁盘空间，以及网络连接。

> [!IMPORTANT]
> 本文提供了基本部署的最低要求。 不用于演示性能、可伸缩性或高可用性。 不描述为大型企业或生产环境推荐的部署拓扑。

## <a name="installing-from-software-packages"></a>从软件包安装

下面的软件可从 TechNet 评估中心或 MSDN 下载：

- Microsoft Identity Manager 2016
  - 服务和门户：包含适用于 MIM 服务和 MIM 门户以及 PAM 方案的安装程序
  - 加载项和扩展：包含适用于请求程序 PowerShell cmdlet 的安装程序

下面的软件可从 GitHub 下载：

- [PAMSamplePortal](https://github.com/Azure/identity-management-samples)：包含适用于 REST API 的示例 Web 应用程序

## <a name="required-software"></a>所需软件

- Windows Server 2012 R2
- Windows 10 企业版
- SQL Server 2012 Service Pack 1 或 SOL Server 2014

## <a name="evaluation-software"></a>评估软件

如果没有用于 Windows、SQL Server 或 Windows Server 的许可证，则可以下载评估版。

### <a name="technet-evaluation-center"></a>TechNet 评估中心

- [Windows Server 2012 R2](https://www.microsoft.com/evalcenter/evaluate-windows-server-2012-r2)
- [Windows 10 企业版](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise)

### <a name="microsoft-download-center"></a>Microsoft 下载中心

- [SQL Server](https://www.microsoft.com/download/details.aspx?id=29066)  
- [SharePoint Foundation 2013 SP1 及其必备组件](https://www.microsoft.com/download/details.aspx?id=42039)

## <a name="hardware-requirements"></a>硬件要求

对于 PAM 的每个组件，请参阅软件产品的系统要求。

对于 CORPDC：

- [Windows Server 2012 R2](https://technet.microsoft.com/library/dn303418.aspx) 或更低版本

对于 CORPWKSTN：

- [Windows 10](https://technet.microsoft.com/windows/dn798752.aspx)

对于 PRIVDC：

- [Windows Server 2012 R2](https://technet.microsoft.com/library/dn303418.aspx)

对于 PAMSRV：

- [Windows Server 2012 R2](https://technet.microsoft.com/library/dn303418.aspx)
- [SQL Server 2012](https://msdn.microsoft.com/library/ms143506(sql.110).aspx) 或 [SQL Server 2014](https://msdn.microsoft.com/library/ms143506(v=sql.120).aspx)
