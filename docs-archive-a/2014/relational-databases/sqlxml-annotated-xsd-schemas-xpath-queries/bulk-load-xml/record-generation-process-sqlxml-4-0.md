---
title: 記錄產生進程 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XML Bulk Load [SQLXML], record generation process
- node scopes [SQLXML]
- record subsets [SQLXML]
- scope [SQLXML]
- key ordering rules [SQLXML]
- record generation process for bulk loads [SQLXML]
- entering node scope [SQLXML]
- bulk load [SQLXML], record generation process
- leaving node scope [SQLXML]
- schema mapping [SQLXML]
ms.assetid: d8885bbe-6f15-4fb9-9684-ca7883cfe9ac
author: rothja
ms.author: jroth
ms.openlocfilehash: 5734776864aecbda7adaf0b9b16180b5ebd55ce3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686875"
---
# <a name="record-generation-process-sqlxml-40"></a><span data-ttu-id="03a33-102">記錄產生處理序 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="03a33-102">Record Generation Process (SQLXML 4.0)</span></span>
  <span data-ttu-id="03a33-103">XML 大量載入會處理 XML 輸入資料，並在 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中為適當的資料表準備記錄。</span><span class="sxs-lookup"><span data-stu-id="03a33-103">XML Bulk Load processes the XML input data and prepares records for the appropriate tables in Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="03a33-104">XML 大量載入的邏輯會判斷在何時產生新記錄，要複製哪種子元素或屬性值到記錄欄位中，以及記錄何時會完成並準備傳送到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以供插入之用。</span><span class="sxs-lookup"><span data-stu-id="03a33-104">The logic in XML Bulk Load determines when to generate a new record, what child element or attribute values to copy into the fields of the record, and when the record is complete and ready to be sent to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for insertion.</span></span>  
  
 <span data-ttu-id="03a33-105">XML 大量載入不會將整個 XML 輸入資料載入到記憶體中，也不會在將資料傳送到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 之前產生完整的記錄集。</span><span class="sxs-lookup"><span data-stu-id="03a33-105">XML Bulk Load does not load the entire XML input data into memory, and does not produce complete record sets before sending data to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="03a33-106">這是因為 XML 輸入資料可以是大型文件，而且將整個文件載入到記憶體中的成本可能會很高。</span><span class="sxs-lookup"><span data-stu-id="03a33-106">This is because XML input data can be a large document and loading the entire document in memory can be expensive.</span></span> <span data-ttu-id="03a33-107">XML 大量載入會改為執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="03a33-107">Instead, XML Bulk Load does the following:</span></span>  
  
1.  <span data-ttu-id="03a33-108">分析對應結構描述和準備需要的執行計畫。</span><span class="sxs-lookup"><span data-stu-id="03a33-108">Analyzes the mapping schema and prepares the necessary execution plan.</span></span>  
  
