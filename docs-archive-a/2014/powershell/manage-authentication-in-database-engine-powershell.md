---
title: 管理資料庫引擎 PowerShell 中的驗證 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: ab9212a6-6628-4f08-a38c-d3156e05ddea
author: stevestein
ms.author: sstein
ms.openlocfilehash: 018a2698a43148af971622f54c8418bf23c2c781
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687949"
---
# <a name="manage-authentication-in-database-engine-powershell"></a><span data-ttu-id="45a72-102">管理 Database Engine PowerShell 中的驗證</span><span class="sxs-lookup"><span data-stu-id="45a72-102">Manage Authentication in Database Engine PowerShell</span></span>
  <span data-ttu-id="45a72-103">依預設，連接至 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的執行個體時， [!INCLUDE[ssDE](../includes/ssde-md.md)]PowerShell 元件會使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="45a72-103">By default, the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell components use Windows Authentication when connecting to an instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="45a72-104">藉由定義 PowerShell 虛擬磁碟機，或指定 `-Username` 的 `-Password` 和 `Invoke-Sqlcmd` 參數，即可使用 SQL Server 驗證。</span><span class="sxs-lookup"><span data-stu-id="45a72-104">You can use SQL Server Authentication by either defining a PowerShell virtual drive, or by specifying the `-Username` and `-Password` parameters for `Invoke-Sqlcmd`.</span></span>  
  
