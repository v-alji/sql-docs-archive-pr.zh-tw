---
title: 設定 PowerPivot 資料重新整理的預存認證 (PowerPivot for SharePoint) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 987eff0f-bcfe-4bbd-81e0-9aca993a2a75
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5a1350c5d776891397401e9d3127b7849281b106
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593039"
---
# <a name="configure-stored-credentials-for-powerpivot-data-refresh-powerpivot-for-sharepoint"></a><span data-ttu-id="d7227-102">設定 PowerPivot 資料重新整理的預存認證 (PowerPivot for SharePoint)</span><span class="sxs-lookup"><span data-stu-id="d7227-102">Configure Stored Credentials for PowerPivot Data Refresh (PowerPivot for SharePoint)</span></span>
  <span data-ttu-id="d7227-103">只要您在 Secure Store Service 中建立目標應用程式來儲存想要使用的認證，PowerPivot 資料重新整理作業就可以在任何 Windows 使用者帳戶之下執行。</span><span class="sxs-lookup"><span data-stu-id="d7227-103">PowerPivot data refresh jobs can run under any Windows user account as long as you create a target application in Secure Store Service to store the credentials you want to use.</span></span> <span data-ttu-id="d7227-104">同樣地，若想要提供的資料庫登入不同於最初用於匯入 PowerPivot for Excel 資料的登入，可以將這些認證對應至 Secure Store Service 目標應用程式，然後在資料重新整理排程中指定該目標應用程式。</span><span class="sxs-lookup"><span data-stu-id="d7227-104">Similarly, if you want to provide a database login that varies from the one used to originally import the data in PowerPivot for Excel, you can map those credentials to a Secure Store Service target application, and then specify that target application in a data refresh schedule.</span></span>  
  
 <span data-ttu-id="d7227-105">**[!INCLUDE[applies](../includes/applies-md.md)]** SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="d7227-105">**[!INCLUDE[applies](../includes/applies-md.md)]**  SharePoint 2010</span></span>  
  
 <span data-ttu-id="d7227-106">當您依照本主題的指示進行之後，即可使用 PowerPivot 資料重新整理排程頁面中的認證選項，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d7227-106">After you follow the instructions in this topic, you will be able to use the following credentials option in the PowerPivot data refresh schedule page:</span></span>  
  
 <span data-ttu-id="d7227-107">![SSAS_PowerPivotDataRefreshCreds_Stored](media/ssas-powerpivotdatarefreshcreds-stored.gif "SSAS_PowerPivotDataRefreshCreds_Stored")</span><span class="sxs-lookup"><span data-stu-id="d7227-107">![SSAS_PowerPivotDataRefreshCreds_Stored](media/ssas-powerpivotdatarefreshcreds-stored.gif "SSAS_PowerPivotDataRefreshCreds_Stored")</span></span>  
  
 <span data-ttu-id="d7227-108">本主題說明如何設定 SharePoint 2010 伺服器陣列中用於 PowerPivot 資料重新整理的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="d7227-108">This topic explains how to set up the user names and passwords that are used for PowerPivot data refresh in a SharePoint 2010 farm.</span></span> <span data-ttu-id="d7227-109">您必須先啟用 Secure Store Service 並產生主要金鑰，然後才能使用這些步驟。</span><span class="sxs-lookup"><span data-stu-id="d7227-109">Before you can use these steps, you must have enabled Secure Store Service and generated a master key.</span></span> <span data-ttu-id="d7227-110">如需詳細資訊，請參閱[PowerPivot 資料重新整理與 SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md)</span><span class="sxs-lookup"><span data-stu-id="d7227-110">For more information, see [PowerPivot Data Refresh with SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md)</span></span>  
  
 <span data-ttu-id="d7227-111">本主題包含下列幾節：</span><span class="sxs-lookup"><span data-stu-id="d7227-111">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="d7227-112">針對資料重新整理設定任何 Windows 帳戶</span><span class="sxs-lookup"><span data-stu-id="d7227-112">Configure any Windows account for data refresh</span></span>](#configAny)  
  
 [<span data-ttu-id="d7227-113">針對存取外部或協力廠商資料來源設定預先定義的帳戶</span><span class="sxs-lookup"><span data-stu-id="d7227-113">Configure a predefined account for accessing external or third-party data sources</span></span>](#config3rd)  
  
 <span data-ttu-id="d7227-114">如果您在設定或使用資料重新整理時遇到問題，請參閱 TechNet wiki 上的[疑難排解 PowerPivot 資料](https://go.microsoft.com/fwlink/?LinkID=223279)重新整理頁面，以取得可能的解決方案。</span><span class="sxs-lookup"><span data-stu-id="d7227-114">If you have problems configuring or using data refresh, refer to the [Troubleshooting PowerPivot Data Refresh](https://go.microsoft.com/fwlink/?LinkID=223279) page on the TechNet wiki for possible solutions.</span></span>  
  
##  <a name="configure-any-windows-account-for-data-refresh"></a><a name="configAny"></a><span data-ttu-id="d7227-115">設定任何 Windows 帳戶以進行資料重新整理</span><span class="sxs-lookup"><span data-stu-id="d7227-115">Configure any Windows account for data refresh</span></span>  
 <span data-ttu-id="d7227-116">當 SharePoint 使用者定義資料重新整理排程時，該使用者必須指定用來執行資料重新整理的使用者識別。</span><span class="sxs-lookup"><span data-stu-id="d7227-116">When a SharePoint user defines a data refresh schedule, he or she must specify the user identity under which data refresh is performed.</span></span> <span data-ttu-id="d7227-117">您可以選擇選取 PowerPivot 無人看管的資料重新整理帳戶，也可輸入使用者的 Windows 網域使用者帳戶，或是輸入其他可以適用於資料重新整理的 Windows 使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="d7227-117">Options include selecting the PowerPivot unattended data refresh account, entering his or her Windows domain user account, or entering some other Windows user account that is valid for data refresh purposes.</span></span> <span data-ttu-id="d7227-118">本節中的步驟適用於最後一個選項：指定某些其他 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="d7227-118">The steps in this section are for the last option: specifying some other Windows account.</span></span>  
  
 <span data-ttu-id="d7227-119">如果您想要使用 PowerPivot 無人看管的資料重新整理帳戶 (適用於 SharePoint 的所有 PowerPivot 使用者) 或活頁簿擁有者之認證的替代方案，可能會選擇這種方式。</span><span class="sxs-lookup"><span data-stu-id="d7227-119">You might choose this approach if you want an alternative to using the PowerPivot unattended data refresh account (available to all PowerPivot users on SharePoint) or the credentials of the workbook owner.</span></span> <span data-ttu-id="d7227-120">例如，您可能會想要將一系列資料重新整理帳戶提供給不同的工作群組，以便協助您在組織層級中追蹤和管理資料重新整理活動。</span><span class="sxs-lookup"><span data-stu-id="d7227-120">For example, you might want to make a series of data refresh accounts available to different workgroups to help you track and manage data refresh activity at the organizational level.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d7227-121">使用此目標應用程式 (及所儲存之認證) 的人員和應用程式都必須列為應用程式的成員。</span><span class="sxs-lookup"><span data-stu-id="d7227-121">People and applications that use this target application (and the credentials that it stores) must be listed as members of the application.</span></span> <span data-ttu-id="d7227-122">您必須加入將使用目標應用程式之每個 PowerPivot 服務應用程式的識別、您的 Windows 帳戶，以及將在其資料重新整理排程中指定此目標應用程式之人員的群組或使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="d7227-122">You must add the identity of each PowerPivot service application that will use the target application, your Windows account, and the group or user accounts of people who will be specifying this target application in their data refresh schedules.</span></span> <span data-ttu-id="d7227-123">當您建立目標應用程式時，可以指定上述所有帳戶。</span><span class="sxs-lookup"><span data-stu-id="d7227-123">You can specify all of these accounts when you create the target application.</span></span> <span data-ttu-id="d7227-124">如果您不知道將需要存取此應用程式的所有使用者和群組帳戶，您可以在建立目標應用程式之後再加入它們。</span><span class="sxs-lookup"><span data-stu-id="d7227-124">If you do not know all of the user and group accounts that will require access to this application, you can add them later after the target application is created.</span></span>  
  
 <span data-ttu-id="d7227-125">設定資料重新整理的預存認證共有 4 個部分：</span><span class="sxs-lookup"><span data-stu-id="d7227-125">There are 4 parts to configuring stored credentials for data refresh:</span></span>  
  
-   <span data-ttu-id="d7227-126">建立用以儲存認證的目標應用程式。</span><span class="sxs-lookup"><span data-stu-id="d7227-126">Create the target application that stores the credentials.</span></span>  
  
-   <span data-ttu-id="d7227-127">授與「參與」權限給帳戶。</span><span class="sxs-lookup"><span data-stu-id="d7227-127">Grant Contribute permissions to the account.</span></span>  
  
-   <span data-ttu-id="d7227-128">授與帳戶讀取權限，以便在資料重新整理期間存取外部資料來源。</span><span class="sxs-lookup"><span data-stu-id="d7227-128">Grant the account read permissions to access external data sources during data refresh.</span></span>  
  
-   <span data-ttu-id="d7227-129">驗證當您在資料重新整理排程中指定此目標應用程式時，資料重新整理可否運作。</span><span class="sxs-lookup"><span data-stu-id="d7227-129">Verify that data refresh works when you specify this target application in a data refresh schedule.</span></span>  
  
### <a name="step-1-create-a-target-application"></a><span data-ttu-id="d7227-130">步驟 1：建立目標應用程式</span><span class="sxs-lookup"><span data-stu-id="d7227-130">Step 1: Create a target application</span></span>  
  
1.  <span data-ttu-id="d7227-131">在 [管理中心] 的 [應用程式管理] 中，按一下 **[管理服務應用程式]** 。</span><span class="sxs-lookup"><span data-stu-id="d7227-131">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="d7227-132">按一下 [ **Secure Store Service**]。</span><span class="sxs-lookup"><span data-stu-id="d7227-132">Click **Secure Store Service**.</span></span>  
  
3.  <span data-ttu-id="d7227-133">在 [管理目標應用程式] 中，按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="d7227-133">In Manage Target Applications, click **New**.</span></span>  
  
4.  <span data-ttu-id="d7227-134">在 [目標應用程式識別碼] 中，輸入文字字串。</span><span class="sxs-lookup"><span data-stu-id="d7227-134">In Target application ID, type a text string.</span></span> <span data-ttu-id="d7227-135">此字串必須是唯一的，但也應該容易記憶。</span><span class="sxs-lookup"><span data-stu-id="d7227-135">The string must be unique, but it should also be easy to remember.</span></span> <span data-ttu-id="d7227-136">每當使用者想要使用儲存在此應用程式中的認證時，將在資料重新整理排程頁面中輸入這個字串。</span><span class="sxs-lookup"><span data-stu-id="d7227-136">Users will type this string in data refresh schedule pages whenever they want to use the credentials that are stored in this application.</span></span>  
  
5.  <span data-ttu-id="d7227-137">在 [顯示名稱] 中，輸入描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="d7227-137">In Display Name, enter a descriptive name.</span></span> <span data-ttu-id="d7227-138">此名稱僅用於顯示用途，</span><span class="sxs-lookup"><span data-stu-id="d7227-138">This name is used for display purposes only.</span></span> <span data-ttu-id="d7227-139">而不是在資料重新整理排程中用來指定目標應用程式。</span><span class="sxs-lookup"><span data-stu-id="d7227-139">It is not used to specify the target application in a data refresh schedule.</span></span>  
  
6.  <span data-ttu-id="d7227-140">在 [連絡人電子郵件] 中，輸入您的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="d7227-140">In Contact Email, type your e-mail address.</span></span>  
  
7.  <span data-ttu-id="d7227-141">在 [目標應用程式類型] 中，選取 [**群組**]。</span><span class="sxs-lookup"><span data-stu-id="d7227-141">In Target Application Type, select **Group**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="d7227-142">您必須選擇群組帳戶類型，如此才能夠指定存取認證所需的所有使用者與服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="d7227-142">Choosing a Group account type is necessary because it allows you to specify all of the user and service accounts requesting access to the credentials.</span></span> <span data-ttu-id="d7227-143">PowerPivot 系統服務會檢查各項要求的要求者是否為目標應用程式的成員。</span><span class="sxs-lookup"><span data-stu-id="d7227-143">For each request, PowerPivot System Service verifies whether the requestor is a member of the target application.</span></span>  
  
8.  <span data-ttu-id="d7227-144">略過目標應用程式的網頁 URL。</span><span class="sxs-lookup"><span data-stu-id="d7227-144">Skip Target Application Page URL.</span></span> <span data-ttu-id="d7227-145">PowerPivot 資料重新整理不會使用它。</span><span class="sxs-lookup"><span data-stu-id="d7227-145">PowerPivot data refresh does not use it.</span></span>  
  
9. <span data-ttu-id="d7227-146">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="d7227-146">Click **Next**.</span></span>  
  
10. <span data-ttu-id="d7227-147">在 [**指定 Secure Store 目標應用程式的認證欄位**] 頁面中，接受預設值。</span><span class="sxs-lookup"><span data-stu-id="d7227-147">In the **Specify the credentials fields for your Secure Store Target application** page, accept the default values.</span></span> <span data-ttu-id="d7227-148">欄位名稱和類型應該是 Windows 使用者名稱和 Windows 密碼。</span><span class="sxs-lookup"><span data-stu-id="d7227-148">Field names and types should be Windows User Name and Windows Password.</span></span>  
  
11. <span data-ttu-id="d7227-149">按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="d7227-149">Click Next.</span></span>  
  
12. <span data-ttu-id="d7227-150">在 [目標應用程式管理員] 中，指定 SharePoint 使用者的 Windows 網域使用者帳戶，而該使用者必須具備目標應用程式的系統管理存取權 (例如新增或移除 [成員] 清單中之帳戶的能力)。</span><span class="sxs-lookup"><span data-stu-id="d7227-150">In Target Application Administrators, specify the Windows domain user accounts of SharePoint users who should have administrative access to target application settings (for example, the ability to add or remove accounts from the Members list).</span></span>  
  
13. <span data-ttu-id="d7227-151">在 [成員] 中，加入下列使用者和群組帳戶：</span><span class="sxs-lookup"><span data-stu-id="d7227-151">In Members, add the following user and group accounts:</span></span>  
  
    1.  <span data-ttu-id="d7227-152">將您的 Windows 使用者帳戶加入至 [成員] 清單中，做為建立應用程式的人員。</span><span class="sxs-lookup"><span data-stu-id="d7227-152">As the person creating the application, add your Windows user account to the Members list.</span></span>  
  
    2.  <span data-ttu-id="d7227-153">加入 PowerPivot 服務應用程式的應用程式集區識別，讓它能夠在資料重新整理排程為執行時擷取認證。</span><span class="sxs-lookup"><span data-stu-id="d7227-153">Add the application pool identity of the PowerPivot service application so that it can retrieve the credentials when data refresh is scheduled to run.</span></span> <span data-ttu-id="d7227-154">若要查看應用程式集區身分識別，請移至 [**管理服務應用程式**]，按一下 [名稱] 旁邊的空白處，選取 [PowerPivot 服務應用程式] (這會選取資料列) ，然後按一下 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="d7227-154">To view the application pool identity, go to **Manage service applications**, select the PowerPivot service application by clicking the empty space next to the name (this selects the row), and then click **Properties**.</span></span> <span data-ttu-id="d7227-155">出現在此頁面的安全性帳戶就是要當做目標應用程式成員加入的帳戶。</span><span class="sxs-lookup"><span data-stu-id="d7227-155">The security account that appears on this page is the account to add as a member of the target application.</span></span>  
  
    3.  <span data-ttu-id="d7227-156">加入將在資料重新整理排程中輸入此目標應用程式的 Windows 使用者和群組帳戶。</span><span class="sxs-lookup"><span data-stu-id="d7227-156">Add Windows user and group accounts that will be entering this target application in data refresh schedules.</span></span>  
  
14. <span data-ttu-id="d7227-157">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="d7227-157">Click **OK**.</span></span>  
  
15. <span data-ttu-id="d7227-158">選取您剛才建立的目標應用程式，按一下向下箭號，然後選取 [**設定認證]。**</span><span class="sxs-lookup"><span data-stu-id="d7227-158">Select the target application you just created, click the down arrow and select **Set Credentials.**</span></span>  
  
16. <span data-ttu-id="d7227-159">請注意，[認證擁有者] 中的認證擁有者清單為唯讀。</span><span class="sxs-lookup"><span data-stu-id="d7227-159">In Credential Owner, notice that the list of credential owners is read-only.</span></span> <span data-ttu-id="d7227-160">凡具有認證擁有權的帳戶，皆是目標應用程式的成員。</span><span class="sxs-lookup"><span data-stu-id="d7227-160">The accounts who have ownership over the credentials are the members of the target application.</span></span> <span data-ttu-id="d7227-161">若要新增或移除認證擁有者，必須先在目標應用程式的成員清單中新增或移除帳戶。</span><span class="sxs-lookup"><span data-stu-id="d7227-161">To add or remove a credential owner, you must add or remove accounts from the target application members list.</span></span>  
  
     <span data-ttu-id="d7227-162">在 [Windows 使用者名稱] 及 [Windows 密碼] 中，輸入要用於執行資料重新整理之 Windows 使用者帳戶的認證。</span><span class="sxs-lookup"><span data-stu-id="d7227-162">In Windows User Name and Windows Password, type credentials of Windows user account that will be used to run data refresh.</span></span>  
  
17. <span data-ttu-id="d7227-163">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="d7227-163">Click **OK**.</span></span>  
  
###  <a name="step-2-grant-contribute-permissions-to-the-account"></a><a name="bkmk_grant"></a><span data-ttu-id="d7227-164">步驟2：授與帳戶的「參與」許可權</span><span class="sxs-lookup"><span data-stu-id="d7227-164">Step 2: Grant Contribute permissions to the account</span></span>  
 <span data-ttu-id="d7227-165">帳戶必須先獲指派其所應用之任何 PowerPivot 活頁簿的「參與」權限，您才可使用預存認證。</span><span class="sxs-lookup"><span data-stu-id="d7227-165">Before you can use the stored credentials, the account must be assigned Contribute permissions on any PowerPivot workbook for which it is used.</span></span> <span data-ttu-id="d7227-166">您需要這個權限等級才能從文件庫開啟活頁簿，然後在重新整理資料之後，將其存回文件庫。</span><span class="sxs-lookup"><span data-stu-id="d7227-166">This permission level is necessary to open the workbook from a library and then save it back to the library after the data is refreshed.</span></span>  
  
 <span data-ttu-id="d7227-167">指派權限是由網站集合管理員所執行的步驟。</span><span class="sxs-lookup"><span data-stu-id="d7227-167">Assigning permissions is a step that is performed by the site collection administrator.</span></span> <span data-ttu-id="d7227-168">您可以在根網站集合或根網站集合底下的任何層級 (包括個別文件和項目) 指派 SharePoint 權限。</span><span class="sxs-lookup"><span data-stu-id="d7227-168">SharePoint permissions can be assigned at the root site collection or at any level below that, including on individual documents and items.</span></span> <span data-ttu-id="d7227-169">設定權限的方式將隨著細緻程度而有所不同。</span><span class="sxs-lookup"><span data-stu-id="d7227-169">How you set permissions will vary depending on how granular you need them to be.</span></span> <span data-ttu-id="d7227-170">下列步驟示範授與權限的其中一個方法。</span><span class="sxs-lookup"><span data-stu-id="d7227-170">The following steps show you one approach for granting permissions.</span></span>  
  
1.  <span data-ttu-id="d7227-171">在 SharePoint 網站的 [網站動作] 中，按一下 [**網站許可權**]。</span><span class="sxs-lookup"><span data-stu-id="d7227-171">On a SharePoint site, in Site Actions, click **Site Permissions**.</span></span>  
  
2.  <span data-ttu-id="d7227-172">按一下 [授與權限]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d7227-172">Click **Grant Permissions**.</span></span>  
  
3.  <span data-ttu-id="d7227-173">在 [選取使用者] 中，輸入您在目標應用程式中所指定之 Windows 網域使用者帳戶的名稱。</span><span class="sxs-lookup"><span data-stu-id="d7227-173">In Select users, type the name of the Windows domain user account that you specified in the target application.</span></span>  
  
4.  <span data-ttu-id="d7227-174">在 [授與許可權] 中，選取 **[直接授與使用者許可權**]。</span><span class="sxs-lookup"><span data-stu-id="d7227-174">In Grant Permissions, select **Grant users permission directly**.</span></span>  
  
5.  <span data-ttu-id="d7227-175">選取 [**參與**]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d7227-175">Select **Contribute**, and then click **OK**.</span></span>  
  
###  <a name="step-3-grant-read-permissions-to-access-external-data-sources-used-in-data-refresh"></a><a name="bkmk_dbread"></a><span data-ttu-id="d7227-176">步驟3：授與讀取權限以存取資料重新整理時所使用的外部資料源</span><span class="sxs-lookup"><span data-stu-id="d7227-176">Step 3: Grant read permissions to access external data sources used in data refresh</span></span>  
 <span data-ttu-id="d7227-177">當資料匯入至 PowerPivot 活頁簿時，外部資料連接通常是以信任連接或是以使用目前使用者身分連接至資料來源的模擬連接為基礎。</span><span class="sxs-lookup"><span data-stu-id="d7227-177">When importing data into a PowerPivot workbook, connections to external data are often based on trusted connections or impersonated connections that use the identity of the current user to connect to the data source.</span></span> <span data-ttu-id="d7227-178">這些類型的連接只能在目前使用者有讀取所匯入之資料的權限時使用。</span><span class="sxs-lookup"><span data-stu-id="d7227-178">These types of connections work only when the current user has permission to read the data that he or she is importing.</span></span>  
  
 <span data-ttu-id="d7227-179">在資料重新整理案例中，用來匯入資料的相同連接字串現在會重複使用來重新整理資料。</span><span class="sxs-lookup"><span data-stu-id="d7227-179">In a data refresh scenario, the same connection string that was used to import data is now reused to refresh the data.</span></span> <span data-ttu-id="d7227-180">假使連接字串採行目前使用者 (例如字串中包含 Integrated_Security=SSPI) 的作法，PowerPivot 系統服務在傳遞目前使用者時，即會將目標應用程式中所指定的使用者識別視為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="d7227-180">If the connection string assumes the current user (for example, a string that includes Integrated_Security=SSPI), then the PowerPivot System Service will pass the user identity specified in the target application as the current user.</span></span> <span data-ttu-id="d7227-181">帳戶必須具備外部資料來源的讀取權限，此連接才會成功。</span><span class="sxs-lookup"><span data-stu-id="d7227-181">This connection will only succeed if the account has read permissions on the external data source.</span></span>  
  
 <span data-ttu-id="d7227-182">因此，您必須將資料重新整理期間所要使用之所有外部資料來源的唯讀權限授與帳戶。</span><span class="sxs-lookup"><span data-stu-id="d7227-182">For this reason, you must grant the account read-only permissions on all of the external data sources that are used during data refresh.</span></span>  
  
 <span data-ttu-id="d7227-183">如果您是組織中使用的資料來源的系統管理員，可以建立登入並指定所需的權限。</span><span class="sxs-lookup"><span data-stu-id="d7227-183">If you are an administrator of the data sources used in your organization, you can create a login and assign the necessary permissions.</span></span> <span data-ttu-id="d7227-184">否則，您必須連絡資料擁有者並提供帳戶資訊。</span><span class="sxs-lookup"><span data-stu-id="d7227-184">Otherwise, you must contact the data owners and provide the account information.</span></span> <span data-ttu-id="d7227-185">請務必指定對應至目標應用程式的 Windows 網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="d7227-185">Be sure to specify the Windows domain user account that maps to the target application.</span></span> <span data-ttu-id="d7227-186">這是您在本主題的「步驟1：建立目標應用程式」中指定的帳號。</span><span class="sxs-lookup"><span data-stu-id="d7227-186">This is the account you specified in "Step 1: Create a target application" in this topic.</span></span>  
  
###  <a name="step-4-verify-account-availability-in-data-refresh-configuration-pages"></a><a name="bkmk_verify"></a><span data-ttu-id="d7227-187">步驟4：確認資料重新整理設定頁面中的帳戶可用性</span><span class="sxs-lookup"><span data-stu-id="d7227-187">Step 4: Verify account availability in data refresh configuration pages</span></span>  
  
1.  <span data-ttu-id="d7227-188">為包含 PowerPivot 資料之已發行的活頁簿，開啟資料重新整理組態頁面。</span><span class="sxs-lookup"><span data-stu-id="d7227-188">Open a data refresh configuration page for a published workbook that contains PowerPivot data.</span></span> <span data-ttu-id="d7227-189">如需如何開啟頁面的指示，請參閱[排程資料重新整理 &#40;PowerPivot for SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="d7227-189">For instructions on how to open the page, see [Schedule a Data Refresh &#40;PowerPivot for SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md).</span></span>  
  
2.  <span data-ttu-id="d7227-190">確認已在 [資料重新整理設定] 頁面中，啟用 [**使用儲存在 Secure Store Service (SSS) 中的認證來登入資料來源]** 選項，然後輸入目標應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="d7227-190">Verify that the **Connect using the credentials saved in Secure Store Service (SSS) to log on to the data source** option is enabled in the data refresh configuration page, and then enter the name of the target application.</span></span>  
  
3.  <span data-ttu-id="d7227-191">選取 [**同時**儘快重新整理] 核取方塊，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="d7227-191">Select the **Also refresh as soon as possible** checkbox, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="d7227-192">在包含活頁簿的文件庫中，選取活頁簿，按一下向右顯示的向下箭號，然後選取 [**管理 PowerPivot 資料**重新整理]。</span><span class="sxs-lookup"><span data-stu-id="d7227-192">In the library that contains the workbook, select the workbook, click the down arrow that appears to right, and then select **Manage PowerPivot Data Refresh**.</span></span> <span data-ttu-id="d7227-193">若資料重新整理作業傳回的資料量十分龐大，可能需要等候數分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="d7227-193">You might need to wait several minutes if the data refresh job is returning a large amount of data.</span></span>  
  
 <span data-ttu-id="d7227-194">如果發生錯誤，您可以按一下 [資料重新整理記錄] 頁面中的 [設定**排程**]，以嘗試不同的認證。</span><span class="sxs-lookup"><span data-stu-id="d7227-194">If an error occurs, you can click **Configure schedule** in the data refresh history page to try different credentials.</span></span> <span data-ttu-id="d7227-195">您也可能需要檢查原始活頁簿中的資料來源連接資訊，以查看資料重新整理期間所使用的連接字串。</span><span class="sxs-lookup"><span data-stu-id="d7227-195">You might also need to inspect the data source connection information in the original workbook to view the connection string that is used during data refresh.</span></span> <span data-ttu-id="d7227-196">連接字串所提供的伺服器位置與資料庫資訊，可讓您用於疑難排解問題。</span><span class="sxs-lookup"><span data-stu-id="d7227-196">The connection string will provide information about the server location and database that you can use to troubleshoot the problem.</span></span>  
  
 <span data-ttu-id="d7227-197">如需有關疑難排解的詳細資訊，請參閱 TechNet Wiki 上的[疑難排解 PowerPivot 資料](https://go.microsoft.com/fwlink/p/?LinkID=223279)重新整理。</span><span class="sxs-lookup"><span data-stu-id="d7227-197">For more information about troubleshooting, see [Troubleshooting PowerPivot Data Refresh](https://go.microsoft.com/fwlink/p/?LinkID=223279) on the TechNet Wiki.</span></span>  
  
##  <a name="configure-a-predefined-account-for-accessing-external-or-third-party-data-sources"></a><a name="config3rd"></a><span data-ttu-id="d7227-198">設定預先定義的帳戶來存取外部或協力廠商資料來源</span><span class="sxs-lookup"><span data-stu-id="d7227-198">Configure a predefined account for accessing external or third-party data sources</span></span>  
 <span data-ttu-id="d7227-199">資料庫伺服器通常會有自己的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="d7227-199">Database servers often come with their own authentication methods.</span></span> <span data-ttu-id="d7227-200">如果您的 PowerPivot 活頁簿需要資料庫認證，以便在資料重新整理期間存取外部資料來源，則可以建立認證的目標應用程式識別碼，然後在排程資料重新整理頁面的 [資料來源] 區段指定目標應用程式。</span><span class="sxs-lookup"><span data-stu-id="d7227-200">If you have a PowerPivot workbook that requires database credentials to access an external data source during data refresh, you can create a target application ID for the credentials, and then specify the target application in the Data Sources section of the schedule data refresh page.</span></span>  
  
 <span data-ttu-id="d7227-201">只有在您想要讓使用者選擇覆寫已經內嵌在 PowerPivot 活頁簿中的資料庫認證時，才需要這個步驟。</span><span class="sxs-lookup"><span data-stu-id="d7227-201">This step is only necessary if you want to provide users with an option of overriding the database credentials that are already embedded in the PowerPivot workbook.</span></span>  
  
 <span data-ttu-id="d7227-202">連接字串中必須包含使用者名稱及密碼，此步驟才能運作。</span><span class="sxs-lookup"><span data-stu-id="d7227-202">This step only works if the connection string already includes a user name and password.</span></span> <span data-ttu-id="d7227-203">請注意，在連接字串中包含認證十分罕見，因此您在使用此選項時也會有所限制。</span><span class="sxs-lookup"><span data-stu-id="d7227-203">Note that having credentials in the connection string is relatively uncommon, so your ability to make use of this option is somewhat limited.</span></span> <span data-ttu-id="d7227-204">在大多數的情況下，您若是使用資料庫驗證來連接資料來源，則連接字串中將只會包含使用者識別碼及密碼。</span><span class="sxs-lookup"><span data-stu-id="d7227-204">In most cases, you will only have a user ID and password in the connection string if you are using database authentication to connect to the data source.</span></span> <span data-ttu-id="d7227-205">如需如何檢查連接字串以查看其是否包含使用者識別碼和密碼的詳細資訊，請參閱[PowerPivot Data Refresh With SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md)中的「授與建立排程和存取外部資料的許可權」一節。</span><span class="sxs-lookup"><span data-stu-id="d7227-205">For more information about how to check the connection string to see if it includes a User ID and password, see the "Grant permissions to create schedules and access external data" section in [PowerPivot Data Refresh with SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md).</span></span>  
  
1.  <span data-ttu-id="d7227-206">在 [管理中心] 的 [應用程式管理] 中，按一下 **[管理服務應用程式]** 。</span><span class="sxs-lookup"><span data-stu-id="d7227-206">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="d7227-207">按一下 [ **Secure Store Service**]。</span><span class="sxs-lookup"><span data-stu-id="d7227-207">Click **Secure Store Service**.</span></span>  
  
3.  <span data-ttu-id="d7227-208">在 [管理目標應用程式] 中，按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="d7227-208">In Manage Target Applications, click **New**.</span></span>  
  
4.  <span data-ttu-id="d7227-209">在 [目標應用程式識別碼] 中，輸入文字字串。</span><span class="sxs-lookup"><span data-stu-id="d7227-209">In Target application ID, type a text string.</span></span> <span data-ttu-id="d7227-210">此字串必須是唯一的，但也應該容易記憶。</span><span class="sxs-lookup"><span data-stu-id="d7227-210">The string must be unique, but it should also be easy to remember.</span></span> <span data-ttu-id="d7227-211">每當使用者想要使用儲存在此應用程式中的認證時，將在資料重新整理排程頁面中輸入這個字串。</span><span class="sxs-lookup"><span data-stu-id="d7227-211">Users will type this string in data refresh schedule pages whenever they want to use the credentials that are stored in this application.</span></span>  
  
5.  <span data-ttu-id="d7227-212">在 [顯示名稱] 中，輸入描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="d7227-212">In Display Name, enter a descriptive name.</span></span> <span data-ttu-id="d7227-213">此名稱僅用於顯示用途，</span><span class="sxs-lookup"><span data-stu-id="d7227-213">This name is used for display purposes only.</span></span> <span data-ttu-id="d7227-214">而不是在資料重新整理排程中用來指定目標應用程式。</span><span class="sxs-lookup"><span data-stu-id="d7227-214">It is not used to specify the target application in a data refresh schedule.</span></span>  
  
6.  <span data-ttu-id="d7227-215">在 [連絡人電子郵件] 中，輸入您的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="d7227-215">In Contact Email, type your e-mail address.</span></span>  
  
7.  <span data-ttu-id="d7227-216">在 [目標應用程式類型] 中，選取 [**群組**]。</span><span class="sxs-lookup"><span data-stu-id="d7227-216">In Target Application Type, select **Group**.</span></span>  
  
8.  <span data-ttu-id="d7227-217">略過目標應用程式的網頁 URL。</span><span class="sxs-lookup"><span data-stu-id="d7227-217">Skip Target Application Page URL.</span></span> <span data-ttu-id="d7227-218">PowerPivot 資料重新整理不會使用它。</span><span class="sxs-lookup"><span data-stu-id="d7227-218">PowerPivot data refresh does not use it.</span></span>  
  
9. <span data-ttu-id="d7227-219">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="d7227-219">Click **Next**.</span></span>  
  
10. <span data-ttu-id="d7227-220">在 [**指定 Secure Store 目標應用程式的認證欄位**] 頁面中，只有在資料來源使用 Windows 驗證時才接受預設值。</span><span class="sxs-lookup"><span data-stu-id="d7227-220">In the **Specify the credentials fields for your Secure Store Target application** page, accept the default values only if the data source uses Windows authentication.</span></span> <span data-ttu-id="d7227-221">否則，請選擇適用於資料來源的欄位類型，然後編輯欄位名稱以符合此類型。</span><span class="sxs-lookup"><span data-stu-id="d7227-221">Otherwise, choose the field types that are valid for your data source, and then edit the field names to match the type.</span></span>  
  
     <span data-ttu-id="d7227-222">例如，您可能在欄位名稱中指定 SQL Server 使用者名稱及 SQL Server 使用者密碼，然後選擇使用者名稱及密碼做為欄位類型。</span><span class="sxs-lookup"><span data-stu-id="d7227-222">For example, you might specify SQL Server User Name and SQL Server User Password for field names, and then choose User Name and Password for field types.</span></span>  
  
11. <span data-ttu-id="d7227-223">按一下 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="d7227-223">Click Next.</span></span>  
  
12. <span data-ttu-id="d7227-224">在 [目標應用程式管理員] 中，針對應該擁有應用程式設定管理存取權的 SharePoint 使用者指定 Windows 網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="d7227-224">In Target Application Administrators, specify the Windows domain user accounts of SharePoint users who should have administrative access to the application settings.</span></span>  
  
13. <span data-ttu-id="d7227-225">在 [成員] 中，加入下列使用者和群組帳戶：</span><span class="sxs-lookup"><span data-stu-id="d7227-225">In Members, add the following user and group accounts:</span></span>  
  
    1.  <span data-ttu-id="d7227-226">將您的 Windows 使用者帳戶加入至 [成員] 清單中，做為建立應用程式的人員。</span><span class="sxs-lookup"><span data-stu-id="d7227-226">As the person creating the application, add your Windows user account to the Members list.</span></span>  
  
    2.  <span data-ttu-id="d7227-227">加入將使用目標應用程式存取其預存認證之每個 PowerPivot 服務應用程式的應用程式集區識別。</span><span class="sxs-lookup"><span data-stu-id="d7227-227">Add the application pool identity of each PowerPivot service application that will be using the target application to access its stored credentials.</span></span> <span data-ttu-id="d7227-228">若要查看身分識別，請移至 [**管理服務應用程式**]，按一下 [名稱] 旁邊的空白處來選取 PowerPivot 服務應用程式 (這會選取資料列) ，然後按一下 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="d7227-228">To view the identity, go to **Manage service applications**, select the PowerPivot service application by clicking the empty space next to the name (this selects the row), and then click **Properties**.</span></span> <span data-ttu-id="d7227-229">出現在此頁面的安全性帳戶就是您要當做目標應用程式成員加入的帳戶。</span><span class="sxs-lookup"><span data-stu-id="d7227-229">The security account that appears on this page is the account that you want to add as a member of the target application.</span></span>  
  
    3.  <span data-ttu-id="d7227-230">加入將在資料重新整理排程頁面之資料來源區段中輸入此目標應用程式的 Windows 使用者和群組帳戶。</span><span class="sxs-lookup"><span data-stu-id="d7227-230">Add Windows user and group accounts that will be entering this target application in the data sources section of a data refresh schedule page.</span></span>  
  
14. <span data-ttu-id="d7227-231">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="d7227-231">Click **OK**.</span></span>  
  
15. <span data-ttu-id="d7227-232">選取您剛才建立的目標應用程式，按一下向下箭號，然後選取 [**設定認證]。**</span><span class="sxs-lookup"><span data-stu-id="d7227-232">Select the target application you just created, click the down arrow and select **Set Credentials.**</span></span>  
  
16. <span data-ttu-id="d7227-233">輸入要用於連接資料來源的認證 (例如 SQL Server 登入的使用者名稱及密碼)。</span><span class="sxs-lookup"><span data-stu-id="d7227-233">Enter the credentials that will be used to connect to the data source (for example, the user name and password of a SQL Server login).</span></span>  
  
17. <span data-ttu-id="d7227-234">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="d7227-234">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7227-235">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7227-235">See Also</span></span>  
 <span data-ttu-id="d7227-236">[排程資料重新整理 &#40;PowerPivot for SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="d7227-236">[Schedule a Data Refresh &#40;PowerPivot for SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md) </span></span>  
 [<span data-ttu-id="d7227-237">SharePoint 2010 中的 PowerPivot 資料重新整理</span><span class="sxs-lookup"><span data-stu-id="d7227-237">PowerPivot Data Refresh with SharePoint 2010</span></span>](powerpivot-data-refresh-with-sharepoint-2010.md)  
  
  
