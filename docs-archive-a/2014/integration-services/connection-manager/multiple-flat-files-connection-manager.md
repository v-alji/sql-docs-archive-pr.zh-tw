---
title: 多個一般檔案連線管理員 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Multiple Flat Files connection manager
- connections [Integration Services], flat files
- flat files
- flat file connections [Integration Services]
- connection managers [Integration Services], Multiple Flat Files
- multiple flat file connections
ms.assetid: 31fc3f7a-d323-44f5-a907-1fa3de66631a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a17125fedb495daabc4838161b3260c0d5590319
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599134"
---
# <a name="multiple-flat-files-connection-manager"></a><span data-ttu-id="2b61a-102">多個一般檔案連接管理員</span><span class="sxs-lookup"><span data-stu-id="2b61a-102">Multiple Flat Files Connection Manager</span></span>
  <span data-ttu-id="2b61a-103">「多個一般檔案」連接管理員可讓封裝存取多個一般檔案中的資料。</span><span class="sxs-lookup"><span data-stu-id="2b61a-103">A Multiple Flat Files connection manager enables a package to access data in multiple flat files.</span></span> <span data-ttu-id="2b61a-104">例如，當資料流程工作位於迴圈容器 (如 For 迴圈容器) 內時，「一般檔案」來源可以使用「多個一般檔案」連接管理員。</span><span class="sxs-lookup"><span data-stu-id="2b61a-104">For example, a Flat File source can use a Multiple Flat Files connection manager when the Data Flow task is inside a loop container, such as the For Loop container.</span></span> <span data-ttu-id="2b61a-105">在此容器的每一個迴圈上，「一般檔案」來源會從「多個一般檔案」連接管理員提供的下一個檔案名稱中載入資料。</span><span class="sxs-lookup"><span data-stu-id="2b61a-105">On each loop of the container, the Flat File source loads data from the next file name that the Multiple Flat Files connection manager provides.</span></span>  
  
 <span data-ttu-id="2b61a-106">當您將「多個一般檔案」連接管理員加入封裝時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 會建立連線管理員，在執行時間解析為「多個一般檔案」連接、在「多個一般檔案」連接管理員上設定屬性，以及將「多個一般檔案」連接管理員加入 `Connections` 封裝的集合。</span><span class="sxs-lookup"><span data-stu-id="2b61a-106">When you add a Multiple Flat Files connection manager to a package, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to a Multiple Flat Files connection at run time, sets the properties on the Multiple Flat Files connection manager, and adds the Multiple Flat Files connection manager to the `Connections` collection of the package.</span></span>  
  
 <span data-ttu-id="2b61a-107">連接管理員的 `ConnectionManagerType` 屬性會設為 `MULTIFLATFILE`。</span><span class="sxs-lookup"><span data-stu-id="2b61a-107">The `ConnectionManagerType` property of the connection manager is set to `MULTIFLATFILE`.</span></span>  
  
 <span data-ttu-id="2b61a-108">您可以利用下列方式設定「多個一般檔案」連接管理員：</span><span class="sxs-lookup"><span data-stu-id="2b61a-108">You can configure the Multiple Flat Files connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="2b61a-109">指定要使用的檔案、地區設定和字碼頁。</span><span class="sxs-lookup"><span data-stu-id="2b61a-109">Specify the files, locale, and code page to use.</span></span> <span data-ttu-id="2b61a-110">地區設定用於解譯區分地區設定的資料 (如日期)，字碼頁用於將字串資料轉換為 Unicode。</span><span class="sxs-lookup"><span data-stu-id="2b61a-110">The locale is used to interpret locale-sensitive data such as dates, and the code page is used to convert string data to Unicode.</span></span>  
  
-   <span data-ttu-id="2b61a-111">指定檔案格式。</span><span class="sxs-lookup"><span data-stu-id="2b61a-111">Specify the file format.</span></span> <span data-ttu-id="2b61a-112">您可以使用分隔的、固定寬度或不齊右格式。</span><span class="sxs-lookup"><span data-stu-id="2b61a-112">You can use a delimited, fixed width, or ragged right format.</span></span>  
  
