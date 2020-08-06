---
title: 在合併同步處理期間執行商務邏輯 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- custom error resolution [SQL Server replication]
- custom change handling [SQL Server replication]
- errors [SQL Server replication], business logic handlers
- merge replication business logic handlers [SQL Server replication]
- conflict resolution [SQL Server replication], merge replication
- business logic handlers [SQL Server replication]
ms.assetid: 9d4da2ef-c17f-4a31-a1f6-5c3b7ca85f71
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1e082cbbb46ceae712cd39925c28fe89988a3793
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584450"
---
# <a name="execute-business-logic-during-merge-synchronization"></a><span data-ttu-id="ed721-102">在合併同步處理期間執行商務邏輯</span><span class="sxs-lookup"><span data-stu-id="ed721-102">Execute Business Logic During Merge Synchronization</span></span>
  <span data-ttu-id="ed721-103">商務邏輯處理常式架構允許您撰寫在合併同步處理過程中呼叫的 Managed 程式碼組件。</span><span class="sxs-lookup"><span data-stu-id="ed721-103">The business logic handler framework allows you to write a managed code assembly that is called during the merge synchronization process.</span></span> <span data-ttu-id="ed721-104">組件包括可對應至幾種同步處理條件的商務邏輯：資料變更、衝突和錯誤。</span><span class="sxs-lookup"><span data-stu-id="ed721-104">The assembly includes business logic that can respond to a number of conditions during synchronization: data changes, conflicts, and errors.</span></span> <span data-ttu-id="ed721-105">商務邏輯處理常式架構提供了簡單的程式設計模型，且合併處理為您組件提供的資料是 ADO.NET 資料集的形式，因此您可以利用 ADO.NET 知識而無需了解專屬介面。</span><span class="sxs-lookup"><span data-stu-id="ed721-105">The business logic handler framework provides a simple programming model, and the data that the merge process provides to your assembly is in the form of an ADO.NET data set, so you can leverage knowledge of ADO.NET rather than learning a proprietary interface.</span></span> <span data-ttu-id="ed721-106">如需程式設計商務邏輯處理常式的詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="ed721-106">For more information on programming business logic handlers, see:</span></span>  
  
-   <span data-ttu-id="ed721-107">應用程式開發介面 (API) 參考： <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport></span><span class="sxs-lookup"><span data-stu-id="ed721-107">The application programming interface (API) reference: <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport></span></span>  
  
-   <span data-ttu-id="ed721-108">如何實作商務邏輯處理常式的指示：[為合併發行項實作商務邏輯處理常式](../implement-a-business-logic-handler-for-a-merge-article.md)</span><span class="sxs-lookup"><span data-stu-id="ed721-108">Instructions on how to implement a business logic handler: [Implement a Business Logic Handler for a Merge Article](../implement-a-business-logic-handler-for-a-merge-article.md)</span></span>  
  
## <a name="uses-for-business-logic-handlers"></a><span data-ttu-id="ed721-109">商務邏輯處理常式的使用</span><span class="sxs-lookup"><span data-stu-id="ed721-109">Uses for Business Logic Handlers</span></span>  
 <span data-ttu-id="ed721-110">合併同步處理可以叫用商務邏輯處理常式以執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="ed721-110">The merge synchronization process can invoke business logic handlers to perform:</span></span>  
  
-   <span data-ttu-id="ed721-111">自訂變更處理</span><span class="sxs-lookup"><span data-stu-id="ed721-111">Custom change handling</span></span>  
  
-   <span data-ttu-id="ed721-112">自訂衝突解決方案</span><span class="sxs-lookup"><span data-stu-id="ed721-112">Custom conflict resolution</span></span>  
  
