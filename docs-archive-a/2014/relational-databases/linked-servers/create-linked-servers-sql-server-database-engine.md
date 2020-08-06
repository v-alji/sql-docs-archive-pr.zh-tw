---
title: 建立連結的伺服器 (SQL Server Database Engine) | Microsoft Docs
ms.custom: ''
ms.date: 11/20/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.linkedserver.properties.general.f1
- sql12.swb.linkedserver.properties.security.f1
- sql12.swb.linkedserver.properties.provider.f1
- sql12.swb.linkedserver.properties.options.f1
helpviewer_keywords:
- linked servers [SQL Server], creating
ms.assetid: 3228065d-de8f-4ece-a9b1-e06d3dca9310
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6b28468db1024a9789364e5b6e5c115cba71fa9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698200"
---
# <a name="create-linked-servers-sql-server-database-engine"></a><span data-ttu-id="f5d71-102">建立連結的伺服器 (SQL Server Database Engine)</span><span class="sxs-lookup"><span data-stu-id="f5d71-102">Create Linked Servers (SQL Server Database Engine)</span></span>
  <span data-ttu-id="f5d71-103">此主題說明如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，建立連結的伺服器以及存取來自其他 [!INCLUDE[tsql](../../includes/tsql-md.md)]的資料。</span><span class="sxs-lookup"><span data-stu-id="f5d71-103">This topic shows how to create a linked server and access data from another [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="f5d71-104">透過建立連結的伺服器，您可以處理多個來源的資料。</span><span class="sxs-lookup"><span data-stu-id="f5d71-104">By creating a linked server,  you can work with data from multiple sources.</span></span> <span data-ttu-id="f5d71-105">連結的伺服器不必是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的另一個執行個體，但那是常見狀況。</span><span class="sxs-lookup"><span data-stu-id="f5d71-105">The linked server does not have to be another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but that is a common scenario.</span></span>  
  
##  <a name="background"></a><a name="Background"></a> <span data-ttu-id="f5d71-106">背景</span><span class="sxs-lookup"><span data-stu-id="f5d71-106">Background</span></span>  
 <span data-ttu-id="f5d71-107">連結的伺服器可讓您對 OLE DB 資料來源存取分散式異質性查詢。</span><span class="sxs-lookup"><span data-stu-id="f5d71-107">A linked server allows for access to distributed, heterogeneous queries against OLE DB data sources.</span></span> <span data-ttu-id="f5d71-108">建立連結的伺服器之後，即可對這部伺服器執行分散式查詢，而且查詢可以加入來自多個資料來源的資料表。</span><span class="sxs-lookup"><span data-stu-id="f5d71-108">After a linked server is created, distributed queries can be run against this server, and queries can join tables from more than one data source.</span></span> <span data-ttu-id="f5d71-109">如果連結的伺服器定義為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體，就可以執行遠端預存程序。</span><span class="sxs-lookup"><span data-stu-id="f5d71-109">If the linked server is defined as an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], remote stored procedures can be executed.</span></span>  
  
 <span data-ttu-id="f5d71-110">連結之伺服器的功能以及所需的引數可能會大大地改變。</span><span class="sxs-lookup"><span data-stu-id="f5d71-110">The capabilities and required arguments of the linked server can vary significantly.</span></span> <span data-ttu-id="f5d71-111">本主題中的範例會提供一般範例，但不會描述所有選項。</span><span class="sxs-lookup"><span data-stu-id="f5d71-111">The examples in this topic provide a typical example but all options are not described.</span></span> <span data-ttu-id="f5d71-112">如需詳細資訊，請參閱 [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)的資料。</span><span class="sxs-lookup"><span data-stu-id="f5d71-112">For more information, see [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).</span></span>  
  
##  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f5d71-113">Security</span><span class="sxs-lookup"><span data-stu-id="f5d71-113">Security</span></span>  
  
### <a name="permissions"></a><span data-ttu-id="f5d71-114">權限</span><span class="sxs-lookup"><span data-stu-id="f5d71-114">Permissions</span></span>  
 <span data-ttu-id="f5d71-115">使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 語句時，需要 `ALTER ANY LINKED SERVER` 伺服器的許可權或**setupadmin**固定伺服器角色中的成員資格。</span><span class="sxs-lookup"><span data-stu-id="f5d71-115">When using [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, requires `ALTER ANY LINKED SERVER` permission on the server or membership in the **setupadmin** fixed server role.</span></span> <span data-ttu-id="f5d71-116">使用時 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] `CONTROL SERVER` ，需要**系統管理員（sysadmin** ）固定伺服器角色的許可權或成員資格。</span><span class="sxs-lookup"><span data-stu-id="f5d71-116">When using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] requires `CONTROL SERVER` permission or membership in the **sysadmin** fixed server role.</span></span>  
  
##  <a name="how-to-create-a-linked-server"></a><a name="Procedures"></a> <span data-ttu-id="f5d71-117">如何建立連結的伺服器</span><span class="sxs-lookup"><span data-stu-id="f5d71-117">How to Create a Linked Server</span></span>  
 <span data-ttu-id="f5d71-118">您可以使用下列任一項：</span><span class="sxs-lookup"><span data-stu-id="f5d71-118">You can use any of the following:</span></span>  
  
