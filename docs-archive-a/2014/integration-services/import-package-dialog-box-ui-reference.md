---
title: 匯入封裝對話方塊 UI 參考 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.dtsserver.importpackage.f1
helpviewer_keywords:
- Import Package dialog box
ms.assetid: 0e5fb127-c7ff-4dfa-b90e-d9bcf0ce763b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ff20bf8eb221778465a26944280d53b6aab07601
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596196"
---
# <a name="import-package-dialog-box-ui-reference"></a><span data-ttu-id="2d651-102">匯入封裝對話方塊 UI 參考</span><span class="sxs-lookup"><span data-stu-id="2d651-102">Import Package Dialog Box UI Reference</span></span>
  <span data-ttu-id="2d651-103">使用 **[匯入封裝]** 對話方塊 (可以從 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]存取)，即可匯入 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝，並設定或修改封裝的保護等級。</span><span class="sxs-lookup"><span data-stu-id="2d651-103">Use the **Import Package** dialog box, available in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], to import a [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package and to set or modify the protection level of the package.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2d651-104">選項。</span><span class="sxs-lookup"><span data-stu-id="2d651-104">Options</span></span>  
 <span data-ttu-id="2d651-105">**封裝位置**</span><span class="sxs-lookup"><span data-stu-id="2d651-105">**Package location**</span></span>  
 <span data-ttu-id="2d651-106">選取要匯入封裝之儲存位置的類型。</span><span class="sxs-lookup"><span data-stu-id="2d651-106">Select the type of storage location to import the package to.</span></span> <span data-ttu-id="2d651-107">有下列選項可供使用：</span><span class="sxs-lookup"><span data-stu-id="2d651-107">The following options are available:</span></span>  
  
 <span data-ttu-id="2d651-108">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="2d651-108">**SQL Server**</span></span>  
  
 <span data-ttu-id="2d651-109">**檔案系統**</span><span class="sxs-lookup"><span data-stu-id="2d651-109">**File System**</span></span>  
  
 <span data-ttu-id="2d651-110">**SSIS 封裝存放區**</span><span class="sxs-lookup"><span data-stu-id="2d651-110">**SSIS Package Store**</span></span>  
  
 <span data-ttu-id="2d651-111">**Server**</span><span class="sxs-lookup"><span data-stu-id="2d651-111">**Server**</span></span>  
 <span data-ttu-id="2d651-112">輸入伺服器名稱，或者從清單中選取一個伺服器。</span><span class="sxs-lookup"><span data-stu-id="2d651-112">Type a server name or select a server from the list.</span></span>  
  
 <span data-ttu-id="2d651-113">**驗證**</span><span class="sxs-lookup"><span data-stu-id="2d651-113">**Authentication**</span></span>  
 <span data-ttu-id="2d651-114">選取 Windows 驗證或 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證。</span><span class="sxs-lookup"><span data-stu-id="2d651-114">Select Windows Authentication or [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="2d651-115">唯有儲存位置是 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]時，才能使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="2d651-115">This option is available only if the storage location is [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2d651-116">可能的話，請使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="2d651-116">Whenever possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="2d651-117">**驗證類型**</span><span class="sxs-lookup"><span data-stu-id="2d651-117">**Authentication type**</span></span>  
 <span data-ttu-id="2d651-118">選取驗證類型。</span><span class="sxs-lookup"><span data-stu-id="2d651-118">Select an authentication type.</span></span>  
  
 <span data-ttu-id="2d651-119">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="2d651-119">**User name**</span></span>  
 <span data-ttu-id="2d651-120">如果使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證，請提供使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="2d651-120">If using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a user name.</span></span>  
  
 <span data-ttu-id="2d651-121">**密碼**</span><span class="sxs-lookup"><span data-stu-id="2d651-121">**Password**</span></span>  
 <span data-ttu-id="2d651-122">如果使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證，請提供密碼。</span><span class="sxs-lookup"><span data-stu-id="2d651-122">If using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a password.</span></span>  
  
 <span data-ttu-id="2d651-123">**封裝路徑**</span><span class="sxs-lookup"><span data-stu-id="2d651-123">**Package path**</span></span>  
 <span data-ttu-id="2d651-124">輸入封裝路徑，或按一下瀏覽按鈕 ([...])  ，然後找出封裝。</span><span class="sxs-lookup"><span data-stu-id="2d651-124">Type the package path, or click the browse button **(...)** and locate the package.</span></span>  
  
 <span data-ttu-id="2d651-125">**封裝名稱**</span><span class="sxs-lookup"><span data-stu-id="2d651-125">**Package name**</span></span>  
 <span data-ttu-id="2d651-126">選擇性地重新命名封裝。</span><span class="sxs-lookup"><span data-stu-id="2d651-126">Optionally, rename the package.</span></span> <span data-ttu-id="2d651-127">預設名稱是要匯入的封裝名稱。</span><span class="sxs-lookup"><span data-stu-id="2d651-127">The default name is the name of the package to import.</span></span>  
  
 <span data-ttu-id="2d651-128">**保護等級**</span><span class="sxs-lookup"><span data-stu-id="2d651-128">**Protection level**</span></span>  
 <span data-ttu-id="2d651-129">按一下瀏覽按鈕 ([...])  並更新 [封裝保護等級]  對話方塊中的保護等級。</span><span class="sxs-lookup"><span data-stu-id="2d651-129">Click the browse button **(...)** and, in the **Package Protection Level** dialog box, update the protection level.</span></span> <span data-ttu-id="2d651-130">如需詳細資訊，請參閱 [封裝與專案保護等級對話方塊](../../2014/integration-services/package-and-project-protection-level-dialog-box.md)。</span><span class="sxs-lookup"><span data-stu-id="2d651-130">For more information, see [Package and Project Protection Level Dialog Box](../../2014/integration-services/package-and-project-protection-level-dialog-box.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d651-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d651-131">See Also</span></span>  
 <span data-ttu-id="2d651-132">[儲存封裝的副本](../../2014/integration-services/save-copy-of-package.md) </span><span class="sxs-lookup"><span data-stu-id="2d651-132">[Save Copy of Package](../../2014/integration-services/save-copy-of-package.md) </span></span>  
 <span data-ttu-id="2d651-133">[匯出封裝對話方塊 UI 參考](../../2014/integration-services/export-package-dialog-box-ui-reference.md) </span><span class="sxs-lookup"><span data-stu-id="2d651-133">[Export Package Dialog Box UI Reference](../../2014/integration-services/export-package-dialog-box-ui-reference.md) </span></span>  
 <span data-ttu-id="2d651-134">[儲存封裝](save-packages.md) </span><span class="sxs-lookup"><span data-stu-id="2d651-134">[Save Packages](save-packages.md) </span></span>  
 [<span data-ttu-id="2d651-135">匯入和匯出封裝 &#40;SSIS 服務&#41;</span><span class="sxs-lookup"><span data-stu-id="2d651-135">Import and Export Packages &#40;SSIS Service&#41;</span></span>](../../2014/integration-services/import-and-export-packages-ssis-service.md)  
  
  
