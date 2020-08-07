---
title: ODBC 目的地編輯器 (連線管理員頁面) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcdest.connection.f1
ms.assetid: f6d9c6c2-e4c4-468b-9e0d-af7b9609614d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6e4fc1073bb187c0864d2991459a358a7f81d066
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703197"
---
# <a name="odbc-destination-editor-connection-manager-page"></a><span data-ttu-id="1a6e5-102">ODBC 目的地編輯器 (連接管理員頁面)</span><span class="sxs-lookup"><span data-stu-id="1a6e5-102">ODBC Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="1a6e5-103">使用 **[ODBC 目的地編輯器]** 對話方塊的 **[連接管理員]** 頁面，即可選取目的地的 ODBC 連接管理員。</span><span class="sxs-lookup"><span data-stu-id="1a6e5-103">Use the **Connection Manager** page of the **ODBC Destination Editor** dialog box to select the ODBC connection manager for the destination.</span></span> <span data-ttu-id="1a6e5-104">這個頁面也可以讓您從資料庫中選取資料表或檢視表。</span><span class="sxs-lookup"><span data-stu-id="1a6e5-104">This page also lets you select a table or view from the database</span></span>  
  
 <span data-ttu-id="1a6e5-105">如需有關 ODBC 目的地的詳細資訊，請參閱＜ [ODBC Destination](data-flow/odbc-destination.md)＞。</span><span class="sxs-lookup"><span data-stu-id="1a6e5-105">For more information about the ODBC destination, see [ODBC Destination](data-flow/odbc-destination.md).</span></span>  
  
 <span data-ttu-id="1a6e5-106">**若要開啟 ODBC 目的地編輯器的連接管理員頁面**</span><span class="sxs-lookup"><span data-stu-id="1a6e5-106">**To open the ODBC Destination Editor Connection Manager Page**</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="1a6e5-107">工作清單</span><span class="sxs-lookup"><span data-stu-id="1a6e5-107">Task List</span></span>  
  
-   <span data-ttu-id="1a6e5-108">在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]中，開啟具有 ODBC 目的地的 [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="1a6e5-108">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], open the [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] package that has the ODBC destination.</span></span>  
  
-   <span data-ttu-id="1a6e5-109">在 [資料流程]  索引標籤中，按兩下 ODBC 目的地。</span><span class="sxs-lookup"><span data-stu-id="1a6e5-109">On the **Data Flow** tab, double-click the ODBC destination.</span></span>  
  
-   <span data-ttu-id="1a6e5-110">在 **[ODBC 目的地編輯器]** 中，按一下 **[連接管理員]** 。</span><span class="sxs-lookup"><span data-stu-id="1a6e5-110">In the **ODBC Destination Editor**, click **Connection Manager**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1a6e5-111">選項。</span><span class="sxs-lookup"><span data-stu-id="1a6e5-111">Options</span></span>  
  
### <a name="connection-manager"></a><span data-ttu-id="1a6e5-112">[ODBC 來源編輯器]</span><span class="sxs-lookup"><span data-stu-id="1a6e5-112">Connection manager</span></span>  
 <span data-ttu-id="1a6e5-113">從清單中選取現有的 ODBC 連接管理員，或按一下 [新增] 建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="1a6e5-113">Select an existing ODBC connection manager from the list, or click New to create a new connection.</span></span> <span data-ttu-id="1a6e5-114">此連接可以指向任何 ODBC 支援的資料庫。</span><span class="sxs-lookup"><span data-stu-id="1a6e5-114">The connection can be to any ODBC-supported database.</span></span>  
  
### <a name="new"></a><span data-ttu-id="1a6e5-115">新增</span><span class="sxs-lookup"><span data-stu-id="1a6e5-115">New</span></span>  
 <span data-ttu-id="1a6e5-116">按一下 **[新增]** 。</span><span class="sxs-lookup"><span data-stu-id="1a6e5-116">Click **New**.</span></span> <span data-ttu-id="1a6e5-117">**[設定 ODBC 連接管理員編輯器]** 對話方塊隨即開啟，讓您能夠建立新的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="1a6e5-117">The **Configure ODBC Connection Manager Editor** dialog box opens where you can create a new connection manager.</span></span>  
  
### <a name="data-access-mode"></a><span data-ttu-id="1a6e5-118">資料存取模式</span><span class="sxs-lookup"><span data-stu-id="1a6e5-118">Data Access Mode</span></span>  
 <span data-ttu-id="1a6e5-119">選取將資料載入目的地的方法。</span><span class="sxs-lookup"><span data-stu-id="1a6e5-119">Select the method for loading data to the destination.</span></span> <span data-ttu-id="1a6e5-120">下表將顯示這些選項：</span><span class="sxs-lookup"><span data-stu-id="1a6e5-120">The options are shown in the following table:</span></span>  
  
