---
title: 執行封裝工作編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executepackagetask.parameter.F1
- sql12.dts.designer.executepackagetask.package.f1
- sql12.dts.designer.executepackagetask.general.f1
ms.assetid: c2c96b4f-eb10-4d8b-be34-88edfd0785fb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b9b2e18516e1f5c1b7af56bd1e84ef875557fd49
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596795"
---
# <a name="execute-package-task-editor"></a><span data-ttu-id="415b3-102">執行封裝工作編輯器</span><span class="sxs-lookup"><span data-stu-id="415b3-102">Execute Package Task Editor</span></span>
  <span data-ttu-id="415b3-103">使用「執行封裝工作編輯器」設定「執行封裝」工作。</span><span class="sxs-lookup"><span data-stu-id="415b3-103">Use the Execute Package Task Editor to configure the Execute Package Task.</span></span> <span data-ttu-id="415b3-104">「執行封裝」工作可讓封裝將其他封裝當做工作流程的一部分執行，以延伸 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 的企業功能。</span><span class="sxs-lookup"><span data-stu-id="415b3-104">The Execute Package task extends the enterprise capabilities of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] by letting packages run other packages as part of a workflow.</span></span>  
  
 <span data-ttu-id="415b3-105">**您想要做什麼事？**</span><span class="sxs-lookup"><span data-stu-id="415b3-105">**What do you want to do?**</span></span>  
  
