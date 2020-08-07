---
title: 執行封裝公用程式 (DtExecUI) UI 參考 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.dtexecui.general.f1
- sql12.dts.dtexecui.executionoptions.f1
- sql12.dts.dtexecui.configuration.f1
- sql12.dts.dtexecui.setvalues.f1
- sql12.dts.dtexecui.commandline.f1
- sql12.dts.dtexecui.commandfiles.f1
- sql12.dts.dtexecui.verification.f1
- sql12.dts.dtexecui.datasources.f1
- sql12.dts.dtexecui.reporting.f1
- sql12.dts.dtexecui.logging.f1
helpviewer_keywords:
- DTExecUI utility
ms.assetid: 3d71df39-126b-4c8e-bd77-128bbd5b0887
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 13601983a4ab841a2b64ff8e4fc722fcf5ae496c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597200"
---
# <a name="execute-package-utility-dtexecui-ui-reference"></a><span data-ttu-id="7ec4d-102">執行封裝公用程式 (DtExecUI) UI 參考</span><span class="sxs-lookup"><span data-stu-id="7ec4d-102">Execute Package Utility (DtExecUI) UI Reference</span></span>
  <span data-ttu-id="7ec4d-103">您可使用 **[執行封裝公用程式]** 來執行 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-103">Use the **Execute Package Utility** to run [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span> <span data-ttu-id="7ec4d-104">此公用程式會執行儲存在下列三個位置之一的套件：[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫、[!INCLUDE[ssIS](../../includes/ssis-md.md)] 套件存放區及檔案系統。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-104">The utility runs packages that are stored in one of three locations: [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Store, and the file system.</span></span> <span data-ttu-id="7ec4d-105">此使用者介面可以從開啟 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] `dtexecui` ，或在命令提示字元中輸入，這是使用**DTExec**命令提示字元工具執行封裝的替代方法。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-105">This user interface, which can be opened from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or by typing `dtexecui` at a command prompt, is an alternative to running packages by using the **DTExec** command prompt tool.</span></span>  
  
 <span data-ttu-id="7ec4d-106">封裝會在與 **dtexecui.exe** 公用程式相同的處理序中執行。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-106">Packages execute in the same process as the **dtexecui.exe** utility.</span></span> <span data-ttu-id="7ec4d-107">由於此公用程式是 32 位元工具，因此封裝會在 Windows on Win32 (WOW) 所執行的 64 位元環境中透過 **dtexecui.exe** 加以執行。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-107">Because this utility is a 32-bit tool, packages run by using **dtexecui.exe** in a 64-bit environment run in Windows on Win32 (WOW).</span></span> <span data-ttu-id="7ec4d-108">在 64 位元電腦上使用 dtexecui.exe 公用程式開發及測試命令時，應先使用 64 位元版本的 **dtexec.exe** 以 64 位元模式測試命令，然後才在實際伺服器上部署或為命令排程。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-108">When developing and testing commands by using the dtexecui.exe utility on a 64-bit computer, you should test the commands in 64-bit mode by using the 64-bit version of **dtexec.exe** before deploying or scheduling the commands on a production server.</span></span>  
  
 <span data-ttu-id="7ec4d-109">[執行封裝公用程式]  是 **DTExec** 命令提示字元工具的圖形化使用者介面。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-109">The **Execute Package Utility** is a graphical user interface for the **DTExec** command prompt tool.</span></span> <span data-ttu-id="7ec4d-110">該使用者介面可輕易設定選項，並在透過所指定的選項執行封裝時，自動組裝傳送給 **DTExec** 命令提示字元工具的命令列。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-110">The user interface makes it easy to configure options and it automatically assembles the command line that is passed to the **DTExec** command prompt tool when you run the package from the specified options.</span></span>  
  
 <span data-ttu-id="7ec4d-111">[執行封裝公用程式]  也可用來組裝您在直接執行 **DTExec** 時所使用的命令列。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-111">The **Execute Package Utility** can also be used to assemble command lines that you use when running **DTExec** directly.</span></span>  
  
### <a name="to-open-execute-package-utility-in-sql-server-management-studio"></a><span data-ttu-id="7ec4d-112">在 SQL Server Management Studio 中開啟執行封裝公用程式</span><span class="sxs-lookup"><span data-stu-id="7ec4d-112">To open Execute Package Utility in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="7ec4d-113">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的 **[檢視]** 功能表上，按一下 **[物件總管]** 。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-113">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Object Explorer**.</span></span>  
  
2.  <span data-ttu-id="7ec4d-114">在 [物件總管] 中，按一下 **[連接]** ，然後按一下 **[Integration Services]** 。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-114">In Object Explorer, click **Connect**, and then click **Integration Services**.</span></span>  
  
3.  <span data-ttu-id="7ec4d-115">在 **[連接到伺服器]** 對話方塊的 **[伺服器名稱]** 清單中，輸入伺服器名稱，然後按一下 **[連接]** 。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-115">In the **Connect to Server** dialog box, enter the server name in the **Server name** list, and then click **Connect**.</span></span>  
  
4.  <span data-ttu-id="7ec4d-116">展開 [存放的封裝]  資料夾和子資料夾，以滑鼠右鍵按一下要執行的封裝，然後按一下 [執行封裝]  。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-116">Expand the **Stored Package**s folder and subfolders, right-click the package you want to run, and then click **Run Package**.</span></span>  
  
