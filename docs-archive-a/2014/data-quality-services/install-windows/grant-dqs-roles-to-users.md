---
title: 對使用者授與 DQS 角色 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: afb445b5-bdbe-4bfe-844f-344766cdc2b2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 62ff5eb03fa46279ee1b8a1329c58bd69361ef82
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705437"
---
# <a name="grant-dqs-roles-to-users"></a><span data-ttu-id="2f375-102">對使用者授與 DQS 角色</span><span class="sxs-lookup"><span data-stu-id="2f375-102">Grant DQS Roles to Users</span></span>
  <span data-ttu-id="2f375-103">本主題描述如何根據 Windows 主體建立 SQL 登入，並在 DQS_MAIN 資料庫上授與 [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) 角色。</span><span class="sxs-lookup"><span data-stu-id="2f375-103">This topic describes how to create SQL logins based on a Windows principal, and grant [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) roles on the DQS_MAIN database.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2f375-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="2f375-104">Prerequisites</span></span>  
  
-   <span data-ttu-id="2f375-105">您必須執行 DQSInstaller.exe 檔案，才可以完成 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 的安裝。</span><span class="sxs-lookup"><span data-stu-id="2f375-105">You must have completed the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] installation by running the DQSInstaller.exe file.</span></span> <span data-ttu-id="2f375-106">如需詳細資訊，請參閱 [執行 DQSInstaller.exe 完成 Data Quality Server 安裝](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md)。</span><span class="sxs-lookup"><span data-stu-id="2f375-106">For more information, see [Run DQSInstaller.exe to Complete Data Quality Server Installation](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).</span></span>  
  
-   <span data-ttu-id="2f375-107">您的 Windows 使用者帳戶必須是適當固定伺服器角色 (例如 securityadmin、serveradmin 或 sysadmin) 的成員，才能建立 SQL 登入並授與它們 DQS 角色。</span><span class="sxs-lookup"><span data-stu-id="2f375-107">Your Windows user account must be a member of the appropriate fixed server role (such as securityadmin, serveradmin, or sysadmin) to create SQL login, and grant them DQS roles.</span></span>  
  
### <a name="to-create-sql-login-and-grant-dqs-roles"></a><span data-ttu-id="2f375-108">若要建立 SQL 登入並授與 DQS 角色</span><span class="sxs-lookup"><span data-stu-id="2f375-108">To create SQL login and grant DQS roles</span></span>  
  
1.  <span data-ttu-id="2f375-109">啟動 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2f375-109">Start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="2f375-110">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，展開您的 SQL Server 執行個體，然後展開 **[安全性]**。</span><span class="sxs-lookup"><span data-stu-id="2f375-110">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand your SQL Server instance, and then expand **Security**.</span></span>  
  
3.  <span data-ttu-id="2f375-111">以滑鼠右鍵按一下 [安全性]\*\*\*\* 資料夾，並指向 [新增]\*\*\*\*，然後按一下 [登入]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2f375-111">Right-click the **Security** folder, point to **New**, and then click **Login**.</span></span>  
  
4.  <span data-ttu-id="2f375-112">在 [登入 - 新增]\*\*\*\* 對話方塊的 [登入名稱]\*\*\*\* 方塊中，指定 Windows 使用者的名稱，指定 [Windows 驗證]\*\*\*\* 做為驗證類型，然後按一下 [搜尋]\*\*\*\* 驗證使用者。</span><span class="sxs-lookup"><span data-stu-id="2f375-112">In the **Login - New** dialog box, specify the name of a Windows user in the **Login name** box, specify the type of authentication as **Windows authentication**, and click **Search** to validate the user.</span></span>  
  
5.  <span data-ttu-id="2f375-113">使用者驗證完成後，按一下左窗格中的 **[使用者對應]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="2f375-113">After the user is validated, click the **User Mapping** page in the left pane.</span></span>  
  
6.  <span data-ttu-id="2f375-114">根據使用者所需的存取層級，在右邊的窗格中，從 **DQS_MAIN** 資料庫的 [地圖]\*\*\*\* 資料行選取該核取方塊，然後選取 [資料庫角色成員資格對象: DQS_MAIN]\*\*\*\* 窗格中的 **dqs_administrator**、**dqs_kb_editor** 或 **dqs_kb_operator** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="2f375-114">In the right pane, select the check box under the **Map** column for the **DQS_MAIN** database, and then select the **dqs_administrator**, **dqs_kb_editor**, or **dqs_kb_operator** check box in the **Database role membership for: DQS_MAIN** pane, depending on the access level needed for the user.</span></span> <span data-ttu-id="2f375-115">如需有關三個 DQS 角色的詳細資訊，請參閱＜ [DQS 安全](../dqs-security.md)＞。</span><span class="sxs-lookup"><span data-stu-id="2f375-115">For information about the three DQS roles, see [DQS Security](../dqs-security.md).</span></span>  
  
7.  <span data-ttu-id="2f375-116">在 [登入 - 新增]\*\*\*\* 對話方塊中，按一下 [確定]\*\*\*\* 套用變更。</span><span class="sxs-lookup"><span data-stu-id="2f375-116">In the **Login - New** dialog box, click **OK** to apply the changes.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2f375-117">如果您對使用者授與 **dqs_administrator** 角色並套用了變更，然後重新檢查使用者的權限，也會同時選取另外兩個 DQS 角色核取方塊 (**dq_kb_editor** 和 **dqs_kb_operator**)。</span><span class="sxs-lookup"><span data-stu-id="2f375-117">If you grant the **dqs_administrator** role to a user, apply the changes, and then recheck the user permissions, the other two DQS roles check boxes (**dq_kb_editor** and **dqs_kb_operator**) are also selected.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="2f375-118">後續步驟</span><span class="sxs-lookup"><span data-stu-id="2f375-118">Next Steps</span></span>  
 <span data-ttu-id="2f375-119">嘗試使用您剛才為其建立 SQL 登入並授與 DQS 角色的 Windows 使用者帳戶登入 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2f375-119">Try logging on to [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] by using the Windows user account for which you just created a SQL login, and granted a DQS role.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f375-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f375-120">See Also</span></span>  
 <span data-ttu-id="2f375-121">[安裝 Data Quality Services](install-data-quality-services.md) </span><span class="sxs-lookup"><span data-stu-id="2f375-121">[Install Data Quality Services](install-data-quality-services.md) </span></span>  
 [<span data-ttu-id="2f375-122">建立登入</span><span class="sxs-lookup"><span data-stu-id="2f375-122">Create a Login</span></span>](../../relational-databases/security/authentication-access/create-a-login.md)  
  
  
