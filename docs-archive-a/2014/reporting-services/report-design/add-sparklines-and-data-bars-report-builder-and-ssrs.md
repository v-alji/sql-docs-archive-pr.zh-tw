---
title: 新增走勢圖和資料橫條 (報表產生器和 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 0b297c2e-d48b-41b0-aabd-29680cdcdb05
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 55ec15354cdc78dd9678b9466f30d2fca0a73adc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592455"
---
# <a name="add-sparklines-and-data-bars-report-builder-and-ssrs"></a><span data-ttu-id="be32c-102">加入走勢圖和資料橫條 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="be32c-102">Add Sparklines and Data Bars (Report Builder and SSRS)</span></span>
  <span data-ttu-id="be32c-103">走勢圖和資料橫條很小，也就是以少量的外來細節傳達許多資訊的精簡圖表。</span><span class="sxs-lookup"><span data-stu-id="be32c-103">Sparklines and data bars are small, spare charts that convey a lot of information with little extraneous detail.</span></span> <span data-ttu-id="be32c-104">如需詳細資訊，請參閱[走勢圖和資料橫條 &#40;報表產生器和 SSRS&#41;](sparklines-and-data-bars-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="be32c-104">For more information about them, see [Sparklines and Data Bars &#40;Report Builder and SSRS&#41;](sparklines-and-data-bars-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="be32c-105">走勢圖和資料橫條最常放在資料表或矩陣內的資料格中。</span><span class="sxs-lookup"><span data-stu-id="be32c-105">Sparklines and data bars are most commonly placed in cells in a table or matrix.</span></span> <span data-ttu-id="be32c-106">走勢圖通常會針對每個資料格只顯示一個數列。</span><span class="sxs-lookup"><span data-stu-id="be32c-106">Sparklines usually display only one series each.</span></span> <span data-ttu-id="be32c-107">資料橫條可以包含一個或多個資料點。</span><span class="sxs-lookup"><span data-stu-id="be32c-107">Data bars can contain one or more data points.</span></span> <span data-ttu-id="be32c-108">走勢圖和資料橫條會從資料表或矩陣內每一個資料列的重複數列資訊來衍生其影響力。</span><span class="sxs-lookup"><span data-stu-id="be32c-108">Both sparklines and data bars derive their impact from repeating the series information for each row in the table or matrix.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-sparkline-or-data-bar-to-a-table-or-matrix"></a><span data-ttu-id="be32c-109">若要將走勢圖或資料橫條加入至資料表或矩陣</span><span class="sxs-lookup"><span data-stu-id="be32c-109">To add a sparkline or data bar to a table or matrix</span></span>  
  
1.  <span data-ttu-id="be32c-110">如果您還沒這樣做，請使用您想要顯示的資料建立資料表或矩陣。</span><span class="sxs-lookup"><span data-stu-id="be32c-110">If you have not done so already, create a table or matrix with the data you want to display.</span></span> <span data-ttu-id="be32c-111">如需詳細資訊，請參閱[資料表 &#40;報表產生器及 SSRS&#41;](tables-report-builder-and-ssrs.md) 和[矩陣 &#40;報表產生器及 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="be32c-111">For more information, see [Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) or [Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="be32c-112">將資料行插入資料表或矩陣中。</span><span class="sxs-lookup"><span data-stu-id="be32c-112">Insert a column in your table or matrix.</span></span> <span data-ttu-id="be32c-113">如需詳細資訊，請參閱[插入或刪除資料行 &#40;報表產生器及 SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="be32c-113">For more information, see [Insert or Delete a Column &#40;Report Builder and SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md).</span></span>  
  
3.  <span data-ttu-id="be32c-114">在 **[插入]** 索引標籤上，按一下 **[走勢圖]** 或 **[資料橫條]**，然後在新資料行的資料格內按一下。</span><span class="sxs-lookup"><span data-stu-id="be32c-114">On the **Insert** tab, click **Sparkline** or **Data Bar**, and then click in a cell in the new column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="be32c-115">您無法將走勢圖放在資料表的詳細資料群組中。</span><span class="sxs-lookup"><span data-stu-id="be32c-115">You cannot place sparklines in a detail group in a table.</span></span> <span data-ttu-id="be32c-116">它們必須放在與群組相關聯的資料格中。</span><span class="sxs-lookup"><span data-stu-id="be32c-116">They must go in a cell associated with a group.</span></span>  
  
4.  <span data-ttu-id="be32c-117">在 [變更走勢圖類型/變更資料橫條類型]\*\*\*\* 對話方塊中，按一下您想要的走勢圖或資料橫條類型，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="be32c-117">In the **Change Sparkline/Data Bar Type** dialog box, click the kind of sparkline or data bar you want, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="be32c-118">按一下走勢圖或資料橫條。</span><span class="sxs-lookup"><span data-stu-id="be32c-118">Click the sparkline or data bar.</span></span>  
  
     <span data-ttu-id="be32c-119">隨即開啟 **[圖表資料]** 窗格。</span><span class="sxs-lookup"><span data-stu-id="be32c-119">The **Chart Data** pane opens.</span></span>  
  
6.  <span data-ttu-id="be32c-120">在 [值]\*\*\*\* 區域中，按一下 [新增欄位]\*\*\*\* 的加號 (**+**)，然後按一下您想要將哪一個欄位的值加入圖表。</span><span class="sxs-lookup"><span data-stu-id="be32c-120">In the **Values** area, click the **Add Fields** plus sign (**+**), and then click the field whose values you want charted.</span></span>  
  
7.  <span data-ttu-id="be32c-121">在 [類別目錄群組]\*\*\*\* 區域中，按一下 [新增欄位]\*\*\*\* 的加號 (**+**)，然後按一下您想要將哪一個欄位的值當作分組依據。</span><span class="sxs-lookup"><span data-stu-id="be32c-121">In the **Category Groups** area, click the **Add Fields** plus sign (**+**), and then click the field whose values you want to group by.</span></span>  
  
     <span data-ttu-id="be32c-122">一般對於走勢圖或資料橫條而言，您不會將欄位加入至 **[數列群組]** 區域，因為您希望每一個資料列只有一個數列。</span><span class="sxs-lookup"><span data-stu-id="be32c-122">Typically for sparklines and data bars, you will not add a field to the **Series Group** area because you only want one series for each row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be32c-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be32c-123">See Also</span></span>  
 <span data-ttu-id="be32c-124">[圖表 &#40;報表產生器和 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="be32c-124">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="be32c-125">在資料表或矩陣的圖表上對齊資料 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="be32c-125">Align the Data in a Chart in a Table or Matrix &#40;Report Builder and SSRS&#41;</span></span>](align-the-data-in-a-chart-in-a-table-or-matrix-report-builder-and-ssrs.md)  
  
  
