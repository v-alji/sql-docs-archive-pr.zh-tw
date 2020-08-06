---
title: 執行全文檢索搜尋 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- full-text search [SMO]
ms.assetid: 9ce9ad9c-f671-4760-90b5-e0c8ca051473
author: stevestein
ms.author: sstein
ms.openlocfilehash: f8b797e2a38c9136c34b7058b539fca522e03229
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686885"
---
# <a name="implementing-full-text-search"></a><span data-ttu-id="fc53e-102">實作全文檢索搜尋</span><span class="sxs-lookup"><span data-stu-id="fc53e-102">Implementing Full-Text Search</span></span>
  <span data-ttu-id="fc53e-103">全文檢索搜尋可用於 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的每個執行個體，在 SMO 中是由 <xref:Microsoft.SqlServer.Management.Smo.Server.FullTextService%2A> 物件表示。</span><span class="sxs-lookup"><span data-stu-id="fc53e-103">Full-text search is available per instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and is represented in SMO by the <xref:Microsoft.SqlServer.Management.Smo.Server.FullTextService%2A> object.</span></span> <span data-ttu-id="fc53e-104"><xref:Microsoft.SqlServer.Management.Smo.FullTextService> 物件位於 `Server` 物件之下，</span><span class="sxs-lookup"><span data-stu-id="fc53e-104">The <xref:Microsoft.SqlServer.Management.Smo.FullTextService> object resides under the `Server` object.</span></span> <span data-ttu-id="fc53e-105">可用於管理 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 全文檢索搜尋服務的組態選項。</span><span class="sxs-lookup"><span data-stu-id="fc53e-105">It is used to manage the configuration options for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Full Text Search service.</span></span> <span data-ttu-id="fc53e-106"><xref:Microsoft.SqlServer.Management.Smo.FullTextCatalogCollection> 物件屬於 <xref:Microsoft.SqlServer.Management.Smo.Database> 物件，且為 <xref:Microsoft.SqlServer.Management.Smo.FullTextCatalog> 物件的集合 (這些物件表示針對資料庫所定義的全文檢索目錄)。</span><span class="sxs-lookup"><span data-stu-id="fc53e-106">The <xref:Microsoft.SqlServer.Management.Smo.FullTextCatalogCollection> object belongs to the <xref:Microsoft.SqlServer.Management.Smo.Database> object and it is a collection of <xref:Microsoft.SqlServer.Management.Smo.FullTextCatalog> objects that represent full-text catalogs defined for the database.</span></span> <span data-ttu-id="fc53e-107">與一般索引不同的是，您只能為每個資料表定義一個全文檢索索引，</span><span class="sxs-lookup"><span data-stu-id="fc53e-107">You can only have one full-text index defined for each table, unlike normal indexes.</span></span> <span data-ttu-id="fc53e-108">這是由 <xref:Microsoft.SqlServer.Management.Smo.FullTextIndexColumn> 物件中的 <xref:Microsoft.SqlServer.Management.Smo.Table> 物件表示。</span><span class="sxs-lookup"><span data-stu-id="fc53e-108">This is represented by a <xref:Microsoft.SqlServer.Management.Smo.FullTextIndexColumn> object in the <xref:Microsoft.SqlServer.Management.Smo.Table> object.</span></span>  
  
 <span data-ttu-id="fc53e-109">若要建立全文檢索搜尋服務，您必須在資料庫上定義全文檢索目錄，並在資料庫的其中一個資料表上定義全文檢索搜尋索引。</span><span class="sxs-lookup"><span data-stu-id="fc53e-109">To create a full-text search service, you must have a full-text catalog defined on the database and a full-text search index defined on one of the tables in the database.</span></span>  
  
 <span data-ttu-id="fc53e-110">首先，請呼叫 <xref:Microsoft.SqlServer.Management.Smo.FullTextCatalog> 建構函式並指定目錄名稱，以在資料庫上建立全文檢索目錄。</span><span class="sxs-lookup"><span data-stu-id="fc53e-110">First, create a full-text catalog on the database by calling the <xref:Microsoft.SqlServer.Management.Smo.FullTextCatalog> constructor and specifying the catalog name.</span></span> <span data-ttu-id="fc53e-111">接著再呼叫建構函式，並指定要在其上建立全文檢索索引的資料表，以建立全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="fc53e-111">Then, create the full-text index by calling the constructor and specifying the table on which it is to be created.</span></span> <span data-ttu-id="fc53e-112">接下來可以使用 <xref:Microsoft.SqlServer.Management.Smo.FullTextIndexColumn> 物件並且提供資料表內資料行的名稱，以加入全文檢索索引的索引資料行。</span><span class="sxs-lookup"><span data-stu-id="fc53e-112">You can then add index columns for the full-text index, by using the <xref:Microsoft.SqlServer.Management.Smo.FullTextIndexColumn> object and providing the name of the column within the table.</span></span> <span data-ttu-id="fc53e-113">然後再將 <xref:Microsoft.SqlServer.Management.Smo.FullTextIndex.CatalogName%2A> 屬性設定為已建立的目錄。</span><span class="sxs-lookup"><span data-stu-id="fc53e-113">Then, set the <xref:Microsoft.SqlServer.Management.Smo.FullTextIndex.CatalogName%2A> property to the catalog you have created.</span></span> <span data-ttu-id="fc53e-114">最後呼叫 <xref:Microsoft.SqlServer.Management.Smo.FullTextIndex.Create%2A> 方法，並在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體上建立全文檢索索引。</span><span class="sxs-lookup"><span data-stu-id="fc53e-114">Finally, call the <xref:Microsoft.SqlServer.Management.Smo.FullTextIndex.Create%2A> method and create the full-text index on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc53e-115">範例</span><span class="sxs-lookup"><span data-stu-id="fc53e-115">Example</span></span>  
 <span data-ttu-id="fc53e-116">如果要使用所提供的任何程式碼範例，您必須選擇建立應用程式用的程式設計環境、程式設計範本，及程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="fc53e-116">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="fc53e-117">如需詳細資訊，請參閱[在 Visual Studio .net 中建立 VISUAL BASIC SMO 專案](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)或[在 Visual Studio .Net 中建立 VISUAL C&#35; SMO 專案](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="fc53e-117">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-a-full-text-search-service-in-visual-basic"></a><span data-ttu-id="fc53e-118">在 Visual Basic 中建立全文檢索搜尋服務</span><span class="sxs-lookup"><span data-stu-id="fc53e-118">Creating a Full-Text Search Service in Visual Basic</span></span>  
 <span data-ttu-id="fc53e-119">此程式碼範例會針對 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 範例資料庫中的 `ProductCategory` 資料表建立全文檢索搜尋目錄。</span><span class="sxs-lookup"><span data-stu-id="fc53e-119">This code example creates a full-text search catalog for the `ProductCategory` table in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database.</span></span> <span data-ttu-id="fc53e-120">然後在 `ProductCategory` 資料表的 Name 資料行上建立全文檢索搜尋索引。</span><span class="sxs-lookup"><span data-stu-id="fc53e-120">It then creates a full-text search index on the Name column in the `ProductCategory` table.</span></span> <span data-ttu-id="fc53e-121">全文檢索搜尋索引需要資料行上已定義了唯一索引。</span><span class="sxs-lookup"><span data-stu-id="fc53e-121">The full-text search index requires that there is a unique index already defined on the column.</span></span>  
  
```vb
' compile with:   
' /r:Microsoft.SqlServer.SqlEnum.dll   
' /r:Microsoft.SqlServer.Smo.dll   
' /r:Microsoft.SqlServer.ConnectionInfo.dll   
' /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll  
  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Sdk.Sfc  
Imports Microsoft.SqlServer.Management.Common  
  
Public Class A  
   Public Shared Sub Main()  
      ' Connect to the local, default instance of SQL Server.  
      Dim srv As Server = Nothing  
      srv = New Server()  
  
      ' Reference the AdventureWorks database.  
      Dim db As Database = Nothing  
      db = srv.Databases("AdventureWorks")  
  
      ' Reference the ProductCategory table.  
      Dim tb As Table = Nothing  
      tb = db.Tables("ProductCategory", "Production")  
  
      ' Define a FullTextCatalog object variable by specifying the parent database and name arguments in the constructor.  
      Dim ftc As FullTextCatalog = Nothing  
      ftc = New FullTextCatalog(db, "Test_Catalog")  
      ftc.IsDefault = True  
  
      ' Create the Full-Text Search catalog on the instance of SQL Server.  
      ftc.Create()  
  
      ' Define a FullTextIndex object varaible by supplying the parent table argument in the constructor.  
      Dim fti As FullTextIndex = Nothing  
      fti = New FullTextIndex(tb)  
  
      ' Define a FullTextIndexColumn object variable by supplying the parent index and column name arguments in the constructor.  
      Dim ftic As FullTextIndexColumn = Nothing  
      ftic = New FullTextIndexColumn(fti, "Name")  
  
      ' Add the indexed column to the index.  
      fti.IndexedColumns.Add(ftic)  
      fti.ChangeTracking = ChangeTracking.Automatic  
  
      ' Specify the unique index on the table that is required by the Full Text Search index.  
      fti.UniqueIndexName = "AK_ProductCategory_Name"  
  
      ' Specify the catalog associated with the index.  
      fti.CatalogName = "Test_Catalog"  
  
      ' Create the Full Text Search index on the instance of SQL Server.  
      fti.Create()  
   End Sub  
End Class  
```  
  
## <a name="creating-a-full-text-search-service-in-visual-c"></a><span data-ttu-id="fc53e-122">在 Visual C# 中建立全文檢索搜尋服務</span><span class="sxs-lookup"><span data-stu-id="fc53e-122">Creating a Full-Text Search Service in Visual C#</span></span>  
 <span data-ttu-id="fc53e-123">此程式碼範例會針對 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 範例資料庫中的 `ProductCategory` 資料表建立全文檢索搜尋目錄。</span><span class="sxs-lookup"><span data-stu-id="fc53e-123">This code example creates a full-text search catalog for the `ProductCategory` table in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database.</span></span> <span data-ttu-id="fc53e-124">然後在 `ProductCategory` 資料表的 Name 資料行上建立全文檢索搜尋索引。</span><span class="sxs-lookup"><span data-stu-id="fc53e-124">It then creates a full-text search index on the Name column in the `ProductCategory` table.</span></span> <span data-ttu-id="fc53e-125">全文檢索搜尋索引需要資料行上已定義了唯一索引。</span><span class="sxs-lookup"><span data-stu-id="fc53e-125">The full-text search index requires that there is a unique index already defined on the column.</span></span>  
  
```csharp
// compile with:   
// /r:Microsoft.SqlServer.SqlEnum.dll   
// /r:Microsoft.SqlServer.Smo.dll   
// /r:Microsoft.SqlServer.ConnectionInfo.dll   
// /r:Microsoft.SqlServer.Management.Sdk.Sfc.dll   
  
using Microsoft.SqlServer.Management.Smo;  
using Microsoft.SqlServer.Management.Sdk.Sfc;  
using Microsoft.SqlServer.Management.Common;  
  
public class A {  
   public static void Main() {  
      // Connect to the local, default instance of SQL Server.  
      Server srv = default(Server);  
      srv = new Server();  
  
      // Reference the AdventureWorks database.  
      Database db = default(Database);  
      db = srv.Databases ["AdventureWorks"];  
  
      // Reference the ProductCategory table.  
      Table tb = default(Table);  
      tb = db.Tables["ProductCategory", "Production"];  
  
      // Define a FullTextCatalog object variable by specifying the parent database and name arguments in the constructor.  
      FullTextCatalog ftc = default(FullTextCatalog);  
      ftc = new FullTextCatalog(db, "Test_Catalog");  
      ftc.IsDefault = true;  
  
      // Create the Full-Text Search catalog on the instance of SQL Server.  
      ftc.Create();  
  
      // Define a FullTextIndex object varaible by supplying the parent table argument in the constructor.  
      FullTextIndex fti = default(FullTextIndex);  
      fti = new FullTextIndex(tb);  
  
      // Define a FullTextIndexColumn object variable by supplying the parent index and column name arguments in the constructor.  
      FullTextIndexColumn ftic = default(FullTextIndexColumn);  
      ftic = new FullTextIndexColumn(fti, "Name");  
  
      // Add the indexed column to the index.  
      fti.IndexedColumns.Add(ftic);  
      fti.ChangeTracking = ChangeTracking.Automatic;  
  
      // Specify the unique index on the table that is required by the Full Text Search index.  
      fti.UniqueIndexName = "AK_ProductCategory_Name";  
  
      // Specify the catalog associated with the index.  
      fti.CatalogName = "Test_Catalog";  
  
      // Create the Full Text Search index on the instance of SQL Server.  
      fti.Create();  
   }  
}  
```  
  
## <a name="creating-a-full-text-search-service-in-powershell"></a><span data-ttu-id="fc53e-126">在 PowerShell 中建立全文檢索搜尋服務</span><span class="sxs-lookup"><span data-stu-id="fc53e-126">Creating a Full-Text Search Service in PowerShell</span></span>  
 <span data-ttu-id="fc53e-127">此程式碼範例會針對 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 範例資料庫中的 `ProductCategory` 資料表建立全文檢索搜尋目錄。</span><span class="sxs-lookup"><span data-stu-id="fc53e-127">This code example creates a full-text search catalog for the `ProductCategory` table in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database.</span></span> <span data-ttu-id="fc53e-128">然後在 `ProductCategory` 資料表的 Name 資料行上建立全文檢索搜尋索引。</span><span class="sxs-lookup"><span data-stu-id="fc53e-128">It then creates a full-text search index on the Name column in the `ProductCategory` table.</span></span> <span data-ttu-id="fc53e-129">全文檢索搜尋索引需要資料行上已定義了唯一索引。</span><span class="sxs-lookup"><span data-stu-id="fc53e-129">The full-text search index requires that there is a unique index already defined on the column.</span></span>  
  
```powershell
# Example of implementing a full text search on the default instance.  
# Set the path context to the local, default instance of SQL Server and database tables  
  
CD \sql\localhost\default\databases  
$db = Get-Item AdventureWorks2012  
  
CD AdventureWorks\tables  
  
#Get a reference to the table  
$tb = Get-Item Production.ProductCategory  
  
# Define a FullTextCatalog object variable by specifying the parent database and name arguments in the constructor.  
  
$ftc = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextCatalog -ArgumentList $db, "Test_Catalog2"  
$ftc.IsDefault = $true  
  
# Create the Full Text Search catalog on the instance of SQL Server.  
$ftc.Create()  
  
# Define a FullTextIndex object variable by supplying the parent table argument in the constructor.  
$fti = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextIndex -ArgumentList $tb  
  
#  Define a FullTextIndexColumn object variable by supplying the parent index
#  and column name arguments in the constructor.  
  
$ftic = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextIndexColumn -ArgumentList $fti, "Name"  
  
# Add the indexed column to the index.  
$fti.IndexedColumns.Add($ftic)  
  
# Set change tracking  
$fti.ChangeTracking = [Microsoft.SqlServer.Management.SMO.ChangeTracking]::Automatic  
  
# Specify the unique index on the table that is required by the Full Text Search index.  
$fti.UniqueIndexName = "AK_ProductCategory_Name"  
  
# Specify the catalog associated with the index.  
$fti.CatalogName = "Test_Catalog2"  
  
# Create the Full Text Search Index  
$fti.Create()  
```  
