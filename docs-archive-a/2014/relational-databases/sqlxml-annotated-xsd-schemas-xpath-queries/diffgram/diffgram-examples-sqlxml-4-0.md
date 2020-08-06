---
title: " (SQLXML 4.0) 的 DiffGram 範例 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- DiffGrams [SQLXML], examples
- examples [SQLXML], DiffGram
- diffgr:parentID
- parentID annotation
ms.assetid: fc148583-dfd3-4efb-a413-f47b150b0975
author: rothja
ms.author: jroth
ms.openlocfilehash: 04fb355af01f9853149a84af72471375d9135468
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596602"
---
# <a name="diffgram-examples-sqlxml-40"></a><span data-ttu-id="b5ce7-102">DiffGram 範例 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="b5ce7-102">DiffGram Examples (SQLXML 4.0)</span></span>
  <span data-ttu-id="b5ce7-103">本主題的範例是由 DiffGram 所組成，DiffGram 會針對資料庫執行插入、更新和刪除作業。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-103">The examples in this topic consist of DiffGrams that perform insert, update, and delete operations to the database.</span></span> <span data-ttu-id="b5ce7-104">在使用範例之前，請注意下列事項：</span><span class="sxs-lookup"><span data-stu-id="b5ce7-104">Before using the examples, note the following:</span></span>  
  
-   <span data-ttu-id="b5ce7-105">如果您想要測試 DiffGram 範例，範例中會使用兩個必須建立的資料表 (Cust 和 Ord)：</span><span class="sxs-lookup"><span data-stu-id="b5ce7-105">The examples use two tables (Cust and Ord) that must be created if you want to test the DiffGram examples:</span></span>  
  
    ```  
    Cust(CustomerID, CompanyName, ContactName)  
    Ord(OrderID, CustomerID)  
    ```  
  
