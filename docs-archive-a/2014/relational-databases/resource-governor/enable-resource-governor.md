---
title: 啟用資源管理員 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, enabling
ms.assetid: 4d17af53-cf11-4ce4-aab4-deda94a49836
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7b1b0f780457aa5a4d26cbb463c9f31a94185f0d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699397"
---
# <a name="enable-resource-governor"></a><span data-ttu-id="ff533-102">啟用資源管理員</span><span class="sxs-lookup"><span data-stu-id="ff533-102">Enable Resource Governor</span></span>
  <span data-ttu-id="ff533-103">預設會關閉資源管理員。</span><span class="sxs-lookup"><span data-stu-id="ff533-103">The Resource Governor is turned off by default.</span></span> <span data-ttu-id="ff533-104">您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 Transact-SQL 啟用資源管理員。</span><span class="sxs-lookup"><span data-stu-id="ff533-104">You can enable the Resource Governor by using either [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or Transact-SQL.</span></span>  
  
-   <span data-ttu-id="ff533-105">**開始之前：** [限制事項](#LimitationsRestrictions)、[權限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="ff533-105">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="ff533-106">**若要啟用 Resource Governor，請使用下列方式：** [物件總管](#RGOnObjEx)、[Resource Governor 屬性](#RGOnProp)、[Transact-SQL](#RGOnTSQL)</span><span class="sxs-lookup"><span data-stu-id="ff533-106">**To enable Resource Governorn, using:**  [Object Explorer](#RGOnObjEx), [Resource Governor Properties](#RGOnProp), [Transact-SQL](#RGOnTSQL)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ff533-107">開始之前</span><span class="sxs-lookup"><span data-stu-id="ff533-107">Before You Begin</span></span>  
 <span data-ttu-id="ff533-108">啟用資源管理員會產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="ff533-108">Enabling the resource governor has the following results:</span></span>  
  
-   <span data-ttu-id="ff533-109">系統會針對新的連接執行分類函數，以便將其工作負載指派給工作負載群組。</span><span class="sxs-lookup"><span data-stu-id="ff533-109">The classifier function is run for new connections so that their workloads can be assigned to workload groups.</span></span>  
  
-   <span data-ttu-id="ff533-110">系統會接受並強制執行資源管理員組態中指定的資源限制。</span><span class="sxs-lookup"><span data-stu-id="ff533-110">The resource limits that are specified in the Resource Governor configuration are honored and enforced.</span></span>  
  
-   <span data-ttu-id="ff533-111">啟用資源管理員之前存在的要求會受到停用資源管理員時所做的任何組態變更影響。</span><span class="sxs-lookup"><span data-stu-id="ff533-111">Requests that existed before enabling Resource Governor are affected by any configuration changes that were made when the Resource Governor was disabled.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="ff533-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="ff533-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="ff533-113">在使用者交易中時，您無法使用 `ALTER RESOURCE GOVERNOR` 陳述式啟用資源管理員。</span><span class="sxs-lookup"><span data-stu-id="ff533-113">You cannot use the `ALTER RESOURCE GOVERNOR` statement to enable Resource Governor when in a user transaction.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ff533-114">權限</span><span class="sxs-lookup"><span data-stu-id="ff533-114">Permissions</span></span>  
 <span data-ttu-id="ff533-115">啟用資源管理員需要 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="ff533-115">Enabling the Resource Governor requires CONTROL SERVER permission.</span></span>  
  
##  <a name="enable-resource-governor-using-object-explorer"></a><a name="RGOnObjEx"></a> <span data-ttu-id="ff533-116">使用物件總管啟用資源管理員</span><span class="sxs-lookup"><span data-stu-id="ff533-116">Enable Resource Governor Using Object Explorer</span></span>  
 <span data-ttu-id="ff533-117">**若要使用物件總管啟用資源管理員**</span><span class="sxs-lookup"><span data-stu-id="ff533-117">**To enable the Resource Governor by using Object Explorer**</span></span>  
  
1.  <span data-ttu-id="ff533-118">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，開啟 [物件總管]，然後遞迴地向下展開 **[管理]** 節點至 **[資源管理員]** 。</span><span class="sxs-lookup"><span data-stu-id="ff533-118">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to **Resource Governor**.</span></span>  
  
2.  <span data-ttu-id="ff533-119">以滑鼠右鍵按一下 [資源管理員]，然後按一下 [啟用]。</span><span class="sxs-lookup"><span data-stu-id="ff533-119">Right-click **Resource Governor**, and then click **Enable**.</span></span>  
  
##  <a name="enable-resource-governor-using-resource-governor-properties"></a><a name="RGOnProp"></a> <span data-ttu-id="ff533-120">使用資源管理員屬性啟用資源管理員</span><span class="sxs-lookup"><span data-stu-id="ff533-120">Enable Resource Governor Using Resource Governor Properties</span></span>  
 <span data-ttu-id="ff533-121">**若要使用資源管理員屬性頁面來啟用資源管理員**</span><span class="sxs-lookup"><span data-stu-id="ff533-121">**To enable the Resource Governor by using the Resource Governor Properties page**</span></span>  
  
1.  <span data-ttu-id="ff533-122">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，開啟 [物件總管]，然後遞迴地向下展開 **[管理]** 節點至 **[資源管理員]** 。</span><span class="sxs-lookup"><span data-stu-id="ff533-122">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer and recursively expand the **Management** node down to **Resource Governor**.</span></span>  
  
2.  <span data-ttu-id="ff533-123">以滑鼠右鍵按一下 [資源管理員]，然後按一下 [屬性]，這會開啟 [資源管理員屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="ff533-123">Right-click **Resource Governor** and then click **Properties**, this opens the **Resource Governor Properties** page.</span></span>  
  
3.  <span data-ttu-id="ff533-124">按一下 **[啟用資源管理員]** 核取方塊，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="ff533-124">Click the **Enable Resource Governor** check box, and then click **OK**.</span></span>  
  
##  <a name="enable-resource-governor-using-transact-sql"></a><a name="RGOnTSQL"></a> <span data-ttu-id="ff533-125">使用 Transact-SQL 啟用資源管理員</span><span class="sxs-lookup"><span data-stu-id="ff533-125">Enable Resource Governor Using Transact-SQL</span></span>  
 <span data-ttu-id="ff533-126">**若要使用 Transact-SQL 啟用資源管理員**</span><span class="sxs-lookup"><span data-stu-id="ff533-126">**To enable the Resource Governor by using Transact-SQL**</span></span>  
  
1.  <span data-ttu-id="ff533-127">執行 **ALTER RESOURCE GOVERNOR RECONFIGURE** 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ff533-127">Run the **ALTER RESOURCE GOVERNOR RECONFIGURE** statement.</span></span>  
  
### <a name="example-transact-sql"></a><span data-ttu-id="ff533-128">範例 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ff533-128">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="ff533-129">下列範例會啟用資源管理員。</span><span class="sxs-lookup"><span data-stu-id="ff533-129">The following example enables the Resource Governor.</span></span>  
  
```  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="ff533-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff533-130">See Also</span></span>  
 <span data-ttu-id="ff533-131">[資源管理員](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="ff533-131">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="ff533-132">[停用資源管理員](disable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="ff533-132">[Disable Resource Governor](disable-resource-governor.md) </span></span>  
 <span data-ttu-id="ff533-133">[資源管理員資源集區](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="ff533-133">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="ff533-134">[資源管理員工作負載群組](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="ff533-134">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 <span data-ttu-id="ff533-135">[資源管理員分類函數](resource-governor-classifier-function.md) </span><span class="sxs-lookup"><span data-stu-id="ff533-135">[Resource Governor Classifier Function](resource-governor-classifier-function.md) </span></span>  
 [<span data-ttu-id="ff533-136">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ff533-136">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