2.  <span data-ttu-id="03a33-109">將執行計畫套用到輸入資料流中的資料。</span><span class="sxs-lookup"><span data-stu-id="03a33-109">Applies the execution plan to the data in the input stream.</span></span>  
  
 <span data-ttu-id="03a33-110">這個循序處理對於以特殊方式提供 XML 輸入資料而言很重要。</span><span class="sxs-lookup"><span data-stu-id="03a33-110">This sequential processing makes it important to provide the XML input data in a specific way.</span></span> <span data-ttu-id="03a33-111">您必須了解 XML 大量載入是如何分析對應結構描述，以及了解記錄產生處理序是如何發生的。</span><span class="sxs-lookup"><span data-stu-id="03a33-111">You must understand how XML Bulk Load analyzes the mapping schema and how the record generation process occurs.</span></span> <span data-ttu-id="03a33-112">有了這樣的了解，您就可以為 XML 大量載入提供會產生您想要結果的對應結構描述。</span><span class="sxs-lookup"><span data-stu-id="03a33-112">With this understanding, you can provide a mapping schema to XML Bulk Load that produces the results you want.</span></span>  
  
 <span data-ttu-id="03a33-113">XML 大量載入會處理一般對應結構描述註解，包括資料行和資料表對應 (藉由使用註解明確指定，或透過預設對應隱含指定)，並聯結關聯性。</span><span class="sxs-lookup"><span data-stu-id="03a33-113">XML Bulk Load handles common mapping schema annotations, including column and table mappings (specified explicitly by using annotations or implicitly through the default mapping), and join relationships.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="03a33-114">假設您熟悉註解式 XSD 或 XDR 對應結構描述。</span><span class="sxs-lookup"><span data-stu-id="03a33-114">It is assumed that you are familiar with annotated XSD or XDR mapping schemas.</span></span> <span data-ttu-id="03a33-115">如需有關架構的詳細資訊，請參閱[批註式 XSD 架構簡介 &#40;sqlxml 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)或[&#40;已在 sqlxml 4.0&#41;中取代的批註式 XDR 架構](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="03a33-115">For more information about schemas, see [Introduction to Annotated XSD Schemas &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md) or [Annotated XDR Schemas &#40;Deprecated in SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="03a33-116">了解記錄產生之前，需要先了解下列概念：</span><span class="sxs-lookup"><span data-stu-id="03a33-116">Understanding record generation requires understanding the following concepts:</span></span>  
  
-   <span data-ttu-id="03a33-117">節點範圍</span><span class="sxs-lookup"><span data-stu-id="03a33-117">Scope of a node</span></span>  
  
-   <span data-ttu-id="03a33-118">記錄產生規則</span><span class="sxs-lookup"><span data-stu-id="03a33-118">Record Generation Rule</span></span>  
  
-   <span data-ttu-id="03a33-119">記錄子集和索引鍵排列順序規則</span><span class="sxs-lookup"><span data-stu-id="03a33-119">Record subset and the Key Ordering Rule</span></span>  
  
-   <span data-ttu-id="03a33-120">記錄產生規則的例外狀況</span><span class="sxs-lookup"><span data-stu-id="03a33-120">Exceptions to the Record Generation Rule</span></span>  
  
## <a name="scope-of-a-node"></a><span data-ttu-id="03a33-121">節點範圍</span><span class="sxs-lookup"><span data-stu-id="03a33-121">Scope of a Node</span></span>  
 <span data-ttu-id="03a33-122">當 XML 大量載入在 XML 輸入資料流程中遇到時，節點 (XML 檔中的元素或屬性) 進入*範圍*。</span><span class="sxs-lookup"><span data-stu-id="03a33-122">A node (an element or an attribute) in an XML document enters *into scope* when XML Bulk Load encounters it in the XML input data stream.</span></span> <span data-ttu-id="03a33-123">如果是元素節點，元素的開始標記會將元素納入範圍中。</span><span class="sxs-lookup"><span data-stu-id="03a33-123">For an element node, the start tag of the element brings the element in scope.</span></span> <span data-ttu-id="03a33-124">如果是屬性節點，屬性名稱會將屬性納入範圍中。</span><span class="sxs-lookup"><span data-stu-id="03a33-124">For an attribute node, the attribute name brings the attribute in scope.</span></span>  
  
 <span data-ttu-id="03a33-125">當節點沒有更多資料時，就會離開範圍：可能是在結束標記 (在元素節點的狀況下)，或是在屬性值的結尾 (在屬性節點的狀況下)。</span><span class="sxs-lookup"><span data-stu-id="03a33-125">A node leaves scope when there is no more data for it: either at the end tag (in the case of an element node) or at the end of an attribute value (in the case of an attribute node).</span></span>  
  
## <a name="record-generation-rule"></a><span data-ttu-id="03a33-126">記錄產生規則</span><span class="sxs-lookup"><span data-stu-id="03a33-126">Record Generation Rule</span></span>  
 <span data-ttu-id="03a33-127">當節點 (元素或屬性) 進入範圍內時，記錄可能會從該節點產生。</span><span class="sxs-lookup"><span data-stu-id="03a33-127">When a node (element or attribute) enters into scope, there is a potential for generating a record from that node.</span></span> <span data-ttu-id="03a33-128">只要相關聯的節點在範圍內，記錄就會一直存在。</span><span class="sxs-lookup"><span data-stu-id="03a33-128">The record lives as long as the associated node is in scope.</span></span> <span data-ttu-id="03a33-129">當節點離開範圍時，XML 大量載入會視為產生的記錄是完整的 (具有資料)，並將它傳送到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 供插入之用。</span><span class="sxs-lookup"><span data-stu-id="03a33-129">When the node goes out of scope, XML Bulk Load considers the generated record complete (with data) and sends it to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] for insertion.</span></span>  
  
 <span data-ttu-id="03a33-130">例如，請考慮下列 XSD 結構描述片段：</span><span class="sxs-lookup"><span data-stu-id="03a33-130">For example, consider the following XSD schema fragment:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Customer" sql:relation="Customers" >  
   <xsd:complexType>  
     <xsd:attribute name="CustomerID" type="xsd:string" />  
     <xsd:attribute name="CompanyName" type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="03a33-131">架構會指定 **\<Customer>** 具有**CustomerID**和**公司名稱**屬性的元素。</span><span class="sxs-lookup"><span data-stu-id="03a33-131">The schema specifies a **\<Customer>** element with **CustomerID** and **CompanyName** attributes.</span></span> <span data-ttu-id="03a33-132">批註會將 `sql:relation` **\<Customer>** 元素對應至 Customers 資料表。</span><span class="sxs-lookup"><span data-stu-id="03a33-132">The `sql:relation` annotation maps the **\<Customer>** element to the Customers table.</span></span>  
  
 <span data-ttu-id="03a33-133">請考慮這個 XML 文件的片段：</span><span class="sxs-lookup"><span data-stu-id="03a33-133">Consider this fragment of an XML document:</span></span>  
  
