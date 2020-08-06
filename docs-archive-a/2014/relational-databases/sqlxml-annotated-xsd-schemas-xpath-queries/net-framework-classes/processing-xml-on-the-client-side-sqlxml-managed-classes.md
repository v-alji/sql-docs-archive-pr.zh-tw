---
title: 在用戶端上處理 XML (SQLXML Managed 類別) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- processing XML on client side [SQLXML]
- client-side XML formatting
- Managed Classes [SQLXML], client-side XML formatting
- SQLXML Managed Classes, client-side XML formatting
- ClientSideXml property
ms.assetid: 5e7ecf18-66fc-49ff-bc50-83635cd7ac0b
author: rothja
ms.author: jroth
ms.openlocfilehash: fb90f7c5c823c750b64f47d0c9df9551b9f857b5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585247"
---
# <a name="processing-xml-on-the-client-side-sqlxml-managed-classes"></a><span data-ttu-id="a90a0-102">在用戶端上處理 XML (SQLXML Managed 類別)</span><span class="sxs-lookup"><span data-stu-id="a90a0-102">Processing XML on the Client Side (SQLXML Managed Classes)</span></span>
  <span data-ttu-id="a90a0-103">這個範例說明如何使用 ClientSideXml 屬性。</span><span class="sxs-lookup"><span data-stu-id="a90a0-103">This example illustrates the use of the ClientSideXml property.</span></span> <span data-ttu-id="a90a0-104">應用程式會在伺服器上執行預存程序。</span><span class="sxs-lookup"><span data-stu-id="a90a0-104">The application executes a stored procedure on the server.</span></span> <span data-ttu-id="a90a0-105">預存程序的結果 (兩個資料行的資料列集) 會在用戶端上進行處理以產生 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="a90a0-105">The result of the stored procedure (a two-column rowset) is processed on the client side to produce an XML document.</span></span>  
  
 <span data-ttu-id="a90a0-106">下列 GetContacts 預存程式會傳回 AdventureWorks 資料庫之 Person 資料表中員工的**FirstName**和**LastName** 。</span><span class="sxs-lookup"><span data-stu-id="a90a0-106">The following GetContacts stored procedure returns **FirstName** and **LastName** of employees in the Person.Contact table in the AdventureWorks database.</span></span>  
  
```  
USE AdventureWorks  
CREATE PROCEDURE GetContacts @LastName varchar(20)  
AS  
SELECT FirstName, LastName  
FROM   Person.Contact  
WHERE LastName = @LastName  
Go  
```  
  
 <span data-ttu-id="a90a0-107">這個 c # 應用程式會執行預存程式，並在指定 CommandText 值時指定 FOR XML AUTO 選項。</span><span class="sxs-lookup"><span data-stu-id="a90a0-107">This C# application executes the stored procedure and specifies the FOR XML AUTO option in specifying the CommandText value.</span></span> <span data-ttu-id="a90a0-108">在應用程式中，SqlXmlCommand 物件的 ClientSideXml 屬性會設定為 true。</span><span class="sxs-lookup"><span data-stu-id="a90a0-108">In the application, the ClientSideXml property of the SqlXmlCommand object is set to true.</span></span> <span data-ttu-id="a90a0-109">這可讓您執行預先存在的預存程序以傳回資料列集，並在用戶端上，將 XML 轉換套用到該資料列集。</span><span class="sxs-lookup"><span data-stu-id="a90a0-109">This allows you to execute preexisting stored procedures that return a rowset and apply an XML transformation to it on the client.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a90a0-110">在程式碼中，您必須於連接字串內提供 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="a90a0-110">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
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
         SqlXmlParameter p;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.ClientSideXml = true;  
         cmd.CommandText = "EXEC GetContacts ? FOR XML NESTED";  
         p = cmd.CreateParameter();  
         p.Value = "Achong";  
         using (Stream strm = cmd.ExecuteStream())   
         {  
            using (StreamReader sr = new StreamReader(strm))  
                  {  
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
  
 <span data-ttu-id="a90a0-111">若要測試此範例，您必須先在電腦上安裝 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="a90a0-111">To test this example, you must have the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework installed on your computer.</span></span>  
  
### <a name="to-test-the-application"></a><span data-ttu-id="a90a0-112">若要測試應用程式</span><span class="sxs-lookup"><span data-stu-id="a90a0-112">To test the application</span></span>  
  
1.  <span data-ttu-id="a90a0-113">建立預存程序。</span><span class="sxs-lookup"><span data-stu-id="a90a0-113">Create the stored procedure.</span></span>  
  
2.  <span data-ttu-id="a90a0-114">將此範例中提供的 C# 程式碼 (DocSample.cs) 儲存到資料夾中。</span><span class="sxs-lookup"><span data-stu-id="a90a0-114">Save the C# code (DocSample.cs) that is provided in this example in a folder.</span></span> <span data-ttu-id="a90a0-115">編輯該程式碼來指定適當的登入和密碼資訊。</span><span class="sxs-lookup"><span data-stu-id="a90a0-115">Edit the code to specify appropriate login and password information.</span></span>  
  
3.  <span data-ttu-id="a90a0-116">編譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="a90a0-116">Compile the code.</span></span> <span data-ttu-id="a90a0-117">若要在命令提示字元下編譯程式碼，請使用：</span><span class="sxs-lookup"><span data-stu-id="a90a0-117">To compile the code at the command prompt, use:</span></span>  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     <span data-ttu-id="a90a0-118">這樣會建立可執行檔 (DocSample.exe)。</span><span class="sxs-lookup"><span data-stu-id="a90a0-118">This creates an executable (DocSample.exe).</span></span>  
  
4.  <span data-ttu-id="a90a0-119">在命令提示字元中，執行 DocSample.exe。</span><span class="sxs-lookup"><span data-stu-id="a90a0-119">At the command prompt, execute DocSample.exe.</span></span>  
  
  
