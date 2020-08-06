---
title: Analysis Server 屬性 (服務索引標籤) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 8dbe4bc5-6aa9-48ee-857e-0b4ea764b9cb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 91200120d87224c8e7733b0ff41ed423d3086c34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708870"
---
# <a name="analysis-server-properties-service-tab"></a><span data-ttu-id="ead7d-102">Analysis Server 屬性 (服務索引標籤)</span><span class="sxs-lookup"><span data-stu-id="ead7d-102">Analysis Server Properties (Service Tab)</span></span>
  <span data-ttu-id="ead7d-103">這個服務是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ead7d-103">This service is the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="ead7d-104">必須執行此服務， [!INCLUDE[ssAS](../../includes/ssas-md.md)] 才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="ead7d-104">This service must be running for [!INCLUDE[ssAS](../../includes/ssas-md.md)] to work properly.</span></span> <span data-ttu-id="ead7d-105">淺灰色的屬性值不得以此應用程式加以變更。</span><span class="sxs-lookup"><span data-stu-id="ead7d-105">The property values in light gray cannot be changed using this application.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ead7d-106">選項。</span><span class="sxs-lookup"><span data-stu-id="ead7d-106">Options</span></span>  
 <span data-ttu-id="ead7d-107">**二進位路徑**</span><span class="sxs-lookup"><span data-stu-id="ead7d-107">**Binary Path**</span></span>  
 <span data-ttu-id="ead7d-108">顯示這個服務使用之程式檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="ead7d-108">Displays the location of the program files used by this service.</span></span>  
  
 <span data-ttu-id="ead7d-109">**錯誤控制**</span><span class="sxs-lookup"><span data-stu-id="ead7d-109">**Error Control**</span></span>  
 <span data-ttu-id="ead7d-110">1 表示 `SERVICE_ERROR_NORMAL`。</span><span class="sxs-lookup"><span data-stu-id="ead7d-110">1 indicates `SERVICE_ERROR_NORMAL`.</span></span> <span data-ttu-id="ead7d-111">如果在電腦啟動過程中，服務無法啟動，啟動程式就會記錄錯誤並顯示快顯訊息方塊，但是仍會繼續啟動作業。</span><span class="sxs-lookup"><span data-stu-id="ead7d-111">If the service fails to start during computer start up, the startup program logs the error and displays a pop-up message box but continues the startup operation.</span></span> <span data-ttu-id="ead7d-112">這項值不能被改變。</span><span class="sxs-lookup"><span data-stu-id="ead7d-112">This value cannot be changed.</span></span>  
  
 <span data-ttu-id="ead7d-113">**結束碼**</span><span class="sxs-lookup"><span data-stu-id="ead7d-113">**Exit Code**</span></span>  
 <span data-ttu-id="ead7d-114">發生錯誤時，錯誤號碼會在這個方塊中顯示。</span><span class="sxs-lookup"><span data-stu-id="ead7d-114">When an error occurs, the error number appears in this box.</span></span> <span data-ttu-id="ead7d-115">請使用這個號碼進行疑難排解，方法是在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 知識庫中搜尋該號碼，或者將號碼提供給技術支援人員。</span><span class="sxs-lookup"><span data-stu-id="ead7d-115">Use this number to troubleshoot failures by searching for the number in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base or provide the number to your technical support staff.</span></span>  
  
 <span data-ttu-id="ead7d-116">**Host Name**</span><span class="sxs-lookup"><span data-stu-id="ead7d-116">**Host Name**</span></span>  
 <span data-ttu-id="ead7d-117">顯示執行 [!INCLUDE[ssAS](../../includes/ssas-md.md)]之電腦或叢集的名稱。</span><span class="sxs-lookup"><span data-stu-id="ead7d-117">Displays the name of the computer or cluster running [!INCLUDE[ssAS](../../includes/ssas-md.md)].</span></span>  
  
 <span data-ttu-id="ead7d-118">**名稱**</span><span class="sxs-lookup"><span data-stu-id="ead7d-118">**Name**</span></span>  
 <span data-ttu-id="ead7d-119">表示服務的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="ead7d-119">Indicates the display name of the service.</span></span>  
  
 <span data-ttu-id="ead7d-120">**處理序識別碼**</span><span class="sxs-lookup"><span data-stu-id="ead7d-120">**Process ID**</span></span>  
 <span data-ttu-id="ead7d-121">顯示 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 用來追蹤此程式之處理序的編號。</span><span class="sxs-lookup"><span data-stu-id="ead7d-121">Displays the number used by [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows to keep track of this program's processes.</span></span>  
  
 <span data-ttu-id="ead7d-122">**SQL 服務類型**</span><span class="sxs-lookup"><span data-stu-id="ead7d-122">**SQL Service Type**</span></span>  
 <span data-ttu-id="ead7d-123">顯示為呼叫處理序所提供的服務類型。</span><span class="sxs-lookup"><span data-stu-id="ead7d-123">Displays the type of service provided to calling processes.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="ead7d-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會安裝數個服務。</span><span class="sxs-lookup"><span data-stu-id="ead7d-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installs several services.</span></span>  
  
 <span data-ttu-id="ead7d-125">**啟動模式**</span><span class="sxs-lookup"><span data-stu-id="ead7d-125">**Start Mode**</span></span>  
 <span data-ttu-id="ead7d-126">將這個服務設定為下列選擇：</span><span class="sxs-lookup"><span data-stu-id="ead7d-126">Set this service to the following choices:</span></span>  
  
-   <span data-ttu-id="ead7d-127">手動：電腦啟動時，這項服務不會自動啟動。</span><span class="sxs-lookup"><span data-stu-id="ead7d-127">Manual: This service does not automatically start when the computer starts.</span></span> <span data-ttu-id="ead7d-128">您必須使用「 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員」或其他工具來啟動服務。</span><span class="sxs-lookup"><span data-stu-id="ead7d-128">You must start the service using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, or some other tool.</span></span>  
  
-   <span data-ttu-id="ead7d-129">自動：這部電腦啟動時，這項服務會嘗試啟動。</span><span class="sxs-lookup"><span data-stu-id="ead7d-129">Automatic: This service attempts to start when this computer starts.</span></span>  
  
-   <span data-ttu-id="ead7d-130">停用：這項服務無法啟動。</span><span class="sxs-lookup"><span data-stu-id="ead7d-130">Disabled: This service cannot be started.</span></span>  
  
 <span data-ttu-id="ead7d-131">**State**</span><span class="sxs-lookup"><span data-stu-id="ead7d-131">**State**</span></span>  
 <span data-ttu-id="ead7d-132">表示這項服務為執行中、已停止或已停用。</span><span class="sxs-lookup"><span data-stu-id="ead7d-132">Indicates whether this service is running, stopped, or disabled.</span></span>  
  
  
