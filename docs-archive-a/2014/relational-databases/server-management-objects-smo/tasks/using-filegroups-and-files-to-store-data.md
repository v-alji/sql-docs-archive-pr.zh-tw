---
title: 使用檔案群組和檔案來儲存資料 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- filegroups [SMO]
- storing data [SMO]
- files [SMO]
- files [SMO], about files
- storage [SMO]
ms.assetid: 7e2327ce-e1a6-4904-83d1-0944b24a7b43
author: stevestein
ms.author: sstein
ms.openlocfilehash: 15ac5fd0c43c9b58432a774ae11aeb6500f0403b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599440"
---
# <a name="using-filegroups-and-files-to-store-data"></a><span data-ttu-id="4c867-102">使用檔案群組和檔案來儲存資料</span><span class="sxs-lookup"><span data-stu-id="4c867-102">Using Filegroups and Files to Store Data</span></span>
  <span data-ttu-id="4c867-103">資料檔案可用於儲存資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="4c867-103">Data files are used to store database files.</span></span> <span data-ttu-id="4c867-104">資料檔案被分成檔案群組。</span><span class="sxs-lookup"><span data-stu-id="4c867-104">The data files are subdivided into file groups.</span></span> <span data-ttu-id="4c867-105"> 物件具有  屬性，這個屬性會參考  物件。</span><span class="sxs-lookup"><span data-stu-id="4c867-105">The <xref:Microsoft.SqlServer.Management.Smo.Database> object has a <xref:Microsoft.SqlServer.Management.Smo.Database.FileGroups%2A> property that references a <xref:Microsoft.SqlServer.Management.Smo.FileGroupCollection> object.</span></span> <span data-ttu-id="4c867-106">該集合中的每個 <xref:Microsoft.SqlServer.Management.Smo.FileGroup> 物件都具有 <xref:Microsoft.SqlServer.Management.Smo.FileGroup.Files%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="4c867-106">Each <xref:Microsoft.SqlServer.Management.Smo.FileGroup> object in that collection has a <xref:Microsoft.SqlServer.Management.Smo.FileGroup.Files%2A> property.</span></span> <span data-ttu-id="4c867-107">這個屬性會參考 <xref:Microsoft.SqlServer.Management.Smo.DataFileCollection> 集合，其中包含資料庫所屬的所有資料檔。</span><span class="sxs-lookup"><span data-stu-id="4c867-107">This property refers to a <xref:Microsoft.SqlServer.Management.Smo.DataFileCollection> collection that contains all the data files that belong to the database.</span></span> <span data-ttu-id="4c867-108">檔案群組的主要功能是將用於儲存資料庫物件的檔案放入群組。</span><span class="sxs-lookup"><span data-stu-id="4c867-108">A file group is principally used to group files together that are used to store a database object.</span></span> <span data-ttu-id="4c867-109">將一個資料庫物件散佈到數個檔案的其中一個理由就是改善效能，特別是如果檔案儲存在不同的磁碟機上。</span><span class="sxs-lookup"><span data-stu-id="4c867-109">One reason for spreading a database object over several files is that it can improve performance, especially if the files are stored on different disk drives.</span></span>  
  
 <span data-ttu-id="4c867-110">每個自動建立的資料庫都具有名為 "Primary" 的檔案群組以及與資料庫同名的資料檔。</span><span class="sxs-lookup"><span data-stu-id="4c867-110">Every database that is created automatically has a file group named "Primary" and a data file with the same name as the database.</span></span> <span data-ttu-id="4c867-111">可以在集合中加入其他檔案和群組。</span><span class="sxs-lookup"><span data-stu-id="4c867-111">Additional files and groups can be added to the collections.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="4c867-112">範例</span><span class="sxs-lookup"><span data-stu-id="4c867-112">Examples</span></span>  
 <span data-ttu-id="4c867-113">在下列的程式碼範例中，您必須選取用於建立應用程式的程式設計環境、程式設計範本和程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="4c867-113">For the following code examples, you will have to select the programming environment, programming template and the programming language to create your application.</span></span> <span data-ttu-id="4c867-114">如需詳細資訊，請參閱[在 Visual Studio .net 中建立 VISUAL BASIC SMO 專案](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)和[在 Visual Studio .Net 中建立 VISUAL C&#35; SMO 專案](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="4c867-114">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) and [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="adding-filegroups-and-datafiles-to-a-database-in-visual-basic"></a><span data-ttu-id="4c867-115">在 Visual Basic 中將 FileGroups 和 DataFiles 加入至資料庫</span><span class="sxs-lookup"><span data-stu-id="4c867-115">Adding FileGroups and DataFiles to a Database in Visual Basic</span></span>  
 <span data-ttu-id="4c867-116">主要檔案群組和資料檔會使用預設的屬性值自動建立。</span><span class="sxs-lookup"><span data-stu-id="4c867-116">The primary file group and data file are created automatically with default property values.</span></span> <span data-ttu-id="4c867-117">程式碼範例會指定某些可以使用的某些屬性值；</span><span class="sxs-lookup"><span data-stu-id="4c867-117">The code example specifies some property values that you can use.</span></span> <span data-ttu-id="4c867-118">否則，系統會使用預設屬性值。</span><span class="sxs-lookup"><span data-stu-id="4c867-118">Otherwise, the default property values are used.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBFileGroups1](SMO How to#SMO_VBFileGroups1)]  -->  
  
## <a name="adding-filegroups-and-datafiles-to-a-database-in-visual-c"></a><span data-ttu-id="4c867-119">在 Visual C# 中將 FileGroups 和 DataFiles 加入至資料庫</span><span class="sxs-lookup"><span data-stu-id="4c867-119">Adding FileGroups and DataFiles to a Database in Visual C#</span></span>  
 <span data-ttu-id="4c867-120">主要檔案群組和資料檔會使用預設的屬性值自動建立。</span><span class="sxs-lookup"><span data-stu-id="4c867-120">The primary file group and data file are created automatically with default property values.</span></span> <span data-ttu-id="4c867-121">程式碼範例會指定某些可以使用的某些屬性值；</span><span class="sxs-lookup"><span data-stu-id="4c867-121">The code example specifies some property values that you can use.</span></span> <span data-ttu-id="4c867-122">否則，系統會使用預設屬性值。</span><span class="sxs-lookup"><span data-stu-id="4c867-122">Otherwise, the default property values are used.</span></span>  
  
```csharp
{  
            Server srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db = default(Database);  
            db = srv.Databases["AdventureWorks2012"];  
            //Define a FileGroup object called SECONDARY on the database.   
            FileGroup fg1 = default(FileGroup);  
            fg1 = new FileGroup(db, "SECONDARY");  
            //Call the Create method to create the file group on the instance of SQL Server.   
            fg1.Create();  
            //Define a DataFile object on the file group and set the FileName property.   
            DataFile df1 = default(DataFile);  
            df1 = new DataFile(fg1, "datafile1");  
            df1.FileName = "c:\\Program Files\\Microsoft SQL Server\\MSSQL.1\\MSSQL\\Data\\datafile2.ndf";  
            //Call the Create method to create the data file on the instance of SQL Server.   
            df1.Create();  
        }  
```  
  
## <a name="adding-filegroups-and-datafiles-to-a-database-in-powershell"></a><span data-ttu-id="4c867-123">在 PowerShell 中將 FileGroups 和 DataFiles 加入至資料庫</span><span class="sxs-lookup"><span data-stu-id="4c867-123">Adding FileGroups and DataFiles to a Database in PowerShell</span></span>  
 <span data-ttu-id="4c867-124">主要檔案群組和資料檔會使用預設的屬性值自動建立。</span><span class="sxs-lookup"><span data-stu-id="4c867-124">The primary file group and data file are created automatically with default property values.</span></span> <span data-ttu-id="4c867-125">程式碼範例會指定某些可以使用的某些屬性值；</span><span class="sxs-lookup"><span data-stu-id="4c867-125">The code example specifies some property values that you can use.</span></span> <span data-ttu-id="4c867-126">否則，系統會使用預設屬性值。</span><span class="sxs-lookup"><span data-stu-id="4c867-126">Otherwise, the default property values are used.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\default\Databases\  
  
#And the database object corresponding to AdventureWorks2012.  
$db = get-item AdventureWorks2012  
  
#Create a new filegroup  
$fg1 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Filegroup -argumentlist $db, "SECONDARY"  
$fg1.Create()  
  
#Define a DataFile object on the file group and set the FileName property.   
$df1 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.DataFile -argumentlist $fg1, "datafile1"  
  
#Make sure to have a directory created to hold the designated data file  
$df1.FileName = "c:\\TestData\\datafile2.ndf"  
  
#Call the Create method to create the data file on the instance of SQL Server.   
$df1.Create()  
```  
  
## <a name="creating-altering-and-removing-a-log-file-in-visual-basic"></a><span data-ttu-id="4c867-127">在 Visual Basic 中建立、改變和移除記錄檔</span><span class="sxs-lookup"><span data-stu-id="4c867-127">Creating, Altering, and Removing a Log File in Visual Basic</span></span>  
 <span data-ttu-id="4c867-128">程式碼範例會建立 <xref:Microsoft.SqlServer.Management.Smo.LogFile> 物件、變更其中一個屬性，然後將它從資料庫移除。</span><span class="sxs-lookup"><span data-stu-id="4c867-128">The code example creates a <xref:Microsoft.SqlServer.Management.Smo.LogFile> object, changes one of the properties, and then removes it from the database.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBFileGroups3](SMO How to#SMO_VBFileGroups3)]  -->  
  
## <a name="creating-altering-and-removing-a-log-file-in-visual-c"></a><span data-ttu-id="4c867-129">在 Visual C# 中建立、改變和移除記錄檔</span><span class="sxs-lookup"><span data-stu-id="4c867-129">Creating, Altering, and Removing a Log File in Visual C#</span></span>  
 <span data-ttu-id="4c867-130">程式碼範例會建立 <xref:Microsoft.SqlServer.Management.Smo.LogFile> 物件、變更其中一個屬性，然後將它從資料庫移除。</span><span class="sxs-lookup"><span data-stu-id="4c867-130">The code example creates a <xref:Microsoft.SqlServer.Management.Smo.LogFile> object, changes one of the properties, and then removes it from the database.</span></span>  
  
```csharp
//Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db = default(Database);  
            db = srv.Databases["AdventureWorks2012"];  
            //Define a LogFile object and set the database, name, and file name properties in the constructor.   
            LogFile lf1 = default(LogFile);  
            lf1 = new LogFile(db, "logfile1", "c:\\Program Files\\Microsoft SQL Server\\MSSQL.10_50.MSSQLSERVER\\MSSQL\\Data\\logfile1.ldf");  
            //Set the file growth to 6%.   
            lf1.GrowthType = FileGrowthType.Percent;  
            lf1.Growth = 6;  
            //Run the Create method to create the log file on the instance of SQL Server.   
            lf1.Create();  
            //Alter the growth percentage.
            lf1.Growth = 7;  
            lf1.Alter();  
            //Remove the log file.
            lf1.Drop();
```  
  
## <a name="creating-altering-and-removing-a-log-file-in-powershell"></a><span data-ttu-id="4c867-131">在 PowerShell 中建立、改變和移除記錄檔</span><span class="sxs-lookup"><span data-stu-id="4c867-131">Creating, Altering, and Removing a Log File in PowerShell</span></span>  
 <span data-ttu-id="4c867-132">程式碼範例會建立 <xref:Microsoft.SqlServer.Management.Smo.LogFile> 物件、變更其中一個屬性，然後將它從資料庫移除。</span><span class="sxs-lookup"><span data-stu-id="4c867-132">The code example creates a <xref:Microsoft.SqlServer.Management.Smo.LogFile> object, changes one of the properties, and then removes it from the database.</span></span>  
  
```powershell
#Load the assembly containing the enums used in this example  
[reflection.assembly]::LoadWithPartialName("Microsoft.SqlServer.SqlEnum")  
  
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\default\Databases\  
  
#And the database object corresponding to AdventureWorks2012  
$db = get-item AdventureWorks2012  
  
#Create a filegroup  
$fg1 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Filegroup -argumentlist $db, "Secondary"  
  
#Call the Create method to create the file group on the instance of SQL Server.   
$fg1.Create()  
  
#Define a LogFile object on the file group and set the FileName property.   
$lf1 = New-Object -TypeName Microsoft.SqlServer.Management.SMO.LogFile -argumentlist $db, "LogFile2"  
  
#Set a location for it - make sure the directory exists  
$lf1.FileName = "logfile1", "c:\\Program Files\\Microsoft SQL Server\\MSSQL.10_50.MSSQLSERVER\\MSSQL\\Data\\logfile1.ldf"  
  
#Set file growth to 6%  
$lf1.GrowthType = [Microsoft.SqlServer.Management.Smo.FileGrowthType]::Percent  
$lf1.Growth = 6.0  
  
#Call the Create method to create the data file on the instance of SQL Server.   
$lf1.Create()  
  
#Alter a value and drop the log file  
$lf1.Growth = 7.0  
$lf1.Alter()  
$lf1.Drop()
```  
  
## <a name="see-also"></a><span data-ttu-id="4c867-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c867-133">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.FileGroup>   
 [<span data-ttu-id="4c867-134">資料庫檔案與檔案群組</span><span class="sxs-lookup"><span data-stu-id="4c867-134">Database Files and Filegroups</span></span>](../../databases/database-files-and-filegroups.md)  
