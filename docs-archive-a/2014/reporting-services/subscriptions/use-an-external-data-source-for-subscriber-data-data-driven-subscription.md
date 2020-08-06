---
title: 使用外部資料來源以取得訂閱者資料 (資料驅動訂閱) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriber data sources [Reporting Services]
- subscriptions [Reporting Services], external data sources
- query-based subscriptions [Reporting Services]
- external data sources [Reporting Services]
- data-driven subscriptions
- data sources [Reporting Services], subscriptions
ms.assetid: 1cade8ec-729c-4df8-a428-e75c9ad86369
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e23da709289ffb6ca345bb6211f40388877a1a87
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706965"
---
# <a name="use-an-external-data-source-for-subscriber-data-data-driven-subscription"></a><span data-ttu-id="92e8e-102">使用外部資料來源以取得訂閱者資料 (資料驅動訂閱)</span><span class="sxs-lookup"><span data-stu-id="92e8e-102">Use an External Data Source for Subscriber Data (Data-Driven Subscription)</span></span>
  <span data-ttu-id="92e8e-103">在資料驅動訂閱中，動態訂閱資料是由從外部資料來源擷取資料的查詢或命令所提供。</span><span class="sxs-lookup"><span data-stu-id="92e8e-103">In a data-driven subscription, dynamic subscription data is provided by a query or command that retrieves data from an external data source.</span></span> <span data-ttu-id="92e8e-104">訂閱資料可以從任何支援的資料來源 (符合資料驅動訂閱處理的需求) 中擷取。</span><span class="sxs-lookup"><span data-stu-id="92e8e-104">Subscription data can be retrieved from any supported data source that meets the requirements for data-driven subscription processing.</span></span> <span data-ttu-id="92e8e-105">查詢或命令語法必須對安裝在您報表伺服器上的資料處理延伸模組有效。</span><span class="sxs-lookup"><span data-stu-id="92e8e-105">The query or command syntax must be valid for a data processing extension installed with your report server.</span></span>  
  
## <a name="data-processing-requirements"></a><span data-ttu-id="92e8e-106">資料處理需求</span><span class="sxs-lookup"><span data-stu-id="92e8e-106">Data Processing Requirements</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="92e8e-107">會使用資料處理延伸模組來擷取訂閱資料。</span><span class="sxs-lookup"><span data-stu-id="92e8e-107">uses data processing extensions to retrieve subscription data.</span></span> <span data-ttu-id="92e8e-108">建議的資料來源類型包含下列幾種：</span><span class="sxs-lookup"><span data-stu-id="92e8e-108">Recommended data source types include the following:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="92e8e-109">關聯式資料庫</span><span class="sxs-lookup"><span data-stu-id="92e8e-109">relational databases</span></span>  
  
-   <span data-ttu-id="92e8e-110">Oracle 資料庫</span><span class="sxs-lookup"><span data-stu-id="92e8e-110">Oracle databases</span></span>  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="92e8e-111">多維度和資料採礦資料來源</span><span class="sxs-lookup"><span data-stu-id="92e8e-111">multidimensional and data mining data sources</span></span>  
  
-   <span data-ttu-id="92e8e-112">XML 資料來源</span><span class="sxs-lookup"><span data-stu-id="92e8e-112">XML data sources</span></span>  
  
     <span data-ttu-id="92e8e-113">使用訂閱者資料的 XML 資料處理延伸模組時，請務必增加訂閱中的查詢逾時設定。</span><span class="sxs-lookup"><span data-stu-id="92e8e-113">When using the XML data processing extension for subscriber data, be sure to increase the query timeout settings in the subscription.</span></span> <span data-ttu-id="92e8e-114">XML 資料處理延伸模組所使用查詢逾時值的單位是毫秒，而不是秒。</span><span class="sxs-lookup"><span data-stu-id="92e8e-114">The XML data processing extension uses milliseconds rather than seconds for query timeout values.</span></span> <span data-ttu-id="92e8e-115">如果沒有增加逾時值，訂閱可能會因為處理時間不足而失敗。</span><span class="sxs-lookup"><span data-stu-id="92e8e-115">If you do not increase the timeout value, the subscription might fail due to insufficient processing time.</span></span>  
  
     <span data-ttu-id="92e8e-116">設定訂閱者資料來源的連接時，請避免使用 **[不需要認證]** 選項。</span><span class="sxs-lookup"><span data-stu-id="92e8e-116">Avoid using the **Credentials are not required** option when configuring the connection to the subscriber data source.</span></span> <span data-ttu-id="92e8e-117">使用 XML 資料處理延伸模組在執行階段擷取訂閱資料時，建議您使用預存認證。</span><span class="sxs-lookup"><span data-stu-id="92e8e-117">Stored credentials are recommended when using the XML data processing extension to retrieve subscription data at run time.</span></span>  
  
 <span data-ttu-id="92e8e-118">您或許可以使用其他支援的資料來源類型，但不保證它們全部都能執行。</span><span class="sxs-lookup"><span data-stu-id="92e8e-118">You might be able to use other supported data source types, but not all of them are guaranteed to work.</span></span> <span data-ttu-id="92e8e-119">例如，訂閱者資料就無法使用下列資料來源類型：</span><span class="sxs-lookup"><span data-stu-id="92e8e-119">For example, the following data source types cannot be used for subscriber data:</span></span>  
  
