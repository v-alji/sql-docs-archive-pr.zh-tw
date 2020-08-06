---
title: 新增群組 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- groups [Master Data Services], adding
- adding groups [Master Data Services]
ms.assetid: c7a88381-3b2c-4af7-9cf7-3a930c1abdee
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8f9da1d558ccb648af8fbc0dd3b802751bd5ae44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705233"
---
# <a name="add-a-group-master-data-services"></a><span data-ttu-id="9cd98-102">加入群組 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="9cd98-102">Add a Group (Master Data Services)</span></span>
  <span data-ttu-id="9cd98-103">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 的 [群組]\*\*\*\* 清單中加入群組，開始指派 Web 應用程式權限的程序。</span><span class="sxs-lookup"><span data-stu-id="9cd98-103">Add a group to the **Groups** list in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] to begin the process of assigning permission to the Web application.</span></span> <span data-ttu-id="9cd98-104">在群組中的使用者存取 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]之前，您必須提供群組一個或多個功能區域和模型物件的權限。</span><span class="sxs-lookup"><span data-stu-id="9cd98-104">Before a user in the group can access [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], you must give the group permission to one or more functional areas and model objects.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9cd98-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="9cd98-105">Prerequisites</span></span>  
 <span data-ttu-id="9cd98-106">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="9cd98-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="9cd98-107">您必須擁有存取 **[使用者及群組的權限]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="9cd98-107">You must have permission to access the **Users and Group Permissions** functional area.</span></span>  
  
### <a name="to-add-a-group"></a><span data-ttu-id="9cd98-108">若要加入群組</span><span class="sxs-lookup"><span data-stu-id="9cd98-108">To add a group</span></span>  
  
1.  <span data-ttu-id="9cd98-109">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[使用者及群組的權限]**。</span><span class="sxs-lookup"><span data-stu-id="9cd98-109">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **User and Group Permissions**.</span></span>  
  
2.  <span data-ttu-id="9cd98-110">在 [使用者]\*\*\*\* 頁面上，按一下功能表列中的 [管理群組]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9cd98-110">On the **Users** page, from the menu bar, click **Manage Groups**.</span></span>  
  
3.  <span data-ttu-id="9cd98-111">按一下 [加入群組]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9cd98-111">Click **Add groups**.</span></span>  
  
4.  <span data-ttu-id="9cd98-112">輸入群組名稱，並在名稱前面加入 Active Directory 網域名稱或伺服器電腦名稱，如下： *domain\group_name* 或 *computer\group_name*。</span><span class="sxs-lookup"><span data-stu-id="9cd98-112">Type the group's name preceded by the Active Directory domain name or by the server computer's name, as in *domain\group_name* or *computer\group_name*.</span></span>  
  
5.  <span data-ttu-id="9cd98-113">(選擇性) 按一下 **[檢查名稱]**。</span><span class="sxs-lookup"><span data-stu-id="9cd98-113">Optionally, click **Check names**.</span></span>  
  
6.  <span data-ttu-id="9cd98-114">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="9cd98-114">Click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9cd98-115">在使用者第一次存取 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]時，使用者的名稱就會加入至 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 使用者清單。</span><span class="sxs-lookup"><span data-stu-id="9cd98-115">When the user first accesses [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], the user's name is added to the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] list of users.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="9cd98-116">後續步驟</span><span class="sxs-lookup"><span data-stu-id="9cd98-116">Next Steps</span></span>  
  
-   [<span data-ttu-id="9cd98-117">指派功能區域權限 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="9cd98-117">Assign Functional Area Permissions &#40;Master Data Services&#41;</span></span>](assign-functional-area-permissions-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="9cd98-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9cd98-118">See Also</span></span>  
 [<span data-ttu-id="9cd98-119">安全性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="9cd98-119">Security &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/security-master-data-services.md)  
  
  
