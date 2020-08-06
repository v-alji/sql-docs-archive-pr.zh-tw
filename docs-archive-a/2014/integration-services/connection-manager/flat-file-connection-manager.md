---
title: 一般檔案連線管理員 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connection managers [Integration Services], Flat File
- connections [Integration Services], flat files
- files [Integration Services], connections
- Flat File connection manager
- flat files
- flat file connections [Integration Services]
ms.assetid: 7830f80d-af32-4e8f-a6fc-f03af6bc1946
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 961fa5ebd0c254c152cb4a84a855f719b6dfaa43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706625"
---
# <a name="flat-file-connection-manager"></a><span data-ttu-id="8a11b-102">一般檔案連接管理員</span><span class="sxs-lookup"><span data-stu-id="8a11b-102">Flat File Connection Manager</span></span>
  <span data-ttu-id="8a11b-103">「一般檔案」連接管理員可讓封裝存取一般檔案中的資料。</span><span class="sxs-lookup"><span data-stu-id="8a11b-103">A Flat File connection manager enables a package to access data in a flat file.</span></span> <span data-ttu-id="8a11b-104">例如，「一般檔案」來源與目的地可以使用「一般檔案」連接管理員來擷取並載入資料。</span><span class="sxs-lookup"><span data-stu-id="8a11b-104">For example, the Flat File source and destination can use Flat File connection managers to extract and load data.</span></span>  
  
 <span data-ttu-id="8a11b-105">「一般檔案」連接管理員僅可存取一個檔案。</span><span class="sxs-lookup"><span data-stu-id="8a11b-105">The Flat File connection manager can access only one file.</span></span> <span data-ttu-id="8a11b-106">若要參考多個檔案，請使用「多個一般檔案」連接管理員，而非「一般檔案」連接管理員。</span><span class="sxs-lookup"><span data-stu-id="8a11b-106">To reference multiple files, use a Multiple Flat Files connection manager instead of a Flat File connection manager.</span></span> <span data-ttu-id="8a11b-107">如需詳細資訊，請參閱 [Multiple Flat Files Connection Manager](multiple-flat-files-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="8a11b-107">For more information, see [Multiple Flat Files Connection Manager](multiple-flat-files-connection-manager.md).</span></span>  
  
## <a name="column-length"></a><span data-ttu-id="8a11b-108">資料行長度</span><span class="sxs-lookup"><span data-stu-id="8a11b-108">Column Length</span></span>  
 <span data-ttu-id="8a11b-109">依預設，「一般檔案」連接管理員會將字串資料行的長度設定成 50 個字元。</span><span class="sxs-lookup"><span data-stu-id="8a11b-109">By default, the Flat File connection manager sets the length of string columns to 50 characters.</span></span> <span data-ttu-id="8a11b-110">在 [一般檔案連接管理員編輯器]  對話方塊中，您可以評估取樣資料，並自動調整這些資料行的長度，以避免資料遭截斷或超出資料行寬度。</span><span class="sxs-lookup"><span data-stu-id="8a11b-110">In the **Flat File Connection Manager Editor** dialog box, you can evaluate sample data and automatically resize the length of these columns to prevent truncation of data or excess column width.</span></span> <span data-ttu-id="8a11b-111">此外，除非接著在一般檔案來源或轉換中調整資料行長度，否則字串資料行在整個資料流程中的資料行長度將維持不變。</span><span class="sxs-lookup"><span data-stu-id="8a11b-111">Also, unless you subsequently resize the column length in a Flat File source or a transformation, the column length of string column remains the same throughout the data flow.</span></span> <span data-ttu-id="8a11b-112">如果這些字串資料行對應到較窄的目的地資料行，使用者介面中將會出現警告。</span><span class="sxs-lookup"><span data-stu-id="8a11b-112">If these string columns map to destination columns that are narrower, warnings appear in the user interface.</span></span> <span data-ttu-id="8a11b-113">此外，執行階段中也可能發生因為資料截斷所產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="8a11b-113">Moreover, at run time, errors may occur due to data truncation.</span></span> <span data-ttu-id="8a11b-114">若要避免錯誤或資料截斷，您可以調整資料行的大小，使其與一般檔案連接管理員、一般檔案來源或轉換中的目的地資料行相容。</span><span class="sxs-lookup"><span data-stu-id="8a11b-114">To avoid errors or truncation, you can resize the columns to be compatible with the destination columns in the Flat File connection manager, the Flat File source, or a transformation.</span></span> <span data-ttu-id="8a11b-115">若要修改輸出資料行的長度，您可以在 `Length` [**進階編輯器**] 對話方塊的 [**輸入與輸出屬性**] 索引標籤上，設定輸出資料行的屬性。</span><span class="sxs-lookup"><span data-stu-id="8a11b-115">To modify the length of output columns, you set the `Length` property of the output column on the **Input and Output Properties** tab in the **Advanced Editor** dialog box.</span></span>  
  
 <span data-ttu-id="8a11b-116">如果在加入及設定使用「一般檔案」連接管理員的一般檔案來源之後，在該連接管理員中更新資料行長度，您就不需要手動調整一般檔案來源中輸出資料行的大小。</span><span class="sxs-lookup"><span data-stu-id="8a11b-116">If you update column lengths in the Flat File connection manager after you have added and configured the Flat File source that uses the connection manager, you do not have to manually resize the output columns in the Flat File source.</span></span> <span data-ttu-id="8a11b-117">在您開啟 **[一般檔案來源]** 對話方塊時，一般檔案來源會提供一個用來同步化資料行中繼資料的選項。</span><span class="sxs-lookup"><span data-stu-id="8a11b-117">When you open the **Flat File Source** dialog box, the Flat File source provides an option to synchronize the column metadata.</span></span>  
  
## <a name="configuration-of-the-flat-file-connection-manager"></a><span data-ttu-id="8a11b-118">設定一般檔案連接管理員</span><span class="sxs-lookup"><span data-stu-id="8a11b-118">Configuration of the Flat File Connection Manager</span></span>  
 <span data-ttu-id="8a11b-119">當您將「一般檔案」連線管理員加入封裝時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 會建立在執行時間解析為「一般檔案」連接的連線管理員、設定「一般檔案」連接屬性，並將「一般檔案」連接管理員加入 `Connections` 封裝的集合。</span><span class="sxs-lookup"><span data-stu-id="8a11b-119">When you add a Flat File connection manager to a package, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to a Flat File connection at run time, sets the Flat File connection properties, and adds the Flat File connection manager to the `Connections` collection of the package.</span></span>  
  
 <span data-ttu-id="8a11b-120">連接管理員的 `ConnectionManagerType` 屬性會設為 `FLATFILE`。</span><span class="sxs-lookup"><span data-stu-id="8a11b-120">The `ConnectionManagerType` property of the connection manager is set to `FLATFILE`.</span></span>  
  
 <span data-ttu-id="8a11b-121">根據預設，「一般檔案」連接管理員一律會檢查未加引號之資料中的資料列分隔符號，並在找到資料列分隔符號時開始一個新資料列。</span><span class="sxs-lookup"><span data-stu-id="8a11b-121">By default, the Flat File connection manager always checks for a row delimiter in unquoted data, and starts a new row when a row delimiter is found.</span></span> <span data-ttu-id="8a11b-122">這可讓連接管理員正確地剖析資料列缺少資料行欄位的檔案。</span><span class="sxs-lookup"><span data-stu-id="8a11b-122">This enables the connection manager to correctly parse files with rows that are missing column fields.</span></span>  
  
 <span data-ttu-id="8a11b-123">在某些情況下，停用此功能可能會提升封裝效能。</span><span class="sxs-lookup"><span data-stu-id="8a11b-123">In some cases, disabling this feature may improve package performance.</span></span> <span data-ttu-id="8a11b-124">您可以藉由將「一般檔案」連接管理員屬性**alwayscheckforrowdelimiters 設定]** 設定為來停用這項功能 `False` 。</span><span class="sxs-lookup"><span data-stu-id="8a11b-124">You can disable this feature by setting the Flat File connection manager property, **AlwaysCheckForRowDelimiters**, to `False`.</span></span>  
  
 <span data-ttu-id="8a11b-125">您可以利用下列方式設定「一般檔案」連接管理員：</span><span class="sxs-lookup"><span data-stu-id="8a11b-125">You can configure the Flat File connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="8a11b-126">指定要使用的檔案、地區設定及字碼頁。</span><span class="sxs-lookup"><span data-stu-id="8a11b-126">Specify the file, locale, and code page to use.</span></span> <span data-ttu-id="8a11b-127">地區設定用於解譯區分地區設定的資料 (如日期)，字碼頁用於將字串資料轉換為 Unicode。</span><span class="sxs-lookup"><span data-stu-id="8a11b-127">The locale is used to interpret locale-sensitive data such as dates, and the code page is used to convert string data to Unicode.</span></span>  
  
