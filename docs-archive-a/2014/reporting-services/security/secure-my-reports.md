---
title: 保護我的報表 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- denying My Reports folder access
- private folders [Reporting Services]
- user workspace [Reporting Services]
- security [Reporting Services], My Reports folder
- My Reports folder [Reporting Services]
ms.assetid: 3b23a382-13b8-4196-9a93-7fe62d03a63c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b0a832133852e05c54a80b73fad8a91426840467
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688485"
---
# <a name="secure-my-reports"></a><span data-ttu-id="f916c-102">保護我的報表</span><span class="sxs-lookup"><span data-stu-id="f916c-102">Secure My Reports</span></span>
  <span data-ttu-id="f916c-103">[我的報表] 功能會提供用於報表之使用者管理的工作空間。</span><span class="sxs-lookup"><span data-stu-id="f916c-103">The My Reports feature provides a user-managed workspace for working with reports.</span></span> <span data-ttu-id="f916c-104">為達成其目的，[我的報表] 資料夾的權限，應較一般用途的其他資料夾為寬鬆。</span><span class="sxs-lookup"><span data-stu-id="f916c-104">In order to serve its intended purpose, the My Reports folder requires less restrictive permissions than other folders that are available for general use.</span></span> <span data-ttu-id="f916c-105">使用者如果只有檢視及執行其他資料夾中之報表的權限，則需要一組擴充的權限來管理其 [我的報表] 資料夾和擁有的內容。</span><span class="sxs-lookup"><span data-stu-id="f916c-105">Users who have permissions to only view and run reports in other folders might require an expanded set of permissions to manage their My Reports folders and content that they own.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="f916c-106">提供此用途的特殊角色指派及角色定義。</span><span class="sxs-lookup"><span data-stu-id="f916c-106">provides a specialized role assignment and role definition for this purpose.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f916c-107">只有在報表管理員中，才能使用 [我的報表]。</span><span class="sxs-lookup"><span data-stu-id="f916c-107">My Reports is available only in Report Manager.</span></span> <span data-ttu-id="f916c-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中無法使用它。</span><span class="sxs-lookup"><span data-stu-id="f916c-108">It is not available in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
## <a name="role-assignment-for-my-reports"></a><span data-ttu-id="f916c-109">[我的報表] 的角色指派</span><span class="sxs-lookup"><span data-stu-id="f916c-109">Role Assignment for My Reports</span></span>  
 <span data-ttu-id="f916c-110">[我的報表] 的角色指派有預先設定的元素，而且是為啟用 [我的報表] 資料夾的每一個使用者自動建立的。</span><span class="sxs-lookup"><span data-stu-id="f916c-110">The role assignment for My Reports has preset elements and is automatically created for each user who activates a My Reports folder.</span></span> <span data-ttu-id="f916c-111">讓報表伺服器自動指派安全性，對於廣泛使用 [我的報表] 的組織特別有用，因為管理員不必啟用每個 [我的報表] 使用者的存取權。</span><span class="sxs-lookup"><span data-stu-id="f916c-111">Having the report server automatically assign security is especially useful for organizations that use My Reports widely because administrators do not have to enable access for each My Reports user.</span></span>  
  
 <span data-ttu-id="f916c-112">**我的報表** 角色指派是由下列元素組成：</span><span class="sxs-lookup"><span data-stu-id="f916c-112">A **My Reports** role assignment consists of the following elements:</span></span>  
  
-   <span data-ttu-id="f916c-113">使用者的 [我的報表] 資料夾，位於 [使用者資料夾] [ \\ *\<username>* \My 報告] 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="f916c-113">The user's My Reports folder, which is located in Users Folders\\*\<username>* \My Reports folder.</span></span>  
  
-   <span data-ttu-id="f916c-114">使用者帳戶，會判斷何時啟用 [我的報表] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="f916c-114">The user account, which is determined when the My Reports folder is activated.</span></span> <span data-ttu-id="f916c-115">資料夾是當使用者按一下報表管理員的 [我的報表] 資料夾，或者從報表設計師發行報表至 [我的報表] 資料夾時啟用。</span><span class="sxs-lookup"><span data-stu-id="f916c-115">A folder is activated when a user clicks a My Reports folder in Report Manager or when publishing a report to a My Reports folder from Report Designer.</span></span> <span data-ttu-id="f916c-116">此資料夾也會在使用者要求 [我的報表] 連結的屬性時啟用。</span><span class="sxs-lookup"><span data-stu-id="f916c-116">This folder is also activated when a user requests properties on the My Reports link.</span></span>  
  
-   <span data-ttu-id="f916c-117">[我的報表] 之預先定義的角色定義。</span><span class="sxs-lookup"><span data-stu-id="f916c-117">The predefined role definition for My Reports.</span></span>  
  
