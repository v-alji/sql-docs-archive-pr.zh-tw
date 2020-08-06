---
title: SQL 全文檢索篩選精靈啟動器 ([服務] 索引標籤) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 6aad7ebe-c4be-4d37-8536-61502f51faa2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8f0d9c76d7d92947dd17fe2ed6e912e3d6baa6bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605964"
---
# <a name="sql-full-text-filter-daemon-launcher-service-tab"></a><span data-ttu-id="47ed9-102">SQL 全文檢索篩選背景程式啟動器 (服務索引標籤)</span><span class="sxs-lookup"><span data-stu-id="47ed9-102">SQL Full-text Filter Daemon Launcher (Service Tab)</span></span>
  <span data-ttu-id="47ed9-103">從 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]開始， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 全文檢索就會使用 SQL 全文檢索篩選背景程式啟動器 (FDHOST 啟動器) 服務。</span><span class="sxs-lookup"><span data-stu-id="47ed9-103">Beginning in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], the SQL Full-text Filter Daemon Launcher (FDHOST Launcher) service is used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] full-text.</span></span> <span data-ttu-id="47ed9-104">如果您使用全文檢索搜尋，這個服務就必須執行。</span><span class="sxs-lookup"><span data-stu-id="47ed9-104">This service must be running if you use full-text search.</span></span> <span data-ttu-id="47ed9-105">如需有關篩選背景程式主機處理序的詳細資訊，請參閱《 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的＜全文檢索搜尋架構＞。</span><span class="sxs-lookup"><span data-stu-id="47ed9-105">For information about the filter daemon host processes, see "Full-Text Search Architecture" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="47ed9-106">您可以使用 [SQL 全文檢索篩選背景程式啟動器屬性] 對話方塊的 [服務] 索引標籤來檢視或指定下列選項。</span><span class="sxs-lookup"><span data-stu-id="47ed9-106">Use the **Service**tab on the **SQL Full-text Filter Daemon LauncherProperties** dialog box to view or specify the following options.</span></span>  
  
