---
title: 同步處理目標伺服器時鐘 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- clocks [SQL Server]
- master servers [SQL Server], clock synchronization
- synchronization [SQL Server], target server clocks
- target servers [SQL Server], clock synchronization
ms.assetid: 4fb80502-d271-4d06-bcbc-bfbbceb5f2a2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8e7150cd42699503ab22cdd89fb6206194bd64e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686748"
---
# <a name="synchronize-target-server-clocks-sql-server-management-studio"></a><span data-ttu-id="87693-102">Synchronize Target Server Clocks (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="87693-102">Synchronize Target Server Clocks (SQL Server Management Studio)</span></span>
  <span data-ttu-id="87693-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，將 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的目標伺服器的時鐘與主要伺服器的時鐘進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="87693-103">This topic describes how to synchronize target server clocks in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] with the master server clock by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="87693-104">同步處理這些系統時鐘可以支援您的作業排程。</span><span class="sxs-lookup"><span data-stu-id="87693-104">Synchronizing these system clocks supports your job schedules.</span></span>  
  
 <span data-ttu-id="87693-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="87693-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="87693-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="87693-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="87693-107">安全性</span><span class="sxs-lookup"><span data-stu-id="87693-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="87693-108">**若要使用下列項目將目標伺服器的時鐘同步處理：**</span><span class="sxs-lookup"><span data-stu-id="87693-108">**To synchronize target server clocks, using:**</span></span>  
  
     [<span data-ttu-id="87693-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="87693-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="87693-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="87693-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="87693-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="87693-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="87693-112">Security</span><span class="sxs-lookup"><span data-stu-id="87693-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="87693-113">權限</span><span class="sxs-lookup"><span data-stu-id="87693-113">Permissions</span></span>  
 <span data-ttu-id="87693-114">需要 **系統管理員 (sysadmin)** 固定伺服器角色中的成員資格。</span><span class="sxs-lookup"><span data-stu-id="87693-114">Requires membership in the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="87693-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="87693-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-synchronize-target-server-clocks"></a><span data-ttu-id="87693-116">若要將目標伺服器的時鐘同步化</span><span class="sxs-lookup"><span data-stu-id="87693-116">To synchronize target server clocks</span></span>  
  
1.  <span data-ttu-id="87693-117">在 **[物件總管]** 中，按一下加號，展開要將目標伺服器的時鐘與主要伺服器的時鐘進行同步處理的伺服器。</span><span class="sxs-lookup"><span data-stu-id="87693-117">In **Object Explorer,** click the plus sign to expand the server where you want to synchronize the target server clocks with the master server clock.</span></span>  
  
2.  <span data-ttu-id="87693-118">以滑鼠右鍵按一下 [SQL Server Agent]\*\*\*\*、指向 [多伺服器管理]\*\*\*\*，然後選取 [管理目標伺服器]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="87693-118">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and select **Manage Target Servers**.</span></span>  
  
3.  <span data-ttu-id="87693-119">在 **[管理目標伺服器]** 對話方塊中，按一下 **[公佈指示]**。</span><span class="sxs-lookup"><span data-stu-id="87693-119">In the **Manage Target Servers** dialog box, click **Post Instructions**.</span></span>  
  
4.  <span data-ttu-id="87693-120">在 **[指示類型]** 清單中選取 **[同步處理時鐘]**。</span><span class="sxs-lookup"><span data-stu-id="87693-120">In the **Instruction type** list, select **Synchronize clocks**.</span></span>  
  
5.  <span data-ttu-id="87693-121">在 **[收件者]** 下，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="87693-121">Under **Recipients**, do one of the following:</span></span>  
  
    -   <span data-ttu-id="87693-122">按一下 **[所有目標伺服器]** ，將所有目標伺服器的時鐘與主要伺服器的時鐘進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="87693-122">Click **All target servers** to synchronize all target server clocks with the master server clock.</span></span>  
  
    -   <span data-ttu-id="87693-123">按一下 **[下列目標伺服器]** 以同步處理特定的伺服器時鐘，然後選取要與主要伺服器時鐘進行時鐘同步處理的每一部目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="87693-123">Click **These target servers** to synchronize certain server clocks, and then select each target server whose clock you want to synchronize with the master server clock.</span></span>  
  
6.  <span data-ttu-id="87693-124">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="87693-124">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="87693-125">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="87693-125">Using Transact-SQL</span></span>  
  
#### <a name="to-synchronize-target-server-clocks"></a><span data-ttu-id="87693-126">若要將目標伺服器的時鐘同步化</span><span class="sxs-lookup"><span data-stu-id="87693-126">To synchronize target server clocks</span></span>  
  
1.  <span data-ttu-id="87693-127">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="87693-127">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="87693-128">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="87693-128">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="87693-129">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="87693-129">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE msdb ;  
    GO  
    -- resynchronizes the SEATTLE1 target server  
    EXEC dbo.sp_resync_targetserver  
        N'SEATTLE1' ;  
    GO  
    ```  
  
 <span data-ttu-id="87693-130">如需詳細資訊，請參閱[sp_resync_targetserver &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="87693-130">For more information, see [sp_resync_targetserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql).</span></span>  
  
  
