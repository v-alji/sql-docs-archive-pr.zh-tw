---
title: 啟用與停用我的報表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- deactivated My Reports folder
- folders [Reporting Services], My Reports
- activated My Reports folder
- My Reports folder [Reporting Services]
- disabling My Reports folder
ms.assetid: 16c76e82-9fd4-417c-9ed3-a7d5bcd1dba2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ef9b48744365b981d11b0e5ae20dc654f2d131d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597583"
---
# <a name="enable-and-disable-my-reports"></a><span data-ttu-id="0e08d-102">啟用與停用我的報表</span><span class="sxs-lookup"><span data-stu-id="0e08d-102">Enable and Disable My Reports</span></span>
  <span data-ttu-id="0e08d-103">[我的報表] 功能會配置報表伺服器資料庫中的個人儲存區，讓使用者能夠將自己的報表儲存在私人資料夾內。</span><span class="sxs-lookup"><span data-stu-id="0e08d-103">The My Reports feature allocates personal storage in the report server database so that users can save reports that they own in a private folder.</span></span> <span data-ttu-id="0e08d-104">身為報表伺服器管理員，您可以啟用或停用此功能，或修改安全性設定 (此設定會控制使用者可以在其工作空間執行哪些動作) 來變更此功能的運作方式。</span><span class="sxs-lookup"><span data-stu-id="0e08d-104">As a report server administrator, you can enable or disable this feature or change how the feature works by modifying the security settings that control what users can do with this workspace.</span></span>  
  
 <span data-ttu-id="0e08d-105">根據預設值，[我的報表] 功能是停用的。</span><span class="sxs-lookup"><span data-stu-id="0e08d-105">The My Reports feature is disabled by default.</span></span> <span data-ttu-id="0e08d-106">您可以針對所有使用者啟用或停用此功能，但無法針對部份使用者啟用此功能。</span><span class="sxs-lookup"><span data-stu-id="0e08d-106">You can either enable or disable the feature for all users, but you cannot enable it for a subset of users.</span></span> <span data-ttu-id="0e08d-107">大多數的使用者和組織都認為此功能很有用；請詳閱此主題稍後所呈現的優點及缺點，以決定此功能是否適合您的組織。</span><span class="sxs-lookup"><span data-stu-id="0e08d-107">Most users and organizations find this feature valuable; study the advantages and disadvantages presented later in this topic to determine whether it is a good fit for your organization.</span></span>  
  