-   <span data-ttu-id="2b61a-113">指定標頭資料列、資料列和資料行分隔符號。</span><span class="sxs-lookup"><span data-stu-id="2b61a-113">Specify a header row, data row, and column delimiters.</span></span> <span data-ttu-id="2b61a-114">資料行分隔符號可以在檔案層級設定，並在資料行層級覆寫。</span><span class="sxs-lookup"><span data-stu-id="2b61a-114">Column delimiters can be set at the file level and overwritten at the column level.</span></span>  
  
-   <span data-ttu-id="2b61a-115">指出檔案中的第一個資料列是否包含資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="2b61a-115">Indicate whether the first row in the files contains column names.</span></span>  
  
-   <span data-ttu-id="2b61a-116">指定文字限定詞字元。</span><span class="sxs-lookup"><span data-stu-id="2b61a-116">Specify a text qualifier character.</span></span> <span data-ttu-id="2b61a-117">每個資料行都可以設定為識別文字限定詞。</span><span class="sxs-lookup"><span data-stu-id="2b61a-117">Each column can be configured to recognize a text qualifier.</span></span>  
  
-   <span data-ttu-id="2b61a-118">在個別的資料行上設定屬性，例如名稱、資料類型和最大寬度。</span><span class="sxs-lookup"><span data-stu-id="2b61a-118">Set properties such as the name, data type, and maximum width on individual columns.</span></span>  
  
 <span data-ttu-id="2b61a-119">如果「多個一般檔案」連接管理員參考多個檔案，則檔案的路徑會以垂直線 (|) 字元隔開。</span><span class="sxs-lookup"><span data-stu-id="2b61a-119">When the Multiple Flat Files connection manager references multiple files, the paths of the files are separated by the pipe (|) character.</span></span> <span data-ttu-id="2b61a-120">連接管理員的 `ConnectionString` 屬性具有下列格式：</span><span class="sxs-lookup"><span data-stu-id="2b61a-120">The `ConnectionString` property of the connection manager has the following format:</span></span>  
  
 \<*path*>|\<*path*>  
  
 <span data-ttu-id="2b61a-121">您也可以使用萬用字元來指定多個檔案。</span><span class="sxs-lookup"><span data-stu-id="2b61a-121">You can also specify multiple files by using wildcard characters.</span></span> <span data-ttu-id="2b61a-122">例如，若要參考 C 磁片磁碟機上的所有文字檔，屬性的值 `ConnectionString` 可以設定為 c： \\ \* .txt。</span><span class="sxs-lookup"><span data-stu-id="2b61a-122">For example, to reference all the text files on the C drive, the value of the `ConnectionString` property can be set to C:\\*.txt.</span></span>  
  
 <span data-ttu-id="2b61a-123">如果「多個一般檔案」連接管理員參考多個檔案，則所有檔案必須具有相同的格式。</span><span class="sxs-lookup"><span data-stu-id="2b61a-123">If a Multiple Flat Files connection manager references multiple files, all the files must have the same format.</span></span>  
  
 <span data-ttu-id="2b61a-124">依預設，「多個一般檔案」連接管理員會將字串資料行的長度設定成 50 個字元。</span><span class="sxs-lookup"><span data-stu-id="2b61a-124">By default, the Multiple Flat Files connection manager sets the length of string columns to 50 characters.</span></span> <span data-ttu-id="2b61a-125">在 **[多個一般檔案連接管理員編輯器]** 對話方塊中，您可以評估取樣資料，並自動調整這些資料行的長度，以避免資料遭截斷或超出資料行寬度。</span><span class="sxs-lookup"><span data-stu-id="2b61a-125">In the **Multiple Flat Files Connection Manager Editor** dialog box, you can evaluate sample data and automatically resize the length of these columns to prevent truncation of data or excess column width.</span></span> <span data-ttu-id="2b61a-126">除非在一般檔案來源或轉換中調整資料行長度，否則在整個資料流程中，資料行長度將維持不變。</span><span class="sxs-lookup"><span data-stu-id="2b61a-126">Unless you resize the column length in a Flat File source or a transformation, the column length remains the same throughout the data flow.</span></span> <span data-ttu-id="2b61a-127">如果這些資料行對應到較窄的目的資料行，使用者介面中將會出現警告，而且在執行階段中可能發生因為資料截斷所產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="2b61a-127">If these columns map to destination columns that are narrower, warnings appear in the user interface, and at run time, errors may occur due to data truncation.</span></span> <span data-ttu-id="2b61a-128">您可以調整資料行的大小，使其與一般檔案連接管理員、一般檔案來源或轉換中的目的地資料行相容。</span><span class="sxs-lookup"><span data-stu-id="2b61a-128">You can resize the columns to be compatible with the destination columns in the Flat File connection manager, the Flat File source, or a transformation.</span></span> <span data-ttu-id="2b61a-129">若要修改輸出資料行的長度，您可以在 `Length` [**進階編輯器**] 對話方塊的 [**輸入與輸出屬性**] 索引標籤上，設定輸出資料行的屬性。</span><span class="sxs-lookup"><span data-stu-id="2b61a-129">To modify the length of output columns, you set the `Length` property of the output column on the **Input and Output Properties** tab in the **Advanced Editor** dialog box.</span></span>  
  
 <span data-ttu-id="2b61a-130">如果在加入及設定使用「多個一般檔案」連接管理員的一般檔案來源之後，在該連接管理員中更新資料行長度，您就不需要手動調整一般檔案來源中輸出資料行的大小。</span><span class="sxs-lookup"><span data-stu-id="2b61a-130">If you update column lengths in the Multiple Flat Files connection manager after you have added and configured the Flat File source that uses the connection manager, you do not have to manually resize the output columns in the Flat File source.</span></span> <span data-ttu-id="2b61a-131">在您開啟 **[一般檔案來源]** 對話方塊時，一般檔案來源會提供一個用來同步化資料行中繼資料的選項。</span><span class="sxs-lookup"><span data-stu-id="2b61a-131">When you open the **Flat File Source** dialog box, the Flat File source provides an option to synchronize the column metadata.</span></span>  
  