-   <span data-ttu-id="ed721-113">自訂錯誤解決方案</span><span class="sxs-lookup"><span data-stu-id="ed721-113">Custom error resolution</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ed721-114">指定的商務邏輯處理常式會針對要同步處理的每一個資料列執行。</span><span class="sxs-lookup"><span data-stu-id="ed721-114">The business logic handler you specify is executed for every row that is synchronized.</span></span> <span data-ttu-id="ed721-115">對其他應用程式或網路服務的複雜邏輯與呼叫可能會影響效能。</span><span class="sxs-lookup"><span data-stu-id="ed721-115">Complex logic and calls to other applications or network services can impact performance.</span></span>  
  
### <a name="custom-change-handling"></a><span data-ttu-id="ed721-116">自訂變更處理</span><span class="sxs-lookup"><span data-stu-id="ed721-116">Custom Change Handling</span></span>  
 <span data-ttu-id="ed721-117">商務邏輯處理常式可以在處理相互不衝突的資料變更期間叫用，並可執行下列三個動作之一：</span><span class="sxs-lookup"><span data-stu-id="ed721-117">The business logic handler can be invoked during the processing of non-conflicting data changes and can perform one of three actions:</span></span>  
  
-   <span data-ttu-id="ed721-118">拒絕資料</span><span class="sxs-lookup"><span data-stu-id="ed721-118">Reject the data</span></span>  
  
     <span data-ttu-id="ed721-119">這對不想與給定「訂閱者」進行變更傳播的應用程式非常有用。</span><span class="sxs-lookup"><span data-stu-id="ed721-119">This is useful for applications that do not want changes propagated to or from a given Subscriber.</span></span> <span data-ttu-id="ed721-120">例如，管理員可以篩選出不屬於「訂閱者」資料分割的插入，或拒絕在「訂閱者」端執行的刪除。</span><span class="sxs-lookup"><span data-stu-id="ed721-120">For example, an administrator could filter out inserts that do not belong in the Subscriber's partition, or possibly reject deletes performed at a Subscriber.</span></span> <span data-ttu-id="ed721-121">另一個範例是，當庫存無法再使用時，應用程式可以拒絕在「訂閱者」端輸入的訂單。</span><span class="sxs-lookup"><span data-stu-id="ed721-121">As another example, an application could reject an order entered at a Subscriber because the inventory is no longer available.</span></span>  
  
-   <span data-ttu-id="ed721-122">接受資料</span><span class="sxs-lookup"><span data-stu-id="ed721-122">Accept the data</span></span>  
  
     <span data-ttu-id="ed721-123">這對於在允許對「發行者」或「訂閱者」端所作的資料變更進行傳播之前，必須檢閱這些變更的應用程式非常有用。</span><span class="sxs-lookup"><span data-stu-id="ed721-123">This is useful for applications in which it is necessary to review data changes made at either the Publisher or Subscriber before allowing them to be propagated.</span></span> <span data-ttu-id="ed721-124">例如，中層應用程式可以檢查來自現場的新訂單，並與中層採購工作流程處理整合在一起。</span><span class="sxs-lookup"><span data-stu-id="ed721-124">For example, a mid-tier application could examine new orders coming in from the field and integrate with a procurement workflow process in the mid-tier.</span></span>  
  
-   <span data-ttu-id="ed721-125">套用自訂資料</span><span class="sxs-lookup"><span data-stu-id="ed721-125">Apply custom data</span></span>  
  
     <span data-ttu-id="ed721-126">這對於需要覆寫特定資料值或作業的應用程式非常有用。</span><span class="sxs-lookup"><span data-stu-id="ed721-126">This is useful for applications that need to override specific data values or operations.</span></span> <span data-ttu-id="ed721-127">例如，應用程式可以將資料列刪除轉換至資料列之 **status** 資料行設定為「已刪除」值的特殊更新，然後追蹤執行刪除的用戶端識別。</span><span class="sxs-lookup"><span data-stu-id="ed721-127">For example, an application could transform a row delete into a special update that sets a **status** column in the row to a value of "deleted" and then tracks the identity of the client performing the delete.</span></span> <span data-ttu-id="ed721-128">可用於稽核或工作流程。</span><span class="sxs-lookup"><span data-stu-id="ed721-128">This might be useful for auditing or workflow purposes.</span></span>  
  
