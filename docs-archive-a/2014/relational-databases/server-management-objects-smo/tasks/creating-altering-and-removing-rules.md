---
title: 建立、改變和移除規則 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- rules [SMO]
ms.assetid: 16981459-524e-4b39-a899-4370eaf763cc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7742a9cb718bdde4f268d5226c45eba475f44ddd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598258"
---
# <a name="creating-altering-and-removing-rules"></a><span data-ttu-id="0d8f2-102">建立、改變和移除規則</span><span class="sxs-lookup"><span data-stu-id="0d8f2-102">Creating, Altering, and Removing Rules</span></span>
  <span data-ttu-id="0d8f2-103">在 SMO 中，規則會以 <xref:Microsoft.SqlServer.Management.Smo.Rule> 物件表示，</span><span class="sxs-lookup"><span data-stu-id="0d8f2-103">In SMO, rules are represented by the <xref:Microsoft.SqlServer.Management.Smo.Rule> object.</span></span> <span data-ttu-id="0d8f2-104">並由 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> 屬性定義，該屬性是文字字串，包含使用運算子或述詞 (例如 IN、LIKE 或 BETWEEN) 的條件運算式。</span><span class="sxs-lookup"><span data-stu-id="0d8f2-104">The rule is defined by the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> property, which is a text string that contains a condition expression that uses operators or predicates, such as IN, LIKE, or BETWEEN.</span></span> <span data-ttu-id="0d8f2-105">規則不能參考資料行或其他資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="0d8f2-105">A rule cannot reference columns or other database objects.</span></span> <span data-ttu-id="0d8f2-106">未參考資料庫物件的內建函數可以包括在內。</span><span class="sxs-lookup"><span data-stu-id="0d8f2-106">Built-in functions that do not reference database objects can be included.</span></span>  
  
 <span data-ttu-id="0d8f2-107"><xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> 屬性中的定義必須包含參考所輸入之資料值的變數。</span><span class="sxs-lookup"><span data-stu-id="0d8f2-107">The definition in the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> property must contain a variable that refers to the data value entered.</span></span> <span data-ttu-id="0d8f2-108">建立規則時，可以使用任何名稱或符號來代表值，但第一個字元必須是 \@ 符號。</span><span class="sxs-lookup"><span data-stu-id="0d8f2-108">Any name or symbol can be used to represent the value when creating the rule, but the first character must be the \@ symbol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d8f2-109">範例</span><span class="sxs-lookup"><span data-stu-id="0d8f2-109">Example</span></span>  
 <span data-ttu-id="0d8f2-110">如果要使用所提供的任何程式碼範例，您必須選擇建立應用程式用的程式設計環境、程式設計範本，及程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="0d8f2-110">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="0d8f2-111">如需詳細資訊，請參閱[在 Visual Studio .net 中建立 VISUAL BASIC SMO 專案](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)或[在 Visual Studio .Net 中建立 VISUAL C&#35; SMO 專案](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="0d8f2-111">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-altering-and-removing-a-rule-in-visual-basic"></a><span data-ttu-id="0d8f2-112">在 Visual Basic 中建立、改變和移除規則</span><span class="sxs-lookup"><span data-stu-id="0d8f2-112">Creating, Altering, and Removing a Rule in Visual Basic</span></span>  
 <span data-ttu-id="0d8f2-113">此程式碼範例示範如何建立規則、將規則附加至資料行、修改 <xref:Microsoft.SqlServer.Management.Smo.Rule> 物件的屬性、將規則從資料行卸離，然後再加以卸除。</span><span class="sxs-lookup"><span data-stu-id="0d8f2-113">This code sample shows how to create a rule, attach it to a column, modify properties of the <xref:Microsoft.SqlServer.Management.Smo.Rule> object, detach it from the column, and then drop it.</span></span>  
  
 <span data-ttu-id="0d8f2-114"><xref:Microsoft.SqlServer.Management.Smo.Rule> 物件的 `Dim` 陳述式會以完整的組件路徑指定，以避免與 System.Data 組件中的 <xref:Microsoft.SqlServer.Management.Smo.Rule> 物件混淆。</span><span class="sxs-lookup"><span data-stu-id="0d8f2-114">The `Dim` statement for the <xref:Microsoft.SqlServer.Management.Smo.Rule> object is specified with the full assembly path to avoid ambiguity with a <xref:Microsoft.SqlServer.Management.Smo.Rule> object in the System.Data assembly.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBRules1](SMO How to#SMO_VBRules1)]  -->  
  
## <a name="creating-altering-and-removing-a-rule-in-visual-c"></a><span data-ttu-id="0d8f2-115">在 Visual C# 中建立、改變和移除規則</span><span class="sxs-lookup"><span data-stu-id="0d8f2-115">Creating, Altering, and Removing a Rule in Visual C#</span></span>  
 <span data-ttu-id="0d8f2-116">此程式碼範例示範如何建立規則、將規則附加至資料行、修改 <xref:Microsoft.SqlServer.Management.Smo.Rule> 物件的屬性、將規則從資料行卸離，然後再加以卸除。</span><span class="sxs-lookup"><span data-stu-id="0d8f2-116">This code sample shows how to create a rule, attach it to a column, modify properties of the <xref:Microsoft.SqlServer.Management.Smo.Rule> object, detach it from the column, and then drop it.</span></span>  
  
 <span data-ttu-id="0d8f2-117"><xref:Microsoft.SqlServer.Management.Smo.Rule> 物件的 `Dim` 陳述式會以完整的組件路徑指定，以避免與 System.Data 組件中的 <xref:Microsoft.SqlServer.Management.Smo.Rule> 物件混淆。</span><span class="sxs-lookup"><span data-stu-id="0d8f2-117">The `Dim` statement for the <xref:Microsoft.SqlServer.Management.Smo.Rule> object is specified with the full assembly path to avoid ambiguity with a <xref:Microsoft.SqlServer.Management.Smo.Rule> object in the System.Data assembly.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv;  
            srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db;  
            db = srv.Databases["AdventureWorks2012"];  
  
            //Define a Rule object variable by supplying the parent database, name and schema in the constructor.   
            //Note that the full namespace must be given for the Rule type to differentiate it from other Rule types.   
            Microsoft.SqlServer.Management.Smo.Rule ru;  
            ru = new Rule(db, "TestRule", "Production");  
            //Set the TextHeader and TextBody properties to define the rule.   
            ru.TextHeader = "CREATE RULE [Production].[TestRule] AS";  
            ru.TextBody = "@value BETWEEN GETDATE() AND DATEADD(year,4,GETDATE())";  
            //Create the rule on the instance of SQL Server.   
            ru.Create();  
            //Bind the rule to a column in the Product table by supplying the table, schema, and   
            //column as arguments in the BindToColumn method.   
            ru.BindToColumn("Product", "SellEndDate", "Production");  
            //Unbind from the column before removing the rule from the database.   
            ru.UnbindFromColumn("Product", "SellEndDate", "Production");  
            ru.Drop();  
  
        }  