-   <span data-ttu-id="b5ce7-106">本主題的大多數範例都會使用以下 XSD 結構描述：</span><span class="sxs-lookup"><span data-stu-id="b5ce7-106">Most of the examples in this topic use the following XSD Schema:</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
    <xsd:annotation>  
      <xsd:documentation>  
        Diffgram Customers/Orders Schema.  
      </xsd:documentation>  
      <xsd:appinfo>  
           <sql:relationship name="CustomersOrders"   
                      parent="Cust"  
                      parent-key="CustomerID"  
                      child-key="CustomerID"  
                      child="Ord"/>  
      </xsd:appinfo>  
    </xsd:annotation>  
  
    <xsd:element name="Customer" sql:relation="Cust">  
      <xsd:complexType>  
        <xsd:sequence>  
          <xsd:element name="CompanyName"    type="xsd:string"/>  
          <xsd:element name="ContactName"    type="xsd:string"/>  
           <xsd:element name="Order" sql:relation="Ord" sql:relationship="CustomersOrders">  
            <xsd:complexType>  
              <xsd:attribute name="OrderID" type="xsd:int" sql:field="OrderID"/>  
              <xsd:attribute name="CustomerID" type="xsd:string"/>  
            </xsd:complexType>  
          </xsd:element>  
        </xsd:sequence>  
        <xsd:attribute name="CustomerID" type="xsd:string" sql:field="CustomerID"/>  
      </xsd:complexType>  
    </xsd:element>  
  
    </xsd:schema>     
    ```  
  
     <span data-ttu-id="b5ce7-107">請將這個結構描述儲存為 DiffGramSchema.xml，並放在您想要儲存範例中使用之其他檔案的相同資料夾內。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-107">Save this schema as DiffGramSchema.xml in the same folder where you save other files used in the examples.</span></span>  
  
## <a name="a-deleting-a-record-by-using-a-diffgram"></a><span data-ttu-id="b5ce7-108">A.</span><span class="sxs-lookup"><span data-stu-id="b5ce7-108">A.</span></span> <span data-ttu-id="b5ce7-109">使用 DiffGram 刪除記錄</span><span class="sxs-lookup"><span data-stu-id="b5ce7-109">Deleting a record by using a DiffGram</span></span>  
 <span data-ttu-id="b5ce7-110">此範例中的 DiffGram 會從 Cust 資料表中刪除客戶 (CustomerID 為 ALFKI) 記錄，並從 Ord 資料表中刪除對應的訂單記錄 (OrderID 為 1)。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-110">The DiffGram in this example deletes a customer (whose CustomerID is ALFKI) record from the Cust table and deletes the corresponding order record (whose OrderID is 1) from the Ord table.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql" sql:mapping-schema="DiffGramSchema.xml">  
  <diffgr:diffgram   
           xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"   
           xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
    <DataInstance/>  
  
    <diffgr:before>  
        <Order diffgr:id="Order1"   
               msdata:rowOrder="0"   
               CustomerID="ALFKI"   
               OrderID="1"/>  
        <Customer diffgr:id="Customer1"   
                  msdata:rowOrder="0"   
                  CustomerID="ALFKI">  
           <CompanyName>Alfreds Futterkiste</CompanyName>  
           <ContactName>Maria Anders</ContactName>  
        </Customer>  
    </diffgr:before>  
    <msdata:errors/>  
  </diffgr:diffgram>  
</ROOT>  
```  
  
 <span data-ttu-id="b5ce7-111">在 **\<before>** 區塊中，有一個 **\<Order>** 元素 (**diffgr： Id = "Order1"**) ， **\<Customer>** (**diffgr： id = "Customer1"**) 的元素。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-111">In the **\<before>** block, there is an **\<Order>** element (**diffgr:id="Order1"**) and a **\<Customer>** element (**diffgr:id="Customer1"**).</span></span> <span data-ttu-id="b5ce7-112">這些項目代表資料庫中的現有記錄。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-112">These elements represent existing records in the database.</span></span> <span data-ttu-id="b5ce7-113">**\<DataInstance>** 元素沒有對應的記錄 (具有相同的**diffgr： id**) 。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-113">The **\<DataInstance>** element does not have the corresponding records (with the same **diffgr:id**).</span></span> <span data-ttu-id="b5ce7-114">這表示刪除作業。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-114">This indicates a delete operation.</span></span>  
  
#### <a name="to-test-the-diffgram"></a><span data-ttu-id="b5ce7-115">若要測試 DiffGram</span><span class="sxs-lookup"><span data-stu-id="b5ce7-115">To test the DiffGram</span></span>  
  
1.  <span data-ttu-id="b5ce7-116">在**tempdb**資料庫中建立這些資料表。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-116">Create these tables in the **tempdb** database.</span></span>  
  
    ```  
    CREATE TABLE Cust(  
            CustomerID  nchar(5) Primary Key,  
            CompanyName nvarchar(40) NOT NULL ,  
            ContactName nvarchar(60) NULL)  
    GO  
  
    CREATE TABLE Ord(  
       OrderID    int Primary Key,  
       CustomerID nchar(5) Foreign Key REFERENCES Cust(CustomerID))  
    GO  
    ```  
  
2.  <span data-ttu-id="b5ce7-117">加入這個範例資料：</span><span class="sxs-lookup"><span data-stu-id="b5ce7-117">Add this sample data:</span></span>  
  
    ```  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ALFKI', N'Alfreds Futterkiste', N'Maria Anders')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANATR', N'Ana Trujillo Emparedados y helados', N'Ana Trujillo')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANTON', N'Antonio Moreno Taquer??a', N'Antonio Moreno')  
  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(1, N'ALFKI')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(2, N'ANATR')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(3, N'ANTON')  
    ```  
  
3.  <span data-ttu-id="b5ce7-118">複製上述的 DiffGram，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-118">Copy the DiffGram above and paste it into a text file.</span></span> <span data-ttu-id="b5ce7-119">然後將檔案儲存為 MyDiffGram.xml，放在前述步驟所使用的相同資料夾中。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-119">Save the file as MyDiffGram.xml in the same folder used in the previous step.</span></span>  
  
