---
title: 使用 OLE DB 連線管理員，以完整快取模式來執行查閱轉換 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Lookup transformation [Integration Services]
ms.assetid: c4150e1b-bdff-4f7a-af4c-3401c34def83
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f77a753dd71bc487d57492371906fc48bc114357
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599145"
---
# <a name="implement-a-lookup-transformation-in-full-cache-mode-using-the-ole-db-connection-manager"></a><span data-ttu-id="ced08-102">使用 OLE DB 連接管理員，以完整快取模式來實作查閱轉換</span><span class="sxs-lookup"><span data-stu-id="ced08-102">Implement a Lookup Transformation in Full Cache Mode Using the OLE DB Connection Manager</span></span>
  <span data-ttu-id="ced08-103">您可以將查閱轉換設定為使用完整快取模式以及 OLE DB 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="ced08-103">You can configure the Lookup transformation to use full cache mode and an OLE DB connection manager.</span></span> <span data-ttu-id="ced08-104">在完整快取模式中，參考資料集會在查閱轉換執行之前載入快取。</span><span class="sxs-lookup"><span data-stu-id="ced08-104">In the full cache mode, the reference dataset is loaded into cache before the Lookup transformation runs.</span></span>  
  
 <span data-ttu-id="ced08-105">查閱轉換會藉由聯結已連接資料來源輸入資料行中的資料與參考資料集中的資料行來執行查閱。</span><span class="sxs-lookup"><span data-stu-id="ced08-105">The Lookup transformation performs lookups by joining data in input columns from a connected data source with columns in a reference dataset.</span></span> <span data-ttu-id="ced08-106">如需相關資訊，請參閱 [Lookup Transformation](../data-flow/transformations/lookup-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="ced08-106">For more information, see [Lookup Transformation](../data-flow/transformations/lookup-transformation.md).</span></span>  
  
 <span data-ttu-id="ced08-107">當您將查閱轉換設定為使用 OLE DB 連接管理員時，可以選取資料表、檢視或 SQL 查詢來產生參考資料集。</span><span class="sxs-lookup"><span data-stu-id="ced08-107">When you configure the Lookup transformation to use an OLE DB connection manager, you select a table, view, or SQL query to generate the reference dataset.</span></span>  
  
### <a name="to-implement-a-lookup-transformation-in-full-cache-mode-by-using-ole-db-connection-manager"></a><span data-ttu-id="ced08-108">使用 OLE DB 連接管理員以完整快取模式實作查閱轉換</span><span class="sxs-lookup"><span data-stu-id="ced08-108">To implement a Lookup transformation in full cache mode by using OLE DB connection manager</span></span>  
  
1.  <span data-ttu-id="ced08-109">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案，然後在 [方案總管] 中按兩下該封裝。</span><span class="sxs-lookup"><span data-stu-id="ced08-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want, and then double-click the package in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="ced08-110">在 **[資料流程]** 索引標籤中，將查閱轉換從 **[工具箱]** 拖曳至設計介面。</span><span class="sxs-lookup"><span data-stu-id="ced08-110">On the **Data Flow** tab, from the **Toolbox**, drag the Lookup transformation to the design surface.</span></span>  
  
3.  <span data-ttu-id="ced08-111">從來源或先前的轉換將連接子拖曳到查閱轉換，以便將查閱轉換連接到資料流程。</span><span class="sxs-lookup"><span data-stu-id="ced08-111">Connect the Lookup transformation to the data flow by dragging a connector from a source or a previous transformation to the Lookup transformation.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ced08-112">查閱轉換如果連接到包含空白日期欄位的一般檔案，則查閱轉換可能不會驗證。</span><span class="sxs-lookup"><span data-stu-id="ced08-112">A Lookup transformation might not validate if that transformation connects to a flat file that contains an empty date field.</span></span> <span data-ttu-id="ced08-113">此轉換是否會驗證將取決於一般檔案的連線管理員是否已設定為保留 null 值。</span><span class="sxs-lookup"><span data-stu-id="ced08-113">Whether the transformation validates depends on whether the connection manager for the flat file has been configured to retain null values.</span></span> <span data-ttu-id="ced08-114">若要確保查閱轉換會驗證，請在 **[一般檔案來源編輯器]** 的 **[連線管理員]** 頁面上，選取 **[將來源的 Null 值保留為資料流程中的 Null 值]** 選項。</span><span class="sxs-lookup"><span data-stu-id="ced08-114">To ensure that the Lookup transformation validates, in the **Flat File Source Editor**, on the **Connection Manager Page**, select the **Retain null values from the source as null values in the data flow** option.</span></span>  
  
4.  <span data-ttu-id="ced08-115">按兩下來源或前一個轉換以設定元件。</span><span class="sxs-lookup"><span data-stu-id="ced08-115">Double-click the source or previous transformation to configure the component.</span></span>  
  
5.  <span data-ttu-id="ced08-116">按兩下查閱轉換，然後在 [查閱轉換編輯器]  的 [一般]  頁面上，選取 [完整快取]  。</span><span class="sxs-lookup"><span data-stu-id="ced08-116">Double-click the Lookup transformation, and then in the **Lookup Transformation Editor**, on the **General** page, select **Full cache**.</span></span>  
  
6.  <span data-ttu-id="ced08-117">在 **[連接類型]** 區域中，選取 **[OLE DB 連接管理員]** 。</span><span class="sxs-lookup"><span data-stu-id="ced08-117">In the **Connection type** area, select **OLE DB connection manager**.</span></span>  
  
7.  <span data-ttu-id="ced08-118">在 **[指定如何處理無相符項目的資料列]** 清單中，針對沒有相符項目的資料列選取錯誤處理選項。</span><span class="sxs-lookup"><span data-stu-id="ced08-118">In the **Specify how to handle rows with no matching entries** list, select an error handling option for rows without matching entries.</span></span>  
  
8.  <span data-ttu-id="ced08-119">在 [連接] 頁面上，從 **[OLE DB 連接管理員]** 清單中選取連接管理員，或按一下 **[新增]** 建立新的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="ced08-119">On the Connection page, select a connection manager from the **OLE DB connection manager** list or click **New** to create a new connection manager.</span></span> <span data-ttu-id="ced08-120">如需相關資訊，請參閱 [OLE DB Connection Manager](ole-db-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="ced08-120">For more information, see [OLE DB Connection Manager](ole-db-connection-manager.md).</span></span>  
  
9. <span data-ttu-id="ced08-121">執行下列其中一項工作：</span><span class="sxs-lookup"><span data-stu-id="ced08-121">Do one of the following tasks:</span></span>  
  
    -   <span data-ttu-id="ced08-122">按一下 **[使用資料表或檢視]** ，然後選取資料表或檢視，或按一下 **[新增]** 建立資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="ced08-122">Click **Use a table or a view**, and then either select a table or view, or click **New** to create a table or view.</span></span>  
  
         <span data-ttu-id="ced08-123">-或-</span><span class="sxs-lookup"><span data-stu-id="ced08-123">-or-</span></span>  
  
    -   <span data-ttu-id="ced08-124">按一下 **[使用 SQL 查詢的結果]** ，然後在 **[SQL 命令]** 視窗中建立查詢，或是按一下 **[建立查詢]** ，使用 **[查詢產生器]** 提供的圖形工具來建立查詢。</span><span class="sxs-lookup"><span data-stu-id="ced08-124">Click **Use results of an SQL query**, and then build a query in the **SQL Command** window, or click **Build Query** to build a query by using the graphical tools that the **Query Builder** provides.</span></span>  
  
         <span data-ttu-id="ced08-125">-或-</span><span class="sxs-lookup"><span data-stu-id="ced08-125">-or-</span></span>  
  
    -   <span data-ttu-id="ced08-126">或者，按一下 **[瀏覽]** ，從檔案匯入 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ced08-126">Alternatively, click **Browse** to import an SQL statement from a file.</span></span>  
  
     <span data-ttu-id="ced08-127">若要驗證 SQL 查詢，請按一下 **[剖析查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="ced08-127">To validate the SQL query, click **Parse Query**.</span></span>  
  
     <span data-ttu-id="ced08-128">若要檢視資料範例，按一下 **[預覽]** 。</span><span class="sxs-lookup"><span data-stu-id="ced08-128">To view a sample of the data, click **Preview**.</span></span>  
  
10. <span data-ttu-id="ced08-129">按一下 **[資料行]** 頁面，然後從 **[可用的輸入資料行]** 清單，拖曳至少一個資料行至 **[可用的查閱資料行]** 清單中的資料行。</span><span class="sxs-lookup"><span data-stu-id="ced08-129">Click the **Columns** page, and then from the **Available Input Columns** list, drag at least one column to a column in the **Available Lookup Column** list.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ced08-130">「查閱」轉換會自動對應具有相同名稱和相同資料類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="ced08-130">The Lookup transformation automatically maps columns that have the same name and the same data type.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ced08-131">資料行必須具有要對應的相符資料類型。</span><span class="sxs-lookup"><span data-stu-id="ced08-131">Columns must have matching data types to be mapped.</span></span> <span data-ttu-id="ced08-132">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="ced08-132">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
11. <span data-ttu-id="ced08-133">執行下列工作，以便在輸出中包含查閱資料行：</span><span class="sxs-lookup"><span data-stu-id="ced08-133">Include lookup columns in the output by doing the following tasks:</span></span>  
  
    1.  <span data-ttu-id="ced08-134">在 **[可用的查閱資料行]** 清單中。</span><span class="sxs-lookup"><span data-stu-id="ced08-134">In the **Available Lookup Columns** list.</span></span> <span data-ttu-id="ced08-135">選取資料行。</span><span class="sxs-lookup"><span data-stu-id="ced08-135">select columns.</span></span>  
  
    2.  <span data-ttu-id="ced08-136">在 **[查閱作業]** 清單中，指定查閱資料行的值要取代輸入資料行中的值，還是要寫入至新的資料行。</span><span class="sxs-lookup"><span data-stu-id="ced08-136">In **Lookup Operation** list, specify whether the values from the lookup columns replace values in the input column or are written to a new column.</span></span>  
  
12. <span data-ttu-id="ced08-137">若要設定錯誤輸出，按一下 **[錯誤輸出]** 頁面，然後設定錯誤處理選項。</span><span class="sxs-lookup"><span data-stu-id="ced08-137">To configure the error output, click the **Error Output** page and set the error handling options.</span></span> <span data-ttu-id="ced08-138">如需詳細資訊，請參閱[查閱轉換編輯器 &#40;錯誤輸出頁面&#41;](../lookup-transformation-editor-error-output-page.md)。</span><span class="sxs-lookup"><span data-stu-id="ced08-138">For more information, see [Lookup Transformation Editor &#40;Error Output Page&#41;](../lookup-transformation-editor-error-output-page.md).</span></span>  
  
13. <span data-ttu-id="ced08-139">按一下 **[確定]** ，將變更儲存至查閱轉換，然後再執行封裝。</span><span class="sxs-lookup"><span data-stu-id="ced08-139">Click **OK** to save your changes to the Lookup transformation, and then run the package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ced08-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ced08-140">See Also</span></span>  
 <span data-ttu-id="ced08-141">[使用快取連線管理員以完整快取模式來實作查閱轉換](lookup-transformation-full-cache-mode-ole-db-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="ced08-141">[Implement a Lookup Transformation in Full Cache Mode Using the Cache Connection Manager](lookup-transformation-full-cache-mode-ole-db-connection-manager.md) </span></span>  
 <span data-ttu-id="ced08-142">[以沒有快取或部分快取模式來實作查閱](../data-flow/transformations/implement-a-lookup-in-no-cache-or-partial-cache-mode.md) </span><span class="sxs-lookup"><span data-stu-id="ced08-142">[Implement a Lookup in No Cache or Partial Cache Mode](../data-flow/transformations/implement-a-lookup-in-no-cache-or-partial-cache-mode.md) </span></span>  
 [<span data-ttu-id="ced08-143">Integration Services 轉換</span><span class="sxs-lookup"><span data-stu-id="ced08-143">Integration Services Transformations</span></span>](../data-flow/transformations/integration-services-transformations.md)  
  
  
