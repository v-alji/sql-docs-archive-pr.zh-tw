---
title: 簽入檔案 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- VisualStudio.SourceControl.CheckInDialog
helpviewer_keywords:
- checking in files
ms.assetid: 0657a387-8411-4406-bef9-d262a5bfa269
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 070c1dfa5dd057cf777980f7022752a97a4dc84c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597367"
---
# <a name="check-in-files"></a><span data-ttu-id="5ea47-102">簽入檔案</span><span class="sxs-lookup"><span data-stu-id="5ea47-102">Check In Files</span></span>
  <span data-ttu-id="5ea47-103">若要將您修改過的原始檔控制檔案提供給其他使用者，您必須將這些檔案簽入原始檔控制中。</span><span class="sxs-lookup"><span data-stu-id="5ea47-103">To make source-controlled files that you have modified available to other users, you must check the files into source control.</span></span> <span data-ttu-id="5ea47-104">當您簽入檔案時，您簽入的版本會寫入原始檔控制提供者中，且會成為檔案的最新版本。</span><span class="sxs-lookup"><span data-stu-id="5ea47-104">When you check in a file, the version you check in is written to the source control provider and becomes the latest version of the file.</span></span>  
  
 <span data-ttu-id="5ea47-105">您可以使用 [**簽入**] 命令來簽入檔案。</span><span class="sxs-lookup"><span data-stu-id="5ea47-105">You can use the **Check In** command to check in files.</span></span> <span data-ttu-id="5ea47-106">如果您利用這個命令來簽入方案或專案，也會簽入方案或專案中的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="5ea47-106">If you use this command to check in a solution or project, all the files in the solution or project are also checked in.</span></span> <span data-ttu-id="5ea47-107">不過，簽入個別來源程式碼檔案，並不會簽入它所屬的專案或方案。</span><span class="sxs-lookup"><span data-stu-id="5ea47-107">However, checking in an individual source code file does not result in the check-in of the project or solution to which it belongs.</span></span>  
  
### <a name="to-check-in-a-file"></a><span data-ttu-id="5ea47-108">簽入檔案</span><span class="sxs-lookup"><span data-stu-id="5ea47-108">To check in a file</span></span>  
  
1.  <span data-ttu-id="5ea47-109">在方案總管中，以滑鼠右鍵按一下要簽入的檔案，然後按一下 [**簽入**]。</span><span class="sxs-lookup"><span data-stu-id="5ea47-109">In Solution Explorer, right-click the file to check in, and then click **Check In**.</span></span>  
  
