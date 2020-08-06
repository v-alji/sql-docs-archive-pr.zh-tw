---
title: 分類的 Web 服務作業 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: e3f346b5-7e26-481d-9821-1846e2e91289
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0f7dd682f55c16c6dcbff9f0f669593a10486da6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598498"
---
# <a name="categorized-web-service-operations-master-data-services"></a><span data-ttu-id="33323-102">分類的 Web 服務作業 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="33323-102">Categorized Web Service Operations (Master Data Services)</span></span>
  <span data-ttu-id="33323-103"> Web 服務包含一組完整的作業，這組作業可讓您撰寫程式碼以控制  透過其使用者介面所執行的所有功能。</span><span class="sxs-lookup"><span data-stu-id="33323-103">The [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] web service contains a complete set of operations that let you write code to control all of the features that [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] does through its user interface.</span></span> <span data-ttu-id="33323-104">這些 Web 服務作業是透過 <xref:Microsoft.MasterDataServices.IService> 介面定義，並當做 <xref:Microsoft.MasterDataServices.ServiceClient> 類別中的方法實作。</span><span class="sxs-lookup"><span data-stu-id="33323-104">The web service operations are defined by the <xref:Microsoft.MasterDataServices.IService> interface and are implemented as methods in the <xref:Microsoft.MasterDataServices.ServiceClient> class.</span></span> <span data-ttu-id="33323-105">本主題將 Web 服務作業分為概念性類別目錄，以協助您了解如何使用 Web 服務 API。</span><span class="sxs-lookup"><span data-stu-id="33323-105">This topic groups the web service operations into conceptual categories to help you understand how to use the web service API.</span></span>  
  
