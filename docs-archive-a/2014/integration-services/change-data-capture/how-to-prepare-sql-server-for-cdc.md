---
title: 如何為 CDC 準備 SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a327fa18-58f4-4e69-bb87-44faf47e20ef
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fbd285faaa55a28ad82beb673fa783570809bd04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686459"
---
# <a name="how-to-prepare-sql-server-for-cdc"></a><span data-ttu-id="bc4f1-102">如何為 CDC 準備 SQL Server</span><span class="sxs-lookup"><span data-stu-id="bc4f1-102">How to Prepare SQL Server for CDC</span></span>
  <span data-ttu-id="bc4f1-103">Oracle CDC 服務要求所有目標 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體都必須包含 MSXDBCDC 資料庫。</span><span class="sxs-lookup"><span data-stu-id="bc4f1-103">The Oracle CDC service requires all target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances to contain the MSXDBCDC database.</span></span> <span data-ttu-id="bc4f1-104">您可在 CDC 服務組態主控台中使用「準備 SQL Server」動作來建立這個資料庫。每一個目標 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體只會執行這項工作一次。</span><span class="sxs-lookup"><span data-stu-id="bc4f1-104">You create this database using the Prepare SQL Server action in the CDC Service Configuration Console.This task is done one time only for each target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="bc4f1-105">以下描述如何使用 CDC 服務組態主控台針對 Oracle 異動資料擷取來準備 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="bc4f1-105">The following describes how to prepare a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database for Oracle Change Data Capture using the CDC Service Configuration Console.</span></span> <span data-ttu-id="bc4f1-106">這個程序會建立 MSXDBCDC 資料庫，並定義所需的資料表、預存程序和其他必要成品。</span><span class="sxs-lookup"><span data-stu-id="bc4f1-106">This process creates the MSXDBCDC database and defines the required tables, stored procedures, and other required artifacts.</span></span>  
  
 <span data-ttu-id="bc4f1-107">為 Oracle CDC 準備 SQL Server 是由 Oracle CDC 服務管理員所執行。</span><span class="sxs-lookup"><span data-stu-id="bc4f1-107">Preparing the SQL Server for Oracle CDC is done by the Oracle CDC Service Administrator.</span></span> <span data-ttu-id="bc4f1-108">如需 CDC 服務系統管理員角色的詳細資訊，請參閱[適用於 Oracle 的異動資料擷取服務的使用者角色（依 Attunity](user-roles.md)）。</span><span class="sxs-lookup"><span data-stu-id="bc4f1-108">For more information about the CDC Service Administrator role, see [User Roles for Change Data Capture Service for Oracle by Attunity](user-roles.md).</span></span>  
  
### <a name="to-enable-sql-server-for-cdc"></a><span data-ttu-id="bc4f1-109">若要為 CDC 啟用 SQL Server</span><span class="sxs-lookup"><span data-stu-id="bc4f1-109">To enable SQL Server for CDC</span></span>  
  
1.  <span data-ttu-id="bc4f1-110">從 **[開始]** 功能表，選取 **[Oracle CDC 服務組態]** 。</span><span class="sxs-lookup"><span data-stu-id="bc4f1-110">From the **Start** menu, select the **CDC Service Configuration for Oracle**.</span></span>  
  
2.  <span data-ttu-id="bc4f1-111">從左窗格中選取 **[動作]** 窗格中的 **[本機 CDC 服務]** ，然後按一下 **[準備 SQL Server]** 。</span><span class="sxs-lookup"><span data-stu-id="bc4f1-111">From the left pane, select **Local CDC Services** then from the **Actions** pane, click **Prepare SQL Server**.</span></span>  
  
     <span data-ttu-id="bc4f1-112">您也可以用滑鼠右鍵按一下 [本機 CDC 服務]  ，並選取 [準備 SQL Server]  。</span><span class="sxs-lookup"><span data-stu-id="bc4f1-112">You can also right-click **Local CDC Services** and select **Prepare SQL Server**.</span></span>  
  
3.  <span data-ttu-id="bc4f1-113">請在 [為 Oracle CDC 準備 SQL Server 執行個體] 對話方塊中輸入必要的資訊。</span><span class="sxs-lookup"><span data-stu-id="bc4f1-113">Enter the required information in the Preparing SQL Server Instance for Oracle CDC dialog box.</span></span> <span data-ttu-id="bc4f1-114">如需有關如何在此對話方塊中輸入必要資訊的詳細資訊，請參閱＜ [Prepare SQL Server for CDC](prepare-sql-server-for-cdc.md)＞。</span><span class="sxs-lookup"><span data-stu-id="bc4f1-114">For information on how to enter the required information into this dialog box, see [Prepare SQL Server for CDC](prepare-sql-server-for-cdc.md).</span></span>  
  
     <span data-ttu-id="bc4f1-115">若要為 Oracle CDC 準備 SQL Server 執行個體，登入必須擁有 MSXDBCDC 資料庫的寫入權限。</span><span class="sxs-lookup"><span data-stu-id="bc4f1-115">To Prepare the SQL Server instance for Oracle CDC, the login must have write permission to the MSXDBCDC database.</span></span> <span data-ttu-id="bc4f1-116">請輸入擁有 MSXDBCDC 資料庫寫入權限之登入的認證，例如 `sysasmin` 角色的成員。</span><span class="sxs-lookup"><span data-stu-id="bc4f1-116">Enter the credentials for a login that has write permission to the MSXDBCDC database, such as a member of the `sysasmin` role.</span></span>  
  
 <span data-ttu-id="bc4f1-117">**注意**：您可以按一下 [檢視指令碼]  ，檢視設定指令碼的唯讀版本。</span><span class="sxs-lookup"><span data-stu-id="bc4f1-117">**Note**: You can click **View Script** to view a read-only version of the setup script.</span></span> <span data-ttu-id="bc4f1-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統管理員可以將此指令碼複製到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理主控台來編輯和執行 (必要的話)。</span><span class="sxs-lookup"><span data-stu-id="bc4f1-118">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator can copy this script into the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Console to edit and execute it, if necessary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc4f1-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc4f1-119">See Also</span></span>  
 [<span data-ttu-id="bc4f1-120">準備 SQL Server 以使用 CDC</span><span class="sxs-lookup"><span data-stu-id="bc4f1-120">Prepare SQL Server for CDC</span></span>](prepare-sql-server-for-cdc.md)  
  
  
