---
title: 建立及管理表格式模型資料分割 (SSAS 表格式) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: dab72cf0-95bc-4b63-95dc-505b5cd881c1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 58c408c712d6ac4b6bd590bd0f8c895dc1a88700
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598527"
---
# <a name="create-and-manage-tabular-model-partitions-ssas-tabular"></a><span data-ttu-id="3f56c-102">建立及管理表格式模型資料分割 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="3f56c-102">Create and Manage Tabular Model Partitions (SSAS Tabular)</span></span>
  <span data-ttu-id="3f56c-103">分割區會將一個資料表分割成多個邏輯部分。</span><span class="sxs-lookup"><span data-stu-id="3f56c-103">Partitions divide a table into logical parts.</span></span> <span data-ttu-id="3f56c-104">接著，每個分割區可以不受其他分割區的影響，單獨處理 (重新整理)。</span><span class="sxs-lookup"><span data-stu-id="3f56c-104">Each partition can then be processed (Refreshed) independent of other partitions.</span></span> <span data-ttu-id="3f56c-105">模型撰寫期間，在已部署的模型中有重複定義的模型資料分割。</span><span class="sxs-lookup"><span data-stu-id="3f56c-105">Partitions defined for a model during model authoring are duplicated in a deployed model.</span></span> <span data-ttu-id="3f56c-106">部署之後，即可使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的 [資料分割]\*\*\*\* 對話方塊或指令碼，管理這些資料分割。</span><span class="sxs-lookup"><span data-stu-id="3f56c-106">Once deployed, you can manage those partitions by using the **Partitions** dialog box in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or by using a script.</span></span> <span data-ttu-id="3f56c-107">此主題提供的工作描述如何為已部署的模型建立及管理資料分割。</span><span class="sxs-lookup"><span data-stu-id="3f56c-107">Tasks provided in this topic describe how to create and manage partitions for a deployed model.</span></span>  
  
 <span data-ttu-id="3f56c-108">本主題也包括下列工作：</span><span class="sxs-lookup"><span data-stu-id="3f56c-108">This topic includes the following tasks:</span></span>  
  
