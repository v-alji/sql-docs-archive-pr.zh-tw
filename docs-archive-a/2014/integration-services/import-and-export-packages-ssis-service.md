---
title: " (SSIS 服務匯入和匯出套件) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], importing
- packages [Integration Services], exporting
- importing packages
- exporting packages
ms.assetid: ef18ec11-b536-47d9-abd1-794099f43486
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b69f9d23431ed86f6b84be6857b7104cd8ba3dcc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597955"
---
# <a name="import-and-export-packages-ssis-service"></a><span data-ttu-id="22383-102">匯入和匯出封裝 (SSIS 服務)</span><span class="sxs-lookup"><span data-stu-id="22383-102">Import and Export Packages (SSIS Service)</span></span>
    
> [!IMPORTANT]  
>  <span data-ttu-id="22383-103">本主題會討論 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務，即用於管理 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝的 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="22383-103">This topic discusses the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="22383-104">支援此服務能與舊版 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]回溯相容。</span><span class="sxs-lookup"><span data-stu-id="22383-104">supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="22383-105">從 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]開始，您可以管理 Integration Services 伺服器上的物件，例如封裝。</span><span class="sxs-lookup"><span data-stu-id="22383-105">Starting in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], you can manage objects such as packages on the Integration Services server.</span></span>  
  
 <span data-ttu-id="22383-106">封裝可以儲存在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb 資料庫的 sysssispackages 資料表中，也可以儲存在檔案系統中。</span><span class="sxs-lookup"><span data-stu-id="22383-106">Packages can be saved either in the sysssispackages table in the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb database or in the file system.</span></span>  
  
 <span data-ttu-id="22383-107">封裝存放區 ( [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務所監視和管理的邏輯儲存體) 可以同時包含在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務之組態檔中指定的 msdb 資料庫和檔案系統資料夾。</span><span class="sxs-lookup"><span data-stu-id="22383-107">The package store, which is the logical storage that [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service monitors and manages, can include both the msdb database and the file system folders specified in the configuration file for the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span>  
  
 <span data-ttu-id="22383-108">您可以在下列儲存體類型之間匯入和匯出封裝：</span><span class="sxs-lookup"><span data-stu-id="22383-108">You can import and export packages between the following storage types:</span></span>  
  
-   <span data-ttu-id="22383-109">檔案系統中任意位置的檔案系統資料夾。</span><span class="sxs-lookup"><span data-stu-id="22383-109">File system folders anywhere in the file system.</span></span>  
  
-   <span data-ttu-id="22383-110">「SSIS 封裝存放區」中的資料夾。</span><span class="sxs-lookup"><span data-stu-id="22383-110">Folders in the SSIS Package Store.</span></span> <span data-ttu-id="22383-111">兩個預設資料夾名為 File System 和 MSDB。</span><span class="sxs-lookup"><span data-stu-id="22383-111">The two default folders are named File System and MSDB.</span></span>  
  
-   <span data-ttu-id="22383-112">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb 資料庫。</span><span class="sxs-lookup"><span data-stu-id="22383-112">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] msdb database.</span></span>  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="22383-113">可讓您匯入和匯出封裝，並藉此變更封裝的儲存格式和位置。</span><span class="sxs-lookup"><span data-stu-id="22383-113">gives you the ability to import and export packages, and by doing this change the storage format and location of packages.</span></span> <span data-ttu-id="22383-114">使用匯入和匯出功能，可以將封裝加入檔案系統、封裝存放區或 msdb 資料庫，並將封裝從一個儲存體複製到另一個儲存體。</span><span class="sxs-lookup"><span data-stu-id="22383-114">Using the import and export features, you can add packages to the file system, package store, or msdb database, and copy packages from one storage format to another.</span></span> <span data-ttu-id="22383-115">例如，可以將 msdb 中儲存的封裝複製到檔案系統，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="22383-115">For example, packages saved in msdb can be copied to the file system and vice versa.</span></span>  
  
 <span data-ttu-id="22383-116">您也可以使用 **dtutil** 命令提示公用程式 (dtutil.exe)，將封裝複製成其他格式。</span><span class="sxs-lookup"><span data-stu-id="22383-116">You can also copy a package to a different format using the **dtutil** command prompt utility (dtutil.exe).</span></span> <span data-ttu-id="22383-117">如需詳細資訊，請參閱 [dtutil Utility](dtutil-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="22383-117">For more information, see [dtutil Utility](dtutil-utility.md).</span></span>  
  
## <a name="to-import-or-export-a-package"></a><span data-ttu-id="22383-118">匯入或匯出封裝</span><span class="sxs-lookup"><span data-stu-id="22383-118">To import or export a package</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="22383-119">本主題會討論 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 的 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]服務。</span><span class="sxs-lookup"><span data-stu-id="22383-119">This topic discusses the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service that is part of [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].</span></span> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="22383-120">支援 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務，可回溯相容於 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="22383-120">supports the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service for backward compatibility with [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].</span></span> <span data-ttu-id="22383-121">如需在 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 中管理封裝的資訊，請參閱 [Integration Services &#40;SSIS&#41; 伺服器](catalog/integration-services-ssis-server-and-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="22383-121">For information about managing packages in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], see [Integration Services &#40;SSIS&#41; Server](catalog/integration-services-ssis-server-and-catalog.md).</span></span>  
  
 <span data-ttu-id="22383-122">您可以在下列位置之間匯入或匯出 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝：</span><span class="sxs-lookup"><span data-stu-id="22383-122">You can import or export an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package from or to the following locations:</span></span>  
  
-   <span data-ttu-id="22383-123">您可以匯入儲存在 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體、檔案系統或 [!INCLUDE[ssIS](../includes/ssis-md.md)] 套件存放區中的套件。</span><span class="sxs-lookup"><span data-stu-id="22383-123">You can import a package that is stored in an instance of [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], in the file system, or in the [!INCLUDE[ssIS](../includes/ssis-md.md)] package store.</span></span> <span data-ttu-id="22383-124">匯入的封裝將儲存到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssIS](../includes/ssis-md.md)] 封裝存放區內的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="22383-124">The imported package is saved to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or to a folder in the [!INCLUDE[ssIS](../includes/ssis-md.md)] package store.</span></span>  
  
