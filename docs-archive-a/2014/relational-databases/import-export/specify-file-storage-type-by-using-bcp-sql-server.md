---
title: 使用 BCP 指定檔案儲存類型 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bcp utility [SQL Server], file storage types
- importing data, file storage types
- native data format [SQL Server]
- file storage types [SQL Server]
- data formats [SQL Server], file storage types
ms.assetid: 85e12df8-1be7-4bdc-aea9-05aade085c06
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c1f3ad2a94ffe3e0f1db19a8e66f85497e7143dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592013"
---
# <a name="specify-file-storage-type-by-using-bcp-sql-server"></a><span data-ttu-id="d8470-102">使用 bcp 指定檔案儲存類型 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d8470-102">Specify File Storage Type by Using bcp (SQL Server)</span></span>
  <span data-ttu-id="d8470-103">*檔案儲存類型* 描述資料如何儲存在資料檔中。</span><span class="sxs-lookup"><span data-stu-id="d8470-103">The *file storage type* describes how data is stored in the data file.</span></span> <span data-ttu-id="d8470-104">資料可以依其資料庫資料表類型 (原生格式)、依其字元表示 (字元格式)，或者依支援隱含轉換的任何資料類型匯出至資料檔；例如，將 `smallint` 複製為 `int`。</span><span class="sxs-lookup"><span data-stu-id="d8470-104">Data can be exported to a data file as its database table type (native format), in its character representation (character format), or as any data type where implicit conversion is supported; for example, copying a `smallint` as an `int`.</span></span> <span data-ttu-id="d8470-105">使用者自訂資料類型會依其基底類型匯出。</span><span class="sxs-lookup"><span data-stu-id="d8470-105">User-defined data types are exported as their base types.</span></span>  
  
## <a name="the-bcp-prompt-for-file-storage-type"></a><span data-ttu-id="d8470-106">檔案儲存類型的 bcp 提示</span><span class="sxs-lookup"><span data-stu-id="d8470-106">The bcp Prompt for File Storage Type</span></span>  
 <span data-ttu-id="d8470-107">如果互動式 **bcp** 命令包含 **in** 或 **out** 選項，但沒有格式檔案參數 ( **-f**) 或資料格式參數 ( **-n**、 **-c**、 **-w**或 **-N**)，此命令就會提示您輸入每個資料欄位的檔案儲存類型，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d8470-107">If an interactive **bcp** command contains the **in** or **out** option without either the format file switch (**-f**) or a data-format switch (**-n**, **-c**, **-w**, or **-N**), the command prompts for the file storage type of each data field, as follows:</span></span>  
  
 `Enter the file storage type of field <field_name> [<default>]:`  
  
 <span data-ttu-id="d8470-108">您對此提示的回應視執行的工作而定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d8470-108">Your response to this prompt depends on the task you perform, as follows:</span></span>  
  
-   <span data-ttu-id="d8470-109">若要以最精簡的儲存方式 (原生資料格式)，將 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的資料大量匯出到資料檔案，請接受 **bcp** 提供的預設檔案儲存類型。</span><span class="sxs-lookup"><span data-stu-id="d8470-109">To bulk export data from an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to a data file in the most compact storage possible (native data format), accept the default file storage types that are provided by **bcp**.</span></span> <span data-ttu-id="d8470-110">如需原生檔案儲存類型的清單，請參閱此主題稍後的＜原生檔案儲存類型＞。</span><span class="sxs-lookup"><span data-stu-id="d8470-110">For a list of the native file storage types, see "Native File Storage Types," later in this topic.</span></span>  
  
-   <span data-ttu-id="d8470-111">若要以字元格式將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的資料大量匯出到資料檔案，請將資料表中所有資料行的檔案儲存類型指定為 `char`。</span><span class="sxs-lookup"><span data-stu-id="d8470-111">To bulk export data from an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to a data file in character format, specify `char` as the file storage type for all columns in the table.</span></span>  
  
