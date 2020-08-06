---
title: 查看已修改的檔案清單 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- VisualStudio.SourceControl.CheckinWindow
helpviewer_keywords:
- listing modified files
- modified files list [SQL Server]
- checking in files
ms.assetid: 1b053719-8500-4300-a169-fffca5801dd0
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a2899ab9889908089d17b3c929e7bf4b2dfe2185
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598506"
---
# <a name="view-a-list-of-modified-files"></a><span data-ttu-id="fa025-102">檢視修改檔案清單</span><span class="sxs-lookup"><span data-stu-id="fa025-102">View a List of Modified Files</span></span>
  <span data-ttu-id="fa025-103">您可以使用 [**暫止簽入**] 視窗，隨時顯示目前方案中的簽出檔案清單，並在按一下按鈕的情況下簽入這些檔案。</span><span class="sxs-lookup"><span data-stu-id="fa025-103">You can use the **Pending Checkins** window to display at all times a list of the checked-out files in the current solution, and to check in these files with a single button click.</span></span>  
  
### <a name="to-view-a-list-of-modified-files"></a><span data-ttu-id="fa025-104">檢視修改檔案清單</span><span class="sxs-lookup"><span data-stu-id="fa025-104">To view a list of modified files</span></span>  
  
1.  <span data-ttu-id="fa025-105">在 [ **View** ] 功能表上，按一下 [**暫止簽入**]。</span><span class="sxs-lookup"><span data-stu-id="fa025-105">On the **View** menu, click **Pending Checkins**.</span></span>  
  
