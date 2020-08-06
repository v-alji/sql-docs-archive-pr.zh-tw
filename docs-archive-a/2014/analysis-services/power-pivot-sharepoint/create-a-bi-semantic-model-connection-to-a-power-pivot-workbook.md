---
title: 建立與 PowerPivot 活頁簿的 BI 語義模型連接 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b2e3f97f-18a8-42b6-9030-b4f818afc3b9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7ea4ddcc38328acc6ff8cfb5387b13056b689a24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598580"
---
# <a name="create-a-bi-semantic-model-connection-to-a-powerpivot-workbook"></a><span data-ttu-id="2ac73-102">建立與 PowerPivot 活頁簿的 BI 語意模型連接</span><span class="sxs-lookup"><span data-stu-id="2ac73-102">Create a BI Semantic Model Connection to a PowerPivot Workbook</span></span>
  <span data-ttu-id="2ac73-103">使用本主題中的資訊可設定 BI 語意模型連接，該連接會重新導向至相同伺服器陣列中的 PowerPivot 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="2ac73-103">Use the information in this topic to set up a BI semantic model connection that redirects to a PowerPivot workbook in the same farm.</span></span>  
  
 <span data-ttu-id="2ac73-104">在您建立 BI 語意模型連接並且設定 SharePoint 權限之後，可以將其做為 Excel 或 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] 報表的資料來源。</span><span class="sxs-lookup"><span data-stu-id="2ac73-104">After you create a BI semantic model connection and configure SharePoint permissions, you can use it as a data source for Excel or [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] reports.</span></span>  
  
 <span data-ttu-id="2ac73-105">本主題包含下列各節。</span><span class="sxs-lookup"><span data-stu-id="2ac73-105">This topic includes the following sections.</span></span> <span data-ttu-id="2ac73-106">請依指定順序執行每個工作。</span><span class="sxs-lookup"><span data-stu-id="2ac73-106">Perform each task in the order given.</span></span>  
  
 [<span data-ttu-id="2ac73-107">檢閱必要條件</span><span class="sxs-lookup"><span data-stu-id="2ac73-107">Review Prerequisites</span></span>](#bkmk_prereq)  
  
 [<span data-ttu-id="2ac73-108">建立連接</span><span class="sxs-lookup"><span data-stu-id="2ac73-108">Create a Connection</span></span>](#bkmk_create)  
  
 [<span data-ttu-id="2ac73-109">設定 BI 語義模型連接的 SharePoint 許可權</span><span class="sxs-lookup"><span data-stu-id="2ac73-109">Configure SharePoint Permissions on the BI Semantic Model Connection</span></span>](#bkmk_permissions)  
  
 [<span data-ttu-id="2ac73-110">設定活頁簿的 SharePoint 權限</span><span class="sxs-lookup"><span data-stu-id="2ac73-110">Configure SharePoint Permissions on the Workbook</span></span>](#bkmk_userdb)  
  
 [<span data-ttu-id="2ac73-111">後續步驟</span><span class="sxs-lookup"><span data-stu-id="2ac73-111">Next Steps</span></span>](#bkmk_next)  
  
##  <a name="review-prerequisites"></a><a name="bkmk_prereq"></a><span data-ttu-id="2ac73-112">審查必要條件</span><span class="sxs-lookup"><span data-stu-id="2ac73-112">Review Prerequisites</span></span>  
 <span data-ttu-id="2ac73-113">您必須有 [參與] 以上權限，才能建立 BI 語意模型連接檔案。</span><span class="sxs-lookup"><span data-stu-id="2ac73-113">You must have Contribute permissions or above to create a BI semantic model connection file.</span></span>  
  
 <span data-ttu-id="2ac73-114">您必須具有支援 BI 語意模型連接內容類型的文件庫。</span><span class="sxs-lookup"><span data-stu-id="2ac73-114">You must have a library that supports the BI semantic model connection content type.</span></span> <span data-ttu-id="2ac73-115">如需詳細資訊，請參閱[將 BI 語義模型連接內容類型新增至程式庫 &#40;PowerPivot for SharePoint&#41;](add-bi-semantic-model-connection-content-type-to-library.md)。</span><span class="sxs-lookup"><span data-stu-id="2ac73-115">For more information, see [Add a BI Semantic Model Connection Content Type to a Library &#40;PowerPivot for SharePoint&#41;](add-bi-semantic-model-connection-content-type-to-library.md).</span></span>  
  
 <span data-ttu-id="2ac73-116">您必須知道要設定 BI 語義模型連接的 PowerPivot 活頁簿 URL (例如， http://adventure-works/shared documents/myworkbook.xlsx) 。</span><span class="sxs-lookup"><span data-stu-id="2ac73-116">You must know the URL of the PowerPivot workbook for which you are setting up a BI semantic model connection (for example, http://adventure-works/shared documents/myworkbook.xlsx).</span></span> <span data-ttu-id="2ac73-117">活頁簿必須位於相同伺服器陣列中。</span><span class="sxs-lookup"><span data-stu-id="2ac73-117">The workbook must be in the same farm.</span></span>  
  
 <span data-ttu-id="2ac73-118">參與連接順序的所有電腦和使用者都必須是在相同網域或受信任網域 (雙向信任) 中。</span><span class="sxs-lookup"><span data-stu-id="2ac73-118">All computers and users that participate in the connection sequence must be in the same domain or trusted domain (two-way trust).</span></span>  
  
##  <a name="create-a-connection"></a><a name="bkmk_create"></a><span data-ttu-id="2ac73-119">建立連接</span><span class="sxs-lookup"><span data-stu-id="2ac73-119">Create a Connection</span></span>  
  
1.  <span data-ttu-id="2ac73-120">在包含 BI 語意模型連接的文件庫中，按一下 SharePoint 功能區上的 [文件]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2ac73-120">In the library that will contain the BI semantic model connection, click **Documents** on the SharePoint ribbon.</span></span> <span data-ttu-id="2ac73-121">按一下 [新文件] 上的向下箭號，然後選取 [BISM 連接檔案]\*\*\*\* 開啟 [新增 BI 語意模型連接] 頁面。</span><span class="sxs-lookup"><span data-stu-id="2ac73-121">Click the down arrow on New Document, and select **BISM Connection File** to open the New BI Semantic Model Connection page.</span></span>  
  
     <span data-ttu-id="2ac73-122">![SharePoint 文件庫中的新文件子功能表](../media/ssas-bismconnection-new.gif "SharePoint 文件庫中的新文件子功能表")</span><span class="sxs-lookup"><span data-stu-id="2ac73-122">![New Document submenu in a SharePoint library](../media/ssas-bismconnection-new.gif "New Document submenu in a SharePoint library")</span></span>  
  
2.  <span data-ttu-id="2ac73-123">將 [**伺服器**] 屬性設定為 PowerPivot 活頁簿 (的 SharePoint URL，例如\*\* http://mysharepoint/shared documents/myWorkbook.xlsx\*\*。</span><span class="sxs-lookup"><span data-stu-id="2ac73-123">Set the **Server** property to the SharePoint URL of the PowerPivot workbook (for example, **http://mysharepoint/shared documents/myWorkbook.xlsx**.</span></span> <span data-ttu-id="2ac73-124">在 PowerPivot for SharePoint 部署中，可以在伺服器陣列中的任何伺服器上載入資料。</span><span class="sxs-lookup"><span data-stu-id="2ac73-124">In a PowerPivot for SharePoint deployment, data can be loaded on any server in the farm.</span></span> <span data-ttu-id="2ac73-125">因此，資料來源與 PowerPivot 資料的連接只會指定活頁簿的路徑。</span><span class="sxs-lookup"><span data-stu-id="2ac73-125">For this reason, data source connections to PowerPivot data specify just the path to the workbook.</span></span> <span data-ttu-id="2ac73-126">PowerPivot 系統服務會決定載入資料的伺服器。</span><span class="sxs-lookup"><span data-stu-id="2ac73-126">The PowerPivot System Service determines which server loads the data.</span></span>  
  
     <span data-ttu-id="2ac73-127">請勿使用**資料庫**屬性;指定 PowerPivot 活頁簿的位置時，不會使用它。</span><span class="sxs-lookup"><span data-stu-id="2ac73-127">Do not use the **Database** property; it is not used when specifying the location of a PowerPivot workbook.</span></span>  
  
     <span data-ttu-id="2ac73-128">頁面應看起來類似下圖。</span><span class="sxs-lookup"><span data-stu-id="2ac73-128">Your page should look similar to the following illustration.</span></span>  
  
     <span data-ttu-id="2ac73-129">![顯示活頁簿 URL 的 BISM 連接頁面](../media/ssas-bismconnection-ppvtds.gif "顯示活頁簿 URL 的 BISM 連接頁面")</span><span class="sxs-lookup"><span data-stu-id="2ac73-129">![BISM connection page showing URL to workbook](../media/ssas-bismconnection-ppvtds.gif "BISM connection page showing URL to workbook")</span></span>  
  
     <span data-ttu-id="2ac73-130">或者，如果您有活頁簿的 SharePoint 權限，則會執行額外的驗證步驟，以確保該位置有效。</span><span class="sxs-lookup"><span data-stu-id="2ac73-130">Optionally, if you have SharePoint permissions to the workbook, an extra validation step is performed, ensuring that the location is valid.</span></span> <span data-ttu-id="2ac73-131">如果您沒有資料的存取權限，則會提供一個無需驗證回應即儲存 BI 語意模型連接的選項。</span><span class="sxs-lookup"><span data-stu-id="2ac73-131">If you do not have permission to access the data, you are given the option of saving the BI semantic model connection without the validation response.</span></span>  
  
##  <a name="configure-sharepoint-permissions-on-the-bi-semantic-model-connection"></a><a name="bkmk_permissions"></a><span data-ttu-id="2ac73-132">設定 BI 語義模型連接的 SharePoint 許可權</span><span class="sxs-lookup"><span data-stu-id="2ac73-132">Configure SharePoint Permissions on the BI Semantic Model Connection</span></span>  
 <span data-ttu-id="2ac73-133">需要有 SharePoint 文件庫中 BI 語意模型連接項目的 [讀取]\*\*\*\* 權限，才能使用 BI 語意模型連接作為 Excel 活頁簿或 Reporting Services 報表的資料來源。</span><span class="sxs-lookup"><span data-stu-id="2ac73-133">Ability to use a BI semantic model connection as a data source for an Excel workbook or Reporting Services report requires **Read** permissions on the BI semantic model connection item in a SharePoint library.</span></span> <span data-ttu-id="2ac73-134">[讀取] 權限等級包含 [開啟項目]\*\*\*\* 權限，此權限允許將 BI 語意模型連接資訊下載到 Excel 桌面應用程式。</span><span class="sxs-lookup"><span data-stu-id="2ac73-134">The Read permission level includes the **Open Items** permission that enables downloading BI semantic model connection information to an Excel desktop application.</span></span>  
  
 <span data-ttu-id="2ac73-135">有數種方法可以在 SharePoint 中授與權限。</span><span class="sxs-lookup"><span data-stu-id="2ac73-135">There are several ways to grant permissions in SharePoint.</span></span> <span data-ttu-id="2ac73-136">下列指示說明如何建立具有 [讀取]\*\*\*\* 權限等級、稱為「BISM 使用者」\*\*\*\* 的新群組。</span><span class="sxs-lookup"><span data-stu-id="2ac73-136">The following instructions explain how to create a new group called **BISM Users** that have the **Read** permission level.</span></span>  
  
 <span data-ttu-id="2ac73-137">您必須是網站擁有者，才能變更權限。</span><span class="sxs-lookup"><span data-stu-id="2ac73-137">You must be a site owner to change permissions.</span></span>  
  
1.  <span data-ttu-id="2ac73-138">在 [網站動作] 中，按一下 [網站權限]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2ac73-138">In Site Actions, click **Site Permissions**.</span></span>  
  
2.  <span data-ttu-id="2ac73-139">按一下 [建立群組]\*\*\*\*，並將新群組命名為「BISM 使用者」\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2ac73-139">Click **Create Group** and name the new group **BISM Users**.</span></span>  
  
3.  <span data-ttu-id="2ac73-140">選擇 [讀取]\*\*\*\* 權限等級，然後按一下 [建立]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2ac73-140">Choose the **Read** permission level and click **Create**.</span></span>  
  
4.  <span data-ttu-id="2ac73-141">選取 [人員與群組] 中的 [BISM 使用者]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2ac73-141">Select **BISM Users** in People and Groups.</span></span>  
  
5.  <span data-ttu-id="2ac73-142">指向 [新增]，按一下 [加入使用者]\*\*\*\*，然後加入使用者或群組帳戶。</span><span class="sxs-lookup"><span data-stu-id="2ac73-142">Point to New, click **Add Users**, and then add user or group accounts.</span></span>  
  
     <span data-ttu-id="2ac73-143">這些使用者和群組現在具有整個網站 (包括從網站層級繼承權限的所有文件庫和清單) 的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="2ac73-143">These users and groups will now have Read permissions throughout the site, including all libraries and lists that inherit permissions from the site level.</span></span> <span data-ttu-id="2ac73-144">如果這些權限太高，您可以從特定文件庫、清單或項目中選擇地移除此群組。</span><span class="sxs-lookup"><span data-stu-id="2ac73-144">If these permissions are too high, you can selectively remove this group from specific libraries, lists, or items.</span></span>  
  
 <span data-ttu-id="2ac73-145">若要選擇地在項目層級移除權限，請執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="2ac73-145">To selectively remove permissions at the item level, do the following:</span></span>  
  
1.  <span data-ttu-id="2ac73-146">在文件庫中，選取文件。</span><span class="sxs-lookup"><span data-stu-id="2ac73-146">In a library, select a document.</span></span> <span data-ttu-id="2ac73-147">按一下右下箭頭，然後按一下 [管理權限]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2ac73-147">Click the right down arrow and then click **Manage Permissions**.</span></span>  
  
2.  <span data-ttu-id="2ac73-148">根據預設，項目會繼承權限。</span><span class="sxs-lookup"><span data-stu-id="2ac73-148">By default, an item inherits permissions.</span></span> <span data-ttu-id="2ac73-149">若要變更此文件庫中個別文件的權限，請按一下 [停止繼承權限]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2ac73-149">To change the permissions of individual documents in this library, click **Stop Inheriting Permissions**.</span></span>  
  
3.  <span data-ttu-id="2ac73-150">選取 [BISM 使用者]\*\*\*\* 旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="2ac73-150">Select the checkbox next to **BISM Users**.</span></span>  
  
4.  <span data-ttu-id="2ac73-151">按一下 [移除使用者權限]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2ac73-151">Click **Remove User Permissions**.</span></span>  
  
##  <a name="configure-sharepoint-permissions-on-the-workbook"></a><a name="bkmk_userdb"></a><span data-ttu-id="2ac73-152">設定活頁簿的 SharePoint 許可權</span><span class="sxs-lookup"><span data-stu-id="2ac73-152">Configure SharePoint Permissions on the Workbook</span></span>  
 <span data-ttu-id="2ac73-153">如果您在 Excel 活頁簿內使用 PowerPivot 資料庫，此 Excel 活頁簿的 SharePoint 權限會決定透過 BI 語意模型連接的資料存取。</span><span class="sxs-lookup"><span data-stu-id="2ac73-153">If you are using a PowerPivot database inside an Excel workbook, the SharePoint permissions on the Excel workbook determine data access via the BI semantic model connection.</span></span> <span data-ttu-id="2ac73-154">存取活頁簿的所有使用者都必須擁有活頁簿的讀取權限，才能將它做為外部資料來源。</span><span class="sxs-lookup"><span data-stu-id="2ac73-154">All users who access the workbook must have Read permissions on the workbook in order to use it as an external data source.</span></span>  
  
 <span data-ttu-id="2ac73-155">如果您使用上一節中的指示建立了「BISM 使用者」\*\*\*\* 群組，則「BISM 使用者」\*\*\*\* 成員的使用者和群組帳戶都會有此活頁簿和 BI 語意模型連接檔案的充足權限 (假設活頁簿使用繼承的權限)。</span><span class="sxs-lookup"><span data-stu-id="2ac73-155">If you created a **BISM Users** group using the instructions in the previous section, user and group accounts that are members of **BISM Users** will have sufficient permission on the workbook as well as the BI semantic model connection file, assuming the workbook uses inherited permissions.</span></span>  
  
##  <a name="next-steps"></a><a name="bkmk_next"></a> <span data-ttu-id="2ac73-156">後續步驟</span><span class="sxs-lookup"><span data-stu-id="2ac73-156">Next Steps</span></span>  
 <span data-ttu-id="2ac73-157">在建立 BI 語意模型連接並且確保其安全之後，可以將此連接指定為資料來源。</span><span class="sxs-lookup"><span data-stu-id="2ac73-157">After you create and secure a BI semantic model connection, you can specify it as a data source.</span></span> <span data-ttu-id="2ac73-158">如需詳細資訊，請參閱 [在 Excel 或 Reporting Services 使用 BI 語意模型連接](use-a-bi-semantic-model-connection-in-excel-or-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="2ac73-158">For more information, see [Use a BI Semantic Model Connection in Excel or Reporting Services](use-a-bi-semantic-model-connection-in-excel-or-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ac73-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ac73-159">See Also</span></span>  
 <span data-ttu-id="2ac73-160">[PowerPivot BI 語義模型連接 &#40;. bism&#41;](power-pivot-bi-semantic-model-connection-bism.md) </span><span class="sxs-lookup"><span data-stu-id="2ac73-160">[PowerPivot BI Semantic Model Connection &#40;.bism&#41;](power-pivot-bi-semantic-model-connection-bism.md) </span></span>  
 <span data-ttu-id="2ac73-161">[在 Excel 或 Reporting Services 中使用 BI 語義模型連接](use-a-bi-semantic-model-connection-in-excel-or-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="2ac73-161">[Use a BI Semantic Model Connection in Excel or Reporting Services](use-a-bi-semantic-model-connection-in-excel-or-reporting-services.md) </span></span>  
 [<span data-ttu-id="2ac73-162">建立與表格式模型資料庫的 BI 語義模型連接</span><span class="sxs-lookup"><span data-stu-id="2ac73-162">Create a BI Semantic Model Connection to a Tabular Model Database</span></span>](create-a-bi-semantic-model-connection-to-a-tabular-model-database.md)  
  
  
