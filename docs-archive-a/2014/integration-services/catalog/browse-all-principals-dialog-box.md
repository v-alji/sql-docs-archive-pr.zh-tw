---
title: 瀏覽所有主體對話方塊 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.browseprincipals.f1
ms.assetid: f11d2c5e-ee05-45f3-8dc2-0feb99b2f76f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c204411a4daace27745e46269cbcfa0ed33f323f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592187"
---
# <a name="browse-all-principals-dialog-box"></a><span data-ttu-id="7f24c-102">瀏覽所有主體對話方塊</span><span class="sxs-lookup"><span data-stu-id="7f24c-102">Browse All Principals Dialog Box</span></span>
  <span data-ttu-id="7f24c-103">使用 [瀏覽所有主體]  對話方塊選取資料庫主體，以變更主體在所選專案或所選資料夾中包含之所有專案上的權限。</span><span class="sxs-lookup"><span data-stu-id="7f24c-103">Use the **Browse All Principals** dialog box to select a database principal to change the principal's permissions on the selected project or on all projects contained in a selected folder.</span></span>  
  
 <span data-ttu-id="7f24c-104">**您想要做什麼事？**</span><span class="sxs-lookup"><span data-stu-id="7f24c-104">**What do you want to do?**</span></span>  
  
-   <span data-ttu-id="7f24c-105">[開啟 [瀏覽所有主體] 對話方塊](#open_dialog)</span><span class="sxs-lookup"><span data-stu-id="7f24c-105">[Open the Browse All Principals dialog box](#open_dialog)</span></span>  
  
-   [<span data-ttu-id="7f24c-106">設定選項</span><span class="sxs-lookup"><span data-stu-id="7f24c-106">Configure the Options</span></span>](#options)  
  
##  <a name="open-the-browse-all-principals-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="7f24c-107">開啟 [瀏覽所有主體] 對話方塊</span><span class="sxs-lookup"><span data-stu-id="7f24c-107">Open the Browse All Principals dialog box</span></span>  
  
1.  <span data-ttu-id="7f24c-108">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，連接至 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器。</span><span class="sxs-lookup"><span data-stu-id="7f24c-108">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="7f24c-109">您正在連線到主控 SSISDB 目錄的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="7f24c-109">You're connecting to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the SSISDB catalog.</span></span>  
  
2.  <span data-ttu-id="7f24c-110">在 [物件總管] 中，展開樹狀目錄以顯示 **[Integration Services 目錄]** 節點。</span><span class="sxs-lookup"><span data-stu-id="7f24c-110">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="7f24c-111">展開 **[SSISDB]** 節點。</span><span class="sxs-lookup"><span data-stu-id="7f24c-111">Expand the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="7f24c-112">若要變更主體在所選資料中包含之所有專案上的權限，請以滑鼠右鍵按一下資料夾，然後按一下 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="7f24c-112">To change the principal's permissions on all projects contained in a selected folder, right-click the folder and then click **Properties**.</span></span>  
  
     <span data-ttu-id="7f24c-113">若要變更主體在所選專案上的權限，請展開包含專案的資料夾，以滑鼠右鍵按一下該專案，然後按一下 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="7f24c-113">To change the principal's permissions on a selected project, expand the folder that contains the project, right-click the project, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="7f24c-114">選取 **[權限]** 頁面，然後按一下 **[瀏覽]** 。</span><span class="sxs-lookup"><span data-stu-id="7f24c-114">Select the **Permissions** page, and then click **Browse**.</span></span>  
  
##  <a name="configure-the-options"></a><a name="options"></a> <span data-ttu-id="7f24c-115">設定選項</span><span class="sxs-lookup"><span data-stu-id="7f24c-115">Configure the Options</span></span>  
 <span data-ttu-id="7f24c-116">這個頁面會顯示來自 SSISDB 資料庫之目錄檢視 sys.database_principals 的主體。</span><span class="sxs-lookup"><span data-stu-id="7f24c-116">This page displays the principals from the catalog view, sys.database_principals, of the SSISDB database.</span></span>  
  
 <span data-ttu-id="7f24c-117">若選取主體，在您按一下 **[確定]** 並關閉 **[瀏覽所有主體]** 對話方塊時，它們就會加入至父對話方塊中 **[權限]** 頁面上的 **[登入或角色]** 清單。</span><span class="sxs-lookup"><span data-stu-id="7f24c-117">Selecting principals adds them to the **Logins or roles** list on the **Permissions** page of the parent dialog box when you click **OK** and close the **Browse All Principals** dialog box.</span></span> <span data-ttu-id="7f24c-118">將主體加入至 **[登入或角色]** 清單後，您可以變更它們在所選專案上的權限。</span><span class="sxs-lookup"><span data-stu-id="7f24c-118">After adding principals to the **Logins or roles** list, you can change their permissions on the selected project.</span></span>  
  
 <span data-ttu-id="7f24c-119">**選取資料行**</span><span class="sxs-lookup"><span data-stu-id="7f24c-119">**Selection column**</span></span>  
 <span data-ttu-id="7f24c-120">選取此選項即可將主體加入至父對話方塊中 [權限] 頁面上的 [登入或角色] 清單。</span><span class="sxs-lookup"><span data-stu-id="7f24c-120">Select to add the principal to the **Logins or roles** list on the **Permissions** page of the parent dialog box.</span></span>  
  
 <span data-ttu-id="7f24c-121">**圖示資料行**</span><span class="sxs-lookup"><span data-stu-id="7f24c-121">**Icon column**</span></span>  
 <span data-ttu-id="7f24c-122">與主體之 [類型]  對應的圖示。</span><span class="sxs-lookup"><span data-stu-id="7f24c-122">An icon that corresponds to the **Type** of the principal.</span></span>  
  
 <span data-ttu-id="7f24c-123">**名稱**</span><span class="sxs-lookup"><span data-stu-id="7f24c-123">**Name**</span></span>  
 <span data-ttu-id="7f24c-124">主體的名稱。</span><span class="sxs-lookup"><span data-stu-id="7f24c-124">The name of the principal.</span></span>  
  
 <span data-ttu-id="7f24c-125">**型別**</span><span class="sxs-lookup"><span data-stu-id="7f24c-125">**Type**</span></span>  
 <span data-ttu-id="7f24c-126">主體的類型。</span><span class="sxs-lookup"><span data-stu-id="7f24c-126">The type of the principal.</span></span> <span data-ttu-id="7f24c-127">常見的類型如下：</span><span class="sxs-lookup"><span data-stu-id="7f24c-127">The common types are:</span></span>  
  
-   <span data-ttu-id="7f24c-128">SQL 使用者</span><span class="sxs-lookup"><span data-stu-id="7f24c-128">SQL User</span></span>  
  
-   <span data-ttu-id="7f24c-129">Windows 使用者</span><span class="sxs-lookup"><span data-stu-id="7f24c-129">Windows User</span></span>  
  
-   <span data-ttu-id="7f24c-130">資料庫角色</span><span class="sxs-lookup"><span data-stu-id="7f24c-130">Database Role</span></span>  
  
  
