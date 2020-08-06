---
title: 資料夾和檔案權限 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- security [Master Data Services], file and folder
- folders [Master Data Services]
- files [Master Data Services]
ms.assetid: 6402d81d-7349-47b1-95ca-99b0c0f4f373
author: lrtoyou1223
ms.author: lle
robots: noindex,nofollow
ms.openlocfilehash: 6dc356e074574a4c520b1f4de2f41db0e983c4df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699934"
---
# <a name="folder-and-file-permissions-master-data-services"></a><span data-ttu-id="4493b-102">資料夾和檔案的權限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="4493b-102">Folder and File Permissions (Master Data Services)</span></span>
  <span data-ttu-id="4493b-103">當您安裝 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]時，資料夾和檔案會安裝在檔案系統中針對 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 共用功能所指定的安裝路徑。</span><span class="sxs-lookup"><span data-stu-id="4493b-103">When you install [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], folders and files are installed in the file system at the installation path you specify for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] shared features.</span></span> <span data-ttu-id="4493b-104">如果您使用共用功能的預設安裝路徑 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，的安裝路徑為 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] *drive*： \Program Files\Microsoft SQL Server\120\Master 資料服務。</span><span class="sxs-lookup"><span data-stu-id="4493b-104">If you use the default installation path for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] shared features, the installation path for [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] is *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services.</span></span> <span data-ttu-id="4493b-105">雖然您可以變更共用功能的安裝路徑，但請注意繼承自父資料夾的權限以及為 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]明確設定的權限。</span><span class="sxs-lookup"><span data-stu-id="4493b-105">Although you can change the shared features installation path, be aware of permissions that are inherited from the parent folder and permissions that are explicitly set for [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].</span></span>  
  
## <a name="inherited-permissions"></a><span data-ttu-id="4493b-106">繼承的權限</span><span class="sxs-lookup"><span data-stu-id="4493b-106">Inherited Permissions</span></span>  
 <span data-ttu-id="4493b-107">**Microsoft SQL Server** 資料夾、 **Master Data Services** 資料夾，以及大部分子資料夾和檔案都會從 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 安裝程式中指定的父資料夾繼承權限。</span><span class="sxs-lookup"><span data-stu-id="4493b-107">The **Microsoft SQL Server** folder, the **Master Data Services** folder, and most subfolders and files inherit permissions from the parent folder specified in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Setup.</span></span> <span data-ttu-id="4493b-108">如果您選擇預設安裝位置，則會從下列父資料夾繼承權限： *drive*:\Program Files。</span><span class="sxs-lookup"><span data-stu-id="4493b-108">If you choose the default installation location, the parent folder that permissions are inherited from is *drive*:\Program Files.</span></span> <span data-ttu-id="4493b-109">下表描述 **Program Files**的預設權限。</span><span class="sxs-lookup"><span data-stu-id="4493b-109">The following table describes the default permissions for **Program Files**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4493b-110">如果您修改 **Program Files**的預設權限或選擇不同的安裝位置， [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料夾和檔案會跟著從其父資料夾繼承權限，而這些權限可能不同於下表所描述的權限。</span><span class="sxs-lookup"><span data-stu-id="4493b-110">If you modify default permissions for **Program Files**, or you choose a different installation location, the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] folders and files inherit permissions from their parent folder accordingly, and the permissions might differ from those described in the following table.</span></span>  
  
###### <a name="program-files-default-permissions"></a><span data-ttu-id="4493b-111">Program Files 的預設權限</span><span class="sxs-lookup"><span data-stu-id="4493b-111">Program Files Default Permissions</span></span>  
  
|<span data-ttu-id="4493b-112">群組或帳戶名稱</span><span class="sxs-lookup"><span data-stu-id="4493b-112">Group or account name</span></span>|<span data-ttu-id="4493b-113">權限</span><span class="sxs-lookup"><span data-stu-id="4493b-113">Permissions</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="4493b-114">CREATOR OWNER</span><span class="sxs-lookup"><span data-stu-id="4493b-114">CREATOR OWNER</span></span>|<span data-ttu-id="4493b-115">特殊權限</span><span class="sxs-lookup"><span data-stu-id="4493b-115">Special permissions</span></span>|  
|<span data-ttu-id="4493b-116">系統</span><span class="sxs-lookup"><span data-stu-id="4493b-116">SYSTEM</span></span>|<span data-ttu-id="4493b-117">特殊權限</span><span class="sxs-lookup"><span data-stu-id="4493b-117">Special permissions</span></span>|  
|<span data-ttu-id="4493b-118">Administrators</span><span class="sxs-lookup"><span data-stu-id="4493b-118">Administrators</span></span>|<span data-ttu-id="4493b-119">特殊權限</span><span class="sxs-lookup"><span data-stu-id="4493b-119">Special permissions</span></span>|  
|<span data-ttu-id="4493b-120">使用者</span><span class="sxs-lookup"><span data-stu-id="4493b-120">Users</span></span>|<span data-ttu-id="4493b-121">讀取與執行、列出資料夾內容、讀取</span><span class="sxs-lookup"><span data-stu-id="4493b-121">Read & execute, List folder contents, Read</span></span>|  
|<span data-ttu-id="4493b-122">TrustedInstaller</span><span class="sxs-lookup"><span data-stu-id="4493b-122">TrustedInstaller</span></span>|<span data-ttu-id="4493b-123">列出資料夾內容、特殊權限</span><span class="sxs-lookup"><span data-stu-id="4493b-123">List folder contents, Special permissions</span></span>|  
  