### <a name="custom-conflict-resolution"></a><span data-ttu-id="ed721-129">自訂衝突解決方案</span><span class="sxs-lookup"><span data-stu-id="ed721-129">Custom Conflict Resolution</span></span>  
 <span data-ttu-id="ed721-130">合併式複寫提供了衝突偵測和解決，可讓您接受預設解決策略或選取自訂的衝突解決方案。</span><span class="sxs-lookup"><span data-stu-id="ed721-130">Merge replication provides conflict detection and resolution, allowing you to accept a default resolution strategy or choose custom resolution for conflicts.</span></span> <span data-ttu-id="ed721-131">如需詳細資訊，請參閱 [進階合併式複寫衝突偵測與解決](advanced-merge-replication-conflict-detection-and-resolution.md)。</span><span class="sxs-lookup"><span data-stu-id="ed721-131">For more information, see [Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md).</span></span> <span data-ttu-id="ed721-132">商務邏輯處理常式可以在處理衝突的資料變更期間叫用，並可執行下列兩個動作之一：</span><span class="sxs-lookup"><span data-stu-id="ed721-132">The business logic handler can be invoked during the processing of conflicting data changes and can perform one of two actions:</span></span>  
  
-   <span data-ttu-id="ed721-133">接受預設解決方案</span><span class="sxs-lookup"><span data-stu-id="ed721-133">Accept default resolution</span></span>  
  
     <span data-ttu-id="ed721-134">這對於可能需要檢閱衝突、執行其他動作以及記錄自訂衝突記錄檔訊息的應用程式非常有用。</span><span class="sxs-lookup"><span data-stu-id="ed721-134">This is useful for applications that might need to review the conflict, perform additional actions, and possibly log a custom conflict log message.</span></span>  
  
-   <span data-ttu-id="ed721-135">執行自訂解決方案</span><span class="sxs-lookup"><span data-stu-id="ed721-135">Perform custom resolution</span></span>  
  
     <span data-ttu-id="ed721-136">這適用於可能需要針對商務邏輯選取特定資料值，而且會在自訂資料集內提供同步處理流程的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ed721-136">This is useful for applications that might need to select data values that are specific to their business logic and supply the synchronization process with this custom dataset.</span></span> <span data-ttu-id="ed721-137">例如，應用程式可以透過將「發行者」和「訂閱者」資料集的值進行組合，提供新版的優先資料列。</span><span class="sxs-lookup"><span data-stu-id="ed721-137">For example, an application could provide a new version of the winning row by combining values from the Publisher and Subscriber data sets.</span></span>  
  
### <a name="custom-error-resolution"></a><span data-ttu-id="ed721-138">自訂錯誤解決方案</span><span class="sxs-lookup"><span data-stu-id="ed721-138">Custom Error Resolution</span></span>  
 <span data-ttu-id="ed721-139">在傳播產生錯誤的變更時可以叫用自訂邏輯。</span><span class="sxs-lookup"><span data-stu-id="ed721-139">Custom logic can be invoked during the propagation of changes that result in errors.</span></span> <span data-ttu-id="ed721-140">此邏輯可以執行下列兩個動作之一：</span><span class="sxs-lookup"><span data-stu-id="ed721-140">The logic can perform one of two actions:</span></span>  
  
-   <span data-ttu-id="ed721-141">接受預設錯誤解決方案</span><span class="sxs-lookup"><span data-stu-id="ed721-141">Accept default error resolution</span></span>  
  
     <span data-ttu-id="ed721-142">這對於可能需要檢閱錯誤、執行其他動作以及記錄自訂錯誤記錄檔訊息的應用程式非常有用。</span><span class="sxs-lookup"><span data-stu-id="ed721-142">This is useful for applications that might need to review the error and perform additional action and possibly log a custom error log message.</span></span>  
  
