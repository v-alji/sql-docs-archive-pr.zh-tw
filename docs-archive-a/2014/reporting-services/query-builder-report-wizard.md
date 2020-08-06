---
title: 查詢產生器 (報表 Wizard) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.dataview.vdtquerydesigner.f1
- sql12.rtp.rptwizard.querybuilder.f1
helpviewer_keywords:
- Query Builder [Reporting Services]
ms.assetid: 1b0904ea-28c1-448e-b56c-c0fdfbc8b222
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 34369bc72fadae75afbc93eb03c0e40509dd27a4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585114"
---
# <a name="query-builder-report-wizard"></a><span data-ttu-id="9cc43-102">查詢產生器 (報表精靈)</span><span class="sxs-lookup"><span data-stu-id="9cc43-102">Query Builder (Report Wizard)</span></span>
  <span data-ttu-id="9cc43-103">使用查詢產生器，即可指定查詢以擷取使用於報表中的結果集。</span><span class="sxs-lookup"><span data-stu-id="9cc43-103">Use the Query Builder to specify a query that retrieves a result set to use in a report.</span></span> <span data-ttu-id="9cc43-104">您可以在兩種查詢產生器之間進行選擇：</span><span class="sxs-lookup"><span data-stu-id="9cc43-104">You can choose between two query builders:</span></span>  
  
-   <span data-ttu-id="9cc43-105">以文字為基礎的查詢產生器 (預設) 會提供簡單的工作空間，讓您指定查詢和檢視結果。</span><span class="sxs-lookup"><span data-stu-id="9cc43-105">The text-based query builder (default) provides a simple workspace for specifying a query and viewing the results.</span></span> <span data-ttu-id="9cc43-106">您可以指定多個 [!INCLUDE[tsql](../includes/tsql-md.md)] 陳述式、自訂資料處理延伸模組的查詢或命令語法，以及指定為運算式的查詢。</span><span class="sxs-lookup"><span data-stu-id="9cc43-106">You can specify multiple [!INCLUDE[tsql](../includes/tsql-md.md)] statements, query or command syntax for custom data processing extensions, and queries that are specified as expressions.</span></span> <span data-ttu-id="9cc43-107">因為一般查詢產生器不會前置處理查詢，而且可以容納各種查詢語法，所以它是報表設計師的預設查詢產生器工具。</span><span class="sxs-lookup"><span data-stu-id="9cc43-107">Because the generic query builder does not preprocess the query and can accommodate any kind of query syntax, it is the default query builder tool for Report Designer.</span></span>  
  
-   <span data-ttu-id="9cc43-108">圖形化查詢產生器可以提供較豐富的視覺體驗。</span><span class="sxs-lookup"><span data-stu-id="9cc43-108">The graphical query builder provides a richer visual experience.</span></span> <span data-ttu-id="9cc43-109">它會用於 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 和 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的其他部分中。</span><span class="sxs-lookup"><span data-stu-id="9cc43-109">It is used in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] and in other parts of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9cc43-110">如果您並未建立運算式或多重部分 SQL 陳述式，則可以使用圖形化查詢產生器。</span><span class="sxs-lookup"><span data-stu-id="9cc43-110">You can use the graphical query builder if you are not creating expressions or multi-part SQL statements.</span></span>  
  
     <span data-ttu-id="9cc43-111">若要切換至圖形化查詢產生器，請切換視窗左上角的 **[當成文字編輯]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="9cc43-111">To switch to the graphical query builder, toggle the **Edit As Text** button in the top left corner of the window.</span></span>  
  
 <span data-ttu-id="9cc43-112">您也可以從其他報表匯入查詢。</span><span class="sxs-lookup"><span data-stu-id="9cc43-112">You can also import a query from another report.</span></span>  
  
