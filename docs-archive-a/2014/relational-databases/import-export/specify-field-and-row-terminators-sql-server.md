---
title: 指定欄位與資料列結束字元 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bcp utility [SQL Server], terminators
- field terminators [SQL Server]
- data formats [SQL Server], terminators
- row terminators [SQL Server]
- terminators [SQL Server]
ms.assetid: f68b6782-f386-4947-93c4-e89110800704
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 548beeae68f5585c5cf2ba56b67027532ab43b71
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708402"
---
# <a name="specify-field-and-row-terminators-sql-server"></a><span data-ttu-id="b1377-102">指定欄位與資料列結束字元 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b1377-102">Specify Field and Row Terminators (SQL Server)</span></span>
  <span data-ttu-id="b1377-103">針對字元資料欄位，選擇性結束字元可讓您使用「欄位結束字元」  標示資料檔案中每個欄位的結尾，並使用「資料列結束字元」  標示每個資料列的結尾。</span><span class="sxs-lookup"><span data-stu-id="b1377-103">For character data fields, optional terminating characters allow you to mark the end of each field in a data file with a *field terminator* and the end of each row with a *row terminator*.</span></span> <span data-ttu-id="b1377-104">結束字元是指示程式從欄位或資料列結束與開始的交接處讀取資料檔的一種方法。</span><span class="sxs-lookup"><span data-stu-id="b1377-104">Terminating characters are one way to indicate to programs that read the data file where one field or row ends and another field or row begins.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b1377-105">在使用原生或 Unicode 原生格式時，請使用長度前置詞，而不使用欄位結束字元。</span><span class="sxs-lookup"><span data-stu-id="b1377-105">When you use native or Unicode native format, use length prefixes rather than field terminators.</span></span> <span data-ttu-id="b1377-106">由於原生格式資料檔案存放格式為 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的內部二進位資料格式，因此原生格式資料可能會與結束字元相衝突。</span><span class="sxs-lookup"><span data-stu-id="b1377-106">Native format data can conflict with terminators because a native-format data file is stored in the [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] internal binary data format.</span></span>  
  
## <a name="characters-supported-as-terminators"></a><span data-ttu-id="b1377-107">支援為結束字元的字元</span><span class="sxs-lookup"><span data-stu-id="b1377-107">Characters Supported As Terminators</span></span>  
 <span data-ttu-id="b1377-108">**bcp** 命令、BULK INSERT 陳述式與 OPENROWSET 大量資料列集提供者，都支援使用各式字元作為欄位或資料列結束字元，且一律會尋找每個結束字元的第一個執行個體。</span><span class="sxs-lookup"><span data-stu-id="b1377-108">The **bcp** command, BULK INSERT statement, and the OPENROWSET bulk rowset provider support a variety of characters as field or row terminators and always look for the first instance of each terminator.</span></span> <span data-ttu-id="b1377-109">下表列出支援作為結束字元的字元。</span><span class="sxs-lookup"><span data-stu-id="b1377-109">The following table lists the supported characters for terminators.</span></span>  
  
