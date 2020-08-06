---
title: 執行包含 SQL 查詢 (SQLXMLOLEDB 提供者) 的範本 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- templates [SQLXML]
- SQLXMLOLEDB Provider, executing template files
- templates [SQLXML], SQL queries
- XML templates [SQLXML]
- SQL queries [SQLXML]
ms.assetid: ff2bc36f-e3fb-4d8f-8e3a-2680a39eda11
author: rothja
ms.author: jroth
ms.openlocfilehash: c3d3bc340612286e211d85f52a3d914d1d1b6b9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597037"
---
# <a name="executing-templates-that-contain-sql-queries-sqlxmloledb-provider"></a><span data-ttu-id="181ea-102">執行包含 SQL 查詢的範本 (SQLXMLOLEDB 提供者)</span><span class="sxs-lookup"><span data-stu-id="181ea-102">Executing Templates That Contain SQL Queries (SQLXMLOLEDB Provider)</span></span>
  <span data-ttu-id="181ea-103">這個範例說明如何使用 SQLXMLOLEDB 提供者特定的屬性 ClientSideXML。</span><span class="sxs-lookup"><span data-stu-id="181ea-103">This example illustrates the use of the SQLXMLOLEDB Provider-specific property ClientSideXML.</span></span> <span data-ttu-id="181ea-104">在此用戶端 ADO 範例應用程式中，由 SQL 查詢所組成的 XML 範本會在伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="181ea-104">In this client-side ADO sample application, an XML template that consists of an SQL query is executed on the server.</span></span>  
  
 <span data-ttu-id="181ea-105">因為 ClientSideXML 屬性設定為 True，所以不含 FOR XML 子句的 SELECT 語句會傳送至伺服器。</span><span class="sxs-lookup"><span data-stu-id="181ea-105">Because the ClientSideXML property is set to True, the SELECT statement without the FOR XML clause is sent to the server.</span></span> <span data-ttu-id="181ea-106">伺服器會執行查詢，並將資料列集傳回給用戶端。</span><span class="sxs-lookup"><span data-stu-id="181ea-106">The server executes the query and returns a rowset to the client.</span></span> <span data-ttu-id="181ea-107">用戶端接著會將 FOR XML 轉換套用至資料列集，並產生 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="181ea-107">The client then applies the FOR XML transformation to the rowset and produces an XML document.</span></span>  
  
 <span data-ttu-id="181ea-108">XML 範本會針對所產生的 XML 檔提供單一最上層根項目 (\<ROOT>) ，因此不會提供 xml 根屬性。</span><span class="sxs-lookup"><span data-stu-id="181ea-108">The XML template provides a single top-level root element (\<ROOT>) for the XML document that is generated; therefore, the xml root property is not provided.</span></span>  
  
 <span data-ttu-id="181ea-109">若要執行 XML 範本，必須指定 Dialect {5d531cb2-e6ed-11d2-b252-00c04f681b71}。</span><span class="sxs-lookup"><span data-stu-id="181ea-109">To execute XML templates, the dialect {5d531cb2-e6ed-11d2-b252-00c04f681b71} must be specified.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="181ea-110">在程式碼中，您必須於連接字串內提供 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="181ea-110">In the code, you must provide the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span> <span data-ttu-id="181ea-111">此外，這個範例會指定針對資料提供者使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) (需要安裝其他網路用戶端軟體)。</span><span class="sxs-lookup"><span data-stu-id="181ea-111">Also, this example specifies the use of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) for the data provider which requires additional network client software to be installed.</span></span> <span data-ttu-id="181ea-112">如需詳細資訊，請參閱[SQL Server Native Client 的系統需求](../../native-client/system-requirements-for-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="181ea-112">For more information, see [System Requirements for SQL Server Native Client](../../native-client/system-requirements-for-sql-server-native-client.md).</span></span>  
  
```  
Option Explicit  
  
Sub Main()  
  Dim oTestStream As New ADODB.Stream  
  Dim oTestConnection As New ADODB.Connection  
  Dim oTestCommand As New ADODB.Command  
  oTestConnection.Open "Provider=SQLXMLOLEDB.4.0;Data Provider=SQLNCLI11;Data Source=SqlServerName;Initial Catalog=AdventureWorks;Integrated Security=SSPI;"  
  
  Set oTestCommand.ActiveConnection = oTestConnection  
  oTestCommand.Properties("ClientSideXML") = True  
  oTestCommand.CommandText = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'> " & _  
        " <sql:query> " & _  
        "   SELECT TOP 10 FirstName, LastName FROM Person.Contact FOR XML AUTO " & _  
        "   </sql:query> " & _  
        " </ROOT> "  
  oTestStream.Open  
  ' You need the dialect if you are executing   
  ' XML templates (not for SQL queries).  
  oTestCommand.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
  oTestCommand.Properties("Output Stream").Value = oTestStream  
  oTestCommand.Execute , , adExecuteStream  
  
  oTestStream.Position = 0  
  oTestStream.Charset = "utf-8"  
  Debug.Print oTestStream.ReadText(adReadAll)  
End Sub  
  
Sub Form_Load()  
  Main  
End Sub  
```  
  
  
