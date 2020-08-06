---
title: 使用模糊群組轉換來識別相似的資料列 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Fuzzy Grouping transformation
- match similar data [Integration Services]
- similar data rows [Integration Services]
- fuzzy matches
ms.assetid: ffcb41a6-e23d-49ea-8c32-ac980e3dc495
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4e6d49548c211b38a35d6f5f7efc3d50fec93588
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599107"
---
# <a name="identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation"></a><span data-ttu-id="c786e-102">使用模糊群組轉換來識別相似的資料列</span><span class="sxs-lookup"><span data-stu-id="c786e-102">Identify Similar Data Rows by Using the Fuzzy Grouping Transformation</span></span>
  <span data-ttu-id="c786e-103">若要加入和設定「模糊群組」轉換，封裝必須至少包含一個「資料流程」工作和一個來源。</span><span class="sxs-lookup"><span data-stu-id="c786e-103">To add and configure a Fuzzy Grouping transformation, the package must already include at least one Data Flow task and a source.</span></span>  
  
### <a name="to-implement-fuzzy-grouping-transformation-in-a-data-flow"></a><span data-ttu-id="c786e-104">在資料流程中實作「模糊群組」轉換</span><span class="sxs-lookup"><span data-stu-id="c786e-104">To implement Fuzzy Grouping transformation in a data flow</span></span>  
  
1.  <span data-ttu-id="c786e-105">在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="c786e-105">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="c786e-106">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="c786e-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="c786e-107">按一下 [資料流程]  索引標籤，然後將「模糊群組」轉換從 [工具箱]  拖曳到設計介面。</span><span class="sxs-lookup"><span data-stu-id="c786e-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the Fuzzy Grouping transformation to the design surface.</span></span>  
  
4.  <span data-ttu-id="c786e-108">將連接子從資料來源或前一轉換拖曳至「模糊群組」轉換，以便將「模糊群組」轉換連接到資料流程。</span><span class="sxs-lookup"><span data-stu-id="c786e-108">Connect the Fuzzy Grouping transformation to the data flow by dragging the connector from the data source or a previous transformation to the Fuzzy Grouping transformation.</span></span>  
  
5.  <span data-ttu-id="c786e-109">按兩下「模糊群組」轉換。</span><span class="sxs-lookup"><span data-stu-id="c786e-109">Double-click the Fuzzy Grouping transformation.</span></span>  
  
6.  <span data-ttu-id="c786e-110">在 [模糊群組轉換編輯器]  對話方塊的 [連線管理員]  索引標籤上，選取連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫的 OLE DB 連線管理員。</span><span class="sxs-lookup"><span data-stu-id="c786e-110">In the **Fuzzy Grouping Transformation Editor** dialog box, on the **Connection Manager** tab, select an OLE DB connection manager that connects to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c786e-111">該轉換需要到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫的連接，以建立暫存資料表和索引。</span><span class="sxs-lookup"><span data-stu-id="c786e-111">The transformation requires a connection to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database to create temporary tables and indexes.</span></span>  
  
7.  <span data-ttu-id="c786e-112">按一下 [資料行]  索引標籤，並在 [可用的輸入資料行]  清單中，選取用於識別資料集中相似資料列之輸入資料行的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="c786e-112">Click the **Columns** tab and, in the **Available Input Columns** list, select the check box of the input columns to use to identify similar rows in the dataset.</span></span>  
  
8.  <span data-ttu-id="c786e-113">選取 [通過]  資料行中的核取方塊，以識別要傳遞至轉換輸出的輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="c786e-113">Select the check box in the **Pass Through** column to identify the input columns to pass through to the transformation output.</span></span> <span data-ttu-id="c786e-114">重複資料列的識別處理中未包含傳遞資料行。</span><span class="sxs-lookup"><span data-stu-id="c786e-114">Pass-through columns are not included in the process of identification of duplicate rows.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c786e-115">用於群組的輸入資料行會自動選取為傳遞資料行，並且在用於群組時，無法取消對它們的選取。</span><span class="sxs-lookup"><span data-stu-id="c786e-115">Input columns that are used for grouping are automatically selected as pass-through columns, and they cannot be unselected while used for grouping.</span></span>  
  
9. <span data-ttu-id="c786e-116">(選擇性) 在 [輸出別名]  資料行中更新輸出資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="c786e-116">Optionally, update the names of output columns in the **Output Alias** column.</span></span>  
  
