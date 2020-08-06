---
title: 使用 SQL Server PowerShell 路徑 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: f31d8e2c-8d59-4fee-ac2a-324668e54262
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6d2647251eb1c8843d4ab7a95d2c439e47f5bb6a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699847"
---
# <a name="work-with-sql-server-powershell-paths"></a><span data-ttu-id="2d3ad-102">使用 SQL Server PowerShell 路徑</span><span class="sxs-lookup"><span data-stu-id="2d3ad-102">Work With SQL Server PowerShell Paths</span></span>
  <span data-ttu-id="2d3ad-103">當您導覽至 [!INCLUDE[ssDE](../includes/ssde-md.md)] 提供者路徑中的節點之後，即可使用與該節點相關聯之 [!INCLUDE[ssDE](../includes/ssde-md.md)] 管理物件的方法與屬性，進行工作或取得資訊。</span><span class="sxs-lookup"><span data-stu-id="2d3ad-103">After you have navigated to a node in a [!INCLUDE[ssDE](../includes/ssde-md.md)] provider path, you can perform work or retrieve information by using the methods and properties from the [!INCLUDE[ssDE](../includes/ssde-md.md)] management object associated with the node.</span></span>  
  
1.  [<span data-ttu-id="2d3ad-104">開始之前</span><span class="sxs-lookup"><span data-stu-id="2d3ad-104">Before You Begin</span></span>](#BeforeYouBegin)  
  
2.  <span data-ttu-id="2d3ad-105">**To work on a path node:**  [Listing Methods and Properties](#ListPropMeth), [Using Methods and Properties](#UsePropMeth)</span><span class="sxs-lookup"><span data-stu-id="2d3ad-105">**To work on a path node:**  [Listing Methods and Properties](#ListPropMeth), [Using Methods and Properties](#UsePropMeth)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2d3ad-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="2d3ad-106">Before You Begin</span></span>  
 <span data-ttu-id="2d3ad-107">當您導覽至 [!INCLUDE[ssDE](../includes/ssde-md.md)] 提供者路徑中的節點之後，可以執行兩種動作：</span><span class="sxs-lookup"><span data-stu-id="2d3ad-107">After you have navigated to a node in a [!INCLUDE[ssDE](../includes/ssde-md.md)] provider path, you can perform two types of actions:</span></span>  
  
-   <span data-ttu-id="2d3ad-108">您可以執行在節點上運作的 Windows PowerShell Cmdlet，例如 **Rename-Item**。</span><span class="sxs-lookup"><span data-stu-id="2d3ad-108">You can run Windows PowerShell cmdlets that operate on nodes, such as **Rename-Item**.</span></span>  
  
-   <span data-ttu-id="2d3ad-109">您可以從相關聯的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 管理物件模型 (如 SMO) 呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="2d3ad-109">You can call the methods from the associated [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] management object model, such as SMO.</span></span> <span data-ttu-id="2d3ad-110">例如，如果您導覽至路徑中的資料庫節點，您可以使用 <xref:Microsoft.SqlServer.Management.Smo.Database> 類別的方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="2d3ad-110">For example, if you navigate to the Databases node in a path, you can use the methods and properties of the <xref:Microsoft.SqlServer.Management.Smo.Database> class.</span></span>  
  
 <span data-ttu-id="2d3ad-111">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 提供者是用來管理 [!INCLUDE[ssDE](../includes/ssde-md.md)]執行個體中的物件，</span><span class="sxs-lookup"><span data-stu-id="2d3ad-111">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider is used to manage the objects in an instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="2d3ad-112">而不是用來處理資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="2d3ad-112">It is not used to work with the data in databases.</span></span> <span data-ttu-id="2d3ad-113">如果您導覽至資料表或檢視表，即無法使用此提供者選取、插入、更新或刪除資料。</span><span class="sxs-lookup"><span data-stu-id="2d3ad-113">If you have navigated to a table or view, you cannot use the provider to select, insert, update, or delete data.</span></span> <span data-ttu-id="2d3ad-114">使用 **Invoke-Sqlcmd** Cmdlet 可從 Windows PowerShell 環境中，查詢或變更資料表與檢視中的資料。</span><span class="sxs-lookup"><span data-stu-id="2d3ad-114">Use the **Invoke-Sqlcmd** cmdlet to query or change data in tables and views from the Windows PowerShell environment.</span></span> <span data-ttu-id="2d3ad-115">如需詳細資訊，請參閱 [Invoke-Sqlcmd Cmdlet](../database-engine/invoke-sqlcmd-cmdlet.md)。</span><span class="sxs-lookup"><span data-stu-id="2d3ad-115">For more information, see [Invoke-Sqlcmd cmdlet](../database-engine/invoke-sqlcmd-cmdlet.md).</span></span>  
  
##  <a name="listing-methods-and-properties"></a><a name="ListPropMeth"></a> <span data-ttu-id="2d3ad-116">列出方法與屬性</span><span class="sxs-lookup"><span data-stu-id="2d3ad-116">Listing Methods and Properties</span></span>
  
 <span data-ttu-id="2d3ad-117">請使用 **Get-Member** Cmdlet，以檢視特定物件或物件類別適用的方法或屬性。</span><span class="sxs-lookup"><span data-stu-id="2d3ad-117">To view the methods and properties available for specific objects or object classes, use the **Get-Member** cmdlet.</span></span>  
  
### <a name="examples-listing-methods-and-properties"></a><span data-ttu-id="2d3ad-118">範例：列出方法與屬性</span><span class="sxs-lookup"><span data-stu-id="2d3ad-118">Examples: Listing Methods and Properties</span></span>  
 <span data-ttu-id="2d3ad-119">此範例將 Windows PowerShell 變數設定為 SMO <xref:Microsoft.SqlServer.Management.Smo.Database> 類別，並列出方法和屬性：</span><span class="sxs-lookup"><span data-stu-id="2d3ad-119">This example sets a Windows PowerShell variable to the SMO <xref:Microsoft.SqlServer.Management.Smo.Database> class and lists the methods and properties:</span></span>  
  
```powershell
$MyDBVar = New-Object Microsoft.SqlServer.Management.SMO.Database  
$MyDBVar | Get-Member -Type Methods  
$MyDBVar | Get-Member -Type Properties  
```  
  
 <span data-ttu-id="2d3ad-120">您也可以使用 **Get-Member** 列出與 Windows PowerShell 路徑之結束節點相關聯的方法與屬性。</span><span class="sxs-lookup"><span data-stu-id="2d3ad-120">You can also use **Get-Member** to list the methods and properties that are associated with the end node of a Windows PowerShell path.</span></span>  
  
 <span data-ttu-id="2d3ad-121">此範例會導覽至 SQLSERVER: 路徑中的 Databases 節點，並列出集合屬性：</span><span class="sxs-lookup"><span data-stu-id="2d3ad-121">This example navigates to the Databases node in a SQLSERVER: path and lists the collection properties:</span></span>  
  
```powershell
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases  
Get-Item . | Get-Member -Type Properties  
```  
  
 <span data-ttu-id="2d3ad-122">此範例會導覽至 SQLSERVER: 路徑中的 AdventureWorks2012 節點，並列出物件屬性：</span><span class="sxs-lookup"><span data-stu-id="2d3ad-122">This example navigates to the AdventureWorks2012 node in a SQLSERVER: path and lists the object properties:</span></span>  
  
```powershell
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases\AdventureWorks2012  
Get-Item . | Get-Member -Type Properties  
```  
  
##  <a name="using-smo-methods-and-properties"></a><a name="UsePropMeth"></a><span data-ttu-id="2d3ad-123">使用 SMO 方法和屬性</span><span class="sxs-lookup"><span data-stu-id="2d3ad-123">Using SMO Methods and Properties</span></span>  
  
 <span data-ttu-id="2d3ad-124">若要從 [!INCLUDE[ssDE](../includes/ssde-md.md)] 提供者路徑對物件進行工作，可以使用 SMO 方法與屬性。</span><span class="sxs-lookup"><span data-stu-id="2d3ad-124">To perform work on objects from a [!INCLUDE[ssDE](../includes/ssde-md.md)] provider path, you can use SMO methods and properties.</span></span>  
  
### <a name="examples-using-methods-and-properties"></a><span data-ttu-id="2d3ad-125">範例：使用方法與屬性</span><span class="sxs-lookup"><span data-stu-id="2d3ad-125">Examples: Using Methods and Properties</span></span>  
 <span data-ttu-id="2d3ad-126">此範例會使用 SMO [結構描述]\*\*\*\* 屬性來取得 AdventureWorks2012中 Sales 結構描述內的資料表清單：</span><span class="sxs-lookup"><span data-stu-id="2d3ad-126">This example uses the SMO **Schema** property to get a list of the tables from the Sales schema in AdventureWorks2012:</span></span>  
  
```powershell
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases\AdventureWorks2012\Tables  
Get-ChildItem | Where {$_.Schema -eq "Sales"}  
```  
  
 <span data-ttu-id="2d3ad-127">這個範例會使用 SMO**腳本**方法來產生腳本，其中包含 `CREATE VIEW` 您必須在 AdventureWorks2012 中重新建立視圖的語句：</span><span class="sxs-lookup"><span data-stu-id="2d3ad-127">This example uses the SMO **Script** method to generate a script that contains the `CREATE VIEW` statements you must have to re-create the views in AdventureWorks2012:</span></span>  
  
```powershell
Remove-Item C:\PowerShell\CreateViews.sql  
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases\AdventureWorks2012\Views  
foreach ($Item in Get-ChildItem) { $Item.Script() | Out-File -Filepath C:\PowerShell\CreateViews.sql -append }  
```  
  
 <span data-ttu-id="2d3ad-128">此範例使用 SMO **Create** 方法建立資料庫，然後使用 **State** 屬性顯示此資料庫是否存在：</span><span class="sxs-lookup"><span data-stu-id="2d3ad-128">This example uses the SMO **Create** method to create a database, and then uses the **State** property to show whether the database exists:</span></span>  
  
```powershell
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases  
$MyDBVar = New-Object Microsoft.SqlServer.Management.SMO.Database  
$MyDBVar.Parent = (Get-Item ..)  
$MyDBVar.Name = "NewDB"  
$MyDBVar.Create()  
$MyDBVar.State  
```  
  
## <a name="see-also"></a><span data-ttu-id="2d3ad-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d3ad-129">See Also</span></span>  
 <span data-ttu-id="2d3ad-130">[SQL Server PowerShell 提供者](sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="2d3ad-130">[SQL Server PowerShell Provider](sql-server-powershell-provider.md) </span></span>  
 <span data-ttu-id="2d3ad-131">[流覽 SQL Server PowerShell 路徑](navigate-sql-server-powershell-paths.md) </span><span class="sxs-lookup"><span data-stu-id="2d3ad-131">[Navigate SQL Server PowerShell Paths](navigate-sql-server-powershell-paths.md) </span></span>  
 <span data-ttu-id="2d3ad-132">[將 Urn 轉換為 SQL Server 提供者路徑](../database-engine/convert-urns-to-sql-server-provider-paths.md) </span><span class="sxs-lookup"><span data-stu-id="2d3ad-132">[Convert URNs to SQL Server Provider Paths](../database-engine/convert-urns-to-sql-server-provider-paths.md) </span></span>  
 [<span data-ttu-id="2d3ad-133">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="2d3ad-133">SQL Server PowerShell</span></span>](sql-server-powershell.md)  
  
  
