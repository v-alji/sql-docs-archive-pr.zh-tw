---
title: 從資料庫中擷取 DAC | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.extractdacwizard.buildandsave.f1
- sql12.swb.extractdacwizard.setdacproperties.f1
- sql12.swb.extractdacwizard.validationandsummary.f1
- sql12.swb.extractdacwizard.introduction.f1
- sql12.swb.extractdacwizard.selectdatapage.f1
helpviewer_keywords:
- extract DAC
- How to [DAC], extract
- data-tier application [SQL Server], extract
- wizard [DAC], extract
ms.assetid: ae52a723-91c4-43fd-bcc7-f8de1d1f90e5
author: stevestein
ms.author: sstein
ms.openlocfilehash: bd024af9c201563773e20bae7e5fded1985abbe1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606370"
---
# <a name="extract-a-dac-from-a-database"></a><span data-ttu-id="733cf-102">從資料庫中擷取 DAC</span><span class="sxs-lookup"><span data-stu-id="733cf-102">Extract a DAC From a Database</span></span>
  <span data-ttu-id="733cf-103">您可以使用 [擷取資料層應用程式精靈]  或 Windows PowerShell 指令碼，從現有的 SQL Server 資料庫中擷取資料層應用程式 (DAC) 封裝。</span><span class="sxs-lookup"><span data-stu-id="733cf-103">Use either the **Extract Data-tier Application Wizard** or a Windows PowerShell script to extract a data-tier application (DAC) package from an existing SQL Server database.</span></span> <span data-ttu-id="733cf-104">此擷取程序會建立 DAC 封裝檔案，其中包含資料庫物件及其相關執行個體層級元素的定義。</span><span class="sxs-lookup"><span data-stu-id="733cf-104">The extraction process creates a DAC package file that contains definitions of the database objects and their related instance-level elements.</span></span> <span data-ttu-id="733cf-105">例如，DAC 封裝檔案會包含資料庫資料表、預存程序、檢視表、使用者以及對應至資料庫使用者的登入。</span><span class="sxs-lookup"><span data-stu-id="733cf-105">For example, a DAC package file contains the database tables, stored procedures, views, and users, along with the logins that map to the database users.</span></span>  
  
