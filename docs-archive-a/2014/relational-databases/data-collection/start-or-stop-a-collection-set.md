---
title: 啟動或停止收集組 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- collection sets [SQL Server], stopping
- collection sets [SQL Server], starting
ms.assetid: 48a7b2fe-6bc3-4278-a7ec-1babc1290345
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e37d4b2edcd7a6e048c405b072bcbf9b1fef78c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599022"
---
# <a name="start-or-stop-a-collection-set"></a><span data-ttu-id="cafc1-102">啟動或停止收集組</span><span class="sxs-lookup"><span data-stu-id="cafc1-102">Start or Stop a Collection Set</span></span>
  <span data-ttu-id="cafc1-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中啟動或停止收集組。</span><span class="sxs-lookup"><span data-stu-id="cafc1-103">This topic describes how to start or stop a collection set in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="cafc1-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="cafc1-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="cafc1-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="cafc1-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="cafc1-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="cafc1-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="cafc1-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="cafc1-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="cafc1-108">建議</span><span class="sxs-lookup"><span data-stu-id="cafc1-108">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="cafc1-109">安全性</span><span class="sxs-lookup"><span data-stu-id="cafc1-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="cafc1-110">**若要使用下列項目啟動或停止收集組：**</span><span class="sxs-lookup"><span data-stu-id="cafc1-110">**To start or stop a collection set, using:**</span></span>  
  
     [<span data-ttu-id="cafc1-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cafc1-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="cafc1-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cafc1-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="cafc1-113">開始之前</span><span class="sxs-lookup"><span data-stu-id="cafc1-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="cafc1-114">限制事項</span><span class="sxs-lookup"><span data-stu-id="cafc1-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="cafc1-115">資料收集器預存程序和目錄檢視儲存在 **msdb** 資料庫。</span><span class="sxs-lookup"><span data-stu-id="cafc1-115">Data Collector stored procedures and catalog views are stored in the **msdb** database.</span></span>  
  
-   <span data-ttu-id="cafc1-116">不同於一般預存程序，資料收集器預存程序的參數會具備嚴格的類型，而且不支援資料類型的自動轉換。</span><span class="sxs-lookup"><span data-stu-id="cafc1-116">Unlike regular stored procedures, the parameters for data collector stored procedures are strictly typed and do not support automatic data type conversion.</span></span> <span data-ttu-id="cafc1-117">如果沒有依照引數描述所指定，以正確的輸入參數資料類型來呼叫這些參數，預存程序會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="cafc1-117">If these parameters are not called with the correct input parameter data types, as specified in the argument description, the stored procedure returns an error.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="cafc1-118">必要條件</span><span class="sxs-lookup"><span data-stu-id="cafc1-118">Prerequisites</span></span>  
  
-   <span data-ttu-id="cafc1-119">SQL Server Agent 必須已啟動。</span><span class="sxs-lookup"><span data-stu-id="cafc1-119">SQL Server Agent must be started.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="cafc1-120">建議</span><span class="sxs-lookup"><span data-stu-id="cafc1-120">Recommendations</span></span>  
  
-   <span data-ttu-id="cafc1-121">若要取得收集組的相關資訊，請查詢 [syscollector_collection_sets](/sql/relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql) 目錄檢視。</span><span class="sxs-lookup"><span data-stu-id="cafc1-121">To obtain information about collection sets, query the [syscollector_collection_sets](/sql/relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql) catalog view.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="cafc1-122">Security</span><span class="sxs-lookup"><span data-stu-id="cafc1-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="cafc1-123">權限</span><span class="sxs-lookup"><span data-stu-id="cafc1-123">Permissions</span></span>  
 <span data-ttu-id="cafc1-124">需要 **dc_operator** 固定資料庫角色中的成員資格。</span><span class="sxs-lookup"><span data-stu-id="cafc1-124">Requires membership in the **dc_operator** fixed database role.</span></span> <span data-ttu-id="cafc1-125">如果收集組沒有 Proxy 帳戶，就需要 **系統管理員 (sysadmin)** 固定伺服器角色中的成員資格。</span><span class="sxs-lookup"><span data-stu-id="cafc1-125">If the collection set does not have a proxy account, membership in the **sysadmin** fixed server role is required.Examples</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="cafc1-126">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="cafc1-126">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-start-a-collection-set"></a><span data-ttu-id="cafc1-127">若要啟動收集組</span><span class="sxs-lookup"><span data-stu-id="cafc1-127">To start a collection set</span></span>  
  
1.  <span data-ttu-id="cafc1-128">在 [物件總管] 中，依序展開 **[管理]** 節點、 **[資料收集]** 和 **[系統資料收集組]** 。</span><span class="sxs-lookup"><span data-stu-id="cafc1-128">In Object Explorer, expand the **Management** node, expand **Data Collection**, and then expand **System Data Collection Sets**.</span></span>  
  
2.  <span data-ttu-id="cafc1-129">以滑鼠右鍵按一下您要啟動的收集組，然後按一下 [啟動資料收集組]  。</span><span class="sxs-lookup"><span data-stu-id="cafc1-129">Right-click the collection set that you want to start, and then click **Start Data Collection Set**.</span></span>  
  
     <span data-ttu-id="cafc1-130">訊息方塊會顯示此動作的結果，而此收集組圖示上的綠色箭頭會指示此收集組已經啟動。</span><span class="sxs-lookup"><span data-stu-id="cafc1-130">A message box displays the results of this action, and a green arrow on the icon for the collection set indicates that the collection set has started.</span></span>  
  
#### <a name="to-stop-a-collection-set"></a><span data-ttu-id="cafc1-131">若要停止收集組</span><span class="sxs-lookup"><span data-stu-id="cafc1-131">To stop a collection set</span></span>  
  
1.  <span data-ttu-id="cafc1-132">在 [物件總管] 中，依序展開 **[管理]** 節點、 **[資料收集]** 和 **[系統資料收集組]** 。</span><span class="sxs-lookup"><span data-stu-id="cafc1-132">In Object Explorer, expand the **Management** node, expand **Data Collection**, and then expand **System Data Collection Sets**.</span></span>  
  
2.  <span data-ttu-id="cafc1-133">以滑鼠右鍵按一下您要停止的收集組，然後按一下 **[停止資料收集組]** 。</span><span class="sxs-lookup"><span data-stu-id="cafc1-133">Right-click the collection set that you want to stop, and then click **Stop Data Collection Set**.</span></span>  
  
     <span data-ttu-id="cafc1-134">訊息方塊會顯示此動作的結果，而此收集組圖示上的紅色圓圈會指示此收集組已經停止。</span><span class="sxs-lookup"><span data-stu-id="cafc1-134">A message box displays the results of this action, and a red circle on the icon for the collection set indicates that the collection set has stopped.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="cafc1-135">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cafc1-135">Using Transact-SQL</span></span>  
  
#### <a name="to-start-a-collection-set"></a><span data-ttu-id="cafc1-136">若要啟動收集組</span><span class="sxs-lookup"><span data-stu-id="cafc1-136">To start a collection set</span></span>  
  
1.  <span data-ttu-id="cafc1-137">連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cafc1-137">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="cafc1-138">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="cafc1-138">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="cafc1-139">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="cafc1-139">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="cafc1-140">此範例使用 [sp_syscollector_start_collection_set](/sql/relational-databases/system-stored-procedures/sp-syscollector-start-collection-set-transact-sql) 啟動識別碼為 `1`的收集組。</span><span class="sxs-lookup"><span data-stu-id="cafc1-140">This example uses [sp_syscollector_start_collection_set](/sql/relational-databases/system-stored-procedures/sp-syscollector-start-collection-set-transact-sql) to start the collection set that has the ID of `1`.</span></span>  
  
```sql  
USE msdb;  
GO  
EXEC sp_syscollector_start_collection_set @collection_set_id = 1;  
```  
  
#### <a name="to-stop-a-collection-set"></a><span data-ttu-id="cafc1-141">若要停止收集組</span><span class="sxs-lookup"><span data-stu-id="cafc1-141">To stop a collection set</span></span>  
  
1.  <span data-ttu-id="cafc1-142">連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cafc1-142">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="cafc1-143">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="cafc1-143">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="cafc1-144">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="cafc1-144">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="cafc1-145">此範例使用 [sp_syscollector_stop_collection_set](/sql/relational-databases/system-stored-procedures/sp-syscollector-stop-collection-set-transact-sql) 停止識別碼為 `1`的收集組。</span><span class="sxs-lookup"><span data-stu-id="cafc1-145">This example uses [sp_syscollector_stop_collection_set](/sql/relational-databases/system-stored-procedures/sp-syscollector-stop-collection-set-transact-sql) to stop the collection set that has the ID of `1`.</span></span>  
  
```sql  
USE msdb;  
GO  
EXEC sp_syscollector_stop_collection_set @collection_set_id = 1;  
```  
  
## <a name="see-also"></a><span data-ttu-id="cafc1-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cafc1-146">See Also</span></span>  
 <span data-ttu-id="cafc1-147">[資料收集器檢視 &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/data-collector-views-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cafc1-147">[Data Collector Views &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/data-collector-views-transact-sql) </span></span>  
 <span data-ttu-id="cafc1-148">[[資料收集]](data-collection.md)</span><span class="sxs-lookup"><span data-stu-id="cafc1-148">[Data Collection](data-collection.md)</span></span>  
  
  
