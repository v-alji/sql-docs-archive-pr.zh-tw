---
title: 導覽 SQL Server PowerShell 路徑 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: d68aca48-d161-45ed-9f4f-14122ed30218
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0a605479991c3e907cd9dcae254cc1bc04a49392
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708458"
---
# <a name="navigate-sql-server-powershell-paths"></a><span data-ttu-id="18e1f-102">導覽 SQL Server PowerShell 路徑</span><span class="sxs-lookup"><span data-stu-id="18e1f-102">Navigate SQL Server PowerShell Paths</span></span>
  <span data-ttu-id="18e1f-103">[!INCLUDE[ssDE](../includes/ssde-md.md)] PowerShell 提供者會公開一組物件，而這組物件位在類似於檔案路徑之結構的 SQL Server 執行個體中。</span><span class="sxs-lookup"><span data-stu-id="18e1f-103">The [!INCLUDE[ssDE](../includes/ssde-md.md)] PowerShell provider exposes the set of objects in an instance of SQL Server in a structure similar to a file path.</span></span> <span data-ttu-id="18e1f-104">您可以使用 Windows PowerShell 指令程式導覽提供者路徑，以及建立自訂磁碟機來縮短必須輸入的路徑。</span><span class="sxs-lookup"><span data-stu-id="18e1f-104">You can use Windows PowerShell cmdlets to navigate the provider path, and create custom drives to shorten the path you have to type.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="18e1f-105">開始之前</span><span class="sxs-lookup"><span data-stu-id="18e1f-105">Before You Begin</span></span>  
 <span data-ttu-id="18e1f-106">Windows PowerShell 實作指令程式以導覽路徑結構，而路徑結構代表 PowerShell 提供者所支援物件的階層。</span><span class="sxs-lookup"><span data-stu-id="18e1f-106">Windows PowerShell implements cmdlets to navigate the path structure that represent the hierarchy of objects supported by a PowerShell provider.</span></span> <span data-ttu-id="18e1f-107">在您導覽至路徑中的節點時，可以使用其他 Cmdlet 來執行目前物件的基本作業。</span><span class="sxs-lookup"><span data-stu-id="18e1f-107">When you have navigated to a node in the path, you can use other cmdlets to perform basic operations on the current object.</span></span> <span data-ttu-id="18e1f-108">由於 Cmdlet 會經常被使用，所以具有簡短、標準的別名。</span><span class="sxs-lookup"><span data-stu-id="18e1f-108">Because the cmdlets are used frequently, they have short, canonical aliases.</span></span> <span data-ttu-id="18e1f-109">也有一組別名會將指令程式對應到類似的命令提示字元命令，而且有另一組別名適用於 UNIX Shell 命令。</span><span class="sxs-lookup"><span data-stu-id="18e1f-109">There is also one set of aliases that maps the cmdlets to similar command prompt commands, and another set for UNIX shell commands.</span></span>  
  
 <span data-ttu-id="18e1f-110">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 提供者會實作提供者指令程式的子集，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="18e1f-110">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider implements a subset of the provider cmdlets, shown in the following table.</span></span>  
  
