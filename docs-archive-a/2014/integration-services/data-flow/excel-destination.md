---
title: Excel 目的地 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.exceldest.f1
helpviewer_keywords:
- destinations [Integration Services], Excel
- Excel [Integration Services]
ms.assetid: 37c07446-1264-4814-b4f5-9c66d333bb24
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3e959f14e52fc045cb0cbc2ba0255d20bd0356d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709805"
---
# <a name="excel-destination"></a><span data-ttu-id="fbc65-102">Excel 目的地</span><span class="sxs-lookup"><span data-stu-id="fbc65-102">Excel Destination</span></span>
  <span data-ttu-id="fbc65-103">Excel 目的地會將資料載入至 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel 活頁簿中的工作表或範圍。</span><span class="sxs-lookup"><span data-stu-id="fbc65-103">The Excel destination loads data into worksheets or ranges in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel workbooks.</span></span>  
  
## <a name="access-modes"></a><span data-ttu-id="fbc65-104">存取模式</span><span class="sxs-lookup"><span data-stu-id="fbc65-104">Access Modes</span></span>  
 <span data-ttu-id="fbc65-105">Excel 目的地提供三種不同的資料存取模式用於載入資料：</span><span class="sxs-lookup"><span data-stu-id="fbc65-105">The Excel destination provides three different data access modes for loading data:</span></span>  
  
-   <span data-ttu-id="fbc65-106">資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="fbc65-106">A table or view.</span></span>  
  
-   <span data-ttu-id="fbc65-107">在變數中指定的資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="fbc65-107">A table or view specified in a variable.</span></span>  
  
-   <span data-ttu-id="fbc65-108">SQL 陳述式的結果。</span><span class="sxs-lookup"><span data-stu-id="fbc65-108">The results of an SQL statement.</span></span> <span data-ttu-id="fbc65-109">查詢可以是參數化查詢。</span><span class="sxs-lookup"><span data-stu-id="fbc65-109">The query can be a parameterized query.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fbc65-110">在 Excel 中，工作表或範圍相當於資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="fbc65-110">In Excel, a worksheet or range is the equivalent of a table or view.</span></span> <span data-ttu-id="fbc65-111">「Excel 來源」及「Excel 目的地」編輯器中的可用資料表清單，僅會顯示現有工作表 (以附加到工作表名稱的 $ 符號識別，例如 Sheet1$) 及具名範圍 (以沒有 $ 符號的方式識別，例如 MyRange)。</span><span class="sxs-lookup"><span data-stu-id="fbc65-111">The lists of available tables in the Excel Source and Destination editors display only existing worksheets (identified by the $ sign appended to the worksheet name, such as Sheet1$) and named ranges (identified by the absence of the $ sign, such as MyRange).</span></span>  
  
