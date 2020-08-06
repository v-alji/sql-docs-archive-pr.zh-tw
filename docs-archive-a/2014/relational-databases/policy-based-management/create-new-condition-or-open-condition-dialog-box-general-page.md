---
title: 建立新條件或開啟條件對話方塊，一般頁面 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.condition.f1
ms.assetid: 106954bf-e4ba-412b-9c1a-907d06153dcd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 72e4a77df553ac8e97609e82bd51c8fd93b64b23
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606805"
---
# <a name="create-new-condition-or-open-condition-dialog-box-general-page"></a><span data-ttu-id="07d01-102">建立新條件或開啟條件對話方塊，一般頁面</span><span class="sxs-lookup"><span data-stu-id="07d01-102">Create New Condition or Open Condition Dialog Box, General Page</span></span>
  <span data-ttu-id="07d01-103">使用此對話方塊可建立或變更以原則為基礎的管理條件。</span><span class="sxs-lookup"><span data-stu-id="07d01-103">Use this dialog box to create or change a Policy-Based Management condition.</span></span> <span data-ttu-id="07d01-104">條件是一種布林運算式，可指定以原則為基礎之管理 Managed 目標所允許的一組狀態 (與 Facet 有關)。</span><span class="sxs-lookup"><span data-stu-id="07d01-104">A condition is a Boolean expression that specifies a set of allowed states of a Policy-Based Management managed target with regard to facets.</span></span> <span data-ttu-id="07d01-105">可以在 [運算式/欄位]\*\*\*\* 方塊中選取的屬性需視所使用的 Facet 而定。</span><span class="sxs-lookup"><span data-stu-id="07d01-105">The properties that can be selected in the **Expression/Field** box depend upon the facet that is used.</span></span> <span data-ttu-id="07d01-106">如需條件如何與 Facet 和原則相關的詳細資訊，請參閱 [使用原則式管理來管理伺服器](administer-servers-by-using-policy-based-management.md)。</span><span class="sxs-lookup"><span data-stu-id="07d01-106">For more information about how conditions relate to facets and policies, see [Administer Servers by Using Policy-Based Management](administer-servers-by-using-policy-based-management.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="07d01-107">選項。</span><span class="sxs-lookup"><span data-stu-id="07d01-107">Options</span></span>  
 <span data-ttu-id="07d01-108">**名稱**</span><span class="sxs-lookup"><span data-stu-id="07d01-108">**Name**</span></span>  
 <span data-ttu-id="07d01-109">為新的條件輸入新的條件名稱。</span><span class="sxs-lookup"><span data-stu-id="07d01-109">For a new condition, type the new condition name.</span></span> <span data-ttu-id="07d01-110">如果是現有的條件，則會顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="07d01-110">For an existing condition, the name is displayed.</span></span>  
  
 <span data-ttu-id="07d01-111">**Facet**</span><span class="sxs-lookup"><span data-stu-id="07d01-111">**Facet**</span></span>  
 <span data-ttu-id="07d01-112">此條件所使用的 Facet。</span><span class="sxs-lookup"><span data-stu-id="07d01-112">The facet used by this condition.</span></span>  
  
 <span data-ttu-id="07d01-113">**AndOr**</span><span class="sxs-lookup"><span data-stu-id="07d01-113">**AndOr**</span></span>  
 <span data-ttu-id="07d01-114">當您加入多個運算式時，指出應該使用 **And** 還是 **Or**聯結運算式。</span><span class="sxs-lookup"><span data-stu-id="07d01-114">When you add multiple expressions, indicates whether the expressions should be joined by using **And** or **Or**.</span></span> <span data-ttu-id="07d01-115">只有當有一個運算式時，才保留空白。</span><span class="sxs-lookup"><span data-stu-id="07d01-115">Remains blank when there is only one expression.</span></span>  
  
 <span data-ttu-id="07d01-116">**欄位**</span><span class="sxs-lookup"><span data-stu-id="07d01-116">**Field**</span></span>  
 <span data-ttu-id="07d01-117">每一個 Facet 都會公開一或多個可以設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="07d01-117">Each facet exposes one or more properties that can be set.</span></span> <span data-ttu-id="07d01-118">在此欄位方塊中，請從可用的屬性清單中選取屬性，以便為這個條件建立運算式。</span><span class="sxs-lookup"><span data-stu-id="07d01-118">In the field box, select a property from the list of available properties to create an expression for this condition.</span></span>  
  
 <span data-ttu-id="07d01-119">**運算子**</span><span class="sxs-lookup"><span data-stu-id="07d01-119">**Operator**</span></span>  
 <span data-ttu-id="07d01-120">為這個運算式選取比較運算子。</span><span class="sxs-lookup"><span data-stu-id="07d01-120">Select a comparison operator for this expression.</span></span> <span data-ttu-id="07d01-121">運算子如下：=、!=、>、>=、<、<=、[NOT]LIKE、[NOT]IN。</span><span class="sxs-lookup"><span data-stu-id="07d01-121">Operators are as follows: =, !=, >, >=, <, <=, [NOT]LIKE, [NOT]IN.</span></span> <span data-ttu-id="07d01-122">並非所有運算子都適用於某些屬性。</span><span class="sxs-lookup"><span data-stu-id="07d01-122">Not all operators are available for some properties.</span></span>  
  
 <span data-ttu-id="07d01-123">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="07d01-123">**Value**</span></span>  
 <span data-ttu-id="07d01-124">這個運算式的值設定。</span><span class="sxs-lookup"><span data-stu-id="07d01-124">The value setting for this expression.</span></span> <span data-ttu-id="07d01-125">允許的值取決於此 Facet 而定。</span><span class="sxs-lookup"><span data-stu-id="07d01-125">The allowed values depend on the facet.</span></span> <span data-ttu-id="07d01-126">值可以是 TRUE/FALSE、字串或數字。</span><span class="sxs-lookup"><span data-stu-id="07d01-126">Values can be TRUE/FALSE, string, or numeric.</span></span> <span data-ttu-id="07d01-127">字串值必須括在單引號中，例如 **'AdventureWorks'**。</span><span class="sxs-lookup"><span data-stu-id="07d01-127">String values must be enclosed in single quotation marks, for example: **'AdventureWorks'**.</span></span> <span data-ttu-id="07d01-128">並非所有運算子都適用於某些屬性。</span><span class="sxs-lookup"><span data-stu-id="07d01-128">Not all operators are available for some properties.</span></span>  
  
## <a name="group-clauses"></a><span data-ttu-id="07d01-129">群組子句</span><span class="sxs-lookup"><span data-stu-id="07d01-129">Group Clauses</span></span>  
 <span data-ttu-id="07d01-130">子句可加以群組，使其當成單一單位來運作，並與查詢的其餘部分區隔開來，這種方式與在數學方程式或邏輯陳述式的運算式周圍放置括號類似。</span><span class="sxs-lookup"><span data-stu-id="07d01-130">Clauses can be grouped to operate as a single unit separate from the rest of the query, just like putting parentheses around an expression in a mathematical equation or logic statement.</span></span> <span data-ttu-id="07d01-131">當您建立複雜的查詢時，群組子句將會很實用。</span><span class="sxs-lookup"><span data-stu-id="07d01-131">Grouping clauses is useful when you are building complex queries.</span></span>  
  
 <span data-ttu-id="07d01-132">**群組子句**</span><span class="sxs-lookup"><span data-stu-id="07d01-132">**To group clauses**</span></span>  
  
-   <span data-ttu-id="07d01-133">按下 SHIFT 或 CTRL 鍵，然後按一下兩個或多個子句來選取範圍。</span><span class="sxs-lookup"><span data-stu-id="07d01-133">Press the SHIFT or CTRL keys, and then click two or more clauses to select a range.</span></span> <span data-ttu-id="07d01-134">以滑鼠右鍵按一下選取的區域，然後按一下 [群組子句]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="07d01-134">Right-click the selected area, and then click **Group Clauses**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07d01-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07d01-135">See Also</span></span>  
 [<span data-ttu-id="07d01-136">使用原則式管理來管理伺服器</span><span class="sxs-lookup"><span data-stu-id="07d01-136">Administer Servers by Using Policy-Based Management</span></span>](administer-servers-by-using-policy-based-management.md)  
  
  