-   [<span data-ttu-id="3f56c-109">建立新的資料分割</span><span class="sxs-lookup"><span data-stu-id="3f56c-109">To create a new partition</span></span>](#bkmk_create_new)  
  
-   [<span data-ttu-id="3f56c-110">複製資料分割</span><span class="sxs-lookup"><span data-stu-id="3f56c-110">To copy a partition</span></span>](#bkmk_copy)  
  
-   [<span data-ttu-id="3f56c-111">合併兩個以上的分割區</span><span class="sxs-lookup"><span data-stu-id="3f56c-111">To merge two or more partitions</span></span>](#bkmk_merge)  
  
-   [<span data-ttu-id="3f56c-112">若要刪除資料分割</span><span class="sxs-lookup"><span data-stu-id="3f56c-112">To delete a partition</span></span>](#bkmk_delete)  
  
## <a name="tasks"></a><span data-ttu-id="3f56c-113">工作</span><span class="sxs-lookup"><span data-stu-id="3f56c-113">Tasks</span></span>  
 <span data-ttu-id="3f56c-114">若要為已部署的表格式模型資料庫建立及管理資料分割，您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的 [資料分割]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3f56c-114">To create and manage partitions for a deployed tabular model database, you will use the **Partitions** dialog box in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="3f56c-115">若要檢視 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [資料分割]\*\*\*\* 對話方塊，請以滑鼠右鍵按一下資料表，然後按一下 [資料分割]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3f56c-115">To view the **Partitions** dialog box, in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click on a table, and then click **Partitions**.</span></span>  
  
###  <a name="to-create-a-new-partition"></a><a name="bkmk_create_new"></a><span data-ttu-id="3f56c-116">若要建立新的磁碟分割</span><span class="sxs-lookup"><span data-stu-id="3f56c-116">To create a new partition</span></span>  
  
1.  <span data-ttu-id="3f56c-117">在 [資料分割]\*\*\*\* 對話方塊中，按一下 [新增]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="3f56c-117">In the **Partitions** dialog box, click the **New** button.</span></span>  
  
2.  <span data-ttu-id="3f56c-118">在 **[資料分割名稱]** 中，輸入資料分割的名稱。</span><span class="sxs-lookup"><span data-stu-id="3f56c-118">In **Partition Name**, type a name for the partition.</span></span> <span data-ttu-id="3f56c-119">依預設，每個新資料分割的預設資料分割名稱是以累加的方式進行編號。</span><span class="sxs-lookup"><span data-stu-id="3f56c-119">By default, the name of the default partition will be incrementally numbered for each new partition.</span></span>  
  
3.  <span data-ttu-id="3f56c-120">在 [SQL 陳述式]\*\*\*\* 中，於查詢視窗內輸入或貼上 SQL 查詢陳述式，以定義您要包含在資料分割中的資料行及任何子句。</span><span class="sxs-lookup"><span data-stu-id="3f56c-120">In **SQL Statement**, type or paste a SQL query statement that defines the columns and any clauses you want to include in the partition into the query window.</span></span>  
  
4.  <span data-ttu-id="3f56c-121">若要驗證陳述式，請按一下 [檢查語法]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3f56c-121">To validate the statement, click **Check Syntax**.</span></span>  
  
###  <a name="to-copy-a-partition"></a><a name="bkmk_copy"></a> <span data-ttu-id="3f56c-122">複製資料分割</span><span class="sxs-lookup"><span data-stu-id="3f56c-122">To copy a partition</span></span>  
  
1.  <span data-ttu-id="3f56c-123">在 [資料分割]\*\*\*\* 對話方塊的 [資料分割]\*\*\*\* 清單中，選取您要複製的資料分割，然後按一下 [複製]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="3f56c-123">In the **Partitions** dialog box, in the **Partitions** list, select the partition you want to copy, and then click the **Copy** button.</span></span>  
  
2.  <span data-ttu-id="3f56c-124">在 **[資料分割名稱]** 中，輸入資料分割的新名稱。</span><span class="sxs-lookup"><span data-stu-id="3f56c-124">In **Partition Name**, type a new name for the partition.</span></span>  
  
3.  <span data-ttu-id="3f56c-125">在 [SQL 陳述式]\*\*\*\* 中，編輯 SQL 查詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="3f56c-125">In **SQL Statement**, edit the SQL query statement.</span></span>  
  
###  <a name="to-merge-two-or-more-partitions"></a><a name="bkmk_merge"></a> <span data-ttu-id="3f56c-126">合併兩個或兩個以上的資料分割</span><span class="sxs-lookup"><span data-stu-id="3f56c-126">To merge two or more partitions</span></span>  
  
-   <span data-ttu-id="3f56c-127">在 [資料**分割] 對話方塊的 [** 資料分割 **] 清單中**，使用 Ctrl + 按一下來選取您要合併的資料分割，然後按一下 [**合併**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="3f56c-127">In the **Partitions** dialog box, in the **Partitions** list, use Ctrl+click to select the partitions you want to merge, and then click the **Merge** button.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3f56c-128">合併資料分割並不會更新資料分割中繼資料。</span><span class="sxs-lookup"><span data-stu-id="3f56c-128">Merging partitions does not update the partition metadata.</span></span> <span data-ttu-id="3f56c-129">管理員必須針對產生的資料分割改變 SQL 陳述式，以確保處理作業會處理合併之資料分割中的所有資料。</span><span class="sxs-lookup"><span data-stu-id="3f56c-129">Administrators must alter the SQL Statement for the resulting partition to make sure processing operations process all data in the merged partition.</span></span>  
  
###  <a name="to-delete-a-partition"></a><a name="bkmk_delete"></a><span data-ttu-id="3f56c-130">若要刪除資料分割</span><span class="sxs-lookup"><span data-stu-id="3f56c-130">To delete a partition</span></span>  
  
-   <span data-ttu-id="3f56c-131">在 [資料分割]\*\*\*\* 對話方塊的 [資料分割]\*\*\*\* 清單中，選取您要刪除的資料分割，然後按一下 [刪除]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="3f56c-131">In the **Partitions** dialog box, in the **Partitions** list, select the partition you want to delete, and then click the **Delete** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f56c-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f56c-132">See Also</span></span>  
 <span data-ttu-id="3f56c-133">[表格式模型資料分割 &#40;SSAS 表格式&#41;](partitions-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="3f56c-133">[Tabular Model Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="3f56c-134">處理表格式模型資料分割 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="3f56c-134">Process Tabular Model Partitions &#40;SSAS Tabular&#41;</span></span>](process-tabular-model-partitions-ssas-tabular.md)  
  
  
