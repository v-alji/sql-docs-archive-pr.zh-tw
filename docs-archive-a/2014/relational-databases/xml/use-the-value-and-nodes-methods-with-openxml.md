---
title: 在 OPENXML 中使用 value () 和 nodes () 方法 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- OpenXML method [XML in SQL Server]
- value method [XML in SQL Server]
- nodes method [XML in SQL Server]
ms.assetid: c73dbe55-d685-42eb-b0ee-9f3c5b9d97f3
author: rothja
ms.author: jroth
ms.openlocfilehash: 5dccf5a7ef626d1f1a42d011d22ba77807b34eba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706262"
---
# <a name="use-the-value-and-nodes-methods-with-openxml"></a><span data-ttu-id="0c5aa-102">在 OPENXML 中使用 value () 和 nodes () 方法</span><span class="sxs-lookup"><span data-stu-id="0c5aa-102">Use the value() and nodes() Methods with OPENXML</span></span>
  <span data-ttu-id="0c5aa-103">您可以在 SELECT 子句中的資料類型上，使用多個**值 ( # B1**方法 `xml` ，以產生已解壓縮值的資料列集。 **SELECT**</span><span class="sxs-lookup"><span data-stu-id="0c5aa-103">You can use multiple **value()** methods on `xml` data type in a **SELECT** clause to generate a rowset of extracted values.</span></span> <span data-ttu-id="0c5aa-104">**nodes()** 方法會針對可用於額外查詢的每個選定節點，各產生一個內部參考。</span><span class="sxs-lookup"><span data-stu-id="0c5aa-104">The **nodes()** method yields an internal reference for each selected node that can be used for additional query.</span></span> <span data-ttu-id="0c5aa-105">在產生資料列集時，如果所產生的資料列集會有數個資料行，且用來產生資料列集的路徑運算式很複雜時，合併 **nodes()** 和 **value()** 方法會比較有效率。</span><span class="sxs-lookup"><span data-stu-id="0c5aa-105">The combination of the **nodes()** and **value()** methods can be more efficient in generating the rowset when it has several columns and, perhaps, when the path expressions used in its generation are complex.</span></span>  
  
 <span data-ttu-id="0c5aa-106">\*\* ( # B1\*\*方法的節點會產生特殊 `xml` 資料類型的實例，其中每個都將其內容設定為不同的選取節點。</span><span class="sxs-lookup"><span data-stu-id="0c5aa-106">The **nodes()** method yields instances of a special `xml` data type, each of which has its context set to a different selected node.</span></span> <span data-ttu-id="0c5aa-107">這種 XML 執行個體可支援 **query()** 、**value()** 、**nodes()** 和 **exist()** 方法，並可用於 **count(\*)** 彙總。</span><span class="sxs-lookup"><span data-stu-id="0c5aa-107">This kind of XML instance supports **query()**, **value()**, **nodes()**, and **exist()** methods and can be used in **count(\*)** aggregations.</span></span> <span data-ttu-id="0c5aa-108">所有其他用法都會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="0c5aa-108">All other uses cause an error.</span></span>  
  
## <a name="example-using-nodes"></a><span data-ttu-id="0c5aa-109">範例：使用 nodes()</span><span class="sxs-lookup"><span data-stu-id="0c5aa-109">Example: Using nodes()</span></span>  
 <span data-ttu-id="0c5aa-110">假設您要擷取作者的姓名，而名字部份不是 "David"。</span><span class="sxs-lookup"><span data-stu-id="0c5aa-110">Assume that you want to extract the first and last names of authors, and the first name is not "David".</span></span> <span data-ttu-id="0c5aa-111">此外，您還想要將此資訊擷取成包含二個資料行 (FirstName 及 LastName) 的資料列集。</span><span class="sxs-lookup"><span data-stu-id="0c5aa-111">Additionally, you want to extract this information as a rowset that contains two columns, FirstName and LastName.</span></span> <span data-ttu-id="0c5aa-112">您可以使用 **nodes()** 和 **value()** 方法來完成此作業，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0c5aa-112">By using **nodes()** and **value()** methods, you can accomplish this as shown in the following:</span></span>  
  
```  
SELECT nref.value('(first-name/text())[1]', 'nvarchar(50)') FirstName,  
       nref.value('(last-name/text())[1]', 'nvarchar(50)') LastName  
FROM   T CROSS APPLY xCol.nodes('//author') AS R(nref)  
WHERE  nref.exist('first-name[. != "David"]') = 1  
```  
  
 <span data-ttu-id="0c5aa-113">在此範例中， `nodes('//author')` 會產生參考各個 XML 執行個體之 `<author>` 元素的資料列集。</span><span class="sxs-lookup"><span data-stu-id="0c5aa-113">In this example, `nodes('//author')` yields a rowset of references to `<author>` elements for each XML instance.</span></span> <span data-ttu-id="0c5aa-114">藉由評估與那些參考有關的 **value()** 方法，即可取得作者的姓名。</span><span class="sxs-lookup"><span data-stu-id="0c5aa-114">The first and last names of authors are obtained by evaluating **value()** methods relative to those references.</span></span>  
  
 <span data-ttu-id="0c5aa-115">SQL Server 2000 提供一種功能，可使用 **OpenXml()** 從 XML 執行個體產生資料列集。</span><span class="sxs-lookup"><span data-stu-id="0c5aa-115">SQL Server 2000 provides the capability for generating a rowset from an XML instance by using **OpenXml()**.</span></span> <span data-ttu-id="0c5aa-116">您可以指定資料列集的關聯式結構描述，以及 XML 執行個體中的值要如何對應到資料列集中的資料行。</span><span class="sxs-lookup"><span data-stu-id="0c5aa-116">You can specify the relational schema for the rowset and how values inside the XML instance map to columns in the rowset.</span></span>  
  
## <a name="example-using-openxml-on-the-xml-data-type"></a><span data-ttu-id="0c5aa-117">範例：在 xml 資料類型上使用 OpenXml()</span><span class="sxs-lookup"><span data-stu-id="0c5aa-117">Example: Using OpenXml() on the xml Data Type</span></span>  
 <span data-ttu-id="0c5aa-118">您可以依下列方式使用 **OpenXml()** 來改寫上一個範例中的查詢。</span><span class="sxs-lookup"><span data-stu-id="0c5aa-118">The query can be rewritten from the previous example by using **OpenXml()** as shown in the following.</span></span> <span data-ttu-id="0c5aa-119">這個方式是建立資料指標來將每個 XML 執行個體讀入 XML 變數，然後再套用 OpenXML：</span><span class="sxs-lookup"><span data-stu-id="0c5aa-119">This is done by creating a cursor that reads each XML instance into an XML variable and then applies OpenXML to it:</span></span>  
  
```  
DECLARE name_cursor CURSOR  
FOR  
   SELECT xCol   
   FROM   T  
OPEN name_cursor  
DECLARE @xmlVal XML  
DECLARE @idoc int  
FETCH NEXT FROM name_cursor INTO @xmlVal  
  
WHILE (@@FETCH_STATUS = 0)  
BEGIN  
   EXEC sp_xml_preparedocument @idoc OUTPUT, @xmlVal  
   SELECT   *  
   FROM   OPENXML (@idoc, '//author')  
          WITH (FirstName  varchar(50) 'first-name',  
                LastName   varchar(50) 'last-name') R  
   WHERE  R.FirstName != 'David'  
  
   EXEC sp_xml_removedocument @idoc  
   FETCH NEXT FROM name_cursor INTO @xmlVal  
END  
CLOSE name_cursor  
DEALLOCATE name_cursor   
```  
  
 <span data-ttu-id="0c5aa-120">**OpenXml()** 會建立一個 in-memory 表示法，並使用工作資料表來代替查詢處理器。</span><span class="sxs-lookup"><span data-stu-id="0c5aa-120">**OpenXml()** creates an in-memory representation and uses work tables instead of the query processor.</span></span> <span data-ttu-id="0c5aa-121">它是倚賴 MSXML 3.0 版的 XPath 1.0 版處理器，而不是 XQuery 引擎。</span><span class="sxs-lookup"><span data-stu-id="0c5aa-121">It relies on the XPath version 1.0 processor of MSXML version 3.0 instead of the XQuery engine.</span></span> <span data-ttu-id="0c5aa-122">即使是在同一個 XML 執行個體上，工作資料表還是不能讓多個 **OpenXml()** 呼叫共用。</span><span class="sxs-lookup"><span data-stu-id="0c5aa-122">The work tables are not shared among multiple calls to **OpenXml()**, even on the same XML instance.</span></span> <span data-ttu-id="0c5aa-123">這限制了它的可調適性。</span><span class="sxs-lookup"><span data-stu-id="0c5aa-123">This limits its scalability.</span></span> <span data-ttu-id="0c5aa-124">**OpenXml()** 可讓您在沒有指定 WITH 子句的情況下，存取 XML 資料的邊緣資料表格式。</span><span class="sxs-lookup"><span data-stu-id="0c5aa-124">**OpenXml()** allows you to access an edge table format for the XML data when the WITH clause is not specified.</span></span> <span data-ttu-id="0c5aa-125">此外，也可以讓您在另一個「溢位」資料行中使用其餘的 XML 值。</span><span class="sxs-lookup"><span data-stu-id="0c5aa-125">Also, it allows you to use the remaining XML value in a separate, "overflow" column.</span></span>  
  
 <span data-ttu-id="0c5aa-126">**nodes()** 與 **value()** 函數的組合可以有效地利用 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="0c5aa-126">The combination of **nodes()** and **value()** functions uses XML indexes effectively.</span></span> <span data-ttu-id="0c5aa-127">因此，這種組合所展現的可調適性比 **OpenXml**好。</span><span class="sxs-lookup"><span data-stu-id="0c5aa-127">As a result, this combination can exhibit more scalability than **OpenXml**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c5aa-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c5aa-128">See Also</span></span>  
 [<span data-ttu-id="0c5aa-129">OPENXML &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0c5aa-129">OPENXML &#40;SQL Server&#41;</span></span>](openxml-sql-server.md)  
  
  
