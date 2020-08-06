---
title: 選取目的地位置 (SSIS 封裝升級嚮導) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.is.upgradewizard.selectdestinationlocation.f1
ms.assetid: 89274a71-0ffe-4889-84df-f5a7d78459ef
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9411157434c3dbb9fb033f7b63b5e6041fd8f75d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606974"
---
# <a name="select-destination-location-ssis-package-upgrade-wizard"></a><span data-ttu-id="3c1ba-102">選取目的地位置 (SSIS 封裝升級精靈)</span><span class="sxs-lookup"><span data-stu-id="3c1ba-102">Select Destination Location (SSIS Package Upgrade Wizard)</span></span>
  <span data-ttu-id="3c1ba-103">使用 **[選取目的地位置]** 頁面，指定用來儲存升級封裝的目的地。</span><span class="sxs-lookup"><span data-stu-id="3c1ba-103">Use the **Select Destination Location** page to specify the destination to which to save the upgraded packages.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3c1ba-104">只有當您從 [!INCLUDE[ssIS](../includes/ssis-md.md)] 或命令提示字元執行 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 封裝升級精靈時，才可使用此頁面。</span><span class="sxs-lookup"><span data-stu-id="3c1ba-104">This page is only available when you run the [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Upgrade Wizard from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] or at the command prompt.</span></span>  
  
 <span data-ttu-id="3c1ba-105">**執行 SSIS 封裝升級精靈**</span><span class="sxs-lookup"><span data-stu-id="3c1ba-105">**To run the SSIS Package Upgrade Wizard**</span></span>  
  
-   [<span data-ttu-id="3c1ba-106">使用 SSIS 套件升級精靈來升級 Integration Services 套件</span><span class="sxs-lookup"><span data-stu-id="3c1ba-106">Upgrade Integration Services Packages Using the SSIS Package Upgrade Wizard</span></span>](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)  
  
