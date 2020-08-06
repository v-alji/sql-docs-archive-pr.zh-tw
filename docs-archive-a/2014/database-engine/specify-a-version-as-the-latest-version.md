---
title: 將版本指定為最新版本 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- version control services [SQL Server], latest version
- latest file version specified
- file versions [SQL Server]
ms.assetid: 407dffb1-3ecf-461e-835d-124781f26ee7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: dafe4f757e33a5db63340c3d3cc7c9151871d438
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585562"
---
# <a name="specify-a-version-as-the-latest-version"></a><span data-ttu-id="b264c-102">將版本指定為最新版</span><span class="sxs-lookup"><span data-stu-id="b264c-102">Specify a Version as the Latest Version</span></span>
  <span data-ttu-id="b264c-103">當您將檔案簽入原始檔控制中，簽入的版本會成為最新的版本；簽出或擷取最新版本的使用者會收到最近簽入之項目的本機副本。</span><span class="sxs-lookup"><span data-stu-id="b264c-103">When you check a file into source control, the version you check in becomes the latest version; users who check out or retrieve the latest version receive local copies of the item most recently checked in.</span></span>  
  
 <span data-ttu-id="b264c-104">不過，在某些狀況下，您可能會想指定項目較早的版本來做為最新的版本。</span><span class="sxs-lookup"><span data-stu-id="b264c-104">However, in some situations, you may want to designate an earlier version of an item as the latest version.</span></span> <span data-ttu-id="b264c-105">例如，您簽出檔案，並修改檔案，然後再簽入檔案。</span><span class="sxs-lookup"><span data-stu-id="b264c-105">For example, you check out a file, modify the file, and then check the file in.</span></span> <span data-ttu-id="b264c-106">稍後決定捨棄您進行的修改。</span><span class="sxs-lookup"><span data-stu-id="b264c-106">You later decide to discard your modifications.</span></span> <span data-ttu-id="b264c-107">由於您已簽入這個項目，您無法恢復原來的簽出項目。</span><span class="sxs-lookup"><span data-stu-id="b264c-107">Because you have checked in the item, undoing your original checkout is not an option.</span></span> <span data-ttu-id="b264c-108">在這個狀況下，您可以將原來簽出的版本指定為項目的最新版本。</span><span class="sxs-lookup"><span data-stu-id="b264c-108">In this situation, you can designate the version you originally checked out as the latest version of the item.</span></span>  
  
 <span data-ttu-id="b264c-109">您可以利用下列方式來指定最新的版本：</span><span class="sxs-lookup"><span data-stu-id="b264c-109">You can designate the latest version by:</span></span>  
  
-   <span data-ttu-id="b264c-110">**釘選版本**。</span><span class="sxs-lookup"><span data-stu-id="b264c-110">**Pinning a version**.</span></span> <span data-ttu-id="b264c-111">當您固定某個檔案版本時，並不會刪除比固定版本還新的版本。</span><span class="sxs-lookup"><span data-stu-id="b264c-111">When you pin a file version, versions that are more recent than the pinned version are not deleted.</span></span> <span data-ttu-id="b264c-112">另外，您也可以取消固定先前所固定的檔案。</span><span class="sxs-lookup"><span data-stu-id="b264c-112">In addition, you can unpin a file that you have previously pinned.</span></span> <span data-ttu-id="b264c-113">當您執行這個動作時，最近簽入的檔案版本會成為最新的版本。</span><span class="sxs-lookup"><span data-stu-id="b264c-113">When you do this, the most recently checked in version of the file becomes the latest version.</span></span> <span data-ttu-id="b264c-114">不過，您無法簽出固定的檔案。</span><span class="sxs-lookup"><span data-stu-id="b264c-114">However, you cannot check out a pinned file.</span></span>  
  
-   <span data-ttu-id="b264c-115">回復**到指定的版本**。</span><span class="sxs-lookup"><span data-stu-id="b264c-115">**Rolling back to a specified version**.</span></span> <span data-ttu-id="b264c-116">當您回復到指定的版本時，會從原始檔控制中刪除比回復目標版本還新的所有版本。</span><span class="sxs-lookup"><span data-stu-id="b264c-116">When you roll back to a version, all versions more recent than the one to which you have rolled back are deleted from source control.</span></span> <span data-ttu-id="b264c-117">之後，您可以簽出其餘的最新版本。</span><span class="sxs-lookup"><span data-stu-id="b264c-117">You can then check out the latest remaining version.</span></span>  
  
