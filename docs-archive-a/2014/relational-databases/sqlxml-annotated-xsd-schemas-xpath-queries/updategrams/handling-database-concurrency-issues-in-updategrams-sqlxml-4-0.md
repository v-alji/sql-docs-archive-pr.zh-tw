---
title: 處理 Updategram 中的資料庫並行問題 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- <before> block
- low concurrency protection
- database concurrency [SQLXML]
- timestamp column [SQLXML]
- updategrams [SQLXML], database concurrency
- high concurrency protection [SQLXML]
- optimistic concurrency control
- concurrency [SQLXML]
- intermediate concurrency protection [SQLXML]
ms.assetid: d4b908d1-b25b-4ad9-8478-9cd882e8c44e
author: rothja
ms.author: jroth
ms.openlocfilehash: dd808b2688e8bf05149a5454bee91123878fb2ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597748"
---
# <a name="handling-database-concurrency-issues-in-updategrams-sqlxml-40"></a><span data-ttu-id="4fbd7-102">在 Updategram (SQLXML 4.0) 中處理資料庫並行的問題</span><span class="sxs-lookup"><span data-stu-id="4fbd7-102">Handling Database Concurrency Issues in Updategrams (SQLXML 4.0)</span></span>
  <span data-ttu-id="4fbd7-103">與其他資料庫更新機制一樣，Updategram 必須處理在多使用者環境中的資料並行更新。</span><span class="sxs-lookup"><span data-stu-id="4fbd7-103">Like other database update mechanisms, updategrams must deal with concurrent updates to data in a multiuser environment.</span></span> <span data-ttu-id="4fbd7-104">Updategram 使用開放式並行控制，該控制使用選取欄位資料的比較為快照集，以確保自從要更新的資料從資料庫讀取後，尚未受到其他使用者應用程式改變。</span><span class="sxs-lookup"><span data-stu-id="4fbd7-104">Updategrams use the Optimistic Concurrency Control, which uses comparison of select field data as snapshots to ensure that the data to be updated has not been altered by another user application since it was read from the database.</span></span> <span data-ttu-id="4fbd7-105">Updategram 在 updategram 的區塊中包含這些快照集值 **\<before>** 。</span><span class="sxs-lookup"><span data-stu-id="4fbd7-105">Updategrams include these snapshot values in the **\<before>** block of the updategrams.</span></span> <span data-ttu-id="4fbd7-106">在更新資料庫之前，updategram 會根據目前在資料庫中的值，檢查區塊中指定的值， **\<before>** 以確保更新有效。</span><span class="sxs-lookup"><span data-stu-id="4fbd7-106">Before updating the database, the updategram checks the values that are specified in the **\<before>** block against the values currently in the database to ensure that the update is valid.</span></span>  
  
 <span data-ttu-id="4fbd7-107">開放式並行控制在 Updategram 中提供三種保護等級：低 (無)、中和高。</span><span class="sxs-lookup"><span data-stu-id="4fbd7-107">The Optimistic Concurrency Control offers three levels of protection in an updategram: low (none), intermediate, and high.</span></span> <span data-ttu-id="4fbd7-108">您可以藉由指定 Updategram，決定需要哪種保護等級。</span><span class="sxs-lookup"><span data-stu-id="4fbd7-108">You can decide what level of protection you need by specifying the updategram accordingly.</span></span>  
  
## <a name="lowest-level-of-protection"></a><span data-ttu-id="4fbd7-109">最低保護等級</span><span class="sxs-lookup"><span data-stu-id="4fbd7-109">Lowest Level of Protection</span></span>  
 <span data-ttu-id="4fbd7-110">這個等級是一種盲目更新 (Blind Update)，在這個等級中，會直接處理更新，而不會參考自從上一次讀取資料庫之後所做的其他更新。</span><span class="sxs-lookup"><span data-stu-id="4fbd7-110">This level is a blind update, in which the update is processed without reference to other updates that have been made since the database was last read.</span></span> <span data-ttu-id="4fbd7-111">在這種情況下，您只需在區塊中指定 (s) 的主鍵 **\<before>** 資料行來識別記錄，並在區塊中指定更新的資訊 **\<after>** 。</span><span class="sxs-lookup"><span data-stu-id="4fbd7-111">In such a case, you specify only the primary key column(s) in the **\<before>** block to identify the record, and you specify the updated information in the **\<after>** block.</span></span>  
  
 <span data-ttu-id="4fbd7-112">例如，在下列的 Updategram 中的新連絡電話號碼是正確的，無論之前的電話號碼是幾號。</span><span class="sxs-lookup"><span data-stu-id="4fbd7-112">For example, the new contact phone number in the following updategram is correct, regardless of what the phone number was previously.</span></span> <span data-ttu-id="4fbd7-113">請注意， **\<before>** 區塊如何只指定主要索引鍵資料行 (ContactID) 。</span><span class="sxs-lookup"><span data-stu-id="4fbd7-113">Notice how the **\<before>** block specifies only the primary key column (ContactID).</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
