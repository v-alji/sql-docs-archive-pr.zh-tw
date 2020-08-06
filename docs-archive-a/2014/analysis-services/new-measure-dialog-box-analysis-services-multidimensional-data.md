---
title: '[新增量值] 對話方塊 (Analysis Services-多維度資料) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.newmeasuredialog.f1
helpviewer_keywords:
- New Measure dialog box
ms.assetid: 86dc9146-cc6d-4cef-b178-9a6b4cf616e8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1fb60bd598257d2de1f60900aafa43b085000fd8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710893"
---
# <a name="new-measure-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="f1eca-102">新增量值對話方塊 (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="f1eca-102">New Measure Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="f1eca-103">使用 **中的** [新增量值] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 對話方塊，即可將新量值加入至 Cube 設計師中的量值群組。</span><span class="sxs-lookup"><span data-stu-id="f1eca-103">Use the **New Measure** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to add a new measure to a measure group in Cube Designer.</span></span> <span data-ttu-id="f1eca-104">您可以藉由下列方式顯示 **[新增量值]** 對話方塊：</span><span class="sxs-lookup"><span data-stu-id="f1eca-104">You can display the **New Measure** dialog box by:</span></span>  
  
-   <span data-ttu-id="f1eca-105">在 Cube 設計師的 **[Cube 結構]** 索引標籤上，於 **[工具列]** 窗格中按一下 **[新增量值]** 。</span><span class="sxs-lookup"><span data-stu-id="f1eca-105">Clicking **New Measure** in the **Toolbar** pane on the **Cube Structure** tab in Cube Designer.</span></span>  
  
-   <span data-ttu-id="f1eca-106">在 Cube 設計師的 [Cube 結構]\*\*\*\* 索引標籤上，以滑鼠右鍵按一下 [量值]\*\*\*\* 窗格中的量值群組或量值，然後從內容功能表中選取 [新增量值]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f1eca-106">Right-clicking a measure group or measure in the **Measures** pane on the **Cube Structure** tab in Cube Designer and selecting **New Measure** from the context menu.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f1eca-107">選項</span><span class="sxs-lookup"><span data-stu-id="f1eca-107">Options</span></span>  
 <span data-ttu-id="f1eca-108">**使用量**</span><span class="sxs-lookup"><span data-stu-id="f1eca-108">**Usage**</span></span>  
 <span data-ttu-id="f1eca-109">選取新量值將使用的彙總函式。</span><span class="sxs-lookup"><span data-stu-id="f1eca-109">Select the aggregation function to be used by the new measure.</span></span>  
  
 <span data-ttu-id="f1eca-110">**來源資料表**</span><span class="sxs-lookup"><span data-stu-id="f1eca-110">**Source table**</span></span>  
 <span data-ttu-id="f1eca-111">選取將用於建立新量值的資料表。</span><span class="sxs-lookup"><span data-stu-id="f1eca-111">Select the table from which the new measure is to be created.</span></span>  
  
 <span data-ttu-id="f1eca-112">**來源資料行**</span><span class="sxs-lookup"><span data-stu-id="f1eca-112">**Source column**</span></span>  
 <span data-ttu-id="f1eca-113">在 [來源資料表]\*\*\*\* 所選取的資料表中，選取新量值將依據的資料行。</span><span class="sxs-lookup"><span data-stu-id="f1eca-113">Select the column in the table selected in **Source table** on which the new measure is to be based.</span></span>  
  
 <span data-ttu-id="f1eca-114">**顯示所有資料行**</span><span class="sxs-lookup"><span data-stu-id="f1eca-114">**Show all columns**</span></span>  
 <span data-ttu-id="f1eca-115">選取即可顯示量值群組之事實資料表中的所有資料行，該量值群組是要包含新量值的量值群組。</span><span class="sxs-lookup"><span data-stu-id="f1eca-115">Select to display all columns in the fact table for the measure group in which the new measure is to be created.</span></span> <span data-ttu-id="f1eca-116">如果未選取， **[來源資料行]** 就僅會顯示不作為邏輯主索引鍵或牽涉到關聯性的數值資料行。</span><span class="sxs-lookup"><span data-stu-id="f1eca-116">If not selected, **Source column** only displays numeric columns that are not used as logical primary keys or involved in relationships.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1eca-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1eca-117">See Also</span></span>  
 <span data-ttu-id="f1eca-118">[Cube 結構 &#40;Cube 設計師&#41; &#40;Analysis Services 多維度資料&#41;](cube-structure-cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="f1eca-118">[Cube Structure &#40;Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](cube-structure-cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="f1eca-119">Analysis Services 的設計工具和對話方塊 &#40;多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="f1eca-119">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
