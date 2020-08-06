---
title: SQL Server 的 User Settable 物件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- User Settable object
- SQLServer:User Settable
ms.assetid: 633de3ef-533c-4f0c-9c7b-c105129d8e94
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7243ab4767c8de93dccf4556f136a94b47554d3d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687793"
---
# <a name="sql-server-user-settable-object"></a><span data-ttu-id="6cf11-102">SQL Server 的 User Settable 物件</span><span class="sxs-lookup"><span data-stu-id="6cf11-102">SQL Server, User Settable Object</span></span>
  <span data-ttu-id="6cf11-103">Microsoft **的** User Settable [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 物件可讓您建立自訂的計數器執行個體。</span><span class="sxs-lookup"><span data-stu-id="6cf11-103">The **User Settable** object in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] allows you to create custom counter instances.</span></span> <span data-ttu-id="6cf11-104">使用自訂計數器執行個體來監視現有計數器未監視的伺服器層面，例如您的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫獨有的元件 (例如，記錄的客戶訂單數或產品庫存數)。</span><span class="sxs-lookup"><span data-stu-id="6cf11-104">Use custom counter instances to monitor aspects of the server not monitored by existing counters, such as components unique to your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database (for example, the number of customer orders logged or the product inventory).</span></span>  
  
 <span data-ttu-id="6cf11-105">**User Settable** 物件包含 10 個查詢計數器執行個體：**User counter 1** 至 **User counter 10**。</span><span class="sxs-lookup"><span data-stu-id="6cf11-105">The **User Settable** object contains 10 instances of the query counter: **User counter 1** through **User counter 10**.</span></span> <span data-ttu-id="6cf11-106">這些計數器分別對應至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sp_user_counter1 **到** sp_user_counter10 **的**預存程序。</span><span class="sxs-lookup"><span data-stu-id="6cf11-106">These counters map to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedures **sp_user_counter1** through **sp_user_counter10**.</span></span> <span data-ttu-id="6cf11-107">當使用者應用程式執行這些預存程序時，預存程序所設定的數值將顯示於「系統監視器」內。</span><span class="sxs-lookup"><span data-stu-id="6cf11-107">As these stored procedures are executed by user applications, the values set by the stored procedures are displayed in System Monitor.</span></span> <span data-ttu-id="6cf11-108">計數器可監視任何一個整數值，例如計算特定產品在某天內發生的訂單數的預存程序。</span><span class="sxs-lookup"><span data-stu-id="6cf11-108">A counter can monitor any single integer value (for example, a stored procedure that counts how many orders for a particular product have occurred in one day).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6cf11-109">「系統監視器」不會自動輪詢使用者計數器預存程序。</span><span class="sxs-lookup"><span data-stu-id="6cf11-109">The user counter stored procedures are not polled automatically by System Monitor.</span></span> <span data-ttu-id="6cf11-110">必須由使用者應用程式明確執行，才會更新計數器的值。</span><span class="sxs-lookup"><span data-stu-id="6cf11-110">They must be explicitly executed by a user application for the counter values to be updated.</span></span> <span data-ttu-id="6cf11-111">請利用觸發程序來自動更新計數器的值。</span><span class="sxs-lookup"><span data-stu-id="6cf11-111">Use a trigger to update the value of the counter automatically.</span></span> <span data-ttu-id="6cf11-112">例如，若要建立計數器來監視資料表的資料列數目，請在資料表建立 INSERT 和 DELETE 觸發程序來執行下列陳述式： `SELECT COUNT(*) FROM table`。</span><span class="sxs-lookup"><span data-stu-id="6cf11-112">For example, to create a counter that monitors the number of rows in a table, create an INSERT and DELETE trigger on the table that executes the following statement: `SELECT COUNT(*) FROM table`.</span></span> <span data-ttu-id="6cf11-113">每當資料表因 INSERT 或 DELETE 作業而引發觸發程序時，「系統監視器」計數器就會自動更新。</span><span class="sxs-lookup"><span data-stu-id="6cf11-113">Whenever the trigger is fired because of an INSERT or DELETE operation occurring on the table, the System Monitor counter is automatically updated.</span></span>  
  
 <span data-ttu-id="6cf11-114">下表描述 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **User Settable** 物件。</span><span class="sxs-lookup"><span data-stu-id="6cf11-114">This table describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **User Settable** object.</span></span>  
  
|<span data-ttu-id="6cf11-115">SQL Server User Settable 計數器</span><span class="sxs-lookup"><span data-stu-id="6cf11-115">SQL Server User Settable counters</span></span>|<span data-ttu-id="6cf11-116">描述</span><span class="sxs-lookup"><span data-stu-id="6cf11-116">Description</span></span>|  
|---------------------------------------|-----------------|  
|<span data-ttu-id="6cf11-117">**查詢**</span><span class="sxs-lookup"><span data-stu-id="6cf11-117">**Query**</span></span>|<span data-ttu-id="6cf11-118">**User Settable** 物件包含查詢計數器。</span><span class="sxs-lookup"><span data-stu-id="6cf11-118">The **User Settable** object contains the query counter.</span></span> <span data-ttu-id="6cf11-119">使用者可設定查詢物件內的 **User counter** 。</span><span class="sxs-lookup"><span data-stu-id="6cf11-119">Users configure the **User counters** within the query object.</span></span>|  
  
 <span data-ttu-id="6cf11-120">下表描述 **Query** 計數器的 **執行個體** 。</span><span class="sxs-lookup"><span data-stu-id="6cf11-120">This table describes the **instances** of the **Query** counter.</span></span>  
  