```  
<Customer CustomerID="1" CompanyName="xyz" />  
<Customer CustomerID="2" CompanyName="abc" />  
...  
```  
  
 <span data-ttu-id="03a33-134">當 XML 大量載入是由結構描述提供，而該結構描述在前面段落和 XML 資料中是描述為輸入時，則 XML 大量載入會在來源資料中處理節點 (元素和屬性)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="03a33-134">When XML Bulk Load is provided with the schema described in the preceding paragraphs and XML data as input, it processes the nodes (elements and attributes) in the source data as follows:</span></span>  
  
-   <span data-ttu-id="03a33-135">第一個元素的開始標記 **\<Customer>** 會將該元素帶入範圍中。</span><span class="sxs-lookup"><span data-stu-id="03a33-135">The start tag of the first **\<Customer>** element brings that element in scope.</span></span> <span data-ttu-id="03a33-136">這個節點會對應到「客戶」資料表。</span><span class="sxs-lookup"><span data-stu-id="03a33-136">This node maps to the Customers table.</span></span> <span data-ttu-id="03a33-137">因此，XML 大量載入會產生「客戶」資料表的記錄。</span><span class="sxs-lookup"><span data-stu-id="03a33-137">Therefore, XML Bulk Load generates a record for the Customers table.</span></span>  
  
-   <span data-ttu-id="03a33-138">在架構中，元素的所有屬性都會 **\<Customer>** 對應到 Customers 資料表的資料行。</span><span class="sxs-lookup"><span data-stu-id="03a33-138">In the schema, all attributes of the **\<Customer>** element map to columns of the Customers table.</span></span> <span data-ttu-id="03a33-139">當這些屬性進入範圍內時，XML 大量載入會將屬性值複製到已由父範圍產生的客戶記錄中。</span><span class="sxs-lookup"><span data-stu-id="03a33-139">As these attributes enter into scope, XML Bulk Load copies their values to the customer record that is already generated by the parent scope.</span></span>  
  
-   <span data-ttu-id="03a33-140">當 XML 大量載入到達元素的結束標記時 **\<Customer>** ，元素會超出範圍。</span><span class="sxs-lookup"><span data-stu-id="03a33-140">When XML Bulk Load reaches the end tag for the **\<Customer>** element, the element goes out of scope.</span></span> <span data-ttu-id="03a33-141">這會造成 XML 大量載入將記錄視為已完成並將之傳送到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="03a33-141">This causes XML Bulk Load to consider the record complete and send it to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="03a33-142">XML 大量載入會針對每個後續元素，遵循此程式 **\<Customer>** 。</span><span class="sxs-lookup"><span data-stu-id="03a33-142">XML Bulk Load follows this process for each subsequent **\<Customer>** element.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="03a33-143">在這個模型中，因為在到達結束標記時 (或節點離開範圍時) 會插入記錄，所以您必須定義與在節點範圍內之記錄相關聯的所有資料。</span><span class="sxs-lookup"><span data-stu-id="03a33-143">In this model, because a record is inserted when the end tag is reached (or the node is out of scope), you must define all of the data that is associated with the record within the scope of the node.</span></span>  
  