<updg:before>  
   <Person.Contact ContactID="1" />  
</updg:before>  
<updg:after>  
   <Person.Contact ContactID="1" Phone="111-111-1111" />  
</updg:after>  
</updg:sync>  
</ROOT>  
```  
  
## <a name="intermediate-level-of-protection"></a><span data-ttu-id="4fbd7-114">中級保護等級</span><span class="sxs-lookup"><span data-stu-id="4fbd7-114">Intermediate Level of Protection</span></span>  
 <span data-ttu-id="4fbd7-115">在這個保護等級中，Updategram 會比較使用資料庫資料行中的值所更新的目前值，以確定自從您的交易讀取記錄之後，值沒有受到其他交易改變。</span><span class="sxs-lookup"><span data-stu-id="4fbd7-115">In this level of protection, the updategram compares the current value(s) of the data being updated with the value(s) in the database column(s) to ensure that the values have not been changed by some other transaction since the record was read by your transaction.</span></span>  
  
 <span data-ttu-id="4fbd7-116">您可以在區塊中指定 (s) 的主鍵資料行，以及要更新的資料行 () ，藉此取得此層級的保護 **\<before>** 。</span><span class="sxs-lookup"><span data-stu-id="4fbd7-116">You can get this level of protection by specifying the primary key column(s) and the column(s) that you are updating in the **\<before>** block.</span></span>  
  
 <span data-ttu-id="4fbd7-117">例如，這個 Updategram 為 ContactID 為 1 的連絡人，變更了 Person.Contact 資料表 Phone 資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="4fbd7-117">For example, this updategram changes the value in the Phone column of the Person.Contact table for the contact with ContactID of 1.</span></span> <span data-ttu-id="4fbd7-118">**\<before>** 區塊會指定**Phone**屬性，以確保此屬性值符合資料庫中對應資料行的值，然後再套用更新的值。</span><span class="sxs-lookup"><span data-stu-id="4fbd7-118">The **\<before>** block specifies the **Phone** attribute to ensure that this attribute value matches the value in the corresponding column in the database before applying the updated value.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
<updg:before>  
   <Person.Contact ContactID="1" Phone="398-555-0132" />  
</updg:before>  
<updg:after>  
   <Person.Contact ContactID="1" Phone="111-111-1111" />  
</updg:after>  
</updg:sync>  
</ROOT>  
```  
  
## <a name="high-level-of-protection"></a><span data-ttu-id="4fbd7-119">高級保護等級</span><span class="sxs-lookup"><span data-stu-id="4fbd7-119">High Level of Protection</span></span>  
 <span data-ttu-id="4fbd7-120">一種高級保護等級，可以確定記錄自從您的應用程式上次讀取之後是維持原狀的 (也就是說，自從您的應用程式讀取記錄後，該記錄尚未由其他交易改變)。</span><span class="sxs-lookup"><span data-stu-id="4fbd7-120">A high level of protection ensures that the record remains the same since your application last read that record (that is, since your application has read the record, it has not been changed by any other transaction).</span></span>  
  
 <span data-ttu-id="4fbd7-121">您可以藉由兩種方法，針對並行更新取得這個保護等級：</span><span class="sxs-lookup"><span data-stu-id="4fbd7-121">There are two ways you can get this high level of protection against concurrent updates:</span></span>  
  
