---
title: 資料庫引擎 PowerShell 參考 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 3c379a43-c497-47dd-8e7d-2b015c068bb7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2d72f9fcedee02e475369c32a7c263578c9ff156
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596885"
---
# <a name="database-engine-powershell-reference"></a><span data-ttu-id="f5568-102">資料庫引擎 PowerShell 參考</span><span class="sxs-lookup"><span data-stu-id="f5568-102">Database Engine PowerShell Reference</span></span>
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="f5568-103">包含一組用以執行 [!INCLUDE[ssDE](../includes/ssde-md.md)] 中常用動作的 Windows PowerShell 2.0 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f5568-103">includes a set of Windows PowerShell 2.0 cmdlets for performing common actions in the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="f5568-104">此外，查詢運算式與統一資源名稱 (URN) 可轉換為 SQL Server PowerShell 路徑，或用以指定 [!INCLUDE[ssDE](../includes/ssde-md.md)]中的一個或多個物件。</span><span class="sxs-lookup"><span data-stu-id="f5568-104">In addition, Query Expressions and Uniform Resource Names (URN) can be converted to SQL Server PowerShell paths, or used to specify one or more objects in the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
## <a name="database-engine-cmdlets"></a><span data-ttu-id="f5568-105">Database Engine Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f5568-105">Database Engine Cmdlets</span></span>  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] <span data-ttu-id="f5568-106">包含相對較少的 [!INCLUDE[ssDE](../includes/ssde-md.md)]Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f5568-106">includes relatively few cmdlets for the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="f5568-107">多數用於 [!INCLUDE[ssDE](../includes/ssde-md.md)] 的 PowerShell 指令碼，皆使用 SQL Server PowerShell 提供者和管理能力物件模型。</span><span class="sxs-lookup"><span data-stu-id="f5568-107">Most PowerShell scripts working with the [!INCLUDE[ssDE](../includes/ssde-md.md)] use the SQL Server PowerShell provider and the manageability object models.</span></span> <span data-ttu-id="f5568-108">如需詳細資訊，請參閱 [SQL Server PowerShell Provider](../powershell/sql-server-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="f5568-108">For more information, see [SQL Server PowerShell Provider](../powershell/sql-server-powershell-provider.md).</span></span>  
  
 <span data-ttu-id="f5568-109">如需了解在 Windows PowerShell 環境中取得 SQL Server Cmdlet 相關說明的方法，請參閱＜ [Get Help SQL Server PowerShell](../powershell/sql-server-powershell.md)＞。</span><span class="sxs-lookup"><span data-stu-id="f5568-109">To learn how to get help about the SQL Server cmdlets in a Windows PowerShell environment, see [Get Help SQL Server PowerShell](../powershell/sql-server-powershell.md).</span></span>  
  
### <a name="in-this-section"></a><span data-ttu-id="f5568-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="f5568-110">In This Section</span></span>  
 <span data-ttu-id="f5568-111">本節包含了有關這些 Cmdlet 的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="f5568-111">This section contains information about these cmdlets.</span></span>  
  
|<span data-ttu-id="f5568-112">描述</span><span class="sxs-lookup"><span data-stu-id="f5568-112">Description</span></span>|<span data-ttu-id="f5568-113">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f5568-113">Cmdlet</span></span>|  
|-----------------|------------|  
|<span data-ttu-id="f5568-114">執行 Runs Transact-SQL 與 XQuery 指令碼，例如可使用 `sqlcmd` 公用程式執行的指令碼。</span><span class="sxs-lookup"><span data-stu-id="f5568-114">Runs Transact-SQL and XQuery scripts, such as scripts that can be run using the `sqlcmd` utility.</span></span>|[<span data-ttu-id="f5568-115">Invoke-Sqlcmd 指令程式</span><span class="sxs-lookup"><span data-stu-id="f5568-115">Invoke-Sqlcmd cmdlet</span></span>](../../2014/database-engine/invoke-sqlcmd-cmdlet.md)|  
|<span data-ttu-id="f5568-116">評估 Database Engine 物件是否符合原則式管理之原則。</span><span class="sxs-lookup"><span data-stu-id="f5568-116">Evaluates whether a Database Engine object complies with a Policy-based Management policy.</span></span>|[<span data-ttu-id="f5568-117">Invoke-PolicyEvaluation 指令程式</span><span class="sxs-lookup"><span data-stu-id="f5568-117">Invoke-PolicyEvaluation cmdlet</span></span>](../../2014/database-engine/invoke-policyevaluation-cmdlet.md)|  
  