-   <span data-ttu-id="8a11b-128">指定檔案格式。</span><span class="sxs-lookup"><span data-stu-id="8a11b-128">Specify the file format.</span></span> <span data-ttu-id="8a11b-129">您可以使用分隔的、固定寬度或不齊右格式。</span><span class="sxs-lookup"><span data-stu-id="8a11b-129">You can use a delimited, fixed width, or ragged right format.</span></span>  
  
-   <span data-ttu-id="8a11b-130">指定標頭資料列、資料列和資料行分隔符號。</span><span class="sxs-lookup"><span data-stu-id="8a11b-130">Specify a header row, data row, and column delimiters.</span></span> <span data-ttu-id="8a11b-131">資料行分隔符號可以在檔案層級設定，並在資料行層級覆寫。</span><span class="sxs-lookup"><span data-stu-id="8a11b-131">Column delimiters can be set at the file level and overwritten at the column level.</span></span>  
  
-   <span data-ttu-id="8a11b-132">指示檔案中的第一個資料列是否包含資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="8a11b-132">Indicate whether the first row in the file contains column names.</span></span>  
  
-   <span data-ttu-id="8a11b-133">指定文字限定詞字元。</span><span class="sxs-lookup"><span data-stu-id="8a11b-133">Specify a text qualifier character.</span></span> <span data-ttu-id="8a11b-134">每個資料行都可以設定為識別文字限定詞。</span><span class="sxs-lookup"><span data-stu-id="8a11b-134">Each column can be configured to recognize a text qualifier.</span></span>  
  
     <span data-ttu-id="8a11b-135">現在支援使用限定詞字元，將限定詞字元內嵌到限定字串中。</span><span class="sxs-lookup"><span data-stu-id="8a11b-135">The use of a qualifier character to embed a qualifier character into a qualified string is now supported.</span></span> <span data-ttu-id="8a11b-136">文字限定詞的雙執行個體會解譯成常值 (該字串的單一執行個體)。</span><span class="sxs-lookup"><span data-stu-id="8a11b-136">The double instance of a text qualifier is interpreted as a literal, single instance of that string.</span></span> <span data-ttu-id="8a11b-137">例如，文字限定詞如果是單引號，而輸入資料為 'abc'、'def'、'g'hi'，則輸出資料為 abc、def、g'hi。</span><span class="sxs-lookup"><span data-stu-id="8a11b-137">For example, if the text qualifier is a single quote and the input data is 'abc', 'def', 'g'hi', the output data is abc, def, g'hi.</span></span>  
  