### <a name="to-pin-a-version"></a><span data-ttu-id="b264c-118">固定版本</span><span class="sxs-lookup"><span data-stu-id="b264c-118">To pin a version</span></span>  
  
1.  <span data-ttu-id="b264c-119">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中，開啟方案。</span><span class="sxs-lookup"><span data-stu-id="b264c-119">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], open the solution.</span></span>  
  
2.  <span data-ttu-id="b264c-120">在 [方案總管] 中，選取您要指定為最新版本的檔案。</span><span class="sxs-lookup"><span data-stu-id="b264c-120">In Solution Explorer, select the file that you want to specify as the latest version.</span></span>  
  
3.  <span data-ttu-id="b264c-121">**在 [檔案**] 功能表上，指向 [原始檔**控制**]，然後按一下 [ **ViewHistory**]。</span><span class="sxs-lookup"><span data-stu-id="b264c-121">On the **File** menu, point to **Source Control** and click **ViewHistory**.</span></span>  
  
4.  <span data-ttu-id="b264c-122">在 [歷程**記錄** \<file> ] 對話方塊中，選取您要指定為最新的版本，然後按一下 [**釘**選]。</span><span class="sxs-lookup"><span data-stu-id="b264c-122">In the **History of** \<file> dialog box, select the version that you want to specify as the latest, and click **Pin**.</span></span>  
  
     <span data-ttu-id="b264c-123">此時所選版本旁會出現圖釘符號，表示它是目前的檔案版本。</span><span class="sxs-lookup"><span data-stu-id="b264c-123">A pin symbol appears next to the version you have selected, indicating that it is the current file version.</span></span> <span data-ttu-id="b264c-124">如果 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 載入了不同的版本，系統會提示您重新載入檔案。</span><span class="sxs-lookup"><span data-stu-id="b264c-124">If you have a different version loaded in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], you are prompted to reload the file.</span></span>  
  
### <a name="to-roll-back-to-a-version"></a><span data-ttu-id="b264c-125">回復到某個版本</span><span class="sxs-lookup"><span data-stu-id="b264c-125">To roll back to a version</span></span>  
  
1.  <span data-ttu-id="b264c-126">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中，開啟方案。</span><span class="sxs-lookup"><span data-stu-id="b264c-126">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], open the solution.</span></span>  
  
2.  <span data-ttu-id="b264c-127">在 [方案總管] 中，選取您要指定為最新版本的項目。</span><span class="sxs-lookup"><span data-stu-id="b264c-127">In Solution Explorer, select the item that you want to specify as the latest version.</span></span>  
  
3.  <span data-ttu-id="b264c-128">**在 [檔案**] 功能表上，指向 [原始檔**控制**]，然後按一下 [歷程**記錄**]。</span><span class="sxs-lookup"><span data-stu-id="b264c-128">On the **File** menu, point to **Source Control** and click **History**.</span></span>  
  
4.  <span data-ttu-id="b264c-129">在 [**記錄選項**] 對話方塊中，按一下 **[確定**] 以顯示 [檔案的歷程**記錄**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b264c-129">In the **History Options** dialog box, click **OK** to display the **History of File** dialog box.</span></span>  
  
5.  <span data-ttu-id="b264c-130">在 [檔案的歷程**記錄**] 方塊中，選取您要指定為最新版本的版本，然後按一下 [**復原**]。</span><span class="sxs-lookup"><span data-stu-id="b264c-130">In the **History of File** box, select the version you want to specify as the latest version, and click **Rollback**.</span></span>  
  
     <span data-ttu-id="b264c-131">此時會出現一則訊息，通知您將刪除所選版本之後的所有版本。</span><span class="sxs-lookup"><span data-stu-id="b264c-131">A message appears notifying you that all versions subsequent to the one you have selected will be deleted.</span></span>  
  
6.  <span data-ttu-id="b264c-132">按一下 **[是]** ，回復到選取的版本。</span><span class="sxs-lookup"><span data-stu-id="b264c-132">Click **Yes** to roll back to the selected version.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b264c-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b264c-133">See Also</span></span>  
 <span data-ttu-id="b264c-134">[管理簽入](../../2014/database-engine/manage-checkins.md) </span><span class="sxs-lookup"><span data-stu-id="b264c-134">[Manage Checkins](../../2014/database-engine/manage-checkins.md) </span></span>  
 [<span data-ttu-id="b264c-135">簽入檔案</span><span class="sxs-lookup"><span data-stu-id="b264c-135">Check In Files</span></span>](../../2014/database-engine/check-in-files.md)  
  
  
