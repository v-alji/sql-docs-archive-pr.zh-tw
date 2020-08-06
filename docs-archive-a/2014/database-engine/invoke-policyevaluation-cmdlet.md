---
title: Invoke-PolicyEvaluation Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, Invoke-PolicyEvaluation
- Policy-Based Management, PowerShell
- Invoke-PolicyEvaluation cmdlet
- Cmdlets [SQL Server], Invoke-PolicyEvaluation
- PowerShell [SQL Server], Invoke-PolicyEvaluation
ms.assetid: 3e6d4f5a-59b7-4203-b95a-f7e692c0f131
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 656fdffea191c9cf6fc42d860164bc5af1e04561
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698509"
---
# <a name="invoke-policyevaluation-cmdlet"></a><span data-ttu-id="35a4b-102">Invoke-PolicyEvaluation 指令程式</span><span class="sxs-lookup"><span data-stu-id="35a4b-102">Invoke-PolicyEvaluation cmdlet</span></span>
  <span data-ttu-id="35a4b-103">**Invoke-PolicyEvaluation** 是一項 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Cmdlet，它會報告 SQL Server 物件的目標集是否符合在一或多個原則式管理原則中所指定的條件。</span><span class="sxs-lookup"><span data-stu-id="35a4b-103">**Invoke-PolicyEvaluation** is a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlet that reports whether a target set of SQL Server objects complies with the conditions specified in one or more Policy-Based Management policies.</span></span>  
  
## <a name="using-invoke-policyevaluation"></a><span data-ttu-id="35a4b-104">使用 Invoke-PolicyEvaluation</span><span class="sxs-lookup"><span data-stu-id="35a4b-104">Using Invoke-PolicyEvaluation</span></span>  
 <span data-ttu-id="35a4b-105">**Invoke-PolicyEvaluation** 會針對稱為目標集的一組 SQL Server 物件評估一或多個原則。</span><span class="sxs-lookup"><span data-stu-id="35a4b-105">**Invoke-PolicyEvaluation** evaluates one or more policies against a set of SQL Server objects called the target set.</span></span> <span data-ttu-id="35a4b-106">目標物件集來自目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="35a4b-106">The set of target objects comes from a target server.</span></span> <span data-ttu-id="35a4b-107">每個原則都會定義一些條件，而它們就是目標物件所允許的狀態。</span><span class="sxs-lookup"><span data-stu-id="35a4b-107">Each policy defines conditions, which are the allowed states for the target objects.</span></span> <span data-ttu-id="35a4b-108">例如， **可信任的資料庫** 原則表示 TRUSTWORTHY 資料庫屬性必須設定為 OFF。</span><span class="sxs-lookup"><span data-stu-id="35a4b-108">For example, the **Trustworthy Database** policy states that the TRUSTWORTHY database property must be set to OFF.</span></span>  
  
 <span data-ttu-id="35a4b-109">**-AdHocPolicyEvaluationMode** 參數會指定採取的動作：</span><span class="sxs-lookup"><span data-stu-id="35a4b-109">The **-AdHocPolicyEvaluationMode** parameter specifies the actions taken:</span></span>  
  
 <span data-ttu-id="35a4b-110">勾選</span><span class="sxs-lookup"><span data-stu-id="35a4b-110">Check</span></span>  
 <span data-ttu-id="35a4b-111">使用目前登入的認證來報告目標物件的符合狀態。</span><span class="sxs-lookup"><span data-stu-id="35a4b-111">Report the compliance status of the target objects using the credentials of your current login.</span></span> <span data-ttu-id="35a4b-112">請勿重新設定任何物件。</span><span class="sxs-lookup"><span data-stu-id="35a4b-112">Do no reconfigure any objects.</span></span> <span data-ttu-id="35a4b-113">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="35a4b-113">This is the default setting.</span></span>  
  
 <span data-ttu-id="35a4b-114">CheckSqlScriptAsProxy</span><span class="sxs-lookup"><span data-stu-id="35a4b-114">CheckSqlScriptAsProxy</span></span>  
 <span data-ttu-id="35a4b-115">使用 **##MS_PolicyTSQLExecutionLogin##** Proxy 登入的認證來報告目標物件的符合狀態。</span><span class="sxs-lookup"><span data-stu-id="35a4b-115">Report the compliance status of the target objects using the credentials of the **##MS_PolicyTSQLExecutionLogin##** proxy login.</span></span> <span data-ttu-id="35a4b-116">請勿重新設定任何物件。</span><span class="sxs-lookup"><span data-stu-id="35a4b-116">Do no reconfigure any objects.</span></span>  
  
 <span data-ttu-id="35a4b-117">設定</span><span class="sxs-lookup"><span data-stu-id="35a4b-117">Configure</span></span>  
 <span data-ttu-id="35a4b-118">使用目前登入的認證來報告目標物件的符合狀態。</span><span class="sxs-lookup"><span data-stu-id="35a4b-118">Report the compliance status of the target objects using the credentials of your current login.</span></span> <span data-ttu-id="35a4b-119">請重新設定任何不符合原則的可設定且具決定性選項。</span><span class="sxs-lookup"><span data-stu-id="35a4b-119">Reconfigure any settable and deterministic options that are not in compliance with the policies.</span></span>  
  
