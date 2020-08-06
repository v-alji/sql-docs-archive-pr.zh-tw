---
title: 快照集選項屬性頁面 (報表管理員) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f6641f59-5267-4f57-8957-63b93d1a9679
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3025b23dfe498a92c2ce1d8535229d8d23dfd429
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687414"
---
# <a name="snapshot-options-properties-page-report-manager"></a><span data-ttu-id="06823-102">快照集選項屬性頁面 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="06823-102">Snapshot Options Properties Page (Report Manager)</span></span>
  <span data-ttu-id="06823-103">使用 [快照集選項] 屬性頁面可以排程要加入至報表記錄的報表快照集，以及設定報表記錄中儲存之報表快照集的數目限制。</span><span class="sxs-lookup"><span data-stu-id="06823-103">Use the Snapshot Options properties page to schedule report snapshots to be added to report history, and to set limits on the number of report snapshots that are stored in report history.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="06823-104">並非所有 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]版本都提供此功能。</span><span class="sxs-lookup"><span data-stu-id="06823-104">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="06823-105">如需版本支援的功能清單 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，請參閱[其他資料庫服務](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md#Add_DBServices)。</span><span class="sxs-lookup"><span data-stu-id="06823-105">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Additional Database Services](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md#Add_DBServices).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="06823-106">導覽</span><span class="sxs-lookup"><span data-stu-id="06823-106">Navigation</span></span>  
 <span data-ttu-id="06823-107">您可以使用下列程序，在使用者介面 (UI) 中導覽至這個位置。</span><span class="sxs-lookup"><span data-stu-id="06823-107">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
### <a name="to-open-the-snapshot-options-properties-page-for-a-report"></a><span data-ttu-id="06823-108">若要開啟報表的快照集選項屬性頁面</span><span class="sxs-lookup"><span data-stu-id="06823-108">To open the Snapshot Options properties page for a report</span></span>  
  
1.  <span data-ttu-id="06823-109">開啟報表管理員，然後找出您想要設定報表快照集屬性的報表。</span><span class="sxs-lookup"><span data-stu-id="06823-109">Open Report Manager, and locate the report for which you want to configure report snapshot properties.</span></span>  
  
2.  <span data-ttu-id="06823-110">將滑鼠停留在該報表上，然後按一下下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="06823-110">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="06823-111">在下拉式功能表中，按一下 **[管理]**。</span><span class="sxs-lookup"><span data-stu-id="06823-111">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="06823-112">這樣就會開啟該報表的 [一般] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="06823-112">This opens the General properties page for the report.</span></span>  
  
4.  <span data-ttu-id="06823-113">選取 **[快照集選項]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="06823-113">Select the **Snapshot Options** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="06823-114">選項</span><span class="sxs-lookup"><span data-stu-id="06823-114">Options</span></span>  
 <span data-ttu-id="06823-115">**允許手動建立報表記錄**</span><span class="sxs-lookup"><span data-stu-id="06823-115">**Allow report history to be created manually**</span></span>  
 <span data-ttu-id="06823-116">選取此核取方塊，即可視需要將快照集加入報表記錄中。</span><span class="sxs-lookup"><span data-stu-id="06823-116">Select this check box to add snapshots to report history as needed.</span></span> <span data-ttu-id="06823-117">選取此核取方塊會使 **[新增快照集]** 按鈕出現在 [記錄] 頁面上。</span><span class="sxs-lookup"><span data-stu-id="06823-117">Selecting this check box causes the **New Snapshot** button to appear on the History page.</span></span>  
  
 <span data-ttu-id="06823-118">**將所有報表執行快照集儲存至報表記錄**</span><span class="sxs-lookup"><span data-stu-id="06823-118">**Store all report execution snapshots in report history**</span></span>  
 <span data-ttu-id="06823-119">選取此核取方塊，將根據報表執行屬性所建立的報表快照集，複製到報表記錄。</span><span class="sxs-lookup"><span data-stu-id="06823-119">Select this check box to copy a report snapshot that you generate based on report execution properties to report history.</span></span> <span data-ttu-id="06823-120">可以將報表執行屬性設定為，從產生的快照集來執行報表。</span><span class="sxs-lookup"><span data-stu-id="06823-120">You can set report execution properties to run a report from a generated snapshot.</span></span> <span data-ttu-id="06823-121">設定此報表記錄屬性，就可以將所有長期產生的報表快照集複本，放入報表記錄中作為保存。</span><span class="sxs-lookup"><span data-stu-id="06823-121">By setting this report history property, you can keep a record of all reports snapshots that are generated over time by placing copies of them in report history.</span></span>  
  
 <span data-ttu-id="06823-122">**使用下列排程將快照集加入至報表記錄**</span><span class="sxs-lookup"><span data-stu-id="06823-122">**Use the following schedule to add snapshots to report history**</span></span>  
 <span data-ttu-id="06823-123">選取此核取方塊，即可根據排程將快照集加入報表記錄中。</span><span class="sxs-lookup"><span data-stu-id="06823-123">Select this check box to add snapshots to report history on a scheduled basis.</span></span> <span data-ttu-id="06823-124">您可以建立專用於此目的的排程，或者當某個預先定義的共用排程包含您要的排程資訊，可以選擇預先定義的共用排程。</span><span class="sxs-lookup"><span data-stu-id="06823-124">You can create a schedule that is used exclusively for this purpose, or you can select a predefined shared schedule if one contains the schedule information you want.</span></span>  
  
 <span data-ttu-id="06823-125">**選取要保留的快照集數目**</span><span class="sxs-lookup"><span data-stu-id="06823-125">**Select the number of snapshots to keep**</span></span>  
 <span data-ttu-id="06823-126">選取下列選項來控制報表記錄中保留的報表數目。</span><span class="sxs-lookup"><span data-stu-id="06823-126">Select from the following options to control the number of reports that are kept in report history.</span></span> <span data-ttu-id="06823-127">報表記錄設定可以隨每一個報表而改變。</span><span class="sxs-lookup"><span data-stu-id="06823-127">Report history settings can vary for each report.</span></span>  
  
-   <span data-ttu-id="06823-128">選取 **[使用預設值]** 即可保留預設值。</span><span class="sxs-lookup"><span data-stu-id="06823-128">Select **Use default setting** to retain the default setting.</span></span> <span data-ttu-id="06823-129">報表伺服器管理員控制報表記錄儲存的主要設定。</span><span class="sxs-lookup"><span data-stu-id="06823-129">The report server administrator controls a master setting for report history storage.</span></span> <span data-ttu-id="06823-130">若您選擇此選項，則可由此主要設定中取得保留的快照集數目。</span><span class="sxs-lookup"><span data-stu-id="06823-130">If you choose this option, the number of snapshots that are retained is obtained from this master setting.</span></span>  
  
-   <span data-ttu-id="06823-131">選取 **[不限制報表記錄中的快照集數目]** ，即可保留所有的報表記錄快照集。</span><span class="sxs-lookup"><span data-stu-id="06823-131">Select **Keep an unlimited number of snapshots in report history** to retain all report history snapshots.</span></span> <span data-ttu-id="06823-132">您必須手動刪除快照集以縮減報表記錄的大小。</span><span class="sxs-lookup"><span data-stu-id="06823-132">You must manually delete snapshots to reduce the size of report history.</span></span>  
  
-   <span data-ttu-id="06823-133">選取 **[限制報表記錄的副本]** ，即可保留固定的快照集數目。</span><span class="sxs-lookup"><span data-stu-id="06823-133">Select **Limit the copies of report history** to retain a set number of snapshots.</span></span> <span data-ttu-id="06823-134">當達到限制時，就會從報表記錄中移除較舊的複本，增加較新複本所需的空間。</span><span class="sxs-lookup"><span data-stu-id="06823-134">When the limit is reached, older copies are removed from report history to make room for newer copies.</span></span>  
  
 <span data-ttu-id="06823-135">報表記錄會儲存在報表伺服器資料庫中。</span><span class="sxs-lookup"><span data-stu-id="06823-135">Report history is stored in the report server database.</span></span> <span data-ttu-id="06823-136">如果您有想要保留記錄的大型報表或許多報表，請考慮限制報表記錄的數量，以便協助管理報表伺服器資料庫的磁碟空間需求。</span><span class="sxs-lookup"><span data-stu-id="06823-136">If you have large reports or numerous reports for which you want to maintain history, consider limiting the amount of report history to help manage the disk space requirements of the report server database.</span></span>  
  
 <span data-ttu-id="06823-137">**套用**</span><span class="sxs-lookup"><span data-stu-id="06823-137">**Apply**</span></span>  
 <span data-ttu-id="06823-138">按一下即可儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="06823-138">Click to save your changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06823-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06823-139">See Also</span></span>  
 <span data-ttu-id="06823-140">[將快照集加入至報表記錄 &#40;報表管理員&#41;](report-server/add-a-snapshot-to-report-history-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="06823-140">[Add a Snapshot to Report History &#40;Report Manager&#41;](report-server/add-a-snapshot-to-report-history-report-manager.md) </span></span>  
 <span data-ttu-id="06823-141">[報表管理員 &#40;SSRS 原生模式&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="06823-141">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="06823-142">[建立、修改及刪除報表記錄中的快照集](report-server/create-modify-and-delete-snapshots-in-report-history.md) </span><span class="sxs-lookup"><span data-stu-id="06823-142">[Create, Modify, and Delete Snapshots in Report History](report-server/create-modify-and-delete-snapshots-in-report-history.md) </span></span>  
 [<span data-ttu-id="06823-143">報表管理員 F1 說明</span><span class="sxs-lookup"><span data-stu-id="06823-143">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
