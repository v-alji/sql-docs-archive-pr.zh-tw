---
title: 連結量值群組 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- linked measure groups [Analysis Services]
- referencing measure groups
- Linked Measure Group Wizard
- measure groups [Analysis Services], linked
- linked dimensions [Analysis Services]
ms.assetid: 7f838452-8669-4194-8e15-7afdc7f15251
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2a7d7443b8c25f5cbafa5af83364ef05d8053145
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596369"
---
# <a name="linked-measure-groups"></a><span data-ttu-id="b1604-102">連結量值群組</span><span class="sxs-lookup"><span data-stu-id="b1604-102">Linked Measure Groups</span></span>
  <span data-ttu-id="b1604-103">連結的量值群組會以相同資料庫或不同的 Analysis Services 資料庫中不同之 Cube 中的另一個量值群組為基礎。</span><span class="sxs-lookup"><span data-stu-id="b1604-103">A linked measure group is based on another measure group in a different cube within the same database or a different Analysis Services database.</span></span> <span data-ttu-id="b1604-104">如果您想要重複使用多個 Cube 中的一組量值及對應的資料值，您可使用連結量值群組。</span><span class="sxs-lookup"><span data-stu-id="b1604-104">You might use a linked measure group if you want to reuse a set of measures, and the corresponding data values, in multiple cubes.</span></span>  
  
 <span data-ttu-id="b1604-105">Microsoft 建議原始和連結的量值群組皆位於同一部伺服器上所執行的解決方案中。</span><span class="sxs-lookup"><span data-stu-id="b1604-105">Microsoft recommends that the original and linked measure groups reside in solutions that run on the same server.</span></span> <span data-ttu-id="b1604-106">連結到遠端伺服器上的量值群組已排定在未來的版本中淘汰 (請參閱[SQL Server 2014) 中已取代的 Analysis Services 功能](../deprecated-analysis-services-features-in-sql-server-2014.md)。</span><span class="sxs-lookup"><span data-stu-id="b1604-106">Linking to a measure group on a remote server is scheduled for deprecation in a future release (see [Deprecated Analysis Services Features in SQL Server 2014](../deprecated-analysis-services-features-in-sql-server-2014.md)).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b1604-107">連結量值群組是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="b1604-107">Linked measure groups are read-only.</span></span> <span data-ttu-id="b1604-108">若要挑選最新的變更，您必須先刪除所有連結量值群組，再根據修改的來源物件重新建立連結量值群組。</span><span class="sxs-lookup"><span data-stu-id="b1604-108">To pick up the latest changes, you must delete and recreate all linked measure groups based on the modified source object.</span></span> <span data-ttu-id="b1604-109">基於這個理由，未來需要修改量值群組時，建議您考慮在專案之間複製並貼上量值群組這個替代方法。</span><span class="sxs-lookup"><span data-stu-id="b1604-109">For this reason, copy and pasting measure groups between projects is an alternative approach that you should consider in case future modifications to the measure group are required.</span></span>  
  
## <a name="usage-limitations"></a><span data-ttu-id="b1604-110">使用方式的限制</span><span class="sxs-lookup"><span data-stu-id="b1604-110">Usage Limitations</span></span>  
 <span data-ttu-id="b1604-111">如同先前所註明，使用連結量值的一個重要限制就是無法直接自訂連結量值。</span><span class="sxs-lookup"><span data-stu-id="b1604-111">As noted previously, an important constraint to using linked measures is an inability to customize a linked measure directly.</span></span> <span data-ttu-id="b1604-112">修改資料類型、格式、資料繫結和可見度以及量值群組本身之項目的成員資格是原始量值群組中所必須進行的所有變更。</span><span class="sxs-lookup"><span data-stu-id="b1604-112">Modifications to the data type, format, data binding, and visibility, as well as membership of the items in the measure group itself, are all changes that must be made in the original measure group.</span></span>  
  
 <span data-ttu-id="b1604-113">就作業上而言，透過用戶端應用程式進行存取時，連結量值群組與其他量值群組相同，而查詢方式也與其他量值群組相同。</span><span class="sxs-lookup"><span data-stu-id="b1604-113">Operationally, linked measure groups are identical to other measure groups when accessed by client applications, and are queried in the same manner as other measure groups.</span></span>  
  
 <span data-ttu-id="b1604-114">查詢含有連結量值群組的 Cube 時，會在目的地 Cube 的第一次計算行程中，建立和解析連結。</span><span class="sxs-lookup"><span data-stu-id="b1604-114">When you query a cube that contains a linked measure group, the link is established and resolved during the first calculation pass of the destination cube.</span></span> <span data-ttu-id="b1604-115">因為這樣的行為，所以在評估查詢之前，無法解析儲存在連結量值群組中的任何計算。</span><span class="sxs-lookup"><span data-stu-id="b1604-115">Because of this behavior, any calculations that are stored in the linked measure group cannot be resolved before the query is evaluated.</span></span> <span data-ttu-id="b1604-116">換句話說，必須在目的地 Cube 中重新建立導出量值和導出資料格，而不是從來源 Cube 繼承而來。</span><span class="sxs-lookup"><span data-stu-id="b1604-116">In other words, calculated measures and calculated cells must be recreated in the destination cube rather than inherited from the source cube.</span></span>  
  
 <span data-ttu-id="b1604-117">下列清單摘要說明使用上的限制。</span><span class="sxs-lookup"><span data-stu-id="b1604-117">The following list summarizes usage limitations.</span></span>  
  
