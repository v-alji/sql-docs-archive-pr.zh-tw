---
title: 檢視儲存的 XML 結構描述集合 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- schema collections [SQL Server], viewing
- XML schemas [SQL Server], viewing
- CREATE XML SCHEMA COLLECTION statement
- xml_schema_namespace function
- XML schema collections [SQL Server], viewing
- displaying XML schema collections
- viewing XML schema collections
ms.assetid: e38031af-22df-4cd9-a14e-e316b822f91b
author: rothja
ms.author: jroth
ms.openlocfilehash: 6383fb17183a991d2f83325044663cc9671e9442
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592550"
---
# <a name="view-a-stored-xml-schema-collection"></a><span data-ttu-id="a08b8-102">檢視儲存的 XML 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="a08b8-102">View a Stored XML Schema Collection</span></span>
  <span data-ttu-id="a08b8-103">使用 [CREATE XML SCHEMA COLLECTION](/sql/t-sql/statements/create-xml-schema-collection-transact-sql)匯入 XML 結構描述集合之後，即會將結構描述元件儲存在中繼資料中。</span><span class="sxs-lookup"><span data-stu-id="a08b8-103">After you import an XML schema collection by using [CREATE XML SCHEMA COLLECTION](/sql/t-sql/statements/create-xml-schema-collection-transact-sql), the schema components are stored in the metadata.</span></span> <span data-ttu-id="a08b8-104">您可以使用 [xml_schema_namespace](/sql/t-sql/xml/xml-schema-namespace)內建函數以重建 XML 結構描述集合。</span><span class="sxs-lookup"><span data-stu-id="a08b8-104">You can use the [xml_schema_namespace](/sql/t-sql/xml/xml-schema-namespace)intrinsic function to reconstruct the XML schema collection.</span></span> <span data-ttu-id="a08b8-105">這個函數會傳回 `xml` 資料類型執行個體。</span><span class="sxs-lookup"><span data-stu-id="a08b8-105">This function returns an `xml` data type instance.</span></span>  
  
 <span data-ttu-id="a08b8-106">例如，下列查詢會從`ProductDescriptionSchemaCollection`資料庫的生產關聯式結構描述擷取 XML 結構描述集合 ( [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] )。</span><span class="sxs-lookup"><span data-stu-id="a08b8-106">For example, the following query retrieves an XML schema collection (`ProductDescriptionSchemaCollection`) from the production relational schema in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection')  
GO  
```  
  
 <span data-ttu-id="a08b8-107">如果您只想查看 XML 結構描述集合的一個結構描述，您可以針對 `xml_schema_namespace` 傳回的 `xml` 類型結果指定 XQuery。</span><span class="sxs-lookup"><span data-stu-id="a08b8-107">If you want to see only one schema from the XML schema collection, you can specify XQuery against the `xml` type result that is returned by `xml_schema_namespace`.</span></span>  
  
```  
SELECT xml_schema_namespace(N'RelationalSchemaName',N'XmlSchemaCollectionName').query('  
/xs:schema[@targetNamespace="TargetNameSpace"]  
')  
GO  
```  
  
 <span data-ttu-id="a08b8-108">例如，下列查詢可從 `ProductDescriptionSchemaCollection` XML 結構描述集合擷取產品保證和維護 XML 結構描述資訊。</span><span class="sxs-lookup"><span data-stu-id="a08b8-108">For example, the following query retrieves product warranty and maintenance XML schema information from the `ProductDescriptionSchemaCollection` XML schema collection.</span></span>  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection').query('  
/xs:schema[@targetNamespace="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain"]  
')  
GO  
```  
  
 <span data-ttu-id="a08b8-109">您也可以將選擇性的目標命名空間當做第三個參數傳遞至 `xml_schema_namespace` 函數，以擷取集合中的特定結構描述，如下列查詢所示：</span><span class="sxs-lookup"><span data-stu-id="a08b8-109">You can also pass the optional target namespace as the third parameter to the `xml_schema_namespace` function to retrieve specific schema from the collection, as shown in the following query:</span></span>  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection', N'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain')  
GO  
```  
  
 <span data-ttu-id="a08b8-110">當使用資料庫中的 CREATE XML SCHEMA COLLECTION 來建立 XML 結構描述集合時，陳述式會在中繼資料內儲存結構描述元件。</span><span class="sxs-lookup"><span data-stu-id="a08b8-110">When you create an XML schema collection by using CREATE XML SCHEMA COLLECTION in the database, the statement stores the schema components in the metadata.</span></span> <span data-ttu-id="a08b8-111">請注意只會儲存 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可辨識的結構描述元件。</span><span class="sxs-lookup"><span data-stu-id="a08b8-111">Note that only the schema components that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] understands are stored.</span></span> <span data-ttu-id="a08b8-112">不會儲存任何註解或非 XSD 屬性。</span><span class="sxs-lookup"><span data-stu-id="a08b8-112">Any comments, annotations, or non-XSD attributes are not stored.</span></span> <span data-ttu-id="a08b8-113">因此， **xml_schema_namespace** 重新建構的結構描述在功能上等於原始結構描述，但是它看起來不一定相同。</span><span class="sxs-lookup"><span data-stu-id="a08b8-113">Therefore, the schema reconstructed by **xml_schema_namespace** is functionally equivalent to the original schema, but it will not necessarily look the same.</span></span> <span data-ttu-id="a08b8-114">例如，您將看不到與原始結構描述中相同的前置詞。</span><span class="sxs-lookup"><span data-stu-id="a08b8-114">For example, you will not see the same prefixes you had in the original schema.</span></span> <span data-ttu-id="a08b8-115">**xml_schema_namespace** 傳回的結構描述使用 **t** 作為目標命名空間以及其他命名空間 **ns1**、 **ns2**等的前置詞。</span><span class="sxs-lookup"><span data-stu-id="a08b8-115">The schema returned by **xml_schema_namespace** uses **t** as the prefix for the target namespace and **ns1**, **ns2**, and so on, for other namespaces.</span></span>  
  
 <span data-ttu-id="a08b8-116">如果您想要保留一份完全相同的 XML 結構描述，您應該將 XML 結構描述儲存在檔案或資料庫資料表的 `xml` 類型資料行中。</span><span class="sxs-lookup"><span data-stu-id="a08b8-116">If you want to retain an identical copy of the XML schemas, you should save your XML schema in a file or in a database table in an `xml` type column.</span></span>  
  
 <span data-ttu-id="a08b8-117">[sys.xml_schema_collections](/sql/relational-databases/system-catalog-views/sys-xml-schema-collections-transact-sql) 目錄檢視也會傳回 XML 結構描述集合的資訊。</span><span class="sxs-lookup"><span data-stu-id="a08b8-117">The [sys.xml_schema_collections](/sql/relational-databases/system-catalog-views/sys-xml-schema-collections-transact-sql) catalog view also returns information about XML schema collections.</span></span> <span data-ttu-id="a08b8-118">此資訊包含集合的名稱、建立日期以及集合的擁有者。</span><span class="sxs-lookup"><span data-stu-id="a08b8-118">This information includes the name of the collection, the creation date, and the owner of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a08b8-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a08b8-119">See Also</span></span>  
 [<span data-ttu-id="a08b8-120">XML 結構描述集合 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="a08b8-120">XML Schema Collections &#40;SQL Server&#41;</span></span>](xml-schema-collections-sql-server.md)  
  
  
