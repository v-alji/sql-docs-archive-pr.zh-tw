---
title: 設定目標伺服器的輪詢間隔 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- interval for polling [SQL Server]
- target servers [SQL Server], polling interval
- polling interval [SQL Server]
ms.assetid: 4ffbbefa-77fb-442e-a77c-cb8c6cab9f3c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 36517f60a99a1a844f6d14d489587eef1de9cb13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710093"
---
# <a name="set-the-polling-interval-for-target-servers"></a><span data-ttu-id="9baa5-102">Set the Polling Interval for Target Servers</span><span class="sxs-lookup"><span data-stu-id="9baa5-102">Set the Polling Interval for Target Servers</span></span>
  <span data-ttu-id="9baa5-103">本主題描述如何設定 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 從主伺服器重新整理資訊到目標伺服器的頻率。</span><span class="sxs-lookup"><span data-stu-id="9baa5-103">This topic describes how to set the frequency that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent refreshes information from the master to the target servers.</span></span> <span data-ttu-id="9baa5-104">作業是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 執行的一系列指定動作。</span><span class="sxs-lookup"><span data-stu-id="9baa5-104">A job is a specified series of actions that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent performs.</span></span> <span data-ttu-id="9baa5-105">多重伺服器作業是一個主要伺服器執行於一或多個目標伺服器上的作業。</span><span class="sxs-lookup"><span data-stu-id="9baa5-105">A multiserver job is a job that a master server runs on one or more target servers.</span></span>  
  