## <a name="specifying-polices"></a><span data-ttu-id="35a4b-120">指定原則</span><span class="sxs-lookup"><span data-stu-id="35a4b-120">Specifying Polices</span></span>  
 <span data-ttu-id="35a4b-121">指定原則的方式會取決於儲存原則的位置。</span><span class="sxs-lookup"><span data-stu-id="35a4b-121">How you specify a policy depends on where the policy is stored.</span></span> <span data-ttu-id="35a4b-122">您可以使用兩種格式來儲存原則：</span><span class="sxs-lookup"><span data-stu-id="35a4b-122">Policies can be stored in two formats:</span></span>  
  
-   <span data-ttu-id="35a4b-123">原則可以是儲存在原則存放區中的物件，例如 Database Engine 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="35a4b-123">They can be objects stored in a policy store, such as an instance of the Database Engine.</span></span> <span data-ttu-id="35a4b-124">您可以使用 SQLSERVER:\SQLPolicy 資料夾來指定原則存放區中的原則位置。</span><span class="sxs-lookup"><span data-stu-id="35a4b-124">You can use the SQLSERVER:\SQLPolicy folder to specify the location of policies in a policy store.</span></span> <span data-ttu-id="35a4b-125">您可以使用 Windows PowerShell 指令程式來根據屬性篩選輸入原則，例如使用 Where-Object 來依據原則類別目錄篩選，或使用 Get-Item 來依據原則名稱篩選。</span><span class="sxs-lookup"><span data-stu-id="35a4b-125">You can use Windows PowerShell cmdlets to filter the input polices based on their properties, such as using Where-Object to filter on the policy category or Get-Item to filter on policy name.</span></span>  
  
