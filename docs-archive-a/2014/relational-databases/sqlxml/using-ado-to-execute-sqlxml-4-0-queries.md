---
title: 使用 ADO 執行 SQLXML 4.0 查詢
ms.custom: ''
ms.date: 12/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- query testers [SQLXML]
- test scripts
- ADO [SQLXML]
- queries [SQLXML], ADO
- SQLXML, ADO
ms.assetid: 3d54e3bb-7c5f-427e-82f8-1403a54c4f53
author: rothja
ms.author: jroth
ms.openlocfilehash: 169d20b4192e4a5b8e7b32839f2da255fc58d89c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687749"
---
# <a name="using-ado-to-execute-sqlxml-40-queries"></a><span data-ttu-id="0da8a-102">使用 ADO 執行 SQLXML 4.0 查詢</span><span class="sxs-lookup"><span data-stu-id="0da8a-102">Using ADO to Execute SQLXML 4.0 Queries</span></span>
  <span data-ttu-id="0da8a-103">在舊版的 SQLXML 中，可使用 SQLXML IIS 虛擬目錄和 SQLXML ISAPI 篩選來支援以 HTTP 為基礎的查詢執行。</span><span class="sxs-lookup"><span data-stu-id="0da8a-103">In previous versions of SQLXML, HTTP-based query execution was supported using SQLXML IIS virtual directories and the SQLXML ISAPI filter.</span></span> <span data-ttu-id="0da8a-104">在 SQLXML 4.0 中已經移除這些元件，因為自 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 開始引進的原生 XML Web 服務提供了類似且重疊的功能。</span><span class="sxs-lookup"><span data-stu-id="0da8a-104">In SQLXML 4.0, these components have been removed as similar and overlapping functionality is provided with native XML Web services beginning in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="0da8a-105">另一種選擇是利用在 Microsoft Data Access Components (MDAC) 2.6 和更新版本中初次引進的 ActiveX Data Objects (ADO) 的 SQL XML 延伸模組來執行查詢，並使用 SQLXML 4.0 來搭配以 COM 為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0da8a-105">As an alternative, you can execute queries and use SQLXML 4.0 with your COM-based applications, by leveraging the SQLXML extensions to ActiveX Data Objects (ADO) that were first introduced in Microsoft Data Access Components (MDAC) 2.6 and later.</span></span>  
  
 <span data-ttu-id="0da8a-106">本主題示範如何使用 SQLXML 和 ADO 以當做 Visual Basic Scripting Edition (VBScript) 應用程式的一部分 (具有 .vbs 副檔名的指令碼)。</span><span class="sxs-lookup"><span data-stu-id="0da8a-106">This topic demonstrates using SQLXML and ADO as part of a Visual Basic Scripting Edition (VBScript) application (a script with the .vbs file extension).</span></span> <span data-ttu-id="0da8a-107">本主題提供初始的安裝程序，以協助您重建和測試 SQLXML 4.0 文件集中的查詢範例。</span><span class="sxs-lookup"><span data-stu-id="0da8a-107">It provides initial setup procedures to help you recreate and test query samples in the SQLXML 4.0 documentation.</span></span>  
  
## <a name="creating-the-sqlxml-40-test-script"></a><span data-ttu-id="0da8a-108">建立 SQLXML 4.0 測試指令碼</span><span class="sxs-lookup"><span data-stu-id="0da8a-108">Creating the SQLXML 4.0 Test Script</span></span>  
 <span data-ttu-id="0da8a-109">在此程序中，您會建立 VBScript (.vbs) 檔案 Sqlxml4test.vbs，這個檔案可利用 ADO 2.6 和更新版本的 SQLXML ADO 延伸模組來執行 SQLXML 查詢。</span><span class="sxs-lookup"><span data-stu-id="0da8a-109">In this procedure, you create a VBScript (.vbs) file, Sqlxml4test.vbs, which can be used to execute SQLXML queries by leveraging the SQLXML ADO extensions in ADO 2.6 and later.</span></span>  
  
#### <a name="to-create-the-sqlxml-40-query-tester-using-ado-vbscript"></a><span data-ttu-id="0da8a-110">使用 ADO (VBScript) 建立 SQLXML 4.0 查詢測試者</span><span class="sxs-lookup"><span data-stu-id="0da8a-110">To create the SQLXML 4.0 query tester using ADO (VBScript).</span></span>  
  
