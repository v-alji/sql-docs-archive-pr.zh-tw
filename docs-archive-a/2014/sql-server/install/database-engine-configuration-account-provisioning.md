---
title: 資料庫引擎設定-帳戶提供 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 834b26bc-49de-4033-88d5-6aa7b1609720
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 7885bdda72668ac96e90b0900772a4f56575d5fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584994"
---
# <a name="database-engine-configuration---account-provisioning"></a><span data-ttu-id="eb45e-102">Database Engine 組態 - 帳戶提供</span><span class="sxs-lookup"><span data-stu-id="eb45e-102">Database Engine Configuration - Account Provisioning</span></span>
  <span data-ttu-id="eb45e-103">您可以使用此頁面來設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安全性模式，以及加入 Windows 使用者或群組做為 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的管理員。</span><span class="sxs-lookup"><span data-stu-id="eb45e-103">Use this page to set the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security mode, and to add Windows users or groups as administrators of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
## <a name="considerations-for-running-sscurrent"></a><span data-ttu-id="eb45e-104">執行[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 時的考量</span><span class="sxs-lookup"><span data-stu-id="eb45e-104">Considerations for Running [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]</span></span>  
 <span data-ttu-id="eb45e-105">在舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]上， **BUILTIN\Administrators** 群組是提供成 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的登入，而且本機 Administrators 群組的成員可以使用其管理員認證登入。</span><span class="sxs-lookup"><span data-stu-id="eb45e-105">On previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the **BUILTIN\Administrators** group was provisioned as a login in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and members of the local Administrators group could login using their Administrator credentials.</span></span> <span data-ttu-id="eb45e-106">使用較高的權限並非最佳做法。</span><span class="sxs-lookup"><span data-stu-id="eb45e-106">Using elevated permissions is not a best practice.</span></span> <span data-ttu-id="eb45e-107">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中， **BUILTIN\Administrators** 群組並未提供成登入。</span><span class="sxs-lookup"><span data-stu-id="eb45e-107">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] the **BUILTIN\Administrators** group is not provisioned as a login.</span></span> <span data-ttu-id="eb45e-108">因此，您應該為每個管理使用者建立 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入，並在安裝新的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]執行個體期間，將該登入加入至系統管理員 (sysadmin) 固定伺服器角色。</span><span class="sxs-lookup"><span data-stu-id="eb45e-108">As a result, you should create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login for each administrative user, and add that login to the sysadmin fixed server role during installation of a new instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="eb45e-109">您也應該針對用來執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理程式作業的 Windows 帳戶進行上述作業。</span><span class="sxs-lookup"><span data-stu-id="eb45e-109">You should also do this for Windows accounts that are used to run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agent jobs.</span></span> <span data-ttu-id="eb45e-110">這些作業包括複寫代理程式作業。</span><span class="sxs-lookup"><span data-stu-id="eb45e-110">These include replication agent jobs.</span></span>  
  
