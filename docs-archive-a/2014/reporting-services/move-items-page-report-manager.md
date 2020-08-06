---
title: 移動專案頁面 (報表管理員) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: fc83b8d2-bc79-4b56-8970-34a1cbbcc176
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 98ff306caf634a5f0478e2eba03c2313b24be274
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707261"
---
# <a name="move-items-page-report-manager"></a><span data-ttu-id="f9624-102">移動項目頁面 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="f9624-102">Move Items Page (Report Manager)</span></span>
  <span data-ttu-id="f9624-103">您可以使用 [移動項目] 頁面，將報表、資料夾或其他項目移至報表伺服器上的新位置。</span><span class="sxs-lookup"><span data-stu-id="f9624-103">Use the Move Items page to move a report, folder, or other item to a new location on the report server.</span></span> <span data-ttu-id="f9624-104">您可以輸入新位置的路徑，或使用樹狀檢視以導覽到報表伺服器命名空間中的新位置。</span><span class="sxs-lookup"><span data-stu-id="f9624-104">You can type the path of the new location or use a tree view to browse to a new location in the report server namespace.</span></span> <span data-ttu-id="f9624-105">您只能移動您有權移動並儲存在目前報表伺服器上的項目。</span><span class="sxs-lookup"><span data-stu-id="f9624-105">You can only move items that you have permission to move and that are stored on the current report server.</span></span>  
  
 <span data-ttu-id="f9624-106">當您移動了其他項目所參考的項目 (例如，許多報表所參考的共用資料來源或模型) 時，系統就會自動更新該項目的路徑資訊。</span><span class="sxs-lookup"><span data-stu-id="f9624-106">When you move an item that is referenced by another item (for example, a shared data source or model that is referenced by many reports), the path information for that item is updated automatically.</span></span> <span data-ttu-id="f9624-107">移動共用資料來源並不會中斷使用此共用資料來源之報表和模型的資料來源連接。</span><span class="sxs-lookup"><span data-stu-id="f9624-107">Moving a shared data source does not disrupt a data source connection to the reports and models that use it.</span></span> <span data-ttu-id="f9624-108">如果您將共用資料來源移至使用者沒有權限的資料夾，他們仍然能夠執行參考此資料來源或模型的任何報表，不過他們在資料夾階層中將看不到該項目。</span><span class="sxs-lookup"><span data-stu-id="f9624-108">If you move a shared data source or model to a folder for which users do not have permission, they will still be able to run any report that references the data source or model, however the item will not be visible to them in the folder hierarchy.</span></span>  
  
 <span data-ttu-id="f9624-109">針對 **[位置]**，請指定資料夾的完整路徑，由根資料夾名稱開始。</span><span class="sxs-lookup"><span data-stu-id="f9624-109">For **Location**, specify the full path to folder, beginning with the root folder name.</span></span> <span data-ttu-id="f9624-110">您可以輸入路徑名稱，或使用樹狀檢視以導覽到適當的資料夾。</span><span class="sxs-lookup"><span data-stu-id="f9624-110">You can type the path name or use the tree view to navigate to the folder you want.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f9624-111">並非所有項目都可以移動。</span><span class="sxs-lookup"><span data-stu-id="f9624-111">Not all items are movable.</span></span> <span data-ttu-id="f9624-112">您不可以移動保留的資料夾，例如 [主資料夾]、[我的報表] 或 [使用者資料夾]。</span><span class="sxs-lookup"><span data-stu-id="f9624-112">You cannot move reserved folders such as Home, My Reports, or Users Folders.</span></span> <span data-ttu-id="f9624-113">您不可以將報表記錄或快照集移至其他位置。</span><span class="sxs-lookup"><span data-stu-id="f9624-113">You cannot move report history or snapshots to different locations.</span></span> <span data-ttu-id="f9624-114">記錄與快照集一律會置於所依據報表的位置，且一律需要透過該報表存取。</span><span class="sxs-lookup"><span data-stu-id="f9624-114">History and snapshots are always located with, and accessed through, the report on which they are based.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="f9624-115">導覽</span><span class="sxs-lookup"><span data-stu-id="f9624-115">Navigation</span></span>  
 <span data-ttu-id="f9624-116">您可以使用下列程序，在使用者介面 (UI) 中導覽至這個位置。</span><span class="sxs-lookup"><span data-stu-id="f9624-116">Use the following procedures to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-move-items-page-from-the-contents-page-in-details-view"></a><span data-ttu-id="f9624-117">若要從詳細資料檢視的內容頁面開啟移動項目頁面</span><span class="sxs-lookup"><span data-stu-id="f9624-117">To open the Move Items page from the Contents page in Details View</span></span>  
  
1.  <span data-ttu-id="f9624-118">開啟報表管理員，然後導覽至包含您想要移動之項目的資料夾。</span><span class="sxs-lookup"><span data-stu-id="f9624-118">Open Report Manager, and navigate to the folder that contains an item you want to move.</span></span> <span data-ttu-id="f9624-119">您也可以從報表管理員首頁移動項目。</span><span class="sxs-lookup"><span data-stu-id="f9624-119">You can also move items from the Report Manager Home page.</span></span>  
  
