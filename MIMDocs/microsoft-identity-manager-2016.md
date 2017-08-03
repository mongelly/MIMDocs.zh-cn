---
title: Microsoft Identity Manager 2016 | Microsoft Docs
description: "MIM 包括 FIM 2010 的访问权限管理功能，有助于管理用户、凭据、策略及组织中的访问权限。"
keywords: 
author: barclayn
ms.author: barclayn
manager: mbaldwin
ms.date: 07/13/2017
ms.topic: article
ms.service: microsoft-identity-manager
ms.technology: security
ms.assetid: ccdd8a9f-02da-440a-81a8-354800dcd2a8
ms.reviewer: mwahl
ms.suite: ems
ms.openlocfilehash: ca5dafb78899e286aff6d2e767ad1509a6439e65
ms.sourcegitcommit: 0cb8269f07a5f419d2d1cd760d9cc78b8a1c8aa9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2017
---
# <a name="microsoft-identity-manager-2016"></a>Microsoft Identity Manager 2016
Microsoft Identity Manager (MIM) 2016 以 [FIM 2010 R2](https://technet.microsoft.com/library/jj133885.aspx) 的标识和访问管理功能为基础。 如同其前身，MIM 有助于管理组织中的用户、凭据、策略和访问。  此外，MIM 2016 增加了混合体验、特权访问管理功能，并支持新的平台。

此版 Microsoft Identity Manager 提供 	Privileged Identity Management 等新功能，并支持使用证书管理 REST API。 证书管理现已开始支持多林拓扑、适用于虚拟智能卡和证书生命周期管理的 Windows 应用、更新后的事件和疑难解答功能。 自助式方案现在包括帐户解锁和用于密码重置的 Azure MFA（多重身份验证）入口。

## <a name="hybrid-experience"></a>混合体验
Microsoft Identity Manager 2016 与 Azure AD 协同工作，以便用户能够控制整个环境。 Azure AD 中的混合报表在一个地方集中显示云数据和本地数据。 此外，自助服务密码重置门户支持 Azure 多重身份验证 (MFA)。

## <a name="privileged-identity-management"></a>特权标识管理
借助 Privileged Identity Management，可基于任务暂时性地访问敏感资源，从而对管理访问权限进行控制和管理。 这意味着你可仅授予用户所需的足够权限，从而降低网络攻击者获取完全管理访问权限的几率。 此外，特权标识管理还可从现有 Active Directory 林提取和隔离管理帐户。

MIM 支持用于管理 Active Directory 的本地 Privileged Identity Management 解决方案。 请从[使用 Privileged Access Management](./pam/privileged-identity-management-for-active-directory-domain-services.md) 开始。

## <a name="related-topics"></a>相关主题
Microsoft Identity Manager 与其前身 Forefront Identity Manager 仍然紧密相关。 如果仍然使用 FIM，或者想要引用其他文档，请参阅 [FIM 2010 R2 文档路线图](https://technet.microsoft.com/library/jj133885.aspx)。