---
title: 發行與重新發行報表組件 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 92dce484-f39b-403c-9caf-d8772bc3aca3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 95fd5e3f7519c6a0d4a6f08cb9bcbf2507d32aaa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594384"
---
# <a name="publish-and-republish-report-parts-report-builder-and-ssrs"></a><span data-ttu-id="d8547-102">發行與重新發行報表組件 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="d8547-102">Publish and Republish Report Parts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="d8547-103">您可以使用預設值在預設位置發行報表組件，或者您可以編輯報表組件中繼資料 (例如名稱和描述)，並將其儲存在報表伺服器的其他位置。</span><span class="sxs-lookup"><span data-stu-id="d8547-103">You can publish a report part with default settings in a default location, or you can edit report part metadata such as name and description, and save it somewhere else on a report server.</span></span> <span data-ttu-id="d8547-104">如果您有正確的權限，也可以將其儲存到與報表伺服器整合的 SharePoint 網站。</span><span class="sxs-lookup"><span data-stu-id="d8547-104">You can also save it to a SharePoint site that is integrated with a report server if you have the correct permissions.</span></span>  
  
 <span data-ttu-id="d8547-105">您可以只發行相依之資料集內嵌在其中的報表組件，或者您可以個別發行資料集。</span><span class="sxs-lookup"><span data-stu-id="d8547-105">You can publish just the report part, with the dataset that it depends on embedded in it, or you can publish the dataset separately.</span></span> <span data-ttu-id="d8547-106">如果個別發行資料集，它會變成共用資料集，而且報表組件會連結到該資料集。</span><span class="sxs-lookup"><span data-stu-id="d8547-106">If you publish the dataset separately, it becomes a shared dataset, and the report part links to it.</span></span> <span data-ttu-id="d8547-107">如需詳細資訊，請參閱 [報表產生器中的報表組件和資料集](../report-data/report-parts-and-datasets-in-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="d8547-107">For more information, see [Report Parts and Datasets in Report Builder](../report-data/report-parts-and-datasets-in-report-builder.md).</span></span>  
  
 <span data-ttu-id="d8547-108">您可以重新發行現有的報表組件。</span><span class="sxs-lookup"><span data-stu-id="d8547-108">You can republish an existing report part.</span></span> <span data-ttu-id="d8547-109">如果您有權限，即使您沒有建立報表組件，也可以加以儲存以覆寫伺服器上報表組件的原始執行個體。</span><span class="sxs-lookup"><span data-stu-id="d8547-109">If you have permissions, you can save over the original instance of the report part on the server, even if you didn't create it.</span></span> <span data-ttu-id="d8547-110">您也可以將它發行為新的報表組件，並儲存在相同或不同的位置。</span><span class="sxs-lookup"><span data-stu-id="d8547-110">You can also publish it as a new report part and save it either in the same or a different location.</span></span>  
  
### <a name="to-publish-a-report-part"></a><span data-ttu-id="d8547-111">若要發行報表組件</span><span class="sxs-lookup"><span data-stu-id="d8547-111">To publish a report part</span></span>  
  
1.  <span data-ttu-id="d8547-112">在 [報表產生器] 功能表上，按一下 [發行報表組件]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d8547-112">On the Report Builder menu, click **Publish Report Parts**.</span></span>  
  
     <span data-ttu-id="d8547-113">如果您沒有連接到報表伺服器，系統會提示您連接。</span><span class="sxs-lookup"><span data-stu-id="d8547-113">If you are not connected to a report server, you will be prompted to connect.</span></span> <span data-ttu-id="d8547-114">如果您無法連接到報表伺服器，就無法啊型報表組件。</span><span class="sxs-lookup"><span data-stu-id="d8547-114">If you cannot connect to a report server, you cannot publish report parts.</span></span>  
  
2.  <span data-ttu-id="d8547-115">若要使用預設值將報表組件儲存至預設位置，請按一下 [使用預設值發行所有報表組件]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d8547-115">To save your report parts with default settings to the default location, click **Publish all report parts with default settings**.</span></span>  
  
     <span data-ttu-id="d8547-116">否則，按一下 [發行前檢閱並修改報表組件]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d8547-116">Otherwise, click **Review and modify report parts before publishing**.</span></span>  
  
3.  <span data-ttu-id="d8547-117">編輯報表組件名稱和描述：按兩下名稱可以編輯名稱，而在 [描述]\*\*\*\* 欄位中按一下則可新增描述。</span><span class="sxs-lookup"><span data-stu-id="d8547-117">Edit the report part name and description: Double-click the name to edit it and click in the **Description** field to add a description.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d8547-118">最好提供報表組件名稱和描述，以協助使用者在搜尋時識別它。</span><span class="sxs-lookup"><span data-stu-id="d8547-118">It is a good idea to give the report part name and description, to help people identify it when searching.</span></span> <span data-ttu-id="d8547-119">若是完整路徑，報表組件名稱的最大長度為 260 個字元，包括伺服器上的資料夾名稱，後面接著報表組件的實際名稱。</span><span class="sxs-lookup"><span data-stu-id="d8547-119">The maximum length for the name of a report part is 260 characters for the entire path, including the names of the folders on the server, followed by the actual name of the report part.</span></span>  
  
4.  <span data-ttu-id="d8547-120">若要將報表組件儲存至預設值之外的其他資料夾中，請按一下 [瀏覽]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d8547-120">To save your report part to a folder other than the default, click the **Browse** button.</span></span>  
  
5.  <span data-ttu-id="d8547-121">完成設定報表中所有報表組件的選項時，請按一下 [發行]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d8547-121">When you have set the options for all the report parts in the report, click **Publish**.</span></span>  
  
     <span data-ttu-id="d8547-122">發行報表組件之後，對話方塊會顯示成功發行的報表組件，以及未成功發行的報表組件。</span><span class="sxs-lookup"><span data-stu-id="d8547-122">After you publish the report parts, the dialog box shows which were successfully published and which were not.</span></span> <span data-ttu-id="d8547-123">您可以在 [發行報表組件]\*\*\*\* 對話方塊中，檢視無法發行之報表組件的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="d8547-123">You can view details in the **Publish Report Parts** dialog box for the report parts that failed to publish.</span></span>  
  
6.  <span data-ttu-id="d8547-124">按一下 **關閉**。</span><span class="sxs-lookup"><span data-stu-id="d8547-124">Click **Close**.</span></span>  
  
### <a name="to-republish-a-report-part"></a><span data-ttu-id="d8547-125">重新發行報表組件</span><span class="sxs-lookup"><span data-stu-id="d8547-125">To republish a report part</span></span>  
  
1.  <span data-ttu-id="d8547-126">請遵循先前的程序發行報表組件。</span><span class="sxs-lookup"><span data-stu-id="d8547-126">Follow the previous procedure for publishing a report part.</span></span>  
  
2.  <span data-ttu-id="d8547-127">在 [發行報表組件]\*\*\*\* 對話方塊中，如果您按一下 [發行為報表組件的新複本]\*\*\*\*，報表產生器就不會覆寫伺服器上現有的報表組件，但是會建立另一個報表組件。</span><span class="sxs-lookup"><span data-stu-id="d8547-127">In the **Publish Report Parts** dialog box, if you click **Publish as a New Copy of the Report Part**, Report Builder will not save over the existing report part on the server, but will create another report part instead.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d8547-128">如果您將其發行為新的報表組件，它將會擁有一個新的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="d8547-128">If you publish it as a new report part, it will have a new unique ID.</span></span> <span data-ttu-id="d8547-129">如果原始報表組件變更，它不會再接收更新。</span><span class="sxs-lookup"><span data-stu-id="d8547-129">It will no longer receive updates if the original report part changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8547-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8547-130">See Also</span></span>  
 <span data-ttu-id="d8547-131">[報表元件 &#40;報表產生器和 SSRS&#41;](../report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d8547-131">[Report Parts &#40;Report Builder and SSRS&#41;](../report-parts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d8547-132">[報表產生器中的報表元件和資料集](../report-data/report-parts-and-datasets-in-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="d8547-132">[Report Parts and Datasets in Report Builder](../report-data/report-parts-and-datasets-in-report-builder.md) </span></span>  
 <span data-ttu-id="d8547-133">[&#40;報表產生器和 SSRS&#41;疑難排解報表元件](../troubleshoot-report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d8547-133">[Troubleshoot Report Parts &#40;Report Builder and SSRS&#41;](../troubleshoot-report-parts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="d8547-134">[檢查是否有更新，或關閉 &#40;報表產生器和 SSRS 的更新&#41;](../check-for-updates-or-turn-updates-off-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d8547-134">[Check for Updates or Turn Updates Off &#40;Report Builder and SSRS&#41;](../check-for-updates-or-turn-updates-off-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="d8547-135">瀏覽報表組件及設定預設資料夾 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d8547-135">Browse for Report Parts and Set a Default Folder &#40;Report Builder and SSRS&#41;</span></span>](browse-for-report-parts-and-set-a-default-folder-report-builder-and-ssrs.md)  
  
  