4.  <span data-ttu-id="b5ce7-120">複製本主題稍早所提供的 DiffGramSchema，並將它貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-120">Copy the DiffGramSchema provided earlier in this topic and paste it into a text file.</span></span> <span data-ttu-id="b5ce7-121">然後將檔案儲存為 DiffGramSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-121">Save the file as DiffGramSchema.xml.</span></span>  
  
5.  <span data-ttu-id="b5ce7-122">建立及使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 來執行 DiffGram。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-122">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the DiffGram.</span></span>  
  
     <span data-ttu-id="b5ce7-123">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-123">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
## <a name="b-inserting-a-record-by-using-a-diffgram"></a><span data-ttu-id="b5ce7-124">B.</span><span class="sxs-lookup"><span data-stu-id="b5ce7-124">B.</span></span> <span data-ttu-id="b5ce7-125">使用 DiffGram 插入記錄</span><span class="sxs-lookup"><span data-stu-id="b5ce7-125">Inserting a record by using a DiffGram</span></span>  
 <span data-ttu-id="b5ce7-126">在此範例中，DiffGram 會在 Cust 資料表中插入記錄，並在 Ord 資料表中插入記錄。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-126">In this example, the DiffGram inserts a record in the Cust table and a record in the Ord table.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql"   
      sql:mapping-schema="DiffGramSchema.xml">  
  <diffgr:diffgram   
          xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"   
          xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
    <DataInstance>  
       <Customer diffgr:id="Customer1" msdata:rowOrder="0"    
                 diffgr:hasChanges="inserted" CustomerID="ALFKI">  
        <CompanyName>C3Company</CompanyName>  
        <ContactName>C3Contact</ContactName>  
        <Order diffgr:id="Order1"   
               msdata:rowOrder="0"  
               diffgr:hasChanges="inserted"   
               CustomerID="ALFKI" OrderID="1"/>  
      </Customer>  
    </DataInstance>  
  
  </diffgr:diffgram>  