-   <span data-ttu-id="22383-125">您可以將儲存在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]執行個體、檔案系統或 [!INCLUDE[ssIS](../includes/ssis-md.md)] 封裝存放區內的封裝匯出至不同的儲存格式和位置。</span><span class="sxs-lookup"><span data-stu-id="22383-125">You can export a package that is stored in an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], the file system, or the [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Store to a different storage format and location.</span></span>  
  
 <span data-ttu-id="22383-126">不過，在不同的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]版本之間匯入和匯出封裝有一些限制：</span><span class="sxs-lookup"><span data-stu-id="22383-126">However, there are some restrictions on importing and exporting a package between different versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="22383-127">在 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]的執行個體上，雖然您可以從 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]的執行個體匯入封裝，但是無法將封裝匯出至 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="22383-127">On an instance of [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], you can import packages from an instance of [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], but you cannot export packages to an instance of [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)].</span></span>  
  
-   <span data-ttu-id="22383-128">在 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]的執行個體上，您無法在 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]的執行個體之間匯入封裝或匯出封裝。</span><span class="sxs-lookup"><span data-stu-id="22383-128">On an instance of [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], you cannot import packages from, or export packages to, an instance of [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].</span></span>  
  
 <span data-ttu-id="22383-129">下列程序將描述如何使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 來匯入或匯出封裝。</span><span class="sxs-lookup"><span data-stu-id="22383-129">The following procedures describe how to use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to import or export a package.</span></span>  
  
