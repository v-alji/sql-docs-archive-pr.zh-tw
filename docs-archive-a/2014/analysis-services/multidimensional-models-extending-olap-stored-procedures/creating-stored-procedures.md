---
title: 建立預存程式 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- registering assemblies
- database assemblies [Analysis Services]
- server assemblies [Analysis Services]
- stored procedures [Analysis Services], creating
- assemblies [Analysis Services]
ms.assetid: a12ff02f-6d0b-4488-9846-3609fc0d0554
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9a997244a2d54cca8732196107dd21927b5f9e2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700438"
---
# <a name="creating-stored-procedures"></a><span data-ttu-id="d684d-102">建立預存程序</span><span class="sxs-lookup"><span data-stu-id="d684d-102">Creating Stored Procedures</span></span>
  <span data-ttu-id="d684d-103">所有預存程序都必須與 Common Language Runtime (CLR) 或元件物件模型 (COM) 類別建立關聯，才能使用。</span><span class="sxs-lookup"><span data-stu-id="d684d-103">All stored procedures must be associated with a common language runtime (CLR) or Component Object Model (COM) class in order to be used.</span></span> <span data-ttu-id="d684d-104">類別必須安裝在伺服器上-通常是以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX®動態連結程式庫的形式， (DLL) ，並在伺服器或資料庫中註冊為元件 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d684d-104">The class must be installed on the server - usually in the form of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX® dynamic link library (DLL) - and registered as an assembly on the server or in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="d684d-105">預存程序是在伺服器或資料庫上註冊。</span><span class="sxs-lookup"><span data-stu-id="d684d-105">Stored procedures are registered on a server or on a database.</span></span> <span data-ttu-id="d684d-106">可以從任何查詢內容呼叫伺服器預存程序。</span><span class="sxs-lookup"><span data-stu-id="d684d-106">Server stored procedures can be called from any query context.</span></span> <span data-ttu-id="d684d-107">只有資料庫內容是為預存程序定義的資料庫時，才能存取資料庫預存程序。</span><span class="sxs-lookup"><span data-stu-id="d684d-107">Database stored procedures can only be accessed if the database context is the database under which the stored procedure is defined.</span></span> <span data-ttu-id="d684d-108">如果某個組件中的函數呼叫其他組件中的函數，您必須將兩個組件註冊在相同內容 (伺服器或資料庫) 中。</span><span class="sxs-lookup"><span data-stu-id="d684d-108">If functions in one assembly call functions in a different assembly, you must register both assemblies in the same context (server or database).</span></span> <span data-ttu-id="d684d-109">如果是伺服器或伺服器上已部署的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫，您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 來註冊元件。</span><span class="sxs-lookup"><span data-stu-id="d684d-109">For a server or a deployed [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database on a server, you can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to register an assembly.</span></span> <span data-ttu-id="d684d-110">如果是 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案，您可使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 設計師在專案中註冊組件。</span><span class="sxs-lookup"><span data-stu-id="d684d-110">For an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, you can use [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Designer to register an assembly in the project.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d684d-111">COM 組件可能會造成安全性風險。</span><span class="sxs-lookup"><span data-stu-id="d684d-111">COM assemblies might pose a security risk.</span></span> <span data-ttu-id="d684d-112">由於這項風險和其他考量，COM 組件在 [!INCLUDE[ssASversion10](../../includes/ssasversion10-md.md)]中已經被取代。</span><span class="sxs-lookup"><span data-stu-id="d684d-112">Due to this risk and other considerations, COM assemblies were deprecated in [!INCLUDE[ssASversion10](../../includes/ssasversion10-md.md)].</span></span> <span data-ttu-id="d684d-113">在未來的版本中，可能不再支援 COM 組件。</span><span class="sxs-lookup"><span data-stu-id="d684d-113">COM assemblies might not be supported in future releases.</span></span>  
  
## <a name="registering-a-server-assembly"></a><span data-ttu-id="d684d-114">註冊伺服器組件</span><span class="sxs-lookup"><span data-stu-id="d684d-114">Registering a Server Assembly</span></span>  
 <span data-ttu-id="d684d-115">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的物件總管中，伺服器組件會在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體下的 [組件] 資料夾中列出。</span><span class="sxs-lookup"><span data-stu-id="d684d-115">In Object Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], server assemblies are listed in the Assemblies folder under an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="d684d-116">伺服器組件可以同時包含 .NET (CLR) 組件與 COM 程式庫。</span><span class="sxs-lookup"><span data-stu-id="d684d-116">Server assemblies can contain both .NET (CLR) assemblies and COM libraries.</span></span>  
  
