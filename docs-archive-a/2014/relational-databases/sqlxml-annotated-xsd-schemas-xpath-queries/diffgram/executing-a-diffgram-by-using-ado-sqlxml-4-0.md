---
title: 使用 ADO 執行 DiffGram (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- providers [SQLXML], SQLOLEDB Provider
- ADO [SQLXML]
- SQLXMLOLEDB Provider, DiffGrams
- data providers [SQLXML], SQLOLEDB Provider
- DiffGrams [SQLXML], ADO
ms.assetid: 741fce82-de83-4923-86eb-30acb5b9a5e6
author: rothja
ms.author: jroth
ms.openlocfilehash: b96db25fd46b1ecbbc15c8acd912743e5560f178
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596597"
---
# <a name="executing-a-diffgram-by-using-ado-sqlxml-40"></a><span data-ttu-id="00438-102">使用 ADO 執行 DiffGram (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="00438-102">Executing a DiffGram by Using ADO (SQLXML 4.0)</span></span>
  <span data-ttu-id="00438-103">這個 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic 應用程式會使用 ADO 來建立 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的連接，然後執行 DiffGram。</span><span class="sxs-lookup"><span data-stu-id="00438-103">This [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic application uses ADO to establish a connection to an instance of Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and then executes a DiffGram.</span></span> <span data-ttu-id="00438-104">在此應用程式中，DiffGram 和 XSD 結構描述會儲存在一個檔案中。</span><span class="sxs-lookup"><span data-stu-id="00438-104">In this application, the DiffGram and the XSD schema are stored in a file.</span></span> <span data-ttu-id="00438-105">應用程式會從指定的檔案載入 DiffGram。</span><span class="sxs-lookup"><span data-stu-id="00438-105">The application loads the DiffGram from the specified file.</span></span> <span data-ttu-id="00438-106">您可以使用任何 Diffgram (和相關聯的 XSD 架構) ，如[DiffGram 範例](diffgram-examples-sqlxml-4-0.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="00438-106">You can use any of the DiffGrams (and the associated XSD schema) described in [DiffGram Examples](diffgram-examples-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="00438-107">這是範例應用程式的程序：</span><span class="sxs-lookup"><span data-stu-id="00438-107">This is the process for the sample application:</span></span>  
  
-   <span data-ttu-id="00438-108"> (ADODB 的**conn**物件 **。連接**) 會建立與特定伺服器上 SQL Server 之執行中實例的連接。</span><span class="sxs-lookup"><span data-stu-id="00438-108">The **conn** object (**ADODB.Connection**) establishes a connection to a running instance of SQL Server on a specific server.</span></span>  
  
-   <span data-ttu-id="00438-109">**Cmd**物件 (**ADODB** ，) 會在已建立的連接上執行。</span><span class="sxs-lookup"><span data-stu-id="00438-109">The **cmd** object (**ADODB.Command**) executes on the established connection.</span></span>  
  
-   <span data-ttu-id="00438-110">命令用語會設定為 DBGUID_MSSQLXML。</span><span class="sxs-lookup"><span data-stu-id="00438-110">The command dialect is set to DBGUID_MSSQLXML.</span></span>  
  
-   <span data-ttu-id="00438-111">DiffGram 會從檔案複製到命令資料流程 (**字串分 text.append**) 。</span><span class="sxs-lookup"><span data-stu-id="00438-111">The DiffGram is copied to the command stream (**strmIn**) from a file.</span></span>  
  
-   <span data-ttu-id="00438-112">命令的輸出資料流程會設定為**StrmOut**物件 (**ADODB。串流**) 以接收任何傳回的資料。</span><span class="sxs-lookup"><span data-stu-id="00438-112">The command's output stream is set to the **StrmOut** object (**ADODB.Stream**) to receive any returned data.</span></span>  
  
-   <span data-ttu-id="00438-113">當您使用 SQLOLEDB 提供者時，根據預設，您會取得 Sqlxmlx.dll 提供的 Microsoft SQLXML 功能。</span><span class="sxs-lookup"><span data-stu-id="00438-113">When you are using the SQLOLEDB Provider, by default you will get the Microsoft SQLXML functionality provided by Sqlxmlx.dll.</span></span> <span data-ttu-id="00438-114">若要使用 Sqlxml4.dll 搭配 SQLOLEDB 提供者，必須在 SQLOLEDB 提供者**連接**物件上，將**sqlxml Version**屬性設定為**sqlxml. 4.0。**</span><span class="sxs-lookup"><span data-stu-id="00438-114">To use Sqlxml4.dll with the SQLOLEDB Provider, the **SQLXML Version** property must be set to **SQLXML.4.0** on the SQLOLEDB Provider **Connection** object.</span></span>  
  
-   <span data-ttu-id="00438-115">執行命令 (DiffGram)。</span><span class="sxs-lookup"><span data-stu-id="00438-115">The command (DiffGram) is executed.</span></span>  
  
 <span data-ttu-id="00438-116">下列程式碼是範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="00438-116">The following code is the sample application.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="00438-117">在程式碼中，您必須於連接字串內提供 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="00438-117">In the code, you must provide the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in the connection string.</span></span>  
  
```  
Private Sub Command1_Click()  
  Dim cmd As New ADODB.Command  
  Dim conn As New ADODB.Connection  
  Dim strmOut As New ADODB.Stream  
  Dim strmIn As New ADODB.Stream  
  
  'Open a connection to SQL Server.  
  conn.Provider = "SQLOLEDB"  
  conn.Open "server=SqlServerName; database=tempdb; Integrated Security=SSPI; "  
  conn.Properties("SQLXML Version") = "SQLXML.4.0"  
  Set cmd.ActiveConnection = conn  
  strmIn.Open  
  strmIn.Charset = "UTF-8"  
  strmIn.LoadFromFile "C:\SomeFilePath\SampleDiffGram.xml"  
  strmIn.Position = 0  
  Set cmd.CommandStream = strmIn  
  
  strmOut.Open  
  cmd.Properties("Output Stream").Value = strmOut  
  cmd.Properties("Output Encoding").Value = "UTF-8"  
  
  cmd.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
  cmd.Properties("Mapping Schema") = "C:\SomeFilePath\SampleDiffGram.xml"  
  cmd.Execute , , adExecuteStream  
  strmOut.Position = 0  
  Set cmd = Nothing  
  strmOut.Charset = "UTF-8"  
  strmOut.SaveToFile "C:\DropIt.txt", adSaveCreateOverWrite  
  strmOut.Close  
  Set strmOut = Nothing  
  
End Sub  
```  
  
### <a name="to-test-the-diffgram"></a><span data-ttu-id="00438-118">若要測試 DiffGram</span><span class="sxs-lookup"><span data-stu-id="00438-118">To test the DiffGram</span></span>  
  
1.  <span data-ttu-id="00438-119">如果您是電腦上的資料夾，請從[DiffGram 範例](diffgram-examples-sqlxml-4-0.md)中的其中一個範例複製其中一個 diffgram 和對應的 XSD 架構。</span><span class="sxs-lookup"><span data-stu-id="00438-119">To a folder on your computer, copy any one of the DiffGrams and the corresponding XSD schema from one of the examples in [DiffGram Examples](diffgram-examples-sqlxml-4-0.md).</span></span>  
  
2.  <span data-ttu-id="00438-120">開啟 Visual Basic，然後建立一個標準的 EXE 專案。</span><span class="sxs-lookup"><span data-stu-id="00438-120">Open Visual Basic and create a Standard EXE project.</span></span>  
  
3.  <span data-ttu-id="00438-121">將這些參考加入到專案中：</span><span class="sxs-lookup"><span data-stu-id="00438-121">Add these references to the project:</span></span>  
  
    ```  
    Microsoft ActiveX Data Objects 2.8 Library  
    ```  
  
4.  <span data-ttu-id="00438-122">在 [工具箱] 中，按一下 [**命令**]，然後在表單上繪製一個按鈕。</span><span class="sxs-lookup"><span data-stu-id="00438-122">In the Toolbox, click **CommandButton**, and then draw a button on the form.</span></span>  
  
5.  <span data-ttu-id="00438-123">按兩下該按鈕來編輯程式碼，然後加入主題中提供之應用程式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="00438-123">Double-click the button to edit the code, and add the application code that is provided in the topic.</span></span>  
  
6.  <span data-ttu-id="00438-124">編輯程式碼以指定 DiffGram 和 XSD 檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="00438-124">Edit the code to specify the DiffGram and XSD file names.</span></span> <span data-ttu-id="00438-125">同時在適當時，編輯連接字串。</span><span class="sxs-lookup"><span data-stu-id="00438-125">Also edit the connection string as appropriate.</span></span>  
  
7.  <span data-ttu-id="00438-126">執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="00438-126">Execute the application.</span></span> <span data-ttu-id="00438-127">執行的結果取決於您所執行的 DiffGram。</span><span class="sxs-lookup"><span data-stu-id="00438-127">The result of the execution depends on what DiffGram you are executing.</span></span>  
  
  
