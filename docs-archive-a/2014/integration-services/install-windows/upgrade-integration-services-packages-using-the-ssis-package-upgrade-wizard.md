---
title: 使用 SSIS 封裝升級精靈來升級 Integration Services 封裝 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, upgrading
- upgrading Integration Services packages
ms.assetid: 9359275a-48f5-4d1e-8ae7-e797759e3ccf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bcafd1c9750d8333639ca2d315512a2c2b8759c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596189"
---
# <a name="upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard"></a><span data-ttu-id="c0795-102">使用 SSIS 封裝升級精靈來升級 Integration Services 封裝</span><span class="sxs-lookup"><span data-stu-id="c0795-102">Upgrade Integration Services Packages Using the SSIS Package Upgrade Wizard</span></span>
  <span data-ttu-id="c0795-103">您可以升級以舊版 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 所建立的封裝，至 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 所使用的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 格式。</span><span class="sxs-lookup"><span data-stu-id="c0795-103">You can upgrade packages that were created in earlier versions of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] format that [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] uses.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c0795-104">提供 [ [!INCLUDE[ssIS](../../includes/ssis-md.md)] 封裝升級精靈] 協助完成此程序。</span><span class="sxs-lookup"><span data-stu-id="c0795-104">provides the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard to help in this process.</span></span> <span data-ttu-id="c0795-105">因為您可以將精靈設定成備份原始封裝，所以如果您遇到升級問題，就可以繼續使用原始封裝。</span><span class="sxs-lookup"><span data-stu-id="c0795-105">Because you can configure the wizard to backup up your original packages, you can continue to use the original packages if you experience upgrade difficulties.</span></span>  
  
 <span data-ttu-id="c0795-106">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 封裝升級精靈是在安裝 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 時安裝的。</span><span class="sxs-lookup"><span data-stu-id="c0795-106">The [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard is installed when [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] is installed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c0795-107">您可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 的 Standard、Enterprise 和 Developer Edition 中使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]封裝升級精靈。</span><span class="sxs-lookup"><span data-stu-id="c0795-107">The [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard is available in the Standard, Enterprise, and Developer Editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="c0795-108">如需如何升級 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝的詳細資訊，請參閱 [升級 Integration Services 封裝](upgrade-integration-services-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="c0795-108">For more information about how to upgrade [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, see [Upgrade Integration Services Packages](upgrade-integration-services-packages.md).</span></span>  
  
 <span data-ttu-id="c0795-109">本主題的其餘部分描述的是如何執行此精靈以及備份原始封裝。</span><span class="sxs-lookup"><span data-stu-id="c0795-109">The remainder of this topic describes how to run the wizard and back up the original packages.</span></span>  
  
## <a name="running-the-ssis-package-upgrade-wizard"></a><span data-ttu-id="c0795-110">執行 SSIS 封裝升級精靈</span><span class="sxs-lookup"><span data-stu-id="c0795-110">Running the SSIS Package Upgrade Wizard</span></span>  
 <span data-ttu-id="c0795-111">您可以從 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 、從 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]或在命令提示字元中執行 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]封裝升級精靈。</span><span class="sxs-lookup"><span data-stu-id="c0795-111">You can run the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard from [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], or at the command prompt.</span></span>  
  
#### <a name="to-run-the-wizard-from-sql-server-data-tools"></a><span data-ttu-id="c0795-112">若要從 SQL Server 資料工具執行此精靈</span><span class="sxs-lookup"><span data-stu-id="c0795-112">To run the wizard from SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="c0795-113">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，建立或開啟 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="c0795-113">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], create or open an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="c0795-114">在方案總管中，以滑鼠右鍵按一下 [SSIS 封裝]  節點，然後按一下 [升級所有封裝]  ，即可升級這個節點底下的所有封裝。</span><span class="sxs-lookup"><span data-stu-id="c0795-114">In Solution Explorer, right-click the **SSIS Packages** node, and then click **Upgrade All Packages** to upgrade all the packages under this node.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c0795-115">當您開啟包含 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 或 [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] 封裝的 [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] 專案時，[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 會自動開啟 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 封裝升級精靈。</span><span class="sxs-lookup"><span data-stu-id="c0795-115">When you open an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] or [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] packages, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] automatically opens the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard.</span></span>  
  