-   <span data-ttu-id="35a4b-126">原則可以匯出成 XML 檔。</span><span class="sxs-lookup"><span data-stu-id="35a4b-126">They can be exported as XML files.</span></span> <span data-ttu-id="35a4b-127">您可以使用檔案系統磁碟機 (例如 D:) 來指定 XML 檔的位置。</span><span class="sxs-lookup"><span data-stu-id="35a4b-127">You can use a file system drive, such as D:, to specify the location of the XML files.</span></span> <span data-ttu-id="35a4b-128">您可以使用 Where-Object 等 Windows PowerShell 指令程式來依據檔案屬性 (例如檔案名稱) 篩選原則。</span><span class="sxs-lookup"><span data-stu-id="35a4b-128">You can use Windows PowerShell cmdlets such as Where-Object to filter the policies on their file properties, such as file name.</span></span>  
  
 <span data-ttu-id="35a4b-129">如果原則儲存在原則存放區中，您就必須傳入一組指向要評估之原則的 PSObjects。</span><span class="sxs-lookup"><span data-stu-id="35a4b-129">If the policies are stored in a policy store, you must pass in a set of PSObjects pointing to the policies to be evaluated.</span></span> <span data-ttu-id="35a4b-130">您通常可以透過將 Get-Item 等 Cmdlet 的輸出傳送至 **Invoke-PolicyEvaluation**完成此作業，而且不需要指定 **-Policy** 參數。</span><span class="sxs-lookup"><span data-stu-id="35a4b-130">This is typically done by piping the output of a cmdlet such as Get-Item to **Invoke-PolicyEvaluation**, and does not require that you specify the **-Policy** parameter.</span></span> <span data-ttu-id="35a4b-131">例如，如果您已將 Microsoft 最佳作法原則匯入 Database Engine 的執行個體中，這個命令就會評估 **資料庫狀態** 原則：</span><span class="sxs-lookup"><span data-stu-id="35a4b-131">For example, if you have imported the Microsoft Best Practices policies into your instance of the database engine, this command evaluates the **Database Status** policy:</span></span>  
  
```powershell
sl "SQLSERVER:\SQLPolicy\MyComputer\DEFAULT\Policies"  
Get-Item "Database Status" | Invoke-PolicyEvaluation -TargetServerName "MYCOMPUTER"  
```  
  
 <span data-ttu-id="35a4b-132">這則範例會示範如何使用 Where-Object 來根據 **PolicyCategory** 屬性篩選原則存放區中的多個原則。</span><span class="sxs-lookup"><span data-stu-id="35a4b-132">This example shows using Where-Object to filter multiple policies from a policy store based on their **PolicyCategory** property.</span></span> <span data-ttu-id="35a4b-133">**Invoke-PolicyEvaluation** 會取用 **Where-Object**傳送輸出的物件。</span><span class="sxs-lookup"><span data-stu-id="35a4b-133">The objects from the piped output of **Where-Object** is consumed by **Invoke-PolicyEvaluation**.</span></span>  
  
```powershell
sl "SQLSERVER:\SQLPolicy\MyComputer\DEFAULT\Policies"  
gci | Where-Object {$_.PolicyCategory -eq "Microsoft Best Practices: Maintenance"} | Invoke-PolicyEvaluation -TargetServer "MYCOMPUTER"  
```  
  
 <span data-ttu-id="35a4b-134">如果原則儲存成 XML 檔，您就必須使用 **-Policy** 參數來提供每個原則的路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="35a4b-134">If the policies are stored as XML files, you must use the **-Policy** parameter to supply both the path and name for each policy.</span></span> <span data-ttu-id="35a4b-135">如果您沒有在 **-Policy** 參數中指定路徑， **Invoke-PolicyEvaulation** 就會使用 **sqlps** 路徑的目前設定。</span><span class="sxs-lookup"><span data-stu-id="35a4b-135">If you do not specify a path in the **-Policy** parameter, **Invoke-PolicyEvaulation** uses the current setting of the **sqlps** path.</span></span> <span data-ttu-id="35a4b-136">例如，這個命令會針對您登入的預設資料庫評估與 SQL Server 一起安裝的其中一個 Microsoft 最佳作法原則：</span><span class="sxs-lookup"><span data-stu-id="35a4b-136">For example, this command evaluates one of the Microsoft Best Practice policies installed with SQL Server against the default database for your login:</span></span>  
  
```powershell
Invoke-PolicyEvaluation -Policy "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033\Database Status.xml" -TargetServerName "MYCOMPUTER"  
```  
  
 <span data-ttu-id="35a4b-137">這個命令會進行相同的作業，但是它會使用目前的 **sqlps** 路徑來建立原則 XML 檔的位置：</span><span class="sxs-lookup"><span data-stu-id="35a4b-137">This command does the same thing, only it uses the current **sqlps** path to establish the location of the policy XML file:</span></span>  
  
