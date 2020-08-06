---
title: 查詢選項結果 (格線頁) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.grid.f1
ms.assetid: 764bf435-3aab-4c62-b4e0-64fe020a5a95
author: rothja
ms.author: jroth
ms.openlocfilehash: bf300dd5071128b0259230ae788a27595bd8d29e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599165"
---
# <a name="query-options-results-grid-page"></a><span data-ttu-id="395f0-102">查詢選項結果 (方格頁面)</span><span class="sxs-lookup"><span data-stu-id="395f0-102">Query Options Results (Grid Page)</span></span>
  <span data-ttu-id="395f0-103">使用這個頁面即可指定選項，使查詢結果集以方格的格式顯示。</span><span class="sxs-lookup"><span data-stu-id="395f0-103">Use this page to specify the options for displaying a query result set in grid format.</span></span>  
  
## <a name="options"></a><span data-ttu-id="395f0-104">選項</span><span class="sxs-lookup"><span data-stu-id="395f0-104">Options</span></span>  
 <span data-ttu-id="395f0-105">**在結果集裡包含查詢**</span><span class="sxs-lookup"><span data-stu-id="395f0-105">**Include the query in the result set**</span></span>  
 <span data-ttu-id="395f0-106">將查詢的文字當成結果集的一部分傳回。</span><span class="sxs-lookup"><span data-stu-id="395f0-106">Returns the text of the query as part of the result set.</span></span>  
  
 <span data-ttu-id="395f0-107">**複製或儲存結果時包含資料行標頭**</span><span class="sxs-lookup"><span data-stu-id="395f0-107">**Include column headers when copying or saving the results**</span></span>  
 <span data-ttu-id="395f0-108">將結果複製到剪貼簿或儲存在檔案中時，請包含資料行標頭 (標題)。</span><span class="sxs-lookup"><span data-stu-id="395f0-108">Include column headers (titles) when results are copied to the clipboard, or saved in a file.</span></span> <span data-ttu-id="395f0-109">如果您不想將結果資料儲存或複製為只有資料而沒有資料行標題，請清除此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="395f0-109">Clear this check box if you do not want saved or copied result data to have only the data, and not the column headings.</span></span>  
  
 <span data-ttu-id="395f0-110">**執行之後捨棄結果**</span><span class="sxs-lookup"><span data-stu-id="395f0-110">**Discard results after execution**</span></span>  
 <span data-ttu-id="395f0-111">在螢幕顯示已收到查詢結果後，將查詢結果捨棄以釋放記憶體。</span><span class="sxs-lookup"><span data-stu-id="395f0-111">Free memory by discarding the query results after the screen display has received them.</span></span>  
  
 <span data-ttu-id="395f0-112">**在其他索引標籤中顯示結果**</span><span class="sxs-lookup"><span data-stu-id="395f0-112">**Display results in a separate tab**</span></span>  
 <span data-ttu-id="395f0-113">在新的文件視窗中顯示結果集，而非在查詢文件視窗的下方顯示。</span><span class="sxs-lookup"><span data-stu-id="395f0-113">Display the result set in a new document window, instead of at the bottom of the query document window.</span></span>  
  
 <span data-ttu-id="395f0-114">**執行查詢後，切換至結果索引標籤**</span><span class="sxs-lookup"><span data-stu-id="395f0-114">**Switch to results tab after the query executes**</span></span>  
 <span data-ttu-id="395f0-115">自動將螢幕焦點設定為結果集。</span><span class="sxs-lookup"><span data-stu-id="395f0-115">Automatically set the screen focus to the result set.</span></span>  
  
 <span data-ttu-id="395f0-116">**已擷取的最大字元數**</span><span class="sxs-lookup"><span data-stu-id="395f0-116">**Maximum Characters Retrieved**</span></span>  
 <span data-ttu-id="395f0-117">**非 XML 資料**：</span><span class="sxs-lookup"><span data-stu-id="395f0-117">**Non XML data**:</span></span>  
  
 <span data-ttu-id="395f0-118">輸入從 1 到 65535 的數字，來指定每個資料格中會顯示的最大字元數。</span><span class="sxs-lookup"><span data-stu-id="395f0-118">Enter a number from 1 through 65535 to specify the maximum number of characters that will be displayed in each cell.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="395f0-119">指定大量字元可能造成結果集內顯示的資料截斷。</span><span class="sxs-lookup"><span data-stu-id="395f0-119">Specifying a large number of characters may cause data in the result set to appear truncated.</span></span> <span data-ttu-id="395f0-120">每個資料格中所顯示的最大字元數，會視字型大小而定。</span><span class="sxs-lookup"><span data-stu-id="395f0-120">The maximum number of characters displayed in each cell is dependent on the font size.</span></span> <span data-ttu-id="395f0-121">若傳回了大量的結果集，且此方塊中所設定的值較大，就可能會造成 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 的可用記憶體不足而降低系統的效能。</span><span class="sxs-lookup"><span data-stu-id="395f0-121">When large result sets are returned, a high value in this box can cause [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to run low on memory and hinder system performance.</span></span>  
  
 <span data-ttu-id="395f0-122">**XML 資料**：</span><span class="sxs-lookup"><span data-stu-id="395f0-122">**XML data**:</span></span>  
  
 <span data-ttu-id="395f0-123">選取 [1 MB]\*\*\*\*、[2 MB]\*\*\*\* 或 [5 MB]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="395f0-123">Select **1 MB**, **2 MB**, or **5 MB**.</span></span> <span data-ttu-id="395f0-124">選取 [無限制]\*\*\*\* 以擷取所有字元。</span><span class="sxs-lookup"><span data-stu-id="395f0-124">Select **Unlimited** to retrieve all characters.</span></span>  
  
 <span data-ttu-id="395f0-125">**重設為預設值**</span><span class="sxs-lookup"><span data-stu-id="395f0-125">**Reset to Default**</span></span>  
 <span data-ttu-id="395f0-126">將此頁面上的所有值重設為原始預設值。</span><span class="sxs-lookup"><span data-stu-id="395f0-126">Resets all values on this page to the original default values.</span></span>  
  
  
