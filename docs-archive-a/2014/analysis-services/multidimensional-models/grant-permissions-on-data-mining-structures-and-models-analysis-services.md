---
title: 授與資料採礦結構和模型的許可權 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.roledesignerdialog.miningmodels.f1
helpviewer_keywords:
- data mining [Analysis Services], security
- permissions [Analysis Services], mining models
- mining models [Analysis Services], security
- mining structures [Analysis Services], security
- permissions [Analysis Services], mining structures
- user access rights [Analysis Services], mining structures
- user access rights [Analysis Services], mining models
ms.assetid: a0008004-e2b7-47db-acad-5fe7e12b130f
author: minewiskan
ms.author: owend
ms.openlocfilehash: d0db849551bdb38615f280b123c98f0e9d3053d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703341"
---
# <a name="grant-permissions-on-data-mining-structures-and-models-analysis-services"></a><span data-ttu-id="c01d6-102">授與資料採礦結構和模型的權限 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="c01d6-102">Grant permissions on data mining structures and models (Analysis Services)</span></span>
  <span data-ttu-id="c01d6-103">根據預設，只有 Analysis Services 伺服器管理員擁有檢視資料庫中資料採礦結構或採礦模型的權限。</span><span class="sxs-lookup"><span data-stu-id="c01d6-103">By default, only an Analysis Services server administrator has permissions to view data mining structures or mining models in the database.</span></span> <span data-ttu-id="c01d6-104">請依照下列指示，授與權限給非管理員的使用者。</span><span class="sxs-lookup"><span data-stu-id="c01d6-104">Follow the instructions below to grant permissions to non-administrator users.</span></span>  
  
## <a name="set-permissions-to-access-a-mining-structure"></a><span data-ttu-id="c01d6-105">設定權限以存取採礦結構</span><span class="sxs-lookup"><span data-stu-id="c01d6-105">Set permissions to access a mining structure</span></span>  
  
