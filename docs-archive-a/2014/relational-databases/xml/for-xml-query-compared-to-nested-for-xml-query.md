---
title: 與巢狀 FOR XML 查詢比較的 FOR XML 查詢 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML query
- queries [XML in SQL Server], comparing query types
ms.assetid: 19225b4a-ee3f-47cf-8bcc-52699eeda32c
author: rothja
ms.author: jroth
ms.openlocfilehash: ca10060702d0c7e50f2be79310c55e177dca358d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710461"
---
# <a name="for-xml-query-compared-to-nested-for-xml-query"></a><span data-ttu-id="039fb-102">與巢狀 FOR XML 查詢比較的 FOR XML 查詢</span><span class="sxs-lookup"><span data-stu-id="039fb-102">FOR XML Query Compared to Nested FOR XML Query</span></span>
  <span data-ttu-id="039fb-103">本主題會將單一層 FOR XML 查詢與巢狀 FOR XML 查詢做比較。</span><span class="sxs-lookup"><span data-stu-id="039fb-103">This topic compares a single-level FOR XML query to a nested FOR XML query.</span></span> <span data-ttu-id="039fb-104">使用巢狀 FOR XML 查詢的其中一個好處，就是可以針對查詢結果指定屬性中心及元素中心 XML 的組合。</span><span class="sxs-lookup"><span data-stu-id="039fb-104">One of the benefits of using nested FOR XML queries is that you can specify a combination of attribute-centric and element-centric XML for query results.</span></span> <span data-ttu-id="039fb-105">以下範例將提供示範。</span><span class="sxs-lookup"><span data-stu-id="039fb-105">The example demonstrates this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="039fb-106">範例</span><span class="sxs-lookup"><span data-stu-id="039fb-106">Example</span></span>  
 <span data-ttu-id="039fb-107">下列 `SELECT` 查詢會擷取 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫中的產品類別目錄及子類別目錄資訊。</span><span class="sxs-lookup"><span data-stu-id="039fb-107">The following `SELECT` query retrieves product category and subcategory information in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="039fb-108">此查詢中沒有巢狀的 FOR XML。</span><span class="sxs-lookup"><span data-stu-id="039fb-108">There is no nested FOR XML in the query.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT   ProductCategory.ProductCategoryID,   
         ProductCategory.Name as CategoryName,  
         ProductSubCategory.ProductSubCategoryID,   
         ProductSubCategory.Name  
FROM     Production.ProductCategory, Production.ProductSubCategory  
WHERE    ProductCategory.ProductCategoryID = ProductSubCategory.ProductCategoryID  
ORDER BY ProductCategoryID  
FOR XML AUTO, TYPE  
GO  
```  
  
 <span data-ttu-id="039fb-109">以下是部份結果：</span><span class="sxs-lookup"><span data-stu-id="039fb-109">This is the partial result:</span></span>  
  
```  
<ProductCategory ProductCategoryID="1" CategoryName="Bike">  
  <ProductSubCategory ProductSubCategoryID="1" Name="Mountain Bike"/>  
  <ProductSubCategory ProductSubCategoryID="2" Name="Road Bike"/>  
  <ProductSubCategory ProductSubCategoryID="3" Name="Touring Bike"/>  
</ProductCategory>  
...  
```  
  
 <span data-ttu-id="039fb-110">如果在查詢中指定 `ELEMENTS` 指示詞，會收到元素中心的結果，如以下結果片段所示：</span><span class="sxs-lookup"><span data-stu-id="039fb-110">If you specify the `ELEMENTS` directive in the query, you receive an element-centric result, as shown in the following result fragment:</span></span>  
  
```  
<ProductCategory>  
  <ProductCategoryID>1</ProductCategoryID>  
  <CategoryName>Bike</CategoryName>  
  <ProductSubCategory>  
    <ProductSubCategoryID>1</ProductSubCategoryID>  
    <Name>Mountain Bike</Name>  
  </ProductSubCategory>  
  <ProductSubCategory>  
     ...  
  </ProductSubCategory>  
</ProductCategory>  
```  
  
 <span data-ttu-id="039fb-111">接下來，假設您想要產生 XML 階層，結合屬性中心及元素中心的 XML，如以下片段所示：</span><span class="sxs-lookup"><span data-stu-id="039fb-111">Next, assume that you want to generate an XML hierarchy that is a combination of attribute-centric and element-centric XML, as shown in the following fragment:</span></span>  
  
```  
<ProductCategory ProductCategoryID="1" CategoryName="Bike">  
  <ProductSubCategory>  
    <ProductSubCategoryID>1</ProductSubCategoryID>  
    <SubCategoryName>Mountain Bike</SubCategoryName></ProductSubCategory>  
  <ProductSubCategory>  
     ...  
  <ProductSubCategory>  
     ...  
