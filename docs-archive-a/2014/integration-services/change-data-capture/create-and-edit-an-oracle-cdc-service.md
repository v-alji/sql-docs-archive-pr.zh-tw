---
title: 建立及編輯 Oracle CDC 服務 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- createSrv
ms.assetid: 10cd612e-d8f1-4af2-97d3-a0c22e1e2326
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3325e272285895e813f01d50a1c312e75472919b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594140"
---
# <a name="create-and-edit-an-oracle-cdc-service"></a><span data-ttu-id="4a3eb-102">建立及編輯 Oracle CDC 服務</span><span class="sxs-lookup"><span data-stu-id="4a3eb-102">Create and Edit an Oracle CDC Service</span></span>
  <span data-ttu-id="4a3eb-103">您會從 CDC 服務組態主控台來建立和編輯新的 Oracle CDC Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-103">You create and edit a new Oracle CDC Windows Service from the CDC Service Configuration Console.</span></span>  
  
 <span data-ttu-id="4a3eb-104">若要建立新的 Oracle CDC Windows 服務，請從左窗格選取 **[本機 CDC 服務]** ，然後按一下 **[動作]** 窗格中的 **[新增服務]** 。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-104">To create a new Oracle CDC Windows service, select **Local CDC Services** from the left pane, then click **New Service** from the **Actions** pane.</span></span> <span data-ttu-id="4a3eb-105">您也可以用滑鼠右鍵按一下 [Local CDC Services (本機 CDC 服務)]  ，然後選取 [新增服務]  。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-105">You can also right-click **Local CDC Services** and select **New Service**.</span></span> <span data-ttu-id="4a3eb-106">隨即開啟 [新增 Oracle CDC Windows 服務] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-106">The New Oracle CDC Windows Service dialog box opens.</span></span>  
  
 <span data-ttu-id="4a3eb-107">**OR**</span><span class="sxs-lookup"><span data-stu-id="4a3eb-107">**OR**</span></span>  
  
 <span data-ttu-id="4a3eb-108">若要編輯 CDC 服務屬性，請選取您要編輯屬性的服務，然後按一下 **[動作]** 窗格中的 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-108">To edit the CDC service properties, select the service that you want to edit the properties for and click **Properties** from the **Actions** pane.</span></span> <span data-ttu-id="4a3eb-109">您也可以用滑鼠右鍵按一下您要使用的服務，然後選取 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-109">You can also right-click the service you are working with and select **Properties**.</span></span> <span data-ttu-id="4a3eb-110">[CDC 服務屬性] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-110">The CDC Service Properties dialog box opens.</span></span>  
  
 <span data-ttu-id="4a3eb-111">在 [新增 Oracle CDC Windows 服務] 對話方塊或 [CDC 服務屬性] 對話方塊中輸入以下資訊。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-111">Enter the following information in the New Oracle CDC Windows Service dialog box or the CDC Service Properties dialog box.</span></span>  
  
 <span data-ttu-id="4a3eb-112">服務名稱</span><span class="sxs-lookup"><span data-stu-id="4a3eb-112">Service Name</span></span>  
 <span data-ttu-id="4a3eb-113">輸入新的 Oracle CDC Windows 服務名稱。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-113">Type the name of the new Oracle CDC Windows Service.</span></span> <span data-ttu-id="4a3eb-114">盡可能不要使用完整名稱。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-114">You should not use long names, if possible.</span></span> <span data-ttu-id="4a3eb-115">不能在服務名稱中使用 / 和 \ 字元。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-115">The characters / and \ cannot be used in the service name.</span></span>  
  
> [!NOTE]  
> <span data-ttu-id="4a3eb-116">當您編輯此服務時，不可使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-116">This option is not available when editing the service.</span></span> <span data-ttu-id="4a3eb-117">您不能變更已經存在的 Windows 服務名稱。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-117">You cannot change the name of a Windows service that already exists.</span></span>  
  
 <span data-ttu-id="4a3eb-118">**說明**</span><span class="sxs-lookup"><span data-stu-id="4a3eb-118">**Description**</span></span>  
 <span data-ttu-id="4a3eb-119">請輸入此服務的描述來加以識別。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-119">Type a description of the service to help identify it.</span></span>  
  
 <span data-ttu-id="4a3eb-120">**服務帳戶**</span><span class="sxs-lookup"><span data-stu-id="4a3eb-120">**Service Account**</span></span>  
 <span data-ttu-id="4a3eb-121">選取下列其中一項，以判斷執行此服務所要使用的帳戶：</span><span class="sxs-lookup"><span data-stu-id="4a3eb-121">Select one of the following to determine under which account to run the service:</span></span>  
  
