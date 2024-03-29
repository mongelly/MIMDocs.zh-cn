---
title: 部署 PAM 步骤 6 - 移动组 | Microsoft Docs
description: 将组迁移到 PRIV 林，以便可以通过 Privileged Access Management 对它们进行管理。
keywords: ''
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 09/13/2017
ms.topic: article
ms.prod: microsoft-identity-manager
ms.assetid: 7b689eff-3a10-4f51-97b2-cb1b4827b63c
ms.reviewer: mwahl
ms.suite: ems
ms.openlocfilehash: 0473ea9e01a44aeb4acbebe01e6e6f989c8581d0
ms.sourcegitcommit: 44a2293ff17c50381a59053303311d7db8b25249
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50379305"
---
# <a name="step-6--transition-a-group-to-privileged-access-management"></a>步骤 6 – 将某个组转换为特权访问管理

> [!div class="step-by-step"]
> [« 步骤 5 ](step-5-establish-trust-between-priv-corp-forests.md)
> [步骤 7 »](step-7-elevate-user-access.md)

使用 PowerShell cmdlet 在 PRIV 林中创建了特权帐户。 这些 cmdlet 执行以下功能：

- 在 PRIV 林中创建与 CORP 林中的组具有相同安全标识符 (SID) 的组。  
- 在 MIM 服务数据库中创建与 PRIV 林中的组对应的对象。  
- 对于每个用户帐户，在 MIM 服务数据库中将创建两个对象，分别对应 CORP 林中的用户和 PRIV 林中的新用户帐户。  
- 在 MIM 服务数据库中创建 PAM 角色对象。  

需要为每个组以及组的每个成员运行一次 cmdlet。 迁移 cmdlet 不会更改或修改 CORP 林中的任何用户或组：此操作随后由 PAM 管理员手动执行。

1. 以 PRIV\MIMAdmin 身份直接登录或从 PRIV 工作站登录到 PAMSRV。

2.  启动 PowerShell，键入以下命令。

```PowerShell
   Import-Module MIMPAM
   Import-Module ActiveDirectory
```

3. 针对现有林中的用户帐户，在 PRIV 中创建相应的用于演示的用户帐户。

   在 PowerShell 中键入以下命令。  如果之前未在 contoso.local 中使用名称 Jen 创建用户，请根据情况更改命令的参数。 密码 'Pass@word1' 只是一个示例，应更改为唯一密码值。

   ```PowerShell
       $sj = New-PAMUser –SourceDomain CONTOSO.local –SourceAccountName Jen
       $jp = ConvertTo-SecureString "Pass@word1" –asplaintext –force
       Set-ADAccountPassword –identity priv.Jen –NewPassword $jp
       Set-ADUser –identity priv.Jen –Enabled 1
   ```

4. 出于演示目的，将一个组及其成员 Jen，从 CONTOSO 复制到 PRIV 域。

    运行以下命令，在系统提示你输入 CORP 域管理员 (CONTOSO\Administrator) 密码时请指定该密码：

   ```PowerShell
        $ca = get-credential –UserName CONTOSO\Administrator –Message "CORP forest domain admin credentials"
        $pg = New-PAMGroup –SourceGroupName "CorpAdmins" –SourceDomain CONTOSO.local                 –SourceDC CORPDC.contoso.local –Credentials $ca
        $pr = New-PAMRole –DisplayName "CorpAdmins" –Privileges $pg –Candidates $sj
   ```

    **New-PAMGroup** 命令采用以下参数（供参考）：

     -   NetBIOS 窗体中的 CORP 林域名  
     -   要从该域复制的组的名称  
     -   CORP 林域控制器的 NetBIOS 名称  
     -   CORP 林中的域管理员用户的凭据  

5. （可选）在 CORPDC 上，从 **CONTOSO CorpAdmins** 组中删除 Jen 的帐户（如果仍存在）。  这仅仅是出于演示的需要，用来说明如何将权限与 PRIV 林中创建的帐户相关联。

   1.  以 CONTOSO\Administrator 身份登录到 CORPDC。

   2.  启动 PowerShell，运行以下命令并确认更改。

       ```PowerShell
       Remove-ADGroupMember -identity "CorpAdmins" -Members "Jen"
       ```


如果你想要证明跨林的访问权限对用户的管理员帐户有效，则继续下一步。

> [!div class="step-by-step"]
> [« 步骤 5 ](step-5-establish-trust-between-priv-corp-forests.md)
> [步骤 7 »](step-7-elevate-user-access.md)