</ROOT>  
```  
  
 <span data-ttu-id="b5ce7-127">在這個 DiffGram 中， **\<before>** 不會指定區塊 () 找不到任何現有的資料庫記錄。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-127">In this DiffGram the **\<before>** block is not specified (no existing database records identified).</span></span> <span data-ttu-id="b5ce7-128">有兩個記錄實例 (由 **\<Customer>** **\<Order>** 區塊) 中的和元素識別， **\<DataInstance>** 分別對應至 [加入] 和 [Ord] 資料表。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-128">There are two record instances (identified by the **\<Customer>** and **\<Order>** elements in the **\<DataInstance>** block) that map to Cust and Ord tables, respectively.</span></span> <span data-ttu-id="b5ce7-129">這兩個元素都會指定**diffgr： hasChanges**屬性 (**hasChanges = "插入"**) 。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-129">Both of these elements specify the **diffgr:hasChanges** attribute (**hasChanges="inserted"**).</span></span> <span data-ttu-id="b5ce7-130">這表示插入作業。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-130">This indicates an insert operation.</span></span> <span data-ttu-id="b5ce7-131">在這個 DiffGram 中，如果您指定**hasChanges = "modified"**，表示您想要修改不存在的記錄，這會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-131">In this DiffGram, if you specify **hasChanges="modified"**, you are indicating that you want to modify a record that does not exist, which results in an error.</span></span>  
  
#### <a name="to-test-the-diffgram"></a><span data-ttu-id="b5ce7-132">若要測試 DiffGram</span><span class="sxs-lookup"><span data-stu-id="b5ce7-132">To test the DiffGram</span></span>  
  
1.  <span data-ttu-id="b5ce7-133">在**tempdb**資料庫中建立這些資料表。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-133">Create these tables in the **tempdb** database.</span></span>  
  
    ```  
    CREATE TABLE Cust(  
            CustomerID  nchar(5) Primary Key,  
            CompanyName nvarchar(40) NOT NULL ,  
            ContactName nvarchar(60) NULL)  
    GO  
  
    CREATE TABLE Ord(  
       OrderID    int Primary Key,  
       CustomerID nchar(5) Foreign Key REFERENCES Cust(CustomerID))  
    GO  
    ```  
  
2.  <span data-ttu-id="b5ce7-134">加入這個範例資料：</span><span class="sxs-lookup"><span data-stu-id="b5ce7-134">Add this sample data:</span></span>  
  
    ```  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ALFKI', N'Alfreds Futterkiste', N'Maria Anders')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANATR', N'Ana Trujillo Emparedados y helados', N'Ana Trujillo')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANTON', N'Antonio Moreno Taquer??a', N'Antonio Moreno')  
  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(1, N'ALFKI')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(2, N'ANATR')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(3, N'ANTON')  
    ```  
  
3.  <span data-ttu-id="b5ce7-135">複製上述的 DiffGram，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-135">Copy the DiffGram above and paste it into a text file.</span></span> <span data-ttu-id="b5ce7-136">然後將檔案儲存為 MyDiffGram.xml，放在前述步驟所使用的相同資料夾中。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-136">Save the file as MyDiffGram.xml in the same folder used in the previous step.</span></span>  
  
4.  <span data-ttu-id="b5ce7-137">複製本主題稍早所提供的 DiffGramSchema，並將它貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-137">Copy the DiffGramSchema provided earlier in this topic and paste it into a text file.</span></span> <span data-ttu-id="b5ce7-138">然後將檔案儲存為 DiffGramSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-138">Save the file as DiffGramSchema.xml.</span></span>  
  
5.  <span data-ttu-id="b5ce7-139">建立及使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 來執行 DiffGram。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-139">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the DiffGram.</span></span>  
  
     <span data-ttu-id="b5ce7-140">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-140">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
## <a name="c-updating-an-existing-record-by-using-a-diffgram"></a><span data-ttu-id="b5ce7-141">C.</span><span class="sxs-lookup"><span data-stu-id="b5ce7-141">C.</span></span> <span data-ttu-id="b5ce7-142">使用 DiffGram 來更新現有的記錄</span><span class="sxs-lookup"><span data-stu-id="b5ce7-142">Updating an existing record by using a DiffGram</span></span>  
 <span data-ttu-id="b5ce7-143">在此範例中，DiffGram 會更新客戶 ALFKI 的客戶資訊 (CompanyName 和 ContactName)。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-143">In this example, the DiffGram updates customer information (CompanyName and ContactName) for customer ALFKI.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql" sql:mapping-schema="DiffGramSchema.xml">  
  <diffgr:diffgram   
           xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"   
           xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
    <DataInstance>  
      <Customer diffgr:id="Customer1"   
                msdata:rowOrder="0" diffgr:hasChanges="modified"   
                CustomerID="ALFKI">  
          <CompanyName>Bottom Dollar Markets</CompanyName>  
          <ContactName>Antonio Moreno</ContactName>  
      </Customer>  
    </DataInstance>  
  
    <diffgr:before>  
     <Customer diffgr:id="Customer1"   
               msdata:rowOrder="0"   
               CustomerID="ALFKI">  
        <CompanyName>Alfreds Futterkiste</CompanyName>  
        <ContactName>Maria Anders</ContactName>  
      </Customer>  
    </diffgr:before>  
  
  </diffgr:diffgram>  
</ROOT>  
```  
  
 <span data-ttu-id="b5ce7-144">**\<before>** 區塊包含 **\<Customer>** 元素 (**diffgr： Id = "Customer1"**) 。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-144">The **\<before>** block includes a **\<Customer>** element (**diffgr:id="Customer1"**).</span></span> <span data-ttu-id="b5ce7-145">**\<DataInstance>** 區塊包含 **\<Customer>** 具有相同**識別碼**的對應元素。**\<customer>** 中的元素 **\<NewDataSet>** 也會指定**diffgr： hasChanges = "modified"**。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-145">The **\<DataInstance>** block includes the corresponding **\<Customer>** element with same **id**. The **\<customer>** element in the **\<NewDataSet>** also specifies **diffgr:hasChanges="modified"**.</span></span> <span data-ttu-id="b5ce7-146">這表示更新作業，而**customer 資料表中的客戶**記錄也會隨之更新。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-146">This indicates an update operation, and the customer record in the **Cust** table is updated accordingly.</span></span> <span data-ttu-id="b5ce7-147">請注意，如果未指定**diffgr： hasChanges**屬性，DiffGram 處理邏輯會忽略這個元素，而且不會執行任何更新。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-147">Note that if the **diffgr:hasChanges** attribute is not specified, the DiffGram processing logic ignores this element and no updates are performed.</span></span>  
  
