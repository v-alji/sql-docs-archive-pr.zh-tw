---
title: SQL Server Browser 屬性 (服務索引標籤) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 98ace9b0-72d5-4b72-9b7b-11fbc490981a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 200e45648b94e26c5e808e9a817cfe01866e6a65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585741"
---
# <a name="sql-server-browser-properties-service-tab"></a><span data-ttu-id="2a583-102">SQL Server Browser 屬性 (服務索引標籤)</span><span class="sxs-lookup"><span data-stu-id="2a583-102">SQL Server Browser Properties (Service Tab)</span></span>
  <span data-ttu-id="2a583-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 程式會以伺服器服務的方式執行。</span><span class="sxs-lookup"><span data-stu-id="2a583-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser program runs as a service on the server.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="2a583-104">Browser 會接聽 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資源的內送要求，並提供有關在電腦上所安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的資訊。</span><span class="sxs-lookup"><span data-stu-id="2a583-104">Browser listens for incoming requests for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resources and provides information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances installed on the computer.</span></span>  
  
 <span data-ttu-id="2a583-105">您可以使用 **[SQL Server Browser 內容]** 對話方塊上的 **[服務]** 索引標籤來檢視下列選項。</span><span class="sxs-lookup"><span data-stu-id="2a583-105">Use the **Service** tab on the **SQL Server Browser Properties** dialog box to view the following options.</span></span> <span data-ttu-id="2a583-106">除了 [啟動模式]  之外的所有屬性都是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="2a583-106">All properties except **Start Mode** are read-only.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2a583-107">選項。</span><span class="sxs-lookup"><span data-stu-id="2a583-107">Options</span></span>  
 <span data-ttu-id="2a583-108">**二進位路徑**</span><span class="sxs-lookup"><span data-stu-id="2a583-108">**Binary Path**</span></span>  
 <span data-ttu-id="2a583-109">顯示這個服務使用之程式檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="2a583-109">Displays the location of the program files used by this service.</span></span>  
  
 <span data-ttu-id="2a583-110">**錯誤控制**</span><span class="sxs-lookup"><span data-stu-id="2a583-110">**Error Control**</span></span>  
 <span data-ttu-id="2a583-111">1 表示 `SERVICE_ERROR_NORMAL`。</span><span class="sxs-lookup"><span data-stu-id="2a583-111">1 indicates `SERVICE_ERROR_NORMAL`.</span></span> <span data-ttu-id="2a583-112">如果在電腦啟動過程中，服務無法啟動，啟動程式就會記錄錯誤並顯示快顯訊息方塊，但是仍會繼續啟動作業。</span><span class="sxs-lookup"><span data-stu-id="2a583-112">If the service fails to start during computer start up, the startup program logs the error and displays a pop-up message box but continues the startup operation.</span></span> <span data-ttu-id="2a583-113">這項值不能被改變。</span><span class="sxs-lookup"><span data-stu-id="2a583-113">This value cannot be changed.</span></span>  
  
 <span data-ttu-id="2a583-114">**結束碼**</span><span class="sxs-lookup"><span data-stu-id="2a583-114">**Exit Code**</span></span>  
 <span data-ttu-id="2a583-115">發生錯誤時，錯誤號碼會在這個方塊中顯示。</span><span class="sxs-lookup"><span data-stu-id="2a583-115">When an error occurs, the error number appears in this box.</span></span> <span data-ttu-id="2a583-116">請使用這個號碼進行疑難排解，方法是在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 知識庫中搜尋該號碼，或者將號碼提供給技術支援人員。</span><span class="sxs-lookup"><span data-stu-id="2a583-116">Use this number to troubleshoot failures by searching for the number in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base or provide the number to your technical support staff.</span></span>  
  
 <span data-ttu-id="2a583-117">**Host Name**</span><span class="sxs-lookup"><span data-stu-id="2a583-117">**Host Name**</span></span>  
 <span data-ttu-id="2a583-118">顯示執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser 服務之電腦或叢集的名稱。</span><span class="sxs-lookup"><span data-stu-id="2a583-118">Displays the name of the computer or cluster running the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser service.</span></span>  
  
 <span data-ttu-id="2a583-119">**名稱**</span><span class="sxs-lookup"><span data-stu-id="2a583-119">**Name**</span></span>  
 <span data-ttu-id="2a583-120">表示服務的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="2a583-120">Indicates the display name of the service.</span></span>  
  
 <span data-ttu-id="2a583-121">**處理序識別碼**</span><span class="sxs-lookup"><span data-stu-id="2a583-121">**Process ID**</span></span>  
 <span data-ttu-id="2a583-122">顯示 Windows 處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="2a583-122">Displays the Windows process ID.</span></span>  
  
 <span data-ttu-id="2a583-123">**服務類型**</span><span class="sxs-lookup"><span data-stu-id="2a583-123">**Service Type**</span></span>  
 <span data-ttu-id="2a583-124">顯示為呼叫處理序所提供的服務類型。</span><span class="sxs-lookup"><span data-stu-id="2a583-124">Displays the type of service provided to calling processes.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="2a583-125">會安裝數個服務。</span><span class="sxs-lookup"><span data-stu-id="2a583-125">installs several services.</span></span>  
  
 <span data-ttu-id="2a583-126">**啟動模式**</span><span class="sxs-lookup"><span data-stu-id="2a583-126">**Start Mode**</span></span>  
 <span data-ttu-id="2a583-127">將這個服務設定為下列選擇：</span><span class="sxs-lookup"><span data-stu-id="2a583-127">Set this service to the following choices:</span></span>  
  
-   <span data-ttu-id="2a583-128">手動：電腦啟動時，這項服務不會自動啟動。</span><span class="sxs-lookup"><span data-stu-id="2a583-128">Manual: This service does not automatically start when the computer starts.</span></span> <span data-ttu-id="2a583-129">您必須使用「 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員」或其他工具來啟動服務。</span><span class="sxs-lookup"><span data-stu-id="2a583-129">You must start the service using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, or some other tool.</span></span>  
  
-   <span data-ttu-id="2a583-130">自動：這部電腦啟動時，這項服務會嘗試啟動。</span><span class="sxs-lookup"><span data-stu-id="2a583-130">Automatic: This service attempts to start when this computer starts.</span></span>  
  
-   <span data-ttu-id="2a583-131">停用：這項服務無法啟動。</span><span class="sxs-lookup"><span data-stu-id="2a583-131">Disabled: This service cannot be started.</span></span>  
  
 <span data-ttu-id="2a583-132">**State**</span><span class="sxs-lookup"><span data-stu-id="2a583-132">**State**</span></span>  
 <span data-ttu-id="2a583-133">表示這項服務為執行中、已停止或已停用。</span><span class="sxs-lookup"><span data-stu-id="2a583-133">Indicates whether this service is running, stopped, or disabled.</span></span> <span data-ttu-id="2a583-134">" **...** " 表示狀態變更已暫止。</span><span class="sxs-lookup"><span data-stu-id="2a583-134">"**...**" indicates a state change is pending.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a583-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a583-135">See Also</span></span>  
 [<span data-ttu-id="2a583-136">SQL Server Browser 服務</span><span class="sxs-lookup"><span data-stu-id="2a583-136">SQL Server Browser Service</span></span>](../../../2014/tools/configuration-manager/sql-server-browser-service.md)  
  
  
