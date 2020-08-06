---
title: 設定 SharePoint 網站上報表伺服器專案的許可權 (SharePoint 整合模式中的 Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- permissions [Reporting Services], SharePoint integrated mode
- SharePoint integration [Reporting Services], permissions
ms.assetid: 2467c657-a3bf-4ec3-a88c-8877df19823d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f38497843ca99342f13952153d7fed957564e006
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688481"
---
# <a name="set-permissions-for-report-server-items-on-a-sharepoint-site-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="2eacf-102">設定 SharePoint 網站上報表伺服器項目的權限 (SharePoint 整合模式的 Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="2eacf-102">Set Permissions for Report Server Items on a SharePoint Site (Reporting Services in SharePoint Integrated Mode)</span></span>
  <span data-ttu-id="2eacf-103">如果預設安全性設定無法提供所需的存取層級，您可以建立新的權限等級，以便提供特定報表伺服器項目或作業的存取權。</span><span class="sxs-lookup"><span data-stu-id="2eacf-103">If default security settings do not provide the level of access that you require, you can create new permission levels to provide access to specific report server items or operations.</span></span> <span data-ttu-id="2eacf-104">如果您想要限制特定報表的存取權，自訂安全性設定就很有用。</span><span class="sxs-lookup"><span data-stu-id="2eacf-104">Custom security settings can be useful if you want to restrict access to a particular report.</span></span>  
  
 <span data-ttu-id="2eacf-105">您必須是網站擁有者才能建立權限等級和群組。</span><span class="sxs-lookup"><span data-stu-id="2eacf-105">You must be a site owner to create permission levels and groups.</span></span> <span data-ttu-id="2eacf-106">權限等級適用於網站全域。</span><span class="sxs-lookup"><span data-stu-id="2eacf-106">Permission levels are used globally throughout a site.</span></span> <span data-ttu-id="2eacf-107">如果您建立新的權限等級，其他網站擁有者都可以使用該權限等級。</span><span class="sxs-lookup"><span data-stu-id="2eacf-107">If you create a new permission level, it will be available to other site owners.</span></span>  
  
 <span data-ttu-id="2eacf-108">大部分權限是繼承自上層網站。</span><span class="sxs-lookup"><span data-stu-id="2eacf-108">Most permissions are inherited from a parent site.</span></span> <span data-ttu-id="2eacf-109">如果您為特定文件庫或項目指派權限，就會中斷權限繼承，並且在網站階層中該分支的權限管理方面產生額外的負擔。</span><span class="sxs-lookup"><span data-stu-id="2eacf-109">If you assign permissions on a specific library or item, you break permission inheritance and incur additional overhead in how manage permissions for that branch of your site hierarchy.</span></span>  
  
 <span data-ttu-id="2eacf-110">您還可以在報表定義 (.rdl)、模型 (.smdl) 及共用資料來源 (.rsds) 檔上設定權限。</span><span class="sxs-lookup"><span data-stu-id="2eacf-110">You can set permissions on report definition (.rdl), model (.smdl), and shared data source (.rsds) files.</span></span> <span data-ttu-id="2eacf-111">不過您無法組合相同項目上的繼承和管理權限。</span><span class="sxs-lookup"><span data-stu-id="2eacf-111">You cannot combine inherited and managed permissions on the same item.</span></span> <span data-ttu-id="2eacf-112">如果您選擇直接管理權限，則繼承權限對於目前項目將不會有作用。</span><span class="sxs-lookup"><span data-stu-id="2eacf-112">If you choose to manage permissions directly, inherited permissions will have no effect on the current item.</span></span> <span data-ttu-id="2eacf-113">如果之後要恢復權限繼承，您可以在 **[動作]** 功能表上選取 **[繼承權限]** 。</span><span class="sxs-lookup"><span data-stu-id="2eacf-113">If you want to resume permission inheritance later, you can select **Inherit Permissions** on the **Actions** menu.</span></span>  
  
 <span data-ttu-id="2eacf-114">若要設定模型中實體和檢視方塊的權限，您必須具有該模型的「完整控制權」權限等級。</span><span class="sxs-lookup"><span data-stu-id="2eacf-114">To set permissions on entities and perspectives in a model, you must have Full Control level of permission for the model.</span></span> <span data-ttu-id="2eacf-115">「完整控制權」包括「管理權限」，這個網站層級權限會授與具有「完整控制權」權限等級的網站擁有者和其他 SharePoint 群組。</span><span class="sxs-lookup"><span data-stu-id="2eacf-115">Full Control includes "Manage Permissions", which is a site level permission that is granted to site owners and other SharePoint groups who have Full Control level of permission.</span></span> <span data-ttu-id="2eacf-116">如果要提供設定模型項目安全性的功能給特定使用者，就必須中斷權限繼承，並針對模型檔授與使用者或群組更高的權限 (例如「完整控制權」)。</span><span class="sxs-lookup"><span data-stu-id="2eacf-116">If you want to offer specific users the ability to set model item security, you must break permission inheritance and grant elevated permissions (such as Full Control) to the user or group on the model file.</span></span> <span data-ttu-id="2eacf-117">當您針對文件庫中的項目 (例如檔案) 授與「完整控制權」時，這些權限的範圍僅限於該項目，不會擴充至父代或相同文件庫中的其他項目。</span><span class="sxs-lookup"><span data-stu-id="2eacf-117">When you grant Full Control on an item such as a file in the library, the permissions are scoped to that item and do not extend to the parent or to other items within the same library.</span></span> <span data-ttu-id="2eacf-118">在使用者具有模型的「管理權限」之後，該使用者就可以透過 SharePoint 網站或模型設計師使用設定模型項目安全性。</span><span class="sxs-lookup"><span data-stu-id="2eacf-118">After the user has Manage Permissions permission on the model, he or she can use set model item security via the SharePoint site or Model Designer.</span></span>  
  
### <a name="to-set-permissions-on-an-individual-report-model-or-data-source"></a><span data-ttu-id="2eacf-119">設定個別報表、模型或資料來源的權限</span><span class="sxs-lookup"><span data-stu-id="2eacf-119">To set permissions on an individual report, model, or data source</span></span>  
  
1.  <span data-ttu-id="2eacf-120">如果尚未開啟文件庫，請按一下 [快速啟動] 上的文件庫名稱。</span><span class="sxs-lookup"><span data-stu-id="2eacf-120">If the library is not already open, click its name on the Quick Launch.</span></span> <span data-ttu-id="2eacf-121">如果找不到您的文件庫名稱，請先按一下 **[檢視所有網站內容]** ，然後再按一下文件庫名稱。</span><span class="sxs-lookup"><span data-stu-id="2eacf-121">If the name of your library does not appear, click **View All Site Content**, and then click the name of your library.</span></span>  
  
2.  <span data-ttu-id="2eacf-122">指向報表、報表模型或共用資料來源檔。</span><span class="sxs-lookup"><span data-stu-id="2eacf-122">Point to the report, report model, or shared data source file.</span></span>  
  
3.  <span data-ttu-id="2eacf-123">按一下向下箭頭，然後在功能表上按一下 **[管理權限]** 。</span><span class="sxs-lookup"><span data-stu-id="2eacf-123">Click the down arrow, and on the menu, click **Manage Permissions**.</span></span>  
  
4.  <span data-ttu-id="2eacf-124">在 **[動作]** 功能表上，按一下 **[編輯權限]** ，然後按一下 **[確定]** 確認該動作。</span><span class="sxs-lookup"><span data-stu-id="2eacf-124">On the **Actions** menu, click **Edit Permissions**, and then click **OK** to confirm the action.</span></span>  
  
5.  <span data-ttu-id="2eacf-125">若要將權限授與尚未具備該檔案使用權限的使用者或群組，請按一下 **[新增]** ，然後按一下 **[加入使用者]** 。</span><span class="sxs-lookup"><span data-stu-id="2eacf-125">To give permissions to a user or group that does not yet have permissions to use the file, click **New**, and then click **Add Users**.</span></span>  
  
6.  <span data-ttu-id="2eacf-126">若要移除或修改現有使用者或群組的權限，請按一下使用者或群組旁的核取方塊，並按一下 **[動作]** ，然後按一下 **[移除使用者權限]** 或 **[編輯使用者權限]** 。</span><span class="sxs-lookup"><span data-stu-id="2eacf-126">To remove or modify permissions for an existing user or group, click the check box next to the user or group, click **Actions**, and then click **Remove User Permissions** or **Edit User Permissions**.</span></span>  
  
### <a name="to-set-permissions-that-enable-model-item-security"></a><span data-ttu-id="2eacf-127">設定啟用模型項目安全性的權限</span><span class="sxs-lookup"><span data-stu-id="2eacf-127">To set permissions that enable model item security</span></span>  
  
1.  <span data-ttu-id="2eacf-128">使用在網站上具有「管理權限」的帳戶，登入 SharePoint 網站。</span><span class="sxs-lookup"><span data-stu-id="2eacf-128">Log in to the SharePoint site using an account that has Manage Permissions permission on the site.</span></span>  
  
2.  <span data-ttu-id="2eacf-129">開啟包含模型的文件庫。</span><span class="sxs-lookup"><span data-stu-id="2eacf-129">Open the library that contains the model.</span></span>  
  
3.  <span data-ttu-id="2eacf-130">指向模型。</span><span class="sxs-lookup"><span data-stu-id="2eacf-130">Point to the model.</span></span>  
  
4.  <span data-ttu-id="2eacf-131">按一下模型旁的向下箭頭，然後按一下 **[管理權限]** 。</span><span class="sxs-lookup"><span data-stu-id="2eacf-131">Click the down arrow next to the model, and click **Manage Permissions**.</span></span>  
  
5.  <span data-ttu-id="2eacf-132">按一下 **[動作]** 。</span><span class="sxs-lookup"><span data-stu-id="2eacf-132">Click **Actions**.</span></span>  
  
6.  <span data-ttu-id="2eacf-133">按一下 **[編輯權限]** 。</span><span class="sxs-lookup"><span data-stu-id="2eacf-133">Click **Edit Permissions**.</span></span> <span data-ttu-id="2eacf-134">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="2eacf-134">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="2eacf-135">按一下 **[新增]** 。</span><span class="sxs-lookup"><span data-stu-id="2eacf-135">Click **New**.</span></span>  
  
8.  <span data-ttu-id="2eacf-136">按一下 [加入使用者]  。</span><span class="sxs-lookup"><span data-stu-id="2eacf-136">Click **Add Users**.</span></span>  
  
9. <span data-ttu-id="2eacf-137">在 [使用者/群組] 中，輸入使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="2eacf-137">In Users/Groups, enter the user account.</span></span>  
  
10. <span data-ttu-id="2eacf-138">選取 **[直接授與使用者權限]** 。</span><span class="sxs-lookup"><span data-stu-id="2eacf-138">Select **Give users permission directly**.</span></span>  
  
11. <span data-ttu-id="2eacf-139">按一下 **[完整控制權]** 。</span><span class="sxs-lookup"><span data-stu-id="2eacf-139">Click **Full Control**.</span></span>  
  
12. <span data-ttu-id="2eacf-140">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="2eacf-140">Click **OK**.</span></span> <span data-ttu-id="2eacf-141">使用者一旦具有管理特定模型權限的能力，就可以開啟該模型，編輯該模型內的權限。</span><span class="sxs-lookup"><span data-stu-id="2eacf-141">Once a user has the ability to manage permissions for a specific model, he or she can open the model to edit permissions within the model.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2eacf-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2eacf-142">See Also</span></span>  
 <span data-ttu-id="2eacf-143">[在 Windows SharePoint Services 中使用報表伺服器項目的內建安全性](use-built-in-security-in-windows-sharepoint-services-for-report-server-items.md) </span><span class="sxs-lookup"><span data-stu-id="2eacf-143">[Use Built-in Security in Windows SharePoint Services for Report Server Items](use-built-in-security-in-windows-sharepoint-services-for-report-server-items.md) </span></span>  
 <span data-ttu-id="2eacf-144">[設定 SharePoint Web 應用程式中報表伺服器作業的權限](set-permissions-for-report-server-operations-in-a-sharepoint-web-application.md) </span><span class="sxs-lookup"><span data-stu-id="2eacf-144">[Set Permissions for Report Server Operations in a SharePoint Web Application](set-permissions-for-report-server-operations-in-a-sharepoint-web-application.md) </span></span>  
 <span data-ttu-id="2eacf-145">[將 Reporting Services 中的角色和工作與 SharePoint 群組和權限做比較](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="2eacf-145">[Compare Roles and Tasks in Reporting Services to SharePoint Groups and Permissions](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md) </span></span>  
 <span data-ttu-id="2eacf-146">[報表伺服器項目的 SharePoint 網站和清單權限參考](sharepoint-site-and-list-permission-reference-for-report-server-items.md) </span><span class="sxs-lookup"><span data-stu-id="2eacf-146">[SharePoint Site and List Permission Reference for Report Server Items](sharepoint-site-and-list-permission-reference-for-report-server-items.md) </span></span>  
 [<span data-ttu-id="2eacf-147">授與 SharePoint 網站上報表伺服器項目的權限</span><span class="sxs-lookup"><span data-stu-id="2eacf-147">Granting Permissions on Report Server Items on a SharePoint Site</span></span>](granting-permissions-on-report-server-items-on-a-sharepoint-site.md)  
  
  
