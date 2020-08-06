---
title: 在 SSMS 中管理 DQS 使用者 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 955af01d-00da-4c51-9311-f3848749df54
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: bf8789abb59d168f39562f6486bb5c54bfc0fc50
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599676"
---
# <a name="manage-dqs-users-in-ssms"></a><span data-ttu-id="6fb7e-102">在 SSMS 中管理 DQS 使用者</span><span class="sxs-lookup"><span data-stu-id="6fb7e-102">Manage DQS Users in SSMS</span></span>
  <span data-ttu-id="6fb7e-103">此主題描述如何使用 SQL Server Management Studio 在 SQL Server 執行個體中建立其他使用者，並為其授與 DQS_MAIN 資料庫的適當 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 角色。</span><span class="sxs-lookup"><span data-stu-id="6fb7e-103">This topic describes how to create additional users in the SQL Server instance using SQL Server Management Studio, and grant them appropriate [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) roles on the DQS_MAIN database.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6fb7e-104">開始之前</span><span class="sxs-lookup"><span data-stu-id="6fb7e-104">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6fb7e-105">Security</span><span class="sxs-lookup"><span data-stu-id="6fb7e-105">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6fb7e-106">權限</span><span class="sxs-lookup"><span data-stu-id="6fb7e-106">Permissions</span></span>  
 <span data-ttu-id="6fb7e-107">您的 Windows 使用者帳戶必須是適當固定伺服器角色 (例如 securityadmin、serveradmin 或 sysadmin) 的成員，才能建立 SQL 登入並授與適當的 DQS 角色。</span><span class="sxs-lookup"><span data-stu-id="6fb7e-107">Your Windows user account must be a member of the appropriate fixed server role (such as securityadmin, serveradmin, or sysadmin) to create SQL login, and grant appropriate DQS roles.</span></span>  
  
##  <a name="create-a-sql-login-and-grant-dqs-role"></a><a name="GrantRoles"></a><span data-ttu-id="6fb7e-108">建立 SQL 登入並授與 DQS 角色</span><span class="sxs-lookup"><span data-stu-id="6fb7e-108">Create a SQL Login and Grant DQS Role</span></span>  
  
1.  <span data-ttu-id="6fb7e-109">啟動 Microsoft SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="6fb7e-109">Start Microsoft SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="6fb7e-110">在 Microsoft SQL Server Management Studio 中，展開您的 SQL Server 執行個體，然後展開 **[安全性]**。</span><span class="sxs-lookup"><span data-stu-id="6fb7e-110">In Microsoft SQL Server Management Studio, expand your SQL Server instance, and then expand **Security**.</span></span>  
  
3.  <span data-ttu-id="6fb7e-111">以滑鼠右鍵按一下 [安全性]\*\*\*\* 資料夾，並指向 [新增]\*\*\*\*，然後按一下 [登入]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="6fb7e-111">Right-click the **Security** folder, point to **New**, and then click **Login**.</span></span>  
  
4.  <span data-ttu-id="6fb7e-112">在 [登入 - 新增]\*\*\*\* 對話方塊的 [登入名稱]\*\*\*\* 方塊中，指定 Windows 使用者的名稱，指定 [Windows 驗證]\*\*\*\* 做為驗證類型，然後按一下 [搜尋]\*\*\*\* 驗證使用者。</span><span class="sxs-lookup"><span data-stu-id="6fb7e-112">In the **Login - New** dialog box, specify the name of a Windows user in the **Login name** box, specify the type of authentication as **Windows authentication**, and click **Search** to validate the user.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6fb7e-113">DQS 僅支援 Windows 驗證，不支援 SQL Server 驗證。</span><span class="sxs-lookup"><span data-stu-id="6fb7e-113">DQS only supports Windows authentication; SQL Server authentication is not supported.</span></span>  
  
5.  <span data-ttu-id="6fb7e-114">使用者驗證完成後，按一下左窗格中的 **[使用者對應]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="6fb7e-114">After the user is validated, click the **User Mapping** page in the left pane.</span></span>  
  
6.  <span data-ttu-id="6fb7e-115">根據使用者所需的存取層級，在右邊的窗格中，從 **DQS_MAIN** 資料庫的 [地圖]\*\*\*\* 資料行選取該核取方塊，然後選取 [資料庫角色成員資格對象: DQS_MAIN]\*\*\*\* 窗格中的 **dqs_administrator**、**dqs_kb_editor** 或 **dqs_kb_operator** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="6fb7e-115">In the right pane, select the check box under the **Map** column for the **DQS_MAIN** database, and then select the **dqs_administrator**, **dqs_kb_editor**, or **dqs_kb_operator** check box in the **Database role membership for: DQS_MAIN** pane, depending on the access level needed for the user.</span></span>  
  
7.  <span data-ttu-id="6fb7e-116">在 [登入 - 新增]\*\*\*\* 對話方塊中，按一下 [確定]\*\*\*\* 套用變更。</span><span class="sxs-lookup"><span data-stu-id="6fb7e-116">In the **Login - New** dialog box, click **OK** to apply the changes.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6fb7e-117">如果您對使用者授與 **dqs_administrator** 角色並套用了變更，然後重新檢查使用者的權限，也會同時選取另外兩個 DQS 角色核取方塊 (**dq_kb_editor** 和 **dqs_kb_operator**)。</span><span class="sxs-lookup"><span data-stu-id="6fb7e-117">If you grant the **dqs_administrator** role to a user, apply the changes, and then recheck the user permissions, the other two DQS roles check boxes (**dq_kb_editor** and **dqs_kb_operator**) are also selected.</span></span>  
  
  
