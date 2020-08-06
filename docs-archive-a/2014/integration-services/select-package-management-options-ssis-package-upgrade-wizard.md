---
title: 選取 [套件管理選項] (SSIS 封裝升級嚮導]) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.is.upgradewizard.selectpackagemgtoptions.f1
ms.assetid: 810fc020-51cd-43ed-9f35-af99b4f35947
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b5113ad5a1f6758a75742ca58aef04ce92168649
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606972"
---
# <a name="select-package-management-options-ssis-package-upgrade-wizard"></a><span data-ttu-id="e4b9b-102">選取封裝管理選項 (SSIS 封裝升級精靈)</span><span class="sxs-lookup"><span data-stu-id="e4b9b-102">Select Package Management Options (SSIS Package Upgrade Wizard)</span></span>
  <span data-ttu-id="e4b9b-103">使用 [選取封裝管理選項]  頁面，指定用來升級封裝的選項。</span><span class="sxs-lookup"><span data-stu-id="e4b9b-103">Use the **Select Package Management Options** page to specify options for upgrading packages.</span></span>  
  
 <span data-ttu-id="e4b9b-104">**執行 SSIS 封裝升級精靈**</span><span class="sxs-lookup"><span data-stu-id="e4b9b-104">**To run the SSIS Package Upgrade Wizard**</span></span>  
  
-   [<span data-ttu-id="e4b9b-105">使用 SSIS 套件升級精靈來升級 Integration Services 套件</span><span class="sxs-lookup"><span data-stu-id="e4b9b-105">Upgrade Integration Services Packages Using the SSIS Package Upgrade Wizard</span></span>](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)  
  