</ProductCategory>  
```  
  
 <span data-ttu-id="039fb-112">在前述片段中，類別目錄識別碼及類別目錄名稱等產品類別目錄資訊為屬性。</span><span class="sxs-lookup"><span data-stu-id="039fb-112">In the previous fragment, product category information such as category ID and category name are attributes.</span></span> <span data-ttu-id="039fb-113">但是，子類別目錄資訊是元素中心的。</span><span class="sxs-lookup"><span data-stu-id="039fb-113">However, the subcategory information is element-centric.</span></span> <span data-ttu-id="039fb-114">若要建構 <`ProductCategory`> 元素，您可以撰寫 `FOR XML` 查詢，如下所示：</span><span class="sxs-lookup"><span data-stu-id="039fb-114">To construct the <`ProductCategory`> element, you can write a `FOR XML` query as shown in the following:</span></span>  
  
```  
SELECT ProductCategoryID, Name as CategoryName  
FROM Production.ProductCategory ProdCat  
ORDER BY ProductCategoryID  
FOR XML AUTO, TYPE  
```  
  
 <span data-ttu-id="039fb-115">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="039fb-115">This is the result:</span></span>  
  
```  
< ProdCat ProductCategoryID="1" CategoryName="Bikes" />  
< ProdCat ProductCategoryID="2" CategoryName="Components" />  
< ProdCat ProductCategoryID="3" CategoryName="Clothing" />  
< ProdCat ProductCategoryID="4" CategoryName="Accessories" />  
```  
  
 <span data-ttu-id="039fb-116">若要在希望的 XML 中建構巢狀的 <`ProductSubCategory`> 元素，您可以接著加入巢狀 `FOR XML` 查詢，如下所示：</span><span class="sxs-lookup"><span data-stu-id="039fb-116">To construct the nested <`ProductSubCategory`> elements in the XML you want, you then add a nested `FOR XML` query, as shown in the following:</span></span>  
  
```  
SELECT ProductCategoryID, Name as CategoryName,  
       (SELECT ProductSubCategoryID, Name SubCategoryName  
        FROM   Production.ProductSubCategory  
        WHERE ProductSubCategory.ProductCategoryID =   
              ProductCategory.ProductCategoryID  
        FOR XML AUTO, TYPE, ELEMENTS  
       )  
FROM Production.ProductCategory  
ORDER BY ProductCategoryID  
FOR XML AUTO, TYPE  
```  
  
 <span data-ttu-id="039fb-117">下列為上一個查詢的注意事項：</span><span class="sxs-lookup"><span data-stu-id="039fb-117">Note the following in the previous query:</span></span>  
  
-   <span data-ttu-id="039fb-118">內部 `FOR XML` 查詢會擷取產品子類別目錄資訊。</span><span class="sxs-lookup"><span data-stu-id="039fb-118">The inner `FOR XML` query retrieves product subcategory information.</span></span> <span data-ttu-id="039fb-119">在內部 `ELEMENTS` 中加入 `FOR XML` 指示詞，以產生元素中心的 XML，此 XML 已加入至外部查詢產生的 XML 中。</span><span class="sxs-lookup"><span data-stu-id="039fb-119">The `ELEMENTS` directive is added in the inner `FOR XML` to generate element-centric XML that is added to the XML generated by the outer query.</span></span> <span data-ttu-id="039fb-120">根據預設，外部查詢會產生屬性中西的 XML。</span><span class="sxs-lookup"><span data-stu-id="039fb-120">By default, the outer query generates attribute-centric XML.</span></span>  
  
-   <span data-ttu-id="039fb-121">在內部查詢中指定 `TYPE` 指示詞，好讓結果屬於 **xml** 類型。</span><span class="sxs-lookup"><span data-stu-id="039fb-121">In the inner query, the `TYPE` directive is specified so the result is of **xml** type.</span></span> <span data-ttu-id="039fb-122">如果未指定 `TYPE`，則結果會以 `nvarchar(max)` 類型傳回，而 XML 資料會以實體傳回。</span><span class="sxs-lookup"><span data-stu-id="039fb-122">If `TYPE` is not specified, the result is returned as `nvarchar(max)` type and the XML data is returned as entities.</span></span>  
  
-   <span data-ttu-id="039fb-123">外部查詢也可以指定 `TYPE` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="039fb-123">The outer query also specifies the `TYPE` directive.</span></span> <span data-ttu-id="039fb-124">因此，此查詢的結果會以 **xml** 類型傳回給用戶端。</span><span class="sxs-lookup"><span data-stu-id="039fb-124">Therefore, the result of this query is returned to the client as **xml** type.</span></span>  
  
 <span data-ttu-id="039fb-125">以下是部份結果：</span><span class="sxs-lookup"><span data-stu-id="039fb-125">This is the partial result:</span></span>  
  
```  
<ProductCategory ProductCategoryID="1" CategoryName="Bike">  
  <ProductSubCategory>  
    <ProductSubCategoryID>1</ProductSubCategoryID>  
    <SubCategoryName>Mountain Bike</SubCategoryName></ProductSubCategory>  
  <ProductSubCategory>  
     ...  
  <ProductSubCategory>  
     ...  