## <a name="model-operations"></a><span data-ttu-id="33323-106">模型作業</span><span class="sxs-lookup"><span data-stu-id="33323-106">Model Operations</span></span>  
 <span data-ttu-id="33323-107">這些作業用於建立、更新與刪除模型，以及針對模型的所有內容操作，例如實體、階層和版本。</span><span class="sxs-lookup"><span data-stu-id="33323-107">These operations are used to create, update, and delete models, as well as to operate on all the contents of a model, such as entities, hierarchies, and versions.</span></span> <span data-ttu-id="33323-108">如需詳細資訊，請參閱[模型 &#40;Master Data Services&#41;](../models-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="33323-108">For more information, see [Models &#40;Master Data Services&#41;](../models-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.MetadataClone%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.MetadataCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.MetadataDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.MetadataGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.MetadataUpdate%2A>|  
  
## <a name="entity-operations"></a><span data-ttu-id="33323-109">實體作業</span><span class="sxs-lookup"><span data-stu-id="33323-109">Entity Operations</span></span>  
 <span data-ttu-id="33323-110">這些作業用於建立、更新與刪除單一實體的成員。</span><span class="sxs-lookup"><span data-stu-id="33323-110">These operations are used to create, update, and delete the members of a single entity.</span></span> <span data-ttu-id="33323-111">如需詳細資訊，請參閱[實體 &#40;Master Data Services&#41;](../entities-master-data-services.md) 和[成員 &#40;Master Data Services&#41;](../members-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="33323-111">For more information, see [Entities &#40;Master Data Services&#41;](../entities-master-data-services.md) and [Members &#40;Master Data Services&#41;](../members-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMemberKeyLookup%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMembersCopy%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMembersCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMembersDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMembersGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMembersMerge%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMembersUpdate%2A>|  
  
## <a name="member-operations"></a><span data-ttu-id="33323-112">成員作業</span><span class="sxs-lookup"><span data-stu-id="33323-112">Member Operations</span></span>  
 <span data-ttu-id="33323-113">這些作業用於取得、更新與刪除成員。</span><span class="sxs-lookup"><span data-stu-id="33323-113">These operations are used to get, update, and delete members.</span></span> <span data-ttu-id="33323-114">這組成員的操作對象可以包含來自多個實體的成員。</span><span class="sxs-lookup"><span data-stu-id="33323-114">The set of members operated on can contain members from multiple entities.</span></span> <span data-ttu-id="33323-115">如需詳細資訊，請參閱[成員 &#40;Master Data Services&#41;](../members-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="33323-115">For more information, see [Members &#40;Master Data Services&#41;](../members-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ModelMembersBulkDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ModelMembersBulkMerge%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ModelMembersBulkUpdate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ModelMembersGet%2A>|  
  
## <a name="attribute-and-hierarchy-operations"></a><span data-ttu-id="33323-116">屬性和階層作業</span><span class="sxs-lookup"><span data-stu-id="33323-116">Attribute and Hierarchy Operations</span></span>  
 <span data-ttu-id="33323-117">這些作業用於取得屬性和階層資訊。</span><span class="sxs-lookup"><span data-stu-id="33323-117">These operations are used to get attribute and hierarchy information.</span></span> <span data-ttu-id="33323-118">您也可以使用模型作業 (例如 <xref:Microsoft.MasterDataServices.ServiceClient.MetadataUpdate%2A>) 來修改屬性和階層。</span><span class="sxs-lookup"><span data-stu-id="33323-118">Attributes and hierarchies can also be modified by using the model operations, such as <xref:Microsoft.MasterDataServices.ServiceClient.MetadataUpdate%2A>.</span></span> <span data-ttu-id="33323-119">如需詳細資訊，請參閱[屬性 &#40;Master Data Services&#41;](../attributes-master-data-services.md) 和[階層 &#40;Master Data Services&#41;](../hierarchies-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="33323-119">For more information, see [Attributes &#40;Master Data Services&#41;](../attributes-master-data-services.md) and [Hierarchies &#40;Master Data Services&#41;](../hierarchies-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMemberAttributesGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.HierarchyMembersGet%2A>|  
  
## <a name="business-rule-operations"></a><span data-ttu-id="33323-120">商務規則作業</span><span class="sxs-lookup"><span data-stu-id="33323-120">Business Rule Operations</span></span>  
 <span data-ttu-id="33323-121">這些作業用於建立、更新、刪除與發佈商務規則。</span><span class="sxs-lookup"><span data-stu-id="33323-121">These operations are used to create, update, delete, and publish business rules.</span></span> <span data-ttu-id="33323-122">如需詳細資訊，請參閱[商務規則 &#40;Master Data Services&#41;](../business-rules-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="33323-122">For more information, see [Business Rules &#40;Master Data Services&#41;](../business-rules-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesClone%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesPaletteGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesPublish%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.BusinessRulesUpdate%2A>|  
  
## <a name="annotation-operations"></a><span data-ttu-id="33323-123">註解作業</span><span class="sxs-lookup"><span data-stu-id="33323-123">Annotation Operations</span></span>  
 <span data-ttu-id="33323-124">這些作業用於建立、更新與刪除註解。</span><span class="sxs-lookup"><span data-stu-id="33323-124">These operations are used to create, update, and delete annotations.</span></span> <span data-ttu-id="33323-125">如需詳細資訊，請參閱[註解 &#40;Master Data Services&#41;](../annotations-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="33323-125">For more information, see [Annotations &#40;Master Data Services&#41;](../annotations-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.AnnotationsDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.AnnotationsUpdate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMemberAnnotationsCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityMemberAnnotationsGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.TransactionAnnotationsCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.TransactionAnnotationsGet%2A>|  
  
## <a name="transaction-operations"></a><span data-ttu-id="33323-126">交易作業</span><span class="sxs-lookup"><span data-stu-id="33323-126">Transaction Operations</span></span>  
 <span data-ttu-id="33323-127">這些作業用於取得與反轉交易。</span><span class="sxs-lookup"><span data-stu-id="33323-127">These operations are used to get and reverse transactions.</span></span> <span data-ttu-id="33323-128">如需詳細資訊，請參閱[交易 &#40;Master Data Services&#41;](../transactions-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="33323-128">For more information, see [Transactions &#40;Master Data Services&#41;](../transactions-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.TransactionsGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.TransactionsReverse%2A>|  
  
## <a name="version-and-validation-operations"></a><span data-ttu-id="33323-129">版本和驗證作業</span><span class="sxs-lookup"><span data-stu-id="33323-129">Version and Validation Operations</span></span>  
 <span data-ttu-id="33323-130">這些作業用於複製和驗證版本。</span><span class="sxs-lookup"><span data-stu-id="33323-130">These operations are used to copy and validate versions.</span></span> <span data-ttu-id="33323-131">如需詳細資訊，請參閱[版本 &#40;Master Data Services&#41;](../versions-master-data-services.md) 和[驗證 &#40;Master Data Services&#41;](../validation-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="33323-131">For more information, see [Versions &#40;Master Data Services&#41;](../versions-master-data-services.md) and [Validation &#40;Master Data Services&#41;](../validation-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.VersionCopy%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ValidationGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ValidationProcess%2A>|  
  
## <a name="data-quality-operations"></a><span data-ttu-id="33323-132">資料品質作業</span><span class="sxs-lookup"><span data-stu-id="33323-132">Data Quality Operations</span></span>  
 <span data-ttu-id="33323-133">這些作業用於執行資料品質工作及檢查其結果。</span><span class="sxs-lookup"><span data-stu-id="33323-133">These operations are used to perform data quality tasks and to examine their results.</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityCleansingOperationCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityMatchingOperationCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityOperationStart%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityInstalledState%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityKnowledgeBasesGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityOperationResultsGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.DataQualityOperationStatus%2A>|  
  
## <a name="data-import-operations"></a><span data-ttu-id="33323-134">資料匯入作業</span><span class="sxs-lookup"><span data-stu-id="33323-134">Data Import Operations</span></span>  
 <span data-ttu-id="33323-135">這些作業用於將資料匯入至 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="33323-135">These operations are used to import data into a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="33323-136">如需詳細資訊，請參閱[資料匯入 &#40;Master Data Services&#41;](../overview-importing-data-from-tables-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="33323-136">For more information, see [Data Import &#40;Master Data Services&#41;](../overview-importing-data-from-tables-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityStagingClear%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityStagingGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityStagingLoad%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.EntityStagingProcess%2A>|  
  
 <span data-ttu-id="33323-137">下列作業用於透過 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 中包含的暫存處理序匯入資料。</span><span class="sxs-lookup"><span data-stu-id="33323-137">The following operations are used to import data by using the staging process included in [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].</span></span> <span data-ttu-id="33323-138">這些作業僅用於支援現有的資料庫。</span><span class="sxs-lookup"><span data-stu-id="33323-138">These operations should be used only to support existing databases.</span></span> <span data-ttu-id="33323-139">對於新的開發，請使用先前列出的作業。</span><span class="sxs-lookup"><span data-stu-id="33323-139">For new development, use the previously listed operations.</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.StagingClear%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.StagingGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.StagingNameCheck%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.StagingProcess%2A>|  
  
## <a name="data-export-operations"></a><span data-ttu-id="33323-140">資料匯出作業</span><span class="sxs-lookup"><span data-stu-id="33323-140">Data Export Operations</span></span>  
 <span data-ttu-id="33323-141">這些作業用於透過訂閱檢視匯出資料。</span><span class="sxs-lookup"><span data-stu-id="33323-141">These operations are used to export data through the use of subscription views.</span></span> <span data-ttu-id="33323-142">如需詳細資訊，請參閱[匯出資料 &#40;Master Data Services&#41;](../overview-exporting-data-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="33323-142">For more information, see [Exporting Data &#40;Master Data Services&#41;](../overview-exporting-data-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ExportViewCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ExportViewDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ExportViewListGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ExportViewUpdate%2A>|  
  
## <a name="security-operations"></a><span data-ttu-id="33323-143">安全性作業</span><span class="sxs-lookup"><span data-stu-id="33323-143">Security Operations</span></span>  
 <span data-ttu-id="33323-144">這些作業用於修改控制對 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 資料庫之存取的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="33323-144">These operations are used to modify the security settings that control access to the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="33323-145">如需詳細資訊，請參閱[安全性 &#40;Master Data Services&#41;](../security-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="33323-145">For more information, see [Security &#40;Master Data Services&#41;](../security-master-data-services.md).</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrincipalsClone%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrincipalsCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrincipalsDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrincipalsGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrincipalsUpdate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrivilegesClone%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrivilegesCreate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrivilegesDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrivilegesGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SecurityPrivilegesUpdate%2A>|  
  
## <a name="system-operations"></a><span data-ttu-id="33323-146">系統作業</span><span class="sxs-lookup"><span data-stu-id="33323-146">System Operations</span></span>  
 <span data-ttu-id="33323-147">這些作業用於取得與更新系統設定和使用者喜好設定。</span><span class="sxs-lookup"><span data-stu-id="33323-147">These operations are used to get and update system settings and user preferences.</span></span>  
  
||  
|-|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ServiceCheck%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.ServiceVersionGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SystemDomainListGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SystemPropertiesGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SystemSettingsGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.SystemSettingsUpdate%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.UserPreferencesDelete%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.UserPreferencesGet%2A>|  
|<xref:Microsoft.MasterDataServices.ServiceClient.UserPreferencesUpdate%2A>|  
  
  