## <a name="static-options"></a><span data-ttu-id="3c1ba-107">靜態選項</span><span class="sxs-lookup"><span data-stu-id="3c1ba-107">Static Options</span></span>  
 <span data-ttu-id="3c1ba-108">**儲存至來源位置**</span><span class="sxs-lookup"><span data-stu-id="3c1ba-108">**Save to source location**</span></span>  
 <span data-ttu-id="3c1ba-109">將升級封裝儲存到此精靈之 [選取來源位置]  頁面上所指定的相同位置。</span><span class="sxs-lookup"><span data-stu-id="3c1ba-109">Save the upgraded packages to the same location as specified on the **Select Source Location** page of the wizard.</span></span>  
  
 <span data-ttu-id="3c1ba-110">如果原始封裝儲存在檔案系統中，而且您希望精靈備份這些封裝，請選取 **[儲存至來源位置]** 選項。</span><span class="sxs-lookup"><span data-stu-id="3c1ba-110">If the original packages are stored in the file system and you want the wizard to back up those packages, select the **Save to source location** option.</span></span> <span data-ttu-id="3c1ba-111">如需詳細資訊，請參閱 [使用 SSIS 封裝升級精靈來升級 Integration Services 封裝](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="3c1ba-111">For more information, see [Upgrade Integration Services Packages Using the SSIS Package Upgrade Wizard](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md).</span></span>  
  
 <span data-ttu-id="3c1ba-112">**選取新的目的地位置**</span><span class="sxs-lookup"><span data-stu-id="3c1ba-112">**Select new destination location**</span></span>  
 <span data-ttu-id="3c1ba-113">將升級封裝儲存到此頁面上指定的目的地位置。</span><span class="sxs-lookup"><span data-stu-id="3c1ba-113">Save the upgraded packages to the destination location that is specified on this page.</span></span>  
  
 <span data-ttu-id="3c1ba-114">**封裝來源**</span><span class="sxs-lookup"><span data-stu-id="3c1ba-114">**Package source**</span></span>  
 <span data-ttu-id="3c1ba-115">指定要儲存升級封裝的位置。</span><span class="sxs-lookup"><span data-stu-id="3c1ba-115">Specify where the upgrade packages are to be stored.</span></span> <span data-ttu-id="3c1ba-116">這個選項的值列於下表中。</span><span class="sxs-lookup"><span data-stu-id="3c1ba-116">This option has the values listed in the following table.</span></span>  
  
|<span data-ttu-id="3c1ba-117">值</span><span class="sxs-lookup"><span data-stu-id="3c1ba-117">Value</span></span>|<span data-ttu-id="3c1ba-118">描述</span><span class="sxs-lookup"><span data-stu-id="3c1ba-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3c1ba-119">**檔案系統**</span><span class="sxs-lookup"><span data-stu-id="3c1ba-119">**File System**</span></span>|<span data-ttu-id="3c1ba-120">指示升級封裝要儲存到本機電腦的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="3c1ba-120">Indicates that the upgraded packages are to be saved to a folder on the local computer.</span></span>|  
|<span data-ttu-id="3c1ba-121">**SSIS 封裝存放區**</span><span class="sxs-lookup"><span data-stu-id="3c1ba-121">**SSIS Package Store**</span></span>|<span data-ttu-id="3c1ba-122">指示升級封裝要儲存到 Integration Services 封裝存放區。</span><span class="sxs-lookup"><span data-stu-id="3c1ba-122">Indicates that the upgraded packages are to be saved to the Integration Services package store.</span></span> <span data-ttu-id="3c1ba-123">此封裝存放區是由 Integration Services 服務所管理的檔案系統資料夾集合所組成。</span><span class="sxs-lookup"><span data-stu-id="3c1ba-123">The package store consists of the set of file system folders that the Integration Services service manages.</span></span> <span data-ttu-id="3c1ba-124">如需詳細資訊，請參閱[封裝管理 &#40;SSIS 服務&#41;](service/package-management-ssis-service.md)。</span><span class="sxs-lookup"><span data-stu-id="3c1ba-124">For more information, see [Package Management &#40;SSIS Service&#41;](service/package-management-ssis-service.md).</span></span><br /><br /> <span data-ttu-id="3c1ba-125">選取這個值會顯示對應的 **[封裝來源]** 動態選項。</span><span class="sxs-lookup"><span data-stu-id="3c1ba-125">Selecting this value displays the corresponding **Package source** dynamics options.</span></span>|  
|<span data-ttu-id="3c1ba-126">**Microsoft SQL Server**</span><span class="sxs-lookup"><span data-stu-id="3c1ba-126">**Microsoft SQL Server**</span></span>|<span data-ttu-id="3c1ba-127">指示升級封裝要儲存到現有的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]執行個體。</span><span class="sxs-lookup"><span data-stu-id="3c1ba-127">Indicates that the upgraded packages are to be saved to an existing instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="3c1ba-128">選取這個值會顯示對應的 **[封裝來源]** 動態選項。</span><span class="sxs-lookup"><span data-stu-id="3c1ba-128">Selecting this value displays the corresponding dynamic **Package source** dynamic options.</span></span>|  
  
 <span data-ttu-id="3c1ba-129">**資料夾**</span><span class="sxs-lookup"><span data-stu-id="3c1ba-129">**Folder**</span></span>  
 <span data-ttu-id="3c1ba-130">輸入將用來儲存升級封裝的資料夾名稱，或是按一下 [瀏覽]  並尋找資料夾。</span><span class="sxs-lookup"><span data-stu-id="3c1ba-130">Type the name of a folder to which the upgraded packages will be saved, or click **Browse** and locate the folder.</span></span>  
  
 <span data-ttu-id="3c1ba-131">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="3c1ba-131">**Browse**</span></span>  
 <span data-ttu-id="3c1ba-132">瀏覽來尋找將儲存升級封裝的資料夾。</span><span class="sxs-lookup"><span data-stu-id="3c1ba-132">Browse to locate the folder to which the upgraded packages will be saved.</span></span>  
  
## <a name="package-source-dynamic-options"></a><span data-ttu-id="3c1ba-133">封裝來源動態選項</span><span class="sxs-lookup"><span data-stu-id="3c1ba-133">Package Source Dynamic Options</span></span>  
  
### <a name="package-source--ssis-package-store"></a><span data-ttu-id="3c1ba-134">封裝來源 = SSIS 封裝存放區</span><span class="sxs-lookup"><span data-stu-id="3c1ba-134">Package source = SSIS Package Store</span></span>  
 <span data-ttu-id="3c1ba-135">**Server**</span><span class="sxs-lookup"><span data-stu-id="3c1ba-135">**Server**</span></span>  
 <span data-ttu-id="3c1ba-136">輸入升級封裝儲存所在的伺服器名稱，或是從清單中選取伺服器。</span><span class="sxs-lookup"><span data-stu-id="3c1ba-136">Type the name of the server to which the upgrade packages will be saved, or select a server in the list.</span></span>  
  
### <a name="package-source--microsoft-sql-server"></a><span data-ttu-id="3c1ba-137">封裝來源 = Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="3c1ba-137">Package source = Microsoft SQL Server</span></span>  
 <span data-ttu-id="3c1ba-138">**Server**</span><span class="sxs-lookup"><span data-stu-id="3c1ba-138">**Server**</span></span>  
 <span data-ttu-id="3c1ba-139">輸入升級封裝儲存所在的伺服器名稱，或是從清單中選取此伺服器。</span><span class="sxs-lookup"><span data-stu-id="3c1ba-139">Type the name of the server to which the upgrade packages will be saved, or select this server in the list.</span></span>  
  
 <span data-ttu-id="3c1ba-140">**使用 Windows 驗證**</span><span class="sxs-lookup"><span data-stu-id="3c1ba-140">**Use Windows authentication**</span></span>  
 <span data-ttu-id="3c1ba-141">選取此選項可使用 Windows 驗證來連接伺服器。</span><span class="sxs-lookup"><span data-stu-id="3c1ba-141">Select to use Windows Authentication to connect to the server.</span></span>  
  
 <span data-ttu-id="3c1ba-142">**使用 SQL Server 驗證**</span><span class="sxs-lookup"><span data-stu-id="3c1ba-142">**Use SQL Server authentication**</span></span>  
 <span data-ttu-id="3c1ba-143">選取此選項可使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證連接到伺服器。</span><span class="sxs-lookup"><span data-stu-id="3c1ba-143">Select to use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication to connect to the server.</span></span> <span data-ttu-id="3c1ba-144">如果您使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證，就必須提供使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="3c1ba-144">If you use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, you must provide a user name and password.</span></span>  
  
 <span data-ttu-id="3c1ba-145">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="3c1ba-145">**User name**</span></span>  
 <span data-ttu-id="3c1ba-146">輸入使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證來連接伺服器時所要使用的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="3c1ba-146">Type the user name to be used when using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication to connect to the server.</span></span>  
  
 <span data-ttu-id="3c1ba-147">**密碼**</span><span class="sxs-lookup"><span data-stu-id="3c1ba-147">**Password**</span></span>  
 <span data-ttu-id="3c1ba-148">輸入使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證來連接伺服器時所要使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="3c1ba-148">Type the password to be used when using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication to connect to the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c1ba-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c1ba-149">See Also</span></span>  
 [<span data-ttu-id="3c1ba-150">升級 Integration Services 套件</span><span class="sxs-lookup"><span data-stu-id="3c1ba-150">Upgrade Integration Services Packages</span></span>](install-windows/upgrade-integration-services-packages.md)  
  
  
