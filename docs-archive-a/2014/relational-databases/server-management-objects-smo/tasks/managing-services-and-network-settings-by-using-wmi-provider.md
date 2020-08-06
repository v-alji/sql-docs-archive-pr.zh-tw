---
title: 使用 WMI 提供者管理服務和網路設定 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- WMI provider [SMO]
- services [SQL Server], SMO
- network settings [SMO]
- monitoring [SMO]
ms.assetid: ef8c3986-1098-4f21-b03a-f1f6bdb51c26
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1cd373c46460ac95dbe81469eeaa4b3bf9548d68
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598254"
---
# <a name="managing-services-and-network-settings-by-using-wmi-provider"></a><span data-ttu-id="6c1f0-102">使用 WMI 提供者管理服務和網路設定</span><span class="sxs-lookup"><span data-stu-id="6c1f0-102">Managing Services and Network Settings by Using WMI Provider</span></span>
  <span data-ttu-id="6c1f0-103">WMI 提供者是 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Management Console (MMC) 用於管理 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務和網路通訊協定的已發行介面。</span><span class="sxs-lookup"><span data-stu-id="6c1f0-103">The WMI provider is a published interface that is used by [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Management Console (MMC) to manage the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] services and network protocols.</span></span> <span data-ttu-id="6c1f0-104">在 SMO 中，<xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> 物件表示 WMI 提供者。</span><span class="sxs-lookup"><span data-stu-id="6c1f0-104">In SMO, the <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> object represents the WMI Provider.</span></span>  
  
 <span data-ttu-id="6c1f0-105"><xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> 物件可獨立操作，不受使用 <xref:Microsoft.SqlServer.Management.Smo.Server> 物件對 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體所建立連接的影響，並會使用 Windows 認證連接到 WMI 服務。</span><span class="sxs-lookup"><span data-stu-id="6c1f0-105">The <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> object operates independently of the connection established with the <xref:Microsoft.SqlServer.Management.Smo.Server> object to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], and uses Windows credentials to connect to the WMI service.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c1f0-106">範例</span><span class="sxs-lookup"><span data-stu-id="6c1f0-106">Example</span></span>  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
 <span data-ttu-id="6c1f0-107">對於使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] wmi 提供者的程式，您必須包含 `Imports` 語句來限定 wmi 命名空間。</span><span class="sxs-lookup"><span data-stu-id="6c1f0-107">For programs that use the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] WMI provider, you must include the `Imports` statement to qualify the WMI namespace.</span></span> <span data-ttu-id="6c1f0-108">將陳述式插入至其他 `Imports` 陳述式之後、在應用程式中的任何宣告之前，例如：</span><span class="sxs-lookup"><span data-stu-id="6c1f0-108">Insert the statement after the other `Imports` statements, before any declarations in the application, such as:</span></span>  
  
 `Imports Microsoft.SqlServer.Management.Smo`  
  
 `Imports Microsoft.SqlServer.Management.Common`  
  
 `Imports Microsoft.SqlServer.Management.Smo.Wmi`  
  
