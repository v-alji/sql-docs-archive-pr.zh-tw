---
title: 刪除資源集區 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, resource pool delete
- resource pools [SQL Server], delete
ms.assetid: 3bdd348b-6582-4ffa-80ef-d49e50596ce5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a67b0e2262fa3007597091b6087cc937bb0f3276
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699406"
---
# <a name="delete-a-resource-pool"></a><span data-ttu-id="5c104-102">刪除資源集區</span><span class="sxs-lookup"><span data-stu-id="5c104-102">Delete a Resource Pool</span></span>
  <span data-ttu-id="5c104-103">您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 Transact-SQL 刪除資源集區。</span><span class="sxs-lookup"><span data-stu-id="5c104-103">You can delete a resource pool by using either [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or Transact-SQL.</span></span>  
  
-   <span data-ttu-id="5c104-104">**開始之前：** [限制事項](#LimitationsRestrictions)、[權限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="5c104-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="5c104-105">**若要刪除資源集區，請使用下列方式：** [SQL Server Management Studio](#DelRPSSMS)、[Transact-SQL](#DelRPTSQL)</span><span class="sxs-lookup"><span data-stu-id="5c104-105">**To delete a resource pool, using:** [SQL Server Management Studio](#DelRPSSMS), [Transact-SQL](#DelRPTSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5c104-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="5c104-106">Before You Begin</span></span>  
 <span data-ttu-id="5c104-107">如果資源集區包含工作負載群組，您就無法刪除該資源集區。</span><span class="sxs-lookup"><span data-stu-id="5c104-107">You cannot delete a resource pool if it contains workload groups.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="5c104-108">限制事項</span><span class="sxs-lookup"><span data-stu-id="5c104-108">Limitations and Restrictions</span></span>  
 <span data-ttu-id="5c104-109">您無法刪除資源管理員的預設或內部資源集區。</span><span class="sxs-lookup"><span data-stu-id="5c104-109">You cannot delete the Resource Governor default or internal resource pools.</span></span> <span data-ttu-id="5c104-110">如果資源集區包含工作負載群組，您就無法刪除該資源集區。</span><span class="sxs-lookup"><span data-stu-id="5c104-110">You cannot delete a resource pool if it contains workload groups.</span></span> <span data-ttu-id="5c104-111">如需詳細資訊，請參閱 [Delete a Workload Group](delete-a-workload-group.md)。</span><span class="sxs-lookup"><span data-stu-id="5c104-111">For more information, see [Delete a Workload Group](delete-a-workload-group.md).</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="5c104-112">權限</span><span class="sxs-lookup"><span data-stu-id="5c104-112">Permissions</span></span>  
 <span data-ttu-id="5c104-113">刪除資源集區需要 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="5c104-113">Deleting a resource pool requires CONTROL SERVER permission.</span></span>  
  
##  <a name="delete-a-resource-pool-using-object-explorer"></a><a name="DelRPSSMS"></a> <span data-ttu-id="5c104-114">使用物件總管刪除資源集區</span><span class="sxs-lookup"><span data-stu-id="5c104-114">Delete a Resource Pool Using Object Explorer</span></span>  
 <span data-ttu-id="5c104-115">**若要使用 SQL Server Management Studio 刪除資源集區**</span><span class="sxs-lookup"><span data-stu-id="5c104-115">**To delete a resource pool by using SQL Server Management Studio**</span></span>  
  
1.  <span data-ttu-id="5c104-116">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，開啟 [物件總管]，然後遞迴地向下展開 **[管理]** 節點至 **[資源管理員]** 。</span><span class="sxs-lookup"><span data-stu-id="5c104-116">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to and including **Resource Governor**.</span></span>  
  
2.  <span data-ttu-id="5c104-117">以滑鼠右鍵按一下要刪除的資源集區，然後按一下 [刪除]。</span><span class="sxs-lookup"><span data-stu-id="5c104-117">Right-click the resource pool to be deleted, and then click **Delete**.</span></span>  
  
3.  <span data-ttu-id="5c104-118">在 **[刪除物件]** 視窗中，資源集區列於 **[要刪除的物件]** 清單內。</span><span class="sxs-lookup"><span data-stu-id="5c104-118">In the **Delete Object** window, the resource pool is listed in the **Object to be deleted** list.</span></span> <span data-ttu-id="5c104-119">若要刪除資源集區，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="5c104-119">To delete the resource pool, click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5c104-120">如果您嘗試刪除的資源集區包含工作負載群組，這項動作將會失敗。</span><span class="sxs-lookup"><span data-stu-id="5c104-120">If the resource pool that you are trying to delete contains a workload group, this action will fail.</span></span>  
  
##  <a name="delete-a-resource-pool-using-transact-sql"></a><a name="DelRPTSQL"></a> <span data-ttu-id="5c104-121">使用 Transact-SQL 刪除資源集區</span><span class="sxs-lookup"><span data-stu-id="5c104-121">Delete a Resource Pool Using Transact-SQL</span></span>  
 <span data-ttu-id="5c104-122">**若要使用 Transact-SQL 刪除資源集區**</span><span class="sxs-lookup"><span data-stu-id="5c104-122">**To delete a resource pool by using Transact-SQL**</span></span>  
  
1.  <span data-ttu-id="5c104-123">執行 `DROP RESOURCE POOL` 陳述式，並指定要刪除之資源集區的名稱。</span><span class="sxs-lookup"><span data-stu-id="5c104-123">Run the `DROP RESOURCE POOL` statement specifying the name of the resource pool to delete.</span></span>  
  
2.  <span data-ttu-id="5c104-124">執行 **ALTER RESOURCE GOVERNOR RECONFIGURE** 陳述式。</span><span class="sxs-lookup"><span data-stu-id="5c104-124">Run the **ALTER RESOURCE GOVERNOR RECONFIGURE** statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="5c104-125">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5c104-125">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="5c104-126">下列範例會卸除名稱為 `poolAdhoc`的工作負載群組。</span><span class="sxs-lookup"><span data-stu-id="5c104-126">The following example drops a workload group named `poolAdhoc`.</span></span>  
  
```  
DROP RESOURCE POOL poolAdhoc;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="5c104-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c104-127">See Also</span></span>  
 <span data-ttu-id="5c104-128">[資源管理員](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="5c104-128">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="5c104-129">[資源管理員資源集區](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="5c104-129">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="5c104-130">[建立資源集區](create-a-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="5c104-130">[Create a Resource Pool](create-a-resource-pool.md) </span></span>  
 <span data-ttu-id="5c104-131">[變更資源集區設定](change-resource-pool-settings.md) </span><span class="sxs-lookup"><span data-stu-id="5c104-131">[Change Resource Pool Settings](change-resource-pool-settings.md) </span></span>  
 <span data-ttu-id="5c104-132">[資源管理員工作負載群組](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="5c104-132">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 <span data-ttu-id="5c104-133">[資源管理員分類函數](resource-governor-classifier-function.md) </span><span class="sxs-lookup"><span data-stu-id="5c104-133">[Resource Governor Classifier Function](resource-governor-classifier-function.md) </span></span>  
 <span data-ttu-id="5c104-134">[DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-workload-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5c104-134">[DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-workload-group-transact-sql) </span></span>  
 <span data-ttu-id="5c104-135">[DROP RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5c104-135">[DROP RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-resource-pool-transact-sql) </span></span>  
 [<span data-ttu-id="5c104-136">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5c104-136">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
