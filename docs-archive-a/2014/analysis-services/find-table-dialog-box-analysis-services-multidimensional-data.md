---
title: 尋找資料表對話方塊 (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.findtabledialog.f1
helpviewer_keywords:
- Find Table dialog box
ms.assetid: 133d28e8-55eb-4783-bb8b-d3776a95ebda
author: minewiskan
ms.author: owend
ms.openlocfilehash: ee22c912a3121841a7827e31d53f7b8baba72174
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592986"
---
# <a name="find-table-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="fa93b-102">尋找資料表對話方塊 (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="fa93b-102">Find Table Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="fa93b-103">使用 **中的** [尋找資料表] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 對話方塊，即可尋找與維度、Cube 或採礦結構相關聯之資料來源檢視中的資料表。</span><span class="sxs-lookup"><span data-stu-id="fa93b-103">Use the **Find Table** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to locate a table in the data source view associated with a dimension, cube, or mining structure.</span></span> <span data-ttu-id="fa93b-104">您可以藉由下列方式在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中顯示此對話方塊：</span><span class="sxs-lookup"><span data-stu-id="fa93b-104">You can display this dialog box in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] by:</span></span>  
  
-   <span data-ttu-id="fa93b-105">在 **[維度設計師]** 的 **[維度結構]** 頁面上，從 **[工具列]** 窗格按一下 **[尋找資料表]**。</span><span class="sxs-lookup"><span data-stu-id="fa93b-105">Clicking **Find Table** from the **Toolbar** pane on the **Dimension Structure** page of the **Dimension Designer**.</span></span>  
  
-   <span data-ttu-id="fa93b-106">在 [維度設計師]\*\*\*\* 的 [維度結構]\*\*\*\* 頁面上，以滑鼠右鍵按一下 [資料來源檢視]\*\*\*\* 窗格的背景，然後選取 [尋找資料表]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fa93b-106">Right-clicking the background of the **Data Source View** pane on the **Dimension Structure** page of the **Dimension Designer** and selecting **Find Table**.</span></span>  
  
-   <span data-ttu-id="fa93b-107">在 **[Cube 設計師]** 的 **[Cube 結構]** 頁面上，從 **[工具列]** 窗格中按一下 **[尋找資料表]**。</span><span class="sxs-lookup"><span data-stu-id="fa93b-107">Clicking **Find Table** from the **Toolbar** pane on the **Cube Structure** page of the **Cube Designer**.</span></span>  
  
-   <span data-ttu-id="fa93b-108">在 [Cube 設計師]\*\*\*\* 的 [Cube 結構]\*\*\*\* 頁面上，以滑鼠右鍵按一下 [資料來源檢視]\*\*\*\* 窗格的背景，然後選取 [尋找資料表]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fa93b-108">Right-clicking the background of the **Data Source View** pane on the **Cube Structure** page of the **Cube Designer** and selecting **Find Table**.</span></span>  
  
-   <span data-ttu-id="fa93b-109">在 [資料採礦模型設計師]\*\*\*\* 的 [採礦結構]\*\*\*\* 頁面上，以滑鼠右鍵按一下 [資料來源檢視]\*\*\*\* 窗格的背景，然後選取 [尋找資料表]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fa93b-109">Right-clicking the background of the **Data Source View** pane on the **Mining Structure** page of the **Data Mining Model Designer** and selecting **Find Table**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="fa93b-110">選項</span><span class="sxs-lookup"><span data-stu-id="fa93b-110">Options</span></span>  
 <span data-ttu-id="fa93b-111">**從資料來源檢視中選取資料表**</span><span class="sxs-lookup"><span data-stu-id="fa93b-111">**Select a table from data source view**</span></span>  
 <span data-ttu-id="fa93b-112">在 [資料來源檢視]\*\*\*\* 窗格中，選取要尋找的資料表。</span><span class="sxs-lookup"><span data-stu-id="fa93b-112">Select the table to find in the **Data Source View** pane.</span></span> <span data-ttu-id="fa93b-113">此選項會顯示可用物件及其類型的方格，這些類型符合 [篩選]\*\*\*\* 中設定的篩選 (如果未設定 [篩選]\*\*\*\*，則為所有資料表)，且尚未在目前圖表中顯示。</span><span class="sxs-lookup"><span data-stu-id="fa93b-113">This option displays a grid of available objects and their types that match the filter set in **Filter** (or all tables if **Filter** is not set) and have not yet been shown in the current diagram.</span></span>  
  
 <span data-ttu-id="fa93b-114">**Filter**</span><span class="sxs-lookup"><span data-stu-id="fa93b-114">**Filter**</span></span>  
 <span data-ttu-id="fa93b-115">鍵入篩選以限制列出的物件，然後按一下按鈕來篩選 [從資料來源檢視中選取資料表]\*\*\*\* 列出的資料表。</span><span class="sxs-lookup"><span data-stu-id="fa93b-115">Type the filter used to restrict the objects listed, and then click the button to filter the tables listed in **Select a table from data source view**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa93b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa93b-116">See Also</span></span>  
 <span data-ttu-id="fa93b-117">[元件屬性對話方塊 &#40;Analysis Services-多維度資料&#41;](assembly-properties-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="fa93b-117">[Assembly Properties Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](assembly-properties-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="fa93b-118">[資料來源視圖 &#40;維度結構索引標籤、維度設計師&#41; &#40;Analysis Services-多維度資料&#41;](datasource-view-dimension-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="fa93b-118">[Data Source View &#40;Dimension Structure Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](datasource-view-dimension-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="fa93b-119">資料來源視圖 &#40;Cube 結構索引標籤、Cube 設計工具&#41; &#40;Analysis Services 多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="fa93b-119">Data Source View &#40;Cube Structure Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](data-source-view-cube-designer-analysis-services-multidimensional-data.md)  
  
  
