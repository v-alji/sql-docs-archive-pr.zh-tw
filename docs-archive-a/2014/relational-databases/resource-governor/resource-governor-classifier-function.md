---
title: 資源管理員分類函式 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, classifier function
- user-defined functions [SQL Server], classifier function
- classifier function [SQL Server]
- classifier function [SQL Server], overview
ms.assetid: 64c25012-7068-476f-afa2-0b4f3adde9a4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 69b6fd10ac0adc6f76925e0d41f110b917111466
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699388"
---
# <a name="resource-governor-classifier-function"></a><span data-ttu-id="36d5a-102">Resource Governor Classifier Function</span><span class="sxs-lookup"><span data-stu-id="36d5a-102">Resource Governor Classifier Function</span></span>
  <span data-ttu-id="36d5a-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資源管理員分類程序會根據內送工作階段的特性，將工作階段指派給工作負載群組。</span><span class="sxs-lookup"><span data-stu-id="36d5a-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resource governor classification process assigns incoming sessions to a workload group based on the characteristics of the session.</span></span> <span data-ttu-id="36d5a-104">您可以透過撰寫使用者定義函數 (稱為分類函數) 來自訂分類邏輯。</span><span class="sxs-lookup"><span data-stu-id="36d5a-104">You can tailor the classification logic by writing a user-defined function, called a classifier function.</span></span>  
  
## <a name="classification"></a><span data-ttu-id="36d5a-105">分類</span><span class="sxs-lookup"><span data-stu-id="36d5a-105">Classification</span></span>  
 <span data-ttu-id="36d5a-106">資源管理員支援內送工作階段的分類。</span><span class="sxs-lookup"><span data-stu-id="36d5a-106">Resource Governor supports the classification of incoming sessions.</span></span> <span data-ttu-id="36d5a-107">分類是以函數中包含的一組使用者撰寫準則為基礎。</span><span class="sxs-lookup"><span data-stu-id="36d5a-107">Classification is based on a set of user-written criteria contained in a function.</span></span> <span data-ttu-id="36d5a-108">函數邏輯的結果可讓資源管理員將工作階段分類至現有的工作負載群組中。</span><span class="sxs-lookup"><span data-stu-id="36d5a-108">The results of the function logic enable Resource Governor to classify sessions into existing workload groups.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="36d5a-109">內部工作負載群組會填入僅供內部使用的要求。</span><span class="sxs-lookup"><span data-stu-id="36d5a-109">The internal workload group is populated with requests that are for internal use only.</span></span> <span data-ttu-id="36d5a-110">您無法變更用於路由傳送這些要求的準則，而且無法將要求分類至內部工作負載群組中。</span><span class="sxs-lookup"><span data-stu-id="36d5a-110">You cannot change the criteria used for routing these requests and you cannot classify requests into the internal workload group.</span></span>  
  
 <span data-ttu-id="36d5a-111">您可以撰寫純量函數，其中包含用來將內送工作階段指派給工作負載群組的邏輯。</span><span class="sxs-lookup"><span data-stu-id="36d5a-111">You can write a scalar function that contains the logic that is used to assign incoming sessions to a workload group.</span></span> <span data-ttu-id="36d5a-112">您必須先完成下列動作，然後才能使用這個函數：</span><span class="sxs-lookup"><span data-stu-id="36d5a-112">Before you can use this function, you must complete the following actions:</span></span>  
  
-   <span data-ttu-id="36d5a-113">使用 ALTER RESOURCE GOVERNOR 陳述式來建立並註冊此函數。</span><span class="sxs-lookup"><span data-stu-id="36d5a-113">Create and register the function using the ALTER RESOURCE GOVERNOR statement.</span></span> <span data-ttu-id="36d5a-114">如需詳細資訊，請參閱 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="36d5a-114">For more information, see [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql).</span></span>  
  
