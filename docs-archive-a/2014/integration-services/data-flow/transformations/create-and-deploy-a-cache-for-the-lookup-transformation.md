---
title: 針對查閱轉換來建立及部署快取 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- creating cache files for Lookup transformation
- deploying cache files for Lookup transformation
- Lookup transformation cache files
ms.assetid: cedf5cad-2fac-42d0-ad91-9461e117d330
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b33b00b84f1f1448c2ee80882aedc3a330ba0a5a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584646"
---
# <a name="create-and-deploy-a-cache-for-the-lookup-transformation"></a><span data-ttu-id="cf8b7-102">針對查閱轉換來建立及部署快取</span><span class="sxs-lookup"><span data-stu-id="cf8b7-102">Create and Deploy a Cache for the Lookup Transformation</span></span>
  <span data-ttu-id="cf8b7-103">您可以針對查閱轉換建立及部署快取檔案 (.caw)。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-103">You can create and deploy a cache file (.caw) for the Lookup transformation.</span></span> <span data-ttu-id="cf8b7-104">參考資料集會儲存在快取檔案中。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-104">The reference dataset is stored in the cache file.</span></span>  
  
 <span data-ttu-id="cf8b7-105">查閱轉換會藉由聯結已連接資料來源輸入資料行中的資料與參考資料集中的資料行來執行查閱。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-105">The Lookup transformation performs lookups by joining data in input columns from a connected data source with columns in the reference dataset.</span></span>  
  
 <span data-ttu-id="cf8b7-106">您可以使用快取連接管理員和快取轉換轉換來建立快取檔案。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-106">You create a cache file by using a Cache connection manager and a Cache Transform transformation.</span></span> <span data-ttu-id="cf8b7-107">如需詳細資訊，請參閱 [快取連線管理員](../../connection-manager/cache-connection-manager.md) 和 [快取轉換](cache-transform.md)。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-107">For more information, see [Cache Connection Manager](../../connection-manager/cache-connection-manager.md) and [Cache Transform](cache-transform.md).</span></span>  
  
 <span data-ttu-id="cf8b7-108">若要深入了解查閱轉換和快取檔案，請參閱 [查閱轉換](lookup-transformation.md)。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-108">To learn more about the Lookup transformation and cache files, see [Lookup Transformation](lookup-transformation.md).</span></span>  
  
### <a name="to-create-a-cache-file"></a><span data-ttu-id="cf8b7-109">若要建立快取檔案</span><span class="sxs-lookup"><span data-stu-id="cf8b7-109">To create a cache file</span></span>  
  
1.  <span data-ttu-id="cf8b7-110">在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]中，開啟包含所要封裝的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 專案，然後再開啟封裝。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-110">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want, and then open the package.</span></span>  
  
2.  <span data-ttu-id="cf8b7-111">在 [控制流程]  索引標籤上，加入資料流程工作。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-111">On the **Control Flow** tab, add a Data Flow task.</span></span>  
  
3.  <span data-ttu-id="cf8b7-112">在 [資料流程]  索引標籤上，將「快取轉換」轉換加入至資料流程，然後將該轉換連接到資料來源。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-112">On the **Data Flow** tab, add a Cache Transform transformation to the data flow, and then connect the transformation to a data source.</span></span>  
  
     <span data-ttu-id="cf8b7-113">視需要設定資料來源。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-113">Configure the data source as needed.</span></span>  
  
4.  <span data-ttu-id="cf8b7-114">按兩下快取轉換，然後在 [快取轉換編輯器]  中，按一下 [連線管理員]  頁面上的 [新增]  ，建立新的快取連線管理員。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-114">Double-click the Cache Transform, and then in the **Cache Transformation Editor**, on the **Connection Manager** page, click **New** to create a new Cache connection manager.</span></span>  
  
5.  <span data-ttu-id="cf8b7-115">在 [快取連線管理員編輯器]  的 [一般]  索引標籤上，藉由設定下列選項，將快取連線管理員設定為儲存快取：</span><span class="sxs-lookup"><span data-stu-id="cf8b7-115">In the **Cache Connection Manager Editor**, on the **General** tab, configure the Cache connection manager to save the cache by selecting the following options:</span></span>  
  
    1.  <span data-ttu-id="cf8b7-116">選取 [使用檔案快取]  。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-116">Select **Use file cache**.</span></span>  
  
    2.  <span data-ttu-id="cf8b7-117">針對 [檔案名稱]  ，輸入檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-117">For **File name**, type the file path.</span></span>  
  
     <span data-ttu-id="cf8b7-118">系統會在執行封裝時建立該檔案。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-118">The system creates the file when you run the package.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cf8b7-119">封裝保護等級不會套用至快取檔案。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-119">The protection level of the package does not apply to the cache file.</span></span> <span data-ttu-id="cf8b7-120">如果快取檔案包含機密資訊，請使用存取控制清單 (ACL) 限制對其中儲存檔案的位置或資料夾的存取權。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-120">If the cache file contains sensitive information, use an access control list (ACL) to restrict access to the location or folder in which you store the file.</span></span> <span data-ttu-id="cf8b7-121">您應該只啟用特定帳戶的存取權。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-121">You should enable access only to certain accounts.</span></span> <span data-ttu-id="cf8b7-122">如需詳細資訊，請參閱 [對封裝使用之檔案的存取權](../../access-to-files-used-by-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-122">For more information, see [Access to Files Used by Packages](../../access-to-files-used-by-packages.md).</span></span>  
  
