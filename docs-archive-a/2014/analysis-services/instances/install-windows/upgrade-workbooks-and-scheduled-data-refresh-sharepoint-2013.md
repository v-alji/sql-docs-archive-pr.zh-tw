---
title: 升級活頁簿和排程的資料重新整理 (SharePoint 2013) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: a49c4af4-e243-4926-be97-74da1f9d54eb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 185fe0864bc4c1cdda9a63fa97a17319d65dc87d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688317"
---
# <a name="upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013"></a><span data-ttu-id="a87ea-102">升級活頁簿和排程的資料重新整理 (SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="a87ea-102">Upgrade Workbooks and Scheduled Data Refresh (SharePoint 2013)</span></span>
  <span data-ttu-id="a87ea-103">本主題將說明在先前 PowerPivot 環境中建立之活頁簿的使用者體驗，以及如何升級 PowerPivot 活頁簿，以便讓您運用這個版本所導入的新功能。</span><span class="sxs-lookup"><span data-stu-id="a87ea-103">This topic explains the user experience of workbooks created in previous PowerPivot environments and how to upgrade PowerPivot workbooks so that you can take advantage of new features introduced in this release.</span></span> <span data-ttu-id="a87ea-104">若要深入瞭解新功能，請參閱[PowerPivot 的新](https://go.microsoft.com/fwlink/?LinkID=203917)功能。</span><span class="sxs-lookup"><span data-stu-id="a87ea-104">To learn more about new features, see [What's New in PowerPivot](https://go.microsoft.com/fwlink/?LinkID=203917).</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="a87ea-105">您不能針對在伺服器上自動升級的活頁簿回復升級。</span><span class="sxs-lookup"><span data-stu-id="a87ea-105">You cannot rollback upgrade for workbooks that are upgraded automatically on the server.</span></span> <span data-ttu-id="a87ea-106">一旦升級活頁簿之後，它就會保持升級的狀態。</span><span class="sxs-lookup"><span data-stu-id="a87ea-106">Once a workbook is upgraded, it remains upgraded.</span></span> <span data-ttu-id="a87ea-107">若要使用之前的版本，可以將之前的活頁簿重新發行至 SharePoint、還原之前的版本或回收活頁簿。</span><span class="sxs-lookup"><span data-stu-id="a87ea-107">To use a previous version, you can republish the previous workbook to SharePoint, restore a previous version, or recycle the workbook.</span></span> <span data-ttu-id="a87ea-108">如需有關在 SharePoint 中還原或回收文件的詳細資訊，請參閱＜ [規劃如何使用資源回收筒及版本設定功能保護內容](https://go.microsoft.com/fwlink/?LinkId=238669)＞。</span><span class="sxs-lookup"><span data-stu-id="a87ea-108">For more information about restoring or recycling a document in SharePoint, see [Plan to protect content by using recycle bins and versioning](https://go.microsoft.com/fwlink/?LinkId=238669).</span></span>  
  
 <span data-ttu-id="a87ea-109">本主題包含下列幾節：</span><span class="sxs-lookup"><span data-stu-id="a87ea-109">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="a87ea-110">升級活頁簿的概觀</span><span class="sxs-lookup"><span data-stu-id="a87ea-110">Overview of Upgrading Workbooks</span></span>](#bkmk_overview)  
  
-   [<span data-ttu-id="a87ea-111">從 2008 R2 活頁簿升級為 SQL Server 2012 Service Pack 1 (SP1) 活頁簿</span><span class="sxs-lookup"><span data-stu-id="a87ea-111">Upgrade to SQL Server 2012 Service Pack 1 (SP1) workbooks from 2008 R2 Workbooks</span></span>](#bkmk_to_2012sp1_from_2008r2)  
  
-   [<span data-ttu-id="a87ea-112">從使用 2012 PowerPivot for Excel 增益集所建立的版本升級為 Office 2013 活頁簿</span><span class="sxs-lookup"><span data-stu-id="a87ea-112">Upgrade to Office 2013 workbooks from Versions created by using the 2012 PowerPivot Add-In for Excel</span></span>](#bkmk_to_2012sp1_from_2012)  
  
-   [<span data-ttu-id="a87ea-113">從使用 2008 R2 PowerPivot for Excel 2010 增益集所建立的版本升級為 SQL Server 2012 活頁簿</span><span class="sxs-lookup"><span data-stu-id="a87ea-113">Upgrade to SQL Server 2012 workbooks from Versions created by using the 2008 R2 PowerPivot Add-In for Excel 2010</span></span>](#bkmk_to_2012_from_2008R2)  
  
-   [<span data-ttu-id="a87ea-114">在較新的伺服器上執行多個活頁簿版本</span><span class="sxs-lookup"><span data-stu-id="a87ea-114">Running Multiple Workbook Versions on a Newer Server</span></span>](#bkmk_runold)  
  
##  <a name="overview-of-upgrading-workbooks"></a><a name="bkmk_overview"></a><span data-ttu-id="a87ea-115">升級活頁簿的總覽</span><span class="sxs-lookup"><span data-stu-id="a87ea-115">Overview of Upgrading Workbooks</span></span>  
 <span data-ttu-id="a87ea-116">PowerPivot 活頁簿是指包含內嵌 PowerPivot 資料的 Excel 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="a87ea-116">A PowerPivot workbook is an Excel workbook that contains embedded PowerPivot data.</span></span> <span data-ttu-id="a87ea-117">升級活頁簿有兩個好處：</span><span class="sxs-lookup"><span data-stu-id="a87ea-117">Upgrading a workbook has two benefits:</span></span>  
  
-   <span data-ttu-id="a87ea-118">使用 [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)]中的新功能。</span><span class="sxs-lookup"><span data-stu-id="a87ea-118">Use new features in [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)].</span></span>  
  
-   <span data-ttu-id="a87ea-119">針對搭配 SharePoint 模式之 [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] Analysis Services 伺服器執行的活頁簿啟用排程的資料重新整理。</span><span class="sxs-lookup"><span data-stu-id="a87ea-119">Enables scheduled data refresh for workbooks that run with a [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] Analysis Services server in SharePoint mode.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a87ea-120">您無法回復已升級的活頁簿，所以如果希望在舊版 [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)]或舊版 [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)]中使用該活頁簿，請務必製作檔案的複本。</span><span class="sxs-lookup"><span data-stu-id="a87ea-120">You cannot rollback an upgraded workbook, so be sure to make a copy of the file if you want to use it in the previous version of [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)], or on a previous version of [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)].</span></span>  
  
 <span data-ttu-id="a87ea-121">下表將根據建立活頁簿的環境列出 PowerPivot 活頁簿的支援和行為。</span><span class="sxs-lookup"><span data-stu-id="a87ea-121">The following table lists the support and behavior of PowerPivot workbooks based on the environment  in which the workbook was created.</span></span> <span data-ttu-id="a87ea-122">描述的行為包括一般使用者體驗、將活頁簿升級為特定環境的支援升級選項，以及尚未升級之活頁簿的排程資料重新整理行為。</span><span class="sxs-lookup"><span data-stu-id="a87ea-122">The behavior described includes the general user experience, the supported upgrade options to upgrade the workbook to the particular environment, and the behavior of scheduled data refresh of a workbook that has not yet been upgraded.</span></span>  
  
### <a name="workbook-behavior-and-upgrade-options"></a><span data-ttu-id="a87ea-123">活頁簿行為和升級選項</span><span class="sxs-lookup"><span data-stu-id="a87ea-123">Workbook Behavior and Upgrade Options</span></span>  
  
|<span data-ttu-id="a87ea-124">建立於</span><span class="sxs-lookup"><span data-stu-id="a87ea-124">Created In</span></span>|\<|<span data-ttu-id="a87ea-125">支援和行為</span><span class="sxs-lookup"><span data-stu-id="a87ea-125">Support and Behavior</span></span>|>|  
|----------------|--------|--------------------------|--------|  
||<span data-ttu-id="a87ea-126">**2008 R2 PowerPivot for SharePoint 2010**</span><span class="sxs-lookup"><span data-stu-id="a87ea-126">**2008 R2 PowerPivot for SharePoint 2010**</span></span>|<span data-ttu-id="a87ea-127">**2012 PowerPivot for SharePoint 2010**</span><span class="sxs-lookup"><span data-stu-id="a87ea-127">**2012 PowerPivot for SharePoint 2010**</span></span>|<span data-ttu-id="a87ea-128">**2012 SP1 PowerPivot for SharePoint 2013**</span><span class="sxs-lookup"><span data-stu-id="a87ea-128">**2012 SP1 PowerPivot for SharePoint 2013**</span></span>|  
|<span data-ttu-id="a87ea-129">**2008 R2 PowerPivot for Excel 2010**</span><span class="sxs-lookup"><span data-stu-id="a87ea-129">**2008 R2 PowerPivot for Excel 2010**</span></span>|<span data-ttu-id="a87ea-130">所有功能</span><span class="sxs-lookup"><span data-stu-id="a87ea-130">All Features</span></span>|<span data-ttu-id="a87ea-131">**體驗** ：使用者可以透過瀏覽器與活頁簿進行互動，而且可以使用它做為其他方案的資料來源。</span><span class="sxs-lookup"><span data-stu-id="a87ea-131">**Experience:** Users can interact with the workbook in the browser and use it as a data source for other solutions.</span></span><br /><br /> <span data-ttu-id="a87ea-132">**升級** ：如果 SharePoint 伺服器陣列中的 PowerPivot 系統服務已啟用自動升級，活頁簿就會在文件庫中自動升級。</span><span class="sxs-lookup"><span data-stu-id="a87ea-132">**Upgrade:** Workbooks will auto upgrade in the document library if Auto Upgrade is enabled for the PowerPivot system Service in the SharePoint farm,</span></span><br /><br /> <span data-ttu-id="a87ea-133">**排程資料重新整理** ：不支援。</span><span class="sxs-lookup"><span data-stu-id="a87ea-133">**Schedule data refresh:** NOT supported.</span></span> <span data-ttu-id="a87ea-134">活頁簿需要升級。</span><span class="sxs-lookup"><span data-stu-id="a87ea-134">Workbook needs to be upgraded.</span></span>|<span data-ttu-id="a87ea-135">**體驗** ：使用者可以與活頁簿進行互動，而且可以使用它做為其他方案的資料來源。</span><span class="sxs-lookup"><span data-stu-id="a87ea-135">**Experience:** Users can interact with the workbook and use it as a data source for other solutions.</span></span><br /><br /> <span data-ttu-id="a87ea-136">**升級** ：無法使用自動升級。</span><span class="sxs-lookup"><span data-stu-id="a87ea-136">**Upgrade:** Auto upgrade is not available.</span></span> <span data-ttu-id="a87ea-137">使用者必須手動將其 2008 R2 活頁簿升級為 2012 版本或 Office 2013 版本。</span><span class="sxs-lookup"><span data-stu-id="a87ea-137">Users must manually upgrade their 2008 R2 workbooks to the 2012 version or to the office 2013 version.</span></span><br /><br /> <span data-ttu-id="a87ea-138">**排程資料重新整理** ：不支援。</span><span class="sxs-lookup"><span data-stu-id="a87ea-138">**Schedule data refresh:** NOT supported.</span></span> <span data-ttu-id="a87ea-139">活頁簿需要升級。</span><span class="sxs-lookup"><span data-stu-id="a87ea-139">Workbook needs to be upgraded.</span></span>|  
|<span data-ttu-id="a87ea-140">**2012 PowerPivot for Excel**</span><span class="sxs-lookup"><span data-stu-id="a87ea-140">**2012 PowerPivot for Excel**</span></span>|<span data-ttu-id="a87ea-141">不支援</span><span class="sxs-lookup"><span data-stu-id="a87ea-141">Not supported</span></span>|<span data-ttu-id="a87ea-142">所有功能</span><span class="sxs-lookup"><span data-stu-id="a87ea-142">All Features</span></span>|<span data-ttu-id="a87ea-143">**體驗** ：使用者可以透過瀏覽器與活頁簿進行互動，而且可以使用它做為其他方案的資料來源。</span><span class="sxs-lookup"><span data-stu-id="a87ea-143">**Experience:** Users can interact with the workbook in the browser and use it as a data source for other solutions.</span></span> <span data-ttu-id="a87ea-144">可以使用排程資料重新整理。</span><span class="sxs-lookup"><span data-stu-id="a87ea-144">Schedule data refresh is available.</span></span><br /><br /> <span data-ttu-id="a87ea-145">**升級** ：不支援自動升級。</span><span class="sxs-lookup"><span data-stu-id="a87ea-145">**Upgrade:** Auto upgrade is not supported.</span></span> <span data-ttu-id="a87ea-146">使用者可以手動將其活頁簿升級為 Office 2013 版本。</span><span class="sxs-lookup"><span data-stu-id="a87ea-146">Users can manually upgrade their workbooks to the Office 2013 version.</span></span><br /><br /> <span data-ttu-id="a87ea-147">**排程資料重新整理** ：支援。</span><span class="sxs-lookup"><span data-stu-id="a87ea-147">**Schedule data refresh:** supported.</span></span>|  
|<span data-ttu-id="a87ea-148">**Excel 2013**</span><span class="sxs-lookup"><span data-stu-id="a87ea-148">**Excel 2013**</span></span>|<span data-ttu-id="a87ea-149">不支援</span><span class="sxs-lookup"><span data-stu-id="a87ea-149">Not supported</span></span>|<span data-ttu-id="a87ea-150">不支援</span><span class="sxs-lookup"><span data-stu-id="a87ea-150">Not supported</span></span>|<span data-ttu-id="a87ea-151">所有功能</span><span class="sxs-lookup"><span data-stu-id="a87ea-151">All Features</span></span>|  
  
##  <a name="upgrade-to-sql-server-2012-service-pack-1-sp1-workbooks-from-2008-r2-workbooks"></a><a name="bkmk_to_2012sp1_from_2008r2"></a><span data-ttu-id="a87ea-152">從 2008 R2 活頁簿升級至 SQL Server 2012 Service Pack 1 (SP1) 活頁簿</span><span class="sxs-lookup"><span data-stu-id="a87ea-152">Upgrade to SQL Server 2012 Service Pack 1 (SP1) workbooks from 2008 R2 Workbooks</span></span>  
 <span data-ttu-id="a87ea-153">本節將描述如何從 SQL Server 2008 R2 PowerPivot for Excel 2010 活頁簿升級為 SQL Server 2012 SP1 PowerPivot for Excel 2013 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="a87ea-153">This section describes upgrading to SQL Server 2012 SP1 PowerPivot for Excel 2013 workbooks from SQL Server 2008 R2 PowerPivot for Excel 2010 workbooks.</span></span>  
  
 <span data-ttu-id="a87ea-154">**行為變更** ：在 SQL Server 2012 SP1 PowerPivot for SharePoint 2013 中使用 SQL Server 2008 R2 PowerPivot 活頁簿時，這些活頁簿不會自動升級。</span><span class="sxs-lookup"><span data-stu-id="a87ea-154">**Behavior Change:** SQL Server 2008 R2 PowerPivot workbooks will not be automatically upgraded  when they are used in SQL Server 2012 SP1 PowerPivot for SharePoint 2013.</span></span> <span data-ttu-id="a87ea-155">因此，排程的資料重新整理不會針對 SQL Server 2008 R2 PowerPivot 活頁簿運作</span><span class="sxs-lookup"><span data-stu-id="a87ea-155">Therefore, scheduled data refreshes will not work for SQL Server 2008 R2 PowerPivot workbooks</span></span>  
  
 <span data-ttu-id="a87ea-156">2008 R2 活頁簿將在 PowerPivot for SharePoint 2013 中開啟，但是排程的資料重新整理不會運作。</span><span class="sxs-lookup"><span data-stu-id="a87ea-156">2008 R2 workbooks will open in PowerPivot for SharePoint 2013, however scheduled data refreshes will not work.</span></span> <span data-ttu-id="a87ea-157">如果您檢閱重新整理記錄，將會看到類似以下的錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="a87ea-157">If you review the refresh history you will see an error message similar to the following:</span></span>  
  
 <span data-ttu-id="a87ea-158">「活頁簿包含不支援的 PowerPivot 模型。</span><span class="sxs-lookup"><span data-stu-id="a87ea-158">"The workbook contains an unsupported PowerPivot model.</span></span> <span data-ttu-id="a87ea-159">活頁簿中的 PowerPivot 模型是採用 SQL Server 2008 R2 PowerPivot for Excel 2010 格式。</span><span class="sxs-lookup"><span data-stu-id="a87ea-159">The PowerPivot model in the workbook is in the SQL Server 2008 R2 PowerPivot for Excel 2010 format.</span></span> <span data-ttu-id="a87ea-160">支援的 PowerPivot 模型如下:</span><span class="sxs-lookup"><span data-stu-id="a87ea-160">Supported PowerPivot models are the following:</span></span>  
  
-   <span data-ttu-id="a87ea-161">SQL Server 2012 PowerPivot for Excel 2010。</span><span class="sxs-lookup"><span data-stu-id="a87ea-161">SQL Server 2012 PowerPivot for Excel 2010.</span></span>  
  
-   <span data-ttu-id="a87ea-162">SQL Server 2012 PowerPivot for Excel 2013。</span><span class="sxs-lookup"><span data-stu-id="a87ea-162">SQL Server 2012 PowerPivot for Excel 2013.</span></span>  
  
 <span data-ttu-id="a87ea-163">**如何升級活頁簿** ：在您將活頁簿升級為 2012 活頁簿之前，排程的資料重新整理無法運作。</span><span class="sxs-lookup"><span data-stu-id="a87ea-163">**How to upgrade a workbook:** The Scheduled data refresh will not work until you upgrade the workbook to a 2012 workbook.</span></span> <span data-ttu-id="a87ea-164">若要升級活頁簿及它所包含的模型，請完成下列其中一項作業：</span><span class="sxs-lookup"><span data-stu-id="a87ea-164">To upgrade the workbook and model it contains, complete one of the following:</span></span>  
  
-   <span data-ttu-id="a87ea-165">在已安裝 SQL Server 2012 PowerPivot for Excel 增益集的 Microsoft Excel 2010 中下載並開啟活頁簿。</span><span class="sxs-lookup"><span data-stu-id="a87ea-165">Download and open the workbook in Microsoft Excel 2010 with the SQL Server 2012 PowerPivot for Excel add-in installed.</span></span>  
  
     <span data-ttu-id="a87ea-166">開啟 PowerPivot 視窗並升級 PowerPivot 模型。</span><span class="sxs-lookup"><span data-stu-id="a87ea-166">Open the PowerPivot window and upgrade the PowerPivot model.</span></span>  
  
     <span data-ttu-id="a87ea-167">然後，儲存活頁簿並重新發行至 SharePoint。</span><span class="sxs-lookup"><span data-stu-id="a87ea-167">Then save the workbook and republish it to SharePoint.</span></span>  
  
-   <span data-ttu-id="a87ea-168">在 Microsoft Excel 2013 中下載並開啟活頁簿。</span><span class="sxs-lookup"><span data-stu-id="a87ea-168">Download and open the workbook in Microsoft Excel 2013.</span></span>  
  
     <span data-ttu-id="a87ea-169">開啟 PowerPivot 視窗並升級 PowerPivot 模型。</span><span class="sxs-lookup"><span data-stu-id="a87ea-169">Open the PowerPivot window and upgrade the PowerPivot model.</span></span>  
  
     <span data-ttu-id="a87ea-170">然後，儲存活頁簿並重新發行至 SharePoint 伺服器。</span><span class="sxs-lookup"><span data-stu-id="a87ea-170">Then save the workbook and republish it to the SharePoint server.</span></span>  
  
 <span data-ttu-id="a87ea-171">如需 Analysis Services 功能變更的詳細資訊，請參閱[SQL Server 2014 中 Analysis Services 功能的行為變更](../../behavior-changes-to-analysis-services-features-in-sql-server-2014.md)</span><span class="sxs-lookup"><span data-stu-id="a87ea-171">For more information on Changes to Analysis Services features, see [Behavior Changes to Analysis Services Features in SQL Server 2014](../../behavior-changes-to-analysis-services-features-in-sql-server-2014.md)</span></span>  
  
 <span data-ttu-id="a87ea-172">如需重新整理記錄的詳細資訊，請參閱[View Data Refresh history &#40;PowerPivot for SharePoint&#41;](../../power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="a87ea-172">For more information on refresh history, see [View Data Refresh History &#40;PowerPivot for SharePoint&#41;](../../power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md).</span></span>  
  
##  <a name="upgrade-to-office-2013-workbooks-from-versions-created-by-using-the-2012-powerpivot-add-in-for-excel"></a><a name="bkmk_to_2012sp1_from_2012"></a><span data-ttu-id="a87ea-173">從使用適用于 Excel 的 2012 PowerPivot 增益集所建立的版本升級為 Office 2013 活頁簿</span><span class="sxs-lookup"><span data-stu-id="a87ea-173">Upgrade to Office 2013 workbooks from Versions created by using the 2012 PowerPivot Add-In for Excel</span></span>  
 <span data-ttu-id="a87ea-174">本節將描述如何 **從** SQL Server 2012 PowerPivot for Excel 2010 活頁簿升級 **為** SQL Server 2012 SP1 PowerPivot for Excel 2013。</span><span class="sxs-lookup"><span data-stu-id="a87ea-174">This section describes Upgrading **to** SQL Server 2012 SP1 PowerPivot in Excel 2013 **from** SQL Server 2012 PowerPivot for Excel 2010 workbooks.</span></span>  
  
 <span data-ttu-id="a87ea-175">升級活頁簿可解決下列嘗試針對舊版活頁簿進行排程資料重新整理時所發生的錯誤：</span><span class="sxs-lookup"><span data-stu-id="a87ea-175">Upgrading a workbook resolves the following error that occurs when attempting scheduled data refresh on the previous workbook version workbook:</span></span>  
  
 <span data-ttu-id="a87ea-176">「無法使用舊版 PowerPivot 所建立之活頁簿的重新整理作業。」</span><span class="sxs-lookup"><span data-stu-id="a87ea-176">"Refresh operation for workbooks created with earlier version of PowerPivot is not available."</span></span>  
  
 <span data-ttu-id="a87ea-177">**如何升級活頁簿**</span><span class="sxs-lookup"><span data-stu-id="a87ea-177">**How to upgrade a workbook**</span></span>  
  
1.  <span data-ttu-id="a87ea-178">在 Microsoft Excel 2013 中手動開啟每個活頁簿，藉以進行升級。</span><span class="sxs-lookup"><span data-stu-id="a87ea-178">Upgrade each workbook manually by opening it in Microsoft Excel 2013.</span></span>  
  
2.  <span data-ttu-id="a87ea-179">若要升級活頁簿及它所包含的模型，請在 Microsoft Excel 2013 中下載並開啟活頁簿。</span><span class="sxs-lookup"><span data-stu-id="a87ea-179">To upgrade the workbook and model it contains, download and open the workbook in Microsoft Excel 2013.</span></span>  
  
3.  <span data-ttu-id="a87ea-180">開啟 PowerPivot 視窗並升級 PowerPivot 模型。</span><span class="sxs-lookup"><span data-stu-id="a87ea-180">Open the PowerPivot window and upgrade the PowerPivot model.</span></span>  
  
4.  <span data-ttu-id="a87ea-181">然後，儲存活頁簿並重新發行至 SharePoint 2013 伺服器。</span><span class="sxs-lookup"><span data-stu-id="a87ea-181">Then save the workbook and republish it to the SharePoint 2013 server.</span></span>  
  
##  <a name="upgrade-to-sql-server-2012-workbooks-from-versions-created-by-using-the-2008-r2-powerpivot-add-in-for-excel-2010"></a><a name="bkmk_to_2012_from_2008R2"></a><span data-ttu-id="a87ea-182">從使用適用于 2010 Excel 的 2008 R2 PowerPivot 增益集所建立的版本升級至 SQL Server 2012 活頁簿</span><span class="sxs-lookup"><span data-stu-id="a87ea-182">Upgrade to SQL Server 2012 workbooks from Versions created by using the 2008 R2 PowerPivot Add-In for Excel 2010</span></span>  
 <span data-ttu-id="a87ea-183">本節將描述如何 **從** SQL Server 2008 R2 PowerPivot for Excel 2010 活頁簿升級 **為** SQL Server 2012 PowerPivot for Excel 2010。</span><span class="sxs-lookup"><span data-stu-id="a87ea-183">This section describes Upgrading **to** SQL Server 2012 PowerPivot for Excel 2010 **from** SQL Server 2008 R2 PowerPivot for Excel 2010 workbooks.</span></span>  
  
 <span data-ttu-id="a87ea-184">升級活頁簿可解決下列嘗試針對舊版活頁簿進行排程資料重新整理時所發生的錯誤：</span><span class="sxs-lookup"><span data-stu-id="a87ea-184">Upgrading a workbook resolves the following error that occurs when attempting scheduled data refresh on the previous workbook version workbook:</span></span>  
  
 <span data-ttu-id="a87ea-185">「無法使用舊版 PowerPivot 所建立之活頁簿的重新整理作業。」</span><span class="sxs-lookup"><span data-stu-id="a87ea-185">"Refresh operation for workbooks created with earlier version of PowerPivot is not available."</span></span>  
  
 <span data-ttu-id="a87ea-186">**如何升級活頁簿**</span><span class="sxs-lookup"><span data-stu-id="a87ea-186">**How to upgrade a workbook**</span></span>  
  
 <span data-ttu-id="a87ea-187">升級的方式有兩種：</span><span class="sxs-lookup"><span data-stu-id="a87ea-187">There are two ways to upgrade:</span></span>  
  
1.  <span data-ttu-id="a87ea-188">在具有 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 版 PowerPivot for Excel 的電腦上使用 Excel 來開啟每個活頁簿，藉以手動升級每個活頁簿，然後將它重新發行至伺服器。</span><span class="sxs-lookup"><span data-stu-id="a87ea-188">Upgrade each workbook manually by opening it in Excel on a computer that has the [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] version of PowerPivot for Excel, and then republish it to the server.</span></span> <span data-ttu-id="a87ea-189">當您在新版增益集中開啟活頁簿時，就會執行以下內部作業：活頁簿資料連接字串中的資料提供者會更新為 MSOLAP.5，中繼資料也會更新，而且還會重新建立關聯性，以符合新的實作。</span><span class="sxs-lookup"><span data-stu-id="a87ea-189">When you open the workbook in the newer version of the add-in, the following internal operations occur: the data provider in the workbook data connection string is updated to MSOLAP.5, metadata is updated, and relationships are recreated to conform to a newer implementation.</span></span>  
  
2.  <span data-ttu-id="a87ea-190">或者，SharePoint 管理員也可以針對 SharePoint 伺服器陣列中的 PowerPivot 系統服務啟用自動升級功能，以便在排程資料重新整理執行時自動升級 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] PowerPivot 活頁簿 (只會升級針對排程資料重新整理設定的活頁簿)。</span><span class="sxs-lookup"><span data-stu-id="a87ea-190">Alternatively, a SharePoint Administrator  can enable the auto-upgrade feature for the PowerPivot System Service in a SharePoint farm to  automatically upgrade a [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] PowerPivot workbook when schedule data refresh runs (only workbooks that are configured for scheduled data refresh are upgraded).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a87ea-191">自動升級是伺服器組態功能。您無法針對特定活頁簿、文件庫或網站集合啟用或停用此功能。</span><span class="sxs-lookup"><span data-stu-id="a87ea-191">Automatic upgrade is a server configuration feature; you cannot enable or disable it for specific workbooks, libraries, or site collections.</span></span>  
  
 <span data-ttu-id="a87ea-192">**如何在資料重新整理期間設定自動升級**</span><span class="sxs-lookup"><span data-stu-id="a87ea-192">**How to configure automatic upgrade during data refresh**</span></span>  
  
 <span data-ttu-id="a87ea-193">若要使用自動升級，您必須在 PowerPivot 組態工具中選取 **[自動升級 PowerPivot 活頁簿，以便從伺服器進行資料重新整理]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="a87ea-193">To use automatic upgrade, you must select the **Automatically upgrade PowerPivot workbooks to enable data refresh from the server** checkbox in the PowerPivot Configuration Tool.</span></span> <span data-ttu-id="a87ea-194">在此工具中，該核取方塊位於 **[升級 PowerPivot 系統服務]** 頁面上，而且位於 **[建立 PowerPivot 服務應用程式]** 頁面上 (如果您要設定新安裝的話)。</span><span class="sxs-lookup"><span data-stu-id="a87ea-194">Within the tool, the checkbox is on the **Upgrade PowerPivot System Service** page, and on the **Create PowerPivot Service Application** page if you are configuring a new installation.</span></span>  
  
 <span data-ttu-id="a87ea-195">您可以執行下列指令程式來確認是否已啟用自動升級：</span><span class="sxs-lookup"><span data-stu-id="a87ea-195">You can run the following cmdlet to verify whether automatic upgrade is enabled:</span></span>  
  
```  
PS C:\Windows\system32> Get-PowerPivotSystemService  
```  
  
 <span data-ttu-id="a87ea-196">Get-PowerPivotSystemService 的輸出是屬性和對應值的清單。</span><span class="sxs-lookup"><span data-stu-id="a87ea-196">The output from Get-PowerPivotSystemService is a list of properties and corresponding values.</span></span> <span data-ttu-id="a87ea-197">您應該會在屬性清單中看見 `WorkbookUpgradeOnDataRefresh`。</span><span class="sxs-lookup"><span data-stu-id="a87ea-197">You should see `WorkbookUpgradeOnDataRefresh` in the property list.</span></span> <span data-ttu-id="a87ea-198">如果自動升級已啟用，它就會設定為 **true** 。</span><span class="sxs-lookup"><span data-stu-id="a87ea-198">It will be set to **true** if automatic upgrade is enabled.</span></span> <span data-ttu-id="a87ea-199">如果它是 **false**，請繼續進行下一個步驟，啟用自動活頁簿升級。</span><span class="sxs-lookup"><span data-stu-id="a87ea-199">If it is **false**, continue to the next step, enabling automatic workbook upgrade.</span></span>  
  
 <span data-ttu-id="a87ea-200">若要啟用自動活頁簿升級，請執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="a87ea-200">To enable automatic workbook upgrade, run the following command:</span></span>  
  
```  
PS C:\Windows\system32> Set-PowerPivotSystemService -WorkbookUpgradeOnDataRefresh:$true -Confirm:$false  
```  
  
 <span data-ttu-id="a87ea-201">升級活頁簿之後，您就可以在 PowerPivot for Excel 增益集中使用排程的資料重新整理和新功能。</span><span class="sxs-lookup"><span data-stu-id="a87ea-201">After you upgrade the workbook, you can use scheduled data refresh and new features in the PowerPivot for Excel add-in.</span></span>  
  
##  <a name="running-multiple-workbook-versions-on-a-newer-server"></a><a name="bkmk_runold"></a> <span data-ttu-id="a87ea-202">執行較新伺服器上的多個活頁簿版本</span><span class="sxs-lookup"><span data-stu-id="a87ea-202">Running Multiple Workbook Versions on a Newer Server</span></span>  
 <span data-ttu-id="a87ea-203">您可以在 [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] 的 [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)]執行個體上並存執行舊版與新版的 PowerPivot 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="a87ea-203">You can run older and newer versions of PowerPivot workbooks side by side on a [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] instance of [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)].</span></span>  
  
 <span data-ttu-id="a87ea-204">根據伺服器的安裝方式而定， **您可能需要** 安裝舊版 Analysis Services OLE DB 提供者，才能在同一部伺服器上存取舊版和新版活頁簿。</span><span class="sxs-lookup"><span data-stu-id="a87ea-204">Depending on how you installed the server, **you might need** to install a previous version of the Analysis Services OLE DB provider before you can access older and newer workbooks on the same server.</span></span>  
  
 <span data-ttu-id="a87ea-205">請注意，目前不支援在 [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 的舊版 SQL Server 執行個體上發行新版的活頁簿。</span><span class="sxs-lookup"><span data-stu-id="a87ea-205">Note that Publishing newer version workbooks on previous SQL Server instances of [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] is not supported.</span></span> <span data-ttu-id="a87ea-206">[!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] 執行個體無法載入您在 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 版 [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)]中建立的活頁簿，而且 SQL Server 2012 執行個體無法載入包含您使用 [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] 版 PowerPivot for Excel 所建立之進階資料模型的 Office 2013 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="a87ea-206">A [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] instance will not load a workbook that you created in the [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] version of [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)], and a SQL Server 2012 instance will not load Office 2013 workbooks with advanced data models that you created using the [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] version of PowerPivot in Excel.</span></span>  
  