2.  <span data-ttu-id="5ea47-110">如果 [**簽入**] 對話方塊出現，請選取適當的選項，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="5ea47-110">If the **Check In** dialog box appears, select the appropriate options, and then click **OK**.</span></span>  
  
     <span data-ttu-id="5ea47-111">**登記**</span><span class="sxs-lookup"><span data-stu-id="5ea47-111">**Check In**</span></span>  
     <span data-ttu-id="5ea47-112">簽入所有選取的項目。</span><span class="sxs-lookup"><span data-stu-id="5ea47-112">Check in all the selected items.</span></span>  
  
     <span data-ttu-id="5ea47-113">**資料行**</span><span class="sxs-lookup"><span data-stu-id="5ea47-113">**Columns**</span></span>  
     <span data-ttu-id="5ea47-114">識別要顯示的資料行以及它們顯示的順序。</span><span class="sxs-lookup"><span data-stu-id="5ea47-114">Identify the columns to display and the order in which they are displayed.</span></span>  
  
     <span data-ttu-id="5ea47-115">**註解**</span><span class="sxs-lookup"><span data-stu-id="5ea47-115">**Comments**</span></span>  
     <span data-ttu-id="5ea47-116">加入與簽入作業相關聯的註解。</span><span class="sxs-lookup"><span data-stu-id="5ea47-116">Add a comment to associate with the check-in operation.</span></span>  
  
     <span data-ttu-id="5ea47-117">**簽入項目時不要顯示簽入對話方塊**</span><span class="sxs-lookup"><span data-stu-id="5ea47-117">**Don't show Check in dialog box when checking in items**</span></span>  
     <span data-ttu-id="5ea47-118">簽入作業期間抑制此對話方塊。</span><span class="sxs-lookup"><span data-stu-id="5ea47-118">Suppress the dialog box during check-in operations.</span></span>  
  
     <span data-ttu-id="5ea47-119">**一般檢視**</span><span class="sxs-lookup"><span data-stu-id="5ea47-119">**Flat View**</span></span>  
     <span data-ttu-id="5ea47-120">在檔案的原始檔控制連接下，將您正在簽入的檔案顯示為一般清單。</span><span class="sxs-lookup"><span data-stu-id="5ea47-120">Display the files you are checking in as flat lists under their source control connection.</span></span>  
  
     <span data-ttu-id="5ea47-121">**名稱**</span><span class="sxs-lookup"><span data-stu-id="5ea47-121">**Name**</span></span>  
     <span data-ttu-id="5ea47-122">顯示要簽入之項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="5ea47-122">Displays the names of the items to check in.</span></span> <span data-ttu-id="5ea47-123">項目出現時，旁邊的核取方塊會顯示為已選取。</span><span class="sxs-lookup"><span data-stu-id="5ea47-123">Items appear with the check boxes next to them selected.</span></span> <span data-ttu-id="5ea47-124">如果您不想要簽入特定的項目，請清除它的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="5ea47-124">If you do not want to check in a particular item, clear its check box.</span></span>  
  
     <span data-ttu-id="5ea47-125">**選項**</span><span class="sxs-lookup"><span data-stu-id="5ea47-125">**Options**</span></span>  
     <span data-ttu-id="5ea47-126">按一下按鈕右邊的箭頭之後，就會顯示原始檔控制外掛程式特定的簽入選項。</span><span class="sxs-lookup"><span data-stu-id="5ea47-126">Displays source control plug-in-specific check-in options when the arrow to the right of the button is clicked.</span></span>  
  
     <span data-ttu-id="5ea47-127">**排序**</span><span class="sxs-lookup"><span data-stu-id="5ea47-127">**Sort**</span></span>  
     <span data-ttu-id="5ea47-128">排序顯示資料行的順序。</span><span class="sxs-lookup"><span data-stu-id="5ea47-128">Sort the order of the display columns.</span></span>  
  
     <span data-ttu-id="5ea47-129">**樹狀檢視**</span><span class="sxs-lookup"><span data-stu-id="5ea47-129">**Tree View**</span></span>  
     <span data-ttu-id="5ea47-130">顯示您正在簽入之項目的資料夾和檔案階層。</span><span class="sxs-lookup"><span data-stu-id="5ea47-130">Display the folder and file hierarchy for the items you are checking in.</span></span>  
  
 <span data-ttu-id="5ea47-131">如果您簽入的檔案不在共用的簽出中，[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 環境會立即簽入這個檔案。</span><span class="sxs-lookup"><span data-stu-id="5ea47-131">If the file you have checked in is not part of a shared checkout, the [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] environment checks in the file immediately.</span></span> <span data-ttu-id="5ea47-132">否則，它可能會提示您合併您的版本和其他使用者所建立的版本。</span><span class="sxs-lookup"><span data-stu-id="5ea47-132">Otherwise, it may prompt you to merge your version with versions created by other users.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ea47-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ea47-133">See Also</span></span>  
 <span data-ttu-id="5ea47-134">[查看修改過的檔案清單](../../2014/database-engine/view-a-list-of-modified-files.md) </span><span class="sxs-lookup"><span data-stu-id="5ea47-134">[View a List of Modified Files](../../2014/database-engine/view-a-list-of-modified-files.md) </span></span>  
 [<span data-ttu-id="5ea47-135">管理簽入</span><span class="sxs-lookup"><span data-stu-id="5ea47-135">Manage Checkins</span></span>](../../2014/database-engine/manage-checkins.md)  
  
  
