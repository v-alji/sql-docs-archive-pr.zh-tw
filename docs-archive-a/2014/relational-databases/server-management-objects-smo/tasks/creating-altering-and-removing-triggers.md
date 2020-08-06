---
title: 建立、改變和移除觸發程式 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- triggers [SMO]
ms.assetid: 8ddbe23b-6e31-4f8e-8a70-17bd5072413e
author: stevestein
ms.author: sstein
ms.openlocfilehash: c2cdd1573c488fbe7b2309f656cd6bf42e82a527
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606183"
---
# <a name="creating-altering-and-removing-triggers"></a><span data-ttu-id="9571a-102">建立、改變和移除觸發程式</span><span class="sxs-lookup"><span data-stu-id="9571a-102">Creating, Altering, and Removing Triggers</span></span>
  <span data-ttu-id="9571a-103">在 SMO 中，觸發程序是利用 <xref:Microsoft.SqlServer.Management.Smo.Trigger> 物件表示。</span><span class="sxs-lookup"><span data-stu-id="9571a-103">In SMO, triggers are represented by using the <xref:Microsoft.SqlServer.Management.Smo.Trigger> object.</span></span> <span data-ttu-id="9571a-104">[!INCLUDE[tsql](../../../includes/tsql-md.md)]引發觸發程式時所執行的程式碼是由 <xref:Microsoft.SqlServer.Management.Smo.Trigger.TextBody%2A> trigger 物件的屬性所設定。</span><span class="sxs-lookup"><span data-stu-id="9571a-104">The [!INCLUDE[tsql](../../../includes/tsql-md.md)] code that runs when the trigger that is fired is set by the <xref:Microsoft.SqlServer.Management.Smo.Trigger.TextBody%2A> property of the Trigger object.</span></span> <span data-ttu-id="9571a-105">觸發程序的類型是利用 <xref:Microsoft.SqlServer.Management.Smo.Trigger> 物件的其他屬性所設定，例如 <xref:Microsoft.SqlServer.Management.Smo.Trigger.Update%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="9571a-105">The type of trigger is set by using other properties of the <xref:Microsoft.SqlServer.Management.Smo.Trigger> object, such as the <xref:Microsoft.SqlServer.Management.Smo.Trigger.Update%2A> property.</span></span> <span data-ttu-id="9571a-106">這是布林值屬性，指定觸發程序是否由記錄的 `UPDATE` 在父資料表上引發。</span><span class="sxs-lookup"><span data-stu-id="9571a-106">This is a Boolean property that specifies whether the trigger is fired by an `UPDATE` of records on the parent table.</span></span>  
  
 <span data-ttu-id="9571a-107"><xref:Microsoft.SqlServer.Management.Smo.Trigger> 物件代表傳統的資料操作語言 (DML) 觸發程式。</span><span class="sxs-lookup"><span data-stu-id="9571a-107">The <xref:Microsoft.SqlServer.Management.Smo.Trigger> object represents traditional, data manipulation language (DML) triggers.</span></span> <span data-ttu-id="9571a-108">[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 和更新版本也支援資料定義語言 (DDL) 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="9571a-108">In [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] and later versions, data definition language (DDL) triggers are also supported.</span></span> <span data-ttu-id="9571a-109">DDL 觸發程序是由 <xref:Microsoft.SqlServer.Management.Smo.DatabaseDdlTrigger> 物件和 <xref:Microsoft.SqlServer.Management.Smo.ServerDdlTrigger> 物件表示。</span><span class="sxs-lookup"><span data-stu-id="9571a-109">DDL triggers are represented by the <xref:Microsoft.SqlServer.Management.Smo.DatabaseDdlTrigger> object and the <xref:Microsoft.SqlServer.Management.Smo.ServerDdlTrigger> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9571a-110">範例</span><span class="sxs-lookup"><span data-stu-id="9571a-110">Example</span></span>  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="creating-altering-and-removing-a-trigger-in-visual-basic"></a><span data-ttu-id="9571a-111">在 Visual Basic 中建立、改變和移除觸發程序</span><span class="sxs-lookup"><span data-stu-id="9571a-111">Creating, Altering, and Removing a Trigger in Visual Basic</span></span>  
 <span data-ttu-id="9571a-112">此程式碼範例示範如何在 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 資料庫中名為 `Sales` 的現有資料表上，建立及插入更新觸發程序。</span><span class="sxs-lookup"><span data-stu-id="9571a-112">This code example shows how to create and insert an update trigger on an existing table, named `Sales`, in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="9571a-113">此觸發程序會在資料表更新或新記錄插入時傳送提醒訊息。</span><span class="sxs-lookup"><span data-stu-id="9571a-113">The trigger sends a reminder message when the table is updated or a new record is inserted.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBTriggers1](SMO How to#SMO_VBTriggers1)]  -->  
  
## <a name="creating-altering-and-removing-a-trigger-in-visual-c"></a><span data-ttu-id="9571a-114">在 Visual C# 中建立、改變和移除觸發程序</span><span class="sxs-lookup"><span data-stu-id="9571a-114">Creating, Altering, and Removing a Trigger in Visual C#</span></span>  
 <span data-ttu-id="9571a-115">此程式碼範例示範如何在 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 資料庫中名為 `Sales` 的現有資料表上，建立及插入更新觸發程序。</span><span class="sxs-lookup"><span data-stu-id="9571a-115">This code example shows how to create and insert an update trigger on an existing table, named `Sales`, in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="9571a-116">此觸發程序會在資料表更新或新記錄插入時傳送提醒訊息。</span><span class="sxs-lookup"><span data-stu-id="9571a-116">The trigger sends a reminder message when the table is updated or a new record is inserted.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            Server mysrv;  
            mysrv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database mydb;  
            mydb = mysrv.Databases["AdventureWorks2012"];  
            //Declare a Table object variable and reference the Customer table.   
            Table mytab;  
            mytab = mydb.Tables["Customer", "Sales"];  
            //Define a Trigger object variable by supplying the parent table, schema ,and name in the constructor.   
            Trigger tr;  
            tr = new Trigger(mytab, "Sales");  
            //Set TextMode property to False, then set other properties to define the trigger.   
            tr.TextMode = false;  
            tr.Insert = true;  
            tr.Update = true;  
            tr.InsertOrder = ActivationOrder.First;  
            string stmt;  
            stmt = " RAISERROR('Notify Customer Relations',16,10) ";  
            tr.TextBody = stmt;  
            tr.ImplementationType = ImplementationType.TransactSql;  
            //Create the trigger on the instance of SQL Server.   
            tr.Create();  
            //Remove the trigger.   
            tr.Drop();  
        }  