-   [<span data-ttu-id="f5d71-119">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f5d71-119">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="f5d71-120">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f5d71-120">Transact-SQL</span></span>](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f5d71-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f5d71-121">Using SQL Server Management Studio</span></span>  
  
##### <a name="to-create-a-linked-server-to-another-instance-of-sql-server-using-sql-server-management-studio"></a><span data-ttu-id="f5d71-122">若要使用 SQL Server Management Studio 建立與另一個 SQL Server 執行個體的連結伺服器</span><span class="sxs-lookup"><span data-stu-id="f5d71-122">To create a linked server to another instance of SQL Server Using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="f5d71-123">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，開啟 [物件總管]，展開 **[伺服器物件]** ，以滑鼠右鍵按一下 **[連結的伺服器]** ，然後按一下 **[新增連結的伺服器]** 。</span><span class="sxs-lookup"><span data-stu-id="f5d71-123">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer, expand **Server Objects**, right-click **Linked Servers**, and then click **New Linked Server**.</span></span>  
  
2.  <span data-ttu-id="f5d71-124">在 **[一般]** 頁面的 **[連結的伺服器]** 方塊中，輸入您要連結之 **[SQL Server]** 的執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="f5d71-124">On the **General** page, in the **Linked server** box, type the name of the instance of **SQL Server** that you area linking to.</span></span>  
  
     <span data-ttu-id="f5d71-125">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="f5d71-125">**SQL Server**</span></span>  
     <span data-ttu-id="f5d71-126">將連結的伺服器識別為 [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="f5d71-126">Identify the linked server as an instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f5d71-127">如果您使用這個定義 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 連結之伺服器的方法， **[連結的伺服器]** 中所指定的名稱就必須是伺服器的網路名稱。</span><span class="sxs-lookup"><span data-stu-id="f5d71-127">If you use this method of defining a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] linked server, the name specified in **Linked server** must be the network name of the server.</span></span> <span data-ttu-id="f5d71-128">另外，從伺服器擷取的任何資料表，都會是來自已連結伺服器上之登入所定義的預設資料庫。</span><span class="sxs-lookup"><span data-stu-id="f5d71-128">Also, any tables retrieved from the server are from the default database defined for the login on the linked server.</span></span>  
  
     <span data-ttu-id="f5d71-129">**其他資料來源**</span><span class="sxs-lookup"><span data-stu-id="f5d71-129">**Other data source**</span></span>  
     <span data-ttu-id="f5d71-130">指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]以外的 OLE DB 伺服器。</span><span class="sxs-lookup"><span data-stu-id="f5d71-130">Specify an OLE DB server type other than [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f5d71-131">按一下這個選項會啟動在它下面的選項。</span><span class="sxs-lookup"><span data-stu-id="f5d71-131">Clicking this option activates the options below it.</span></span>  
  
     <span data-ttu-id="f5d71-132">**提供者**</span><span class="sxs-lookup"><span data-stu-id="f5d71-132">**Provider**</span></span>  
     <span data-ttu-id="f5d71-133">從清單方塊中選取 OLE DB 資料來源。</span><span class="sxs-lookup"><span data-stu-id="f5d71-133">Select an OLE DB data source from the list box.</span></span> <span data-ttu-id="f5d71-134">在登錄中，OLE DB 提供者是使用給定的 PROGID 註冊。</span><span class="sxs-lookup"><span data-stu-id="f5d71-134">The OLE DB provider is registered with the given PROGID in the registry.</span></span>  
  
     <span data-ttu-id="f5d71-135">**產品名稱**</span><span class="sxs-lookup"><span data-stu-id="f5d71-135">**Product name**</span></span>  
     <span data-ttu-id="f5d71-136">輸入 OLE DB 資料來源的產品名稱，以加入成為連結的伺服器。</span><span class="sxs-lookup"><span data-stu-id="f5d71-136">Type the product name of the OLE DB data source to add as a linked server.</span></span>  
  
     <span data-ttu-id="f5d71-137">**資料來源**</span><span class="sxs-lookup"><span data-stu-id="f5d71-137">**Data source**</span></span>  
     <span data-ttu-id="f5d71-138">輸入資料來源的名稱，如 OLE DB 提供者所解譯。</span><span class="sxs-lookup"><span data-stu-id="f5d71-138">Type the name of the data source as interpreted by the OLE DB provider.</span></span> <span data-ttu-id="f5d71-139">如果您要連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體，請提供執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="f5d71-139">If you are connecting to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], provide the instance name.</span></span>  
  
     <span data-ttu-id="f5d71-140">**提供者字串**</span><span class="sxs-lookup"><span data-stu-id="f5d71-140">**Provider string**</span></span>  
     <span data-ttu-id="f5d71-141">輸入對應至資料來源之 OLE DB 提供者的唯一程式設計識別碼 (PROGID)。</span><span class="sxs-lookup"><span data-stu-id="f5d71-141">Type the unique programmatic identifier (PROGID) of the OLE DB provider that corresponds to the data source.</span></span> <span data-ttu-id="f5d71-142">如需有效提供者字串的範例，請參閱 [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)的資料。</span><span class="sxs-lookup"><span data-stu-id="f5d71-142">For examples of valid provider strings, see [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).</span></span>  
  
     <span data-ttu-id="f5d71-143">**位置**</span><span class="sxs-lookup"><span data-stu-id="f5d71-143">**Location**</span></span>  
     <span data-ttu-id="f5d71-144">依 OLE DB 提供者的解譯，輸入資料庫的位置。</span><span class="sxs-lookup"><span data-stu-id="f5d71-144">Type the location of the database as interpreted by the OLE DB provider.</span></span>  
  
     <span data-ttu-id="f5d71-145">**目錄**</span><span class="sxs-lookup"><span data-stu-id="f5d71-145">**Catalog**</span></span>  
     <span data-ttu-id="f5d71-146">輸入連接到 OLE DB 提供者時，要使用的目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="f5d71-146">Type the name of the catalog to use when making a connection to the OLE DB provider.</span></span>  
  
     <span data-ttu-id="f5d71-147">若要測試連接到連結伺服器的能力，在 [物件總管] 中，以滑鼠右鍵按一下連結伺服器，然後按一下 **[測試連接]** 。</span><span class="sxs-lookup"><span data-stu-id="f5d71-147">To test the ability to connect to a linked server, in Object Explorer, right-click the linked server and then click **Test Connection**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f5d71-148">如果 **[SQL Server]** 的執行個體是預設的執行個體，請輸入裝載 **[SQL Server]** 執行個體之電腦的名稱。</span><span class="sxs-lookup"><span data-stu-id="f5d71-148">If the instance of **SQL Server** is the default instance, enter the name of the computer that hosts the instance of **SQL Server**.</span></span> <span data-ttu-id="f5d71-149">如果 **SQL Server** 是具名執行個體，請輸入電腦的名稱和執行個體的名稱，例如 **Accounting\SQLExpress**。</span><span class="sxs-lookup"><span data-stu-id="f5d71-149">If the **SQL Server** is a named instance, enter the name of the computer and the name of the instance, such as **Accounting\SQLExpress**.</span></span>  
  
3.  <span data-ttu-id="f5d71-150">在 [伺服器類型]  區域中，選取 [SQL Server]  表示連結的伺服器是 **SQL Server** 的另一個執行個體。</span><span class="sxs-lookup"><span data-stu-id="f5d71-150">In the **Server type** area, select **SQL Server** to indicate that the linked server is another instance of **SQL Server**.</span></span>  
  
4.  <span data-ttu-id="f5d71-151">在 **[安全性]** 頁面上，指定原始 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 連線到連結的伺服器時將使用的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="f5d71-151">On the **Security** page, specify the security context that will be used when the original [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connects to the linked server.</span></span> <span data-ttu-id="f5d71-152">在使用者使用其網域登入進行連線的網域環境中，選取 [使用登入的目前安全性內容建立]  通常是最佳選擇。</span><span class="sxs-lookup"><span data-stu-id="f5d71-152">In a domain environment where users are connecting by using their domain logins, selecting **Be made using the login's current security context** is often the best choice.</span></span> <span data-ttu-id="f5d71-153">當使用者使用 **[SQL Server]** 登入連線到原始 **[SQL Server]** 時，最佳選擇通常是選取 **[使用此安全性內容]** ，然後提供所需的認證在連結的伺服器進行驗證。</span><span class="sxs-lookup"><span data-stu-id="f5d71-153">When users connect to the original **SQL Server** by using a **SQL Server** login, the best choice is often to select **By using this security context**, and then providing the necessary credentials to authenticate at the linked server.</span></span>  
  
     <span data-ttu-id="f5d71-154">**本機登入**</span><span class="sxs-lookup"><span data-stu-id="f5d71-154">**Local login**</span></span>  
     <span data-ttu-id="f5d71-155">指定可以連接到連結伺服器的本機登入。</span><span class="sxs-lookup"><span data-stu-id="f5d71-155">Specify the local login that can connect to the linked server.</span></span> <span data-ttu-id="f5d71-156">本機登入可以是使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證的登入或 Windows 驗證登入。</span><span class="sxs-lookup"><span data-stu-id="f5d71-156">The local login can be either a login using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication or a Windows Authentication login.</span></span> <span data-ttu-id="f5d71-157">使用這份清單可限制與特定登入的連接，或允許某些登入連接成不同的登入。</span><span class="sxs-lookup"><span data-stu-id="f5d71-157">Use this list to restrict the connection to specific logins, or to allow some logins to connect as a different login.</span></span>  
  
     <span data-ttu-id="f5d71-158">**Impersonate**</span><span class="sxs-lookup"><span data-stu-id="f5d71-158">**Impersonate**</span></span>  
     <span data-ttu-id="f5d71-159">將使用者名稱和密碼從本機登入傳送給連結伺服器。</span><span class="sxs-lookup"><span data-stu-id="f5d71-159">Pass the username and password from the local login to the linked server.</span></span> <span data-ttu-id="f5d71-160">若為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證，則遠端伺服器上必須要有名稱和密碼完全相同的登入。</span><span class="sxs-lookup"><span data-stu-id="f5d71-160">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, a login with the exact same name and password must exist on the remote server.</span></span> <span data-ttu-id="f5d71-161">若為 Windows 登入，則登入必須是連結伺服器上的有效登入。</span><span class="sxs-lookup"><span data-stu-id="f5d71-161">For Windows logins, the login must be a valid login on the linked server.</span></span>  
  
     <span data-ttu-id="f5d71-162">若要使用模擬，則組態必須符合委派需求。</span><span class="sxs-lookup"><span data-stu-id="f5d71-162">To use impersonation, the configuration must meet the requirement for delegation.</span></span>  
  
     <span data-ttu-id="f5d71-163">**遠端使用者**</span><span class="sxs-lookup"><span data-stu-id="f5d71-163">**Remote User**</span></span>  
     <span data-ttu-id="f5d71-164">使用遠端使用者以對應未定義於 **[本機登入]** 中的使用者。</span><span class="sxs-lookup"><span data-stu-id="f5d71-164">Use the remote user to map users not defined in **Local login**.</span></span> <span data-ttu-id="f5d71-165">**[遠端使用者]** 必須是遠端伺服器上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證登入。</span><span class="sxs-lookup"><span data-stu-id="f5d71-165">The **Remote User** must be a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication login on the remote server.</span></span>  
  
     <span data-ttu-id="f5d71-166">**遠端密碼**</span><span class="sxs-lookup"><span data-stu-id="f5d71-166">**Remote Password**</span></span>  
     <span data-ttu-id="f5d71-167">指定遠端使用者的密碼。</span><span class="sxs-lookup"><span data-stu-id="f5d71-167">Specify the password of the Remote User.</span></span>  
  
     <span data-ttu-id="f5d71-168">**加入**</span><span class="sxs-lookup"><span data-stu-id="f5d71-168">**Add**</span></span>  
     <span data-ttu-id="f5d71-169">加入新的本機登入。</span><span class="sxs-lookup"><span data-stu-id="f5d71-169">Add a new local login.</span></span>  
  
     <span data-ttu-id="f5d71-170">**移除**</span><span class="sxs-lookup"><span data-stu-id="f5d71-170">**Remove**</span></span>  
     <span data-ttu-id="f5d71-171">移除現有的本機登入。</span><span class="sxs-lookup"><span data-stu-id="f5d71-171">Remove an existing local login.</span></span>  
  
     <span data-ttu-id="f5d71-172">**不建立**</span><span class="sxs-lookup"><span data-stu-id="f5d71-172">**Not be made**</span></span>  
     <span data-ttu-id="f5d71-173">指定不會為未定義於清單中的登入建立連接。</span><span class="sxs-lookup"><span data-stu-id="f5d71-173">Specify that a connection will not be made for logins not defined in the list.</span></span>  
  
     <span data-ttu-id="f5d71-174">**不使用安全性內容建立**</span><span class="sxs-lookup"><span data-stu-id="f5d71-174">**Be made without using a security context**</span></span>  
     <span data-ttu-id="f5d71-175">指定不會使用安全性內容為未定義於清單中的登入建立連接。</span><span class="sxs-lookup"><span data-stu-id="f5d71-175">Specify that a connection will be made without using a security context for logins not defined in the list.</span></span>  
  
     <span data-ttu-id="f5d71-176">**使用登入的目前安全性內容建立**</span><span class="sxs-lookup"><span data-stu-id="f5d71-176">**Be made using the login's current security context**</span></span>  
     <span data-ttu-id="f5d71-177">指定使用登入的目前安全性內容為未定義於清單中的登入建立連接。</span><span class="sxs-lookup"><span data-stu-id="f5d71-177">Specify that a connection will be made using the current security context of the login for logins not defined in the list.</span></span> <span data-ttu-id="f5d71-178">如果使用 Windows 驗證連接到本機伺服器，則會使用您的 Windows 認證來連接到遠端伺服器。</span><span class="sxs-lookup"><span data-stu-id="f5d71-178">If connected to the local server using Windows Authentication, your windows credentials will be used to connect to the remote server.</span></span> <span data-ttu-id="f5d71-179">如果使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證連接到本機伺服器，則會使用登入名稱和密碼來連接到遠端伺服器。</span><span class="sxs-lookup"><span data-stu-id="f5d71-179">If connected to the local server using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, login name and password will be used to connect to the remote server.</span></span> <span data-ttu-id="f5d71-180">在此情況下，遠端伺服器上必須要有名稱和密碼完全相同的登入。</span><span class="sxs-lookup"><span data-stu-id="f5d71-180">In this case a login with the exact same name and password must exist on the remote server.</span></span>  
  
     <span data-ttu-id="f5d71-181">**使用此安全性內容建立**</span><span class="sxs-lookup"><span data-stu-id="f5d71-181">**Be made using this security context**</span></span>  
     <span data-ttu-id="f5d71-182">指定使用 **[遠端登入]** 和 **[指定密碼]** 方塊中所指定的登入和密碼為未定義於清單中的登入建立連接。</span><span class="sxs-lookup"><span data-stu-id="f5d71-182">Specify that a connection will be made using the login and password specified in the **Remote login** and **With password** boxes for logins not defined in the list.</span></span> <span data-ttu-id="f5d71-183">遠端登入必須是遠端伺服器上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證登入。</span><span class="sxs-lookup"><span data-stu-id="f5d71-183">The remote login must be a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication login on the remote server.</span></span>  
  
5.  <span data-ttu-id="f5d71-184">(選擇性) 若要檢視或指定伺服器選項，請按一下 **[伺服器選項]**  頁面。</span><span class="sxs-lookup"><span data-stu-id="f5d71-184">Optionally, to view or specify server options, click the **Server Options**  page.</span></span>  
  
     <span data-ttu-id="f5d71-185">**定序相容**</span><span class="sxs-lookup"><span data-stu-id="f5d71-185">**Collation Compatible**</span></span>  
     <span data-ttu-id="f5d71-186">影響針對連結伺服器的分散式查詢執行。</span><span class="sxs-lookup"><span data-stu-id="f5d71-186">Affects Distributed Query execution against linked servers.</span></span> <span data-ttu-id="f5d71-187">如果這個選項設為 true，關於字元集和定序順序 (或排序順序)， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會假設連結伺服器中的所有字元都與本機伺服器相容。</span><span class="sxs-lookup"><span data-stu-id="f5d71-187">If this option is set to true, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assumes that all characters in the linked server are compatible with the local server, with regard to character set and collation sequence (or sort order).</span></span> <span data-ttu-id="f5d71-188">這會使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 能夠將字元資料行的比較傳給提供者。</span><span class="sxs-lookup"><span data-stu-id="f5d71-188">This enables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to send comparisons on character columns to the provider.</span></span> <span data-ttu-id="f5d71-189">如果未設定這個選項， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 一律會在本機環境中評估字元資料行的比較。</span><span class="sxs-lookup"><span data-stu-id="f5d71-189">If this option is not set, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] always evaluates comparisons on character columns locally.</span></span>  
  
     <span data-ttu-id="f5d71-190">只有在確定對應於連結伺服器的資料來源與本機伺服器的字元集和排序順序相同時，才應該設定這個選項。</span><span class="sxs-lookup"><span data-stu-id="f5d71-190">This option should be set only if it is certain that the data source corresponding to the linked server has the same character set and sort order as the local server.</span></span>  
  
     <span data-ttu-id="f5d71-191">**資料存取**</span><span class="sxs-lookup"><span data-stu-id="f5d71-191">**Data Access**</span></span>  
     <span data-ttu-id="f5d71-192">啟用和停用連結伺服器的分散式查詢存取。</span><span class="sxs-lookup"><span data-stu-id="f5d71-192">Enables and disables a linked server for distributed query access.</span></span>  
  
     <span data-ttu-id="f5d71-193">**RPC**</span><span class="sxs-lookup"><span data-stu-id="f5d71-193">**RPC**</span></span>  
     <span data-ttu-id="f5d71-194">從指定伺服器啟用 RPC。</span><span class="sxs-lookup"><span data-stu-id="f5d71-194">Enables RPC from the specified server.</span></span>  
  
     <span data-ttu-id="f5d71-195">**RPC 輸出**</span><span class="sxs-lookup"><span data-stu-id="f5d71-195">**RPC Out**</span></span>  
     <span data-ttu-id="f5d71-196">啟用對指定伺服器的 RPC。</span><span class="sxs-lookup"><span data-stu-id="f5d71-196">Enables RPC to the specified server.</span></span>  
  
     <span data-ttu-id="f5d71-197">**使用遠端定序**</span><span class="sxs-lookup"><span data-stu-id="f5d71-197">**Use Remote Collation**</span></span>  
     <span data-ttu-id="f5d71-198">決定將使用遠端資料行或本機伺服器的定序。</span><span class="sxs-lookup"><span data-stu-id="f5d71-198">Determines whether the collation of a remote column or of a local server will be used.</span></span>  
  
     <span data-ttu-id="f5d71-199">如果為 True，針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料來源會使用遠端資料行的定序，而針對非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料來源會使用定序名稱中所指定的定序。</span><span class="sxs-lookup"><span data-stu-id="f5d71-199">If true, the collation of remote columns is used for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data sources, and the collation specified in collation name is used for non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data sources.</span></span>  
  
     <span data-ttu-id="f5d71-200">如果為 False，分散式查詢一律會使用本機伺服器的預設定序，而定序名稱與遠端資料行的定序則會被忽略。</span><span class="sxs-lookup"><span data-stu-id="f5d71-200">If false, distributed queries will always use the default collation of the local server, while collation name and the collation of remote columns are ignored.</span></span> <span data-ttu-id="f5d71-201">預設為 false。</span><span class="sxs-lookup"><span data-stu-id="f5d71-201">The default is false.</span></span>  
  
     <span data-ttu-id="f5d71-202">**定序名稱**</span><span class="sxs-lookup"><span data-stu-id="f5d71-202">**Collation Name**</span></span>  
     <span data-ttu-id="f5d71-203">如果使用遠端定序為 True，並且資料來源不是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料來源，請指定遠端資料來源所使用的定序名稱。</span><span class="sxs-lookup"><span data-stu-id="f5d71-203">Specifies the name of the collation used by the remote data source if use remote collation is true and the data source is not a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data source.</span></span> <span data-ttu-id="f5d71-204">這個名稱必須是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]所支援的定序之一。</span><span class="sxs-lookup"><span data-stu-id="f5d71-204">The name must be one of the collations supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="f5d71-205">當存取不是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，但其定序卻符合某項 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 定序的 OLE DB 資料來源時，請使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="f5d71-205">Use this option when accessing an OLE DB data source other than [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but whose collation matches one of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] collations.</span></span>  
  
     <span data-ttu-id="f5d71-206">連結伺服器必須支援供這部伺服器的所有資料行使用的單一定序。</span><span class="sxs-lookup"><span data-stu-id="f5d71-206">The linked server must support a single collation to be used for all columns in that server.</span></span> <span data-ttu-id="f5d71-207">如果連結伺服器支援單一資料來源內的多重定序，或無法確定連結伺服器的定序是否符合某項 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 定序時，請勿設定這個選項。</span><span class="sxs-lookup"><span data-stu-id="f5d71-207">Do not set this option if the linked server supports multiple collations within a single data source, or if the linked server's collation cannot be determined to match one of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] collations.</span></span>  
  
     <span data-ttu-id="f5d71-208">**連接逾時**</span><span class="sxs-lookup"><span data-stu-id="f5d71-208">**Connection Timeout**</span></span>  
     <span data-ttu-id="f5d71-209">連接到連結伺服器的逾時值 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="f5d71-209">Time-out value in seconds for connecting to a linked server.</span></span>  
  
     <span data-ttu-id="f5d71-210">若為 0，則使用 **sp_configure** 的預設 [remote query timeout](../../database-engine/configure-windows/configure-the-remote-login-timeout-server-configuration-option.md) 選項值。</span><span class="sxs-lookup"><span data-stu-id="f5d71-210">If 0, use the **sp_configure** default [remote login timeout](../../database-engine/configure-windows/configure-the-remote-login-timeout-server-configuration-option.md) option value.</span></span>  
  
     <span data-ttu-id="f5d71-211">**查詢逾時**</span><span class="sxs-lookup"><span data-stu-id="f5d71-211">**Query Timeout**</span></span>  
     <span data-ttu-id="f5d71-212">針對連結伺服器進行查詢的逾時值 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="f5d71-212">Time-out value in seconds for queries against a linked server.</span></span>  
  
     <span data-ttu-id="f5d71-213">如果為 0，則使用 **sp_configure** 預設 [remote query timeout](../../database-engine/configure-windows/configure-the-remote-query-timeout-server-configuration-option.md) 選項值。</span><span class="sxs-lookup"><span data-stu-id="f5d71-213">If 0, use the **sp_configure** default [remote query timeout](../../database-engine/configure-windows/configure-the-remote-query-timeout-server-configuration-option.md) option value.</span></span>  
  
     <span data-ttu-id="f5d71-214">**啟用分散式交易的升級**</span><span class="sxs-lookup"><span data-stu-id="f5d71-214">**Enable Promotion of Distributed Transactions**</span></span>  
     <span data-ttu-id="f5d71-215">使用此選項，透過 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 分散式交易協調器 (MS DTC) 交易，保護伺服器對伺服器程序的動作。</span><span class="sxs-lookup"><span data-stu-id="f5d71-215">Use this option to protect the actions of a server-to-server procedure through a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) transaction.</span></span> <span data-ttu-id="f5d71-216">此選項為 TRUE 時，呼叫遠端預存程序就會啟動分散式交易，而且會利用 MS DTC 來編列這項交易。</span><span class="sxs-lookup"><span data-stu-id="f5d71-216">When this option is TRUE, calling a remote stored procedure starts a distributed transaction and enlists the transaction with MS DTC.</span></span> <span data-ttu-id="f5d71-217">如需詳細資訊，請參閱 [sp_serveroption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-serveroption-transact-sql)的資料。</span><span class="sxs-lookup"><span data-stu-id="f5d71-217">For more information, see [sp_serveroption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-serveroption-transact-sql).</span></span>  
  
