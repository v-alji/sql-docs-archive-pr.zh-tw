---
title: 建立 XML 資料行檢視 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- views [XML in SQL Server]
ms.assetid: eb5f0439-1f69-49c2-8759-e59bda1633b7
author: rothja
ms.author: jroth
ms.openlocfilehash: bf06f1107cbf4875eb63fe6747775b5c5c04810c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706294"
---
# <a name="create-views-over-xml-columns"></a><span data-ttu-id="bbea1-102">建立 XML 資料行檢視</span><span class="sxs-lookup"><span data-stu-id="bbea1-102">Create Views over XML Columns</span></span>
  <span data-ttu-id="bbea1-103">您可以使用 `xml` 類型的資料行建立檢視。</span><span class="sxs-lookup"><span data-stu-id="bbea1-103">You can use an `xml` type column to create views.</span></span> <span data-ttu-id="bbea1-104">下列範例會建立一個檢視，而在此檢視中會使用 `xml` 資料類型的 `value()` 方法，擷取 `xml` 類型資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="bbea1-104">The following example creates a view in which the value from an `xml` type column is retrieved using the `value()` method of the `xml` data type.</span></span>  
  
```  
-- Create the table.  
CREATE TABLE T (  
    ProductID          int primary key,   
    CatalogDescription xml)  
GO  
-- Insert sample data.  
INSERT INTO T values(1,'<ProductDescription ProductID="1" ProductName="SomeName" />')  
GO  
-- Create view (note the value() method used to retrieve ProductName   
-- attribute value from the XML).  
CREATE VIEW MyView AS   
  SELECT ProductID,  
         CatalogDescription.value('(/ProductDescription/@ProductName)[1]', 'varchar(40)') AS PName  
  FROM T  
GO   
```  
  
 <span data-ttu-id="bbea1-105">針對此檢視執行下列查詢：</span><span class="sxs-lookup"><span data-stu-id="bbea1-105">Execute the following query against the view:</span></span>  
  
```  
SELECT *   
FROM   MyView  
```  
  
 <span data-ttu-id="bbea1-106">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="bbea1-106">This is the result:</span></span>  
  
```  
ProductID   PName        
----------- ------------  
1           SomeName   
```  
  
 <span data-ttu-id="bbea1-107">請注意下列有關使用 `xml` 資料類型來建立檢視的要點：</span><span class="sxs-lookup"><span data-stu-id="bbea1-107">Note the following points about using the `xml` data type to create views:</span></span>  
  
-   <span data-ttu-id="bbea1-108">xml 資料類型可以在具體化檢視中建立。</span><span class="sxs-lookup"><span data-stu-id="bbea1-108">The xml data type can be created in a materialized view.</span></span> <span data-ttu-id="bbea1-109">具體化檢視無法以 xml 資料類型方法為基礎，</span><span class="sxs-lookup"><span data-stu-id="bbea1-109">The materialized view cannot be based on an xml data type method.</span></span> <span data-ttu-id="bbea1-110">但是，可以將它轉換成與基底資料表中之 xml 類型資料行不同的 XML 結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="bbea1-110">However, it can be cast to an XML schema collection that is different from the xml type column in the base table.</span></span>  
  
-   <span data-ttu-id="bbea1-111">`xml` 資料類型無法用於「分散式資料分割檢視」。</span><span class="sxs-lookup"><span data-stu-id="bbea1-111">The `xml` data type cannot be used in Distributed Partitioned Views.</span></span>  
  
-   <span data-ttu-id="bbea1-112">針對此檢視執行的 SQL 預測將不會發送到檢視定義的 XQuery 中。</span><span class="sxs-lookup"><span data-stu-id="bbea1-112">SQL predicates running against the view will not be pushed into the XQuery of the view definition.</span></span>  
  
-   <span data-ttu-id="bbea1-113">檢視中的 XML 資料類型方法將無法更新。</span><span class="sxs-lookup"><span data-stu-id="bbea1-113">XML data type methods in a view are not updatable.</span></span>  
  
  
