---
title: 擷取及查詢 XML 資料 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XML data [SQL Server], retrieving
- XML instance retrieval
ms.assetid: 24a28760-1225-42b3-9c89-c9c0332d9c51
author: rothja
ms.author: jroth
ms.openlocfilehash: d387d1b96a57dcc7100368779f8ec6078fad5c7e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688633"
---
# <a name="retrieve-and-query-xml-data"></a><span data-ttu-id="5aa96-102">擷取及查詢 XML 資料</span><span class="sxs-lookup"><span data-stu-id="5aa96-102">Retrieve and Query XML Data</span></span>
  <span data-ttu-id="5aa96-103">本主題說明查詢 XML 資料必須指定的查詢選項。</span><span class="sxs-lookup"><span data-stu-id="5aa96-103">This topic describes the query options that you have to specify to query XML data.</span></span> <span data-ttu-id="5aa96-104">也會描述當 XML 執行個體儲存於資料庫中時，未保留的 XML 執行個體部分。</span><span class="sxs-lookup"><span data-stu-id="5aa96-104">It also describes the parts of XML instances that are not preserved when they are stored in databases.</span></span>  
  
##  <a name="features-of-an-xml-instance-that-are-not-preserved"></a><a name="features"></a> <span data-ttu-id="5aa96-105">未保留的 XML 執行個體功能</span><span class="sxs-lookup"><span data-stu-id="5aa96-105">Features of an XML Instance That Are Not Preserved</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5aa96-106">會保留 XML 執行個體的內容，但是不會保留在 XML 資料模型中不視為重大之 XML 執行個體的層面。</span><span class="sxs-lookup"><span data-stu-id="5aa96-106">preserves the content of the XML instance, but does not preserve aspects of the XML instance that are not considered to be significant in the XML data model.</span></span> <span data-ttu-id="5aa96-107">這表示擷取的 XML 執行個體可能不等於儲存於伺服器上的執行個體，但是將會包含相同的資訊。</span><span class="sxs-lookup"><span data-stu-id="5aa96-107">This means that a retrieved XML instance might not be identical to the instance that was stored in the server, but will contain the same information.</span></span>  
  
### <a name="xml-declaration"></a><span data-ttu-id="5aa96-108">XML 宣告</span><span class="sxs-lookup"><span data-stu-id="5aa96-108">XML Declaration</span></span>  
 <span data-ttu-id="5aa96-109">若執行個體儲存於資料庫中，就不會保留執行個體中的 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="5aa96-109">The XML declaration in an instance is not preserved when the instance is stored in the database.</span></span> <span data-ttu-id="5aa96-110">例如：</span><span class="sxs-lookup"><span data-stu-id="5aa96-110">For example:</span></span>  
  
