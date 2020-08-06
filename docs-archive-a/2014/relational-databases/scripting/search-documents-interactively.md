---
title: 以互動方式搜尋文件
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- interactive searches [SQL Server Management Studio]
- searches [SQL Server Management Studio], interactive
- Query Editor [SQL Server Management Studio], interactive search
ms.assetid: dae65ac5-67af-45c6-a6e0-952fea26d680
author: rothja
ms.author: jroth
ms.openlocfilehash: 5603db77ea4f58d4bb036635a23ec3cfa400a818
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606212"
---
# <a name="search-documents-interactively"></a><span data-ttu-id="9a7d1-102">以互動方式搜尋文件</span><span class="sxs-lookup"><span data-stu-id="9a7d1-102">Search Documents Interactively</span></span>
  <span data-ttu-id="9a7d1-103">您可以利用 [尋找和取代]  對話方塊，搜尋一或多個開啟的檔案或視窗，並逐一搜尋相符的項目。</span><span class="sxs-lookup"><span data-stu-id="9a7d1-103">Using the **Find and Replace** dialog box, you can search one or more open files or windows and move through the search matches one by one.</span></span> <span data-ttu-id="9a7d1-104">這項技術可讓您在環繞相符項目的文字內容中，檢閱每項個別的搜尋相符項目。</span><span class="sxs-lookup"><span data-stu-id="9a7d1-104">This technique allows you to review each individual search match in the context of the text around the match.</span></span> <span data-ttu-id="9a7d1-105">您也可以選擇執行大量尋找作業，或利用 [尋找和取代]  對話方塊，以報表格式檢閱搜尋相符項目。</span><span class="sxs-lookup"><span data-stu-id="9a7d1-105">You also have the option of performing bulk find operations and reviewing search matches in report format using the **Find and Replace** dialog box.</span></span>  
  
### <a name="to-search-all-open-documents"></a><span data-ttu-id="9a7d1-106">搜尋所有開啟的文件</span><span class="sxs-lookup"><span data-stu-id="9a7d1-106">To search all open documents</span></span>  
  
1.  <span data-ttu-id="9a7d1-107">開啟您要搜尋的項目。</span><span class="sxs-lookup"><span data-stu-id="9a7d1-107">Open the items you wish to search.</span></span>  
  
2.  <span data-ttu-id="9a7d1-108">在 [編輯]  功能表上，指向 [尋找和取代]  ，再按一下 [快速尋找]  。</span><span class="sxs-lookup"><span data-stu-id="9a7d1-108">On the **Edit** menu, point to **Find and Replace,** and then click **QuickFind**.</span></span>  
  
3.  <span data-ttu-id="9a7d1-109">在 [尋找和取代]  文字方塊中，輸入要搜尋的文字。</span><span class="sxs-lookup"><span data-stu-id="9a7d1-109">In the **Find and Replace** text box, enter the text to search for.</span></span>  
  
4.  <span data-ttu-id="9a7d1-110">在 [查詢]  清單中，選取 [所有開啟的文件]  。</span><span class="sxs-lookup"><span data-stu-id="9a7d1-110">In the **Look in** list, select **All Open Documents**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9a7d1-111">當選取 [所有開啟的文件]  時，可能不會搜尋某些開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="9a7d1-111">Certain open files might not be searched when **All Open Documents** is selected.</span></span> <span data-ttu-id="9a7d1-112">搜尋只包括文字檢視 (如 [程式碼] 檢視) 所開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="9a7d1-112">Only files currently open in a textual view, such as Code view, are included in searches.</span></span> <span data-ttu-id="9a7d1-113">搜尋不包括 [設計師] 檢視中的檔案。</span><span class="sxs-lookup"><span data-stu-id="9a7d1-113">Files in Designer view are not included in searches.</span></span>  
  
5.  <span data-ttu-id="9a7d1-114">選取其他搜尋選項來增加搜尋的精確度。</span><span class="sxs-lookup"><span data-stu-id="9a7d1-114">Select additional search options to increase the accuracy of the search.</span></span>  
  
6.  <span data-ttu-id="9a7d1-115">按一下 [尋找下一個]  開始搜尋，再繼續按 [尋找下一個]  ，直到搜尋到最後一個檔案為止。</span><span class="sxs-lookup"><span data-stu-id="9a7d1-115">Click **Find Next** to start the search, and continue clicking **Find Next** until the last file has been searched.</span></span>  
  
 <span data-ttu-id="9a7d1-116">當搜尋通過文件的開頭或結尾時，狀態列會出現一則訊息。</span><span class="sxs-lookup"><span data-stu-id="9a7d1-116">When the search passes the beginning or end of the document, a message is displayed in the status bar.</span></span> <span data-ttu-id="9a7d1-117">當搜尋到了搜尋的起點時，會出現一個訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="9a7d1-117">A message box appears when the search reaches the starting point of the search.</span></span>  
  
