---
title: 使用 SQLXML Managed 類別執行 DiffGram |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- DiffGrams [SQLXML], Managed Classes
- SQLXML Managed Classes, DiffGrams
- Managed Classes [SQLXML], DiffGrams
- SQLXML, Managed Classes
ms.assetid: 81c687ca-8c9f-4f58-801f-8dabcc508a06
author: rothja
ms.author: jroth
ms.openlocfilehash: f36127c37eea73a2872d4bf0aef7172a88e430a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596594"
---
# <a name="executing-a-diffgram-by-using-sqlxml-managed-classes"></a><span data-ttu-id="a0fa8-102">使用 SQLXML Managed 類別執行 DiffGram</span><span class="sxs-lookup"><span data-stu-id="a0fa8-102">Executing a DiffGram by Using SQLXML Managed Classes</span></span>
  <span data-ttu-id="a0fa8-103">這個範例示範如何在 .NET Framework 環境中執行 DiffGram 檔案 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] ，使用 (的 Sqlxml Managed 類別，將資料更新套用到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料表。 sqlxml) 。</span><span class="sxs-lookup"><span data-stu-id="a0fa8-103">This example shows how to execute a DiffGram file in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework environment to apply data updates to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tables using SQLXML Managed Classes (Microsoft.Data.SqlXml).</span></span>  
  
 <span data-ttu-id="a0fa8-104">在此範例中，DiffGram 會更新客戶 ALFKI 的客戶資訊 (CompanyName 和 ContactName)。</span><span class="sxs-lookup"><span data-stu-id="a0fa8-104">In this example, the DiffGram updates customer information (CompanyName and ContactName) for customer ALFKI.</span></span>  
  
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
  
 <span data-ttu-id="a0fa8-105">**\<before>** 區塊包含 **\<Customer>** 元素 (**diffgr： Id = "Customer1"**) 。</span><span class="sxs-lookup"><span data-stu-id="a0fa8-105">The **\<before>** block includes a **\<Customer>** element (**diffgr:id="Customer1"**).</span></span> <span data-ttu-id="a0fa8-106">**\<DataInstance>** 區塊包含 **\<Customer>** 具有相同**識別碼**的對應元素。**\<customer>** 中的元素 **\<NewDataSet>** 也會指定**diffgr： hasChanges = "modified"**。</span><span class="sxs-lookup"><span data-stu-id="a0fa8-106">The **\<DataInstance>** block includes the corresponding **\<Customer>** element with same **id**. The **\<customer>** element in the **\<NewDataSet>** also specifies **diffgr:hasChanges="modified"**.</span></span> <span data-ttu-id="a0fa8-107">這表示更新作業，而且 Cust 資料表中的客戶記錄也會隨之更新。</span><span class="sxs-lookup"><span data-stu-id="a0fa8-107">This indicates an update operation, and the customer record in the Cust table is updated accordingly.</span></span> <span data-ttu-id="a0fa8-108">請注意，如果未指定**diffgr： hasChanges**屬性，DiffGram 處理邏輯會忽略這個元素，而且不會執行任何更新。</span><span class="sxs-lookup"><span data-stu-id="a0fa8-108">Note that if the **diffgr:hasChanges** attribute is not specified, the DiffGram processing logic ignores this element and no updates are performed.</span></span>  
  
 <span data-ttu-id="a0fa8-109">以下是 c # 教學課程應用程式的程式碼，它會示範如何使用 SQLXML Managed 類別來執行上述 DiffGram，並更新兩個數據表 (使用者，Ord) 您也會在**tempdb**資料庫中建立。</span><span class="sxs-lookup"><span data-stu-id="a0fa8-109">The following is code for a C# tutorial application that shows how to use the SQLXML Managed Classes to execute the above DiffGram and update two tables (Cust, Ord) you will also create in the **tempdb** database.</span></span>  
  
```  
using System;  
using System.Data;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
   static string ConnString = "Provider=SQLOLEDB;Server=MyServer;database=tempdb;Integrated Security=SSPI;";  
   public static int testParams()  
   {  
      SqlXmlAdapter ad;  
      // Need a memory stream to hold diff gram temporarily  
      MemoryStream ms = new MemoryStream();  
      SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
      cmd.RootTag = "ROOT";  
      cmd.CommandStream = new FileStream("MyDiffgram.xml", FileMode.Open, FileAccess.Read);  
      cmd.CommandType = SqlXmlCommandType.DiffGram;  
      cmd.SchemaPath = "DiffGramSchema.xml";  
      // Load data set  
      DataSet ds = new DataSet();  
      ad = new SqlXmlAdapter(cmd);  
      ad.Fill(ds);  
      ad.Update(ds);  
      return 0;  
   }  
   public static int Main(String[] args)  
   {  
      testParams();  
      return 0;  
   }  
}  
```  
  