|<span data-ttu-id="b1377-110">結束字元</span><span class="sxs-lookup"><span data-stu-id="b1377-110">Terminating character</span></span>|<span data-ttu-id="b1377-111">表示方式</span><span class="sxs-lookup"><span data-stu-id="b1377-111">Indicated by</span></span>|  
|---------------------------|------------------|  
|<span data-ttu-id="b1377-112">索引標籤</span><span class="sxs-lookup"><span data-stu-id="b1377-112">Tab</span></span>|<span data-ttu-id="b1377-113">\t</span><span class="sxs-lookup"><span data-stu-id="b1377-113">\t</span></span><br /><br /> <span data-ttu-id="b1377-114">這是預設欄位結束字元。</span><span class="sxs-lookup"><span data-stu-id="b1377-114">This is the default field terminator.</span></span>|  
|<span data-ttu-id="b1377-115">新行字元 (Newline Character)</span><span class="sxs-lookup"><span data-stu-id="b1377-115">Newline character</span></span>|<span data-ttu-id="b1377-116">\n</span><span class="sxs-lookup"><span data-stu-id="b1377-116">\n</span></span><br /><br /> <span data-ttu-id="b1377-117">這是預設資料列結束字元。</span><span class="sxs-lookup"><span data-stu-id="b1377-117">This is the default row terminator.</span></span>|  
|<span data-ttu-id="b1377-118">歸位字元/換行字元</span><span class="sxs-lookup"><span data-stu-id="b1377-118">Carriage return/line feed</span></span>|<span data-ttu-id="b1377-119">\r</span><span class="sxs-lookup"><span data-stu-id="b1377-119">\r</span></span>|  
|<span data-ttu-id="b1377-120">反斜線<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b1377-120">Backslash<sup>1</sup></span></span>|\\\|  
|<span data-ttu-id="b1377-121">Null 結束字元 (看不見結束字元) <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="b1377-121">Null terminator (nonvisible terminator)<sup>2</sup></span></span>|<span data-ttu-id="b1377-122">\0</span><span class="sxs-lookup"><span data-stu-id="b1377-122">\0</span></span>|  
|<span data-ttu-id="b1377-123">任何可列印的字元 (除了 Null 值、定位點、新行字元和 Return 鍵外，控制字元均無法列印)</span><span class="sxs-lookup"><span data-stu-id="b1377-123">Any printable character (control characters are not printable, except null, tab, newline, and carriage return)</span></span>|<span data-ttu-id="b1377-124">(\*、A、t、l 等等)</span><span class="sxs-lookup"><span data-stu-id="b1377-124">(\*, A, t, l, and so on)</span></span>|  
|<span data-ttu-id="b1377-125">最多包含 10 個可列印字元的字串，包括先前所列的一些或所有結束字元</span><span class="sxs-lookup"><span data-stu-id="b1377-125">String of up to 10 printable characters, including some or all of the terminators listed earlier</span></span>|<span data-ttu-id="b1377-126">(\*\*\t\*\*、end、!!!!!!!!!!、\t-\n 等等)</span><span class="sxs-lookup"><span data-stu-id="b1377-126">(\*\*\t\*\*, end, !!!!!!!!!!, \t-\n, and so on)</span></span>|  
  
 <span data-ttu-id="b1377-127"><sup>1</sup>只有 t、n、r、0和 ' \ 0 ' 字元可以與反斜線 escape 字元搭配使用，以產生控制字元。</span><span class="sxs-lookup"><span data-stu-id="b1377-127"><sup>1</sup> Only the t, n, r, 0 and '\0' characters work with the backslash escape character to produce a control character.</span></span>  
  
 <span data-ttu-id="b1377-128"><sup>2</sup>即使在列印時看不到 null 控制字元 ( \ 0) ，它也是資料檔案中的相異字元。</span><span class="sxs-lookup"><span data-stu-id="b1377-128"><sup>2</sup> Even though the null control character (\0) is not visible when printed, it is a distinct character in the data file.</span></span> <span data-ttu-id="b1377-129">這表示使用 null 控制字元做為欄位或資料列結束字元，和完全沒有欄位或資料列結束字元不同。</span><span class="sxs-lookup"><span data-stu-id="b1377-129">This means that using the null control character as a field or row terminator is different than having no field or row terminator at all.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b1377-130">如果在資料內發現結束字元，它會當作結束字元而非當作資料來解譯，而該字元之後的資料則會解譯為屬於下一個欄位或記錄。</span><span class="sxs-lookup"><span data-stu-id="b1377-130">If a terminator character occurs within the data, it is interpreted as a terminator, not as data, and the data after that character is interpreted as belonging to the next field or record.</span></span> <span data-ttu-id="b1377-131">因此，請小心選擇結束字元，確定這些結束字元絕不會出現在您的資料中。</span><span class="sxs-lookup"><span data-stu-id="b1377-131">Therefore, choose your terminators carefully to make sure that they never appear in your data.</span></span> <span data-ttu-id="b1377-132">例如，如果資料中包含低 Surrogate，此低 surrogate 欄位結束字元就不是欄位結束字元的好選項。</span><span class="sxs-lookup"><span data-stu-id="b1377-132">For example, a low surrogate field terminator would not be a good choice for a field terminator if the data contains that low surrogate.</span></span>  
  