|<span data-ttu-id="18e1f-111">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="18e1f-111">cmdlet</span></span>|<span data-ttu-id="18e1f-112">標準的別名</span><span class="sxs-lookup"><span data-stu-id="18e1f-112">Canonical alias</span></span>|<span data-ttu-id="18e1f-113">cmd 別名</span><span class="sxs-lookup"><span data-stu-id="18e1f-113">cmd alias</span></span>|<span data-ttu-id="18e1f-114">UNIX Shell 別名</span><span class="sxs-lookup"><span data-stu-id="18e1f-114">UNIX shell alias</span></span>|<span data-ttu-id="18e1f-115">描述</span><span class="sxs-lookup"><span data-stu-id="18e1f-115">Description</span></span>|  
|------------|---------------------|---------------|----------------------|-----------------|  
|<span data-ttu-id="18e1f-116">**Get-Location**</span><span class="sxs-lookup"><span data-stu-id="18e1f-116">**Get-Location**</span></span>|<span data-ttu-id="18e1f-117">**gl**</span><span class="sxs-lookup"><span data-stu-id="18e1f-117">**gl**</span></span>|<span data-ttu-id="18e1f-118">**pwd**</span><span class="sxs-lookup"><span data-stu-id="18e1f-118">**pwd**</span></span>|<span data-ttu-id="18e1f-119">**pwd**</span><span class="sxs-lookup"><span data-stu-id="18e1f-119">**pwd**</span></span>|<span data-ttu-id="18e1f-120">取得目前的節點。</span><span class="sxs-lookup"><span data-stu-id="18e1f-120">Gets the current node.</span></span>|  
|`Set-Location`|<span data-ttu-id="18e1f-121">**sl**</span><span class="sxs-lookup"><span data-stu-id="18e1f-121">**sl**</span></span>|<span data-ttu-id="18e1f-122">**cd, chdir**</span><span class="sxs-lookup"><span data-stu-id="18e1f-122">**cd, chdir**</span></span>|<span data-ttu-id="18e1f-123">**cd, chdir**</span><span class="sxs-lookup"><span data-stu-id="18e1f-123">**cd, chdir**</span></span>|<span data-ttu-id="18e1f-124">變更目前的節點。</span><span class="sxs-lookup"><span data-stu-id="18e1f-124">Changes the current node.</span></span>|  
|<span data-ttu-id="18e1f-125">**Get-ChildItem**</span><span class="sxs-lookup"><span data-stu-id="18e1f-125">**Get-ChildItem**</span></span>|<span data-ttu-id="18e1f-126">**gci**</span><span class="sxs-lookup"><span data-stu-id="18e1f-126">**gci**</span></span>|<span data-ttu-id="18e1f-127">**dir**</span><span class="sxs-lookup"><span data-stu-id="18e1f-127">**dir**</span></span>|<span data-ttu-id="18e1f-128">**！**</span><span class="sxs-lookup"><span data-stu-id="18e1f-128">**ls**</span></span>|<span data-ttu-id="18e1f-129">列出儲存在目前節點上的物件。</span><span class="sxs-lookup"><span data-stu-id="18e1f-129">Lists the objects stored at the current node.</span></span>|  
|<span data-ttu-id="18e1f-130">**Get-Item**</span><span class="sxs-lookup"><span data-stu-id="18e1f-130">**Get-Item**</span></span>|<span data-ttu-id="18e1f-131">**gi**</span><span class="sxs-lookup"><span data-stu-id="18e1f-131">**gi**</span></span>|||<span data-ttu-id="18e1f-132">傳回目前項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="18e1f-132">Returns the properties of the current item.</span></span>|  
|<span data-ttu-id="18e1f-133">**Rename-Item**</span><span class="sxs-lookup"><span data-stu-id="18e1f-133">**Rename-Item**</span></span>|<span data-ttu-id="18e1f-134">**rni**</span><span class="sxs-lookup"><span data-stu-id="18e1f-134">**rni**</span></span>|<span data-ttu-id="18e1f-135">**rn**</span><span class="sxs-lookup"><span data-stu-id="18e1f-135">**rn**</span></span>|<span data-ttu-id="18e1f-136">**ren**</span><span class="sxs-lookup"><span data-stu-id="18e1f-136">**ren**</span></span>|<span data-ttu-id="18e1f-137">重新命名物件。</span><span class="sxs-lookup"><span data-stu-id="18e1f-137">Renames an object.</span></span>|  
|<span data-ttu-id="18e1f-138">**Remove-Item**</span><span class="sxs-lookup"><span data-stu-id="18e1f-138">**Remove-Item**</span></span>|<span data-ttu-id="18e1f-139">**ri**</span><span class="sxs-lookup"><span data-stu-id="18e1f-139">**ri**</span></span>|<span data-ttu-id="18e1f-140">**del, rd**</span><span class="sxs-lookup"><span data-stu-id="18e1f-140">**del, rd**</span></span>|<span data-ttu-id="18e1f-141">**rm, rmdir**</span><span class="sxs-lookup"><span data-stu-id="18e1f-141">**rm, rmdir**</span></span>|<span data-ttu-id="18e1f-142">移除物件。</span><span class="sxs-lookup"><span data-stu-id="18e1f-142">Removes an object.</span></span>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="18e1f-143">某些 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 識別碼 (物件名稱) 包含 Windows PowerShell 在路徑名稱中不支援的字元。</span><span class="sxs-lookup"><span data-stu-id="18e1f-143">Some [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] identifiers (object names) contain characters that Windows PowerShell does not support in path names.</span></span> <span data-ttu-id="18e1f-144">如需如何使用包含這些字元之名稱的詳細資訊，請參閱 [PowerShell 中的 SQL Server 識別碼](sql-server-identifiers-in-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="18e1f-144">For more information about how to use names that contain these characters, see [SQL Server Identifiers in PowerShell](sql-server-identifiers-in-powershell.md).</span></span>  
  
### <a name="sql-server-information-returned-by-get-childitem"></a><span data-ttu-id="18e1f-145">Get-ChildItem 所傳回的 SQL Server 資訊</span><span class="sxs-lookup"><span data-stu-id="18e1f-145">SQL Server Information Returned by Get-ChildItem</span></span>  
 <span data-ttu-id="18e1f-146">**Get-ChildItem** (或其 **dir** 和 **ls** 別名) 傳回的資訊視您在 SQLSERVER: 路徑中的位置而定。</span><span class="sxs-lookup"><span data-stu-id="18e1f-146">The information returned by **Get-ChildItem** (or its **dir** and **ls** aliases) depends on your location in a SQLSERVER: path.</span></span>  
  
|<span data-ttu-id="18e1f-147">路徑位置</span><span class="sxs-lookup"><span data-stu-id="18e1f-147">Path location</span></span>|<span data-ttu-id="18e1f-148">Get-ChildItem 結果</span><span class="sxs-lookup"><span data-stu-id="18e1f-148">Get-ChildItem results</span></span>|  
|-------------------|----------------------------|  
|<span data-ttu-id="18e1f-149">SQLSERVER:\SQL</span><span class="sxs-lookup"><span data-stu-id="18e1f-149">SQLSERVER:\SQL</span></span>|<span data-ttu-id="18e1f-150">傳回本機電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="18e1f-150">Returns the name of the local computer.</span></span> <span data-ttu-id="18e1f-151">若您已經使用 SMO 或 WMI 連接到其他電腦上的 [!INCLUDE[ssDE](../includes/ssde-md.md)] 執行個體，也會列出這些電腦。</span><span class="sxs-lookup"><span data-stu-id="18e1f-151">If you have used the SMO or WMI to connect to instances of the [!INCLUDE[ssDE](../includes/ssde-md.md)] on other computers, those computers are also listed.</span></span>|  
|<span data-ttu-id="18e1f-152">SQLSERVER:\SQL\\*ComputerName*</span><span class="sxs-lookup"><span data-stu-id="18e1f-152">SQLSERVER:\SQL\\*ComputerName*</span></span>|<span data-ttu-id="18e1f-153">電腦上 [!INCLUDE[ssDE](../includes/ssde-md.md)] 執行個體的清單。</span><span class="sxs-lookup"><span data-stu-id="18e1f-153">The list of instances of the [!INCLUDE[ssDE](../includes/ssde-md.md)] on the computer.</span></span>|  
|<span data-ttu-id="18e1f-154">SQLSERVER： \ SQL \\ *ComputerName* \\ *實例*名稱</span><span class="sxs-lookup"><span data-stu-id="18e1f-154">SQLSERVER:\SQL\\*ComputerName*\\*InstanceName*</span></span>|<span data-ttu-id="18e1f-155">執行個體中最上層物件類型的清單，例如 Endpoints、Certificates 和 Databases。</span><span class="sxs-lookup"><span data-stu-id="18e1f-155">The list of top-level object types in the instance, such as Endpoints, Certificates, and Databases.</span></span>|  
|<span data-ttu-id="18e1f-156">物件類別節點，例如 Databases</span><span class="sxs-lookup"><span data-stu-id="18e1f-156">Object class node, such as Databases</span></span>|<span data-ttu-id="18e1f-157">該類型的物件清單，例如資料庫的清單：master、model、AdventureWorks20008R2。</span><span class="sxs-lookup"><span data-stu-id="18e1f-157">The list of objects of that type, such as the list of databases: master, model, AdventureWorks20008R2.</span></span>|  
|<span data-ttu-id="18e1f-158">物件名稱節點，例如 AdventureWorks2012</span><span class="sxs-lookup"><span data-stu-id="18e1f-158">Object name node, such as AdventureWorks2012</span></span>|<span data-ttu-id="18e1f-159">此物件內所包含的物件類型清單。</span><span class="sxs-lookup"><span data-stu-id="18e1f-159">The list of object types contained within the object.</span></span> <span data-ttu-id="18e1f-160">例如，資料庫會列出資料表和檢視表之類的物件類型。</span><span class="sxs-lookup"><span data-stu-id="18e1f-160">For example, a database would list object types such as tables and views.</span></span>|  
  
 <span data-ttu-id="18e1f-161">**Get-ChildItem** 預設不會列出任何系統物件。</span><span class="sxs-lookup"><span data-stu-id="18e1f-161">By default, **Get-ChildItem** does not list any system objects.</span></span> <span data-ttu-id="18e1f-162">*Force* 參數可用來查看系統物件，例如 **sys** 結構描述中的物件。</span><span class="sxs-lookup"><span data-stu-id="18e1f-162">Use the *Force* parameter to see system objects, such as the objects in the **sys** schema.</span></span>  
  
### <a name="custom-drives"></a><span data-ttu-id="18e1f-163">自訂磁碟機</span><span class="sxs-lookup"><span data-stu-id="18e1f-163">Custom Drives</span></span>  
 <span data-ttu-id="18e1f-164">Windows PowerShell 可讓使用者定義稱為 PowerShell 磁碟機的虛擬磁碟機。</span><span class="sxs-lookup"><span data-stu-id="18e1f-164">Windows PowerShell lets users define virtual drives, which are referred to as PowerShell drives.</span></span> <span data-ttu-id="18e1f-165">這些磁碟機會透過路徑陳述式的開始節點進行對應。</span><span class="sxs-lookup"><span data-stu-id="18e1f-165">These map over the starting nodes of a path statement.</span></span> <span data-ttu-id="18e1f-166">它們通常是用來縮短經常輸入的路徑。</span><span class="sxs-lookup"><span data-stu-id="18e1f-166">They are typically used to shorten paths that are typed frequently.</span></span> <span data-ttu-id="18e1f-167">SQLSERVER: 路徑可能會很長，佔據 Windows PowerShell 視窗的空間且需要很長的輸入。</span><span class="sxs-lookup"><span data-stu-id="18e1f-167">SQLSERVER: paths can get long, taking space in the Windows PowerShell window and requiring a lot of typing.</span></span> <span data-ttu-id="18e1f-168">若您要在特定路徑節點上執行很多工作，您可以定義可對應至該節點的自訂 Windows PowerShell 磁碟機。</span><span class="sxs-lookup"><span data-stu-id="18e1f-168">If you are going to do a lot of work at a particular path node, you can define a custom Windows PowerShell drive that maps to that node.</span></span>  
  
## <a name="use-powershell-cmdlet-aliases"></a><span data-ttu-id="18e1f-169">使用 PowerShell 指令程式別名</span><span class="sxs-lookup"><span data-stu-id="18e1f-169">Use PowerShell Cmdlet Aliases</span></span>  
 <span data-ttu-id="18e1f-170">**使用 Cmdlet 別名**</span><span class="sxs-lookup"><span data-stu-id="18e1f-170">**Use a cmdlet alias**</span></span>  
  
-   <span data-ttu-id="18e1f-171">輸入較短的別名，或對應至熟悉命令提示字元命令的別名，而不要輸入完整 Cmdlet 名稱。</span><span class="sxs-lookup"><span data-stu-id="18e1f-171">Instead of typing a full cmdlet name, type a shorter alias, or one that maps to a familiar commend prompt command.</span></span>  
  
### <a name="alias-example-powershell"></a><span data-ttu-id="18e1f-172">別名範例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="18e1f-172">Alias Example (PowerShell)</span></span>  
 <span data-ttu-id="18e1f-173">例如，您可以使用下列其中一組 Cmdlet 或別名來擷取可用的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體清單，方式是導覽至 SQLSERVER:\SQL 資料夾，並要求該資料夾的子項目清單：</span><span class="sxs-lookup"><span data-stu-id="18e1f-173">For example, you can use one of the following sets of cmdlets or aliases to retrieve a listing of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instances available to you by navigating to the SQLSERVER:\SQL folder and requesting the list of child items for the folder:</span></span>  
  
```powershell
## Shows using the full cmdet name.  
Set-Location SQLSERVER:\SQL  
Get-ChildItem  
  
## Shows using canonical aliases.  
sl SQLSERVER:\SQL  
gci  
  
## Shows using command prompt aliases.  
cd SQLSERVER:\SQL  
dir  
  
## Shows using Unix shell aliases.  
cd SQLSERVER:\SQL  
ls  
```  
  
## <a name="use-get-childitem"></a><span data-ttu-id="18e1f-174">使用 Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="18e1f-174">Use Get-ChildItem</span></span>  

### <a name="return-information-by-using-get-childitem"></a><span data-ttu-id="18e1f-175">使用 Get-ChildItem 傳回資訊</span><span class="sxs-lookup"><span data-stu-id="18e1f-175">Return information by using Get-Childitem</span></span>
  
1.  <span data-ttu-id="18e1f-176">導覽至您要其 childrem 清單的節點</span><span class="sxs-lookup"><span data-stu-id="18e1f-176">Navigate to the node for which you want a list of childrem</span></span>  
  
2.  <span data-ttu-id="18e1f-177">執行 Get-Childitem 以取得清單。</span><span class="sxs-lookup"><span data-stu-id="18e1f-177">Run Get-Childitem to get the list.</span></span>  
  
### <a name="get-childitem-example-powershell"></a><span data-ttu-id="18e1f-178">Get-ChildItem 範例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="18e1f-178">Get-ChildItem Example (PowerShell)</span></span>  
 <span data-ttu-id="18e1f-179">這些範例說明 Get-Childitem 針對 SQL Server 提供者路徑中不同節點所傳回的資訊。</span><span class="sxs-lookup"><span data-stu-id="18e1f-179">These examples illustrate the information returned by Get-Childitem for different nodes in a SQL Server provider path.</span></span>  
  
```powershell
## Return the current computer and any computer  
## to which you have made a SQL or WMI connection.  
Set-Location SQLSERVER:\SQL  
Get-ChildItem  
  
## List the instances of the Database Engine on the local computer.  
Set-Location SQLSERVER:\SQL\localhost  
Get-ChildItem  
  
## Lists the categories of objects available in the  
## default instance on the local computer.  
Set-Location SQLSERVER:\SQL\localhost\DEFAULT  
Get-ChildItem  
  
## Lists the databases from the local default instance.  
## The force parameter is used to include the system databases.  
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases  
Get-ChildItem -force  
```  
  
## <a name="create-a-custom-drive"></a><span data-ttu-id="18e1f-180">建立自訂磁碟機</span><span class="sxs-lookup"><span data-stu-id="18e1f-180">Create a Custom Drive</span></span>  

### <a name="create-and-use-a-custom-drive"></a><span data-ttu-id="18e1f-181">建立和使用自訂磁碟機</span><span class="sxs-lookup"><span data-stu-id="18e1f-181">Create and use a custom drive</span></span>
  
1.  <span data-ttu-id="18e1f-182">您可以使用 `New-PSDrive` 定義自訂磁碟機。</span><span class="sxs-lookup"><span data-stu-id="18e1f-182">Use `New-PSDrive` to define a custom drive.</span></span> <span data-ttu-id="18e1f-183">您可以使用 `Root` 參數指定以自訂磁碟機名稱呈現的路徑。</span><span class="sxs-lookup"><span data-stu-id="18e1f-183">Use the `Root` parameter to specify the path that is represented by the custom drive name.</span></span>  
  
2.  <span data-ttu-id="18e1f-184">參考路徑導覽 Cmdlet (例如 `Set-Location`) 中的自訂磁碟機名稱。</span><span class="sxs-lookup"><span data-stu-id="18e1f-184">Reference the custom drive name in path navigation cmdlets such as `Set-Location`.</span></span>  
  
### <a name="custom-drive-example-powershell"></a><span data-ttu-id="18e1f-185">自訂磁碟機範例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="18e1f-185">Custom Drive Example (PowerShell)</span></span>  
 <span data-ttu-id="18e1f-186">此範例會建立名為 AWDB 且對應至已部署 AdventureWorks2012 範例資料庫複本之節點的虛擬磁碟機。</span><span class="sxs-lookup"><span data-stu-id="18e1f-186">This example creates a virtual drive named AWDB that maps to the node for a deployed copy of the AdventureWorks2012 sample database.</span></span> <span data-ttu-id="18e1f-187">然後，您可以使用虛擬磁碟機來導覽至資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="18e1f-187">The virtual drive is then used to navigate to a table in the database.</span></span>  
  
```powershell
## Create a new virtual drive.  
New-PSDrive -Name AWDB -Root SQLSERVER:\SQL\localhost\DEFAULT\Databases\AdventureWorks2012  
  
## Use AWDB: to navigate to a specific table.  
Set-Location AWDB:\Tables\Purchasing.Vendor  
```  
  
## <a name="see-also"></a><span data-ttu-id="18e1f-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18e1f-188">See Also</span></span>  
 <span data-ttu-id="18e1f-189">[SQL Server PowerShell 提供者](sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="18e1f-189">[SQL Server PowerShell Provider](sql-server-powershell-provider.md) </span></span>  
 <span data-ttu-id="18e1f-190">[使用 SQL Server PowerShell 路徑](work-with-sql-server-powershell-paths.md) </span><span class="sxs-lookup"><span data-stu-id="18e1f-190">[Work With SQL Server PowerShell Paths](work-with-sql-server-powershell-paths.md) </span></span>  
 <span data-ttu-id="18e1f-191">[將 Urn 轉換為 SQL Server 提供者路徑](../database-engine/convert-urns-to-sql-server-provider-paths.md) </span><span class="sxs-lookup"><span data-stu-id="18e1f-191">[Convert URNs to SQL Server Provider Paths](../database-engine/convert-urns-to-sql-server-provider-paths.md) </span></span>  
 [<span data-ttu-id="18e1f-192">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="18e1f-192">SQL Server PowerShell</span></span>](sql-server-powershell.md)  