```  
CREATE TABLE T1 (Col1 int primary key, Col2 xml)  
GO  
INSERT INTO T1 values (1, '<?xml version="1.0" encoding="windows-1252" ?><doc></doc>')  
GO  
SELECT Col2  
FROM T1  
```  
  
 <span data-ttu-id="5aa96-111">結果為 `<doc/>`。</span><span class="sxs-lookup"><span data-stu-id="5aa96-111">The result is `<doc/>`.</span></span>  
  
 <span data-ttu-id="5aa96-112">將 XML 資料儲存於 `xml` 資料類型執行個體內時，不會保留 XML 宣告 (例如 `<?xml version='1.0'?>`)。</span><span class="sxs-lookup"><span data-stu-id="5aa96-112">The XML declaration, such as `<?xml version='1.0'?>`, is not preserved when storing XML data in an `xml` data type instance.</span></span> <span data-ttu-id="5aa96-113">這是原廠設定。</span><span class="sxs-lookup"><span data-stu-id="5aa96-113">This is by design.</span></span> <span data-ttu-id="5aa96-114">將資料轉換成類型之後，XML 宣告 ( # A1 及其屬性 (版本/編碼/獨立) 會遺失 `xml` 。</span><span class="sxs-lookup"><span data-stu-id="5aa96-114">The XML declaration () and its attributes (version/encoding/stand-alone) are lost after data is converted to type `xml`.</span></span> <span data-ttu-id="5aa96-115">XML 宣告會被視為 XML 剖析器的指示詞。</span><span class="sxs-lookup"><span data-stu-id="5aa96-115">The XML declaration is treated as a directive to the XML parser.</span></span> <span data-ttu-id="5aa96-116">XML 資料會當做 ucs-2 儲存於內部。</span><span class="sxs-lookup"><span data-stu-id="5aa96-116">The XML data is stored internally as ucs-2.</span></span> <span data-ttu-id="5aa96-117">XML 執行個體中的所有其他 PI 都會保留下來。</span><span class="sxs-lookup"><span data-stu-id="5aa96-117">All other PIs in the XML instance are preserved.</span></span>  
  
  
### <a name="order-of-attributes"></a><span data-ttu-id="5aa96-118">屬性順序</span><span class="sxs-lookup"><span data-stu-id="5aa96-118">Order of Attributes</span></span>  
 <span data-ttu-id="5aa96-119">XML 執行個體中屬性的順序不會被保留。</span><span class="sxs-lookup"><span data-stu-id="5aa96-119">The order of attributes in an XML instance is not preserved.</span></span> <span data-ttu-id="5aa96-120">當您查詢 `xml` 類型資料行中儲存的 XML 執行個體時，產生之 XML 中的屬性順序可能會與原始 XML 執行個體不一樣。</span><span class="sxs-lookup"><span data-stu-id="5aa96-120">When you query the XML instance stored in the `xml` type column, the order of attributes in the resulting XML may be different from the original XML instance.</span></span>  
  
  
### <a name="quotation-marks-around-attribute-values"></a><span data-ttu-id="5aa96-121">屬性值兩側的引號</span><span class="sxs-lookup"><span data-stu-id="5aa96-121">Quotation Marks Around Attribute Values</span></span>  
 <span data-ttu-id="5aa96-122">屬性值兩側的單引號與雙引號不會保留。</span><span class="sxs-lookup"><span data-stu-id="5aa96-122">Single quotation marks and double quotations marks around attribute values are not preserved.</span></span> <span data-ttu-id="5aa96-123">屬性值會當做成對的名稱/值儲存在資料庫中。</span><span class="sxs-lookup"><span data-stu-id="5aa96-123">The attribute values are stored in the database as a name and value pair.</span></span> <span data-ttu-id="5aa96-124">引號則不會儲存。</span><span class="sxs-lookup"><span data-stu-id="5aa96-124">The quotation marks are not stored.</span></span> <span data-ttu-id="5aa96-125">當您針對 XML 執行個體執行 XQuery 時，產生的 XML 會序列化並以雙引號括住屬性值。</span><span class="sxs-lookup"><span data-stu-id="5aa96-125">When an XQuery is executed against an XML instance, the resulting XML is serialized with double quotation marks around the attribute values.</span></span>  
  
```  
DECLARE @x xml  
-- Use double quotation marks.  
SET @x = '<root a="1" />'  
SELECT @x  
GO  
DECLARE @x xml  
-- Use single quotation marks.  
SET @x = '<root a=''1'' />'  
SELECT @x  
GO  
```  
  
 <span data-ttu-id="5aa96-126">兩個查詢都會傳回 = `<root a="1" />`。</span><span class="sxs-lookup"><span data-stu-id="5aa96-126">Both queries return = `<root a="1" />`.</span></span>  
  
  
### <a name="namespace-prefixes"></a><span data-ttu-id="5aa96-127">命名空間前置詞</span><span class="sxs-lookup"><span data-stu-id="5aa96-127">Namespace Prefixes</span></span>  
 <span data-ttu-id="5aa96-128">命名空間前置詞不會保留。</span><span class="sxs-lookup"><span data-stu-id="5aa96-128">Namespace prefixes are not preserved.</span></span> <span data-ttu-id="5aa96-129">當您針對 `xml` 類型的資料行指定 XQuery 時，序列化的 XML 結果可能會傳回不同的命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="5aa96-129">When you specify XQuery against an `xml` type column, the serialized XML result may return different namespace prefixes.</span></span>  
  
```  
DECLARE @x xml  
SET @x = '<ns1:root xmlns:ns1="abc" xmlns:ns2="abc">  
            <ns2:SomeElement/>  
          </ns1:root>'  
SELECT @x  
SELECT @x.query('/*')  
GO  
```  
  
 <span data-ttu-id="5aa96-130">結果中的命名空間前置詞可能會不同。</span><span class="sxs-lookup"><span data-stu-id="5aa96-130">The namespace prefix in the result may be different.</span></span> <span data-ttu-id="5aa96-131">例如：</span><span class="sxs-lookup"><span data-stu-id="5aa96-131">For example:</span></span>  
  
```  
<p1:root xmlns:p1="abc"><p1:SomeElement/></p1:root>  
```  
  
  
##  <a name="setting-required-query-options"></a><a name="query"></a> <span data-ttu-id="5aa96-132">設定必要查詢選項</span><span class="sxs-lookup"><span data-stu-id="5aa96-132">Setting Required Query Options</span></span>  
 <span data-ttu-id="5aa96-133">`xml`使用資料類型方法查詢類型資料行或變數時 `xml` ，必須設定下列選項，如下所示。</span><span class="sxs-lookup"><span data-stu-id="5aa96-133">When querying `xml` type columns or variables using `xml` data type methods, the following options must be set as shown.</span></span>  
  
|<span data-ttu-id="5aa96-134">SET 選項</span><span class="sxs-lookup"><span data-stu-id="5aa96-134">SET Options</span></span>|<span data-ttu-id="5aa96-135">必要值</span><span class="sxs-lookup"><span data-stu-id="5aa96-135">Required Values</span></span>|  
|-----------------|---------------------|  
|<span data-ttu-id="5aa96-136">ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="5aa96-136">ANSI_NULLS</span></span>|<span data-ttu-id="5aa96-137">開啟</span><span class="sxs-lookup"><span data-stu-id="5aa96-137">ON</span></span>|  
|<span data-ttu-id="5aa96-138">ANSI_PADDING</span><span class="sxs-lookup"><span data-stu-id="5aa96-138">ANSI_PADDING</span></span>|<span data-ttu-id="5aa96-139">開啟</span><span class="sxs-lookup"><span data-stu-id="5aa96-139">ON</span></span>|  
|<span data-ttu-id="5aa96-140">ANSI_WARNINGS</span><span class="sxs-lookup"><span data-stu-id="5aa96-140">ANSI_WARNINGS</span></span>|<span data-ttu-id="5aa96-141">開啟</span><span class="sxs-lookup"><span data-stu-id="5aa96-141">ON</span></span>|  
|<span data-ttu-id="5aa96-142">ARITHABORT</span><span class="sxs-lookup"><span data-stu-id="5aa96-142">ARITHABORT</span></span>|<span data-ttu-id="5aa96-143">開啟</span><span class="sxs-lookup"><span data-stu-id="5aa96-143">ON</span></span>|  
|<span data-ttu-id="5aa96-144">CONCAT_NULL_YIELDS_NULL</span><span class="sxs-lookup"><span data-stu-id="5aa96-144">CONCAT_NULL_YIELDS_NULL</span></span>|<span data-ttu-id="5aa96-145">開啟</span><span class="sxs-lookup"><span data-stu-id="5aa96-145">ON</span></span>|  
|<span data-ttu-id="5aa96-146">NUMERIC_ROUNDABORT</span><span class="sxs-lookup"><span data-stu-id="5aa96-146">NUMERIC_ROUNDABORT</span></span>|<span data-ttu-id="5aa96-147">OFF</span><span class="sxs-lookup"><span data-stu-id="5aa96-147">OFF</span></span>|  
|<span data-ttu-id="5aa96-148">QUOTED_IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="5aa96-148">QUOTED_IDENTIFIER</span></span>|<span data-ttu-id="5aa96-149">開啟</span><span class="sxs-lookup"><span data-stu-id="5aa96-149">ON</span></span>|  
  
 <span data-ttu-id="5aa96-150">如果未將選項設定為如所示，則查詢和修改 `xml` 資料類型方法將會失敗。</span><span class="sxs-lookup"><span data-stu-id="5aa96-150">If the options are not set as shown, queries and modifications on `xml` data type methods will fail.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="5aa96-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5aa96-151">See Also</span></span>  
 [<span data-ttu-id="5aa96-152">建立 XML 資料的執行個體</span><span class="sxs-lookup"><span data-stu-id="5aa96-152">Create Instances of XML Data</span></span>](create-instances-of-xml-data.md)  
  
  
