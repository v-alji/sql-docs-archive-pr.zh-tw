---
title: ODBC 來源 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcsource.f1
ms.assetid: abcf34eb-9140-4100-82e6-b85bccd22abe
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 792557839d60f34bdf944dab150959d4df7cb8cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593483"
---
# <a name="odbc-source"></a><span data-ttu-id="fac38-102">ODBC 來源</span><span class="sxs-lookup"><span data-stu-id="fac38-102">ODBC Source</span></span>
  <span data-ttu-id="fac38-103">ODBC 來源會使用資料庫資料表、檢視或 SQL 陳述式，從 ODBC 支援的資料庫中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="fac38-103">The ODBC source extracts data from ODBC-supported database by using a database table, a view, or an SQL statement.</span></span>  
  
 <span data-ttu-id="fac38-104">ODBC 來源有下列資料存取模式可供擷取資料：</span><span class="sxs-lookup"><span data-stu-id="fac38-104">The ODBC source has the following data access modes for extracting data:</span></span>  
  
-   <span data-ttu-id="fac38-105">資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="fac38-105">A table or view.</span></span>  
  
-   <span data-ttu-id="fac38-106">SQL 陳述式的結果。</span><span class="sxs-lookup"><span data-stu-id="fac38-106">The results of an SQL statement.</span></span>  
  
 <span data-ttu-id="fac38-107">來源使用 ODBC 連接管理員，指定要使用的提供者。</span><span class="sxs-lookup"><span data-stu-id="fac38-107">The source uses an ODBC connection manager, which specifies the provider to use.</span></span>  
  
 <span data-ttu-id="fac38-108">ODBC 來源包含來源資料輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="fac38-108">An ODBC source includes the source data output columns.</span></span> <span data-ttu-id="fac38-109">在 ODBC 目的地中將輸入資料行對應到目的地資料行時，如果沒有輸入資料行對應到目的地資料行，可能會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="fac38-109">When output columns are mapped in the ODBC destination to the destination columns, errors may occur if no output columns are mapped to the destination columns.</span></span> <span data-ttu-id="fac38-110">可對應不同類型的資料行，但是如果輸出資料與目的地不相容，在執行階段會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="fac38-110">Columns of different types can be mapped, however if the output data is not compatible for the destination then an error occurs at runtime.</span></span> <span data-ttu-id="fac38-111">根據錯誤行為設定，錯誤會被忽略，導致失敗，或者資料列會傳送至錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="fac38-111">Depending on the error behavior, setting the error will be ignored, cause a failure, or the row is sent to the error output.</span></span>  
  
 <span data-ttu-id="fac38-112">ODBC 來源有一個一般輸出和一個錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="fac38-112">The ODBC source has one regular output and one error output.</span></span>  
  
## <a name="error-handling"></a><span data-ttu-id="fac38-113">錯誤處理</span><span class="sxs-lookup"><span data-stu-id="fac38-113">Error Handling</span></span>  
 <span data-ttu-id="fac38-114">ODBC 來源有錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="fac38-114">The ODBC source has an error output.</span></span> <span data-ttu-id="fac38-115">此元件的錯誤輸出包含下列輸出資料行：</span><span class="sxs-lookup"><span data-stu-id="fac38-115">The component error output includes the following output columns:</span></span>  
  
-   <span data-ttu-id="fac38-116">**錯誤碼**：對應至目前錯誤的編號。</span><span class="sxs-lookup"><span data-stu-id="fac38-116">**Error Code**: The number that corresponds to the current error.</span></span> <span data-ttu-id="fac38-117">請參閱 ODBC 支援的資料庫的文件集，以取得錯誤清單。</span><span class="sxs-lookup"><span data-stu-id="fac38-117">See the documentation for the ODBC-supported database you are using for a list of errors.</span></span> <span data-ttu-id="fac38-118">如需 SSIS 錯誤碼清單，請參閱＜SSIS 錯誤碼和訊息參考＞。</span><span class="sxs-lookup"><span data-stu-id="fac38-118">For a list of SSIS error codes, see the SSIS Error Code and Message Reference.</span></span>  
  