-   <span data-ttu-id="4fbd7-122">在區塊的資料表中指定其他 **\<before>** 資料行。</span><span class="sxs-lookup"><span data-stu-id="4fbd7-122">Specify additional columns in the table in the **\<before>** block.</span></span>  
  
     <span data-ttu-id="4fbd7-123">如果您在區塊中指定其他 **\<before>** 資料行，則 updategram 會將這些資料行所指定的值與資料庫中的值相比較，然後再套用更新。</span><span class="sxs-lookup"><span data-stu-id="4fbd7-123">If you specify additional columns in the **\<before>** block, the updategram compares the values that are specified for these columns with the values that were in the database before applying the update.</span></span> <span data-ttu-id="4fbd7-124">如果任何記錄資料行在您的交易讀取記錄之後變更的話，則 Updategram 不會執行更新。</span><span class="sxs-lookup"><span data-stu-id="4fbd7-124">If any of the record columns has changed since your transaction read the record, the updategram does not perform the update.</span></span>  
  
     <span data-ttu-id="4fbd7-125">例如，下列 updategram 會更新 shift 名稱，但會在區塊中指定額外的資料行 (StartTime、EndTime) ，藉以 **\<before>** 針對並行更新要求更高的保護層級。</span><span class="sxs-lookup"><span data-stu-id="4fbd7-125">For example, the following updategram updates the shift name, but specifies additional columns (StartTime,EndTime) in the **\<before>** block, thereby requesting a higher level of protection against concurrent updates.</span></span>  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
    <updg:sync >  
    <updg:before>  
       <HumanResources.Shift ShiftID="1"   
                 Name="Day"   
                 StartTime="1900-01-01 07:00:00.000"   
                 EndTime="1900-01-01 15:00:00.000" />  
    </updg:before>  
    <updg:after>  
       <HumanResources.Shift Name="Morning" />  
    </updg:after>  
    </updg:sync>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="4fbd7-126">這個範例會藉由指定區塊中記錄的所有資料行值，指定最高層級的保護 **\<before>** 。</span><span class="sxs-lookup"><span data-stu-id="4fbd7-126">This example specifies the highest level of protection by specifying all column values for the record in the **\<before>** block.</span></span>  
  