## <a name="usage-considerations"></a><span data-ttu-id="fbc65-112">使用狀況的考量</span><span class="sxs-lookup"><span data-stu-id="fbc65-112">Usage Considerations</span></span>  
 <span data-ttu-id="fbc65-113">Excel 連線管理員會使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Jet 4.0 及其支援的 Excel ISAM (Indexed Sequential Access Method，索引循序存取方法) 驅動程式，連接和讀寫資料至 Excel 資料來源。</span><span class="sxs-lookup"><span data-stu-id="fbc65-113">The Excel Connection Manager uses the [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Jet 4.0 and its supporting Excel ISAM (Indexed Sequential Access Method) driver to connect and read and write data to Excel data sources.</span></span>  
  
 <span data-ttu-id="fbc65-114">許多現有的「 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 知識庫」文件都有記錄此提供者和驅動程式的行為，而即使這些文件並非 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 或其前置的「資料轉換服務」專用，您仍會想了解可能導致未預期結果的特定行為。</span><span class="sxs-lookup"><span data-stu-id="fbc65-114">Many existing [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base articles document the behavior of this provider and driver, and although these articles are not specific to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] or its predecessor Data Transformation Services, you may want to know about certain behaviors that can lead to unexpected results.</span></span> <span data-ttu-id="fbc65-115">如需有關 Excel 驅動程式之使用與行為的一般資訊，請參閱＜ [如何從 Visual Basic 或 VBA 搭配使用 ADO 與 Excel 資料](https://support.microsoft.com/kb/257819)＞。</span><span class="sxs-lookup"><span data-stu-id="fbc65-115">For general information on the use and behavior of the Excel driver, see [HOWTO: Use ADO with Excel Data from Visual Basic or VBA](https://support.microsoft.com/kb/257819).</span></span>  
  
 <span data-ttu-id="fbc65-116">在將資料儲存至 Excel 目的地時，下列隨附於 Excel 驅動程式之 Jet 提供者的行為可能會導致非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="fbc65-116">The following behaviors of the Jet provider that is included with the Excel driver can lead to unexpected results when saving data to an Excel destination.</span></span>  
  
-   <span data-ttu-id="fbc65-117">**儲存文字資料**。</span><span class="sxs-lookup"><span data-stu-id="fbc65-117">**Saving text data**.</span></span> <span data-ttu-id="fbc65-118">將文字資料值儲存至 Excel 目的地時，Excel 驅動程式會在每個資料格的文字前面加上單引號字元 (')，以確保儲存的值會被解譯為文字值。</span><span class="sxs-lookup"><span data-stu-id="fbc65-118">When the Excel driver saves text data values to an Excel destination, the driver precedes the text in each cell with the single quote character (') to ensure that the saved values will be interpreted as text values.</span></span> <span data-ttu-id="fbc65-119">如果您擁有或開發讀取或處理儲存值的其他應用程式，您可能必須包含加在每個文字值前面的單引號字元的特殊處理。</span><span class="sxs-lookup"><span data-stu-id="fbc65-119">If you have or develop other applications that read or process the saved data, you may need to include special handling for the single quote character that precedes each text value.</span></span>  
  
     <span data-ttu-id="fbc65-120">如需如何避免包含單引號的資訊，請參閱 msdn.com 上的此篇部落格文章 [使用 SSIS 封裝中 Excel 資料流程目的地元件將資料轉換至 Excel 時，附加至所有字串的單引號](https://go.microsoft.com/fwlink/?LinkId=400876)(英文)。</span><span class="sxs-lookup"><span data-stu-id="fbc65-120">For information on how to avoid including the single quote, see this blog post, [Single quote is appended to all strings when data is transformed to excel when using Excel destination data flow component in SSIS package](https://go.microsoft.com/fwlink/?LinkId=400876), on msdn.com.</span></span>  
  
-   <span data-ttu-id="fbc65-121">**正在儲存備忘 (ntext) 資料**。</span><span class="sxs-lookup"><span data-stu-id="fbc65-121">**Saving memo (ntext) da**ta.</span></span> <span data-ttu-id="fbc65-122">在 Excel 資料行中成功儲存長於 255 個字元的字串之前，驅動程式必須能將目的地資料行的資料類型辨識為 **備忘** ，而不是 **字串**。</span><span class="sxs-lookup"><span data-stu-id="fbc65-122">Before you can successfully save strings longer than 255 characters to an Excel column, the driver must recognize the data type of the destination column as **memo** and not **string**.</span></span> <span data-ttu-id="fbc65-123">如果目的地資料表已包含資料列，則驅動程式所取樣的前幾個資料列必須在備忘資料行中至少包含一個值長於 255 個字元的執行個體。</span><span class="sxs-lookup"><span data-stu-id="fbc65-123">If the destination table already contains rows of data, then the first few rows that are sampled by the driver must contain at least one instance of a value longer than 255 characters in the memo column.</span></span> <span data-ttu-id="fbc65-124">如果目的地資料表是在封裝設計期間或在執行時間建立的，則 CREATE TABLE 語句必須使用 LONGTEXT (或它的其中一個同義字) 作為備忘資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="fbc65-124">If the destination table is created during package design or at run time, then the CREATE TABLE statement must use LONGTEXT (or one of its synonyms) as the data type of the memo column.</span></span>  
  
-   <span data-ttu-id="fbc65-125">**資料類型**。</span><span class="sxs-lookup"><span data-stu-id="fbc65-125">**Data types**.</span></span> <span data-ttu-id="fbc65-126">Excel 驅動程式只能辨識有限的一組資料類型。</span><span class="sxs-lookup"><span data-stu-id="fbc65-126">The Excel driver recognizes only a limited set of data types.</span></span> <span data-ttu-id="fbc65-127">例如，所有的數值資料行都會被解譯為倍整數 (DT_R8)，而所有的字串資料行 (備忘錄資料行除外) 全都會被解譯成 255 個字元的 Unicode 字串 (DT_WSTR)。</span><span class="sxs-lookup"><span data-stu-id="fbc65-127">For example, all numeric columns are interpreted as doubles (DT_R8), and all string columns (other than memo columns) are interpreted as 255-character Unicode strings (DT_WSTR).</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="fbc65-128">對應 Excel 資料類型的情況如下：</span><span class="sxs-lookup"><span data-stu-id="fbc65-128">maps the Excel data types as follows:</span></span>  
  
    -   <span data-ttu-id="fbc65-129">數值 - 雙精確度浮點數 (DT_R8)</span><span class="sxs-lookup"><span data-stu-id="fbc65-129">Numeric    double-precision float (DT_R8)</span></span>  
  
    -   <span data-ttu-id="fbc65-130">貨幣 - 貨幣 (DT_CY)</span><span class="sxs-lookup"><span data-stu-id="fbc65-130">Currency     currency (DT_CY)</span></span>  
  
    -   <span data-ttu-id="fbc65-131">布林值 - 布林值 (DT_BOOL)</span><span class="sxs-lookup"><span data-stu-id="fbc65-131">Boolean     Boolean (DT_BOOL)</span></span>  
  
    -   <span data-ttu-id="fbc65-132">日期/時間 `datetime` (DT_DATE) </span><span class="sxs-lookup"><span data-stu-id="fbc65-132">Date/time     `datetime` (DT_DATE)</span></span>  
  
    -   <span data-ttu-id="fbc65-133">字串 - Unicode 字串，長度 255 (DT_WSTR)</span><span class="sxs-lookup"><span data-stu-id="fbc65-133">String     Unicode string, length 255 (DT_WSTR)</span></span>  
  
    -   <span data-ttu-id="fbc65-134">備忘錄 - Unicode 文字資料流 (DT_NTEXT)</span><span class="sxs-lookup"><span data-stu-id="fbc65-134">Memo     Unicode text stream (DT_NTEXT)</span></span>  
  
-   <span data-ttu-id="fbc65-135">**資料類型和長度轉換**。</span><span class="sxs-lookup"><span data-stu-id="fbc65-135">**Data type and length conversions**.</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="fbc65-136">不會隱含地轉換資料類型。</span><span class="sxs-lookup"><span data-stu-id="fbc65-136">does not implicitly convert data types.</span></span> <span data-ttu-id="fbc65-137">因此，您可能必須使用衍生的資料行轉換或資料轉換，在將 Excel 資料載入到非 Excel 目的地之前明確轉換 Excel 資料，或是在將非 Excel 資料載入到 Excel 目的地之前轉換資料。</span><span class="sxs-lookup"><span data-stu-id="fbc65-137">As a result, you may need to use the Derived Column or Data Conversion transformations to convert Excel data explicitly before loading it into a non-Excel destination, or to convert non-Excel data before loading it into an Excel destination.</span></span> <span data-ttu-id="fbc65-138">在這種情況下，使用「匯入和匯出精靈」建立初始封裝可能很有用，因為這個精靈會為您設定必要的轉換。</span><span class="sxs-lookup"><span data-stu-id="fbc65-138">In this case, it may be useful to create the initial package by using the Import and Export Wizard, which configures the necessary conversions for you.</span></span> <span data-ttu-id="fbc65-139">某些轉換範例可能必須包含下列各項：</span><span class="sxs-lookup"><span data-stu-id="fbc65-139">Some examples of the conversions that may be required include the following:</span></span>  
  
    -   <span data-ttu-id="fbc65-140">Unicode Excel 字串資料行與具有特定字碼頁之非 Unicode 字串資料行之間的轉換。</span><span class="sxs-lookup"><span data-stu-id="fbc65-140">Conversion between Unicode Excel string columns and non-Unicode string columns with specific codepages.</span></span>  
  
    -   <span data-ttu-id="fbc65-141">255 個字元之 Excel 字串資料行與不同長度之字串資料行之間的轉換。</span><span class="sxs-lookup"><span data-stu-id="fbc65-141">Conversion between 255-character Excel string columns and string columns of different lengths.</span></span>  
  
    -   <span data-ttu-id="fbc65-142">雙精確度 Excel 數值資料行與其他類型之數值資料行之間的轉換。</span><span class="sxs-lookup"><span data-stu-id="fbc65-142">Conversion between double-precision Excel numeric columns and numeric columns of other types.</span></span>  
  
## <a name="configuration-of-the-excel-destination"></a><span data-ttu-id="fbc65-143">設定 Excel 目的地</span><span class="sxs-lookup"><span data-stu-id="fbc65-143">Configuration of the Excel Destination</span></span>  
 <span data-ttu-id="fbc65-144">Excel 目的地會使用 Excel 連接管理員，以連接到資料來源，而連接管理員會指定要使用的活頁簿檔案。</span><span class="sxs-lookup"><span data-stu-id="fbc65-144">The Excel destination uses an Excel connection manager to connect to a data source, and the connection manager specifies the workbook file to use.</span></span> <span data-ttu-id="fbc65-145">如需詳細資訊，請參閱 [Excel Connection Manager](../connection-manager/excel-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="fbc65-145">For more information, see [Excel Connection Manager](../connection-manager/excel-connection-manager.md).</span></span>  
  
 <span data-ttu-id="fbc65-146">Excel 目的地擁有一個規則輸入與一個錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="fbc65-146">The Excel destination has one regular input and one error output.</span></span>  
  
 <span data-ttu-id="fbc65-147">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="fbc65-147">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="fbc65-148">如需有關 **[Excel 目的地編輯器]** 對話方塊中可設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="fbc65-148">For more information about the properties that you can set in the **Excel Destination Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="fbc65-149">Excel 目的地編輯器 &#40;連線管理員頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="fbc65-149">Excel Destination Editor &#40;Connection Manager Page&#41;</span></span>](../excel-destination-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="fbc65-150">Excel 目的地編輯器 &#40;對應頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="fbc65-150">Excel Destination Editor &#40;Mappings Page&#41;</span></span>](../excel-destination-editor-mappings-page.md)  
  
-   [<span data-ttu-id="fbc65-151">Excel 目的地編輯器 &#40;錯誤輸出頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="fbc65-151">Excel Destination Editor &#40;Error Output Page&#41;</span></span>](../excel-destination-editor-error-output-page.md)  
  
 <span data-ttu-id="fbc65-152">**[進階編輯器]** 對話方塊會反映能以程式設計的方式設定之所有屬性。</span><span class="sxs-lookup"><span data-stu-id="fbc65-152">The **Advanced Editor** dialog box reflects all the properties that can be set programmatically.</span></span> <span data-ttu-id="fbc65-153">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="fbc65-153">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="fbc65-154">Common Properties</span><span class="sxs-lookup"><span data-stu-id="fbc65-154">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="fbc65-155">Excel 自訂屬性</span><span class="sxs-lookup"><span data-stu-id="fbc65-155">Excel Custom Properties</span></span>](excel-custom-properties.md)  
  
 <span data-ttu-id="fbc65-156">如需如何設定屬性的詳細資訊，請參閱 [設定資料流程元件的屬性](set-the-properties-of-a-data-flow-component.md)。</span><span class="sxs-lookup"><span data-stu-id="fbc65-156">For more information about how to set properties, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="fbc65-157">相關工作</span><span class="sxs-lookup"><span data-stu-id="fbc65-157">Related Tasks</span></span>  
  
-   [<span data-ttu-id="fbc65-158">使用 SQL Server Integration Services (SSIS) 從 Excel 匯入資料，或將資料匯出至 Excel</span><span class="sxs-lookup"><span data-stu-id="fbc65-158">Import data from Excel or export data to Excel with SQL Server Integration Services (SSIS)</span></span>](../load-data-to-from-excel-with-ssis.md)  
  
-   [<span data-ttu-id="fbc65-159">使用 Foreach 迴圈容器來執行 Excel 檔案和資料表迴圈</span><span class="sxs-lookup"><span data-stu-id="fbc65-159">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](../control-flow/foreach-loop-container.md)  
  
-   [<span data-ttu-id="fbc65-160">設定資料流程元件的屬性</span><span class="sxs-lookup"><span data-stu-id="fbc65-160">Set the Properties of a Data Flow Component</span></span>](set-the-properties-of-a-data-flow-component.md)  
  
## <a name="see-also"></a><span data-ttu-id="fbc65-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbc65-161">See Also</span></span>  
 <span data-ttu-id="fbc65-162">[Excel 來源](excel-source.md) </span><span class="sxs-lookup"><span data-stu-id="fbc65-162">[Excel Source](excel-source.md) </span></span>  
 <span data-ttu-id="fbc65-163">[Integration Services &#40;SSIS&#41; 變數](../integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="fbc65-163">[Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) </span></span>  
 <span data-ttu-id="fbc65-164">[資料流程](data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="fbc65-164">[Data Flow](data-flow.md) </span></span>  
 [<span data-ttu-id="fbc65-165">以指令碼工作處理 Excel 檔案</span><span class="sxs-lookup"><span data-stu-id="fbc65-165">Working with Excel Files with the Script Task</span></span>](../extending-packages-scripting-task-examples/working-with-excel-files-with-the-script-task.md)  
  
  