6.  <span data-ttu-id="f5d71-218">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="f5d71-218">Click **OK**.</span></span>  
  
##### <a name="to-view-the-provider-options"></a><span data-ttu-id="f5d71-219">若要檢視提供者選項</span><span class="sxs-lookup"><span data-stu-id="f5d71-219">To view the provider options</span></span>  
  
-   <span data-ttu-id="f5d71-220">若要檢視提供者提供的選項，請按一下 **[提供者選項]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="f5d71-220">To view the options that the provider makes available, click the **Providers Options** page.</span></span>  
  
     <span data-ttu-id="f5d71-221">所有提供者的可用選項並不相同。</span><span class="sxs-lookup"><span data-stu-id="f5d71-221">All providers do not have the same options available.</span></span> <span data-ttu-id="f5d71-222">例如，某些資料類型有索引可用，而某些可能沒有。</span><span class="sxs-lookup"><span data-stu-id="f5d71-222">For example, some types of data have indexes available and some might not.</span></span> <span data-ttu-id="f5d71-223">使用這個對話方塊來幫助 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 了解提供者的功能。</span><span class="sxs-lookup"><span data-stu-id="f5d71-223">Use this dialog box to help [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] understand the capabilities of the provider.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f5d71-224">會安裝某些共用的資料提供者，不過當提供資料的產品變更時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所安裝的該提供者不一定支援所有的最新功能。</span><span class="sxs-lookup"><span data-stu-id="f5d71-224">installs some common data providers, however when the product providing the data changes, the provider installed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] might not support all the newest features.</span></span> <span data-ttu-id="f5d71-225">提供資料之產品功能的最佳資源來源是該產品的說明文件。</span><span class="sxs-lookup"><span data-stu-id="f5d71-225">The best source of information about the capabilities of the product providing the data is the documentation for that product.</span></span>  
  
     <span data-ttu-id="f5d71-226">**動態參數**</span><span class="sxs-lookup"><span data-stu-id="f5d71-226">**Dynamic parameter**</span></span>  
     <span data-ttu-id="f5d71-227">表示提供者允許在參數化查詢時使用 '?' 參數標記語法。</span><span class="sxs-lookup"><span data-stu-id="f5d71-227">Indicates that the provider allows '?' parameter marker syntax for parameterized queries.</span></span> <span data-ttu-id="f5d71-228">這個選項只有在提供者支援 **IcommandWithParameters** 介面，並支援 '?' 作為參數標記時才能設定。</span><span class="sxs-lookup"><span data-stu-id="f5d71-228">Set this option only if the provider supports the **ICommandWithParameters** interface and supports a '?' as the parameter marker.</span></span> <span data-ttu-id="f5d71-229">設定這個選項允許 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 針對提供者執行參數化查詢。</span><span class="sxs-lookup"><span data-stu-id="f5d71-229">Setting this option allows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to execute parameterized queries against the provider.</span></span> <span data-ttu-id="f5d71-230">針對提供者執行參數化查詢的能力，對於某些查詢而言可以達到較佳的效能。</span><span class="sxs-lookup"><span data-stu-id="f5d71-230">The ability to execute parameterized queries against the provider can result in better performance for certain queries.</span></span>  
  
     <span data-ttu-id="f5d71-231">**巢狀查詢**</span><span class="sxs-lookup"><span data-stu-id="f5d71-231">**Nested queries**</span></span>  
     <span data-ttu-id="f5d71-232">表示該提供者允許 FROM 子句中使用巢狀  `SELECT` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="f5d71-232">Indicates that the provider allows nested  `SELECT` statements in the FROM clause.</span></span> <span data-ttu-id="f5d71-233">設定這個選項允許 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 向需要在 FROM 子句中包含巢狀 SELECT 陳述式的提供者委派某些查詢。</span><span class="sxs-lookup"><span data-stu-id="f5d71-233">Setting this option allows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to delegate certain queries to the provider that require nesting SELECT statements in the FROM clause.</span></span>  
  
     <span data-ttu-id="f5d71-234">**限層級零**</span><span class="sxs-lookup"><span data-stu-id="f5d71-234">**Level zero only**</span></span>  
     <span data-ttu-id="f5d71-235">只會針對提供者叫用層級 0 的 OLE DB 介面。</span><span class="sxs-lookup"><span data-stu-id="f5d71-235">Only level 0 OLE DB interfaces are invoked against the provider.</span></span>  
  
     <span data-ttu-id="f5d71-236">**允許 Inprocess**</span><span class="sxs-lookup"><span data-stu-id="f5d71-236">**Allow inprocess**</span></span>  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f5d71-237">允許提供者被具現化為同處理序伺服器。</span><span class="sxs-lookup"><span data-stu-id="f5d71-237">allows the provider to be instantiated as an in-process server.</span></span> <span data-ttu-id="f5d71-238">未設定此選項時，預設的行為便是將提供者具現化於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 處理序之外。</span><span class="sxs-lookup"><span data-stu-id="f5d71-238">When this option is not set, the default behavior is to instantiate the provider outside the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process.</span></span> <span data-ttu-id="f5d71-239">將提供者起始於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 處理序之外可以保護 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 處理序不會受到提供者發生錯誤的影響。</span><span class="sxs-lookup"><span data-stu-id="f5d71-239">Instantiating the provider outside the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process protects the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process from errors in the provider.</span></span> <span data-ttu-id="f5d71-240">當提供者具現化於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 處理序之外時，便不允許對要參考的長資料行 (`text`、`ntext` 或 `image`) 進行更新或插入。</span><span class="sxs-lookup"><span data-stu-id="f5d71-240">When the provider is instantiated outside the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process, updates or inserts referencing long columns (`text`, `ntext`, or `image`) are not allowed.</span></span>  
  
     <span data-ttu-id="f5d71-241">**非交易更新**</span><span class="sxs-lookup"><span data-stu-id="f5d71-241">**Non transacted updates**</span></span>  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f5d71-242">即使 **ITransactionLocal** 無法使用，仍然允許更新。</span><span class="sxs-lookup"><span data-stu-id="f5d71-242">allows updates, even if **ITransactionLocal** is not available.</span></span> <span data-ttu-id="f5d71-243">如果已啟用此選項，則針對提供者的更新便無法復原，因為提供者不支援交易。</span><span class="sxs-lookup"><span data-stu-id="f5d71-243">If this option is enabled, updates against the provider are not recoverable, because the provider does not support transactions.</span></span>  
  
     <span data-ttu-id="f5d71-244">**索引為存取路徑**</span><span class="sxs-lookup"><span data-stu-id="f5d71-244">**Index as access path**</span></span>  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f5d71-245">嘗試使用提供者的索引來提取資料。</span><span class="sxs-lookup"><span data-stu-id="f5d71-245">attempts to use indexes of the provider to fetch data.</span></span> <span data-ttu-id="f5d71-246">依預設值，索引只用於中繼資料，絕不會開啟</span><span class="sxs-lookup"><span data-stu-id="f5d71-246">By default, indexes are used only for metadata and are never opened</span></span>  
  
     <span data-ttu-id="f5d71-247">**不允許特定存取**</span><span class="sxs-lookup"><span data-stu-id="f5d71-247">**Disallow ad hoc access**</span></span>  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f5d71-248">不允許透過 OPENROWSET 與 OPENDATASOURCE 函數對 OLE DB 提供者進行特定存取。</span><span class="sxs-lookup"><span data-stu-id="f5d71-248">does not allow ad hoc access through the OPENROWSET and OPENDATASOURCE functions against the OLE DB provider.</span></span> <span data-ttu-id="f5d71-249">未設定此選項時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 也不會允許特定存取。</span><span class="sxs-lookup"><span data-stu-id="f5d71-249">When this option is not set, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] also does not allow ad hoc access.</span></span>  
  
     <span data-ttu-id="f5d71-250">**支援 'Like' 運算子**</span><span class="sxs-lookup"><span data-stu-id="f5d71-250">**Supports 'Like' operator**</span></span>  
     <span data-ttu-id="f5d71-251">表示該提供者支援使用 LIKE 關鍵字的查詢。</span><span class="sxs-lookup"><span data-stu-id="f5d71-251">Indicates that the provider supports queries using the LIKE key word.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f5d71-252">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f5d71-252">Using Transact-SQL</span></span>  
 <span data-ttu-id="f5d71-253">若要使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 建立連結的伺服器，請使用 [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql) 和 [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="f5d71-253">To create a linked server by using [!INCLUDE[tsql](../../includes/tsql-md.md)], use the [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql) and [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql) statements.</span></span>  
  
##### <a name="to-create-a-linked-server-to-another-instance-of-sql-server-using-transact-sql"></a><span data-ttu-id="f5d71-254">若要使用 Transact-SQL 建立與另一個 SQL Server 執行個體的連結伺服器</span><span class="sxs-lookup"><span data-stu-id="f5d71-254">To create a linked server to another instance of SQL Server using Transact-SQL</span></span>  
  
1.  <span data-ttu-id="f5d71-255">在查詢編輯器中，輸入下列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 命令來連結名稱為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 `SRVR002\ACCTG`執行個體：</span><span class="sxs-lookup"><span data-stu-id="f5d71-255">In Query Editor, enter the following [!INCLUDE[tsql](../../includes/tsql-md.md)] command to link to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] named `SRVR002\ACCTG`:</span></span>  
  
    ```sql  
    USE [master]  
    GO  
    EXEC master.dbo.sp_addlinkedserver   
        @server = N'SRVR002\ACCTG',   
        @srvproduct=N'SQL Server' ;  
    GO  
  
    ```  
  
