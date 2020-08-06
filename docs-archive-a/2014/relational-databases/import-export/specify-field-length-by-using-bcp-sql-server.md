---
title: 使用 BCP 指定欄位長度 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- native data format [SQL Server]
- default field lengths
- field length [SQL Server]
- data formats [SQL Server], field length
- bcp utility [SQL Server], field length
ms.assetid: 240f33ca-ef4a-413a-a4de-831885cb505b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 13343b4f3778df1bbe7ef1c99b3d06338f18631c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687885"
---
# <a name="specify-field-length-by-using-bcp-sql-server"></a><span data-ttu-id="db88e-102">使用 bcp 指定欄位長度 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="db88e-102">Specify Field Length by Using bcp (SQL Server)</span></span>
  <span data-ttu-id="db88e-103">欄位長度會指出以字元格式表現資料所需的最大字元數。</span><span class="sxs-lookup"><span data-stu-id="db88e-103">The field length indicates the maximum number of characters that are required to represent data in character format.</span></span> <span data-ttu-id="db88e-104">如果是以原生格式儲存資料的話，欄位長度眾所皆知；例如，`int` 資料類型會佔用 4 個位元組。</span><span class="sxs-lookup"><span data-stu-id="db88e-104">The field length is already known if the data is stored in the native format; for example, the `int` data type takes 4 bytes.</span></span> <span data-ttu-id="db88e-105">如果您針對前置長度指定為0， **bcp**命令會提示您輸入欄位長度、預設欄位長度，以及欄位長度對包含資料之資料檔案中資料儲存的影響 `char` 。</span><span class="sxs-lookup"><span data-stu-id="db88e-105">If you have indicated 0 for the prefix length, the **bcp** command prompts you for field length, the default field lengths, and the impact of field-length on data storage in data files that contain `char` data.</span></span>  
  
