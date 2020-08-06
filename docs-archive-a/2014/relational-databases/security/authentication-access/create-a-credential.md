---
title: 建立認證 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- credentials [SQL Server], creating
- authentication [SQL Server], credentials
- logins [SQL Server], credentials
ms.assetid: c1e77e91-2a69-40d9-b8b3-97cffc710586
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 23221424699449ac3775b0e805bb02ae0ad233f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697777"
---
# <a name="create-a-credential"></a><span data-ttu-id="69293-102">建立認證</span><span class="sxs-lookup"><span data-stu-id="69293-102">Create a Credential</span></span>
  <span data-ttu-id="69293-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中建立認證。</span><span class="sxs-lookup"><span data-stu-id="69293-103">This topic describes how to create a credential in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="69293-104">認證提供允許 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證使用者擁有 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]以外之識別的方法。</span><span class="sxs-lookup"><span data-stu-id="69293-104">Credentials provide a way to allow [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication users to have an identity outside of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="69293-105">這主要是用來執行具 EXTERNAL_ACCESS 權限集之組件中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="69293-105">This is primarily used to execute code in Assemblies with EXTERNAL_ACCESS permission set.</span></span> <span data-ttu-id="69293-106">認證也可以在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 驗證使用者需要存取網域資源時使用，例如儲存備份的檔案位置。</span><span class="sxs-lookup"><span data-stu-id="69293-106">Credentials can also be used when a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication user needs access to a domain resource, such as a file location to store a backup.</span></span>  
  
 <span data-ttu-id="69293-107">認證可以同時對應至數個 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登入。</span><span class="sxs-lookup"><span data-stu-id="69293-107">A credential can be mapped to several [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] logins at the same time.</span></span> <span data-ttu-id="69293-108">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 登入每次只能對應至一個認證。</span><span class="sxs-lookup"><span data-stu-id="69293-108">A [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login can only be mapped to one credential at a time.</span></span> <span data-ttu-id="69293-109">建立認證之後，請使用 [登入屬性 (一般頁面)] 將登入對應至認證。</span><span class="sxs-lookup"><span data-stu-id="69293-109">After a credential is created, use the **Login Properties (General Page)** to map a login to a credential.</span></span>  
  
 <span data-ttu-id="69293-110">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="69293-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="69293-111">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="69293-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="69293-112">限制事項</span><span class="sxs-lookup"><span data-stu-id="69293-112">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="69293-113">安全性</span><span class="sxs-lookup"><span data-stu-id="69293-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="69293-114">**若要使用下列項目建立認證：**</span><span class="sxs-lookup"><span data-stu-id="69293-114">**To create a credential, using:**</span></span>  
  
     [<span data-ttu-id="69293-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="69293-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="69293-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="69293-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="69293-117">開始之前</span><span class="sxs-lookup"><span data-stu-id="69293-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="69293-118">限制事項</span><span class="sxs-lookup"><span data-stu-id="69293-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="69293-119">如果提供者沒有任何登入對應認證，系統就會使用對應至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務帳戶的認證。</span><span class="sxs-lookup"><span data-stu-id="69293-119">If there is no login mapped credential for the provider, the credential mapped to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service account is used.</span></span>  
  
-   <span data-ttu-id="69293-120">一個登入可以具有多個對應認證，只要這些認證用於不同的提供者即可。</span><span class="sxs-lookup"><span data-stu-id="69293-120">A login can have multiple credentials mapped to it as long as they are used with distinctive providers.</span></span> <span data-ttu-id="69293-121">但是，每個登入的每個提供者必須只有一個對應認證。</span><span class="sxs-lookup"><span data-stu-id="69293-121">There must be only one mapped credential per provider per login.</span></span> <span data-ttu-id="69293-122">相同的認證可對應至其他登入。</span><span class="sxs-lookup"><span data-stu-id="69293-122">The same credential can be mapped to other logins.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="69293-123">Security</span><span class="sxs-lookup"><span data-stu-id="69293-123">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="69293-124">權限</span><span class="sxs-lookup"><span data-stu-id="69293-124">Permissions</span></span>  
 <span data-ttu-id="69293-125">需要 ALTER ANY CREDENTIAL 權限才能建立或修改認證，以及 ALTER ANY LOGIN 權限才能將登入對應至認證。</span><span class="sxs-lookup"><span data-stu-id="69293-125">Requires ALTER ANY CREDENTIAL permission to create or modify a credential and ALTER ANY LOGIN permission to map a login to a credential.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="69293-126">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="69293-126">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-credential"></a><span data-ttu-id="69293-127">若要建立認證</span><span class="sxs-lookup"><span data-stu-id="69293-127">To create a credential</span></span>  
  
1.  <span data-ttu-id="69293-128">在物件總管中，展開 [安全性]  資料夾。</span><span class="sxs-lookup"><span data-stu-id="69293-128">In Object Explorer, expand  the **Security** folder.</span></span>  
  
2.  <span data-ttu-id="69293-129">以滑鼠右鍵按一下 [認證] 資料夾，然後選取 [新增認證]。</span><span class="sxs-lookup"><span data-stu-id="69293-129">Right-click the **Credentials** folder and select **New Credential...**.</span></span>  
  
3.  <span data-ttu-id="69293-130">在 **[新增認證]** 對話方塊的 **[認證名稱]** 方塊中，輸入認證的名稱。</span><span class="sxs-lookup"><span data-stu-id="69293-130">In the **New Credential** dialog box, in the **Credential Name** box, type a name for the credential.</span></span>  
  
4.  <span data-ttu-id="69293-131">在 [識別] 方塊中，輸入用於傳出連線 (離開 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 內容時) 的帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="69293-131">In the **Identity** box, type the name of the account used for outgoing connections (when leaving the context of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]).</span></span> <span data-ttu-id="69293-132">通常，這將是 Windows 使用者帳戶，但識別可以是另一種類型的帳戶。</span><span class="sxs-lookup"><span data-stu-id="69293-132">Typically, this will be a Windows user account, but the identity can be an account of another type.</span></span>  
  
     <span data-ttu-id="69293-133">或者，按一下省略符號 **(...)** 開啟 [選取使用者或群組] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="69293-133">Alternately, click the ellipsis **(...)** to open the **Select User or Group** dialog box.</span></span>  
  
5.  <span data-ttu-id="69293-134">在 **[密碼]** 與 **[確認密碼]** 方塊中，輸入 **[識別]** 方塊中所指定的帳戶密碼。</span><span class="sxs-lookup"><span data-stu-id="69293-134">In the **Password** and **Confirm password** boxes, type the password of the account specified in the **Identity** box.</span></span> <span data-ttu-id="69293-135">如果 **[識別]** 是 Windows 使用者帳戶，則為 Windows 密碼。</span><span class="sxs-lookup"><span data-stu-id="69293-135">If **Identity** is a Windows user account, this is the Windows password.</span></span> <span data-ttu-id="69293-136">如果不需要密碼， **[密碼]** 可以是空白。</span><span class="sxs-lookup"><span data-stu-id="69293-136">The **Password** can be blank, if no password is required.</span></span>  
  
6.  <span data-ttu-id="69293-137">選取 [使用加密提供者]，設定要由可延伸金鑰管理 (EKM) 提供者所驗證的認證。</span><span class="sxs-lookup"><span data-stu-id="69293-137">Select **Use Encryption Provider** to set the credential to be verified by an Extensible Key Management (EKM) Provider.</span></span> <span data-ttu-id="69293-138">如需詳細資訊，請參閱[可延伸金鑰管理 &#40;EKM&#41;](../encryption/extensible-key-management-ekm.md)</span><span class="sxs-lookup"><span data-stu-id="69293-138">For more information, see [Extensible Key Management &#40;EKM&#41;](../encryption/extensible-key-management-ekm.md)</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="69293-139">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="69293-139">Using Transact-SQL</span></span>  
  
###  <a name="to-create-a-credential"></a><a name="Credential"></a><span data-ttu-id="69293-140">建立認證</span><span class="sxs-lookup"><span data-stu-id="69293-140">To create a credential</span></span>  
  
1.  <span data-ttu-id="69293-141">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="69293-141">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="69293-142">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="69293-142">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="69293-143">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="69293-143">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Creates the credential called "AlterEgo.".   
    -- The credential contains the Windows user "Mary5" and a password.  
    CREATE CREDENTIAL AlterEgo WITH IDENTITY = 'Mary5',   
        SECRET = '<EnterStrongPasswordHere>';  
    GO  
    ```  
  
 <span data-ttu-id="69293-144">如需詳細資訊，請參閱 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="69293-144">For more information, see [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql).</span></span>  
  
  
