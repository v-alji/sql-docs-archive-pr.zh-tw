---
title: 隱藏或凍結 (SSAS 表格式) 的資料行 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.hideunhidecolumnsdb.f1
ms.assetid: 5407aee5-6a07-4559-a2ba-2ca00a242f02
author: minewiskan
ms.author: owend
ms.openlocfilehash: 71398eecbc342b4e3f9c2445fef3023132266dac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687237"
---
# <a name="hide-or-freeze-columns-ssas-tabular"></a><span data-ttu-id="f9716-102">隱藏或凍結資料行 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="f9716-102">Hide or Freeze Columns (SSAS Tabular)</span></span>
  <span data-ttu-id="f9716-103">在模型設計師中，如果資料表中有您不想要顯示的資料行，可以暫時隱藏起來。</span><span class="sxs-lookup"><span data-stu-id="f9716-103">In the model designer, if there are columns that you don't want to display in a table, you can temporarily hide them.</span></span> <span data-ttu-id="f9716-104">隱藏資料行會讓您在螢幕上有更多的空間，以加入新的資料行或是只處理相關的資料行。</span><span class="sxs-lookup"><span data-stu-id="f9716-104">Hiding a column gives you more room on the screen to add new columns or to work with only relevant columns of data.</span></span> <span data-ttu-id="f9716-105">您可以從模型設計師的 [資料行]\*\*\*\* 功能表，以及從每個資料行標頭所提供的右鍵功能表，來隱藏及取消隱藏資料行。</span><span class="sxs-lookup"><span data-stu-id="f9716-105">You can hide and unhide columns from the **Column** menu in the model designer, and from the right-click menu available from each column header.</span></span> <span data-ttu-id="f9716-106">若要在捲動到模型其他區域時，讓某個模型區域保持可見，您可以執行凍結操作，將特定的資料行鎖定於一個區域之中。</span><span class="sxs-lookup"><span data-stu-id="f9716-106">To keep an area of a model visible while you scroll to another area of the model, you can lock specific columns in one area by freezing them.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f9716-107">隱藏資料行的功能並不是要用來提供資料安全性，而只是要在模型設計師或報表中簡化及縮短可見資料行清單。</span><span class="sxs-lookup"><span data-stu-id="f9716-107">The ability to hide columns is not intended to be used for data security, only to simplify and shorten the list of columns visible in the model designer or reports.</span></span> <span data-ttu-id="f9716-108">您可以定義安全性角色，以保護資料的安全性。</span><span class="sxs-lookup"><span data-stu-id="f9716-108">To secure data, you can define security roles.</span></span> <span data-ttu-id="f9716-109">角色可以限制只有角色中定義的物件，才可以檢視中繼資料和資料。</span><span class="sxs-lookup"><span data-stu-id="f9716-109">Roles can limit viewable metadata and data to only those objects defined in the role.</span></span> <span data-ttu-id="f9716-110">如需詳細資訊，請參閱 [角色 &#40;SSAS 表格式&#41;](roles-ssas-tabular.md)中撰寫的表格式模型專案。</span><span class="sxs-lookup"><span data-stu-id="f9716-110">For more information, see [Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="f9716-111">隱藏資料行時，可以選擇只有在模型設計師或報表中作業時才隱藏資料行。</span><span class="sxs-lookup"><span data-stu-id="f9716-111">When you hide a column, you have the option to hide the column while you are working in the model designer or in reports.</span></span> <span data-ttu-id="f9716-112">如果隱藏所有資料行，整個資料表在模型設計師中就會顯示為空白。</span><span class="sxs-lookup"><span data-stu-id="f9716-112">If you hide all columns, the entire table appears blank in the model designer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f9716-113">如果您需要隱藏許多資料行，可以建立檢視方塊，而非隱藏並取消隱藏資料行。</span><span class="sxs-lookup"><span data-stu-id="f9716-113">If you have many columns to hide, you can create a perspective instead of hiding and unhiding columns.</span></span> <span data-ttu-id="f9716-114">檢視方塊是資料的自訂檢視，可讓您更輕鬆地使用相關資料的子集。</span><span class="sxs-lookup"><span data-stu-id="f9716-114">A perspective is a custom view of the data that makes it easier to work with subset of related data.</span></span> <span data-ttu-id="f9716-115">如需詳細資訊，請參閱[建立及管理檢視方塊 &#40;SSAS 表格式&#41;](perspectives-ssas-tabular.md)</span><span class="sxs-lookup"><span data-stu-id="f9716-115">For more information, see [Create and Manage Perspectives &#40;SSAS Tabular&#41;](perspectives-ssas-tabular.md)</span></span>  
  
