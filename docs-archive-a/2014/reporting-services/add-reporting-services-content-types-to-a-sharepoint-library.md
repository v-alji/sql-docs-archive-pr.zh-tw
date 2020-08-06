---
title: 將報表伺服器內容類型加入至程式庫 (SharePoint 整合模式中的 Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ac9136c8-9ef4-484c-8e9d-05008a186db5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9e0ee56c235a54920fba5389a61f300eeaa65329
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707313"
---
# <a name="add-report-server-content-types-to-a-library-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="3972b-102">將報表伺服器內容類型加入至文件庫 (SharePoint 整合模式中的 Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="3972b-102">Add Report Server Content Types to a Library (Reporting Services in SharePoint Integrated Mode)</span></span>
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="3972b-103">會提供預先定義的 SharePoint 內容類型，可用來管理共用資料來源檔案 (.rsds)、報表模型檔案 (.smdl)，以及報表產生器的報表定義檔案 (.rdl)。</span><span class="sxs-lookup"><span data-stu-id="3972b-103">provides predefined SharePoint content types that are used to manage shared data source (.rsds) files, report models (.smdl), and Report Builder report definition (.rdl) files.</span></span> <span data-ttu-id="3972b-104">將 **[報表產生器報表]**、 **[報表模型]** 和 **[報表資料來源]** 內容類型加入至文件庫會啟用 **[新增]** 命令，讓您能夠建立該類型的新文件。</span><span class="sxs-lookup"><span data-stu-id="3972b-104">Adding a **Report Builder Report**, **Report Model**, and **Report Data Source** content type to a library enables the **New** command so that you can create new documents of that type.</span></span>  
  
 <span data-ttu-id="3972b-105">**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="3972b-105">**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint mode</span></span>  
  
 <span data-ttu-id="3972b-106">若要將內容類型加入至文件庫，您必須是網站管理員或具有「完整控制」等級的權限。</span><span class="sxs-lookup"><span data-stu-id="3972b-106">To add content types to a library, you must be a site administrator or have Full Control level of permission.</span></span>  
  
 <span data-ttu-id="3972b-107">系統會針對從下列 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [商務智慧中心] **網站範本建立的現有網站集合，在所有文件庫中自動啟用** 內容類型與內容類型管理。</span><span class="sxs-lookup"><span data-stu-id="3972b-107">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] content types and content type management will automatically be enabled in all document libraries for existing site collections created from the following **Business Intelligence Center** site template.</span></span>  
  
 <span data-ttu-id="3972b-108">在 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 整合之後建立的網站將不會啟用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 內容類型。</span><span class="sxs-lookup"><span data-stu-id="3972b-108">Sites created after the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] integration will not have the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] content types enabled.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="3972b-109">如果您先前 **沒有** 設定文件庫的內容類型，請先啟用內容類型的管理，然後再啟用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 內容類型。</span><span class="sxs-lookup"><span data-stu-id="3972b-109">If you have **not** previously configured content types for a library, first enable management of content types, then enable the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] content types.</span></span> <span data-ttu-id="3972b-110">請參閱在單一文件庫中啟用內容類型管理的程序。</span><span class="sxs-lookup"><span data-stu-id="3972b-110">See the procedures on enabling content type management in a single document library.</span></span>  
  
 <span data-ttu-id="3972b-111">**短片：** [(SSRS) 啟用 SharePoint2010.wmv 中的內容類型](http://www.youtube.com/watch?v=yqhm3DrtT1w) (http://www.youtube.com/watch?v=yqhm3DrtT1w)。</span><span class="sxs-lookup"><span data-stu-id="3972b-111">**Short video:** [(SSRS) Enabling Content Types in SharePoint2010.wmv](http://www.youtube.com/watch?v=yqhm3DrtT1w) (http://www.youtube.com/watch?v=yqhm3DrtT1w).</span></span>  
  
 <span data-ttu-id="3972b-112">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="3972b-112">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="3972b-113">在現有 BI 中心的所有文件庫中啟用內容類型</span><span class="sxs-lookup"><span data-stu-id="3972b-113">Enable content types in all document libraries in an existing BI center</span></span>](#bkmk_enable_all)  
  
-   [<span data-ttu-id="3972b-114">啟用單一文件庫的內容類型管理 (SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="3972b-114">To enable content type management for a single document library (SharePoint 2013)</span></span>](#bkmk_enable_content_management)  
  
-   [<span data-ttu-id="3972b-115"> (SharePoint 2013 新增 Reporting Services 內容類型) </span><span class="sxs-lookup"><span data-stu-id="3972b-115">To add Reporting Services content types (SharePoint 2013)</span></span>](#bkmk_add_single)  
  
-   [<span data-ttu-id="3972b-116">啟用單一文件庫的內容類型管理 (SharePoint 2010)</span><span class="sxs-lookup"><span data-stu-id="3972b-116">To enable content type management for a single document library (SharePoint 2010)</span></span>](#bkmk_enable_content_management_2010)  
  
-   [<span data-ttu-id="3972b-117">若要加入報表伺服器內容類型 (SharePoint 2010)</span><span class="sxs-lookup"><span data-stu-id="3972b-117">To add report server content types (SharePoint 2010)</span></span>](#bkmk_add_single_2010)  
  
-   [<span data-ttu-id="3972b-118">啟用多個 BI 網站的內容類型與內容管理</span><span class="sxs-lookup"><span data-stu-id="3972b-118">To enable Content types and content management for multiple BI sites</span></span>](#bkmk_enable_multiple_sites)  
  
##  <a name="enable-content-types-in-all-document-libraries-in-an-existing-bi-center"></a><a name="bkmk_enable_all"></a><span data-ttu-id="3972b-119">在現有 BI 中心的所有文件庫中啟用內容類型</span><span class="sxs-lookup"><span data-stu-id="3972b-119">Enable content types in all document libraries in an existing BI center</span></span>  
  
1.  <span data-ttu-id="3972b-120">若要在現有 **商業智慧中心** 網站的所有文件庫中啟用內容類型與內容管理，您可以切換 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 整合功能。</span><span class="sxs-lookup"><span data-stu-id="3972b-120">To enable the content types and content management in all document libraries in an existing **Business Intelligence Center** site, you can toggle the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] integration feature.</span></span>  
  
2.  <span data-ttu-id="3972b-121">前往 **[網站設定]**。</span><span class="sxs-lookup"><span data-stu-id="3972b-121">Go to **Site settings**.</span></span>  
  
    -   <span data-ttu-id="3972b-122">在 SharePoint 2013，按一下 **[設定]** 圖示。</span><span class="sxs-lookup"><span data-stu-id="3972b-122">In SharePoint 2013, click the **Settings** icon.</span></span> <span data-ttu-id="3972b-123">![SharePoint 設定](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint 設定")</span><span class="sxs-lookup"><span data-stu-id="3972b-123">![SharePoint Settings](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint Settings")</span></span>  
  
    -   <span data-ttu-id="3972b-124">在 SharePoint 2010，按一下 **[網站動作]**，然後按一下 **[網站設定]**。</span><span class="sxs-lookup"><span data-stu-id="3972b-124">In SharePoint 2010, click **Site Actions**, then click **Site Settings**.</span></span>  
  
3.  <span data-ttu-id="3972b-125">按一下 [**網站集合功能**]。</span><span class="sxs-lookup"><span data-stu-id="3972b-125">Click **Site collection features**.</span></span>  
  
4.  <span data-ttu-id="3972b-126">尋找 **[報表伺服器整合功能]** 並按一下 **[停用]**。</span><span class="sxs-lookup"><span data-stu-id="3972b-126">Find the **Report Server Integration Feature** and click **Deactivate**.</span></span>  
  
     <span data-ttu-id="3972b-127">![rs_reportserver_integration_active](media/rs-reportserver-integration-active.gif "rs_reportserver_integration_active")</span><span class="sxs-lookup"><span data-stu-id="3972b-127">![rs_reportserver_integration_active](media/rs-reportserver-integration-active.gif "rs_reportserver_integration_active")</span></span>  
  
5.  <span data-ttu-id="3972b-128">重新整理瀏覽器，然後按一下 **[報表伺服器整合功能]** 的 **[啟動]**。</span><span class="sxs-lookup"><span data-stu-id="3972b-128">Refresh the browser then click **Activate** for the **Report Server Integration Feature**.</span></span>  
  
    <span data-ttu-id="3972b-129">![取消](media/rs-reportserver-integration-deactivate.gif "rs_reportserver_integration_deactive")</span><span class="sxs-lookup"><span data-stu-id="3972b-129">![Deactivate](media/rs-reportserver-integration-deactivate.gif "rs_reportserver_integration_deactive")</span></span>  
  
##  <a name="to-enable-content-type-management-for-a-single-document-library-sharepoint-2013"></a><a name="bkmk_enable_content_management"></a><span data-ttu-id="3972b-130">若要啟用單一文件庫的內容類型管理 (SharePoint 2013) </span><span class="sxs-lookup"><span data-stu-id="3972b-130">To enable content type management for a single document library (SharePoint 2013)</span></span>  
  
1.  <span data-ttu-id="3972b-131">開啟要啟用多個內容類型的文件庫。</span><span class="sxs-lookup"><span data-stu-id="3972b-131">Open the library for which you want to enable multiple content types.</span></span>  
  
2.  <span data-ttu-id="3972b-132">在功能區中，按一下 **[文件庫]** 。</span><span class="sxs-lookup"><span data-stu-id="3972b-132">Click **Library** in the ribbon.</span></span>  
  
     <span data-ttu-id="3972b-133">![rs_SharePoint2013_LibraryRibbon](media/rs-sharepoint2013-libraryribbon.gif "rs_SharePoint2013_LibraryRibbon")</span><span class="sxs-lookup"><span data-stu-id="3972b-133">![rs_SharePoint2013_LibraryRibbon](media/rs-sharepoint2013-libraryribbon.gif "rs_SharePoint2013_LibraryRibbon")</span></span>  
  
3.  <span data-ttu-id="3972b-134">在 **[文件庫]** 功能區中，按一下 **[文件庫設定]**。</span><span class="sxs-lookup"><span data-stu-id="3972b-134">On the **Library** ribbon, click **Library Settings**.</span></span> <span data-ttu-id="3972b-135">如果看不到 **[文件庫設定]** 或按鈕已停用，表示您沒有設定文件庫設定 (包括內容類型) 的權限。</span><span class="sxs-lookup"><span data-stu-id="3972b-135">If you do not see **Library Settings** or the button is disabled, you do not have permission to configure library settings, including content types.</span></span>  
  
     <span data-ttu-id="3972b-136">![rs_SharePoint2013_LibrarySettings](media/rs-sharepoint2013-librarysettings.gif "rs_SharePoint2013_LibrarySettings")</span><span class="sxs-lookup"><span data-stu-id="3972b-136">![rs_SharePoint2013_LibrarySettings](media/rs-sharepoint2013-librarysettings.gif "rs_SharePoint2013_LibrarySettings")</span></span>  
  
4.  <span data-ttu-id="3972b-137">按一下 **[一般設定]** 區段中的 **[進階設定]**。</span><span class="sxs-lookup"><span data-stu-id="3972b-137">In the **General Settings** section, click **Advanced settings**.</span></span>  
  
     <span data-ttu-id="3972b-138">![rs_SharePoint2013_LibrarySettings_AdvancedSettings](media/rs-sharepoint2013-librarysettings-advancedsettings.gif "rs_SharePoint2013_LibrarySettings_AdvancedSettings")</span><span class="sxs-lookup"><span data-stu-id="3972b-138">![rs_SharePoint2013_LibrarySettings_AdvancedSettings](media/rs-sharepoint2013-librarysettings-advancedsettings.gif "rs_SharePoint2013_LibrarySettings_AdvancedSettings")</span></span>  
  
5.  <span data-ttu-id="3972b-139">在 **[內容類型]** 區段中，選取 **[是]** 允許內容類型的管理。</span><span class="sxs-lookup"><span data-stu-id="3972b-139">In the **Content Types** section, select **Yes** to allow management of content types.</span></span>  
  
6.  <span data-ttu-id="3972b-140">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="3972b-140">Click **OK**.</span></span>  
  
##  <a name="to-add-reporting-services-content-types-sharepoint-2013"></a><a name="bkmk_add_single"></a> <span data-ttu-id="3972b-141">加入 Reporting Services 內容類型 (SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="3972b-141">To add Reporting Services content types (SharePoint 2013)</span></span>  
  
1.  <span data-ttu-id="3972b-142">開啟要加入 Reporting Services 內容類型的程式庫。</span><span class="sxs-lookup"><span data-stu-id="3972b-142">Open the library for which you want to add Reporting Services content types.</span></span>  
  
2.  <span data-ttu-id="3972b-143">在功能區中，按一下 **[文件庫]**。</span><span class="sxs-lookup"><span data-stu-id="3972b-143">On the ribbon, click **Library**.</span></span>  
  
3.  <span data-ttu-id="3972b-144">按一下 **[文件庫設定]**。</span><span class="sxs-lookup"><span data-stu-id="3972b-144">Click **Library Settings**.</span></span>  
  
4.  <span data-ttu-id="3972b-145">在 **[內容類型]** 底下，按一下 **[從現有的網站內容類型新增]**。</span><span class="sxs-lookup"><span data-stu-id="3972b-145">Under **Content Types**, click **Add from existing site content types**.</span></span>  
  
5.  <span data-ttu-id="3972b-146">在 **[從下列位置選取網站內容類型]**，選取 **[SQL Server Reporting Services 內容類型]**。</span><span class="sxs-lookup"><span data-stu-id="3972b-146">In **Select site content types from**, select **SQL Server Reporting Services Content Types**.</span></span>  
  
6.  <span data-ttu-id="3972b-147">在 **[可用的網站內容類型]** 清單中，按一下 **[報表產生器]**，然後按一下 **[加入]** 將選取的內容類型移至 **[要新增的內容類型]** 清單。</span><span class="sxs-lookup"><span data-stu-id="3972b-147">In the **Available Site Content Types** list, click **Report Builder**, and then click **Add** to move the selected content type to the **Content types to add** list.</span></span>  
  
7.  <span data-ttu-id="3972b-148">若要加入 **[報表模型]** 和 **[報表資料來源]** 內容類型，請重複上一個步驟。</span><span class="sxs-lookup"><span data-stu-id="3972b-148">To add **Report Model** and **Report Data Source** content types, repeat the previous step.</span></span>  
  
8.  <span data-ttu-id="3972b-149">當您完成新增內容類型後，按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="3972b-149">When you finish adding content types, click **OK**.</span></span>  
  
9. > [!NOTE]  
    >  <span data-ttu-id="3972b-150"> 如果在 [新增內容類型] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 頁面上看不到\ \*\*\** 內容類型群組 [SQL Server Reporting Services 內容類型]\ \*\*\** ，表示下列有一條件成立：</span><span class="sxs-lookup"><span data-stu-id="3972b-150">If the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] content type group **SQL Server Reporting Services Content Types** is not visible on the **Add Content Types** page, one of the following conditions is true:</span></span>  
  
    -   <span data-ttu-id="3972b-151">尚未安裝適用於 SharePoint 產品的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 增益集。</span><span class="sxs-lookup"><span data-stu-id="3972b-151">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] add-in for SharePoint products has not been installed.</span></span> <span data-ttu-id="3972b-152">如需詳細資訊，請參閱[安裝或卸載適用于 sharepoint 的 Reporting Services 增益集 &#40;sharepoint 2010 和 sharepoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="3972b-152">For more information, see [Install or Uninstall the Reporting Services Add-in for SharePoint &#40;SharePoint 2010 and SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).</span></span> <span data-ttu-id="3972b-153">本主題包含安裝增益集的資訊，並逐步帶領您進行增益集中僅檔案部分的安裝，以解決問題。</span><span class="sxs-lookup"><span data-stu-id="3972b-153">The topic includes information on installing the add-in and stepping through a files only installation of the add-in to work around issues.</span></span>  
  
    -   <span data-ttu-id="3972b-154">安裝了增益集，但網站集合功能的 [報表伺服器整合功能]\*\*\*\* 未啟用。</span><span class="sxs-lookup"><span data-stu-id="3972b-154">The add-in is installed but the site collection feature **Report Server Integration Feature** is not active.</span></span> <span data-ttu-id="3972b-155">請確認 [網站設定] \*\*\*\* 中的網站集合功能。</span><span class="sxs-lookup"><span data-stu-id="3972b-155">Verify the site collection feature in **Site Settings**.</span></span>  
  
    -   <span data-ttu-id="3972b-156">所有 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 內容類型已經加入至文件庫。</span><span class="sxs-lookup"><span data-stu-id="3972b-156">All of the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] content types have already been added to the library.</span></span> <span data-ttu-id="3972b-157">如果所有內容類型是文件庫的一部分，則該群組已從 **[新增內容類型]** 頁面中移除。</span><span class="sxs-lookup"><span data-stu-id="3972b-157">If all the content types are part of a library, then the group is removed from the **Add Content Types** page.</span></span> <span data-ttu-id="3972b-158">如果您刪除一個或多個 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 內容類型，就會在 **[新增內容類型]** 頁面上看到群組 **[SQL Server Reporting Services 內容類型]** 。</span><span class="sxs-lookup"><span data-stu-id="3972b-158">If you delete one or more of the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] content types, then the group **SQL Server Reporting Services Content Types** will be visible on the **Add Content Types** page.</span></span>  
  
##  <a name="to-enable-content-type-management-for-a-single-document-library-sharepoint-2010"></a><a name="bkmk_enable_content_management_2010"></a><span data-ttu-id="3972b-159">若要啟用單一文件庫的內容類型管理 (SharePoint 2010) </span><span class="sxs-lookup"><span data-stu-id="3972b-159">To enable content type management for a single document library (SharePoint 2010)</span></span>  
  
1.  <span data-ttu-id="3972b-160">開啟要啟用多個內容類型的文件庫。</span><span class="sxs-lookup"><span data-stu-id="3972b-160">Open the library for which you want to enable multiple content types.</span></span> <span data-ttu-id="3972b-161">在文件庫功能表列上，您應該會看見下列功能表： **[新增]**、 **[上傳]**、 **[動作]** 及 **[設定]**。</span><span class="sxs-lookup"><span data-stu-id="3972b-161">On the library menu bar, you should see the following menus: **New**, **Upload**, **Actions**, and **Settings**.</span></span> <span data-ttu-id="3972b-162">如果您看不到 **[設定]**，表示您沒有加入內容類型的權限。</span><span class="sxs-lookup"><span data-stu-id="3972b-162">If you do not see **Settings**, you do not have permission to add a content type.</span></span>  
  
2.  <span data-ttu-id="3972b-163">在 **[文件庫工具]** 功能區中，按一下 **[文件庫]**。</span><span class="sxs-lookup"><span data-stu-id="3972b-163">On the **Library Tools** ribbon, click **Library**.</span></span>  
  
     <span data-ttu-id="3972b-164">![rs_SharePoint2010_LibraryRibbon](media/rs-sharepoint2010-libraryribbon.gif "rs_SharePoint2010_LibraryRibbon")</span><span class="sxs-lookup"><span data-stu-id="3972b-164">![rs_SharePoint2010_LibraryRibbon](media/rs-sharepoint2010-libraryribbon.gif "rs_SharePoint2010_LibraryRibbon")</span></span>  
  
3.  <span data-ttu-id="3972b-165">按一下 **[設定]** 功能區群組的 **[文件庫設定]**。</span><span class="sxs-lookup"><span data-stu-id="3972b-165">On the **Settings** ribbon group, click **Library Settings**.</span></span>  
  
4.  <span data-ttu-id="3972b-166">在 **[一般設定]** 底下，按一下 **[進階設定]**。</span><span class="sxs-lookup"><span data-stu-id="3972b-166">Under **General Settings**, click **Advanced settings**.</span></span>  
  
5.  <span data-ttu-id="3972b-167">在 **[內容類型]** 區段中，選取 **[是]** 允許內容類型的管理。</span><span class="sxs-lookup"><span data-stu-id="3972b-167">In the **Content Types** section, select **Yes** to allow management of content types.</span></span>  
  
6.  <span data-ttu-id="3972b-168">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="3972b-168">Click **OK**.</span></span>  
  
##  <a name="to-add-report-server-content-types-sharepoint-2010"></a><a name="bkmk_add_single_2010"></a><span data-ttu-id="3972b-169">若要將報表伺服器內容類型加入 (SharePoint 2010) </span><span class="sxs-lookup"><span data-stu-id="3972b-169">To add report server content types (SharePoint 2010)</span></span>  
  
1.  <span data-ttu-id="3972b-170">開啟要加入 Reporting Services 內容類型的程式庫。</span><span class="sxs-lookup"><span data-stu-id="3972b-170">Open the library for which you want to add Reporting Services content types.</span></span>  
  
2.  <span data-ttu-id="3972b-171">按一下 **[文件庫工具]** 功能區索引標籤的 **[文件庫]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3972b-171">On the **Library Tools** ribbon tabs, click the **Library tab**.</span></span>  
  
3.  <span data-ttu-id="3972b-172">按一下 **[設定]** 功能區群組的 **[文件庫設定]**。</span><span class="sxs-lookup"><span data-stu-id="3972b-172">On the **Settings** ribbon group, click **Library Settings**.</span></span>  
  
4.  <span data-ttu-id="3972b-173">在 **[內容類型]** 底下，按一下 **[從現有的網站內容類型新增]**。</span><span class="sxs-lookup"><span data-stu-id="3972b-173">Under **Content Types**, click **Add from existing site content types**.</span></span>  
  
5.  <span data-ttu-id="3972b-174">在 **[選取內容類型]** 區段的 **[從下列位置選取網站內容類型]** 中，按一下箭號選取 **[SQL Server Reporting Services 內容類型]**。</span><span class="sxs-lookup"><span data-stu-id="3972b-174">In the **Select Content Types** section, in **Select site content types from**, click the arrow to select **SQL Server Reporting Services Content Types**.</span></span>  
  
6.  <span data-ttu-id="3972b-175">在 **[可用的網站內容類型]** 清單中，按一下 **[報表產生器]**，然後按一下 **[加入]** 將選取的內容類型移至 **[要新增的內容類型]** 清單。</span><span class="sxs-lookup"><span data-stu-id="3972b-175">In the **Available Site Content Types** list, click **Report Builder**, and then click **Add** to move the selected content type to the **Content types to add** list.</span></span>  
  
7.  <span data-ttu-id="3972b-176">若要加入 **[報表模型]** 和 **[報表資料來源]** 內容類型，請重複上一個步驟。</span><span class="sxs-lookup"><span data-stu-id="3972b-176">To add **Report Model** and **Report Data Source** content types, repeat the previous step.</span></span>  
  
8.  <span data-ttu-id="3972b-177">當您完成新增內容類型後，按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="3972b-177">When you finish adding content types, click **OK**.</span></span>  
  
##  <a name="to-enable-content-types-and-content-management-for-multiple-bi-sites"></a><a name="bkmk_enable_multiple_sites"></a><span data-ttu-id="3972b-178">啟用多個 BI 網站的內容類型與內容管理</span><span class="sxs-lookup"><span data-stu-id="3972b-178">To enable Content types and content management for multiple BI sites</span></span>  
  
1.  <span data-ttu-id="3972b-179">對於 SQL Server Reporting Services 2008 及 2008 R2 報表伺服器，您可以啟用多個商業智慧中心網站的內容類型與內容管理：</span><span class="sxs-lookup"><span data-stu-id="3972b-179">For SQL Server Reporting Services 2008 and 2008 R2 report servers, you can enable content types and content management for multiple Business Intelligence Center sites:</span></span>  
  
2.  <span data-ttu-id="3972b-180">在 [SharePoint 管理中心]，按一下 **[一般應用程式設定]**。</span><span class="sxs-lookup"><span data-stu-id="3972b-180">In SharePoint Central Administration, click **General Applications settings**.</span></span> <span data-ttu-id="3972b-181">在 [SQL Server Reporting Services (2008 和 2008 R2)]\*\*\*\* 區段中，按一下 [Reporting Services 整合]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3972b-181">In the **SQL Server Reporting Services (2008 and 2008 R2)** section, click **Reporting Services Integration**.</span></span>  
  
     <span data-ttu-id="3972b-182">![rs_general_app_settings](media/rs-general-app-settings.gif "rs_general_app_settings")</span><span class="sxs-lookup"><span data-stu-id="3972b-182">![rs_general_app_settings](media/rs-general-app-settings.gif "rs_general_app_settings")</span></span>  
  
3.  <span data-ttu-id="3972b-183">按一下 **[所有現有網站集合中的啟動功能]**。</span><span class="sxs-lookup"><span data-stu-id="3972b-183">Click **Activate feature in all exciting site collections**.</span></span>  
  
     <span data-ttu-id="3972b-184">![rs_general_app_settings_old_integrations](media/rs-general-app-settings-old-integrations.gif "rs_general_app_settings_old_integrations")</span><span class="sxs-lookup"><span data-stu-id="3972b-184">![rs_general_app_settings_old_integrations](media/rs-general-app-settings-old-integrations.gif "rs_general_app_settings_old_integrations")</span></span>  
  
4.  <span data-ttu-id="3972b-185">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="3972b-185">Click **Ok**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3972b-186">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3972b-186">See Also</span></span>  
 <span data-ttu-id="3972b-187">[報表伺服器專案的 SharePoint 網站和清單許可權參考](security/sharepoint-site-and-list-permission-reference-for-report-server-items.md) </span><span class="sxs-lookup"><span data-stu-id="3972b-187">[SharePoint Site and List Permission Reference for Report Server Items](security/sharepoint-site-and-list-permission-reference-for-report-server-items.md) </span></span>  
 [<span data-ttu-id="3972b-188">開始報表產生器 &#40;報表產生器&#41;</span><span class="sxs-lookup"><span data-stu-id="3972b-188">Start Report Builder &#40;Report Builder&#41;</span></span>](report-builder/start-report-builder.md)  
  
  