#### <a name="to-import-a-package-by-using-sql-server-management-studio"></a><span data-ttu-id="22383-130">使用 SQL Server Management Studio 來匯入封裝</span><span class="sxs-lookup"><span data-stu-id="22383-130">To import a package by Using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="22383-131">按一下 [開始]  、指向 Microsoft  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]，然後按一下 [SQL Server Management Studio]  。</span><span class="sxs-lookup"><span data-stu-id="22383-131">Click **Start**, point to **Microsoft** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="22383-132">在 [連接到伺服器]  對話方塊上，設定下列選項：</span><span class="sxs-lookup"><span data-stu-id="22383-132">In the **Connect to Server** dialog box set the following options:</span></span>  
  
    -   <span data-ttu-id="22383-133">在 [伺服器類型]  方塊中，選取 [Integration Services]  。</span><span class="sxs-lookup"><span data-stu-id="22383-133">In the **Server type** box, select **Integration Services**.</span></span>  
  
    -   <span data-ttu-id="22383-134">在 [伺服器名稱] 方塊中，提供伺服器名稱，或按一下 [\<Browse for more...>] 並尋找要使用的伺服器。</span><span class="sxs-lookup"><span data-stu-id="22383-134">In the **Server name** box, provide a server name or click **\<Browse for more...>** and locate the server to use.</span></span>  
  
3.  <span data-ttu-id="22383-135">如果物件總管尚未開啟，請在 [檢視]  功能表上，按一下物件總管  。</span><span class="sxs-lookup"><span data-stu-id="22383-135">If Object Explorer is not open, on the **View** menu, click **Object Explorer**.</span></span>  
  
4.  <span data-ttu-id="22383-136">在物件總管中，展開 [存放的封裝]  資料夾。</span><span class="sxs-lookup"><span data-stu-id="22383-136">In Object Explorer, expand the **Stored Packages** folder.</span></span>  
  
5.  <span data-ttu-id="22383-137">展開子資料夾以尋找您要匯入封裝的資料夾。</span><span class="sxs-lookup"><span data-stu-id="22383-137">Expand the subfolders to locate the folder into which you want to import a package.</span></span>  
  
