---
title: 變更伺服器驗證模式 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- sa account
- authentication [SQL Server], changing modes
- server authentication mode [SQL Server]
- modifying server authentication mode
ms.assetid: 79babcf8-19fd-4495-b8eb-453dc575cac0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8bda31ca7d0c5949173a9a3e5ea656c1757c04f7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707878"
---
# <a name="change-server-authentication-mode"></a><span data-ttu-id="a6d59-102">變更伺服器驗證模式</span><span class="sxs-lookup"><span data-stu-id="a6d59-102">Change Server Authentication Mode</span></span>
  <span data-ttu-id="a6d59-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 變更 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的伺服器驗證模式。</span><span class="sxs-lookup"><span data-stu-id="a6d59-103">This topic describes how to change the server authentication mode in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="a6d59-104">在安裝期間， [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 會設為 **[Windows 驗證模式]** 或 **[SQL Server 及 Windows 驗證模式]** 。</span><span class="sxs-lookup"><span data-stu-id="a6d59-104">During installation, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] is set to either **Windows Authentication mode** or **SQL Server and Windows Authentication mode**.</span></span> <span data-ttu-id="a6d59-105">安裝後，您可以隨時變更驗證模式。</span><span class="sxs-lookup"><span data-stu-id="a6d59-105">After installation, you can change the authentication mode at any time.</span></span>  
  
 <span data-ttu-id="a6d59-106">如果您在安裝期間選取 [Windows 驗證模式]，sa 登入便會停用，且安裝程式會指派密碼。</span><span class="sxs-lookup"><span data-stu-id="a6d59-106">If **Windows Authentication mode** is selected during installation, the sa login is disabled and a password is assigned by setup.</span></span> <span data-ttu-id="a6d59-107">即使稍後將驗證模式改成 [SQL Server 及 Windows 驗證模式]，sa 登入也會保持停用狀態。</span><span class="sxs-lookup"><span data-stu-id="a6d59-107">If you later change authentication mode to **SQL Server and Windows Authentication mode**, the sa login remains disabled.</span></span> <span data-ttu-id="a6d59-108">若要使用 sa 登入，請使用 ALTER LOGIN 陳述式啟用 sa 登入並指派新密碼。</span><span class="sxs-lookup"><span data-stu-id="a6d59-108">To use the sa login, use the ALTER LOGIN statement to enable the sa login and assign a new password.</span></span> <span data-ttu-id="a6d59-109">sa 登入只能使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證連接到伺服器。</span><span class="sxs-lookup"><span data-stu-id="a6d59-109">The sa login can only connect to the server by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="a6d59-110">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="a6d59-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a6d59-111">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="a6d59-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a6d59-112">安全性</span><span class="sxs-lookup"><span data-stu-id="a6d59-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a6d59-113">**若要使用下列項目變更伺服器驗證模式：**</span><span class="sxs-lookup"><span data-stu-id="a6d59-113">**To change server authentication mode, using:**</span></span>  
  
     [<span data-ttu-id="a6d59-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a6d59-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a6d59-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a6d59-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a6d59-116">開始之前</span><span class="sxs-lookup"><span data-stu-id="a6d59-116">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a6d59-117">Security</span><span class="sxs-lookup"><span data-stu-id="a6d59-117">Security</span></span>  
 <span data-ttu-id="a6d59-118">sa 帳戶是已知的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶，而且經常是惡意使用者的攻擊目標。</span><span class="sxs-lookup"><span data-stu-id="a6d59-118">The sa account is a well-known [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account and it is often targeted by malicious users.</span></span> <span data-ttu-id="a6d59-119">除非您的應用程式需要，否則請勿啟用 sa 帳戶。</span><span class="sxs-lookup"><span data-stu-id="a6d59-119">Do not enable the sa account unless your application requires it.</span></span> <span data-ttu-id="a6d59-120">請務必針對 sa 登入使用一個增強式密碼。</span><span class="sxs-lookup"><span data-stu-id="a6d59-120">It is very important that you use a strong password for the sa login.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a6d59-121">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a6d59-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-change-security-authentication-mode"></a><span data-ttu-id="a6d59-122">變更安全性驗證模式</span><span class="sxs-lookup"><span data-stu-id="a6d59-122">To change security authentication mode</span></span>  
  
1.  <span data-ttu-id="a6d59-123">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的物件總管中，以滑鼠右鍵按一下伺服器，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="a6d59-123">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Object Explorer, right-click the server, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="a6d59-124">在 **[安全性]** 頁面上的 **[伺服器驗證]** 中，選取新的伺服器驗證模式，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="a6d59-124">On the **Security** page, under **Server authentication**, select the new server authentication mode, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="a6d59-125">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 對話方塊中，按一下 **[確定]** 以確認需要重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a6d59-125">In the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] dialog box, click **OK** to acknowledge the requirement to restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
4.  <span data-ttu-id="a6d59-126">在物件總管中，以滑鼠右鍵按一下伺服器，然後按一下 [重新啟動]。</span><span class="sxs-lookup"><span data-stu-id="a6d59-126">In Object Explorer, right-click your server, and then click **Restart**.</span></span> <span data-ttu-id="a6d59-127">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 正在執行，也必須將它重新啟動。</span><span class="sxs-lookup"><span data-stu-id="a6d59-127">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is running, it must also be restarted.</span></span>  
  
#### <a name="to-enable-the-sa-login"></a><span data-ttu-id="a6d59-128">若要啟用 sa 登入</span><span class="sxs-lookup"><span data-stu-id="a6d59-128">To enable the sa login</span></span>  
  
1.  <span data-ttu-id="a6d59-129">在物件總管中，依序展開 [**安全性**] 和 [登入]，以滑鼠右鍵按一下，然後按一下 [內容] `sa` 。 **Properties**</span><span class="sxs-lookup"><span data-stu-id="a6d59-129">In Object Explorer, expand **Security**, expand Logins, right-click `sa`, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="a6d59-130">在 **[一般]** 頁面上，您可能需要為登入建立並確認密碼。</span><span class="sxs-lookup"><span data-stu-id="a6d59-130">On the **General** page, you might have to create and confirm a password for the  login.</span></span>  
  
3.  <span data-ttu-id="a6d59-131">在 **[狀態]** 頁面的 **[登入]** 區段中按一下 **[已啟用]** ，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="a6d59-131">On the **Status** page, in the **Login** section, click **Enabled**, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a6d59-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a6d59-132">Using Transact-SQL</span></span>  
 <span data-ttu-id="a6d59-133">**若要啟用 sa 登入**</span><span class="sxs-lookup"><span data-stu-id="a6d59-133">**To enable the sa login**</span></span>  
  
1.  <span data-ttu-id="a6d59-134">在 [物件總管] 中，連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a6d59-134">In Object Explorer, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a6d59-135">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="a6d59-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a6d59-136">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="a6d59-136">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="a6d59-137">下列範例會啟用 sa 登入並設定新密碼。</span><span class="sxs-lookup"><span data-stu-id="a6d59-137">The following example enables the sa login and sets a new password.</span></span>  
  
    ```  
    ALTER LOGIN sa ENABLE ;  
    GO  
    ALTER LOGIN sa WITH PASSWORD = '<enterStrongPasswordHere>' ;  
    GO  
  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a6d59-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6d59-138">See Also</span></span>  
 <span data-ttu-id="a6d59-139">[增強式密碼](../../relational-databases/security/strong-passwords.md) </span><span class="sxs-lookup"><span data-stu-id="a6d59-139">[Strong Passwords](../../relational-databases/security/strong-passwords.md) </span></span>  
 <span data-ttu-id="a6d59-140">[SQL Server 安裝的安全性考慮](../../sql-server/install/security-considerations-for-a-sql-server-installation.md) </span><span class="sxs-lookup"><span data-stu-id="a6d59-140">[Security Considerations for a SQL Server Installation](../../sql-server/install/security-considerations-for-a-sql-server-installation.md) </span></span>  
 <span data-ttu-id="a6d59-141">[ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a6d59-141">[ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql) </span></span>  
 [<span data-ttu-id="a6d59-142">當系統管理員遭到鎖定時連接到 SQL Server</span><span class="sxs-lookup"><span data-stu-id="a6d59-142">Connect to SQL Server When System Administrators Are Locked Out</span></span>](connect-to-sql-server-when-system-administrators-are-locked-out.md)  
  
  