## <a name="the-bcp-prompt-for-field-length"></a><span data-ttu-id="db88e-106">bcp 提示輸入欄位長度</span><span class="sxs-lookup"><span data-stu-id="db88e-106">The bcp Prompt for Field Length</span></span>  
 <span data-ttu-id="db88e-107">如果互動式 **bcp** 命令包含 **in** 或 **out** 選項，但沒有格式檔案參數 ( **-f**) 或資料格式參數 ( **-n**、 **-c**、 **-w** 或 **-N**)，此命令就會提示您輸入每個資料欄位的欄位長度，如下所示：</span><span class="sxs-lookup"><span data-stu-id="db88e-107">If an interactive **bcp** command contains the **in** or **out** option without either the format file switch (**-f**) or a data-format switch (**-n**, **-c**, **-w**, or **-N**), the command prompts for the field length of each data field, as follows:</span></span>  
  
 `Enter length of field <field_name> [<default>]:`  
  
 <span data-ttu-id="db88e-108">如需在內容中顯示此提示的範例，請參閱[使用 bcp 時指定相容性的資料格式 &#40;SQL Server&#41;](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="db88e-108">For an example that shows this prompt in context, see [Specify Data Formats for Compatibility when Using bcp &#40;SQL Server&#41;](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db88e-109">以互動方式在 **bcp** 命令中指定所有欄位之後，此命令會提示您將每個欄位的回應以非 XML 格式的檔案加以儲存。</span><span class="sxs-lookup"><span data-stu-id="db88e-109">After you interactively specify all of the fields in a **bcp** command, the command prompts you save your responses for each field in a non-XML format file.</span></span> <span data-ttu-id="db88e-110">如需非 XML 格式檔案的詳細資訊，請參閱[非 XML 格式檔案 &#40;SQL Server&#41;](xml-format-files-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="db88e-110">For more information on non-XML format files, see [Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
 <span data-ttu-id="db88e-111">**bcp** 命令是否會提示輸入欄位長度，取決於以下數個因素：</span><span class="sxs-lookup"><span data-stu-id="db88e-111">Whether a **bcp** command prompts for field length depends on several factors, as follows:</span></span>  
  
-   <span data-ttu-id="db88e-112">當您複製的資料類型沒有固定長度，而且指定前置長度為 0 時， **bcp** 就會提示輸入欄位長度。</span><span class="sxs-lookup"><span data-stu-id="db88e-112">When you copy data types that are not of fixed length and you specify a prefix length of 0, **bcp** prompts for a field length.</span></span>  
  
-   <span data-ttu-id="db88e-113">將非字元資料轉換為字元資料時， **bcp** 會建議足以儲存資料的預設欄位長度。</span><span class="sxs-lookup"><span data-stu-id="db88e-113">When converting noncharacter data to character data, **bcp** suggests a default field length large enough to store the data.</span></span>  
  
-   <span data-ttu-id="db88e-114">如果是非字元的檔案儲存類型， **bcp** 命令就不會提示輸入欄位長度。</span><span class="sxs-lookup"><span data-stu-id="db88e-114">If the file storage type is noncharacter, the **bcp** command does not prompt for a field length.</span></span> <span data-ttu-id="db88e-115">該資料會以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 原生資料表示法 (原生格式) 儲存。</span><span class="sxs-lookup"><span data-stu-id="db88e-115">The data is stored in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native data representation (native format).</span></span>  
  
## <a name="using-default-field-lengths"></a><span data-ttu-id="db88e-116">使用預設的欄位長度</span><span class="sxs-lookup"><span data-stu-id="db88e-116">Using Default Field Lengths</span></span>  
 <span data-ttu-id="db88e-117">一般而言， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 建議您接受 **bcp**所建議的欄位長度預設值。</span><span class="sxs-lookup"><span data-stu-id="db88e-117">Generally, [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommends that you accept the **bcp**-suggested default values for the field length.</span></span> <span data-ttu-id="db88e-118">已建立字元模式資料檔案時，使用預設的欄位長度可確定不會截斷資料，而且不會發生數值溢位錯誤。</span><span class="sxs-lookup"><span data-stu-id="db88e-118">When a character mode data file is created, using the default field length ensures that data is not truncated and that numeric overflow errors do not occur.</span></span>  
  
 <span data-ttu-id="db88e-119">如果指定不正確的欄位長度，就會發生問題。</span><span class="sxs-lookup"><span data-stu-id="db88e-119">If you specify a field length that is incorrect, problems can occur.</span></span> <span data-ttu-id="db88e-120">例如，如果複製數值資料，而對該資料來說指定的欄位長度太短， **bcp** 公用程式就會印出溢位訊息，而且不會複製該資料。</span><span class="sxs-lookup"><span data-stu-id="db88e-120">For instance, if you copy numeric data and you specify a field length that is too short for the data, the **bcp** utility prints an overflow message and does not copy the data.</span></span> <span data-ttu-id="db88e-121">此外，如果您匯出 `datetime` 資料並為字元字串指定少於26個位元組的欄位長度， **bcp**公用程式就會截斷資料，而不會出現錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="db88e-121">Also, if you export `datetime` data and specify a field length of less than 26 bytes for the character string, the **bcp** utility truncates the data without an error message.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="db88e-122">使用預設的大小選項時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 預期會讀取整個字串。</span><span class="sxs-lookup"><span data-stu-id="db88e-122">When the default size option is used, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] expects to read an entire string.</span></span> <span data-ttu-id="db88e-123">在某些狀況下，使用預設欄位長度卻會導致發生「未預期的檔案結尾」錯誤。</span><span class="sxs-lookup"><span data-stu-id="db88e-123">In some situations, use of a default field length can lead to an "unexpected end of file" error.</span></span> <span data-ttu-id="db88e-124">一般來說， `money` `datetime` 當資料檔案中只有部分預期的欄位出現時，和資料類型會發生此錯誤; 例如， `datetime` 指定*mm* / *dd* / *yy*的值而沒有時間元件時，則會比格式的值所預期的24個字元長度短 `datetime` `char` 。</span><span class="sxs-lookup"><span data-stu-id="db88e-124">Typically, this error occurs with the `money` and `datetime` data types when only part of the expected field occurs in the data file; for example, when a `datetime` value of *mm*/*dd*/*yy* is specified without the time component and is, therefore, shorter than the expected 24 character length of a `datetime` value in `char` format.</span></span> <span data-ttu-id="db88e-125">若要避免此種錯誤類型，請使用欄位結束字元或固定長度資料欄位，或指定其他的值以變更預設的欄位長度。</span><span class="sxs-lookup"><span data-stu-id="db88e-125">To avoid this type of error, use field terminators or fixed-length data fields, or change the default field length by specifying another value.</span></span>  
  
### <a name="default-field-lengths-for-character-file-storage"></a><span data-ttu-id="db88e-126">字元檔案儲存的預設欄位長度</span><span class="sxs-lookup"><span data-stu-id="db88e-126">Default Field Lengths for Character File Storage</span></span>  
 <span data-ttu-id="db88e-127">下表列出資料的預設欄位長度，以儲存為字元檔案儲存類型。</span><span class="sxs-lookup"><span data-stu-id="db88e-127">The following table lists the default field lengths for data to be stored as a character-file storage type.</span></span> <span data-ttu-id="db88e-128">可為 Null 的資料長度與非 Null 的資料長度相同。</span><span class="sxs-lookup"><span data-stu-id="db88e-128">Nullable data is the same length as nonnull data.</span></span>  
  
|<span data-ttu-id="db88e-129">資料類型</span><span class="sxs-lookup"><span data-stu-id="db88e-129">Data type</span></span>|<span data-ttu-id="db88e-130">預設長度 (字元)</span><span class="sxs-lookup"><span data-stu-id="db88e-130">Default length (characters)</span></span>|  
|---------------|-----------------------------------|  
|`char`|<span data-ttu-id="db88e-131">該資料行的定義長度</span><span class="sxs-lookup"><span data-stu-id="db88e-131">Length defined for the column</span></span>|  
|`varchar`|<span data-ttu-id="db88e-132">該資料行的定義長度</span><span class="sxs-lookup"><span data-stu-id="db88e-132">Length defined for the column</span></span>|  
|`nchar`|<span data-ttu-id="db88e-133">該資料行定義長度的兩倍</span><span class="sxs-lookup"><span data-stu-id="db88e-133">Twice the length defined for the column</span></span>|  
|`nvarchar`|<span data-ttu-id="db88e-134">該資料行定義長度的兩倍</span><span class="sxs-lookup"><span data-stu-id="db88e-134">Twice the length defined for the column</span></span>|  
|`Text`|<span data-ttu-id="db88e-135">0</span><span class="sxs-lookup"><span data-stu-id="db88e-135">0</span></span>|  
|`ntext`|<span data-ttu-id="db88e-136">0</span><span class="sxs-lookup"><span data-stu-id="db88e-136">0</span></span>|  
|`bit`|<span data-ttu-id="db88e-137">1</span><span class="sxs-lookup"><span data-stu-id="db88e-137">1</span></span>|  
|`binary`|<span data-ttu-id="db88e-138">該資料行定義長度的兩倍 + 1</span><span class="sxs-lookup"><span data-stu-id="db88e-138">Twice the length defined for the column + 1</span></span>|  
|`varbinary`|<span data-ttu-id="db88e-139">該資料行定義長度的兩倍 + 1</span><span class="sxs-lookup"><span data-stu-id="db88e-139">Twice the length defined for the column + 1</span></span>|  
|`image`|<span data-ttu-id="db88e-140">0</span><span class="sxs-lookup"><span data-stu-id="db88e-140">0</span></span>|  
|`datetime`|<span data-ttu-id="db88e-141">24</span><span class="sxs-lookup"><span data-stu-id="db88e-141">24</span></span>|  
|`smalldatetime`|<span data-ttu-id="db88e-142">24</span><span class="sxs-lookup"><span data-stu-id="db88e-142">24</span></span>|  
|`float`|<span data-ttu-id="db88e-143">30</span><span class="sxs-lookup"><span data-stu-id="db88e-143">30</span></span>|  
|`real`|<span data-ttu-id="db88e-144">30</span><span class="sxs-lookup"><span data-stu-id="db88e-144">30</span></span>|  
|`int`|<span data-ttu-id="db88e-145">12</span><span class="sxs-lookup"><span data-stu-id="db88e-145">12</span></span>|  
|`bigint`|<span data-ttu-id="db88e-146">19</span><span class="sxs-lookup"><span data-stu-id="db88e-146">19</span></span>|  
|`smallint`|<span data-ttu-id="db88e-147">7</span><span class="sxs-lookup"><span data-stu-id="db88e-147">7</span></span>|  
|`tinyint`|<span data-ttu-id="db88e-148">5</span><span class="sxs-lookup"><span data-stu-id="db88e-148">5</span></span>|  
|`money`|<span data-ttu-id="db88e-149">30</span><span class="sxs-lookup"><span data-stu-id="db88e-149">30</span></span>|  
|`smallmoney`|<span data-ttu-id="db88e-150">30</span><span class="sxs-lookup"><span data-stu-id="db88e-150">30</span></span>|  
|`decimal`|<span data-ttu-id="db88e-151">41\*</span><span class="sxs-lookup"><span data-stu-id="db88e-151">41\*</span></span>|  
|`numeric`|<span data-ttu-id="db88e-152">41\*</span><span class="sxs-lookup"><span data-stu-id="db88e-152">41\*</span></span>|  
|`uniqueidentifier`|<span data-ttu-id="db88e-153">37</span><span class="sxs-lookup"><span data-stu-id="db88e-153">37</span></span>|  
|`timestamp`|<span data-ttu-id="db88e-154">17</span><span class="sxs-lookup"><span data-stu-id="db88e-154">17</span></span>|  
|`varchar(max)`|<span data-ttu-id="db88e-155">0</span><span class="sxs-lookup"><span data-stu-id="db88e-155">0</span></span>|  
|`varbinary(max)`|<span data-ttu-id="db88e-156">0</span><span class="sxs-lookup"><span data-stu-id="db88e-156">0</span></span>|  
|`nvarchar(max)`|<span data-ttu-id="db88e-157">0</span><span class="sxs-lookup"><span data-stu-id="db88e-157">0</span></span>|  
|<span data-ttu-id="db88e-158">UDT</span><span class="sxs-lookup"><span data-stu-id="db88e-158">UDT</span></span>|<span data-ttu-id="db88e-159">使用者自訂術語 (UDT) 資料行的長度</span><span class="sxs-lookup"><span data-stu-id="db88e-159">Length of the user-defined term (UDT) column</span></span>|  
|<span data-ttu-id="db88e-160">XML</span><span class="sxs-lookup"><span data-stu-id="db88e-160">XML</span></span>|<span data-ttu-id="db88e-161">0</span><span class="sxs-lookup"><span data-stu-id="db88e-161">0</span></span>|  
  
 <span data-ttu-id="db88e-162">\*如需 `decimal` 和資料類型的詳細資訊 `numeric` ，請參閱[decimal 和 numeric &#40;transact-sql&#41;](/sql/t-sql/data-types/decimal-and-numeric-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="db88e-162">\*For more information about the `decimal` and `numeric` data types, see [decimal and numeric &#40;Transact-SQL&#41;](/sql/t-sql/data-types/decimal-and-numeric-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db88e-163">`tinyint` 類型的資料行可包含 0 到 255 的數值；因此代表該範圍內任意數值所需的最大字元數為 3 (代表數值 100 到 255)。</span><span class="sxs-lookup"><span data-stu-id="db88e-163">A column of type `tinyint` can have values from 0 through 255; the maximum number of characters that are needed to represent any number in that range is three (representing values 100 through 255).</span></span>  
  
### <a name="default-field-lengths-for-native-file-storage"></a><span data-ttu-id="db88e-164">原生檔案儲存的預設欄位長度</span><span class="sxs-lookup"><span data-stu-id="db88e-164">Default Field Lengths for Native File Storage</span></span>  
 <span data-ttu-id="db88e-165">下表列出資料的預設欄位長度，以儲存為原生檔案儲存類型。</span><span class="sxs-lookup"><span data-stu-id="db88e-165">The following table lists the default field lengths for data to be stored as native file storage type.</span></span> <span data-ttu-id="db88e-166">可為 Null 的資料長度與非 Null 的資料長度相同，字元資料永遠都會以字元格式儲存。</span><span class="sxs-lookup"><span data-stu-id="db88e-166">Nullable data is the same length as nonnull data, and character data is always stored in character format.</span></span>  
  
|<span data-ttu-id="db88e-167">資料類型</span><span class="sxs-lookup"><span data-stu-id="db88e-167">Data type</span></span>|<span data-ttu-id="db88e-168">預設長度 (字元)</span><span class="sxs-lookup"><span data-stu-id="db88e-168">Default length (characters)</span></span>|  
|---------------|-----------------------------------|  
|`bit`|<span data-ttu-id="db88e-169">1</span><span class="sxs-lookup"><span data-stu-id="db88e-169">1</span></span>|  
|`binary`|<span data-ttu-id="db88e-170">該資料行的定義長度</span><span class="sxs-lookup"><span data-stu-id="db88e-170">Length defined for the column</span></span>|  
|`varbinary`|<span data-ttu-id="db88e-171">該資料行的定義長度</span><span class="sxs-lookup"><span data-stu-id="db88e-171">Length defined for the column</span></span>|  
|`image`|<span data-ttu-id="db88e-172">0</span><span class="sxs-lookup"><span data-stu-id="db88e-172">0</span></span>|  
|`datetime`|<span data-ttu-id="db88e-173">8</span><span class="sxs-lookup"><span data-stu-id="db88e-173">8</span></span>|  
|`smalldatetime`|<span data-ttu-id="db88e-174">4</span><span class="sxs-lookup"><span data-stu-id="db88e-174">4</span></span>|  
|`float`|<span data-ttu-id="db88e-175">8</span><span class="sxs-lookup"><span data-stu-id="db88e-175">8</span></span>|  
|`real`|<span data-ttu-id="db88e-176">4</span><span class="sxs-lookup"><span data-stu-id="db88e-176">4</span></span>|  
|`int`|<span data-ttu-id="db88e-177">4</span><span class="sxs-lookup"><span data-stu-id="db88e-177">4</span></span>|  
|`bigint`|<span data-ttu-id="db88e-178">8</span><span class="sxs-lookup"><span data-stu-id="db88e-178">8</span></span>|  
|`smallint`|<span data-ttu-id="db88e-179">2</span><span class="sxs-lookup"><span data-stu-id="db88e-179">2</span></span>|  
|`tinyint`|<span data-ttu-id="db88e-180">1</span><span class="sxs-lookup"><span data-stu-id="db88e-180">1</span></span>|  
|`money`|<span data-ttu-id="db88e-181">8</span><span class="sxs-lookup"><span data-stu-id="db88e-181">8</span></span>|  
|`smallmoney`|<span data-ttu-id="db88e-182">4</span><span class="sxs-lookup"><span data-stu-id="db88e-182">4</span></span>|  
|<span data-ttu-id="db88e-183">`decimal` <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="db88e-183">`decimal` <sup>1</sup></span></span>|<sup>*</sup>|  
|<span data-ttu-id="db88e-184">`numeric` <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="db88e-184">`numeric` <sup>1</sup></span></span>|<sup>*</sup>|  
|`uniqueidentifier`|<span data-ttu-id="db88e-185">16</span><span class="sxs-lookup"><span data-stu-id="db88e-185">16</span></span>|  
|`timestamp`|<span data-ttu-id="db88e-186">8</span><span class="sxs-lookup"><span data-stu-id="db88e-186">8</span></span>|  
  
 <span data-ttu-id="db88e-187"><sup>1</sup>如需 `decimal` 和資料類型的詳細資訊 `numeric` ，請參閱[decimal 和 numeric &#40;transact-sql&#41;](/sql/t-sql/data-types/decimal-and-numeric-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="db88e-187"><sup>1</sup> For more information about the `decimal` and `numeric` data types, see [decimal and numeric &#40;Transact-SQL&#41;](/sql/t-sql/data-types/decimal-and-numeric-transact-sql).</span></span>  
  
 <span data-ttu-id="db88e-188">在先前的所有案例中，若要建立一個資料檔案，之後重新載入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，以將所佔用的儲存空間保持在最低，請搭配預設的檔案儲存類型與預設的欄位長度和長度前置詞一起使用。</span><span class="sxs-lookup"><span data-stu-id="db88e-188">In all of the preceding cases, to create a data file for later reloading into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that keeps the storage space to a minimum, use a length prefix with the default file storage type and the default field length.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db88e-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db88e-189">See Also</span></span>  
 <span data-ttu-id="db88e-190">[bcp 公用程式](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="db88e-190">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="db88e-191">[資料類型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="db88e-191">[Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span></span>  
 <span data-ttu-id="db88e-192">[指定欄位與資料列結束字元 &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="db88e-192">[Specify Field and Row Terminators &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md) </span></span>  
 <span data-ttu-id="db88e-193">[使用 bcp 時指定資料檔案的前置長度 &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="db88e-193">[Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md) </span></span>  
 <span data-ttu-id="db88e-194">[使用 bcp 指定檔案儲存類型 &#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="db88e-194">[Specify File Storage Type by Using bcp &#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md) </span></span>  
 [<span data-ttu-id="db88e-195">大量匯入期間保留 Null 或使用預設值 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="db88e-195">Keep Nulls or Use Default Values During Bulk Import &#40;SQL Server&#41;</span></span>](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
  
