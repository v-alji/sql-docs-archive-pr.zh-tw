---
title: 部署 CLR 資料庫物件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- deployment script [CLR integration]
- common language runtime [SQL Server], deploying
- deploying assemblies [CLR integration]
- deploying [CLR integration]
ms.assetid: 00752573-3367-41a7-af98-7b7a29e8e2f2
author: rothja
ms.author: jroth
ms.openlocfilehash: daf069bc37a58a879224b2217f4dcb700c1d6e99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584571"
---
# <a name="deploying-clr-database-objects"></a><span data-ttu-id="d0730-102">部署 CLR 資料庫物件</span><span class="sxs-lookup"><span data-stu-id="d0730-102">Deploying CLR Database Objects</span></span>
  <span data-ttu-id="d0730-103">部署是指您用來散發即將在其他電腦上安裝和執行之已完成應用程式或模組的程序。</span><span class="sxs-lookup"><span data-stu-id="d0730-103">Deployment is the process by which you distribute a finished application or module to be installed and run on another computer.</span></span> <span data-ttu-id="d0730-104">您可以使用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio 來開發 Common Language Runtime (CLR) 資料庫物件並將它們部署至測試伺服器。</span><span class="sxs-lookup"><span data-stu-id="d0730-104">Using [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio, you can develop common language runtime (CLR) database objects and deploy them to a test server.</span></span> <span data-ttu-id="d0730-105">或者，您也可以使用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework 轉散發檔案 (而非 Visual Studio) 來編譯 Managed 資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="d0730-105">Alternatively, the managed database objects can also be compiled with the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework redistribution files, instead of Visual Studio.</span></span> <span data-ttu-id="d0730-106">一旦編譯完成之後，您就可以使用 Visual Studio 或 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式，將包含 CLR 資料庫物件的組件部署至測試伺服器。</span><span class="sxs-lookup"><span data-stu-id="d0730-106">Once compiled, the assemblies containing the CLR database objects can then be deployed to a test server using Visual Studio or [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="d0730-107">請注意，Visual Studio .NET 2003 無法用於 CLR 整合程式設計或部署。</span><span class="sxs-lookup"><span data-stu-id="d0730-107">Note that Visual Studio .NET 2003 cannot be used for CLR integration programming or deployment.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="d0730-108">包含預先安裝的 .NET Framework，而且 Visual Studio .NET 2003 無法使用 .NET Framework 2.0 組件。</span><span class="sxs-lookup"><span data-stu-id="d0730-108">includes the .NET Framework pre-installed, and Visual Studio .NET 2003 cannot use the .NET Framework 2.0 assemblies.</span></span>  
  
 <span data-ttu-id="d0730-109">一旦 CLR 方法已經在測試伺服器上測試並驗證之後，您就可以使用部署指令碼，將它們散發至實際伺服器。</span><span class="sxs-lookup"><span data-stu-id="d0730-109">Once the CLR methods have been tested and verified on the test server, they can be distributed to production servers using a deployment script.</span></span> <span data-ttu-id="d0730-110">您可以手動產生部署指令碼，也可以使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 來產生部署指令碼 (請參閱本主題後面的程序)。</span><span class="sxs-lookup"><span data-stu-id="d0730-110">The deployment script can be generated manually, or by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] (see the procedure later in this topic).</span></span>  
  
 <span data-ttu-id="d0730-111">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中，CLR 整合功能預設是關閉的，而且您必須啟用此功能才能使用 CLR 組件。</span><span class="sxs-lookup"><span data-stu-id="d0730-111">The CLR integration feature is turned off by default in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and must be enabled in order to use CLR assemblies.</span></span> <span data-ttu-id="d0730-112">如需詳細資訊，請參閱 [Enabling CLR Integration](clr-integration-enabling.md)。</span><span class="sxs-lookup"><span data-stu-id="d0730-112">For more information, see [Enabling CLR Integration](clr-integration-enabling.md).</span></span>  
  
## <a name="deploying-the-assembly-to-the-test-server"></a><span data-ttu-id="d0730-113">將組件部署至測試伺服器</span><span class="sxs-lookup"><span data-stu-id="d0730-113">Deploying the Assembly to the Test Server</span></span>  
 <span data-ttu-id="d0730-114">您可以使用 Visual Studio 來開發 CLR 函數、程序、觸發程序、使用者定義型別 (UDT) 或使用者定義彙總 (UDA)，然後將它們部署至測試伺服器。</span><span class="sxs-lookup"><span data-stu-id="d0730-114">Using Visual Studio, you can develop CLR functions, procedures, triggers, user-defined types (UDTs), or user-defined aggregates (UDAs), and deploy them to a test server.</span></span> <span data-ttu-id="d0730-115">您也可以使用 .NET Framework 轉散發檔案隨附的命令列編譯器 (例如 csc.exe 和 vbc.exe) 來編譯這些 Managed 資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="d0730-115">These managed database objects can also be compiled with the command line compilers, such as csc.exe and vbc.exe, included with the .NET Framework redistribution files.</span></span> <span data-ttu-id="d0730-116">Visual Studio Integrated Development Environment 並非開發 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 之 Managed 資料庫物件所需的條件。</span><span class="sxs-lookup"><span data-stu-id="d0730-116">The Visual Studio Integrated Development Environment is not required to develop managed database objects for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="d0730-117">請確定已解決所有編譯器錯誤和警告。</span><span class="sxs-lookup"><span data-stu-id="d0730-117">Make sure that all compiler errors and warnings are resolved.</span></span> <span data-ttu-id="d0730-118">然後，您就可以使用 Visual Studio 或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 陳述式，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 資料庫中註冊包含 CLR 常式的組件。</span><span class="sxs-lookup"><span data-stu-id="d0730-118">The assemblies containing the CLR routines can then be registered in a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database using Visual Studio or [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d0730-119">您必須在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體上啟用 TCP/IP 網路通訊協定，才能針對遠端開發、偵錯和開發使用 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="d0730-119">The TCP/IP network protocol must be enabled on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance in order to use [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio for remote development, debugging, and development.</span></span> <span data-ttu-id="d0730-120">如需在伺服器上啟用 TCP/IP 通訊協定的詳細資訊，請參閱[設定用戶端通訊協定](../../database-engine/configure-windows/configure-client-protocols.md)。</span><span class="sxs-lookup"><span data-stu-id="d0730-120">For more information about enabling TCP/IP protocol on the server, see [Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md).</span></span>  
  
#### <a name="to-deploy-the-assembly-using-visual-studio"></a><span data-ttu-id="d0730-121">使用 Visual Studio 來部署組件</span><span class="sxs-lookup"><span data-stu-id="d0730-121">To deploy the assembly using Visual Studio</span></span>  
  
1.  <span data-ttu-id="d0730-122">**Build** \<project name> 從 [**建立**] 功能表中選取 [組建] 來建立專案。</span><span class="sxs-lookup"><span data-stu-id="d0730-122">Build the project by selecting **Build** \<project name> from the **Build** menu.</span></span>  
  
2.  <span data-ttu-id="d0730-123">解決所有建立錯誤和警告，然後再將組件部署至測試伺服器。</span><span class="sxs-lookup"><span data-stu-id="d0730-123">Resolve all build errors and warnings before deploying the assembly to the test server.</span></span>  
  
3.  <span data-ttu-id="d0730-124">從 [**建立**] 功能表中選取 [**部署**]。</span><span class="sxs-lookup"><span data-stu-id="d0730-124">Select **Deploy** from the **Build** menu.</span></span> <span data-ttu-id="d0730-125">然後，系統就會在第一次於 Visual Studio 中建立 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 專案時指定的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體和資料庫中註冊此組件。</span><span class="sxs-lookup"><span data-stu-id="d0730-125">The assembly will then be registered in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance and database specified when the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] project was first created in Visual Studio.</span></span>  
  
#### <a name="to-deploy-the-assembly-using-transact-sql"></a><span data-ttu-id="d0730-126">使用 Transact-SQL 來部署組件</span><span class="sxs-lookup"><span data-stu-id="d0730-126">To deploy the assembly using Transact-SQL</span></span>  
  
1.  <span data-ttu-id="d0730-127">使用 .NET Framework 隨附的命令列編譯器來編譯來源檔案的組件。</span><span class="sxs-lookup"><span data-stu-id="d0730-127">Compile the assembly from the source file using the command line compilers included with the .NET Framework.</span></span>  
  
2.  <span data-ttu-id="d0730-128">若為 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# 來源檔案：</span><span class="sxs-lookup"><span data-stu-id="d0730-128">For [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# source files:</span></span>  
  
3.  `csc /target:library C:\helloworld.cs`  
  
4.  <span data-ttu-id="d0730-129">若為 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic 來源檔案：</span><span class="sxs-lookup"><span data-stu-id="d0730-129">For [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic source files:</span></span>  
  
 `vbc /target:library C:\helloworld.vb`  
  
 <span data-ttu-id="d0730-130">這些命令會啟動 Visual C# 或 Visual Basic 編譯器，並使用 `/target` 選項來指定要建立程式庫 DLL。</span><span class="sxs-lookup"><span data-stu-id="d0730-130">These commands launch the Visual C# or Visual Basic compiler using the `/target` option to specify building a library DLL.</span></span>  
  
1.  <span data-ttu-id="d0730-131">解決所有建立錯誤和警告，然後再將組件部署至測試伺服器。</span><span class="sxs-lookup"><span data-stu-id="d0730-131">Resolve all build errors and warnings before deploying the assembly to the test server.</span></span>  
  
2.  <span data-ttu-id="d0730-132">在測試伺服器上開啟 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d0730-132">Open [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] on the test server.</span></span> <span data-ttu-id="d0730-133">建立連接至適當測試資料庫 (例如 AdventureWorks) 的新查詢。</span><span class="sxs-lookup"><span data-stu-id="d0730-133">Create a new query, connected to a suitable test database (such as AdventureWorks).</span></span>  
  
3.  <span data-ttu-id="d0730-134">將下列 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 加入至查詢，藉以在伺服器中建立組件。</span><span class="sxs-lookup"><span data-stu-id="d0730-134">Create the assembly in the server by adding the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] to the query.</span></span>  
  
 `CREATE ASSEMBLY HelloWorld from 'c:\helloworld.dll' WITH PERMISSION_SET = SAFE;`  
  
1.  <span data-ttu-id="d0730-135">然後，您必須在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的執行個體中建立程序、函數、彙總、使用者定義型別或觸發程序。</span><span class="sxs-lookup"><span data-stu-id="d0730-135">The procedure, function, aggregate, user-defined type, or trigger must then be created in the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d0730-136">如果 `HelloWorld` 組件在 `HelloWorld` 類別中包含名為 `Procedures` 的方法，您就可以將下列 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 加入至查詢，以便在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中建立稱為 `hello` 的程序。</span><span class="sxs-lookup"><span data-stu-id="d0730-136">If the `HelloWorld` assembly contains a method named `HelloWorld` in the `Procedures` class, the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] can be added to the query to create a procedure called `hello` in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 `CREATE PROCEDURE hello`  
  
 `AS`  
  
 `EXTERNAL NAME HelloWorld.Procedures.HelloWorld`  
  
 <span data-ttu-id="d0730-137">如需在中建立不同類型的 managed 資料庫物件的詳細資訊 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，請參閱[Clr 使用者定義函數](../clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)、 [clr 使用者定義匯總](../clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md)、 [Clr 使用者定義類型](../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)、 [clr 預存程式](../../database-engine/dev-guide/clr-stored-procedures.md)和[clr 觸發](../../database-engine/dev-guide/clr-triggers.md)程式。</span><span class="sxs-lookup"><span data-stu-id="d0730-137">For more information about creating the different types of managed database objects in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], see [CLR User-Defined Functions](../clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md), [CLR User-Defined Aggregates](../clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md), [CLR User-Defined Types](../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md), [CLR Stored Procedures](../../database-engine/dev-guide/clr-stored-procedures.md), and [CLR Triggers](../../database-engine/dev-guide/clr-triggers.md).</span></span>  
  
