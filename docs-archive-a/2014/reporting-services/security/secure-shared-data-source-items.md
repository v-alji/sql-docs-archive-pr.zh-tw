---
title: 保護共用資料來源項目的安全 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- shared data sources [Reporting Services]
- data sources [Reporting Services], shared
- security [Reporting Services], data sources
ms.assetid: 7299e498-0a1a-4821-a22a-5199bb773ce0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c4177834a90e2852f4079e3b2bf5a1dd85b9cd51
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596474"
---
# <a name="secure-shared-data-source-items"></a><span data-ttu-id="fbf8b-102">保護共用資料來源項目的安全</span><span class="sxs-lookup"><span data-stu-id="fbf8b-102">Secure Shared Data Source Items</span></span>
  <span data-ttu-id="fbf8b-103">您可以在共用資料來源項目上設定安全性，以啟用或停用它的存取權。</span><span class="sxs-lookup"><span data-stu-id="fbf8b-103">You can set security on a shared data source item to enable or disable access to it.</span></span>  
  
 <span data-ttu-id="fbf8b-104">對共用資料來源有最小存取權的使用者 (例如，透過**瀏覽器**角色授與的存取權)，只要也得到檢視報表本身的授權，就可以檢視使用項目的報表清單。</span><span class="sxs-lookup"><span data-stu-id="fbf8b-104">A user who has minimal access to a shared data source (for example, the access granted through the **Browser** role) can view the list of reports that use the item, provided the user is also authorized to view the reports themselves.</span></span>  
  
 <span data-ttu-id="fbf8b-105">擁有更多存取權 (例如，透過**內容管理員**角色授與) 的使用者，可以檢視和設定共用資料來源的屬性。</span><span class="sxs-lookup"><span data-stu-id="fbf8b-105">A user who has additional access (such as that granted through the **Content Manager** role) can view and set properties for the shared data source.</span></span>  
  
 <span data-ttu-id="fbf8b-106">若要設定安全性，您可以建立角色指派來指定哪些使用者或群組帳戶可以存取共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="fbf8b-106">To set security, you create a role assignment that specifies which user or group account has access to the shared data source.</span></span> <span data-ttu-id="fbf8b-107">擁有共用資料項目之存取權的使用者可以變更它的名稱、描述、連接字串或認證資訊。</span><span class="sxs-lookup"><span data-stu-id="fbf8b-107">Users who have access to a shared data source item can change its name, description, connection string, or credential information.</span></span>  
  
## <a name="tasks-and-access-to-items"></a><span data-ttu-id="fbf8b-108">工作與項目的存取</span><span class="sxs-lookup"><span data-stu-id="fbf8b-108">Tasks and Access to Items</span></span>  
 <span data-ttu-id="fbf8b-109">建立角色指派時，使用擁有這些工作的角色，以指定適當的權限給使用者和群組。</span><span class="sxs-lookup"><span data-stu-id="fbf8b-109">When creating role assignments, use a role that has these tasks to assign appropriate permissions to users and groups.</span></span>  
  
|<span data-ttu-id="fbf8b-110">選取的工作</span><span class="sxs-lookup"><span data-stu-id="fbf8b-110">Select this task</span></span>|<span data-ttu-id="fbf8b-111">授與的權限</span><span class="sxs-lookup"><span data-stu-id="fbf8b-111">To give users permission to</span></span>|  
|----------------------|---------------------------------|  
|<span data-ttu-id="fbf8b-112">檢視資料來源</span><span class="sxs-lookup"><span data-stu-id="fbf8b-112">View data sources</span></span>|<span data-ttu-id="fbf8b-113">檢視資料夾階層中的共用資料來源項目。</span><span class="sxs-lookup"><span data-stu-id="fbf8b-113">View the shared data source item in the folder hierarchy.</span></span> <span data-ttu-id="fbf8b-114">如果沒有此工作，使用者看不到項目，也許不知道有資料來源可以使用。</span><span class="sxs-lookup"><span data-stu-id="fbf8b-114">Without this task, the item is not visible to users and they may not be aware that the data source is available.</span></span>|  
|<span data-ttu-id="fbf8b-115">管理資料來源</span><span class="sxs-lookup"><span data-stu-id="fbf8b-115">Manage data sources</span></span>|<span data-ttu-id="fbf8b-116">檢視指定名稱、描述和連接資訊的屬性。</span><span class="sxs-lookup"><span data-stu-id="fbf8b-116">View properties that specify the name, description, and connection information.</span></span> <span data-ttu-id="fbf8b-117">此工作也會用來顯示資料夾階層中的共用資料來源項目。</span><span class="sxs-lookup"><span data-stu-id="fbf8b-117">This task is also used to display a shared data source item in the folder hierarchy.</span></span> <span data-ttu-id="fbf8b-118">如果您選擇此工作，可以省略「檢視資料來源」工作。</span><span class="sxs-lookup"><span data-stu-id="fbf8b-118">If you choose this task, you can omit the "View data sources" task.</span></span>|  
|<span data-ttu-id="fbf8b-119">設定項目安全性</span><span class="sxs-lookup"><span data-stu-id="fbf8b-119">Set security on items</span></span>|<span data-ttu-id="fbf8b-120">建立和修改控制共用資料來源之存取權的角色指派。</span><span class="sxs-lookup"><span data-stu-id="fbf8b-120">Create and modify role assignments that control access to the shared data source.</span></span> <span data-ttu-id="fbf8b-121">此工作必須用於「檢視資料來源」或「管理資料來源」工作。</span><span class="sxs-lookup"><span data-stu-id="fbf8b-121">This task must be used with either "View data source" or "Manage data sources" tasks.</span></span> <span data-ttu-id="fbf8b-122">如果不是，則因為使用者無法選取項目，而沒有作用。</span><span class="sxs-lookup"><span data-stu-id="fbf8b-122">If it is not, it has no effect because the user cannot select the item.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fbf8b-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbf8b-123">See Also</span></span>  
 <span data-ttu-id="fbf8b-124">[管理報表資料來源](../report-data/manage-report-data-sources.md) </span><span class="sxs-lookup"><span data-stu-id="fbf8b-124">[Manage Report Data Sources](../report-data/manage-report-data-sources.md) </span></span>  
 <span data-ttu-id="fbf8b-125">[保護資料夾的安全](secure-folders.md) </span><span class="sxs-lookup"><span data-stu-id="fbf8b-125">[Secure Folders](secure-folders.md) </span></span>  
 <span data-ttu-id="fbf8b-126">[保護報表和資源的安全](secure-reports-and-resources.md) </span><span class="sxs-lookup"><span data-stu-id="fbf8b-126">[Secure Reports and Resources](secure-reports-and-resources.md) </span></span>  
 <span data-ttu-id="fbf8b-127">[在原生模式報表伺服器上授與權限](granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="fbf8b-127">[Granting Permissions on a Native Mode Report Server](granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 [<span data-ttu-id="fbf8b-128">在 Reporting Services 資料來源中儲存認證</span><span class="sxs-lookup"><span data-stu-id="fbf8b-128">Store Credentials in a Reporting Services Data Source</span></span>](../report-data/store-credentials-in-a-reporting-services-data-source.md)  
  
  
