---
title: 保護資料夾的安全 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- high-security folders [Reporting Services]
- low-security folders
- folders [Reporting Services], security
- security [Reporting Services], folders
ms.assetid: 0fd91f77-0143-476b-9af0-87293be78e44
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 483b3108713032b3aaf566208f39f6c2f705da1a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593263"
---
# <a name="secure-folders"></a><span data-ttu-id="2062e-102">保護資料夾的安全</span><span class="sxs-lookup"><span data-stu-id="2062e-102">Secure Folders</span></span>
  <span data-ttu-id="2062e-103">資料夾安全性是保護報表伺服器中之所有內容的基礎。</span><span class="sxs-lookup"><span data-stu-id="2062e-103">Folder security is the foundation for securing all content in a report server.</span></span> <span data-ttu-id="2062e-104">因為安全性會在整個資料夾結構繼承，所以您可以指定很多或很少區段的資料夾階層，來允許特定類型的存取。</span><span class="sxs-lookup"><span data-stu-id="2062e-104">Because security is inherited throughout the folder structure, you can designate large or small sections of the folder hierarchy to allow for certain kinds of access.</span></span>  
  
 <span data-ttu-id="2062e-105">高安全性資料夾可以用來儲存機密報表，或當成臨時區域；例如，您可以先使用一個資料夾來測試報表，然後再將報表移至最終位置。</span><span class="sxs-lookup"><span data-stu-id="2062e-105">High-security folders can be used to store confidential reports or as staging areas; for example, you can have a folder that you use to test reports before moving them to a final location.</span></span> <span data-ttu-id="2062e-106">若要控制此區域的存取，您可以定義一個角色指派，只允許報表作者加入和刪除項目，以及第二個角色指派，允許測試者執行報表，但不能加入或移除項目。</span><span class="sxs-lookup"><span data-stu-id="2062e-106">To control access to this area, you can define one role assignment that allows only report authors to add and delete items, and a second role assignment that allows testers to run reports but not to add or remove items.</span></span> <span data-ttu-id="2062e-107">因為角色指派是專為測試者與報表作者所定義，所以沒有其他使用者 (除了本機系統管理員以外) 可以存取資料夾。</span><span class="sxs-lookup"><span data-stu-id="2062e-107">Because the role assignments are defined explicitly for testers and report authors, no other users (except for local system administrators) can access the folder.</span></span>  
  
 <span data-ttu-id="2062e-108">低安全性資料夾可以用來儲存您要很容易存取的報表。</span><span class="sxs-lookup"><span data-stu-id="2062e-108">Low-security folders can be used to store reports that you want to be easily accessible.</span></span>  
  
 <span data-ttu-id="2062e-109">資料夾安全性會形成項目層級安全性的基礎，以報表伺服器資料夾階層的根節點開始，也就是 [主資料夾] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="2062e-109">Folder security forms the basis of item-level security, starting with the root node of the report server folder hierarchy, the Home folder.</span></span> <span data-ttu-id="2062e-110">因為安全性是繼承的，建議在 [主資料夾] 資料夾設定較嚴格的安全性原則。</span><span class="sxs-lookup"><span data-stu-id="2062e-110">Because security is inherited, it is advisable to set a fairly restrictive security policy on the Home folder.</span></span> <span data-ttu-id="2062e-111">使用 [主資料夾] 角色指派裡的 [瀏覽器]  角色，即可提供只供檢視存取。</span><span class="sxs-lookup"><span data-stu-id="2062e-111">Using the **Browser** role in Home folder role assignments does exactly that by providing view-only access.</span></span>  
  
## <a name="tasks-and-folder-access"></a><span data-ttu-id="2062e-112">工作和資料夾存取</span><span class="sxs-lookup"><span data-stu-id="2062e-112">Tasks and Folder Access</span></span>  
 <span data-ttu-id="2062e-113">建立資料夾的角色指派時，請考慮下表列出的工作。</span><span class="sxs-lookup"><span data-stu-id="2062e-113">When creating role assignments for folders, consider the tasks listed in the following table.</span></span>  
  
