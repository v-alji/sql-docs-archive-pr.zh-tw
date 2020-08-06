---
title: MSSQLSERVER_18456 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 18456 (Database Engine error)
ms.assetid: c417631d-be1f-42e0-8844-9f92c77e11f7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f5addb6bfb9d056d9f1796749ae629d4150102a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699694"
---
# <a name="mssqlserver_18456"></a><span data-ttu-id="aba31-102">MSSQLSERVER_18456</span><span class="sxs-lookup"><span data-stu-id="aba31-102">MSSQLSERVER_18456</span></span>
    
## <a name="details"></a><span data-ttu-id="aba31-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="aba31-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aba31-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="aba31-104">Product Name</span></span>|<span data-ttu-id="aba31-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="aba31-105">SQL Server</span></span>|  
|<span data-ttu-id="aba31-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="aba31-106">Event ID</span></span>|<span data-ttu-id="aba31-107">18456</span><span class="sxs-lookup"><span data-stu-id="aba31-107">18456</span></span>|  
|<span data-ttu-id="aba31-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="aba31-108">Event Source</span></span>|<span data-ttu-id="aba31-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="aba31-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="aba31-110">元件</span><span class="sxs-lookup"><span data-stu-id="aba31-110">Component</span></span>|<span data-ttu-id="aba31-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="aba31-111">SQLEngine</span></span>|  
|<span data-ttu-id="aba31-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="aba31-112">Symbolic Name</span></span>|<span data-ttu-id="aba31-113">LOGON_FAILED</span><span class="sxs-lookup"><span data-stu-id="aba31-113">LOGON_FAILED</span></span>|  
|<span data-ttu-id="aba31-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="aba31-114">Message Text</span></span>|<span data-ttu-id="aba31-115">使用者 '%.\*ls'.%.\*ls 登入失敗</span><span class="sxs-lookup"><span data-stu-id="aba31-115">Login failed for user '%.\*ls'.%.\*ls</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="aba31-116">說明</span><span class="sxs-lookup"><span data-stu-id="aba31-116">Explanation</span></span>  
 <span data-ttu-id="aba31-117">當連線嘗試因為密碼或使用者名稱不正確而驗證失敗並遭到拒絕時，將會傳回與下列內容相似的訊息到用戶端：「使用者 '<user_name>' 登入失敗。</span><span class="sxs-lookup"><span data-stu-id="aba31-117">When a connection attempt is rejected because of an authentication failure that involves a bad password or user name, a message similar to the following is returned to the client:  "Login failed for user '<user_name>'.</span></span> <span data-ttu-id="aba31-118">(Microsoft SQL Server，錯誤：18456)」。</span><span class="sxs-lookup"><span data-stu-id="aba31-118">(Microsoft SQL Server, Error: 18456)".</span></span>  
  
 <span data-ttu-id="aba31-119">其他傳回給用戶端的資訊還包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="aba31-119">Additional information returned to the client includes the following:</span></span>  
  
 <span data-ttu-id="aba31-120">「使用者 '<user_name>' 登入失敗。</span><span class="sxs-lookup"><span data-stu-id="aba31-120">"Login failed for user '<user_name>'.</span></span> <span data-ttu-id="aba31-121">(.Net SqlClient 資料提供者)」</span><span class="sxs-lookup"><span data-stu-id="aba31-121">(.Net SqlClient Data Provider)"</span></span>  
  
 -----------------------------\-  
  
 <span data-ttu-id="aba31-122">「伺服器名稱：<computer_name>」</span><span class="sxs-lookup"><span data-stu-id="aba31-122">"Server Name: <computer_name>"</span></span>  
  
 <span data-ttu-id="aba31-123">「錯誤號碼：18456」</span><span class="sxs-lookup"><span data-stu-id="aba31-123">"Error Number: 18456"</span></span>  
  
 <span data-ttu-id="aba31-124">「嚴重性：14」</span><span class="sxs-lookup"><span data-stu-id="aba31-124">"Severity: 14"</span></span>  
  
 <span data-ttu-id="aba31-125">「狀態：1」</span><span class="sxs-lookup"><span data-stu-id="aba31-125">"State: 1"</span></span>  
  
 <span data-ttu-id="aba31-126">「行號：65536」</span><span class="sxs-lookup"><span data-stu-id="aba31-126">"Line Number: 65536"</span></span>  
  
 <span data-ttu-id="aba31-127">也可能傳回下列訊息：</span><span class="sxs-lookup"><span data-stu-id="aba31-127">The following message might also be returned:</span></span>  
  
 <span data-ttu-id="aba31-128">「訊息 18456，層級 14，狀態 1，伺服器 <computer_name>，行 1」</span><span class="sxs-lookup"><span data-stu-id="aba31-128">"Msg 18456, Level 14, State 1, Server <computer_name>, Line 1"</span></span>  
  
 <span data-ttu-id="aba31-129">「使用者 '<user_name>' 登入失敗。」</span><span class="sxs-lookup"><span data-stu-id="aba31-129">"Login failed for user '<user_name>'."</span></span>  
  
