---
title: 搜尋和取代
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- match case [SQL Server]
- undo operations
- searches [SQL Server Management Studio]
- replacing text
- quick search and replaces [SQL Server Management Studio]
- Query Editor [SQL Server Management Studio], undo
- Query Editor [SQL Server Management Studio], searching
- regular expressions [SQL Server Management Studio]
- finding text [SQL Server Management Studio]
- text [SQL Server], search and replace operations
- finding [SQL Server Management Studio]
- locating text
- Query Editor [SQL Server Management Studio], replacing text
- Find and Replace dialog box
- wildcard options [SQL Server Management Studio]
- match whole word [SQL Server]
- searches [SQL Server Management Studio], replacing
ms.assetid: 3641c7b3-3e3e-4ddd-af82-c15b50004f94
author: rothja
ms.author: jroth
ms.openlocfilehash: 55422fa7201213477426c7bc25c45ff05acf8945
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592593"
---
# <a name="search-and-replace"></a><span data-ttu-id="9bf7a-102">搜尋和取代</span><span class="sxs-lookup"><span data-stu-id="9bf7a-102">Search and Replace</span></span>
  <span data-ttu-id="9bf7a-103">您可以利用多種不同的方式來尋找和取代文字。</span><span class="sxs-lookup"><span data-stu-id="9bf7a-103">There are several different ways to find and replace text.</span></span> <span data-ttu-id="9bf7a-104">在 **[編輯]** 功能表上， **[尋找和取代]** 提供了四個選項： **[快速尋找]** 、 **[快速取代]** 、 **[檔案中尋找]** 和 **[檔案中取代]** 。</span><span class="sxs-lookup"><span data-stu-id="9bf7a-104">On the **Edit** menu, **Find and Replace** offers four choices: **Quick Find**, **Quick Replace**, **Find in Files**, or **Replace in Files**.</span></span> <span data-ttu-id="9bf7a-105">這些選項會開啟各個版本的 **[尋找和取代]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9bf7a-105">Each of these opens versions of the **Find and Replace** dialog box.</span></span> <span data-ttu-id="9bf7a-106">您也可以不用對話方塊，而利用累加搜尋鍵盤快速鍵來搜尋。</span><span class="sxs-lookup"><span data-stu-id="9bf7a-106">You can also search without a dialog box by using incremental search keyboard shortcut keys.</span></span> <span data-ttu-id="9bf7a-107">這些技術可讓您控制尋找和取代的範圍，以及選擇檢閱搜尋相符項目和取代項目的方法。</span><span class="sxs-lookup"><span data-stu-id="9bf7a-107">These techniques allow you to control the scope of find and replace, and choose the method of reviewing search matches and replacements.</span></span>  
  
 <span data-ttu-id="9bf7a-108">當您搜尋和取代文字時，您應該考慮下列各點：</span><span class="sxs-lookup"><span data-stu-id="9bf7a-108">You should consider the following when you search and replace text:</span></span>  
  
-   <span data-ttu-id="9bf7a-109">**[尋找和取代]** 對話方塊所設定的選項會影響所有搜尋。</span><span class="sxs-lookup"><span data-stu-id="9bf7a-109">Options set in the **Find and Replace** dialog box affect all the searches.</span></span> <span data-ttu-id="9bf7a-110">這些選項包括 **[大小寫須相符]** 、 **[全字拼寫須相符]** 、 **[向上搜尋]** 、 **[搜尋隱藏文字]** 、 **[萬用字元]** 、 **[規則運算式]** 、 **[查詢所有開啟的文件]** 和 **[查詢目前專案]** 。</span><span class="sxs-lookup"><span data-stu-id="9bf7a-110">These options include **Match case**, **Match whole word**, **Search up**, **Search hidden text**, **Wildcards**, **Regular Expressions**, **Look in All Open Documents**, and **Look in Current Project**.</span></span> <span data-ttu-id="9bf7a-111">並非 **[尋找和取代]** 對話方塊的所有版本都提供了所有選項。</span><span class="sxs-lookup"><span data-stu-id="9bf7a-111">All options are not available in all versions of the **Find and Replace** dialog box.</span></span>  
  
-   <span data-ttu-id="9bf7a-112">只有在取代作業之後維持開啟狀態的文件，才能夠使用 **[恢復]** 。</span><span class="sxs-lookup"><span data-stu-id="9bf7a-112">**Undo** is available only for documents left open after a replace operation.</span></span>  
  
-   <span data-ttu-id="9bf7a-113">跨越多個檔案的 **[全部取代]** 作業，其 **[恢復]** 會被視為跨越所有受影響之檔案的單一龐大動作。</span><span class="sxs-lookup"><span data-stu-id="9bf7a-113">**Undo** for a **Replace All** operation that spans more than one file is considered a single, bulk action across all the affected files.</span></span> <span data-ttu-id="9bf7a-114">也就是說，您無法只恢復某些檔案中的變更，卻保留其他檔案中的變更。</span><span class="sxs-lookup"><span data-stu-id="9bf7a-114">That is, you cannot undo the change in some files while retaining the change in other files.</span></span>  
  
 <span data-ttu-id="9bf7a-115">一般而言，您無法利用圖形檢視來搜尋項目。</span><span class="sxs-lookup"><span data-stu-id="9bf7a-115">Generally, you cannot search items with graphical views.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bf7a-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9bf7a-116">See Also</span></span>  
 <span data-ttu-id="9bf7a-117">[以累加方式搜尋作用中的文件](search-an-active-document-incrementally.md) </span><span class="sxs-lookup"><span data-stu-id="9bf7a-117">[Search an Active Document Incrementally](search-an-active-document-incrementally.md) </span></span>  
 <span data-ttu-id="9bf7a-118">[以互動方式搜尋文件](search-documents-interactively.md) </span><span class="sxs-lookup"><span data-stu-id="9bf7a-118">[Search Documents Interactively](search-documents-interactively.md) </span></span>  
 <span data-ttu-id="9bf7a-119">[使用結果清單搜尋文件](search-documents-using-results-lists.md) </span><span class="sxs-lookup"><span data-stu-id="9bf7a-119">[Search Documents Using Results Lists](search-documents-using-results-lists.md) </span></span>  
 <span data-ttu-id="9bf7a-120">[使用萬用字元搜尋文字](search-text-with-wildcards.md) </span><span class="sxs-lookup"><span data-stu-id="9bf7a-120">[Search Text with Wildcards](search-text-with-wildcards.md) </span></span>  
 [<span data-ttu-id="9bf7a-121">使用規則運算式搜尋文字</span><span class="sxs-lookup"><span data-stu-id="9bf7a-121">Search Text with Regular Expressions</span></span>](search-text-with-regular-expressions.md)  
  
  
