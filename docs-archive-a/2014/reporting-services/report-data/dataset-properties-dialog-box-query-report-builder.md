---
title: 資料集屬性對話方塊、查詢 (報表產生器) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10024"
ms.assetid: 75432318-0b00-4797-917c-0a2e74f9d951
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a3c9df366bc36302cc7faf22b6efb6c3d1017b5c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710254"
---
# <a name="dataset-properties-dialog-box-query-report-builder"></a><span data-ttu-id="d2801-102">資料集屬性對話方塊、查詢 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="d2801-102">Dataset Properties Dialog Box, Query (Report Builder)</span></span>
  <span data-ttu-id="d2801-103">選取 **[資料集屬性]** 對話方塊上的 **[查詢]** ，從報表伺服器選擇共用資料集或是建立內嵌資料集。</span><span class="sxs-lookup"><span data-stu-id="d2801-103">Select **Query** on the **Dataset Properties** dialog box to choose a shared dataset from a report server or to create an embedded dataset.</span></span> <span data-ttu-id="d2801-104">如果是內嵌資料集，您必須選擇資料來源並建立查詢。</span><span class="sxs-lookup"><span data-stu-id="d2801-104">For an embedded dataset, you must choose a data source and build a query.</span></span>  
  
 <span data-ttu-id="d2801-105">**[資料集屬性]** 對話方塊包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="d2801-105">The **Dataset Properties** dialog box includes the following:</span></span>  
  