## <a name="options"></a><span data-ttu-id="eb45e-111">選項</span><span class="sxs-lookup"><span data-stu-id="eb45e-111">Options</span></span>  
 <span data-ttu-id="eb45e-112">**安全性模式** - 為您的安裝選取 Windows 驗證或混合模式驗證。</span><span class="sxs-lookup"><span data-stu-id="eb45e-112">**Security Mode** - Select Windows Authentication or Mixed Mode Authentication for your installation.</span></span>  
  
 <span data-ttu-id="eb45e-113">**Windows 主體提供** - 在舊版的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中，Windows Builtin\Administrator 本機群組置於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統管理員伺服器角色中，可有效授與 Windows 管理員對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的存取權。</span><span class="sxs-lookup"><span data-stu-id="eb45e-113">**Windows Principal Provisioning** - In previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the Windows Builtin\Administrator local group was placed into the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sysadmin server role, effectively granting Windows administrators access to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="eb45e-114">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中，Builtin\Administrator 群組不會提供在系統管理員 (sysadmin) 伺服器角色中。</span><span class="sxs-lookup"><span data-stu-id="eb45e-114">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the Builtin\Administrator group is not provisioned in the sysadmin server role.</span></span> <span data-ttu-id="eb45e-115">您應該改在安裝期間針對新的安裝明確提供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理員。</span><span class="sxs-lookup"><span data-stu-id="eb45e-115">Instead, you should explicitly provision [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administrators for new installations during Setup.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="eb45e-116">您必須在安裝期間針對新的安裝明確提供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理員。</span><span class="sxs-lookup"><span data-stu-id="eb45e-116">You must explicitly provision [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administrators for new installations during Setup.</span></span> <span data-ttu-id="eb45e-117">要等到您完成此步驟之後，安裝程式才允許您繼續。</span><span class="sxs-lookup"><span data-stu-id="eb45e-117">Setup will not allow you to continue until you complete this step.</span></span>  
  
 <span data-ttu-id="eb45e-118">**指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理員** - 您必須為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體指定至少一個 Windows 主體。</span><span class="sxs-lookup"><span data-stu-id="eb45e-118">**Specify [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Administrators** - You must specify at least one Windows principal for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="eb45e-119">若要加入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式執行所用的帳戶，請按一下 [目前使用者]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="eb45e-119">To add the account under which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup is running, click the **Current User** button.</span></span> <span data-ttu-id="eb45e-120">若要從系統管理員清單中加入或移除帳戶，請按一下 **[加入]** 或 **[移除]** ，然後編輯在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體中將會有管理員權限的使用者、群組或電腦清單。</span><span class="sxs-lookup"><span data-stu-id="eb45e-120">To add or remove accounts from the list of system administrators, click **Add** or **Remove**, and then edit the list of users, groups, or computers that will have administrator privileges for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="eb45e-121">當您完成清單的編輯之後，請按一下 [確定]\*\*\*\*，然後在組態對話方塊中確認管理員的清單。</span><span class="sxs-lookup"><span data-stu-id="eb45e-121">When you are finished editing the list, click **OK**, then verify the list of administrators in the configuration dialog.</span></span> <span data-ttu-id="eb45e-122">當此清單完成時，請按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="eb45e-122">When the list is complete, click **Next**.</span></span>  
  
 <span data-ttu-id="eb45e-123">如果您選取混合模式驗證，您必須為內建 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統管理員 (SA) 帳戶提供登入認證。</span><span class="sxs-lookup"><span data-stu-id="eb45e-123">If you select Mixed Mode Authentication, you must provide logon credentials for the builtin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator (SA) account.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]  
  
 <span data-ttu-id="eb45e-124">**Windows 驗證模式**</span><span class="sxs-lookup"><span data-stu-id="eb45e-124">**Windows Authentication Mode**</span></span>  
 <span data-ttu-id="eb45e-125">當使用者透過 Windows 使用者帳戶連接時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會使用作業系統中的 Windows 主體 Token 來驗證帳戶名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="eb45e-125">When a user connects through a Windows user account, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] validates the account name and password using the Windows principal token in the operating system.</span></span> <span data-ttu-id="eb45e-126">這是預設驗證模式，比混合模式更加安全。</span><span class="sxs-lookup"><span data-stu-id="eb45e-126">This is the default authentication mode, and is much more secure than Mixed Mode.</span></span> <span data-ttu-id="eb45e-127">Windows 驗證利用 Kerberos 安全性通訊協定，在增強式密碼的複雜驗證方面提供密碼原則強化，並提供對帳戶鎖定的支援，同時支援密碼逾期。</span><span class="sxs-lookup"><span data-stu-id="eb45e-127">Windows Authentication utilizes Kerberos security protocol, provides password policy enforcement in terms of complexity validation for strong passwords, provides support for account lockout, and supports password expiration.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)] <span data-ttu-id="eb45e-128">絕對不可設定空白或弱式 sa 密碼。</span><span class="sxs-lookup"><span data-stu-id="eb45e-128">Never set a blank or weak sa password.</span></span>  
  
 <span data-ttu-id="eb45e-129">\*\*混合模式 (Windows 驗證或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證) \*\*</span><span class="sxs-lookup"><span data-stu-id="eb45e-129">**Mixed Mode (Windows Authentication or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication)**</span></span>  
 <span data-ttu-id="eb45e-130">允許使用者利用 Windows 驗證或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證來連接。</span><span class="sxs-lookup"><span data-stu-id="eb45e-130">Allows users to connect by using Windows Authentication or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="eb45e-131">透過 Windows 使用者帳戶連接的使用者可以使用 Windows 已驗證的信任連接。</span><span class="sxs-lookup"><span data-stu-id="eb45e-131">Users who connect through a Windows user account can use trusted connections that are validated by Windows.</span></span>  
  
 <span data-ttu-id="eb45e-132">如果您必須選擇混合模式驗證，而且需要使用 SQL 登入來配合舊版應用程式，則您必須為所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶設定增強式密碼。</span><span class="sxs-lookup"><span data-stu-id="eb45e-132">If you must choose Mixed Mode Authentication and you have a requirement for using SQL logins to accommodate legacy applications, you must set strong passwords for all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] accounts.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="eb45e-133">提供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證的目的，只是為了回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="eb45e-133">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication is provided for backward compatibility only.</span></span> [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
 <span data-ttu-id="eb45e-134">**輸入密碼**</span><span class="sxs-lookup"><span data-stu-id="eb45e-134">**Enter Password**</span></span>  
 <span data-ttu-id="eb45e-135">輸入並確認系統管理員 (sa) 登入。</span><span class="sxs-lookup"><span data-stu-id="eb45e-135">Enter and confirm the system administrator (sa) login.</span></span> <span data-ttu-id="eb45e-136">密碼是對抗入侵者的第一道防線，因此，設定增強式密碼對於系統的安全性很重要。</span><span class="sxs-lookup"><span data-stu-id="eb45e-136">Passwords are the first line of defense against intruders, so setting strong passwords is essential to the security of your system.</span></span> <span data-ttu-id="eb45e-137">不得設定空白或弱式 sa 密碼。</span><span class="sxs-lookup"><span data-stu-id="eb45e-137">Never set a blank or weak sa password.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="eb45e-138">密碼可包含 1 到 128 個字元，包括字母、符號和數字的任意組合。</span><span class="sxs-lookup"><span data-stu-id="eb45e-138">passwords can contain from 1 to 128 characters, including any combination of letters, symbols, and numbers.</span></span> <span data-ttu-id="eb45e-139">如果您選擇混合模式驗證，則在您可以繼續到安裝精靈的下一頁之前，必須先輸入增強式 sa 密碼。</span><span class="sxs-lookup"><span data-stu-id="eb45e-139">If you choose Mixed Mode authentication, you must enter a strong sa password before you can continue to the next page of the Installation Wizard.</span></span>  
  
 <span data-ttu-id="eb45e-140">**增強式密碼方針**</span><span class="sxs-lookup"><span data-stu-id="eb45e-140">**Strong Password Guidelines**</span></span>  
 <span data-ttu-id="eb45e-141">增強式密碼不會很快被猜到，使用電腦程式也不容易破解。</span><span class="sxs-lookup"><span data-stu-id="eb45e-141">Strong passwords are not readily guessed by a person, and are not easily hacked using a computer program.</span></span> <span data-ttu-id="eb45e-142">增強式密碼不得使用禁止條件或詞彙，包括：</span><span class="sxs-lookup"><span data-stu-id="eb45e-142">Strong passwords cannot use prohibited conditions or terms, including:</span></span>  
  
-   <span data-ttu-id="eb45e-143">空白或 NULL 條件</span><span class="sxs-lookup"><span data-stu-id="eb45e-143">A blank or NULL condition</span></span>  
  
-   <span data-ttu-id="eb45e-144">"Password"</span><span class="sxs-lookup"><span data-stu-id="eb45e-144">"Password"</span></span>  
  
-   <span data-ttu-id="eb45e-145">"Admin"</span><span class="sxs-lookup"><span data-stu-id="eb45e-145">"Admin"</span></span>  
  
-   <span data-ttu-id="eb45e-146">"Administrator"</span><span class="sxs-lookup"><span data-stu-id="eb45e-146">"Administrator"</span></span>  
  
-   <span data-ttu-id="eb45e-147">"sa"</span><span class="sxs-lookup"><span data-stu-id="eb45e-147">"sa"</span></span>  
  
-   <span data-ttu-id="eb45e-148">"sysadmin"</span><span class="sxs-lookup"><span data-stu-id="eb45e-148">"sysadmin"</span></span>  
  
 <span data-ttu-id="eb45e-149">增強式密碼不得為與安裝電腦相關的下列詞彙：</span><span class="sxs-lookup"><span data-stu-id="eb45e-149">A strong password cannot be the following terms associated with the installation computer:</span></span>  
  
-   <span data-ttu-id="eb45e-150">目前登入機器的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="eb45e-150">The name of the user currently logged onto the machine.</span></span>  
  
-   <span data-ttu-id="eb45e-151">電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="eb45e-151">The computer name.</span></span>  
  
 <span data-ttu-id="eb45e-152">增強式密碼的長度必須為 8 個字元以上，且至少滿足下列四項準則中的三項：</span><span class="sxs-lookup"><span data-stu-id="eb45e-152">A strong password must be more than 8 characters in length and satisfy at least three of the following four criteria:</span></span>  
  
-   <span data-ttu-id="eb45e-153">必須包含大寫字母。</span><span class="sxs-lookup"><span data-stu-id="eb45e-153">It must contain uppercase letters.</span></span>  
  
-   <span data-ttu-id="eb45e-154">必須包含小寫字母。</span><span class="sxs-lookup"><span data-stu-id="eb45e-154">It must contain lowercase letters.</span></span>  
  
-   <span data-ttu-id="eb45e-155">必須包含數字。</span><span class="sxs-lookup"><span data-stu-id="eb45e-155">It must contain numbers.</span></span>  
  
-   <span data-ttu-id="eb45e-156">必須包含非英數字元；例如 #、% 或 ^。</span><span class="sxs-lookup"><span data-stu-id="eb45e-156">It must contain non-alphanumeric characters; for example, #, %, or ^.</span></span>  
  
 <span data-ttu-id="eb45e-157">此頁面中輸入的密碼必須符合增強式密碼原則的需求。</span><span class="sxs-lookup"><span data-stu-id="eb45e-157">Passwords entered on this page must meet strong password policy requirements.</span></span> <span data-ttu-id="eb45e-158">如果您有使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證的任何自動化作業，請確定此密碼符合增強式密碼原則的需求。</span><span class="sxs-lookup"><span data-stu-id="eb45e-158">If you have any automation that uses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, ensure that the password meets strong password policy requirements.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="eb45e-159">相關內容</span><span class="sxs-lookup"><span data-stu-id="eb45e-159">Related Content</span></span>  
 <span data-ttu-id="eb45e-160">如需有關選擇 Windows 驗證和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證之比較的詳細資訊，請參閱《 **線上叢書》中的** 選擇驗證模式 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 主題。</span><span class="sxs-lookup"><span data-stu-id="eb45e-160">For more information about choosing Windows Authentication vs. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, see the topic **Choose an Authentication Mode** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="eb45e-161">如需選擇帳戶以執行 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的**設定 Windows 服務帳戶與權限**主題。</span><span class="sxs-lookup"><span data-stu-id="eb45e-161">For more information about choosing an account to run the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], see the topic **Configure Windows Service Accounts and Permissions** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb45e-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb45e-162">See Also</span></span>  
 [<span data-ttu-id="eb45e-163">設定 Windows 服務帳戶與權限</span><span class="sxs-lookup"><span data-stu-id="eb45e-163">Configure Windows Service Accounts and Permissions</span></span>](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)  
  
  
