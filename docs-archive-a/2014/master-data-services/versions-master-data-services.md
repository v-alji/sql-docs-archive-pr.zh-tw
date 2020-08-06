---
title: 版本 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- version flags [Master Data Services], about version flags
- versions [Master Data Services]
- version flags [Master Data Services]
- versions [Master Data Services], version flags
ms.assetid: 752ec96d-53d7-4160-8ed2-92e0324645f3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 6f8b55a32cdf2a5aabad38ee3d0d4154c2ad6a6f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585496"
---
# <a name="versions-master-data-services"></a><span data-ttu-id="bb189-102">版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="bb189-102">Versions (Master Data Services)</span></span>
  <span data-ttu-id="bb189-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，您可以在模型內建立多個版本的主要資料。</span><span class="sxs-lookup"><span data-stu-id="bb189-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can create multiple versions of the master data within a model.</span></span> <span data-ttu-id="bb189-104">系統會在您驗證資料時鎖定版本，並在驗證資料之後認可版本。</span><span class="sxs-lookup"><span data-stu-id="bb189-104">Versions can be locked while you validate your data and committed after the data is validated.</span></span> <span data-ttu-id="bb189-105">認可的版本會形成可稽核的變更記錄。</span><span class="sxs-lookup"><span data-stu-id="bb189-105">Committed versions form an auditable record of changes.</span></span> <span data-ttu-id="bb189-106">您建立的每個版本都包含該模型的所有成員、屬性值、階層成員、階層關聯性和集合。</span><span class="sxs-lookup"><span data-stu-id="bb189-106">Each version you create contains all members, attribute values, hierarchy members, hierarchy relationships, and collections for the model.</span></span>  
  
## <a name="when-to-use-versions"></a><span data-ttu-id="bb189-107">使用版本的時機</span><span class="sxs-lookup"><span data-stu-id="bb189-107">When to Use Versions</span></span>  
 <span data-ttu-id="bb189-108">使用版本可進行以下作業：</span><span class="sxs-lookup"><span data-stu-id="bb189-108">Use versions to:</span></span>  
  
-   <span data-ttu-id="bb189-109">當主要資料隨著時間而變化時，維護主資料的可稽核記錄。</span><span class="sxs-lookup"><span data-stu-id="bb189-109">Maintain an auditable record of your master data as it changes over time.</span></span>  
  
-   <span data-ttu-id="bb189-110">防止使用者進行變更，同時確保可根據商務規則來成功驗證所有資料。</span><span class="sxs-lookup"><span data-stu-id="bb189-110">Prevent users from making changes while you ensure all data validates successfully against business rules.</span></span>  
  
-   <span data-ttu-id="bb189-111">鎖定模型以供訂閱系統使用。</span><span class="sxs-lookup"><span data-stu-id="bb189-111">Lock down a model for use by subscribing systems.</span></span>  
  
-   <span data-ttu-id="bb189-112">測試不同的階層，而不立即實作。</span><span class="sxs-lookup"><span data-stu-id="bb189-112">Test different hierarchies without implementing them right away.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bb189-113">當您變更模型的結構時 (例如建立新的實體或網域屬性時)，此變更會套用至所有版本。</span><span class="sxs-lookup"><span data-stu-id="bb189-113">When you change the structure of your model, such as when you create a new entity or domain-based attribute, the change applies to all versions.</span></span> <span data-ttu-id="bb189-114">如果您檢視舊版的模型，將會顯示該實體或屬性，但不會有任何資料存在。</span><span class="sxs-lookup"><span data-stu-id="bb189-114">If you view an earlier version of the model, the entity or attribute is displayed, but no data exists.</span></span>  
  
## <a name="version-flags"></a><span data-ttu-id="bb189-115">版本旗標</span><span class="sxs-lookup"><span data-stu-id="bb189-115">Version Flags</span></span>  
 <span data-ttu-id="bb189-116">當某個版本可供使用者或訂閱系統使用時，您可以設定旗標來識別該版本。</span><span class="sxs-lookup"><span data-stu-id="bb189-116">When a version is ready for users or for a subscribing system, you can set a flag to identify the version.</span></span> <span data-ttu-id="bb189-117">您可以視需要在不同的版本之間移動這個旗標。</span><span class="sxs-lookup"><span data-stu-id="bb189-117">You can move this flag from version to version as needed.</span></span> <span data-ttu-id="bb189-118">旗標可幫助使用者和訂閱系統來識別所要使用之模型的版本。</span><span class="sxs-lookup"><span data-stu-id="bb189-118">Flags help users and subscribing systems identify which version of a model to use.</span></span>  
  
## <a name="workflow-for-version-management"></a><span data-ttu-id="bb189-119">版本管理的工作流程</span><span class="sxs-lookup"><span data-stu-id="bb189-119">Workflow for Version Management</span></span>  
 <span data-ttu-id="bb189-120">請使用下列版本管理的工作流程：</span><span class="sxs-lookup"><span data-stu-id="bb189-120">Use the following workflow for version management:</span></span>  
  
