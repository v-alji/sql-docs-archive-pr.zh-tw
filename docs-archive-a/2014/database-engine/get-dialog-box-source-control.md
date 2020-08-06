---
title: 取得對話方塊 (原始檔控制) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- VisualStudio.SourceControl.GetVersionDialog
helpviewer_keywords:
- Get dialog box
ms.assetid: 048564d3-6c58-405b-8b57-b690fbfdbe9e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 6d949a649a35ee3c5a6521223d45975b7c372aff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607036"
---
# <a name="get-dialog-box-source-control"></a><span data-ttu-id="e4bdb-102">取得對話方塊 (原始檔控制)</span><span class="sxs-lookup"><span data-stu-id="e4bdb-102">Get Dialog Box (Source Control)</span></span>
  <span data-ttu-id="e4bdb-103">從原始檔控制資料庫擷取選取項目的唯讀副本，傳送到您的工作資料夾，或者其他指定資料夾。</span><span class="sxs-lookup"><span data-stu-id="e4bdb-103">Retrieves a read-only copy of the selected item from the source control database to your working folder, or another folder that you specify.</span></span>  
  
## <a name="dialog-box-access"></a><span data-ttu-id="e4bdb-104">對話方塊存取</span><span class="sxs-lookup"><span data-stu-id="e4bdb-104">Dialog Box Access</span></span>  
 <span data-ttu-id="e4bdb-105">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中，選取方案總管中的項目。</span><span class="sxs-lookup"><span data-stu-id="e4bdb-105">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], select an item in Solution Explorer.</span></span> <span data-ttu-id="e4bdb-106">**在 [檔案**] 功能表上，按一下 [原始檔控制] **，** 然後按一下 [**取得**]。</span><span class="sxs-lookup"><span data-stu-id="e4bdb-106">On the **File** menu, click **Source Control,** then click **Get**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e4bdb-107">在方案總管中以滑鼠右鍵按一下項目，亦可使用此對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e4bdb-107">This dialog box is also available by right-clicking the item in Solution Explorer.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e4bdb-108">選項</span><span class="sxs-lookup"><span data-stu-id="e4bdb-108">Options</span></span>  
 <span data-ttu-id="e4bdb-109">**動作**</span><span class="sxs-lookup"><span data-stu-id="e4bdb-109">**Action**</span></span>  
 <span data-ttu-id="e4bdb-110">指定欲擷取項目上要執行的動作。</span><span class="sxs-lookup"><span data-stu-id="e4bdb-110">Specifies the action being performed on the items to retrieve.</span></span>  
  
 <span data-ttu-id="e4bdb-111">**資料行**</span><span class="sxs-lookup"><span data-stu-id="e4bdb-111">**Columns**</span></span>  
 <span data-ttu-id="e4bdb-112">識別要顯示的資料行，以及資料行的顯示順序。</span><span class="sxs-lookup"><span data-stu-id="e4bdb-112">Identifies columns to display and the order in which they are displayed.</span></span>  
  
 <span data-ttu-id="e4bdb-113">**一般檢視**</span><span class="sxs-lookup"><span data-stu-id="e4bdb-113">**Flat View**</span></span>  
 <span data-ttu-id="e4bdb-114">在原始檔控制連接下，以一般清單的方式顯示您正在擷取的檔案。</span><span class="sxs-lookup"><span data-stu-id="e4bdb-114">Display the files you are retrieving as flat lists under their source control connection.</span></span>  
  
 <span data-ttu-id="e4bdb-115">**修改時間**</span><span class="sxs-lookup"><span data-stu-id="e4bdb-115">**Modified Time**</span></span>  
 <span data-ttu-id="e4bdb-116">顯示項目上次修改的時間。</span><span class="sxs-lookup"><span data-stu-id="e4bdb-116">Displays the time when an item was last modified.</span></span>  
  
 <span data-ttu-id="e4bdb-117">**名稱**</span><span class="sxs-lookup"><span data-stu-id="e4bdb-117">**Name**</span></span>  
 <span data-ttu-id="e4bdb-118">顯示要擷取的項目名稱。</span><span class="sxs-lookup"><span data-stu-id="e4bdb-118">Display the names of the items to retrieve.</span></span> <span data-ttu-id="e4bdb-119">項目出現時，旁邊的核取方塊會顯示為已選取。</span><span class="sxs-lookup"><span data-stu-id="e4bdb-119">Items appear with the check boxes next to them selected.</span></span> <span data-ttu-id="e4bdb-120">如果您不想擷取特定項目，請清除其核取方塊。</span><span class="sxs-lookup"><span data-stu-id="e4bdb-120">If you do not want to retrieve a particular item, clear its check box.</span></span>  
  
 <span data-ttu-id="e4bdb-121">**選項**</span><span class="sxs-lookup"><span data-stu-id="e4bdb-121">**Options**</span></span>  
 <span data-ttu-id="e4bdb-122">點選按鈕右側的箭頭之後，就會顯示來源安全外掛程式特定的取得選項。</span><span class="sxs-lookup"><span data-stu-id="e4bdb-122">Displays source safe plug-in-specific get options when the arrow to the right of the button is clicked.</span></span>  
  
 <span data-ttu-id="e4bdb-123">**排序**</span><span class="sxs-lookup"><span data-stu-id="e4bdb-123">**Sort**</span></span>  
 <span data-ttu-id="e4bdb-124">排序顯示之資料行的順序。</span><span class="sxs-lookup"><span data-stu-id="e4bdb-124">Sort the order of the displayed columns.</span></span>  
  
 <span data-ttu-id="e4bdb-125">**樹狀檢視**</span><span class="sxs-lookup"><span data-stu-id="e4bdb-125">**Tree View**</span></span>  
 <span data-ttu-id="e4bdb-126">顯示正在擷取項目的資料夾與檔案階層。</span><span class="sxs-lookup"><span data-stu-id="e4bdb-126">Display the folder and file hierarchy for the items you are retrieving.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4bdb-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4bdb-127">See Also</span></span>  
 <span data-ttu-id="e4bdb-128">[取出檔案](../../2014/database-engine/retrieve-files.md) </span><span class="sxs-lookup"><span data-stu-id="e4bdb-128">[Retrieve Files](../../2014/database-engine/retrieve-files.md) </span></span>  
 [<span data-ttu-id="e4bdb-129">方案總管原始檔控制</span><span class="sxs-lookup"><span data-stu-id="e4bdb-129">Solution Explorer Source Control</span></span>](../../2014/database-engine/solution-explorer-source-control.md)  
  
  