### <a name="to-open-the-execute-package-utility-at-the-command-prompt"></a><span data-ttu-id="7ec4d-117">在命令提示字元下開啟執行封裝公用程式</span><span class="sxs-lookup"><span data-stu-id="7ec4d-117">To open the Execute Package Utility at the Command Prompt</span></span>  
  
-   <span data-ttu-id="7ec4d-118">在命令提示字元視窗中，執行 `dtexecui`。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-118">In a command prompt window, run `dtexecui`.</span></span>  
  
 <span data-ttu-id="7ec4d-119">下列各節將說明 **[執行封裝公用程式]** 對話方塊的各個頁面。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-119">The following sections describe pages of the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="general-page"></a><span data-ttu-id="7ec4d-120">一般頁面</span><span class="sxs-lookup"><span data-stu-id="7ec4d-120">General Page</span></span>  
 <span data-ttu-id="7ec4d-121">使用 **[執行封裝公用程式]** 對話方塊的 **[一般]** 頁面，即可指定封裝名稱和位置。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-121">Use the **General** page of the **Execute Package Utility** dialog box to specify a package name and location.</span></span>  
  
 <span data-ttu-id="7ec4d-122">即使封裝儲存在遠端伺服器上，執行封裝公用程式 (dtexecui.exe) 會永遠在本機電腦上執行封裝。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-122">The Execute Package utility (dtexecui.exe) always runs a package on the local computer, even if the package is saved on a remote server.</span></span> <span data-ttu-id="7ec4d-123">如果遠端封裝使用的組態檔也儲存在遠端伺服器上，則執行封裝公用程式可能會找不到組態而導致封裝失敗。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-123">If the remote package uses configuration files that also are saved on the remote server, then the Execute Package utility may not locate the configurations and the package fails.</span></span> <span data-ttu-id="7ec4d-124">為了避免此問題，必須以通用命名慣例 (UNC) 共用名稱來參考組態，例如 \\\myserver\myfile。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-124">To avoid this problem, the configurations must be referenced by using a Universal Naming Convention (UNC) share name like \\\myserver\myfile.</span></span>  
  
### <a name="static-options"></a><span data-ttu-id="7ec4d-125">靜態選項</span><span class="sxs-lookup"><span data-stu-id="7ec4d-125">Static Options</span></span>  
 <span data-ttu-id="7ec4d-126">**封裝來源**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-126">**Package source**</span></span>  
 <span data-ttu-id="7ec4d-127">使用下列選項，指定要執行之封裝的位置：</span><span class="sxs-lookup"><span data-stu-id="7ec4d-127">Specify the location of the package to run, using the following options:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7ec4d-128">值</span><span class="sxs-lookup"><span data-stu-id="7ec4d-128">Value</span></span>|<span data-ttu-id="7ec4d-129">描述</span><span class="sxs-lookup"><span data-stu-id="7ec4d-129">Description</span></span>|  
|<span data-ttu-id="7ec4d-130">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-130">**SQL Server**</span></span>|<span data-ttu-id="7ec4d-131">當套件位於 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-131">Select this option when the package resides in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7ec4d-132">指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體，並提供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-132">Specify an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and provide a user name and password for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="7ec4d-133">每個使用者名稱和密碼都會將 **/USER** _username_ 和 **/PASSWORD** _password_ 選項新增至命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-133">Each user name and password adds the **/USER** _username_ and **/PASSWORD** _password_ options to the command prompt.</span></span>|  
|<span data-ttu-id="7ec4d-134">**檔案系統**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-134">**File system**</span></span>|<span data-ttu-id="7ec4d-135">當封裝位於檔案系統時，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-135">Select this option when the package resides in the file system.</span></span>|  
|<span data-ttu-id="7ec4d-136">**SSIS 封裝存放區**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-136">**SSIS Package Store**</span></span>|<span data-ttu-id="7ec4d-137">當封裝位於 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 封裝存放區時，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-137">Select this option when the package resides in the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Store.</span></span>|  
  
 <span data-ttu-id="7ec4d-138">每一個選取項目都具有下列選項集合。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-138">Each of these selections has the following set of options.</span></span>  
  
 <span data-ttu-id="7ec4d-139">**執行**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-139">**Execute**</span></span>  
 <span data-ttu-id="7ec4d-140">按一下以執行封裝。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-140">Click to run the package.</span></span>  
  
 <span data-ttu-id="7ec4d-141">**關閉**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-141">**Close**</span></span>  
 <span data-ttu-id="7ec4d-142">按一下即可關閉 [執行封裝公用程式]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-142">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
### <a name="dynamic-options"></a><span data-ttu-id="7ec4d-143">動態選項</span><span class="sxs-lookup"><span data-stu-id="7ec4d-143">Dynamic Options</span></span>  
  
