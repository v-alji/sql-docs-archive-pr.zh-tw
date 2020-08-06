---
title: 建立登入 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.LOGIN.SERVERROLES.F1
- sql12.swb.login.databaseaccess.f1
- sql12.swb.login.general.f1
- sql12.swb.login.effectivepermissions.f1
- sql12.swb.login.status.f1
helpviewer_keywords:
- authentication [SQL Server], logins
- logins [SQL Server], creating
- creating logins with Management Studio
- Create login [SQL Server]
- SQL Server logins
ms.assetid: fb163e47-1546-4682-abaa-8c9494e9ddc7
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: e476880103a69ae016c6720f36e26ef884db6f5d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697756"
---
# <a name="create-a-login"></a><span data-ttu-id="debd9-102">建立登入</span><span class="sxs-lookup"><span data-stu-id="debd9-102">Create a Login</span></span>
  <span data-ttu-id="debd9-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中建立登入。</span><span class="sxs-lookup"><span data-stu-id="debd9-103">This topic describes how to create a login in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="debd9-104">登入是連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]執行個體的人員或程序的識別。</span><span class="sxs-lookup"><span data-stu-id="debd9-104">A login is the identity of the person or process that is connecting to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="debd9-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="debd9-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="debd9-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="debd9-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="debd9-107">背景</span><span class="sxs-lookup"><span data-stu-id="debd9-107">Background</span></span>](#Background)  
  
     [<span data-ttu-id="debd9-108">安全性</span><span class="sxs-lookup"><span data-stu-id="debd9-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="debd9-109">**若要使用下列項目建立登入：**</span><span class="sxs-lookup"><span data-stu-id="debd9-109">**To create a login, using:**</span></span>  
  
     [<span data-ttu-id="debd9-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="debd9-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="debd9-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="debd9-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="debd9-112">**後續操作：**  [建立登入之後所採取的步驟](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="debd9-112">**Follow Up:**  [Steps to take after you create a login](#FollowUp)</span></span>  
  
##  <a name="background"></a><a name="Background"></a> <span data-ttu-id="debd9-113">背景</span><span class="sxs-lookup"><span data-stu-id="debd9-113">Background</span></span>  
 <span data-ttu-id="debd9-114">登入是安全性主體或可由安全系統驗證的實體。</span><span class="sxs-lookup"><span data-stu-id="debd9-114">A login is a security principal, or an entity that can be authenticated by a secure system.</span></span> <span data-ttu-id="debd9-115">使用者需要登入才能連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="debd9-115">Users need a login to connect to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="debd9-116">您可以建立以 Windows 主體為基礎的登入 (例如網域使用者或 Windows 網域群組)，也可以建立不是以 Windows 主體為基礎的登入 (例如 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登入)。</span><span class="sxs-lookup"><span data-stu-id="debd9-116">You can create a login based on a Windows principal (such as a domain user or a Windows domain group) or you can create a login that is not based on a Windows principal (such as an [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="debd9-117">若要使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證，[!INCLUDE[ssDE](../../../includes/ssde-md.md)] 必須使用混合模式驗證。</span><span class="sxs-lookup"><span data-stu-id="debd9-117">To use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] must use mixed mode authentication.</span></span> <span data-ttu-id="debd9-118">如需詳細資訊，請參閱 [選擇驗證模式](../choose-an-authentication-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="debd9-118">For more information, see [Choose an Authentication Mode](../choose-an-authentication-mode.md).</span></span>  
  
 <span data-ttu-id="debd9-119">登入做為安全性主體時，可以將權限授與登入。</span><span class="sxs-lookup"><span data-stu-id="debd9-119">As a security principal, permissions can be granted to logins.</span></span> <span data-ttu-id="debd9-120">登入的範圍是整個 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="debd9-120">The scope of a login is the whole [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span> <span data-ttu-id="debd9-121">若要連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]執行個體上的特定資料庫，則登入必須對應到資料庫使用者。</span><span class="sxs-lookup"><span data-stu-id="debd9-121">To connect to a specific database on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], a login must be mapped to a database user.</span></span> <span data-ttu-id="debd9-122">資料庫內的權限是對資料庫使用者授與或拒絕，而不是登入。</span><span class="sxs-lookup"><span data-stu-id="debd9-122">Permissions inside the database are granted and denied to the database user, not the login.</span></span> <span data-ttu-id="debd9-123">範圍包含整個 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的權限 (例如 `CREATE ENDPOINT` 權限) 可以授與登入。</span><span class="sxs-lookup"><span data-stu-id="debd9-123">Permissions that have the scope of the whole instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (for example, the `CREATE ENDPOINT` permission) can be granted to a login.</span></span>  
  
##  <a name="security"></a><a name="Security"></a> <span data-ttu-id="debd9-124">Security</span><span class="sxs-lookup"><span data-stu-id="debd9-124">Security</span></span>  
  
### <a name="permissions"></a><span data-ttu-id="debd9-125">權限</span><span class="sxs-lookup"><span data-stu-id="debd9-125">Permissions</span></span>  
 <span data-ttu-id="debd9-126">需要伺服器的 `ALTER ANY LOGIN` 或 `ALTER LOGIN` 權限。</span><span class="sxs-lookup"><span data-stu-id="debd9-126">Requires `ALTER ANY LOGIN` or `ALTER LOGIN` permission on the server.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="debd9-127">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="debd9-127">Using SQL Server Management Studio</span></span>  
  
##### <a name="to-create-a-sql-server-login"></a><span data-ttu-id="debd9-128">若要建立 SQL Server 登入</span><span class="sxs-lookup"><span data-stu-id="debd9-128">To create a SQL Server login</span></span>  
  
1.  <span data-ttu-id="debd9-129">在 [物件總管] 中，展開要建立新登入之伺服器執行個體的資料夾。</span><span class="sxs-lookup"><span data-stu-id="debd9-129">In Object Explorer, expand the folder of the server instance in which you want to create the new login.</span></span>  
  
2.  <span data-ttu-id="debd9-130">以滑鼠右鍵按一下 [安全性] 資料夾，指向 [新增]，然後選取 [登入...]。</span><span class="sxs-lookup"><span data-stu-id="debd9-130">Right-click the **Security** folder, point to **New**, and select **Login...**.</span></span>  
  
3.  <span data-ttu-id="debd9-131">在 [登入 - 新增] 對話方塊的 [一般] 頁面上，於 [登入名稱] 方塊中輸入使用者的名稱。</span><span class="sxs-lookup"><span data-stu-id="debd9-131">In the **Login - New** dialog box, on the **General** page, enter the name of a user in the **Login name** box.</span></span> <span data-ttu-id="debd9-132">或者，按一下 [搜尋...] 開啟 [選取使用者或群組] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="debd9-132">Alternately, click **Search...** to open the **Select User or Group** dialog box.</span></span>  
  
     <span data-ttu-id="debd9-133">如果您按一下 [搜尋...]：</span><span class="sxs-lookup"><span data-stu-id="debd9-133">If you click **Search...**:</span></span>  
  
    1.  <span data-ttu-id="debd9-134">按一下 [選取此物件類型] 底下的 [物件類型...]，開啟 [物件類型] 對話方塊並選取下列任何一個或所有選項：[內建安全性主體]、[群組] 和 [使用者]。</span><span class="sxs-lookup"><span data-stu-id="debd9-134">Under **Select this object type**, click **Object Types...** to open the **Object Types** dialog box and select any or all of the following: **Built-in security principals**, **Groups**, and **Users**.</span></span> <span data-ttu-id="debd9-135">預設會選取 [內建安全性主體] 和 [使用者]。</span><span class="sxs-lookup"><span data-stu-id="debd9-135">**Built-in security principals** and **Users** are selected by default.</span></span> <span data-ttu-id="debd9-136">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="debd9-136">When finished, click **OK**.</span></span>  
  
    2.  <span data-ttu-id="debd9-137">按一下 [從這個位置] 下的 [位置..] 開啟 [位置] 對話方塊，然後選取其中一個可用的伺服器位置。</span><span class="sxs-lookup"><span data-stu-id="debd9-137">Under **From this location**, click **Locations...** to open the **Locations** dialog box and select one of the available server locations.</span></span> <span data-ttu-id="debd9-138">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="debd9-138">When finished, click **OK**.</span></span>  
  
    3.  <span data-ttu-id="debd9-139">在 [輸入要選取的物件名稱 (範例)] 底下，輸入要尋找的使用者或群組名稱。</span><span class="sxs-lookup"><span data-stu-id="debd9-139">Under **Enter the object name to select (examples)**, enter the user or group name that you want to find.</span></span> <span data-ttu-id="debd9-140">如需詳細資訊，請參閱＜ [選擇使用者、電腦或群組對話方塊](https://technet.microsoft.com/library/cc771712.aspx)＞。</span><span class="sxs-lookup"><span data-stu-id="debd9-140">For more information, see [Select Users, Computers, or Groups Dialog Box](https://technet.microsoft.com/library/cc771712.aspx).</span></span>  
  
    4.  <span data-ttu-id="debd9-141">如需其他進階搜尋選項，請按一下 [進階...]。</span><span class="sxs-lookup"><span data-stu-id="debd9-141">Click **Advanced...** for more advanced search options.</span></span> <span data-ttu-id="debd9-142">如需詳細資訊，請參閱 [選擇使用者、電腦或群組對話方塊 - 進階頁面](https://technet.microsoft.com/library/cc733110.aspx)。</span><span class="sxs-lookup"><span data-stu-id="debd9-142">For more information, see [Select Users, Computers, or Groups Dialog Box - Advanced Page](https://technet.microsoft.com/library/cc733110.aspx).</span></span>  
  
    5.  <span data-ttu-id="debd9-143">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="debd9-143">Click **OK**.</span></span>  
  
4.  <span data-ttu-id="debd9-144">若要建立以 Windows 主體為基礎的登入，請選取 **[Windows 驗證]** 。</span><span class="sxs-lookup"><span data-stu-id="debd9-144">To create a login based on a Windows principal, select **Windows authentication**.</span></span> <span data-ttu-id="debd9-145">這是預設選項。</span><span class="sxs-lookup"><span data-stu-id="debd9-145">This is the default selection.</span></span>  
  
5.  <span data-ttu-id="debd9-146">若要建立儲存在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫上的登入，請選取 **[SQL Server 驗證]** 。</span><span class="sxs-lookup"><span data-stu-id="debd9-146">To create a login that is saved on a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database, select **SQL Server authentication**.</span></span>  
  
    1.  <span data-ttu-id="debd9-147">在 [密碼]  方塊中，輸入新使用者的密碼。</span><span class="sxs-lookup"><span data-stu-id="debd9-147">In the **Password** box, enter a password for the new user.</span></span> <span data-ttu-id="debd9-148">在 [確認密碼]  方塊中再次輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="debd9-148">Enter that password again into the **Confirm Password** box.</span></span>  
  
    2.  <span data-ttu-id="debd9-149">變更現有密碼時，選取 **[指定舊密碼]** ，然後在 **[舊密碼]** 方塊中輸入舊密碼。</span><span class="sxs-lookup"><span data-stu-id="debd9-149">When changing an existing password, select **Specify old password**, and then type the old password in the **Old password** box.</span></span>  
  
    3.  <span data-ttu-id="debd9-150">若要強制執行複雜性和強制執行的密碼原則選項，請選取 **[強制執行密碼原則]** 。</span><span class="sxs-lookup"><span data-stu-id="debd9-150">To enforce password policy options for complexity and enforcement, select **Enforce password policy**.</span></span> <span data-ttu-id="debd9-151">如需詳細資訊，請參閱＜ [Password Policy](../password-policy.md)＞。</span><span class="sxs-lookup"><span data-stu-id="debd9-151">For more information, see [Password Policy](../password-policy.md).</span></span> <span data-ttu-id="debd9-152">這是已選取 **[SQL Server 驗證]** 時的預設選項。</span><span class="sxs-lookup"><span data-stu-id="debd9-152">This is a default option when **SQL Server authentication** is selected.</span></span>  
  
    4.  <span data-ttu-id="debd9-153">若要強制執行逾期的密碼原則選項，請選取 **[強制執行密碼逾期]** 。</span><span class="sxs-lookup"><span data-stu-id="debd9-153">To enforce password policy options for expiration, select **Enforce password expiration**.</span></span> <span data-ttu-id="debd9-154">必須選取 **[強制執行密碼原則]** 才能啟用此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="debd9-154">**Enforce password policy** must be selected to enable this checkbox.</span></span> <span data-ttu-id="debd9-155">這是已選取 **[SQL Server 驗證]** 時的預設選項。</span><span class="sxs-lookup"><span data-stu-id="debd9-155">This is a default option when **SQL Server authentication** is selected.</span></span>  
  
    5.  <span data-ttu-id="debd9-156">若要強制使用者必須在第一次使用登入後建立新的密碼，請選取 **[使用者必須在下次登入時變更密碼]** 。</span><span class="sxs-lookup"><span data-stu-id="debd9-156">To force the user to create a new password after the first time the login is used, select **User must change password at next login**.</span></span> <span data-ttu-id="debd9-157">必須選取 **[強制執行密碼逾期]** 才能啟用此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="debd9-157">**Enforce password expiration** must be selected to enable this checkbox.</span></span> <span data-ttu-id="debd9-158">這是已選取 **[SQL Server 驗證]** 時的預設選項。</span><span class="sxs-lookup"><span data-stu-id="debd9-158">This is a default option when **SQL Server authentication** is selected.</span></span>  
  
6.  <span data-ttu-id="debd9-159">若要將登入與獨立安全性憑證建立關聯，請選取 [已對應到憑證]，然後從清單中選取現有憑證的名稱。</span><span class="sxs-lookup"><span data-stu-id="debd9-159">To associate the login with a stand-alone security certificate, select **Mapped to certificate** and then select the name of an existing certificate from the list.</span></span>  
  
7.  <span data-ttu-id="debd9-160">若要將登入與獨立非對稱金鑰建立關聯，請選取 [已對應到非對稱金鑰]，然後從清單中選取現有金鑰的名稱。</span><span class="sxs-lookup"><span data-stu-id="debd9-160">To associate the login with a stand-alone asymmetric key, select **Mapped to asymmetric key** to, and then select the name of an existing key from the list.</span></span>  
  
8.  <span data-ttu-id="debd9-161">若要將登入與安全性認證建立關聯，請選取 **[對應到認證]** 核取方塊，然後從清單中選取現有認證，或按一下 **[加入]** 建立新的認證。</span><span class="sxs-lookup"><span data-stu-id="debd9-161">To associate the login with a security credential, select the **Mapped to Credential** check box, and then either select an existing credential from the list or click **Add** to create a new credential.</span></span> <span data-ttu-id="debd9-162">若要從登入移除安全性認證的對應，請在 **[已對應的認證]** 中選取認證，然後按一下 **[移除]** 。</span><span class="sxs-lookup"><span data-stu-id="debd9-162">To remove a mapping to a security credential from the login, select the credential from **Mapped Credentials** and click **Remove**.</span></span> <span data-ttu-id="debd9-163">如需一般認證的詳細資訊，請參閱[認證 &#40;Database Engine&#41;](credentials-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="debd9-163">For more information about credentials in general, see [Credentials &#40;Database Engine&#41;](credentials-database-engine.md).</span></span>  
  
9. <span data-ttu-id="debd9-164">從 **[預設資料庫]** 清單中，為登入選取預設的資料庫。</span><span class="sxs-lookup"><span data-stu-id="debd9-164">From the **Default database** list, select a default database for the login.</span></span> <span data-ttu-id="debd9-165">**[Master]** 是此選項的預設值。</span><span class="sxs-lookup"><span data-stu-id="debd9-165">**Master** is the default for this option.</span></span>  
  
10. <span data-ttu-id="debd9-166">從 **[預設語言]** 清單中，為登入選取預設的語言。</span><span class="sxs-lookup"><span data-stu-id="debd9-166">From the **Default language** list, select a default language for the login.</span></span>  
  
11. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="additional-options"></a><span data-ttu-id="debd9-167">其他選項</span><span class="sxs-lookup"><span data-stu-id="debd9-167">Additional Options</span></span>  
 <span data-ttu-id="debd9-168">[登入 - 新增] 對話方塊也在其他四個頁面上提供選項：[伺服器角色]、[使用者對應]、[安全性實體] 和 [狀態]。</span><span class="sxs-lookup"><span data-stu-id="debd9-168">The **Login - New** dialog box also offers options on four additional pages: **Server Roles**, **User Mapping**, **Securables**, and **Status**.</span></span>  
  
### <a name="server-roles"></a><span data-ttu-id="debd9-169">[伺服器角色]</span><span class="sxs-lookup"><span data-stu-id="debd9-169">Server Roles</span></span>  
 <span data-ttu-id="debd9-170">**[伺服器角色]** 頁面列出所有可指派給新登入的可能角色。</span><span class="sxs-lookup"><span data-stu-id="debd9-170">The **Server Roles** page lists all possible roles that can be assigned to the new login.</span></span> <span data-ttu-id="debd9-171">有下列選項可供使用：</span><span class="sxs-lookup"><span data-stu-id="debd9-171">The following options are available:</span></span>  
  
 <span data-ttu-id="debd9-172">[bulkadmin] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="debd9-172">**bulkadmin** check box</span></span>  
 <span data-ttu-id="debd9-173">**bulkadmin** 固定伺服器角色的成員可以執行 BULK INSERT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="debd9-173">Members of the **bulkadmin** fixed server role can run the BULK INSERT statement.</span></span>  
  
 <span data-ttu-id="debd9-174">[dbcreator] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="debd9-174">**dbcreator** check box</span></span>  
 <span data-ttu-id="debd9-175">**dbcreator** 固定伺服器角色的成員可以建立、改變、卸除及還原任何資料庫。</span><span class="sxs-lookup"><span data-stu-id="debd9-175">Members of the **dbcreator** fixed server role can create, alter, drop, and restore any database.</span></span>  
  
 <span data-ttu-id="debd9-176">[diskadmin] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="debd9-176">**diskadmin** check box</span></span>  
 <span data-ttu-id="debd9-177">**diskadmin** 固定伺服器角色的成員可以管理磁碟檔案。</span><span class="sxs-lookup"><span data-stu-id="debd9-177">Members of the **diskadmin** fixed server role can manage disk files.</span></span>  
  
 <span data-ttu-id="debd9-178">[processadmin] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="debd9-178">**processadmin** check box</span></span>  
 <span data-ttu-id="debd9-179">**processadmin** 固定伺服器角色的成員可以結束在 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]執行個體中執行的處理序。</span><span class="sxs-lookup"><span data-stu-id="debd9-179">Members of the **processadmin** fixed server role can terminate processes running in an instance of the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="debd9-180">[public] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="debd9-180">**public** check box</span></span>  
 <span data-ttu-id="debd9-181">所有 SQL Server 使用者、群組和角色預設都屬於 **public** 固定伺服器角色。</span><span class="sxs-lookup"><span data-stu-id="debd9-181">All SQL Server users, groups, and roles belong to the **public** fixed server role by default.</span></span>  
  
 <span data-ttu-id="debd9-182">[securityadmin] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="debd9-182">**securityadmin** check box</span></span>  
 <span data-ttu-id="debd9-183">**securityadmin** 固定伺服器角色的成員可以管理登入及其屬性。</span><span class="sxs-lookup"><span data-stu-id="debd9-183">Members of the **securityadmin** fixed server role manage logins and their properties.</span></span> <span data-ttu-id="debd9-184">他們可以 GRANT、DENY 及 REVOKE 伺服器層級權限。</span><span class="sxs-lookup"><span data-stu-id="debd9-184">They can GRANT, DENY, and REVOKE server-level permissions.</span></span> <span data-ttu-id="debd9-185">他們也可以 GRANT、DENY 和 REVOKE 資料庫層級權限。</span><span class="sxs-lookup"><span data-stu-id="debd9-185">They can also GRANT, DENY, and REVOKE database-level permissions.</span></span> <span data-ttu-id="debd9-186">此外，他們可以重設 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登入的密碼。</span><span class="sxs-lookup"><span data-stu-id="debd9-186">Additionally, they can reset passwords for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] logins.</span></span>  
  
 <span data-ttu-id="debd9-187">[serveradmin] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="debd9-187">**serveradmin** check box</span></span>  
 <span data-ttu-id="debd9-188">**serveradmin** 固定伺服器角色的成員可以變更全伺服器組態選項及關閉伺服器。</span><span class="sxs-lookup"><span data-stu-id="debd9-188">Members of the **serveradmin** fixed server role can change server-wide configuration options and shut down the server.</span></span>  
  
 <span data-ttu-id="debd9-189">[setupadmin] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="debd9-189">**setupadmin** check box</span></span>  
 <span data-ttu-id="debd9-190">**setupadmin** 固定伺服器角色的成員可以加入和移除連結的伺服器，也可以執行一些系統預存程序。</span><span class="sxs-lookup"><span data-stu-id="debd9-190">Members of the **setupadmin** fixed server role can add and remove linked servers, and they can execute some system stored procedures.</span></span>  
  
 <span data-ttu-id="debd9-191">[系統管理員] 核取方塊</span><span class="sxs-lookup"><span data-stu-id="debd9-191">**sysadmin** check box</span></span>  
 <span data-ttu-id="debd9-192">**系統管理員** 固定伺服器角色的成員可以執行 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]中的所有活動。</span><span class="sxs-lookup"><span data-stu-id="debd9-192">Members of the **sysadmin** fixed server role can perform any activity in the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
### <a name="user-mapping"></a><span data-ttu-id="debd9-193">[使用者對應]</span><span class="sxs-lookup"><span data-stu-id="debd9-193">User Mapping</span></span>  
 <span data-ttu-id="debd9-194">**[使用者對應]** 頁面列出所有可能的資料庫和這些資料庫上可套用至此登入的資料庫角色成員資格。</span><span class="sxs-lookup"><span data-stu-id="debd9-194">The **User Mapping** page lists all possible databases and the database role memberships on those databases that can be applied to the login.</span></span> <span data-ttu-id="debd9-195">所選的資料庫決定可供登入使用的角色成員資格。</span><span class="sxs-lookup"><span data-stu-id="debd9-195">The databases selected determine the role memberships that are available for the login.</span></span> <span data-ttu-id="debd9-196">此頁面提供下列選項：</span><span class="sxs-lookup"><span data-stu-id="debd9-196">The following options are available on this page:</span></span>  
  
 <span data-ttu-id="debd9-197">**已對應到此登入的使用者**</span><span class="sxs-lookup"><span data-stu-id="debd9-197">**Users mapped to this login**</span></span>  
 <span data-ttu-id="debd9-198">選取此登入可以存取的資料庫。</span><span class="sxs-lookup"><span data-stu-id="debd9-198">Select the databases that this login can access.</span></span> <span data-ttu-id="debd9-199">選取資料庫時，[資料庫角色成員資格對象: <資料庫名稱>] 窗格會顯示有效的資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="debd9-199">When you select a database, its valid database roles are displayed in the **Database role membership for:** _database_name_ pane.</span></span>  
  
 <span data-ttu-id="debd9-200">**地圖**</span><span class="sxs-lookup"><span data-stu-id="debd9-200">**Map**</span></span>  
 <span data-ttu-id="debd9-201">允許登入存取下列資料庫。</span><span class="sxs-lookup"><span data-stu-id="debd9-201">Allow the login to access the databases listed below.</span></span>  
  
 <span data-ttu-id="debd9-202">**Database**</span><span class="sxs-lookup"><span data-stu-id="debd9-202">**Database**</span></span>  
 <span data-ttu-id="debd9-203">列出伺服器上可用的資料庫。</span><span class="sxs-lookup"><span data-stu-id="debd9-203">Lists the databases available on the server.</span></span>  
  
 <span data-ttu-id="debd9-204">**使用者**</span><span class="sxs-lookup"><span data-stu-id="debd9-204">**User**</span></span>  
 <span data-ttu-id="debd9-205">指定要對應至登入的資料庫使用者。</span><span class="sxs-lookup"><span data-stu-id="debd9-205">Specify a database user to map to the login.</span></span> <span data-ttu-id="debd9-206">依預設，資料庫使用者與登入的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="debd9-206">By default, the database user has the same name as the login.</span></span>  
  
 <span data-ttu-id="debd9-207">**預設結構描述**</span><span class="sxs-lookup"><span data-stu-id="debd9-207">**Default Schema**</span></span>  
 <span data-ttu-id="debd9-208">指定使用者的預設結構描述。</span><span class="sxs-lookup"><span data-stu-id="debd9-208">Specifies the default schema of the user.</span></span> <span data-ttu-id="debd9-209">使用者最初建立時，預設結構描述為 **dbo**。</span><span class="sxs-lookup"><span data-stu-id="debd9-209">When a user is first created, its default schema is **dbo**.</span></span> <span data-ttu-id="debd9-210">可以指定不存在的預設結構描述。</span><span class="sxs-lookup"><span data-stu-id="debd9-210">It is possible to specify a default schema that does not yet exist.</span></span> <span data-ttu-id="debd9-211">您無法為使用者指定對應至 Windows 群組、憑證或非對稱金鑰的預設結構描述。</span><span class="sxs-lookup"><span data-stu-id="debd9-211">You cannot specify a default schema for a user that is mapped to a Windows group, a certificate, or an asymmetric key.</span></span>  
  
 <span data-ttu-id="debd9-212">**已啟用 <資料庫名稱> 的來賓帳戶**</span><span class="sxs-lookup"><span data-stu-id="debd9-212">**Guest account enabled for:**  _database_name_</span></span>  
 <span data-ttu-id="debd9-213">唯讀屬性，表示選取的資料庫上是否啟用 Guest 帳戶。</span><span class="sxs-lookup"><span data-stu-id="debd9-213">Read-only attribute indicating whether the Guest account is enabled on the selected database.</span></span> <span data-ttu-id="debd9-214">使用 Guest 帳戶之 **[登入屬性]** 對話方塊的 **[狀態]** 頁面，啟用或停用 Guest 帳戶。</span><span class="sxs-lookup"><span data-stu-id="debd9-214">Use the **Status** page of the **Login Properties** dialog box of the Guest account to enable or disable the Guest account.</span></span>  
  
 <span data-ttu-id="debd9-215">**資料庫角色成員資格對象: <資料庫名稱>** </span><span class="sxs-lookup"><span data-stu-id="debd9-215">**Database role membership for:**  _database_name_</span></span>  
 <span data-ttu-id="debd9-216">在指定的資料庫中選取使用者的角色。</span><span class="sxs-lookup"><span data-stu-id="debd9-216">Select the roles for the user in the specified database.</span></span> <span data-ttu-id="debd9-217">在每一個資料庫中，所有使用者都是 **public** 角色的成員，且無法移除。</span><span class="sxs-lookup"><span data-stu-id="debd9-217">All users are members of the **public** role in every database and cannot be removed.</span></span> <span data-ttu-id="debd9-218">如需資料庫角色的詳細資訊，請參閱 [資料庫層級角色](database-level-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="debd9-218">For more information about database roles, see [Database-Level Roles](database-level-roles.md).</span></span>  
  
### <a name="securables"></a><span data-ttu-id="debd9-219">安全性實體</span><span class="sxs-lookup"><span data-stu-id="debd9-219">Securables</span></span>  
 <span data-ttu-id="debd9-220">**[安全性實體]** 頁面列出所有可能的安全性實體以及可授與登入的安全性實體權限。</span><span class="sxs-lookup"><span data-stu-id="debd9-220">The **Securables** page lists all possible securables and the permissions on those securables that can be granted to the login.</span></span> <span data-ttu-id="debd9-221">此頁面提供下列選項：</span><span class="sxs-lookup"><span data-stu-id="debd9-221">The following options are available on this page:</span></span>  
  
 <span data-ttu-id="debd9-222">**上方格**</span><span class="sxs-lookup"><span data-stu-id="debd9-222">**Upper Grid**</span></span>  
 <span data-ttu-id="debd9-223">包含一個或多個可以設定權限的項目。</span><span class="sxs-lookup"><span data-stu-id="debd9-223">Contains one or more items for which permissions can be set.</span></span> <span data-ttu-id="debd9-224">顯示在上方格中的資料行會隨著主體或安全性實體而有所不同。</span><span class="sxs-lookup"><span data-stu-id="debd9-224">The columns that are displayed in the upper grid vary depending on the principal or securable.</span></span>  
  
 <span data-ttu-id="debd9-225">若要在上方格中加入項目：</span><span class="sxs-lookup"><span data-stu-id="debd9-225">To add items to the upper grid:</span></span>  
  
1.  <span data-ttu-id="debd9-226">按一下 **[搜尋]** 。</span><span class="sxs-lookup"><span data-stu-id="debd9-226">Click **Search**.</span></span>  
  
2.  <span data-ttu-id="debd9-227">在 [**加入物件**] 對話方塊中，選取下列其中一個選項： [**特定物件 ...**]、 **[這些類型的所有物件**...] 或 **[伺服器**_server_name_]。</span><span class="sxs-lookup"><span data-stu-id="debd9-227">In the **Add Objects** dialog box, select one of the following options: **Specific objects...**, **All objects of the types...**, or **The server**_server_name_.</span></span> [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  <span data-ttu-id="debd9-228">選取**伺服器**_server_name_會以所有伺服器的安全物件自動填滿上方格。</span><span class="sxs-lookup"><span data-stu-id="debd9-228">Selecting **The server**_server_name_ automatically fills the upper grid with all of that servers' securable objects.</span></span>  
  
3.  <span data-ttu-id="debd9-229">如果您選取 [特定物件...]：</span><span class="sxs-lookup"><span data-stu-id="debd9-229">If you select **Specific objects...**:</span></span>  
  
    1.  <span data-ttu-id="debd9-230">在 [選取物件] 對話方塊中，按一下 [選取下列物件類型] 下的 [物件類型...]。</span><span class="sxs-lookup"><span data-stu-id="debd9-230">In the **Select Objects** dialog box, under **Select these object types**, click **Object Types...**.</span></span>  
  
    2.  <span data-ttu-id="debd9-231">在 [選取物件類型] 對話方塊中，選取下列任何一個或所有物件類型：[端點]、[登入]、[伺服器]、[可用性群組] 和 [伺服器角色]。</span><span class="sxs-lookup"><span data-stu-id="debd9-231">In the **Select Object Types** dialog box, select any or all of the following object types: **Endpoints**, **Logins**, **Servers**, **Availability Groups**, and **Server roles**.</span></span> [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
    3.  <span data-ttu-id="debd9-232">按一下 [輸入要選取的物件名稱 (範例)] 下的 [瀏覽...]。</span><span class="sxs-lookup"><span data-stu-id="debd9-232">Under **Enter the object names to select (examples)**, click **Browse...**.</span></span>  
  
    4.  <span data-ttu-id="debd9-233">在 **[瀏覽物件]** 對話方塊中，選取您在 **[選取物件類型]** 對話方塊中所選物件類型的任何一項，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="debd9-233">In the **Browse for Objects** dialog box, select any of the available objects of the type that you selected in the **Select Object Types** dialog box, and then click **OK**.</span></span>  
  
    5.  <span data-ttu-id="debd9-234">在 **[選取物件]** 對話方塊中，按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="debd9-234">In the **Select Objects** dialog box, click **OK**.</span></span>  
  
4.  <span data-ttu-id="debd9-235">如果您選取 [下列類型的所有物件...]，請在 [選取物件類型] 對話方塊中，選取下列任何一個或所有物件類型：[端點]、[登入]、[伺服器]、[可用性群組] 和 [伺服器角色]。</span><span class="sxs-lookup"><span data-stu-id="debd9-235">If you select **All objects of the types...**, in the **Select Object Types** dialog box, select any or all of the following object types: **Endpoints**, **Logins**, **Servers**, **Availability Groups**, and **Server roles**.</span></span> [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 <span data-ttu-id="debd9-236">**名稱**</span><span class="sxs-lookup"><span data-stu-id="debd9-236">**Name**</span></span>  
 <span data-ttu-id="debd9-237">加入此方格的每一個主體或安全性實體名稱。</span><span class="sxs-lookup"><span data-stu-id="debd9-237">The name of each principal or securable that is added to the grid.</span></span>  
  
 <span data-ttu-id="debd9-238">**型別**</span><span class="sxs-lookup"><span data-stu-id="debd9-238">**Type**</span></span>  
 <span data-ttu-id="debd9-239">描述每個項目的類型。</span><span class="sxs-lookup"><span data-stu-id="debd9-239">Describes the type of each item.</span></span>  
  
 <span data-ttu-id="debd9-240">**明確索引標籤**</span><span class="sxs-lookup"><span data-stu-id="debd9-240">**Explicit Tab**</span></span>  
 <span data-ttu-id="debd9-241">列出上方格中選取之安全性實體的可能權限。</span><span class="sxs-lookup"><span data-stu-id="debd9-241">Lists the possible permissions for the securable that are selected in the upper grid.</span></span> <span data-ttu-id="debd9-242">並非所有選項都適用於所有明確權限。</span><span class="sxs-lookup"><span data-stu-id="debd9-242">Not all options are available for all explicit permissions.</span></span>  
  
 <span data-ttu-id="debd9-243">**權限**</span><span class="sxs-lookup"><span data-stu-id="debd9-243">**Permissions**</span></span>  
 <span data-ttu-id="debd9-244">權限的名稱。</span><span class="sxs-lookup"><span data-stu-id="debd9-244">The name of the permission.</span></span>  
  
 <span data-ttu-id="debd9-245">**授與者**</span><span class="sxs-lookup"><span data-stu-id="debd9-245">**Grantor**</span></span>  
 <span data-ttu-id="debd9-246">授與權限的主體。</span><span class="sxs-lookup"><span data-stu-id="debd9-246">The principal that granted the permission.</span></span>  
  
 <span data-ttu-id="debd9-247">**授與**</span><span class="sxs-lookup"><span data-stu-id="debd9-247">**Grant**</span></span>  
 <span data-ttu-id="debd9-248">選取此選項即可授與此權限給登入。</span><span class="sxs-lookup"><span data-stu-id="debd9-248">Select to grant this permission to the login.</span></span> <span data-ttu-id="debd9-249">清除此選項即可撤銷這個權限。</span><span class="sxs-lookup"><span data-stu-id="debd9-249">Clear to revoke this permission.</span></span>  
  
 <span data-ttu-id="debd9-250">**使用授與**</span><span class="sxs-lookup"><span data-stu-id="debd9-250">**With Grant**</span></span>  
 <span data-ttu-id="debd9-251">反映出所列權限之 WITH GRANT 選項的狀態。</span><span class="sxs-lookup"><span data-stu-id="debd9-251">Reflects the state of the WITH GRANT option for the listed permission.</span></span> <span data-ttu-id="debd9-252">這個方塊是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="debd9-252">This box is read-only.</span></span> <span data-ttu-id="debd9-253">若要套用此權限，請使用 [GRANT](/sql/t-sql/statements/grant-transact-sql) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="debd9-253">To apply this permission, use the [GRANT](/sql/t-sql/statements/grant-transact-sql) statement.</span></span>  
  
 <span data-ttu-id="debd9-254">**拒絕**</span><span class="sxs-lookup"><span data-stu-id="debd9-254">**Deny**</span></span>  
 <span data-ttu-id="debd9-255">選取此選項即可拒絕授與此權限給登入。</span><span class="sxs-lookup"><span data-stu-id="debd9-255">Select to deny this permission to the login.</span></span> <span data-ttu-id="debd9-256">清除此選項即可撤銷這個權限。</span><span class="sxs-lookup"><span data-stu-id="debd9-256">Clear to revoke this permission.</span></span>  
  
### <a name="status"></a><span data-ttu-id="debd9-257">狀態</span><span class="sxs-lookup"><span data-stu-id="debd9-257">Status</span></span>  
 <span data-ttu-id="debd9-258">**[狀態]** 頁面列出可在所選取之 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登入上設定的一些驗證和授權選項。</span><span class="sxs-lookup"><span data-stu-id="debd9-258">The **Status** page lists some of the authentication and authorization options that can be configured on the selected [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login.</span></span>  
  
 <span data-ttu-id="debd9-259">此頁面提供下列選項：</span><span class="sxs-lookup"><span data-stu-id="debd9-259">The following options are available on this page:</span></span>  
  
 <span data-ttu-id="debd9-260">**連接到 Database Engine 的權限**</span><span class="sxs-lookup"><span data-stu-id="debd9-260">**Permission to connect to database engine**</span></span>  
 <span data-ttu-id="debd9-261">使用這個設定時，應該將選取的登入視為可對其授與或拒絕安全性實體權限的主體。</span><span class="sxs-lookup"><span data-stu-id="debd9-261">When you work with this setting, you should think of the selected login as a principal that can be granted or denied permission on a securable.</span></span>  
  
 <span data-ttu-id="debd9-262">選取 **[授與]** 可為登入授與 CONNECT SQL 權限。</span><span class="sxs-lookup"><span data-stu-id="debd9-262">Select **Grant** to grant CONNECT SQL permission to the login.</span></span> <span data-ttu-id="debd9-263">選取 **[拒絕]** 則可以拒絕授與登入 CONNECT SQL 權限。</span><span class="sxs-lookup"><span data-stu-id="debd9-263">Select **Deny** to deny CONNECT SQL to the login.</span></span>  
  
 <span data-ttu-id="debd9-264">**登入**</span><span class="sxs-lookup"><span data-stu-id="debd9-264">**Login**</span></span>  
 <span data-ttu-id="debd9-265">使用這個設定時，應該將選取的登入視為資料表中的記錄。</span><span class="sxs-lookup"><span data-stu-id="debd9-265">When you work with this setting, you should think of the selected login as a record in a table.</span></span> <span data-ttu-id="debd9-266">對此處所列的值所做的變更會套用至記錄。</span><span class="sxs-lookup"><span data-stu-id="debd9-266">Changes to the values listed here will be applied to the record.</span></span>  
  
 <span data-ttu-id="debd9-267">已經停用的登入會繼續以記錄形式存在。</span><span class="sxs-lookup"><span data-stu-id="debd9-267">A login that has been disabled continues to exist as a record.</span></span> <span data-ttu-id="debd9-268">但是如果登入嘗試連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]，就無法對其進行驗證。</span><span class="sxs-lookup"><span data-stu-id="debd9-268">But if it tries to connect to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the login will not be authenticated.</span></span>  
  
 <span data-ttu-id="debd9-269">選取此選項可啟用或停用此登入。</span><span class="sxs-lookup"><span data-stu-id="debd9-269">Select this option to enable or disable this login.</span></span> <span data-ttu-id="debd9-270">此選項會搭配 ENABLE 或 DISABLE 選項來使用 ALTER LOGIN 陳述式。</span><span class="sxs-lookup"><span data-stu-id="debd9-270">This option uses the ALTER LOGIN statement with the either ENABLE or DISABLE option.</span></span>  
  
 <span data-ttu-id="debd9-271">**SQL Server 驗證**</span><span class="sxs-lookup"><span data-stu-id="debd9-271">**SQL Server Authentication**</span></span>  
 <span data-ttu-id="debd9-272">只有在選取的登入使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證進行連接，而且登入已經鎖定時，[登入已經鎖定] 核取方塊才可使用。此設定是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="debd9-272">The check box **Login is locked out** is only available if the selected login connects using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication and the login has been locked out. This setting is read-only.</span></span> <span data-ttu-id="debd9-273">若要解除鎖定已經鎖定的登入，請搭配 UNLOCK 選項執行 ALTER LOGIN。</span><span class="sxs-lookup"><span data-stu-id="debd9-273">To unlock a login that is locked out, execute ALTER LOGIN with the UNLOCK option.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="debd9-274">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="debd9-274">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-login-using-windows-authentication"></a><span data-ttu-id="debd9-275">若要建立使用 Windows 驗證的登入</span><span class="sxs-lookup"><span data-stu-id="debd9-275">To create a login using Windows Authentication</span></span>  
  
1.  <span data-ttu-id="debd9-276">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="debd9-276">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="debd9-277">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="debd9-277">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="debd9-278">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="debd9-278">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Create a login for SQL Server by specifying a server name and a Windows domain account name.  
  
    CREATE LOGIN [<domainName>\<loginName>] FROM WINDOWS;  
    GO  
  
    ```  
  
#### <a name="to-create-a-login-using-sql-server-authentication"></a><span data-ttu-id="debd9-279">若要建立使用 SQL Server 驗證的登入</span><span class="sxs-lookup"><span data-stu-id="debd9-279">To create a login using SQL Server Authentication</span></span>  
  
1.  <span data-ttu-id="debd9-280">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="debd9-280">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="debd9-281">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="debd9-281">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="debd9-282">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="debd9-282">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Creates the user "shcooper" for SQL Server using the security credential "RestrictedFaculty"   
    -- The user login starts with the password "Baz1nga," but that password must be changed after the first login.  
  
    CREATE LOGIN shcooper   
       WITH PASSWORD = 'Baz1nga' MUST_CHANGE,  
       CREDENTIAL = RestrictedFaculty;  
    GO  
  
    ```  
  
 <span data-ttu-id="debd9-283">如需詳細資訊，請參閱 [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="debd9-283">For more information, see [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql).</span></span>  
  
##  <a name="follow-up-steps-to-take-after-you-create-a-login"></a><a name="FollowUp"></a> <span data-ttu-id="debd9-284">後續操作：建立登入之後採取的步驟</span><span class="sxs-lookup"><span data-stu-id="debd9-284">Follow Up: Steps to take after you create a login</span></span>  
 <span data-ttu-id="debd9-285">建立登入之後，登入就可以連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]，但是不一定有足夠的權限可以執行任何實際工作。</span><span class="sxs-lookup"><span data-stu-id="debd9-285">After creating a login, the login can connect to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], but does not necessarily have sufficient permission to perform any useful work.</span></span> <span data-ttu-id="debd9-286">下列清單提供常用登入動作的連結。</span><span class="sxs-lookup"><span data-stu-id="debd9-286">The following list provides links to common login actions.</span></span>  
  
-   <span data-ttu-id="debd9-287">若要讓登入加入角色，請參閱 [加入角色](join-a-role.md)。</span><span class="sxs-lookup"><span data-stu-id="debd9-287">To have the login join a role, see [Join a Role](join-a-role.md).</span></span>  
  
-   <span data-ttu-id="debd9-288">若要授權登入使用資料庫，請參閱 [建立資料庫使用者](../authentication-access/create-a-database-user.md)。</span><span class="sxs-lookup"><span data-stu-id="debd9-288">To authorize a login to use a database, see [Create a Database User](../authentication-access/create-a-database-user.md).</span></span>  
  
-   <span data-ttu-id="debd9-289">若要將權限授與登入，請參閱 [為主體授與權限](grant-a-permission-to-a-principal.md)。</span><span class="sxs-lookup"><span data-stu-id="debd9-289">To grant a permission to a login, see [Grant a Permission to a Principal](grant-a-permission-to-a-principal.md).</span></span>  
  
  
