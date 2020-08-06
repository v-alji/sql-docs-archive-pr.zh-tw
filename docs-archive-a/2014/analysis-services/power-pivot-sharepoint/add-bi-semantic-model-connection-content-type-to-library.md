---
title: 將 BI 語義模型連接內容類型新增至程式庫 (PowerPivot for SharePoint) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 145505ed-50bc-4528-912b-2a5cd2566011
author: minewiskan
ms.author: owend
ms.openlocfilehash: ecd40193b382aa692beeadd55ab8f9388c328620
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599222"
---
# <a name="add-a-bi-semantic-model-connection-content-type-to-a-library-powerpivot-for-sharepoint"></a><span data-ttu-id="18986-102">將 BI 語意模型連接內容類型加入至文件庫 (PowerPivot for SharePoint)</span><span class="sxs-lookup"><span data-stu-id="18986-102">Add a BI Semantic Model Connection Content Type to a Library (PowerPivot for SharePoint)</span></span>
  <span data-ttu-id="18986-103">BI 語意模型連接是在 SharePoint 中所建立，它會重新導向至網路伺服器上 PowerPivot 活頁簿或 Analysis Services 表格式模型資料庫內的商業智慧語意模型資料。</span><span class="sxs-lookup"><span data-stu-id="18986-103">A BI semantic model connection is created in SharePoint and provides redirection to business intelligence semantic model data in a PowerPivot workbook or Analysis Services tabular model database on a network server.</span></span> <span data-ttu-id="18986-104">在 SharePoint 中建立 BI 語意模型連接之前，您必須擴充文件庫以允許建立 .bism 檔。</span><span class="sxs-lookup"><span data-stu-id="18986-104">Before you can create a BI semantic model connection in SharePoint, you must extend a document library to allow the creation of a .bism file.</span></span> <span data-ttu-id="18986-105">針對每個文件庫，僅需要執行一次這個步驟，但是您將需要針對您要建立 .bism 檔的任何來源文件庫重複該步驟。</span><span class="sxs-lookup"><span data-stu-id="18986-105">This step only needs to be performed once for each library, but you will need to repeat it for any library from which you want to create .bism files.</span></span> <span data-ttu-id="18986-106">最佳做法建議您建立集中式文件庫來儲存 .bism 檔，讓您可以在一個地方管理權限。</span><span class="sxs-lookup"><span data-stu-id="18986-106">Best practices recommend that you create a centralized library for storing .bism files so that you can manage permissions in one place.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="18986-107">如果您已經使用 SharePoint 資料連線庫，則會將 BI 語意模型連接內容類型自動加入至該連線庫範本。</span><span class="sxs-lookup"><span data-stu-id="18986-107">If you already use SharePoint Data Connection Libraries, the BI Semantic Model Connection content type is automatically added to that library template.</span></span> <span data-ttu-id="18986-108">如果您使用已經讓您建立新 BI 語意模型連接文件的資料連線庫，可以略過本節中的步驟。</span><span class="sxs-lookup"><span data-stu-id="18986-108">You can skip the steps in this section if you use a data connection library that already lets you create new BI semantic model connection documents.</span></span>  
  
##  <a name="add-the-content-type-to-a-document-library"></a><a name="bkmk_addtype"></a> <span data-ttu-id="18986-109">將內容類型加入至文件庫</span><span class="sxs-lookup"><span data-stu-id="18986-109">Add the content type to a document library</span></span>  
 <span data-ttu-id="18986-110">您必須至少有「管理清單」權限，才能加入並設定內容類型。</span><span class="sxs-lookup"><span data-stu-id="18986-110">You must have at least the Manage Lists permission to add and configure a content type.</span></span> <span data-ttu-id="18986-111">此權限內建在「設計」權限等級以上 (含)。</span><span class="sxs-lookup"><span data-stu-id="18986-111">This permission is built into the Design permission level and above.</span></span>  
  
 <span data-ttu-id="18986-112">包含文件庫的網站必須啟用 PowerPivot for SharePoint 的功能。</span><span class="sxs-lookup"><span data-stu-id="18986-112">The site that contains the document library must have feature activation for PowerPivot for SharePoint.</span></span> <span data-ttu-id="18986-113">如需詳細資訊，請參閱為[管理中心的網站集合啟用 PowerPivot 功能整合](activate-power-pivot-integration-for-site-collections-in-ca.md)。</span><span class="sxs-lookup"><span data-stu-id="18986-113">For more information, see [Activate PowerPivot Feature Integration for Site Collections in Central Administration](activate-power-pivot-integration-for-site-collections-in-ca.md).</span></span>  
  
1.  <span data-ttu-id="18986-114">開啟要啟用 BI 語意模型連接內容類型的文件庫。</span><span class="sxs-lookup"><span data-stu-id="18986-114">Open the document library for which you want to enable the BI Semantic Model Connection content type.</span></span>  
  
2.  <span data-ttu-id="18986-115">在 SharePoint 功能區的 [文件庫工具] 中，按一下 **[文件庫]**。</span><span class="sxs-lookup"><span data-stu-id="18986-115">On the SharePoint ribbon, in Library Tools, click **Library**.</span></span>  
  
3.  <span data-ttu-id="18986-116">按一下 **[文件庫設定]**。</span><span class="sxs-lookup"><span data-stu-id="18986-116">Click **Library Settings**.</span></span>  
  
4.  <span data-ttu-id="18986-117">按一下 [一般設定] 中的 **[進階設定]**。</span><span class="sxs-lookup"><span data-stu-id="18986-117">In General Settings, click **Advanced settings**.</span></span>  
  