-   <span data-ttu-id="92e8e-120">SAP Netweaver BI 資料庫</span><span class="sxs-lookup"><span data-stu-id="92e8e-120">SAP Netweaver BI databases</span></span>  
  
-   <span data-ttu-id="92e8e-121">報表模型</span><span class="sxs-lookup"><span data-stu-id="92e8e-121">report models</span></span>  
  
 <span data-ttu-id="92e8e-122">如果您希望在資料驅動訂閱中使用自訂的資料處理延伸模組，則該延伸模組必須實作 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand> 和 <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> 介面。</span><span class="sxs-lookup"><span data-stu-id="92e8e-122">If you have a custom data processing extension that you want to use in data-driven subscriptions, it must implement the <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand> and the <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> interfaces.</span></span> <span data-ttu-id="92e8e-123">該資料處理延伸模組必須支援僅限結構描述的查詢執行。</span><span class="sxs-lookup"><span data-stu-id="92e8e-123">The data processing extension must support a schema-only query execution.</span></span> <span data-ttu-id="92e8e-124">此查詢是用於在設計階段擷取資料行中繼資料，因此使用者可以將資料行對應至訂閱定義中的傳遞選項以及報表參數。</span><span class="sxs-lookup"><span data-stu-id="92e8e-124">This query is used to retrieve column metadata at design-time so that users can map columns to delivery options and report parameters in the subscription definition.</span></span> <span data-ttu-id="92e8e-125">僅限結構描述的查詢執行會發生在使用者定義訂閱的初期階段。</span><span class="sxs-lookup"><span data-stu-id="92e8e-125">Schema-only query execution occurs at an early stage when the user is defining the subscription.</span></span>  
  
## <a name="query-requirements"></a><span data-ttu-id="92e8e-126">查詢需求</span><span class="sxs-lookup"><span data-stu-id="92e8e-126">Query Requirements</span></span>  
 <span data-ttu-id="92e8e-127">當您建立擷取訂閱資料的查詢時，請牢記下列幾點：</span><span class="sxs-lookup"><span data-stu-id="92e8e-127">When creating query that retrieves subscription data, keep the following points in mind:</span></span>  
  
-   <span data-ttu-id="92e8e-128">您只能針對該訂閱建立一個查詢。</span><span class="sxs-lookup"><span data-stu-id="92e8e-128">You can only create one query for the subscription.</span></span>  
  
-   <span data-ttu-id="92e8e-129">該查詢必須傳回所有您要用於傳遞選項以及指定報表參數的值。</span><span class="sxs-lookup"><span data-stu-id="92e8e-129">The query must return all of the values that you want to use for delivery options and for specifying report parameters.</span></span>  
  
-   <span data-ttu-id="92e8e-130">報表伺服器將在結果集內為每一個資料列建立報表傳遞。</span><span class="sxs-lookup"><span data-stu-id="92e8e-130">The report server will create a report delivery for every row in the result set.</span></span> <span data-ttu-id="92e8e-131">如果結果集是由三百個資料列組成，則報表伺服器將會嘗試傳遞三百個報表。</span><span class="sxs-lookup"><span data-stu-id="92e8e-131">If the result set consists of three hundred rows, the report server will attempt to deliver three hundred reports.</span></span>  
  
