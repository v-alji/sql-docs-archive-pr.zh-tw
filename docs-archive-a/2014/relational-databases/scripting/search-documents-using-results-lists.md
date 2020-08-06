---
title: 使用結果清單搜尋文件
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- searches [SQL Server Management Studio], result lists
- result list searches [SQL Server Management Studio]
- searches [SQL Server Management Studio], multiple files
- Query Editor [SQL Server Management Studio], search multiple files
ms.assetid: 275e1b6c-fbd0-4408-af77-35903f90657c
author: rothja
ms.author: jroth
ms.openlocfilehash: 58ff3754bc1667de75426e52b3ddd855e7d1a348
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606207"
---
# <a name="search-documents-using-results-lists"></a><span data-ttu-id="6fc48-102">使用結果清單搜尋文件</span><span class="sxs-lookup"><span data-stu-id="6fc48-102">Search Documents Using Results Lists</span></span>
  <span data-ttu-id="6fc48-103">您可以利用 **[尋找和取代]** 對話方塊來搜尋和取代專案或方案或檔案系統資料夾中之所有檔案內的文字，即使尚未在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中開啟它們，也是如此。</span><span class="sxs-lookup"><span data-stu-id="6fc48-103">Using the **Find and Replace** dialog box, you can search and replace text in all files in a project or solution or in a file system folder, even when they are not open in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="6fc48-104">**[尋找和取代]** 對話方塊所執行之搜尋的相符項目會出現在 [尋找結果 1] 和 [尋找結果 2] 視窗中，可讓您檢視相符項目所在字行中的確實文字。</span><span class="sxs-lookup"><span data-stu-id="6fc48-104">Matches from searches that were performed with the **Find and Replace** dialog box appear in the Find Results 1 and Find Results 2 windows, which allows you to view the exact text from the line containing the match.</span></span>  
  
### <a name="to-search-in-multiple-files"></a><span data-ttu-id="6fc48-105">在多個檔案中搜尋</span><span class="sxs-lookup"><span data-stu-id="6fc48-105">To search in multiple files</span></span>  
  
1.  <span data-ttu-id="6fc48-106">在 **[編輯]** 功能表上，指向 **[尋找和取代]** ，再按一下 **[檔案中尋找]** 。</span><span class="sxs-lookup"><span data-stu-id="6fc48-106">On the **Edit** menu, point to **Find and Replace,** and then click **Find in Files**.</span></span>  
  
2.  <span data-ttu-id="6fc48-107">在 **[尋找目標]** 文字方塊中，輸入要搜尋的文字。</span><span class="sxs-lookup"><span data-stu-id="6fc48-107">In the **Find what** text box, enter the text to search for.</span></span>  
  
3.  <span data-ttu-id="6fc48-108">在 **[查詢]** 清單中，按一下 **[所有開啟的文件]** 、 **[目前的專案]** 或 **[整個方案]** ，或輸入目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="6fc48-108">In the **Look in** list, click **All Open Documents**, **Current Project**, **Entire Solution**, or type a directory path.</span></span>  
  
4.  <span data-ttu-id="6fc48-109">在 **[檔案類型]** 清單中，選取列出的各組副檔名之一，或用分號分隔來輸入要搜尋之檔案類型的副檔名。</span><span class="sxs-lookup"><span data-stu-id="6fc48-109">In the **File types** list, select one of the listed sets of file extensions or enter the extensions for the types of files to be searched, separated by semicolons.</span></span> <span data-ttu-id="6fc48-110">請利用 \*.\* 來搜尋 [查詢]  下拉式清單列出之目錄中的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="6fc48-110">Use \*.\* to search all files in the directory listed in the **Look in** drop-down list.</span></span>  
  
5.  <span data-ttu-id="6fc48-111">選取其餘搜尋選項來改進搜尋的精確度。</span><span class="sxs-lookup"><span data-stu-id="6fc48-111">Select from the remaining search options to improve the accuracy of the search.</span></span>  
  
6.  <span data-ttu-id="6fc48-112">按一下 **[尋找]** 來開始搜尋。</span><span class="sxs-lookup"><span data-stu-id="6fc48-112">Click **Find** to begin the search.</span></span>  
  
 <span data-ttu-id="6fc48-113">依預設，搜尋的相符項目會出現在 [尋找結果 1] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="6fc48-113">The matches for the search appear in the Find Results 1 window by default.</span></span> <span data-ttu-id="6fc48-114">您可以在 [尋找結果 1] 視窗中，按兩下各個項目來瀏覽搜尋相符項目。</span><span class="sxs-lookup"><span data-stu-id="6fc48-114">You can browse the search matches by double-clicking each entry in the Find Results 1 window.</span></span> <span data-ttu-id="6fc48-115">若要在新視窗中檢視搜尋結果，請選取 **[顯示在 [尋找結果 2] 視窗]** 。</span><span class="sxs-lookup"><span data-stu-id="6fc48-115">To view the search results in a new window, select **Display in Find 2**.</span></span>  
  