2.  <span data-ttu-id="fa025-106">若要簽入選取的檔案，請按一下 [**簽入**]。</span><span class="sxs-lookup"><span data-stu-id="fa025-106">To check in the selected files, click **Check In**.</span></span> <span data-ttu-id="fa025-107">或者，您可以將 [**暫止簽入**] 視窗停駐在環境的右側， [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 讓您可以在工作完成時簽入檔案。</span><span class="sxs-lookup"><span data-stu-id="fa025-107">Alternatively, you can dock the **Pending Checkins** window on the right side of the [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] environment so that you can check in the files when you are finished working.</span></span>  
  
     <span data-ttu-id="fa025-108">**登記**</span><span class="sxs-lookup"><span data-stu-id="fa025-108">**Check In**</span></span>  
     <span data-ttu-id="fa025-109">簽入方案。</span><span class="sxs-lookup"><span data-stu-id="fa025-109">Checks in the solution.</span></span>  
  
     <span data-ttu-id="fa025-110">**註解**</span><span class="sxs-lookup"><span data-stu-id="fa025-110">**Comments**</span></span>  
     <span data-ttu-id="fa025-111">使純文字註解與暫止簽入建立關聯。</span><span class="sxs-lookup"><span data-stu-id="fa025-111">Associates a plain text comment with the pending check in.</span></span> <span data-ttu-id="fa025-112">針對每一個專案版本，都會建立註解以及註解與專案版本的關聯性，並儲存於原始檔控制資料庫中。</span><span class="sxs-lookup"><span data-stu-id="fa025-112">A comment is created and associated with each version of a project, and stored in the source control database.</span></span>  
  
     <span data-ttu-id="fa025-113">**選項**</span><span class="sxs-lookup"><span data-stu-id="fa025-113">**Options**</span></span>  
     <span data-ttu-id="fa025-114">指定當您按一下 [**簽入**] 按鈕時，原始檔控制應採取的動作。</span><span class="sxs-lookup"><span data-stu-id="fa025-114">Specifies the actions that source control should take when you click the **Check In** button.</span></span>  
  
    -   <span data-ttu-id="fa025-115">**保留所有簽出**</span><span class="sxs-lookup"><span data-stu-id="fa025-115">**Keep All Checked Out**</span></span>  
  
         <span data-ttu-id="fa025-116">指定您的變更應該寫入原始檔控制提供者，但檔案應保持簽出。</span><span class="sxs-lookup"><span data-stu-id="fa025-116">Specifies that your changes should be written to the source control provider but that the files should remain checked out.</span></span>  
  
     <span data-ttu-id="fa025-117">**排序**</span><span class="sxs-lookup"><span data-stu-id="fa025-117">**Sort**</span></span>  
     <span data-ttu-id="fa025-118">指定項目清單中所顯示資料行的排序順序。</span><span class="sxs-lookup"><span data-stu-id="fa025-118">Specifies the sort order for the columns displayed in the Items list.</span></span>  
  
     <span data-ttu-id="fa025-119">**資料行**</span><span class="sxs-lookup"><span data-stu-id="fa025-119">**Columns**</span></span>  
     <span data-ttu-id="fa025-120">顯示您可以加入視窗項目清單中的資料行清單。</span><span class="sxs-lookup"><span data-stu-id="fa025-120">Displays a list of the columns you can add to the window's Items list.</span></span>  
  
     <span data-ttu-id="fa025-121">**樹狀檢視**</span><span class="sxs-lookup"><span data-stu-id="fa025-121">**Tree View**</span></span>  
     <span data-ttu-id="fa025-122">顯示您正在簽入之方案或專案的資料夾和檔案階層。</span><span class="sxs-lookup"><span data-stu-id="fa025-122">Displays the folder and file hierarchy for the solution or project you are checking in.</span></span>  
  
     <span data-ttu-id="fa025-123">**一般檢視**</span><span class="sxs-lookup"><span data-stu-id="fa025-123">**Flat View**</span></span>  
     <span data-ttu-id="fa025-124">在檔案的原始檔控制連接下，將您正在簽入的檔案顯示為一般清單。</span><span class="sxs-lookup"><span data-stu-id="fa025-124">Displays the files you are checking in as flat lists under their source control connection.</span></span>  
  
     <span data-ttu-id="fa025-125">**比較版本**</span><span class="sxs-lookup"><span data-stu-id="fa025-125">**Compare Versions**</span></span>  
     <span data-ttu-id="fa025-126">開啟 [Visual SourceSafe**差異選項**] 對話方塊，將您的開發環境專案中選取的檔案與任何其他選取的檔案相比較，並顯示其差異（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="fa025-126">Opens the Visual SourceSafe **Difference Options** dialog box, which compares a selected file in your development environment project to any other selected file and shows you the differences, if any.</span></span>  
  
     <span data-ttu-id="fa025-127">**復原簽出**</span><span class="sxs-lookup"><span data-stu-id="fa025-127">**Undo checkout**</span></span>  
     <span data-ttu-id="fa025-128">反轉 [**暫止簽入**] 視窗中選取之所有專案的簽出。</span><span class="sxs-lookup"><span data-stu-id="fa025-128">Reverses the checkout of all items selected in the **Pending Checkins** window.</span></span>  
  
     <span data-ttu-id="fa025-129">**名稱**</span><span class="sxs-lookup"><span data-stu-id="fa025-129">**Name**</span></span>  
     <span data-ttu-id="fa025-130">顯示可用於簽入的項目清單。</span><span class="sxs-lookup"><span data-stu-id="fa025-130">Displays a list of the items available for check in.</span></span> <span data-ttu-id="fa025-131">項目出現時，旁邊的核取方塊會顯示為已選取。</span><span class="sxs-lookup"><span data-stu-id="fa025-131">Items appear with the check box next to them selected.</span></span> <span data-ttu-id="fa025-132">如果您不想要簽入特定的項目，請清除它旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="fa025-132">If you do not want to check in a particular item, clear the check box next to it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa025-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa025-133">See Also</span></span>  
 <span data-ttu-id="fa025-134">[管理簽入](../../2014/database-engine/manage-checkins.md) </span><span class="sxs-lookup"><span data-stu-id="fa025-134">[Manage Checkins](../../2014/database-engine/manage-checkins.md) </span></span>  
 [<span data-ttu-id="fa025-135">管理簽出</span><span class="sxs-lookup"><span data-stu-id="fa025-135">Manage Checkouts</span></span>](../../2014/database-engine/manage-checkouts.md)  
  
  
