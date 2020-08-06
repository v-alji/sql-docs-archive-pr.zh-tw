---
title: 使用快取連線管理員，以完整快取模式來執行查閱轉換 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Lookup transformation [Integration Services]
ms.assetid: 58bc7611-5fb5-4113-9742-10959e06b94c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8b8c77f7ecfbe79db00acce09f706468ec0a0055
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599146"
---
# <a name="implement-a-lookup-transformation-in-full-cache-mode-using-the-cache-connection-manager"></a><span data-ttu-id="cde2c-102">使用快取連線管理員以完整快取模式實作查閱轉換</span><span class="sxs-lookup"><span data-stu-id="cde2c-102">Implement a Lookup Transformation in Full Cache Mode Using the Cache Connection Manager</span></span>
  <span data-ttu-id="cde2c-103">您可以將查閱轉換設定為使用完整快取模式以及快取連接管理員。</span><span class="sxs-lookup"><span data-stu-id="cde2c-103">You can configure the Lookup transformation to use full cache mode and a Cache connection manager.</span></span> <span data-ttu-id="cde2c-104">在完整快取模式中，參考資料集會在查閱轉換執行之前載入快取。</span><span class="sxs-lookup"><span data-stu-id="cde2c-104">In full cache mode, the reference dataset is loaded into cache before the Lookup transformation runs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cde2c-105">快取連接管理員不支援二進位大型物件 (BLOB) 資料類型 DT_TEXT、DT_NTEXT 和 DT_IMAGE。</span><span class="sxs-lookup"><span data-stu-id="cde2c-105">The Cache connection manager does not support the Binary Large Object (BLOB) data types DT_TEXT, DT_NTEXT, and DT_IMAGE.</span></span> <span data-ttu-id="cde2c-106">如果參考資料集包含 BLOB 資料類型，則在您執行封裝時元件會失敗。</span><span class="sxs-lookup"><span data-stu-id="cde2c-106">If the reference dataset contains a BLOB data type, the component will fail when you run the package.</span></span> <span data-ttu-id="cde2c-107">您可以使用 **[快取連接管理員編輯器]** 修改資料行資料類型。</span><span class="sxs-lookup"><span data-stu-id="cde2c-107">You can use the **Cache Connection Manager Editor** to modify column data types.</span></span> <span data-ttu-id="cde2c-108">如需詳細資訊，請參閱 [快取連線管理員編輯器](../cache-connection-manager-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="cde2c-108">For more information, see [Cache Connection Manager Editor](../cache-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="cde2c-109">查閱轉換會藉由聯結已連接資料來源輸入資料行中的資料與參考資料集中的資料行來執行查閱。</span><span class="sxs-lookup"><span data-stu-id="cde2c-109">The Lookup transformation performs lookups by joining data in input columns from a connected data source with columns in a reference dataset.</span></span> <span data-ttu-id="cde2c-110">如需相關資訊，請參閱 [Lookup Transformation](../data-flow/transformations/lookup-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="cde2c-110">For more information, see [Lookup Transformation](../data-flow/transformations/lookup-transformation.md).</span></span>  
  
 <span data-ttu-id="cde2c-111">您可以使用下列其中一個項目來產生參考資料集：</span><span class="sxs-lookup"><span data-stu-id="cde2c-111">You use one of the following to generate a reference dataset:</span></span>  
  
-   <span data-ttu-id="cde2c-112">快取檔案 (.caw)</span><span class="sxs-lookup"><span data-stu-id="cde2c-112">Cache file (.caw)</span></span>  
  
     <span data-ttu-id="cde2c-113">將快取連接管理員設定為從現有的快取檔案讀取資料。</span><span class="sxs-lookup"><span data-stu-id="cde2c-113">You configure the Cache connection manager to read data from an existing cache file.</span></span>  
  
-   <span data-ttu-id="cde2c-114">資料流程中的已連接資料來源</span><span class="sxs-lookup"><span data-stu-id="cde2c-114">Connected data source in the data flow</span></span>  
  
     <span data-ttu-id="cde2c-115">使用快取轉換，將資料流程中已連接資料來源的資料寫入快取連接管理員。</span><span class="sxs-lookup"><span data-stu-id="cde2c-115">You use a Cache Transform transformation to write data from a connected data source in the data flow to a Cache connection manager.</span></span> <span data-ttu-id="cde2c-116">資料永遠會儲存在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="cde2c-116">The data is always stored in memory.</span></span>  
  
     <span data-ttu-id="cde2c-117">您必須將查閱轉換加入個別的資料流程中。</span><span class="sxs-lookup"><span data-stu-id="cde2c-117">You must add the Lookup transformation to a separate data flow.</span></span> <span data-ttu-id="cde2c-118">如此可在查閱轉換執行之前，先讓快取轉換擴展快取連接管理員。</span><span class="sxs-lookup"><span data-stu-id="cde2c-118">This enables the Cache Transform to populate the Cache connection manager before the Lookup transformation is executed.</span></span> <span data-ttu-id="cde2c-119">資料流程可能位於相同的封裝或兩個不同的封裝。</span><span class="sxs-lookup"><span data-stu-id="cde2c-119">The data flows can be in the same package or in two separate packages.</span></span>  
  
     <span data-ttu-id="cde2c-120">如果資料流程位於相同的封裝，請使用優先順序條件約束來連接資料流程。</span><span class="sxs-lookup"><span data-stu-id="cde2c-120">If the data flows are in the same package, use a precedence constraint to connect the data flows.</span></span> <span data-ttu-id="cde2c-121">如此可在查閱轉換執行之前，先讓快取轉換執行。</span><span class="sxs-lookup"><span data-stu-id="cde2c-121">This enables the Cache Transform to run before the Lookup transformation runs.</span></span>  
  
     <span data-ttu-id="cde2c-122">如果資料流程位於不同的封裝，可以使用執行封裝工作從父封裝呼叫子封裝。</span><span class="sxs-lookup"><span data-stu-id="cde2c-122">If the data flows are in separate packages, you can use the Execute Package task to call the child package from the parent package.</span></span> <span data-ttu-id="cde2c-123">您可以將多個執行封裝工作加入父封裝中的時序容器工作，藉此呼叫多個子封裝。</span><span class="sxs-lookup"><span data-stu-id="cde2c-123">You can call multiple child packages by adding multiple Execute Package tasks to a Sequence Container task in the parent package.</span></span>  
  
 <span data-ttu-id="cde2c-124">您可以藉由使用下列其中一種方法，在多個查閱轉換之間共用儲存在快取中的參考資料集：</span><span class="sxs-lookup"><span data-stu-id="cde2c-124">You can share the reference dataset stored in cache, between multiple Lookup transformations by using one of the following methods:</span></span>  
  