-   <span data-ttu-id="8a11b-138">在個別的資料行上設定屬性，例如名稱、資料類型和最大寬度。</span><span class="sxs-lookup"><span data-stu-id="8a11b-138">Set properties such as the name, data type, and maximum width on individual columns.</span></span>  
  
 <span data-ttu-id="8a11b-139">您可以針對一般檔案連接管理員來設定 ConnectionString 屬性，其方式是在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]的 [屬性] 視窗中指定運算式。</span><span class="sxs-lookup"><span data-stu-id="8a11b-139">You can set the ConnectionString property for the Flat File connection manager by specifying an expression in the Properties window of [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="8a11b-140">為避免驗證錯誤，請執行下列操作。</span><span class="sxs-lookup"><span data-stu-id="8a11b-140">To avoid a validation error, do the following.</span></span>  
  
-   <span data-ttu-id="8a11b-141">當您使用運算式指定檔案時，請在 [一般檔案連接管理員編輯器] \*\*\*\* 的 [檔案名稱] \*\*\*\* 方塊中加入檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="8a11b-141">When you use an expression to specify the file, add a file path in the **File name** box in the **Flat File Connection Manager Editor**.</span></span>  
  
-   <span data-ttu-id="8a11b-142">在「一般檔案」連接管理員上將 **DelayValidation** 屬性設定為 [True] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8a11b-142">Set the **DelayValidation** property on the Flat File connection manager to **True**.</span></span>  
  
 <span data-ttu-id="8a11b-143">您可以透過具有「一般檔案」目的地的「一般檔案」連接管理員，使用運算式在執行階段建立檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="8a11b-143">You can use an expression to create a file name at runtime by using the Flat File connection manager with the Flat File destination.</span></span>  
  
 <span data-ttu-id="8a11b-144">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="8a11b-144">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="8a11b-145">如需有關可以在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="8a11b-145">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="8a11b-146">一般檔案連線管理員編輯器 &#40;一般頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="8a11b-146">Flat File Connection Manager Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   <span data-ttu-id="8a11b-147">[一般檔案連線管理員編輯器 &#40;[資料行] 頁面&#41;](../flat-file-connection-manager-editor-columns-page.md)</span><span class="sxs-lookup"><span data-stu-id="8a11b-147">[Flat File Connection Manager Editor &#40;Columns Page&#41;](../flat-file-connection-manager-editor-columns-page.md)</span></span>  
  
-   [<span data-ttu-id="8a11b-148">一般檔案連線管理員編輯器 &#40;進階頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="8a11b-148">Flat File Connection Manager Editor &#40;Advanced Page&#41;</span></span>](../flat-file-connection-manager-editor-advanced-page.md)  
  
-   [<span data-ttu-id="8a11b-149">一般檔案連線管理員編輯器 &#40;預覽頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="8a11b-149">Flat File Connection Manager Editor &#40;Preview Page&#41;</span></span>](../flat-file-connection-manager-editor-preview-page.md)  
  
 <span data-ttu-id="8a11b-150">如需以程式設計方式設定連線管理員的資訊，請參閱 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和 [以程式設計方式加入連接](../building-packages-programmatically/adding-connections-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="8a11b-150">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
  
