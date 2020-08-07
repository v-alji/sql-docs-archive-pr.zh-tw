---
title: 使用報表管理員建立模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report models [Reporting Services], creating
- Report Manager [Reporting Services], model creation
ms.assetid: 8e5d2bd3-48ec-45f3-afee-6d86797c8f28
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 59ce278a22ec9797b001ca37a0bde576483cf5d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703937"
---
# <a name="create-a-model-using-report-manager"></a><span data-ttu-id="e1a6a-102">使用報表管理員建立模型</span><span class="sxs-lookup"><span data-stu-id="e1a6a-102">Create a Model Using Report Manager</span></span>
  <span data-ttu-id="e1a6a-103">您可以使用報表管理員，從 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Cube、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料庫或 Oracle 資料庫產生模型。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-103">You can generate models from an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cube, a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database, or an Oracle database using Report Manager.</span></span> <span data-ttu-id="e1a6a-104">報表模型是從在報表伺服器上發行的共用資料來源產生的。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-104">Report models are generated from shared data sources that are published on the report server.</span></span> <span data-ttu-id="e1a6a-105">如果您還沒有共用資料來源，則必須建立一個。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-105">If you do not already have a shared data source, you must create one.</span></span>  
  
 <span data-ttu-id="e1a6a-106">您產生的報表模型是完全以共用資料來源的結構描述為基礎。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-106">The report model that you generate is based entirely on the schema of the shared data source.</span></span> <span data-ttu-id="e1a6a-107">您無法選擇模型中要包含資料來源的哪些部分，也無法編輯產生之模型的規則或中繼資料。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-107">You cannot choose which parts of the data source are included in the model, nor can you edit the rules or metadata of a generated model.</span></span> <span data-ttu-id="e1a6a-108">但是，您可以在產生模型後設定模型的屬性，以及定義限制對模型全部或部分之存取的角色指派。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-108">However, you can set properties on the model after it is generated and define role assignments that restrict access to all or part of the model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e1a6a-109">使用報表管理員或2007產生的 Oracle 模型 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[offSPServ](../includes/offspserv-md.md)] [!INCLUDE[SPS2010](../includes/sps2010-md.md)] 會包含屬於架構一部分的資料庫物件，而使用者帳戶是用來連接到 Oracle 資料來源。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-109">An Oracle-based model generated using Report Manager or [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[offSPServ](../includes/offspserv-md.md)] 2007 [!INCLUDE[SPS2010](../includes/sps2010-md.md)] will include database objects that are a part of the schema for the user account used to connect to the Oracle data source.</span></span> <span data-ttu-id="e1a6a-110">使用者帳戶名稱會在資料來源屬性認證中指定。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-110">The user account name is specified in the data source properties credentials.</span></span>  
  
### <a name="to-create-a-new-data-source-for-a-report-model-using-report-manager"></a><span data-ttu-id="e1a6a-111">使用報表管理員建立報表模型的新資料來源</span><span class="sxs-lookup"><span data-stu-id="e1a6a-111">To create a new data source for a report model using Report Manager</span></span>  
  
1.  <span data-ttu-id="e1a6a-112">在網頁瀏覽器的網址列中，輸入報表伺服器的 URL。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-112">In your Web browser, type the URL for your report server in the address bar.</span></span>  
  
2.  <span data-ttu-id="e1a6a-113">按一下 **[新增資料來源]**。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-113">Click **New Data Source**.</span></span>  
  
3.  <span data-ttu-id="e1a6a-114">在 **[名稱]** 方塊中，輸入資料來源的名稱。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-114">In the **Name** box, enter a name for the data source.</span></span>  
  
4.  <span data-ttu-id="e1a6a-115">選擇性，在 **[描述]** 文字方塊中輸入模式的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-115">Optionally, enter a brief description of the mode in the **Description** text box.</span></span>  
  
5.  <span data-ttu-id="e1a6a-116">確認已經選取 **[啟用此資料來源]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-116">Verify that the **Enable this data source** check box is selected.</span></span>  
  
6.  <span data-ttu-id="e1a6a-117">在 **[連接類型]** 清單中，選取您要連接的資料來源類型。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-117">In the **Connection type** list, select the data source type to which you want to connect.</span></span> <span data-ttu-id="e1a6a-118">連接類型必須是下列任一個： **Oracle**、 **Microsoft SQL Server** 或 **Microsoft SQL Server Analysis Services**。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-118">The connection type must be one of the following: **Oracle**, **Microsoft SQL Server** or **Microsoft SQL Server Analysis Services**.</span></span>  
  
