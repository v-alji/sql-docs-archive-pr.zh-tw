---
title: " (SQLXML Managed 類別) 執行 SQL 查詢 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- queries [SQLXML], SQLXML Managed Classes
- SQLXML Managed Classes, executing SQL queries
- Managed Classes [SQLXML], executing SQL queries
- ExecuteToStream method
- SQL queries [SQLXML]
ms.assetid: a561ae83-a8b6-4b9b-a819-9b86839546b4
author: rothja
ms.author: jroth
ms.openlocfilehash: d869e45de359e602b2451b9f66fa3046f6823c1e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596573"
---
# <a name="executing-sql-queries-sqlxml-managed-classes"></a><span data-ttu-id="56572-102">執行 SQL 查詢 (SQLXML Managed 類別)</span><span class="sxs-lookup"><span data-stu-id="56572-102">Executing SQL Queries (SQLXML Managed Classes)</span></span>
  <span data-ttu-id="56572-103">此範例示範：</span><span class="sxs-lookup"><span data-stu-id="56572-103">This example demonstrates:</span></span>  
  
-   <span data-ttu-id="56572-104"> (SqlXmlParameter 物件) 建立參數。</span><span class="sxs-lookup"><span data-stu-id="56572-104">Creating parameters (SqlXmlParameter objects).</span></span>  
  
-   <span data-ttu-id="56572-105">將值指派給屬性 (SqlXmlParameter 物件的名稱和值) 。</span><span class="sxs-lookup"><span data-stu-id="56572-105">Assigning values to the properties (Name and Value) of SqlXmlParameter objects.</span></span>  
  
 <span data-ttu-id="56572-106">在此範例中，系統會執行簡單 SQL 查詢來擷取其姓氏值當做參數傳遞之員工的名字、姓氏和生日。</span><span class="sxs-lookup"><span data-stu-id="56572-106">In this example, a simple SQL query is executed to retrieve the first name, last name, and birth date of the employee whose last name value is passed as a parameter.</span></span> <span data-ttu-id="56572-107">在 (*LastName*) 中指定參數時，只會設定 Value 屬性。</span><span class="sxs-lookup"><span data-stu-id="56572-107">In specifying the parameter (*LastName*), only the Value property is set.</span></span> <span data-ttu-id="56572-108">未設定 Name 屬性，因為在此查詢中，參數是位置，而且不需要名稱。</span><span class="sxs-lookup"><span data-stu-id="56572-108">The Name property is not set, because in this query the parameter is positional and no name is required.</span></span>  
  
 <span data-ttu-id="56572-109">SqlXmlCommand 物件的 CommandType 屬性預設為**Sql**。</span><span class="sxs-lookup"><span data-stu-id="56572-109">The CommandType property of the SqlXmlCommand object by default is **Sql**.</span></span> <span data-ttu-id="56572-110">因此，未明確地設定屬性。</span><span class="sxs-lookup"><span data-stu-id="56572-110">Therefore, the property is not explicitly set.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="56572-111">在程式碼中，您必須於連接字串內提供 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="56572-111">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
 <span data-ttu-id="56572-112">以下為 C# 程式碼：</span><span class="sxs-lookup"><span data-stu-id="56572-112">This is the C# code:</span></span>  
  
