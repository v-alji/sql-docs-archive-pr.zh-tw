---
title: 使用 PowerShell 來變更和列出 Reporting Services 訂用帳戶擁有者並執行訂用帳戶 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 0fa6cb36-68fc-4fb8-b1dc-ae4f12bf6ff0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b274dc190d8830a2cf7b55110f15267a00c581e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596468"
---
# <a name="use-powershell-to-change-and-list-reporting-services-subscription-owners-and-run-a-subscription"></a><span data-ttu-id="571aa-102">Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription</span><span class="sxs-lookup"><span data-stu-id="571aa-102">Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription</span></span>
  <span data-ttu-id="571aa-103">從 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 開始，您可以用程式設計方式，將 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 訂閱的擁有權，從某位使用者轉移到另一位使用者。</span><span class="sxs-lookup"><span data-stu-id="571aa-103">Starting with [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] you can programmatically transfer the ownership of a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] subscription from one user to another.</span></span> <span data-ttu-id="571aa-104">本主題提供數個 Windows PowerShell 指令碼，供您可變更或單純列出訂閱擁有權時使用。</span><span class="sxs-lookup"><span data-stu-id="571aa-104">This topic provides several Windows PowerShell scripts you can use to change or simply list subscription ownership.</span></span> <span data-ttu-id="571aa-105">每項範例均包含原生模式和 SharePoint 模式的範例語法。</span><span class="sxs-lookup"><span data-stu-id="571aa-105">Each sample includes sample syntax for both Native mode and SharePoint mode.</span></span> <span data-ttu-id="571aa-106">當您變更訂閱擁有者之後，便會在新擁有者的安全性內容中執行訂閱，且報表中的 [User!UserID] 欄位會顯示新擁有者的值。</span><span class="sxs-lookup"><span data-stu-id="571aa-106">After you change the subscription owner, the subscription will then execute in the security context of the new owner, and the User!UserID field in the report will display the value of new owner.</span></span> <span data-ttu-id="571aa-107">如需 PowerShell 範例呼叫的物件模型詳細資訊，請參閱 <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A></span><span class="sxs-lookup"><span data-stu-id="571aa-107">For more information on the object model the PowerShell samples call, see <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A></span></span>

 <span data-ttu-id="571aa-108">![PowerShell 相關內容](../media/rs-powershellicon.jpg "PowerShell 相關內容")</span><span class="sxs-lookup"><span data-stu-id="571aa-108">![PowerShell related content](../media/rs-powershellicon.jpg "PowerShell related content")</span></span>

||
|-|
|<span data-ttu-id="571aa-109">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 原生模式 &#124; [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="571aa-109">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Native mode &#124; [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] SharePoint mode</span></span>|

 <span data-ttu-id="571aa-110">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="571aa-110">**In this topic:**</span></span>

