---
title: 建立、改變和移除使用者定義函數 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- user-defined functions [SMO]
ms.assetid: 0ebebd3b-0775-41c2-989d-aa4cf81af12a
author: stevestein
ms.author: sstein
ms.openlocfilehash: b9ff6d1b6e675d41e96f26fc24e6e0dd4ba69454
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606182"
---
# <a name="creating-altering-and-removing-user-defined-functions"></a><span data-ttu-id="1a606-102">建立、改變和移除使用者定義函數</span><span class="sxs-lookup"><span data-stu-id="1a606-102">Creating, Altering, and Removing User-Defined Functions</span></span>
  <span data-ttu-id="1a606-103"><xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction>物件所提供的功能，可讓使用者以程式設計方式管理中的使用者定義函數 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1a606-103">The <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> object provides functionality that lets users programmatically manage user-defined functions in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1a606-104">使用者定義函數支援輸入和輸出參數，也支援資料表資料行的直接參考。</span><span class="sxs-lookup"><span data-stu-id="1a606-104">User-defined functions support input and output parameters, and also support direct references to table columns.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="1a606-105">需要先在資料庫內註冊組件，然後才能在預存程序、使用者定義函數、觸發程序和使用者定義資料類型中使用組件。</span><span class="sxs-lookup"><span data-stu-id="1a606-105">requires assemblies to be registered within a database before these can be used inside stored procedures, user defined functions, triggers, and user defined data types.</span></span> <span data-ttu-id="1a606-106">SMO 以 <xref:Microsoft.SqlServer.Management.Smo.SqlAssembly> 物件支援此功能。</span><span class="sxs-lookup"><span data-stu-id="1a606-106">SMO supports this feature with the <xref:Microsoft.SqlServer.Management.Smo.SqlAssembly> object.</span></span>  
  
 <span data-ttu-id="1a606-107"><xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> 物件會以 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.AssemblyName%2A>、<xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.ClassName%2A> 和 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.MethodName%2A> 屬性參考 .NET 組件。</span><span class="sxs-lookup"><span data-stu-id="1a606-107">The <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> object references the .NET assembly with the <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.AssemblyName%2A>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.ClassName%2A>, and <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.MethodName%2A> properties.</span></span>  
  
 <span data-ttu-id="1a606-108">當 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> 物件參考 .NET 組件時，您必須藉由建立 <xref:Microsoft.SqlServer.Management.Smo.SqlAssembly> 物件並將其加入至 <xref:Microsoft.SqlServer.Management.Smo.SqlAssemblyCollection> 物件 (後者屬於 <xref:Microsoft.SqlServer.Management.Smo.Database> 物件) 來註冊該組件。</span><span class="sxs-lookup"><span data-stu-id="1a606-108">When the <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> object references a .NET assembly, you must register the assembly by creating a <xref:Microsoft.SqlServer.Management.Smo.SqlAssembly> object and adding it to the <xref:Microsoft.SqlServer.Management.Smo.SqlAssemblyCollection> object, which belongs to the <xref:Microsoft.SqlServer.Management.Smo.Database> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a606-109">範例</span><span class="sxs-lookup"><span data-stu-id="1a606-109">Example</span></span>  
 <span data-ttu-id="1a606-110">如果要使用所提供的任何程式碼範例，您必須選擇建立應用程式用的程式設計環境、程式設計範本，及程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="1a606-110">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="1a606-111">如需詳細資訊，請參閱[在 Visual Studio .net 中建立 VISUAL BASIC SMO 專案](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)或[在 Visual Studio .Net 中建立 VISUAL C&#35; SMO 專案](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="1a606-111">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-a-scalar-user-defined-function-in-visual-basic"></a><span data-ttu-id="1a606-112">在 Visual Basic 中建立純量使用者定義函數</span><span class="sxs-lookup"><span data-stu-id="1a606-112">Creating a Scalar User-Defined Function in Visual Basic</span></span>  
 <span data-ttu-id="1a606-113">這個程式碼範例示範如何在 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 中，建立及移除具有輸入 <xref:System.DateTime> 物件參數和整數傳回類型的純量使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="1a606-113">This code example shows how to create and remove a scalar user-defined function that has an input <xref:System.DateTime> object parameter and an integer return type in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)].</span></span> <span data-ttu-id="1a606-114">使用者定義函數會建立在 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 資料庫上。</span><span class="sxs-lookup"><span data-stu-id="1a606-114">The user-defined function is created on the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="1a606-115">此範例會建立使用者定義函數 ISOweek，該函數取用日期引數並計算 ISO 週數。</span><span class="sxs-lookup"><span data-stu-id="1a606-115">The example creates a user-defined function, ISOweek, which takes a date argument and calculates the ISO week number.</span></span> <span data-ttu-id="1a606-116">為了讓這個函數能夠正確計算，必須先將資料庫 DATEFIRST 選項設定為 1，才能呼叫該函數。</span><span class="sxs-lookup"><span data-stu-id="1a606-116">For this function to calculate correctly, the database DATEFIRST option must be set to 1 before the function is called.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBUserDefFuncs1](SMO How to#SMO_VBUserDefFuncs1)]  -->  
  
## <a name="creating-a-scalar-user-defined-function-in-visual-c"></a><span data-ttu-id="1a606-117">在 Visual C# 中建立純量使用者定義函數</span><span class="sxs-lookup"><span data-stu-id="1a606-117">Creating a Scalar User-Defined Function in Visual C#</span></span>  
 <span data-ttu-id="1a606-118">這個程式碼範例示範如何在 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] 中，建立及移除具有輸入 <xref:System.DateTime> 物件參數和整數傳回類型的純量使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="1a606-118">This code example shows how to create and remove a scalar user-defined function that has an input <xref:System.DateTime> object parameter and an integer return type in [!INCLUDE[csprcs](../../../includes/csprcs-md.md)].</span></span> <span data-ttu-id="1a606-119">使用者定義函數會建立在 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 資料庫上。</span><span class="sxs-lookup"><span data-stu-id="1a606-119">The user-defined function is created on the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="1a606-120">本範例會建立使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="1a606-120">The example creates the user-defined function.</span></span> <span data-ttu-id="1a606-121">`ISOweek`.</span><span class="sxs-lookup"><span data-stu-id="1a606-121">`ISOweek`.</span></span> <span data-ttu-id="1a606-122">這個函數採用日期引數並計算 ISO 週數。</span><span class="sxs-lookup"><span data-stu-id="1a606-122">This function takes a date argument and calculates the ISO week number.</span></span> <span data-ttu-id="1a606-123">為了讓這個函數能夠正確計算，必須先將資料庫 `DATEFIRST` 選項設定為 `1` ，才能呼叫該函數。</span><span class="sxs-lookup"><span data-stu-id="1a606-123">For this function to calculate correctly, the database `DATEFIRST` option must be set to `1` before the function is called.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
           Server srv = new Server();  
            //Reference the AdventureWorks2012 database.   
           Database db = srv.Databases["AdventureWorks2012"];  
  
            //Define a UserDefinedFunction object variable by supplying the parent database and the name arguments in the constructor.   
            UserDefinedFunction udf = new UserDefinedFunction(db, "IsOWeek");  
  
            //Set the TextMode property to false and then set the other properties.   
            udf.TextMode = false;  
            udf.DataType = DataType.Int;  
            udf.ExecutionContext = ExecutionContext.Caller;  
            udf.FunctionType = UserDefinedFunctionType.Scalar;  
            udf.ImplementationType = ImplementationType.TransactSql;  
  
            //Add a parameter.   
  
     UserDefinedFunctionParameter par = new UserDefinedFunctionParameter(udf, "@DATE", DataType.DateTime);  
            udf.Parameters.Add(par);  
  
            //Set the TextBody property to define the user-defined function.   
            udf.TextBody = "BEGIN DECLARE @ISOweek int SET @ISOweek= DATEPART(wk,@DATE)+1 -DATEPART(wk,CAST(DATEPART(yy,@DATE) as CHAR(4))+'0104') IF (@ISOweek=0) SET @ISOweek=dbo.ISOweek(CAST(DATEPART(yy,@DATE)-1 AS CHAR(4))+'12'+ CAST(24+DATEPART(DAY,@DATE) AS CHAR(2)))+1 IF ((DATEPART(mm,@DATE)=12) AND ((DATEPART(dd,@DATE)-DATEPART(dw,@DATE))>= 28)) SET @ISOweek=1 RETURN(@ISOweek) END;";  
  
            //Create the user-defined function on the instance of SQL Server.   
            udf.Create();  
  
            //Remove the user-defined function.   
            udf.Drop();  
        }  
