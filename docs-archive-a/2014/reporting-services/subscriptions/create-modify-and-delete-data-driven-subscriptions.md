---
title: 建立、修改和刪除資料驅動訂閱 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- query-based subscriptions [Reporting Services]
- queries [Reporting Services], data-driven subscriptions
- subscriptions [Reporting Services], data-driven
- data-driven subscriptions
ms.assetid: 0ba2093e-9393-4eb6-af06-9da10988cfaf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0ec7fad729e5a7bd0f75d7a524ba315b4511a7a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598732"
---
# <a name="create-modify-and-delete-a-data-driven-subscription"></a><span data-ttu-id="599a1-102">Create, Modify, and Delete a Data-Driven Subscription</span><span class="sxs-lookup"><span data-stu-id="599a1-102">Create, Modify, and Delete a Data-Driven Subscription</span></span>
  <span data-ttu-id="599a1-103">資料驅動訂閱是查詢式訂閱，會在執行階段取得用於處理訂閱的資料值。</span><span class="sxs-lookup"><span data-stu-id="599a1-103">A data-driven subscription is a query-based subscription that gets the data values used for processing the subscription at run time.</span></span> <span data-ttu-id="599a1-104">觸發訂閱時，會處理查詢以取得有關收件者、報表傳遞選項、轉譯格式，以及參數設定的最新資訊。</span><span class="sxs-lookup"><span data-stu-id="599a1-104">When the subscription is triggered, a query is processed to get up-to-date information about recipients, report delivery options, rendering formats, and parameter settings.</span></span> <span data-ttu-id="599a1-105">查詢結果會與訂閱定義結合，以建立動態訂閱，該動態訂閱會使用您已在員工資料庫、客戶資料庫，或包含可做為訂閱者資料之資訊的其他任何資料庫中維護的資料。</span><span class="sxs-lookup"><span data-stu-id="599a1-105">The query results are combined with the subscription definition to create a dynamic subscription that uses data you already maintain in an employee database, a customer database, or any other database that contains information that can be used as subscriber data.</span></span>  
  
