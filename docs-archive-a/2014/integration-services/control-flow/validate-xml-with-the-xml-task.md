---
title: 使用 XML 工作驗證 XML | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- XML validation
- XML, validating
ms.assetid: 224fc025-c21f-4d43-aa9d-5ffac337f9b0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 633a269f53c85353c956b33bff8fd3af518dad56
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584650"
---
# <a name="validate-xml-with-the-xml-task"></a><span data-ttu-id="cf677-102">Validate XML with the XML Task</span><span class="sxs-lookup"><span data-stu-id="cf677-102">Validate XML with the XML Task</span></span>
  <span data-ttu-id="cf677-103">驗證 XML 文件，並啟用 XML 工作的 `ValidationDetails` 屬性以取得詳細的錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="cf677-103">Validate XML documents and get rich error output by enabling the `ValidationDetails` property of the XML Task.</span></span>

 <span data-ttu-id="cf677-104">下列螢幕擷取畫面顯示 [XML 工作編輯器]  ，內含具有豐富錯誤輸出之 XML 驗證所需的設定。</span><span class="sxs-lookup"><span data-stu-id="cf677-104">The following screen shot shows the **XML Task Editor** with the settings required for XML validation with rich error output.</span></span>

 <span data-ttu-id="cf677-105">![[XML 工作編輯器] 中的 XML 工作屬性](../media/xmltaskproperties.jpg "[XML 工作編輯器] 中的 XML 工作屬性")</span><span class="sxs-lookup"><span data-stu-id="cf677-105">![XML task properties in the XML Task Editor](../media/xmltaskproperties.jpg "XML task properties in the XML Task Editor")</span></span>

 <span data-ttu-id="cf677-106">在提供 `ValidationDetails` 屬性前，XML 工作所執行的 XML 驗證只會傳回結果為 True 或 False，而不會有錯誤的相關資訊及其位置。</span><span class="sxs-lookup"><span data-stu-id="cf677-106">Before the `ValidationDetails` property was available, XML validation by the XML Task returned only a true or false result, with no information about errors or their locations.</span></span> <span data-ttu-id="cf677-107">現在，當您將 `ValidationDetails` 設定為 True 時，輸出檔案即涵蓋每項錯誤的詳細資訊，包括行號及位置。</span><span class="sxs-lookup"><span data-stu-id="cf677-107">Now, when you set `ValidationDetails` to true, the output file contains detailed information about every error including the line number and the position.</span></span> <span data-ttu-id="cf677-108">您可以使用此資訊來了解、尋找及修正 XML 文件中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="cf677-108">You can use this information to understand, locate, and fix errors in XML documents.</span></span>

 <span data-ttu-id="cf677-109">XML 驗證功能可針對大型 XML 文件和大量的錯誤輕鬆地進行調整。</span><span class="sxs-lookup"><span data-stu-id="cf677-109">The XML validation functionality scales easily for large XML documents and large numbers of errors.</span></span> <span data-ttu-id="cf677-110">因為輸出檔案本身是 XML 格式，所以您可以查詢和分析輸出。</span><span class="sxs-lookup"><span data-stu-id="cf677-110">Since the output file itself is in XML format, you can query and analyze the output.</span></span> <span data-ttu-id="cf677-111">例如，如果輸出包含大量錯誤，您可以使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 查詢將錯誤分組 (如本主題所述)。</span><span class="sxs-lookup"><span data-stu-id="cf677-111">For example, if the output contains a large number of errors, you can group the errors by using a [!INCLUDE[tsql](../../../includes/tsql-md.md)] query, as described in this topic.</span></span>

> [!NOTE]
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="cf677-112">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) `ValidationDetails` 在 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Service Pack 2 中引進屬性。</span><span class="sxs-lookup"><span data-stu-id="cf677-112">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) introduced the `ValidationDetails` property in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Service Pack 2.</span></span> <span data-ttu-id="cf677-113">和中也提供屬性， [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SQL Server 2016。</span><span class="sxs-lookup"><span data-stu-id="cf677-113">The property is also available in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] and in SQL Server 2016.</span></span>

## <a name="sample-output-for-xml-thats-valid"></a><span data-ttu-id="cf677-114">有效 XML 範例輸出</span><span class="sxs-lookup"><span data-stu-id="cf677-114">Sample output for XML that's valid</span></span>
 <span data-ttu-id="cf677-115">以下範例輸出檔案具有有效 XML 檔案的驗證結果。</span><span class="sxs-lookup"><span data-stu-id="cf677-115">Here is a sample output file with validation results for a valid XML file.</span></span>

```xml

<root xmlns:ns="https://schemas.microsoft.com/xmltools/2002/xmlvalidation">
    <metadata>
        <result>true</result>
        <errors>0</errors>
        <warnings>0</warnings>
        <startTime>2015-05-28T10:27:22.087</startTime>
        <endTime>2015-05-28T10:29:07.007</endTime>
        <xmlFile>d:\Temp\TestData.xml</xmlFile>
        <xsdFile>d:\Temp\TestSchema.xsd</xsdFile>
    </metadata>
    <messages />
</root>
```

