---
title: 建立 XML 資料類型變數與資料行 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- xml data type [SQL Server], variables
- xml data type [SQL Server], columns
ms.assetid: 8994ab6e-5519-4ba2-97a1-fac8af6f72db
author: rothja
ms.author: jroth
ms.openlocfilehash: 08b79888eb47634deaccc910b2ea3c93800b7c78
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706290"
---
# <a name="create-xml-data-type-variables-and-columns"></a><span data-ttu-id="77d4c-102">建立 XML 資料類型變數與資料行</span><span class="sxs-lookup"><span data-stu-id="77d4c-102">Create XML Data Type Variables and Columns</span></span>
  <span data-ttu-id="77d4c-103">`xml` 資料類型是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的內建資料類型，而且與其他內建類型有些相似，例如 `int` 與 `varchar`。</span><span class="sxs-lookup"><span data-stu-id="77d4c-103">The `xml` data type is a built-in data type in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and is somewhat similar to other built-in types such as `int` and `varchar`.</span></span> <span data-ttu-id="77d4c-104">如同其他內建類型， `xml` 當您建立資料表作為變數類型、參數類型、函數傳回類型，或是在[CAST 和 CONVERT](/sql/t-sql/functions/cast-and-convert-transact-sql)中時，您可以使用資料類型做為資料行類型。</span><span class="sxs-lookup"><span data-stu-id="77d4c-104">As with other built-in types, you can use the `xml` data type as a column type when you create a table as a variable type, a parameter type, a function-return type, or in [CAST and CONVERT](/sql/t-sql/functions/cast-and-convert-transact-sql).</span></span>  
  
## <a name="creating-columns-and-variables"></a><span data-ttu-id="77d4c-105">建立資料行和變數</span><span class="sxs-lookup"><span data-stu-id="77d4c-105">Creating Columns and Variables</span></span>  
 <span data-ttu-id="77d4c-106">若要在資料表中建立 `xml` 類型資料行，請使用 `CREATE TABLE` 陳述式，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="77d4c-106">To create an `xml` type column as part of a table, use a `CREATE TABLE` statement, as shown in the following example:</span></span>  
  
```  
CREATE TABLE T1(Col1 int primary key, Col2 xml)   
```  
  
 <span data-ttu-id="77d4c-107">您可以使用 `DECLARE statement` 來建立 `xml` 類型的變數，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="77d4c-107">You can use a `DECLARE statement` to create a variable of `xml` type, as the following example shows.</span></span>  
  
```  
DECLARE @x xml   
```  
  
 <span data-ttu-id="77d4c-108">藉由指定 XML 結構描述集合來建立具類型的 `xml` 變數，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="77d4c-108">Create a typed `xml` variable by specifying an XML schema collection, as shown in the following example.</span></span>  
  
```  
DECLARE @x xml (Sales.StoreSurveySchemaCollection)  
```  
  
 <span data-ttu-id="77d4c-109">若要將 `xml` 類型參數傳遞給預存程序，請使用 `CREATE PROCEDURE` 陳述式，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="77d4c-109">To pass an `xml` type parameter to a stored procedure, use a `CREATE PROCEDURE` statement, as shown in the following example.</span></span>  
  
```  
CREATE PROCEDURE SampleProc(@XmlDoc xml) AS ...   
```  
  
 <span data-ttu-id="77d4c-110">您可以使用 XQuery 來查詢儲存在資料行、參數或變數中的 XML 執行個體中。</span><span class="sxs-lookup"><span data-stu-id="77d4c-110">You can use XQuery to query XML instances stored in columns, parameters, or variables.</span></span> <span data-ttu-id="77d4c-111">您也可以使用「XML 資料操作語言」(XML DML) 來套用 XML 執行個體的更新。</span><span class="sxs-lookup"><span data-stu-id="77d4c-111">You can also use the XML Data Manipulation Language (XML DML) to apply updates to the XML instances.</span></span> <span data-ttu-id="77d4c-112">由於 XQuery 標準在開發時並不會定義 XQuery DML，因此 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 引進了 XQuery 的 [XML 資料修改語言](/sql/t-sql/xml/xml-data-modification-language-xml-dml) 擴充功能。</span><span class="sxs-lookup"><span data-stu-id="77d4c-112">Because the XQuery standard did not define XQuery DML at the time of development, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] introduces [XML Data Modification Language](/sql/t-sql/xml/xml-data-modification-language-xml-dml) extensions to XQuery.</span></span> <span data-ttu-id="77d4c-113">這些延伸模組可讓您執行插入、更新和刪除作業。</span><span class="sxs-lookup"><span data-stu-id="77d4c-113">These extensions allow you to perform insert, update, and delete operations.</span></span>  
  
