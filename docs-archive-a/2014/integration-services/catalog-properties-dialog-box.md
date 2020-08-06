---
title: 目錄屬性對話方塊 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.iscatalogprop.general.f1
- sql12.ssis.ssms.iscreatecatalog.f1
ms.assetid: 3e2fcf11-e010-41c6-bc26-e4b281c0bfbc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9f1a4a9d7a74e47d609c319f90b07d8ebfdce00e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599151"
---
# <a name="catalog-properties-dialog-box"></a><span data-ttu-id="0922a-102">目錄屬性對話方塊</span><span class="sxs-lookup"><span data-stu-id="0922a-102">Catalog Properties Dialog Box</span></span>
  <span data-ttu-id="0922a-103">使用 [目錄屬性] 對話方塊來設定 SSISDB 目錄。</span><span class="sxs-lookup"><span data-stu-id="0922a-103">Use the Catalog Properties dialog box to configure the SSISDB catalog.</span></span> <span data-ttu-id="0922a-104">目錄屬性定義如何加密敏感性資料，如何保留作業和專案版本設定資料，以及何時驗證作業逾時。SSISDB 目錄是 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案、封裝、參數與環境的中央儲存和管理點。</span><span class="sxs-lookup"><span data-stu-id="0922a-104">Catalog properties define how sensitive data is encrypted, how operations and project versioning data is retained, and when validation operations time out. The SSISDB catalog is a central storage and administration point for [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects, packages, parameters, and environments.</span></span>  
  
 <span data-ttu-id="0922a-105">您也可以在 catalog.catalog_property 檢視表中檢視目錄屬性，以及使用 catalog.configure_catalog 預存程序來設定屬性。</span><span class="sxs-lookup"><span data-stu-id="0922a-105">You can also view catalog properties in the catalog.catalog_property view, and set the properties by using the catalog.configure_catalog stored procedure.</span></span> <span data-ttu-id="0922a-106">如需詳細資訊，請參閱 [catalog.catalog_properties &#40;SSISDB 資料庫&#41;](/sql/integration-services/system-views/catalog-catalog-properties-ssisdb-database) 和 [catalog.configure_catalog &#40;SSISDB 資料庫&#41;](/sql/integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database)。</span><span class="sxs-lookup"><span data-stu-id="0922a-106">For more information, see [catalog.catalog_properties &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-catalog-properties-ssisdb-database) and [catalog.configure_catalog &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database).</span></span>  
  
 <span data-ttu-id="0922a-107">如需如何建立 SSISDB 目錄的資訊，請參閱 [建立 SSIS 目錄](catalog/ssis-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="0922a-107">For information on how to create the SSISDB catalog, see [Create the SSIS Catalog](catalog/ssis-catalog.md).</span></span>  
  
 <span data-ttu-id="0922a-108">**您想要做什麼事？**</span><span class="sxs-lookup"><span data-stu-id="0922a-108">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="0922a-109">開啟目錄屬性對話方塊</span><span class="sxs-lookup"><span data-stu-id="0922a-109">Open the Catalog Properties Dialog Box</span></span>](#open_dialog)  
  
-   [<span data-ttu-id="0922a-110">設定選項</span><span class="sxs-lookup"><span data-stu-id="0922a-110">Configure the Options</span></span>](#options)  
  
##  <a name="open-the-catalog-properties-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="0922a-111">開啟目錄屬性對話方塊</span><span class="sxs-lookup"><span data-stu-id="0922a-111">Open the Catalog Properties Dialog Box</span></span>  
  
1.  <span data-ttu-id="0922a-112">開啟 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0922a-112">Open [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="0922a-113">連接 Microsoft SQL Server Database Engine。</span><span class="sxs-lookup"><span data-stu-id="0922a-113">Connect Microsoft SQL Server Database Engine.</span></span>  
  
3.  <span data-ttu-id="0922a-114">在物件總管中，展開 [Integration Services] 節點，並以滑鼠右鍵按一下 [SSISDB]，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="0922a-114">In Object Explorer, expand the **Integration Services** node, right-click **SSISDB**, and then click **Properties**.</span></span>  
  
##  <a name="configure-the-options"></a><a name="options"></a> <span data-ttu-id="0922a-115">設定選項</span><span class="sxs-lookup"><span data-stu-id="0922a-115">Configure the Options</span></span>  
  
### <a name="options"></a><span data-ttu-id="0922a-116">選項。</span><span class="sxs-lookup"><span data-stu-id="0922a-116">Options</span></span>  
 <span data-ttu-id="0922a-117">下表描述對話方塊中的特定屬性，以及 catalog.catalog_property 檢視表中的對應屬性。</span><span class="sxs-lookup"><span data-stu-id="0922a-117">The following table describes certain properties in the dialog box and the corresponding properties in the catalog.catalog_property view.</span></span>  
  
|<span data-ttu-id="0922a-118">屬性名稱 (目錄屬性對話方塊)</span><span class="sxs-lookup"><span data-stu-id="0922a-118">Property Name (Catalog Properties dialog box)</span></span>|<span data-ttu-id="0922a-119">屬性名稱 (catalog.catalog_property 檢視表)</span><span class="sxs-lookup"><span data-stu-id="0922a-119">Property Name (catalog.catalog_property view)</span></span>|<span data-ttu-id="0922a-120">描述</span><span class="sxs-lookup"><span data-stu-id="0922a-120">Description</span></span>|  
|-----------------------------------------------------|------------------------------------------------------|-----------------|  
|<span data-ttu-id="0922a-121">加密演算法名稱</span><span class="sxs-lookup"><span data-stu-id="0922a-121">Encryption Algorithm Name</span></span>|<span data-ttu-id="0922a-122">ENCRYPTION_CLEANUP_ENABLED</span><span class="sxs-lookup"><span data-stu-id="0922a-122">ENCRYPTION_CLEANUP_ENABLED</span></span>|<span data-ttu-id="0922a-123">指定用來加密目錄中敏感性參數值的加密類型。</span><span class="sxs-lookup"><span data-stu-id="0922a-123">Specifies the type of encryption that is used to encrypt the sensitive parameter values in the catalog.</span></span> <span data-ttu-id="0922a-124">以下是可能的值：</span><span class="sxs-lookup"><span data-stu-id="0922a-124">The following are the possible values:</span></span><br /><br /> <span data-ttu-id="0922a-125">**DES**</span><span class="sxs-lookup"><span data-stu-id="0922a-125">**DES**</span></span><br /><br /> <span data-ttu-id="0922a-126">**TRIPLE_DES**</span><span class="sxs-lookup"><span data-stu-id="0922a-126">**TRIPLE_DES**</span></span><br /><br /> <span data-ttu-id="0922a-127">**TRIPLE_DES_3KEY**</span><span class="sxs-lookup"><span data-stu-id="0922a-127">**TRIPLE_DES_3KEY**</span></span><br /><br /> <span data-ttu-id="0922a-128">**DESPX**</span><span class="sxs-lookup"><span data-stu-id="0922a-128">**DESPX**</span></span><br /><br /> <span data-ttu-id="0922a-129">**AES_128**</span><span class="sxs-lookup"><span data-stu-id="0922a-129">**AES_128**</span></span><br /><br /> <span data-ttu-id="0922a-130">**AES_192**</span><span class="sxs-lookup"><span data-stu-id="0922a-130">**AES_192**</span></span><br /><br /> <span data-ttu-id="0922a-131">**AES_256** (預設) </span><span class="sxs-lookup"><span data-stu-id="0922a-131">**AES_256** (default)</span></span>|  
|<span data-ttu-id="0922a-132">驗證逾時 (秒)</span><span class="sxs-lookup"><span data-stu-id="0922a-132">Validation Timeout (seconds)</span></span>|<span data-ttu-id="0922a-133">VALIDATION_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0922a-133">VALIDATION_TIMEOUT</span></span>|<span data-ttu-id="0922a-134">指定專案驗證或封裝驗證在停止之前，可以執行的秒數上限。</span><span class="sxs-lookup"><span data-stu-id="0922a-134">Specify the maxium number of seconds a project validation or a package validation can run before it is stopped.</span></span> <span data-ttu-id="0922a-135">預設值為 300 秒。</span><span class="sxs-lookup"><span data-stu-id="0922a-135">The default value is 300 seconds.</span></span><br /><br /> <span data-ttu-id="0922a-136">執行驗證是非同步作業。</span><span class="sxs-lookup"><span data-stu-id="0922a-136">Performing the validation is an asynchronous operation.</span></span> <span data-ttu-id="0922a-137">專案或封裝愈大，驗證所需時間愈長。</span><span class="sxs-lookup"><span data-stu-id="0922a-137">The larger the project or package is, the longer it will take to validate.</span></span><br /><br /> <span data-ttu-id="0922a-138">如需有關驗證專案和封裝的詳細資訊，請參閱＜ [Integration Services Data Types in Expressions](expressions/integration-services-data-types-in-expressions.md)＞。</span><span class="sxs-lookup"><span data-stu-id="0922a-138">For information on validating projects and packages, see [Integration Services Data Types in Expressions](expressions/integration-services-data-types-in-expressions.md).</span></span>|  
|<span data-ttu-id="0922a-139">定期清除記錄檔</span><span class="sxs-lookup"><span data-stu-id="0922a-139">Clean Logs Periodically</span></span>|<span data-ttu-id="0922a-140">OPERATION_CLEANUP_ENABLED</span><span class="sxs-lookup"><span data-stu-id="0922a-140">OPERATION_CLEANUP_ENABLED</span></span>|<span data-ttu-id="0922a-141">將屬性設為 True，指出 SQL Server Agent 作業 (作業清除) 會執行。</span><span class="sxs-lookup"><span data-stu-id="0922a-141">Set the property to True to indicate that the SQL Server Agent job, operations cleanup, runs.</span></span> <span data-ttu-id="0922a-142">否則請將屬性設為 False。</span><span class="sxs-lookup"><span data-stu-id="0922a-142">Otherwise, set the property to False.</span></span>|  
|<span data-ttu-id="0922a-143">保留週期 (天)</span><span class="sxs-lookup"><span data-stu-id="0922a-143">Retention Period (days)</span></span>|<span data-ttu-id="0922a-144">RETENTION_WINDOW</span><span class="sxs-lookup"><span data-stu-id="0922a-144">RETENTION_WINDOW</span></span>|<span data-ttu-id="0922a-145">指定可允許的作業資料存在時間上限 (以天為單位)。</span><span class="sxs-lookup"><span data-stu-id="0922a-145">Specify the maximum age of allowable operations data (in days).</span></span> <span data-ttu-id="0922a-146">SQL Agent 作業 (作業清除) 會移除比指定天數還舊的資料。</span><span class="sxs-lookup"><span data-stu-id="0922a-146">Data that is older than the specified number of days will be removed by the SQL Agent job, operations cleanup.</span></span>|  
|<span data-ttu-id="0922a-147">每一專案的版本數目上限</span><span class="sxs-lookup"><span data-stu-id="0922a-147">Maximum Number of Versions per Project</span></span>|<span data-ttu-id="0922a-148">MAX_PROJECT_VERSIONS</span><span class="sxs-lookup"><span data-stu-id="0922a-148">MAX_PROJECT_VERSIONS</span></span>|<span data-ttu-id="0922a-149">指定多少個專案版本會儲存在目錄中。</span><span class="sxs-lookup"><span data-stu-id="0922a-149">Specify how many versions of a project will be stored in the catalog.</span></span> <span data-ttu-id="0922a-150">當專案版本清除作業執行時，將會移除超過最大值的舊專案版本。</span><span class="sxs-lookup"><span data-stu-id="0922a-150">Older versions of projects that exceed the maximum will be removed when the project version cleanup job runs.</span></span>|  
  
  