## <a name="options"></a><span data-ttu-id="e4b9b-106">選項。</span><span class="sxs-lookup"><span data-stu-id="e4b9b-106">Options</span></span>  
 <span data-ttu-id="e4b9b-107">**更新連接字串以使用新的提供者名稱**</span><span class="sxs-lookup"><span data-stu-id="e4b9b-107">**Update connection strings to use new provider names**</span></span>  
 <span data-ttu-id="e4b9b-108">更新目前版本之 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]的連接字串，以使用下列提供者的名稱：</span><span class="sxs-lookup"><span data-stu-id="e4b9b-108">Update the connection strings to use the names for the following providers for the current release of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="e4b9b-109">OLE DB Provider for [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4b9b-109">OLE DB Provider for [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="e4b9b-110">Native Client</span><span class="sxs-lookup"><span data-stu-id="e4b9b-110">Native Client</span></span>  
  
 <span data-ttu-id="e4b9b-111">[ [!INCLUDE[ssIS](../includes/ssis-md.md)] 封裝升級精靈] 只會更新儲存在連線管理員中的連接字串。</span><span class="sxs-lookup"><span data-stu-id="e4b9b-111">The [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Upgrade Wizard updates only connection strings that are stored in connection managers.</span></span> <span data-ttu-id="e4b9b-112">此精靈不會更新使用 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 運算式語言或使用指令碼工作中之程式碼以動態方式建構的連接字串。</span><span class="sxs-lookup"><span data-stu-id="e4b9b-112">The wizard does not update connection strings that are constructed dynamically by using the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] expression language, or by using code in a Script task.</span></span>  
  
 <span data-ttu-id="e4b9b-113">**驗證升級套件**</span><span class="sxs-lookup"><span data-stu-id="e4b9b-113">**Validate upgrade packages**</span></span>  
 <span data-ttu-id="e4b9b-114">驗證升級封裝，並只儲存通過驗證的那些升級封裝。</span><span class="sxs-lookup"><span data-stu-id="e4b9b-114">Validate the upgrade packages and save only those upgrade packages that pass validation.</span></span>  
  
 <span data-ttu-id="e4b9b-115">如果您不選取這個選項，此精靈將不會驗證升級封裝。</span><span class="sxs-lookup"><span data-stu-id="e4b9b-115">If you do not select this option, the wizard will not validate upgrade packages.</span></span> <span data-ttu-id="e4b9b-116">因此，此精靈將會儲存所有的升級封裝，不論封裝是否有效。</span><span class="sxs-lookup"><span data-stu-id="e4b9b-116">Therefore, the wizard will save all upgrade packages, regardless of whether the packages are valid or not.</span></span> <span data-ttu-id="e4b9b-117">此精靈會將升級封裝儲存到精靈之 [選取目的地位置]  頁面上所指定的目的地。</span><span class="sxs-lookup"><span data-stu-id="e4b9b-117">The wizard saves upgrade packages to the destination that is specified on the **SelectDestination Location** page of the wizard.</span></span>  
  
 <span data-ttu-id="e4b9b-118">驗證會增加升級程序的時間。</span><span class="sxs-lookup"><span data-stu-id="e4b9b-118">Validation adds time to the upgrade process.</span></span> <span data-ttu-id="e4b9b-119">如果是可能會升級成功的大型封裝，我們建議您不要選取這個選項。</span><span class="sxs-lookup"><span data-stu-id="e4b9b-119">We recommend that you do not select this option for large packages that are likely to be upgraded successfully.</span></span>  
  
 <span data-ttu-id="e4b9b-120">**建立新的套件識別碼**</span><span class="sxs-lookup"><span data-stu-id="e4b9b-120">**Create new package IDs**</span></span>  
 <span data-ttu-id="e4b9b-121">為升級封裝建立新的封裝識別碼。</span><span class="sxs-lookup"><span data-stu-id="e4b9b-121">Create new package IDs for the upgrade packages.</span></span>  
  
 <span data-ttu-id="e4b9b-122">**當套件升級失敗時，繼續升級程序**</span><span class="sxs-lookup"><span data-stu-id="e4b9b-122">**Continue upgrade process when a package upgrade fails**</span></span>  
 <span data-ttu-id="e4b9b-123">指定當封裝無法升級時，[ [!INCLUDE[ssIS](../includes/ssis-md.md)] 封裝升級精靈] 應繼續升級其餘的封裝。</span><span class="sxs-lookup"><span data-stu-id="e4b9b-123">Specify that when a package cannot be upgraded, the [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Upgrade Wizard continues to upgrade the remaining packages.</span></span>  
  
 <span data-ttu-id="e4b9b-124">**套件名稱衝突**</span><span class="sxs-lookup"><span data-stu-id="e4b9b-124">**Package name conflicts**</span></span>  
 <span data-ttu-id="e4b9b-125">指定精靈應該要如何處理同名的封裝。</span><span class="sxs-lookup"><span data-stu-id="e4b9b-125">Specify how the wizard should handle packages that have the same name.</span></span> <span data-ttu-id="e4b9b-126">這個選項的值列於下表中。</span><span class="sxs-lookup"><span data-stu-id="e4b9b-126">This option has the values listed in the following table.</span></span>  
  
 <span data-ttu-id="e4b9b-127">**覆寫現有套件檔案**</span><span class="sxs-lookup"><span data-stu-id="e4b9b-127">**Overwrite existing package files**</span></span>  
 <span data-ttu-id="e4b9b-128">以同名的升級封裝取代現有的封裝。</span><span class="sxs-lookup"><span data-stu-id="e4b9b-128">Replaces the existing package with the upgrade package of the same name.</span></span>  
  
 <span data-ttu-id="e4b9b-129">**在升級套件名稱後新增數字後置字元**</span><span class="sxs-lookup"><span data-stu-id="e4b9b-129">**Add numeric suffixes to upgrade package names**</span></span>  
 <span data-ttu-id="e4b9b-130">在升級封裝名稱後加入數字後置字元。</span><span class="sxs-lookup"><span data-stu-id="e4b9b-130">Adds a numeric suffix to the name of the upgrade package.</span></span>  
  
 <span data-ttu-id="e4b9b-131">**不升級套件**</span><span class="sxs-lookup"><span data-stu-id="e4b9b-131">**Do not upgrade packages**</span></span>  
 <span data-ttu-id="e4b9b-132">停止升級封裝，並在完成精靈時顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="e4b9b-132">Stops the packages from being upgraded and displays an error when you complete the wizard.</span></span>  
  
 <span data-ttu-id="e4b9b-133">當您在精靈的 [選取目的地位置]  頁面上選取 [儲存至來源位置]  選項時，無法使用這些選項。</span><span class="sxs-lookup"><span data-stu-id="e4b9b-133">These options are not available when you select the **Save to source location** option on the **Select Destination Location** page of the wizard.</span></span>  
  
 <span data-ttu-id="e4b9b-134">**忽略設定**</span><span class="sxs-lookup"><span data-stu-id="e4b9b-134">**Ignore Configurations**</span></span>  
 <span data-ttu-id="e4b9b-135">封裝升級期間不載入封裝組態。</span><span class="sxs-lookup"><span data-stu-id="e4b9b-135">Does not load package configurations during the package upgrade.</span></span> <span data-ttu-id="e4b9b-136">選取此選項可減少升級封裝所需的時間。</span><span class="sxs-lookup"><span data-stu-id="e4b9b-136">Selecting this option reduces the time required to upgrade the package.</span></span>  
  
 <span data-ttu-id="e4b9b-137">**備份原始套件**</span><span class="sxs-lookup"><span data-stu-id="e4b9b-137">**Backup original packages**</span></span>  
 <span data-ttu-id="e4b9b-138">讓精靈將原始封裝備份到 **SSISBackupFolder** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="e4b9b-138">Have the wizard back up the original packages to an **SSISBackupFolder** folder.</span></span> <span data-ttu-id="e4b9b-139">此精靈會將 **SSISBackupFolder** 資料夾建立為包含原始封裝和升級封裝之資料夾的子資料夾。</span><span class="sxs-lookup"><span data-stu-id="e4b9b-139">The wizard creates the **SSISBackupFolder** folder as a subfolder to the folder that contains the original packages and the upgraded packages.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e4b9b-140">只有當您指定原始封裝和升級封裝儲存在檔案系統和相同的資料夾時，才可使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="e4b9b-140">This option is available only when you specify that the original packages and the upgraded packages are stored in the file system and in the same folder.</span></span>  
  
 <span data-ttu-id="e4b9b-141">如需詳細資訊，請參閱 [使用 SSIS 封裝升級精靈來升級 Integration Services 封裝](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="e4b9b-141">For more information, see [Upgrade Integration Services Packages Using the SSIS Package Upgrade Wizard](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4b9b-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4b9b-142">See Also</span></span>  
 [<span data-ttu-id="e4b9b-143">升級 Integration Services 套件</span><span class="sxs-lookup"><span data-stu-id="e4b9b-143">Upgrade Integration Services Packages</span></span>](install-windows/upgrade-integration-services-packages.md)  
  
  
