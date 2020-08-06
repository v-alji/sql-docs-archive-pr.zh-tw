---
title: 建立、改變和移除資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- databases [SMO]
- databases [SMO], creating
- databases [SMO], modifying
- databases [SMO], deleting
ms.assetid: fcfb3ec2-7556-4f72-971a-501295892cb0
author: stevestein
ms.author: sstein
ms.openlocfilehash: e8bd34e939fcbc1ecfc5238f5fc4524d187d3f30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707342"
---
# <a name="creating-altering-and-removing-databases"></a><span data-ttu-id="d06fb-102">建立、改變和移除資料庫</span><span class="sxs-lookup"><span data-stu-id="d06fb-102">Creating, Altering, and Removing Databases</span></span>
  <span data-ttu-id="d06fb-103">在 SMO 中，資料庫是由 <xref:Microsoft.SqlServer.Management.Smo.Database> 物件表示。</span><span class="sxs-lookup"><span data-stu-id="d06fb-103">In SMO, a database is represented by the <xref:Microsoft.SqlServer.Management.Smo.Database> object.</span></span>  
  
 <span data-ttu-id="d06fb-104">您不必建立 <xref:Microsoft.SqlServer.Management.Smo.Database> 物件，即可修改或移除該物件。</span><span class="sxs-lookup"><span data-stu-id="d06fb-104">It is not necessary to create a <xref:Microsoft.SqlServer.Management.Smo.Database> object to modify or remove it.</span></span> <span data-ttu-id="d06fb-105">您可以利用集合來參考資料庫。</span><span class="sxs-lookup"><span data-stu-id="d06fb-105">The database can be referenced by using a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d06fb-106">範例</span><span class="sxs-lookup"><span data-stu-id="d06fb-106">Example</span></span>  
 <span data-ttu-id="d06fb-107">如果要使用所提供的任何程式碼範例，您必須選擇建立應用程式用的程式設計環境、程式設計範本，及程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="d06fb-107">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="d06fb-108">如需詳細資訊，請參閱[在 Visual Studio .net 中建立 VISUAL BASIC SMO 專案](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)或[在 Visual Studio .Net 中建立 VISUAL C&#35; SMO 專案](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="d06fb-108">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-altering-and-removing-a-database-in-visual-basic"></a><span data-ttu-id="d06fb-109">在 Visual Basic 中建立、改變和移除資料庫</span><span class="sxs-lookup"><span data-stu-id="d06fb-109">Creating, Altering, and Removing a Database in Visual Basic</span></span>  
 <span data-ttu-id="d06fb-110">此程式碼範例會建立新資料庫，</span><span class="sxs-lookup"><span data-stu-id="d06fb-110">This code example creates a new database.</span></span> <span data-ttu-id="d06fb-111">並自動為資料庫建立檔案和檔案群組。</span><span class="sxs-lookup"><span data-stu-id="d06fb-111">Files and file groups are automatically created for the database.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDatabase1](SMO How to#SMO_VBDatabase1)]  -->  
  
## <a name="creating-altering-and-removing-a-database-in-visual-c"></a><span data-ttu-id="d06fb-112">在 Visual C# 中建立、改變和移除資料庫</span><span class="sxs-lookup"><span data-stu-id="d06fb-112">Creating, Altering, and Removing a Database in Visual C#</span></span>  
 <span data-ttu-id="d06fb-113">此程式碼範例會建立新資料庫，</span><span class="sxs-lookup"><span data-stu-id="d06fb-113">This code example creates a new database.</span></span> <span data-ttu-id="d06fb-114">並自動為資料庫建立檔案和檔案群組。</span><span class="sxs-lookup"><span data-stu-id="d06fb-114">Files and file groups are automatically created for the database.</span></span>  
  
```csharp
{  
                //Connect to the local, default instance of SQL Server.   
                Server srv;  
                srv = new Server();  
                //Define a Database object variable by supplying the server and the database name arguments in the constructor.   
                Database db;  
                db = new Database(srv, "Test_SMO_Database");  
                //Create the database on the instance of SQL Server.   
                db.Create();  
                //Reference the database and display the date when it was created.   
                db = srv.Databases["Test_SMO_Database"];  
                Console.WriteLine(db.CreateDate);  
                //Remove the database.   
                db.Drop();  
            }  
```  
  
## <a name="creating-altering-and-removing-a-database-in-powershell"></a><span data-ttu-id="d06fb-115">在 PowerShell 中建立、改變和移除資料庫</span><span class="sxs-lookup"><span data-stu-id="d06fb-115">Creating, Altering, and Removing a Database in PowerShell</span></span>  
 <span data-ttu-id="d06fb-116">此程式碼範例會建立新資料庫，</span><span class="sxs-lookup"><span data-stu-id="d06fb-116">This code example creates a new database.</span></span> <span data-ttu-id="d06fb-117">並自動為資料庫建立檔案和檔案群組。</span><span class="sxs-lookup"><span data-stu-id="d06fb-117">Files and file groups are automatically created for the database.</span></span>  
  
```powershell
#Get a server object which corresponds to the default instance  
cd \sql\localhost\  
$srv = Get-Item default  
  
#Create a new database  
$db = New-Object -TypeName Microsoft.SqlServer.Management.Smo.Database -argumentlist $srv, "Test_SMO_Database"  
$db.Create()  
  
#Reference the database and display the date when it was created.
$db = $srv.Databases["Test_SMO_Database"]  
$db.CreateDate  
  
#Drop the database  
$db.Drop()  
```  
  
## <a name="see-also"></a><span data-ttu-id="d06fb-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d06fb-118">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.Database>  
