---
title: 建立伺服器稽核與伺服器稽核規格 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.SQLAUDIT.FILTER.F1
- sql12.swb.sqlaudit.srvaudit.general.f1
- sql12.swb.sqlaudit.general.f1
helpviewer_keywords:
- server audit [SQL Server]
- audits [SQL Server], specification
ms.assetid: 6624b1ab-7ec8-44ce-8292-397edf644394
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: a648a975ae9f2c4139a8ebd584f6998f4d0fa1a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700960"
---
# <a name="create-a-server-audit-and-server-audit-specification"></a><span data-ttu-id="817c9-102">建立伺服器稽核與伺服器稽核規格</span><span class="sxs-lookup"><span data-stu-id="817c9-102">Create a Server Audit and Server Audit Specification</span></span>
  <span data-ttu-id="817c9-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中建立伺服器稽核和伺服器稽核規格。</span><span class="sxs-lookup"><span data-stu-id="817c9-103">This topic describes how to create a server audit and server audit specification in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="817c9-104">*「稽核」* (Audit) [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 或 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫的執行個體牽涉到追蹤和記錄系統上所發生的事件。</span><span class="sxs-lookup"><span data-stu-id="817c9-104">*Auditing* an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database involves tracking and logging events that occur on the system.</span></span> <span data-ttu-id="817c9-105">*SQL Server Audit* 物件會收集要監視之伺服器或資料庫層級動作和動作群組的單一執行個體。</span><span class="sxs-lookup"><span data-stu-id="817c9-105">The *SQL Server Audit* object collects a single instance of server- or database-level actions and groups of actions to monitor.</span></span> <span data-ttu-id="817c9-106">此稽核位於 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體層級。</span><span class="sxs-lookup"><span data-stu-id="817c9-106">The audit is at the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance level.</span></span> <span data-ttu-id="817c9-107">您可以針對每個 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體設有多個稽核。</span><span class="sxs-lookup"><span data-stu-id="817c9-107">You can have multiple audits per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="817c9-108">*「伺服器稽核規格」* (Server Audit Specification) 物件屬於稽核。</span><span class="sxs-lookup"><span data-stu-id="817c9-108">The *Server Audit Specification* object belongs to an audit.</span></span> <span data-ttu-id="817c9-109">您可以針對每個稽核建立一個伺服器稽核規格，因為這兩者都是在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體範圍所建立。</span><span class="sxs-lookup"><span data-stu-id="817c9-109">You can create one server audit specification per audit, because both are created at the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance scope.</span></span> <span data-ttu-id="817c9-110">如需詳細資訊，請參閱 [SQL Server Audit &#40;Database Engine&#41;](sql-server-audit-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="817c9-110">For more information, see [SQL Server Audit &#40;Database Engine&#41;](sql-server-audit-database-engine.md).</span></span>  
  
 <span data-ttu-id="817c9-111">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="817c9-111">**In This Topic**</span></span>  
  
-   <span data-ttu-id="817c9-112">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="817c9-112">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="817c9-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="817c9-113">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="817c9-114">安全性</span><span class="sxs-lookup"><span data-stu-id="817c9-114">Security</span></span>](#Security)  
  