```  
  
## <a name="creating-altering-and-removing-a-rule-in-powershell"></a><span data-ttu-id="0d8f2-118">在 PowerShell 中建立、改變和移除規則</span><span class="sxs-lookup"><span data-stu-id="0d8f2-118">Creating, Altering, and Removing a Rule in PowerShell</span></span>  
 <span data-ttu-id="0d8f2-119">此程式碼範例示範如何建立規則、將規則附加至資料行、修改 <xref:Microsoft.SqlServer.Management.Smo.Rule> 物件的屬性、將規則從資料行卸離，然後再加以卸除。</span><span class="sxs-lookup"><span data-stu-id="0d8f2-119">This code sample shows how to create a rule, attach it to a column, modify properties of the <xref:Microsoft.SqlServer.Management.Smo.Rule> object, detach it from the column, and then drop it.</span></span>  
  
 <span data-ttu-id="0d8f2-120"><xref:Microsoft.SqlServer.Management.Smo.Rule> 物件的 `Dim` 陳述式會以完整的組件路徑指定，以避免與 System.Data 組件中的 <xref:Microsoft.SqlServer.Management.Smo.Rule> 物件混淆。</span><span class="sxs-lookup"><span data-stu-id="0d8f2-120">The `Dim` statement for the <xref:Microsoft.SqlServer.Management.Smo.Rule> object is specified with the full assembly path to avoid ambiguity with a <xref:Microsoft.SqlServer.Management.Smo.Rule> object in the System.Data assembly.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = Get-Item Adventureworks2012  
  
# Define a Rule object variable by supplying the parent database, name and schema in the constructor.
$ru = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Rule -argumentlist $db, "TestRule", "Production"  
  
#Set the TextHeader and TextBody properties to define the rule.
$ru.TextHeader = "CREATE RULE [Production].[TestRule] AS"  
$ru.TextBody = "@value BETWEEN GETDATE() AND DATEADD(year,4,GETDATE())"  
  
#Create the rule on the instance of SQL Server.
$ru.Create()  
  
# Bind the rule to a column in the Product table by supplying the table, schema, and column as arguments in the BindToColumn method.
$ru.BindToColumn("Product", "SellEndDate", "Production")  
  
#Unbind from the column before removing the rule from the database.
$ru.UnbindFromColumn("Product", "SellEndDate", "Production")  
$ru.Drop()  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d8f2-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d8f2-121">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.Rule>  
