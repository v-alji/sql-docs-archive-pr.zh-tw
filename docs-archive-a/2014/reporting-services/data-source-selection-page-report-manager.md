---
title: 資料來源選取頁面 (報表管理員) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 7f7e8b19-0c0b-4b1f-9cc1-057099aa07eb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 03c5558397786b02b764b78d47584d9b190290cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597637"
---
# <a name="data-source-selection-page-report-manager"></a><span data-ttu-id="3d3dd-102">資料來源選擇頁面 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="3d3dd-102">Data Source Selection Page (Report Manager)</span></span>
  <span data-ttu-id="3d3dd-103">您可以使用 [資料來源選擇] 頁面來選取要搭配報表或報表模型使用的現有共用資料來源項目。</span><span class="sxs-lookup"><span data-stu-id="3d3dd-103">Use the Data Source Selection page to select an existing shared data source item to use with a report or a report model.</span></span> <span data-ttu-id="3d3dd-104">您也可以使用此頁面來選取不同的資料來源。</span><span class="sxs-lookup"><span data-stu-id="3d3dd-104">You can also use this page to select a different data source.</span></span> <span data-ttu-id="3d3dd-105">若要檢視資料來源類型或連接字串，您必須導覽到共用資料來源並開啟屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="3d3dd-105">To view the data source type or connection string, you must navigate to the shared data source and open the property pages.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="3d3dd-106">導覽</span><span class="sxs-lookup"><span data-stu-id="3d3dd-106">Navigation</span></span>  
 <span data-ttu-id="3d3dd-107">您可以使用下列程序，在使用者介面 (UI) 中導覽至這個位置。</span><span class="sxs-lookup"><span data-stu-id="3d3dd-107">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-data-source-selection-page"></a><span data-ttu-id="3d3dd-108">若要開啟資料來源選擇頁面</span><span class="sxs-lookup"><span data-stu-id="3d3dd-108">To open the Data Source Selection page</span></span>  
  
1.  <span data-ttu-id="3d3dd-109">開啟報表管理員，然後找出您想要選取資料來源的報表或模型。</span><span class="sxs-lookup"><span data-stu-id="3d3dd-109">Open Report Manager, and locate the report or model for which you want to select a data source.</span></span>  
  
2.  <span data-ttu-id="3d3dd-110">將滑鼠停留在該報表上，然後按一下下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="3d3dd-110">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="3d3dd-111">在下拉式功能表中，按一下 **[管理]**。</span><span class="sxs-lookup"><span data-stu-id="3d3dd-111">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="3d3dd-112">這樣就會開啟該報表或模型的 [一般] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="3d3dd-112">This opens the General properties page for the report or model.</span></span>  
  
4.  <span data-ttu-id="3d3dd-113">選取 **[資料來源]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3d3dd-113">Select the **Data Sources** tab.</span></span>  
  
5.  <span data-ttu-id="3d3dd-114">在屬性窗格中，選取 **[共用資料來源]** ，然後按一下 **[瀏覽]**。</span><span class="sxs-lookup"><span data-stu-id="3d3dd-114">In the properties pane, select **A shared data source** and then click **Browse**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="3d3dd-115">選項</span><span class="sxs-lookup"><span data-stu-id="3d3dd-115">Options</span></span>  
 <span data-ttu-id="3d3dd-116">**位置**</span><span class="sxs-lookup"><span data-stu-id="3d3dd-116">**Location**</span></span>  
 <span data-ttu-id="3d3dd-117">指定共用資料來源項目的完整路徑，由根資料夾名稱開始。</span><span class="sxs-lookup"><span data-stu-id="3d3dd-117">Specify the full path to the shared data source item, beginning with the root folder name.</span></span> <span data-ttu-id="3d3dd-118">您可以輸入路徑名稱，或使用樹狀檢視來瀏覽想要的共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="3d3dd-118">You can type the path name or use the tree view to navigate to the shared data source you want.</span></span>  
  
 <span data-ttu-id="3d3dd-119">**樹狀檢視**</span><span class="sxs-lookup"><span data-stu-id="3d3dd-119">**Tree view**</span></span>  
 <span data-ttu-id="3d3dd-120">顯示報表伺服器命名空間的資料夾結構。</span><span class="sxs-lookup"><span data-stu-id="3d3dd-120">Shows the folder structure of the report server namespace.</span></span> <span data-ttu-id="3d3dd-121">按一下共用資料來源項目，即可將完整路徑加入至 **[位置]** 欄位。</span><span class="sxs-lookup"><span data-stu-id="3d3dd-121">Click a shared data source item to add the full path to the **Location** field.</span></span>  
  
 <span data-ttu-id="3d3dd-122">**確定**</span><span class="sxs-lookup"><span data-stu-id="3d3dd-122">**OK**</span></span>  
 <span data-ttu-id="3d3dd-123">按一下即可將資料來源選擇複製到 [資料來源] 屬性頁面上。</span><span class="sxs-lookup"><span data-stu-id="3d3dd-123">Click to copy the data source selection to the Data Sources properties page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d3dd-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d3dd-124">See Also</span></span>  
 <span data-ttu-id="3d3dd-125">[管理報表資料來源](report-data/manage-report-data-sources.md) </span><span class="sxs-lookup"><span data-stu-id="3d3dd-125">[Manage Report Data Sources](report-data/manage-report-data-sources.md) </span></span>  
 <span data-ttu-id="3d3dd-126">[指定報表資料來源的認證及連接資訊](report-data/specify-credential-and-connection-information-for-report-data-sources.md) </span><span class="sxs-lookup"><span data-stu-id="3d3dd-126">[Specify Credential and Connection Information for Report Data Sources](report-data/specify-credential-and-connection-information-for-report-data-sources.md) </span></span>  
 <span data-ttu-id="3d3dd-127">[資料來源屬性頁面 &#40;報表管理員&#41;](../../2014/reporting-services/data-sources-properties-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="3d3dd-127">[Data Sources Properties Page &#40;Report Manager&#41;](../../2014/reporting-services/data-sources-properties-page-report-manager.md) </span></span>  
 <span data-ttu-id="3d3dd-128">[新增資料來源頁面 &#40;報表管理員&#41;](../../2014/reporting-services/new-data-source-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="3d3dd-128">[New Data Source Page &#40;Report Manager&#41;](../../2014/reporting-services/new-data-source-page-report-manager.md) </span></span>  
 [<span data-ttu-id="3d3dd-129">報表管理員 F1 說明</span><span class="sxs-lookup"><span data-stu-id="3d3dd-129">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
