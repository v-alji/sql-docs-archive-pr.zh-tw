---
title: 報表產生器中的報表組件和資料集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 1fe86481-9c41-4535-a4b7-c7c4d780cab6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6ad592561fa8d1ee7a57bc83eb89d9aec1ba6f6a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710217"
---
# <a name="report-parts-and-datasets-in-report-builder"></a><span data-ttu-id="bc46a-102">報表產生器中的報表組件和資料集</span><span class="sxs-lookup"><span data-stu-id="bc46a-102">Report Parts and Datasets in Report Builder</span></span>
  <span data-ttu-id="bc46a-103">在報表產生器中，在報表內包含資料最簡單的方式，就是從報表組件庫加入報表組件。</span><span class="sxs-lookup"><span data-stu-id="bc46a-103">In Report Builder, the easiest way to include data in a report is to add report parts from the Report Part Gallery.</span></span> <span data-ttu-id="bc46a-104">報表組件包含相依的資料集，稱為 *「相依資料集」* (Dependent Dataset)。</span><span class="sxs-lookup"><span data-stu-id="bc46a-104">Report parts contain the datasets that they depend on, which are known as *dependent datasets*.</span></span> <span data-ttu-id="bc46a-105">相依資料集是以共用資料來源為基礎，而且可以是內嵌資料集或共用資料集。</span><span class="sxs-lookup"><span data-stu-id="bc46a-105">Dependent datasets are based on shared data sources and can be either embedded datasets or shared datasets.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBrptparts](../../includes/ssrbrptparts-md.md)]  
  
 <span data-ttu-id="bc46a-106">在報表內包含資料的另一個方式是使用共用資料集。</span><span class="sxs-lookup"><span data-stu-id="bc46a-106">Another easy way to include data in a report is to use a shared dataset.</span></span> <span data-ttu-id="bc46a-107">如需詳細資訊，請參閱 [報表內嵌資料集和共用資料集 &#40;報表產生器及 SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="bc46a-107">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="adding-a-report-part-with-dependent-datasets-to-your-report"></a><a name="Adding"></a><span data-ttu-id="bc46a-108">將包含相依資料集的報表元件加入至報表</span><span class="sxs-lookup"><span data-stu-id="bc46a-108">Adding a Report Part with Dependent Datasets to Your Report</span></span>  
 <span data-ttu-id="bc46a-109">當您將報表組件加入至報表時，其中包含的相依資料集也會加入到報表中。</span><span class="sxs-lookup"><span data-stu-id="bc46a-109">When you add a report part to your report, the dependent datasets that it contains are also added to your report.</span></span> <span data-ttu-id="bc46a-110">報表組件可能包含其中內含許多其他報表項目的矩形，因此，它可以將多個相依資料集加入至報表中。</span><span class="sxs-lookup"><span data-stu-id="bc46a-110">Because a report part might include a rectangle that contains many other report items, it can add multiple dependent datasets to your report.</span></span> <span data-ttu-id="bc46a-111">每個共用資料集都是一個獨立的參考；其相依的共用資料來源不會加入到您的報表中。</span><span class="sxs-lookup"><span data-stu-id="bc46a-111">Each shared dataset is an independent reference; the shared data source that it depends on is not added to your report.</span></span> <span data-ttu-id="bc46a-112">每個內嵌資料集也會加入相依的內嵌或共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="bc46a-112">Each embedded dataset also adds the embedded or shared data source that it depends on.</span></span>  
  
 <span data-ttu-id="bc46a-113">內嵌資料來源的認證不會儲存為報表組件的一部分。</span><span class="sxs-lookup"><span data-stu-id="bc46a-113">The credentials for an embedded data source are not saved as part of the report part.</span></span> <span data-ttu-id="bc46a-114">如果將內嵌資料來源加入到您的報表，系統會在您執行報表時提示您提供認證。</span><span class="sxs-lookup"><span data-stu-id="bc46a-114">If an embedded data source is added to your report, you will be prompted for credentials when you run the report.</span></span> <span data-ttu-id="bc46a-115">為避免系統提示您提供認證，請搭配預存認證使用以共用資料來源為基礎的報表組件。</span><span class="sxs-lookup"><span data-stu-id="bc46a-115">To avoid being prompted for credentials, use report parts that are based on shared data sources with stored credentials.</span></span>  
  
 <span data-ttu-id="bc46a-116">將報表組件加入至報表之後，加入的資料集就與您建立的內嵌或共用資料集沒什麼不同了。</span><span class="sxs-lookup"><span data-stu-id="bc46a-116">After you add a report part to your report, the added datasets are no different than embedded or shared datasets that you create.</span></span> <span data-ttu-id="bc46a-117">您可以在 [報表資料] 窗格中，檢視額外的資料集。</span><span class="sxs-lookup"><span data-stu-id="bc46a-117">You can view the additional datasets in the Report Data pane.</span></span> <span data-ttu-id="bc46a-118">內嵌資料集會出現在對應的共用資料來源下方，而共用資料集則出現在 [共用資料集] 資料夾的下方。</span><span class="sxs-lookup"><span data-stu-id="bc46a-118">Embedded datasets appear under the corresponding shared data source and shared datasets appear under the Shared Datasets folder.</span></span>  
  
  
##  <a name="customizing-dependent-datasets"></a><a name="Customizing"></a><span data-ttu-id="bc46a-119">自訂相依資料集</span><span class="sxs-lookup"><span data-stu-id="bc46a-119">Customizing Dependent Datasets</span></span>  
 <span data-ttu-id="bc46a-120">將報表組件加入至報表之後，您可以進行預覽，並決定是否要對資料進行一些變更。</span><span class="sxs-lookup"><span data-stu-id="bc46a-120">After you add report parts to your report, you might preview it and decide to make some changes to the data.</span></span> <span data-ttu-id="bc46a-121">您可以變更的內容取決於您要使用的資料集類型。</span><span class="sxs-lookup"><span data-stu-id="bc46a-121">What you can change depends on the type of dataset that you are working with.</span></span>  
  
 <span data-ttu-id="bc46a-122">若要變更內嵌資料集的資料和資料選項，您可以編輯包括查詢在內的資料集屬性，就像您先前自己建立資料集一樣。</span><span class="sxs-lookup"><span data-stu-id="bc46a-122">To change data and data options for an embedded dataset, you can edit the dataset properties, including the query, just as if you had created the dataset yourself.</span></span>  
  
 <span data-ttu-id="bc46a-123">若要變更共用資料集的資料及資料選項，您僅能在您有足夠權限的報表伺服器上，變更共用資料集定義。</span><span class="sxs-lookup"><span data-stu-id="bc46a-123">To change a data and data options for a shared dataset, you can change the shared dataset definition on the report server only you have sufficient permissions.</span></span> <span data-ttu-id="bc46a-124">您也可以在報表中加入篩選、加入導出欄位，以及變更區分大小寫之類的資料選項，藉以自訂共用資料集的執行個體。</span><span class="sxs-lookup"><span data-stu-id="bc46a-124">You can also customize the instance of the shared dataset in your report by adding filters, adding calculated fields, and changing data options such as case sensitivity.</span></span> <span data-ttu-id="bc46a-125">如需詳細資訊，請參閱[內嵌和共用資料集 &#40;報表產生器及 SSRS&#41;](embedded-and-shared-datasets-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="bc46a-125">For more information, see [Embedded and Shared Datasets &#40;Report Builder and SSRS&#41;](embedded-and-shared-datasets-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="bc46a-126">如需如何變更共用資料集定義，或如何顯示報表中共用資料集之最新資料變更的詳細資訊，請參閱[建立共用資料集或內嵌資料集 &#40;報表產生器及 SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) 和[加入、編輯、重新整理報表資料窗格中的欄位 &#40;報表產生器及 SSRS&#41;](add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="bc46a-126">For more information about how to change the definition of a shared dataset or how to show the latest data changes for a shared dataset in your report, see [Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) and [Add, Edit, Refresh Fields in the Report Data Pane &#40;Report Builder and SSRS&#41;](add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs.md).</span></span>  
  
  
##  <a name="publishing-dependent-datasets-as-shared-datasets"></a><a name="Publishing"></a><span data-ttu-id="bc46a-127">將相依資料集發行為共用資料集</span><span class="sxs-lookup"><span data-stu-id="bc46a-127">Publishing Dependent Datasets as Shared Datasets</span></span>  
 <span data-ttu-id="bc46a-128">當您發行包含相依資料集的報表項目時，您可以選擇將每個資料集當做共用資料集發行，或當做仍然內嵌在報表項目中的內嵌資料集發行。</span><span class="sxs-lookup"><span data-stu-id="bc46a-128">When you publish a report item that has dependent datasets, you have the option to publish each dataset as a shared dataset or as an embedded dataset that remains embedded in the report item.</span></span>  
  
 <span data-ttu-id="bc46a-129">當您選取共用資料集選項時，資料集會儲存至報表伺服器，做為共用資料集定義。</span><span class="sxs-lookup"><span data-stu-id="bc46a-129">When you select the shared dataset option, the dataset is saved to the report server as a shared dataset definition.</span></span> <span data-ttu-id="bc46a-130">在您的報表中，使用該資料集的每個報表項目都會進行更新，以指向現在位於報表伺服器上的共用資料集。</span><span class="sxs-lookup"><span data-stu-id="bc46a-130">In your report, every report item that uses that dataset is updated to point to the shared dataset that is now on the report server.</span></span> <span data-ttu-id="bc46a-131">因此會發生兩件事：</span><span class="sxs-lookup"><span data-stu-id="bc46a-131">Two things happen as a result:</span></span>  
  
1.  <span data-ttu-id="bc46a-132">在 [發行] 對話方塊中，已經發行的每個共用資料集都會從可用於發行之項目的清單中移除。</span><span class="sxs-lookup"><span data-stu-id="bc46a-132">In the Publish dialog box, each shared dataset that has been published is removed from the list of items that are available to publish.</span></span>  
  
2.  <span data-ttu-id="bc46a-133">當您結束報表產生器，或啟動新的報表時，系統會提示您儲存報表。</span><span class="sxs-lookup"><span data-stu-id="bc46a-133">When you exit Report Builder or start a new report, you are prompted to save your report.</span></span> <span data-ttu-id="bc46a-134">如果您不儲存報表，下次開啟此報表並發行報表項目時，您可能會發行相同資料集的新複本。</span><span class="sxs-lookup"><span data-stu-id="bc46a-134">If you do not save your report, the next time you open this report and publish report items, you might publish new copies of the same datasets.</span></span> <span data-ttu-id="bc46a-135">為避免將共用資料集的多個複本儲存至報表伺服器，建議您儲存報表。</span><span class="sxs-lookup"><span data-stu-id="bc46a-135">To prevent saving multiple copies of shared datasets to the report server, we recommend that you save the report.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bc46a-136">為確保您和其他人可以繼續成功地使用共用資料集中的資料，您必須了解保護報表項目安全背後的原則。</span><span class="sxs-lookup"><span data-stu-id="bc46a-136">To ensure that you and others can continue to successfully use data from a shared dataset, you must understand the principles behind securing report items.</span></span> <span data-ttu-id="bc46a-137">如需詳細資訊，請參閱 [保護共用資料集項目的安全](../security/secure-shared-dataset-items.md)。</span><span class="sxs-lookup"><span data-stu-id="bc46a-137">For more information, see [Secure Shared Dataset Items](../security/secure-shared-dataset-items.md).</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="bc46a-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc46a-138">See Also</span></span>  
 <span data-ttu-id="bc46a-139">[報表設計檢視 &#40;報表產生器&#41;](../report-builder/report-design-view-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="bc46a-139">[Report Design View &#40;Report Builder&#41;](../report-builder/report-design-view-report-builder.md) </span></span>  
 <span data-ttu-id="bc46a-140">[安全性 &#40;報表產生器&#41;](../report-builder/security-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="bc46a-140">[Security &#40;Report Builder&#41;](../report-builder/security-report-builder.md) </span></span>  
 <span data-ttu-id="bc46a-141">[報表元件 &#40;報表產生器和 SSRS&#41;](../report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="bc46a-141">[Report Parts &#40;Report Builder and SSRS&#41;](../report-parts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="bc46a-142">報表內嵌資料集和共用資料集 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="bc46a-142">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
  
  
