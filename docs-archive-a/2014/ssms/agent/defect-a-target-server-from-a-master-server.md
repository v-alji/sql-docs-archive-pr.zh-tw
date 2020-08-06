---
title: 使目標伺服器脫離主要伺服器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- target servers [SQL Server], defecting
- SQL Server Agent jobs, master servers
- master servers [SQL Server], defecting target servers
- defecting target servers
ms.assetid: a6da262b-7b38-4ce4-bfd6-6a557c6e8a84
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2b17703fa87f5c0d3e7146a1660ac1ca7c7c1d81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699238"
---
# <a name="defect-a-target-server-from-a-master-server"></a><span data-ttu-id="b82f8-102">使目標伺服器脫離主要伺服器</span><span class="sxs-lookup"><span data-stu-id="b82f8-102">Defect a Target Server from a Master Server</span></span>
  <span data-ttu-id="b82f8-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 SQL Server 管理物件 (SMO) 在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 中從主伺服器脫離目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="b82f8-103">This topic describes how to defect a target server from a master server in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="b82f8-104">請從目標伺服器執行這個程序。</span><span class="sxs-lookup"><span data-stu-id="b82f8-104">Run this procedure from the target server.</span></span>  
  
 <span data-ttu-id="b82f8-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="b82f8-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b82f8-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="b82f8-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b82f8-107">安全性</span><span class="sxs-lookup"><span data-stu-id="b82f8-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b82f8-108">**使用下列方法脫離目標伺服器：**</span><span class="sxs-lookup"><span data-stu-id="b82f8-108">**To defect a target server, using:**</span></span>  
  
     [<span data-ttu-id="b82f8-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b82f8-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b82f8-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b82f8-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="b82f8-111">SMO</span><span class="sxs-lookup"><span data-stu-id="b82f8-111">SMO</span></span>](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b82f8-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="b82f8-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b82f8-113">Security</span><span class="sxs-lookup"><span data-stu-id="b82f8-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b82f8-114">權限</span><span class="sxs-lookup"><span data-stu-id="b82f8-114">Permissions</span></span>  
 <span data-ttu-id="b82f8-115">若要執行這個預存程序，使用者必須是 `sysadmin` (系統管理員) 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="b82f8-115">To execute this stored procedure, a user must be a member of the `sysadmin` fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b82f8-116">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b82f8-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-defect-a-target-server-from-a-master-server"></a><span data-ttu-id="b82f8-117">若要使目標伺服器脫離主伺服器</span><span class="sxs-lookup"><span data-stu-id="b82f8-117">To defect a target server from a master server</span></span>  
  
1.  <span data-ttu-id="b82f8-118">在 **[物件總管]** 中，展開設定為目標伺服器的伺服器。</span><span class="sxs-lookup"><span data-stu-id="b82f8-118">In **Object Explorer**, expand a server that is configured as a target server.</span></span>  
  
2.  <span data-ttu-id="b82f8-119">以滑鼠右鍵按一下 **[SQL Server Agent]**，指向 **[多伺服器管理]**，然後按一下 **[脫離]**。</span><span class="sxs-lookup"><span data-stu-id="b82f8-119">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and then click **Defect**.</span></span>  
  
3.  <span data-ttu-id="b82f8-120">按一下 **[是]** 以確定您要從主要伺服器脫離這台目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="b82f8-120">Click **Yes** to confirm that you want to defect this target server from a master server.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b82f8-121">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b82f8-121">Using Transact-SQL</span></span>  
  
#### <a name="to-defect-a-target-server-from-a-master-server"></a><span data-ttu-id="b82f8-122">若要使目標伺服器脫離主伺服器</span><span class="sxs-lookup"><span data-stu-id="b82f8-122">To defect a target server from a master server</span></span>  
  
1.  <span data-ttu-id="b82f8-123">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b82f8-123">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b82f8-124">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="b82f8-124">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b82f8-125">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="b82f8-125">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
```sql
sp_msx_defect ;  
```  
  
 <span data-ttu-id="b82f8-126">如需詳細資訊，請參閱[sp_msx_defect &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-defect-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b82f8-126">For more information, see [sp_msx_defect &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-defect-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects-smo"></a><a name="PowerShellProcedure"></a><span data-ttu-id="b82f8-127">使用 SQL Server 管理物件 (SMO) </span><span class="sxs-lookup"><span data-stu-id="b82f8-127">Using SQL Server Management Objects (SMO)</span></span>  
 <span data-ttu-id="b82f8-128">請使用 `MsxDefect Method`。</span><span class="sxs-lookup"><span data-stu-id="b82f8-128">Use the `MsxDefect Method`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b82f8-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b82f8-129">See Also</span></span>  
 <span data-ttu-id="b82f8-130">[建立多伺服器環境](create-a-multiserver-environment.md) </span><span class="sxs-lookup"><span data-stu-id="b82f8-130">[Create a Multiserver Environment](create-a-multiserver-environment.md) </span></span>  
 <span data-ttu-id="b82f8-131">[將整個企業的管理自動化](automated-administration-across-an-enterprise.md) </span><span class="sxs-lookup"><span data-stu-id="b82f8-131">[Automated Administration Across an Enterprise](automated-administration-across-an-enterprise.md) </span></span>  
 [<span data-ttu-id="b82f8-132">從主要伺服器脫離多個目標伺服器</span><span class="sxs-lookup"><span data-stu-id="b82f8-132">Defect Multiple Target Servers from a Master Server</span></span>](defect-multiple-target-servers-from-a-master-server.md)  
