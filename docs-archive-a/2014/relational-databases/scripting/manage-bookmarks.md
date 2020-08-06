---
title: 管理書籤
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- bookmarks [SQL Server Management Studio]
ms.assetid: 67cc3fd6-3238-4c58-a3ec-2d3b0438143a
author: rothja
ms.author: jroth
ms.openlocfilehash: 0d2613c9232d34c036f746c0937c80e9ca4ef892
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606725"
---
# <a name="manage-bookmarks"></a><span data-ttu-id="2c3aa-102">管理書籤</span><span class="sxs-lookup"><span data-stu-id="2c3aa-102">Manage Bookmarks</span></span>
  <span data-ttu-id="2c3aa-103">使用程式碼編輯器時，[書籤]  視窗可讓您建立連結至文件內之程式碼的特定行。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-103">While you are working in a code editor, the **Bookmarks** window allows you to create links to specific lines of code within your document.</span></span> <span data-ttu-id="2c3aa-104">您可以從 [檢視]  功能表顯示這個視窗。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-104">You can display this window from the **View** menu.</span></span>  
  
 <span data-ttu-id="2c3aa-105">若要建立和巡覽整個書籤，請按一下位於 [文字編輯器]  工具列上和 [書籤]  視窗上方的按鈕。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-105">To create and navigate through bookmarks, click the buttons located on the **TextEditor** toolbar and at the top of the **Bookmarks** window.</span></span> <span data-ttu-id="2c3aa-106">您可加入和刪除書籤、啟動或停用書籤以及將書籤組織到資料夾中。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-106">You can add and remove bookmarks, activate or disable bookmarks, and organize bookmarks into folders.</span></span> <span data-ttu-id="2c3aa-107">[書籤]  視窗的捷徑功能表中，也有一些可用的特定命令。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-107">Certain commands are also available from the **Bookmarks** window shortcut menu.</span></span> <span data-ttu-id="2c3aa-108">若要加入或移除書籤，請將插入點放在適用的編輯器行上，然後按一下 [切換書籤]  。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-108">To add or remove a bookmark, place the insertion point on the desired line in the Editor, and then click **Toggle a bookmark**.</span></span> <span data-ttu-id="2c3aa-109">若要啟用書籤，請在 [書籤]  視窗中選取其核取方塊；若要停用 (而非移除) 書籤，則請清除其核取方塊。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-109">To activate a bookmark, select its check box in the **Bookmarks** window; to disable (but not remove) a bookmark, clear its check box.</span></span>  
  