## <a name="options"></a><span data-ttu-id="47ed9-107">選項。</span><span class="sxs-lookup"><span data-stu-id="47ed9-107">Options</span></span>  
 <span data-ttu-id="47ed9-108">**二進位路徑**</span><span class="sxs-lookup"><span data-stu-id="47ed9-108">**Binary Path**</span></span>  
 <span data-ttu-id="47ed9-109">列出這個服務使用之程式檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="47ed9-109">Lists the location of the program files used by this service.</span></span>  
  
 <span data-ttu-id="47ed9-110">**錯誤控制**</span><span class="sxs-lookup"><span data-stu-id="47ed9-110">**Error Control**</span></span>  
 <span data-ttu-id="47ed9-111">1 表示 `SERVICE_ERROR_NORMAL`。</span><span class="sxs-lookup"><span data-stu-id="47ed9-111">1 indicates `SERVICE_ERROR_NORMAL`.</span></span> <span data-ttu-id="47ed9-112">如果在電腦啟動過程中，服務無法啟動，啟動程式就會記錄錯誤並顯示快顯訊息方塊，但是仍會繼續啟動作業。</span><span class="sxs-lookup"><span data-stu-id="47ed9-112">If the service fails to start during computer start up, the startup program logs the error and displays a pop-up message box but continues the startup operation.</span></span> <span data-ttu-id="47ed9-113">這項值不能被改變。</span><span class="sxs-lookup"><span data-stu-id="47ed9-113">This value cannot be changed.</span></span>  
  
 <span data-ttu-id="47ed9-114">**結束碼**</span><span class="sxs-lookup"><span data-stu-id="47ed9-114">**Exit Code**</span></span>  
 <span data-ttu-id="47ed9-115">發生錯誤時，錯誤號碼會在這個方塊中顯示。</span><span class="sxs-lookup"><span data-stu-id="47ed9-115">When an error occurs, the error number appears in this box.</span></span> <span data-ttu-id="47ed9-116">請使用這個號碼進行疑難排解，方法是在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 知識庫中搜尋該號碼，或者將號碼提供給技術支援人員。</span><span class="sxs-lookup"><span data-stu-id="47ed9-116">Use this number to troubleshoot failures by searching for the number in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base or provide the number to your technical support staff.</span></span>  
  
 <span data-ttu-id="47ed9-117">**Host Name**</span><span class="sxs-lookup"><span data-stu-id="47ed9-117">**Host Name**</span></span>  
 <span data-ttu-id="47ed9-118">顯示執行 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務的電腦或叢集名稱。</span><span class="sxs-lookup"><span data-stu-id="47ed9-118">Displays the name of the computer or cluster running the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
 <span data-ttu-id="47ed9-119">**名稱**</span><span class="sxs-lookup"><span data-stu-id="47ed9-119">**Name**</span></span>  
 <span data-ttu-id="47ed9-120">表示服務的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="47ed9-120">Indicates the display name of the service.</span></span>  
  
 <span data-ttu-id="47ed9-121">**處理序識別碼**</span><span class="sxs-lookup"><span data-stu-id="47ed9-121">**Process ID**</span></span>  
 <span data-ttu-id="47ed9-122">顯示 Windows 處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="47ed9-122">Displays the Windows process ID.</span></span>  
  
 <span data-ttu-id="47ed9-123">**SQL 服務類型**</span><span class="sxs-lookup"><span data-stu-id="47ed9-123">**SQL Service Type**</span></span>  
 <span data-ttu-id="47ed9-124">顯示為呼叫處理序所提供的服務類型。</span><span class="sxs-lookup"><span data-stu-id="47ed9-124">Displays the type of service provided to calling processes.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="47ed9-125">會安裝數個服務。</span><span class="sxs-lookup"><span data-stu-id="47ed9-125">installs several services.</span></span>  
  
 <span data-ttu-id="47ed9-126">**啟動模式**</span><span class="sxs-lookup"><span data-stu-id="47ed9-126">**Start Mode**</span></span>  
 <span data-ttu-id="47ed9-127">將這個服務設定為下列選擇：</span><span class="sxs-lookup"><span data-stu-id="47ed9-127">Set this service to the following choices:</span></span>  
  
-   <span data-ttu-id="47ed9-128">手動：電腦啟動時，這項服務不會自動啟動。</span><span class="sxs-lookup"><span data-stu-id="47ed9-128">Manual: This service does not automatically start when the computer starts.</span></span> <span data-ttu-id="47ed9-129">您必須使用「 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員」或其他工具來啟動服務。</span><span class="sxs-lookup"><span data-stu-id="47ed9-129">You must start the service using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, or some other tool.</span></span>  
  
-   <span data-ttu-id="47ed9-130">自動：這部電腦啟動時，這項服務會嘗試啟動。</span><span class="sxs-lookup"><span data-stu-id="47ed9-130">Automatic: This service attempts to start when this computer starts.</span></span>  
  
-   <span data-ttu-id="47ed9-131">停用：這項服務無法啟動。</span><span class="sxs-lookup"><span data-stu-id="47ed9-131">Disabled: This service cannot be started.</span></span>  
  
 <span data-ttu-id="47ed9-132">**State**</span><span class="sxs-lookup"><span data-stu-id="47ed9-132">**State**</span></span>  
 <span data-ttu-id="47ed9-133">表示這項服務為執行中、已停止或已停用。</span><span class="sxs-lookup"><span data-stu-id="47ed9-133">Indicates whether this service is running, stopped, or disabled.</span></span> <span data-ttu-id="47ed9-134">" **...** " 表示狀態變更已暫止。</span><span class="sxs-lookup"><span data-stu-id="47ed9-134">"**...**" indicates a state change is pending.</span></span>  
  
  