```powershell
sl "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033"  
Invoke-PolicyEvaluation -Policy "Database Status.xml" -TargetServerName "MYCOMPUTER"  
```  
  
 <span data-ttu-id="35a4b-138">此範例將示範如何使用 **Get-ChildItem** Cmdlet 擷取多個原則 XML 檔，然後將這些物件傳送至 **Invoke-PolicyEvaluation**中：</span><span class="sxs-lookup"><span data-stu-id="35a4b-138">This example shows using the **Get-ChildItem** cmdlet to retrieve multiple policy XML files and pipe the objects into **Invoke-PolicyEvaluation**:</span></span>  
  
```powershell
sl "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033"  
gci "Database Status.xml", "Trustworthy Database.xml" | Invoke-PolicyEvaluation -TargetServer "MYCOMPUTER"  
```  
  
## <a name="specifying-the-target-set"></a><span data-ttu-id="35a4b-139">指定目標集</span><span class="sxs-lookup"><span data-stu-id="35a4b-139">Specifying the Target Set</span></span>  
 <span data-ttu-id="35a4b-140">您可以使用三種參數來指定目標物件集：</span><span class="sxs-lookup"><span data-stu-id="35a4b-140">Use three parameters to specify the set of target objects:</span></span>  
  
-   <span data-ttu-id="35a4b-141">**-TargetServerName** 會指定包含目標物件的 SQL Server 執行個體。</span><span class="sxs-lookup"><span data-stu-id="35a4b-141">**-TargetServerName** specifies the instance of SQL Server containing the target objects.</span></span> <span data-ttu-id="35a4b-142">您可以在使用針對 <xref:System.Data.SqlClient.SqlConnection> 類別之 ConnectionString 屬性所定義格式的字串中指定這項資訊。</span><span class="sxs-lookup"><span data-stu-id="35a4b-142">You can specify the information in a string that uses the format defined for the ConnectionString property of the <xref:System.Data.SqlClient.SqlConnection> class.</span></span> <span data-ttu-id="35a4b-143">您可以使用 <xref:System.Data.SqlClient.SqlConnectionStringBuilder> 類別來建立格式正確的連接字串。</span><span class="sxs-lookup"><span data-stu-id="35a4b-143">You can use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> class to build a correctly formatted connection string.</span></span> <span data-ttu-id="35a4b-144">您也可以建立 <xref:Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection> 物件，並將它傳遞給 **-TargetServer**傳送輸出的物件。</span><span class="sxs-lookup"><span data-stu-id="35a4b-144">You can also create a <xref:Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection> object and pass it to **-TargetServer**.</span></span> <span data-ttu-id="35a4b-145">如果您提供只有伺服器名稱的字串， **Invoke-PolicyEvaluation** 就會使用 Windows 驗證來連接至伺服器。</span><span class="sxs-lookup"><span data-stu-id="35a4b-145">If you supply a string that has only the name of the server, **Invoke-PolicyEvaluation** uses Windows Authentication to connect to the server.</span></span>  
  
-   <span data-ttu-id="35a4b-146">**-TargetObjects** 會使用在目標集中代表 SQL Server 物件的物件或物件陣列。</span><span class="sxs-lookup"><span data-stu-id="35a4b-146">**-TargetObjects** takes an object or array of objects that represent the SQL Server objects in the target set.</span></span> <span data-ttu-id="35a4b-147">例如，您可以建立要傳入 <xref:Microsoft.SqlServer.Management.Smo.Database> 的 **-TargetObjects**傳送輸出的物件。</span><span class="sxs-lookup"><span data-stu-id="35a4b-147">For example, you could create an array of <xref:Microsoft.SqlServer.Management.Smo.Database> class objects to pass in to **-TargetObjects**.</span></span>  
  
