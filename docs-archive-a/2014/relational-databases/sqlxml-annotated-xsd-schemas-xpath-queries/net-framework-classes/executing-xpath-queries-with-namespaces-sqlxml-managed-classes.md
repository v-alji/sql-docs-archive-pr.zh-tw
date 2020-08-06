---
title: 使用命名空間執行 XPath 查詢 (SQLXML Managed 類別) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- namespaces property
- XPath queries [SQLXML], SQLXML Managed Classes
- queries [SQLXML], SQLXML Managed Classes
- XPath queries [SQLXML], namespaces
- Managed Classes [SQLXML], executing XPath queries
- SQLXML Managed Classes, executing XPath queries
- namespaces [SQLXML], XPath queries
ms.assetid: c6fc46d8-6b42-4992-a8f1-a8d4b8886e6e
author: rothja
ms.author: jroth
ms.openlocfilehash: a2d726de95929709c1ae958ee22388df3195bc84
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584355"
---
# <a name="executing-xpath-queries-with-namespaces-sqlxml-managed-classes"></a><span data-ttu-id="30538-102">執行含有命名空間的 XPath 查詢 (SQLXML Managed 類別)</span><span class="sxs-lookup"><span data-stu-id="30538-102">Executing XPath Queries with Namespaces (SQLXML Managed Classes)</span></span>
  <span data-ttu-id="30538-103">XPath 查詢可以包含命名空間。</span><span class="sxs-lookup"><span data-stu-id="30538-103">XPath queries can include namespaces.</span></span> <span data-ttu-id="30538-104">如果結構描述元素會限定命名空間 (使用目標命名空間)，針對此結構描述進行的 XPath 查詢就必須指定此命名空間。</span><span class="sxs-lookup"><span data-stu-id="30538-104">If the schema elements are namespace-qualified (use a target namespace), the XPath queries against the schema must specify the namespace.</span></span>  
  
 <span data-ttu-id="30538-105">由於 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 不支援萬用字元 (\*)，所以您必須使用命名空間前置詞來指定 XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="30538-105">Because the wildcard character (\*) is not supported in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0, you must specify the XPath query by using a namespace prefix.</span></span> <span data-ttu-id="30538-106">若要解析前置詞，請使用 namespace 屬性來指定命名空間系結。</span><span class="sxs-lookup"><span data-stu-id="30538-106">To resolve the prefix, use the namespaces property to specify the namespace binding.</span></span>  
  
 <span data-ttu-id="30538-107">在下列範例中，XPath 查詢會使用萬用字元 (\*) 和本機名稱 ( # A3 和 namespace-uri ( # A5 XPath 函數來指定命名空間。</span><span class="sxs-lookup"><span data-stu-id="30538-107">In the following example, the XPath query specifies namespaces by using the wildcard character (\*) and the local-name() and namespace-uri() XPath functions.</span></span> <span data-ttu-id="30538-108">這個 XPath 查詢會傳回本機名稱為 `Employee` 而且命名空間 URI 為 `urn:myschema:Contacts` 的所有元素：</span><span class="sxs-lookup"><span data-stu-id="30538-108">This XPath query returns all the elements where the local name is `Employee` and the namespace URI is `urn:myschema:Contacts`:</span></span>  
  
```  
/*[local-name() = 'Contact' and namespace-uri() = 'urn:myschema:Contacts']  
```  
  
 <span data-ttu-id="30538-109">在 SQLXML 4.0 中，使用命名空間前置詞來指定這個 XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="30538-109">In SQLXML 4.0, specify this XPath query with a namespace prefix.</span></span> <span data-ttu-id="30538-110">例如，`x:Contact`，其中 `x` 是命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="30538-110">An example is `x:Contact`, where `x` is the namespace prefix.</span></span> <span data-ttu-id="30538-111">請考慮下列 XSD 結構描述：</span><span class="sxs-lookup"><span data-stu-id="30538-111">Consider the following XSD schema:</span></span>  
  
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
  
 <span data-ttu-id="30538-112">由於這個結構描述會定義目標命名空間，所以針對此結構描述進行的 XPath 查詢 (例如 "Employee") 必須包含該命名空間。</span><span class="sxs-lookup"><span data-stu-id="30538-112">Because this schema defines the target namespace, an XPath query (such as "Employee") against this schema must include the namespace.</span></span>  
  
 <span data-ttu-id="30538-113">下列 C# 範例應用程式會針對先前的 XSD 結構描述 (MySchema.xml) 執行 XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="30538-113">The following C# sample application executes an XPath query against the preceding XSD schema (MySchema.xml).</span></span> <span data-ttu-id="30538-114">若要解析前置詞，請使用 SqlXmlCommand 物件的 namespace 屬性來指定命名空間系結。</span><span class="sxs-lookup"><span data-stu-id="30538-114">To resolve the prefix, specify the namespace binding by using the Namespaces property of the SqlXmlCommand object.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="30538-115">在程式碼中，您必須於連接字串內提供 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="30538-115">In the code, you must provide the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testXPath()  
      {  
         //Stream strm;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandText = "x:Contact[@CID='1']";  
         cmd.CommandType = SqlXmlCommandType.XPath;  
         cmd.RootTag = "ROOT";  
         cmd.Namespaces = "xmlns:x='urn:myschema:Contacts'";  
         cmd.SchemaPath = "MySchema.xml";  
         using (Stream strm = cmd.ExecuteStream()){  
            using (StreamReader sr = new StreamReader(strm)){  
               Console.WriteLine(sr.ReadToEnd());  
            }  
         }  
         return 0;  
      }  
      public static int Main(String[] args)  
      {  
         testXPath();  
         return 0;  
      }  
   }  
