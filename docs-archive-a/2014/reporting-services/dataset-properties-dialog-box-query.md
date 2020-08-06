---
title: 資料集屬性對話方塊、查詢 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10160"
- sql12.rtp.rptdesigner.datasetproperties.query.f1
ms.assetid: 1fa34a4b-7de0-4e92-99fa-bc28a206773f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bffb14155d37e67333eb626747e1fcc54e618bbe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606643"
---
# <a name="dataset-properties-dialog-box-query"></a><span data-ttu-id="43268-102">資料集屬性對話方塊、查詢</span><span class="sxs-lookup"><span data-stu-id="43268-102">Dataset Properties Dialog Box, Query</span></span>
  <span data-ttu-id="43268-103">選取 [**資料集屬性**] 對話方塊上的 [**查詢**]，即可選擇資料來源並建立查詢。</span><span class="sxs-lookup"><span data-stu-id="43268-103">Select **Query** on the **Dataset Properties** dialog box to choose a data source and create a query.</span></span>  
  
 <span data-ttu-id="43268-104">**[資料集屬性]** 對話方塊包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="43268-104">The **Dataset Properties** dialog box includes the following:</span></span>  
  
-   [<span data-ttu-id="43268-105">資料集屬性對話方塊、參數</span><span class="sxs-lookup"><span data-stu-id="43268-105">Dataset Properties Dialog Box, Parameters</span></span>](report-data/dataset-properties-dialog-box-parameters.md)  
  
-   [<span data-ttu-id="43268-106">資料集屬性對話方塊、欄位</span><span class="sxs-lookup"><span data-stu-id="43268-106">Dataset Properties Dialog Box, Fields</span></span>](../../2014/reporting-services/dataset-properties-dialog-box-fields.md)  
  
-   [<span data-ttu-id="43268-107">資料集屬性對話方塊、選項</span><span class="sxs-lookup"><span data-stu-id="43268-107">Dataset Properties Dialog Box, Options</span></span>](../../2014/reporting-services/dataset-properties-dialog-box-options.md)  
  
-   [<span data-ttu-id="43268-108">資料集屬性對話方塊、篩選</span><span class="sxs-lookup"><span data-stu-id="43268-108">Dataset Properties Dialog Box, Filters</span></span>](report-data/dataset-properties-dialog-box-filters.md)  
  
