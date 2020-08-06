---
title: SQL Server 複寫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], about
- replication [SQL Server]
ms.assetid: 3a5f4592-3c61-4b4d-9ceb-39716aeeba41
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e51f45e06939971ada6166fb977c787ad0354926
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585257"
---
# <a name="sql-server-replication"></a><span data-ttu-id="f2ff2-102">SQL Server 複寫</span><span class="sxs-lookup"><span data-stu-id="f2ff2-102">SQL Server Replication</span></span>
  <span data-ttu-id="f2ff2-103">複寫是指，將資料和資料庫物件從某個資料庫複製和散發到另一個資料庫，然後在兩個資料庫之間進行同步處理，以維護一致性的一組技術。</span><span class="sxs-lookup"><span data-stu-id="f2ff2-103">Replication is a set of technologies for copying and distributing data and database objects from one database to another and then synchronizing between databases to maintain consistency.</span></span> <span data-ttu-id="f2ff2-104">使用複寫，您可以透過區域網路、廣域網路、撥號連接、無線連接及網際網路，將資料散發到不同的位置，以及散發到遠端或行動使用者。</span><span class="sxs-lookup"><span data-stu-id="f2ff2-104">Using replication, you can distribute data to different locations and to remote or mobile users over local and wide area networks, dial-up connections, wireless connections, and the Internet.</span></span>  
  
 <span data-ttu-id="f2ff2-105">異動複寫一般用於需要高輸送量的伺服器對伺服器案例中，其中包括：提升延展性和可用性、資料倉儲和報表、整合多個站台的資料、整合異質資料，以及卸載批次處理。</span><span class="sxs-lookup"><span data-stu-id="f2ff2-105">Transactional replication is typically used in server-to-server scenarios that require high throughput, including: improving scalability and availability; data warehousing and reporting; integrating data from multiple sites; integrating heterogeneous data; and offloading batch processing.</span></span> <span data-ttu-id="f2ff2-106">合併式複寫主要是為了可能具有資料衝突的行動應用程式或分散式伺服器應用程式而設計。</span><span class="sxs-lookup"><span data-stu-id="f2ff2-106">Merge replication is primarily designed for mobile applications or distributed server applications that have possible data conflicts.</span></span> <span data-ttu-id="f2ff2-107">常見的案例包括：與行動使用者交換資料、消費者銷售點 (POS) 應用程式，以及多個站台的資料整合。</span><span class="sxs-lookup"><span data-stu-id="f2ff2-107">Common scenarios include: exchanging data with mobile users; consumer point of sale (POS) applications; and integration of data from multiple sites.</span></span> <span data-ttu-id="f2ff2-108">快照式複寫用於提供交易式和合併式複寫的初始資料集；它也可以用於適合將資料完全重新整理時。</span><span class="sxs-lookup"><span data-stu-id="f2ff2-108">Snapshot replication is used to provide the initial data set for transactional and merge replication; it can also be used when complete refreshes of data are appropriate.</span></span> <span data-ttu-id="f2ff2-109">使用這三種複寫， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供了強大且彈性的系統，可同步處理您企業中的資料。</span><span class="sxs-lookup"><span data-stu-id="f2ff2-109">With these three types of replication, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides a powerful and flexible system for synchronizing data across your enterprise.</span></span> <span data-ttu-id="f2ff2-110">[!INCLUDE[win8srv](../../includes/win8srv-md.md)] 和 [!INCLUDE[win8](../../includes/win8-md.md)]支援複寫至 SQLCE 3.5 和 SQLCE 4.0。</span><span class="sxs-lookup"><span data-stu-id="f2ff2-110">Replication to SQLCE 3.5 and SQLCE 4.0 is supported on both [!INCLUDE[win8srv](../../includes/win8srv-md.md)] and [!INCLUDE[win8](../../includes/win8-md.md)].</span></span>  
  
 <span data-ttu-id="f2ff2-111">複寫的替代方法是使用 Microsoft Sync Framework 以同步處理資料庫。</span><span class="sxs-lookup"><span data-stu-id="f2ff2-111">As an alternative to replication, you can synchronize databases by using Microsoft Sync Framework.</span></span> <span data-ttu-id="f2ff2-112">Sync Framework 包含多個元件以及一個直覺式且彈性的 API，而此 API 可簡化 SQL Server、SQL Server Express、SQL Server Compact 和 SQL Azure 資料庫之間的同步處理。</span><span class="sxs-lookup"><span data-stu-id="f2ff2-112">Sync Framework includes components and an intuitive and flexible API that make it easy to synchronize among SQL Server, SQL Server Express, SQL Server Compact, and SQL Azure databases.</span></span> <span data-ttu-id="f2ff2-113">Sync Framework 也會包含類別，您可以調整這些類別以同步處理 SQL Server 資料庫與 ADO.NET 相容的任何其他資料庫。</span><span class="sxs-lookup"><span data-stu-id="f2ff2-113">Sync Framework also includes classes that can be adapted to synchronize between a SQL Server database and any other database that is compatible with ADO.NET.</span></span> <span data-ttu-id="f2ff2-114">如需 Sync Framework 資料庫同步處理元件的詳細文件，請參閱 [同步處理資料庫](https://go.microsoft.com/fwlink/?LinkId=209079)。</span><span class="sxs-lookup"><span data-stu-id="f2ff2-114">For detailed documentation of the Sync Framework database synchronization components, see [Synchronizing Databases](https://go.microsoft.com/fwlink/?LinkId=209079).</span></span> <span data-ttu-id="f2ff2-115">如需 Sync Framework 的概觀，請參閱 [Microsoft Sync Framework 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=209078)。</span><span class="sxs-lookup"><span data-stu-id="f2ff2-115">For an overview of Sync Framework, see [Microsoft Sync Framework Developer Center](https://go.microsoft.com/fwlink/?LinkId=209078).</span></span> <span data-ttu-id="f2ff2-116">如需 Sync Framework 與合併式複寫的比較，請參閱 [概觀和案例](https://msdn.microsoft.com/library/bb902818\(SQL.110\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="f2ff2-116">For a comparison between Sync Framework and Merge Replication, see [Synchronizing Databases Overview](https://msdn.microsoft.com/library/bb902818\(SQL.110\).aspx)</span></span>  
  

## <a name="whats-new"></a><span data-ttu-id="f2ff2-117">新功能</span><span class="sxs-lookup"><span data-stu-id="f2ff2-117">What's new</span></span> 
- <span data-ttu-id="f2ff2-118">SQL Server 2017 尚未在 SQL Server 複寫中導入重大的新功能。</span><span class="sxs-lookup"><span data-stu-id="f2ff2-118">SQL Server 2017 has not introduced significant new features to SQL Server replication.</span></span> 
- <span data-ttu-id="f2ff2-119">SQL Server 2016 尚未在 SQL Server 複寫中導入重大的新功能。</span><span class="sxs-lookup"><span data-stu-id="f2ff2-119">SQL Server 2016 has not introduced significant new features to SQL Server replication.</span></span> 

<span data-ttu-id="f2ff2-120">如需回溯相容性資訊，請參閱[複寫回溯相容性](replication-backward-compatibility.md)</span><span class="sxs-lookup"><span data-stu-id="f2ff2-120">For backward compatibility information see, [Replication Backward Compatibility](replication-backward-compatibility.md)</span></span> 


 ## <a name="replication-security"></a><span data-ttu-id="f2ff2-121">複寫安全性</span><span class="sxs-lookup"><span data-stu-id="f2ff2-121">Replication security</span></span>
  
-   [<span data-ttu-id="f2ff2-122">檢視及修改複寫安全性設定</span><span class="sxs-lookup"><span data-stu-id="f2ff2-122">View and Modify Replication Security Settings</span></span>](security/view-and-modify-replication-security-settings.md)  
-   [<span data-ttu-id="f2ff2-123">管理發行集存取清單中的登入</span><span class="sxs-lookup"><span data-stu-id="f2ff2-123">Manage Logins in the Publication Access List</span></span>](security/manage-logins-in-the-publication-access-list.md)  
  
## <a name="publishing-and-distribution"></a><span data-ttu-id="f2ff2-124">發行和散發</span><span class="sxs-lookup"><span data-stu-id="f2ff2-124">Publishing and Distribution</span></span>  
  
-   [<span data-ttu-id="f2ff2-125">設定發行和散發</span><span class="sxs-lookup"><span data-stu-id="f2ff2-125">Configure Publishing and Distribution</span></span>](configure-publishing-and-distribution.md)   
-   [<span data-ttu-id="f2ff2-126">檢視和修改發行集屬性</span><span class="sxs-lookup"><span data-stu-id="f2ff2-126">View and Modify Publication Properties</span></span>](publish/view-and-modify-publication-properties.md)   
-   [<span data-ttu-id="f2ff2-127">停用發行和散發</span><span class="sxs-lookup"><span data-stu-id="f2ff2-127">Disable Publishing and Distribution</span></span>](disable-publishing-and-distribution.md)  
  
## <a name="publications-and-articles"></a><span data-ttu-id="f2ff2-128">發行集和發行項</span><span class="sxs-lookup"><span data-stu-id="f2ff2-128">Publications and Articles</span></span> 
  
-   [<span data-ttu-id="f2ff2-129">建立發行集</span><span class="sxs-lookup"><span data-stu-id="f2ff2-129">Create a Publication</span></span>](publish/create-a-publication.md)    
-   [<span data-ttu-id="f2ff2-130">定義發行項</span><span class="sxs-lookup"><span data-stu-id="f2ff2-130">Define an Article</span></span>](publish/define-an-article.md)   
-   [<span data-ttu-id="f2ff2-131">檢視和修改發行集屬性</span><span class="sxs-lookup"><span data-stu-id="f2ff2-131">View and Modify Publication Properties</span></span>](publish/view-and-modify-publication-properties.md)   
-   [<span data-ttu-id="f2ff2-132">檢視和修改發行項屬性</span><span class="sxs-lookup"><span data-stu-id="f2ff2-132">View and Modify Article Properties</span></span>](publish/view-and-modify-article-properties.md)    
-   [<span data-ttu-id="f2ff2-133">刪除發行集</span><span class="sxs-lookup"><span data-stu-id="f2ff2-133">Delete a Publication</span></span>](publish/delete-a-publication.md)   
-   [<span data-ttu-id="f2ff2-134">刪除發行項</span><span class="sxs-lookup"><span data-stu-id="f2ff2-134">Delete an Article</span></span>](publish/delete-an-article.md)    
-   [<span data-ttu-id="f2ff2-135">從 Oracle 資料庫建立發行集</span><span class="sxs-lookup"><span data-stu-id="f2ff2-135">Create a Publication from an Oracle Database</span></span>](publish/create-a-publication-from-an-oracle-database.md)   
-   [<span data-ttu-id="f2ff2-136">設定訂閱的到期時間</span><span class="sxs-lookup"><span data-stu-id="f2ff2-136">Set the Expiration Period for Subscriptions</span></span>](publish/set-the-expiration-period-for-subscriptions.md)  
-   [<span data-ttu-id="f2ff2-137">指定結構描述選項</span><span class="sxs-lookup"><span data-stu-id="f2ff2-137">Specify Schema Options</span></span>](publish/specify-schema-options.md)  
-   [<span data-ttu-id="f2ff2-138">複寫結構描述變更</span><span class="sxs-lookup"><span data-stu-id="f2ff2-138">Replicate Schema Changes</span></span>](publish/replicate-schema-changes.md)    
-   [<span data-ttu-id="f2ff2-139">管理識別資料行</span><span class="sxs-lookup"><span data-stu-id="f2ff2-139">Manage Identity Columns</span></span>](publish/manage-identity-columns.md)   
-   [<span data-ttu-id="f2ff2-140">設定合併式發行集的相容性層級</span><span class="sxs-lookup"><span data-stu-id="f2ff2-140">Set the Compatibility Level for Merge Publications</span></span>](publish/set-the-compatibility-level-for-merge-publications.md)  
  
### <a name="snapshot-options"></a><span data-ttu-id="f2ff2-141">快照集選項</span><span class="sxs-lookup"><span data-stu-id="f2ff2-141">Snapshot Options</span></span>  
  
-   [<span data-ttu-id="f2ff2-142">設定快照集屬性</span><span class="sxs-lookup"><span data-stu-id="f2ff2-142">Configure Snapshot Properties</span></span>](publish/configure-snapshot-properties-replication-transact-sql-programming.md)    
-   [<span data-ttu-id="f2ff2-143">透過 FTP 傳遞快照集</span><span class="sxs-lookup"><span data-stu-id="f2ff2-143">Deliver a Snapshot Through FTP</span></span>](publish/deliver-a-snapshot-through-ftp.md) 
  
### <a name="filter-data"></a><span data-ttu-id="f2ff2-144">篩選資料</span><span class="sxs-lookup"><span data-stu-id="f2ff2-144">Filter Data</span></span>  
  
-   [<span data-ttu-id="f2ff2-145">定義及修改資料行篩選</span><span class="sxs-lookup"><span data-stu-id="f2ff2-145">Define and Modify a Column Filter</span></span>](publish/define-and-modify-a-column-filter.md)    
-   [<span data-ttu-id="f2ff2-146">定義及修改靜態資料列篩選</span><span class="sxs-lookup"><span data-stu-id="f2ff2-146">Define and Modify a Static Row Filter</span></span>](publish/define-and-modify-a-static-row-filter.md)    
-   [<span data-ttu-id="f2ff2-147">針對合併發行項定義及修改參數化資料列篩選</span><span class="sxs-lookup"><span data-stu-id="f2ff2-147">Define and Modify a Parameterized Row Filter for a Merge Article</span></span>](publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)    
-   [<span data-ttu-id="f2ff2-148">最佳化參數化資料列篩選</span><span class="sxs-lookup"><span data-stu-id="f2ff2-148">Optimize Parameterized Row Filters</span></span>](publish/optimize-parameterized-row-filters.md)    
-   [<span data-ttu-id="f2ff2-149">定義和修改合併發行項之間的聯結篩選</span><span class="sxs-lookup"><span data-stu-id="f2ff2-149">Define and Modify a Join Filter Between Merge Articles</span></span>](publish/define-and-modify-a-join-filter-between-merge-articles.md)  
  
### <a name="transactional-replication-options"></a><span data-ttu-id="f2ff2-150">異動複寫選項</span><span class="sxs-lookup"><span data-stu-id="f2ff2-150">Transactional Replication Options</span></span>  
  
-   [<span data-ttu-id="f2ff2-151">設定對交易式發行項之資料變更的傳播方法</span><span class="sxs-lookup"><span data-stu-id="f2ff2-151">Set the Propagation Method for Data Changes to Transactional Articles</span></span>](publish/set-the-propagation-method-for-data-changes-to-transactional-articles.md)    
-   [<span data-ttu-id="f2ff2-152">啟用交易式發行集的更新訂閱</span><span class="sxs-lookup"><span data-stu-id="f2ff2-152">Enable Updating Subscriptions for Transactional Publications</span></span>](publish/enable-updating-subscriptions-for-transactional-publications.md)  
  
### <a name="merge-replication-options"></a><span data-ttu-id="f2ff2-153">合併式複寫選項</span><span class="sxs-lookup"><span data-stu-id="f2ff2-153">Merge Replication Options</span></span>  
  
-   [<span data-ttu-id="f2ff2-154">定義合併資料表發行項之間的邏輯記錄關聯性</span><span class="sxs-lookup"><span data-stu-id="f2ff2-154">Define a Logical Record Relationship Between Merge Table Articles</span></span>](publish/define-a-logical-record-relationship-between-merge-table-articles.md)    
-   [<span data-ttu-id="f2ff2-155">指定合併式複寫屬性</span><span class="sxs-lookup"><span data-stu-id="f2ff2-155">Specify Merge replication properties</span></span>](publish/specify-merge-replication-properties.md)    
-   [<span data-ttu-id="f2ff2-156">指定合併發行項解析程式</span><span class="sxs-lookup"><span data-stu-id="f2ff2-156">Specify a Merge Article Resolver</span></span>](publish/specify-a-merge-article-resolver.md)    

  
## <a name="manage-subscriptions"></a><span data-ttu-id="f2ff2-157">管理訂閱</span><span class="sxs-lookup"><span data-stu-id="f2ff2-157">Manage Subscriptions</span></span>  
  
-   [<span data-ttu-id="f2ff2-158">建立提取訂閱</span><span class="sxs-lookup"><span data-stu-id="f2ff2-158">Create a Pull Subscription</span></span>](create-a-pull-subscription.md)    
-   [<span data-ttu-id="f2ff2-159">檢視及修改提取訂閱屬性</span><span class="sxs-lookup"><span data-stu-id="f2ff2-159">View and Modify Pull Subscription Properties</span></span>](view-and-modify-pull-subscription-properties.md)    
-   [<span data-ttu-id="f2ff2-160">刪除提取訂閱</span><span class="sxs-lookup"><span data-stu-id="f2ff2-160">Delete a Pull Subscription</span></span>](delete-a-pull-subscription.md)    
-   [<span data-ttu-id="f2ff2-161">建立發送訂閱</span><span class="sxs-lookup"><span data-stu-id="f2ff2-161">Create a Push Subscription</span></span>](create-a-push-subscription.md)   
-   [<span data-ttu-id="f2ff2-162">檢視及修改發送訂閱屬性</span><span class="sxs-lookup"><span data-stu-id="f2ff2-162">View and Modify Push Subscription Properties</span></span>](view-and-modify-push-subscription-properties.md)   
-   [<span data-ttu-id="f2ff2-163">刪除發送訂閱</span><span class="sxs-lookup"><span data-stu-id="f2ff2-163">Delete a Push Subscription</span></span>](delete-a-push-subscription.md)   
-   [<span data-ttu-id="f2ff2-164">指定同步處理排程</span><span class="sxs-lookup"><span data-stu-id="f2ff2-164">Specify Synchronization Schedules</span></span>](specify-synchronization-schedules.md)    
-   [<span data-ttu-id="f2ff2-165">建立交易式發行集的可更新訂閱</span><span class="sxs-lookup"><span data-stu-id="f2ff2-165">Create an Updatable Subscription to a Transactional Publication</span></span>](publish/create-an-updatable-subscription-to-a-transactional-publication.md)  
-   [<span data-ttu-id="f2ff2-166">為非 SQL Server 訂閱者建立訂閱</span><span class="sxs-lookup"><span data-stu-id="f2ff2-166">Create a Subscription for a Non-SQL Server Subscriber</span></span>](create-a-subscription-for-a-non-sql-server-subscriber.md)  
  
## <a name="synchronize-subscriptions"></a><span data-ttu-id="f2ff2-167">同步處理訂閱</span><span class="sxs-lookup"><span data-stu-id="f2ff2-167">Synchronize Subscriptions</span></span>  
  
-   [<span data-ttu-id="f2ff2-168">建立和套用初始快照集</span><span class="sxs-lookup"><span data-stu-id="f2ff2-168">Create and Apply the Initial Snapshot</span></span>](create-and-apply-the-initial-snapshot.md)   
-   [<span data-ttu-id="f2ff2-169">使用參數化篩選建立合併式發行集的快照集</span><span class="sxs-lookup"><span data-stu-id="f2ff2-169">Create a Snapshot for a Merge Publication with Parameterized Filters</span></span>](create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)    
-   [<span data-ttu-id="f2ff2-170">從備份初始化交易式訂閱</span><span class="sxs-lookup"><span data-stu-id="f2ff2-170">Initialize a Transactional Subscription from a Backup</span></span>](initialize-a-transactional-subscription-from-a-backup.md)    
-   [<span data-ttu-id="f2ff2-171">手動初始化訂閱</span><span class="sxs-lookup"><span data-stu-id="f2ff2-171">Initialize a Subscription Manually</span></span>](initialize-a-subscription-manually.md)    
-   [<span data-ttu-id="f2ff2-172">同步處理提取訂閱</span><span class="sxs-lookup"><span data-stu-id="f2ff2-172">Synchronize a Pull Subscription</span></span>](synchronize-a-pull-subscription.md)    
-   [<span data-ttu-id="f2ff2-173">同步處理發送訂閱</span><span class="sxs-lookup"><span data-stu-id="f2ff2-173">Synchronize a Push Subscription</span></span>](synchronize-a-push-subscription.md)   
-   [<span data-ttu-id="f2ff2-174">重新初始化訂閱</span><span class="sxs-lookup"><span data-stu-id="f2ff2-174">Reinitialize a Subscription</span></span>](reinitialize-a-subscription.md)    
-   [<span data-ttu-id="f2ff2-175">在同步處理期間執行指令碼</span><span class="sxs-lookup"><span data-stu-id="f2ff2-175">Execute Scripts During Synchronization</span></span>](execute-scripts-during-synchronization-replication-transact-sql-programming.md)    
-   [<span data-ttu-id="f2ff2-176">為合併發行項實作商務邏輯處理常式</span><span class="sxs-lookup"><span data-stu-id="f2ff2-176">Implement a Business Logic Handler for a Merge Article</span></span>](implement-a-business-logic-handler-for-a-merge-article.md)  
-   [<span data-ttu-id="f2ff2-177">偵錯商務邏輯處理常式 &#40;複寫程式設計&#41;</span><span class="sxs-lookup"><span data-stu-id="f2ff2-177">Debug a Business Logic Handler &#40;Replication Programming&#41;</span></span>](debug-a-business-logic-handler-replication-programming.md)    
-   [<span data-ttu-id="f2ff2-178">在同步處理期間控制觸發程式和條件約束的行為</span><span class="sxs-lookup"><span data-stu-id="f2ff2-178">Control the Behavior of Triggers and Constraints During Synchronization</span></span>](control-behavior-of-triggers-and-constraints-in-synchronization.md)    
-   [<span data-ttu-id="f2ff2-179">為合併發行項實作自訂衝突解析程式</span><span class="sxs-lookup"><span data-stu-id="f2ff2-179">Implement a Custom Conflict Resolver for a Merge Article</span></span>](implement-a-custom-conflict-resolver-for-a-merge-article.md)  
  
## <a name="administeration"></a><span data-ttu-id="f2ff2-180">Administeration</span><span class="sxs-lookup"><span data-stu-id="f2ff2-180">Administeration</span></span> 
  
-   [<span data-ttu-id="f2ff2-181">處理複寫代理程式設定檔</span><span class="sxs-lookup"><span data-stu-id="f2ff2-181">Work with Replication Agent Profiles</span></span>](agents/work-with-replication-agent-profiles.md)   
-   [<span data-ttu-id="f2ff2-182">驗證訂閱者端的資料</span><span class="sxs-lookup"><span data-stu-id="f2ff2-182">Validate Data at the Subscriber</span></span>](validate-data-at-the-subscriber.md)    
-   [<span data-ttu-id="f2ff2-183">使用參數化篩選管理合併式發行集的資料分割</span><span class="sxs-lookup"><span data-stu-id="f2ff2-183">Manage Partitions for a Merge Publication with Parameterized Filters</span></span>](publish/manage-partitions-for-a-merge-publication-with-parameterized-filters.md)    
-   [<span data-ttu-id="f2ff2-184">將資料大量載入合併式發行集中的資料表</span><span class="sxs-lookup"><span data-stu-id="f2ff2-184">Bulk-Load Data into Tables in a Merge Publication</span></span>](bulk-load-data-into-tables-in-a-merge-publication.md)    
-   [<span data-ttu-id="f2ff2-185">清除合併中繼資料</span><span class="sxs-lookup"><span data-stu-id="f2ff2-185">Clean Up Merge Metadata</span></span>](administration/clean-up-merge-metadata-replication-transact-sql-programming.md)    
-   [<span data-ttu-id="f2ff2-186">執行合併發行項的虛擬更新</span><span class="sxs-lookup"><span data-stu-id="f2ff2-186">Perform a Dummy Update for a Merge Article</span></span>](administration/perform-a-dummy-update-for-a-merge-article-replication-transact-sql-programming.md)    
-   [<span data-ttu-id="f2ff2-187">在散發資料庫中查看複寫的命令和其他資訊</span><span class="sxs-lookup"><span data-stu-id="f2ff2-187">View Replicated Commands and Other Information in the Distribution Database</span></span>](monitor/view-replicated-commands-and-information-in-distribution-database.md)    
-   [<span data-ttu-id="f2ff2-188">為異動複寫啟用協調備份</span><span class="sxs-lookup"><span data-stu-id="f2ff2-188">Enable Coordinated Backups for Transactional Replication</span></span>](administration/enable-coordinated-backups-for-transactional-replication.md)   
-   [<span data-ttu-id="f2ff2-189">管理點對點拓撲</span><span class="sxs-lookup"><span data-stu-id="f2ff2-189">Administer a Peer-to-Peer Topology</span></span>](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)    
-   [<span data-ttu-id="f2ff2-190">停止複寫拓撲</span><span class="sxs-lookup"><span data-stu-id="f2ff2-190">Quiesce a Replication Topology</span></span>](administration/quiesce-a-replication-topology-replication-transact-sql-programming.md)    
-   [<span data-ttu-id="f2ff2-191">設定 Oracle 發行者的交易集作業</span><span class="sxs-lookup"><span data-stu-id="f2ff2-191">Configure the Transaction Set Job for an Oracle Publisher</span></span>](administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)   
-   [<span data-ttu-id="f2ff2-192">升級複寫腳本</span><span class="sxs-lookup"><span data-stu-id="f2ff2-192">Upgrade Replication Scripts</span></span>](administration/upgrade-replication-scripts-replication-transact-sql-programming.md)  
  
## <a name="monitor"></a><span data-ttu-id="f2ff2-193">監視</span><span class="sxs-lookup"><span data-stu-id="f2ff2-193">Monitor</span></span>
  
-   [<span data-ttu-id="f2ff2-194">允許非管理員使用複寫監視器</span><span class="sxs-lookup"><span data-stu-id="f2ff2-194">Allow Non-Administrators to Use Replication Monitor</span></span>](monitor/allow-non-administrators-to-use-replication-monitor.md)    
-   [<span data-ttu-id="f2ff2-195">以程式設計方式監視複寫</span><span class="sxs-lookup"><span data-stu-id="f2ff2-195">Programmatically Monitor Replication</span></span>](monitor/programmatically-monitor-replication.md)    
-   [<span data-ttu-id="f2ff2-196">在散發資料庫中查看複寫的命令和其他資訊</span><span class="sxs-lookup"><span data-stu-id="f2ff2-196">View Replicated Commands and Other Information in the Distribution Database</span></span>](monitor/view-replicated-commands-and-information-in-distribution-database.md)    
-   [<span data-ttu-id="f2ff2-197">檢視合併式發行集的衝突資訊</span><span class="sxs-lookup"><span data-stu-id="f2ff2-197">View Conflict Information for Merge Publications</span></span>](view-conflict-information-for-merge-publications.md) 
-   [<span data-ttu-id="f2ff2-198">針對異動複寫測量延遲及驗證連接</span><span class="sxs-lookup"><span data-stu-id="f2ff2-198">Measure Latency and Validate Connections for Transactional Replication</span></span>](monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  