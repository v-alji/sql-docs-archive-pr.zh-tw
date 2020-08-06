---
title: " (SQLXML Managed 類別) 執行 XPath 查詢 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], SQLXML Managed Classes
- queries [SQLXML], SQLXML Managed Classes
- Managed Classes [SQLXML], executing XPath queries
- mapping schema [SQLXML], XPath queries
- SQLXML Managed Classes, executing XPath queries
ms.assetid: 8bef4c4d-bf0e-4236-a875-fd7d3e058396
author: rothja
ms.author: jroth
ms.openlocfilehash: d8f5fd2612a0992f18e0b7f32c749c352d29d2b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584356"
---
# <a name="executing-xpath-queries-sqlxml-managed-classes"></a><span data-ttu-id="9cf3c-102">執行 XPath 查詢 (SQLXML Managed 類別)</span><span class="sxs-lookup"><span data-stu-id="9cf3c-102">Executing XPath Queries (SQLXML Managed Classes)</span></span>
  <span data-ttu-id="9cf3c-103">此範例說明如何根據對應結構描述執行 XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="9cf3c-103">This example illustrates how XPath queries are executed against a mapping schema.</span></span>  
  
 <span data-ttu-id="9cf3c-104">請考慮使用這個結構描述：</span><span class="sxs-lookup"><span data-stu-id="9cf3c-104">Consider this schema:</span></span>  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Con" sql:relation="Person.Contact" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="FName"    
                     sql:field="FirstName"   
                     type="xsd:string" />   
        <xsd:element name="LName"    
                     sql:field="LastName"    
                     type="xsd:string" />  
     </xsd:sequence>  
     <xsd:attribute name="ContactID" type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 <span data-ttu-id="9cf3c-105">這個 C# 應用程式會根據此結構描述 (MySchema.xml) 執行 XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="9cf3c-105">This C# application executes an XPath query against this schema (MySchema.xml).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9cf3c-106">在程式碼中，您必須於連接字串內提供 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="9cf3c-106">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
  
      public static int testXPath()  
      {  
         Stream strm;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandText = "Con";  
         cmd.CommandType = SqlXmlCommandType.XPath;  
         cmd.RootTag = "ROOT";  
         cmd.SchemaPath = "MySchema.xml";  
         strm = cmd.ExecuteStream();  
         using (StreamReader sr = new StreamReader(strm)){  
            Console.WriteLine(sr.ReadToEnd());  
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
  
### <a name="to-test-the-application"></a><span data-ttu-id="9cf3c-107">若要測試應用程式</span><span class="sxs-lookup"><span data-stu-id="9cf3c-107">To test the application</span></span>  
  
1.  <span data-ttu-id="9cf3c-108">請確認您在電腦上已安裝 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="9cf3c-108">Make sure that you have the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework installed on your computer.</span></span>  
  
2.  <span data-ttu-id="9cf3c-109">將這個範例所提供的 XSD 結構描述 (MySchema.xml) 儲存在資料夾中。</span><span class="sxs-lookup"><span data-stu-id="9cf3c-109">Save the XSD schema (MySchema.xml) that is provided in this example in a folder.</span></span>  
  
3.  <span data-ttu-id="9cf3c-110">將此範例中提供的 C# 程式碼 (DocSample.cs) 儲存到儲存結構描述的相同資料夾中 </span><span class="sxs-lookup"><span data-stu-id="9cf3c-110">Save the C# code (DocSample.cs) that is provided in this example in the same folder in which the schema is stored.</span></span> <span data-ttu-id="9cf3c-111">(如果您將檔案儲存在不同的資料夾中，您將需要編輯程式碼，然後為對應的結構描述指定適當的目錄路徑)。</span><span class="sxs-lookup"><span data-stu-id="9cf3c-111">(If you store the files in a different folder, you will have to edit the code and specify the appropriate directory path for the mapping schema.)</span></span>  
  
4.  <span data-ttu-id="9cf3c-112">編譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="9cf3c-112">Compile the code.</span></span> <span data-ttu-id="9cf3c-113">若要在命令提示字元下編譯程式碼，請使用：</span><span class="sxs-lookup"><span data-stu-id="9cf3c-113">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     <span data-ttu-id="9cf3c-114">這樣會建立可執行檔 (DocSample.exe)。</span><span class="sxs-lookup"><span data-stu-id="9cf3c-114">This creates an executable (DocSample.exe).</span></span>  
  
5.  <span data-ttu-id="9cf3c-115">在命令提示字元中，執行 DocSample.exe。</span><span class="sxs-lookup"><span data-stu-id="9cf3c-115">At the command prompt, execute DocSample.exe.</span></span>  
  
  
