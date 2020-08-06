---
title: 管理簽出 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- source controls [SQL Server Management Studio], checkouts
- checkouts [SQL Server Management Studio]
- checking out files
ms.assetid: ddd4adba-d432-4005-9cb2-bb9ee3163d8e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cdfa25cdc27e707d4be705e66b215130c9d70ce1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607020"
---
# <a name="manage-checkouts"></a><span data-ttu-id="fb03b-102">管理簽出</span><span class="sxs-lookup"><span data-stu-id="fb03b-102">Manage Checkouts</span></span>
  <span data-ttu-id="fb03b-103">檔案加入原始檔控制之後，您必須先簽出檔案，才能修改它。</span><span class="sxs-lookup"><span data-stu-id="fb03b-103">After a file has been added to source control, you must check out the file before you can modify it.</span></span> <span data-ttu-id="fb03b-104">當您將檔案從原始檔控制中簽出時，原始檔控制提供者會在您的本機磁碟中建立最新版本的本機副本，且會移除檔案的唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="fb03b-104">When you check a file out of source control, the source control provider creates a copy of the latest version on your local disk and removes the read-only attribute of the file.</span></span> <span data-ttu-id="fb03b-105">在某些情況下，您可能需要在未簽出檔案的情況下編輯檔案。</span><span class="sxs-lookup"><span data-stu-id="fb03b-105">In some circumstances you might need to edit a file without checking out the file.</span></span> <span data-ttu-id="fb03b-106">如需有關編輯檔案而不簽出檔案的詳細資訊，請參閱[編輯已簽入](../../2014/database-engine/edit-checked-in-files.md)的檔案。</span><span class="sxs-lookup"><span data-stu-id="fb03b-106">For more information about editing a file without checking the file out, see [Edit Checked-In Files](../../2014/database-engine/edit-checked-in-files.md).</span></span>  
  
 <span data-ttu-id="fb03b-107">您可以使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 手動或自動簽出檔案。</span><span class="sxs-lookup"><span data-stu-id="fb03b-107">You can use [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to check out files manually or automatically.</span></span> <span data-ttu-id="fb03b-108">您可以藉由開啟包含環境中檔案的方案 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] ，然後按一下 [**簽出**] 命令，以手動方式簽出檔案。</span><span class="sxs-lookup"><span data-stu-id="fb03b-108">You check out files manually by opening the solution that contains the files in the [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] environment, and then clicking the **Check Out** command.</span></span> <span data-ttu-id="fb03b-109">如果您設定 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 環境來自動簽出檔案，您也可以自動簽出檔案。</span><span class="sxs-lookup"><span data-stu-id="fb03b-109">You can check out files automatically if you configure the [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] environment to do so.</span></span>  
  
 <span data-ttu-id="fb03b-110">隨著管理員所設定的原始檔控制提供者的選項而不同，您也可以利用獨佔或共用模式來簽出檔案。</span><span class="sxs-lookup"><span data-stu-id="fb03b-110">Depending on the options that your administrator sets on your source control provider, you can also check out files in exclusive or shared mode.</span></span> <span data-ttu-id="fb03b-111">當您以獨佔模式簽出檔案時，只有您可以修改它，且在您重新簽入此檔案之前，任何其他使用者都無法將其簽出。</span><span class="sxs-lookup"><span data-stu-id="fb03b-111">When you check out a file exclusively, only you can modify it, and no other user can check out the file until you check it in.</span></span> <span data-ttu-id="fb03b-112">當您以共用模式簽出檔案時，其他使用者仍可簽出相同的檔案且使用者人數不限。</span><span class="sxs-lookup"><span data-stu-id="fb03b-112">When you check out a file in shared mode, any number of users can check out the same file.</span></span> <span data-ttu-id="fb03b-113">由於每位使用者都簽入檔案，因此，原始檔控制提供者會嘗試將檔案和檔案的最新伺服器版本合併起來。</span><span class="sxs-lookup"><span data-stu-id="fb03b-113">As each user checks in the file, the source control provider attempts to merge the file with the latest server version of the file.</span></span> <span data-ttu-id="fb03b-114">如果簽入的版本與最新的版本發生衝突，原始檔控制提供者會提示使用者解決衝突。</span><span class="sxs-lookup"><span data-stu-id="fb03b-114">If conflicts arise between the version that is being checked in and the latest version, the source control provider prompts the user to resolve the conflicts.</span></span>  
  
 <span data-ttu-id="fb03b-115">下表描述此章節的主題。</span><span class="sxs-lookup"><span data-stu-id="fb03b-115">The following table describes the topics in this section.</span></span>  
  
|<span data-ttu-id="fb03b-116">主題</span><span class="sxs-lookup"><span data-stu-id="fb03b-116">Topic</span></span>|<span data-ttu-id="fb03b-117">描述</span><span class="sxs-lookup"><span data-stu-id="fb03b-117">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="fb03b-118">簽出檔案</span><span class="sxs-lookup"><span data-stu-id="fb03b-118">Check Out Files</span></span>](../../2014/database-engine/check-out-files.md)|<span data-ttu-id="fb03b-119">提供如何簽出檔案以便修改的指示。</span><span class="sxs-lookup"><span data-stu-id="fb03b-119">Provides instructions on how to check out a file so you can modify it.</span></span>|  
|[<span data-ttu-id="fb03b-120">復原簽出</span><span class="sxs-lookup"><span data-stu-id="fb03b-120">Undo Checkouts</span></span>](../../2014/database-engine/undo-checkouts.md)|<span data-ttu-id="fb03b-121">說明如何取消現有的簽出。</span><span class="sxs-lookup"><span data-stu-id="fb03b-121">Explains how to cancel an existing checkout.</span></span>|  
|[<span data-ttu-id="fb03b-122">在編輯時自動簽出檔案</span><span class="sxs-lookup"><span data-stu-id="fb03b-122">Automatically Check Out Files Upon Edit</span></span>](../../2014/database-engine/automatically-check-out-files-upon-edit.md)|<span data-ttu-id="fb03b-123">說明如何將原始檔控制設定成在開始編輯檔案時簽出檔案。</span><span class="sxs-lookup"><span data-stu-id="fb03b-123">Explains how to configure source control to check out a file when you start to edit it.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fb03b-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb03b-124">See Also</span></span>  
 <span data-ttu-id="fb03b-125">[管理簽入](../../2014/database-engine/manage-checkins.md) </span><span class="sxs-lookup"><span data-stu-id="fb03b-125">[Manage Checkins](../../2014/database-engine/manage-checkins.md) </span></span>  
 [<span data-ttu-id="fb03b-126">編輯簽入的檔案</span><span class="sxs-lookup"><span data-stu-id="fb03b-126">Edit Checked-In Files</span></span>](../../2014/database-engine/edit-checked-in-files.md)  
  
  
