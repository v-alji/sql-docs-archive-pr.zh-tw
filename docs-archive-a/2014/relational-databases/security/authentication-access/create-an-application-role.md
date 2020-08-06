---
title: 建立應用程式角色 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.approle.general.f1
helpviewer_keywords:
- application roles [SQL Server], creating
ms.assetid: 6b8da1f5-3d8e-4f88-b111-b915788b06f1
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 51272dad57558cdb771f9b98a2f5e5b3da7609cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598784"
---
# <a name="create-an-application-role"></a><span data-ttu-id="5e8ca-102">建立應用程式角色</span><span class="sxs-lookup"><span data-stu-id="5e8ca-102">Create an Application Role</span></span>
  <span data-ttu-id="5e8ca-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中建立應用程式角色。</span><span class="sxs-lookup"><span data-stu-id="5e8ca-103">This topic describes how to create an application role in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="5e8ca-104">應用程式角色限制使用者必須經由特定應用程式存取資料庫。</span><span class="sxs-lookup"><span data-stu-id="5e8ca-104">Application roles restrict user access to a database except through specific applications.</span></span> <span data-ttu-id="5e8ca-105">應用程式角色沒有使用者，所以選取 **[應用程式角色]** 時，不會顯示 **[角色成員]** 。</span><span class="sxs-lookup"><span data-stu-id="5e8ca-105">Application roles have no users, so the **Role Members** list is not displayed when **Application role** is selected.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5e8ca-106">設定應用程式角色時會檢查密碼複雜性。</span><span class="sxs-lookup"><span data-stu-id="5e8ca-106">Password complexity is checked when application role passwords are set.</span></span> <span data-ttu-id="5e8ca-107">叫用應用程式角色的應用程式必須儲存其密碼。</span><span class="sxs-lookup"><span data-stu-id="5e8ca-107">Applications that invoke application roles must store their passwords.</span></span> <span data-ttu-id="5e8ca-108">應用程式角色密碼應該一律以加密方式儲存。</span><span class="sxs-lookup"><span data-stu-id="5e8ca-108">Application role passwords should always be stored encrypted.</span></span>  
  
 <span data-ttu-id="5e8ca-109">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="5e8ca-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="5e8ca-110">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="5e8ca-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="5e8ca-111">安全性</span><span class="sxs-lookup"><span data-stu-id="5e8ca-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="5e8ca-112">**若要使用下列項目建立應用程式角色：**</span><span class="sxs-lookup"><span data-stu-id="5e8ca-112">**To create an application role, using:**</span></span>  
  
     [<span data-ttu-id="5e8ca-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5e8ca-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="5e8ca-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5e8ca-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5e8ca-115">開始之前</span><span class="sxs-lookup"><span data-stu-id="5e8ca-115">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5e8ca-116">Security</span><span class="sxs-lookup"><span data-stu-id="5e8ca-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="5e8ca-117">權限</span><span class="sxs-lookup"><span data-stu-id="5e8ca-117">Permissions</span></span>  
 <span data-ttu-id="5e8ca-118">需要資料庫的 ALTER ANY APPLICATION ROLE 權限。</span><span class="sxs-lookup"><span data-stu-id="5e8ca-118">Requires ALTER ANY APPLICATION ROLE permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="5e8ca-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5e8ca-119">Using SQL Server Management Studio</span></span>  
  
##### <a name="to-create-an-application-role"></a><span data-ttu-id="5e8ca-120">若要建立應用程式角色</span><span class="sxs-lookup"><span data-stu-id="5e8ca-120">To create an application role</span></span>  
  
1.  <span data-ttu-id="5e8ca-121">在 [物件總管] 中，展開您要建立應用程式角色的資料庫。</span><span class="sxs-lookup"><span data-stu-id="5e8ca-121">In Object Explorer, expand the database where you want to create an application role.</span></span>  
  
2.  <span data-ttu-id="5e8ca-122">展開 **[安全性]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="5e8ca-122">Expand the **Security** folder.</span></span>  
  
3.  <span data-ttu-id="5e8ca-123">展開 **[角色]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="5e8ca-123">Expand the **Roles** folder.</span></span>  
  
4.  <span data-ttu-id="5e8ca-124">以滑鼠右鍵按一下 [應用程式角色] 資料夾，然後選取 [新增應用程式角色]。</span><span class="sxs-lookup"><span data-stu-id="5e8ca-124">Right-click the **Application Roles** folder and select **New Application Role...**.</span></span>  
  
5.  <span data-ttu-id="5e8ca-125">在 [應用程式角色 - 新增] 對話方塊，於 [一般] 頁面上的 [角色名稱] 方塊中輸入新應用程式角色的名稱。</span><span class="sxs-lookup"><span data-stu-id="5e8ca-125">In the **Application Role - New** dialog box, on the **General Page**, enter the new name of the new application role in the **Role name** box.</span></span>  
  
6.  <span data-ttu-id="5e8ca-126">在 **[預設結構描述]** 方塊中，透過輸入物件名稱，指定擁有此角色建立的物件之結構描述。</span><span class="sxs-lookup"><span data-stu-id="5e8ca-126">In the **Default Schema** box, specify the schema that will own objects created by this role by entering the object names.</span></span> <span data-ttu-id="5e8ca-127">或者，按一下省略符號 **(...)** ，開啟 [尋找結構描述] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="5e8ca-127">Alternately, click the ellipsis **(...)** to open the **Locate Schema** dialog box.</span></span>  
  
7.  <span data-ttu-id="5e8ca-128">在 **[密碼]** 方塊中，輸入新角色的密碼。</span><span class="sxs-lookup"><span data-stu-id="5e8ca-128">In the **Password** box, enter a password for the new role.</span></span> <span data-ttu-id="5e8ca-129">在 [確認密碼]  方塊中再次輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="5e8ca-129">Enter that password again into the **Confirm Password** box.</span></span>  
  
8.  <span data-ttu-id="5e8ca-130">在 **[此角色擁有的結構描述]** 底下，選取或檢視此角色將擁有的結構描述。</span><span class="sxs-lookup"><span data-stu-id="5e8ca-130">Under **Schemas owned by this role**, select or view schemas that will be owned by this role.</span></span> <span data-ttu-id="5e8ca-131">結構描述僅能由一個結構描述或角色擁有。</span><span class="sxs-lookup"><span data-stu-id="5e8ca-131">A schema can be owned by only one schema or role.</span></span>  
  
9. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="additional-options"></a><span data-ttu-id="5e8ca-132">其他選項</span><span class="sxs-lookup"><span data-stu-id="5e8ca-132">Additional Options</span></span>  
 <span data-ttu-id="5e8ca-133">[應用程式角色 - 新增] 對話方塊也在其他兩個頁面上提供選項：[安全性實體] 和 [擴充屬性]。</span><span class="sxs-lookup"><span data-stu-id="5e8ca-133">The **Application Role - New** dialog box also offers options on two additional pages: **Securables** and **Extended Properties**.</span></span>  
  
-   <span data-ttu-id="5e8ca-134">**[安全性實體]** 頁面列出所有可能的安全性實體以及可授與登入的安全性實體權限。</span><span class="sxs-lookup"><span data-stu-id="5e8ca-134">The **Securables** page lists all possible securables and the permissions on those securables that can be granted to the login.</span></span>  
  
-   <span data-ttu-id="5e8ca-135">**[擴充屬性]** 頁面讓您能夠將自訂屬性加入至資料庫使用者。</span><span class="sxs-lookup"><span data-stu-id="5e8ca-135">The **Extended properties** page allows you to add custom properties to database users.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="5e8ca-136">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5e8ca-136">Using Transact-SQL</span></span>  
  
#### <a name="to-create-an-application-role"></a><span data-ttu-id="5e8ca-137">若要建立應用程式角色</span><span class="sxs-lookup"><span data-stu-id="5e8ca-137">To create an application role</span></span>  
  
1.  <span data-ttu-id="5e8ca-138">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="5e8ca-138">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="5e8ca-139">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="5e8ca-139">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5e8ca-140">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="5e8ca-140">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Creates an application role called "weekly_receipts" that has the password "987Gbv876sPYY5m23" and "Sales" as its default schema.  
  
    CREATE APPLICATION ROLE weekly_receipts   
        WITH PASSWORD = '987G^bv876sPY)Y5m23'   
        , DEFAULT_SCHEMA = Sales;  
    GO  
    ```  
  
 <span data-ttu-id="5e8ca-141">如需詳細資訊，請參閱 [CREATE APPLICATION ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-application-role-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="5e8ca-141">For more information, see [CREATE APPLICATION ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-application-role-transact-sql).</span></span>  
  
  