|<span data-ttu-id="1a6e5-121">選項</span><span class="sxs-lookup"><span data-stu-id="1a6e5-121">Option</span></span>|<span data-ttu-id="1a6e5-122">描述</span><span class="sxs-lookup"><span data-stu-id="1a6e5-122">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="1a6e5-123">資料表名稱 - 批次</span><span class="sxs-lookup"><span data-stu-id="1a6e5-123">Table Name - Batch</span></span>|<span data-ttu-id="1a6e5-124">若要將 ODBC 目的地設定成以批次模式運作，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="1a6e5-124">Select this option to configure the ODBC destination to work in batch mode.</span></span> <span data-ttu-id="1a6e5-125">當您選取此選項時，可以使用下列選項：</span><span class="sxs-lookup"><span data-stu-id="1a6e5-125">When you select this option the following options are available:</span></span>|  
||<span data-ttu-id="1a6e5-126">**資料表或檢視的名稱**：從清單中選取可用的資料表或檢視表。</span><span class="sxs-lookup"><span data-stu-id="1a6e5-126">**Name of the table or the view**: Select an available table or view from the list.</span></span><br /><br /> <span data-ttu-id="1a6e5-127">此清單只包含前 1000 個資料表。</span><span class="sxs-lookup"><span data-stu-id="1a6e5-127">This list contains the first 1000 tables only.</span></span> <span data-ttu-id="1a6e5-128">如果您的資料庫包含超過 1000 個資料表，您可以輸入資料表名稱的開頭或使用 (\*) 萬用字元來輸入名稱的任何部分，以便顯示您想要使用的資料表。</span><span class="sxs-lookup"><span data-stu-id="1a6e5-128">If your database contains more than 1000 tables, you can type the beginning of a table name or use the (\*) wild card to enter any part of the name to display the table or tables you want to use.</span></span><br /><br /> <span data-ttu-id="1a6e5-129">**批次大小**：輸入大量載入的批次大小。</span><span class="sxs-lookup"><span data-stu-id="1a6e5-129">**Batch size**: Type the size of the batch for bulk loading.</span></span> <span data-ttu-id="1a6e5-130">這是當做批次載入的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="1a6e5-130">This is the number of rows loaded as a batch</span></span>|  
|<span data-ttu-id="1a6e5-131">資料表名稱 - 逐列</span><span class="sxs-lookup"><span data-stu-id="1a6e5-131">Table Name - Row by Row</span></span>|<span data-ttu-id="1a6e5-132">若要將 ODBC 目的地設定成插入每個資料列至目的地資料表 (一次一個)，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="1a6e5-132">Select this option to configure the ODBC destination to insert each of the rows into the destination table one at a time.</span></span> <span data-ttu-id="1a6e5-133">當您選取此選項時，可以使用下列選項：</span><span class="sxs-lookup"><span data-stu-id="1a6e5-133">When you select this option the following option is available:</span></span>|  
||<span data-ttu-id="1a6e5-134">**資料表或檢視的名稱**：從清單的資料庫中選取可用的資料表或檢視表。</span><span class="sxs-lookup"><span data-stu-id="1a6e5-134">**Name of the table or the view**: Select an available table or view from the database from the list.</span></span><br /><br /> <span data-ttu-id="1a6e5-135">此清單只包含前 1000 個資料表。</span><span class="sxs-lookup"><span data-stu-id="1a6e5-135">This list contains the first 1000 tables only.</span></span> <span data-ttu-id="1a6e5-136">如果您的資料庫包含超過 1000 個資料表，您可以輸入資料表名稱的開頭或使用 (\*) 萬用字元來輸入名稱的任何部分，以便顯示您想要使用的資料表。</span><span class="sxs-lookup"><span data-stu-id="1a6e5-136">If your database contains more than 1000 tables, you can type the beginning of a table name or use the (\*) wild card to enter any part of the name to display the table or tables you want to use.</span></span>|  
  
### <a name="preview"></a><span data-ttu-id="1a6e5-137">預覽</span><span class="sxs-lookup"><span data-stu-id="1a6e5-137">Preview</span></span>  
 <span data-ttu-id="1a6e5-138">按一下 **[預覽]** ，最多可檢視您所選取之資料表的 200 個資料列。</span><span class="sxs-lookup"><span data-stu-id="1a6e5-138">Click **Preview** to view up to 200 rows of data for the table that you selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a6e5-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a6e5-139">See Also</span></span>  
 <span data-ttu-id="1a6e5-140">[ODBC 目的地自訂屬性](data-flow/odbc-destination-custom-properties.md) </span><span class="sxs-lookup"><span data-stu-id="1a6e5-140">[ODBC Destination Custom Properties](data-flow/odbc-destination-custom-properties.md) </span></span>  
 <span data-ttu-id="1a6e5-141">[ODBC 目的地編輯器 &#40;對應頁面&#41;](../../2014/integration-services/odbc-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="1a6e5-141">[ODBC Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/odbc-destination-editor-mappings-page.md) </span></span>  
 [<span data-ttu-id="1a6e5-142">ODBC 目的地編輯器 &#40;錯誤輸出頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="1a6e5-142">ODBC Destination Editor &#40;Error Output Page&#41;</span></span>](../../2014/integration-services/odbc-destination-editor-error-output-page.md)  
  
  