#### <a name="package-source--sql-server"></a><span data-ttu-id="7ec4d-144">封裝來源 = SQL Server</span><span class="sxs-lookup"><span data-stu-id="7ec4d-144">Package Source = SQL Server</span></span>  
 <span data-ttu-id="7ec4d-145">**Server**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-145">**Server**</span></span>  
 <span data-ttu-id="7ec4d-146">輸入封裝所在的伺服器名稱，或從清單中選取伺服器。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-146">Type the name of the server where the package resides, or select a server from the list.</span></span>  
  
 <span data-ttu-id="7ec4d-147">**登入伺服器**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-147">**Log on to the server**</span></span>  
 <span data-ttu-id="7ec4d-148">指定封裝要使用 Windows 驗證或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-148">Specify whether the package should use Windows Authentication or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7ec4d-149">建議使用 Windows 驗證，以獲得較佳的安全性。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-149">Windows Authentication is recommended for better security.</span></span> <span data-ttu-id="7ec4d-150">使用 Windows 驗證，您就不需要指定使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-150">With Windows Authentication you do not have to specify a user name and password.</span></span>  
  
 <span data-ttu-id="7ec4d-151">**[使用 Windows 驗證]**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-151">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="7ec4d-152">選取此選項即可使用 Windows 驗證，並以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 使用者帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-152">Select this option to use Windows Authentication and log on using a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows user account.</span></span>  
  
 <span data-ttu-id="7ec4d-153">**[使用 SQL Server 驗證]**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-153">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="7ec4d-154">選取此選項即可使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-154">Select this option to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="7ec4d-155">當使用者透過不信任連接並指定登入名稱和密碼進行連接時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會執行驗證，檢查是否已設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入帳戶，以及指定的密碼是否符合先前記錄的密碼。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-155">When a user connects with a specified login name and password from a non-trusted connection, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs the authentication by checking to see if a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login account has been set up and if the specified password matches the one previously recorded.</span></span> <span data-ttu-id="7ec4d-156">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 找不到登入帳戶，驗證將會失敗，且使用者會收到錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-156">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot find the login account, authentication fails, and the user receives an error message.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7ec4d-157">盡可能使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-157">When possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="7ec4d-158">**套件**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-158">**Package**</span></span>  
 <span data-ttu-id="7ec4d-159">鍵入套件的名稱，或按一下省略符號按鈕 **(...)** ，以使用 [選取 SSIS 套件]  對話方塊來尋找套件。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-159">Type the name of the package, or click the ellipsis button **(...)** to locate a package using the **Select an SSIS Package** dialog box.</span></span>  
  
#### <a name="package-source--file-system"></a><span data-ttu-id="7ec4d-160">封裝來源 = 檔案系統</span><span class="sxs-lookup"><span data-stu-id="7ec4d-160">Package Source = File System</span></span>  
 <span data-ttu-id="7ec4d-161">**套件**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-161">**Package**</span></span>  
 <span data-ttu-id="7ec4d-162">鍵入套件的名稱，或按一下省略符號按鈕 **(...)** ，以使用 [開啟] 對話方塊來尋找套件。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-162">Type the name of the package, or click the ellipsis button **(...)** to locate a package using the Open dialog box.</span></span> <span data-ttu-id="7ec4d-163">依預設，對話方塊只會列出副檔名為 .dtsx 的檔案。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-163">By default, the dialog box lists only files that have the .dtsx extension.</span></span>  
  
#### <a name="package-source--ssis-package-store"></a><span data-ttu-id="7ec4d-164">封裝來源 = SSIS 封裝存放區</span><span class="sxs-lookup"><span data-stu-id="7ec4d-164">Package Source = SSIS Package Store</span></span>  
 <span data-ttu-id="7ec4d-165">**Server**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-165">**Server**</span></span>  
 <span data-ttu-id="7ec4d-166">輸入封裝所在的電腦名稱，或從清單中選取電腦。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-166">Type the name of the computer where the package resides, or select a computer from the list.</span></span>  
  
 <span data-ttu-id="7ec4d-167">**登入伺服器**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-167">**Log on to the server**</span></span>  
 <span data-ttu-id="7ec4d-168">指定封裝是否應該使用 Microsoft Windows 驗證來連接封裝來源。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-168">Specify whether the package should use Microsoft Windows Authentication to connect to the package source.</span></span> <span data-ttu-id="7ec4d-169">建議使用 Windows 驗證，以獲得較佳的安全性。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-169">Windows Authentication is recommended for better security.</span></span> <span data-ttu-id="7ec4d-170">使用 Windows 驗證，您就不需要指定使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-170">With Windows Authentication you do not have to specify a user name and password.</span></span>  
  
 <span data-ttu-id="7ec4d-171">**[使用 Windows 驗證]**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-171">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="7ec4d-172">選取此選項即可使用 Windows 驗證，並以 Microsoft Windows 使用者帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-172">Select this option to use Windows Authentication and log on using a Microsoft Windows user account.</span></span>  
  
 <span data-ttu-id="7ec4d-173">**[使用 SQL Server 驗證]**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-173">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="7ec4d-174">當您執行儲存在 [SSIS 封裝存放區]  的封裝時，無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-174">This option is not available when you run a package stored in the **SSIS Package Store**.</span></span>  
  
 <span data-ttu-id="7ec4d-175">**套件**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-175">**Package**</span></span>  
 <span data-ttu-id="7ec4d-176">鍵入套件的名稱，或按一下省略符號按鈕 **(...)** ，以使用 [選取 SSIS 套件]  對話方塊來尋找套件。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-176">Type the name of the package, or click the ellipsis button **(...)** to locate a package using the **Select an SSIS Package** dialog box.</span></span>  
  
## <a name="configurations-page"></a><span data-ttu-id="7ec4d-177">組態頁面</span><span class="sxs-lookup"><span data-stu-id="7ec4d-177">Configurations Page</span></span>  
 <span data-ttu-id="7ec4d-178">使用 **[執行封裝公用程式]** 對話方塊的 **[組態]** 頁面，即可選取要在執行階段載入的組態檔，並指定載入這些檔案的順序。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-178">Use the **Configurations** page of the **Execute Package Utility** dialog box to select the configuration files to load at run time, and to specify the order in which they load.</span></span>  
  
