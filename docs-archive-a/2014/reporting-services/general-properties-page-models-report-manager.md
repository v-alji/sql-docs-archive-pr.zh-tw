---
title: 一般屬性頁面、模型 (報表管理員) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.modelproperties.general.f1
ms.assetid: 7ad59850-8135-4c4d-95e9-6d705b6d77a8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0fbd96392716c63fb739c6455bb1eac04912b93f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606093"
---
# <a name="general-properties-page-models-report-manager"></a><span data-ttu-id="79762-102">一般屬性頁面，模型 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="79762-102">General Properties Page, Models (Report Manager)</span></span>
  <span data-ttu-id="79762-103">您可以使用報表模型的 [一般屬性] 頁面來重新命名、刪除、移動或取代模型定義 (.smdl) 檔案。</span><span class="sxs-lookup"><span data-stu-id="79762-103">Use the General properties page for report models to rename, delete, move, or replace the model definition (.smdl) file.</span></span> <span data-ttu-id="79762-104">有關模型建立者與修改者及變更日期的詳細資料都會顯示在頁面頂端。</span><span class="sxs-lookup"><span data-stu-id="79762-104">Details about who created or modified the model and when the changes took place are indicated at the top of the page.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="79762-105">導覽</span><span class="sxs-lookup"><span data-stu-id="79762-105">Navigation</span></span>  
 <span data-ttu-id="79762-106">您可以使用下列程序，在使用者介面 (UI) 中導覽至這個位置。</span><span class="sxs-lookup"><span data-stu-id="79762-106">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-general-properties-page-for-a-model"></a><span data-ttu-id="79762-107">若要開啟模型的一般屬性頁面</span><span class="sxs-lookup"><span data-stu-id="79762-107">To open the General properties page for a model</span></span>  
  
1.  <span data-ttu-id="79762-108">開啟報表管理員，然後找出您想要檢視或設定屬性的模型。</span><span class="sxs-lookup"><span data-stu-id="79762-108">Open Report Manager, and locate the model for which you want to view or configure properties.</span></span>  
  
2.  <span data-ttu-id="79762-109">將滑鼠停留在該模型上，然後按一下下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="79762-109">Hover over the model, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="79762-110">在下拉式功能表中，按一下 **[管理]**。</span><span class="sxs-lookup"><span data-stu-id="79762-110">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="79762-111">這樣就會開啟該模型的 [一般] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="79762-111">This opens the General properties page for the model.</span></span>  
  