## <a name="configuration-of-the-multiple-flat-files-connection-manager"></a><span data-ttu-id="2b61a-132">設定多個一般檔案連接管理員</span><span class="sxs-lookup"><span data-stu-id="2b61a-132">Configuration of the Multiple Flat Files Connection Manager</span></span>  
 <span data-ttu-id="2b61a-133">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="2b61a-133">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="2b61a-134">如需有關可以在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="2b61a-134">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="2b61a-135">多個一般檔案連接管理員編輯器 &#40;一般頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="2b61a-135">Multiple Flat Files Connection Manager Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="2b61a-136">多個一般檔案連接管理員編輯器 &#40;資料行頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="2b61a-136">Multiple Flat Files Connection Manager Editor &#40;Columns Page&#41;</span></span>](../multiple-flat-files-connection-manager-editor-columns-page.md)  
  
-   [<span data-ttu-id="2b61a-137">多個一般檔案連線管理員編輯器 &#40;進階頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="2b61a-137">Multiple Flat Files Connection Manager Editor &#40;Advanced Page&#41;</span></span>](../multiple-flat-files-connection-manager-editor-advanced-page.md)  
  
-   [<span data-ttu-id="2b61a-138">多個一般檔案連線管理員編輯器 &#40;預覽頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="2b61a-138">Multiple Flat Files Connection Manager Editor &#40;Preview Page&#41;</span></span>](../multiple-flat-files-connection-manager-editor-preview-page.md)  
  
 <span data-ttu-id="2b61a-139">如需以程式設計方式設定連線管理員的資訊，請參閱 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 和 [以程式設計方式加入連接](../building-packages-programmatically/adding-connections-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="2b61a-139">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b61a-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b61a-140">See Also</span></span>  
 <span data-ttu-id="2b61a-141">[一般檔案來源](../data-flow/flat-file-source.md) </span><span class="sxs-lookup"><span data-stu-id="2b61a-141">[Flat File Source](../data-flow/flat-file-source.md) </span></span>  
 <span data-ttu-id="2b61a-142">[一般檔案目的地](../data-flow/flat-file-destination.md) </span><span class="sxs-lookup"><span data-stu-id="2b61a-142">[Flat File Destination](../data-flow/flat-file-destination.md) </span></span>  
 [<span data-ttu-id="2b61a-143">Integration Services &#40;SSIS&#41; 連接</span><span class="sxs-lookup"><span data-stu-id="2b61a-143">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
