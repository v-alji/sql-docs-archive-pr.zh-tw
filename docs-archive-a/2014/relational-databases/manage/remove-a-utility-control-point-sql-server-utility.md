---
title: 移除公用程式控制點 (SQL Server 公用程式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c048a416-900e-4c77-8243-e0f0d8b94068
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fe4ebb9de3f7644b4cff5c7dbfb34e50be7e8993
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606834"
---
# <a name="remove-a-utility-control-point-sql-server-utility"></a><span data-ttu-id="84384-102">移除公用程式控制點 (SQL Server 公用程式)</span><span class="sxs-lookup"><span data-stu-id="84384-102">Remove a Utility Control Point (SQL Server Utility)</span></span>
  <span data-ttu-id="84384-103">此主題描述如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中從 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 執行個體移除 [!INCLUDE[tsql](../../includes/tsql-md.md)]公用程式控制點 (UCP)。</span><span class="sxs-lookup"><span data-stu-id="84384-103">This topic describes how to remove a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utility control point (UCP) from the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="84384-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="84384-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="84384-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="84384-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="84384-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="84384-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="84384-107">安全性</span><span class="sxs-lookup"><span data-stu-id="84384-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="84384-108">**若要使用下列項目移除公用程式控制點：**</span><span class="sxs-lookup"><span data-stu-id="84384-108">**To remove a Utility Control Point, using:**</span></span>  
  
     [<span data-ttu-id="84384-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="84384-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="84384-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="84384-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="84384-111">限制事項</span><span class="sxs-lookup"><span data-stu-id="84384-111">Limitations and Restrictions</span></span>  
 <span data-ttu-id="84384-112">在您使用此程序從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 公用程式移除 UCP 之前，請注意下列需求。</span><span class="sxs-lookup"><span data-stu-id="84384-112">Before you use this procedure to remove the UCP from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility, note the following requirements.</span></span> <span data-ttu-id="84384-113">預存程序將會在操作時執行必要條件檢查。</span><span class="sxs-lookup"><span data-stu-id="84384-113">The stored procedure will run prerequisite checks as part of the operation.</span></span>  
  
-   <span data-ttu-id="84384-114">在您執行此程序之前，必須從 UCP 中移除所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 受管理的執行個體。</span><span class="sxs-lookup"><span data-stu-id="84384-114">Before you run this procedure, all managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be removed from the UCP.</span></span> <span data-ttu-id="84384-115">請注意，UCP 是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的受管理的執行個體。</span><span class="sxs-lookup"><span data-stu-id="84384-115">Note that the UCP is a managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="84384-116">如需詳細資訊，請參閱 [從 SQL Server 公用程式中移除 SQL Server 執行個體](remove-an-instance-of-sql-server-from-the-sql-server-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="84384-116">From more information, see [Remove an Instance of SQL Server from the SQL Server Utility](remove-an-instance-of-sql-server-from-the-sql-server-utility.md).</span></span>  
  
-   <span data-ttu-id="84384-117">此程序必須在成為 UCP 的電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="84384-117">This procedure must be run on a computer that is a UCP.</span></span>  
  
-   <span data-ttu-id="84384-118">如果已移除 UCP 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體具有非公用程式資料收集組，此程序就不會卸除 UMDW 資料庫 (sysutility_mdw)。</span><span class="sxs-lookup"><span data-stu-id="84384-118">If the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] where the UCP was removed has a non-Utility data collection set, the UMDW database (sysutility_mdw) will not be dropped by the procedure.</span></span> <span data-ttu-id="84384-119">如果發生這種情況，您就必須先手動卸除 UMDW 資料庫 (sysutility_mdw)，然後才能再次建立 UCP。</span><span class="sxs-lookup"><span data-stu-id="84384-119">If this is the case, the UMDW database (sysutility_mdw) must be dropped manually before the UCP can be created again.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="84384-120">Security</span><span class="sxs-lookup"><span data-stu-id="84384-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="84384-121">權限</span><span class="sxs-lookup"><span data-stu-id="84384-121">Permissions</span></span>  
 <span data-ttu-id="84384-122">此程序必須由擁有系統管理員 (`sysadmin`) 權限的使用者執行，而這些是建立 UCP 所需的相同權限。</span><span class="sxs-lookup"><span data-stu-id="84384-122">This procedure must be run by a user with `sysadmin` permissions; the same permissions required to create a UCP.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="84384-123">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="84384-123">Using Transact-SQL</span></span>  
  
#### <a name="to-remove-a-utility-control-point"></a><span data-ttu-id="84384-124">若要移除公用程式控制點</span><span class="sxs-lookup"><span data-stu-id="84384-124">To remove a Utility Control Point</span></span>  
  
1.  <span data-ttu-id="84384-125">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="84384-125">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="84384-126">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="84384-126">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="84384-127">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="84384-127">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
```  
EXEC msdb.dbo.sp_sysutility_ucp_remove;  
```  
  
## <a name="see-also"></a><span data-ttu-id="84384-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84384-128">See Also</span></span>  
 <span data-ttu-id="84384-129">[SQL Server 公用程式的功能與工作](sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="84384-129">[SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md) </span></span>  
 <span data-ttu-id="84384-130">[使用公用程式總管來管理 SQL Server 公用程式](use-utility-explorer-to-manage-the-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="84384-130">[Use Utility Explorer to Manage the SQL Server Utility](use-utility-explorer-to-manage-the-sql-server-utility.md) </span></span>  
 [<span data-ttu-id="84384-131">疑難排解 SQL Server 公用程式</span><span class="sxs-lookup"><span data-stu-id="84384-131">Troubleshoot the SQL Server Utility</span></span>](../../database-engine/troubleshoot-the-sql-server-utility.md)  
  
  
