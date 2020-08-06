---
title: 非 XML 格式檔案 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- non-XML format files
- format files [SQL Server], non-XML format files
- bulk importing [SQL Server], format files
ms.assetid: f566db3e-0a3b-4a61-9c84-49f8d42f5760
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8fb040cb60eb188a7878357e7b45ca1114df2cdb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708409"
---
# <a name="non-xml-format-files-sql-server"></a><span data-ttu-id="4193b-102">非 XML 格式檔案 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="4193b-102">Non-XML Format Files (SQL Server)</span></span>
  <span data-ttu-id="4193b-103">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中，有兩種格式檔案支援大量匯出和匯入： *「非 XML 格式檔案」* (Non-XML Format File) 和 *「XML 格式檔案」* (XML Format File)。</span><span class="sxs-lookup"><span data-stu-id="4193b-103">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], two types of format files are supported for bulk exporting and importing: *non-XML format files* and *XML format files*.</span></span>  
  
 <span data-ttu-id="4193b-104">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="4193b-104">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="4193b-105">優點</span><span class="sxs-lookup"><span data-stu-id="4193b-105">Benefits</span></span>](#Benefits)  
  
-   [<span data-ttu-id="4193b-106">非 XML 格式檔案的結構</span><span class="sxs-lookup"><span data-stu-id="4193b-106">Structure of Non-XML Format Files</span></span>](#Structure)  
  
-   [<span data-ttu-id="4193b-107">非 XML 格式檔案範例</span><span class="sxs-lookup"><span data-stu-id="4193b-107">Example of a Non-XML Format File</span></span>](#Examples)  
  
-   [<span data-ttu-id="4193b-108">相關工作</span><span class="sxs-lookup"><span data-stu-id="4193b-108">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="benefits-of-non-xml-format-files"></a><a name="Benefits"></a> <span data-ttu-id="4193b-109">非 XML 格式檔案的優點</span><span class="sxs-lookup"><span data-stu-id="4193b-109">Benefits of Non-XML Format Files</span></span>  
  
-   <span data-ttu-id="4193b-110">您可以在 **format** 命令中指定 **bcp** 選項，以自動建立非 XML 格式檔案。</span><span class="sxs-lookup"><span data-stu-id="4193b-110">You can create a non-XML format file automatically by specifying the **format** option in a **bcp** command.</span></span>  
  
-   <span data-ttu-id="4193b-111">在 **bcp** 命令中指定現有的格式檔案時，命令會使用記錄在格式檔案中的值，而且不提示您輸入檔案儲存類型、前置長度、欄位長度或欄位結束字元。</span><span class="sxs-lookup"><span data-stu-id="4193b-111">When you specify an existing format file in a **bcp** command, the command uses the values that are recorded in the format file and does not prompt you for the file storage type, prefix length, field length, or field terminator.</span></span>  
  
-   <span data-ttu-id="4193b-112">您可以為特定資料類型 (如字元資料或原生資料) 建立格式檔案。</span><span class="sxs-lookup"><span data-stu-id="4193b-112">You can create a format file for a particular data type such as character data or native data.</span></span>  
  
     <span data-ttu-id="4193b-113">您可以建立非 XML 格式檔案，其中包含以互動方式，針對每個資料欄位所指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="4193b-113">You can create a non-XML format file that contains interactively specified attributes for each data field.</span></span> <span data-ttu-id="4193b-114">如需詳細資訊，請參閱[使用 bcp 時指定相容性的資料格式 &#40;SQL Server&#41;](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4193b-114">For more information, see [Specify Data Formats for Compatibility when Using bcp &#40;SQL Server&#41;](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4193b-115">XML 格式檔案提供了許多優於非 XML 格式檔案的優點。</span><span class="sxs-lookup"><span data-stu-id="4193b-115">XML format files offer several advantages over non-XML format files.</span></span> <span data-ttu-id="4193b-116">如需詳細資訊，請參閱 [XML 格式檔案 &#40;SQL Server&#41;](xml-format-files-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4193b-116">For more information, see [XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  
##  <a name="structure-of-non-xml-format-files"></a><a name="Structure"></a> <span data-ttu-id="4193b-117">非 XML 格式檔案的結構</span><span class="sxs-lookup"><span data-stu-id="4193b-117">Structure of Non-XML Format Files</span></span>  
 <span data-ttu-id="4193b-118">非 XML 格式檔案是具有特定結構的文字檔。</span><span class="sxs-lookup"><span data-stu-id="4193b-118">A non-XML format file is a text file that has a specific structure.</span></span> <span data-ttu-id="4193b-119">非 XML 格式檔案包含每個資料表資料行的檔案儲存類型、前置長度、欄位長度和欄位結束字元等相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4193b-119">The non-XML format file contains information about the file storage type, prefix length, field length, and field terminator of every table column.</span></span>  
  
 <span data-ttu-id="4193b-120">下圖說明非 XML 格式範例檔案的格式檔案欄位。</span><span class="sxs-lookup"><span data-stu-id="4193b-120">The following illustration illustrates the format-file fields for a sample non-XML format file.</span></span>  
  
 <span data-ttu-id="4193b-121">![識別非 XML 格式檔案的欄位](../../database-engine/media/mydepart-fmt-ident-c.gif "識別非 XML 格式檔案的欄位")</span><span class="sxs-lookup"><span data-stu-id="4193b-121">![Identifies the fields of a non-XML format file](../../database-engine/media/mydepart-fmt-ident-c.gif "Identifies the fields of a non-XML format file")</span></span>  
  
 <span data-ttu-id="4193b-122">**Version** 和 **Number of columns** 欄位只出現一次。</span><span class="sxs-lookup"><span data-stu-id="4193b-122">The **Version** and **Number of columns** fields occur one time only.</span></span> <span data-ttu-id="4193b-123">下表描述其意義。</span><span class="sxs-lookup"><span data-stu-id="4193b-123">Their meanings are describes in the following table.</span></span>  
  
|<span data-ttu-id="4193b-124">格式檔案欄位</span><span class="sxs-lookup"><span data-stu-id="4193b-124">Format-file field</span></span>|<span data-ttu-id="4193b-125">描述</span><span class="sxs-lookup"><span data-stu-id="4193b-125">Description</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="4193b-126">版本</span><span class="sxs-lookup"><span data-stu-id="4193b-126">Version</span></span>|<span data-ttu-id="4193b-127">只能由 **bcp**辨識版本號碼，而不是由 [!INCLUDE[tsql](../../includes/tsql-md.md)]辨識。</span><span class="sxs-lookup"><span data-stu-id="4193b-127">The version number is recognized only by **bcp**, not by [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="4193b-128">**bcp** 公用程式的版本號碼：</span><span class="sxs-lookup"><span data-stu-id="4193b-128">Version number of the **bcp** utility:</span></span><br /><br /> <span data-ttu-id="4193b-129">9.0 = [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4193b-129">9.0 = [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]</span></span><br /><br /> <span data-ttu-id="4193b-130">10.0 = [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4193b-130">10.0 = [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]</span></span><br /><br /> <span data-ttu-id="4193b-131">11.0 = [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4193b-131">11.0 = [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]</span></span><br /><br /> <span data-ttu-id="4193b-132">12.0 = [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4193b-132">12.0 = [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]</span></span><br /><br /> <span data-ttu-id="4193b-133">注意:用於讀取格式檔案的 **bcp** 公用程式 (Bcp.exe) 版本必須與用於建立格式檔案的版本相同，或比它更新。</span><span class="sxs-lookup"><span data-stu-id="4193b-133">Note: The version of the **bcp** utility (Bcp.exe) used to read a format file must be the same as, or a later version than was used to create the format file.</span></span> <span data-ttu-id="4193b-134">例如， [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]**bcp** 可以讀取由 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]**bcp**產生的 10.0 版格式檔案，但是 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]**bcp** 無法讀取由 [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]**bcp**產生的 12.0 版格式檔案。</span><span class="sxs-lookup"><span data-stu-id="4193b-134">For example, [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]**bcp** can read a version 10.0 format file, which is generated by [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]**bcp**, but [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]**bcp** cannot read a version 12.0 format file, which is generated by [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]**bcp**.</span></span>|  
|<span data-ttu-id="4193b-135">Number of columns</span><span class="sxs-lookup"><span data-stu-id="4193b-135">Number of columns</span></span>|<span data-ttu-id="4193b-136">資料檔案的欄位數。</span><span class="sxs-lookup"><span data-stu-id="4193b-136">Number of fields in the data file.</span></span> <span data-ttu-id="4193b-137">在所有資料列中此數目必須相同。</span><span class="sxs-lookup"><span data-stu-id="4193b-137">This number must be the same in all rows.</span></span>|  
  
 <span data-ttu-id="4193b-138">其他格式檔案欄位描述要大量匯入或匯出的資料欄位。</span><span class="sxs-lookup"><span data-stu-id="4193b-138">The other format-file fields describe the data fields that are to be bulk imported or exported.</span></span> <span data-ttu-id="4193b-139">每個資料欄位在格式檔案中，必須有個別的資料列來代表。</span><span class="sxs-lookup"><span data-stu-id="4193b-139">Each data field requires a separate row in the format file.</span></span> <span data-ttu-id="4193b-140">每個格式檔案資料列都包含下表所述之格式檔案欄位的值。</span><span class="sxs-lookup"><span data-stu-id="4193b-140">Every format-file row contains values for the format-file fields that are described in the following table.</span></span>  
  
|<span data-ttu-id="4193b-141">格式檔案欄位</span><span class="sxs-lookup"><span data-stu-id="4193b-141">Format-file field</span></span>|<span data-ttu-id="4193b-142">描述</span><span class="sxs-lookup"><span data-stu-id="4193b-142">Description</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="4193b-143">**主檔案欄位順序**</span><span class="sxs-lookup"><span data-stu-id="4193b-143">**Host file field order**</span></span>|<span data-ttu-id="4193b-144">指出資料檔中每個欄位之位置的號碼。</span><span class="sxs-lookup"><span data-stu-id="4193b-144">A number that indicates the position of each field in the data file.</span></span> <span data-ttu-id="4193b-145">資料列中的第一個欄位為 1，其餘依此類推。</span><span class="sxs-lookup"><span data-stu-id="4193b-145">The first field in the row is 1, and so on.</span></span>|  
|<span data-ttu-id="4193b-146">**主檔案資料類型**</span><span class="sxs-lookup"><span data-stu-id="4193b-146">**Host file data type**</span></span>|<span data-ttu-id="4193b-147">指出存放在資料檔給定欄位中的資料類型。</span><span class="sxs-lookup"><span data-stu-id="4193b-147">Indicates the data type that is stored in a given field of the data file.</span></span> <span data-ttu-id="4193b-148">對於 ASCII 資料檔，請使用 SQLCHAR；對於原生 (Native) 格式的資料檔，請使用預設的資料類型。</span><span class="sxs-lookup"><span data-stu-id="4193b-148">With ASCII data files, use SQLCHAR; for native format data files, use default data types.</span></span> <span data-ttu-id="4193b-149">如需詳細資訊，請參閱 [使用 bcp 時指定檔案儲存類型 &#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4193b-149">For more information, see [Specify File Storage Type by Using bcp &#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md).</span></span>|  
|<span data-ttu-id="4193b-150">**前置長度**</span><span class="sxs-lookup"><span data-stu-id="4193b-150">**Prefix length**</span></span>|<span data-ttu-id="4193b-151">該欄位的長度前置詞字元數。</span><span class="sxs-lookup"><span data-stu-id="4193b-151">Number of length prefix characters for the field.</span></span> <span data-ttu-id="4193b-152">有效的前置長度為 0、1、2、4 和 8。</span><span class="sxs-lookup"><span data-stu-id="4193b-152">Valid prefix lengths are 0, 1, 2, 4, and 8.</span></span> <span data-ttu-id="4193b-153">若要避免指定長度前置詞，請將它設定為 0。</span><span class="sxs-lookup"><span data-stu-id="4193b-153">To avoid specifying the length prefix, set this to 0.</span></span> <span data-ttu-id="4193b-154">如果欄位包含 NULL 資料值，就必須指定長度前置詞。</span><span class="sxs-lookup"><span data-stu-id="4193b-154">A length prefix must be specified if the field contains NULL data values.</span></span> <span data-ttu-id="4193b-155">如需詳細資訊，請參閱 [使用 bcp 時指定資料檔案的前置長度 &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4193b-155">For more information, see [Specify Prefix Length in Data Files by Using bcp &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md).</span></span>|  
|<span data-ttu-id="4193b-156">**主檔案資料長度**</span><span class="sxs-lookup"><span data-stu-id="4193b-156">**Host file data length**</span></span>|<span data-ttu-id="4193b-157">儲存於資料檔特定欄位中的資料類型最大長度，以位元組為單位。</span><span class="sxs-lookup"><span data-stu-id="4193b-157">Maximum length, in bytes, of the data type stored in the particular field of the data file.</span></span><br /><br /> <span data-ttu-id="4193b-158">如果您要為分隔的文字檔建立非 XML 格式檔案，可以將每個資料欄位的主檔案資料長度指定為 0。</span><span class="sxs-lookup"><span data-stu-id="4193b-158">If you are creating a non-XML format file for a delimited text file, you can specify 0 for the host file data length of every data field.</span></span> <span data-ttu-id="4193b-159">當分隔文字檔的前置長度為 0 且已匯入結束字元，則會忽略欄位長度值，因為欄位使用的儲存空間即等於資料加上結束字元的長度。</span><span class="sxs-lookup"><span data-stu-id="4193b-159">When a delimited text file having a prefix length of 0 and a terminator is imported, the field-length value is ignored, because the storage space used by the field equals the length of the data plus the terminator.</span></span><br /><br /> <span data-ttu-id="4193b-160">如需詳細資訊，請參閱 [使用 bcp 指定欄位長度 &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4193b-160">For more information, see [Specify Field Length by Using bcp &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md).</span></span>|  
|<span data-ttu-id="4193b-161">**結束字元**</span><span class="sxs-lookup"><span data-stu-id="4193b-161">**Terminator**</span></span>|<span data-ttu-id="4193b-162">用來分隔資料檔中欄位的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="4193b-162">Delimiter to separate the fields in a data file.</span></span> <span data-ttu-id="4193b-163">一般的結束字元為逗點 (,)、定位點 (\t) 和行尾 (\r\n)。</span><span class="sxs-lookup"><span data-stu-id="4193b-163">Common terminators are comma (,), tab (\t), and end of line (\r\n).</span></span> <span data-ttu-id="4193b-164">如需詳細資訊，請參閱 [指定欄位與資料列結束字元 &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4193b-164">For more information, see [Specify Field and Row Terminators &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md).</span></span>|  
|<span data-ttu-id="4193b-165">**伺服器資料行順序**</span><span class="sxs-lookup"><span data-stu-id="4193b-165">**Server column order**</span></span>|<span data-ttu-id="4193b-166">資料行出現在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料表中的順序。</span><span class="sxs-lookup"><span data-stu-id="4193b-166">Order in which columns appear in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="4193b-167">例如，如果資料檔的第四個欄位對應至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料表的第六個資料行，那麼第四個欄位的伺服器資料行順序為 6。</span><span class="sxs-lookup"><span data-stu-id="4193b-167">For example, if the fourth field in the data file maps to the sixth column in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] table, the server column order for the fourth field is 6.</span></span><br /><br /> <span data-ttu-id="4193b-168">若要防止資料表中的某個資料行接收資料檔中的任何資料，請將伺服器資料行順序值設為 0。</span><span class="sxs-lookup"><span data-stu-id="4193b-168">To prevent a column in the table from receiving any data from the data file, set the server column order value to 0.</span></span>|  
|<span data-ttu-id="4193b-169">**伺服器資料行名稱**</span><span class="sxs-lookup"><span data-stu-id="4193b-169">**Server column name**</span></span>|<span data-ttu-id="4193b-170">從 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料表複製的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="4193b-170">Name of the column copied from the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="4193b-171">欄位的實際名稱不是必要的，但是格式檔案中的欄位不能是空白。</span><span class="sxs-lookup"><span data-stu-id="4193b-171">The actual name of the field is not required, but the field in the format file must not be blank.</span></span>|  
|<span data-ttu-id="4193b-172">**資料行定序**</span><span class="sxs-lookup"><span data-stu-id="4193b-172">**Column collation**</span></span>|<span data-ttu-id="4193b-173">用來儲存資料檔的字元和 Unicode 資料的定序。</span><span class="sxs-lookup"><span data-stu-id="4193b-173">The collation used to store character and Unicode data in the data file.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="4193b-174">您可以修改格式檔案，讓您從欄位數目或順序與資料表資料行數目或順序不同的資料檔，進行大量匯入。</span><span class="sxs-lookup"><span data-stu-id="4193b-174">You can modify a format file to let you bulk import from a data file in which the number or order of the fields are different from the number or order of table columns.</span></span> <span data-ttu-id="4193b-175">如需詳細資訊，請參閱本主題稍後的 [相關工作](#RelatedTasks) 清單。</span><span class="sxs-lookup"><span data-stu-id="4193b-175">For more information, see the [Related Tasks](#RelatedTasks) list, later in this topic.</span></span>  
  
##  <a name="example-of-a-non-xml-format-file"></a><a name="Examples"></a> <span data-ttu-id="4193b-176">非 XML 格式檔案範例</span><span class="sxs-lookup"><span data-stu-id="4193b-176">Example of a Non-XML Format File</span></span>  
 <span data-ttu-id="4193b-177">下列範例顯示先前建立的非 XML 格式檔案 (`myDepartmentIdentical-f-c.fmt`)。</span><span class="sxs-lookup"><span data-stu-id="4193b-177">The following example shows a previously created non-XML format file (`myDepartmentIdentical-f-c.fmt`).</span></span> <span data-ttu-id="4193b-178">這個檔案針對 `HumanResources.Department` 範例資料庫的 `AdventureWorks2012` 資料表，描述其中每個資料行的字元資料欄位。</span><span class="sxs-lookup"><span data-stu-id="4193b-178">This file describes a character-data field for every column in the `HumanResources.Department` table in the `AdventureWorks2012` sample database.</span></span>  
  
 <span data-ttu-id="4193b-179">產生的格式檔案 `myDepartmentIdentical-f-c.fmt`包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="4193b-179">The generated format file, `myDepartmentIdentical-f-c.fmt`, contains the following information:</span></span>  
  
```  
12.0  
4  
1       SQLCHAR       0       7       "\t"     1     DepartmentID     ""  
2       SQLCHAR       0       100     "\t"     2     Name             SQL_Latin1_General_CP1_CI_AS  
3       SQLCHAR       0       100     "\t"     3     GroupName        SQL_Latin1_General_CP1_CI_AS  
4       SQLCHAR       0       24      "\r\n"   4     ModifiedDate     ""  
```  
  
> [!NOTE]  
>  <span data-ttu-id="4193b-180">如需與這個非 XML 格式範例檔案有關的格式檔案欄位圖解，請參閱本主題稍早的 [非 XML 格式檔案結構](#Structure)。</span><span class="sxs-lookup"><span data-stu-id="4193b-180">For an illustration that shows the format-file fields in relation to this sample non-XML format file, see [Structure of Non-XML Format Files](#Structure), earlier in this topic.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="4193b-181">相關工作</span><span class="sxs-lookup"><span data-stu-id="4193b-181">Related Tasks</span></span>  
  
-   [<span data-ttu-id="4193b-182">建立格式檔案 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4193b-182">Create a Format File &#40;SQL Server&#41;</span></span>](create-a-format-file-sql-server.md)  
  
-   [<span data-ttu-id="4193b-183">使用格式檔案大量匯入資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4193b-183">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="4193b-184">使用格式檔案略過資料表資料行 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4193b-184">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [<span data-ttu-id="4193b-185">使用格式檔案略過資料欄位 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4193b-185">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [<span data-ttu-id="4193b-186">使用格式檔案將資料表資料行對應至資料檔案欄位 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4193b-186">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="4193b-187">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4193b-187">See Also</span></span>  
 <span data-ttu-id="4193b-188">[bcp 公用程式](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="4193b-188">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="4193b-189">[建立格式檔案 &#40;SQL Server&#41;](create-a-format-file-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4193b-189">[Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md) </span></span>  
 <span data-ttu-id="4193b-190">[XML 格式檔案 &#40;SQL Server&#41;](xml-format-files-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4193b-190">[XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md) </span></span>  
 [<span data-ttu-id="4193b-191">匯入或匯出資料的格式檔案 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4193b-191">Format Files for Importing or Exporting Data &#40;SQL Server&#41;</span></span>](format-files-for-importing-or-exporting-data-sql-server.md)  
  
  