1.  <span data-ttu-id="0da8a-111">複製下列 VBScript 程式碼，並將它貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="0da8a-111">Copy the VBScript code below, and paste it into a text file.</span></span> <span data-ttu-id="0da8a-112">將檔案儲存為 Sqlxml4test.vbs。</span><span class="sxs-lookup"><span data-stu-id="0da8a-112">Save the file as Sqlxml4test.vbs.</span></span>  
  
    ```vb
    WScript.Echo "Query process may take a few seconds to complete. Please be patient."  
  
    ' Note that for SQL Server Native Client to be used as the data provider,  
    ' it needs to be installed on the client computer first. Also, SQLXML extensions   
    ' for ADO are used and available in MDAC 2.6 or later.  
  
    'Set script variables.  
    inputFile = "@@FILE_NAME@@"  
    strServer = "@@SERVER_NAME@@"  
    strDatabase = "@@DATABASE_NAME@@"  
    dbGuid = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
  
    ' Establish ADO connection to SQL Server and   
    ' create an instance of the ADO Command object.  
    Set conn = CreateObject("ADODB.Connection")  
    Set cmd = CreateObject("ADODB.Command")  
    conn.Open "Provider=SQLXMLOLEDB.4.0;Data Provider=SQLNCLI11;Server=" & strServer & _  
              ";Database=" & strDatabase & ";Integrated Security=SSPI"  
    Set cmd.ActiveConnection = conn  
  
    ' Create the input stream as an instance of the ADO Stream object.  
    Set inStream = CreateObject("ADODB.Stream")  
    inStream.Open  
    inStream.Charset = "utf-8"  
    inStream.LoadFromFile inputFile  
  
    ' Set ADO Command instance to use input stream.  
    Set cmd.CommandStream = inStream  
  
    ' Set the command dialect.  
    cmd.Dialect = dbGuid  
  
    ' Set a second ADO Stream instance for use as a results stream.   
    Set outStream = CreateObject("ADODB.Stream")  
    outStream.Open  
  
    ' Set dynamic properties used by the SQLXML ADO command instance.   
    cmd.Properties("XML Root").Value = "ROOT"  
    cmd.Properties("Output Encoding").Value = "UTF-8"  
  
    ' Connect the results stream to the command instance and execute the command.  
    cmd.Properties("Output Stream").Value = outStream  
    cmd.Execute , , 1024  
  
    ' Echo cropped/partial results to console.  
    WScript.Echo Left(outStream.ReadText, 1023)  
  
    inStream.Close  
    outStream.Close  
    ```  
  
2.  <span data-ttu-id="0da8a-113">針對您正嘗試測試的範例及您的測試環境更新下列的指令碼值。</span><span class="sxs-lookup"><span data-stu-id="0da8a-113">Update the following script values for the sample you are trying to test and your test environment.</span></span>  
  
    -   <span data-ttu-id="0da8a-114">尋找 "`@@FILE_NAME@@`"，並以您的範例檔名稱加以取代。</span><span class="sxs-lookup"><span data-stu-id="0da8a-114">Find "`@@FILE_NAME@@`" and replace it with the name of your template file.</span></span>  
  
    -   <span data-ttu-id="0da8a-115">尋找 "`@@SERVER_NAME@@`"，並以您的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的名稱加以取代 (例如，如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在本機執行，則為 "`(local)`")。</span><span class="sxs-lookup"><span data-stu-id="0da8a-115">Find "`@@SERVER_NAME@@`" and replace it with the name of your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance (for example, "`(local)`" if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is running locally).</span></span>  
  
    -   <span data-ttu-id="0da8a-116">尋找 "`@@DATABASE_NAME@@`"，並以資料庫的名稱加以取代 (例如，"`AdventureWorks2012`" 或 "`tempdb`")。</span><span class="sxs-lookup"><span data-stu-id="0da8a-116">Find "`@@DATABASE_NAME@@`" and replace it with the name of the database (for example, either "`AdventureWorks2012`" or "`tempdb`").</span></span>  
  
     <span data-ttu-id="0da8a-117">更新任何的其他值 (若您嘗試在電腦本機上重新建立之範例的特定指示中有提及)。</span><span class="sxs-lookup"><span data-stu-id="0da8a-117">Update any other values if mentioned in the specific instructions for the example you are attempting to recreate locally on your computer.</span></span>  
  
3.  <span data-ttu-id="0da8a-118">儲存並關閉檔案。</span><span class="sxs-lookup"><span data-stu-id="0da8a-118">Save the file and close it.</span></span>  
  
4.  <span data-ttu-id="0da8a-119">確認您已建立了任何其他的檔案，例如屬於您嘗試在電腦本機上重新建立之範例的 XML 範本或結構描述。</span><span class="sxs-lookup"><span data-stu-id="0da8a-119">Verify that you have created any additional files, such as XML templates or schemas that are part of the sample you are attempting to recreate locally on your computer.</span></span> <span data-ttu-id="0da8a-120">這些檔案應該位於與您儲存測試指令碼檔案 (Sqlxml4test.vbs) 相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="0da8a-120">These files should be located in the same directory where you have saved the test script file (Sqlxml4test.vbs).</span></span>  
  