## <a name="assigning-defaults"></a><span data-ttu-id="77d4c-114">指派預設值</span><span class="sxs-lookup"><span data-stu-id="77d4c-114">Assigning Defaults</span></span>  
 <span data-ttu-id="77d4c-115">在資料表中，您可以將預設的 XML 執行個體指派給 `xml` 類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="77d4c-115">In a table, you can assign a default XML instance to a column of `xml` type.</span></span> <span data-ttu-id="77d4c-116">您可以使用以下兩種方法的其中一種來提供預設的 XML：使用 XML 常數，或是明確轉換成 `xml` 類型。</span><span class="sxs-lookup"><span data-stu-id="77d4c-116">You can provide the default XML in one of two ways: by using an XML constant, or by using an explicit cast to the `xml` type.</span></span>  
  
 <span data-ttu-id="77d4c-117">若要將預設 XML 提供為 XML 常數，請使用類似以下範例的語法。</span><span class="sxs-lookup"><span data-stu-id="77d4c-117">To provide the default XML as an XML constant, use syntax as shown in the following example.</span></span> <span data-ttu-id="77d4c-118">請注意，此字串會隱含轉換成 `xml` 類型。</span><span class="sxs-lookup"><span data-stu-id="77d4c-118">Note that the string is implicitly CAST to `xml` type.</span></span>  
  
```  
CREATE TABLE T (XmlColumn xml default N'<element1/><element2/>')  
```  
  
 <span data-ttu-id="77d4c-119">若要將預設 XML 提供為轉換成 `CAST` 的明確 `xml`，請使用類似以下範例的語法。</span><span class="sxs-lookup"><span data-stu-id="77d4c-119">To provide the default XML as an explicit `CAST` to `xml`, use syntax as shown in the following example.</span></span>  
  
