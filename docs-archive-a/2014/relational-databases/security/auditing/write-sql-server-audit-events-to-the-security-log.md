---
title: 將 SQL Server Audit 事件寫入安全性記錄檔 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], Security Log
- server audit [SQL Server]
- audits [SQL Server], writing to Security Log
- security logs [SQL Server]
ms.assetid: 6fabeea3-7a42-4769-a0f3-7e04daada314
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: d59134b278f29c9b604208d8cab7e982144b9c9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592572"
---
# <a name="write-sql-server-audit-events-to-the-security-log"></a><span data-ttu-id="f30f3-102">將 SQL Server Audit 事件寫入安全性記錄檔</span><span class="sxs-lookup"><span data-stu-id="f30f3-102">Write SQL Server Audit Events to the Security Log</span></span>
  <span data-ttu-id="f30f3-103">在高度安全性的環境中，Windows 安全性記錄檔是寫入記錄物件存取之事件的適當位置。</span><span class="sxs-lookup"><span data-stu-id="f30f3-103">In a high security environment, the Windows Security log is the appropriate location to write events that record object access.</span></span> <span data-ttu-id="f30f3-104">雖然支援其他稽核位置，但是這些位置容易遭算改。</span><span class="sxs-lookup"><span data-stu-id="f30f3-104">Other audit locations are supported but are more subject to tampering.</span></span>  
  
 <span data-ttu-id="f30f3-105">將 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 伺服器稽核寫入 Windows 安全性記錄檔有兩個重要需求：</span><span class="sxs-lookup"><span data-stu-id="f30f3-105">There are two key requirements for writing [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] server audits to the Windows Security log:</span></span>  
  