```  
  
## <a name="creating-altering-and-removing-a-trigger-in-powershell"></a><span data-ttu-id="9571a-117">在 PowerShell 中建立、改變和移除觸發程序</span><span class="sxs-lookup"><span data-stu-id="9571a-117">Creating, Altering, and Removing a Trigger in PowerShell</span></span>  
 <span data-ttu-id="9571a-118">此程式碼範例示範如何在 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 資料庫中名為 `Sales` 的現有資料表上，建立及插入更新觸發程序。</span><span class="sxs-lookup"><span data-stu-id="9571a-118">This code example shows how to create and insert an update trigger on an existing table, named `Sales`, in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="9571a-119">此觸發程序會在資料表更新或新記錄插入時傳送提醒訊息。</span><span class="sxs-lookup"><span data-stu-id="9571a-119">The trigger sends a reminder message when the table is updated or a new record is inserted.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server and to the  
#database tables in Adventureworks2012  
CD \sql\localhost\default\databases\AdventureWorks2012\Tables\  
  
#Get reference to the trigger's target table  
$mytab = Get-Item Sales.Customer  
  
# Define a Trigger object variable by supplying the parent table, schema ,and name in the constructor.  
$tr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Trigger -argumentlist $mytab, "Sales"  
  
# Set TextMode property to False, then set other properties to define the trigger.
$tr.TextMode = $false  
$tr.Insert = $true  
$tr.Update = $true  
$tr.InsertOrder = [Microsoft.SqlServer.Management.SMO.Agent.ActivationOrder]::First  
$tr.TextBody = " RAISERROR('Notify Customer Relations',16,10) "  
$tr.ImplementationType = [Microsoft.SqlServer.Management.SMO.ImplementationType]::TransactSql  
  
# Create the trigger on the instance of SQL Server.
$tr.Create()  
  
#Remove the trigger.
$tr.Drop()  
```  
