---
title: 移除修改系統物件的語句 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- direct system catalog updates [SQL Server]
- system catalogs [SQL Server]
ms.assetid: 221b46c2-c27e-4df8-bd8c-8b990d6d5e98
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 526181bc4bf7ab81df2eaa25f19e7627c9b7af10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710169"
---
# <a name="remove-statements-that-modify-system-objects"></a><span data-ttu-id="2a7e9-102">移除修改系統物件的陳述式</span><span class="sxs-lookup"><span data-stu-id="2a7e9-102">Remove statements that modify system objects</span></span>
  <span data-ttu-id="2a7e9-103">Upgrade Advisor 偵測到更新系統目錄的陳述式。</span><span class="sxs-lookup"><span data-stu-id="2a7e9-103">Upgrade Advisor detected statements that update the system catalog.</span></span> <span data-ttu-id="2a7e9-104">不允許直接更新系統目錄。</span><span class="sxs-lookup"><span data-stu-id="2a7e9-104">Direct system catalog updates are not allowed.</span></span> <span data-ttu-id="2a7e9-105">請修改您的 SQL 指令碼，以使用官方與有記載的應用程式開發介面。</span><span class="sxs-lookup"><span data-stu-id="2a7e9-105">Modify your SQL scripts to use official and documented APIs.</span></span>  
  
## <a name="component"></a><span data-ttu-id="2a7e9-106">元件</span><span class="sxs-lookup"><span data-stu-id="2a7e9-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="2a7e9-107">描述</span><span class="sxs-lookup"><span data-stu-id="2a7e9-107">Description</span></span>  
 <span data-ttu-id="2a7e9-108">不允許直接更新系統目錄。</span><span class="sxs-lookup"><span data-stu-id="2a7e9-108">Direct system catalog updates are not allowed.</span></span> <span data-ttu-id="2a7e9-109">任何執行這個動作的嘗試都將產生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="2a7e9-109">Any attempt to do so will generate the following error:</span></span>  
  
 `Server: Msg 259, Level 16, State 1, Line 1`  
  
 `Ad hoc updates to system catalogs are not allowed.`  
  
## <a name="corrective-action"></a><span data-ttu-id="2a7e9-110">更正動作</span><span class="sxs-lookup"><span data-stu-id="2a7e9-110">Corrective Action</span></span>  
 <span data-ttu-id="2a7e9-111">請修改您的 SQL 指令碼，以使用官方與有記載的應用程式開發介面。</span><span class="sxs-lookup"><span data-stu-id="2a7e9-111">Modify your SQL scripts to use official and documented APIs.</span></span> <span data-ttu-id="2a7e9-112">例如，使用 ALTER DATABASE *database_name*設定緊急，而不是在**sysdatabases**系統資料表上執行 UPDATE 語句。</span><span class="sxs-lookup"><span data-stu-id="2a7e9-112">For example, use ALTER DATABASE *database_name* SET EMERGENCY instead of running an UPDATE statement on the **sysdatabases** system table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a7e9-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a7e9-113">See Also</span></span>  
 <span data-ttu-id="2a7e9-114">[資料庫引擎升級問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="2a7e9-114">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="2a7e9-115">SQL Server 2014 Upgrade Advisor &#91;新的&#93;</span><span class="sxs-lookup"><span data-stu-id="2a7e9-115">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](https://docs.microsoft.com/sql/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