-   <span data-ttu-id="35a4b-148">**-TargetExpressions** 會使用字串，其中包含在目標集中指定物件的查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="35a4b-148">**-TargetExpressions** takes a string containing a query expression that specifies the objects in the target set.</span></span> <span data-ttu-id="35a4b-149">查詢運算式的格式為以 '/' 字元分隔的節點。</span><span class="sxs-lookup"><span data-stu-id="35a4b-149">The query expression is in the form of nodes separated by the '/' character.</span></span> <span data-ttu-id="35a4b-150">每個節點的格式為 ObjectType[Filter]。</span><span class="sxs-lookup"><span data-stu-id="35a4b-150">Each node is in the form ObjectType[Filter].</span></span> <span data-ttu-id="35a4b-151">物件類型是 SQL Server 管理物件中的其中一個物件， (SMO) 物件階層。</span><span class="sxs-lookup"><span data-stu-id="35a4b-151">Object type is one of the objects in a SQL Server Management Object (SMO) object hierarchy.</span></span> <span data-ttu-id="35a4b-152">篩選是篩選位於該節點之物件的運算式。</span><span class="sxs-lookup"><span data-stu-id="35a4b-152">Filter is an expression that filters for objects at that node.</span></span> <span data-ttu-id="35a4b-153">如需詳細資訊，請參閱 [Query Expressions and Uniform Resource Names](../powershell/query-expressions-and-uniform-resource-names.md)。</span><span class="sxs-lookup"><span data-stu-id="35a4b-153">For more information, see [Query Expressions and Uniform Resource Names](../powershell/query-expressions-and-uniform-resource-names.md).</span></span>  
  
 <span data-ttu-id="35a4b-154">請指定 **-TargetObjects** 或 **-TargetExpression**，但不能同時指定。</span><span class="sxs-lookup"><span data-stu-id="35a4b-154">Specify either **-TargetObjects** or **-TargetExpression**, not both.</span></span>  
  
 <span data-ttu-id="35a4b-155">這則範例會使用 Sfc.SqlStoreConnection 物件來指定目標伺服器：</span><span class="sxs-lookup"><span data-stu-id="35a4b-155">This example uses an Sfc.SqlStoreConnection object to specify the target server:</span></span>  
  
```powershell
sl "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033"  
$conn = New-Object Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection("server='MYCOMPUTER';Trusted_Connection=True")  
Invoke-PolicyEvaluation -Policy "Database Status.xml" -TargetServerName $conn  
```  
  
 <span data-ttu-id="35a4b-156">此範例會使用 **-TargetExpression** 來識別要評估的特定資料庫：</span><span class="sxs-lookup"><span data-stu-id="35a4b-156">This example uses **-TargetExpression** to identify the specific database to evaluate:</span></span>  
  
```powershell
sl "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033"  
Invoke-PolicyEvaluation -Policy "Database Status.xml" -TargetServerName "MyComputer" -TargetExpression "Server[@Name='MYCOMPUTER']/Database[@Name='AdventureWorks2012']"  
```  
  
## <a name="evaluating-analysis-services-policies"></a><span data-ttu-id="35a4b-157">評估 Analysis Services 原則</span><span class="sxs-lookup"><span data-stu-id="35a4b-157">Evaluating Analysis Services Policies</span></span>  
 <span data-ttu-id="35a4b-158">若要為 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]的執行個體評估原則，您必須在 PowerShell 中載入並註冊組件、使用 Analysis Services 連接物件建立變數，然後將此變數傳遞給 **-TargetObject** 參數。</span><span class="sxs-lookup"><span data-stu-id="35a4b-158">To evaluate policies against an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], you must load and register an assembly into PowerShell, create a variable with an Analysis Services connection object, and pass the variable to the **-TargetObject** parameter.</span></span> <span data-ttu-id="35a4b-159">此範例將示範如何評估 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]的最佳作法介面區組態原則：</span><span class="sxs-lookup"><span data-stu-id="35a4b-159">This example shows evaluating the Best Practices surface area configuration policy for [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]:</span></span>  
  
