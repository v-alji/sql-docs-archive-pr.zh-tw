---
title: 使用集合 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQL Server Management Objects, collections
- SMO [SQL Server], collections
- collections [SMO]
ms.assetid: 209eb175-2514-4de1-bc32-b2e6a469d945
author: stevestein
ms.author: sstein
ms.openlocfilehash: 288f2110952a85d2aab610c0f1da40d433882400
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592557"
---
# <a name="using-collections"></a><span data-ttu-id="07d5e-102">使用集合</span><span class="sxs-lookup"><span data-stu-id="07d5e-102">Using Collections</span></span>
  <span data-ttu-id="07d5e-103">集合是已經從相同物件類別建構，而且共用相同父物件的物件清單。</span><span class="sxs-lookup"><span data-stu-id="07d5e-103">A collection is a list of objects that have been constructed from the same object class and that share the same parent object.</span></span> <span data-ttu-id="07d5e-104">集合物件一定會包含具有 Collection 後置詞之物件類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="07d5e-104">The collection object always contains the name of the object type with the Collection suffix.</span></span> <span data-ttu-id="07d5e-105">例如，若要存取指定之資料表內的資料行，請使用 <xref:Microsoft.SqlServer.Management.Smo.ColumnCollection> 物件類型。</span><span class="sxs-lookup"><span data-stu-id="07d5e-105">For example, to access the columns in a specified table, use the <xref:Microsoft.SqlServer.Management.Smo.ColumnCollection> object type.</span></span> <span data-ttu-id="07d5e-106">它會包含屬於相同 <xref:Microsoft.SqlServer.Management.Smo.Column> 物件的所有 <xref:Microsoft.SqlServer.Management.Smo.Table> 物件。</span><span class="sxs-lookup"><span data-stu-id="07d5e-106">It contains all the <xref:Microsoft.SqlServer.Management.Smo.Column> objects that belong to the same <xref:Microsoft.SqlServer.Management.Smo.Table> object.</span></span>  
  
 <span data-ttu-id="07d5e-107">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] `For...Each` 語句或 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] `foreach` 語句可以用來逐一查看集合的每個成員。</span><span class="sxs-lookup"><span data-stu-id="07d5e-107">The [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] `For...Each` statement or the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] `foreach` statement can be used to iterate through each member of the collection.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="07d5e-108">範例</span><span class="sxs-lookup"><span data-stu-id="07d5e-108">Examples</span></span>  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="referencing-an-object-by-using-a-collection-in-visual-basic"></a><span data-ttu-id="07d5e-109">在 Visual Basic 中使用集合來參考物件</span><span class="sxs-lookup"><span data-stu-id="07d5e-109">Referencing an Object by Using a Collection in Visual Basic</span></span>  
 <span data-ttu-id="07d5e-110">此程式碼範例示範如何使用 <xref:Microsoft.SqlServer.Management.Smo.TableViewTableTypeBase.Columns%2A>、<xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> 和 <xref:Microsoft.SqlServer.Management.Smo.Server.Databases%2A> 屬性來設定資料行屬性。</span><span class="sxs-lookup"><span data-stu-id="07d5e-110">This code example shows how to set a column property by using the <xref:Microsoft.SqlServer.Management.Smo.TableViewTableTypeBase.Columns%2A>, <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A>, and <xref:Microsoft.SqlServer.Management.Smo.Server.Databases%2A> properties.</span></span> <span data-ttu-id="07d5e-111">這些屬性代表集合，當這些屬性搭配可指定物件名稱的參數使用時，就可用來識別特定物件。</span><span class="sxs-lookup"><span data-stu-id="07d5e-111">These properties represent collections, which can be used to identify a particular object when they are used with a parameter that specifies the name of the object.</span></span> <span data-ttu-id="07d5e-112"><xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> 集合物件屬性需要名稱和結構描述。</span><span class="sxs-lookup"><span data-stu-id="07d5e-112">The name and the schema are required for the <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> collection object property.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBCollections1](SMO How to#SMO_VBCollections1)]  -->  
  
## <a name="referencing-an-object-by-using-a-collection-in-visual-c"></a><span data-ttu-id="07d5e-113">在 Visual C# 中使用集合來參考物件</span><span class="sxs-lookup"><span data-stu-id="07d5e-113">Referencing an Object by Using a Collection in Visual C#</span></span>  
 <span data-ttu-id="07d5e-114">此程式碼範例示範如何使用 <xref:Microsoft.SqlServer.Management.Smo.TableViewTableTypeBase.Columns%2A>、<xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> 和 <xref:Microsoft.SqlServer.Management.Smo.Server.Databases%2A> 屬性來設定資料行屬性。</span><span class="sxs-lookup"><span data-stu-id="07d5e-114">This code example shows how to set a column property by using the <xref:Microsoft.SqlServer.Management.Smo.TableViewTableTypeBase.Columns%2A>, <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A>, and <xref:Microsoft.SqlServer.Management.Smo.Server.Databases%2A> properties.</span></span> <span data-ttu-id="07d5e-115">這些屬性代表集合，當這些屬性搭配可指定物件名稱的參數使用時，就可用來識別特定物件。</span><span class="sxs-lookup"><span data-stu-id="07d5e-115">These properties represent collections, which can be used to identify a particular object when they are used with a parameter that specifies the name of the object.</span></span> <span data-ttu-id="07d5e-116"><xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> 集合物件屬性需要名稱和結構描述。</span><span class="sxs-lookup"><span data-stu-id="07d5e-116">The name and the schema are required for the <xref:Microsoft.SqlServer.Management.Smo.Database.Tables%2A> collection object property.</span></span>  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Modify a property using the Databases, Tables, and Columns collections to reference a column.   
srv.Databases("AdventureWorks2012").Tables("Person", "Person").Columns("LastName").Nullable = true;   
//Call the Alter method to make the change on the instance of SQL Server.   
srv.Databases("AdventureWorks2012").Tables("Person", "Person").Columns("LastName").Alter();   
}  
```  
  
## <a name="iterating-through-the-members-of-a-collection-in-visual-basic"></a><span data-ttu-id="07d5e-117">在 Visual Basic 中逐一查看集合的成員</span><span class="sxs-lookup"><span data-stu-id="07d5e-117">Iterating Through the Members of a Collection in Visual Basic</span></span>  
 <span data-ttu-id="07d5e-118">此程式碼範例會逐一查看 <xref:Microsoft.AnalysisServices.Server.Databases%2A> 集合屬性，並顯示與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的所有資料庫連接。</span><span class="sxs-lookup"><span data-stu-id="07d5e-118">This code example iterates through the <xref:Microsoft.AnalysisServices.Server.Databases%2A> collection property and displays all database connections to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBCollections2](SMO How to#SMO_VBCollections2)]  -->  
  
## <a name="iterating-through-the-members-of-a-collection-in-visual-c"></a><span data-ttu-id="07d5e-119">在 Visual C# 中逐一查看集合的成員</span><span class="sxs-lookup"><span data-stu-id="07d5e-119">Iterating Through the Members of a Collection in Visual C#</span></span>  
 <span data-ttu-id="07d5e-120">此程式碼範例會逐一查看 <xref:Microsoft.AnalysisServices.Server.Databases%2A> 集合屬性，並顯示與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的所有資料庫連接。</span><span class="sxs-lookup"><span data-stu-id="07d5e-120">This code example iterates through the <xref:Microsoft.AnalysisServices.Server.Databases%2A> collection property and displays all database connections to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
```  
//Connect to the local, default instance of SQL Server.   
{   
Server srv = default(Server);   
srv = new Server();   
int count = 0;   
int total = 0;   
//Iterate through the databases and call the GetActiveDBConnectionCount method.   
Database db = default(Database);   
foreach ( db in srv.Databases) {   
  count = srv.GetActiveDBConnectionCount(db.Name);   
  total = total + count;   
  //Display the number of connections for each database.   
  Console.WriteLine(count + " connections on " + db.Name);   
}   
//Display the total number of connections on the instance of SQL Server.   
Console.WriteLine("Total connections =" + total);   
}   
```  
  
  
