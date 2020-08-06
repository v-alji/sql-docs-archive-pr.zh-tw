---
title: 匯入 SQLPS 模組 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: a972c56e-b2af-4fe6-abbd-817406e2c93a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 37e66db05615ce8a285a80e5ac26b0cae411abeb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703277"
---
# <a name="import-the-sqlps-module"></a><span data-ttu-id="3281c-102">匯入 SQLPS 模組</span><span class="sxs-lookup"><span data-stu-id="3281c-102">Import the SQLPS Module</span></span>
  <span data-ttu-id="3281c-103">從 PowerShell 管理 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的建議方式是將 `sqlps` 模組匯入 Windows PowerShell 2.0 環境中。</span><span class="sxs-lookup"><span data-stu-id="3281c-103">The recommended way to manage [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] from PowerShell is to import the `sqlps` module into a Windows PowerShell 2.0 environment.</span></span> <span data-ttu-id="3281c-104">此模組會載入及註冊 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 嵌入式管理單元和管理能力組件。</span><span class="sxs-lookup"><span data-stu-id="3281c-104">The module loads and registers the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] snap-ins and manageability assemblies.</span></span>  
  
1.  <span data-ttu-id="3281c-105">**開始之前：**  [安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="3281c-105">**Before You Begin:**  [Security](#Security)</span></span>  
  
2.  <span data-ttu-id="3281c-106">**載入模組**  [載入 sqlps 模組](#LoadSqlps)</span><span class="sxs-lookup"><span data-stu-id="3281c-106">**To load the module:**  [Load the sqlps Module](#LoadSqlps)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="3281c-107">開始之前</span><span class="sxs-lookup"><span data-stu-id="3281c-107">Before You Begin</span></span>  
 <span data-ttu-id="3281c-108">將 `sqlps` 模組匯入 Windows PowerShell 之後，即可：</span><span class="sxs-lookup"><span data-stu-id="3281c-108">After importing the `sqlps` module into Windows PowerShell, you can then:</span></span>  
  
-   <span data-ttu-id="3281c-109">以互動方式執行 Windows PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="3281c-109">Interactively run Windows PowerShell commands.</span></span>  
  
-   <span data-ttu-id="3281c-110">執行 Windows PowerShell 指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="3281c-110">Run Windows PowerShell script files.</span></span>  
  
-   <span data-ttu-id="3281c-111">執行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 指令程式。</span><span class="sxs-lookup"><span data-stu-id="3281c-111">Run [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlets.</span></span>  
  
-   <span data-ttu-id="3281c-112">使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 提供者路徑來逐一導覽 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 物件的階層。</span><span class="sxs-lookup"><span data-stu-id="3281c-112">Use the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider paths to navigate through the hierarchy of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects.</span></span>  
  
-   <span data-ttu-id="3281c-113">使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 管理能力物件模型 (例如 Microsoft.SqlServer.Management.Smo) 來管理 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 物件。</span><span class="sxs-lookup"><span data-stu-id="3281c-113">Use the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] manageability object models (such as Microsoft.SqlServer.Management.Smo) to manage [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3281c-114">兩個 SQL Server Cmdlet (`Encode-Sqlname` 和 `Decode-Sqlname`) 名稱中所用的動詞，與核准的 Windows PowerShell 2.0 動詞不相符。</span><span class="sxs-lookup"><span data-stu-id="3281c-114">The verbs used in the names of two SQL Server cmdlets (`Encode-Sqlname` and `Decode-Sqlname`) do not match the approved verbs for Windows PowerShell 2.0.</span></span> <span data-ttu-id="3281c-115">這不會影響其作業，但是 Windows PowerShell 會在將 `sqlps` 模組匯入工作階段時引發警告。</span><span class="sxs-lookup"><span data-stu-id="3281c-115">This has no effect on their operation, but Windows PowerShell raises a warning when the `sqlps` module is imported to a session.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3281c-116">Security</span><span class="sxs-lookup"><span data-stu-id="3281c-116">Security</span></span>  
 <span data-ttu-id="3281c-117">根據預設，Windows PowerShell 執行時會將指令碼執行原則設定為 [受限制]\*\*\*\*，這樣就不會執行任何 Windows PowerShell 指令碼。</span><span class="sxs-lookup"><span data-stu-id="3281c-117">By default, Windows PowerShell runs with the scripting execution policy set to **Restricted**, which prevents running any Windows PowerShell scripts.</span></span> <span data-ttu-id="3281c-118">若要載入 `sqlps` 模組，您可以使用 `Set-ExecutionPolicy` Cmdlet 來允許執行已簽署的指令碼或任何指令碼。</span><span class="sxs-lookup"><span data-stu-id="3281c-118">To load the `sqlps` module, you can use the `Set-ExecutionPolicy` cmdlet to enable running signed scripts, or any scripts.</span></span> <span data-ttu-id="3281c-119">建議您只執行來自信任來源的指令碼，並且利用適當的 NTFS 權限來保護所有輸入檔和輸出檔的安全。</span><span class="sxs-lookup"><span data-stu-id="3281c-119">Only run scripts from trusted sources, and secure all input and output files using the appropriate NTFS permissions.</span></span> <span data-ttu-id="3281c-120">如需啟用 Windows PowerShell 指令碼的詳細資訊，請參閱 [Running Windows PowerShell Scripts](https://docs.microsoft.com/powershell/scripting/getting-started/starting-windows-powershell?view=powershell-6#how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows)(執行 Windows PowerShell 指令碼)。</span><span class="sxs-lookup"><span data-stu-id="3281c-120">For more information about enabling Windows PowerShell scripts, see [Running Windows PowerShell Scripts](https://docs.microsoft.com/powershell/scripting/getting-started/starting-windows-powershell?view=powershell-6#how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows).</span></span>  
  
##  <a name="load-the-sqlps-module"></a><a name="LoadSqlps"></a> <span data-ttu-id="3281c-121">載入 sqlps 模組</span><span class="sxs-lookup"><span data-stu-id="3281c-121">Load the sqlps Module</span></span>  

### <a name="to-load-the-sqlps-module-in-windows-powershell"></a><span data-ttu-id="3281c-122">在 Windows PowerShell 中載入 sqlps 模組</span><span class="sxs-lookup"><span data-stu-id="3281c-122">To load the sqlps module in Windows PowerShell</span></span>
  
1.  <span data-ttu-id="3281c-123">使用 `Set-ExecutionPolicy` Cmdlet，設定適當的指令碼執行原則。</span><span class="sxs-lookup"><span data-stu-id="3281c-123">Use the `Set-ExecutionPolicy` cmdlet to set the appropriate script execution policy.</span></span>  
  
2.  <span data-ttu-id="3281c-124">使用 `Import-Module` Cmdlet，匯入 sqlps 模組。</span><span class="sxs-lookup"><span data-stu-id="3281c-124">Use the `Import-Module` cmdlet to import the sqlps module.</span></span> <span data-ttu-id="3281c-125">如果您想要隱藏 `DisableNameChecking` 和 `Encode-Sqlname` 的警告，請指定 `Decode-Sqlname` 參數。</span><span class="sxs-lookup"><span data-stu-id="3281c-125">Specify the `DisableNameChecking` parameter if you want to suppress the warning about `Encode-Sqlname` and `Decode-Sqlname`.</span></span>  
  
### <a name="example-powershell"></a><span data-ttu-id="3281c-126">範例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="3281c-126">Example (PowerShell)</span></span>  
 <span data-ttu-id="3281c-127">此範例載入已關閉名稱檢查的 `sqlps` 模組。</span><span class="sxs-lookup"><span data-stu-id="3281c-127">This example loads the `sqlps` module with name checking turned off.</span></span>  
  
```powershell
## Import the SQL Server Module.  
  
Import-Module "sqlps" -DisableNameChecking  
```  

## <a name="see-also"></a><span data-ttu-id="3281c-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3281c-128">See Also</span></span>  
 <span data-ttu-id="3281c-129">[SQL Server PowerShell](../powershell/sql-server-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="3281c-129">[SQL Server PowerShell](../powershell/sql-server-powershell.md) </span></span>  
 <span data-ttu-id="3281c-130">[SQL Server PowerShell 提供者](../powershell/sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="3281c-130">[SQL Server PowerShell Provider](../powershell/sql-server-powershell-provider.md) </span></span>  
 [<span data-ttu-id="3281c-131">使用 Database Engine Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3281c-131">Use the Database Engine cmdlets</span></span>](../../2014/database-engine/use-the-database-engine-cmdlets.md)  