-   [<span data-ttu-id="571aa-111">如何使用指令碼</span><span class="sxs-lookup"><span data-stu-id="571aa-111">How to use the scripts</span></span>](#bkmk_how_to)

-   [<span data-ttu-id="571aa-112">指令碼：列出所有訂閱的擁有權</span><span class="sxs-lookup"><span data-stu-id="571aa-112">Script: List the ownership of all subscriptions</span></span>](#bkmk_list_ownership_all)

-   [<span data-ttu-id="571aa-113">指令碼：列出特定使用者擁有的所有訂閱</span><span class="sxs-lookup"><span data-stu-id="571aa-113">Script: List all subscriptions owned by a specific user</span></span>](#bkmk_list_all_one_user)

-   [<span data-ttu-id="571aa-114">指令碼：針對特定使用者擁有的所有訂閱變更擁有權</span><span class="sxs-lookup"><span data-stu-id="571aa-114">Script: Change ownership for all subscriptions owned by a specific user</span></span>](#bkmk_change_all)

-   [<span data-ttu-id="571aa-115">指令碼：列出與特定報表建立關聯的所有訂閱</span><span class="sxs-lookup"><span data-stu-id="571aa-115">Script: List all subscriptions associated with a specific report</span></span>](#bkmk_list_for_1_report)

-   [<span data-ttu-id="571aa-116">指令碼：變更特定訂閱的擁有權</span><span class="sxs-lookup"><span data-stu-id="571aa-116">Script: Change ownership of a specific subscription</span></span>](#bkmk_change_all_1_subscription)

-   [<span data-ttu-id="571aa-117">指令碼：執行 (引發) 單一訂閱</span><span class="sxs-lookup"><span data-stu-id="571aa-117">Script: Run (fire) a single subscription</span></span>](#bkmk_run_1_subscription)

##  <a name="how-to-use-the-scripts"></a><a name="bkmk_how_to"></a> <span data-ttu-id="571aa-118">如何使用指令碼</span><span class="sxs-lookup"><span data-stu-id="571aa-118">How to use the scripts</span></span>

### <a name="permissions"></a><span data-ttu-id="571aa-119">權限</span><span class="sxs-lookup"><span data-stu-id="571aa-119">Permissions</span></span>
 <span data-ttu-id="571aa-120">本節針對原生及 SharePoint 模式 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]，摘要說明使用每個方法所需的權限等級。</span><span class="sxs-lookup"><span data-stu-id="571aa-120">This section summarizes the permission levels required to use each of the methods for both Native and SharePoint mode [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="571aa-121">本主題中的指令碼使用下列 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 方法：</span><span class="sxs-lookup"><span data-stu-id="571aa-121">The scripts in this topic use the following [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] methods:</span></span>

-   [<span data-ttu-id="571aa-122">ReportingService2010.ListSubscriptions 方法</span><span class="sxs-lookup"><span data-stu-id="571aa-122">ReportingService2010.ListSubscriptions Method</span></span>](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.listsubscriptions.aspx)

-   [<span data-ttu-id="571aa-123">ReportingService2010.ChangeSubscriptionOwner 方法</span><span class="sxs-lookup"><span data-stu-id="571aa-123">ReportingService2010.ChangeSubscriptionOwner Method</span></span>](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.changesubscriptionowner.aspx)

-   [<span data-ttu-id="571aa-124">ReportingService2010.ListChildren</span><span class="sxs-lookup"><span data-stu-id="571aa-124">ReportingService2010.ListChildren</span></span>](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.listchildren.aspx)

-   <span data-ttu-id="571aa-125">觸發要執行的特訂訂閱時，才需要在最後一個指令碼中使用 [ReportingService2010.FireEvent](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.fireevent.aspx) (機器翻譯) 方法。</span><span class="sxs-lookup"><span data-stu-id="571aa-125">The method [ReportingService2010.FireEvent](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.fireevent.aspx) is only used in the last script to trigger a specific subscription to run.</span></span> <span data-ttu-id="571aa-126">若您不打算使用該指令碼，可以跳過 FireEvent 方法所需的權限需求。</span><span class="sxs-lookup"><span data-stu-id="571aa-126">If you do not plan to use that script you can ignore the permission requirements for the FireEvent method.</span></span>

 <span data-ttu-id="571aa-127">**原生模式：**</span><span class="sxs-lookup"><span data-stu-id="571aa-127">**Native mode:**</span></span>

-   <span data-ttu-id="571aa-128">列出訂用帳戶：報表上的 ( HYPERLINK " https://technet.microsoft.com/library/microsoft.reportingservices.interfaces.reportoperation.aspx " HTTP://technet.microsoft.com/library/microsoft.reportingservices.interfaces.reportoperation.aspx 報表，而使用者是) 或 ReadAnySubscription 的訂閱擁有者</span><span class="sxs-lookup"><span data-stu-id="571aa-128">List Subscriptions: ( HYPERLINK "https://technet.microsoft.com/library/microsoft.reportingservices.interfaces.reportoperation.aspx" ReadSubscription on the report AND the user is the subscription owner) OR ReadAnySubscription</span></span>

-   <span data-ttu-id="571aa-129">變更訂閱：使用者必須是 BUILTIN\Administrators 群組的成員</span><span class="sxs-lookup"><span data-stu-id="571aa-129">Change Subscriptions: The user must be a member of the BUILTIN\Administrators group</span></span>

-   <span data-ttu-id="571aa-130">列出子系：項目的 ReadProperties</span><span class="sxs-lookup"><span data-stu-id="571aa-130">List Children: ReadProperties on Item</span></span>

-   <span data-ttu-id="571aa-131">引發事件：GenerateEvents (系統)</span><span class="sxs-lookup"><span data-stu-id="571aa-131">Fire Event: GenerateEvents (System)</span></span>

 <span data-ttu-id="571aa-132">**SharePoint 模式：**</span><span class="sxs-lookup"><span data-stu-id="571aa-132">**SharePoint mode:**</span></span>

-   <span data-ttu-id="571aa-133">列出訂用帳戶： ManageAlerts 或 ( HYPERLINK " https://technet.microsoft.com/library/microsoft.sharepoint.spbasepermissions.aspx " (報表 createalerts 在報表上，而使用者是訂閱擁有者，而訂用帳戶是計時訂用帳戶) 。</span><span class="sxs-lookup"><span data-stu-id="571aa-133">List Subscriptions: ManageAlerts OR ( HYPERLINK "https://technet.microsoft.com/library/microsoft.sharepoint.spbasepermissions.aspx" CreateAlerts on the report AND the user is the subscription owner and the subscription is a timed subscription).</span></span>

-   <span data-ttu-id="571aa-134">變更訂閱：ManageWeb</span><span class="sxs-lookup"><span data-stu-id="571aa-134">Change Subscriptions: ManageWeb</span></span>

-   <span data-ttu-id="571aa-135">列出子系：ViewListItems</span><span class="sxs-lookup"><span data-stu-id="571aa-135">List Children: ViewListItems</span></span>

-   <span data-ttu-id="571aa-136">引發事件：ManageWeb</span><span class="sxs-lookup"><span data-stu-id="571aa-136">Fire Event: ManageWeb</span></span>

 <span data-ttu-id="571aa-137">如需詳細資訊，請參閱 [將 Reporting Services 中的角色和工作與 SharePoint 群組和權限做比較](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="571aa-137">For more information, see [Compare Roles and Tasks in Reporting Services to SharePoint Groups and Permissions](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md).</span></span>

### <a name="script-usage"></a><span data-ttu-id="571aa-138">指令碼使用方式</span><span class="sxs-lookup"><span data-stu-id="571aa-138">Script usage</span></span>
 <span data-ttu-id="571aa-139">**建立指令碼檔案 (.ps1)**</span><span class="sxs-lookup"><span data-stu-id="571aa-139">**Create Script files (.ps1)**</span></span>

1.  <span data-ttu-id="571aa-140">建立名為 **c:\scripts**的資料夾。</span><span class="sxs-lookup"><span data-stu-id="571aa-140">Create a folder named **c:\scripts**.</span></span> <span data-ttu-id="571aa-141">若您選擇其他資料夾，則請修改範例命令列陳述式語法中使用的資料夾名稱。</span><span class="sxs-lookup"><span data-stu-id="571aa-141">If you choose a different folder then modify the folder name used in the example command line syntax statements.</span></span>

2.  <span data-ttu-id="571aa-142">為每個指令碼建立文字檔，然後將檔案儲存至 c:\scripts 資料夾。</span><span class="sxs-lookup"><span data-stu-id="571aa-142">Create a text file for each script and save the files to the c:\scripts folder.</span></span> <span data-ttu-id="571aa-143">當您建立 .ps1 檔案時，請使用每個範例命令列語法中的名稱。</span><span class="sxs-lookup"><span data-stu-id="571aa-143">When you create the .ps1 files, use the name from each example command line syntax.</span></span>

3.  <span data-ttu-id="571aa-144">以系統管理權限開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="571aa-144">Open a command prompt with administrative privileges.</span></span>

4.  <span data-ttu-id="571aa-145">執行每個指令碼檔案時，請使用每個範例所提供的範例命令列語法。</span><span class="sxs-lookup"><span data-stu-id="571aa-145">Run each script file, using the sample command line syntax provided with each example.</span></span>

 <span data-ttu-id="571aa-146">**測試的環境**</span><span class="sxs-lookup"><span data-stu-id="571aa-146">**Tested environments**</span></span>

 <span data-ttu-id="571aa-147">本主題中的指令碼測試於 PowerShell 第 3 版，並使用下列版本的 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]：</span><span class="sxs-lookup"><span data-stu-id="571aa-147">The scripts in this topic were tested on PowerShell version 3 and with the following versions of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]:</span></span>

-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]

-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]

-   [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]

##  <a name="script-list-the-ownership-of-all-subscriptions"></a><a name="bkmk_list_ownership_all"></a> <span data-ttu-id="571aa-148">指令碼：列出所有訂閱的擁有權</span><span class="sxs-lookup"><span data-stu-id="571aa-148">Script: List the ownership of all subscriptions</span></span>
 <span data-ttu-id="571aa-149">此指令碼會列出網站的所有訂閱。</span><span class="sxs-lookup"><span data-stu-id="571aa-149">This script lists all of the subscriptions on a site.</span></span> <span data-ttu-id="571aa-150">您可以使用此指令碼測試您的連接，或是確認其他指令碼中使用的報表路徑及訂閱識別碼。</span><span class="sxs-lookup"><span data-stu-id="571aa-150">You can use this script to test your connection or to verify the report path and subscription id for use in the other scripts.</span></span> <span data-ttu-id="571aa-151">若要單純稽核有哪些訂閱以及誰擁有這些訂閱，這會是很實用的指令碼。</span><span class="sxs-lookup"><span data-stu-id="571aa-151">This is also a useful script to simply audit what subscriptions exist and who owns them.</span></span>

### <a name="native-mode-syntax"></a><span data-ttu-id="571aa-152">原生模式語法</span><span class="sxs-lookup"><span data-stu-id="571aa-152">Native mode syntax</span></span>

```cmd
powershell c:\scripts\ListAll_SSRS_Subscriptions.ps1 "[server]/reportserver" "/"
```

### <a name="sharepoint-mode-syntax"></a><span data-ttu-id="571aa-153">SharePoint 模式語法</span><span class="sxs-lookup"><span data-stu-id="571aa-153">SharePoint mode syntax</span></span>

```cmd
powershell c:\scripts\ListAll_SSRS_Subscriptions.ps1 "[server]/_vti_bin/reportserver" "http://[server]"
```

### <a name="script"></a><span data-ttu-id="571aa-154">指令碼</span><span class="sxs-lookup"><span data-stu-id="571aa-154">Script</span></span>

```powershell
# Parameters
#    server   - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)

Param(
    [string]$server,
    [string]$site
   )

$rs2010 += New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;
$subscriptions += $rs2010.ListSubscriptions($site); # use "/" for default native mode site

Write-Host " "
Write-Host "----- $server's Subscriptions: "
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted, Status
```

> [!TIP]
>  <span data-ttu-id="571aa-155">若要以 SharePoint 模式確認網站 URL，請使用 SharePoint Cmdlet **Get-SPSite**。</span><span class="sxs-lookup"><span data-stu-id="571aa-155">To verify site URLS in SharePoint mode, use the SharePoint cmdlet **Get-SPSite**.</span></span> <span data-ttu-id="571aa-156">如需詳細資訊，請參閱 [Get-SPSite](https://technet.microsoft.com/library/ff607950\(v=office.15\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="571aa-156">For more information, see [Get-SPSite](https://technet.microsoft.com/library/ff607950\(v=office.15\).aspx).</span></span>

##  <a name="script-list-all-subscriptions-owned-by-a-specific-user"></a><a name="bkmk_list_all_one_user"></a> <span data-ttu-id="571aa-157">指令碼：列出特定使用者擁有的所有訂閱</span><span class="sxs-lookup"><span data-stu-id="571aa-157">Script: List all subscriptions owned by a specific user</span></span>
 <span data-ttu-id="571aa-158">此指令碼會列出特定使用者所擁有的所有訂閱。</span><span class="sxs-lookup"><span data-stu-id="571aa-158">This script lists all of the subscriptions owned by a specific user.</span></span> <span data-ttu-id="571aa-159">您可以使用此指令碼測試您的連接，或是確認其他指令碼中使用的報表路徑及訂閱識別碼。</span><span class="sxs-lookup"><span data-stu-id="571aa-159">You can use this script to test your connection or to verify the report path and subscription id for use in the other scripts.</span></span> <span data-ttu-id="571aa-160">當您組織中有人離開而您想要確認該人員擁有那些訂閱，好讓您變更擁有者或刪除訂閱時，此指令碼相當實用。</span><span class="sxs-lookup"><span data-stu-id="571aa-160">This script is useful when someone in your organization leaves and you want to verify what subscriptions they owned so you can change the owner or delete the subscription.</span></span>

### <a name="native-mode-syntax"></a><span data-ttu-id="571aa-161">原生模式語法</span><span class="sxs-lookup"><span data-stu-id="571aa-161">Native mode syntax</span></span>

```cmd
powershell c:\scripts\ListAll_SSRS_Subscriptions4User.ps1 "[Domain]\[user]" "[server]/reportserver" "/"
```

### <a name="sharepoint-mode-syntax"></a><span data-ttu-id="571aa-162">SharePoint 模式語法</span><span class="sxs-lookup"><span data-stu-id="571aa-162">SharePoint mode syntax</span></span>

```cmd
powershell c:\scripts\ListAll_SSRS_Subscriptions4User.ps1 "[Domain]\[user]"  "[server]/_vti_bin/reportserver" "http://[server]"
```

### <a name="script"></a><span data-ttu-id="571aa-163">指令碼</span><span class="sxs-lookup"><span data-stu-id="571aa-163">Script</span></span>

```powershell
# Parameters:
#    currentOwner - DOMAIN\USER that owns the subscriptions you wish to change
#    server        - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)
#    site        - use "/" for default native mode site
Param(
    [string]$currentOwner,
    [string]$server,
    [string]$site
)

$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;
$subscriptions += $rs2010.ListSubscriptions($site);

Write-Host " "
Write-Host " "
Write-Host "----- $currentOwner's Subscriptions: "
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted,Status | where {$_.owner -eq $currentOwner}
```

##  <a name="script-change-ownership-for-all-subscriptions-owned-by-a-specific-user"></a><a name="bkmk_change_all"></a> <span data-ttu-id="571aa-164">指令碼：針對特定使用者擁有的所有訂閱變更擁有權</span><span class="sxs-lookup"><span data-stu-id="571aa-164">Script: Change ownership for all subscriptions owned by a specific user</span></span>
 <span data-ttu-id="571aa-165">此指令碼會將特定使用者擁有的所有訂閱擁有權變更至新擁有者參數。</span><span class="sxs-lookup"><span data-stu-id="571aa-165">This script changes the ownership for all subscriptions owned by a specific user to the new owner parameter.</span></span>

### <a name="native-mode-syntax"></a><span data-ttu-id="571aa-166">原生模式語法</span><span class="sxs-lookup"><span data-stu-id="571aa-166">Native mode syntax</span></span>

```cmd
powershell c:\scripts\ChangeALL_SSRS_SubscriptionOwner.ps1 "[Domain]\current owner]" "[Domain]\[new owner]" "[server]/reportserver"
```

### <a name="sharepoint-mode-syntax"></a><span data-ttu-id="571aa-167">SharePoint 模式語法</span><span class="sxs-lookup"><span data-stu-id="571aa-167">SharePoint mode syntax</span></span>

```cmd
powershell c:\scripts\ChangeALL_SSRS_SubscriptionOwner.ps1 "[Domain]\{current owner]" "[Domain]\[new owner]" "[server]/_vti_bin/reportserver"
```

### <a name="script"></a><span data-ttu-id="571aa-168">指令碼</span><span class="sxs-lookup"><span data-stu-id="571aa-168">Script</span></span>

```powershell
# Parameters:
#    currentOwner - DOMAIN\USER that owns the subscriptions you wish to change
#    newOwner      - DOMAIN\USER that will own the subscriptions you wish to change
#    server        - server and instance name (e.g. myserver/reportserver, myserver/reportserver_db2, myserver/_vti_bin/reportserver)

Param(
    [string]$currentOwner,
    [string]$newOwner,
    [string]$server
)

$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;
$items = $rs2010.ListChildren("/", $true);

$subscriptions = @();

ForEach ($item in $items)
{
    if ($item.TypeName -eq "Report")
    {
        $curRepSubs = $rs2010.ListSubscriptions($item.Path);
        ForEach ($curRepSub in $curRepSubs)
        {
            if ($curRepSub.Owner -eq $currentOwner)
            {
                $subscriptions += $curRepSub;
            }
        }
    }
}

Write-Host " "
Write-Host " "
Write-Host -foregroundcolor "green" "-----  $currentOwner's Subscriptions changing ownership to $newOwner : "
$subscriptions | select SubscriptionID, Owner, Path, Description,  Status  | format-table -AutoSize

ForEach ($sub in $subscriptions)
{
    $rs2010.ChangeSubscriptionOwner($sub.SubscriptionID, $newOwner);
}

$subs2 = @();

ForEach ($item in $items)
{
    if ($item.TypeName -eq "Report")
    {
        $subs2 += $rs2010.ListSubscriptions($item.Path);
    }
}
```

##  <a name="script-list-all-subscriptions-associated-with-a-specific-report"></a><a name="bkmk_list_for_1_report"></a> <span data-ttu-id="571aa-169">指令碼：列出與特定報表建立關聯的所有訂閱</span><span class="sxs-lookup"><span data-stu-id="571aa-169">Script: List all subscriptions associated with a specific report</span></span>
 <span data-ttu-id="571aa-170">此指令碼會列出與特定報表相關聯的所有訂閱。</span><span class="sxs-lookup"><span data-stu-id="571aa-170">This script lists all of the subscriptions associated with a specific report.</span></span> <span data-ttu-id="571aa-171">不同之處在於 SharePoint 模式的報表路徑語法，需要完整的 URL。</span><span class="sxs-lookup"><span data-stu-id="571aa-171">The report path syntax is different SharePoint mode which requires a full URL.</span></span> <span data-ttu-id="571aa-172">在語法範例中，使用的報表名稱是 "title only"，其中包含空格，因此需要以單引號將報表名稱括住。</span><span class="sxs-lookup"><span data-stu-id="571aa-172">In the syntax examples, the report name used is "title only", which contains a space and therefore requires the single quotes around the report name.</span></span>

### <a name="native-mode-syntax"></a><span data-ttu-id="571aa-173">原生模式語法</span><span class="sxs-lookup"><span data-stu-id="571aa-173">Native mode syntax</span></span>

```cmd
powershell c:\scripts\List_SSRS_One_Reports_Subscriptions.ps1 "[server]/reportserver" "'/reports/title only'" "/"
```

### <a name="sharepoint-mode-syntax"></a><span data-ttu-id="571aa-174">SharePoint 模式語法</span><span class="sxs-lookup"><span data-stu-id="571aa-174">SharePoint mode syntax</span></span>

```cmd
powershell c:\scripts\List_SSRS_One_Reports_Subscriptions.ps1 "[server]/_vti_bin/reportserver"  "'http://[server]/shared documents/title only.rdl'" "http://[server]"
```

### <a name="script"></a><span data-ttu-id="571aa-175">指令碼</span><span class="sxs-lookup"><span data-stu-id="571aa-175">Script</span></span>

```powershell
# Parameters:
#    server      - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)
#    reportpath  - path to report in the report server, including report name e.g. /reports/test report >> pass in  "'/reports/title only'"
#    site        - use "/" for default native mode site
Param
(
      [string]$server,
      [string]$reportpath,
      [string]$site
)

$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;
$subscriptions += $rs2010.ListSubscriptions($site);

Write-Host " "
Write-Host " "
Write-Host "----- $reportpath 's Subscriptions: "
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted,Status | where {$_.path -eq $reportpath}
```

##  <a name="script-change-ownership-of-a-specific-subscription"></a><a name="bkmk_change_all_1_subscription"></a> <span data-ttu-id="571aa-176">指令碼：變更特定訂閱的擁有權</span><span class="sxs-lookup"><span data-stu-id="571aa-176">Script: Change ownership of a specific subscription</span></span>
 <span data-ttu-id="571aa-177">此指令碼會變更特定訂閱的擁有權。</span><span class="sxs-lookup"><span data-stu-id="571aa-177">This script changes the ownership for a specific subscription.</span></span> <span data-ttu-id="571aa-178">訂閱由您傳遞至指令碼中的 SubscriptionID 所識別。</span><span class="sxs-lookup"><span data-stu-id="571aa-178">The subscription is identified by the SubscriptionID that you pass into the script.</span></span> <span data-ttu-id="571aa-179">您可以使用其中一個列出訂閱的指令碼，以判斷正確的 SubscriptionID。</span><span class="sxs-lookup"><span data-stu-id="571aa-179">You can use one of the list subscription scripts to determine the correct SubscriptionID.</span></span>

### <a name="native-mode-syntax"></a><span data-ttu-id="571aa-180">原生模式語法</span><span class="sxs-lookup"><span data-stu-id="571aa-180">Native mode syntax</span></span>

```cmd
powershell c:\scripts\Change_SSRS_Owner_One_Subscription.ps1 "[Domain]\[new owner]" "[server]/reportserver" "/" "ac5637a1-9982-4d89-9d69-a72a9c3b3150"
```

### <a name="sharepoint-mode-syntax"></a><span data-ttu-id="571aa-181">SharePoint 模式語法</span><span class="sxs-lookup"><span data-stu-id="571aa-181">SharePoint mode syntax</span></span>

```cmd
powershell c:\scripts\Change_SSRS_Owner_One_Subscription.ps1 "[Domain]\[new owner]" "[server]/_vti_bin/reportserver" "http://[server]" "9660674b-f020-453f-b1e3-d9ba37624519"
```

### <a name="script"></a><span data-ttu-id="571aa-182">指令碼</span><span class="sxs-lookup"><span data-stu-id="571aa-182">Script</span></span>

```powershell
# Parameters:
#    newOwner       - DOMAIN\USER that will own the subscriptions you wish to change
#    server         - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)
#    site        - use "/" for default native mode site
#    subscriptionID - guid for the single subscription to change

Param(
    [string]$newOwner,
    [string]$server,
    [string]$site,
    [string]$subscriptionid
   )
$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential;

$subscription += $rs2010.ListSubscriptions($site) | where {$_.SubscriptionID -eq $subscriptionid};

Write-Host " "
Write-Host "----- $subscriptionid's Subscription properties: "
$subscription | select Path, report, Description, SubscriptionID, Owner, Status

$rs2010.ChangeSubscriptionOwner($subscription.SubscriptionID, $newOwner)

#refresh the list
$subscription = $rs2010.ListSubscriptions($site) | where {$_.SubscriptionID -eq $subscriptionid}; # use "/" for default native mode site
Write-Host "----- $subscriptionid's Subscription properties: "
$subscription | select Path, report, Description, SubscriptionID, Owner, Status
```

##  <a name="script-run-fire-a-single-subscription"></a><a name="bkmk_run_1_subscription"></a> <span data-ttu-id="571aa-183">指令碼：執行 (引發) 單一訂閱</span><span class="sxs-lookup"><span data-stu-id="571aa-183">Script: Run (fire) a single subscription</span></span>
 <span data-ttu-id="571aa-184">此指令碼會使用 FireEvent 方法執行特定訂閱。</span><span class="sxs-lookup"><span data-stu-id="571aa-184">This script will run a specific subscription using the FireEvent method.</span></span> <span data-ttu-id="571aa-185">無論為訂閱的設定排程為何，指令碼都會立即執行該訂閱。</span><span class="sxs-lookup"><span data-stu-id="571aa-185">The script will immediately run the subscription regardless of the schedule configured for the subscription.</span></span> <span data-ttu-id="571aa-186">EventType 會根據定義在報表伺服器組態檔 **rsreportserver.config** 中已知的事件集合進行比對。此指令碼會為標準訂閱使用下列事件類型：</span><span class="sxs-lookup"><span data-stu-id="571aa-186">The EventType is matched against the known set of events that are defined in the report server configuration file **rsreportserver.config** The script uses the following event type for standard subscriptions:</span></span>

 `<Event>`

 `<Type>TimedSubscription</Type>`

 `</Event>`

 <span data-ttu-id="571aa-187">如需組態檔的詳細資訊，請參閱＜ [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md)＞。</span><span class="sxs-lookup"><span data-stu-id="571aa-187">For more information on the configuration file, see [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md).</span></span>

 <span data-ttu-id="571aa-188">指令碼包含延遲邏輯 "`Start-Sleep -s 6`"，所以在觸發事件之後會有時間，以透過 ListSubscription 方法取得更新的狀態。</span><span class="sxs-lookup"><span data-stu-id="571aa-188">The script includes delay logic "`Start-Sleep -s 6`" so there is time after the event fires, for the updated status to be available with the ListSubscription method.</span></span>

### <a name="native-mode-syntax"></a><span data-ttu-id="571aa-189">原生模式語法</span><span class="sxs-lookup"><span data-stu-id="571aa-189">Native mode syntax</span></span>

```cmd
powershell c:\scripts\FireSubscription.ps1 "[server]/reportserver" $null "70366e82-2d3c-4edd-a216-b97e51e26de9"
```

### <a name="sharepoint-mode-syntax"></a><span data-ttu-id="571aa-190">SharePoint 模式語法</span><span class="sxs-lookup"><span data-stu-id="571aa-190">SharePoint mode syntax</span></span>

```cmd
powershell c:\scripts\FireSubscription.ps1 "[server]/_vti_bin/reportserver" "http://[server]" "c3425c72-580d-423e-805a-41cf9799fd25"
```

### <a name="script"></a><span data-ttu-id="571aa-191">指令碼</span><span class="sxs-lookup"><span data-stu-id="571aa-191">Script</span></span>

```powershell
# Parameters
#    server         - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)
#    site           - use $null for a native mode server
#    subscriptionid - subscription guid

Param(
  [string]$server,
  [string]$site,
  [string]$subscriptionid
  )

$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;
#event type is case sensative to what is in the rsreportserver.config
$rs2010.FireEvent("TimedSubscription",$subscriptionid,$site)

Write-Host " "
Write-Host "----- Subscription ($subscriptionid) status: "
#get list of subscriptions and filter to the specific ID to see the Status and LastExecuted
Start-Sleep -s 6 # slight delay in processing so ListSubscription returns the updated Status and LastExecuted
$subscriptions = $rs2010.ListSubscriptions($site); 
$subscriptions | select Status, Path, report, Description, Owner, SubscriptionID, EventType, lastexecuted | where {$_.SubscriptionID -eq $subscriptionid}
```

## <a name="see-also"></a><span data-ttu-id="571aa-192">另請參閱</span><span class="sxs-lookup"><span data-stu-id="571aa-192">See Also</span></span>
 <span data-ttu-id="571aa-193"><xref:ReportService2010.ReportingService2010.ListSubscriptions%2A> <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A></span><span class="sxs-lookup"><span data-stu-id="571aa-193"><xref:ReportService2010.ReportingService2010.ListSubscriptions%2A> <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A></span></span> 
 <xref:ReportService2010.ReportingService2010.ListChildren%2A> 
 <xref:ReportService2010.ReportingService2010.FireEvent%2A>