-   <span data-ttu-id="4fbd7-127">如果區塊中有) ，請指定 (的時間戳記 **\<before>** 資料行。</span><span class="sxs-lookup"><span data-stu-id="4fbd7-127">Specify the timestamp column (if available) in the **\<before>** block.</span></span>  
  
     <span data-ttu-id="4fbd7-128">除了指定> 區塊中的所有記錄資料行之外 `<before` ，您可以只指定時間戳記資料行 (如果資料表有一個) ，以及區塊中的主鍵資料行 (s) **\<before>** 。</span><span class="sxs-lookup"><span data-stu-id="4fbd7-128">Instead of specifying all the record columns in the `<before`> block, you can just specify the timestamp column (if the table has one) along with the primary key column(s) in the **\<before>** block.</span></span> <span data-ttu-id="4fbd7-129">資料庫會在每一筆記錄更新後，將時間戳記資料行更新為唯一值。</span><span class="sxs-lookup"><span data-stu-id="4fbd7-129">The database updates the timestamp column to a unique value after each update of the record.</span></span> <span data-ttu-id="4fbd7-130">在這個狀況下，Updategram 會比較時間戳記值與資料庫中對應的值。</span><span class="sxs-lookup"><span data-stu-id="4fbd7-130">In this case, the updategram compares the value of the timestamp with the corresponding value in the database.</span></span> <span data-ttu-id="4fbd7-131">儲存在資料庫中的時間戳記值是二進位值。</span><span class="sxs-lookup"><span data-stu-id="4fbd7-131">The timestamp value stored in the database is a binary value.</span></span> <span data-ttu-id="4fbd7-132">因此，時間戳記資料行必須在結構描述中指定為 `dt:type="bin.hex"`、`dt:type="bin.base64"` 或 `sql:datatype="timestamp"`。</span><span class="sxs-lookup"><span data-stu-id="4fbd7-132">Therefore, the timestamp column must be specified in the schema as `dt:type="bin.hex"`, `dt:type="bin.base64"`, or `sql:datatype="timestamp"`.</span></span> <span data-ttu-id="4fbd7-133"> (您可以指定 `xml` 資料類型或 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料類型。 ) </span><span class="sxs-lookup"><span data-stu-id="4fbd7-133">(You can specify either the `xml` data type or the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data type.)</span></span>  
  
#### <a name="to-test-the-updategram"></a><span data-ttu-id="4fbd7-134">若要測試 Updategram</span><span class="sxs-lookup"><span data-stu-id="4fbd7-134">To test the updategram</span></span>  
  
1.  <span data-ttu-id="4fbd7-135">在**tempdb**資料庫中建立此資料表：</span><span class="sxs-lookup"><span data-stu-id="4fbd7-135">Create this table in the **tempdb** database:</span></span>  
  
    ```  
    USE tempdb  
    CREATE TABLE Customer (  
                 CustomerID  varchar(5),  
                 ContactName varchar(20),  
                 LastUpdated timestamp)  
    ```  
  
2.  <span data-ttu-id="4fbd7-136">新增這個範例記錄：</span><span class="sxs-lookup"><span data-stu-id="4fbd7-136">Add this sample record:</span></span>  
  
    ```  
    INSERT INTO Customer (CustomerID, ContactName) VALUES   
                         ('C1', 'Andrew Fuller')  
    ```  
  
3.  <span data-ttu-id="4fbd7-137">複製下列 XSD 結構描述並貼到 [記事本] 中，</span><span class="sxs-lookup"><span data-stu-id="4fbd7-137">Copy the following XSD schema and paste it into Notepad.</span></span> <span data-ttu-id="4fbd7-138">將它儲存為 ConcurrencySampleSchema.xml：</span><span class="sxs-lookup"><span data-stu-id="4fbd7-138">Save it as ConcurrencySampleSchema.xml:</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
      <xsd:element name="Customer" sql:relation="Customer" >  
       <xsd:complexType>  
            <xsd:attribute name="CustomerID"    
                           sql:field="CustomerID"   
                           type="xsd:string" />   
  
            <xsd:attribute name="ContactName"    
                           sql:field="ContactName"   
                           type="xsd:string" />  
  
            <xsd:attribute name="LastUpdated"   
                           sql:field="LastUpdated"   
                           type="xsd:hexBinary"   
                 sql:datatype="timestamp" />  
  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
4.  <span data-ttu-id="4fbd7-139">複製下列 Updategram 程式碼並貼到 [記事本] 中，然後將它儲存為 ConcurrencySampleTemplate.xml 並放在與前一個步驟中所建立的結構描述一樣的目錄中。</span><span class="sxs-lookup"><span data-stu-id="4fbd7-139">Copy the following updategram code into Notepad and save it as ConcurrencySampleTemplate.xml in the same directory where you saved the schema created in the previous step.</span></span> <span data-ttu-id="4fbd7-140">(請注意，以下 LastUpdated 的時間戳記值與您的範例 Customer 資料表中的值不同，所以請從資料表複製 LastUpdated 的實際值，並貼至 Updategram 中)。</span><span class="sxs-lookup"><span data-stu-id="4fbd7-140">(Note the timestamp value below for LastUpdated will differ in your example Customer table, so copy the actual value for LastUpdated from the table and paste it into the updategram.)</span></span>  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
    <updg:sync mapping-schema="SampleSchema.xml" >  
    <updg:before>  
       <Customer CustomerID="C1"   
                 LastUpdated = "0x00000000000007D1" />  
    </updg:before>  
    <updg:after>  
       <Customer ContactName="Robert King" />  
    </updg:after>  
    </updg:sync>  
    </ROOT>  
    ```  
  
5.  <span data-ttu-id="4fbd7-141">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="4fbd7-141">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="4fbd7-142">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="4fbd7-142">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="4fbd7-143">這是相等的 XDR 結構描述：</span><span class="sxs-lookup"><span data-stu-id="4fbd7-143">This is the equivalent XDR schema:</span></span>  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
<ElementType name="Customer" sql:relation="Customer" >  
    <AttributeType name="CustomerID" />  
    <AttributeType name="ContactName" />  
    <AttributeType name="LastUpdated"  dt:type="bin.hex"   
                                       sql:datatype="timestamp" />  
    <attribute type="CustomerID" />  
    <attribute type="ContactName" />  
    <attribute type="LastUpdated" />  
</ElementType>  
</Schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4fbd7-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fbd7-144">See Also</span></span>  
 [<span data-ttu-id="4fbd7-145">&#40;SQLXML 4.0&#41;的 Updategram 安全性考慮</span><span class="sxs-lookup"><span data-stu-id="4fbd7-145">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