#### <a name="to-replace-in-all-active-files-interactively"></a><span data-ttu-id="9a7d1-118">在所有作用檔案中，以互動方式取代</span><span class="sxs-lookup"><span data-stu-id="9a7d1-118">To replace in all active files interactively</span></span>  
  
1.  <span data-ttu-id="9a7d1-119">在 [編輯]  功能表上，指向 [尋找和取代]  ，再按一下 [快速尋找]  。</span><span class="sxs-lookup"><span data-stu-id="9a7d1-119">On the **Edit** menu, point to **Find and Replace**, and then click **QuickReplace**.</span></span>  
  
2.  <span data-ttu-id="9a7d1-120">在 [尋找目標]  方塊中，輸入要搜尋的文字。</span><span class="sxs-lookup"><span data-stu-id="9a7d1-120">In the **Find what** box, enter the text to search for.</span></span>  
  
3.  <span data-ttu-id="9a7d1-121">在 **[取代成]** 方塊中，輸入用來取代搜尋文字的文字。</span><span class="sxs-lookup"><span data-stu-id="9a7d1-121">In the **Replace with** box, enter the text to replace the search text.</span></span>  
  
4.  <span data-ttu-id="9a7d1-122">在 [查詢]  清單中，選取 [所有開啟的文件]  。</span><span class="sxs-lookup"><span data-stu-id="9a7d1-122">In the **Look in** list, select **All Open Documents**.</span></span>  
  
5.  <span data-ttu-id="9a7d1-123">按一下 [取代]  ，再繼續按 [取代]  ，直到取代最後一個檔案中最後一個相符的項目為止。</span><span class="sxs-lookup"><span data-stu-id="9a7d1-123">Click **Replace**, and continue clicking **Replace** until the last match in the last file has been replaced.</span></span> <span data-ttu-id="9a7d1-124">若要跳過不要取代的相符項目，請按一下 [尋找下一個]  。</span><span class="sxs-lookup"><span data-stu-id="9a7d1-124">Click **Find Next** to skip a match you do not want to replace.</span></span>  
  
     <span data-ttu-id="9a7d1-125">-或-</span><span class="sxs-lookup"><span data-stu-id="9a7d1-125">-or-</span></span>  
  
     <span data-ttu-id="9a7d1-126">選擇 [取代全部]  取代所有相符項目。</span><span class="sxs-lookup"><span data-stu-id="9a7d1-126">Choose **Replace All** to replace all matches.</span></span> <span data-ttu-id="9a7d1-127">此時會出現一個訊息方塊，列出取代的總數。</span><span class="sxs-lookup"><span data-stu-id="9a7d1-127">A message box appears, listing the total number of replacements.</span></span>  
  
 <span data-ttu-id="9a7d1-128">[取代全部]  命令會取代所有搜尋相符項目，其中包括您利用 [尋找下一個]  按鈕所略過的相符項目。</span><span class="sxs-lookup"><span data-stu-id="9a7d1-128">The **Replace All** command replaces all search matches, including those you have skipped with the **Find Next** button.</span></span> <span data-ttu-id="9a7d1-129">若要取消 [取代全部]，請在關閉任何檔案之前，按一下 [編輯] 功能表中的 [恢復]。</span><span class="sxs-lookup"><span data-stu-id="9a7d1-129">To cancel **Replace All**, click **Undo** from the **Edit** menu before closing any of the files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a7d1-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a7d1-130">See Also</span></span>  
 <span data-ttu-id="9a7d1-131">[以累加方式搜尋作用中的文件](search-an-active-document-incrementally.md) </span><span class="sxs-lookup"><span data-stu-id="9a7d1-131">[Search an Active Document Incrementally](search-an-active-document-incrementally.md) </span></span>  
 <span data-ttu-id="9a7d1-132">[搜尋和取代](search-and-replace.md) </span><span class="sxs-lookup"><span data-stu-id="9a7d1-132">[Search and Replace](search-and-replace.md) </span></span>  
 <span data-ttu-id="9a7d1-133">[使用結果清單搜尋文件](search-documents-using-results-lists.md) </span><span class="sxs-lookup"><span data-stu-id="9a7d1-133">[Search Documents Using Results Lists](search-documents-using-results-lists.md) </span></span>  
 <span data-ttu-id="9a7d1-134">[使用萬用字元搜尋文字](search-text-with-wildcards.md) </span><span class="sxs-lookup"><span data-stu-id="9a7d1-134">[Search Text with Wildcards](search-text-with-wildcards.md) </span></span>  
 [<span data-ttu-id="9a7d1-135">使用規則運算式搜尋文字</span><span class="sxs-lookup"><span data-stu-id="9a7d1-135">Search Text with Regular Expressions</span></span>](search-text-with-regular-expressions.md)  
  
  
