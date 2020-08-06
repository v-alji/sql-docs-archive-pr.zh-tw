---
title: 將資料庫設定為單一使用者模式 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- single-user mode [SQL Server], database option
ms.assetid: fb5254eb-b635-4b39-8361-136fd36f2b1f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 16281b5fa7d4f6698bb6c498915bfa84779b3e14
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686973"
---
# <a name="set-a-database-to-single-user-mode"></a><span data-ttu-id="ccfbd-102">將資料庫設定為單一使用者模式</span><span class="sxs-lookup"><span data-stu-id="ccfbd-102">Set a Database to Single-user Mode</span></span>
  <span data-ttu-id="ccfbd-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中將使用者定義資料庫設定為單一使用者模式。</span><span class="sxs-lookup"><span data-stu-id="ccfbd-103">This topic describes how to set a user-defined database to single-user mode in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="ccfbd-104">單一使用者模式指定一次只可有一位使用者存取資料庫，且一般是用於維護動作。</span><span class="sxs-lookup"><span data-stu-id="ccfbd-104">Single-user mode specifies that only one user at a time can access the database and is generally used for maintenance actions.</span></span>  
  
 <span data-ttu-id="ccfbd-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="ccfbd-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ccfbd-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="ccfbd-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ccfbd-107">限制事項</span><span class="sxs-lookup"><span data-stu-id="ccfbd-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="ccfbd-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="ccfbd-108">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="ccfbd-109">安全性</span><span class="sxs-lookup"><span data-stu-id="ccfbd-109">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ccfbd-110">**使用下列方法，將資料庫設定為單一使用者模式：**</span><span class="sxs-lookup"><span data-stu-id="ccfbd-110">**To set a database to single-user mode, using:**</span></span>  
  
     [<span data-ttu-id="ccfbd-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ccfbd-111">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ccfbd-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ccfbd-112">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ccfbd-113">開始之前</span><span class="sxs-lookup"><span data-stu-id="ccfbd-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="ccfbd-114">限制事項</span><span class="sxs-lookup"><span data-stu-id="ccfbd-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="ccfbd-115">如果其他使用者可在將資料庫設定為單一使用者模式時連接到資料庫，則會關閉他們與資料庫的連接，而不會發出警告。</span><span class="sxs-lookup"><span data-stu-id="ccfbd-115">If other users are connected to the database at the time that you set the database to single-user mode, their connections to the database will be closed without warning.</span></span>  
  
-   <span data-ttu-id="ccfbd-116">即使設定該選項的使用者登出，資料庫仍會保持為單一使用者模式。</span><span class="sxs-lookup"><span data-stu-id="ccfbd-116">The database remains in single-user mode even if the user that set the option logs off.</span></span> <span data-ttu-id="ccfbd-117">此時其他使用者可以連接到這個資料庫，但只能有一位。</span><span class="sxs-lookup"><span data-stu-id="ccfbd-117">At that point, a different user, but only one, can connect to the database.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="ccfbd-118">必要條件</span><span class="sxs-lookup"><span data-stu-id="ccfbd-118">Prerequisites</span></span>  
  
-   <span data-ttu-id="ccfbd-119">將資料庫設為 SINGLE_USER 之前，請先確定 AUTO_UPDATE_STATISTICS_ASYNC 選項是否設為 OFF。</span><span class="sxs-lookup"><span data-stu-id="ccfbd-119">Before you set the database to SINGLE_USER, verify that the AUTO_UPDATE_STATISTICS_ASYNC option is set to OFF.</span></span> <span data-ttu-id="ccfbd-120">此選項設為 ON 時，更新統計資料的背景執行緒會取得資料庫連接，而您就無法以單一使用者模式存取資料庫。</span><span class="sxs-lookup"><span data-stu-id="ccfbd-120">When this option is set to ON, the background thread that is used to update statistics takes a connection against the database, and you will be unable to access the database in single-user mode.</span></span> <span data-ttu-id="ccfbd-121">如需詳細資訊，請參閱 [ALTER DATABASE SET 選項 &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)。</span><span class="sxs-lookup"><span data-stu-id="ccfbd-121">For more information, see [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ccfbd-122">Security</span><span class="sxs-lookup"><span data-stu-id="ccfbd-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ccfbd-123">權限</span><span class="sxs-lookup"><span data-stu-id="ccfbd-123">Permissions</span></span>  
 <span data-ttu-id="ccfbd-124">需要資料庫的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="ccfbd-124">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ccfbd-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ccfbd-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-a-database-to-single-user-mode"></a><span data-ttu-id="ccfbd-126">若要將資料庫設定為單一使用者模式</span><span class="sxs-lookup"><span data-stu-id="ccfbd-126">To set a database to single-user mode</span></span>  
  
1.  <span data-ttu-id="ccfbd-127">在 **[物件總管]** 中，連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="ccfbd-127">In **Object Explorer**, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="ccfbd-128">以滑鼠右鍵按一下要變更的資料庫，然後按一下 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="ccfbd-128">Right-click the database to change, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="ccfbd-129">在 [資料庫屬性]  對話方塊中按一下 [選項]  頁面。</span><span class="sxs-lookup"><span data-stu-id="ccfbd-129">In the **Database Properties** dialog box, click the **Options** page.</span></span>  
  
4.  <span data-ttu-id="ccfbd-130">從 **[限制存取]** 選項中，選取 **[單一]** 。</span><span class="sxs-lookup"><span data-stu-id="ccfbd-130">From the **Restrict Access** option, select **Single**.</span></span>  
  
5.  <span data-ttu-id="ccfbd-131">如果其他使用者已連接到資料庫，則會出現 **[開啟連接]** 訊息。</span><span class="sxs-lookup"><span data-stu-id="ccfbd-131">If other users are connected to the database, an **Open Connections** message will appear.</span></span> <span data-ttu-id="ccfbd-132">若要變更屬性並關閉其他所有連接，請按一下 **[是]** 。</span><span class="sxs-lookup"><span data-stu-id="ccfbd-132">To change the property and close all other connections, click **Yes**.</span></span>  
  
 <span data-ttu-id="ccfbd-133">您也可使用這個程序，將資料庫設定為多個或限制存取。</span><span class="sxs-lookup"><span data-stu-id="ccfbd-133">You can also set the database to Multiple or Restricted access by using this procedure.</span></span> <span data-ttu-id="ccfbd-134">如需限制存取選項的詳細資訊，請參閱[資料庫屬性 &#40;選項頁面&#41;](database-properties-options-page.md)。</span><span class="sxs-lookup"><span data-stu-id="ccfbd-134">For more information about the Restrict Access options, see [Database Properties &#40;Options Page&#41;](database-properties-options-page.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ccfbd-135">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ccfbd-135">Using Transact-SQL</span></span>  
  
#### <a name="to-set-a-database-to-single-user-mode"></a><span data-ttu-id="ccfbd-136">若要將資料庫設定為單一使用者模式</span><span class="sxs-lookup"><span data-stu-id="ccfbd-136">To set a database to single-user mode</span></span>  
  
1.  <span data-ttu-id="ccfbd-137">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ccfbd-137">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ccfbd-138">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="ccfbd-138">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ccfbd-139">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="ccfbd-139">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="ccfbd-140">這個範例會將資料庫設成 `SINGLE_USER` 模式來取得獨佔存取。</span><span class="sxs-lookup"><span data-stu-id="ccfbd-140">This example sets the database to `SINGLE_USER` mode to obtain exclusive access.</span></span> <span data-ttu-id="ccfbd-141">之後，範例會將 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 資料庫的狀態設成 `READ_ONLY` ，並將資料庫的存取權還給所有使用者。終止選項 `WITH ROLLBACK IMMEDIATE` 是在第一個 `ALTER DATABASE` 陳述式中指定。</span><span class="sxs-lookup"><span data-stu-id="ccfbd-141">The example then sets the state of the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database to `READ_ONLY` and returns access to the database to all users.The termination option `WITH ROLLBACK IMMEDIATE` is specified in the first `ALTER DATABASE` statement.</span></span> <span data-ttu-id="ccfbd-142">這會導致所有未完成的交易都會回復，而且 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 資料庫的任何其他連接都會立即中斷。</span><span class="sxs-lookup"><span data-stu-id="ccfbd-142">This will cause all incomplete transactions to be rolled back and any other connections to the [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] database to be immediately disconnected.</span></span>  
  
 [!code-sql[DatabaseDDL#AlterDatabase8](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase8)]  
  
## <a name="see-also"></a><span data-ttu-id="ccfbd-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ccfbd-143">See Also</span></span>  
 [<span data-ttu-id="ccfbd-144">ALTER DATABASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ccfbd-144">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
