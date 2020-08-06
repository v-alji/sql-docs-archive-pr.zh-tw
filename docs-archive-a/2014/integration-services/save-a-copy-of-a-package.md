---
title: 儲存封裝的複本 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, saving
- packages [Integration Services], saving
- saving packages
- SSIS packages, saving
- SQL Server Integration Services packages, saving
ms.assetid: 21482a20-e420-4452-b7eb-8f9fa1929f31
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 02ee2374fddb7dbb6b17adc2a4a10707179c882d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698437"
---
# <a name="save-a-copy-of-a-package"></a><span data-ttu-id="52a14-102">儲存封裝的複本</span><span class="sxs-lookup"><span data-stu-id="52a14-102">Save a Copy of a Package</span></span>
  <span data-ttu-id="52a14-103">此程序描述如何將封裝的複本儲存至檔案系統、封裝存放區，或 \*\*\*\* 中的 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="52a14-103">This procedure describes how to save a copy of a package to the file system, to the package store, or to the **msdb** database in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="52a14-104">當您指定儲存封裝副本的位置時，也可以更新封裝名稱。</span><span class="sxs-lookup"><span data-stu-id="52a14-104">When you specify a location to save the package copy, you can also update the name of the package.</span></span>  
  
 <span data-ttu-id="52a14-105">封裝存放區可以包含 **msdb** 資料庫和檔案系統中的資料夾、或者只有包含 **msdb**，或只有包含檔案系統中的資料夾。</span><span class="sxs-lookup"><span data-stu-id="52a14-105">The package store can include both the **msdb** database and the folders in the file system, only **msdb**, or only folders in the file system.</span></span> <span data-ttu-id="52a14-106">在 **msdb**中，封裝是儲存至 **sysssispackages** 資料表。</span><span class="sxs-lookup"><span data-stu-id="52a14-106">In **msdb**, packages are saved to the **sysssispackages** table.</span></span> <span data-ttu-id="52a14-107">這個資料表包含了識別封裝所屬之邏輯資料夾的 **folderid** 資料行。</span><span class="sxs-lookup"><span data-stu-id="52a14-107">This table includes a **folderid** column that identifies the logical folder to which the package belongs.</span></span> <span data-ttu-id="52a14-108">邏輯資料夾會以相同的方式為 **msdb** 中所儲存的封裝提供實用的分組方法，就像檔案系統中的資料夾為檔案系統中所儲存的封裝提供實用的分組方法一樣。</span><span class="sxs-lookup"><span data-stu-id="52a14-108">The logical folders provide a useful way to group packages saved to **msdb** in the same way that folders in the file system provide a way to group packages saved to the file system.</span></span> <span data-ttu-id="52a14-109">**msdb** 中 **sysssispackagefolders** 資料表的資料列會定義資料夾。</span><span class="sxs-lookup"><span data-stu-id="52a14-109">Rows in the **sysssispackagefolders** table in **msdb** define the folders.</span></span>  
  
 <span data-ttu-id="52a14-110">如果 **msdb** 不是定義為封裝存放區的一部分，那麼當您在 **[封裝路徑]** 選項中選取 SQL Server 時，可以繼續讓封裝與現有邏輯資料夾產生關聯。</span><span class="sxs-lookup"><span data-stu-id="52a14-110">If **msdb** is not defined as part of the package store, you can continue to associate packages with existing logical folders when you select SQL Server in the **Package Path** option.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="52a14-111">您必須先在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師中開啟封裝，才能儲存封裝的副本。</span><span class="sxs-lookup"><span data-stu-id="52a14-111">The package must be opened in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer before you can save a copy of the package.</span></span>  
  
### <a name="to-save-a-copy-of-a-package"></a><span data-ttu-id="52a14-112">若要儲存封裝的副本</span><span class="sxs-lookup"><span data-stu-id="52a14-112">To save a copy of a package</span></span>  
  
1.  <span data-ttu-id="52a14-113">在 [方案總管] 中，按兩下要儲存副本的封裝。</span><span class="sxs-lookup"><span data-stu-id="52a14-113">In Solution Explorer, double-click the package of which you want to save a copy.</span></span>  
  
2.  <span data-ttu-id="52a14-114">在 [檔案] 功能表上，按一下 [將 \<package file> 的複本另存新檔]。</span><span class="sxs-lookup"><span data-stu-id="52a14-114">On the **File** menu, click **Save Copy of \<package file> As**.</span></span>  
  
3.  <span data-ttu-id="52a14-115">在 **[儲存封裝的副本]** 對話方塊中，從 **[封裝位置]** 清單選取封裝位置。</span><span class="sxs-lookup"><span data-stu-id="52a14-115">In the **Save Copy of Package** dialog box, select a package location in the **Package location** list.</span></span>  
  
4.  <span data-ttu-id="52a14-116">如果位置為 **[SQL Server]** 或 **[SSIS 封裝存放區]** ，請提供伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="52a14-116">If the location is **SQL Server** or **SSIS Package Store**, provide a server name.</span></span>  
  
5.  <span data-ttu-id="52a14-117">若要儲存至 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]，請指定驗證類型；如果使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證，請提供使用者名稱與密碼。</span><span class="sxs-lookup"><span data-stu-id="52a14-117">If saving to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], specify the authentication type and, if using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a user name and password.</span></span>  
  
