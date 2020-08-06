---
title: 設定 SMO 中的 SQL Server |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server, configuring
- configuration options [SMO]
ms.assetid: 0a372643-15cb-45a7-8665-04f1215df8ed
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6da1bca0aec650c01553b42bc2f3628b0bf7282e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707358"
---
# <a name="configuring-sql-server-in-smo"></a><span data-ttu-id="74286-102">在 SMO 中設定 SQL Server</span><span class="sxs-lookup"><span data-stu-id="74286-102">Configuring SQL Server in SMO</span></span>
  <span data-ttu-id="74286-103">在 SMO 中，物件 <xref:Microsoft.SqlServer.Management.Smo.Information> 、 <xref:Microsoft.SqlServer.Management.Smo.Settings> 物件、物件 <xref:Microsoft.SqlServer.Management.Smo.UserOptions> 和物件都 <xref:Microsoft.SqlServer.Management.Smo.Configuration> 包含實例的設定和資訊 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="74286-103">In SMO, the <xref:Microsoft.SqlServer.Management.Smo.Information> object, the <xref:Microsoft.SqlServer.Management.Smo.Settings> object, the <xref:Microsoft.SqlServer.Management.Smo.UserOptions> object, and the <xref:Microsoft.SqlServer.Management.Smo.Configuration> object contain settings and information for the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="74286-104">具有多個描述已安裝之執行個體行為的屬性。</span><span class="sxs-lookup"><span data-stu-id="74286-104">has numerous properties that describe the behavior of the installed instance.</span></span> <span data-ttu-id="74286-105">這些屬性描述啟動選項、伺服器預設值、檔案和目錄、系統和處理資訊、產品和版本、連接資訊、記憶體選項、語言和定序選取項目，以及驗證模式。</span><span class="sxs-lookup"><span data-stu-id="74286-105">The properties describe the startup options, the server defaults, files and directories, system and processor information, product and versions, connection information, memory options, language and collation selections, and the authentication mode.</span></span>  
  
