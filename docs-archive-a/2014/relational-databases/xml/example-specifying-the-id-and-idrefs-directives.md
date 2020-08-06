---
title: 範例：指定識別碼和 IDREFS 指示詞 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- IDREFS directive
- ID directive
ms.assetid: 99b9f0d8-ecbb-4225-859f-881066c09785
author: rothja
ms.author: jroth
ms.openlocfilehash: c21ba1bd19691014f179801421322970a3dd6dd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599393"
---
# <a name="example-specifying-the-id-and-idrefs-directives"></a><span data-ttu-id="57821-102">範例：指定 ID 和 IDREFS 指示詞</span><span class="sxs-lookup"><span data-stu-id="57821-102">Example: Specifying the ID and IDREFS Directives</span></span>
  <span data-ttu-id="57821-103">元素屬性可以指定為 `ID` 類型屬性，然後可以使用 `IDREFS` 屬性來參考它。</span><span class="sxs-lookup"><span data-stu-id="57821-103">An element attribute can be specified as an `ID` type attribute, and the `IDREFS` attribute can then be used to refer to it.</span></span> <span data-ttu-id="57821-104">這會啟用內部文件連結，而且與關聯式資料庫中的主索引鍵及外部索引鍵關聯性類似。</span><span class="sxs-lookup"><span data-stu-id="57821-104">This enables intra-document links and is similar to the primary key and foreign key relationships in relational databases.</span></span>  
  
 <span data-ttu-id="57821-105">此範例說明如何使用 `ID` 及 `IDREFS` 指示詞，建立 `ID` 及 `IDREFS` 類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="57821-105">This example illustrates how the `ID` and `IDREFS` directives can be used to create attributes of `ID` and `IDREFS` types.</span></span> <span data-ttu-id="57821-106">因為 ID 不能是整數值，所以此範例中的 ID 值會經過轉換。</span><span class="sxs-lookup"><span data-stu-id="57821-106">Because IDs cannot be integer values, the ID values in this example are converted.</span></span> <span data-ttu-id="57821-107">換句話說，會經過類型轉換。</span><span class="sxs-lookup"><span data-stu-id="57821-107">In other words, they are type casted.</span></span> <span data-ttu-id="57821-108">ID 值會使用前置詞。</span><span class="sxs-lookup"><span data-stu-id="57821-108">Prefixes are used for the ID values.</span></span>  
  
 <span data-ttu-id="57821-109">假設您想要建構如下所示的 XML：</span><span class="sxs-lookup"><span data-stu-id="57821-109">Assume that you want to construct XML as shown in the following:</span></span>  
  
```  
<Customer CustomerID="C1" SalesOrderIDList=" O11 O22 O33..." >  
    <SalesOrder SalesOrderID="O11" OrderDate="..." />  
    <SalesOrder SalesOrderID="O22" OrderDate="..." />  
    <SalesOrder SalesOrderID="O33" OrderDate="..." />  
    ...  
</Customer>  
```  
  
 <span data-ttu-id="57821-110">< `SalesOrderIDList` > 元素的 `Customer` 屬性是多重值屬性，會參考到 < `SalesOrderID` > 元素的 `SalesOrder` 屬性。</span><span class="sxs-lookup"><span data-stu-id="57821-110">The `SalesOrderIDList` attribute of the < `Customer` > element is a multivalued attribute that refers to the `SalesOrderID` attribute of the < `SalesOrder` > element.</span></span> <span data-ttu-id="57821-111">若要建立此連結，`SalesOrderID` 屬性必須宣告為 `ID` 類型，而且 <`Customer`> 元素的 `SalesOrderIDList` 屬性必須宣告為 `IDREFS` 類型。</span><span class="sxs-lookup"><span data-stu-id="57821-111">To establish this link, the `SalesOrderID` attribute must be declared of `ID` type, and the `SalesOrderIDList` attribute of the < `Customer`> element must be declared of `IDREFS` type.</span></span> <span data-ttu-id="57821-112">因為一位客戶可以下多份訂單，所以要使用 `IDREFS` 類型。</span><span class="sxs-lookup"><span data-stu-id="57821-112">Because a customer can request several orders, the `IDREFS` type is used.</span></span>  
  
 <span data-ttu-id="57821-113">`IDREFS` 類型的元素也會有一個以上的值。</span><span class="sxs-lookup"><span data-stu-id="57821-113">Elements of `IDREFS` type also have more than one value.</span></span> <span data-ttu-id="57821-114">因此，您必須使用個別的 select 子句，以重複使用相同的標記、父系及索引鍵資料行資訊。</span><span class="sxs-lookup"><span data-stu-id="57821-114">Therefore, you have to use a separate select clause that will reuse the same tag, parent, and key column information.</span></span> <span data-ttu-id="57821-115">然後 `ORDER BY` 必須確定構成 `IDREFS` 值的資料列順序，在它們的父成員下會分在同一組。</span><span class="sxs-lookup"><span data-stu-id="57821-115">The `ORDER BY` then has to ensure that the sequence of rows that make up the `IDREFS` values appears grouped together under their parent element.</span></span>  
  
 <span data-ttu-id="57821-116">以下查詢會產生您想要的 XML。</span><span class="sxs-lookup"><span data-stu-id="57821-116">This is the query that produces the XML you want.</span></span> <span data-ttu-id="57821-117">此查詢會使用 `ID` 和 `IDREFS` 指示詞來複寫資料行名稱 (`SalesOrder!2!SalesOrderID!ID`、 `Customer!1!SalesOrderIDList!IDREFS`) 中的類型。</span><span class="sxs-lookup"><span data-stu-id="57821-117">The query uses the `ID` and `IDREFS` directives to overwrite the types in the column names (`SalesOrder!2!SalesOrderID!ID`, `Customer!1!SalesOrderIDList!IDREFS`).</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        C.CustomerID       [Customer!1!CustomerID],  
        NULL               [Customer!1!SalesOrderIDList!IDREFS],  
        NULL               [SalesOrder!2!SalesOrderID!ID],  
        NULL               [SalesOrder!2!OrderDate]  
FROM   Sales.Customer C   
UNION ALL   
SELECT  1 as Tag,  
        0 as Parent,  
        C.CustomerID,  
        'O-'+CAST(SalesOrderID as varchar(10)),   
        NULL,  
        NULL  
FROM   Sales.Customer AS C  
INNER JOIN Sales.SalesOrderHeader AS SOH  
    ON  C.CustomerID = SOH.CustomerID  
UNION ALL  
SELECT 2 as Tag,  
       1 as Parent,  
        C.CustomerID,  
        NULL,  
        'O-'+CAST(SalesOrderID as varchar(10)),  
        OrderDate  
FROM   Sales.Customer AS C  
INNER JOIN Sales.SalesOrderHeader AS SOH  
    ON  C.CustomerID = SOH.CustomerIDORDER BY [Customer!1!CustomerID] ,  
         [SalesOrder!2!SalesOrderID!ID],  
         [Customer!1!SalesOrderIDList!IDREFS]  
FOR XML EXPLICIT;  
```  
  
## <a name="see-also"></a><span data-ttu-id="57821-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57821-118">See Also</span></span>  
 [<span data-ttu-id="57821-119">搭配 FOR XML 使用 EXPLICIT 模式</span><span class="sxs-lookup"><span data-stu-id="57821-119">Use EXPLICIT Mode with FOR XML</span></span>](use-explicit-mode-with-for-xml.md)  
  
  