7.  <span data-ttu-id="e1a6a-119">在 **[連接字串]** 方塊中，輸入指向資料庫的連接字串。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-119">In the **Connection string** box, enter the connection string that points to the database.</span></span>  
  
8.  <span data-ttu-id="e1a6a-120">選取報表產生器使用者需要用來連接到資料庫的連接方法。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-120">Select the connection method that Report Builder users will need to use to connect to the database.</span></span>  
  
    -   <span data-ttu-id="e1a6a-121">Windows 驗證：如果您要作業系統驗證 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 使用者，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-121">Windows Authentication: Select this option when you want the operating system to authenticate [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] users.</span></span> <span data-ttu-id="e1a6a-122">此選項允許 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 使用 Windows 安全性功能 (例如密碼加密)，來驗證使用者。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-122">This option allows [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to use Windows security features, such as password encryption, to authenticate users.</span></span> <span data-ttu-id="e1a6a-123">強烈建議您選取此選項。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-123">It is strongly recommended that you select this option.</span></span>  
  
    -   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]<span data-ttu-id="e1a6a-124">驗證：當您想要讓使用者使用您建立的登入帳戶時，請選取此選項 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-124">Authentication: Select this option when you want users to use a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login account that you created.</span></span> <span data-ttu-id="e1a6a-125">使用者必須提供有效的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 登入名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-125">Users must supply a valid [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] login name and password.</span></span>  
  
        > [!CAUTION]  
        >  <span data-ttu-id="e1a6a-126">可能的話，請使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-126">Whenever possible, use Windows Authentication.</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-create-a-report-model-using-report-manager"></a><span data-ttu-id="e1a6a-127">使用報表管理員建立報表模型</span><span class="sxs-lookup"><span data-stu-id="e1a6a-127">To create a report model using Report Manager</span></span>  
  
1.  <span data-ttu-id="e1a6a-128">在報表管理員中，選取您要用於模型的資料來源。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-128">In Report Manager, select the data source that you want to use for your model.</span></span>  
  
     <span data-ttu-id="e1a6a-129">就會出現 [屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-129">The Properties page is displayed.</span></span>  
  
2.  <span data-ttu-id="e1a6a-130">確認您要使用為資料來源指定的選項。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-130">Verify that you want to use the options specified for the data source.</span></span>  
  
3.  <span data-ttu-id="e1a6a-131">按一下 **[產生模型]**。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-131">Click **Generate Model**.</span></span>  
  
     <span data-ttu-id="e1a6a-132">就會顯示資料來源的 [一般] 頁面。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-132">The General page is displayed for the data source.</span></span>  
  
4.  <span data-ttu-id="e1a6a-133">在 **[名稱]** 方塊中，輸入報表模型的名稱。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-133">In the **Name** box, enter a name for the report model.</span></span>  
  
5.  <span data-ttu-id="e1a6a-134">在 **[描述]** 方塊中，輸入模型的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-134">In the **Description** box, enter a brief description of the model.</span></span>  
  
6.  <span data-ttu-id="e1a6a-135">若要指定儲存報表模型的新位置，請按一下 **[變更位置]**。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-135">To specify a new location to save the report model to, click **Change Location**.</span></span>  
  
     <span data-ttu-id="e1a6a-136">依預設，報表模型是儲存在報表管理員的主資料夾。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-136">By default, the report model is saved to Report Manager Home.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     <span data-ttu-id="e1a6a-137">接著會建立報表模型，並將模型儲存到您指定的位置。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-137">The report model is created and saved to the location that you specified.</span></span> <span data-ttu-id="e1a6a-138">您可以使用「報表管理員」來為這個模型指派權限。</span><span class="sxs-lookup"><span data-stu-id="e1a6a-138">You can assign permissions to this model by using Report Manager.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1a6a-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1a6a-139">See Also</span></span>  
 <span data-ttu-id="e1a6a-140">[在原生模式報表伺服器上授與權限](security/granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="e1a6a-140">[Granting Permissions on a Native Mode Report Server](security/granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 <span data-ttu-id="e1a6a-141">[Reporting Services 中的資料連線、資料來源及連接字串](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="e1a6a-141">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="e1a6a-142">新增資料來源頁面 &#40;報表管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="e1a6a-142">New Data Source Page &#40;Report Manager&#41;</span></span>](../../2014/reporting-services/new-data-source-page-report-manager.md)  
  
  