## <a name="setting-delivery-options-using-variable-data-from-a-subscriber-database"></a><span data-ttu-id="92e8e-132">使用訂閱者資料庫的變數資料建立傳遞選項</span><span class="sxs-lookup"><span data-stu-id="92e8e-132">Setting Delivery Options Using Variable Data from a Subscriber Database</span></span>  
 <span data-ttu-id="92e8e-133">您可以使用訂閱者資料庫中的資料，自訂每一個收件者的傳遞選項。</span><span class="sxs-lookup"><span data-stu-id="92e8e-133">You can use data in the subscriber database to customize delivery options for each recipient.</span></span> <span data-ttu-id="92e8e-134">所使用的傳遞延伸模組種類會決定可用的選項。</span><span class="sxs-lookup"><span data-stu-id="92e8e-134">The kind of delivery extension you are using determines which options are available.</span></span> <span data-ttu-id="92e8e-135">如果您使用報表伺服器電子郵件傳遞延伸模組，則查詢應包含每一個訂閱者的電子郵件別名。</span><span class="sxs-lookup"><span data-stu-id="92e8e-135">If you are using the report server e-mail delivery extension, the query should contain an e-mail alias for each subscriber.</span></span> <span data-ttu-id="92e8e-136">如果您使用檔案共用傳遞，訂閱者資料應包含可用來建立訂閱者特定報表檔案或提供傳遞目的地的值。</span><span class="sxs-lookup"><span data-stu-id="92e8e-136">If you are using file share delivery, the subscriber data should include values that can be used to create subscriber-specific report files or to provide a destination for the delivery.</span></span> <span data-ttu-id="92e8e-137">如需詳細資訊，請參閱 Reporting Services 中的檔案[共用傳遞](file-share-delivery-in-reporting-services.md)和[Reporting Services 中的電子郵件傳遞](e-mail-delivery-in-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="92e8e-137">For more information, see [File Share Delivery in Reporting Services](file-share-delivery-in-reporting-services.md) and [E-Mail Delivery in Reporting Services](e-mail-delivery-in-reporting-services.md).</span></span>  
  
## <a name="passing-parameter-values-from-the-subscriber-database-to-the-report"></a><span data-ttu-id="92e8e-138">將參數值從訂閱者資料庫傳遞到報表</span><span class="sxs-lookup"><span data-stu-id="92e8e-138">Passing Parameter Values from the Subscriber Database to the Report</span></span>  
 <span data-ttu-id="92e8e-139">如果正在建立參數化報表的資料驅動訂閱，則可以使用可變個數參數值來自訂每份報表的輸出。</span><span class="sxs-lookup"><span data-stu-id="92e8e-139">If you are creating a data-driven subscription for a parameterized report, you can use variable parameter values to customize the output of each report.</span></span> <span data-ttu-id="92e8e-140">例如，訂閱者資料庫可能包含可用來篩選報表資料的員工識別碼、雇用日期、職稱和辦公室位置資訊。</span><span class="sxs-lookup"><span data-stu-id="92e8e-140">For example, the subscriber database might contain employee identification numbers, hire dates, job titles, and office location information that can be used to filter report data.</span></span> <span data-ttu-id="92e8e-141">如果報表接受以這些或其他可用的資料行資料為基礎的參數，您就可以將參數對應到適當的資料行。</span><span class="sxs-lookup"><span data-stu-id="92e8e-141">If the report accepts parameters that are based on these or other available column data, you can map the parameter to the appropriate column.</span></span>  
  
 <span data-ttu-id="92e8e-142">將訂閱者欄位對應至報表參數時，請確定資料類型與資料行長度相容。</span><span class="sxs-lookup"><span data-stu-id="92e8e-142">When mapping subscriber fields to report parameters, make sure that the data types and column lengths are compatible.</span></span> <span data-ttu-id="92e8e-143">如果資料類型不符合，訂閱處理期間會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="92e8e-143">If there is a data type mismatch, an error will occur during subscription processing.</span></span> <span data-ttu-id="92e8e-144">若要深入了解如何使用參數化報表中的訂閱者資料，請參閱[建立資料驅動訂閱 &#40;SSRS 教學課程&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="92e8e-144">To learn more about using subscriber data in a parameterized report, see [Create a Data-Driven Subscription &#40;SSRS Tutorial&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md).</span></span>  
  
## <a name="modifying-the-subscriber-data-source"></a><span data-ttu-id="92e8e-145">修改訂閱者資料來源</span><span class="sxs-lookup"><span data-stu-id="92e8e-145">Modifying the Subscriber Data Source</span></span>  
 <span data-ttu-id="92e8e-146">下列對訂閱者資料來源的修改會妨礙訂閱執行：</span><span class="sxs-lookup"><span data-stu-id="92e8e-146">The following modifications to the subscriber data source can prevent the subscription from running:</span></span>  
  
-   <span data-ttu-id="92e8e-147">移除在訂閱中所參考的資料行。</span><span class="sxs-lookup"><span data-stu-id="92e8e-147">Removing columns that are referenced in the subscription.</span></span>  
  
-   <span data-ttu-id="92e8e-148">修改資料來源的資料表結構。</span><span class="sxs-lookup"><span data-stu-id="92e8e-148">Modifying the table structure of the data source.</span></span>  
  
-   <span data-ttu-id="92e8e-149">變更其他資料行屬性的資料類型。</span><span class="sxs-lookup"><span data-stu-id="92e8e-149">Changing data type and other column properties.</span></span>  
  
 <span data-ttu-id="92e8e-150">如果您做了其中的任一變更，就必須更新訂閱。</span><span class="sxs-lookup"><span data-stu-id="92e8e-150">If you make any of these changes, you must update the subscription.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92e8e-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92e8e-151">See Also</span></span>  
 <span data-ttu-id="92e8e-152">[建立、修改和刪除資料驅動訂閱](data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="92e8e-152">[Create, Modify, and Delete a Data-Driven Subscription](data-driven-subscriptions.md) </span></span>  
 <span data-ttu-id="92e8e-153">[Data-Driven Subscriptions](data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="92e8e-153">[Data-Driven Subscriptions](data-driven-subscriptions.md) </span></span>  
 [<span data-ttu-id="92e8e-154">訂閱與傳遞 &#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="92e8e-154">Subscriptions and Delivery &#40;Reporting Services&#41;</span></span>](subscriptions-and-delivery-reporting-services.md)  
  
  