## <a name="deploying-the-assembly-to-production-servers"></a><span data-ttu-id="d0730-138">將組件部署至實際伺服器</span><span class="sxs-lookup"><span data-stu-id="d0730-138">Deploying the Assembly to Production Servers</span></span>  
 <span data-ttu-id="d0730-139">一旦 CLR 資料庫物件已經在測試伺服器上測試並驗證之後，您就可以將它們散發至實際伺服器。</span><span class="sxs-lookup"><span data-stu-id="d0730-139">Once the CLR database objects have been tested and verified on the test server, they can be distributed to production servers.</span></span> <span data-ttu-id="d0730-140">如需有關如何對 managed 資料庫物件進行偵錯工具的詳細資訊，請參閱[偵錯工具 CLR 資料庫物件](debugging-clr-database-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="d0730-140">For more information about debugging managed database objects, see [Debugging CLR Database Objects](debugging-clr-database-objects.md).</span></span>  
  
 <span data-ttu-id="d0730-141">Managed 資料庫物件的部署作業與一般資料庫物件 (資料表、[!INCLUDE[tsql](../../../includes/tsql-md.md)] 常式等項目) 的部署作業很相似。</span><span class="sxs-lookup"><span data-stu-id="d0730-141">The deployment of managed database objects is similar to that of regular database objects (tables, [!INCLUDE[tsql](../../../includes/tsql-md.md)] routines, and so on).</span></span> <span data-ttu-id="d0730-142">您可以使用部署指令碼，將包含 CLR 資料庫物件的組件部署至其他伺服器。</span><span class="sxs-lookup"><span data-stu-id="d0730-142">The assemblies containing the CLR database objects can be deployed to other servers using a deployment script.</span></span> <span data-ttu-id="d0730-143">您可以使用 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] 的「產生指令碼」功能來建立部署指令碼。</span><span class="sxs-lookup"><span data-stu-id="d0730-143">The deployment script can be built by using the "Generate Scripts" functionality of [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="d0730-144">此外，您也可以手動建立部署指令碼，或先使用「產生指令碼」來建立部署指令碼，然後再手動進行更改。</span><span class="sxs-lookup"><span data-stu-id="d0730-144">The deployment script can also be built manually, or built using "Generate Scripts" and manually altered.</span></span> <span data-ttu-id="d0730-145">一旦部署指令碼已經建立完成之後，您就可以在其他 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體上執行此指令碼，以便部署 Managed 資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="d0730-145">Once the deployment script has been built, it can be run on other instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to deploy the managed database objects.</span></span>  
  
#### <a name="to-generate-a-deployment-script-using-generate-scripts"></a><span data-ttu-id="d0730-146">使用產生指令碼來產生部署指令碼</span><span class="sxs-lookup"><span data-stu-id="d0730-146">To generate a deployment script using generate scripts</span></span>  
  
1.  <span data-ttu-id="d0730-147">開啟 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] 並連接至已註冊要部署之 Managed 組件或資料庫物件的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="d0730-147">Open [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] and connect to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance where the managed assembly or database object to be deployed is registered.</span></span>  
  
