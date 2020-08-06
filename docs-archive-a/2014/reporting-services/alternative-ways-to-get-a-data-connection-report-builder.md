---
title: 取得資料連線的替代方式 (報表產生器) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: aebc5f3d-97d5-4d54-b525-753fed073a9a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2be693469318172b2a55fbcb17b33e1deaaed3df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592545"
---
# <a name="alternative-ways-to-get-a-data-connection-report-builder"></a><span data-ttu-id="f39a3-102">取得資料連接的替代方式 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="f39a3-102">Alternative Ways to Get a Data Connection (Report Builder)</span></span>
  <span data-ttu-id="f39a3-103">資料連接包含連接至外部資料來源的資訊，例如 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="f39a3-103">A data connection contains the information to connect to an external data source such as a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="f39a3-104">通常您會向資料來源擁有者取得連接資訊以及要使用的認證類型。</span><span class="sxs-lookup"><span data-stu-id="f39a3-104">Usually, you get the connection information and the type of credentials to use from the data source owner.</span></span>  
  
 <span data-ttu-id="f39a3-105">若要指定資料連接，您可以使用來自報表伺服器的共用資料來源，或是建立僅在特定報表中使用的內嵌資料來源。</span><span class="sxs-lookup"><span data-stu-id="f39a3-105">To specify a data connection, you can use a shared data source from the report server or create an embedded data source that is used only in a specific report.</span></span>  
  
 <span data-ttu-id="f39a3-106">大部分的教學課程都是使用內嵌資料來源，但如果您具有共用資料來源的存取權，就可以改用後者這種資料來源。</span><span class="sxs-lookup"><span data-stu-id="f39a3-106">In most tutorials you use embedded data sources, but if you have access to shared data sources, then you can use them instead.</span></span>  
  
## <a name="getting-a-data-connection-from-a-shared-data-source"></a><span data-ttu-id="f39a3-107">從共用資料來源取得資料連接</span><span class="sxs-lookup"><span data-stu-id="f39a3-107">Getting a Data Connection From a Shared Data Source</span></span>  
 <span data-ttu-id="f39a3-108">如果您有權限使用報表伺服器中可用的共用資料來源，則可以使用共用資料來源，而不使用內嵌資料來源。</span><span class="sxs-lookup"><span data-stu-id="f39a3-108">If the report server has available shared data source that you have permissions to use, you can use them instead of an embedded data source.</span></span> <span data-ttu-id="f39a3-109">下列程序說明如何尋找共用資料來源，並提供使用共用資料來源所需的任何認證。</span><span class="sxs-lookup"><span data-stu-id="f39a3-109">The following procedures tell how to locate the shared data sources and provide any credentials needed to use them.</span></span>  
  
 <span data-ttu-id="f39a3-110">若要使用共用資料來源，您必須瀏覽至報表伺服器，並選取一個共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="f39a3-110">To use a shared data source, you must browse to a report server and select one.</span></span> <span data-ttu-id="f39a3-111">通常您可向報表伺服器管理員取得報表伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="f39a3-111">Usually, you get the report server URL from the report server administrator.</span></span>  
  
#### <a name="to-specify-a-data-connection-from-a-list-of-shared-data-sources"></a><span data-ttu-id="f39a3-112">從共用資料來源清單指定資料連接</span><span class="sxs-lookup"><span data-stu-id="f39a3-112">To specify a data connection from a list of shared data sources</span></span>  
  
1.  <span data-ttu-id="f39a3-113">在 **[選擇資料集]** 頁面上，選取 **[建立資料集]**，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="f39a3-113">On the **Choose a dataset** page, select **Create a dataset**, and then click **Next**.</span></span> <span data-ttu-id="f39a3-114">**[選擇與資料來源的連接]** 頁面隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="f39a3-114">The **Choose a connection to a data source** page opens.</span></span>  
  
2.  <span data-ttu-id="f39a3-115">從資料來源清單中，選取您有權存取的資料來源。</span><span class="sxs-lookup"><span data-stu-id="f39a3-115">From the list of data sources, select a data source that you have permission to access.</span></span>  
  
3.  <span data-ttu-id="f39a3-116">若要確認您能夠連接至資料來源，請按一下 **[測試連接]** 。</span><span class="sxs-lookup"><span data-stu-id="f39a3-116">To verify that you can connect to the data source, click **Test Connection**.</span></span> <span data-ttu-id="f39a3-117">「成功建立連接」訊息就會出現。</span><span class="sxs-lookup"><span data-stu-id="f39a3-117">The message "Connection created successfully" appears.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
4.  <span data-ttu-id="f39a3-118">按 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="f39a3-118">Click **Next**.</span></span>  
  
     <span data-ttu-id="f39a3-119">如有需要，請輸入您的認證。</span><span class="sxs-lookup"><span data-stu-id="f39a3-119">If necessary, enter your credentials.</span></span> <span data-ttu-id="f39a3-120">若要在本機儲存認證，請選取 [儲存連接的密碼]  。</span><span class="sxs-lookup"><span data-stu-id="f39a3-120">To save the credentials locally, select **Save password with connection**.</span></span> <span data-ttu-id="f39a3-121">如果您未選取此選項，則會在每次執行報表時提示您提供認證</span><span class="sxs-lookup"><span data-stu-id="f39a3-121">If you not select this option, you will be prompted for credentials every time that you run the report</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-specify-a-data-connection-by-browsing-to-a-shared-data-source-on-a-report-server"></a><span data-ttu-id="f39a3-122">透過瀏覽報表伺服器上共用資料來源的方式指定資料連接</span><span class="sxs-lookup"><span data-stu-id="f39a3-122">To specify a data connection by browsing to a shared data source on a report server</span></span>  
  
