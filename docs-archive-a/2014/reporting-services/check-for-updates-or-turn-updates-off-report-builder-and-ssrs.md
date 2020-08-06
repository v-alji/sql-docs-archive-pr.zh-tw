---
title: 檢查是否有更新，或關閉 (報表產生器和 SSRS) 的更新 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9c69792d-d7c4-453b-ae2f-6d2d071d8606
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 088d41e71d770f746367f2760cff8ff67b15623c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595798"
---
# <a name="check-for-updates-or-turn-updates-off-report-builder-and-ssrs"></a><span data-ttu-id="b74c4-102">檢查更新或關閉更新 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="b74c4-102">Check for Updates or Turn Updates Off (Report Builder and SSRS)</span></span>
  <span data-ttu-id="b74c4-103">每當您開啟報表時，報表產生器都會檢查報表伺服器或與報表伺服器整合的 SharePoint 網站上是否已經更新該報表中已發行的報表組件執行個體。</span><span class="sxs-lookup"><span data-stu-id="b74c4-103">Every time you open a report, Report Builder checks to see if the published instances of report parts in that report have been updated on the report server or SharePoint site integrated with a report server.</span></span> <span data-ttu-id="b74c4-104">它也會檢查報表組件的相依項目 (如資料集和參數) 是否有變更。</span><span class="sxs-lookup"><span data-stu-id="b74c4-104">It also checks for changes in the report parts' dependent items, such as the dataset and parameters.</span></span> <span data-ttu-id="b74c4-105">如果網站或伺服器上已經更新任何報表組件或其相依性，報表中的資訊列會顯示更新的組件數。</span><span class="sxs-lookup"><span data-stu-id="b74c4-105">If any report parts or their dependencies have been updated on the site or server, an information bar in your report displays the number of updated parts.</span></span> <span data-ttu-id="b74c4-106">您可以選擇檢視並接受或拒絕更新，或是解除資訊列。</span><span class="sxs-lookup"><span data-stu-id="b74c4-106">You can choose to view and accept or reject the updates, or dismiss the information bar.</span></span>  
  
 <span data-ttu-id="b74c4-107">您也可以停用資訊列，如此一來，當已發行的報表組件執行個體變更時，您將不會收到通知。</span><span class="sxs-lookup"><span data-stu-id="b74c4-107">You can also disable the information bar and not be informed if published instances of report parts have changed.</span></span> <span data-ttu-id="b74c4-108">這是一項使用者設定，您所開啟的所有報表都會停用這項設定。</span><span class="sxs-lookup"><span data-stu-id="b74c4-108">This is a user setting; it will be disabled for all reports that you open.</span></span> <span data-ttu-id="b74c4-109">即使您停用了資訊列，還是可以檢查更新。</span><span class="sxs-lookup"><span data-stu-id="b74c4-109">Even if you have disabled the information bar, you can still check for updates.</span></span>  
  
### <a name="to-turn-on-and-off-report-part-updates"></a><span data-ttu-id="b74c4-110">若要開啟和關閉報表組件更新</span><span class="sxs-lookup"><span data-stu-id="b74c4-110">To turn on and off report part updates</span></span>  
  
1.  <span data-ttu-id="b74c4-111">按一下 [報表產生器] 按鈕，然後按一下 [**選項**]。</span><span class="sxs-lookup"><span data-stu-id="b74c4-111">Click the Report Builder button, and then click **Options**.</span></span>  
  
2.  <span data-ttu-id="b74c4-112">在 [**選項**] 對話方塊的 [**資源**] 索引標籤上，選取或清除 [在**我的報表中顯示報表元件的更新**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="b74c4-112">In the **Options** dialog box, on the **Resources** tab, select or clear the **Show updates to report parts in my reports** check box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b74c4-113">這是使用者設定。</span><span class="sxs-lookup"><span data-stu-id="b74c4-113">This is a user setting.</span></span> <span data-ttu-id="b74c4-114">您所開啟的所有報表都會停用這項設定。</span><span class="sxs-lookup"><span data-stu-id="b74c4-114">It will be disabled for all reports that you open.</span></span>  
  
### <a name="to-check-for-updates"></a><span data-ttu-id="b74c4-115">若要檢查更新</span><span class="sxs-lookup"><span data-stu-id="b74c4-115">To check for updates</span></span>  
  
-   <span data-ttu-id="b74c4-116">以滑鼠右鍵按一下報表外部的設計介面，或在報表主體中，按一下 [**檢查更新**]。</span><span class="sxs-lookup"><span data-stu-id="b74c4-116">Right-click the design surface outside the report, or in the report body, and click **Check for Updates**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b74c4-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b74c4-117">See Also</span></span>  
 <span data-ttu-id="b74c4-118">[報表元件 &#40;報表產生器和 SSRS&#41;](report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b74c4-118">[Report Parts &#40;Report Builder and SSRS&#41;](report-parts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="b74c4-119">[報表產生器和 SSRS &#40;發行和重新發佈報表元件&#41;](report-design/publish-and-republish-report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b74c4-119">[Publish and Republish Report Parts &#40;Report Builder and SSRS&#41;](report-design/publish-and-republish-report-parts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="b74c4-120">[流覽報表元件，並 &#40;報表產生器和 SSRS 設定預設資料夾&#41;](report-design/browse-for-report-parts-and-set-a-default-folder-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b74c4-120">[Browse for Report Parts and Set a Default Folder &#40;Report Builder and SSRS&#41;](report-design/browse-for-report-parts-and-set-a-default-folder-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="b74c4-121">[&#40;報表產生器和 SSRS&#41;疑難排解報表元件](../../2014/reporting-services/troubleshoot-report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b74c4-121">[Troubleshoot Report Parts &#40;Report Builder and SSRS&#41;](../../2014/reporting-services/troubleshoot-report-parts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="b74c4-122">報表產生器中的報表組件和資料集</span><span class="sxs-lookup"><span data-stu-id="b74c4-122">Report Parts and Datasets in Report Builder</span></span>](report-data/report-parts-and-datasets-in-report-builder.md)  
  
  