## <a name="stopping-and-restarting-the-microsoft-sql-server-service-to-the-instance-of-sql-server-in-visual-basic"></a><span data-ttu-id="6c1f0-109">在 Visual Basic 中對 SQL Server 的執行個體停止和重新啟動 Microsoft SQL Server 服務</span><span class="sxs-lookup"><span data-stu-id="6c1f0-109">Stopping and Restarting the Microsoft SQL Server Service to the Instance of SQL Server in Visual Basic</span></span>  
 <span data-ttu-id="6c1f0-110">此程式碼範例示範如何使用 SMO <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> 物件停止和啟動服務。</span><span class="sxs-lookup"><span data-stu-id="6c1f0-110">This code example shows how to stop and start services by using the SMO <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> object.</span></span> <span data-ttu-id="6c1f0-111">如此可為 WMI 提供者提供組態管理的介面。</span><span class="sxs-lookup"><span data-stu-id="6c1f0-111">This provides an interface to the WMI Provider for Configuration Management.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBWMIService1](SMO How to#SMO_VBWMIService1)]  -->  
  
## <a name="enabling-a-server-protocol-using-a-urn-string-in-visual-basic"></a><span data-ttu-id="6c1f0-112">在 Visual Basic 中使用 URN 字串啟用伺服器通訊協定</span><span class="sxs-lookup"><span data-stu-id="6c1f0-112">Enabling a Server Protocol using a URN String in Visual Basic</span></span>  
 <span data-ttu-id="6c1f0-113">這個程式碼範例示範如何使用 URN 物件辨識伺服器通訊協定，然後啟用該通訊協定。</span><span class="sxs-lookup"><span data-stu-id="6c1f0-113">The code example shows how to identify a server protocol using a URN object, and then enable the protocol.</span></span>  
  
```vb
'This program must run with administrator privileges.  
        'Declare the ManagedComputer WMI interface.  
        Dim mc As New ManagedComputer()  
  
        'Create a URN object that represents the TCP server protocol.  
        Dim u As New Urn("ManagedComputer[@Name='V-ROBMA3']/ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Tcp']")  
  
        'Declare the serverProtocol variable and return the ServerProtocol object.  
        Dim sp As ServerProtocol  
        sp = mc.GetSmoObject(u)  
  
        'Enable the protocol.  
        sp.IsEnabled = True  
  
        'propagate back to the service  
        sp.Alter()  
```  
  
## <a name="enabling-a-server-protocol-using-a-urn-string-in-powershell"></a><span data-ttu-id="6c1f0-114">在 PowerShell 中使用 URN 字串啟用伺服器通訊協定</span><span class="sxs-lookup"><span data-stu-id="6c1f0-114">Enabling a Server Protocol using a URN String in PowerShell</span></span>  
 <span data-ttu-id="6c1f0-115">這個程式碼範例示範如何使用 URN 物件辨識伺服器通訊協定，然後啟用該通訊協定。</span><span class="sxs-lookup"><span data-stu-id="6c1f0-115">The code example shows how to identify a server protocol using a URN object, and then enable the protocol.</span></span>  
  
```powershell
#This example shows how to identify a server protocol using a URN object, and then enable the protocol  
#This program must run with administrator privileges.  
  
#Load the assembly containing the classes used in this example  
[reflection.assembly]::LoadWithPartialName("Microsoft.SqlServer.SqlWmiManagement")  
  
#Get a managed computer instance  
$mc = New-Object -TypeName Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer  
  
#Create a URN object that represents the TCP server protocol  
#Change 'MyPC' to the name of the your computer   
$urn = New-Object -TypeName Microsoft.SqlServer.Management.Sdk.Sfc.Urn -argumentlist "ManagedComputer[@Name='MyPC']/ServerInstance[@Name='MSSQLSERVER']/ServerProtocol[@Name='Tcp']"  
  
#Get the protocol object  
$sp = $mc.GetSmoObject($urn)  
  
#enable the protocol on the object  
$sp.IsEnabled = $true  
  
#propagate back to actual service  
$sp.Alter()  
```  
  
## <a name="starting-and-stopping-a-service-in-visual-c"></a><span data-ttu-id="6c1f0-116">在 Visual C# 中啟動和停止服務</span><span class="sxs-lookup"><span data-stu-id="6c1f0-116">Starting and stopping a service in Visual C#</span></span>  
 <span data-ttu-id="6c1f0-117">此程式碼範例示範如何停止和啟動 SQL Server 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6c1f0-117">The code example shows how to stop and start an instance of SQL Server.</span></span>  
  
```csharp
{   
   //Declare and create an instance of the ManagedComputer   
   //object that represents the WMI Provider services.   
   ManagedComputer mc;   
   mc = new ManagedComputer();   
   //Iterate through each service registered with the WMI Provider.   
  
   foreach (Service svc in mc.Services)  
   {   
      Console.WriteLine(svc.Name);   
   }   
//Reference the Microsoft SQL Server service.   
  Service Mysvc = mc.Services["MSSQLSERVER"];   
//Stop the service if it is running and report on the status  
// continuously until it has stopped.   
   if (Mysvc.ServiceState == ServiceState.Running) {   
      Mysvc.Stop();   
      Console.WriteLine(string.Format("{0} service state is {1}", Mysvc.Name, Mysvc.ServiceState));   
      while (!(string.Format("{0}", Mysvc.ServiceState) == "Stopped")) {   
         Console.WriteLine(string.Format("{0}", Mysvc.ServiceState));   
          Mysvc.Refresh();   
      }   
      Console.WriteLine(string.Format("{0} service state is {1}", Mysvc.Name, Mysvc.ServiceState));   
//Start the service and report on the status continuously   
//until it has started.   
      Mysvc.Start();   
      while (!(string.Format("{0}", Mysvc.ServiceState) == "Running")) {   
         Console.WriteLine(string.Format("{0}", Mysvc.ServiceState));   
         Mysvc.Refresh();   
      }   
      Console.WriteLine(string.Format("{0} service state is {1}", Mysvc.Name, Mysvc.ServiceState));  
      Console.ReadLine();  
   }   
   else {   
      Console.WriteLine("SQL Server service is not running.");  
      Console.ReadLine();  
   }   
}  
```  
  
## <a name="starting-and-stopping-a-service-in-powershell"></a><span data-ttu-id="6c1f0-118">在 PowerShell 中啟動和停止服務</span><span class="sxs-lookup"><span data-stu-id="6c1f0-118">Starting and stopping a service in PowerShell</span></span>  
 <span data-ttu-id="6c1f0-119">此程式碼範例示範如何停止和啟動 SQL Server 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6c1f0-119">The code example shows how to stop and start an instance of SQL Server.</span></span>  
  
```powershell
#Load the assembly containing the objects used in this example  
[reflection.assembly]::LoadWithPartialName("Microsoft.SqlServer.SqlWmiManagement")  
  
#Get a managed computer instance  
$mc = New-Object -TypeName Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer  
  
#List out all sql server instnces running on this mc  
foreach ($Item in $mc.Services){$Item.Name}  
  
#Get the default sql server datbase engine service  
$svc = $mc.Services["MSSQLSERVER"]  
  
# for stopping and starting services PowerShell must run as administrator  
  
#Stop this service  
$svc.Stop()  
$svc.Refresh()  
while ($svc.ServiceState -ne "Stopped")  
{  
$svc.Refresh()  
$svc.ServiceState  
}  
"Service" + $svc.Name + " is now stopped"  
"Starting " + $svc.Name  
$svc.Start()  
$svc.Refresh()  
while ($svc.ServiceState -ne "Running")  
{  
$svc.Refresh()  
$svc.ServiceState  
}  
$svc.ServiceState  
"Service" + $svc.Name + "is now started"
```  
  
## <a name="see-also"></a><span data-ttu-id="6c1f0-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c1f0-120">See Also</span></span>  
 [<span data-ttu-id="6c1f0-121">組態管理的 WMI 提供者概念</span><span class="sxs-lookup"><span data-stu-id="6c1f0-121">WMI Provider for Configuration Management Concepts</span></span>](../../wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