### <a name="options"></a><span data-ttu-id="7ec4d-179">選項。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-179">Options</span></span>  
 <span data-ttu-id="7ec4d-180">**組態檔**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-180">**Configuration files**</span></span>  
 <span data-ttu-id="7ec4d-181">列出封裝使用的組態。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-181">Lists the configurations that the package uses.</span></span> <span data-ttu-id="7ec4d-182">每個組態檔都會將 **/CONFIGFILE filename** 選項加入命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-182">Each configuration file adds a **/CONFIGFILE filename** option to the command prompt.</span></span>  
  
 <span data-ttu-id="7ec4d-183">**方向鍵**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-183">**Arrow keys**</span></span>  
 <span data-ttu-id="7ec4d-184">選取清單中的組態檔，並使用右邊的箭頭按鍵，即可變更載入的順序。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-184">Select a configuration file in the list, and use the arrow keys at right to change the loading order.</span></span> <span data-ttu-id="7ec4d-185">組態會從清單的頂端開始依序載入。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-185">Configurations load in order starting from the top of the list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7ec4d-186">如果有多個組態會修改同一項屬性，就會採用最後載入的組態。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-186">If multiple configurations modify the same property, the configuration that loads last is used.</span></span>  
  
 <span data-ttu-id="7ec4d-187">**加入**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-187">**Add**</span></span>  
 <span data-ttu-id="7ec4d-188">按一下即可使用 [開啟]  對話方塊來加入組態。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-188">Click to add configurations using the **Open** dialog box.</span></span> <span data-ttu-id="7ec4d-189">依預設，對話方塊只會列出具有 .dtsconfig 副檔名的檔案。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-189">By default, the dialog box lists only files that have the .dtsconfig extension.</span></span>  
  
 <span data-ttu-id="7ec4d-190">**移除**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-190">**Remove**</span></span>  
 <span data-ttu-id="7ec4d-191">選取清單中的組態檔，然後按一下 [移除]  。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-191">Select a configuration file in the list and then click **Remove**.</span></span>  
  
 <span data-ttu-id="7ec4d-192">**執行**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-192">**Execute**</span></span>  
 <span data-ttu-id="7ec4d-193">按一下以執行封裝。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-193">Click to run the package.</span></span>  
  
 <span data-ttu-id="7ec4d-194">**關閉**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-194">**Close**</span></span>  
 <span data-ttu-id="7ec4d-195">按一下即可關閉 [執行封裝公用程式]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-195">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="command-files-page"></a><span data-ttu-id="7ec4d-196">命令檔頁面</span><span class="sxs-lookup"><span data-stu-id="7ec4d-196">Command Files Page</span></span>  
 <span data-ttu-id="7ec4d-197">使用 **[執行封裝公用程式]** 對話方塊的 **[命令檔]** 頁面，即可選取在執行階段要載入的命令檔。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-197">Use the **Command Files** page of the **Execute Package Utility** dialog box to select the command files to load at run time.</span></span>  
  
### <a name="options"></a><span data-ttu-id="7ec4d-198">選項。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-198">Options</span></span>  
 <span data-ttu-id="7ec4d-199">**命令檔**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-199">**Command files**</span></span>  
 <span data-ttu-id="7ec4d-200">列出封裝所使用的命令檔。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-200">Lists the command files that the package uses.</span></span> <span data-ttu-id="7ec4d-201">封裝可以使用多個檔案來設定命令列選項。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-201">A package can use multiple files to set command-line options.</span></span>  
  
 <span data-ttu-id="7ec4d-202">**方向鍵**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-202">**Arrow keys**</span></span>  
 <span data-ttu-id="7ec4d-203">選取清單中的命令檔，並使用右邊的方向鍵來變更載入順序。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-203">Select a command file in the list, and use the arrow keys at right to change the loading order.</span></span> <span data-ttu-id="7ec4d-204">命令檔依序載入，從清單的最上方開始。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-204">Command files load in order, starting from the top of the list.</span></span>  
  
 <span data-ttu-id="7ec4d-205">**加入**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-205">**Add**</span></span>  
 <span data-ttu-id="7ec4d-206">按一下即可使用 [開啟]  對話方塊加入命令檔。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-206">Click to add a command file, using the **Open** dialog box.</span></span>  
  
 <span data-ttu-id="7ec4d-207">**移除**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-207">**Remove**</span></span>  
 <span data-ttu-id="7ec4d-208">選取文字方塊中的命令檔，然後使用 [移除]  按鈕將它移除。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-208">Select a command file in the text box, and then remove it using the **Remove** button.</span></span>  
  
 <span data-ttu-id="7ec4d-209">**執行**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-209">**Execute**</span></span>  
 <span data-ttu-id="7ec4d-210">按一下以執行封裝。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-210">Click to run the package.</span></span>  
  
 <span data-ttu-id="7ec4d-211">**關閉**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-211">**Close**</span></span>  
 <span data-ttu-id="7ec4d-212">按一下即可關閉 [執行封裝公用程式]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-212">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="connection-managers-page"></a><span data-ttu-id="7ec4d-213">連接管理員頁面</span><span class="sxs-lookup"><span data-stu-id="7ec4d-213">Connection Managers Page</span></span>  
 <span data-ttu-id="7ec4d-214">使用 **[執行封裝公用程式]** 對話方塊的 **[連接管理員]** 頁面，即可編輯封裝使用之連接管理員的連接字串。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-214">Use the **Connection Managers** page of the **Execute Package Utility** dialog box to edit the connection strings of the connection managers that the package uses.</span></span>  
  