1.  <span data-ttu-id="bb189-121">當您建立模型，並使用公司的主要資料填入 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫時，便會自動建立初始版本。</span><span class="sxs-lookup"><span data-stu-id="bb189-121">An initial version is created automatically when you create a model and populate the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database with your company's master data.</span></span> <span data-ttu-id="bb189-122">根據權限，使用者可以視需要來變更這個版本。</span><span class="sxs-lookup"><span data-stu-id="bb189-122">Based on permissions, users can make changes to this version as needed.</span></span>  
  
2.  <span data-ttu-id="bb189-123">當您想要認可某個模型的版本時，請鎖定該版本，讓模型管理員才可以更新資料。</span><span class="sxs-lookup"><span data-stu-id="bb189-123">When you want to commit a version of a model, lock the version so that only model administrators can update the data.</span></span> <span data-ttu-id="bb189-124">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="bb189-124">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span> <span data-ttu-id="bb189-125">如果設定通知，每次版本狀態變更時，都會傳送電子郵件通知給模型管理員。</span><span class="sxs-lookup"><span data-stu-id="bb189-125">If notifications are configured, an email notification is sent to model administrators each time the version's status changes.</span></span> <span data-ttu-id="bb189-126">如需詳細資訊，請參閱[設定電子郵件通知 &#40;Master Data Services&#41;](../../2014/master-data-services/configure-email-notifications-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="bb189-126">For more information, see [Configure Email Notifications &#40;Master Data Services&#41;](../../2014/master-data-services/configure-email-notifications-master-data-services.md).</span></span>  
  
3.  <span data-ttu-id="bb189-127">將商務規則套用至鎖定版本的資料，並檢閱任何驗證問題。</span><span class="sxs-lookup"><span data-stu-id="bb189-127">Apply business rules to the locked version's data and review any validation issues.</span></span> <span data-ttu-id="bb189-128">必要時，您可以填入遺失的資訊，或還原造成問題的交易。</span><span class="sxs-lookup"><span data-stu-id="bb189-128">If necessary, you can fill in missing information or revert the transaction that caused the issue.</span></span> <span data-ttu-id="bb189-129">您也可以解除鎖定版本，以供使用者進行變更。</span><span class="sxs-lookup"><span data-stu-id="bb189-129">You can also unlock the version for users to make changes.</span></span>  
  
4.  <span data-ttu-id="bb189-130">當所有資料都通過驗證時，請認可版本並為它設定旗標，以供訂閱系統使用。</span><span class="sxs-lookup"><span data-stu-id="bb189-130">When all the data passes validation, commit the version and flag it for use by subscribing systems.</span></span> <span data-ttu-id="bb189-131">已認可的版本將無法變更。</span><span class="sxs-lookup"><span data-stu-id="bb189-131">Changes cannot be made to a committed version.</span></span>  
  
5.  <span data-ttu-id="bb189-132">複製已認可的版本，並通知使用者他們可以開始使用新版本的模型。</span><span class="sxs-lookup"><span data-stu-id="bb189-132">Copy the committed version and notify users that they can begin working in a new version of the model.</span></span>  
  
## <a name="sequential-or-simultaneous-versions"></a><span data-ttu-id="bb189-133">循序版本或同時版本</span><span class="sxs-lookup"><span data-stu-id="bb189-133">Sequential or Simultaneous Versions</span></span>  
 <span data-ttu-id="bb189-134">您可以建立模型的循序版本或同時版本。</span><span class="sxs-lookup"><span data-stu-id="bb189-134">You can create sequential or simultaneous versions of your model.</span></span>  
  
-   <span data-ttu-id="bb189-135">**循序版本。**</span><span class="sxs-lookup"><span data-stu-id="bb189-135">**Sequential versions.**</span></span> <span data-ttu-id="bb189-136">每當您認可版本時，都可以建立新的複本，並為此版本提供下一個循序號碼。</span><span class="sxs-lookup"><span data-stu-id="bb189-136">Each time you commit a version, create a new copy and give the version the next sequential number.</span></span> <span data-ttu-id="bb189-137">例如，您可以複製模型的 **版本 7** ，並將此複本命名為 **版本 8**。</span><span class="sxs-lookup"><span data-stu-id="bb189-137">For example, you can copy **Version 7** of your model and name the copy **Version 8**.</span></span>  
  
