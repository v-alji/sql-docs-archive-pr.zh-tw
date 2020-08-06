---
title: " (SQLXMLOLEDB 提供者套用 XSL 轉換) |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXMLOLEDB Provider, applying XSL transformations
- applying XSL transformations [SQLXML]
- xsl property
- Base Path property
- XSL Transformations [SQLXML]
ms.assetid: cb5e41ab-dd20-4873-af20-f417bd1bbf6d
author: rothja
ms.author: jroth
ms.openlocfilehash: 7fbb427a95d9f2308bf65724758a4a1563b42575
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597038"
---
# <a name="applying-an-xsl-transformation-sqlxmloledb-provider"></a><span data-ttu-id="23d6d-102">套用 XSL 轉換 (SQLXMLOLEDB 提供者)</span><span class="sxs-lookup"><span data-stu-id="23d6d-102">Applying an XSL Transformation (SQLXMLOLEDB Provider)</span></span>
  <span data-ttu-id="23d6d-103">在此範例 ADO 應用程式中，會執行 SQL 查詢，而且會將 XSL 轉換套用到結果中。</span><span class="sxs-lookup"><span data-stu-id="23d6d-103">In this sample ADO application, an SQL query is executed, and an XSL transformation is applied to the result.</span></span> <span data-ttu-id="23d6d-104">將 ClientSideXML 屬性設定為 True 會強制處理用戶端上的資料列集。</span><span class="sxs-lookup"><span data-stu-id="23d6d-104">Setting the ClientSideXML property to True enforces the processing of the rowset on the client side.</span></span> <span data-ttu-id="23d6d-105">命令用語設定為 {5d531cb2-e6ed-11d2-b252-00c04f681b71}，因為 SQL 查詢是在範本中指定，而且此用語必須在執行範本時指定。</span><span class="sxs-lookup"><span data-stu-id="23d6d-105">The command dialect is set to {5d531cb2-e6ed-11d2-b252-00c04f681b71}, because the SQL query is specified in a template and this dialect must be specified when executing a template.</span></span> <span data-ttu-id="23d6d-106">Xsl 屬性會指定要用來套用轉換的 XSL 檔案。</span><span class="sxs-lookup"><span data-stu-id="23d6d-106">The xsl property specifies the XSL file to use to apply the transformation.</span></span> <span data-ttu-id="23d6d-107">[基底路徑] 屬性的值是用來搜尋 XSL 檔案。</span><span class="sxs-lookup"><span data-stu-id="23d6d-107">The value of Base Path property is used to search for the XSL file.</span></span> <span data-ttu-id="23d6d-108">如果您在 [xsl] 屬性的值中指定路徑，則路徑會相對於 [基底路徑] 屬性中指定的路徑。</span><span class="sxs-lookup"><span data-stu-id="23d6d-108">If you specify a path in the value of the xsl property, the path is relative to the path that is specified in the Base Path property.</span></span>  
  
 <span data-ttu-id="23d6d-109">此範例顯示如何使用下列 SQLXMLOLEDB 提供者專屬的屬性：</span><span class="sxs-lookup"><span data-stu-id="23d6d-109">This example shows how to use the following SQLXMLOLEDB Provider-specific properties:</span></span>  
  
-   <span data-ttu-id="23d6d-110">ClientSideXML</span><span class="sxs-lookup"><span data-stu-id="23d6d-110">ClientSideXML</span></span>  
  
