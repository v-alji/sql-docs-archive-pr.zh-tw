---
title: 使用資料表和索引資料分割 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- partitions [SMO]
- storing data [SMO]
- partitioned tables [SQL Server], SMO
- partitioned indexes [SQL Server], SMO
ms.assetid: 0e682d7e-86c3-4d73-950d-aa692d46cb62
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8e05087f63da163b8fa339befae039eb5e7e8245
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593333"
---
# <a name="using-table-and-index-partitioning"></a><span data-ttu-id="b4935-102">使用資料表和索引資料分割</span><span class="sxs-lookup"><span data-stu-id="b4935-102">Using Table and Index Partitioning</span></span>
  <span data-ttu-id="b4935-103">資料可以使用 [Partitioned Tables and Indexes](../../partitions/partitioned-tables-and-indexes.md)提供的儲存演算法來儲存。</span><span class="sxs-lookup"><span data-stu-id="b4935-103">Data can be stored by using the storage algorithms provided by [Partitioned Tables and Indexes](../../partitions/partitioned-tables-and-indexes.md).</span></span> <span data-ttu-id="b4935-104">分割作業可讓大型資料表和索引更容易管理及擴充。</span><span class="sxs-lookup"><span data-stu-id="b4935-104">Partitioning can make large tables and indexes more manageable and scalable.</span></span>  
  