```  
CREATE TABLE T (XmlColumn xml   
                  default CAST(N'<element1/><element2/>' AS xml))  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="77d4c-120">也支援在 `xml` 類型之資料行上的 NULL 和 NOT NULL 條件約束。</span><span class="sxs-lookup"><span data-stu-id="77d4c-120">also supports NULL and NOT NULL constraints on columns of `xml` type.</span></span> <span data-ttu-id="77d4c-121">例如：</span><span class="sxs-lookup"><span data-stu-id="77d4c-121">For example:</span></span>  
  
```  
CREATE TABLE T (XmlColumn xml NOT NULL)  
```  
  
## <a name="specifying-constraints"></a><span data-ttu-id="77d4c-122">指定條件約束</span><span class="sxs-lookup"><span data-stu-id="77d4c-122">Specifying Constraints</span></span>  
 <span data-ttu-id="77d4c-123">當您建立 `xml` 類型的資料行時，您可以定義資料行層級或資料表層級的條件約束。</span><span class="sxs-lookup"><span data-stu-id="77d4c-123">When you create columns of `xml` type, you can define column-level or table-level constraints.</span></span> <span data-ttu-id="77d4c-124">在下列情況下，請使用條件約束：</span><span class="sxs-lookup"><span data-stu-id="77d4c-124">Use constraints in the following situations:</span></span>  
  
-   <span data-ttu-id="77d4c-125">您的商務規則無法以 XML 結構描述來表達。</span><span class="sxs-lookup"><span data-stu-id="77d4c-125">Your business rules cannot be expressed in XML schemas.</span></span> <span data-ttu-id="77d4c-126">例如，花店的送貨地址必須在該店的方圓 50 英哩內。</span><span class="sxs-lookup"><span data-stu-id="77d4c-126">For example, the delivery address of a flower shop must be within 50 miles of its business location.</span></span> <span data-ttu-id="77d4c-127">這一點可以在 XML 資料行上寫成條件約束。</span><span class="sxs-lookup"><span data-stu-id="77d4c-127">This can be written as a constraint on the XML column.</span></span> <span data-ttu-id="77d4c-128">條件約束可能會牽涉到 `xml` 資料類型方法。</span><span class="sxs-lookup"><span data-stu-id="77d4c-128">The constraint may involve `xml` data type methods.</span></span>  
  
-   <span data-ttu-id="77d4c-129">您的條件約束牽涉到資料表中的其他 XML 或非 XML 資料行。</span><span class="sxs-lookup"><span data-stu-id="77d4c-129">Your constraint involves other XML or non-XML columns in the table.</span></span> <span data-ttu-id="77d4c-130">有一個例子，就是強制 XML 執行個體中的「客戶識別碼」(`/Customer/@CustId`) 要符合關聯式 CustomerID 資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="77d4c-130">An example is the enforcement of the ID of a Customer (`/Customer/@CustId`) found in an XML instance to match the value in a relational CustomerID column.</span></span>  
  
 <span data-ttu-id="77d4c-131">您可以為具類型或不具類型的 `xml` 資料類型資料行指定條件約束。</span><span class="sxs-lookup"><span data-stu-id="77d4c-131">You can specify constraints for typed or untyped `xml` data type columns.</span></span> <span data-ttu-id="77d4c-132">不過，在指定條件約束時無法使用 [XML 資料類型方法](/sql/t-sql/xml/xml-data-type-methods) 。</span><span class="sxs-lookup"><span data-stu-id="77d4c-132">However, you cannot use the [XML data type methods](/sql/t-sql/xml/xml-data-type-methods) when you specify constraints.</span></span> <span data-ttu-id="77d4c-133">此外，請注意 `xml` 資料類型不支援下列資料行和資料表條件約束：</span><span class="sxs-lookup"><span data-stu-id="77d4c-133">Also, note that the `xml` data type does not support the following column and table constraints:</span></span>  
  
-   <span data-ttu-id="77d4c-134">PRIMARY KEY/ FOREIGN KEY</span><span class="sxs-lookup"><span data-stu-id="77d4c-134">PRIMARY KEY/ FOREIGN KEY</span></span>  
  
-   <span data-ttu-id="77d4c-135">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="77d4c-135">UNIQUE</span></span>  
  
-   <span data-ttu-id="77d4c-136">COLLATE</span><span class="sxs-lookup"><span data-stu-id="77d4c-136">COLLATE</span></span>  
  
     <span data-ttu-id="77d4c-137">XML 可自行提供編碼。</span><span class="sxs-lookup"><span data-stu-id="77d4c-137">XML provides its own encoding.</span></span> <span data-ttu-id="77d4c-138">定序僅適用於字串類型。</span><span class="sxs-lookup"><span data-stu-id="77d4c-138">Collations apply to string types only.</span></span> <span data-ttu-id="77d4c-139">`xml` 資料類型不是字串類型。</span><span class="sxs-lookup"><span data-stu-id="77d4c-139">The `xml` data type is not a string type.</span></span> <span data-ttu-id="77d4c-140">但它確實具有字串表示法，並允許轉換成字串資料類型，以及從字串資料類型轉換回來。</span><span class="sxs-lookup"><span data-stu-id="77d4c-140">However, it does have string representation and allows casting to and from string data types.</span></span>  
  
-   <span data-ttu-id="77d4c-141">RULE</span><span class="sxs-lookup"><span data-stu-id="77d4c-141">RULE</span></span>  
  
 <span data-ttu-id="77d4c-142">有一個替代使用條件約束的方法就是建立包裝函數 (用來包裝 `xml` 資料類型方法的使用者定義函數)，並在檢查條件約束中指定使用者定義函數，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="77d4c-142">An alternative to using constraints is to create a wrapper, user-defined function to wrap the `xml` data type method and specify user-defined function in the check constraint as shown in the following example.</span></span>  
  
 <span data-ttu-id="77d4c-143">在下列範例中，在 `Col2` 上的條件約束指定儲存在此資料行中的每個 XML 執行個體都必須有包含 `<ProductDescription>` 屬性的 `ProductID` 元素。</span><span class="sxs-lookup"><span data-stu-id="77d4c-143">In the following example, the constraint on `Col2` specifies that each XML instance stored in this column must have a `<ProductDescription>` element that contains a `ProductID` attribute.</span></span> <span data-ttu-id="77d4c-144">此條件約束是由使用者定義函數所強制執行：</span><span class="sxs-lookup"><span data-stu-id="77d4c-144">This constraint is enforced by this user-defined function:</span></span>  
  
```  
CREATE FUNCTION my_udf(@var xml) returns bit  
AS BEGIN   
RETURN @var.exist('/ProductDescription/@ProductID')  
END  
GO  
```  
  
 <span data-ttu-id="77d4c-145">請注意如果在執行個體中的 `exist()` 元素包含 `xml` 屬性， `1` 資料類型的 `<ProductDescription>` 方法會傳回 `ProductID` 。</span><span class="sxs-lookup"><span data-stu-id="77d4c-145">Note that the `exist()` method of the `xml` data type returns `1` if the `<ProductDescription>` element in the instance contains the `ProductID` attribute.</span></span> <span data-ttu-id="77d4c-146">否則會傳回 `0`。</span><span class="sxs-lookup"><span data-stu-id="77d4c-146">Otherwise, it returns `0`.</span></span>  
  
 <span data-ttu-id="77d4c-147">現在，您可以使用下列資料行層級的條件約束來建立資料表：</span><span class="sxs-lookup"><span data-stu-id="77d4c-147">Now, you can create a table with a column-level constraint as follows:</span></span>  
  
```  
CREATE TABLE T (  
    Col1 int primary key,   
    Col2 xml check(dbo.my_udf(Col2)=1))  
