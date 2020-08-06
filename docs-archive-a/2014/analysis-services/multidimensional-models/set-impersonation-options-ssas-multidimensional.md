---
title: 將模擬選項設定 (SSAS-多維度) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.impersonationinfo.f1
helpviewer_keywords:
- Impersonation Information dialog box
ms.assetid: 8e127f72-ef23-44ad-81e6-3dd58981770e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9b9a8526ff4b8a6dd6f68d13817e427ec70d1953
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598021"
---
# <a name="set-impersonation-options-ssas---multidimensional"></a><span data-ttu-id="a8a16-102">設定模擬選項 (SSAS - 多維度)</span><span class="sxs-lookup"><span data-stu-id="a8a16-102">Set Impersonation Options (SSAS - Multidimensional)</span></span>
  <span data-ttu-id="a8a16-103">在 Analysis Services 模型中建立 `data source` 物件時，您必須進行的其中一項設定就是模擬選項。</span><span class="sxs-lookup"><span data-stu-id="a8a16-103">When creating a `data source` object in an Analysis Services model, one of the settings that you must configure is an impersonation option.</span></span> <span data-ttu-id="a8a16-104">此選項會決定當執行與連接有關的本機作業時，Analysis Services 是否採用特定 Windows 使用者帳戶的識別，例如在支援漫遊設定檔的環境中載入 OLE DB 資料提供者或解析使用者設定檔資訊。</span><span class="sxs-lookup"><span data-stu-id="a8a16-104">This option determines whether Analysis Services assumes the identity of a specific Windows user account when performing local operations related to the connection, such as loading an OLE DB data provider or resolving user profile information in environments that support roaming profiles.</span></span>  
  
 <span data-ttu-id="a8a16-105">如果是使用 Windows 驗證的連接，則模擬選項也會決定在外部資料來源執行查詢所使用的使用者識別。</span><span class="sxs-lookup"><span data-stu-id="a8a16-105">For connections that use Windows authentication, the impersonation option also determines the user identity under which queries execute on the external data source.</span></span> <span data-ttu-id="a8a16-106">例如，如果您將模擬選項設定為 **contoso\dbuser**，則在處理期間用來擷取資料的查詢將會以資料庫伺服器上的 **contoso\dbuser** 身分執行。</span><span class="sxs-lookup"><span data-stu-id="a8a16-106">For example, if you set the impersonation option to **contoso\dbuser**, queries used to retrieve data during processing will execute as **contoso\dbuser** on the database server.</span></span>  
  
 <span data-ttu-id="a8a16-107">本主題說明在設定資料來源物件時，如何在 [模擬資訊]\*\*\*\* 對話方塊中設定模擬選項。</span><span class="sxs-lookup"><span data-stu-id="a8a16-107">This topic explains how to set impersonation options in the **Impersonation Information** dialog box when configuring a data source object.</span></span>  
  
## <a name="set-impersonation-options-in-sql-server-data-tools"></a><span data-ttu-id="a8a16-108">在 SQL Server Data Tools 中設定模擬選項</span><span class="sxs-lookup"><span data-stu-id="a8a16-108">Set impersonation options in SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="a8a16-109">在 [方案總管] 中，按兩下資料來源開啟 [資料來源設計師]。</span><span class="sxs-lookup"><span data-stu-id="a8a16-109">Double-click a data source in Solution Explorer to open Data Source Designer.</span></span>  
  
2.  <span data-ttu-id="a8a16-110">按一下 [資料來源設計師] 中的 [模擬資訊]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="a8a16-110">Click the **Impersonation Information** tab in Data Source Designer.</span></span>  
  
3.  <span data-ttu-id="a8a16-111">選擇本主題的 [模擬選項](#bkmk_options) 所述的選項。</span><span class="sxs-lookup"><span data-stu-id="a8a16-111">Choose an option described in [Impersonation options](#bkmk_options) in this topic.</span></span>  
  
## <a name="set-impersonation-options-in-management-studio"></a><span data-ttu-id="a8a16-112">在 Management Studio 中設定模擬選項</span><span class="sxs-lookup"><span data-stu-id="a8a16-112">Set impersonation options in Management Studio</span></span>  
 <span data-ttu-id="a8a16-113">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中，針對這些對話方塊的下列屬性按一下省略符號 (**...**) 按鈕，以開啟 [模擬資訊]\*\*\*\* 對話方塊：</span><span class="sxs-lookup"><span data-stu-id="a8a16-113">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], open the **Impersonation Information** dialog box by clicking the ellipsis (**...**) button for the following properties of these dialog boxes:</span></span>  
  