## <a name="options"></a><span data-ttu-id="43268-109">選項。</span><span class="sxs-lookup"><span data-stu-id="43268-109">Options</span></span>  
 <span data-ttu-id="43268-110">**名稱**</span><span class="sxs-lookup"><span data-stu-id="43268-110">**Name**</span></span>  
 <span data-ttu-id="43268-111">輸入資料集的名稱。</span><span class="sxs-lookup"><span data-stu-id="43268-111">Type a name for the dataset.</span></span> <span data-ttu-id="43268-112">此名稱不可以與報表中任何資料區域或群組的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="43268-112">The name cannot be the same as a name for any data region or group in the report.</span></span>  
  
 <span data-ttu-id="43268-113">**資料來源**</span><span class="sxs-lookup"><span data-stu-id="43268-113">**Data Source**</span></span>  
 <span data-ttu-id="43268-114">選取要做為資料集基礎的資料來源。</span><span class="sxs-lookup"><span data-stu-id="43268-114">Select the data source on which to base the dataset.</span></span> <span data-ttu-id="43268-115">若要建立新的資料來源，按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="43268-115">To create a new data source, click **New**.</span></span>  
  
 <span data-ttu-id="43268-116">**查詢類型**</span><span class="sxs-lookup"><span data-stu-id="43268-116">**Query type**</span></span>  
 <span data-ttu-id="43268-117">選取資料集使用的命令或查詢類型。</span><span class="sxs-lookup"><span data-stu-id="43268-117">Select the type of command or query to use for the dataset.</span></span> <span data-ttu-id="43268-118">選取 **[文字]** 來執行查詢，以便從資料庫中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="43268-118">Select **Text** to run a query to retrieve data from the database.</span></span> <span data-ttu-id="43268-119">選取 **[資料表]** 即可使用 **的** [TableDirect] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 功能來選取資料表中的所有欄位。</span><span class="sxs-lookup"><span data-stu-id="43268-119">Select **Table** to use the **TableDirect** feature of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to select all the fields within a table.</span></span> <span data-ttu-id="43268-120">選取 **[預存程序]** 即可依名稱執行預存程序。</span><span class="sxs-lookup"><span data-stu-id="43268-120">Select **Stored Procedure** to run a stored procedure by name.</span></span> <span data-ttu-id="43268-121">依預設，會選取 **[文字]** ，這適用於大多數的查詢。</span><span class="sxs-lookup"><span data-stu-id="43268-121">**Text** is selected by default and is used for most queries.</span></span> <span data-ttu-id="43268-122">若要編輯選取的資料來源查詢，按一下 **[查詢設計工具]**。</span><span class="sxs-lookup"><span data-stu-id="43268-122">To edit the selected data source query, click **Query Designer**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="43268-123">並非所有的查詢類型都受到所有資料來源的支援。</span><span class="sxs-lookup"><span data-stu-id="43268-123">Not all query types are supported by all data sources.</span></span> <span data-ttu-id="43268-124">例如， **[資料表]** 只受到 **[OLE DB]** 和 **[ODBC]** 資料來源類型的支援。</span><span class="sxs-lookup"><span data-stu-id="43268-124">For example, **Table** is supported only by data source types **OLE DB** and **ODBC**.</span></span>  
  
 <span data-ttu-id="43268-125">**查詢**</span><span class="sxs-lookup"><span data-stu-id="43268-125">**Query**</span></span>  
 <span data-ttu-id="43268-126">此選項會在選擇 [文字]\*\*\*\* 命令類型選項時出現。</span><span class="sxs-lookup"><span data-stu-id="43268-126">This option appears when you choose the **Text** command type option.</span></span> <span data-ttu-id="43268-127">鍵入查詢，或按一下 [匯入]\*\*\*\* 來匯入已存在的查詢。</span><span class="sxs-lookup"><span data-stu-id="43268-127">Type a query or import a pre-existing query by clicking **Import**.</span></span> <span data-ttu-id="43268-128">按一下**運算式** (*Fx*) ] 按鈕，即可編輯運算式。</span><span class="sxs-lookup"><span data-stu-id="43268-128">Click the **Expression** (*fx*) button to edit the expression.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="43268-129">如果您使用查詢設計工具來建立查詢，則查詢的文字會顯示在此方塊中。</span><span class="sxs-lookup"><span data-stu-id="43268-129">If you used a query designer to build a query, the text of the query appears in this box.</span></span>  
  
 <span data-ttu-id="43268-130">**資料表名稱**</span><span class="sxs-lookup"><span data-stu-id="43268-130">**Table name**</span></span>  
 <span data-ttu-id="43268-131">輸入您想要當做資料集使用之資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="43268-131">Enter the name of the table that you want to use as a dataset.</span></span> <span data-ttu-id="43268-132">此選項會在您選取 **[資料表]** 時出現。</span><span class="sxs-lookup"><span data-stu-id="43268-132">This option appears when you select **Table**.</span></span>  
  
 <span data-ttu-id="43268-133">**選取或輸入預存程序名稱**</span><span class="sxs-lookup"><span data-stu-id="43268-133">**Select or enter stored procedure name**</span></span>  
 <span data-ttu-id="43268-134">輸入或選擇您要使用之預存程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="43268-134">Type or choose the name of the stored procedure that you want to use.</span></span> <span data-ttu-id="43268-135">按一下**運算式** (*Fx*) ] 按鈕，即可編輯運算式。</span><span class="sxs-lookup"><span data-stu-id="43268-135">Click the **Expression** (*fx*) button to edit the expression.</span></span> <span data-ttu-id="43268-136">此選項會在選擇 [預存程序] 命令類型選項時出現。</span><span class="sxs-lookup"><span data-stu-id="43268-136">This option appears when you choose the Stored Procedure command type option.</span></span>  
  
 <span data-ttu-id="43268-137">**逾時 (以秒為單位)**</span><span class="sxs-lookup"><span data-stu-id="43268-137">**Time out (in seconds)**</span></span>  
 <span data-ttu-id="43268-138">輸入查詢超時之前的秒數。預設值是30秒。</span><span class="sxs-lookup"><span data-stu-id="43268-138">Type the number of seconds until the query times out. The default is 30 seconds.</span></span> <span data-ttu-id="43268-139">**[逾時]** 的值必須是空白或大於零。</span><span class="sxs-lookup"><span data-stu-id="43268-139">The value for **Time out** must be empty or greater than zero.</span></span> <span data-ttu-id="43268-140">如果是空白，則查詢不會逾時。</span><span class="sxs-lookup"><span data-stu-id="43268-140">If it is empty, the query does not time out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43268-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43268-141">See Also</span></span>  
 <span data-ttu-id="43268-142">[Reporting Services 中的資料連線、資料來源及連接字串](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="43268-142">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 <span data-ttu-id="43268-143">[將資料加入報表 &#40;報表產生器和 SSRS&#41;](report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="43268-143">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-data/report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="43268-144">[查詢設計工具 &#40;報表產生器&#41;](../../2014/reporting-services/query-designers-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="43268-144">[Query Designers &#40;Report Builder&#41;](../../2014/reporting-services/query-designers-report-builder.md) </span></span>  
 [<span data-ttu-id="43268-145">Reporting Services 查詢設計工具</span><span class="sxs-lookup"><span data-stu-id="43268-145">Reporting Services Query Designers</span></span>](../../2014/reporting-services/reporting-services-query-designers.md)  
  
  
