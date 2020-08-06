---
title: " () 採礦結構視圖中，選取 [嵌套資料表索引鍵資料行] 對話方塊 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.structure.addnestedtable.f1
helpviewer_keywords:
- Select a Nested Table Key Column dialog box
ms.assetid: f68b89a7-17df-45f8-ba7f-b458cd9b1ec3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4dc524f6913b7be15e87869355515397a3e0b65c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598569"
---
# <a name="select-a-nested-table-key-column-dialog-box-mining-structure-view"></a><span data-ttu-id="aa0af-102">選取巢狀資料表索引鍵資料行對話方塊 (採礦結構檢視)</span><span class="sxs-lookup"><span data-stu-id="aa0af-102">Select a Nested Table Key Column Dialog Box (Mining Structure View)</span></span>
  <span data-ttu-id="aa0af-103">使用 **[選取巢狀資料表索引鍵資料行]** 對話方塊，即可指定將作為新巢狀資料表之索引鍵的資料行。</span><span class="sxs-lookup"><span data-stu-id="aa0af-103">Use the **Select a Nested Table Key Column** dialog box to designate a column that will act as the key for the new nested table.</span></span> <span data-ttu-id="aa0af-104">當您結束對話方塊時，會將新資料表加入至包含指定索引鍵資料行的採礦結構。</span><span class="sxs-lookup"><span data-stu-id="aa0af-104">When you exit the dialog box, a new table is added to the mining structure that contains the designated key column.</span></span> <span data-ttu-id="aa0af-105">以滑鼠右鍵按一下結構，然後選取 [加入資料行]\*\*\*\*，即可將其他資料行加入至巢狀資料表。</span><span class="sxs-lookup"><span data-stu-id="aa0af-105">You can add additional columns to the nested table by right-clicking the structure and selecting **Add a Column**.</span></span> <span data-ttu-id="aa0af-106">視您正在處理 OLAP 採礦模型或是關聯式採礦模型而定，此對話方塊會包含不同的選項。</span><span class="sxs-lookup"><span data-stu-id="aa0af-106">The dialog box contains different options depending on whether you are working with an OLAP mining model or a relational mining model.</span></span>  
  
## <a name="options"></a><span data-ttu-id="aa0af-107">選項</span><span class="sxs-lookup"><span data-stu-id="aa0af-107">Options</span></span>  
 <span data-ttu-id="aa0af-108">**來源資料表**</span><span class="sxs-lookup"><span data-stu-id="aa0af-108">**Source table**</span></span>  
 <span data-ttu-id="aa0af-109">作為採礦模型基礎的資料表。</span><span class="sxs-lookup"><span data-stu-id="aa0af-109">The table on which the mining model is based.</span></span>  
  
 <span data-ttu-id="aa0af-110">這只用於關聯式採礦模型。</span><span class="sxs-lookup"><span data-stu-id="aa0af-110">This is only used for relational mining models.</span></span>  
  
 <span data-ttu-id="aa0af-111">**來源資料行**</span><span class="sxs-lookup"><span data-stu-id="aa0af-111">**Source column**</span></span>  
 <span data-ttu-id="aa0af-112">在來源資料表中，您可以用來作為巢狀資料表之索引鍵的所有可用資料行清單。</span><span class="sxs-lookup"><span data-stu-id="aa0af-112">A list of all the available columns in the source table that you can use as the key of the nested table.</span></span>  
  
 <span data-ttu-id="aa0af-113">這只用於關聯式採礦模型。</span><span class="sxs-lookup"><span data-stu-id="aa0af-113">This is only used for relational mining models.</span></span>  
  
 <span data-ttu-id="aa0af-114">**顯示資料行類型**</span><span class="sxs-lookup"><span data-stu-id="aa0af-114">**Show column types**</span></span>  
 <span data-ttu-id="aa0af-115">可用資料行資料類型的清單。</span><span class="sxs-lookup"><span data-stu-id="aa0af-115">A list of available column data types.</span></span> <span data-ttu-id="aa0af-116">選取或清除資料類型，以篩選 **[來源資料行]** 中的資料行清單。</span><span class="sxs-lookup"><span data-stu-id="aa0af-116">Select or clear data types to filter the list of columns in **Source column**.</span></span> <span data-ttu-id="aa0af-117">在 **[來源資料行]** 清單中，只會顯示與核取的資料類型相符的資料行。</span><span class="sxs-lookup"><span data-stu-id="aa0af-117">Only columns that match the checked data types will be shown in the **Source column** list.</span></span>  
  
 <span data-ttu-id="aa0af-118">這只用於關聯式採礦模型。</span><span class="sxs-lookup"><span data-stu-id="aa0af-118">This is only used for relational mining models.</span></span>  
  
 <span data-ttu-id="aa0af-119">**屬性**</span><span class="sxs-lookup"><span data-stu-id="aa0af-119">**Attributes**</span></span>  
 <span data-ttu-id="aa0af-120">您可以用來作為巢狀資料表之索引鍵的屬性清單。</span><span class="sxs-lookup"><span data-stu-id="aa0af-120">A list of attributes that you can use as the key of the nested table.</span></span>  
  
 <span data-ttu-id="aa0af-121">此選項只用於 OLAP 採礦模型。</span><span class="sxs-lookup"><span data-stu-id="aa0af-121">This is only used for OLAP mining models.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa0af-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa0af-122">See Also</span></span>  
 [<span data-ttu-id="aa0af-123">&#40;資料採礦模型設計工具的「採礦結構視圖」&#41;</span><span class="sxs-lookup"><span data-stu-id="aa0af-123">Mining Structure View &#40;Data Mining Model Designer&#41;</span></span>](mining-structure-view-data-mining-model-designer.md)  
  
  