-   <span data-ttu-id="d8470-112">若要將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的資料大量匯入資料檔案，對於以字元格式儲存的類型，請將檔案儲存類型指定為 `char`，對於以原生資料類型格式儲存的資料，請指定其中一個適當的檔案儲存類型：</span><span class="sxs-lookup"><span data-stu-id="d8470-112">To bulk import data to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a data file, specify the file storage type as `char` for types stored in character format and, for data stored in native data type format, specify one of the file storage types, as appropriate:</span></span>  
  
    |<span data-ttu-id="d8470-113">檔案儲存類型</span><span class="sxs-lookup"><span data-stu-id="d8470-113">File storage type</span></span>|<span data-ttu-id="d8470-114">在命令提示字元中輸入</span><span class="sxs-lookup"><span data-stu-id="d8470-114">Enter at command prompt</span></span>|  
    |-----------------------|-----------------------------|  
    |<span data-ttu-id="d8470-115">`char` <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d8470-115">`char` <sup>1</sup></span></span>|<span data-ttu-id="d8470-116">`c`[`har`]</span><span class="sxs-lookup"><span data-stu-id="d8470-116">`c`[`har`]</span></span>|  
    |`varchar`|`c[har]`|  
    |`nchar`|`w`|  
    |`nvarchar`|`w`|  
    |<span data-ttu-id="d8470-117">`text` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="d8470-117">`text` <sup>2</sup></span></span>|<span data-ttu-id="d8470-118">`T`[`ext`]</span><span class="sxs-lookup"><span data-stu-id="d8470-118">`T`[`ext`]</span></span>|  
    |`ntext2`|`W`|  
    |`binary`|`x`|  
    |`varbinary`|`x`|  
    |<span data-ttu-id="d8470-119">`image` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="d8470-119">`image` <sup>2</sup></span></span>|<span data-ttu-id="d8470-120">`I`[`mage`]</span><span class="sxs-lookup"><span data-stu-id="d8470-120">`I`[`mage`]</span></span>|  
    |`datetime`|<span data-ttu-id="d8470-121">**d[ate]**</span><span class="sxs-lookup"><span data-stu-id="d8470-121">**d[ate]**</span></span>|  
    |`smalldatetime`|`D`|  
    |`time`|`te`|  
    |`date`|`de`|  
    |`datetime2`|`d2`|  
    |`datetimeoffset`|`do`|  
    |`decimal`|`n`|  
    |`numeric`|`n`|  
    |`float`|<span data-ttu-id="d8470-122">**f[loat]**</span><span class="sxs-lookup"><span data-stu-id="d8470-122">**f[loat]**</span></span>|  
    |`real`|`r`|  
    |`Int`|<span data-ttu-id="d8470-123">**i[nt]**</span><span class="sxs-lookup"><span data-stu-id="d8470-123">**i[nt]**</span></span>|  
    |`bigint`|`B[igint]`|  
    |`smallint`|<span data-ttu-id="d8470-124">**s[mallint]**</span><span class="sxs-lookup"><span data-stu-id="d8470-124">**s[mallint]**</span></span>|  
    |`tinyint`|<span data-ttu-id="d8470-125">**t[inyint]**</span><span class="sxs-lookup"><span data-stu-id="d8470-125">**t[inyint]**</span></span>|  
    |`money`|<span data-ttu-id="d8470-126">**m[oney]**</span><span class="sxs-lookup"><span data-stu-id="d8470-126">**m[oney]**</span></span>|  
    |`smallmoney`|`M`|  
    |`bit`|`b[it]`|  
    |`uniqueidentifier`|`u`|  
    |`sql_variant`|`V[ariant]`|  
    |`timestamp`|`x`|  
    |<span data-ttu-id="d8470-127">`UDT` (使用者定義的資料類型)</span><span class="sxs-lookup"><span data-stu-id="d8470-127">`UDT` (a user-defined data type)</span></span>|`U`|  
    |`XML`|`X`|  
  
     <span data-ttu-id="d8470-128"><sup>1</sup>欄位長度、前置長度和結束字元的互動，可決定在資料檔案中配置的儲存空間量，以非字元匯出為檔案 `char` 儲存類型的資料。</span><span class="sxs-lookup"><span data-stu-id="d8470-128"><sup>1</sup> The interaction of field length, prefix length, and terminators determines the amount of storage space that is allocated in a data file for noncharacter data that is exported as the `char` file storage type.</span></span>  
  
     <span data-ttu-id="d8470-129"><sup>2</sup> `ntext` ，、 `text` 和 `image` 資料類型將會在未來的版本中移除 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d8470-129"><sup>2</sup> The `ntext`, `text`, and `image` data types will be removed in a future version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d8470-130">請避免在新的開發工作中使用這些資料類型，並規劃修改目前使用這些資料類型的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d8470-130">In new development work, avoid using these data types, and plan to modify applications that currently use them.</span></span> <span data-ttu-id="d8470-131">請改用 `nvarchar(max)`、`varchar(max)` 和 `varbinary(max)`。</span><span class="sxs-lookup"><span data-stu-id="d8470-131">Use `nvarchar(max)`, `varchar(max)`, and `varbinary(max)` instead.</span></span>  
  