## <a name="explicit-permissions"></a><span data-ttu-id="4493b-124">明確權限</span><span class="sxs-lookup"><span data-stu-id="4493b-124">Explicit Permissions</span></span>  
 <span data-ttu-id="4493b-125">**MDSTempDir** 資料夾和 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web.config 檔案 (在 **WebApplication** 資料夾中) 不會繼承權限。</span><span class="sxs-lookup"><span data-stu-id="4493b-125">The **MDSTempDir** folder and the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web.config file (in the **WebApplication** folder) do not inherit permissions.</span></span> <span data-ttu-id="4493b-126">它們的權限是在您安裝 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]時明確設定，無論所選安裝路徑為何。</span><span class="sxs-lookup"><span data-stu-id="4493b-126">They have permissions that are set explicitly when you install [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], regardless of the installation path you choose.</span></span> <span data-ttu-id="4493b-127">請不要修改這些權限。</span><span class="sxs-lookup"><span data-stu-id="4493b-127">Do not modify these permissions.</span></span>  
  
###### <a name="mdstempdir-permissions"></a><span data-ttu-id="4493b-128">MDSTempDir 的權限</span><span class="sxs-lookup"><span data-stu-id="4493b-128">MDSTempDir Permissions</span></span>  
  
|<span data-ttu-id="4493b-129">群組或帳戶名稱</span><span class="sxs-lookup"><span data-stu-id="4493b-129">Group or account name</span></span>|<span data-ttu-id="4493b-130">權限</span><span class="sxs-lookup"><span data-stu-id="4493b-130">Permissions</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="4493b-131">系統</span><span class="sxs-lookup"><span data-stu-id="4493b-131">SYSTEM</span></span>|<span data-ttu-id="4493b-132">修改、讀取與執行、列出資料夾內容、讀取、寫入</span><span class="sxs-lookup"><span data-stu-id="4493b-132">Modify, Read & execute, List folder contents, Read, Write</span></span>|  
|<span data-ttu-id="4493b-133">Administrators</span><span class="sxs-lookup"><span data-stu-id="4493b-133">Administrators</span></span>|<span data-ttu-id="4493b-134">修改、讀取與執行、列出資料夾內容、讀取、寫入</span><span class="sxs-lookup"><span data-stu-id="4493b-134">Modify, Read & execute, List folder contents, Read, Write</span></span>|  
|<span data-ttu-id="4493b-135">MDS_ServiceAccounts</span><span class="sxs-lookup"><span data-stu-id="4493b-135">MDS_ServiceAccounts</span></span>|<span data-ttu-id="4493b-136">修改、讀取與執行、列出資料夾內容、讀取、寫入</span><span class="sxs-lookup"><span data-stu-id="4493b-136">Modify, Read & execute, List folder contents, Read, Write</span></span>|  
  
###### <a name="webconfig-permissions"></a><span data-ttu-id="4493b-137">Web.config 的權限</span><span class="sxs-lookup"><span data-stu-id="4493b-137">Web.config Permissions</span></span>  
  
|<span data-ttu-id="4493b-138">群組或帳戶名稱</span><span class="sxs-lookup"><span data-stu-id="4493b-138">Group or account name</span></span>|<span data-ttu-id="4493b-139">權限</span><span class="sxs-lookup"><span data-stu-id="4493b-139">Permissions</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="4493b-140">系統</span><span class="sxs-lookup"><span data-stu-id="4493b-140">SYSTEM</span></span>|<span data-ttu-id="4493b-141">完全控制、修改、讀取與執行、讀取、寫入</span><span class="sxs-lookup"><span data-stu-id="4493b-141">Full control, Modify, Read & execute, Read, Write</span></span>|  
|<span data-ttu-id="4493b-142">Administrators</span><span class="sxs-lookup"><span data-stu-id="4493b-142">Administrators</span></span>|<span data-ttu-id="4493b-143">完全控制、修改、讀取與執行、讀取、寫入</span><span class="sxs-lookup"><span data-stu-id="4493b-143">Full control, Modify, Read & execute, Read, Write</span></span>|  
|<span data-ttu-id="4493b-144">MDS_ServiceAccounts</span><span class="sxs-lookup"><span data-stu-id="4493b-144">MDS_ServiceAccounts</span></span>|<span data-ttu-id="4493b-145">讀取與執行、讀取</span><span class="sxs-lookup"><span data-stu-id="4493b-145">Read & execute, Read</span></span>|  
  
 <span data-ttu-id="4493b-146">如需 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web.config 檔案內容的詳細資訊，請參閱 [Web 組態參考 &#40;Master Data Services&#41;](web-configuration-reference-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="4493b-146">For more information about the contents of the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web.config file, see [Web Configuration Reference &#40;Master Data Services&#41;](web-configuration-reference-master-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4493b-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4493b-147">See Also</span></span>  
 [<span data-ttu-id="4493b-148">安裝 Master Data Services</span><span class="sxs-lookup"><span data-stu-id="4493b-148">Install Master Data Services</span></span>](install-windows/install-master-data-services.md)  
  
  
