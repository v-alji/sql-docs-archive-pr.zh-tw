---
title: Excel 來源 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.excelsource.f1
helpviewer_keywords:
- Excel [Integration Services]
- sources [Integration Services], Excel
ms.assetid: e66349f3-b1b8-4763-89b7-7803541a4d62
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c1324ca9e9b9535b8598e3e2de22f6c06c350b7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709809"
---
# <a name="excel-source"></a><span data-ttu-id="17f55-102">Excel 來源</span><span class="sxs-lookup"><span data-stu-id="17f55-102">Excel Source</span></span>
  <span data-ttu-id="17f55-103">Excel 來源會從 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel 活頁簿中的工作表或範圍擷取資料。</span><span class="sxs-lookup"><span data-stu-id="17f55-103">The Excel source extracts data from worksheets or ranges in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel workbooks.</span></span>  
  
 <span data-ttu-id="17f55-104">Excel 來源會提供四種不同的資料存取模式來擷取資料：</span><span class="sxs-lookup"><span data-stu-id="17f55-104">The Excel source provides four different data access modes for extracting data:</span></span>  
  
-   <span data-ttu-id="17f55-105">資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="17f55-105">A table or view.</span></span>  
  
-   <span data-ttu-id="17f55-106">在變數中指定的資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="17f55-106">A table or view specified in a variable.</span></span>  
  
-   <span data-ttu-id="17f55-107">SQL 陳述式的結果。</span><span class="sxs-lookup"><span data-stu-id="17f55-107">The results of an SQL statement.</span></span> <span data-ttu-id="17f55-108">查詢可以是參數化查詢。</span><span class="sxs-lookup"><span data-stu-id="17f55-108">The query can be a parameterized query.</span></span>  
  