-   <span data-ttu-id="4a3eb-122">**本機系統帳戶**</span><span class="sxs-lookup"><span data-stu-id="4a3eb-122">**Local System Account**</span></span>  
  
     <span data-ttu-id="4a3eb-123">不建議使用這項，因為它提供此服務的權限太多。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-123">This is not recommended because it gives too many permissions to the service.</span></span>  
  
-   <span data-ttu-id="4a3eb-124">**這個帳戶**</span><span class="sxs-lookup"><span data-stu-id="4a3eb-124">**This Account**</span></span>  
  
     <span data-ttu-id="4a3eb-125">在 Windows Vista 或 Windows Server 2008 上，預設服務帳戶為 NETWORK SERVICE 帳戶。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-125">On Windows Vista or Windows Server 2008, the default service account is the NETWORK SERVICE account.</span></span>  
  
     <span data-ttu-id="4a3eb-126">在 Windows 7、Windows Server 2008 R2 及更新版本上，預設服務帳戶為 NT Service\\<服務名稱>。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-126">On Windows 7, Windows Server 2008 R2 and later, the default service account is NT Service\\<service-name>.</span></span>  
  
     <span data-ttu-id="4a3eb-127">使用這些帳戶讓您不需使用密碼即可工作，因為這些帳戶不需要密碼。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-127">Using these accounts lets you work without using passwords because a password is not necessary for these accounts.</span></span> <span data-ttu-id="4a3eb-128">此外，這些帳戶只會提供 Oracle CDC 服務執行所需的必要權限。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-128">In addition these accounts provide only the necessary permissions required for the Oracle CDC Service to run.</span></span>  
  
     <span data-ttu-id="4a3eb-129">您可以針對此服務帳戶使用本機或網域 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-129">You can use a local or domain Windows account for the service account.</span></span> <span data-ttu-id="4a3eb-130">在此情況下，您必須針對該帳戶輸入 **[密碼]** 。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-130">In this case, you must enter the **Password** for that account.</span></span> <span data-ttu-id="4a3eb-131">此帳戶可適用於本機主機或網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-131">This account can be for the local host or a domain account.</span></span> <span data-ttu-id="4a3eb-132">在 Windows [控制台] 中使用本機服務變更密碼時，請務必更新密碼。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-132">Be sure to update the password when it is changed using Local Services in the Windows Control Panel.</span></span>  
  
 <span data-ttu-id="4a3eb-133">**伺服器名稱**：選取要連接的目標 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體 (例如， **\\\\<電腦名稱>\\<執行個體名稱>** )。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-133">**Server name**: Select the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to connect to (for example, **\\\\<computer_name>\\<instance_name>**).</span></span> <span data-ttu-id="4a3eb-134">預設會顯示上次連接的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-134">The server instance last connected to is displayed by default.</span></span>  
  
 <span data-ttu-id="4a3eb-135">**驗證**</span><span class="sxs-lookup"><span data-stu-id="4a3eb-135">**Authentication**</span></span>  
 <span data-ttu-id="4a3eb-136">選取下列其中一個：</span><span class="sxs-lookup"><span data-stu-id="4a3eb-136">Select one of the following:</span></span>  
  
-   <span data-ttu-id="4a3eb-137">**Windows 驗證**：如果您選取這個選項，Oracle CDC 服務會使用服務帳戶識別連接到目標 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-137">**Windows Authentication**: If you select this option, the Oracle CDC service connects to the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance using the service account identity.</span></span> <span data-ttu-id="4a3eb-138">如果正在另一部電腦上執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，必須搭配網域帳戶使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-138">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance is running on a different computer, Windows Authentication must be used with domain accounts.</span></span>  
  