## <a name="options"></a><span data-ttu-id="79762-112">選項。</span><span class="sxs-lookup"><span data-stu-id="79762-112">Options</span></span>  
 <span data-ttu-id="79762-113">**名稱**</span><span class="sxs-lookup"><span data-stu-id="79762-113">**Name**</span></span>  
 <span data-ttu-id="79762-114">指定模型的名稱。</span><span class="sxs-lookup"><span data-stu-id="79762-114">Specifies the name of the model.</span></span> <span data-ttu-id="79762-115">名稱必須至少包含一個英數字元。</span><span class="sxs-lookup"><span data-stu-id="79762-115">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="79762-116">它也可以包含空格和某些符號。</span><span class="sxs-lookup"><span data-stu-id="79762-116">It can also include spaces and some symbols.</span></span> <span data-ttu-id="79762-117">指定名稱時，請勿使用下列字元：</span><span class="sxs-lookup"><span data-stu-id="79762-117">Do not use the following characters when specifying a name:</span></span>  
  
 <span data-ttu-id="79762-118">; ?</span><span class="sxs-lookup"><span data-stu-id="79762-118">; ?</span></span> <span data-ttu-id="79762-119">： \@ & = +，$/\* \< > |" /</span><span class="sxs-lookup"><span data-stu-id="79762-119">: \@ & = + , $ / \* \< > | " /</span></span>  
  
 <span data-ttu-id="79762-120">**說明**</span><span class="sxs-lookup"><span data-stu-id="79762-120">**Description**</span></span>  
 <span data-ttu-id="79762-121">輸入模型的描述。</span><span class="sxs-lookup"><span data-stu-id="79762-121">Type a description of the model.</span></span> <span data-ttu-id="79762-122">這項描述會顯示在有權存取此模型之使用者的 [內容] 頁面上。</span><span class="sxs-lookup"><span data-stu-id="79762-122">This description appears in the Contents page to users who have permission to access the modelt.</span></span>  
  
 <span data-ttu-id="79762-123">**在清單檢視中隱藏**</span><span class="sxs-lookup"><span data-stu-id="79762-123">**Hidden in list view**</span></span>  
 <span data-ttu-id="79762-124">選取此核取方塊即可在清單檢視中設定資料夾時，隱藏項目。</span><span class="sxs-lookup"><span data-stu-id="79762-124">Select this check box to hide the item when the folder is set in list view.</span></span> <span data-ttu-id="79762-125">清單檢視是檢視資料夾內容的一種模式，報表管理員中支援這種檢視模式。</span><span class="sxs-lookup"><span data-stu-id="79762-125">List view is a mode for viewing folder contents that is supported in Report Manager.</span></span> <span data-ttu-id="79762-126">您可以在 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 中設定這個選項，以便定義在報表管理員中檢視這個項目的方式。</span><span class="sxs-lookup"><span data-stu-id="79762-126">You can set this option in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] to define how this item is viewed in Report Manager.</span></span> <span data-ttu-id="79762-127">如需報表管理員中視圖模式的詳細資訊，請參閱[內容頁面 &#40;報表管理員&#41;](../../2014/reporting-services/contents-page-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="79762-127">For more information about view modes in Report Manager, see [Contents Page &#40;Report Manager&#41;](../../2014/reporting-services/contents-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="79762-128">**套用**</span><span class="sxs-lookup"><span data-stu-id="79762-128">**Apply**</span></span>  
 <span data-ttu-id="79762-129">按一下即可儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="79762-129">Click to save your changes.</span></span>  
  
 <span data-ttu-id="79762-130">**刪除**</span><span class="sxs-lookup"><span data-stu-id="79762-130">**Delete**</span></span>  
 <span data-ttu-id="79762-131">按一下即可從報表伺服器資料庫中移除模型。</span><span class="sxs-lookup"><span data-stu-id="79762-131">Click to remove the model from the report server database.</span></span> <span data-ttu-id="79762-132">刪除模型並不會刪除提供連接資訊的相依共用資料來源，也不會刪除使用此模型當做資料來源的報表。</span><span class="sxs-lookup"><span data-stu-id="79762-132">Deleting a model does not delete the dependent shared data source that provides connection information, nor does it delete reports that use the model as a data source.</span></span> <span data-ttu-id="79762-133">不過，刪除模型之後，使用該模型的報表將無法再執行。</span><span class="sxs-lookup"><span data-stu-id="79762-133">However, after the model is deleted, reports that use the model will no longer run.</span></span>  
  
 <span data-ttu-id="79762-134">**移動**</span><span class="sxs-lookup"><span data-stu-id="79762-134">**Move**</span></span>  
 <span data-ttu-id="79762-135">按一下即可在報表伺服器資料夾階層內重新定位模型。</span><span class="sxs-lookup"><span data-stu-id="79762-135">Click to relocate a model within the report server folder hierarchy.</span></span> <span data-ttu-id="79762-136">按一下此按鈕會開啟 [移動項目] 頁面，您可在此瀏覽資料夾以選取新位置。</span><span class="sxs-lookup"><span data-stu-id="79762-136">Clicking this button opens the Move Items page, on which you can browse through folders for a new folder location.</span></span> <span data-ttu-id="79762-137">如需詳細資訊，請參閱[&#40;報表管理員&#41;中移動專案頁面](../../2014/reporting-services/move-items-page-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="79762-137">For more information, see [Move Items Page &#40;Report Manager&#41;](../../2014/reporting-services/move-items-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="79762-138">**儲存**</span><span class="sxs-lookup"><span data-stu-id="79762-138">**Save**</span></span>  
 <span data-ttu-id="79762-139">按一下即可儲存模型定義的唯讀副本。</span><span class="sxs-lookup"><span data-stu-id="79762-139">Click to save a read-only copy of the model definition.</span></span> <span data-ttu-id="79762-140">視電腦上定義的檔案關聯而定，系統會在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 或其他應用程式中開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="79762-140">Depending on the file associations defined on your computer, the file will open in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] or a different application.</span></span> <span data-ttu-id="79762-141">在大多數情況下，系統會將模型開啟為 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="79762-141">In most cases, the model opens as an XML file.</span></span>  
  
 <span data-ttu-id="79762-142">您開啟的副本與初始發行至報表伺服器的原始模型定義相同。</span><span class="sxs-lookup"><span data-stu-id="79762-142">The copy that you open is identical to the original model definition that was initially published to the report server.</span></span> <span data-ttu-id="79762-143">發行模型之後在模型上設定的任何屬性 (例如資料來源屬性) 都不會反映在您開啟的檔案中。</span><span class="sxs-lookup"><span data-stu-id="79762-143">Any properties that were set on the model after it was published (such as data source properties) are not reflected in the file that you open.</span></span>  
  
 <span data-ttu-id="79762-144">您可以修改模型定義並在共用資料夾中另存新檔，然後將模型定義上傳到報表伺服器當做新項目。</span><span class="sxs-lookup"><span data-stu-id="79762-144">You can modify the model definition and save it as a new file in a shared folder, and upload the model definition to the report server as a new item.</span></span> <span data-ttu-id="79762-145">在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (或其他應用程式) 中開啟模型定義時，您對模型定義所做的修改並不會直接儲存到報表伺服器中。</span><span class="sxs-lookup"><span data-stu-id="79762-145">Modifications that you make to the model definition while it is open in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (or another application) are not saved directly to the report server.</span></span> <span data-ttu-id="79762-146">您必須上傳檔案，才能將修改的模型發行到報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="79762-146">You must upload the file to publish the modified model to the report server.</span></span>  
  
 <span data-ttu-id="79762-147">請注意，如果您想要在模型設計師中開啟此報表模型，就應該將此模型儲存成 .smdl 檔案，然後在模型設計師中，將此 .smdl 檔案加入至專案。</span><span class="sxs-lookup"><span data-stu-id="79762-147">Note that if you want to open the report model in Model Designer, you should save the model as .smdl file, and then add the .smdl file to a project in Model Designer.</span></span>  
  
 <span data-ttu-id="79762-148">**Replace**</span><span class="sxs-lookup"><span data-stu-id="79762-148">**Replace**</span></span>  
 <span data-ttu-id="79762-149">按一下即可使用位於檔案系統中 .smdl 檔案的不同模型定義，取代此模型定義。</span><span class="sxs-lookup"><span data-stu-id="79762-149">Click to replace the model definition with a different one from an .smdl file located on the file system.</span></span> <span data-ttu-id="79762-150">如果您更新了模型定義，就必須在完成更新之後重設共用資料來源設定。</span><span class="sxs-lookup"><span data-stu-id="79762-150">If you update a model definition, you must reset the shared data source settings after the update is complete.</span></span>  
  
 <span data-ttu-id="79762-151">**重新產生模型**</span><span class="sxs-lookup"><span data-stu-id="79762-151">**Regenerate Model**</span></span>  
 <span data-ttu-id="79762-152">按一下即可重新產生取代目前版本的預設模型。</span><span class="sxs-lookup"><span data-stu-id="79762-152">Click to regenerate a default model that replaces the current version.</span></span> <span data-ttu-id="79762-153">這個選項會在產生模型之後顯示。</span><span class="sxs-lookup"><span data-stu-id="79762-153">This option appears after the model is generated.</span></span> <span data-ttu-id="79762-154">產生的模型是以共用資料來源為基礎。</span><span class="sxs-lookup"><span data-stu-id="79762-154">The generated model is based on the shared data source.</span></span> <span data-ttu-id="79762-155">您無法在它產生之前進行自訂。</span><span class="sxs-lookup"><span data-stu-id="79762-155">It cannot be customized before it is generated.</span></span> <span data-ttu-id="79762-156">不過，當您產生它之後，就可以按一下 **[編輯]** 開啟模型定義、將它儲存至檔案系統，然後在模型設計師中，將它加入至專案。</span><span class="sxs-lookup"><span data-stu-id="79762-156">However, after you generate it, you can click **Edit** to open the model definition, save it to the file system, and then add it to a project in Model Designer.</span></span> <span data-ttu-id="79762-157">當您修改模型之後，可以將它上傳至報表伺服器當做新項目，也可以按一下這個頁面上的 **[更新]** ，使用您在模型設計師中修訂的版本來取代產生的模型。</span><span class="sxs-lookup"><span data-stu-id="79762-157">After you refine the model, you can upload it to the report server as a new item, or click **Update** on this page to replace the generated model with the version you revised in Model Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79762-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79762-158">See Also</span></span>  
 <span data-ttu-id="79762-159">[將報表或模型系結至 &#40;SSRS&#41;的共用資料來源](report-data/bind-a-report-or-model-to-a-shared-data-source-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="79762-159">[Bind a Report or Model to a Shared Data Source &#40;SSRS&#41;](report-data/bind-a-report-or-model-to-a-shared-data-source-ssrs.md) </span></span>  
 [<span data-ttu-id="79762-160">Management Studio F1 說明中的報表伺服器</span><span class="sxs-lookup"><span data-stu-id="79762-160">Report Server in Management Studio F1 Help</span></span>](tools/report-server-in-management-studio-f1-help.md)  
  
  
