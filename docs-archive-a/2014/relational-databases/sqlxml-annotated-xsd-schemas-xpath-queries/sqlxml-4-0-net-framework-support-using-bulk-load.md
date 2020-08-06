---
title: 在 .NET 環境中使用 SQLXML 大量載入 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, XML Bulk Load
- XML Bulk Load [SQLXML], .NET environment
- .NET Framework [SQLXML], XML Bulk Load
- bulk load [SQLXML], .NET environment
ms.assetid: b85df83b-ba56-43bf-bcdf-b2a6fca43276
author: rothja
ms.author: jroth
ms.openlocfilehash: 6bd1c44a8b56bc5129aeb9843ed9ba814d45742a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706358"
---
# <a name="using-sqlxml-bulk-load-in-the-net-environment"></a><span data-ttu-id="193f5-102">在 .NET 環境中使用 SQLXML 大量載入</span><span class="sxs-lookup"><span data-stu-id="193f5-102">Using SQLXML Bulk Load in the .NET Environment</span></span>
  <span data-ttu-id="193f5-103">本主題說明如何在 .NET 環境中使用 XML 大量載入功能。</span><span class="sxs-lookup"><span data-stu-id="193f5-103">This topic explains how the XML Bulk Load functionality can be used in the .NET environment.</span></span> <span data-ttu-id="193f5-104">如需 XML 大量載入的詳細資訊，請參閱[執行 Xml 資料的大量載入 &#40;SQLXML 4.0&#41;](bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="193f5-104">For detailed information about XML Bulk Load, see [Performing Bulk Load of XML Data &#40;SQLXML 4.0&#41;](bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="193f5-105">若要從 Managed 環境使用 SQLXML 大量載入 COM 物件，您需要將專案參考加入到此物件中。</span><span class="sxs-lookup"><span data-stu-id="193f5-105">To use the SQLXML Bulk Load COM object from a managed environment, you need to add a project reference to this object.</span></span> <span data-ttu-id="193f5-106">這會在大量載入 COM 物件周圍產生 Managed 包裝函數介面。</span><span class="sxs-lookup"><span data-stu-id="193f5-106">This generates a managed wrapper interface around the Bulk Load COM object.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="193f5-107">Managed XML 大量載入不會使用 Managed 資料流，而且在原生資料流周圍需要使用包裝函數。</span><span class="sxs-lookup"><span data-stu-id="193f5-107">Managed XML Bulk load does not work with managed streams and requires a wrapper around native streams.</span></span> <span data-ttu-id="193f5-108">SQLXML 大量載入元件將不會在多執行緒環境 ('[MTAThread]' 屬性) 下執行。</span><span class="sxs-lookup"><span data-stu-id="193f5-108">The SQLXML Bulk Load component will not run in a multi-threaded environment ('[MTAThread]' attribute).</span></span> <span data-ttu-id="193f5-109">如果您嘗試在多執行緒環境中執行大量載入元件，您會收到 InvalidCastException 例外狀況，其中包含下列其他資訊：「介面 SQLXMLBULKLOADLib. Queryinterface 的 QueryInterface 失敗」。</span><span class="sxs-lookup"><span data-stu-id="193f5-109">If you attempt to run the Bulk Load component in a multi-thread environment, you get an InvalidCastException exception with the following additional information: "QueryInterface for interface SQLXMLBULKLOADLib.ISQLXMLBulkLoad failed."</span></span> <span data-ttu-id="193f5-110">因應措施是將包含大量載入物件單一執行緒可供存取的物件 (例如，使用 **[STAThread]** 屬性，如範例) 所示。</span><span class="sxs-lookup"><span data-stu-id="193f5-110">The workaround is to make the object that contains the Bulk Load object single-thread accessible (for example, by using the **[STAThread]** attribute as shown in the sample).</span></span>  
  
 <span data-ttu-id="193f5-111">本主題提供 C# 工作範例應用程式，將 XML 資料大量載入到資料庫中。</span><span class="sxs-lookup"><span data-stu-id="193f5-111">This topic provides a working C# sample application to bulk load XML data in the database.</span></span> <span data-ttu-id="193f5-112">若要建立工作範例，按照下列步驟進行：</span><span class="sxs-lookup"><span data-stu-id="193f5-112">To create a working sample, follow these steps:</span></span>  
  
1.  <span data-ttu-id="193f5-113">建立下列資料表：</span><span class="sxs-lookup"><span data-stu-id="193f5-113">Create the following tables:</span></span>  
  
    ```  
    CREATE TABLE Ord (  
             OrderID     int identity(1,1)  PRIMARY KEY,  
             CustomerID  varchar(5))  
    GO  
    CREATE TABLE Product (  
             ProductID   int identity(1,1) PRIMARY KEY,  
             ProductName varchar(20))  
    GO  
    CREATE TABLE OrderDetail (  
           OrderID     int FOREIGN KEY REFERENCES Ord(OrderID),  
           ProductID   int FOREIGN KEY REFERENCES Product(ProductID),  
                       CONSTRAINT OD_key PRIMARY KEY (OrderID, ProductID))  
    GO  
    ```  
  
2.  <span data-ttu-id="193f5-114">將下列結構描述儲存在檔案 (schema.xml) 中：</span><span class="sxs-lookup"><span data-stu-id="193f5-114">Save the following schema in a file (schema.xml):</span></span>  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
    <xsd:annotation>  
      <xsd:appinfo>  
        <sql:relationship name="OrderOD"  
              parent="Ord"  
              parent-key="OrderID"  
              child="OrderDetail"  
              child-key="OrderID" />  
  
        <sql:relationship name="ODProduct"  
              parent="OrderDetail"  
              parent-key="ProductID"  
              child="Product"  
              child-key="ProductID"   
              inverse="true"/>  
      </xsd:appinfo>  
    </xsd:annotation>  
  
      <xsd:element name="Order" sql:relation="Ord"   
                                sql:key-fields="OrderID" >  
       <xsd:complexType>  
         <xsd:sequence>  
            <xsd:element name="Product" sql:relation="Product"   
                         sql:key-fields="ProductID"  
                         sql:relationship="OrderOD ODProduct">  
              <xsd:complexType>  
                 <xsd:attribute name="ProductID" type="xsd:int" />  
                 <xsd:attribute name="ProductName" type="xsd:string" />  
              </xsd:complexType>  
            </xsd:element>  
         </xsd:sequence>  
            <xsd:attribute name="OrderID"   type="xsd:integer" />   
            <xsd:attribute name="CustomerID"   type="xsd:string" />  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
3.  <span data-ttu-id="193f5-115">將下列範例 XML 文件儲存在檔案 (data.xml) 中：</span><span class="sxs-lookup"><span data-stu-id="193f5-115">Save the following sample XML document in a file (data.xml):</span></span>  
  
    ```  
    <ROOT>    
      <Order OrderID="11" CustomerID="ALFKI">  
        <Product ProductID="11" ProductName="Chai" />  
        <Product ProductID="22" ProductName="Chang" />  
      </Order>  
      <Order OrderID="22" CustomerID="ANATR">  
         <Product ProductID="33" ProductName="Aniseed Syrup" />  
        <Product ProductID="44" ProductName="Gumbo Mix" />  
      </Order>  
    </ROOT>  
    ```  
  
4.  <span data-ttu-id="193f5-116">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="193f5-116">Start Visual Studio.</span></span>  
  
5.  <span data-ttu-id="193f5-117">建立 C# 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="193f5-117">Create a C# console application.</span></span>  
  
6.  <span data-ttu-id="193f5-118">從 [**專案**] 功能表中，選取 [**加入參考**]。</span><span class="sxs-lookup"><span data-stu-id="193f5-118">From the **Project** menu, select **Add Reference**.</span></span>  
  
7.  <span data-ttu-id="193f5-119">在 [ **COM** ] 索引標籤中，選取 [ **Microsoft SQLXML Bulkload 4.0 型別程式庫**] ( # A0) 然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="193f5-119">In the **COM** tab, select **Microsoft SQLXML Bulkload 4.0 Type Library** (xblkld4.dll) and click **OK**.</span></span> <span data-ttu-id="193f5-120">您會看到在專案中建立的**SQLXMLBULKLOADLib**元件。</span><span class="sxs-lookup"><span data-stu-id="193f5-120">You will see the **Interop.SQLXMLBULKLOADLib** assembly created in the project.</span></span>  
  
8.  <span data-ttu-id="193f5-121">將 Main() 方法取代成下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="193f5-121">Replace the Main() method with the following code.</span></span> <span data-ttu-id="193f5-122">將**ConnectionString**屬性和檔案路徑更新為架構和資料檔案。</span><span class="sxs-lookup"><span data-stu-id="193f5-122">Update the **ConnectionString** property and the file path to the schema and data files.</span></span>  
  
    ```  
    [STAThread]  
       static void Main(string[] args)  
       {     
             try  
             {  
                SQLXMLBULKLOADLib.SQLXMLBulkLoad4Class objBL = new SQLXMLBULKLOADLib.SQLXMLBulkLoad4Class();  
                objBL.ConnectionString = "Provider=sqloledb;server=server;database=databaseName;integrated security=SSPI";  
                objBL.ErrorLogFile = "error.xml";  
                objBL.KeepIdentity = false;  
                objBL.Execute ("schema.xml","data.xml");  
             }  
             catch(Exception e)  
             {  
             Console.WriteLine(e.ToString());  
             }  
       }  
    ```  
  
9. <span data-ttu-id="193f5-123">若要將 XML 載入到您所建立的資料表中，建立並執行專案。</span><span class="sxs-lookup"><span data-stu-id="193f5-123">To load the XML in the table you created, build and run the project.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="193f5-124">大量載入元件 (xblkld4.dll) 的參考也可以使用 tlbimp.exe 工具加入，該工具是 .NET Framework 的一部分。</span><span class="sxs-lookup"><span data-stu-id="193f5-124">The reference to the Bulk Load component (xblkld4.dll) can also be added using the tlbimp.exe tool, which is available as part of .NET framework.</span></span> <span data-ttu-id="193f5-125">此工具會針對原生 DLL (xblkld4.dll) 建立 Managed 包裝函數，然後就可以在任何 .NET 專案中使用。</span><span class="sxs-lookup"><span data-stu-id="193f5-125">This tool creates a managed wrapper for the native DLL (xblkld4.dll), which can then be used in any .NET project.</span></span> <span data-ttu-id="193f5-126">例如：</span><span class="sxs-lookup"><span data-stu-id="193f5-126">For example:</span></span>  
  
    ```  
    c:\>tlbimp xblkld4.dll  
    ```  
  
     <span data-ttu-id="193f5-127">這會建立您可以在 .NET Framework 專案中使用的 Managed 包裝函數 DLL (SQLXMLBULKLOADLib.dll)。</span><span class="sxs-lookup"><span data-stu-id="193f5-127">This creates the managed wrapper DLL (SQLXMLBULKLOADLib.dll) that you can use in the .NET Framework project.</span></span> <span data-ttu-id="193f5-128">在 .NET Framework 中，您可以將專案參考加入到新建立的 DLL。</span><span class="sxs-lookup"><span data-stu-id="193f5-128">In the .NET Framework, you add project reference to the newly created DLL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="193f5-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="193f5-129">See Also</span></span>  
 [<span data-ttu-id="193f5-130">執行 XML 資料的大量載入 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="193f5-130">Performing Bulk Load of XML Data &#40;SQLXML 4.0&#41;</span></span>](bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)  
  
  