-   <span data-ttu-id="36d5a-115">使用 ALTER RESOURCE GOVERNOR 陳述式搭配 RECONFIGURE 參數來更新資源管理員組態。</span><span class="sxs-lookup"><span data-stu-id="36d5a-115">Update the Resource Governor configuration using the ALTER RESOURCE GOVERNOR statement with the RECONFIGURE parameter.</span></span>  
  
 <span data-ttu-id="36d5a-116">在您建立此函數並套用組態變更之後，資源管理員分類就會使用此函數傳回的工作負載群組名稱，將新的要求傳送至適當的工作負載群組。</span><span class="sxs-lookup"><span data-stu-id="36d5a-116">After you create the function and apply the configuration changes, the Resource Governor classifier will use the workload group name returned by the function to send a new request to the appropriate workload group.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="36d5a-117">如果分類函數沒有在指定的登入逾時設定內完成，用戶端工作階段可能會逾時。</span><span class="sxs-lookup"><span data-stu-id="36d5a-117">The client session may time out if the classification function does not complete within the specified time-out for the login.</span></span> <span data-ttu-id="36d5a-118">但是，登入逾時是用戶端屬性，因此伺服器不知道發生逾時。長時間執行的分類函數可能會長期給伺服器留下遭遺棄的連接。</span><span class="sxs-lookup"><span data-stu-id="36d5a-118">Login time-out is a client property and as such, the server is unaware of a time-out. A long-running classifier function can leave the server with orphaned connections for long periods.</span></span> <span data-ttu-id="36d5a-119">因此，請務必建立在連接逾時之前執行完成的分類函數。</span><span class="sxs-lookup"><span data-stu-id="36d5a-119">It is important that you create classifier functions that finish executing before a connection time-out.</span></span>  
  
 <span data-ttu-id="36d5a-120">使用者定義的函數具有下列特性和行為：</span><span class="sxs-lookup"><span data-stu-id="36d5a-120">The user-defined function has the following characteristics and behaviors:</span></span>  
  
-   <span data-ttu-id="36d5a-121">系統會針對每個新的工作階段評估使用者定義函數，即使啟用了連接共用也一樣。</span><span class="sxs-lookup"><span data-stu-id="36d5a-121">The user-defined function is evaluated for every new session, even when connection pooling is enabled.</span></span>  
  
-   <span data-ttu-id="36d5a-122">使用者定義的函數會提供工作負載群組內容給工作階段。</span><span class="sxs-lookup"><span data-stu-id="36d5a-122">The user-defined function gives workload group context for the session.</span></span> <span data-ttu-id="36d5a-123">決定群組成員資格之後，此工作階段就會在工作階段的存留期間繫結至工作負載群組。</span><span class="sxs-lookup"><span data-stu-id="36d5a-123">After group membership is determined, the session is bound to the workload group for the lifetime of the session.</span></span>  
  
-   <span data-ttu-id="36d5a-124">如果使用者定義的函數傳回 NULL、預設值或不存在群組的名稱，系統就會提供預設工作負載群組內容給此工作階段。</span><span class="sxs-lookup"><span data-stu-id="36d5a-124">If the user-defined function returns NULL, default, or the name of non-existent group the session is given the default workload group context.</span></span> <span data-ttu-id="36d5a-125">此外，如果這個函數由於任何原因而失敗，系統也會提供預設內容給此工作階段。</span><span class="sxs-lookup"><span data-stu-id="36d5a-125">The session is also given the default context if the function fails for any reason.</span></span>  
  
-   <span data-ttu-id="36d5a-126">您應該使用伺服器範圍 (master 資料庫) 來定義此函數。</span><span class="sxs-lookup"><span data-stu-id="36d5a-126">The function should be defined with server scope (master database).</span></span>  
  
-   <span data-ttu-id="36d5a-127">只有在 ALTER RESOURCE GOVERNOR RECONFIGURE 執行之後，使用者定義的分類函數指定才會生效。</span><span class="sxs-lookup"><span data-stu-id="36d5a-127">The classifier user-defined function designation only takes effect after ALTER RESOURCE GOVERNOR RECONFIGURE is executed.</span></span>  
  
-   <span data-ttu-id="36d5a-128">您一次只能指定一個使用者定義函數當做分類函數。</span><span class="sxs-lookup"><span data-stu-id="36d5a-128">Only one user-defined function can be designated as a classifier at a time.</span></span>  
  
-   <span data-ttu-id="36d5a-129">除非分類狀態被移除，否則您無法卸除或更改使用者定義的分類函數。</span><span class="sxs-lookup"><span data-stu-id="36d5a-129">The classifier user-defined function cannot be dropped or altered unless its classifier status is removed.</span></span>  
  
-   <span data-ttu-id="36d5a-130">如果使用者定義的分類函數不存在，所有工作階段都會分類至預設群組中。</span><span class="sxs-lookup"><span data-stu-id="36d5a-130">In the absence of a classifier user-defined function, all sessions are classified into the default group.</span></span>  
  