###  <a name="how-to-check-for-msolap-data-provider-information-in-a-powerpivot-workbook"></a><a name="bkmk_msolapxslx"></a><span data-ttu-id="a87ea-207">如何檢查 PowerPivot 活頁簿中的 MSOLAP Data Provider 資訊</span><span class="sxs-lookup"><span data-stu-id="a87ea-207">How to Check for MSOLAP Data Provider Information in a PowerPivot Workbook</span></span>  
 <span data-ttu-id="a87ea-208">請利用下列指示，檢查 PowerPivot 活頁簿中使用哪一個 OLE DB 提供者。</span><span class="sxs-lookup"><span data-stu-id="a87ea-208">Use the following instructions to check which OLE DB provider is used in a PowerPivot workbook.</span></span> <span data-ttu-id="a87ea-209">檢查資料連接資訊不需要安裝 [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)] 增益集。</span><span class="sxs-lookup"><span data-stu-id="a87ea-209">Checking the data connection information does not require the [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)] add-in to be installed.</span></span>  
  
1.  <span data-ttu-id="a87ea-210">在 Excel 中的 [資料] 索引標籤上，按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="a87ea-210">In Excel, on the Data tab, click **Connections**.</span></span> <span data-ttu-id="a87ea-211">按一下 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="a87ea-211">Click **Properties**.</span></span>  
  
