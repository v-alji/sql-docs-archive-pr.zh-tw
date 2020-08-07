---
title: 使用 sql：最大深度來指定遞迴關聯性的深度 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- max-depth annotation
- XPath queries [SQLXML], recursive relationships
- depth in recursive relationships [SQLXML]
- annotated XSD schemas, recursive relationships
- relationships [SQLXML], recursive relationships
- self joins
- recursive relationships [SQLXML]
- recursion [SQLXML]
- sql:max-depth
- recursive joins [SQLXML]
ms.assetid: 0ffdd57d-dc30-44d9-a8a0-f21cadedb327
author: rothja
ms.author: jroth
ms.openlocfilehash: 5e3ccb2de9c7b2ac8f8702b52aa990d755620e46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597046"
---
# <a name="specifying-depth-in-recursive-relationships-by-using-sqlmax-depth"></a><span data-ttu-id="ebb07-102">使用 sql:max-depth 來指定遞迴關聯性的深度</span><span class="sxs-lookup"><span data-stu-id="ebb07-102">Specifying Depth in Recursive Relationships by Using sql:max-depth</span></span>
  <span data-ttu-id="ebb07-103">在關聯式資料庫中，當某份資料表與本身具有關聯性時，它就稱為遞迴關聯性。</span><span class="sxs-lookup"><span data-stu-id="ebb07-103">In relational databases, when a table is involved in a relationship with itself, it is called a recursive relationship.</span></span> <span data-ttu-id="ebb07-104">例如，在監督者-被監督者的關聯性中，儲存員工記錄的資料表會與本身具有關聯。</span><span class="sxs-lookup"><span data-stu-id="ebb07-104">For example, in a supervisor-supervisee relationship, a table storing employee records is involved in a relationship with itself.</span></span> <span data-ttu-id="ebb07-105">在此情況下，員工資料表在關聯性的一端扮演監督者的角色，而同一份資料表在另一端則扮演被監督者的角色。</span><span class="sxs-lookup"><span data-stu-id="ebb07-105">In this case, the employees table plays a role of supervisor on one side of the relationship, and the same table plays a role of supervisee on the other side.</span></span>  
  
 <span data-ttu-id="ebb07-106">對應結構描述可能包含遞迴關聯性，其中某個元素及其上階屬於相同的類型。</span><span class="sxs-lookup"><span data-stu-id="ebb07-106">Mapping schemas can include recursive relationships where an element and its ancestor are of the same type.</span></span>  
  
## <a name="example-a"></a><span data-ttu-id="ebb07-107">範例 A</span><span class="sxs-lookup"><span data-stu-id="ebb07-107">Example A</span></span>  
 <span data-ttu-id="ebb07-108">請考慮下列資料表：</span><span class="sxs-lookup"><span data-stu-id="ebb07-108">Consider the following table:</span></span>  
  
```  
Emp (EmployeeID, FirstName, LastName, ReportsTo)  
```  
  
 <span data-ttu-id="ebb07-109">在這份資料表中，ReportsTo 資料行會儲存經理的員工識別碼。</span><span class="sxs-lookup"><span data-stu-id="ebb07-109">In this table, the ReportsTo column stores the employee ID of the manager.</span></span>  
  
 <span data-ttu-id="ebb07-110">假設您想要產生一種員工的 XML 階層，其中經理員工位於階層頂端，而且向經理報告的員工顯示在對應的階層中，如下列範例 XML 片段所示。</span><span class="sxs-lookup"><span data-stu-id="ebb07-110">Assume that you want to generate an XML hierarchy of employees in which the manager employee is at the top of the hierarchy, and in which the employees that report to that manager appear in the corresponding hierarchy as shown in the following sample XML fragment.</span></span> <span data-ttu-id="ebb07-111">此片段顯示的內容是 employee 1 的*遞迴樹狀結構*。</span><span class="sxs-lookup"><span data-stu-id="ebb07-111">What this fragment shows is the *recursive tree* for employee 1.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <Emp FirstName="Nancy" EmployeeID="1" LastName="Devolio">  
     <Emp FirstName="Andrew" EmployeeID="2" LastName="Fuller" />   
     <Emp FirstName="Janet" EmployeeID="3" LastName="Leverling">  
        <Emp FirstName="Margaret" EmployeeID="4" LastName="Peacock">  
          <Emp FirstName="Steven" EmployeeID="5" LastName="Devolio">  