## <a name="additional-error-information"></a><span data-ttu-id="aba31-130">其他錯誤資訊</span><span class="sxs-lookup"><span data-stu-id="aba31-130">Additional Error Information</span></span>  
 <span data-ttu-id="aba31-131">為增加安全性，傳回用戶端的錯誤訊息會刻意隱藏驗證錯誤的原本形式。</span><span class="sxs-lookup"><span data-stu-id="aba31-131">To increase security, the error message that is returned to the client deliberately hides the nature of the authentication error.</span></span> <span data-ttu-id="aba31-132">不過，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔中，會有對應的錯誤包含對應至驗證失敗狀況的錯誤狀態。</span><span class="sxs-lookup"><span data-stu-id="aba31-132">However, in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log, a corresponding error contains an error state that maps to an authentication failure condition.</span></span> <span data-ttu-id="aba31-133">請將錯誤狀態與下列清單做比較，以判斷登入失敗的原因。</span><span class="sxs-lookup"><span data-stu-id="aba31-133">Compare the error state to the following list to determine the reason for the login failure.</span></span>  
  
|<span data-ttu-id="aba31-134">State</span><span class="sxs-lookup"><span data-stu-id="aba31-134">State</span></span>|<span data-ttu-id="aba31-135">描述</span><span class="sxs-lookup"><span data-stu-id="aba31-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="aba31-136">1</span><span class="sxs-lookup"><span data-stu-id="aba31-136">1</span></span>|<span data-ttu-id="aba31-137">無錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="aba31-137">Error information is not available.</span></span> <span data-ttu-id="aba31-138">這個狀態通常表示您沒有接收錯誤詳細資料的權限。</span><span class="sxs-lookup"><span data-stu-id="aba31-138">This state usually means you do not have permission to receive the error details.</span></span> <span data-ttu-id="aba31-139">如需詳細資訊，請連絡 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理員。</span><span class="sxs-lookup"><span data-stu-id="aba31-139">Contact your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administrator for more information.</span></span>|  
|<span data-ttu-id="aba31-140">2</span><span class="sxs-lookup"><span data-stu-id="aba31-140">2</span></span>|<span data-ttu-id="aba31-141">使用者識別碼無效。</span><span class="sxs-lookup"><span data-stu-id="aba31-141">User ID is not valid.</span></span>|  
|<span data-ttu-id="aba31-142">5</span><span class="sxs-lookup"><span data-stu-id="aba31-142">5</span></span>|<span data-ttu-id="aba31-143">使用者識別碼無效。</span><span class="sxs-lookup"><span data-stu-id="aba31-143">User ID is not valid.</span></span>|  
|<span data-ttu-id="aba31-144">6</span><span class="sxs-lookup"><span data-stu-id="aba31-144">6</span></span>|<span data-ttu-id="aba31-145">嘗試將 Windows 登入名稱用於 SQL Server 驗證。</span><span class="sxs-lookup"><span data-stu-id="aba31-145">An attempt was made to use a Windows login name with SQL Server Authentication.</span></span>|  
|<span data-ttu-id="aba31-146">7</span><span class="sxs-lookup"><span data-stu-id="aba31-146">7</span></span>|<span data-ttu-id="aba31-147">已停用登入且密碼不正確。</span><span class="sxs-lookup"><span data-stu-id="aba31-147">Login is disabled, and the password is incorrect.</span></span>|  
|<span data-ttu-id="aba31-148">8</span><span class="sxs-lookup"><span data-stu-id="aba31-148">8</span></span>|<span data-ttu-id="aba31-149">密碼不正確。</span><span class="sxs-lookup"><span data-stu-id="aba31-149">The password is incorrect.</span></span>|  
|<span data-ttu-id="aba31-150">9</span><span class="sxs-lookup"><span data-stu-id="aba31-150">9</span></span>|<span data-ttu-id="aba31-151">密碼無效。</span><span class="sxs-lookup"><span data-stu-id="aba31-151">Password is not valid.</span></span>|  
|<span data-ttu-id="aba31-152">11</span><span class="sxs-lookup"><span data-stu-id="aba31-152">11</span></span>|<span data-ttu-id="aba31-153">登入有效，但伺服器存取失敗。</span><span class="sxs-lookup"><span data-stu-id="aba31-153">Login is valid, but server access failed.</span></span> <span data-ttu-id="aba31-154">導致此錯誤的一個可能原因是：Windows 使用者可以使用本機 Administrators 群組成員的身分存取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，但 Windows 不會提供系統管理員認證。</span><span class="sxs-lookup"><span data-stu-id="aba31-154">One possible cause of this error is when the Windows user has access to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as a member of the local administrators group, but Windows is not providing administrator credentials.</span></span> <span data-ttu-id="aba31-155">若要連接，請使用 [以系統管理員身分執行] 選項開始連接程式，然後以特定登入，將 Windows 使用者新增至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="aba31-155">To connect, start the connecting program using the **Run as administrator** option, and then add the Windows user to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as a specific login.</span></span>|  
|<span data-ttu-id="aba31-156">12</span><span class="sxs-lookup"><span data-stu-id="aba31-156">12</span></span>|<span data-ttu-id="aba31-157">登入是有效的登入，但伺服器存取失敗。</span><span class="sxs-lookup"><span data-stu-id="aba31-157">Login is valid login, but server access failed.</span></span>|  
|<span data-ttu-id="aba31-158">18</span><span class="sxs-lookup"><span data-stu-id="aba31-158">18</span></span>|<span data-ttu-id="aba31-159">密碼必須變更。</span><span class="sxs-lookup"><span data-stu-id="aba31-159">Password must be changed.</span></span>|  
  
 <span data-ttu-id="aba31-160">其他錯誤狀態存在，表示有未預期的內部處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="aba31-160">Other error states exist and signify an unexpected internal processing error.</span></span>  
  
 <span data-ttu-id="aba31-161">**另一個不尋常的可能原因**</span><span class="sxs-lookup"><span data-stu-id="aba31-161">**An additional unusual possible cause**</span></span>  
  
 <span data-ttu-id="aba31-162">如有下列情況，可能會傳回這個錯誤原因：**嘗試使用 SQL 驗證登入失敗。伺服器設定成只允許 Windows 驗證。**</span><span class="sxs-lookup"><span data-stu-id="aba31-162">The error reason **An attempt to login using SQL authentication failed. Server is configured for Windows authentication only.**</span></span> <span data-ttu-id="aba31-163">會在下列情況傳回。</span><span class="sxs-lookup"><span data-stu-id="aba31-163">can be returned in the following situations.</span></span>  
  
