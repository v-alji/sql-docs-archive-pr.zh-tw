---
title: 載入 Windows PowerShell 中的 SMO 組件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 8ca42b69-da5a-47f4-9085-34e443f0e389
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9886d80c305dba251e6e3ab22ddb4dfb39783748
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686994"
---
# <a name="load-the-smo-assemblies-in-windows-powershell"></a><span data-ttu-id="d565f-102">載入 Windows PowerShell 中的 SMO 組件</span><span class="sxs-lookup"><span data-stu-id="d565f-102">Load the SMO Assemblies in Windows PowerShell</span></span>
  <span data-ttu-id="d565f-103">此主題描述如何在未使用 SQL Server PowerShell 提供者的 Windows PowerShell 指令碼中載入 SQL Server 管理物件 (SMO) 組件。</span><span class="sxs-lookup"><span data-stu-id="d565f-103">This topic describes how to load the SQL Server Management Object (SMO) assemblies in Windows PowerShell scripts that do not use the SQL Server PowerShell provider.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="d565f-104">開始之前</span><span class="sxs-lookup"><span data-stu-id="d565f-104">Before You Begin</span></span>  
 <span data-ttu-id="d565f-105">載入 SMO 組件的慣用機制是載入 `sqlps` 模組。</span><span class="sxs-lookup"><span data-stu-id="d565f-105">The preferred mechanism for loading the SMO assemblies is to load the `sqlps` module.</span></span> <span data-ttu-id="d565f-106">模組中所含的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 提供者會自動載入 SMO 組件，也會實作可擴充 PowerShell 指令碼中 SMO 物件使用性的功能。</span><span class="sxs-lookup"><span data-stu-id="d565f-106">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider included in the module automatically loads the SMO assemblies, and also implements features that extend the usefulness of the SMO objects in PowerShell scripts.</span></span>  
  
 <span data-ttu-id="d565f-107">有兩種情況您可能必須直接載入 SMO 組件：</span><span class="sxs-lookup"><span data-stu-id="d565f-107">There are two cases where you may need to load the SMO assemblies directly:</span></span>  
  
-   <span data-ttu-id="d565f-108">如果您的指令碼在第一個命令之前先參考 SMO 物件，而該命令會從 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 嵌入式管理單元參考提供者或指令程式。</span><span class="sxs-lookup"><span data-stu-id="d565f-108">If your script references a SMO object before the first command that references the provider or cmdlets from the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] snap-ins.</span></span>  
  
-   <span data-ttu-id="d565f-109">您想要從不使用提供者或 Cmdlet 的另一個語言 (例如 C# 或 Visual Basic) 移植 SMO 程式碼。</span><span class="sxs-lookup"><span data-stu-id="d565f-109">You want to port SMO code from another language, such as C# or Visual Basic, which does not use the provider or cmdlets.</span></span>  
  
## <a name="example-loading-the-sql-server-management-objects"></a><span data-ttu-id="d565f-110">範例：載入 SQL Server 管理物件</span><span class="sxs-lookup"><span data-stu-id="d565f-110">Example: Loading the SQL Server Management Objects</span></span>  
 <span data-ttu-id="d565f-111">下列程式碼會載入 SMO 組件：</span><span class="sxs-lookup"><span data-stu-id="d565f-111">The following code loads the SMO assemblies:</span></span>  
  
```powershell
# Loads the SQL Server Management Objects (SMO)  
  
$ErrorActionPreference = "Stop"  
  
$sqlpsreg = "HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.SqlServer.Management.PowerShell.sqlps"  
  
if (Get-ChildItem $sqlpsreg -ErrorAction "SilentlyContinue")  
{  
    throw "SQL Server Provider for Windows PowerShell is not installed."  
}  
else  
{  
    $item = Get-ItemProperty $sqlpsreg  
    $sqlpsPath = [System.IO.Path]::GetDirectoryName($item.Path)  
}  
  
$assemblylist =   
"Microsoft.SqlServer.Management.Common",  
"Microsoft.SqlServer.Smo",  
"Microsoft.SqlServer.Dmf ",  
"Microsoft.SqlServer.Instapi ",  
"Microsoft.SqlServer.SqlWmiManagement ",  
"Microsoft.SqlServer.ConnectionInfo ",  
"Microsoft.SqlServer.SmoExtended ",  
"Microsoft.SqlServer.SqlTDiagM ",  
"Microsoft.SqlServer.SString ",  
"Microsoft.SqlServer.Management.RegisteredServers ",  
"Microsoft.SqlServer.Management.Sdk.Sfc ",  
"Microsoft.SqlServer.SqlEnum ",  
"Microsoft.SqlServer.RegSvrEnum ",  
"Microsoft.SqlServer.WmiEnum ",  
"Microsoft.SqlServer.ServiceBrokerEnum ",  
"Microsoft.SqlServer.ConnectionInfoExtended ",  
"Microsoft.SqlServer.Management.Collector ",  
"Microsoft.SqlServer.Management.CollectorEnum",  
"Microsoft.SqlServer.Management.Dac",  
"Microsoft.SqlServer.Management.DacEnum",  
"Microsoft.SqlServer.Management.Utility"  
  
foreach ($asm in $assemblylist)  
{  
    $asm = [Reflection.Assembly]::LoadWithPartialName($asm)  
}  
  
Push-Location  
cd $sqlpsPath  
Update-FormatData -PrependPath SQLProvider.Format.ps1xml
Pop-Location  
```  
  
## <a name="see-also"></a><span data-ttu-id="d565f-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d565f-112">See Also</span></span>  
 [<span data-ttu-id="d565f-113">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="d565f-113">SQL Server PowerShell</span></span>](sql-server-powershell.md)  
