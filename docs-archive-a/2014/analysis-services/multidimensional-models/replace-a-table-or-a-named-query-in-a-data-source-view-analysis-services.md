---
title: 將資料來源 View 中的資料表或已命名的查詢取代 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- replacing tables
- data source views [Analysis Services], tables
- named queries [Analysis Services], replacing tables
- tables [Analysis Services], data source views
- partitions [Analysis Services], named queries
ms.assetid: 60c2a018-1299-4915-b60e-e73316524def
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2b5055de60ba757c9dcfa118e4e2c4748c6534e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597405"
---
# <a name="replace-a-table-or-a-named-query-in-a-data-source-view-analysis-services"></a><span data-ttu-id="5a7b2-102">取代資料來源檢視中的資料表或具名查詢 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="5a7b2-102">Replace a Table or a Named Query in a Data Source View (Analysis Services)</span></span>
  <span data-ttu-id="5a7b2-103">在資料來源檢視設計工具中，您可以將資料來源檢視 (DSV) 中的資料表、檢視表或具名查詢取代為相同或不同資料來源中的不同資料表或檢視表，或是 DSV 中已定義的具名查詢。</span><span class="sxs-lookup"><span data-stu-id="5a7b2-103">In Data Source View Designer, you can replace a table, view, or named query in a data source view (DSV) with a different table or view from the same or a different data source, or with a named query defined in the DSV.</span></span> <span data-ttu-id="5a7b2-104">當您取代資料表時， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫或專案中有參考該資料表的所有其他物件仍可繼續參考該資料表，因為 DSV 中資料表的物件識別碼不變。</span><span class="sxs-lookup"><span data-stu-id="5a7b2-104">When you replace a table, all other objects in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database or project that have references to the table continue to reference the table because the object ID for the table in the DSV does not change.</span></span> <span data-ttu-id="5a7b2-105">仍然相關的所有關聯性 (依據名稱和資料行類型比對) 都會保留下來。</span><span class="sxs-lookup"><span data-stu-id="5a7b2-105">Any relationships that are still relevant (based on name and column-type matching) are retained.</span></span> <span data-ttu-id="5a7b2-106">相對而言，如果您先刪除，再加入資料表，則會失去參考和關聯性，而且必須重新建立。</span><span class="sxs-lookup"><span data-stu-id="5a7b2-106">In contrast, if you delete and then add a table, references and relationships are lost and must be recreated.</span></span>  
  
 <span data-ttu-id="5a7b2-107">若要將資料表取代成另一個資料表，您必須與專案模式下的資料來源檢視設計師的來源資料之間有使用中連接。</span><span class="sxs-lookup"><span data-stu-id="5a7b2-107">To replace a table with another table, you must have an active connection to the source data in Data Source View Designer in project mode.</span></span>  
  
 <span data-ttu-id="5a7b2-108">您最常將資料來源檢視中的資料表取代成資料來源中的另一個資料表。</span><span class="sxs-lookup"><span data-stu-id="5a7b2-108">You most frequently replace a table in the data source view with another table in the data source.</span></span> <span data-ttu-id="5a7b2-109">不過，您也可以將具名查詢取代成資料表。</span><span class="sxs-lookup"><span data-stu-id="5a7b2-109">However, you can also replace a named query with a table.</span></span> <span data-ttu-id="5a7b2-110">例如，您先前曾將資料表取代成具名查詢，而現在要還原為資料表。</span><span class="sxs-lookup"><span data-stu-id="5a7b2-110">For example, you previously replaced a table with a named query, and now want to revert to a table.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5a7b2-111">如果您在資料來源中重新命名資料表，請遵循取代資料表的步驟，並在重新整理 DSV 之前，將重新命名的資料表指定 DSV 中的相對應資料表的來源。</span><span class="sxs-lookup"><span data-stu-id="5a7b2-111">If you rename a table in a data source, follow the steps for replacing a table and specify the renamed table as the source of the corresponding table in the DSV before you refresh a DSV.</span></span> <span data-ttu-id="5a7b2-112">完成取代及重新命名程序會在 DSV 中保留資料表、資料表的參考和資料表的關聯性。</span><span class="sxs-lookup"><span data-stu-id="5a7b2-112">Completing the replacement and renaming process preserves the table, the table's references, and the table's relationships in the DSV.</span></span> <span data-ttu-id="5a7b2-113">否則，當您重新整理 DSV 時，資料來源中重新命名的資料表會被解譯為已刪除。</span><span class="sxs-lookup"><span data-stu-id="5a7b2-113">Otherwise, when you refresh the DSV, a renamed table in data source is interpreted as being deleted.</span></span> <span data-ttu-id="5a7b2-114">如需詳細資訊，請參閱[在資料來源檢視中重新整理結構描述 &#40;Analysis Services&#41;](refresh-the-schema-in-a-data-source-view-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="5a7b2-114">For more information, see [Refresh the Schema in a Data Source View &#40;Analysis Services&#41;](refresh-the-schema-in-a-data-source-view-analysis-services.md).</span></span>  
  
