---
title: 將報表或模型繫結至共用資料來源 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- shared data sources [Reporting Services]
- data sources [Reporting Services], shared
ms.assetid: 23cc15f2-2883-48e2-bc6c-fa0ab61a2e21
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 596caba042d476173b3c49d1ad18e79d0827fe89
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688602"
---
# <a name="bind-a-report-or-model-to-a-shared-data-source-ssrs"></a><span data-ttu-id="8498a-102">將報表或模型繫結至共用資料來源 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="8498a-102">Bind a Report or Model to a Shared Data Source (SSRS)</span></span>
  <span data-ttu-id="8498a-103">在某些情況下 (例如，將報表或模型從測試伺服器移到實際伺服器時)，您可能想先將檔案儲存在本機電腦，然後再上傳到不同報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="8498a-103">In some situations, such as when you move a report or model from a test server to a production server, you might want to save the file to your local computer and then upload it to a different report server.</span></span> <span data-ttu-id="8498a-104">當您將報表或模型上傳到新伺服器時，您必須將它重新繫結至新報表伺服器上儲存的共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="8498a-104">When you upload the report or model to the new server, you need to rebind it to a shared data source that is stored on the new report server.</span></span> <span data-ttu-id="8498a-105">如果不重新繫結報表或模型，從新報表伺服器存取該報表或模型時將無法正常運作。</span><span class="sxs-lookup"><span data-stu-id="8498a-105">If you don't rebind the report or model, it will not work correctly when accessed from the new report server.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8498a-106">將報表或模型重新繫結至共用資料來源時，資料來源必須已存在報表伺服器或 SharePoint 文件庫中。</span><span class="sxs-lookup"><span data-stu-id="8498a-106">Before rebinding a report or model to a shared data source, the data source must already exist on the report server or SharePoint library.</span></span> <span data-ttu-id="8498a-107">如需資料來源的詳細資訊，請參閱[建立、修改和刪除共用資料來源 &#40;SSRS&#41;](create-modify-and-delete-shared-data-sources-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="8498a-107">For more information about data sources, see [Create, Modify, and Delete Shared Data Sources &#40;SSRS&#41;](create-modify-and-delete-shared-data-sources-ssrs.md).</span></span>  
  
### <a name="to-bind-a-report-or-model-to-a-shared-data-source-on-a-report-server-running-in-native-mode"></a><span data-ttu-id="8498a-108">將報表或模型繫結至以原生模式執行之報表伺服器上的共用資料來源</span><span class="sxs-lookup"><span data-stu-id="8498a-108">To bind a report or model to a shared data source on a report server running in native mode</span></span>  
  
1.  <span data-ttu-id="8498a-109">在 **[報表管理員]** 中，按一下要上傳至伺服器的報表或模型名稱。</span><span class="sxs-lookup"><span data-stu-id="8498a-109">In **Report Manager**, click the name of the report or model that you uploaded to the server.</span></span>  
  
     <span data-ttu-id="8498a-110">[屬性] 索引標籤隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="8498a-110">The Properties tab opens.</span></span>  
  
2.  <span data-ttu-id="8498a-111">按一下 **[資料來源]**。</span><span class="sxs-lookup"><span data-stu-id="8498a-111">Click **Data Sources**.</span></span>  
  
3.  <span data-ttu-id="8498a-112">按一下 **[瀏覽]**，然後導覽到報表或模型要繫結的資料來源。</span><span class="sxs-lookup"><span data-stu-id="8498a-112">Click **Browse**, and then navigate to the data source to which you want to bind the report or model.</span></span>  
  
4.  <span data-ttu-id="8498a-113">選取資料來源，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="8498a-113">Select the data source and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="8498a-114">按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="8498a-114">Click **Apply**.</span></span>  
  
     <span data-ttu-id="8498a-115">現在報表或模型已繫結至所選取的資料來源。</span><span class="sxs-lookup"><span data-stu-id="8498a-115">The report or model is now bound to the data source that you selected.</span></span>  
  
