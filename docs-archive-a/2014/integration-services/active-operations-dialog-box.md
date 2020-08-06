---
title: 作用中的作業對話方塊 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.isoperations.executions.f1
- sql12.ssis.ssms.isoperations.general.f1
ms.assetid: 5bb0fcd6-0ce9-488a-85b8-25dddaa03cda
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 49861de7be207875c554e02d3f3b1b2f941fff64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592826"
---
# <a name="active-operations-dialog-box"></a><span data-ttu-id="05d44-102">作用中的作業對話方塊</span><span class="sxs-lookup"><span data-stu-id="05d44-102">Active Operations Dialog Box</span></span>
  <span data-ttu-id="05d44-103">使用 **[作用中的作業]** 對話方塊檢視 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 伺服器上目前執行中之 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 作業 (例如，部署、驗證及封裝執行) 的狀態。</span><span class="sxs-lookup"><span data-stu-id="05d44-103">Use the **Active Operations** dialog box to view the status of currently running [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] operations on the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server, such as deployment, validation, and package execution.</span></span> <span data-ttu-id="05d44-104">此資料儲存在 SSISDB 目錄中。</span><span class="sxs-lookup"><span data-stu-id="05d44-104">This data is stored in the SSISDB catalog.</span></span>  
  
 <span data-ttu-id="05d44-105">如需相關 [!INCLUDE[tsql](../includes/tsql-md.md)] 檢視的詳細資訊，請參閱 [catalog.operations &#40;SSISDB 資料庫&#41;](/sql/integration-services/system-views/catalog-operations-ssisdb-database)、[catalog.validations &#40;SSISDB 資料庫&#41;](/sql/integration-services/system-views/catalog-validations-ssisdb-database) 和 [catalog.executions &#40;SSISDB 資料庫&#41;](/sql/integration-services/system-views/catalog-executions-ssisdb-database)</span><span class="sxs-lookup"><span data-stu-id="05d44-105">For more information about related [!INCLUDE[tsql](../includes/tsql-md.md)] views, see [catalog.operations &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-operations-ssisdb-database), [catalog.validations &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-validations-ssisdb-database), and [catalog.executions &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-executions-ssisdb-database)</span></span>  
  
 <span data-ttu-id="05d44-106">**您想要做什麼事？**</span><span class="sxs-lookup"><span data-stu-id="05d44-106">**What do you want to do?**</span></span>  
  
1.  <span data-ttu-id="05d44-107">[開啟 [作用中的作業] 對話方塊](#open_dialog)</span><span class="sxs-lookup"><span data-stu-id="05d44-107">[Open the Active Operations Dialog Box](#open_dialog)</span></span>  
  
2.  [<span data-ttu-id="05d44-108">設定選項</span><span class="sxs-lookup"><span data-stu-id="05d44-108">Configure the Options</span></span>](#options)  
  
##  <a name="open-the-active-operations-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="05d44-109">開啟 [作用中的作業] 對話方塊</span><span class="sxs-lookup"><span data-stu-id="05d44-109">Open the Active Operations Dialog Box</span></span>  
  
1.  <span data-ttu-id="05d44-110">開啟 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05d44-110">Open [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="05d44-111">連接 Microsoft SQL Server Database Engine</span><span class="sxs-lookup"><span data-stu-id="05d44-111">Connect Microsoft SQL Server Database Engine</span></span>  
  
3.  <span data-ttu-id="05d44-112">在 [物件總管] 中，展開 **[Integration Services]** 節點，再以滑鼠右鍵按一下 **[SSISDB]** ，然後按一下 **[作用中的作業]** 。</span><span class="sxs-lookup"><span data-stu-id="05d44-112">In Object Explorer, expand the **Integration Services** node, right-click **SSISDB**, and then click **Active Operations**.</span></span>  
  
##  <a name="configure-the-options"></a><a name="options"></a> <span data-ttu-id="05d44-113">設定選項</span><span class="sxs-lookup"><span data-stu-id="05d44-113">Configure the Options</span></span>  
  
### <a name="options"></a><span data-ttu-id="05d44-114">選項。</span><span class="sxs-lookup"><span data-stu-id="05d44-114">Options</span></span>  
 <span data-ttu-id="05d44-115">**型別**</span><span class="sxs-lookup"><span data-stu-id="05d44-115">**Type**</span></span>  
 <span data-ttu-id="05d44-116">指定作業的類型。</span><span class="sxs-lookup"><span data-stu-id="05d44-116">Specifies the type of operation.</span></span> <span data-ttu-id="05d44-117">以下是 [**類型**] 欄位的可能值，以及 transact-sql 視圖的 [operations_type] 資料行中的對應值 `catalog.operations` 。</span><span class="sxs-lookup"><span data-stu-id="05d44-117">The following are the possible values for the **Type** field and the corresponding values in the operations_type column of the Transact-SQL `catalog.operations` view.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="05d44-118">初始化 Integration Services</span><span class="sxs-lookup"><span data-stu-id="05d44-118">Integration Services initialization</span></span>|<span data-ttu-id="05d44-119">1</span><span class="sxs-lookup"><span data-stu-id="05d44-119">1</span></span>|  
|<span data-ttu-id="05d44-120">作業清除 (SQL 代理程式作業)</span><span class="sxs-lookup"><span data-stu-id="05d44-120">Operations cleanup (SQL Agent job)</span></span>|<span data-ttu-id="05d44-121">2</span><span class="sxs-lookup"><span data-stu-id="05d44-121">2</span></span>|  
|<span data-ttu-id="05d44-122">專案版本清理 (SQL 代理程式作業)</span><span class="sxs-lookup"><span data-stu-id="05d44-122">Project versions cleanup (SQL Agent job)</span></span>|<span data-ttu-id="05d44-123">3</span><span class="sxs-lookup"><span data-stu-id="05d44-123">3</span></span>|  
|<span data-ttu-id="05d44-124">部署專案</span><span class="sxs-lookup"><span data-stu-id="05d44-124">Deploy project</span></span>|<span data-ttu-id="05d44-125">101</span><span class="sxs-lookup"><span data-stu-id="05d44-125">101</span></span>|  
|<span data-ttu-id="05d44-126">還原專案</span><span class="sxs-lookup"><span data-stu-id="05d44-126">Restore project</span></span>|<span data-ttu-id="05d44-127">106</span><span class="sxs-lookup"><span data-stu-id="05d44-127">106</span></span>|  
|<span data-ttu-id="05d44-128">建立及啟動封裝執行</span><span class="sxs-lookup"><span data-stu-id="05d44-128">Create and start package execution</span></span>|<span data-ttu-id="05d44-129">200</span><span class="sxs-lookup"><span data-stu-id="05d44-129">200</span></span>|  
|<span data-ttu-id="05d44-130">停止作業 (停止驗證或執行</span><span class="sxs-lookup"><span data-stu-id="05d44-130">Stop operation (stopping a validation or execution</span></span>|<span data-ttu-id="05d44-131">202</span><span class="sxs-lookup"><span data-stu-id="05d44-131">202</span></span>|  
|<span data-ttu-id="05d44-132">驗證專案</span><span class="sxs-lookup"><span data-stu-id="05d44-132">Validate project</span></span>|<span data-ttu-id="05d44-133">300</span><span class="sxs-lookup"><span data-stu-id="05d44-133">300</span></span>|  
|<span data-ttu-id="05d44-134">驗證封裝</span><span class="sxs-lookup"><span data-stu-id="05d44-134">Validate package</span></span>|<span data-ttu-id="05d44-135">301</span><span class="sxs-lookup"><span data-stu-id="05d44-135">301</span></span>|  
|<span data-ttu-id="05d44-136">設定目錄</span><span class="sxs-lookup"><span data-stu-id="05d44-136">Configure catalog</span></span>|<span data-ttu-id="05d44-137">1000</span><span class="sxs-lookup"><span data-stu-id="05d44-137">1000</span></span>|  
  
 <span data-ttu-id="05d44-138">**停止**</span><span class="sxs-lookup"><span data-stu-id="05d44-138">**Stop**</span></span>  
 <span data-ttu-id="05d44-139">按一下即可停止目前執行中的作業。</span><span class="sxs-lookup"><span data-stu-id="05d44-139">Click to stop a currently running operation.</span></span>  
  
  