GO  
```  
  
 <span data-ttu-id="77d4c-148">下列插入會成功：</span><span class="sxs-lookup"><span data-stu-id="77d4c-148">The following insert succeeds:</span></span>  
  
```  
INSERT INTO T values(1,'<ProductDescription ProductID="1" />')  
```  
  
 <span data-ttu-id="77d4c-149">由於條件約束之故，下列插入會失敗：</span><span class="sxs-lookup"><span data-stu-id="77d4c-149">Because of the constraint, the following insert fails:</span></span>  
  
```  
INSERT INTO T values(1,'<Product />')  
```  
  
## <a name="same-or-different-table"></a><span data-ttu-id="77d4c-150">相同或相異的資料表</span><span class="sxs-lookup"><span data-stu-id="77d4c-150">Same or Different Table</span></span>  
 <span data-ttu-id="77d4c-151">您 `xml` 可以在包含其他關聯式資料行的資料表中，或在與主資料表具有外鍵關聯性的個別資料表中，建立資料類型資料行。</span><span class="sxs-lookup"><span data-stu-id="77d4c-151">An `xml` data type column can be created in a table that contains other relational columns, or in a separate table with a foreign key relationship to a main table.</span></span>  
  
 <span data-ttu-id="77d4c-152">`xml`當下列其中一個條件成立時，請在相同的資料表中建立資料類型資料行：</span><span class="sxs-lookup"><span data-stu-id="77d4c-152">Create an `xml` data type column in the same table when one of the following conditions is true:</span></span>  
  
-   <span data-ttu-id="77d4c-153">您的應用程式在 XML 資料行上執行資料擷取，而且不需要 XML 資料行的 XML 索引。</span><span class="sxs-lookup"><span data-stu-id="77d4c-153">Your application performs data retrieval on the XML column and does not require an XML index on the XML column.</span></span>  
  
-   <span data-ttu-id="77d4c-154">您想要在 `xml` 資料類型資料行上建立 XML 索引，且主資料表的主索引鍵與其叢集索引鍵相同。</span><span class="sxs-lookup"><span data-stu-id="77d4c-154">You want to build an XML index on the `xml` data type column and the primary key of the main table is the same as its clustering key.</span></span> <span data-ttu-id="77d4c-155">如需詳細資訊，請參閱 [XML 索引 &#40;SQL Server&#41;](xml-indexes-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="77d4c-155">For more information, see [XML Indexes &#40;SQL Server&#41;](xml-indexes-sql-server.md).</span></span>  
  
 <span data-ttu-id="77d4c-156">若下列情況成立，請將 `xml` 資料類型資料行建立在不同的資料表中：</span><span class="sxs-lookup"><span data-stu-id="77d4c-156">Create the `xml` data type column in a separate table if the following conditions are true:</span></span>  
  
-   <span data-ttu-id="77d4c-157">您想要在 `xml` 資料類型資料行上建立 XML 索引，但是主資料表的主索引鍵與其叢集索引鍵不同，或者主資料表沒有主索引鍵，或者主資料表是堆積 (沒有叢集索引鍵)。</span><span class="sxs-lookup"><span data-stu-id="77d4c-157">You want to build an XML index on the `xml` data type column, but the primary key of the main table is different from its clustering key, or the main table does not have a primary key, or the main table is a heap (no clustering key).</span></span> <span data-ttu-id="77d4c-158">如果主資料表已存在，就可能會有這種情形。</span><span class="sxs-lookup"><span data-stu-id="77d4c-158">This may be true if the main table already exists.</span></span>  
  
-   <span data-ttu-id="77d4c-159">您不想因為資料表中有 XML 資料行存在，而讓資料表掃描的速度慢下來。</span><span class="sxs-lookup"><span data-stu-id="77d4c-159">You do not want table scans to slow down because of the presence of the XML column in the table.</span></span> <span data-ttu-id="77d4c-160">無論是以同資料列或資料列外的方式儲存，都會用到空間。</span><span class="sxs-lookup"><span data-stu-id="77d4c-160">This uses space whether it is stored in-row or out-of-row.</span></span>  
  
  
