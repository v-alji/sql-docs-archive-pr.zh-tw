---
title: 使用萬用字元搜尋文字
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- vswildcardsbuilder
helpviewer_keywords:
- searches [SQL Server Management Studio], wildcards
- Query Editor [SQL Server Management Studio], wildcard searches
- wildcard options [SQL Server Management Studio]
ms.assetid: 449600f8-cc87-4b3f-878a-59c158a88a40
author: rothja
ms.author: jroth
ms.openlocfilehash: cc4e24c3dce73e46350b0c106429c42ab5f0edb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606723"
---
# <a name="search-text-with-wildcards"></a><span data-ttu-id="b92e3-102">使用萬用字元搜尋文字</span><span class="sxs-lookup"><span data-stu-id="b92e3-102">Search Text with Wildcards</span></span>
  <span data-ttu-id="b92e3-103">下列運算式可以取代  **[尋找和取代]** [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 對話方塊中 [尋找目標]  欄位的字元或數字。</span><span class="sxs-lookup"><span data-stu-id="b92e3-103">The following expressions can replace characters or digits in the **Find what** field of the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Find and Replace** dialog box.</span></span>  
  
#### <a name="to-search-using-wildcards"></a><span data-ttu-id="b92e3-104">若要利用萬用字元搜尋</span><span class="sxs-lookup"><span data-stu-id="b92e3-104">To search using wildcards</span></span>  
  
1.  <span data-ttu-id="b92e3-105">若要在 [快速尋找]、 **[檔案中尋找]** 、 **[快速取代]** 或 **[檔案中取代]** 等作業期間，在 **[尋找目標]** 欄位中啟用萬用字元，請在 **[尋找選項]** 之下，選取 **[使用]** 選項，再選擇 **[萬用字元]** 。</span><span class="sxs-lookup"><span data-stu-id="b92e3-105">To enable the use of wildcards in the **Find what** field during Quick Find, **Find in Files**, **Quick Replace**, or **Replace in Files** operations, select the **Use** option under **Find Options** and then choose **Wildcards**.</span></span>  
  
2.  <span data-ttu-id="b92e3-106">之後，就可以使用 **[尋找目標]** 欄位旁三角形的 **[參考清單]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="b92e3-106">The triangular **Reference List** button next to the **Find what** field then becomes available.</span></span> <span data-ttu-id="b92e3-107">請按一下這個按鈕來顯示可用萬用字元的清單。</span><span class="sxs-lookup"><span data-stu-id="b92e3-107">Click this button to display a list of the available wildcards.</span></span> <span data-ttu-id="b92e3-108">當您從 **[參考清單]** 中選擇任何項目時，項目會插入 **[尋找目標]** 字串中。</span><span class="sxs-lookup"><span data-stu-id="b92e3-108">When you choose any item from the **Reference List**, it is inserted into the **Find what** string.</span></span>  
  
 <span data-ttu-id="b92e3-109">下表說明 **[參考清單]** 中可用的萬用字元。</span><span class="sxs-lookup"><span data-stu-id="b92e3-109">The following table describes the wildcards available in the **Reference List**.</span></span>  
  
|<span data-ttu-id="b92e3-110">運算是</span><span class="sxs-lookup"><span data-stu-id="b92e3-110">Expression</span></span>|<span data-ttu-id="b92e3-111">語法</span><span class="sxs-lookup"><span data-stu-id="b92e3-111">Syntax</span></span>|<span data-ttu-id="b92e3-112">描述</span><span class="sxs-lookup"><span data-stu-id="b92e3-112">Description</span></span>|  
|----------------|------------|-----------------|  
|<span data-ttu-id="b92e3-113">任何單一字元</span><span class="sxs-lookup"><span data-stu-id="b92e3-113">Any single character</span></span>|<span data-ttu-id="b92e3-114">?</span><span class="sxs-lookup"><span data-stu-id="b92e3-114">?</span></span>|<span data-ttu-id="b92e3-115">符合任何單一字元。</span><span class="sxs-lookup"><span data-stu-id="b92e3-115">Matches any single character.</span></span>|  
|<span data-ttu-id="b92e3-116">任何單一位數</span><span class="sxs-lookup"><span data-stu-id="b92e3-116">Any single digit</span></span>|#|<span data-ttu-id="b92e3-117">符合任何單一位數。</span><span class="sxs-lookup"><span data-stu-id="b92e3-117">Matches any single digit.</span></span> <span data-ttu-id="b92e3-118">例如，7# 符合在 7 後面接著另一個數字的數字，如 71，17 便不符合。</span><span class="sxs-lookup"><span data-stu-id="b92e3-118">For example, 7# matches numbers that include 7 followed by another number, such as 71, but not 17.</span></span>|  
|<span data-ttu-id="b92e3-119">不在集合中的字元</span><span class="sxs-lookup"><span data-stu-id="b92e3-119">Characters not in set</span></span>|<span data-ttu-id="b92e3-120">[!</span><span class="sxs-lookup"><span data-stu-id="b92e3-120">[!</span></span> <span data-ttu-id="b92e3-121">]</span><span class="sxs-lookup"><span data-stu-id="b92e3-121">]</span></span>|<span data-ttu-id="b92e3-122">符合集合中所未指定的任何字元。</span><span class="sxs-lookup"><span data-stu-id="b92e3-122">Matches any one character that is not specified in the set.</span></span>|  
|<span data-ttu-id="b92e3-123">一或多個字元</span><span class="sxs-lookup"><span data-stu-id="b92e3-123">One or more characters</span></span>|*|<span data-ttu-id="b92e3-124">符何任何一或多個字元。</span><span class="sxs-lookup"><span data-stu-id="b92e3-124">Matches any one or more characters.</span></span> <span data-ttu-id="b92e3-125">例如，new\* 符合任何包括 "new" 的文字，如 newfile.txt。</span><span class="sxs-lookup"><span data-stu-id="b92e3-125">For example, new\* matches any text that includes "new", such as newfile.txt.</span></span>|  
|<span data-ttu-id="b92e3-126">字元集</span><span class="sxs-lookup"><span data-stu-id="b92e3-126">Set of characters</span></span>|<span data-ttu-id="b92e3-127">[ ]</span><span class="sxs-lookup"><span data-stu-id="b92e3-127">[ ]</span></span>|<span data-ttu-id="b92e3-128">符合集合中所指定的任何一個字元。</span><span class="sxs-lookup"><span data-stu-id="b92e3-128">Matches any one of the characters specified in the set.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b92e3-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b92e3-129">See Also</span></span>  
 <span data-ttu-id="b92e3-130">[搜尋和取代](search-and-replace.md) </span><span class="sxs-lookup"><span data-stu-id="b92e3-130">[Search and Replace](search-and-replace.md) </span></span>  
 [<span data-ttu-id="b92e3-131">使用規則運算式搜尋文字</span><span class="sxs-lookup"><span data-stu-id="b92e3-131">Search Text with Regular Expressions</span></span>](search-text-with-regular-expressions.md)  
