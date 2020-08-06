---
title: 根據商務規則驗證版本 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- validating versions [Master Data Services]
- validating versions [Master Data Services], about validating versions
- versions [Master Data Services], validating
- business rules [Master Data Services], applying to all members
ms.assetid: 5aee7901-6d05-41d4-8bbb-c6f26791d1df
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 085fa071ca511c9d838c140547419bf87fb857bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595160"
---
# <a name="validate-a-version-against-business-rules-master-data-services"></a><span data-ttu-id="56bea-102">根據商務規則驗證版本 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="56bea-102">Validate a Version against Business Rules (Master Data Services)</span></span>
  <span data-ttu-id="56bea-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，驗證版本，以便將商務規則套用到模型版本中的所有成員。</span><span class="sxs-lookup"><span data-stu-id="56bea-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], validate a version to apply business rules to all members in the model version.</span></span>  
  
 <span data-ttu-id="56bea-104">此程序說明如何使用 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 應用程式來驗證資料。</span><span class="sxs-lookup"><span data-stu-id="56bea-104">This procedure explains how to use the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application to validate data.</span></span> <span data-ttu-id="56bea-105">如果您具有 MDS 資料庫的權限，則可以改用預存程序。</span><span class="sxs-lookup"><span data-stu-id="56bea-105">If you have permission in the MDS database, you can use a stored procedure instead.</span></span> <span data-ttu-id="56bea-106">如需詳細資訊，請參閱 [驗證預存程序 &#40;Master Data Services&#41;](validation-stored-procedure-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="56bea-106">For more information, see [Validation Stored Procedure &#40;Master Data Services&#41;](validation-stored-procedure-master-data-services.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="56bea-107">所有成員都必須通過驗證之後，才能認可版本。</span><span class="sxs-lookup"><span data-stu-id="56bea-107">All members must pass validation before a version can be committed.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="56bea-108">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="56bea-108">Prerequisites</span></span>  
 <span data-ttu-id="56bea-109">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="56bea-109">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="56bea-110">您必須擁有存取 **[版本管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="56bea-110">You must have permission to access the **Version Management** functional area.</span></span>  
  
-   <span data-ttu-id="56bea-111">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="56bea-111">You must be a model administrator.</span></span> <span data-ttu-id="56bea-112">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="56bea-112">For more information, see [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="56bea-113">版本的狀態必須是 [開啟]\*\*\*\* 或 [已鎖定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="56bea-113">The version's status must be **Open** or **Locked**.</span></span>  
  
-   <span data-ttu-id="56bea-114">在 [驗證版本]\*\*\*\* 頁面上，成員必須存在，且其狀態不得為 [驗證成功]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="56bea-114">On the **Validate Versions** page, members must exist with a status other than **Validation succeeded**.</span></span>  
  
### <a name="to-validate-a-version"></a><span data-ttu-id="56bea-115">若要驗證版本</span><span class="sxs-lookup"><span data-stu-id="56bea-115">To validate a version</span></span>  
  
1.  <span data-ttu-id="56bea-116">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[版本管理]**。</span><span class="sxs-lookup"><span data-stu-id="56bea-116">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="56bea-117">在 [管理版本]\*\*\*\* 頁面上，按一下功能表列上的 [驗證版本]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="56bea-117">On the **Manage Versions** page, from the menu bar, click **Validate Version**.</span></span>  
  
3.  <span data-ttu-id="56bea-118">在 [驗證版本]\*\*\*\* 頁面上，選取要驗證的模型和版本。</span><span class="sxs-lookup"><span data-stu-id="56bea-118">On the **Validate Versions** page, select the model and version you want to validate.</span></span>  
  
4.  <span data-ttu-id="56bea-119">按一下 **[驗證]** 。</span><span class="sxs-lookup"><span data-stu-id="56bea-119">Click **Validate**.</span></span>  
  
5.  <span data-ttu-id="56bea-120">在確認對話方塊中按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="56bea-120">In the confirmation dialog box, click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="56bea-121">不再顯示進度指標時，表示版本已完成驗證。</span><span class="sxs-lookup"><span data-stu-id="56bea-121">When the progress indicator is no longer displayed, the version has finished validation.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="56bea-122">後續步驟</span><span class="sxs-lookup"><span data-stu-id="56bea-122">Next Steps</span></span>  
  
-   [<span data-ttu-id="56bea-123">鎖定版本 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="56bea-123">Lock a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/lock-a-version-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="56bea-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56bea-124">See Also</span></span>  
 <span data-ttu-id="56bea-125">[驗證狀態 &#40;Master Data Services&#41;](../../2014/master-data-services/validation-statuses-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="56bea-125">[Validation Statuses &#40;Master Data Services&#41;](../../2014/master-data-services/validation-statuses-master-data-services.md) </span></span>  
 <span data-ttu-id="56bea-126">[驗證預存程式 &#40;Master Data Services&#41;](validation-stored-procedure-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="56bea-126">[Validation Stored Procedure &#40;Master Data Services&#41;](validation-stored-procedure-master-data-services.md) </span></span>  
 <span data-ttu-id="56bea-127">[版本 &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="56bea-127">[Versions &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md) </span></span>  
 <span data-ttu-id="56bea-128">[商務規則 &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="56bea-128">[Business Rules &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md) </span></span>  
 [<span data-ttu-id="56bea-129">根據商務規則驗證特定成員 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="56bea-129">Validate Specific Members against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
  
