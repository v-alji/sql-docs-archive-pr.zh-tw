---
title: 復原簽出 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- VisualStudio.SourcControl.UndoCheckDialog
helpviewer_keywords:
- checking out files
- checkout source controls [SQL Server]
- undoing checkouts
ms.assetid: a6596b20-3aa5-4dc4-a4c5-3649f1f5a20e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ff6e6041b59caa75bf7f8530d915db48e0379338
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585545"
---
# <a name="undo-checkouts"></a><span data-ttu-id="7b71f-102">復原簽出</span><span class="sxs-lookup"><span data-stu-id="7b71f-102">Undo Checkouts</span></span>
  <span data-ttu-id="7b71f-103">您可以使用 [**復原簽出**] 命令來取消現有的簽出。</span><span class="sxs-lookup"><span data-stu-id="7b71f-103">You can use the **Undo Checkout** command to cancel an existing checkout.</span></span> <span data-ttu-id="7b71f-104">當您修改且儲存了某個檔案之後，又需要回復這些變更時，這尤其有用。</span><span class="sxs-lookup"><span data-stu-id="7b71f-104">This is particularly useful when you have modified and saved a file, and then later need to roll back your changes.</span></span>  
  
 <span data-ttu-id="7b71f-105">根據您在 [**復原簽出**] [選項] 對話方塊中設定的選項，Studio 環境會將專案的工作複本保留在本機磁片上，或以最新的原始檔控制版本來取代。</span><span class="sxs-lookup"><span data-stu-id="7b71f-105">Depending on the options you set in the **Undo Checkout Advanced Options** dialog box, the Studio environment either leaves the working copy of the item on your local disk or replaces it with the latest source-controlled version.</span></span> <span data-ttu-id="7b71f-106">如果有人在原始檔控制系統的環境之外修改了這個項目，擷取的版本便可能不是最新的版本。</span><span class="sxs-lookup"><span data-stu-id="7b71f-106">If someone has modified the item outside the context of the source control system, the retrieved version may not be the latest one.</span></span>  
  
### <a name="to-undo-a-checkout"></a><span data-ttu-id="7b71f-107">恢復簽出</span><span class="sxs-lookup"><span data-stu-id="7b71f-107">To undo a checkout</span></span>  
  
1.  <span data-ttu-id="7b71f-108">在 [方案總管] 中選取專案。</span><span class="sxs-lookup"><span data-stu-id="7b71f-108">In Solution Explorer, select the project.</span></span>  
  
2.  <span data-ttu-id="7b71f-109">**在 [檔案**] 功能表上，指向 [原始檔**控制**]，然後按一下 [**復原簽出**]。</span><span class="sxs-lookup"><span data-stu-id="7b71f-109">On the **File** menu, point to **Source Control**, and then click **Undo Checkout**.</span></span>  
  
3.  <span data-ttu-id="7b71f-110">在 [**復原簽出**] 對話方塊中，選取適當的選項，然後按一下 [**復原簽出**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7b71f-110">In the **Undo Checkout** dialog box, select the appropriate options, and then click the **Undo Checkout** button.</span></span>  
  
     <span data-ttu-id="7b71f-111">**資料行**</span><span class="sxs-lookup"><span data-stu-id="7b71f-111">**Columns**</span></span>  
     <span data-ttu-id="7b71f-112">識別要顯示的資料行以及它們顯示的順序。</span><span class="sxs-lookup"><span data-stu-id="7b71f-112">Identify the columns to display and the order in which they are displayed.</span></span>  
  
     <span data-ttu-id="7b71f-113">**一般檢視**</span><span class="sxs-lookup"><span data-stu-id="7b71f-113">**Flat View**</span></span>  
     <span data-ttu-id="7b71f-114">在原始檔控制連接下，以一般清單的方式顯示項目。</span><span class="sxs-lookup"><span data-stu-id="7b71f-114">Display the items as flat lists under their source control connection.</span></span>  
  
     <span data-ttu-id="7b71f-115">**名稱**</span><span class="sxs-lookup"><span data-stu-id="7b71f-115">**Name**</span></span>  
     <span data-ttu-id="7b71f-116">顯示要恢復簽出的項目名稱。</span><span class="sxs-lookup"><span data-stu-id="7b71f-116">Displays the names of the items for which to undo the checkout.</span></span> <span data-ttu-id="7b71f-117">項目出現時，旁邊的核取方塊會顯示為已選取。</span><span class="sxs-lookup"><span data-stu-id="7b71f-117">Items appear with the check boxes next to them selected.</span></span> <span data-ttu-id="7b71f-118">如果您不想恢復項目的簽出，請清除該核取方塊。</span><span class="sxs-lookup"><span data-stu-id="7b71f-118">If you do not want to undo the checkout of an item, clear its check box.</span></span>  
  
     <span data-ttu-id="7b71f-119">**選項**</span><span class="sxs-lookup"><span data-stu-id="7b71f-119">**Options**</span></span>  
     <span data-ttu-id="7b71f-120">按一下按鈕右邊的箭頭之後，就會顯示原始檔控制外掛程式特定的恢復簽出選項。</span><span class="sxs-lookup"><span data-stu-id="7b71f-120">Displays source control plug-in-specific undo checkout options when the arrow to the right of the button is clicked.</span></span>  
  
     <span data-ttu-id="7b71f-121">**排序**</span><span class="sxs-lookup"><span data-stu-id="7b71f-121">**Sort**</span></span>  
     <span data-ttu-id="7b71f-122">排序顯示資料行的順序。</span><span class="sxs-lookup"><span data-stu-id="7b71f-122">Sort the order of the display columns.</span></span>  
  
     <span data-ttu-id="7b71f-123">**樹狀檢視**</span><span class="sxs-lookup"><span data-stu-id="7b71f-123">**Tree View**</span></span>  
     <span data-ttu-id="7b71f-124">顯示您要反轉簽出之項目的資料夾和項目階層。</span><span class="sxs-lookup"><span data-stu-id="7b71f-124">Display the folder and item hierarchy for items on which you are reversing the checkout.</span></span>  
  
     <span data-ttu-id="7b71f-125">**恢復簽出**</span><span class="sxs-lookup"><span data-stu-id="7b71f-125">**Undo Checkout**</span></span>  
     <span data-ttu-id="7b71f-126">反轉簽出，捨棄對簽出檔案所做的任何變更。</span><span class="sxs-lookup"><span data-stu-id="7b71f-126">Revert the checkout, discarding any changes to the checked-out file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b71f-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b71f-127">See Also</span></span>  
 <span data-ttu-id="7b71f-128">[簽出檔案](../../2014/database-engine/check-out-files.md) </span><span class="sxs-lookup"><span data-stu-id="7b71f-128">[Check Out Files](../../2014/database-engine/check-out-files.md) </span></span>  
 [<span data-ttu-id="7b71f-129">管理簽出</span><span class="sxs-lookup"><span data-stu-id="7b71f-129">Manage Checkouts</span></span>](../../2014/database-engine/manage-checkouts.md)  
  
  
