---
title: 修改預設資料表名稱 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ddd97483-a76d-43c1-8b40-fc7cc57fb0c2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 254f797be95f60211983400b019415431d4cf39c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584796"
---
# <a name="modifying-default-table-names"></a><span data-ttu-id="dce77-102">修改預設資料表名稱</span><span class="sxs-lookup"><span data-stu-id="dce77-102">Modifying Default Table Names</span></span>
  <span data-ttu-id="dce77-103">您可以針對資料來源檢視中的物件，變更 **FriendlyName** 屬性的值，使其更明顯且更容易使用。</span><span class="sxs-lookup"><span data-stu-id="dce77-103">You can change the value of the **FriendlyName** property for objects in the data source view to make them easier to notice and use.</span></span>  
  
 <span data-ttu-id="dce77-104">在下列工作中，您會在資料來源檢視中變更每個資料表的易記名稱，方法是從這些資料表中移除 "**Dim**" 和 "**Fact**" 前置詞。</span><span class="sxs-lookup"><span data-stu-id="dce77-104">In the following task, you will change the friendly name of each table in the data source view by removing the "**Dim**" and "**Fact**" prefixes from these tables.</span></span> <span data-ttu-id="dce77-105">這樣可以讓 Cube 和維度物件 (將在下一課定義) 更明顯且更容易使用。</span><span class="sxs-lookup"><span data-stu-id="dce77-105">This will make the cube and dimension objects (that you will define in the next lesson) easier to notice and use.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dce77-106">您也可以在資料來源檢視中變更資料行的易記名稱、定義導出資料行和聯結資料表或檢視，使其更容易使用。</span><span class="sxs-lookup"><span data-stu-id="dce77-106">You can also change the friendly names of columns, define calculated columns, and join tables or views in the data source view to make them easier to use.</span></span>  
  
### <a name="to-modify-the-default-name-of-a-table"></a><span data-ttu-id="dce77-107">若要修改資料表的預設名稱</span><span class="sxs-lookup"><span data-stu-id="dce77-107">To modify the default name of a table</span></span>  
  
1.  <span data-ttu-id="dce77-108">在 [資料來源檢視設計師]\*\*\*\* 的 [資料表]\*\*\*\* 窗格中，以滑鼠右鍵按一下 **FactInternetSales** 資料表，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dce77-108">In the **Tables** pane of **Data Source View Designer**, right-click the **FactInternetSales** table, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="dce77-109">如果未顯示 [Microsoft Visual Studio] 視窗右側的 [屬性] 視窗，請按一下 [屬性] 視窗標題列上的 [自動隱藏]\*\*\*\* 按鈕，讓該視窗保持可見狀態。</span><span class="sxs-lookup"><span data-stu-id="dce77-109">If the Properties window on the right side of the Microsoft Visual Studio window is not displayed, click the **Auto Hide** button on the title bar of the Properties window so that this window remains visible.</span></span>  
  
     <span data-ttu-id="dce77-110">當 [屬性] 視窗保持開啟時，要在資料來源檢視中變更每一個資料表的屬性會更加容易。</span><span class="sxs-lookup"><span data-stu-id="dce77-110">It is easier to change the properties for each table in the data source view when the Properties window remains open.</span></span> <span data-ttu-id="dce77-111">如果您未使用 [自動隱藏]\*\*\*\* 按鈕使視窗固定開啟，則在 [圖表]\*\*\*\* 窗格中按一下不同的物件時即會關閉視窗。</span><span class="sxs-lookup"><span data-stu-id="dce77-111">If you do not pin the window open by using the **Auto Hide** button, the window will close when you click a different object in the **Diagram** pane.</span></span>  
  
3.  <span data-ttu-id="dce77-112">將**FactInternetSales**物件的**FriendlyName**屬性變更為 *`InternetSales`* 。</span><span class="sxs-lookup"><span data-stu-id="dce77-112">Change the **FriendlyName** property for the **FactInternetSales** object to *`InternetSales`*.</span></span>  
  
     <span data-ttu-id="dce77-113">當您按一下而離開 **FriendlyName** 屬性的資料格時，即套用變更。</span><span class="sxs-lookup"><span data-stu-id="dce77-113">When you click away from the cell for the **FriendlyName** property, the change is applied.</span></span> <span data-ttu-id="dce77-114">在下一課，您將定義以此事實資料表為基礎的量值群組。</span><span class="sxs-lookup"><span data-stu-id="dce77-114">In the next lesson, you will define a measure group that is based on this fact table.</span></span> <span data-ttu-id="dce77-115">事實資料表的名稱是 InternetSales 而不是 FactInternetSales，因為您在這一課已做了變更。</span><span class="sxs-lookup"><span data-stu-id="dce77-115">The name of the fact table will be InternetSales instead of FactInternetSales because of the change you made in this lesson.</span></span>  
  
4.  <span data-ttu-id="dce77-116">按一下 [資料表]\*\*\*\* 窗格中的 [DimProduct]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="dce77-116">Click **DimProduct** in the **Tables** pane.</span></span> <span data-ttu-id="dce77-117">在 [屬性視窗中，將 [ **FriendlyName** ] 屬性變更為 *`Product`* 。</span><span class="sxs-lookup"><span data-stu-id="dce77-117">In the Properties window, change the **FriendlyName** property to *`Product`*.</span></span>  
  
5.  <span data-ttu-id="dce77-118">以相同方式變更資料來源檢視中其餘每個資料表的 **FriendlyName** 屬性，以便移除 "**Dim**" 前置詞。</span><span class="sxs-lookup"><span data-stu-id="dce77-118">Change the **FriendlyName** property of each remaining table in the data source view in the same way, to remove the "**Dim**" prefix.</span></span>  
  
6.  <span data-ttu-id="dce77-119">完成時，按一下 [自動隱藏]\*\*\*\* 按鈕，再次隱藏 [屬性] 視窗。</span><span class="sxs-lookup"><span data-stu-id="dce77-119">When you have finished, click the **Auto Hide** button to hide the Properties window again.</span></span>  
  
7.  <span data-ttu-id="dce77-120">在 [檔案]\*\*\*\* 功能表上或 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 的工具列上，按一下 [全部儲存]\*\*\*\*，即可儲存您到目前為止在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程專案中所做的變更。</span><span class="sxs-lookup"><span data-stu-id="dce77-120">On the **File** menu, or on the toolbar of [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click **Save All** to save the changes you have made to this point in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project.</span></span> <span data-ttu-id="dce77-121">如果您想要的話，可以在此停止教學課程，之後再繼續。</span><span class="sxs-lookup"><span data-stu-id="dce77-121">You can stop the tutorial here if you want and resume it later.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="dce77-122">下一課</span><span class="sxs-lookup"><span data-stu-id="dce77-122">Next Lesson</span></span>  
 [<span data-ttu-id="dce77-123">第2課：定義和部署 Cube</span><span class="sxs-lookup"><span data-stu-id="dce77-123">Lesson 2: Defining and Deploying a Cube</span></span>](lesson-2-defining-and-deploying-a-cube.md)  
  
## <a name="see-also"></a><span data-ttu-id="dce77-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dce77-124">See Also</span></span>  
 <span data-ttu-id="dce77-125">[多維度模型中的資料來源視圖](multidimensional-models/data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="dce77-125">[Data Source Views in Multidimensional Models](multidimensional-models/data-source-views-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="dce77-126">變更資料來源檢視的屬性 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="dce77-126">Change Properties in a Data Source View &#40;Analysis Services&#41;</span></span>](multidimensional-models/change-properties-in-a-data-source-view-analysis-services.md)  
  
  
