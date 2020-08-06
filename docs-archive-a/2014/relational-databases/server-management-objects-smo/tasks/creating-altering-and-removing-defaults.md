---
title: 建立、改變和移除預設值 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- defaults [SMO]
ms.assetid: c30ac3b9-8150-4264-ba4c-c549f44261ab
author: stevestein
ms.author: sstein
ms.openlocfilehash: 747f7ff60122c5265cd68060063946a3e22d0301
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707338"
---
# <a name="creating-altering-and-removing-defaults"></a><span data-ttu-id="0fe1c-102">建立、改變和移除預設值</span><span class="sxs-lookup"><span data-stu-id="0fe1c-102">Creating, Altering, and Removing Defaults</span></span>
  <span data-ttu-id="0fe1c-103">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理物件 (SMO) 中，預設的條件約束是由 <xref:Microsoft.SqlServer.Management.Smo.Default> 物件表示。</span><span class="sxs-lookup"><span data-stu-id="0fe1c-103">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO), the default constraint is represented by the <xref:Microsoft.SqlServer.Management.Smo.Default> object.</span></span>  
  
 <span data-ttu-id="0fe1c-104"><xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> 物件的 <xref:Microsoft.SqlServer.Management.Smo.Default> 屬性可用於設定要插入的值。</span><span class="sxs-lookup"><span data-stu-id="0fe1c-104">The <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Default> object is used to set the value to be inserted.</span></span> <span data-ttu-id="0fe1c-105">這可以是常數，或傳回常數值的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式，例如 GETDATE()。</span><span class="sxs-lookup"><span data-stu-id="0fe1c-105">This can be a constant or a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement that returns a constant value, such as GETDATE().</span></span> <span data-ttu-id="0fe1c-106"><xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> 屬性無法藉由 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> 方法進行修改，</span><span class="sxs-lookup"><span data-stu-id="0fe1c-106">The <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> property cannot be modified by using the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> method.</span></span> <span data-ttu-id="0fe1c-107">反而必須將 <xref:Microsoft.SqlServer.Management.Smo.Default> 物件卸除，然後重新建立。</span><span class="sxs-lookup"><span data-stu-id="0fe1c-107">Instead, the <xref:Microsoft.SqlServer.Management.Smo.Default> object must be dropped and re-created.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fe1c-108">範例</span><span class="sxs-lookup"><span data-stu-id="0fe1c-108">Example</span></span>  
 <span data-ttu-id="0fe1c-109">如果要使用所提供的任何程式碼範例，您必須選擇建立應用程式用的程式設計環境、程式設計範本，及程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="0fe1c-109">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="0fe1c-110">如需詳細資訊，請參閱[在 Visual Studio .net 中建立 VISUAL BASIC SMO 專案](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)或[在 Visual Studio .Net 中建立 VISUAL C&#35; SMO 專案](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="0fe1c-110">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-altering-and-removing-a-default-in-visual-basic"></a><span data-ttu-id="0fe1c-111">在 Visual Basic 中建立、改變和移除預設值</span><span class="sxs-lookup"><span data-stu-id="0fe1c-111">Creating, Altering, and Removing a Default in Visual Basic</span></span>  
 <span data-ttu-id="0fe1c-112">此程式碼範例示範如何建立一個純文字的預設值，以及另一個 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式的預設值。</span><span class="sxs-lookup"><span data-stu-id="0fe1c-112">This code example shows how to create one default that is simple text, and another default that is a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="0fe1c-113">預設值必須使用 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> 方法附加到資料行，並使用 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A> 方法卸離。</span><span class="sxs-lookup"><span data-stu-id="0fe1c-113">The default must be attached to the column by using the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> method and detached by using the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A> method.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDefaults1](SMO How to#SMO_VBDefaults1)]  -->  
  
## <a name="creating-altering-and-removing-a-default-in-visual-c"></a><span data-ttu-id="0fe1c-114">在 Visual C# 中建立、改變和移除預設值</span><span class="sxs-lookup"><span data-stu-id="0fe1c-114">Creating, Altering, and Removing a Default in Visual C#</span></span>  
 <span data-ttu-id="0fe1c-115">此程式碼範例示範如何建立一個純文字的預設值，以及另一個 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式的預設值。</span><span class="sxs-lookup"><span data-stu-id="0fe1c-115">This code example shows how to create one default that is simple text, and another default that is a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="0fe1c-116">預設值必須使用 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> 方法附加到資料行，並使用 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A> 方法卸離。</span><span class="sxs-lookup"><span data-stu-id="0fe1c-116">The default must be attached to the column by using the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> method and detached by using the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A> method.</span></span>  
  
```csharp
{
          Server srv = new Server();  
  
            //Reference the AdventureWorks2012 database.   
            Database  db = srv.Databases["AdventureWorks2012"];  
  
            //Define a Default object variable by supplying the parent database and the default name   
            //in the constructor.   
            Default def = new Default(db, "Test_Default2");  
  
            //Set the TextHeader and TextBody properties that define the default.   
            def.TextHeader = "CREATE DEFAULT [Test_Default2] AS";  
            def.TextBody = "GetDate()";  
  
            //Create the default on the instance of SQL Server.   
            def.Create();  
  
            //Bind the default to a column in a table in AdventureWorks2012  
            def.BindToColumn("SpecialOffer", "StartDate", "Sales");  
  
            //Unbind the default from the column and remove it from the database.   
            def.UnbindFromColumn("SpecialOffer", "StartDate", "Sales");  
            def.Drop();  
        }  
```  
  
## <a name="creating-altering-and-removing-a-default-in-powershell"></a><span data-ttu-id="0fe1c-117">在 PowerShell 中建立、改變和移除預設值</span><span class="sxs-lookup"><span data-stu-id="0fe1c-117">Creating, Altering, and Removing a Default in PowerShell</span></span>  
 <span data-ttu-id="0fe1c-118">此程式碼範例示範如何建立一個純文字的預設值，以及另一個 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式的預設值。</span><span class="sxs-lookup"><span data-stu-id="0fe1c-118">This code example shows how to create one default that is simple text, and another default that is a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="0fe1c-119">預設值必須使用 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> 方法附加到資料行，並使用 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A> 方法卸離。</span><span class="sxs-lookup"><span data-stu-id="0fe1c-119">The default must be attached to the column by using the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> method and detached by using the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A> method.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = Get-Item Adventureworks2012  
  
#Define a Default object variable by supplying the parent database and the default name in the constructor.  
$def = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Default `  
-argumentlist $db, "Test_Default2"  
  
#Set the TextHeader and TextBody properties that define the default.   
$def.TextHeader = "CREATE DEFAULT [Test_Default2] AS"  
$def.TextBody = "GetDate()"  
  
#Create the default on the instance of SQL Server.   
$def.Create()  
  
#Bind the default to the column.   
$def.BindToColumn("SpecialOffer", "StartDate", "Sales")  
  
#Unbind the default from the column and remove it from the database.   
$def.UnbindFromColumn("SpecialOffer", "StartDate", "Sales")  
$def.Drop()  
```  
  
## <a name="see-also"></a><span data-ttu-id="0fe1c-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0fe1c-120">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.Default>  
