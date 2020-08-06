---
title: 第 3 課：定義資料驅動訂閱 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 89197b9b-7502-4fe2-bea3-ed7943eebf3b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d1bbc25bdd08b369180e31378a6d25a595badbcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710261"
---
# <a name="lesson-3-defining-a-data-driven-subscription"></a><span data-ttu-id="079a4-102">Lesson 3: Defining a Data-Driven Subscription</span><span class="sxs-lookup"><span data-stu-id="079a4-102">Lesson 3: Defining a Data-Driven Subscription</span></span>
  <span data-ttu-id="079a4-103">在這個課程中，您將利用資料驅動訂閱頁面來連接訂閱資料來源、建立擷取訂閱資料的查詢，以及將結果集對應至報表和傳遞選項。</span><span class="sxs-lookup"><span data-stu-id="079a4-103">In this lesson, you use the data-driven subscription pages to connect to a subscription data source, build a query that retrieves subscription data, and map the result set to report and delivery options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="079a4-104">開始之前，請確認 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent 服務正在執行。</span><span class="sxs-lookup"><span data-stu-id="079a4-104">Before you start, verify that [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent service is running.</span></span> <span data-ttu-id="079a4-105">若未執行，您就無法儲存訂閱。</span><span class="sxs-lookup"><span data-stu-id="079a4-105">If it is not running, you cannot save the subscription.</span></span>  
  
 <span data-ttu-id="079a4-106">這一課會假設您已完成第 1 課和第 2 課，而且報表資料來源使用預存認證。</span><span class="sxs-lookup"><span data-stu-id="079a4-106">This lesson assumes you completed Lesson 1 and Lesson 2 and that the report data source uses stored credentials.</span></span>  <span data-ttu-id="079a4-107">如需詳細資訊，請參閱 [第 2 課：修改報表資料來源屬性](../reporting-services/lesson-2-modifying-the-report-data-source-properties.md)</span><span class="sxs-lookup"><span data-stu-id="079a4-107">For more information, see [Lesson 2: Modifying the Report Data Source Properties](../reporting-services/lesson-2-modifying-the-report-data-source-properties.md)</span></span>  
  
 <span data-ttu-id="079a4-108">本主題內容：</span><span class="sxs-lookup"><span data-stu-id="079a4-108">In this topic:</span></span>  
  
-   [<span data-ttu-id="079a4-109">啟動資料驅動訂閱嚮導</span><span class="sxs-lookup"><span data-stu-id="079a4-109">Start the Data-Driven Subscription Wizard</span></span>](#bkmk_startwizard)  
  
-   [<span data-ttu-id="079a4-110">步驟 1 - 定義描述</span><span class="sxs-lookup"><span data-stu-id="079a4-110">Step 1 - Define a description</span></span>](#bkmk_definesubscription)  
  
-   [<span data-ttu-id="079a4-111">步驟 2 - 定義訂閱者資料來源的連接</span><span class="sxs-lookup"><span data-stu-id="079a4-111">Step 2 - Define a Connection to the Subscriber Data Source</span></span>](#bkmk_defineconnectiontosubscriber)  
  
-   [<span data-ttu-id="079a4-112">步驟 3 - 定義擷取訂閱者資料的查詢</span><span class="sxs-lookup"><span data-stu-id="079a4-112">Step 3 - Define a Query to Retrieve Subscriber data</span></span>](#bkmk_definequery)  
  
-   [<span data-ttu-id="079a4-113">步驟 4 - 設定傳遞選項</span><span class="sxs-lookup"><span data-stu-id="079a4-113">Step 4 - Set Delivery Options</span></span>](#bkmk_set_deliveryoptions)  
  
-   [<span data-ttu-id="079a4-114">步驟 5 - 設定參數值以改變報表輸出</span><span class="sxs-lookup"><span data-stu-id="079a4-114">Step 5 - Configure a Parameter Value to Very Report Output</span></span>](#bkmk_configure_parameter)  
  
-   [<span data-ttu-id="079a4-115">步驟 6 - 為訂閱建立排程</span><span class="sxs-lookup"><span data-stu-id="079a4-115">Step 6 - To Schedule a Subscription</span></span>](#bkmk_schedule_subscription)  
  
##  <a name="start-the-data-driven-subscription-wizard"></a><a name="bkmk_startwizard"></a><span data-ttu-id="079a4-116">啟動資料驅動訂閱嚮導</span><span class="sxs-lookup"><span data-stu-id="079a4-116">Start the Data-Driven Subscription Wizard</span></span>  
  
1.  <span data-ttu-id="079a4-117">在報表管理員中，按一下 **[首頁]**，然後導覽至包含 **Sales Orders** 報表的資料夾。</span><span class="sxs-lookup"><span data-stu-id="079a4-117">In Report Manager, click **Home**, and navigate to the folder containing the **Sales Orders** report.</span></span>  
  
2.  <span data-ttu-id="079a4-118">在報表的內容功能表中，按一下 **[管理]**，然後按一下 **[訂閱]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="079a4-118">In the context menu of the report, click **Manage**, and then click the **Subscriptions** tab.</span></span>  
  
3.  <span data-ttu-id="079a4-119">按一下 [**新增資料驅動訂閱**]。</span><span class="sxs-lookup"><span data-stu-id="079a4-119">Click **New Data-driven Subscription**.</span></span> <span data-ttu-id="079a4-120">如果您沒有看見這個按鈕，表示您沒有「內容管理員」權限。</span><span class="sxs-lookup"><span data-stu-id="079a4-120">If you do not see this button, you do not have Content Manager permissions.</span></span>  
  
##  <a name="step-1---define-a-description"></a><a name="bkmk_definesubscription"></a><span data-ttu-id="079a4-121">步驟 1-定義描述</span><span class="sxs-lookup"><span data-stu-id="079a4-121">Step 1 - Define a description</span></span>  
  
1.  <span data-ttu-id="079a4-122">在 [描述] 中，輸入 **銷售訂單傳遞** 。</span><span class="sxs-lookup"><span data-stu-id="079a4-122">Type **Sales Order delivery** in description.</span></span>  
  
2.  <span data-ttu-id="079a4-123">在 **[指定通知收件者的方式]** 中，選取 **[Windows FileShare]**。</span><span class="sxs-lookup"><span data-stu-id="079a4-123">Select **Windows FileShare** for **Specify how recipients are notified**.</span></span>  
  
3.  <span data-ttu-id="079a4-124">選取 **[僅為此訂閱指定]**，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="079a4-124">Select **Specify for this subscription only**, and then click **Next**.</span></span>  
  
##  <a name="step-2---define-a-connection-to-the-subscriber-data-source"></a><a name="bkmk_defineconnectiontosubscriber"></a><span data-ttu-id="079a4-125">步驟 2-定義訂閱者資料來源的連接</span><span class="sxs-lookup"><span data-stu-id="079a4-125">Step 2 - Define a Connection to the Subscriber Data Source</span></span>  
  
1.  <span data-ttu-id="079a4-126">選取 **[Microsoft SQL Server]** 做為資料來源類型。</span><span class="sxs-lookup"><span data-stu-id="079a4-126">Select **Microsoft SQL Server** as the data source type.</span></span>  
  
2.  <span data-ttu-id="079a4-127">在 [連接字串] 中，輸入下列連接字串：</span><span class="sxs-lookup"><span data-stu-id="079a4-127">In Connection string, type the following connection string:</span></span>  
  
    ```  
    data source=localhost; initial catalog=Subscribers  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="079a4-128">訂閱者是您在第 1 課所建立的資料庫。</span><span class="sxs-lookup"><span data-stu-id="079a4-128">Subscribers is the database you created in lesson 1.</span></span>  
  
3.  <span data-ttu-id="079a4-129">按一下 **[安全地儲存在報表伺服器中的認證]**。</span><span class="sxs-lookup"><span data-stu-id="079a4-129">Click **Credentials stored securely in the report server**.</span></span>  
  
4.  <span data-ttu-id="079a4-130">在 **[使用者名稱]** 和 **[密碼]** 中，輸入網域使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="079a4-130">In **User Name** and **Password**, type your domain user name and password.</span></span> <span data-ttu-id="079a4-131">指定 **[使用者名稱]** 時，請同時包括網域和使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="079a4-131">Include both the domain and user account when specifying **User Name**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="079a4-132">用於連接至訂閱者資料來源的認證不會傳回給 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="079a4-132">Credentials used to connect to a subscriber data source are not passed back to [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="079a4-133">如果您稍後修改了訂閱，就必須重新輸入用於連接到資料來源的密碼。</span><span class="sxs-lookup"><span data-stu-id="079a4-133">If you modify the subscription later, you must retype the password used to connect to the data source.</span></span>  
  
5.  <span data-ttu-id="079a4-134">選取 **[連接到資料來源時做為 Windows 認證]**，再按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="079a4-134">Select **Use as windows credentials when connecting to the data source**, and then click **Next**.</span></span>  
  
##  <a name="step-3---define-a-query-to-retrieve-subscriber-data"></a><a name="bkmk_definequery"></a><span data-ttu-id="079a4-135">步驟 3-定義用來抓取訂閱者資料的查詢</span><span class="sxs-lookup"><span data-stu-id="079a4-135">Step 3 - Define a Query to Retrieve Subscriber data</span></span>  
  
1.  <span data-ttu-id="079a4-136">在查詢方塊中，輸入下列查詢：</span><span class="sxs-lookup"><span data-stu-id="079a4-136">In the query box, type the following query:</span></span>  
  
    ```  
    Select * from OrderInfo  
    ```  
  
2.  <span data-ttu-id="079a4-137">將逾時指定為 30 秒。</span><span class="sxs-lookup"><span data-stu-id="079a4-137">Specify a time-out of 30 seconds.</span></span>  
  
3.  <span data-ttu-id="079a4-138">按一下 **[驗證]**，再按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="079a4-138">Click **Validate**, and then click **Next**.</span></span>  
  
##  <a name="step-4---set-delivery-options"></a><a name="bkmk_set_deliveryoptions"></a><span data-ttu-id="079a4-139">步驟 4-設定傳遞選項</span><span class="sxs-lookup"><span data-stu-id="079a4-139">Step 4 - Set Delivery Options</span></span>  
  
1.  <span data-ttu-id="079a4-140">針對 **[檔案名稱]**，選取 **[從資料庫取值]**。</span><span class="sxs-lookup"><span data-stu-id="079a4-140">For **File name**, select **Get the value from the database**.</span></span> <span data-ttu-id="079a4-141">選取 **[Order]** 欄位。</span><span class="sxs-lookup"><span data-stu-id="079a4-141">Select the field **Order**.</span></span>  
  
2.  <span data-ttu-id="079a4-142">針對 **[路徑]**，選取 **[指定靜態值]**。</span><span class="sxs-lookup"><span data-stu-id="079a4-142">For **Path**, select **Specify a static value**.</span></span> <span data-ttu-id="079a4-143">在 [設定值] 中，輸入您擁有寫入權限之公用檔案共用的名稱 (例如 `\\mycomputer\public\myreports`)。</span><span class="sxs-lookup"><span data-stu-id="079a4-143">In Setting Value, type the name of a public file share for which you have write permissions (for example, `\\mycomputer\public\myreports`).</span></span>  
  
3.  <span data-ttu-id="079a4-144">針對 **[轉譯格式]**，選取 **[從資料庫取值]**。</span><span class="sxs-lookup"><span data-stu-id="079a4-144">For **Render Format**, select **Get the value from the database**.</span></span> <span data-ttu-id="079a4-145">選取 [**格式**]。</span><span class="sxs-lookup"><span data-stu-id="079a4-145">Select **Format**.</span></span>  
  
4.  <span data-ttu-id="079a4-146">針對 **[寫入模式]**，選取 **[指定靜態值]** 並選取 **[自動遞增]**。</span><span class="sxs-lookup"><span data-stu-id="079a4-146">For **Write mode**, select **Specify a static value** and select **AutoIncrement**.</span></span>  
  
5.  <span data-ttu-id="079a4-147">針對 **[副檔名]**，選取 **[指定靜態值]** 並選取 **[True]**。</span><span class="sxs-lookup"><span data-stu-id="079a4-147">For **File Extension**, select **Specify a static value** and select **True**.</span></span>  
  
6.  <span data-ttu-id="079a4-148">針對 **[使用者名稱]**，選取 **[指定靜態值]**。</span><span class="sxs-lookup"><span data-stu-id="079a4-148">For **User name**, select **Specify a static value**.</span></span> <span data-ttu-id="079a4-149">輸入網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="079a4-149">Type your domain user account.</span></span> <span data-ttu-id="079a4-150">請使用下列格式輸入： `<domain>\<account>`。</span><span class="sxs-lookup"><span data-stu-id="079a4-150">Enter it in this format: `<domain>\<account>`.</span></span> <span data-ttu-id="079a4-151">使用者帳戶必須擁有您在上述步驟中設定之路徑的權限。</span><span class="sxs-lookup"><span data-stu-id="079a4-151">The user account needs to have permissions to the path you configured in the previous steps.</span></span>  
  
7.  <span data-ttu-id="079a4-152">針對 **[密碼]**，選取 **[指定靜態值]**。</span><span class="sxs-lookup"><span data-stu-id="079a4-152">For **Password**, select **Specify a static value**.</span></span> <span data-ttu-id="079a4-153">輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="079a4-153">Type your password.</span></span> <span data-ttu-id="079a4-154">請務必小心輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="079a4-154">Be sure that you type the password carefully.</span></span> <span data-ttu-id="079a4-155">精靈不會驗證密碼。</span><span class="sxs-lookup"><span data-stu-id="079a4-155">The wizard does not validate the password.</span></span>  
  
8.  <span data-ttu-id="079a4-156">按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="079a4-156">Click **Next.**</span></span>  
  
##  <a name="step-5---configure-a-parameter-value-to-very-report-output"></a><a name="bkmk_configure_parameter"></a><span data-ttu-id="079a4-157">步驟 5-將參數值設定為非常報告的輸出</span><span class="sxs-lookup"><span data-stu-id="079a4-157">Step 5 - Configure a Parameter Value to Very Report Output</span></span>  
  
1.  <span data-ttu-id="079a4-158">針對 **[OrderNumber]**，選取 **[從資料庫取值]**。</span><span class="sxs-lookup"><span data-stu-id="079a4-158">For **OrderNumber**, select **Get the value from the database**.</span></span> <span data-ttu-id="079a4-159">在 [值] 中，選取 **[Order]**。</span><span class="sxs-lookup"><span data-stu-id="079a4-159">In Value, select **Order**.</span></span> <span data-ttu-id="079a4-160">按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="079a4-160">Click **Next.**</span></span>  
  
##  <a name="step-6---to-schedule-a-subscription"></a><a name="bkmk_schedule_subscription"></a><span data-ttu-id="079a4-161">步驟 6-排程訂閱</span><span class="sxs-lookup"><span data-stu-id="079a4-161">Step 6 - To Schedule a Subscription</span></span>  
  
1.  <span data-ttu-id="079a4-162">按一下 **[在為此訂閱建立的排程上]**，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="079a4-162">Click **On a schedule created for this subscription**, and then click **Next**.</span></span>  
  
2.  <span data-ttu-id="079a4-163">在 **[排程詳細資料]** 中，按一下 **[一次]**。</span><span class="sxs-lookup"><span data-stu-id="079a4-163">In **Schedule Details**, click **Once**.</span></span>  
  
3.  <span data-ttu-id="079a4-164">請指定現在以後的幾分鐘做為開始時間。</span><span class="sxs-lookup"><span data-stu-id="079a4-164">Specify a start time that is a few minutes ahead of the current time.</span></span>  
  
4.  <span data-ttu-id="079a4-165">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="079a4-165">Click **Finish**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="079a4-166">後續步驟</span><span class="sxs-lookup"><span data-stu-id="079a4-166">Next Steps</span></span>  
 <span data-ttu-id="079a4-167">當訂閱執行時，會將四個報表檔傳遞至您指定的檔案共用，「訂閱者」 \*\* 資料來源中的每筆訂單各一個。</span><span class="sxs-lookup"><span data-stu-id="079a4-167">When the subscription runs, four report files will be delivered to the file share you specified, one for each order in the *Subscribers* data source.</span></span> <span data-ttu-id="079a4-168">在資料 (資料應該隨著訂單而不同)、轉譯格式及檔案格式等方面，每項傳遞都應該是唯一的。</span><span class="sxs-lookup"><span data-stu-id="079a4-168">Each delivery should be unique in terms of data (the data should be order-specific), rendering format, and file format.</span></span> <span data-ttu-id="079a4-169">您可以開啟共用資料夾中的每一份報表，確認每個版本都是根據您定義的訂閱選項來自訂的。</span><span class="sxs-lookup"><span data-stu-id="079a4-169">You can open each report from the shared folder to verify that each version is customized based on the subscription options you defined.</span></span>  
  
 <span data-ttu-id="079a4-170">![訂閱建立的檔案清單](../../2014/tutorials/media/ssrs-tutorial-datadriven-subscription-filelist.gif "訂閱建立的檔案清單")</span><span class="sxs-lookup"><span data-stu-id="079a4-170">![List of files created by the subscription](../../2014/tutorials/media/ssrs-tutorial-datadriven-subscription-filelist.gif "List of files created by the subscription")</span></span>  
  
 <span data-ttu-id="079a4-171">報表管理員中的訂閱頁面將包含訂閱的 **[上次執行]** 日期和 **[狀態]** 。</span><span class="sxs-lookup"><span data-stu-id="079a4-171">The subscription page in Report Manager will contain the **Last Run** date and **Status** of the subscription.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="079a4-172">請在訂閱執行之後重新整理頁面，以便查看更新的資訊。</span><span class="sxs-lookup"><span data-stu-id="079a4-172">Refresh the page after the subscription runs to see the updated information.</span></span>  
  
 <span data-ttu-id="079a4-173">![報表管理員中的訂用帳戶結果](../../2014/tutorials/media/ssrs-tutorial-datadriven-subscription-status-reportmanager.gif "報表管理員中的訂用帳戶結果")</span><span class="sxs-lookup"><span data-stu-id="079a4-173">![Subscription results in Report Manager](../../2014/tutorials/media/ssrs-tutorial-datadriven-subscription-status-reportmanager.gif "Subscription results in Report Manager")</span></span>  
  
 <span data-ttu-id="079a4-174">此步驟是＜定義資料驅動訂閱＞教學課程的總結。</span><span class="sxs-lookup"><span data-stu-id="079a4-174">This step concludes the tutorial "Defining a Data-Driven Subscription".</span></span> <span data-ttu-id="079a4-175">若要深入瞭解其他 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 教學課程，請參閱[REPORTING SERVICES &#40;SSRS&#41;的教學](../reporting-services/reporting-services-tutorials-ssrs.md)課程。</span><span class="sxs-lookup"><span data-stu-id="079a4-175">To learn more about other [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] tutorials, see [Reporting Services Tutorials &#40;SSRS&#41;](../reporting-services/reporting-services-tutorials-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="079a4-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="079a4-176">See Also</span></span>  
 <span data-ttu-id="079a4-177">[建立資料驅動訂閱 &#40;SSRS 教學課程&#41;](../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="079a4-177">[Create a Data-Driven Subscription &#40;SSRS Tutorial&#41;](../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md) </span></span>  
 <span data-ttu-id="079a4-178">[訂閱與傳遞 &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="079a4-178">[Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md) </span></span>  
 <span data-ttu-id="079a4-179">[Data-Driven Subscriptions](subscriptions/data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="079a4-179">[Data-Driven Subscriptions](subscriptions/data-driven-subscriptions.md) </span></span>  
 <span data-ttu-id="079a4-180">[建立、修改和刪除資料驅動訂閱](subscriptions/create-modify-and-delete-data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="079a4-180">[Create, Modify, and Delete a Data-Driven Subscription](subscriptions/create-modify-and-delete-data-driven-subscriptions.md) </span></span>  
 [<span data-ttu-id="079a4-181">使用外部資料來源以取得訂閱者資料 &#40;資料驅動訂閱&#41;</span><span class="sxs-lookup"><span data-stu-id="079a4-181">Use an External Data Source for Subscriber Data &#40;Data-Driven Subscription&#41;</span></span>](subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md)  
  
  
