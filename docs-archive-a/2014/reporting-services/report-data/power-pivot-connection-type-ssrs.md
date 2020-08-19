---
title: " (SSRS) 的 PowerPivot 連線類型 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a104c3c7-f118-4d02-9a0f-6859f1469d11
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 08ce995afa7d458e8ce3ae50a9f572a086a3c697
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710221"
---
# <a name="powerpivot-connection-type-ssrs"></a><span data-ttu-id="b06c3-102">PowerPivot 連接類型 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="b06c3-102">PowerPivot Connection Type (SSRS)</span></span>
  <span data-ttu-id="b06c3-103">您可以使用 SQL Server Analysis Services 資料處理延伸模組，從已在 SharePoint PowerPivot 圖庫中發行的 PowerPivot 活頁簿中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="b06c3-103">You can use SQL Server Analysis Services data processing extension to retrieve data from a PowerPivot workbook that is published in a SharePoint PowerPivot Gallery.</span></span>  
  
 <span data-ttu-id="b06c3-104">您可以使用本主題中的資訊來建置資料來源。</span><span class="sxs-lookup"><span data-stu-id="b06c3-104">Use the information in this topic to build a data source.</span></span> <span data-ttu-id="b06c3-105">如需逐步指示，請參閱 [加入及驗證資料連線或資料來源 &#40;Report Builder 和 SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="b06c3-105">For step-by-step instructions, see [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b06c3-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="b06c3-106">Prerequisites</span></span>  
 <span data-ttu-id="b06c3-107">您必須在 SharePoint 網站的 PowerPivot 圖庫中發行 PowerPivot 資料來源。</span><span class="sxs-lookup"><span data-stu-id="b06c3-107">The PowerPivot data source must be published in a PowerPivot Gallery on a SharePoint site.</span></span>  
  
 <span data-ttu-id="b06c3-108">若要支援報表產生器與 PowerPivot 活頁簿的連接，您的工作站電腦上必須擁有 SQL Server 2008 R2 ADOMD.NET。</span><span class="sxs-lookup"><span data-stu-id="b06c3-108">To support connections from Report Builder to a PowerPivot workbook, you must have SQL Server 2008 R2 ADOMD.NET on your workstation computer.</span></span> <span data-ttu-id="b06c3-109">此用戶端程式庫會隨 PowerPivot for Excel 一起安裝，但是如果您使用的電腦沒有此應用程式，則必須從 [SQL Server 2008 R2 Feature Pack](https://www.microsoft.com/download/details.aspx?id=44272)下載並安裝 ADOMD.NET。</span><span class="sxs-lookup"><span data-stu-id="b06c3-109">This client library is installed with PowerPivot for Excel, but if you are using a computer that does not have this application, you must download and install ADOMD.NET from the [SQL Server 2008 R2 Feature Pack](https://www.microsoft.com/download/details.aspx?id=44272).</span></span>  
  
## <a name="data-source-type"></a><span data-ttu-id="b06c3-110">資料來源類型</span><span class="sxs-lookup"><span data-stu-id="b06c3-110">Data Source Type</span></span>  
 <span data-ttu-id="b06c3-111">請使用報表資料來源類型： **Microsoft SQL Server Analysis Services**。</span><span class="sxs-lookup"><span data-stu-id="b06c3-111">Use report data source type **Microsoft SQL Server Analysis Services**.</span></span>  
  
## <a name="connection-string"></a><span data-ttu-id="b06c3-112">連接字串</span><span class="sxs-lookup"><span data-stu-id="b06c3-112">Connection String</span></span>  
 <span data-ttu-id="b06c3-113">連接字串是 PowerPivot 圖庫或其他文件庫中 SharePoint 上所發行之 PowerPivot 活頁簿的 URL，例如 http://contoso-srv/subsite/PowerPivotLibrary/ContosoSales.xlsx 。</span><span class="sxs-lookup"><span data-stu-id="b06c3-113">The connection string is the URL to PowerPivot workbook published on SharePoint in the PowerPivot Gallery or other library, for example, http://contoso-srv/subsite/PowerPivotLibrary/ContosoSales.xlsx.</span></span>  
  
## <a name="credentials"></a><span data-ttu-id="b06c3-114">認證</span><span class="sxs-lookup"><span data-stu-id="b06c3-114">Credentials</span></span>  
 <span data-ttu-id="b06c3-115">請指定存取 PowerPivot 活頁簿和 SharePoint 網站所需的認證，例如 Windows 驗證 (整合式安全性)。</span><span class="sxs-lookup"><span data-stu-id="b06c3-115">Specify the credentials that you need to access the PowerPivot workbook and SharePoint site, for example, Windows Authentication (Integrated Security).</span></span> <span data-ttu-id="b06c3-116">如需詳細資訊，請參閱 [Reporting Services 中的資料連線、資料來源及連接字串](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) ，或 [在 Report Builder 中指定認證](../specify-credentials-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="b06c3-116">For more information, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) or [Specify Credentials in Report Builder](../specify-credentials-in-report-builder.md).</span></span>  
  
## <a name="queries"></a><span data-ttu-id="b06c3-117">查詢</span><span class="sxs-lookup"><span data-stu-id="b06c3-117">Queries</span></span>  
 <span data-ttu-id="b06c3-118">在您連接至 PowerPivot 資料來源之後，請使用 MDX 圖形化查詢來建立查詢，其方式是從基礎資料結構進行瀏覽及選取。</span><span class="sxs-lookup"><span data-stu-id="b06c3-118">After you connect to the PowerPivot data source, use the MDX graphical query to build a query by browsing and selecting from the underlying data structures.</span></span> <span data-ttu-id="b06c3-119">建立查詢之後，請執行查詢，於結果窗格中查看範例資料。</span><span class="sxs-lookup"><span data-stu-id="b06c3-119">After you build a query, run the query to see sample data in the results pane.</span></span>  
  
 <span data-ttu-id="b06c3-120">查詢設計工具會分析該查詢來決定資料集的欄位。</span><span class="sxs-lookup"><span data-stu-id="b06c3-120">The query designer analyzes the query to determine the dataset fields.</span></span> <span data-ttu-id="b06c3-121">您也可以在 [報表資料] 窗格中手動編輯資料集欄位集合。</span><span class="sxs-lookup"><span data-stu-id="b06c3-121">You can also manually edit the dataset field collection in the **Report Data** pane.</span></span> <span data-ttu-id="b06c3-122">如需詳細資訊，請參閱[加入、編輯、重新整理報表資料窗格中的欄位 &#40;報表產生器及 SSRS&#41;](add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="b06c3-122">For more information, see [Add, Edit, Refresh Fields in the Report Data Pane &#40;Report Builder and SSRS&#41;](add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs.md).</span></span>  
  
## <a name="filters"></a><span data-ttu-id="b06c3-123">篩選器</span><span class="sxs-lookup"><span data-stu-id="b06c3-123">Filters</span></span>  
 <span data-ttu-id="b06c3-124">在 [篩選] 窗格中，請指定要從查詢結果中篩選出或包含在查詢結果中的維度和成員。</span><span class="sxs-lookup"><span data-stu-id="b06c3-124">In the Filters pane, specify dimensions and members to filter out or to include in the query results.</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="b06c3-125">參數</span><span class="sxs-lookup"><span data-stu-id="b06c3-125">Parameters</span></span>  
 <span data-ttu-id="b06c3-126">在 [篩選] 窗格中，選取篩選的 [參數]\*\*\*\* 選項，以便使用對應至篩選選取範圍的可用值來自動建立報表參數。</span><span class="sxs-lookup"><span data-stu-id="b06c3-126">In the Filters pane, select the **Parameters** option for a filter to automatically create a report parameter with available values that correspond to the filter selections.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b06c3-127">備註</span><span class="sxs-lookup"><span data-stu-id="b06c3-127">Remarks</span></span>  
 <span data-ttu-id="b06c3-128">如果您從 PowerPivot 圖庫中的 PowerPivot 活頁簿開啟報表產生器，該報表就不會重新建立樞紐分析表、樞紐分析圖、交叉分析篩選器，以及來自 PowerPivot 活頁簿的其他配置和分析功能。</span><span class="sxs-lookup"><span data-stu-id="b06c3-128">If you open Report Builder from the PowerPivot workbook in a PowerPivot Gallery, the PivotTables, PivotCharts, slicers, and other layout and analytical features from the PowerPivot workbook are not re-created in the report.</span></span> <span data-ttu-id="b06c3-129">而是，空白報表會包括指向 PowerPivot 活頁簿中資料的預先設定資料來源。</span><span class="sxs-lookup"><span data-stu-id="b06c3-129">Instead, the blank report includes a preconfigured data source that points to the data in the PowerPivot workbook.</span></span> <span data-ttu-id="b06c3-130">根據您想要在報表中重新建立的交叉分析篩選器、篩選和資料表或圖表數目，設計以 PowerPivot 活頁簿為基礎的報表可能會相當費時耗力。</span><span class="sxs-lookup"><span data-stu-id="b06c3-130">Designing reports based on a PowerPivot workbook can be labor-intensive and time-consuming depending on the number of slicers, filters, and tables or charts that you want to re-create in the report.</span></span> <span data-ttu-id="b06c3-131">較佳的方法是分開想像報表資料的呈現方式與 PowerPivot 設計方式。</span><span class="sxs-lookup"><span data-stu-id="b06c3-131">A better approach is to envision the presentation of the data that you want in a report independently from the PowerPivot design.</span></span>  
  
 <span data-ttu-id="b06c3-132">PowerPivot 活頁簿中的資料會進行高度壓縮，而針對報表從 PowerPivot 活頁簿中擷取的資料則不會進行壓縮。</span><span class="sxs-lookup"><span data-stu-id="b06c3-132">The data in a PowerPivot workbook is highly compressed; data retrieved from the PowerPivot workbook for a report is not compressed.</span></span> <span data-ttu-id="b06c3-133">您可以使用查詢設計工具來指定篩選和參數，以便將資料限制為報表所需的項目。</span><span class="sxs-lookup"><span data-stu-id="b06c3-133">Use the query designer to specify filters and parameters to limit the data to just what is needed in the report.</span></span>  
  
 <span data-ttu-id="b06c3-134">與連接至 Analysis Services Cube 不同的是，PowerPivot 模型沒有任何階層。</span><span class="sxs-lookup"><span data-stu-id="b06c3-134">Unlike connecting to an Analysis Services cube, a PowerPivot model has no hierarchies.</span></span> <span data-ttu-id="b06c3-135">若要提供類似的功能給活頁簿中的相關交叉分析篩選器，您必須在報表中建立串聯參數。</span><span class="sxs-lookup"><span data-stu-id="b06c3-135">To provide similar functionality to related slicers in the workbook, you must create cascading parameters in the report.</span></span> <span data-ttu-id="b06c3-136">如需詳細資訊，請參閱 [將串聯參數加入至報表 &#40;報表產生器及 SSRS&#41;](../report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)中建立的行動報表。</span><span class="sxs-lookup"><span data-stu-id="b06c3-136">For more information, see [Add Cascading Parameters to a Report &#40;Report Builder and SSRS&#41;](../report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="b06c3-137">在某些情況下，您可能需要調整運算式，才能容納來自 PowerPivot 模型的基礎資料值。</span><span class="sxs-lookup"><span data-stu-id="b06c3-137">In some cases, you might need to adjust expressions to accommodate the underlying data values from the PowerPivot model.</span></span> <span data-ttu-id="b06c3-138">若要將資料轉換成正確的資料類型，或是加入或移除彙總函式，您可能需要修改運算式。</span><span class="sxs-lookup"><span data-stu-id="b06c3-138">You might need to modify expressions to convert data to the right data type or to add or remove an aggregate function.</span></span> <span data-ttu-id="b06c3-139">例如，若要將資料類型從字串轉換成整數，請使用 `=CInt`。</span><span class="sxs-lookup"><span data-stu-id="b06c3-139">For example, to convert data type from String to Integer, use `=CInt`.</span></span> <span data-ttu-id="b06c3-140">發行報表之前，請務必確認報表顯示 PowerPivot 模型中資料的預期值。</span><span class="sxs-lookup"><span data-stu-id="b06c3-140">Always verify that the report displays the expected values from the data in the PowerPivot model before you publish the report.</span></span>  
  
 <span data-ttu-id="b06c3-141">只有在符合下列條件時，才會產生 PowerPivot 圖庫中報表的預覽影像：</span><span class="sxs-lookup"><span data-stu-id="b06c3-141">Preview images of a report in a PowerPivot Gallery are generated only if the following conditions are met:</span></span>  
  
-   <span data-ttu-id="b06c3-142">報表和提供資料的 PowerPivot 活頁簿必須一起儲存在相同的 PowerPivot 圖庫中。</span><span class="sxs-lookup"><span data-stu-id="b06c3-142">The report and the PowerPivot workbook that provides the data must be stored together in the same PowerPivot Gallery.</span></span>  
  
-   <span data-ttu-id="b06c3-143">報表只包含 PowerPivot 資料來源中的 PowerPivot 資料。</span><span class="sxs-lookup"><span data-stu-id="b06c3-143">The report contains only PowerPivot data from a PowerPivot data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b06c3-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b06c3-144">See Also</span></span>  
 <span data-ttu-id="b06c3-145">[Analysis Services MDX 查詢設計工具使用者介面 &#40;報表產生器&#41;](../analysis-services-mdx-query-designer-user-interface-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="b06c3-145">[Analysis Services MDX Query Designer User Interface &#40;Report Builder&#41;](../analysis-services-mdx-query-designer-user-interface-report-builder.md) </span></span>  
 [<span data-ttu-id="b06c3-146">運算式 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="b06c3-146">Expressions &#40;Report Builder and SSRS&#41;</span></span>](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
