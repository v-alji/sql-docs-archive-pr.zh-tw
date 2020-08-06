---
title: 鎖定版本 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- versions [Master Data Services], locking
- locking versions [Master Data Services]
ms.assetid: 7bb62a84-12d8-4b29-9b6e-6aa25410618e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 68ef979b14d9bd228c7ca89a260b31b2fc6efccd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706549"
---
# <a name="lock-a-version-master-data-services"></a><span data-ttu-id="f5aa4-102">鎖定版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f5aa4-102">Lock a Version (Master Data Services)</span></span>
  <span data-ttu-id="f5aa4-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，鎖定模型版本，以防止模型成員及其屬性的變更。</span><span class="sxs-lookup"><span data-stu-id="f5aa4-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], lock a version of a model to prevent changes to the model's members and their attributes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f5aa4-104">版本已鎖定時，模型管理員可以繼續加入、編輯及移除成員。</span><span class="sxs-lookup"><span data-stu-id="f5aa4-104">When a version is locked, model administrators can continue to add, edit, and remove members.</span></span> <span data-ttu-id="f5aa4-105">其他具有模型權限的使用者只能檢視成員。</span><span class="sxs-lookup"><span data-stu-id="f5aa4-105">Other users with permission to the model can view members only.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f5aa4-106">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="f5aa4-106">Prerequisites</span></span>  
 <span data-ttu-id="f5aa4-107">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="f5aa4-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="f5aa4-108">您必須擁有存取 **[版本管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="f5aa4-108">You must have permission to access the **Version Management** functional area.</span></span>  
  
-   <span data-ttu-id="f5aa4-109">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="f5aa4-109">You must be a model administrator.</span></span> <span data-ttu-id="f5aa4-110">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f5aa4-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="f5aa4-111">版本的狀態必須是 [開啟]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f5aa4-111">The version's status must be **Open**.</span></span>  
  
### <a name="to-lock-a-version"></a><span data-ttu-id="f5aa4-112">若要鎖定版本</span><span class="sxs-lookup"><span data-stu-id="f5aa4-112">To lock a version</span></span>  
  
1.  <span data-ttu-id="f5aa4-113">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[版本管理]**。</span><span class="sxs-lookup"><span data-stu-id="f5aa4-113">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="f5aa4-114">在 [管理版本]\*\*\*\* 頁面上，選取要鎖定之版本的資料列。</span><span class="sxs-lookup"><span data-stu-id="f5aa4-114">On the **Manage Versions** page, select the row for the version that you want to lock.</span></span>  
  
3.  <span data-ttu-id="f5aa4-115">按一下 [鎖定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f5aa4-115">Click **Lock**.</span></span>  
  
4.  <span data-ttu-id="f5aa4-116">在確認對話方塊中按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f5aa4-116">In the confirmation dialog box, click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f5aa4-117">後續步驟</span><span class="sxs-lookup"><span data-stu-id="f5aa4-117">Next Steps</span></span>  
  
-   [<span data-ttu-id="f5aa4-118">根據商務規則驗證版本 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f5aa4-118">Validate a Version against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
-   [<span data-ttu-id="f5aa4-119">認可版本 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f5aa4-119">Commit a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/commit-a-version-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="f5aa4-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5aa4-120">See Also</span></span>  
 <span data-ttu-id="f5aa4-121">[版本 &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="f5aa4-121">[Versions &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md) </span></span>  
 [<span data-ttu-id="f5aa4-122">解除鎖定版本 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f5aa4-122">Unlock a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/unlock-a-version-master-data-services.md)  
  
  
