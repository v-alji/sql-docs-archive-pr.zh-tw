---
title: 使用 CommandText 屬性執行範本檔案 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- Managed Classes [SQLXML], executing template files
- SQLXML Managed Classes, executing template files
- templates [SQLXML], SQLXML Managed Classes
- executing template files [SQLXML]
- CommandText property
ms.assetid: f1b1278d-252d-4a06-836e-4ef77f338ef9
author: rothja
ms.author: jroth
ms.openlocfilehash: f5507e84daf57ca4646fae3efe78c6105af35700
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584357"
---
# <a name="executing-template-files-by-using-the-commandtext-property"></a><span data-ttu-id="80a79-102">使用 CommandText 屬性執行範本檔案</span><span class="sxs-lookup"><span data-stu-id="80a79-102">Executing Template Files by Using the CommandText Property</span></span>
  <span data-ttu-id="80a79-103">這個範例說明如何使用 CommandTextproperty 來指定由 SQL 或 XPath 查詢所組成的範本檔案。</span><span class="sxs-lookup"><span data-stu-id="80a79-103">This example illustrates how template files that consist of SQL or XPath queries can be specified by using the CommandTextproperty.</span></span> <span data-ttu-id="80a79-104">您可以指定檔案名做為值，而不是將 SQL 或 XPath 查詢指定為 CommandText 的值。</span><span class="sxs-lookup"><span data-stu-id="80a79-104">Instead of specifying the SQL or XPath query as the value of CommandText, you can specify a file name as the value.</span></span> <span data-ttu-id="80a79-105">在下列範例中，CommandType 屬性指定為 SqlXmlCommandType. TemplateFile。</span><span class="sxs-lookup"><span data-stu-id="80a79-105">In the following example, the CommandType property is specified as SqlXmlCommandType.TemplateFile.</span></span>  
  
 <span data-ttu-id="80a79-106">此範例應用程式會執行此範本：</span><span class="sxs-lookup"><span data-stu-id="80a79-106">The sample application executes this template:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query>  
    SELECT TOP 2 ContactID, FirstName, LastName   
    FROM   Person.Contact  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="80a79-107">這是 C# 應用程式範例。</span><span class="sxs-lookup"><span data-stu-id="80a79-107">This is the C# sample application.</span></span> <span data-ttu-id="80a79-108">若要測試應用程式，請儲存範本 (TemplateFile.xml)，然後再執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="80a79-108">To test the application, save the template (TemplateFile.xml) and then execute the application.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="80a79-109">在程式碼中，您必須於連接字串內提供 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="80a79-109">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
  
      public static int testParams()  
      {  
         //Stream strm;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandType = SqlXmlCommandType.TemplateFile;  
         cmd.CommandText = "TemplateFile.xml";  
         using (Stream strm = cmd.ExecuteStream()){  
            using (StreamReader sr = new StreamReader(strm)){  
                Console.WriteLine(sr.ReadToEnd());  
            }  
         }  
  
         return 0;        
      }  
      public static int Main(String[] args)  
      {  
         testParams();     
         return 0;  
      }  
   }  
```  
  
### <a name="to-test-the-application"></a><span data-ttu-id="80a79-110">若要測試應用程式</span><span class="sxs-lookup"><span data-stu-id="80a79-110">To test the application</span></span>  
  
1.  <span data-ttu-id="80a79-111">請確認您在電腦上已安裝 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="80a79-111">Make sure that you have the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework installed on your computer.</span></span>  
  
2.  <span data-ttu-id="80a79-112">將這個範例所提供的 XML 範本 (TemplateFile.xml) 儲存在資料夾中。</span><span class="sxs-lookup"><span data-stu-id="80a79-112">Save the XML template (TemplateFile.xml) that is provided in this example in a folder.</span></span>  
  
3.  <span data-ttu-id="80a79-113">將此範例中提供的 C# 程式碼 (DocSample.cs) 儲存到儲存結構描述的相同資料夾中 </span><span class="sxs-lookup"><span data-stu-id="80a79-113">Save the C# code (DocSample.cs) that is provided in this example in the same folder in which the schema is stored.</span></span> <span data-ttu-id="80a79-114">(如果您將檔案儲存在不同的資料夾中，您將需要編輯程式碼，然後為對應的結構描述指定適當的目錄路徑)。</span><span class="sxs-lookup"><span data-stu-id="80a79-114">(If you store the files in a different folder, you will have to edit the code and specify the appropriate directory path for the mapping schema.)</span></span>  
  
4.  <span data-ttu-id="80a79-115">編譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="80a79-115">Compile the code.</span></span> <span data-ttu-id="80a79-116">若要在命令提示字元下編譯程式碼，請使用：</span><span class="sxs-lookup"><span data-stu-id="80a79-116">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     <span data-ttu-id="80a79-117">這樣會建立可執行檔 (DocSample.exe)。</span><span class="sxs-lookup"><span data-stu-id="80a79-117">This creates an executable (DocSample.exe).</span></span>  
  
5.  <span data-ttu-id="80a79-118">在命令提示字元中，執行 DocSample.exe。</span><span class="sxs-lookup"><span data-stu-id="80a79-118">At the command prompt, execute DocSample.exe.</span></span>  
  
 <span data-ttu-id="80a79-119">如果您將參數傳遞至範本，參數名稱的開頭必須是 @ )  ( @;例如，p.Name = " @ContactID "，其中 p 是 SqlXmlParameter 物件。</span><span class="sxs-lookup"><span data-stu-id="80a79-119">If you pass a parameter to a template, the parameter name must begin with at sign (@); for example, p.Name="@ContactID", where p is a SqlXmlParameter object.</span></span>  
  
 <span data-ttu-id="80a79-120">這是採用一個參數的已更新範本。</span><span class="sxs-lookup"><span data-stu-id="80a79-120">This is the updated template which takes one parameter.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:header>  
     <sql:param name='ContactID'>1</sql:param>    
  </sql:header>  
  <sql:query>  
    SELECT ContactID, FirstName, LastName  
    FROM   Person.Contact  
    WHERE  ContactID=@ContactID  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="80a79-121">這是已更新的程式碼，會將參數傳入其中來執行範本。</span><span class="sxs-lookup"><span data-stu-id="80a79-121">This is the updated code in which a parameter is passed in to execute the template.</span></span>  
  
```  
public static int testParams()  
{  
  
   Stream strm;  
   SqlXmlParameter p;  
  
   SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
   cmd.CommandType = SqlXmlCommandType.TemplateFile;  
   cmd.CommandText = "TemplateFile.xml";  
   p = cmd.CreateParameter();  
   p.Name="@ContactID";  
   p.Value = "1";  
   strm = cmd.ExecuteStream();  
   StreamReader sw = new StreamReader(strm);  
   Console.WriteLine(sw.ReadToEnd());  
   return 0;        
}  
```  
  
  