-   <span data-ttu-id="9baa5-106">**開始之前：** [安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="9baa5-106">**Before you begin:**  [Security](#Security)</span></span>  
  
-   <span data-ttu-id="9baa5-107">**若要設定目標伺服器的輪詢間隔，使用**  [SQL Server Management Studio](#SSMS)、 [Transact-SQL](#TSQL)</span><span class="sxs-lookup"><span data-stu-id="9baa5-107">**To set the polling interval for target servers, using:**  [SQL Server Management Studio](#SSMS), [Transact-SQL](#TSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9baa5-108">開始之前</span><span class="sxs-lookup"><span data-stu-id="9baa5-108">Before You Begin</span></span>  
 <span data-ttu-id="9baa5-109">每一個目標伺服器可以同時執行相同作業的一個執行個體。</span><span class="sxs-lookup"><span data-stu-id="9baa5-109">Each target server can run one instance of the same job at the same time.</span></span> <span data-ttu-id="9baa5-110">每個目標伺服器會定期輪詢主要伺服器、下載任何指派到目標伺服器的新作業之副本，然後中斷連接。</span><span class="sxs-lookup"><span data-stu-id="9baa5-110">Each target server periodically polls the master server, downloads a copy of any new jobs assigned to the target server, and then disconnects.</span></span> <span data-ttu-id="9baa5-111">目標伺服器會先在本機執行作業，然後再重新連接到主要伺服器，以便上傳作業結果的狀態。</span><span class="sxs-lookup"><span data-stu-id="9baa5-111">The target server runs the job locally and then reconnects to the master server to upload the job outcome status.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9baa5-112">如果當目標伺服器嘗試上傳作業狀態時無法存取主要伺服器，作業狀態會被多工緩衝處理，直到可以存取主要伺服器為止。</span><span class="sxs-lookup"><span data-stu-id="9baa5-112">If the master server is inaccessible when the target server tries to upload job status, the job status is spooled until the master server can be accessed.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9baa5-113">Security</span><span class="sxs-lookup"><span data-stu-id="9baa5-113">Security</span></span>  
 <span data-ttu-id="9baa5-114">如需詳細資訊，請參閱＜ [Implement SQL Server Agent Security](implement-sql-server-agent-security.md) ＞和＜ [Choose the Right SQL Server Agent Service Account for Multiserver Environments](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md)＞。</span><span class="sxs-lookup"><span data-stu-id="9baa5-114">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md) and [Choose the Right SQL Server Agent Service Account for Multiserver Environments](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> <span data-ttu-id="9baa5-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9baa5-115">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="9baa5-116">**若要設定目標伺服器的輪詢間隔**</span><span class="sxs-lookup"><span data-stu-id="9baa5-116">**To set the polling interval for target servers**</span></span>  
  
1.  <span data-ttu-id="9baa5-117">在**物件總管中，** 連接到的實例 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] ，然後展開該實例。</span><span class="sxs-lookup"><span data-stu-id="9baa5-117">In **Object Explorer,** connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="9baa5-118">以滑鼠右鍵按一下 [SQL Server Agent]\*\*\*\*，指向 [多重伺服器管理]\*\*\*\*，然後按一下 [管理目標伺服器]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9baa5-118">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and then click **Manage Target Servers**.</span></span>  
  
3.  <span data-ttu-id="9baa5-119">在 **[目標伺服器狀態]** 索引標籤上，按一下 **[公佈指示]**。</span><span class="sxs-lookup"><span data-stu-id="9baa5-119">On the **Target Server Status** tab, click **Post Instructions**.</span></span>  
  
4.  <span data-ttu-id="9baa5-120">在 **[指示類型]** 清單中選取 **[設定輪詢間隔]**。</span><span class="sxs-lookup"><span data-stu-id="9baa5-120">In the **Instruction type** list, select **Set polling interval**.</span></span>  
  
5.  <span data-ttu-id="9baa5-121">在 **[輪詢間隔]** 方塊中，輸入介於 10 到 28,800 之間的秒數，這是目標伺服器輪詢主要伺服器之前所需經過的時間。</span><span class="sxs-lookup"><span data-stu-id="9baa5-121">In the **Polling interval** box, enter the number of seconds from 10 through 28,800 that must pass before the target server polls the master server.</span></span>  
  
6.  <span data-ttu-id="9baa5-122">在 **[收件者]** 下，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="9baa5-122">Under **Recipients**, do one of the following:</span></span>  
  
    1.  <span data-ttu-id="9baa5-123">如果所有的目標伺服器共用相同的輪詢間隔，請按一下 **[所有目標伺服器]** 。</span><span class="sxs-lookup"><span data-stu-id="9baa5-123">Click **All target servers** if all target servers share the same polling interval.</span></span>  
  
    2.  <span data-ttu-id="9baa5-124">如果並非所有的目標伺服器都共用相同的輪詢間隔，請按一下 **[下列目標伺服器]** ，然後選取將使用此輪詢間隔的每一部目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="9baa5-124">Click **These target servers** if not all target servers share the same polling interval, and then select each target server that will use this polling interval.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="9baa5-125">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9baa5-125">Using Transact-SQL</span></span>  
 <span data-ttu-id="9baa5-126">**若要設定目標伺服器的輪詢間隔**</span><span class="sxs-lookup"><span data-stu-id="9baa5-126">**To set the polling interval for target servers**</span></span>  
  
1.  <span data-ttu-id="9baa5-127">在 [物件總管] 中，連接到 Database Engine 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="9baa5-127">In Object Explorer, connect to an instance of the Database Engine, and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="9baa5-128">在工具列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="9baa5-128">On the toolbar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="9baa5-129">在查詢視窗中，使用[sp_post_msx_operation &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql)系統預存程式來設定目標伺服器的輪詢間隔。</span><span class="sxs-lookup"><span data-stu-id="9baa5-129">In the query window, use the [sp_post_msx_operation &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql) system stored procedure to set the polling interval for target servers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9baa5-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9baa5-130">See Also</span></span>  
 [<span data-ttu-id="9baa5-131">dbo.sysdownloadlist &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="9baa5-131">dbo.sysdownloadlist &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-tables/dbo-sysdownloadlist-transact-sql)  
  
  