-   <span data-ttu-id="f30f3-106">稽核物件存取設定必須設定為可擷取事件。</span><span class="sxs-lookup"><span data-stu-id="f30f3-106">The audit object access setting must be configured to capture the events.</span></span> <span data-ttu-id="f30f3-107">稽核原則工具 (`auditpol.exe`) 會在 **audit object access** 類別目錄中公開各種子原則設定。</span><span class="sxs-lookup"><span data-stu-id="f30f3-107">The audit policy tool (`auditpol.exe`) exposes a variety of sub-policies settings in the **audit object access** category.</span></span> <span data-ttu-id="f30f3-108">若要允許 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 稽核物件存取，請設定 **application generated** 設定。</span><span class="sxs-lookup"><span data-stu-id="f30f3-108">To allow [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to audit object access, configure the **application generated** setting.</span></span>  
  
-   <span data-ttu-id="f30f3-109">執行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務所使用的帳戶必須擁有 [產生安全性稽核]  權限，才能寫入 Windows 安全性記錄檔。</span><span class="sxs-lookup"><span data-stu-id="f30f3-109">The account that the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service is running under must have the **generate security audits** permission to write to the Windows Security log.</span></span> <span data-ttu-id="f30f3-110">根據預設，LOCAL SERVICE 和 NETWORK SERVICE 帳戶都擁有這個權限。</span><span class="sxs-lookup"><span data-stu-id="f30f3-110">By default, the LOCAL SERVICE and the NETWORK SERVICE accounts have this permission.</span></span> <span data-ttu-id="f30f3-111">如果 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 是在其中一個帳戶底下執行，就不需要進行這個步驟。</span><span class="sxs-lookup"><span data-stu-id="f30f3-111">This step is not required if [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is running under one of those accounts.</span></span>  
  
 <span data-ttu-id="f30f3-112">如果 Windows 稽核原則設定為寫入 Windows 安全性記錄檔，它就可能會影響 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 稽核，而且如果稽核原則的設定不正確，甚至可能會遺失事件。</span><span class="sxs-lookup"><span data-stu-id="f30f3-112">The Windows audit policy can affect [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auditing if it is configured to write to the Windows Security log, with the potential of losing events if the audit policy is incorrectly configured.</span></span> <span data-ttu-id="f30f3-113">一般而言，Windows 安全性記錄檔會設定為覆寫較舊的事件。</span><span class="sxs-lookup"><span data-stu-id="f30f3-113">Typically, the Windows Security log is set to overwrite the older events.</span></span> <span data-ttu-id="f30f3-114">這樣做會保留最近的事件。</span><span class="sxs-lookup"><span data-stu-id="f30f3-114">This preserves the most recent events.</span></span> <span data-ttu-id="f30f3-115">不過，如果 Windows 安全性記錄檔並非設定為覆寫較舊的事件，只要安全性記錄檔已滿，系統就會發出 Windows 事件 1104 (記錄檔已滿)。</span><span class="sxs-lookup"><span data-stu-id="f30f3-115">However, if the Windows Security log is not set to overwrite older events, then if the Security log is full, the system will issue Windows event 1104 (Log is full).</span></span> <span data-ttu-id="f30f3-116">此時：</span><span class="sxs-lookup"><span data-stu-id="f30f3-116">At that point:</span></span>  
  
-   <span data-ttu-id="f30f3-117">系統將不會記錄其他安全性事件。</span><span class="sxs-lookup"><span data-stu-id="f30f3-117">No further security events will be recorded</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="f30f3-118">將無法偵測出系統無法在安全性記錄檔中記錄事件，進而導致可能遺失稽核事件。</span><span class="sxs-lookup"><span data-stu-id="f30f3-118">will not be able to detect that the system is not able to record the events in the Security log, resulting in the potential loss of audit events</span></span>  
  
-   <span data-ttu-id="f30f3-119">在方塊管理員修正安全性記錄檔之後，記錄行為才會返回正常狀態。</span><span class="sxs-lookup"><span data-stu-id="f30f3-119">After the box administrator fixes the Security log, the logging behavior will return to normal.</span></span>  
  
 <span data-ttu-id="f30f3-120">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="f30f3-120">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f30f3-121">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="f30f3-121">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f30f3-122">限制事項</span><span class="sxs-lookup"><span data-stu-id="f30f3-122">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="f30f3-123">安全性</span><span class="sxs-lookup"><span data-stu-id="f30f3-123">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f30f3-124">**若要將 SQL Server 稽核事件寫入安全性記錄檔：**</span><span class="sxs-lookup"><span data-stu-id="f30f3-124">**To write SQL Server audit events to the Security Log:**</span></span>  
  
     [<span data-ttu-id="f30f3-125">使用 auditpol 在 Windows 中設定稽核物件存取設定</span><span class="sxs-lookup"><span data-stu-id="f30f3-125">Configure the audit object access setting in Windows using auditpol</span></span>](#auditpolAccess)  
  
     [<span data-ttu-id="f30f3-126">使用 secpol 在 Windows 中設定稽核物件存取設定</span><span class="sxs-lookup"><span data-stu-id="f30f3-126">Configure the audit object access setting in Windows using secpol</span></span>](#secpolAccess)  
  
     [<span data-ttu-id="f30f3-127">使用 secpol 將 generate security audits 權限授與帳戶</span><span class="sxs-lookup"><span data-stu-id="f30f3-127">Grant the generate security audits permission to an account using secpol</span></span>](#secpolPermission)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f30f3-128">開始之前</span><span class="sxs-lookup"><span data-stu-id="f30f3-128">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="f30f3-129">限制事項</span><span class="sxs-lookup"><span data-stu-id="f30f3-129">Limitations and Restrictions</span></span>  
 <span data-ttu-id="f30f3-130">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 電腦的管理員應該了解安全性記錄檔的本機設定可以由網域原則覆寫。</span><span class="sxs-lookup"><span data-stu-id="f30f3-130">Administrators of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] computer should understand that local settings for the Security log can be overwritten by a domain policy.</span></span> <span data-ttu-id="f30f3-131">在此情況下，網域原則可能會覆寫子類別目錄設定 (**auditpol /get /subcategory:"application generated"** )。</span><span class="sxs-lookup"><span data-stu-id="f30f3-131">In this case, the domain policy might overwrite the subcategory setting (**auditpol /get /subcategory:"application generated"**).</span></span> <span data-ttu-id="f30f3-132">這可能會影響 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 記錄事件的功能，讓它無法偵測出系統無法繼續記錄 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 正嘗試稽核的事件。</span><span class="sxs-lookup"><span data-stu-id="f30f3-132">This can affect [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ability to log events without having any way to detect that the events that [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is trying to audit are not going to be recorded.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f30f3-133">Security</span><span class="sxs-lookup"><span data-stu-id="f30f3-133">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f30f3-134">權限</span><span class="sxs-lookup"><span data-stu-id="f30f3-134">Permissions</span></span>  
 <span data-ttu-id="f30f3-135">您必須是 Windows 管理員才能設定這些設定。</span><span class="sxs-lookup"><span data-stu-id="f30f3-135">You must be a Windows administrator to configure these settings.</span></span>  
  
##  <a name="to-configure-the-audit-object-access-setting-in-windows-using-auditpol"></a><a name="auditpolAccess"></a> <span data-ttu-id="f30f3-136">使用 auditpol 在 Windows 中設定稽核物件存取設定</span><span class="sxs-lookup"><span data-stu-id="f30f3-136">To configure the audit object access setting in Windows using auditpol</span></span>  
  
1.  <span data-ttu-id="f30f3-137">以系統管理權限開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="f30f3-137">Open a command prompt with administrative permissions.</span></span>  
  
    1.  <span data-ttu-id="f30f3-138">在 [開始] 功能表上，依序指向 [所有程式] 和 [附屬應用程式]、以滑鼠右鍵按一下 [命令提示字元]，然後按一下 [以系統管理員身分執行]。</span><span class="sxs-lookup"><span data-stu-id="f30f3-138">On the **Start** menu, point to **All Programs**, point to **Accessories**, right-click **Command Prompt**, and then click **Run as administrator**.</span></span>  
  
    2.  <span data-ttu-id="f30f3-139">如果開啟 **[使用者帳戶控制]** 對話方塊，請按一下 **[繼續]** 。</span><span class="sxs-lookup"><span data-stu-id="f30f3-139">If the **User Account Control** dialog box opens, click **Continue**.</span></span>  
  
2.  <span data-ttu-id="f30f3-140">執行下列陳述式，以便啟用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]的稽核。</span><span class="sxs-lookup"><span data-stu-id="f30f3-140">Execute the following statement to enable auditing from [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
    ```  
    auditpol /set /subcategory:"application generated" /success:enable /failure:enable  
    ```  
  
3.  <span data-ttu-id="f30f3-141">關閉 [命令提示字元] 視窗。</span><span class="sxs-lookup"><span data-stu-id="f30f3-141">Close the command prompt window.</span></span>  
  
##  <a name="to-grant-the-generate-security-audits-permission-to-an-account-using-secpol"></a><a name="secpolAccess"></a> <span data-ttu-id="f30f3-142">使用 secpol 將 generate security audits 權限授與帳戶</span><span class="sxs-lookup"><span data-stu-id="f30f3-142">To grant the generate security audits permission to an account using secpol</span></span>  
  
1.  <span data-ttu-id="f30f3-143">在任何 Windows 作業系統的 **[開始]** 功能表上，按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="f30f3-143">For any Windows operating system, on the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="f30f3-144">輸入 **secpol.msc** ，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="f30f3-144">Type **secpol.msc** and then click **OK**.</span></span> <span data-ttu-id="f30f3-145">如果出現 **[使用者存取控制]** 對話方塊，請按一下 **[繼續]** 。</span><span class="sxs-lookup"><span data-stu-id="f30f3-145">If the **User Access Control** dialog box appears, click **Continue**.</span></span>  
  
3.  <span data-ttu-id="f30f3-146">在本機安全性原則工具中，依序展開 **[安全性設定]** 和 **[本機原則]** ，然後按一下 **[使用者權限指派]** 。</span><span class="sxs-lookup"><span data-stu-id="f30f3-146">In the Local Security Policy tool, expand **Security Settings**, expand **Local Policies**, and then click **User Rights Assignment**.</span></span>  
  
4.  <span data-ttu-id="f30f3-147">在結果窗格中，按兩下 [產生安全性稽核]。</span><span class="sxs-lookup"><span data-stu-id="f30f3-147">In the results pane, double-click **Generate security audits**.</span></span>  
  
5.  <span data-ttu-id="f30f3-148">在 **[本機安全性設定]** 索引標籤上，按一下 **[新增使用者或群組]** 。</span><span class="sxs-lookup"><span data-stu-id="f30f3-148">On the **Local Security Setting** tab, click **Add User or Group**.</span></span>  
  
6.  <span data-ttu-id="f30f3-149">在 [選取使用者、電腦或群組] 對話方塊中，輸入使用者帳戶的名稱 (例如 **domain1\user1**) 並按一下 [確定]，或按一下 [進階] 並搜尋帳戶。</span><span class="sxs-lookup"><span data-stu-id="f30f3-149">In the **Select Users, Computers, or Groups** dialog box, either type the name of the user account, such as **domain1\user1** and then click **OK**, or click **Advanced** and search for the account.</span></span>  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
8.  <span data-ttu-id="f30f3-150">關閉安全性原則工具。</span><span class="sxs-lookup"><span data-stu-id="f30f3-150">Close the Security Policy tool.</span></span>  
  
9. <span data-ttu-id="f30f3-151">重新啟動 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以啟用此設定。</span><span class="sxs-lookup"><span data-stu-id="f30f3-151">Restart [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to enable this setting.</span></span>  
  
##  <a name="to-configure-the-audit-object-access-setting-in-windows-using-secpol"></a><a name="secpolPermission"></a> <span data-ttu-id="f30f3-152">使用 secpol 在 Windows 中設定稽核物件存取設定</span><span class="sxs-lookup"><span data-stu-id="f30f3-152">To configure the audit object access setting in Windows using secpol</span></span>  
  
1.  <span data-ttu-id="f30f3-153">如果作業系統是 [!INCLUDE[wiprlhext](../../../includes/wiprlhext-md.md)] 或 Windows Server 2008 之前的版本，請在 **[開始]** 功能表上，按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="f30f3-153">If the operating system is earlier than [!INCLUDE[wiprlhext](../../../includes/wiprlhext-md.md)] or Windows Server 2008, on the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="f30f3-154">輸入 **secpol.msc** ，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="f30f3-154">Type **secpol.msc** and then click **OK**.</span></span> <span data-ttu-id="f30f3-155">如果出現 **[使用者存取控制]** 對話方塊，請按一下 **[繼續]** 。</span><span class="sxs-lookup"><span data-stu-id="f30f3-155">If the **User Access Control** dialog box appears, click **Continue**.</span></span>  
  
3.  <span data-ttu-id="f30f3-156">在本機安全性原則工具中，依序展開 **[安全性設定]** 和 **[本機原則]** ，然後按一下 **[稽核原則]** 。</span><span class="sxs-lookup"><span data-stu-id="f30f3-156">In the Local Security Policy tool, expand **Security Settings**, expand **Local Policies**, and then click **Audit Policy**.</span></span>  
  
4.  <span data-ttu-id="f30f3-157">在結果窗格中，按兩下 [稽核物件存取]。</span><span class="sxs-lookup"><span data-stu-id="f30f3-157">In the results pane, double-click **Audit object access**.</span></span>  
  
5.  <span data-ttu-id="f30f3-158">在 **[本機安全性設定]** 索引標籤的 **[稽核這些嘗試]** 區域中，同時選取 **[成功]** 和 **[失敗]** 。</span><span class="sxs-lookup"><span data-stu-id="f30f3-158">On the **Local Security Setting** tab, in the **Audit these attempts** area, select both **Success** and **Failure**.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="f30f3-159">關閉安全性原則工具。</span><span class="sxs-lookup"><span data-stu-id="f30f3-159">Close the Security Policy tool.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f30f3-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f30f3-160">See Also</span></span>  
 [<span data-ttu-id="f30f3-161">SQL Server Audit &#40;Database Engine&#41;</span><span class="sxs-lookup"><span data-stu-id="f30f3-161">SQL Server Audit &#40;Database Engine&#41;</span></span>](sql-server-audit-database-engine.md)  
  
  
