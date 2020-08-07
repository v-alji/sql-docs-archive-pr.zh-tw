---
title: " (查詢結果的選項-SQL Server 結果到文字頁面) |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryResults.SqlServer.SQLResultsToText
ms.assetid: 2ccbdf17-e14f-42f1-a836-ca999a3432c9
author: rothja
ms.author: jroth
ms.openlocfilehash: 4ece458e4bab9a57cb6692d4ac6dfdf2e8f4bd22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703234"
---
# <a name="options-query-results-sql-server-results-to-text-page"></a><span data-ttu-id="45c69-102"> (查詢結果的選項-SQL Server 到文字的結果頁面) </span><span class="sxs-lookup"><span data-stu-id="45c69-102">Options (Query Results-SQL Server-Results to Text Page)</span></span>
  <span data-ttu-id="45c69-103">使用此頁面，即可指定以文字格式顯示查詢結果集的選項。</span><span class="sxs-lookup"><span data-stu-id="45c69-103">Use this page to specify the options for displaying a query result set in text format.</span></span> <span data-ttu-id="45c69-104">這些選項的變更僅適用於新的 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 查詢。</span><span class="sxs-lookup"><span data-stu-id="45c69-104">Changes to these options are applied only to new [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] queries.</span></span> <span data-ttu-id="45c69-105">若要變更目前查詢的選項，請按一下 [**查詢**] 功能表上的 [**查詢選項**]，或在查詢視窗中按一下滑鼠右鍵 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，然後選取 [**查詢選項**]。</span><span class="sxs-lookup"><span data-stu-id="45c69-105">To change the options for the current queries, click **Query Options** on the **Query** menu, or right-click in the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Query window, and select **Query Options**.</span></span> <span data-ttu-id="45c69-106">在 **[查詢選項]** 對話方塊中，於 **[結果]** 之下，按一下 **[文字]**。</span><span class="sxs-lookup"><span data-stu-id="45c69-106">In the **Query Options** dialog box, under **Results**, click **Text**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="45c69-107">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="45c69-107">UI element list</span></span>  
 <span data-ttu-id="45c69-108">**輸出格式**</span><span class="sxs-lookup"><span data-stu-id="45c69-108">**Output format**</span></span>  
 <span data-ttu-id="45c69-109">根據預設，輸出會顯示在以空格填補結果所建立的資料行中。</span><span class="sxs-lookup"><span data-stu-id="45c69-109">By default the output is displayed in columns created by padding the results with spaces.</span></span> <span data-ttu-id="45c69-110">其他選項為使用逗號、定位點或空格來分隔資料行。</span><span class="sxs-lookup"><span data-stu-id="45c69-110">Other options are to use commas, tabs, or spaces to separate columns.</span></span> <span data-ttu-id="45c69-111">在此下拉式清單中選取 [自訂分隔符號]\*\*\*\*，即可在 [自訂分隔符號]\*\*\*\* 文字方塊中指定不同的分隔字元。</span><span class="sxs-lookup"><span data-stu-id="45c69-111">Select **Custom delimiter** from this drop-down list to specify a different delimiting character in the **Custom delimiter** text box.</span></span>  
  
 <span data-ttu-id="45c69-112">**[自訂分隔符號]**</span><span class="sxs-lookup"><span data-stu-id="45c69-112">**Custom delimiter**</span></span>  
 <span data-ttu-id="45c69-113">指定您要用來分隔資料行的字元。</span><span class="sxs-lookup"><span data-stu-id="45c69-113">Specify the character of your choice to separate columns.</span></span> <span data-ttu-id="45c69-114">此文字方塊只有在 [輸出格式]\*\*\*\* 下拉式清單方塊中，按一下自訂分隔符號時才能使用。</span><span class="sxs-lookup"><span data-stu-id="45c69-114">This text box is available only if you clicked Custom delimiter in the **Output format** drop-down list box.</span></span>  
  
 <span data-ttu-id="45c69-115">**在結果集內包含資料行標頭**</span><span class="sxs-lookup"><span data-stu-id="45c69-115">**Include column headers in the result set**</span></span>  
 <span data-ttu-id="45c69-116">如果您不要每個資料行均標示有資料行標題，請清除此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="45c69-116">Clear this check box if you do not want each column labeled with a column title.</span></span>  
  
 <span data-ttu-id="45c69-117">**在結果集裡包含查詢**</span><span class="sxs-lookup"><span data-stu-id="45c69-117">**Include the query in the result set**</span></span>  
 <span data-ttu-id="45c69-118">選取此核取方塊，即可在查詢結果的前面，包含正在結果窗格中執行之查詢的查詢文字。</span><span class="sxs-lookup"><span data-stu-id="45c69-118">Select this check box to include the text of the query that is running in the results pane before the results of the query.</span></span>  
  
 <span data-ttu-id="45c69-119">**收到結果時捲動**</span><span class="sxs-lookup"><span data-stu-id="45c69-119">**Scroll as results are received**</span></span>  
 <span data-ttu-id="45c69-120">選取此核取方塊，將顯示焦點放在結果集尾端最新傳回的記錄。</span><span class="sxs-lookup"><span data-stu-id="45c69-120">Select this check box to keep the display focus on the most recently returned records at the end of the results set.</span></span> <span data-ttu-id="45c69-121">清除此核取方塊，即可將作用中的顯示保持為接收到的第一組資料列。</span><span class="sxs-lookup"><span data-stu-id="45c69-121">Clear this check box to keep the display focus on the first rows received.</span></span>  
  
 <span data-ttu-id="45c69-122">**數值靠右對齊**</span><span class="sxs-lookup"><span data-stu-id="45c69-122">**Right align numeric values**</span></span>  
 <span data-ttu-id="45c69-123">選取此核取方塊，即可將數值靠資料行的右邊對齊。</span><span class="sxs-lookup"><span data-stu-id="45c69-123">Select this check box to align numeric values to the right of the column.</span></span> <span data-ttu-id="45c69-124">如此可便於檢閱有固定小數位數的數字。</span><span class="sxs-lookup"><span data-stu-id="45c69-124">This can make it easier to review numbers with a fixed number of decimal places.</span></span>  
  
 <span data-ttu-id="45c69-125">**執行查詢之後捨棄結果**</span><span class="sxs-lookup"><span data-stu-id="45c69-125">**Discard result after query executes**</span></span>  
 <span data-ttu-id="45c69-126">選取此核取方塊，當查詢結果顯示於查詢視窗的結果窗格之後，即捨棄查詢結果。</span><span class="sxs-lookup"><span data-stu-id="45c69-126">Select this check box to discard the query results after they are displayed in the results pane of the query window.</span></span>  
  
 <span data-ttu-id="45c69-127">**在其他索引標籤中顯示結果**</span><span class="sxs-lookup"><span data-stu-id="45c69-127">**Display results in a separate tab**</span></span>  
 <span data-ttu-id="45c69-128">選取此核取方塊，即可在新的文件視窗中顯示結果集，而非在查詢文件視窗的下方顯示。</span><span class="sxs-lookup"><span data-stu-id="45c69-128">Select this check box to display the result set in a new document window, instead of at the bottom of the query document window.</span></span>  
  
 <span data-ttu-id="45c69-129">**執行查詢後，切換至結果索引標籤**</span><span class="sxs-lookup"><span data-stu-id="45c69-129">**Switch to results tab after the query executes**</span></span>  
 <span data-ttu-id="45c69-130">選取此核取方塊以自動將螢幕焦點設定為結果集。</span><span class="sxs-lookup"><span data-stu-id="45c69-130">Select this check box to automatically set the screen focus to the result set.</span></span>  
  
 <span data-ttu-id="45c69-131">**每個資料行中顯示的最大字元數**</span><span class="sxs-lookup"><span data-stu-id="45c69-131">**Maximum number of characters displayed in each column**</span></span>  
 <span data-ttu-id="45c69-132">這個值預設為 256。</span><span class="sxs-lookup"><span data-stu-id="45c69-132">This value defaults to 256.</span></span> <span data-ttu-id="45c69-133">增加這個值即可顯示較大的結果集而不會截斷。</span><span class="sxs-lookup"><span data-stu-id="45c69-133">Increase this value to display larger result sets without truncation.</span></span> <span data-ttu-id="45c69-134">最大值為 8,192。</span><span class="sxs-lookup"><span data-stu-id="45c69-134">The maximum value is 8,192.</span></span>  
  
 <span data-ttu-id="45c69-135">**重設為預設值**</span><span class="sxs-lookup"><span data-stu-id="45c69-135">**Reset to Default**</span></span>  
 <span data-ttu-id="45c69-136">將此頁面上的所有值重設為原始預設值。</span><span class="sxs-lookup"><span data-stu-id="45c69-136">Resets all values on this page to the original default values.</span></span>  
  
  