```powershell
sl "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\AnalysisServices\1033"  
[System.Reflection.Assembly]::LoadWithPartialName("Microsoft.AnalysisServices")  
$SSASsvr = New-Object Microsoft.AnalysisServices.Server  
$SSASsvr.Connect("Data Source=Localhost")  
Invoke-PolicyEvaluation -Policy "Surface Area Configuration for Analysis Services Features.xml" -TargetObject $SSASsvr  
```  
  
## <a name="evaluating-reporting-services-policies"></a><span data-ttu-id="35a4b-160">評估 Reporting Services 原則</span><span class="sxs-lookup"><span data-stu-id="35a4b-160">Evaluating Reporting Services Policies</span></span>  
 <span data-ttu-id="35a4b-161">若要評估 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 原則，您必須在 PowerShell 中載入並註冊組件、使用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 連接物件建立變數，然後將此變數傳遞給 **-TargetObject** 參數。</span><span class="sxs-lookup"><span data-stu-id="35a4b-161">To evaluate [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] policies, you must load and register an assembly into PowerShell, create a variable with a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] connection object, and pass the variable to the **-TargetObject** parameter.</span></span> <span data-ttu-id="35a4b-162">此範例將示範如何評估 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]的最佳作法介面區組態原則：</span><span class="sxs-lookup"><span data-stu-id="35a4b-162">This example shows evaluating the Best Practices surface area configuration policy for [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]:</span></span>  
  
```powershell
sl "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\ReportingServices\1033"  
[System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.Dmf.Adapters")  
$SSRSsvr = new-object Microsoft.SqlServer.Management.Adapters.RSContainer('MyComputer')  
Invoke-PolicyEvaluation -Policy "Surface Area Configuration for Reporting Services 2008 Features.xml" -TargetObject $SSRSsvr  
```  
  
## <a name="formatting-output"></a><span data-ttu-id="35a4b-163">格式化輸出</span><span class="sxs-lookup"><span data-stu-id="35a4b-163">Formatting Output</span></span>  
 <span data-ttu-id="35a4b-164">根據預設， **Invoke-PolicyEvaluation** 的輸出會在命令提示字元視窗中以使用者可讀取的格式顯示成精簡報表。</span><span class="sxs-lookup"><span data-stu-id="35a4b-164">By default, the output of **Invoke-PolicyEvaluation** is displayed in the command prompt window as a concise report in human-readable format.</span></span> <span data-ttu-id="35a4b-165">您可以使用 **-OutputXML** 參數，指定此 Cmdlet 要改為將詳細的報表產生成 XML 檔。</span><span class="sxs-lookup"><span data-stu-id="35a4b-165">You can use the **-OutputXML** parameter to specify that the cmdlet instead produce a detailed report as an XML file.</span></span> <span data-ttu-id="35a4b-166">**Invoke-PolicyEvaluation** 會使用「系統模組化語言交換格式」(Systems Modeling Language Interchange Format, SML-IF) 結構描述，所以 SML-IF 讀取器可以讀取此檔案。</span><span class="sxs-lookup"><span data-stu-id="35a4b-166">**Invoke-PolicyEvaluation** uses the Systems Modeling Language Interchange Format (SML-IF) schema so the file can be read by SML-IF readers.</span></span>  
  
```powershell
sl "SQLSERVER:\SQLPolicy\MyComputer\DEFAULT\Policies"  
Invoke-PolicyEvaluation -Policy "Datbase Status" -TargetServer "MYCOMPUTER" -OutputXML > C:\MyReports\DatabaseStatusReport.xml  
```  
  
## <a name="see-also"></a><span data-ttu-id="35a4b-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35a4b-167">See Also</span></span>  
 [<span data-ttu-id="35a4b-168">使用 Database Engine Cmdlet</span><span class="sxs-lookup"><span data-stu-id="35a4b-168">Use the Database Engine cmdlets</span></span>](../../2014/database-engine/use-the-database-engine-cmdlets.md)  