### <a name="to-bind-a-report-or-model-to-a-shared-data-source-on-a-report-server-running-in-sharepoint-integrated-mode"></a><span data-ttu-id="8498a-116">將報表或模型繫結至以 SharePoint 整合模式執行之報表伺服器上的共用資料來源</span><span class="sxs-lookup"><span data-stu-id="8498a-116">To bind a report or model to a shared data source on a report server running in SharePoint integrated mode</span></span>  
  
1.  <span data-ttu-id="8498a-117">如果文件庫尚未開啟，請在 [快速啟動] 列上按一下文件庫名稱。</span><span class="sxs-lookup"><span data-stu-id="8498a-117">If the library is not already open, click its name on the Quick Launch bar.</span></span> <span data-ttu-id="8498a-118">如果找不到您的文件庫名稱，請先按一下 **[檢視所有網站內容]**，然後再按一下文件庫名稱。</span><span class="sxs-lookup"><span data-stu-id="8498a-118">If the name of your library does not appear, click **View All Site Content**, and then click the name of your library.</span></span>  
  
2.  <span data-ttu-id="8498a-119">指向報表或模型，然後按一下向下箭頭。</span><span class="sxs-lookup"><span data-stu-id="8498a-119">Point to the report or model and click the down arrow.</span></span>  
  
3.  <span data-ttu-id="8498a-120">按一下 **[管理資料來源]**。</span><span class="sxs-lookup"><span data-stu-id="8498a-120">Click **Manage Data Sources**.</span></span>  
  
4.  <span data-ttu-id="8498a-121">按一下 **[dataSource1]**。</span><span class="sxs-lookup"><span data-stu-id="8498a-121">Click **dataSource1**.</span></span>  
  
5.  <span data-ttu-id="8498a-122">在 **[連接類型]** 區域中，確認已選取 **[共用資料來源]** 。</span><span class="sxs-lookup"><span data-stu-id="8498a-122">In the **Connection Type** area, verify that **Shared data source** is selected.</span></span>  
  
6.  <span data-ttu-id="8498a-123">在 [資料來源連結]\*\*\*\* 區域中，按一下省略符號 (...) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="8498a-123">In the **Data Source Link** area, click the ellipsis (...) button.</span></span>  
  
7.  <span data-ttu-id="8498a-124">找到要使用的資料來源。</span><span class="sxs-lookup"><span data-stu-id="8498a-124">Locate the data source you want to use.</span></span>  
  
8.  <span data-ttu-id="8498a-125">選取資料來源，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="8498a-125">Select the data source and **click OK**.</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
10. <span data-ttu-id="8498a-126">按一下 [關閉] 。</span><span class="sxs-lookup"><span data-stu-id="8498a-126">Click **Close**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8498a-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8498a-127">See Also</span></span>  
 <span data-ttu-id="8498a-128">[上傳檔案或報表 &#40;報表管理員&#41;](../reports/upload-a-file-or-report-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="8498a-128">[Upload a File or Report &#40;Report Manager&#41;](../reports/upload-a-file-or-report-report-manager.md) </span></span>  
 <span data-ttu-id="8498a-129">[將檔上傳至 sharepoint 文件庫 &#40;sharepoint 模式中的 Reporting Services&#41;](../upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode.md) </span><span class="sxs-lookup"><span data-stu-id="8498a-129">[Upload Documents to a SharePoint Library &#40;Reporting Services in SharePoint Mode&#41;](../upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode.md) </span></span>  
 <span data-ttu-id="8498a-130">[以 SharePoint 整合模式 &#40;Reporting Services 建立和管理共用資料來源&#41;](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md) </span><span class="sxs-lookup"><span data-stu-id="8498a-130">[Create and Manage Shared Data Sources &#40;Reporting Services in SharePoint Integrated Mode&#41;](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md) </span></span>  
 <span data-ttu-id="8498a-131">[建立、刪除或修改共用資料來源 &#40;報表管理員&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="8498a-131">[Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) </span></span>  
 <span data-ttu-id="8498a-132">[Reporting Services 中的資料連線、資料來源及連接字串](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="8498a-132">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="8498a-133">Reporting Services 支援的資料來源 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="8498a-133">Data Sources Supported by Reporting Services &#40;SSRS&#41;</span></span>](../create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
  
