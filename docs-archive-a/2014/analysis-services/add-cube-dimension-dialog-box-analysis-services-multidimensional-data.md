---
title: '[加入 Cube 維度] 對話方塊 (Analysis Services-多維度資料) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.addcubedimensiondialog.f1
helpviewer_keywords:
- Add Cube Dimension dialog box
ms.assetid: 625a3b1f-183b-445f-9bb7-96945c324767
author: minewiskan
ms.author: owend
ms.openlocfilehash: d0de75c02c39b0690184f35f2b0b6a07d7ed9a4f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592345"
---
# <a name="add-cube-dimension-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="f4800-102">加入 Cube 維度對話方塊 (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="f4800-102">Add Cube Dimension Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="f4800-103">使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中的 [加入 Cube 維度]\*\*\*\* 對話方塊，即可將資料庫維度的參考加入 Cube。</span><span class="sxs-lookup"><span data-stu-id="f4800-103">Use the **Add Cube Dimension** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to add a reference to a database dimension to a cube.</span></span> <span data-ttu-id="f4800-104">您可以執行下列其中一個動作，來顯示 [加入 Cube 維度]\*\*\*\* 對話方塊：</span><span class="sxs-lookup"><span data-stu-id="f4800-104">You can display the **Add Cube Dimension** dialog box by doing one of the following:</span></span>  
  
-   <span data-ttu-id="f4800-105">在 Cube 設計師之 [Cube 結構]\*\*\*\* 或 [維度使用方式]\*\*\*\* 索引標籤的 [工具列]\*\*\*\* 窗格中，按一下 [加入 Cube 維度]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f4800-105">Click **Add Cube Dimension** in the **Toolbar** pane on the **Cube Structure** or **Dimension Usage** tab in Cube Designer.</span></span>  
  
-   <span data-ttu-id="f4800-106">在 Cube 設計師的 [Cube 結構]\*\*\*\* 索引標籤上，以滑鼠右鍵按一下 [維度]\*\*\*\* 窗格，然後從操作功能表中選取 [加入 Cube 維度]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f4800-106">Right-click the **Dimensions** pane on the **Cube Structure** tab in Cube Designer and select **Add Cube Dimension** from the context menu.</span></span>  
  
-   <span data-ttu-id="f4800-107">在 Cube 設計師的 [維度使用方式]\*\*\*\* 索引標籤上，以滑鼠右鍵按一下 [方格]\*\*\*\* 窗格，然後從操作功能表中選取 [加入 Cube 維度]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f4800-107">Right-click the **Grid** pane on the **Dimension Usage** tab in Cube Designer and select **Add Cube Dimension** from the context menu.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f4800-108">每個 Cube 維度對量值群組只能有一個關聯性。</span><span class="sxs-lookup"><span data-stu-id="f4800-108">Each cube dimension can have only one relationship to a measure group.</span></span> <span data-ttu-id="f4800-109">不過，如果 Cube 維度所依據的資料庫維度，在資料來源檢視中透過一個以上的關聯性與量值群組相關，則您可以建立一個以上的 Cube 維度並將其加入至 Cube。</span><span class="sxs-lookup"><span data-stu-id="f4800-109">However, you can create more than one cube dimension and add it to the cube, if the database dimension on which the cube dimension is based is related to measure groups through more than one relationship in the data source view.</span></span> <span data-ttu-id="f4800-110">此類維度被稱為角色扮演維度，且一般是和時間維度一起發生。</span><span class="sxs-lookup"><span data-stu-id="f4800-110">Such dimensions are referred to as role-playing dimensions and commonly occur with time dimensions.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f4800-111">選項</span><span class="sxs-lookup"><span data-stu-id="f4800-111">Options</span></span>  
 <span data-ttu-id="f4800-112">**選取維度**</span><span class="sxs-lookup"><span data-stu-id="f4800-112">**Select dimension**</span></span>  
 <span data-ttu-id="f4800-113">選取現有的資料庫維度，即可將依據此資料庫維度的 Cube 維度加入至選取的 Cube。</span><span class="sxs-lookup"><span data-stu-id="f4800-113">Select an existing database dimension to add a cube dimension based on it to the selected cube.</span></span> <span data-ttu-id="f4800-114">從相同資料庫維度中可以定義多個 Cube 維度。</span><span class="sxs-lookup"><span data-stu-id="f4800-114">Multiple cube dimensions can be defined from the same database dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f4800-115">如果有依據相同資料庫維度之一個以上的 Cube 維度加入至一個 Cube，則其他的 Cube 維度會被稱為角色扮演維度。</span><span class="sxs-lookup"><span data-stu-id="f4800-115">If more than one cube dimension based on the same database dimension is added to a cube, the additional cube dimensions are called role-playing dimensions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4800-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4800-116">See Also</span></span>  
 [<span data-ttu-id="f4800-117">Analysis Services 的設計工具和對話方塊 &#40;多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="f4800-117">Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;</span></span>](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