## <a name="using-row-terminators"></a><span data-ttu-id="b1377-133">使用資料列結束字元</span><span class="sxs-lookup"><span data-stu-id="b1377-133">Using Row Terminators</span></span>  
 <span data-ttu-id="b1377-134">資料列結束字元可以和最後一個欄位的結束字元相同。</span><span class="sxs-lookup"><span data-stu-id="b1377-134">The row terminator can be the same character as the terminator for the last field.</span></span> <span data-ttu-id="b1377-135">不過，個別的資料列結束字元通常十分有用。</span><span class="sxs-lookup"><span data-stu-id="b1377-135">Generally, however, a distinct row terminator is useful.</span></span> <span data-ttu-id="b1377-136">例如，若要產生表格式輸出，請以新行字元 (\n) 結束每個資料列的最後一個欄位，並以定位字元 (Tab) 結束所有其他欄位。</span><span class="sxs-lookup"><span data-stu-id="b1377-136">For example, to produce tabular output, terminate the last field in each row with the newline character (\n) and all other fields with the tab character (\t).</span></span> <span data-ttu-id="b1377-137">若要將每個資料記錄放在資料檔中自己的那一行，請指定 \r\n 組合做為資料列結束字元。</span><span class="sxs-lookup"><span data-stu-id="b1377-137">To place each data record on its own line in the data file, specify the combination \r\n as the row terminator.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b1377-138">以互動方式使用 **bcp** 並指定 \n (新行) 作為資料列結束字元時， **bcp** 會自動以 \r (歸位字元) 字元當作前置詞，而產生資料列結束字元 \r\n。</span><span class="sxs-lookup"><span data-stu-id="b1377-138">When you use **bcp** interactively and specify \n (newline) as the row terminator, **bcp** automatically prefixes it with a \r (carriage return) character, which results in a row terminator of \r\n.</span></span>  
  
## <a name="specifying-terminators-for-bulk-export"></a><span data-ttu-id="b1377-139">指定大量匯出的結束字元</span><span class="sxs-lookup"><span data-stu-id="b1377-139">Specifying Terminators for Bulk Export</span></span>  
 <span data-ttu-id="b1377-140">當您大量匯出 `char` 或 `nchar` 資料，而且想要使用非預設的結束字元時，您必須指定**bcp**命令的結束字元。</span><span class="sxs-lookup"><span data-stu-id="b1377-140">When you bulk export `char` or `nchar` data, and want to use a non-default terminator, you must specify the terminator to the **bcp** command.</span></span> <span data-ttu-id="b1377-141">您可以使用下列方式指定結束字元：</span><span class="sxs-lookup"><span data-stu-id="b1377-141">You can specify terminators in any of the following ways:</span></span>  
  
