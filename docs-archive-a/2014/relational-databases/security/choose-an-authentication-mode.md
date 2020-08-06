---
title: 選擇驗證模式 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.ins.instwizard.authenticationmode.f1
helpviewer_keywords:
- sa account
- authentication modes
- trusted connection
- SQL Server Installation Wizard, Authentication Mode page
- choose authentication mode
- authentication [SQL Server], choosing a mode
- Windows authentication [SQL Server]
- mixed mode authentication
- mixed authentication mode
- SQL authentication mode
ms.assetid: ff7a6a48-3d38-4209-aa0f-7d6c0a8c64ef
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 973d1ef75512f44c5dd7bbff844b72525554082e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702593"
---
# <a name="choose-an-authentication-mode"></a><span data-ttu-id="97af6-102">選擇驗證模式</span><span class="sxs-lookup"><span data-stu-id="97af6-102">Choose an Authentication Mode</span></span>
  <span data-ttu-id="97af6-103">在安裝期間，您必須選取 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的驗證模式。</span><span class="sxs-lookup"><span data-stu-id="97af6-103">During setup, you must select an authentication mode for the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="97af6-104">有兩種可能的模式：Windows 驗證模式與混合模式。</span><span class="sxs-lookup"><span data-stu-id="97af6-104">There are two possible modes: Windows Authentication mode and mixed mode.</span></span> <span data-ttu-id="97af6-105">Windows 驗證模式會啟用 Windows 驗證並停用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證。</span><span class="sxs-lookup"><span data-stu-id="97af6-105">Windows Authentication mode enables Windows Authentication and disables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="97af6-106">混合模式會啟用 Windows 驗證及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證。</span><span class="sxs-lookup"><span data-stu-id="97af6-106">Mixed mode enables both Windows Authentication and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="97af6-107">Windows 驗證一定可用而且無法停用。</span><span class="sxs-lookup"><span data-stu-id="97af6-107">Windows Authentication is always available and cannot be disabled.</span></span>  
  