-   <span data-ttu-id="4a3eb-139">**SQL Server 驗證**：如果您選取這個選項，您必須針對您要使用的 **登入來輸入**使用者名稱**和**密碼[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-139">**SQL Server Authentication**: If you select this option, you must type the **User Name** and **Password** for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login you want to use.</span></span> <span data-ttu-id="4a3eb-140">Oracle CDC 服務會在連接到目標 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體時使用這些認證。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-140">The Oracle CDC service uses these credentials when connecting to the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="4a3eb-141">Oracle CDC 服務所使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入只要求它必須是公用固定伺服器角色的成員，不需要其他權限。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-141">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login used by the Oracle CDC Service only needs to be a member of the public fixed-server role, no other privileges are needed.</span></span> <span data-ttu-id="4a3eb-142">一旦加入新的 Oracle CDC 執行個體之後，該登入會取得關聯 **CDC 資料庫的** db_owner [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 存取權。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-142">Once new Oracle CDC Instances are added, that login will gain **db_owner** access to the associated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC databases.</span></span>  
  
 <span data-ttu-id="4a3eb-143">若要建立 Oracle CDC Windows 服務定義，此程式需要關聯 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中 MSXDBCDC 資料庫的更新存取權。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-143">To create the Oracle CDC Windows Service definition, the program needs update access to the MSXDBCDC database in the associated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="4a3eb-144">當您按一下 **[確定]** 時，隨即出現一個對話方塊，提示使用者輸入具有 MSXDBCDC 資料庫之更新存取權的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-144">When you click **OK**, a dialog box prompts the user to enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login with an update access to the MSXDBCDC database.</span></span>  
  
 <span data-ttu-id="4a3eb-145">如需有關您必須在 [連接到 SQL Server] 對話方塊中輸入之資料的詳細資訊，請參閱＜ [Connection to SQL Server](connection-to-sql-server.md)＞。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-145">For information about the data you must type into the Connect to SQL Server dialog box, see [Connection to SQL Server](connection-to-sql-server.md).</span></span>  
  
 <span data-ttu-id="4a3eb-146">**選項**</span><span class="sxs-lookup"><span data-stu-id="4a3eb-146">**Options**</span></span>  
 <span data-ttu-id="4a3eb-147">按一下箭頭即可檢視要設定的可用選項。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-147">Click the arrow to view available options to be configured.</span></span> <span data-ttu-id="4a3eb-148">您可以選擇保留這些選項的預設值。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-148">You can choose to leave these options with their default value.</span></span> <span data-ttu-id="4a3eb-149">可用的選項如下：</span><span class="sxs-lookup"><span data-stu-id="4a3eb-149">The available options are:</span></span>  
  
-   <span data-ttu-id="4a3eb-150">**連接逾時**：輸入 Oracle CDC 服務在逾時之前等候連接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的時間 (以秒數為單位)。預設值為 **15**。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-150">**Connection Timeout**: Type the time (in seconds) that the CDC Service for Oracle waits for a connection to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before timing out. The default value is **15**.</span></span>  
  
-   <span data-ttu-id="4a3eb-151">**執行逾時**：輸入 Oracle CDC Windows 服務在逾時之前，等候執行命令的時間 (以秒數為單位)。預設值是 **30**。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-151">**Execution Timeout**: Type the time (in seconds) that the Oracle CDC Windows Service waits for a command to execute before timing out. The default value is **30**.</span></span>  
  
-   <span data-ttu-id="4a3eb-152">**加密連接**：針對 Oracle CDC 服務與使用加密連線之目標 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體之間的通訊選取 [加密連線]  。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-152">**Encrypt Connection**: Select **Encrypt Connection** for communication between the Oracle CDC Service and the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance using an encrypted connection.</span></span>  
  
-   <span data-ttu-id="4a3eb-153">**進階**：必要時輸入其他任何連接屬性。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-153">**Advanced**: Type any additional connection properties, if necessary.</span></span>  
  
 <span data-ttu-id="4a3eb-154">**主要密碼**</span><span class="sxs-lookup"><span data-stu-id="4a3eb-154">**Master Password**</span></span>  
 <span data-ttu-id="4a3eb-155">輸入 Oracle CDC Windows 服務為了保護 Oracle 記錄採礦認證所使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-155">Enter a password to be used by the Oracle CDC Windows Service to protect the Oracle log-mining credentials.</span></span>  
  
 <span data-ttu-id="4a3eb-156">在高可用性組態叢集的其他節點上設定相同服務的其他執行個體時，也必須使用相同的主要密碼。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-156">The same master password must also be used when other instances of the same service are configured on other nodes on a cluster in high-availability configuration.</span></span> <span data-ttu-id="4a3eb-157">如果您遺失或修改主要密碼，則儲存在 Oracle CDC 執行個體資料庫中的所有記錄採礦密碼都必須使用 CDC 設計工具主控台重新輸入。</span><span class="sxs-lookup"><span data-stu-id="4a3eb-157">If you lose or modify the master password, all log mining passwords stored in Oracle CDC Instance databases must be re-entered using the CDC Designer console.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a3eb-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a3eb-158">See Also</span></span>  
 [<span data-ttu-id="4a3eb-159">如何建立及編輯 CDC 服務</span><span class="sxs-lookup"><span data-stu-id="4a3eb-159">How to Create and Edit a CDC Service</span></span>](how-to-create-and-edit-a-cdc-service.md)  
  
  