### <a name="to-hide-an-individual-column"></a><span data-ttu-id="f9716-116">隱藏個別資料行</span><span class="sxs-lookup"><span data-stu-id="f9716-116">To hide an individual column</span></span>  
  
1.  <span data-ttu-id="f9716-117">在模型設計師中，選取包含所要隱藏資料行的資料表。</span><span class="sxs-lookup"><span data-stu-id="f9716-117">In the model designer, select the table that contains the column that you want to hide.</span></span>  
  
2.  <span data-ttu-id="f9716-118">以滑鼠右鍵按一下資料行，然後按一下 [隱藏資料行]\*\*\*\*，再按一下 [從設計師和報表]\*\*\*\*、[從報表]\*\*\*\* 或 [從設計師]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f9716-118">Right-click the column, then click **Hide Columns**, and then click **From Designer and Reports**, **From Reports**, or **From Designer**.</span></span>  
  
### <a name="to-hide-multiple-columns"></a><span data-ttu-id="f9716-119">隱藏多個資料行</span><span class="sxs-lookup"><span data-stu-id="f9716-119">To hide multiple columns</span></span>  
  
1.  <span data-ttu-id="f9716-120">在模型設計師中，選取包含所要隱藏資料行的資料表。</span><span class="sxs-lookup"><span data-stu-id="f9716-120">In the model designer, select the table that contains the columns that you want to hide.</span></span>  
  
2.  <span data-ttu-id="f9716-121">按一下 [資料行]\*\*\*\* 功能表，然後按一下 [隱藏和取消隱藏]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f9716-121">Click on the **Columns** menu, and then click **Hide and Unhide**.</span></span>  
  
3.  <span data-ttu-id="f9716-122">在 [隱藏和取消隱藏資料行]\*\*\*\* 對話方塊中，找出所要隱藏的每個資料行，然後取消選取 [在設計師中]\*\*\*\* 及/或 [在報表中]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f9716-122">In the **Hide and Unhide Columns** dialog box, locate each column that you want to hide, and then deselect one or both of **In Designer** and **In Reports**.</span></span>  
  
4.  <span data-ttu-id="f9716-123">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="f9716-123">Click **OK**.</span></span>  
  
### <a name="to-freeze-columns"></a><span data-ttu-id="f9716-124">凍結資料行</span><span class="sxs-lookup"><span data-stu-id="f9716-124">To freeze columns</span></span>  
  
1.  <span data-ttu-id="f9716-125">在模型設計師中，選取包含所要凍結資料行的資料表。</span><span class="sxs-lookup"><span data-stu-id="f9716-125">In the model designer, select the table that contains the columns that you want to freeze.</span></span>  
  
2.  <span data-ttu-id="f9716-126">選取一個或多個要凍結的資料行。</span><span class="sxs-lookup"><span data-stu-id="f9716-126">Select one or more columns to freeze.</span></span>  
  
3.  <span data-ttu-id="f9716-127">按一下 [資料行]\*\*\*\* 功能表，然後按一下 [凍結]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f9716-127">Click on the **Columns** menu, and then click **Freeze**..</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f9716-128">凍結資料行時，該資料行會移至設計師之資料表的左方 (或上方)。</span><span class="sxs-lookup"><span data-stu-id="f9716-128">When a column(s) is frozen, it is moved to left (or front) of the table in the designer.</span></span> <span data-ttu-id="f9716-129">取消凍結資料行不會將資料行移回其原始位置。</span><span class="sxs-lookup"><span data-stu-id="f9716-129">Unfreezing the column does not move it back to its original location.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9716-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9716-130">See Also</span></span>  
 <span data-ttu-id="f9716-131">[&#40;SSAS 表格式&#41;的資料表和資料行](tables-and-columns-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="f9716-131">[Tables and Columns &#40;SSAS Tabular&#41;](tables-and-columns-ssas-tabular.md) </span></span>  
 <span data-ttu-id="f9716-132">[SSAS 表格式 &#40;的觀點&#41;](perspectives-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="f9716-132">[Perspectives &#40;SSAS Tabular&#41;](perspectives-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="f9716-133">角色 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="f9716-133">Roles &#40;SSAS Tabular&#41;</span></span>](roles-ssas-tabular.md)  
  
  