#### <a name="to-test-the-diffgram"></a><span data-ttu-id="b5ce7-148">若要測試 DiffGram</span><span class="sxs-lookup"><span data-stu-id="b5ce7-148">To test the DiffGram</span></span>  
  
1.  <span data-ttu-id="b5ce7-149">在**tempdb**資料庫中建立這些資料表。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-149">Create these tables in the **tempdb** database.</span></span>  
  
    ```  
    CREATE TABLE Cust(  
            CustomerID  nchar(5) Primary Key,  
            CompanyName nvarchar(40) NOT NULL ,  
            ContactName nvarchar(60) NULL)  
    GO  
  
    CREATE TABLE Ord(  
       OrderID    int Primary Key,  
       CustomerID nchar(5) Foreign Key REFERENCES Cust(CustomerID))  
    GO  
    ```  
  
2.  <span data-ttu-id="b5ce7-150">加入這個範例資料：</span><span class="sxs-lookup"><span data-stu-id="b5ce7-150">Add this sample data:</span></span>  
  
    ```  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ALFKI', N'Alfreds Futterkiste', N'Maria Anders')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANATR', N'Ana Trujillo Emparedados y helados', N'Ana Trujillo')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANTON', N'Antonio Moreno Taquer??a', N'Antonio Moreno')  
  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(1, N'ALFKI')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(2, N'ANATR')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(3, N'ANTON')  
    ```  
  
3.  <span data-ttu-id="b5ce7-151">複製上述的 DiffGram，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-151">Copy the DiffGram above and paste it into a text file.</span></span> <span data-ttu-id="b5ce7-152">然後將檔案儲存為 MyDiffGram.xml，放在前述步驟所使用的相同資料夾中。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-152">Save the file as MyDiffGram.xml in the same folder used in the previous step.</span></span>  
  
4.  <span data-ttu-id="b5ce7-153">複製本主題稍早所提供的 DiffGramSchema，並將它貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-153">Copy the DiffGramSchema provided earlier in this topic and paste it into a text file.</span></span> <span data-ttu-id="b5ce7-154">然後將檔案儲存為 DiffGramSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-154">Save the file as DiffGramSchema.xml.</span></span>  
  
5.  <span data-ttu-id="b5ce7-155">建立及使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 來執行 DiffGram。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-155">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the DiffGram.</span></span>  
  
     <span data-ttu-id="b5ce7-156">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-156">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