2.  <span data-ttu-id="f5d71-256">執行下列程式碼來設定連結的伺服器使用將使用連結的伺服器之登入的網域認證。</span><span class="sxs-lookup"><span data-stu-id="f5d71-256">Execute the following code to configure the linked server to use the domain credentials of the login that is using the linked server.</span></span>  
  
    ```sql  
    EXEC master.dbo.sp_addlinkedsrvlogin   
        @rmtsrvname = N'SRVR002\ACCTG',   
        @locallogin = NULL ,   
        @useself = N'True' ;  
    GO  
  
    ```  
  
##  <a name="follow-up-steps-to-take-after-you-create-a-linked-server"></a><a name="FollowUp"></a> <span data-ttu-id="f5d71-257">待處理：建立連結的伺服器之後所採取的步驟</span><span class="sxs-lookup"><span data-stu-id="f5d71-257">Follow Up: Steps to take after you create a linked server</span></span>  
  
#### <a name="to-test-the-linked-server"></a><span data-ttu-id="f5d71-258">若要測試連結的伺服器</span><span class="sxs-lookup"><span data-stu-id="f5d71-258">To test the linked server</span></span>  
  
-   <span data-ttu-id="f5d71-259">執行下列程式碼來測試連結之伺服器的連線。</span><span class="sxs-lookup"><span data-stu-id="f5d71-259">Execute the following code to test the connection to the linked server.</span></span> <span data-ttu-id="f5d71-260">此範例會傳回連結之伺服器上的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="f5d71-260">This example the returns the names of the databases on the linked server.</span></span>  
  
    ```sql  
    SELECT name FROM [SRVR002\ACCTG].master.sys.databases ;  
    GO  
  
    ```  
  
