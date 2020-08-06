---
title: SQL Server 屬性 (服務索引標籤) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: e4ae0c6b-6fd8-4325-b54e-1758fc659958
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5822a02d5631e0d0e9318b20a1dcee87b8a4ded1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707997"
---
# <a name="sql-server-properties-service-tab"></a><span data-ttu-id="9d0f5-102">SQL Server 屬性 (服務索引標籤)</span><span class="sxs-lookup"><span data-stu-id="9d0f5-102">SQL Server Properties (Service Tab)</span></span>
  <span data-ttu-id="9d0f5-103">您可以使用 [MSSQLSERVER 屬性] 對話方塊的 [服務] 索引標籤來檢視或指定下列選項。</span><span class="sxs-lookup"><span data-stu-id="9d0f5-103">Use the **Service**tab on the **MSSQLSERVER Properties** dialog box to view or specify the following options.</span></span>  
  
## <a name="options"></a><span data-ttu-id="9d0f5-104">選項。</span><span class="sxs-lookup"><span data-stu-id="9d0f5-104">Options</span></span>  
 <span data-ttu-id="9d0f5-105">**二進位路徑**</span><span class="sxs-lookup"><span data-stu-id="9d0f5-105">**Binary Path**</span></span>  
 <span data-ttu-id="9d0f5-106">列出這個服務使用之程式檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="9d0f5-106">Lists the location of the program files used by this service.</span></span>  
  
 <span data-ttu-id="9d0f5-107">**錯誤控制**</span><span class="sxs-lookup"><span data-stu-id="9d0f5-107">**Error Control**</span></span>  
 <span data-ttu-id="9d0f5-108">1 表示 `SERVICE_ERROR_NORMAL`。</span><span class="sxs-lookup"><span data-stu-id="9d0f5-108">1 indicates `SERVICE_ERROR_NORMAL`.</span></span> <span data-ttu-id="9d0f5-109">如果在電腦啟動過程中，服務無法啟動，啟動程式就會記錄錯誤並顯示快顯訊息方塊，但是仍會繼續啟動作業。</span><span class="sxs-lookup"><span data-stu-id="9d0f5-109">If the service fails to start during computer start up, the startup program logs the error and displays a pop-up message box but continues the startup operation.</span></span> <span data-ttu-id="9d0f5-110">這項值不能被改變。</span><span class="sxs-lookup"><span data-stu-id="9d0f5-110">This value cannot be changed.</span></span>  
  
 <span data-ttu-id="9d0f5-111">**結束碼**</span><span class="sxs-lookup"><span data-stu-id="9d0f5-111">**Exit Code**</span></span>  
 <span data-ttu-id="9d0f5-112">發生錯誤時，錯誤號碼會在這個方塊中顯示。</span><span class="sxs-lookup"><span data-stu-id="9d0f5-112">When an error occurs, the error number appears in this box.</span></span> <span data-ttu-id="9d0f5-113">請使用這個號碼進行疑難排解，方法是在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 知識庫中搜尋該號碼，或者將號碼提供給技術支援人員。</span><span class="sxs-lookup"><span data-stu-id="9d0f5-113">Use this number to troubleshoot failures by searching for the number in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base or provide the number to your technical support staff.</span></span>  
  
 <span data-ttu-id="9d0f5-114">**Host Name**</span><span class="sxs-lookup"><span data-stu-id="9d0f5-114">**Host Name**</span></span>  
 <span data-ttu-id="9d0f5-115">顯示執行 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務的電腦或叢集名稱。</span><span class="sxs-lookup"><span data-stu-id="9d0f5-115">Displays the name of the computer or cluster running the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
 <span data-ttu-id="9d0f5-116">**名稱**</span><span class="sxs-lookup"><span data-stu-id="9d0f5-116">**Name**</span></span>  
 <span data-ttu-id="9d0f5-117">表示服務的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="9d0f5-117">Indicates the display name of the service.</span></span>  
  
 <span data-ttu-id="9d0f5-118">**處理序識別碼**</span><span class="sxs-lookup"><span data-stu-id="9d0f5-118">**Process ID**</span></span>  
 <span data-ttu-id="9d0f5-119">顯示 Windows 處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="9d0f5-119">Displays the Windows process ID.</span></span>  
  
 <span data-ttu-id="9d0f5-120">**服務類型**</span><span class="sxs-lookup"><span data-stu-id="9d0f5-120">**Service Type**</span></span>  
 <span data-ttu-id="9d0f5-121">顯示為呼叫處理序所提供的服務類型。</span><span class="sxs-lookup"><span data-stu-id="9d0f5-121">Displays the type of service provided to calling processes.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9d0f5-122">會安裝數個服務。</span><span class="sxs-lookup"><span data-stu-id="9d0f5-122">installs several services.</span></span>  
  
 <span data-ttu-id="9d0f5-123">**啟動模式**</span><span class="sxs-lookup"><span data-stu-id="9d0f5-123">**Start Mode**</span></span>  
 <span data-ttu-id="9d0f5-124">將這個服務設定為下列選擇：</span><span class="sxs-lookup"><span data-stu-id="9d0f5-124">Set this service to the following choices:</span></span>  
  
-   <span data-ttu-id="9d0f5-125">手動：電腦啟動時，這項服務不會自動啟動。</span><span class="sxs-lookup"><span data-stu-id="9d0f5-125">Manual: This service does not automatically start when the computer starts.</span></span> <span data-ttu-id="9d0f5-126">您必須使用「 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員」或其他工具來啟動服務。</span><span class="sxs-lookup"><span data-stu-id="9d0f5-126">You must start the service using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, or some other tool.</span></span>  
  
-   <span data-ttu-id="9d0f5-127">自動：這部電腦啟動時，這項服務會嘗試啟動。</span><span class="sxs-lookup"><span data-stu-id="9d0f5-127">Automatic: This service attempts to start when this computer starts.</span></span>  
  
-   <span data-ttu-id="9d0f5-128">停用：這項服務無法啟動。</span><span class="sxs-lookup"><span data-stu-id="9d0f5-128">Disabled: This service cannot be started.</span></span>  
  
 <span data-ttu-id="9d0f5-129">**State**</span><span class="sxs-lookup"><span data-stu-id="9d0f5-129">**State**</span></span>  
 <span data-ttu-id="9d0f5-130">表示這項服務為執行中、已停止或已停用。</span><span class="sxs-lookup"><span data-stu-id="9d0f5-130">Indicates whether this service is running, stopped, or disabled.</span></span> <span data-ttu-id="9d0f5-131">" **...** " 表示狀態變更已暫止。</span><span class="sxs-lookup"><span data-stu-id="9d0f5-131">"**...**" indicates a state change is pending.</span></span>  
  
  