## <a name="role-definition-for-my-reports"></a><span data-ttu-id="f916c-118">[我的報表] 的角色定義</span><span class="sxs-lookup"><span data-stu-id="f916c-118">Role Definition for My Reports</span></span>  
 <span data-ttu-id="f916c-119">**我的報表** 角色定義包含支援 [我的報表] 資料夾之內容管理的工作。</span><span class="sxs-lookup"><span data-stu-id="f916c-119">The **My Reports** role definition includes tasks that support content management of a My Reports folder.</span></span> <span data-ttu-id="f916c-120">**我的報表** 角色旨在作為單一用途角色。</span><span class="sxs-lookup"><span data-stu-id="f916c-120">The **My Reports** role is intended to be a single-purpose role.</span></span> <span data-ttu-id="f916c-121">雖然您在任何項目層級的安全性原則中都能選擇此角色，不過應該避免此動作，盡量不要為了配合其他資料夾需求而修改。</span><span class="sxs-lookup"><span data-stu-id="f916c-121">Although you can choose it for any item-level security policy, you should avoid doing so to minimize the chance that you will modify it to accommodate other folder requirements.</span></span> <span data-ttu-id="f916c-122">保留 [我的報表] 功能的 **我的報表** 角色，能夠協助您維護使用者經驗的一致性。</span><span class="sxs-lookup"><span data-stu-id="f916c-122">Reserving the **My Reports** role for the My Reports feature can help you maintain a consistent experience for users.</span></span>  
  
 <span data-ttu-id="f916c-123">依預設，只有報表伺服器管理員能夠修改 **我的報表** 角色。</span><span class="sxs-lookup"><span data-stu-id="f916c-123">By default, only report server administrators modify the **My Reports** role.</span></span> <span data-ttu-id="f916c-124">您可以變更 **我的報表** 角色所包含的工作，以此來自訂角色。</span><span class="sxs-lookup"><span data-stu-id="f916c-124">You can customize the **My Reports** role by changing the tasks it contains.</span></span> <span data-ttu-id="f916c-125">您也可以替代其他角色。</span><span class="sxs-lookup"><span data-stu-id="f916c-125">You can also substitute a different role.</span></span>  
  
## <a name="denying-access-to-my-reports"></a><span data-ttu-id="f916c-126">拒絕存取 [我的報表]</span><span class="sxs-lookup"><span data-stu-id="f916c-126">Denying Access to My Reports</span></span>  
 <span data-ttu-id="f916c-127">您可以禁止使用者存取 [我的報表]，方法是：</span><span class="sxs-lookup"><span data-stu-id="f916c-127">You can prevent users from accessing My Reports by:</span></span>  
  
-   <span data-ttu-id="f916c-128">在 [站台設定] 頁面上停用 [我的報表]。</span><span class="sxs-lookup"><span data-stu-id="f916c-128">Disabling My Reports on the Site Settings page.</span></span> <span data-ttu-id="f916c-129">如需詳細資訊，請參閱 [啟用與停用我的報表](../report-server/enable-and-disable-my-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="f916c-129">For more information, see [Enable and Disable My Reports](../report-server/enable-and-disable-my-reports.md).</span></span>  
  
-   <span data-ttu-id="f916c-130">移除 **我的報表** 角色中的所有工作。</span><span class="sxs-lookup"><span data-stu-id="f916c-130">Removing all tasks from the **My Reports** role.</span></span>  
  
 <span data-ttu-id="f916c-131">當您停用 [我的報表] 時，會從報表管理員移除 [我的報表] 資料夾的連結。</span><span class="sxs-lookup"><span data-stu-id="f916c-131">When you disable My Reports, the link to a My Reports folder is removed from Report Manager.</span></span> <span data-ttu-id="f916c-132">支援 [我的報表] 的基礎資料夾結構 (亦即，[使用者資料夾] 資料夾和子資料夾) 仍然可以使用，而且若使用者知道資料夾路徑，也可以存取。</span><span class="sxs-lookup"><span data-stu-id="f916c-132">The underlying folder structure that supports My Reports (that is, the Users Folders folder and subfolders) is still available and can be accessed if a user knows the folder path.</span></span> <span data-ttu-id="f916c-133">從 **我的報表** 角色移除工作，可確保禁止存取。</span><span class="sxs-lookup"><span data-stu-id="f916c-133">Removing tasks from **My Reports** role ensures that access is prevented.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f916c-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f916c-134">See Also</span></span>  
 <span data-ttu-id="f916c-135">[保護報表和資源的安全](secure-reports-and-resources.md) </span><span class="sxs-lookup"><span data-stu-id="f916c-135">[Secure Reports and Resources](secure-reports-and-resources.md) </span></span>  
 <span data-ttu-id="f916c-136">[保護資料夾的安全](secure-folders.md) </span><span class="sxs-lookup"><span data-stu-id="f916c-136">[Secure Folders](secure-folders.md) </span></span>  
 [<span data-ttu-id="f916c-137">在原生模式報表伺服器上授與權限</span><span class="sxs-lookup"><span data-stu-id="f916c-137">Granting Permissions on a Native Mode Report Server</span></span>](granting-permissions-on-a-native-mode-report-server.md)  
  
  
