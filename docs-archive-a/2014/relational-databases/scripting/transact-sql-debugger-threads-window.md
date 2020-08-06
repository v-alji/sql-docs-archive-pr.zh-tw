---
title: 執行緒視窗
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Threads Window [Transact-SQL]
ms.assetid: e153f619-0049-4162-9076-c24a454f3278
author: rothja
ms.author: jroth
ms.openlocfilehash: 6f3460c892c182996a753c2a16076418a6b2008f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697873"
---
# <a name="threads-window"></a><span data-ttu-id="ffdec-102">執行緒視窗</span><span class="sxs-lookup"><span data-stu-id="ffdec-102">Threads Window</span></span>
  <span data-ttu-id="ffdec-103">[執行緒] 視窗會顯示有關所偵錯之 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器工作階段使用的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行緒資訊。</span><span class="sxs-lookup"><span data-stu-id="ffdec-103">The **Threads** window displays information about the [!INCLUDE[ssDE](../../includes/ssde-md.md)] thread that is used by the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor session that is being debugged.</span></span> <span data-ttu-id="ffdec-104">您必須在偵錯模式中，才能顯示執行緒資訊。</span><span class="sxs-lookup"><span data-stu-id="ffdec-104">You must be in debug mode to display the thread information.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="ffdec-105">工作清單</span><span class="sxs-lookup"><span data-stu-id="ffdec-105">Task List</span></span>  
 <span data-ttu-id="ffdec-106">**若要存取執行緒視窗**</span><span class="sxs-lookup"><span data-stu-id="ffdec-106">**To access the Threads window**</span></span>  
  
-   <span data-ttu-id="ffdec-107">在 [偵錯]  功能表中，按一下 [視窗]  ，再按一下 [執行緒]  。</span><span class="sxs-lookup"><span data-stu-id="ffdec-107">On the **Debug** menu, click **Windows**, and then click **Threads**.</span></span>  
  
## <a name="columns"></a><span data-ttu-id="ffdec-108">資料行</span><span class="sxs-lookup"><span data-stu-id="ffdec-108">Columns</span></span>  
 <span data-ttu-id="ffdec-109">**識別碼**</span><span class="sxs-lookup"><span data-stu-id="ffdec-109">**ID**</span></span>  
 <span data-ttu-id="ffdec-110">這是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具指派給執行緒的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="ffdec-110">Is a unique identifying number that the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger assigns to the thread.</span></span> <span data-ttu-id="ffdec-111">您可以從 sys.dm_os_threads 動態管理檢視選取資料列，以尋找有關執行緒的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="ffdec-111">You can find more information about the thread by selecting a row from the sys.dm_os_threads dynamic management view.</span></span>  
  
 <span data-ttu-id="ffdec-112">如果您不是在輕量型共用模式下執行，請選取一個資料列，其中的 os_thread_id 值符合 [識別碼]  資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="ffdec-112">If you are not running in lightweight pooling mode, select the row in which the value in os_thread_id matches the value in the **ID** column.</span></span> <span data-ttu-id="ffdec-113">如果您在輕量型共用模式下執行，請選取一個資料列，其中的 fiber_context_address 值符合 [識別碼]  資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="ffdec-113">If you are running in lightweight pooling mode, select the row in which the value in fiber_context_address matches the value in the **ID** column.</span></span>  
  
 <span data-ttu-id="ffdec-114">**名稱**</span><span class="sxs-lookup"><span data-stu-id="ffdec-114">**Name**</span></span>  
 <span data-ttu-id="ffdec-115">使用 [!INCLUDE[ssDE](../../includes/ssde-md.md)] ComputerName/InstanceName [SPID] **格式顯示有關**工作階段的資訊。</span><span class="sxs-lookup"><span data-stu-id="ffdec-115">Displays information about the [!INCLUDE[ssDE](../../includes/ssde-md.md)] session in the format **ComputerName/InstanceName [SPID]**.</span></span>  
  
 <span data-ttu-id="ffdec-116">**ComputerName**</span><span class="sxs-lookup"><span data-stu-id="ffdec-116">**ComputerName**</span></span>  
 <span data-ttu-id="ffdec-117">正在執行查詢編輯器工作階段連接之 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="ffdec-117">The name of the computer that is running the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] that the Query Editor session is connected to.</span></span>  
  
 <span data-ttu-id="ffdec-118">**InstanceName**</span><span class="sxs-lookup"><span data-stu-id="ffdec-118">**InstanceName**</span></span>  
 <span data-ttu-id="ffdec-119">查詢編輯器工作階段連接之 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="ffdec-119">The name of the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] that the Query Editor session is connected to.</span></span>  
  
 <span data-ttu-id="ffdec-120">**[SPID]**</span><span class="sxs-lookup"><span data-stu-id="ffdec-120">**[SPID]**</span></span>  
 <span data-ttu-id="ffdec-121">可唯一識別此工作階段的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 工作階段處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="ffdec-121">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] session process ID that uniquely identifies this session.</span></span> <span data-ttu-id="ffdec-122">您可以取得有關此工作階段的資訊，其方式是在 sys.sysprocesses 檢視表中選取與 spid 資料行有相同值的資料列。</span><span class="sxs-lookup"><span data-stu-id="ffdec-122">You can obtain more information about the session by selecting the row in the sys.sysprocesses view that has the same value in the spid column.</span></span>  
  
 <span data-ttu-id="ffdec-123">**位置**</span><span class="sxs-lookup"><span data-stu-id="ffdec-123">**Location**</span></span>  
 <span data-ttu-id="ffdec-124">顯示所偵錯之查詢編輯器工作階段內使用的指令碼檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="ffdec-124">Displays the name of the script file that is used in the Query Editor session that is being debugged.</span></span>  
  
 <span data-ttu-id="ffdec-125">**優先順序**</span><span class="sxs-lookup"><span data-stu-id="ffdec-125">**Priority**</span></span>  
 <span data-ttu-id="ffdec-126">[!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具不支援這個功能。</span><span class="sxs-lookup"><span data-stu-id="ffdec-126">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger does not support this feature.</span></span>  
  
 <span data-ttu-id="ffdec-127">**暫止**</span><span class="sxs-lookup"><span data-stu-id="ffdec-127">**Suspend**</span></span>  
 <span data-ttu-id="ffdec-128">[!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具不支援這個功能。</span><span class="sxs-lookup"><span data-stu-id="ffdec-128">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger does not support this feature.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffdec-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffdec-129">See Also</span></span>  
 <span data-ttu-id="ffdec-130">[Transact-SQL 偵錯工具](transact-sql-debugger.md) </span><span class="sxs-lookup"><span data-stu-id="ffdec-130">[Transact-SQL Debugger](transact-sql-debugger.md) </span></span>  
 <span data-ttu-id="ffdec-131">[Transact-SQL 偵錯工具資訊](transact-sql-debugger-information.md) </span><span class="sxs-lookup"><span data-stu-id="ffdec-131">[Transact-SQL Debugger Information](transact-sql-debugger-information.md) </span></span>  
 <span data-ttu-id="ffdec-132">[sys.dm_os_threads &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-threads-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ffdec-132">[sys.dm_os_threads &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-threads-transact-sql) </span></span>  
 [<span data-ttu-id="ffdec-133">sys.sysprocesses &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ffdec-133">sys.sysprocesses &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql)  
