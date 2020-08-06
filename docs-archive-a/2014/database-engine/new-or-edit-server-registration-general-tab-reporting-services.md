---
title: 新增或編輯服務器註冊 (一般] 索引標籤)  (Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.registerserver.general.reportserver.f1
ms.assetid: 5f899a8e-52ef-46b5-b7a9-f200ccd9f724
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 195756498dcefe4686d4b06e758dba9919c0b304
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599663"
---
# <a name="new-or-edit-server-registration-general-tab-reporting-services"></a><span data-ttu-id="6c301-102">新增或編輯伺服器註冊 (一般索引標籤) (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="6c301-102">New or Edit Server Registration (General Tab) (Reporting Services)</span></span>
  <span data-ttu-id="6c301-103">當您註冊 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 的執行個體時，請使用此索引標籤來指定選項。</span><span class="sxs-lookup"><span data-stu-id="6c301-103">Use this tab to specify options when registering an instance of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="6c301-104">若要存取此頁面，請在 [已註冊的伺服器]\*\*\*\* 工具列按一下 [Reporting Services]\*\*\*\*，以滑鼠右鍵按一下任何已註冊的伺服器群組 (例如 [Reporting Services]\*\*\*\*)，指向 [新增]\*\*\*\*，然後按一下 [伺服器註冊]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6c301-104">To access this page, in Registered Servers, click **Reporting Services** on the **Registered Servers** toolbar, right-click any registered servers group such as **Reporting Services**, point to **New**, and then click **Server Registration**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6c301-105">選項。</span><span class="sxs-lookup"><span data-stu-id="6c301-105">Options</span></span>  
 <span data-ttu-id="6c301-106">**伺服器類型**</span><span class="sxs-lookup"><span data-stu-id="6c301-106">**Server type**</span></span>  
 <span data-ttu-id="6c301-107">從 [已註冊的伺服器] 註冊伺服器時，[**伺服器類型**] 方塊是唯讀的，而且會與 [**已註冊的伺服器**] 窗格中顯示的伺服器類型相符。</span><span class="sxs-lookup"><span data-stu-id="6c301-107">When a server is registered from Registered Servers, the **Server type** box is read-only, and it matches the type of server displayed in the **Registered Servers** pane.</span></span> <span data-ttu-id="6c301-108">若要註冊一個不同類型的伺服器，在開始註冊新伺服器之前，請在 **[已註冊的伺服器]** 工具列上按一下您想要的伺服器。</span><span class="sxs-lookup"><span data-stu-id="6c301-108">To register a different type of server, click the server you want on the **Registered Servers** toolbar before starting to register a new server.</span></span>  
  
 <span data-ttu-id="6c301-109">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="6c301-109">**Server name**</span></span>  
 <span data-ttu-id="6c301-110">指定要連接到的報表伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="6c301-110">Specify the report server instance to connect to.</span></span> <span data-ttu-id="6c301-111">在 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]中，您可以透過執行個體名稱來存取報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="6c301-111">In [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], you can access a report server through its instance name.</span></span> <span data-ttu-id="6c301-112">您安裝的每一個 SQL Server 執行個體可以有一個報表伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="6c301-112">You can have one report server instance for each SQL Server instance that you install.</span></span> <span data-ttu-id="6c301-113">如果您使用預設執行個體，請鍵入 SQL Server 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="6c301-113">If you are using the default instance, type the name of the SQL Server instance.</span></span> <span data-ttu-id="6c301-114">如果您使用具名執行個體，請以 MSSQL$InstanceName 格式指定要連接到報表伺服器的具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="6c301-114">If you are using a named instance, specify the named instance to connect to the report server in the format MSSQL$InstanceName.</span></span>  
  
 <span data-ttu-id="6c301-115">**驗證**</span><span class="sxs-lookup"><span data-stu-id="6c301-115">**Authentication**</span></span>  
 <span data-ttu-id="6c301-116">對報表伺服器的驗證是透過 Internet Information Services (IIS) 來完成。</span><span class="sxs-lookup"><span data-stu-id="6c301-116">Authentication to a report server is made through Internet Information Services (IIS).</span></span> <span data-ttu-id="6c301-117">連接到 Reporting Services 時，請選取下列其中一種驗證模式：</span><span class="sxs-lookup"><span data-stu-id="6c301-117">Select from one of the following authentication modes when connecting to Reporting Services:</span></span>  
  
 <span data-ttu-id="6c301-118">**Windows 驗證模式 (Windows 驗證)**</span><span class="sxs-lookup"><span data-stu-id="6c301-118">**Windows Authentication Mode (Windows Authentication)**</span></span>  
 <span data-ttu-id="6c301-119">使用您的 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 認證連接到報表伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="6c301-119">Connect to the report server instance using your [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows credentials.</span></span>  
  
 <span data-ttu-id="6c301-120">**基本驗證**</span><span class="sxs-lookup"><span data-stu-id="6c301-120">**Basic Authentication**</span></span>  
 <span data-ttu-id="6c301-121">如果您的 Reporting Services 安裝設定為使用基本驗證，請使用 [基本驗證]\*\*\*\* 來連接。</span><span class="sxs-lookup"><span data-stu-id="6c301-121">Connect using **Basic Authentication** if your Reporting Services installation is configured to use Basic Authentication.</span></span>  
  
 <span data-ttu-id="6c301-122">**表單驗證**</span><span class="sxs-lookup"><span data-stu-id="6c301-122">**Forms Authentication**</span></span>  
 <span data-ttu-id="6c301-123">如果您的 Reporting Services 安裝設定為使用自訂驗證延伸模組，請使用 [表單驗證]\*\*\*\* 來連接。</span><span class="sxs-lookup"><span data-stu-id="6c301-123">Connect using **Forms Authentication** if your Reporting Services installation is configured to use a custom authentication extension.</span></span>  
  
 <span data-ttu-id="6c301-124">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="6c301-124">**User Name**</span></span>  
 <span data-ttu-id="6c301-125">請輸入連接將使用的登入名稱。</span><span class="sxs-lookup"><span data-stu-id="6c301-125">Enter the login name to use for the connection.</span></span> <span data-ttu-id="6c301-126">唯有選取 **[基本驗證]** 或 **[表單驗證]** 時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="6c301-126">This option is only available if you have selected **Basic** or **Forms Authentication**.</span></span>  
  
 <span data-ttu-id="6c301-127">**密碼**</span><span class="sxs-lookup"><span data-stu-id="6c301-127">**Password**</span></span>  
 <span data-ttu-id="6c301-128">請輸入使用者名稱的密碼。</span><span class="sxs-lookup"><span data-stu-id="6c301-128">Enter the password for the user name.</span></span> <span data-ttu-id="6c301-129">唯有選取 **[基本驗證]** 或 **[表單驗證]** 時，才能編輯此選項。</span><span class="sxs-lookup"><span data-stu-id="6c301-129">This option is only editable if you have selected **Basic** or **Forms Authentication**.</span></span>  
  
 <span data-ttu-id="6c301-130">**記住密碼**</span><span class="sxs-lookup"><span data-stu-id="6c301-130">**Remember password**</span></span>  
 <span data-ttu-id="6c301-131">請儲存您輸入的密碼。</span><span class="sxs-lookup"><span data-stu-id="6c301-131">Store the password you have entered.</span></span> <span data-ttu-id="6c301-132">唯有已按一下 **[基本驗證]** 或 **[表單驗證]** 時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="6c301-132">This option is only available if you have clicked **Basic** or **Forms Authentication**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6c301-133"> 如果您已儲存密碼但不想再儲存，請清除此核取方塊，然後按一下 **[儲存]**。</span><span class="sxs-lookup"><span data-stu-id="6c301-133">If you have stored the password and want to stop storing it, clear this check box and then click **Save**.</span></span>  
  
 <span data-ttu-id="6c301-134">**已註冊的伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="6c301-134">**Registered server name**</span></span>  
 <span data-ttu-id="6c301-135">您要在 [已註冊的伺服器] 上顯示的名稱。</span><span class="sxs-lookup"><span data-stu-id="6c301-135">The name you want to appear in Registered Servers.</span></span> <span data-ttu-id="6c301-136">此名稱不需與 **[伺服器名稱]** 方塊中的名稱相符。</span><span class="sxs-lookup"><span data-stu-id="6c301-136">This name does not have to match the name in the **Server name** box.</span></span>  
  
 <span data-ttu-id="6c301-137">**已註冊的伺服器描述**</span><span class="sxs-lookup"><span data-stu-id="6c301-137">**Registered server description**</span></span>  
 <span data-ttu-id="6c301-138">輸入伺服器的選擇性描述。</span><span class="sxs-lookup"><span data-stu-id="6c301-138">Enter an optional description of the server.</span></span>  
  
 <span data-ttu-id="6c301-139">**Test**</span><span class="sxs-lookup"><span data-stu-id="6c301-139">**Test**</span></span>  
 <span data-ttu-id="6c301-140">按一下以測試與 [伺服器名稱]\*\*\*\* 中選取之伺服器的連接。</span><span class="sxs-lookup"><span data-stu-id="6c301-140">Click to test the connection to the server selected in **Server name**.</span></span>  
  
 <span data-ttu-id="6c301-141">**儲存**</span><span class="sxs-lookup"><span data-stu-id="6c301-141">**Save**</span></span>  
 <span data-ttu-id="6c301-142">按一下即可儲存已註冊的伺服器設定。</span><span class="sxs-lookup"><span data-stu-id="6c301-142">Click to save the registered server settings.</span></span>  
  
  
