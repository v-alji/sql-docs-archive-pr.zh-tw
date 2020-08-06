---
title: 相依專案頁面 (報表管理員) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4dcfb311-e9c3-4c5d-b2e0-018d79f37d2e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 488b10d7d7985972274340897ee3975618a12639
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592534"
---
# <a name="dependent-items-page-report-manager"></a><span data-ttu-id="88fb8-102">相依項目頁面 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="88fb8-102">Dependent Items Page (Report Manager)</span></span>
  <span data-ttu-id="88fb8-103">您可以使用 [相依項目] 頁面來檢視參考共用資料來源的報表和模型清單。</span><span class="sxs-lookup"><span data-stu-id="88fb8-103">Use the Dependent Items page to view a list of reports and models that reference a shared data source.</span></span> <span data-ttu-id="88fb8-104">每一個項目類型的圖示表示該項目是報表或模型。</span><span class="sxs-lookup"><span data-stu-id="88fb8-104">The icon for each item type indicates whether it is a report or a model.</span></span> <span data-ttu-id="88fb8-105">檢視這個頁面可以使用清單檢視或詳細資料檢視。</span><span class="sxs-lookup"><span data-stu-id="88fb8-105">This page can be viewed in list view or details view.</span></span> <span data-ttu-id="88fb8-106">使用詳細資料檢視來顯示有關每一個項目的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="88fb8-106">Use details view to show more information about each item.</span></span> <span data-ttu-id="88fb8-107">詳細資料檢視有其他頁面選項可用。</span><span class="sxs-lookup"><span data-stu-id="88fb8-107">Additional page options are available in details view.</span></span> <span data-ttu-id="88fb8-108">為了協助您管理共用資料來源，這個頁面提供了使用資料來源之報表和模型的連結、有關上次執行或修改報表或模型之時間的標準，以及 [刪除] 和 [移動] 按鈕，以便您可以輕易地移除不再使用的報表和模型，或在您判斷是否仍然需要它們時，將它們移至不同的位置。</span><span class="sxs-lookup"><span data-stu-id="88fb8-108">To help you manage the shared data source, this page provides links to reports and models that use the data source, metrics on when the report or model was last run or modified, and Delete and Move buttons so that you can easily remove reports and models that are no longer used, or move them to a different location while you determine whether they are still needed.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="88fb8-109">導覽</span><span class="sxs-lookup"><span data-stu-id="88fb8-109">Navigation</span></span>  
 <span data-ttu-id="88fb8-110">您可以使用下列程序，在使用者介面 (UI) 中導覽至這個位置。</span><span class="sxs-lookup"><span data-stu-id="88fb8-110">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-dependent-items-page"></a><span data-ttu-id="88fb8-111">若要開啟相依項目頁面</span><span class="sxs-lookup"><span data-stu-id="88fb8-111">To open the Dependent Items page</span></span>  
  
1.  <span data-ttu-id="88fb8-112">開啟報表管理員，然後找出您想要檢視相依項目的共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="88fb8-112">Open Report Manager, and locate the shared data source for which you want to view dependent items.</span></span>  
  
2.  <span data-ttu-id="88fb8-113">將滑鼠停留在該項目上，然後按一下下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="88fb8-113">Hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="88fb8-114">在下拉式功能表中，按一下 **[管理]**。</span><span class="sxs-lookup"><span data-stu-id="88fb8-114">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="88fb8-115">這樣就會開啟該資料來源的 [一般] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="88fb8-115">This opens the General properties page for the data source.</span></span>  
  
