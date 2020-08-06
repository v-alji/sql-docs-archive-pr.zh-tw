---
title: 使用 ExecuteXMLReader 方法執行 SQL 查詢 |Microsoft Docs
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
- ExecuteXmlReader method
- SQL queries [SQLXML]
ms.assetid: f106a4c5-8d6e-40c0-bf1f-11e121afcb01
author: rothja
ms.author: jroth
ms.openlocfilehash: 1570e877ae84a813e5a053df34c35d5fe840969c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596575"
---
# <a name="executing-sql-queries-by-using-the-executexmlreader-method"></a><span data-ttu-id="08411-102">使用 ExecuteXMLReader 方法執行 SQL 查詢</span><span class="sxs-lookup"><span data-stu-id="08411-102">Executing SQL Queries by Using the ExecuteXMLReader Method</span></span>
  <span data-ttu-id="08411-103">您可以使用 SqlXmlCommand 物件的 ExecuteXmlReader 方法來執行命令，而不是使用 ExecuteToStream 方法。</span><span class="sxs-lookup"><span data-stu-id="08411-103">Instead of using the ExecuteToStream method, you can use the ExecuteXmlReader method of the SqlXmlCommand object to execute commands.</span></span> <span data-ttu-id="08411-104">這個方法會傳回可用來進一步處理結果 (的 XmlReader 物件，在此範例中，會列印元素或屬性名稱，以及) 的值。</span><span class="sxs-lookup"><span data-stu-id="08411-104">This method returns an XmlReader object that can be used for further processing of the result (which in this example is printing the element or attribute names and the values).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="08411-105">在程式碼中，您必須於連接字串內提供 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="08411-105">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
using System.Xml;  
   class Test  
   {  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks2012;Integrated Security=SSPI";  
      public static int testParams()  
      {  
         SqlXmlParameter p;  
         XmlReader Reader;  
         XmlTextWriter tw;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandText = "select FirstName, LastName from Person.Person where LastName = ? For XML Auto";  
         p = cmd.CreateParameter();  
         p.Value = "Achong";  
         Reader = cmd.ExecuteXmlReader();  
            tw = new XmlTextWriter(Console.Out);  
         Reader.MoveToContent();  
         tw.WriteNode(Reader, false);  
         tw.Flush();  
         tw.Close();  
         Reader.Close();  
  
         return 0;  
      }  
  
      static int Main(string[] args)  
      {  
         testParams();  
         return 0;  
      }  
   }  
```  
  
### <a name="to-test-the-application"></a><span data-ttu-id="08411-106">若要測試應用程式</span><span class="sxs-lookup"><span data-stu-id="08411-106">To test the application</span></span>  
  
1.  <span data-ttu-id="08411-107">請確認您在電腦上已安裝 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="08411-107">Make sure that you have the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework installed on your computer.</span></span>  
  
2.  <span data-ttu-id="08411-108">將這個主題所提供的 C# 程式碼 (DocSample.cs) 儲存在資料夾中。</span><span class="sxs-lookup"><span data-stu-id="08411-108">Save the C# code (DocSample.cs) that is provided in this topic in a folder.</span></span>  
  
3.  <span data-ttu-id="08411-109">編譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="08411-109">Compile the code.</span></span> <span data-ttu-id="08411-110">若要在命令提示字元下編譯程式碼，請使用：</span><span class="sxs-lookup"><span data-stu-id="08411-110">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     <span data-ttu-id="08411-111">這樣會建立可執行檔 (DocSample.exe)。</span><span class="sxs-lookup"><span data-stu-id="08411-111">This creates an executable (DocSample.exe).</span></span>  
  
4.  <span data-ttu-id="08411-112">在命令提示字元中，執行 DocSample.exe。</span><span class="sxs-lookup"><span data-stu-id="08411-112">At the command prompt, execute DocSample.exe.</span></span>  
  
  
