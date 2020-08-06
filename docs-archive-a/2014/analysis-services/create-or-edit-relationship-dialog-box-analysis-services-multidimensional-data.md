---
title: 建立或編輯關聯性對話方塊 (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.createrelationship.f1
helpviewer_keywords:
- Create Relationship dialog box
ms.assetid: da3c7074-623e-4ddf-a707-d3276a47cf1c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4edae3f78ac6b764d91e1be97787fe59d49421db
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594279"
---
# <a name="create-or-edit-relationship-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="e5204-102">建立或編輯關聯性對話方塊 (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="e5204-102">Create or Edit Relationship Dialog Box (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="e5204-103">使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中的 [Create/Edit Relationship (建立/編輯關聯性)]\*\*\*\* 對話方塊，即可定義或修改資料來源檢視中的關聯性。</span><span class="sxs-lookup"><span data-stu-id="e5204-103">Use the **Create/Edit Relationship** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to define or modify a relationship in a data source view.</span></span> <span data-ttu-id="e5204-104">您可以用下列方式來顯示 [Create/Edit Relationship (建立/編輯關聯性)]\*\*\*\* 對話方塊：</span><span class="sxs-lookup"><span data-stu-id="e5204-104">You can display the **Create/Edit Relationship** dialog box by:</span></span>  
  
-   <span data-ttu-id="e5204-105">按一下 [Data Source View Designer (資料來源檢視設計工具)]\*\*\*\* 之 [工具列]\*\*\*\* 窗格中的 [新增關聯性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e5204-105">Clicking **New Relationship** in the **Toolbar** pane of **Data Source View Designer**.</span></span>  
  
-   <span data-ttu-id="e5204-106">以滑鼠右鍵按一下 [Data Source View Designer (資料來源檢視設計工具)]\*\*\*\* 之 [資料表]\*\*\*\* 或 [圖表]\*\*\*\* 窗格中的資料表，並選取 [新增關聯性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e5204-106">Right-clicking a table in either the **Tables** or **Diagram** pane of **Data Source View Designer** and selecting **New Relationship**.</span></span>  
  
-   <span data-ttu-id="e5204-107">以滑鼠右鍵按一下 [Data Source View Designer (資料來源檢視設計工具)]\*\*\*\* 之 [圖表]\*\*\*\* 窗格中的關聯性，並選取 [編輯關聯性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e5204-107">Right-clicking a relationship in the **Diagram** pane of **Data Source View Designer** and selecting **Edit Relationship**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e5204-108">您可以在 [資料來源檢視設計師]\*\*\*\* 中，建立不存在於基礎資料來源的關聯性，也可以從基礎資料來源的現有外部索引鍵關聯性，移除**資料來源檢視設計師**所建立的關聯性。</span><span class="sxs-lookup"><span data-stu-id="e5204-108">You can create relationships in **Data Source View Designer** that do not exist in the underlying data source, and remove relationships created by **Data Source View Designer** from existing foreign key relationships in the underlying data source.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e5204-109">選項</span><span class="sxs-lookup"><span data-stu-id="e5204-109">Options</span></span>  
 <span data-ttu-id="e5204-110">**來源 (外部索引鍵) 資料表**</span><span class="sxs-lookup"><span data-stu-id="e5204-110">**Source (foreign key) table**</span></span>  
 <span data-ttu-id="e5204-111">選取包含參考目的地資料表中之一個或多個資料行的資料表或具名查詢。</span><span class="sxs-lookup"><span data-stu-id="e5204-111">Select the table or named query that contains the reference to one or more columns in the destination table.</span></span>  
  
 <span data-ttu-id="e5204-112">**目的地 (主索引鍵) 資料表**</span><span class="sxs-lookup"><span data-stu-id="e5204-112">**Destination (primary key) table**</span></span>  
 <span data-ttu-id="e5204-113">選取包含來源資料表所參考之一個或多個資料行的資料表。</span><span class="sxs-lookup"><span data-stu-id="e5204-113">Select the table that contains one or more columns referenced by the source table.</span></span> <span data-ttu-id="e5204-114">針對自我聯結，選取與在 [來源 (外部索引鍵) 資料表]\*\*\*\* 中所選取的相同資料表。</span><span class="sxs-lookup"><span data-stu-id="e5204-114">For self-joins, select the same table selected in **Source (foreign key) table**.</span></span>  
  
 <span data-ttu-id="e5204-115">**來源資料行**</span><span class="sxs-lookup"><span data-stu-id="e5204-115">**Source columns**</span></span>  
 <span data-ttu-id="e5204-116">選取會參考目的地資料表中之資料行的資料行。</span><span class="sxs-lookup"><span data-stu-id="e5204-116">Select the columns that reference columns in the destination table.</span></span>  
  
 <span data-ttu-id="e5204-117">**目的地資料行**</span><span class="sxs-lookup"><span data-stu-id="e5204-117">**Destination columns**</span></span>  
 <span data-ttu-id="e5204-118">選取來源資料表中之資料行所參考的資料行。</span><span class="sxs-lookup"><span data-stu-id="e5204-118">Select the columns that are referenced by columns in the source table.</span></span>  
  
 <span data-ttu-id="e5204-119">**反向**</span><span class="sxs-lookup"><span data-stu-id="e5204-119">**Reverse**</span></span>  
 <span data-ttu-id="e5204-120">按一下即可反轉關聯性的方向。</span><span class="sxs-lookup"><span data-stu-id="e5204-120">Click to reverse the direction of the relationship.</span></span>  
  
 <span data-ttu-id="e5204-121">**說明**</span><span class="sxs-lookup"><span data-stu-id="e5204-121">**Description**</span></span>  
 <span data-ttu-id="e5204-122">選擇性地鍵入關聯性的描述。</span><span class="sxs-lookup"><span data-stu-id="e5204-122">Type an optional description for the relationship.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5204-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5204-123">See Also</span></span>  
 <span data-ttu-id="e5204-124">[Analysis Services 的設計工具和對話方塊 &#40;多維度資料&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="e5204-124">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="e5204-125">資料來源檢視設計工具 &#40;Analysis Services - 多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="e5204-125">Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](data-source-view-designer-analysis-services-multidimensional-data.md)  
  
  