...  
...  
</root>  
```  
  
 <span data-ttu-id="ebb07-112">在這個片段中，員工 5 會向員工 4 報告、員工 4 會向員工 3 報告，而員工 3 和 2 會向員工 1 報告。</span><span class="sxs-lookup"><span data-stu-id="ebb07-112">In this fragment, employee 5 reports to employee 4, employee 4 reports to employee 3, and employees 3 and 2 reports to employee 1.</span></span>  
  
 <span data-ttu-id="ebb07-113">若要產生這種結果，您可以使用下列 XSD 結構描述並針對它指定 XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="ebb07-113">To produce this result, you can use the following XSD schema and specify an XPath query against it.</span></span> <span data-ttu-id="ebb07-114">架構會描述 **\<Emp>** EmployeeType 類型的元素，其中包含 **\<Emp>** 相同類型的子項目 EmployeeType。</span><span class="sxs-lookup"><span data-stu-id="ebb07-114">The schema describes an **\<Emp>** element of type EmployeeType, consisting of an **\<Emp>** child element of the same type, EmployeeType.</span></span> <span data-ttu-id="ebb07-115">這就是遞迴關聯性 (元素及其上階屬於相同的類型)。</span><span class="sxs-lookup"><span data-stu-id="ebb07-115">This is a recursive relationship (the element and its ancestor are of the same type).</span></span> <span data-ttu-id="ebb07-116">此外，架構會使用 **\<sql:relationship>** 來描述監督員和被監督者之間的父子式關聯性。</span><span class="sxs-lookup"><span data-stu-id="ebb07-116">In addition, the schema uses a **\<sql:relationship>** to describe the parent-child relationship between the supervisor and supervisee.</span></span> <span data-ttu-id="ebb07-117">請注意，在此中 **\<sql:relationship>** ，Emp 同時是父系和子資料工作表。</span><span class="sxs-lookup"><span data-stu-id="ebb07-117">Note that in this **\<sql:relationship>**, Emp is both the parent and the child table.</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:appinfo>  
      <sql:relationship name="SupervisorSupervisee"  
                                  parent="Emp"  
                                  parent-key="EmployeeID"  
                                  child="Emp"  
                                  child-key="ReportsTo" />  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="Emp" type="EmployeeType"   
                          sql:relation="Emp"   
                          sql:key-fields="EmployeeID"   
                          sql:limit-field="ReportsTo" />  
  <xsd:complexType name="EmployeeType">  
    <xsd:sequence>  
      <xsd:element name="Emp" type="EmployeeType"   
                              sql:relation="Emp"   
                              sql:key-fields="EmployeeID"  
                              sql:relationship="SupervisorSupervisee"  
                              sql:max-depth="6" />  
    </xsd:sequence>   
    <xsd:attribute name="EmployeeID" type="xsd:ID" />  
    <xsd:attribute name="FirstName" type="xsd:string"/>  
    <xsd:attribute name="LastName" type="xsd:string"/>  
  </xsd:complexType>  
</xsd:schema>  
```  
  
 <span data-ttu-id="ebb07-118">由於此關聯性是遞迴的，所以您需要某種方式來指定結構描述中的遞迴深度。</span><span class="sxs-lookup"><span data-stu-id="ebb07-118">Because the relationship is recursive, you need some way to specify the depth of recursion in the schema.</span></span> <span data-ttu-id="ebb07-119">否則，結果將是無止盡的遞迴 (員工向員工報告，依此類推)。</span><span class="sxs-lookup"><span data-stu-id="ebb07-119">Otherwise, the result will be an endless recursion (employee reporting to employee reporting to employee, and so on).</span></span> <span data-ttu-id="ebb07-120">`sql:max-depth` 註解可讓您指定遞迴的深度。</span><span class="sxs-lookup"><span data-stu-id="ebb07-120">The `sql:max-depth` annotation allows you to specify how deep in the recursion to go.</span></span> <span data-ttu-id="ebb07-121">在這個範例中，若要指定 `sql:max-depth` 的值，您必須知道公司中管理階層的深度。</span><span class="sxs-lookup"><span data-stu-id="ebb07-121">In this particular example, to specify a value for `sql:max-depth`, you must know how deep the management hierarchy goes in the company.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ebb07-122">此結構描述會指定 `sql:limit-field` 註解，但是不會指定 `sql:limit-value` 註解。</span><span class="sxs-lookup"><span data-stu-id="ebb07-122">The schema specifies the `sql:limit-field` annotation, but does not specify the `sql:limit-value` annotation.</span></span> <span data-ttu-id="ebb07-123">這會將產生之階層中的最上層節點限制為不向任何人報告的員工 </span><span class="sxs-lookup"><span data-stu-id="ebb07-123">This limits the top node in the resulting hierarchy to only those employees who do not report to anyone.</span></span> <span data-ttu-id="ebb07-124"> (的上級是 Null。 ) 指定 `sql:limit-field` ，但不指定 `sql:limit-value` (預設為 null) 注釋完成這種情況。</span><span class="sxs-lookup"><span data-stu-id="ebb07-124">(ReportsTo is NULL.) Specifying `sql:limit-field` and not specifying `sql:limit-value` (which defaults to NULL) annotation accomplishes this.</span></span> <span data-ttu-id="ebb07-125">如果您想讓產生的 XML 包含每個可能的報告樹狀結構 (資料表中每位員工的報告樹狀結構)，請從結構描述中移除 `sql:limit-field` 註解。</span><span class="sxs-lookup"><span data-stu-id="ebb07-125">If you want the resulting XML to include every possible reporting tree (the reporting tree for every employee in the table), remove the `sql:limit-field` annotation from the schema.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ebb07-126">下列程序會使用 tempdb 資料庫。</span><span class="sxs-lookup"><span data-stu-id="ebb07-126">The following procedure uses the tempdb database.</span></span>  
  