#### <a name="writing-a-query-that-joins-tables-from-a-linked-server"></a><span data-ttu-id="f5d71-261">撰寫加入來自連結伺服器之資料表的查詢</span><span class="sxs-lookup"><span data-stu-id="f5d71-261">Writing a query that joins tables from a linked server</span></span>  
  
-   <span data-ttu-id="f5d71-262">使用四部分的名稱來表示連結之伺服器上的物件。</span><span class="sxs-lookup"><span data-stu-id="f5d71-262">Use four-part names to refer to an object on a linked server.</span></span> <span data-ttu-id="f5d71-263">執行下列程式碼以傳回本機伺服器上的所有登入清單，及其連結之伺服器上相符的登入。</span><span class="sxs-lookup"><span data-stu-id="f5d71-263">Execute the following code to return a list of all logins on the local server and their matching logins on the linked server.</span></span>  
  
    ```sql  
    SELECT local.name AS LocalLogins, linked.name AS LinkedLogins  
    FROM master.sys.server_principals AS local  
    LEFT JOIN [SRVR002\ACCTG].master.sys.server_principals AS linked  
        ON local.name = linked.name ;  
    GO  
    ```  
  
     <span data-ttu-id="f5d71-264">當連結的伺服器登入傳回 NULL 時，表示該登入不存在連結的伺服器上。</span><span class="sxs-lookup"><span data-stu-id="f5d71-264">When NULL is returned for the linked server login it indicates that the login does not exist on the linked server.</span></span> <span data-ttu-id="f5d71-265">除非將連結的伺服器設定為傳遞不同的安全性內容，或連結的伺服器接受匿名連線，否則這些登入將無法使用連結的伺服器。</span><span class="sxs-lookup"><span data-stu-id="f5d71-265">These logins will not be able to use the linked server unless the linked server is configured to pass a different security context or the linked server accepts anonymous connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5d71-266">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5d71-266">See Also</span></span>  
 <span data-ttu-id="f5d71-267">[連結的伺服器 &#40;Database Engine&#41;](linked-servers-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="f5d71-267">[Linked Servers &#40;Database Engine&#41;](linked-servers-database-engine.md) </span></span>  
 <span data-ttu-id="f5d71-268">[sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f5d71-268">[sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql) </span></span>  
 [<span data-ttu-id="f5d71-269">sp_serveroption &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f5d71-269">sp_serveroption &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-serveroption-transact-sql)  
  
  