|<span data-ttu-id="6cf11-121">Query 計數器執行個體</span><span class="sxs-lookup"><span data-stu-id="6cf11-121">Query counter instances</span></span>|<span data-ttu-id="6cf11-122">描述</span><span class="sxs-lookup"><span data-stu-id="6cf11-122">Description</span></span>|  
|-----------------------------|-----------------|  
|<span data-ttu-id="6cf11-123">**User counter 1**</span><span class="sxs-lookup"><span data-stu-id="6cf11-123">**User counter 1**</span></span>|<span data-ttu-id="6cf11-124">使用 **sp_user_counter1**來定義。</span><span class="sxs-lookup"><span data-stu-id="6cf11-124">Defined using **sp_user_counter1**.</span></span>|  
|<span data-ttu-id="6cf11-125">**使用者計數器 2**</span><span class="sxs-lookup"><span data-stu-id="6cf11-125">**User counter 2**</span></span>|<span data-ttu-id="6cf11-126">使用 **sp_user_counter2**來定義。</span><span class="sxs-lookup"><span data-stu-id="6cf11-126">Defined using **sp_user_counter2**.</span></span>|  
|<span data-ttu-id="6cf11-127">**使用者計數器 3**</span><span class="sxs-lookup"><span data-stu-id="6cf11-127">**User counter 3**</span></span>|<span data-ttu-id="6cf11-128">使用 **sp_user_counter3**來定義。</span><span class="sxs-lookup"><span data-stu-id="6cf11-128">Defined using **sp_user_counter3**.</span></span>|  
|<span data-ttu-id="6cf11-129">...</span><span class="sxs-lookup"><span data-stu-id="6cf11-129">...</span></span>||  
|<span data-ttu-id="6cf11-130">**User counter 10**</span><span class="sxs-lookup"><span data-stu-id="6cf11-130">**User counter 10**</span></span>|<span data-ttu-id="6cf11-131">使用 **sp_user_counter10**來定義。</span><span class="sxs-lookup"><span data-stu-id="6cf11-131">Defined using **sp_user_counter10**.</span></span>|  
  
 <span data-ttu-id="6cf11-132">若要使用使用者計數器預存程序，只要從您自己的應用程式執行它們，並且以一個整數參數代表計數器的新數值。</span><span class="sxs-lookup"><span data-stu-id="6cf11-132">To make use of the user counter stored procedures, execute them from your own application with a single integer parameter representing the new value for the counter.</span></span> <span data-ttu-id="6cf11-133">例如若要將 **User counter 1** 設成數值 10，可執行下列的 Transact-SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="6cf11-133">For example, to set **User counter 1** to the value 10, execute this Transact-SQL statement:</span></span>  
  
```  
EXECUTE sp_user_counter1 10  
```  
  
 <span data-ttu-id="6cf11-134">可呼叫使用者計數器預存程序的位置和呼叫其他預存程序的位置一樣，像是您自己的預存程序。</span><span class="sxs-lookup"><span data-stu-id="6cf11-134">The user counter stored procedures can be called from anywhere other stored procedures can be called, such as your own stored procedures.</span></span> <span data-ttu-id="6cf11-135">例如，您可以建立下列的預存程序，計算自從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體啟動之後的連接數和嘗試連接數。</span><span class="sxs-lookup"><span data-stu-id="6cf11-135">For example, you can create the following stored procedure to count the number of connections and attempted connections since an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] was started:</span></span>  
  
```  
DROP PROC My_Proc  
GO  
CREATE PROC My_Proc  
AS   
   EXECUTE sp_user_counter1 @@CONNECTIONS  
GO  
```  
  
 <span data-ttu-id="6cf11-136">@@CONNECTIONS 函式可傳回自從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體啟動之後的連接數或嘗試連接數。</span><span class="sxs-lookup"><span data-stu-id="6cf11-136">The @@CONNECTIONS function returns the number of connections or attempted connections since an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] started.</span></span> <span data-ttu-id="6cf11-137">此數值將傳至 **sp_user_counter1** 預存程序作為參數。</span><span class="sxs-lookup"><span data-stu-id="6cf11-137">This value is passed to the **sp_user_counter1** stored procedure as the parameter.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6cf11-138">盡量讓定義於使用者計數器預存程序的查詢越簡單越好。</span><span class="sxs-lookup"><span data-stu-id="6cf11-138">Make the queries defined in the user counter stored procedures as simple as possible.</span></span> <span data-ttu-id="6cf11-139">執行大量排序或雜湊作業的記憶體密集查詢，或是執行大量 I/O 的查詢，都需要很多資源才能執行，所以可能影響效能。</span><span class="sxs-lookup"><span data-stu-id="6cf11-139">Memory-intensive queries that perform substantial sort or hash operations or queries that perform large amounts of I/O are expensive to execute and can impact performance.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="6cf11-140">權限</span><span class="sxs-lookup"><span data-stu-id="6cf11-140">Permissions</span></span>  
 <span data-ttu-id="6cf11-141">**sp_user_counter** 適用於所有使用者，但可以由任何查詢計數器來限制。</span><span class="sxs-lookup"><span data-stu-id="6cf11-141">**sp_user_counter** is available for all users but can be restricted for any query counter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cf11-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6cf11-142">See Also</span></span>  
 [<span data-ttu-id="6cf11-143">監視資源使用狀況 &#40;System Monitor&#41;</span><span class="sxs-lookup"><span data-stu-id="6cf11-143">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