-   <span data-ttu-id="aba31-164">伺服器是設定成混合模式驗證，而 ODBC 連接使用了 TCP 通訊協定，且此連接並未明確指定連接應使用信任連接。</span><span class="sxs-lookup"><span data-stu-id="aba31-164">When the server is configured for mixed mode authentication, and an ODBC connection uses the TCP protocol, and the connection does not explicitly specify that the connection should use a trusted connection.</span></span>  
  
-   <span data-ttu-id="aba31-165">伺服器是設定成混合模式驗證，而 ODBC 連接使用了具名管道，同時用戶端用以開啟具名管道的認證已用於自動模擬使用者，且此連接並未明確指定連接應使用信任連接。</span><span class="sxs-lookup"><span data-stu-id="aba31-165">When the server is configured for mixed mode authentication, and an ODBC connection uses named pipes, and the credentials the client used to open the named pipe are used to automatically impersonate the user, and the connection does not explicitly specify that the connection should use a trusted connection.</span></span>  
  
 <span data-ttu-id="aba31-166">若要解決此問題，請在連接字串中加上 `TRUSTED_CONNECTION = TRUE`。</span><span class="sxs-lookup"><span data-stu-id="aba31-166">To resolve this issue, include `TRUSTED_CONNECTION = TRUE` in the connection string.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="aba31-167">範例</span><span class="sxs-lookup"><span data-stu-id="aba31-167">Examples</span></span>  
 <span data-ttu-id="aba31-168">在此範例中，驗證錯誤狀態為 8。</span><span class="sxs-lookup"><span data-stu-id="aba31-168">In this example, the authentication error state is 8.</span></span> <span data-ttu-id="aba31-169">這表示密碼不正確。</span><span class="sxs-lookup"><span data-stu-id="aba31-169">This indicates that the password is incorrect.</span></span>  
  
