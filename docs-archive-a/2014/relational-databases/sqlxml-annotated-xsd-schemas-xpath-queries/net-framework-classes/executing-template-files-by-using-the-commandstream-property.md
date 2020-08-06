---
title: 使用 CommandStream 屬性執行範本檔案 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- Managed Classes [SQLXML], executing template files
- SQLXML Managed Classes, executing template files
- templates [SQLXML], SQLXML Managed Classes
- CommandStream property
ms.assetid: 55c564e3-56d1-4d85-bcaa-703e2905dd57
author: rothja
ms.author: jroth
ms.openlocfilehash: c57a2ab2f3780a8bc75b53b0cceeee0799fcfcc2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584358"
---
# <a name="executing-template-files-by-using-the-commandstream-property"></a><span data-ttu-id="c19bc-102">利用 CommandStream 屬性執行範本檔案</span><span class="sxs-lookup"><span data-stu-id="c19bc-102">Executing Template Files by Using the CommandStream Property</span></span>
  <span data-ttu-id="c19bc-103">這個範例說明如何使用 SqlXmlCommand 物件的 CommandStream 屬性來指定由 SQL 或 XPath 查詢所組成的範本檔案。</span><span class="sxs-lookup"><span data-stu-id="c19bc-103">This example illustrates how template files that consist of SQL or XPath queries can be specified by using the CommandStream property of the SqlXmlCommand object.</span></span> <span data-ttu-id="c19bc-104">在此應用程式中，會開啟命令檔的 FileStreamobject，並將檔案資料流程指派為執行的 CommandStream。</span><span class="sxs-lookup"><span data-stu-id="c19bc-104">In this application, a FileStreamobject is opened for a command file, and the file stream is assigned as the CommandStream that is executed.</span></span>  
  
 <span data-ttu-id="c19bc-105">在下列範例中，CommandType 屬性指定為 SqlXmlCommandType， (不是 TemplateFile) 。</span><span class="sxs-lookup"><span data-stu-id="c19bc-105">In the following example, the CommandType property is specified as SqlXmlCommandType.Template (not as TemplateFile).</span></span>  
  
 <span data-ttu-id="c19bc-106">這是 XML 範本範例：</span><span class="sxs-lookup"><span data-stu-id="c19bc-106">This is the sample XML template:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query>  
    SELECT TOP 2 ContactID, FirstName, LastName   
    FROM   Person.Contact  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 <span data-ttu-id="c19bc-107">這是 C# 應用程式範例。</span><span class="sxs-lookup"><span data-stu-id="c19bc-107">This is the sample C# application.</span></span> <span data-ttu-id="c19bc-108">若要測試應用程式，請儲存範本 (TemplateFile.xml)，然後再執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="c19bc-108">To test the application, save the template (TemplateFile.xml) and then execute the application.</span></span> <span data-ttu-id="c19bc-109">應用程式會執行在 XML 範本中指定的查詢，並將產生的 XML 文件顯示在螢幕上。</span><span class="sxs-lookup"><span data-stu-id="c19bc-109">The application executes the query that is specified in the XML template and displays the XML document that is generated on the screen.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c19bc-110">在程式碼中，您必須於連接字串內提供 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="c19bc-110">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
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
         MemoryStream ms = new MemoryStream();  
         StreamWriter sw = new StreamWriter(ms);  
         ms.Position = 0;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandStream = new FileStream("TemplateFile.xml", FileMode.Open, FileAccess.Read);  
         cmd.CommandType = SqlXmlCommandType.Template;  
         using (Stream strm = cmd.ExecuteStream())  
         {  
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
  
### <a name="to-test-the-application"></a><span data-ttu-id="c19bc-111">若要測試應用程式</span><span class="sxs-lookup"><span data-stu-id="c19bc-111">To test the application</span></span>  
  
1.  <span data-ttu-id="c19bc-112">將這個範例所提供的 XML 範本 (TemplateFile.xml) 儲存在資料夾中。</span><span class="sxs-lookup"><span data-stu-id="c19bc-112">Save the XML template (TemplateFile.xml) that is provided in this example in a folder.</span></span>  
  
2.  <span data-ttu-id="c19bc-113">將此範例中提供的 C# 程式碼 (DocSample.cs) 儲存到儲存結構描述的相同資料夾中 </span><span class="sxs-lookup"><span data-stu-id="c19bc-113">Save the C# code (DocSample.cs) that is provided in this example in the same folder in which the schema is stored.</span></span> <span data-ttu-id="c19bc-114">(如果您將檔案儲存在不同的資料夾中，您將需要編輯程式碼，然後為對應的結構描述指定適當的目錄路徑)。</span><span class="sxs-lookup"><span data-stu-id="c19bc-114">(If you store the files in a different folder, you will have to edit the code and specify the appropriate directory path for the mapping schema.)</span></span>  
  
3.  <span data-ttu-id="c19bc-115">編譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="c19bc-115">Compile the code.</span></span> <span data-ttu-id="c19bc-116">若要在命令提示字元下編譯程式碼，請使用：</span><span class="sxs-lookup"><span data-stu-id="c19bc-116">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     <span data-ttu-id="c19bc-117">這樣會建立可執行檔 (DocSample.exe)。</span><span class="sxs-lookup"><span data-stu-id="c19bc-117">This creates an executable (DocSample.exe).</span></span>  
  
4.  <span data-ttu-id="c19bc-118">在命令提示字元中，執行 DocSample.exe。</span><span class="sxs-lookup"><span data-stu-id="c19bc-118">At the command prompt, execute DocSample.exe.</span></span>  
  
  