#### <a name="to-test-a-sample-xpath-query-against-the-schema"></a><span data-ttu-id="ebb07-127">針對結構描述測試範例 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="ebb07-127">To test a sample XPath query against the schema</span></span>  
  
1.  <span data-ttu-id="ebb07-128">在虛擬根目錄指向的 tempdb 資料庫中建立名為 Emp 的範例資料表。</span><span class="sxs-lookup"><span data-stu-id="ebb07-128">Create a sample table called Emp in the tempdb database to which the virtual root points.</span></span>  
  
    ```  
    USE tempdb  
    CREATE TABLE Emp (  
           EmployeeID int primary key,   
           FirstName  varchar(20),   
           LastName   varchar(20),   
           ReportsTo int)  
    ```  
  
2.  <span data-ttu-id="ebb07-129">加入這個範例資料：</span><span class="sxs-lookup"><span data-stu-id="ebb07-129">Add this sample data:</span></span>  
  
    ```  
    INSERT INTO Emp values (1, 'Nancy', 'Devolio',NULL)  
    INSERT INTO Emp values (2, 'Andrew', 'Fuller',1)  
    INSERT INTO Emp values (3, 'Janet', 'Leverling',1)  
    INSERT INTO Emp values (4, 'Margaret', 'Peacock',3)  
    INSERT INTO Emp values (5, 'Steven', 'Devolio',4)  
    INSERT INTO Emp values (6, 'Nancy', 'Buchanan',5)  
    INSERT INTO Emp values (7, 'Michael', 'Suyama',6)  
    ```  
  
3.  <span data-ttu-id="ebb07-130">複製上述的結構描述程式碼，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="ebb07-130">Copy the schema code above and paste it into a text file.</span></span> <span data-ttu-id="ebb07-131">將檔案儲存為 maxDepth.xml。</span><span class="sxs-lookup"><span data-stu-id="ebb07-131">Save the file as maxDepth.xml.</span></span>  
  
