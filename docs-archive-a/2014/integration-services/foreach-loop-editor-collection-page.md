---
title: '[Foreach 迴圈編輯器] (集合] 頁面) |Microsoft Docs'
ms.custom: ''
ms.date: 08/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.foreachloopcontainer.collection.f1
ms.assetid: 95a19dde-61ca-4d9b-aa3d-131fa4264296
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a90ce0c8971c57ef90b502cfde298605a73c253d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710733"
---
# <a name="foreach-loop-editor-collection-page"></a><span data-ttu-id="cd85e-102">Foreach 迴圈編輯器 (集合頁面)</span><span class="sxs-lookup"><span data-stu-id="cd85e-102">Foreach Loop Editor (Collection Page)</span></span>
  <span data-ttu-id="cd85e-103">使用 [Foreach 迴圈編輯器]\*\*\*\* 對話方塊的 [集合]\*\*\*\* 頁面，即可指定列舉值類型和設定列舉值。</span><span class="sxs-lookup"><span data-stu-id="cd85e-103">Use the **Collection** pageof the **Foreach Loop Editor** dialog box to specify the enumerator type and configure the enumerator.</span></span>  
  
 <span data-ttu-id="cd85e-104">若要了解 Foreach 迴圈容器以及如何設定該容器，請參閱 [Foreach 迴圈容器](control-flow/foreach-loop-container.md) 和 [設定 Foreach 迴圈容器](../../2014/integration-services/configure-a-foreach-loop-container.md)。</span><span class="sxs-lookup"><span data-stu-id="cd85e-104">To learn about the Foreach Loop container and how to configure it, see [Foreach Loop Container](control-flow/foreach-loop-container.md) and [Configure a Foreach Loop Container](../../2014/integration-services/configure-a-foreach-loop-container.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="cd85e-105">靜態選項</span><span class="sxs-lookup"><span data-stu-id="cd85e-105">Static Options</span></span>  
 <span data-ttu-id="cd85e-106">**列舉值**</span><span class="sxs-lookup"><span data-stu-id="cd85e-106">**Enumerator**</span></span>  
 <span data-ttu-id="cd85e-107">從清單中選取列舉值類型。</span><span class="sxs-lookup"><span data-stu-id="cd85e-107">Select the enumerator type from the list.</span></span> <span data-ttu-id="cd85e-108">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="cd85e-108">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="cd85e-109">值</span><span class="sxs-lookup"><span data-stu-id="cd85e-109">Value</span></span>|<span data-ttu-id="cd85e-110">描述</span><span class="sxs-lookup"><span data-stu-id="cd85e-110">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cd85e-111">**Foreach 檔案列舉值**</span><span class="sxs-lookup"><span data-stu-id="cd85e-111">**Foreach File Enumerator**</span></span>|<span data-ttu-id="cd85e-112">列舉檔案。</span><span class="sxs-lookup"><span data-stu-id="cd85e-112">Enumerate files.</span></span> <span data-ttu-id="cd85e-113">選取這個值就會在 **[Foreach 檔案列舉值]** 區段中顯示動態選項。</span><span class="sxs-lookup"><span data-stu-id="cd85e-113">Selecting this value displays the dynamic options in the section, **Foreach File Enumerator**.</span></span>|  
|<span data-ttu-id="cd85e-114">**Foreach 項目列舉值**</span><span class="sxs-lookup"><span data-stu-id="cd85e-114">**Foreach Item Enumerator**</span></span>|<span data-ttu-id="cd85e-115">列舉項目中的值。</span><span class="sxs-lookup"><span data-stu-id="cd85e-115">Enumerate values in an item.</span></span> <span data-ttu-id="cd85e-116">選取這個值就會在 **[Foreach 項目列舉值]** 區段中顯示動態選項。</span><span class="sxs-lookup"><span data-stu-id="cd85e-116">Selecting this value displays the dynamic options in the section, **Foreach Item Enumerator**.</span></span>|  
|<span data-ttu-id="cd85e-117">**Foreach ADO 列舉值**</span><span class="sxs-lookup"><span data-stu-id="cd85e-117">**Foreach ADO Enumerator**</span></span>|<span data-ttu-id="cd85e-118">列舉資料表或資料表中的資料列。</span><span class="sxs-lookup"><span data-stu-id="cd85e-118">Enumerate tables or rows in tables.</span></span> <span data-ttu-id="cd85e-119">選取這個值就會在 **[Foreach ADO 列舉值]** 區段中顯示動態選項。</span><span class="sxs-lookup"><span data-stu-id="cd85e-119">Selecting this value displays the dynamic options in the section, **Foreach ADO Enumerator**.</span></span>|  
|<span data-ttu-id="cd85e-120">**Foreach ADO.NET 結構描述資料列集列舉值**</span><span class="sxs-lookup"><span data-stu-id="cd85e-120">**Foreach ADO.NET Schema Rowset Enumerator**</span></span>|<span data-ttu-id="cd85e-121">列舉結構描述。</span><span class="sxs-lookup"><span data-stu-id="cd85e-121">Enumerate a schema.</span></span> <span data-ttu-id="cd85e-122">選取這個值就會在 **[Foreach ADO.NET 列舉值]** 區段中顯示動態選項。</span><span class="sxs-lookup"><span data-stu-id="cd85e-122">Selecting this value displays the dynamic options in the section, **Foreach ADO.NET Enumerator**.</span></span>|  
|<span data-ttu-id="cd85e-123">**Foreach From Variable 列舉值**</span><span class="sxs-lookup"><span data-stu-id="cd85e-123">**Foreach From Variable Enumerator**</span></span>|<span data-ttu-id="cd85e-124">列舉變數中的值。</span><span class="sxs-lookup"><span data-stu-id="cd85e-124">Enumerate the value in a variable.</span></span> <span data-ttu-id="cd85e-125">選取這個值就會在 **[Foreach From Variable 列舉值]** 區段中顯示動態選項。</span><span class="sxs-lookup"><span data-stu-id="cd85e-125">Selecting this value displays the dynamic options in the section, **Foreach From Variable Enumerator**.</span></span>|  
|<span data-ttu-id="cd85e-126">**Foreach NodeList 列舉值**</span><span class="sxs-lookup"><span data-stu-id="cd85e-126">**Foreach Nodelist Enumerator**</span></span>|<span data-ttu-id="cd85e-127">以 XML 文件列舉節點。</span><span class="sxs-lookup"><span data-stu-id="cd85e-127">Enumerate nodes in an XML document.</span></span> <span data-ttu-id="cd85e-128">選取這個值就會在 **[Foreach NodeList 列舉值]** 區段中顯示動態選項。</span><span class="sxs-lookup"><span data-stu-id="cd85e-128">Selecting this value displays the dynamic options in the section, **Foreach Nodelist Enumerator**.</span></span>|  
|<span data-ttu-id="cd85e-129">**Foreach SMO 列舉值**</span><span class="sxs-lookup"><span data-stu-id="cd85e-129">**Foreach SMO Enumerator**</span></span>|<span data-ttu-id="cd85e-130">列舉 SMO 物件。</span><span class="sxs-lookup"><span data-stu-id="cd85e-130">Enumerate a SMO object.</span></span> <span data-ttu-id="cd85e-131">選取這個值就會在 **[Foreach SMO 列舉值]** 區段中顯示動態選項。</span><span class="sxs-lookup"><span data-stu-id="cd85e-131">Selecting this value displays the dynamic options in the section, **Foreach SMO Enumerator**.</span></span>|  
|<span data-ttu-id="cd85e-132">**Foreach Azure Blob 列舉值**</span><span class="sxs-lookup"><span data-stu-id="cd85e-132">**Foreach Azure Blob Enumerator**</span></span>|<span data-ttu-id="cd85e-133">列舉指定 Blob 位置中的 Blob 檔案。</span><span class="sxs-lookup"><span data-stu-id="cd85e-133">Enumerate blob files in the specified blob location.</span></span> <span data-ttu-id="cd85e-134">選取此值可在 **[Foreach ADO 列舉值]** 區段中顯示動態選項。</span><span class="sxs-lookup"><span data-stu-id="cd85e-134">Selecting this value displays the dynamic options in the section, **Foreach Azure Blob Enumerator**.</span></span>|  
|<span data-ttu-id="cd85e-135">**Foreach ADLS 檔案列舉值**</span><span class="sxs-lookup"><span data-stu-id="cd85e-135">**Foreach ADLS File Enumerator**</span></span>|<span data-ttu-id="cd85e-136">使用篩選準則列舉 ADLS 上的檔案。</span><span class="sxs-lookup"><span data-stu-id="cd85e-136">Enumerate files on ADLS with filters.</span></span> <span data-ttu-id="cd85e-137">選取這個值就會在 [Foreach ADLS 檔案列舉值]  區段中顯示動態選項。</span><span class="sxs-lookup"><span data-stu-id="cd85e-137">Selecting this value displays the dynamic options in the section, **Foreach ADLS File Enumerator**.</span></span>|
  
 <span data-ttu-id="cd85e-138">**運算式**</span><span class="sxs-lookup"><span data-stu-id="cd85e-138">**Expressions**</span></span>  
 <span data-ttu-id="cd85e-139">按一下或展開 **[運算式]** ，即可檢視現有屬性運算式的清單。</span><span class="sxs-lookup"><span data-stu-id="cd85e-139">Click or expand **Expressions** to view the list of existing property expressions.</span></span> <span data-ttu-id="cd85e-140">按一下省略符號 **(...)** 按鈕以新增列舉值屬性的屬性運算式，或是編輯和評估現有的屬性運算式。</span><span class="sxs-lookup"><span data-stu-id="cd85e-140">Click the ellipsis button **(...)** to add a property expression for an enumerator property, or edit and evaluate an existing property expression.</span></span>  
  
 <span data-ttu-id="cd85e-141">**相關主題：** [Integration Services &#40;SSIS&#41; 運算式](expressions/integration-services-ssis-expressions.md)、[屬性運算式編輯器](expressions/property-expressions-editor.md)、[運算式產生器](expressions/expression-builder.md)</span><span class="sxs-lookup"><span data-stu-id="cd85e-141">**Related Topics:**  [Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md), [Property Expressions Editor](expressions/property-expressions-editor.md), [Expression Builder](expressions/expression-builder.md)</span></span>  
  
## <a name="enumerator-dynamic-options"></a><span data-ttu-id="cd85e-142">列舉值動態選項</span><span class="sxs-lookup"><span data-stu-id="cd85e-142">Enumerator Dynamic Options</span></span>  
  
### <a name="enumerator--foreach-file-enumerator"></a><span data-ttu-id="cd85e-143">列舉值 = Foreach 檔案列舉值</span><span class="sxs-lookup"><span data-stu-id="cd85e-143">Enumerator = Foreach File Enumerator</span></span>  
 <span data-ttu-id="cd85e-144">Foreach 檔案列舉值可用來列舉資料夾中的檔案。</span><span class="sxs-lookup"><span data-stu-id="cd85e-144">You use the Foreach File enumerator to enumerate files in a folder.</span></span> <span data-ttu-id="cd85e-145">例如，如果 Foreach 迴圈包括「執行 SQL」工作，則您可使用 Foreach 檔案列舉值來列舉檔案，而這些檔案包含執行「執行 SQL」工作的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="cd85e-145">For example, if the Foreach Loop includes an Execute SQL task, you can use the Foreach File enumerator to enumerate files that contain SQL statements that the Execute SQL task runs.</span></span> <span data-ttu-id="cd85e-146">您也可以將列舉值設定成包括子資料夾。</span><span class="sxs-lookup"><span data-stu-id="cd85e-146">The enumerator can be configured to include subfolders.</span></span>  
  
 <span data-ttu-id="cd85e-147">因為迴圈中的外部處理序或工作在迴圈執行時加入、重新命名或刪除檔案，所以 Foreach 檔案列舉值所列舉的資料夾和子資料夾內容在迴圈執行時可能會變更。</span><span class="sxs-lookup"><span data-stu-id="cd85e-147">The content of the folders and subfolders that the Foreach File enumerator enumerates might change while the loop is executing because external processes or tasks in the loop add, rename, or delete files while the loop is executing.</span></span> <span data-ttu-id="cd85e-148">這表示可能會發生一些非預期的狀況：</span><span class="sxs-lookup"><span data-stu-id="cd85e-148">This means that a number of unexpected situations may occur:</span></span>  
  
-   <span data-ttu-id="cd85e-149">如果是刪除檔案，則 Foreach 迴圈中的其中一個工作可能會針對與後續工作所用之檔案不同的一組檔案執行工作。</span><span class="sxs-lookup"><span data-stu-id="cd85e-149">If files are deleted, one task in the Foreach Loop may perform work on a different set of files than the files used by subsequent tasks.</span></span>  
  
-   <span data-ttu-id="cd85e-150">如果是重新命名檔案，且外部處理序自動加入檔案以取代重新命名的檔案，則 Foreach 迴圈可能會針對相同的檔案內容執行兩次工作。</span><span class="sxs-lookup"><span data-stu-id="cd85e-150">If files are renamed and an external process automatically adds files to replace the renamed files, the Foreach Loop might perform work twice on the same file content.</span></span>  
  
-   <span data-ttu-id="cd85e-151">如果是加入檔案，則可能會很難判斷 Foreach 迴圈執行的是哪個檔案的工作。</span><span class="sxs-lookup"><span data-stu-id="cd85e-151">If files are added, it may be difficult to determine for which files the Foreach Loop performed work.</span></span>  
  
 <span data-ttu-id="cd85e-152">**資料夾**</span><span class="sxs-lookup"><span data-stu-id="cd85e-152">**Folder**</span></span>  
 <span data-ttu-id="cd85e-153">提供要列舉的根資料夾之路徑。</span><span class="sxs-lookup"><span data-stu-id="cd85e-153">Provide the path of the root folder to enumerate.</span></span>  
  
 <span data-ttu-id="cd85e-154">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="cd85e-154">**Browse**</span></span>  
 <span data-ttu-id="cd85e-155">瀏覽以尋找根資料夾。</span><span class="sxs-lookup"><span data-stu-id="cd85e-155">Browse to locate the root folder.</span></span>  
  
 <span data-ttu-id="cd85e-156">**檔案**</span><span class="sxs-lookup"><span data-stu-id="cd85e-156">**Files**</span></span>  
 <span data-ttu-id="cd85e-157">指定要列舉的檔案。</span><span class="sxs-lookup"><span data-stu-id="cd85e-157">Specify the files to enumerate.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cd85e-158">使用萬用字元 (\*) 即可指定要包含在集合中的檔案。</span><span class="sxs-lookup"><span data-stu-id="cd85e-158">Use wildcard characters (\*) to specify the files to include in the collection.</span></span> <span data-ttu-id="cd85e-159">例如，若要包括名稱內含 "abc" 的檔案，請使用下列篩選：\*abc\*。</span><span class="sxs-lookup"><span data-stu-id="cd85e-159">For example, to include files with names that contain "abc", use the following filter: \*abc\*.</span></span>  
>   
>  <span data-ttu-id="cd85e-160">當您指定副檔名時，此列舉值也會傳回附加其他字元之相同副檔名的檔案</span><span class="sxs-lookup"><span data-stu-id="cd85e-160">When you specify a file name extension, the enumerator also returns files that have the same extension with additional characters appended.</span></span> <span data-ttu-id="cd85e-161">(這個行為與作業系統中 **dir** 命令的行為相同，而且此命令也會針對回溯相容性比較 8.3 檔案名稱)。列舉值的這個行為可能會導致非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="cd85e-161">(This is the same behavior as that of the **dir** command in the operating system, which also compares 8.3 file names for backward compatibility.) This behavior of the enumerator could cause unexpected results.</span></span> <span data-ttu-id="cd85e-162">例如，您只想要列舉 Excel 2003 檔案，而且指定了 "\*.xls"。</span><span class="sxs-lookup"><span data-stu-id="cd85e-162">For example, you want to enumerate only Excel 2003 files, and you specify "\*.xls".</span></span> <span data-ttu-id="cd85e-163">不過，此列舉值也會傳回 Excel 2007 檔案，因為這些檔案的副檔名為 ".xlsx"。</span><span class="sxs-lookup"><span data-stu-id="cd85e-163">However, the enumerator will also return Excel 2007 files because those files have the extension, ".xlsx".</span></span>  
>   
>  <span data-ttu-id="cd85e-164">您可以使用運算式指定要包括在集合中的檔案，方法是展開 [集合]  頁面上的 [運算式]  ，選取 **FileSpec** 屬性，然後按一下省略符號按鈕 (...) 來新增屬性運算式。</span><span class="sxs-lookup"><span data-stu-id="cd85e-164">You can use an expression to specify the files to include in a collection, by expanding **Expressions** on the **Collection** page, selecting the **FileSpec** property, and then clicking the ellipsis button (...) to add the property expression.</span></span> <span data-ttu-id="cd85e-165">如需動態選取所指定檔案的詳細資訊，請參閱[SSIS-動態設定檔案遮罩： FileSpec](https://rajsudeep.blogspot.com/2010/09/ssisdynamically-set-file-mask-filespec.html)</span><span class="sxs-lookup"><span data-stu-id="cd85e-165">For more information about dynamically selecting specified files, see [SSIS-Dynamically set File Mask : FileSpec](https://rajsudeep.blogspot.com/2010/09/ssisdynamically-set-file-mask-filespec.html)</span></span>  
  
 <span data-ttu-id="cd85e-166">**完整**</span><span class="sxs-lookup"><span data-stu-id="cd85e-166">**Fully qualified**</span></span>  
 <span data-ttu-id="cd85e-167">選取即可擷取檔案名稱的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="cd85e-167">Select to retrieve the fully qualified path of file names.</span></span> <span data-ttu-id="cd85e-168">如果在檔案選項中指定萬用字元，則會傳回符合篩選的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="cd85e-168">If wildcard characters are specified in the Files option, then the fully-qualified paths that are returned match the filter.</span></span>  
  
 <span data-ttu-id="cd85e-169">**只有名稱**</span><span class="sxs-lookup"><span data-stu-id="cd85e-169">**Name only**</span></span>  
 <span data-ttu-id="cd85e-170">選取即可只擷取檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="cd85e-170">Select to retrieve only the file names.</span></span> <span data-ttu-id="cd85e-171">如果在檔案選項中指定萬用字元，則會傳回符合篩選的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="cd85e-171">If wildcard characters are specified in the Files option, then the file names returned match the filter.</span></span>  
  
 <span data-ttu-id="cd85e-172">**名稱和副檔名**</span><span class="sxs-lookup"><span data-stu-id="cd85e-172">**Name and extension**</span></span>  
 <span data-ttu-id="cd85e-173">選取即可擷取檔案名稱及其副檔名。</span><span class="sxs-lookup"><span data-stu-id="cd85e-173">Select to retrieve the file names and their file name extensions.</span></span> <span data-ttu-id="cd85e-174">如果在檔案選項中指定萬用字元，則會傳回符合篩選的檔案名稱和副檔名。</span><span class="sxs-lookup"><span data-stu-id="cd85e-174">If wildcard characters are specified in the Files option, then the name and extension of files returned match the filter.</span></span>  
  
 <span data-ttu-id="cd85e-175">**周遊子資料夾**</span><span class="sxs-lookup"><span data-stu-id="cd85e-175">**Traverse Subfolders**</span></span>  
 <span data-ttu-id="cd85e-176">選取即可在列舉中包含子資料夾。</span><span class="sxs-lookup"><span data-stu-id="cd85e-176">Select to include the subfolders in the enumeration.</span></span>  
  
### <a name="enumerator--foreach-item-enumerator"></a><span data-ttu-id="cd85e-177">列舉值 = Foreach 項目列舉值</span><span class="sxs-lookup"><span data-stu-id="cd85e-177">Enumerator = Foreach Item Enumerator</span></span>  
 <span data-ttu-id="cd85e-178">Foreach 項目列舉值可用來列舉集合中的項目。</span><span class="sxs-lookup"><span data-stu-id="cd85e-178">You use the Foreach Item enumerator to enumerate items in a collection.</span></span> <span data-ttu-id="cd85e-179">您指定資料行和資料行值，即可定義集合中的項目。</span><span class="sxs-lookup"><span data-stu-id="cd85e-179">You define the items in the collection by specifying columns and column values.</span></span> <span data-ttu-id="cd85e-180">一個資料列中的所有資料行都可定義項目。</span><span class="sxs-lookup"><span data-stu-id="cd85e-180">The columns in a row define an item.</span></span> <span data-ttu-id="cd85e-181">例如，指定用來執行「執行處理」工作之可執行檔及該工作所使用之工作目錄的項目會有兩個資料行，一個會列出可執行檔名稱，而另一個會列出工作目錄。</span><span class="sxs-lookup"><span data-stu-id="cd85e-181">For example, an item that specifies the executables that an Execute Process task runs and the working directory that the task uses has two columns, one that lists the names of executables and one that lists the working directory.</span></span> <span data-ttu-id="cd85e-182">資料列數目會決定迴圈的重複次數。</span><span class="sxs-lookup"><span data-stu-id="cd85e-182">The number of rows determines the number of times that the loop is repeated.</span></span> <span data-ttu-id="cd85e-183">如果資料表有 10 個資料列，則迴圈會重複 10 次。</span><span class="sxs-lookup"><span data-stu-id="cd85e-183">If the table has 10 rows, the loop repeats 10 times.</span></span>  
  
 <span data-ttu-id="cd85e-184">若要更新執行處理工作的屬性，則使用資料行的索引，您可以將變數對應至項目資料行。</span><span class="sxs-lookup"><span data-stu-id="cd85e-184">To update the properties of the Execute Process task, you map variables to item columns by using the index of the column.</span></span> <span data-ttu-id="cd85e-185">列舉值項目中所定義之第一個資料行的索引值為 0，第二個資料行則為 1，以此類推。</span><span class="sxs-lookup"><span data-stu-id="cd85e-185">The first column defined in the enumerator item has the index value 0, the second column 1, and so on.</span></span> <span data-ttu-id="cd85e-186">每次重複迴圈時，都會更新變數值。</span><span class="sxs-lookup"><span data-stu-id="cd85e-186">The variable values are updated with each repeat of the loop.</span></span> <span data-ttu-id="cd85e-187">然後，會透過使用這些變數的屬性運算式來更新「執行處理」工作的 `Executable` 和 `WorkingDirectory` 屬性。</span><span class="sxs-lookup"><span data-stu-id="cd85e-187">The `Executable` and `WorkingDirectory` properties of the Execute Process task can then be updated by property expressions that use these variables.</span></span>  
  
 <span data-ttu-id="cd85e-188">**定義 For Each 項目集合中的項目**</span><span class="sxs-lookup"><span data-stu-id="cd85e-188">**Define the items in the For Each Item collection**</span></span>  
 <span data-ttu-id="cd85e-189">提供資料表中每個資料行的值。</span><span class="sxs-lookup"><span data-stu-id="cd85e-189">Provide a value for each column in the table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cd85e-190">在資料列資料行輸入值之後，就會在資料表中自動加入新的資料列。</span><span class="sxs-lookup"><span data-stu-id="cd85e-190">A new row is automatically added to the table after you enter values in row columns.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cd85e-191">如果提供的值與資料行資料類型不相容，文字就會以紅色顯示。</span><span class="sxs-lookup"><span data-stu-id="cd85e-191">If the values provided are not compatible with the column data type, the text is colored red.</span></span>  
  
 <span data-ttu-id="cd85e-192">**資料行資料類型**</span><span class="sxs-lookup"><span data-stu-id="cd85e-192">**Column data type**</span></span>  
 <span data-ttu-id="cd85e-193">列出使用中資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="cd85e-193">Lists the data type of the active column.</span></span>  
  
 <span data-ttu-id="cd85e-194">**移除**</span><span class="sxs-lookup"><span data-stu-id="cd85e-194">**Remove**</span></span>  
 <span data-ttu-id="cd85e-195">選取項目，然後按一下 **[移除]** 即可從清單中移除。</span><span class="sxs-lookup"><span data-stu-id="cd85e-195">Select an item, and then click **Remove** to remove it from the list.</span></span>  
  
 <span data-ttu-id="cd85e-196">**資料行**</span><span class="sxs-lookup"><span data-stu-id="cd85e-196">**Columns**</span></span>  
 <span data-ttu-id="cd85e-197">按一下即可在項目中設定資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="cd85e-197">Click to configure the data type of the columns in the item.</span></span>  
  
 <span data-ttu-id="cd85e-198">**相關主題：** [For Each 項目資料行對話方塊 UI 參考](../../2014/integration-services/for-each-item-columns-dialog-box-ui-reference.md)</span><span class="sxs-lookup"><span data-stu-id="cd85e-198">**Related Topics:** [For Each Item Columns Dialog Box UI Reference](../../2014/integration-services/for-each-item-columns-dialog-box-ui-reference.md)</span></span>  
  
### <a name="enumerator--foreach-ado-enumerator"></a><span data-ttu-id="cd85e-199">列舉值 = Foreach ADO 列舉值</span><span class="sxs-lookup"><span data-stu-id="cd85e-199">Enumerator = Foreach ADO Enumerator</span></span>  
 <span data-ttu-id="cd85e-200">Foreach ADO 列舉值可用來列舉 ADO 或 ADO.NET 物件中的資料列或資料表，而這類物件是儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="cd85e-200">You use the Foreach ADO enumerator to enumerate rows or tables in an ADO or ADO.NET object that is stored in a variable.</span></span> <span data-ttu-id="cd85e-201">例如，如果 Foreach 迴圈包括將資料集寫入變數的指令碼工作，您可以使用 Foreach ADO 列舉值來列舉該資料集中的資料列。</span><span class="sxs-lookup"><span data-stu-id="cd85e-201">For example, if the Foreach Loop includes a Script task that writes a dataset to a variable, you can use the Foreach ADO enumerator to enumerate the rows in the dataset.</span></span> <span data-ttu-id="cd85e-202">如果變數包含 ADO.NET 資料集，則可將列舉值設定成列舉多個資料表中的資料列，或設定成列舉資料表。</span><span class="sxs-lookup"><span data-stu-id="cd85e-202">If the variable contains an ADO.NET dataset, the enumerator can be configured to enumerate rows in multiple tables or to enumerate tables.</span></span>  
  
 <span data-ttu-id="cd85e-203">**ADO 物件來源變數**</span><span class="sxs-lookup"><span data-stu-id="cd85e-203">**ADO object source variable**</span></span>  
 <span data-ttu-id="cd85e-204">在清單中選取使用者自訂變數，或按一下 \<**New variable...**> 以建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="cd85e-204">Select a user-defined variable in the list, or click \<**New variable...**> to create a new variable.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cd85e-205">變數必須為物件資料類型，否則會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="cd85e-205">The variable must have the Object data type, otherwise an error occurs.</span></span>  
  
 <span data-ttu-id="cd85e-206">**相關主題：** [Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)、[新增變數](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="cd85e-206">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
 <span data-ttu-id="cd85e-207">**第一個資料表的資料列**</span><span class="sxs-lookup"><span data-stu-id="cd85e-207">**Rows in first table**</span></span>  
 <span data-ttu-id="cd85e-208">選取此選項即可只列舉第一個資料表的資料列。</span><span class="sxs-lookup"><span data-stu-id="cd85e-208">Select to enumerate only rows in the first table.</span></span>  
  
 <span data-ttu-id="cd85e-209">**所有資料表的資料列 (僅 ADO.NET 資料集)**</span><span class="sxs-lookup"><span data-stu-id="cd85e-209">**Rows in all tables (ADO.NET dataset only)**</span></span>  
 <span data-ttu-id="cd85e-210">選取即可列舉所有資料表的資料列。</span><span class="sxs-lookup"><span data-stu-id="cd85e-210">Select to enumerate rows in all tables.</span></span> <span data-ttu-id="cd85e-211">唯有所有列舉的物件都是相同 ADO.NET 資料集的成員時，才可以使用此選項。</span><span class="sxs-lookup"><span data-stu-id="cd85e-211">This option is available only if the objects to enumerate are all members of the same ADO.NET dataset.</span></span>  
  
 <span data-ttu-id="cd85e-212">**所有資料表 (僅 ADO.NET 資料集)**</span><span class="sxs-lookup"><span data-stu-id="cd85e-212">**All tables (ADO.NET dataset only)**</span></span>  
 <span data-ttu-id="cd85e-213">選取即可只列舉資料表。</span><span class="sxs-lookup"><span data-stu-id="cd85e-213">Select to enumerate tables only.</span></span>  
  
### <a name="enumerator--foreach-adonet-schema-rowset-enumerator"></a><span data-ttu-id="cd85e-214">列舉值 = Foreach ADO.NET 結構描述資料列集列舉值</span><span class="sxs-lookup"><span data-stu-id="cd85e-214">Enumerator = Foreach ADO.NET Schema Rowset Enumerator</span></span>  
 <span data-ttu-id="cd85e-215">Foreach ADO.NET 結構描述資料列集列舉值可用來列舉所指定之資料來源的結構描述。</span><span class="sxs-lookup"><span data-stu-id="cd85e-215">You use the Foreach ADO.NET Schema Rowset enumerator to enumerate a schema for a specified data source.</span></span> <span data-ttu-id="cd85e-216">例如，如果 Foreach 迴圈包括「執行 SQL」工作，您可以使用 Foreach ADO.NET 結構描述資料列集列舉值來列舉結構描述 (例如 **AdventureWorks** 資料庫中的資料行)，以及使用「執行 SQL」工作來取得結構描述權限。</span><span class="sxs-lookup"><span data-stu-id="cd85e-216">For example, if the Foreach Loop includes an Execute SQL task, you can use the Foreach ADO.NET Schema Rowset enumerator to enumerate schemas such as the columns in the **AdventureWorks** database, and the Execute SQL task to get the schema permissions.</span></span>  
  
 <span data-ttu-id="cd85e-217">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="cd85e-217">**Connection**</span></span>  
 <span data-ttu-id="cd85e-218">在清單中選取一個 ADO.NET 連線管理員，或按一下 \<**New connection...**> 即可建立新的 ADO.NET 連線管理員。</span><span class="sxs-lookup"><span data-stu-id="cd85e-218">Select an ADO.NET connection manager in the list, or click \<**New connection...**> to create a new ADO.NET connection manager.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="cd85e-219">ADO.NET 連接管理員必須使用 OLE DB 的 .NET 提供者。</span><span class="sxs-lookup"><span data-stu-id="cd85e-219">The ADO.NET connection manager must use a .NET provider for OLE DB.</span></span> <span data-ttu-id="cd85e-220">如果連接到 SQL Server，則建議使用的提供者是 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client，會列在 **[連接管理員]** 對話方塊的 **[OleDb 的 .Net 提供者]** 區段中。</span><span class="sxs-lookup"><span data-stu-id="cd85e-220">If connecting to SQL Server, the recommended provider to use is the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client, listed in the **.Net Providers for OleDb** section of the **Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="cd85e-221">**相關主題：** [ADO 連線管理員](connection-manager/ado-connection-manager.md)、[設定 ADO.NET 連線管理員](configure-ado-net-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="cd85e-221">**Related Topics:** [ADO Connection Manager](connection-manager/ado-connection-manager.md), [Configure ADO.NET Connection Manager](configure-ado-net-connection-manager.md)</span></span>  
  
 <span data-ttu-id="cd85e-222">**結構描述**</span><span class="sxs-lookup"><span data-stu-id="cd85e-222">**Schema**</span></span>  
 <span data-ttu-id="cd85e-223">選取要列舉的結構描述。</span><span class="sxs-lookup"><span data-stu-id="cd85e-223">Select the schema to enumerate.</span></span>  
  
 <span data-ttu-id="cd85e-224">**設定限制**</span><span class="sxs-lookup"><span data-stu-id="cd85e-224">**Set Restrictions**</span></span>  
 <span data-ttu-id="cd85e-225">設定要套用至指定之結構描述的限制。</span><span class="sxs-lookup"><span data-stu-id="cd85e-225">Set the restrictions to apply to the specified schema.</span></span>  
  
 <span data-ttu-id="cd85e-226">**相關主題：** [結構描述限制對話方塊](../../2014/integration-services/schema-restrictions-dialog-box.md)</span><span class="sxs-lookup"><span data-stu-id="cd85e-226">**Related Topics:** [Schema Restrictions Dialog Box](../../2014/integration-services/schema-restrictions-dialog-box.md)</span></span>  
  
### <a name="enumerator--foreach-from-variable-enumerator"></a><span data-ttu-id="cd85e-227">列舉值 = Foreach From Variable 列舉值</span><span class="sxs-lookup"><span data-stu-id="cd85e-227">Enumerator = Foreach From Variable Enumerator</span></span>  
 <span data-ttu-id="cd85e-228">Foreach From Variable 列舉值可用來列舉所指定之變數中可列舉的物件。</span><span class="sxs-lookup"><span data-stu-id="cd85e-228">You use the Foreach From Variable enumerator to enumerate the enumerable objects in the specified variable.</span></span> <span data-ttu-id="cd85e-229">例如，如果 Foreach 迴圈包括執行查詢並將結果儲存在變數中的「執行 SQL」工作，您可以使用 Foreach From Variable 列舉值來列舉查詢結果。</span><span class="sxs-lookup"><span data-stu-id="cd85e-229">For example, if the Foreach Loop includes an Execute SQL task that runs a query and stores the result in a variable, you can use the Foreach From Variable enumerator to enumerate the query results.</span></span>  
  
 <span data-ttu-id="cd85e-230">**變數**</span><span class="sxs-lookup"><span data-stu-id="cd85e-230">**Variable**</span></span>  
 <span data-ttu-id="cd85e-231">在清單中選取變數，或按一下 \<**New variable...**> 以建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="cd85e-231">Select a variable in the list, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="cd85e-232">**相關主題：** [Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)、[新增變數](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="cd85e-232">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
### <a name="enumerator--foreach-nodelist-enumerator"></a><span data-ttu-id="cd85e-233">列舉值 = Foreach NodeList 列舉值</span><span class="sxs-lookup"><span data-stu-id="cd85e-233">Enumerator = Foreach NodeList Enumerator</span></span>  
 <span data-ttu-id="cd85e-234">Foreach Nodelist 列舉值可用來列舉因為將 XPath 運算式套用至 XML 檔案而產生的 XML 節點集合。</span><span class="sxs-lookup"><span data-stu-id="cd85e-234">You use the Foreach Nodelist enumerator to enumerate the set of XML nodes that results from applying an XPath expression to an XML file.</span></span> <span data-ttu-id="cd85e-235">例如，如果 Foreach 迴圈包括指令碼工作，則您可使用 Foreach NodeList 列舉值將符合 XPath 運算式條件的值從 XML 檔案傳送給該指令碼工作。</span><span class="sxs-lookup"><span data-stu-id="cd85e-235">For example, if the Foreach Loop includes a Script task, you can use the Foreach NodeList enumerator to pass a value that meets the XPath expression criteria from the XML file to the Script task.</span></span>  
  
 <span data-ttu-id="cd85e-236">套用至 XML 檔案的 XPath 運算式就是儲存在 OuterXPathString 屬性中的外部 XPath 作業。</span><span class="sxs-lookup"><span data-stu-id="cd85e-236">The XPath expression that applies to the XML file is the outer XPath operation, stored in the OuterXPathString property.</span></span> <span data-ttu-id="cd85e-237">如果 XPath 列舉類型設定為 `ElementCollection` ，則 Foreach NodeList 列舉值可以將儲存在 InnerXPathString 屬性中的內部 XPath 運算式套用至元素的集合。</span><span class="sxs-lookup"><span data-stu-id="cd85e-237">If the XPath enumeration type is set to `ElementCollection`, the Foreach NodeList enumerator can apply an inner XPath expression, stored in the InnerXPathString property, to a collection of element.</span></span>  
  
 <span data-ttu-id="cd85e-238">若要深入了解 XML 文件和資料，請參閱 MSDN Library 中的[在 .NET Framework 內採用 XML](https://go.microsoft.com/fwlink/?LinkId=56214)。</span><span class="sxs-lookup"><span data-stu-id="cd85e-238">To learn more about working with XML documents and data, see "[Employing XML in the .NET Framework](https://go.microsoft.com/fwlink/?LinkId=56214)" in the MSDN Library.</span></span>  
  
 <span data-ttu-id="cd85e-239">**DocumentSourceType**</span><span class="sxs-lookup"><span data-stu-id="cd85e-239">**DocumentSourceType**</span></span>  
 <span data-ttu-id="cd85e-240">選取 XML 文件的來源類型。</span><span class="sxs-lookup"><span data-stu-id="cd85e-240">Select the source type of the XML document.</span></span> <span data-ttu-id="cd85e-241">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="cd85e-241">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="cd85e-242">值</span><span class="sxs-lookup"><span data-stu-id="cd85e-242">Value</span></span>|<span data-ttu-id="cd85e-243">描述</span><span class="sxs-lookup"><span data-stu-id="cd85e-243">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cd85e-244">**直接輸入**</span><span class="sxs-lookup"><span data-stu-id="cd85e-244">**Direct input**</span></span>|<span data-ttu-id="cd85e-245">設定 XML 文件的來源。</span><span class="sxs-lookup"><span data-stu-id="cd85e-245">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="cd85e-246">**檔案連接**</span><span class="sxs-lookup"><span data-stu-id="cd85e-246">**File connection**</span></span>|<span data-ttu-id="cd85e-247">選取包含 XML 文件的檔案。</span><span class="sxs-lookup"><span data-stu-id="cd85e-247">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="cd85e-248">**變數**</span><span class="sxs-lookup"><span data-stu-id="cd85e-248">**Variable**</span></span>|<span data-ttu-id="cd85e-249">設定包含 XML 文件的變數來源。</span><span class="sxs-lookup"><span data-stu-id="cd85e-249">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="cd85e-250">**DocumentSource**</span><span class="sxs-lookup"><span data-stu-id="cd85e-250">**DocumentSource**</span></span>  
 <span data-ttu-id="cd85e-251">如果 [DocumentSourceType]  設定為 [直接輸入]  ，請提供 XML 程式碼，或按一下省略符號 (...) 按鈕，以使用 [文件來源編輯器]  對話方塊來提供 XML。</span><span class="sxs-lookup"><span data-stu-id="cd85e-251">If **DocumentSourceType** is set to **Direct input**, provide the XML code, or click the ellipsis (...) button to provide XML by using the **Document Source Edito**r dialog box.</span></span>  
  
 <span data-ttu-id="cd85e-252">如果 [DocumentSourceType] 設定為 [檔案連線]，請選取檔案連線管理員，或按一下 \<**New connection...**>，以建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="cd85e-252">If **DocumentSourceType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="cd85e-253">**相關主題：** [檔案連線管理員](connection-manager/file-connection-manager.md)、[檔案連線管理員編輯器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="cd85e-253">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="cd85e-254">如果 [DocumentSourceType] 設定為 [變數]，請選取現有的變數，或按一下 \<**New variable...**>，以建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="cd85e-254">If **DocumentSourceType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="cd85e-255">**相關主題：** [Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)、[新增變數](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="cd85e-255">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
 <span data-ttu-id="cd85e-256">**EnumerationType**</span><span class="sxs-lookup"><span data-stu-id="cd85e-256">**EnumerationType**</span></span>  
 <span data-ttu-id="cd85e-257">從清單中選取列舉類型。</span><span class="sxs-lookup"><span data-stu-id="cd85e-257">Select an enumeration type from the list.</span></span> <span data-ttu-id="cd85e-258">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="cd85e-258">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="cd85e-259">值</span><span class="sxs-lookup"><span data-stu-id="cd85e-259">Value</span></span>|<span data-ttu-id="cd85e-260">描述</span><span class="sxs-lookup"><span data-stu-id="cd85e-260">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cd85e-261">**Navigator**</span><span class="sxs-lookup"><span data-stu-id="cd85e-261">**Navigator**</span></span>|<span data-ttu-id="cd85e-262">使用 XPathNavigator 列舉。</span><span class="sxs-lookup"><span data-stu-id="cd85e-262">Enumerate using an XPathNavigator.</span></span>|  
|<span data-ttu-id="cd85e-263">**節點**</span><span class="sxs-lookup"><span data-stu-id="cd85e-263">**Node**</span></span>|<span data-ttu-id="cd85e-264">列舉 XPath 作業傳回的節點。</span><span class="sxs-lookup"><span data-stu-id="cd85e-264">Enumerate nodes returned by an XPath operation.</span></span>|  
|<span data-ttu-id="cd85e-265">**NodeText**</span><span class="sxs-lookup"><span data-stu-id="cd85e-265">**NodeText**</span></span>|<span data-ttu-id="cd85e-266">列舉 XPath 作業傳回的文字節點。</span><span class="sxs-lookup"><span data-stu-id="cd85e-266">Enumerate text nodes returned by an XPath operation.</span></span>|  
|`ElementCollection`|<span data-ttu-id="cd85e-267">列舉 XPath 作業傳回的元素節點。</span><span class="sxs-lookup"><span data-stu-id="cd85e-267">Enumerates element nodes returned by an XPath operation.</span></span>|  
  
 <span data-ttu-id="cd85e-268">**OuterXPathStringSourceType**</span><span class="sxs-lookup"><span data-stu-id="cd85e-268">**OuterXPathStringSourceType**</span></span>  
 <span data-ttu-id="cd85e-269">選取 XPath 字串的來源類型。</span><span class="sxs-lookup"><span data-stu-id="cd85e-269">Select the source type of the XPath string.</span></span> <span data-ttu-id="cd85e-270">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="cd85e-270">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="cd85e-271">值</span><span class="sxs-lookup"><span data-stu-id="cd85e-271">Value</span></span>|<span data-ttu-id="cd85e-272">描述</span><span class="sxs-lookup"><span data-stu-id="cd85e-272">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cd85e-273">**直接輸入**</span><span class="sxs-lookup"><span data-stu-id="cd85e-273">**Direct input**</span></span>|<span data-ttu-id="cd85e-274">設定 XML 文件的來源。</span><span class="sxs-lookup"><span data-stu-id="cd85e-274">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="cd85e-275">**檔案連接**</span><span class="sxs-lookup"><span data-stu-id="cd85e-275">**File connection**</span></span>|<span data-ttu-id="cd85e-276">選取包含 XML 文件的檔案。</span><span class="sxs-lookup"><span data-stu-id="cd85e-276">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="cd85e-277">**變數**</span><span class="sxs-lookup"><span data-stu-id="cd85e-277">**Variable**</span></span>|<span data-ttu-id="cd85e-278">設定包含 XML 文件的變數來源。</span><span class="sxs-lookup"><span data-stu-id="cd85e-278">Set the source to a variable that contains the XML document.</span></span>|  
  
 `OuterXPathString`  
 <span data-ttu-id="cd85e-279">如果 [OuterXPathStringSourceType]  設定為 [直接輸入]  ，請提供 XPath 字串。</span><span class="sxs-lookup"><span data-stu-id="cd85e-279">If **OuterXPathStringSourceType** is set to **Direct input**, provide the XPath string.</span></span>  
  
 <span data-ttu-id="cd85e-280">如果 [OuterXPathStringSourceType] 設定為 [檔案連線]，請選取檔案連線管理員，或按一下 \<**New connection...**> 以建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="cd85e-280">If **OuterXPathStringSourceType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="cd85e-281">**相關主題：** [檔案連線管理員](connection-manager/file-connection-manager.md)、[檔案連線管理員編輯器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="cd85e-281">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="cd85e-282">如果 [OuterXPathStringSourceType] 設定為 [變數]，請選取現有的變數，或按一下 \<**New variable...**> 以建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="cd85e-282">If **OuterXPathStringSourceType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="cd85e-283">**相關主題：** [Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)、[新增變數](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="cd85e-283">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
 <span data-ttu-id="cd85e-284">**InnerElementType**</span><span class="sxs-lookup"><span data-stu-id="cd85e-284">**InnerElementType**</span></span>  
 <span data-ttu-id="cd85e-285">如果 [ **EnumerationType** ] 設定為 `ElementCollection` ，請在清單中選取內部元素的類型。</span><span class="sxs-lookup"><span data-stu-id="cd85e-285">If **EnumerationType** is set to `ElementCollection`, select the type of inner element in the list.</span></span>  
  
 <span data-ttu-id="cd85e-286">**InnerXPathStringSourceType**</span><span class="sxs-lookup"><span data-stu-id="cd85e-286">**InnerXPathStringSourceType**</span></span>  
 <span data-ttu-id="cd85e-287">選取內部 XPath 字串的來源類型。</span><span class="sxs-lookup"><span data-stu-id="cd85e-287">Select the source type of the inner XPath string.</span></span> <span data-ttu-id="cd85e-288">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="cd85e-288">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="cd85e-289">值</span><span class="sxs-lookup"><span data-stu-id="cd85e-289">Value</span></span>|<span data-ttu-id="cd85e-290">描述</span><span class="sxs-lookup"><span data-stu-id="cd85e-290">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cd85e-291">**直接輸入**</span><span class="sxs-lookup"><span data-stu-id="cd85e-291">**Direct input**</span></span>|<span data-ttu-id="cd85e-292">設定 XML 文件的來源。</span><span class="sxs-lookup"><span data-stu-id="cd85e-292">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="cd85e-293">**檔案連接**</span><span class="sxs-lookup"><span data-stu-id="cd85e-293">**File connection**</span></span>|<span data-ttu-id="cd85e-294">選取包含 XML 文件的檔案。</span><span class="sxs-lookup"><span data-stu-id="cd85e-294">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="cd85e-295">**變數**</span><span class="sxs-lookup"><span data-stu-id="cd85e-295">**Variable**</span></span>|<span data-ttu-id="cd85e-296">設定包含 XML 文件的變數來源。</span><span class="sxs-lookup"><span data-stu-id="cd85e-296">Set the source to a variable that contains the XML document.</span></span>|  
  
 `InnerXPathString`  
 <span data-ttu-id="cd85e-297">如果 [InnerXPathStringSourceType]  設定為 [直接輸入]  ，請提供 XPath 字串。</span><span class="sxs-lookup"><span data-stu-id="cd85e-297">If **InnerXPathStringSourceType** is set to **Direct input**, provide the XPath string.</span></span>  
  
 <span data-ttu-id="cd85e-298">如果 [InnerXPathStringSourceType] 設定為 [檔案連線]，請選取檔案連線管理員，或按一下 \<**New connection...**> 以建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="cd85e-298">If **InnerXPathStringSourceType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="cd85e-299">**相關主題：** [檔案連線管理員](connection-manager/file-connection-manager.md)、[檔案連線管理員編輯器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="cd85e-299">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="cd85e-300">如果 [InnerXPathStringSourceType] 設定為 [變數]，請選取現有的變數，或按一下 \<**New variable...**> 以建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="cd85e-300">If **InnerXPathStringSourceType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="cd85e-301">**相關主題：** [Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)、[新增變數](../../2014/integration-services/add-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="cd85e-301">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
### <a name="enumerator--foreach-smo-enumerator"></a><span data-ttu-id="cd85e-302">列舉值 = Foreach SMO 列舉值</span><span class="sxs-lookup"><span data-stu-id="cd85e-302">Enumerator = Foreach SMO Enumerator</span></span>  
 <span data-ttu-id="cd85e-303">Foreach SMO 列舉值可用來列舉 SQL Server 管理物件 (SMO) 物件。</span><span class="sxs-lookup"><span data-stu-id="cd85e-303">You use the Foreach SMO enumerator to enumerate SQL Server Management Object (SMO) objects.</span></span> <span data-ttu-id="cd85e-304">例如，如果 Foreach 迴圈包括「執行 SQL」工作，您可以使用 Foreach SMO 列舉值來列舉 **AdventureWorks** 資料庫中的資料表，並執行用來計算每個資料表中資料列數目的查詢。</span><span class="sxs-lookup"><span data-stu-id="cd85e-304">For example, if the Foreach Loop includes an Execute SQL task, you can use the Foreach SMO enumerator to enumerate the tables in the **AdventureWorks** database and run queries that counts the number of rows in each table.</span></span>  
  
 <span data-ttu-id="cd85e-305">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="cd85e-305">**Connection**</span></span>  
 <span data-ttu-id="cd85e-306">選取現有的 ADO.NET 連線管理員，或按一下 \<**New connection...**> 以建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="cd85e-306">Select an existing ADO.NET connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="cd85e-307">相關主題：[ADO.NET 連線管理員](connection-manager/ado-net-connection-manager.md)、[設定 ADO.NET 連線管理員](configure-ado-net-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="cd85e-307">Related Topics: [ADO.NET Connection Manager](connection-manager/ado-net-connection-manager.md), [Configure ADO.NET Connection Manager](configure-ado-net-connection-manager.md)</span></span>  
  
 <span data-ttu-id="cd85e-308">**列舉**</span><span class="sxs-lookup"><span data-stu-id="cd85e-308">**Enumerate**</span></span>  
 <span data-ttu-id="cd85e-309">指定要列舉的 SMO 物件。</span><span class="sxs-lookup"><span data-stu-id="cd85e-309">Specify the SMO object to enumerate.</span></span>  
  
 <span data-ttu-id="cd85e-310">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="cd85e-310">**Browse**</span></span>  
 <span data-ttu-id="cd85e-311">選取 SMO 列舉。</span><span class="sxs-lookup"><span data-stu-id="cd85e-311">Select the SMO enumeration.</span></span>  
  
 <span data-ttu-id="cd85e-312">**相關主題：** [選取 SMO 列舉對話方塊](../../2014/integration-services/select-smo-enumeration-dialog-box.md)</span><span class="sxs-lookup"><span data-stu-id="cd85e-312">**Related Topics:** [Select SMO Enumeration Dialog Box](../../2014/integration-services/select-smo-enumeration-dialog-box.md)</span></span>  
  
### <a name="enumerator--foreach-azure-blob-enumerator"></a><span data-ttu-id="cd85e-313">列舉值 = Foreach Azure Blob 的列舉值</span><span class="sxs-lookup"><span data-stu-id="cd85e-313">Enumerator = Foreach Azure Blob Enumerator</span></span>  
 <span data-ttu-id="cd85e-314">**Azure Blob 的列舉值**可讓 SSIS 封裝列舉指定 Blob 位置中的 Blob 檔案。</span><span class="sxs-lookup"><span data-stu-id="cd85e-314">The  **Azure Blob Enumerator**r enables an SSIS package to enumerate blob files in the specified blob location.</span></span> <span data-ttu-id="cd85e-315">列舉之 Blob 檔案的名稱可以儲存在變數中，也可以用於 Foreach 迴圈容器中的工作中。</span><span class="sxs-lookup"><span data-stu-id="cd85e-315">The name of enumerated blob file can be stored in a variable and used in tasks inside the Foreach Loop Container.</span></span>  
  
 <span data-ttu-id="cd85e-316">**Azure 儲存體連線管理員**</span><span class="sxs-lookup"><span data-stu-id="cd85e-316">**Azure storage connection manager**</span></span>  
 <span data-ttu-id="cd85e-317">選取現有的 Azure 儲存體連接管理員，或建立參考 Azure 儲存體帳戶的新連接管理員。</span><span class="sxs-lookup"><span data-stu-id="cd85e-317">Select an existing Azure Storage Connection Manager or create a new one that refers to an Azure Storage Account.</span></span>  
  
 <span data-ttu-id="cd85e-318">相關主題：[Azure 儲存體連線管理員](connection-manager/azure-storage-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="cd85e-318">Related Topics: [Azure Storage Connection Manager](connection-manager/azure-storage-connection-manager.md).</span></span>  
  
 <span data-ttu-id="cd85e-319">**Blob 容器名稱**</span><span class="sxs-lookup"><span data-stu-id="cd85e-319">**Blob container name**</span></span>  
 <span data-ttu-id="cd85e-320">指定包含要列舉之 Blob 檔案的 Blob 容器之名稱。</span><span class="sxs-lookup"><span data-stu-id="cd85e-320">Specify the name of the blob container that contains the blob files to be enumerated..</span></span>  
  
 <span data-ttu-id="cd85e-321">**Blob 目錄**</span><span class="sxs-lookup"><span data-stu-id="cd85e-321">**Blob directory**</span></span>  
 <span data-ttu-id="cd85e-322">指定指定包含要列舉之 Blob 檔案的 Blob 目錄。</span><span class="sxs-lookup"><span data-stu-id="cd85e-322">Specify the specify the blob directory that contains the blob files to be enumerated.</span></span> <span data-ttu-id="cd85e-323">Blob 目錄是虛擬的階層式結構。</span><span class="sxs-lookup"><span data-stu-id="cd85e-323">The blob directory is a virtual hierarchical structure.</span></span>  
  
 <span data-ttu-id="cd85e-324">**Blob 名稱篩選**</span><span class="sxs-lookup"><span data-stu-id="cd85e-324">**Blob name filter**</span></span>  
 <span data-ttu-id="cd85e-325">指定名稱篩選條件以列舉具有特定名稱模式的檔案。</span><span class="sxs-lookup"><span data-stu-id="cd85e-325">Specify a name filter to enumerate files with a certain name pattern.</span></span> <span data-ttu-id="cd85e-326">例如</span><span class="sxs-lookup"><span data-stu-id="cd85e-326">E.g.</span></span> <span data-ttu-id="cd85e-327">MySheet\*.xls\* 會包含 MySheet001.xls 及 MySheetABC.xlsx 一類的檔案。</span><span class="sxs-lookup"><span data-stu-id="cd85e-327">MySheet\*.xls\* will include files such as MySheet001.xls and MySheetABC.xlsx.</span></span>  
  
 <span data-ttu-id="cd85e-328">**Blob 的起迄時間範圍篩選**</span><span class="sxs-lookup"><span data-stu-id="cd85e-328">**Blob time range from/to filter**</span></span>  
 <span data-ttu-id="cd85e-329">指定時間範圍篩選條件。</span><span class="sxs-lookup"><span data-stu-id="cd85e-329">Specify a time range filter.</span></span> <span data-ttu-id="cd85e-330">這會列舉在 **TimeRangeFrom** 之後及在 **TimeRangeTo** 之前修改的檔案。</span><span class="sxs-lookup"><span data-stu-id="cd85e-330">Files modified after **TimeRangeFrom** and before **TimeRangeTo** will be enumerated.</span></span>  
### <a name="enumerator--foreach-adls-file-enumerator"></a><span data-ttu-id="cd85e-331"> 列舉值 = Foreach ADLS 檔案列舉值</span><span class="sxs-lookup"><span data-stu-id="cd85e-331">Enumerator = Foreach ADLS File Enumerator</span></span>  
<span data-ttu-id="cd85e-332">**ADLS 檔案列舉**值可讓 SSIS 封裝以篩選器列舉 ADLS 上的檔案。</span><span class="sxs-lookup"><span data-stu-id="cd85e-332">The **ADLS File Enumerator** enables an SSIS package to enumerate files on ADLS with filters.</span></span> <span data-ttu-id="cd85e-333">斜線 (`/`) 首碼的完整路徑可以儲存在變數中，並用於 Foreach 迴圈容器內的工作中。</span><span class="sxs-lookup"><span data-stu-id="cd85e-333">The slash (`/`)-prefixed full path of enumerated files can be stored in a variable and used in tasks inside the Foreach Loop Container.</span></span>
  
<span data-ttu-id="cd85e-334">**AzureDataLakeConnection**</span><span class="sxs-lookup"><span data-stu-id="cd85e-334">**AzureDataLakeConnection**</span></span>  
<span data-ttu-id="cd85e-335">指定 Azure Data Lake 連線管理員，或建立參考 ADLS 帳戶的新連線管理員。</span><span class="sxs-lookup"><span data-stu-id="cd85e-335">Specifies an Azure Data Lake connection manager, or creates a new one that refers to an ADLS account.</span></span>   
  
<span data-ttu-id="cd85e-336">**AzureDataLakeDirectory**</span><span class="sxs-lookup"><span data-stu-id="cd85e-336">**AzureDataLakeDirectory**</span></span>  
<span data-ttu-id="cd85e-337">指定要搜尋的 ADLS 目錄。</span><span class="sxs-lookup"><span data-stu-id="cd85e-337">Specifies the ADLS directory to search.</span></span>
  
<span data-ttu-id="cd85e-338">**FileNamePattern**</span><span class="sxs-lookup"><span data-stu-id="cd85e-338">**FileNamePattern**</span></span>  
<span data-ttu-id="cd85e-339">指定檔案名稱篩選。</span><span class="sxs-lookup"><span data-stu-id="cd85e-339">Specifies a file name filter.</span></span> <span data-ttu-id="cd85e-340">只會列舉名稱符合指定模式的檔案。</span><span class="sxs-lookup"><span data-stu-id="cd85e-340">Only files whose name matches the specified pattern will be enumerated.</span></span> <span data-ttu-id="cd85e-341">支援萬用字元 `*` 和 `?`。</span><span class="sxs-lookup"><span data-stu-id="cd85e-341">Wildcards `*` and `?` are supported.</span></span> 
  
<span data-ttu-id="cd85e-342">**SearchRecursively**</span><span class="sxs-lookup"><span data-stu-id="cd85e-342">**SearchRecursively**</span></span>  
<span data-ttu-id="cd85e-343">指定是否在指定的目錄內以遞迴方式搜尋。</span><span class="sxs-lookup"><span data-stu-id="cd85e-343">Specifies whether to search recursively within the specified directory.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="cd85e-344">外部資源</span><span class="sxs-lookup"><span data-stu-id="cd85e-344">External Resources</span></span>  
  
-   <span data-ttu-id="cd85e-345">bidn.com 上的部落格文章： [SSIS ForEach NodeList 列舉值](https://go.microsoft.com/fwlink/?LinkId=220671)。</span><span class="sxs-lookup"><span data-stu-id="cd85e-345">Blog entry, [SSIS For Each Node List Enumerator](https://go.microsoft.com/fwlink/?LinkId=220671), on bidn.com.</span></span>  
  
-   <span data-ttu-id="cd85e-346">Blog 專案， [SSIS-動態設定檔案遮罩： FileSpec](https://rajsudeep.blogspot.com/2010/09/ssisdynamically-set-file-mask-filespec.html)。</span><span class="sxs-lookup"><span data-stu-id="cd85e-346">Blog entry, [SSIS-Dynamically set File Mask : FileSpec](https://rajsudeep.blogspot.com/2010/09/ssisdynamically-set-file-mask-filespec.html).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd85e-347">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd85e-347">See Also</span></span>  
 <span data-ttu-id="cd85e-348">[Integration Services 錯誤和訊息參考](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="cd85e-348">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="cd85e-349">[[Foreach 迴圈編輯器] &#40;一般頁面&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="cd85e-349">[Foreach Loop Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="cd85e-350">[Foreach 迴圈編輯器 &#40;變數對應頁面&#41;](../../2014/integration-services/foreach-loop-editor-variable-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="cd85e-350">[Foreach Loop Editor &#40;Variable Mappings Page&#41;](../../2014/integration-services/foreach-loop-editor-variable-mappings-page.md) </span></span>  
 <span data-ttu-id="cd85e-351">[運算式頁面](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="cd85e-351">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="cd85e-352">For 迴圈容器</span><span class="sxs-lookup"><span data-stu-id="cd85e-352">For Loop Container</span></span>](control-flow/for-loop-container.md)  
  
  
