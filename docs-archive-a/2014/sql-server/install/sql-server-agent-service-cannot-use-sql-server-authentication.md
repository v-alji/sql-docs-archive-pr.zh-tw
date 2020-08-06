---
title: SQL Server Agent 服務無法使用 SQL Server 驗證 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- authentication [SQL Server Agent]
- SQL Server Authentication [SQL Server Agent]
ms.assetid: c39f3ec3-fc2c-4c12-940f-60d8d3d17660
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 32188b1c47168aefbca914fa15f71850df716153
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597556"
---
# <a name="sql-server-agent-service-cannot-use-sql-server-authentication"></a><span data-ttu-id="28466-102">SQL Server Agent 服務無法使用 SQL Server 驗證</span><span class="sxs-lookup"><span data-stu-id="28466-102">SQL Server Agent Service cannot use SQL Server Authentication</span></span>
  <span data-ttu-id="28466-103">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理程式服務連接至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體時，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理程式只支援 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="28466-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent only supports Windows Authentication when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service connects to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="component"></a><span data-ttu-id="28466-104">元件</span><span class="sxs-lookup"><span data-stu-id="28466-104">Component</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="28466-105">Agent</span><span class="sxs-lookup"><span data-stu-id="28466-105">Agent</span></span>  
  
## <a name="description"></a><span data-ttu-id="28466-106">描述</span><span class="sxs-lookup"><span data-stu-id="28466-106">Description</span></span>  
 <span data-ttu-id="28466-107">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理程式服務只可以使用 Windows 驗證來登入資料庫。</span><span class="sxs-lookup"><span data-stu-id="28466-107">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service can only log on to the database using Windows Authentication.</span></span> <span data-ttu-id="28466-108">這表示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理程式服務帳戶必須是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用者。</span><span class="sxs-lookup"><span data-stu-id="28466-108">This means that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account must be a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user.</span></span>  
  
 <span data-ttu-id="28466-109">如需詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜自動系統管理安全性＞和＜實作 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理程式安全性＞主題。</span><span class="sxs-lookup"><span data-stu-id="28466-109">For more information, see the topics "Security for Automatic Administration" and "Implementing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Security" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28466-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28466-110">See Also</span></span>  
 [<span data-ttu-id="28466-111">SQL Server Agent 升級問題</span><span class="sxs-lookup"><span data-stu-id="28466-111">SQL Server Agent Upgrade Issues</span></span>](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
