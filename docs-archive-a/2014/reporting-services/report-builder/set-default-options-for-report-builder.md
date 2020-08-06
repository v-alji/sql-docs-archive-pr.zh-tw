---
title: 報表產生器選項] 對話方塊中，報表產生器) 的設定 (|Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10427"
ms.assetid: 423360de-9bed-462e-921f-60a5abab004f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 07bd4a7f9dfe1abd8ab76765cb1ac10ff5227066
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593320"
---
# <a name="report-builder-options-dialog-box-settings-report-builder"></a><span data-ttu-id="53dd1-102">報表產生器選項對話方塊、設定 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="53dd1-102">Report Builder Options Dialog Box, Settings (Report Builder)</span></span>
  <span data-ttu-id="53dd1-103">按一下 [**報表產生器**] 按鈕，然後按一下 [**選項**]，設定顯示最近使用的檔案和連線的選項。</span><span class="sxs-lookup"><span data-stu-id="53dd1-103">Click the **Report Builder** button and then click **Options** to set options for showing recent files and connections.</span></span> <span data-ttu-id="53dd1-104">您也可以變更預設報表伺服器，或加入報表伺服器 (如果沒有預設值的話)。</span><span class="sxs-lookup"><span data-stu-id="53dd1-104">You can also change the default report server, or add one if you don't have a default.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="53dd1-105">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="53dd1-105">UI element list</span></span>  
 <span data-ttu-id="53dd1-106">**預設使用此報表伺服器或 SharePoint 網站**</span><span class="sxs-lookup"><span data-stu-id="53dd1-106">**Use this report server or SharePoint site by default**</span></span>  
 <span data-ttu-id="53dd1-107">您的管理員可能已經設定這個選項。</span><span class="sxs-lookup"><span data-stu-id="53dd1-107">Your administrator may have configured this.</span></span> <span data-ttu-id="53dd1-108">此值可以是以 http:// 或 https:// 為開頭的正確格式 URL。</span><span class="sxs-lookup"><span data-stu-id="53dd1-108">The value can be a well-formed URL starting with http:// or https://.</span></span> <span data-ttu-id="53dd1-109">這項設定會決定預設顯示在資料表/矩陣和圖表精靈中的資料來源連接。</span><span class="sxs-lookup"><span data-stu-id="53dd1-109">This setting determines which data source connections appear by default in the Table/Matrix and Chart wizards.</span></span> <span data-ttu-id="53dd1-110">此外，您的報表將在這個伺服器上處理，而且您可以參考來自這個伺服器的資源。</span><span class="sxs-lookup"><span data-stu-id="53dd1-110">In addition, your reports will be processed on this server and you can reference resources from this server.</span></span>  
  
 <span data-ttu-id="53dd1-111">如果您選取不同的報表伺服器，可能必須重新啟動報表產生器，才能讓這項變更生效。</span><span class="sxs-lookup"><span data-stu-id="53dd1-111">If you select a different report server, you may need to restart Report Builder in order for this change to take affect.</span></span>  
  
 <span data-ttu-id="53dd1-112">**預設發行報表組件到這個資料夾**</span><span class="sxs-lookup"><span data-stu-id="53dd1-112">**Publish report parts to this folder by default**</span></span>  
 <span data-ttu-id="53dd1-113">報表產生器會儲存您發行到這個資料夾的報表組件。</span><span class="sxs-lookup"><span data-stu-id="53dd1-113">Report Builder will save report parts that you publish to this folder.</span></span> <span data-ttu-id="53dd1-114">如果此資料夾尚未存在，而且您有權在報表伺服器上建立資料夾，報表產生器將會建立這個資料夾。</span><span class="sxs-lookup"><span data-stu-id="53dd1-114">If the folder does not exist yet and you have permissions to create folders on the report server, Report Builder will create this folder.</span></span>  
  
 <span data-ttu-id="53dd1-115">您不需要重新啟動報表產生器，這項設定也會生效。</span><span class="sxs-lookup"><span data-stu-id="53dd1-115">You do not need to restart Report Builder for this setting to take effect.</span></span>  
  
 <span data-ttu-id="53dd1-116">**顯示下列數量之最近使用的網站和伺服器**</span><span class="sxs-lookup"><span data-stu-id="53dd1-116">**Show this number of recent sites and servers**</span></span>  
 <span data-ttu-id="53dd1-117">指定要顯示在 [開啟報表]  和 [另存為報表]  對話方塊中的最近使用之網站和連接的數目。</span><span class="sxs-lookup"><span data-stu-id="53dd1-117">Specify the number of recent sites and connections to show in the **Open Report** and **Save As Report** dialog boxes.</span></span>  
  
 <span data-ttu-id="53dd1-118">**顯示下列數量之最近使用的共用資料集和資料來源連接**</span><span class="sxs-lookup"><span data-stu-id="53dd1-118">**Show this number of recent shared datasets and data source connections**</span></span>  
 <span data-ttu-id="53dd1-119">指定要顯示在 [資料集屬性]  對話方塊和資料區域精靈之 [選擇與資料來源的連接]  頁面中的最近使用之共用資料集和資料來源連接的數目。</span><span class="sxs-lookup"><span data-stu-id="53dd1-119">Specify the number of recent shared datasets and data source connections to show in the **Dataset Properties** dialog box and the **Choose a connection to a data source** page of the Data Regions Wizard.</span></span>  
  
 <span data-ttu-id="53dd1-120">**顯示下列數量之最近使用的文件**</span><span class="sxs-lookup"><span data-stu-id="53dd1-120">**Show this number of recent documents**</span></span>  
 <span data-ttu-id="53dd1-121">指定要在您按一下 [報表產生器] 按鈕時顯示的最近使用之文件的數目。</span><span class="sxs-lookup"><span data-stu-id="53dd1-121">Specify the number of recent documents to show when you click the Report Builder button.</span></span>  
  
 <span data-ttu-id="53dd1-122">**清除所有最近使用的項目清單**</span><span class="sxs-lookup"><span data-stu-id="53dd1-122">**Clear all recent item lists**</span></span>  
 <span data-ttu-id="53dd1-123">清除最近使用之網站和伺服器、共用資料集和共用資料來源連接以及文件的目前清單。</span><span class="sxs-lookup"><span data-stu-id="53dd1-123">Clear the current lists of recent sites and servers, shared datasets, shared data source connections, and documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53dd1-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53dd1-124">See Also</span></span>  
 [<span data-ttu-id="53dd1-125">對話方塊、窗格和精靈的報表產生器說明</span><span class="sxs-lookup"><span data-stu-id="53dd1-125">Report Builder Help for Dialog Boxes, Panes, and Wizards</span></span>](../report-builder-help-for-dialog-boxes-panes-and-wizards.md)  
  
  
