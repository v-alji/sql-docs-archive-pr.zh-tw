---
title: " (SQLXMLOLEDB 提供者) 執行 SQL 查詢Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- queries [SQLXML], SQLXMLOLEDB Provider
- xml root property [SQLXML]
- SQLXMLOLEDB Provider, executing SQL queries
- SQL queries [SQLXML]
ms.assetid: 50334cf5-9c87-4c00-9beb-e08577c4fa82
author: rothja
ms.author: jroth
ms.openlocfilehash: a1e2cc87f90700e3b81a5a2ec3dd80f219a9b1d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597751"
---
# <a name="executing-sql-queries-sqlxmloledb-provider"></a><span data-ttu-id="9f638-102">執行 SQL 查詢 (SQLXMLOLEDB 提供者)</span><span class="sxs-lookup"><span data-stu-id="9f638-102">Executing SQL Queries (SQLXMLOLEDB Provider)</span></span>
  <span data-ttu-id="9f638-103">此範例示範如何使用下列 SQLXMLOLEDB 提供者專屬的屬性：</span><span class="sxs-lookup"><span data-stu-id="9f638-103">This example illustrates the use of the following SQLXMLOLEDB Provider-specific properties:</span></span>  
  
-   <span data-ttu-id="9f638-104">ClientSideXML</span><span class="sxs-lookup"><span data-stu-id="9f638-104">ClientSideXML</span></span>  
  
-   <span data-ttu-id="9f638-105">xml root</span><span class="sxs-lookup"><span data-stu-id="9f638-105">xml root</span></span>  
  
 <span data-ttu-id="9f638-106">在此用戶端的 ADO 範例應用程式中，會在用戶端上執行簡單的 SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="9f638-106">In this client-side ADO sample application, a simple SQL query is executed on the client.</span></span> <span data-ttu-id="9f638-107">因為 ClientSideXML 屬性設定為 True，所以不含 FOR XML 子句的 SELECT 語句會傳送至伺服器。</span><span class="sxs-lookup"><span data-stu-id="9f638-107">Because the ClientSideXML property is set to True, the SELECT statement without the FOR XML clause is sent to the server.</span></span> <span data-ttu-id="9f638-108">伺服器會執行查詢，並將資料列集傳回給用戶端。</span><span class="sxs-lookup"><span data-stu-id="9f638-108">The server executes the query and returns a rowset to the client.</span></span> <span data-ttu-id="9f638-109">用戶端接著會將 FOR XML 轉換套用至資料列集，並產生 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="9f638-109">The client then applies the FOR XML transformation to the rowset and produces an XML document.</span></span>  
  
 <span data-ttu-id="9f638-110">Xml 根屬性會為所產生的 XML 檔提供單一最上層根項目。</span><span class="sxs-lookup"><span data-stu-id="9f638-110">The xml root property provides the single top-level root element for the XML document that is generated.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f638-111">在程式碼中，您必須於連接字串內提供 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="9f638-111">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span> <span data-ttu-id="9f638-112">此外，這個範例會指定針對資料提供者使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) (需要安裝其他網路用戶端軟體)。</span><span class="sxs-lookup"><span data-stu-id="9f638-112">Also, this example specifies the use of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) for the data provider, which requires additional network client software to be installed.</span></span> <span data-ttu-id="9f638-113">如需詳細資訊，請參閱[SQL Server Native Client 的系統需求](../../native-client/system-requirements-for-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="9f638-113">For more information, see [System Requirements for SQL Server Native Client](../../native-client/system-requirements-for-sql-server-native-client.md).</span></span>  
  
```  
Option Explicit  
Sub main()  
Dim oTestStream As New ADODB.Stream  
Dim oTestConnection As New ADODB.Connection  
Dim oTestCommand As New ADODB.Command  
  
oTestConnection.Open "provider=SQLXMLOLEDB.4.0;data provider=SQLNCLI11;data source=SqlServerName;initial catalog=AdventureWorks;Integrated Security=SSPI ;"  
oTestCommand.ActiveConnection = oTestConnection  
oTestCommand.Properties("ClientSideXML") = True  
oTestCommand.CommandText = "SELECT TOP 10 FirstName, LastName FROM Person.Contact FOR XML AUTO"  
oTestStream.Open  
oTestCommand.Properties("Output Stream").Value = oTestStream  
oTestCommand.Properties("xml root") = "root"  
oTestCommand.Execute , , adExecuteStream  
  
oTestStream.Position = 0  
oTestStream.Charset = "utf-8"  
Debug.Print oTestStream.ReadText(adReadAll)  
End Sub  
Sub Form_Load()  
 main  
End Sub  
```  
  
  
