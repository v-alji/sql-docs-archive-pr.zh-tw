---
title: 流覽資料來源視圖中的資料 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- exploring data [Analysis Services]
- data source views [Analysis Services], exploring data
- viewing source data
ms.assetid: 2c922c35-fbcb-45b2-96b1-c7a846d8b419
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6adf9edecd807158ba1d0de3287cccd6fa8dd787
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607110"
---
# <a name="explore-data-in-a-data-source-view-analysis-services"></a><span data-ttu-id="1f76c-102">在資料來源檢視中瀏覽資料 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="1f76c-102">Explore Data in a Data Source View (Analysis Services)</span></span>
  <span data-ttu-id="1f76c-103">您可以在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 的資料來源檢視設計師中使用 [瀏覽資料]\*\*\*\* 對話方塊，瀏覽資料來源檢視 (DSV) 中之資料表、檢視或具名查詢的資料。</span><span class="sxs-lookup"><span data-stu-id="1f76c-103">You can use the **Explore Data** dialog box in Data Source View Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to browse data for a table, view, or named query in a data source view (DSV).</span></span> <span data-ttu-id="1f76c-104">當您在資料來源檢視設計師中瀏覽資料時，可以檢視選定資料表、檢視或具名查詢中每一個資料行的內容。</span><span class="sxs-lookup"><span data-stu-id="1f76c-104">When you explore the data in Data Source View Designer, you can view the contents of each column of data in a selected table, view, or named query.</span></span> <span data-ttu-id="1f76c-105">檢視實際內容可協助您判斷是否需要所有的資料行、是否需要具名計算來提高使用者易懂性和可用性，以及現有的具名計算或具名查詢是否會傳回預期的值。</span><span class="sxs-lookup"><span data-stu-id="1f76c-105">Viewing the actual contents assists you in determining whether all columns are needed, if named calculations are required to increase user friendliness and usability, and whether existing named calculations or named queries return the anticipated values.</span></span>  
  
 <span data-ttu-id="1f76c-106">若要檢視資料，您必須要有使用中連接來連接到資料來源或 DSV 中選定物件的來源。</span><span class="sxs-lookup"><span data-stu-id="1f76c-106">To view data, you must have an active connection to the data source or sources for the selected object in the DSV.</span></span> <span data-ttu-id="1f76c-107">資料表中的任何具名計算也會在查詢中傳送。</span><span class="sxs-lookup"><span data-stu-id="1f76c-107">Any named calculations in a table are also sent in the query.</span></span>  
  
 <span data-ttu-id="1f76c-108">以表格式格式傳回的資料可進行排序和複製。</span><span class="sxs-lookup"><span data-stu-id="1f76c-108">The data returned in a tabular format that you can sort and copy.</span></span> <span data-ttu-id="1f76c-109">按一下資料行標題，即可依據該資料行重新排序資料列。</span><span class="sxs-lookup"><span data-stu-id="1f76c-109">Click on the column headers to re-sort the rows by that column.</span></span> <span data-ttu-id="1f76c-110">您也可以反白顯示方格中的資料，按下 Ctrl-C 將選取範圍複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="1f76c-110">You can also highlight data in the grid and press Ctrl-C to copy the selection to the clipboard.</span></span>  
  
 <span data-ttu-id="1f76c-111">您也可以控制取樣方法和取樣計數。</span><span class="sxs-lookup"><span data-stu-id="1f76c-111">You can also control the sample method and the sample count.</span></span> <span data-ttu-id="1f76c-112">預設會傳回前 5000 個資料列。</span><span class="sxs-lookup"><span data-stu-id="1f76c-112">By default, the top 5000 rows are returned.</span></span>  
  
## <a name="to-browse-data-or-change-sampling-options"></a><span data-ttu-id="1f76c-113">瀏覽資料或變更取樣選項</span><span class="sxs-lookup"><span data-stu-id="1f76c-113">To browse data or change sampling options</span></span>  
  
1.  <span data-ttu-id="1f76c-114">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟含有您想在其中瀏覽資料之資料來源檢視的專案，或連接到包含此資料來源檢視的資料庫。</span><span class="sxs-lookup"><span data-stu-id="1f76c-114">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project or connect to the database that contains the data source view in which you want to browse data.</span></span>  
  
2.  <span data-ttu-id="1f76c-115">在方案總管中，展開 [資料來源檢視]\*\*\*\* 資料夾，然後按兩下資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="1f76c-115">In Solution Explorer, expand the **Data Source Views** folder, and then double-click the data source view.</span></span>  
  
3.  <span data-ttu-id="1f76c-116">以滑鼠右鍵按一下包含您要檢視之資料的資料表、檢視或具名查詢，然後按一下 [瀏覽資料]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1f76c-116">Right-click the table, view, or named query that contains the data you want to view, and then click **Explore Data**.</span></span>  
  
     <span data-ttu-id="1f76c-117">資料來源視圖中資料表、視圖或命名查詢的基礎資料來源為查詢，結果會出現在 [**流覽 \<object name> 資料表**] 索引標籤中。</span><span class="sxs-lookup"><span data-stu-id="1f76c-117">The data source underlying the table, view, or named query in the data source view are queries, and the results appear in the **Explore \<object name> Table** tab.</span></span>  
  
4.  <span data-ttu-id="1f76c-118">在 [**流覽 \<object name> 資料表**] 工具列上，按一下 [**取樣選項**] 圖示。</span><span class="sxs-lookup"><span data-stu-id="1f76c-118">On the **Explore \<object name> Table** toolbar, click the **Sampling options** icon.</span></span>  
  
     <span data-ttu-id="1f76c-119">**[資料瀏覽選項]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="1f76c-119">The **Data Exploration Options** dialog box opens.</span></span> <span data-ttu-id="1f76c-120">在這個對話方塊中，您可以指定取樣方法 (比預設取樣大小 5000 個資料列更多或更少)，或取樣計數。</span><span class="sxs-lookup"><span data-stu-id="1f76c-120">In this dialog box you can specify the sampling method (fewer or more records than the default sampling size of 5000 rows), or sample count.</span></span>  
  
5.  <span data-ttu-id="1f76c-121">依適當情況按一下 **[確定]** 或 **[取消]** 。</span><span class="sxs-lookup"><span data-stu-id="1f76c-121">Click **OK** or **Cancel** as appropriate.</span></span>  
  
6.  <span data-ttu-id="1f76c-122">若要重新取樣資料，請按一下 [**流覽 \<object name> 資料表**] 工具列上的 [重新**取樣資料**]。</span><span class="sxs-lookup"><span data-stu-id="1f76c-122">To resample the data, click **Resample Data** on the **Explore \<object name> Table** toolbar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f76c-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f76c-123">See Also</span></span>  
 [<span data-ttu-id="1f76c-124">多維度模型中的資料來源檢視</span><span class="sxs-lookup"><span data-stu-id="1f76c-124">Data Source Views in Multidimensional Models</span></span>](data-source-views-in-multidimensional-models.md)  
  
  
