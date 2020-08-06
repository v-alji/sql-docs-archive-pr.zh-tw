---
title: 查詢選項結果 (Text 頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.text.f1
ms.assetid: fd2fb409-58f9-4ede-8349-ce007126b68d
author: rothja
ms.author: jroth
ms.openlocfilehash: 45019450c8fc959b440aac5bf1e9098e59cecefc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599164"
---
# <a name="query-options-results-text-page"></a><span data-ttu-id="867e8-102">查詢選項結果 (文字頁面)</span><span class="sxs-lookup"><span data-stu-id="867e8-102">Query Options Results (Text Page)</span></span>
  <span data-ttu-id="867e8-103">使用此頁面，即可指定以文字格式顯示查詢結果集的選項。</span><span class="sxs-lookup"><span data-stu-id="867e8-103">Use this page to specify the options for displaying a query result set in text format.</span></span> <span data-ttu-id="867e8-104">選取 **[將結果存檔]** 時，此頁面上的設定也適用。</span><span class="sxs-lookup"><span data-stu-id="867e8-104">The settings on this page also apply when **Results to File** is selected.</span></span>  
  
 <span data-ttu-id="867e8-105">**輸出格式**</span><span class="sxs-lookup"><span data-stu-id="867e8-105">**Output format**</span></span>  
 <span data-ttu-id="867e8-106">根據預設，輸出會顯示在以空格填補結果所建立的資料行中。</span><span class="sxs-lookup"><span data-stu-id="867e8-106">By default the output is displayed in columns created by padding the results with spaces.</span></span> <span data-ttu-id="867e8-107">其他選項包括使用逗號、索引標籤，或空格來分隔資料行。</span><span class="sxs-lookup"><span data-stu-id="867e8-107">Other options are using commas, tabs, or spaces to separate columns.</span></span> <span data-ttu-id="867e8-108">選取 **[自訂分隔符號]** 核取方塊，即可在 **[自訂分隔符號]** 方塊中指定不同的分隔字元。</span><span class="sxs-lookup"><span data-stu-id="867e8-108">Select the **Custom delimiter** check box to specify a different delimiting character in the **Custom delimiter** box.</span></span>  
  
 <span data-ttu-id="867e8-109">**[自訂分隔符號]**</span><span class="sxs-lookup"><span data-stu-id="867e8-109">**Custom delimiter**</span></span>  
 <span data-ttu-id="867e8-110">指定您要用來分隔資料行的字元。</span><span class="sxs-lookup"><span data-stu-id="867e8-110">Specify the character of your choice to separate columns.</span></span> <span data-ttu-id="867e8-111">唯有在 **[輸出格式]** 方塊中選取了 **[自訂分隔符號]** 核取方塊之後，此選項才可以使用。</span><span class="sxs-lookup"><span data-stu-id="867e8-111">This option is only available if the **Custom delimiter** check box is selected in the **Output format** box.</span></span>  
  
 <span data-ttu-id="867e8-112">**在結果集內包含資料行標頭**</span><span class="sxs-lookup"><span data-stu-id="867e8-112">**Include column headers in the result set**</span></span>  
 <span data-ttu-id="867e8-113">如果您不要每個資料行均標示有資料行標題，請清除此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="867e8-113">Clear this check box if you do not want each column labeled with a column title.</span></span>  
  
 <span data-ttu-id="867e8-114">**收到結果時捲動**</span><span class="sxs-lookup"><span data-stu-id="867e8-114">**Scroll as results are received**</span></span>  
 <span data-ttu-id="867e8-115">選取此核取方塊，即可將顯示焦點保持在最近傳回的底部記錄上。</span><span class="sxs-lookup"><span data-stu-id="867e8-115">Select this check box to keep the display focus on the most recently returned records at the bottom.</span></span> <span data-ttu-id="867e8-116">清除此核取方塊，即可將作用中的顯示保持為接收到的第一組資料列。</span><span class="sxs-lookup"><span data-stu-id="867e8-116">Clear this check box to keep the display focus on the first rows received.</span></span>  
  
 <span data-ttu-id="867e8-117">**數值靠右對齊**</span><span class="sxs-lookup"><span data-stu-id="867e8-117">**Right align numeric values**</span></span>  
 <span data-ttu-id="867e8-118">選取此核取方塊，即可將數值靠資料行的右邊對齊。</span><span class="sxs-lookup"><span data-stu-id="867e8-118">Select this check box to align numeric values to the right of the column.</span></span> <span data-ttu-id="867e8-119">如此可便於檢閱有固定小數位數的數字。</span><span class="sxs-lookup"><span data-stu-id="867e8-119">This can make it easier to review numbers with a fixed number of decimal places.</span></span>  
  
 <span data-ttu-id="867e8-120">**執行查詢之後捨棄結果**</span><span class="sxs-lookup"><span data-stu-id="867e8-120">**Discard result after query executes**</span></span>  
 <span data-ttu-id="867e8-121">在螢幕上顯示查詢結果之後即將其捨棄，以釋放記憶體。</span><span class="sxs-lookup"><span data-stu-id="867e8-121">Frees memory by discarding the query results after the screen display has received them.</span></span>  
  
 <span data-ttu-id="867e8-122">**在其他索引標籤中顯示結果**</span><span class="sxs-lookup"><span data-stu-id="867e8-122">**Display results in a separate tab**</span></span>  
 <span data-ttu-id="867e8-123">選取此核取方塊，即可在新的文件視窗中顯示結果集，而非在查詢文件視窗的下方顯示。</span><span class="sxs-lookup"><span data-stu-id="867e8-123">Select this check box to display the result set in a new document window, instead of at the bottom of the query document window.</span></span>  
  
 <span data-ttu-id="867e8-124">**執行查詢後，切換至結果索引標籤**</span><span class="sxs-lookup"><span data-stu-id="867e8-124">**Switch to results tab after the query executes**</span></span>  
 <span data-ttu-id="867e8-125">按一下以自動將螢幕焦點設定為結果集。</span><span class="sxs-lookup"><span data-stu-id="867e8-125">Click to automatically set the screen focus to the result set.</span></span>  
  
 <span data-ttu-id="867e8-126">**每個資料行中顯示的最大字元數**</span><span class="sxs-lookup"><span data-stu-id="867e8-126">**Maximum number of characters displayed in each column**</span></span>  
 <span data-ttu-id="867e8-127">這個值預設為 256。</span><span class="sxs-lookup"><span data-stu-id="867e8-127">This value defaults to 256.</span></span> <span data-ttu-id="867e8-128">增加這個值即可顯示較大的結果集而不會截斷。</span><span class="sxs-lookup"><span data-stu-id="867e8-128">Increase this value to display larger result sets without truncation.</span></span>  
  
 <span data-ttu-id="867e8-129">**重設為預設值**</span><span class="sxs-lookup"><span data-stu-id="867e8-129">**Reset to Default**</span></span>  
 <span data-ttu-id="867e8-130">將此頁面上的所有值重設為原始預設值。</span><span class="sxs-lookup"><span data-stu-id="867e8-130">Resets all values on this page to the original default values.</span></span>  
  
## <a name="saving-a-text-result-set-with-headers"></a><span data-ttu-id="867e8-131">儲存具標頭的文字結果集</span><span class="sxs-lookup"><span data-stu-id="867e8-131">Saving a text result set with headers</span></span>  
 <span data-ttu-id="867e8-132">若要將查詢結果儲存為具標頭的文字檔案，請選取 **[在結果集內包含資料行標頭]** 核取方塊，以及輸出的分隔格式。</span><span class="sxs-lookup"><span data-stu-id="867e8-132">To save query results as a text file with headers, select the **Include column headers in the result set** check box and a delimited output format.</span></span> <span data-ttu-id="867e8-133">當您按一下工具列上的 [將結果存檔]\*\*\*\* 時；或以滑鼠右鍵按一下任何查詢結果，按一下 [儲存結果]\*\*\*\*，輸入檔案名稱，然後按一下 [儲存]\*\*\*\* 時；此報表檔就會包含標頭。</span><span class="sxs-lookup"><span data-stu-id="867e8-133">Now the report file will contain headers when you click **Results to File** on the toolbar, or when you right-click any query results, click **Save Results As**, type a file name, and then click **Save**.</span></span>  
  
  