-   <span data-ttu-id="36d5a-131">分類函數所傳回工作負載群組位於結構描述繫結限制的範圍以外。</span><span class="sxs-lookup"><span data-stu-id="36d5a-131">The workload group returned by the classifier function is outside the scope of the schema-binding restriction.</span></span> <span data-ttu-id="36d5a-132">例如，雖然您無法卸除資料表，但是卻能夠卸除工作負載群組。</span><span class="sxs-lookup"><span data-stu-id="36d5a-132">For example, you cannot drop a table, but you can drop a workload group.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="36d5a-133">我們建議您在伺服器上啟用專用管理員連接 (DAC)。</span><span class="sxs-lookup"><span data-stu-id="36d5a-133">We recommend enabling the Dedicated Administrator Connection (DAC) on the server.</span></span> <span data-ttu-id="36d5a-134">DAC 不受資源管理員分類限制，而且可用來監視和疑難排解分類函數。</span><span class="sxs-lookup"><span data-stu-id="36d5a-134">The DAC is not subject to Resource Governor classification and can be used to monitor and troubleshoot a classifier function.</span></span> <span data-ttu-id="36d5a-135">如需詳細資訊，請參閱 [資料庫管理員的診斷連接](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)。</span><span class="sxs-lookup"><span data-stu-id="36d5a-135">For more information, see [Diagnostic Connection for Database Administrators](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md).</span></span> <span data-ttu-id="36d5a-136">如果 DAC 無法用於疑難排解，其他選項就是在單一使用者模式中重新啟動系統。</span><span class="sxs-lookup"><span data-stu-id="36d5a-136">If a DAC is not available for troubleshooting, the other option is to restart the system in single user mode.</span></span> <span data-ttu-id="36d5a-137">雖然單一使用者模式不受分類限制，但是您無法在資源管理員分類執行時進行診斷。</span><span class="sxs-lookup"><span data-stu-id="36d5a-137">Although single user mode is not subject to classification, it does not give you the ability to diagnose Resource Governor classification while it is running.</span></span>  
  
### <a name="classification-process"></a><span data-ttu-id="36d5a-138">分類程序</span><span class="sxs-lookup"><span data-stu-id="36d5a-138">Classification Process</span></span>  
 <span data-ttu-id="36d5a-139">在資源管理員的內容中，工作階段的登入程序包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="36d5a-139">In the context of Resource Governor, the login process for a session consists of the following steps:</span></span>  
  
1.  <span data-ttu-id="36d5a-140">登入驗證</span><span class="sxs-lookup"><span data-stu-id="36d5a-140">Login authentication</span></span>  
  
2.  <span data-ttu-id="36d5a-141">LOGON 觸發程序執行</span><span class="sxs-lookup"><span data-stu-id="36d5a-141">LOGON trigger execution</span></span>  
  
3.  <span data-ttu-id="36d5a-142">分類</span><span class="sxs-lookup"><span data-stu-id="36d5a-142">Classification</span></span>  
  
 <span data-ttu-id="36d5a-143">開始分類時，資源管理員就會執行分類函數並使用此函數所傳回的值，將要求傳送至適當的工作負載群組。</span><span class="sxs-lookup"><span data-stu-id="36d5a-143">When classification starts, Resource Governor executes the classifier function and uses the value returned by the function to send requests to the appropriate workload group.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="36d5a-144">[sys.dm_exec_sessions](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) 和 [sys.dm_exec_requests](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql)中有公開執行分類函數和 LOGON 觸發程序的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="36d5a-144">Information about the execution of the classifier function and LOGON triggers is exposed in [sys.dm_exec_sessions](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql) and [sys.dm_exec_requests](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql).</span></span>  
  
## <a name="classification-function-tasks"></a><span data-ttu-id="36d5a-145">分類函數工作</span><span class="sxs-lookup"><span data-stu-id="36d5a-145">Classification Function Tasks</span></span>  
  
|<span data-ttu-id="36d5a-146">工作描述</span><span class="sxs-lookup"><span data-stu-id="36d5a-146">Task Description</span></span>|<span data-ttu-id="36d5a-147">主題</span><span class="sxs-lookup"><span data-stu-id="36d5a-147">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="36d5a-148">描述如何建立和測試分類使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="36d5a-148">Describes how to create and test a classifier user-defined function.</span></span>|[<span data-ttu-id="36d5a-149">建立和測試分類使用者定義函數</span><span class="sxs-lookup"><span data-stu-id="36d5a-149">Create and Test a Classifier User-Defined Function</span></span>](create-and-test-a-classifier-user-defined-function.md)|  
  
## <a name="see-also"></a><span data-ttu-id="36d5a-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36d5a-150">See Also</span></span>  
 <span data-ttu-id="36d5a-151">[資源管理員](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="36d5a-151">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="36d5a-152">[啟用資源管理員](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="36d5a-152">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="36d5a-153">[資源管理員資源集區](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="36d5a-153">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="36d5a-154">[資源管理員工作負載群組](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="36d5a-154">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 <span data-ttu-id="36d5a-155">[使用範本來設定資源管理員](configure-resource-governor-using-a-template.md) </span><span class="sxs-lookup"><span data-stu-id="36d5a-155">[Configure Resource Governor Using a Template](configure-resource-governor-using-a-template.md) </span></span>  
 [<span data-ttu-id="36d5a-156">檢視資源管理員屬性</span><span class="sxs-lookup"><span data-stu-id="36d5a-156">View Resource Governor Properties</span></span>](view-resource-governor-properties.md)  
  
  
