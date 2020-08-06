---
title: 認可版本 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- committing versions [Master Data Services]
- versions [Master Data Services], committing
ms.assetid: 6b967a39-b333-4b84-9e5f-4fb07e156826
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: cec3244d4ddaa78d9168e3ede503fa16756633a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699976"
---
# <a name="commit-a-version-master-data-services"></a><span data-ttu-id="d320c-102">認可版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d320c-102">Commit a Version (Master Data Services)</span></span>
  <span data-ttu-id="d320c-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，您可認可模型版本，以防止模型成員及其屬性的變更。</span><span class="sxs-lookup"><span data-stu-id="d320c-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], commit a version of a model to prevent changes to the model's members and their attributes.</span></span> <span data-ttu-id="d320c-104">已認可的版本無法解除鎖定。</span><span class="sxs-lookup"><span data-stu-id="d320c-104">Committed versions cannot be unlocked.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d320c-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="d320c-105">Prerequisites</span></span>  
 <span data-ttu-id="d320c-106">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="d320c-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="d320c-107">您必須擁有存取 **[版本管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="d320c-107">You must have permission to access the **Version Management** functional area.</span></span>  
  
-   <span data-ttu-id="d320c-108">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="d320c-108">You must be a model administrator.</span></span> <span data-ttu-id="d320c-109">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d320c-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="d320c-110">版本的狀態必須是 [已鎖定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d320c-110">The version's status must be **Locked**.</span></span> <span data-ttu-id="d320c-111">如需詳細資訊，請參閱 [鎖定版本 &#40;Master Data Services&#41;](../../2014/master-data-services/lock-a-version-master-data-services.md)(管理員 (Master Data Services))。</span><span class="sxs-lookup"><span data-stu-id="d320c-111">For more information, see [Lock a Version &#40;Master Data Services&#41;](../../2014/master-data-services/lock-a-version-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="d320c-112">所有成員必須都已驗證成功。</span><span class="sxs-lookup"><span data-stu-id="d320c-112">All members must have validated successfully.</span></span>  
  
### <a name="to-commit-a-version"></a><span data-ttu-id="d320c-113">若要認可版本</span><span class="sxs-lookup"><span data-stu-id="d320c-113">To commit a version</span></span>  
  
1.  <span data-ttu-id="d320c-114">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[版本管理]**。</span><span class="sxs-lookup"><span data-stu-id="d320c-114">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="d320c-115">在 [管理版本]\*\*\*\* 頁面上，按一下功能表列上的 [驗證版本]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d320c-115">On the **Manage Versions** page, on the menu bar, click **Validate Version**.</span></span>  
  
3.  <span data-ttu-id="d320c-116">在 [驗證版本]\*\*\*\* 頁面上，選取要認可的模型和版本。</span><span class="sxs-lookup"><span data-stu-id="d320c-116">On the **Validate Version** page, select the model and version you want to commit.</span></span>  
  
4.  <span data-ttu-id="d320c-117">按一下 [認可]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d320c-117">Click **Commit**.</span></span>  
  
5.  <span data-ttu-id="d320c-118">在確認對話方塊中按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d320c-118">In the confirmation dialog box, click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d320c-119">後續步驟</span><span class="sxs-lookup"><span data-stu-id="d320c-119">Next Steps</span></span>  
  
-   [<span data-ttu-id="d320c-120">建立版本旗標 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d320c-120">Create a Version Flag &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-version-flag-master-data-services.md)  
  
-   [<span data-ttu-id="d320c-121">將旗標指派給版本 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d320c-121">Assign a Flag to a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/assign-a-flag-to-a-version-master-data-services.md)  
  
-   [<span data-ttu-id="d320c-122">複製版本 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d320c-122">Copy a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/copy-a-version-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="d320c-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d320c-123">See Also</span></span>  
 [<span data-ttu-id="d320c-124">版本 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d320c-124">Versions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/versions-master-data-services.md)  
  
  
