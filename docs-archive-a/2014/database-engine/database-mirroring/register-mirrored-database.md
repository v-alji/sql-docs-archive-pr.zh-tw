---
title: 註冊鏡像資料庫 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.dbmmonitor.registermirroreddb.f1
ms.assetid: 6acd02b9-2311-49b0-a5f8-3852beecb4b0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 24732f82c971959ed202358613ef98c5ccc714d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701815"
---
# <a name="register-mirrored-database"></a><span data-ttu-id="bb799-102">註冊鏡像資料庫</span><span class="sxs-lookup"><span data-stu-id="bb799-102">Register Mirrored Database</span></span>
  <span data-ttu-id="bb799-103">使用這個對話方塊可在特定的伺服器執行個體上註冊一或多個鏡像資料庫，只要將資料庫加入至「資料庫鏡像監視器」即可。</span><span class="sxs-lookup"><span data-stu-id="bb799-103">Use this dialog box to register one or more mirrored databases on a given server instance by adding the database or databases to the Database Mirroring Monitor.</span></span> <span data-ttu-id="bb799-104">加入資料庫之後，「資料庫鏡像監視器」就會在本機快取有關資料庫、其夥伴以及如何連接到夥伴的資訊。</span><span class="sxs-lookup"><span data-stu-id="bb799-104">When a database is added, Database Mirroring Monitor locally caches information about the database, its partners, and how to connect to the partners.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bb799-105">如果您在主體伺服器執行個體上是 **系統管理員** 固定伺服器角色的成員，但是在鏡像伺服器執行個體上不是該角色的成員，則只能在主體伺服器執行個體上查看狀態。</span><span class="sxs-lookup"><span data-stu-id="bb799-105">If you are a member of the **sysadmin** fixed server role on the principal server instance but not on the mirror server instance, you can only see status on the principal server instance.</span></span>  
  
 <span data-ttu-id="bb799-106">**若要使用 SQL Server Management Studio 監視資料庫鏡像**</span><span class="sxs-lookup"><span data-stu-id="bb799-106">**To use SQL Server Management Studio to monitor database mirroring**</span></span>  
  