5.  <span data-ttu-id="0da8a-121">請遵照下一節中的指示來使用 SQLXML 4.0 測試指令碼。</span><span class="sxs-lookup"><span data-stu-id="0da8a-121">Follow the instructions in the next section for how to use the SQLXML 4.0 test script.</span></span>  
  
## <a name="using-the-sqlxml-40-test-script"></a><span data-ttu-id="0da8a-122">使用 SQLXML 4.0 測試指令碼</span><span class="sxs-lookup"><span data-stu-id="0da8a-122">Using the SQLXML 4.0 Test Script</span></span>  
 <span data-ttu-id="0da8a-123">下列程序描述如何使用 Sqlxml4test.vbs 檔案來測試本文件集所提供的範例查詢。</span><span class="sxs-lookup"><span data-stu-id="0da8a-123">The following procedure describes how to use the Sqlxml4test.vbs files to test the example queries provided in this documentation.</span></span>  
  
#### <a name="to-use-the-sqlxml-40-query-tester"></a><span data-ttu-id="0da8a-124">使用 SQLXML 4.0 查詢測試者</span><span class="sxs-lookup"><span data-stu-id="0da8a-124">To use the SQLXML 4.0 query tester</span></span>  
  
1.  <span data-ttu-id="0da8a-125">確認已安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0da8a-125">Verify that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client is installed, as follows:</span></span>  
  
    1.  <span data-ttu-id="0da8a-126">在 [**開始**] 功能表中，指向 [**設定**]，然後按一下 [**控制台**]。</span><span class="sxs-lookup"><span data-stu-id="0da8a-126">From the **Start** menu, point to **Settings**, and then click **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="0da8a-127">在 [控制台] 中，開啟 [**新增或移除程式**]</span><span class="sxs-lookup"><span data-stu-id="0da8a-127">In Control Panel, open **Add or Remove Programs**</span></span>  
  
    3.  <span data-ttu-id="0da8a-128">在目前已安裝的程式清單中，確認 [ **Microsoft SQL Server Native Client** ] 出現在清單中。</span><span class="sxs-lookup"><span data-stu-id="0da8a-128">In the list of currently installed programs, verify that **Microsoft SQL Server Native Client** appears in the list.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="0da8a-129">如果您需要安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client，請參閱[安裝 SQL Server Native Client](../native-client/applications/installing-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="0da8a-129">If you need to install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, see [Installing SQL Server Native Client](../native-client/applications/installing-sql-server-native-client.md).</span></span>  
  
2.  <span data-ttu-id="0da8a-130">確認用戶端電腦所安裝的 MDAC 版本為 2.6 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="0da8a-130">Verify that the version of MDAC installed for the client computer is 2.6 or later.</span></span> <span data-ttu-id="0da8a-131">如果您需要驗證 MDAC 版本資訊，您可以使用 MDAC Component 檢查工具，這是從 Microsoft 網站免費下載提供 [https://www.microsoft.com/](https://www.microsoft.com/) 。</span><span class="sxs-lookup"><span data-stu-id="0da8a-131">If you need to verify MDAC version information, you can use the MDAC Component Checker tool, which is provided as free download from the Microsoft Web site [https://www.microsoft.com/](https://www.microsoft.com/).</span></span> <span data-ttu-id="0da8a-132">如需詳細資訊，請在 Microsoft 網站上搜尋「MDAC 元件檢查程式」。</span><span class="sxs-lookup"><span data-stu-id="0da8a-132">For more information, search on "MDAC Component Checker" on the Microsoft Web site.</span></span>  
  
3.  <span data-ttu-id="0da8a-133">執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="0da8a-133">Execute the script.</span></span>  
  
     <span data-ttu-id="0da8a-134">您可以在命令列使用 Cscript.exe 來執行 VBScript 檔案，或者按兩下 Sqlxml4test.vbs 檔案來叫用 Windows Script Host (WScript.exe)。</span><span class="sxs-lookup"><span data-stu-id="0da8a-134">You can execute the VBScript file either at the command line using Cscript.exe or by double-clicking Sqlxml4test.vbs file to invoke the Windows Script Host (WScript.exe).</span></span>  
  
     <span data-ttu-id="0da8a-135">此指令碼在執行時會顯示訊息，警示您指令碼可能需要一些時間執行，才能將查詢結果傳回並顯示為指令碼輸出。</span><span class="sxs-lookup"><span data-stu-id="0da8a-135">When executed, the script should display a message to alert you that the script might take a few moments to execute before returning and displaying query results as script output.</span></span> <span data-ttu-id="0da8a-136">當輸出出現時，請將其內容與範例的預期結果比較。</span><span class="sxs-lookup"><span data-stu-id="0da8a-136">When the output appears, compare its contents to the expected results for the sample.</span></span>  
  
  
