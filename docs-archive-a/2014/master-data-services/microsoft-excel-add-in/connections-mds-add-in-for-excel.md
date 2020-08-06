---
title: 連接 (適用於 Excel 的 MDS 增益集) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 2f2b2f9d-7744-460e-83cd-56d34ea70ff0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d4dc41afc6dd59cade9e75475c7cb914d14a8937
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584620"
---
# <a name="connections-mds-add-in-for-excel"></a><span data-ttu-id="0b9cd-102">連接 (適用於 Excel 的 MDS 增益集)</span><span class="sxs-lookup"><span data-stu-id="0b9cd-102">Connections (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="0b9cd-103">若要將資料下載至 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，您必須先建立連接。</span><span class="sxs-lookup"><span data-stu-id="0b9cd-103">To download data in to the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], you must first create a connection.</span></span> <span data-ttu-id="0b9cd-104">連接可讓 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web 服務知道要連接的目標 MDS 資料庫。</span><span class="sxs-lookup"><span data-stu-id="0b9cd-104">A connection is how the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] web service knows which MDS database to connect to.</span></span>  
  
 <span data-ttu-id="0b9cd-105">連接字串通常是 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web 應用程式的 URL，例如 http://contoso/mds。</span><span class="sxs-lookup"><span data-stu-id="0b9cd-105">The connection string is usually the URL of the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application, for example http://contoso/mds.</span></span>  
  
 <span data-ttu-id="0b9cd-106">每次您啟動 Excel 時，都必須連接到 MDS 儲存機制。</span><span class="sxs-lookup"><span data-stu-id="0b9cd-106">Each time you start Excel, you must connect to an MDS repository.</span></span> <span data-ttu-id="0b9cd-107">唯一的例外狀況是使用中試算表已經包含 MDS 管理的資料。</span><span class="sxs-lookup"><span data-stu-id="0b9cd-107">The only exception is when the active spreadsheet already contains MDS-managed data.</span></span> <span data-ttu-id="0b9cd-108">在此情況中，每次您重新整理或發行工作表中的資料時，系統就會自動建立連接。</span><span class="sxs-lookup"><span data-stu-id="0b9cd-108">In this case, a connection is automatically made each time you refresh or publish data in the sheet.</span></span>  
  
 <span data-ttu-id="0b9cd-109">您可以建立多個連線。</span><span class="sxs-lookup"><span data-stu-id="0b9cd-109">You can create multiple connections.</span></span> <span data-ttu-id="0b9cd-110">最近存取的連接會被視為預設值。</span><span class="sxs-lookup"><span data-stu-id="0b9cd-110">The most recently-accessed connection is considered the default.</span></span>  
  
 <span data-ttu-id="0b9cd-111">多位使用者可以同時進行連接。</span><span class="sxs-lookup"><span data-stu-id="0b9cd-111">Multiple users can be connected at the same time.</span></span> <span data-ttu-id="0b9cd-112">不過，當多位使用者嘗試發行相同的資料時，可能會引發衝突。</span><span class="sxs-lookup"><span data-stu-id="0b9cd-112">However, conflicts can arise when multiple users attempt to publish the same data.</span></span> <span data-ttu-id="0b9cd-113">如需詳細資訊，請參閱[發行 Data &#40;適用于 Excel 的 MDS 增益集&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="0b9cd-113">For more information, see [Publishing Data &#40;MDS Add-in for Excel&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md).</span></span>  
  
## <a name="connect-automatically-and-load-frequently-used-data"></a><span data-ttu-id="0b9cd-114">自動連接並載入經常使用的資料</span><span class="sxs-lookup"><span data-stu-id="0b9cd-114">Connect Automatically and Load Frequently-Used Data</span></span>  
 <span data-ttu-id="0b9cd-115">如果您想要永遠連接到相同的伺服器並且載入相同的資料集，可以建立包含連接和篩選資訊的捷徑查詢檔案。</span><span class="sxs-lookup"><span data-stu-id="0b9cd-115">If you want to always connect to the same server and load the same set of data, you can create shortcut query files, which contain connection and filter information.</span></span> <span data-ttu-id="0b9cd-116">如需查詢檔案的詳細資訊，請參閱 [捷徑查詢檔案 &#40;適用於 Excel 的 MDS 增益集&#41;](shortcut-query-files-mds-add-in-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="0b9cd-116">For more information about query files, see [Shortcut Query Files &#40;MDS Add-in for Excel&#41;](shortcut-query-files-mds-add-in-for-excel.md).</span></span>  
  
## <a name="data-quality-services"></a><span data-ttu-id="0b9cd-117">Data Quality Services</span><span class="sxs-lookup"><span data-stu-id="0b9cd-117">Data Quality Services</span></span>  
 <span data-ttu-id="0b9cd-118">[!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] 具有 Data Quality Services 功能，可協助您在發行資料至 MDS 儲存機制之前比對資料。</span><span class="sxs-lookup"><span data-stu-id="0b9cd-118">The [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] has Data Quality Services functionality to help you match data before publishing it to the MDS repository.</span></span> <span data-ttu-id="0b9cd-119">當您建立連接時，如果 DQS 資料庫與 MDS 資料庫安裝在相同的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上，您就能夠在功能區上檢視 DQS 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0b9cd-119">When you make a connection, if a DQS database is installed on the same instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as the MDS database, you will be able to view DQS buttons on the ribbon.</span></span> <span data-ttu-id="0b9cd-120">如果 DQS_Main 資料庫不存在執行個體上，系統就不會顯示這些按鈕，而且資料品質功能將無法使用。</span><span class="sxs-lookup"><span data-stu-id="0b9cd-120">If the DQS_Main database does not exist on the instance, these buttons are not displayed and data quality functionality is not available.</span></span>  
  
## <a name="troubleshooting-connections"></a><span data-ttu-id="0b9cd-121">疑難排解連接</span><span class="sxs-lookup"><span data-stu-id="0b9cd-121">Troubleshooting Connections</span></span>  
 <span data-ttu-id="0b9cd-122">當您連接到 MDS 時，如果您遇到任何問題，請參閱 [https://social.technet.microsoft.com/wiki/contents/articles/4520.aspx](https://social.technet.microsoft.com/wiki/contents/articles/4520.aspx) 以取得疑難排解秘訣。</span><span class="sxs-lookup"><span data-stu-id="0b9cd-122">When you connect to MDS, if you encounter any issues see [https://social.technet.microsoft.com/wiki/contents/articles/4520.aspx](https://social.technet.microsoft.com/wiki/contents/articles/4520.aspx) for troubleshooting tips.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="0b9cd-123">相關工作</span><span class="sxs-lookup"><span data-stu-id="0b9cd-123">Related Tasks</span></span>  
  
|<span data-ttu-id="0b9cd-124">工作描述</span><span class="sxs-lookup"><span data-stu-id="0b9cd-124">Task Description</span></span>|<span data-ttu-id="0b9cd-125">主題</span><span class="sxs-lookup"><span data-stu-id="0b9cd-125">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="0b9cd-126">建立 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="0b9cd-126">Create a connection to a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span>|[<span data-ttu-id="0b9cd-127">連接到 MDS 儲存機制 &#40;適用於 Excel 的 MDS 增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="0b9cd-127">Connect to an MDS Repository &#40;MDS Add-in for Excel&#41;</span></span>](connect-to-an-mds-repository-mds-add-in-for-excel.md)|  
|<span data-ttu-id="0b9cd-128">將 MDS 資料載入 Excel 中。</span><span class="sxs-lookup"><span data-stu-id="0b9cd-128">Load MDS data into Excel.</span></span>|[<span data-ttu-id="0b9cd-129">將資料從 MDS 載入 Excel 中</span><span class="sxs-lookup"><span data-stu-id="0b9cd-129">Load Data from MDS into Excel</span></span>](export-data-to-excel-from-master-data-services.md)|  
|<span data-ttu-id="0b9cd-130">在將 MDS 資料載入 Excel 之前篩選資料。</span><span class="sxs-lookup"><span data-stu-id="0b9cd-130">Filter MDS data before you load it into Excel.</span></span>|[<span data-ttu-id="0b9cd-131">載入 &#40;適用于 Excel 的 MDS 增益集之前先篩選資料&#41;</span><span class="sxs-lookup"><span data-stu-id="0b9cd-131">Filter Data before Loading &#40;MDS Add-in for Excel&#41;</span></span>](filter-data-before-exporting-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a><span data-ttu-id="0b9cd-132">相關內容</span><span class="sxs-lookup"><span data-stu-id="0b9cd-132">Related Content</span></span>  
  
-   [<span data-ttu-id="0b9cd-133">載入適用于 Excel 的 MDS 增益集&#41;的資料 &#40;</span><span class="sxs-lookup"><span data-stu-id="0b9cd-133">Loading Data &#40;MDS Add-in for Excel&#41;</span></span>](overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="0b9cd-134">捷徑查詢檔案 &#40;適用於 Excel 的 MDS 增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="0b9cd-134">Shortcut Query Files &#40;MDS Add-in for Excel&#41;</span></span>](shortcut-query-files-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="0b9cd-135">適用於 Microsoft Excel 的 Master Data Services 增益集</span><span class="sxs-lookup"><span data-stu-id="0b9cd-135">Master Data Services Add-in for Microsoft Excel</span></span>](master-data-services-add-in-for-microsoft-excel.md)  
  
  
