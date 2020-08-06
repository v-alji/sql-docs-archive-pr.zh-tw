---
title: SQL Server 2014 中已停止的 Master Data Services 功能 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 3236cce0-cfd9-43f8-8be3-e8c8dff8f162
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 595b8bf9829ee57ff0d3bee1a82e527876ecc4f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607421"
---
# <a name="discontinued-master-data-services-features-in-sql-server-2014"></a><span data-ttu-id="06615-102">SQL Server 2014 中已停止的 Master Data Services 功能</span><span class="sxs-lookup"><span data-stu-id="06615-102">Discontinued Master Data Services Features in SQL Server 2014</span></span>
  <span data-ttu-id="06615-103">本主題描述 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 中不再可用的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]功能。</span><span class="sxs-lookup"><span data-stu-id="06615-103">This topic describes [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] features that are no longer available in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="sssql14-discontinued-features"></a>[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] <span data-ttu-id="06615-104">已停止的功能</span><span class="sxs-lookup"><span data-stu-id="06615-104">Discontinued Features</span></span>  
 <span data-ttu-id="06615-105">這一版沒有已停止的功能。</span><span class="sxs-lookup"><span data-stu-id="06615-105">There are no discontinued features in this release.</span></span>  
  
## <a name="sssql11-discontinued-features"></a>[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="06615-106">已停止的功能</span><span class="sxs-lookup"><span data-stu-id="06615-106">Discontinued Features</span></span>  
  
### <a name="security"></a><span data-ttu-id="06615-107">安全性</span><span class="sxs-lookup"><span data-stu-id="06615-107">Security</span></span>  
 <span data-ttu-id="06615-108">若要讓安全性的指派更為容易，您可以不再將模型物件權限指派給 [衍生階層]、[明確階層] 和 [屬性群組] 物件。</span><span class="sxs-lookup"><span data-stu-id="06615-108">To make assigning security easier, you can no longer assign model object permissions to the Derived Hierarchy, Explicit Hierarchy, and Attribute Group objects.</span></span>  
  
-   <span data-ttu-id="06615-109">衍生階層權限現在是以模型為基礎。</span><span class="sxs-lookup"><span data-stu-id="06615-109">Derived hierarchy permissions are now based on the model.</span></span> <span data-ttu-id="06615-110">例如，如果您想要讓使用者擁有衍生階層的許可權，則必須將**更新**指派給模型物件。</span><span class="sxs-lookup"><span data-stu-id="06615-110">For example, if you want a user to have permission to a derived hierarchy, you must assign **Update** to the model object.</span></span> <span data-ttu-id="06615-111">接著，您可以將**拒絕**存取權指派給您不想讓使用者存取的任何實體。</span><span class="sxs-lookup"><span data-stu-id="06615-111">Then you can assign **Deny** access to any entities you don't want the user to have access to.</span></span>  
  
-   <span data-ttu-id="06615-112">明確階層權限現在是以實體為基礎。</span><span class="sxs-lookup"><span data-stu-id="06615-112">Explicit hierarchy permissions are now based on the entity.</span></span> <span data-ttu-id="06615-113">例如，如果使用者具有帳戶實體的 [**更新**] 許可權，則該實體的所有明確階層都是可更新的。</span><span class="sxs-lookup"><span data-stu-id="06615-113">For example, if the user has **Update** permissions to an Account entity, then all explicit hierarchies for the entity will be updateable.</span></span>  
  
-   <span data-ttu-id="06615-114">在 [**使用者和群組的許可權**] 功能區域中，無法再指派屬性群組許可權。</span><span class="sxs-lookup"><span data-stu-id="06615-114">Attribute group permissions can no longer be assigned in the **User and Group Permissions** functional area.</span></span> <span data-ttu-id="06615-115">相反地，在建立屬性群組的 [**系統管理**] 功能區域中，使用者和群組可以獲得屬性群組的 [**更新**] 許可權。</span><span class="sxs-lookup"><span data-stu-id="06615-115">Instead, in the **System Administration** functional area where attribute groups are created, users and groups can be given **Update** permission to attribute groups.</span></span> <span data-ttu-id="06615-116">屬性群組的**唯讀**許可權已無法再使用。</span><span class="sxs-lookup"><span data-stu-id="06615-116">**Read-only** permission to attribute groups is no longer available.</span></span>  
  