## <a name="record-subset-and-the-key-ordering-rule"></a><span data-ttu-id="03a33-144">記錄子集和索引鍵排列順序規則</span><span class="sxs-lookup"><span data-stu-id="03a33-144">Record Subset and the Key Ordering Rule</span></span>  
 <span data-ttu-id="03a33-145">當您指定使用 `<sql:relationship>` 的對應結構描述時，子集詞彙會參考在關聯性外部端上產生的記錄。</span><span class="sxs-lookup"><span data-stu-id="03a33-145">When you specify a mapping schema that uses `<sql:relationship>`, the subset term refers to the set of records that is generated on the foreign side of the relationship.</span></span> <span data-ttu-id="03a33-146">在下列範例中，CustOrder 記錄是在外部端 `<sql:relationship>`。</span><span class="sxs-lookup"><span data-stu-id="03a33-146">In the following example, the CustOrder records are on the foreign side, `<sql:relationship>`.</span></span>  
  
 <span data-ttu-id="03a33-147">例如，假設資料庫包含下列資料表：</span><span class="sxs-lookup"><span data-stu-id="03a33-147">For example, suppose a database contains the following tables:</span></span>  
  
-   <span data-ttu-id="03a33-148">Cust (CustomerID、CompanyName、City)</span><span class="sxs-lookup"><span data-stu-id="03a33-148">Cust (CustomerID, CompanyName, City)</span></span>  
  
-   <span data-ttu-id="03a33-149">CustOrder (CustomerID、OrderID)</span><span class="sxs-lookup"><span data-stu-id="03a33-149">CustOrder (CustomerID, OrderID)</span></span>  
  
 <span data-ttu-id="03a33-150">在 CustOrder 資料表中的 CustomerID 是外部索引鍵，會參考在 Cust 資料表中的 CustomerID 主要索引鍵。</span><span class="sxs-lookup"><span data-stu-id="03a33-150">The CustomerID in the CustOrder table is a foreign key that refers to the CustomerID primary key in the Cust table.</span></span>  
  
 <span data-ttu-id="03a33-151">現在，請將 XML 檢視視為是在下列註解式 XSD 結構描述中所指定。</span><span class="sxs-lookup"><span data-stu-id="03a33-151">Now, consider the XML view as specified in the following annotated XSD schema.</span></span> <span data-ttu-id="03a33-152">這個結構描述使用 `<sql:relationship>` 指定 Cust 和 CustOrder 資料表之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="03a33-152">This schema uses `<sql:relationship>` to specify the relationship between the Cust and CustOrder tables.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustCustOrder"  
          parent="Cust"  
          parent-key="CustomerID"  
          child="CustOrder"  
          child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customers" sql:relation="Cust" >  
   <xsd:complexType>  
     <xsd:sequence>  
       <xsd:element name="CustomerID"  type="xsd:integer" />  
       <xsd:element name="CompanyName" type="xsd:string" />  
       <xsd:element name="City"        type="xsd:string" />  
       <xsd:element name="Order"   
                          sql:relation="CustOrder"  
                          sql:relationship="CustCustOrder" >  
         <xsd:complexType>  
          <xsd:attribute name="OrderID" type="xsd:integer" />  
         </xsd:complexType>  
       </xsd:element>  
     </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="03a33-153">範例 XML 資料和建立工作範例的步驟如下。</span><span class="sxs-lookup"><span data-stu-id="03a33-153">The sample XML data and the steps to create a working sample are given below.</span></span>  
  
