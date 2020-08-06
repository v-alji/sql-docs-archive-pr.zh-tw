---
title: 匯出封裝對話方塊 UI 參考 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.dtsserver.exportpackage.f1
helpviewer_keywords:
- Export Package dialog box
ms.assetid: 3742fe8a-ef57-444d-b2fb-cb25d16bae97
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8aedb771dc61fca737ba3841e65b8cb8655d173e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710758"
---
# <a name="export-package-dialog-box-ui-reference"></a><span data-ttu-id="fef22-102">匯出封裝對話方塊 UI 參考</span><span class="sxs-lookup"><span data-stu-id="fef22-102">Export Package Dialog Box UI Reference</span></span>
  <span data-ttu-id="fef22-103">使用 **[匯出封裝]** 對話方塊 (可以從 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中存取)，即可匯出 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝到不同的位置，並選擇性地修改封裝的保護等級。</span><span class="sxs-lookup"><span data-stu-id="fef22-103">Use the **Export Package** dialog box, available in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], to export a [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package to a different location and optionally, modify the protection level of the package.</span></span>  
  
## <a name="options"></a><span data-ttu-id="fef22-104">選項。</span><span class="sxs-lookup"><span data-stu-id="fef22-104">Options</span></span>  
 <span data-ttu-id="fef22-105">**封裝位置**</span><span class="sxs-lookup"><span data-stu-id="fef22-105">**Package location**</span></span>  
 <span data-ttu-id="fef22-106">選取要用來儲存所匯出之封裝的儲存體類型。</span><span class="sxs-lookup"><span data-stu-id="fef22-106">Select the type of storage to export the package to.</span></span> <span data-ttu-id="fef22-107">有下列選項可供使用：</span><span class="sxs-lookup"><span data-stu-id="fef22-107">The following options are available:</span></span>  
  
 <span data-ttu-id="fef22-108">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="fef22-108">**SQL Server**</span></span>  
  
 <span data-ttu-id="fef22-109">**檔案系統**</span><span class="sxs-lookup"><span data-stu-id="fef22-109">**File System**</span></span>  
  
 <span data-ttu-id="fef22-110">**SSIS 封裝儲存體**</span><span class="sxs-lookup"><span data-stu-id="fef22-110">**SSIS Package Storage**</span></span>  
  
 <span data-ttu-id="fef22-111">**Server**</span><span class="sxs-lookup"><span data-stu-id="fef22-111">**Server**</span></span>  
 <span data-ttu-id="fef22-112">輸入伺服器名稱，或者從清單中選取一個伺服器。</span><span class="sxs-lookup"><span data-stu-id="fef22-112">Type a server name or select a server from the list.</span></span>  
  
 <span data-ttu-id="fef22-113">**驗證**</span><span class="sxs-lookup"><span data-stu-id="fef22-113">**Authentication**</span></span>  
 <span data-ttu-id="fef22-114">選取 Windows 驗證或 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證。</span><span class="sxs-lookup"><span data-stu-id="fef22-114">Select Windows Authentication or [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="fef22-115">唯有儲存位置是 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]時，才能使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="fef22-115">This option is available only if the storage location is [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fef22-116">可能的話，請使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="fef22-116">Whenever possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="fef22-117">**驗證類型**</span><span class="sxs-lookup"><span data-stu-id="fef22-117">**Authentication type**</span></span>  
 <span data-ttu-id="fef22-118">選取驗證類型。</span><span class="sxs-lookup"><span data-stu-id="fef22-118">Select an authentication type.</span></span>  
  
 <span data-ttu-id="fef22-119">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="fef22-119">**User name**</span></span>  
 <span data-ttu-id="fef22-120">如果使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證，請提供使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="fef22-120">If using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a user name.</span></span>  
  
 <span data-ttu-id="fef22-121">**密碼**</span><span class="sxs-lookup"><span data-stu-id="fef22-121">**Password**</span></span>  
 <span data-ttu-id="fef22-122">如果使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證，請提供密碼。</span><span class="sxs-lookup"><span data-stu-id="fef22-122">If using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, provide a password.</span></span>  
  
 <span data-ttu-id="fef22-123">**封裝路徑**</span><span class="sxs-lookup"><span data-stu-id="fef22-123">**Package path**</span></span>  
 <span data-ttu-id="fef22-124">輸入封裝路徑，或按一下瀏覽按鈕 ([...])  ，並找出要儲存封裝的資料夾。</span><span class="sxs-lookup"><span data-stu-id="fef22-124">Type the package path, or click the browse button **(...)** and locate the folder in which to store the package.</span></span>  
  
 <span data-ttu-id="fef22-125">**保護等級**</span><span class="sxs-lookup"><span data-stu-id="fef22-125">**Protection level**</span></span>  
 <span data-ttu-id="fef22-126">按一下瀏覽按鈕 ([...])  並更新 [封裝保護等級]  對話方塊中的保護等級。</span><span class="sxs-lookup"><span data-stu-id="fef22-126">Click the browse button **(...)** and update the protection level in the **Package Protection Level** dialog box.</span></span> <span data-ttu-id="fef22-127">如需詳細資訊，請參閱 [封裝與專案保護等級對話方塊](../../2014/integration-services/package-and-project-protection-level-dialog-box.md)。</span><span class="sxs-lookup"><span data-stu-id="fef22-127">For more information, see [Package and Project Protection Level Dialog Box](../../2014/integration-services/package-and-project-protection-level-dialog-box.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fef22-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fef22-128">See Also</span></span>  
 <span data-ttu-id="fef22-129">[儲存封裝的副本](../../2014/integration-services/save-copy-of-package.md) </span><span class="sxs-lookup"><span data-stu-id="fef22-129">[Save Copy of Package](../../2014/integration-services/save-copy-of-package.md) </span></span>  
 <span data-ttu-id="fef22-130">[匯入封裝對話方塊 UI 參考](../../2014/integration-services/import-package-dialog-box-ui-reference.md) </span><span class="sxs-lookup"><span data-stu-id="fef22-130">[Import Package Dialog Box UI Reference](../../2014/integration-services/import-package-dialog-box-ui-reference.md) </span></span>  
 <span data-ttu-id="fef22-131">[儲存封裝](save-packages.md) </span><span class="sxs-lookup"><span data-stu-id="fef22-131">[Save Packages](save-packages.md) </span></span>  
 [<span data-ttu-id="fef22-132">匯入和匯出封裝 &#40;SSIS 服務&#41;</span><span class="sxs-lookup"><span data-stu-id="fef22-132">Import and Export Packages &#40;SSIS Service&#41;</span></span>](../../2014/integration-services/import-and-export-packages-ssis-service.md)  
  
  