-   [<span data-ttu-id="d2801-106">資料集屬性對話方塊、參數 &#40;報表產生器&#41;</span><span class="sxs-lookup"><span data-stu-id="d2801-106">Dataset Properties Dialog Box, Parameters &#40;Report Builder&#41;</span></span>](../dataset-properties-dialog-box-parameters-report-builder.md)  
  
-   [<span data-ttu-id="d2801-107">資料集屬性對話方塊、欄位 &#40;報表產生器&#41;</span><span class="sxs-lookup"><span data-stu-id="d2801-107">Dataset Properties Dialog Box, Fields &#40;Report Builder&#41;</span></span>](../dataset-properties-dialog-box-fields-report-builder.md)  
  
-   [<span data-ttu-id="d2801-108">資料集屬性對話方塊、選項 &#40;報表產生器&#41;</span><span class="sxs-lookup"><span data-stu-id="d2801-108">Dataset Properties Dialog Box, Options &#40;Report Builder&#41;</span></span>](dataset-properties-dialog-box-options-report-builder.md)  
  
-   [<span data-ttu-id="d2801-109">資料集屬性對話方塊、篩選 &#40;報表產生器&#41;</span><span class="sxs-lookup"><span data-stu-id="d2801-109">Dataset Properties Dialog Box, Filters &#40;Report Builder&#41;</span></span>](../dataset-properties-dialog-box-filters-report-builder.md)  
  
 <span data-ttu-id="d2801-110">如需詳細資訊，請參閱 [報表內嵌資料集和共用資料集 &#40;報表產生器及 SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="d2801-110">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="d2801-111">選項。</span><span class="sxs-lookup"><span data-stu-id="d2801-111">Options</span></span>  
 <span data-ttu-id="d2801-112">**名稱**</span><span class="sxs-lookup"><span data-stu-id="d2801-112">**Name**</span></span>  
 <span data-ttu-id="d2801-113">輸入資料集的名稱。</span><span class="sxs-lookup"><span data-stu-id="d2801-113">Type a name for the dataset.</span></span> <span data-ttu-id="d2801-114">此名稱不可以與報表中任何資料區域或群組的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="d2801-114">The name cannot be the same as a name for any data region or group in the report.</span></span>  
  
 <span data-ttu-id="d2801-115">**使用共用資料集**</span><span class="sxs-lookup"><span data-stu-id="d2801-115">**Use a shared dataset**</span></span>  
 <span data-ttu-id="d2801-116">選取這個選項可以從報表伺服器使用預先定義的資料集。</span><span class="sxs-lookup"><span data-stu-id="d2801-116">Select this option to use a predefined dataset from the report server.</span></span>  
  
 <span data-ttu-id="d2801-117">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="d2801-117">**Browse**</span></span>  
 <span data-ttu-id="d2801-118">瀏覽到報表伺服器或 SharePoint 網站上的資料夾，並選取共用資料集 (.rsd)。</span><span class="sxs-lookup"><span data-stu-id="d2801-118">Browse to a folder on a report server or SharePoint site and select a shared dataset (.rsd).</span></span>  
  
 <span data-ttu-id="d2801-119">**在報表中使用內嵌資料集**</span><span class="sxs-lookup"><span data-stu-id="d2801-119">**Use an embedded dataset in my report**</span></span>  
 <span data-ttu-id="d2801-120">選取此選項，即可建立僅供這份報表使用的資料集。</span><span class="sxs-lookup"><span data-stu-id="d2801-120">Select this option to create a dataset for use only by this report.</span></span>  
  
 <span data-ttu-id="d2801-121">**資料來源**</span><span class="sxs-lookup"><span data-stu-id="d2801-121">**Data Source**</span></span>  
 <span data-ttu-id="d2801-122">選取要做為資料集基礎的資料來源。</span><span class="sxs-lookup"><span data-stu-id="d2801-122">Select the data source on which to base the dataset.</span></span> <span data-ttu-id="d2801-123">若要建立新的資料來源，按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="d2801-123">To create a new data source, click **New**.</span></span>  
  
 <span data-ttu-id="d2801-124">**查詢類型**</span><span class="sxs-lookup"><span data-stu-id="d2801-124">**Query type**</span></span>  
 <span data-ttu-id="d2801-125">選取資料集使用的命令或查詢類型。</span><span class="sxs-lookup"><span data-stu-id="d2801-125">Select the type of command or query to use for the dataset.</span></span> <span data-ttu-id="d2801-126">選取 **[文字]** 來執行查詢，以便從資料庫中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="d2801-126">Select **Text** to run a query to retrieve data from the database.</span></span> <span data-ttu-id="d2801-127">選取 **[資料表]** 即可使用 **的** [TableDirect] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能來選取資料表中的所有欄位。</span><span class="sxs-lookup"><span data-stu-id="d2801-127">Select **Table** to use the **TableDirect** feature of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to select all the fields within a table.</span></span> <span data-ttu-id="d2801-128">選取 **[預存程序]** 即可依名稱執行預存程序。</span><span class="sxs-lookup"><span data-stu-id="d2801-128">Select **Stored Procedure** to run a stored procedure by name.</span></span> <span data-ttu-id="d2801-129">依預設，會選取 **[文字]** ，這適用於大多數的查詢。</span><span class="sxs-lookup"><span data-stu-id="d2801-129">**Text** is selected by default and is used for most queries.</span></span> <span data-ttu-id="d2801-130">若要編輯選取的資料來源查詢，按一下 **[查詢設計工具]**。</span><span class="sxs-lookup"><span data-stu-id="d2801-130">To edit the selected data source query, click **Query Designer**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d2801-131">並非所有的查詢類型都受到所有資料來源的支援。</span><span class="sxs-lookup"><span data-stu-id="d2801-131">Not all query types are supported by all data sources.</span></span> <span data-ttu-id="d2801-132">例如， **[資料表]** 只受到 **[OLE DB]** 和 **[ODBC]** 資料來源類型的支援。</span><span class="sxs-lookup"><span data-stu-id="d2801-132">For example, **Table** is supported only by data source types **OLE DB** and **ODBC**.</span></span>  
  
 <span data-ttu-id="d2801-133">**查詢**</span><span class="sxs-lookup"><span data-stu-id="d2801-133">**Query**</span></span>  
 <span data-ttu-id="d2801-134">此選項會在選擇 [文字]\*\*\*\* 命令類型選項時出現。</span><span class="sxs-lookup"><span data-stu-id="d2801-134">This option appears when you choose the **Text** command type option.</span></span> <span data-ttu-id="d2801-135">鍵入查詢，或按一下 [匯入]\*\*\*\* 來匯入已存在的查詢。</span><span class="sxs-lookup"><span data-stu-id="d2801-135">Type a query or import a pre-existing query by clicking **Import**.</span></span> <span data-ttu-id="d2801-136">按一下**運算式** (*Fx*) ] 按鈕，即可編輯運算式。</span><span class="sxs-lookup"><span data-stu-id="d2801-136">Click the **Expression** (*fx*) button to edit the expression.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d2801-137">如果您使用查詢設計工具來建立查詢，則查詢的文字會顯示在此方塊中。</span><span class="sxs-lookup"><span data-stu-id="d2801-137">If you used a query designer to build a query, the text of the query appears in this box.</span></span>  
  
 <span data-ttu-id="d2801-138">**資料表名稱**</span><span class="sxs-lookup"><span data-stu-id="d2801-138">**Table name**</span></span>  
 <span data-ttu-id="d2801-139">輸入您想要當做資料集使用之資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="d2801-139">Enter the name of the table that you want to use as a dataset.</span></span> <span data-ttu-id="d2801-140">此選項會在您選取 **[資料表]** 時出現。</span><span class="sxs-lookup"><span data-stu-id="d2801-140">This option appears when you select **Table**.</span></span>  
  
 <span data-ttu-id="d2801-141">**選取或輸入預存程序名稱**</span><span class="sxs-lookup"><span data-stu-id="d2801-141">**Select or enter stored procedure name**</span></span>  
 <span data-ttu-id="d2801-142">輸入或選擇您要使用之預存程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="d2801-142">Type or choose the name of the stored procedure that you want to use.</span></span> <span data-ttu-id="d2801-143">按一下**運算式** (*Fx*) ] 按鈕，即可編輯運算式。</span><span class="sxs-lookup"><span data-stu-id="d2801-143">Click the **Expression** (*fx*) button to edit the expression.</span></span> <span data-ttu-id="d2801-144">此選項會在選擇 [預存程序] 命令類型選項時出現。</span><span class="sxs-lookup"><span data-stu-id="d2801-144">This option appears when you choose the Stored Procedure command type option.</span></span>  
  
 <span data-ttu-id="d2801-145">**逾時 (以秒為單位)**</span><span class="sxs-lookup"><span data-stu-id="d2801-145">**Time out (in seconds)**</span></span>  
 <span data-ttu-id="d2801-146">輸入查詢超時之前的秒數。預設值是30秒。</span><span class="sxs-lookup"><span data-stu-id="d2801-146">Type the number of seconds until the query times out. The default is 30 seconds.</span></span> <span data-ttu-id="d2801-147">**[逾時]** 的值必須是空白或大於零。</span><span class="sxs-lookup"><span data-stu-id="d2801-147">The value for **Time out** must be empty or greater than zero.</span></span> <span data-ttu-id="d2801-148">如果是空白，則查詢不會逾時。</span><span class="sxs-lookup"><span data-stu-id="d2801-148">If it is empty, the query does not time out.</span></span>  
  
 <span data-ttu-id="d2801-149">**重新整理欄位**</span><span class="sxs-lookup"><span data-stu-id="d2801-149">**Refresh Fields**</span></span>  
 <span data-ttu-id="d2801-150">執行查詢命令，以更新 [資料集屬性對話方塊、欄位](../dataset-properties-dialog-box-fields-report-builder.md) 頁面上的欄位清單。</span><span class="sxs-lookup"><span data-stu-id="d2801-150">Run the query command to update the list of fields in the [Dataset Properties Dialog Box, Fields](../dataset-properties-dialog-box-fields-report-builder.md) page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2801-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2801-151">See Also</span></span>  
 <span data-ttu-id="d2801-152">[將資料加入報表 &#40;報表產生器和 SSRS&#41;](report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d2801-152">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="d2801-153">[對話方塊、窗格和嚮導的報表產生器說明](../report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="d2801-153">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 [<span data-ttu-id="d2801-154">查詢設計工具 &#40;報表產生器&#41;</span><span class="sxs-lookup"><span data-stu-id="d2801-154">Query Designers &#40;Report Builder&#41;</span></span>](../query-designers-report-builder.md)  
  
  