### <a name="options"></a><span data-ttu-id="7ec4d-215">選項。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-215">Options</span></span>  
 <span data-ttu-id="7ec4d-216">**連線管理員**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-216">**Connection Manager**</span></span>  
 <span data-ttu-id="7ec4d-217">選取其核取方塊即可使 [連接字串]  資料行變成可編輯。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-217">Select its check box to make the **Connection String** column editable.</span></span>  
  
 <span data-ttu-id="7ec4d-218">**說明**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-218">**Description**</span></span>  
 <span data-ttu-id="7ec4d-219">檢視每個連接管理員的描述。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-219">View a description for each connection manager.</span></span> <span data-ttu-id="7ec4d-220">無法編輯描述。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-220">Descriptions cannot be edited.</span></span>  
  
 <span data-ttu-id="7ec4d-221">**連接字串**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-221">**Connection String**</span></span>  
 <span data-ttu-id="7ec4d-222">編輯連接管理員的連接字串。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-222">Edit the connection string for a connection manager.</span></span> <span data-ttu-id="7ec4d-223">只有選取 **[連接管理員]** 核取方塊時，才可以編輯此欄位。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-223">This field is editable only when the **Connection Manager** check box is selected.</span></span>  
  
 <span data-ttu-id="7ec4d-224">**執行**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-224">**Execute**</span></span>  
 <span data-ttu-id="7ec4d-225">按一下以執行封裝。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-225">Click to run the package.</span></span>  
  
 <span data-ttu-id="7ec4d-226">**關閉**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-226">**Close**</span></span>  
 <span data-ttu-id="7ec4d-227">按一下即可關閉 [執行封裝公用程式]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-227">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="execution-options-page"></a><span data-ttu-id="7ec4d-228">執行選項頁面</span><span class="sxs-lookup"><span data-stu-id="7ec4d-228">Execution Options Page</span></span>  
 <span data-ttu-id="7ec4d-229">使用 [執行封裝公用程式]  對話方塊的 [執行選項]  頁面，即可為封裝指定執行階段的選項。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-229">Use the **Execution Options** page of the **Execute Package Utility** dialog box to specify run-time options for the package.</span></span>  
  
### <a name="options"></a><span data-ttu-id="7ec4d-230">選項。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-230">Options</span></span>  
 <span data-ttu-id="7ec4d-231">**發生驗證警告時封裝就失敗**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-231">**Fail package on validation warnings**</span></span>  
 <span data-ttu-id="7ec4d-232">指出在發生驗證警告時，封裝是否會失敗。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-232">Indicate whether the package fails if a validation warning occurs.</span></span>  
  
 <span data-ttu-id="7ec4d-233">**驗證封裝但不執行**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-233">**Validate package without executing**</span></span>  
 <span data-ttu-id="7ec4d-234">指出是否只對封裝進行驗證。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-234">Indicate whether the package is validated only.</span></span>  
  
 <span data-ttu-id="7ec4d-235">**最大並行可執行檔數目**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-235">**Maximum concurrent executables**</span></span>  
 <span data-ttu-id="7ec4d-236">指出您是否想要指定可以同時在封裝中執行的最大可執行檔數目。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-236">Indicate whether you want to specify the maximum number of executables that can run in the package at the same time.</span></span> <span data-ttu-id="7ec4d-237">當您選取此核取方塊之後，請使用微調方塊來指定最大可執行檔數目。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-237">After you select this check box, use the spin box to specify the maximum number of executables.</span></span>  
  
 <span data-ttu-id="7ec4d-238">**啟用封裝檢查點**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-238">**Enable package checkpoints**</span></span>  
 <span data-ttu-id="7ec4d-239">表示是否要啟用封裝檢查點。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-239">Indicate whether to enable package checkpoints.</span></span>  
  
 <span data-ttu-id="7ec4d-240">**檢查點檔案**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-240">**Checkpoint file**</span></span>  
 <span data-ttu-id="7ec4d-241">如果您啟用了封裝檢查點，就會列出封裝使用的檢查點檔案。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-241">List the checkpoint file the package uses, if you enable package checkpoints.</span></span>  
  
 <span data-ttu-id="7ec4d-242">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-242">**Browse**</span></span>  
 <span data-ttu-id="7ec4d-243">如果您啟用了套件檢查點，請按一下瀏覽按鈕 **(...)** ，使用 [開啟]  對話方塊來找出檢查點檔案。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-243">Click the browse button **(...)** to locate the checkpoint file using the **Open** dialog box, if you enable package checkpoints.</span></span> <span data-ttu-id="7ec4d-244">如果已經指定了檢查點檔案，就會用選取的檔案來取代它。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-244">If a checkpoint file is already specified, it is replaced by the selected file.</span></span>  
  
 <span data-ttu-id="7ec4d-245">**覆寫重新啟動選項**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-245">**Override restart options**</span></span>  
 <span data-ttu-id="7ec4d-246">如果您啟用了封裝檢查點，會指出是否要覆寫重新啟動選項。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-246">Indicate whether to override restart options, if you enable package checkpoints.</span></span>  
  
 <span data-ttu-id="7ec4d-247">**重新啟動選項**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-247">**Restart option**</span></span>  
 <span data-ttu-id="7ec4d-248">如果您覆寫重新啟動選項，選取如何使用檢查點。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-248">Select how to use checkpoints, if you override restart options.</span></span>  
  
 <span data-ttu-id="7ec4d-249">**執行**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-249">**Execute**</span></span>  
 <span data-ttu-id="7ec4d-250">按一下以執行封裝。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-250">Click to run the package.</span></span>  
  
 <span data-ttu-id="7ec4d-251">**關閉**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-251">**Close**</span></span>  
 <span data-ttu-id="7ec4d-252">按一下即可關閉 [執行封裝公用程式]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-252">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="reporting-page"></a><span data-ttu-id="7ec4d-253">報告頁面</span><span class="sxs-lookup"><span data-stu-id="7ec4d-253">Reporting Page</span></span>  
 <span data-ttu-id="7ec4d-254">使用 **[執行封裝公用程式]** 對話方塊的 **[報表]** 頁面，即可指定封裝執行時，記錄至主控台的事件與封裝的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-254">Use the **Reporting** page of the **Execute Package Utility** dialog box to specify the events and information about the package to log to the console when the package runs.</span></span>  
  
