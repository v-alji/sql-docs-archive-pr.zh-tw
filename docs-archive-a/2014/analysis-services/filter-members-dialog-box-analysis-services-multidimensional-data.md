---
title: '[篩選成員] 對話方塊 (Analysis Services-多維度資料) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensiondesigner.filtermembers.f1
helpviewer_keywords:
- Filter Members dialog box
ms.assetid: 52c6da1d-9fb5-4dbc-bffa-248d11cd337c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 66980b1afe9d4eed353ae18c37ed1fdd052e62b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584803"
---
# <a name="filter-members-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="6102d-102">篩選成員對話方塊 (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="6102d-102">Filter Members Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="6102d-103">使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中的 [篩選成員]\*\*\*\* 對話方塊，即可在 [維度設計師]\*\*\*\* 的 [瀏覽器]\*\*\*\* 索引標籤中瀏覽維度時，依成員標題、成員名稱、成員唯一的名稱、索引鍵資料行的值或值資料行的值，篩選目前層級的維度成員。</span><span class="sxs-lookup"><span data-stu-id="6102d-103">Use the **Filter Members** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to filter dimension members by member caption, member name, member unique name, key column value, or value column value for the current level while browsing a dimension in the **Browser** tab of **Dimension Designer**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6102d-104">選項</span><span class="sxs-lookup"><span data-stu-id="6102d-104">Options</span></span>  
  
|<span data-ttu-id="6102d-105">詞彙</span><span class="sxs-lookup"><span data-stu-id="6102d-105">Term</span></span>|<span data-ttu-id="6102d-106">定義</span><span class="sxs-lookup"><span data-stu-id="6102d-106">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="6102d-107">**篩選運算式**</span><span class="sxs-lookup"><span data-stu-id="6102d-107">**Filter expression**</span></span>|<span data-ttu-id="6102d-108">顯示用來建構篩選運算式之屬性、運算子和值的方格。</span><span class="sxs-lookup"><span data-stu-id="6102d-108">Displays a grid of properties, operators, and values used to construct a filter expression.</span></span> <span data-ttu-id="6102d-109">請注意，在加入資料列之後，就無法移除該資料列。</span><span class="sxs-lookup"><span data-stu-id="6102d-109">Note that after a row is added, it cannot be removed.</span></span> <span data-ttu-id="6102d-110">您必須關閉和重新開啟對話方塊，以指定新的篩選運算式。</span><span class="sxs-lookup"><span data-stu-id="6102d-110">You must close and reopen the dialog box to specify a new filter expression.</span></span> <span data-ttu-id="6102d-111">方格包含下列資料行：</span><span class="sxs-lookup"><span data-stu-id="6102d-111">The grid contains the following columns:</span></span><br /><br /> <span data-ttu-id="6102d-112">**屬性**：選取要用於篩選運算式之成員的屬性。</span><span class="sxs-lookup"><span data-stu-id="6102d-112">**Property**: Select the property of the member to use for the filter expression.</span></span><br /><br /> <span data-ttu-id="6102d-113">**Operator**：選取用於篩選運算式的運算子。</span><span class="sxs-lookup"><span data-stu-id="6102d-113">**Operator**: Select the operator to use for the filter expression.</span></span><br /><br /> <span data-ttu-id="6102d-114">**值**：輸入在 [**屬性**] 中所選取屬性的值，以使用 [**運算子**] 中指定的運算子進行評估。</span><span class="sxs-lookup"><span data-stu-id="6102d-114">**Value**: Type the value of the property selected in **Property** to evaluate using the operator specified in **Operator**.</span></span>|  
|<span data-ttu-id="6102d-115">**測試窗格**</span><span class="sxs-lookup"><span data-stu-id="6102d-115">**Test pane**</span></span>|<span data-ttu-id="6102d-116">按一下 [測試]\*\*\*\* 時，此窗格會顯示篩選運算式傳回的成員。</span><span class="sxs-lookup"><span data-stu-id="6102d-116">When **Test** is clicked, this pane displays the members returned by the filter expression.</span></span> <span data-ttu-id="6102d-117">如果使用 [篩選運算式]\*\*\*\* 中指定的準則而沒有傳回任何成員，則會顯示警告。</span><span class="sxs-lookup"><span data-stu-id="6102d-117">If no members are returned using the criteria specified in **Filter expression**, a warning is displayed.</span></span>|  
|<span data-ttu-id="6102d-118">**Test**</span><span class="sxs-lookup"><span data-stu-id="6102d-118">**Test**</span></span>|<span data-ttu-id="6102d-119">按一下即可測試 [篩選運算式]\*\*\*\* 中指定的準則。</span><span class="sxs-lookup"><span data-stu-id="6102d-119">Click to test the criteria specified in **Filter expression**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6102d-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6102d-120">See Also</span></span>  
 <span data-ttu-id="6102d-121">[Analysis Services 的設計工具和對話方塊 &#40;多維度資料&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="6102d-121">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="6102d-122">瀏覽器 &#40;維度設計師&#41; &#40;Analysis Services-多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="6102d-122">Browser &#40;Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](browser-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
