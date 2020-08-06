---
title: 建立或自訂資料摘要庫 (PowerPivot for SharePoint) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data feed library
- data feeds [Analysis Services with SharePoint]
ms.assetid: 699fbeb9-42ab-436b-beba-214db51ea3dd
author: minewiskan
ms.author: owend
ms.openlocfilehash: b86f63c1af094ea9e8a2a1149debeac387bccbf0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698581"
---
# <a name="create-or-customize-a-data-feed-library-powerpivot-for-sharepoint"></a><span data-ttu-id="747cc-102">建立或自訂資料摘要庫 (PowerPivot for SharePoint)</span><span class="sxs-lookup"><span data-stu-id="747cc-102">Create or Customize a Data Feed Library (PowerPivot for SharePoint)</span></span>
  <span data-ttu-id="747cc-103">*「資料摘要庫」* (Data Feed Library) 是一種特殊用途的 SharePoint 文件庫，可讓您註冊與共用 Atom 資料服務文件 (.atomsvc)。</span><span class="sxs-lookup"><span data-stu-id="747cc-103">A *data feed library* is a special-purpose SharePoint library that enables you to register and share Atom data service documents (.atomsvc).</span></span> <span data-ttu-id="747cc-104">這些文件會提供 XML 資料摘要給支援 Atom 資料摘要格式的 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 活頁簿或其他用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="747cc-104">These documents provide XML data feeds to [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] workbooks or other client applications that support the Atom data feed format.</span></span> <span data-ttu-id="747cc-105">資料摘要庫與其他 SharePoint 文件庫不同，因為它讓您能夠：</span><span class="sxs-lookup"><span data-stu-id="747cc-105">A data feed library is different from other SharePoint libraries because it gives you the ability to:</span></span>

-   <span data-ttu-id="747cc-106">建立或編輯 *「資料服務文件」*(Data service document)，用來指定特定摘要的 HTTP 連接。</span><span class="sxs-lookup"><span data-stu-id="747cc-106">Create or edit a *data service document*, used to specify an HTTP connection to a specific feed.</span></span>

-   <span data-ttu-id="747cc-107">在中央位置共用及管理資料服務文件。</span><span class="sxs-lookup"><span data-stu-id="747cc-107">Share and manage data service documents in a central location.</span></span>

