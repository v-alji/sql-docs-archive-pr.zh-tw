---
title: 套件屬性對話方塊 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.ispackageprop.general.f1
- sql12.ssis.ssms.packageproperties.f1
ms.assetid: a70acbf4-5f5c-4606-8ce4-8eb3684233de
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b386bf4e75ff784cd8d4a96363515786d242d2a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594643"
---
# <a name="package-properties-dialog-box"></a><span data-ttu-id="f10c1-102">封裝屬性對話方塊</span><span class="sxs-lookup"><span data-stu-id="f10c1-102">Package Properties Dialog Box</span></span>
  <span data-ttu-id="f10c1-103">使用 [封裝屬性]  對話方塊，檢視儲存在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器上之封裝的屬性。</span><span class="sxs-lookup"><span data-stu-id="f10c1-103">Use the **Package Properties** dialog box to view properties for packages that are stored on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
 <span data-ttu-id="f10c1-104">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 伺服器](integration-services-ssis-server-and-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="f10c1-104">For more information, see [Integration Services &#40;SSIS&#41; Server](integration-services-ssis-server-and-catalog.md).</span></span>  
  
 <span data-ttu-id="f10c1-105">**您想要做什麼事？**</span><span class="sxs-lookup"><span data-stu-id="f10c1-105">**What do you want to do?**</span></span>  
  
-   <span data-ttu-id="f10c1-106">[開啟 [封裝屬性] 對話方塊](#open_dialog)</span><span class="sxs-lookup"><span data-stu-id="f10c1-106">[Open the Package Properties dialog box](#open_dialog)</span></span>  
  
-   [<span data-ttu-id="f10c1-107">設定選項</span><span class="sxs-lookup"><span data-stu-id="f10c1-107">Configure the Options</span></span>](#options)  
  
##  <a name="open-the-package-properties-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="f10c1-108">開啟 [封裝屬性] 對話方塊</span><span class="sxs-lookup"><span data-stu-id="f10c1-108">Open the Package Properties dialog box</span></span>  
  
1.  <span data-ttu-id="f10c1-109">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，連接至 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器。</span><span class="sxs-lookup"><span data-stu-id="f10c1-109">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="f10c1-110">您正在連線到裝載 SSISDB 資料庫的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="f10c1-110">You're connecting to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the SSISDB database.</span></span>  
  
2.  <span data-ttu-id="f10c1-111">在 [物件總管] 中，展開樹狀目錄以顯示 **[Integration Services 目錄]** 節點。</span><span class="sxs-lookup"><span data-stu-id="f10c1-111">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="f10c1-112">展開 **[SSISDB]** 節點。</span><span class="sxs-lookup"><span data-stu-id="f10c1-112">Expand the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="f10c1-113">展開包含您要檢視其屬性之封裝的資料夾。</span><span class="sxs-lookup"><span data-stu-id="f10c1-113">Expand the folder that contains the package you want to view properties for.</span></span>  
  
5.  <span data-ttu-id="f10c1-114">以滑鼠右鍵按一下封裝，然後選取 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="f10c1-114">Right-click the package, and then select **Properties**.</span></span>  
  
##  <a name="configure-the-options"></a><a name="options"></a> <span data-ttu-id="f10c1-115">設定選項</span><span class="sxs-lookup"><span data-stu-id="f10c1-115">Configure the Options</span></span>  
 <span data-ttu-id="f10c1-116">使用 [一般]  頁面，即可檢視所選封裝的屬性。</span><span class="sxs-lookup"><span data-stu-id="f10c1-116">Use the **General** page to view the properties of the selected package.</span></span>  
  
 <span data-ttu-id="f10c1-117">[一般]  頁面上的所有屬性都是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="f10c1-117">All properties on the **General** page are read-only.</span></span>  
  
 <span data-ttu-id="f10c1-118">**名稱**</span><span class="sxs-lookup"><span data-stu-id="f10c1-118">**Name**</span></span>  
 <span data-ttu-id="f10c1-119">顯示封裝名稱。</span><span class="sxs-lookup"><span data-stu-id="f10c1-119">Displays the name of the package.</span></span>  
  
 <span data-ttu-id="f10c1-120">**識別碼**</span><span class="sxs-lookup"><span data-stu-id="f10c1-120">**Identifier**</span></span>  
 <span data-ttu-id="f10c1-121">列出封裝識別碼。</span><span class="sxs-lookup"><span data-stu-id="f10c1-121">Lists the package ID.</span></span>  
  
 <span data-ttu-id="f10c1-122">**進入點**</span><span class="sxs-lookup"><span data-stu-id="f10c1-122">**Entry Point**</span></span>  
 <span data-ttu-id="f10c1-123">`True` 的值表示封裝是直接啟動。</span><span class="sxs-lookup"><span data-stu-id="f10c1-123">The value of `True` indicates that the package is started directly.</span></span> <span data-ttu-id="f10c1-124">`False` 的值表示封裝是使用「執行封裝」，由另一個封裝啟動。</span><span class="sxs-lookup"><span data-stu-id="f10c1-124">The value of `False` indicates that the package is started by another package using the Execute Package task.</span></span> <span data-ttu-id="f10c1-125">預設值是 `True`。</span><span class="sxs-lookup"><span data-stu-id="f10c1-125">The default value is `True`.</span></span>  
  
 <span data-ttu-id="f10c1-126">以滑鼠右鍵按一下方案總管中的封裝，然後按一下 [進入點封裝]，就可以在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中為父封裝和子封裝設定此屬性。</span><span class="sxs-lookup"><span data-stu-id="f10c1-126">You set this property in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] for both the parent package and the child packages by right-clicking the package in Solution Explorer and then clicking **Entry-point Package**.</span></span>  
  
 <span data-ttu-id="f10c1-127">**說明**</span><span class="sxs-lookup"><span data-stu-id="f10c1-127">**Description**</span></span>  
 <span data-ttu-id="f10c1-128">顯示封裝的選擇性描述。</span><span class="sxs-lookup"><span data-stu-id="f10c1-128">Displays the optional description of the package.</span></span>  
  
  
