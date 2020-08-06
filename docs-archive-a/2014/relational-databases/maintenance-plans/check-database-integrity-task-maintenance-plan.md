---
title: 檢查資料庫完整性工作 (維護計畫) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.maintplanproperties.integrity.f1
- sql12.swb.maint.integrity.f1
helpviewer_keywords:
- Check Database Integrity Task dialog box
ms.assetid: 3534494a-5dfe-4738-b49a-e7fabd731c47
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f786755a3b7ed5d991b4cf0e32c067e355c111ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598363"
---
# <a name="check-database-integrity-task-maintenance-plan"></a><span data-ttu-id="6c317-102">檢查資料庫完整性工作 (維護計畫)</span><span class="sxs-lookup"><span data-stu-id="6c317-102">Check Database Integrity Task (Maintenance Plan)</span></span>
  <span data-ttu-id="6c317-103">使用 [檢查資料庫完整性工作] 對話方塊，並執行 `DBCC CHECKDB`[!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式，以檢查使用者和系統資料表的配置和結構完整性以及資料庫的索引。</span><span class="sxs-lookup"><span data-stu-id="6c317-103">Use the **Check Database Integrity Task** dialog to check the allocation and structural integrity of user and system tables, and indexes in the database, by running the `DBCC CHECKDB`[!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="6c317-104">執行 `DBCC` 以確實回報任何有關資料庫完整性的問題，以便系統管理員或資料庫擁有者稍後解決。</span><span class="sxs-lookup"><span data-stu-id="6c317-104">Running `DBCC` ensures that any integrity problems with the database are reported, thereby allowing them to be addressed later by a system administrator or database owner.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6c317-105">選項。</span><span class="sxs-lookup"><span data-stu-id="6c317-105">Options</span></span>  
 <span data-ttu-id="6c317-106">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="6c317-106">**Connection**</span></span>  
 <span data-ttu-id="6c317-107">選取執行此工作時要使用的伺服器連接。</span><span class="sxs-lookup"><span data-stu-id="6c317-107">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="6c317-108">**新增**</span><span class="sxs-lookup"><span data-stu-id="6c317-108">**New**</span></span>  
 <span data-ttu-id="6c317-109">建立新的伺服器連接，以便執行此工作時使用。</span><span class="sxs-lookup"><span data-stu-id="6c317-109">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="6c317-110">下面會描述 **[新增連接]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6c317-110">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="6c317-111">**資料庫**</span><span class="sxs-lookup"><span data-stu-id="6c317-111">**Databases**</span></span>  
 <span data-ttu-id="6c317-112">指定受此工作影響的資料庫。</span><span class="sxs-lookup"><span data-stu-id="6c317-112">Specify the databases affected by this task.</span></span>  
  
-   <span data-ttu-id="6c317-113">**所有資料庫**</span><span class="sxs-lookup"><span data-stu-id="6c317-113">**All databases**</span></span>  
  
     <span data-ttu-id="6c317-114">產生維護計畫，針對所有 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫執行維護工作，但 **tempdb** 除外。</span><span class="sxs-lookup"><span data-stu-id="6c317-114">Generate a maintenance plan that runs maintenance tasks against all [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases except **tempdb**.</span></span>  
  
-   <span data-ttu-id="6c317-115">**所有系統資料庫**</span><span class="sxs-lookup"><span data-stu-id="6c317-115">**All system databases**</span></span>  
  
     <span data-ttu-id="6c317-116">產生維護計畫，針對每個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統資料庫執行維護工作，但 **tempdb**除外。</span><span class="sxs-lookup"><span data-stu-id="6c317-116">Generate a maintenance plan that runs maintenance tasks against each of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases except **tempdb**.</span></span> <span data-ttu-id="6c317-117">不會針對使用者建立的資料庫執行維護工作。</span><span class="sxs-lookup"><span data-stu-id="6c317-117">No maintenance tasks are run against user-created databases.</span></span>  
  
-   <span data-ttu-id="6c317-118">**所有使用者資料庫**</span><span class="sxs-lookup"><span data-stu-id="6c317-118">**All user databases**</span></span>  
  
     <span data-ttu-id="6c317-119">產生維護計畫，針對所有使用者建立的資料庫執行維護工作。</span><span class="sxs-lookup"><span data-stu-id="6c317-119">Generate a maintenance plan that runs maintenance tasks against all user-created databases.</span></span> <span data-ttu-id="6c317-120">不會對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統資料庫執行任何維護工作。</span><span class="sxs-lookup"><span data-stu-id="6c317-120">No maintenance tasks are run against the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases.</span></span>  
  
-   <span data-ttu-id="6c317-121">**這些特定的資料庫**</span><span class="sxs-lookup"><span data-stu-id="6c317-121">**These specific databases**</span></span>  
  
     <span data-ttu-id="6c317-122">產生維護計畫，只針對選取的資料庫執行維護工作。</span><span class="sxs-lookup"><span data-stu-id="6c317-122">Generate a maintenance plan that runs maintenance tasks against only those databases that are selected.</span></span> <span data-ttu-id="6c317-123">如果選擇此選項，則必須在清單中至少選取一個資料庫。</span><span class="sxs-lookup"><span data-stu-id="6c317-123">At least one database in the list must be selected if this option is chosen.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6c317-124">維護計畫只針對相容性層級設為 80 (含) 以上的資料庫來執行。</span><span class="sxs-lookup"><span data-stu-id="6c317-124">Maintenance plans only run against databases set to compatibility level 80 or higher.</span></span> <span data-ttu-id="6c317-125">不會顯示相容性層級設為 70 或更低的資料庫。</span><span class="sxs-lookup"><span data-stu-id="6c317-125">Databases set to compatibility level 70 or lower are not displayed.</span></span>  
  
 <span data-ttu-id="6c317-126">**包含索引**</span><span class="sxs-lookup"><span data-stu-id="6c317-126">**Include indexes**</span></span>  
 <span data-ttu-id="6c317-127">檢查所有的索引頁面以及資料表資料頁面的完整性。</span><span class="sxs-lookup"><span data-stu-id="6c317-127">Check the integrity of all the index pages as well as the table data pages.</span></span>  
  
 <span data-ttu-id="6c317-128">**檢視 T-SQL**</span><span class="sxs-lookup"><span data-stu-id="6c317-128">**View T-SQL**</span></span>  
 <span data-ttu-id="6c317-129">根據選取的選項，檢視此工作在伺服器上執行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="6c317-129">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6c317-130">受影響的物件數目較為大量時，會多花一些時間才會顯示。</span><span class="sxs-lookup"><span data-stu-id="6c317-130">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="6c317-131">新增連接對話方塊</span><span class="sxs-lookup"><span data-stu-id="6c317-131">New Connection Dialog Box</span></span>  
 <span data-ttu-id="6c317-132">**連線名稱**</span><span class="sxs-lookup"><span data-stu-id="6c317-132">**Connection name**</span></span>  
 <span data-ttu-id="6c317-133">輸入新連接的名稱。</span><span class="sxs-lookup"><span data-stu-id="6c317-133">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="6c317-134">**選取或輸入伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="6c317-134">**Select or enter a server name**</span></span>  
 <span data-ttu-id="6c317-135">選取執行此工作時要連接的伺服器。</span><span class="sxs-lookup"><span data-stu-id="6c317-135">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="6c317-136">**[重新整理]**</span><span class="sxs-lookup"><span data-stu-id="6c317-136">**Refresh**</span></span>  
 <span data-ttu-id="6c317-137">重新整理可用的伺服器清單。</span><span class="sxs-lookup"><span data-stu-id="6c317-137">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="6c317-138">**輸入要登入到伺服器的資訊**</span><span class="sxs-lookup"><span data-stu-id="6c317-138">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="6c317-139">指定如何對伺服器進行驗證。</span><span class="sxs-lookup"><span data-stu-id="6c317-139">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="6c317-140">**使用 Windows 整合式安全性**</span><span class="sxs-lookup"><span data-stu-id="6c317-140">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="6c317-141">使用 Windows 驗證連線到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6c317-141">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] with Windows Authentication.</span></span>  
  
 <span data-ttu-id="6c317-142">**使用特定的使用者名稱和密碼**</span><span class="sxs-lookup"><span data-stu-id="6c317-142">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="6c317-143">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證連線到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6c317-143">Connect to an instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="6c317-144">無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="6c317-144">This option is not available.</span></span>  
  
 <span data-ttu-id="6c317-145">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="6c317-145">**User name**</span></span>  
 <span data-ttu-id="6c317-146">提供驗證時要使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。</span><span class="sxs-lookup"><span data-stu-id="6c317-146">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="6c317-147">無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="6c317-147">This option is not available.</span></span>  
  
 <span data-ttu-id="6c317-148">**密碼**</span><span class="sxs-lookup"><span data-stu-id="6c317-148">**Password**</span></span>  
 <span data-ttu-id="6c317-149">提供驗證時要使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="6c317-149">Provide a password to use when authenticating.</span></span> <span data-ttu-id="6c317-150">無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="6c317-150">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c317-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c317-151">See Also</span></span>  
 [<span data-ttu-id="6c317-152">DBCC CHECKDB &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6c317-152">DBCC CHECKDB &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
  
