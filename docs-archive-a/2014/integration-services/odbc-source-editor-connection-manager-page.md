---
title: ODBC 來源編輯器 (連線管理員頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcsource.connection.f1
ms.assetid: e2c8dc83-6394-4d6c-9232-97e94be72431
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c8b54ce4a1c1b3fea0afb51f1cbf7447971ccab4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703185"
---
# <a name="odbc-source-editor-connection-manager-page"></a><span data-ttu-id="aff8b-102">ODBC 來源編輯器 (連接管理員頁面)</span><span class="sxs-lookup"><span data-stu-id="aff8b-102">ODBC Source Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="aff8b-103">使用 **[ODBC 來源編輯器]** 對話方塊的 **[連接管理員]** 頁面，即可選取來源的 ODBC 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="aff8b-103">Use the **Connection Manager** page of the **ODBC Source Editor** dialog box to select the ODBC connection manager for the source.</span></span> <span data-ttu-id="aff8b-104">這個頁面也可以讓您從資料庫中選取資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="aff8b-104">This page also lets you select a table or view from the database.</span></span>  
  
 <span data-ttu-id="aff8b-105">如需有關 ODBC 來源的詳細資訊，請參閱＜ [ODBC Source](data-flow/odbc-source.md)＞。</span><span class="sxs-lookup"><span data-stu-id="aff8b-105">For more information about the ODBC source, see [ODBC Source](data-flow/odbc-source.md).</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="aff8b-106">工作清單</span><span class="sxs-lookup"><span data-stu-id="aff8b-106">Task List</span></span>  
 <span data-ttu-id="aff8b-107">**若要開啟 ODBC 來源編輯器的連接管理員頁面**</span><span class="sxs-lookup"><span data-stu-id="aff8b-107">**To open the ODBC Source Editor Connection Manager Page**</span></span>  
  
-   <span data-ttu-id="aff8b-108">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，開啟具有 ODBC 來源的 [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="aff8b-108">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] package that has the ODBC source.</span></span>  
  
-   <span data-ttu-id="aff8b-109">在 [資料流程]\*\*\*\* 索引標籤上，按兩下 ODBC 來源。</span><span class="sxs-lookup"><span data-stu-id="aff8b-109">On the **Data Flow** tab, double-click the ODBC source.</span></span>  
  
## <a name="options"></a><span data-ttu-id="aff8b-110">選項。</span><span class="sxs-lookup"><span data-stu-id="aff8b-110">Options</span></span>  
  
### <a name="connection-manager"></a><span data-ttu-id="aff8b-111">[ODBC 來源編輯器]</span><span class="sxs-lookup"><span data-stu-id="aff8b-111">Connection manager</span></span>  
 <span data-ttu-id="aff8b-112">從清單中選取現有的 ODBC 連接管理員，或按一下 [**新增**] 以建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="aff8b-112">Select an existing ODBC connection manager from the list, or click **New** to create a new connection.</span></span> <span data-ttu-id="aff8b-113">此連接可以指向任何 ODBC 支援的資料庫。</span><span class="sxs-lookup"><span data-stu-id="aff8b-113">The connection can be to any ODBC-supported database.</span></span>  
  
### <a name="new"></a><span data-ttu-id="aff8b-114">新增</span><span class="sxs-lookup"><span data-stu-id="aff8b-114">New</span></span>  
 <span data-ttu-id="aff8b-115">按一下 **[新增]** 。</span><span class="sxs-lookup"><span data-stu-id="aff8b-115">Click **New**.</span></span> <span data-ttu-id="aff8b-116">**[設定 ODBC 連接管理員編輯器]** 對話方塊隨即開啟，讓您能夠建立新的 ODBC 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="aff8b-116">The **Configure ODBC Connection Manager Editor** dialog box opens where you can create a new ODBC connection manager.</span></span>  
  
### <a name="data-access-mode"></a><span data-ttu-id="aff8b-117">資料存取模式</span><span class="sxs-lookup"><span data-stu-id="aff8b-117">Data Access Mode</span></span>  
 <span data-ttu-id="aff8b-118">選取從來源中選取資料的方法。</span><span class="sxs-lookup"><span data-stu-id="aff8b-118">Select the method for selecting data from the source.</span></span> <span data-ttu-id="aff8b-119">下表將顯示這些選項：</span><span class="sxs-lookup"><span data-stu-id="aff8b-119">The options are shown in the following table:</span></span>  
  
|<span data-ttu-id="aff8b-120">選項</span><span class="sxs-lookup"><span data-stu-id="aff8b-120">Option</span></span>|<span data-ttu-id="aff8b-121">描述</span><span class="sxs-lookup"><span data-stu-id="aff8b-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="aff8b-122">資料表名稱</span><span class="sxs-lookup"><span data-stu-id="aff8b-122">Table Name</span></span>|<span data-ttu-id="aff8b-123">從 ODBC 資料來源中的資料表或檢視表擷取資料。</span><span class="sxs-lookup"><span data-stu-id="aff8b-123">Retrieve data from a table or view in the ODBC data source.</span></span> <span data-ttu-id="aff8b-124">當您選取此選項時，請從清單中選取下列項目的值：</span><span class="sxs-lookup"><span data-stu-id="aff8b-124">When you select this option, select a value from the list for the following:</span></span>|  
||<span data-ttu-id="aff8b-125">**資料表或檢視表的名稱**：從清單中選取可用的資料表或檢視表，或是輸入可識別資料表的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="aff8b-125">**Name of the table or the view**: Select an available table or view from the list or type a regular expression to identify the table.</span></span>|  
||<span data-ttu-id="aff8b-126">此清單只包含前 1000 個資料表。</span><span class="sxs-lookup"><span data-stu-id="aff8b-126">This list contains the first 1000 tables only.</span></span> <span data-ttu-id="aff8b-127">如果您的資料庫包含超過 1000 個資料表，您可以輸入資料表名稱的開頭或使用 (\*) 萬用字元來輸入名稱的任何部分，以便顯示您想要使用的資料表。</span><span class="sxs-lookup"><span data-stu-id="aff8b-127">If your database contains more than 1000 tables, you can type the beginning of a table name or use the (\*) wild card to enter any part of the name to display the table or tables you want to use.</span></span>|  
|<span data-ttu-id="aff8b-128">SQL (命令)</span><span class="sxs-lookup"><span data-stu-id="aff8b-128">SQL command</span></span>|<span data-ttu-id="aff8b-129">使用 SQL 查詢從 ODBC 資料來源中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="aff8b-129">Retrieve data from the ODBC data source by using an SQL query.</span></span> <span data-ttu-id="aff8b-130">您應該以目前所使用之來源資料庫的語法撰寫查詢。</span><span class="sxs-lookup"><span data-stu-id="aff8b-130">You should write the query in the syntax of the source database you are working with.</span></span> <span data-ttu-id="aff8b-131">當您選取此選項時，請用下列其中一種方式輸入查詢：</span><span class="sxs-lookup"><span data-stu-id="aff8b-131">When you select this option, enter a query in one of the following ways:</span></span>|  
||<span data-ttu-id="aff8b-132">在 **[SQL 命令文字]** 欄位中輸入 SQL 查詢的文字。</span><span class="sxs-lookup"><span data-stu-id="aff8b-132">Enter the text of the SQL query in the **SQL command text** field.</span></span>|  
||<span data-ttu-id="aff8b-133">按一下 **[瀏覽]** ，從文字檔載入 SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="aff8b-133">Click **Browse** to load the SQL query from a text file.</span></span>|  
||<span data-ttu-id="aff8b-134">按一下 **[剖析查詢]** 驗證查詢文字的語法。</span><span class="sxs-lookup"><span data-stu-id="aff8b-134">Click **Parse query** to verify the syntax of the query text.</span></span>|  
  
### <a name="preview"></a><span data-ttu-id="aff8b-135">預覽</span><span class="sxs-lookup"><span data-stu-id="aff8b-135">Preview</span></span>  
 <span data-ttu-id="aff8b-136">按一下 **[預覽]** ，最多可檢視從所選取之資料表或檢視表中擷取的前 200 個資料列。</span><span class="sxs-lookup"><span data-stu-id="aff8b-136">Click **Preview** to view up to the first 200 rows of the data extracted from the table or view you selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aff8b-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aff8b-137">See Also</span></span>  
 <span data-ttu-id="aff8b-138">[ODBC 來源自訂屬性](data-flow/odbc-source-custom-properties.md) </span><span class="sxs-lookup"><span data-stu-id="aff8b-138">[ODBC Source Custom Properties](data-flow/odbc-source-custom-properties.md) </span></span>  
 <span data-ttu-id="aff8b-139">[ODBC 來源編輯器 &#40;資料行] 頁面&#41;](../../2014/integration-services/odbc-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="aff8b-139">[ODBC Source Editor &#40;Columns Page&#41;](../../2014/integration-services/odbc-source-editor-columns-page.md) </span></span>  
 [<span data-ttu-id="aff8b-140">ODBC 來源編輯器 &#40;錯誤輸出頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="aff8b-140">ODBC Source Editor &#40;Error Output Page&#41;</span></span>](../../2014/integration-services/odbc-source-editor-error-output-page.md)  
  
  