## <a name="text-editor-toolbar"></a><span data-ttu-id="2c3aa-110">文字編輯器工具列</span><span class="sxs-lookup"><span data-stu-id="2c3aa-110">Text Editor Toolbar</span></span>  
 <span data-ttu-id="2c3aa-111">在編輯器中開啟文字文件時，會啟用 [文字編輯器]  工具列的下列按鈕。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-111">The following buttons are enabled on the **Text Editor** toolbar when a text document is opened in the Editor.</span></span> <span data-ttu-id="2c3aa-112">在使用查詢編輯器時，若要顯示 [文字編輯器]  工具列，請在 [檢視]  功能表上指向 [工具列]  ，然後按一下 [文字編輯器]  。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-112">To display the **Text Editor** toolbar when you are in the Query Editor, on the **View** menu, point to **Toolbars**, and then click **Text Editor**.</span></span>  
  
 <span data-ttu-id="2c3aa-113">**在目前的行上切換書籤**</span><span class="sxs-lookup"><span data-stu-id="2c3aa-113">**Toggle a bookmark on the current line**</span></span>  
 <span data-ttu-id="2c3aa-114">在使用中的編輯器內，於文件的選取行上加入或移除書籤。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-114">Adds or removes a bookmark on the selected line of the document in the active Editor.</span></span> <span data-ttu-id="2c3aa-115">這不會改變有書籤的程式碼行。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-115">Does not alter the line of code bookmarked.</span></span>  
  
 <span data-ttu-id="2c3aa-116">**將插入號移動到前一個書籤**</span><span class="sxs-lookup"><span data-stu-id="2c3aa-116">**Move the caret to previous bookmark**</span></span>  
 <span data-ttu-id="2c3aa-117">請選取在 [書籤]  視窗中已啟用的上一個書籤。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-117">Selects the previous bookmark that is enabled in the **Bookmarks** window.</span></span> <span data-ttu-id="2c3aa-118">當已到達第一個書籤時，將向前跳至最後一個。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-118">When the first bookmark is reached, jumps ahead to the last one.</span></span> <span data-ttu-id="2c3aa-119">視需要而定，將於選取的書籤在編輯器中出現之處開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-119">As needed, opens the file where the selected bookmark occurs in the Editor.</span></span> <span data-ttu-id="2c3aa-120">捲動該文件至有書籤的行，然後將插入點加入該處。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-120">Scrolls that document to the bookmarked line, and places the insertion point there.</span></span>  
  
 <span data-ttu-id="2c3aa-121">**移動插入號到下一個書籤**</span><span class="sxs-lookup"><span data-stu-id="2c3aa-121">**Move the caret to the next bookmark**</span></span>  
 <span data-ttu-id="2c3aa-122">請選取在 [書籤]  視窗中已啟用的下一個書籤。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-122">Selects the next bookmark that is enabled in the **Bookmarks** window.</span></span> <span data-ttu-id="2c3aa-123">當已到達最後一個書籤時，將向後跳回至第一個。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-123">When the last bookmark is reached, jumps back to the first one.</span></span> <span data-ttu-id="2c3aa-124">視需要而定，將於選取的書籤在編輯器中出現之處開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-124">As needed, opens the file where the selected bookmark occurs in the Editor.</span></span> <span data-ttu-id="2c3aa-125">捲動該文件至有書籤的行，然後將插入點加入該處。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-125">Scrolls that document to the bookmarked line, and places the insertion point there.</span></span>  
  
 <span data-ttu-id="2c3aa-126">**清除目前文件中所有的書籤**</span><span class="sxs-lookup"><span data-stu-id="2c3aa-126">**Clear all bookmarks in the current document**</span></span>  
 <span data-ttu-id="2c3aa-127">顯示確認訊息，然後移除使用中文件的所有書籤。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-127">Displays a confirmation message, and then removes all bookmarks from the active document.</span></span> <span data-ttu-id="2c3aa-128">這不會移除有書籤的程式碼行。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-128">Does not remove the lines of code that were bookmarked.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="2c3aa-129">您無法恢復此程序。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-129">You cannot undo this procedure.</span></span> <span data-ttu-id="2c3aa-130">之後，您必須使用 [在目前這一行切換書籤]  建立新書籤。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-130">Afterward, you must use **Toggle a bookmark on the current line** to create new bookmarks.</span></span> <span data-ttu-id="2c3aa-131">若要停用書籤但不將它們移除，請在 [書籤]  視窗中清除其核取方塊。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-131">To disable bookmarks but not remove them, clear their check boxes in the **Bookmarks** window.</span></span>  
  
