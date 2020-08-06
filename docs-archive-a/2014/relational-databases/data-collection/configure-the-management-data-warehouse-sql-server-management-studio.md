---
title: 設定管理資料倉儲 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dc.datacollection.wizard_finish.f1
- sql12.swb.dc.datacollection.wizard_maploginuser.f1
- sql12.swb.dc.datacollection.wizard_welcome.f1
- sql12.swb.dc.datacollection.wizard_choosemdw.f1
- sql12.swb.dc.datacollection.wizard_completecfg.f1
- sql12.swb.dc.datacollection.wizard_config.f1
- sql12.swb.dc.datacollection.wizard_createmdw.f1
helpviewer_keywords:
- data warehouse [SQL Server], multiple instances
- data warehouse [SQL Server], configuring
- Configure Management Data Warehouse Wizard
- management data warehouse, configuring
ms.assetid: 23a584f3-c5e1-414c-9afe-73cd7efbda4b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1ef4ddd518343a3076c72ecc41f9b15ddf092dc0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607413"
---
# <a name="configure-the-management-data-warehouse-sql-server-management-studio"></a><span data-ttu-id="72be8-102">設定管理資料倉儲 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="72be8-102">Configure the Management Data Warehouse (SQL Server Management Studio)</span></span>
  <span data-ttu-id="72be8-103">此主題描述如何設定管理資料倉儲，以支援使用資料收集器之一個或多個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的資料儲存體。</span><span class="sxs-lookup"><span data-stu-id="72be8-103">This topic describes how to configure the management data warehouse to support data storage on a single instance or multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are using the data collector.</span></span> <span data-ttu-id="72be8-104">這些執行個體可以在相同伺服器或不同伺服器上。</span><span class="sxs-lookup"><span data-stu-id="72be8-104">These instances can be on the same server or on different servers.</span></span> <span data-ttu-id="72be8-105">此主題也提供 [設定管理資料倉儲精靈](#Wizard) 對話方塊的使用者介面描述。</span><span class="sxs-lookup"><span data-stu-id="72be8-105">This topic also provides descriptions of the user interface for the [Configure Data Management Warehouse Wizard](#Wizard) dialog box.</span></span> <span data-ttu-id="72be8-106">如需設定資料收集器的詳細資訊，請參閱＜ [Configure Properties of a Data Collector](configure-properties-of-a-data-collector.md)＞。</span><span class="sxs-lookup"><span data-stu-id="72be8-106">For information about configuring a data collector, see [Configure Properties of a Data Collector](configure-properties-of-a-data-collector.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="72be8-107">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 設定成使用其中一個系統服務帳戶 (本機系統、網路服務或本機服務) 來執行，而且管理資料倉儲是從資料收集器的另一個執行個體建立，您就必須設定收集組使用 Proxy 將資料上傳到管理資料倉儲。</span><span class="sxs-lookup"><span data-stu-id="72be8-107">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is configured to run using one of the System service accounts (Local System, Network Service, or Local Service), and the management data warehouse is created on a different instance from the data collector, you must configure collection sets to use a proxy for uploading data to the management data warehouse.</span></span>  
  
### <a name="configure-the-management-data-warehouse-on-a-single-instance-or-multiple-instances-of-ssnoversion"></a><span data-ttu-id="72be8-108">在一個或多個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72be8-108">Configure the management data warehouse on a single instance or multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]</span></span>  
  
1.  <span data-ttu-id="72be8-109">確定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 正在執行中。</span><span class="sxs-lookup"><span data-stu-id="72be8-109">Ensure that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is running.</span></span>  
  
2.  <span data-ttu-id="72be8-110">在 [物件總管] 中，展開 **[管理]** 節點。</span><span class="sxs-lookup"><span data-stu-id="72be8-110">In Object Explorer, expand the **Management** node.</span></span>  
  
3.  <span data-ttu-id="72be8-111">以滑鼠右鍵按一下 [資料收集]，展開 [工作]，然後按一下 [設定管理資料倉儲]。</span><span class="sxs-lookup"><span data-stu-id="72be8-111">Right-click **Data Collection**, expand **Tasks**, and then click **Configure Management Data Warehouse**.</span></span>  
  
4.  <span data-ttu-id="72be8-112">使用 [設定管理資料倉儲精靈](#Wizard) 來建立管理資料倉儲、設定登入、啟用資料收集，並啟動 **[系統資料收集組]** 。</span><span class="sxs-lookup"><span data-stu-id="72be8-112">Use the [Configure Management Data Warehouse Wizard](#Wizard) to create a management data warehouse, configure logins, enable data collection, and start the **System Data Collection Sets**.</span></span>  
  
     <span data-ttu-id="72be8-113">若要設定多個執行個體，請繼續執行步驟 5。</span><span class="sxs-lookup"><span data-stu-id="72be8-113">To configure multiple instances, continue with step 5.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="72be8-114">公認的最佳作法是將 Proxy 用於在多個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體 (使用相同的管理資料倉儲) 上安裝資料收集器的部署中。</span><span class="sxs-lookup"><span data-stu-id="72be8-114">It is considered best practice to use proxies in deployments where the data collector is installed on multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are using the same management data warehouse.</span></span>  
  
5.  <span data-ttu-id="72be8-115">在另一個執行個體上開啟 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，然後進行下列任何一項動作：</span><span class="sxs-lookup"><span data-stu-id="72be8-115">Open [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] on another instance and do either of the following:</span></span>  
  
    -   <span data-ttu-id="72be8-116">使用「設定管理資料倉儲精靈」來針對現有的管理資料倉儲設定資料收集。</span><span class="sxs-lookup"><span data-stu-id="72be8-116">Use the Configure Management Data Warehouse wizard to configure data collection for the existing management data warehouse.</span></span>  
  
    -   <span data-ttu-id="72be8-117">以滑鼠右鍵按一下 [資料收集]，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="72be8-117">Right-click **Data Collection**, and then click **Properties**.</span></span> <span data-ttu-id="72be8-118">在 **[一般]** 索引標籤中，指定現有的管理資料倉儲以及它安裝所在的伺服器。</span><span class="sxs-lookup"><span data-stu-id="72be8-118">On the **General** tab, specify the existing management data warehouse and the server that it is installed on.</span></span>  
  
6.  <span data-ttu-id="72be8-119">重複步驟 5，直到使用資料收集器的所有資料庫執行個體都設定為可將資料上傳到共用管理資料倉儲為止。</span><span class="sxs-lookup"><span data-stu-id="72be8-119">Repeat step 5 until all the database instances that use the data collector are configured to upload data to the shared management data warehouse.</span></span>  
  
####  <a name="configure-management-data-warehouse-wizard"></a><a name="Wizard"></a> <span data-ttu-id="72be8-120">設定管理資料倉儲精靈</span><span class="sxs-lookup"><span data-stu-id="72be8-120">Configure Management Data Warehouse Wizard</span></span>  
 <span data-ttu-id="72be8-121">**歡迎頁面**</span><span class="sxs-lookup"><span data-stu-id="72be8-121">**Welcome Page**</span></span>  
  
 <span data-ttu-id="72be8-122">此歡迎頁面是「設定資料收集精靈」的起始頁面。</span><span class="sxs-lookup"><span data-stu-id="72be8-122">The Welcome page is the starting page of the Configure Data Collection Wizard.</span></span> <span data-ttu-id="72be8-123">可以選擇是否顯示此頁面。</span><span class="sxs-lookup"><span data-stu-id="72be8-123">Displaying this page is optional.</span></span>  
  
 <span data-ttu-id="72be8-124">**不要再顯示此開始頁面。**</span><span class="sxs-lookup"><span data-stu-id="72be8-124">**Do not show this starting page again.**</span></span>  
 <span data-ttu-id="72be8-125">選取此選項，可在下一次啟動「設定資料收集精靈」時隱藏這個頁面。</span><span class="sxs-lookup"><span data-stu-id="72be8-125">Select to suppress this page the next time you launch the Configure Data Collection Wizard.</span></span>  
  
 <span data-ttu-id="72be8-126">**設定管理資料倉儲儲存體頁面**</span><span class="sxs-lookup"><span data-stu-id="72be8-126">**Configure Management Data Warehouse Storage Page**</span></span>  
  
 <span data-ttu-id="72be8-127">使用這個頁面可選取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫伺服器和管理資料倉儲。</span><span class="sxs-lookup"><span data-stu-id="72be8-127">Use this page to select a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database server and management data warehouse.</span></span> <span data-ttu-id="72be8-128">管理資料倉儲是一種關聯式資料庫，它將會儲存收集而來的資料。</span><span class="sxs-lookup"><span data-stu-id="72be8-128">The management data warehouse is a relational database that will store collected data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="72be8-129">您必須具備適當的權限等級，才能在伺服器上建立管理資料倉儲。</span><span class="sxs-lookup"><span data-stu-id="72be8-129">You must have the appropriate level of permissions in order to create the management data warehouse on the server.</span></span> <span data-ttu-id="72be8-130">如需詳細資訊，請參閱 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="72be8-130">For more information, see [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).</span></span> <span data-ttu-id="72be8-131">您也必須具備適當的權限等級，才能建立管理資料倉儲角色的登入。</span><span class="sxs-lookup"><span data-stu-id="72be8-131">You also must have the appropriate level of permissions to create logins for management data warehouse roles.</span></span>  
  
 <span data-ttu-id="72be8-132">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="72be8-132">**Server name**</span></span>  
 <span data-ttu-id="72be8-133">指定將主控管理資料倉儲的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="72be8-133">Specifies the name of the server that will host the management data warehouse.</span></span>  
  
 <span data-ttu-id="72be8-134">在設定管理資料倉儲時， **[伺服器名稱]** 永遠是本機伺服器的名稱，而且無法修改。</span><span class="sxs-lookup"><span data-stu-id="72be8-134">When configuring a management data warehouse, **Server name** is always the name of the local server and cannot be modified.</span></span>  
  
 <span data-ttu-id="72be8-135">**資料庫名稱**</span><span class="sxs-lookup"><span data-stu-id="72be8-135">**Database name**</span></span>  
 <span data-ttu-id="72be8-136">指定將會儲存收集之資料的關聯式資料庫。</span><span class="sxs-lookup"><span data-stu-id="72be8-136">Specifies the relational database that will store collected data.</span></span> <span data-ttu-id="72be8-137">使用此清單來選取現有的資料庫，或是使用 **[新增資料庫]** 對話方塊來按一下 **[新增]** ，建立新的資料庫。</span><span class="sxs-lookup"><span data-stu-id="72be8-137">Use the list to select an existing database or click **New** to create a new database using the **New Database** dialog.</span></span>  
  
 <span data-ttu-id="72be8-138">**[新增]** 選項只有在設定資料收集組時才提供。</span><span class="sxs-lookup"><span data-stu-id="72be8-138">The **New** option is available only when configuring a data collection set</span></span>  
  
 <span data-ttu-id="72be8-139">**對應登入及使用者頁面**</span><span class="sxs-lookup"><span data-stu-id="72be8-139">**Map Logins and Users Page**</span></span>  
  
 <span data-ttu-id="72be8-140">使用這個頁面可將登入對應到管理資料倉儲的資料庫使用者角色。</span><span class="sxs-lookup"><span data-stu-id="72be8-140">Use this page to map logins to database user roles for the management data warehouse.</span></span>  
  
 <span data-ttu-id="72be8-141">**已對應到此登入的使用者**</span><span class="sxs-lookup"><span data-stu-id="72be8-141">**Users mapped to this login**</span></span>  
 <span data-ttu-id="72be8-142">顯示伺服器上將主控管理資料倉儲的現有登入。</span><span class="sxs-lookup"><span data-stu-id="72be8-142">Displays the existing logins on the server that will host the management data warehouse.</span></span> <span data-ttu-id="72be8-143">每一個資料列都包含可編輯的 **[對應]** 核取方塊、 **[登入]** 名稱和登入的 **[類型]** 。</span><span class="sxs-lookup"><span data-stu-id="72be8-143">Each row contains an editable **Map** check box, a **Login** name, and a **Type** of login.</span></span>  
  
 <span data-ttu-id="72be8-144">為登入選取 **[對應]** 核取方塊來指定此登入。</span><span class="sxs-lookup"><span data-stu-id="72be8-144">Specify a login by selecting the **Map** checkbox for the login.</span></span>  
  
 <span data-ttu-id="72be8-145">**資料庫角色成員資格對象:**  *\<data warehouse name>*</span><span class="sxs-lookup"><span data-stu-id="72be8-145">**Database role membership for:**  *\<data warehouse name>*</span></span>  
 <span data-ttu-id="72be8-146">選取此登入所對應的管理資料倉儲角色，其方式是按一下下列一或多個選項旁邊的核取方塊：</span><span class="sxs-lookup"><span data-stu-id="72be8-146">Select the management data warehouse role that the login is mapped to by clicking the checkbox by one or more of the following options:</span></span>  
  
-   <span data-ttu-id="72be8-147">**mdw_admin**</span><span class="sxs-lookup"><span data-stu-id="72be8-147">**mdw_admin**</span></span>  
  
-   <span data-ttu-id="72be8-148">**mdw_reader**</span><span class="sxs-lookup"><span data-stu-id="72be8-148">**mdw_reader**</span></span>  
  
-   <span data-ttu-id="72be8-149">**mdw_writer**</span><span class="sxs-lookup"><span data-stu-id="72be8-149">**mdw_writer**</span></span>  
  
 <span data-ttu-id="72be8-150">**新增登入**</span><span class="sxs-lookup"><span data-stu-id="72be8-150">**New Login**</span></span>  
 <span data-ttu-id="72be8-151">開啟 [登入 - 新增] 對話方塊，並為此管理資料倉儲建立新的登入。</span><span class="sxs-lookup"><span data-stu-id="72be8-151">Open the **Login - New** dialog box and create a new login for the management data warehouse.</span></span>  
  
 <span data-ttu-id="72be8-152">**完成精靈頁面**</span><span class="sxs-lookup"><span data-stu-id="72be8-152">**Complete the Wizard Page**</span></span>  
  
 <span data-ttu-id="72be8-153">使用此頁面可驗證及完成資料收集組態。</span><span class="sxs-lookup"><span data-stu-id="72be8-153">Use this page to verify and complete data collection configuration.</span></span> <span data-ttu-id="72be8-154">檢視視窗中所顯示的樹狀目錄會顯示將要套用哪些組態，以及當您按一下 **[完成]** 時將會發生的動作。</span><span class="sxs-lookup"><span data-stu-id="72be8-154">The tree displayed in the viewing window shows what configurations will applied as well as what actions will take place when you click **Finish**.</span></span>  
  
 <span data-ttu-id="72be8-155">**設定資料收集精靈進度頁面**</span><span class="sxs-lookup"><span data-stu-id="72be8-155">**Configure Data Collection Wizard Progress Page**</span></span>  
  
 <span data-ttu-id="72be8-156">使用此頁面可檢視每一個組態步驟的結果。</span><span class="sxs-lookup"><span data-stu-id="72be8-156">Use this page to view the results of each configuration step.</span></span>  
  
 <span data-ttu-id="72be8-157">**詳細資料**</span><span class="sxs-lookup"><span data-stu-id="72be8-157">**Details**</span></span>  
 <span data-ttu-id="72be8-158">將每一個組態步驟顯示為 [詳細資料] 方格中的資料列。</span><span class="sxs-lookup"><span data-stu-id="72be8-158">Displays each configuration step as a row in the **Details** grid.</span></span> <span data-ttu-id="72be8-159">每一個資料列都包含一個可描述此步驟的 **[動作]** 資料行，以及一個指示此步驟為成功或失敗的 **[狀態]** 資料行。</span><span class="sxs-lookup"><span data-stu-id="72be8-159">Each row contains an **Action** column that describes the step, and a **Status** column that indicates the success or failure of the step.</span></span> <span data-ttu-id="72be8-160">如果發生錯誤， **[訊息]** 資料行中會出現訊息。</span><span class="sxs-lookup"><span data-stu-id="72be8-160">If there is an error, a message appears in the **Message** column.</span></span>  
  
 <span data-ttu-id="72be8-161">**停止**</span><span class="sxs-lookup"><span data-stu-id="72be8-161">**Stop**</span></span>  
 <span data-ttu-id="72be8-162">停止精靈的處理。</span><span class="sxs-lookup"><span data-stu-id="72be8-162">Stop wizard processing.</span></span>  
  
 <span data-ttu-id="72be8-163">**Report**</span><span class="sxs-lookup"><span data-stu-id="72be8-163">**Report**</span></span>  
 <span data-ttu-id="72be8-164">檢視資料收集組態的報表。</span><span class="sxs-lookup"><span data-stu-id="72be8-164">View a report of the data collection configuration.</span></span> <span data-ttu-id="72be8-165">以下是提供的報表選項：</span><span class="sxs-lookup"><span data-stu-id="72be8-165">The following report options are provided:</span></span>  
  
-   <span data-ttu-id="72be8-166">檢視報表</span><span class="sxs-lookup"><span data-stu-id="72be8-166">View Report</span></span>  
  
-   <span data-ttu-id="72be8-167">將報表儲存到檔案</span><span class="sxs-lookup"><span data-stu-id="72be8-167">Save Report to File</span></span>  
  
-   <span data-ttu-id="72be8-168">[複製報表到剪貼簿]</span><span class="sxs-lookup"><span data-stu-id="72be8-168">Copy Report to Clipboard</span></span>  
  
-   <span data-ttu-id="72be8-169">以電子郵件傳送報表</span><span class="sxs-lookup"><span data-stu-id="72be8-169">Send Report as E-mail</span></span>  
  
 <span data-ttu-id="72be8-170">**關閉**</span><span class="sxs-lookup"><span data-stu-id="72be8-170">**Close**</span></span>  
 <span data-ttu-id="72be8-171">關閉精靈。</span><span class="sxs-lookup"><span data-stu-id="72be8-171">Close the wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72be8-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72be8-172">See Also</span></span>  
 <span data-ttu-id="72be8-173">[sp_syscollector_enable_collector &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-enable-collector-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="72be8-173">[sp_syscollector_enable_collector &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-enable-collector-transact-sql) </span></span>  
 <span data-ttu-id="72be8-174">[sp_syscollector_disable_collector &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-disable-collector-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="72be8-174">[sp_syscollector_disable_collector &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syscollector-disable-collector-transact-sql) </span></span>  
 <span data-ttu-id="72be8-175">[資料收集](data-collection.md) </span><span class="sxs-lookup"><span data-stu-id="72be8-175">[Data Collection](data-collection.md) </span></span>  
 [<span data-ttu-id="72be8-176">管理資料收集</span><span class="sxs-lookup"><span data-stu-id="72be8-176">Manage Data Collection</span></span>](manage-data-collection.md)  
  
  