4.  <span data-ttu-id="88fb8-116">選取 **[相依項目]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="88fb8-116">Select the **Dependent Items** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="88fb8-117">選項。</span><span class="sxs-lookup"><span data-stu-id="88fb8-117">Options</span></span>  
 <span data-ttu-id="88fb8-118">**名稱**</span><span class="sxs-lookup"><span data-stu-id="88fb8-118">**Name**</span></span>  
 <span data-ttu-id="88fb8-119">顯示報表或模型的名稱。</span><span class="sxs-lookup"><span data-stu-id="88fb8-119">Shows the name of the report or model.</span></span> <span data-ttu-id="88fb8-120">按一下報表名稱將它開啟。</span><span class="sxs-lookup"><span data-stu-id="88fb8-120">Click the name of the report to open it.</span></span> <span data-ttu-id="88fb8-121">按一下模型的名稱則可開啟它的屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="88fb8-121">Click the name of the model to open its property pages.</span></span>  
  
 <span data-ttu-id="88fb8-122">**說明**</span><span class="sxs-lookup"><span data-stu-id="88fb8-122">**Description**</span></span>  
 <span data-ttu-id="88fb8-123">顯示報表或模型的描述。</span><span class="sxs-lookup"><span data-stu-id="88fb8-123">Shows the description of the report or model.</span></span>  
  
 <span data-ttu-id="88fb8-124">**刪除**</span><span class="sxs-lookup"><span data-stu-id="88fb8-124">**Delete**</span></span>  
 <span data-ttu-id="88fb8-125">按一下即可從報表伺服器資料庫中刪除報表或模型。</span><span class="sxs-lookup"><span data-stu-id="88fb8-125">Click to delete the report or model from the report server database.</span></span> <span data-ttu-id="88fb8-126">在按一下 **[刪除]** 之前，請先選取要刪除之每一個項目旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="88fb8-126">Before clicking **Delete**, select the check box next to each item that you want to delete.</span></span>  
  
 <span data-ttu-id="88fb8-127">**移動**</span><span class="sxs-lookup"><span data-stu-id="88fb8-127">**Move**</span></span>  
 <span data-ttu-id="88fb8-128">按一下即可在資料夾階層中重新定位報表或模型。</span><span class="sxs-lookup"><span data-stu-id="88fb8-128">Click to relocate a report or model within the folder hierarchy.</span></span> <span data-ttu-id="88fb8-129">在按一下 **[移動]** 之前，請先選取您要移動之每個項目旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="88fb8-129">Before clicking **Move**, select the check box next to each item that you want to move.</span></span> <span data-ttu-id="88fb8-130">這樣做會開啟 [移動項目] 頁面，如此您就可以在其中瀏覽資料夾以選取新位置。</span><span class="sxs-lookup"><span data-stu-id="88fb8-130">This opens the Move Items page, where you can browse through folders to select a new location.</span></span>  
  
 <span data-ttu-id="88fb8-131">**編輯**</span><span class="sxs-lookup"><span data-stu-id="88fb8-131">**Edit**</span></span>  
 <span data-ttu-id="88fb8-132">按一下 [屬性] 圖示即可存取報表或模型的屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="88fb8-132">Click the Property icon to access the property pages of a report, or model.</span></span>  
  
 <span data-ttu-id="88fb8-133">**型別**</span><span class="sxs-lookup"><span data-stu-id="88fb8-133">**Type**</span></span>  
 <span data-ttu-id="88fb8-134">顯示項目類型的圖示。</span><span class="sxs-lookup"><span data-stu-id="88fb8-134">Shows the icon of the item type.</span></span>  
  
 <span data-ttu-id="88fb8-135">**修改日期**</span><span class="sxs-lookup"><span data-stu-id="88fb8-135">**Modified Date**</span></span>  
 <span data-ttu-id="88fb8-136">顯示上次修改報表或模型的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="88fb8-136">Shows the date and time when the report or model was last modified.</span></span>  
  
 <span data-ttu-id="88fb8-137">**修改者**</span><span class="sxs-lookup"><span data-stu-id="88fb8-137">**Modified By**</span></span>  
 <span data-ttu-id="88fb8-138">顯示上次修改項目屬性的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="88fb8-138">Shows the name of the user who last modified the item properties.</span></span>  
  
 <span data-ttu-id="88fb8-139">**執行時**</span><span class="sxs-lookup"><span data-stu-id="88fb8-139">**When Run**</span></span>  
 <span data-ttu-id="88fb8-140">針對以報表執行快照集執行的報表，顯示上次重新整理報表的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="88fb8-140">For reports that run as report execution snapshots, displays the date and time at which the report was last refreshed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88fb8-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88fb8-141">See Also</span></span>  
 <span data-ttu-id="88fb8-142">[報表管理員 F1 說明](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="88fb8-142">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 <span data-ttu-id="88fb8-143">[報表管理員 &#40;SSRS 原生模式&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="88fb8-143">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="88fb8-144">[[內容] 頁面 &#40;報表管理員&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="88fb8-144">[Contents Page &#40;Report Manager&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span></span>  
 [<span data-ttu-id="88fb8-145">報表管理員 F1 說明</span><span class="sxs-lookup"><span data-stu-id="88fb8-145">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
