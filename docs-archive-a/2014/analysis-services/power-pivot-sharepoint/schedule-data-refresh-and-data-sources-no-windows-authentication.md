---
title: 排程資料重新整理和不支援 Windows 驗證的資料來源 (PowerPivot for SharePoint) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d8d875bc-7823-46b7-a939-867cefd4de12
author: minewiskan
ms.author: owend
ms.openlocfilehash: 63e37dec6f334395c0c1812c6f76d750c16c53ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596321"
---
# <a name="schedule-data-refresh-and-data-sources-that-do-not-support-windows-authentication-powerpivot-for-sharepoint"></a><span data-ttu-id="85274-102">排程資料重新整理與不支援 Windows 驗證的資料來源 (PowerPivot for SharePoint)</span><span class="sxs-lookup"><span data-stu-id="85274-102">Schedule Data Refresh and Data Sources That Do Not Support Windows Authentication (PowerPivot for SharePoint)</span></span>
  <span data-ttu-id="85274-103">本主題描述 PowerPivot for SharePoint 排程資料重新整理的工作流程，而且這項作業可以使用**不**支援 Windows 驗證的資料來源。</span><span class="sxs-lookup"><span data-stu-id="85274-103">This topic describes a workflow of PowerPivot for SharePoint schedule data fresh that can use data sources that do **NOT** support Windows Authentication.</span></span> <span data-ttu-id="85274-104">例如，Oracle 或 IDM DB2 資料來源。</span><span class="sxs-lookup"><span data-stu-id="85274-104">For example Oracle or IDM DB2 data sources.</span></span> <span data-ttu-id="85274-105">雖然本主題的圖例和步驟參考的是 Oracle 資料來源，但是相同的工作流程也適用於其他資料來源。</span><span class="sxs-lookup"><span data-stu-id="85274-105">The illustrations and steps in this topic reference Oracle data sources but the same workflow applies to other data sources.</span></span>  
  
||  
|-|  
|<span data-ttu-id="85274-106">**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2010 &#124; SharePoint 2013。</span><span class="sxs-lookup"><span data-stu-id="85274-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2010 &#124; SharePoint 2013.</span></span>|  
  
 <span data-ttu-id="85274-107">**概觀** 建立兩個安全存放目標應用程式。</span><span class="sxs-lookup"><span data-stu-id="85274-107">**Overview:** Create two Secure Store Target Applications.</span></span> <span data-ttu-id="85274-108">將第一個目標應用程式 (PowerPivotDataRefresh) 設定為使用 Windows 認證。</span><span class="sxs-lookup"><span data-stu-id="85274-108">Configure the first target application (PowerPivotDataRefresh) to use Windows credentials.</span></span> <span data-ttu-id="85274-109">使用不支援 Windows 驗證之資料來源 (例如 Oracle 資料庫) 的認證來設定第二個目標應用程式。</span><span class="sxs-lookup"><span data-stu-id="85274-109">Configure the second target application with the credentials for a data source that does not support windows authentication, for example, an Oracle database.</span></span> <span data-ttu-id="85274-110">第二個目標應用程式也會將第一個目標應用程式用於無人看管的資料重新整理帳戶。</span><span class="sxs-lookup"><span data-stu-id="85274-110">The second target application also uses the first target application for the unattended data refresh account.</span></span>  
  
 <span data-ttu-id="85274-111">![as_powerpivot_refresh_no_windows_auth](../media/as-powerpivot-refresh-no-windows-auth.gif "as_powerpivot_refresh_no_windows_auth")</span><span class="sxs-lookup"><span data-stu-id="85274-111">![as_powerpivot_refresh_no_windows_auth](../media/as-powerpivot-refresh-no-windows-auth.gif "as_powerpivot_refresh_no_windows_auth")</span></span>  
  
-   <span data-ttu-id="85274-112">**(1) PowerPivotDatarefresh** 使用 Windows 驗證所設定的安全存放目標應用程式識別碼。</span><span class="sxs-lookup"><span data-stu-id="85274-112">**(1) PowerPivotDatarefresh:** A Secure Store Target Application ID that is set with windows authentication.</span></span>  
  