#### <a name="to-run-the-wizard-from-sql-server-management-studio"></a><span data-ttu-id="c0795-116">從 SQL Server Management Studio 執行此精靈</span><span class="sxs-lookup"><span data-stu-id="c0795-116">To run the wizard from SQL Server Management Studio</span></span>  
  
-   <span data-ttu-id="c0795-117">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，連接至 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]，展開 [存放的封裝]  節點，以滑鼠右鍵按一下 [檔案系統]  或 [MSDB]  節點，然後按一下 [升級封裝]  。</span><span class="sxs-lookup"><span data-stu-id="c0795-117">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], expand the **Stored Packages** node, and right-click the **File System** or **MSDB** node, and then click **Upgrade Packages**.</span></span>  
  
#### <a name="to-run-the-wizard-at-the-command-prompt"></a><span data-ttu-id="c0795-118">在命令提示字元中執行此精靈</span><span class="sxs-lookup"><span data-stu-id="c0795-118">To run the wizard at the command prompt</span></span>  
  
-   <span data-ttu-id="c0795-119">在命令提示字元中，從**C:\Program FILES\MICROSOFT SQL Server\120\DTS\Binn**資料夾執行 SSISUpgrade.exe 檔案。</span><span class="sxs-lookup"><span data-stu-id="c0795-119">At the command prompt, run the SSISUpgrade.exe file from the **C:\Program Files\Microsoft SQL Server\120\DTS\Binn** folder.</span></span>  
  
## <a name="backing-up-the-original-packages"></a><span data-ttu-id="c0795-120">備份原始封裝</span><span class="sxs-lookup"><span data-stu-id="c0795-120">Backing Up the Original Packages</span></span>  
 <span data-ttu-id="c0795-121">若要備份原始封裝，原始封裝和升級封裝都必須存放在檔案系統的相同資料夾中。</span><span class="sxs-lookup"><span data-stu-id="c0795-121">To back up the original packages, both the original packages and the upgraded packages must be stored in the same folder in the file system.</span></span> <span data-ttu-id="c0795-122">根據您執行此精靈的方式，系統可能會自動選取這個儲存位置。</span><span class="sxs-lookup"><span data-stu-id="c0795-122">Depending on how you run the wizard, this storage location might be automatically selected.</span></span>  
  
-   <span data-ttu-id="c0795-123">當您從 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 執行 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]封裝升級精靈時，此精靈會自動將原始封裝和升級封裝都存放在檔案系統的相同資料夾中。</span><span class="sxs-lookup"><span data-stu-id="c0795-123">When you run the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard from [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], the wizard automatically stores both the original packages and upgraded packages in the same folder in the file system.</span></span>  
  
-   <span data-ttu-id="c0795-124">當您從 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 或在命令提示字元中執行 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 封裝升級精靈時，就可以針對原始和升級封裝指定不同的儲存位置。</span><span class="sxs-lookup"><span data-stu-id="c0795-124">When you run the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or at the command prompt, you can specify different storage locations for the original and upgraded packages.</span></span> <span data-ttu-id="c0795-125">若要備份原始封裝，請務必指定原始封裝和升級封裝都存放在檔案系統的相同資料夾中。</span><span class="sxs-lookup"><span data-stu-id="c0795-125">To back up the original packages, make sure to specify that both the original and upgraded packages are stored in the same folder in the file system.</span></span> <span data-ttu-id="c0795-126">如果您指定任何其他儲存選項，此精靈將無法備份原始封裝。</span><span class="sxs-lookup"><span data-stu-id="c0795-126">If you specify any other storage options, the wizard will not be able to back up the original packages.</span></span>  
  
 <span data-ttu-id="c0795-127">當此精靈備份原始封裝時，它會將原始封裝的複本存放在 [SSISBackupFolder]  資料夾中。</span><span class="sxs-lookup"><span data-stu-id="c0795-127">When the wizard backs up the original packages, the wizard stores a copy of the original packages in an **SSISBackupFolder** folder.</span></span> <span data-ttu-id="c0795-128">此精靈會將這個 [SSISBackupFolder]  資料夾建立為包含原始封裝和升級封裝之資料夾的子資料夾。</span><span class="sxs-lookup"><span data-stu-id="c0795-128">The wizard creates this **SSISBackupFolder** folder as a subfolder to the folder that contains the original packages and the upgraded packages.</span></span>  
  
