---
title: ODBC 目的地 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcdest.f1
ms.assetid: bffa63e0-c737-4b54-b4ea-495a400ffcf8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: beb29c511af62ba69ca0b9e2c595f61c57edab6f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599125"
---
# <a name="odbc-destination"></a><span data-ttu-id="c2224-102">ODBC 目的地</span><span class="sxs-lookup"><span data-stu-id="c2224-102">ODBC Destination</span></span>
  <span data-ttu-id="c2224-103">ODBC 目的地會將資料大量載入到 ODBC 支援的資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="c2224-103">The ODBC destination bulk loads data into ODBC-supported database tables.</span></span> <span data-ttu-id="c2224-104">ODBC 目的地使用 ODBC 連接管理員來連接到資料來源。</span><span class="sxs-lookup"><span data-stu-id="c2224-104">The ODBC destination uses an ODBC connection manager to connect to the data source.</span></span>  
  
 <span data-ttu-id="c2224-105">ODBC 目的地包含輸入資料行與目的地資料來源中資料行之間的對應。</span><span class="sxs-lookup"><span data-stu-id="c2224-105">An ODBC destination includes mappings between input columns and columns in the destination data source.</span></span> <span data-ttu-id="c2224-106">您不一定要將輸入資料行對應到所有目的地資料行，但因目的地資料行屬性的不同，如果輸入資料行未對應到目的地資料行，則可能發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c2224-106">You do not have to map input columns to all destination columns, but depending on the properties of the destination columns, errors may occur if no input columns are mapped to the destination columns.</span></span> <span data-ttu-id="c2224-107">例如，如果目的地資料行不允許 Null 值，則輸入資料行必須對應到該資料行。</span><span class="sxs-lookup"><span data-stu-id="c2224-107">For example, if a destination column does not allow null values, an input column must be mapped to that column.</span></span> <span data-ttu-id="c2224-108">此外，雖然可對應不同類型的資料行，但是如果輸入資料與目的地資料行類型不相容，在執行階段會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c2224-108">In addition, columns of different types can be mapped, however if the input data is not compatible for the destination column type, an error occurs at runtime.</span></span> <span data-ttu-id="c2224-109">根據錯誤行為設定，錯誤會被忽略，導致失敗，或者資料列會傳送至錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="c2224-109">Depending on the error behavior setting, the error will be ignored, cause a failure, or the row is sent to the error output.</span></span>  
  
 <span data-ttu-id="c2224-110">ODBC 目的地具有一個一般輸出和一個錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="c2224-110">The ODBC destination has one regular output and one error output.</span></span>  
  