### <a name="staging-process"></a><span data-ttu-id="06615-117">暫存處理序</span><span class="sxs-lookup"><span data-stu-id="06615-117">Staging Process</span></span>  
 <span data-ttu-id="06615-118">您不能使用新的暫存處理序來：</span><span class="sxs-lookup"><span data-stu-id="06615-118">You cannot use the new staging process to:</span></span>  
  
-   <span data-ttu-id="06615-119">建立或刪除集合。</span><span class="sxs-lookup"><span data-stu-id="06615-119">Create or delete collections.</span></span>  
  
-   <span data-ttu-id="06615-120">在集合中加入或移除成員。</span><span class="sxs-lookup"><span data-stu-id="06615-120">Add members to or remove members from collections.</span></span>  
  
-   <span data-ttu-id="06615-121">重新啟用成員和集合。</span><span class="sxs-lookup"><span data-stu-id="06615-121">Reactivate members and collections.</span></span>  
  
 <span data-ttu-id="06615-122">您可以使用 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 暫存處理序來搭配集合一起運作。</span><span class="sxs-lookup"><span data-stu-id="06615-122">You can use the [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] staging process to work with collections.</span></span>  
  
### <a name="model-deployment-wizard"></a><span data-ttu-id="06615-123">模型部署精靈</span><span class="sxs-lookup"><span data-stu-id="06615-123">Model Deployment Wizard</span></span>  
 <span data-ttu-id="06615-124">包含資料的封裝無法再使用 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 應用程式中的精靈加以建立及部署。</span><span class="sxs-lookup"><span data-stu-id="06615-124">Packages that contain data can no longer be created and deployed by using the wizard in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application.</span></span> <span data-ttu-id="06615-125">但可以改用新的命令列公用程式。</span><span class="sxs-lookup"><span data-stu-id="06615-125">A new command line utility can be used instead.</span></span> <span data-ttu-id="06615-126">如需詳細資訊，請參閱[部署模型 &#40;Master Data Services&#41;](deploying-models-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="06615-126">For more information, see [Deploying Models &#40;Master Data Services&#41;](deploying-models-master-data-services.md).</span></span>  
  
 <span data-ttu-id="06615-127">此精靈依然可用來建立及部署不含資料的封裝。</span><span class="sxs-lookup"><span data-stu-id="06615-127">The wizard can still be used to create and deploy packages that do not contain data.</span></span>  
  
 <span data-ttu-id="06615-128">此外，封裝只能部署到之前建立封裝所使用的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="06615-128">In addition, packages can be deployed to the edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] they were created in only.</span></span> <span data-ttu-id="06615-129">這表示，在 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 中建立的封裝無法部署到 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="06615-129">This means that packages created in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] cannot be deployed to [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span></span> <span data-ttu-id="06615-130">您必須將封裝部署到 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 環境，然後將資料庫升級到 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="06615-130">You must deploy the package to a [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] environment and then upgrade the database to [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span></span>  
  
### <a name="code-generation-business-rules"></a><span data-ttu-id="06615-131">代碼產生商務規則</span><span class="sxs-lookup"><span data-stu-id="06615-131">Code Generation Business Rules</span></span>  
 <span data-ttu-id="06615-132">自動為代碼屬性產生值的商務規則現在會以不同的方式管理。</span><span class="sxs-lookup"><span data-stu-id="06615-132">Business rules that automatically generate values for the Code attribute are now administered differently.</span></span> <span data-ttu-id="06615-133">先前，若要產生 Code 屬性的值，您在 [**商務規則**] 下的 [**系統管理**] 功能區域中，使用了 [預設屬性] 做為 [**產生的值**] 動作。</span><span class="sxs-lookup"><span data-stu-id="06615-133">Previously, to generate values for the Code attribute, you used the **Default attribute to a generated value** action in the **System Administration** functional area under **Business Rules**.</span></span> <span data-ttu-id="06615-134">現在，在 [**系統管理**] 中，您必須編輯實體以啟用自動產生的程式碼值。</span><span class="sxs-lookup"><span data-stu-id="06615-134">Now, in **System Administration**, you must edit the entity to enable automatically-generated Code values.</span></span> <span data-ttu-id="06615-135">如需詳細資訊，請參閱[自動建立程式碼 &#40;Master Data Services&#41;](automatic-code-creation-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="06615-135">For more information, see [Automatic Code Creation &#40;Master Data Services&#41;](automatic-code-creation-master-data-services.md).</span></span>  
  
 <span data-ttu-id="06615-136">如果您擁有包含此類型之規則的 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 模型部署封裝，當您將資料庫升級到 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 時，將會排除此商務規則。</span><span class="sxs-lookup"><span data-stu-id="06615-136">If you have a [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] model deployment package that contains a rule of this type, when you upgrade the database to [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], the business rule will be excluded.</span></span>  
  
### <a name="bulk-updates-and-exporting"></a><span data-ttu-id="06615-137">大量更新及匯出</span><span class="sxs-lookup"><span data-stu-id="06615-137">Bulk Updates and Exporting</span></span>  
 <span data-ttu-id="06615-138">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 應用程式中，您無法再針對多個成員大量更新屬性值。</span><span class="sxs-lookup"><span data-stu-id="06615-138">In the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application, you can no longer update attribute values for multiple members in bulk.</span></span> <span data-ttu-id="06615-139">若要執行大量更新，請使用暫存進程或 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="06615-139">To do bulk updates, use the staging process or the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].</span></span>  
  
 <span data-ttu-id="06615-140">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 應用程式中，您無法再將成員匯出到 Excel 中。</span><span class="sxs-lookup"><span data-stu-id="06615-140">In the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application, you can no longer export members to Excel.</span></span> <span data-ttu-id="06615-141">若要在 Excel 中使用成員，請使用 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="06615-141">To work with members in Excel, use the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="06615-142">異動</span><span class="sxs-lookup"><span data-stu-id="06615-142">Transactions</span></span>  
 <span data-ttu-id="06615-143">在 [ **Explorer** ] 功能區域中，使用者無法再還原自己的交易。</span><span class="sxs-lookup"><span data-stu-id="06615-143">In the **Explorer** functional area, users can no longer revert their own transactions.</span></span> <span data-ttu-id="06615-144">之前，使用者可以還原他們對**Explorer**中資料所做的變更。</span><span class="sxs-lookup"><span data-stu-id="06615-144">Previously, users could revert changes they made to data in **Explorer**.</span></span> <span data-ttu-id="06615-145">系統管理員仍然可以還原 [**版本管理**] 功能區域中所有使用者的交易。</span><span class="sxs-lookup"><span data-stu-id="06615-145">Administrators can still revert transactions for all users in the **Version Management** functional area.</span></span>  
  
 <span data-ttu-id="06615-146">註解現在是永久的，而且無法刪除。</span><span class="sxs-lookup"><span data-stu-id="06615-146">Annotations are now permanent and cannot be deleted.</span></span> <span data-ttu-id="06615-147">先前系統會將註解視為交易，因此可以透過還原交易來刪除。</span><span class="sxs-lookup"><span data-stu-id="06615-147">Previously, annotations were considered transactions and could be deleted by reverting the transaction.</span></span>  
  
### <a name="web-service"></a><span data-ttu-id="06615-148">Web 服務</span><span class="sxs-lookup"><span data-stu-id="06615-148">Web Service</span></span>  
 <span data-ttu-id="06615-149">如 Silverlight 所要求，系統現在會自動啟用 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web 服務。</span><span class="sxs-lookup"><span data-stu-id="06615-149">The [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] web service is now enabled automatically, as required by Silverlight.</span></span> <span data-ttu-id="06615-150">先前必須手動啟用 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="06615-150">Previously, the web service had to be enabled manually.</span></span>  
  
### <a name="powershell-cmdlets"></a><span data-ttu-id="06615-151">PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="06615-151">PowerShell Cmdlets</span></span>  
 <span data-ttu-id="06615-152">MDS 不再包含 PowerShell 指令程式。</span><span class="sxs-lookup"><span data-stu-id="06615-152">MDS no longer includes PowerShell cmdlets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06615-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06615-153">See Also</span></span>  
 [<span data-ttu-id="06615-154">SQL Server 2014 中已被取代的 Master Data Services 功能</span><span class="sxs-lookup"><span data-stu-id="06615-154">Deprecated Master Data Services Features in SQL Server 2014</span></span>](deprecated-master-data-services-features.md)  
  
  