```  
using System;  
  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testParams()  
      {  
         Stream strm;  
         SqlXmlParameter p;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);        
         cmd.CommandText = "SELECT FirstName, LastName FROM Person.Contact WHERE LastName=? For XML Auto";  
         p = cmd.CreateParameter();  
         p.Value = "Achong";  
         string strResult;  
         try   
         {  
            strm = cmd.ExecuteStream();  
            strm.Position = 0;  
            using(StreamReader sr = new StreamReader(strm))  
            {  
               Console.WriteLine(sr.ReadToEnd());  
            }  
         }  
         catch (SqlXmlException e)  
         {  
            //in case of an error, this prints error returned.  
            e.ErrorStream.Position=0;  
            strResult=new StreamReader(e.ErrorStream).ReadToEnd();  
            System.Console.WriteLine(strResult);  
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
  
### <a name="to-test-the-application"></a><span data-ttu-id="56572-113">若要測試應用程式</span><span class="sxs-lookup"><span data-stu-id="56572-113">To test the application</span></span>  
  
1.  <span data-ttu-id="56572-114">將此主題中提供的 C# 程式碼 (DocSample.cs) 儲存到資料夾中。</span><span class="sxs-lookup"><span data-stu-id="56572-114">Save the C# code (DocSample.cs) provided in this topic in a folder.</span></span>  
  
2.  <span data-ttu-id="56572-115">編譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="56572-115">Compile the code.</span></span> <span data-ttu-id="56572-116">若要在命令提示字元下編譯程式碼，請使用：</span><span class="sxs-lookup"><span data-stu-id="56572-116">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     <span data-ttu-id="56572-117">這樣會建立可執行檔 (DocSample.exe)。</span><span class="sxs-lookup"><span data-stu-id="56572-117">This creates an executable (DocSample.exe).</span></span>  
  
3.  <span data-ttu-id="56572-118">在命令提示字元中，執行 DocSample.exe。</span><span class="sxs-lookup"><span data-stu-id="56572-118">At the command prompt, execute DocSample.exe.</span></span>  
  
 <span data-ttu-id="56572-119">若要測試此範例，您必須先在電腦上安裝 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="56572-119">To test this example, you must have the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework installed on your computer.</span></span>  
  
 <span data-ttu-id="56572-120">您可以指定執行 Updategram (也是一個範本) 的範本 (如以下程式碼片段所示) 來插入客戶記錄，而不是指定 SQL 查詢當做命令文字。</span><span class="sxs-lookup"><span data-stu-id="56572-120">Instead of specifying SQL queries as the command text, you can specify a template (as shown in the following code fragment) that executes an updategram (which is also a template) to insert a customer record.</span></span> <span data-ttu-id="56572-121">您可以在檔案中指定範本和 Updategrams 並執行這些檔案。</span><span class="sxs-lookup"><span data-stu-id="56572-121">You can specify templates and updategrams in files and execute files.</span></span> <span data-ttu-id="56572-122">如需詳細資訊，請參閱[使用 CommandText 屬性執行範本](executing-template-files-by-using-the-commandtext-property.md)檔案。</span><span class="sxs-lookup"><span data-stu-id="56572-122">For more information, see [Executing Template Files by Using the CommandText Property](executing-template-files-by-using-the-commandtext-property.md).</span></span>  
  
```  
SqlXmlCommand cmd = new SqlXmlCommand("Provider=SQLOLEDB;Data Source=SqlServerName;Initial Catalog=Database; Integrated Security=SSPI;");  
Stream stm;  
cmd.CommandType = SqlXmlCommandType.UpdateGram;  
cmd.CommandText = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql' xmlns:updg='urn:schemas-microsoft-com:xml-updategram'>" +  
      "<updg:sync>" +  
       "<updg:before/>" +  
       "<updg:after>" +  
         "<Customer CustomerID='aaaaa' CustomerName='Some Name' CustomerTitle='SomeTitle' />" +  
       "</updg:after>" +  
       "</updg:sync>" +  
       "</ROOT>";  
  
stm = cmd.ExecuteStream();  
stm = null;  
cmd = null;  
```  
  
## <a name="using-executetostream"></a><span data-ttu-id="56572-123">使用 ExecuteToStream</span><span class="sxs-lookup"><span data-stu-id="56572-123">Using ExecuteToStream</span></span>  
 <span data-ttu-id="56572-124">如果您有現有的資料流程，您可以使用 ExecuteToStream 方法，而不是建立資料流程物件，並使用 Execute 方法。</span><span class="sxs-lookup"><span data-stu-id="56572-124">If you have an existing stream, you can use the ExecuteToStream method instead of creating a Stream object and using the Execute method.</span></span> <span data-ttu-id="56572-125">上述範例中的程式碼會在這裡修訂，以使用 ExecuteToStream 方法：</span><span class="sxs-lookup"><span data-stu-id="56572-125">The code from the preceding example is revised here to use the ExecuteToStream method:</span></span>  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
   static string ConnString = "Provider=SQLOLEDB;Server=SqlServerName;database=AdventureWorks;Integrated Security=SSPI;";  
   public static int testParams()  
   {  
      SqlXmlParameter p;  
      MemoryStream ms = new MemoryStream();  
      StreamReader sr = new StreamReader(ms);  
      ms.Position = 0;  
      SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
      cmd.CommandText = "select FirstName, LastName from Person.Contact where LastName = ? For XML Auto";  
      p = cmd.CreateParameter();  
      p.Value = "Achong";  
      cmd.ExecuteToStream(ms);  
      ms.Position = 0;  
      Console.WriteLine(sr.ReadToEnd());  
      return 0;        
   }  
   public static int Main(String[] args)  
   {  
      testParams();     
      return 0;  
   }  
}  
```  
  
> [!NOTE]  
>  <span data-ttu-id="56572-126">您也可以使用傳回 XmlReader 物件的 ExecuteXMLReadermethod。</span><span class="sxs-lookup"><span data-stu-id="56572-126">You can also use the ExecuteXMLReadermethod that returns an XmlReader object.</span></span> <span data-ttu-id="56572-127">如需詳細資訊，請參閱[使用 ExecuteXMLReader 方法執行 SQL 查詢](executing-sql-queries-by-using-the-executexmlreader-method.md)。</span><span class="sxs-lookup"><span data-stu-id="56572-127">For more information, see [Executing SQL Queries by Using the ExecuteXMLReader Method](executing-sql-queries-by-using-the-executexmlreader-method.md).</span></span>  
  
  