-   [<span data-ttu-id="bb799-107">啟動資料庫鏡像監視器 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="bb799-107">Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;</span></span>](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
## <a name="options"></a><span data-ttu-id="bb799-108">選項。</span><span class="sxs-lookup"><span data-stu-id="bb799-108">Options</span></span>  
 <span data-ttu-id="bb799-109">**伺服器執行個體**</span><span class="sxs-lookup"><span data-stu-id="bb799-109">**Server instance**</span></span>  
 <span data-ttu-id="bb799-110">從包含「資料庫鏡像監視器」已經儲存連接之伺服器執行個體的清單中選取一個伺服器執行個體，或是按一下 [連接] 。</span><span class="sxs-lookup"><span data-stu-id="bb799-110">Select a server instance from the list, which contains server instances to which Database Mirroring Monitor already has a connection stored, or click **Connect**.</span></span> <span data-ttu-id="bb799-111">若要為清單中所列的伺服器執行個體指定新的認證，請按一下 [連接]  並使用新的認證來連接。</span><span class="sxs-lookup"><span data-stu-id="bb799-111">To specify new credentials for a listed server instance, click **Connect** and connect using the new credentials.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bb799-112">若要在多個伺服器執行個體上註冊資料庫，當您檢查完其中一個伺服器執行個體所需的資料庫之後，請按一下 [套用] ，然後選取另一個伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="bb799-112">To register databases on multiple server instances, after you finish checking the desired databases for one server instance, click **Apply**, and then select another server instance.</span></span>  
  
 <span data-ttu-id="bb799-113">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="bb799-113">**Connect**</span></span>  
 <span data-ttu-id="bb799-114">若要為伺服器執行個體指定新的認證，請按一下 [連接]  並使用新的認證來連接。</span><span class="sxs-lookup"><span data-stu-id="bb799-114">To specify new credentials for the server instance, click **Connect** and connect using the new credentials.</span></span> <span data-ttu-id="bb799-115">在連接到伺服器執行個體時，「資料庫鏡像監視器」會顯示 [正在等候資料] 。</span><span class="sxs-lookup"><span data-stu-id="bb799-115">While connecting to a server instance, Database Mirroring Monitor displays **Waiting for data**.</span></span>  
  
 <span data-ttu-id="bb799-116">**鏡像資料庫**</span><span class="sxs-lookup"><span data-stu-id="bb799-116">**Mirrored databases**</span></span>  
 <span data-ttu-id="bb799-117">[鏡像資料庫]  方格會列出伺服器執行個體上的鏡像資料庫。</span><span class="sxs-lookup"><span data-stu-id="bb799-117">The **Mirrored databases** grid lists the mirrored databases on the server instance.</span></span>  
  
 <span data-ttu-id="bb799-118">方格包含下列資料行：</span><span class="sxs-lookup"><span data-stu-id="bb799-118">The grid contains the following columns:</span></span>  
  
|<span data-ttu-id="bb799-119">資料行名稱</span><span class="sxs-lookup"><span data-stu-id="bb799-119">Column name</span></span>|<span data-ttu-id="bb799-120">描述</span><span class="sxs-lookup"><span data-stu-id="bb799-120">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="bb799-121">**註冊**</span><span class="sxs-lookup"><span data-stu-id="bb799-121">**Register**</span></span>|<span data-ttu-id="bb799-122">檢查您要註冊的每一個資料庫。</span><span class="sxs-lookup"><span data-stu-id="bb799-122">Check each of the databases that you want to register.</span></span> <span data-ttu-id="bb799-123">如果資料庫目前受到監視，則其核取方塊為已選取和停用狀態。</span><span class="sxs-lookup"><span data-stu-id="bb799-123">If a database is currently monitored, its check box is checked and is disabled.</span></span><br /><br /> <span data-ttu-id="bb799-124">注意:若要取消註冊資料庫，請關閉 [註冊鏡像資料庫] 對話方塊，在導覽樹狀目錄中選取資料庫，然後選取 [動作] 功能表中的 [取消註冊]。</span><span class="sxs-lookup"><span data-stu-id="bb799-124">Note: To unregister a database, close the **Registered Mirrored Database** dialog box, select the database in the navigation tree, and select **Unregister** from the **Action** menu.</span></span>|  
|<span data-ttu-id="bb799-125">**Database**</span><span class="sxs-lookup"><span data-stu-id="bb799-125">**Database**</span></span>|<span data-ttu-id="bb799-126">選取之伺服器執行個體上的鏡像資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="bb799-126">The name of a mirrored database on the selected server instance.</span></span>|  
|<span data-ttu-id="bb799-127">**目前的角色**</span><span class="sxs-lookup"><span data-stu-id="bb799-127">**Current Role**</span></span>|<span data-ttu-id="bb799-128">資料庫目前在選取之伺服器執行個體上的鏡像角色，可為 [主體] 或 [鏡像]。</span><span class="sxs-lookup"><span data-stu-id="bb799-128">The current mirroring role of the database, either Principal or Mirror, on the selected server instance.</span></span>|  
|<span data-ttu-id="bb799-129">**夥伴 (連接為)**</span><span class="sxs-lookup"><span data-stu-id="bb799-129">**Partner (Connect as)**</span></span>|<span data-ttu-id="bb799-130">資料庫的容錯移轉夥伴名稱。</span><span class="sxs-lookup"><span data-stu-id="bb799-130">The name of the failover partner for the database.</span></span> <span data-ttu-id="bb799-131">括號內會顯示 [主控台使用者的 Windows 驗證] 或 [登入 '***\<login name>***' 的 SQL Server 驗證]。</span><span class="sxs-lookup"><span data-stu-id="bb799-131">Either **Windows Authentication of console user** or **SQL Server Authentication of login '***\<login name>***'** is displayed within the parentheses.</span></span> <span data-ttu-id="bb799-132">如果之前已加入這個執行個體，則這是目前使用的驗證資訊；如果尚未將這個執行個體加入至監視器，則這是將要使用的驗證資訊。</span><span class="sxs-lookup"><span data-stu-id="bb799-132">This is the authentication information currently used, if the instance has been added before, or that will be used, if this instance has not been added to the monitor.</span></span>|  
  
 <span data-ttu-id="bb799-133">**當我按一下確定時顯示管理伺服器連接對話方塊**</span><span class="sxs-lookup"><span data-stu-id="bb799-133">**Show the Manage Server Connections dialog box when I click OK.**</span></span>  
 <span data-ttu-id="bb799-134">依預設，若是先前未給予認證的夥伴伺服器執行個體，「資料庫鏡像監視器」會使用「Windows 驗證」認證。</span><span class="sxs-lookup"><span data-stu-id="bb799-134">By default, Database Mirroring Monitor uses Windows Authentication credentials for partner server instances for which credentials have not been previously given.</span></span> <span data-ttu-id="bb799-135">當您完成資料庫的註冊時，啟用此選項即可變更一個或多個伺服器執行個體的認證。</span><span class="sxs-lookup"><span data-stu-id="bb799-135">Enable this option to change the credentials for one or more server instances when you finish registering databases.</span></span>  
  
 <span data-ttu-id="bb799-136">如果已啟用此選項，當您按一下 [確定] 時，[管理伺服器連接]  對話方塊便會開啟。</span><span class="sxs-lookup"><span data-stu-id="bb799-136">If this option is enabled, when you click **OK**, the **Manage Server Connections** dialog box opens.</span></span> <span data-ttu-id="bb799-137">您可以在這個對話方塊中選擇您要指定認證的伺服器執行個體，以供監視器連接到特定容錯移轉夥伴時使用。</span><span class="sxs-lookup"><span data-stu-id="bb799-137">There, you can choose a server instance for which you want to specify credentials for the monitor to use when connecting to a given failover partner.</span></span>  
  
 <span data-ttu-id="bb799-138">若要編輯夥伴的認證，請在 [伺服器執行個體]  方格中找到其項目，然後按一下該資料列上的 [編輯]  。</span><span class="sxs-lookup"><span data-stu-id="bb799-138">To edit the credentials for a partner, locate its entry in the **Server instances** grid, and click **Edit** on that row.</span></span> <span data-ttu-id="bb799-139">此時便會開啟該伺服器執行個體名稱的 [連接到伺服器]  對話方塊，而且會將認證控制項初始化為目前的快取值。</span><span class="sxs-lookup"><span data-stu-id="bb799-139">This opens the **Connect to Server** dialog box for that server instance name, with the credential controls initialized to the current cached value.</span></span> <span data-ttu-id="bb799-140">視需要變更認證，然後按一下 [連接] 。</span><span class="sxs-lookup"><span data-stu-id="bb799-140">Change the credentials as necessary and click **Connect**.</span></span> <span data-ttu-id="bb799-141">如果認證具有足夠的權限，就會以新的認證更新 [連接方式]  資料行。</span><span class="sxs-lookup"><span data-stu-id="bb799-141">If the credentials have sufficient privileges, the **Connect Using** column is updated with the new credentials.</span></span>  
  
 <span data-ttu-id="bb799-142">**套用**</span><span class="sxs-lookup"><span data-stu-id="bb799-142">**Apply**</span></span>  
 <span data-ttu-id="bb799-143">按一下這個按鈕即可註冊選取的資料庫 (並儲存夥伴伺服器執行個體的認證)，同時將對話方塊保持為開啟狀態。</span><span class="sxs-lookup"><span data-stu-id="bb799-143">Click this button to register the selected databases (and save credentials for the partner server instances) while keeping the dialog box open.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb799-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb799-144">See Also</span></span>  
 <span data-ttu-id="bb799-145">[啟動資料庫鏡像監視器 &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="bb799-145">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="bb799-146">[監視資料庫鏡像 &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="bb799-146">[Monitoring Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="bb799-147">啟動設定資料庫鏡像安全性精靈 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="bb799-147">Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;</span></span>](start-the-configuring-database-mirroring-security-wizard.md)  
  
  