## <a name="native-file-storage-types"></a><span data-ttu-id="d8470-132">原生檔案儲存類型</span><span class="sxs-lookup"><span data-stu-id="d8470-132">Native File Storage Types</span></span>  
 <span data-ttu-id="d8470-133">每個原生檔案儲存類型都記錄於格式檔案內，做為對應的主機檔案資料類型。</span><span class="sxs-lookup"><span data-stu-id="d8470-133">Each native file storage type is recorded in the format file as a corresponding host file data type.</span></span>  
  
|<span data-ttu-id="d8470-134">檔案儲存類型</span><span class="sxs-lookup"><span data-stu-id="d8470-134">File storage type</span></span>|<span data-ttu-id="d8470-135">主檔案資料類型</span><span class="sxs-lookup"><span data-stu-id="d8470-135">Host file data type</span></span>|  
|-----------------------|-------------------------|  
|<span data-ttu-id="d8470-136">`char` <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d8470-136">`char` <sup>1</sup></span></span>|<span data-ttu-id="d8470-137">SQLCHAR</span><span class="sxs-lookup"><span data-stu-id="d8470-137">SQLCHAR</span></span>|  
|`varchar`|<span data-ttu-id="d8470-138">SQLCHAR</span><span class="sxs-lookup"><span data-stu-id="d8470-138">SQLCHAR</span></span>|  
|`nchar`|<span data-ttu-id="d8470-139">SQLNCHAR</span><span class="sxs-lookup"><span data-stu-id="d8470-139">SQLNCHAR</span></span>|  
|`nvarchar`|<span data-ttu-id="d8470-140">SQLNCHAR</span><span class="sxs-lookup"><span data-stu-id="d8470-140">SQLNCHAR</span></span>|  
|<span data-ttu-id="d8470-141">`text` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="d8470-141">`text` <sup>2</sup></span></span>|<span data-ttu-id="d8470-142">SQLCHAR</span><span class="sxs-lookup"><span data-stu-id="d8470-142">SQLCHAR</span></span>|  
|<span data-ttu-id="d8470-143">`ntext` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="d8470-143">`ntext` <sup>2</sup></span></span>|<span data-ttu-id="d8470-144">SQLNCHAR</span><span class="sxs-lookup"><span data-stu-id="d8470-144">SQLNCHAR</span></span>|  
|`binary`|<span data-ttu-id="d8470-145">SQLBINARY</span><span class="sxs-lookup"><span data-stu-id="d8470-145">SQLBINARY</span></span>|  
|`varbinary`|<span data-ttu-id="d8470-146">SQLBINARY</span><span class="sxs-lookup"><span data-stu-id="d8470-146">SQLBINARY</span></span>|  
|<span data-ttu-id="d8470-147">`image` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="d8470-147">`image` <sup>2</sup></span></span>|<span data-ttu-id="d8470-148">SQLBINARY</span><span class="sxs-lookup"><span data-stu-id="d8470-148">SQLBINARY</span></span>|  
|`datetime`|<span data-ttu-id="d8470-149">SQLDATETIME</span><span class="sxs-lookup"><span data-stu-id="d8470-149">SQLDATETIME</span></span>|  
|`smalldatetime`|<span data-ttu-id="d8470-150">SQLDATETIM4</span><span class="sxs-lookup"><span data-stu-id="d8470-150">SQLDATETIM4</span></span>|  
|`decimal`|<span data-ttu-id="d8470-151">SQLDECIMAL</span><span class="sxs-lookup"><span data-stu-id="d8470-151">SQLDECIMAL</span></span>|  
|`numeric`|<span data-ttu-id="d8470-152">SQLNUMERIC</span><span class="sxs-lookup"><span data-stu-id="d8470-152">SQLNUMERIC</span></span>|  
|`float`|<span data-ttu-id="d8470-153">SQLFLT8</span><span class="sxs-lookup"><span data-stu-id="d8470-153">SQLFLT8</span></span>|  
|`real`|<span data-ttu-id="d8470-154">SQLFLT4</span><span class="sxs-lookup"><span data-stu-id="d8470-154">SQLFLT4</span></span>|  
|`int`|<span data-ttu-id="d8470-155">SQLINT</span><span class="sxs-lookup"><span data-stu-id="d8470-155">SQLINT</span></span>|  
|`bigint`|<span data-ttu-id="d8470-156">SQLBIGINT</span><span class="sxs-lookup"><span data-stu-id="d8470-156">SQLBIGINT</span></span>|  
|`smallint`|<span data-ttu-id="d8470-157">SQLSMALLINT</span><span class="sxs-lookup"><span data-stu-id="d8470-157">SQLSMALLINT</span></span>|  
|`tinyint`|<span data-ttu-id="d8470-158">SQLTINYINT</span><span class="sxs-lookup"><span data-stu-id="d8470-158">SQLTINYINT</span></span>|  
|`money`|<span data-ttu-id="d8470-159">SQLMONEY</span><span class="sxs-lookup"><span data-stu-id="d8470-159">SQLMONEY</span></span>|  
|`smallmoney`|<span data-ttu-id="d8470-160">SQLMONEY4</span><span class="sxs-lookup"><span data-stu-id="d8470-160">SQLMONEY4</span></span>|  
|`bit`|<span data-ttu-id="d8470-161">SQLBIT</span><span class="sxs-lookup"><span data-stu-id="d8470-161">SQLBIT</span></span>|  
|`uniqueidentifier`|<span data-ttu-id="d8470-162">SQLUNIQUEID</span><span class="sxs-lookup"><span data-stu-id="d8470-162">SQLUNIQUEID</span></span>|  
|`sql_variant`|<span data-ttu-id="d8470-163">SQLVARIANT</span><span class="sxs-lookup"><span data-stu-id="d8470-163">SQLVARIANT</span></span>|  
|`timestamp`|<span data-ttu-id="d8470-164">SQLBINARY</span><span class="sxs-lookup"><span data-stu-id="d8470-164">SQLBINARY</span></span>|  
|<span data-ttu-id="d8470-165">UDT (使用者定義資料類型)</span><span class="sxs-lookup"><span data-stu-id="d8470-165">UDT (a user-defined data type)</span></span>|<span data-ttu-id="d8470-166">SQLUDT</span><span class="sxs-lookup"><span data-stu-id="d8470-166">SQLUDT</span></span>|  
  
 <span data-ttu-id="d8470-167"><sup>1</sup>以字元格式儲存的資料檔案會使用 `char` 做為檔案儲存類型。</span><span class="sxs-lookup"><span data-stu-id="d8470-167"><sup>1</sup> Data files that are stored in character format use `char` as the file storage type.</span></span> <span data-ttu-id="d8470-168">因此，對於字元資料檔案，SQLCHAR 是唯一會出現在格式檔案中的資料類型。</span><span class="sxs-lookup"><span data-stu-id="d8470-168">Therefore, for character data files, SQLCHAR is the only data type that appears in a format file.</span></span>  
  
 <span data-ttu-id="d8470-169"><sup>2</sup>您無法將資料大量匯入 `text` `ntext` `image` 具有預設值的、和資料行。</span><span class="sxs-lookup"><span data-stu-id="d8470-169"><sup>2</sup> You cannot bulk import data into `text`, `ntext`, and `image` columns that have DEFAULT values.</span></span>  
  
