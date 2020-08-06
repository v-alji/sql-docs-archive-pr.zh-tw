---
title: 建置、部署和偵錯自訂物件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom objects [Integration Services]
ms.assetid: b03685bc-5398-4c3f-901a-1219c1098fbe
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 13157fce4e5c7dd8987f4950a6b4250ea0e36094
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705306"
---
# <a name="building-deploying-and-debugging-custom-objects"></a><span data-ttu-id="27e54-102">建立、部署和偵錯自訂物件</span><span class="sxs-lookup"><span data-stu-id="27e54-102">Building, Deploying, and Debugging Custom Objects</span></span>
  <span data-ttu-id="27e54-103">撰寫 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 之自訂物件的程式碼之後，必須建立並部署組件，以及將其整合到 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計工具，其才可供封裝使用，並進行測試及偵錯。</span><span class="sxs-lookup"><span data-stu-id="27e54-103">After you have written the code for a custom object for [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], you must build the assembly, deploy it, integrate it into [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer to make it available for use in packages, and test and debug it.</span></span>

##  <a name="steps-in-building-deploying-and-debugging-a-custom-object-for-integration-services"></a><a name="top"></a> <span data-ttu-id="27e54-104">針對 Integration Services 建置、部署和偵錯自訂物件的步驟</span><span class="sxs-lookup"><span data-stu-id="27e54-104">Steps in Building, Deploying, and Debugging a Custom Object for Integration Services</span></span>
 <span data-ttu-id="27e54-105">您已經撰寫物件的自訂功能。</span><span class="sxs-lookup"><span data-stu-id="27e54-105">You have already written the custom functionality for your object.</span></span> <span data-ttu-id="27e54-106">現在您必須測試它，並使其可供使用者使用。</span><span class="sxs-lookup"><span data-stu-id="27e54-106">Now you have to test it and to make it available to users.</span></span> <span data-ttu-id="27e54-107">其步驟非常類似於可以為 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 建立之所有類型的自訂物件。</span><span class="sxs-lookup"><span data-stu-id="27e54-107">The steps are very similar for all the types of custom objects that you can create for [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span>

 <span data-ttu-id="27e54-108">以下是您在建立、部署及偵錯它時所要遵循的步驟：</span><span class="sxs-lookup"><span data-stu-id="27e54-108">Here are the steps that you follow in building, deploying, and debugging it:</span></span>

1.  <span data-ttu-id="27e54-109">[簽署](#signing)要使用強式名稱產生的組件。</span><span class="sxs-lookup"><span data-stu-id="27e54-109">[Sign](#signing) the assembly to be generated with a strong name.</span></span>

2.  <span data-ttu-id="27e54-110">[建置](#building)組件。</span><span class="sxs-lookup"><span data-stu-id="27e54-110">[Build](#building) the assembly.</span></span>

3.  <span data-ttu-id="27e54-111">將組件移至或複製至適當的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 資料夾，以[部署](#deploying)組件。</span><span class="sxs-lookup"><span data-stu-id="27e54-111">[Deploy](#deploying) the assembly by moving or copying it to the appropriate [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] folder.</span></span>

4.  <span data-ttu-id="27e54-112">在全域組件快取 (GAC) 中[安裝](#installing)組件。</span><span class="sxs-lookup"><span data-stu-id="27e54-112">[Install](#installing) the assembly in the global assembly cache (GAC).</span></span>

     <span data-ttu-id="27e54-113">此物件會自動加入工具箱。</span><span class="sxs-lookup"><span data-stu-id="27e54-113">The object is automatically added to the Toolbox.</span></span>

5.  <span data-ttu-id="27e54-114">必要時，可以為部署進行[疑難排解](#troubleshooting)。</span><span class="sxs-lookup"><span data-stu-id="27e54-114">[Troubleshoot](#troubleshooting) the deployment, if necessary.</span></span>

6.  <span data-ttu-id="27e54-115">[測試](#testing)和偵錯您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="27e54-115">[Test](#testing) and debug your code.</span></span>

##  <a name="signing-the-assembly"></a><a name="signing"></a> <span data-ttu-id="27e54-116">簽署組件</span><span class="sxs-lookup"><span data-stu-id="27e54-116">Signing the Assembly</span></span>
 <span data-ttu-id="27e54-117">當要共用某個組件時，必須在全域組件快取中安裝它。</span><span class="sxs-lookup"><span data-stu-id="27e54-117">When an assembly is meant to be shared, it must be installed in the global assembly cache.</span></span> <span data-ttu-id="27e54-118">將組件加入至全域組件快取之後，類似 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 的應用程式就可以使用該組件。</span><span class="sxs-lookup"><span data-stu-id="27e54-118">After the assembly has been added to the global assembly cache, the assembly can be used by applications such as [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="27e54-119">全域組件快取的要求是組件必須以強式名稱簽署，以確保組件是全域唯一的。</span><span class="sxs-lookup"><span data-stu-id="27e54-119">A requirement of the global assembly cache is that the assembly must be signed with a strong name, which guarantees that an assembly is globally unique.</span></span> <span data-ttu-id="27e54-120">強式名稱的組件具有包含組件名稱、文化特性、公開金鑰和版本號碼的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="27e54-120">A strong-named assembly has a fully qualified name that includes the name, culture, public key, and version number of the assembly.</span></span> <span data-ttu-id="27e54-121">執行階段會使用這項資訊找出該組件，並和其他同名的組件區別。</span><span class="sxs-lookup"><span data-stu-id="27e54-121">The runtime uses this information to locate the assembly and to differentiate it from other assemblies with the same name.</span></span>

 <span data-ttu-id="27e54-122">若要使用強式名稱簽署組件，您必須先擁有或是建立公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="27e54-122">To sign an assembly with a strong name, you must first have or create a public/private key pair.</span></span> <span data-ttu-id="27e54-123">這個公開和私密密碼編譯金鑰組將在建立時期用來建立強式名稱的組件。</span><span class="sxs-lookup"><span data-stu-id="27e54-123">This public and private cryptographic key pair is used at build time to create a strong-named assembly.</span></span>

 <span data-ttu-id="27e54-124">如需有關強式名稱以及簽署組件時必須遵循之步驟的詳細資訊，請參閱在 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 文件中的下列主題：</span><span class="sxs-lookup"><span data-stu-id="27e54-124">For more information about strong names and on the steps that you must followto sign an assembly, see the following topics in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation:</span></span>

-   <span data-ttu-id="27e54-125">強式名稱的組件</span><span class="sxs-lookup"><span data-stu-id="27e54-125">Strong-Named Assemblies</span></span>

-   <span data-ttu-id="27e54-126">建立金鑰組</span><span class="sxs-lookup"><span data-stu-id="27e54-126">Creating a Key Pair</span></span>

-   <span data-ttu-id="27e54-127">使用強式名稱簽署組件</span><span class="sxs-lookup"><span data-stu-id="27e54-127">Signing an Assembly with a Strong Name</span></span>

 <span data-ttu-id="27e54-128">您可以在建立時期使用 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 中的強式名稱輕鬆地簽署組件。</span><span class="sxs-lookup"><span data-stu-id="27e54-128">You can easily sign your assembly with a strong name in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] at build time.</span></span> <span data-ttu-id="27e54-129">在 [**專案屬性**] 對話方塊中，選取 [**簽署**] 索引標籤。選取 [**簽署元件**] 選項，然後提供金鑰的路徑 ( .snk) 檔案。</span><span class="sxs-lookup"><span data-stu-id="27e54-129">In the **Project Properties** dialog box, select the **Signing** tab. Select the option to **Sign the assembly** and then provide the path of the key (.snk) file.</span></span>

##  <a name="building-the-assembly"></a><a name="building"></a> <span data-ttu-id="27e54-130">建置組件</span><span class="sxs-lookup"><span data-stu-id="27e54-130">Building the Assembly</span></span>
 <span data-ttu-id="27e54-131">在簽署專案之後，您必須使用 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 的 [建置]\*\*\*\* 功能表上可用的命令，以建置或重建專案或是解決方案。</span><span class="sxs-lookup"><span data-stu-id="27e54-131">After signing the project, you must build or rebuild the project or the solution by using the commands available on the **Build** menu of [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="27e54-132">您的方案可能包含自訂使用者介面的個別專案，它也必須以強式名稱簽署，而且可以同時建立。</span><span class="sxs-lookup"><span data-stu-id="27e54-132">Your solution may contain a separate project for a custom user interface, which must also be signed with a strong name, and can be built at the same time.</span></span>

 <span data-ttu-id="27e54-133">執行接下來兩個步驟 (部署組件以及在全域組件快取中加以安裝) 的最方便方法，就是在 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 中將這些步驟撰寫成建置後事件。</span><span class="sxs-lookup"><span data-stu-id="27e54-133">The most convenient method for performing the next two steps-deploying the assembly and installing it in the global assembly cache-is to script these steps as a post-build event in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="27e54-134">建置事件可從 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 專案上 [專案屬性] 的 [編譯]\*\*\*\* 頁面取得，以及從 C# 專案的 [建置事件]\*\*\*\* 頁面取得。</span><span class="sxs-lookup"><span data-stu-id="27e54-134">Build events are available from the **Compile** page of Project Properties for a [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] project, and from the **Build Events** page for a C# project.</span></span> <span data-ttu-id="27e54-135">**gacutil.exe** 這類的命令提示字元公用程式需要完整路徑。</span><span class="sxs-lookup"><span data-stu-id="27e54-135">The full path is required for command prompt utilities such as **gacutil.exe**.</span></span> <span data-ttu-id="27e54-136">凡包含空格的路徑，以及會使用到包含空格之路徑的巨集 (例如 $(TargetPath))，皆必須括以引號。</span><span class="sxs-lookup"><span data-stu-id="27e54-136">Quotation marks are required both around paths that contain spaces and around macros such as $(TargetPath) that expand to paths that contain spaces.</span></span>

 <span data-ttu-id="27e54-137">以下是自訂記錄提供者的建置後事件命令列範例：</span><span class="sxs-lookup"><span data-stu-id="27e54-137">Here is an example of a post-build event command line for a custom log provider:</span></span>

```
"C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0A\bin\NETFX 4.0 Tools\gacutil.exe" -u $(TargetName)
"C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0A\bin\NETFX 4.0 Tools\gacutil.exe" -i $(TargetFileName)
copy $(TargetFileName) "C:\Program Files\Microsoft SQL Server\120\DTS\LogProviders "
```

##  <a name="deploying-the-assembly"></a><a name="deploying"></a> <span data-ttu-id="27e54-138">部署組件</span><span class="sxs-lookup"><span data-stu-id="27e54-138">Deploying the Assembly</span></span>
 <span data-ttu-id="27e54-139">[!INCLUDE[ssIS](../../includes/ssis-md.md)]設計工具會藉由列舉在安裝時所建立的一系列資料夾中找到的檔案，來尋找可在封裝中使用的自訂物件 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="27e54-139">The [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer locates the custom objects available for use in packages by enumerating the files found in a series of folders that are created when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] is installed.</span></span> <span data-ttu-id="27e54-140">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用預設安裝設定時，這組資料夾位於**C:\PROGRAM Files\Microsoft SQL Server\120\DTS**。</span><span class="sxs-lookup"><span data-stu-id="27e54-140">When the default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation settings are used, this set of folders is located under **C:\Program Files\Microsoft SQL Server\120\DTS**.</span></span> <span data-ttu-id="27e54-141">不過，如果您為自訂物件建立安裝程式，則應該檢查**HKEY_LOCAL_MACHINE \SOFTWARE\MICROSOFT\MICROSOFT SQL Server\120\SSIS\Setup\DtsPath**登錄機碼的值，以確認此資料夾的位置。</span><span class="sxs-lookup"><span data-stu-id="27e54-141">However if you create a setup program for your custom object, you should check the value of the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\SSIS\Setup\DtsPath** registry key to verify the location of this folder.</span></span>

 <span data-ttu-id="27e54-142">您可以透過下列兩種方式將組件放入資料夾中：</span><span class="sxs-lookup"><span data-stu-id="27e54-142">You can put the assembly in the folder in two ways:</span></span>

-   <span data-ttu-id="27e54-143">在建立編譯的組件之後，將它移動或複製到適當的資料夾 </span><span class="sxs-lookup"><span data-stu-id="27e54-143">Move or copy the compiled assembly to the appropriate folder after building it.</span></span> <span data-ttu-id="27e54-144">(為了方便起見，您可以在建置後事件中包括複製命令)。</span><span class="sxs-lookup"><span data-stu-id="27e54-144">(For convenience, you can include the copy command in a Post-build Event.)</span></span>

-   <span data-ttu-id="27e54-145">直接在適當的資料夾中建置組件。</span><span class="sxs-lookup"><span data-stu-id="27e54-145">Build the assembly directly in the appropriate folder.</span></span>

 <span data-ttu-id="27e54-146">**C:\Program FILES\MICROSOFT SQL Server\120\DTS**下的下列部署資料夾會用於各種類型的自訂物件：</span><span class="sxs-lookup"><span data-stu-id="27e54-146">The following deployment folders under **C:\Program Files\Microsoft SQL Server\120\DTS** are used for the various types of custom objects:</span></span>

|<span data-ttu-id="27e54-147">自訂物件</span><span class="sxs-lookup"><span data-stu-id="27e54-147">Custom object</span></span>|<span data-ttu-id="27e54-148">部署資料夾</span><span class="sxs-lookup"><span data-stu-id="27e54-148">Deployment folder</span></span>|
|-------------------|-----------------------|
|<span data-ttu-id="27e54-149">Task</span><span class="sxs-lookup"><span data-stu-id="27e54-149">Task</span></span>|<span data-ttu-id="27e54-150">工作</span><span class="sxs-lookup"><span data-stu-id="27e54-150">Tasks</span></span>|
|<span data-ttu-id="27e54-151">[ODBC 來源編輯器]</span><span class="sxs-lookup"><span data-stu-id="27e54-151">Connection manager</span></span>|<span data-ttu-id="27e54-152">連接</span><span class="sxs-lookup"><span data-stu-id="27e54-152">Connections</span></span>|
|<span data-ttu-id="27e54-153">記錄提供者</span><span class="sxs-lookup"><span data-stu-id="27e54-153">Log provider</span></span>|<span data-ttu-id="27e54-154">LogProviders</span><span class="sxs-lookup"><span data-stu-id="27e54-154">LogProviders</span></span>|
|<span data-ttu-id="27e54-155">資料流程元件</span><span class="sxs-lookup"><span data-stu-id="27e54-155">Data flow component</span></span>|<span data-ttu-id="27e54-156">PipelineComponents</span><span class="sxs-lookup"><span data-stu-id="27e54-156">PipelineComponents</span></span>|

> [!NOTE]
>  <span data-ttu-id="27e54-157">將組件複製到這些資料夾中，以支援可用工作、連接管理員等項目的列舉。</span><span class="sxs-lookup"><span data-stu-id="27e54-157">Assemblies are copied to these folders to support the enumeration of available tasks, connection managers, and so on.</span></span> <span data-ttu-id="27e54-158">因此，您不必將只包含自訂物件之自訂使用者介面的組件部署到這些資料夾。</span><span class="sxs-lookup"><span data-stu-id="27e54-158">Therefore you do not have to deploy assemblies that contain only the custom user interface for custom objects to these folders.</span></span>

##  <a name="installing-the-assembly-in-the-global-assembly-cache"></a><a name="installing"></a> <span data-ttu-id="27e54-159">在全域組件快取中安裝組件</span><span class="sxs-lookup"><span data-stu-id="27e54-159">Installing the Assembly in the Global Assembly Cache</span></span>
 <span data-ttu-id="27e54-160">若要將工作組件安裝至全域組件快取 (GAC)，請使用命令列工具 **gacutil.exe**，或是將組件拖曳至 `%system%\assembly` 目錄。</span><span class="sxs-lookup"><span data-stu-id="27e54-160">To install the task assembly into the global assembly cache (GAC), use the command line tool **gacutil.exe**, or drag the assemblies to the `%system%\assembly` directory.</span></span> <span data-ttu-id="27e54-161">為了方便起見，您也可以在建置後事件中新增 **gacutil.exe** 呼叫。</span><span class="sxs-lookup"><span data-stu-id="27e54-161">For convenience, you can also include the call to **gacutil.exe** in a Post-build Event.</span></span>

 <span data-ttu-id="27e54-162">下列命令會使用 **gacutil.exe** 將名為 *MyTask.dll* 的元件安裝至 GAC。</span><span class="sxs-lookup"><span data-stu-id="27e54-162">The following command installs a component named *MyTask.dll* into the GAC by using **gacutil.exe**.</span></span>

 `gacutil /iF MyTask.dll`

 <span data-ttu-id="27e54-163">您必須在安裝新版本的自訂物件之後，關閉並重新開啟 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計工具。</span><span class="sxs-lookup"><span data-stu-id="27e54-163">You must close and reopen [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer after you install a new version of your custom object.</span></span> <span data-ttu-id="27e54-164">如果您已在全域組件快取中安裝舊版的自訂物件，必須在安裝新版本之前先將之移除。</span><span class="sxs-lookup"><span data-stu-id="27e54-164">If you have installed earlier versions of your custom object in the global assembly cache, you must remove them before installing the new version.</span></span> <span data-ttu-id="27e54-165">若要解除安裝組件，請執行 **gacutil.exe**，並使用 `/u` 選項指定組件名稱。</span><span class="sxs-lookup"><span data-stu-id="27e54-165">To uninstall an assembly, run **gacutil.exe** and specify the assembly name with the `/u` option.</span></span>

 <span data-ttu-id="27e54-166">如需全域組件快取的詳細資訊，請參閱 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 工具中的全域組件快取工具 (Gactutil.exe)。</span><span class="sxs-lookup"><span data-stu-id="27e54-166">For more information about the global assembly cache, see Global Assembly Cache Tool (Gactutil.exe) in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Tools.</span></span>

##  <a name="troubleshooting-the-deployment"></a><a name="troubleshooting"></a> <span data-ttu-id="27e54-167">針對部署進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="27e54-167">Troubleshooting the Deployment</span></span>
 <span data-ttu-id="27e54-168">如果您的自訂物件出現在 [工具箱]\*\*\*\* 或可用物件清單中，但您無法將它新增至套件，請嘗試下列動作：</span><span class="sxs-lookup"><span data-stu-id="27e54-168">If your custom object appears in the **Toolbox** or the list of available objects, but you are not able to add it to a package, try the following:</span></span>

1.  <span data-ttu-id="27e54-169">查詢全域組件快取，以取得元件的多個版本。</span><span class="sxs-lookup"><span data-stu-id="27e54-169">Look in the global assembly cache for multiple versions of your component.</span></span> <span data-ttu-id="27e54-170">如果在全域組件快取中有多個版本的元件，設計師可能無法載入您的元件。</span><span class="sxs-lookup"><span data-stu-id="27e54-170">If there are multiple versions of the component in the global assembly cache, the designer may not be able to load your component.</span></span> <span data-ttu-id="27e54-171">從全域組件快取中刪除此組件的所有執行個體，然後重新加入該組件。</span><span class="sxs-lookup"><span data-stu-id="27e54-171">Delete all instances of the assembly from the global assembly cache, and re-add the assembly.</span></span>

2.  <span data-ttu-id="27e54-172">請確定部署資料夾中只包含一個該組件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="27e54-172">Make sure that only a single instance of the assembly exists in the deployment folder.</span></span>

3.  <span data-ttu-id="27e54-173">重新整理工具箱。</span><span class="sxs-lookup"><span data-stu-id="27e54-173">Refresh the Toolbox.</span></span>

4.  <span data-ttu-id="27e54-174">將 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 附加至 **devenv.exe**，並設定中斷點，以逐步完成初始化程式碼，從而確保不會發生任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="27e54-174">Attach [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] to **devenv.exe** and set a breakpoint to step through your initialization code to ensure that no exceptions occur.</span></span>

##  <a name="testing-and-debugging-your-code"></a><a name="testing"></a> <span data-ttu-id="27e54-175">測試和偵錯您的程式碼</span><span class="sxs-lookup"><span data-stu-id="27e54-175">Testing and Debugging Your Code</span></span>
 <span data-ttu-id="27e54-176">在建置自訂物件以及執行可使用該元件的套件之後，從 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 啟動 **dtexec.exe** 是偵錯自訂物件之執行階段方法的最簡單方法。</span><span class="sxs-lookup"><span data-stu-id="27e54-176">The simplest approach to debugging the run-time methods of a custom object is to start **dtexec.exe** from [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] after building your custom object and run a package that uses the component.</span></span>

 <span data-ttu-id="27e54-177">如果您想要對元件的設計階段方法（例如方法）進行偵錯工具，請 `Validate` 開啟使用第二個實例中之元件的封裝 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ，並附加至其**devenv.exe**進程。</span><span class="sxs-lookup"><span data-stu-id="27e54-177">If you want to debug the component's design-time methods, such as the `Validate` method, open a package that uses the component in a second instance of [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], and attach to its **devenv.exe** process.</span></span>

 <span data-ttu-id="27e54-178">如果您也想要在套件於 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計工具中開啟與執行時偵錯元件的執行階段方法，則必須在執行套件時強制暫停，才可附加到 **DtsDebugHost.exe** 處理序。</span><span class="sxs-lookup"><span data-stu-id="27e54-178">If you also want to debug the component's run-time methods when a package is open and running in [!INCLUDE[ssIS](../../includes/ssis-md.md)] designer, you must force a pause in the execution of the package so that you can also attach to the **DtsDebugHost.exe** process.</span></span>

#### <a name="to-debug-an-objects-run-time-methods-by-attaching-to-dtexecexe"></a><span data-ttu-id="27e54-179">附加到 dtexec.exe 偵錯物件的執行階段方法</span><span class="sxs-lookup"><span data-stu-id="27e54-179">To debug an object's run-time methods by attaching to dtexec.exe</span></span>

1.  <span data-ttu-id="27e54-180">在偵錯組態中簽署和建立專案，然後加以部署，並將它安裝在全域組件快取中，如本主題所述。</span><span class="sxs-lookup"><span data-stu-id="27e54-180">Sign and build your project in the Debug configuration, deploy it, and install it in the global assembly cache as described in this topic.</span></span>

2.  <span data-ttu-id="27e54-181">在 [**專案屬性**] 的 [**調試**程式] 索引標籤上，選取 [**啟動外部程式**] 做為 [**起始動作**]，然後找出預設會安裝在 C:\Program Files\Microsoft SQL server\120\dts\binn 中的**dtexec.exe**。</span><span class="sxs-lookup"><span data-stu-id="27e54-181">On the **Debug** tab of **Project Properties**, select **Start external program** as the **Start Action**, and locate **dtexec.exe**, which is installed by default in C:\Program Files\Microsoft SQL Server\120\DTS\Binn.</span></span>

3.  <span data-ttu-id="27e54-182">在 [命令列選項]\*\*\*\* 文字方塊的 [起始選項]\*\*\*\* 之下，輸入執行可使用您的元件之套件所需的命令列引數。</span><span class="sxs-lookup"><span data-stu-id="27e54-182">In the **Command line options** text box, under **Start Options**, enter the command line arguments required to run a package that uses your component.</span></span> <span data-ttu-id="27e54-183">通常命令列引數是由 /F[ILE] 參數以及緊接在後面之 .dtsx 檔案的路徑與檔案名稱所組成。</span><span class="sxs-lookup"><span data-stu-id="27e54-183">Often the command-line argument will consist of the /F[ILE] switch followed by the path and file name of the .dtsx file.</span></span> <span data-ttu-id="27e54-184">如需詳細資訊，請參閱 [dtexec Utility](../packages/dtexec-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="27e54-184">For more information, see [dtexec Utility](../packages/dtexec-utility.md).</span></span>

4.  <span data-ttu-id="27e54-185">在原始程式碼中設定中斷點，設定之處必須適合元件的執行階段方法。</span><span class="sxs-lookup"><span data-stu-id="27e54-185">Set breakpoints in the source code where appropriate in the run-time methods of your component.</span></span>

5.  <span data-ttu-id="27e54-186">執行您的專案。</span><span class="sxs-lookup"><span data-stu-id="27e54-186">Run your project.</span></span>

#### <a name="to-debug-a-custom-objects-design-time-methods-by-attaching-to-sql-server-data-tools"></a><span data-ttu-id="27e54-187">若要將自訂物件的設計階段方法附加到 SQL Server Data Tools 以進行偵錯</span><span class="sxs-lookup"><span data-stu-id="27e54-187">To debug a custom object's design-time methods by attaching to SQL Server Data Tools</span></span>

1.  <span data-ttu-id="27e54-188">在偵錯組態中簽署和建立專案，然後加以部署，並將它安裝在全域組件快取中，如本主題所述。</span><span class="sxs-lookup"><span data-stu-id="27e54-188">Sign and build your project in the Debug configuration, deploy it, and install it in the global assembly cache as described in this topic.</span></span>

2.  <span data-ttu-id="27e54-189">在原始程式碼中設定中斷點，設定之處必須適合自訂物件的設計階段方法。</span><span class="sxs-lookup"><span data-stu-id="27e54-189">Set breakpoints in the source code where appropriate in the design-time methods of your custom object.</span></span>

3.  <span data-ttu-id="27e54-190">開啟第二個 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 執行個體，並載入 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案，該專案包含使用自訂物件的封裝。</span><span class="sxs-lookup"><span data-stu-id="27e54-190">Open a second instance of [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] and load an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains a package that uses the custom object.</span></span>

4.  <span data-ttu-id="27e54-191">從第一個 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 執行個體的 [偵錯]\*\*\*\* 功能表中，選取 [附加至處理序]\*\*\*\* 載入套件，以從第一個執行個體附加到第二個 **devenv.exe** 執行個體。</span><span class="sxs-lookup"><span data-stu-id="27e54-191">From the first instance of [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], attach to the second instance of **devenv.exe** in which the package is loaded by selecting **Attach to Process** from the **Debug** menu of the first instance.</span></span>

5.  <span data-ttu-id="27e54-192">從第二個 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 執行個體執行封裝。</span><span class="sxs-lookup"><span data-stu-id="27e54-192">Run the package from the second instance of [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].</span></span>

#### <a name="to-debug-a-custom-objects-run-time-methods-by-attaching-to-sql-server-data-tools"></a><span data-ttu-id="27e54-193">若要將自訂物件的執行階段方法附加到 SQL Server Data Tools 以進行偵錯</span><span class="sxs-lookup"><span data-stu-id="27e54-193">To debug a custom object's run-time methods by attaching to SQL Server Data Tools</span></span>

1.  <span data-ttu-id="27e54-194">完成前一個程序所列的步驟之後，請強制暫停套件的執行，以附加到 **DtsDebugHost.exe**。</span><span class="sxs-lookup"><span data-stu-id="27e54-194">After you have completed the steps listed in the previous procedure, force a pause in the execution of your package so that you can attach to **DtsDebugHost.exe**.</span></span> <span data-ttu-id="27e54-195">如果要強制執行此暫停動作，可以將中斷點加入 `OnPreExecute` 事件，或將指令碼工作加入專案，並輸入可顯示強制回應訊息方塊的指令碼。</span><span class="sxs-lookup"><span data-stu-id="27e54-195">You can force this pause by adding a breakpoint to the `OnPreExecute` event, or by adding a Script task to your project and entering script that displays a modal message box.</span></span>

2.  <span data-ttu-id="27e54-196">執行封裝。</span><span class="sxs-lookup"><span data-stu-id="27e54-196">Run the package.</span></span> <span data-ttu-id="27e54-197">暫停發生時，請切換至已開啟程式碼專案的 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 執行個體，然後從 [偵錯]\*\*\*\* 功能表中選取 [附加至處理序]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="27e54-197">When the pause occurs, switch to the instance of [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] in which your code project is open, and select **Attach to Process** from the **Debug** menu.</span></span> <span data-ttu-id="27e54-198">請務必附加至 [類型]\*\*\*\* 資料行中列為 **Managed, x86** 的 **DtsDebugHost.exe** 執行個體，而不只是附加至列為 **x86** 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="27e54-198">Make sure to attach to the instance of **DtsDebugHost.exe** listed as **Managed, x86** in the **Type** column, not to the instance listed as **x86** only.</span></span>

3.  <span data-ttu-id="27e54-199">返回暫停的套件並繼續略過中斷點，或是按一下 [確定]\*\*\*\* 以解除指令碼工作所引發的訊息方塊，然後繼續套件執行和偵錯。</span><span class="sxs-lookup"><span data-stu-id="27e54-199">Return to the paused package and continue past the breakpoint, or click **OK** to dismiss the message box raised by the Script task, and continue package execution and debugging.</span></span>

<span data-ttu-id="27e54-200">![Integration Services 圖示 (小型) ](../media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="27e54-200">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="27e54-201">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="27e54-201">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="27e54-202">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="27e54-202">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="27e54-203">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="27e54-203">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="27e54-204">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27e54-204">See Also</span></span>
 <span data-ttu-id="27e54-205">[開發自訂物件以 Integration Services](developing-custom-objects-for-integration-services.md) [保存自訂物件](persisting-custom-objects.md)[疑難排解封裝開發的工具](../troubleshooting/troubleshooting-tools-for-package-development.md)</span><span class="sxs-lookup"><span data-stu-id="27e54-205">[Developing Custom Objects for Integration Services](developing-custom-objects-for-integration-services.md) [Persisting Custom Objects](persisting-custom-objects.md) [Troubleshooting Tools for Package Development](../troubleshooting/troubleshooting-tools-for-package-development.md)</span></span>


