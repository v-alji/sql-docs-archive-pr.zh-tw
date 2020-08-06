---
title: 簽出檔案 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- Visual Studio.SourceControl.CheckOutDialog
helpviewer_keywords:
- checking out files
ms.assetid: cc033727-51bb-4b58-a12b-8977ce61ff56
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 151f554742bd6c381b27b58155d3f0e40e9eeb0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597366"
---
# <a name="check-out-files"></a><span data-ttu-id="d3f79-102">簽出檔案</span><span class="sxs-lookup"><span data-stu-id="d3f79-102">Check Out Files</span></span>
  <span data-ttu-id="d3f79-103">除非您將 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 環境設成允許編輯簽入的檔案，否則，您必須先將檔案簽出，才能修改它。</span><span class="sxs-lookup"><span data-stu-id="d3f79-103">Unless you have configured the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] environment to permit checked-in files to be edited, you must check out a file before you can modify it.</span></span> <span data-ttu-id="d3f79-104">當您簽出檔案時，會將檔案版本的副本複製到您的本機磁碟中，且必須移除檔案的唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="d3f79-104">When you check out a file, a copy of the file version is copied to your local disk, and the read-only attribute of the file is removed.</span></span>  
  
 <span data-ttu-id="d3f79-105">您可以採獨佔或共用的模式來簽出檔案。</span><span class="sxs-lookup"><span data-stu-id="d3f79-105">You can check files out either exclusively or in shared mode.</span></span> <span data-ttu-id="d3f79-106">當您以獨佔方式來簽出檔案時，在您重新簽入這個檔案之前，任何使用者都無法將它簽出。</span><span class="sxs-lookup"><span data-stu-id="d3f79-106">When you check out a file exclusively, no other user can check out the file until you check it in.</span></span> <span data-ttu-id="d3f79-107">當您以共用模式來簽出檔案時，其他使用者也可以簽出和修改這個檔案，則當您將它簽入時，可能需要合併您簽出的版本及其他使用者所建立的版本。</span><span class="sxs-lookup"><span data-stu-id="d3f79-107">When you check out a file in shared mode, other users can check out and modify the file, and when you check it in, you may need to merge the version you have checked out with the versions created by other users.</span></span>  
  
 <span data-ttu-id="d3f79-108">使用 [**簽出**] 命令來簽出原始檔控制的專案和檔案。</span><span class="sxs-lookup"><span data-stu-id="d3f79-108">Use the **Check Out** command to check out source-controlled projects and files.</span></span> <span data-ttu-id="d3f79-109">如果您使用這個命令來簽出方案或專案，則也會簽出方案或專案中的所有檔案。不過，簽出個別的原始程式碼檔案並不會導致簽出它所屬的專案或方案。</span><span class="sxs-lookup"><span data-stu-id="d3f79-109">If you use this command to check out a solution or project, all the files in the solution or project are also checked out. However, checking out an individual source code file does not result in the check out of the project or solution to which it belongs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d3f79-110">如果 [!INCLUDE[msCoName](../includes/msconame-md.md)] 您專案的 Visual SourceSafe 資料庫設定為允許多個簽出，而您想要以獨佔方式簽出檔案，您必須在簽出檔案之前，清除 [**高級簽出選項**] 對話方塊中的 [**允許多次簽**出] 選項。</span><span class="sxs-lookup"><span data-stu-id="d3f79-110">If the [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe database for your project is configured to allow multiple checkouts, and you want to check out a file exclusively, you must clear the **Allow multiple checkouts** option in the **Advanced Check Out Options** dialog box before checking out the file.</span></span> <span data-ttu-id="d3f79-111">您必須重新啟動 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]，這項設定才會生效。</span><span class="sxs-lookup"><span data-stu-id="d3f79-111">You must restart the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] for this setting to take effect.</span></span>  
  
### <a name="to-check-out-a-file"></a><span data-ttu-id="d3f79-112">簽出檔案</span><span class="sxs-lookup"><span data-stu-id="d3f79-112">To check out a file</span></span>  
  
1.  <span data-ttu-id="d3f79-113">在 [方案總管] 中，選取專案或檔案。</span><span class="sxs-lookup"><span data-stu-id="d3f79-113">In Solution Explorer, select the project or file.</span></span>  
  
2.  <span data-ttu-id="d3f79-114">**在 [檔案**] 功能表上，指向 [原始檔**控制**]，然後按一下 [**簽出] 進行編輯**。</span><span class="sxs-lookup"><span data-stu-id="d3f79-114">On the **File** menu, point to **Source Control**, and then click **Check Out for Edit**.</span></span>  
  
