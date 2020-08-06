---
title: 建立、改變和移除視圖 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- views [SMO]
ms.assetid: 7d445c0e-77ef-4734-993b-e022de31df23
author: stevestein
ms.author: sstein
ms.openlocfilehash: fd8d75e413b1871ce4b8784f5087cb08ed08da73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606181"
---
# <a name="creating-altering-and-removing-views"></a><span data-ttu-id="cd36d-102">建立、改變和移除檢視</span><span class="sxs-lookup"><span data-stu-id="cd36d-102">Creating, Altering, and Removing Views</span></span>
  <span data-ttu-id="cd36d-103">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理物件 (SMO) 中，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 檢視是由 <xref:Microsoft.SqlServer.Management.Smo.View> 物件表示。</span><span class="sxs-lookup"><span data-stu-id="cd36d-103">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO), [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] views are represented by the <xref:Microsoft.SqlServer.Management.Smo.View> object.</span></span>  
  
 <span data-ttu-id="cd36d-104"><xref:Microsoft.SqlServer.Management.Smo.View.TextBody%2A> 物件的 <xref:Microsoft.SqlServer.Management.Smo.View> 屬性會定義檢視。</span><span class="sxs-lookup"><span data-stu-id="cd36d-104">The <xref:Microsoft.SqlServer.Management.Smo.View.TextBody%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.View> object defines the view.</span></span> <span data-ttu-id="cd36d-105">該屬性等於用於建立檢視的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="cd36d-105">It is the equivalent of the [!INCLUDE[tsql](../../../includes/tsql-md.md)] SELECT statement for creating a view.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd36d-106">範例</span><span class="sxs-lookup"><span data-stu-id="cd36d-106">Example</span></span>  
 <span data-ttu-id="cd36d-107">如果要使用所提供的任何程式碼範例，您必須選擇建立應用程式用的程式設計環境、程式設計範本，及程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="cd36d-107">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="cd36d-108">如需詳細資訊，請參閱[在 Visual Studio .net 中建立 VISUAL BASIC SMO 專案](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)或[在 Visual Studio .Net 中建立 VISUAL C&#35; SMO 專案](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="cd36d-108">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-altering-and-removing-a-view-in-visual-basic"></a><span data-ttu-id="cd36d-109">在 Visual Basic 中建立、改變和移除檢視</span><span class="sxs-lookup"><span data-stu-id="cd36d-109">Creating, Altering, and Removing a View in Visual Basic</span></span>  
 <span data-ttu-id="cd36d-110">此程式碼範例示範如何使用內部聯結建立兩個資料表的檢視。</span><span class="sxs-lookup"><span data-stu-id="cd36d-110">This code sample shows how to create a view of two tables by using an inner join.</span></span> <span data-ttu-id="cd36d-111">該檢視是利用文字模式建立，所以必須設定 <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="cd36d-111">The view is created by using text mode, so the <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> property must be set.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBViews1](SMO How to#SMO_VBViews1)]  -->  
  
## <a name="creating-altering-and-removing-a-view-in-visual-c"></a><span data-ttu-id="cd36d-112">在 Visual C# 中建立、改變和移除檢視</span><span class="sxs-lookup"><span data-stu-id="cd36d-112">Creating, Altering, and Removing a View in Visual C#</span></span>  
 <span data-ttu-id="cd36d-113">此程式碼範例示範如何使用內部聯結建立兩個資料表的檢視。</span><span class="sxs-lookup"><span data-stu-id="cd36d-113">This code sample shows how to create a view of two tables by using an inner join.</span></span> <span data-ttu-id="cd36d-114">該檢視是利用文字模式建立，所以必須設定 <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="cd36d-114">The view is created by using text mode, so the <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> property must be set.</span></span>  
  
```csharp
{  
        //Connect to the local, default instance of SQL Server.   
        Server srv;   
        srv = new Server();   
        //Reference the AdventureWorks2012 database.   
        Database db;   
        db = srv.Databases["AdventureWorks2012"];   
        //Define a View object variable by supplying the parent database, view name and schema in the constructor.   
        View myview;   
        myview = new View(db, "Test_View", "Sales");   
        //Set the TextHeader and TextBody property to define the view.   
        myview.TextHeader = "CREATE VIEW [Sales].[Test_View] AS";   
        myview.TextBody = "SELECT h.SalesOrderID, d.OrderQty FROM Sales.SalesOrderHeader AS h INNER JOIN Sales.SalesOrderDetail AS d ON h.SalesOrderID = d.SalesOrderID";   
        //Create the view on the instance of SQL Server.   
        myview.Create();   
        //Remove the view.   
        myview.Drop();   
        }  
```  
  
## <a name="creating-altering-and-removing-a-view-in-powershell"></a><span data-ttu-id="cd36d-115">在 PowerShell 中建立、改變和移除檢視</span><span class="sxs-lookup"><span data-stu-id="cd36d-115">Creating, Altering, and Removing a View in PowerShell</span></span>  
 <span data-ttu-id="cd36d-116">此程式碼範例示範如何使用內部聯結建立兩個資料表的檢視。</span><span class="sxs-lookup"><span data-stu-id="cd36d-116">This code sample shows how to create a view of two tables by using an inner join.</span></span> <span data-ttu-id="cd36d-117">該檢視是利用文字模式建立，所以必須設定 <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="cd36d-117">The view is created by using text mode, so the <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> property must be set.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = Get-Item Adventureworks2012  
  
# Define a View object variable by supplying the parent database, view name and schema in the constructor.
$myview  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.View -argumentlist $db, "Test_View", "Sales"  
  
# Set the TextHeader and TextBody property to define the view.
$myview.TextHeader = "CREATE VIEW [Sales].[Test_View] AS"  
$myview.TextBody ="SELECT h.SalesOrderID, d.OrderQty FROM Sales.SalesOrderHeader AS h INNER JOIN Sales.SalesOrderDetail AS d ON h.SalesOrderID = d.SalesOrderID"  
  
# Create the view on the instance of SQL Server.
$myview.Create()  
  
# Remove the view
$myview.Drop();  
```  
  
## <a name="see-also"></a><span data-ttu-id="cd36d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd36d-118">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.View>  
