---
title: 步骤 6 安装 PAM 信任
description: 步骤 6 使用脚本配置 PAM。 本部分介绍在 corp 域和 priv 域间设置必要的信任
keywords: ''
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 08/18/2017
ms.topic: article
ms.prod: microsoft-identity-manager
ms.assetid: 4b524ae7-6610-40a0-8127-de5a08988a8a
ms.reviewer: ''
ms.suite: ems
ms.openlocfilehash: ad1482718693c9ae7004a71334013de68f7c20da
ms.sourcegitcommit: 44a2293ff17c50381a59053303311d7db8b25249
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50379373"
---
# <a name="step-6-set-up-the-pam-trust"></a>步骤 6 安装 PAM 信任

> [!div class="step-by-step"]
> [« 步骤 5](sp1-step5-configuring-pam.md)
> [步骤 7 »](sp1-step7-setup-sidhistory-sidfiltering.md)

**这对于仅 PRIV 环境而言不需要** 使用 MIMAdmin 帐户登录 PAMServer。

1. 使用 MIMAdmin 帐户登录 PAMServer
2. 以管理员身份运行 PowerShell
3. cd $env: SYSTEMDRIVE\PAM
4. .\PAMDeployment.ps1
5. 选择菜单选项 6（PAM 信任安装程序）

   出现提示时，请输入 CORP 管理员帐户的凭据。 提供凭据后，将建立信任关系并完成配置。

> [!div class="step-by-step"]
> [« 步骤 5](sp1-step5-configuring-pam.md)
> [步骤 7 »](sp1-step7-setup-sidhistory-sidfiltering.md)