2.  <span data-ttu-id="d0730-148">在 [**物件總管**中，展開 [ **\<server name>** 和**資料庫**] 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="d0730-148">In the **Object Explorer**, expand the **\<server name>** and **Databases** trees.</span></span> <span data-ttu-id="d0730-149">以滑鼠右鍵按一下已註冊受控資料庫物件的資料庫 **，選取 [** 工作]，然後選取 [**產生腳本**]。</span><span class="sxs-lookup"><span data-stu-id="d0730-149">Right-click the database where the managed database object is registered, select **Tasks**, and then select **Generate Scripts**.</span></span> <span data-ttu-id="d0730-150">指令碼精靈隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="d0730-150">The Script Wizard opens.</span></span>  
  
3.  <span data-ttu-id="d0730-151">從清單方塊中選取資料庫，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d0730-151">Select the database from the list box and click **Next**.</span></span>  
  
4.  <span data-ttu-id="d0730-152">在 [**選擇腳本選項**] 窗格中，按 **[下一步]** 或變更選項，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d0730-152">In the **Choose Script Options** pane, click **Next**, or change the options and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="d0730-153">在 [**選擇物件類型**] 窗格中，選擇要部署的資料庫物件類型。</span><span class="sxs-lookup"><span data-stu-id="d0730-153">In the **Choose Object Types** pane, choose the type of database object to be deployed.</span></span> <span data-ttu-id="d0730-154">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="d0730-154">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="d0730-155">針對在 [**選擇物件類型**] 窗格中選取的每個物件類型，會顯示\*\* \<type> [選擇\*\*] 窗格。</span><span class="sxs-lookup"><span data-stu-id="d0730-155">For every object type selected in the **Choose Object Types** pane, a **Choose \<type>** pane is presented.</span></span> <span data-ttu-id="d0730-156">在這個窗格中，您可以從該資料庫物件類型 (已在指定的資料庫中註冊) 的所有執行個體中選擇。</span><span class="sxs-lookup"><span data-stu-id="d0730-156">In this pane, you can choose from all the instances of that database object type registered in the specified database.</span></span> <span data-ttu-id="d0730-157">選取一或多個物件，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d0730-157">Select one or more objects and click **Next**.</span></span>  
  
7.  <span data-ttu-id="d0730-158">當所有所需的資料庫物件類型都已選取時，[**輸出選項**] 窗格就會出現。</span><span class="sxs-lookup"><span data-stu-id="d0730-158">The **Output Options** pane comes up when all of the desired database object types have been selected.</span></span> <span data-ttu-id="d0730-159">選取 [**編寫腳本至**檔案]，並指定腳本的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="d0730-159">Select **Script to file** and specify a file path for the script.</span></span> <span data-ttu-id="d0730-160">選取 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="d0730-160">Select **Next**.</span></span> <span data-ttu-id="d0730-161">檢查您的選擇，然後按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="d0730-161">Review your selections and click **Finish**.</span></span> <span data-ttu-id="d0730-162">此時，部署指令碼就會儲存至指定的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="d0730-162">The deployment script is saved to the specified file path.</span></span>  
  
## <a name="post-deployment-scripts"></a><span data-ttu-id="d0730-163">部署後指令碼</span><span class="sxs-lookup"><span data-stu-id="d0730-163">Post Deployment Scripts</span></span>  
 <span data-ttu-id="d0730-164">您可以執行部署後指令碼。</span><span class="sxs-lookup"><span data-stu-id="d0730-164">You can run a post deployment script.</span></span>  
  
 <span data-ttu-id="d0730-165">若要加入部署後指令碼，請在您的 Visual Studio 專案目錄中加入稱為 postdeployscript.sql 的檔案。</span><span class="sxs-lookup"><span data-stu-id="d0730-165">To add a post deployment script, add a file called postdeployscript.sql in your Visual Studio project directory.</span></span> <span data-ttu-id="d0730-166">例如，以滑鼠右鍵按一下**方案總管**中的專案，然後選取 [**加入現有專案**]。</span><span class="sxs-lookup"><span data-stu-id="d0730-166">For example, right click your project in **Solution Explorer** and select **Add Existing Item**.</span></span> <span data-ttu-id="d0730-167">將此檔案加入專案的根目錄中，而非加入 Test Scripts 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="d0730-167">Add the file in the root of the project, rather than in the Test Scripts folder.</span></span>  
  
 <span data-ttu-id="d0730-168">當您按一下 [部署] 時，Visual Studio 就會在專案部署完成之後執行此指令碼。</span><span class="sxs-lookup"><span data-stu-id="d0730-168">When you click deploy, Visual Studio will run this script after the deployment of your project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0730-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0730-169">See Also</span></span>  
 [<span data-ttu-id="d0730-170">Common Language Runtime &#40;CLR&#41; 整合程式設計概念</span><span class="sxs-lookup"><span data-stu-id="d0730-170">Common Language Runtime &#40;CLR&#41; Integration Programming Concepts</span></span>](common-language-runtime-clr-integration-programming-concepts.md)  
  
  
