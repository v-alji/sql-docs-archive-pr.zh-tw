---
title: 使用 BCP 指定相容性的資料格式 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk exporting [SQL Server], compatibility
- bulk importing [SQL Server], compatibility
- compatibility [SQL Server], data formats
- data formats [SQL Server], compatibility
- bcp utility [SQL Server], compatibility
ms.assetid: cd5fc8c8-eab1-4165-9468-384f31e53f0a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5d12456760f32ddbd8cc434d474aebb0e0ecf141
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706525"
---
# <a name="specify-data-formats-for-compatibility-when-using-bcp-sql-server"></a><span data-ttu-id="99281-102">使用 bcp 指定相容性的資料格式 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="99281-102">Specify Data Formats for Compatibility when Using bcp (SQL Server)</span></span>
  <span data-ttu-id="99281-103">本主題描述資料格式屬性、欄位特定提示，以及以命令的非 xml 格式檔案來儲存逐欄位資料 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `bcp` 。</span><span class="sxs-lookup"><span data-stu-id="99281-103">This topic describes the data-format attributes, field-specific prompts, and storing field-by-field data in a non-xml format file of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`bcp` command.</span></span> <span data-ttu-id="99281-104">大量匯出 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料以大量匯入至另一個程式 (例如另一個資料庫程式) 時，了解這些資訊十分有用。</span><span class="sxs-lookup"><span data-stu-id="99281-104">Understanding these can be helpful when you bulk export [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data for bulk import into another program, such as another database program.</span></span> <span data-ttu-id="99281-105">在來源資料表中的預設資料格式 (原生、字元或 Unicode) 可能和另一個程式所預期的資料配置不相容。如果匯出資料時發生了不相容的狀況，您就必須描述資料配置的方式。</span><span class="sxs-lookup"><span data-stu-id="99281-105">The default data formats (native, character, or Unicode) in the source table might be incompatible with the data layout expected by the other program If an incompatibility exists, when you export the data, you must describe the data layout.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="99281-106">如不熟悉資料匯入或匯出的資料格式，請參閱 [大量匯入或大量匯出的資料格式 &#40;SQL Server&#41;](data-formats-for-bulk-import-or-bulk-export-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="99281-106">If you are unfamiliar with data formats for importing or exporting data, see [Data Formats for Bulk Import or Bulk Export &#40;SQL Server&#41;](data-formats-for-bulk-import-or-bulk-export-sql-server.md).</span></span>  
  
 <span data-ttu-id="99281-107">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="99281-107">**In This Topic:**</span></span>  
  
-   [<span data-ttu-id="99281-108">bcp 資料格式屬性</span><span class="sxs-lookup"><span data-stu-id="99281-108">bcp Data-Format Attributes</span></span>](#bcpDataFormatAttr)  
  
-   [<span data-ttu-id="99281-109">特定欄位提示的總覽</span><span class="sxs-lookup"><span data-stu-id="99281-109">Overview of the Field-Specific Prompts</span></span>](#FieldSpecificPrompts)  
  
-   [<span data-ttu-id="99281-110">以非 XML 格式檔案儲存逐欄位資料</span><span class="sxs-lookup"><span data-stu-id="99281-110">Storing Field-by-Field Data in a Non-XML Format File</span></span>](#FieldByFieldNonXmlFF)  
  
-   [<span data-ttu-id="99281-111">相關工作</span><span class="sxs-lookup"><span data-stu-id="99281-111">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="bcp-data-format-attributes"></a><a name="bcpDataFormatAttr"></a> <span data-ttu-id="99281-112">bcp 資料格式屬性</span><span class="sxs-lookup"><span data-stu-id="99281-112">bcp Data-Format Attributes</span></span>  
 <span data-ttu-id="99281-113">`bcp` 命令可讓您根據下列資料格式屬性，指定資料檔中每個欄位的結構：</span><span class="sxs-lookup"><span data-stu-id="99281-113">The `bcp` command allows you to specify the structure of each field in a data file in terms of the following data-format attributes:</span></span>  
  
-   <span data-ttu-id="99281-114">檔案儲存類型</span><span class="sxs-lookup"><span data-stu-id="99281-114">File storage type</span></span>  
  
     <span data-ttu-id="99281-115">*檔案儲存類型* 描述資料如何儲存在資料檔中。</span><span class="sxs-lookup"><span data-stu-id="99281-115">The *file storage type* describes how data is stored in the data file.</span></span> <span data-ttu-id="99281-116">資料可以依其資料庫資料表類型 (原生格式)、依其字元表示 (字元格式)，或者依支援隱含轉換的任何資料類型匯出至資料檔；例如，將 `smallint` 複製為 `int`。</span><span class="sxs-lookup"><span data-stu-id="99281-116">Data can be exported to a data file as its database table type (native format), in its character representation (character format), or as any data type where implicit conversion is supported; for example, copying a `smallint` as an `int`.</span></span> <span data-ttu-id="99281-117">使用者自訂資料類型會依其基底類型匯出。</span><span class="sxs-lookup"><span data-stu-id="99281-117">User-defined data types are exported as their base types.</span></span> <span data-ttu-id="99281-118">如需詳細資訊，請參閱 [使用 bcp 時指定檔案儲存類型 &#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="99281-118">For more information, see [Specify File Storage Type by Using bcp &#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md).</span></span>  
  
-   <span data-ttu-id="99281-119">前置長度</span><span class="sxs-lookup"><span data-stu-id="99281-119">Prefix length</span></span>  
  
     <span data-ttu-id="99281-120">為了讓原生格式的資料大量匯出至資料檔時，能夠有最精簡的檔案儲存方式，`bcp` 命令會在每個欄位前面都加上一個或多個字元，指出欄位的長度。</span><span class="sxs-lookup"><span data-stu-id="99281-120">To provide the most compact file storage for the bulk export of data in native format to a data file, the `bcp` command precedes each field with one or more characters that indicates the length of the field.</span></span> <span data-ttu-id="99281-121">這些字元稱作 *「長度前置字元」* (Length prefix characters)。</span><span class="sxs-lookup"><span data-stu-id="99281-121">These characters are called *length prefix characters*.</span></span> <span data-ttu-id="99281-122">如需詳細資訊，請參閱 [使用 bcp 時指定資料檔案的前置長度 &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="99281-122">For more information, see [Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md).</span></span>  
  
-   <span data-ttu-id="99281-123">欄位長度</span><span class="sxs-lookup"><span data-stu-id="99281-123">Field length</span></span>  
  
     <span data-ttu-id="99281-124">欄位長度會指出以字元格式表現資料所需的最大字元數。</span><span class="sxs-lookup"><span data-stu-id="99281-124">The field length indicates the maximum number of characters that are required to represent data in character format.</span></span> <span data-ttu-id="99281-125">如果資料是以原生格式儲存，則欄位長度為已知。</span><span class="sxs-lookup"><span data-stu-id="99281-125">The field length is already known if the data is stored in the native format.</span></span> <span data-ttu-id="99281-126">如需詳細資訊，請參閱 [使用 bcp 指定欄位長度 &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="99281-126">For more information, see [Specify Field Length by Using bcp &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md).</span></span>  
  
-   <span data-ttu-id="99281-127">欄位結束字元</span><span class="sxs-lookup"><span data-stu-id="99281-127">Field terminator</span></span>  
  
     <span data-ttu-id="99281-128">針對字元資料欄位，選擇性的結束字元讓您可以標示資料檔中每個欄位的結尾 (使用「欄位結束字元」  )，以及每個資料列的結尾 (使用「資料列結束字元」  )。</span><span class="sxs-lookup"><span data-stu-id="99281-128">For character data fields, optional terminating characters allow you to mark the end of each field in a data file (using a *field terminator*) and the end of each row (using a *row terminator*).</span></span> <span data-ttu-id="99281-129">結束字元可讓讀取資料檔的程式知道某個欄位或資料列在何處結束，另一個在何處開始。</span><span class="sxs-lookup"><span data-stu-id="99281-129">Terminating characters are one way to indicate to programs reading the data file where one field or row ends and another begins.</span></span> <span data-ttu-id="99281-130">如需詳細資訊，請參閱 [指定欄位與資料列結束字元 &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="99281-130">For more information, see [Specify Field and Row Terminators &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md).</span></span>  
  
##  <a name="overview-of-the-field-specific-prompts"></a><a name="FieldSpecificPrompts"></a> <span data-ttu-id="99281-131">欄位專用提示字元的概觀</span><span class="sxs-lookup"><span data-stu-id="99281-131">Overview of the Field-Specific Prompts</span></span>  
 <span data-ttu-id="99281-132">如果互動式 `bcp` 命令包含**in**或**out**選項，但不包含格式檔案參數 (**-f**) 或資料格式參數 (**-n**、 **-c**、 **-w**或 **-n**) ，則來源或目標資料表中的每個資料行都會依次出現每一個前述屬性的命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="99281-132">If an interactive `bcp` command contains the **in** or **out** option but does not also contain either the format file switch (**-f**) or a data-format switch (**-n**, **-c**, **-w**, or **-N**),  each column in the source or target table, the command prompts for each of the preceding attributes, in turn.</span></span> <span data-ttu-id="99281-133">在每個提示字元中，`bcp` 命令是根據資料表資料行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型來提供預設值。</span><span class="sxs-lookup"><span data-stu-id="99281-133">In each prompt, the `bcp` command provides a default value based on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type of the table column.</span></span> <span data-ttu-id="99281-134">接受所有提示字元的預設值，會和在命令行上指定原生格式 ( **-n**) 產生相同結果。</span><span class="sxs-lookup"><span data-stu-id="99281-134">Accepting the default value for all of the prompts produces the same result as specifying native format (**-n**) on the command line.</span></span> <span data-ttu-id="99281-135">每個提示都會將預設值顯示於方括號中：[*預設值*]。</span><span class="sxs-lookup"><span data-stu-id="99281-135">Each prompt displays a default value in brackets: [*default*].</span></span> <span data-ttu-id="99281-136">按下 ENTER 即可接受顯示的預設值。</span><span class="sxs-lookup"><span data-stu-id="99281-136">Pressing ENTER accepts the displayed default.</span></span> <span data-ttu-id="99281-137">若要指定預設以外的值，請在提示字元中輸入新值。</span><span class="sxs-lookup"><span data-stu-id="99281-137">To specify a value other than the default, enter the new value at the prompt.</span></span>  
  
### <a name="example"></a><span data-ttu-id="99281-138">範例</span><span class="sxs-lookup"><span data-stu-id="99281-138">Example</span></span>  
 <span data-ttu-id="99281-139">下列範例使用 `bcp` 命令，將資料以互動方式從 `HumanResources.myTeam` 資料表大量匯出至 `myTeam.txt` 檔案。</span><span class="sxs-lookup"><span data-stu-id="99281-139">The following example uses the `bcp` command to bulk export data from the `HumanResources.myTeam` table interactively to the `myTeam.txt` file.</span></span> <span data-ttu-id="99281-140">您必須先建立此資料表，才能執行範例。</span><span class="sxs-lookup"><span data-stu-id="99281-140">Before you can run the example, you must create this table.</span></span> <span data-ttu-id="99281-141">如需此資料表及建立方式的相關資訊，請參閱 [HumanResources.myTeam 範例資料表 &#40;SQL Server&#41;](humanresources-myteam-sample-table-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="99281-141">For information about the table and how to create it, see [HumanResources.myTeam Sample Table &#40;SQL Server&#41;](humanresources-myteam-sample-table-sql-server.md).</span></span>  
  
 <span data-ttu-id="99281-142">該命令不會指定格式檔案，也不會指定資料類型，因此會導致 `bcp` 出現提示詢問資料格式資訊。</span><span class="sxs-lookup"><span data-stu-id="99281-142">The command specifies neither a format file nor a data type, causing `bcp` to prompt for data-format information.</span></span> <span data-ttu-id="99281-143">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="99281-143">At the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows command prompt, enter:</span></span>  
  
```  
bcp AdventureWorks.HumanResources.myTeam out myTeam.txt -T  
```  
  
 <span data-ttu-id="99281-144">bcp 會針對每個資料行提示欄位專用的值。</span><span class="sxs-lookup"><span data-stu-id="99281-144">For each column, bcp prompts for field-specific values.</span></span> <span data-ttu-id="99281-145">下列範例將為資料表的 `EmployeeID` 和 `Name` 資料行，顯示欄位專用的提示字元，並為每個資料行建議預設的檔案儲存類型 (原生格式)。</span><span class="sxs-lookup"><span data-stu-id="99281-145">The following example shows the field-specific prompts for the `EmployeeID` and `Name` columns of the table, and suggests the default file storage type (the native format) for each column.</span></span> <span data-ttu-id="99281-146">`EmployeeID` 和 `Name` 資料行的前置長度分別為 0 和 2。</span><span class="sxs-lookup"><span data-stu-id="99281-146">The prefix lengths of the `EmployeeID` and `Name` column are 0 and 2, respectively.</span></span> <span data-ttu-id="99281-147">使用者指定逗號 (`,`)，作為每個欄位的結束字元。</span><span class="sxs-lookup"><span data-stu-id="99281-147">The user specifies a comma (`,`) as the terminator of each field.</span></span>  
  
 `Enter the file storage type of field EmployeeID [smallint]:`  
  
 `Enter prefix-length of field EmployeeID [0]:`  
  
 `Enter field terminator [none]:,`  
  
 `Enter the file storage type of field Name [nvarchar]:`  
  
 `Enter prefix length of field Name [2]:`  
  
 `Enter field terminator [none]:,`  
  
 `.`  
  
 `.`  
  
 `.`  
  
 <span data-ttu-id="99281-148">相等的提示字元 (視需要而定) 會依序顯示在每個資料表資料行中。</span><span class="sxs-lookup"><span data-stu-id="99281-148">Equivalent prompts (as needed) are displayed for each of the table columns in order.</span></span>  
  
##  <a name="storing-field-by-field-data-in-a-non-xml-format-file"></a><a name="FieldByFieldNonXmlFF"></a> <span data-ttu-id="99281-149">將逐欄資料儲存至非 XML 格式檔案中</span><span class="sxs-lookup"><span data-stu-id="99281-149">Storing Field-by-Field Data in a Non-XML Format File</span></span>  
 <span data-ttu-id="99281-150">指定所有的資料表資料行之後，`bcp` 命令會提示您選擇性地產生非 XML 格式檔案，該檔案儲存剛剛提供的逐欄資訊 (請參閱先前範例)。</span><span class="sxs-lookup"><span data-stu-id="99281-150">After all of the table columns are specified, the `bcp` command prompts you to optionally generate a non-XML format file that stores the field-by-field information just supplied (see the preceding example).</span></span> <span data-ttu-id="99281-151">如果您選擇產生格式檔案，則可以隨時匯出該資料表的資料，或將類結構化資料匯入到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="99281-151">If you choose to generate a format file, you can whenever you export data out of that table or import like-structured data into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="99281-152">您可以使用格式檔案，從資料檔中將資料大量匯入到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，或從資料表中大量匯出資料，而不需重新指定格式。</span><span class="sxs-lookup"><span data-stu-id="99281-152">You can use the format file to bulk import data from the data file into an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or to bulk export data from the table, without needing to respecify the format.</span></span> <span data-ttu-id="99281-153">如需詳細資訊，請參閱 [匯入或匯出資料的格式檔案 &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)＞。</span><span class="sxs-lookup"><span data-stu-id="99281-153">For more information, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="99281-154">下列範例會建立一個名為 `myFormatFile.fmt`的非 XML 格式檔案。</span><span class="sxs-lookup"><span data-stu-id="99281-154">The following example creates a non-XML format file named `myFormatFile.fmt`:</span></span>  
  
 `Do you want to save this format information in a file? [Y/n] y`  
  
 `Host filename: [bcp.fmt]myFormatFile.fmt`  
  
 <span data-ttu-id="99281-155">格式檔案的預設名稱為 bcp.fmt，但您也可以選擇指定不同的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="99281-155">The default name for the format file is bcp.fmt, but you can specify a different file name if you choose.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="99281-156">若為使用單一資料格式作為檔案儲存類型的資料檔 (例如字元或原生格式)，您可以快速建立格式檔案，而不需透過 [格式]  選項來匯出或匯入資料。</span><span class="sxs-lookup"><span data-stu-id="99281-156">For a data file that uses a single data format for its file-storage type, such as character or native format, you can quickly create a format file without exporting or importing data by using the **format** option.</span></span> <span data-ttu-id="99281-157">此方法的優點是容易使用，並且可讓您建立 XML 格式檔案或非 XML 格式檔案。</span><span class="sxs-lookup"><span data-stu-id="99281-157">This approach has the advantages of being easy and of allowing you to create either an XML format file or a non-XML format file.</span></span> <span data-ttu-id="99281-158">如需詳細資訊，請參閱[建立格式檔案 &#40;SQL Server&#41;](create-a-format-file-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="99281-158">For more information, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="99281-159">相關工作</span><span class="sxs-lookup"><span data-stu-id="99281-159">Related Tasks</span></span>  
  
-   [<span data-ttu-id="99281-160">使用 bcp 時指定檔案儲存類型 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="99281-160">Specify File Storage Type by Using bcp &#40;SQL Server&#41;</span></span>](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
-   [<span data-ttu-id="99281-161">使用 bcp 指定資料檔的前置長度 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="99281-161">Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;</span></span>](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
-   [<span data-ttu-id="99281-162">使用 bcp 指定欄位長度 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="99281-162">Specify Field Length by Using bcp &#40;SQL Server&#41;</span></span>](specify-field-length-by-using-bcp-sql-server.md)  
  
-   [<span data-ttu-id="99281-163">指定欄位與資料列結束字元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="99281-163">Specify Field and Row Terminators &#40;SQL Server&#41;</span></span>](specify-field-and-row-terminators-sql-server.md)  
  
## <a name="related-content"></a><span data-ttu-id="99281-164">相關內容</span><span class="sxs-lookup"><span data-stu-id="99281-164">Related Content</span></span>  
 <span data-ttu-id="99281-165">無。</span><span class="sxs-lookup"><span data-stu-id="99281-165">None.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99281-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99281-166">See Also</span></span>  
 <span data-ttu-id="99281-167">[資料的大量匯入及匯出 &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="99281-167">[Bulk Import and Export of Data &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md) </span></span>  
 <span data-ttu-id="99281-168">[大量匯入或大量匯出的資料格式 &#40;SQL Server&#41;](data-formats-for-bulk-import-or-bulk-export-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="99281-168">[Data Formats for Bulk Import or Bulk Export &#40;SQL Server&#41;](data-formats-for-bulk-import-or-bulk-export-sql-server.md) </span></span>  
 <span data-ttu-id="99281-169">[bcp 公用程式](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="99281-169">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 [<span data-ttu-id="99281-170">資料類型 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="99281-170">Data Types &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/data-types-transact-sql)  
  
  