6.  <span data-ttu-id="22383-138">以滑鼠右鍵按一下資料夾，然後按一下 [匯入封裝]  。</span><span class="sxs-lookup"><span data-stu-id="22383-138">Right-click the folder, click **Import Package**.</span></span> <span data-ttu-id="22383-139">然後執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="22383-139">and then do one of the following:</span></span>  
  
    -   <span data-ttu-id="22383-140">若要從 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體匯入，請選取 [SQL Server]  選項，然後指定伺服器並選取驗證模式。</span><span class="sxs-lookup"><span data-stu-id="22383-140">To import from an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], select the **SQL Server** option, and then specify the server and select the authentication mode.</span></span> <span data-ttu-id="22383-141">如果選取 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證，請提供使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="22383-141">If you select [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a user name and a password.</span></span>  
  
         <span data-ttu-id="22383-142">按一下瀏覽按鈕 ([...])  ，選取要匯入的封裝，然後按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="22383-142">Click the browse button **(...)**, select the package to import, and then click **OK.**</span></span>  
  
    -   <span data-ttu-id="22383-143">若要從檔案系統匯入，請選取 [檔案系統]  選項。</span><span class="sxs-lookup"><span data-stu-id="22383-143">To import from the file system, select the **File system** option.</span></span>  
  
         <span data-ttu-id="22383-144">按一下瀏覽按鈕 ([...])  ，選取要匯入的封裝，然後按一下 [開啟]  。</span><span class="sxs-lookup"><span data-stu-id="22383-144">Click the browse button **(...)**, select the package to import, and then click **Open.**</span></span>  
  
    -   <span data-ttu-id="22383-145">若要從 [!INCLUDE[ssIS](../includes/ssis-md.md)] 封裝存放區匯入，請選取 [SSIS 封裝存放區]  選項並指定伺服器。</span><span class="sxs-lookup"><span data-stu-id="22383-145">To import from the [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Store, select the **SSIS Package Store** option and specify the server.</span></span>  
  
         <span data-ttu-id="22383-146">按一下瀏覽按鈕 ([...])  ，選取要匯入的封裝，然後按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="22383-146">Click the browse button **(...)**, select the package to import, and then click **OK.**</span></span>  
  
7.  <span data-ttu-id="22383-147">(選擇性) 更新封裝名稱。</span><span class="sxs-lookup"><span data-stu-id="22383-147">Optionally, update the package name.</span></span>  
  
8.  <span data-ttu-id="22383-148">若要更新封裝的保護等級，請按一下瀏覽按鈕 ([...])  ，並使用 [封裝保護等級]  對話方塊選擇其他保護等級。</span><span class="sxs-lookup"><span data-stu-id="22383-148">To update the protection level of the package, click the browse button **(...)** and choose a different protection level by using the **Package Protection Level** dialog box.</span></span> <span data-ttu-id="22383-149">如果選取 [機密資料以密碼加密]  或 [所有資料以密碼加密]  選項，請鍵入並確認密碼。</span><span class="sxs-lookup"><span data-stu-id="22383-149">If the **Encrypt sensitive data with password** or the **Encrypt all data with password** option is selected, type and confirm a password.</span></span>  
  
9. <span data-ttu-id="22383-150">按一下 [確定]  以完成匯入。</span><span class="sxs-lookup"><span data-stu-id="22383-150">Click **OK** to complete the import.</span></span>  
  
#### <a name="to-export-a-package-by-using-sql-server-management-studio"></a><span data-ttu-id="22383-151">使用 SQL Server Management Studio 來匯出封裝</span><span class="sxs-lookup"><span data-stu-id="22383-151">To export a package by Using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="22383-152">按一下 [開始]  、指向 Microsoft  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]，然後按一下 [SQL Server Management Studio]  。</span><span class="sxs-lookup"><span data-stu-id="22383-152">Click **Start**, point to **Microsoft** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="22383-153">在 [連接到伺服器]  對話方塊上，設定下列選項：</span><span class="sxs-lookup"><span data-stu-id="22383-153">In the **Connect to Server** dialog box, set the following options:</span></span>  
  
    -   <span data-ttu-id="22383-154">在 [伺服器類型]  方塊中，選取 [Integration Services]  。</span><span class="sxs-lookup"><span data-stu-id="22383-154">In the **Server type** box, select **Integration Services**.</span></span>  
  
    -   <span data-ttu-id="22383-155">在 [伺服器名稱] 方塊中，提供伺服器名稱，或按一下 [\<Browse for more...>] 並尋找要使用的伺服器。</span><span class="sxs-lookup"><span data-stu-id="22383-155">In the **Server name** box, provide a server name or click **\<Browse for more...>** and locate the server to use.</span></span>  
  
3.  <span data-ttu-id="22383-156">如果物件總管尚未開啟，請在 [檢視]  功能表上，按一下物件總管  。</span><span class="sxs-lookup"><span data-stu-id="22383-156">If Object Explorer is not open, on the **View** menu, click **Object Explorer**.</span></span>  
  
4.  <span data-ttu-id="22383-157">在物件總管中，展開 [存放的封裝]  資料夾。</span><span class="sxs-lookup"><span data-stu-id="22383-157">In Object Explorer, expand the **Stored Packages** folder.</span></span>  
  
5.  <span data-ttu-id="22383-158">展開子資料夾，以找出您要匯出的封裝。</span><span class="sxs-lookup"><span data-stu-id="22383-158">Expand the subfolders to locate the package you want to export.</span></span>  
  
6.  <span data-ttu-id="22383-159">以滑鼠右鍵按一下封裝，再按一下 [匯出]  ，然後執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="22383-159">Right-click the package, click **Export**, and then do one of the following:</span></span>  
  
    -   <span data-ttu-id="22383-160">若要匯出至 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的執行個體，請選取 [SQL Server]  選項，然後指定伺服器並選取驗證模式。</span><span class="sxs-lookup"><span data-stu-id="22383-160">To export to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], select the **SQL Server** option, and then specify the server and select the authentication mode.</span></span> <span data-ttu-id="22383-161">如果選取 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證，請提供使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="22383-161">If you select [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a user name and a password.</span></span>  
  
         <span data-ttu-id="22383-162">按一下瀏覽按鈕 ([...])  並展開 [SSIS 封裝]  資料夾，以找出您要儲存封裝的資料夾。</span><span class="sxs-lookup"><span data-stu-id="22383-162">Click the browse button **(...)**, and expand the **SSIS Packages** folder to locate the folder to which you want to save the package.</span></span> <span data-ttu-id="22383-163">(選擇性) 更新封裝的預設名稱並按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="22383-163">Optionally, update the default name of the package, and then click **OK**.</span></span>  
  
    -   <span data-ttu-id="22383-164">若要匯出至檔案系統，請選取 [檔案系統]  選項。</span><span class="sxs-lookup"><span data-stu-id="22383-164">To export to the file system, select the **File System** option.</span></span>  
  
         <span data-ttu-id="22383-165">按一下瀏覽按鈕 ([...])  找出您要匯出封裝的目標資料夾、輸入封裝檔案的名稱，然後按一下 [儲存]  。</span><span class="sxs-lookup"><span data-stu-id="22383-165">Click the browse button **(...)** to locate the folder to which you want to export the package, type the name of the package file, and then click **Save.**</span></span>  
  
    -   <span data-ttu-id="22383-166">若要匯出至 [!INCLUDE[ssIS](../includes/ssis-md.md)] 封裝存放區，請選取 [SSIS 封裝存放區]  選項，並指定伺服器。</span><span class="sxs-lookup"><span data-stu-id="22383-166">To export to the [!INCLUDE[ssIS](../includes/ssis-md.md)] package store, select the **SSIS Package Store** option, and specify the server.</span></span>  
  
         <span data-ttu-id="22383-167">按一下瀏覽按鈕 ([...])  ，展開 [SSIS 封裝]  資料夾，並選取您要儲存封裝的資料夾。</span><span class="sxs-lookup"><span data-stu-id="22383-167">Click the browse button **(...)**, expand the **SSIS Packages** folder, and select the folder to which you want to save the package.</span></span> <span data-ttu-id="22383-168">(選擇性) 在 [封裝名稱]  文字方塊中輸入封裝的新名稱。</span><span class="sxs-lookup"><span data-stu-id="22383-168">Optionally, enter a new name for the package in the **Package Name** text box.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="22383-169">若要更新封裝的保護等級，請按一下瀏覽按鈕 ([...])  ，並使用 [封裝保護等級]  對話方塊選擇其他保護等級。</span><span class="sxs-lookup"><span data-stu-id="22383-169">To update the protection level of the package, click the browse button **(...)** and choose a different protection level by using the **Package Protection Level** dialog box.</span></span> <span data-ttu-id="22383-170">如果選取 [機密資料以密碼加密]  或 [所有資料以密碼加密]  選項，請鍵入並確認密碼。</span><span class="sxs-lookup"><span data-stu-id="22383-170">If the **Encrypt sensitive data with password** or the **Encrypt all data with password** option is selected, type and confirm a password.</span></span>  
  
8.  <span data-ttu-id="22383-171">按一下 [確定]  以完成匯出。</span><span class="sxs-lookup"><span data-stu-id="22383-171">Click **OK** to complete the export.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22383-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22383-172">See Also</span></span>  
 [<span data-ttu-id="22383-173">封裝管理 &#40;SSIS 服務&#41;</span><span class="sxs-lookup"><span data-stu-id="22383-173">Package Management &#40;SSIS Service&#41;</span></span>](service/package-management-ssis-service.md)  
  
  
