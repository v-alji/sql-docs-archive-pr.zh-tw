---
title: 安全性實體項目 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- securable items [Reporting Services]
- roles [Reporting Services], securable items
- security [Reporting Services], securable items listed
- role-based security [Reporting Services], securable items
ms.assetid: 27f58d4c-5c7b-4947-af5b-0f1fa60faf5f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f2f9fa5108831cb6c469710a71439bf3cfb6194a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598737"
---
# <a name="securable-items"></a><span data-ttu-id="2845a-102">安全性實體項目</span><span class="sxs-lookup"><span data-stu-id="2845a-102">Securable Items</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="2845a-103">會使用以角色為基礎的安全性，控制儲存在報表伺服器上之項目的存取權。</span><span class="sxs-lookup"><span data-stu-id="2845a-103">uses role-based security to control access to items that are stored on a report server.</span></span> <span data-ttu-id="2845a-104">當您授與使用者對報表伺服器的存取權時，您通常會建立一對角色指派來進行此動作：</span><span class="sxs-lookup"><span data-stu-id="2845a-104">When you grant a user access to a report server, you typically do so by creating a pair of role assignments:</span></span>  
  
-   <span data-ttu-id="2845a-105">在網站層級上。</span><span class="sxs-lookup"><span data-stu-id="2845a-105">At the site level</span></span>  
  
-   <span data-ttu-id="2845a-106">在主資料夾上，這是報表伺服器資料夾階層的根節點。</span><span class="sxs-lookup"><span data-stu-id="2845a-106">On Home, which is the root node of the report server folder hierarchy</span></span>  
  
 <span data-ttu-id="2845a-107">安全性會在報表伺服器資料夾階層中繼承。</span><span class="sxs-lookup"><span data-stu-id="2845a-107">Security is inherited within the report server folder hierarchy.</span></span> <span data-ttu-id="2845a-108">在網站層級和主資料夾上建立角色指派，會設定可擴充至所有項目的權限繼承及報表伺服器上的作業。</span><span class="sxs-lookup"><span data-stu-id="2845a-108">Creating role assignments at the site level and on the Home folder sets permission inheritance that extends to all items and operations on a report server.</span></span>  
  
 <span data-ttu-id="2845a-109">您可以為個別項目定義安全性，以覆寫權限繼承。</span><span class="sxs-lookup"><span data-stu-id="2845a-109">You can override permission inheritance by defining security for individual items.</span></span> <span data-ttu-id="2845a-110">您可以個別維護安全的項目包括：</span><span class="sxs-lookup"><span data-stu-id="2845a-110">Items that you can secure individually include:</span></span>  
  
-   <span data-ttu-id="2845a-111">資料夾</span><span class="sxs-lookup"><span data-stu-id="2845a-111">Folders</span></span>  
  
-   <span data-ttu-id="2845a-112">報表</span><span class="sxs-lookup"><span data-stu-id="2845a-112">Reports</span></span>  
  
-   <span data-ttu-id="2845a-113">報表模型</span><span class="sxs-lookup"><span data-stu-id="2845a-113">Report models</span></span>  
  
-   <span data-ttu-id="2845a-114">資源</span><span class="sxs-lookup"><span data-stu-id="2845a-114">Resources</span></span>  
  
-   <span data-ttu-id="2845a-115">共用資料來源</span><span class="sxs-lookup"><span data-stu-id="2845a-115">Shared data sources</span></span>  
  
-   <span data-ttu-id="2845a-116">共用資料集</span><span class="sxs-lookup"><span data-stu-id="2845a-116">Shared datasets</span></span>  
  
 <span data-ttu-id="2845a-117">其他建構 (例如排程與訂閱) 並未明確保護。</span><span class="sxs-lookup"><span data-stu-id="2845a-117">Other constructs, such as schedules and subscriptions, are not explicitly secured.</span></span> <span data-ttu-id="2845a-118">排程與訂閱是在報表的安全性內作業。</span><span class="sxs-lookup"><span data-stu-id="2845a-118">Schedules and subscriptions operate within the security of a report.</span></span>  
  
