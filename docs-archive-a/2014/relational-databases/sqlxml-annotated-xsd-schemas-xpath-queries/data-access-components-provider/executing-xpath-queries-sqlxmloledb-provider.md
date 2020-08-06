---
title: " (SQLXMLOLEDB 提供者) 執行 XPath 查詢 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXMLOLEDB Provider, executing XPath queries
- queries [SQLXML], SQLXMLOLEDB Provider
- Base Path property
- XPath queries [SQLXML], SQLXMLOLEDB Provider
- Mapping Schema property
ms.assetid: 19063222-dc9c-48ae-a55f-778103674a9e
author: rothja
ms.author: jroth
ms.openlocfilehash: 667bc8dfd95c37c0a10c0bc68f3007e7d04533e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700909"
---
# <a name="executing-xpath-queries-sqlxmloledb-provider"></a><span data-ttu-id="3e67e-102">執行 XPath 查詢 (SQLXMLOLEDB 提供者)</span><span class="sxs-lookup"><span data-stu-id="3e67e-102">Executing XPath Queries (SQLXMLOLEDB Provider)</span></span>
  <span data-ttu-id="3e67e-103">此範例示範如何使用下列 SQLXMLOLEDB 提供者專屬的屬性：</span><span class="sxs-lookup"><span data-stu-id="3e67e-103">This example illustrates the use of the following SQLXMLOLEDB Provider-specific properties:</span></span>  
  
-   `ClientSideXML`  
  
-   `Base Path`  
  
-   `Mapping Schema`  
  
 <span data-ttu-id="3e67e-104">在這個範例 ADO 應用程式中，已針對 XSD 對應結構描述 (MySchema.xml) 指定了 XPath 查詢 (root)。</span><span class="sxs-lookup"><span data-stu-id="3e67e-104">In this sample ADO application, an XPath query (root) is specified against an XSD mapping schema (MySchema.xml).</span></span> <span data-ttu-id="3e67e-105">此架構具有 **\<Contacts>** 具有**ContactID**、 **FirstName**和**LastName**屬性的元素。</span><span class="sxs-lookup"><span data-stu-id="3e67e-105">The schema has a **\<Contacts>** element with **ContactID**, **FirstName**, and **LastName** attributes.</span></span> <span data-ttu-id="3e67e-106">在此結構描述中，系統會進行預設對應：元素名稱會對應至具有相同名稱的資料表，而且屬於簡單類型的屬性會對應至具有相同名稱的資料行。</span><span class="sxs-lookup"><span data-stu-id="3e67e-106">In the schema, default mapping takes place: an element name maps to the table with the same name, and attributes of simple type map to the columns with the same names.</span></span>  
  
```  
<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'  
   xmlns:sql='urn:schemas-microsoft-com:mapping-schema'>  
 <xsd:element name= 'root' sql:is-constant='1'>   
    <xsd:complexType>  
       <xsd:sequence>  
         <xsd:element ref = 'Contacts'/>  
       </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
  <xsd:element name='Contacts' sql:relation='Person.Contact'>   
     <xsd:complexType>  
          <xsd:attribute name='ContactID' type='xsd:integer' />  
          <xsd:attribute name='FirstName' type='xsd:string'/>   
          <xsd:attribute name='LastName' type='xsd:string' />   
     </xsd:complexType>  
   </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="3e67e-107">對應架構屬性會提供 XPath 查詢執行時所依據的對應架構。</span><span class="sxs-lookup"><span data-stu-id="3e67e-107">The Mapping Schema property provides the mapping schema against which the XPath query is executed.</span></span> <span data-ttu-id="3e67e-108">此對應結構描述可能是 XSD 或 XDR 結構描述。</span><span class="sxs-lookup"><span data-stu-id="3e67e-108">The mapping schema can be an XSD or XDR schema.</span></span> <span data-ttu-id="3e67e-109">[基底路徑] 屬性會提供對應架構的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="3e67e-109">The Base Path property provides the file path to the mapping schema.</span></span>  
  
 <span data-ttu-id="3e67e-110">ClientSideXML 屬性設定為 True。</span><span class="sxs-lookup"><span data-stu-id="3e67e-110">The ClientSideXML property is set to True.</span></span> <span data-ttu-id="3e67e-111">因此，XML 文件會在用戶端上產生。</span><span class="sxs-lookup"><span data-stu-id="3e67e-111">Therefore, the XML document is generated on the client.</span></span>  
  
 <span data-ttu-id="3e67e-112">在應用程式中，會直接指定 XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="3e67e-112">In the application, an XPath query is specified directly.</span></span> <span data-ttu-id="3e67e-113">因此，必須包含 XPath Dialect {ec2a4293-e898-11d2-b1b7-00c04f680c56}。</span><span class="sxs-lookup"><span data-stu-id="3e67e-113">Therefore, the XPath dialect {ec2a4293-e898-11d2-b1b7-00c04f680c56} must be included.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3e67e-114">在程式碼中，您必須於連接字串內提供 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="3e67e-114">In the code, you must provide the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span> <span data-ttu-id="3e67e-115">此外，這個範例會指定針對資料提供者使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) (需要安裝其他網路用戶端軟體)。</span><span class="sxs-lookup"><span data-stu-id="3e67e-115">Also, this example specifies the use of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) for the data provider which requires additional network client software to be installed.</span></span> <span data-ttu-id="3e67e-116">如需詳細資訊，請參閱[SQL Server Native Client 的系統需求](../../native-client/system-requirements-for-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="3e67e-116">For more information, see [System Requirements for SQL Server Native Client](../../native-client/system-requirements-for-sql-server-native-client.md).</span></span>  
  
```  
Option Explicit  
Sub main()  
Dim oTestStream As New ADODB.Stream  
Dim oTestConnection As New ADODB.Connection  
Dim oTestCommand As New ADODB.Command  
  
oTestConnection.Open "provider=SQLXMLOLEDB.4.0;data provider=SQLNCLI11;data source=SqlServerName;initial catalog=AdventureWorks;Integrated Security= SSPI;"  
  
oTestCommand.ActiveConnection = oTestConnection  
oTestCommand.Properties("ClientSideXML") = True  
  
oTestCommand.CommandText = "root"  
oTestStream.Open  
oTestCommand.Dialect = "{ec2a4293-e898-11d2-b1b7-00c04f680c56}"  
oTestCommand.Properties("Output Stream").Value = oTestStream  
oTestCommand.Properties("Base Path").Value = "c:\Schemas\SQLXML4\XPathDirect\"  
oTestCommand.Properties("Mapping Schema").Value = "mySchema.xml"  
oTestCommand.Properties("Output Encoding") = "utf-8"  
oTestCommand.Execute , , adExecuteStream  
oTestStream.Position = 0  
oTestStream.Charset = "utf-8"  
Debug.Print oTestStream.ReadText(adReadAll)  
  
End Sub  
Sub Form_Load()  
 main  
End Sub  
```  
  
  
