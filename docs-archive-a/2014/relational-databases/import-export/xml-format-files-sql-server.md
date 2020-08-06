---
title: XML 格式檔案 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- format files [SQL Server], XML format files
- bulk importing [SQL Server], format files
- XML format files [SQL Server]
ms.assetid: 69024aad-eeea-4187-8fea-b49bc2359849
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7cc1e8de30fa582898ef8516b9767dec14c4fa81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598878"
---
# <a name="xml-format-files-sql-server"></a><span data-ttu-id="a2421-102">XML 格式檔案 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a2421-102">XML Format Files (SQL Server)</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="a2421-103">提供 XML 結構描述，以定義撰寫 *「XML 格式檔案」* (XML format file) 用於將資料大量匯入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表的語法。</span><span class="sxs-lookup"><span data-stu-id="a2421-103">provides an XML schema that defines syntax for writing *XML format files* to use for bulk importing data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> <span data-ttu-id="a2421-104">XML 格式檔案必須遵守以 XML 結構描述定義語言 (XSDL) 定義的這個結構描述。</span><span class="sxs-lookup"><span data-stu-id="a2421-104">XML format files must adhere to this schema, which is defined in the XML Schema Definition Language (XSDL).</span></span> <span data-ttu-id="a2421-105">只有在同時安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 工具和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 時，才能支援 XML 格式檔案。</span><span class="sxs-lookup"><span data-stu-id="a2421-105">XML format files are only supported when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tools are installed together with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 <span data-ttu-id="a2421-106">您可以搭配使用 XML 格式檔案與 **bcp**命令、BULK INSERT 陳述式或 INSERT ...SELECT \* FROM OPENROWSET(BULK...) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="a2421-106">You can use an XML format file with a **bcp** command, BULK INSERT statement, or INSERT ... SELECT \* FROM OPENROWSET(BULK...) statement.</span></span> <span data-ttu-id="a2421-107">**bcp** 命令可讓您自動產生資料表的 XML 格式檔案；如需詳細資訊，請參閱＜ [bcp Utility](../../tools/bcp-utility.md)＞。</span><span class="sxs-lookup"><span data-stu-id="a2421-107">The **bcp** command allows you to automatically generate an XML format file for a table; for more information, see [bcp Utility](../../tools/bcp-utility.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a2421-108">有兩種類型的格式檔案支援大量匯出和匯入：「非 XML 格式檔案」和「XML 格式檔案」。</span><span class="sxs-lookup"><span data-stu-id="a2421-108">Two types of format files are supported for bulk exporting and importing: *non-XML format files* and *XML format files*.</span></span> <span data-ttu-id="a2421-109">相較於非 XML 格式檔案而言，XML 格式檔案是較彈性且功能強大的替代方案。</span><span class="sxs-lookup"><span data-stu-id="a2421-109">XML format files provide a flexible and powerful alternative to non-XML format files.</span></span> <span data-ttu-id="a2421-110">如需非 XML 格式檔案的相關資訊，請參閱 [非 XML 格式檔案 &#40;SQL Server&#41;](xml-format-files-sql-server.md)＞。</span><span class="sxs-lookup"><span data-stu-id="a2421-110">For information about non-XML format files, see [Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md).</span></span>  
  

  
##  <a name="benefits-of-xml-format-files"></a><a name="BenefitsOfXmlFFs"></a> <span data-ttu-id="a2421-111">XML 格式檔案的優點</span><span class="sxs-lookup"><span data-stu-id="a2421-111">Benefits of XML Format Files</span></span>  
  
-   <span data-ttu-id="a2421-112">XML 格式檔案具有自我描述能力，使其易於讀取、建立和擴充。</span><span class="sxs-lookup"><span data-stu-id="a2421-112">XML format files are self-describing, making them easy to read, create, and extend.</span></span> <span data-ttu-id="a2421-113">XML 格式檔案容易讀懂，以便輕鬆地了解在大量作業期間如何解譯資料。</span><span class="sxs-lookup"><span data-stu-id="a2421-113">They are human readable, making it easy to understand how data is interpreted during bulk operations.</span></span>  
  
-   <span data-ttu-id="a2421-114">XML 格式檔案包含目標資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="a2421-114">XML format files contain the data types of target columns.</span></span>  <span data-ttu-id="a2421-115">XML 編碼清楚描述資料檔的資料類型和資料元素，以及資料元素和資料表資料行之間的對應關係。</span><span class="sxs-lookup"><span data-stu-id="a2421-115">The XML encoding clearly describes the data types and data elements of the data file and also the mapping between data elements and table columns.</span></span>  
  
     <span data-ttu-id="a2421-116">如此可將資料檔呈現資料的方式，與檔案中每一個欄位和資料類型間的關係，予以區隔開來。</span><span class="sxs-lookup"><span data-stu-id="a2421-116">This enables separation between how data is represented in the data file and what data type is associated with each field in the file.</span></span> <span data-ttu-id="a2421-117">例如，資料檔若包含資料的字元表示法，就會遺失對應的 SQL 資料行類型。</span><span class="sxs-lookup"><span data-stu-id="a2421-117">For example, if a data file contains a character representation of the data, the corresponding SQL column type is lost.</span></span>  
  
-   <span data-ttu-id="a2421-118">XML 格式檔案允許從資料檔載入包含單一大型物件 (LOB) 資料類型的欄位。</span><span class="sxs-lookup"><span data-stu-id="a2421-118">An XML format file allows for loading of a field that contains a single large object (LOB) data type from a data file.</span></span>  
  
-   <span data-ttu-id="a2421-119">XML 格式檔案雖然功能增強，但仍保持與其舊版的相容性。</span><span class="sxs-lookup"><span data-stu-id="a2421-119">An XML format file can be enhanced yet remain compatible with its earlier versions.</span></span> <span data-ttu-id="a2421-120">此外，XML 清楚的編碼方式，有利於建立所指定的資料檔的多個格式檔案。</span><span class="sxs-lookup"><span data-stu-id="a2421-120">Furthermore, the clarity of XML encoding facilitates the creation of multiple format files for a given data file.</span></span> <span data-ttu-id="a2421-121">如果您需要將資料欄位的全部或部分對應到不同資料表或檢視表中的資料行，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="a2421-121">This is useful if you have to map all or some of the data fields to columns in different tables or views.</span></span>  
  
-   <span data-ttu-id="a2421-122">XML 語法與作業方向無關；也就是說，大量匯出和大量匯入作業的語法相同。</span><span class="sxs-lookup"><span data-stu-id="a2421-122">The XML syntax is independent of the direction of the operation; that is, the syntax is the same for bulk export and bulk import.</span></span>  
  
-   <span data-ttu-id="a2421-123">您可以使用 XML 格式檔案，大量匯入資料至資料表或非資料分割檢視中及大量匯出資料。</span><span class="sxs-lookup"><span data-stu-id="a2421-123">You can use XML format files to bulk import data into tables or non-partitioned views and to bulk export data.</span></span>  
  
-   <span data-ttu-id="a2421-124">針對 OPENROWSET(BULK...) 函數，指定目標資料表是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="a2421-124">For the OPENROWSET(BULK...) function specifying a target table is optional.</span></span> <span data-ttu-id="a2421-125">原因是函數依賴 XML 格式檔案，才能從資料檔讀取資料。</span><span class="sxs-lookup"><span data-stu-id="a2421-125">This is because the function relies on the XML format file to read data from a data file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a2421-126">使用 **bcp** 命令和 BULK INSERT 陳述式 (使用目標資料表資料行來執行類型轉換)，需要目標資料表。</span><span class="sxs-lookup"><span data-stu-id="a2421-126">A target table is necessary with the **bcp** command and the BULK INSERT statement, which uses the target table columns to do the type conversion.</span></span>  
  
##  <a name="structure-of-xml-format-files"></a><a name="StructureOfXmlFFs"></a> <span data-ttu-id="a2421-127">XML 格式檔案的結構</span><span class="sxs-lookup"><span data-stu-id="a2421-127">Structure of XML Format Files</span></span>  
 <span data-ttu-id="a2421-128">就像非 XML 格式檔案一樣，XML 格式檔案也定義資料檔中資料欄位的格式和結構，並將那些資料欄位對應到單一目標資料表中的資料行。</span><span class="sxs-lookup"><span data-stu-id="a2421-128">Like a non-XML format file, an XML format file defines the format and structure of the data fields in a data file and maps those data fields to columns in a single target table.</span></span>  
  
 <span data-ttu-id="a2421-129">XML 格式檔案擁有兩個主要元件，\<RECORD> 與 \<ROW>：</span><span class="sxs-lookup"><span data-stu-id="a2421-129">An XML format file possesses two main components, \<RECORD> and \<ROW>:</span></span>  
  
-   <span data-ttu-id="a2421-130">\<RECORD> 描述儲存在資料檔案中的資料。</span><span class="sxs-lookup"><span data-stu-id="a2421-130">\<RECORD> describes the data as it is stored in the data file.</span></span>  
  
     <span data-ttu-id="a2421-131">每個 \<RECORD> 元素都包含一組單一或多個 \<FIELD> 元素。</span><span class="sxs-lookup"><span data-stu-id="a2421-131">Each \<RECORD> element contains a set of one or more \<FIELD> elements.</span></span> <span data-ttu-id="a2421-132">這些元素對應到資料檔案中的欄位。</span><span class="sxs-lookup"><span data-stu-id="a2421-132">These elements correspond to fields in the data file.</span></span> <span data-ttu-id="a2421-133">基本語法如下：</span><span class="sxs-lookup"><span data-stu-id="a2421-133">The basic syntax is as follows:</span></span>  
  
     \<RECORD>  
  
     <span data-ttu-id="a2421-134">\<FIELD .../> [ ...*n* ]</span><span class="sxs-lookup"><span data-stu-id="a2421-134">\<FIELD .../> [ ...*n* ]</span></span>  
  
     \</RECORD>  
  
     <span data-ttu-id="a2421-135">每個 \<FIELD> 元素都會描述特定資料欄位的內容。</span><span class="sxs-lookup"><span data-stu-id="a2421-135">Each \<FIELD> element describes the contents of a specific data field.</span></span> <span data-ttu-id="a2421-136">一個欄位只能對應到資料表的一個資料行。</span><span class="sxs-lookup"><span data-stu-id="a2421-136">A field can only be mapped to one column in the table.</span></span> <span data-ttu-id="a2421-137">並非所有欄位都需要對應到資料行。</span><span class="sxs-lookup"><span data-stu-id="a2421-137">Not all fields need to be mapped to columns.</span></span>  
  
     <span data-ttu-id="a2421-138">資料檔中的欄位可以是固定/可變長度或以字元終止。</span><span class="sxs-lookup"><span data-stu-id="a2421-138">A field in a data file can be either of fixed/variable length or character terminated.</span></span> <span data-ttu-id="a2421-139">「欄位值」可以如此表示：一個字元 (使用單一位元組表示法)、一個寬字元 (使用 Unicode 雙位元組表示法)、原生資料庫格式或一個檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="a2421-139">A *field value* can be represented as: a character (using single-byte representation), a wide character (using Unicode two-byte representation), native database format, or a file name.</span></span> <span data-ttu-id="a2421-140">如果欄位值是以檔案名稱表示，則檔案名稱指向包含目標資料表中 BLOB 資料行的值的檔案。</span><span class="sxs-lookup"><span data-stu-id="a2421-140">If a field value is represented as a file name, the file name points to the file that contains the value of a BLOB column in the target table.</span></span>  
  
