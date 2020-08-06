---
title: 使用 Database Engine Cmdlet | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Cmdlets [SQL Server], Encode-Sqlname
- Encode-Sqlname cmdlet
- PowerShell [SQL Server], Encode-Sqlname
- Convert-UrnToPath cmdlet
- PowerShell [SQL Server], cmdlets
- Cmdlets [SQL Server]
- PowerShell [SQL Server], Convert-UrnToPath
- Cmdlets [SQL Server], Convert-UrnToPath
- Decode-Sqlname cmdlet
- PowerShell [SQL Server], Decode-Sqlname
- Cmdlets [SQL Server], Decode-Sqlname
ms.assetid: 720aa982-09ae-41a3-b603-a91004cfbe3e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 015500c7c985f9f1a1d190954406844f3b184932
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585539"
---
# <a name="use-the-database-engine-cmdlets"></a><span data-ttu-id="62535-102">使用 Database Engine Cmdlet</span><span class="sxs-lookup"><span data-stu-id="62535-102">Use the Database Engine cmdlets</span></span>
  <span data-ttu-id="62535-103">Windows PowerShell Cmdlet 是單一功能的命令，通常具有動詞-名詞命名慣例，例如 **Get-Help** 或 **Set-MachineName**。</span><span class="sxs-lookup"><span data-stu-id="62535-103">Windows PowerShell cmdlets are single-function commands that typically have a verb-noun naming convention, such as **Get-Help** or **Set-MachineName**.</span></span> <span data-ttu-id="62535-104">適用於 Windows PowerShell 的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 提供者會提供 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]特有的指令程式。</span><span class="sxs-lookup"><span data-stu-id="62535-104">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider for Windows PowerShell supplies cmdlets specific to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="database-engine-cmdlets"></a><span data-ttu-id="62535-105">Database Engine 指令程式</span><span class="sxs-lookup"><span data-stu-id="62535-105">Database Engine cmdlets</span></span>  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="62535-106">會實作少數的 [!INCLUDE[ssDE](../includes/ssde-md.md)]Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="62535-106">implements a small number of cmdlets for the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="62535-107">這些指令程式主要是用來從新的 PowerShell 指令碼執行現有的 Transact-SQL 指令碼、評估原則式管理原則，以及協助在 SQL Server 提供者路徑中指定 SQL Server 識別碼。</span><span class="sxs-lookup"><span data-stu-id="62535-107">These cmdlets are primarily used to run existing Transact-SQL scripts from new PowerShell scripts, evaluate policy-based management policies, and aid in specifying SQL Server identifiers in SQL Server Provider paths.</span></span>  
  
 <span data-ttu-id="62535-108">大部分的 Windows PowerShell 指令碼都會使用 SQL Server PowerShell 提供者和 SQL Server 管理能力物件模型，來處理 [!INCLUDE[ssDE](../includes/ssde-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="62535-108">Most Windows PowerShell scripts work with the [!INCLUDE[ssDE](../includes/ssde-md.md)] by using the SQL Server PowerShell provider and the SQL Server manageability object models.</span></span> <span data-ttu-id="62535-109">如需詳細資訊，請參閱 [SQL Server PowerShell](../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="62535-109">For more information, see [SQL Server PowerShell](../powershell/sql-server-powershell.md).</span></span>  
  
### <a name="get-cmdlet-help"></a><span data-ttu-id="62535-110">取得指令程式說明</span><span class="sxs-lookup"><span data-stu-id="62535-110">Get Cmdlet Help</span></span>  
 <span data-ttu-id="62535-111">在 Windows PowerShell 環境中， **Get-Help** Cmdlet 會提供每個 Cmdlet 的說明資訊。</span><span class="sxs-lookup"><span data-stu-id="62535-111">In the Windows PowerShell environment, the **Get-Help** cmdlet provides help information for each cmdlet.</span></span> <span data-ttu-id="62535-112">**Get-Help** 會傳回語法、參數定義、輸入和輸出類型以及 Cmdlet 所執行之動作描述等資訊。</span><span class="sxs-lookup"><span data-stu-id="62535-112">**Get-Help** returns information such as the syntax, parameter definitions, input and output types, and a description of the action performed by the cmdlet.</span></span> <span data-ttu-id="62535-113">如需詳細資訊，請參閱 [Get Help SQL Server PowerShell](../../2014/database-engine/get-help-sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="62535-113">For more information, see [Get Help SQL Server PowerShell](../../2014/database-engine/get-help-sql-server-powershell.md).</span></span>  
  
### <a name="partial-parameter-names"></a><span data-ttu-id="62535-114">部分參數名稱</span><span class="sxs-lookup"><span data-stu-id="62535-114">Partial Parameter Names</span></span>  
 <span data-ttu-id="62535-115">您不需要指定指令程式參數的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="62535-115">You do not have to specify the entire name of a cmdlet parameter.</span></span> <span data-ttu-id="62535-116">您只要指定足夠的名稱，就可以唯一地分隔它與指令程式所支援的其他參數。</span><span class="sxs-lookup"><span data-stu-id="62535-116">You only have to specify enough of the name to uniquely separate it from the other parameters that are supported by the cmdlet.</span></span> <span data-ttu-id="62535-117">例如，下列範例將示範三種指定 **Invoke-Sqlcmd -QueryTimeout** 參數的方式：</span><span class="sxs-lookup"><span data-stu-id="62535-117">For example, these examples show three ways of specifying the **Invoke-Sqlcmd -QueryTimeout** parameter:</span></span>  
  
```powershell
Invoke-Sqlcmd -Query "SELECT @@VERSION;" -QueryTimeout 3  
Invoke-Sqlcmd -Query "SELECT @@VERSION;" -QueryTime 3  
Invoke-Sqlcmd -Query "SELECT @@VERSION;" -QueryT 3  
```  
  
## <a name="database-engine-cmdlet-tasks"></a><span data-ttu-id="62535-118">Database Engine 指令程式工作</span><span class="sxs-lookup"><span data-stu-id="62535-118">Database Engine cmdlet Tasks</span></span>  
  
|<span data-ttu-id="62535-119">工作描述</span><span class="sxs-lookup"><span data-stu-id="62535-119">Task Description</span></span>|<span data-ttu-id="62535-120">主題</span><span class="sxs-lookup"><span data-stu-id="62535-120">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="62535-121">描述如何使用 **Invoke-Sqlcmd** 來執行包含 **或 XQuery 陳述式的** sqlcmd [!INCLUDE[tsql](../includes/tsql-md.md)] 指令碼或命令。</span><span class="sxs-lookup"><span data-stu-id="62535-121">Describes using **Invoke-Sqlcmd** to run **sqlcmd** scripts or commands that contain [!INCLUDE[tsql](../includes/tsql-md.md)] or XQuery statements.</span></span> <span data-ttu-id="62535-122">它可接受 **sqlcmd** 輸入作為字元字串輸入參數，或作為要開啟的指令碼檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="62535-122">It can accept the **sqlcmd** input as either a character string input parameter, or as the name of a script file to open.</span></span>|[<span data-ttu-id="62535-123">Invoke-Sqlcmd 指令程式</span><span class="sxs-lookup"><span data-stu-id="62535-123">Invoke-Sqlcmd cmdlet</span></span>](../../2014/database-engine/invoke-sqlcmd-cmdlet.md)|  
|<span data-ttu-id="62535-124">描述如何使用 **Invoke-PolicyEvaluation** 報告 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 物件的目標集是否符合在原則式管理原則中定義的條件。</span><span class="sxs-lookup"><span data-stu-id="62535-124">Describes using **Invoke-PolicyEvaluation** to report whether a target set of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects comply with the conditions that are defined in policy-based management policies.</span></span> <span data-ttu-id="62535-125">您可以選擇性地使用此指令程式，在目標物件中重新設定任何不符合原則條件的可設定選項。</span><span class="sxs-lookup"><span data-stu-id="62535-125">Optionally, the cmdlet can be used to reconfigure any settable options in the target objects that do not comply with the policy conditions.</span></span>|[<span data-ttu-id="62535-126">Invoke-PolicyEvaluation 指令程式</span><span class="sxs-lookup"><span data-stu-id="62535-126">Invoke-PolicyEvaluation cmdlet</span></span>](../../2014/database-engine/invoke-policyevaluation-cmdlet.md)|  
|<span data-ttu-id="62535-127">描述如何使用 `Encode-Sqlname` 和 `Decode-Sqlname` 處理含有 Windows PowerShell 路徑不支援之字元的 SQL Server 識別碼。</span><span class="sxs-lookup"><span data-stu-id="62535-127">Describes using `Encode-Sqlname` and `Decode-Sqlname` to handle SQL Server identifiers that contain characters not supported in Windows PowerShell paths.</span></span>|[<span data-ttu-id="62535-128">編碼及解碼 SQL Server 識別碼</span><span class="sxs-lookup"><span data-stu-id="62535-128">Encode and Decode SQL Server Identifiers</span></span>](../powershell/encode-and-decode-sql-server-identifiers.md)|  
|<span data-ttu-id="62535-129">描述如何使用 `Convert-UrnToPath`，將 SQL Server 管理能力物件統一資源名稱 (URN) 轉換為對等的 SQL Server 提供者路徑。</span><span class="sxs-lookup"><span data-stu-id="62535-129">Describes using `Convert-UrnToPath` to convert a SQL Server Manageability Object Uniform Resource Name (URN) to the equivalent SQL Server Provider path.</span></span>|[<span data-ttu-id="62535-130">將 URN 轉換成 SQL Server 提供者路徑</span><span class="sxs-lookup"><span data-stu-id="62535-130">Convert URNs to SQL Server Provider Paths</span></span>](../../2014/database-engine/convert-urns-to-sql-server-provider-paths.md)|  
  
## <a name="see-also"></a><span data-ttu-id="62535-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62535-131">See Also</span></span>  
 <span data-ttu-id="62535-132">[SQL Server PowerShell 提供者](../powershell/sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="62535-132">[SQL Server PowerShell Provider](../powershell/sql-server-powershell-provider.md) </span></span>  
 <span data-ttu-id="62535-133">[SQL Server PowerShell](../powershell/sql-server-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="62535-133">[SQL Server PowerShell](../powershell/sql-server-powershell.md) </span></span>  
 [<span data-ttu-id="62535-134">AlwaysOn 可用性群組 &#40;SQL Server&#41;的 PowerShell Cmdlet 總覽</span><span class="sxs-lookup"><span data-stu-id="62535-134">Overview of PowerShell Cmdlets for AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](availability-groups/windows/overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md)  
  
  
