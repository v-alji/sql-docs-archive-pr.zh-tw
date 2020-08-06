---
title: 選取 [來源位置] (SSIS 封裝升級嚮導) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.is.upgradewizard.selectsourcelocation.f1
ms.assetid: 429f146e-edb4-4401-a225-f2c8468971c5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e24eec77dc87a6215f9d686cf5af964cc244d68d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687034"
---
# <a name="select-source-location-ssis-package-upgrade-wizard"></a><span data-ttu-id="ba5b2-102">選取來源位置 (SSIS 封裝升級精靈)</span><span class="sxs-lookup"><span data-stu-id="ba5b2-102">Select Source Location (SSIS Package Upgrade Wizard)</span></span>
  <span data-ttu-id="ba5b2-103">使用 **[選取來源位置]** 頁面，指定升級封裝的來源。</span><span class="sxs-lookup"><span data-stu-id="ba5b2-103">Use the **Select Source Location** page to specify the source from which to upgrade packages.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ba5b2-104">只有當您從 [!INCLUDE[ssIS](../includes/ssis-md.md)] 或命令提示字元執行 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 封裝升級精靈時，才可使用此頁面。</span><span class="sxs-lookup"><span data-stu-id="ba5b2-104">This page is only available when you run the [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Upgrade Wizard from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] or at the command prompt.</span></span>  
  
 <span data-ttu-id="ba5b2-105">**執行 SSIS 封裝升級精靈**</span><span class="sxs-lookup"><span data-stu-id="ba5b2-105">**To run the SSIS Package Upgrade Wizard**</span></span>  
  
-   [<span data-ttu-id="ba5b2-106">使用 SSIS 套件升級精靈來升級 Integration Services 套件</span><span class="sxs-lookup"><span data-stu-id="ba5b2-106">Upgrade Integration Services Packages Using the SSIS Package Upgrade Wizard</span></span>](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)  
  
## <a name="static-options"></a><span data-ttu-id="ba5b2-107">靜態選項</span><span class="sxs-lookup"><span data-stu-id="ba5b2-107">Static Options</span></span>  
 <span data-ttu-id="ba5b2-108">**封裝來源**</span><span class="sxs-lookup"><span data-stu-id="ba5b2-108">**Package source**</span></span>  
 <span data-ttu-id="ba5b2-109">選取包含要升級之封裝的儲存位置。</span><span class="sxs-lookup"><span data-stu-id="ba5b2-109">Select the storage location that contains the packages to be upgraded.</span></span> <span data-ttu-id="ba5b2-110">這個選項的值列於下表中。</span><span class="sxs-lookup"><span data-stu-id="ba5b2-110">This option has the values listed in the following table.</span></span>  
  
|<span data-ttu-id="ba5b2-111">值</span><span class="sxs-lookup"><span data-stu-id="ba5b2-111">Value</span></span>|<span data-ttu-id="ba5b2-112">描述</span><span class="sxs-lookup"><span data-stu-id="ba5b2-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ba5b2-113">**檔案系統**</span><span class="sxs-lookup"><span data-stu-id="ba5b2-113">**File System**</span></span>|<span data-ttu-id="ba5b2-114">指示要升級的封裝位於本機電腦的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="ba5b2-114">Indicates that the packages to be upgraded are in a folder on the local computer.</span></span><br /><br /> <span data-ttu-id="ba5b2-115">若要讓精靈在升級這些封裝之前先備份原始封裝，原始封裝必須儲存在檔案系統中。</span><span class="sxs-lookup"><span data-stu-id="ba5b2-115">To have the wizard back up the original packages before upgrading those packages, the original packages must be stored in the file system.</span></span> <span data-ttu-id="ba5b2-116">如需詳細資訊，請參閱「如何」主題。</span><span class="sxs-lookup"><span data-stu-id="ba5b2-116">For more information, see How To Topic.</span></span>|  
|<span data-ttu-id="ba5b2-117">**SSIS 封裝存放區**</span><span class="sxs-lookup"><span data-stu-id="ba5b2-117">**SSIS Package Store**</span></span>|<span data-ttu-id="ba5b2-118">指示要升級的封裝位於封裝存放區中。</span><span class="sxs-lookup"><span data-stu-id="ba5b2-118">Indicates that the packages to be upgraded are in the package store.</span></span> <span data-ttu-id="ba5b2-119">此封裝存放區是由 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務所管理的檔案系統資料夾集合所組成。</span><span class="sxs-lookup"><span data-stu-id="ba5b2-119">The package store consists of the set of file system folders that the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service manages.</span></span> <span data-ttu-id="ba5b2-120">如需詳細資訊，請參閱[封裝管理 &#40;SSIS 服務&#41;](service/package-management-ssis-service.md)。</span><span class="sxs-lookup"><span data-stu-id="ba5b2-120">For more information, see [Package Management &#40;SSIS Service&#41;](service/package-management-ssis-service.md).</span></span><br /><br /> <span data-ttu-id="ba5b2-121">選取這個值會顯示對應的 **[封裝來源]** 動態選項。</span><span class="sxs-lookup"><span data-stu-id="ba5b2-121">Selecting this value displays the corresponding **Package source** dynamic options.</span></span>|  
|<span data-ttu-id="ba5b2-122">**Microsoft SQL Server**</span><span class="sxs-lookup"><span data-stu-id="ba5b2-122">**Microsoft SQL Server**</span></span>|<span data-ttu-id="ba5b2-123">指示要升級的封裝是來自現有的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]執行個體。</span><span class="sxs-lookup"><span data-stu-id="ba5b2-123">Indicates the packages to be upgraded are from an existing instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="ba5b2-124">選取這個值會顯示對應的 **[封裝來源]** 動態選項。</span><span class="sxs-lookup"><span data-stu-id="ba5b2-124">Selecting this value displays the corresponding **Package source** dynamic options.</span></span>|  
  
 <span data-ttu-id="ba5b2-125">**資料夾**</span><span class="sxs-lookup"><span data-stu-id="ba5b2-125">**Folder**</span></span>  
 <span data-ttu-id="ba5b2-126">輸入包含您想要升級之封裝的資料夾名稱，或是按一下 [瀏覽]  並尋找資料夾。</span><span class="sxs-lookup"><span data-stu-id="ba5b2-126">Type the name of a folder that contains the packages you want to upgrade or click **Browse** and locate the folder.</span></span>  
  
 <span data-ttu-id="ba5b2-127">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="ba5b2-127">**Browse**</span></span>  
 <span data-ttu-id="ba5b2-128">瀏覽來尋找包含您要升級之封裝的資料夾。</span><span class="sxs-lookup"><span data-stu-id="ba5b2-128">Browse to locate the folder that contains the packages you want to upgrade.</span></span>  
  