-   <span data-ttu-id="85274-113">**(2) OracleAuthentication** 使用 Oracle 認證所設定的安全存放目標應用程式識別碼。</span><span class="sxs-lookup"><span data-stu-id="85274-113">**(2) OracleAuthentication:** A Secure Store Target Application ID that is set with Oracle credentials.</span></span>  
  
-   <span data-ttu-id="85274-114">\*\* (3) **PowerPivot 服務應用程式會設定為將目標應用程式 "PowerPivotDataRefresh" 用於**無人看管的資料\*\*重新整理帳戶。</span><span class="sxs-lookup"><span data-stu-id="85274-114">**(3)** The PowerPivot Service application is configure to use the target application "PowerPivotDataRefresh" for the **Unattended Data Refresh Account**.</span></span>  
  
-   <span data-ttu-id="85274-115">**(4)** PowerePivot 活頁簿會使用 Oracle 資料。</span><span class="sxs-lookup"><span data-stu-id="85274-115">**(4)** PowerePivot Workbook uses Oracle data.</span></span> <span data-ttu-id="85274-116">活頁簿重新整理設定會指定要將目標應用程式 **(2)** 用於認證的資料來源連接。</span><span class="sxs-lookup"><span data-stu-id="85274-116">The workbook refresh settings specify the data source connection to use the target application **(2)** for credentials.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="85274-117">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="85274-117">Prerequisites</span></span>  
  
-   <span data-ttu-id="85274-118">PowerPivot 服務應用程式存在。</span><span class="sxs-lookup"><span data-stu-id="85274-118">A PowerPivot Service Application exists.</span></span>  
  
-   <span data-ttu-id="85274-119">Secure Store Service 應用程式存在。</span><span class="sxs-lookup"><span data-stu-id="85274-119">A Secure Store Service Application exists.</span></span>  
  
-   <span data-ttu-id="85274-120">包含 PowerPivot 資料模型的 Excel 活頁簿存在。</span><span class="sxs-lookup"><span data-stu-id="85274-120">An Excel workbook with a PowerPivot data model exists.</span></span>  
  
## <a name="to-create-a-target-application-id-that-uses-windows-authentication"></a><span data-ttu-id="85274-121">若要建立使用 Windows 驗證的目標應用程式識別碼</span><span class="sxs-lookup"><span data-stu-id="85274-121">To Create a Target Application ID that uses Windows Authentication</span></span>  
  