### <a name="options"></a><span data-ttu-id="7ec4d-255">選項。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-255">Options</span></span>  
 <span data-ttu-id="7ec4d-256">**主控台事件**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-256">**Console events**</span></span>  
 <span data-ttu-id="7ec4d-257">指出要報告的事件和訊息類型。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-257">Indicate the events and types of messages to report.</span></span>  
  
 <span data-ttu-id="7ec4d-258">**None**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-258">**None**</span></span>  
 <span data-ttu-id="7ec4d-259">選擇不報告。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-259">Select for no reporting.</span></span>  
  
 <span data-ttu-id="7ec4d-260">**錯誤**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-260">**Errors**</span></span>  
 <span data-ttu-id="7ec4d-261">選擇要報告錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-261">Select to report error messages.</span></span>  
  
 <span data-ttu-id="7ec4d-262">**警告**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-262">**Warnings**</span></span>  
 <span data-ttu-id="7ec4d-263">選擇要報告警告訊息。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-263">Select to report warning messages.</span></span>  
  
 <span data-ttu-id="7ec4d-264">**自訂事件**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-264">**Custom Events**</span></span>  
 <span data-ttu-id="7ec4d-265">選擇要報告自訂事件訊息。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-265">Select to report custom event messages.</span></span>  
  
 <span data-ttu-id="7ec4d-266">**管線事件**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-266">**Pipeline Events**</span></span>  
 <span data-ttu-id="7ec4d-267">選擇要報告資料流程事件訊息。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-267">Select to report data flow events messages.</span></span>  
  
 <span data-ttu-id="7ec4d-268">**資訊**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-268">**Information**</span></span>  
 <span data-ttu-id="7ec4d-269">選擇要報告資訊訊息。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-269">Select to report information messages.</span></span>  
  
 <span data-ttu-id="7ec4d-270">**詳細資訊**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-270">**Verbose**</span></span>  
 <span data-ttu-id="7ec4d-271">選擇要使用詳細資訊報表。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-271">Select to use verbose reporting.</span></span>  
  
 <span data-ttu-id="7ec4d-272">**主控台記錄**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-272">**Console logging**</span></span>  
 <span data-ttu-id="7ec4d-273">指定選取的事件發生時，要寫入記錄的資訊。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-273">Specify the information that you want written to the log when the selected event occurs.</span></span>  
  
 <span data-ttu-id="7ec4d-274">**名稱**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-274">**Name**</span></span>  
 <span data-ttu-id="7ec4d-275">選擇要報告建立封裝的人員名稱。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-275">Select to report the name of the person who created the package.</span></span>  
  
 <span data-ttu-id="7ec4d-276">**電腦**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-276">**Computer**</span></span>  
 <span data-ttu-id="7ec4d-277">選擇要報告正在執行封裝的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-277">Select to report the name of the computer the package is running on.</span></span>  
  
 <span data-ttu-id="7ec4d-278">**運算子**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-278">**Operator**</span></span>  
 <span data-ttu-id="7ec4d-279">選擇要報告啟動封裝的人員名稱。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-279">Select to report the name of the person who started the package.</span></span>  
  
 <span data-ttu-id="7ec4d-280">**來源名稱**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-280">**Source name**</span></span>  
 <span data-ttu-id="7ec4d-281">選擇要報告封裝名稱。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-281">Select to report the package name.</span></span>  
  
 <span data-ttu-id="7ec4d-282">**來源 GUID**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-282">**Source GUID**</span></span>  
 <span data-ttu-id="7ec4d-283">選擇要報告封裝 GUID。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-283">Select to report the package GUID.</span></span>  
  
 <span data-ttu-id="7ec4d-284">**執行 GUID**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-284">**Execution GUID**</span></span>  
 <span data-ttu-id="7ec4d-285">選擇要報告封裝執行個體的 GUID。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-285">Select to report the GUID of the package execution instance.</span></span>  
  
 <span data-ttu-id="7ec4d-286">**訊息**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-286">**Message**</span></span>  
 <span data-ttu-id="7ec4d-287">選擇要報告訊息。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-287">Select to report messages.</span></span>  
  
 <span data-ttu-id="7ec4d-288">**開始時間和結束時間**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-288">**Start time and end time**</span></span>  
 <span data-ttu-id="7ec4d-289">選擇要報告封裝開始和結束的時間。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-289">Select to report when the package began and finished.</span></span>  
  
 <span data-ttu-id="7ec4d-290">**執行**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-290">**Execute**</span></span>  
 <span data-ttu-id="7ec4d-291">按一下以執行封裝。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-291">Click to run the package.</span></span>  
  
 <span data-ttu-id="7ec4d-292">**關閉**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-292">**Close**</span></span>  
 <span data-ttu-id="7ec4d-293">按一下即可關閉 [執行封裝公用程式]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-293">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="logging-page"></a><span data-ttu-id="7ec4d-294">記錄頁面</span><span class="sxs-lookup"><span data-stu-id="7ec4d-294">Logging Page</span></span>  
 <span data-ttu-id="7ec4d-295">使用 **[執行封裝公用程式]** 對話方塊的 **[記錄]** 頁面，即可讓封裝在執行階段使用記錄提供者。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-295">Use the **Logging** page of the **Execute Package Utility** dialog box to make log providers available to the package at run time.</span></span> <span data-ttu-id="7ec4d-296">提供連接到記錄的封裝記錄提供者類型和連接字串。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-296">Provide the package log provider type and the connection string for connecting to the log.</span></span> <span data-ttu-id="7ec4d-297">每個記錄提供者項目都會將 **/LOGGER**_classid_ 選項加入命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-297">Each log provider entry adds a **/LOGGER**_classid_ option to the command prompt.</span></span>  
  