10. <span data-ttu-id="c786e-117">(選擇性) 在 [群組輸出別名]  資料行中更新已清除資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="c786e-117">Optionally, update the names of cleaned columns in the **Group OutputAlias** column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c786e-118">資料行的預設名稱是具有 "_clean" 後置詞之輸入資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="c786e-118">The default names of columns are the names of the input columns with a "_clean" suffix.</span></span>  
  
11. <span data-ttu-id="c786e-119">(選擇性) 在 [比對類型]  資料行中更新要使用的比對類型。</span><span class="sxs-lookup"><span data-stu-id="c786e-119">Optionally, update the type of match to use in the **Match Type** column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c786e-120">至少一個資料行必須使用模糊比對。</span><span class="sxs-lookup"><span data-stu-id="c786e-120">At least one column must use fuzzy matching.</span></span>  
  
12. <span data-ttu-id="c786e-121">在 [最小相似度]  資料行中指定最小相似度層級資料行。</span><span class="sxs-lookup"><span data-stu-id="c786e-121">Specify the minimum similarity level columns in the **Minimum Similarity** column.</span></span> <span data-ttu-id="c786e-122">值長度必須介於 0 到 1 之間。</span><span class="sxs-lookup"><span data-stu-id="c786e-122">The value must be between 0 and 1.</span></span> <span data-ttu-id="c786e-123">值愈接近 1，必須形成群組之輸入資料行中的值會愈相似。</span><span class="sxs-lookup"><span data-stu-id="c786e-123">The closer the value is to 1, the more similar the values in the input columns must be to form a group.</span></span> <span data-ttu-id="c786e-124">最小相似度 1 表示完全相符。</span><span class="sxs-lookup"><span data-stu-id="c786e-124">A minimum similarity of 1 indicates an exact match.</span></span>  
  
13. <span data-ttu-id="c786e-125">(選擇性) 在 [相似度輸出別名]  資料行中更新相似度資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="c786e-125">Optionally, update the names of similarity columns in the **Similarity Output Alias** column.</span></span>  
  
14. <span data-ttu-id="c786e-126">若要指定資料值中數字的處理方式，請更新 [數字]  資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="c786e-126">To specify the handling of numbers in data values, update the values in the **Numerals** column.</span></span>  
  
15. <span data-ttu-id="c786e-127">若要指定如何將轉換與資料行中的字串資料進行比較，請修改 [比較旗標]  資料行中之比較選項的預設選擇。</span><span class="sxs-lookup"><span data-stu-id="c786e-127">To specify how the transformation compares the string data in a column, modify the default selection of comparison options in the **Comparison Flags** column.</span></span>  
  
16. <span data-ttu-id="c786e-128">按一下 [進階]  索引標籤，以修改資料行的名稱，轉換會將這些資料行加入唯一資料列識別碼 (_key_in)、重複資料列識別碼 (_key_out) 和相似度值 (_score) 的輸出。</span><span class="sxs-lookup"><span data-stu-id="c786e-128">Click the **Advanced** tab to modify the names of the columns that the transformation adds to the output for the unique row identifier (_key_in), the duplicate row identifier (_key_out), and the similarity value (_score).</span></span>  
  
17. <span data-ttu-id="c786e-129">(選擇性) 藉由移動滑動軸來調整相似度臨界值。</span><span class="sxs-lookup"><span data-stu-id="c786e-129">Optionally, adjust the similarity threshold by moving the slider bar.</span></span>  
  
18. <span data-ttu-id="c786e-130">(選擇性) 清除 Token 分隔符號核取方塊，以忽略資料中的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="c786e-130">Optionally, clear the token delimiter check boxes to ignore delimiters in the data.</span></span>  
  
19. <span data-ttu-id="c786e-131">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="c786e-131">Click **OK**.</span></span>  
  
20. <span data-ttu-id="c786e-132">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="c786e-132">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c786e-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c786e-133">See Also</span></span>  
 <span data-ttu-id="c786e-134">[Fuzzy Grouping Transformation](fuzzy-grouping-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="c786e-134">[Fuzzy Grouping Transformation](fuzzy-grouping-transformation.md) </span></span>  
 <span data-ttu-id="c786e-135">[Integration Services 轉換](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="c786e-135">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 <span data-ttu-id="c786e-136">[Integration Services 路徑](../integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="c786e-136">[Integration Services Paths](../integration-services-paths.md) </span></span>  
 [<span data-ttu-id="c786e-137">資料流程工作</span><span class="sxs-lookup"><span data-stu-id="c786e-137">Data Flow Task</span></span>](../../control-flow/data-flow-task.md)  
  
  