</ProductCategory>  
```  
  
 <span data-ttu-id="039fb-126">以下查詢只是前述查詢的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="039fb-126">The following query is just an extension of the previous query.</span></span> <span data-ttu-id="039fb-127">它會顯示 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫的完整產品階層。</span><span class="sxs-lookup"><span data-stu-id="039fb-127">It shows the full product hierarchy in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="039fb-128">這包括下列項目：</span><span class="sxs-lookup"><span data-stu-id="039fb-128">This includes the following:</span></span>  
  
-   <span data-ttu-id="039fb-129">產品類別目錄</span><span class="sxs-lookup"><span data-stu-id="039fb-129">Product categories</span></span>  
  
-   <span data-ttu-id="039fb-130">每個_類別目錄中的產品子類別目錄</span><span class="sxs-lookup"><span data-stu-id="039fb-130">Product subcategories in each category</span></span>  
  
-   <span data-ttu-id="039fb-131">每個子類別目錄中的產品型號</span><span class="sxs-lookup"><span data-stu-id="039fb-131">Product models in each subcategory</span></span>  
  
-   <span data-ttu-id="039fb-132">每個型號中的產品</span><span class="sxs-lookup"><span data-stu-id="039fb-132">Products in each model</span></span>  
  
 <span data-ttu-id="039fb-133">以下查詢應該有助於了解 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫：</span><span class="sxs-lookup"><span data-stu-id="039fb-133">You might find the following query useful in understanding the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database:</span></span>  
  
```  
SELECT ProductCategoryID, Name as CategoryName,  
       (SELECT ProductSubCategoryID, Name SubCategoryName,  
               (SELECT ProductModel.ProductModelID,   
                       ProductModel.Name as ModelName,  
                       (SELECT ProductID, Name as ProductName, Color  
                        FROM   Production.Product  
                        WHERE  Product.ProductModelID =   
                               ProductModel.ProductModelID  
                        FOR XML AUTO, TYPE)  
                FROM   (SELECT distinct ProductModel.ProductModelID,   
                               ProductModel.Name  
                        FROM   Production.ProductModel,   
                               Production.Product  
                        WHERE  ProductModel.ProductModelID =   
                               Product.ProductModelID  
                        AND    Product.ProductSubCategoryID =   
                               ProductSubCategory.ProductSubCategoryID)   
                                  ProductModel  
                FOR XML AUTO, type  
               )  
        FROM Production.ProductSubCategory  
        WHERE ProductSubCategory.ProductCategoryID =   
              ProductCategory.ProductCategoryID  
        FOR XML AUTO, TYPE, ELEMENTS  
       )  
FROM Production.ProductCategory  
ORDER BY ProductCategoryID  
FOR XML AUTO, TYPE  
```  
  
 <span data-ttu-id="039fb-134">以下是部份結果：</span><span class="sxs-lookup"><span data-stu-id="039fb-134">This is the partial result:</span></span>  
  
```  
<Production.ProductCategory ProductCategoryID="1" CategoryName="Bikes">  
  <Production.ProductSubCategory>  
    <ProductSubCategoryID>1</ProductSubCategoryID>  
    <SubCategoryName>Mountain Bikes</SubCategoryName>  
    <ProductModel ProductModelID="19" ModelName="Mountain-100">  
      <Production.Product ProductID="771"   
                ProductName="Mountain-100 Silver, 38" Color="Silver" />  
      <Production.Product ProductID="772"   
                ProductName="Mountain-100 Silver, 42" Color="Silver" />  
      <Production.Product ProductID="773"   
                ProductName="Mountain-100 Silver, 44" Color="Silver" />  
        ...  
    </ProductModel>  
     ...  
```  
  
 <span data-ttu-id="039fb-135">如果從產生產品子類別目錄的巢狀 `ELEMENTS` 查詢移除 `FOR XML` 指示詞，整個結果將為屬性中心。</span><span class="sxs-lookup"><span data-stu-id="039fb-135">If you remove the `ELEMENTS` directive from the nested `FOR XML` query that generates product subcategories, the whole result is attribute-centric.</span></span> <span data-ttu-id="039fb-136">然後您可以無套疊的方式撰寫此查詢</span><span class="sxs-lookup"><span data-stu-id="039fb-136">You can then write this query without nesting.</span></span> <span data-ttu-id="039fb-137">加入 `ELEMENTS` 會使 XML 一部份為屬性中心，一部份為元素中心。</span><span class="sxs-lookup"><span data-stu-id="039fb-137">The addition of `ELEMENTS` results in an XML that is partly attribute-centric and partly element-centric.</span></span> <span data-ttu-id="039fb-138">此結果無法由單一層 FOR XML 查詢產生。</span><span class="sxs-lookup"><span data-stu-id="039fb-138">This result cannot be generated by a single-level, FOR XML query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="039fb-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="039fb-139">See Also</span></span>  
 [<span data-ttu-id="039fb-140">使用巢狀 FOR XML 查詢</span><span class="sxs-lookup"><span data-stu-id="039fb-140">Use Nested FOR XML Queries</span></span>](use-nested-for-xml-queries.md)  
  
  