## <a name="configuring-the-authentication-mode"></a><span data-ttu-id="97af6-108">設定驗證模式</span><span class="sxs-lookup"><span data-stu-id="97af6-108">Configuring the Authentication Mode</span></span>  
 <span data-ttu-id="97af6-109">如果您在安裝期間選取混合模式驗證，就必須為名為 sa 的內建 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統管理員帳戶提供並確認增強式密碼。</span><span class="sxs-lookup"><span data-stu-id="97af6-109">If you select Mixed Mode Authentication during setup, you must provide and then confirm a strong password for the built-in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator account named sa.</span></span> <span data-ttu-id="97af6-110">sa 帳戶會使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證進行連接。</span><span class="sxs-lookup"><span data-stu-id="97af6-110">The sa account connects by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="97af6-111">如果您在安裝期間選取 Windows 驗證，安裝程式就會針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證建立 sa 帳戶，但是此帳戶是停用的。</span><span class="sxs-lookup"><span data-stu-id="97af6-111">If you select Windows Authentication during setup, Setup creates the sa account for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication but it is disabled.</span></span> <span data-ttu-id="97af6-112">如果您之後變更為混合模式驗證，而且想要使用 sa 帳戶，就必須啟用此帳戶。</span><span class="sxs-lookup"><span data-stu-id="97af6-112">If you later change to Mixed Mode Authentication and you want to use the sa account, you must enable the account.</span></span> <span data-ttu-id="97af6-113">任何 Windows 或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶都可以設定為系統管理員。</span><span class="sxs-lookup"><span data-stu-id="97af6-113">Any Windows or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account can be configured as a system administrator.</span></span> <span data-ttu-id="97af6-114">由於 sa 帳戶是已知的而且經常成為惡意使用者的攻擊目標，因此除非您的應用程式需要 sa 帳戶，否則請勿啟用此帳戶。</span><span class="sxs-lookup"><span data-stu-id="97af6-114">Because the sa account is well known and often targeted by malicious users, do not enable the sa account unless your application requires it.</span></span> <span data-ttu-id="97af6-115">此外，絕對不可針對 sa 帳戶設定空白或弱式密碼。</span><span class="sxs-lookup"><span data-stu-id="97af6-115">Never set a blank or weak password for the sa account.</span></span> <span data-ttu-id="97af6-116">若要從 Windows 驗證模式變更為混合模式驗證，並且使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證，請參閱 [變更伺服器驗證模式](../../database-engine/configure-windows/change-server-authentication-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="97af6-116">To change from Windows Authentication mode to Mixed Mode Authentication and use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, see [Change Server Authentication Mode](../../database-engine/configure-windows/change-server-authentication-mode.md).</span></span>  
  
## <a name="connecting-through-windows-authentication"></a><span data-ttu-id="97af6-117">透過 Windows 驗證進行連接</span><span class="sxs-lookup"><span data-stu-id="97af6-117">Connecting Through Windows Authentication</span></span>  
 <span data-ttu-id="97af6-118">當使用者透過 Windows 使用者帳戶連接時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會使用作業系統中的 Windows 主體 Token 來驗證帳戶名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="97af6-118">When a user connects through a Windows user account, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] validates the account name and password using the Windows principal token in the operating system.</span></span> <span data-ttu-id="97af6-119">這代表 Windows 已確認使用者身分。</span><span class="sxs-lookup"><span data-stu-id="97af6-119">This means that the user identity is confirmed by Windows.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="97af6-120">不會要求您輸入密碼，而且不會執行身分驗證。</span><span class="sxs-lookup"><span data-stu-id="97af6-120">does not ask for the password, and does not perform the identity validation.</span></span> <span data-ttu-id="97af6-121">Windows 驗證是預設驗證模式，而且比 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證更安全。</span><span class="sxs-lookup"><span data-stu-id="97af6-121">Windows Authentication is the default authentication mode, and is much more secure than [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="97af6-122">Windows 驗證會使用 Kerberos 安全性通訊協定、在增強式密碼的複雜驗證方面提供密碼原則強化、提供對帳戶鎖定的支援，而且支援密碼逾期。</span><span class="sxs-lookup"><span data-stu-id="97af6-122">Windows Authentication uses Kerberos security protocol, provides password policy enforcement with regard to complexity validation for strong passwords, provides support for account lockout, and supports password expiration.</span></span> <span data-ttu-id="97af6-123">使用 Windows 驗證所建立的連接有時候稱為信任連接，因為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會信任 Windows 所提供的認證。</span><span class="sxs-lookup"><span data-stu-id="97af6-123">A connection made using Windows Authentication is sometimes called a trusted connection, because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] trusts the credentials provided by Windows.</span></span>  
  
 <span data-ttu-id="97af6-124">使用 Windows 驗證，可以在網域層級建立 Windows 群組，也可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 建立整個群組的登入。</span><span class="sxs-lookup"><span data-stu-id="97af6-124">By using Windows Authentication, Windows groups can be created at the domain level, and a login can be created on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for the entire group.</span></span> <span data-ttu-id="97af6-125">從網域層級管理存取可簡化帳戶管理。</span><span class="sxs-lookup"><span data-stu-id="97af6-125">Managing access from at the domain level can simplify account administration.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
## <a name="connecting-through-sql-server-authentication"></a><span data-ttu-id="97af6-126">透過 SQL Server 驗證進行連接</span><span class="sxs-lookup"><span data-stu-id="97af6-126">Connecting Through SQL Server Authentication</span></span>  
 <span data-ttu-id="97af6-127">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證時，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中建立不是以 Windows 使用者帳戶為基礎的登入。</span><span class="sxs-lookup"><span data-stu-id="97af6-127">When using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, logins are created in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are not based on Windows user accounts.</span></span> <span data-ttu-id="97af6-128">其使用者名稱和密碼都是使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所建立而且儲存在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中。</span><span class="sxs-lookup"><span data-stu-id="97af6-128">Both the user name and the password are created by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="97af6-129">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證進行連接的使用者必須在每次連接時提供其認證 (登入和密碼)。</span><span class="sxs-lookup"><span data-stu-id="97af6-129">Users connecting using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication must provide their credentials (login and password) every time that they connect.</span></span> <span data-ttu-id="97af6-130">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證時，所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶都必須設定增強式密碼。</span><span class="sxs-lookup"><span data-stu-id="97af6-130">When using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, you must set strong passwords for all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] accounts.</span></span> <span data-ttu-id="97af6-131">如需增強式密碼的指導方針，請參閱 [增強式密碼](strong-passwords.md)。</span><span class="sxs-lookup"><span data-stu-id="97af6-131">For strong password guidelines, see [Strong Passwords](strong-passwords.md).</span></span>  
  
 <span data-ttu-id="97af6-132">有三個選擇性密碼原則可供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入使用。</span><span class="sxs-lookup"><span data-stu-id="97af6-132">Three optional password policies are available for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins.</span></span>  
  
