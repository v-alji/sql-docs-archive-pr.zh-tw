---
title: 此活頁簿包含可重新整理外部資料的一個或多個查詢。 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: aa65c992-eb41-4032-9e11-a9ba871b6a3c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 25b2095e13d6151c68eb4a3507400dfdb1739564
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595312"
---
# <a name="this-workbook-contains-one-or-more-queries-that-refresh-external-data"></a><span data-ttu-id="41af2-103">此活頁簿包含可重新整理外部資料的一個或多個查詢。</span><span class="sxs-lookup"><span data-stu-id="41af2-103">This workbook contains one or more queries that refresh external data.</span></span>
  <span data-ttu-id="41af2-104">對於包含 PowerPivot 資料的 Excel 活頁簿，Excel Services 會在偵測到連接資訊時顯示這個警告，然後提示您啟用或停用此活頁簿的查詢。</span><span class="sxs-lookup"><span data-stu-id="41af2-104">For Excel workbooks that contain PowerPivot data, Excel Services shows this warning when it detects connection information and prompts you to enable or disable queries for this workbook.</span></span>  
  
## <a name="details"></a><span data-ttu-id="41af2-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="41af2-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="41af2-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="41af2-106">Product Name</span></span>|<span data-ttu-id="41af2-107">PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="41af2-107">PowerPivot for SharePoint</span></span>|  
|<span data-ttu-id="41af2-108">產品版本</span><span class="sxs-lookup"><span data-stu-id="41af2-108">Product Version</span></span>|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="41af2-109">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41af2-109">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|<span data-ttu-id="41af2-110">原因</span><span class="sxs-lookup"><span data-stu-id="41af2-110">Cause</span></span>|<span data-ttu-id="41af2-111">Excel Services 設定為資料重新整理時警告。</span><span class="sxs-lookup"><span data-stu-id="41af2-111">Excel Services is configured to warn on data refresh.</span></span>|  
|<span data-ttu-id="41af2-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="41af2-112">Message Text</span></span>|<span data-ttu-id="41af2-113">此活頁簿包含可重新整理外部資料的一個或多個查詢。</span><span class="sxs-lookup"><span data-stu-id="41af2-113">This workbook contains one or more queries that refresh external data.</span></span> <span data-ttu-id="41af2-114">惡意使用者可以設計一個查詢來存取機密資訊，並將其散發給其他使用者或執行其他有害的動作。</span><span class="sxs-lookup"><span data-stu-id="41af2-114">A malicious user can design a query to access confidential information and distribute it to other users or perform other harmful actions.</span></span><br /><br /> <span data-ttu-id="41af2-115">如果您信任此活頁簿的來源，按一下 [是]，啟用此活頁簿中對外部資料的查詢。</span><span class="sxs-lookup"><span data-stu-id="41af2-115">If you trust the source of this workbook, click Yes to enable queries to external data in this workbook.</span></span> <span data-ttu-id="41af2-116">如果您不確定，按一下 [否]，變更就不會套用到您的活頁簿中。</span><span class="sxs-lookup"><span data-stu-id="41af2-116">If you are not sure, click No so that changes are not applied to your workbook.</span></span><br /><br /> <span data-ttu-id="41af2-117">您要啟用此活頁簿中對外部資料的查詢嗎？</span><span class="sxs-lookup"><span data-stu-id="41af2-117">Do you want to enable queries to external data in this workbook?</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="41af2-118">說明</span><span class="sxs-lookup"><span data-stu-id="41af2-118">Explanation</span></span>  
 <span data-ttu-id="41af2-119">PowerPivot 活頁簿包含內嵌的資料連接字串，Excel 會使用這些連接字串與載入和計算資料的外部 PowerPivot 伺服器進行通訊。</span><span class="sxs-lookup"><span data-stu-id="41af2-119">PowerPivot workbooks contain embedded data connection strings that are used by Excel to communicate with an external PowerPivot server that loads and calculates the data.</span></span> <span data-ttu-id="41af2-120">如果啟用資料重新整理時警告，Excel Services 會偵測此連接字串，並據此警告使用者。</span><span class="sxs-lookup"><span data-stu-id="41af2-120">When warn on data refresh is enabled, Excel Services detects this connection string and warns the user accordingly.</span></span>  
  
 <span data-ttu-id="41af2-121">若要篩選與配量活頁簿中的 PowerPivot 資料，必須啟用查詢。</span><span class="sxs-lookup"><span data-stu-id="41af2-121">To filter and slice PowerPivot data in the workbook, queries must be enabled.</span></span> <span data-ttu-id="41af2-122">請務必僅針對您信任的 PowerPivot 活頁簿啟用查詢。</span><span class="sxs-lookup"><span data-stu-id="41af2-122">Be sure that you enable queries for only those PowerPivot workbooks that you trust.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="41af2-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="41af2-123">User Action</span></span>  
 <span data-ttu-id="41af2-124">按一下 [是]\*\*\*\* 以啟用查詢。</span><span class="sxs-lookup"><span data-stu-id="41af2-124">Click **Yes** to enable queries.</span></span>  
  
 <span data-ttu-id="41af2-125">您也可以變更組態設定，不再於重新整理時警告。</span><span class="sxs-lookup"><span data-stu-id="41af2-125">You can also change the configuration settings so that warn on refresh no longer occurs:</span></span>  
  
1.  <span data-ttu-id="41af2-126">在 [管理中心] 的 [應用程式管理] 中，按一下 **[管理服務應用程式]** 。</span><span class="sxs-lookup"><span data-stu-id="41af2-126">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="41af2-127">按一下 [Excel Services 應用程式]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="41af2-127">Click **Excel Services Application**.</span></span>  
  
3.  <span data-ttu-id="41af2-128">按一下 [信任的檔案位置]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="41af2-128">Click **Trusted File Location**.</span></span>  
  
4.  <span data-ttu-id="41af2-129">按一下 [http://]\*\*\*\* 或是您想要設定的位置。</span><span class="sxs-lookup"><span data-stu-id="41af2-129">Click **http://** or the location you want to configure.</span></span>  
  
5.  <span data-ttu-id="41af2-130">在 [外部資料] 中，清除 [Warn on data refresh (資料重新整理時警告)]\*\*\*\* 的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="41af2-130">In External Data, clear the checkbox for **Warn on data refresh**.</span></span>  
  
6.  <span data-ttu-id="41af2-131">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="41af2-131">Click **OK**.</span></span>  
  
 <span data-ttu-id="41af2-132">或者，您可以針對包含 PowerPivot 活頁簿的網站建立新的信任位置，然後只針對該網站修改組態設定。</span><span class="sxs-lookup"><span data-stu-id="41af2-132">Alternatively, you can create a new trusted location for sites that contain PowerPivot workbooks, and then modify the configuration settings for just that site.</span></span> <span data-ttu-id="41af2-133">如需相關資訊，請參閱 [Create a trusted location for PowerPivot sites in Central Administration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md)。</span><span class="sxs-lookup"><span data-stu-id="41af2-133">For more information, see [Create a trusted location for PowerPivot sites in Central Administration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).</span></span>  
  
  