-   <span data-ttu-id="03a33-154">當 **\<Customer>** xml 資料檔案中的元素節點進入範圍內時，Xml 大量載入會產生「加入」資料表的記錄。</span><span class="sxs-lookup"><span data-stu-id="03a33-154">When a **\<Customer>** element node in the XML data file enters into scope, XML Bulk Load generates a record for the Cust table.</span></span> <span data-ttu-id="03a33-155">然後，XML 大量載入會從、和子專案中，將必要的資料行值複製 (CustomerID、公司名稱和 City) **\<CustomerID>** ，因為這些專案會在 **\<CompanyName>** 範圍中 **\<City>** 輸入這些元素。</span><span class="sxs-lookup"><span data-stu-id="03a33-155">XML Bulk Load then copies the necessary column values (CustomerID, CompanyName, and City) from the **\<CustomerID>**, **\<CompanyName>**, and the **\<City>** child elements as these elements enter into scope.</span></span>  
  
-   <span data-ttu-id="03a33-156">當 **\<Order>** 元素節點進入範圍內時，XML 大量載入會產生 CustOrder 資料表的記錄。</span><span class="sxs-lookup"><span data-stu-id="03a33-156">When an **\<Order>** element node enters into scope, XML Bulk Load generates a record for the CustOrder table.</span></span> <span data-ttu-id="03a33-157">XML 大量載入會將 [**訂單**] 屬性的值複製到此記錄。</span><span class="sxs-lookup"><span data-stu-id="03a33-157">XML Bulk Load copies the value of the **OrderID** attribute to this record.</span></span> <span data-ttu-id="03a33-158">CustomerID 資料行所需的值是從元素的 **\<CustomerID>** 子項目取得 **\<Customer>** 。</span><span class="sxs-lookup"><span data-stu-id="03a33-158">The value required for the CustomerID column is obtained from the **\<CustomerID>** child element of the **\<Customer>** element.</span></span> <span data-ttu-id="03a33-159">除非在元素中指定 Customerid 屬性，否則 XML 大量載入會使用中指定的資訊 `<sql:relationship>` 來取得此記錄的**CustomerID** customerid 外鍵值 **\<Order>** 。</span><span class="sxs-lookup"><span data-stu-id="03a33-159">XML Bulk Load uses the information that is specified in `<sql:relationship>` to obtain the CustomerID foreign key value for this record, unless the **CustomerID** attribute was specified in the **\<Order>** element.</span></span> <span data-ttu-id="03a33-160">一般規則是，如果子元素明確指定外部索引鍵屬性的值，則 XML 大量載入會使用該值，而且不會藉由使用指定的 `<sql:relationship>` 從父元素取得值。</span><span class="sxs-lookup"><span data-stu-id="03a33-160">The general rule is that if the child element explicitly specifies a value for the foreign key attribute, XML Bulk Load uses that value and does not obtain the value from the parent element by using the specified `<sql:relationship>`.</span></span> <span data-ttu-id="03a33-161">當此 **\<Order>** 元素節點超出範圍時，XML 大量載入會將記錄傳送至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，然後 **\<Order>** 以相同的方式處理所有後續的元素節點。</span><span class="sxs-lookup"><span data-stu-id="03a33-161">As this **\<Order>** element node goes out of scope, XML Bulk Load sends the record to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and then processes all the subsequent **\<Order>** element nodes in the same manner.</span></span>  
  
-   <span data-ttu-id="03a33-162">最後， **\<Customer>** 元素節點超出範圍。</span><span class="sxs-lookup"><span data-stu-id="03a33-162">Finally, the **\<Customer>** element node goes out of scope.</span></span> <span data-ttu-id="03a33-163">這時候，XML 大量載入會傳送客戶記錄到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="03a33-163">At that time, XML Bulk Load sends the customer record to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="03a33-164">對於 XML 資料流中的所有後續客戶，XML 大量載入都會遵循這個處理序。</span><span class="sxs-lookup"><span data-stu-id="03a33-164">XML Bulk Load follows this process for all the subsequent customers in the XML data stream.</span></span>  
  
 <span data-ttu-id="03a33-165">以下是有關對應結構描述的兩個觀察：</span><span class="sxs-lookup"><span data-stu-id="03a33-165">Here are two observations about the mapping schema:</span></span>  
  