-   <span data-ttu-id="ed721-143">接受自訂錯誤解決方案</span><span class="sxs-lookup"><span data-stu-id="ed721-143">Accept custom error resolution</span></span>  
  
     <span data-ttu-id="ed721-144">這適用於可能需要針對商務邏輯選取特定資料值，而且會在自訂資料集內提供同步處理流程的應用程式。</span><span class="sxs-lookup"><span data-stu-id="ed721-144">This is useful for applications that might need to select data values that are specific to their business logic and supply the synchronization process with this custom dataset.</span></span> <span data-ttu-id="ed721-145">例如，當複寫處理遇到重複索引鍵違規時，商務邏輯處理常式可以提供新版的資料變更，其中的索引鍵將不再發生衝突。</span><span class="sxs-lookup"><span data-stu-id="ed721-145">For example, if the replication process encounters a duplicate key violation, the business logic handler could provide a new version of the data change in which the key will no longer conflict.</span></span> <span data-ttu-id="ed721-146">隨後在「發行者」與「訂閱者」端所作的變更仍將保存在資料庫中，且複寫處理不必以刪除來補償失敗的插入。</span><span class="sxs-lookup"><span data-stu-id="ed721-146">Changes made at the Publisher and Subscriber can then persist in the database, and the replication process doesn't have to compensate for the failed insert with a delete.</span></span>  
  
## <a name="deployment-scenarios-for-business-logic-handlers"></a><span data-ttu-id="ed721-147">商務邏輯處理常式的部署案例</span><span class="sxs-lookup"><span data-stu-id="ed721-147">Deployment Scenarios for Business Logic Handlers</span></span>  
 <span data-ttu-id="ed721-148">商務邏輯處理常式可以部署在：</span><span class="sxs-lookup"><span data-stu-id="ed721-148">Business logic handlers can be deployed at:</span></span>  
  
-   <span data-ttu-id="ed721-149">散發者。</span><span class="sxs-lookup"><span data-stu-id="ed721-149">The Distributor.</span></span> <span data-ttu-id="ed721-150">使用發送訂閱，以便在「散發者」端執行商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="ed721-150">Use a push subscription so that business logic is executed at the Distributor.</span></span>  
  
-   <span data-ttu-id="ed721-151">「訂閱者」端。</span><span class="sxs-lookup"><span data-stu-id="ed721-151">The Subscriber.</span></span> <span data-ttu-id="ed721-152">使用提取訂閱，以便在「訂閱者」端執行商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="ed721-152">Use a pull subscription so that business logic is executed at the Subscriber.</span></span>  
  
-   <span data-ttu-id="ed721-153">Internet Information Services (IIS) 伺服器，如果使用 Web 同步處理。</span><span class="sxs-lookup"><span data-stu-id="ed721-153">An Internet Information Services (IIS) server if Web synchronization is used.</span></span> <span data-ttu-id="ed721-154">使用與 Web 同步處理同步的提取訂閱，且商務邏輯處理常式將在 IIS Server 端執行。</span><span class="sxs-lookup"><span data-stu-id="ed721-154">Use a pull subscription synchronized with Web synchronization, and the business logic handler will execute at the IIS Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed721-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed721-155">See Also</span></span>  
 <span data-ttu-id="ed721-156">[合併式複寫](merge-replication.md) </span><span class="sxs-lookup"><span data-stu-id="ed721-156">[Merge Replication](merge-replication.md) </span></span>  
 <span data-ttu-id="ed721-157">[Subscribe to Publications](../subscribe-to-publications.md) </span><span class="sxs-lookup"><span data-stu-id="ed721-157">[Subscribe to Publications](../subscribe-to-publications.md) </span></span>  
 <span data-ttu-id="ed721-158">[同步處理資料](../synchronize-data.md) </span><span class="sxs-lookup"><span data-stu-id="ed721-158">[Synchronize Data](../synchronize-data.md) </span></span>  
 [<span data-ttu-id="ed721-159">合併式複寫的 Web 同步處理</span><span class="sxs-lookup"><span data-stu-id="ed721-159">Web Synchronization for Merge Replication</span></span>](../web-synchronization-for-merge-replication.md)  
  
  
