---
title: 開啟活動監視器 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Activity Monitor [SQL Server], setting the refresh interval
- refresh interval for Activity Monitor
- Activity Monitor [SQL Server], opening
- opening Activity Monitor
ms.assetid: 0a6eeb16-f02b-479d-9a60-543e40ebf46b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ea74122ad18a0a1ede5eef1e09684606ca0ce073
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707398"
---
# <a name="open-activity-monitor-sql-server-management-studio"></a><span data-ttu-id="463bc-102">開啟活動監視器 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="463bc-102">Open Activity Monitor (SQL Server Management Studio)</span></span>
  <span data-ttu-id="463bc-103">本主題描述如何開啟 [活動監視器] 來取得有關 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 處理序以及這些處理序如何影響目前 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的資訊。</span><span class="sxs-lookup"><span data-stu-id="463bc-103">This topic describes how to open the Activity Monitor to obtain information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] processes and how these processes affect the current instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="463bc-104">此外，本主題也描述如何設定 [活動監視器] 的重新整理間隔。</span><span class="sxs-lookup"><span data-stu-id="463bc-104">It also describes how to set the refresh interval of the Activity Monitor.</span></span>  
  
 <span data-ttu-id="463bc-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="463bc-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="463bc-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="463bc-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="463bc-107">安全性</span><span class="sxs-lookup"><span data-stu-id="463bc-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="463bc-108">**若要使用下列項目來開啟活動監視器：**</span><span class="sxs-lookup"><span data-stu-id="463bc-108">**To open the Activity Monitor using:**</span></span>  
  
     [<span data-ttu-id="463bc-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="463bc-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   <span data-ttu-id="463bc-110">**使用下列項目，設定重新整理間隔：**  [SQL Server Management Studio](#Refresh)</span><span class="sxs-lookup"><span data-stu-id="463bc-110">**To set the refresh interval using:**  [SQL Server Management Studio](#Refresh)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="463bc-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="463bc-111">Before You Begin</span></span>  
 <span data-ttu-id="463bc-112">[活動監視器] 會在監視的執行個體上執行查詢，以便取得 [活動監視器] 顯示窗格的資訊。</span><span class="sxs-lookup"><span data-stu-id="463bc-112">Activity Monitor runs queries on the monitored instance to obtain information for the Activity Monitor display panes.</span></span> <span data-ttu-id="463bc-113">當重新整理間隔的設定小於 10 秒時，用來執行這些查詢的時間就可能會影響伺服器效能。</span><span class="sxs-lookup"><span data-stu-id="463bc-113">When the refresh interval is set to less than 10 seconds, the time that is used to run these queries can affect server performance</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="463bc-114">Security</span><span class="sxs-lookup"><span data-stu-id="463bc-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="463bc-115">權限</span><span class="sxs-lookup"><span data-stu-id="463bc-115">Permissions</span></span>  
 <span data-ttu-id="463bc-116">若要檢視 [活動監視器]，使用者必須擁有 VIEW SERVER STATE 權限。</span><span class="sxs-lookup"><span data-stu-id="463bc-116">To view the Activity Monitor, a user must have VIEW SERVER STATE permission.</span></span> <span data-ttu-id="463bc-117">若要檢視活動監視器的 [資料檔案 I/O] 區段，除了 VIEW SERVER STATE 之外，您也必須具有 CREATE DATABASE、ALTER ANY DATABASE 或 VIEW ANY DEFINITION 權限。</span><span class="sxs-lookup"><span data-stu-id="463bc-117">To view the Data File I/O section of Activity Monitor, you must have CREATE DATABASE, ALTER ANY DATABASE, or VIEW ANY DEFINITION permission in addition to VIEW SERVER STATE.</span></span>  
  
 <span data-ttu-id="463bc-118">若要針對處理序執行 KILL 命令，使用者必須是系統管理員 (sysadmin) 或處理序管理員 (processadmin) 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="463bc-118">To KILL a process, a user must be a member of the sysadmin or processadmin fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="463bc-119">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="463bc-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-open-activity-monitor-in-sql-server-management-studio"></a><span data-ttu-id="463bc-120">若要在 SQL Server Management Studio 中開啟活動監視器</span><span class="sxs-lookup"><span data-stu-id="463bc-120">To open Activity Monitor in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="463bc-121">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 標準工具列上，按一下 **[活動監視器]**。</span><span class="sxs-lookup"><span data-stu-id="463bc-121">On the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] standard toolbar, click **Activity Monitor**.</span></span>  
  
2.  <span data-ttu-id="463bc-122">在 **[連接到伺服器]** 對話方塊中，選取伺服器名稱和驗證模式，然後按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="463bc-122">In the **Connect to Server** dialog box, select the server name and authentication mode, and then click **Connect**.</span></span>  
  
 <span data-ttu-id="463bc-123">您也可以隨時按下 CTRL+ALT A，藉以開啟 [活動監視器]。</span><span class="sxs-lookup"><span data-stu-id="463bc-123">You can also open Activity Monitor at any time by pressing CTRL+ALT A.</span></span>  
  
#### <a name="to-open-activity-monitor-in-object-explorer"></a><span data-ttu-id="463bc-124">若要在物件總管中開啟活動監視器</span><span class="sxs-lookup"><span data-stu-id="463bc-124">To open Activity Monitor in Object Explorer</span></span>  
  
-   <span data-ttu-id="463bc-125">在物件總管中，以滑鼠右鍵按一下實例名稱，然後選取 [**活動監視器**]。</span><span class="sxs-lookup"><span data-stu-id="463bc-125">In Object Explorer, right-click the instance name, and then select **Activity Monitor**.</span></span>  
  
#### <a name="to-open-activity-monitor-when-opening-sql-server-management-studio"></a><span data-ttu-id="463bc-126">若要在開啟 SQL Server Management Studio 時開啟活動監視器</span><span class="sxs-lookup"><span data-stu-id="463bc-126">To open Activity Monitor when opening SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="463bc-127">在 **[工具]** 功能表上，按一下 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="463bc-127">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="463bc-128">在 **[選項]** 對話方塊中，展開 **[環境]**，然後選取 **[一般]**。</span><span class="sxs-lookup"><span data-stu-id="463bc-128">In the **Options** dialog box, expand **Environment**, and then select **General**.</span></span>  
  
3.  <span data-ttu-id="463bc-129">在 **[啟動時]** 方塊中，選取 **[開啟物件總管和活動監視器]**。</span><span class="sxs-lookup"><span data-stu-id="463bc-129">In the **At startup** box, select **Open Object Explorer and Activity Monitor**.</span></span>  
  
4.  <span data-ttu-id="463bc-130">若要啟動這些變更，請關閉並重新開啟 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="463bc-130">To activate the changes, close and reopen [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
###  <a name="to-set-the-activity-monitor-refresh-interval"></a><a name="Refresh"></a><span data-ttu-id="463bc-131">若要設定活動監視器的重新整理間隔</span><span class="sxs-lookup"><span data-stu-id="463bc-131">To Set the Activity Monitor Refresh Interval</span></span>  
  
-   <span data-ttu-id="463bc-132">開啟 [活動監視器]。</span><span class="sxs-lookup"><span data-stu-id="463bc-132">Open the Activity Monitor.</span></span>  
  
-   <span data-ttu-id="463bc-133">以滑鼠右鍵按一下 [概觀]，選取 [重新整理間隔]，然後選取活動監視器應該用來取得新執行個體資訊的間隔。</span><span class="sxs-lookup"><span data-stu-id="463bc-133">Right-click **Overview**, select **Refresh Interval**, and then select the interval in which Activity Monitor should obtain new instance information.</span></span>  
  
  
