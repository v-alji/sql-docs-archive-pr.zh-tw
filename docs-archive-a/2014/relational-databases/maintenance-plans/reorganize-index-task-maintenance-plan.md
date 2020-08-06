---
title: 重新組織索引工作 (維護計畫) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.defrag.f1
helpviewer_keywords:
- Reorganize Index Task dialog box
ms.assetid: e9cbebbd-f36f-4176-9832-382a46ac946c
author: rothja
ms.author: jroth
ms.openlocfilehash: 0bbb154045b781f8a92dfce9c9d2f6ee2d819c17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594518"
---
# <a name="reorganize-index-task-maintenance-plan"></a><span data-ttu-id="5b5b2-102">重新組織索引工作 (維護計畫)</span><span class="sxs-lookup"><span data-stu-id="5b5b2-102">Reorganize Index Task (Maintenance Plan)</span></span>
  <span data-ttu-id="5b5b2-103">使用 [重新組織索引工作]  對話方塊，即可將索引頁面移至更有效率的搜尋順序。</span><span class="sxs-lookup"><span data-stu-id="5b5b2-103">Use the **ReorganizeIndex Task** dialog to move index pages into a more efficient search order.</span></span> <span data-ttu-id="5b5b2-104">此工作會使用 `ALTER INDEX REORGANIZE` 陳述式搭配 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="5b5b2-104">This task uses the `ALTER INDEX REORGANIZE` statement with [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] databases.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5b5b2-105">選項。</span><span class="sxs-lookup"><span data-stu-id="5b5b2-105">Options</span></span>  
 <span data-ttu-id="5b5b2-106">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="5b5b2-106">**Connection**</span></span>  
 <span data-ttu-id="5b5b2-107">選取執行此工作時要使用的伺服器連接。</span><span class="sxs-lookup"><span data-stu-id="5b5b2-107">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="5b5b2-108">**新增**</span><span class="sxs-lookup"><span data-stu-id="5b5b2-108">**New**</span></span>  
 <span data-ttu-id="5b5b2-109">建立新的伺服器連接，以便執行此工作時使用。</span><span class="sxs-lookup"><span data-stu-id="5b5b2-109">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="5b5b2-110">下面會描述 **[新增連接]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="5b5b2-110">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="5b5b2-111">**資料庫**</span><span class="sxs-lookup"><span data-stu-id="5b5b2-111">**Databases**</span></span>  
 <span data-ttu-id="5b5b2-112">指定受此工作影響的資料庫。</span><span class="sxs-lookup"><span data-stu-id="5b5b2-112">Specify the databases affected by this task.</span></span>  
  
-   <span data-ttu-id="5b5b2-113">**所有資料庫**</span><span class="sxs-lookup"><span data-stu-id="5b5b2-113">**All databases**</span></span>  
  
     <span data-ttu-id="5b5b2-114">產生維護計畫，針對所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫執行維護工作，但 tempdb 除外。</span><span class="sxs-lookup"><span data-stu-id="5b5b2-114">Generate a maintenance plan that runs maintenance tasks against all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases except tempdb.</span></span>  
  
-   <span data-ttu-id="5b5b2-115">**所有系統資料庫**</span><span class="sxs-lookup"><span data-stu-id="5b5b2-115">**All system databases**</span></span>  
  
     <span data-ttu-id="5b5b2-116">產生維護計畫，針對每個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統資料庫執行維護工作，但 **tempdb**除外。</span><span class="sxs-lookup"><span data-stu-id="5b5b2-116">Generate a maintenance plan that runs maintenance tasks against each of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases except **tempdb**.</span></span> <span data-ttu-id="5b5b2-117">不會針對使用者建立的資料庫執行維護工作。</span><span class="sxs-lookup"><span data-stu-id="5b5b2-117">No maintenance tasks are run against user-created databases.</span></span>  
  
-   <span data-ttu-id="5b5b2-118">**所有使用者資料庫**</span><span class="sxs-lookup"><span data-stu-id="5b5b2-118">**All user databases**</span></span>  
  
     <span data-ttu-id="5b5b2-119">產生維護計畫，針對所有使用者建立的資料庫執行維護工作。</span><span class="sxs-lookup"><span data-stu-id="5b5b2-119">Generate a maintenance plan that runs maintenance tasks against all user-created databases.</span></span> <span data-ttu-id="5b5b2-120">不會對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統資料庫執行任何維護工作。</span><span class="sxs-lookup"><span data-stu-id="5b5b2-120">No maintenance tasks are run against the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases.</span></span>  
  