### <a name="to-create-a-server-assembly"></a><span data-ttu-id="d684d-117">建立伺服器組件</span><span class="sxs-lookup"><span data-stu-id="d684d-117">To create a server assembly</span></span>  
  
1.  <span data-ttu-id="d684d-118">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]在物件總管中展開的實例，以滑鼠右鍵按一下 [**元件**] 資料夾，然後按一下 [**新增元件**]。</span><span class="sxs-lookup"><span data-stu-id="d684d-118">Expand the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in Object Explorer, right-click the **Assemblies** folder, and then click **New Assembly**.</span></span> <span data-ttu-id="d684d-119">這會顯示 [**註冊伺服器元件**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d684d-119">This displays the **Register Server Assembly** dialog box.</span></span>  
  
2.  <span data-ttu-id="d684d-120">針對 [**類型**]，指定元件的類型：</span><span class="sxs-lookup"><span data-stu-id="d684d-120">For **Type** specify the type of assembly:</span></span>  
  
    -   <span data-ttu-id="d684d-121">針對 Managed 程式碼 (CLR) DLL，請指定 .NET 組件。</span><span class="sxs-lookup"><span data-stu-id="d684d-121">For a managed code (CLR) DLL, specify .NET Assembly.</span></span>  
  
    -   <span data-ttu-id="d684d-122">若是機器碼 (COM) DLL，請指定 COM DLL。</span><span class="sxs-lookup"><span data-stu-id="d684d-122">For a native code (COM) DLL, specify COM DLL.</span></span>  
  
3.  <span data-ttu-id="d684d-123">針對 [**檔案名**]，指定包含預存程式的 DLL。</span><span class="sxs-lookup"><span data-stu-id="d684d-123">For **File name**, specify the DLL containing the stored procedures.</span></span>  
  
4.  <span data-ttu-id="d684d-124">針對 [**元件名稱**]，指定元件的名稱。</span><span class="sxs-lookup"><span data-stu-id="d684d-124">For **Assembly name**, specify a name for the assembly.</span></span>  
  
5.  <span data-ttu-id="d684d-125">如果這是您要用來進行預存程式之程式庫的偵錯工具組建，請選取 [**包含 debug 資訊**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d684d-125">If this is a debug build of the library that you are going to use to debug stored procedures, select the **Include debug information** check box.</span></span> <span data-ttu-id="d684d-126">如需有關偵錯工具預存程式的詳細資訊，請參閱[偵錯工具預存程式](debugging-stored-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="d684d-126">For more information about debugging stored procedures, see [Debugging Stored Procedures](debugging-stored-procedures.md).</span></span>  
  
6.  <span data-ttu-id="d684d-127">您可以按一下 **[確定]** 立即註冊元件，或在對話方塊工具列上，按一下 [**腳本**] 功能表上的命令，將註冊動作的腳本編寫為查詢視窗、檔案或剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="d684d-127">You can click **OK** to register the assembly immediately, or on the dialog box toolbar, you can click a command on the **Script** menu to script the registration action to a query window, a file, or the Clipboard.</span></span>  
  
 <span data-ttu-id="d684d-128">註冊伺服器元件之後，您可以在物件總管中的元件上按一下滑鼠右鍵，然後按一下 [**屬性**] 來設定它。</span><span class="sxs-lookup"><span data-stu-id="d684d-128">After you register a server assembly, you can configure it by right-clicking the assembly in Object Explorer and then clicking **Properties**.</span></span>  
  
## <a name="registering-a-database-assembly-on-the-server"></a><span data-ttu-id="d684d-129">在伺服器上註冊資料庫組件</span><span class="sxs-lookup"><span data-stu-id="d684d-129">Registering a Database Assembly on the Server</span></span>  
 <span data-ttu-id="d684d-130">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的物件總管中，伺服器組件會在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫下的 [組件] 資料夾中列出。</span><span class="sxs-lookup"><span data-stu-id="d684d-130">In Object Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], database assemblies are listed in the Assemblies folder under an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="d684d-131">資料庫組件可以同時包含 .NET (CLR) 組件和 COM 程式庫。</span><span class="sxs-lookup"><span data-stu-id="d684d-131">Database assemblies can contain both .NET (CLR) assemblies and COM libraries.</span></span>  
  
### <a name="to-create-a-database-assembly-on-a-server"></a><span data-ttu-id="d684d-132">在伺服器上建立資料庫組件</span><span class="sxs-lookup"><span data-stu-id="d684d-132">To create a database assembly on a server</span></span>  
  
1.  <span data-ttu-id="d684d-133">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]在 [物件總管中展開資料庫的實例，以滑鼠右鍵按一下 [**元件**] 資料夾，然後按一下 [**新增元件**]。</span><span class="sxs-lookup"><span data-stu-id="d684d-133">Expand the instance the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in Object Explorer, right-click the **Assemblies** folder, and then click **New Assembly**.</span></span> <span data-ttu-id="d684d-134">這會顯示 [**註冊資料庫元件**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d684d-134">This displays the **Register Database Assembly** dialog box.</span></span>  
  
2.  <span data-ttu-id="d684d-135">針對 [**類型**]，指定元件的類型：</span><span class="sxs-lookup"><span data-stu-id="d684d-135">For **Type** specify the type of assembly:</span></span>  
  
    -   <span data-ttu-id="d684d-136">針對 Managed 程式碼 (CLR) DLL，請指定 .NET 組件。</span><span class="sxs-lookup"><span data-stu-id="d684d-136">For a managed code (CLR) DLL, specify .NET Assembly.</span></span>  
  
    -   <span data-ttu-id="d684d-137">若是機器碼 (COM) DLL，請指定 COM DLL。</span><span class="sxs-lookup"><span data-stu-id="d684d-137">For a native code (COM) DLL), specify COM DLL.</span></span>  
  
3.  <span data-ttu-id="d684d-138">針對 [**檔案名**]，指定包含預存程式的 DLL。</span><span class="sxs-lookup"><span data-stu-id="d684d-138">For **File name**, specify the DLL containing the stored procedures.</span></span>  
  
4.  <span data-ttu-id="d684d-139">針對 [**元件名稱**]，指定元件的名稱。</span><span class="sxs-lookup"><span data-stu-id="d684d-139">For **Assembly name**, specify a name for the assembly.</span></span>  
  
5.  <span data-ttu-id="d684d-140">如果這是您要用來進行預存程式之程式庫的偵錯工具組建，請選取 [**包含 debug 資訊**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d684d-140">If this is a debug build of the library that you are going to use to debug stored procedures, select the **Include debug information** check box.</span></span> <span data-ttu-id="d684d-141">如需有關偵錯工具預存程式的詳細資訊，請參閱[偵錯工具預存程式](debugging-stored-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="d684d-141">For more information about debugging stored procedures, see [Debugging Stored Procedures](debugging-stored-procedures.md).</span></span>  
  
6.  <span data-ttu-id="d684d-142">您可以按一下 **[確定]** 立即註冊元件，或在對話方塊工具列上，按一下 [**腳本**] 功能表上的命令，將註冊動作的腳本編寫為查詢視窗、檔案或剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="d684d-142">You can click **OK** to register the assembly immediately, or on the dialog box toolbar, you can click a command on the **Script** menu to script the registration action to a query window, a file, or the Clipboard.</span></span>  
  
 <span data-ttu-id="d684d-143">註冊資料庫元件之後，您可以在物件總管中的元件上按一下滑鼠右鍵，然後按一下 [**屬性**] 來設定它。</span><span class="sxs-lookup"><span data-stu-id="d684d-143">After you register a database assembly, you can configure it by right-clicking the assembly in Object Explorer and then clicking **Properties**.</span></span>  
  
## <a name="registering-a-database-assembly-in-a-project"></a><span data-ttu-id="d684d-144">在專案中註冊資料庫組件</span><span class="sxs-lookup"><span data-stu-id="d684d-144">Registering a Database Assembly in a Project</span></span>  
 <span data-ttu-id="d684d-145">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 的方案總管中，資料庫組件會在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案下的 [組件] 資料夾中列出。</span><span class="sxs-lookup"><span data-stu-id="d684d-145">In Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], database assemblies are listed in the Assemblies folder under an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="d684d-146">資料庫組件可以同時包含 .NET (CLR) 組件和 COM 程式庫。</span><span class="sxs-lookup"><span data-stu-id="d684d-146">Database assemblies can contain both .NET (CLR) assemblies and COM libraries.</span></span>  
  
### <a name="to-create-a-database-assembly-in-an-analysis-service-project"></a><span data-ttu-id="d684d-147">在 Analysis Service 專案中建立資料庫組件</span><span class="sxs-lookup"><span data-stu-id="d684d-147">To create a database assembly in an Analysis Service project</span></span>  
  
1.  <span data-ttu-id="d684d-148">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]在 [物件總管中展開資料庫的實例，以滑鼠右鍵按一下 [**元件**] 資料夾，然後按一下 [**新增元件參考**]。</span><span class="sxs-lookup"><span data-stu-id="d684d-148">Expand the instance the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in Object Explorer, right-click the **Assemblies** folder, and then click **New Assembly Reference**.</span></span> <span data-ttu-id="d684d-149">這會顯示 [**加入參考**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d684d-149">This displays the **Add Reference** dialog box.</span></span> <span data-ttu-id="d684d-150">[**加入參考**] 對話方塊的 [ **.net** ] 索引標籤會列出現有的 .net (CLR) 元件，而 [**專案**] 索引標籤則會列出專案。</span><span class="sxs-lookup"><span data-stu-id="d684d-150">The **.NET** tab of the **Add Reference** dialog box lists existing .NET (CLR) assemblies, while the **Projects** tab lists projects.</span></span>  
  
2.  <span data-ttu-id="d684d-151">您可以按一下現有的元件或專案，然後按一下 [**新增**] 將它加入至 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="d684d-151">You can click an existing component or project and then click **Add** to add it to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="d684d-152">若要加入 COM DLL 的參考，請按一下 [**流覽**] 索引標籤來尋找檔案。</span><span class="sxs-lookup"><span data-stu-id="d684d-152">To add a reference to a COM DLL, click the **Browse** tab to find the file.</span></span> <span data-ttu-id="d684d-153">[**選取的專案和元件**] 清單會顯示您要新增至專案之每個元件的名稱、類型、版本和位置。</span><span class="sxs-lookup"><span data-stu-id="d684d-153">The **Selected projects and components** list shows the name, type, version, and location for each component that you are adding to the project.</span></span>  
  
3.  <span data-ttu-id="d684d-154">當您完成選取要加入的元件時，請按一下 **[確定]** 將其新增至 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="d684d-154">When you are finished selecting components to add, click **OK** to add them to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span>  
  
## <a name="script-format-for-an-assembly"></a><span data-ttu-id="d684d-155">組件的指令碼格式</span><span class="sxs-lookup"><span data-stu-id="d684d-155">Script Format For an Assembly</span></span>  
 <span data-ttu-id="d684d-156">註冊 .NET 組件相當地簡單。</span><span class="sxs-lookup"><span data-stu-id="d684d-156">Registering a .NET assembly is fairly simple.</span></span> <span data-ttu-id="d684d-157">.NET 組件會使用下列格式，以二進位格式加入資料庫中：</span><span class="sxs-lookup"><span data-stu-id="d684d-157">A .NET assembly is added to a database in binary format using the following format:</span></span>  
  
```  
<Create>  
   <ObjectDefinition>  
      <Assembly>  
         <Files>  
            <File>  
               <Name>filename</Name>  
               <Type>filetype</Type>  
               <Data>  
                  <Block>binarydatablock</Block>  
                  <Block>binarydatablock</Block>  
                  ...  
               </Data>  
            </File>  
         </Files>  
         <PermissionSet>PermissionSet</PermissionSet>  
      </Assembly>  
   <ObjectDefinition>  
</Create>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d684d-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d684d-158">See Also</span></span>  
 <span data-ttu-id="d684d-159">[多維度模型元件管理](../multidimensional-models/multidimensional-model-assemblies-management.md) </span><span class="sxs-lookup"><span data-stu-id="d684d-159">[Multidimensional Model Assemblies Management](../multidimensional-models/multidimensional-model-assemblies-management.md) </span></span>  
 [<span data-ttu-id="d684d-160">定義預存程式</span><span class="sxs-lookup"><span data-stu-id="d684d-160">Defining Stored Procedures</span></span>](defining-stored-procedures.md)  
  
  