6.  <span data-ttu-id="52a14-118">若要指定封裝路徑，請輸入路徑或按一下瀏覽按鈕 ([...])  指定封裝的位置。</span><span class="sxs-lookup"><span data-stu-id="52a14-118">To specify the package path, either type the path or click the browse button **(...)** to specify the location of the package.</span></span> <span data-ttu-id="52a14-119">封裝的預設名稱是 Package。</span><span class="sxs-lookup"><span data-stu-id="52a14-119">The default name of the package is Package.</span></span> <span data-ttu-id="52a14-120">您也可以選擇更新封裝名稱，以符合您的需求。</span><span class="sxs-lookup"><span data-stu-id="52a14-120">Optionally, update the package name to one that suits your needs.</span></span>  
  
     <span data-ttu-id="52a14-121">如果您選取 **[SQL Server]** 作為 **[封裝路徑]** 選項，封裝路徑會由 **msdb** 中的邏輯資料夾和封裝名稱組成。</span><span class="sxs-lookup"><span data-stu-id="52a14-121">If you select **SQL Server** as the **Package Path** option, the package path consists of logical folders in **msdb** and the package name.</span></span> <span data-ttu-id="52a14-122">例如，如果 DownloadMonthlyData 封裝與 [MSDB] 資料夾 ( **msdb**中根邏輯資料夾的預設名稱) 中的 [Finance] 資料夾關聯，則名為 DownloadMonthlyData 之封裝的封裝路徑就是 MSDB/Finance/DownloadMonthlyData</span><span class="sxs-lookup"><span data-stu-id="52a14-122">For example, if the package DownloadMonthlyData is associated with the Finance folder within the MSDB folder (the default name of the root logical folder in **msdb**), the package path for the package named DownloadMonthlyData is MSDB/Finance/DownloadMonthlyData</span></span>  
  
     <span data-ttu-id="52a14-123">如果您選取 **[SSIS 封裝存放區]** 作為 **[封裝路徑]** 選項，封裝路徑會由 Integration Services 服務所管理的資料夾組成。</span><span class="sxs-lookup"><span data-stu-id="52a14-123">If you select **SSIS Package Store** as the **Package Path** option, the package path consists of the folder that the Integration Services service manages.</span></span> <span data-ttu-id="52a14-124">例如，如果 UpdateDeductions 封裝位於服務所管理之檔案系統資料夾的 [HumanResources] 資料夾中，封裝路徑就是 /File System/HumanResources/UpdateDeductions；同樣地，如果封裝 PostResumes 是與 [MSDB] 資料夾中的 [HumanResources] 資料夾關聯，封裝路徑就是 MSDB/HumanResources/PostResumes。</span><span class="sxs-lookup"><span data-stu-id="52a14-124">For example, if the package UpdateDeductions is located in the HumanResources folder within the file system folder that the service manages, the package path is /File System/HumanResources/UpdateDeductions; likewise, if the package PostResumes is associated with the HumanResources folder within the MSDB folder, the package path is MSDB/HumanResources/PostResumes.</span></span>  
  
     <span data-ttu-id="52a14-125">如果您選取 **[檔案系統]** 作為 **[封裝路徑]** 選項，封裝路徑就是檔案系統中的位置和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="52a14-125">If you select **File System** as the **Package Path** option, the package path is the location in the file system and the file name.</span></span> <span data-ttu-id="52a14-126">例如，如果封裝名稱是 UpdateDemographics，封裝路徑就是 C:\HumanResources\Quarterly\UpdateDemographics.dtsx。</span><span class="sxs-lookup"><span data-stu-id="52a14-126">For example, if the package name is UpdateDemographics the package path is C:\HumanResources\Quarterly\UpdateDemographics.dtsx.</span></span>  
  
7.  <span data-ttu-id="52a14-127">檢閱封裝保護等級。</span><span class="sxs-lookup"><span data-stu-id="52a14-127">Review the package protection level.</span></span>  
  
8.  <span data-ttu-id="52a14-128">或者，按一下 [保護等級] 方塊旁的瀏覽按鈕 ([...])，以變更保護等級。</span><span class="sxs-lookup"><span data-stu-id="52a14-128">Optionally, click the browse button **(...)** by the **Protection level** box to change the protection level.</span></span>  
  
    -   <span data-ttu-id="52a14-129">在 **[封裝保護等級]** 對話方塊中，選取不同的保護等級。</span><span class="sxs-lookup"><span data-stu-id="52a14-129">In the **Package Protection Level** dialog box, select a different protection level.</span></span>  
  
    -   <span data-ttu-id="52a14-130">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="52a14-130">Click **OK**.</span></span>  
  
9. <span data-ttu-id="52a14-131">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="52a14-131">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52a14-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52a14-132">See Also</span></span>  
 <span data-ttu-id="52a14-133">[Integration Services &#40;SSIS&#41; 封裝](../../2014/integration-services/integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="52a14-133">[Integration Services &#40;SSIS&#41; Packages](../../2014/integration-services/integration-services-ssis-packages.md) </span></span>  
 [<span data-ttu-id="52a14-134">設定 Integration Services 服務 &#40;SSIS 服務&#41;</span><span class="sxs-lookup"><span data-stu-id="52a14-134">Configuring the Integration Services Service &#40;SSIS Service&#41;</span></span>](service/integration-services-service-ssis-service.md)  
  
  
