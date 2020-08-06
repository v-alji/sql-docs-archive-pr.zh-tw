---
title: 建立資料庫結構描述 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.schemas.general.f1
helpviewer_keywords:
- creating schemas with Management Studio
- CREATE SCHEMA [Management Studio]
- database schemas
- schemas [SQL Server], creating
ms.assetid: ed2a5522-f4d2-4111-95a4-d3e1e5081739
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 3ac0c00768db6501c7d786c35758c1a9d75a5a7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697771"
---
# <a name="create-a-database-schema"></a><span data-ttu-id="f574a-102">建立資料庫結構描述</span><span class="sxs-lookup"><span data-stu-id="f574a-102">Create a Database Schema</span></span>
  <span data-ttu-id="f574a-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中建立結構描述。</span><span class="sxs-lookup"><span data-stu-id="f574a-103">This topic describes how to create a schema in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="f574a-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="f574a-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f574a-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="f574a-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f574a-106">限制事項</span><span class="sxs-lookup"><span data-stu-id="f574a-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="f574a-107">安全性</span><span class="sxs-lookup"><span data-stu-id="f574a-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f574a-108">**若要使用下列項目建立結構描述：**</span><span class="sxs-lookup"><span data-stu-id="f574a-108">**To create a schema, using:**</span></span>  
  
     [<span data-ttu-id="f574a-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f574a-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f574a-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f574a-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f574a-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="f574a-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="f574a-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="f574a-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="f574a-113">新結構描述的擁有者是下列資料庫層級主體之一：資料庫使用者、資料庫角色或應用程式角色。</span><span class="sxs-lookup"><span data-stu-id="f574a-113">The new schema is owned by one of the following database-level principals: database user, database role, or application role.</span></span> <span data-ttu-id="f574a-114">在結構描述中建立的物件由結構描述擁有者擁有，其在 **sys.objects** 中具有 NULL **principal_id**。</span><span class="sxs-lookup"><span data-stu-id="f574a-114">Objects created within a schema are owned by the owner of the schema, and have a NULL **principal_id** in **sys.objects**.</span></span> <span data-ttu-id="f574a-115">結構描述包含物件的擁有權可以轉移到任何資料庫層級主體，但結構描述擁有者恆保有結構描述中物件的 CONTROL 權限。</span><span class="sxs-lookup"><span data-stu-id="f574a-115">Ownership of schema-contained objects can be transferred to any database-level principal, but the schema owner always retains CONTROL permission on objects within the schema.</span></span>  
  
-   <span data-ttu-id="f574a-116">建立資料庫物件時，如果您將有效的網域主體 (使用者或群組) 指定為物件擁有者，則會將該網域主體加入至資料庫做為結構描述。</span><span class="sxs-lookup"><span data-stu-id="f574a-116">When creating a database object, if you specify a valid domain principal (user or group) as the object owner, the domain principal will be added to the database as a schema.</span></span> <span data-ttu-id="f574a-117">新的結構描述將由該網域主體所擁有。</span><span class="sxs-lookup"><span data-stu-id="f574a-117">The new schema will be owned by that domain principal.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f574a-118">Security</span><span class="sxs-lookup"><span data-stu-id="f574a-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f574a-119">權限</span><span class="sxs-lookup"><span data-stu-id="f574a-119">Permissions</span></span>  
  
-   <span data-ttu-id="f574a-120">需要資料庫的 CREATE SCHEMA 權限。</span><span class="sxs-lookup"><span data-stu-id="f574a-120">Requires CREATE SCHEMA permission on the database.</span></span>  
  
-   <span data-ttu-id="f574a-121">若要指定其他使用者做為建立之結構描述的擁有者，呼叫者必須具有該使用者的 IMPERSONATE 權限。</span><span class="sxs-lookup"><span data-stu-id="f574a-121">To specify another user as the owner of the schema being created, the caller must have IMPERSONATE permission on that user.</span></span> <span data-ttu-id="f574a-122">如果指定資料庫角色做為擁有者，呼叫端必須具有下列項目之一：角色的成員資格或角色的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="f574a-122">If a database role is specified as the owner, the caller must have one of the following: membership in the role or ALTER permission on the role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f574a-123">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f574a-123">Using SQL Server Management Studio</span></span>  
  
##### <a name="to-create-a-schema"></a><span data-ttu-id="f574a-124">若要建立結構描述</span><span class="sxs-lookup"><span data-stu-id="f574a-124">To create a schema</span></span>  
  
1.  <span data-ttu-id="f574a-125">在 [物件總管] 中，展開 **[資料庫]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="f574a-125">In Object Explorer, expand the **Databases** folder.</span></span>  
  
2.  <span data-ttu-id="f574a-126">展開要建立新資料庫結構描述的資料庫。</span><span class="sxs-lookup"><span data-stu-id="f574a-126">Expand the database in which to create the new database schema.</span></span>  
  
3.  <span data-ttu-id="f574a-127">以滑鼠右鍵按一下 [安全性] 資料夾，指向 [新增]，然後選取 [結構描述]。</span><span class="sxs-lookup"><span data-stu-id="f574a-127">Right-click the **Security** folder, point to **New**, and select **Schema**.</span></span>  
  
4.  <span data-ttu-id="f574a-128">在 [結構描述 - 新增] 對話方塊的 [一般] 頁面上，將新結構描述的名稱輸入 [結構描述名稱] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="f574a-128">In the **Schema - New** dialog box, on the **General** page, enter a name for the new schema in the **Schema name** box.</span></span>  
  
5.  <span data-ttu-id="f574a-129">在 **[結構描述擁有者]** 方塊中，輸入擁有結構描述之資料庫使用者或角色的名稱。</span><span class="sxs-lookup"><span data-stu-id="f574a-129">In the **Schema owner** box, enter the name of a database user or role to own the schema.</span></span> <span data-ttu-id="f574a-130">或者，按一下 **[搜尋]** 開啟 **[搜尋角色和使用者]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f574a-130">Alternately, click **Search** to open the **Search Roles and Users** dialog box.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="additional-options"></a><span data-ttu-id="f574a-131">其他選項</span><span class="sxs-lookup"><span data-stu-id="f574a-131">Additional Options</span></span>  
 <span data-ttu-id="f574a-132">[結構描述 - 新增] 對話方塊也在其他兩個頁面上提供選項：[權限] 和 [延伸屬性]。</span><span class="sxs-lookup"><span data-stu-id="f574a-132">The **Schema- New** dialog box also offers options on two additional pages: **Permissions** and **Extended Properties**.</span></span>  
  
-   <span data-ttu-id="f574a-133">**[權限]** 頁面列出所有可能的安全性實體以及可授與登入的安全性實體權限。</span><span class="sxs-lookup"><span data-stu-id="f574a-133">The **Permissions** page lists all possible securables and the permissions on those securables that can be granted to the login.</span></span>  
  
-   <span data-ttu-id="f574a-134">**[擴充屬性]** 頁面讓您能夠將自訂屬性加入至資料庫使用者。</span><span class="sxs-lookup"><span data-stu-id="f574a-134">The **Extended properties** page allows you to add custom properties to database users.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f574a-135">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f574a-135">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-schema"></a><span data-ttu-id="f574a-136">若要建立結構描述</span><span class="sxs-lookup"><span data-stu-id="f574a-136">To create a schema</span></span>  
  
1.  <span data-ttu-id="f574a-137">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="f574a-137">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f574a-138">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="f574a-138">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f574a-139">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="f574a-139">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Creates the schema Sprockets owned by Annik that contains table NineProngs.   
    -- The statement grants SELECT to Mandar and denies SELECT to Prasanna.  
  
    CREATE SCHEMA Sprockets AUTHORIZATION Annik  
        CREATE TABLE NineProngs (source int, cost int, partnumber int)  
        GRANT SELECT ON SCHEMA::Sprockets TO Mandar  
        DENY SELECT ON SCHEMA::Sprockets TO Prasanna;  
    GO  
    ```  
  
 <span data-ttu-id="f574a-140">如需詳細資訊，請參閱 [CREATE SCHEMA &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-schema-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f574a-140">For more information, see [CREATE SCHEMA &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-schema-transact-sql).</span></span>  
  
  
