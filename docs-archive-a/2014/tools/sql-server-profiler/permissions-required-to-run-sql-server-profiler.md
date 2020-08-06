---
title: 執行 SQL Server Profiler 所需的權限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], permissions
- traces [SQL Server], replaying
- replaying traces
- SQL Server Profiler, permissions
- security [SQL Server], SQL Server Profiler
ms.assetid: 5c580a87-88ae-4314-8fe1-54ade83f227f
author: stevestein
ms.author: sstein
ms.openlocfilehash: e73ffe2e127299db9a9e37e48f089aab2cccca52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705762"
---
# <a name="permissions-required-to-run-sql-server-profiler"></a><span data-ttu-id="33126-102">執行 SQL Server Profiler 所需的權限</span><span class="sxs-lookup"><span data-stu-id="33126-102">Permissions Required to Run SQL Server Profiler</span></span>
  <span data-ttu-id="33126-103">根據預設，執行 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] 時，所需的使用者權限與用來建立追蹤的 Transact-SQL 預存程序相同。</span><span class="sxs-lookup"><span data-stu-id="33126-103">By default, running [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] requires the same user permissions as the Transact-SQL stored procedures that are used to create traces.</span></span> <span data-ttu-id="33126-104">若要執行 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)]，使用者必須被授與 ALTER TRACE 權限。</span><span class="sxs-lookup"><span data-stu-id="33126-104">To run [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)], users must be granted the ALTER TRACE permission.</span></span> <span data-ttu-id="33126-105">如需詳細資訊，請參閱 [GRANT 伺服器權限 &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-server-permissions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="33126-105">For more information, see [GRANT Server Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-server-permissions-transact-sql).</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="33126-106">具有 SHOWPLAN、ALTER TRACE 或 VIEW SERVER STATE 權限的使用者可以檢視執行程序表輸出中所擷取的查詢。</span><span class="sxs-lookup"><span data-stu-id="33126-106">Users who have the SHOWPLAN, the ALTER TRACE, or the VIEW SERVER STATE permission can view queries that are captured in Showplan output.</span></span> <span data-ttu-id="33126-107">這些查詢可能會包含類似密碼的敏感資訊。</span><span class="sxs-lookup"><span data-stu-id="33126-107">These queries may contain sensitive information such as passwords.</span></span> <span data-ttu-id="33126-108">因此，我們建議您只能將這些權限授與給有權檢視敏感資訊的使用者，例如 db_owner 固定資料庫角色的成員或是 sysadmin 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="33126-108">Therefore, we recommend that you only grant these permissions to users who are authorized to view sensitive information, such as members of the db_owner fixed database role, or members of the sysadmin fixed server role.</span></span> <span data-ttu-id="33126-109">此外，我們也建議您只將執行程序表檔案或是包含與執行程序表相關之事件的追蹤檔案儲存到使用 NTFS 檔案系統的位置，並建議您將存取權限制為有權檢視敏感資訊的使用者。</span><span class="sxs-lookup"><span data-stu-id="33126-109">Additionally, we recommend that you only save Showplan files or trace files that contain Showplan-related events to a location that uses the NTFS file system, and that you restrict access to users who are authorized to view sensitive information.</span></span>

## <a name="permissions-used-to-replay-traces"></a><span data-ttu-id="33126-110">用來重新執行追蹤的權限</span><span class="sxs-lookup"><span data-stu-id="33126-110">Permissions Used to Replay Traces</span></span>
 <span data-ttu-id="33126-111">重新執行追蹤時，執行的使用者也必須要有 ALTER TRACE 權限。</span><span class="sxs-lookup"><span data-stu-id="33126-111">Replaying traces also requires that the user who is replaying the trace have the ALTER TRACE permission.</span></span>

 <span data-ttu-id="33126-112">然而，在重新執行期間，如果所重新執行的追蹤發生「稽核登入」事件，則 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] 會使用 EXECUTE AS 命令。</span><span class="sxs-lookup"><span data-stu-id="33126-112">However, during replay, [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] uses the EXECUTE AS command if an Audit Login event is encountered in the trace that is being replayed.</span></span> [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] <span data-ttu-id="33126-113">會使用 EXECUTE AS 命令來模擬與該登入事件有關的使用者。</span><span class="sxs-lookup"><span data-stu-id="33126-113">uses the EXECUTE AS command to impersonate the user who is associated with the login event.</span></span>

 <span data-ttu-id="33126-114">如果 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] 在重新執行的追蹤中發生登入事件，就會執行下列權限檢查：</span><span class="sxs-lookup"><span data-stu-id="33126-114">If [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] encounters a login event in a trace that is being replayed, the following permission checks are performed:</span></span>

1.  <span data-ttu-id="33126-115">User1 (具有 ALTER TRACE 權限) 開始重新執行追蹤。</span><span class="sxs-lookup"><span data-stu-id="33126-115">User1, who has the ALTER TRACE permission, starts replaying a trace.</span></span>