-   <span data-ttu-id="733cf-106">**開始之前：** [限制事項](#LimitationsRestrictions)、[權限](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="733cf-106">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="733cf-107">**若要使用下列程式來解壓縮 DAC：**  [解壓縮資料層應用程式嚮導](#UsingDACExtractWizard)、 [PowerShell](#ExtractDACPowerShell)</span><span class="sxs-lookup"><span data-stu-id="733cf-107">**To extract a DAC, using:**  [The Extract Data-tier Application Wizard](#UsingDACExtractWizard), [PowerShell](#ExtractDACPowerShell)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="733cf-108">開始之前</span><span class="sxs-lookup"><span data-stu-id="733cf-108">Before You Begin</span></span>  
 <span data-ttu-id="733cf-109">您可以從位於 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]或 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Service Pack 4 或更新版本之執行個體的資料庫中擷取 DAC。</span><span class="sxs-lookup"><span data-stu-id="733cf-109">You can extract a DAC from databases residing on instances of [!INCLUDE[ssSDS](../../includes/sssds-md.md)], or [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Service Pack 4 or later.</span></span> <span data-ttu-id="733cf-110">如果您針對從 DAC 部署的資料庫來執行擷取程序，則只會擷取資料庫中物件的定義。</span><span class="sxs-lookup"><span data-stu-id="733cf-110">If the extraction process is run against a database that was deployed from a DAC, only the definitions of the objects in the database are extracted.</span></span> <span data-ttu-id="733cf-111">此程式不會參考 `msdb`) 中 (**master**註冊的 DAC [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="733cf-111">The process does not reference the DAC registered in `msdb` (**master** in [!INCLUDE[ssSDS](../../includes/sssds-md.md)]).</span></span> <span data-ttu-id="733cf-112">擷取程序不會在目前的 Database Engine 執行個體中註冊 DAC 定義。</span><span class="sxs-lookup"><span data-stu-id="733cf-112">The extraction process does not register the DAC definition in the current instance of the Database Engine.</span></span> <span data-ttu-id="733cf-113">如需有關註冊 DAC 的詳細資訊，請參閱＜ [Register a Database As a DAC](register-a-database-as-a-dac.md)＞。</span><span class="sxs-lookup"><span data-stu-id="733cf-113">For more information about registering a DAC, see [Register a Database As a DAC](register-a-database-as-a-dac.md).</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="733cf-114">限制事項</span><span class="sxs-lookup"><span data-stu-id="733cf-114">Limitations and Restrictions</span></span>  
 <span data-ttu-id="733cf-115">DAC 只能從 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]或 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) 或更新版本的資料庫中進行擷取。</span><span class="sxs-lookup"><span data-stu-id="733cf-115">A DAC can only be extracted from a database in [!INCLUDE[ssSDS](../../includes/sssds-md.md)], or [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) or later.</span></span> <span data-ttu-id="733cf-116">如果 DAC 或包含的使用者中不支援資料庫中的物件，則無法擷取 DAC。</span><span class="sxs-lookup"><span data-stu-id="733cf-116">You cannot extract a DAC if the database has objects that are not supported in a DAC, or contained users.</span></span> <span data-ttu-id="733cf-117">如需有關 DAC 中支援之物件類型的詳細資訊，請參閱＜ [DAC Support For SQL Server Objects and Versions](dac-support-for-sql-server-objects-and-versions.md)＞。</span><span class="sxs-lookup"><span data-stu-id="733cf-117">For more information about the types of objects supported in a DAC, see [DAC Support For SQL Server Objects and Versions](dac-support-for-sql-server-objects-and-versions.md).</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="733cf-118">權限</span><span class="sxs-lookup"><span data-stu-id="733cf-118">Permissions</span></span>  
 <span data-ttu-id="733cf-119">擷取 DAC 至少需要 ALTER ANY LOGIN 和資料庫範圍 VIEW DEFINITION 權限，以及 **sys.sql_expression_dependencies**的 SELECT 權限。</span><span class="sxs-lookup"><span data-stu-id="733cf-119">Extracting a DAC requires at least ALTER ANY LOGIN and database scope VIEW DEFINITION permissions, as well as SELECT permissions on **sys.sql_expression_dependencies**.</span></span> <span data-ttu-id="733cf-120">擷取 DAC 可以透過 securityadmin 固定伺服器角色的成員來完成，這個角色的成員也是擷取 DAC 之來源資料庫中 database_owner 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="733cf-120">Extracting a DAC can be done by members of the securityadmin fixed server role who are also members of the database_owner fixed database role in the database from which the DAC is extracted.</span></span> <span data-ttu-id="733cf-121">sysadmin 固定伺服器角色的成員或是內建 SQL Server 系統管理員帳戶 **sa** 也可以擷取 DAC。</span><span class="sxs-lookup"><span data-stu-id="733cf-121">Members of the sysadmin fixed server role or the built-in SQL Server system administrator account named **sa** can also extract a DAC.</span></span>  
  
##  <a name="using-the-extract-data-tier-application-wizard"></a><a name="UsingDACExtractWizard"></a> <span data-ttu-id="733cf-122">使用擷取資料層應用程式精靈</span><span class="sxs-lookup"><span data-stu-id="733cf-122">Using the Extract Data-tier Application Wizard</span></span>  
 <span data-ttu-id="733cf-123">**使用精靈擷取 DAC**</span><span class="sxs-lookup"><span data-stu-id="733cf-123">**To Extract a DAC Using a Wizard**</span></span>  
  
1.  <span data-ttu-id="733cf-124">在 **[物件總管]** 中，展開含有待擷取 DAC 之資料庫的執行個體的節點。</span><span class="sxs-lookup"><span data-stu-id="733cf-124">In **Object Explorer**, expand the node for the instance containing the database from which the DAC is to be extracted.</span></span>  
  
2.  <span data-ttu-id="733cf-125">展開 **[資料庫]** 節點。</span><span class="sxs-lookup"><span data-stu-id="733cf-125">Expand the **Databases** node.</span></span>  
  