2.  <span data-ttu-id="a87ea-212">在 **[定義]** 索引標籤上，提供者版本會出現在連接字串的開頭。</span><span class="sxs-lookup"><span data-stu-id="a87ea-212">On the **Definition** tab, the provider version appears at the beginning of the connection string.</span></span>  
  
     <span data-ttu-id="a87ea-213">[]\*\*\*\* 表示活頁簿為 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a87ea-213">**Provider=MSOLAP.5** indicates the workbook is [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].</span></span>  
  
     <span data-ttu-id="a87ea-214">[]\*\*\*\* 則是指 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a87ea-214">**Provider=MSOLAP.4** indicates [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)].</span></span>  
  
     <span data-ttu-id="a87ea-215">[**資料來源 = $Embedded $** ] 表示活頁簿是使用內嵌資料庫的 PowerPivot 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="a87ea-215">**Data Source=$Embedded$** indicates that the workbook is a PowerPivot workbook, using an embedded database.</span></span>  
  
###  <a name="how-to-check-for-the-current-version-of-the-msolap-data-provider-on-a-local-computer"></a><a name="bkmk_msolappc"></a> <span data-ttu-id="a87ea-216">如何檢查本機電腦上目前的 MSOLAP 資料提供者版本</span><span class="sxs-lookup"><span data-stu-id="a87ea-216">How to Check for the Current Version of the MSOLAP Data Provider on a Local Computer</span></span>  
 <span data-ttu-id="a87ea-217">請利用下列指示，檢查哪一個 OLE DB 提供者是目前在伺服器或工作站上執行 PowerPivot 活頁簿的版本。</span><span class="sxs-lookup"><span data-stu-id="a87ea-217">Use the following instructions to check which OLE DB provider is the current version on the server or workstation that runs PowerPivot workbooks.</span></span> <span data-ttu-id="a87ea-218">得知目前版本可協助您在升級之後針對資料連接錯誤進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="a87ea-218">Knowing the current version can help you troubleshoot data connection errors after upgrading.</span></span>  
  
