---
title: " (查詢執行的選項-SQL Server-一般頁面) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryExecution.SqlServer.SqlExecutionGeneral
ms.assetid: 3f8d59bc-3f97-4e5d-8b86-5ac670d20780
author: rothja
ms.author: jroth
ms.openlocfilehash: eaa95293636d02674fb720dcd1b8146279f78e72
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599644"
---
# <a name="options-query-execution-sql-server-general-page"></a><span data-ttu-id="38d82-102"> (查詢執行的選項-SQL Server-一般頁面) </span><span class="sxs-lookup"><span data-stu-id="38d82-102">Options (Query Execution-SQL Server-General Page)</span></span>
  <span data-ttu-id="38d82-103">使用此頁面可指定執行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 查詢的選項。</span><span class="sxs-lookup"><span data-stu-id="38d82-103">Use this page to specify the options for running [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] queries.</span></span> <span data-ttu-id="38d82-104">這些選項的變更僅適用於新的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 查詢。</span><span class="sxs-lookup"><span data-stu-id="38d82-104">Changes to these options are only applied to new [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] queries.</span></span> <span data-ttu-id="38d82-105">若要變更目前查詢的選項，請按一下 [查詢]\*\*\*\* 功能表上的 [查詢選項]\*\*\*\*，或在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 查詢視窗中按一下滑鼠右鍵，並選取 [查詢選項]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="38d82-105">To change the options for a current query, click **Query Options** on the **Query** menu, or in a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Query window right-click and select **Query Options**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="38d82-106">選項</span><span class="sxs-lookup"><span data-stu-id="38d82-106">Options</span></span>  
 <span data-ttu-id="38d82-107">**SET ROWCOUNT**</span><span class="sxs-lookup"><span data-stu-id="38d82-107">**SET ROWCOUNT**</span></span>  
 <span data-ttu-id="38d82-108">預設值 0 指出 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 將等候結果，直到所有結果都收到為止。</span><span class="sxs-lookup"><span data-stu-id="38d82-108">The default value of 0 indicates that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] will wait for results until all results are received.</span></span> <span data-ttu-id="38d82-109">如果您要 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 在取得指定的資料列數後停止查詢，請提供大於 0 的值。</span><span class="sxs-lookup"><span data-stu-id="38d82-109">Provide a value greater than 0 if you want [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to halt the query after obtaining the specified number of rows.</span></span> <span data-ttu-id="38d82-110">若要關閉此選項 (以便傳回所有資料列)，請指定 SET ROWCOUNT 0。</span><span class="sxs-lookup"><span data-stu-id="38d82-110">To turn this option off (so that all rows are returned), specify SET ROWCOUNT 0.</span></span>  
  
 <span data-ttu-id="38d82-111">**SET TEXTSIZE**</span><span class="sxs-lookup"><span data-stu-id="38d82-111">**SET TEXTSIZE**</span></span>  
 <span data-ttu-id="38d82-112">2,147,483,647 個位元組的預設值，指出 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 將提供完整的資料欄位，直到 `text` 和 `ntext` 資料欄位的上限。</span><span class="sxs-lookup"><span data-stu-id="38d82-112">The default value of 2,147,483,647 bytes indicates that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] will provide complete data fields up to the limit of `text` and `ntext` data fields.</span></span> <span data-ttu-id="38d82-113">提供較小的數值，即可在有大量數值時，限制傳回的結果數量。</span><span class="sxs-lookup"><span data-stu-id="38d82-113">Provide a smaller number to limit results in the case of large values.</span></span> <span data-ttu-id="38d82-114">資料行若大於提供的數值，就會被截斷。</span><span class="sxs-lookup"><span data-stu-id="38d82-114">Columns greater than the number provided will be truncated.</span></span>  
  
 <span data-ttu-id="38d82-115">**執行逾時**</span><span class="sxs-lookup"><span data-stu-id="38d82-115">**Execution time-out**</span></span>  
 <span data-ttu-id="38d82-116">在 **[新增連接]** 對話方塊中設定預設值。</span><span class="sxs-lookup"><span data-stu-id="38d82-116">Sets the default value in the **New Connection** dialog box.</span></span> <span data-ttu-id="38d82-117">使用此微調方塊，指出 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 取消查詢之前要等候的秒數。</span><span class="sxs-lookup"><span data-stu-id="38d82-117">Use this spin box to tell [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] the number of seconds to wait before canceling the query.</span></span> <span data-ttu-id="38d82-118">值為0表示無限期等候，或沒有超時。新安裝上的此值為0。</span><span class="sxs-lookup"><span data-stu-id="38d82-118">A value of 0 indicates an infinite wait, or no time-out. This value is 0 on a new installation.</span></span>  
  
 <span data-ttu-id="38d82-119">**批次分隔符號**</span><span class="sxs-lookup"><span data-stu-id="38d82-119">**Batch separator**</span></span>  
 <span data-ttu-id="38d82-120">輸入用來將 [!INCLUDE[tsql](../includes/tsql-md.md)] 陳述式分隔成批次的文字。</span><span class="sxs-lookup"><span data-stu-id="38d82-120">Type a word that you use to separate [!INCLUDE[tsql](../includes/tsql-md.md)] statements into batches.</span></span> <span data-ttu-id="38d82-121">預設為 GO。</span><span class="sxs-lookup"><span data-stu-id="38d82-121">The default is GO.</span></span>  
  
 <span data-ttu-id="38d82-122">**預設會以 SQLCMD 模式開啟新查詢**</span><span class="sxs-lookup"><span data-stu-id="38d82-122">**By default, open new queries in SQLCMD Mode**</span></span>  
 <span data-ttu-id="38d82-123">選取此核取方塊，即可以 SQLCMD 模式開啟新查詢。</span><span class="sxs-lookup"><span data-stu-id="38d82-123">Select this check box to open new queries in SQLCMD mode.</span></span> <span data-ttu-id="38d82-124">如需 SQLCMD 模式的詳細資訊，請參閱[使用查詢編輯器編輯 SQLCMD 指令碼](../relational-databases/scripting/edit-sqlcmd-scripts-with-query-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="38d82-124">For more information about SQLCMD mode, see [Edit SQLCMD Scripts with Query Editor](../relational-databases/scripting/edit-sqlcmd-scripts-with-query-editor.md).</span></span>  
  
 <span data-ttu-id="38d82-125">當您選取此選項時，請注意以下限制：</span><span class="sxs-lookup"><span data-stu-id="38d82-125">When you select this option, be aware of the following limitations:</span></span>  
  
-   <span data-ttu-id="38d82-126">[!INCLUDE[ssDE](../includes/ssde-md.md)] 查詢編輯器中的 IntelliSense 會關閉。</span><span class="sxs-lookup"><span data-stu-id="38d82-126">IntelliSense in the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor is turned off.</span></span>  
  
-   <span data-ttu-id="38d82-127">由於查詢編輯器不會從命令列執行，所以您無法傳入命令列參數 (如變數)。</span><span class="sxs-lookup"><span data-stu-id="38d82-127">Because Query Editor does not run from the command line, you cannot pass in command-line parameters such as variables.</span></span>  
  
-   <span data-ttu-id="38d82-128">由於查詢編輯器無法回應作業系統提示，所以您必須非常小心，不要執行互動式陳述式。</span><span class="sxs-lookup"><span data-stu-id="38d82-128">Because Query Editor cannot respond to operating-system prompts, you must be careful not to run interactive statements.</span></span>  
  
 <span data-ttu-id="38d82-129">**重設為預設值**</span><span class="sxs-lookup"><span data-stu-id="38d82-129">**Reset to Default**</span></span>  
 <span data-ttu-id="38d82-130">按一下即可將此頁面上的所有值重設為原始預設值。</span><span class="sxs-lookup"><span data-stu-id="38d82-130">Click to reset all values on this page to the original default values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38d82-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38d82-131">See Also</span></span>  
 [<span data-ttu-id="38d82-132">sqlcmd 公用程式</span><span class="sxs-lookup"><span data-stu-id="38d82-132">sqlcmd Utility</span></span>](../tools/sqlcmd-utility.md)  
  
  