### <a name="information-about-other-cmdlets"></a><span data-ttu-id="f5568-118">其他 Cmdlet 的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="f5568-118">Information About Other Cmdlets</span></span>  
 <span data-ttu-id="f5568-119">`Encode-Sqlname` 與 `Decode-Sqlname` Cmdlet 可協助您指定內含 PowerShell 路徑所不支援之字元的 SQL Server 識別碼。</span><span class="sxs-lookup"><span data-stu-id="f5568-119">The `Encode-Sqlname` and `Decode-Sqlname` cmdlets help you specify SQL Server identifiers that contain characters not supported in PowerShell paths.</span></span> <span data-ttu-id="f5568-120">如需詳細資訊，請參閱 [SQL Server Identifiers in PowerShell](../powershell/sql-server-identifiers-in-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="f5568-120">For more information, see [SQL Server Identifiers in PowerShell](../powershell/sql-server-identifiers-in-powershell.md).</span></span>  
  
 <span data-ttu-id="f5568-121">使用 `Convert-UrnToPath` Cmdlet 將 [!INCLUDE[ssDE](../includes/ssde-md.md)] 物件的唯一資源名稱轉換為 SQL Server PowerShell 提供者的路徑。</span><span class="sxs-lookup"><span data-stu-id="f5568-121">Use the `Convert-UrnToPath` cmdlet to convert a Unique Resource Name for a [!INCLUDE[ssDE](../includes/ssde-md.md)] object to a path for the SQL Server PowerShell provider.</span></span> <span data-ttu-id="f5568-122">如需詳細資訊，請參閱 [Convert URNs to SQL Server Provider Paths](../../2014/database-engine/convert-urns-to-sql-server-provider-paths.md)。</span><span class="sxs-lookup"><span data-stu-id="f5568-122">For more information, see [Convert URNs to SQL Server Provider Paths](../../2014/database-engine/convert-urns-to-sql-server-provider-paths.md).</span></span>  
  
## <a name="query-expressions-and-unique-resource-names"></a><span data-ttu-id="f5568-123">查詢運算式和唯一的資源名稱</span><span class="sxs-lookup"><span data-stu-id="f5568-123">Query Expressions and Unique Resource Names</span></span>  
 <span data-ttu-id="f5568-124">查詢運算式是使用類似 XPath 語法的一些字串，可用以指定在物件模型階層中列舉一個或多個物件的準則集合。</span><span class="sxs-lookup"><span data-stu-id="f5568-124">Query expressions are strings that use syntax similar to XPath to specify a set of criteria that enumerate one or more objects in an object model hierarchy.</span></span> <span data-ttu-id="f5568-125">唯一的資源名稱 (URN) 是可唯一識別單一物件的特定查詢運算式字串類型。</span><span class="sxs-lookup"><span data-stu-id="f5568-125">A Unique Resource Name (URN) is a specific type of query expression string that uniquely identifies a single object.</span></span> <span data-ttu-id="f5568-126">如需詳細資訊，請參閱 [Query Expressions and Uniform Resource Names](../powershell/query-expressions-and-uniform-resource-names.md)。</span><span class="sxs-lookup"><span data-stu-id="f5568-126">For more information, see [Query Expressions and Uniform Resource Names](../powershell/query-expressions-and-uniform-resource-names.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5568-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5568-127">See Also</span></span>  
 [<span data-ttu-id="f5568-128">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="f5568-128">SQL Server PowerShell</span></span>](../powershell/sql-server-powershell.md)  
  
  