|<span data-ttu-id="aba31-170">Date</span><span class="sxs-lookup"><span data-stu-id="aba31-170">Date</span></span>|<span data-ttu-id="aba31-171">來源</span><span class="sxs-lookup"><span data-stu-id="aba31-171">Source</span></span>|<span data-ttu-id="aba31-172">訊息</span><span class="sxs-lookup"><span data-stu-id="aba31-172">Message</span></span>|  
|----------|------------|-------------|  
|<span data-ttu-id="aba31-173">2007-12-05 20:12:56.34</span><span class="sxs-lookup"><span data-stu-id="aba31-173">2007-12-05 20:12:56.34</span></span>|<span data-ttu-id="aba31-174">登入</span><span class="sxs-lookup"><span data-stu-id="aba31-174">Logon</span></span>|<span data-ttu-id="aba31-175">錯誤：18456，嚴重性：14，狀態：8.</span><span class="sxs-lookup"><span data-stu-id="aba31-175">Error: 18456, Severity: 14, State: 8.</span></span>|  
|<span data-ttu-id="aba31-176">2007-12-05 20:12:56.34</span><span class="sxs-lookup"><span data-stu-id="aba31-176">2007-12-05 20:12:56.34</span></span>|<span data-ttu-id="aba31-177">登入</span><span class="sxs-lookup"><span data-stu-id="aba31-177">Logon</span></span>|<span data-ttu-id="aba31-178">使用者 '<user_name>' 登入失敗。</span><span class="sxs-lookup"><span data-stu-id="aba31-178">Login failed for user '<user_name>'.</span></span> <span data-ttu-id="aba31-179">[CLIENT: \<ip address>]</span><span class="sxs-lookup"><span data-stu-id="aba31-179">[CLIENT: \<ip address>]</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="aba31-180">若您使用 Windows 驗證模式來安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，並於之後將其變更為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 與 Windows 驗證模式，就會先停用 **sa** 登入。</span><span class="sxs-lookup"><span data-stu-id="aba31-180">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed using Windows Authentication mode and is later changed to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows Authentication mode, the **sa** login is initially disabled.</span></span> <span data-ttu-id="aba31-181">這將造成狀態 7 錯誤：「使用者 'sa' 登入失敗。」若要啟用 **sa** 登入，請參閱[變更伺服器驗證模式](../../database-engine/configure-windows/change-server-authentication-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="aba31-181">This causes the state 7 error: "Login failed for user 'sa'." To enable the **sa** login, see [Change Server Authentication Mode](../../database-engine/configure-windows/change-server-authentication-mode.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="aba31-182">使用者動作</span><span class="sxs-lookup"><span data-stu-id="aba31-182">User Action</span></span>  
 <span data-ttu-id="aba31-183">如果您正嘗試使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證進行連接，請確定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 是在混合驗證模式下設定。</span><span class="sxs-lookup"><span data-stu-id="aba31-183">If you are trying to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, verify that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is configured in Mixed Authentication Mode.</span></span>  
  
 <span data-ttu-id="aba31-184">如果您正嘗試使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證進行連接，請確定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入存在而且您的拼字正確無誤。</span><span class="sxs-lookup"><span data-stu-id="aba31-184">If you are trying to connect using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, verify that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login exists and that you have spelled it properly.</span></span>  
  
 <span data-ttu-id="aba31-185">如果您正嘗試使用 Windows 驗證進行連接，請確定您已適當地登入正確的網域。</span><span class="sxs-lookup"><span data-stu-id="aba31-185">If you are trying to connect using Windows Authentication, verify that you are properly logged into the correct domain.</span></span>  
  
 <span data-ttu-id="aba31-186">如果您的錯誤表示狀態 1，請連絡 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理員。</span><span class="sxs-lookup"><span data-stu-id="aba31-186">If your error indicates state 1, contact your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administrator.</span></span>  
  
 <span data-ttu-id="aba31-187">如果您正嘗試使用系統管理員認證進行連接，請使用 [以系統管理員身分執行] 選項啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="aba31-187">If you are trying to connect using your administrator credentials, start you application by using the **Run as Administrator** option.</span></span> <span data-ttu-id="aba31-188">連接之後，請將您的 Windows 使用者當做個別登入加入。</span><span class="sxs-lookup"><span data-stu-id="aba31-188">When connected, add your Windows user as an individual login.</span></span>  
  
 <span data-ttu-id="aba31-189">如果 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 支援自主資料庫，請確認在移轉至自主資料庫使用者之後，登入不會遭到刪除。</span><span class="sxs-lookup"><span data-stu-id="aba31-189">If the [!INCLUDE[ssDE](../../includes/ssde-md.md)] supports contained databases, confirm that the login was not deleted after migration to a contained database user.</span></span>  
  
 <span data-ttu-id="aba31-190">本機連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體時，如果要從以 **NT AUTHORITY\NETWORK SERVICE** 執行的服務來連線，則必須使用電腦的完整網域名稱進行驗證。</span><span class="sxs-lookup"><span data-stu-id="aba31-190">When connecting locally to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], connections from services running under **NT AUTHORITY\NETWORK SERVICE** must authenticate using the computers fully qualified domain name.</span></span> <span data-ttu-id="aba31-191">如需詳細資訊，請參閱本主題中的[如何：使用網路服務帳戶存取 ASP.NET 中的資源](https://msdn.microsoft.com/library/ff647402.aspx)</span><span class="sxs-lookup"><span data-stu-id="aba31-191">For more information, see [How To: Use the Network Service Account to Access Resources in ASP.NET](https://msdn.microsoft.com/library/ff647402.aspx)</span></span>  
  
  
