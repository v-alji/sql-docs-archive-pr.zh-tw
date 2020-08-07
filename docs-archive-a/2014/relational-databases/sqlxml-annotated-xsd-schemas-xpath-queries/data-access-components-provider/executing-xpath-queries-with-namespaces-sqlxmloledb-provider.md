---
title: 使用命名空間執行 XPath 查詢 (SQLXMLOLEDB 提供者) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXMLOLEDB Provider, executing XPath queries
- namespaces property
- queries [SQLXML], SQLXMLOLEDB Provider
- XPath queries [SQLXML], namespaces
- XPath queries [SQLXML], SQLXMLOLEDB Provider
- namespaces [SQLXML], XPath queries
ms.assetid: 024a4b7d-435d-47ba-9e80-2c2f640108f5
author: rothja
ms.author: jroth
ms.openlocfilehash: ff692b49a4c32c14655af3a9eb07071dc60ba2a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700894"
---
# <a name="executing-xpath-queries-with-namespaces-sqlxmloledb-provider"></a><span data-ttu-id="d6ce5-102">執行含有命名空間的 XPath 查詢 (SQLXMLOLEDB 提供者)</span><span class="sxs-lookup"><span data-stu-id="d6ce5-102">Executing XPath Queries with Namespaces (SQLXMLOLEDB Provider)</span></span>
  <span data-ttu-id="d6ce5-103">XPath 查詢可以包含命名空間。</span><span class="sxs-lookup"><span data-stu-id="d6ce5-103">XPath queries can include namespaces.</span></span> <span data-ttu-id="d6ce5-104">如果結構描述元素會限定命名空間 (亦即，如果它們包含目標命名空間)，針對此結構描述進行的 XPath 查詢就必須指定此命名空間。</span><span class="sxs-lookup"><span data-stu-id="d6ce5-104">If the schema elements are namespace qualified (that is, if they include a target namespace), XPath queries against the schema must specify this namespace.</span></span>  
  
 <span data-ttu-id="d6ce5-105">由於 SQLXML 4.0 不支援使用萬用字元 (\*)，所以您必須使用命名空間前置詞來指定 XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="d6ce5-105">Because using the wildcard character (\*) is not supported in SQLXML 4.0, you must specify the XPath query by using a namespace prefix.</span></span> <span data-ttu-id="d6ce5-106">若要解析此前置詞，請使用 namespace 屬性來指定命名空間系結。</span><span class="sxs-lookup"><span data-stu-id="d6ce5-106">To resolve this prefix, use the namespaces property to specify the namespace binding.</span></span>  
  
 <span data-ttu-id="d6ce5-107">在下列範例中，XPath 查詢會使用萬用字元 (\*) 和本機名稱 ( # A3 和 namespace-uri ( # A5 XPath 函數來指定命名空間。</span><span class="sxs-lookup"><span data-stu-id="d6ce5-107">In the following example, the XPath query specifies namespaces by using the wildcard character (\*) and the local-name() and namespace-uri() XPath functions.</span></span> <span data-ttu-id="d6ce5-108">這個 XPath 查詢會傳回本機名稱為 `Contact` 而且命名空間 URI 為 `urn:myschema:Contacts` 的所有元素。</span><span class="sxs-lookup"><span data-stu-id="d6ce5-108">This XPath query returns all the elements where the local name is `Contact` and the namespace URI is `urn:myschema:Contacts`.</span></span>  
  
```  
/*[local-name() = 'Contact' and namespace-uri() = 'urn:myschema:Contacts']  
```  
  
 <span data-ttu-id="d6ce5-109">在 SQLXML 4.0 中，您必須使用命名空間前置詞來指定這個 XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="d6ce5-109">In SQLXML 4.0, this XPath query must be specified with a namespace prefix.</span></span> <span data-ttu-id="d6ce5-110">例如，`x:Contact`，其中 `x` 是命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="d6ce5-110">An example is `x:Contact`, where `x` is the namespace prefix.</span></span> <span data-ttu-id="d6ce5-111">請考慮下列 XSD 結構描述：</span><span class="sxs-lookup"><span data-stu-id="d6ce5-111">Consider the following XSD schema:</span></span>  
  
```  
<schema xmlns="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema"  
            xmlns:con="urn:myschema:Contacts"  
            targetNamespace="urn:myschema:Contacts">  
<complexType name="ContactType">  
  <attribute name="CID" sql:field="ContactID" type="ID"/>  
  <attribute name="FName" sql:field="FirstName" type="string"/>  
  <attribute name="LName" sql:field="LastName"/>   
</complexType>  
<element name="Contact" type="con:ContactType" sql:relation="Person.Contact"/>  
</schema>  
```  
  
 <span data-ttu-id="d6ce5-112">由於這個結構描述會定義目標命名空間，所以針對此結構描述進行的 XPath 查詢 (例如 "Employee") 必須包含該命名空間。</span><span class="sxs-lookup"><span data-stu-id="d6ce5-112">Because this schema defines the target namespace, an XPath query (such as "Employee") against the schema must include the namespace.</span></span>  
  
 <span data-ttu-id="d6ce5-113">這是針對上述 XSD 結構描述執行 XPath 查詢 (x:Employee) 的範例 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d6ce5-113">This is a sample [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic application that executes an XPath query (x:Employee) against the preceding XSD schema.</span></span> <span data-ttu-id="d6ce5-114">若要解析前置詞，命名空間系結是使用 namespace 屬性所指定。</span><span class="sxs-lookup"><span data-stu-id="d6ce5-114">To resolve the prefix, the namespace binding is specified by using the namespaces property.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d6ce5-115">在程式碼中，您必須於連接字串內提供 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="d6ce5-115">In the code, you must provide the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span> <span data-ttu-id="d6ce5-116">此外，這個範例會指定針對資料提供者使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) (需要安裝其他網路用戶端軟體)。</span><span class="sxs-lookup"><span data-stu-id="d6ce5-116">Also, this example specifies the use of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) for the data provider, which requires additional network client software to be installed.</span></span> <span data-ttu-id="d6ce5-117">如需詳細資訊，請參閱[SQL Server Native Client 的系統需求](../../native-client/system-requirements-for-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="d6ce5-117">For more information, see [System Requirements for SQL Server Native Client](../../native-client/system-requirements-for-sql-server-native-client.md).</span></span>  
  
```  
Option Explicit  
Private Sub Form_Load()  
    Dim con As New ADODB.Connection  
    Dim cmd As New ADODB.Command  
    Dim stm As New ADODB.Stream  
    con.Open "provider=SQLXMLOLEDB.4.0;Data Provider=SQLNCLI11;Data Source=SqlServerName;Initial Catalog=AdventureWorks;Integrated Security=SSPI;"  
    Set cmd.ActiveConnection = con  
    stm.Open  
    cmd.Properties("Output Stream").Value = stm  
    cmd.Properties("Output Encoding") = "utf-8"  
    cmd.Properties("Mapping schema") = "C:\DirectoryPath\con-ex.xml"  
    cmd.Properties("namespaces") = "xmlns:x='urn:myschema:Contacts'"  
    '  Debug.Print "Set Command Dialect to DBGUID_XPATH"  
    cmd.Dialect = "{ec2a4293-e898-11d2-b1b7-00c04f680c56}"  
    cmd.CommandText = "x:Contact"  
    cmd.Execute , , adExecuteStream   
    stm.Position = 0  
    Debug.Print stm.ReadText(adReadAll)  
End Sub  
```  
  
### <a name="to-test-this-application"></a><span data-ttu-id="d6ce5-118">測試這個應用程式</span><span class="sxs-lookup"><span data-stu-id="d6ce5-118">To test this application</span></span>  
  
1.  <span data-ttu-id="d6ce5-119">將範例 XSD 結構描述儲存在資料夾中。</span><span class="sxs-lookup"><span data-stu-id="d6ce5-119">Save the sample XSD schema in a folder.</span></span>  
  
2.  <span data-ttu-id="d6ce5-120">建立 Visual Basic 可執行檔專案，然後將程式碼複製到其中。</span><span class="sxs-lookup"><span data-stu-id="d6ce5-120">Create a Visual Basic executable project, and copy the code into it.</span></span> <span data-ttu-id="d6ce5-121">依適當情況變更指定的目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="d6ce5-121">Change the specified directory path as appropriate.</span></span>  
  
3.  <span data-ttu-id="d6ce5-122">加入下列專案參考：</span><span class="sxs-lookup"><span data-stu-id="d6ce5-122">Add the following project reference:</span></span>  
  
    ```  
    "Microsoft ActiveX Data Objects 2.8 Library"  
    ```  
  
4.  <span data-ttu-id="d6ce5-123">執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d6ce5-123">Execute the application.</span></span>  
  
 <span data-ttu-id="d6ce5-124">以下是部份結果：</span><span class="sxs-lookup"><span data-stu-id="d6ce5-124">This is the partial result:</span></span>  
  
```  
<y0:Employee xmlns:y0="urn:myschema:Contacts"   
             LName="Achong" CID="1" FName="Gustavo"/>  
<y0:Employee xmlns:y0="urn:myschema:Employees"   
             LName="Abel" CID="2" FName="Catherine"/>  
```  
  
 <span data-ttu-id="d6ce5-125">雖然在 XML 文件中產生的前置詞是任意的，但是它們會對應至相同的命名空間。</span><span class="sxs-lookup"><span data-stu-id="d6ce5-125">The prefixes that are generated in the XML document are arbitrary, but they map to the same namespace.</span></span>  
  
  