```  
  
 <span data-ttu-id="30538-116">若要測試此範例，您必須先在電腦上安裝 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="30538-116">To test this example, you must have the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework installed on your computer.</span></span>  
  
### <a name="to-test-the-application"></a><span data-ttu-id="30538-117">若要測試應用程式</span><span class="sxs-lookup"><span data-stu-id="30538-117">To test the application</span></span>  
  
1.  <span data-ttu-id="30538-118">將這個範例所提供的 XSD 結構描述 (MySchema.xml) 儲存在資料夾中。</span><span class="sxs-lookup"><span data-stu-id="30538-118">Save the XSD schema (MySchema.xml) that is provided in this example in a folder.</span></span>  
  
2.  <span data-ttu-id="30538-119">將此範例中提供的 C# 程式碼 (DocSample.cs) 儲存到儲存結構描述的相同資料夾中 </span><span class="sxs-lookup"><span data-stu-id="30538-119">Save the C# code (DocSample.cs) that is provided in this example in the same folder in which the schema is stored.</span></span> <span data-ttu-id="30538-120">(如果您將檔案儲存在不同的資料夾中，您將需要編輯程式碼，然後為對應的結構描述指定適當的目錄路徑)。</span><span class="sxs-lookup"><span data-stu-id="30538-120">(If you store the files in a different folder, you will have to edit the code and specify the appropriate directory path for the mapping schema.)</span></span>  
  
3.  <span data-ttu-id="30538-121">編譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="30538-121">Compile the code.</span></span> <span data-ttu-id="30538-122">若要在命令提示字元下編譯程式碼，請使用：</span><span class="sxs-lookup"><span data-stu-id="30538-122">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     <span data-ttu-id="30538-123">這樣會建立可執行檔 (DocSample.exe)。</span><span class="sxs-lookup"><span data-stu-id="30538-123">This creates an executable (DocSample.exe).</span></span>  
  
4.  <span data-ttu-id="30538-124">在命令提示字元中，執行 DocSample.exe。</span><span class="sxs-lookup"><span data-stu-id="30538-124">At the command prompt, execute DocSample.exe.</span></span>  
  
  
