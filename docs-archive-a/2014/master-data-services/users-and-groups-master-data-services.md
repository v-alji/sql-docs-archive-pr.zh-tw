---
title: 使用者和群組 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- users [Master Data Services]
- groups [Master Data Services]
- users [Master Data Services], about users
- groups [Master Data Services], about groups
ms.assetid: ed08dd2d-248e-4b68-91d4-e9961cb50eed
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: efad65bf273d58b4f60b98d050a8b99705cb00ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710685"
---
# <a name="users-and-groups-master-data-services"></a><span data-ttu-id="dac5b-102">使用者和群組 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="dac5b-102">Users and Groups (Master Data Services)</span></span>
  <span data-ttu-id="dac5b-103">若要存取 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 應用程式，使用者必須擁有 Windows 網域帳戶或安裝 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 之伺服器電腦上的帳戶。</span><span class="sxs-lookup"><span data-stu-id="dac5b-103">To access the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application a user must have a Windows domain account or an account on the server computer where [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] is installed.</span></span> <span data-ttu-id="dac5b-104">若要授與 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 存取權，您可以執行下列其中一項作業：</span><span class="sxs-lookup"><span data-stu-id="dac5b-104">To grant access to [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] you can either:</span></span>  
  
-   <span data-ttu-id="dac5b-105">將使用者帳戶新增至網域或本機群組，然後將群組新增至 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]的群組清單。</span><span class="sxs-lookup"><span data-stu-id="dac5b-105">Add the user account to a domain or local group and then add the group to the list of groups in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
-   <span data-ttu-id="dac5b-106">將使用者帳戶新增至 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]的使用者清單。</span><span class="sxs-lookup"><span data-stu-id="dac5b-106">Add the user account to the list of users in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dac5b-107">如果使用者屬於可存取 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]的群組，則在第一次存取 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 或 MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]時，使用者的名稱會自動新增至使用者清單。</span><span class="sxs-lookup"><span data-stu-id="dac5b-107">When a user belongs to a group that has access to [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], the user's name is automatically added to the list of users the first time the user accesses [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] or the MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].</span></span>  
  
 <span data-ttu-id="dac5b-108">若要在 UI 的 [總管]\*\*\*\* 功能區域內執行動作，群組或使用者必須獲得指派 [總管]\*\*\*\* 功能區域存取權以及模型物件權限。</span><span class="sxs-lookup"><span data-stu-id="dac5b-108">To take action within the **Explorer** functional area of the UI, the group or user must be assigned access to the **Explorer** functional area and assigned permission to model objects.</span></span>  
  
 <span data-ttu-id="dac5b-109">如果使用者或群組需要存取其他功能區域，使用者或群組必須是管理員。</span><span class="sxs-lookup"><span data-stu-id="dac5b-109">If a user or group needs access to other functional areas, the user or group must be an administrator.</span></span> <span data-ttu-id="dac5b-110">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="dac5b-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
## <a name="best-practice"></a><span data-ttu-id="dac5b-111">最佳做法</span><span class="sxs-lookup"><span data-stu-id="dac5b-111">Best Practice</span></span>  
 <span data-ttu-id="dac5b-112">若要簡化管理，請建立群組，然後指派每個群組的功能區域和模型物件權限。</span><span class="sxs-lookup"><span data-stu-id="dac5b-112">To simplify administration, create groups and assign each group permission to functional areas and model objects.</span></span> <span data-ttu-id="dac5b-113">您即可在群組中新增及移除使用者，而不需存取 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] UI。</span><span class="sxs-lookup"><span data-stu-id="dac5b-113">You can then add and remove users from the groups without accessing the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] UI.</span></span>  
  
 <span data-ttu-id="dac5b-114">請勿指派其他權限給個別使用者，也不要在具有 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]存取權的多個群組中加入使用者。</span><span class="sxs-lookup"><span data-stu-id="dac5b-114">Do not assign additional permissions to an individual user, and do not include a user in multiple groups that have access to [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span> <span data-ttu-id="dac5b-115">此外，除非您希望群組擁有特定成員的受限存取權，否則請勿使用階層成員權限。</span><span class="sxs-lookup"><span data-stu-id="dac5b-115">In addition, do not use hierarchy member permissions unless you want a group to have limited access to specific members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dac5b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dac5b-116">See Also</span></span>  
 <span data-ttu-id="dac5b-117">[新增使用者 &#40;Master Data Services&#41;](../../2014/master-data-services/add-a-user-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="dac5b-117">[Add a User &#40;Master Data Services&#41;](../../2014/master-data-services/add-a-user-master-data-services.md) </span></span>  
 <span data-ttu-id="dac5b-118">[新增群組 &#40;Master Data Services&#41;](../../2014/master-data-services/add-a-group-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="dac5b-118">[Add a Group &#40;Master Data Services&#41;](../../2014/master-data-services/add-a-group-master-data-services.md) </span></span>  
 <span data-ttu-id="dac5b-119">[刪除 &#40;Master Data Services&#41;的使用者或群組](../../2014/master-data-services/delete-users-or-groups-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="dac5b-119">[Delete Users or Groups &#40;Master Data Services&#41;](../../2014/master-data-services/delete-users-or-groups-master-data-services.md) </span></span>  
 [<span data-ttu-id="dac5b-120">測試使用者的權限 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="dac5b-120">Test a User's Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/test-a-user-s-permissions-master-data-services.md)  
  
  
