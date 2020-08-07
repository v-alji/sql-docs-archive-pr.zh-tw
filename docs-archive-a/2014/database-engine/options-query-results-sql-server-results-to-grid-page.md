---
title: " (查詢結果的選項-SQL Server 到格線的結果頁面) |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryResults.SqlServer.SQLResultsToGrid
ms.assetid: f88a0f5c-e800-473b-ae23-c3943de5ed63
author: rothja
ms.author: jroth
ms.openlocfilehash: 3f9cec7e544c295420a9ae2a25e96ea9aa82030b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703238"
---
# <a name="options-query-results-sql-server-results-to-grid-page"></a><span data-ttu-id="e97d1-102"> (查詢結果的選項-SQL Server 到格線的結果頁面) </span><span class="sxs-lookup"><span data-stu-id="e97d1-102">Options (Query Results-SQL Server-Results to Grid Page)</span></span>
  <span data-ttu-id="e97d1-103">使用這個頁面即可指定選項，使查詢結果集以方格的格式顯示。</span><span class="sxs-lookup"><span data-stu-id="e97d1-103">Use this page to specify the options for displaying a query result set in grid format.</span></span> <span data-ttu-id="e97d1-104">這些選項的變更僅適用於新的 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 查詢。</span><span class="sxs-lookup"><span data-stu-id="e97d1-104">Changes to these options are applied only to new [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] queries.</span></span> <span data-ttu-id="e97d1-105">若要變更目前查詢的選項，請按一下 [**查詢**] 功能表上的 [**查詢選項**]，或在查詢視窗中按一下滑鼠右鍵， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 然後選取 [**查詢選項**]。</span><span class="sxs-lookup"><span data-stu-id="e97d1-105">To change the options for the current queries, click **Query Options** on the **Query** menu, or right-click in the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Query window and select **Query Options**.</span></span> <span data-ttu-id="e97d1-106">在 [查詢選項]\*\*\*\* 對話方塊的左窗格中，於 [結果]\*\*\*\* 之下，按一下 [方格]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e97d1-106">In the left pane of the **Query Options** dialog box, under **Results**, click **Grid**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="e97d1-107">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="e97d1-107">UI element list</span></span>  
 <span data-ttu-id="e97d1-108">**在結果集裡包含查詢**</span><span class="sxs-lookup"><span data-stu-id="e97d1-108">**Include the query in the result set**</span></span>  
 <span data-ttu-id="e97d1-109">將查詢的文字傳回作為查詢輸出的一部分。</span><span class="sxs-lookup"><span data-stu-id="e97d1-109">Returns the text of the query as part of the query output.</span></span>  
  
 <span data-ttu-id="e97d1-110">**複製或儲存結果時包含資料行標頭**</span><span class="sxs-lookup"><span data-stu-id="e97d1-110">**Include column headers when copying or saving the results**</span></span>  
 <span data-ttu-id="e97d1-111">將結果複製到剪貼簿或儲存在檔案中時，選取此核取方塊即可包含資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="e97d1-111">Select this check box to include column headers when results are copied to the clipboard, or saved in a file.</span></span> <span data-ttu-id="e97d1-112">如果您想要儲存或複製的結果資料中只有資料，而不要有資料行標頭，請清除這個核取方塊。</span><span class="sxs-lookup"><span data-stu-id="e97d1-112">Clear this check box if you want saved or copied result data to have only the data and not the column headings.</span></span>  
  
 <span data-ttu-id="e97d1-113">**執行之後捨棄結果**</span><span class="sxs-lookup"><span data-stu-id="e97d1-113">**Discard results after execution**</span></span>  
 <span data-ttu-id="e97d1-114">避免查詢結果顯示在檢閱窗格中。</span><span class="sxs-lookup"><span data-stu-id="e97d1-114">Prevents query results from being displayed in the reviewing pane.</span></span> <span data-ttu-id="e97d1-115">執行之後會立即捨棄結果。</span><span class="sxs-lookup"><span data-stu-id="e97d1-115">The results are discarded immediately after execution.</span></span> <span data-ttu-id="e97d1-116">指定這個選項有助於節省記憶體。</span><span class="sxs-lookup"><span data-stu-id="e97d1-116">Specifying this option helps save memory.</span></span>  
  
 <span data-ttu-id="e97d1-117">**在其他索引標籤中顯示結果**</span><span class="sxs-lookup"><span data-stu-id="e97d1-117">**Display results in a separate tab**</span></span>  
 <span data-ttu-id="e97d1-118">核取此核取方塊即可在新的索引標籤中顯示結果集，而不是顯示在查詢文件視窗的底部。</span><span class="sxs-lookup"><span data-stu-id="e97d1-118">Select this check box to display the result set in a new tab, instead of at the bottom of the query document window.</span></span>  
  
 <span data-ttu-id="e97d1-119">**執行查詢後，切換至結果索引標籤**</span><span class="sxs-lookup"><span data-stu-id="e97d1-119">**Switch to results tab after the query executes**</span></span>  
 <span data-ttu-id="e97d1-120">按一下即可在開始執行查詢時，自動將螢幕焦點設定為結果窗格。</span><span class="sxs-lookup"><span data-stu-id="e97d1-120">Click to automatically set the screen focus to the results pane upon execution of a query.</span></span>  
  
 <span data-ttu-id="e97d1-121">**已擷取的最大字元數**</span><span class="sxs-lookup"><span data-stu-id="e97d1-121">**Maximum Characters Retrieved**</span></span>  
 <span data-ttu-id="e97d1-122">**非 XML 資料**：</span><span class="sxs-lookup"><span data-stu-id="e97d1-122">**Non XML data**:</span></span>  
  
 <span data-ttu-id="e97d1-123">輸入從 1 到 65535 的數字，來指定每個資料格中會顯示的最大字元數。</span><span class="sxs-lookup"><span data-stu-id="e97d1-123">Enter a number from 1 through 65535 to specify the maximum number of characters that will be displayed in each cell.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e97d1-124">指定大量字元可能造成結果集內顯示的資料截斷。</span><span class="sxs-lookup"><span data-stu-id="e97d1-124">Specifying a large number of characters may cause data in the result set to appear truncated.</span></span> <span data-ttu-id="e97d1-125">每個資料格中所顯示的最大字元數，會視字型大小而定。</span><span class="sxs-lookup"><span data-stu-id="e97d1-125">The maximum number of characters displayed in each cell is dependent on the font size.</span></span> <span data-ttu-id="e97d1-126">若傳回了大量的結果集，且此方塊中所設定的值較大，就可能會造成 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 的可用記憶體不足而降低系統的效能。</span><span class="sxs-lookup"><span data-stu-id="e97d1-126">When large result sets are returned, a high value in this box can cause [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to run low on memory and hinder system performance.</span></span>  
  
 <span data-ttu-id="e97d1-127">**XML 資料**：</span><span class="sxs-lookup"><span data-stu-id="e97d1-127">**XML data**:</span></span>  
  
 <span data-ttu-id="e97d1-128">選取 [1 MB]\*\*\*\*、[2 MB]\*\*\*\* 或 [5 MB]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e97d1-128">Select **1 MB**, **2 MB**, or **5 MB**.</span></span> <span data-ttu-id="e97d1-129">選取 [無限制]\*\*\*\* 以擷取所有字元。</span><span class="sxs-lookup"><span data-stu-id="e97d1-129">Select **Unlimited** to retrieve all characters.</span></span>  
  
 <span data-ttu-id="e97d1-130">**重設為預設值**</span><span class="sxs-lookup"><span data-stu-id="e97d1-130">**Reset to Default**</span></span>  
 <span data-ttu-id="e97d1-131">將此頁面上的所有值重設為原始預設值。</span><span class="sxs-lookup"><span data-stu-id="e97d1-131">Resets all values on this page to the original default values.</span></span>  
  
  