-   <span data-ttu-id="fac38-119">**錯誤資料行**：造成錯誤 (用於轉換錯誤) 的來源資料行。</span><span class="sxs-lookup"><span data-stu-id="fac38-119">**Error Column**: The source column causing the error (for conversion errors).</span></span>  
  
-   <span data-ttu-id="fac38-120">標準輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="fac38-120">The standard output data columns.</span></span>  
  
 <span data-ttu-id="fac38-121">根據錯誤行為設定，ODBC 來源支援在錯誤輸出中傳回擷取程序期間發生的錯誤 (資料轉換、截斷)。</span><span class="sxs-lookup"><span data-stu-id="fac38-121">Depending on the error behavior setting, the ODBC source supports returning errors (data conversion, truncation) that occur during the extraction process in the error output.</span></span> <span data-ttu-id="fac38-122">如需詳細資訊，請參閱 [ODBC 目的地編輯器 &#40;連線管理員頁面&#41;](../odbc-destination-editor-connection-manager-page.md)。</span><span class="sxs-lookup"><span data-stu-id="fac38-122">For more information, see [ODBC Destination Editor &#40;Connection Manager Page&#41;](../odbc-destination-editor-connection-manager-page.md).</span></span>  
  
## <a name="data-type-support"></a><span data-ttu-id="fac38-123">資料類型支援</span><span class="sxs-lookup"><span data-stu-id="fac38-123">Data Type Support</span></span>  
 <span data-ttu-id="fac38-124">如需有關 ODBC 來源支援之資料類型的資訊，請參閱＜Connector for Open Database Connectivity (ODBC) by Attunity＞。</span><span class="sxs-lookup"><span data-stu-id="fac38-124">For information about the data types supported by the ODBC source, see Connector for Open Database Connectivity (ODBC) by Attunity.</span></span>  
  
## <a name="extract-options"></a><span data-ttu-id="fac38-125">擷取選項</span><span class="sxs-lookup"><span data-stu-id="fac38-125">Extract Options</span></span>  
 <span data-ttu-id="fac38-126">ODBC 來源以 [批次]  或 [逐列]  模式操作。</span><span class="sxs-lookup"><span data-stu-id="fac38-126">The ODBC source operates in either **Batch** or **Row-by-Row** mode.</span></span> <span data-ttu-id="fac38-127">所用的模式是由 **FetchMethod** 屬性所決定。</span><span class="sxs-lookup"><span data-stu-id="fac38-127">The mode used is determined by the **FetchMethod** property.</span></span> <span data-ttu-id="fac38-128">下列清單描述這些模式。</span><span class="sxs-lookup"><span data-stu-id="fac38-128">The following list describes the modes.</span></span>  
  
-   <span data-ttu-id="fac38-129">**批次**：元件會根據所見的 ODBC 提供者功能，嘗試使用最有效率的提取方法。</span><span class="sxs-lookup"><span data-stu-id="fac38-129">**Batch**: The component attempts to use the most efficient fetch method based on the perceived ODBC provider capabilities.</span></span> <span data-ttu-id="fac38-130">對於最新型的 ODBC 提供者，這是 SQLFetchScroll 與陣列繫結搭配使用 (陣列大小是由 **BatchSize** 屬性所決定)。</span><span class="sxs-lookup"><span data-stu-id="fac38-130">For most modern ODBC providers, this is SQLFetchScroll with array binding (where the array size is determined by the **BatchSize** property).</span></span> <span data-ttu-id="fac38-131">如果您選取 [批次]  ，而提供者不支援此方法，ODBC 目的地會自動切換為**逐列**模式。</span><span class="sxs-lookup"><span data-stu-id="fac38-131">If you select **Batch** and the provider does not support this method, the ODBC destination automatically switches to the **Row-by-row** mode.</span></span>  
  
-   <span data-ttu-id="fac38-132">**逐列**：元件會使用 SQLFetch，一次擷取一個資料列。</span><span class="sxs-lookup"><span data-stu-id="fac38-132">**Row-by Row**: The component uses SQLFetch to retrieve the rows one at a time.</span></span>  
  
 <span data-ttu-id="fac38-133">如需有關 **FetchMethod** 屬性的詳細資訊，請參閱＜ [ODBC Source Custom Properties](odbc-source-custom-properties.md)＞。</span><span class="sxs-lookup"><span data-stu-id="fac38-133">For more information about the **FetchMethod** property, see [ODBC Source Custom Properties](odbc-source-custom-properties.md).</span></span>  
  
## <a name="parallelism"></a><span data-ttu-id="fac38-134">平行處理原則</span><span class="sxs-lookup"><span data-stu-id="fac38-134">Parallelism</span></span>  
 <span data-ttu-id="fac38-135">可針對相同電腦或不同電腦上的相同資料表或不同資料表平行執行的 ODBC 來源元件數目不受限制 (除了一般全域工作階段限制之外)。</span><span class="sxs-lookup"><span data-stu-id="fac38-135">There is no limitation on the number of ODBC source components that can run in parallel against the same table or different tables, on the same machine or on different machines (other than normal global session limits).</span></span>  
  
 <span data-ttu-id="fac38-136">然而，所使用的 ODBC 提供者的限制可能會限制透過提供者的並行連接數目。</span><span class="sxs-lookup"><span data-stu-id="fac38-136">However, limitations of the ODBC provider being used may restrict the number of concurrent connections through the provider.</span></span> <span data-ttu-id="fac38-137">這些限制會限制 ODBC 來源支援的平行執行個體數目。</span><span class="sxs-lookup"><span data-stu-id="fac38-137">These limitations limit the number of supported parallel instances possible for the ODBC source.</span></span> <span data-ttu-id="fac38-138">SSIS 開發人員必須知道所使用的任何 ODBC 提供者的限制，並在建立 SSIS 封裝時將這些限制納入考量。</span><span class="sxs-lookup"><span data-stu-id="fac38-138">The SSIS developer must be aware of the limitations of any ODBC provider being used and take them into consideration when building SSIS packages.</span></span>  
  
## <a name="troubleshooting-the-odbc-source"></a><span data-ttu-id="fac38-139">ODBC 來源的疑難排解</span><span class="sxs-lookup"><span data-stu-id="fac38-139">Troubleshooting the ODBC Source</span></span>  
 <span data-ttu-id="fac38-140">您可以記錄 ODBC 來源對外部資料提供者所執行的呼叫。</span><span class="sxs-lookup"><span data-stu-id="fac38-140">You can log the calls that the ODBC source makes to external data providers.</span></span> <span data-ttu-id="fac38-141">您可以使用這項記錄功能，疑難排解 ODBC 來源執行的從外部資料來源載入資料的作業。</span><span class="sxs-lookup"><span data-stu-id="fac38-141">You can use this logging capability to troubleshoot the loading of data from external data sources that the ODBC source performs.</span></span> <span data-ttu-id="fac38-142">若要記錄 ODBC 來源對外部資料提供者執行的呼叫，請啟用 ODBC 驅動程式管理員追蹤。</span><span class="sxs-lookup"><span data-stu-id="fac38-142">To log the calls that the ODBC source makes to external data providers, enable the ODBC driver manager trace.</span></span> <span data-ttu-id="fac38-143">如需詳細資訊，請參閱 Microsoft 文件集＜如何使用 ODBC 資料來源管理員產生 ODBC 追蹤＞。 </span><span class="sxs-lookup"><span data-stu-id="fac38-143">For more information, see the Microsoft documentation on *How To Generate an ODBC Trace with ODBC the Data Source Administrator.*</span></span>  
  
## <a name="configuring-the-odbc-source"></a><span data-ttu-id="fac38-144">設定 ODBC 來源</span><span class="sxs-lookup"><span data-stu-id="fac38-144">Configuring the ODBC Source</span></span>  
 <span data-ttu-id="fac38-145">您可以透過程式設計方式或 SSIS 設計師來設定 ODBC 來源。</span><span class="sxs-lookup"><span data-stu-id="fac38-145">You can configure the ODBC source programmatically or through the SSIS Designer.</span></span>  
  
 <span data-ttu-id="fac38-146">如需詳細資訊，請參閱下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="fac38-146">For more information, see one of the following topics:</span></span>  
  
-   [<span data-ttu-id="fac38-147">ODBC 來源編輯器 &#40;連線管理員頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="fac38-147">ODBC Source Editor &#40;Connection Manager Page&#41;</span></span>](../odbc-source-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="fac38-148">ODBC 來源編輯器 &#40;資料行頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="fac38-148">ODBC Source Editor &#40;Columns Page&#41;</span></span>](../odbc-source-editor-columns-page.md)  
  
-   [<span data-ttu-id="fac38-149">ODBC 來源編輯器 &#40;錯誤輸出頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="fac38-149">ODBC Source Editor &#40;Error Output Page&#41;</span></span>](../odbc-source-editor-error-output-page.md)  
  
 <span data-ttu-id="fac38-150">**[進階編輯器]** 對話方塊包含可以程式設計方式設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="fac38-150">The **Advanced Editor** dialog box contains the properties that can be set programmatically.</span></span>  
  
 <span data-ttu-id="fac38-151">若要開啟 **[進階編輯器]** 對話方塊：</span><span class="sxs-lookup"><span data-stu-id="fac38-151">To open the **Advanced Editor** dialog box:</span></span>  
  
-   <span data-ttu-id="fac38-152">在 **專案的** [資料流程] [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 畫面中，以滑鼠右鍵按一下 ODBC 來源，然後選取 **[顯示進階編輯器]**。</span><span class="sxs-lookup"><span data-stu-id="fac38-152">In the **Data Flow** screen of your [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] project, right click the ODBC source and select **Show Advanced Editor**.</span></span>  
  
 <span data-ttu-id="fac38-153">如需有關可在 [進階編輯器] 對話方塊中設定之屬性的詳細資訊，請參閱＜ [ODBC Source Custom Properties](odbc-source-custom-properties.md)＞。</span><span class="sxs-lookup"><span data-stu-id="fac38-153">For more information about the properties that you can set in the Advanced Editor dialog box, see [ODBC Source Custom Properties](odbc-source-custom-properties.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fac38-154">本節內容</span><span class="sxs-lookup"><span data-stu-id="fac38-154">In This Section</span></span>  
  
-   [<span data-ttu-id="fac38-155">ODBC 來源編輯器 &#40;錯誤輸出頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="fac38-155">ODBC Source Editor &#40;Error Output Page&#41;</span></span>](../odbc-source-editor-error-output-page.md)  
  
-   [<span data-ttu-id="fac38-156">ODBC 來源編輯器 &#40;資料行頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="fac38-156">ODBC Source Editor &#40;Columns Page&#41;</span></span>](../odbc-source-editor-columns-page.md)  
  
-   [<span data-ttu-id="fac38-157">ODBC 來源編輯器 &#40;連線管理員頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="fac38-157">ODBC Source Editor &#40;Connection Manager Page&#41;</span></span>](../odbc-source-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="fac38-158">使用 ODBC 來源來擷取資料</span><span class="sxs-lookup"><span data-stu-id="fac38-158">Extract Data by Using the ODBC Source</span></span>](odbc-source.md)  
  
-   [<span data-ttu-id="fac38-159">ODBC Source Custom Properties</span><span class="sxs-lookup"><span data-stu-id="fac38-159">ODBC Source Custom Properties</span></span>](odbc-source-custom-properties.md)  
  
  
