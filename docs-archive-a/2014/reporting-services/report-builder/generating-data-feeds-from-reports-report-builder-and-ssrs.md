---
title: 從多個報表產生資料摘要 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4e00789f-6967-42e5-b2b4-03181fdb1e2c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c7f999560bf3216ea84c672c733539d2cad44a15
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593846"
---
# <a name="generating-data-feeds-from-reports-report-builder-and-ssrs"></a><span data-ttu-id="cd225-102">從多個報表產生資料摘要 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="cd225-102">Generating Data Feeds from Reports (Report Builder and SSRS)</span></span>
  <span data-ttu-id="cd225-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Atom 轉譯延伸模組會產生 Atom 服務文件，其中會列出可從報表取得的資料摘要，以及來自報表中之資料區的資料摘要。</span><span class="sxs-lookup"><span data-stu-id="cd225-103">The [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Atom rendering extension generates an Atom service document that lists the data feeds available from a report and the data feeds from the data regions in a report.</span></span> <span data-ttu-id="cd225-104">您可以使用此延伸模組產生符合 Atom 的資料摘要，這些資料摘要可以使用可取用報表產生之資料摘要的應用程式讀取與交換。</span><span class="sxs-lookup"><span data-stu-id="cd225-104">You use this extension to generate Atom-compliant data feeds that are readable and exchangeable with applications that can consume data feeds generated from reports.</span></span> <span data-ttu-id="cd225-105">例如，您可以使用 Atom 轉譯延伸模組來產生可在用戶端中使用的資料摘要 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cd225-105">For example, you can use the Atom rendering extension to generated data feeds that you can then use in the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] client.</span></span>  
  
 <span data-ttu-id="cd225-106">Atom 服務文件在報表中，每個資料區至少會列出一個資料摘要。</span><span class="sxs-lookup"><span data-stu-id="cd225-106">The Atom service document lists at least one data feed for each data region in a report.</span></span> <span data-ttu-id="cd225-107">根據資料區的類型以及該資料區顯示的資料， [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 可能會產生來自某個資料區的多個資料摘要。</span><span class="sxs-lookup"><span data-stu-id="cd225-107">Depending on the type of data region and the data that the data region displays, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] might generate multiple data feeds from a data region.</span></span> <span data-ttu-id="cd225-108">例如，矩陣或圖表可以提供多個資料摘要。</span><span class="sxs-lookup"><span data-stu-id="cd225-108">For example, a matrix or chart can provide multiple data feeds.</span></span> <span data-ttu-id="cd225-109">當 Atom 轉譯延伸模組建立 Atom 服務文件時，系統會針對每個資料摘要建立一個唯一的識別碼，而您會在 URL 中使用該識別碼來存取資料摘要的內容。</span><span class="sxs-lookup"><span data-stu-id="cd225-109">When the Atom rendering extension creates the Atom service document, a unique identifier is created for each data feed and you use the identifier in the URL to access the content of the data feed.</span></span>  
  
 <span data-ttu-id="cd225-110">Atom 轉譯延伸模組針對資料摘要產生資料的方式類似於逗點分隔值 (CSV) 轉譯延伸模組將資料轉譯為 CSV 檔案的方式。</span><span class="sxs-lookup"><span data-stu-id="cd225-110">The way that the Atom rendering extension generates data for a data feed is similar to how the Comma-Separated Value (CSV) rendering extension renders data to a CSV file.</span></span> <span data-ttu-id="cd225-111">資料摘要就像是 CSV 檔案，是報表資料的扁平化表示法。</span><span class="sxs-lookup"><span data-stu-id="cd225-111">Like a CSV file, a data feed is a flattened representation of the report data.</span></span> <span data-ttu-id="cd225-112">例如，包含加總群組內銷售量之資料列群組的資料表會在每個資料列中重複顯示這個總和，而且沒有僅包含總和的個別資料列。</span><span class="sxs-lookup"><span data-stu-id="cd225-112">For example, a table with a row group that sums the sales within a group repeats the sum in every data row and there is no separate row that contains only the sum.</span></span>  
  
 <span data-ttu-id="cd225-113">您可以使用報表管理員、報表伺服器或是與 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]整合的 SharePoint 網站，產生 Atom 服務文件與資料摘要。</span><span class="sxs-lookup"><span data-stu-id="cd225-113">You can generate Atom service documents and data feeds using Report Manager, Report Server, or a SharePoint site that is integrated with [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="cd225-114">Atom 適用於成對的相關標準。</span><span class="sxs-lookup"><span data-stu-id="cd225-114">Atom applies to a pair of related standards.</span></span> <span data-ttu-id="cd225-115">Atom 服務文件符合 RFC 5023 Atom 發行通訊協定規格，而資料摘要符合 RFC 4287 Atom 同步發佈格式通訊協定規格。</span><span class="sxs-lookup"><span data-stu-id="cd225-115">The Atom service document conforms to the RFC 5023 Atom publishing protocol specification and the data feeds conform to the RFC 4287 Atom syndication format protocol specification.</span></span>  
  
 <span data-ttu-id="cd225-116">下列章節提供如何使用 Atom 轉譯延伸模組的其他資訊：</span><span class="sxs-lookup"><span data-stu-id="cd225-116">The following sections provide additional information about how to use the Atom rendering extension:</span></span>  
  
 [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="reports-as-data-feeds"></a><a name="ReportDataAsDataFeeds"></a> <span data-ttu-id="cd225-117">當做資料摘要的報表</span><span class="sxs-lookup"><span data-stu-id="cd225-117">Reports as Data Feeds</span></span>  
 <span data-ttu-id="cd225-118">您可以匯出實際報表做為資料摘要，或者您可以建立其主要用途為以資料摘要的形式提供資料給應用程式的報表。</span><span class="sxs-lookup"><span data-stu-id="cd225-118">You can export a production report as a data feed or you can create a report whose primary purpose is provide data, in the form of data feeds, to applications.</span></span> <span data-ttu-id="cd225-119">當資料不容易透過用戶端資料提供者存取時，或當您想要隱藏資料來源的複雜度，讓資料的使用更為簡單時，使用報表做為資料摘要提供您另一種將資料提供給應用程式的方式。</span><span class="sxs-lookup"><span data-stu-id="cd225-119">Using reports as a data feed gives you an additional way to provide data to applications when the data is not easy to access through client data providers, or when you prefer to hide the complexity of the data source and make it simpler to use the data.</span></span> <span data-ttu-id="cd225-120">使用報表資料做為資料摘要的另一個優點是，您可以使用報表管理員、安全性、排程，以及報表快照集之類的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 功能來管理提供資料摘要的報表。</span><span class="sxs-lookup"><span data-stu-id="cd225-120">Another benefit of using report data as a data feed is that you can use [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] features such as Report Manager, security, scheduling, and report snapshots to manage the reports that provide data feeds.</span></span>  
  
 <span data-ttu-id="cd225-121">為充分利用 Atom 轉譯延伸模組，您應該了解如何將報表轉譯為資料摘要。</span><span class="sxs-lookup"><span data-stu-id="cd225-121">To get the most from the Atom rendering extension, you should understand how the report is rendered into data feeds.</span></span> <span data-ttu-id="cd225-122">如果您要使用現有的報表，能夠預測報表所要產生的資料摘要是一項相當實用的功能；如果您要撰寫專門當做資料摘要使用的報表，則可以包含資料並微調報表配置以充分發揮資料摘要實用性，就是非常重要的功能。</span><span class="sxs-lookup"><span data-stu-id="cd225-122">If you are using existing reports, being able to predict what the data feeds the reports will generate is useful; if you are writing report specifically for use as data feeds, being able to include the data and fine tune the report layout to maximize the usefulness of the data feeds is valuable.</span></span>  
  
 <span data-ttu-id="cd225-123">如需詳細資訊，請參閱[從報表產生資料摘要 &#40;報表產生器和 SSRS&#41;](generate-data-feeds-from-a-report-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="cd225-123">For more information, see [Generate Data Feeds from a Report &#40;Report Builder and SSRS&#41;](generate-data-feeds-from-a-report-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="atom-service-document-atomsvc-file"></a><a name="AtomServiceDocument"></a> <span data-ttu-id="cd225-124">Atom 服務文件 (.atomsvc 檔)</span><span class="sxs-lookup"><span data-stu-id="cd225-124">Atom Service Document (.atomsvc file)</span></span>  
 <span data-ttu-id="cd225-125">Atom 服務文件會指定一個或多個資料摘要的連接。</span><span class="sxs-lookup"><span data-stu-id="cd225-125">An Atom service document specifies a connection to one or more data feeds.</span></span> <span data-ttu-id="cd225-126">連線至少是產生摘要之資料服務的簡單 URL。</span><span class="sxs-lookup"><span data-stu-id="cd225-126">At a minimum, the connection is a simple URL to the data service that produces the feed.</span></span>  
  
 <span data-ttu-id="cd225-127">當您使用 Atom 轉譯延伸模組轉譯報表資料時，Atom 服務文件會列出可用於報表的資料摘要。</span><span class="sxs-lookup"><span data-stu-id="cd225-127">When you render report data by using the Atom rendering extension, the Atom service document lists the data feeds available for a report.</span></span> <span data-ttu-id="cd225-128">此文件至少會列出報表中每個資料區的一個資料摘要。</span><span class="sxs-lookup"><span data-stu-id="cd225-128">The document lists at least one data feed for each data region in the report.</span></span> <span data-ttu-id="cd225-129">資料表和量測計各自只會產生一個資料摘要，但是矩陣、清單和圖表可能會根據所顯示的資料，產生多個資料摘要。</span><span class="sxs-lookup"><span data-stu-id="cd225-129">Tables and gauges generate only one data feed each, but matrices, lists, and charts might generated multiple depending on the data they display.</span></span>  
  
 <span data-ttu-id="cd225-130">下列圖表顯示使用兩個資料表和一個圖表的報表。</span><span class="sxs-lookup"><span data-stu-id="cd225-130">The following diagram shows a report that uses two tables and a chart.</span></span>  
  
 <span data-ttu-id="cd225-131">![RS_Atom_TableAndChartDataFeeds](../media/rs-atom-tableandchartdatafeeds.gif "RS_Atom_TableAndChartDataFeeds")</span><span class="sxs-lookup"><span data-stu-id="cd225-131">![RS_Atom_TableAndChartDataFeeds](../media/rs-atom-tableandchartdatafeeds.gif "RS_Atom_TableAndChartDataFeeds")</span></span>  
  
 <span data-ttu-id="cd225-132">從此報表產生的 Atom 服務文件包含三個資料摘要，兩個資料表和一個圖表各一個資料摘要。</span><span class="sxs-lookup"><span data-stu-id="cd225-132">The Atom service document generated from this report includes three data feeds, one for each table and one for the chart.</span></span>  
  
 <span data-ttu-id="cd225-133">根據矩陣的結構，矩陣資料區可能會有一個以上的資料摘要。</span><span class="sxs-lookup"><span data-stu-id="cd225-133">The matrix data regions might have more than one data feed, depending on the structure of the matrix.</span></span> <span data-ttu-id="cd225-134">下列圖表顯示使用產生兩個資料摘要之矩陣的報表。</span><span class="sxs-lookup"><span data-stu-id="cd225-134">The following diagram shows a report that uses a matrix that generates two data feeds.</span></span>  
  
 <span data-ttu-id="cd225-135">![RS_Atom_PeerDynamicColumns](../media/rs-atom-peerdynamiccolumns.gif "RS_Atom_PeerDynamicColumns")</span><span class="sxs-lookup"><span data-stu-id="cd225-135">![RS_Atom_PeerDynamicColumns](../media/rs-atom-peerdynamiccolumns.gif "RS_Atom_PeerDynamicColumns")</span></span>  
  
 <span data-ttu-id="cd225-136">從此報表產生的 Atom 服務文件包含兩個資料摘要 (每個動態對等資料行各一個)：Territory 和 Year。</span><span class="sxs-lookup"><span data-stu-id="cd225-136">The Atom service document generated from this report includes two data feeds, one for each of the dynamic peer columns: Territory and Year.</span></span> <span data-ttu-id="cd225-137">下列圖表顯示每個資料摘要的內容。</span><span class="sxs-lookup"><span data-stu-id="cd225-137">The following diagram shows the content of each data feed.</span></span>  
  
 <span data-ttu-id="cd225-138">![RS_Atom_PeerDynamicDataFeeds](../media/rs-atom-peerdynamicdatafeeds.gif "RS_Atom_PeerDynamicDataFeeds")</span><span class="sxs-lookup"><span data-stu-id="cd225-138">![RS_Atom_PeerDynamicDataFeeds](../media/rs-atom-peerdynamicdatafeeds.gif "RS_Atom_PeerDynamicDataFeeds")</span></span>  
  

  
##  <a name="data-feeds"></a><a name="DataFeeds"></a> <span data-ttu-id="cd225-139">資料摘要</span><span class="sxs-lookup"><span data-stu-id="cd225-139">Data Feeds</span></span>  
 <span data-ttu-id="cd225-140">資料摘要是一種 XML 檔案，這個檔案擁有一致的表格格式 (不會隨時間而變更) 與變數資料 (每次執行報表時都可能不同)。</span><span class="sxs-lookup"><span data-stu-id="cd225-140">The data feed is an XML file that has a consistent tabular format that does not change over time and variable data that can be different each time the report is run.</span></span> <span data-ttu-id="cd225-141">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 所產生的資料摘要與 ADO.NET Data Services 所產生的資料摘要格式相同。</span><span class="sxs-lookup"><span data-stu-id="cd225-141">The data feeds generated by [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] are in the same format as those generated by  that ADO.NET Data Services.</span></span>  
  
 <span data-ttu-id="cd225-142">一個資料摘要包含兩個區段：標頭和資料。</span><span class="sxs-lookup"><span data-stu-id="cd225-142">A data feed contains two sections: header and data.</span></span> <span data-ttu-id="cd225-143">Atom 規格會定義每個區段中的元素。</span><span class="sxs-lookup"><span data-stu-id="cd225-143">The Atom specification defines the elements in each section.</span></span> <span data-ttu-id="cd225-144">標頭包含搭配資料摘要使用之字元編碼結構描述之類的資訊。</span><span class="sxs-lookup"><span data-stu-id="cd225-144">The header includes information such as the character encoding schema to use with the data feeds.</span></span>  
  
### <a name="header-section"></a><span data-ttu-id="cd225-145">標頭區段</span><span class="sxs-lookup"><span data-stu-id="cd225-145">Header Section</span></span>  
 <span data-ttu-id="cd225-146">下列 XML 程式碼顯示資料摘要的標頭區段。</span><span class="sxs-lookup"><span data-stu-id="cd225-146">The following XML code shows the header section of a data feed.</span></span>  
  
 `<?xml version="1.0" encoding="utf-8" standalone="yes"?><feed xmlns:d="https://schemas.microsoft.com/ado/2007/08/dataservices" xmlns:m="https://schemas.microsoft.com/ado/2007/08/dataservices/metadata" xmlns="http://www.w3.org/2005/Atom">`  
  
 `<title type="text"></title>`  
  
 `<id>uuid:1795992c-a6f3-40ec-9243-fbfd0b1a5be3;id=166321</id>`  
  
 `<updated>2009-05-08T23:09:58Z</updated>`  
  
### <a name="data-section"></a><span data-ttu-id="cd225-147">資料區段</span><span class="sxs-lookup"><span data-stu-id="cd225-147">Data Section</span></span>  
 <span data-ttu-id="cd225-148">資料摘要的資料區段在 Atom 轉譯延伸模組 `entry` 所產生的簡維資料列集內，包含一個 <> 元素。</span><span class="sxs-lookup"><span data-stu-id="cd225-148">The data section of the data feeds contains one <`entry`> element for each row in the flattened rowset generated by the Atom rendering extension.</span></span>  
  
 <span data-ttu-id="cd225-149">下列圖表顯示使用群組和總計的報表。</span><span class="sxs-lookup"><span data-stu-id="cd225-149">The following diagram shows a report that uses groups and totals.</span></span>  
  
 <span data-ttu-id="cd225-150">![RS_Atom_ProductSalesSummaryCircledValues](../media/rs-atom-productsalessummarycircledvalues.gif "RS_Atom_ProductSalesSummaryCircledValues")</span><span class="sxs-lookup"><span data-stu-id="cd225-150">![RS_Atom_ProductSalesSummaryCircledValues](../media/rs-atom-productsalessummarycircledvalues.gif "RS_Atom_ProductSalesSummaryCircledValues")</span></span>  
  
 <span data-ttu-id="cd225-151">下列 XML 顯示 `entry` 來自資料摘要中該報表的 <> 元素。</span><span class="sxs-lookup"><span data-stu-id="cd225-151">The following XML shows an <`entry`> element from that report in a data feed.</span></span> <span data-ttu-id="cd225-152">請注意，<`entry`> 元素包含群組的銷售和訂單總計，以及所有群組的銷售和訂單總計。</span><span class="sxs-lookup"><span data-stu-id="cd225-152">Notice that the <`entry`> element includes the totals of the sales and orders for the group and the totals of sales and orders for all the groups.</span></span> <span data-ttu-id="cd225-153"><`entry`> 元素包含報表上的所有值。</span><span class="sxs-lookup"><span data-stu-id="cd225-153">The <`entry`> element includes all values on the report.</span></span>  
  
 `<entry><id>uuid:1795992c-a6f3-40ec-9243-fbfd0b1a5be3;id=166322</id><title type="text"></title><updated>2009-05-08T23:09:58Z</updated><author /><content type="application/xml"><m:properties>`  
  
 `<d:ProductCategory_Value>Accessories</d:ProductCategory_Value>`  
  
 `<d:OrderYear_Value m:type="Edm.Int32">2001</d:OrderYear_Value>`  
  
 `<d:SumLineTotal_Value m:type="Edm.Decimal">20235.364608</d:SumLineTotal_Value>`  
  
 `<d:SumOrderQty_Value m:type="Edm.Int32">1003</d:SumOrderQty_Value>`  
  
 `<d:SumLineTotal_Total_2_1 m:type="Edm.Decimal">1272072.883926</d:SumLineTotal_Total_2_1>`  
  
 `<d:SumOrderQty_Total_2_1 m:type="Edm.Double">61932</d:SumOrderQty_Total_2_1>`  
  
 `<d:SumLineTotal_Total_2_2 m:type="Edm.Decimal">109846381.399888</d:SumLineTotal_Total_2_2>`  
  
 `<d:SumOrderQty_Total_2_2 m:type="Edm.Double">274914</d:SumOrderQty_Total_2_2></m:properties></content>`  
  
 `</entry>`  
  
### <a name="working-with-data-feeds"></a><span data-ttu-id="cd225-154">處理資料摘要</span><span class="sxs-lookup"><span data-stu-id="cd225-154">Working with Data Feeds</span></span>  
 <span data-ttu-id="cd225-155">報表所產生的所有資料摘要包含產生資料摘要之資料區父系範圍內的報表項目。</span><span class="sxs-lookup"><span data-stu-id="cd225-155">All data feeds generated by the report include the report items that are in scope of the parent of the data region that generate the data feeds.</span></span> <span data-ttu-id="cd225-156">.</span><span class="sxs-lookup"><span data-stu-id="cd225-156">.</span></span> <span data-ttu-id="cd225-157">設想一個包含數個資料表和一個圖表的報表。</span><span class="sxs-lookup"><span data-stu-id="cd225-157">Imagine a report that has several tables and a chart.</span></span> <span data-ttu-id="cd225-158">報表主體中的文字方塊會提翁每個資料區的描述文字。</span><span class="sxs-lookup"><span data-stu-id="cd225-158">Text boxes in the report body provides descriptive text of each data region.</span></span> <span data-ttu-id="cd225-159">報表所產生之每個資料摘要中的每個項目都包含文字方塊的值。</span><span class="sxs-lookup"><span data-stu-id="cd225-159">Every entry in every data feed that the report generates includes the value of the text box.</span></span> <span data-ttu-id="cd225-160">例如，如果文字為 "Chart displays monthly sales averages by sales region" (圖表依銷售區域顯示每月的平均銷售額)，全部三個資料摘要都會在每個資料列上加入這段文字。</span><span class="sxs-lookup"><span data-stu-id="cd225-160">For example, if the text is "Chart displays monthly sales averages by sales region", all three data feeds would include this text on each row.</span></span>  
  
 <span data-ttu-id="cd225-161">如果報表配置包含階層式資料關聯性 (如巢狀資料區)，這些關聯性就會包含在報表資料的扁平化資料列集中。</span><span class="sxs-lookup"><span data-stu-id="cd225-161">If the report layout includes hierarchical data relationships, such as nested data regions, those relationships are included in the flattened rowset of report data.</span></span>  
  
 <span data-ttu-id="cd225-162">巢狀資料區的資料列通常很寬，特別是巢狀資料表和矩陣包含群組和總計時更是如此。</span><span class="sxs-lookup"><span data-stu-id="cd225-162">The data rows for nested data regions are typically wide, especially if the nested tables and matrices include groups and totals.</span></span> <span data-ttu-id="cd225-163">將報表匯出至資料摘要，以及檢視資料摘要以確認產生的資料就是預期的資料時，您可能會發現這個功能相當實用。</span><span class="sxs-lookup"><span data-stu-id="cd225-163">You might find it useful to export the report to a data feed and view the data feed to verify that the data generated is what you expected.</span></span>  
  
 <span data-ttu-id="cd225-164">當 Atom 轉譯延伸模組建立 Atom 服務文件時，系統會針對資料摘要建立一個唯一的識別碼，而您會在 URL 中使用該識別碼來檢視資料摘要的內容。</span><span class="sxs-lookup"><span data-stu-id="cd225-164">When the Atom rendering extension creates the Atom service document, a unique identifier is created for the data feed and you use the identifier in the URL to view the content of the data feed.</span></span> <span data-ttu-id="cd225-165">如上所示的範例 Atom 服務檔包含 URL <http://ServerName/ReportServer?%2fProduct+Sales+Summary&rs%3aCommand=Render&rs%3aFormat=ATOM&rc%3aDataFeed=xAx0x1> "。</span><span class="sxs-lookup"><span data-stu-id="cd225-165">The sample Atom service document, shown above, includes the URL <http://ServerName/ReportServer?%2fProduct+Sales+Summary&rs%3aCommand=Render&rs%3aFormat=ATOM&rc%3aDataFeed=xAx0x1>".</span></span> <span data-ttu-id="cd225-166">此 URL 會識別報表 (Product Sales Summary)、Atom 轉譯延伸模組 (ATOM)，以及資料摘要的名稱 (xAx0x1)。</span><span class="sxs-lookup"><span data-stu-id="cd225-166">The URL identifies the report (Product Sales Summary), the Atom rendering format (ATOM), and the name of the data feed (xAx0x1).</span></span>  
  
 <span data-ttu-id="cd225-167">報表項目名稱預設為報表項目的報表定義語言 (RDL) 元素名稱，而且這些名稱通常不容易了解或是不容易記住。</span><span class="sxs-lookup"><span data-stu-id="cd225-167">Report item names default to the report definition language (RDL) element names of the report items and often they are not intuitive or easy to remember.</span></span> <span data-ttu-id="cd225-168">例如，置於報表中之第一個矩陣的預設名稱為 Tablix 1。</span><span class="sxs-lookup"><span data-stu-id="cd225-168">For example, the default name of the first matrix placed in a report is Tablix 1.</span></span> <span data-ttu-id="cd225-169">資料摘要會使用這些名稱。</span><span class="sxs-lookup"><span data-stu-id="cd225-169">The data feeds use these names.</span></span>  
  
 <span data-ttu-id="cd225-170">若要讓資料摘要更容易處理，您可以使用資料區的 DataElementName 屬性來提供易記的名稱。</span><span class="sxs-lookup"><span data-stu-id="cd225-170">To make the data feed easier to work with, you can use the DataElementName property of the data region to provide friendly names.</span></span> <span data-ttu-id="cd225-171">如果您提供 DataElementName 資料摘要子項目的值 <`d`> 會使用它，而不是預設的資料區名稱。</span><span class="sxs-lookup"><span data-stu-id="cd225-171">If you provide a value for DataElementName the data feed subelement <`d`> will use is it instead of the default data region name.</span></span> <span data-ttu-id="cd225-172">例如，如果資料區的預設名稱是 Tablix1，而 DataElementName 設定 SalesByTerritoryYear，則資料摘要中的 <`d`> 會使用 SalesByTerritoryYear。</span><span class="sxs-lookup"><span data-stu-id="cd225-172">For example, if the default name of a data regions is Tablix1 and DataElementName set SalesByTerritoryYear then the <`d`> in the data feed uses SalesByTerritoryYear.</span></span> <span data-ttu-id="cd225-173">如果資料區有兩個資料摘要，如上述的矩陣報表，則在資料摘要中使用的名稱為 SalesByTerritoryYear _Territory 和 SalesByTerritoryYear _Year。</span><span class="sxs-lookup"><span data-stu-id="cd225-173">If the data regions has two data feeds like the matrix report described above, the names used in the data feeds are SalesByTerritoryYear _Territory and SalesByTerritoryYear _Year.</span></span>  
  
 <span data-ttu-id="cd225-174">如果您比較顯示在報表上的資料與資料摘要中的資料，可能會發現部分差異。</span><span class="sxs-lookup"><span data-stu-id="cd225-174">If you compare the data shown on the report and the data in the data feed, you might notice some differences.</span></span> <span data-ttu-id="cd225-175">報表通常會顯示格式化的數值和時間/日期資料，而資料摘要則包含未格式化的摘要。</span><span class="sxs-lookup"><span data-stu-id="cd225-175">Reports often shows formatted numeric and time/date data whereas the data feed contains unformatted data.</span></span>  
  
 <span data-ttu-id="cd225-176">資料摘要會以副檔名 .atom 儲存。</span><span class="sxs-lookup"><span data-stu-id="cd225-176">A data feed is saved with the .atom file name extension.</span></span> <span data-ttu-id="cd225-177">您可以使用文字或 XML 編輯器 (例如 [記事本] 或 XML 編輯器) 來檢視檔案結構和內容。</span><span class="sxs-lookup"><span data-stu-id="cd225-177">You can use a text or XML editor such as Notepad or XML Editor to view the file structure and content.</span></span>  
  

  
##  <a name="flattening-report-data"></a><a name="FlatteningReportData"></a> <span data-ttu-id="cd225-178">扁平化報表資料</span><span class="sxs-lookup"><span data-stu-id="cd225-178">Flattening Report Data</span></span>  
 <span data-ttu-id="cd225-179">Atom 轉譯器會提供 XML 格式的報表資料做為扁平化的資料列集。</span><span class="sxs-lookup"><span data-stu-id="cd225-179">The Atom renderer provides report data as flattened rowsets in an XML format.</span></span> <span data-ttu-id="cd225-180">除了以下幾個例外情況之外，扁平化資料表的規則與 CSV 轉譯器的規則相同：</span><span class="sxs-lookup"><span data-stu-id="cd225-180">The rules for flattening data tables are the same to those of the CSV renderer with a few exceptions:</span></span>  
  
-   <span data-ttu-id="cd225-181">範圍中的項目已扁平化為詳細資料層次。</span><span class="sxs-lookup"><span data-stu-id="cd225-181">Items in scope are flattened to the detail level.</span></span> <span data-ttu-id="cd225-182">與 CSV 轉譯器不同的是，最上層的文字方塊會出現在寫入資料摘要的每個項目中。</span><span class="sxs-lookup"><span data-stu-id="cd225-182">Unlike the CSV renderer, the text boxes at the top level appear in each entry written to the data feed.</span></span>  
  
-   <span data-ttu-id="cd225-183">報表參數值在輸出的每個資料列上已經過轉譯。</span><span class="sxs-lookup"><span data-stu-id="cd225-183">Report parameter values are rendered on each row of the output.</span></span>  
  
 <span data-ttu-id="cd225-184">階層式與群組資料必須扁平化，才能以符合 Atom 的格式表示。</span><span class="sxs-lookup"><span data-stu-id="cd225-184">Hierarchical and grouped data must be flattened in order to be represented in the Atom-compliant format.</span></span> <span data-ttu-id="cd225-185">轉譯延伸模組會將報表扁平化為樹狀結構，可表示資料區域內的巢狀群組。</span><span class="sxs-lookup"><span data-stu-id="cd225-185">The rendering extension flattens the report into a tree structure that represents the nested groups within the data region.</span></span> <span data-ttu-id="cd225-186">若要將報表扁平化：</span><span class="sxs-lookup"><span data-stu-id="cd225-186">To flatten the report:</span></span>  
  
-   <span data-ttu-id="cd225-187">資料列階層要在資料行階層之前扁平化。</span><span class="sxs-lookup"><span data-stu-id="cd225-187">A row hierarchy is flattened before a column hierarchy.</span></span>  
  
-   <span data-ttu-id="cd225-188">資料列階層的成員會在資料行階層的成員之前，轉譯為資料摘要。</span><span class="sxs-lookup"><span data-stu-id="cd225-188">Members of the row hierarchy are rendered to the data feed before members of the column hierarchy.</span></span>  
  
-   <span data-ttu-id="cd225-189">資料行的排列順序如下：文字方塊在主體順序中為由左至右、由上至下，後面接著以由左至右、由上至下排列的資料區域。</span><span class="sxs-lookup"><span data-stu-id="cd225-189">Columns are ordered as follows: text boxes in body order left-to-right, top-to-bottom followed by data regions ordered left-to-right, top-to-bottom.</span></span>  
  
-   <span data-ttu-id="cd225-190">在資料區域中，資料行的排列順序如下：邊角成員、資料列階層成員、資料行階層成員，然後是資料格。</span><span class="sxs-lookup"><span data-stu-id="cd225-190">Within a data region, the columns are ordered as follows: corner members, row hierarchy members, column hierarchy members, and then cells.</span></span>  
  
-   <span data-ttu-id="cd225-191">對等資料區域是一種資料區域或動態群組，可以共用一般資料區域或動態上階。</span><span class="sxs-lookup"><span data-stu-id="cd225-191">Peer data regions are data regions or dynamic groups that share a common data region or dynamic ancestor.</span></span> <span data-ttu-id="cd225-192">對等資料會以扁平化樹狀結構的分支識別。</span><span class="sxs-lookup"><span data-stu-id="cd225-192">Peer data is identified by branching of the flattened tree.</span></span>  
  
 <span data-ttu-id="cd225-193">如需詳細資訊，請參閱 [資料表、矩陣和清單 &#40;報表產生器及 SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="cd225-193">For more information, see [Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="atom-rendering-rules"></a><a name="AtomRendering"></a> <span data-ttu-id="cd225-194">Atom 轉譯規則</span><span class="sxs-lookup"><span data-stu-id="cd225-194">Atom Rendering Rules</span></span>  
 <span data-ttu-id="cd225-195">轉譯資料摘要時，Atom 轉譯延伸模組會忽略下列資訊：</span><span class="sxs-lookup"><span data-stu-id="cd225-195">The Atom rendering extension ignores the following information when rendering a data feed:</span></span>  
  
-   <span data-ttu-id="cd225-196">格式和配置</span><span class="sxs-lookup"><span data-stu-id="cd225-196">Formatting and layout</span></span>  
  
-   <span data-ttu-id="cd225-197">頁首</span><span class="sxs-lookup"><span data-stu-id="cd225-197">Page header</span></span>  
  
-   <span data-ttu-id="cd225-198">頁尾</span><span class="sxs-lookup"><span data-stu-id="cd225-198">Page footer</span></span>  
  
-   <span data-ttu-id="cd225-199">自訂報表項目</span><span class="sxs-lookup"><span data-stu-id="cd225-199">Custom report items</span></span>  
  
-   <span data-ttu-id="cd225-200">矩形</span><span class="sxs-lookup"><span data-stu-id="cd225-200">Rectangles</span></span>  
  
-   <span data-ttu-id="cd225-201">線條</span><span class="sxs-lookup"><span data-stu-id="cd225-201">Lines</span></span>  
  
-   <span data-ttu-id="cd225-202">影像</span><span class="sxs-lookup"><span data-stu-id="cd225-202">Images</span></span>  
  
-   <span data-ttu-id="cd225-203">自動小計</span><span class="sxs-lookup"><span data-stu-id="cd225-203">Automatic subtotals</span></span>  
  
 <span data-ttu-id="cd225-204">其餘的報表項目會先由上至下，再由左至右排序。</span><span class="sxs-lookup"><span data-stu-id="cd225-204">The remaining report items are sorted, from top to bottom, and then left to right.</span></span> <span data-ttu-id="cd225-205">接著，每個項目會轉譯成資料行。</span><span class="sxs-lookup"><span data-stu-id="cd225-205">Each item is then rendered to a column.</span></span> <span data-ttu-id="cd225-206">如果報表有巢狀資料項目 (例如，清單或資料表)，則父項目會在每一個資料列中重複。</span><span class="sxs-lookup"><span data-stu-id="cd225-206">If the report has nested data items like lists or tables, the parent items are repeated on each row.</span></span>  
  
 <span data-ttu-id="cd225-207">下表指出報表項目轉譯時的外觀：</span><span class="sxs-lookup"><span data-stu-id="cd225-207">The following table indicates the appearance of report items when rendered:</span></span>  
  
|<span data-ttu-id="cd225-208">項目</span><span class="sxs-lookup"><span data-stu-id="cd225-208">Item</span></span>|<span data-ttu-id="cd225-209">轉譯行為</span><span class="sxs-lookup"><span data-stu-id="cd225-209">Rendering behavior</span></span>|  
|----------|------------------------|  
|<span data-ttu-id="cd225-210">資料表</span><span class="sxs-lookup"><span data-stu-id="cd225-210">Table</span></span>|<span data-ttu-id="cd225-211">藉由展開資料表，並為每個資料列與資料行以最低層級的詳細資料建立資料列與資料行，來進行轉譯。</span><span class="sxs-lookup"><span data-stu-id="cd225-211">Renders by expanding the table and creating a row and column for each row and column at the lowest level of detail.</span></span> <span data-ttu-id="cd225-212">小計資料列和資料行沒有資料行或資料列標題。</span><span class="sxs-lookup"><span data-stu-id="cd225-212">Subtotal rows and columns do not have column or row headings.</span></span> <span data-ttu-id="cd225-213">不支援鑽研報表。</span><span class="sxs-lookup"><span data-stu-id="cd225-213">Drillthrough reports are not supported.</span></span>|  
|<span data-ttu-id="cd225-214">Matrix</span><span class="sxs-lookup"><span data-stu-id="cd225-214">Matrix</span></span>|<span data-ttu-id="cd225-215">藉由展開矩陣，並為每個資料列與資料行以最低層級的詳細資料建立資料列與資料行，來進行轉譯。</span><span class="sxs-lookup"><span data-stu-id="cd225-215">Renders by expanding the matrix and creating a row and column for each row and column at the lowest level of detail.</span></span> <span data-ttu-id="cd225-216">小計資料列和資料行沒有資料行或資料列標題。</span><span class="sxs-lookup"><span data-stu-id="cd225-216">Subtotal rows and columns do not have column or row headings.</span></span>|  
|<span data-ttu-id="cd225-217">清單</span><span class="sxs-lookup"><span data-stu-id="cd225-217">List</span></span>|<span data-ttu-id="cd225-218">轉譯每個詳細資料列或清單中執行個體的記錄。</span><span class="sxs-lookup"><span data-stu-id="cd225-218">Renders a record for each detail row or instance in the list.</span></span>|  
|<span data-ttu-id="cd225-219">子報表</span><span class="sxs-lookup"><span data-stu-id="cd225-219">Subreport</span></span>|<span data-ttu-id="cd225-220">內容的每個執行個體都會重複父項目。</span><span class="sxs-lookup"><span data-stu-id="cd225-220">The parent item is repeated for each instance of the contents.</span></span>|  
|<span data-ttu-id="cd225-221">圖表</span><span class="sxs-lookup"><span data-stu-id="cd225-221">Chart</span></span>|<span data-ttu-id="cd225-222">以每個圖表值的所有圖表標籤轉譯記錄。</span><span class="sxs-lookup"><span data-stu-id="cd225-222">Renders a record with all chart labels for each chart value.</span></span> <span data-ttu-id="cd225-223">階層中數列和類別目錄的標籤會扁平化，並且包含在圖表值的資料列中。</span><span class="sxs-lookup"><span data-stu-id="cd225-223">Labels from series and categories in hierarchies are flattened and included in the row for a chart value.</span></span>|  
|<span data-ttu-id="cd225-224">資料橫條</span><span class="sxs-lookup"><span data-stu-id="cd225-224">Data bar</span></span>|<span data-ttu-id="cd225-225">像圖表一樣轉譯。</span><span class="sxs-lookup"><span data-stu-id="cd225-225">Renders like a chart.</span></span> <span data-ttu-id="cd225-226">資料橫條通常不包含階層或標籤。</span><span class="sxs-lookup"><span data-stu-id="cd225-226">Typically, a data bar does not include hierarchies or labels.</span></span>|  
|<span data-ttu-id="cd225-227">走勢圖</span><span class="sxs-lookup"><span data-stu-id="cd225-227">Sparkline</span></span>|<span data-ttu-id="cd225-228">像圖表一樣轉譯。</span><span class="sxs-lookup"><span data-stu-id="cd225-228">Renders like a chart.</span></span> <span data-ttu-id="cd225-229">走勢圖通常不包含階層或標籤。</span><span class="sxs-lookup"><span data-stu-id="cd225-229">Typically, a sparkline does not include hierarchies or labels.</span></span>|  
|<span data-ttu-id="cd225-230">量測計</span><span class="sxs-lookup"><span data-stu-id="cd225-230">Gauge</span></span>|<span data-ttu-id="cd225-231">轉譯為包含線性標尺的最小與最大值、範圍的開始與結束值，以及指標值的單一記錄。</span><span class="sxs-lookup"><span data-stu-id="cd225-231">Renders as a single record with the minimum and maximum values of the linear scale, start and end values of the range, and the value of the pointer.</span></span>|  
|<span data-ttu-id="cd225-232">指標</span><span class="sxs-lookup"><span data-stu-id="cd225-232">Indicator</span></span>|<span data-ttu-id="cd225-233">以作用中的狀態名稱、可用的狀態以及資料值轉譯成單一記錄。</span><span class="sxs-lookup"><span data-stu-id="cd225-233">Renders as a single record with the active state name, available states, and the data value.</span></span>|  
|<span data-ttu-id="cd225-234">對應</span><span class="sxs-lookup"><span data-stu-id="cd225-234">Map</span></span>|<span data-ttu-id="cd225-235">針對每一個地圖資料區域產生資料摘要。</span><span class="sxs-lookup"><span data-stu-id="cd225-235">Generates a data feed for each map data region.</span></span> <span data-ttu-id="cd225-236">如果多個地圖圖層使用相同的資料區域，則資料摘要會包含所有地圖圖層。</span><span class="sxs-lookup"><span data-stu-id="cd225-236">If multiple map layers use the same data region, the data feed includes all of them.</span></span> <span data-ttu-id="cd225-237">此資料摘要包含一筆記錄，其中包含地圖圖層之每一個地圖成員的標籤和值。</span><span class="sxs-lookup"><span data-stu-id="cd225-237">The data feed includes a record with the labels and values for each map member of the map layer.</span></span>|  
  

  
##  <a name="device-information-settings"></a><a name="DeviceInfo"></a><span data-ttu-id="cd225-238">裝置資訊設定</span><span class="sxs-lookup"><span data-stu-id="cd225-238">Device Information Settings</span></span>  
 <span data-ttu-id="cd225-239">您可以變更此轉譯器的某些預設設定，包括要使用的編碼結構描述。</span><span class="sxs-lookup"><span data-stu-id="cd225-239">You can change some default settings for this renderer, including the encoding schema to use.</span></span> <span data-ttu-id="cd225-240">如需詳細資訊，請參閱 [ATOM Device Information Settings](../atom-device-information-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="cd225-240">For more information, see [ATOM Device Information Settings](../atom-device-information-settings.md).</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="cd225-241">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd225-241">See Also</span></span>  
 <span data-ttu-id="cd225-242">[匯出至 CSV 檔案 &#40;報表產生器及 SSRS&#41;](exporting-to-a-csv-file-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="cd225-242">[Exporting to a CSV File &#40;Report Builder and SSRS&#41;](exporting-to-a-csv-file-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="cd225-243">匯出報表 &#40;報表產生器和 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="cd225-243">Exporting Reports &#40;Report Builder and SSRS&#41;</span></span>](export-reports-report-builder-and-ssrs.md)  
  
  