## <a name="bookmarks-window"></a><span data-ttu-id="2c3aa-132">書籤視窗</span><span class="sxs-lookup"><span data-stu-id="2c3aa-132">Bookmarks Window</span></span>  
 <span data-ttu-id="2c3aa-133">若要組織書籤，請在 [書籤]  視窗中建立書籤資料夾。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-133">To organize bookmarks, create bookmark folders in the **Bookmarks** window.</span></span> <span data-ttu-id="2c3aa-134">拖放書籤到資料夾中。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-134">Drag and drop bookmarks into the folders.</span></span> <span data-ttu-id="2c3aa-135">下列按鈕可以在 [書籤]  視窗的上方找到。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-135">The following buttons are available at the top of the **Bookmarks** window.</span></span>  
  
 <span data-ttu-id="2c3aa-136">**在目前的行上切換書籤。**</span><span class="sxs-lookup"><span data-stu-id="2c3aa-136">**Toggle a bookmark on the current line.**</span></span>  
 <span data-ttu-id="2c3aa-137">在使用中的編輯器內，於文件的選取行上加入或移除書籤。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-137">Adds or removes a bookmark on the selected line of the document in the active Editor.</span></span> <span data-ttu-id="2c3aa-138">這不會改變有書籤的程式碼行。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-138">Does not alter the line of code bookmarked.</span></span>  
  
 <span data-ttu-id="2c3aa-139">**新增資料夾**</span><span class="sxs-lookup"><span data-stu-id="2c3aa-139">**New folder**</span></span>  
 <span data-ttu-id="2c3aa-140">加入資料夾到 [書籤]  視窗。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-140">Adds a folder to the **Bookmarks** window.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="2c3aa-141">在冗長的程式碼檔案中，將書籤組織至與工作相關的資料夾中是有幫助的。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-141">In a lengthy code file, it can be helpful to organize bookmarks into task-related folders.</span></span> <span data-ttu-id="2c3aa-142">選取資料夾，啟用 [移至資料夾中上一個書籤]  和 [移至資料夾下一個書籤]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-142">Selecting a folder enables the **Go to previous bookmark in folder** and **Go to next bookmark in folder** buttons.</span></span>  
  
 <span data-ttu-id="2c3aa-143">**將插入號移動到前一個書籤**</span><span class="sxs-lookup"><span data-stu-id="2c3aa-143">**Move the caret to previous bookmark**</span></span>  
 <span data-ttu-id="2c3aa-144">請選取在 [書籤]  視窗中已啟用的上一個書籤。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-144">Selects the previous bookmark that is enabled in the **Bookmarks** window.</span></span> <span data-ttu-id="2c3aa-145">當已到達第一個書籤時，將向前跳至最後一個。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-145">When the first bookmark is reached, jumps ahead to the last one.</span></span> <span data-ttu-id="2c3aa-146">視需要而定，將於選取的書籤在編輯器中出現之處開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-146">As needed, opens the file where the selected bookmark occurs in the Editor.</span></span> <span data-ttu-id="2c3aa-147">捲動該文件至有書籤的行，然後將插入點加入該處。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-147">Scrolls that document to the bookmarked line, and places the insertion point there.</span></span>  
  
 <span data-ttu-id="2c3aa-148">**移動插入號到下一個書籤**</span><span class="sxs-lookup"><span data-stu-id="2c3aa-148">**Move the caret to the next bookmark**</span></span>  
 <span data-ttu-id="2c3aa-149">請選取在 [書籤]  視窗中已啟用的下一個書籤。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-149">Selects the next bookmark that is enabled in the **Bookmarks** window.</span></span> <span data-ttu-id="2c3aa-150">當已到達最後一個書籤時，將向後跳回至第一個。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-150">When the last bookmark is reached, jumps back to the first one.</span></span> <span data-ttu-id="2c3aa-151">視需要而定，將於選取的書籤在編輯器中出現之處開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-151">As needed, opens the file where the selected bookmark occurs in the Editor.</span></span> <span data-ttu-id="2c3aa-152">捲動該文件至有書籤的行，然後將插入點加入該處。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-152">Scrolls that document to the bookmarked line, and places the insertion point there.</span></span>  
  
 <span data-ttu-id="2c3aa-153">**將插入號移動到目前資料夾中的前一個書籤**</span><span class="sxs-lookup"><span data-stu-id="2c3aa-153">**Move the caret to previous bookmark in the current folder**</span></span>  
 <span data-ttu-id="2c3aa-154">選取在 [書籤]  視窗中，於同一資料夾內啟用的上一個書籤。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-154">Selects the previous bookmark that is enabled within the same folder in the **Bookmarks** window.</span></span> <span data-ttu-id="2c3aa-155">當已到達第一個書籤時，將向前跳至資料夾中的最後一個。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-155">When the first bookmark is reached, jumps ahead to the last one in that folder.</span></span> <span data-ttu-id="2c3aa-156">視需要而定，將於選取的書籤在編輯器中出現之處開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-156">As needed, opens the file where the selected bookmark occurs in the Editor.</span></span> <span data-ttu-id="2c3aa-157">捲動該文件至有書籤的行，然後將插入點加入該處。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-157">Scrolls that document to the bookmarked line, and places the insertion point there.</span></span>  
  
 <span data-ttu-id="2c3aa-158">**將插入號移動到目前資料夾中的下一個書籤**</span><span class="sxs-lookup"><span data-stu-id="2c3aa-158">**Move the caret to next bookmark in the current folder**</span></span>  
 <span data-ttu-id="2c3aa-159">選取在 [書籤]  視窗中，於同一資料夾內啟用的下一個書籤。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-159">Selects the next bookmark that is enabled within the same folder in the **Bookmarks** window.</span></span> <span data-ttu-id="2c3aa-160">當已到達第一個書籤時，將向後跳至資料夾中的第一個。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-160">When the first bookmark is reached, jumps back to the first one in that folder.</span></span> <span data-ttu-id="2c3aa-161">視需要而定，將於選取的書籤在編輯器中出現之處開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-161">As needed, opens the file where the selected bookmark occurs in the Editor.</span></span> <span data-ttu-id="2c3aa-162">捲動該文件至有書籤的行，然後將插入點加入該處。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-162">Scrolls that document to the bookmarked line, and places the insertion point there.</span></span>  
  
 <span data-ttu-id="2c3aa-163">**停用/啟用所有書籤**</span><span class="sxs-lookup"><span data-stu-id="2c3aa-163">**Disable/Enable All Bookmarks**</span></span>  
 <span data-ttu-id="2c3aa-164">在 [書籤]  視窗中，清除或啟用所有書籤的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-164">Clears or enables the check boxes for all bookmarks in the **Bookmarks** window.</span></span> <span data-ttu-id="2c3aa-165">這不會移除書籤，或改變它們標示的程式碼行。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-165">Does not remove bookmarks, or alter the lines of code that they mark.</span></span>  
  
 <span data-ttu-id="2c3aa-166">**刪除**</span><span class="sxs-lookup"><span data-stu-id="2c3aa-166">**Delete**</span></span>  
 <span data-ttu-id="2c3aa-167">從 [書籤]  視窗以及書籤所出現的文件中，移除目前選取的書籤。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-167">Removes the currently selected bookmark from the **Bookmarks** window and from the document where the bookmark occurred.</span></span> <span data-ttu-id="2c3aa-168">這不會移除有書籤的程式碼行。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-168">Does not remove the line of code that was bookmarked.</span></span>  
  
 <span data-ttu-id="2c3aa-169">書籤核取方塊</span><span class="sxs-lookup"><span data-stu-id="2c3aa-169">Bookmark check boxes</span></span>  
 <span data-ttu-id="2c3aa-170">每個書籤都有自己的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-170">Each bookmark has its own check box.</span></span> <span data-ttu-id="2c3aa-171">若要啟用現有的書籤，請在 [書籤]  視窗中選取其核取方塊。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-171">To activate an existing bookmark, select its check box in the **Bookmarks** window.</span></span> <span data-ttu-id="2c3aa-172">若要隱藏 (但不移除) 現有的書籤，請在 [書籤]  視窗中清除其核取方塊。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-172">To hide (but not remove) an existing bookmark, clear its check box in the **Bookmarks** window.</span></span>  
  
