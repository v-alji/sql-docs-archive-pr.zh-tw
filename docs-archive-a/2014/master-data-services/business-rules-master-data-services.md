---
title: 商務規則 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], about business rules
- business rules [Master Data Services]
ms.assetid: a9f9e41a-2461-4845-b947-58b3a205543f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 00ac4b7d8970978ef111d56e5a809ada36362583
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606968"
---
# <a name="business-rules-master-data-services"></a><span data-ttu-id="7e072-102">商務規則 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="7e072-102">Business Rules (Master Data Services)</span></span>
  <span data-ttu-id="7e072-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，商務規則是用來確保主要資料品質和正確性的規則。</span><span class="sxs-lookup"><span data-stu-id="7e072-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], a business rule is a rule that you use to ensure the quality and accuracy of your master data.</span></span> <span data-ttu-id="7e072-104">您可以使用商務規則自動更新資料、傳送電子郵件，或啟動商務程序或工作流程。</span><span class="sxs-lookup"><span data-stu-id="7e072-104">You can use a business rule to automatically update data, to send email, or to start a business process or workflow.</span></span>  
  
## <a name="create-and-publish-business-rules"></a><span data-ttu-id="7e072-105">建立及發行商務規則</span><span class="sxs-lookup"><span data-stu-id="7e072-105">Create and Publish Business Rules</span></span>  
 <span data-ttu-id="7e072-106">商務規則是您在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 中建立的 `If/Then` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="7e072-106">Business rules are `If/Then` statements that you create in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span> <span data-ttu-id="7e072-107">如果屬性值符合指定的條件，便會執行動作。</span><span class="sxs-lookup"><span data-stu-id="7e072-107">If an attribute value meets a specified condition, then an action is taken.</span></span> <span data-ttu-id="7e072-108">可能的動作包含設定預設值或變更值。</span><span class="sxs-lookup"><span data-stu-id="7e072-108">Possible actions include setting a default value or changing a value.</span></span> <span data-ttu-id="7e072-109">這些動作可以結合傳送電子郵件通知。</span><span class="sxs-lookup"><span data-stu-id="7e072-109">These actions can be combined with sending an email notification.</span></span>  
  
 <span data-ttu-id="7e072-110">商務規則可以以特定的屬性值 (例如，如果 Color=Blue，則採取動作) 為基礎，或當屬性值變更 (例如，如果 Color 屬性的值變更時，則採取動作)。</span><span class="sxs-lookup"><span data-stu-id="7e072-110">Business rules can be based on specific attribute values (for example, take action if Color=Blue), or when attribute values change (for example, take action if the value of the Color attribute changes).</span></span> <span data-ttu-id="7e072-111">如需追蹤非特定變更的詳細資訊，請參閱[變更追蹤 &#40;Master Data Services&#41;](change-tracking-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="7e072-111">For more information about tracking non-specific changes, see [Change Tracking &#40;Master Data Services&#41;](change-tracking-master-data-services.md).</span></span>  
  
 <span data-ttu-id="7e072-112">若要使用商務規則，您必須先建立並發行規則，然後將已發行的規則套用至資料。</span><span class="sxs-lookup"><span data-stu-id="7e072-112">To use business rules you must first create and publish your rules, then apply the published rules to data.</span></span> <span data-ttu-id="7e072-113">您可以透過驗證版本，將規則套用至某個版本的資料子集或所有資料。</span><span class="sxs-lookup"><span data-stu-id="7e072-113">You can apply rules to subsets of data or to all data for a version by validating the version.</span></span> <span data-ttu-id="7e072-114">直到所有屬性都通過商務規則驗證之後，才能認可版本。</span><span class="sxs-lookup"><span data-stu-id="7e072-114">A version cannot be committed until all attributes pass business rule validation.</span></span>  
  
 <span data-ttu-id="7e072-115">如果使用者所要新增的屬性值未通過商務規則驗證，此值仍然可以儲存。</span><span class="sxs-lookup"><span data-stu-id="7e072-115">If a user attempts to add an attribute value that doesn't pass business rule validation, the value can still be saved.</span></span> <span data-ttu-id="7e072-116">您可以檢閱及更正 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中顯示的驗證問題。</span><span class="sxs-lookup"><span data-stu-id="7e072-116">You can review and correct validation issues, which are displayed in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
 <span data-ttu-id="7e072-117">當您建立模型部署封裝時，若要包含商務規則，必須從封裝中的版本包含資料。</span><span class="sxs-lookup"><span data-stu-id="7e072-117">When you create a model deployment package, if you want to include business rules you must include data from the version in the package.</span></span>  
  
 <span data-ttu-id="7e072-118">如果您建立使用 **OR** 運算子的商務規則，您應該為每個可獨立評估的條件陳述式建立不同的規則。</span><span class="sxs-lookup"><span data-stu-id="7e072-118">If you create a business rule that uses the **OR** operator, you should create a separate rule for each conditional statement that can be evaluated independently.</span></span> <span data-ttu-id="7e072-119">然後您可以視需要排除規則，提供更多彈性和輕鬆疑難排解。</span><span class="sxs-lookup"><span data-stu-id="7e072-119">You can then exclude rules as needed, providing more flexibility and easier troubleshooting.</span></span>  
  
## <a name="how-business-rules-are-applied"></a><span data-ttu-id="7e072-120">如何套用商務規則</span><span class="sxs-lookup"><span data-stu-id="7e072-120">How Business Rules Are Applied</span></span>  
 <span data-ttu-id="7e072-121">您可以設定執行規則的優先順序。</span><span class="sxs-lookup"><span data-stu-id="7e072-121">You can set priority order for rules to run in.</span></span> <span data-ttu-id="7e072-122">但是在考量優先順序之前，將會根據商務規則所採取的動作類型套用該規則。</span><span class="sxs-lookup"><span data-stu-id="7e072-122">However, before priority is taken into account, business rules are applied based on the type of action the rule takes.</span></span> <span data-ttu-id="7e072-123">順序如下：</span><span class="sxs-lookup"><span data-stu-id="7e072-123">The order is as follows:</span></span>  
  
1.  <span data-ttu-id="7e072-124">**預設值**</span><span class="sxs-lookup"><span data-stu-id="7e072-124">**Default Value**</span></span>  
  
2.  <span data-ttu-id="7e072-125">**變更值**</span><span class="sxs-lookup"><span data-stu-id="7e072-125">**Change Value**</span></span>  
  
3.  <span data-ttu-id="7e072-126">**驗證**</span><span class="sxs-lookup"><span data-stu-id="7e072-126">**Validation**</span></span>  
  
4.  <span data-ttu-id="7e072-127">**外部動作**</span><span class="sxs-lookup"><span data-stu-id="7e072-127">**External Action**</span></span>  
  
 <span data-ttu-id="7e072-128">在這些群組中，將會依照從最低到最高的優先順序來套用動作。</span><span class="sxs-lookup"><span data-stu-id="7e072-128">Within these groups, actions are applied in priority order, from lowest to highest.</span></span> <span data-ttu-id="7e072-129">例如，四個不同的規則可能有 **[預設值]** 動作。</span><span class="sxs-lookup"><span data-stu-id="7e072-129">So for example, four separate rules might have **Default Value** actions.</span></span> <span data-ttu-id="7e072-130">發生的 **[預設值]** 動作首先取決於 Web UI 中所指定的優先順序。</span><span class="sxs-lookup"><span data-stu-id="7e072-130">The **Default Value** action that occurs first depends on the priority order specified in the web UI.</span></span>  
  
 <span data-ttu-id="7e072-131">其他有關套用規則的重要注意事項：</span><span class="sxs-lookup"><span data-stu-id="7e072-131">Other important notes about applying rules:</span></span>  
  
-   <span data-ttu-id="7e072-132">如果商務規則被排除在外或不是以 **作用中**狀態發行，此規則仍然可以使用但在套用商務規則時未包含在內。</span><span class="sxs-lookup"><span data-stu-id="7e072-132">If a business rule is excluded or is not published with a status of **Active**, the rule is still available but is not included when business rules are applied.</span></span>  
  
-   <span data-ttu-id="7e072-133">商務規則套用至所有分葉或所有合併成員的屬性值，但非兩者同時套用。</span><span class="sxs-lookup"><span data-stu-id="7e072-133">Business rules apply to the attribute values for all leaf or all consolidated members, not both.</span></span>  
  
-   <span data-ttu-id="7e072-134">商務規則可以套用至 **[開啟]** 或 **[已鎖定]** 之任何版本的模型。</span><span class="sxs-lookup"><span data-stu-id="7e072-134">Business rules can be applied to any version of a model that is **Open** or **Locked**.</span></span>  
  
-   <span data-ttu-id="7e072-135">套用商務規則時對資料所做的變更不會記錄為交易。</span><span class="sxs-lookup"><span data-stu-id="7e072-135">Changes made to data when business rules are applied are not logged as transactions.</span></span>  
  
-   <span data-ttu-id="7e072-136">商務規則不得包含一個以上的 **[啟動工作流程]** 動作。</span><span class="sxs-lookup"><span data-stu-id="7e072-136">A business rule cannot contain more than one **start workflow** action.</span></span>  
  
## <a name="system-settings"></a><span data-ttu-id="7e072-137">系統設定</span><span class="sxs-lookup"><span data-stu-id="7e072-137">System Settings</span></span>  
 <span data-ttu-id="7e072-138">[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 中有兩項設定會影響商務規則。</span><span class="sxs-lookup"><span data-stu-id="7e072-138">There are two settings in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] that affect business rules.</span></span> <span data-ttu-id="7e072-139">您可以在 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 中或直接在 [系統設定] 表格中調整這些設定。</span><span class="sxs-lookup"><span data-stu-id="7e072-139">You can adjust these settings in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] or directly in the System Settings table.</span></span> <span data-ttu-id="7e072-140">如需詳細資訊，請參閱 [系統設定 &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="7e072-140">For more information, see [System Settings &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="7e072-141">相關工作</span><span class="sxs-lookup"><span data-stu-id="7e072-141">Related Tasks</span></span>  
  
|<span data-ttu-id="7e072-142">工作描述</span><span class="sxs-lookup"><span data-stu-id="7e072-142">Task Description</span></span>|<span data-ttu-id="7e072-143">主題</span><span class="sxs-lookup"><span data-stu-id="7e072-143">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="7e072-144">建立及發行新的商務規則。</span><span class="sxs-lookup"><span data-stu-id="7e072-144">Create and publish a new business rule.</span></span>|[<span data-ttu-id="7e072-145">建立及發行商務規則 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="7e072-145">Create and Publish a Business Rule &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md)|  
|<span data-ttu-id="7e072-146">將多個條件加入至商務規則。</span><span class="sxs-lookup"><span data-stu-id="7e072-146">Add multiple conditions to a business rule.</span></span>|[<span data-ttu-id="7e072-147">將多個條件新增至商務規則 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="7e072-147">Add Multiple Conditions to a Business Rule &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/add-multiple-conditions-to-a-business-rule-master-data-services.md)|  
|<span data-ttu-id="7e072-148">建立商務規則來要求屬性包含值。</span><span class="sxs-lookup"><span data-stu-id="7e072-148">Create a business rule to require that attributes have values.</span></span>|[<span data-ttu-id="7e072-149">要求屬性值 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="7e072-149">Require Attribute Values &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/require-attribute-values-master-data-services.md)|  
|<span data-ttu-id="7e072-150">建立商務規則根據屬性值變更來執行動作。</span><span class="sxs-lookup"><span data-stu-id="7e072-150">Create a business rule to take an action based on changes to attribute values.</span></span>|[<span data-ttu-id="7e072-151">根據屬性值變更來起始動作 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="7e072-151">Initiate Actions Based on Attribute Value Changes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)|  
|<span data-ttu-id="7e072-152">變更現有商務規則的名稱。</span><span class="sxs-lookup"><span data-stu-id="7e072-152">Change the name of an existing business rule.</span></span>|[<span data-ttu-id="7e072-153">變更商務規則名稱 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="7e072-153">Change a Business Rule Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md)|  
|<span data-ttu-id="7e072-154">設定 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 在套用商務規則時傳送通知。</span><span class="sxs-lookup"><span data-stu-id="7e072-154">Configure [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] to send notifications when business rules are applied.</span></span>|[<span data-ttu-id="7e072-155">設定商務規則來傳送通知 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="7e072-155">Configure Business Rules to Send Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)|  
|<span data-ttu-id="7e072-156">將商務規則套用至特定成員。</span><span class="sxs-lookup"><span data-stu-id="7e072-156">Apply business rules to specific members.</span></span>|[<span data-ttu-id="7e072-157">根據商務規則驗證特定成員 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="7e072-157">Validate Specific Members against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)|  
|<span data-ttu-id="7e072-158">排除商務規則以便不使用該規則。</span><span class="sxs-lookup"><span data-stu-id="7e072-158">Exclude a business rule so it is not used.</span></span>|[<span data-ttu-id="7e072-159">排除商務規則 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="7e072-159">Exclude a Business Rule &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/exclude-a-business-rule-master-data-services.md)|  
|<span data-ttu-id="7e072-160">刪除現有商務規則。</span><span class="sxs-lookup"><span data-stu-id="7e072-160">Delete an existing business rule.</span></span>|[<span data-ttu-id="7e072-161">刪除商務規則 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="7e072-161">Delete a Business Rule &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-business-rule-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="7e072-162">相關內容</span><span class="sxs-lookup"><span data-stu-id="7e072-162">Related Content</span></span>  
  
-   [<span data-ttu-id="7e072-163">Master Data Services 概觀</span><span class="sxs-lookup"><span data-stu-id="7e072-163">Master Data Services Overview</span></span>](master-data-services-overview-mds.md)  
  
-   [<span data-ttu-id="7e072-164">版本 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="7e072-164">Versions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/versions-master-data-services.md)  
  
-   [<span data-ttu-id="7e072-165">驗證 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="7e072-165">Validation &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validation-master-data-services.md)  
  
-   [<span data-ttu-id="7e072-166">變更追蹤 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="7e072-166">Change Tracking &#40;Master Data Services&#41;</span></span>](change-tracking-master-data-services.md)  
  
  
