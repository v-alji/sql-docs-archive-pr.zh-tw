---
title: 套件設定召集人 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.packageconfigurationorganizer.f1
helpviewer_keywords:
- Package Configurations Organizer dialog box
ms.assetid: f20ae6cb-9e6a-4d24-88ff-d7a903a4e8d3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 67fdc9ca0faeff57c18fdb6e4d10acca3e9963f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705258"
---
# <a name="package-configurations-organizer"></a><span data-ttu-id="fa602-102">[封裝組態組合管理]</span><span class="sxs-lookup"><span data-stu-id="fa602-102">Package Configurations Organizer</span></span>
  <span data-ttu-id="fa602-103">使用 **[封裝組態組合管理]** 對話方塊，即可啟用封裝組態、檢視目前封裝的組態清單，以及指定載入組態的喜好順序。</span><span class="sxs-lookup"><span data-stu-id="fa602-103">Use the **Package Configurations Organizer** dialog box to enable package configurations, view a list of configurations for the current package, and specify the preferred order in which the configurations should be loaded.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fa602-104">組態可用於封裝部署模型。</span><span class="sxs-lookup"><span data-stu-id="fa602-104">Configurations are available for the package deployment model.</span></span> <span data-ttu-id="fa602-105">參數是用來取代專案部署模型的組態。</span><span class="sxs-lookup"><span data-stu-id="fa602-105">Parameters are used in place of configurations for the project deployment model.</span></span> <span data-ttu-id="fa602-106">專案部署模型讓您能將 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 伺服器。</span><span class="sxs-lookup"><span data-stu-id="fa602-106">The project deployment model enables you to deploy [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="fa602-107">如需有關部署模型的詳細資訊，請參閱＜ [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md)＞。</span><span class="sxs-lookup"><span data-stu-id="fa602-107">For more information about the deployment models, see [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md).</span></span>  
  
 <span data-ttu-id="fa602-108">如果組態更新相同的屬性，列於組態清單較下面的組態值會取代清單中較上面的組態值。</span><span class="sxs-lookup"><span data-stu-id="fa602-108">If multiple configurations update the same property, values from configurations listed lower in the configuration list will replace values from configurations higher in the list.</span></span> <span data-ttu-id="fa602-109">載入屬性的最後一個值是封裝執行時所使用的值。</span><span class="sxs-lookup"><span data-stu-id="fa602-109">The last value loaded into the property is the value that is used when the package runs.</span></span> <span data-ttu-id="fa602-110">此外，如果封裝使用如 XML 組態檔案等直接組態以及如環境變數等間接組態的組合，則指向直接組態位置的間接組態必須是清單中較上面的部份。</span><span class="sxs-lookup"><span data-stu-id="fa602-110">Also, if the package uses a combination of direct configuration such as an XML configuration file and an indirect configuration such as an environment variable, the indirect configuration that points to the location of the direct configuration must be higher in the list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fa602-111">以喜好的順序載入封裝組態時，組態會根據 **[封裝組態組合管理]** 對話方塊中清單顯示的順序 (由上而下) 依序載入。</span><span class="sxs-lookup"><span data-stu-id="fa602-111">When package configurations load in the preferred order, configurations load from the top of the list shown in the **Package Configuration Organizer** dialog box to the bottom of the list.</span></span> <span data-ttu-id="fa602-112">不過，在執行階段，封裝組態可能不會以喜好的順序載入。</span><span class="sxs-lookup"><span data-stu-id="fa602-112">However, at run time, package configurations might not load in the preferred order.</span></span> <span data-ttu-id="fa602-113">特別是，父封裝組態會在其他類型的組態後面載入。</span><span class="sxs-lookup"><span data-stu-id="fa602-113">In particular, Parent Package Configurations load after configurations of other types.</span></span>  
  
 <span data-ttu-id="fa602-114">封裝組態會在執行階段更新封裝物件的屬性值。</span><span class="sxs-lookup"><span data-stu-id="fa602-114">Package configurations update the values of properties of package objects at run time.</span></span> <span data-ttu-id="fa602-115">載入封裝時，組態值將會取代開發封裝時所設定的值。</span><span class="sxs-lookup"><span data-stu-id="fa602-115">When a package is loaded, the values from the configurations replace the values that were set when the package was developed.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="fa602-116">支援不同的組態類型。</span><span class="sxs-lookup"><span data-stu-id="fa602-116">supports different configuration types.</span></span> <span data-ttu-id="fa602-117">例如，您可以使用包含多個組態的 XML 檔案，或是包含單一組態的環境變數。</span><span class="sxs-lookup"><span data-stu-id="fa602-117">For example, you can use an XML file that can contain multiple configurations, or an environment variable that contains a single configuration.</span></span> <span data-ttu-id="fa602-118">如需相關資訊，請參閱 [Package Configurations](../../2014/integration-services/package-configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="fa602-118">For more information, see [Package Configurations](../../2014/integration-services/package-configurations.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="fa602-119">選項。</span><span class="sxs-lookup"><span data-stu-id="fa602-119">Options</span></span>  
 <span data-ttu-id="fa602-120">**啟用封裝組態**</span><span class="sxs-lookup"><span data-stu-id="fa602-120">**Enable package configurations**</span></span>  
 <span data-ttu-id="fa602-121">選取即可使用封裝的組態。</span><span class="sxs-lookup"><span data-stu-id="fa602-121">Select to use configurations with the package.</span></span>  
  
 <span data-ttu-id="fa602-122">**組態名稱**</span><span class="sxs-lookup"><span data-stu-id="fa602-122">**Configuration Name**</span></span>  
 <span data-ttu-id="fa602-123">檢視組態的名稱。</span><span class="sxs-lookup"><span data-stu-id="fa602-123">View the name of the configuration.</span></span>  
  
 <span data-ttu-id="fa602-124">**組態類型**</span><span class="sxs-lookup"><span data-stu-id="fa602-124">**Configuration Type**</span></span>  
 <span data-ttu-id="fa602-125">檢視儲存組態的位置類型。</span><span class="sxs-lookup"><span data-stu-id="fa602-125">View the type of the location where configurations are stored.</span></span>  
  
 <span data-ttu-id="fa602-126">**組態字串**</span><span class="sxs-lookup"><span data-stu-id="fa602-126">**Configuration String**</span></span>  
 <span data-ttu-id="fa602-127">檢視儲存組態值的位置。</span><span class="sxs-lookup"><span data-stu-id="fa602-127">View the location where the configuration values are stored.</span></span> <span data-ttu-id="fa602-128">位置可以是檔案的路徑、環境變數的名稱、父封裝變數的名稱、登錄機碼，或是 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="fa602-128">The location can be the path of a file, the name of an environment variable, the name of a parent package variable, a Registry key, or the name of a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="fa602-129">**目標物件**</span><span class="sxs-lookup"><span data-stu-id="fa602-129">**Target Object**</span></span>  
 <span data-ttu-id="fa602-130">檢視組態所更新之物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="fa602-130">View the name of the object that the configuration updates.</span></span> <span data-ttu-id="fa602-131">如果組態是 XML 組態檔或 SQL Server 資料表，則資料行是空白的，因為該組態可包含多個物件。</span><span class="sxs-lookup"><span data-stu-id="fa602-131">If the configuration is an XML configuration file or a SQL Server table, the column is blank because the configuration can include multiple objects.</span></span>  
  
 <span data-ttu-id="fa602-132">**目標屬性**</span><span class="sxs-lookup"><span data-stu-id="fa602-132">**Target Property**</span></span>  
 <span data-ttu-id="fa602-133">檢視組態所修改之屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="fa602-133">View the name of the property modified by the configuration.</span></span> <span data-ttu-id="fa602-134">如果組態類型支援多個組態，則此資料行是空白。</span><span class="sxs-lookup"><span data-stu-id="fa602-134">This column is blank if the configuration type supports multiple configurations.</span></span>  
  
 <span data-ttu-id="fa602-135">**加入**</span><span class="sxs-lookup"><span data-stu-id="fa602-135">**Add**</span></span>  
 <span data-ttu-id="fa602-136">使用封裝組態精靈來加入組態。</span><span class="sxs-lookup"><span data-stu-id="fa602-136">Add a configuration by using the Package Configuration Wizard.</span></span>  
  
 <span data-ttu-id="fa602-137">**編輯**</span><span class="sxs-lookup"><span data-stu-id="fa602-137">**Edit**</span></span>  
 <span data-ttu-id="fa602-138">重新執行封裝組態精靈來編輯現有的組態。</span><span class="sxs-lookup"><span data-stu-id="fa602-138">Edit an existing configuration by rerunning the Package Configuration Wizard.</span></span>  
  
 <span data-ttu-id="fa602-139">**移除**</span><span class="sxs-lookup"><span data-stu-id="fa602-139">**Remove**</span></span>  
 <span data-ttu-id="fa602-140">選取組態，然後按一下 [移除]  。</span><span class="sxs-lookup"><span data-stu-id="fa602-140">Select a configuration, and then click **Remove**.</span></span>  
  
 <span data-ttu-id="fa602-141">**箭頭**</span><span class="sxs-lookup"><span data-stu-id="fa602-141">**Arrows**</span></span>  
 <span data-ttu-id="fa602-142">選取組態，然後使用向上和向下箭頭，即可將其在清單中向上移動或向下移動。</span><span class="sxs-lookup"><span data-stu-id="fa602-142">Select a configuration and use the up and down arrows to move it up or down in the list.</span></span> <span data-ttu-id="fa602-143">組態會依其出現在清單中的順序載入。</span><span class="sxs-lookup"><span data-stu-id="fa602-143">Configurations are loaded in the sequence in which they appear in the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa602-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa602-144">See Also</span></span>  
 [<span data-ttu-id="fa602-145">建立套件設定</span><span class="sxs-lookup"><span data-stu-id="fa602-145">Create Package Configurations</span></span>](../../2014/integration-services/create-package-configurations.md)  
  
  