||  
|-|  
|<span data-ttu-id="599a1-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 原生模式 &#124; SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="599a1-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode &#124; SharePoint mode</span></span>|  
  
 <span data-ttu-id="599a1-107">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="599a1-107">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="599a1-108">建立和修改資料驅動訂閱</span><span class="sxs-lookup"><span data-stu-id="599a1-108">Create and Modify a Data-Driven Subscription</span></span>](#bkmk_create_and_modify)  
  
-   [<span data-ttu-id="599a1-109">定義查詢以擷取訂閱資訊</span><span class="sxs-lookup"><span data-stu-id="599a1-109">Define a query that retrieves subscription information</span></span>](#bkmk_define_query)  
  
-   [<span data-ttu-id="599a1-110">執行訂閱</span><span class="sxs-lookup"><span data-stu-id="599a1-110">Run a subscription</span></span>](#bkmk_run_subscription)  
  
-   [<span data-ttu-id="599a1-111">管理和刪除資料驅動訂閱</span><span class="sxs-lookup"><span data-stu-id="599a1-111">Manage and delete a data-driven subscription</span></span>](#bkmk_manage_and_delete)  
  
##  <a name="create-and-modify-a-data-driven-subscription"></a><a name="bkmk_create_and_modify"></a><span data-ttu-id="599a1-112">建立和修改資料驅動訂閱</span><span class="sxs-lookup"><span data-stu-id="599a1-112">Create and Modify a Data-Driven Subscription</span></span>  
 <span data-ttu-id="599a1-113">若要建立新的資料驅動訂閱或修改現有的訂閱，請使用報表管理員中的 [建立資料驅動訂閱] 頁面。</span><span class="sxs-lookup"><span data-stu-id="599a1-113">To create a new data-driven subscription or modify an existing subscription, use the Create Data-Driven Subscription pages in Report Manager.</span></span> <span data-ttu-id="599a1-114">這些頁面會引導您逐步建立或修改訂閱。</span><span class="sxs-lookup"><span data-stu-id="599a1-114">These pages walk you through each step of creating or modifying a subscription.</span></span> <span data-ttu-id="599a1-115">若要在訂閱建立之後存取，請使用 [我的訂閱] 頁面和報表的 [訂閱] 清單。</span><span class="sxs-lookup"><span data-stu-id="599a1-115">To access a subscription after it is created, use the My Subscriptions page and the Subscriptions list of a report.</span></span> <span data-ttu-id="599a1-116">若要了解如何建立資料驅動訂閱，請參閱[建立資料驅動訂閱 &#40;SSRS 教學課程&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="599a1-116">To learn how to create a data-driven subscription, see [Create a Data-Driven Subscription &#40;SSRS Tutorial&#41;](../create-a-data-driven-subscription-ssrs-tutorial.md).</span></span>  
  
 <span data-ttu-id="599a1-117">若要建立資料驅動訂閱，請選取使用預存認證或無認證的報表。</span><span class="sxs-lookup"><span data-stu-id="599a1-117">To create a data-driven subscription, select a report that uses stored credentials or no credentials.</span></span> <span data-ttu-id="599a1-118">當您建立資料驅動訂閱時，請考慮使用 [描述] 欄位的命名慣例，如此就能輕鬆區分標準訂閱與資料驅動訂閱。</span><span class="sxs-lookup"><span data-stu-id="599a1-118">When you create the data-driven subscription, consider using a naming convention for the description field so you can easily differentiate standard subscriptions from data-driven subscriptions.</span></span>  
  
#### <a name="to-create-a-data-driven-subscription-native-mode"></a><span data-ttu-id="599a1-119">若要建立資料驅動訂閱 (原生模式)</span><span class="sxs-lookup"><span data-stu-id="599a1-119">To create a data-driven subscription (Native Mode)</span></span>  
  
1.  <span data-ttu-id="599a1-120">在報表管理員中，導覽到包含報表的資料夾，將滑鼠停留在報表上方，接著開啟 [選項] 功能表，然後按一下 **[管理]**。</span><span class="sxs-lookup"><span data-stu-id="599a1-120">In Report Manager navigate to the folder containing the report, hover over the report, open the options menu and Click the **Manage.**</span></span>  
  
2.  <span data-ttu-id="599a1-121">按一下 **[訂閱]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="599a1-121">Click the **Subscriptions** tab.</span></span>  
  
3.  <span data-ttu-id="599a1-122">按一下 **[新增資料驅動訂閱]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="599a1-122">Click the **New Data-Driven Subscription** button.</span></span>  
  
#### <a name="to-create-a-data-driven-subscription-sharepoint-mode"></a><span data-ttu-id="599a1-123">若要建立資料驅動訂閱 (SharePoint 模式)</span><span class="sxs-lookup"><span data-stu-id="599a1-123">To create a data-driven subscription (SharePoint Mode)</span></span>  
  
1.  <span data-ttu-id="599a1-124">在 SharePoint 文件庫中，將滑鼠停留在報告上方，接著開啟 [選項] 功能表，然後按一下 **[管理訂閱]** 。</span><span class="sxs-lookup"><span data-stu-id="599a1-124">In the SharePoint document library, hover over the report, open the options menu and Click **Manage Subscriptions**.</span></span>  
  
2.  <span data-ttu-id="599a1-125">按一下 **[加入資料驅動訂閱]** 。</span><span class="sxs-lookup"><span data-stu-id="599a1-125">Click **Add Data-Driven Subscription**.</span></span>  
  
#### <a name="to-modify-an-existing-data-driven-subscription-native-mode"></a><span data-ttu-id="599a1-126">若要修改現有的資料驅動訂閱 (原生模式)</span><span class="sxs-lookup"><span data-stu-id="599a1-126">To modify an existing data-driven subscription (Native Mode)</span></span>  
  
1.  <span data-ttu-id="599a1-127">在 [報表管理員流覽至包含報表的資料夾，將滑鼠停留在報表上，開啟 [選項] 功能表，然後按一下 [**管理**]。</span><span class="sxs-lookup"><span data-stu-id="599a1-127">In Report Manager navigate to the folder containing the report, hover over the report, open the options menu and Click the **Manage**.</span></span>  
  
2.  <span data-ttu-id="599a1-128">按一下 [**訂閱**] 索引標籤。或者，在報表管理員的頂端上按一下 [**我的訂閱**] 連結</span><span class="sxs-lookup"><span data-stu-id="599a1-128">Click the **Subscriptions** tab. Alternatively click the **My Subscriptions** link on at the tope of report manager</span></span>  
  
3.  <span data-ttu-id="599a1-129">選取您要修改的訂閱。</span><span class="sxs-lookup"><span data-stu-id="599a1-129">Select the subscription you want to modify.</span></span> <span data-ttu-id="599a1-130">下列圖示表示資料驅動訂閱：![資料驅動訂閱圖示](../media/hlp-16subscriptiondd.gif "資料驅動訂閱圖示")</span><span class="sxs-lookup"><span data-stu-id="599a1-130">The following icon indicates a data-driven subscription: ![Data-driven subscription icon](../media/hlp-16subscriptiondd.gif "Data-driven subscription icon")</span></span>  
  
#### <a name="to-modify-an-existing-data-driven-subscription-sharepoint-mode"></a><span data-ttu-id="599a1-131">若要修改現有的資料驅動訂閱 (SharePoint 模式)</span><span class="sxs-lookup"><span data-stu-id="599a1-131">To modify an existing data-driven subscription (SharePoint Mode)</span></span>  
  
1.  <span data-ttu-id="599a1-132">在 SharePoint 文件庫中，將滑鼠停留在報告上方，接著開啟 [選項] 功能表，然後按一下 **[管理訂閱]** 。</span><span class="sxs-lookup"><span data-stu-id="599a1-132">In the SharePoint document library, hover over the report, open the options menu and Click **Manage Subscriptions**.</span></span>  
  
2.  <span data-ttu-id="599a1-133">選取您要修改的訂閱。</span><span class="sxs-lookup"><span data-stu-id="599a1-133">Select the subscription you want to modify.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="599a1-134">您可以修改任何已經指定的值。</span><span class="sxs-lookup"><span data-stu-id="599a1-134">You can modify any value that is already specified.</span></span> <span data-ttu-id="599a1-135">所有值均以第一次建立時的方式呈現，除了用來存取訂閱者資料存放區的密碼。</span><span class="sxs-lookup"><span data-stu-id="599a1-135">All values are presented as they were first created, except for the password that is used to access the subscriber data store.</span></span> <span data-ttu-id="599a1-136">每次修改值的時候，都必須在第二頁或任何後續頁面重新輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="599a1-136">You must retype the password every time you modify values on the second page or any subsequent page.</span></span>  
  
 <span data-ttu-id="599a1-137">在可以建立資料驅動訂閱之前，請先確定有滿足以下需求：</span><span class="sxs-lookup"><span data-stu-id="599a1-137">Before you can create a data-driven subscription, ensure that you satisfy the following requirements:</span></span>  
  
-   <span data-ttu-id="599a1-138">**報表需求**。</span><span class="sxs-lookup"><span data-stu-id="599a1-138">**Report requirements**.</span></span> <span data-ttu-id="599a1-139">報表必須使用預存認證或不使用認證，才能在執行階段擷取資料。</span><span class="sxs-lookup"><span data-stu-id="599a1-139">The report must use stored credentials or no credentials to retrieve data at run time.</span></span> <span data-ttu-id="599a1-140">如果報表是使用模擬或委派的認證來連接外部資料來源，您便無法訂閱此報表；當處理此訂閱時，將無法使用建立或擁有此訂閱之使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="599a1-140">You cannot subscribe to a report that uses impersonated or delegated credentials to connect to an external data source; the credentials of the user who creates or owns the subscription will not be available when the subscription is processed.</span></span> <span data-ttu-id="599a1-141">預存認證可以是 Windows 帳戶或資料庫使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="599a1-141">The stored credentials can be a Windows account or a database user account.</span></span> <span data-ttu-id="599a1-142">如需詳細資訊，請參閱 [指定報表資料來源的認證及連接資訊](../report-data/specify-credential-and-connection-information-for-report-data-sources.md)。</span><span class="sxs-lookup"><span data-stu-id="599a1-142">For more information, see [Specify Credential and Connection Information for Report Data Sources](../report-data/specify-credential-and-connection-information-for-report-data-sources.md).</span></span>  
  
     <span data-ttu-id="599a1-143">如果「報表產生器」報表是使用模型當做資料來源，而該模型包含模型項目安全性設定，您便無法訂閱此報表。</span><span class="sxs-lookup"><span data-stu-id="599a1-143">You cannot subscribe to a Report Builder report that uses a model as a data source and the model contains model item security settings.</span></span> <span data-ttu-id="599a1-144">這項限制中只包含使用模型項目安全性的報表。</span><span class="sxs-lookup"><span data-stu-id="599a1-144">Only reports that use model item security are included in this restriction.</span></span>  
  
     <span data-ttu-id="599a1-145">您不能在包含 `User!UserID` 運算式的報表上建立資料驅動訂閱。</span><span class="sxs-lookup"><span data-stu-id="599a1-145">You cannot create a data-driven subscription on a report that contains the `User!UserID` expression.</span></span>  
  
-   <span data-ttu-id="599a1-146">**資料需求**。</span><span class="sxs-lookup"><span data-stu-id="599a1-146">**Data requirements**.</span></span> <span data-ttu-id="599a1-147">您必須有一個包含訂閱者資料的可存取外部資料來源。</span><span class="sxs-lookup"><span data-stu-id="599a1-147">You must have an accessible external data source that contains subscriber data.</span></span>  
  
-   <span data-ttu-id="599a1-148">**使用者需求**。</span><span class="sxs-lookup"><span data-stu-id="599a1-148">**User requirements**.</span></span> <span data-ttu-id="599a1-149">此訂閱的作者必須具有「管理報表」和「管理所有訂閱」的權限。</span><span class="sxs-lookup"><span data-stu-id="599a1-149">The author of the subscription must have permission to "Manage reports" and "Manage all subscriptions."</span></span> <span data-ttu-id="599a1-150">如需項目層級工作權限的詳細資訊，請參閱 [工作和權限](../security/tasks-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="599a1-150">For more information about item-level task permissions, see [Tasks and Permissions](../security/tasks-and-permissions.md).</span></span> <span data-ttu-id="599a1-151">此作者也必須具有適當的認證，才能存取包含訂閱者資料的外部資料來源。</span><span class="sxs-lookup"><span data-stu-id="599a1-151">The author must also have the necessary credentials to access the external data source that contains subscriber data.</span></span>  
  
##  <a name="define-a-query-that-retrieves-subscription-information"></a><a name="bkmk_define_query"></a><span data-ttu-id="599a1-152">定義可抓取訂閱資訊的查詢</span><span class="sxs-lookup"><span data-stu-id="599a1-152">Define a query that retrieves subscription information</span></span>  
 <span data-ttu-id="599a1-153">資料驅動訂閱必須指定查詢或命令來擷取訂閱者資料，</span><span class="sxs-lookup"><span data-stu-id="599a1-153">A data-driven subscription must specify a query or command that retrieves subscriber data.</span></span> <span data-ttu-id="599a1-154">查詢應該針對每一個訂閱者產生一個資料列。</span><span class="sxs-lookup"><span data-stu-id="599a1-154">The query should produce one row for each subscriber.</span></span> <span data-ttu-id="599a1-155">如果您是使用電子郵件傳遞延伸模組，則查詢應傳回每一個訂閱者的有效電子郵件別名。</span><span class="sxs-lookup"><span data-stu-id="599a1-155">If you are using the e-mail delivery extension, the query should return a valid e-mail alias for each subscriber.</span></span> <span data-ttu-id="599a1-156">傳遞的數目會依據查詢所傳回的資料列數目而定。</span><span class="sxs-lookup"><span data-stu-id="599a1-156">The number of deliveries that are made is based on the number of rows returned by the query.</span></span> <span data-ttu-id="599a1-157">如果資料列集包括 10,000 個資料列，則訂閱會傳遞 10,000 個報表。</span><span class="sxs-lookup"><span data-stu-id="599a1-157">If the row set consists of 10,000 rows, the subscription delivers 10,000 reports.</span></span>  
  
 <span data-ttu-id="599a1-158">如果執行查詢很花時間，您可以增加逾時值以容納更多的處理。</span><span class="sxs-lookup"><span data-stu-id="599a1-158">If executing the query is time-consuming, you can increase the time-out value to accommodate additional processing.</span></span>  
  
 <span data-ttu-id="599a1-159">針對此步驟，您必須在繼續之前先驗證查詢。</span><span class="sxs-lookup"><span data-stu-id="599a1-159">For this step, the query must be validated before you continue.</span></span> <span data-ttu-id="599a1-160">驗證並不會處理查詢，但會傳回在資料列集內的所有資料行清單，讓您可以在後續選取範圍中參考資料行。</span><span class="sxs-lookup"><span data-stu-id="599a1-160">Validation does not process the query, but it does return a list of all columns that are in the row set so that you can reference the columns in subsequent selections.</span></span> <span data-ttu-id="599a1-161">如果查詢未通過驗證，您就無法繼續。</span><span class="sxs-lookup"><span data-stu-id="599a1-161">If the query fails to validate, you cannot continue.</span></span> <span data-ttu-id="599a1-162">如果查詢語法不正確或資料來源的連接無效，查詢就無法通過驗證。</span><span class="sxs-lookup"><span data-stu-id="599a1-162">A query fails to validate if the query syntax is incorrect or if the connection to the data source is not valid.</span></span> <span data-ttu-id="599a1-163">使用 **[上一步]** 按鈕，以更正資料來源。</span><span class="sxs-lookup"><span data-stu-id="599a1-163">Use the **Back** button to make corrections to the data source.</span></span>  
  
##  <a name="run-a-subscription"></a><a name="bkmk_run_subscription"></a><span data-ttu-id="599a1-164">執行訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="599a1-164">Run a subscription</span></span>  
 <span data-ttu-id="599a1-165">您需要設定訂閱處理的條件。</span><span class="sxs-lookup"><span data-stu-id="599a1-165">You configure the conditions for subscription processing.</span></span> <span data-ttu-id="599a1-166">您可以設定排程或觸發訂閱，讓更新與報表執行快照集一致。</span><span class="sxs-lookup"><span data-stu-id="599a1-166">You can configure a schedule, or you can trigger the subscription to coincide with updates to a report execution snapshot.</span></span>  
  
 <span data-ttu-id="599a1-167">![注意](../media/rs-fyinote.png "注意")雖然使用者介面中沒有可用來立即執行訂閱的功能，但您可以使用簡單的 Windows PowerShell 腳本來觸發要執行的訂閱。</span><span class="sxs-lookup"><span data-stu-id="599a1-167">![note](../media/rs-fyinote.png "note") While there is no feature in the user interface that you can use to immediately run a subscription, you can use a simple Windows PowerShell script to trigger a subscription to run.</span></span> <span data-ttu-id="599a1-168">如需詳細資訊，請參閱[使用 PowerShell 變更和列出 Reporting Services 訂用帳戶擁有者和執行訂](manage-subscription-owners-and-run-subscription-powershell.md)用帳戶中的「腳本：執行 (引發) 單一訂閱」一節。</span><span class="sxs-lookup"><span data-stu-id="599a1-168">For more information, see the "Script: Run (fire) a single subscription" section of [Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription](manage-subscription-owners-and-run-subscription-powershell.md).</span></span>  
  
 <span data-ttu-id="599a1-169">執行資料驅動訂閱的排程和條件，與標準訂閱的處理相同。</span><span class="sxs-lookup"><span data-stu-id="599a1-169">Schedule and conditions for running a data-driven subscriptions is the same as processing for standard subscriptions.</span></span>  
  
##  <a name="manage-and-delete-a-data-driven-subscription"></a><a name="bkmk_manage_and_delete"></a><span data-ttu-id="599a1-170">管理和刪除資料驅動訂閱</span><span class="sxs-lookup"><span data-stu-id="599a1-170">Manage and delete a data-driven subscription</span></span>  
 <span data-ttu-id="599a1-171">您無法透過報表管理員的 [管理作業] 頁面，停止或刪除正在進行中的資料驅動訂閱。</span><span class="sxs-lookup"><span data-stu-id="599a1-171">A data-driven subscription that is in progress cannot be stopped or deleted through the Manage Jobs page of Report Manager.</span></span> <span data-ttu-id="599a1-172">因此，建議您使用共用排程來觸發資料驅動訂閱。</span><span class="sxs-lookup"><span data-stu-id="599a1-172">For this reason, it is advantageous to use a shared schedule to trigger data-driven subscription.</span></span> <span data-ttu-id="599a1-173">這樣一來，如果您想要暫時防止訂閱處理，就可以暫停觸發訂閱的排程。</span><span class="sxs-lookup"><span data-stu-id="599a1-173">That way, if you want to temporarily prevent a subscription from processing, you can pause the schedule that triggers the subscription.</span></span> <span data-ttu-id="599a1-174">如需詳細資訊，請參閱 [建立和管理原生模式報表伺服器的訂閱](../create-manage-subscriptions-native-mode-report-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="599a1-174">For more information, see [Create and Manage Subscriptions for Native Mode Report Servers](../create-manage-subscriptions-native-mode-report-servers.md).</span></span>  
  
 <span data-ttu-id="599a1-175">若要刪除資料驅動訂閱，請從報表的 [我的訂閱] 頁面或 [訂閱] 頁面選取該訂閱，然後按一下 **[刪除]**。</span><span class="sxs-lookup"><span data-stu-id="599a1-175">To delete a data-driven subscription, select it from the My Subscriptions page or the Subscriptions page of a report and then click **Delete**.</span></span>  
  
 <span data-ttu-id="599a1-176">如需如何取消資料驅動訂閱的指示，請參閱 [管理執行中的處理序](manage-a-running-process.md)。</span><span class="sxs-lookup"><span data-stu-id="599a1-176">For instructions on how to cancel a data-driven subscription, see [Manage a Running Process](manage-a-running-process.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="599a1-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="599a1-177">See Also</span></span>  
 <span data-ttu-id="599a1-178">[以原生模式 &#40;Reporting Services 建立、修改和刪除標準訂閱&#41;](create-and-manage-subscriptions-for-native-mode-report-servers.md) </span><span class="sxs-lookup"><span data-stu-id="599a1-178">[Create, Modify, and Delete Standard Subscriptions &#40;Reporting Services in Native Mode&#41;](create-and-manage-subscriptions-for-native-mode-report-servers.md) </span></span>  
 <span data-ttu-id="599a1-179">[訂閱與傳遞 &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="599a1-179">[Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span></span>  
 <span data-ttu-id="599a1-180">[報表管理員 &#40;SSRS 原生模式&#41;](../report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="599a1-180">[Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="599a1-181">[建立及管理原生模式報表伺服器的訂閱](../create-manage-subscriptions-native-mode-report-servers.md) </span><span class="sxs-lookup"><span data-stu-id="599a1-181">[Create and Manage Subscriptions for Native Mode Report Servers](../create-manage-subscriptions-native-mode-report-servers.md) </span></span>  
 <span data-ttu-id="599a1-182">[訂閱頁面 &#40;報表管理員&#41;](../subscriptions-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="599a1-182">[Subscriptions Page &#40;Report Manager&#41;](../subscriptions-page-report-manager.md) </span></span>  
 [<span data-ttu-id="599a1-183">我的訂閱頁面 &#40;報表管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="599a1-183">My Subscriptions Page &#40;Report Manager&#41;</span></span>](../my-subscriptions-page-report-manager.md)  
  
  
