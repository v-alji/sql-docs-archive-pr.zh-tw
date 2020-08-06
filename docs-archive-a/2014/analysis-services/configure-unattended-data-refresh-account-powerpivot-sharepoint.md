---
title: 設定 PowerPivot 無人看管的資料重新整理帳戶 (PowerPivot for SharePoint) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 81401eac-c619-4fad-ad3e-599e7a6f8493
author: minewiskan
ms.author: owend
ms.openlocfilehash: d6f53d7272dc48ed55ffb175e0ace3e97263946c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593033"
---
# <a name="configure-the-powerpivot-unattended-data-refresh-account-powerpivot-for-sharepoint"></a><span data-ttu-id="28e48-102">設定 PowerPivot 無人看管的資料重新整理帳戶 (PowerPivot for SharePoint)</span><span class="sxs-lookup"><span data-stu-id="28e48-102">Configure the PowerPivot Unattended Data Refresh Account (PowerPivot for SharePoint)</span></span>
  <span data-ttu-id="28e48-103">PowerPivot 無人看管的資料重新整理帳戶是一個指定的帳戶，可在 SharePoint 伺服器陣列中執行 PowerPivot 資料重新整理作業。</span><span class="sxs-lookup"><span data-stu-id="28e48-103">The PowerPivot unattended data refresh account is a designated account for running PowerPivot data refresh jobs in a SharePoint farm.</span></span> <span data-ttu-id="28e48-104">藉由設定它，您可以在資料重新整理排程頁面中，啟用 [**使用系統管理員所設定的資料**重新整理帳戶] 選項 (如下) 所示。</span><span class="sxs-lookup"><span data-stu-id="28e48-104">By configuring it, you enable the **Use the data refresh account configured by the administrator** option in a data refresh schedule page (see below).</span></span> <span data-ttu-id="28e48-105">若排程資料重新整理的活頁簿作者想要使用 PowerPivot 無人看管的資料重新整理帳戶執行資料重新整理作業，可以選擇此選項。</span><span class="sxs-lookup"><span data-stu-id="28e48-105">Workbook authors who schedule data refresh can choose this option if they want to use the PowerPivot unattended data refresh account to run a data refresh job.</span></span> <span data-ttu-id="28e48-106">如需有關如何在資料重新整理排程中查看認證選項的詳細資訊，請參閱[排程資料重新整理 &#40;PowerPivot for SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="28e48-106">For more information about how to view the Credentials options in a data refresh schedule, see [Schedule a Data Refresh &#40;PowerPivot for SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md).</span></span>  
  
 <span data-ttu-id="28e48-107">![SSAS_PowerpivotKJ_DataRefreshCreds](media/ssas-powerpivotkj-datarefreshcreds.gif "SSAS_PowerpivotKJ_DataRefreshCreds")</span><span class="sxs-lookup"><span data-stu-id="28e48-107">![SSAS_PowerpivotKJ_DataRefreshCreds](media/ssas-powerpivotkj-datarefreshcreds.gif "SSAS_PowerpivotKJ_DataRefreshCreds")</span></span>  
  
 <span data-ttu-id="28e48-108">**[!INCLUDE[applies](../includes/applies-md.md)]** SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="28e48-108">**[!INCLUDE[applies](../includes/applies-md.md)]**  SharePoint 2010</span></span>  
  
 <span data-ttu-id="28e48-109">根據您在設定伺服器時選取的選項而定，可能已經建立無人看管的資料重新整理帳戶。</span><span class="sxs-lookup"><span data-stu-id="28e48-109">Depending on which options you selected when configuring the server, the unattended data refresh account might already be created.</span></span> <span data-ttu-id="28e48-110">在預設組態中，一開始會將無人看管的資料重新整理帳戶識別設定為伺服器陣列帳戶。</span><span class="sxs-lookup"><span data-stu-id="28e48-110">In a default configuration, the identity of the unattended data refresh account is initially set to the farm account.</span></span> <span data-ttu-id="28e48-111">您可以將帳戶變更為以不同的使用者執行，藉以提高部署的安全性。</span><span class="sxs-lookup"><span data-stu-id="28e48-111">You can improve the security of your deployment by changing the account to run as a different user.</span></span> <span data-ttu-id="28e48-112">請依照下列指示來變更帳戶：[更新現有 PowerPivot 無人看管的資料重新整理帳戶所使用的認證](#bkmk_editUA)。</span><span class="sxs-lookup"><span data-stu-id="28e48-112">Follow these instructions to change the account: [Update the credentials used by an existing PowerPivot unattended data refresh account](#bkmk_editUA).</span></span>  
  
 <span data-ttu-id="28e48-113">對於所有其他安裝情況，您必須使用下列指示手動設定此帳戶。</span><span class="sxs-lookup"><span data-stu-id="28e48-113">For all other installation scenarios, you must configure this account manually using the instructions below.</span></span>  
  
 <span data-ttu-id="28e48-114">本主題包含下列幾節：</span><span class="sxs-lookup"><span data-stu-id="28e48-114">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="28e48-115">先決條件</span><span class="sxs-lookup"><span data-stu-id="28e48-115">Prerequisites</span></span>](#bkmk_prereq)  
  
 [<span data-ttu-id="28e48-116">步驟 1：建立目標應用程式並設定認證</span><span class="sxs-lookup"><span data-stu-id="28e48-116">Step 1: Create a target application and set the credentials</span></span>](#bkmk_create)  
  
 [<span data-ttu-id="28e48-117">步驟 2：在 PowerPivot 伺服器組態頁面中，指定無人看管的帳戶</span><span class="sxs-lookup"><span data-stu-id="28e48-117">Step 2: Specify the unattended account in PowerPivot server configuration pages</span></span>](#bkmk_specifyUA)  
  
 [<span data-ttu-id="28e48-118">步驟3：授與帳戶的「參與」許可權</span><span class="sxs-lookup"><span data-stu-id="28e48-118">Step 3: Grant contribute permissions to the account</span></span>](#bkmk_grant)  
  
 [<span data-ttu-id="28e48-119">步驟 4：授與資料重新整理期間存取外部資料來源時所需的讀取權限</span><span class="sxs-lookup"><span data-stu-id="28e48-119">Step 4: Grant read permissions to access external data sources used in data refresh</span></span>](#bkmk_dbread)  
  
 [<span data-ttu-id="28e48-120">步驟 5：在資料重新整理組態頁面中，確認帳戶可用性</span><span class="sxs-lookup"><span data-stu-id="28e48-120">Step 5: Verify account availability in data refresh configuration pages</span></span>](#bkmk_verify)  
  
 [<span data-ttu-id="28e48-121">使用 PowerPivot 無人看管的資料重新整理帳戶</span><span class="sxs-lookup"><span data-stu-id="28e48-121">Using the PowerPivot Unattended Data Refresh Account</span></span>](#bkmk_use)  
  
 [<span data-ttu-id="28e48-122">更新現有 PowerPivot 無人看管的資料重新整理帳戶所使用的認證</span><span class="sxs-lookup"><span data-stu-id="28e48-122">Update the credentials used by an existing PowerPivot unattended data refresh account</span></span>](#bkmk_editUA)  
  
##  <a name="prerequisites"></a><a name="bkmk_prereq"></a> <span data-ttu-id="28e48-123">必要條件</span><span class="sxs-lookup"><span data-stu-id="28e48-123">Prerequisites</span></span>  
 <span data-ttu-id="28e48-124">您必須啟用並設定 Secure Store Service，而且必須產生主要金鑰。</span><span class="sxs-lookup"><span data-stu-id="28e48-124">Secure Store Service must be enabled and configured, and a master key must be generated.</span></span> <span data-ttu-id="28e48-125">如需如何執行這種操作的指示，請參閱[使用 SharePoint 2010 的 PowerPivot 資料](powerpivot-data-refresh-with-sharepoint-2010.md)重新整理</span><span class="sxs-lookup"><span data-stu-id="28e48-125">For instructions on how to do this, see [PowerPivot Data Refresh with SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md)</span></span>  
  
 <span data-ttu-id="28e48-126">您必須事先決定要將哪個 Windows 網域使用者帳戶當做 PowerPivot 無人看管的資料重新整理帳戶使用。</span><span class="sxs-lookup"><span data-stu-id="28e48-126">You must decide in advance which Windows domain user account to use as the PowerPivot unattended data refresh account.</span></span> <span data-ttu-id="28e48-127">這應該是特別針對這個用途所建立的帳戶，讓您可以監視其使用方式。</span><span class="sxs-lookup"><span data-stu-id="28e48-127">This should be an account that is created specifically for this purpose so that you can monitor how it is used.</span></span>  
  
 <span data-ttu-id="28e48-128">您必須知道 PowerPivot 系統服務的應用程式識別。</span><span class="sxs-lookup"><span data-stu-id="28e48-128">You must know the application identity of the PowerPivot System Service.</span></span> <span data-ttu-id="28e48-129">當您在步驟1中為其建立目標應用程式時，您會將無人看管資料重新整理帳戶的 [**完全控制**] 許可權授與此服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="28e48-129">You will give this service account **Full Control** permissions over the unattended data refresh account when you create the target application for it in step 1.</span></span> <span data-ttu-id="28e48-130">這些權限允許 PowerPivot 系統服務在資料重新整理期間擷取無人看管資料重新整理帳戶的認證。</span><span class="sxs-lookup"><span data-stu-id="28e48-130">These permissions allow the PowerPivot System Service to retrieve the credentials of the unattended data refresh account during data refresh.</span></span> <span data-ttu-id="28e48-131">若要取得所需的服務帳戶資訊，請開啟 [管理中心] 中的 [**設定服務帳戶**] 頁面，然後選取 PowerPivot 服務應用程式所使用的服務應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="28e48-131">To get the required service account information, open the **Configure service accounts** page in Central Administration and select the service application pool used by the PowerPivot service application.</span></span> <span data-ttu-id="28e48-132">根據預設，這是**服務應用程式集區-SharePoint Web 服務系統**。</span><span class="sxs-lookup"><span data-stu-id="28e48-132">By default, this is the **Service Application Pool - SharePoint Web Services System**.</span></span>  
  
## <a name="configure-the-unattended-powerpivot-data-refresh-account"></a><span data-ttu-id="28e48-133">設定無人看管的 PowerPivot 資料重新整理帳戶</span><span class="sxs-lookup"><span data-stu-id="28e48-133">Configure the unattended PowerPivot data refresh account</span></span>  
 <span data-ttu-id="28e48-134">每個 PowerPivot 服務應用程式僅能設定一個無人看管的 PowerPivot 資料重新整理帳戶。</span><span class="sxs-lookup"><span data-stu-id="28e48-134">You can configure only one PowerPivot unattended data refresh account for each PowerPivot service application.</span></span> <span data-ttu-id="28e48-135">帳戶資訊儲存在目標應用程式的 Secure Store Service 中，而且該服務設為預先定義的 Windows 網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="28e48-135">Account information is stored in Secure Store Service in a target application that is set to a predefined Windows domain user account.</span></span> <span data-ttu-id="28e48-136">建立目標應用程式之後，您就可以在 PowerPivot 服務應用程式的組態頁面中，將其指定為 PowerPivot 資料重新整理帳戶。</span><span class="sxs-lookup"><span data-stu-id="28e48-136">Once the target application is created, you can specify it as the PowerPivot data refresh account in the configuration pages of a PowerPivot service application.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="28e48-137">使用無人看管的資料重新整理帳戶執行資料重新整理時，使用方式報告與資料重新整理記錄會針對用於無人看管之資料重新整理的 Windows 使用者帳戶進行記錄。</span><span class="sxs-lookup"><span data-stu-id="28e48-137">When data refresh is performed under the unattended data refresh account, usage reporting and data refresh history is recorded against the Windows user account used for unattended data refresh.</span></span> <span data-ttu-id="28e48-138">如果您需要要求資料重新整理或擁有排程之個人的更正確記錄，請考慮用於執行資料重新整理的其中一個其他選項。</span><span class="sxs-lookup"><span data-stu-id="28e48-138">If you require a more accurate record of the individuals who are requesting data refresh or who own schedules, consider one of the other options for running data refresh.</span></span> <span data-ttu-id="28e48-139">換句話說，讓使者指定自己的認證 (這是預設值)，或建立其他目標應用程式來儲存您要用於資料重新整理用途的所有 Windows 認證。</span><span class="sxs-lookup"><span data-stu-id="28e48-139">Namely, having users specify their own credentials (this is the default), or creating additional target applications for storing any Windows credentials that you want to use for data refresh purposes.</span></span> <span data-ttu-id="28e48-140">如需詳細資訊，請參閱[設定 PowerPivot 資料重新整理的預存認證 &#40;PowerPivot for SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="28e48-140">For more information, see [Configure Stored Credentials for PowerPivot Data Refresh &#40;PowerPivot for SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md).</span></span>  
  
 <span data-ttu-id="28e48-141">建立無人看管的資料重新整理帳戶有五部分。</span><span class="sxs-lookup"><span data-stu-id="28e48-141">There are five parts to creating the unattended data refresh account.</span></span>  
  
-   <span data-ttu-id="28e48-142">在 Secure Store Service 中建立帳戶的目標應用程式，然後指定認證。</span><span class="sxs-lookup"><span data-stu-id="28e48-142">Create a target application in Secure Store Service for the account and specify the credentials.</span></span>  
  
-   <span data-ttu-id="28e48-143">在 PowerPivot 伺服器組態頁面中，針對無人看管的資料重新整理帳戶指定目標應用程式識別碼。</span><span class="sxs-lookup"><span data-stu-id="28e48-143">Specify the target application ID for the unattended data refresh account in the PowerPivot server configuration page.</span></span>  
  
-   <span data-ttu-id="28e48-144">授與「參與」權限給帳戶。</span><span class="sxs-lookup"><span data-stu-id="28e48-144">Grant Contribute permissions to the account.</span></span>  
  
-   <span data-ttu-id="28e48-145">授與帳戶讀取權限，以便在資料重新整理期間存取外部資料來源。</span><span class="sxs-lookup"><span data-stu-id="28e48-145">Grant the account read permissions to access external data sources during data refresh.</span></span>  
  
-   <span data-ttu-id="28e48-146">針對已發行的 PowerPivot 活頁簿，確認在 [管理資料重新整理] 排程頁面中可以使用該帳戶。</span><span class="sxs-lookup"><span data-stu-id="28e48-146">Verify the account is available in the Manage Data Refresh schedule page for a published PowerPivot workbook.</span></span>  
  
###  <a name="step-1-create-a-target-application-and-set-the-credentials"></a><a name="bkmk_create"></a><span data-ttu-id="28e48-147">步驟1：建立目標應用程式並設定認證</span><span class="sxs-lookup"><span data-stu-id="28e48-147">Step 1: Create a target application and set the credentials</span></span>  
  
1.  <span data-ttu-id="28e48-148">在 [管理中心] 的 [應用程式管理] 中，按一下 **[管理服務應用程式]** 。</span><span class="sxs-lookup"><span data-stu-id="28e48-148">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="28e48-149">按一下 [ **Secure Store Service**]。</span><span class="sxs-lookup"><span data-stu-id="28e48-149">Click **Secure Store Service**.</span></span>  
  
3.  <span data-ttu-id="28e48-150">在 [管理目標應用程式] 中，按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="28e48-150">In Manage Target Applications, click **New**.</span></span>  
  
4.  <span data-ttu-id="28e48-151">在 [目標應用程式識別碼] 中，輸入**PowerPivotDataRefresh**。</span><span class="sxs-lookup"><span data-stu-id="28e48-151">In Target application ID, type **PowerPivotDataRefresh**.</span></span>  
  
5.  <span data-ttu-id="28e48-152">在 [顯示名稱] 中，輸入**PowerPivot Data Refresh**。</span><span class="sxs-lookup"><span data-stu-id="28e48-152">In Display Name, type **PowerPivot Data Refresh**.</span></span>  
  
6.  <span data-ttu-id="28e48-153">在 [連絡人電子郵件] 中，輸入您的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="28e48-153">In Contact Email, type your e-mail address.</span></span>  
  
7.  <span data-ttu-id="28e48-154">在 [目標應用程式類型] 中，選取 [**個人**]。</span><span class="sxs-lookup"><span data-stu-id="28e48-154">In Target Application Type, select **Individual**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="28e48-155">在此案例中指定 [個別] 帳戶類型是正確的，因為只有 PowerPivot 服務應用程式才會要求 PowerPivot 無人看管的資料重新整理帳戶的認證。</span><span class="sxs-lookup"><span data-stu-id="28e48-155">Specifying an Individual account type is correct for this scenario because only the PowerPivot service application will request the credentials of the PowerPivot unattended data refresh account.</span></span> <span data-ttu-id="28e48-156">在實際情況中，此服務應用程式是唯一會使用無人看管的資料重新整理帳戶的使用者，因此對於此目標應用程式而言，[個別] 帳戶類別是最佳的選擇。</span><span class="sxs-lookup"><span data-stu-id="28e48-156">In practice, the service application is the sole user of the unattended data refresh account, making the Individual account type the best choice for this target application.</span></span>  
  
8.  <span data-ttu-id="28e48-157">略過目標應用程式的網頁 URL。</span><span class="sxs-lookup"><span data-stu-id="28e48-157">Skip Target Application Page URL.</span></span> <span data-ttu-id="28e48-158">PowerPivot 資料重新整理不會使用它。</span><span class="sxs-lookup"><span data-stu-id="28e48-158">PowerPivot data refresh does not use it.</span></span>  
  
9. <span data-ttu-id="28e48-159">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="28e48-159">Click **Next**.</span></span>  
  
10. <span data-ttu-id="28e48-160">在 [**指定 Secure Store 目標應用程式的認證欄位**] 頁面中，接受預設值。</span><span class="sxs-lookup"><span data-stu-id="28e48-160">In the **Specify the credentials fields for your Secure Store Target application** page, accept the default values.</span></span> <span data-ttu-id="28e48-161">欄位名稱和類型應該是 Windows 使用者名稱和 Windows 密碼。</span><span class="sxs-lookup"><span data-stu-id="28e48-161">Field names and types should be Windows User Name and Windows Password</span></span>  
  
11. <span data-ttu-id="28e48-162">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="28e48-162">Click **Next**.</span></span>  
  
12. <span data-ttu-id="28e48-163">在 [目標應用程式管理員]，指定 PowerPivot 服務應用程式的應用程式集區識別。</span><span class="sxs-lookup"><span data-stu-id="28e48-163">In Target Application Administrators, specify the application pool identity of the PowerPivot service application.</span></span> <span data-ttu-id="28e48-164">服務需要 [**完全控制**] 許可權，才能在執行時間捕獲自動資料重新整理帳戶資訊。</span><span class="sxs-lookup"><span data-stu-id="28e48-164">The service requires **Full Control** permissions so that it can retrieve unattended data refresh account information at run time.</span></span> <span data-ttu-id="28e48-165">此外，請針對應該擁有應用程式設定管理存取權的任何其他 SharePoint 使用者指定 Windows 網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="28e48-165">In addition, specify the Windows domain user accounts of any other SharePoint user who should have administrative access to the application settings.</span></span>  
  
13. <span data-ttu-id="28e48-166">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="28e48-166">Click **OK**.</span></span>  
  
14. <span data-ttu-id="28e48-167">選取您剛才建立的目標應用程式，按一下向下箭號，然後選取 [**設定認證]。**</span><span class="sxs-lookup"><span data-stu-id="28e48-167">Select the target application you just created, click the down arrow and select **Set Credentials.**</span></span>  
  
15. <span data-ttu-id="28e48-168">在 [**認證擁有**者] 中，輸入您想要擁有更新認證之許可權的 Windows 網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="28e48-168">In **Credential Owners**, type a Windows domain user account that you want to have permissions to update the credentials.</span></span> <span data-ttu-id="28e48-169">認證會用於資料的新動作，而**認證擁有**者具有修改認證的許可權。</span><span class="sxs-lookup"><span data-stu-id="28e48-169">The credentials are used for data fresh actions and the **Credential Owners** have permissions to modify the credentials.</span></span>  
  
16. <span data-ttu-id="28e48-170">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="28e48-170">Click **OK**.</span></span>  
  
###  <a name="step-2-specify-the-unattended-account-in-powerpivot-server-configuration-pages"></a><a name="bkmk_specifyUA"></a><span data-ttu-id="28e48-171">步驟2：在 PowerPivot 服務器設定頁面中指定自動帳戶</span><span class="sxs-lookup"><span data-stu-id="28e48-171">Step 2: Specify the unattended account in PowerPivot server configuration pages</span></span>  
  
1.  <span data-ttu-id="28e48-172">在 [管理中心] 的 [應用程式管理] 中，按一下 **[管理服務應用程式]** 。</span><span class="sxs-lookup"><span data-stu-id="28e48-172">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="28e48-173">尋找 PowerPivot 服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="28e48-173">Find the PowerPivot Service application.</span></span> <span data-ttu-id="28e48-174">您可以依其類型來識別服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="28e48-174">You can identify a service application by its type.</span></span> <span data-ttu-id="28e48-175">PowerPivot 服務應用程式類型為 **[PowerPivot 服務應用程式]**。</span><span class="sxs-lookup"><span data-stu-id="28e48-175">A PowerPivot service application type is **PowerPivot Service Application**.</span></span>  
  
3.  <span data-ttu-id="28e48-176">按一下 PowerPivot 服務應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="28e48-176">Click the PowerPivot service application name.</span></span> <span data-ttu-id="28e48-177">等待 PowerPivot 管理儀表板出現。</span><span class="sxs-lookup"><span data-stu-id="28e48-177">Wait for the PowerPivot Management Dashboard to appear.</span></span>  
  
4.  <span data-ttu-id="28e48-178">在 [動作] 中，按一下右上角的 [**設定服務應用程式設定**]。</span><span class="sxs-lookup"><span data-stu-id="28e48-178">In Actions, in the top right corner, click **Configure service application settings**.</span></span>  
  
5.  <span data-ttu-id="28e48-179">在 [資料重新整理] 的 [PowerPivot 無人看管的資料重新整理帳戶] 中，輸入您在上一個步驟建立的目標應用程式識別碼： **PowerPivotDataRefresh**。</span><span class="sxs-lookup"><span data-stu-id="28e48-179">In Data Refresh, in PowerPivot Unattended Data Refresh Account, type the target application ID you created in a previous step: **PowerPivotDataRefresh**.</span></span>  
  
6.  <span data-ttu-id="28e48-180">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="28e48-180">Click **OK**.</span></span>  
  
###  <a name="step-3-grant-contribute-permissions-to-the-account"></a><a name="bkmk_grant"></a><span data-ttu-id="28e48-181">步驟3：授與帳戶的「參與」許可權</span><span class="sxs-lookup"><span data-stu-id="28e48-181">Step 3: Grant contribute permissions to the account</span></span>  
 <span data-ttu-id="28e48-182">在您可以使用 PowerPivot 無人看管的資料重新整理帳戶之前，必須在該帳戶所使用的任何 PowerPivot 活頁簿上指派「參與」權限給它。</span><span class="sxs-lookup"><span data-stu-id="28e48-182">Before you can use the PowerPivot unattended data refresh account, it must be assigned Contribute permissions on any PowerPivot workbook for which it is used.</span></span> <span data-ttu-id="28e48-183">您需要這個權限等級才能從文件庫開啟活頁簿，然後在重新整理資料之後，將其存回文件庫。</span><span class="sxs-lookup"><span data-stu-id="28e48-183">This permission level is necessary to open the workbook from a library and then save it back to the library after the data is refreshed.</span></span>  
  
 <span data-ttu-id="28e48-184">指派權限是由網站集合管理員所執行的步驟。</span><span class="sxs-lookup"><span data-stu-id="28e48-184">Assigning permissions is a step that is performed by the site collection administrator.</span></span> <span data-ttu-id="28e48-185">您可以在根網站集合或根網站集合底下的任何層級 (包括個別文件和項目) 指派 SharePoint 權限。</span><span class="sxs-lookup"><span data-stu-id="28e48-185">SharePoint permissions can be assigned at the root site collection or at any level below that, including on individual documents and items.</span></span> <span data-ttu-id="28e48-186">設定權限的方式將隨著細緻程度而有所不同。</span><span class="sxs-lookup"><span data-stu-id="28e48-186">How you set permissions will vary depending on how granular you need them to be.</span></span> <span data-ttu-id="28e48-187">下列步驟示範授與權限的其中一個方法。</span><span class="sxs-lookup"><span data-stu-id="28e48-187">The following steps show you one approach for granting permissions.</span></span>  
  
1.  <span data-ttu-id="28e48-188">在 SharePoint 網站的 [網站動作] 中，按一下 [**網站許可權**]。</span><span class="sxs-lookup"><span data-stu-id="28e48-188">On a SharePoint site, in Site Actions, click **Site Permissions**.</span></span>  
  
2.  <span data-ttu-id="28e48-189">按一下 [授與權限]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="28e48-189">Click **Grant Permissions**.</span></span>  
  
3.  <span data-ttu-id="28e48-190">在 [選取使用者] 中，輸入您指定為 PowerPivot 無人看管的帳戶之 Windows 網域使用者帳戶的名稱。</span><span class="sxs-lookup"><span data-stu-id="28e48-190">In Select users, type the name of the Windows domain user account that you designated as the PowerPivot unattended account.</span></span> <span data-ttu-id="28e48-191">這是您在目標應用程式的 Secure Store Service 中指定之 Windows 網域使用者帳戶的名稱。</span><span class="sxs-lookup"><span data-stu-id="28e48-191">This is the name of the Windows domain user account that you specified in target application in Secure Store Service.</span></span>  
  
4.  <span data-ttu-id="28e48-192">在 [授與許可權] 中，選取 **[直接授與使用者許可權**]。</span><span class="sxs-lookup"><span data-stu-id="28e48-192">In Grant Permissions, select **Grant users permission directly**.</span></span>  
  
5.  <span data-ttu-id="28e48-193">選取 [**參與**]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="28e48-193">Select **Contribute**, and then click **OK**.</span></span>  
  
###  <a name="step-4-grant-read-permissions-to-access-external-data-sources-used-in-data-refresh"></a><a name="bkmk_dbread"></a><span data-ttu-id="28e48-194">步驟4：授與讀取權限以存取資料重新整理時所使用的外部資料源</span><span class="sxs-lookup"><span data-stu-id="28e48-194">Step 4: Grant read permissions to access external data sources used in data refresh</span></span>  
 <span data-ttu-id="28e48-195">當資料匯入至 PowerPivot 活頁簿時，外部資料連接通常是以信任連接或是以使用目前使用者身分連接至資料來源的模擬連接為基礎。</span><span class="sxs-lookup"><span data-stu-id="28e48-195">When importing data into a PowerPivot workbook, connections to external data are often based on trusted connections or impersonated connections that use the identity of the current user to connect to the data source.</span></span> <span data-ttu-id="28e48-196">這些類型的連接只能在目前使用者有讀取所匯入之資料的權限時使用。</span><span class="sxs-lookup"><span data-stu-id="28e48-196">These types of connections work only when the current user has permission to read the data that he or she is importing.</span></span>  
  
 <span data-ttu-id="28e48-197">在資料重新整理案例中，用來匯入資料的相同連接字串現在會重複使用來重新整理資料。</span><span class="sxs-lookup"><span data-stu-id="28e48-197">In a data refresh scenario, the same connection string that was used to import data is now reused to refresh the data.</span></span> <span data-ttu-id="28e48-198">如果連接字串假設目前使用者 (例如，包含 Integrated_Security=SSPI 的字串)，PowerPivot 系統服務就會將 PowerPivot 無人看管資料重新整理帳戶的使用者身分當做目前使用者。</span><span class="sxs-lookup"><span data-stu-id="28e48-198">If the connection string assumes the current user (for example, a string that includes Integrated_Security=SSPI), then the PowerPivot System Service will pass the user identity of the PowerPivot unattended data refresh account as the current user.</span></span> <span data-ttu-id="28e48-199">此連接只在 PowerPivot 無人看管的資料重新整理帳戶有讀取外部資料來源的權限時才會成功。</span><span class="sxs-lookup"><span data-stu-id="28e48-199">This connection will only succeed if the PowerPivot unattended data refresh account has read permissions on the external data source.</span></span>  
  
 <span data-ttu-id="28e48-200">因此，您必須將 PowerPivot 無人看管的資料重新整理帳戶所執行之任何資料重新整理作業所要使用的所有外部資料來源的唯讀權限，授與此帳戶。</span><span class="sxs-lookup"><span data-stu-id="28e48-200">For this reason, you must grant the PowerPivot unattended data refresh account read-only permissions on all of the external data sources that are used in any data refresh operation that runs under the unattended account.</span></span>  
  
 <span data-ttu-id="28e48-201">如果您是組織中使用的資料來源的系統管理員，可以建立登入並指定所需的權限。</span><span class="sxs-lookup"><span data-stu-id="28e48-201">If you are an administrator of the data sources used in your organization, you can create a login and assign the necessary permissions.</span></span> <span data-ttu-id="28e48-202">否則，您必須連絡資料擁有者並提供帳戶資訊。</span><span class="sxs-lookup"><span data-stu-id="28e48-202">Otherwise, you must contact the data owners and provide the account information.</span></span> <span data-ttu-id="28e48-203">請務必指定對應至 PowerPivot 無人看管資料重新整理帳戶的 Windows 網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="28e48-203">Be sure to specify the Windows domain user account that maps to the PowerPivot unattended data refresh account.</span></span> <span data-ttu-id="28e48-204">這是您在本主題的「 (步驟 1) ：建立目標應用程式並設定認證」中指定的帳號。</span><span class="sxs-lookup"><span data-stu-id="28e48-204">This is the account you specified in "(Step 1): Create a target application and set the credentials" in this topic.</span></span>  
  
###  <a name="step-5-verify-account-availability-in-data-refresh-configuration-pages"></a><a name="bkmk_verify"></a><span data-ttu-id="28e48-205">步驟5：在資料重新整理設定頁面中確認帳戶可用性</span><span class="sxs-lookup"><span data-stu-id="28e48-205">Step 5: Verify account availability in data refresh configuration pages</span></span>  
  
1.  <span data-ttu-id="28e48-206">為包含 PowerPivot 資料之已發行的活頁簿，開啟資料重新整理組態頁面。</span><span class="sxs-lookup"><span data-stu-id="28e48-206">Open a data refresh configuration page for a published workbook that contains PowerPivot data.</span></span> <span data-ttu-id="28e48-207">如需如何開啟頁面的指示，請參閱[排程資料重新整理 &#40;PowerPivot for SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="28e48-207">For instructions on how to open the page, see [Schedule a Data Refresh &#40;PowerPivot for SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md).</span></span>  
  
2.  <span data-ttu-id="28e48-208">確認已在 [資料重新整理設定] 頁面中，啟用 [**使用系統管理員所設定的資料**重新整理帳戶] 選項。</span><span class="sxs-lookup"><span data-stu-id="28e48-208">Verify that the **Use the data refresh account configured by the administrator** option is enabled in the data refresh configuration page.</span></span>  
  
3.  <span data-ttu-id="28e48-209">選取 [**同時**儘快重新整理] 核取方塊，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="28e48-209">Select the **Also refresh as soon as possible** checkbox, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="28e48-210">在包含活頁簿的文件庫中，選取活頁簿，按一下向右顯示的向下箭號，然後選取 [**管理 PowerPivot 資料**重新整理]。</span><span class="sxs-lookup"><span data-stu-id="28e48-210">In the library that contains the workbook, select the workbook, click the down arrow that appears to right, and then select **Manage PowerPivot Data Refresh**.</span></span> <span data-ttu-id="28e48-211">若資料重新整理作業傳回的資料量十分龐大，可能需要等候數分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="28e48-211">You might need to wait several minutes if the data refresh job is returning a large amount of data.</span></span>  
  
 <span data-ttu-id="28e48-212">如果發生錯誤，您可以按一下 [資料重新整理記錄] 頁面中的 [設定**排程**]，以嘗試不同的認證。</span><span class="sxs-lookup"><span data-stu-id="28e48-212">If an error occurs, you can click **Configure schedule** in the data refresh history page to try different credentials.</span></span> <span data-ttu-id="28e48-213">您也可能需要檢查原始活頁簿中的資料來源連接資訊，以查看資料重新整理期間所使用的連接字串。</span><span class="sxs-lookup"><span data-stu-id="28e48-213">You might also need to inspect the data source connection information in the original workbook to view the connection string that is used during data refresh.</span></span> <span data-ttu-id="28e48-214">連接字串所提供的伺服器位置與資料庫資訊，可讓您用於疑難排解問題。</span><span class="sxs-lookup"><span data-stu-id="28e48-214">The connection string will provide information about the server location and database that you can use to troubleshoot the problem.</span></span>  
  
 <span data-ttu-id="28e48-215">如需有關疑難排解的詳細資訊，請參閱 TechNet Wiki 上的[疑難排解 PowerPivot 資料](https://go.microsoft.com/fwlink/p/?LinkID=223279)重新整理。</span><span class="sxs-lookup"><span data-stu-id="28e48-215">For more information about troubleshooting, see [Troubleshooting PowerPivot Data Refresh](https://go.microsoft.com/fwlink/p/?LinkID=223279) on the TechNet Wiki.</span></span>  
  
##  <a name="using-the-powerpivot-unattended-data-refresh-account"></a><a name="bkmk_use"></a><span data-ttu-id="28e48-216">使用 PowerPivot 無人看管的資料重新整理帳戶</span><span class="sxs-lookup"><span data-stu-id="28e48-216">Using the PowerPivot Unattended Data Refresh Account</span></span>  
 <span data-ttu-id="28e48-217">在 PowerPivot 資料重新整理排程頁面上所提供的三個認證選項中，只有第一個選項會對應到無人看管的資料重新整理帳戶。</span><span class="sxs-lookup"><span data-stu-id="28e48-217">Of the three credential options in PowerPivot data refresh scheduling page, only the first one corresponds to the unattended data refresh account.</span></span> <span data-ttu-id="28e48-218">設定資料重新整理排程時，請務必選取此選項。</span><span class="sxs-lookup"><span data-stu-id="28e48-218">Be sure to select this option when setting up the data refresh schedule.</span></span>  
  
 <span data-ttu-id="28e48-219">![SSAS_PowerpivotKJ_DataRefreshCreds](media/ssas-powerpivotkj-datarefreshcreds.gif "SSAS_PowerpivotKJ_DataRefreshCreds")</span><span class="sxs-lookup"><span data-stu-id="28e48-219">![SSAS_PowerpivotKJ_DataRefreshCreds](media/ssas-powerpivotkj-datarefreshcreds.gif "SSAS_PowerpivotKJ_DataRefreshCreds")</span></span>  
  
 <span data-ttu-id="28e48-220">請勿使用第三個認證選項 (即需要您輸入目標應用程式識別碼的選項) 存取 PowerPivot 無人看管的資料重新整理帳戶。</span><span class="sxs-lookup"><span data-stu-id="28e48-220">Do not use the third credential option (the one that requires you to enter the target application ID) to access the PowerPivot unattended data refresh account.</span></span> <span data-ttu-id="28e48-221">此選項另外還會執行模擬檢查，若您嘗試將此選項用於 PowerPivot 無人看管的資料重新整理帳戶 (或任何使用 [個別] 帳戶類型的目標應用程式)，將會導致驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="28e48-221">There is an additional impersonation check that is performed with that option that will result in a validation error if you try to use it with the PowerPivot unattended data refresh account (or any target application that is based on the Individual account type).</span></span> <span data-ttu-id="28e48-222">如需如何使用第三個選項的詳細資訊，請參閱[設定 PowerPivot 資料重新整理的預存認證 &#40;PowerPivot for SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="28e48-222">For more information about how to use the third option, see [Configure Stored Credentials for PowerPivot Data Refresh &#40;PowerPivot for SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md).</span></span>  
  
##  <a name="update-the-credentials-used-by-an-existing-powerpivot-unattended-data-refresh-account"></a><a name="bkmk_editUA"></a><span data-ttu-id="28e48-223">更新現有 PowerPivot 無人看管的資料重新整理帳戶所使用的認證</span><span class="sxs-lookup"><span data-stu-id="28e48-223">Update the credentials used by an existing PowerPivot unattended data refresh account</span></span>  
 <span data-ttu-id="28e48-224">若安裝程式或管理員已設定了無人看管的資料重新整理帳戶，您即可藉由編輯儲存認證的目標應用程式來更新使用者名稱或密碼。</span><span class="sxs-lookup"><span data-stu-id="28e48-224">If the unattended data refresh account is already configured through setup or by an administrator, you can update the user name or password by editing the target application that stores the credentials.</span></span> <span data-ttu-id="28e48-225">請注意，當您編輯 Secure Store Service 中的認證時，將不會顯示先前與 PowerPivot 無人看管的資料重新整理帳戶相關聯的原始 Windows 識別。</span><span class="sxs-lookup"><span data-stu-id="28e48-225">Note that the original Windows identity that was previously associated with PowerPivot unattended data refresh account will not be visible when you edit the credentials in Secure Store Service.</span></span> <span data-ttu-id="28e48-226">不論您要更新過期密碼，或要指定不同的帳戶，皆必須在 Secure Store Service 中重新輸入該目標應用程式的使用者名稱及密碼。</span><span class="sxs-lookup"><span data-stu-id="28e48-226">Whether you are updating an expired password or specifying different account, you must always re-type both the user name and password for that target application in Secure Store Service.</span></span>  
  
1.  <span data-ttu-id="28e48-227">在 [管理中心] 的 [應用程式管理] 中，按一下 **[管理服務應用程式]** 。</span><span class="sxs-lookup"><span data-stu-id="28e48-227">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="28e48-228">按一下 [ **Secure Store Service**]。</span><span class="sxs-lookup"><span data-stu-id="28e48-228">Click **Secure Store Service**.</span></span>  
  
3.  <span data-ttu-id="28e48-229">選取 [ **PowerPivotDataRefresh**] 旁的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="28e48-229">Select the checkbox next to **PowerPivotDataRefresh**.</span></span>  
  
4.  <span data-ttu-id="28e48-230">在 [認證] 中，按一下 [**設定**]。</span><span class="sxs-lookup"><span data-stu-id="28e48-230">In Credentials, click **Set**.</span></span>  
  
5.  <span data-ttu-id="28e48-231">在 [**認證擁有**者] 中，輸入您想要擁有更新認證之許可權的 Windows 網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="28e48-231">In **Credential Owners**, type a Windows domain user account that you want to have permissions to update the credentials.</span></span> <span data-ttu-id="28e48-232">認證會用於資料的新動作，而**認證擁有**者具有修改認證的許可權。</span><span class="sxs-lookup"><span data-stu-id="28e48-232">The credentials are used for data fresh actions and the **Credential Owners** have permissions to modify the credentials.</span></span>  
  
6.  <span data-ttu-id="28e48-233">在 [使用者名稱] 中，輸入將成為自動資料重新整理認證一部分的 Windows 網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="28e48-233">In User Name, type the Windows domain user account that will be part of the unattended data refresh credentials.</span></span>  
  
7.  <span data-ttu-id="28e48-234">在 [密碼] 中，輸入帳戶的密碼，然後重新輸入密碼進行確認。</span><span class="sxs-lookup"><span data-stu-id="28e48-234">In Password, type the password for the account, and then re-type it to confirm the password.</span></span>  
  
8.  <span data-ttu-id="28e48-235">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="28e48-235">Click **OK**.</span></span>  
  
 <span data-ttu-id="28e48-236">若同時變更了密碼與使用者名稱，您很可能需要執行其他的組態步驟 (例如授與外部資料來源的讀取權限及 SharePoint 權限)，才可更新 PowerPivot 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="28e48-236">If you are changing not just the password, but the account user name as well, you will most likely need to perform additional configuration steps, such as granting read permissions to external data sources and SharePoint permissions to update the PowerPivot workbook.</span></span> <span data-ttu-id="28e48-237">如需相關指示，請移至 PowerPivot 無人看管的資料重新整理帳戶設定中的這個步驟：[步驟3：授與帳戶的「參與」許可權](#bkmk_grant)，然後繼續進行所有剩餘的步驟，最後才會確認帳戶已正確設定。</span><span class="sxs-lookup"><span data-stu-id="28e48-237">For instructions, go to this step in PowerPivot unattended data refresh account configuration: [Step 3: Grant contribute permissions to the account](#bkmk_grant), and then continue with all remaining steps, concluding with verification that the account is configured correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28e48-238">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28e48-238">See Also</span></span>  
 <span data-ttu-id="28e48-239">[PowerPivot 資料重新整理與 SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md) </span><span class="sxs-lookup"><span data-stu-id="28e48-239">[PowerPivot Data Refresh with SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md) </span></span>  
 <span data-ttu-id="28e48-240">[排程資料重新整理 &#40;PowerPivot for SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="28e48-240">[Schedule a Data Refresh &#40;PowerPivot for SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md) </span></span>  
 [<span data-ttu-id="28e48-241">PowerPivot 資料重新整理</span><span class="sxs-lookup"><span data-stu-id="28e48-241">PowerPivot Data Refresh</span></span>](power-pivot-sharepoint/power-pivot-data-refresh.md)  
  
  
