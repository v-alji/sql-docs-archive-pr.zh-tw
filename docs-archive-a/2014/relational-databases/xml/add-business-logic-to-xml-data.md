---
title: 將商務邏輯新增至 XML 資料 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- business logic [XML]
ms.assetid: 0877fb38-f1a2-43d8-86cf-4754be224dc1
author: rothja
ms.author: jroth
ms.openlocfilehash: 5bf8e9edc36e9c420faa92f2db1a92c311194e99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593877"
---
# <a name="add-business-logic-to-xml-data"></a><span data-ttu-id="09d72-102">將商務邏輯加入至 XML 資料</span><span class="sxs-lookup"><span data-stu-id="09d72-102">Add Business Logic to XML Data</span></span>
  <span data-ttu-id="09d72-103">將商務邏輯加入至 XML 資料的方法有好幾種：</span><span class="sxs-lookup"><span data-stu-id="09d72-103">Your business logic can be added to XML data in several ways:</span></span>  
  
-   <span data-ttu-id="09d72-104">您可以撰寫資料列或資料行條件約束，以在插入及修改 XML 資料時，強制執行網域專屬的條件約束。</span><span class="sxs-lookup"><span data-stu-id="09d72-104">You can write row or column constraints to enforce domain-specific constraints during insertion and modification of XML data.</span></span>  
  
-   <span data-ttu-id="09d72-105">您可以在 XML 資料行上撰寫觸發程序，當您在資料行中插入或更新值時，即引發該觸發程序。</span><span class="sxs-lookup"><span data-stu-id="09d72-105">You can write a trigger on the XML column that fires when you insert or update values in the column.</span></span> <span data-ttu-id="09d72-106">觸發程序可包含網域專屬的驗證規則，或是擴展屬性資料表。</span><span class="sxs-lookup"><span data-stu-id="09d72-106">The trigger can contain domain-specific validation rules or populate property tables.</span></span>  
  
-   <span data-ttu-id="09d72-107">Database Engine 包含執行 Managed 程式碼的能力。</span><span class="sxs-lookup"><span data-stu-id="09d72-107">The Database Engine includes the ability execute managed code.</span></span> <span data-ttu-id="09d72-108">您可以使用這項 Common Language Runtime (CLR) 整合功能來撰寫要接收 XML 值的 Managed 程式碼函數，並使用 System.Xml 命名空間所提供的 XML 處理功能。</span><span class="sxs-lookup"><span data-stu-id="09d72-108">You can use this common language runtime (CLR) integration to write functions in managed code to which you pass XML values, and use XML processing capabilities provided by the System.Xml namespace.</span></span> <span data-ttu-id="09d72-109">例如，將 XSL 轉換套用至 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="09d72-109">An example is to apply XSL transformation to XML data.</span></span> <span data-ttu-id="09d72-110">或者，您可以將 XML 還原序列化成一個或多個 Managed 類別，並使用 Managed 程式碼來加以操作。</span><span class="sxs-lookup"><span data-stu-id="09d72-110">Alternatively, you can deserialize the XML into one or more managed classes and operate on them by using managed code.</span></span>  
  
-   <span data-ttu-id="09d72-111">您可以撰寫 Transact-SQL 預存程序及函數，以針對您的商業需求開始處理 XML 資料行。</span><span class="sxs-lookup"><span data-stu-id="09d72-111">You can write Transact-SQL stored procedures and functions that start the processing on the XML column for your business needs.</span></span>  
  
## <a name="example-applying-xsl-transformation"></a><span data-ttu-id="09d72-112">範例：套用 XSL 轉換</span><span class="sxs-lookup"><span data-stu-id="09d72-112">Example: Applying XSL Transformation</span></span>  
 <span data-ttu-id="09d72-113">假設有一個 CLR 函數**TransformXml ( # B1** ，它會接受 `xml` 資料類型實例和儲存在檔案中的 XSL 轉換，將轉換套用至 XML 資料，然後在結果中傳回已轉換的 XML。</span><span class="sxs-lookup"><span data-stu-id="09d72-113">Consider a CLR function **TransformXml()** that accepts an `xml` data type instance and an XSL transformation stored in a file, applies the transformation to the XML data, and then returns the transformed XML in the result.</span></span> <span data-ttu-id="09d72-114">以下是用 C# 來撰寫的基本架構函數：</span><span class="sxs-lookup"><span data-stu-id="09d72-114">Following is a skeleton function that is written in C#:</span></span>  
  
```  
public static SqlXml TransformXml (SqlXml XmlData, string xslPath) {  
   // Load XSL transformation  
   XslCompiledTransform xform = new XslCompiledTransform();  
   XPathDocument xslDoc = new XPathDocument (xslPath);  
   xform.Load(xslDoc);  
  
   // Load XML data   
   XPathDocument xDoc = new XPathDocument (XmlData.CreateReader());  
  
   // Return the transformed value  
   MemoryStream xsltResult = new MemoryStream();  
   xform.Transform(xDoc, null, xsltResult);  
   SqlXml retSqlXml = new SqlXml(xsltResult);  
   return (retSqlXml);  
}   
```  
  
 <span data-ttu-id="09d72-115">在註冊完組件，並建立使用者定義的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 函數之後 ( **SqlXslTransform()** 對應到 **TransformXml()** )，即可從 Transact-SQL 來叫用該函數，如下列查詢所示：</span><span class="sxs-lookup"><span data-stu-id="09d72-115">After the assembly is registered and a user-defined [!INCLUDE[tsql](../../includes/tsql-md.md)] function is created, **SqlXslTransform()** corresponding to **TransformXml()**, the function can be invoked from Transact-SQL as shown in the following query:</span></span>  
  
```  
SELECT SqlXslTransform (xCol, 'C:\MyFile\xsltransform.xsl')  
FROM    T  
WHERE  xCol.exist('/book/title/text()[contains(.,"custom")]') =1;  
```  
  
 <span data-ttu-id="09d72-116">查詢結果包含已轉換之 XML 的資料列集。</span><span class="sxs-lookup"><span data-stu-id="09d72-116">The query result contains a rowset of the transformed XML.</span></span>  
  
 <span data-ttu-id="09d72-117">與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 整合的 CLR 擴展了下列作業的可能性：將 XML 資料分解成資料表或屬性升級，以及在 System.Xml 命名空間中使用 Managed 類別來查詢 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="09d72-117">The CLR integration into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] expands the possibilities for decomposing XML data into tables or property promotion, and querying XML data by using managed classes in the System.Xml namespace.</span></span> <span data-ttu-id="09d72-118">如需詳細資訊，請參閱 [XML 資料 &#40;SQL Server&#41;](xml-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="09d72-118">For more information, see [XML Data &#40;SQL Server&#41;](xml-data-sql-server.md).</span></span>  
  
  