-   <span data-ttu-id="97af6-133">使用者必須在下次登入時變更密碼</span><span class="sxs-lookup"><span data-stu-id="97af6-133">User must change password at next login</span></span>  
  
     <span data-ttu-id="97af6-134">要求使用者在下次連接時變更密碼。</span><span class="sxs-lookup"><span data-stu-id="97af6-134">Requires the user to change the password the next time that the user connects.</span></span> <span data-ttu-id="97af6-135">變更密碼的功能是由 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]提供的。</span><span class="sxs-lookup"><span data-stu-id="97af6-135">The ability to change the password is provided by [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="97af6-136">如果使用這個選項，協力廠商軟體開發人員應該提供這項功能。</span><span class="sxs-lookup"><span data-stu-id="97af6-136">Third-party software developers should provide this feature if this option is used.</span></span>  
  
-   <span data-ttu-id="97af6-137">強制執行密碼逾期</span><span class="sxs-lookup"><span data-stu-id="97af6-137">Enforce password expiration</span></span>  
  
     <span data-ttu-id="97af6-138">針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入強制執行電腦的最大密碼存在時間原則。</span><span class="sxs-lookup"><span data-stu-id="97af6-138">The maximum password age policy of the computer is enforced for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins.</span></span>  
  
-   <span data-ttu-id="97af6-139">強制執行密碼原則</span><span class="sxs-lookup"><span data-stu-id="97af6-139">Enforce password policy</span></span>  
  
     <span data-ttu-id="97af6-140">針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入強制執行電腦的 Windows 密碼原則。</span><span class="sxs-lookup"><span data-stu-id="97af6-140">The Windows password policies of the computer are enforced for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins.</span></span> <span data-ttu-id="97af6-141">這包括密碼長度和複雜性。</span><span class="sxs-lookup"><span data-stu-id="97af6-141">This includes password length and complexity.</span></span> <span data-ttu-id="97af6-142">這項功能相依於 `NetValidatePasswordPolicy` API，而這個 API 只有 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 和更新版本才有。</span><span class="sxs-lookup"><span data-stu-id="97af6-142">This functionality depends on the `NetValidatePasswordPolicy` API, which is only available in [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] and later versions.</span></span>  
  
#### <a name="to-determine-the-password-policies-of-the-local-computer"></a><span data-ttu-id="97af6-143">判斷本機電腦的密碼原則</span><span class="sxs-lookup"><span data-stu-id="97af6-143">To determine the password policies of the local computer</span></span>  
  
1.  <span data-ttu-id="97af6-144">在 **[開始]** 功能表上，按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="97af6-144">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="97af6-145">在 [**執行**] 對話方塊中，輸入 `secpol.msc` ，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="97af6-145">In the **Run** dialog box, type `secpol.msc`, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="97af6-146">在 [本機安全性設定] 應用程式中，依序展開 [安全性設定] 和 [帳戶原則]，然後按一下 [密碼原則]。</span><span class="sxs-lookup"><span data-stu-id="97af6-146">In the **Local Security Settings** application, expand **Security Settings**, expand **Account Policies**, and then click **Password Policy**.</span></span>  
  
     <span data-ttu-id="97af6-147">密碼原則就會描述在結果窗格中。</span><span class="sxs-lookup"><span data-stu-id="97af6-147">The password policies are described in the results pane.</span></span>  
  
### <a name="disadvantages-of-sql-server-authentication"></a><span data-ttu-id="97af6-148">SQL Server 驗證的缺點</span><span class="sxs-lookup"><span data-stu-id="97af6-148">Disadvantages of SQL Server Authentication</span></span>  
  
-   <span data-ttu-id="97af6-149">如果某位使用者是擁有 Windows 登入和密碼的 Windows 網域使用者，則仍然必須提供其他 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) 登入和密碼才能連接。</span><span class="sxs-lookup"><span data-stu-id="97af6-149">If a user is a Windows domain user who has a login and password for Windows, he must still provide another ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) login and password to connect.</span></span> <span data-ttu-id="97af6-150">追蹤多個名稱和密碼對於許多使用者而言很困難。</span><span class="sxs-lookup"><span data-stu-id="97af6-150">Keeping track of multiple names and passwords is difficult for many users.</span></span> <span data-ttu-id="97af6-151">此外，每次連接至資料庫就必須提供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認證可能會造成困擾。</span><span class="sxs-lookup"><span data-stu-id="97af6-151">Having to provide [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] credentials every time that one connects to the database can be annoying.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="97af6-152">驗證無法使用 Kerberos 安全性通訊協定。</span><span class="sxs-lookup"><span data-stu-id="97af6-152">Authentication cannot use Kerberos security protocol.</span></span>  
  
