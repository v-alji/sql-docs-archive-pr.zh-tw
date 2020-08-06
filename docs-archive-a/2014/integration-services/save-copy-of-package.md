---
title: 儲存封裝的副本 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.savecopyas.f1
helpviewer_keywords:
- Save Copy of Package dialog box
ms.assetid: 7b44c0d7-d8fa-4491-8836-0899f621d3a8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f0a685d8b38299e1ba1d03c4ec8c1052cc957dbb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706586"
---
# <a name="save-copy-of-package"></a><span data-ttu-id="9e215-102">儲存封裝的副本</span><span class="sxs-lookup"><span data-stu-id="9e215-102">Save Copy of Package</span></span>
  <span data-ttu-id="9e215-103">使用 **[儲存封裝的副本]** 對話方塊 (可以在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中使用)，即可將 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝的副本從 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 儲存到另一個位置，然後選擇性的修改封裝的保護等級。</span><span class="sxs-lookup"><span data-stu-id="9e215-103">Use the **Save Copy of Package** dialog box, available in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], to save a copy of an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package from [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to a different location and, optionally, modify the protection level of the package.</span></span>  
  
## <a name="options"></a><span data-ttu-id="9e215-104">選項。</span><span class="sxs-lookup"><span data-stu-id="9e215-104">Options</span></span>  
 <span data-ttu-id="9e215-105">**封裝位置**</span><span class="sxs-lookup"><span data-stu-id="9e215-105">**Package location**</span></span>  
 <span data-ttu-id="9e215-106">選取要儲存封裝副本之儲存位置的類型。</span><span class="sxs-lookup"><span data-stu-id="9e215-106">Select the type of storage location in which to save the package copy.</span></span> <span data-ttu-id="9e215-107">有下列選項可供使用：</span><span class="sxs-lookup"><span data-stu-id="9e215-107">The following options are available:</span></span>  
  
 <span data-ttu-id="9e215-108">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="9e215-108">**SQL Server**</span></span>  
  
 <span data-ttu-id="9e215-109">**檔案系統**</span><span class="sxs-lookup"><span data-stu-id="9e215-109">**File System**</span></span>  
  
 <span data-ttu-id="9e215-110">**SSIS 封裝存放區**</span><span class="sxs-lookup"><span data-stu-id="9e215-110">**SSIS Package Store**</span></span>  
  
 <span data-ttu-id="9e215-111">**Server**</span><span class="sxs-lookup"><span data-stu-id="9e215-111">**Server**</span></span>  
 <span data-ttu-id="9e215-112">輸入伺服器名稱，或者從清單中選取一個伺服器。</span><span class="sxs-lookup"><span data-stu-id="9e215-112">Type a server name or select a server from the list.</span></span> <span data-ttu-id="9e215-113">唯有儲存位置是 **[SQL Server]** 或 **[SSIS 封裝存放區]** 時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="9e215-113">This option is available only if the storage location is **SQL Server** or **SSIS Package Store**.</span></span>  
  
 <span data-ttu-id="9e215-114">**驗證**</span><span class="sxs-lookup"><span data-stu-id="9e215-114">**Authentication**</span></span>  
 <span data-ttu-id="9e215-115">選取 Windows 驗證或 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證。</span><span class="sxs-lookup"><span data-stu-id="9e215-115">Select Windows Authentication or [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="9e215-116">唯有儲存位置是 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]時，才能使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="9e215-116">This option is available only if the storage location is [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9e215-117">儘可能使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="9e215-117">Whenever possible use Windows Authentication.</span></span>  
  
 <span data-ttu-id="9e215-118">**驗證類型**</span><span class="sxs-lookup"><span data-stu-id="9e215-118">**Authentication type**</span></span>  
 <span data-ttu-id="9e215-119">選取驗證類型。</span><span class="sxs-lookup"><span data-stu-id="9e215-119">Select an authentication type.</span></span>  
  
 <span data-ttu-id="9e215-120">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="9e215-120">**User name**</span></span>  
 <span data-ttu-id="9e215-121">如果使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證，請提供使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="9e215-121">If using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a user name.</span></span>  
  
 <span data-ttu-id="9e215-122">**密碼**</span><span class="sxs-lookup"><span data-stu-id="9e215-122">**Password**</span></span>  
 <span data-ttu-id="9e215-123">如果使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證，請提供密碼。</span><span class="sxs-lookup"><span data-stu-id="9e215-123">If using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a password.</span></span>  
  
 <span data-ttu-id="9e215-124">**封裝路徑**</span><span class="sxs-lookup"><span data-stu-id="9e215-124">**Package path**</span></span>  
 <span data-ttu-id="9e215-125">輸入封裝路徑，或按一下 [流覽\*\* ( ... ) \*\* ] 按鈕，並找出要儲存封裝的資料夾。</span><span class="sxs-lookup"><span data-stu-id="9e215-125">Type the package path, or click the browse **(...)** button and locate the folder in which to store the package.</span></span>  
  
 <span data-ttu-id="9e215-126">**保護等級**</span><span class="sxs-lookup"><span data-stu-id="9e215-126">**Protection level**</span></span>  
 <span data-ttu-id="9e215-127">按一下 [流覽\*\* ( ... ) \*\* ] 按鈕，並更新 [**封裝保護等級**] 對話方塊中的保護等級。</span><span class="sxs-lookup"><span data-stu-id="9e215-127">Click the browse **(...)** button and update the protection level in the **Package Protection Level** dialog box.</span></span> <span data-ttu-id="9e215-128">如需詳細資訊，請參閱 [封裝與專案保護等級對話方塊](../../2014/integration-services/package-and-project-protection-level-dialog-box.md)。</span><span class="sxs-lookup"><span data-stu-id="9e215-128">For more information, see [Package and Project Protection Level Dialog Box](../../2014/integration-services/package-and-project-protection-level-dialog-box.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e215-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e215-129">See Also</span></span>  
 <span data-ttu-id="9e215-130">[匯入封裝對話方塊 UI 參考](../../2014/integration-services/import-package-dialog-box-ui-reference.md) </span><span class="sxs-lookup"><span data-stu-id="9e215-130">[Import Package Dialog Box UI Reference](../../2014/integration-services/import-package-dialog-box-ui-reference.md) </span></span>  
 <span data-ttu-id="9e215-131">[匯出封裝對話方塊 UI 參考](../../2014/integration-services/export-package-dialog-box-ui-reference.md) </span><span class="sxs-lookup"><span data-stu-id="9e215-131">[Export Package Dialog Box UI Reference](../../2014/integration-services/export-package-dialog-box-ui-reference.md) </span></span>  
 <span data-ttu-id="9e215-132">[儲存封裝](save-packages.md) </span><span class="sxs-lookup"><span data-stu-id="9e215-132">[Save Packages](save-packages.md) </span></span>  
 [<span data-ttu-id="9e215-133">匯入和匯出封裝 &#40;SSIS 服務&#41;</span><span class="sxs-lookup"><span data-stu-id="9e215-133">Import and Export Packages &#40;SSIS Service&#41;</span></span>](../../2014/integration-services/import-and-export-packages-ssis-service.md)  
  
  