-   <span data-ttu-id="bb189-138">**同時版本。**</span><span class="sxs-lookup"><span data-stu-id="bb189-138">**Simultaneous versions.**</span></span> <span data-ttu-id="bb189-139">當您想要一次處理兩個或多個版本的資料時，可以建立模型的同時版本。</span><span class="sxs-lookup"><span data-stu-id="bb189-139">Create simultaneous versions of your model when you want to work on two or more versions of your data at once.</span></span> <span data-ttu-id="bb189-140">當公司的重組或併購與正常的商業流程衝突，而且您想要判斷新的主資料是否適合現有的結構時，這個處理方式將會很實用。</span><span class="sxs-lookup"><span data-stu-id="bb189-140">This is useful when your company has reorganizations or mergers that coincide with the normal course of business and you want to determine how the new master data might fit into your existing structures.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="bb189-141">[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 中的設定會決定您是否可以複製所有版本，還是只能複製已認可的版本。</span><span class="sxs-lookup"><span data-stu-id="bb189-141">A setting in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] determines whether or not you can copy all versions or only those that are committed.</span></span> <span data-ttu-id="bb189-142">若要建立同時版本，您必須設定 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 允許您複製所有版本。</span><span class="sxs-lookup"><span data-stu-id="bb189-142">To create simultaneous versions you must configure [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] to allow you to copy all versions.</span></span> <span data-ttu-id="bb189-143">此設定也可以在 [系統設定] 表格中使用。</span><span class="sxs-lookup"><span data-stu-id="bb189-143">This setting is also available in the System Settings table.</span></span> <span data-ttu-id="bb189-144">如需詳細資訊，請參閱 [系統設定 &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="bb189-144">For more information, see [System Settings &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="bb189-145">相關工作</span><span class="sxs-lookup"><span data-stu-id="bb189-145">Related Tasks</span></span>  
  
|<span data-ttu-id="bb189-146">工作描述</span><span class="sxs-lookup"><span data-stu-id="bb189-146">Task Description</span></span>|<span data-ttu-id="bb189-147">主題</span><span class="sxs-lookup"><span data-stu-id="bb189-147">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="bb189-148">變更現有版本的名稱。</span><span class="sxs-lookup"><span data-stu-id="bb189-148">Change the name of an existing version.</span></span>|[<span data-ttu-id="bb189-149">變更版本名稱 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="bb189-149">Change a Version Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-a-version-name-master-data-services.md)|  
|<span data-ttu-id="bb189-150">鎖定版本，僅讓管理員可以編輯其資料。</span><span class="sxs-lookup"><span data-stu-id="bb189-150">Lock a version so only administrators can edit its data.</span></span>|[<span data-ttu-id="bb189-151">鎖定版本 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="bb189-151">Lock a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/lock-a-version-master-data-services.md)|  
|<span data-ttu-id="bb189-152">解除鎖定版本，讓使用者可以編輯其資料。</span><span class="sxs-lookup"><span data-stu-id="bb189-152">Unlock a version so users can edit its data.</span></span>|[<span data-ttu-id="bb189-153">解除鎖定版本 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="bb189-153">Unlock a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/unlock-a-version-master-data-services.md)|  
|<span data-ttu-id="bb189-154">在驗證所有資料之後認可版本。</span><span class="sxs-lookup"><span data-stu-id="bb189-154">Commit a version after all data is validated.</span></span>|[<span data-ttu-id="bb189-155">認可版本 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="bb189-155">Commit a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/commit-a-version-master-data-services.md)|  
|<span data-ttu-id="bb189-156">建立新旗標來標示版本。</span><span class="sxs-lookup"><span data-stu-id="bb189-156">Create a new flag to mark a version.</span></span>|[<span data-ttu-id="bb189-157">建立版本旗標 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="bb189-157">Create a Version Flag &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-version-flag-master-data-services.md)|  
|<span data-ttu-id="bb189-158">變更現有版本旗標的名稱。</span><span class="sxs-lookup"><span data-stu-id="bb189-158">Change the name of an existing version flag.</span></span>|[<span data-ttu-id="bb189-159">變更版本旗標名稱 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="bb189-159">Change a Version Flag Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-a-version-flag-name-master-data-services.md)|  
|<span data-ttu-id="bb189-160">將現有旗標指派給版本。</span><span class="sxs-lookup"><span data-stu-id="bb189-160">Assign an existing flag to a version.</span></span>|[<span data-ttu-id="bb189-161">將旗標指派給版本 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="bb189-161">Assign a Flag to a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/assign-a-flag-to-a-version-master-data-services.md)|  
|<span data-ttu-id="bb189-162">建立現有版本的新副本</span><span class="sxs-lookup"><span data-stu-id="bb189-162">Create a new copy of an existing version</span></span>|[<span data-ttu-id="bb189-163">複製版本 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="bb189-163">Copy a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/copy-a-version-master-data-services.md)|  
|<span data-ttu-id="bb189-164">刪除現有版本。</span><span class="sxs-lookup"><span data-stu-id="bb189-164">Delete an existing version.</span></span>|[<span data-ttu-id="bb189-165">刪除版本 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="bb189-165">Delete a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-version-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="bb189-166">相關內容</span><span class="sxs-lookup"><span data-stu-id="bb189-166">Related Content</span></span>  
  
-   [<span data-ttu-id="bb189-167">反轉交易 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="bb189-167">Reverse a Transaction &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/reverse-a-transaction-master-data-services.md)  
  
-   [<span data-ttu-id="bb189-168">通知 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="bb189-168">Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/notifications-master-data-services.md)  
  
-   [<span data-ttu-id="bb189-169">商務規則 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="bb189-169">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
