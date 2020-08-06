---
title: 建立和更新統計資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- statistical information [SMO]
ms.assetid: 47a0a172-a969-4deb-bca9-dd04401a0fe1
author: stevestein
ms.author: sstein
ms.openlocfilehash: 48c61bb1b213e4b57c7fbae0b0ec7294c9401a0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606180"
---
# <a name="creating-and-updating-statistics"></a><span data-ttu-id="3d6eb-102">建立和更新統計資料</span><span class="sxs-lookup"><span data-stu-id="3d6eb-102">Creating and Updating Statistics</span></span>
  <span data-ttu-id="3d6eb-103">在 SMO 中，有關在資料庫中處理查詢的統計資訊可以利用 <xref:Microsoft.SqlServer.Management.Smo.Statistic> 物件來收集。</span><span class="sxs-lookup"><span data-stu-id="3d6eb-103">In SMO, statistical information about processing queries in the database can be collected by using the <xref:Microsoft.SqlServer.Management.Smo.Statistic> object.</span></span>  
  
 <span data-ttu-id="3d6eb-104">您可以使用 <xref:Microsoft.SqlServer.Management.Smo.Statistic> 和 <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> 物件，為任何資料行建立統計資料。</span><span class="sxs-lookup"><span data-stu-id="3d6eb-104">It is possible to create statistics for any column by using the <xref:Microsoft.SqlServer.Management.Smo.Statistic> and <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> object.</span></span> <span data-ttu-id="3d6eb-105">您可以執行 <xref:Microsoft.SqlServer.Management.Smo.Statistic.Update%2A> 方法來更新 <xref:Microsoft.SqlServer.Management.Smo.Statistic> 物件中的統計資料。</span><span class="sxs-lookup"><span data-stu-id="3d6eb-105">The <xref:Microsoft.SqlServer.Management.Smo.Statistic.Update%2A> method can be run to update the statistics in the <xref:Microsoft.SqlServer.Management.Smo.Statistic> object.</span></span> <span data-ttu-id="3d6eb-106">結果則可在查詢最佳化工具中檢視。</span><span class="sxs-lookup"><span data-stu-id="3d6eb-106">The results can be viewed in the Query Optimizer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d6eb-107">範例</span><span class="sxs-lookup"><span data-stu-id="3d6eb-107">Example</span></span>  
 <span data-ttu-id="3d6eb-108">如果要使用所提供的任何程式碼範例，您必須選擇建立應用程式用的程式設計環境、程式設計範本，及程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="3d6eb-108">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="3d6eb-109">如需詳細資訊，請參閱[在 Visual Studio .net 中建立 VISUAL BASIC SMO 專案](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)或[在 Visual Studio .Net 中建立 VISUAL C&#35; SMO 專案](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="3d6eb-109">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-and-update-statistics-in-visual-basic"></a><span data-ttu-id="3d6eb-110">在 Visual Basic 中建立和更新統計資料</span><span class="sxs-lookup"><span data-stu-id="3d6eb-110">Creating and Update Statistics in Visual Basic</span></span>  
 <span data-ttu-id="3d6eb-111">此程式碼範例會在為其建立 <xref:Microsoft.SqlServer.Management.Smo.Statistic> 物件和 <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> 物件的現有資料庫上，建立新的資料表。</span><span class="sxs-lookup"><span data-stu-id="3d6eb-111">This code example creates a new table on an existing database for which the <xref:Microsoft.SqlServer.Management.Smo.Statistic> object and the <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> object are created.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBStatistics1](SMO How to#SMO_VBStatistics1)]  -->  
  
## <a name="creating-and-update-statistics-in-visual-c"></a><span data-ttu-id="3d6eb-112">在 Visual C# 中建立和更新統計資料</span><span class="sxs-lookup"><span data-stu-id="3d6eb-112">Creating and Update Statistics in Visual C#</span></span>  
 <span data-ttu-id="3d6eb-113">此程式碼範例會在為其建立 <xref:Microsoft.SqlServer.Management.Smo.Statistic> 物件和 <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> 物件的現有資料庫上，建立新的資料表。</span><span class="sxs-lookup"><span data-stu-id="3d6eb-113">This code example creates a new table on an existing database for which the <xref:Microsoft.SqlServer.Management.Smo.Statistic> object and the <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> object are created.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.  
            Server srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db = default(Database);  
            db = srv.Databases["AdventureWorks2012"];  
            //Reference the CreditCard table.   
  
           Table tb = db.Tables["CreditCard", "Sales"];  
            //Define a Statistic object by supplying the parent table and name   
            //arguments in the constructor.   
            Statistic stat = default(Statistic);  
            stat = new Statistic(tb, "Test_Statistics");  
            //Define a StatisticColumn object variable for the CardType column   
            //and add to the Statistic object variable.   
            StatisticColumn statcol = default(StatisticColumn);  
            statcol = new StatisticColumn(stat, "CardType");  
            stat.StatisticColumns.Add(statcol);  
            //Create the statistic counter on the instance of SQL Server.   
            stat.Create();  
        }  
```  
  
## <a name="creating-and-update-statistics-in-powershell"></a><span data-ttu-id="3d6eb-114">在 PowerShell 中建立和更新統計資料</span><span class="sxs-lookup"><span data-stu-id="3d6eb-114">Creating and Update Statistics in PowerShell</span></span>  
 <span data-ttu-id="3d6eb-115">此程式碼範例會在為其建立 <xref:Microsoft.SqlServer.Management.Smo.Statistic> 物件和 <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> 物件的現有資料庫上，建立新的資料表。</span><span class="sxs-lookup"><span data-stu-id="3d6eb-115">This code example creates a new table on an existing database for which the <xref:Microsoft.SqlServer.Management.Smo.Statistic> object and the <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> object are created.</span></span>  
  
```powershell
# Example of implementing a full text search on the default instance.  
# Set the path context to the local, default instance of SQL Server and database tables  
  
CD \sql\localhost\default\databases  
$db = get-item AdventureWorks2012  
  
CD AdventureWorks2012\tables  
  
#Get a reference to the table  
$tb = get-item Production.ProductCategory  
  
# Define a FullTextCatalog object variable by specifying the parent database and name arguments in the constructor.  
  
$ftc = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextCatalog -argumentlist $db, "Test_Catalog2"  
$ftc.IsDefault = $true  
  
# Create the Full Text Search catalog on the instance of SQL Server.  
$ftc.Create()  
  
# Define a FullTextIndex object variable by supplying the parent table argument in the constructor.  
$fti = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextIndex -argumentlist $tb  
  
#  Define a FullTextIndexColumn object variable by supplying the parent index   
#  and column name arguments in the constructor.  
  
$ftic = New-Object -TypeName Microsoft.SqlServer.Management.SMO.FullTextIndexColumn -argumentlist $fti, "Name"  
  
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