1.  <span data-ttu-id="85274-122">在 SharePoint 管理中心內，按一下 [**管理服務應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="85274-122">In SharePoint Central administration, click **Manage Service Applications**.</span></span>  
  
2.  <span data-ttu-id="85274-123">按一下 Secure Store Service 應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="85274-123">Click the name of your secure store service application.</span></span>  
  
3.  <span data-ttu-id="85274-124">在 [管理]\*\*\*\* 頁面上，按一下 [新增]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="85274-124">On the **Manage** page, click **New**.</span></span> <span data-ttu-id="85274-125">![as_powerpivot_refresh_sss_new_target_application](../media/as-powerpivot-refresh-sss-new-target-application.gif "as_powerpivot_refresh_sss_new_target_application")</span><span class="sxs-lookup"><span data-stu-id="85274-125">![as_powerpivot_refresh_sss_new_target_application](../media/as-powerpivot-refresh-sss-new-target-application.gif "as_powerpivot_refresh_sss_new_target_application")</span></span>  
  
4.  <span data-ttu-id="85274-126">在 [建立新的 Secure Store 目標應用程式] \*\*\*\* 頁面上，設定下列值：</span><span class="sxs-lookup"><span data-stu-id="85274-126">On the **Create New Secure Store Target Application** page, configure the following values:</span></span>  
  
    -   <span data-ttu-id="85274-127">**目標應用程式識別碼** ：PowerPivotDataRefresh。</span><span class="sxs-lookup"><span data-stu-id="85274-127">**Target Application ID:** PowerPivotDataRefresh.</span></span>  
  
    -   <span data-ttu-id="85274-128">**顯示名稱** ：PowerPivotDataRefresh。</span><span class="sxs-lookup"><span data-stu-id="85274-128">**Display Name:** PowerPivotDataRefresh.</span></span>  
  
    -   <span data-ttu-id="85274-129">**連絡人電子郵件：** ？</span><span class="sxs-lookup"><span data-stu-id="85274-129">**Contact E-mail:** ?</span></span>  
  
    -   <span data-ttu-id="85274-130">**目標應用程式類型** ：群組。</span><span class="sxs-lookup"><span data-stu-id="85274-130">**Target Application Type:** Group.</span></span>  
  
    -   <span data-ttu-id="85274-131">**目標應用程式頁面 URL** ：無。</span><span class="sxs-lookup"><span data-stu-id="85274-131">**Target Application Page URL:** None.</span></span>  
  
5.  <span data-ttu-id="85274-132">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="85274-132">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="85274-133">在 [認證] 頁面上，保留 [Windows 使用者名稱] \*\*\*\* 和 [Windows 密碼] \*\*\*\* 的兩個預設欄位名稱和欄位類型。</span><span class="sxs-lookup"><span data-stu-id="85274-133">On the Credentials page, leave the two default field names and field types for **Windows User Name** and **Windows Password**.</span></span>  
  
7.  <span data-ttu-id="85274-134">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="85274-134">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="85274-135">在 [成員資格設定] \*\*\*\* 頁面上，至少加入一個 **目標應用程式管理員** ，然後加入需要存取目標應用程式的成員。</span><span class="sxs-lookup"><span data-stu-id="85274-135">On the **Membership Settings** page, add at least one **Target Application Administrator** and then add members that need access to the target application.</span></span>  
  
9. <span data-ttu-id="85274-136">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="85274-136">Click **OK**.</span></span>  
  
10. <span data-ttu-id="85274-137">新的目標應用程式識別碼就會加入至清單。</span><span class="sxs-lookup"><span data-stu-id="85274-137">The new Target Application ID is added to the list.</span></span> <span data-ttu-id="85274-138">選取目標應用程式識別碼，然後按一下 [**設定認證**]![as_powerpivot_refresh_sss_set_key](../media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key")。</span><span class="sxs-lookup"><span data-stu-id="85274-138">Select the Target application ID and click **Set Credentials**![as_powerpivot_refresh_sss_set_key](../media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key").</span></span>  
  
11. <span data-ttu-id="85274-139">輸入 Windows 使用者名稱和 Windows 密碼，然後按一下 [確定] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="85274-139">Type the Windows User Name and Windows Password and then click **OK**.</span></span>  
  
## <a name="to-create-a-target-application-id-that-uses-oracle-credentials"></a><span data-ttu-id="85274-140">若要建立使用 Oracle 認證的目標應用程式識別碼</span><span class="sxs-lookup"><span data-stu-id="85274-140">To Create a Target Application ID that uses Oracle credentials</span></span>  
  
1.  <span data-ttu-id="85274-141">在 SharePoint 管理中心內，按一下 [**管理服務應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="85274-141">In SharePoint Central administration, click **Manage Service Applications**.</span></span>  
  
2.  <span data-ttu-id="85274-142">按一下 Secure Store Service 應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="85274-142">Click the name of your Secure Store Service application.</span></span>  
  
3.  <span data-ttu-id="85274-143">在 [**管理**] 頁面上，按一下 [**新增**![as_powerpivot_refresh_sss_new_target_application](../media/as-powerpivot-refresh-sss-new-target-application.gif "as_powerpivot_refresh_sss_new_target_application")]。</span><span class="sxs-lookup"><span data-stu-id="85274-143">On the **Manage** page, click **New**![as_powerpivot_refresh_sss_new_target_application](../media/as-powerpivot-refresh-sss-new-target-application.gif "as_powerpivot_refresh_sss_new_target_application").</span></span>  
  
4.  <span data-ttu-id="85274-144">在 [建立新的 Secure Store 目標應用程式] \*\*\*\* 頁面上，設定下列值：</span><span class="sxs-lookup"><span data-stu-id="85274-144">On the **Create New Secure Store Target Application** page, configure the following values:</span></span>  
  
    -   <span data-ttu-id="85274-145">**目標應用程式識別碼：** OracleAuthentication。</span><span class="sxs-lookup"><span data-stu-id="85274-145">**Target Application ID:** OracleAuthentication.</span></span>  
  
    -   <span data-ttu-id="85274-146">**顯示名稱：** OracleAuthentication。</span><span class="sxs-lookup"><span data-stu-id="85274-146">**Display Name:** OracleAuthentication.</span></span>  
  
    -   <span data-ttu-id="85274-147">**連絡人電子郵件：** ？</span><span class="sxs-lookup"><span data-stu-id="85274-147">**Contact E-mail:** ?</span></span>  
  
    -   <span data-ttu-id="85274-148">**目標應用程式類型** ：群組。</span><span class="sxs-lookup"><span data-stu-id="85274-148">**Target Application Type:** Group.</span></span>  
  
    -   <span data-ttu-id="85274-149">**目標應用程式頁面 URL** ：無。</span><span class="sxs-lookup"><span data-stu-id="85274-149">**Target Application Page URL:** None.</span></span>  
  
5.  <span data-ttu-id="85274-150">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="85274-150">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="85274-151">在 [**認證**] 頁面上，將第一個功能變數名稱變更為， `Oracle User ID` 並將**欄位類型**變更為 `User Name` 。</span><span class="sxs-lookup"><span data-stu-id="85274-151">On the **Credentials** page, change the first field name to `Oracle User ID` and change the **Field Type** to `User Name`.</span></span>  
  
     <span data-ttu-id="85274-152">將第二個功能變數名稱變更為 `Oracle Password` ，並將**欄位類型**變更為 `Password` 。</span><span class="sxs-lookup"><span data-stu-id="85274-152">Change the second field name to `Oracle Password` and the **Field Type** to `Password`.</span></span>  
  
7.  <span data-ttu-id="85274-153">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="85274-153">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="85274-154">在 [成員資格設定] \*\*\*\* 頁面上，至少加入一個 **目標應用程式管理員** ，然後加入需要存取目標應用程式的成員。</span><span class="sxs-lookup"><span data-stu-id="85274-154">On the **Membership Settings** page, add at least one **Target Application Administrator** and then add members that need access to the target application.</span></span>  
  
9. <span data-ttu-id="85274-155">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="85274-155">Click **OK**.</span></span>  
  
10. <span data-ttu-id="85274-156">新的目標應用程式識別碼就會加入至清單。</span><span class="sxs-lookup"><span data-stu-id="85274-156">The new Target Application ID is added to the list.</span></span> <span data-ttu-id="85274-157">選取目標應用程式識別碼，然後按一下 [**設定認證**]![as_powerpivot_refresh_sss_set_key](../media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key")。</span><span class="sxs-lookup"><span data-stu-id="85274-157">Select the Target application ID and click **Set Credentials**![as_powerpivot_refresh_sss_set_key](../media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key").</span></span>  
  
11. <span data-ttu-id="85274-158">輸入 Oracle 使用者識別碼和 Oracle 密碼，然後按一下 [確定] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="85274-158">Type the Oracle User ID and Oracle Password and then click **OK**.</span></span>  
  
 <span data-ttu-id="85274-159">如需詳細資訊，請參閱[使用 Secure Store 與 SQL Server Authentication (SharePoint Server 2013) ](https://technet.microsoft.com/library/gg298949.aspx) (中的「若要建立 SQL Server 驗證的目標應用程式」一節 https://technet.microsoft.com/library/gg298949.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="85274-159">For more information, see section "To Create a target application for SQL Server Authentication" in [Use Secure Store with SQL Server Authentication (SharePoint Server 2013)](https://technet.microsoft.com/library/gg298949.aspx) (https://technet.microsoft.com/library/gg298949.aspx).</span></span>  
  
## <a name="to-configure-the-powerpivot-service-application"></a><span data-ttu-id="85274-160">若要設定 PowerPivot 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="85274-160">To Configure the PowerPivot Service Application</span></span>  
  
1.  <span data-ttu-id="85274-161">在 SharePoint 管理中心內，按一下 [管理服務應用程式]。</span><span class="sxs-lookup"><span data-stu-id="85274-161">In SharePoint central administration, click Manage Service Applications.</span></span>  
  
2.  <span data-ttu-id="85274-162">按一下 PowerPivot 服務應用程式的名稱，例如「預設的 PowerPivot 服務應用程式」。</span><span class="sxs-lookup"><span data-stu-id="85274-162">Click the name of your PowerPivot Service Application, for example "Default PowerPivot Service Application".</span></span>  
  
3.  <span data-ttu-id="85274-163">在 [動作] 區段中，按一下 [設定服務應用程式設定] \*\*\*\* 。</span><span class="sxs-lookup"><span data-stu-id="85274-163">Click **Configure service application settings** in the Actions section.</span></span>  
  
4.  <span data-ttu-id="85274-164">在 [**資料**重新整理] 區段中，將**PowerPivot 無人看管的資料**重新整理帳戶設定為， `PowerPivotDataRefresh` 然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="85274-164">In the **Data Refresh** section, set the **PowerPivot Unattended Data Refresh Account**to`PowerPivotDataRefresh` and then click **OK**.</span></span>  
  
     <span data-ttu-id="85274-165">![as_powerpivot_refresh_new_refresh_acount](../media/as-powerpivot-refresh-new-refresh-acount.gif "as_powerpivot_refresh_new_refresh_acount")</span><span class="sxs-lookup"><span data-stu-id="85274-165">![as_powerpivot_refresh_new_refresh_acount](../media/as-powerpivot-refresh-new-refresh-acount.gif "as_powerpivot_refresh_new_refresh_acount")</span></span>  
  
## <a name="to-configure-the-workbook"></a><span data-ttu-id="85274-166">若要設定活頁簿</span><span class="sxs-lookup"><span data-stu-id="85274-166">To configure the workbook</span></span>  
  
1.  <span data-ttu-id="85274-167">流覽至 PowerPivot 圖庫中的活頁簿，然後按一下 [**管理資料**重新整理]![as_powerpivot_refresh_manage_reresh](../media/as-powerpivot-refresh-manage-reresh.gif "as_powerpivot_refresh_manage_reresh")。</span><span class="sxs-lookup"><span data-stu-id="85274-167">Browse to your workbook in the PowerPivot Gallery and click **Manage Data Refresh**![as_powerpivot_refresh_manage_reresh](../media/as-powerpivot-refresh-manage-reresh.gif "as_powerpivot_refresh_manage_reresh").</span></span>  
  
2.  <span data-ttu-id="85274-168">如果您看見 [資料重新整理記錄] \*\*\*\* 頁面，請按一下 [設定排程] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="85274-168">If you see the **Data Refresh History** page, click **Configure Schedule**.</span></span>  
  
3.  <span data-ttu-id="85274-169">按一下 [啟用] 。</span><span class="sxs-lookup"><span data-stu-id="85274-169">Click **Enable**.</span></span>  
  
4.  <span data-ttu-id="85274-170">按一下 [並且盡快重新整理] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="85274-170">Click **Also Refresh as soon as possible**.</span></span>  
  
5.  <span data-ttu-id="85274-171">在 [認證] \*\*\*\* 區段中，按一下 [使用系統管理員所設定的資料重新整理帳戶] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="85274-171">In the **Credentials** section, click **Use the Data refresh account configured by the administrator**.</span></span>  
  
6.  <span data-ttu-id="85274-172">清除 [所有資料來源] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="85274-172">Clear **All data sources**.</span></span>  
  
7.  <span data-ttu-id="85274-173">針對使用 Oracle 資料的資料來源選取 [重新整理] \*\*\*\* 。</span><span class="sxs-lookup"><span data-stu-id="85274-173">Select **Refresh** for the data source that uses the Oracle data.</span></span> <span data-ttu-id="85274-174">您可以在 Microsoft Excel 的 [資料] \*\*\*\*、[連線] \*\*\*\*、[內容] \*\*\*\* 功能表中變更資料來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="85274-174">The name of the data source name can be changed in Microsoft Excel in the **Data**, **Connections**, **Properties** menu.</span></span>  
  
8.  <span data-ttu-id="85274-175">在您的資料來源底下，選取 [使用預設排程] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="85274-175">Under your data source, Select **Use Default Schedule**.</span></span>  
  
9. <span data-ttu-id="85274-176">選取 **[使用儲存在 Secure Store Service (SSS) 中的認證進行連接，以登入資料來源。在 SSS ID 方塊中輸入用來查閱認證的 ID**。</span><span class="sxs-lookup"><span data-stu-id="85274-176">Select **Connect using the credentials saved in Secure Store Service (SSS) to log on to the data source. Enter the ID used to look up the credentials in the SSS ID box**.</span></span>  
  
10. <span data-ttu-id="85274-177">在 [**識別碼：** ] 方塊中，輸入 `OracleAuthentication` 。</span><span class="sxs-lookup"><span data-stu-id="85274-177">In the **ID:** box, type `OracleAuthentication`.</span></span>  
  
11. <span data-ttu-id="85274-178">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="85274-178">Click **OK**.</span></span>  
  
     <span data-ttu-id="85274-179">如果您看到類似下列的錯誤訊息： `The provided Secure Store target application is either incorrectly configured or does not exist`。</span><span class="sxs-lookup"><span data-stu-id="85274-179">If you see an error message similar to: `The provided Secure Store target application is either incorrectly configured or does not exist`.</span></span>  
  
     <span data-ttu-id="85274-180">常見的解決方法有兩種：</span><span class="sxs-lookup"><span data-stu-id="85274-180">The two common solutions are:</span></span>  
  
    -   <span data-ttu-id="85274-181">確認目標應用程式識別碼是否正確。</span><span class="sxs-lookup"><span data-stu-id="85274-181">Verify that the Target Application ID is correct.</span></span>  
  
    -   <span data-ttu-id="85274-182">確認您已設定目標應用程式的認證。</span><span class="sxs-lookup"><span data-stu-id="85274-182">Verify that you set credentials for the Target Application.</span></span>  
  
## <a name="to-verify-data-refresh-with-the-new-authentication"></a><span data-ttu-id="85274-183">若要使用新的驗證來確認資料重新整理</span><span class="sxs-lookup"><span data-stu-id="85274-183">To Verify Data Refresh with the new authentication</span></span>  
 <span data-ttu-id="85274-184">當您按一下 [確定] \*\*\*\* 時，就會看見 [重新整理記錄] \*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="85274-184">When you click **ok**, you see the **Refresh History** page.</span></span> <span data-ttu-id="85274-185">在幾分鐘之內，您應該會在重新整理記錄中看見新的項目，因為您在先前的步驟中選取了 [並且盡快重新整理] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="85274-185">Within a few minutes, you should see a new item in the refresh history because in the previous steps you selected **Also Refresh as soon as possible**.</span></span> <span data-ttu-id="85274-186">計時器工作 **PowerPivot 資料重新整理計時器工作**的預設值為 1 分鐘。</span><span class="sxs-lookup"><span data-stu-id="85274-186">The default value for the timer job **PowerPivot Data Refresh Timer Job** is 1 minute.</span></span> <span data-ttu-id="85274-187">如果您並未在重新整理記錄中看見新的項目，請等候幾分鐘，然後重新整理瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="85274-187">If you do not see a new item in the refresh history, wait a few minutes and refresh your browser.</span></span> <span data-ttu-id="85274-188">如果您仍然看不到新的項目，請確認計時器工作的目前值。</span><span class="sxs-lookup"><span data-stu-id="85274-188">If you still do not see the new item, verify the current value of the timer job.</span></span>  
  
## <a name="more-information"></a><span data-ttu-id="85274-189">相關資訊</span><span class="sxs-lookup"><span data-stu-id="85274-189">More Information</span></span>  
  
-   <span data-ttu-id="85274-190">[在 SharePoint 2013 中設定 Secure Store Service](https://technet.microsoft.com/library/ee806866.aspx)。</span><span class="sxs-lookup"><span data-stu-id="85274-190">[Configure the Secure Store Service in SharePoint 2013](https://technet.microsoft.com/library/ee806866.aspx).</span></span>  
  
-   <span data-ttu-id="85274-191">請參閱[PowerPivot data refresh With SharePoint 2013 和 SQL Server 2012 SP1 (Analysis Services) ](https://msdn.microsoft.com/library/jj879294.aspx#bkmk_windows_auth_interactive_data_refresh)中的「排程的資料重新整理」一節。</span><span class="sxs-lookup"><span data-stu-id="85274-191">See the "Scheduled Data Refresh" section of [PowerPivot Data Refresh with SharePoint 2013 and SQL Server 2012 SP1 (Analysis Services)](https://msdn.microsoft.com/library/jj879294.aspx#bkmk_windows_auth_interactive_data_refresh).</span></span>  
  
  