2.  <span data-ttu-id="f9624-120">在工具列中，按一下 **[詳細資料檢視]**。</span><span class="sxs-lookup"><span data-stu-id="f9624-120">In the toolbar, click **Details View**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f9624-121"> 如果您只有看到 **[並排檢視]**，表示您已經在 **[詳細資料檢視]** 中。</span><span class="sxs-lookup"><span data-stu-id="f9624-121">If you see only **Tiles View**, you are already in **Details View**.</span></span>  
  
3.  <span data-ttu-id="f9624-122">選取項目旁的方塊，然後按一下工具列中的 **[移動]** 。</span><span class="sxs-lookup"><span data-stu-id="f9624-122">Select the box next to an item, and then click **Move** in the toolbar.</span></span> <span data-ttu-id="f9624-123">如果您想要將多個項目移至相同的新位置，也可以選取多個方塊。</span><span class="sxs-lookup"><span data-stu-id="f9624-123">You can select more than one box if you want to move multiple items to the same new location.</span></span>  
  
###### <a name="to-open-the-move-items-page-from-the-contents-page-in-tiles-view"></a><span data-ttu-id="f9624-124">若要從並排檢視的內容頁面開啟移動項目頁面</span><span class="sxs-lookup"><span data-stu-id="f9624-124">To open the Move Items page from the Contents page in Tiles View</span></span>  
  
1.  <span data-ttu-id="f9624-125">開啟報表管理員，然後導覽至包含您想要移動之項目的資料夾。</span><span class="sxs-lookup"><span data-stu-id="f9624-125">Open Report Manager, and navigate to the folder that contains an item you want to move.</span></span> <span data-ttu-id="f9624-126">您也可以從報表管理員首頁移動項目。</span><span class="sxs-lookup"><span data-stu-id="f9624-126">You can also move items from the Report Manager Home page.</span></span>  
  
2.  <span data-ttu-id="f9624-127">在工具列中，按一下 **[並排檢視]**。</span><span class="sxs-lookup"><span data-stu-id="f9624-127">In the toolbar, click **Tiles View**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f9624-128"> 如果您只有看到 **[詳細資料檢視]**，表示您已經在 **[並排檢視]** 中。</span><span class="sxs-lookup"><span data-stu-id="f9624-128">If you see only **Details View**, you are already in **Tiles View**.</span></span>  
  
3.  <span data-ttu-id="f9624-129">將滑鼠停留在該項目上，然後按一下下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="f9624-129">Hover over an item, and click the drop-down arrow.</span></span>  
  
4.  <span data-ttu-id="f9624-130">在下拉式功能表中，按一下 **[移動]**。</span><span class="sxs-lookup"><span data-stu-id="f9624-130">In the drop-down menu, click **Move**.</span></span>  
  
###### <a name="to-open-the-move-items-page-from-the-general-properties-page-of-an-item"></a><span data-ttu-id="f9624-131">若要從項目的一般屬性頁面開啟移動項目頁面</span><span class="sxs-lookup"><span data-stu-id="f9624-131">To open the Move Items page from the General Properties page of an item</span></span>  
  
1.  <span data-ttu-id="f9624-132">開啟報表管理員，然後導覽至包含您想要移動之項目的資料夾。</span><span class="sxs-lookup"><span data-stu-id="f9624-132">Open Report Manager, and navigate to the folder that contains an item you want to move.</span></span> <span data-ttu-id="f9624-133">您也可以從報表管理員首頁移動項目。</span><span class="sxs-lookup"><span data-stu-id="f9624-133">You can also move items from the Report Manager Home page.</span></span>  
  
2.  <span data-ttu-id="f9624-134">將滑鼠停留在該項目上，然後按一下下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="f9624-134">Hover over an item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="f9624-135">在下拉式功能表中，按一下 **[管理]**。</span><span class="sxs-lookup"><span data-stu-id="f9624-135">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="f9624-136">這樣就會開啟該項目的 [一般] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="f9624-136">This opens the General properties page for an item.</span></span>  
  
4.  <span data-ttu-id="f9624-137">在項目工具列中，按一下 **[移動]**。</span><span class="sxs-lookup"><span data-stu-id="f9624-137">In the item toolbar, click **Move**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9624-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9624-138">See Also</span></span>  
 <span data-ttu-id="f9624-139">[報表管理員 &#40;SSRS 原生模式&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="f9624-139">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="f9624-140">[一般屬性頁面、資料夾 &#40;報表管理員&#41;](../../2014/reporting-services/general-properties-page-folders-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="f9624-140">[General Properties Page, Folders &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-folders-report-manager.md) </span></span>  
 <span data-ttu-id="f9624-141">[一般屬性頁面、報表 &#40;報表管理員&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="f9624-141">[General Properties Page, Reports &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span></span>  
 <span data-ttu-id="f9624-142">[一般屬性頁面、資源 &#40;報表管理員&#41;](../../2014/reporting-services/general-properties-page-resources-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="f9624-142">[General Properties Page, Resources &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-resources-report-manager.md) </span></span>  
 <span data-ttu-id="f9624-143">[一般屬性頁面、共用資料來源 &#40;報表管理員&#41;](../../2014/reporting-services/general-properties-page-shared-data-sources-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="f9624-143">[General Properties Page, Shared Data Sources &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-shared-data-sources-report-manager.md) </span></span>  
 [<span data-ttu-id="f9624-144">報表管理員 F1 說明</span><span class="sxs-lookup"><span data-stu-id="f9624-144">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