### <a name="to-test-the-application"></a><span data-ttu-id="a0fa8-110">若要測試應用程式</span><span class="sxs-lookup"><span data-stu-id="a0fa8-110">To test the application</span></span>  
  
1.  <span data-ttu-id="a0fa8-111">確認用戶端電腦上是否安裝 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="a0fa8-111">Ensure that the .NET Framework is installed on your computer.</span></span>  
  
2.  <span data-ttu-id="a0fa8-112">將下列 XSD 結構描述 (DiffGramSchema.xml) 儲存在資料夾中：</span><span class="sxs-lookup"><span data-stu-id="a0fa8-112">Save the following XSD schema (DiffGramSchema.xml) in a folder:</span></span>  
  
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
  
3.  <span data-ttu-id="a0fa8-113">在**tempdb**資料庫中建立這些資料表。</span><span class="sxs-lookup"><span data-stu-id="a0fa8-113">Create these tables in the **tempdb** database.</span></span>  
  
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
  
4.  <span data-ttu-id="a0fa8-114">加入這個範例資料：</span><span class="sxs-lookup"><span data-stu-id="a0fa8-114">Add this sample data:</span></span>  
  
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
  
5.  <span data-ttu-id="a0fa8-115">複製上述的 DiffGram，並將其貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="a0fa8-115">Copy the DiffGram above and paste it into a text file.</span></span> <span data-ttu-id="a0fa8-116">然後在步驟 1 所使用的相同資料夾中，將檔案儲存為 MyDiffGram.xml。</span><span class="sxs-lookup"><span data-stu-id="a0fa8-116">Save the file as MyDiffGram.xml in the same folder used in step 1.</span></span>  
  
6.  <span data-ttu-id="a0fa8-117">將以上提供的 C# 程式碼 (DiffgramSample.cs) 儲存在上述步驟中儲存 DiffGramSchema.xml 和 MyDiffGram.xml 所在的相同資料夾中。</span><span class="sxs-lookup"><span data-stu-id="a0fa8-117">Save the C# code (DiffgramSample.cs) that is provided above in the same folder in which the DiffGramSchema.xml and MyDiffGram.xml were stored in previous steps.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a0fa8-118">您需要將連接字串中的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體名稱從 '`MyServer`' 更新為已安裝之 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的實際名稱。</span><span class="sxs-lookup"><span data-stu-id="a0fa8-118">You will need to update the name of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance in the connection string from '`MyServer`' to the actual name of your installed instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="a0fa8-119">如果您將檔案儲存在不同的資料夾中，您將需要編輯程式碼，然後為對應的結構描述指定適當的目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="a0fa8-119">If you store the files in a different folder, you will have to edit the code and specify the appropriate directory path for the mapping schema.</span></span>  
  
7.  <span data-ttu-id="a0fa8-120">編譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="a0fa8-120">Compile the code.</span></span> <span data-ttu-id="a0fa8-121">若要在命令提示字元下編譯程式碼，請使用：</span><span class="sxs-lookup"><span data-stu-id="a0fa8-121">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DiffgramSample.cs  
    ```  
  
     <span data-ttu-id="a0fa8-122">這樣會建立可執行檔 (DiffgramSample.exe)。</span><span class="sxs-lookup"><span data-stu-id="a0fa8-122">This creates an executable (DiffgramSample.exe).</span></span>  
  
8.  <span data-ttu-id="a0fa8-123">在命令提示字元中，執行 DiffgramSample.exe。</span><span class="sxs-lookup"><span data-stu-id="a0fa8-123">At the command prompt, execute DiffgramSample.exe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0fa8-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0fa8-124">See Also</span></span>  
 [<span data-ttu-id="a0fa8-125">&#40;SQLXML 4.0&#41;的 DiffGram 範例</span><span class="sxs-lookup"><span data-stu-id="a0fa8-125">DiffGram Examples &#40;SQLXML 4.0&#41;</span></span>](diffgram-examples-sqlxml-4-0.md)  
  
  
