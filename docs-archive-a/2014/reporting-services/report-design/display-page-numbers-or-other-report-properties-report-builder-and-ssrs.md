---
title: 顯示頁碼或其他報表屬性 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c7d95245-4709-4d04-acb4-59bf71e60d97
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: efc3d5d5de11af1fcdfefc52ed12d5057ee12668
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595738"
---
# <a name="display-page-numbers-or-other-report-properties-report-builder-and-ssrs"></a><span data-ttu-id="ff818-102">顯示頁碼或其他報表屬性 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="ff818-102">Display Page Numbers or Other Report Properties (Report Builder and SSRS)</span></span>
  <span data-ttu-id="ff818-103">您可以輕鬆地將頁碼、報表標題、檔案名稱和其他報表屬性加入至報表的頁首或頁尾。</span><span class="sxs-lookup"><span data-stu-id="ff818-103">It's easy to add page numbers, a report title, file name, and other report properties to the page headers or footers of your report.</span></span> <span data-ttu-id="ff818-104">在 [報表資料] 窗格的 [內建欄位] 資料夾中，這些屬性會儲存成欄位：</span><span class="sxs-lookup"><span data-stu-id="ff818-104">These properties are stored as fields in the Built-in Fields folder in the Report Data pane:</span></span>  
  
-   <span data-ttu-id="ff818-105">執行時間</span><span class="sxs-lookup"><span data-stu-id="ff818-105">Execution time</span></span>  
  
-   <span data-ttu-id="ff818-106">頁碼</span><span class="sxs-lookup"><span data-stu-id="ff818-106">Page number</span></span>  
  
-   <span data-ttu-id="ff818-107">報表資料夾</span><span class="sxs-lookup"><span data-stu-id="ff818-107">Report folder</span></span>  
  
-   <span data-ttu-id="ff818-108">報告名稱</span><span class="sxs-lookup"><span data-stu-id="ff818-108">Report name</span></span>  
  
-   <span data-ttu-id="ff818-109">報表伺服器 URL</span><span class="sxs-lookup"><span data-stu-id="ff818-109">Report server URL</span></span>  
  
-   <span data-ttu-id="ff818-110">總頁數</span><span class="sxs-lookup"><span data-stu-id="ff818-110">Total pages</span></span>  
  
-   <span data-ttu-id="ff818-111">使用者識別碼</span><span class="sxs-lookup"><span data-stu-id="ff818-111">User ID</span></span>  
  
-   <span data-ttu-id="ff818-112">Language</span><span class="sxs-lookup"><span data-stu-id="ff818-112">Language</span></span>  
  
 <span data-ttu-id="ff818-113">您可能會想要針對頁碼，在數字前面加入 "Page" 一詞。</span><span class="sxs-lookup"><span data-stu-id="ff818-113">For a page number, you may want to add the word "Page" before the number.</span></span> <span data-ttu-id="ff818-114">您可能也會想要顯示總頁數。</span><span class="sxs-lookup"><span data-stu-id="ff818-114">You may also want to show the total number of pages.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ff818-115">將總頁數加入至頁尾可能會在您執行或預覽報表時降低效能。</span><span class="sxs-lookup"><span data-stu-id="ff818-115">Adding the total number of pages to the footer may slow performance when you run or preview your report.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-page-number-or-other-report-properties"></a><span data-ttu-id="ff818-116">若要加入頁碼或其他報表屬性</span><span class="sxs-lookup"><span data-stu-id="ff818-116">To add a page number or other report properties</span></span>  
  
1.  <span data-ttu-id="ff818-117">在 [報表資料] 窗格中，展開 [內建欄位] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="ff818-117">In the Report Data pane, expand the Built-in Fields folder.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ff818-118">如果您看不到 [報表資料] 窗格，請在 [檢視] 索引標籤上，核取 [報表資料]  。</span><span class="sxs-lookup"><span data-stu-id="ff818-118">If you don't see the Report Data pane, on the View tab, check **Report Data**.</span></span>  
  