## <a name="how-to-enable-and-disable-my-reports"></a><span data-ttu-id="0e08d-108">如何啟用與停用我的報表</span><span class="sxs-lookup"><span data-stu-id="0e08d-108">How to Enable and Disable My Reports</span></span>  
 <span data-ttu-id="0e08d-109">若要使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]啟用 [我的報表]，連接到報表伺服器執行個體，然後開啟 **[伺服器屬性]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="0e08d-109">To enable My Reports by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the report server instance and open the **Server Properties** page.</span></span> <span data-ttu-id="0e08d-110">接著在 **[一般]** 索引標籤上，選取 **[為每個使用者啟用 [我的報表] 資料夾]** 選項。</span><span class="sxs-lookup"><span data-stu-id="0e08d-110">Then on the **General** tab, select the **Enable a My Reports folder for each user** option.</span></span>  
  
 <span data-ttu-id="0e08d-111">[我的報表] 所使用的角色定義會決定 [我的報表] 工作空間所支援的動作。</span><span class="sxs-lookup"><span data-stu-id="0e08d-111">The role definition used for My Reports determines what actions are supported in the My Reports workspace.</span></span> <span data-ttu-id="0e08d-112">例如，如果「我的報表」角色排除「建立連結報表」，則使用者無法在 [我的報表] 資料夾中建立連結報表。</span><span class="sxs-lookup"><span data-stu-id="0e08d-112">For example, if the My Reports role excludes "Create linked reports," users cannot create linked reports in the My Reports folders.</span></span> <span data-ttu-id="0e08d-113">如需詳細資訊，請參閱 [保護我的報表](../security/secure-my-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="0e08d-113">For more information, see [Secure My Reports](../security/secure-my-reports.md).</span></span>  
  
 <span data-ttu-id="0e08d-114">若要停用 [我的報表]，清除 **[為每個使用者啟用 [我的報表] 資料夾]** 。</span><span class="sxs-lookup"><span data-stu-id="0e08d-114">To deactivate My Reports, clear **Enable a My Reports folder for each user**.</span></span> <span data-ttu-id="0e08d-115">停用「我的報表」之後，將會移除所有與 [我的報表] 資料夾相關的可見項目。</span><span class="sxs-lookup"><span data-stu-id="0e08d-115">Deactivating My Reports removes for users all visible indications of the My Reports folder.</span></span> <span data-ttu-id="0e08d-116">停用此功能之後，必須手動移除實際用於儲存的資料夾 (亦即 [使用者資料夾] 中的子資料夾)。</span><span class="sxs-lookup"><span data-stu-id="0e08d-116">The folders that provide actual storage (that is, the subfolders in Users Folders) must be deleted manually once the feature is disabled.</span></span>  
  
### <a name="when-my-reports-is-activated"></a><span data-ttu-id="0e08d-117">當啟動 [我的報表] 時</span><span class="sxs-lookup"><span data-stu-id="0e08d-117">When My Reports Is Activated</span></span>  
 <span data-ttu-id="0e08d-118">當此功能啟動時，使用者可以在根資料夾 (主資料夾) 中看到 [我的報表] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0e08d-118">Once the feature is activated, users see a My Reports folder located under the root folder, Home.</span></span> <span data-ttu-id="0e08d-119">除了 [我的報表] 資料夾以外，報表伺服器管理員也可以看到包含每位使用者子資料夾的 [使用者資料夾] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0e08d-119">In addition to a My Reports folder, report server administrators also see a Users Folders folder that contains the subfolder for each user.</span></span>  
  
 <span data-ttu-id="0e08d-120">此功能啟動期間，將無法刪除 [使用者資料夾] 及其子資料夾。</span><span class="sxs-lookup"><span data-stu-id="0e08d-120">While the feature is activated, Users Folders and its subfolders cannot be deleted.</span></span> <span data-ttu-id="0e08d-121">此外，[我的報表] 名稱將成為根節點 (主資料夾) 之下的資料夾保留名稱。</span><span class="sxs-lookup"><span data-stu-id="0e08d-121">Furthermore, the name "My Reports" becomes a reserved name for folders created under the root node (Home).</span></span>  
  
 <span data-ttu-id="0e08d-122">若您在停用 [我的報表] 之後重新啟動該功能，如果 [使用者資料夾] 資料夾不存在，報表伺服器就會建立一個新的 [使用者資料夾] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0e08d-122">If you activate My Reports after it has been deactivated, the report server creates a new Users Folders folder if one does not already exist.</span></span> <span data-ttu-id="0e08d-123">如果 [使用者資料夾] 已經存在，報表伺服器會在使用者登入其 [我的報表] 資料夾時建立新的子資料夾。</span><span class="sxs-lookup"><span data-stu-id="0e08d-123">If Users Folders exists, the report server adds new subfolders as users log on to their My Reports folders.</span></span>  
  
### <a name="when-my-reports-is-deactivated"></a><span data-ttu-id="0e08d-124">當停用 [我的報表] 時</span><span class="sxs-lookup"><span data-stu-id="0e08d-124">When My Reports Is Deactivated</span></span>  
 <span data-ttu-id="0e08d-125">當此功能停用時，[我的報表] 名稱將不再保留；使用者可以在 [主資料夾] 資料夾之下建立名為 [我的報表] 的個人資料夾。</span><span class="sxs-lookup"><span data-stu-id="0e08d-125">Once the feature is deactivated, the name "My Reports" is no longer reserved; users can create a personal folder named My Reports under the Home folder.</span></span> <span data-ttu-id="0e08d-126">此外，將無法再重新導向我的報表至使用者特定之 [我的報表] 子資料夾。</span><span class="sxs-lookup"><span data-stu-id="0e08d-126">In addition, redirection from My Reports to user-specific My Reports subfolders is no longer performed.</span></span> <span data-ttu-id="0e08d-127">最後，任何包含使用者特定之 [我的報表] 子資料夾的報表連結 URL 位址，將無法正常運作。</span><span class="sxs-lookup"><span data-stu-id="0e08d-127">Lastly, any report links that include a user-specific My Reports folder in the URL address will no longer work.</span></span>  
  
## <a name="choosing-to-use-my-reports"></a><span data-ttu-id="0e08d-128">選擇使用 [我的報表]</span><span class="sxs-lookup"><span data-stu-id="0e08d-128">Choosing to Use My Reports</span></span>  
 <span data-ttu-id="0e08d-129">是否使用 [我的報表]，取決於您是否想要有專屬的伺服器資源，來支援使用者工作空間。</span><span class="sxs-lookup"><span data-stu-id="0e08d-129">Deciding whether to use My Reports depends on whether you want to dedicate server resources to support a user workspace.</span></span> <span data-ttu-id="0e08d-130">[我的報表] 具有強大的功能，可以讓使用者掌控資訊資源，以協助他們完成工作。</span><span class="sxs-lookup"><span data-stu-id="0e08d-130">My Reports is a powerful feature that allows users to have control over information resources that help them do their jobs.</span></span> <span data-ttu-id="0e08d-131">它也提供使用者特殊的報表使用方式。</span><span class="sxs-lookup"><span data-stu-id="0e08d-131">It also provides a way for users to work with reports that are not intended for general use.</span></span> <span data-ttu-id="0e08d-132">使用 [我的報表] 的重要原因之一，是它可以提供安全、易於管理的支援，給需要撰寫及檢視報表的使用者群組。</span><span class="sxs-lookup"><span data-stu-id="0e08d-132">One of the most compelling reasons to use My Reports is that it provides secure, manageable support for the segment of users who need to author and review reports.</span></span> <span data-ttu-id="0e08d-133">若無此功能，您可能會需要經常為不同的使用者，建立特定的資料夾和安全性原則。</span><span class="sxs-lookup"><span data-stu-id="0e08d-133">Without this feature, you may find yourself creating folders and security policies for various users on an ad hoc basis.</span></span> <span data-ttu-id="0e08d-134">隨著使用者及使用者需求的變更，此方式會使資料夾和原則數量隨著時間而增加，因而難以維護。</span><span class="sxs-lookup"><span data-stu-id="0e08d-134">As users and user needs change, this approach results in ever-increasing numbers of folders and policies that are difficult to maintain over time.</span></span>  
  
 <span data-ttu-id="0e08d-135">請注意，若您啟用「我的報表」，當網域帳戶的使用者按下 [我的報表] 連結時，報表伺服器就會為每一位使用者建立 [我的報表] 資料夾，即使使用者不想要或不需要 [我的報表] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0e08d-135">Note that if you do activate My Reports, the report server creates a My Reports folder for every user with a domain account who clicks the My Reports link, even if the user does not want or need a My Reports folder.</span></span> <span data-ttu-id="0e08d-136">目前沒有可判斷哪些資料夾正在使用的有效方法。</span><span class="sxs-lookup"><span data-stu-id="0e08d-136">There is no systematic way to determine which folders are being used.</span></span> <span data-ttu-id="0e08d-137">您必須手動檢視資料夾，以查看其中是否包含任何資料。</span><span class="sxs-lookup"><span data-stu-id="0e08d-137">You must review the folders manually to see whether they contain anything.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e08d-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e08d-138">See Also</span></span>  
 <span data-ttu-id="0e08d-139">[保護我的報表](../security/secure-my-reports.md) </span><span class="sxs-lookup"><span data-stu-id="0e08d-139">[Secure My Reports](../security/secure-my-reports.md) </span></span>  
 [<span data-ttu-id="0e08d-140">報表伺服器內容管理 &#40;SSRS 原生模式&#41;</span><span class="sxs-lookup"><span data-stu-id="0e08d-140">Report Server Content Management &#40;SSRS Native Mode&#41;</span></span>](report-server-content-management-ssrs-native-mode.md)  
  
  