## <a name="bookmarks-window-shortcut-menu"></a><span data-ttu-id="2c3aa-173">書籤視窗快速鍵功能表</span><span class="sxs-lookup"><span data-stu-id="2c3aa-173">Bookmarks Window Shortcut Menu</span></span>  
 <span data-ttu-id="2c3aa-174">以滑鼠右鍵按一下 [書籤]  視窗中的項目時，可從捷徑功能表使用下列命令。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-174">When you right-click on an entry in the **Bookmarks** window, the following commands are available from the shortcut menu.</span></span>  
  
 <span data-ttu-id="2c3aa-175">**刪除**</span><span class="sxs-lookup"><span data-stu-id="2c3aa-175">**Delete**</span></span>  
 <span data-ttu-id="2c3aa-176">從 [書籤]  視窗以及書籤所出現的文件中，移除目前選取的書籤。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-176">Removes the currently selected bookmark from the **Bookmarks** window and from the document where the bookmark occurred.</span></span> <span data-ttu-id="2c3aa-177">這不會移除有書籤的程式碼行。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-177">Does not remove the line of code that was bookmarked.</span></span>  
  
 <span data-ttu-id="2c3aa-178">**重新命名**</span><span class="sxs-lookup"><span data-stu-id="2c3aa-178">**Rename**</span></span>  
 <span data-ttu-id="2c3aa-179">允許您指派新的顯示名稱給書籤或資料夾。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-179">Allows you to assign a new display name to a bookmark or folder.</span></span>  
  
 <span data-ttu-id="2c3aa-180">**停用/啟用書籤**</span><span class="sxs-lookup"><span data-stu-id="2c3aa-180">**Disable/Enable Bookmark**</span></span>  
 <span data-ttu-id="2c3aa-181">在 [書籤]  視窗中，清除或啟用所選取書籤的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-181">Clears or enables the check box for the selected bookmark in the **Bookmarks** window.</span></span> <span data-ttu-id="2c3aa-182">這不會移除書籤，或改變其標示的程式碼行。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-182">Does not remove the bookmark, or alter the line of code that it marks.</span></span>  
  
 <span data-ttu-id="2c3aa-183">**停用/啟用所有書籤**</span><span class="sxs-lookup"><span data-stu-id="2c3aa-183">**Disable/Enable All Bookmarks**</span></span>  
 <span data-ttu-id="2c3aa-184">在 [書籤]  視窗中，清除或啟用所有書籤的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-184">Clears or enables the check boxes for all bookmarks in the **Bookmarks** window.</span></span> <span data-ttu-id="2c3aa-185">這不會移除書籤，或改變它們標示的程式碼行。</span><span class="sxs-lookup"><span data-stu-id="2c3aa-185">Does not remove bookmarks, or alter the lines of code that they mark.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c3aa-186">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c3aa-186">See Also</span></span>  
 [<span data-ttu-id="2c3aa-187">SQL Server Management Studio 鍵盤快速鍵</span><span class="sxs-lookup"><span data-stu-id="2c3aa-187">SQL Server Management Studio Keyboard Shortcuts</span></span>](../../ssms/sql-server-management-studio-keyboard-shortcuts.md)  
