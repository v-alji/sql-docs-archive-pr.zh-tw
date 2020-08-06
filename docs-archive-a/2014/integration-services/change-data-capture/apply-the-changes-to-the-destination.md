---
title: 將變更套用到目的地 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],applying changes
ms.assetid: 338a56db-cb14-4784-a692-468eabd30f41
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dd7ab93a299ffaab2259c3d462a5c0a69160ad5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606998"
---
# <a name="apply-the-changes-to-the-destination"></a><span data-ttu-id="677b2-102">將變更套用到目的地</span><span class="sxs-lookup"><span data-stu-id="677b2-102">Apply the Changes to the Destination</span></span>
  <span data-ttu-id="677b2-103">在執行累加式變更資料載入之 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝的資料流程中，第三個工作，也就是最後一個工作是將變更套用到您的目的地。</span><span class="sxs-lookup"><span data-stu-id="677b2-103">In the data flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that performs an incremental load of change data, the third and final task is to apply the changes to your destination.</span></span> <span data-ttu-id="677b2-104">您將需要一個元件來套用插入、一個元件來套用更新，以及一個元件來套用刪除。</span><span class="sxs-lookup"><span data-stu-id="677b2-104">You will need one component to apply inserts, one to apply updates, and one to apply deletes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="677b2-105">在設計可執行累加式變更資料載入的資料流程時，第二個工作是分隔插入、更新與刪除。</span><span class="sxs-lookup"><span data-stu-id="677b2-105">The second task in designing the data flow of a package that performs an incremental load of change data is to separate inserts, updates, and deletes.</span></span> <span data-ttu-id="677b2-106">如需此元件的詳細資訊，請參閱 [處理插入、更新與刪除](process-inserts-updates-and-deletes.md)。</span><span class="sxs-lookup"><span data-stu-id="677b2-106">For more information about this component, see [Process Inserts, Updates, and Deletes](process-inserts-updates-and-deletes.md).</span></span> <span data-ttu-id="677b2-107">如需建立可執行累加式變更資料載入之封裝的完整程序描述，請參閱[異動資料擷取 &#40;SSIS&#41;](change-data-capture-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="677b2-107">For a description of the overall process for creating a package that performs an incremental load of change data, see [Change Data Capture &#40;SSIS&#41;](change-data-capture-ssis.md).</span></span>  
  
## <a name="applying-inserts"></a><span data-ttu-id="677b2-108">套用插入</span><span class="sxs-lookup"><span data-stu-id="677b2-108">Applying Inserts</span></span>  
 <span data-ttu-id="677b2-109">若要套用插入，您可以使用 OLE DB 目的地，因為新的資料列不需要任何特殊處理。</span><span class="sxs-lookup"><span data-stu-id="677b2-109">To apply inserts, you use an OLE DB destination because the new rows do not require any special handling.</span></span>  
  
#### <a name="to-process-inserts-by-using-an-ole-db-destination"></a><span data-ttu-id="677b2-110">使用 OLE DB 目的地來處理插入</span><span class="sxs-lookup"><span data-stu-id="677b2-110">To process inserts by using an OLE DB Destination</span></span>  
  
1.  <span data-ttu-id="677b2-111">在 **[資料流程]** 索引標籤上，加入 OLE DB 目的地。</span><span class="sxs-lookup"><span data-stu-id="677b2-111">On the **Data flow** tab, add an OLE DB destination.</span></span>  
  
2.  <span data-ttu-id="677b2-112">將包含插入的輸出從「條件式分割」轉換連接到 OLE DB 目的地。</span><span class="sxs-lookup"><span data-stu-id="677b2-112">Connect the output that contains inserts from the Conditional Split transformation to the OLE DB destination.</span></span>  
  
3.  <span data-ttu-id="677b2-113">在 **[OLE DB 目的地編輯器]** 的 **[連接管理員]** 頁面上，選取下列選項：</span><span class="sxs-lookup"><span data-stu-id="677b2-113">In the **OLE DB Destination Editor**, on the **Connection Manager** page, select the following options:</span></span>  
  
    1.  <span data-ttu-id="677b2-114">針對目的地資料庫選取或建立 OLE DB 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="677b2-114">Select or create an OLE DB Connection Manager for the destination database.</span></span>  
  
    2.  <span data-ttu-id="677b2-115">選取 **[資料存取模式]** 選項，然後選取目的地資料表，或輸入包含目的地資料行的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="677b2-115">Select a **Data access mode** option, and then select the destination table or enter a SQL statement that contains the destination columns.</span></span>  
  
4.  <span data-ttu-id="677b2-116">在編輯器的 **[對應]** 頁面上，將適當的資料行從變更資料對應到目的地資料表。</span><span class="sxs-lookup"><span data-stu-id="677b2-116">On the **Mappings** page of the editor, map the appropriate columns from the change data to the destination table.</span></span>  
  
## <a name="applying-updates"></a><span data-ttu-id="677b2-117">套用更新</span><span class="sxs-lookup"><span data-stu-id="677b2-117">Applying Updates</span></span>  
 <span data-ttu-id="677b2-118">若要套用更新，您可以使用「OLE DB 命令」轉換。</span><span class="sxs-lookup"><span data-stu-id="677b2-118">To apply updates, you use an OLE DB Command transformation.</span></span> <span data-ttu-id="677b2-119">您必須使用參數化的 UPDATE 陳述式，一次更新一個具有新資料行值的資料列，因此您可以使用這個轉換。</span><span class="sxs-lookup"><span data-stu-id="677b2-119">You use this transformation because you have to use a parameterized UPDATE statement to update one row at a time with the new column values.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="677b2-120">您也可以使用目的地元件套用更新。</span><span class="sxs-lookup"><span data-stu-id="677b2-120">You can also use destination components to apply updates.</span></span> <span data-ttu-id="677b2-121">使用這個方式時，您可以使用目的地元件，將資料列儲存到針對此用途所建立的暫存資料表。</span><span class="sxs-lookup"><span data-stu-id="677b2-121">When using this approach, you use the destination components to save the rows to temporary tables that you create for this purpose.</span></span> <span data-ttu-id="677b2-122">接著，您可以使用「執行 SQL」工作，根據暫存資料表的目的地，執行大量更新與大量刪除作業。</span><span class="sxs-lookup"><span data-stu-id="677b2-122">Then, you use Execute SQL tasks to perform bulk update and bulk delete operations against the destination from the temporary tables.</span></span>  
  
#### <a name="to-process-updates-by-using-an-ole-db-command-transformation"></a><span data-ttu-id="677b2-123">使用 OLE DB 命令轉換處理更新</span><span class="sxs-lookup"><span data-stu-id="677b2-123">To process updates by using an OLE DB Command transformation</span></span>  
  
1.  <span data-ttu-id="677b2-124">在 **[資料流程]** 索引標籤上，加入「OLE DB 命令」轉換。</span><span class="sxs-lookup"><span data-stu-id="677b2-124">On the **Data flow** tab, add an OLE DB Command transformation.</span></span>  
  
2.  <span data-ttu-id="677b2-125">將包含更新的輸出從「條件式分割」轉換連接到「OLE DB 命令」轉換。</span><span class="sxs-lookup"><span data-stu-id="677b2-125">Connect the output that contains updates from the Conditional Split transformation to the OLE DB Command transformation.</span></span>  
  
3.  <span data-ttu-id="677b2-126">在 **[OLE DB 命令的進階編輯器]** 的 **[連接管理員]** 索引標籤上，選取或建立目的地資料庫的 OLE DB 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="677b2-126">In the **Advanced Editor for OLE DB Command**, on the **Connection Manager** tab, select or create an OLE DB Connection Manager for the destination database.</span></span>  
  
4.  <span data-ttu-id="677b2-127">在 **[OLE DB 命令的進階編輯器]** 的 **[元件屬性]** 索引標籤上，為 **SqlCommand**輸入一個參數化的 UPDATE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="677b2-127">In the **Advanced Editor for OLE DB Command**, on the **Component Properties** tab, for **SqlCommand**, enter a parameterized UPDATE statement.</span></span>  
  
     <span data-ttu-id="677b2-128">例如，用於 Customer 資料表的 UPDATE 陳述式語法可能如下：</span><span class="sxs-lookup"><span data-stu-id="677b2-128">For example, an UPDATE statement for a Customer table might have the following syntax:</span></span>  
  
    ```  
    update CDCSample.Customer  
    set TerritoryID  = ?,  
        CustomerType  = ?,  
        rowguid  = ?,  
        ModifiedDate  = ?  
    where CustomerID = ?  
  
    ```  
  
5.  <span data-ttu-id="677b2-129">在編輯器的 **[資料行對應]** 索引標籤上，將適當的資料行從變更資料對應到 UPDATE 陳述式中的參數。</span><span class="sxs-lookup"><span data-stu-id="677b2-129">On the **Column Mappings** tab of the editor, map the appropriate columns from the change data to the parameters in the UPDATE statement.</span></span>  
  
## <a name="applying-deletes"></a><span data-ttu-id="677b2-130">套用刪除</span><span class="sxs-lookup"><span data-stu-id="677b2-130">Applying Deletes</span></span>  
 <span data-ttu-id="677b2-131">若要套用刪除，您可以使用「OLE DB 命令」轉換。</span><span class="sxs-lookup"><span data-stu-id="677b2-131">To apply deletes, you use an OLE DB Command transformation.</span></span> <span data-ttu-id="677b2-132">您必須使用參數化的 DELETE 陳述式，根據唯一識別資料列的資料行值，一次刪除單一資料列，因此您可以使用這個轉換。</span><span class="sxs-lookup"><span data-stu-id="677b2-132">You use this transformation because you have to use a parameterized DELETE statement that deletes a single row at a time based on the column value that uniquely identifies the row.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="677b2-133">您也可以使用目的地元件套用刪除。</span><span class="sxs-lookup"><span data-stu-id="677b2-133">You can also use destination components to apply deletes.</span></span> <span data-ttu-id="677b2-134">使用這個方式時，您可以使用目的地元件，將資料列儲存到針對此用途所建立的暫存資料表。</span><span class="sxs-lookup"><span data-stu-id="677b2-134">When using this approach, you use the destination components to save the rows to temporary tables that you create for this purpose.</span></span> <span data-ttu-id="677b2-135">接著，您可以使用「執行 SQL」工作，根據暫存資料表的目的地，執行大量更新與大量刪除作業。</span><span class="sxs-lookup"><span data-stu-id="677b2-135">Then, you use Execute SQL tasks to perform bulk update and bulk delete operations against the destination from the temporary tables.</span></span>  
  
#### <a name="to-process-deletes-by-using-an-ole-db-command-transformation"></a><span data-ttu-id="677b2-136">使用 OLE DB 命令轉換處理刪除</span><span class="sxs-lookup"><span data-stu-id="677b2-136">To process deletes by using an OLE DB Command transformation</span></span>  
  
1.  <span data-ttu-id="677b2-137">在 **[資料流程]** 索引標籤上，將「OLE DB 命令」轉換加入到資料流程。</span><span class="sxs-lookup"><span data-stu-id="677b2-137">On the **Data flow** tab, add an OLE DB Command transformation to the data flow.</span></span>  
  
2.  <span data-ttu-id="677b2-138">將包含刪除的輸出從「條件式分割」轉換連接到「OLE DB 命令」轉換。</span><span class="sxs-lookup"><span data-stu-id="677b2-138">Connect the output that contains deletes from the Conditional Split transformation to the OLE DB Command transformation.</span></span>  
  
3.  <span data-ttu-id="677b2-139">開啟 [進階編輯器] 來設定轉換。</span><span class="sxs-lookup"><span data-stu-id="677b2-139">Open the Advanced Editor to configure the transformation.</span></span>  
  
4.  <span data-ttu-id="677b2-140">在 **[OLE DB 命令的進階編輯器]** 的 **[連接管理員]** 索引標籤上，選取或建立目的地資料庫的 OLE DB 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="677b2-140">In the **Advanced Editor for OLE DB Command**, on the **Connection Manager** tab, select or create an OLE DB Connection Manager for the destination database.</span></span>  
  
5.  <span data-ttu-id="677b2-141">在 **[OLE DB 命令的進階編輯器]** 的 **[元件屬性]** 索引標籤上，為 **SqlCommand**輸入一個參數化的 DELETE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="677b2-141">In the **Advanced Editor for OLE DB Command**, on the **Component Properties** tab of the editor, for **SqlCommand**, enter a parameterized DELETE statement.</span></span>  
  
     <span data-ttu-id="677b2-142">例如，用於 Customer 資料表的 DELETE 陳述式語法可能如下：</span><span class="sxs-lookup"><span data-stu-id="677b2-142">For example, a DELETE statement for a Customer table might have the following syntax:</span></span>  
  
    ```  
    delete from Customer where CustomerID = ?  
  
    ```  
  
6.  <span data-ttu-id="677b2-143">在編輯器的 **[資料行對應]** 索引標籤上，將適當的資料行從變更資料對應到 DELETE 陳述式中的參數。</span><span class="sxs-lookup"><span data-stu-id="677b2-143">On the **Column Mappings** tab of the editor, map the appropriate column from the change data to the parameter in the DELETE statement.</span></span>  
  
## <a name="optimizing-inserts-and-updates-by-using-merge-functionality"></a><span data-ttu-id="677b2-144">使用 MERGE 功能最佳化插入和更新</span><span class="sxs-lookup"><span data-stu-id="677b2-144">Optimizing Inserts and Updates by Using MERGE Functionality</span></span>  
 <span data-ttu-id="677b2-145">您可以結合特定的異動資料擷取選項與 Transact-SQL MERGE 關鍵字的使用，將插入和更新的處理最佳化。</span><span class="sxs-lookup"><span data-stu-id="677b2-145">You can optimize the processing of inserts and updates by combining certain change data capture options with the use of the Transact-SQL MERGE keyword.</span></span> <span data-ttu-id="677b2-146">如需 MERGE 關鍵字的詳細資訊，請參閱 [MERGE &#40;Transact-SQL&#41;](/sql/t-sql/statements/merge-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="677b2-146">For more information about the MERGE keyword, see [MERGE &#40;Transact-SQL&#41;](/sql/t-sql/statements/merge-transact-sql).</span></span>  
  
 <span data-ttu-id="677b2-147">當您呼叫 **cdc.fn_cdc_get_net_changes_<capture_instance>** 函數時，您可以在擷取變更資料的 Transact-SQL 陳述式中，指定 *all with merge* 作為 *row_filter_option* 參數的值。</span><span class="sxs-lookup"><span data-stu-id="677b2-147">In the Transact-SQL statement that retrieves the change data, you can specify *all with merge* as the value of the *row_filter_option* parameter when you call the **cdc.fn_cdc_get_net_changes_<capture_instance>** function.</span></span> <span data-ttu-id="677b2-148">當這個異動資料擷取函數不必執行區別插入與更新所需的額外處理時，其運作會更有效率。</span><span class="sxs-lookup"><span data-stu-id="677b2-148">This change data capture function operates more efficiently when it does not have to perform the extra processing that is required to distinguish inserts from updates.</span></span> <span data-ttu-id="677b2-149">當您指定 *all with merge* 參數值時，變更資料的 **__$operation** 值為 1 (針對刪除) 或 5 (針對插入或更新所造成的變更)。</span><span class="sxs-lookup"><span data-stu-id="677b2-149">When you specify the *all with merge* parameter value, the **__$operation** value of the change data is 1 for deletes or 5 for changes that were caused by inserts or updates.</span></span> <span data-ttu-id="677b2-150">如需用於擷取變更資料之 Transact-SQL 函數的詳細資訊，請參閱 [擷取與了解變更資料](retrieve-and-understand-the-change-data.md)。利用 *all with merge* 參數值擷取變更後，您可以套用刪除，並將剩餘的資料列輸出到暫存資料表或臨時資料表。</span><span class="sxs-lookup"><span data-stu-id="677b2-150">For more information about the Transact-SQL function that is used to retrieve the change data, see [Retrieve and Understand the Change Data](retrieve-and-understand-the-change-data.md).After retrieving changes with the *all with merge* parameter value, you can apply deletes, and output the remaining rows to a temporary table or a staging table.</span></span> <span data-ttu-id="677b2-151">接著，在下游的「執行 SQL」工作中，您可以使用單一 MERGE 陳述式，將所有插入或更新從臨時資料表套用到目的地。</span><span class="sxs-lookup"><span data-stu-id="677b2-151">Then, in a downstream Execute SQL Task, you can use a single MERGE statement to apply all the inserts or updates from the staging table to the destination.</span></span>  
  
  