-   <span data-ttu-id="a8a16-114">[資料庫屬性]\*\*\*\* 對話方塊，透過 [資料來源模擬資訊] 屬性。</span><span class="sxs-lookup"><span data-stu-id="a8a16-114">**Database Properties** dialog box, through the Data Source Impersonation Info property.</span></span>  
  
-   <span data-ttu-id="a8a16-115">[資料來源屬性]\*\*\*\* 對話方塊，透過 [模擬資訊] 屬性。</span><span class="sxs-lookup"><span data-stu-id="a8a16-115">**Data Source Properties** dialog box, through the Impersonation Info property.</span></span>  
  
-   <span data-ttu-id="a8a16-116">[組件屬性]\*\*\*\* 對話方塊，透過 [模擬資訊] 屬性。</span><span class="sxs-lookup"><span data-stu-id="a8a16-116">**Assembly Properties** dialog box, through the Impersonation Info property.</span></span>  
  
##  <a name="impersonation-options"></a><a name="bkmk_options"></a> <span data-ttu-id="a8a16-117">模擬選項</span><span class="sxs-lookup"><span data-stu-id="a8a16-117">Impersonation options</span></span>  
 <span data-ttu-id="a8a16-118">對話方塊中的所有選項都可以使用，但並非所有選項都適合所有案例。</span><span class="sxs-lookup"><span data-stu-id="a8a16-118">All options are available in the dialog box, but not all options are appropriate for every scenario.</span></span> <span data-ttu-id="a8a16-119">請使用下列資訊來確定最適合您案例的選項。</span><span class="sxs-lookup"><span data-stu-id="a8a16-119">Use the following information to determine the best option for your scenario.</span></span>  
  
 <span data-ttu-id="a8a16-120">**使用特定的使用者名稱和密碼**</span><span class="sxs-lookup"><span data-stu-id="a8a16-120">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="a8a16-121">選取此選項，讓 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 物件使用以下列格式指定之 Windows 使用者帳戶的安全性認證： *\<Domain name>***\\***\<User account name>* 。</span><span class="sxs-lookup"><span data-stu-id="a8a16-121">Select this option to have the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object use the security credentials of a Windows user account specified in this format: *\<Domain name>***\\***\<User account name>*.</span></span>  
  
 <span data-ttu-id="a8a16-122">選擇此選項，即可使用您專為資料存取目的所建立的專用最低權限 Windows 使用者識別。</span><span class="sxs-lookup"><span data-stu-id="a8a16-122">Choose this option to use a dedicated, least-privilege Windows user identity that you have created specifically for data access purposes.</span></span> <span data-ttu-id="a8a16-123">例如，如果您習慣建立一般用途帳戶來擷取報表中使用的資料，則可以在此指定該帳戶。</span><span class="sxs-lookup"><span data-stu-id="a8a16-123">For example, if you routinely create a general purpose account for retrieving data used in reports, you can specify that account here.</span></span>  
  
 <span data-ttu-id="a8a16-124">若為多維度資料庫，指定的認證將用於處理、ROLAP 查詢、非正規 (out-of-line) 繫結、本機 Cube、採礦模型、遠端資料分割、連結物件以及從目標到來源的同步處理。</span><span class="sxs-lookup"><span data-stu-id="a8a16-124">For multidimensional databases, the specified credentials will be used for processing, ROLAP queries, out-of-line bindings, local cubes, mining models, remote partitions, linked objects, and synchronization from target to source.</span></span>  
  
 <span data-ttu-id="a8a16-125">若為表格式資料庫，指定的認證將用於處理、針對關聯式資料存放區執行的查詢 (使用 DirectQuery)、非正規 (out-of-line) 繫結、遠端資料分割以及從目標到來源的同步處理。</span><span class="sxs-lookup"><span data-stu-id="a8a16-125">For tabular databases, the specified credentials will be used for processing, queries that run against a relational data store (using DirectQuery), out-of-line bindings, remote partitions, and synchronization from target to source.</span></span>  
  
 <span data-ttu-id="a8a16-126">若為 DMX OPENQUERY 陳述式，系統將忽略這個選項，並且使用目前使用者的認證，而非指定的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="a8a16-126">For DMX OPENQUERY statements, this option is ignored and the credentials of the current user will be used rather than the specified user account.</span></span>  
  
 <span data-ttu-id="a8a16-127">**使用服務帳戶**</span><span class="sxs-lookup"><span data-stu-id="a8a16-127">**Use the service account**</span></span>  
 <span data-ttu-id="a8a16-128">選取此選項即可讓 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 物件使用與管理該物件之 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 服務相關聯的安全性認證。</span><span class="sxs-lookup"><span data-stu-id="a8a16-128">Select this option to have the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object use the security credentials associated with the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] service that manages the object.</span></span> <span data-ttu-id="a8a16-129">這是預設選項。</span><span class="sxs-lookup"><span data-stu-id="a8a16-129">This is the default option.</span></span> <span data-ttu-id="a8a16-130">在舊版中，這是您可以使用的唯一選項。</span><span class="sxs-lookup"><span data-stu-id="a8a16-130">In previous releases, this was the only option you could use.</span></span> <span data-ttu-id="a8a16-131">若要監視服務等級的資料存取，而不是個別使用者帳戶，建議您使用此選項。</span><span class="sxs-lookup"><span data-stu-id="a8a16-131">You might prefer this option to monitor data access at the service level rather than individual user accounts.</span></span>  
  
 <span data-ttu-id="a8a16-132">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中，服務帳戶可能是 NetworkService 或針對特定 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體所建立的內建虛擬帳戶 (視您使用的作業系統而定)。</span><span class="sxs-lookup"><span data-stu-id="a8a16-132">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], depending on the operating system you are using, the service account might be NetworkService or a built-in virtual account created for a specific [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="a8a16-133">如果您針對使用 Windows 驗證的連接選擇此服務帳戶，請記得要為這個帳戶建立資料庫登入並授與讀取權限，因為它將在處理期間用來擷取資料。</span><span class="sxs-lookup"><span data-stu-id="a8a16-133">If you choose the service account for a connection that uses Windows authentication, remember to create a database login for this account and grant read permissions, as it will be used to retrieve data during processing.</span></span> <span data-ttu-id="a8a16-134">如需服務帳戶的詳細資訊，請參閱 [設定 Windows 服務帳戶和權限](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="a8a16-134">For more information about the service account, see [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a8a16-135">當您使用資料庫驗證時，如果服務是在 Analysis Services 的專用虛擬帳戶之下執行，您應該選擇 [使用服務帳戶]\*\*\*\* 模擬選項。</span><span class="sxs-lookup"><span data-stu-id="a8a16-135">When using database authentication, you should choose the **Use the service account** impersonation option if the service is running under the dedicated virtual account for Analysis Services.</span></span> <span data-ttu-id="a8a16-136">此帳戶將具有存取本機檔案的權限。</span><span class="sxs-lookup"><span data-stu-id="a8a16-136">This account will have permissions to access local files.</span></span> <span data-ttu-id="a8a16-137">如果此服務是以 NetworkService 身分執行，更好的替代方式是使用具有 [允許本機登入]\*\*\*\* 權限的最低權限 Windows 使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="a8a16-137">If the service runs as NetworkService, a better alternative is to use a least privilege Windows user account that has **Allow log on locally** permissions.</span></span> <span data-ttu-id="a8a16-138">根據您提供的帳戶而定，您可能也需要授與 Analysis Services 程式資料夾的檔案存取權限。</span><span class="sxs-lookup"><span data-stu-id="a8a16-138">Depending on the account you provide, you might also need to grant file access permissions on the Analysis Services program folder.</span></span>  
  
 <span data-ttu-id="a8a16-139">若為多維度資料庫，服務帳戶認證將用於處理、ROLAP 查詢、遠端資料分割、連結物件以及從目標到來源的同步處理。</span><span class="sxs-lookup"><span data-stu-id="a8a16-139">For multidimensional databases, the service account credentials will be used for processing, ROLAP queries, remote partitions, linked objects, and synchronization from target to source.</span></span>  
  
 <span data-ttu-id="a8a16-140">若為表格式資料庫，指定的認證將用於處理、針對關聯式資料存放區執行的查詢 (使用 DirectQuery)、遠端資料分割以及從目標到來源的同步處理。</span><span class="sxs-lookup"><span data-stu-id="a8a16-140">For tabular databases, the specified credentials will be used for processing, queries that run against a relational data store (using DirectQuery), remote partitions, and synchronization from target to source.</span></span>  
  
 <span data-ttu-id="a8a16-141">若是 DMX OPENQUERY 陳述式、本機 Cube 和採礦模型，即使選擇服務帳戶選項，也會使用目前使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="a8a16-141">For DMX OPENQUERY statements, local cubes, and mining models, the credentials of the current user will be used even if you choose the service account option.</span></span> <span data-ttu-id="a8a16-142">非正規 (out-of-line) 繫結不支援服務帳戶選項。</span><span class="sxs-lookup"><span data-stu-id="a8a16-142">The service account option is not supported for out-of-line bindings.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a8a16-143">如果服務帳戶沒有 Analysis Services 執行個體的管理員權限，則從 Cube 處理資料採礦模型時可能會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="a8a16-143">Errors can occur when processing a data mining model from a cube if the service account does not have administrator permissions on the Analysis Services instance.</span></span> <span data-ttu-id="a8a16-144">如需詳細資訊，請參閱 [採礦結構：當資料來源為 OLAP Cube 時的處理問題](https://go.microsoft.com/fwlink/?LinkId=251610)。</span><span class="sxs-lookup"><span data-stu-id="a8a16-144">For more information, see [Mining Structure: Issue while Processing when DataSource is OLAP Cube](https://go.microsoft.com/fwlink/?LinkId=251610).</span></span>  
  
 <span data-ttu-id="a8a16-145">**使用目前使用者的認證**</span><span class="sxs-lookup"><span data-stu-id="a8a16-145">**Use the credentials of the current user**</span></span>  
 <span data-ttu-id="a8a16-146">選取此選項即可讓 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 物件使用目前使用者的安全性認證來進行非正規 (out-of-line) 繫結、DMX OPENQUERY、本機 Cube 和採礦模型。</span><span class="sxs-lookup"><span data-stu-id="a8a16-146">Select this option to have the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object use the security credentials of the current user for out-of-line bindings, DMX OPENQUERY, local cubes, and mining models.</span></span>  
  
 <span data-ttu-id="a8a16-147">此選項不支援表格式資料庫。</span><span class="sxs-lookup"><span data-stu-id="a8a16-147">This option is not supported for tabular databases.</span></span>  
  
 <span data-ttu-id="a8a16-148">除了使用非正規 (out-of-line) 繫結的本機 Cube 和處理之外，多維度資料庫不支援這個選項。</span><span class="sxs-lookup"><span data-stu-id="a8a16-148">With the exception of local cubes and processing using out-of-line bindings, this option is not supported for multidimensional databases.</span></span>  
  
 <span data-ttu-id="a8a16-149">**預設值**或**繼承**</span><span class="sxs-lookup"><span data-stu-id="a8a16-149">**Default** or **Inherit**</span></span>  
 <span data-ttu-id="a8a16-150">此對話方塊會針對在資料庫層級設定的模擬選項使用 [預設值]\*\*\*\*，而針對在資料來源層級設定的模擬選項使用 [繼承]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a8a16-150">The dialog box uses **Default** for the impersonation options set at the database level and **Inherit** for impersonation options set at the data source level.</span></span>  
  
 <span data-ttu-id="a8a16-151">**資料來源-繼承選項**</span><span class="sxs-lookup"><span data-stu-id="a8a16-151">**Data Sources - Inherit Option**</span></span>  
  
 <span data-ttu-id="a8a16-152">在資料來源層級，[繼承]\*\*\*\* 會指定 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 應該使用父物件的模擬選項。</span><span class="sxs-lookup"><span data-stu-id="a8a16-152">At the data source level, **Inherit** specifies that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] should use the impersonation option of the parent object.</span></span> <span data-ttu-id="a8a16-153">在多維度模型中，父物件是 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="a8a16-153">In a multidimensional model, the parent object is the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="a8a16-154">選擇 [繼承]\*\*\*\* 選項，可讓您集中管理這個資料來源及屬於相同資料庫之其他資料來源的模擬設定。</span><span class="sxs-lookup"><span data-stu-id="a8a16-154">Choosing the **Inherit** option lets you centrally manage the impersonation settings for this and other data sources that are part of the same database.</span></span> <span data-ttu-id="a8a16-155">您必須在資料庫層級選擇特定 Windows 使用者名稱和密碼，這個選項才有意義。</span><span class="sxs-lookup"><span data-stu-id="a8a16-155">For this option to be meaningful, choose a specific Windows user name and password at the database level.</span></span> <span data-ttu-id="a8a16-156">否則，在資料來源上使用 [繼承]\*\*\*\* 搭配在資料庫上使用 [預設值]\*\*\*\*，會相當於使用服務帳戶選項。</span><span class="sxs-lookup"><span data-stu-id="a8a16-156">Otherwise, the combination of **Inherit** on the data source and **Default** on the database are equivalent to using service account option.</span></span>  
  
 <span data-ttu-id="a8a16-157">若要在資料庫層級指定 Windows 使用者名稱和密碼，請執行以下操作：</span><span class="sxs-lookup"><span data-stu-id="a8a16-157">To specify a Windows user name and password at the database level, do the following:</span></span>  
  
1.  <span data-ttu-id="a8a16-158">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中，以滑鼠右鍵按一下資料庫，然後選取 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="a8a16-158">Right-click the database in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="a8a16-159">在 [資料來源模擬資訊]\*\*\*\* 中，指定 Windows 使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="a8a16-159">In **Data Source Impersonation Info**, specify a Windows user name and password.</span></span>  
  
3.  <span data-ttu-id="a8a16-160">以滑鼠右鍵按一下每個資料來源，並檢視其屬性，以確保每個資料來源使用 [繼承]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="a8a16-160">Right-click each data source and view its properties to ensure that each one is using the **Inherit** option.</span></span>  
  
 <span data-ttu-id="a8a16-161">如需資料庫層級之預設設定的詳細資訊，請參閱[設定多維度資料庫屬性 &#40;Analysis Services&#41;](set-multidimensional-database-properties-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="a8a16-161">For more information about default settings at the database level, see [Set Multidimensional Database Properties &#40;Analysis Services&#41;](set-multidimensional-database-properties-analysis-services.md).</span></span>  
  
 <span data-ttu-id="a8a16-162">**資料庫-預設選項**</span><span class="sxs-lookup"><span data-stu-id="a8a16-162">**Databases - Default option**</span></span>  
  
 <span data-ttu-id="a8a16-163">對於表格式資料庫，[**預設值**] 表示使用服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="a8a16-163">For tabular databases, **Default** means use the service account.</span></span>  
  
 <span data-ttu-id="a8a16-164">若為多維度資料庫，[預設值]\*\*\*\* 表示使用服務帳戶和目前使用者進行資料採礦作業。</span><span class="sxs-lookup"><span data-stu-id="a8a16-164">For multidimensional databases, **Default** means use the service account, and current user for data mining operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8a16-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8a16-165">See Also</span></span>  
 <span data-ttu-id="a8a16-166">[建立 &#40;SSAS 多維度&#41;的資料來源](create-a-data-source-ssas-multidimensional.md) </span><span class="sxs-lookup"><span data-stu-id="a8a16-166">[Create a Data Source &#40;SSAS Multidimensional&#41;](create-a-data-source-ssas-multidimensional.md) </span></span>  
 <span data-ttu-id="a8a16-167">[將資料來源屬性設定 &#40;SSAS 多維度&#41;](set-data-source-properties-ssas-multidimensional.md) </span><span class="sxs-lookup"><span data-stu-id="a8a16-167">[Set Data Source Properties &#40;SSAS Multidimensional&#41;](set-data-source-properties-ssas-multidimensional.md) </span></span>  
 [<span data-ttu-id="a8a16-168">&#40;SSAS 表格式&#41;的 DirectQuery 部署案例</span><span class="sxs-lookup"><span data-stu-id="a8a16-168">DirectQuery Deployment Scenarios &#40;SSAS Tabular&#41;</span></span>](../directquery-deployment-scenarios-ssas-tabular.md)  
  
  
