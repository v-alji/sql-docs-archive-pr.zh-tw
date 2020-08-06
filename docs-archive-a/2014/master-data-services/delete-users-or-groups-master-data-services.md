---
title: 刪除使用者或群組 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting groups [Master Data Services]
- groups [Master Data Services], deleting
- users [Master Data Services], deleting
- deleting users [Master Data Services]
ms.assetid: 0bbf9d2c-b826-48bb-8aa9-9905db6e717f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: be302bc974994d0f4f17a8e61244065c76fa93ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599547"
---
# <a name="delete-users-or-groups-master-data-services"></a><span data-ttu-id="caf74-102">刪除使用者或群組 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="caf74-102">Delete Users or Groups (Master Data Services)</span></span>
  <span data-ttu-id="caf74-103">當您不再希望使用者或群組存取 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]時，可以刪除他們。</span><span class="sxs-lookup"><span data-stu-id="caf74-103">Delete users or groups when you no longer want them to access [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
 <span data-ttu-id="caf74-104">在刪除使用者和群組時，請注意下列行為：</span><span class="sxs-lookup"><span data-stu-id="caf74-104">Note the following behavior when deleting users and groups:</span></span>  
  
-   <span data-ttu-id="caf74-105">如果刪除有 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]存取權之群組成員的使用者，該使用者仍然可以存取 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ，直到從 Active Directory 或本機群組移除使用者為止。</span><span class="sxs-lookup"><span data-stu-id="caf74-105">If you delete a user who is a member of a group that has access to [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], then the user can still access [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] until you remove the user from the Active Directory or local group.</span></span>  
  
-   <span data-ttu-id="caf74-106">如果刪除群組，群組中已存取 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 的所有使用者都會顯示在 **[使用者]** 清單，直到刪除使用者為止。</span><span class="sxs-lookup"><span data-stu-id="caf74-106">If you delete a group, all users from the group who have accessed [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] are displayed in the **Users** list until you delete them.</span></span>  
  
-   <span data-ttu-id="caf74-107">對安全性的變更不會傳播至 MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] 20 分鐘。</span><span class="sxs-lookup"><span data-stu-id="caf74-107">Changes to security are not propagated to the MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] for 20 minutes.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="caf74-108">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="caf74-108">Prerequisites</span></span>  
 <span data-ttu-id="caf74-109">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="caf74-109">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="caf74-110">您必須擁有存取 **[使用者及群組的權限]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="caf74-110">You must have permission to access the **Users and Group Permissions** functional area.</span></span>  
  
-   <span data-ttu-id="caf74-111">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="caf74-111">You must be a model administrator.</span></span> <span data-ttu-id="caf74-112">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="caf74-112">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-delete-users-or-groups"></a><span data-ttu-id="caf74-113">若要刪除使用者或群組</span><span class="sxs-lookup"><span data-stu-id="caf74-113">To delete users or groups</span></span>  
  
1.  <span data-ttu-id="caf74-114">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[使用者及群組的權限]**。</span><span class="sxs-lookup"><span data-stu-id="caf74-114">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **User and Group Permissions**.</span></span>  
  
2.  <span data-ttu-id="caf74-115">若要刪除使用者，請停留在 **[使用者]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="caf74-115">To delete a user, remain on the **Users** page.</span></span> <span data-ttu-id="caf74-116">若要刪除群組，請按一下功能表列上的 [管理群組]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="caf74-116">To delete a group, from the menu bar, click **ManageGroups.**</span></span>  
  
3.  <span data-ttu-id="caf74-117">在方格中，選取要刪除之使用者或群組的資料列。</span><span class="sxs-lookup"><span data-stu-id="caf74-117">In the grid,select the row for the user or group that you want to delete.</span></span>  
  
4.  <span data-ttu-id="caf74-118">按一下 **[刪除選取的使用者]** 或 **[刪除選取的群組]**。</span><span class="sxs-lookup"><span data-stu-id="caf74-118">Click **Delete selected user** or **Delete selected group**.</span></span>  
  
5.  <span data-ttu-id="caf74-119">在確認對話方塊中按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="caf74-119">On the confirmation dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caf74-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="caf74-120">See Also</span></span>  
 [<span data-ttu-id="caf74-121">安全性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="caf74-121">Security &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/security-master-data-services.md)  
  
  
