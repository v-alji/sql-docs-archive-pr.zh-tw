---
title: 透視圖詳細資料 (透視圖] 索引標籤、Cube 設計工具)  (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.perspectives.perspectivespane.perspectivedetails.f2
ms.assetid: b4d0ff9e-5ee7-470c-abc2-d748ac4c04e7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6fb28b5d4d833ec66e84f17f54237b4866adcdbb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599224"
---
# <a name="perspective-details-perspectives-tab-cube-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="8c4ea-102">檢視方塊詳細資料 (檢視方塊索引標籤，Cube 設計師) (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="8c4ea-102">Perspective Details (Perspectives Tab, Cube Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="8c4ea-103">使用 Cube 設計師中 **[檢視方塊]** 索引標籤上的 **[檢視方塊詳細資料]** 窗格，即可管理查詢所選檢視方塊之使用者可用的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="8c4ea-103">Use the **Perspective Details** pane on the **Perspectives** tab in Cube Designer to manage the metadata available to users who query the selected perspective.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8c4ea-104">選項</span><span class="sxs-lookup"><span data-stu-id="8c4ea-104">Options</span></span>  
 <span data-ttu-id="8c4ea-105">**Cube 物件**</span><span class="sxs-lookup"><span data-stu-id="8c4ea-105">**Cube Objects**</span></span>  
 <span data-ttu-id="8c4ea-106">顯示可包含在檢視方塊中的 Cube 所含之物件與屬性的階層清單。</span><span class="sxs-lookup"><span data-stu-id="8c4ea-106">Displays a hierarchical list of objects and properties contained in the cube that can be included in the perspective.</span></span>  
  
 <span data-ttu-id="8c4ea-107">**物件類型**</span><span class="sxs-lookup"><span data-stu-id="8c4ea-107">**Object Type**</span></span>  
 <span data-ttu-id="8c4ea-108">顯示可包含在檢視方塊中之 Cube 的物件類型或屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="8c4ea-108">Displays the object type or property name from the cube that can be included in the perspective.</span></span>  
  
 <span data-ttu-id="8c4ea-109">**檢視方塊名稱**</span><span class="sxs-lookup"><span data-stu-id="8c4ea-109">**Perspective Name**</span></span>  
 <span data-ttu-id="8c4ea-110">顯示屬性值與 Cube 物件是否包含在 [檢視方塊名稱]\*\*\*\* 資料行所代表的檢視方塊中。</span><span class="sxs-lookup"><span data-stu-id="8c4ea-110">Displays the property values and whether a cube object is included in the perspective represented by the **Perspective Name** column.</span></span> <span data-ttu-id="8c4ea-111">Cube 中的每個檢視方塊會列出一個 **[檢視方塊名稱]** 資料行。</span><span class="sxs-lookup"><span data-stu-id="8c4ea-111">One **Perspective Name** column is listed for each perspective in the cube.</span></span>  
  
 <span data-ttu-id="8c4ea-112">在所選檢視方塊之 Cube 的 **[名稱]** 屬性資料格中，鍵入檢視方塊的名稱。</span><span class="sxs-lookup"><span data-stu-id="8c4ea-112">Type the name of the perspective in the cell for the **Name** property of the cube for the selected perspective.</span></span>  
  
 <span data-ttu-id="8c4ea-113">在所選檢視方塊之 Cube 的 **[DefaultMeasure]** 屬性資料格中，選取檢視方塊的預設量值。</span><span class="sxs-lookup"><span data-stu-id="8c4ea-113">Select the default measure of the perspective in the cell for the **DefaultMeasure** property of the cube for the selected perspective.</span></span>  
  
 <span data-ttu-id="8c4ea-114">選取要包含在檢視方塊中的物件。</span><span class="sxs-lookup"><span data-stu-id="8c4ea-114">Select an object to include it in the perspective.</span></span>  
  
## <a name="context-menu"></a><span data-ttu-id="8c4ea-115">操作功能表</span><span class="sxs-lookup"><span data-stu-id="8c4ea-115">Context Menu</span></span>  
 <span data-ttu-id="8c4ea-116">以滑鼠右鍵按一下 [檢視方塊詳細資料]\*\*\*\* 窗格中所顯示檢視方塊的任何資料格，即可顯示提供下列選項的操作功能表：</span><span class="sxs-lookup"><span data-stu-id="8c4ea-116">The following options are available in the context menu displayed by right-clicking any cell in a perspective displayed in the **Perspective Details** pane:</span></span>  
  
|<span data-ttu-id="8c4ea-117">選項</span><span class="sxs-lookup"><span data-stu-id="8c4ea-117">Option</span></span>|<span data-ttu-id="8c4ea-118">描述</span><span class="sxs-lookup"><span data-stu-id="8c4ea-118">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="8c4ea-119">**新增檢視方塊**</span><span class="sxs-lookup"><span data-stu-id="8c4ea-119">**New Perspective**</span></span>|<span data-ttu-id="8c4ea-120">按一下即可在選取的 Cube 中建立新的檢視方塊。</span><span class="sxs-lookup"><span data-stu-id="8c4ea-120">Click to create a new perspective in the selected cube.</span></span>|  
|<span data-ttu-id="8c4ea-121">**刪除檢視方塊**</span><span class="sxs-lookup"><span data-stu-id="8c4ea-121">**Delete Perspective**</span></span>|<span data-ttu-id="8c4ea-122">按一下以顯示 [**刪除物件**] 對話方塊，並刪除選取的觀點</span><span class="sxs-lookup"><span data-stu-id="8c4ea-122">Click to display the **Delete Objects** dialog box and delete the selected perspective</span></span>|  
  
  