-   <span data-ttu-id="747cc-108">以圖示以視覺化方式識別資料服務檔，讓您可以輕鬆地區別服務檔與儲存在相同文件庫中的其他檔： ![GMNI_IconDataFeed](../media/gmni-icondatafeed.gif "GMNI_IconDataFeed")</span><span class="sxs-lookup"><span data-stu-id="747cc-108">Visually identify data service documents by an icon, so that you can easily distinguish service documents from other documents stored in the same library: ![GMNI_IconDataFeed](../media/gmni-icondatafeed.gif "GMNI_IconDataFeed")</span></span>

 <span data-ttu-id="747cc-109">資料摘要庫一直都是包含資料服務文件 (.atomsvc) 檔案，而從來都不包含資料摘要本身。</span><span class="sxs-lookup"><span data-stu-id="747cc-109">A data feed library always contains data service document (.atomsvc) files, and never the data feed itself.</span></span> <span data-ttu-id="747cc-110">資料服務文件與包含靜態 XML 資料的資料摘要不同，它會指定 URL 給接到要求時會產生摘要的服務或應用程式，為可重複的匯入作業提供可重複使用的連接資訊。</span><span class="sxs-lookup"><span data-stu-id="747cc-110">Unlike a data feed, which consists of static XML data, the data service document specifies a URL to a service or application that generates a feed upon request, providing reusable connection information for repeatable import operations.</span></span>

 <span data-ttu-id="747cc-111">本主題包含下列幾節：</span><span class="sxs-lookup"><span data-stu-id="747cc-111">This topic contains the following sections:</span></span>

 [<span data-ttu-id="747cc-112">先決條件</span><span class="sxs-lookup"><span data-stu-id="747cc-112">Prerequisites</span></span>](#prereq)

 [<span data-ttu-id="747cc-113">建立新的資料摘要庫</span><span class="sxs-lookup"><span data-stu-id="747cc-113">Create a New Data Feed Library</span></span>](#createlib)

 [<span data-ttu-id="747cc-114">將資料摘要庫內容類型加入至任何文件庫</span><span class="sxs-lookup"><span data-stu-id="747cc-114">Add the Data Feed Content Type to Any Library</span></span>](#addtolib)

##  <a name="prerequisites"></a><a name="prereq"></a> <span data-ttu-id="747cc-115">必要條件</span><span class="sxs-lookup"><span data-stu-id="747cc-115">Prerequisites</span></span>
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] <span data-ttu-id="747cc-116">功能整合必須針對您要建立其資料摘要庫的網站啟用。</span><span class="sxs-lookup"><span data-stu-id="747cc-116">feature integration must be activated for the sites for which you are creating the data feed library.</span></span> <span data-ttu-id="747cc-117">如果無法使用資料摘要庫範本類型，最可能的原因是不符合這項先決條件。</span><span class="sxs-lookup"><span data-stu-id="747cc-117">If the data feed library template type is not available, the most likely cause is that this prerequisite has not been met.</span></span> <span data-ttu-id="747cc-118">如需詳細資訊，請參閱為[管理中心的網站集合啟用 PowerPivot 功能整合](activate-power-pivot-integration-for-site-collections-in-ca.md)。</span><span class="sxs-lookup"><span data-stu-id="747cc-118">For more information, see [Activate PowerPivot Feature Integration for Site Collections in Central Administration](activate-power-pivot-integration-for-site-collections-in-ca.md).</span></span>

 <span data-ttu-id="747cc-119">您必須是網站擁有者，才能建立該文件庫。</span><span class="sxs-lookup"><span data-stu-id="747cc-119">You must be a site owner to create the library.</span></span>

##  <a name="create-a-new-data-feed-library"></a><a name="createlib"></a><span data-ttu-id="747cc-120">建立新的資料摘要庫</span><span class="sxs-lookup"><span data-stu-id="747cc-120">Create a New Data Feed Library</span></span>
 <span data-ttu-id="747cc-121">建立資料摘要庫是為 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 活頁簿啟用資料摘要的第一個步驟。</span><span class="sxs-lookup"><span data-stu-id="747cc-121">Creating a data feed library is the first step to enabling data feeds for [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] workbooks.</span></span> <span data-ttu-id="747cc-122">資料摘要庫會提供資料服務文件的應用程式和管理頁面，因此您必須先將此摘要庫準備就緒，才能建立新文件。</span><span class="sxs-lookup"><span data-stu-id="747cc-122">Because a data feed library provides application and management pages for data service documents, you must have this library in place before you can create a new document.</span></span>

 <span data-ttu-id="747cc-123">資料摘要庫的根據是內建範本與預先設定的 *「資料服務文件內容類型」* (Data service document content type)，此類型定義資料服務文件的屬性和行為。</span><span class="sxs-lookup"><span data-stu-id="747cc-123">A data feed library is based on a built-in template and a preconfigured *data service document content type* that defines properties and behaviors for a data service document.</span></span>

1.  <span data-ttu-id="747cc-124">按一下頁面左上角的 [網站動作]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="747cc-124">Click **Site Actions** at the top left corner of the page.</span></span>

2.  <span data-ttu-id="747cc-125">按一下 [**更多選項**]</span><span class="sxs-lookup"><span data-stu-id="747cc-125">Click **More Options**...</span></span>

3.  <span data-ttu-id="747cc-126">按一下文件庫之下的 [資料摘要庫]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="747cc-126">Under Libraries, click **Data Feed Library**.</span></span>

4.  <span data-ttu-id="747cc-127">輸入名稱、描述、啟動及版本喜好設定。</span><span class="sxs-lookup"><span data-stu-id="747cc-127">Type the name, description, launch, and version preferences.</span></span> <span data-ttu-id="747cc-128">加入描述性資訊，以協助使用者將這個文件庫識別為資料服務文件的儲存位置。</span><span class="sxs-lookup"><span data-stu-id="747cc-128">Include descriptive information to help users identify this library as storage for data service documents.</span></span>

5.  <span data-ttu-id="747cc-129">按一下 [建立]。</span><span class="sxs-lookup"><span data-stu-id="747cc-129">Click **Create**.</span></span>

 <span data-ttu-id="747cc-130">資料摘要庫的連結會出現在目前網站的導覽 [快速啟動] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="747cc-130">A link to the data feed library will appear in the navigation Quick Launch pane for the current site.</span></span>

 <span data-ttu-id="747cc-131">建立文件庫之後，您可以使用它來建立資料服務文件。</span><span class="sxs-lookup"><span data-stu-id="747cc-131">After you create a library, you can use it to create data service documents.</span></span> <span data-ttu-id="747cc-132">如需詳細資訊，請參閱[使用資料摘要 &#40;PowerPivot for SharePoint&#41;](use-data-feeds-power-pivot-for-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="747cc-132">For more information, see [Use Data Feeds &#40;PowerPivot for SharePoint&#41;](use-data-feeds-power-pivot-for-sharepoint.md).</span></span>

##  <a name="add-the-data-feed-content-type-to-any-library"></a><a name="addtolib"></a><span data-ttu-id="747cc-133">將資料摘要內容類型新增至任何程式庫</span><span class="sxs-lookup"><span data-stu-id="747cc-133">Add the Data Feed Content Type to Any Library</span></span>
 <span data-ttu-id="747cc-134">如果您不要建立專用的資料摘要庫，但仍要從 SharePoint 網站建立及管理資料服務文件，則可以手動方式為要用來共用資料服務文件 (.atomsvc) 檔案的任何文件庫，加入並設定資料服務文件內容類型。</span><span class="sxs-lookup"><span data-stu-id="747cc-134">If you do not want to create a dedicated data feed library, but you still want to create and manage data service documents from a SharePoint site, you can manually add and configure the data service document content type for any library that you will use to share data service document (.atomsvc) files.</span></span>

 <span data-ttu-id="747cc-135">您必須至少有「管理清單」權限，才能加入並設定內容類型。</span><span class="sxs-lookup"><span data-stu-id="747cc-135">You must have at least the Manage Lists permission to add and configure a content type.</span></span> <span data-ttu-id="747cc-136">此權限內建在「設計」權限等級以上 (含)。</span><span class="sxs-lookup"><span data-stu-id="747cc-136">This permission is built into the Design permission level and above.</span></span>

 <span data-ttu-id="747cc-137">您必須為要建立或編輯資料摘要註冊文件的每個文件庫重複執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="747cc-137">The following steps must be repeated for each library in which you want to create or edit data feed registration documents.</span></span>

#### <a name="step-1-enable-content-type-management"></a><span data-ttu-id="747cc-138">步驟 1：啟用內容類型管理</span><span class="sxs-lookup"><span data-stu-id="747cc-138">Step 1: Enable Content Type Management</span></span>

1.  <span data-ttu-id="747cc-139">開啟要啟用多個內容類型的文件庫。</span><span class="sxs-lookup"><span data-stu-id="747cc-139">Open the document library for which you want to enable multiple content types.</span></span>

2.  <span data-ttu-id="747cc-140">在 SharePoint 功能區的 [文件庫工具] 中，按一下 **[文件庫]**。</span><span class="sxs-lookup"><span data-stu-id="747cc-140">On the SharePoint ribbon, in Library Tools, click **Library**.</span></span>

3.  <span data-ttu-id="747cc-141">按一下 [設定]。</span><span class="sxs-lookup"><span data-stu-id="747cc-141">Click **Settings**.</span></span>

4.  <span data-ttu-id="747cc-142">按一下 **[文件庫設定]**。</span><span class="sxs-lookup"><span data-stu-id="747cc-142">Click **Library Settings**.</span></span>

5.  <span data-ttu-id="747cc-143">按一下 [一般設定] 中的 **[進階設定]**。</span><span class="sxs-lookup"><span data-stu-id="747cc-143">In General Settings, click **Advanced settings**.</span></span>

6.  <span data-ttu-id="747cc-144">在 [內容類型] 的 [是否允許內容類型的管理?]</span><span class="sxs-lookup"><span data-stu-id="747cc-144">In Content Types, in the "Allow management of content types?"</span></span> <span data-ttu-id="747cc-145">區段中按一下 **[是]**。</span><span class="sxs-lookup"><span data-stu-id="747cc-145">section, click **Yes**.</span></span>

7.  <span data-ttu-id="747cc-146">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="747cc-146">Click **OK**.</span></span>

#### <a name="step-2-add-the-data-service-document-content-type"></a><span data-ttu-id="747cc-147">步驟 2：加入資料服務文件內容類型</span><span class="sxs-lookup"><span data-stu-id="747cc-147">Step 2: Add the Data Service Document Content Type</span></span>

1.  <span data-ttu-id="747cc-148">在 [內容類型] 區段中，按一下 **[從現有的網站內容類型新增]**。</span><span class="sxs-lookup"><span data-stu-id="747cc-148">In the Content Types section, click **Add from existing site content types**.</span></span> <span data-ttu-id="747cc-149">如果您看不到此頁面，請回到網站中，按一下文件庫工具中的 **[文件庫]** ，然後按一下 **[文件庫設定]**。</span><span class="sxs-lookup"><span data-stu-id="747cc-149">If you do not see this page, go back to the site, click **Library** in Library Tools, and then click **Library Settings**.</span></span>

2.  <span data-ttu-id="747cc-150">在 [內容類型] 中，按一下 **[從現有的網站內容類型新增]**。</span><span class="sxs-lookup"><span data-stu-id="747cc-150">In Content Types, click **Add from existing site content types**.</span></span>

3.  <span data-ttu-id="747cc-151">在 [從下列位置選取網站內容類型:] 中，選取 **[商業智慧]**。</span><span class="sxs-lookup"><span data-stu-id="747cc-151">In Select site content types from:, select **Business Intelligence**.</span></span>

4.  <span data-ttu-id="747cc-152">在 [可用的網站內容類型] 中，按一下 [資料服務文件]\*\*\*\*，然後按一下 [加入]\*\*\*\*，將所選取的內容類型移到 [要新增的內容類型] 清單中。</span><span class="sxs-lookup"><span data-stu-id="747cc-152">In Available Site Content Types, click **Data Service Document**, and then click **Add** to move the selected content type to the Content types to add list.</span></span>

5.  <span data-ttu-id="747cc-153">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="747cc-153">Click **OK**.</span></span>

#### <a name="step-3-verify-data-service-document-configuration"></a><span data-ttu-id="747cc-154">步驟 3：確認資料服務文件設定</span><span class="sxs-lookup"><span data-stu-id="747cc-154">Step 3: Verify Data Service Document Configuration</span></span>

1.  <span data-ttu-id="747cc-155">開啟網站首頁。</span><span class="sxs-lookup"><span data-stu-id="747cc-155">Open the site home page.</span></span>

2.  <span data-ttu-id="747cc-156">開啟文件庫。</span><span class="sxs-lookup"><span data-stu-id="747cc-156">Open the library.</span></span>

3.  <span data-ttu-id="747cc-157">在 SharePoint 功能區上，按一下 [文件]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="747cc-157">On the SharePoint ribbon, click **Documents**.</span></span>

4.  <span data-ttu-id="747cc-158">按一下 [新文件] 上的向下箭號，然後選取 [資料服務文件]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="747cc-158">Click the down arrow on New Document, and select **Data Service Document**.</span></span> <span data-ttu-id="747cc-159">[新資料服務文件] 頁面應該會出現。</span><span class="sxs-lookup"><span data-stu-id="747cc-159">The New Data Service Document page should appear.</span></span>

## <a name="see-also"></a><span data-ttu-id="747cc-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="747cc-160">See Also</span></span>
 <span data-ttu-id="747cc-161">[使用資料摘要 &#40;PowerPivot for SharePoint&#41;](use-data-feeds-power-pivot-for-sharepoint.md)在管理中心[powerpivot 資料](power-pivot-data-feeds.md)摘要中[刪除 Powerpivot 資料摘要庫](delete-a-power-pivot-data-feed-library.md) [powerpivot 伺服器管理和](power-pivot-server-administration-and-configuration-in-central-administration.md)設定</span><span class="sxs-lookup"><span data-stu-id="747cc-161">[Use Data Feeds &#40;PowerPivot for SharePoint&#41;](use-data-feeds-power-pivot-for-sharepoint.md) [Delete a PowerPivot Data Feed Library](delete-a-power-pivot-data-feed-library.md) [PowerPivot Server Administration and Configuration in Central Administration](power-pivot-server-administration-and-configuration-in-central-administration.md) [PowerPivot Data Feeds](power-pivot-data-feeds.md)</span></span>