5.  <span data-ttu-id="18986-118">在 [內容類型] 的 [是否允許內容類型的管理?]</span><span class="sxs-lookup"><span data-stu-id="18986-118">In Content Types, in the "Allow management of content types?"</span></span> <span data-ttu-id="18986-119">區段中按一下 **[是]**。</span><span class="sxs-lookup"><span data-stu-id="18986-119">section, click **Yes**.</span></span>  
  
6.  <span data-ttu-id="18986-120">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="18986-120">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="18986-121">在 [內容類型] 區段中，按一下 **[從現有的網站內容類型新增]**。</span><span class="sxs-lookup"><span data-stu-id="18986-121">In the Content Types section, click **Add from existing site content types**.</span></span> <span data-ttu-id="18986-122">如果您看不到此頁面，請回到網站中，按一下文件庫工具中的 **[文件庫]** ，然後按一下 **[文件庫設定]**。</span><span class="sxs-lookup"><span data-stu-id="18986-122">If you do not see this page, go back to the site, click **Library** in Library Tools, and then click **Library Settings**.</span></span>  
  
8.  <span data-ttu-id="18986-123">在 [內容類型] 中，按一下 **[從現有的網站內容類型新增]**。</span><span class="sxs-lookup"><span data-stu-id="18986-123">In Content Types, click **Add from existing site content types**.</span></span>  
  
9. <span data-ttu-id="18986-124">在 [從下列位置選取網站內容類型:] 中，選取 **[商業智慧]**。</span><span class="sxs-lookup"><span data-stu-id="18986-124">In Select site content types from:, select **Business Intelligence**.</span></span>  
  
10. <span data-ttu-id="18986-125">在 [可用的網站內容類型] 中，按一下 **[BI 語意模型連接檔案]**，然後按一下 **[加入]** ，將所選取的內容類型移到 [要新增的內容類型] 清單中。</span><span class="sxs-lookup"><span data-stu-id="18986-125">In Available Site Content Types, click **BI Semantic Model Connection File**, and then click **Add** to move the selected content type to the Content types to add list.</span></span>  
  
11. <span data-ttu-id="18986-126">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="18986-126">Click **OK**.</span></span>  
  
12. <span data-ttu-id="18986-127">若要驗證您是否加入此內容類型，請回到文件庫，然後在文件庫功能區的文件區域上按一下 **[新文件]** 。</span><span class="sxs-lookup"><span data-stu-id="18986-127">To verify you added the content type, go back to the library and click **New Document** on the Documents area of the library ribbon.</span></span> <span data-ttu-id="18986-128">您應該會在 [新文件] 清單中看到 **[BI 語意模型連接檔案]** 。</span><span class="sxs-lookup"><span data-stu-id="18986-128">You should see **BI Semantic Model Connection File** in the New Documents list.</span></span>  
  
     <span data-ttu-id="18986-129">![SharePoint 文件庫中的新文件子功能表](../media/ssas-bismconnection-new.gif "SharePoint 文件庫中的新文件子功能表")</span><span class="sxs-lookup"><span data-stu-id="18986-129">![New Document submenu in a SharePoint library](../media/ssas-bismconnection-new.gif "New Document submenu in a SharePoint library")</span></span>  
  
 <span data-ttu-id="18986-130">在您為文件庫啟用 BI 語意模型連接內容類型之後，您可以建立連接來重新導向至可由 Excel 或 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 報表使用的商業語意模型資料。</span><span class="sxs-lookup"><span data-stu-id="18986-130">After you enable the BI semantic model connection content type for a library, you can create a connection that provides redirection to business semantic model data that can be used by Excel or [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] reports.</span></span> <span data-ttu-id="18986-131">從下列連結進行選擇，以深入了解下一個步驟：</span><span class="sxs-lookup"><span data-stu-id="18986-131">Choose from the following links to learn more about this next step:</span></span>  
  
 [<span data-ttu-id="18986-132">建立與 PowerPivot 活頁簿的 BI 語意模型連接</span><span class="sxs-lookup"><span data-stu-id="18986-132">Create a BI Semantic Model Connection to a PowerPivot Workbook</span></span>](create-a-bi-semantic-model-connection-to-a-power-pivot-workbook.md)  
  
 [<span data-ttu-id="18986-133">建立與表格式模型資料庫的 BI 語義模型連接</span><span class="sxs-lookup"><span data-stu-id="18986-133">Create a BI Semantic Model Connection to a Tabular Model Database</span></span>](create-a-bi-semantic-model-connection-to-a-tabular-model-database.md)  
  
## <a name="see-also"></a><span data-ttu-id="18986-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18986-134">See Also</span></span>  
 <span data-ttu-id="18986-135">[PowerPivot BI 語義模型連接 &#40;. bism&#41;](power-pivot-bi-semantic-model-connection-bism.md) </span><span class="sxs-lookup"><span data-stu-id="18986-135">[PowerPivot BI Semantic Model Connection &#40;.bism&#41;](power-pivot-bi-semantic-model-connection-bism.md) </span></span>  
 [<span data-ttu-id="18986-136">在 Excel 或 Reporting Services 使用 BI 語意模型連接</span><span class="sxs-lookup"><span data-stu-id="18986-136">Use a BI Semantic Model Connection in Excel or Reporting Services</span></span>](use-a-bi-semantic-model-connection-in-excel-or-reporting-services.md)  
  
  
