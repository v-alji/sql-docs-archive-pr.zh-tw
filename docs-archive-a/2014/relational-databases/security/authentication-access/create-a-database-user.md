---
title: 建立資料庫使用者 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.DATABASEUSER.GENERAL.F1
- sql12.swb.user.securables.f1
helpviewer_keywords:
- database users, creating
- creating users with Management Studio
- mapping users
- users [SQL Server], creating
- database user additions [SQL Server]
- database users, mapping
- CREATE USER [Management Studio]
- users [SQL Server], adding
- mapping database users
ms.assetid: 782798d3-9552-4514-9f58-e87be4b264e4
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 97fc758c754f5fc8803e988d55147670fc3ff45b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697762"
---
# <a name="create-a-database-user"></a><span data-ttu-id="c1be0-102">建立資料庫使用者</span><span class="sxs-lookup"><span data-stu-id="c1be0-102">Create a Database User</span></span>
  <span data-ttu-id="c1be0-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中建立對應到登入的資料庫使用者。</span><span class="sxs-lookup"><span data-stu-id="c1be0-103">This topic describes how to create a database user mapped to a login in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="c1be0-104">連接到資料庫時，資料庫使用者是登入的識別。</span><span class="sxs-lookup"><span data-stu-id="c1be0-104">The database user is the identity of the login when it is connected to a database.</span></span> <span data-ttu-id="c1be0-105">資料庫使用者可以使用相同的名稱做為登入，但是並非必要。</span><span class="sxs-lookup"><span data-stu-id="c1be0-105">The database user can use the same name as the login, but that is not required.</span></span> <span data-ttu-id="c1be0-106">本主題假設 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中已有登入存在。</span><span class="sxs-lookup"><span data-stu-id="c1be0-106">This topic assumes that a login already exists in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c1be0-107">如需如何建立登入的詳細資訊，請參閱[建立登](create-a-login.md)入。</span><span class="sxs-lookup"><span data-stu-id="c1be0-107">For information about how to create a login, see [Create a Login](create-a-login.md).</span></span>  
  
 <span data-ttu-id="c1be0-108">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="c1be0-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c1be0-109">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="c1be0-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c1be0-110">背景</span><span class="sxs-lookup"><span data-stu-id="c1be0-110">Background</span></span>](#Restrictions)  
  
     [<span data-ttu-id="c1be0-111">安全性</span><span class="sxs-lookup"><span data-stu-id="c1be0-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="c1be0-112">**若要使用下列項目建立資料庫使用者：**</span><span class="sxs-lookup"><span data-stu-id="c1be0-112">**To create a database user, using:**</span></span>  
  
     [<span data-ttu-id="c1be0-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c1be0-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c1be0-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c1be0-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c1be0-115">開始之前</span><span class="sxs-lookup"><span data-stu-id="c1be0-115">Before You Begin</span></span>  
  
###  <a name="background"></a><a name="Restrictions"></a> <span data-ttu-id="c1be0-116">背景</span><span class="sxs-lookup"><span data-stu-id="c1be0-116">Background</span></span>  
 <span data-ttu-id="c1be0-117">使用者是資料庫層級的安全性主體。</span><span class="sxs-lookup"><span data-stu-id="c1be0-117">A user is a database level security principal.</span></span> <span data-ttu-id="c1be0-118">登入必須對應到資料庫使用者，才能連接到資料庫。</span><span class="sxs-lookup"><span data-stu-id="c1be0-118">Logins must be mapped to a database user to connect to a database.</span></span> <span data-ttu-id="c1be0-119">登入可以做為不同的使用者對應到不同的資料庫，但在每一個資料庫中只能對應為一位使用者。</span><span class="sxs-lookup"><span data-stu-id="c1be0-119">A login can be mapped to different databases as different users but can only be mapped as one user in each database.</span></span> <span data-ttu-id="c1be0-120">在部分自主資料庫中，可以建立沒有登入的使用者。</span><span class="sxs-lookup"><span data-stu-id="c1be0-120">In a partially contained database, a user can be created that does not have a login.</span></span> <span data-ttu-id="c1be0-121">如需自主資料庫使用者的詳細資訊，請參閱 [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c1be0-121">For more information about contained database users, see [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql).</span></span> <span data-ttu-id="c1be0-122">如果資料庫中啟用 guest 使用者，則未對應到資料庫使用者的登入就可以用 guest 使用者的身分進入資料庫。</span><span class="sxs-lookup"><span data-stu-id="c1be0-122">If the guest user in a database is enabled, a login that is not mapped to a database user can enter the database as the guest user.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c1be0-123">guest 使用者通常為停用狀態。</span><span class="sxs-lookup"><span data-stu-id="c1be0-123">The guest user is ordinarily disabled.</span></span> <span data-ttu-id="c1be0-124">除非必要，否則不要啟用 guest 使用者。</span><span class="sxs-lookup"><span data-stu-id="c1be0-124">Do not enable the guest user unless it is necessary.</span></span>  
  
 <span data-ttu-id="c1be0-125">使用者做為安全性主體時，可以將權限授與使用者。</span><span class="sxs-lookup"><span data-stu-id="c1be0-125">As a security principal, permissions can be granted to users.</span></span> <span data-ttu-id="c1be0-126">使用者的範圍為資料庫。</span><span class="sxs-lookup"><span data-stu-id="c1be0-126">The scope of a user is the database.</span></span> <span data-ttu-id="c1be0-127">若要連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]執行個體上的特定資料庫，則登入必須對應到資料庫使用者。</span><span class="sxs-lookup"><span data-stu-id="c1be0-127">To connect to a specific database on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], a login must be mapped to a database user.</span></span> <span data-ttu-id="c1be0-128">資料庫內的權限是對資料庫使用者授與或拒絕，而不是登入。</span><span class="sxs-lookup"><span data-stu-id="c1be0-128">Permissions inside the database are granted and denied to the database user, not the login.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c1be0-129">Security</span><span class="sxs-lookup"><span data-stu-id="c1be0-129">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c1be0-130">權限</span><span class="sxs-lookup"><span data-stu-id="c1be0-130">Permissions</span></span>  
 <span data-ttu-id="c1be0-131">需要資料庫的 `ALTER ANY USER` 權限。</span><span class="sxs-lookup"><span data-stu-id="c1be0-131">Requires `ALTER ANY USER` permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c1be0-132">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c1be0-132">Using SQL Server Management Studio</span></span>  
  
##### <a name="to-create-a-database-user"></a><span data-ttu-id="c1be0-133">若要建立資料庫使用者</span><span class="sxs-lookup"><span data-stu-id="c1be0-133">To create a database user</span></span>  
  
1.  <span data-ttu-id="c1be0-134">在 [物件總管] 中，展開 **[資料庫]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c1be0-134">In Object Explorer, expand the **Databases** folder.</span></span>  
  
2.  <span data-ttu-id="c1be0-135">展開要建立新資料庫使用者的資料庫。</span><span class="sxs-lookup"><span data-stu-id="c1be0-135">Expand the database in which to create the new database user.</span></span>  
  
3.  <span data-ttu-id="c1be0-136">以滑鼠右鍵按一下 [安全性] 資料夾，指向 [新增]，然後選取 [使用者...]。</span><span class="sxs-lookup"><span data-stu-id="c1be0-136">Right-click the **Security** folder, point to **New**, and select **User...**.</span></span>  
  
4.  <span data-ttu-id="c1be0-137">在 [**資料庫使用者-新增**] 對話方塊的 [**一般**] 頁面上，從 [**使用者類型**] 清單中選取下列其中一個使用者類型： [**具有登**入的 sql 使用者]、[**沒有登**入的 sql 使用者]、[**對應到憑證**的使用者]、[**對應到非對稱金鑰**的使用者] 或 [ **Windows 使用者**]。</span><span class="sxs-lookup"><span data-stu-id="c1be0-137">In the **Database User - New** dialog box, on the **General** page, select one of the following user types from the **User type** list: **SQL user with login**, **SQL user without login**, **User mapped to a certificate**, **User mapped to an asymmetric key**, or **Windows user**.</span></span>  
  
5.  <span data-ttu-id="c1be0-138">在 **[使用者名稱]** 方塊中，輸入新使用者的名稱。</span><span class="sxs-lookup"><span data-stu-id="c1be0-138">In the **User name** box, enter a name for the new user.</span></span> <span data-ttu-id="c1be0-139">如果您已經從 [使用者類型] 清單中選擇 [Windows 使用者]，也可以按一下省略符號 **(...)** 開啟 [選取使用者或群組] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c1be0-139">If you have chosen **Windows user** from the **User type** list, you can also click the ellipsis **(...)** to open the **Select User or Group** dialog box.</span></span>  
  
6.  <span data-ttu-id="c1be0-140">在 **[登入名稱]** 方塊中，輸入使用者的登入。</span><span class="sxs-lookup"><span data-stu-id="c1be0-140">In the **Login name** box, enter the login for the user.</span></span> <span data-ttu-id="c1be0-141">或者，按一下省略符號 **(...)** ，開啟 [選取登入] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c1be0-141">Alternately, click the ellipsis **(...)** to open the **Select Login** dialog box.</span></span> <span data-ttu-id="c1be0-142">如果您從 **[使用者類型]** 清單中選取 **[有登入的 SQL 使用者]** 或 **[Windows 使用者]** ， **[登入名稱]** 就是可用的。</span><span class="sxs-lookup"><span data-stu-id="c1be0-142">**Login name** is available if you select either **SQL user with login** or **Windows user** from the **User type** list.</span></span>  
  
7.  <span data-ttu-id="c1be0-143">在 **[預設結構描述]** 方塊中，指定擁有此使用者建立的物件之結構描述。</span><span class="sxs-lookup"><span data-stu-id="c1be0-143">In the **Default schema** box, specifies the schema that will own objects created by this user.</span></span> <span data-ttu-id="c1be0-144">或者，按一下省略符號 **(...)** ，開啟 [選取結構描述] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c1be0-144">Alternately, click the ellipsis **(...)** to open the **Select Schema** dialog box.</span></span> <span data-ttu-id="c1be0-145">如果您從 **[使用者類型]** 清單中選取 **[有登入的 SQL 使用者]** , **[沒有登入的 SQL 使用者]** 或 **[Windows 使用者]** ， **[預設結構描述]** 就是可用的。</span><span class="sxs-lookup"><span data-stu-id="c1be0-145">**Default schema** is available if you select either **SQL user with login**, **SQL user without login**, or **Windows user** from the **User type** list.</span></span>  
  
8.  <span data-ttu-id="c1be0-146">在 **[憑證名稱]** 方塊中，輸入要用於資料庫使用者的憑證。</span><span class="sxs-lookup"><span data-stu-id="c1be0-146">In the **Certificate name** box, enter the certificate to be used for the database user.</span></span> <span data-ttu-id="c1be0-147">或者，按一下省略符號 **(...)** ，開啟 [選取憑證] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c1be0-147">Alternately, click the ellipsis **(...)** to open the **Select Certificate** dialog box.</span></span> <span data-ttu-id="c1be0-148">如果您從 **[使用者類型]** 清單中選取 **[對應到憑證的使用者]** ， **[憑證名稱]** 就是可用的。</span><span class="sxs-lookup"><span data-stu-id="c1be0-148">**Certificate name** is available if you select **User mapped to a certificate** from the **User type** list.</span></span>  
  
9. <span data-ttu-id="c1be0-149">在 **[非對稱金鑰名稱]**  方塊中，輸入要用於資料庫使用者的金鑰。</span><span class="sxs-lookup"><span data-stu-id="c1be0-149">In the **Asymmetric key name**  box, enter the key to be used for the database user.</span></span> <span data-ttu-id="c1be0-150">或者，按一下省略符號 **(...)** ，開啟 [選取非對稱金鑰] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c1be0-150">Alternately, click the ellipsis **(...)** to open the **Select Asymmetric Key** dialog box.</span></span> <span data-ttu-id="c1be0-151">如果您從 **[使用者類型]** 清單中選取 **[對應到非對稱金鑰的使用者]** ， **[非對稱金鑰名稱]** 就是可用的。</span><span class="sxs-lookup"><span data-stu-id="c1be0-151">**Asymmetric key name** is available if you select **User mapped to an asymmetric key** from the **User type** list.</span></span>  
  
10. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="additional-options"></a><span data-ttu-id="c1be0-152">其他選項</span><span class="sxs-lookup"><span data-stu-id="c1be0-152">Additional Options</span></span>  
 <span data-ttu-id="c1be0-153">[資料庫使用者 - 新增] 對話方塊也會在其他四個頁面上提供選項：[自有結構描述]、[成員資格]、[安全性實體] 和 [延伸屬性]。</span><span class="sxs-lookup"><span data-stu-id="c1be0-153">The **Database User - New** dialog box also offers options on four additional pages: **Owned Schemas**, **Membership**, **Securables**, and **Extended Properties**.</span></span>  
  
-   <span data-ttu-id="c1be0-154">**[擁有的結構描述]** 頁面列出新資料庫使用者可擁有的所有可能結構描述。</span><span class="sxs-lookup"><span data-stu-id="c1be0-154">The **Owned Schemas** page lists all possible schemas that can be owned by the new database user.</span></span> <span data-ttu-id="c1be0-155">若要在資料庫使用者中加入或移除結構描述，請在 **[這個使用者擁有的結構描述]** 底下選取或清除結構描述旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="c1be0-155">To add schemas to or remove them from a database user, under **Schemas owned by this user**, select or clear the check boxes next to the schemas.</span></span>  
  
-   <span data-ttu-id="c1be0-156">**[成員資格]** 頁面列出新資料庫使用者可擁有的所有可能的資料庫角色成員資格。</span><span class="sxs-lookup"><span data-stu-id="c1be0-156">The **Membership** page lists all possible database membership roles that can be owned by the new database user.</span></span> <span data-ttu-id="c1be0-157">若要在資料庫使用者中加入或移除角色，請在 **[資料庫角色成員資格]** 底下選取或清除角色旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="c1be0-157">To add roles to or remove them from a database user, under **Database role membership**, select or clear the check boxes next to the roles.</span></span>  
  
-   <span data-ttu-id="c1be0-158">**[安全性實體]** 頁面列出所有可能的安全性實體以及可授與登入的安全性實體權限。</span><span class="sxs-lookup"><span data-stu-id="c1be0-158">The **Securables** page lists all possible securables and the permissions on those securables that can be granted to the login.</span></span>  
  
-   <span data-ttu-id="c1be0-159">**[擴充屬性]** 頁面讓您能夠將自訂屬性加入至資料庫使用者。</span><span class="sxs-lookup"><span data-stu-id="c1be0-159">The **Extended properties** page allows you to add custom properties to database users.</span></span> <span data-ttu-id="c1be0-160">此頁面提供下列選項。</span><span class="sxs-lookup"><span data-stu-id="c1be0-160">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="c1be0-161">**Database**</span><span class="sxs-lookup"><span data-stu-id="c1be0-161">**Database**</span></span>  
     <span data-ttu-id="c1be0-162">顯示選取之資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="c1be0-162">Displays the name of the selected database.</span></span> <span data-ttu-id="c1be0-163">此欄位是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="c1be0-163">This field is read-only.</span></span>  
  
     <span data-ttu-id="c1be0-164">**定序**</span><span class="sxs-lookup"><span data-stu-id="c1be0-164">**Collation**</span></span>  
     <span data-ttu-id="c1be0-165">顯示用於所選取資料庫的定序。</span><span class="sxs-lookup"><span data-stu-id="c1be0-165">Displays the collation used for the selected database.</span></span> <span data-ttu-id="c1be0-166">此欄位是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="c1be0-166">This field is read-only.</span></span>  
  
     <span data-ttu-id="c1be0-167">**屬性**</span><span class="sxs-lookup"><span data-stu-id="c1be0-167">**Properties**</span></span>  
     <span data-ttu-id="c1be0-168">檢視或指定物件的擴充屬性。</span><span class="sxs-lookup"><span data-stu-id="c1be0-168">View or specify the extended properties for the object.</span></span> <span data-ttu-id="c1be0-169">每個擴充屬性都包含與物件相關聯的一對名稱/值中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c1be0-169">Each extended property consists of a name/value pair of metadata associated with the object.</span></span>  
  
     <span data-ttu-id="c1be0-170">**省略符號 (...)**</span><span class="sxs-lookup"><span data-stu-id="c1be0-170">**Ellipsis (...)**</span></span>  
     <span data-ttu-id="c1be0-171">按一下 [值] 後面的省略符號 **(...)** ，開啟 [擴充屬性的值] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c1be0-171">Click the ellipsis **(...)** after **Value** to open the **Value for Extended Property** dialog box.</span></span> <span data-ttu-id="c1be0-172">在這個較大的位置輸入或檢視擴充屬性的值。</span><span class="sxs-lookup"><span data-stu-id="c1be0-172">Type or view the value of the extended property in this larger location.</span></span> <span data-ttu-id="c1be0-173">如需詳細資訊，請參閱＜ [擴充屬性的值對話方塊](../../databases/value-for-extended-property-dialog-box.md)＞。</span><span class="sxs-lookup"><span data-stu-id="c1be0-173">For more information, see [Value for Extended Property Dialog Box](../../databases/value-for-extended-property-dialog-box.md).</span></span>  
  
     <span data-ttu-id="c1be0-174">**刪除**</span><span class="sxs-lookup"><span data-stu-id="c1be0-174">**Delete**</span></span>  
     <span data-ttu-id="c1be0-175">移除選取的擴充屬性。</span><span class="sxs-lookup"><span data-stu-id="c1be0-175">Removes the selected extended property.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c1be0-176">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c1be0-176">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-database-user"></a><span data-ttu-id="c1be0-177">若要建立資料庫使用者</span><span class="sxs-lookup"><span data-stu-id="c1be0-177">To create a database user</span></span>  
  
1.  <span data-ttu-id="c1be0-178">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c1be0-178">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c1be0-179">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="c1be0-179">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c1be0-180">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="c1be0-180">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Creates the login AbolrousHazem with password '340$Uuxwp7Mcxo7Khy'.  
    CREATE LOGIN AbolrousHazem   
        WITH PASSWORD = '340$Uuxwp7Mcxo7Khy';  
    GO  
  
    -- Creates a database user for the login created above.  
    CREATE USER AbolrousHazem FOR LOGIN AbolrousHazem;  
    GO  
    ```  
  
 <span data-ttu-id="c1be0-181">如需詳細資訊，請參閱 [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c1be0-181">For more information, see [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1be0-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1be0-182">See Also</span></span>  
 [<span data-ttu-id="c1be0-183">主體 &#40;Database Engine&#41;</span><span class="sxs-lookup"><span data-stu-id="c1be0-183">Principals &#40;Database Engine&#41;</span></span>](principals-database-engine.md)  
  
  
