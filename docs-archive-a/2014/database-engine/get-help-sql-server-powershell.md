---
title: 取得 SQL Server PowerShell 說明 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Help [PowerShell]
- Help [SQL Server], PowerShell
- PowerShell [SQL Server], help
ms.assetid: 968c316d-db83-4c24-8ea6-9f18736842f7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f1d97a3b694eebb924f9e1ff228d4d38da4f45ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701584"
---
# <a name="get-help-sql-server-powershell"></a><span data-ttu-id="3fb75-102">Get Help SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="3fb75-102">Get Help SQL Server PowerShell</span></span>
  <span data-ttu-id="3fb75-103">有關使用適用於 Windows PowerShell 和指令程式之 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 提供者的資訊來源有幾個。</span><span class="sxs-lookup"><span data-stu-id="3fb75-103">There are several sources of information about using the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider for Windows PowerShell and cmdlets.</span></span> <span data-ttu-id="3fb75-104">其中包括 Windows PowerShell 環境中可用的說明。</span><span class="sxs-lookup"><span data-stu-id="3fb75-104">This includes the help that is available in the Windows PowerShell environment.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="3fb75-105">開始之前</span><span class="sxs-lookup"><span data-stu-id="3fb75-105">Before You Begin</span></span>  
 <span data-ttu-id="3fb75-106">若要了解 Windows PowerShell，請參閱 [Windows PowerShell 開始使用手冊](https://technet.microsoft.com/library/hh857337.aspx)。</span><span class="sxs-lookup"><span data-stu-id="3fb75-106">To learn about Windows PowerShell, see [Windows PowerShell Getting Started Guide](https://technet.microsoft.com/library/hh857337.aspx).</span></span>  
  
 <span data-ttu-id="3fb75-107">如需 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Cmdlet 和提供者的概觀，請參閱 [SQL Server PowerShell](../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="3fb75-107">For an overview of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlets and provider, see [SQL Server PowerShell](../powershell/sql-server-powershell.md).</span></span>  
  
### <a name="help-in-the-windows-powershell-environment"></a><span data-ttu-id="3fb75-108">Windows PowerShell 環境中的説明</span><span class="sxs-lookup"><span data-stu-id="3fb75-108">Help in the Windows PowerShell Environment</span></span>  
 <span data-ttu-id="3fb75-109">您可以使用 **Get-Help** Cmdlet，在 Windows PowerShell 環境中取得說明。</span><span class="sxs-lookup"><span data-stu-id="3fb75-109">Use the **Get-Help** cmdlet to get help in the Windows PowerShell environment.</span></span> <span data-ttu-id="3fb75-110">**Get-Help** 提供 Windows PowerShell 語言的基本說明，以及 Windows PowerShell 中可用的各種 Cmdlet 和提供者。</span><span class="sxs-lookup"><span data-stu-id="3fb75-110">**Get-Help** provides basic help for the Windows PowerShell language and the various cmdlets and providers available in Windows PowerShell.</span></span>  
  
 <span data-ttu-id="3fb75-111">如需使用 **Get-Help**之方式的詳細資訊，請參閱 [Get-Help：取得說明](https://go.microsoft.com/fwlink/?LinkId=102136)。</span><span class="sxs-lookup"><span data-stu-id="3fb75-111">For more information on the ways you can use **Get-Help**, see [Get-Help: Getting Help](https://go.microsoft.com/fwlink/?LinkId=102136).</span></span>  
  
### <a name="sql-server-powershell-provider-help"></a><span data-ttu-id="3fb75-112">SQL Server PowerShell 提供者說明</span><span class="sxs-lookup"><span data-stu-id="3fb75-112">SQL Server PowerShell Provider Help</span></span>  
 <span data-ttu-id="3fb75-113">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell 提供者實作 SQLSERVER 虛擬磁碟機上的數個資料夾，例如 SQLSERVER:\SQL 和 SQLSERVER:\DAC 資料夾。</span><span class="sxs-lookup"><span data-stu-id="3fb75-113">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell provider implements several folders on a SQLSERVER virtual drive, such as the SQLSERVER:\SQL and SQLSERVER:\DAC folders.</span></span> <span data-ttu-id="3fb75-114">每一個資料夾都會與一個 SQL Server 管理能力物件模型有關聯。</span><span class="sxs-lookup"><span data-stu-id="3fb75-114">Each folder is associated with one of the SQL Server manageability object models.</span></span> <span data-ttu-id="3fb75-115">雖然您可以列出與 SQL Server 路徑中每個節點相關聯的方法和屬性，但是無法在 PowerShell 環境中取得它們的說明。</span><span class="sxs-lookup"><span data-stu-id="3fb75-115">While you can list the methods and properties associated with each node in a SQL Server path, you cannot get help for them in the PowerShell environment.</span></span> <span data-ttu-id="3fb75-116">如需含有相關聯程式設計參考連結之資料夾的表格，請參閱 [SQL Server PowerShell 提供者](../powershell/sql-server-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="3fb75-116">For a table of the folders with links to the associated programming reference, see [SQL Server PowerShell Provider](../powershell/sql-server-powershell-provider.md).</span></span>  
  
### <a name="invoke-sqlcmd-help"></a><span data-ttu-id="3fb75-117">Invoke-Sqlcmd 說明</span><span class="sxs-lookup"><span data-stu-id="3fb75-117">Invoke-Sqlcmd Help</span></span>  
 <span data-ttu-id="3fb75-118">**Invoke-Sqlcmd** Cmdlet 會採用 **sqlcmd** 公用程式可執行的任何查詢或指令碼檔案作為輸入。</span><span class="sxs-lookup"><span data-stu-id="3fb75-118">The **Invoke-Sqlcmd** cmdlet takes as input any query or script file that can be run by the **sqlcmd** utility.</span></span> <span data-ttu-id="3fb75-119">您可以使用 **Get-Help** 取得有關 **Invoke-Sqlcmd** 和其參數的資訊，但是不包含 **sqlcmd** 查詢的 **Get-Help** 。</span><span class="sxs-lookup"><span data-stu-id="3fb75-119">You can use **Get-Help** to get information about **Invoke-Sqlcmd** and its parameters, but there is no **Get-Help** coverage for the **sqlcmd** queries.</span></span>  
  
 <span data-ttu-id="3fb75-120">*-Query* 或 *-QueryFromFile* 輸入可包含：</span><span class="sxs-lookup"><span data-stu-id="3fb75-120">The *-Query* or *-QueryFromFile* input can contain:</span></span>  
  
-   <span data-ttu-id="3fb75-121">**sqlcmd** 變數和命令。</span><span class="sxs-lookup"><span data-stu-id="3fb75-121">**sqlcmd** variables and commands.</span></span> <span data-ttu-id="3fb75-122">如需這些變數和命令的資訊，請參閱 [sqlcmd 公用程式](../tools/sqlcmd-utility.md)的＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="3fb75-122">For information about these variables and commands, see the Remarks section of [sqlcmd Utility](../tools/sqlcmd-utility.md).</span></span>  
  
-   [!INCLUDE[tsql](../includes/tsql-md.md)] <span data-ttu-id="3fb75-123">陳述式。</span><span class="sxs-lookup"><span data-stu-id="3fb75-123">statements.</span></span> <span data-ttu-id="3fb75-124">如需 [!INCLUDE[tsql](../includes/tsql-md.md)] 語言的詳細資訊，請參閱 [Transact-SQL 參考 &#40;Database Engine&#41;](/sql/t-sql/language-reference)。</span><span class="sxs-lookup"><span data-stu-id="3fb75-124">For more information about the [!INCLUDE[tsql](../includes/tsql-md.md)] language, see [Transact-SQL Reference &#40;Database Engine&#41;](/sql/t-sql/language-reference).</span></span>  
  
-   <span data-ttu-id="3fb75-125">XQuery 陳述式。</span><span class="sxs-lookup"><span data-stu-id="3fb75-125">XQuery statements.</span></span> <span data-ttu-id="3fb75-126">如需 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 所支援之 XQuery 語言的詳細資訊，請參閱 [XQuery 語言參考 &#40;SQL Server&#41;](/sql/xquery/xquery-language-reference-sql-server)。</span><span class="sxs-lookup"><span data-stu-id="3fb75-126">For more information about the XQuery language supported by [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [XQuery Language Reference &#40;SQL Server&#41;](/sql/xquery/xquery-language-reference-sql-server).</span></span>  
  
## <a name="get-help-for-a-sql-server-cmdlet"></a><span data-ttu-id="3fb75-127">取得 SQL Server Cmdlet 的説明</span><span class="sxs-lookup"><span data-stu-id="3fb75-127">Get Help for a SQL Server cmdlet</span></span>  
 <span data-ttu-id="3fb75-128">**取得 Cmdlet 的說明**</span><span class="sxs-lookup"><span data-stu-id="3fb75-128">**To get help for a cmdlet**</span></span>  
  
-   <span data-ttu-id="3fb75-129">指定 Cmdlet 的名稱以及要傳回的說明層級，以執行 Get-Help。</span><span class="sxs-lookup"><span data-stu-id="3fb75-129">Run Get-Help specifying the name of the cmdlet and the level of help to be returned.</span></span>  
  
### <a name="example-cmdlet-get-help"></a><span data-ttu-id="3fb75-130">範例：Get-Help Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3fb75-130">Example: cmdlet Get-Help</span></span>  
 <span data-ttu-id="3fb75-131">下列範例傳回 **Invoke-Sqlcmd**的各種說明層級：</span><span class="sxs-lookup"><span data-stu-id="3fb75-131">The following examples return various levels of help for **Invoke-Sqlcmd**:</span></span>  
  
```powershell
## Get the basic help.  
Get-Help Invoke-Sqlcmd  
  
## Get the full help.  
Get-Help Invoke-Sqlcmd -Full  
  
## Get the parameter descriptions.  
Get-Help Invoke-Sqlcmd -Parameter *  
  
## Get the code examples.  
Get-Help Invoke-Sqlcmd -Examples  
  
## Get the syntax diagram.  
Get-Help Invoke-Sqlcmd -Syntax  
```  
  
## <a name="get-a-list-of-providers"></a><span data-ttu-id="3fb75-132">取得提供者清單</span><span class="sxs-lookup"><span data-stu-id="3fb75-132">Get a List of Providers</span></span>  

### <a name="to-get-a-list-of-active-providers"></a><span data-ttu-id="3fb75-133">取得作用中的提供者清單</span><span class="sxs-lookup"><span data-stu-id="3fb75-133">To get a list of active providers</span></span>
  
1.  <span data-ttu-id="3fb75-134">指定提供者類別目錄，以執行 Get-Help。</span><span class="sxs-lookup"><span data-stu-id="3fb75-134">Run Get-Help specifying the provider category.</span></span>  
  
 <span data-ttu-id="3fb75-135">如需在 Windows PowerShell 中取得提供者說明的詳細資訊，請參閱 [磁碟機和提供者](https://go.microsoft.com/fwlink/?LinkId=102137)。</span><span class="sxs-lookup"><span data-stu-id="3fb75-135">For more information about getting provider help in Windows PowerShell, see [Drives and Providers](https://go.microsoft.com/fwlink/?LinkId=102137).</span></span>  
  
### <a name="example-get-a-list-of-providers"></a><span data-ttu-id="3fb75-136">範例：取得提供者清單</span><span class="sxs-lookup"><span data-stu-id="3fb75-136">Example: Get a List of Providers</span></span>  
 <span data-ttu-id="3fb75-137">此程式碼會傳回目前在 Windows PowerShell 工作階段中啟用的提供者清單：</span><span class="sxs-lookup"><span data-stu-id="3fb75-137">This code returns a list of the providers currently enabled in your Windows PowerShell session:</span></span>  
  
```powershell
Get-Help -Category provider  
```  
  
## <a name="get-help-about-the-sql-server-provider"></a><span data-ttu-id="3fb75-138">取得 SQL Server 提供者的說明</span><span class="sxs-lookup"><span data-stu-id="3fb75-138">Get Help About the SQL Server Provider</span></span>  
 <span data-ttu-id="3fb75-139">**取得提供者的相關說明**</span><span class="sxs-lookup"><span data-stu-id="3fb75-139">**To get help about the provider**</span></span>  
  
1.  <span data-ttu-id="3fb75-140">指定名稱 SQLServer，以執行 Get-Help</span><span class="sxs-lookup"><span data-stu-id="3fb75-140">Run Get-Help specifying the name SQLServer</span></span>  
  
### <a name="example-get-sql-server-provider-help"></a><span data-ttu-id="3fb75-141">範例：取得 SQL Server 提供者說明</span><span class="sxs-lookup"><span data-stu-id="3fb75-141">Example: Get SQL Server Provider Help</span></span>  
 <span data-ttu-id="3fb75-142">此範例會傳回 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 提供者的基本資訊：</span><span class="sxs-lookup"><span data-stu-id="3fb75-142">This example returns basic information about the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider:</span></span>  
  
```powershell
Get-Help SQLServer  
```  
  
## <a name="list-methods-and-properties"></a><span data-ttu-id="3fb75-143">列出方法和屬性</span><span class="sxs-lookup"><span data-stu-id="3fb75-143">List Methods and Properties</span></span>  
 <span data-ttu-id="3fb75-144">**列出 SQL Server 提供者路徑中節點的方法和屬性**</span><span class="sxs-lookup"><span data-stu-id="3fb75-144">**To list the methods and properties for a node in a SQL Server provider path**</span></span>  
  
1.  <span data-ttu-id="3fb75-145">CD (切換) 至 SQL Server 路徑中的節點，或建立該位置的變數集。</span><span class="sxs-lookup"><span data-stu-id="3fb75-145">Either CD to a node in the SQL Server path, or create a variable set to that location.</span></span>  
  
2.  <span data-ttu-id="3fb75-146">以-Type 參數設定為方法或屬性來執行**取得成員**Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3fb75-146">Run the **Get-Member** cmdlet with the -Type parameter set to either Methods or Properties</span></span>  
  
### <a name="examples-listing-methods-and-properties"></a><span data-ttu-id="3fb75-147">範例：列出方法與屬性</span><span class="sxs-lookup"><span data-stu-id="3fb75-147">Examples: Listing Methods and Properties</span></span>  
 <span data-ttu-id="3fb75-148">此範例列出 Databases 節點所支援的方法：</span><span class="sxs-lookup"><span data-stu-id="3fb75-148">This example lists the methods supported for the Databases node:</span></span>  
  
```powershell
Set-Location SQL:\MyComputer\DEFAULT\Databases  
Get-Item . | Get-Member -Type Methods  
```  
  
 <span data-ttu-id="3fb75-149">此範例列出已設為 SMO 資料表物件之變數的屬性：</span><span class="sxs-lookup"><span data-stu-id="3fb75-149">This example lists the properties for a variable that has been set to an SMO Table object:</span></span>  
  
```powershell
$MyVar = New-Object Microsoft.SqlServer.Management.SMO.Table  
$MyVar | Get-Member -Type Properties  
```  
  
## <a name="see-also"></a><span data-ttu-id="3fb75-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3fb75-150">See Also</span></span>  
 <span data-ttu-id="3fb75-151">[SQL Server PowerShell 提供者](../powershell/sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="3fb75-151">[SQL Server PowerShell Provider](../powershell/sql-server-powershell-provider.md) </span></span>  
 [<span data-ttu-id="3fb75-152">使用 Database Engine Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3fb75-152">Use the Database Engine cmdlets</span></span>](../../2014/database-engine/use-the-database-engine-cmdlets.md)  