-   <span data-ttu-id="b1604-118">您不可從另一個連結量值群組建立連結量值群組。</span><span class="sxs-lookup"><span data-stu-id="b1604-118">You cannot create a linked measure group from another linked measure group.</span></span>  
  
-   <span data-ttu-id="b1604-119">您不可在連結量值群組中加入或移除量值。</span><span class="sxs-lookup"><span data-stu-id="b1604-119">You cannot add or remove measures in a linked measure group.</span></span> <span data-ttu-id="b1604-120">成員資格只會定義在原始量值群組中。</span><span class="sxs-lookup"><span data-stu-id="b1604-120">Membership is defined only in the original measure group.</span></span>  
  
-   <span data-ttu-id="b1604-121">連結量值群組不支援回寫。</span><span class="sxs-lookup"><span data-stu-id="b1604-121">Writeback is not supported in linked measure groups.</span></span>  
  
-   <span data-ttu-id="b1604-122">連結量值群組無法用於多個多對多關聯性，特別是當這些關聯性位於不同 Cube 時。</span><span class="sxs-lookup"><span data-stu-id="b1604-122">Linked measure groups cannot be used in multiple many-to-many relationships, especially when those relationships are in different cubes.</span></span> <span data-ttu-id="b1604-123">這樣做可能會導致模糊不清的彙總。</span><span class="sxs-lookup"><span data-stu-id="b1604-123">Doing so can result in ambiguous aggregations.</span></span> <span data-ttu-id="b1604-124">如需詳細資訊，請參閱 [Incorrect Amounts for Linked Measures in Cubes containing Many-to-Many Relationships (SSAS Troubleshooting)](https://social.technet.microsoft.com/wiki/contents/articles/22911.incorrect-amounts-for-linked-measures-in-cubes-containing-many-to-many-relationships-ssas-troubleshooting.aspx)(包含多對多關聯性之 Cube 中連結量值的數量不正確 (SSAS 疑難排解))。</span><span class="sxs-lookup"><span data-stu-id="b1604-124">For more information, see [Incorrect Amounts for Linked Measures in Cubes containing Many-to-Many Relationships](https://social.technet.microsoft.com/wiki/contents/articles/22911.incorrect-amounts-for-linked-measures-in-cubes-containing-many-to-many-relationships-ssas-troubleshooting.aspx).</span></span>  
  
 <span data-ttu-id="b1604-125">連結量值群組中所包含的量值，只能和從同一個 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫擷取的連結維度直接進行組織。</span><span class="sxs-lookup"><span data-stu-id="b1604-125">The measures contained in a linked measure group can be directly organized only along linked dimensions retrieved from the same [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="b1604-126">但是，您可以使用導出成員，將連結量值群組的資訊與您 Cube 中其他非連結維度產生關聯。</span><span class="sxs-lookup"><span data-stu-id="b1604-126">However, you can use calculated members to relate information from linked measure groups to the other, non-linked dimensions in your cube.</span></span> <span data-ttu-id="b1604-127">您也可以使用間接關聯性，例如參考或多對多關聯性，將非連結維度與連結量值群組產生關聯。</span><span class="sxs-lookup"><span data-stu-id="b1604-127">You can also use an indirect relationship, such as a reference or many-to-many relationship, to relate non-linked dimensions to a linked measure group.</span></span>  
  
## <a name="create-or-modify-a-linked-measure"></a><span data-ttu-id="b1604-128">建立或修改連結量值</span><span class="sxs-lookup"><span data-stu-id="b1604-128">Create or modify a linked measure</span></span>  
 <span data-ttu-id="b1604-129">使用 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 建立連結量值群組。</span><span class="sxs-lookup"><span data-stu-id="b1604-129">Use [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] to create a linked measure group.</span></span>  
  
1.  <span data-ttu-id="b1604-130">現在完成來源 Cube 中原始量值群組的任何修改，這樣您稍後就不必在後續的 Cube 中重建連結量值群組。</span><span class="sxs-lookup"><span data-stu-id="b1604-130">Finalize any modifications to the original measure group now, in the source cube, so that you don't have to recreate the linked measure groups later in subsequent cubes.</span></span> <span data-ttu-id="b1604-131">您可以重新命名連結物件，但是不得變更其他任何屬性。</span><span class="sxs-lookup"><span data-stu-id="b1604-131">You can rename a linked object, but you cannot change any other properties.</span></span>  
  
2.  <span data-ttu-id="b1604-132">在 [方案總管] 中，按兩下要將連結量值群組加入至哪一個 Cube。</span><span class="sxs-lookup"><span data-stu-id="b1604-132">In Solution Explorer, double-click the cube to which you are adding the linked measure group.</span></span> <span data-ttu-id="b1604-133">這個步驟會在 Cube 設計師中開啟 Cube。</span><span class="sxs-lookup"><span data-stu-id="b1604-133">This step opens the cube in Cube Designer.</span></span>  
  
3.  <span data-ttu-id="b1604-134">在 Cube 設計師的 [量值] 窗格或 [維度] 窗格中，以滑鼠右鍵按一下其中一個窗格的任何地方，然後選取 [新增連結物件]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b1604-134">In Cube Designer, in either the Measures pane or Dimensions pane, right-click anywhere in either pane, then select **New Linked Object**.</span></span> <span data-ttu-id="b1604-135">這樣會啟動連結物件精靈。</span><span class="sxs-lookup"><span data-stu-id="b1604-135">This starts the Linked Object Wizard.</span></span>  
  
4.  <span data-ttu-id="b1604-136">在第一個頁面上，指定資料來源。</span><span class="sxs-lookup"><span data-stu-id="b1604-136">On the first page, specify the data source.</span></span> <span data-ttu-id="b1604-137">這個步驟會建立原始量值群組的位置。</span><span class="sxs-lookup"><span data-stu-id="b1604-137">This step establishes the location of the original measure group.</span></span> <span data-ttu-id="b1604-138">預設值為目前資料庫中現有的 Cube，但是您也可以選擇不同的 Analysis Services 資料庫。</span><span class="sxs-lookup"><span data-stu-id="b1604-138">The default is the current cube in the current database, but you can also choose a different Analysis Services database.</span></span>  
  
5.  <span data-ttu-id="b1604-139">在下一頁選擇您想要連結的量值群組或維度。</span><span class="sxs-lookup"><span data-stu-id="b1604-139">On the next page, choose the measure group or dimension you want to link.</span></span> <span data-ttu-id="b1604-140">維度和 Cube 物件 (例如量值群組) 會個別列出。</span><span class="sxs-lookup"><span data-stu-id="b1604-140">Dimensions and Cube objects, such as measure groups, are listed separately.</span></span> <span data-ttu-id="b1604-141">只有尚未在目前 Cube 中的物件才可使用。</span><span class="sxs-lookup"><span data-stu-id="b1604-141">Only those objects not already present in the current cube are available.</span></span>  
  
6.  <span data-ttu-id="b1604-142">按一下 [完成]\*\*\*\* 即可建立連結物件。</span><span class="sxs-lookup"><span data-stu-id="b1604-142">Click **Finish** to create the linked object.</span></span> <span data-ttu-id="b1604-143">連結物件會出現在 [量值和維度] 窗格中 (以連結圖示指示)。</span><span class="sxs-lookup"><span data-stu-id="b1604-143">Linked objects appear in the Measures and Dimensions pane, indicated by the link icon.</span></span>  
  
## <a name="secure-a-linked-measure"></a><span data-ttu-id="b1604-144">維護連結量值的安全</span><span class="sxs-lookup"><span data-stu-id="b1604-144">Secure a linked measure</span></span>  
 <span data-ttu-id="b1604-145">定義連結之後，管理連結量值群組中量值的存取權方式，就和管理其他量值群組存取權的方式一樣。</span><span class="sxs-lookup"><span data-stu-id="b1604-145">After the link has been defined, access to the measures in a linked measure group, is managed in the same manner as access to other measure groups.</span></span> <span data-ttu-id="b1604-146">連結物件會連同其非連結的對應項目一起出現在角色設計工具中。</span><span class="sxs-lookup"><span data-stu-id="b1604-146">A linked object appears alongside its non-linked counterparts in Role Designer.</span></span> <span data-ttu-id="b1604-147">如需管理量值群組之安全性的詳細資訊，請參閱[授與 Cube 或模型權限 &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b1604-147">For more information on managing security for a measure group, see [Grant cube or model permissions &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md).</span></span>  
  
 <span data-ttu-id="b1604-148">若要定義或使用連結量值群組，則 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體的 Windows 服務帳戶必須屬於 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫角色 (而此角色擁有來源 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體上對來源 Cube 和量值群組的 `ReadDefinition` 和 `Read` 存取權限)，或必須屬於來源 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 管理員角色。</span><span class="sxs-lookup"><span data-stu-id="b1604-148">In order to define or use a linked measure group, the Windows service account for the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance must belong to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database role that has `ReadDefinition` and `Read` access rights on the source [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance to the source cube and measure group, or must belong to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Administrators role for the source [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1604-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1604-149">See Also</span></span>  
 [<span data-ttu-id="b1604-150">定義連結維度</span><span class="sxs-lookup"><span data-stu-id="b1604-150">Define Linked Dimensions</span></span>](define-linked-dimensions.md)  
  
  