##  <a name="load-options"></a><a name="BKMK_odbcdestination_loadoptions"></a> <span data-ttu-id="c2224-111">載入選項</span><span class="sxs-lookup"><span data-stu-id="c2224-111">Load Options</span></span>  
 <span data-ttu-id="c2224-112">ODBC 目的地可以使用兩種存取載入模組其中之一。</span><span class="sxs-lookup"><span data-stu-id="c2224-112">The ODBC destination can use one of two access load modules.</span></span> <span data-ttu-id="c2224-113">您會在 [ODBC 來源編輯器 &#40;連線管理員頁面&#41;](../odbc-source-editor-connection-manager-page.md) 設定模式。</span><span class="sxs-lookup"><span data-stu-id="c2224-113">You set the mode in the [ODBC Source Editor &#40;Connection Manager Page&#41;](../odbc-source-editor-connection-manager-page.md).</span></span> <span data-ttu-id="c2224-114">兩種模式為：</span><span class="sxs-lookup"><span data-stu-id="c2224-114">The two modes are:</span></span>  
  
-   <span data-ttu-id="c2224-115">**批次**：在此模式中，ODBC 目的地會根據所見的 ODBC 提供者功能，嘗試使用最有效率的插入方法。</span><span class="sxs-lookup"><span data-stu-id="c2224-115">**Batch**: In this mode the ODBC destination attempts to use the most efficient insertion method based on the perceived ODBC provider capabilities.</span></span> <span data-ttu-id="c2224-116">對於最新的 ODBC 提供者，這表示準備含有參數的 INSERT 陳述式，然後使用資料列取向的陣列參數繫結 (陣列大小是由 **BatchSize** 屬性所控制)。</span><span class="sxs-lookup"><span data-stu-id="c2224-116">For most modern ODBC providers, this would mean preparing an INSERT statement with parameters and then using a row-wise array parameter binding (where the array size is controlled by the **BatchSize** property).</span></span> <span data-ttu-id="c2224-117">如果您選取 [批次]  ，而提供者不支援此方法，ODBC 目的地會自動切換為**逐列**模式。</span><span class="sxs-lookup"><span data-stu-id="c2224-117">If you select **Batch** and the provider does not support this method, the ODBC destination automatically switches to the **Row-by-row** mode.</span></span>  
  
-   <span data-ttu-id="c2224-118">**逐列**：在此模式中，ODBC 目的地會準備含有參數的 INSERT 陳述式，然後使用 **SQL Execute** ，一次插入一個資料列。</span><span class="sxs-lookup"><span data-stu-id="c2224-118">**Row-by-row**: In this mode, the ODBC destination prepares an INSERT statement with parameters and uses **SQL Execute** to insert rows one at a time.</span></span>  
  
## <a name="error-handling"></a><span data-ttu-id="c2224-119">錯誤處理</span><span class="sxs-lookup"><span data-stu-id="c2224-119">Error Handling</span></span>  
 <span data-ttu-id="c2224-120">ODBC 目的地有錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="c2224-120">The ODBC destination has an error output.</span></span> <span data-ttu-id="c2224-121">此元件的錯誤輸出包含下列輸出資料行：</span><span class="sxs-lookup"><span data-stu-id="c2224-121">The component error output includes the following output columns:</span></span>  
  
-   <span data-ttu-id="c2224-122">**錯誤碼**：對應至目前錯誤的編號。</span><span class="sxs-lookup"><span data-stu-id="c2224-122">**Error Code**: The number that corresponds to the current error.</span></span> <span data-ttu-id="c2224-123">如需錯誤清單，請參閱來源資料庫的文件集。</span><span class="sxs-lookup"><span data-stu-id="c2224-123">See the documentation for your source database for a list of errors.</span></span> <span data-ttu-id="c2224-124">如需 SSIS 錯誤碼清單，請參閱＜SSIS 錯誤碼和訊息參考＞。</span><span class="sxs-lookup"><span data-stu-id="c2224-124">For a list of SSIS error codes, see the SSIS Error Code and Message Reference.</span></span>  
  
-   <span data-ttu-id="c2224-125">**錯誤資料行**：造成錯誤 (用於轉換錯誤) 的來源資料行。</span><span class="sxs-lookup"><span data-stu-id="c2224-125">**Error Column**: The source column causing the error (for conversion errors).</span></span>  
  
-   <span data-ttu-id="c2224-126">標準輸出資料行。</span><span class="sxs-lookup"><span data-stu-id="c2224-126">The standard output data columns.</span></span>  
  
 <span data-ttu-id="c2224-127">根據錯誤行為設定，ODBC 目的地支援在錯誤輸出中傳回擷取程序期間發生的錯誤 (資料轉換、截斷)。</span><span class="sxs-lookup"><span data-stu-id="c2224-127">Depending on the error behavior setting, the ODBC destination supports returning errors (data conversion, truncation) that occur during the extraction process in the error output.</span></span> <span data-ttu-id="c2224-128">如需詳細資訊，請參閱 [ODBC 來源編輯器 &#40;錯誤輸出頁面&#41;](../odbc-source-editor-error-output-page.md)。</span><span class="sxs-lookup"><span data-stu-id="c2224-128">For more information, see [ODBC Source Editor &#40;Error Output Page&#41;](../odbc-source-editor-error-output-page.md).</span></span>  
  
## <a name="parallelism"></a><span data-ttu-id="c2224-129">平行處理原則</span><span class="sxs-lookup"><span data-stu-id="c2224-129">Parallelism</span></span>  
 <span data-ttu-id="c2224-130">可針對相同電腦或不同電腦上的相同資料表或不同資料表平行執行的 ODBC 目的地元件數目不受限制 (除了一般全域工作階段限制之外)。</span><span class="sxs-lookup"><span data-stu-id="c2224-130">There is no limitation on the number of ODBC destination components that can run in parallel against the same table or different tables, on the same machine or on different machines (other than normal global session limits).</span></span>  
  
 <span data-ttu-id="c2224-131">然而，所使用的 ODBC 提供者的限制可能會限制透過提供者的並行連接數目。</span><span class="sxs-lookup"><span data-stu-id="c2224-131">However, limitations of the ODBC provider being used may restrict the number of concurrent connections through the provider.</span></span> <span data-ttu-id="c2224-132">這些限制會限制 ODBC 目的地支援的平行執行個體數目。</span><span class="sxs-lookup"><span data-stu-id="c2224-132">These limitations limit the number of supported parallel instances possible for the ODBC destination.</span></span> <span data-ttu-id="c2224-133">SSIS 開發人員必須知道所使用的任何 ODBC 提供者的限制，並在建立 SSIS 封裝時將這些限制納入考量。</span><span class="sxs-lookup"><span data-stu-id="c2224-133">The SSIS developer must be aware of the limitations of any ODBC provider being used and take them into consideration when building SSIS packages.</span></span>  
  
 <span data-ttu-id="c2224-134">您還必須知道同時載入到相同資料表可能會因為標準記錄鎖定而降低效能。</span><span class="sxs-lookup"><span data-stu-id="c2224-134">You must also be aware that concurrently loading into the same table may reduce performance because of standard record locking.</span></span> <span data-ttu-id="c2224-135">這取決於正在載入的資料和資料表組織。</span><span class="sxs-lookup"><span data-stu-id="c2224-135">This depends on the data being loaded and on the table organization.</span></span>  
  
## <a name="troubleshooting-the-odbc-destination"></a><span data-ttu-id="c2224-136">ODBC 目的地疑難排解</span><span class="sxs-lookup"><span data-stu-id="c2224-136">Troubleshooting the ODBC Destination</span></span>  
 <span data-ttu-id="c2224-137">您可以記錄 ODBC 來源對外部資料提供者所執行的呼叫。</span><span class="sxs-lookup"><span data-stu-id="c2224-137">You can log the calls that the ODBC source makes to external data providers.</span></span> <span data-ttu-id="c2224-138">您可以使用這項記錄功能，針對 ODBC 目的地所執行之將資料儲存至外部資料來源的作業進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="c2224-138">You can use this logging capability to troubleshoot the saving of data to external data sources that the ODBC destination performs.</span></span> <span data-ttu-id="c2224-139">若要記錄 ODBC 目的地對外部資料提供者執行的呼叫，請啟用 ODBC 驅動程式管理員追蹤。</span><span class="sxs-lookup"><span data-stu-id="c2224-139">To log the calls that the ODBC destination makes to external data providers, enable the ODBC driver manager trace.</span></span> <span data-ttu-id="c2224-140">如需詳細資訊，請參閱 Microsoft 文件集＜如何使用 ODBC 資料來源管理員產生 ODBC 追蹤＞。</span><span class="sxs-lookup"><span data-stu-id="c2224-140">For more information, see the Microsoft documentation on *How To Generate an ODBC Trace with ODBC the Data Source Administrator*.</span></span>  
  
## <a name="configuring-the-odbc-destination"></a><span data-ttu-id="c2224-141">設定 ODBC 目的地</span><span class="sxs-lookup"><span data-stu-id="c2224-141">Configuring the ODBC Destination</span></span>  
 <span data-ttu-id="c2224-142">您可以透過程式設計方式或 SSIS 設計師來設定 ODBC 目的地。</span><span class="sxs-lookup"><span data-stu-id="c2224-142">You can configure the ODBC destination programatically or through the SSIS Designer</span></span>  
  
 <span data-ttu-id="c2224-143">如需詳細資訊，請參閱下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="c2224-143">For more information, see one of the following topics:</span></span>  
  
-   [<span data-ttu-id="c2224-144">ODBC 目的地編輯器 &#40;連線管理員頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="c2224-144">ODBC Destination Editor &#40;Connection Manager Page&#41;</span></span>](../odbc-destination-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="c2224-145">ODBC 目的地編輯器 &#40;對應頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="c2224-145">ODBC Destination Editor &#40;Mappings Page&#41;</span></span>](../odbc-destination-editor-mappings-page.md)  
  
-   [<span data-ttu-id="c2224-146">ODBC 目的地編輯器 &#40;錯誤輸出頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="c2224-146">ODBC Destination Editor &#40;Error Output Page&#41;</span></span>](../odbc-destination-editor-error-output-page.md)  
  
 <span data-ttu-id="c2224-147">**[進階編輯器]** 對話方塊包含可以程式設計方式設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="c2224-147">The **Advanced Editor** dialog box contains the properties that can be set programmatically.</span></span>  
  
 <span data-ttu-id="c2224-148">若要開啟 **[進階編輯器]** 對話方塊：</span><span class="sxs-lookup"><span data-stu-id="c2224-148">To open the **Advanced Editor** dialog box:</span></span>  
  
-   <span data-ttu-id="c2224-149">在 **專案的** [資料流程] [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 畫面中，以滑鼠右鍵按一下 ODBC 目的地，然後選取 **[顯示進階編輯器]** 。</span><span class="sxs-lookup"><span data-stu-id="c2224-149">In the **Data Flow** screen of your [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] project, right click the ODBC destination and select **Show Advanced Editor**.</span></span>  
  
 <span data-ttu-id="c2224-150">如需有關可在 [進階編輯器] 對話方塊中設定之屬性的詳細資訊，請參閱＜ [ODBC Destination Custom Properties](odbc-destination-custom-properties.md)＞。</span><span class="sxs-lookup"><span data-stu-id="c2224-150">For more information about the properties that you can set in the Advanced Editor dialog box, see [ODBC Destination Custom Properties](odbc-destination-custom-properties.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c2224-151">本節內容</span><span class="sxs-lookup"><span data-stu-id="c2224-151">In This Section</span></span>  
  
-   [<span data-ttu-id="c2224-152">ODBC 目的地編輯器 &#40;錯誤輸出頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="c2224-152">ODBC Destination Editor &#40;Error Output Page&#41;</span></span>](../odbc-destination-editor-error-output-page.md)  
  
-   [<span data-ttu-id="c2224-153">ODBC 目的地編輯器 &#40;對應頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="c2224-153">ODBC Destination Editor &#40;Mappings Page&#41;</span></span>](../odbc-destination-editor-mappings-page.md)  
  
-   [<span data-ttu-id="c2224-154">ODBC 目的地編輯器 &#40;連線管理員頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="c2224-154">ODBC Destination Editor &#40;Connection Manager Page&#41;</span></span>](../odbc-destination-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="c2224-155">使用 ODBC 目的地來載入資料</span><span class="sxs-lookup"><span data-stu-id="c2224-155">Load Data by Using the ODBC Destination</span></span>](odbc-destination.md)  
  
-   [<span data-ttu-id="c2224-156">ODBC 目的地自訂屬性</span><span class="sxs-lookup"><span data-stu-id="c2224-156">ODBC Destination Custom Properties</span></span>](odbc-destination-custom-properties.md)  
  
  
