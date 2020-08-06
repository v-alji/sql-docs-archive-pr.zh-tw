---
title: 存取 .NET 環境中的 SQLXML 功能 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- Managed Classes [SQLXML], accessing SQLXML functionality
- SQLXML Managed Classes, accessing SQLXML functionality
- DiffGrams [SQLXML], accessing SQLXML functionality
- .NET Framework [SQLXML], accessing SQLXML functionality
ms.assetid: 74744535-2945-414d-9a5b-7e8cc363953a
author: rothja
ms.author: jroth
ms.openlocfilehash: a2ba0a54310833c0a1a1315aa94d78fe5650d480
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596591"
---
# <a name="accessing-sqlxml-functionality-in-the-net-environment"></a><span data-ttu-id="9cc04-102">存取 .NET 環境中的 SQLXML 功能</span><span class="sxs-lookup"><span data-stu-id="9cc04-102">Accessing SQLXML Functionality in the .NET Environment</span></span>
  <span data-ttu-id="9cc04-103">此範例顯示：</span><span class="sxs-lookup"><span data-stu-id="9cc04-103">This example shows:</span></span>  
  
-   <span data-ttu-id="9cc04-104">如何使用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Sqlxml Managed 類別 (microsoft. Data. sqlxml) ， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 在 .NET Framework 環境中存取 Microsoft [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9cc04-104">How to use [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML Managed Classes (Microsoft.Data.SqlXml) to access Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework environment.</span></span>  
  
-   <span data-ttu-id="9cc04-105">在 .NET Framework 環境中產生的 DiffGrams 如何將資料更新套用到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料表。</span><span class="sxs-lookup"><span data-stu-id="9cc04-105">How DiffGrams that are generated in the .NET Framework environment can apply data updates to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tables.</span></span>  
  
 <span data-ttu-id="9cc04-106">在此應用程式中，XPath 查詢會根據 XSD 結構描述執行。</span><span class="sxs-lookup"><span data-stu-id="9cc04-106">In this application, an XPath query is executed against an XSD schema.</span></span> <span data-ttu-id="9cc04-107">執行 XPath 查詢會傳回 XML 檔，其中包含連絡人資料 (**FirstName**， **LastName**) 。</span><span class="sxs-lookup"><span data-stu-id="9cc04-107">The execution of the XPath query returns an XML document that consists of contact data (**FirstName**, **LastName**).</span></span> <span data-ttu-id="9cc04-108">應用程式會將 XML 文件載入到 .NET Framework 環境的資料集中。</span><span class="sxs-lookup"><span data-stu-id="9cc04-108">The application loads the XML document in the dataset in the .NET Framework environment.</span></span> <span data-ttu-id="9cc04-109">資料集中的資料已修改：連絡人的名字會變更為 "Susan"，成為資料集中的第一個連絡人。</span><span class="sxs-lookup"><span data-stu-id="9cc04-109">The data in the dataset is modified: the contact's first name is changed to "Susan" for the first contact in the dataset.</span></span> <span data-ttu-id="9cc04-110">DiffGram 會從資料集產生，然後會將 DiffGram (員工名字的變更) 中指定的更新套用到 Person.Contact 資料表。</span><span class="sxs-lookup"><span data-stu-id="9cc04-110">The DiffGram is generated from the dataset, and the update that is specified in the DiffGram (the change in the employee's first name) is then applied to the Person.Contact table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9cc04-111">在程式碼中，您必須於連接字串內提供 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="9cc04-111">In the code, you must provide the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
```  
using System;  
using System.Data;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
   static string ConnString = "Provider=SQLOLEDB;Server=SqlServerName;database=AdventureWorks;Integrated Security=SSPI;";  
   public static int testParams()  
   {  
      DataRow row;  
      SqlXmlAdapter ad;  
      //need a memory stream to hold diff gram temporarily  
      MemoryStream ms = new MemoryStream();  
      SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
      cmd.RootTag = "ROOT";  
      cmd.CommandText = "Con";  
      cmd.CommandType = SqlXmlCommandType.XPath;  
      cmd.SchemaPath = "MySchema.xml";  
      //load data set  
      DataSet ds = new DataSet();  
      ad = new SqlXmlAdapter(cmd);  
      ad.Fill(ds);  
      row = ds.Tables["Con"].Rows[0];  
      row["FName"] = "Susan";  
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
  
 <span data-ttu-id="9cc04-112">**測試範例：**</span><span class="sxs-lookup"><span data-stu-id="9cc04-112">**To test the example:**</span></span>  
  
 <span data-ttu-id="9cc04-113">若要測試此範例，您必須先在電腦上安裝 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="9cc04-113">To test this example, you must have the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework installed on your computer.</span></span>  
  
1.  <span data-ttu-id="9cc04-114">將這個 XSD 結構描述 (MySchema.xml) 儲存在資料夾中：</span><span class="sxs-lookup"><span data-stu-id="9cc04-114">Save this XSD schema (MySchema.xml) in a folder:</span></span>  
  
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
  
2.  <span data-ttu-id="9cc04-115">將此範例中提供的 C# 程式碼 (DocSample.cs) 儲存到儲存結構描述的相同資料夾中 </span><span class="sxs-lookup"><span data-stu-id="9cc04-115">Save the C# code (DocSample.cs) provided in this example in the same folder in which the schema is stored.</span></span> <span data-ttu-id="9cc04-116">(如果您將檔案儲存在不同的資料夾中，您將需要編輯程式碼，然後為對應的結構描述指定適當的目錄路徑)。</span><span class="sxs-lookup"><span data-stu-id="9cc04-116">(If you store the files in a different folder, you will have to edit the code and specify the appropriate directory path for the mapping schema.)</span></span>  
  
3.  <span data-ttu-id="9cc04-117">編譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="9cc04-117">Compile the code.</span></span> <span data-ttu-id="9cc04-118">若要在命令提示字元下編譯程式碼，請使用：</span><span class="sxs-lookup"><span data-stu-id="9cc04-118">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     <span data-ttu-id="9cc04-119">這樣會建立可執行檔 (DocSample.exe)。</span><span class="sxs-lookup"><span data-stu-id="9cc04-119">This creates an executable (DocSample.exe).</span></span>  
  
 <span data-ttu-id="9cc04-120">在命令提示字元中，執行 DocSample.exe。</span><span class="sxs-lookup"><span data-stu-id="9cc04-120">At the command prompt, execute DocSample.exe.</span></span>  
  
  