-   <span data-ttu-id="17f55-109">儲存在變數中之 SQL 陳述式的結果。</span><span class="sxs-lookup"><span data-stu-id="17f55-109">The results of an SQL statement stored in a variable.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="17f55-110">在 Excel 中，工作表或範圍相當於資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="17f55-110">In Excel, a worksheet or range is the equivalent of a table or view.</span></span> <span data-ttu-id="17f55-111">「Excel 來源」及「Excel 目的地」編輯器中的可用資料表清單，會顯示現有工作表 (以附加到工作表名稱的 $ 符號識別，例如 Sheet1$) 及具名範圍 (以沒有 $ 符號的方式識別，例如 MyRange)。</span><span class="sxs-lookup"><span data-stu-id="17f55-111">The list of available tables in the Excel Source and Destination editors displays existing worksheets (identified by the $ sign appended to the worksheet name, such as Sheet1$) and named ranges (identified by the absence of the $ sign, such as MyRange).</span></span> <span data-ttu-id="17f55-112">如需詳細資訊，請參閱＜使用狀況的考量＞一節。</span><span class="sxs-lookup"><span data-stu-id="17f55-112">For more information, see the Usage Considerations section.</span></span>  
  
 <span data-ttu-id="17f55-113">Excel 來源會使用 Excel 連接管理員連接到資料來源，而連接管理員會指定要使用的活頁簿檔案。</span><span class="sxs-lookup"><span data-stu-id="17f55-113">The Excel source uses an Excel connection manager to connect to a data source, and the connection manager specifies the workbook file to use.</span></span> <span data-ttu-id="17f55-114">如需詳細資訊，請參閱 [Excel Connection Manager](../connection-manager/excel-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="17f55-114">For more information, see [Excel Connection Manager](../connection-manager/excel-connection-manager.md).</span></span>  
  
 <span data-ttu-id="17f55-115">Excel 來源有一個一般輸出和一個錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="17f55-115">The Excel source has one regular output and one error output.</span></span>  
  
## <a name="usage-considerations"></a><span data-ttu-id="17f55-116">使用狀況的考量</span><span class="sxs-lookup"><span data-stu-id="17f55-116">Usage Considerations</span></span>  
 <span data-ttu-id="17f55-117">Excel 連線管理員會使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Jet 4.0 及其支援的 Excel ISAM (Indexed Sequential Access Method，索引循序存取方法) 驅動程式，連接和讀寫資料至 Excel 資料來源。</span><span class="sxs-lookup"><span data-stu-id="17f55-117">The Excel Connection Manager uses the [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for Jet 4.0 and its supporting Excel ISAM (Indexed Sequential Access Method) driver to connect and read and write data to Excel data sources.</span></span>  
  
 <span data-ttu-id="17f55-118">許多現有的「 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 知識庫」文件都有記錄此提供者和驅動程式的行為，而即使這些文件並非 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 或其前置的「資料轉換服務」專用，您仍會想了解可能導致未預期結果的特定行為。</span><span class="sxs-lookup"><span data-stu-id="17f55-118">Many existing [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base articles document the behavior of this provider and driver, and although these articles are not specific to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] or its predecessor Data Transformation Services, you may want to know about certain behaviors that can lead to unexpected results.</span></span> <span data-ttu-id="17f55-119">如需有關 Excel 驅動程式之使用與行為的一般資訊，請參閱＜ [如何從 Visual Basic 或 VBA 搭配使用 ADO 與 Excel 資料](https://support.microsoft.com/kb/257819)＞。</span><span class="sxs-lookup"><span data-stu-id="17f55-119">For general information on the use and behavior of the Excel driver, see [HOWTO: Use ADO with Excel Data from Visual Basic or VBA](https://support.microsoft.com/kb/257819).</span></span>  
  
 <span data-ttu-id="17f55-120">下列使用 Excel 驅動程式之 Jet 提供者的行為，在從 Excel 資料來源讀取資料時，可能導致未預期的結果。</span><span class="sxs-lookup"><span data-stu-id="17f55-120">The following behaviors of the Jet provider with the Excel driver can lead to unexpected results when reading data from an Excel data source.</span></span>  
  
-   <span data-ttu-id="17f55-121">**資料來源**。</span><span class="sxs-lookup"><span data-stu-id="17f55-121">**Data sources**.</span></span> <span data-ttu-id="17f55-122">Excel 活頁簿中資料的來源可以是工作表 (必須附加 $ 符號，例如 Sheet1$) 或已命名的範圍 (例如 MyRange)。</span><span class="sxs-lookup"><span data-stu-id="17f55-122">The source of data in an Excel workbook can be a worksheet, to which the $ sign must be appended (for example, Sheet1$), or a named range (for example, MyRange).</span></span> <span data-ttu-id="17f55-123">在 SQL 陳述式中，工作表的名稱必須加以分隔 (例如 [Sheet1$])，以避免 $ 符號造成的語法錯誤。</span><span class="sxs-lookup"><span data-stu-id="17f55-123">In a SQL statement, the name of a worksheet must be delimited (for example, [Sheet1$]) to avoid a syntax error caused by the $ sign.</span></span> <span data-ttu-id="17f55-124">「查詢產生器」會自動加入這些分隔符號。</span><span class="sxs-lookup"><span data-stu-id="17f55-124">The Query Builder automatically adds these delimiters.</span></span> <span data-ttu-id="17f55-125">當您指定工作表或範圍時，驅動程式會讀取連續的資料格區塊，從工作表或範圍左上角的第一個非空白資料格開始。</span><span class="sxs-lookup"><span data-stu-id="17f55-125">When you specify a worksheet or range, the driver reads the contiguous block of cells starting with the first non-empty cell in the upper-left corner of the worksheet or range.</span></span> <span data-ttu-id="17f55-126">因此，來源資料的資料列不可以空白，或標題或標頭資料列與資料列之間不可以有空白資料列。</span><span class="sxs-lookup"><span data-stu-id="17f55-126">Therefore you cannot have empty rows in the source data, or an empty row between title or header rows and the data rows.</span></span>  
  
-   <span data-ttu-id="17f55-127">**遺漏值**。</span><span class="sxs-lookup"><span data-stu-id="17f55-127">**Missing values**.</span></span> <span data-ttu-id="17f55-128">Excel 驅動程式會在指定來源中讀取特定資料列數目 (依預設為 8 個資料列)，以猜測各資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="17f55-128">The Excel driver reads a certain number of rows (by default, 8 rows) in the specified source to guess at the data type of each column.</span></span> <span data-ttu-id="17f55-129">當資料行可能包含混合資料類型，尤其是數值資料與文字資料混合時，驅動程式會做出有利於大部分資料類型的決定，並於包含其他類型資料的資料格中傳回 Null 值。</span><span class="sxs-lookup"><span data-stu-id="17f55-129">When a column appears to contain mixed data types, especially numeric data mixed with text data, the driver decides in favor of the majority data type, and returns null values for cells that contain data of the other type.</span></span> <span data-ttu-id="17f55-130">(在繫結中，以數值類型優先)。Excel 工作表中大部分的資料格格式化選項，似乎都不會影響這項資料類型決定。</span><span class="sxs-lookup"><span data-stu-id="17f55-130">(In a tie, the numeric type wins.) Most cell formatting options in the Excel worksheet do not seem to affect this data type determination.</span></span> <span data-ttu-id="17f55-131">您可以藉由指定「匯入模式」來修改 Excel 驅動程式的這項行為。</span><span class="sxs-lookup"><span data-stu-id="17f55-131">You can modify this behavior of the Excel driver by specifying Import Mode.</span></span> <span data-ttu-id="17f55-132">若要指定匯入模式，請 `IMEX=1` 在 [**屬性**] 視窗中，將加入至 Excel 連接管理員之連接字串中的 [擴充屬性] 的值。</span><span class="sxs-lookup"><span data-stu-id="17f55-132">To specify Import Mode, add `IMEX=1` to the value of Extended Properties in the connection string of the Excel connection manager in the **Properties** window.</span></span> <span data-ttu-id="17f55-133">如需詳細資訊，請參閱 [PRB: Excel Values Returned as NULL Using DAO OpenRecordset](https://support.microsoft.com/kb/194124)(PRB：使用 DAO OpenRecordset 以 NULL 形式傳回的 Excel 值)。</span><span class="sxs-lookup"><span data-stu-id="17f55-133">For more information, see [PRB: Excel Values Returned as NULL Using DAO OpenRecordset](https://support.microsoft.com/kb/194124).</span></span>  
  
-   <span data-ttu-id="17f55-134">**截斷的文字**。</span><span class="sxs-lookup"><span data-stu-id="17f55-134">**Truncated text**.</span></span> <span data-ttu-id="17f55-135">當驅動程式判斷出某個 Excel 資料行包含文字資料時，驅動程式將會根據其取樣的最長值來選取資料類型 (字串或備忘錄)。</span><span class="sxs-lookup"><span data-stu-id="17f55-135">When the driver determines that an Excel column contains text data, the driver selects the data type (string or memo) based on the longest value that it samples.</span></span> <span data-ttu-id="17f55-136">如果驅動程式未在其取樣的資料列中發現任何長度超過 255 個字元的值，則會將該資料行視為 255 個字元字串資料行而非備忘錄資料行</span><span class="sxs-lookup"><span data-stu-id="17f55-136">If the driver does not discover any values longer than 255 characters in the rows that it samples, it treats the column as a 255-character string column instead of a memo column.</span></span> <span data-ttu-id="17f55-137">因此，長度超過 255 個字元的值可能會被截斷。</span><span class="sxs-lookup"><span data-stu-id="17f55-137">Therefore, values longer than 255 characters may be truncated.</span></span> <span data-ttu-id="17f55-138">若要以不截斷的方式從備忘資料行匯入資料，您必須確保至少在其中一個取樣資料列中的備忘錄資料行包含長度超過 255 個字元的值，否則您就必須增加驅動程式取樣的資料列數目，使其包含這類資料列。</span><span class="sxs-lookup"><span data-stu-id="17f55-138">To import data from a memo column without truncation, you must make sure that the memo column in at least one of the sampled rows contains a value longer than 255 characters, or you must increase the number of rows sampled by the driver to include such a row.</span></span> <span data-ttu-id="17f55-139">您可以提高 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Jet\4.0\Engines\Excel** 登錄機碼底下 **TypeGuessRows** 的值，藉以增加取樣的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="17f55-139">You can increase the number of rows sampled by increasing the value of **TypeGuessRows** under the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Jet\4.0\Engines\Excel** registry key.</span></span> <span data-ttu-id="17f55-140">如需詳細資訊，請參閱 [PRB︰從 Jet 4.0 OLEDB 來源傳送資料失敗，發生緩衝區溢位錯誤](https://support.microsoft.com/kb/281517)(PRB: Transfer of Data from Jet 4.0 OLEDB Source Fails w/ Error)。</span><span class="sxs-lookup"><span data-stu-id="17f55-140">For more information, see [PRB: Transfer of Data from Jet 4.0 OLEDB Source Fails w/ Error](https://support.microsoft.com/kb/281517).</span></span>  
  
-   <span data-ttu-id="17f55-141">**資料類型**。</span><span class="sxs-lookup"><span data-stu-id="17f55-141">**Data types**.</span></span> <span data-ttu-id="17f55-142">Excel 驅動程式只能辨識有限的一組資料類型。</span><span class="sxs-lookup"><span data-stu-id="17f55-142">The Excel driver recognizes only a limited set of data types.</span></span> <span data-ttu-id="17f55-143">例如，所有的數值資料行都會被解譯為倍整數 (DT_R8)，而所有的字串資料行 (備忘錄資料行除外) 全都會被解譯成 255 個字元的 Unicode 字串 (DT_WSTR)。</span><span class="sxs-lookup"><span data-stu-id="17f55-143">For example, all numeric columns are interpreted as doubles (DT_R8), and all string columns (other than memo columns) are interpreted as 255-character Unicode strings (DT_WSTR).</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="17f55-144">對應 Excel 資料類型的情況如下：</span><span class="sxs-lookup"><span data-stu-id="17f55-144">maps the Excel data types as follows:</span></span>  
  
    -   <span data-ttu-id="17f55-145">數值 - 雙精確度浮點數 (DT_R8)</span><span class="sxs-lookup"><span data-stu-id="17f55-145">Numeric - double-precision float (DT_R8)</span></span>  
  
    -   <span data-ttu-id="17f55-146">貨幣 - 貨幣 (DT_CY)</span><span class="sxs-lookup"><span data-stu-id="17f55-146">Currency - currency (DT_CY)</span></span>  
  
    -   <span data-ttu-id="17f55-147">布林值 - 布林值 (DT_BOOL)</span><span class="sxs-lookup"><span data-stu-id="17f55-147">Boolean - Boolean (DT_BOOL)</span></span>  
  
    -   <span data-ttu-id="17f55-148">日期/時間- `datetime` (DT_DATE) </span><span class="sxs-lookup"><span data-stu-id="17f55-148">Date/time - `datetime` (DT_DATE)</span></span>  
  
    -   <span data-ttu-id="17f55-149">字串 - Unicode 字串，長度 255 (DT_WSTR)</span><span class="sxs-lookup"><span data-stu-id="17f55-149">String - Unicode string, length 255 (DT_WSTR)</span></span>  
  
    -   <span data-ttu-id="17f55-150">備忘錄 - Unicode 文字資料流 (DT_NTEXT)</span><span class="sxs-lookup"><span data-stu-id="17f55-150">Memo - Unicode text stream (DT_NTEXT)</span></span>  
  
-   <span data-ttu-id="17f55-151">**資料類型和長度轉換**。</span><span class="sxs-lookup"><span data-stu-id="17f55-151">**Data type and length conversions**.</span></span> [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="17f55-152">不會隱含地轉換資料類型。</span><span class="sxs-lookup"><span data-stu-id="17f55-152">does not implicitly convert data types.</span></span> <span data-ttu-id="17f55-153">因此，您可能必須使用衍生的資料行轉換或資料轉換，在將 Excel 資料載入到非 Excel 目的地之前明確轉換 Excel 資料，或是在將非 Excel 資料載入到 Excel 目的地之前轉換資料。</span><span class="sxs-lookup"><span data-stu-id="17f55-153">As a result, you may need to use Derived Column or Data Conversion transformations to convert Excel data explicitly before loading it into a non-Excel destination, or to convert non-Excel data before loading it into an Excel destination.</span></span> <span data-ttu-id="17f55-154">在這種情況下，使用「匯入和匯出精靈」建立初始封裝可能很有用，因為這個精靈會為您設定必要的轉換。</span><span class="sxs-lookup"><span data-stu-id="17f55-154">In this case, it may be useful to create the initial package by using the Import and Export Wizard, which configures the necessary conversions for you.</span></span> <span data-ttu-id="17f55-155">某些轉換範例可能必須包含下列各項：</span><span class="sxs-lookup"><span data-stu-id="17f55-155">Some examples of the conversions that may be required include the following:</span></span>  
  
    -   <span data-ttu-id="17f55-156">Unicode Excel 字串資料行與具有特定字碼頁之非 Unicode 字串資料行之間的轉換</span><span class="sxs-lookup"><span data-stu-id="17f55-156">Conversion between Unicode Excel string columns and non-Unicode string columns with specific codepages</span></span>  
  
    -   <span data-ttu-id="17f55-157">255 個字元之 Excel 字串資料行與不同長度之字串資料行之間的轉換</span><span class="sxs-lookup"><span data-stu-id="17f55-157">Conversion between 255-character Excel string columns and string columns of different lengths</span></span>  
  
    -   <span data-ttu-id="17f55-158">雙精確度 Excel 數值資料行與其他類型之數值資料行之間的轉換</span><span class="sxs-lookup"><span data-stu-id="17f55-158">Conversion between double-precision Excel numeric columns and numeric columns of other types</span></span>  
  
## <a name="excel-source-configuration"></a><span data-ttu-id="17f55-159">Excel 來源組態</span><span class="sxs-lookup"><span data-stu-id="17f55-159">Excel Source Configuration</span></span>  
 <span data-ttu-id="17f55-160">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="17f55-160">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="17f55-161">如需可在 [Excel 來源編輯器]\*\*\*\* 對話方塊中設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="17f55-161">For more information about the properties that you can set in the **Excel Source Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="17f55-162">Excel 來源編輯器 &#40;連線管理員頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="17f55-162">Excel Source Editor &#40;Connection Manager Page&#41;</span></span>](../excel-source-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="17f55-163">Excel 來源編輯器 &#40;資料行頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="17f55-163">Excel Source Editor &#40;Columns Page&#41;</span></span>](../excel-source-editor-columns-page.md)  
  
-   [<span data-ttu-id="17f55-164">Excel 來源編輯器 &#40;錯誤輸出頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="17f55-164">Excel Source Editor &#40;Error Output Page&#41;</span></span>](../excel-source-editor-error-output-page.md)  
  
 <span data-ttu-id="17f55-165">**[進階編輯器]** 對話方塊會反映能以程式設計的方式設定之所有屬性。</span><span class="sxs-lookup"><span data-stu-id="17f55-165">The **Advanced Editor** dialog box reflects all the properties that can be set programmatically.</span></span> <span data-ttu-id="17f55-166">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="17f55-166">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="17f55-167">Common Properties</span><span class="sxs-lookup"><span data-stu-id="17f55-167">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="17f55-168">Excel 自訂屬性</span><span class="sxs-lookup"><span data-stu-id="17f55-168">Excel Custom Properties</span></span>](excel-custom-properties.md)  
  
 <span data-ttu-id="17f55-169">如需循環使用 Excel 檔案群組的資訊，請參閱 [使用 Foreach 迴圈容器來循環使用 Excel 檔案和資料表](../control-flow/foreach-loop-container.md)。</span><span class="sxs-lookup"><span data-stu-id="17f55-169">For information about looping through a group of Excel files, see [Loop through Excel Files and Tables by Using a Foreach Loop Container](../control-flow/foreach-loop-container.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="17f55-170">相關工作</span><span class="sxs-lookup"><span data-stu-id="17f55-170">Related Tasks</span></span>  

-   [<span data-ttu-id="17f55-171">使用 SQL Server Integration Services (SSIS) 從 Excel 匯入資料，或將資料匯出至 Excel</span><span class="sxs-lookup"><span data-stu-id="17f55-171">Import data from Excel or export data to Excel with SQL Server Integration Services (SSIS)</span></span>](../load-data-to-from-excel-with-ssis.md)

-   [<span data-ttu-id="17f55-172">在資料流程元件中將查詢參數對應至變數</span><span class="sxs-lookup"><span data-stu-id="17f55-172">Map Query Parameters to Variables in a Data Flow Component</span></span>](map-query-parameters-to-variables-in-a-data-flow-component.md)  
  
-   [<span data-ttu-id="17f55-173">設定資料流程元件的屬性</span><span class="sxs-lookup"><span data-stu-id="17f55-173">Set the Properties of a Data Flow Component</span></span>](set-the-properties-of-a-data-flow-component.md)  
  
-   [<span data-ttu-id="17f55-174">排序合併和合併聯結轉換的資料</span><span class="sxs-lookup"><span data-stu-id="17f55-174">Sort Data for the Merge and Merge Join Transformations</span></span>](transformations/sort-data-for-the-merge-and-merge-join-transformations.md)  
  
-   [<span data-ttu-id="17f55-175">使用 Foreach 迴圈容器來執行 Excel 檔案和資料表迴圈</span><span class="sxs-lookup"><span data-stu-id="17f55-175">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](../control-flow/foreach-loop-container.md)  
  
## <a name="related-content"></a><span data-ttu-id="17f55-176">相關內容</span><span class="sxs-lookup"><span data-stu-id="17f55-176">Related Content</span></span>  
  
-   <span data-ttu-id="17f55-177">hrvoje.piasevoli.com 上的部落格文章： [Importing data from 64-bit Excel in SSIS](https://go.microsoft.com/fwlink/?LinkId=217673)(從 SSIS 中的 64 位元 Excel 匯入資料)</span><span class="sxs-lookup"><span data-stu-id="17f55-177">Blog entry, [Importing data from 64-bit Excel in SSIS](https://go.microsoft.com/fwlink/?LinkId=217673), on hrvoje.piasevoli.com</span></span>  
  
-   <span data-ttu-id="17f55-178">[在 SSIS 中連接到 Excel (.xlsx) 的](https://microsoft-ssis.blogspot.com/2014/02/connecting-to-excel-xlsx-in-ssis.html)Blog 專案。</span><span class="sxs-lookup"><span data-stu-id="17f55-178">Blog entry, [Connecting to Excel (XLSX) in SSIS](https://microsoft-ssis.blogspot.com/2014/02/connecting-to-excel-xlsx-in-ssis.html).</span></span>  
  
  