-   <span data-ttu-id="97af6-153">Windows 提供了不適用於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入的其他密碼原則。</span><span class="sxs-lookup"><span data-stu-id="97af6-153">Windows offers additional password policies that are not available for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins.</span></span>  
  
-   <span data-ttu-id="97af6-154">加密的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證登入密碼在連接時必須透過網路傳遞。</span><span class="sxs-lookup"><span data-stu-id="97af6-154">The encrypted [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication login password, must be passed over the network at the time of the connection.</span></span> <span data-ttu-id="97af6-155">自動連接的某些應用程式會將密碼儲存在用戶端。</span><span class="sxs-lookup"><span data-stu-id="97af6-155">Some applications that connect automatically will store the password at the client.</span></span> <span data-ttu-id="97af6-156">這些是額外的攻擊點。</span><span class="sxs-lookup"><span data-stu-id="97af6-156">These are additional attack points.</span></span>  
  
### <a name="advantages-of-sql-server-authentication"></a><span data-ttu-id="97af6-157">SQL Server 驗證的優點</span><span class="sxs-lookup"><span data-stu-id="97af6-157">Advantages of SQL Server Authentication</span></span>  
  
-   <span data-ttu-id="97af6-158">可讓 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支援需要 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證的舊版應用程式以及協力廠商所提供的應用程式。</span><span class="sxs-lookup"><span data-stu-id="97af6-158">Allows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to support older applications and applications provided by third parties that require [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
-   <span data-ttu-id="97af6-159">可讓 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支援具有混合作業系統的環境，其中 Windows 網域無法驗證所有使用者。</span><span class="sxs-lookup"><span data-stu-id="97af6-159">Allows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to support environments with mixed operating systems, where all users are not authenticated by a Windows domain.</span></span>  
  
-   <span data-ttu-id="97af6-160">可讓使用者從未知或未受信任的網域進行連線。</span><span class="sxs-lookup"><span data-stu-id="97af6-160">Allows users to connect from unknown or untrusted domains.</span></span> <span data-ttu-id="97af6-161">例如，既有客戶使用所指派 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入連接來接收訂單狀態的應用程式。</span><span class="sxs-lookup"><span data-stu-id="97af6-161">For instance, an application where established customers connect with assigned [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins to receive the status of their orders.</span></span>  
  
-   <span data-ttu-id="97af6-162">可讓 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支援 Web 架構應用程式，其中使用者會建立自己的識別。</span><span class="sxs-lookup"><span data-stu-id="97af6-162">Allows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to support Web-based applications where users create their own identities.</span></span>  
  
-   <span data-ttu-id="97af6-163">可讓軟體開發人員根據已知的現有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入，使用複雜的權限階層來散發其應用程式。</span><span class="sxs-lookup"><span data-stu-id="97af6-163">Allows software developers to distribute their applications by using a complex permission hierarchy based on known, preset [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="97af6-164">使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證不會限制安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之電腦上本機管理員的權限。</span><span class="sxs-lookup"><span data-stu-id="97af6-164">Using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication does not limit the permissions of local administrators on the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97af6-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97af6-165">See Also</span></span>  
 [<span data-ttu-id="97af6-166">SQL Server 安裝的安全性考量</span><span class="sxs-lookup"><span data-stu-id="97af6-166">Security Considerations for a SQL Server Installation</span></span>](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
  