1.  <span data-ttu-id="a87ea-219">在 [登錄編輯器] 中，移至 HKEY_CLASSES_ROOT</span><span class="sxs-lookup"><span data-stu-id="a87ea-219">In the Registry Editor, go to HKEY_CLASSES_ROOT</span></span>  
  
2.  <span data-ttu-id="a87ea-220">向下捲動至 MSOLAP。</span><span class="sxs-lookup"><span data-stu-id="a87ea-220">Scroll down to MSOLAP.</span></span> <span data-ttu-id="a87ea-221">確認 MSOLAP.5 列在系統上所安裝的 OLAP 提供者中。</span><span class="sxs-lookup"><span data-stu-id="a87ea-221">Verify that MSOLAP.5 is listed among the OLAP providers installed on the system.</span></span> <span data-ttu-id="a87ea-222">確認 MSOLAP | CurVer 設定為 MSOLAP.5</span><span class="sxs-lookup"><span data-stu-id="a87ea-222">Verify that MSOLAP | CurVer is set to MSOLAP.5</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a87ea-223">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a87ea-223">See Also</span></span>  
 <span data-ttu-id="a87ea-224">[將 PowerPivot 遷移至 SharePoint 2013](migrate-power-pivot-to-sharepoint-2013.md) </span><span class="sxs-lookup"><span data-stu-id="a87ea-224">[Migrate PowerPivot to SharePoint 2013](migrate-power-pivot-to-sharepoint-2013.md) </span></span>  
 <span data-ttu-id="a87ea-225">[升級 PowerPivot for SharePoint](../../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="a87ea-225">[Upgrade PowerPivot for SharePoint](../../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md) </span></span>  
 <span data-ttu-id="a87ea-226">[Analysis Services 和商業智慧的新功能](../../what-s-new-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="a87ea-226">[What's New in Analysis Services and Business Intelligence](../../what-s-new-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="a87ea-227">查看資料重新整理記錄 &#40;PowerPivot for SharePoint&#41;</span><span class="sxs-lookup"><span data-stu-id="a87ea-227">View Data Refresh History &#40;PowerPivot for SharePoint&#41;</span></span>](../../power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md)  
  
  