-   <span data-ttu-id="817c9-115">**若要使用下列項目建立伺服器稽核和伺服器稽核規格：**</span><span class="sxs-lookup"><span data-stu-id="817c9-115">**To create a server audit and server audit specification, using:**</span></span>  
  
     [<span data-ttu-id="817c9-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="817c9-116">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="817c9-117">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="817c9-117">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="817c9-118">開始之前</span><span class="sxs-lookup"><span data-stu-id="817c9-118">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="817c9-119">限制事項</span><span class="sxs-lookup"><span data-stu-id="817c9-119">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="817c9-120">在您為它建立伺服器稽核規格之前，必須有稽核存在。</span><span class="sxs-lookup"><span data-stu-id="817c9-120">An audit must exist before creating a server audit specification for it.</span></span> <span data-ttu-id="817c9-121">當建立伺服器稽核規格之後，它就會處於停用狀態。</span><span class="sxs-lookup"><span data-stu-id="817c9-121">When a server audit specification is created, it is in a disabled state.</span></span>  
  
-   <span data-ttu-id="817c9-122">CREATE SERVER AUDIT 陳述式位於交易的範圍內。</span><span class="sxs-lookup"><span data-stu-id="817c9-122">The CREATE SERVER AUDIT statement is in a transaction's scope.</span></span> <span data-ttu-id="817c9-123">如果回復交易，也會回復此陳述式。</span><span class="sxs-lookup"><span data-stu-id="817c9-123">If the transaction is rolled back, the statement is also rolled back.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="817c9-124">Security</span><span class="sxs-lookup"><span data-stu-id="817c9-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="817c9-125">權限</span><span class="sxs-lookup"><span data-stu-id="817c9-125">Permissions</span></span>  
  
-   <span data-ttu-id="817c9-126">若要建立、更改或卸除伺服器稽核，主體需要使用 ALTER ANY SERVER AUDIT 或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="817c9-126">To create, alter, or drop a server audit, principals require the ALTER ANY SERVER AUDIT or the CONTROL SERVER permission.</span></span>  
  
-   <span data-ttu-id="817c9-127">具有 ALTER ANY SERVER AUDIT 權限的使用者可以建立伺服器稽核規格，並將其繫結至任何稽核。</span><span class="sxs-lookup"><span data-stu-id="817c9-127">Users with the ALTER ANY SERVER AUDIT permission can create server audit specifications and bind them to any audit.</span></span>  
  
-   <span data-ttu-id="817c9-128">一旦建立伺服器稽核規格之後，就可以使用具有 CONTROL SERVER 或 ALTER ANY SERVER AUDIT 權限的主體、系統管理員 (sysadmin) 帳戶或具有此稽核之明確存取權的主體來加以檢視。</span><span class="sxs-lookup"><span data-stu-id="817c9-128">After a server audit specification is created, it can be viewed by principals with the CONTROL SERVER or ALTER ANY SERVER AUDIT permissions, the sysadmin account, or principals having explicit access to the audit.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="817c9-129">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="817c9-129">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-server-audit"></a><span data-ttu-id="817c9-130">若要建立伺服器稽核</span><span class="sxs-lookup"><span data-stu-id="817c9-130">To create a server audit</span></span>  
  
1.  <span data-ttu-id="817c9-131">在 [物件總管] 中，展開 **[安全性]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="817c9-131">In Object Explorer, expand the **Security** folder.</span></span>  
  
2.  <span data-ttu-id="817c9-132">以滑鼠右鍵按一下 [稽核]  資料夾，然後選取 [新增稽核]  。</span><span class="sxs-lookup"><span data-stu-id="817c9-132">Right-click the **Audits** folder and select **New Audit...**.</span></span>  
  
     <span data-ttu-id="817c9-133">下列選項可從 **[建立稽核]** 對話方塊的 **[一般]** 頁面取得。</span><span class="sxs-lookup"><span data-stu-id="817c9-133">The following options are available on the **General** page of the **Create Audit** dialog box.</span></span>  
  
     <span data-ttu-id="817c9-134">**稽核名稱**</span><span class="sxs-lookup"><span data-stu-id="817c9-134">**Audit name**</span></span>  
     <span data-ttu-id="817c9-135">稽核的名稱。</span><span class="sxs-lookup"><span data-stu-id="817c9-135">The name of the audit.</span></span> <span data-ttu-id="817c9-136">當您建立新的稽核時會自動產生這個名稱，但是可加以編輯。</span><span class="sxs-lookup"><span data-stu-id="817c9-136">This is generated automatically when you create a new audit but is editable.</span></span>  
  
     <span data-ttu-id="817c9-137">**佇列延遲 (以毫秒為單位)**</span><span class="sxs-lookup"><span data-stu-id="817c9-137">**Queue delay (in milliseconds)**</span></span>  
     <span data-ttu-id="817c9-138">指定在強制處理稽核動作之前經過的時間長度 (以毫秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="817c9-138">Specifies the amount of time in milliseconds that can elapse before audit actions are forced to be processed.</span></span>  <span data-ttu-id="817c9-139">值為 0 表示同步傳遞。</span><span class="sxs-lookup"><span data-stu-id="817c9-139">A value of 0 indicates synchronous delivery.</span></span> <span data-ttu-id="817c9-140">預設的最小值為 **1000** (1 秒鐘)。</span><span class="sxs-lookup"><span data-stu-id="817c9-140">The default minimum value is **1000** (1 second).</span></span> <span data-ttu-id="817c9-141">最大值為 2,147,483,647 (2,147,483.647 秒鐘或是 24 天 20 小時 31 分鐘又 23.647 秒鐘)。</span><span class="sxs-lookup"><span data-stu-id="817c9-141">The maximum is 2,147,483,647 (2,147,483.647 seconds or 24 days, 20 hours, 31 minutes, 23.647 seconds).</span></span>  
  
     <span data-ttu-id="817c9-142">**於稽核記錄失敗時:**</span><span class="sxs-lookup"><span data-stu-id="817c9-142">**On Audit Log Failure:**</span></span>  
     <span data-ttu-id="817c9-143">**繼續**</span><span class="sxs-lookup"><span data-stu-id="817c9-143">**Continue**</span></span>  
     [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="817c9-144">作業繼續進行。</span><span class="sxs-lookup"><span data-stu-id="817c9-144">operations continue.</span></span> <span data-ttu-id="817c9-145">系統不會保留稽核記錄。</span><span class="sxs-lookup"><span data-stu-id="817c9-145">Audit records are not retained.</span></span> <span data-ttu-id="817c9-146">稽核會繼續嘗試記錄事件，而且如果失敗狀況已解決，就會恢復稽核。</span><span class="sxs-lookup"><span data-stu-id="817c9-146">The audit continues to attempt to log events and will resume if the failure condition is resolved.</span></span> <span data-ttu-id="817c9-147">選取 **[繼續]** 選項會允許可能違反安全性原則的未稽核活動。</span><span class="sxs-lookup"><span data-stu-id="817c9-147">Selecting the **Continue** option can allow unaudited activity which could violate your security policies.</span></span> <span data-ttu-id="817c9-148">當繼續進行 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 作業比維持完整稽核更重要時，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="817c9-148">Select this option when continuing operation of the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] is more important than maintaining a complete audit.</span></span> <span data-ttu-id="817c9-149">這是預設選項。</span><span class="sxs-lookup"><span data-stu-id="817c9-149">This is the default selection.</span></span>  
  
     <span data-ttu-id="817c9-150">**關閉伺服器**</span><span class="sxs-lookup"><span data-stu-id="817c9-150">**Shut down server**</span></span>  
     <span data-ttu-id="817c9-151">當寫入目標的伺服器執行個體無法將資料寫入稽核目標時，強制伺服器關閉。</span><span class="sxs-lookup"><span data-stu-id="817c9-151">Forces a server shut down when the server instance writing to the target cannot write data to the audit target.</span></span> <span data-ttu-id="817c9-152">發出此內容的登入必須具有 `SHUTDOWN` 權限。</span><span class="sxs-lookup"><span data-stu-id="817c9-152">The login issuing this must have the `SHUTDOWN` permission.</span></span> <span data-ttu-id="817c9-153">如果登入沒有此權限，這個功能將會失敗，而且將會引發錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="817c9-153">If the logon does not have this permission, this function will fail and an error message will be raised.</span></span> <span data-ttu-id="817c9-154">不會發生稽核的事件。</span><span class="sxs-lookup"><span data-stu-id="817c9-154">No audited events occur.</span></span> <span data-ttu-id="817c9-155">當稽核失敗可能危害系統的安全性或完整性時，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="817c9-155">Select this option when an audit failure could compromise the security or integrity of the system.</span></span>  
  
     <span data-ttu-id="817c9-156">**讓作業失敗**</span><span class="sxs-lookup"><span data-stu-id="817c9-156">**Fail operation**</span></span>  
     <span data-ttu-id="817c9-157">當 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit 無法寫入稽核記錄時，如果資料庫動作會以其他方式導致稽核事件，這個選項就會讓這些動作失敗。</span><span class="sxs-lookup"><span data-stu-id="817c9-157">In cases where the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit cannot write to the audit log this option causes database actions to fail if they would otherwise cause audited events.</span></span> <span data-ttu-id="817c9-158">不會發生稽核的事件。</span><span class="sxs-lookup"><span data-stu-id="817c9-158">No audited events occur.</span></span> <span data-ttu-id="817c9-159">不會導致稽核事件的動作可繼續進行。</span><span class="sxs-lookup"><span data-stu-id="817c9-159">Actions which do not cause audited events can continue.</span></span> <span data-ttu-id="817c9-160">稽核會繼續嘗試記錄事件，而且如果失敗狀況已解決，就會恢復稽核。</span><span class="sxs-lookup"><span data-stu-id="817c9-160">The audit continues to attempt to log events and will resume if the failure condition is resolved.</span></span> <span data-ttu-id="817c9-161">當維持完整稽核比 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的完整存取權更重要時，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="817c9-161">Select this option when maintaining a complete audit is more important than full access to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="817c9-162">當稽核處於失敗狀態時，專用管理員連接可以繼續執行稽核事件。</span><span class="sxs-lookup"><span data-stu-id="817c9-162">When the audit is in a failed state, the Dedicated Administrator Connection can continue to perform audited events.</span></span>  
  
     <span data-ttu-id="817c9-163">[稽核目的地]  清單</span><span class="sxs-lookup"><span data-stu-id="817c9-163">**Audit destination** list</span></span>  
     <span data-ttu-id="817c9-164">指定稽核資料的目標。</span><span class="sxs-lookup"><span data-stu-id="817c9-164">Specifies the target for auditing data.</span></span> <span data-ttu-id="817c9-165">可用的選項有二進位檔案、Windows 應用程式記錄檔或 Windows 安全性記錄檔。</span><span class="sxs-lookup"><span data-stu-id="817c9-165">The available options are a binary file, the Windows Application log, or the Windows Security log.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="817c9-166">就無法寫入 Windows 安全性記錄檔。</span><span class="sxs-lookup"><span data-stu-id="817c9-166">cannot write to the Windows Security log without configuring additional settings in Windows.</span></span> <span data-ttu-id="817c9-167">如需詳細資訊，請參閱 [將 SQL Server Audit 事件寫入安全性記錄檔](write-sql-server-audit-events-to-the-security-log.md)。</span><span class="sxs-lookup"><span data-stu-id="817c9-167">For more information, see [Write SQL Server Audit Events to the Security Log](write-sql-server-audit-events-to-the-security-log.md).</span></span>  
  
     <span data-ttu-id="817c9-168">**檔案路徑**</span><span class="sxs-lookup"><span data-stu-id="817c9-168">**File path**</span></span>  
     <span data-ttu-id="817c9-169">指定當 [稽核目的地]  為檔案時，要寫入稽核資料的資料夾位置。</span><span class="sxs-lookup"><span data-stu-id="817c9-169">Specifies the location of the folder where audit data is written when the **Audit destination** is a file.</span></span>  
  
     <span data-ttu-id="817c9-170">**省略符號 (...)**</span><span class="sxs-lookup"><span data-stu-id="817c9-170">**Ellipsis (...)**</span></span>  
     <span data-ttu-id="817c9-171">開啟 [**尋找資料夾-**_server_name_ ] 對話方塊，指定檔案路徑或建立用來寫入 audit 檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="817c9-171">Opens the **Locate Folder -**_server_name_ dialog box to specify a file path or create a folder where the audit file is written.</span></span>  
  
     <span data-ttu-id="817c9-172">**稽核檔案最大限制:**</span><span class="sxs-lookup"><span data-stu-id="817c9-172">**Audit File Maximum Limit:**</span></span>  
     <span data-ttu-id="817c9-173">**輪用檔案數量上限**</span><span class="sxs-lookup"><span data-stu-id="817c9-173">**Maximum rollover files**</span></span>  
     <span data-ttu-id="817c9-174">指定在達到最大稽核檔案數目時，新的檔案內容就會覆寫最舊的稽核檔案。</span><span class="sxs-lookup"><span data-stu-id="817c9-174">Specifies that, when the maximum number of audit files is reached, the oldest audit files are overwritten by new file content.</span></span>  
  
     <span data-ttu-id="817c9-175">**檔案上限**</span><span class="sxs-lookup"><span data-stu-id="817c9-175">**Maximum files**</span></span>  
     <span data-ttu-id="817c9-176">指定在達到最大稽核檔案數目時，導致系統產生其他稽核事件的任何動作都將失敗並發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="817c9-176">Specifies that, when the maximum number of audit files is reached, any action that causes additional audit events to be generated will fail with an error.</span></span>  
  
     <span data-ttu-id="817c9-177">[無限制]  核取方塊</span><span class="sxs-lookup"><span data-stu-id="817c9-177">**Unlimited** check box</span></span>  
     <span data-ttu-id="817c9-178">若已選取 [最大換用檔案]  底下的 [無限制]  核取方塊，則要建立的稽核檔案數目就不受限制。</span><span class="sxs-lookup"><span data-stu-id="817c9-178">When the **Unlimited** check box under **Maximum rollover files** is selected, there is no limit imposed on the number of audit files that will be created.</span></span> <span data-ttu-id="817c9-179">**[無限制]** 核取方塊預設為已選取，並套用至 **[輪用檔案數量上限]** 和 **[檔案數量上限]** 選項。</span><span class="sxs-lookup"><span data-stu-id="817c9-179">The **Unlimited** check box is selected by default and applies to both the **Maximum rollover files** and **Maximum files** selections.</span></span>  
  
     <span data-ttu-id="817c9-180">[檔案數目]  方塊</span><span class="sxs-lookup"><span data-stu-id="817c9-180">**Number of files** box</span></span>  
     <span data-ttu-id="817c9-181">指定要建立的稽核檔案數目，上限為 2,147,483,647。</span><span class="sxs-lookup"><span data-stu-id="817c9-181">Specifies the number of audit files to be created, up to 2,147,483,647.</span></span> <span data-ttu-id="817c9-182">只有未核取 **[無限制]** 時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="817c9-182">This option is only available if **Unlimited** is unchecked.</span></span>  
  
     <span data-ttu-id="817c9-183">**檔案大小上限**</span><span class="sxs-lookup"><span data-stu-id="817c9-183">**Maximum file size**</span></span>  
     <span data-ttu-id="817c9-184">指定稽核檔案的大小上限，以 MB、GB 或 TB 為單位。</span><span class="sxs-lookup"><span data-stu-id="817c9-184">Specifies the maximum size for an audit file in either megabytes (MB), gigabytes (GB), or terabytes (TB).</span></span> <span data-ttu-id="817c9-185">您可以指定介於 1024 MB 和 2,147,483,647 TB 之間的值。</span><span class="sxs-lookup"><span data-stu-id="817c9-185">You can specify between 1024 MB and 2,147,483,647 TB.</span></span> <span data-ttu-id="817c9-186">選取 **[無限制]** 核取方塊並不會限制檔案大小。</span><span class="sxs-lookup"><span data-stu-id="817c9-186">Selecting the **Unlimited** check box does not place a limit on the size of the file.</span></span> <span data-ttu-id="817c9-187">指定低於 1024 MB 的值將會失敗並傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="817c9-187">Specifying a value lower than 1024 MB will fail, returning an error.</span></span> <span data-ttu-id="817c9-188">依預設， **[無限制]** 核取方塊已選取。</span><span class="sxs-lookup"><span data-stu-id="817c9-188">The **Unlimited** check box is selected by default.</span></span>  
  
     <span data-ttu-id="817c9-189">[保留磁碟空間]  核取方塊</span><span class="sxs-lookup"><span data-stu-id="817c9-189">**Reserve disk space** check box</span></span>  
     <span data-ttu-id="817c9-190">指定在磁碟上預先配置的空間等於指定的檔案大小上限。</span><span class="sxs-lookup"><span data-stu-id="817c9-190">Specifies that space is pre-allocated on the disk equal to the specified maximum file size.</span></span> <span data-ttu-id="817c9-191">只有未選取 **[檔案大小上限]** 底下的 **[無限制]** 核取方塊時，才能使用此設定。</span><span class="sxs-lookup"><span data-stu-id="817c9-191">This setting can only be used if the **Unlimited** check box under **Maximum file size** is not selected.</span></span> <span data-ttu-id="817c9-192">依預設，這個核取方塊未選取。</span><span class="sxs-lookup"><span data-stu-id="817c9-192">This check box is not selected by default.</span></span>  
  
3.  <span data-ttu-id="817c9-193">選擇性地在 **[篩選]** 頁面上，對伺服器稽核輸入述詞或 `WHERE` 子句，以指定 **[一般]** 頁面上未提供的其他選項。</span><span class="sxs-lookup"><span data-stu-id="817c9-193">Optionally, on the **Filter** page, enter a predicate, or `WHERE` clause, to the server audit to specify additional options not available from the **General** page.</span></span> <span data-ttu-id="817c9-194">將述詞包含在括號內，例如 `(object_name = 'EmployeesTable')`。</span><span class="sxs-lookup"><span data-stu-id="817c9-194">Enclose the predicate in parentheses; for example: `(object_name = 'EmployeesTable')`.</span></span>  
  
4.  <span data-ttu-id="817c9-195">當您完成選取選項之後，按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="817c9-195">When you are finished selecting options, click **OK**.</span></span>  
  
#### <a name="to-create-a-server-audit-specification"></a><span data-ttu-id="817c9-196">若要建立伺服器稽核規格</span><span class="sxs-lookup"><span data-stu-id="817c9-196">To create a server audit specification</span></span>  
  
1.  <span data-ttu-id="817c9-197">在 [物件總管] 中，按一下加號展開 **[安全性]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="817c9-197">In Object Explorer, click the plus sign to expand the **Security** folder.</span></span>  
  
2.  <span data-ttu-id="817c9-198">以滑鼠右鍵按一下 [伺服器稽核規格]  資料夾，然後選取 [新增伺服器稽核規格]  。</span><span class="sxs-lookup"><span data-stu-id="817c9-198">Right-click the **Server Audit Specifications** folder and select **New Server Audit Specification...**.</span></span>  
  
     <span data-ttu-id="817c9-199">**[建立伺服器稽核規格]** 對話方塊有下列選項。</span><span class="sxs-lookup"><span data-stu-id="817c9-199">The following options are available on the **Create Server Audit Specification** dialog box.</span></span>  
  
     <span data-ttu-id="817c9-200">**名稱**</span><span class="sxs-lookup"><span data-stu-id="817c9-200">**Name**</span></span>  
     <span data-ttu-id="817c9-201">伺服器稽核規格的名稱。</span><span class="sxs-lookup"><span data-stu-id="817c9-201">The name of the server audit specification.</span></span> <span data-ttu-id="817c9-202">當您建立新的伺服器稽核規格時會自動產生這個名稱，但是可加以編輯。</span><span class="sxs-lookup"><span data-stu-id="817c9-202">This is generated automatically when you create a new server audit specification but is editable.</span></span>  
  
     <span data-ttu-id="817c9-203">**稽核**</span><span class="sxs-lookup"><span data-stu-id="817c9-203">**Audit**</span></span>  
     <span data-ttu-id="817c9-204">現有伺服器稽核的名稱。</span><span class="sxs-lookup"><span data-stu-id="817c9-204">The name of an existing server audit.</span></span> <span data-ttu-id="817c9-205">請輸入稽核名稱或從清單中選取。</span><span class="sxs-lookup"><span data-stu-id="817c9-205">Either type in the name of the audit or select it from the list.</span></span>  
  
     <span data-ttu-id="817c9-206">**稽核動作類型**</span><span class="sxs-lookup"><span data-stu-id="817c9-206">**Audit Action Type**</span></span>  
     <span data-ttu-id="817c9-207">指定要擷取之伺服器層級的稽核動作群組和稽核動作。</span><span class="sxs-lookup"><span data-stu-id="817c9-207">Specifies the server-level audit action groups and audit actions to capture.</span></span> <span data-ttu-id="817c9-208">如需資料庫層級的稽核動作群組和稽核動作清單以及其所包含的事件描述，請參閱 [SQL Server Audit 動作群組和動作](sql-server-audit-action-groups-and-actions.md)。</span><span class="sxs-lookup"><span data-stu-id="817c9-208">For the list of server-level audit action groups and audit actions and a description of the events they contain, see [SQL Server Audit Action Groups and Actions](sql-server-audit-action-groups-and-actions.md).</span></span>  
  
     <span data-ttu-id="817c9-209">**物件結構描述**</span><span class="sxs-lookup"><span data-stu-id="817c9-209">**Object Schema**</span></span>  
     <span data-ttu-id="817c9-210">顯示指定之 [物件名稱]  的結構描述。</span><span class="sxs-lookup"><span data-stu-id="817c9-210">Displays the schema for the specified **Object Name**.</span></span>  
  
     <span data-ttu-id="817c9-211">**Object Name**</span><span class="sxs-lookup"><span data-stu-id="817c9-211">**Object Name**</span></span>  
     <span data-ttu-id="817c9-212">要稽核的物件名稱。</span><span class="sxs-lookup"><span data-stu-id="817c9-212">The name of the object to audit.</span></span> <span data-ttu-id="817c9-213">這只適用於稽核動作，不適用於稽核群組。</span><span class="sxs-lookup"><span data-stu-id="817c9-213">This is only available for audit actions; it does not apply to audit groups.</span></span>  
  
     <span data-ttu-id="817c9-214">**省略符號 (...)**</span><span class="sxs-lookup"><span data-stu-id="817c9-214">**Ellipsis (...)**</span></span>  
     <span data-ttu-id="817c9-215">開啟 **[選取物件]** 對話方塊來瀏覽及選取可用的物件 (根據指定的 **[稽核動作類型]** )。</span><span class="sxs-lookup"><span data-stu-id="817c9-215">Opens the **Select Objects** dialog to browse for and select an available object, based on the specified **Audit Action Type**.</span></span>  
  
     <span data-ttu-id="817c9-216">**主體名稱**</span><span class="sxs-lookup"><span data-stu-id="817c9-216">**Principal Name**</span></span>  
     <span data-ttu-id="817c9-217">依據所稽核的物件來篩選稽核的帳戶。</span><span class="sxs-lookup"><span data-stu-id="817c9-217">The account to filter the audit by for the object being audited.</span></span>  
  
     <span data-ttu-id="817c9-218">**省略符號 (...)**</span><span class="sxs-lookup"><span data-stu-id="817c9-218">**Ellipsis (...)**</span></span>  
     <span data-ttu-id="817c9-219">開啟 **[選取物件]** 對話方塊來瀏覽及選取可用的物件 (根據指定的 **[物件名稱]** )。</span><span class="sxs-lookup"><span data-stu-id="817c9-219">Opens the **Select Objects** dialog to browse for and select an available object, based on the specified **Object Name**.</span></span>  
  
3.  <span data-ttu-id="817c9-220">完成時，請按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="817c9-220">When you are finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="817c9-221">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="817c9-221">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-server-audit"></a><span data-ttu-id="817c9-222">若要建立伺服器稽核</span><span class="sxs-lookup"><span data-stu-id="817c9-222">To create a server audit</span></span>  
  
1.  <span data-ttu-id="817c9-223">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="817c9-223">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="817c9-224">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="817c9-224">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="817c9-225">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="817c9-225">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Creates a server audit called "HIPAA_Audit" with a binary file as the target and no options.  
    CREATE SERVER AUDIT HIPAA_Audit  
        TO FILE ( FILEPATH ='\\SQLPROD_1\Audit\' );  
    ```  
  
#### <a name="to-create-a-server-audit-specification"></a><span data-ttu-id="817c9-226">若要建立伺服器稽核規格</span><span class="sxs-lookup"><span data-stu-id="817c9-226">To create a server audit specification</span></span>  
  
1.  <span data-ttu-id="817c9-227">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。</span><span class="sxs-lookup"><span data-stu-id="817c9-227">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="817c9-228">在標準列上，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="817c9-228">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="817c9-229">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="817c9-229">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    /*Creates a server audit specification called "HIPAA_Audit_Specification" that audits failed logins for the SQL Server audit "HIPAA_Audit" created above.  
    */  
  
    CREATE SERVER AUDIT SPECIFICATION HIPAA_Audit_Specification  
    FOR SERVER AUDIT HIPAA_Audit  
        ADD (FAILED_LOGIN_GROUP);  
    GO  
    -- Enables the audit.   
  
    ALTER SERVER AUDIT HIPAA_Audit  
    WITH (STATE = ON);  
    GO  
    ```  
  
 <span data-ttu-id="817c9-230">如需詳細資訊，請參閱 [CREATE SERVER AUDIT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-audit-transact-sql) 和 [CREATE SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-audit-specification-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="817c9-230">For more information, see [CREATE SERVER AUDIT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-audit-transact-sql) and [CREATE SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-audit-specification-transact-sql).</span></span>  
  
  
