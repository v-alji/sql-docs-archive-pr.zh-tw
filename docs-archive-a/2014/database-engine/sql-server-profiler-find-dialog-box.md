---
title: SQL Server Profiler-尋找對話方塊 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.find.f1
helpviewer_keywords:
- Find dialog box
ms.assetid: dfaeec04-93d3-4214-9fc1-38b80179b36b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cedf50930c06d211ebcee0c45a249667219f392c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705393"
---
# <a name="sql-server-profiler---find-dialog-box"></a><span data-ttu-id="80030-102">SQL Server Profiler - 尋找對話方塊</span><span class="sxs-lookup"><span data-stu-id="80030-102">SQL Server Profiler - Find Dialog Box</span></span>
  <span data-ttu-id="80030-103">使用 [尋找]\*\*\*\* 對話方塊，即可針對追蹤搜尋特定字元或文字。</span><span class="sxs-lookup"><span data-stu-id="80030-103">Use the **Find** dialog box to search a trace for specific characters or words.</span></span> <span data-ttu-id="80030-104">若要取消進行中的搜尋，請按下 ESC 鍵。</span><span class="sxs-lookup"><span data-stu-id="80030-104">To cancel a search in progress, press ESC.</span></span>  
  
 <span data-ttu-id="80030-105">若要在 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 中開啟此對話方塊，請在 [編輯]\*\*\*\* 功能表上按一下 [尋找]**Find**。</span><span class="sxs-lookup"><span data-stu-id="80030-105">To open this dialog box in [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)], on the **Edit** menu, click **Find**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="80030-106">選項</span><span class="sxs-lookup"><span data-stu-id="80030-106">Options</span></span>  
 <span data-ttu-id="80030-107">**尋找目標**</span><span class="sxs-lookup"><span data-stu-id="80030-107">**Find what**</span></span>  
 <span data-ttu-id="80030-108">輸入您想要搜尋的文字。</span><span class="sxs-lookup"><span data-stu-id="80030-108">Enter the text that you want to search for.</span></span> <span data-ttu-id="80030-109">搜尋會找出其中包含指定字串的字串。</span><span class="sxs-lookup"><span data-stu-id="80030-109">The search matches any string containing the specified string.</span></span> <span data-ttu-id="80030-110">例如，搜尋 "Completed" 會與 "SQL:BatchCompleted" 相符。</span><span class="sxs-lookup"><span data-stu-id="80030-110">For example, searching for "Completed" matches "SQL:BatchCompleted."</span></span> <span data-ttu-id="80030-111">不支援萬用字元 (\*、? 等等)。</span><span class="sxs-lookup"><span data-stu-id="80030-111">Wild card characters (\*, ?, etc.) are not supported.</span></span>  
  
 <span data-ttu-id="80030-112">**在資料行中搜尋**</span><span class="sxs-lookup"><span data-stu-id="80030-112">**Search in column**</span></span>  
 <span data-ttu-id="80030-113">按一下要搜尋的資料行，或按一下 **\<All columns>** 以搜尋追蹤中的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="80030-113">Click a data column to search, or click **\<All columns>** to search all the data columns in the trace.</span></span>  
  
 <span data-ttu-id="80030-114">**大小寫須相符**</span><span class="sxs-lookup"><span data-stu-id="80030-114">**Match case**</span></span>  
 <span data-ttu-id="80030-115">尋找與 [尋找目標]\*\*\*\* 方塊中的大小寫相同的文字。</span><span class="sxs-lookup"><span data-stu-id="80030-115">Finds text that has the same case as the **Find what** box.</span></span> <span data-ttu-id="80030-116">清除此核取方塊，即可在追蹤中同時尋找大寫與小寫文字字元的範例。</span><span class="sxs-lookup"><span data-stu-id="80030-116">Clear this check box to find examples in the trace that are in both uppercase and lowercase text characters.</span></span>  
  
 <span data-ttu-id="80030-117">**全字拼寫須相符**</span><span class="sxs-lookup"><span data-stu-id="80030-117">**Match whole word**</span></span>  
 <span data-ttu-id="80030-118">將搜尋限制為整個文字。</span><span class="sxs-lookup"><span data-stu-id="80030-118">Restricts the search to entire words.</span></span> <span data-ttu-id="80030-119">清除 [全字拼寫須相符]\*\*\*\* 核取方塊來搜尋文字內的所有字元。</span><span class="sxs-lookup"><span data-stu-id="80030-119">Clear the **Match whole word** check box to search for characters within a word.</span></span>  
  
 <span data-ttu-id="80030-120">**找下一個**</span><span class="sxs-lookup"><span data-stu-id="80030-120">**Find Next**</span></span>  
 <span data-ttu-id="80030-121">尋找 [尋找目標]\*\*\*\* 方塊中之字元的下一個範例。</span><span class="sxs-lookup"><span data-stu-id="80030-121">Finds the next example of the characters in the **Find what** box.</span></span>  
  
 <span data-ttu-id="80030-122">**找上一個**</span><span class="sxs-lookup"><span data-stu-id="80030-122">**Find Previous**</span></span>  
 <span data-ttu-id="80030-123">在追蹤中向後搜尋，以尋找 [尋找目標]\*\*\*\* 方塊中之字元的上一個範例。</span><span class="sxs-lookup"><span data-stu-id="80030-123">Searches backwards in the trace, to find the previous example of the characters in the **Find what** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80030-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80030-124">See Also</span></span>  
 <span data-ttu-id="80030-125">[追蹤 &#40;SQL Server Profiler 時，尋找值或資料行&#41;](../tools/sql-server-profiler/find-a-value-or-data-column-while-tracing-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="80030-125">[Find a Value or Data Column While Tracing &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/find-a-value-or-data-column-while-tracing-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="80030-126">[建立追蹤 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="80030-126">[Create a Trace &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="80030-127">[開啟追蹤資料表 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="80030-127">[Open a Trace Table &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="80030-128">[開啟追蹤檔案 &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="80030-128">[Open a Trace File &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) </span></span>  
 <span data-ttu-id="80030-129">[SQL Server Profiler 範本和權限](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="80030-129">[SQL Server Profiler Templates and Permissions](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="80030-130">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="80030-130">SQL Server Profiler</span></span>](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