```  
  
## <a name="creating-a-scalar-user-defined-function-in-powershell"></a><span data-ttu-id="1a606-124">在 PowerShell 中建立純量使用者定義函數</span><span class="sxs-lookup"><span data-stu-id="1a606-124">Creating a Scalar User-Defined Function in PowerShell</span></span>  
 <span data-ttu-id="1a606-125">這個程式碼範例示範如何在 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] 中，建立及移除具有輸入 <xref:System.DateTime> 物件參數和整數傳回類型的純量使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="1a606-125">This code example shows how to create and remove a scalar user-defined function that has an input <xref:System.DateTime> object parameter and an integer return type in [!INCLUDE[csprcs](../../../includes/csprcs-md.md)].</span></span> <span data-ttu-id="1a606-126">使用者定義函數會建立在 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] 資料庫上。</span><span class="sxs-lookup"><span data-stu-id="1a606-126">The user-defined function is created on the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="1a606-127">本範例會建立使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="1a606-127">The example creates the user-defined function.</span></span> <span data-ttu-id="1a606-128">`ISOweek`.</span><span class="sxs-lookup"><span data-stu-id="1a606-128">`ISOweek`.</span></span> <span data-ttu-id="1a606-129">這個函數採用日期引數並計算 ISO 週數。</span><span class="sxs-lookup"><span data-stu-id="1a606-129">This function takes a date argument and calculates the ISO week number.</span></span> <span data-ttu-id="1a606-130">為了讓這個函數能夠正確計算，必須先將資料庫 `DATEFIRST` 選項設定為 `1` ，才能呼叫該函數。</span><span class="sxs-lookup"><span data-stu-id="1a606-130">For this function to calculate correctly, the database `DATEFIRST` option must be set to `1` before the function is called.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = Get-Item Adventureworks2012  
  
# Define a user defined function object variable by supplying the parent database and name arguments in the constructor.
$udf  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedFunction -argumentlist $db, "IsOWeek"  
  
# Set the TextMode property to false and then set the other properties.
$udf.TextMode = $false  
$udf.DataType = [Microsoft.SqlServer.Management.SMO.DataType]::Int
$udf.ExecutionContext = [Microsoft.SqlServer.Management.SMO.ExecutionContext]::Caller  
$udf.FunctionType = [Microsoft.SqlServer.Management.SMO.UserDefinedFunctionType]::Scalar  
$udf.ImplementationType = [Microsoft.SqlServer.Management.SMO.ImplementationType]::TransactSql  
  
# Define a Parameter object variable by supplying the parent function, name and type arguments in the constructor.  
$type = [Microsoft.SqlServer.Management.SMO.DataType]::DateTime  
$par  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedFunctionParameter -argumentlist $udf, "@DATE",$type  
  
# Add the parameter to the function  
$udf.Parameters.Add($par)  
  
#Set the TextBody property to define the user-defined function.
$udf.TextBody = "BEGIN DECLARE @ISOweek int SET @ISOweek= DATEPART(wk,@DATE)+1 -DATEPART(wk,CAST(DATEPART(yy,@DATE) as CHAR(4))+'0104') IF (@ISOweek=0) SET @ISOweek=dbo.ISOweek(CAST(DATEPART(yy,@DATE)-1 AS CHAR(4))+'12'+ CAST(24+DATEPART(DAY,@DATE) AS CHAR(2)))+1 IF ((DATEPART(mm,@DATE)=12) AND ((DATEPART(dd,@DATE)-DATEPART(dw,@DATE))>= 28)) SET @ISOweek=1 RETURN(@ISOweek) END;"  
  
# Create the user-defined function on the instance of SQL Server.
$udf.Create()  
  
# Remove the user-defined function.
$udf.Drop()  
```  
  
## <a name="see-also"></a><span data-ttu-id="1a606-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a606-131">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction>  