-   <span data-ttu-id="03a33-166">當架構符合「內含專案」規則 (例如，與客戶相關聯的所有資料和訂單會定義在相關聯的和元素節點的範圍內 **\<Customer>** **\<Order>**) ，大量載入就會成功。</span><span class="sxs-lookup"><span data-stu-id="03a33-166">When the schema satisfies the "containment" rule (for example, all data that is associated with the customer and the order is defined within the scope of the associated **\<Customer>** and **\<Order>** element nodes), the bulk load succeeds.</span></span>  
  
-   <span data-ttu-id="03a33-167">在描述 **\<Customer>** 元素時，其子專案是以適當的順序指定。</span><span class="sxs-lookup"><span data-stu-id="03a33-167">In describing the **\<Customer>** element, its child elements are specified in the appropriate order.</span></span> <span data-ttu-id="03a33-168">在此情況下， **\<CustomerID>** 子項目會在子專案之前指定 **\<Order>** 。</span><span class="sxs-lookup"><span data-stu-id="03a33-168">In this case, the **\<CustomerID>** child element is specified before the **\<Order>** child element.</span></span> <span data-ttu-id="03a33-169">這表示在輸入 XML 資料檔案中， **\<CustomerID>** 當 **\<Order>** 元素進入範圍內時，元素值會當做外鍵值使用。</span><span class="sxs-lookup"><span data-stu-id="03a33-169">This means that in the input XML data file, the **\<CustomerID>** element value is available as the foreign key value when the **\<Order>** element enters into scope.</span></span> <span data-ttu-id="03a33-170">根據「關鍵識別碼順序規則」，要先指定索引鍵屬性。</span><span class="sxs-lookup"><span data-stu-id="03a33-170">The key attributes are specified first; this is the "Key Ordering Rule."</span></span>  
  
     <span data-ttu-id="03a33-171">如果您指定 **\<CustomerID>** 子專案之後的子項目 **\<Order>** ，當 **\<Order>** 元素進入範圍內時，就無法使用此值。</span><span class="sxs-lookup"><span data-stu-id="03a33-171">If you specify the **\<CustomerID>** child element after the **\<Order>** child element, the value is not available when the **\<Order>** element enters into scope.</span></span> <span data-ttu-id="03a33-172">當結束標記之後，就會將 **\</Order>** CustOrder 資料表的記錄視為 complete，並插入 CustOrder 資料表中，其中包含 CustomerID 資料行的 Null 值，這不是所需的結果。</span><span class="sxs-lookup"><span data-stu-id="03a33-172">When the **\</Order>** end tag is then read, the record for CustOrder table is considered complete and is inserted in the CustOrder table with a NULL value for the CustomerID column, which is not the desired result.</span></span>  
  
#### <a name="to-create-a-working-sample"></a><span data-ttu-id="03a33-173">建立工作範例</span><span class="sxs-lookup"><span data-stu-id="03a33-173">To create a working sample</span></span>  
  
1.  <span data-ttu-id="03a33-174">將這個範例所提供的結構描述儲存為 SampleSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="03a33-174">Save the schema that is provided in this example as SampleSchema.xml.</span></span>  
  
2.  <span data-ttu-id="03a33-175">建立這些資料表：</span><span class="sxs-lookup"><span data-stu-id="03a33-175">Create these tables:</span></span>  
  
    ```  
    CREATE TABLE Cust (  
                  CustomerID     int         PRIMARY KEY,  
                  CompanyName    varchar(20) NOT NULL,  
                  City           varchar(20) DEFAULT 'Seattle')  
    GO  
    CREATE TABLE CustOrder (  
                 OrderID        int         PRIMARY KEY,  
                 CustomerID     int         FOREIGN KEY REFERENCES                                          Cust(CustomerID))  
    GO  
    ```  
  
