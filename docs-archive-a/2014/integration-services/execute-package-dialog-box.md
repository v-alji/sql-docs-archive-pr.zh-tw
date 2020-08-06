---
title: 執行封裝對話方塊 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.ispackageexecute.f1
- sql12.ssis.ssms.executepackage.f1
ms.assetid: 4f7a806d-4867-4d1f-bc65-b00c1caee7b6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1b60381054c781cd59f0a9d434710663b72d616c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596800"
---
# <a name="execute-package-dialog-box"></a><span data-ttu-id="0b935-102">Execute Package Dialog Box</span><span class="sxs-lookup"><span data-stu-id="0b935-102">Execute Package Dialog Box</span></span>
  <span data-ttu-id="0b935-103">使用 **[執行封裝]** 對話方塊，即可執行儲存在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 伺服器上的封裝。</span><span class="sxs-lookup"><span data-stu-id="0b935-103">Use the **Execute Package** dialog box to run a package that is stored on the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span>  
  
 <span data-ttu-id="0b935-104">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝可能會包含參考儲存在環境變數中之值的參數。</span><span class="sxs-lookup"><span data-stu-id="0b935-104">An [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package may contain parameters that values stored in environment variables.</span></span> <span data-ttu-id="0b935-105">在執行這種封裝前，您必須指定要使用何種環境來提供環境變數值。</span><span class="sxs-lookup"><span data-stu-id="0b935-105">Before executing such a package, you must specify which environment will be used to provide the environment variable values.</span></span> <span data-ttu-id="0b935-106">專案可能包含多個環境，但是執行期間只能使用一個環境來繫結環境變數值。</span><span class="sxs-lookup"><span data-stu-id="0b935-106">A project may contain multiple environments, but only one environment can be used for binding environment variable values at the time of execution.</span></span> <span data-ttu-id="0b935-107">如果封裝中沒有使用環境變數，就不需要環境。</span><span class="sxs-lookup"><span data-stu-id="0b935-107">If no environment variables are used in the package, an environment is not required.</span></span>  
  
 <span data-ttu-id="0b935-108">您想要做什麼事？</span><span class="sxs-lookup"><span data-stu-id="0b935-108">What do you want to do?</span></span>  
  
-   <span data-ttu-id="0b935-109">[開啟 [執行封裝] 對話方塊](#open_dialog)</span><span class="sxs-lookup"><span data-stu-id="0b935-109">[Open the Execute Package dialog box](#open_dialog)</span></span>  
  
-   <span data-ttu-id="0b935-110">[設定 [一般] 頁面上的 [選項]](#general)</span><span class="sxs-lookup"><span data-stu-id="0b935-110">[Set the Options on the General page](#general)</span></span>  
  
-   <span data-ttu-id="0b935-111">[設定 [參數] 索引標籤上的 [選項]](#parameters)</span><span class="sxs-lookup"><span data-stu-id="0b935-111">[Set the Options on the Parameters tab](#parameters)</span></span>  
  
-   <span data-ttu-id="0b935-112">[設定[連接管理員] 索引標籤上的 [選項]](#connection)</span><span class="sxs-lookup"><span data-stu-id="0b935-112">[Set the Options on the Connection Managers tab](#connection)</span></span>  
  
-   <span data-ttu-id="0b935-113">[設定 [進階] 索引標籤上的 [選項]](#advanced)</span><span class="sxs-lookup"><span data-stu-id="0b935-113">[Set the Options on the Advanced tab](#advanced)</span></span>  
  
-   [<span data-ttu-id="0b935-114">編寫執行封裝對話方塊中之選項的指令碼</span><span class="sxs-lookup"><span data-stu-id="0b935-114">Scripting the Options in the Execute Package Dialog Box</span></span>](#script)  
  
##  <a name="open-the-execute-package-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="0b935-115">開啟 [執行封裝] 對話方塊</span><span class="sxs-lookup"><span data-stu-id="0b935-115">Open the Execute Package dialog box</span></span>  
  
1.  <span data-ttu-id="0b935-116">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中，連接至 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 伺服器。</span><span class="sxs-lookup"><span data-stu-id="0b935-116">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="0b935-117">您正在連線到裝載 SSISDB 資料庫的 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="0b935-117">You're connecting to the instance of the [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] that hosts the SSISDB database.</span></span>  
  
2.  <span data-ttu-id="0b935-118">在 [物件總管] 中，展開樹狀目錄以顯示 **[Integration Services 目錄]** 節點。</span><span class="sxs-lookup"><span data-stu-id="0b935-118">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="0b935-119">展開 **[SSISDB]** 節點。</span><span class="sxs-lookup"><span data-stu-id="0b935-119">Expand the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="0b935-120">展開包含您要執行之封裝的資料夾。</span><span class="sxs-lookup"><span data-stu-id="0b935-120">Expand the folder that contains the package you want to run.</span></span>  
  
5.  <span data-ttu-id="0b935-121">以滑鼠右鍵按一下封裝，然後按一下 [執行]  。</span><span class="sxs-lookup"><span data-stu-id="0b935-121">Right-click the package, and then click **Execute**.</span></span>  
  
##  <a name="set-the-options-on-the-general-page"></a><a name="general"></a> <span data-ttu-id="0b935-122">設定 [一般] 頁面上的 [選項]</span><span class="sxs-lookup"><span data-stu-id="0b935-122">Set the Options on the General page</span></span>  
 <span data-ttu-id="0b935-123">選取 **[環境]** 來指定適用於執行執行封裝的環境。</span><span class="sxs-lookup"><span data-stu-id="0b935-123">Select **Environment** to specify the environment that is applied with the package is run.</span></span>  
  
##  <a name="set-the-options-on-the-parameters-tab"></a><a name="parameters"></a> <span data-ttu-id="0b935-124">設定 [參數] 索引標籤上的 [選項]</span><span class="sxs-lookup"><span data-stu-id="0b935-124">Set the Options on the Parameters tab</span></span>  
 <span data-ttu-id="0b935-125">使用 **[參數]** 索引標籤來修改封裝執行時所使用的參數值。</span><span class="sxs-lookup"><span data-stu-id="0b935-125">Use the **Parameters** tab to modify the parameter values that are used when the package runs.</span></span>  
  
##  <a name="set-the-options-on-the-connection-managers-tab"></a><a name="connection"></a> <span data-ttu-id="0b935-126">設定[連接管理員] 索引標籤上的 [選項]</span><span class="sxs-lookup"><span data-stu-id="0b935-126">Set the Options on the Connection Managers tab</span></span>  
 <span data-ttu-id="0b935-127">使用 [連接管理員] 索引標籤設定封裝連接管理員的屬性。</span><span class="sxs-lookup"><span data-stu-id="0b935-127">Use the Connection Managers tab to set the properties of the package connection manager(s).</span></span>  
  
##  <a name="set-the-options-on-the-advanced-tab"></a><a name="advanced"></a> <span data-ttu-id="0b935-128">設定 [進階] 索引標籤上的 [選項]</span><span class="sxs-lookup"><span data-stu-id="0b935-128">Set the Options on the Advanced tab</span></span>  
 <span data-ttu-id="0b935-129">使用 [進階] 索引標籤管理屬性和其他封裝設定。</span><span class="sxs-lookup"><span data-stu-id="0b935-129">Use the Advanced tab to manage properties and other package settings.</span></span>  
  
 <span data-ttu-id="0b935-130">[加入]  、[編輯]  、[移除]</span><span class="sxs-lookup"><span data-stu-id="0b935-130">**Add**, **Edit**, **Remove**</span></span>  
 <span data-ttu-id="0b935-131">按一下可加入、編輯或移除屬性。</span><span class="sxs-lookup"><span data-stu-id="0b935-131">Click to add, edit, or remove a property.</span></span>  
  
 <span data-ttu-id="0b935-132">**記錄層級**</span><span class="sxs-lookup"><span data-stu-id="0b935-132">**Logging level**</span></span>  
 <span data-ttu-id="0b935-133">選取用於執行封裝的記錄層級。</span><span class="sxs-lookup"><span data-stu-id="0b935-133">Select the logging level for the package execution.</span></span> <span data-ttu-id="0b935-134">如需詳細資訊，請參閱 [catalog.set_execution_parameter_value &#40;SSISDB 資料庫&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database)。</span><span class="sxs-lookup"><span data-stu-id="0b935-134">For more information, see [catalog.set_execution_parameter_value &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database).</span></span>  
  
 <span data-ttu-id="0b935-135">**在發生錯誤時傾印**</span><span class="sxs-lookup"><span data-stu-id="0b935-135">**Dump on errors**</span></span>  
 <span data-ttu-id="0b935-136">指定在封裝執行期間發生錯誤時是否建立傾印檔。</span><span class="sxs-lookup"><span data-stu-id="0b935-136">Specify whether a dump file is created when errors occur during the package execution.</span></span> <span data-ttu-id="0b935-137">如需相關資訊，請參閱 [產生封裝執行的傾印檔案](troubleshooting/generating-dump-files-for-package-execution.md)。</span><span class="sxs-lookup"><span data-stu-id="0b935-137">For more information, see [Generating Dump Files for Package Execution](troubleshooting/generating-dump-files-for-package-execution.md).</span></span>  
  
 <span data-ttu-id="0b935-138">**32 位元執行階段**</span><span class="sxs-lookup"><span data-stu-id="0b935-138">**32-bit runtime**</span></span>  
 <span data-ttu-id="0b935-139">指定封裝將會在 32 位元系統上執行。</span><span class="sxs-lookup"><span data-stu-id="0b935-139">Specify that the package will execute on a 32-bit system.</span></span>  
  
##  <a name="scripting-the-options-in-the-execute-package-dialog-box"></a><a name="script"></a> <span data-ttu-id="0b935-140">編寫執行封裝對話方塊中之選項的指令碼</span><span class="sxs-lookup"><span data-stu-id="0b935-140">Scripting the Options in the Execute Package Dialog Box</span></span>  
 <span data-ttu-id="0b935-141">當您位於 **[執行封裝]** 對話方塊時，也可以使用工具列上的 **[指令碼]** 按鈕來為您撰寫 [!INCLUDE[tsql](../includes/tsql-md.md)] 程式碼。</span><span class="sxs-lookup"><span data-stu-id="0b935-141">While you are in the **Execute Package** dialog box, you can also use the **Script** button on the toolbar to write [!INCLUDE[tsql](../includes/tsql-md.md)] code for you.</span></span> <span data-ttu-id="0b935-142">產生的指令碼會使用您在 [執行封裝]  對話方塊中已選取的相同選項來呼叫預存程序 [catalog.start_execution &#40;SSISDB 資料庫&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database)。</span><span class="sxs-lookup"><span data-stu-id="0b935-142">The generated script calls the stored procedures [catalog.start_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database) with the same options that you have selected in the **Execute Package** dialog box.</span></span> <span data-ttu-id="0b935-143">指令碼會出現在 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]的新指令碼視窗中。</span><span class="sxs-lookup"><span data-stu-id="0b935-143">The script appears in a new script window in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span>  
  
  