## <a name="additional-considerations-for-file-storage-types"></a><span data-ttu-id="d8470-170">檔案儲存類型的額外考量</span><span class="sxs-lookup"><span data-stu-id="d8470-170">Additional Considerations for File Storage Types</span></span>  
 <span data-ttu-id="d8470-171">當您將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的資料大量匯出到資料檔案時：</span><span class="sxs-lookup"><span data-stu-id="d8470-171">When you bulk export data from an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to a data file:</span></span>  
  
-   <span data-ttu-id="d8470-172">您永遠可以將檔案儲存類型指定為 `char`。</span><span class="sxs-lookup"><span data-stu-id="d8470-172">You can always specify `char` as the file storage type.</span></span>  
  
-   <span data-ttu-id="d8470-173">如果您輸入的檔案儲存類型代表不正確隱含轉換，則**bcp**會失敗;例如，雖然您可以針對資料指定，但 `int` `smallint` 如果您 `smallint` 針對資料指定，就會 `int` 產生溢位錯誤。</span><span class="sxs-lookup"><span data-stu-id="d8470-173">If you enter a file storage type that represents an invalid implicit conversion, **bcp** fails; for example, though you can specify `int` for `smallint` data, if you specify `smallint` for `int` data, overflow errors result.</span></span>  
  
