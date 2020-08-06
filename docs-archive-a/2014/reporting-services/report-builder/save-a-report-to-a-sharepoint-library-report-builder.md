---
title: 將報表儲存至 SharePoint 文件庫 (報表產生器) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4daa1eee-78b7-43d0-8b22-4a98e8fa66ba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 49878a0d7115a11e804382cb5139aa0ec7b3d254
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595777"
---
# <a name="save-a-report-to-a-sharepoint-library-report-builder"></a><span data-ttu-id="35827-102">將報表儲存至 SharePoint 文件庫 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="35827-102">Save a Report to a SharePoint Library (Report Builder)</span></span>
  <span data-ttu-id="35827-103">若要將報表儲存至針對 SharePoint 整合所設定的報表伺服器，您必須瀏覽至 SharePoint 伺服器，然後建立報表伺服器的連接。</span><span class="sxs-lookup"><span data-stu-id="35827-103">To save a report to a report server configured for SharePoint integration, you must browse to the SharePoint server and establish a connection to the report server.</span></span> <span data-ttu-id="35827-104">在報表定義中，與報表相關之項目的所有參考都必須使用 SharePoint 報表伺服器特有的值。</span><span class="sxs-lookup"><span data-stu-id="35827-104">In the report definition, all references to items related to the report must use values that are specific to a SharePoint report server.</span></span> <span data-ttu-id="35827-105">相關的項目包括子報表、鑽研報表和資源，例如以 Web 為基礎的影像。</span><span class="sxs-lookup"><span data-stu-id="35827-105">Related items include subreports, drillthrough reports, and resources such as Web-based images.</span></span> <span data-ttu-id="35827-106">如需詳細資訊，請參閱[指定外部項目的路徑 &#40;報表產生器及 SSRS&#41;](../report-design/specifying-paths-to-external-items-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="35827-106">For more information, see [Specifying Paths to External Items &#40;Report Builder and SSRS&#41;](../report-design/specifying-paths-to-external-items-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="35827-107">您在 SharePoint 網站上必須具有「 **成員** 」或「 **擁有者** 」權限才能設定專案的屬性。</span><span class="sxs-lookup"><span data-stu-id="35827-107">You must have **Member** or **Owner** permission on the SharePoint site to set the properties on the project.</span></span>  
  
### <a name="to-save-a-report-to-a-sharepoint-site"></a><span data-ttu-id="35827-108">若要將報表儲存至 SharePoint 網站</span><span class="sxs-lookup"><span data-stu-id="35827-108">To save a report to a SharePoint site</span></span>  
  
1.  <span data-ttu-id="35827-109">在報表產生器的按鈕中，按一下 **[儲存]**。</span><span class="sxs-lookup"><span data-stu-id="35827-109">From the Report Builder button, click **Save**.</span></span> <span data-ttu-id="35827-110">[**另存**新檔 _\<Report Item>_ ] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="35827-110">The **Save As**_\<Report Item>_ dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="35827-111">如果您重新儲存報表，報表會自動重新儲存到之前的位置。</span><span class="sxs-lookup"><span data-stu-id="35827-111">If you are resaving a report, it is automatically resaved to its previous location.</span></span> <span data-ttu-id="35827-112">使用 [另存新檔]\*\*\*\* 選項可變更位置。</span><span class="sxs-lookup"><span data-stu-id="35827-112">Use the **Save As** option to change location.</span></span>  
  
2.  <span data-ttu-id="35827-113">您也可以選擇按一下 **[最近使用的網站和伺服器]** 來顯示最近使用過的報表伺服器和 SharePoint 網站清單。</span><span class="sxs-lookup"><span data-stu-id="35827-113">Optionally, click **Recent Sites and Servers** to show a list of recently used report servers and SharePoint sites.</span></span>  
  
3.  <span data-ttu-id="35827-114">瀏覽至 SharePoint 網站，然後按一下 [儲存]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35827-114">Browse to the SharePoint site, and then click **Save**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="35827-115">如果您保留已變更的報表超過 10 小時而未加以儲存，此報表就會與伺服器中斷連接，但不會儲存。</span><span class="sxs-lookup"><span data-stu-id="35827-115">If you leave a changed report for more than 10 hours without saving it, it is disconnected from the server without being saved.</span></span> <span data-ttu-id="35827-116">如果發生這種情況，請按一下右下狀態列中的 [中斷連線]\*\*\*\*，然後按一下 [連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="35827-116">If that happens, in the lower-right status bar, click **Disconnect**, and then click **Connect**.</span></span> <span data-ttu-id="35827-117">最新的伺服器將位於可用的伺服器清單中。</span><span class="sxs-lookup"><span data-stu-id="35827-117">The most recent server will be in the list of available servers.</span></span> <span data-ttu-id="35827-118">選取該伺服器，然後報表將會重新連接。</span><span class="sxs-lookup"><span data-stu-id="35827-118">Select it and the report will reconnect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35827-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35827-119">See Also</span></span>  
 [<span data-ttu-id="35827-120">尋找、檢視和管理報表 &#40;報表產生器及 SSRS &#41;</span><span class="sxs-lookup"><span data-stu-id="35827-120">Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;</span></span>](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