2.  <span data-ttu-id="ff818-119">將 [頁碼]  欄位從 [報表資料] 窗格拖曳至報表頁首或頁尾。</span><span class="sxs-lookup"><span data-stu-id="ff818-119">Drag the **Page Number** field from the Report Data pane to the report header or footer.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ff818-120">頁尾就會自動加入至報表。</span><span class="sxs-lookup"><span data-stu-id="ff818-120">The page footer is added to the report automatically.</span></span> <span data-ttu-id="ff818-121">若要新增頁首，請在 [插入]  索引標籤上，按一下 [頁首]  ，然後按一下 [新增頁首]  。</span><span class="sxs-lookup"><span data-stu-id="ff818-121">To add a page header, on the **Insert** tab, click **Header**, and then click **Add Header**.</span></span>  
    >   
    >  <span data-ttu-id="ff818-122">包含簡單運算式 [&PageNumber] 的文字方塊隨即加入。</span><span class="sxs-lookup"><span data-stu-id="ff818-122">A text box that contains the simple expression [&PageNumber] is added.</span></span>  
  
### <a name="to-add-the-word-page-before-the-page-number"></a><span data-ttu-id="ff818-123">若要在頁碼前面加入 "Page" 一詞</span><span class="sxs-lookup"><span data-stu-id="ff818-123">To add the word "Page" before the page number</span></span>  
  
1.  <span data-ttu-id="ff818-124">以滑鼠右鍵按一下包含 [&PageNumber] 的文字方塊，然後按一下 [運算式]  。</span><span class="sxs-lookup"><span data-stu-id="ff818-124">Right-click the text box that contains [&PageNumber] and click **Expressions**.</span></span>  
  
     <span data-ttu-id="ff818-125">[設定運算式對象: 值]  文字方塊包含運算式 =Globals!PageNumber。</span><span class="sxs-lookup"><span data-stu-id="ff818-125">The **Set Expression for: Value** text box contains the expression =Globals!PageNumber.</span></span>  
  
2.  <span data-ttu-id="ff818-126">將游標放在等號 (=) 之後，然後輸入 `"Page " &`。</span><span class="sxs-lookup"><span data-stu-id="ff818-126">Place the cursor after the = sign and type `"Page " &`.</span></span>  
  
     <span data-ttu-id="ff818-127">運算式現在是 ="Page "&Globals!PageNumber</span><span class="sxs-lookup"><span data-stu-id="ff818-127">The expression is now  ="Page "&Globals!PageNumber</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-add-total-number-of-pages-after-the-page-number"></a><span data-ttu-id="ff818-128">若要在頁碼後面加入總頁數</span><span class="sxs-lookup"><span data-stu-id="ff818-128">To add total number of pages after the page number</span></span>  
  
1.  <span data-ttu-id="ff818-129">以滑鼠右鍵按一下包含運算式的文字方塊，然後按一下 [運算式]  。</span><span class="sxs-lookup"><span data-stu-id="ff818-129">Right click the text box with the expression and click **Expressions**.</span></span>  
  
2.  <span data-ttu-id="ff818-130">在運算式結尾鍵入 **&" of "&** 。</span><span class="sxs-lookup"><span data-stu-id="ff818-130">Type **&" of "&** at the end of the expression.</span></span>  
  
3.  <span data-ttu-id="ff818-131">在 [類別目錄] 窗格中，展開 [內建欄位]  ，然後按兩下 [TotalPages]  。</span><span class="sxs-lookup"><span data-stu-id="ff818-131">In the Category pane, expand **Built-in Fields** and double-click **TotalPages**.</span></span>  
  
     <span data-ttu-id="ff818-132">運算式現在是 ="Page "&Globals!PageNumber &" of "&Globals!TotalPages</span><span class="sxs-lookup"><span data-stu-id="ff818-132">The expression is now ="Page "&Globals!PageNumber &" of "&Globals!TotalPages</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ff818-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff818-133">See Also</span></span>  
 <span data-ttu-id="ff818-134">[頁首和頁尾 &#40;報表產生器及 SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="ff818-134">[Page Headers and Footers &#40;Report Builder and SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="ff818-135">格式化文字方塊中的文字 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ff818-135">Format Text in a Text Box &#40;Report Builder and SSRS&#41;</span></span>](format-text-in-a-text-box-report-builder-and-ssrs.md)  
  
  
