---
title: 空間結果視窗
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c2d5a477-6496-4d01-adee-7322ebdfadf3
author: rothja
ms.author: jroth
ms.openlocfilehash: 5e018ec9f016dfc51ed1bb055ba94abf12bc878f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710545"
---
# <a name="spatial-results-window"></a><span data-ttu-id="91bab-102">空間結果視窗</span><span class="sxs-lookup"><span data-stu-id="91bab-102">Spatial Results Window</span></span>
  <span data-ttu-id="91bab-103">[空間結果]  視窗會提供檢視空間資料的視覺化對應工具。</span><span class="sxs-lookup"><span data-stu-id="91bab-103">The **Spatial results** window provides visual mapping tools for viewing spatial data.</span></span> <span data-ttu-id="91bab-104">若要檢視空間結果，您的查詢結果必須包含一個具有幾何或地理位置資料的空間資料行。</span><span class="sxs-lookup"><span data-stu-id="91bab-104">To view spatial results, your query results must include a spatial column with either geometry or geography data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="91bab-105">只有當您的結果傳回至 [結果] 視窗中的方格時，才能使用 [空間結果] 視窗。</span><span class="sxs-lookup"><span data-stu-id="91bab-105">The **Spatial results** window is only available if your results are returned to a grid in the **Results** window.</span></span> <span data-ttu-id="91bab-106">如果您指定要將結果傳回成文字，就無法使用這個視窗。</span><span class="sxs-lookup"><span data-stu-id="91bab-106">If you specify that your results are returned as text, this window is not available.</span></span>  
  
## <a name="options"></a><span data-ttu-id="91bab-107">選項。</span><span class="sxs-lookup"><span data-stu-id="91bab-107">Options</span></span>  
 <span data-ttu-id="91bab-108">**選取空間資料行**</span><span class="sxs-lookup"><span data-stu-id="91bab-108">**Select spatial column**</span></span>  
 <span data-ttu-id="91bab-109">在查詢結果的空間資料行中，指定您想要檢視的空間資料行。</span><span class="sxs-lookup"><span data-stu-id="91bab-109">Specify the spatial column you want to view from the spatial columns in the query results.</span></span> <span data-ttu-id="91bab-110">一次只能選取一個資料行。</span><span class="sxs-lookup"><span data-stu-id="91bab-110">Only one column can be selected at a time.</span></span>  
  
 <span data-ttu-id="91bab-111">**選取標籤資料行**</span><span class="sxs-lookup"><span data-stu-id="91bab-111">**Select label column**</span></span>  
 <span data-ttu-id="91bab-112">在查詢結果所傳回的資料行中，指定要標示空間資料的非空間資料行。</span><span class="sxs-lookup"><span data-stu-id="91bab-112">Specify the non-spatial column from the columns returned in the query results to label the spatial data.</span></span> <span data-ttu-id="91bab-113">一次只能選取一個資料行。</span><span class="sxs-lookup"><span data-stu-id="91bab-113">Only one column can be selected at a time.</span></span>  
  
 <span data-ttu-id="91bab-114">當查詢只有傳回 Point 執行個體時，就無法使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="91bab-114">This option is not available when only point instances are returned in a query.</span></span>  
  
 <span data-ttu-id="91bab-115">**選取投射**</span><span class="sxs-lookup"><span data-stu-id="91bab-115">**Select projection**</span></span>  
 <span data-ttu-id="91bab-116">以四種投射的其中一種來顯示地理位置資料：Equirectangular、Mercator、Robinson 或 Bonne。</span><span class="sxs-lookup"><span data-stu-id="91bab-116">Display geography data in one of four projections: Equirectangular, Mercator, Robinson, or Bonne.</span></span>  
  
 <span data-ttu-id="91bab-117">幾何資料無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="91bab-117">This option is not available for geometry data.</span></span>  
  
 <span data-ttu-id="91bab-118">**Zoom**</span><span class="sxs-lookup"><span data-stu-id="91bab-118">**Zoom**</span></span>  
 <span data-ttu-id="91bab-119">在指數刻度上調整對應顯示。</span><span class="sxs-lookup"><span data-stu-id="91bab-119">Adjust the map display on an exponential scale.</span></span>  
  
 <span data-ttu-id="91bab-120">**顯示格線**</span><span class="sxs-lookup"><span data-stu-id="91bab-120">**Show grid lines**</span></span>  
 <span data-ttu-id="91bab-121">開啟或關閉座標格線。</span><span class="sxs-lookup"><span data-stu-id="91bab-121">Toggle coordinate gridlines on or off.</span></span>  
  
 <span data-ttu-id="91bab-122">若為多邊形形狀，只有當此形狀夠大，足以容納標籤文字時，才會顯示標籤。</span><span class="sxs-lookup"><span data-stu-id="91bab-122">For polygon shapes, the label is displayed only when the shape is large enough to hold the label text.</span></span> <span data-ttu-id="91bab-123">若要顯示小型形狀的標籤，請調整顯示比例。</span><span class="sxs-lookup"><span data-stu-id="91bab-123">To display labels for small shapes, adjust the zoom.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="91bab-124">您無法標示 Point 執行個體。</span><span class="sxs-lookup"><span data-stu-id="91bab-124">Point instances cannot be labeled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91bab-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91bab-125">See Also</span></span>  
 <span data-ttu-id="91bab-126">[檢視物件總管中的空間資料](view-spatial-data-in-object-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="91bab-126">[View Spatial Data in Object Explorer](view-spatial-data-in-object-explorer.md) </span></span>  
 <span data-ttu-id="91bab-127">[空間資料 &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="91bab-127">[Spatial Data &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md) </span></span>  
 <span data-ttu-id="91bab-128">[Database Engine 查詢編輯器 &#40;SQL Server Management Studio&#41;](database-engine-query-editor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="91bab-128">[Database Engine Query Editor &#40;SQL Server Management Studio&#41;](database-engine-query-editor-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="91bab-129">查詢與文字編輯器 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="91bab-129">Query and Text Editors &#40;SQL Server Management Studio&#41;</span></span>](query-and-text-editors-sql-server-management-studio.md)  
  
  