-   <span data-ttu-id="a2421-141">\<ROW> 描述當檔案的資料匯入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表時，如何從資料檔案中建構資料列資料。</span><span class="sxs-lookup"><span data-stu-id="a2421-141">\<ROW> describes how to construct data rows from a data file when the data from the file is imported into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
     <span data-ttu-id="a2421-142">\<ROW> 元素包含一組 \<COLUMN> 元素。</span><span class="sxs-lookup"><span data-stu-id="a2421-142">A \<ROW> element contains a set of \<COLUMN> elements.</span></span> <span data-ttu-id="a2421-143">這些元素對應到資料表資料行。</span><span class="sxs-lookup"><span data-stu-id="a2421-143">These elements correspond to table columns.</span></span> <span data-ttu-id="a2421-144">基本語法如下：</span><span class="sxs-lookup"><span data-stu-id="a2421-144">The basic syntax is as follows:</span></span>  
  
     \<ROW>  
  
     <span data-ttu-id="a2421-145">\<COLUMN .../> [ ...*n* ]</span><span class="sxs-lookup"><span data-stu-id="a2421-145">\<COLUMN .../> [ ...*n* ]</span></span>  
  
     \</ROW>  
  
     <span data-ttu-id="a2421-146">每個 \<COLUMN> 元素都只能對應至資料檔案中的一個欄位。</span><span class="sxs-lookup"><span data-stu-id="a2421-146">Each \<COLUMN> element can be mapped to only one field in the data file.</span></span> <span data-ttu-id="a2421-147">\<ROW> 元素中的 \<COLUMN> 元素順序會定義大量作業傳回這些元素的順序。</span><span class="sxs-lookup"><span data-stu-id="a2421-147">The order of the \<COLUMN> elements in the \<ROW> element defines the order in which they are returned by the bulk operation.</span></span> <span data-ttu-id="a2421-148">XML 格式檔案會將本機名稱指派給每個 \<COLUMN> 元素，而此名稱與大量匯入作業的目標資料表中資料行沒有任何關聯性。</span><span class="sxs-lookup"><span data-stu-id="a2421-148">The XML format file assigns each \<COLUMN> element a local name that has no relationship to the column in the target table of a bulk import operation.</span></span>  
  
