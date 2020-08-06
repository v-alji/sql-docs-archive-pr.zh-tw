---
title: 記錄清除工作 (維護計畫) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.historycleanup.f1
helpviewer_keywords:
- History Cleanup Task dialog box
ms.assetid: 66bb6c39-958c-4053-a27f-b1118d2567f5
ms.reviewer: ''
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 03ff35b14fc13d2b4446b15501114489b52c421e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598355"
---
# <a name="history-cleanup-task-maintenance-plan"></a><span data-ttu-id="5362c-102">記錄清除工作 (維護計畫)</span><span class="sxs-lookup"><span data-stu-id="5362c-102">History Cleanup Task (Maintenance Plan)</span></span>

  <span data-ttu-id="5362c-103">使用 **[記錄清除工作]** 對話方塊，即可從 msdb 資料庫的資料表中捨棄舊的記錄資訊。</span><span class="sxs-lookup"><span data-stu-id="5362c-103">Use the **History Cleanup Task** dialog to discard old historical information from tables in the msdb database.</span></span> <span data-ttu-id="5362c-104">這個工作支援備份和還原記錄、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業記錄，以及維護計畫記錄的刪除。</span><span class="sxs-lookup"><span data-stu-id="5362c-104">This task supports deleting backup and restore history, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Job history, and maintenance plan history.</span></span>  
  
 <span data-ttu-id="5362c-105">此陳述式會使用 **sp_purge_jobhistory** 和 **sp_delete_backuphistory** 陳述式。</span><span class="sxs-lookup"><span data-stu-id="5362c-105">This statement uses the **sp_purge_jobhistory** and **sp_delete_backuphistory** statements.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="5362c-106">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="5362c-106">UI element list</span></span>  
 <span data-ttu-id="5362c-107">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="5362c-107">**Connection**</span></span>  
 <span data-ttu-id="5362c-108">選取執行此工作時要使用的伺服器連接。</span><span class="sxs-lookup"><span data-stu-id="5362c-108">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="5362c-109">**新增**</span><span class="sxs-lookup"><span data-stu-id="5362c-109">**New**</span></span>  
 <span data-ttu-id="5362c-110">建立新的伺服器連接，以便執行此工作時使用。</span><span class="sxs-lookup"><span data-stu-id="5362c-110">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="5362c-111">**[新增連接]** 對話方塊會在本主題稍後描述。</span><span class="sxs-lookup"><span data-stu-id="5362c-111">The **New Connection** dialog box is described later in this topic.</span></span>  
  
 <span data-ttu-id="5362c-112">**備份與還原記錄**</span><span class="sxs-lookup"><span data-stu-id="5362c-112">**Backup and restore history**</span></span>  
 <span data-ttu-id="5362c-113">保留最近建立備份時的記錄，有助於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在您要還原資料庫時，建立復原計畫。</span><span class="sxs-lookup"><span data-stu-id="5362c-113">Retaining records of when recent backups were created can help [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] create a recovery plan when you want to restore a database.</span></span> <span data-ttu-id="5362c-114">保留期限至少應該是完整資料庫備份的頻率。</span><span class="sxs-lookup"><span data-stu-id="5362c-114">The retention period should be at least the frequency of full database back ups.</span></span>  
  
 <span data-ttu-id="5362c-115">**SQL Server Agent 作業記錄**</span><span class="sxs-lookup"><span data-stu-id="5362c-115">**SQL Server Agent Job history**</span></span>  
 <span data-ttu-id="5362c-116">這個記錄可以幫助您疑難排解失敗的作業，或判斷資料庫動作為何發生。</span><span class="sxs-lookup"><span data-stu-id="5362c-116">This history can help you troubleshoot failed jobs, or determine why database actions occurred.</span></span>  
  
 <span data-ttu-id="5362c-117">**維護計畫記錄**</span><span class="sxs-lookup"><span data-stu-id="5362c-117">**Maintenance plan history**</span></span>  
 <span data-ttu-id="5362c-118">這個記錄可以幫助您疑難排解失敗的維護計畫作業，或判斷資料庫動作為何發生。</span><span class="sxs-lookup"><span data-stu-id="5362c-118">This history can help you troubleshoot failed maintenance plan jobs, or determine why database actions occurred.</span></span>  
  
 <span data-ttu-id="5362c-119">**移除早於下列時限的記錄資料**</span><span class="sxs-lookup"><span data-stu-id="5362c-119">**Remove historical data older than**</span></span>  
 <span data-ttu-id="5362c-120">指定您想要刪除的項目之存在時間。</span><span class="sxs-lookup"><span data-stu-id="5362c-120">Specify age of items that you want to delete.</span></span>  
  
 <span data-ttu-id="5362c-121">**檢視 T-SQL**</span><span class="sxs-lookup"><span data-stu-id="5362c-121">**View T-SQL**</span></span>  
 <span data-ttu-id="5362c-122">根據選取的選項，檢視此工作在伺服器上執行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="5362c-122">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5362c-123">受影響的物件數目較為大量時，會多花一些時間才會顯示。</span><span class="sxs-lookup"><span data-stu-id="5362c-123">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="5362c-124">新增連接對話方塊</span><span class="sxs-lookup"><span data-stu-id="5362c-124">New Connection Dialog Box</span></span>  
 <span data-ttu-id="5362c-125">**連線名稱**</span><span class="sxs-lookup"><span data-stu-id="5362c-125">**Connection name**</span></span>  
 <span data-ttu-id="5362c-126">輸入新連接的名稱。</span><span class="sxs-lookup"><span data-stu-id="5362c-126">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="5362c-127">**選取或輸入伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="5362c-127">**Select or enter a server name**</span></span>  
 <span data-ttu-id="5362c-128">選取執行此工作時要連接的伺服器。</span><span class="sxs-lookup"><span data-stu-id="5362c-128">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="5362c-129">**[重新整理]**</span><span class="sxs-lookup"><span data-stu-id="5362c-129">**Refresh**</span></span>  
 <span data-ttu-id="5362c-130">重新整理可用的伺服器清單。</span><span class="sxs-lookup"><span data-stu-id="5362c-130">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="5362c-131">**輸入要登入到伺服器的資訊**</span><span class="sxs-lookup"><span data-stu-id="5362c-131">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="5362c-132">指定如何對伺服器進行驗證。</span><span class="sxs-lookup"><span data-stu-id="5362c-132">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="5362c-133">**使用 Windows 整合式安全性**</span><span class="sxs-lookup"><span data-stu-id="5362c-133">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="5362c-134">使用 Microsoft Windows 驗證來連接 SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="5362c-134">Connect to an instance of the SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)] with Microsoft Windows Authentication.</span></span>  
  
 <span data-ttu-id="5362c-135">**使用特定的使用者名稱和密碼**</span><span class="sxs-lookup"><span data-stu-id="5362c-135">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="5362c-136">使用 SQL Server 驗證來連接 SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="5362c-136">Connect to an instance of the SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)] using SQL Server Authentication.</span></span> <span data-ttu-id="5362c-137">無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="5362c-137">This option is not available.</span></span>  
  
 <span data-ttu-id="5362c-138">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="5362c-138">**User name**</span></span>  
 <span data-ttu-id="5362c-139">提供驗證時要使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。</span><span class="sxs-lookup"><span data-stu-id="5362c-139">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="5362c-140">無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="5362c-140">This option is not available.</span></span>  
  
 <span data-ttu-id="5362c-141">**密碼**</span><span class="sxs-lookup"><span data-stu-id="5362c-141">**Password**</span></span>  
 <span data-ttu-id="5362c-142">提供驗證時要使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="5362c-142">Provide a password to use when authenticating.</span></span> <span data-ttu-id="5362c-143">無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="5362c-143">This option is not available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5362c-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5362c-144">See Also</span></span>  
 <span data-ttu-id="5362c-145">[sp_purge_jobhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="5362c-145">[sp_purge_jobhistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql) </span></span>  
 [<span data-ttu-id="5362c-146">sp_delete_backuphistory &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5362c-146">sp_delete_backuphistory &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql)  
  
  
