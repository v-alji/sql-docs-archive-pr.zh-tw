---
title: sqlps 公用程式 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- sqlps utility
- PowerShell [SQL Server], sqlps utility
ms.assetid: 4b2515a6-12c3-44fb-b263-1c567681cd2b
author: stevestein
ms.author: sstein
ms.openlocfilehash: b445366b3fb99ad4beebdf7b203ada77afe90c8d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686572"
---
# <a name="sqlps-utility"></a><span data-ttu-id="43eca-102">sqlps 公用程式</span><span class="sxs-lookup"><span data-stu-id="43eca-102">sqlps Utility</span></span>
  <span data-ttu-id="43eca-103">`sqlps` 公用程式會啟動 Windows PowerShell 2.0 工作階段並且載入和註冊 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell 提供者與指令程式。</span><span class="sxs-lookup"><span data-stu-id="43eca-103">The `sqlps` utility starts a Windows PowerShell 2.0 session with the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell provider and cmdlets loaded and registered.</span></span> <span data-ttu-id="43eca-104">您可以輸入 PowerShell 命令或指令碼，以便使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell 元件來處理 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體及其物件。</span><span class="sxs-lookup"><span data-stu-id="43eca-104">You can enter PowerShell commands or scripts that use the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell components to work with instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and their objects.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../includes/ssnotedepfutureavoid-md.md)]<span data-ttu-id="43eca-105">請改用 `sqlps` PowerShell 模組。</span><span class="sxs-lookup"><span data-stu-id="43eca-105">Use the `sqlps` PowerShell module instead.</span></span> <span data-ttu-id="43eca-106">如需模組的詳細資訊 `sqlps` ，請參閱匯[入 SQLPS 模組](../database-engine/import-the-sqlps-module.md)。</span><span class="sxs-lookup"><span data-stu-id="43eca-106">For more information about the `sqlps` module, see [Import the SQLPS Module](../database-engine/import-the-sqlps-module.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43eca-107">語法</span><span class="sxs-lookup"><span data-stu-id="43eca-107">Syntax</span></span>  
  
```  
  
      sqlps   
[ [ [ -NoLogo ][ -NoExit ][ -NoProfile ]  
    [ -OutPutFormat { Text | XML } ] [ -InPutFormat { Text | XML } ]  
  ]  
  [ -Command { -  
             | script_block [ -argsargument_array ]  
             | string [ command_parameters ]  
             }  
  ]  
]  
[ -? | -Help ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="43eca-108">引數</span><span class="sxs-lookup"><span data-stu-id="43eca-108">Arguments</span></span>  
 <span data-ttu-id="43eca-109">**-NoLogo**</span><span class="sxs-lookup"><span data-stu-id="43eca-109">**-NoLogo**</span></span>  
 <span data-ttu-id="43eca-110">指定 `sqlps` 公用程式在啟動時隱藏著作權橫幅。</span><span class="sxs-lookup"><span data-stu-id="43eca-110">Specifies that the `sqlps` utility hide the copyright banner when it starts.</span></span>  
  
 <span data-ttu-id="43eca-111">**-NoExit**</span><span class="sxs-lookup"><span data-stu-id="43eca-111">**-NoExit**</span></span>  
 <span data-ttu-id="43eca-112">指定 `sqlps` 公用程式在啟動命令完成之後繼續執行。</span><span class="sxs-lookup"><span data-stu-id="43eca-112">Specifies that the `sqlps` utility continue running after the startup commands have completed.</span></span>  
  
 <span data-ttu-id="43eca-113">**-NoProfile**</span><span class="sxs-lookup"><span data-stu-id="43eca-113">**-NoProfile**</span></span>  
 <span data-ttu-id="43eca-114">指定 `sqlps` 公用程式不要載入使用者設定檔。</span><span class="sxs-lookup"><span data-stu-id="43eca-114">Specifies that the `sqlps` utility not load a user profile.</span></span> <span data-ttu-id="43eca-115">使用者設定檔會記錄在 PowerShell 工作階段之間常用的別名、函數與變數。</span><span class="sxs-lookup"><span data-stu-id="43eca-115">User profiles record commonly used aliases, functions, and variables for use across PowerShell sessions.</span></span>  
  
 <span data-ttu-id="43eca-116">**-OutPutFormat** { **Text** | **XML** }</span><span class="sxs-lookup"><span data-stu-id="43eca-116">**-OutPutFormat** { **Text** | **XML** }</span></span>  
 <span data-ttu-id="43eca-117">指定 `sqlps` 公用程式輸出要格式化為文字字串， (**文字**) 或 (**XML**) 序列化的 CLIXML 格式。</span><span class="sxs-lookup"><span data-stu-id="43eca-117">Specifies that the `sqlps` utility output be formatted as either text strings (**Text**) or in a serialized CLIXML format (**XML**).</span></span>  
  
 <span data-ttu-id="43eca-118">**-InPutFormat** { **Text** | **XML** }</span><span class="sxs-lookup"><span data-stu-id="43eca-118">**-InPutFormat** { **Text** | **XML** }</span></span>  
 <span data-ttu-id="43eca-119">指定公用程式的輸入要 `sqlps` 格式化為文字字串， (**文字**) 或 (**XML**) 序列化的 CLIXML 格式。</span><span class="sxs-lookup"><span data-stu-id="43eca-119">Specifies that input to the `sqlps` utility is formatted as either text strings (**Text**) or in a serialized CLIXML format (**XML**).</span></span>  
  
 <span data-ttu-id="43eca-120">**-Command**</span><span class="sxs-lookup"><span data-stu-id="43eca-120">**-Command**</span></span>  
 <span data-ttu-id="43eca-121">指定 `sqlps` 公用程式要執行的命令。</span><span class="sxs-lookup"><span data-stu-id="43eca-121">Specifies the command for the `sqlps` utility to run.</span></span> <span data-ttu-id="43eca-122">`sqlps`除非同時指定 **-NoExit** ，否則公用程式會執行命令，然後結束。</span><span class="sxs-lookup"><span data-stu-id="43eca-122">The `sqlps` utility runs the command and then exits, unless **-NoExit** is also specified.</span></span> <span data-ttu-id="43eca-123">請勿在 **-Command**之後指定任何其他參數，因為這些參數將會讀取成命令參數。</span><span class="sxs-lookup"><span data-stu-id="43eca-123">Do not specify any other switches after **-Command**, they will be read as command parameters.</span></span>  
  
 **-**  
 <span data-ttu-id="43eca-124">**-Command-** 指定 `sqlps` 公用程式從標準輸入讀取輸入。</span><span class="sxs-lookup"><span data-stu-id="43eca-124">**-Command-** specifies that the `sqlps` utility read the input from the standard input.</span></span>  
  
 <span data-ttu-id="43eca-125">*script_block* [ **-args**_argument_array_ ]</span><span class="sxs-lookup"><span data-stu-id="43eca-125">*script_block* [ **-args**_argument_array_ ]</span></span>  
 <span data-ttu-id="43eca-126">指定要執行的 PowerShell 命令區塊，此區塊必須以大括號括住：{}。</span><span class="sxs-lookup"><span data-stu-id="43eca-126">Specifies a block of PowerShell commands to run, the block must be enclosed in braces: {}.</span></span> <span data-ttu-id="43eca-127">*Script_block*只有在 `sqlps` 從**PowerShell**或其他 `sqlps` 公用程式會話呼叫公用程式時，才能指定 Script_block。</span><span class="sxs-lookup"><span data-stu-id="43eca-127">*Script_block* can only be specified when the `sqlps` utility is called from either **PowerShell** or another `sqlps` utility session.</span></span> <span data-ttu-id="43eca-128">*argument_array* 是 PowerShell 變數的陣列，其中包含 *script_block*中 PowerShell 命令的引數。</span><span class="sxs-lookup"><span data-stu-id="43eca-128">The *argument_array* is an array of PowerShell variables containing the arguments for the PowerShell commands in the *script_block*.</span></span>  
  
 <span data-ttu-id="43eca-129">*string* [ *command_parameters* ]</span><span class="sxs-lookup"><span data-stu-id="43eca-129">*string* [ *command_parameters* ]</span></span>  
 <span data-ttu-id="43eca-130">指定包含要執行之 PowerShell 命令的字串。</span><span class="sxs-lookup"><span data-stu-id="43eca-130">Specifies a string that contains the PowerShell commands to be run.</span></span> <span data-ttu-id="43eca-131">請使用 **"& { *`command`* }"** 格式。</span><span class="sxs-lookup"><span data-stu-id="43eca-131">Use the format **"&{*`command`*}"**.</span></span> <span data-ttu-id="43eca-132">引號表示字串，而叫用運算子 ( # A0) 會導致 `sqlps` 公用程式執行命令。</span><span class="sxs-lookup"><span data-stu-id="43eca-132">The quotation marks indicate a string, and the invoke operator (&) causes the `sqlps` utility to run the command.</span></span>  
  
 <span data-ttu-id="43eca-133">[ **-?**</span><span class="sxs-lookup"><span data-stu-id="43eca-133">[ **-?**</span></span><span data-ttu-id="43eca-134"> |  **-Help** ]</span><span class="sxs-lookup"><span data-stu-id="43eca-134"> | **-Help** ]</span></span>  
 <span data-ttu-id="43eca-135">顯示 `sqlps` 公用程式選項的語法摘要。</span><span class="sxs-lookup"><span data-stu-id="43eca-135">Shows the syntax summary of the `sqlps` utility options.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43eca-136">備註</span><span class="sxs-lookup"><span data-stu-id="43eca-136">Remarks</span></span>  
 <span data-ttu-id="43eca-137">`sqlps`公用程式會啟動 powershell 環境 ( # A0) 並載入 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] powershell 模組。</span><span class="sxs-lookup"><span data-stu-id="43eca-137">The `sqlps` utility starts the PowerShell environment (PowerShell.exe) and loads the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell module.</span></span> <span data-ttu-id="43eca-138">模組（也稱為 `sqlps` ）會載入並註冊這些 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell 嵌入式管理單元：</span><span class="sxs-lookup"><span data-stu-id="43eca-138">The module, also named `sqlps`, loads and registers these [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell snap-ins:</span></span>  
  
-   <span data-ttu-id="43eca-139">Microsoft.SqlServer.Management.PSProvider.dll</span><span class="sxs-lookup"><span data-stu-id="43eca-139">Microsoft.SqlServer.Management.PSProvider.dll</span></span>  
  
     <span data-ttu-id="43eca-140">實作 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell 提供者和相關聯的 Cmdlet，例如 **Encode-SqlName** 和 **Decode-SqlName**。</span><span class="sxs-lookup"><span data-stu-id="43eca-140">Implements the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell provider and associated cmdlets such as **Encode-SqlName** and **Decode-SqlName**.</span></span>  
  
-   <span data-ttu-id="43eca-141">Microsoft.SqlServer.Management.PSSnapin.dll</span><span class="sxs-lookup"><span data-stu-id="43eca-141">Microsoft.SqlServer.Management.PSSnapin.dll</span></span>  
  
     <span data-ttu-id="43eca-142">實作 **Invoke-Sqlcmd** 和 **Invoke-PolicyEvaluation** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="43eca-142">Implements the **Invoke-Sqlcmd** and **Invoke-PolicyEvaluation** cmdlets.</span></span>  
  
 <span data-ttu-id="43eca-143">您可以使用 `sqlps` 公用程式進行下列作業：</span><span class="sxs-lookup"><span data-stu-id="43eca-143">You can use the `sqlps` utility to do the following:</span></span>  
  
-   <span data-ttu-id="43eca-144">以互動方式執行 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="43eca-144">Interactively run PowerShell commands.</span></span>  
  
-   <span data-ttu-id="43eca-145">執行 PowerShell 指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="43eca-145">Run PowerShell script files.</span></span>  
  
-   <span data-ttu-id="43eca-146">執行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 指令程式。</span><span class="sxs-lookup"><span data-stu-id="43eca-146">Run [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlets.</span></span>  
  
-   <span data-ttu-id="43eca-147">使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 提供者路徑來逐一導覽 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 物件的階層。</span><span class="sxs-lookup"><span data-stu-id="43eca-147">Use the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider paths to navigate through the hierarchy of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects.</span></span>  
  
 <span data-ttu-id="43eca-148">根據預設，公用程式會執行， `sqlps` 並將腳本執行原則設定為 [**受限制**]。</span><span class="sxs-lookup"><span data-stu-id="43eca-148">By default, the `sqlps` utility runs with the scripting execution policy set to **Restricted**.</span></span> <span data-ttu-id="43eca-149">如此即不會執行任何 PowerShell 指令碼。</span><span class="sxs-lookup"><span data-stu-id="43eca-149">This prevents running any PowerShell scripts.</span></span> <span data-ttu-id="43eca-150">您可以使用 **Set-ExecutionPolicy** Cmdlet 來允許執行已簽署的指令碼或任何指令碼。</span><span class="sxs-lookup"><span data-stu-id="43eca-150">You can use the **Set-ExecutionPolicy** cmdlet to enable running signed scripts, or any scripts.</span></span> <span data-ttu-id="43eca-151">建議您只執行來自信任來源的指令碼，並且利用適當的 NTFS 權限來保護所有輸入和輸出檔案。</span><span class="sxs-lookup"><span data-stu-id="43eca-151">Only run scripts from trusted sources, and secure all input and output files by using the appropriate NTFS permissions.</span></span> <span data-ttu-id="43eca-152">如需有關啟用 PowerShell 指令碼的詳細資訊，請參閱 [執行 Windows PowerShell 指令碼](https://www.tech-recipes.com/rx/2513/powershell_enable_script_support/)。</span><span class="sxs-lookup"><span data-stu-id="43eca-152">For more information about enabling PowerShell scripts, see [Running Windows PowerShell Scripts](https://www.tech-recipes.com/rx/2513/powershell_enable_script_support/).</span></span>  
  
 <span data-ttu-id="43eca-153">[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 和 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 中的 `sqlps` 公用程式版本實作為 Windows PowerShell 1.0 迷你 shell。</span><span class="sxs-lookup"><span data-stu-id="43eca-153">The version of the `sqlps` utility in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] and [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] was implemented as a Windows PowerShell 1.0 mini-shell.</span></span> <span data-ttu-id="43eca-154">迷你 Shell 有一些限制，例如不允許使用者載入迷你 Shell 所載入之嵌入式管理單元以外的嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="43eca-154">Mini-shells have certain restrictions, such as not allowing users to load snap-ins other than those loaded by the mini-shell.</span></span> <span data-ttu-id="43eca-155">這些限制不適用於 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 及更高版本的公用程式，這些版本已經變更為使用 `sqlps` 模組。</span><span class="sxs-lookup"><span data-stu-id="43eca-155">These restrictions do not apply to the [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] and higher versions of the utility, which have been changed to use the `sqlps` module.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="43eca-156">範例</span><span class="sxs-lookup"><span data-stu-id="43eca-156">Examples</span></span>  

### <a name="a-run-the-sqlps-utility-in-default-interactive-mode-without-the-copyright-banner"></a><span data-ttu-id="43eca-157">A.</span><span class="sxs-lookup"><span data-stu-id="43eca-157">A.</span></span> <span data-ttu-id="43eca-158">在不顯示著作權橫幅的預設互動模式中執行 sqlps 公用程式</span><span class="sxs-lookup"><span data-stu-id="43eca-158">Run the sqlps utility in default, interactive mode without the copyright banner</span></span>
  
```cmd
sqlps -NoLogo  
```  
  
### <a name="b-run-a-sql-server-powershell-script-from-the-command-prompt"></a><span data-ttu-id="43eca-159">B.</span><span class="sxs-lookup"><span data-stu-id="43eca-159">B.</span></span> <span data-ttu-id="43eca-160">從命令提示字元處執行 SQL Server PowerShell 指令碼</span><span class="sxs-lookup"><span data-stu-id="43eca-160">Run a SQL Server PowerShell script from the command prompt</span></span>
  
```cmd
sqlps -Command "&{.\MyFolder.MyScript.ps1}"  
```  
  
### <a name="c-run-a-sql-server-powershell-script-from-the-command-prompt-and-keep-running-after-the-script-completes"></a><span data-ttu-id="43eca-161">C.</span><span class="sxs-lookup"><span data-stu-id="43eca-161">C.</span></span> <span data-ttu-id="43eca-162">從命令提示字元處執行 SQL Server PowerShell 指令碼，並在指令碼完成之後維持執行狀態</span><span class="sxs-lookup"><span data-stu-id="43eca-162">Run a SQL Server PowerShell script from the command prompt, and keep running after the script completes</span></span>
  
```cmd
sqlps -NoExit -Command "&{.\MyFolder.MyScript.ps1}"  
```  
  
## <a name="see-also"></a><span data-ttu-id="43eca-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43eca-163">See Also</span></span>  
 <span data-ttu-id="43eca-164">[啟用或停用伺服器網路通訊協定](../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md) </span><span class="sxs-lookup"><span data-stu-id="43eca-164">[Enable or Disable a Server Network Protocol](../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md) </span></span>  
 [<span data-ttu-id="43eca-165">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="43eca-165">SQL Server PowerShell</span></span>](../powershell/sql-server-powershell.md)  
