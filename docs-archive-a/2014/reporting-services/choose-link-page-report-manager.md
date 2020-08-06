---
title: 選擇連結頁面 (報表管理員) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a89a555d-efa3-45d6-951e-db78ec6a2c8e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bc40fe726555babee8d9940e198a93577bd6a09f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593867"
---
# <a name="choose-link-page-report-manager"></a><span data-ttu-id="e45cf-102">選擇連結頁面 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="e45cf-102">Choose Link Page (Report Manager)</span></span>
  <span data-ttu-id="e45cf-103">使用 [選擇連結] 頁面來選擇不同的報表，作為目前已選取連結報表的基礎。</span><span class="sxs-lookup"><span data-stu-id="e45cf-103">Use the Choose Link page to choose a different report upon which to base the currently selected linked report.</span></span> <span data-ttu-id="e45cf-104">連結報表以已經發行至報表伺服器的其他報表為基礎。</span><span class="sxs-lookup"><span data-stu-id="e45cf-104">Linked reports are based on other reports already published to a report server.</span></span> <span data-ttu-id="e45cf-105">連結報表會使用基底報表的配置和資料，但是具有個別的屬性頁面，可讓您自訂參數屬性、安全性設定、名稱、描述和位置。</span><span class="sxs-lookup"><span data-stu-id="e45cf-105">A linked report uses the layout and data of the base report, but has separate property pages so that you can customize parameter properties, security settings, name, description, and location.</span></span>  
  
 <span data-ttu-id="e45cf-106">透過 [選擇連結] 頁面，您可以選擇不同的已發行報表，以便與連結報表搭配使用。</span><span class="sxs-lookup"><span data-stu-id="e45cf-106">Through the Choose Link page, you can choose a different published report to use with the linked report.</span></span> <span data-ttu-id="e45cf-107">連結報表的其他設定 (例如安全性和參數設定) 不受連結資訊的變更所影響。</span><span class="sxs-lookup"><span data-stu-id="e45cf-107">Other settings of the linked report (such as security and parameter settings) are unaffected by changes to the link information.</span></span> <span data-ttu-id="e45cf-108">由於報表伺服器將不會驗證您的選項，因此請務必選擇與您在連結報表上指定之設定具有相同參數的報表。</span><span class="sxs-lookup"><span data-stu-id="e45cf-108">The report server will not validate your selection, so be sure to choose a report that has the same parameters as those you specified on the linked report.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="e45cf-109">導覽</span><span class="sxs-lookup"><span data-stu-id="e45cf-109">Navigation</span></span>  
 <span data-ttu-id="e45cf-110">您可以使用下列程序，在使用者介面 (UI) 中導覽至這個位置。</span><span class="sxs-lookup"><span data-stu-id="e45cf-110">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-choose-link-page"></a><span data-ttu-id="e45cf-111">若要開啟選擇連結頁面</span><span class="sxs-lookup"><span data-stu-id="e45cf-111">To open the Choose Link page</span></span>  
  
1.  <span data-ttu-id="e45cf-112">開啟報表管理員，然後找出您想要變更的連結報表。</span><span class="sxs-lookup"><span data-stu-id="e45cf-112">Open Report Manager, and locate the linked report you want to change.</span></span>  
  
2.  <span data-ttu-id="e45cf-113">將滑鼠停留在該連結報表上，然後按一下下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="e45cf-113">Hover over the linked report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="e45cf-114">在下拉式功能表中，按一下 **[管理]**。</span><span class="sxs-lookup"><span data-stu-id="e45cf-114">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="e45cf-115">這樣就會開啟該連結報表的 **[一般]** 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="e45cf-115">This opens the **General** properties page for the linked report.</span></span>  
  
4.  <span data-ttu-id="e45cf-116">在 **[一般]** 索引標籤的屬性頁面上，按一下 **[變更連結]**。</span><span class="sxs-lookup"><span data-stu-id="e45cf-116">On the **General** tab, on the properties page, click **Change Link**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e45cf-117">選項</span><span class="sxs-lookup"><span data-stu-id="e45cf-117">Options</span></span>  
 <span data-ttu-id="e45cf-118">**位置**</span><span class="sxs-lookup"><span data-stu-id="e45cf-118">**Location**</span></span>  
 <span data-ttu-id="e45cf-119">指定已發行報表的完整名稱，包括資料夾路徑和報表名稱。</span><span class="sxs-lookup"><span data-stu-id="e45cf-119">Specify the full name of the published report, including the folder path and report name.</span></span> <span data-ttu-id="e45cf-120">您可以輸入報表的完整名稱，或使用樹狀檢視來導覽至您要使用的報表。</span><span class="sxs-lookup"><span data-stu-id="e45cf-120">You can type the full name of the report or use the tree view to navigate to the report you want to use.</span></span>  
  
 <span data-ttu-id="e45cf-121">**樹狀檢視**</span><span class="sxs-lookup"><span data-stu-id="e45cf-121">**Tree view**</span></span>  
 <span data-ttu-id="e45cf-122">顯示報表伺服器資料夾階層中全部的資料夾。</span><span class="sxs-lookup"><span data-stu-id="e45cf-122">Shows all of the folders in the report server folder hierarchy.</span></span> <span data-ttu-id="e45cf-123">若要使用樹狀檢視來填寫 **[位置]** 欄位，請按一下報表的名稱。</span><span class="sxs-lookup"><span data-stu-id="e45cf-123">To use the tree view to fill in the **Location** field, click the name of the report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e45cf-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e45cf-124">See Also</span></span>  
 <span data-ttu-id="e45cf-125">[一般屬性頁面、報表 &#40;報表管理員&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="e45cf-125">[General Properties Page, Reports &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span></span>  
 <span data-ttu-id="e45cf-126">[新的連結報表頁面 &#40;報表管理員&#41;](../../2014/reporting-services/new-linked-report-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="e45cf-126">[New Linked Report Page &#40;Report Manager&#41;](../../2014/reporting-services/new-linked-report-page-report-manager.md) </span></span>  
 [<span data-ttu-id="e45cf-127">報表管理員 F1 說明</span><span class="sxs-lookup"><span data-stu-id="e45cf-127">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