-   <span data-ttu-id="d8470-174">若 `float`、`money`、`datetime` 或 `int` 等非字元資料類型儲存為其資料庫類型時，資料會以 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 原生格式寫入資料檔案中。</span><span class="sxs-lookup"><span data-stu-id="d8470-174">When noncharacter data types such as `float`, `money`, `datetime`, or `int` are stored as their database types, the data is written to the data file in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native format.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d8470-175">以互動方式在 **bcp** 命令中指定所有欄位之後，此命令會提示您將每個欄位的回應以非 XML 格式的檔案加以儲存。</span><span class="sxs-lookup"><span data-stu-id="d8470-175">After you interactively specify all of the fields in a **bcp** command, the command prompts you save your responses for each field in a non-XML format file.</span></span> <span data-ttu-id="d8470-176">如需非 XML 格式檔案的詳細資訊，請參閱[非 XML 格式檔案 &#40;SQL Server&#41;](xml-format-files-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="d8470-176">For more information on non-XML format files, see [Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8470-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8470-177">See Also</span></span>  
 <span data-ttu-id="d8470-178">[bcp 公用程式](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="d8470-178">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="d8470-179">[資料類型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d8470-179">[Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span></span>  
 <span data-ttu-id="d8470-180">[使用 bcp 時指定欄位長度 &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d8470-180">[Specify Field Length by Using bcp &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md) </span></span>  
 <span data-ttu-id="d8470-181">[指定欄位與資料列結束字元 &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="d8470-181">[Specify Field and Row Terminators &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md) </span></span>  
 [<span data-ttu-id="d8470-182">使用 bcp 指定資料檔的前置長度 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d8470-182">Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;</span></span>](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
  