## <a name="sample-output-for-xml-thats-not-valid"></a><span data-ttu-id="cf677-116">無效 XML 範例輸出</span><span class="sxs-lookup"><span data-stu-id="cf677-116">Sample output for XML that's not valid</span></span>
 <span data-ttu-id="cf677-117">以下範例輸出檔案具有含有少量錯誤之 XML 檔案的驗證結果。</span><span class="sxs-lookup"><span data-stu-id="cf677-117">Here is a sample output file with validation results for an XML file that contains a small number of errors.</span></span> <span data-ttu-id="cf677-118">\<error> 元素的文字已換行，以增加可讀性。</span><span class="sxs-lookup"><span data-stu-id="cf677-118">The text of the \<error> elements has been wrapped for readability.</span></span>

```xml

<root xmlns:ns="https://schemas.microsoft.com/xmltools/2002/xmlvalidation">
    <metadata>
        <result>false</result>
        <errors>2</errors>
        <warnings>0</warnings>
        <startTime>2015-05-28T10:45:09.538</startTime>
        <endTime>2015-05-28T10:45:09.558</endTime>
        <xmlFile>C:\Temp\TestData.xml</xmlFile>
        <xsdFile>C:\Temp\TestSchema.xsd</xsdFile>
    </metadata>
    <messages>
        <error line="5" position="26">The 'ApplicantRole' element is invalid - The value 'wer3' is invalid
    according to its datatype 'ApplicantRoleType' - The Enumeration constraint failed.</error>
        <error line="16" position="28">The 'Phone' element is invalid - The value 'we3056666666' is invalid
     according to its datatype 'phone' - The Pattern constraint failed.</error>
    </messages>
</root>
```

## <a name="analyze-xml-validation-output-with-a-transact-sql-query"></a><span data-ttu-id="cf677-119">使用 Transact-SQL 查詢分析 XML 驗證輸出</span><span class="sxs-lookup"><span data-stu-id="cf677-119">Analyze XML validation output with a Transact-SQL query</span></span>
 <span data-ttu-id="cf677-120">如果 XML 驗證的輸出包含大量錯誤，您可以使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 查詢，以載入 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的輸出。</span><span class="sxs-lookup"><span data-stu-id="cf677-120">If the output of XML validation contains a large number of errors, you can use a [!INCLUDE[tsql](../../../includes/tsql-md.md)] query to load the output in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="cf677-121">然後，您可以使用 T-SQL 語言的所有功能 (包括 WHERE、GROUP BY、ORDER BY、JOIN 等) 來分析錯誤清單。</span><span class="sxs-lookup"><span data-stu-id="cf677-121">Then you can analyze the error list with all the capabilities of the T-SQL language including WHERE, GROUP BY, ORDER BY, JOIN, and so forth.</span></span>

```sql
DECLARE @xml XML;

SELECT @xml = XmlDoc   
FROM OPENROWSET (BULK N'C:\Temp\XMLValidation_2016-02-212T10-41-00.xml', SINGLE_BLOB) AS Tab(XmlDoc);

-- Query # 1, flat list of errors
-- convert to relational/rectangular
;WITH XMLNAMESPACES ('https://schemas.microsoft.com/xmltools/2002/xmlvalidation' AS ns), rs AS
(
SELECT col.value('@line','INT') AS line
     , col.value('@position','INT') AS position
     , col.value('.','VARCHAR(1024)') AS error
FROM @XML.nodes('/root/messages/error') AS tab(col)
)
SELECT * FROM rs;
-- WHERE error LIKE '%whatever_string%'

-- Query # 2, count of errors grouped by the error message
-- convert to relational/rectangular
;WITH XMLNAMESPACES ('https://schemas.microsoft.com/xmltools/2002/xmlvalidation' AS ns), rs AS
(
SELECT col.value('@line','INT') AS line
     , col.value('@position','INT') AS position
     , col.value('.','VARCHAR(1024)') AS error
FROM @XML.nodes('/root/messages/error') AS tab(col)
)
SELECT COALESCE(error,'Total # of errors:') AS [error], COUNT(*) AS [counter]
FROM rs
GROUP BY GROUPING SETS ((error), ())
ORDER BY 2 DESC, COALESCE(error, 'Z');

```

 <span data-ttu-id="cf677-122">以下是先前文字所示之第二個範例查詢的 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中的結果。</span><span class="sxs-lookup"><span data-stu-id="cf677-122">Here is the result in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] of the second sample query shown in the preceding text.</span></span>

 <span data-ttu-id="cf677-123">![在 Management Studio 中使用查詢將 XML 錯誤分組](../media/queryforxmlerrors.jpg "在 Management Studio 中使用查詢將 XML 錯誤分組")</span><span class="sxs-lookup"><span data-stu-id="cf677-123">![Query to group XML errors in Management Studio](../media/queryforxmlerrors.jpg "Query to group XML errors in Management Studio")</span></span>

## <a name="see-also"></a><span data-ttu-id="cf677-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf677-124">See Also</span></span>
 <span data-ttu-id="cf677-125">[Xml](xml-task.md)工作[xml 工作編輯器 &#40;一般頁面&#41;](../xml-task-editor-general-page.md)</span><span class="sxs-lookup"><span data-stu-id="cf677-125">[XML Task](xml-task.md) [XML Task Editor &#40;General Page&#41;](../xml-task-editor-general-page.md)</span></span>