3.  <span data-ttu-id="d3f79-115">如果顯示 [**簽出進行編輯**] 對話方塊，請選取您想要的專案，然後按一下 [**簽出**]。如果您已將 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 環境設定為不顯示 [**簽出**] 對話方塊，則會立即簽出方案總管中選取的專案，以及他們可能擁有的任何子系。</span><span class="sxs-lookup"><span data-stu-id="d3f79-115">If the **Check Out for Edit** dialog box is displayed, select the items you want, and click **Check Out**. If you have configured the [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] environment not to display the **Check Out** dialog box, the items selected in Solution Explorer and any children they might have are checked out immediately.</span></span>  
  
     <span data-ttu-id="d3f79-116">**退房**</span><span class="sxs-lookup"><span data-stu-id="d3f79-116">**Check Out**</span></span>  
     <span data-ttu-id="d3f79-117">簽出所有已選取的項目。</span><span class="sxs-lookup"><span data-stu-id="d3f79-117">Check out all the selected items.</span></span>  
  
     <span data-ttu-id="d3f79-118">**資料行**</span><span class="sxs-lookup"><span data-stu-id="d3f79-118">**Columns**</span></span>  
     <span data-ttu-id="d3f79-119">識別要顯示的資料行以及它們顯示的順序。</span><span class="sxs-lookup"><span data-stu-id="d3f79-119">Identify the columns to display and the order in which they are displayed.</span></span>  
  
     <span data-ttu-id="d3f79-120">**註解**</span><span class="sxs-lookup"><span data-stu-id="d3f79-120">**Comments**</span></span>  
     <span data-ttu-id="d3f79-121">指定要與簽出作業產生關聯的註解。</span><span class="sxs-lookup"><span data-stu-id="d3f79-121">Specify a comment to associate with the checkout operation.</span></span>  
  
     <span data-ttu-id="d3f79-122">**簽出項目時不要顯示簽出對話方塊**</span><span class="sxs-lookup"><span data-stu-id="d3f79-122">**Don't Show Check Out dialog box when checking out items**</span></span>  
     <span data-ttu-id="d3f79-123">簽出作業期間抑制此對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d3f79-123">Suppress the dialog box during checkout operations.</span></span>  
  
     <span data-ttu-id="d3f79-124">**一般檢視**</span><span class="sxs-lookup"><span data-stu-id="d3f79-124">**Flat View**</span></span>  
     <span data-ttu-id="d3f79-125">在原始檔控制連接之下，以一般清單顯示正在簽出的項目。</span><span class="sxs-lookup"><span data-stu-id="d3f79-125">Display the items you are checking out as flat lists under their source control connection.</span></span>  
  
     <span data-ttu-id="d3f79-126">**編輯**</span><span class="sxs-lookup"><span data-stu-id="d3f79-126">**Edit**</span></span>  
     <span data-ttu-id="d3f79-127">修改專案但不簽出。只有**Edit**在您已 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 設定為支援編輯簽入檔案時，才會出現 [編輯] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d3f79-127">Modify an item without checking it out. The **Edit** button appears only if you have [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] configured to support the editing of checked-in files.</span></span>  
  
     <span data-ttu-id="d3f79-128">**名稱**</span><span class="sxs-lookup"><span data-stu-id="d3f79-128">**Name**</span></span>  
     <span data-ttu-id="d3f79-129">會顯示可簽出之項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="d3f79-129">Displays the names of the items available for checkout.</span></span> <span data-ttu-id="d3f79-130">選取的項目旁邊會顯示核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d3f79-130">Items that are selected appear with check boxes next to them.</span></span> <span data-ttu-id="d3f79-131">如果您不要簽出特定項目，請清除其核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d3f79-131">If you do not want to check out a particular item, clear its check box.</span></span>  
  
     <span data-ttu-id="d3f79-132">**選項**</span><span class="sxs-lookup"><span data-stu-id="d3f79-132">**Options**</span></span>  
     <span data-ttu-id="d3f79-133">按一下按鈕右邊的箭頭之後，就會顯示原始檔控制外掛程式特定的簽出選項。</span><span class="sxs-lookup"><span data-stu-id="d3f79-133">Displays source control plug-in-specific checkout options when the arrow to the right of the button is clicked.</span></span>  
  
     <span data-ttu-id="d3f79-134">**排序**</span><span class="sxs-lookup"><span data-stu-id="d3f79-134">**Sort**</span></span>  
     <span data-ttu-id="d3f79-135">排序顯示之資料行的順序。</span><span class="sxs-lookup"><span data-stu-id="d3f79-135">Sort the order of the displayed columns.</span></span>  
  
     <span data-ttu-id="d3f79-136">**樹狀檢視**</span><span class="sxs-lookup"><span data-stu-id="d3f79-136">**Tree View**</span></span>  
     <span data-ttu-id="d3f79-137">顯示正在簽出之項目的資料夾與檔案階層。</span><span class="sxs-lookup"><span data-stu-id="d3f79-137">Display the folder and file hierarchy for the item you are checking out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3f79-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3f79-138">See Also</span></span>  
 <span data-ttu-id="d3f79-139">[編輯簽入的檔案](../../2014/database-engine/edit-checked-in-files.md) </span><span class="sxs-lookup"><span data-stu-id="d3f79-139">[Edit Checked-In Files](../../2014/database-engine/edit-checked-in-files.md) </span></span>  
 <span data-ttu-id="d3f79-140">[在編輯時自動簽出檔案](../../2014/database-engine/automatically-check-out-files-upon-edit.md) </span><span class="sxs-lookup"><span data-stu-id="d3f79-140">[Automatically Check Out Files Upon Edit](../../2014/database-engine/automatically-check-out-files-upon-edit.md) </span></span>  
 <span data-ttu-id="d3f79-141">[復原簽出](../../2014/database-engine/undo-checkouts.md) </span><span class="sxs-lookup"><span data-stu-id="d3f79-141">[Undo Checkouts](../../2014/database-engine/undo-checkouts.md) </span></span>  
 [<span data-ttu-id="d3f79-142">管理簽出</span><span class="sxs-lookup"><span data-stu-id="d3f79-142">Manage Checkouts</span></span>](../../2014/database-engine/manage-checkouts.md)  
  
  