##  <a name="schema-syntax-for-xml-format-files"></a><a name="SchemaSyntax"></a> <span data-ttu-id="a2421-149">XML 格式檔案的結構描述語法</span><span class="sxs-lookup"><span data-stu-id="a2421-149">Schema Syntax for XML Format Files</span></span>  
 <span data-ttu-id="a2421-150">本節包含 XML 格式檔案之 XML 結構描述的元素和屬性摘要。</span><span class="sxs-lookup"><span data-stu-id="a2421-150">This section contains a summary of the elements and attributes of the XML schema for XML format files.</span></span> <span data-ttu-id="a2421-151">格式檔案的語法與作業方向無關；也就是說，不管是大量匯出還是大量匯入作業，語法都相同。</span><span class="sxs-lookup"><span data-stu-id="a2421-151">The syntax of a format file is independent of the direction of the operation; that is, the syntax is the same for bulk export and bulk import.</span></span> <span data-ttu-id="a2421-152">本節也將探討大量匯入如何使用 \<ROW> 與 \<COLUMN> 元素，以及如何將元素的 xsi:type 值放入資料集中。</span><span class="sxs-lookup"><span data-stu-id="a2421-152">This section also considers how bulk import uses the \<ROW> and \<COLUMN> elements and how to put the xsi:type value of an element into a data set.</span></span>  
  
 <span data-ttu-id="a2421-153">若要了解語法如何對應到實際 XML 格式檔案，請參閱本主題後面的 [範例 XML 格式檔案](#SampleXmlFFs)。</span><span class="sxs-lookup"><span data-stu-id="a2421-153">To see how the syntax corresponds to actual XML format files, see [Sample XML Format Files](#SampleXmlFFs), later in this topic.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a2421-154">您可以修改格式檔案，讓您從欄位數目及/或順序與資料表資料行數目及/或順序不同的資料檔案，進行大量匯入。</span><span class="sxs-lookup"><span data-stu-id="a2421-154">You can modify a format file to let you bulk import from a data file in which the number and/or order of the fields differ from the number and/or order of table columns.</span></span> <span data-ttu-id="a2421-155">如需詳細資訊，請參閱 [匯入或匯出資料的格式檔案 &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)＞。</span><span class="sxs-lookup"><span data-stu-id="a2421-155">For more information, see [Format Files for Importing or Exporting Data &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).</span></span>  
  
  
  
###  <a name="basic-syntax-of-the-xml-schema"></a><a name="BasicSyntax"></a> <span data-ttu-id="a2421-156">XML 結構描述的基本語法</span><span class="sxs-lookup"><span data-stu-id="a2421-156">Basic Syntax of the XML Schema</span></span>  
 <span data-ttu-id="a2421-157">此語法陳述式只會顯示元素 (\<BCPFORMAT>、\<RECORD>、\<FIELD>、\<ROW> 與 \<COLUMN>) 及其基本屬性。</span><span class="sxs-lookup"><span data-stu-id="a2421-157">This syntax statements show only the elements (\<BCPFORMAT>, \<RECORD>, \<FIELD>, \<ROW>, and \<COLUMN>) and their basic attributes.</span></span>  
  
 \<BCPFORMAT ...>  
  
 \<RECORD>  
  
 <span data-ttu-id="a2421-158">\<欄位識別碼 = "*fieldID*" xsi:type = "*fieldType*" [...]</span><span class="sxs-lookup"><span data-stu-id="a2421-158">\<FIELD ID = "*fieldID*" xsi:type = "*fieldType*" [...]</span></span>  
  
 />  
  
 \</RECORD>  
  
 \<ROW>  
  
 <span data-ttu-id="a2421-159">\<資料行來源 = "*fieldID*" NAME = "*columnName*" xsi:type = "*columnType*" [...]</span><span class="sxs-lookup"><span data-stu-id="a2421-159">\<COLUMN SOURCE = "*fieldID*" NAME = "*columnName*" xsi:type = "*columnType*" [...]</span></span>  
  
 />  
  
 \</ROW>  
  
 \</BCPFORMAT>  
  
> [!NOTE]  
>  <span data-ttu-id="a2421-160">本主題稍後會描述與 \<FIELD> 或 \<COLUMN> 元素中的 xsi:type 值建立關聯的其他屬性。</span><span class="sxs-lookup"><span data-stu-id="a2421-160">Additional attributes that are associated with the value of the xsi:type in a \<FIELD> or \<COLUMN> element are described later in this topic.</span></span>  
  

  
####  <a name="schema-elements"></a><a name="SchemaElements"></a> <span data-ttu-id="a2421-161">Schema 元素</span><span class="sxs-lookup"><span data-stu-id="a2421-161">Schema Elements</span></span>  
 <span data-ttu-id="a2421-162">本節摘要說明 XML 結構描述為 XML 格式檔案定義之每個元素的目的。</span><span class="sxs-lookup"><span data-stu-id="a2421-162">This section summarizes the purpose of each element that the XML schema defines for XML format files.</span></span> <span data-ttu-id="a2421-163">稍後會在此主題另一節說明屬性。</span><span class="sxs-lookup"><span data-stu-id="a2421-163">The attributes are described in separate sections later in this topic.</span></span>  
  
 \<BCPFORMAT>  
 <span data-ttu-id="a2421-164">格式檔案元素，它定義所指定資料檔的記錄結構，以及它和資料表中資料表資料列的資料行之對應關係。</span><span class="sxs-lookup"><span data-stu-id="a2421-164">Is the format-file element that defines the record structure of a given data file and its correspondence to the columns of a table row in the table.</span></span>  
  
 \<RECORD .../>  
 <span data-ttu-id="a2421-165">定義包含一或多個 \<FIELD> 元素的複雜元素。</span><span class="sxs-lookup"><span data-stu-id="a2421-165">Defines a complex element containing one or more \<FIELD> elements.</span></span> <span data-ttu-id="a2421-166">格式檔案中欄位的宣告順序是欄位出現在資料檔中的順序。</span><span class="sxs-lookup"><span data-stu-id="a2421-166">The order in which the fields are declared in the format file is the order in which those fields appear in the data file.</span></span>  
  
 \<FIELD .../>  
 <span data-ttu-id="a2421-167">定義資料檔中包含資料的欄位。</span><span class="sxs-lookup"><span data-stu-id="a2421-167">Defines a field in data file, which contains data.</span></span>  
  
 <span data-ttu-id="a2421-168">這個元素的屬性將在本主題稍後的 [\<FIELD> 元素的屬性](#AttrOfFieldElement)中加以討論。</span><span class="sxs-lookup"><span data-stu-id="a2421-168">The attributes of this element are discussed in [Attributes of the \<FIELD> Element](#AttrOfFieldElement), later in this topic.</span></span>  
  
 \<ROW .../>  
 <span data-ttu-id="a2421-169">定義包含一或多個 \<COLUMN> 元素的複雜元素。</span><span class="sxs-lookup"><span data-stu-id="a2421-169">Defines a complex element containing one or more \<COLUMN> elements.</span></span> <span data-ttu-id="a2421-170">\<COLUMN> 元素的順序與 RECORD 定義中 \<FIELD> 元素的順序無關。</span><span class="sxs-lookup"><span data-stu-id="a2421-170">The order of the \<COLUMN> elements is independent of the order of \<FIELD> elements in a RECORD definition.</span></span> <span data-ttu-id="a2421-171">相反的，格式檔案中的 \<COLUMN> 元素順序會判斷結果資料列集中的資料行順序。</span><span class="sxs-lookup"><span data-stu-id="a2421-171">Rather, the order of the \<COLUMN> elements in a format file determines the column order of the resultant rowset.</span></span> <span data-ttu-id="a2421-172">資料欄位會以相對應 \<COLUMN> 元素在 \<COLUMN> 元素中宣告的順序載入。</span><span class="sxs-lookup"><span data-stu-id="a2421-172">Data fields are loaded in the order in which the corresponding \<COLUMN> elements are declared in the \<COLUMN> element.</span></span>  
  
 <span data-ttu-id="a2421-173">如需詳細資訊，請參閱本主題稍後的[大量匯入如何使用 \<ROW> 元素](#HowUsesROW)。</span><span class="sxs-lookup"><span data-stu-id="a2421-173">For more information, see [How Bulk Import Uses the \<ROW> Element](#HowUsesROW), later in this topic.</span></span>  
  
 \<COLUMN>  
 <span data-ttu-id="a2421-174">定義資料行作為元素 (\<COLUMN>)。</span><span class="sxs-lookup"><span data-stu-id="a2421-174">Defines a column as an element (\<COLUMN>).</span></span> <span data-ttu-id="a2421-175">每個 \<COLUMN> 元素都會對應到 \<FIELD> 元素 (其識別碼是在 \<COLUMN> 元素的 SOURCE 屬性中指定)。</span><span class="sxs-lookup"><span data-stu-id="a2421-175">Each \<COLUMN> element corresponds to a \<FIELD> element (whose ID is specified in the SOURCE attribute of the \<COLUMN> element).</span></span>  
  
 <span data-ttu-id="a2421-176">這個元素屬性將在本主題稍後的 [\<COLUMN> 元素屬性](#AttrOfColumnElement)中加以討論。</span><span class="sxs-lookup"><span data-stu-id="a2421-176">The attributes of this element are discussed in [Attributes of the \<COLUMN> Element](#AttrOfColumnElement), later in this topic.</span></span> <span data-ttu-id="a2421-177">另請參閱本主題稍後的[大量匯入如何使用 \<COLUMN> 元素](#HowUsesColumn)。</span><span class="sxs-lookup"><span data-stu-id="a2421-177">Also see, [How Bulk Import Uses the \<COLUMN> Element](#HowUsesColumn), later in this topic.</span></span>  
  
 \</BCPFORMAT>  
 <span data-ttu-id="a2421-178">結束格式檔案時需要用到。</span><span class="sxs-lookup"><span data-stu-id="a2421-178">Required to end the format file.</span></span>  
  
####  <a name="attributes-of-the-field-element"></a><span data-ttu-id="a2421-179"><a name="AttrOfFieldElement">\<FIELD> 元素的 </a> 屬性</span><span class="sxs-lookup"><span data-stu-id="a2421-179"><a name="AttrOfFieldElement"></a> Attributes of the \<FIELD> Element</span></span>  
 <span data-ttu-id="a2421-180">本節描述 \<FIELD> 元素的屬性，這些屬性會在下列的結構描述語法中摘要說明：</span><span class="sxs-lookup"><span data-stu-id="a2421-180">This section describes the attributes of the \<FIELD> element, which are summarized in the following schema syntax:</span></span>  
  
 <span data-ttu-id="a2421-181"><FIELD</span><span class="sxs-lookup"><span data-stu-id="a2421-181"><FIELD</span></span>  
  
 <span data-ttu-id="a2421-182">識別碼 **= " *`fieldID`* "**</span><span class="sxs-lookup"><span data-stu-id="a2421-182">ID **="*`fieldID`*"**</span></span>  
  
 <span data-ttu-id="a2421-183">xsi **：** type **= " *`fieldType`* "**</span><span class="sxs-lookup"><span data-stu-id="a2421-183">xsi **:** type **="*`fieldType`*"**</span></span>  
  
 <span data-ttu-id="a2421-184">[ LENGTH **="*`n`*"** ]</span><span class="sxs-lookup"><span data-stu-id="a2421-184">[ LENGTH **="*`n`*"** ]</span></span>  
  
 <span data-ttu-id="a2421-185">[PREFIX_LENGTH **= " *`p`* "** ]</span><span class="sxs-lookup"><span data-stu-id="a2421-185">[ PREFIX_LENGTH **="*`p`*"** ]</span></span>  
  
 <span data-ttu-id="a2421-186">[MAX_LENGTH **= " *`m`* "** ]</span><span class="sxs-lookup"><span data-stu-id="a2421-186">[ MAX_LENGTH **="*`m`*"** ]</span></span>  
  
 <span data-ttu-id="a2421-187">[定序 **= " *`collationName`* "** ]</span><span class="sxs-lookup"><span data-stu-id="a2421-187">[ COLLATION **="*`collationName`*"** ]</span></span>  
  
 <span data-ttu-id="a2421-188">[結束字元 **= " *`terminator`* "** ]</span><span class="sxs-lookup"><span data-stu-id="a2421-188">[ TERMINATOR **="*`terminator`*"** ]</span></span>  
  
 />  
  
 <span data-ttu-id="a2421-189">每個 \<FIELD> 元素都與其他元素無關。</span><span class="sxs-lookup"><span data-stu-id="a2421-189">Each \<FIELD> element is independent of the others.</span></span> <span data-ttu-id="a2421-190">以下透過屬性來說明欄位：</span><span class="sxs-lookup"><span data-stu-id="a2421-190">A field is described in terms of the following attributes:</span></span>  
  
|<span data-ttu-id="a2421-191">FIELD 屬性</span><span class="sxs-lookup"><span data-stu-id="a2421-191">FIELD Attribute</span></span>|<span data-ttu-id="a2421-192">描述</span><span class="sxs-lookup"><span data-stu-id="a2421-192">Description</span></span>|<span data-ttu-id="a2421-193">選擇性 /</span><span class="sxs-lookup"><span data-stu-id="a2421-193">Optional /</span></span><br /><br /> <span data-ttu-id="a2421-194">必要</span><span class="sxs-lookup"><span data-stu-id="a2421-194">Required</span></span>|  
|---------------------|-----------------|------------------------------|  
|<span data-ttu-id="a2421-195">識別碼 **= " *`fieldID`* "**</span><span class="sxs-lookup"><span data-stu-id="a2421-195">ID **="*`fieldID`*"**</span></span>|<span data-ttu-id="a2421-196">指定資料檔中欄位的邏輯名稱。</span><span class="sxs-lookup"><span data-stu-id="a2421-196">Specifies the logical name of the field in the data file.</span></span> <span data-ttu-id="a2421-197">欄位識別碼是用來參考該欄位的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="a2421-197">The ID of a field is the key used to refer to the field.</span></span><br /><br /> <span data-ttu-id="a2421-198"><欄位識別碼 **= " *`fieldID`* "**/> 對應到 <資料行來源 **= " *`fieldID`* "**/></span><span class="sxs-lookup"><span data-stu-id="a2421-198"><FIELD ID **="*`fieldID`*"**/> maps to <COLUMN SOURCE **="*`fieldID`*"**/></span></span>|<span data-ttu-id="a2421-199">必要</span><span class="sxs-lookup"><span data-stu-id="a2421-199">Required</span></span>|  
|<span data-ttu-id="a2421-200">xsi： type **= " *`fieldType`* "**</span><span class="sxs-lookup"><span data-stu-id="a2421-200">xsi:type **="*`fieldType`*"**</span></span>|<span data-ttu-id="a2421-201">這是識別元素執行個體之類型的 XML 建構 (如同屬性般使用)。</span><span class="sxs-lookup"><span data-stu-id="a2421-201">This is an XML construct (used like an attribute) that identifies the type of the instance of the element.</span></span> <span data-ttu-id="a2421-202">*fieldType* 的值會決定在指定執行個體中需要哪些選用屬性 (如下)。</span><span class="sxs-lookup"><span data-stu-id="a2421-202">The value of *fieldType* determines which of the optional attributes (below) you need in a given instance.</span></span>|<span data-ttu-id="a2421-203">必要 (視資料類型而定)</span><span class="sxs-lookup"><span data-stu-id="a2421-203">Required (depending on the data type)</span></span>|  
|<span data-ttu-id="a2421-204">長度 **= " *`n`* "**</span><span class="sxs-lookup"><span data-stu-id="a2421-204">LENGTH **="*`n`*"**</span></span>|<span data-ttu-id="a2421-205">此屬性定義固定長度資料類型的執行個體之長度。</span><span class="sxs-lookup"><span data-stu-id="a2421-205">This attribute defines the length for an instance of a fixed-length data type.</span></span><br /><br /> <span data-ttu-id="a2421-206">*n* 的值必須為正整數。</span><span class="sxs-lookup"><span data-stu-id="a2421-206">The value of *n* must be a positive integer.</span></span>|<span data-ttu-id="a2421-207">除非 xsi:type 值有要求，否則是選擇性的</span><span class="sxs-lookup"><span data-stu-id="a2421-207">Optional unless required by the xsi:type value</span></span>|  
|<span data-ttu-id="a2421-208">PREFIX_LENGTH **= " *`p`* "**</span><span class="sxs-lookup"><span data-stu-id="a2421-208">PREFIX_LENGTH **="*`p`*"**</span></span>|<span data-ttu-id="a2421-209">此屬性定義二進位資料代表的前置長度。</span><span class="sxs-lookup"><span data-stu-id="a2421-209">This attribute defines the prefix length for a binary data representation.</span></span> <span data-ttu-id="a2421-210">PREFIX_LENGTH 值 *p* 必須是下列其中一個：1、2、4 或 8。</span><span class="sxs-lookup"><span data-stu-id="a2421-210">The PREFIX_LENGTH value, *p*, must be one of the following: 1, 2, 4, or 8.</span></span>|<span data-ttu-id="a2421-211">除非 xsi:type 值有要求，否則是選擇性的</span><span class="sxs-lookup"><span data-stu-id="a2421-211">Optional unless required by the xsi:type value</span></span>|  
|<span data-ttu-id="a2421-212">MAX_LENGTH **= " *`m`* "**</span><span class="sxs-lookup"><span data-stu-id="a2421-212">MAX_LENGTH **="*`m`*"**</span></span>|<span data-ttu-id="a2421-213">此屬性是可儲存在給定欄位中的最大位元組數。</span><span class="sxs-lookup"><span data-stu-id="a2421-213">This attribute is the maximum number of bytes that can be stored in a given field.</span></span> <span data-ttu-id="a2421-214">若沒有目標資料表，則無法取得資料行最大長度。</span><span class="sxs-lookup"><span data-stu-id="a2421-214">Without a target table, the column max-length is not known.</span></span> <span data-ttu-id="a2421-215">MAX_LENGTH 屬性會限制輸出字元資料行的最大長度，因而限制為資料行值配置的儲存區。</span><span class="sxs-lookup"><span data-stu-id="a2421-215">The MAX_LENGTH attribute restricts the maximum length of an output character column, limiting the storage allocated for the column value.</span></span> <span data-ttu-id="a2421-216">在 ELECT FROM 子句中使用 OPENROWSET 函數的 BULK 選項時，這樣做特別方便。</span><span class="sxs-lookup"><span data-stu-id="a2421-216">This is especially convenient when using the OPENROWSET function's BULK option in a SELECT FROM clause.</span></span><br /><br /> <span data-ttu-id="a2421-217">*m* 的值必須為正整數。</span><span class="sxs-lookup"><span data-stu-id="a2421-217">The value of *m* must be a positive integer.</span></span> <span data-ttu-id="a2421-218">根據預設， **char** 資料行的最大長度是 8000 個字元，而 **nchar** 資料行的最大長度是 4000 個字元。</span><span class="sxs-lookup"><span data-stu-id="a2421-218">By default, the maximum length is 8000 characters for a **char** column and 4000 characters for an **nchar** column.</span></span>|<span data-ttu-id="a2421-219">選用</span><span class="sxs-lookup"><span data-stu-id="a2421-219">Optional</span></span>|  
|<span data-ttu-id="a2421-220">定序 **= " *`collationName`* "**</span><span class="sxs-lookup"><span data-stu-id="a2421-220">COLLATION **="*`collationName`*"**</span></span>|<span data-ttu-id="a2421-221">COLLATION 只能用於字元欄位。</span><span class="sxs-lookup"><span data-stu-id="a2421-221">COLLATION is only allowed for character fields.</span></span> <span data-ttu-id="a2421-222">如需 SQL 定序名稱的清單，請參閱 [SQL Server 定序名稱 &#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a2421-222">For a list of the SQL collation names, see [SQL Server Collation Name &#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql).</span></span>|<span data-ttu-id="a2421-223">選用</span><span class="sxs-lookup"><span data-stu-id="a2421-223">Optional</span></span>|  
|<span data-ttu-id="a2421-224">結束字元 **= " *`terminator`* "**</span><span class="sxs-lookup"><span data-stu-id="a2421-224">TERMINATOR **= "*`terminator`*"**</span></span>|<span data-ttu-id="a2421-225">此屬性會指定資料欄位的結束字元。</span><span class="sxs-lookup"><span data-stu-id="a2421-225">This attribute specifies the terminator of a data field.</span></span> <span data-ttu-id="a2421-226">結束字元可以是任何字元。</span><span class="sxs-lookup"><span data-stu-id="a2421-226">The terminator can be any character.</span></span> <span data-ttu-id="a2421-227">結束字元必須是不包含於資料之任何部分的唯一字元。</span><span class="sxs-lookup"><span data-stu-id="a2421-227">The terminator must be a unique character that is not part of the data.</span></span><br /><br /> <span data-ttu-id="a2421-228">根據預設，欄位結束字元是定位字元 (以 \t 表示)。</span><span class="sxs-lookup"><span data-stu-id="a2421-228">By default, the field terminator is the tab character (represented as \t).</span></span> <span data-ttu-id="a2421-229">若要表示段落標記，請使用 \r\n。</span><span class="sxs-lookup"><span data-stu-id="a2421-229">To represent a paragraph mark, use \r\n.</span></span>|<span data-ttu-id="a2421-230">只能搭配字元資料的 xsi:type 使用，字元資料需要此屬性。</span><span class="sxs-lookup"><span data-stu-id="a2421-230">Used only with an xsi:type of character data, which requires this attribute</span></span>|  
  
#####  <a name="xsitype-values-of-the-field-element"></a><span data-ttu-id="a2421-231"><a name="XsiTypeValuesOfFIELD">\<FIELD> 元素的 </a> xsi:type 值</span><span class="sxs-lookup"><span data-stu-id="a2421-231"><a name="XsiTypeValuesOfFIELD"></a> Xsi:type values of the \<FIELD> Element</span></span>  
 <span data-ttu-id="a2421-232">xsi:type 值是識別元素執行個體之資料類型的 XML 建構 (如同屬性般使用)。</span><span class="sxs-lookup"><span data-stu-id="a2421-232">The xsi:type value is an XML construct (used like an attribute) that identifies the data type of an instance of an element.</span></span> <span data-ttu-id="a2421-233">如需有關使用「將 xsi:type 值放入資料集」的資訊，請參閱本節稍後的部分。</span><span class="sxs-lookup"><span data-stu-id="a2421-233">For information on using the "Putting the xsi:type Value into a Data Set," later in this section.</span></span>  
  
 <span data-ttu-id="a2421-234">\<FIELD> 元素的 xsi:type 值支援下列資料類型。</span><span class="sxs-lookup"><span data-stu-id="a2421-234">The xsi:type value of the \<FIELD> element supports the following data types.</span></span>  
  
|<span data-ttu-id="a2421-235">\<FIELD>xsi:type 值</span><span class="sxs-lookup"><span data-stu-id="a2421-235">\<FIELD> xsi:type values</span></span>|<span data-ttu-id="a2421-236">必要的 XML 屬性</span><span class="sxs-lookup"><span data-stu-id="a2421-236">Required XML Attribute(s)</span></span><br /><br /> <span data-ttu-id="a2421-237">適用於資料類型</span><span class="sxs-lookup"><span data-stu-id="a2421-237">for Data Type</span></span>|<span data-ttu-id="a2421-238">選擇性 XML 屬性</span><span class="sxs-lookup"><span data-stu-id="a2421-238">Optional XML Attribute(s)</span></span><br /><br /> <span data-ttu-id="a2421-239">適用於資料類型</span><span class="sxs-lookup"><span data-stu-id="a2421-239">for Data Type</span></span>|  
|-------------------------------|---------------------------------------------------|---------------------------------------------------|  
|<span data-ttu-id="a2421-240">**NativeFixed**</span><span class="sxs-lookup"><span data-stu-id="a2421-240">**NativeFixed**</span></span>|`LENGTH`|<span data-ttu-id="a2421-241">無。</span><span class="sxs-lookup"><span data-stu-id="a2421-241">None.</span></span>|  
|<span data-ttu-id="a2421-242">**NativePrefix**</span><span class="sxs-lookup"><span data-stu-id="a2421-242">**NativePrefix**</span></span>|`PREFIX_LENGTH`|<span data-ttu-id="a2421-243">MAX_LENGTH</span><span class="sxs-lookup"><span data-stu-id="a2421-243">MAX_LENGTH</span></span>|  
|<span data-ttu-id="a2421-244">**CharFixed**</span><span class="sxs-lookup"><span data-stu-id="a2421-244">**CharFixed**</span></span>|`LENGTH`|<span data-ttu-id="a2421-245">COLLATION</span><span class="sxs-lookup"><span data-stu-id="a2421-245">COLLATION</span></span>|  
|<span data-ttu-id="a2421-246">**NCharFixed**</span><span class="sxs-lookup"><span data-stu-id="a2421-246">**NCharFixed**</span></span>|`LENGTH`|<span data-ttu-id="a2421-247">COLLATION</span><span class="sxs-lookup"><span data-stu-id="a2421-247">COLLATION</span></span>|  
|<span data-ttu-id="a2421-248">**CharPrefix**</span><span class="sxs-lookup"><span data-stu-id="a2421-248">**CharPrefix**</span></span>|`PREFIX_LENGTH`|<span data-ttu-id="a2421-249">MAX_LENGTH、COLLATION</span><span class="sxs-lookup"><span data-stu-id="a2421-249">MAX_LENGTH, COLLATION</span></span>|  
|<span data-ttu-id="a2421-250">**NCharPrefix**</span><span class="sxs-lookup"><span data-stu-id="a2421-250">**NCharPrefix**</span></span>|`PREFIX_LENGTH`|<span data-ttu-id="a2421-251">MAX_LENGTH、COLLATION</span><span class="sxs-lookup"><span data-stu-id="a2421-251">MAX_LENGTH, COLLATION</span></span>|  
|<span data-ttu-id="a2421-252">**CharTerm**</span><span class="sxs-lookup"><span data-stu-id="a2421-252">**CharTerm**</span></span>|`TERMINATOR`|<span data-ttu-id="a2421-253">MAX_LENGTH、COLLATION</span><span class="sxs-lookup"><span data-stu-id="a2421-253">MAX_LENGTH, COLLATION</span></span>|  
|<span data-ttu-id="a2421-254">**NCharTerm**</span><span class="sxs-lookup"><span data-stu-id="a2421-254">**NCharTerm**</span></span>|`TERMINATOR`|<span data-ttu-id="a2421-255">MAX_LENGTH、COLLATION</span><span class="sxs-lookup"><span data-stu-id="a2421-255">MAX_LENGTH, COLLATION</span></span>|  
  
 <span data-ttu-id="a2421-256">如需 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型的詳細資訊，請參閱[資料類型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="a2421-256">For more information about [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
####  <a name="attributes-of-the-column-element"></a><span data-ttu-id="a2421-257"><a name="AttrOfColumnElement">\<COLUMN> 元素的 </a> 屬性</span><span class="sxs-lookup"><span data-stu-id="a2421-257"><a name="AttrOfColumnElement"></a> Attributes of the \<COLUMN> Element</span></span>  
 <span data-ttu-id="a2421-258">本節描述 \<COLUMN> 元素的屬性，這些屬性會在下列的結構描述語法中摘要說明：</span><span class="sxs-lookup"><span data-stu-id="a2421-258">This section describes the attributes of the \<COLUMN> element, which are summarized in the following schema syntax:</span></span>  
  
 <span data-ttu-id="a2421-259">\<元素的 xsi:type 值</span><span class="sxs-lookup"><span data-stu-id="a2421-259">\<COLUMN</span></span>  
  
 <span data-ttu-id="a2421-260">SOURCE = "*fieldID*"</span><span class="sxs-lookup"><span data-stu-id="a2421-260">SOURCE = "*fieldID*"</span></span>  
  
 <span data-ttu-id="a2421-261">NAME = "*columnName*"</span><span class="sxs-lookup"><span data-stu-id="a2421-261">NAME = "*columnName*"</span></span>  
  
 <span data-ttu-id="a2421-262">xsi:type = "*columnType*"</span><span class="sxs-lookup"><span data-stu-id="a2421-262">xsi:type = "*columnType*"</span></span>  
  
 <span data-ttu-id="a2421-263">[ LENGTH = "*n*" ]</span><span class="sxs-lookup"><span data-stu-id="a2421-263">[ LENGTH = "*n*" ]</span></span>  
  
 <span data-ttu-id="a2421-264">[ PRECISION = "*n*" ]</span><span class="sxs-lookup"><span data-stu-id="a2421-264">[ PRECISION = "*n*" ]</span></span>  
  
 <span data-ttu-id="a2421-265">[ SCALE = "*value*" ]</span><span class="sxs-lookup"><span data-stu-id="a2421-265">[ SCALE = "*value*" ]</span></span>  
  
 <span data-ttu-id="a2421-266">[ NULLABLE = { "YES"</span><span class="sxs-lookup"><span data-stu-id="a2421-266">[ NULLABLE = { "YES"</span></span>  
  
 <span data-ttu-id="a2421-267">"NO" } ]</span><span class="sxs-lookup"><span data-stu-id="a2421-267">"NO" } ]</span></span>  
  
 />  
  
 <span data-ttu-id="a2421-268">欄位會使用下列屬性對應到目標資料表的資料行：</span><span class="sxs-lookup"><span data-stu-id="a2421-268">A field is mapped to a column in the target table using the following attributes:</span></span>  
  
|<span data-ttu-id="a2421-269">COLUMN 屬性</span><span class="sxs-lookup"><span data-stu-id="a2421-269">COLUMN Attribute</span></span>|<span data-ttu-id="a2421-270">描述</span><span class="sxs-lookup"><span data-stu-id="a2421-270">Description</span></span>|<span data-ttu-id="a2421-271">選擇性 /</span><span class="sxs-lookup"><span data-stu-id="a2421-271">Optional /</span></span><br /><br /> <span data-ttu-id="a2421-272">必要</span><span class="sxs-lookup"><span data-stu-id="a2421-272">Required</span></span>|  
|----------------------|-----------------|------------------------------|  
|<span data-ttu-id="a2421-273">SOURCE **= " *`fieldID`* "**</span><span class="sxs-lookup"><span data-stu-id="a2421-273">SOURCE **="*`fieldID`*"**</span></span>|<span data-ttu-id="a2421-274">指定對應到資料行的欄位識別碼。</span><span class="sxs-lookup"><span data-stu-id="a2421-274">Specifies the ID of the field being mapped to the column.</span></span><br /><br /> <span data-ttu-id="a2421-275"><資料行來源 **= " *`fieldID`* "**/> 對應到 <欄位識別碼 **= " *`fieldID`* "**/></span><span class="sxs-lookup"><span data-stu-id="a2421-275"><COLUMN SOURCE **="*`fieldID`*"**/> maps to <FIELD ID **="*`fieldID`*"**/></span></span>|<span data-ttu-id="a2421-276">必要</span><span class="sxs-lookup"><span data-stu-id="a2421-276">Required</span></span>|  
|<span data-ttu-id="a2421-277">NAME = "*columnName*"</span><span class="sxs-lookup"><span data-stu-id="a2421-277">NAME = "*columnName*"</span></span>|<span data-ttu-id="a2421-278">指定資料列集中由格式檔案代表的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="a2421-278">Specifies the name of the column in the row set represented by the format file.</span></span> <span data-ttu-id="a2421-279">此資料行名稱會用來識別結果集中的資料行，而且它不需要對應到用於目標資料表中的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="a2421-279">This column name is used to identify the column in the result set, and it need not correspond to the column name used in the target table.</span></span>|<span data-ttu-id="a2421-280">必要</span><span class="sxs-lookup"><span data-stu-id="a2421-280">Required</span></span>|  
|<span data-ttu-id="a2421-281">xsi **：** type **= " *`ColumnType`* "**</span><span class="sxs-lookup"><span data-stu-id="a2421-281">xsi **:** type **="*`ColumnType`*"**</span></span>|<span data-ttu-id="a2421-282">這是識別元素執行個體之資料類型的 XML 建構 (如同屬性般使用)。</span><span class="sxs-lookup"><span data-stu-id="a2421-282">This is an XML construct (used like an attribute) that identifies the data type of the instance of the element.</span></span> <span data-ttu-id="a2421-283">*ColumnType* 的值會決定在指定執行個體中需要哪些選用屬性 (如下)。</span><span class="sxs-lookup"><span data-stu-id="a2421-283">The value of *ColumnType* determines which of the optional attributes (below) you need in a given instance.</span></span><br /><br /> <span data-ttu-id="a2421-284">注意：下表列出*ColumnType*的可能值及其相關聯的屬性。</span><span class="sxs-lookup"><span data-stu-id="a2421-284">Note: The possible values of *ColumnType* and their associated attributes are listed in the next table.</span></span>|<span data-ttu-id="a2421-285">選擇性</span><span class="sxs-lookup"><span data-stu-id="a2421-285">Optional</span></span>|  
|<span data-ttu-id="a2421-286">長度 **= " *`n`* "**</span><span class="sxs-lookup"><span data-stu-id="a2421-286">LENGTH **="*`n`*"**</span></span>|<span data-ttu-id="a2421-287">定義固定長度資料類型的長度。</span><span class="sxs-lookup"><span data-stu-id="a2421-287">Defines the length for an instance of a fixed-length data type.</span></span> <span data-ttu-id="a2421-288">只有當 xsi:type 是字串資料類型時，才會使用 LENGTH。</span><span class="sxs-lookup"><span data-stu-id="a2421-288">LENGTH is used only when the xsi:type is a string data type.</span></span><br /><br /> <span data-ttu-id="a2421-289">*n* 的值必須為正整數。</span><span class="sxs-lookup"><span data-stu-id="a2421-289">The value of *n* must be a positive integer.</span></span>|<span data-ttu-id="a2421-290">選用 (只在 xsi:type 是字串資料類型時才可使用)</span><span class="sxs-lookup"><span data-stu-id="a2421-290">Optional (available only if the xsi:type is a string data type)</span></span>|  
|<span data-ttu-id="a2421-291">PRECISION **="*`n`*"**</span><span class="sxs-lookup"><span data-stu-id="a2421-291">PRECISION **="*`n`*"**</span></span>|<span data-ttu-id="a2421-292">指定數字中的位數。</span><span class="sxs-lookup"><span data-stu-id="a2421-292">Indicates the number of digits in a number.</span></span> <span data-ttu-id="a2421-293">例如，數字 123.45 的精確度是 5。</span><span class="sxs-lookup"><span data-stu-id="a2421-293">For example, the number 123.45 has a precision of 5.</span></span><br /><br /> <span data-ttu-id="a2421-294">其值必須為正整數。</span><span class="sxs-lookup"><span data-stu-id="a2421-294">The value must be a positive integer.</span></span>|<span data-ttu-id="a2421-295">選擇性 (唯有 xsi:type 是變數數字 (variable-number) 資料類型時才能使用)</span><span class="sxs-lookup"><span data-stu-id="a2421-295">Optional (available only if the xsi:type is a variable-number data type)</span></span>|  
|<span data-ttu-id="a2421-296">SCALE **= " *`int`* "**</span><span class="sxs-lookup"><span data-stu-id="a2421-296">SCALE **="*`int`*"**</span></span>|<span data-ttu-id="a2421-297">指定數字中小數點右方的位數。</span><span class="sxs-lookup"><span data-stu-id="a2421-297">Indicates the number of digits to the right of the decimal point in a number.</span></span> <span data-ttu-id="a2421-298">例如，數字 123.45 的小數位數是 2。</span><span class="sxs-lookup"><span data-stu-id="a2421-298">For example, the number 123.45 has a scale of 2.</span></span><br /><br /> <span data-ttu-id="a2421-299">值必須是整數。</span><span class="sxs-lookup"><span data-stu-id="a2421-299">The value must be an integer.</span></span>|<span data-ttu-id="a2421-300">選擇性 (唯有 xsi:type 是變數數字 (variable-number) 資料類型時才能使用)</span><span class="sxs-lookup"><span data-stu-id="a2421-300">Optional (available only if the xsi:type is a variable-number data type)</span></span>|  
|<span data-ttu-id="a2421-301">NULLABLE **=** { **"** YES **"**</span><span class="sxs-lookup"><span data-stu-id="a2421-301">NULLABLE **=** { **"** YES **"**</span></span><br /><br /> <span data-ttu-id="a2421-302">**"** NO **"** }</span><span class="sxs-lookup"><span data-stu-id="a2421-302">**"** NO **"** }</span></span>|<span data-ttu-id="a2421-303">指定資料行是否可指定 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="a2421-303">Indicates whether a column can assume NULL values.</span></span> <span data-ttu-id="a2421-304">此屬性完全與 FIELDS 無關。</span><span class="sxs-lookup"><span data-stu-id="a2421-304">This attribute is completely independent of FIELDS.</span></span> <span data-ttu-id="a2421-305">然而，若資料行並非 NULLABLE 且欄位指定 NULL (未指定任何值)，則會導致執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="a2421-305">However, if a column is not NULLABLE and field specifies NULL (by not specifying any value), a run-time error results.</span></span><br /><br /> <span data-ttu-id="a2421-306">只有當您執行一般的 SELECT FROM OPENROWSET(BULK...) 陳述式時，才會使用 NULLABLE 屬性。</span><span class="sxs-lookup"><span data-stu-id="a2421-306">The NULLABLE attribute is used only if you do a plain SELECT FROM OPENROWSET(BULK...) statement.</span></span>|<span data-ttu-id="a2421-307">選用 (可用於任何資料類型)</span><span class="sxs-lookup"><span data-stu-id="a2421-307">Optional (available for any data type)</span></span>|  
  
#####  <a name="xsitype-values-of-the-column-element"></a><span data-ttu-id="a2421-308"><a name="XsiTypeValuesOfCOLUMN">\<COLUMN> 元素的 </a> xsi:type 值</span><span class="sxs-lookup"><span data-stu-id="a2421-308"><a name="XsiTypeValuesOfCOLUMN"></a> Xsi:type values of the \<COLUMN> Element</span></span>  
 <span data-ttu-id="a2421-309">xsi:type 值是識別元素執行個體之資料類型的 XML 建構 (如同屬性般使用)。</span><span class="sxs-lookup"><span data-stu-id="a2421-309">The xsi:type value is an XML construct (used like an attribute) that identifies the data type of an instance of an element.</span></span> <span data-ttu-id="a2421-310">如需有關使用「將 xsi:type 值放入資料集」的資訊，請參閱本節稍後的部分。</span><span class="sxs-lookup"><span data-stu-id="a2421-310">For information on using the "Putting the xsi:type Value into a Data Set," later in this section.</span></span>  
  
 <span data-ttu-id="a2421-311">\<COLUMN> 元素支援原生 SQL 資料類型，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a2421-311">The \<COLUMN> element supports native SQL data types, as follows:</span></span>  
  
|<span data-ttu-id="a2421-312">類型類別目錄</span><span class="sxs-lookup"><span data-stu-id="a2421-312">Type Category</span></span>|<span data-ttu-id="a2421-313">\<COLUMN> 資料類型</span><span class="sxs-lookup"><span data-stu-id="a2421-313">\<COLUMN> Data Types</span></span>|<span data-ttu-id="a2421-314">必要的 XML 屬性</span><span class="sxs-lookup"><span data-stu-id="a2421-314">Required XML Attribute(s)</span></span><br /><br /> <span data-ttu-id="a2421-315">適用於資料類型</span><span class="sxs-lookup"><span data-stu-id="a2421-315">for Data Type</span></span>|<span data-ttu-id="a2421-316">選擇性 XML 屬性</span><span class="sxs-lookup"><span data-stu-id="a2421-316">Optional XML Attribute(s)</span></span><br /><br /> <span data-ttu-id="a2421-317">適用於資料類型</span><span class="sxs-lookup"><span data-stu-id="a2421-317">for Data Type</span></span>|  
|-------------------|---------------------------|---------------------------------------------------|---------------------------------------------------|  
|<span data-ttu-id="a2421-318">已修正</span><span class="sxs-lookup"><span data-stu-id="a2421-318">Fixed</span></span>|<span data-ttu-id="a2421-319">`SQLBIT`、`SQLTINYINT`、`SQLSMALLINT`、`SQLINT`、`SQLBIGINT`、`SQLFLT4`、`SQLFLT8`、`SQLDATETIME`、`SQLDATETIM4`、`SQLDATETIM8`、`SQLMONEY`、`SQLMONEY4`、`SQLVARIANT` 和 `SQLUNIQUEID`</span><span class="sxs-lookup"><span data-stu-id="a2421-319">`SQLBIT`, `SQLTINYINT`, `SQLSMALLINT`, `SQLINT`, `SQLBIGINT`, `SQLFLT4`, `SQLFLT8`, `SQLDATETIME`, `SQLDATETIM4`, `SQLDATETIM8`, `SQLMONEY`, `SQLMONEY4`, `SQLVARIANT`, and `SQLUNIQUEID`</span></span>|<span data-ttu-id="a2421-320">無。</span><span class="sxs-lookup"><span data-stu-id="a2421-320">None.</span></span>|<span data-ttu-id="a2421-321">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="a2421-321">NULLABLE</span></span>|  
|<span data-ttu-id="a2421-322">變數數字</span><span class="sxs-lookup"><span data-stu-id="a2421-322">Variable Number</span></span>|<span data-ttu-id="a2421-323">`SQLDECIMAL` 和 `SQLNUMERIC`</span><span class="sxs-lookup"><span data-stu-id="a2421-323">`SQLDECIMAL` and `SQLNUMERIC`</span></span>|<span data-ttu-id="a2421-324">無。</span><span class="sxs-lookup"><span data-stu-id="a2421-324">None.</span></span>|<span data-ttu-id="a2421-325">NULLABLE、PRECISION、SCALE</span><span class="sxs-lookup"><span data-stu-id="a2421-325">NULLABLE, PRECISION, SCALE</span></span>|  
|<span data-ttu-id="a2421-326">LOB</span><span class="sxs-lookup"><span data-stu-id="a2421-326">LOB</span></span>|<span data-ttu-id="a2421-327">`SQLIMAGE`、`CharLOB`、`SQLTEXT` 和 `SQLUDT`</span><span class="sxs-lookup"><span data-stu-id="a2421-327">`SQLIMAGE`, `CharLOB`, `SQLTEXT`, and `SQLUDT`</span></span>|<span data-ttu-id="a2421-328">無。</span><span class="sxs-lookup"><span data-stu-id="a2421-328">None.</span></span>|<span data-ttu-id="a2421-329">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="a2421-329">NULLABLE</span></span>|  
|<span data-ttu-id="a2421-330">字元 LOB</span><span class="sxs-lookup"><span data-stu-id="a2421-330">Character LOB</span></span>|`SQLNTEXT`|<span data-ttu-id="a2421-331">無。</span><span class="sxs-lookup"><span data-stu-id="a2421-331">None.</span></span>|<span data-ttu-id="a2421-332">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="a2421-332">NULLABLE</span></span>|  
|<span data-ttu-id="a2421-333">二進位字串</span><span class="sxs-lookup"><span data-stu-id="a2421-333">Binary string</span></span>|<span data-ttu-id="a2421-334">`SQLBINARY` 和 `SQLVARYBIN`</span><span class="sxs-lookup"><span data-stu-id="a2421-334">`SQLBINARY` and `SQLVARYBIN`</span></span>|<span data-ttu-id="a2421-335">無。</span><span class="sxs-lookup"><span data-stu-id="a2421-335">None.</span></span>|<span data-ttu-id="a2421-336">NULLABLE、LENGTH</span><span class="sxs-lookup"><span data-stu-id="a2421-336">NULLABLE, LENGTH</span></span>|  
|<span data-ttu-id="a2421-337">字元字串</span><span class="sxs-lookup"><span data-stu-id="a2421-337">Character string</span></span>|<span data-ttu-id="a2421-338">`SQLCHAR`、`SQLVARYCHAR`、`SQLNCHAR` 和 `SQLNVARCHAR`</span><span class="sxs-lookup"><span data-stu-id="a2421-338">`SQLCHAR`, `SQLVARYCHAR`, `SQLNCHAR`, and `SQLNVARCHAR`</span></span>|<span data-ttu-id="a2421-339">無。</span><span class="sxs-lookup"><span data-stu-id="a2421-339">None.</span></span>|<span data-ttu-id="a2421-340">NULLABLE、LENGTH</span><span class="sxs-lookup"><span data-stu-id="a2421-340">NULLABLE, LENGTH</span></span>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a2421-341">若要大量匯出或匯入 SQLXML 資料，請在格式檔案中使用下列其中一種資料類型：SQLCHAR 或 SQLVARYCHAR (資料會以用戶端字碼頁或定序所隱含的字碼頁傳送)、SQLNCHAR 或 SQLNVARCHAR (資料會以 Unicode 傳送)，或是 SQLBINARY 或 SQLVARYBIN (資料不經轉換即傳送)。</span><span class="sxs-lookup"><span data-stu-id="a2421-341">To bulk export or import SQLXML data, use one of the following data types in your format file: SQLCHAR or SQLVARYCHAR (the data is sent in the client code page or in the code page implied by the collation), SQLNCHAR or SQLNVARCHAR (the data is sent as Unicode), or SQLBINARY or SQLVARYBIN (the data is sent without any conversion).</span></span>  
  
 <span data-ttu-id="a2421-342">如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型的詳細資訊，請參閱 [資料類型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)＞。</span><span class="sxs-lookup"><span data-stu-id="a2421-342">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
###  <a name="how-bulk-import-uses-the-row-element"></a><a name="HowUsesROW"></a><span data-ttu-id="a2421-343">大量匯入如何使用 \<ROW> 元素</span><span class="sxs-lookup"><span data-stu-id="a2421-343">How Bulk Import Uses the \<ROW> Element</span></span>  
 <span data-ttu-id="a2421-344">某些內容會略過 \<ROW> 元素。</span><span class="sxs-lookup"><span data-stu-id="a2421-344">The \<ROW> element is ignored in some contexts.</span></span> <span data-ttu-id="a2421-345">\<ROW> 元素是否會影響大量匯入的作業，視作業執行方式而定：</span><span class="sxs-lookup"><span data-stu-id="a2421-345">Whether the \<ROW> element affects a bulk-import operation depends on how the operation is performed:</span></span>  
  
-   <span data-ttu-id="a2421-346">**bcp** 命令</span><span class="sxs-lookup"><span data-stu-id="a2421-346">the **bcp** command</span></span>  
  
     <span data-ttu-id="a2421-347">將資料載入目標資料表時，**bcp** 會略過 \<ROW> 元件。</span><span class="sxs-lookup"><span data-stu-id="a2421-347">When data is loaded into a target table, **bcp** ignores the \<ROW> component.</span></span> <span data-ttu-id="a2421-348">相反地， **bcp** 會根據目標資料表的資料行類型來載入資料。</span><span class="sxs-lookup"><span data-stu-id="a2421-348">Instead, **bcp** loads the data based on the column types of the target table.</span></span>  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)] <span data-ttu-id="a2421-349">陳述式 (BULK INSERT 和 OPENROWSET 的 Bulk 資料列集提供者)</span><span class="sxs-lookup"><span data-stu-id="a2421-349">statements (BULK INSERT and OPENROWSET's Bulk rowset provider)</span></span>  
  
     <span data-ttu-id="a2421-350">大量匯入資料到資料表時，[!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式會使用 \<ROW> 元件來產生輸入資料列集。</span><span class="sxs-lookup"><span data-stu-id="a2421-350">When bulk importing data into a table, [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements use the \<ROW> component to generate the input rowset.</span></span> <span data-ttu-id="a2421-351">此外，[!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式會根據在目標資料表中 \<ROW> 與對應資料行中指定的資料行類型來執行適當的類型轉換。</span><span class="sxs-lookup"><span data-stu-id="a2421-351">Also, [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements perform appropriate type conversions based on the column types specified under \<ROW> and the corresponding column in the target table.</span></span> <span data-ttu-id="a2421-352">若格式檔案中指定的資料行類型與目標資料表不同，會發生額外的類型轉換。</span><span class="sxs-lookup"><span data-stu-id="a2421-352">If a mismatch exists between column types as specified in the format file and in the target table, an extra type conversion occurs.</span></span> <span data-ttu-id="a2421-353">此額外類型轉換可能會導致 BULK INSERT 或 OPENROWSET 的 Bulk 資料列集提供者發生某些不一致 (亦即，遺失精確度) 的行為 (與 **bcp**相較)。</span><span class="sxs-lookup"><span data-stu-id="a2421-353">This extra type conversion may lead to some discrepancy (that is, a loss of precision) in behavior in BULK INSERT or OPENROWSET's Bulk rowset provider as compared to **bcp**.</span></span>  
  
     <span data-ttu-id="a2421-354">無需任何額外資訊，\<ROW> 元素中的資訊就可供建構資料列。</span><span class="sxs-lookup"><span data-stu-id="a2421-354">The information in the \<ROW> element allows a row to be constructed without requiring any additional information.</span></span> <span data-ttu-id="a2421-355">因此，您可以使用 SELECT 陳述式 (SELECT \* FROM OPENROWSET(BULK *datafile* FORMATFILE=*xmlformatfile*) 來產生資料列集。</span><span class="sxs-lookup"><span data-stu-id="a2421-355">For this reason, you can generate a rowset using a SELECT statement (SELECT \* FROM OPENROWSET(BULK *datafile* FORMATFILE=*xmlformatfile*).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a2421-356">OPENROWSET BULK 子句需要格式檔案 (請注意，要有 XML 格式檔案才能將欄位的資料類型轉換為資料行的資料類型)。</span><span class="sxs-lookup"><span data-stu-id="a2421-356">The OPENROWSET BULK clause requires a format file (note that converting from the data type of the field to the data type of a column is available only with an XML format file).</span></span>  
  
###  <a name="how-bulk-import-uses-the-column-element"></a><a name="HowUsesColumn"></a> <span data-ttu-id="a2421-357">大量匯入如何使用 \<COLUMN> 元素</span><span class="sxs-lookup"><span data-stu-id="a2421-357">How Bulk Import Uses the \<COLUMN> Element</span></span>  
 <span data-ttu-id="a2421-358">若要大量匯入資料至資料表中，格式檔案中的 \<COLUMN> 元素會透過指定下列各項，將資料檔案的欄位對應到資料表資料行：</span><span class="sxs-lookup"><span data-stu-id="a2421-358">For bulk importing data into a table, the \<COLUMN> elements in a format file map a data-file field to table columns by specifying:</span></span>  
  
-   <span data-ttu-id="a2421-359">資料檔的資料列中每一個欄位的位置。</span><span class="sxs-lookup"><span data-stu-id="a2421-359">The position of each field within a row in the data file.</span></span>  
  
-   <span data-ttu-id="a2421-360">資料行類型，用來將欄位資料類型轉換成所要的資料行資料類型。</span><span class="sxs-lookup"><span data-stu-id="a2421-360">The column type, which is used to convert the field data type to the desired column data type.</span></span>  
  
 <span data-ttu-id="a2421-361">若沒有任何資料行對應到欄位，則該欄位不會被複製到產生的資料列。</span><span class="sxs-lookup"><span data-stu-id="a2421-361">If no column is mapped to a field, the field is not copied into the generated row(s).</span></span> <span data-ttu-id="a2421-362">此行為可讓資料檔產生具有不同資料行的資料列 (在不同的資料表中)。</span><span class="sxs-lookup"><span data-stu-id="a2421-362">This behavior allows a data file to generate rows with different columns (in different tables).</span></span>  
  
 <span data-ttu-id="a2421-363">同樣地，從資料表大量匯出資料時，格式檔案中每個 \<COLUMN> 會將輸入資料表資料列中的資料行，對應到輸出資料檔案中的對應欄位。</span><span class="sxs-lookup"><span data-stu-id="a2421-363">Similarly, for bulk exporting data from a table, each \<COLUMN> in the format file maps the column from the input table row to its corresponding field in the output data file.</span></span>  
  
###  <a name="putting-the-xsitype-value-into-a-data-set"></a><a name="PutXsiTypeValueIntoDataSet"></a> <span data-ttu-id="a2421-364">將 xsi:type 值放到資料集中</span><span class="sxs-lookup"><span data-stu-id="a2421-364">Putting the xsi:type Value into a Data Set</span></span>  
 <span data-ttu-id="a2421-365">當您使用 XML Schema Definition (XSD) 語言來驗證 XML 文件時，xsi:type 值不會放到資料集中。</span><span class="sxs-lookup"><span data-stu-id="a2421-365">When an XML document is validated through the XML Schema Definition (XSD) language, the xsi:type value is not put into the data set.</span></span> <span data-ttu-id="a2421-366">然而，您可以透過將 XML 格式檔案載入到 XML 文件 (例如： `myDoc`)，來將 xsi:type 資訊放到資料集中，如以下程式碼片段所示：</span><span class="sxs-lookup"><span data-stu-id="a2421-366">However, you can put the xsi:type information into the data set by loading the XML format file into an XML document (for example, `myDoc`), as illustrated in the following code snippet:</span></span>  
  
```  
...;  
myDoc.LoadXml(xmlFormat);  
XmlNodeList ColumnList = myDoc.GetElementsByTagName("COLUMN");  
for(int i=0;i<ColumnList.Count;i++)  
{  
   Console.Write("COLUMN: xsi:type=" +ColumnList[i].Attributes["type",  
      "http://www.w3.org/2001/XMLSchema-instance"].Value+"\n");  
}  
```  
  
##  <a name="sample-xml-format-files"></a><a name="SampleXmlFFs"></a> <span data-ttu-id="a2421-367">範例 XML 格式檔案</span><span class="sxs-lookup"><span data-stu-id="a2421-367">Sample XML Format Files</span></span>  
 <span data-ttu-id="a2421-368">本節包含有關在各種情況下使用 XML 格式檔案的詳細資訊，包括 [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="a2421-368">This section contains information on using XML format files in a variety of cases, including an [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] example.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a2421-369">在下列範例顯示的資料檔中， `<tab>` 表示資料檔中的定位字元， `<return>` 則表示歸位字元。</span><span class="sxs-lookup"><span data-stu-id="a2421-369">In the data files shown in the following examples, `<tab>` indicates a tab character in a data file, and `<return>` indicates a carriage return.</span></span>  
  

  
> [!NOTE]  
>  <span data-ttu-id="a2421-370">如需如何建立格式檔案的相關資訊，請參閱 [建立格式檔案 &#40;SQL Server&#41;](create-a-format-file-sql-server.md)＞。</span><span class="sxs-lookup"><span data-stu-id="a2421-370">For information about how to create format files, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md).</span></span>  
  
###  <a name="a-ordering-character-data-fields-the-same-as-table-columns"></a><a name="OrderCharFieldsSameAsCols"></a> <span data-ttu-id="a2421-371">A.</span><span class="sxs-lookup"><span data-stu-id="a2421-371">A.</span></span> <span data-ttu-id="a2421-372">以與資料表資料行相同的方式排序字元資料欄位</span><span class="sxs-lookup"><span data-stu-id="a2421-372">Ordering character-data fields the same as table columns</span></span>  
 <span data-ttu-id="a2421-373">下列範例顯示 XML 格式檔案，其中描述包含三個字元資料欄位的資料檔。</span><span class="sxs-lookup"><span data-stu-id="a2421-373">The following example shows an XML format file that describes a data file containing three fields of character data.</span></span> <span data-ttu-id="a2421-374">格式檔案將資料檔對應到包含三個資料行的資料表。</span><span class="sxs-lookup"><span data-stu-id="a2421-374">The format file maps the data file to a table that contains three columns.</span></span> <span data-ttu-id="a2421-375">資料欄位是以一對一的方式，來對應資料表的資料行。</span><span class="sxs-lookup"><span data-stu-id="a2421-375">The data fields correspond one-to-one with the columns of the table.</span></span>  
  
 <span data-ttu-id="a2421-376">**資料表 (資料列)：** Person (Age int, FirstName varchar(20), LastName varchar(30))</span><span class="sxs-lookup"><span data-stu-id="a2421-376">**Table (row):** Person (Age int, FirstName varchar(20), LastName varchar(30))</span></span>  
  
 <span data-ttu-id="a2421-377">**資料檔 (記錄)：** Age\<tab>Firstname\<tab>Lastname\<return></span><span class="sxs-lookup"><span data-stu-id="a2421-377">**Data file (record):** Age\<tab>Firstname\<tab>Lastname\<return></span></span>  
  
 <span data-ttu-id="a2421-378">下列 XML 格式檔案會將資料檔中的資料讀入資料表。</span><span class="sxs-lookup"><span data-stu-id="a2421-378">The following XML format file reads from the data file to the table.</span></span>  
  
 <span data-ttu-id="a2421-379">在 `<RECORD>` 元素中，格式檔案是以字元資料來表示這三個欄位內的資料值。</span><span class="sxs-lookup"><span data-stu-id="a2421-379">In the `<RECORD>` element, the format file represents the data values in all three fields as character data.</span></span> <span data-ttu-id="a2421-380">每一個欄位的 `TERMINATOR` 屬性，都會指出跟在資料值後面的結束字元。</span><span class="sxs-lookup"><span data-stu-id="a2421-380">For each field, the `TERMINATOR` attribute indicates the terminator that follows the data value.</span></span>  
  
 <span data-ttu-id="a2421-381">資料欄位是以一對一的方式，來對應資料表的資料行。</span><span class="sxs-lookup"><span data-stu-id="a2421-381">The data fields correspond one-to-one with the columns of the table.</span></span> <span data-ttu-id="a2421-382">在 `<ROW>` 元素中，格式檔案會將資料行 `Age` 對應到第一個欄位、資料行 `FirstName` 對應到第二個欄位，以及資料行 `LastName` 對應到第三個欄位。</span><span class="sxs-lookup"><span data-stu-id="a2421-382">In the `<ROW>` element, the format file maps the column `Age` to the first field, the column `FirstName` to the second field, and the column `LastName` to the third field.</span></span>  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT   
xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <RECORD>  
    <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="12"/>   
    <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="20" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
    <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="\r\n"   
      MAX_LENGTH="30"   
      COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  </RECORD>  
  <ROW>  
    <COLUMN SOURCE="1" NAME="age" xsi:type="SQLINT"/>  
    <COLUMN SOURCE="2" NAME="firstname" xsi:type="SQLVARYCHAR"/>  
    <COLUMN SOURCE="3" NAME="lastname" xsi:type="SQLVARYCHAR"/>  
  </ROW>  
</BCPFORMAT>  
```  
  
> [!NOTE]  
>  <span data-ttu-id="a2421-383">如需參考相等的 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 範例，請參閱 [建立格式檔案 &#40;SQL Server&#41;](create-a-format-file-sql-server.md)＞。</span><span class="sxs-lookup"><span data-stu-id="a2421-383">For an equivalent [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] example, see [Create a Format File &#40;SQL Server&#41;](create-a-format-file-sql-server.md).</span></span>  
  
###  <a name="b-ordering-data-fields-and-table-columns-differently"></a><a name="OrderFieldsAndColsDifferently"></a> <span data-ttu-id="a2421-384">B.</span><span class="sxs-lookup"><span data-stu-id="a2421-384">B.</span></span> <span data-ttu-id="a2421-385">以不同的方式排序資料欄位與資料表資料行</span><span class="sxs-lookup"><span data-stu-id="a2421-385">Ordering data fields and table columns differently</span></span>  
 <span data-ttu-id="a2421-386">下列範例顯示 XML 格式檔案，其中描述包含三個字元資料欄位的資料檔。</span><span class="sxs-lookup"><span data-stu-id="a2421-386">The following example shows an XML format file that describes a data file containing three fields of character data.</span></span> <span data-ttu-id="a2421-387">格式檔案會將資料檔對應到包含三個資料行 (排序方式與資料檔的欄位不同) 的資料表。</span><span class="sxs-lookup"><span data-stu-id="a2421-387">The format file maps the data file to a table that contains three columns that are ordered differently from the fields of the data file.</span></span>  
  
 <span data-ttu-id="a2421-388">**資料表 (資料列)：** Person (Age int, FirstName varchar(20), LastName varchar(30))</span><span class="sxs-lookup"><span data-stu-id="a2421-388">**Table (row):** Person (Age int, FirstName varchar(20), LastName varchar(30))</span></span>  
  
 <span data-ttu-id="a2421-389">**資料檔 (記錄)：** Age\<tab>Lastname\<tab>Firstname\<return></span><span class="sxs-lookup"><span data-stu-id="a2421-389">**Data file** (record): Age\<tab>Lastname\<tab>Firstname\<return></span></span>  
  
 <span data-ttu-id="a2421-390">在 `<RECORD>` 元素中，格式檔案是以字元資料來表示這三個欄位內的資料值。</span><span class="sxs-lookup"><span data-stu-id="a2421-390">In the `<RECORD>` element, the format file represents the data values in all three fields as character data.</span></span>  
  
 <span data-ttu-id="a2421-391">在 `<ROW>` 元素中，格式檔案會將資料行 `Age` 對應到第一個欄位、資料行 `FirstName` 對應到第三個欄位，以及資料行 `LastName` 對應到第二個欄位。</span><span class="sxs-lookup"><span data-stu-id="a2421-391">In the `<ROW>` element, the format file maps the column `Age` to the first field, the column `FirstName` to the third field, and the column `LastName` to the second field.</span></span>  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT   
xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <RECORD>  
    <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="12"/>  
    <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\t" MAX_LENGTH="20"   
      COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
    <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="\r\n"   
      MAX_LENGTH="30" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  </RECORD>  
  <ROW>  
    <COLUMN SOURCE="1" NAME="age" xsi:type="SQLINT"/>  
    <COLUMN SOURCE="3" NAME="firstname" xsi:type="SQLVARYCHAR"/>  
    <COLUMN SOURCE="2" NAME="lastname" xsi:type="SQLVARYCHAR"/>  
  </ROW>  
</BCPFORMAT>  
```  
  
> [!NOTE]  
>  <span data-ttu-id="a2421-392">如需參考相等的 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 範例，請參閱 [使用格式檔案將資料表資料行對應至資料檔欄位 &#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)＞。</span><span class="sxs-lookup"><span data-stu-id="a2421-392">For an equivalent [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] example, see [Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md).</span></span>  
  
### <a name="c-omitting-a-data-field"></a><span data-ttu-id="a2421-393">C.</span><span class="sxs-lookup"><span data-stu-id="a2421-393">C.</span></span> <span data-ttu-id="a2421-394">省略資料欄位</span><span class="sxs-lookup"><span data-stu-id="a2421-394">Omitting a data field</span></span>  
 <span data-ttu-id="a2421-395">下列範例顯示 XML 格式檔案，其中描述包含四個字元資料欄位的資料檔。</span><span class="sxs-lookup"><span data-stu-id="a2421-395">The following example shows an XML format file that describes a data file containing four fields of character data.</span></span> <span data-ttu-id="a2421-396">格式檔案將資料檔對應到包含三個資料行的資料表。</span><span class="sxs-lookup"><span data-stu-id="a2421-396">The format file maps the data file to a table that contains three columns.</span></span> <span data-ttu-id="a2421-397">第二個資料欄位不對應到任何資料表資料行。</span><span class="sxs-lookup"><span data-stu-id="a2421-397">The second data field does not correspond to any table column.</span></span>  
  
 <span data-ttu-id="a2421-398">**資料表 (資料列)：** Person (Age int, FirstName Varchar(20), LastName Varchar(30))</span><span class="sxs-lookup"><span data-stu-id="a2421-398">**Table (row):** Person (Age int, FirstName Varchar(20), LastName Varchar(30))</span></span>  
  
 <span data-ttu-id="a2421-399">**資料檔 (記錄)：** Age\<tab>employeeID\<tab>Firstname\<tab>Lastname\<return></span><span class="sxs-lookup"><span data-stu-id="a2421-399">**Data file (record):** Age\<tab>employeeID\<tab>Firstname\<tab>Lastname\<return></span></span>  
  
 <span data-ttu-id="a2421-400">在 `<RECORD>` 元素中，格式檔案是以字元資料來表示這四個欄位內的資料值。</span><span class="sxs-lookup"><span data-stu-id="a2421-400">In the `<RECORD>` element, the format file represents the data values in all four fields as character data.</span></span> <span data-ttu-id="a2421-401">每一個欄位的 TERMINATOR 屬性，都會指出跟在資料值後面的結束字元。</span><span class="sxs-lookup"><span data-stu-id="a2421-401">For each field, the TERMINATOR attribute indicates the terminator that follows the data value.</span></span>  
  
 <span data-ttu-id="a2421-402">在 `<ROW>` 元素中，格式檔案會將資料行 `Age` 對應到第一個欄位、資料行 `FirstName` 對應到第三個欄位，以及資料行 `LastName` 對應到第四個欄位。</span><span class="sxs-lookup"><span data-stu-id="a2421-402">In the `<ROW>` element, the format file maps the column `Age` to the first field, the column `FirstName` to the third field, and the column `LastName` to the fourth field.</span></span>  
  
```  
<BCPFORMAT   
xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <RECORD>  
    <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="12"/>  
    <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="10"   
      COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
    <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="\t"   
      MAX_LENGTH="20"   
      COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
    <FIELD ID="4" xsi:type="CharTerm" TERMINATOR="\r\n"   
      MAX_LENGTH="30"   
      COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  </RECORD>  
  <ROW>  
    <COLUMN SOURCE="1" NAME="age" xsi:type="SQLINT"/>  
    <COLUMN SOURCE="3" NAME="firstname" xsi:type="SQLVARYCHAR"/>  
    <COLUMN SOURCE="4" NAME="lastname" xsi:type="SQLVARYCHAR"/>  
  </ROW>  
</BCPFORMAT>  
```  
  
> [!NOTE]  
>  <span data-ttu-id="a2421-403">如需參考相等的 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 範例，請參閱 [使用格式檔案略過資料欄位 &#40;SQL Server&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md)＞。</span><span class="sxs-lookup"><span data-stu-id="a2421-403">For an equivalent [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] example, see [Use a Format File to Skip a Data Field &#40;SQL Server&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md).</span></span>  
  
###  <a name="d-mapping-field-xsitype-to-column-xsitype"></a><a name="MapXSItype"></a> <span data-ttu-id="a2421-404">D.</span><span class="sxs-lookup"><span data-stu-id="a2421-404">D.</span></span> <span data-ttu-id="a2421-405">將 \<FIELD> xsi:type 對應到 \<COLUMN> xsi:type</span><span class="sxs-lookup"><span data-stu-id="a2421-405">Mapping \<FIELD> xsi:type to \<COLUMN> xsi:type</span></span>  
 <span data-ttu-id="a2421-406">下列範例顯示不同類型的欄位，以及它們與資料行的對應關係。</span><span class="sxs-lookup"><span data-stu-id="a2421-406">The following example shows different types of fields and their mappings to columns.</span></span>  
  
```  
<?xml version = "1.0"?>  
<BCPFORMAT  
xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
   <RECORD>  
      <FIELD xsi:type="CharTerm" ID="C1" TERMINATOR="\t"   
            MAX_LENGTH="4"/>  
      <FIELD xsi:type="CharFixed" ID="C2" LENGTH="10"   
         COLLATION="SQL_LATIN1_GENERAL_CP1_CI_AS"/>  
      <FIELD xsi:type="CharPrefix" ID="C3" PREFIX_LENGTH="2"   
         MAX_LENGTH="32" COLLATION="SQL_LATIN1_GENERAL_CP1_CI_AS"/>  
      <FIELD xsi:type="NCharTerm" ID="C4" TERMINATOR="\t"   
         MAX_LENGTH="4"/>  
      <FIELD xsi:type="NCharFixed" ID="C5" LENGTH="10"   
         COLLATION="SQL_LATIN1_GENERAL_CP1_CI_AS"/>  
      <FIELD xsi:type="NCharPrefix" ID="C6" PREFIX_LENGTH="2"   
         MAX_LENGTH="32" COLLATION="SQL_LATIN1_GENERAL_CP1_CI_AS"/>  
      <FIELD xsi:type="NativeFixed" ID="C7" LENGTH="4"/>  
   </RECORD>  
   <ROW>  
      <COLUMN SOURCE="C1" NAME="Age" xsi:type="SQLTINYINT"/>  
      <COLUMN SOURCE="C2" NAME="FirstName" xsi:type="SQLVARYCHAR"   
      LENGTH="16" NULLABLE="NO"/>  
      <COLUMN SOURCE="C3" NAME="LastName" />  
      <COLUMN SOURCE="C4" NAME="Salary" xsi:type="SQLMONEY"/>  
      <COLUMN SOURCE="C5" NAME="Picture" xsi:type="SQLIMAGE"/>  
      <COLUMN SOURCE="C6" NAME="Bio" xsi:type="SQLTEXT"/>  
      <COLUMN SOURCE="C7" NAME="Interest"xsi:type="SQLDECIMAL"   
      PRECISION="5" SCALE="3"/>  
   </ROW>  
</BCPFORMAT>  
```  
  
###  <a name="e-mapping-xml-data-to-a-table"></a><a name="MapXMLDataToTbl"></a> <span data-ttu-id="a2421-407">E.</span><span class="sxs-lookup"><span data-stu-id="a2421-407">E.</span></span> <span data-ttu-id="a2421-408">將 XML 資料對應到資料表</span><span class="sxs-lookup"><span data-stu-id="a2421-408">Mapping XML data to a table</span></span>  
 <span data-ttu-id="a2421-409">下列範例建立包含兩個資料行的空資料表 (`t_xml`)，其中第一個資料行對應到 `int` 資料類型，而第二個資料行則對應到 `xml` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="a2421-409">The following example creates an empty two-column table (`t_xml`), in which the first column maps to the `int` data type and the second column maps to the `xml` data type.</span></span>  
  
```  
CREATE TABLE t_xml (c1 int, c2 xml)  
```  
  
 <span data-ttu-id="a2421-410">下列 XML 格式檔案將會在資料表 `t_xml`中載入資料檔。</span><span class="sxs-lookup"><span data-stu-id="a2421-410">The following XML format file would load a data file into table `t_xml`.</span></span>  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="NativePrefix" PREFIX_LENGTH="1"/>  
  <FIELD ID="2" xsi:type="NCharPrefix" PREFIX_LENGTH="8"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="1" NAME="c1" xsi:type="SQLINT"/>  
  <COLUMN SOURCE="2" NAME="c2" xsi:type="SQLNCHAR"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
###  <a name="f-importing-fixed-length-or-fixed-width-fields"></a><a name="ImportFixedFields"></a> <span data-ttu-id="a2421-411">F.</span><span class="sxs-lookup"><span data-stu-id="a2421-411">F.</span></span> <span data-ttu-id="a2421-412">匯入固定長度或固定寬度的欄位</span><span class="sxs-lookup"><span data-stu-id="a2421-412">Importing fixed-length or fixed-width fields</span></span>  
 <span data-ttu-id="a2421-413">下列範例描述各有 `10` 個或 `6` 個字元的固定欄位。</span><span class="sxs-lookup"><span data-stu-id="a2421-413">The following example describes fixed fields of `10` or `6` characters each.</span></span> <span data-ttu-id="a2421-414">格式檔案分別以 `LENGTH="10"` 和 `LENGTH="6"`來表示這些欄位長度/寬度。</span><span class="sxs-lookup"><span data-stu-id="a2421-414">The format file represents these field lengths/widths as `LENGTH="10"` and `LENGTH="6"`, respectively.</span></span> <span data-ttu-id="a2421-415">資料檔案的每一列都是以歸位字元和換行字元的組合 {CR}{LF} 作為結束，這在格式檔案中是以 `TERMINATOR="\r\n"`來表示。</span><span class="sxs-lookup"><span data-stu-id="a2421-415">Every row of the data files ends with a carriage return-line feed combination, {CR}{LF}, which the format file represents as `TERMINATOR="\r\n"`.</span></span>  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT  
       xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"  
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <RECORD>  
    <FIELD ID="1" xsi:type="CharFixed" LENGTH="10"/>  
    <FIELD ID="2" xsi:type="CharFixed" LENGTH="6"/>  
    <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="\r\n"  
  </RECORD>  
  <ROW>  
    <COLUMN SOURCE="1" NAME="C1" xsi:type="SQLINT" />  
    <COLUMN SOURCE="2" NAME="C2" xsi:type="SQLINT" />  
  </ROW>  
</BCPFORMAT>  
```  
  
###  <a name="additional-examples"></a><a name="AdditionalExamples"></a> <span data-ttu-id="a2421-416">其他範例</span><span class="sxs-lookup"><span data-stu-id="a2421-416">Additional Examples</span></span>  
 <span data-ttu-id="a2421-417">如需非 XML 格式檔案及 XML 格式檔案的其他範例，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="a2421-417">For additional examples of both non-XML format files and XML format files, see the following topics:</span></span>  
  
-   [<span data-ttu-id="a2421-418">使用格式檔案略過資料表資料行 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a2421-418">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [<span data-ttu-id="a2421-419">使用格式檔案略過資料欄位 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a2421-419">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [<span data-ttu-id="a2421-420">使用格式檔案將資料表資料行對應至資料檔案欄位 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a2421-420">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="a2421-421">相關工作</span><span class="sxs-lookup"><span data-stu-id="a2421-421">Related Tasks</span></span>  
  
-   [<span data-ttu-id="a2421-422">建立格式檔案 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a2421-422">Create a Format File &#40;SQL Server&#41;</span></span>](create-a-format-file-sql-server.md)  
  
-   [<span data-ttu-id="a2421-423">使用格式檔案大量匯入資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a2421-423">Use a Format File to Bulk Import Data &#40;SQL Server&#41;</span></span>](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [<span data-ttu-id="a2421-424">使用格式檔案略過資料表資料行 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a2421-424">Use a Format File to Skip a Table Column &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [<span data-ttu-id="a2421-425">使用格式檔案略過資料欄位 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a2421-425">Use a Format File to Skip a Data Field &#40;SQL Server&#41;</span></span>](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [<span data-ttu-id="a2421-426">使用格式檔案將資料表資料行對應至資料檔案欄位 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a2421-426">Use a Format File to Map Table Columns to Data-File Fields &#40;SQL Server&#41;</span></span>](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="a2421-427">相關內容</span><span class="sxs-lookup"><span data-stu-id="a2421-427">Related Content</span></span>  
 <span data-ttu-id="a2421-428">無。</span><span class="sxs-lookup"><span data-stu-id="a2421-428">None.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2421-429">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2421-429">See Also</span></span>  
 <span data-ttu-id="a2421-430">[資料的大量匯入及匯出 &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a2421-430">[Bulk Import and Export of Data &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md) </span></span>  
 <span data-ttu-id="a2421-431">[資料類型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a2421-431">[Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span></span>  
 <span data-ttu-id="a2421-432">[非 XML 格式檔案 &#40;SQL Server&#41;](xml-format-files-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a2421-432">[Non-XML Format Files &#40;SQL Server&#41;](xml-format-files-sql-server.md) </span></span>  
 [<span data-ttu-id="a2421-433">匯入或匯出資料的格式檔案 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a2421-433">Format Files for Importing or Exporting Data &#40;SQL Server&#41;</span></span>](format-files-for-importing-or-exporting-data-sql-server.md)  
  
  