-   <span data-ttu-id="23d6d-111">xsl</span><span class="sxs-lookup"><span data-stu-id="23d6d-111">xsl</span></span>  
  
 <span data-ttu-id="23d6d-112">在此用戶端 ADO 範例應用程式中，由 SQL 查詢所組成的 XML 範本會在伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="23d6d-112">In this client-side ADO sample application, an XML template that consists of an SQL query is executed on the server.</span></span>  
  
 <span data-ttu-id="23d6d-113">因為 ClientSideXML 屬性設定為 True，所以不含 FOR XML 子句的 SELECT 語句會傳送至伺服器。</span><span class="sxs-lookup"><span data-stu-id="23d6d-113">Because the ClientSideXML property is set to True, the SELECT statement without the FOR XML clause is sent to the server.</span></span> <span data-ttu-id="23d6d-114">伺服器會執行查詢，並將資料列集傳回給用戶端。</span><span class="sxs-lookup"><span data-stu-id="23d6d-114">The server executes the query and returns a rowset to the client.</span></span> <span data-ttu-id="23d6d-115">用戶端接著會將 FOR XML 轉換套用至資料列集，並產生 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="23d6d-115">The client then applies the FOR XML transformation to the rowset and produces the XML document.</span></span>  
  
 <span data-ttu-id="23d6d-116">在應用程式中指定了 xsl 屬性。因此，XSL 轉換會套用至用戶端所產生的 XML 檔，而結果會是兩個數據行的資料表。</span><span class="sxs-lookup"><span data-stu-id="23d6d-116">The xsl property is specified in the application; therefore, the XSL transformation is applied to the XML document that is generated on the client, and the result is a two-column table.</span></span>  
  
 <span data-ttu-id="23d6d-117">若要執行範本命令，必須指定 XML 範本方言-{5d531cb2-e6ed-11d2-b252-00c04f681b71}-。</span><span class="sxs-lookup"><span data-stu-id="23d6d-117">To execute the template command, the XML template dialect - {5d531cb2-e6ed-11d2-b252-00c04f681b71} - must be specified.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="23d6d-118">在程式碼中，您必須於連接字串內提供 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="23d6d-118">In the code, you must provide the name of the instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span> <span data-ttu-id="23d6d-119">此外，這個範例會指定 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 用於資料提供者 (這需要安裝其他網路用戶端軟體)。</span><span class="sxs-lookup"><span data-stu-id="23d6d-119">Also, this example specifies the use of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client for the data provider which requires additional network client software to be installed.</span></span> <span data-ttu-id="23d6d-120">如需詳細資訊，請參閱[SQL Server Native Client 的系統需求](../../native-client/system-requirements-for-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="23d6d-120">For more information, see [System Requirements for SQL Server Native Client](../../native-client/system-requirements-for-sql-server-native-client.md).</span></span>  
  
```  
Option Explicit  
Sub main()  
Dim oTestStream As New ADODB.Stream  
Dim oTestConnection As New ADODB.Connection  
Dim oTestCommand As New ADODB.Command  
oTestConnection.Open "provider=SQLXMLOLEDB.4.0;data provider=SQLNCLI11;data source=SqlServerName;initial catalog=AdventureWorks;Integrated Security=SSPI;"  
Set oTestCommand.ActiveConnection = oTestConnection  
oTestCommand.Properties("ClientSideXML") = True  
oTestCommand.CommandText = _  
        "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql' >" & _  
       " <sql:query> " & _  
        "   SELECT TOP 25 FirstName, LastName FROM Person.Contact FOR XML AUTO " & _  
        "   </sql:query> " & _  
        " </ROOT> "  
oTestStream.Open  
' You need the dialect if you are executing a template.  
oTestCommand.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
oTestCommand.Properties("Output Stream").Value = oTestStream  
oTestCommand.Properties("Base Path").Value = "c:\Schemas\SQLXML4\ExecuteTemplateWithXSL\"  
oTestCommand.Properties("xsl").Value = "myxsl.xsl"  
oTestCommand.Execute , , adExecuteStream  
  
oTestStream.Position = 0  
oTestStream.Charset = "utf-8"  
Debug.Print oTestStream.ReadText(adReadAll)  
End Sub  
Sub Form_Load()  
 main  
End Sub  
```  
  
 <span data-ttu-id="23d6d-121">XSL 範本如下。</span><span class="sxs-lookup"><span data-stu-id="23d6d-121">The XSL template follows.</span></span> <span data-ttu-id="23d6d-122">套用此 XSL 範本的結果為兩個資料行的資料表。</span><span class="sxs-lookup"><span data-stu-id="23d6d-122">The result of applying this XSL template is a two-column table.</span></span>  
  
```  
<?xml version='1.0' encoding='UTF-8'?>            
 <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">   
  
    <xsl:template match = 'Person.Contact'>  
       <TR>  
         <TD><xsl:value-of select = '@FirstName' /></TD>  
         <TD><B><xsl:value-of select = '@LastName' /></B></TD>  
       </TR>  
    </xsl:template>  
    <xsl:template match = '/'>  
      <HTML>  
        <HEAD>  
           <STYLE>th { background-color: #CCCCCC }</STYLE>  
        </HEAD>  
        <BODY>  
         <TABLE border='1' style='width:300;'>  
           <TR><TH colspan='2'>Contacts</TH></TR>  
           <TR>  
              <TH >First name</TH>  
              <TH>Last name</TH>  
           </TR>  
           <xsl:apply-templates select = 'ROOT' />  
         </TABLE>  
        </BODY>  
      </HTML>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
  
