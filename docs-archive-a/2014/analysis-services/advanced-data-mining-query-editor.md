---
title: 先進資料採礦查詢編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 27e7fc46-689d-43a4-9647-1c27d182bdd6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2aadf4df75b1ccf6001ad8e97d589ce5666f56ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593241"
---
# <a name="advanced-data-mining-query-editor"></a><span data-ttu-id="6e152-102">進階資料採礦查詢編輯器</span><span class="sxs-lookup"><span data-stu-id="6e152-102">Advanced Data Mining Query Editor</span></span>
  <span data-ttu-id="6e152-103">**資料採礦查詢進階編輯器**是一種工具，可協助您建立自訂模型和查詢。</span><span class="sxs-lookup"><span data-stu-id="6e152-103">The **Data Mining Query Advanced Editor** is a tool to help you build custom models and queries.</span></span>  
  
 <span data-ttu-id="6e152-104">此編輯器提供一組範本，其中包含可點按的連結。</span><span class="sxs-lookup"><span data-stu-id="6e152-104">The editor provides a set of templates with clickable links.</span></span> <span data-ttu-id="6e152-105">只需要按一下每個連結，然後使用對話方塊來選取物件或值，以建立複雜的資料採礦延伸模組 (DMX) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="6e152-105">Just click each link, and use the dialog boxes to select objects or values and build complex Data Mining Extensions (DMX) statements.</span></span> <span data-ttu-id="6e152-106">您可以將檢視切換至文字編輯模式，以手動修改 DMX 陳述式。</span><span class="sxs-lookup"><span data-stu-id="6e152-106">You can switch the view to text editing model to modify the DMX statement manually.</span></span>  
  
 <span data-ttu-id="6e152-107">若要取得**資料採礦查詢進階編輯器**，請按一下 [**查詢**]，然後按一下 [ **Advanced**]。</span><span class="sxs-lookup"><span data-stu-id="6e152-107">To get to the **Data Mining Query Advanced Editor**, click **Query** and then click **Advanced**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="6e152-108">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="6e152-108">UI element list</span></span>  
 <span data-ttu-id="6e152-109">**DMX 查詢窗格**</span><span class="sxs-lookup"><span data-stu-id="6e152-109">**DMX Query pane**</span></span>  
 <span data-ttu-id="6e152-110">您可以在此查看目前的 DMX 陳述式。</span><span class="sxs-lookup"><span data-stu-id="6e152-110">Here you can see the current DMX statement.</span></span>  
  
 <span data-ttu-id="6e152-111">用滑鼠右鍵按一下窗格即可複製目前的 DMX 陳述式。</span><span class="sxs-lookup"><span data-stu-id="6e152-111">Right-click in the pane to copy the current DMX statement.</span></span>  
  
 <span data-ttu-id="6e152-112">您可以按一下陳述式的任何反白顯示部分，以取得該子句特定的選項。</span><span class="sxs-lookup"><span data-stu-id="6e152-112">You can click any highlighted part of the statement to get options specific to that clause.</span></span> <span data-ttu-id="6e152-113">例如，若要刪除、加入或編輯輸出，請在連結上按一下滑鼠右鍵 **\<Output>** 。</span><span class="sxs-lookup"><span data-stu-id="6e152-113">For example, to delete, add, or edit an output, right-click the **\<Output>** link.</span></span>  
  
 <span data-ttu-id="6e152-114">**編輯查詢/查詢產生器**</span><span class="sxs-lookup"><span data-stu-id="6e152-114">**Edit Query/Query Builder**</span></span>  
 <span data-ttu-id="6e152-115">使用此按鈕可在文字編輯器之間切換編輯器，您可以在其中直接撰寫 DMX 語句;和**查詢**產生器，可協助您建立 DMX 語句。</span><span class="sxs-lookup"><span data-stu-id="6e152-115">Use this button to switch the editor between a text editor, where you can write DMX statements directly; and the **Query Builder**, which helps you build a DMX statement.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6e152-116">**警告：** 如果您在執行查詢之前切換 views，則會出現一則訊息，指出您可能會遺失某些變更。</span><span class="sxs-lookup"><span data-stu-id="6e152-116">**Warning:** If you switch views before the query has been run, a message appears stating that you might lose some changes.</span></span> <span data-ttu-id="6e152-117">如果 DMX 語句有效，在許多情況下，**查詢**產生器可能會成功轉換這些變更。</span><span class="sxs-lookup"><span data-stu-id="6e152-117">If the DMX statement is valid, in many cases the **Query Builder** might successfully convert these changes.</span></span> <span data-ttu-id="6e152-118">不過，如果您建立了特別複雜的 DMX 陳述式，則請務必先儲存您的工作，然後再切換檢視。</span><span class="sxs-lookup"><span data-stu-id="6e152-118">However, if you have built a particularly complex DMX statement, you should definitely save your work before switching views.</span></span>  
  
 <span data-ttu-id="6e152-119">**DMX 範本**</span><span class="sxs-lookup"><span data-stu-id="6e152-119">**DMX Templates**</span></span>  
 <span data-ttu-id="6e152-120">按一下此選項，並從包含 DMX 範例的範本清單中選取。</span><span class="sxs-lookup"><span data-stu-id="6e152-120">Click and select from a list of templates that contain DMX examples.</span></span> <span data-ttu-id="6e152-121">這些範本提供您可能需要的所有模型或預測查詢類型，包括使用巢狀資料表的查詢，以及用於管理模型的 DMX 陳述式。</span><span class="sxs-lookup"><span data-stu-id="6e152-121">The templates provide just about every type of model or prediction query that you might need, including queries that use nested tables, and DMX statements to manage models.</span></span> <span data-ttu-id="6e152-122">即使您對 DMX 已有部分了解，這些範本仍可確保語法正確，節省您的時間。</span><span class="sxs-lookup"><span data-stu-id="6e152-122">Even if you know some DMX, the templates can save you time by getting the syntax right.</span></span>  
  
 <span data-ttu-id="6e152-123">**選擇模型**</span><span class="sxs-lookup"><span data-stu-id="6e152-123">**Choose Model**</span></span>  
 <span data-ttu-id="6e152-124">按一下即可檢視目前連接可用的資料採礦模型清單。</span><span class="sxs-lookup"><span data-stu-id="6e152-124">Click to view a list of data mining models available on the current connection.</span></span>  
  
 <span data-ttu-id="6e152-125">您也可以在 [ **Dmx 查詢**] 窗格的 dmx 語句中，按一下模型名稱，以顯示可用的模型清單。</span><span class="sxs-lookup"><span data-stu-id="6e152-125">You can also display a list of available models by clicking on the model name in the DMX statement in the **DMX Query** pane.</span></span> <span data-ttu-id="6e152-126">模型名稱通常會以紅色反白顯示。</span><span class="sxs-lookup"><span data-stu-id="6e152-126">The model name is typically highlighted in red.</span></span>  
  
 <span data-ttu-id="6e152-127">**選取輸入**</span><span class="sxs-lookup"><span data-stu-id="6e152-127">**Select Input**</span></span>  
 <span data-ttu-id="6e152-128">按一下即可選擇要做為採礦模型之輸入的資料。</span><span class="sxs-lookup"><span data-stu-id="6e152-128">Click to choose the data to use as input to the mining model.</span></span> <span data-ttu-id="6e152-129">如果沒有指定資料來源，您也可以按一下 [ **\<Input>** **DMX 查詢**] 窗格中以紅色反白顯示的連結。</span><span class="sxs-lookup"><span data-stu-id="6e152-129">If no data source has been specified, you can also click the **\<Input>** link, which is highlighted in red in the **DMX Query** pane.</span></span>  
  
 <span data-ttu-id="6e152-130">從下拉式清單中選取 [ \*\* \@ InputRowset\*\* ]，以開啟 [**取代 InputRowset** ] 對話方塊，並修改現有的輸入。</span><span class="sxs-lookup"><span data-stu-id="6e152-130">Select **\@InputRowset** from the dropdown list to open the **Replace InputRowset** dialog box and modify an existing input.</span></span>  
  
 <span data-ttu-id="6e152-131">選取 [**新增輸入**] 以開啟 [**加入輸入**] 對話方塊，並指定新的資料來源。</span><span class="sxs-lookup"><span data-stu-id="6e152-131">Select **Add Input** to open the **Add Input** dialog box and specify a new data source.</span></span>  
  
 <span data-ttu-id="6e152-132">您也可以按一下 [ \*\* \@ InputRowset\*\* ] 連結（在 [DMX 查詢] 窗格中以紅色反白顯示）來修改現有的輸入。</span><span class="sxs-lookup"><span data-stu-id="6e152-132">You can also modify an existing input by clicking the **\@InputRowset** link, which is highlighted in red in the DMX Query pane.</span></span>  
  
 <span data-ttu-id="6e152-133">**對應資料行**</span><span class="sxs-lookup"><span data-stu-id="6e152-133">**Map Columns**</span></span>  
 <span data-ttu-id="6e152-134">從採礦模型中選取資料行，然後將這些資料行對應至外部資料來源中的資料行。</span><span class="sxs-lookup"><span data-stu-id="6e152-134">Select columns from the mining model and then map them to columns in the external data source.</span></span>  
  
 <span data-ttu-id="6e152-135">您也可以按一下 **\<Mapping>** [DMX 查詢] 窗格中反白顯示的連結。</span><span class="sxs-lookup"><span data-stu-id="6e152-135">You can also click the highlighted **\<Mapping>** link in the DMX Query pane.</span></span>  
  
 <span data-ttu-id="6e152-136">**加入輸出**</span><span class="sxs-lookup"><span data-stu-id="6e152-136">**Add Output**</span></span>  
 <span data-ttu-id="6e152-137">按一下即可選擇應輸出成為預測查詢一部分的資料行。</span><span class="sxs-lookup"><span data-stu-id="6e152-137">Click to choose the columns that should be output as part of a prediction query.</span></span>  
  
 <span data-ttu-id="6e152-138">您也可以按一下 **\<Add Output>** [DMX 查詢] 窗格中反白顯示的連結。</span><span class="sxs-lookup"><span data-stu-id="6e152-138">You can also click the highlighted **\<Add Output>** link in the DMX Query pane.</span></span>  
  
 <span data-ttu-id="6e152-139">**模型資料行**</span><span class="sxs-lookup"><span data-stu-id="6e152-139">**Model Columns**</span></span>  
 <span data-ttu-id="6e152-140">列出選取之採礦模型中的資料行。</span><span class="sxs-lookup"><span data-stu-id="6e152-140">Lists the columns in the selected mining model.</span></span> <span data-ttu-id="6e152-141">資料行名稱旁的菱形表示資料行是可預測資料行。</span><span class="sxs-lookup"><span data-stu-id="6e152-141">A diamond mark next to the column name indicates that the column is a predictable column.</span></span>  
  
 <span data-ttu-id="6e152-142">**輸入資料行**</span><span class="sxs-lookup"><span data-stu-id="6e152-142">**Input Columns**</span></span>  
 <span data-ttu-id="6e152-143">列出外部資料來源中已加入做為輸入的資料行。</span><span class="sxs-lookup"><span data-stu-id="6e152-143">Lists the columns from the external data source that have been added as inputs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e152-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e152-144">See Also</span></span>  
 [<span data-ttu-id="6e152-145">查詢 &#40;SQL Server 資料採礦增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="6e152-145">Query &#40;SQL Server Data Mining Add-ins&#41;</span></span>](query-sql-server-data-mining-add-ins.md)  
  
  