#### <a name="to-back-up-the-original-packages-in-sql-server-management-studio-or-at-the-command-prompt"></a><span data-ttu-id="c0795-129">在 SQL Server Management Studio 或命令提示字元中備份原始封裝</span><span class="sxs-lookup"><span data-stu-id="c0795-129">To back up the original packages in SQL Server Management Studio or at the command prompt</span></span>  
  
1.  <span data-ttu-id="c0795-130">將原始封裝儲存到檔案系統上的位置。</span><span class="sxs-lookup"><span data-stu-id="c0795-130">Save the original packages to a location on the file system.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c0795-131">此精靈中的備份選項只能搭配已經存放至檔案系統的封裝運作。</span><span class="sxs-lookup"><span data-stu-id="c0795-131">The backup option in the wizard only works with packages that have been stored to the file system.</span></span>  
  
2.  <span data-ttu-id="c0795-132">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或命令提示字元中，執行 [ [!INCLUDE[ssIS](../../includes/ssis-md.md)] 封裝升級精靈]。</span><span class="sxs-lookup"><span data-stu-id="c0795-132">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or at the command prompt, run the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard.</span></span>  
  
3.  <span data-ttu-id="c0795-133">在此精靈的 [選取來源位置]  頁面上，將 [封裝來源]  屬性設定為 [檔案系統]  。</span><span class="sxs-lookup"><span data-stu-id="c0795-133">On the **Select Source Location** page of the wizard, set the **Package source** property to **File System**.</span></span>  
  
4.  <span data-ttu-id="c0795-134">在此精靈的 [選取目的地位置]  頁面上，選取 [儲存至來源位置]  ，即可將升級封裝儲存至與原始封裝相同的位置。</span><span class="sxs-lookup"><span data-stu-id="c0795-134">On the **Select Destination Location** page of the wizard, select **Save to source location** tosave the upgraded packages to the same location as the original packages.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c0795-135">只有當升級封裝與原始封裝都存放在相同的資料夾時，您才能使用此精靈的備份選項。</span><span class="sxs-lookup"><span data-stu-id="c0795-135">The backup option in the wizard is available only when the upgraded packages are stored in the same folder as the original packages.</span></span>  
  
5.  <span data-ttu-id="c0795-136">在此精靈的 [選取封裝管理選項]  頁面上，選取 [備份原始封裝]  選項。</span><span class="sxs-lookup"><span data-stu-id="c0795-136">On the **Select Package Management Options** page of the wizard, select the **Backup original packages** option.</span></span>  
  
#### <a name="to-back-up-the-original-packages-in-sql-server-data-tools"></a><span data-ttu-id="c0795-137">若要在 SQL Server 資料工具中備份原始封裝</span><span class="sxs-lookup"><span data-stu-id="c0795-137">To back up the original packages in SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="c0795-138">將原始封裝儲存到檔案系統上的位置。</span><span class="sxs-lookup"><span data-stu-id="c0795-138">Save the original packages to a location on the file system.</span></span>  
  
2.  <span data-ttu-id="c0795-139">在此精靈的 [選取封裝管理選項]  頁面上，選取 [備份原始封裝]  選項。</span><span class="sxs-lookup"><span data-stu-id="c0795-139">On the **Select Package Management Options** page of the wizard, select the **Backup original packages** option.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="c0795-140">當您在中開啟或專案時，不會顯示 [**備份原始封裝**] 選項 [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ，而這會自動啟動精靈。</span><span class="sxs-lookup"><span data-stu-id="c0795-140">The **Backup original packages** option is not displayed when you open a [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] or [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], which automatically launches the wizard.</span></span>  
  
3.  <span data-ttu-id="c0795-141">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，執行 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 封裝升級精靈。</span><span class="sxs-lookup"><span data-stu-id="c0795-141">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], run the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Upgrade Wizard.</span></span>  
  
  