## <a name="d-inserting-updating-and-deleting-records-by-using-a-diffgram"></a><span data-ttu-id="b5ce7-157">D.</span><span class="sxs-lookup"><span data-stu-id="b5ce7-157">D.</span></span> <span data-ttu-id="b5ce7-158">使用 DiffGram 來插入、更新及刪除記錄</span><span class="sxs-lookup"><span data-stu-id="b5ce7-158">Inserting, updating, and deleting records by using a DiffGram</span></span>  
 <span data-ttu-id="b5ce7-159">這個範例中會使用相對複雜的 DiffGram 來執行插入、更新和刪除作業。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-159">In this example, a relatively complex DiffGram is used to perform insert, update, and delete operations.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql" sql:mapping-schema="DiffGramSchema.xml">  
  <diffgr:diffgram   
         xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"   
         xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
    <DataInstance>  
      <Customer diffgr:id="Customer2" msdata:rowOrder="1"   
                diffgr:hasChanges="modified"   
                CustomerID="ANATR">  
          <CompanyName>Bottom Dollar Markets</CompanyName>  
          <ContactName>Elizabeth Lincoln</ContactName>  
          <Order diffgr:id="Order2" msdata:rowOrder="1"   
               msdata:hiddenCustomerID="ANATR"   
               CustomerID="ANATR" OrderID="2"/>  
      </Customer>  
  
      <Customer diffgr:id="Customer3" msdata:rowOrder="2"   
                CustomerID="ANTON">  
         <CompanyName>Chop-suey Chinese</CompanyName>  
         <ContactName>Yang Wang</ContactName>  
         <Order diffgr:id="Order3" msdata:rowOrder="2"   
               msdata:hiddenCustomerID="ANTON"   
               CustomerID="ANTON" OrderID="3"/>  
      </Customer>  
      <Customer diffgr:id="Customer4" msdata:rowOrder="3"   
                diffgr:hasChanges="inserted"   
                CustomerID="AROUT">  
         <CompanyName>Around the Horn</CompanyName>  
         <ContactName>Thomas Hardy</ContactName>  
         <Order diffgr:id="Order4" msdata:rowOrder="3"   
                diffgr:hasChanges="inserted"   
                msdata:hiddenCustomerID="AROUT"   
               CustomerID="AROUT" OrderID="4"/>  
      </Customer>  
    </DataInstance>  
    <diffgr:before>  
      <Order diffgr:id="Order1" msdata:rowOrder="0"   
             msdata:hiddenCustomerID="ALFKI"   
             CustomerID="ALFKI" OrderID="1"/>  
      <Customer diffgr:id="Customer1" msdata:rowOrder="0"   
                CustomerID="ALFKI">  
        <CompanyName>Alfreds Futterkiste</CompanyName>  
        <ContactName>Maria Anders</ContactName>  
      </Customer>  
      <Customer diffgr:id="Customer2" msdata:rowOrder="1"   
                CustomerID="ANATR">  
        <CompanyName>Ana Trujillo Emparedados y helados</CompanyName>  
        <ContactName>Ana Trujillo</ContactName>  
      </Customer>  
    </diffgr:before>  
  </diffgr:diffgram>  