1.  <span data-ttu-id="c01d6-106">在 SSMS 中，連線到 Analysis Services。</span><span class="sxs-lookup"><span data-stu-id="c01d6-106">In SSMS, connect to Analysis Services.</span></span> <span data-ttu-id="c01d6-107">如果您需要這些步驟的說明，請參閱[從用戶端應用程式連接 &#40;Analysis Services&#41;](../instances/connect-from-client-applications-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="c01d6-107">See [Connect from client applications &#40;Analysis Services&#41;](../instances/connect-from-client-applications-analysis-services.md) if you need help with the steps.</span></span>  
  
2.  <span data-ttu-id="c01d6-108">在物件總管中，開啟 [資料庫]\*\*\*\* 資料夾，然後選取資料庫。</span><span class="sxs-lookup"><span data-stu-id="c01d6-108">Open the **Databases** folder, and select a database in Object Explorer.</span></span>  
  
3.  <span data-ttu-id="c01d6-109">以滑鼠右鍵按一下 [角色]\*\*\*\*，然後選擇 [新增角色]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c01d6-109">Right-click **Roles** and choose **New Role**.</span></span>  
  
4.  <span data-ttu-id="c01d6-110">在 [一般] 窗格中，輸入名稱，並選擇性地輸入描述。</span><span class="sxs-lookup"><span data-stu-id="c01d6-110">In the General page, enter a name, and optionally, a description.</span></span> <span data-ttu-id="c01d6-111">這個頁面也包含數個資料庫權限，例如，[完整控制權]、[處理資料庫] 及 [讀取定義]。</span><span class="sxs-lookup"><span data-stu-id="c01d6-111">The page also contains several database permissions, such as Full Control, Process Database, and Read Definition.</span></span> <span data-ttu-id="c01d6-112">存取資料採礦時不需要這些權限的任何一個。</span><span class="sxs-lookup"><span data-stu-id="c01d6-112">None of these permissions are needed for data mining access.</span></span> <span data-ttu-id="c01d6-113">如需資料庫權限的詳細資訊，請參閱[授與資料庫權限 &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="c01d6-113">See [Grant database permissions &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md) for more information about database permissions.</span></span>  
  
5.  <span data-ttu-id="c01d6-114">在 [採礦結構]\*\*\*\* 窗格中，為每個資料採礦結構選取 [讀取]\*\*\*\* 或 [讀取/寫入]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c01d6-114">In the **Mining Structure** pane, select **Read** or **Read/Write**  for each data mining structure.</span></span>  
  
6.  <span data-ttu-id="c01d6-115">在 [成員資格]\*\*\*\* 窗格中，輸入使用這個角色連線到 Analysis Services 的 Windows 使用者和群組帳戶。</span><span class="sxs-lookup"><span data-stu-id="c01d6-115">In the **Membership** pane, enter the Windows user and group accounts that connect to Analysis Services using this role.</span></span>  
  
7.  <span data-ttu-id="c01d6-116">按一下 [確定]\*\*\*\*，完成角色的建立。</span><span class="sxs-lookup"><span data-stu-id="c01d6-116">Click **OK** to finish creating the role.</span></span>  
  
## <a name="set-permissions-to-access-a-mining-model"></a><span data-ttu-id="c01d6-117">設定權限以存取採礦模型</span><span class="sxs-lookup"><span data-stu-id="c01d6-117">Set permissions to access a mining model</span></span>  
 <span data-ttu-id="c01d6-118">對於資料採礦模型而言，角色可以擁有 [讀取]\*\*\*\* 或 [讀取/寫入]\*\*\*\* 權限，以及 [鑽研]\*\*\*\* 和 [讀取定義]\*\*\*\* 權限，以允許檢視和瀏覽基礎資料。</span><span class="sxs-lookup"><span data-stu-id="c01d6-118">For a data mining model, a role can have either **Read** or **Read/Write** permissions, as well as **Drillthrough** and **Read Definition** permissions that allow viewing and browsing the underlying data.</span></span>  
  
 <span data-ttu-id="c01d6-119">**注意** ：如果您在採礦結構和採礦模型上都啟用鑽研，則任何使用者只要是對於採礦模型和採礦結構具有鑽研權限的角色成員，也都可以檢視採礦結構中的資料行，即使這些資料行未包含在採礦模型中。</span><span class="sxs-lookup"><span data-stu-id="c01d6-119">**Note** If you enable drillthrough on both the mining structure and the mining model, any user who is a member of a role that has drillthrough permissions on the mining model and the mining structure can also view columns in the mining structure, even if those columns are not included in the mining model.</span></span> <span data-ttu-id="c01d6-120">因此，若要保護機密資訊，您應該設定資料來源檢視來遮罩個人資訊，並只有在必要時才允許採礦結構的鑽研存取。</span><span class="sxs-lookup"><span data-stu-id="c01d6-120">Therefore, to protect sensitive information, you should set up the data source view to mask personal information, and allow drillthrough access on the mining structure only when necessary.</span></span>  
  
 <span data-ttu-id="c01d6-121">若要授與資料庫角色讀取或讀取/寫入權限，使用者必須是 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 伺服器角色的成員，或者擁有完整控制權 (管理員) 權限之 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="c01d6-121">To grant read or read/write permissions to a database role, a user must be a member of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server role or a member of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database role that has Full Control (Administrator) permissions.</span></span>  
  
1.  <span data-ttu-id="c01d6-122">在中 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，連接到的實例 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、在物件總管中展開適當資料庫的 [**角色**]，然後按一下資料庫角色 (或建立新的資料庫角色) 。</span><span class="sxs-lookup"><span data-stu-id="c01d6-122">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], expand **Roles** for the appropriate database in Object Explorer, and then click a database role (or create a new database role).</span></span>  
  
2.  <span data-ttu-id="c01d6-123">在 [採礦結構]\*\*\*\* 窗格的 [採礦模型]\*\*\*\* 清單中尋找採礦模型，然後針對該採礦模型選取 [讀取]\*\*\*\*、[讀取/寫入]\*\*\*\*、[鑽研]\*\*\*\* 或 [瀏覽]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c01d6-123">In the **Mining Structure** pane, locate the mining model in the **Mining Models** list, and then select **Read**, **Read/Write**, **Drill Through**, or **Browse** for that mining model.</span></span>  
  
3.  <span data-ttu-id="c01d6-124">在 [成員資格]\*\*\*\* 窗格中，輸入使用這個角色連線到 Analysis Services 的 Windows 使用者和群組帳戶。</span><span class="sxs-lookup"><span data-stu-id="c01d6-124">In the **Membership** pane, enter the Windows user and group accounts that connect to Analysis Services using this role.</span></span>  
  
4.  <span data-ttu-id="c01d6-125">按一下 [確定]\*\*\*\*，完成角色的建立。</span><span class="sxs-lookup"><span data-stu-id="c01d6-125">Click **OK** to finish creating the role.</span></span>  
  
 <span data-ttu-id="c01d6-126">若要在使用資料採礦延伸模組 (DMX) OPENQUERY 子句的鑽研查詢中使用資料來源，資料庫角色還需要對適當的資料來源物件具有讀取/寫入權限。</span><span class="sxs-lookup"><span data-stu-id="c01d6-126">To use a data source in a drillthrough query that uses the Data Mining Extensions (DMX) OPENQUERY clause, the database role also needs read/write permission on the appropriate data source object.</span></span> <span data-ttu-id="c01d6-127">如需詳細資訊，請參閱[授與資料來源物件的權限 &#40;Analysis Services&#41;](grant-permissions-on-a-data-source-object-analysis-services.md) 和 [OPENQUERY &#40;DMX&#41;](/sql/dmx/source-data-query-openquery)。</span><span class="sxs-lookup"><span data-stu-id="c01d6-127">For more information, see [Grant permissions on a data source object &#40;Analysis Services&#41;](grant-permissions-on-a-data-source-object-analysis-services.md) and [OPENQUERY &#40;DMX&#41;](/sql/dmx/source-data-query-openquery).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c01d6-128">依預設，使用 OPENROWSET 來提交 DMX 查詢的功能已停用。</span><span class="sxs-lookup"><span data-stu-id="c01d6-128">By default, the submission of DMX queries by using OPENROWSET is disabled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c01d6-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c01d6-129">See Also</span></span>  
 <span data-ttu-id="c01d6-130">[授與伺服器管理員許可權 &#40;Analysis Services&#41;](../instances/grant-server-admin-rights-to-an-analysis-services-instance.md) </span><span class="sxs-lookup"><span data-stu-id="c01d6-130">[Grant Server Administrator Permissions &#40;Analysis Services&#41;](../instances/grant-server-admin-rights-to-an-analysis-services-instance.md) </span></span>  
 <span data-ttu-id="c01d6-131">[授與 cube 或模型許可權 &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="c01d6-131">[Grant cube or model permissions &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md) </span></span>  
 <span data-ttu-id="c01d6-132">[將維度資料的自訂存取權授與 &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="c01d6-132">[Grant custom access to dimension data &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md) </span></span>  
 [<span data-ttu-id="c01d6-133">授與資料格資料的自訂存取權 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="c01d6-133">Grant custom access to cell data &#40;Analysis Services&#41;</span></span>](grant-custom-access-to-cell-data-analysis-services.md)  
  
  