-   <span data-ttu-id="415b3-106">[開啟 [執行封裝工作編輯器]](#open)</span><span class="sxs-lookup"><span data-stu-id="415b3-106">[Open the Execute Package Task Editor](#open)</span></span>  
  
-   <span data-ttu-id="415b3-107">[設定 [一般] 頁面上的 [選項]](#general)</span><span class="sxs-lookup"><span data-stu-id="415b3-107">[Set the Options on the General Page](#general)</span></span>  
  
-   <span data-ttu-id="415b3-108">[設定 [封裝] 頁面上的 [選項]](#package)</span><span class="sxs-lookup"><span data-stu-id="415b3-108">[Set the Options on the Package Page](#package)</span></span>  
  
-   <span data-ttu-id="415b3-109">[設定 [參數繫結] 頁面上的 [選項]](#parameter)</span><span class="sxs-lookup"><span data-stu-id="415b3-109">[Set the Options on the Parameter Bindings Page](#parameter)</span></span>  
  
##  <a name="open-the-execute-package-task-editor"></a><a name="open"></a> <span data-ttu-id="415b3-110">開啟 [執行封裝工作編輯器]</span><span class="sxs-lookup"><span data-stu-id="415b3-110">Open the Execute Package Task Editor</span></span>  
  
1.  <span data-ttu-id="415b3-111">在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 中開啟包含 [執行封裝] 工作的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="415b3-111">Open an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] that contains an Execute Package task.</span></span>  
  
2.  <span data-ttu-id="415b3-112">以滑鼠右鍵按一下 SSIS 設計師中的工作，然後按一下 [編輯]  。</span><span class="sxs-lookup"><span data-stu-id="415b3-112">Right-click the task in the SSIS Designer, and then click **Edit**.</span></span>  
  
##  <a name="set-the-options-on-the-general-page"></a><a name="general"></a> <span data-ttu-id="415b3-113">設定 [一般] 頁面上的 [選項]</span><span class="sxs-lookup"><span data-stu-id="415b3-113">Set the Options on the General Page</span></span>  
 <span data-ttu-id="415b3-114">**名稱**</span><span class="sxs-lookup"><span data-stu-id="415b3-114">**Name**</span></span>  
 <span data-ttu-id="415b3-115">為執行封裝工作提供唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="415b3-115">Provide a unique name for the Execute Package task.</span></span> <span data-ttu-id="415b3-116">這個名稱是作為工作圖示中的標籤使用。</span><span class="sxs-lookup"><span data-stu-id="415b3-116">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="415b3-117">工作名稱在封裝內必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="415b3-117">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="415b3-118">**說明**</span><span class="sxs-lookup"><span data-stu-id="415b3-118">**Description**</span></span>  
 <span data-ttu-id="415b3-119">輸入「執行封裝」工作的描述。</span><span class="sxs-lookup"><span data-stu-id="415b3-119">Type a description of the Execute Package task.</span></span>  
  
##  <a name="set-the-options-on-the-package-page"></a><a name="package"></a> <span data-ttu-id="415b3-120">設定 [封裝] 頁面上的 [選項]</span><span class="sxs-lookup"><span data-stu-id="415b3-120">Set the Options on the Package Page</span></span>  
 <span data-ttu-id="415b3-121">**ReferenceType**</span><span class="sxs-lookup"><span data-stu-id="415b3-121">**ReferenceType**</span></span>  
 <span data-ttu-id="415b3-122">為專案中的子封裝選取 [專案參考]  。</span><span class="sxs-lookup"><span data-stu-id="415b3-122">Select **Project Reference** for child packages that are in the project.</span></span> <span data-ttu-id="415b3-123">為封裝外部的子封裝選取 [外部參考]</span><span class="sxs-lookup"><span data-stu-id="415b3-123">Select **External Reference** for child packages that are located outside the package</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="415b3-124">[ReferenceType]  選項是唯讀的，如果尚未將包含封裝的專案轉換為專案部署模型，則該選項設為 [外部參考]  。</span><span class="sxs-lookup"><span data-stu-id="415b3-124">The **ReferenceType** option is ready-only and set to **External Reference** if the project that contains the package has not been converted to the project deployment model.</span></span> <span data-ttu-id="415b3-125">如需轉換的詳細資訊，請參閱 [將專案部署至 Integration Services 伺服器](../../2014/integration-services/deploy-projects-to-integration-services-server.md)。</span><span class="sxs-lookup"><span data-stu-id="415b3-125">For more information about conversion, see [Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md).</span></span>  
  
 <span data-ttu-id="415b3-126">**密碼**</span><span class="sxs-lookup"><span data-stu-id="415b3-126">**Password**</span></span>  
 <span data-ttu-id="415b3-127">如果子封裝受到密碼保護，請提供子封裝的密碼，或按一下省略符號 ([...]) 按鈕，然後建立子封裝的新密碼。</span><span class="sxs-lookup"><span data-stu-id="415b3-127">If the child package is password protected, provide the password for the child package, or click the ellipsis button (...) and create a new password for the child package.</span></span>  
  
 `ExecuteOutOfProcess`  
 <span data-ttu-id="415b3-128">指定子封裝是在父封裝的處理序中執行，還是在個別的處理序中執行。</span><span class="sxs-lookup"><span data-stu-id="415b3-128">Specify whether the child package runs in the process of the parent package or in a separate process.</span></span> <span data-ttu-id="415b3-129">根據預設，「執行封裝」工作的 ExecuteOutOfProcess 屬性會設定為 `False` ，而且子封裝會在與父封裝相同的進程中執行。</span><span class="sxs-lookup"><span data-stu-id="415b3-129">By default, the ExecuteOutOfProcess property of the Execute Package task is set to `False`, and the child package runs in the same process as the parent package.</span></span> <span data-ttu-id="415b3-130">如果您將此屬性設定為 `true`，子封裝就會在不同的處理序中執行。</span><span class="sxs-lookup"><span data-stu-id="415b3-130">If you set this property to `true`, the child package runs in a separate process.</span></span> <span data-ttu-id="415b3-131">這可能會降低子封裝的啟動速度。</span><span class="sxs-lookup"><span data-stu-id="415b3-131">This may slow down the launching of the child package.</span></span> <span data-ttu-id="415b3-132">另外，如果此屬性設定為 `true`，則無法在僅限工具安裝中偵錯封裝；您必須安裝 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 產品。</span><span class="sxs-lookup"><span data-stu-id="415b3-132">In addition, if set the property to `true`, you cannot debug the package in a tools-only install; you must install the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] product.</span></span> <span data-ttu-id="415b3-133">如需詳細資訊，請參閱[安裝 Integration Services](install-windows/install-integration-services.md)。</span><span class="sxs-lookup"><span data-stu-id="415b3-133">For more information, see [Install Integration Services](install-windows/install-integration-services.md).</span></span>  
  
### <a name="referencetype-dynamic-options"></a><span data-ttu-id="415b3-134">ReferenceType 動態選項</span><span class="sxs-lookup"><span data-stu-id="415b3-134">ReferenceType Dynamic Options</span></span>  
  
#### <a name="referencetype--external-reference"></a><span data-ttu-id="415b3-135">ReferenceType = 外部參考</span><span class="sxs-lookup"><span data-stu-id="415b3-135">ReferenceType = External Reference</span></span>  
 <span data-ttu-id="415b3-136">**位置**</span><span class="sxs-lookup"><span data-stu-id="415b3-136">**Location**</span></span>  
 <span data-ttu-id="415b3-137">選取子封裝的位置。</span><span class="sxs-lookup"><span data-stu-id="415b3-137">Select the location of the child package.</span></span> <span data-ttu-id="415b3-138">這個屬性具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="415b3-138">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="415b3-139">值</span><span class="sxs-lookup"><span data-stu-id="415b3-139">Value</span></span>|<span data-ttu-id="415b3-140">描述</span><span class="sxs-lookup"><span data-stu-id="415b3-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="415b3-141">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="415b3-141">**SQL Server**</span></span>|<span data-ttu-id="415b3-142">設定 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]執行個體的位置。</span><span class="sxs-lookup"><span data-stu-id="415b3-142">Set the location to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>|  
|<span data-ttu-id="415b3-143">**檔案系統**</span><span class="sxs-lookup"><span data-stu-id="415b3-143">**File system**</span></span>|<span data-ttu-id="415b3-144">設定檔案系統的位置。</span><span class="sxs-lookup"><span data-stu-id="415b3-144">Set the location to the file system.</span></span>|  
  
 <span data-ttu-id="415b3-145">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="415b3-145">**Connection**</span></span>  
 <span data-ttu-id="415b3-146">選取子封裝的儲存位置類型。</span><span class="sxs-lookup"><span data-stu-id="415b3-146">Select the type of storage location for the child package.</span></span>  
  
 <span data-ttu-id="415b3-147">**PackageNameReadOnly**</span><span class="sxs-lookup"><span data-stu-id="415b3-147">**PackageNameReadOnly**</span></span>  
 <span data-ttu-id="415b3-148">顯示封裝名稱。</span><span class="sxs-lookup"><span data-stu-id="415b3-148">Displays the package name.</span></span>  
  
#### <a name="referencetype--project-reference"></a><span data-ttu-id="415b3-149">ReferenceType = 專案參考</span><span class="sxs-lookup"><span data-stu-id="415b3-149">ReferenceType = Project Reference</span></span>  
 <span data-ttu-id="415b3-150">**PackageNameFromProjectReference**</span><span class="sxs-lookup"><span data-stu-id="415b3-150">**PackageNameFromProjectReference**</span></span>  
 <span data-ttu-id="415b3-151">選取專案中包含的封裝，做為子封裝。</span><span class="sxs-lookup"><span data-stu-id="415b3-151">Select a package contained in the project, to be the child package.</span></span>  
  
### <a name="location-dynamic-options"></a><span data-ttu-id="415b3-152">位置動態選項</span><span class="sxs-lookup"><span data-stu-id="415b3-152">Location Dynamic Options</span></span>  
  
#### <a name="location--sql-server"></a><span data-ttu-id="415b3-153">位置 = SQL Server</span><span class="sxs-lookup"><span data-stu-id="415b3-153">Location = SQL Server</span></span>  
 <span data-ttu-id="415b3-154">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="415b3-154">**Connection**</span></span>  
 <span data-ttu-id="415b3-155">在清單中選取 OLE DB 連線管理員，或按一下 [\<**New connection...**>] 以建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="415b3-155">Select an OLE DB connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="415b3-156">**相關主題** [OLE DB 連線管理員](connection-manager/ole-db-connection-manager.md)、 [設定 OLE DB 連接管理員](../../2014/integration-services/configure-ole-db-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="415b3-156">**Related Topics:** [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md), [Configure OLE DB Connection Manager](../../2014/integration-services/configure-ole-db-connection-manager.md)</span></span>  
  
 <span data-ttu-id="415b3-157">**PackageName**</span><span class="sxs-lookup"><span data-stu-id="415b3-157">**PackageName**</span></span>  
 <span data-ttu-id="415b3-158">輸入子封裝的名稱，或按一下省略符號 ([...])，然後找出該封裝。</span><span class="sxs-lookup"><span data-stu-id="415b3-158">Type the name of the child package, or click the ellipsis (...) and then locate the package.</span></span>  
  
#### <a name="location--file-system"></a><span data-ttu-id="415b3-159">位置 = 檔案系統</span><span class="sxs-lookup"><span data-stu-id="415b3-159">Location = File system</span></span>  
 <span data-ttu-id="415b3-160">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="415b3-160">**Connection**</span></span>  
 <span data-ttu-id="415b3-161">在清單中選取檔案連線管理員，或按一下 [\<**New connection...**>] 以建立新的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="415b3-161">Select a File connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="415b3-162">**相關主題：** [檔案連線管理員](connection-manager/file-connection-manager.md)、[檔案連線管理員編輯器](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="415b3-162">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="415b3-163">**PackageNameReadOnly**</span><span class="sxs-lookup"><span data-stu-id="415b3-163">**PackageNameReadOnly**</span></span>  
 <span data-ttu-id="415b3-164">顯示封裝名稱。</span><span class="sxs-lookup"><span data-stu-id="415b3-164">Displays the package name.</span></span>  
  
##  <a name="set-the-options-on-the-parameter-bindings-page"></a><a name="parameter"></a> <span data-ttu-id="415b3-165">設定 [參數繫結] 頁面上的 [選項]</span><span class="sxs-lookup"><span data-stu-id="415b3-165">Set the Options on the Parameter Bindings Page</span></span>  
 <span data-ttu-id="415b3-166">您可以將值從父封裝或專案傳遞至子封裝。</span><span class="sxs-lookup"><span data-stu-id="415b3-166">You can pass values from the parent package or the project, to the child package.</span></span> <span data-ttu-id="415b3-167">專案必須使用專案部署模型，而且子封裝必須包含在包含父封裝的相同專案中。</span><span class="sxs-lookup"><span data-stu-id="415b3-167">The project must use the project deployment model and the child package must be contained in the same project that contains the parent package.</span></span>  
  
 <span data-ttu-id="415b3-168">如需將專案轉換為專案部署模型的資訊，請參閱 [將專案部署至 Integration Services 伺服器](../../2014/integration-services/deploy-projects-to-integration-services-server.md)。</span><span class="sxs-lookup"><span data-stu-id="415b3-168">For information about converting projects to the project deployment model, see [Deploy Projects to Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md).</span></span>  
  
 <span data-ttu-id="415b3-169">**子封裝參數**</span><span class="sxs-lookup"><span data-stu-id="415b3-169">**Child package parameter**</span></span>  
 <span data-ttu-id="415b3-170">輸入或選取子封裝參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="415b3-170">Enter or select a name for the child package parameter.</span></span>  
  
 <span data-ttu-id="415b3-171">**繫結參數或變數**</span><span class="sxs-lookup"><span data-stu-id="415b3-171">**Binding parameter or variable**</span></span>  
 <span data-ttu-id="415b3-172">選取包含您要傳遞到子封裝之值的參數或變數。</span><span class="sxs-lookup"><span data-stu-id="415b3-172">Select the parameter or variable that contains the value that you want to pass to the child package.</span></span>  
  
 <span data-ttu-id="415b3-173">**加入**</span><span class="sxs-lookup"><span data-stu-id="415b3-173">**Add**</span></span>  
 <span data-ttu-id="415b3-174">按一下此選項可將參數或變數對應到子封裝參數。</span><span class="sxs-lookup"><span data-stu-id="415b3-174">Click to map a parameter or variable to a child package parameter.</span></span>  
  
 <span data-ttu-id="415b3-175">**移除**</span><span class="sxs-lookup"><span data-stu-id="415b3-175">**Remove**</span></span>  
 <span data-ttu-id="415b3-176">按一下此選項可移除參數或變數與子封裝參數之間的對應。</span><span class="sxs-lookup"><span data-stu-id="415b3-176">Click to remove a mapping between a parameter or variable and a child package parameter.</span></span>  
  
  