1.  <span data-ttu-id="f39a3-123">在 **[選擇資料集]** 頁面上，選取 **[建立資料集]**，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="f39a3-123">On the **Choose a dataset** page, select **Create a dataset**, and then click **Next**.</span></span> <span data-ttu-id="f39a3-124">**[選擇與資料來源的連接]** 頁面隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="f39a3-124">The **Choose a connection to a data source** page opens.</span></span>  
  
2.  <span data-ttu-id="f39a3-125">按一下 **[瀏覽]** 。</span><span class="sxs-lookup"><span data-stu-id="f39a3-125">Click **Browse**.</span></span> <span data-ttu-id="f39a3-126">[選取資料來源]  對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="f39a3-126">The **Select Data Source** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="f39a3-127">從 [查詢]  下拉式清單中，選取 [最近使用的網站和伺服器]  。</span><span class="sxs-lookup"><span data-stu-id="f39a3-127">From the **Look in** drop-down list, select **Recent Sites and Servers**.</span></span> <span data-ttu-id="f39a3-128">在資料來源窗格中，按一下伺服器的 URL，然後按一下 [開啟]  。</span><span class="sxs-lookup"><span data-stu-id="f39a3-128">In the data source pane, click the URL for your server, and then click **Open**.</span></span>  
  
     <span data-ttu-id="f39a3-129">資料來源或模型的清單隨即出現。</span><span class="sxs-lookup"><span data-stu-id="f39a3-129">The list of data sources or models appears.</span></span>  
  
4.  <span data-ttu-id="f39a3-130">或者，在 [名稱]  中輸入報表伺服器的 URL。</span><span class="sxs-lookup"><span data-stu-id="f39a3-130">Alternatively, in **Name**, type the URL to the report server.</span></span> <span data-ttu-id="f39a3-131">按一下 **[開啟]** 。</span><span class="sxs-lookup"><span data-stu-id="f39a3-131">Click **Open**.</span></span>  
  
     <span data-ttu-id="f39a3-132">報表產生器會連接到報表伺服器，並且在根資料夾中載入可用的資料來源。</span><span class="sxs-lookup"><span data-stu-id="f39a3-132">Report Builder connects to the report server and loads the data sources that are available at the root folder.</span></span>  
  
5.  <span data-ttu-id="f39a3-133">巡覽至包含您有足夠權限可連線之資料來源的資料夾，選取該資料來源，然後按一下 [開啟]  。</span><span class="sxs-lookup"><span data-stu-id="f39a3-133">Navigate to a folder that contains a data source that you have sufficient permissions to connect to, select the data source, and then click **Open**.</span></span>  
  
     <span data-ttu-id="f39a3-134">您會回到 [選擇與資料來源的連線]  頁面。</span><span class="sxs-lookup"><span data-stu-id="f39a3-134">You are back on the **Choose a connection to a data source** page.</span></span>  
  
6.  <span data-ttu-id="f39a3-135">若要確認您能夠連接至資料來源，請按一下 **[測試連接]** 。</span><span class="sxs-lookup"><span data-stu-id="f39a3-135">To verify that you can connect to the data source, click **Test Connection**.</span></span>  
  
     <span data-ttu-id="f39a3-136">「成功建立連接」訊息就會出現。</span><span class="sxs-lookup"><span data-stu-id="f39a3-136">The message "Connection created successfully" appears.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="f39a3-137">按 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="f39a3-137">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="f39a3-138">如果提示您提供使用者名稱和密碼，請輸入您的認證。</span><span class="sxs-lookup"><span data-stu-id="f39a3-138">If you are prompted for a user name and password, enter your credentials.</span></span> <span data-ttu-id="f39a3-139">若要在本機儲存認證，請選取 [儲存連接的密碼]  。</span><span class="sxs-lookup"><span data-stu-id="f39a3-139">To save the credentials locally, select **Save password with connection**.</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f39a3-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f39a3-140">See Also</span></span>  
 <span data-ttu-id="f39a3-141">[將資料加入報表 &#40;報表產生器和 SSRS&#41;](report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="f39a3-141">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-data/report-datasets-ssrs.md) </span></span>  
 [<span data-ttu-id="f39a3-142">教學課程 &#40;報表產生器&#41;</span><span class="sxs-lookup"><span data-stu-id="f39a3-142">Tutorials &#40;Report Builder&#41;</span></span>](report-builder-tutorials.md)  
  
  