## <a name="package-source-dynamic-options"></a><span data-ttu-id="ba5b2-129">封裝來源動態選項</span><span class="sxs-lookup"><span data-stu-id="ba5b2-129">Package Source Dynamic Options</span></span>  
  
### <a name="package-source--ssis-package-store"></a><span data-ttu-id="ba5b2-130">封裝來源 = SSIS 封裝存放區</span><span class="sxs-lookup"><span data-stu-id="ba5b2-130">Package source = SSIS Package Store</span></span>  
 <span data-ttu-id="ba5b2-131">**Server**</span><span class="sxs-lookup"><span data-stu-id="ba5b2-131">**Server**</span></span>  
 <span data-ttu-id="ba5b2-132">輸入具有要升級之封裝的伺服器名稱，或是從清單中選取此伺服器。</span><span class="sxs-lookup"><span data-stu-id="ba5b2-132">Type the name of the server that has the packages to be upgraded, or select this server in the list.</span></span>  
  
### <a name="package-source--microsoft-sql-server"></a><span data-ttu-id="ba5b2-133">封裝來源 = Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="ba5b2-133">Package source = Microsoft SQL Server</span></span>  
 <span data-ttu-id="ba5b2-134">**Server**</span><span class="sxs-lookup"><span data-stu-id="ba5b2-134">**Server**</span></span>  
 <span data-ttu-id="ba5b2-135">輸入具有要升級之封裝的伺服器名稱，或是從清單中選取此伺服器。</span><span class="sxs-lookup"><span data-stu-id="ba5b2-135">Type the name of the server that has the packages to be upgraded, or select this server from the list.</span></span>  
  
 <span data-ttu-id="ba5b2-136">**使用 Windows 驗證**</span><span class="sxs-lookup"><span data-stu-id="ba5b2-136">**Use Windows authentication**</span></span>  
 <span data-ttu-id="ba5b2-137">選取此選項可使用 Windows 驗證來連接伺服器。</span><span class="sxs-lookup"><span data-stu-id="ba5b2-137">Select to use Windows Authentication to connect to the server.</span></span>  
  
 <span data-ttu-id="ba5b2-138">**使用 SQL Server 驗證**</span><span class="sxs-lookup"><span data-stu-id="ba5b2-138">**Use SQL Server authentication**</span></span>  
 <span data-ttu-id="ba5b2-139">選取此選項可使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證連接到伺服器。</span><span class="sxs-lookup"><span data-stu-id="ba5b2-139">Select to use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication to connect to the server.</span></span> <span data-ttu-id="ba5b2-140">如果您使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證，就必須提供使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="ba5b2-140">If you use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, you must provide a user name and password.</span></span>  
  
 <span data-ttu-id="ba5b2-141">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="ba5b2-141">**User name**</span></span>  
 <span data-ttu-id="ba5b2-142">輸入 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證將用來連接伺服器的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="ba5b2-142">Type the user name that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication will use to connect to the server.</span></span>  
  
 <span data-ttu-id="ba5b2-143">**密碼**</span><span class="sxs-lookup"><span data-stu-id="ba5b2-143">**Password**</span></span>  
 <span data-ttu-id="ba5b2-144">輸入 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證將用來連接伺服器的密碼。</span><span class="sxs-lookup"><span data-stu-id="ba5b2-144">Type the password that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication will use to connect to the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba5b2-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba5b2-145">See Also</span></span>  
 [<span data-ttu-id="ba5b2-146">升級 Integration Services 套件</span><span class="sxs-lookup"><span data-stu-id="ba5b2-146">Upgrade Integration Services Packages</span></span>](install-windows/upgrade-integration-services-packages.md)  
  
  