3.  <span data-ttu-id="733cf-126">以滑鼠右鍵按一下待擷取 DAC 之資料庫的節點，並指向 [工作]\*\*\*\*，然後選取 [擷取資料層應用程式...]\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="733cf-126">Right-click the node for the database from which the DAC is to be extracted, point to **Tasks**, and then select **Extract Data-tier Application...**</span></span>  
  
4.  <span data-ttu-id="733cf-127">完成精靈對話方塊：</span><span class="sxs-lookup"><span data-stu-id="733cf-127">Complete the wizard dialogs:</span></span>  
  
    1.  [<span data-ttu-id="733cf-128">簡介頁面</span><span class="sxs-lookup"><span data-stu-id="733cf-128">Introduction Page</span></span>](#Introduction)  
  
    2.  [<span data-ttu-id="733cf-129">選取資料頁面</span><span class="sxs-lookup"><span data-stu-id="733cf-129">Select Data Page</span></span>](#SelectData)  
  
    3.  [<span data-ttu-id="733cf-130">設定屬性頁面</span><span class="sxs-lookup"><span data-stu-id="733cf-130">Set Properties Page</span></span>](#SetProperties)  
  
    4.  [<span data-ttu-id="733cf-131">驗證與摘要頁面</span><span class="sxs-lookup"><span data-stu-id="733cf-131">Validation and Summary Page</span></span>](#ValidateSummary)  
  
    5.  [<span data-ttu-id="733cf-132">建立封裝頁面</span><span class="sxs-lookup"><span data-stu-id="733cf-132">Build Package Page</span></span>](#BuildPackage)  
  
###  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="733cf-133">簡介頁面</span><span class="sxs-lookup"><span data-stu-id="733cf-133">Introduction Page</span></span>  
 <span data-ttu-id="733cf-134">此頁面描述擷取資料層應用程式的步驟。</span><span class="sxs-lookup"><span data-stu-id="733cf-134">This page describes the steps for extracting a data-tier application.</span></span>  
  
 <span data-ttu-id="733cf-135">**不要再顯示此頁面。**</span><span class="sxs-lookup"><span data-stu-id="733cf-135">**Do not show this page again.**</span></span> <span data-ttu-id="733cf-136">- 按一下此核取方塊，之後就不會再顯示此頁面。</span><span class="sxs-lookup"><span data-stu-id="733cf-136">- Click the check box to stop the page from being displayed in the future.</span></span>  
  
 <span data-ttu-id="733cf-137">**下一步 >** - 繼續進行至 [選擇方法]\*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="733cf-137">**Next >** - Proceeds to the **Choose Method** page.</span></span>  
  
 <span data-ttu-id="733cf-138">**取消** ：結束精靈，不從資料庫中擷取資料層應用程式。</span><span class="sxs-lookup"><span data-stu-id="733cf-138">**Cancel** - Ends the wizard without extracting a data-tier application from the database.</span></span>  
  
###  <a name="select-data-page"></a><a name="SelectData"></a><span data-ttu-id="733cf-139">選取資料頁面</span><span class="sxs-lookup"><span data-stu-id="733cf-139">Select Data Page</span></span>  
 <span data-ttu-id="733cf-140">使用精靈的這個頁面，選取您想要包含在資料層應用程式 (DAC) 封裝檔案中的參考資料。</span><span class="sxs-lookup"><span data-stu-id="733cf-140">Use this page of the wizard to select the reference data that you want to include in your data-tier application (DAC) package file.</span></span> <span data-ttu-id="733cf-141">在您的 DAC 封裝檔案中包含資料是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="733cf-141">Including data in your DAC package is optional.</span></span> <span data-ttu-id="733cf-142">DAC 封裝已包含所有受支援資料庫物件和資料庫相關執行個體物件的結構描述。</span><span class="sxs-lookup"><span data-stu-id="733cf-142">The DAC package will already include the schema of all supported database objects and instance objects related to your database.</span></span>  
  
 <span data-ttu-id="733cf-143">您可以在 DAC 封裝檔案中最多包含 10 MB 的參考資料。</span><span class="sxs-lookup"><span data-stu-id="733cf-143">You can include up to 10 MB of reference data in your DAC package file.</span></span> <span data-ttu-id="733cf-144">不過，若要在 DAC 包含資料表，資料表不可以包含二進位大型物件 (BLOB) 資料類型，例如 **image** 或 **varchar(max)**。</span><span class="sxs-lookup"><span data-stu-id="733cf-144">However, for tables to be included in the DAC, they may not contain binary large object (BLOB) data types such as **image** or **varchar(max)**.</span></span> <span data-ttu-id="733cf-145">若要擷取大量資料以傳送至另一個資料庫，請使用 SQL Server Integration Services、大量複製公用程式或許多其他資料移轉技術。</span><span class="sxs-lookup"><span data-stu-id="733cf-145">To extract larger amounts of data for transferring to another database, use SQL Server Integration Services, the bulk copy utility, or one of many other data migration techniques.</span></span>  
  
 <span data-ttu-id="733cf-146">**資料庫資料表** ：選取資料庫資料表旁邊的核取方塊，這些資料庫資料表包含您要併入 DAC 封裝中的資料。</span><span class="sxs-lookup"><span data-stu-id="733cf-146">**Database table** - Select the check box next to the database tables which contain the data that you want to include in your DAC package.</span></span> <span data-ttu-id="733cf-147">您最多可以選取十個不超過 10,000 資料列的資料表。</span><span class="sxs-lookup"><span data-stu-id="733cf-147">You can select up to ten tables that have 10,000 rows or less.</span></span>  
  
###  <a name="set-properties-page"></a><a name="SetProperties"></a> <span data-ttu-id="733cf-148">設定屬性頁面</span><span class="sxs-lookup"><span data-stu-id="733cf-148">Set Properties Page</span></span>  
 <span data-ttu-id="733cf-149">您可以使用此精靈的這個頁面來描述資料層應用程式 (DAC)。</span><span class="sxs-lookup"><span data-stu-id="733cf-149">Use this page of the wizard to describe the data-tier application (DAC).</span></span> <span data-ttu-id="733cf-150">這些屬性會用來識別 DAC，並協助您區別其他項目。</span><span class="sxs-lookup"><span data-stu-id="733cf-150">These properties are used to identify the DAC and help distinguish it from others.</span></span>  
  
 <span data-ttu-id="733cf-151">**名稱** ：此名稱會識別 DAC。</span><span class="sxs-lookup"><span data-stu-id="733cf-151">**Name** - This name identifies the DAC.</span></span> <span data-ttu-id="733cf-152">它可能與 DAC 封裝檔案的名稱不同，而且應該會描述您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="733cf-152">It can be different than the name of the DAC package file and should describe your application.</span></span> <span data-ttu-id="733cf-153">例如，如果此資料庫用於財務應用程式，您可能會想要命名為 DAC Finance。</span><span class="sxs-lookup"><span data-stu-id="733cf-153">For example, if the database is used for a finance application, you may wish to name the DAC Finance.</span></span>  
  
 <span data-ttu-id="733cf-154">**版本 (使用 xx.xx.xx.xx，其中 x 是數字)** ：識別 DAC 版本的數值。</span><span class="sxs-lookup"><span data-stu-id="733cf-154">**Version (use xx.xx.xx.xx, where x is a number)** - A numeric value that identifies the version of the DAC.</span></span> <span data-ttu-id="733cf-155">DAC 版本會用於 Visual Studio 中，以便識別開發人員正在處理的 DAC 版本。</span><span class="sxs-lookup"><span data-stu-id="733cf-155">The DAC version is used in Visual Studio to identify the version of the DAC that developers are working on.</span></span> <span data-ttu-id="733cf-156">部署 DAC 時，版本會儲存在資料庫中， `msdb` 並可于稍後在的 [**資料層應用程式**] 節點下查看 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="733cf-156">When deploying a DAC, the version is stored in the `msdb` database and can later be viewed under the **Data-tier Applications** node in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="733cf-157">**描述** ：選擇性。</span><span class="sxs-lookup"><span data-stu-id="733cf-157">**Description:** - Optional.</span></span> <span data-ttu-id="733cf-158">描述此 DAC。</span><span class="sxs-lookup"><span data-stu-id="733cf-158">Describes the DAC.</span></span> <span data-ttu-id="733cf-159">部署 DAC 時，此描述會儲存在資料庫中， `msdb` 並可于稍後在的 [**資料層應用程式**] 節點下查看 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="733cf-159">When deploying a DAC, the description is stored in the `msdb` database and can later be viewed under the **Data-tier Applications** node in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
 <span data-ttu-id="733cf-160">**儲存至 DAC 封裝檔案 (檔案名稱包含 .dacpac 副檔名)** ：將 DAC 儲存至副檔名為 .dacpac 的 DAC 封裝檔案。</span><span class="sxs-lookup"><span data-stu-id="733cf-160">**Save to DAC package file (include .dacpac extension with file name):** - Saves the DAC to a DAC package file, with a .dacpac extension.</span></span> <span data-ttu-id="733cf-161">按一下 **[瀏覽]** 按鈕，即可指定檔案的名稱和位置。</span><span class="sxs-lookup"><span data-stu-id="733cf-161">Click the **Browse** button to specify a name and location for the file.</span></span>  
  
 <span data-ttu-id="733cf-162">**覆寫現有檔案** ：如果已經有同名的 DAC 封裝檔案，請選取此核取方塊來取代該檔案。</span><span class="sxs-lookup"><span data-stu-id="733cf-162">**Overwrite existing file** - Select this check box to replace the DAC package file if one already exists with the same name.</span></span>  
  
###  <a name="validation-and-summary-page"></a><a name="ValidateSummary"></a> <span data-ttu-id="733cf-163">驗證與摘要頁面</span><span class="sxs-lookup"><span data-stu-id="733cf-163">Validation and Summary Page</span></span>  
 <span data-ttu-id="733cf-164">在這個頁面上，此精靈會驗證資料層應用程式 (DAC) 是否支援所有資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="733cf-164">On this page, the wizard validates that all database objects are supported by a data-tier application (DAC).</span></span> <span data-ttu-id="733cf-165">此外，它也會檢查資料庫物件之間的相依性，以便判斷可成功包含在 DAC 中的物件集合。</span><span class="sxs-lookup"><span data-stu-id="733cf-165">It also checks dependencies across database objects to determine the set of objects that can be successfully included in the DAC.</span></span> <span data-ttu-id="733cf-166">之後，它會顯示驗證報表並摘要列出您在這個精靈中所選取的選項。</span><span class="sxs-lookup"><span data-stu-id="733cf-166">After that, it displays the validation report and summarizes the options that you have selected in this wizard.</span></span> <span data-ttu-id="733cf-167">若要變更選項，請按 **[上一步]** 。</span><span class="sxs-lookup"><span data-stu-id="733cf-167">To change an option, click **Previous**.</span></span> <span data-ttu-id="733cf-168">若要開始擷取 DAC，請按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="733cf-168">To begin extracting a DAC, click **Next**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="733cf-169">如果 DAC 不支援一個或多個物件，則會停用 **[下一步]** 按鈕，而且擷取程序可能會無法繼續。</span><span class="sxs-lookup"><span data-stu-id="733cf-169">If one or more objects are not supported by a DAC, then the **Next** button is disabled and the extraction process may not continue.</span></span> <span data-ttu-id="733cf-170">在這種情況下，建議您移除不支援的物件，然後再次執行此精靈。</span><span class="sxs-lookup"><span data-stu-id="733cf-170">In such cases, it is recommended to remove the non-supported objects and then run this wizard again.</span></span>  
  
 <span data-ttu-id="733cf-171">**摘要**：所選取的選項摘要會列在 [DAC 屬性]  底下。</span><span class="sxs-lookup"><span data-stu-id="733cf-171">**Summary** - A summary of the options you have selected are listed under **DAC properties**.</span></span> <span data-ttu-id="733cf-172">驗證的結果則列在 **[DAC 物件]** 底下。</span><span class="sxs-lookup"><span data-stu-id="733cf-172">The results of the validation are listed under **DAC objects**.</span></span> <span data-ttu-id="733cf-173">驗證的結果有三種類型：</span><span class="sxs-lookup"><span data-stu-id="733cf-173">There are three types of results from the validation:</span></span>  
  
-   <span data-ttu-id="733cf-174">**物件成功包含在 DAC 中**：表示這些物件及其相依性受到支援，而且可以成功包含在 DAC 中。</span><span class="sxs-lookup"><span data-stu-id="733cf-174">**Objects included in DAC successfully**: these objects and their dependencies are supported, and can be included in the DAC successfully.</span></span>  
  
-   <span data-ttu-id="733cf-175">**物件包含在 DAC 中，但是出現警告**：表示雖然這些物件受到支援，不過卻相依於 DAC 不支援的其他物件。</span><span class="sxs-lookup"><span data-stu-id="733cf-175">**Objects included in DAC with warnings**: these objects are supported, but depend on other objects that are not supported in a DAC.</span></span>  
  
-   <span data-ttu-id="733cf-176">**物件未包含在 DAC 中**：表示這些物件不受到支援，而且必須從資料庫中移除它們，然後才能成功擷取 DAC。</span><span class="sxs-lookup"><span data-stu-id="733cf-176">**Objects not included in DAC**: these objects are not supported and must be removed from the database before successfully extracting a DAC.</span></span>  
  
 <span data-ttu-id="733cf-177">驗證程序會檢查多個相依性層級。</span><span class="sxs-lookup"><span data-stu-id="733cf-177">The validation process checks multiple levels of dependencies.</span></span> <span data-ttu-id="733cf-178">例如，如果某個預存程序相依於使用不支援之 CLR 資料類型的資料表，此預存程序就會列在 **[物件包含在 DAC 中，但是出現警告]** 底下。</span><span class="sxs-lookup"><span data-stu-id="733cf-178">For example, if a stored procedure depends on a table that uses the unsupported CLR data type, the stored procedure will be listed under **Objects included in DAC with warnings**.</span></span>  
  
 <span data-ttu-id="733cf-179">如果 DAC 不支援一個或多個物件， **[下一步]** 按鈕就會停用，而且擷取程序將無法繼續。</span><span class="sxs-lookup"><span data-stu-id="733cf-179">If one or more objects are not supported by a DAC, then the **Next** button is disabled and the extraction process will not continue.</span></span> <span data-ttu-id="733cf-180">在這種情況下，建議您移除不支援的物件，然後再次執行此精靈。</span><span class="sxs-lookup"><span data-stu-id="733cf-180">In such cases, it is recommended to remove the objects that are not supported and then run this wizard again.</span></span>  
  
 <span data-ttu-id="733cf-181">**儲存報表**：可讓您儲存以 HTML 為基礎的檔案，其中列出摘要之 [DAC 物件]  節點底下的所有物件。</span><span class="sxs-lookup"><span data-stu-id="733cf-181">**Save Report** - Enables you to save an HTML-based file that lists all of the objects under the **DAC Objects** node in the summary.</span></span> <span data-ttu-id="733cf-182">當 DAC 不支援部分資料庫物件時，這份報表可能會很有用。</span><span class="sxs-lookup"><span data-stu-id="733cf-182">This report can be useful when some of your database objects are not supported in a DAC.</span></span> <span data-ttu-id="733cf-183">您可以先使用此報表來變更或移除不支援的物件，然後再次嘗試擷取 DAC。</span><span class="sxs-lookup"><span data-stu-id="733cf-183">Use the report to change or remove objects that are not supported, before trying to extract the DAC again.</span></span>  
  
###  <a name="build-package-page"></a><a name="BuildPackage"></a><span data-ttu-id="733cf-184">組建封裝頁面</span><span class="sxs-lookup"><span data-stu-id="733cf-184">Build Package Page</span></span>  
 <span data-ttu-id="733cf-185">您可以使用這個頁面來監視此精靈擷取資料層應用程式 (DAC) 的進度。</span><span class="sxs-lookup"><span data-stu-id="733cf-185">Use this page to monitor the progress of the wizard as it extracts the data-tier application (DAC).</span></span>  
  
 <span data-ttu-id="733cf-186">**動作**：在 [建立並儲存 DAC 封裝檔案]  動作期間，此精靈會從 SQL Server 資料庫中擷取 DAC。</span><span class="sxs-lookup"><span data-stu-id="733cf-186">**Action** - During the **Create and save DAC package file** action, the wizard extracts a DAC from your SQL Server database.</span></span> <span data-ttu-id="733cf-187">然後，它會在記憶體中建立 DAC 封裝並儲存至您所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="733cf-187">Then, a DAC package is created in memory and saved to the location you specified.</span></span> <span data-ttu-id="733cf-188">若要查看對應步驟的結果，請按一下 **[結果]** 欄中的連結。</span><span class="sxs-lookup"><span data-stu-id="733cf-188">Click on the links in the **Result** column to see the outcome of the corresponding step.</span></span>  
  
 <span data-ttu-id="733cf-189">**儲存報表** ：按一下即可將精靈進度的結果儲存至檔案。</span><span class="sxs-lookup"><span data-stu-id="733cf-189">**Save Report** - Click to save the results of the wizard's progress to a file.</span></span>  
  
 <span data-ttu-id="733cf-190">**完成** ：在處理完成之後或是發生錯誤時，按一下即可關閉精靈。</span><span class="sxs-lookup"><span data-stu-id="733cf-190">**Finish** - Click to close the wizard after processing has completed, or if an error occurs.</span></span>  
  
##  <a name="extract-a-dac-using-powershell"></a><a name="ExtractDACPowerShell"></a><span data-ttu-id="733cf-191">使用 PowerShell 來解壓縮 DAC</span><span class="sxs-lookup"><span data-stu-id="733cf-191">Extract a DAC Using PowerShell</span></span>  
 <span data-ttu-id="733cf-192">**在 PowerShell 指令碼中使用 Extract() 方法，從資料庫中擷取 DAC**</span><span class="sxs-lookup"><span data-stu-id="733cf-192">**To extract a DAC from a database using the Extract() method in a PowerShell script**</span></span>  
  
1.  <span data-ttu-id="733cf-193">建立 SMO Server 物件，並將它設為含有待擷取 DAC 之資料庫的執行個體。</span><span class="sxs-lookup"><span data-stu-id="733cf-193">Create a SMO Server object and set it to the instance that contains the database from which the DAC is to be extracted.</span></span>  
  
2.  <span data-ttu-id="733cf-194">加入可指定資料庫名稱的變數。</span><span class="sxs-lookup"><span data-stu-id="733cf-194">Add a variable that specifies the name of the database.</span></span>  
  
3.  <span data-ttu-id="733cf-195">指定 DAC 的中繼資料，例如 DAC 名稱、版本及描述。</span><span class="sxs-lookup"><span data-stu-id="733cf-195">Specify the metadata for the DAC, such as the DAC name, version, and description.</span></span>  
  
4.  <span data-ttu-id="733cf-196">為已擷取的 DAC 封裝檔案指定路徑和檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="733cf-196">Specify the path and file name for the extracted DAC package file.</span></span>  
  
5.  <span data-ttu-id="733cf-197">使用上述指定的資訊執行擷取方法。</span><span class="sxs-lookup"><span data-stu-id="733cf-197">Run the Extract method with the information specified above.</span></span>  
  
### <a name="example-powershell"></a><span data-ttu-id="733cf-198">範例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="733cf-198">Example (PowerShell)</span></span>  
 <span data-ttu-id="733cf-199">下列範例會從 MyDB 資料庫中擷取名為 MyApplication 的 DAC。</span><span class="sxs-lookup"><span data-stu-id="733cf-199">The following example extracts a DAC named MyApplication from a database named MyDB.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Specify the database to extract to a DAC.  
$dbname = "MyDB"  
  
## Specify the DAC metadata.  
$applicationname = "MyApplication"  
$version = "1.0.0.0"  
$description = "This DAC defines the database used by my application."  
  
## Specify the location and name for the extracted DAC package.  
$dacpacPath = "C:\MyDACs\MyApplication.dacpac"  
  
## Extract the DAC.  
$extractionunit = New-Object Microsoft.SqlServer.Management.Dac.DacExtractionUnit($srv, $dbname, $applicationname, $version)  
$extractionunit.Description = $description  
$extractionunit.Extract($dacpacPath)  
```  
  
## <a name="see-also"></a><span data-ttu-id="733cf-200">另請參閱</span><span class="sxs-lookup"><span data-stu-id="733cf-200">See Also</span></span>  
 [<span data-ttu-id="733cf-201">資料層應用程式</span><span class="sxs-lookup"><span data-stu-id="733cf-201">Data-tier Applications</span></span>](data-tier-applications.md)  