-   <span data-ttu-id="cde2c-125">將單一封裝中的查閱轉換設定為使用相同的快取連接管理員。</span><span class="sxs-lookup"><span data-stu-id="cde2c-125">Configure the Lookup transformations in a single package to use the same Cache connection manager.</span></span>  
  
-   <span data-ttu-id="cde2c-126">將不同封裝中的快取連接管理員設定為使用相同的快取檔案。</span><span class="sxs-lookup"><span data-stu-id="cde2c-126">Configure the Cache connection managers in different packages to use the same cache file.</span></span>  
  
 <span data-ttu-id="cde2c-127">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="cde2c-127">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="cde2c-128">快取轉換</span><span class="sxs-lookup"><span data-stu-id="cde2c-128">Cache Transform</span></span>](../data-flow/transformations/cache-transform.md)  
  
-   [<span data-ttu-id="cde2c-129">快取連線管理員</span><span class="sxs-lookup"><span data-stu-id="cde2c-129">Cache Connection Manager</span></span>](cache-connection-manager.md)  
  
-   [<span data-ttu-id="cde2c-130">優先順序條件約束</span><span class="sxs-lookup"><span data-stu-id="cde2c-130">Precedence Constraints</span></span>](../control-flow/precedence-constraints.md)  
  
-   [<span data-ttu-id="cde2c-131">執行套件工作</span><span class="sxs-lookup"><span data-stu-id="cde2c-131">Execute Package Task</span></span>](../control-flow/execute-package-task.md)  
  
