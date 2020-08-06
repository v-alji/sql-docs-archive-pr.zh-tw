---
title: 查詢選項執行 (一般頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.general.f1
ms.assetid: 858a0263-2f04-4692-b8bf-63e93c998ead
author: rothja
ms.author: jroth
ms.openlocfilehash: ce3848b51b81f111333ba0e9ac12c96432dd9863
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599170"
---
# <a name="query-options-execution-general-page"></a><span data-ttu-id="b9eff-102">查詢選項執行 (一般頁面)</span><span class="sxs-lookup"><span data-stu-id="b9eff-102">Query Options Execution (General Page)</span></span>
  <span data-ttu-id="b9eff-103">使用此頁面可指定執行 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 查詢的選項。</span><span class="sxs-lookup"><span data-stu-id="b9eff-103">Use this page to specify the options for running [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] queries.</span></span> <span data-ttu-id="b9eff-104">若要存取此對話方塊，請以滑鼠右鍵按一下查詢編輯器視窗的主體，然後按一下 [查詢選項]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b9eff-104">To access this dialog box, right-click the body of a Query Editor window, and then click **Query Options**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="b9eff-105">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="b9eff-105">UI element list</span></span>  
 <span data-ttu-id="b9eff-106">**SET ROWCOUNT**</span><span class="sxs-lookup"><span data-stu-id="b9eff-106">**SET ROWCOUNT**</span></span>  
 <span data-ttu-id="b9eff-107">預設值 0 指出 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 將等候結果，直到所有結果都收到為止。</span><span class="sxs-lookup"><span data-stu-id="b9eff-107">The default value of 0 indicates that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] will wait for results until all results are received.</span></span> <span data-ttu-id="b9eff-108">如果您要 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 在取得指定的資料列數後停止查詢，請提供大於 0 的值。</span><span class="sxs-lookup"><span data-stu-id="b9eff-108">Provide a value greater than 0 if you want [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to halt the query after obtaining the specified number of rows.</span></span> <span data-ttu-id="b9eff-109">若要關閉此選項 (以便傳回所有資料列)，請指定 SET ROWCOUNT 0。</span><span class="sxs-lookup"><span data-stu-id="b9eff-109">To turn this option off (so that all rows are returned), specify SET ROWCOUNT 0.</span></span>  
  
 <span data-ttu-id="b9eff-110">**SET TEXTSIZE**</span><span class="sxs-lookup"><span data-stu-id="b9eff-110">**SET TEXTSIZE**</span></span>  
 <span data-ttu-id="b9eff-111">2,147,483,647 個位元組的預設值表示 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 將提供完整的資料欄位，直到 `text`、`ntext`、`nvarchar(max)` 及 `varchar(max)` 資料欄位的上限。</span><span class="sxs-lookup"><span data-stu-id="b9eff-111">The default value of 2,147,483,647 bytes indicates that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] will provide a complete data field up to the limit of `text`, `ntext`, `nvarchar(max)`, and `varchar(max)` data fields.</span></span> <span data-ttu-id="b9eff-112">這不會影響 XML 資料類型。</span><span class="sxs-lookup"><span data-stu-id="b9eff-112">It does not affect the XML data type.</span></span> <span data-ttu-id="b9eff-113">提供較小的數值，即可在有大量數值時，限制傳回的結果數量。</span><span class="sxs-lookup"><span data-stu-id="b9eff-113">Provide a smaller number to limit results in the case of large values.</span></span> <span data-ttu-id="b9eff-114">資料行若大於提供的數值，就會被截斷。</span><span class="sxs-lookup"><span data-stu-id="b9eff-114">Columns greater than the number provided will be truncated.</span></span>  
  
 <span data-ttu-id="b9eff-115">**執行逾時**</span><span class="sxs-lookup"><span data-stu-id="b9eff-115">**Execution time-out**</span></span>  
 <span data-ttu-id="b9eff-116">指出取消查詢之前要等候的秒數。</span><span class="sxs-lookup"><span data-stu-id="b9eff-116">Indicates the number of seconds to wait before canceling the query.</span></span> <span data-ttu-id="b9eff-117">值為 0 表示無盡的等候，或沒有逾時。</span><span class="sxs-lookup"><span data-stu-id="b9eff-117">A value of 0 indicates an infinite wait, or no time-out.</span></span>  
  
 <span data-ttu-id="b9eff-118">**批次分隔符號**</span><span class="sxs-lookup"><span data-stu-id="b9eff-118">**Batch separator**</span></span>  
 <span data-ttu-id="b9eff-119">鍵入您用來將 Transact-SQL 陳述式分隔成批次的文字。</span><span class="sxs-lookup"><span data-stu-id="b9eff-119">Type a word that you use to separate Transact-SQL statements into batches.</span></span> <span data-ttu-id="b9eff-120">預設為 GO。</span><span class="sxs-lookup"><span data-stu-id="b9eff-120">The default is GO.</span></span>  
  
 <span data-ttu-id="b9eff-121">**預設會以 SQLCMD 模式開啟新查詢**</span><span class="sxs-lookup"><span data-stu-id="b9eff-121">**By default, open new queries in SQLCMD Mode**</span></span>  
 <span data-ttu-id="b9eff-122">選取此核取方塊，即可以 SQLCMD 模式開啟新查詢。</span><span class="sxs-lookup"><span data-stu-id="b9eff-122">Select this check box to open new queries in SQLCMD mode.</span></span> <span data-ttu-id="b9eff-123">只有在透過 [**工具**] 功能表開啟對話方塊時，才會顯示此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="b9eff-123">This check box is visible only when the dialog box is opened through the **Tools** menu.</span></span>  
  
 <span data-ttu-id="b9eff-124">當您選取此選項時，請注意以下限制：</span><span class="sxs-lookup"><span data-stu-id="b9eff-124">When you select this option, be aware of the following limitations:</span></span>  
  
-   <span data-ttu-id="b9eff-125">[!INCLUDE[ssDE](../includes/ssde-md.md)] 查詢編輯器中的 IntelliSense 會關閉。</span><span class="sxs-lookup"><span data-stu-id="b9eff-125">IntelliSense in the [!INCLUDE[ssDE](../includes/ssde-md.md)] Query Editor is turned off.</span></span>  
  
-   <span data-ttu-id="b9eff-126">由於查詢編輯器不會從命令列執行，所以您無法傳入命令列參數 (如變數)。</span><span class="sxs-lookup"><span data-stu-id="b9eff-126">Because Query Editor does not run from the command line, you cannot pass in command-line parameters such as variables.</span></span>  
  
-   <span data-ttu-id="b9eff-127">由於查詢編輯器無法回應作業系統提示，所以您必須非常小心，不要執行互動式陳述式。</span><span class="sxs-lookup"><span data-stu-id="b9eff-127">Because Query Editor cannot respond to operating-system prompts, you must be careful not to run interactive statements.</span></span>  
  
 <span data-ttu-id="b9eff-128">**重設為預設值**</span><span class="sxs-lookup"><span data-stu-id="b9eff-128">**Reset to Default**</span></span>  
 <span data-ttu-id="b9eff-129">將此頁面上的所有值重設為原始預設值。</span><span class="sxs-lookup"><span data-stu-id="b9eff-129">Resets all values on this page to the original default values.</span></span>  
  
  
