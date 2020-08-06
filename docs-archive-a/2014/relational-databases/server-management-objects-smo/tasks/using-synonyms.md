---
title: 使用同義字 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- synonyms [SMO]
ms.assetid: db0a9022-9549-43e5-b6b3-deb236f05fb8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5e8416dc3daea3b173fae92e5454a8a65c399e53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606712"
---
# <a name="using-synonyms"></a><span data-ttu-id="c90a7-102">使用同義字</span><span class="sxs-lookup"><span data-stu-id="c90a7-102">Using Synonyms</span></span>
  <span data-ttu-id="c90a7-103">同義字是結構描述範圍物件的替代名稱。</span><span class="sxs-lookup"><span data-stu-id="c90a7-103">A synonym is an alternative name for a schema-scoped object.</span></span> <span data-ttu-id="c90a7-104">在 SMO 中，同義字是由 <xref:Microsoft.SqlServer.Management.Smo.Synonym> 物件表示。</span><span class="sxs-lookup"><span data-stu-id="c90a7-104">In SMO, synonyms are represented by the <xref:Microsoft.SqlServer.Management.Smo.Synonym> object.</span></span> <span data-ttu-id="c90a7-105"><xref:Microsoft.SqlServer.Management.Smo.Synonym> 物件是 <xref:Microsoft.SqlServer.Management.Smo.Database> 物件的子系。</span><span class="sxs-lookup"><span data-stu-id="c90a7-105">The <xref:Microsoft.SqlServer.Management.Smo.Synonym> object is a child of the <xref:Microsoft.SqlServer.Management.Smo.Database> object.</span></span> <span data-ttu-id="c90a7-106">這表示同義字只有在其定義所在的資料庫範圍內才有效。</span><span class="sxs-lookup"><span data-stu-id="c90a7-106">This means that synonyms are valid only within the scope of the database in which they are defined.</span></span> <span data-ttu-id="c90a7-107">不過，同義字可以參考另一個資料庫或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]遠端執行個體上的物件。</span><span class="sxs-lookup"><span data-stu-id="c90a7-107">However, the synonym can refer to objects on another database, or on a remote instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="c90a7-108">已具有給定替代名稱的物件也稱為基底物件。</span><span class="sxs-lookup"><span data-stu-id="c90a7-108">The object that is given an alternative name is known as the base object.</span></span> <span data-ttu-id="c90a7-109"><xref:Microsoft.SqlServer.Management.Smo.Synonym> 物件的名稱屬性是為基底物件所提供的替代名稱。</span><span class="sxs-lookup"><span data-stu-id="c90a7-109">The name property of the <xref:Microsoft.SqlServer.Management.Smo.Synonym> object is the alternative name given to the base object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c90a7-110">範例</span><span class="sxs-lookup"><span data-stu-id="c90a7-110">Example</span></span>  
 <span data-ttu-id="c90a7-111">在下列的程式碼範例中，您必須選取用於建立應用程式的程式設計環境、程式設計範本和程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="c90a7-111">For the following code example, you will have to select the programming environment, programming template and the programming language to create your application.</span></span> <span data-ttu-id="c90a7-112">如需詳細資訊，請參閱[在 Visual Studio .net 中建立 VISUAL BASIC SMO 專案](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)和[在 Visual Studio .Net 中建立 VISUAL C&#35; SMO 專案](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="c90a7-112">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) and [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-a-synonym-in-visual-basic"></a><span data-ttu-id="c90a7-113">在 Visual Basic 中建立同義字</span><span class="sxs-lookup"><span data-stu-id="c90a7-113">Creating a Synonym in Visual Basic</span></span>  
 <span data-ttu-id="c90a7-114">此程式碼範例示範如何為結構描述範圍物件建立同義字或替代名稱。</span><span class="sxs-lookup"><span data-stu-id="c90a7-114">The code example shows how to create a synonym or an alternate name for a schema scoped object.</span></span> <span data-ttu-id="c90a7-115">用戶端應用程式可以透過同義字使用單一參考來參考基底物件，而不是使用多重部分名稱來參考基底物件。</span><span class="sxs-lookup"><span data-stu-id="c90a7-115">Client applications can use a single reference for the base object via a synonym instead of using a multiple part name to reference the base object.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBSynonyms1](SMO How to#SMO_VBSynonyms1)]  -->  
  
## <a name="creating-a-synonym-in-visual-c"></a><span data-ttu-id="c90a7-116">在 Visual C# 中建立同義字</span><span class="sxs-lookup"><span data-stu-id="c90a7-116">Creating a Synonym in Visual C#</span></span>  
 <span data-ttu-id="c90a7-117">此程式碼範例示範如何為結構描述範圍物件建立同義字或替代名稱。</span><span class="sxs-lookup"><span data-stu-id="c90a7-117">The code example shows how to create a synonym or an alternate name for a schema scoped object.</span></span> <span data-ttu-id="c90a7-118">用戶端應用程式可以透過同義字使用單一參考來參考基底物件，而不是使用多重部分名稱來參考基底物件。</span><span class="sxs-lookup"><span data-stu-id="c90a7-118">Client applications can use a single reference for the base object via a synonym instead of using a multiple part name to reference the base object.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
  
            //Reference the AdventureWorks2012 database.   
            Database db = srv.Databases["AdventureWorks2012"];  
  
            //Define a Synonym object variable by supplying the   
            //parent database, name, and schema arguments in the constructor.   
            //The name is also a synonym of the name of the base object.   
            Synonym syn = new Synonym(db, "Shop", "Sales");  
  
            //Specify the base object, which is the object on which   
            //the synonym is based.   
            syn.BaseDatabase = "AdventureWorks2012";  
            syn.BaseSchema = "Sales";  
            syn.BaseObject = "Store";  
            syn.BaseServer = srv.Name;  
  
            //Create the synonym on the instance of SQL Server.   
            syn.Create();  
        }  
```  
  
## <a name="creating-a-synonym-in-powershell"></a><span data-ttu-id="c90a7-119">在 PowerShell 中建立同義字</span><span class="sxs-lookup"><span data-stu-id="c90a7-119">Creating a Synonym in PowerShell</span></span>  
 <span data-ttu-id="c90a7-120">此程式碼範例示範如何為結構描述範圍物件建立同義字或替代名稱。</span><span class="sxs-lookup"><span data-stu-id="c90a7-120">The code example shows how to create a synonym or an alternate name for a schema scoped object.</span></span> <span data-ttu-id="c90a7-121">用戶端應用程式可以透過同義字使用單一參考來參考基底物件，而不是使用多重部分名稱來參考基底物件。</span><span class="sxs-lookup"><span data-stu-id="c90a7-121">Client applications can use a single reference for the base object via a synonym instead of using a multiple part name to reference the base object.</span></span>  
  
```powershell
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#And the database object corresponding to Adventureworks  
$db = $srv.Databases["AdventureWorks2012"]  
  
$syn = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Synonym -ArgumentList $db, "Shop", "Sales"  
  
#Specify the base object, which is the object on which the synonym is based.  
$syn.BaseDatabase = "AdventureWorks2012"  
$syn.BaseSchema = "Sales"  
$syn.BaseObject = "Store"  
$syn.BaseServer = $srv.Name  
  
#Create the synonym on the instance of SQL Server.  
$syn.Create()  
```  
  
## <a name="see-also"></a><span data-ttu-id="c90a7-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c90a7-122">See Also</span></span>  
 [<span data-ttu-id="c90a7-123">CREATE SYNONYM &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c90a7-123">CREATE SYNONYM &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-synonym-transact-sql)  