## <a name="item-descriptions"></a><span data-ttu-id="2845a-119">項目描述</span><span class="sxs-lookup"><span data-stu-id="2845a-119">Item Descriptions</span></span>  
 <span data-ttu-id="2845a-120">下表列出安全性實體項目並敘述它們的特性。</span><span class="sxs-lookup"><span data-stu-id="2845a-120">The following table lists securable items and describes their characteristics.</span></span>  
  
|<span data-ttu-id="2845a-121">Item</span><span class="sxs-lookup"><span data-stu-id="2845a-121">Item</span></span>|<span data-ttu-id="2845a-122">特性</span><span class="sxs-lookup"><span data-stu-id="2845a-122">Characteristics</span></span>|  
|----------|---------------------|  
|<span data-ttu-id="2845a-123">資料夾</span><span class="sxs-lookup"><span data-stu-id="2845a-123">Folders</span></span>|<span data-ttu-id="2845a-124">資料夾安全性會套用至資料夾本身以及它包含的項目。</span><span class="sxs-lookup"><span data-stu-id="2845a-124">Folder security applies to the folder itself and the items it contains.</span></span> <span data-ttu-id="2845a-125">[主資料夾] 資料夾是資料夾階層的根節點。</span><span class="sxs-lookup"><span data-stu-id="2845a-125">The Home folder is the root node of the folder hierarchy.</span></span> <span data-ttu-id="2845a-126">此資料夾所設定的安全性，會為資料夾階層中所有從屬的資料夾、報表、資源和共用資料來源，建立初始安全性設定。</span><span class="sxs-lookup"><span data-stu-id="2845a-126">Security that you set for this folder establishes the initial security settings for all subordinate folders, reports, resources, and shared data sources in the folder hierarchy.</span></span> <span data-ttu-id="2845a-127">如需詳細資訊，請參閱 [保護資料夾的安全](secure-folders.md)。</span><span class="sxs-lookup"><span data-stu-id="2845a-127">For more information, see [Secure Folders](secure-folders.md).</span></span><br /><br /> <span data-ttu-id="2845a-128">[我的報表] 是特殊用途資料夾，可以透過以專用角色為基礎的隱含角色指派來保護。</span><span class="sxs-lookup"><span data-stu-id="2845a-128">My Reports is a special-purpose folder that is secured through an implied role assignment based on a dedicated role.</span></span> <span data-ttu-id="2845a-129">如需詳細資訊，請參閱 [保護我的報表](secure-my-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="2845a-129">For more information, see [Secure My Reports](secure-my-reports.md).</span></span>|  
|<span data-ttu-id="2845a-130">報表</span><span class="sxs-lookup"><span data-stu-id="2845a-130">Reports</span></span>|<span data-ttu-id="2845a-131">可以保護報表與連結報表，以控制使用者可以執行之動作的範圍，例如變更給定報表的屬性。</span><span class="sxs-lookup"><span data-stu-id="2845a-131">Reports and linked reports can be secured to control the range of actions that users can perform, such as changing the properties of a given report.</span></span><br /><br /> <span data-ttu-id="2845a-132">報表記錄是透過包含記錄的報表來保護。</span><span class="sxs-lookup"><span data-stu-id="2845a-132">Report history is secured through the report that contains the history.</span></span> <span data-ttu-id="2845a-133">您無法保護報表記錄內的個別快照集。</span><span class="sxs-lookup"><span data-stu-id="2845a-133">You cannot secure individual snapshots within report history.</span></span><br /><br /> <span data-ttu-id="2845a-134">如需保護報表的詳細資訊，請參閱 [保護報表和資源的安全](secure-reports-and-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="2845a-134">For more information about report security, see [Secure Reports and Resources](secure-reports-and-resources.md).</span></span>|  
|<span data-ttu-id="2845a-135">報表模型</span><span class="sxs-lookup"><span data-stu-id="2845a-135">Report models</span></span>|<span data-ttu-id="2845a-136">您可以在全部或部分的報表模型上，指定角色指派。</span><span class="sxs-lookup"><span data-stu-id="2845a-136">You can specify role assignment on all or part of a report model.</span></span> <span data-ttu-id="2845a-137">因為報表模型可能很龐大，所以您可能要保護對應至機密資料的模型項目。</span><span class="sxs-lookup"><span data-stu-id="2845a-137">Because report models can be quite extensive, you might want to secure the model items that map to confidential data.</span></span>|  
|<span data-ttu-id="2845a-138">資源</span><span class="sxs-lookup"><span data-stu-id="2845a-138">Resources</span></span>|<span data-ttu-id="2845a-139">可以保護資源，來控制資源本身與其屬性的存取。</span><span class="sxs-lookup"><span data-stu-id="2845a-139">Resources can be secured to control access to the resource itself and its properties.</span></span><br /><br /> <span data-ttu-id="2845a-140">只有獨立的資源可以當成個別項目來保護。</span><span class="sxs-lookup"><span data-stu-id="2845a-140">Only stand-alone resources can be secured as separate items.</span></span> <span data-ttu-id="2845a-141">內嵌在報表中的資源，無法與報表分開保護。</span><span class="sxs-lookup"><span data-stu-id="2845a-141">Resources that are embedded within a report cannot be secured separately from that report.</span></span><br /><br /> <span data-ttu-id="2845a-142">如需資源安全性的詳細資訊，請參閱 [保護報表和資源的安全](secure-reports-and-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="2845a-142">For more information about resource security, see [Secure Reports and Resources](secure-reports-and-resources.md).</span></span>|  
|<span data-ttu-id="2845a-143">共用資料來源</span><span class="sxs-lookup"><span data-stu-id="2845a-143">Shared data sources</span></span>|<span data-ttu-id="2845a-144">共用資料來源可以進行保護，以限制對項目及其屬性頁面的存取。</span><span class="sxs-lookup"><span data-stu-id="2845a-144">Shared data sources can be secured to limit access to the item and its property pages.</span></span> <span data-ttu-id="2845a-145">如需詳細資訊，請參閱 [保護共用資料來源項目的安全](secure-shared-data-source-items.md)。</span><span class="sxs-lookup"><span data-stu-id="2845a-145">For more information, see [Secure Shared Data Source Items](secure-shared-data-source-items.md).</span></span>|  
|<span data-ttu-id="2845a-146">共用資料集</span><span class="sxs-lookup"><span data-stu-id="2845a-146">Shared datasets</span></span>|<span data-ttu-id="2845a-147">共用資料集可以進行保護，以控制使用者能夠執行的動作範圍，例如，檢視或變更定義，或變更指定共用資料集的屬性。</span><span class="sxs-lookup"><span data-stu-id="2845a-147">Shared datasets can be secured to control the range of actions that users can perform, such as viewing or changing the definition, or changing the properties of a given shared dataset.</span></span><br /><br /> <span data-ttu-id="2845a-148">如需詳細資訊，請參閱 [保護共用資料集項目的安全](secure-shared-dataset-items.md)。</span><span class="sxs-lookup"><span data-stu-id="2845a-148">For more information, see [Secure Shared Dataset Items](secure-shared-dataset-items.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2845a-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2845a-149">See Also</span></span>  
 <span data-ttu-id="2845a-150">[在原生模式報表伺服器上授與權限](granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="2845a-150">[Granting Permissions on a Native Mode Report Server](granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 <span data-ttu-id="2845a-151">[建立、刪除或修改角色 &#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md) </span><span class="sxs-lookup"><span data-stu-id="2845a-151">[Create, Delete, or Modify a Role &#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md) </span></span>  
 <span data-ttu-id="2845a-152">[將報表伺服器的存取權授與使用者 &#40;報表管理員&#41;](grant-user-access-to-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="2845a-152">[Grant User Access to a Report Server &#40;Report Manager&#41;](grant-user-access-to-a-report-server.md) </span></span>  
 [<span data-ttu-id="2845a-153">修改或刪除角色指派 &#40;報表管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="2845a-153">Modify or Delete a Role Assignment &#40;Report Manager&#41;</span></span>](role-assignments-modify-or-delete.md)  
  
  
