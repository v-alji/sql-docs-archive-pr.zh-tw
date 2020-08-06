---
title: 角色和許可權 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- security [Analysis Services], about security
- security [Analysis Services - multidimensional data], about security
ms.assetid: bb885447-868b-4686-853c-8241f63d4370
author: minewiskan
ms.author: owend
ms.openlocfilehash: d6595d931b2c2760e5fd3013ff6bec88f85106d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710902"
---
# <a name="roles-and-permissions-analysis-services"></a><span data-ttu-id="8610f-102">角色與權限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="8610f-102">Roles and Permissions (Analysis Services)</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="8610f-103">提供以角色為基礎的授權模型，授與作業、物件和資料的存取權。</span><span class="sxs-lookup"><span data-stu-id="8610f-103">provides a role-based authorization model that grants access to operations, objects, and data.</span></span> <span data-ttu-id="8610f-104">所有存取 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體或資料庫的使用者都必須在角色的內容中進行存取。</span><span class="sxs-lookup"><span data-stu-id="8610f-104">All users who access an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance or database must do so within the context of a role.</span></span>  
  
 <span data-ttu-id="8610f-105">身為 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 系統管理員，您需負責將可無限制存取伺服器上之作業的成員資格授與 **伺服器管理員角色** 。</span><span class="sxs-lookup"><span data-stu-id="8610f-105">As an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] system administrator, you are in charge of granting membership to the **server administrator role** that conveys unrestricted access to operations on the server.</span></span> <span data-ttu-id="8610f-106">此角色有固定的權限，無法進行自訂。</span><span class="sxs-lookup"><span data-stu-id="8610f-106">This role has fixed permissions and cannot be customized.</span></span> <span data-ttu-id="8610f-107">依預設，本機 Administrators 群組的成員會自動成為 Analysis Services 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="8610f-107">By default, members of the local Administrators group are automatically Analysis Services system administrators.</span></span>  
  
 <span data-ttu-id="8610f-108">查詢或處理資料的非管理員使用者是透過 **資料庫角色**來授與存取權。</span><span class="sxs-lookup"><span data-stu-id="8610f-108">Non-administrative users who query or process data are granted access through **database roles**.</span></span> <span data-ttu-id="8610f-109">系統管理員和資料庫管理員都能建立描述指定資料庫內不同存取層級的角色，然後將成員資格指派給每個需要存取的使用者。</span><span class="sxs-lookup"><span data-stu-id="8610f-109">Both system administrators and database administrators can create the roles that describe different levels of access within a given database, and then assign membership to every user who requires access.</span></span> <span data-ttu-id="8610f-110">每一個角色都有一組自訂權限，可用以存取特定資料庫內的物件和作業。</span><span class="sxs-lookup"><span data-stu-id="8610f-110">Each role has a customized set of permissions for accessing objects and operations within a particular database.</span></span> <span data-ttu-id="8610f-111">您可以指派下列層級的權限：資料庫、內部物件如 Cube 和維度 (但不是檢視方塊)，以及資料列。</span><span class="sxs-lookup"><span data-stu-id="8610f-111">You can assign permissions at these levels: database, interior objects such as cubes and dimensions (but not perspectives), and rows.</span></span>  
  
 <span data-ttu-id="8610f-112">常見作法是建立角色並將成員資格指派為個別作業。</span><span class="sxs-lookup"><span data-stu-id="8610f-112">It is common practice to create roles and assign membership as separate operations.</span></span> <span data-ttu-id="8610f-113">通常模型設計人員會在設計階段加入角色。</span><span class="sxs-lookup"><span data-stu-id="8610f-113">Often, the model designer adds roles during the design phase.</span></span> <span data-ttu-id="8610f-114">如此一來，所有角色定義都會反映在定義模型的專案檔案中。</span><span class="sxs-lookup"><span data-stu-id="8610f-114">This way, all role definitions are reflected in the project files that define the model.</span></span> <span data-ttu-id="8610f-115">角色成員資格通常是由資料庫管理員建立可開發、測試及執行為獨立作業的指令碼，稍後在資料庫進入實際執行階段時展開。</span><span class="sxs-lookup"><span data-stu-id="8610f-115">Role membership is typically rolled out later as the database moves into production, usually by database administrators who create scripts that can be developed, tested, and run as an independent operation.</span></span>  
  
 <span data-ttu-id="8610f-116">所有授權都是基於有效的 Windows 使用者識別。</span><span class="sxs-lookup"><span data-stu-id="8610f-116">All authorization is predicated on a valid Windows user identity.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="8610f-117">只使用 Windows 驗證來驗證使用者識別。</span><span class="sxs-lookup"><span data-stu-id="8610f-117">uses Windows authentication exclusively to authenticate user identities.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="8610f-118">未提供任何專屬的驗證方法。請參閱[Analysis Services 支援的驗證方法](../instances/authentication-methodologies-supported-by-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="8610f-118">provides no proprietary authentication method.See [Authentication methodologies supported by Analysis Services](../instances/authentication-methodologies-supported-by-analysis-services.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8610f-119">每個 Windows 使用者或群組的權限可透過資料庫中的所有角色來加總。</span><span class="sxs-lookup"><span data-stu-id="8610f-119">Permissions are additive for each Windows user or group, across all roles in the database.</span></span> <span data-ttu-id="8610f-120">如果一個角色拒絕使用者或群組執行特定工作或檢視特定資料的權限，但另一個角色授與此權限給該使用者或群組，則該使用者或群組將擁有執行此工作或檢視此資料的權限。</span><span class="sxs-lookup"><span data-stu-id="8610f-120">If one role denies a user or group permission to perform certain tasks or view certain data, but another role grants this permission to that user or group, the user or group will have permission to perform the task or view the data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8610f-121">本節內容</span><span class="sxs-lookup"><span data-stu-id="8610f-121">In this section</span></span>  
  
-   [<span data-ttu-id="8610f-122">物件和作業的存取權授權 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="8610f-122">Authorizing access to objects and operations &#40;Analysis Services&#41;</span></span>](authorizing-access-to-objects-and-operations-analysis-services.md)  
  
-   [<span data-ttu-id="8610f-123">授與資料庫權限 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="8610f-123">Grant database permissions &#40;Analysis Services&#41;</span></span>](grant-database-permissions-analysis-services.md)  
  
-   [<span data-ttu-id="8610f-124">授與 Cube 或模型權限 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="8610f-124">Grant cube or model permissions &#40;Analysis Services&#41;</span></span>](grant-cube-or-model-permissions-analysis-services.md)  
  
-   [<span data-ttu-id="8610f-125">授與處理權限 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="8610f-125">Grant process permissions &#40;Analysis Services&#41;</span></span>](grant-process-permissions-analysis-services.md)  
  
-   [<span data-ttu-id="8610f-126">授與物件中繼資料的讀取定義權限 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="8610f-126">Grant read definition permissions on object metadata &#40;Analysis Services&#41;</span></span>](grant-read-definition-permissions-on-object-metadata-analysis-services.md)  
  
-   [<span data-ttu-id="8610f-127">授與資料來源物件的權限 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="8610f-127">Grant permissions on a data source object &#40;Analysis Services&#41;</span></span>](grant-permissions-on-a-data-source-object-analysis-services.md)  
  
-   [<span data-ttu-id="8610f-128">授與資料採礦結構和模型的權限 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="8610f-128">Grant permissions on data mining structures and models &#40;Analysis Services&#41;</span></span>](grant-permissions-on-data-mining-structures-and-models-analysis-services.md)  
  
-   [<span data-ttu-id="8610f-129">授與維度的權限 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="8610f-129">Grant permissions on a dimension &#40;Analysis Services&#41;</span></span>](grant-permissions-on-a-dimension-analysis-services.md)  
  
-   [<span data-ttu-id="8610f-130">授與維度資料的自訂存取權 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="8610f-130">Grant custom access to dimension data &#40;Analysis Services&#41;</span></span>](grant-custom-access-to-dimension-data-analysis-services.md)  
  
-   [<span data-ttu-id="8610f-131">授與資料格資料的自訂存取權 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="8610f-131">Grant custom access to cell data &#40;Analysis Services&#41;</span></span>](grant-custom-access-to-cell-data-analysis-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="8610f-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8610f-132">See Also</span></span>  
 [<span data-ttu-id="8610f-133">建立及管理角色 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="8610f-133">Create and Manage Roles &#40;SSAS Tabular&#41;</span></span>](../tabular-models/roles-ssas-tabular.md)  
  
  
