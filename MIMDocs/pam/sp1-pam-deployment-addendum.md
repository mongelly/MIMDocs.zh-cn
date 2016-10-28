---
title: "附录"
description: "准备 CORP 域，其具有将由 Privileged Identity Manager 使用脚本进行管理的现有标识或新标识"
keywords: 
author: barclayn
manager: MBaldwin
ms.date: 09/27/2016
ms.topic: article
ms.prod: microsoft-identity-manager
ms.service: microsoft-identity-manager
ms.technology: active-directory-domain-services
ms.assetid: 4b524ae7-6610-40a0-8127-de5a08988a8a
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 689c2ef0e4e4a681a398ba7e94fb3def525937ea
ms.openlocfilehash: 482cfbbac3ea668ca4bf9d8a4a45469e61634f98


---
# 附录：

## 附录 1 设置 PRIV 域

压缩文件解压缩到 $env:SYSTEMDRIVE\PAM 文件夹中后，编辑 PAMDeploymentConfig.xml 以提供 PRIV 林的详细信息。 请更新 DNSName、NetbiosName、DC 名称、数据库/日志路径和 Sysvol 路径。 还更新域和 ForestMode。 如果要测试 Windows Server Technical Preview 5，请将 DomainMode 和 ForestMode设置为 WinThreshold。

1. 以管理员身份登录 PRIV 域
2. 以管理员身份运行 PowerShell
3. cd $env: SYSTEMDRIVE\PAM
4. import-module .\PAMDeployment.ps1
5. 选择菜单选项 9（Priv 林安装程序）


DC 将在完成后自动重新启动。 目录服务还原模式 (DSRM) 管理员密码必须符合以下条件：

  * 密码长度至少为 15 个字符
  * 密码中包含至少一个小写字符
  * 密码中包含至少一个大写字符
  * 密码中包含至少一个数字或特殊字符

## 附录 2 设置 CORP 域

如果从 PAM 着手，并且想要设置测试环境，该脚本还允许配置 CORP 域。 压缩文件解压缩到 $env:SYSTEMDRIVE\PAM 文件夹后，编辑 PAMDeploymentConfig.xml 以添加 CORP 林的详细信息。 更新 DNSName、NetbiosName、DC 名称、数据库/日志路径和 Sysvol 路径。 林功能级别必须至少为 Windows Server 2012 R2。

1. 以管理员身份登录 CPRP 域 DC
2. 以管理员身份运行 PowerShell
3. cd $env: SYSTEMDRIVE\PAM
4. import-module .\PAMDeployment.ps1
5. 选择菜单选项 10（CORP 林安装程序）

域控制器将在完成时自动重新启动

## 附录 3 设置 CORP 客户端以进行验证

配置文件中的 ClientBinaryLocation 必须指向 setup.exe 所在的位置。
以本地管理员身份登录客户端，并在提升的 PowerShell 窗口中运行以下命令：

1. cd $env: SYSTEMDRIVE\PAM
2. Import-module .\PAMDeployment.ps1
3. 选择菜单选项 7（MIM PAM 客户端安装程序）


如果计算机未加入域，它将提示输入 CORP 管理员凭据以执行域加入。 在加入域后，必须重新启动计算机。 再次以本地管理员身份登录客户端，并在提升的 PowerShell 窗口中运行以下命令：

1. cd $env: SYSTEMDRIVE\PAM
2. Import-module .\PAMDeployment.ps1
3. 选择菜单选项 7（MIM PAM 客户端安装程序）

继续执行上面提供的步骤 8。

## 如果出现问题，请参阅附录 4

所有脚本日志都保存在 %AppData%\MIMPAMInstall 中。 请将文件夹压缩到 Zip 文件，然后通过电子邮件发送到 [mim2016@microsoft.com](mim2016@microsoft.com)，写明操作和错误的详细信息。



<!--HONumber=Sep16_HO4-->

