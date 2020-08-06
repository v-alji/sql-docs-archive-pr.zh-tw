---
title: 評估原則對話方塊，原則選取頁面 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.runnow.f1
ms.assetid: 20075fbe-0b48-42c8-b747-690f1aa23dcf
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f68a1ccc7873b6a05d2641ddaa87e8d5b0e5c6d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687761"
---
# <a name="evaluate-policies-dialog-box-policy-selection-page"></a><span data-ttu-id="843b5-102">評估原則對話方塊，原則選取頁面</span><span class="sxs-lookup"><span data-stu-id="843b5-102">Evaluate Policies Dialog Box, Policy Selection Page</span></span>
  <span data-ttu-id="843b5-103">使用此對話方塊可評估以原則為基礎的管理原則。</span><span class="sxs-lookup"><span data-stu-id="843b5-103">Use this dialog box to evaluate Policy-Based Management policies.</span></span> <span data-ttu-id="843b5-104">您可以藉由選取 **[評估結果]** 頁面，將原則套用到目標集內不符合原則的項目。</span><span class="sxs-lookup"><span data-stu-id="843b5-104">By selecting the **Evaluation Results** page, you can apply policies to the items in a target set that do not comply with the policies.</span></span>  
  
## <a name="options"></a><span data-ttu-id="843b5-105">選項</span><span class="sxs-lookup"><span data-stu-id="843b5-105">Options</span></span>  
 <span data-ttu-id="843b5-106">**Source**</span><span class="sxs-lookup"><span data-stu-id="843b5-106">**Source**</span></span>  
 <span data-ttu-id="843b5-107">指定原則的來源。</span><span class="sxs-lookup"><span data-stu-id="843b5-107">Specifies the source of the policies.</span></span> <span data-ttu-id="843b5-108">若要變更來源，請按一下 [瀏覽]\( **...** ) 按鈕，開啟 **[選取來源]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="843b5-108">To change the source, click the Browse (**...**) button to open the **Select Source** dialog box.</span></span>  
  
 <span data-ttu-id="843b5-109">**檔案**</span><span class="sxs-lookup"><span data-stu-id="843b5-109">**Files**</span></span>  
 <span data-ttu-id="843b5-110">輸入包含以原則為基礎之管理原則的檔案路徑，或是使用 [瀏覽]\( **...** ) 按鈕來選取檔案。</span><span class="sxs-lookup"><span data-stu-id="843b5-110">Type the path of a file that contains a Policy-Based Management policy, or use the Browse (**...**) button to select the file.</span></span>  
  
 <span data-ttu-id="843b5-111">**Server**</span><span class="sxs-lookup"><span data-stu-id="843b5-111">**Server**</span></span>  
 <span data-ttu-id="843b5-112">選取此選項可連接包含您想要之原則的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="843b5-112">Select to connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that contains the policy that you want.</span></span>  
  
 <span data-ttu-id="843b5-113">**原則: 原則**</span><span class="sxs-lookup"><span data-stu-id="843b5-113">**Policies: Policy**</span></span>  
 <span data-ttu-id="843b5-114">按一下此選項可開啟指定之原則的原則對話方塊。</span><span class="sxs-lookup"><span data-stu-id="843b5-114">Click to open the policy dialog box for the specified policy.</span></span>  
  
 <span data-ttu-id="843b5-115">**原則: 類別目錄**</span><span class="sxs-lookup"><span data-stu-id="843b5-115">**Policies: Category**</span></span>  
 <span data-ttu-id="843b5-116">此原則的類別目錄。</span><span class="sxs-lookup"><span data-stu-id="843b5-116">The category of the policy.</span></span> <span data-ttu-id="843b5-117">這個方塊是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="843b5-117">This box is read-only.</span></span>  
  
 <span data-ttu-id="843b5-118">**原則: Facet**</span><span class="sxs-lookup"><span data-stu-id="843b5-118">**Policies: Facet**</span></span>  
 <span data-ttu-id="843b5-119">此原則所實作的 Facet。</span><span class="sxs-lookup"><span data-stu-id="843b5-119">The facet implemented by the policy.</span></span> <span data-ttu-id="843b5-120">這個方塊是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="843b5-120">This box is read-only.</span></span>  
  
 <span data-ttu-id="843b5-121">**首先**</span><span class="sxs-lookup"><span data-stu-id="843b5-121">**Evaluate**</span></span>  
 <span data-ttu-id="843b5-122">在評估模式下執行此原則。</span><span class="sxs-lookup"><span data-stu-id="843b5-122">Runs the policy in evaluation mode.</span></span> <span data-ttu-id="843b5-123">這樣會產生目標集的符合報表，但是不會重新設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或是強制未來的符合。</span><span class="sxs-lookup"><span data-stu-id="843b5-123">This generates a compliance report for the target set but does not reconfigure [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or enforce future compliance.</span></span>  
  
## <a name="possible-errors"></a><span data-ttu-id="843b5-124">可能的錯誤</span><span class="sxs-lookup"><span data-stu-id="843b5-124">Possible Errors</span></span>  
  
-   <span data-ttu-id="843b5-125">**找不到任何目標**</span><span class="sxs-lookup"><span data-stu-id="843b5-125">**No targets found**</span></span>  
  
     <span data-ttu-id="843b5-126">目標集可能會基於下列任何一個理由而空白：</span><span class="sxs-lookup"><span data-stu-id="843b5-126">The target set could be empty due to any of the following reasons:</span></span>  
  
    -   <span data-ttu-id="843b5-127">此原則指定之型別的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上沒有任何目標。</span><span class="sxs-lookup"><span data-stu-id="843b5-127">There are no targets on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] of the type specified by the policy.</span></span>  
  
    -   <span data-ttu-id="843b5-128">伺服器限制可能會排除包含目標的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="843b5-128">The server restriction might exclude the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that contains the target.</span></span>  
  
    -   <span data-ttu-id="843b5-129">如果此原則位於資料庫的物件上 (如資料表、檢視表或使用者)，資料庫可能沒有訂閱此原則的類別目錄。</span><span class="sxs-lookup"><span data-stu-id="843b5-129">If the policy is on an object in a database (for example a table, view, or user) the database might not subscribe to the category of the policy.</span></span>  
  
    -   <span data-ttu-id="843b5-130">目標集篩選可能會排除這個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體上的所有目標。</span><span class="sxs-lookup"><span data-stu-id="843b5-130">The target-set filter might exclude all targets on this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
    -   <span data-ttu-id="843b5-131">目標伺服器類型與原則評估所在的伺服器類型不同。</span><span class="sxs-lookup"><span data-stu-id="843b5-131">The target server type is different from the server type on which the policy is evaluated.</span></span> <span data-ttu-id="843b5-132">例如在 [!INCLUDE[ssDE](../../includes/ssde-md.md)]中，如果您嘗試評估已經針對 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]建立的原則，您將會收到空的目標集。</span><span class="sxs-lookup"><span data-stu-id="843b5-132">For example, in the [!INCLUDE[ssDE](../../includes/ssde-md.md)], if you try to evaluate a policy that has been created for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you will receive an empty target set</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="843b5-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="843b5-133">See Also</span></span>  
 <span data-ttu-id="843b5-134">[使用以原則為基礎的管理來管理伺服器](administer-servers-by-using-policy-based-management.md) </span><span class="sxs-lookup"><span data-stu-id="843b5-134">[Administer Servers by Using Policy-Based Management](administer-servers-by-using-policy-based-management.md) </span></span>  
 [<span data-ttu-id="843b5-135">評估原則對話方塊，評估結果頁面</span><span class="sxs-lookup"><span data-stu-id="843b5-135">Evaluate Policies Dialog Box, Evaluation Results Page</span></span>](evaluate-policies-dialog-box-evaluation-results-page.md)  
  
  
