---
title: 使用脚本配置 PAM
description: 本文是使用脚本配置 PAM 系列的一部分。 它介绍了如何修改 PAM 部署脚本将使用 XML 文件。
keywords: ''
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 07/20/2017
ms.topic: article
ms.prod: microsoft-identity-manager
ms.assetid: 4b524ae7-6610-40a0-8127-de5a08988a8a
ms.reviewer: ''
ms.suite: ems
ms.openlocfilehash: 28e8f5c28cd38ad820c6a1f12385dffbd0641ddd
ms.sourcegitcommit: 44a2293ff17c50381a59053303311d7db8b25249
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50379527"
---
# <a name="configure-pam-using-scripts"></a>使用脚本配置 PAM

如果选择在单独服务器上安装 SQL 和 SharePoint，则必须使用以下说明进行配置。 如果 SQL、SharePoint 和 PAM 组件安装在同一台计算机上，必须在此计算机上运行以下步骤。

以下步骤假设 PRIV 域已安装，有关配置 PRIV 域的说明，请查看文档末尾的附录。

步骤：

1. 下载 [PAM 部署脚本](https://www.microsoft.com/download/details.aspx?id=53941)
2. 将压缩文件“PAMDeploymentScripts.zip”解压缩到所有计算机上的 %SYSTEMDRIVE%\PAM 文件夹。
3. 在任一计算机上，打开 **PAMDeploymentConfig.xml** 文件，并使用下面的图表或 XML 文件内的指导更新详细信息。 如果 CORP 和 PRIV 林均已安装，则只需更新 **DNSName** 和 **NetbiosName**。
4. 在“角色”部分中，更新 SQL、SharePoint 和 MIM 角色的**服务帐户**、**计算机详细信息**，以及**二进制文件的安装位置**。
    1. MIM 二进制文件的位置必须指向包含“服务和门户”文件夹的目录。 客户端二进制文件的位置必须指向包含“外接程序和 Extensions.msi”的目录。

5. 如果是 PRIVOnly 环境，则 PRIVOnly 标记必须设置为 True。
    1. 对于 PRIVOnly 环境，更新 PRIV 域的 **DNSName** 和 **NetbiosName** 以匹配 CORP 域。 请确保将安装 SQL、SharePoint 和 MIM 的计算机后缀正确无误，因为默认模板文件假设采用 CORP 和 PRIV 配置。
    2. 有关 PRIVOnly 环境的更多详细信息，请单击此处。

6. 将同一 PAMDeploymentConfig.xml 复制到所有计算机、CORPDC、PRIVDC、PAM 服务器、SQL Server 和 SharePoint 服务器上的 %SYSTEMDRIVE%\PAM 文件夹。


## <a name="deployment-worksheet"></a>部署工作表

在继续操作之前，请更新 PAMDeploymentConfig.xml 并将更新的副本放置到所有计算机上。

### <a name="setup"></a>Setup

|机   | 运行人员   |命令   |
|---|---|---|
|  PRIVDC |PRIV 域管理员   | .\PAMDeployment.ps1 选择菜单选项 1（PRIV 林配置）   |
|   |   |  上述步骤生成 SIDs.txt。 在运行下一步之前，需要将此文件复制到 CORPDC 的 $envDrive:PAM。 |
| CORPDC  |CORP 域管理员   | .\PAMDeployment.ps1 选择菜单选项 2（PRIV 林配置）   |
| PAMServer（或 SQL Server）   |CORP 域管理员   |  .\PAMDeployment.ps1 选择菜单选项 2（CORP 林配置）  |
|  PAMServer |  本地管理员（加入域后的 MIM 管理员） |  .\PAMDeployment.ps1 选择菜单选项 4（SharePoint 安装程序）  |
| PAMServer  | 本地管理员（加入域后的 MIM 管理员）  | .\PAMDeployment.ps1 菜单选项 5（MIM PAM 安装程序）   |
|  PAMServer |MIMAdmin   | .\PAMDeployment.ps1 选择菜单选项 6（ PAM 信任安装程序）.\PAMDeployment.ps1 选择菜单选项 6（PAM 信任安装程序） |

### <a name="validation"></a>验证

|  机 | 运行人员   | 命令   |
|---|---|---|
| CORPClient  | CORP 用户（本地管理员）  |   .\PAMDeployment.ps1 选择菜单选项 7（MIM PAM 客户端安装程序）  |
| CORPDC  | CORP 域管理员   | Import-module .\PAMValidation.psm1；Create-PAMValidationCORPDCConfig   |
| PAMServer   | MIMAdmin  | Import-module .\PAMValidation.psm1；Move-PAMValidationUsersToPAM  |
| CORPClient  | CORP 用户（本地管理员）   |   Import-module .\PAMValidation.psm1；Enable-PAMUsersCORPClientRemote |
|  CORPClient | <PRIV>\PRIV.pamRequestor 用户，如果是 PRIVOnly：<CORP>\pamrequestor   | Import-module .\PAMValidation.psm1；Test-PAMValidationScenarioNoApprovalRequest  |


> [!div class="step-by-step"]
> [开始 »](sp1-step1-configuring-priv-domain.md)