</ROOT>  
```  
  
 <span data-ttu-id="b5ce7-160">DiffGram 邏輯會處理這個 DiffGram，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b5ce7-160">The DiffGram logic processes this DiffGram as follows:</span></span>  
  
-   <span data-ttu-id="b5ce7-161">根據 DiffGram 處理邏輯，區塊中的所有最上層元素會 **\<before>** 對應到對應的資料表，如對應架構中所述。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-161">In accordance with DiffGram processing logic, all the top-level elements in the **\<before>** block map to corresponding tables, as described in the mapping schema.</span></span>  
  
-   <span data-ttu-id="b5ce7-162">**\<before>** 區塊具有 **\<Order>** (**dffgr： Id = "Order1"**) 的元素，以及 **\<Customer>** (**diffgr： id = "Customer1"**) 的元素，但區塊 (中沒有對應的元素， **\<DataInstance>**) 具有相同的識別碼。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-162">The **\<before>** block has an **\<Order>** element (**dffgr:id="Order1"**) and a **\<Customer>** element (**diffgr:id="Customer1"**) for which there is no corresponding element in the **\<DataInstance>** block (with the same ID).</span></span> <span data-ttu-id="b5ce7-163">這表示刪除作業，而且會從 Cust 和 Ord 資料表中刪除記錄。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-163">This indicates a delete operation, and the records are deleted from the Cust and Ord tables.</span></span>  
  
-   <span data-ttu-id="b5ce7-164">**\<before>** 區塊具有 **\<Customer>** (**diffgr： Id = "Customer2"**) 的元素，但 **\<Customer>** 區塊 (中有對應的元素， **\<DataInstance>** 但其識別碼) 相同。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-164">The **\<before>** block has a **\<Customer>** element (**diffgr:id="Customer2"**) for which there is a corresponding **\<Customer>** element in the **\<DataInstance>** block (with the same ID).</span></span> <span data-ttu-id="b5ce7-165">區塊中的元素會 **\<DataInstance>** 指定**Diffgr： hasChanges = "modified"**。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-165">The element in the **\<DataInstance>** block specifies **diffgr:hasChanges="modified"**.</span></span> <span data-ttu-id="b5ce7-166">這是更新作業，針對客戶 ANATR，系統會使用區塊中指定的值，在 customer 資料表中更新「公司名稱」和「連絡人」資訊 **\<DataInstance>** 。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-166">This is an update operation in which for customer ANATR, the CompanyName and ContactName information is updated in the Cust table using values that are specified in the **\<DataInstance>** block.</span></span>  
  
-   <span data-ttu-id="b5ce7-167">**\<DataInstance>** 區塊具有 **\<Customer>** 元素 (**diffgr： Id = "Customer3"**) ， **\<Order>** (**diffgr： id = "Order3"**) 的元素。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-167">The **\<DataInstance>** block has a **\<Customer>** element (**diffgr:id="Customer3"**) and an **\<Order>** element (**diffgr:id="Order3"**).</span></span> <span data-ttu-id="b5ce7-168">這兩個元素都不會指定**diffgr： hasChanges**屬性。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-168">Neither of these elements specify the **diffgr:hasChanges** attribute.</span></span> <span data-ttu-id="b5ce7-169">因此，DiffGram 處理邏輯會忽略這些元素。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-169">Therefore, the DiffGram processing logic ignores these elements.</span></span>  
  
-   <span data-ttu-id="b5ce7-170">**\<DataInstance>** 區塊具有 **\<Customer>** 元素 (**diffgr： Id = "Customer4"**) 和 **\<Order>** 元素 (**diffgr： id = "Order4"**) ，但區塊中沒有對應的元素 \<before> 。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-170">The **\<DataInstance>** block has a **\<Customer>** element (**diffgr:id="Customer4"**) and an **\<Order>** element (**diffgr:id="Order4"**) for which there are no corresponding elements in the \<before> block.</span></span> <span data-ttu-id="b5ce7-171">區塊中的這些元素會 **\<DataInstance>** 指定**Diffgr： hasChanges = "已插入"**。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-171">These elements in the **\<DataInstance>** block specify **diffgr:hasChanges="inserted"**.</span></span> <span data-ttu-id="b5ce7-172">因此，新的記錄會加入 Cust 資料表和 Ord 資料表中。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-172">Therefore, a new record is added in the Cust table and in the Ord table.</span></span>  
  
#### <a name="to-test-the-diffgram"></a><span data-ttu-id="b5ce7-173">若要測試 DiffGram</span><span class="sxs-lookup"><span data-stu-id="b5ce7-173">To test the DiffGram</span></span>  
  
1.  <span data-ttu-id="b5ce7-174">在**tempdb**資料庫中建立下列資料表。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-174">Create the following tables in the **tempdb** database.</span></span>  
  
    ```  
    CREATE TABLE Cust(  
            CustomerID  nchar(5) Primary Key,  
            CompanyName nvarchar(40) NOT NULL ,  
            ContactName nvarchar(60) NULL)  
    GO  
  
    CREATE TABLE Ord(  
       OrderID    int Primary Key,  
       CustomerID nchar(5) Foreign Key REFERENCES Cust(CustomerID))  
    GO  
    ```  
  
2.  <span data-ttu-id="b5ce7-175">加入這個範例資料：</span><span class="sxs-lookup"><span data-stu-id="b5ce7-175">Add this sample data:</span></span>  
  
    ```  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ALFKI', N'Alfreds Futterkiste', N'Maria Anders')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANATR', N'Ana Trujillo Emparedados y helados', N'Ana Trujillo')  
    INSERT INTO Cust(CustomerID, CompanyName, ContactName) VALUES  
         (N'ANTON', N'Antonio Moreno Taquer??a', N'Antonio Moreno')  
  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(1, N'ALFKI')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(2, N'ANATR')  
    INSERT INTO Ord(OrderID, CustomerID) VALUES(3, N'ANTON')  
    ```  
  
3.  <span data-ttu-id="b5ce7-176">複製上述的 DiffGram，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-176">Copy the DiffGram above and paste it into a text file.</span></span> <span data-ttu-id="b5ce7-177">然後將檔案儲存為 MyDiffGram.xml，放在前述步驟所使用的相同資料夾中。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-177">Save the file as MyDiffGram.xml in the same folder used in the previous step.</span></span>  
  
4.  <span data-ttu-id="b5ce7-178">複製本主題稍早所提供的 DiffGramSchema，並將它貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-178">Copy the DiffGramSchema provided earlier in this topic and paste it into a text file.</span></span> <span data-ttu-id="b5ce7-179">然後將檔案儲存為 DiffGramSchema.xml。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-179">Save the file as DiffGramSchema.xml.</span></span>  
  
5.  <span data-ttu-id="b5ce7-180">建立及使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 來執行 DiffGram。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-180">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the DiffGram.</span></span>  
  
     <span data-ttu-id="b5ce7-181">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-181">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
## <a name="e-applying-updates-by-using-a-diffgram-with-the-diffgrparentid-annotation"></a><span data-ttu-id="b5ce7-182">E.</span><span class="sxs-lookup"><span data-stu-id="b5ce7-182">E.</span></span> <span data-ttu-id="b5ce7-183">搭配 diffgr:parentID 註解使用 DiffGram 來套用更新</span><span class="sxs-lookup"><span data-stu-id="b5ce7-183">Applying updates by using a DiffGram with the diffgr:parentID annotation</span></span>  
 <span data-ttu-id="b5ce7-184">這個範例說明如何使用 DiffGram 的區塊中指定的**parentID**注釋 **\<before>** 來套用更新。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-184">This example illustrates how the **parentID** annotation that is specified in the **\<before>** block of the DiffGram is used in applying the updates.</span></span>  
  
```  
<NewDataSet />  
<diffgr:before>  
   <Order diffgr:id="Order1" msdata:rowOrder="0" OrderID="2" />  
   <Order diffgr:id="Order3" msdata:rowOrder="2" OrderID="4" />  
  
   <OrderDetail diffgr:id="OrderDetail1"   
                diffgr:parentId="Order1"   
                msdata:rowOrder="0"   
                ProductID="13"   
                OrderID="2" />  
   <OrderDetail diffgr:id="OrderDetail3"   
                diffgr:parentId="Order3"  
                ProductID="77"  
                OrderID="4"/>  
</diffgr:before>  
</diffgr:diffgram>  
```  
  
 <span data-ttu-id="b5ce7-185">這個 DiffGram 會指定刪除作業，因為只有一個 **\<before>** 區塊。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-185">This DiffGram specifies a delete operation because there is only a **\<before>** block.</span></span> <span data-ttu-id="b5ce7-186">在 DiffGram 中， **parentID**注釋是用來指定訂單和訂單詳細資料之間的父子式關聯性。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-186">In the DiffGram, the **parentID** annotation is used to specify a parent-child relationship between the orders and order details.</span></span> <span data-ttu-id="b5ce7-187">當 SQLXML 刪除記錄時，它會從這個關聯性所識別的子資料表中刪除記錄，然後從對應的父資料表中刪除記錄。</span><span class="sxs-lookup"><span data-stu-id="b5ce7-187">When SQLXML deletes the records, it deletes records from the child table that is identified by this relationship and then deletes the records from the corresponding parent table.</span></span>  
  
  