3.  <span data-ttu-id="03a33-176">儲存下列範例 XML 輸入資料為 SampleXMLData.xml：</span><span class="sxs-lookup"><span data-stu-id="03a33-176">Save the following sample XML input data as SampleXMLData.xml:</span></span>  
  
    ```  
    <ROOT>  
      <Customers>  
        <CustomerID>1111</CustomerID>  
        <CompanyName>Hanari Carnes</CompanyName>  
        <City>NY</City>   
        <Order OrderID="1" />  
        <Order OrderID="2" />  
      </Customers>  
  
      <Customers>  
        <CustomerID>1112</CustomerID>  
        <CompanyName>Toms Spezialitten</CompanyName>  
        <City>LA</City>  
        <Order OrderID="3" />  
      </Customers>  
      <Customers>  
        <CustomerID>1113</CustomerID>  
        <CompanyName>Victuailles en stock</CompanyName>  
        <Order OrderID="4" />  
    </Customers>  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="03a33-177">若要執行 XML 大量載入，請儲存和執行下列 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript) 範例 (BulkLoad.vbs)：</span><span class="sxs-lookup"><span data-stu-id="03a33-177">To execute XML Bulk Load, save and execute the following [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript) example (BulkLoad.vbs):</span></span>  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints = True  
    objBL.Execute "c:\SampleSchema.xml", "c:\SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
## <a name="exceptions-to-the-record-generation-rule"></a><span data-ttu-id="03a33-178">記錄產生規則的例外狀況</span><span class="sxs-lookup"><span data-stu-id="03a33-178">Exceptions to the Record Generation Rule</span></span>  
 <span data-ttu-id="03a33-179">當 XML 大量載入進入範圍內時，不會產生節點記錄 (如果該節點是 IDREF 或 IDREFS 類型的話)。</span><span class="sxs-lookup"><span data-stu-id="03a33-179">XML Bulk Load does not generate a record for a node when it enters into scope if that node is either an IDREF or IDREFS type.</span></span> <span data-ttu-id="03a33-180">您必須確定完整的記錄描述會出現在結構描述中的某個地方。</span><span class="sxs-lookup"><span data-stu-id="03a33-180">You must make sure that a complete description of the record occurs at some place in the schema.</span></span> <span data-ttu-id="03a33-181">`dt:type="nmtokens"` 註解會被忽略，就像 IDREFS 類型也被忽略一樣。</span><span class="sxs-lookup"><span data-stu-id="03a33-181">The `dt:type="nmtokens"` annotations are ignored just as the IDREFS type is ignored.</span></span>  
  
 <span data-ttu-id="03a33-182">例如，請考慮下列描述和元素的 XSD **\<Customer>** 架構 **\<Order>** 。</span><span class="sxs-lookup"><span data-stu-id="03a33-182">For example, consider the following XSD schema that describes **\<Customer>** and **\<Order>** elements.</span></span> <span data-ttu-id="03a33-183">**\<Customer>** 元素包含 IDREFS 類型的**OrderList**屬性。</span><span class="sxs-lookup"><span data-stu-id="03a33-183">The **\<Customer>** element includes an **OrderList** attribute of the IDREFS type.</span></span> <span data-ttu-id="03a33-184">`<sql:relationship>` 標記會在客戶和訂單清單之間指定一對多關聯性。</span><span class="sxs-lookup"><span data-stu-id="03a33-184">The `<sql:relationship>` tag specifies the one-to-many relationship between the customer and list of orders.</span></span>  
  
 <span data-ttu-id="03a33-185">這是結構描述：</span><span class="sxs-lookup"><span data-stu-id="03a33-185">This is the schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustCustOrder"  
                 parent="Cust"  
                 parent-key="CustomerID"  
                 child="CustOrder"  
                 child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customers" sql:relation="Cust" >  
   <xsd:complexType>  
    <xsd:attribute name="CustomerID" type="xsd:integer" />  
    <xsd:attribute name="CompanyName" type="xsd:string" />  
    <xsd:attribute name="City" type="xsd:string" />  
    <xsd:attribute name="OrderList"   
                       type="xsd:IDREFS"   
                       sql:relation="CustOrder"   
                       sql:field="OrderID"  
                       sql:relationship="CustCustOrder" >  
    </xsd:attribute>  
  </xsd:complexType>  
 </xsd:element>  
  
  <xsd:element name="Order" sql:relation="CustOrder" >  
   <xsd:complexType>  
    <xsd:attribute name="OrderID" type="xsd:string" />  
    <xsd:attribute name="CustomerID" type="xsd:integer" />  
    <xsd:attribute name="OrderDate" type="xsd:date" />  
  </xsd:complexType>  
 </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="03a33-186">由於大量載入會忽略 IDREFS 類型的節點，因此當 [ **OrderList**屬性] 節點進入範圍內時，不會產生任何記錄。</span><span class="sxs-lookup"><span data-stu-id="03a33-186">Because Bulk Load ignores the nodes of IDREFS type, there is no record generation when the **OrderList** attribute node enters into scope.</span></span> <span data-ttu-id="03a33-187">因此，如果您希望訂單記錄加入「訂單」資料表中，您必須描述那些在結構描述某處的訂單。</span><span class="sxs-lookup"><span data-stu-id="03a33-187">Therefore, if you want the order records added to the Orders table, you must describe those orders somewhere in the schema.</span></span> <span data-ttu-id="03a33-188">在此架構中，指定 **\<Order>** 元素可確保 XML 大量載入會將訂單記錄新增至 Orders 資料表。</span><span class="sxs-lookup"><span data-stu-id="03a33-188">In this schema, specifying the **\<Order>** element ensures that XML Bulk Load adds the order records to the Orders table.</span></span> <span data-ttu-id="03a33-189">**\<Order>** 元素會描述填滿 CustOrder 資料表記錄所需的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="03a33-189">The **\<Order>** element describes all the attributes that are required to fill the record for the CustOrder table.</span></span>  
  
 <span data-ttu-id="03a33-190">您必須確定元素中的**CustomerID**和「**訂單**」值 **\<Customer>** 符合專案中的值 **\<Order>** 。</span><span class="sxs-lookup"><span data-stu-id="03a33-190">You must ensure that the **CustomerID** and **OrderID** values in the **\<Customer>** element match the values in the **\<Order>** element.</span></span> <span data-ttu-id="03a33-191">您必須負責維護參考完整性。</span><span class="sxs-lookup"><span data-stu-id="03a33-191">You are responsible for maintaining referential integrity.</span></span>  
  
#### <a name="to-test-a-working-sample"></a><span data-ttu-id="03a33-192">測試工作範例</span><span class="sxs-lookup"><span data-stu-id="03a33-192">To test a working sample</span></span>  
  
1.  <span data-ttu-id="03a33-193">建立這些資料表：</span><span class="sxs-lookup"><span data-stu-id="03a33-193">Create these tables:</span></span>  
  
    ```  
    CREATE TABLE Cust (  
                  CustomerID     int          PRIMARY KEY,  
                  CompanyName    varchar(20)  NOT NULL,  
                  City           varchar(20)  DEFAULT 'Seattle')  
    GO  
    CREATE TABLE CustOrder (  
                  OrderID        varchar(10) PRIMARY KEY,  
                  CustomerID     int         FOREIGN KEY REFERENCES                                          Cust(CustomerID),  
                  OrderDate      datetime DEFAULT '2000-01-01')  
    GO  
    ```  
  
2.  <span data-ttu-id="03a33-194">將這個範例所提供的對應結構描述儲存為 SampleSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="03a33-194">Save the mapping schema provided in this example as SampleSchema.xml.</span></span>  
  
3.  <span data-ttu-id="03a33-195">將下列 XML 資料範例儲存為 SampleXMLData.xml：</span><span class="sxs-lookup"><span data-stu-id="03a33-195">Save the following sample XML data as SampleXMLData.xml:</span></span>  
  
    ```  
    <ROOT>  
      <Customers CustomerID="1111" CompanyName="Sean Chai" City="NY"  
                 OrderList="Ord1 Ord2" />  
      <Customers CustomerID="1112" CompanyName="Dont Know" City="LA"  
                 OrderList="Ord3 Ord4" />  
      <Order OrderID="Ord1" CustomerID="1111" OrderDate="1999-01-01" />  
      <Order OrderID="Ord2" CustomerID="1111" OrderDate="1999-02-01" />  
      <Order OrderID="Ord3" CustomerID="1112" OrderDate="1999-03-01" />  
      <Order OrderID="Ord4" CustomerID="1112" OrderDate="1999-04-01" />  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="03a33-196">若要執行 XML 大量載入，請儲存和執行這個 VBScript 範例 (SampleVB.vbs)：</span><span class="sxs-lookup"><span data-stu-id="03a33-196">To execute XML Bulk Load, save and execute this VBScript example (SampleVB.vbs):</span></span>  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints=True  
    objBL.Execute "c:\SampleSchema.xml", "c:\SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
  