1.  <span data-ttu-id="45a72-105">**開始之前：** [權限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="45a72-105">**Before you begin:**  [Permissions](#Permissions)</span></span>  
  
2.  <span data-ttu-id="45a72-106">**使用下列項目，設定驗證：**  [虛擬磁碟機](#SQLAuthVirtDrv)、[Invoke-Sqlcmd](#SQLAuthInvSqlCmd)</span><span class="sxs-lookup"><span data-stu-id="45a72-106">**To set authentication, using:**  [A Virtual Drive](#SQLAuthVirtDrv), [Invoke-Sqlcmd](#SQLAuthInvSqlCmd)</span></span>  
  
##  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="45a72-107">權限</span><span class="sxs-lookup"><span data-stu-id="45a72-107">Permissions</span></span>  
 <span data-ttu-id="45a72-108">您在 [!INCLUDE[ssDE](../includes/ssde-md.md)] 的執行個體中可執行的所有動作，都是透過授與用來連接至執行個體之驗證認證的權限所控制。</span><span class="sxs-lookup"><span data-stu-id="45a72-108">All actions you can perform in an instance of the [!INCLUDE[ssDE](../includes/ssde-md.md)] are controlled by the permissions granted to the authentication credentials used to connect to the instance.</span></span> <span data-ttu-id="45a72-109">依預設， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 提供者和 Cmdlet 會使用用來建立 [!INCLUDE[ssDE](../includes/ssde-md.md)]之 Windows 驗證連接的 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="45a72-109">By default, the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider and cmdlets use the Windows account under which it is running to make a Windows Authentication connection to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="45a72-110">若要進行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證連接，您必須提供 SQL Server 驗證登入識別碼和密碼。</span><span class="sxs-lookup"><span data-stu-id="45a72-110">To make a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication connection you must supply a SQL Server Authentication login ID and password.</span></span> <span data-ttu-id="45a72-111">使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 提供者時，您必須將 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 登入認證與虛擬磁片磁碟機產生關聯，然後使用 [變更目錄] 命令 (`cd`) 連線到該磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="45a72-111">When using the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider, you must associate the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login credentials with a virtual drive, and then use the change directory command (`cd`) to connect to that drive.</span></span> <span data-ttu-id="45a72-112">在 Windows PowerShell 中，安全性認證只能與虛擬磁碟機產生關聯。</span><span class="sxs-lookup"><span data-stu-id="45a72-112">In Windows PowerShell, security credentials can only be associated with virtual drives.</span></span>  
  
##  <a name="sql-server-authentication-using-a-virtual-drive"></a><a name="SQLAuthVirtDrv"></a> <span data-ttu-id="45a72-113">使用虛擬磁碟機的 SQL Server 驗證</span><span class="sxs-lookup"><span data-stu-id="45a72-113">SQL Server Authentication Using a Virtual Drive</span></span>  
 <span data-ttu-id="45a72-114">**建立與 SQL Server 驗證登入相關聯的虛擬磁碟機**</span><span class="sxs-lookup"><span data-stu-id="45a72-114">**To create a virtual drive associated with a SQL Server Authentication login**</span></span>  
  
1.  <span data-ttu-id="45a72-115">建立的函數：</span><span class="sxs-lookup"><span data-stu-id="45a72-115">Create a function that:</span></span>  
  
    1.  <span data-ttu-id="45a72-116">具有參數可表示提供給虛擬磁碟機的名稱、登入識別碼，以及與虛擬磁碟機相關聯的提供者路徑。</span><span class="sxs-lookup"><span data-stu-id="45a72-116">Has parameters for the name to give the virtual drive, the login ID, and the provider path to associate with the virtual drive.</span></span>  
  
    2.  <span data-ttu-id="45a72-117">使用 `read-host` 提示使用者輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="45a72-117">Uses `read-host` to prompt the user for the password.</span></span>  
  
    3.  <span data-ttu-id="45a72-118">使用 `new-object` 建立認證物件。</span><span class="sxs-lookup"><span data-stu-id="45a72-118">Uses `new-object` to create a credentials object.</span></span>  
  
    4.  <span data-ttu-id="45a72-119">使用 `new-psdrive` 建立具有已提供認證的虛擬磁碟機。</span><span class="sxs-lookup"><span data-stu-id="45a72-119">Uses `new-psdrive` to create a virtual drive with the supplied credentials.</span></span>  
  
2.  <span data-ttu-id="45a72-120">呼叫此函數，以建立具有已提供認證的虛擬磁碟機。</span><span class="sxs-lookup"><span data-stu-id="45a72-120">Invoke the function to create a virtual drive with the supplied credentials.</span></span>  
  
### <a name="example-virtual-drive"></a><span data-ttu-id="45a72-121">範例 (虛擬磁碟機)</span><span class="sxs-lookup"><span data-stu-id="45a72-121">Example (Virtual Drive)</span></span>  
 <span data-ttu-id="45a72-122">此範例會建立名為 **sqldrive** 的函數，可讓您用來建立與指定之 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證登入和執行個體相關聯的虛擬磁碟機。</span><span class="sxs-lookup"><span data-stu-id="45a72-122">This example creates a function named **sqldrive** that you can use to create a virtual drive that is associated with the specified [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication login and instance.</span></span>  
  
 <span data-ttu-id="45a72-123">**sqldrive** 函數會提示您輸入登入的密碼，並且在您輸入時遮罩密碼。</span><span class="sxs-lookup"><span data-stu-id="45a72-123">The **sqldrive** function prompts you to enter the password for your login, masking the password as you type it in.</span></span> <span data-ttu-id="45a72-124">然後，每當您使用 [變更目錄] 命令 (`cd`) 使用虛擬磁片磁碟機名稱連線到路徑時，就會使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 您在建立磁片磁碟機時所提供的驗證登入認證來執行所有作業。</span><span class="sxs-lookup"><span data-stu-id="45a72-124">Then, whenever you use the change directory command (`cd`) to connect to a path by using the virtual drive name, all operations are performed by using the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication login credentials that you supplied when you created the drive.</span></span>  
  
```powershell
## Create a function that specifies the login and prompts for the password.  
  
function sqldrive  
{  
    param( [string]$name, [string]$login = "MyLogin", [string]$root = "SQLSERVER:\SQL\MyComputer\MyInstance" )  
    $pwd = Read-Host -AsSecureString -Prompt "Password"  
    $cred = New-Object System.Management.Automation.PSCredential -argumentlist $login, $pwd  
    New-PSDrive $name -PSProvider SqlServer -Root $root -Credential $cred -Scope 1  
}  
  
## Use the sqldrive function to create a SQLAuth virtual drive.  
sqldrive SQLAuth  
  
## CD to the virtual drive, which invokes the supplied authentication credentials.  
cd SQLAuth  
```  
  
##  <a name="sql-server-authentication-using-invoke-sqlcmd"></a><a name="SQLAuthInvSqlCmd"></a> <span data-ttu-id="45a72-125">使用 Invoke-Sqlcmd 的 SQL Server 驗證</span><span class="sxs-lookup"><span data-stu-id="45a72-125">SQL Server Authentication Using Invoke-Sqlcmd</span></span>  
 <span data-ttu-id="45a72-126">**搭配使用 Invoke-Sqlcmd 與 SQL Server 驗證**</span><span class="sxs-lookup"><span data-stu-id="45a72-126">**To use Invoke-Sqlcmd with SQL Server Authentication**</span></span>  
  
1.  <span data-ttu-id="45a72-127">使用 `-Username` 參數指定登入識別碼，而 `-Password` 參數則可指定相關聯的密碼。</span><span class="sxs-lookup"><span data-stu-id="45a72-127">Use the `-Username` parameter to specify a login ID, and the `-Password` parameter to specify the associated password.</span></span>  
  
### <a name="example-invoke-sqlcmd"></a><span data-ttu-id="45a72-128">範例 (Invoke-Sqlcmd)</span><span class="sxs-lookup"><span data-stu-id="45a72-128">Example (Invoke-Sqlcmd)</span></span>  
 <span data-ttu-id="45a72-129">此範例使用 read-host Cmdlet 提示使用者輸入密碼，然後使用 SQL Server 驗證進行連接。</span><span class="sxs-lookup"><span data-stu-id="45a72-129">This example uses the read-host cmdlet to prompt the user for a password, and then connects using SQL Server Authentication.</span></span>  
  
```powershell
## Prompt the user for their password.  
$pwd = Read-Host -AsSecureString -Prompt "Password"  
  
Invoke-Sqlcmd -Query "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance "MyComputer\MyInstance" -Username "MyLogin" -Password $pwd  
```  
  
## <a name="see-also"></a><span data-ttu-id="45a72-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45a72-130">See Also</span></span>  
 <span data-ttu-id="45a72-131">[SQL Server PowerShell](sql-server-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="45a72-131">[SQL Server PowerShell](sql-server-powershell.md) </span></span>  
 <span data-ttu-id="45a72-132">[SQL Server PowerShell 提供者](sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="45a72-132">[SQL Server PowerShell Provider](sql-server-powershell-provider.md) </span></span>  
 [<span data-ttu-id="45a72-133">Invoke-Sqlcmd 指令程式</span><span class="sxs-lookup"><span data-stu-id="45a72-133">Invoke-Sqlcmd cmdlet</span></span>](../database-engine/invoke-sqlcmd-cmdlet.md)  
