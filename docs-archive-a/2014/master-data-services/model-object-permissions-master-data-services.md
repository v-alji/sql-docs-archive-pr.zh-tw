---
title: 模型物件權限 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Master Data Services], model objects
- models [Master Data Services], object permissions
ms.assetid: fab6335b-4cae-47de-ae7c-6c4743e0680f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 4cc64d753b680cfabc3707a29c6d9de631708c20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599545"
---
# <a name="model-object-permissions-master-data-services"></a><span data-ttu-id="5047c-102">模型物件權限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="5047c-102">Model Object Permissions (Master Data Services)</span></span>
  <span data-ttu-id="5047c-103">模型物件權限是強制性的。</span><span class="sxs-lookup"><span data-stu-id="5047c-103">Model object permissions are mandatory.</span></span> <span data-ttu-id="5047c-104">這些權限會決定使用者可以在此 UI 的 [總管]\*\*\*\* 功能區域中存取的屬性。</span><span class="sxs-lookup"><span data-stu-id="5047c-104">They determine the attributes a user can access in the **Explorer** functional area of the UI.</span></span>  
  
 <span data-ttu-id="5047c-105">例如，如果您將 Product 實體的 **更新** 權限指派給某個使用者，該使用者就可以更新 Product 實體的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="5047c-105">For example, if you assign a user **Update** permission to the Product entity, the user can update all of the attributes of the Product entity.</span></span> <span data-ttu-id="5047c-106">如果您指派單一屬性的 **更新** 權限，使用者僅能更新該屬性。</span><span class="sxs-lookup"><span data-stu-id="5047c-106">If you assign **Update** permission to a single attribute, the user can update that attribute only.</span></span>  
  
 <span data-ttu-id="5047c-107">若要判斷針對每個個別屬性值指派的安全性，可以將模型物件權限結合階層成員權限，後者可決定使用者可以存取的成員。</span><span class="sxs-lookup"><span data-stu-id="5047c-107">To determine security assigned on each individual attribute value, model object permissions are combined with hierarchy member permissions, which determine the members a user can access.</span></span>  
  
 <span data-ttu-id="5047c-108">若要授與使用者對 [ **Explorer**] 以外功能區域的存取權，使用者必須是模型管理員，這也牽涉到指派模型物件使用權限。</span><span class="sxs-lookup"><span data-stu-id="5047c-108">To give a user access to a functional area other than **Explorer**, the user must be a model administrator, which also involves assigning model object permissions.</span></span> <span data-ttu-id="5047c-109">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="5047c-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
 <span data-ttu-id="5047c-110">模型物件使用權限會在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 使用者介面 (UI) 的 [**模型**] 索引標籤上的 [**使用者和群組的許可權**] 功能區域中指派。在此索引標籤上，模型是以樹狀結構表示。</span><span class="sxs-lookup"><span data-stu-id="5047c-110">Model object permissions are assigned in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] user interface (UI), in the **User and Group Permissions** functional area on the **Models** tab. On this tab, the model is represented as a tree structure.</span></span> <span data-ttu-id="5047c-111">當您將權限指派給樹狀結構中的物件時，底下的所有物件都會繼承該權限。</span><span class="sxs-lookup"><span data-stu-id="5047c-111">When you assign permission to an object in the tree, all objects below inherit that permission.</span></span> <span data-ttu-id="5047c-112">您可以將權限指派給個別物件來覆寫該項繼承。</span><span class="sxs-lookup"><span data-stu-id="5047c-112">You can override that inheritance by assigning permission to individual objects.</span></span>  
  
 <span data-ttu-id="5047c-113">您可以將 [**唯讀**]、[**更新**] 或 [**拒絕**] 許可權指派給模型物件。</span><span class="sxs-lookup"><span data-stu-id="5047c-113">You can assign **Read-only**, **Update**, or **Deny** permission to model objects.</span></span> <span data-ttu-id="5047c-114">如果您未在 [模型]\*\*\*\* 索引標籤上指派任何權限，使用者就無法在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 中檢視任何模型或資料。</span><span class="sxs-lookup"><span data-stu-id="5047c-114">If you do not assign any permissions on the **Models** tab, the user cannot view any models or data in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
## <a name="best-practice"></a><span data-ttu-id="5047c-115">最佳做法</span><span class="sxs-lookup"><span data-stu-id="5047c-115">Best Practice</span></span>  
 <span data-ttu-id="5047c-116">一般而言，您應該指派模型物件的 [**更新**] 許可權，然後明確地將許可權指派給底下的物件。</span><span class="sxs-lookup"><span data-stu-id="5047c-116">In general, you should assign **Update** permission to the model object, and then explicitly assign permission to objects underneath.</span></span> <span data-ttu-id="5047c-117">如果您沒有指派底下物件的權限，就會繼承權限，而且使用者是管理員。</span><span class="sxs-lookup"><span data-stu-id="5047c-117">If you do not assign permission to objects underneath, the permissions are inherited and the user is an administrator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5047c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5047c-118">See Also</span></span>  
 <span data-ttu-id="5047c-119">[指派模型物件使用權限 &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="5047c-119">[Assign Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="5047c-120">[模型許可權 &#40;Master Data Services&#41;](../../2014/master-data-services/model-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="5047c-120">[Model Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/model-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="5047c-121">[功能區域許可權 &#40;Master Data Services&#41;](../../2014/master-data-services/functional-area-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="5047c-121">[Functional Area Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/functional-area-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="5047c-122">[階層成員許可權 &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="5047c-122">[Hierarchy Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="5047c-123">如何決定權限 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="5047c-123">How Permissions Are Determined &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  
