---
title: SQL Server Integration Services 屬性 ([服務] 索引標籤) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 37f0acd9-c96f-48fd-9b53-2ca0097af242
author: stevestein
ms.author: sstein
ms.openlocfilehash: a752bdeab3c99ac97445e3281d3165a2d8f79866
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87605959"
---
# <a name="sql-server-integration-services-properties-service-tab"></a><span data-ttu-id="910ad-102">SQL Server Integration Services 屬性 (服務索引標籤)</span><span class="sxs-lookup"><span data-stu-id="910ad-102">SQL Server Integration Services Properties (Service Tab)</span></span>
  <span data-ttu-id="910ad-103">您可以使用  **[屬性]** [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 對話方塊上的 [服務]  索引標籤來檢視或指定下列選項。</span><span class="sxs-lookup"><span data-stu-id="910ad-103">Use the **Service**tab on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] **Properties** dialog box to view or specify the following options.</span></span>  
  
## <a name="options"></a><span data-ttu-id="910ad-104">選項。</span><span class="sxs-lookup"><span data-stu-id="910ad-104">Options</span></span>  
 <span data-ttu-id="910ad-105">**二進位路徑**</span><span class="sxs-lookup"><span data-stu-id="910ad-105">**Binary Path**</span></span>  
 <span data-ttu-id="910ad-106">顯示這個服務使用之程式檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="910ad-106">Displays the location of the program files used by this service.</span></span>  
  
 <span data-ttu-id="910ad-107">**錯誤控制**</span><span class="sxs-lookup"><span data-stu-id="910ad-107">**Error Control**</span></span>  
 <span data-ttu-id="910ad-108">1 表示 `SERVICE_ERROR_NORMAL`。</span><span class="sxs-lookup"><span data-stu-id="910ad-108">1 indicates `SERVICE_ERROR_NORMAL`.</span></span> <span data-ttu-id="910ad-109">如果在電腦啟動過程中，服務無法啟動，啟動程式就會記錄錯誤並顯示快顯訊息方塊，但是仍會繼續啟動作業。</span><span class="sxs-lookup"><span data-stu-id="910ad-109">If the service fails to start during computer start up, the startup program logs the error and displays a pop-up message box but continues the startup operation.</span></span> <span data-ttu-id="910ad-110">這項值不能被改變。</span><span class="sxs-lookup"><span data-stu-id="910ad-110">This value cannot be changed.</span></span>  
  
 <span data-ttu-id="910ad-111">**結束碼**</span><span class="sxs-lookup"><span data-stu-id="910ad-111">**Exit Code**</span></span>  
 <span data-ttu-id="910ad-112">定義啟動或停止服務時所遇到之問題的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="910ad-112">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows error code defining any problems encountered in starting or stopping the service.</span></span> <span data-ttu-id="910ad-113">當錯誤對於此類別所代表的服務而言是唯一時，此屬性會設定為 [ERROR_SERVICE_SPECIFIC_ERROR]  \(1066)，此錯誤的相關資訊可見於 **ServiceSpecificExitCode** 屬性。</span><span class="sxs-lookup"><span data-stu-id="910ad-113">This property is set to **ERROR_SERVICE_SPECIFIC_ERROR** (1066) when the error is unique to the service represented by this class, and information about the error is available in the **ServiceSpecificExitCode** property.</span></span> <span data-ttu-id="910ad-114">服務執行時會將此值設定為 NO_ERROR (0)，並在正常結束後再將此值設定為 NO_ERROR (0)。</span><span class="sxs-lookup"><span data-stu-id="910ad-114">The service sets this value to NO_ERROR (0) when running, and again upon normal termination.</span></span>  
  
 <span data-ttu-id="910ad-115">**Host Name**</span><span class="sxs-lookup"><span data-stu-id="910ad-115">**Host Name**</span></span>  
 <span data-ttu-id="910ad-116">顯示執行 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 服務之電腦或叢集的名稱。</span><span class="sxs-lookup"><span data-stu-id="910ad-116">Displays the name of the computer or cluster running the [!INCLUDE[ssIS](../../includes/ssis-md.md)] service.</span></span>  
  
 <span data-ttu-id="910ad-117">**名稱**</span><span class="sxs-lookup"><span data-stu-id="910ad-117">**Name**</span></span>  
 <span data-ttu-id="910ad-118">表示服務的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="910ad-118">Indicates the display name of the service.</span></span>  
  
 <span data-ttu-id="910ad-119">**處理序識別碼**</span><span class="sxs-lookup"><span data-stu-id="910ad-119">**Process ID**</span></span>  
 <span data-ttu-id="910ad-120">顯示 Windows 處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="910ad-120">Displays the Windows process ID.</span></span>  
  
 <span data-ttu-id="910ad-121">**SQL 服務類型**</span><span class="sxs-lookup"><span data-stu-id="910ad-121">**SQL Service Type**</span></span>  
 <span data-ttu-id="910ad-122">顯示為呼叫處理序所提供的服務類型。</span><span class="sxs-lookup"><span data-stu-id="910ad-122">Displays the type of service provided to calling processes.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="910ad-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會安裝數個服務。</span><span class="sxs-lookup"><span data-stu-id="910ad-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installs several services.</span></span>  
  
 <span data-ttu-id="910ad-124">**啟動模式**</span><span class="sxs-lookup"><span data-stu-id="910ad-124">**Start Mode**</span></span>  
 <span data-ttu-id="910ad-125">將這個服務設定為下列選擇：</span><span class="sxs-lookup"><span data-stu-id="910ad-125">Set this service to the following choices:</span></span>  
  
-   <span data-ttu-id="910ad-126">手動：電腦啟動時，這項服務不會自動啟動。</span><span class="sxs-lookup"><span data-stu-id="910ad-126">Manual: This service does not automatically start when the computer starts.</span></span> <span data-ttu-id="910ad-127">您必須使用「 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員」或其他工具來啟動服務。</span><span class="sxs-lookup"><span data-stu-id="910ad-127">You must start the service using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, or some other tool.</span></span>  
  
-   <span data-ttu-id="910ad-128">自動：這部電腦啟動時，這項服務會嘗試啟動。</span><span class="sxs-lookup"><span data-stu-id="910ad-128">Automatic: This service attempts to start when this computer starts.</span></span>  
  
-   <span data-ttu-id="910ad-129">停用：這項服務無法啟動。</span><span class="sxs-lookup"><span data-stu-id="910ad-129">Disabled: This service cannot be started.</span></span>  
  
 <span data-ttu-id="910ad-130">**State**</span><span class="sxs-lookup"><span data-stu-id="910ad-130">**State**</span></span>  
 <span data-ttu-id="910ad-131">表示這項服務為執行中、已停止或已停用。</span><span class="sxs-lookup"><span data-stu-id="910ad-131">Indicates whether this service is running, stopped, or disabled.</span></span> <span data-ttu-id="910ad-132">" **...** " 表示狀態變更已暫止。</span><span class="sxs-lookup"><span data-stu-id="910ad-132">"**...**" indicates a state change is pending.</span></span>  
  
  