-   [<span data-ttu-id="cde2c-132">時序容器</span><span class="sxs-lookup"><span data-stu-id="cde2c-132">Sequence Container</span></span>](../control-flow/sequence-container.md)  
  
 <span data-ttu-id="cde2c-133">如需示範如何在完整快取模式中使用快取連線管理員實作查閱轉換的影片，請參閱 [如何：在完整快取模式中實作查閱轉換 (SQL Server 影片)](https://go.microsoft.com/fwlink/?LinkId=131031)。</span><span class="sxs-lookup"><span data-stu-id="cde2c-133">For a video that demonstrates how to implement a Lookup transformation in Full Cache mode using the Cache connection manager, see [How to: Implement a Lookup Transformation in Full Cache Mode (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=131031).</span></span>  
  
### <a name="to-implement-a-lookup-transformation-in-full-cache-mode-in-one-package-by-using-cache-connection-manager-and-a-data-source-in-the-data-flow"></a><span data-ttu-id="cde2c-134">若要使用快取連接管理員和資料流程中的資料來源在單一封裝中以完整快取模式實作查閱轉換</span><span class="sxs-lookup"><span data-stu-id="cde2c-134">To implement a Lookup transformation in full cache mode in one package by using Cache connection manager and a data source in the data flow</span></span>  
  
1.  <span data-ttu-id="cde2c-135">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中開啟 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案，然後開啟封裝。</span><span class="sxs-lookup"><span data-stu-id="cde2c-135">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open a [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project, and then open a package.</span></span>  
  
2.  <span data-ttu-id="cde2c-136">在 [控制流程]  索引標籤上加入兩個資料流程工作，然後使用綠色的連接子來連接這些工作：</span><span class="sxs-lookup"><span data-stu-id="cde2c-136">On the **Control Flow** tab, add two Data Flow tasks, and then connect the tasks by using a green connector:</span></span>  
  
3.  <span data-ttu-id="cde2c-137">在第一個資料流程中加入快取轉換轉換，然後將該轉換連接到資料來源。</span><span class="sxs-lookup"><span data-stu-id="cde2c-137">In the first data flow, add a Cache Transform transformation, and then connect the transformation to a data source.</span></span>  
  
     <span data-ttu-id="cde2c-138">視需要設定資料來源。</span><span class="sxs-lookup"><span data-stu-id="cde2c-138">Configure the data source as needed.</span></span>  
  
4.  <span data-ttu-id="cde2c-139">按兩下快取轉換，然後在 [快取轉換編輯器]  中，按一下 [連線管理員]  頁面上的 [新增]  ，建立新的快取連線管理員。</span><span class="sxs-lookup"><span data-stu-id="cde2c-139">Double-click the Cache Transform, and then in the **Cache Transformation Editor**, on the **Connection Manager** page, click **New** to create a new Cache connection manager.</span></span>  
  
5.  <span data-ttu-id="cde2c-140">按一下 [快取連線管理員編輯器] 對話方塊的 [資料行] 索引標籤，然後使用 [索引位置] 選項，指定哪些資料行是索引資料行。</span><span class="sxs-lookup"><span data-stu-id="cde2c-140">Click the **Columns** tab of the **Cache Connection Manager Editor** dialog box, and then specify which columns are the index columns by using the **Index Position** option.</span></span>  
  
     <span data-ttu-id="cde2c-141">如果是非索引資料行，索引位置為 0。</span><span class="sxs-lookup"><span data-stu-id="cde2c-141">For non-index columns, the index position is 0.</span></span> <span data-ttu-id="cde2c-142">如果是索引資料行，則索引位置是循序的正數。</span><span class="sxs-lookup"><span data-stu-id="cde2c-142">For index columns, the index position is a sequential, positive number.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cde2c-143">當查閱轉換是設定為使用快取連接管理員，則只有參考資料集中的索引資料行可以對應到輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="cde2c-143">When the Lookup transformation is configured to use a Cache connection manager, only index columns in the reference dataset can be mapped to input columns.</span></span> <span data-ttu-id="cde2c-144">而且，所有的索引資料行都必須進行對應。</span><span class="sxs-lookup"><span data-stu-id="cde2c-144">Also, all index columns must be mapped.</span></span> <span data-ttu-id="cde2c-145">如需詳細資訊，請參閱 [快取連線管理員編輯器](../cache-connection-manager-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="cde2c-145">For more information, see [Cache Connection Manager Editor](../cache-connection-manager-editor.md).</span></span>  
  
6.  <span data-ttu-id="cde2c-146">若要將快取儲存至檔案，請在 [快取連線管理員編輯器]  的 [一般]  索引標籤上，藉由設定下列選項來設定快取連線管理員：</span><span class="sxs-lookup"><span data-stu-id="cde2c-146">To save the cache to a file, in the **Cache Connection Manager Editor**, on the **General** tab, configure the Cache connection manager by setting the following options:</span></span>  
  
    -   <span data-ttu-id="cde2c-147">選取 [使用檔案快取]  。</span><span class="sxs-lookup"><span data-stu-id="cde2c-147">Select **Use file cache**.</span></span>  
  
    -   <span data-ttu-id="cde2c-148">在 [檔案名稱]  中，輸入檔案路徑或是按一下 [瀏覽]  選取檔案。</span><span class="sxs-lookup"><span data-stu-id="cde2c-148">For **File name**, either type the file path or click **Browse** to select the file.</span></span>  
  
         <span data-ttu-id="cde2c-149">如果輸入的檔案路徑不存在，系統就會在執行封裝時建立該檔案。</span><span class="sxs-lookup"><span data-stu-id="cde2c-149">If you type a path for a file that does not exist, the system creates the file when you run the package.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cde2c-150">封裝保護等級不會套用至快取檔案。</span><span class="sxs-lookup"><span data-stu-id="cde2c-150">The protection level of the package does not apply to the cache file.</span></span> <span data-ttu-id="cde2c-151">如果快取檔案包含機密資訊，請使用存取控制清單 (ACL) 限制對其中儲存檔案的位置或資料夾的存取權。</span><span class="sxs-lookup"><span data-stu-id="cde2c-151">If the cache file contains sensitive information, use an access control list (ACL) to restrict access to the location or folder in which you store the file.</span></span> <span data-ttu-id="cde2c-152">您應該只啟用特定帳戶的存取權。</span><span class="sxs-lookup"><span data-stu-id="cde2c-152">You should enable access only to certain accounts.</span></span> <span data-ttu-id="cde2c-153">如需詳細資訊，請參閱 [對封裝使用之檔案的存取權](../access-to-files-used-by-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="cde2c-153">For more information, see [Access to Files Used by Packages](../access-to-files-used-by-packages.md).</span></span>  
  
7.  <span data-ttu-id="cde2c-154">視需要設定快取轉換。</span><span class="sxs-lookup"><span data-stu-id="cde2c-154">Configure the Cache Transform as needed.</span></span> <span data-ttu-id="cde2c-155">如需詳細資訊，請參閱[快取轉換編輯器 &#40;連線管理員頁面&#41;](../cache-transformation-editor-connection-manager-page.md) 和[快取轉換編輯器 &#40;對應頁面&#41;](../cache-transformation-editor-mappings-page.md)。</span><span class="sxs-lookup"><span data-stu-id="cde2c-155">For more information, see [Cache Transformation Editor &#40;Connection Manager Page&#41;](../cache-transformation-editor-connection-manager-page.md) and [Cache Transformation Editor &#40;Mappings Page&#41;](../cache-transformation-editor-mappings-page.md).</span></span>  
  
8.  <span data-ttu-id="cde2c-156">藉由執行下列工作，在第二個資料流程中加入查閱轉換，然後設定該轉換：</span><span class="sxs-lookup"><span data-stu-id="cde2c-156">In the second data flow, add a Lookup transformation, and then configure the transformation by doing the following tasks:</span></span>  
  
    1.  <span data-ttu-id="cde2c-157">從來源或先前的轉換將連接子拖曳到查閱轉換，以便將查閱轉換連接到資料流程。</span><span class="sxs-lookup"><span data-stu-id="cde2c-157">Connect the Lookup transformation to the data flow by dragging a connector from a source or a previous transformation to the Lookup transformation.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="cde2c-158">查閱轉換如果連接到包含空白日期欄位的一般檔案，則查閱轉換可能不會驗證。</span><span class="sxs-lookup"><span data-stu-id="cde2c-158">A Lookup transformation might not validate if that transformation connects to a flat file that contains an empty date field.</span></span> <span data-ttu-id="cde2c-159">此轉換是否會驗證將取決於一般檔案的連線管理員是否已設定為保留 null 值。</span><span class="sxs-lookup"><span data-stu-id="cde2c-159">Whether the transformation validates depends on whether the connection manager for the flat file has been configured to retain null values.</span></span> <span data-ttu-id="cde2c-160">若要確保查閱轉換會驗證，請在 **[一般檔案來源編輯器]** 的 **[連線管理員]** 頁面上，選取 **[將來源的 Null 值保留為資料流程中的 Null 值]** 選項。</span><span class="sxs-lookup"><span data-stu-id="cde2c-160">To ensure that the Lookup transformation validates, in the **Flat File Source Editor**, on the **Connection Manager Page**, select the **Retain null values from the source as null values in the data flow** option.</span></span>  
  
    2.  <span data-ttu-id="cde2c-161">按兩下來源或前一個轉換以設定元件。</span><span class="sxs-lookup"><span data-stu-id="cde2c-161">Double-click the source or previous transformation to configure the component.</span></span>  
  
    3.  <span data-ttu-id="cde2c-162">按兩下查閱轉換，然後在 [查閱轉換編輯器]  的 [一般]  頁面上，選取 [完整快取]  。</span><span class="sxs-lookup"><span data-stu-id="cde2c-162">Double-click the Lookup transformation, and then in the **Lookup Transformation Editor**, on the **General** page, select **Full cache**.</span></span>  
  
    4.  <span data-ttu-id="cde2c-163">在 [連接類型] 區域中選取 [快取連線管理員]。</span><span class="sxs-lookup"><span data-stu-id="cde2c-163">In the **Connection type** area, select **Cache connection manager**.</span></span>  
  
    5.  <span data-ttu-id="cde2c-164">從 [指定如何處理無相符項目的資料列]  清單中選取錯誤處理選項。</span><span class="sxs-lookup"><span data-stu-id="cde2c-164">From the **Specify how to handle rows with no matching entries** list, select an error handling option.</span></span>  
  
    6.  <span data-ttu-id="cde2c-165">在 [連接]  頁面的 [快取連線管理員]  清單上，選取快取連線管理員。</span><span class="sxs-lookup"><span data-stu-id="cde2c-165">On the **Connection** page, from the **Cache connection manager** list, select a Cache connection manager.</span></span>  
  
    7.  <span data-ttu-id="cde2c-166">按一下 **[資料行]** 頁面，然後從 **[可用的輸入資料行]** 清單，拖曳至少一個資料行至 **[可用的查閱資料行]** 清單中的資料行。</span><span class="sxs-lookup"><span data-stu-id="cde2c-166">Click the **Columns** page, and then drag at least one column from the **Available Input Columns** list to a column in the **Available Lookup Column** list.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="cde2c-167">「查閱」轉換會自動對應具有相同名稱和相同資料類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="cde2c-167">The Lookup transformation automatically maps columns that have the same name and the same data type.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="cde2c-168">資料行必須具有要對應的相符資料類型。</span><span class="sxs-lookup"><span data-stu-id="cde2c-168">Columns must have matching data types to be mapped.</span></span> <span data-ttu-id="cde2c-169">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="cde2c-169">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
    8.  <span data-ttu-id="cde2c-170">在 [可用的查閱資料行]  清單中選取資料行。</span><span class="sxs-lookup"><span data-stu-id="cde2c-170">In the **Available Lookup Columns** list, select columns.</span></span> <span data-ttu-id="cde2c-171">然後在 [查閱作業]  清單中，指定查閱資料行的值是否要取代輸入資料行中的值，或要寫入至新的資料行。</span><span class="sxs-lookup"><span data-stu-id="cde2c-171">Then in the **Lookup Operation** list, specify whether the values from the lookup columns replace values in the input column or are written to a new column.</span></span>  
  
    9. <span data-ttu-id="cde2c-172">若要設定錯誤輸出，按一下 **[錯誤輸出]** 頁面，然後設定錯誤處理選項。</span><span class="sxs-lookup"><span data-stu-id="cde2c-172">To configure the error output, click the **Error Output** page and set the error handling options.</span></span> <span data-ttu-id="cde2c-173">如需詳細資訊，請參閱[查閱轉換編輯器 &#40;錯誤輸出頁面&#41;](../lookup-transformation-editor-error-output-page.md)。</span><span class="sxs-lookup"><span data-stu-id="cde2c-173">For more information, see [Lookup Transformation Editor &#40;Error Output Page&#41;](../lookup-transformation-editor-error-output-page.md).</span></span>  
  
    10. <span data-ttu-id="cde2c-174">按一下 [確定]  ，將變更儲存至查閱轉換。</span><span class="sxs-lookup"><span data-stu-id="cde2c-174">Click **OK** to save your changes to the Lookup transformation.</span></span>  
  
9. <span data-ttu-id="cde2c-175">執行封裝。</span><span class="sxs-lookup"><span data-stu-id="cde2c-175">Run the package.</span></span>  
  
### <a name="to-implement-a-lookup-transformation-in-full-cache-mode-in-two-packages-by-using-cache-connection-manager-and-a-data-source-in-the-data-flow"></a><span data-ttu-id="cde2c-176">使用快取連接管理員和資料流程中的資料來源在兩個封裝中以完整快取模式實作查閱轉換</span><span class="sxs-lookup"><span data-stu-id="cde2c-176">To implement a Lookup transformation in full cache mode in two packages by using Cache connection manager and a data source in the data flow</span></span>  
  
1.  <span data-ttu-id="cde2c-177">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中開啟 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案，然後開啟兩個封裝。</span><span class="sxs-lookup"><span data-stu-id="cde2c-177">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open a [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project, and then open two packages.</span></span>  
  
2.  <span data-ttu-id="cde2c-178">在每個封裝的 [控制流程] 索引標籤上，加入資料流程工作。</span><span class="sxs-lookup"><span data-stu-id="cde2c-178">On the Control Flow tab in each package, add a Data Flow task.</span></span>  
  
3.  <span data-ttu-id="cde2c-179">在父封裝中，將快取轉換轉換加入至資料流程，然後將該轉換連接到資料來源。</span><span class="sxs-lookup"><span data-stu-id="cde2c-179">In the parent package, add a Cache Transform transformation to the data flow, and then connect the transformation to a data source.</span></span>  
  
     <span data-ttu-id="cde2c-180">視需要設定資料來源。</span><span class="sxs-lookup"><span data-stu-id="cde2c-180">Configure the data source as needed.</span></span>  
  
4.  <span data-ttu-id="cde2c-181">按兩下快取轉換，然後在 [快取轉換編輯器]  中，按一下 [連線管理員]  頁面上的 [新增]  ，建立新的快取連線管理員。</span><span class="sxs-lookup"><span data-stu-id="cde2c-181">Double-click the Cache Transform, and then in the **Cache Transformation Editor**, on the **Connection Manager** page, click **New** to create a new Cache connection manager.</span></span>  
  
5.  <span data-ttu-id="cde2c-182">在 [快取連線管理員編輯器]  的 [一般]  索引標籤上，藉由設定下列選項來設定快取連線管理員：</span><span class="sxs-lookup"><span data-stu-id="cde2c-182">In the **Cache Connection Manager Editor**, on the **General** tab, configure the Cache connection manager by setting the following options:</span></span>  
  
    -   <span data-ttu-id="cde2c-183">選取 [使用檔案快取]  。</span><span class="sxs-lookup"><span data-stu-id="cde2c-183">Select **Use file cache**.</span></span>  
  
    -   <span data-ttu-id="cde2c-184">在 [檔案名稱]  中，輸入檔案路徑或是按一下 [瀏覽]  選取檔案。</span><span class="sxs-lookup"><span data-stu-id="cde2c-184">For **File name**, either type the file path or click **Browse** to select the file.</span></span>  
  
         <span data-ttu-id="cde2c-185">如果輸入的檔案路徑不存在，系統就會在執行封裝時建立該檔案。</span><span class="sxs-lookup"><span data-stu-id="cde2c-185">If you type a path for a file that does not exist, the system creates the file when you run the package.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cde2c-186">封裝保護等級不會套用至快取檔案。</span><span class="sxs-lookup"><span data-stu-id="cde2c-186">The protection level of the package does not apply to the cache file.</span></span> <span data-ttu-id="cde2c-187">如果快取檔案包含機密資訊，請使用存取控制清單 (ACL) 限制對其中儲存檔案的位置或資料夾的存取權。</span><span class="sxs-lookup"><span data-stu-id="cde2c-187">If the cache file contains sensitive information, use an access control list (ACL) to restrict access to the location or folder in which you store the file.</span></span> <span data-ttu-id="cde2c-188">您應該只啟用特定帳戶的存取權。</span><span class="sxs-lookup"><span data-stu-id="cde2c-188">You should enable access only to certain accounts.</span></span> <span data-ttu-id="cde2c-189">如需詳細資訊，請參閱 [對封裝使用之檔案的存取權](../access-to-files-used-by-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="cde2c-189">For more information, see [Access to Files Used by Packages](../access-to-files-used-by-packages.md).</span></span>  
  
6.  <span data-ttu-id="cde2c-190">按一下 [資料行]  索引標籤，然後使用 [索引位置]  選項，指定哪些資料行是索引資料行。</span><span class="sxs-lookup"><span data-stu-id="cde2c-190">Click the **Columns** tab, and then specify which columns are the index columns by using the **Index Position** option.</span></span>  
  
     <span data-ttu-id="cde2c-191">如果是非索引資料行，索引位置為 0。</span><span class="sxs-lookup"><span data-stu-id="cde2c-191">For non-index columns, the index position is 0.</span></span> <span data-ttu-id="cde2c-192">如果是索引資料行，則索引位置是循序的正數。</span><span class="sxs-lookup"><span data-stu-id="cde2c-192">For index columns, the index position is a sequential, positive number.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cde2c-193">當查閱轉換是設定為使用快取連接管理員，則只有參考資料集中的索引資料行可以對應到輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="cde2c-193">When the Lookup transformation is configured to use a Cache connection manager, only index columns in the reference dataset can be mapped to input columns.</span></span> <span data-ttu-id="cde2c-194">而且，所有的索引資料行都必須進行對應。</span><span class="sxs-lookup"><span data-stu-id="cde2c-194">Also, all index columns must be mapped.</span></span> <span data-ttu-id="cde2c-195">如需詳細資訊，請參閱 [快取連線管理員編輯器](../cache-connection-manager-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="cde2c-195">For more information, see [Cache Connection Manager Editor](../cache-connection-manager-editor.md).</span></span>  
  
7.  <span data-ttu-id="cde2c-196">視需要設定快取轉換。</span><span class="sxs-lookup"><span data-stu-id="cde2c-196">Configure the Cache Transform as needed.</span></span> <span data-ttu-id="cde2c-197">如需詳細資訊，請參閱[快取轉換編輯器 &#40;連線管理員頁面&#41;](../cache-transformation-editor-connection-manager-page.md) 和[快取轉換編輯器 &#40;對應頁面&#41;](../cache-transformation-editor-mappings-page.md)。</span><span class="sxs-lookup"><span data-stu-id="cde2c-197">For more information, see [Cache Transformation Editor &#40;Connection Manager Page&#41;](../cache-transformation-editor-connection-manager-page.md) and [Cache Transformation Editor &#40;Mappings Page&#41;](../cache-transformation-editor-mappings-page.md).</span></span>  
  
8.  <span data-ttu-id="cde2c-198">請執行下列其中一項作業，以擴展用於第二個封裝中的快取連接管理員：</span><span class="sxs-lookup"><span data-stu-id="cde2c-198">Do one of the following to populate the Cache connection manager that is used in the second package:</span></span>  
  
    -   <span data-ttu-id="cde2c-199">執行父封裝。</span><span class="sxs-lookup"><span data-stu-id="cde2c-199">Run the parent package.</span></span>  
  
    -   <span data-ttu-id="cde2c-200">按兩下在步驟 4 中所建立的快取連線管理員，再按一下 [資料行]  ，選取資料列，然後按下 CTRL+C 來複製資料行中繼資料。</span><span class="sxs-lookup"><span data-stu-id="cde2c-200">Double-click the Cache connection manager you created in step 4, click **Columns**, select the rows, and then press CTRL+C to copy the column metadata.</span></span>  
  
9. <span data-ttu-id="cde2c-201">在子封裝中，以滑鼠右鍵按一下 [連線管理員] 區域，然後按一下 [新增連接]，在 [加入 SSIS 連線管理員] 對話方塊中選取 [CACHE]，然後按一下 [加入]，藉此建立快取連線管理員。</span><span class="sxs-lookup"><span data-stu-id="cde2c-201">In the child package, create a Cache connection manager by right-clicking in the **Connection Managers** area, clicking **New Connection**, selecting **CACHE** in the **Add SSIS Connection Manager** dialog box, and then clicking **Add**.</span></span>  
  
     <span data-ttu-id="cde2c-202">[連線管理員] 區域會出現在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 設計師的 [控制流程]、[資料流程] 和 [事件處理常式] 索引標籤底部。</span><span class="sxs-lookup"><span data-stu-id="cde2c-202">The **Connection Managers** area appears on the bottom of the **Control Flow**, **Data Flow**, and **Event Handlers** tabs of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Designer.</span></span>  
  
10. <span data-ttu-id="cde2c-203">在 [快取連線管理員編輯器]  的 [一般]  索引標籤上，藉由設定下列選項，將快取連線管理員設定為從選取的快取檔案讀取資料：</span><span class="sxs-lookup"><span data-stu-id="cde2c-203">In the **Cache Connection Manager Editor**, on the **General** tab, configure the Cache connection manager to read the data from the cache file that you selected by setting the following options:</span></span>  
  
    -   <span data-ttu-id="cde2c-204">選取 [使用檔案快取]  。</span><span class="sxs-lookup"><span data-stu-id="cde2c-204">Select **Use file cache**.</span></span>  
  
    -   <span data-ttu-id="cde2c-205">在 [檔案名稱]  中，輸入檔案路徑或是按一下 [瀏覽]  選取檔案。</span><span class="sxs-lookup"><span data-stu-id="cde2c-205">For **File name**, either type the file path or click **Browse** to select the file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cde2c-206">封裝保護等級不會套用至快取檔案。</span><span class="sxs-lookup"><span data-stu-id="cde2c-206">The protection level of the package does not apply to the cache file.</span></span> <span data-ttu-id="cde2c-207">如果快取檔案包含機密資訊，請使用存取控制清單 (ACL) 限制對其中儲存檔案的位置或資料夾的存取權。</span><span class="sxs-lookup"><span data-stu-id="cde2c-207">If the cache file contains sensitive information, use an access control list (ACL) to restrict access to the location or folder in which you store the file.</span></span> <span data-ttu-id="cde2c-208">您應該只啟用特定帳戶的存取權。</span><span class="sxs-lookup"><span data-stu-id="cde2c-208">You should enable access only to certain accounts.</span></span> <span data-ttu-id="cde2c-209">如需詳細資訊，請參閱 [對封裝使用之檔案的存取權](../access-to-files-used-by-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="cde2c-209">For more information, see [Access to Files Used by Packages](../access-to-files-used-by-packages.md).</span></span>  
  
11. <span data-ttu-id="cde2c-210">如果已在步驟 8 中複製了資料行中繼資料，請按一下 [資料行]  ，選取空白資料列，然後按下 CTRL+V 來貼上資料行中繼資料。</span><span class="sxs-lookup"><span data-stu-id="cde2c-210">If you copied the column metadata in step 8, click **Columns**, select the empty row, and then press CTRL+V to paste the column metadata.</span></span>  
  
12. <span data-ttu-id="cde2c-211">藉由執行下列工作加入查閱轉換，然後設定該轉換：</span><span class="sxs-lookup"><span data-stu-id="cde2c-211">Add a Lookup transformation, and then configure the transformation by doing the following:</span></span>  
  
    1.  <span data-ttu-id="cde2c-212">從來源或先前的轉換將連接子拖曳到查閱轉換，以便將查閱轉換連接到資料流程。</span><span class="sxs-lookup"><span data-stu-id="cde2c-212">Connect the Lookup transformation to the data flow by dragging a connector from a source or a previous transformation to the Lookup transformation.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="cde2c-213">查閱轉換如果連接到包含空白日期欄位的一般檔案，則查閱轉換可能不會驗證。</span><span class="sxs-lookup"><span data-stu-id="cde2c-213">A Lookup transformation might not validate if that transformation connects to a flat file that contains an empty date field.</span></span> <span data-ttu-id="cde2c-214">此轉換是否會驗證將取決於一般檔案的連線管理員是否已設定為保留 null 值。</span><span class="sxs-lookup"><span data-stu-id="cde2c-214">Whether the transformation validates depends on whether the connection manager for the flat file has been configured to retain null values.</span></span> <span data-ttu-id="cde2c-215">若要確保查閱轉換會驗證，請在 **[一般檔案來源編輯器]** 的 **[連線管理員]** 頁面上，選取 **[將來源的 Null 值保留為資料流程中的 Null 值]** 選項。</span><span class="sxs-lookup"><span data-stu-id="cde2c-215">To ensure that the Lookup transformation validates, in the **Flat File Source Editor**, on the **Connection Manager Page**, select the **Retain null values from the source as null values in the data flow** option.</span></span>  
  
    2.  <span data-ttu-id="cde2c-216">按兩下來源或前一個轉換以設定元件。</span><span class="sxs-lookup"><span data-stu-id="cde2c-216">Double-click the source or previous transformation to configure the component.</span></span>  
  
    3.  <span data-ttu-id="cde2c-217">按兩下 [查閱轉換]，然後在 [查閱轉換編輯器] 的 [一般] 頁面上，選取 [完整快取]。</span><span class="sxs-lookup"><span data-stu-id="cde2c-217">Double-click the Lookup transformation, and then select **Full cache** on the **General** page of the **Lookup Transformation Editor**.</span></span>  
  
    4.  <span data-ttu-id="cde2c-218">在 [連接類型] 區域中選取 [快取連線管理員]。</span><span class="sxs-lookup"><span data-stu-id="cde2c-218">Select **Cache connection manager** in the **Connection type** area.</span></span>  
  
    5.  <span data-ttu-id="cde2c-219">從 [指定如何處理無相符項目的資料列]  清單，針對沒有相符項目的資料列選取錯誤處理選項。</span><span class="sxs-lookup"><span data-stu-id="cde2c-219">Select an error handling option for rows without matching entries from the **Specify how to handle rows with no matching entries** list.</span></span>  
  
    6.  <span data-ttu-id="cde2c-220">在 [連接]  頁面的 [快取連線管理員]  清單上，選取您加入的快取連線管理員。</span><span class="sxs-lookup"><span data-stu-id="cde2c-220">On the **Connection** page, from the **Cache connection manager** list, select the Cache connection manager that you added.</span></span>  
  
    7.  <span data-ttu-id="cde2c-221">按一下 **[資料行]** 頁面，然後從 **[可用的輸入資料行]** 清單，拖曳至少一個資料行至 **[可用的查閱資料行]** 清單中的資料行。</span><span class="sxs-lookup"><span data-stu-id="cde2c-221">Click the **Columns** page, and then drag at least one column from the **Available Input Columns** list to a column in the **Available Lookup Column** list.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="cde2c-222">「查閱」轉換會自動對應具有相同名稱和相同資料類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="cde2c-222">The Lookup transformation automatically maps columns that have the same name and the same data type.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="cde2c-223">資料行必須具有要對應的相符資料類型。</span><span class="sxs-lookup"><span data-stu-id="cde2c-223">Columns must have matching data types to be mapped.</span></span> <span data-ttu-id="cde2c-224">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="cde2c-224">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
    8.  <span data-ttu-id="cde2c-225">在 [可用的查閱資料行]  清單中選取資料行。</span><span class="sxs-lookup"><span data-stu-id="cde2c-225">In the **Available Lookup Columns** list, select columns.</span></span> <span data-ttu-id="cde2c-226">然後在 [查閱作業]  清單中，指定查閱資料行的值是否要取代輸入資料行中的值，或要寫入至新的資料行。</span><span class="sxs-lookup"><span data-stu-id="cde2c-226">Then in the **Lookup Operation** list, specify whether the values from the lookup columns replace values in the input column or are written to a new column.</span></span>  
  
    9. <span data-ttu-id="cde2c-227">若要設定錯誤輸出，按一下 **[錯誤輸出]** 頁面，然後設定錯誤處理選項。</span><span class="sxs-lookup"><span data-stu-id="cde2c-227">To configure the error output, click the **Error Output** page and set the error handling options.</span></span> <span data-ttu-id="cde2c-228">如需詳細資訊，請參閱[查閱轉換編輯器 &#40;錯誤輸出頁面&#41;](../lookup-transformation-editor-error-output-page.md)。</span><span class="sxs-lookup"><span data-stu-id="cde2c-228">For more information, see [Lookup Transformation Editor &#40;Error Output Page&#41;](../lookup-transformation-editor-error-output-page.md).</span></span>  
  
    10. <span data-ttu-id="cde2c-229">按一下 [確定]  ，將變更儲存至查閱轉換。</span><span class="sxs-lookup"><span data-stu-id="cde2c-229">Click **OK** to save your changes to the Lookup transformation.</span></span>  
  
13. <span data-ttu-id="cde2c-230">開啟父封裝，在控制流程中加入執行封裝工作，然後將工作設定為呼叫子封裝。</span><span class="sxs-lookup"><span data-stu-id="cde2c-230">Open the parent package, add an Execute Package task to the control flow, and then configure the task to call the child package.</span></span> <span data-ttu-id="cde2c-231">如需詳細資訊，請參閱 [執行封裝工作](../control-flow/execute-package-task.md)。</span><span class="sxs-lookup"><span data-stu-id="cde2c-231">For more information, see [Execute Package Task](../control-flow/execute-package-task.md).</span></span>  
  
14. <span data-ttu-id="cde2c-232">執行封裝。</span><span class="sxs-lookup"><span data-stu-id="cde2c-232">Run the packages.</span></span>  
  
### <a name="to-implement-a-lookup-transformation-in-full-cache-mode-by-using-cache-connection-manager-and-an-existing-cache-file"></a><span data-ttu-id="cde2c-233">使用快取連接管理員和現有的快取檔案以完整快取模式實作查閱轉換</span><span class="sxs-lookup"><span data-stu-id="cde2c-233">To implement a Lookup transformation in full cache mode by using Cache connection manager and an existing cache file</span></span>  
  
1.  <span data-ttu-id="cde2c-234">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中開啟 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案，然後開啟封裝。</span><span class="sxs-lookup"><span data-stu-id="cde2c-234">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open a [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project, and then open a package.</span></span>  
  
2.  <span data-ttu-id="cde2c-235">以滑鼠右鍵按一下 [連線管理員]  區域，然後按一下 [新增連接]  。</span><span class="sxs-lookup"><span data-stu-id="cde2c-235">Right-click in the **Connection Managers** area, and then click **New Connection**.</span></span>  
  
     <span data-ttu-id="cde2c-236">[連線管理員] 區域會出現在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 設計師的 [控制流程]、[資料流程] 和 [事件處理常式] 索引標籤底部。</span><span class="sxs-lookup"><span data-stu-id="cde2c-236">The **Connection Managers** area appears on the bottom of the **Control Flow**, **Data Flow**, and **Event Handlers** tabs of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Designer.</span></span>  
  
3.  <span data-ttu-id="cde2c-237">在 [加入 SSIS 連線管理員]  對話方塊中選取 [CACHE]  ，然後按一下 [加入]  加入快取連線管理員。</span><span class="sxs-lookup"><span data-stu-id="cde2c-237">In the **Add SSIS Connection Manager** dialog box, select **CACHE**, and then click **Add** to add a Cache connection manager.</span></span>  
  
4.  <span data-ttu-id="cde2c-238">按兩下 [快取連線管理員]，開啟 [快取連線管理員編輯器]  。</span><span class="sxs-lookup"><span data-stu-id="cde2c-238">Double-click the Cache connection manager to open the **Cache Connection Manager Editor**.</span></span>  
  
5.  <span data-ttu-id="cde2c-239">在 [快取連線管理員編輯器]  的 [一般]  索引標籤上，藉由設定下列選項來設定快取連線管理員：</span><span class="sxs-lookup"><span data-stu-id="cde2c-239">In the **Cache Connection Manager Editor**, on the **General** tab, configure the Cache connection manager by setting the following options:</span></span>  
  
    -   <span data-ttu-id="cde2c-240">選取 [使用檔案快取]  。</span><span class="sxs-lookup"><span data-stu-id="cde2c-240">Select **Use file cache**.</span></span>  
  
    -   <span data-ttu-id="cde2c-241">在 [檔案名稱]  中，輸入檔案路徑或是按一下 [瀏覽]  選取檔案。</span><span class="sxs-lookup"><span data-stu-id="cde2c-241">For **File name**, either type the file path or click **Browse** to select the file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cde2c-242">封裝保護等級不會套用至快取檔案。</span><span class="sxs-lookup"><span data-stu-id="cde2c-242">The protection level of the package does not apply to the cache file.</span></span> <span data-ttu-id="cde2c-243">如果快取檔案包含機密資訊，請使用存取控制清單 (ACL) 限制對其中儲存檔案的位置或資料夾的存取權。</span><span class="sxs-lookup"><span data-stu-id="cde2c-243">If the cache file contains sensitive information, use an access control list (ACL) to restrict access to the location or folder in which you store the file.</span></span> <span data-ttu-id="cde2c-244">您應該只啟用特定帳戶的存取權。</span><span class="sxs-lookup"><span data-stu-id="cde2c-244">You should enable access only to certain accounts.</span></span> <span data-ttu-id="cde2c-245">如需詳細資訊，請參閱 [對封裝使用之檔案的存取權](../access-to-files-used-by-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="cde2c-245">For more information, see [Access to Files Used by Packages](../access-to-files-used-by-packages.md).</span></span>  
  
6.  <span data-ttu-id="cde2c-246">按一下 [資料行]  索引標籤，然後使用 [索引位置]  選項，指定哪些資料行是索引資料行。</span><span class="sxs-lookup"><span data-stu-id="cde2c-246">Click the **Columns** tab, and then specify which columns are the index columns by using the **Index Position** option.</span></span>  
  
     <span data-ttu-id="cde2c-247">如果是非索引資料行，索引位置為 0。</span><span class="sxs-lookup"><span data-stu-id="cde2c-247">For non-index columns, the index position is 0.</span></span> <span data-ttu-id="cde2c-248">如果是索引資料行，則索引位置是循序的正數。</span><span class="sxs-lookup"><span data-stu-id="cde2c-248">For index columns, the index position is a sequential, positive number.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cde2c-249">當查閱轉換是設定為使用快取連接管理員，則只有參考資料集中的索引資料行可以對應到輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="cde2c-249">When the Lookup transformation is configured to use a Cache connection manager, only index columns in the reference dataset can be mapped to input columns.</span></span> <span data-ttu-id="cde2c-250">而且，所有的索引資料行都必須進行對應。</span><span class="sxs-lookup"><span data-stu-id="cde2c-250">Also, all index columns must be mapped.</span></span> <span data-ttu-id="cde2c-251">如需詳細資訊，請參閱 [快取連線管理員編輯器](../cache-connection-manager-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="cde2c-251">For more information, see [Cache Connection Manager Editor](../cache-connection-manager-editor.md).</span></span>  
  
7.  <span data-ttu-id="cde2c-252">在 [控制流程]  索引標籤上，將資料流程工作加入封裝，然後將查閱轉換加入資料流程。</span><span class="sxs-lookup"><span data-stu-id="cde2c-252">On the **Control Flow** tab, add a Data Flow task to the package, and then add a Lookup transformation to the data flow.</span></span>  
  
8.  <span data-ttu-id="cde2c-253">您可以利用下列方式設定查閱轉換：</span><span class="sxs-lookup"><span data-stu-id="cde2c-253">Configure the Lookup transformation by doing the following:</span></span>  
  
    1.  <span data-ttu-id="cde2c-254">從來源或先前的轉換將連接子拖曳到查閱轉換，以便將查閱轉換連接到資料流程。</span><span class="sxs-lookup"><span data-stu-id="cde2c-254">Connect the Lookup transformation to the data flow by dragging a connector from a source or a previous transformation to the Lookup transformation.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="cde2c-255">查閱轉換如果連接到包含空白日期欄位的一般檔案，則查閱轉換可能不會驗證。</span><span class="sxs-lookup"><span data-stu-id="cde2c-255">A Lookup transformation might not validate if that transformation connects to a flat file that contains an empty date field.</span></span> <span data-ttu-id="cde2c-256">此轉換是否會驗證將取決於一般檔案的連線管理員是否已設定為保留 null 值。</span><span class="sxs-lookup"><span data-stu-id="cde2c-256">Whether the transformation validates depends on whether the connection manager for the flat file has been configured to retain null values.</span></span> <span data-ttu-id="cde2c-257">若要確保查閱轉換會驗證，請在 **[一般檔案來源編輯器]** 的 **[連線管理員]** 頁面上，選取 **[將來源的 Null 值保留為資料流程中的 Null 值]** 選項。</span><span class="sxs-lookup"><span data-stu-id="cde2c-257">To ensure that the Lookup transformation validates, in the **Flat File Source Editor**, on the **Connection Manager Page**, select the **Retain null values from the source as null values in the data flow** option.</span></span>  
  
    2.  <span data-ttu-id="cde2c-258">按兩下來源或前一個轉換以設定元件。</span><span class="sxs-lookup"><span data-stu-id="cde2c-258">Double-click the source or previous transformation to configure the component.</span></span>  
  
    3.  <span data-ttu-id="cde2c-259">按兩下查閱轉換，然後在 [查閱轉換編輯器]  的 [一般]  頁面上，選取 [完整快取]  。</span><span class="sxs-lookup"><span data-stu-id="cde2c-259">Double-click the Lookup transformation, and then in the **Lookup Transformation Editor**, on the **General** page, select **Full cache**.</span></span>  
  
    4.  <span data-ttu-id="cde2c-260">在 [連接類型] 區域中選取 [快取連線管理員]。</span><span class="sxs-lookup"><span data-stu-id="cde2c-260">Select **Cache connection manager** in the **Connection type** area.</span></span>  
  
    5.  <span data-ttu-id="cde2c-261">從 [指定如何處理無相符項目的資料列]  清單，針對沒有相符項目的資料列選取錯誤處理選項。</span><span class="sxs-lookup"><span data-stu-id="cde2c-261">Select an error handling option for rows without matching entries from the **Specify how to handle rows with no matching entries** list.</span></span>  
  
    6.  <span data-ttu-id="cde2c-262">在 [連接]  頁面的 [快取連線管理員]  清單上，選取您加入的快取連線管理員。</span><span class="sxs-lookup"><span data-stu-id="cde2c-262">On the **Connection** page, from the **Cache connection manager** list, select the Cache connection manager that you added.</span></span>  
  
    7.  <span data-ttu-id="cde2c-263">按一下 **[資料行]** 頁面，然後從 **[可用的輸入資料行]** 清單，拖曳至少一個資料行至 **[可用的查閱資料行]** 清單中的資料行。</span><span class="sxs-lookup"><span data-stu-id="cde2c-263">Click the **Columns** page, and then drag at least one column from the **Available Input Columns** list to a column in the **Available Lookup Column** list.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="cde2c-264">「查閱」轉換會自動對應具有相同名稱和相同資料類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="cde2c-264">The Lookup transformation automatically maps columns that have the same name and the same data type.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="cde2c-265">資料行必須具有要對應的相符資料類型。</span><span class="sxs-lookup"><span data-stu-id="cde2c-265">Columns must have matching data types to be mapped.</span></span> <span data-ttu-id="cde2c-266">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="cde2c-266">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
    8.  <span data-ttu-id="cde2c-267">在 [可用的查閱資料行]  清單中選取資料行。</span><span class="sxs-lookup"><span data-stu-id="cde2c-267">In the **Available Lookup Columns** list, select columns.</span></span> <span data-ttu-id="cde2c-268">然後在 [查閱作業]  清單中，指定查閱資料行的值是否要取代輸入資料行中的值，或要寫入至新的資料行。</span><span class="sxs-lookup"><span data-stu-id="cde2c-268">Then in the **Lookup Operation** list, specify whether the values from the lookup columns replace values in the input column or are written to a new column.</span></span>  
  
    9. <span data-ttu-id="cde2c-269">若要設定錯誤輸出，按一下 **[錯誤輸出]** 頁面，然後設定錯誤處理選項。</span><span class="sxs-lookup"><span data-stu-id="cde2c-269">To configure the error output, click the **Error Output** page and set the error handling options.</span></span> <span data-ttu-id="cde2c-270">如需詳細資訊，請參閱[查閱轉換編輯器 &#40;錯誤輸出頁面&#41;](../lookup-transformation-editor-error-output-page.md)。</span><span class="sxs-lookup"><span data-stu-id="cde2c-270">For more information, see [Lookup Transformation Editor &#40;Error Output Page&#41;](../lookup-transformation-editor-error-output-page.md).</span></span>  
  
    10. <span data-ttu-id="cde2c-271">按一下 [確定]  ，將變更儲存至查閱轉換。</span><span class="sxs-lookup"><span data-stu-id="cde2c-271">Click **OK** to save your changes to the Lookup transformation.</span></span>  
  
9. <span data-ttu-id="cde2c-272">執行封裝。</span><span class="sxs-lookup"><span data-stu-id="cde2c-272">Run the package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cde2c-273">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cde2c-273">See Also</span></span>  
 <span data-ttu-id="cde2c-274">[使用 OLE DB 連線管理員以完整快取模式來實作查閱轉換](lookup-transformation-full-cache-mode-ole-db-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="cde2c-274">[Implement a Lookup Transformation in Full Cache Mode Using the OLE DB Connection Manager](lookup-transformation-full-cache-mode-ole-db-connection-manager.md) </span></span>  
 <span data-ttu-id="cde2c-275">[以沒有快取或部分快取模式來實作查閱](../data-flow/transformations/implement-a-lookup-in-no-cache-or-partial-cache-mode.md) </span><span class="sxs-lookup"><span data-stu-id="cde2c-275">[Implement a Lookup in No Cache or Partial Cache Mode](../data-flow/transformations/implement-a-lookup-in-no-cache-or-partial-cache-mode.md) </span></span>  
 [<span data-ttu-id="cde2c-276">Integration Services 轉換</span><span class="sxs-lookup"><span data-stu-id="cde2c-276">Integration Services Transformations</span></span>](../data-flow/transformations/integration-services-transformations.md)  
  
  
