---
title: 以累加方式搜尋作用中的文件
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- searches [SQL Server Management Studio], incremental
- Query Editor [SQL Server Management Studio], incremental search
- incremental searches [SQL Server Management Studio]
ms.assetid: 490bb36c-dd43-4219-9e2a-ff27046b9395
author: rothja
ms.author: jroth
ms.openlocfilehash: aefc2f0b7abff5992a8f4f7817e564ef1b72009d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592596"
---
# <a name="search-an-active-document-incrementally"></a><span data-ttu-id="dd52e-102">以累加方式搜尋作用中的文件</span><span class="sxs-lookup"><span data-stu-id="dd52e-102">Search an Active Document Incrementally</span></span>
  <span data-ttu-id="dd52e-103">您可以輸入文字，以累加方式來搜尋單一文件或視窗。</span><span class="sxs-lookup"><span data-stu-id="dd52e-103">You can search a single document or window incrementally by entering text.</span></span> <span data-ttu-id="dd52e-104">搜尋作業會反白顯示第一組符合文件或視窗中之累加搜尋期間所輸入之字元的字元。</span><span class="sxs-lookup"><span data-stu-id="dd52e-104">The search operation highlights the first set of characters that matches the characters entered during the incremental search in the document or window.</span></span> <span data-ttu-id="dd52e-105">累加搜尋會自動搜尋文件或視窗內的所有文字，不過，隱藏的文字除外。</span><span class="sxs-lookup"><span data-stu-id="dd52e-105">Incremental search automatically searches all of the text within a document or window except for text that has been hidden.</span></span>  
  
 <span data-ttu-id="dd52e-106">對於 **[大小寫須相符]** 選項，累加搜尋會使用上一次搜尋的準則。</span><span class="sxs-lookup"><span data-stu-id="dd52e-106">For the **Match case** option, incremental search uses the criteria from your previous search.</span></span> <span data-ttu-id="dd52e-107">例如，如果您利用 [檔案中尋找]  對話方塊搜尋了多個檔案，且選取 [大小寫須相符]  ，您下次累加搜尋時，搜尋會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="dd52e-107">For example, if you searched across multiple files using the **Find in Files** dialog box and select **Match Case**, and you next search incrementally, the search will be case-sensitive.</span></span>  
  
### <a name="to-search-incrementally"></a><span data-ttu-id="dd52e-108">累加搜尋</span><span class="sxs-lookup"><span data-stu-id="dd52e-108">To search incrementally</span></span>  
  
1.  <span data-ttu-id="dd52e-109">開啟您要搜尋的檔案或視窗。</span><span class="sxs-lookup"><span data-stu-id="dd52e-109">Open the file or window to you want to search.</span></span>  
  
2.  <span data-ttu-id="dd52e-110">在 **[編輯]** 功能表上，指向 **[進階]** ，再按一下 **[累加搜尋]** 。</span><span class="sxs-lookup"><span data-stu-id="dd52e-110">On the **Edit** menu, point to **Advanced**, and then click **Incremental Search**.</span></span>  
  
     <span data-ttu-id="dd52e-111">此時游標圖示會改成含箭頭 (表示搜尋方向) 的雙筒望遠鏡，狀態列會顯示「累加搜尋」。</span><span class="sxs-lookup"><span data-stu-id="dd52e-111">The cursor icon changes to a binocular with an arrow, indicating the search direction, and the status bar displays "Incremental Search."</span></span>  
  
3.  <span data-ttu-id="dd52e-112">開始輸入文字字串。</span><span class="sxs-lookup"><span data-stu-id="dd52e-112">Begin typing the text string.</span></span>  
  
     <span data-ttu-id="dd52e-113">狀態列會顯示您輸入的文字，編輯器會反白顯示符合這個文字的第一個出現項目。</span><span class="sxs-lookup"><span data-stu-id="dd52e-113">The status bar displays the text you are entering while the editor highlights the first occurrence that matches the text.</span></span> <span data-ttu-id="dd52e-114">當您繼續輸入時，編輯器會移到下一個相符項目，並反白顯示這個項目。</span><span class="sxs-lookup"><span data-stu-id="dd52e-114">As you continue typing, the editor moves to the next match and highlights it.</span></span> <span data-ttu-id="dd52e-115">如果找不到相符項目，狀態列會顯示如下：</span><span class="sxs-lookup"><span data-stu-id="dd52e-115">If no matches are available, the status bar displays the following.</span></span>  
  
    ```  
    Incremental Search: <text> (not found)  
    ```  
  
 <span data-ttu-id="dd52e-116">累加搜尋是從文件的目前位置開始執行，由上至下，由左至右。</span><span class="sxs-lookup"><span data-stu-id="dd52e-116">Incremental searches are performed from the current location in the document downwards from left to right.</span></span> <span data-ttu-id="dd52e-117">您可以利用鍵盤快速鍵來執行累加搜尋。</span><span class="sxs-lookup"><span data-stu-id="dd52e-117">Incremental searches can be done using keyboard shortcut keys.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dd52e-118">如需完整的鍵盤快速鍵清單，請參閱 [SQL Server Management Studio 鍵盤快速鍵](../../ssms/sql-server-management-studio-keyboard-shortcuts.md)。</span><span class="sxs-lookup"><span data-stu-id="dd52e-118">For a complete list of keyboard shortcut keys, see [SQL Server Management Studio Keyboard Shortcuts](../../ssms/sql-server-management-studio-keyboard-shortcuts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd52e-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd52e-119">See Also</span></span>  
 <span data-ttu-id="dd52e-120">[搜尋和取代](search-and-replace.md) </span><span class="sxs-lookup"><span data-stu-id="dd52e-120">[Search and Replace](search-and-replace.md) </span></span>  
 <span data-ttu-id="dd52e-121">[以互動方式搜尋文件](search-documents-interactively.md) </span><span class="sxs-lookup"><span data-stu-id="dd52e-121">[Search Documents Interactively](search-documents-interactively.md) </span></span>  
 <span data-ttu-id="dd52e-122">[使用結果清單搜尋文件](search-documents-using-results-lists.md) </span><span class="sxs-lookup"><span data-stu-id="dd52e-122">[Search Documents Using Results Lists](search-documents-using-results-lists.md) </span></span>  
 <span data-ttu-id="dd52e-123">[使用萬用字元搜尋文字](search-text-with-wildcards.md) </span><span class="sxs-lookup"><span data-stu-id="dd52e-123">[Search Text with Wildcards](search-text-with-wildcards.md) </span></span>  
 [<span data-ttu-id="dd52e-124">使用規則運算式搜尋文字</span><span class="sxs-lookup"><span data-stu-id="dd52e-124">Search Text with Regular Expressions</span></span>](search-text-with-regular-expressions.md)  
  
  