## <a name="query-builder-options"></a><span data-ttu-id="9cc43-113">查詢產生器選項</span><span class="sxs-lookup"><span data-stu-id="9cc43-113">Query Builder Options</span></span>  
 <span data-ttu-id="9cc43-114">**當成文字編輯**</span><span class="sxs-lookup"><span data-stu-id="9cc43-114">**Edit As Text**</span></span>  
 <span data-ttu-id="9cc43-115">在以文字為基礎和圖形化查詢設計工具之間切換 (如果這兩種工具都適用於查詢的話)。</span><span class="sxs-lookup"><span data-stu-id="9cc43-115">Toggles between the text-based and graphical query designers, if both will work for the query.</span></span>  
  
 <span data-ttu-id="9cc43-116">**匯入**</span><span class="sxs-lookup"><span data-stu-id="9cc43-116">**Import**</span></span>  
 <span data-ttu-id="9cc43-117">開啟 [匯入查詢]\*\*\*\* 對話方塊，然後顯示任何可用報表的 .rdl 和 .sql 檔。</span><span class="sxs-lookup"><span data-stu-id="9cc43-117">Opens the **Import Query** dialog box and displays .rdl and .sql files for any available report.</span></span> <span data-ttu-id="9cc43-118">您可以依原狀使用匯入的查詢，也可以在查詢產生器中修改此查詢。</span><span class="sxs-lookup"><span data-stu-id="9cc43-118">You can use the imported query as it is, or you can modify it in the query builder.</span></span>  
  
 <span data-ttu-id="9cc43-119">\*\*! (執行) \*\*</span><span class="sxs-lookup"><span data-stu-id="9cc43-119">**! (Run)**</span></span>  
 <span data-ttu-id="9cc43-120">執行查詢，如果查詢有效則傳回結果集。</span><span class="sxs-lookup"><span data-stu-id="9cc43-120">Runs the query and returns a result set if the query is valid.</span></span> <span data-ttu-id="9cc43-121">請注意，如果這是一個運算式，則無法執行查詢。</span><span class="sxs-lookup"><span data-stu-id="9cc43-121">Note that you cannot execute the query if it is an expression.</span></span> <span data-ttu-id="9cc43-122">若要驗證以運算式為基礎的查詢，您必須預覽報表。</span><span class="sxs-lookup"><span data-stu-id="9cc43-122">To verify an expression-based query, you must preview the report.</span></span>  
  
 <span data-ttu-id="9cc43-123">**命令類型**</span><span class="sxs-lookup"><span data-stu-id="9cc43-123">**Command type**</span></span>  
 <span data-ttu-id="9cc43-124">指定文字、預存程序或直接指定資料表。</span><span class="sxs-lookup"><span data-stu-id="9cc43-124">Specifies text, stored procedure, or table direct.</span></span> <span data-ttu-id="9cc43-125">命令類型的可用性會視您指定的資料處理延伸模組而定。</span><span class="sxs-lookup"><span data-stu-id="9cc43-125">Availability of a command type depends on the data processing extension you specified.</span></span>  
  
 <span data-ttu-id="9cc43-126">**查詢窗格**</span><span class="sxs-lookup"><span data-stu-id="9cc43-126">**Query pane**</span></span>  
 <span data-ttu-id="9cc43-127">輸入查詢。</span><span class="sxs-lookup"><span data-stu-id="9cc43-127">Type the query.</span></span>  
  
 <span data-ttu-id="9cc43-128">**結果窗格**</span><span class="sxs-lookup"><span data-stu-id="9cc43-128">**Result pane**</span></span>  
 <span data-ttu-id="9cc43-129">顯示查詢傳回的結果集。</span><span class="sxs-lookup"><span data-stu-id="9cc43-129">Shows the result set returned from the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cc43-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9cc43-130">See Also</span></span>  
 <span data-ttu-id="9cc43-131">[報表內嵌資料集和共用資料集 &#40;報表產生器和 SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9cc43-131">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="9cc43-132">報表精靈說明</span><span class="sxs-lookup"><span data-stu-id="9cc43-132">Report Wizard Help</span></span>](../../2014/reporting-services/report-wizard-help.md)  
  
  