#### <a name="to-replace-across-multiple-files-or-folders"></a><span data-ttu-id="6fc48-116">跨多個檔案或資料夾取代</span><span class="sxs-lookup"><span data-stu-id="6fc48-116">To replace across multiple files or folders</span></span>  
  
1.  <span data-ttu-id="6fc48-117">在 **[編輯]** 功能表上，指向 **[尋找和取代]** ，再按一下 **[檔案中取代]** 。</span><span class="sxs-lookup"><span data-stu-id="6fc48-117">On the **Edit** menu, point to **Find and Replace,** and then click **Replace in Files**.</span></span>  
  
2.  <span data-ttu-id="6fc48-118">在 **[尋找目標]** 文字方塊中，輸入要搜尋的文字。</span><span class="sxs-lookup"><span data-stu-id="6fc48-118">In the **Find what** text box, enter the text to search for.</span></span>  
  
3.  <span data-ttu-id="6fc48-119">在 **[取代成]** 方塊中，輸入用來取代搜尋文字的文字。</span><span class="sxs-lookup"><span data-stu-id="6fc48-119">In the **Replace with** box, enter the text to replace the search text.</span></span>  
  
4.  <span data-ttu-id="6fc48-120">在 **[查詢]** 清單中，按一下 **[所有開啟的文件]** 、 **[目前的專案]** 或 **[整個方案]** ，或輸入目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="6fc48-120">In the **Look in** list, click **All Open Documents**, **Current Project**, **Entire Solution**, or type a directory path.</span></span>  
  
5.  <span data-ttu-id="6fc48-121">按一下 **[取代]** 來利用 **[取代成]** 方塊中的文字取代目前的搜尋相符項目。</span><span class="sxs-lookup"><span data-stu-id="6fc48-121">Click **Replace** to replace the current search match with the text in the **Replace with** box.</span></span> <span data-ttu-id="6fc48-122">您可以按一下 **[尋找下一個]** 來略過單一相符項目，或按一下 **[略過檔案]** 來略過整個檔案。</span><span class="sxs-lookup"><span data-stu-id="6fc48-122">You can skip a single match by clicking **Find Next** or skip an entire file clicking **Skip File**.</span></span>  
  
     <span data-ttu-id="6fc48-123">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="6fc48-123">\- or -</span></span>  
  
     <span data-ttu-id="6fc48-124">選擇 **[取代全部]** 來利用 **[取代成]** 方塊中的文字取代所有搜尋相符項目。</span><span class="sxs-lookup"><span data-stu-id="6fc48-124">Choose **Replace all** to replace all search matches with the text in the **Replace with** box.</span></span> <span data-ttu-id="6fc48-125">如果您要在其他時候恢復某些取代作業的結果，請選取 **[全部取代後保持已修改檔案為開啟狀態]** 。</span><span class="sxs-lookup"><span data-stu-id="6fc48-125">Select **Keep modified files open after Replace All** if you want to undo some of the replacements at another time.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6fc48-126">**[取代全部]** 會取代所有搜尋相符項目，其中包括您已在檔案中，利用 **[略過檔案]** 或 **[尋找下一個]** 來略過的項目。</span><span class="sxs-lookup"><span data-stu-id="6fc48-126">**Replace all** replaces all search matches, including those in files you have skipped with **Skip File** or **Find Next**.</span></span> <span data-ttu-id="6fc48-127">您只能利用 **[恢復]** 來處理在取代作業之後保持開啟狀態之檔案中的取代項目。</span><span class="sxs-lookup"><span data-stu-id="6fc48-127">You can only use **Undo** for replacements made in files that remain open after the replacement operation.</span></span>  
  
 <span data-ttu-id="6fc48-128">依預設，取代資訊會出現在 [尋找結果 1] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="6fc48-128">Replacement information appears in the Find Results 1 window by default.</span></span> <span data-ttu-id="6fc48-129">您可以在 [尋找結果 1] 視窗中，按兩下各個項目來瀏覽取代項目。</span><span class="sxs-lookup"><span data-stu-id="6fc48-129">You can browse replacements by double-clicking each entry in the Find Results 1 window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fc48-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6fc48-130">See Also</span></span>  
 <span data-ttu-id="6fc48-131">[搜尋和取代](search-and-replace.md) </span><span class="sxs-lookup"><span data-stu-id="6fc48-131">[Search and Replace](search-and-replace.md) </span></span>  
 <span data-ttu-id="6fc48-132">[以互動方式搜尋文件](search-documents-interactively.md) </span><span class="sxs-lookup"><span data-stu-id="6fc48-132">[Search Documents Interactively](search-documents-interactively.md) </span></span>  
 <span data-ttu-id="6fc48-133">[使用萬用字元搜尋文字](search-text-with-wildcards.md) </span><span class="sxs-lookup"><span data-stu-id="6fc48-133">[Search Text with Wildcards](search-text-with-wildcards.md) </span></span>  
 [<span data-ttu-id="6fc48-134">使用規則運算式搜尋文字</span><span class="sxs-lookup"><span data-stu-id="6fc48-134">Search Text with Regular Expressions</span></span>](search-text-with-regular-expressions.md)  
  
  