6.  <span data-ttu-id="cf8b7-123">按一下 [資料行]  索引標籤，然後使用 [索引位置]  選項，指定哪些資料行是索引資料行。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-123">Click the **Columns** tab, and then specify which columns are the index columns by using the **Index Position** option.</span></span>  
  
     <span data-ttu-id="cf8b7-124">如果是非索引資料行，索引位置為 0。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-124">For non-index columns, the index position is 0.</span></span> <span data-ttu-id="cf8b7-125">如果是索引資料行，則索引位置是循序的正數。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-125">For index columns, the index position is a sequential, positive number.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cf8b7-126">當查閱轉換是設定為使用快取連接管理員，則只有參考資料集中的索引資料行可以對應到輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-126">When the Lookup transformation is configured to use a Cache connection manager, only index columns in the reference dataset can be mapped to input columns.</span></span> <span data-ttu-id="cf8b7-127">而且，所有的索引資料行都必須進行對應。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-127">Also all index columns must be mapped.</span></span>  
  
     <span data-ttu-id="cf8b7-128">如需詳細資訊，請參閱 [快取連線管理員編輯器](../../cache-connection-manager-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-128">For more information, see [Cache Connection Manager Editor](../../cache-connection-manager-editor.md).</span></span>  
  
7.  <span data-ttu-id="cf8b7-129">視需要設定快取轉換。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-129">Configure the Cache Transform as needed.</span></span>  
  
     <span data-ttu-id="cf8b7-130">如需詳細資訊，請參閱[快取轉換編輯器 &#40;連線管理員頁面&#41;](../../cache-transformation-editor-connection-manager-page.md) 和[快取轉換編輯器 &#40;對應頁面&#41;](../../cache-transformation-editor-mappings-page.md)。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-130">For more information, see [Cache Transformation Editor &#40;Connection Manager Page&#41;](../../cache-transformation-editor-connection-manager-page.md) and [Cache Transformation Editor &#40;Mappings Page&#41;](../../cache-transformation-editor-mappings-page.md).</span></span>  
  
8.  <span data-ttu-id="cf8b7-131">執行封裝。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-131">Run the package.</span></span>  
  
### <a name="to-deploy-a-cache-file"></a><span data-ttu-id="cf8b7-132">若要部署快取檔案</span><span class="sxs-lookup"><span data-stu-id="cf8b7-132">To deploy a cache file</span></span>  
  
1.  <span data-ttu-id="cf8b7-133">在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]中，開啟包含所要封裝的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 專案，然後再開啟封裝。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-133">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want, and then open the package.</span></span>  
  
2.  <span data-ttu-id="cf8b7-134">選擇性地建立封裝設定。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-134">Optionally, create a package configuration.</span></span> <span data-ttu-id="cf8b7-135">如需詳細資訊，請參閱 [建立封裝組態](../../create-package-configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-135">For more information, see [Create Package Configurations](../../create-package-configurations.md).</span></span>  
  
3.  <span data-ttu-id="cf8b7-136">藉由執行下列工作，將快取檔案加入至專案：</span><span class="sxs-lookup"><span data-stu-id="cf8b7-136">Add the cache file to the project by doing the following:</span></span>  
  
    1.  <span data-ttu-id="cf8b7-137">在 [方案總管] 中，選取在步驟 1 中開啟的專案。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-137">In Solution Explorer, select the project you opened in step 1.</span></span>  
  
    2.  <span data-ttu-id="cf8b7-138">在 [專案]  功能表上，按一下 [加入現有項目]  。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-138">On the **Project** menu, click **AddExisting Item**.</span></span>  
  
    3.  <span data-ttu-id="cf8b7-139">選取快取檔案，然後按一下 [加入]  。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-139">Select the cache file, and then click **Add**.</span></span>  
  
     <span data-ttu-id="cf8b7-140">檔案便會出現在方案總管的 [其他]  資料夾中。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-140">The file appears in the **Miscellaneous** folder in Solution Explorer.</span></span>  
  
4.  <span data-ttu-id="cf8b7-141">將專案設定為建立部署公用程式，然後建立專案。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-141">Configure the project to create a deployment utility, and then build the project.</span></span> <span data-ttu-id="cf8b7-142">如需詳細資訊，請參閱 [建立部署公用程式](../../create-a-deployment-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-142">For more information, see [Create a Deployment Utility](../../create-a-deployment-utility.md).</span></span>  
  
     <span data-ttu-id="cf8b7-143">資訊清單檔 \<*project name*>.SSISDeploymentManifest.xml 會建立，並列出專案中的其他檔案、套件以及套件組態。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-143">A manifest file, \<*project name*>.SSISDeploymentManifest.xml, is created that lists the miscellaneous files in the project, the packages, and the package configurations.</span></span>  
  
5.  <span data-ttu-id="cf8b7-144">將封裝部署到檔案系統。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-144">Deploy the package to the file system.</span></span> <span data-ttu-id="cf8b7-145">如需詳細資訊，請參閱 [使用部署公用程式來部署封裝](../../deploy-packages-by-using-the-deployment-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="cf8b7-145">For more information, see [Deploy Packages by Using the Deployment Utility](../../deploy-packages-by-using-the-deployment-utility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf8b7-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf8b7-146">See Also</span></span>  
 [<span data-ttu-id="cf8b7-147">建立部署公用程式</span><span class="sxs-lookup"><span data-stu-id="cf8b7-147">Create a Deployment Utility</span></span>](../../create-a-deployment-utility.md)  
  
  