### <a name="options"></a><span data-ttu-id="7ec4d-298">選項。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-298">Options</span></span>  
 <span data-ttu-id="7ec4d-299">**記錄提供者**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-299">**Log Provider**</span></span>  
 <span data-ttu-id="7ec4d-300">從清單中選取記錄提供者。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-300">Select a log provider from the list.</span></span>  
  
 <span data-ttu-id="7ec4d-301">**組態字串**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-301">**Configuration String**</span></span>  
 <span data-ttu-id="7ec4d-302">從指向記錄位置的封裝選取連接管理員的名稱，或鍵入連接到記錄提供者的連接字串。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-302">Select the name of the connection manager from the package that points to the log location, or type the connection string for connecting to the log provider.</span></span>  
  
 <span data-ttu-id="7ec4d-303">**移除**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-303">**Remove**</span></span>  
 <span data-ttu-id="7ec4d-304">選取記錄提供者，然後按一下即可將它移除。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-304">Select a log provider and click to remove it.</span></span>  
  
 <span data-ttu-id="7ec4d-305">**執行**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-305">**Execute**</span></span>  
 <span data-ttu-id="7ec4d-306">按一下以執行封裝。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-306">Click to run the package.</span></span>  
  
 <span data-ttu-id="7ec4d-307">**關閉**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-307">**Close**</span></span>  
 <span data-ttu-id="7ec4d-308">按一下即可關閉 [執行封裝公用程式]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-308">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="set-values-page"></a><span data-ttu-id="7ec4d-309">設定值頁面</span><span class="sxs-lookup"><span data-stu-id="7ec4d-309">Set Values Page</span></span>  
 <span data-ttu-id="7ec4d-310">使用 **[執行封裝公用程式]** 對話方塊的 **[設定值]** 頁面，即可藉由輸入屬性的路徑和屬性值，來設定封裝、可執行檔、連接、變數和記錄提供者的屬性值。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-310">Use the **Set Values** page of the **Execute Package Utility** dialog box to set the property values of packages, executables, connections, variables, and log providers by typing the paths of properties and the property values.</span></span> <span data-ttu-id="7ec4d-311">每個路徑項目都會將 **/SET**_propertypath;value_ 選項加入命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-311">Each path entry adds a **/SET**_propertypath;value_ option to the command prompt.</span></span>  
  
### <a name="options"></a><span data-ttu-id="7ec4d-312">選項。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-312">Options</span></span>  
 <span data-ttu-id="7ec4d-313">**屬性路徑**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-313">**Property Path**</span></span>  
 <span data-ttu-id="7ec4d-314">輸入屬性的路徑。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-314">Type the path of the property.</span></span> <span data-ttu-id="7ec4d-315">路徑的語法會使用反斜線 (\\) 來指出下列項目是容器，使用句點 (.) 來指出下列項目是屬性，以及使用方括號來指出集合成員。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-315">The path syntax uses a backslash (\\) to indicate that the following item is a container, the period (.) to indicate the following item is a property, and brackets to indicate a collection member.</span></span> <span data-ttu-id="7ec4d-316">可以使用成員的索引或其名稱來識別成員。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-316">The member can be identified by its index or its name.</span></span> <span data-ttu-id="7ec4d-317">例如，封裝變數的屬性路徑為 \Package.Variables[MyVariable].Value。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-317">For example, the property path of a package variable is \Package.Variables[MyVariable].Value.</span></span>  
  
 <span data-ttu-id="7ec4d-318">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-318">**Value**</span></span>  
 <span data-ttu-id="7ec4d-319">鍵入屬性的值。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-319">Type the value of the property.</span></span>  
  
 <span data-ttu-id="7ec4d-320">**移除**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-320">**Remove**</span></span>  
 <span data-ttu-id="7ec4d-321">選取屬性路徑，然後按一下即可將它移除。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-321">Select a property path and click to remove it.</span></span>  
  
 <span data-ttu-id="7ec4d-322">**執行**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-322">**Execute**</span></span>  
 <span data-ttu-id="7ec4d-323">按一下以執行封裝。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-323">Click to run the package.</span></span>  
  
 <span data-ttu-id="7ec4d-324">**關閉**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-324">**Close**</span></span>  
 <span data-ttu-id="7ec4d-325">按一下即可關閉 [執行封裝公用程式]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-325">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="verification-page"></a><span data-ttu-id="7ec4d-326">驗證頁面</span><span class="sxs-lookup"><span data-stu-id="7ec4d-326">Verification Page</span></span>  
 <span data-ttu-id="7ec4d-327">使用 **[執行封裝]** 對話方塊的 **[驗證]** 頁面，即可設定驗證封裝的準則。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-327">Use the **Verification** page of the **Execute Package** dialog box to set criteria for verifying the package.</span></span>  
  
