---
title: 資料採礦查詢 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataminingquery.f1
ms.assetid: 948e358a-6245-429f-82c7-4cedc5e048fd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 657e4e173815fa25458e296f7eadb3d4d0696a02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596856"
---
# <a name="data-mining-query"></a><span data-ttu-id="26156-102">資料採礦查詢</span><span class="sxs-lookup"><span data-stu-id="26156-102">Data Mining Query</span></span>
  <span data-ttu-id="26156-103">設計窗格包含資料採礦預測查詢產生器，您可以使用該產生器來建立資料採礦預測查詢。</span><span class="sxs-lookup"><span data-stu-id="26156-103">The design pane contains the data mining prediction query builder, which you can use to build data mining prediction queries.</span></span> <span data-ttu-id="26156-104">您可以依據輸入資料表來設計預測查詢，或設計單一預測查詢。</span><span class="sxs-lookup"><span data-stu-id="26156-104">You can design either prediction queries based on input tables, or singleton prediction queries.</span></span> <span data-ttu-id="26156-105">切換到結果檢視以執行查詢並檢視結果。</span><span class="sxs-lookup"><span data-stu-id="26156-105">Switch to the result view to run the query and view the results.</span></span> <span data-ttu-id="26156-106">查詢檢視會顯示預測查詢產生器所建立的資料採礦延伸模組 (DMX) 查詢。</span><span class="sxs-lookup"><span data-stu-id="26156-106">The query view displays the Data Mining Extensions (DMX) query created by the prediction query builder.</span></span>  
  
