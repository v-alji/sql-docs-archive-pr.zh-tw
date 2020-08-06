---
title: " (SSAS 表格式) 變更資料表、資料行或資料列篩選對應 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2124c526-5772-4f84-a019-9dd3e906e8dd
author: minewiskan
ms.author: owend
ms.openlocfilehash: d8a597fb51804ea12caace63f3308b07bffc5899
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594707"
---
# <a name="change-table-column-or-row-filter-mappings-ssas-tabular"></a><span data-ttu-id="a5669-102">變更資料表、資料行或資料列篩選對應 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="a5669-102">Change table, column, or row filter mappings (SSAS Tabular)</span></span>
  <span data-ttu-id="a5669-103">本主題描述如何在 **中使用** [編輯資料表屬性] [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]對話方塊來變更資料表、資料行或資料列篩選對應。</span><span class="sxs-lookup"><span data-stu-id="a5669-103">This topic describes how to change table, column, or row filter mappings by using the **Edit Table Properties** dialog box in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span>  
  
 <span data-ttu-id="a5669-104">視您一開始是透過從清單中選取資料表或使用 SQL 查詢匯入資料而定， **[編輯資料表屬性]** 對話方塊的選項都不同。</span><span class="sxs-lookup"><span data-stu-id="a5669-104">Options in the **Edit Table Properties** dialog box are different depending on whether you originally imported data by selecting tables from a list or by using a SQL query.</span></span> <span data-ttu-id="a5669-105">若您一開始是從清單中選取來匯入資料， **[編輯資料表屬性]** 對話方塊就會顯示資料表預覽模式。</span><span class="sxs-lookup"><span data-stu-id="a5669-105">If you originally imported the data by selecting from a list, the **Edit Table Properties** dialog box displays the Table Preview mode.</span></span> <span data-ttu-id="a5669-106">這種模式僅會顯示來源資料表的前五十個資料列。</span><span class="sxs-lookup"><span data-stu-id="a5669-106">This mode displays only a subset limited to the first fifty rows of the source table.</span></span> <span data-ttu-id="a5669-107">若您一開始是使用 SQL 陳述式匯入資料， **[編輯資料表屬性]** 對話方塊就只會顯示 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="a5669-107">If you originally imported the data by using a SQL statement, the **Edit Table Properties** dialog box only displays a SQL statement.</span></span> <span data-ttu-id="a5669-108">若是使用 SQL 查詢陳述式，您可以設計篩選或以手動方式編輯 SQL 陳述式，只擷取資料列的子集。</span><span class="sxs-lookup"><span data-stu-id="a5669-108">Using a SQL query statement, you can retrieve a subset of rows, either by designing a filter, or by manually editing the SQL statement.</span></span>  
  
 <span data-ttu-id="a5669-109">如果您將來源變更為具有與目前資料表不同之資料行的資料表，就會顯示資料行不同的警告訊息。</span><span class="sxs-lookup"><span data-stu-id="a5669-109">If you change the source to a table that has different columns than the current table, a message is displayed warning that the columns are different.</span></span> <span data-ttu-id="a5669-110">然後，您必須選取要放入目前資料表中的資料行，並按一下 **[儲存]**。</span><span class="sxs-lookup"><span data-stu-id="a5669-110">You must then select the columns that you want to put in the current table and click **Save**.</span></span> <span data-ttu-id="a5669-111">您可以選取資料表左邊的核取方塊，以取代整個資料表。</span><span class="sxs-lookup"><span data-stu-id="a5669-111">You can replace the entire table by selecting the check box at the left of the table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a5669-112">如果您的資料表有多個資料分割，您無法使用 [編輯資料表屬性] 對話方塊變更資料列篩選對應。</span><span class="sxs-lookup"><span data-stu-id="a5669-112">If your table has more than one partition, you cannot use the Edit Table Properties dialog box to change row filter mappings.</span></span> <span data-ttu-id="a5669-113">若要針對具有多個資料分割的資料表變更資料列篩選對應，請使用資料分割管理員。</span><span class="sxs-lookup"><span data-stu-id="a5669-113">To change row filter mappings for tables with multiple partitions, use Partition Manager.</span></span> <span data-ttu-id="a5669-114">如需詳細資訊，請參閱 [資料分割 &#40;SSAS 表格式&#41;](partitions-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="a5669-114">For more information, see [Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md).</span></span>  
  
#### <a name="to-change-table-column-or-row-filter-mappings"></a><span data-ttu-id="a5669-115">變更資料表、資料行或資料列篩選對應</span><span class="sxs-lookup"><span data-stu-id="a5669-115">To change table, column, or row filter mappings</span></span>  
  
1.  <span data-ttu-id="a5669-116">在模型設計師中，按一下資料表，然後按一下 **[資料表]** 功能表，再按一下 **[資料表屬性]**。</span><span class="sxs-lookup"><span data-stu-id="a5669-116">In the model designer, click the table, then click on the **Table** menu, and then click **Table Properties**.</span></span>  
  
2.  <span data-ttu-id="a5669-117">在 **[編輯資料表屬性]** 對話方塊中，找出包含您所要篩選之準則的資料行，再按一下資料行標題右邊的向下箭號。</span><span class="sxs-lookup"><span data-stu-id="a5669-117">In the **Edit Table Properties** dialog box, locate the column that contains the criteria you want to filter on, and then click the down arrow at the right of the column heading.</span></span>  
  
3.  <span data-ttu-id="a5669-118">在 [**自動篩選**] 功能表中，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="a5669-118">In the **AutoFilter** menu, do one of the following:</span></span>  
  
    -   <span data-ttu-id="a5669-119">在資料行值清單中，選取或清除做為篩選依據的一個或多個值，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="a5669-119">In the list of column values, select or clear one or more values to filter by, and then click OK.</span></span>  
  
         <span data-ttu-id="a5669-120">如果值的數量非常大，在清單中可能不會顯示個別的項目。</span><span class="sxs-lookup"><span data-stu-id="a5669-120">If the number of values is extremely large, individual items might not be shown in the list.</span></span> <span data-ttu-id="a5669-121">但是您會看到「要顯示的項目太多」這個訊息。</span><span class="sxs-lookup"><span data-stu-id="a5669-121">Instead, you will see the message, "Too many items to show."</span></span>  
  
    -   <span data-ttu-id="a5669-122">按一下 [數字篩選]\*\*\*\* 或 [文字篩選]\*\*\*\* (視資料行的類型而定)，然後按一下其中一個比較運算子命令 (例如 [等於])，或按一下 [自訂篩選]。</span><span class="sxs-lookup"><span data-stu-id="a5669-122">Click **Number Filters** or **Text Filters** (depending on the type of column), and then clicke of the comparison operator commands (such as Equals), or click Custom Filter.</span></span> <span data-ttu-id="a5669-123">在 **[自訂篩選]** 對話方塊中，建立篩選，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="a5669-123">In the **Custom Filter** dialog box, create the filter, and then click **OK**.</span></span>  
  
         <span data-ttu-id="a5669-124">如果發生錯誤而需要從頭開始，請按一下 **[清除資料列篩選]**。</span><span class="sxs-lookup"><span data-stu-id="a5669-124">If you make a mistake and need to start over, click **Clear Row Filters**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5669-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5669-125">See Also</span></span>  
 [<span data-ttu-id="a5669-126">編輯資料表屬性對話方塊 &#40;SSAS&#41;</span><span class="sxs-lookup"><span data-stu-id="a5669-126">Edit Table Properties Dialog Box &#40;SSAS&#41;</span></span>](../edit-table-properties-dialog-box-ssas.md)  
  
  