## <a name="index-and-table-partitioning"></a><span data-ttu-id="b4935-105">索引和資料表資料分割</span><span class="sxs-lookup"><span data-stu-id="b4935-105">Index and Table Partitioning</span></span>  
 <span data-ttu-id="b4935-106">此功能可以讓索引和資料表資料散佈到資料分割中的多個檔案群組。</span><span class="sxs-lookup"><span data-stu-id="b4935-106">The feature enables index and table data to be spread across multiple file groups in partitions.</span></span> <span data-ttu-id="b4935-107">資料分割函數會定義資料表的資料列或索引如何依據某些資料行 (稱為分割資料行) 的值對應到資料分割集。</span><span class="sxs-lookup"><span data-stu-id="b4935-107">A partition function defines how the rows of a table or index are mapped to a set of partitions based on the values of certain columns, referred to as partitioning columns.</span></span> <span data-ttu-id="b4935-108">資料分割配置則會將資料分割函數所指定的每個資料分割都對應到檔案群組。</span><span class="sxs-lookup"><span data-stu-id="b4935-108">A partition scheme maps each partition specified by the partition function to a file group.</span></span> <span data-ttu-id="b4935-109">如此您就可以開發出封存策略，讓資料表可以擴充到檔案群組，並進而擴充到實體裝置。</span><span class="sxs-lookup"><span data-stu-id="b4935-109">This lets you develop archiving strategies that enable tables to be scaled across file groups, and therefore physical devices.</span></span>  
  
 <span data-ttu-id="b4935-110"><xref:Microsoft.SqlServer.Management.Smo.Database> 物件包含表示所實作之資料分割函數的 <xref:Microsoft.SqlServer.Management.Smo.PartitionFunction> 物件集合，以及描述資料如何對應到檔案群組的 <xref:Microsoft.SqlServer.Management.Smo.PartitionScheme> 物件集合。</span><span class="sxs-lookup"><span data-stu-id="b4935-110">The <xref:Microsoft.SqlServer.Management.Smo.Database> object contains a collection of <xref:Microsoft.SqlServer.Management.Smo.PartitionFunction> objects that represent the implemented partition functions and a collection of <xref:Microsoft.SqlServer.Management.Smo.PartitionScheme> objects that describe how data is mapped to file groups.</span></span>  
  
 <span data-ttu-id="b4935-111">每個 <xref:Microsoft.SqlServer.Management.Smo.Table> 和 <xref:Microsoft.SqlServer.Management.Smo.Index> 物件都會在 <xref:Microsoft.SqlServer.Management.Smo.PartitionScheme> 屬性中指定所使用的資料分割配置，並在 <xref:Microsoft.SqlServer.Management.Smo.PartitionSchemeParameterCollection> 中指定資料行。</span><span class="sxs-lookup"><span data-stu-id="b4935-111">Each <xref:Microsoft.SqlServer.Management.Smo.Table> and <xref:Microsoft.SqlServer.Management.Smo.Index> object specifies which partition scheme it uses in the <xref:Microsoft.SqlServer.Management.Smo.PartitionScheme> property and specifies the columns in the <xref:Microsoft.SqlServer.Management.Smo.PartitionSchemeParameterCollection>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4935-112">範例</span><span class="sxs-lookup"><span data-stu-id="b4935-112">Example</span></span>  
 <span data-ttu-id="b4935-113">在下列的程式碼範例中，您必須選取用於建立應用程式的程式設計環境、程式設計範本和程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="b4935-113">For the following code example, you will have to select the programming environment, programming template and the programming language to create your application.</span></span> <span data-ttu-id="b4935-114">如需詳細資訊，請參閱[在 Visual Studio .net 中建立 VISUAL BASIC SMO 專案](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)和[在 Visual Studio .Net 中建立 VISUAL C&#35; SMO 專案](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="b4935-114">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) and [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="setting-up-a-partition-scheme-for-a-table-in-visual-basic"></a><span data-ttu-id="b4935-115">在 Visual Basic 中為資料表設定資料分割配置</span><span class="sxs-lookup"><span data-stu-id="b4935-115">Setting Up a Partition Scheme for a Table in Visual Basic</span></span>  
 <span data-ttu-id="b4935-116">此程式碼範例顯示如何為 `TransactionHistory` 範例資料庫中的 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 資料表建立資料分割函數和資料分割配置。</span><span class="sxs-lookup"><span data-stu-id="b4935-116">The code example shows how to create a partition function and a partition scheme for the `TransactionHistory` table in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database.</span></span> <span data-ttu-id="b4935-117">這些資料分割會以日期區分，用意在於將舊記錄區隔到 `TransactionHistoryArchive` 資料表中。</span><span class="sxs-lookup"><span data-stu-id="b4935-117">The partitions are divided by date with the intention of separating out old records into the `TransactionHistoryArchive` table.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBPartition1](SMO How to#SMO_VBPartition1)]  -->  
  
## <a name="setting-up-a-partition-scheme-for-a-table-in-visual-c"></a><span data-ttu-id="b4935-118">在 Visual C# 中為資料表設定資料分割配置</span><span class="sxs-lookup"><span data-stu-id="b4935-118">Setting Up a Partition Scheme for a Table in Visual C#</span></span>  
 <span data-ttu-id="b4935-119">此程式碼範例顯示如何為 `TransactionHistory` 範例資料庫中的 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 資料表建立資料分割函數和資料分割配置。</span><span class="sxs-lookup"><span data-stu-id="b4935-119">The code example shows how to create a partition function and a partition scheme for the `TransactionHistory` table in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database.</span></span> <span data-ttu-id="b4935-120">這些資料分割會以日期區分，用意在於將舊記錄區隔到 `TransactionHistoryArchive` 資料表中。</span><span class="sxs-lookup"><span data-stu-id="b4935-120">The partitions are divided by date with the intention of separating out old records into the `TransactionHistoryArchive` table.</span></span>  
  
```csharp
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Reference the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
//Define and create three new file groups on the database.   
FileGroup fg2;   
fg2 = new FileGroup(db, "Second");   
fg2.Create();   
FileGroup fg3;   
fg3 = new FileGroup(db, "Third");   
fg3.Create();   
FileGroup fg4;   
fg4 = new FileGroup(db, "Fourth");   
fg4.Create();   
//Define a partition function by supplying the parent database and name arguments in the constructor.   
PartitionFunction pf;   
pf = new PartitionFunction(db, "TransHistPF");   
//Add a partition function parameter that specifies the function uses a DateTime range type.   
PartitionFunctionParameter pfp;   
pfp = new PartitionFunctionParameter(pf, DataType.DateTime);   
pf.PartitionFunctionParameters.Add(pfp);   
//Specify the three dates that divide the data into four partitions.   
object[] val;   
val = new object[] {"1/1/2003", "1/1/2004", "1/1/2005"};   
pf.RangeValues = val;   
//Create the partition function.   
pf.Create();   
//Define a partition scheme by supplying the parent database and name arguments in the constructor.   
PartitionScheme ps;   
ps = new PartitionScheme(db, "TransHistPS");   
//Specify the partition function and the filegroups required by the partition scheme.   
ps.PartitionFunction = "TransHistPF";   
ps.FileGroups.Add("PRIMARY");   
ps.FileGroups.Add("second");   
ps.FileGroups.Add("Third");   
ps.FileGroups.Add("Fourth");   
//Create the partition scheme.   
ps.Create();   
}   
```  
  
## <a name="setting-up-a-partition-scheme-for-a-table-in-powershell"></a><span data-ttu-id="b4935-121">在 PowerShell 中為資料表設定資料分割配置</span><span class="sxs-lookup"><span data-stu-id="b4935-121">Setting Up a Partition Scheme for a Table in PowerShell</span></span>  
 <span data-ttu-id="b4935-122">此程式碼範例顯示如何為 `TransactionHistory` 範例資料庫中的 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 資料表建立資料分割函數和資料分割配置。</span><span class="sxs-lookup"><span data-stu-id="b4935-122">The code example shows how to create a partition function and a partition scheme for the `TransactionHistory` table in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sample database.</span></span> <span data-ttu-id="b4935-123">這些資料分割會以日期區分，用意在於將舊記錄區隔到 `TransactionHistoryArchive` 資料表中。</span><span class="sxs-lookup"><span data-stu-id="b4935-123">The partitions are divided by date with the intention of separating out old records into the `TransactionHistoryArchive` table.</span></span>  
  
```powershell  
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\default  
  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
$db = $srv.Databases["AdventureWorks"]  
#Create four filegroups  
$fg1 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Filegroup -argumentlist $db, "First"  
$fg2 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Filegroup -argumentlist $db, "Second"  
$fg3 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Filegroup -argumentlist $db, "Third"  
$fg4 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Filegroup -argumentlist $db, "Fourth"  
  
#Define a partition function by supplying the parent database and name arguments in the constructor.  
$pf =  New-Object -TypeName Microsoft.SqlServer.Management.SMO.PartitionFunction -argumentlist $db, "TransHistPF"  
$T = [Microsoft.SqlServer.Management.SMO.DataType]::DateTime  
$T  
$T.GetType()  
#Add a partition function parameter that specifies the function uses a DateTime range type.  
$pfp =  New-Object -TypeName Microsoft.SqlServer.Management.SMO.PartitionFunctionParameter -argumentlist $pf, $T  
  
#Specify the three dates that divide the data into four partitions.
#Create an array of type object to hold the partition data  
$val = "1/1/2003"."1/1/2004","1/1/2005"  
$pf.RangeValues = $val  
$pf  
#Create the partition function  
$pf.Create()  
  
#Create partition scheme  
$ps = New-Object -TypeName Microsoft.SqlServer.Management.SMO.PartitionScheme -argumentlist $db, "TransHistPS"  
$ps.PartitionFunction = "TransHistPF"  
  
#add the filegroups to the scheme
$ps.FileGroups.Add("PRIMARY")  
$ps.FileGroups.Add("Second")  
$ps.FileGroups.Add("Third")  
$ps.FileGroups.Add("Fourth")  
  
#Create it at the server  
$ps.Create()  
```  
  
## <a name="see-also"></a><span data-ttu-id="b4935-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4935-124">See Also</span></span>  
 [<span data-ttu-id="b4935-125">分割資料表與索引</span><span class="sxs-lookup"><span data-stu-id="b4935-125">Partitioned Tables and Indexes</span></span>](../../partitions/partitioned-tables-and-indexes.md)  