## <a name="options"></a><span data-ttu-id="26156-107">選項。</span><span class="sxs-lookup"><span data-stu-id="26156-107">Options</span></span>  
 <span data-ttu-id="26156-108">切換檢視按鈕</span><span class="sxs-lookup"><span data-stu-id="26156-108">Switch view button</span></span>  
 <span data-ttu-id="26156-109">按一下圖示，即可在設計與查詢窗格之間切換。</span><span class="sxs-lookup"><span data-stu-id="26156-109">Click an icon to switch between the design and query pane.</span></span> <span data-ttu-id="26156-110">預設會開啟設計窗格。</span><span class="sxs-lookup"><span data-stu-id="26156-110">By default, the design pane is open.</span></span>  
  
 <span data-ttu-id="26156-111">若要切換到設計窗格，請按一下 ![設計圖示](../media/ssis-designicon.gif "設計圖示") 圖示。</span><span class="sxs-lookup"><span data-stu-id="26156-111">To switch to the design pane, click the ![Design icon](../media/ssis-designicon.gif "Design icon") icon.</span></span>  
  
 <span data-ttu-id="26156-112">若要切換到查詢窗格，請按一下 ![SQL 圖示](../media/ssis-queryicon.gif "SQL 圖示") 圖示。</span><span class="sxs-lookup"><span data-stu-id="26156-112">To switch to the query pane, click the ![SQL icon](../media/ssis-queryicon.gif "SQL icon") icon.</span></span>  
  
 <span data-ttu-id="26156-113">**採礦模型**</span><span class="sxs-lookup"><span data-stu-id="26156-113">**Mining Model**</span></span>  
 <span data-ttu-id="26156-114">顯示選取的採礦模型，並以此模型作為預測的基礎。</span><span class="sxs-lookup"><span data-stu-id="26156-114">Displays the selected mining model on which you want to base predictions.</span></span>  
  
 <span data-ttu-id="26156-115">**選取模型**</span><span class="sxs-lookup"><span data-stu-id="26156-115">**Select Model**</span></span>  
 <span data-ttu-id="26156-116">開啟 [選取採礦模型]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="26156-116">Opens the **Select Mining Model** dialog box.</span></span>  
  
 <span data-ttu-id="26156-117">**輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="26156-117">**Input Columns**</span></span>  
 <span data-ttu-id="26156-118">顯示用來產生預測之選取的輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="26156-118">Displays the selected input columns used to generate the predictions.</span></span>  
  
 <span data-ttu-id="26156-119">**Source**</span><span class="sxs-lookup"><span data-stu-id="26156-119">**Source**</span></span>  
 <span data-ttu-id="26156-120">從下拉式清單中，選取包含您將用於資料行之欄位的來源。</span><span class="sxs-lookup"><span data-stu-id="26156-120">Select the source containing the field that you will use for the column from the dropdown list.</span></span> <span data-ttu-id="26156-121">您可以使用在 [採礦模型]  資料表中選取的採礦模型、在 [選取輸入資料表]  資料表中選取的輸入資料表、預測函數或自訂運算式。</span><span class="sxs-lookup"><span data-stu-id="26156-121">You can either use the mining model selected in the **Mining Model** table, the input table(s) selected in the **Select Input Table(s)** table, a prediction function, or a custom expression.</span></span>  
  
 <span data-ttu-id="26156-122">可以將資料行從包含採礦模型和輸入資料行的資料表，拖曳至資料格。</span><span class="sxs-lookup"><span data-stu-id="26156-122">Columns can be dragged from the tables containing the mining model and input columns to the cell.</span></span>  
  
 <span data-ttu-id="26156-123">**欄位**</span><span class="sxs-lookup"><span data-stu-id="26156-123">**Field**</span></span>  
 <span data-ttu-id="26156-124">從衍生自來源資料表的資料行清單中，選取一個資料行。</span><span class="sxs-lookup"><span data-stu-id="26156-124">Select a column from the list of columns derived from the source table.</span></span> <span data-ttu-id="26156-125">如果在 [來源] 中選取 [預測函數]，則此資料格會包含選取的採礦模型可用之預測函數的下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="26156-125">If you selected **Prediction Function** in **Source**, this cell contains a drop-down list of the prediction functions available for the selected mining model.</span></span>  
  
 <span data-ttu-id="26156-126">**別名**</span><span class="sxs-lookup"><span data-stu-id="26156-126">**Alias**</span></span>  
 <span data-ttu-id="26156-127">伺服器所傳回之資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="26156-127">The name of the column returned by the server.</span></span>  
  
 <span data-ttu-id="26156-128">**顯示**</span><span class="sxs-lookup"><span data-stu-id="26156-128">**Show**</span></span>  
 <span data-ttu-id="26156-129">選取即可傳回資料行或只使用 WHERE 子句中的資料行。</span><span class="sxs-lookup"><span data-stu-id="26156-129">Select to return the column or to only use the column in the WHERE clause.</span></span>  
  
 <span data-ttu-id="26156-130">**群組**</span><span class="sxs-lookup"><span data-stu-id="26156-130">**Group**</span></span>  
 <span data-ttu-id="26156-131">配合 [及/或]  資料行，即可將運算式群組在一起。</span><span class="sxs-lookup"><span data-stu-id="26156-131">Use with the **And/Or** column to group expressions together.</span></span> <span data-ttu-id="26156-132">例如 (expr1 OR expr2) AND expr3。</span><span class="sxs-lookup"><span data-stu-id="26156-132">For example, (expr1 OR expr2) AND expr3.</span></span>  
  
 <span data-ttu-id="26156-133">**及/或**</span><span class="sxs-lookup"><span data-stu-id="26156-133">**And/Or**</span></span>  
 <span data-ttu-id="26156-134">用於建立邏輯查詢。</span><span class="sxs-lookup"><span data-stu-id="26156-134">Use to create a logical query.</span></span> <span data-ttu-id="26156-135">例如 (expr1 OR expr2) AND expr3。</span><span class="sxs-lookup"><span data-stu-id="26156-135">For example, (expr1 OR expr2) AND expr3.</span></span>  
  
 <span data-ttu-id="26156-136">**準則/引數**</span><span class="sxs-lookup"><span data-stu-id="26156-136">**Criteria/Argument**</span></span>  
 <span data-ttu-id="26156-137">指定套用至資料行的條件或使用者運算式。</span><span class="sxs-lookup"><span data-stu-id="26156-137">Specify a condition or user expression that applies to the column.</span></span> <span data-ttu-id="26156-138">可以將資料行從包含採礦模型和輸入資料行的資料表，拖曳至資料格。</span><span class="sxs-lookup"><span data-stu-id="26156-138">Columns can be dragged from the tables containing the mining model and input columns to the cell.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26156-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26156-139">See Also</span></span>  
 <span data-ttu-id="26156-140">[資料採礦查詢介面](https://docs.microsoft.com/analysis-services/data-mining/data-mining-query-tools) </span><span class="sxs-lookup"><span data-stu-id="26156-140">[Data Mining Query Interfaces](https://docs.microsoft.com/analysis-services/data-mining/data-mining-query-tools) </span></span>  
 [<span data-ttu-id="26156-141">資料採礦延伸模組 &#40;DMX&#41; 陳述式參考</span><span class="sxs-lookup"><span data-stu-id="26156-141">Data Mining Extensions &#40;DMX&#41; Statement Reference</span></span>](/sql/dmx/data-mining-extensions-dmx-statements)  
  
  