4.  <span data-ttu-id="ebb07-132">複製下列範本，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="ebb07-132">Copy the following template and paste it into a text file.</span></span> <span data-ttu-id="ebb07-133">將檔案儲存為 maxDepthT.xml，並放在與儲存 maxDepth.xml 相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="ebb07-133">Save the file as maxDepthT.xml in the same directory where you saved maxDepth.xml.</span></span> <span data-ttu-id="ebb07-134">此範本中的查詢會傳回 Emp 資料表中的所有員工。</span><span class="sxs-lookup"><span data-stu-id="ebb07-134">The query in the template returns all the employees in the Emp table.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="maxDepth.xml">  
        /Emp  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="ebb07-135">針對對應結構描述 (maxDepth.xml) 指定的目錄路徑，相對於儲存範本的目錄。</span><span class="sxs-lookup"><span data-stu-id="ebb07-135">The directory path specified for the mapping schema (maxDepth.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="ebb07-136">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="ebb07-136">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\maxDepth.xml"  
    ```  
  
5.  <span data-ttu-id="ebb07-137">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="ebb07-137">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span> <span data-ttu-id="ebb07-138">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="ebb07-138">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="ebb07-139">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="ebb07-139">This is the result:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <Emp FirstName="Nancy" EmployeeID="1" LastName="Devolio">  
  <Emp FirstName="Andrew" EmployeeID="2" LastName="Fuller" />   
    <Emp FirstName="Janet" EmployeeID="3" LastName="Leverling">  
      <Emp FirstName="Margaret" EmployeeID="4" LastName="Peacock">  
        <Emp FirstName="Steven" EmployeeID="5" LastName="Devolio">  
          <Emp FirstName="Nancy" EmployeeID="6" LastName="Buchanan">  
            <Emp FirstName="Michael" EmployeeID="7" LastName="Suyama" />   
          </Emp>  
        </Emp>  
      </Emp>  
    </Emp>  
  </Emp>  
</root>  
```  
  
> [!NOTE]  
>  <span data-ttu-id="ebb07-140">若要在結果中產生不同的階層深度，請在結構描述中變更 `sql:max-depth` 註解的值，然後在每次變更之後再次執行此範本。</span><span class="sxs-lookup"><span data-stu-id="ebb07-140">To produce different depths of hierarchies in the result, change the value of the `sql:max-depth` annotation in the schema and execute the template again after each change.</span></span>  
  
 <span data-ttu-id="ebb07-141">在先前的架構中，所有 **\<Emp>** 元素都有一組相同的屬性， (專案**id**、 **FirstName**和**LastName**) 。</span><span class="sxs-lookup"><span data-stu-id="ebb07-141">In the previous schema, all the **\<Emp>** elements had exactly the same set of attributes (**EmployeeID**, **FirstName**, and **LastName**).</span></span> <span data-ttu-id="ebb07-142">下列架構已稍微修改，以針對向管理員報告的所有元素傳回額外的 [**上級**] 屬性 **\<Emp>** 。</span><span class="sxs-lookup"><span data-stu-id="ebb07-142">The following schema has been slightly modified to return an additional **ReportsTo** attribute for all the **\<Emp>** elements that report to a manager.</span></span>  
  
 <span data-ttu-id="ebb07-143">例如，這個 XML 片段會顯示員工 1 的部屬：</span><span class="sxs-lookup"><span data-stu-id="ebb07-143">For example, this XML fragment shows the subordinates of employee 1:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
<Emp FirstName="Nancy" EmployeeID="1" LastName="Devolio">  
  <Emp FirstName="Andrew" EmployeeID="2"   
       ReportsTo="1" LastName="Fuller" />   
  <Emp FirstName="Janet" EmployeeID="3"   
       ReportsTo="1" LastName="Leverling">  
...  
...  
```  
  
 <span data-ttu-id="ebb07-144">這是已修訂的結構描述：</span><span class="sxs-lookup"><span data-stu-id="ebb07-144">This is the revised schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:documentation>  
      Customer-Order-Order Details Schema  
      Copyright 2000 Microsoft. All rights reserved.  
    </xsd:documentation>  
    <xsd:appinfo>  
      <sql:relationship name="SupervisorSupervisee"   
                  parent="Emp"  
                  parent-key="EmployeeID"  
                  child="Emp"  
                  child-key="ReportsTo" />  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="Emp"   
                   type="EmpType"   
                   sql:relation="Emp"   
                   sql:key-fields="EmployeeID"   
                   sql:limit-field="ReportsTo" />  
  <xsd:complexType name="EmpType">  
    <xsd:sequence>  
       <xsd:element name="Emp"   
                    type="EmpType"   
                    sql:relation="Emp"   
                    sql:key-fields="EmployeeID"  
                    sql:relationship="SupervisorSupervisee"  
                    sql:max-depth="6"/>  
    </xsd:sequence>   
    <xsd:attribute name="EmployeeID" type="xsd:int" />  
    <xsd:attribute name="FirstName" type="xsd:string"/>  
    <xsd:attribute name="LastName" type="xsd:string"/>  
    <xsd:attribute name="ReportsTo" type="xsd:int" />  
  </xsd:complexType>  
</xsd:schema>  
```  
  
## <a name="sqlmax-depth-annotation"></a><span data-ttu-id="ebb07-145">sql:max-depth 註解</span><span class="sxs-lookup"><span data-stu-id="ebb07-145">sql:max-depth Annotation</span></span>  
 <span data-ttu-id="ebb07-146">在包含遞迴關聯性的結構描述中，遞迴的深度必須明確指定於結構描述中。</span><span class="sxs-lookup"><span data-stu-id="ebb07-146">In a schema consisting of recursive relationships, the depth of recursion must be explicitly specified in the schema.</span></span> <span data-ttu-id="ebb07-147">這是成功產生可傳回要求結果之對應 FOR XML EXPLICIT 查詢的必要條件。</span><span class="sxs-lookup"><span data-stu-id="ebb07-147">This is required to successfully produce the corresponding FOR XML EXPLICIT query that returns the requested results.</span></span>  
  
 <span data-ttu-id="ebb07-148">您可以在結構描述中使用 `sql:max-depth` 註解，以便指定結構描述所描述之遞迴關聯性的遞迴深度。</span><span class="sxs-lookup"><span data-stu-id="ebb07-148">Use the `sql:max-depth` annotation in the schema to specify the depth of recursion in a recursive relationship that is described in the schema.</span></span> <span data-ttu-id="ebb07-149">`sql:max-depth` 註解的值是正整數 (1 到 50)，表示遞迴的數目：值為 1 會在指定 `sql:max-depth` 註解的元素處停止遞迴，值為 2 會在指定 `sql:max-depth` 之元素的下一個階層處停止遞迴，依此類推。</span><span class="sxs-lookup"><span data-stu-id="ebb07-149">The value of the `sql:max-depth` annotation is a positive integer (1 to 50) that indicates the number of recursions:  A value of 1 stops the recursion at the element for which the `sql:max-depth` annotation is specified; a value of 2 stops the recursion at the next level from the element at which `sql:max-depth` is specified; and so on.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ebb07-150">在基礎實作中，針對對應結構描述所指定的 XPath 查詢會轉換成 SELECT ... FOR XML EXPLICIT 查詢。</span><span class="sxs-lookup"><span data-stu-id="ebb07-150">In the underlying implementation, an XPath query that is specified against a mapping schema is converted to a SELECT ... FOR XML EXPLICIT query.</span></span> <span data-ttu-id="ebb07-151">這個查詢會要求您指定有限的遞迴深度。</span><span class="sxs-lookup"><span data-stu-id="ebb07-151">This query requires you to specify a finite depth of recursion.</span></span> <span data-ttu-id="ebb07-152">您針對 `sql:max-depth` 指定的值越高，產生的 FOR XML EXPLICIT 查詢就越大。</span><span class="sxs-lookup"><span data-stu-id="ebb07-152">The higher the value that you specify for `sql:max-depth`, the larger the FOR XML EXPLICIT query that is generated.</span></span> <span data-ttu-id="ebb07-153">這可能會降低擷取速度。</span><span class="sxs-lookup"><span data-stu-id="ebb07-153">This might slow the retrieval time.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ebb07-154">Updategram 和 XML 大量載入會忽略 max-depth 註解。</span><span class="sxs-lookup"><span data-stu-id="ebb07-154">Updategrams and XML Bulk Load ignore the max-depth annotation.</span></span> <span data-ttu-id="ebb07-155">這表示，不論您針對 max-depth 指定的值為何，都會進行遞迴更新或插入。</span><span class="sxs-lookup"><span data-stu-id="ebb07-155">This means, recursive updates or insertions will happen regardless of what value you specify for max-depth.</span></span>  
  
## <a name="specifying-sqlmax-depth-on-complex-elements"></a><span data-ttu-id="ebb07-156">在複雜元素上指定 sql:max-depth</span><span class="sxs-lookup"><span data-stu-id="ebb07-156">Specifying sql:max-depth on Complex Elements</span></span>  
 <span data-ttu-id="ebb07-157">您可以在任何複雜內容元素上指定 `sql:max-depth` 註解。</span><span class="sxs-lookup"><span data-stu-id="ebb07-157">The `sql:max-depth` annotation can be specified on any complex content element.</span></span>  
  
### <a name="recursive-elements"></a><span data-ttu-id="ebb07-158">遞迴元素</span><span class="sxs-lookup"><span data-stu-id="ebb07-158">Recursive Elements</span></span>  
 <span data-ttu-id="ebb07-159">如果您同時在遞迴關聯性中的父元素和子元素上指定了 `sql:max-depth`，就會優先使用在父系上指定的 `sql:max-depth` 註解。</span><span class="sxs-lookup"><span data-stu-id="ebb07-159">If `sql:max-depth` is specified on both the parent element and the child element in a recursive relationship, the `sql:max-depth` annotation specified on the parent takes precedence.</span></span> <span data-ttu-id="ebb07-160">例如，在下列結構描述中，同時在父和子員工元素上指定了 `sql:max-depth` 註解。</span><span class="sxs-lookup"><span data-stu-id="ebb07-160">For example, in the following schema, the `sql:max-depth` annotation is specified on both the parent and the child employee elements.</span></span> <span data-ttu-id="ebb07-161">在此情況下，在 `sql:max-depth=4` **\<Emp>** 父元素上指定 (扮演監督員) 的角色，會優先使用。</span><span class="sxs-lookup"><span data-stu-id="ebb07-161">In this case, `sql:max-depth=4`, specified on the **\<Emp>** parent element (playing a role of supervisor), takes precedence.</span></span> <span data-ttu-id="ebb07-162">在 `sql:max-depth` **\<Emp>** (扮演被監督者) 角色的子項目上指定的會被忽略。</span><span class="sxs-lookup"><span data-stu-id="ebb07-162">The `sql:max-depth` specified on the child **\<Emp>** element (playing a role of supervisee) is ignored.</span></span>  
  
#### <a name="example-b"></a><span data-ttu-id="ebb07-163">範例 B</span><span class="sxs-lookup"><span data-stu-id="ebb07-163">Example B</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:appinfo>  
      <sql:relationship name="SupervisorSupervisee"  
                                  parent="Emp"  
                                  parent-key="EmployeeID"  
                                  child="Emp"  
                                  child-key="ReportsTo" />  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="Emp" type="EmployeeType"   
                          sql:relation="Emp"   
                          sql:key-fields="EmployeeID"   
                          sql:limit-field="ReportsTo"   
                          sql:max-depth="3" />  
  <xsd:complexType name="EmployeeType">  
    <xsd:sequence>  
      <xsd:element name="Emp" type="EmployeeType"   
                              sql:relation="Emp"   
                              sql:key-fields="EmployeeID"  
                              sql:relationship="SupervisorSupervisee"  
                              sql:max-depth="2" />  
    </xsd:sequence>   
    <xsd:attribute name="EmployeeID" type="xsd:ID" />  
    <xsd:attribute name="FirstName" type="xsd:string"/>  
    <xsd:attribute name="LastName" type="xsd:string"/>  
  </xsd:complexType>  
</xsd:schema>  
```  
  
 <span data-ttu-id="ebb07-164">若要測試這個結構描述，請遵循本主題前面針對「範例 A」所提供的步驟。</span><span class="sxs-lookup"><span data-stu-id="ebb07-164">To test this schema, follow the steps provided for Sample A, earlier in this topic.</span></span>  
  
### <a name="nonrecursive-elements"></a><span data-ttu-id="ebb07-165">非遞迴元素</span><span class="sxs-lookup"><span data-stu-id="ebb07-165">Nonrecursive Elements</span></span>  
 <span data-ttu-id="ebb07-166">如果您在結構描述中不會導致任何遞迴的元素上指定了 `sql:max-depth` 註解，系統就會忽略此註解。</span><span class="sxs-lookup"><span data-stu-id="ebb07-166">If the `sql:max-depth` annotation is specified on an element in the schema that does not cause any recursion, it is ignored.</span></span> <span data-ttu-id="ebb07-167">在下列架構中， **\<Emp>** 元素是由子專案所組成，而 **\<Constant>** 該子項目又會有 **\<Emp>** 子專案。</span><span class="sxs-lookup"><span data-stu-id="ebb07-167">In the following schema, an **\<Emp>** element consists of a **\<Constant>** child element, which, in turn, has an **\<Emp>** child element.</span></span>  
  
 <span data-ttu-id="ebb07-168">在此架構中， `sql:max-depth` 會忽略在元素上指定的注釋， **\<Constant>** 因為 **\<Emp>** 父元素和子專案之間沒有遞迴 **\<Constant>** 。</span><span class="sxs-lookup"><span data-stu-id="ebb07-168">In this schema, the `sql:max-depth` annotation specified on the **\<Constant>** element is ignored because there is no recursion between the **\<Emp>** parent and the **\<Constant>** child element.</span></span> <span data-ttu-id="ebb07-169">但是上階 **\<Emp>** 和子系之間有遞迴 **\<Emp>** 。</span><span class="sxs-lookup"><span data-stu-id="ebb07-169">But there is recursion between the **\<Emp>** ancestor and the **\<Emp>** child.</span></span> <span data-ttu-id="ebb07-170">此結構描述會同時在這兩個項目上指定 `sql:max-depth` 註解。</span><span class="sxs-lookup"><span data-stu-id="ebb07-170">The schema specifies the `sql:max-depth` annotation on both.</span></span> <span data-ttu-id="ebb07-171">因此，在 `sql:max-depth` [監督員] 角色的上階 (上指定的注釋 **\<Emp>**) 會優先使用。</span><span class="sxs-lookup"><span data-stu-id="ebb07-171">Therefore, the `sql:max-depth` annotation that is specified on the ancestor (**\<Emp>** in the supervisor role) takes precedence.</span></span>  
  
#### <a name="example-c"></a><span data-ttu-id="ebb07-172">範例 C</span><span class="sxs-lookup"><span data-stu-id="ebb07-172">Example C</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:appinfo>  
      <sql:relationship name="SupervisorSupervisee"   
                  parent="Emp"   
                  child="Emp"   
                  parent-key="EmployeeID"   
                  child-key="ReportsTo"/>  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="Emp"   
               sql:relation="Emp"   
               type="EmpType"  
               sql:limit-field="ReportsTo"  
               sql:max-depth="1" />  
    <xsd:complexType name="EmpType" >  
      <xsd:sequence>  
       <xsd:element name="Constant"   
                    sql:is-constant="1"   
                    sql:max-depth="20" >  
         <xsd:complexType >  
           <xsd:sequence>  
            <xsd:element name="Emp"   
                         sql:relation="Emp" type="EmpType"  
                         sql:relationship="SupervisorSupervisee"   
                         sql:max-depth="3" />  
         </xsd:sequence>  
         </xsd:complexType>  
         </xsd:element>  
      </xsd:sequence>  
      <xsd:attribute name="EmployeeID" type="xsd:int" />  
    </xsd:complexType>  
</xsd:schema>  
```  
  
 <span data-ttu-id="ebb07-173">若要測試這個結構描述，請遵循本主題前面針對「範例 A」所提供的步驟。</span><span class="sxs-lookup"><span data-stu-id="ebb07-173">To test this schema, follow the steps provided for Example A, earlier in this topic.</span></span>  
  
## <a name="complex-types-derived-by-restriction"></a><span data-ttu-id="ebb07-174">限制所衍生的複雜類型</span><span class="sxs-lookup"><span data-stu-id="ebb07-174">Complex Types Derived by Restriction</span></span>  
 <span data-ttu-id="ebb07-175">如果您有衍生的複雜類型 **\<restriction>** ，對應之基底複雜類型的元素就無法指定 `sql:max-depth` 批註。</span><span class="sxs-lookup"><span data-stu-id="ebb07-175">If you have a complex type derivation by **\<restriction>**, elements of the corresponding base complex type cannot specify the `sql:max-depth` annotation.</span></span> <span data-ttu-id="ebb07-176">在這些情況下，您可以將 `sql:max-depth` 註解加入至衍生類型的元素。</span><span class="sxs-lookup"><span data-stu-id="ebb07-176">In these cases, the `sql:max-depth` annotation can be added to the element of the derived type.</span></span>  
  
 <span data-ttu-id="ebb07-177">另一方面，如果您有衍生的複雜型別 **\<extension>** ，則對應之基底複雜型別的專案可以指定 `sql:max-depth` 批註。</span><span class="sxs-lookup"><span data-stu-id="ebb07-177">On the other hand, if you have a complex type derivation by **\<extension>**, the elements of the corresponding base complex type can specify the `sql:max-depth` annotation.</span></span>  
  
 <span data-ttu-id="ebb07-178">例如，下列 XSD 結構描述會產生錯誤，因為在基底類型上指定了 `sql:max-depth` 註解。</span><span class="sxs-lookup"><span data-stu-id="ebb07-178">For example, the following XSD schema generates an error because the `sql:max-depth` annotation is specified on the base type.</span></span> <span data-ttu-id="ebb07-179">從另一個型別衍生的型別不支援這個注釋 **\<restriction>** 。</span><span class="sxs-lookup"><span data-stu-id="ebb07-179">This annotation is not supported on a type that is derived by **\<restriction>** from another type.</span></span> <span data-ttu-id="ebb07-180">若要修正這個問題，您必須變更此結構描述並且在衍生類型的元素上指定 `sql:max-depth` 註解。</span><span class="sxs-lookup"><span data-stu-id="ebb07-180">To fix this problem, you must change the schema and specify the `sql:max-depth` annotation on element in the derived type.</span></span>  
  
#### <a name="example-d"></a><span data-ttu-id="ebb07-181">範例 D</span><span class="sxs-lookup"><span data-stu-id="ebb07-181">Example D</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:msdata="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:complexType name="CustomerBaseType">   
    <xsd:sequence>  
       <xsd:element name="CID" msdata:field="CustomerID" />  
       <xsd:element name="CompanyName"/>  
       <xsd:element name="Customers" msdata:max-depth="3">  
         <xsd:annotation>  
           <xsd:appinfo>  
             <msdata:relationship  
                     parent="Customers"  
                     parent-key="CustomerID"  
                     child-key="CustomerID"  
                     child="Customers" />  
           </xsd:appinfo>  
         </xsd:annotation>  
       </xsd:element>  
    </xsd:sequence>  
  </xsd:complexType>  
  <xsd:element name="Customers" type="CustomerType"/>  
  <xsd:complexType name="CustomerType">  
    <xsd:complexContent>  
       <xsd:restriction base="CustomerBaseType">  
          <xsd:sequence>  
            <xsd:element name="CID"   
                         type="xsd:string"/>  
            <xsd:element name="CompanyName"   
                         type="xsd:string"  
                         msdata:field="CName" />  
            <xsd:element name="Customers"   
                         type="CustomerType" />  
          </xsd:sequence>  
       </xsd:restriction>  
    </xsd:complexContent>  
  </xsd:complexType>  
</xsd:schema>   
```  
  
 <span data-ttu-id="ebb07-182">在此結構描述中，`sql:max-depth` 指定於 `CustomerBaseType` 複雜類型上。</span><span class="sxs-lookup"><span data-stu-id="ebb07-182">In the schema, `sql:max-depth` is specified on a `CustomerBaseType` complex type.</span></span> <span data-ttu-id="ebb07-183">此架構也會指定 **\<Customer>** 類型的元素 `CustomerType` ，此專案衍生自 `CustomerBaseType` 。</span><span class="sxs-lookup"><span data-stu-id="ebb07-183">The schema also specifies a **\<Customer>** element of type `CustomerType`, which is derived from `CustomerBaseType`.</span></span> <span data-ttu-id="ebb07-184">在這類結構描述上指定的 XPath 查詢將會產生錯誤，因為定義於限制基底類型中的元素不支援 `sql:max-depth`。</span><span class="sxs-lookup"><span data-stu-id="ebb07-184">An XPath query specified on such a schema will generate an error, because `sql:max-depth` is not supported on an element that is defined in a restriction base type.</span></span>  
  
## <a name="schemas-with-a-deep-hierarchy"></a><span data-ttu-id="ebb07-185">具有深度階層的結構描述</span><span class="sxs-lookup"><span data-stu-id="ebb07-185">Schemas with a Deep Hierarchy</span></span>  
 <span data-ttu-id="ebb07-186">您可能會擁有一個包括深度階層的結構描述，其中某個元素包含子元素，而後者又包含其他子元素，依此類推。</span><span class="sxs-lookup"><span data-stu-id="ebb07-186">You might have a schema that includes a deep hierarchy in which an element contains a child element, which in turn contains another child element, and so on.</span></span> <span data-ttu-id="ebb07-187">如果在這類結構描述中指定的 `sql:max-depth` 註解產生了包含超過 500 個層級之階層的 XML 文件 (最上層元素位於第 1 層，其子系位於第 2 層，依此類推)，系統就會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="ebb07-187">If the `sql:max-depth` annotation specified in such a schema generates an XML document that includes a hierarchy of more than 500 levels (with top-level element at level 1, its child at level 2, and so on), an error is returned.</span></span>  
  
  