-   <span data-ttu-id="5b5b2-121">**這些特定的資料庫**</span><span class="sxs-lookup"><span data-stu-id="5b5b2-121">**These specific databases**</span></span>  
  
     <span data-ttu-id="5b5b2-122">產生維護計畫，只針對選取的資料庫執行維護工作。</span><span class="sxs-lookup"><span data-stu-id="5b5b2-122">Generate a maintenance plan that runs maintenance tasks against only those databases that are selected.</span></span> <span data-ttu-id="5b5b2-123">如果選擇此選項，則必須在清單中至少選取一個資料庫。</span><span class="sxs-lookup"><span data-stu-id="5b5b2-123">At least one database in the list must be selected if this option is chosen.</span></span>  
  
 <span data-ttu-id="5b5b2-124">**Object**</span><span class="sxs-lookup"><span data-stu-id="5b5b2-124">**Object**</span></span>  
 <span data-ttu-id="5b5b2-125">限制 [選取範圍]  格線僅顯示資料表、檢視或兩者。</span><span class="sxs-lookup"><span data-stu-id="5b5b2-125">Limit the **Selection** grid to display tables, views, or both.</span></span>  
  
 <span data-ttu-id="5b5b2-126">**選取範圍**</span><span class="sxs-lookup"><span data-stu-id="5b5b2-126">**Selection**</span></span>  
 <span data-ttu-id="5b5b2-127">指定受此工作影響的資料表或索引。</span><span class="sxs-lookup"><span data-stu-id="5b5b2-127">Specify the tables or indexes affected by this task.</span></span> <span data-ttu-id="5b5b2-128">[物件] 方塊中的 [資料表和檢視] 為選取狀態時無法使用。</span><span class="sxs-lookup"><span data-stu-id="5b5b2-128">Not available when **Tables and Views** is selected in the **Object** box.</span></span>  
  
 <span data-ttu-id="5b5b2-129">**壓縮大型物件**</span><span class="sxs-lookup"><span data-stu-id="5b5b2-129">**Compact large objects**</span></span>  
 <span data-ttu-id="5b5b2-130">可能時取消配置給資料表和檢視的空間。</span><span class="sxs-lookup"><span data-stu-id="5b5b2-130">Deallocate space for tables and views when possible.</span></span> <span data-ttu-id="5b5b2-131">此選項使用 `ALTER INDEX LOB_COMPACTION = ON`。</span><span class="sxs-lookup"><span data-stu-id="5b5b2-131">This option uses `ALTER INDEX LOB_COMPACTION = ON`.</span></span>  
  
 <span data-ttu-id="5b5b2-132">**檢視 T-SQL**</span><span class="sxs-lookup"><span data-stu-id="5b5b2-132">**View T-SQL**</span></span>  
 <span data-ttu-id="5b5b2-133">根據選取的選項，檢視此工作在伺服器上執行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="5b5b2-133">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5b5b2-134">受影響的物件數目較為大量時，會多花一些時間才會顯示。</span><span class="sxs-lookup"><span data-stu-id="5b5b2-134">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="5b5b2-135">新增連接對話方塊</span><span class="sxs-lookup"><span data-stu-id="5b5b2-135">New Connection Dialog Box</span></span>  
 <span data-ttu-id="5b5b2-136">**連線名稱**</span><span class="sxs-lookup"><span data-stu-id="5b5b2-136">**Connection name**</span></span>  
 <span data-ttu-id="5b5b2-137">輸入新連接的名稱。</span><span class="sxs-lookup"><span data-stu-id="5b5b2-137">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="5b5b2-138">**選取或輸入伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="5b5b2-138">**Select or enter a server name**</span></span>  
 <span data-ttu-id="5b5b2-139">選取執行此工作時要連接的伺服器。</span><span class="sxs-lookup"><span data-stu-id="5b5b2-139">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="5b5b2-140">**[重新整理]**</span><span class="sxs-lookup"><span data-stu-id="5b5b2-140">**Refresh**</span></span>  
 <span data-ttu-id="5b5b2-141">重新整理可用的伺服器清單。</span><span class="sxs-lookup"><span data-stu-id="5b5b2-141">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="5b5b2-142">**輸入要登入到伺服器的資訊**</span><span class="sxs-lookup"><span data-stu-id="5b5b2-142">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="5b5b2-143">指定如何對伺服器進行驗證。</span><span class="sxs-lookup"><span data-stu-id="5b5b2-143">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="5b5b2-144">**使用 Windows 整合式安全性**</span><span class="sxs-lookup"><span data-stu-id="5b5b2-144">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="5b5b2-145">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows 驗證連線到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="5b5b2-145">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] with [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span>  
  
 <span data-ttu-id="5b5b2-146">**使用特定的使用者名稱和密碼**</span><span class="sxs-lookup"><span data-stu-id="5b5b2-146">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="5b5b2-147">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證連線到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="5b5b2-147">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="5b5b2-148">無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="5b5b2-148">This option is not available.</span></span>  
  
 <span data-ttu-id="5b5b2-149">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="5b5b2-149">**User name**</span></span>  
 <span data-ttu-id="5b5b2-150">提供驗證時要使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。</span><span class="sxs-lookup"><span data-stu-id="5b5b2-150">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="5b5b2-151">無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="5b5b2-151">This option is not available.</span></span>  
  
 <span data-ttu-id="5b5b2-152">**密碼**</span><span class="sxs-lookup"><span data-stu-id="5b5b2-152">**Password**</span></span>  
 <span data-ttu-id="5b5b2-153">提供驗證時要使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="5b5b2-153">Provide a password to use when authenticating.</span></span> <span data-ttu-id="5b5b2-154">無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="5b5b2-154">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b5b2-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b5b2-155">See Also</span></span>  
 <span data-ttu-id="5b5b2-156">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5b5b2-156">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) </span></span>  
 [<span data-ttu-id="5b5b2-157">DBCC INDEXDEFRAG &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5b5b2-157">DBCC INDEXDEFRAG &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-indexdefrag-transact-sql)  
  
  
