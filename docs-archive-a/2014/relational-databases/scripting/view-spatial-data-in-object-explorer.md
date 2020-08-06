---
title: 檢視物件總管中的空間資料
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 59cca562-e3f5-4257-b868-adcbcc0142cc
author: rothja
ms.author: jroth
ms.openlocfilehash: 881adf69ee83ee4b7536afae0b190fbec90f132c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596623"
---
# <a name="view-spatial-data-in-object-explorer"></a><span data-ttu-id="feb5a-102">檢視物件總管中的空間資料</span><span class="sxs-lookup"><span data-stu-id="feb5a-102">View Spatial Data in Object Explorer</span></span>
  <span data-ttu-id="feb5a-103">除了以方格格式顯示在 [結果] 視窗中的資料以外，查詢編輯器中的 [空間結果] 視窗還會提供檢視空間資料結果的視覺化對應工具。</span><span class="sxs-lookup"><span data-stu-id="feb5a-103">The **Spatial results** window in Query Editor provides visual mapping tools for viewing spatial data results in addition to the data displayed in grid format in the **Results** window.</span></span> <span data-ttu-id="feb5a-104">若要在 [空間結果]  視窗中顯示空間資料，您的查詢結果至少必須包含一個具有幾何或地理位置資料的空間資料行。</span><span class="sxs-lookup"><span data-stu-id="feb5a-104">To display spatial data in the **Spatial Results** window, your query results must contain at least one spatial data column with either geometry or geography data.</span></span>  
  
### <a name="to-view-spatial-data-in-the-spatial-results-window"></a><span data-ttu-id="feb5a-105">在空間結果視窗中檢視空間資料</span><span class="sxs-lookup"><span data-stu-id="feb5a-105">To view spatial data in the Spatial results window</span></span>  
  
1.  <span data-ttu-id="feb5a-106">在查詢編輯器中，按一下 [空間結果]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="feb5a-106">In Query Editor, click the **Spatial results** tab.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="feb5a-107">如果您的查詢結果沒有包含空間資料，或者您指定要將結果傳回成文字，就無法使用這個視窗。</span><span class="sxs-lookup"><span data-stu-id="feb5a-107">This window is not available if your query results do not contain spatial data or if you specify that your results are returned as text.</span></span>  
  
2.  <span data-ttu-id="feb5a-108">在 [選取空間資料行]  清單中，選取您想要檢視的資料行。</span><span class="sxs-lookup"><span data-stu-id="feb5a-108">Select the column you want to view from the **Select spatial column** list.</span></span> <span data-ttu-id="feb5a-109">如果您的資料表只有一個空間資料行，這個資料行就是清單中的預設選項。</span><span class="sxs-lookup"><span data-stu-id="feb5a-109">If there is only one spatial column in your table, this column is the default option in the list.</span></span>  
  
3.  <span data-ttu-id="feb5a-110">在 [選取標籤資料行]  清單中，選取您想要當作資料標籤使用的非空間資料行。</span><span class="sxs-lookup"><span data-stu-id="feb5a-110">Select the non-spatial column you want to use as data labels from the **Select label columns** list.</span></span>  
  
4.  <span data-ttu-id="feb5a-111">在 [選取投射]  清單中，選取您想要針對地理位置資料使用的投射。</span><span class="sxs-lookup"><span data-stu-id="feb5a-111">Select the projection you want for geography data from the **Select projection** list.</span></span> <span data-ttu-id="feb5a-112">預設投射為 Equirectangular。其他可用的投射包括 Mercator、Robinson 或 Bonne。</span><span class="sxs-lookup"><span data-stu-id="feb5a-112">The default projection is Equirectangular; other projections available are Mercator, Robinson, or Bonne.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="feb5a-113">如果您的空間資料行包含幾何資料，就無法使用 [選取投射]  。</span><span class="sxs-lookup"><span data-stu-id="feb5a-113">**Select projection** is not available if your spatial column contains geometry data.</span></span>  
  
5.  <span data-ttu-id="feb5a-114">調整 [顯示比例]  滑動軸，以便增加對應元素的視覺大小。</span><span class="sxs-lookup"><span data-stu-id="feb5a-114">Adjust the **Zoom** slider to increase the visual size of mapped elements.</span></span> <span data-ttu-id="feb5a-115">若為多邊形形狀，只有當此形狀夠大，足以容納標籤文字時，才會顯示標籤。</span><span class="sxs-lookup"><span data-stu-id="feb5a-115">For polygon shapes, the label is visible only when the shape is large enough to hold the label text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feb5a-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="feb5a-116">See Also</span></span>  
 <span data-ttu-id="feb5a-117">[空間結果視窗](spatial-results-window.md) </span><span class="sxs-lookup"><span data-stu-id="feb5a-117">[Spatial Results Window](spatial-results-window.md) </span></span>  
 <span data-ttu-id="feb5a-118">[Database Engine 查詢編輯器 &#40;SQL Server Management Studio&#41;](database-engine-query-editor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="feb5a-118">[Database Engine Query Editor &#40;SQL Server Management Studio&#41;](database-engine-query-editor-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="feb5a-119">查詢與文字編輯器 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="feb5a-119">Query and Text Editors &#40;SQL Server Management Studio&#41;</span></span>](query-and-text-editors-sql-server-management-studio.md)  
  
  