|<span data-ttu-id="2062e-114">選取的工作</span><span class="sxs-lookup"><span data-stu-id="2062e-114">Select this task</span></span>|<span data-ttu-id="2062e-115">授與的權限</span><span class="sxs-lookup"><span data-stu-id="2062e-115">To give permission to</span></span>|  
|----------------------|---------------------------|  
|<span data-ttu-id="2062e-116">檢視資料夾</span><span class="sxs-lookup"><span data-stu-id="2062e-116">View folders</span></span>|<span data-ttu-id="2062e-117">檢視資料夾階層，以及指出資料夾建立與修改時間的唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="2062e-117">View the folder hierarchy and read-only properties that indicate when the folder was created and modified.</span></span><br /><br /> <span data-ttu-id="2062e-118">除非指派給使用者的角色還包含了「檢視報表」、「檢視模型」、「檢視資源」及「檢視資料來源」等工作，否則使用者無法檢視資料夾內的項目。</span><span class="sxs-lookup"><span data-stu-id="2062e-118">Users cannot view items in the folder unless they are assigned to roles that also include the following tasks: "View reports," "View models", "View resources," and "View data sources."</span></span>|  
|<span data-ttu-id="2062e-119">管理資料夾</span><span class="sxs-lookup"><span data-stu-id="2062e-119">Manage folders</span></span>|<span data-ttu-id="2062e-120">檢視資料夾屬性、變更名稱或描述，或者將資料夾移到另一個位置。</span><span class="sxs-lookup"><span data-stu-id="2062e-120">View folder properties, change the name or description, or move the folder to another location.</span></span> <span data-ttu-id="2062e-121">此工作允許使用者建立資料夾。</span><span class="sxs-lookup"><span data-stu-id="2062e-121">This task allows users to create folders.</span></span>|  
|<span data-ttu-id="2062e-122">管理報表</span><span class="sxs-lookup"><span data-stu-id="2062e-122">Manage reports</span></span>|<span data-ttu-id="2062e-123">從檔案系統將報表加入至資料夾，以及從報表設計師將報表發行至報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="2062e-123">Add reports from the file system to a folder and publish reports from Report Designer to the report server.</span></span>|  
|<span data-ttu-id="2062e-124">管理資料來源</span><span class="sxs-lookup"><span data-stu-id="2062e-124">Manage data sources</span></span>|<span data-ttu-id="2062e-125">將新的共用資料來源項目加入至資料夾，以及變更現有的共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="2062e-125">Add new shared data source items to a folder and change existing shared data sources.</span></span>|  
|<span data-ttu-id="2062e-126">設定項目安全性</span><span class="sxs-lookup"><span data-stu-id="2062e-126">Set security on items</span></span>|<span data-ttu-id="2062e-127">建立和修改控制資料夾之存取的角色指派。</span><span class="sxs-lookup"><span data-stu-id="2062e-127">Create and modify role assignments that control access to the folder.</span></span> <span data-ttu-id="2062e-128">此工作必須用於「檢視資料夾」或「管理資料夾」。</span><span class="sxs-lookup"><span data-stu-id="2062e-128">This task must be used with either "View folders" or "Manage folders."</span></span> <span data-ttu-id="2062e-129">若不這麼做，使用者將無法選取項目，而不會產生任何影響。</span><span class="sxs-lookup"><span data-stu-id="2062e-129">If it is not, it will have no effect because the user will not be able to select the item.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2062e-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2062e-130">See Also</span></span>  
 <span data-ttu-id="2062e-131">[保護報表和資源的安全](secure-reports-and-resources.md) </span><span class="sxs-lookup"><span data-stu-id="2062e-131">[Secure Reports and Resources](secure-reports-and-resources.md) </span></span>  
 <span data-ttu-id="2062e-132">[保護共用資料來源項目的安全](secure-shared-data-source-items.md) </span><span class="sxs-lookup"><span data-stu-id="2062e-132">[Secure Shared Data Source Items](secure-shared-data-source-items.md) </span></span>  
 [<span data-ttu-id="2062e-133">在原生模式報表伺服器上授與權限</span><span class="sxs-lookup"><span data-stu-id="2062e-133">Granting Permissions on a Native Mode Report Server</span></span>](granting-permissions-on-a-native-mode-report-server.md)  
  
  