##  <a name="replace-a-table-with-a-named-query"></a><a name="bkmk_nq"></a> <span data-ttu-id="5a7b2-115">以具名查詢取代資料表</span><span class="sxs-lookup"><span data-stu-id="5a7b2-115">Replace a table with a named query</span></span>  
  
1.  <span data-ttu-id="5a7b2-116">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟含有您想在其中取代資料表或具名查詢之資料來源檢視的專案，或連接到包含此資料來源檢視的資料庫。</span><span class="sxs-lookup"><span data-stu-id="5a7b2-116">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project or connect to the database that contains the data source view in which you want to replace a table or a named query.</span></span>  
  
2.  <span data-ttu-id="5a7b2-117">在方案總管中，展開 [資料來源檢視]\*\*\*\* 資料夾，然後按兩下資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="5a7b2-117">In Solution Explorer, expand the **Data Source Views** folder, and then double-click the data source view.</span></span>  
  
3.  <span data-ttu-id="5a7b2-118">開啟 [建立具名查詢]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="5a7b2-118">Open the **Create Named Query** dialog box.</span></span> <span data-ttu-id="5a7b2-119">在 [資料表]\*\*\*\* 或 [圖表]\*\*\*\* 窗格中，以滑鼠右鍵按一下您想要取代的資料表，並指向 [取代資料表]\*\*\*\*，然後按一下 [使用新具名查詢]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5a7b2-119">In either **Tables** or **Diagram** pane, right-click the table that you wish to replace, point to **Replace Table** and then click **With New Named Query**.</span></span>  
  
4.  <span data-ttu-id="5a7b2-120">在 [建立具名查詢]\*\*\*\* 對話方塊中，定義具名查詢，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5a7b2-120">In the **Create Named Query** dialog box, define the named query and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="5a7b2-121">儲存已修改的資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="5a7b2-121">Save the modified data source view.</span></span>  
  
## <a name="replace-a-table-or-named-query-with-a-table"></a><span data-ttu-id="5a7b2-122">以資料表取代資料表或具名查詢</span><span class="sxs-lookup"><span data-stu-id="5a7b2-122">Replace a table or named query with a table</span></span>  
  
1.  <span data-ttu-id="5a7b2-123">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟含有您想在其中取代資料表或具名查詢之資料來源檢視的專案，或連接到包含此資料來源檢視的資料庫。</span><span class="sxs-lookup"><span data-stu-id="5a7b2-123">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project or connect to the database that contains the data source view in which you want to replace a table or a named query.</span></span>  
  
2.  <span data-ttu-id="5a7b2-124">在方案總管中，展開 [資料來源檢視]\*\*\*\* 資料夾，然後按兩下資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="5a7b2-124">In Solution Explorer, expand the **Data Source Views** folder, and then double-click the data source view.</span></span>  
  
3.  <span data-ttu-id="5a7b2-125">開啟 [使用其他資料表取代]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="5a7b2-125">Open the **Replace Table with Other Table** dialog box.</span></span> <span data-ttu-id="5a7b2-126">在 [資料表]\*\*\*\* 或 [圖表]\*\*\*\* 窗格中，以滑鼠右鍵按一下您想要取代的資料表或具名查詢，並指向 [取代資料表]\*\*\*\*，然後按一下 [使用其他資料表]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="5a7b2-126">In either **Tables** or **Diagram** pane, right-click the table or named query that you wish to replace, point to **Replace Table** and then click **With Other Table**.</span></span>  
  
4.  <span data-ttu-id="5a7b2-127">在 [使用其他資料表取代]\*\*\*\* 對話方塊中：</span><span class="sxs-lookup"><span data-stu-id="5a7b2-127">In the **Replace Table with Other Table** dialog box:</span></span>  
  
    1.  <span data-ttu-id="5a7b2-128">在 [資料來源]\*\*\*\* 下拉式清單方塊中，選取想要的資料來源</span><span class="sxs-lookup"><span data-stu-id="5a7b2-128">In the **DataSource** drop-down list box, select the desired data source</span></span>  
  
    2.  <span data-ttu-id="5a7b2-129">選取您想要用來取代資料表或具名查詢的資料表。</span><span class="sxs-lookup"><span data-stu-id="5a7b2-129">Select the table with which you wish to replace the table or named query</span></span>  
  
5.  <span data-ttu-id="5a7b2-130">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="5a7b2-130">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="5a7b2-131">儲存已修改的資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="5a7b2-131">Save the modified data source view.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a7b2-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a7b2-132">See Also</span></span>  
 [<span data-ttu-id="5a7b2-133">多維度模型中的資料來源檢視</span><span class="sxs-lookup"><span data-stu-id="5a7b2-133">Data Source Views in Multidimensional Models</span></span>](data-source-views-in-multidimensional-models.md)  
  
  