2.  <span data-ttu-id="33126-116">在重新執行的追蹤中，User2 發生登入事件。</span><span class="sxs-lookup"><span data-stu-id="33126-116">A login event for User2 is encountered in the replayed trace.</span></span>

3.  [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] <span data-ttu-id="33126-117">使用 EXECUTE AS 命令來模擬 User2。</span><span class="sxs-lookup"><span data-stu-id="33126-117">uses the EXECUTE AS command to impersonate User2.</span></span>

4.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="33126-118">嘗試驗證 User2，根據驗證結果，會發生下列其中一種情形：</span><span class="sxs-lookup"><span data-stu-id="33126-118">attempts to authenticate User2, and depending on the results, one of the following occurs:</span></span>

    1.  <span data-ttu-id="33126-119">如果無法驗證 User2， [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] 會傳回錯誤，並以 User1 的身分繼續重新執行追蹤。</span><span class="sxs-lookup"><span data-stu-id="33126-119">If User2 cannot be authenticated, [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] returns an error, and continues replaying the trace as User1.</span></span>

    2.  <span data-ttu-id="33126-120">若成功驗證 User2，就會以 User2 的身分繼續重新執行追蹤。</span><span class="sxs-lookup"><span data-stu-id="33126-120">If User2 is successfully authenticated, replaying the trace as User2 continues.</span></span>

5.  <span data-ttu-id="33126-121">在目標資料庫上檢查 User2 的權限，根據檢查結果，會發生下列其中一種情形：</span><span class="sxs-lookup"><span data-stu-id="33126-121">Permissions for User2 are checked on the target database, and depending on the results, one of the following occurs:</span></span>

    1.  <span data-ttu-id="33126-122">如果 User2 擁有目標資料庫的權限，則已模擬成功，而且是以 User2 的身分來重新執行追蹤。</span><span class="sxs-lookup"><span data-stu-id="33126-122">If User2 has permissions on the target database, impersonation has succeeded, and the trace is replayed as User2.</span></span>

    2.  <span data-ttu-id="33126-123">如果 User2 沒有目標資料庫的權限，伺服器會檢查該資料庫上是否有 Guest 使用者。</span><span class="sxs-lookup"><span data-stu-id="33126-123">If User2 does not have permissions on the target database, the server checks for a Guest user on that database.</span></span>

6.  <span data-ttu-id="33126-124">在目標資料庫上檢查是否有 Guest 使用者，根據檢查結果，會發生下列其中一種情形：</span><span class="sxs-lookup"><span data-stu-id="33126-124">Existence of a Guest user is checked on the target database, and depending on the results, one of the following occurs:</span></span>

    1.  <span data-ttu-id="33126-125">若有 Guest 帳戶存在，就會以 Guest 帳戶來重新執行追蹤。</span><span class="sxs-lookup"><span data-stu-id="33126-125">If a Guest account exists, the trace is replayed as the Guest account.</span></span>

    2.  <span data-ttu-id="33126-126">如果目標資料庫沒有 Guest 帳戶，就會傳回錯誤，並以 User1 的身分來重新執行追蹤。</span><span class="sxs-lookup"><span data-stu-id="33126-126">If no Guest account exists on the target database, an error is returned and the trace is replayed as User1.</span></span>

 <span data-ttu-id="33126-127">下圖顯示重新執行追蹤時，檢查權限的程序：</span><span class="sxs-lookup"><span data-stu-id="33126-127">The following diagram shows this process of checking permission when replaying traces:</span></span>

 <span data-ttu-id="33126-128">![SQL Server Profiler 重新執行追蹤權限](../../database-engine/media/replaytracedecisiontree.gif "SQL Server Profiler 重新執行追蹤權限")</span><span class="sxs-lookup"><span data-stu-id="33126-128">![SQL Server Profiler replay trace permissions](../../database-engine/media/replaytracedecisiontree.gif "SQL Server Profiler replay trace permissions")</span></span>

## <a name="see-also"></a><span data-ttu-id="33126-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33126-129">See Also</span></span>
 <span data-ttu-id="33126-130">[SQL Server Profiler 預存程式 &#40;transact-sql&#41;重新](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)[執行追蹤](replay-traces.md)[建立追蹤 &#40;SQL Server Profiler](create-a-trace-sql-server-profiler.md)&#41;重新[執行追蹤資料表](replay-a-trace-table-sql-server-profiler.md)&#40;SQL Server Profiler&#41;重新[執行追蹤檔 &#40;SQL Server Profiler](replay-a-trace-file-sql-server-profiler.md)&#41;</span><span class="sxs-lookup"><span data-stu-id="33126-130">[SQL Server Profiler Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql) [Replay Traces](replay-traces.md) [Create a Trace &#40;SQL Server Profiler&#41;](create-a-trace-sql-server-profiler.md) [Replay a Trace Table &#40;SQL Server Profiler&#41;](replay-a-trace-table-sql-server-profiler.md) [Replay a Trace File &#40;SQL Server Profiler&#41;](replay-a-trace-file-sql-server-profiler.md)</span></span>