-   <span data-ttu-id="b1377-142">使用格式檔案，按個別欄位逐一指定結束字元。</span><span class="sxs-lookup"><span data-stu-id="b1377-142">With a format file that specifies the terminator on a field-by-field basis.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b1377-143">如需格式檔案的詳細資訊，請參閱[匯入或匯出資料的格式檔案 &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="b1377-143">For information about how to use format files, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
-   <span data-ttu-id="b1377-144">不使用格式檔案，可使用下列替代方法：</span><span class="sxs-lookup"><span data-stu-id="b1377-144">Without a format file, the following alternatives exist:</span></span>  
  
    -   <span data-ttu-id="b1377-145">使用 **-t** 參數，對資料列中最後一個欄位以外的所有欄位，指定資料列結束字元，並使用 **-r** 參數指定資料列結束字元。</span><span class="sxs-lookup"><span data-stu-id="b1377-145">Using the **-t** switch to specify the row terminator for all the fields except the last field in the row and using the **-r** switch to specify a row terminator.</span></span>  
  
    -   <span data-ttu-id="b1377-146">使用字元格式參數 ( **-c** 或 **-w**) 但不使用 **-t** 參數，會將欄位結束字元設定為定位字元 \t。</span><span class="sxs-lookup"><span data-stu-id="b1377-146">Using a character-format switch (**-c** or **-w**) without the **-t** switch, which sets the field terminator to the tab character, \t.</span></span> <span data-ttu-id="b1377-147">這與指定 **-t**\t 相同。</span><span class="sxs-lookup"><span data-stu-id="b1377-147">This is the same as specifying **-t**\t.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="b1377-148">如果您指定 **-n** (原生資料) 或 **-N** (Unicode 原生) 參數，則不會插入結束字元。</span><span class="sxs-lookup"><span data-stu-id="b1377-148">If you specify the **-n** (native data) or **-N** (Unicode native) switch, terminators are not inserted.</span></span>  
  
    -   <span data-ttu-id="b1377-149">如果互動式 **bcp** 命令包含 **in** 或 **out** 選項，但不使用格式檔案參數 ( **-f**) 或資料格式參數 ( **-n**、 **-c**、 **-w**，或 **-N**)，而且您選擇不指定前置長度與欄位長度，則該命令會提示輸入每個欄位的欄位結束字元 (預設是無)：</span><span class="sxs-lookup"><span data-stu-id="b1377-149">If an interactive **bcp** command contains the **in** or **out** option without either the format file switch (**-f**) or a data-format switch (**-n**, **-c**, **-w**, or **-N**), and you have chosen not to specify prefix length and field length, the command prompts for the field terminator of each field, with a default of none:</span></span>  
  
         `Enter field terminator [none]:`  
  
         <span data-ttu-id="b1377-150">預設值通常是適合的選擇。</span><span class="sxs-lookup"><span data-stu-id="b1377-150">Generally, the default is a suitable choice.</span></span> <span data-ttu-id="b1377-151">不過，有關 `char` 或 `nchar` 資料欄位，請參閱以下＜使用結束字元的指導方針＞細項。</span><span class="sxs-lookup"><span data-stu-id="b1377-151">However, for `char` or `nchar` data fields, see the following subsection, "Guidelines for Using Terminators."</span></span> <span data-ttu-id="b1377-152">如需在內容中顯示此提示的範例，請參閱[使用 bcp 時指定相容性的資料格式 &#40;SQL Server&#41;](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="b1377-152">For an example that shows this prompt in context, see [Specify Data Formats for Compatibility when Using bcp &#40;SQL Server&#41;](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md).</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="b1377-153">以互動方式在 **bcp** 命令中指定所有欄位之後，此命令會提示您將每個欄位的回應以非 XML 格式的檔案加以儲存。</span><span class="sxs-lookup"><span data-stu-id="b1377-153">After you interactively specify all of the fields in a **bcp** command, the command prompts you save your responses for each field in a non-XML format file.</span></span> <span data-ttu-id="b1377-154">如需非 XML 格式檔案的詳細資訊，請參閱[非 XML 格式檔案 &#40;SQL Server&#41;](xml-format-files-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="b1377-154">For more information about non-XML format files, see [Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
### <a name="guidelines-for-using-terminators"></a><span data-ttu-id="b1377-155">使用結束字元的指導方針</span><span class="sxs-lookup"><span data-stu-id="b1377-155">Guidelines for Using Terminators</span></span>  
 <span data-ttu-id="b1377-156">在某些情況中，結束字元對 `char` 或 `nchar` 資料欄位而言很有用。</span><span class="sxs-lookup"><span data-stu-id="b1377-156">In some situations, a terminator is useful for a `char` or `nchar` data field.</span></span> <span data-ttu-id="b1377-157">例如：</span><span class="sxs-lookup"><span data-stu-id="b1377-157">For example:</span></span>  
  
-   <span data-ttu-id="b1377-158">資料檔中的資料行包含 Null 值，而此資料檔將要匯入至不了解前置長度資訊的程式。</span><span class="sxs-lookup"><span data-stu-id="b1377-158">For a data column that contains a null value in a data file that will be imported into a program that does not understand the prefix length information.</span></span>  
  
     <span data-ttu-id="b1377-159">包含 Null 值的任何資料行會被視為可變長度。</span><span class="sxs-lookup"><span data-stu-id="b1377-159">Any data column that contains a null value is considered variable length.</span></span> <span data-ttu-id="b1377-160">如果沒有使用前置長度，則需要結束字元識別 Null 欄位結尾並確定已正確解譯資料。</span><span class="sxs-lookup"><span data-stu-id="b1377-160">In the absence of prefix lengths, a terminator is necessary to identify the end of a null field, making sure that the data is correctly interpreted.</span></span>  
  
-   <span data-ttu-id="b1377-161">許多資料列只使用其部分空間的固定長度長資料行。</span><span class="sxs-lookup"><span data-stu-id="b1377-161">For a long fixed-length column whose space is only partially used by many rows.</span></span>  
  
     <span data-ttu-id="b1377-162">在這種狀況下，指定結束字元可縮小儲存空間，允許欄位視為可變長度欄位。</span><span class="sxs-lookup"><span data-stu-id="b1377-162">In this situation, specifying a terminator can minimize storage space allowing the field to be treated as a variable-length field.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="b1377-163">範例</span><span class="sxs-lookup"><span data-stu-id="b1377-163">Examples</span></span>  
 <span data-ttu-id="b1377-164">此範例會使用字元格式、以逗號作為欄位結束字元，而且以新行字元 (\n) 作為資料列結束字元，將資料從 `AdventureWorks``HumanResources.Department` 資料表大量匯出資料至 `Department-c-t.txt` 資料檔案。</span><span class="sxs-lookup"><span data-stu-id="b1377-164">This example bulk exports the data from the `AdventureWorks``HumanResources.Department` table to the `Department-c-t.txt` data file using character format, with a comma as a field terminator and the newline character (\n) as the row terminator.</span></span>  
  
 <span data-ttu-id="b1377-165">**bcp** 命令包含下列參數。</span><span class="sxs-lookup"><span data-stu-id="b1377-165">The **bcp** command contains the following switches.</span></span>  
  
|<span data-ttu-id="b1377-166">Switch</span><span class="sxs-lookup"><span data-stu-id="b1377-166">Switch</span></span>|<span data-ttu-id="b1377-167">描述</span><span class="sxs-lookup"><span data-stu-id="b1377-167">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b1377-168">**-c**</span><span class="sxs-lookup"><span data-stu-id="b1377-168">**-c**</span></span>|<span data-ttu-id="b1377-169">指定以字元資料載入資料欄位。</span><span class="sxs-lookup"><span data-stu-id="b1377-169">Specifies that the data fields be loaded as character data.</span></span>|  
|<span data-ttu-id="b1377-170">**-t** `,`</span><span class="sxs-lookup"><span data-stu-id="b1377-170">**-t** `,`</span></span>|<span data-ttu-id="b1377-171">指定逗號 (,) 做為欄位結束字元。</span><span class="sxs-lookup"><span data-stu-id="b1377-171">Specifies a comma (,) as the field terminator.</span></span>|  
|<span data-ttu-id="b1377-172">**-r** \n</span><span class="sxs-lookup"><span data-stu-id="b1377-172">**-r** \n</span></span>|<span data-ttu-id="b1377-173">指定資料列結束字元為新行字元。</span><span class="sxs-lookup"><span data-stu-id="b1377-173">Specifies the row terminator as a newline character.</span></span> <span data-ttu-id="b1377-174">此為預設資料列結束字元，因此可選擇性地加以指定。</span><span class="sxs-lookup"><span data-stu-id="b1377-174">This is the default row terminator, so specifying it is optional.</span></span>|  
|<span data-ttu-id="b1377-175">**-T**</span><span class="sxs-lookup"><span data-stu-id="b1377-175">**-T**</span></span>|<span data-ttu-id="b1377-176">指定 **bcp** 公用程式使用整合式安全性的信任連接，連接至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b1377-176">Specifies that the **bcp** utility connects to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with a trusted connection using integrated security.</span></span> <span data-ttu-id="b1377-177">如果未指定 **-T** ，則必須指定 **-U** 與 **-P** ，才能順利登入。</span><span class="sxs-lookup"><span data-stu-id="b1377-177">If **-T** is not specified, you need to specify **-U** and **-P** to successfully log in.</span></span>|  
  
 <span data-ttu-id="b1377-178">如需相關資訊，請參閱 [bcp Utility](../../tools/bcp-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="b1377-178">For more information, see [bcp Utility](../../tools/bcp-utility.md).</span></span>  
  
 <span data-ttu-id="b1377-179">在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="b1377-179">At the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows command prompt enter:</span></span>  
  
```  
bcp AdventureWorks.HumanResources.Department out C:\myDepartment-c-t.txt -c -t, -r \n -T  
```  
  
 <span data-ttu-id="b1377-180">這會建立 `Department-c-t.txt`，四個欄位中各包含 16 筆記錄。</span><span class="sxs-lookup"><span data-stu-id="b1377-180">This creates `Department-c-t.txt`, which contains 16 records with four fields each.</span></span> <span data-ttu-id="b1377-181">這些欄位會以逗號隔開。</span><span class="sxs-lookup"><span data-stu-id="b1377-181">The fields are separated by a comma.</span></span>  
  
## <a name="specifying-terminators-for-bulk-import"></a><span data-ttu-id="b1377-182">指定大量匯入的結束字元</span><span class="sxs-lookup"><span data-stu-id="b1377-182">Specifying Terminators for Bulk Import</span></span>  
 <span data-ttu-id="b1377-183">當您大量匯入 `char` 或 `nchar` 資料時，大量匯入命令必須辨識資料檔中使用的結束字元。</span><span class="sxs-lookup"><span data-stu-id="b1377-183">When you bulk import `char` or `nchar` data, the bulk-import command must recognize the terminators that are used in the data file.</span></span> <span data-ttu-id="b1377-184">指定結束字元的方式取決於大量匯入命令，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b1377-184">How terminators can be specified depends on the bulk-import command, as follows:</span></span>  
  
-   <span data-ttu-id="b1377-185">**bcp**</span><span class="sxs-lookup"><span data-stu-id="b1377-185">**bcp**</span></span>  
  
     <span data-ttu-id="b1377-186">指定匯入作業結束字元所使用的語法，與用於匯出作業的語法相同。</span><span class="sxs-lookup"><span data-stu-id="b1377-186">Specifying terminators for an import operation uses the same syntax as for an export operation.</span></span> <span data-ttu-id="b1377-187">如需詳細資訊，請參閱本主題前面的「指定大量匯出的結束字元」。</span><span class="sxs-lookup"><span data-stu-id="b1377-187">For more information, see "Specifying Terminators for Bulk Export," earlier in this topic.</span></span>  
  
-   <span data-ttu-id="b1377-188">BULK INSERT</span><span class="sxs-lookup"><span data-stu-id="b1377-188">BULK INSERT</span></span>  
  
     <span data-ttu-id="b1377-189">您可以使用下表所示的限定詞，針對格式檔案中的個別欄位或整個資料檔指定結束字元。</span><span class="sxs-lookup"><span data-stu-id="b1377-189">Terminators can be specified for individual fields in a format file or for the whole data file by using the qualifiers shown in the following table.</span></span>  
  
    |<span data-ttu-id="b1377-190">Qualifier</span><span class="sxs-lookup"><span data-stu-id="b1377-190">Qualifier</span></span>|<span data-ttu-id="b1377-191">描述</span><span class="sxs-lookup"><span data-stu-id="b1377-191">Description</span></span>|  
    |---------------|-----------------|  
    |<span data-ttu-id="b1377-192">FIELDTERMINATOR **= ' *`field_terminator`* '**</span><span class="sxs-lookup"><span data-stu-id="b1377-192">FIELDTERMINATOR **='*`field_terminator`*'**</span></span>|<span data-ttu-id="b1377-193">指定要用於字元和 Unicode 字元資料檔中的欄位結束字元。</span><span class="sxs-lookup"><span data-stu-id="b1377-193">Specifies the field terminator to be used for character and Unicode character data files.</span></span><br /><br /> <span data-ttu-id="b1377-194">預設值是 \t (定位字元)。</span><span class="sxs-lookup"><span data-stu-id="b1377-194">The default is \t (tab character).</span></span>|  
    |<span data-ttu-id="b1377-195">ROWTERMINATOR **= ' *`row_terminator`* '**</span><span class="sxs-lookup"><span data-stu-id="b1377-195">ROWTERMINATOR **='*`row_terminator`*'**</span></span>|<span data-ttu-id="b1377-196">指定要用於字元和 Unicode 字元資料檔中的資料列結束字元。</span><span class="sxs-lookup"><span data-stu-id="b1377-196">Specifies the row terminator to be used for character and Unicode character data files.</span></span><br /><br /> <span data-ttu-id="b1377-197">預設值是 \n (新行字元)。</span><span class="sxs-lookup"><span data-stu-id="b1377-197">The default is \n (newline character).</span></span>|  
  
     <span data-ttu-id="b1377-198">如需詳細資訊，請參閱 [BULK INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b1377-198">For more information, see [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).</span></span>  
  
-   <span data-ttu-id="b1377-199">INSERT ...SELECT \* FROM OPENROWSET(BULK...)</span><span class="sxs-lookup"><span data-stu-id="b1377-199">INSERT ... SELECT \* FROM OPENROWSET(BULK...)</span></span>  
  
     <span data-ttu-id="b1377-200">針對 OPENROWSET 大量資料列集提供者，只可以在格式檔案中指定結束字元 (除了大型物件資料類型以外都需要格式檔案)。</span><span class="sxs-lookup"><span data-stu-id="b1377-200">For the OPENROWSET bulk rowset provider, terminators can be specified only in the format file (which is required except for large-object data types).</span></span> <span data-ttu-id="b1377-201">如果字元資料檔使用非預設結束字元，則必須在格式檔案中加以定義。</span><span class="sxs-lookup"><span data-stu-id="b1377-201">If a character data file uses a non-default terminator, it must be defined in the format file.</span></span> <span data-ttu-id="b1377-202">如需詳細資訊，請參閱[建立格式檔案 &#40;SQL Server&#41;](create-a-format-file-sql-server.md) 和[使用格式檔案大量匯入資料 &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="b1377-202">For more information, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md) and [Use a Format File to Bulk Import Data &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md).</span></span>  
  
     <span data-ttu-id="b1377-203">如需有關 OPENROWSET BULK 子句的詳細資訊，請參閱 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b1377-203">For more information about the OPENROWSET BULK clause, see [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).</span></span>  
  
### <a name="examples"></a><span data-ttu-id="b1377-204">範例</span><span class="sxs-lookup"><span data-stu-id="b1377-204">Examples</span></span>  
 <span data-ttu-id="b1377-205">這一節中的範例會將字元資料從先前範例中建立的 `Department-c-t.txt` 資料檔，大量匯入到 `myDepartment` 範例資料庫中的 [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] 資料表。</span><span class="sxs-lookup"><span data-stu-id="b1377-205">The examples in this section bulk import character data form the `Department-c-t.txt` data file created in the preceding example into the `myDepartment` table in the [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] sample database.</span></span> <span data-ttu-id="b1377-206">您必須先建立這個資料表，才能執行範例。</span><span class="sxs-lookup"><span data-stu-id="b1377-206">Before you can run the examples, you must create this table.</span></span> <span data-ttu-id="b1377-207">在 **dbo** 結構描述下建立這個資料表時，請在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查詢編輯器中執行下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="b1377-207">To create this table under the **dbo** schema, in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute the following code:</span></span>  
  
```  
USE AdventureWorks;  
GO  
DROP TABLE myDepartment;  
CREATE TABLE myDepartment   
(DepartmentID smallint,  
Name nvarchar(50),  
GroupName nvarchar(50) NULL,  
ModifiedDate datetime not NULL CONSTRAINT DF_AddressType_ModifiedDate DEFAULT (GETDATE())  
);  
GO  
  
```  
  
#### <a name="a-using-bcp-to-interactively-specify-terminators"></a><span data-ttu-id="b1377-208">A.</span><span class="sxs-lookup"><span data-stu-id="b1377-208">A.</span></span> <span data-ttu-id="b1377-209">使用 bcp 以互動方式指定結束字元</span><span class="sxs-lookup"><span data-stu-id="b1377-209">Using bcp to interactively specify terminators</span></span>  
 <span data-ttu-id="b1377-210">下列範例會使用 `Department-c-t.txt` 命令，大量匯入 `bcp` 資料檔。</span><span class="sxs-lookup"><span data-stu-id="b1377-210">The following example bulk imports the `Department-c-t.txt` data file using a `bcp` command.</span></span> <span data-ttu-id="b1377-211">此命令與大量匯出命令使用相同的命令參數。</span><span class="sxs-lookup"><span data-stu-id="b1377-211">This command uses the same command switches as the bulk export command.</span></span> <span data-ttu-id="b1377-212">如需詳細資訊，請參閱本主題前面的「指定大量匯出的結束字元」。</span><span class="sxs-lookup"><span data-stu-id="b1377-212">For more information, see "Specifying Terminators for Bulk Export," earlier in this topic.</span></span>  
  
 <span data-ttu-id="b1377-213">在 Windows 命令提示字元上輸入：</span><span class="sxs-lookup"><span data-stu-id="b1377-213">At the Windows command prompt enter:</span></span>  
  
```  
bcp AdventureWorks..myDepartment in C:\myDepartment-c-t.txt -c -t , -r \n -T  
```  
  
#### <a name="b-using-bulk-insert-to-interactively-specify-terminators"></a><span data-ttu-id="b1377-214">B.</span><span class="sxs-lookup"><span data-stu-id="b1377-214">B.</span></span> <span data-ttu-id="b1377-215">使用 BULK INSERT 以互動方式指定結束字元</span><span class="sxs-lookup"><span data-stu-id="b1377-215">Using BULK INSERT to interactively specify terminators</span></span>  
 <span data-ttu-id="b1377-216">下列範例會使用 `Department-c-t.txt` 陳述式 (其中使用下表所示的限定詞)，大量匯入 `BULK INSERT` 資料檔。</span><span class="sxs-lookup"><span data-stu-id="b1377-216">The following example bulk imports the `Department-c-t.txt` data file using a `BULK INSERT` statement that uses the qualifiers shown in the following table.</span></span>  
  
|<span data-ttu-id="b1377-217">選項</span><span class="sxs-lookup"><span data-stu-id="b1377-217">Option</span></span>|<span data-ttu-id="b1377-218">屬性</span><span class="sxs-lookup"><span data-stu-id="b1377-218">Attribute</span></span>|  
|------------|---------------|  
|<span data-ttu-id="b1377-219">DATAFILETYPE **= ' `char` '**</span><span class="sxs-lookup"><span data-stu-id="b1377-219">DATAFILETYPE **='`char`'**</span></span>|<span data-ttu-id="b1377-220">指定以字元資料載入資料欄位。</span><span class="sxs-lookup"><span data-stu-id="b1377-220">Specifies that the data fields be loaded as character data.</span></span>|  
|<span data-ttu-id="b1377-221">FIELDTERMINATOR **='** `,` **'**</span><span class="sxs-lookup"><span data-stu-id="b1377-221">FIELDTERMINATOR **='**`,`**'**</span></span>|<span data-ttu-id="b1377-222">指定逗號 (`,`) 作為欄位結束字元。</span><span class="sxs-lookup"><span data-stu-id="b1377-222">Specifies a comma (`,`) as the field terminator.</span></span>|  
|<span data-ttu-id="b1377-223">ROWTERMINATOR **='** `\n` **'**</span><span class="sxs-lookup"><span data-stu-id="b1377-223">ROWTERMINATOR **='**`\n`**'**</span></span>|<span data-ttu-id="b1377-224">指定資料列結束字元為新行字元。</span><span class="sxs-lookup"><span data-stu-id="b1377-224">Specifies the row terminator as a newline character.</span></span>|  
  
 <span data-ttu-id="b1377-225">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 查詢編輯器中，執行下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="b1377-225">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] Query Editor, execute the following code:</span></span>  
  
```  
USE AdventureWorks;  
GO  
BULK INSERT myDepartment FROM 'C:\myDepartment-c-t.txt'  
   WITH (  
      DATAFILETYPE = 'char',  
      FIELDTERMINATOR = ',',  
      ROWTERMINATOR = '\n'  
);  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="b1377-226">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1377-226">See Also</span></span>  
 <span data-ttu-id="b1377-227">[bcp 公用程式](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="b1377-227">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="b1377-228">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b1377-228">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="b1377-229">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b1377-229">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="b1377-230">[使用 bcp 時指定欄位長度 &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b1377-230">[Specify Field Length by Using bcp &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md) </span></span>  
 <span data-ttu-id="b1377-231">[使用 bcp 時指定資料檔案的前置長度 &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b1377-231">[Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md) </span></span>  
 [<span data-ttu-id="b1377-232">使用 bcp 時指定檔案儲存類型 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b1377-232">Specify File Storage Type by Using bcp &#40;SQL Server&#41;</span></span>](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
  