## <a name="sql-server-configuration"></a><span data-ttu-id="74286-106">SQL Server 組態</span><span class="sxs-lookup"><span data-stu-id="74286-106">SQL Server Configuration</span></span>  
 <span data-ttu-id="74286-107"><xref:Microsoft.SqlServer.Management.Smo.Information> 物件屬性包含有關 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體 (例如處理器和平台) 的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="74286-107">The <xref:Microsoft.SqlServer.Management.Smo.Information> object properties contain information about the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], such as processor and platform.</span></span>  
  
 <span data-ttu-id="74286-108"><xref:Microsoft.SqlServer.Management.Smo.Settings> 物件屬性包含有關 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="74286-108">The <xref:Microsoft.SqlServer.Management.Smo.Settings> object properties contain information about the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="74286-109">除了郵件設定檔和伺服器帳戶外，您也可以修改預設的資料庫檔案和目錄。</span><span class="sxs-lookup"><span data-stu-id="74286-109">The default database file and directory can be modified in addition to the Mail Profile and the Server Account.</span></span> <span data-ttu-id="74286-110">在連接持續時間會保留這些屬性。</span><span class="sxs-lookup"><span data-stu-id="74286-110">These properties remain for the duration of the connection.</span></span>  
  
 <span data-ttu-id="74286-111"><xref:Microsoft.SqlServer.Management.Smo.UserOptions> 物件屬性包含目前與算術、ANSI 標準和交易相關之連接行為的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="74286-111">The <xref:Microsoft.SqlServer.Management.Smo.UserOptions> object properties contain information about the current connections behavior relating to arithmetic, ANSI standards, and transactions.</span></span>  
  
 <span data-ttu-id="74286-112">此外也有一組由 <xref:Microsoft.SqlServer.Management.Smo.Configuration> 物件所代表的組態選項。</span><span class="sxs-lookup"><span data-stu-id="74286-112">There is also a set of configuration options that is represented by the <xref:Microsoft.SqlServer.Management.Smo.Configuration> object.</span></span> <span data-ttu-id="74286-113">其中包含一組屬性，代表可由 `sp_configure` 預存程序修改的選項。</span><span class="sxs-lookup"><span data-stu-id="74286-113">It contains a set of properties that represent the options that can be modified by the `sp_configure` stored procedure.</span></span> <span data-ttu-id="74286-114">[**優先權提升**]、[復原**間隔**] 和 [**網路封包大小**] 等選項會控制實例的效能 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="74286-114">Options such as **Priority Boost**, **Recovery Interval** and **Network Packet Size**control the performance of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="74286-115">這其中許多選項都可以動態變更，但在某些情況下，當 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的執行個體重新啟動時，會先設定值然後再加以變更。</span><span class="sxs-lookup"><span data-stu-id="74286-115">Many of these options can be changed dynamically, but in some cases the value is first configured and then changed when the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is restarted.</span></span>  
  
 <span data-ttu-id="74286-116">每個組態選項都有 <xref:Microsoft.SqlServer.Management.Smo.Configuration> 物件屬性。</span><span class="sxs-lookup"><span data-stu-id="74286-116">There is a <xref:Microsoft.SqlServer.Management.Smo.Configuration> object property for every configuration option.</span></span> <span data-ttu-id="74286-117">您可以使用 <xref:Microsoft.SqlServer.Management.Smo.ConfigProperty> 物件來修改全域組態設定。</span><span class="sxs-lookup"><span data-stu-id="74286-117">Using the <xref:Microsoft.SqlServer.Management.Smo.ConfigProperty> object you can modify the global configuration setting.</span></span> <span data-ttu-id="74286-118">許多屬性都擁有最大和最小值，這些值也會儲存為 <xref:Microsoft.SqlServer.Management.Smo.ConfigProperty> 屬性。</span><span class="sxs-lookup"><span data-stu-id="74286-118">Many properties have maximum and minimum values that are also stored as <xref:Microsoft.SqlServer.Management.Smo.ConfigProperty> properties.</span></span> <span data-ttu-id="74286-119">這些屬性需要 <xref:Microsoft.SqlServer.Management.Smo.ConfigurationBase.Alter%2A> 方法才能認可對實例的變更 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="74286-119">These properties require the <xref:Microsoft.SqlServer.Management.Smo.ConfigurationBase.Alter%2A> method to commit the change to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="74286-120"><xref:Microsoft.SqlServer.Management.Smo.Configuration> 物件中的所有組態選項都必須由系統管理員變更。</span><span class="sxs-lookup"><span data-stu-id="74286-120">All of the configuration options in the <xref:Microsoft.SqlServer.Management.Smo.Configuration> object must be changed by the system administrator.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="74286-121">範例</span><span class="sxs-lookup"><span data-stu-id="74286-121">Examples</span></span>  
 <span data-ttu-id="74286-122">在下列的程式碼範例中，您必須選取用於建立應用程式的程式設計環境、程式設計範本和程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="74286-122">For the following code examples, you will have to select the programming environment, programming template and the programming language to create your application.</span></span> <span data-ttu-id="74286-123">如需詳細資訊，請參閱[在 Visual Studio .net 中建立 VISUAL BASIC SMO 專案](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)和[在 Visual Studio .Net 中建立 VISUAL C&#35; SMO 專案](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。</span><span class="sxs-lookup"><span data-stu-id="74286-123">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) and [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="modifying-sql-server-configuration-options-in-visual-basic"></a><span data-ttu-id="74286-124">在 Visual Basic 中修改 SQL Server 組態選項</span><span class="sxs-lookup"><span data-stu-id="74286-124">Modifying SQL Server Configuration Options in Visual Basic</span></span>  
 <span data-ttu-id="74286-125">此程式碼範例會顯示如何在 Visual Basic .NET 中更新組態選項，</span><span class="sxs-lookup"><span data-stu-id="74286-125">The code example shows how to update a configuration option in Visual Basic .NET.</span></span> <span data-ttu-id="74286-126">也會擷取並顯示有關指定組態選項最大及最小值的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="74286-126">It also retrieves and displays information about maximum and minimum values for the specified configuration option.</span></span> <span data-ttu-id="74286-127">最後，此程式會通知使用者變更是否是以動態方式進行，或者在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的執行個體重新啟動之前都會儲存變更。</span><span class="sxs-lookup"><span data-stu-id="74286-127">Finally, the program informs the user if the change has been made dynamically, or if it is stored until the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is restarted.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBConfigure2](SMO How to#SMO_VBConfigure2)]  -->  
  
## <a name="modifying-sql-server-settings-in-visual-basic"></a><span data-ttu-id="74286-128">在 Visual Basic 中修改 SQL Server 設定</span><span class="sxs-lookup"><span data-stu-id="74286-128">Modifying SQL Server Settings in Visual Basic</span></span>  
 <span data-ttu-id="74286-129">此程式碼範例會在和中顯示實例的相關資訊 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <xref:Microsoft.SqlServer.Management.Smo.Information> <xref:Microsoft.SqlServer.Management.Smo.Settings> ，並修改 <xref:Microsoft.SqlServer.Management.Smo.Settings> 和 <xref:Microsoft.SqlServer.Management.Smo.UserOptions> 物件屬性中的設定。</span><span class="sxs-lookup"><span data-stu-id="74286-129">The code example displays information about the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in <xref:Microsoft.SqlServer.Management.Smo.Information> and <xref:Microsoft.SqlServer.Management.Smo.Settings>, and modifies settings in <xref:Microsoft.SqlServer.Management.Smo.Settings> and <xref:Microsoft.SqlServer.Management.Smo.UserOptions>object properties.</span></span>  
  
 <span data-ttu-id="74286-130">在此範例中，<xref:Microsoft.SqlServer.Management.Smo.UserOptions> 物件和 <xref:Microsoft.SqlServer.Management.Smo.Settings> 物件兩者都擁有 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="74286-130">In the example the <xref:Microsoft.SqlServer.Management.Smo.UserOptions> object and the <xref:Microsoft.SqlServer.Management.Smo.Settings> object both have an <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> method.</span></span> <span data-ttu-id="74286-131">您可以個別地為這些執行 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="74286-131">You can run the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> methods for these individually.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBConfigure1](SMO How to#SMO_VBConfigure1)]  -->  
  
## <a name="modifying-sql-server-settings-in-visual-c"></a><span data-ttu-id="74286-132">在 Visual C# 中修改 SQL Server 設定</span><span class="sxs-lookup"><span data-stu-id="74286-132">Modifying SQL Server Settings in Visual C#</span></span>  
 <span data-ttu-id="74286-133">此程式碼範例會在和中顯示實例的相關資訊 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <xref:Microsoft.SqlServer.Management.Smo.Information> <xref:Microsoft.SqlServer.Management.Smo.Settings> ，並修改 <xref:Microsoft.SqlServer.Management.Smo.Settings> 和 <xref:Microsoft.SqlServer.Management.Smo.UserOptions> 物件屬性中的設定。</span><span class="sxs-lookup"><span data-stu-id="74286-133">The code example displays information about the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in <xref:Microsoft.SqlServer.Management.Smo.Information> and <xref:Microsoft.SqlServer.Management.Smo.Settings>, and modifies settings in <xref:Microsoft.SqlServer.Management.Smo.Settings> and <xref:Microsoft.SqlServer.Management.Smo.UserOptions>object properties.</span></span>  
  
 <span data-ttu-id="74286-134">在此範例中，<xref:Microsoft.SqlServer.Management.Smo.UserOptions> 物件和 <xref:Microsoft.SqlServer.Management.Smo.Settings> 物件兩者都擁有 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="74286-134">In the example the <xref:Microsoft.SqlServer.Management.Smo.UserOptions> object and the <xref:Microsoft.SqlServer.Management.Smo.Settings> object both have an <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> method.</span></span> <span data-ttu-id="74286-135">您可以個別地為這些執行 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="74286-135">You can run the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> methods for these individually.</span></span>  
  
 `//Connect to the local, default instance of SQL Server.`  
  
```csharp
{  
            Server srv = new Server();  
            //Display all the configuration options.   
  
            foreach (ConfigProperty p in srv.Configuration.Properties)  
            {  
                Console.WriteLine(p.DisplayName);  
            }  
            Console.WriteLine("There are " + srv.Configuration.Properties.Count.ToString() + " configuration options.");  
            //Display the maximum and minimum values for ShowAdvancedOptions.   
            int min = 0;  
            int max = 0;  
            min = srv.Configuration.ShowAdvancedOptions.Minimum;  
            max = srv.Configuration.ShowAdvancedOptions.Maximum;  
            Console.WriteLine("Minimum and Maximum values are " + min + " and " + max + ".");  
            //Modify the value of ShowAdvancedOptions and run the Alter method.   
            srv.Configuration.ShowAdvancedOptions.ConfigValue = 0;  
            srv.Configuration.Alter();  
            //Display when the change takes place according to the IsDynamic property.   
            if (srv.Configuration.ShowAdvancedOptions.IsDynamic == true)  
            {  
                Console.WriteLine("Configuration option has been updated.");  
            }  
            else  
            {  
                Console.WriteLine("Configuration option will be updated when SQL Server is restarted.");  
            }  
        }  
```  
  
## <a name="modifying-sql-server-settings-in-powershell"></a><span data-ttu-id="74286-136">在 PowerShell 中修改 SQL Server 設定</span><span class="sxs-lookup"><span data-stu-id="74286-136">Modifying SQL Server Settings in PowerShell</span></span>  
 <span data-ttu-id="74286-137">此程式碼範例會在和中顯示實例的相關資訊 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <xref:Microsoft.SqlServer.Management.Smo.Information> <xref:Microsoft.SqlServer.Management.Smo.Settings> ，並修改 <xref:Microsoft.SqlServer.Management.Smo.Settings> 和 <xref:Microsoft.SqlServer.Management.Smo.UserOptions> 物件屬性中的設定。</span><span class="sxs-lookup"><span data-stu-id="74286-137">The code example displays information about the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in <xref:Microsoft.SqlServer.Management.Smo.Information> and <xref:Microsoft.SqlServer.Management.Smo.Settings>, and modifies settings in <xref:Microsoft.SqlServer.Management.Smo.Settings> and <xref:Microsoft.SqlServer.Management.Smo.UserOptions>object properties.</span></span>  
  
 <span data-ttu-id="74286-138">在此範例中，<xref:Microsoft.SqlServer.Management.Smo.UserOptions> 物件和 <xref:Microsoft.SqlServer.Management.Smo.Settings> 物件兩者都擁有 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="74286-138">In the example the <xref:Microsoft.SqlServer.Management.Smo.UserOptions> object and the <xref:Microsoft.SqlServer.Management.Smo.Settings> object both have an <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> method.</span></span> <span data-ttu-id="74286-139">您可以個別地為這些執行 <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="74286-139">You can run the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> methods for these individually.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\  
$srv = Get-Item default  
  
#Display information about the instance of SQL Server in Information and Settings.  
"OS Version = " + $srv.Information.OSVersion  
"State = "+ $srv.Settings.State.ToString()  
  
#Display information specific to the current user in UserOptions.  
"Quoted Identifier support = " + $srv.UserOptions.QuotedIdentifier  
  
#Modify server settings in Settings.  
$srv.Settings.LoginMode = [Microsoft.SqlServer.Management.SMO.ServerLoginMode]::Integrated  
  
#Modify settings specific to the current connection in UserOptions.  
$srv.UserOptions.AbortOnArithmeticErrors = $true  
  
#Run the Alter method to make the changes on the instance of SQL Server.  
$srv.Alter()  
```  
  
## <a name="modifying-sql-server-configuration-options-in-powershell"></a><span data-ttu-id="74286-140">在 PowerShell 中修改 SQL Server 組態選項</span><span class="sxs-lookup"><span data-stu-id="74286-140">Modifying SQL Server Configuration Options in PowerShell</span></span>  
 <span data-ttu-id="74286-141">此程式碼範例會顯示如何在 Visual Basic .NET 中更新組態選項，</span><span class="sxs-lookup"><span data-stu-id="74286-141">The code example shows how to update a configuration option in Visual Basic .NET.</span></span> <span data-ttu-id="74286-142">也會擷取並顯示有關指定組態選項最大及最小值的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="74286-142">It also retrieves and displays information about maximum and minimum values for the specified configuration option.</span></span> <span data-ttu-id="74286-143">最後，此程式會通知使用者變更是否是以動態方式進行，或者在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的執行個體重新啟動之前都會儲存變更。</span><span class="sxs-lookup"><span data-stu-id="74286-143">Finally, the program informs the user if the change has been made dynamically, or if it is stored until the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is restarted.</span></span>  
  
```powershell
#Get a server object which corresponds to the default instance replace LocalMachine with the physical server  
cd \sql\LocalMachine  
$svr = Get-Item default  
  
#enumerate its properties  
foreach ($Item in $Svr.Configuration.Properties)   
{  
 $Item.DisplayName  
}  
  
"There are " + $svr.Configuration.Properties.Count.ToString() + " configuration options."  
  
#Display the maximum and minimum values for ShowAdvancedOptions.  
$min = $svr.Configuration.ShowAdvancedOptions.Minimum  
$max = $svr.Configuration.ShowAdvancedOptions.Maximum  
"Minimum and Maximum values are " + $min.ToString() + " and " + $max.ToString() + "."  
  
#Modify the value of ShowAdvancedOptions and run the Alter method.  
$svr.Configuration.ShowAdvancedOptions.ConfigValue = 0  
$svr.Configuration.Alter()  
  
#Display when the change takes place according to the IsDynamic property.  
If ($svr.Configuration.ShowAdvancedOptions.IsDynamic -eq $true)  
 {
   "Configuration option has been updated."  
 }  
Else  
 {  
    "Configuration option will be updated when SQL Server is restarted."  
 }  
```  