### <a name="options"></a><span data-ttu-id="7ec4d-328">選項。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-328">Options</span></span>  
 <span data-ttu-id="7ec4d-329">**只執行簽署的封裝**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-329">**Execute only signed packages**</span></span>  
 <span data-ttu-id="7ec4d-330">選取即可只執行已經簽署的封裝。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-330">Select to execute only packages that have been signed.</span></span>  
  
 <span data-ttu-id="7ec4d-331">**確認封裝組建**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-331">**Verify package build**</span></span>  
 <span data-ttu-id="7ec4d-332">選取即可確認封裝組建。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-332">Select to verify the package build.</span></span>  
  
 <span data-ttu-id="7ec4d-333">Build</span><span class="sxs-lookup"><span data-stu-id="7ec4d-333">Build</span></span>  
 <span data-ttu-id="7ec4d-334">指定與組建相關聯的循序組建編號。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-334">Specify the sequential Build number associated with the build.</span></span>  
  
 <span data-ttu-id="7ec4d-335">**確認封裝識別碼**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-335">**Verify package ID**</span></span>  
 <span data-ttu-id="7ec4d-336">選取即可確認封裝識別碼。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-336">Select to verify the package ID.</span></span>  
  
 <span data-ttu-id="7ec4d-337">封裝識別碼</span><span class="sxs-lookup"><span data-stu-id="7ec4d-337">Package ID</span></span>  
 <span data-ttu-id="7ec4d-338">指定封裝識別碼。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-338">Specify the package identification number.</span></span>  
  
 <span data-ttu-id="7ec4d-339">**確認版本識別碼**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-339">**Verify version ID**</span></span>  
 <span data-ttu-id="7ec4d-340">選取即可確認版本識別碼。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-340">Select to verify the version ID.</span></span>  
  
 <span data-ttu-id="7ec4d-341">版本識別碼</span><span class="sxs-lookup"><span data-stu-id="7ec4d-341">Version ID</span></span>  
 <span data-ttu-id="7ec4d-342">指定版本識別碼。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-342">Specify the version identification number.</span></span>  
  
 <span data-ttu-id="7ec4d-343">**執行**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-343">**Execute**</span></span>  
 <span data-ttu-id="7ec4d-344">按一下以執行封裝。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-344">Click to run the package.</span></span>  
  
 <span data-ttu-id="7ec4d-345">**關閉**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-345">**Close**</span></span>  
 <span data-ttu-id="7ec4d-346">按一下即可關閉 [執行封裝公用程式]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-346">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="command-line-page"></a><span data-ttu-id="7ec4d-347">命令列頁面</span><span class="sxs-lookup"><span data-stu-id="7ec4d-347">Command Line Page</span></span>  
 <span data-ttu-id="7ec4d-348">使用 **[執行封裝公用程式]** 對話方塊的 **[命令列]** 節點，即可編輯已經由各對話建立之選項所產生的命令列。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-348">Use the **Command Line** node of the **Execute Package Utility** dialog box to edit the command line that has been generated by the options created by the various dialogs.</span></span>  
  
### <a name="options"></a><span data-ttu-id="7ec4d-349">選項。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-349">Options</span></span>  
 <span data-ttu-id="7ec4d-350">**還原原始選項**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-350">**Restore the original options**</span></span>  
 <span data-ttu-id="7ec4d-351">按一下即可還原命令列至其原始狀態。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-351">Click to restore the command line to its original state.</span></span> <span data-ttu-id="7ec4d-352">如果已經使用 [手動編輯命令列]  選項進行修改，並且要還原原始命令列選項，請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-352">Use this option if you have made modifications using the **Edit the command line manually** option and want to restore the original command-line options.</span></span>  
  
 <span data-ttu-id="7ec4d-353">**手動編輯命令列**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-353">**Edit the command line manually**</span></span>  
 <span data-ttu-id="7ec4d-354">按一下即可編輯 [命令列]  文字方塊中的命令列。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-354">Click to edit the command line in the **Command line** text box.</span></span>  
  
 <span data-ttu-id="7ec4d-355">**命令列**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-355">**Command line**</span></span>  
 <span data-ttu-id="7ec4d-356">顯示目前的命令列。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-356">Displays the current command line.</span></span> <span data-ttu-id="7ec4d-357">如果您選取要以手動編輯命令列的選項，就可以編輯。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-357">Editable if you selected the option to edit the command line manually.</span></span>  
  
 <span data-ttu-id="7ec4d-358">**執行**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-358">**Execute**</span></span>  
 <span data-ttu-id="7ec4d-359">按一下以執行封裝。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-359">Click to run the package.</span></span>  
  
 <span data-ttu-id="7ec4d-360">**關閉**</span><span class="sxs-lookup"><span data-stu-id="7ec4d-360">**Close**</span></span>  
 <span data-ttu-id="7ec4d-361">按一下即可關閉 [執行封裝公用程式]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7ec4d-361">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ec4d-362">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ec4d-362">See Also</span></span>  
 [<span data-ttu-id="7ec4d-363">dtexec 公用程式</span><span class="sxs-lookup"><span data-stu-id="7ec4d-363">dtexec Utility</span></span>](dtexec-utility.md)  
  
  
