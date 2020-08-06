---
title: 報表伺服器屬性 (服務索引標籤) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 2a2e1dbf-02b9-4893-aaf0-c0e4a2c9b4f9
author: stevestein
ms.author: sstein
ms.openlocfilehash: a8d223234e5f53eb087650d0634eb09b520cd21e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597468"
---
# <a name="report-server-properties-service-tab"></a><span data-ttu-id="6668c-102">Report Server 屬性 (服務索引標籤)</span><span class="sxs-lookup"><span data-stu-id="6668c-102">Report Server Properties (Service Tab)</span></span>
  <span data-ttu-id="6668c-103">此服務為 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Report Server 服務。</span><span class="sxs-lookup"><span data-stu-id="6668c-103">This service is the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Report Server service.</span></span> <span data-ttu-id="6668c-104">淺灰色的屬性值不得以此應用程式加以變更。</span><span class="sxs-lookup"><span data-stu-id="6668c-104">The property values in light gray cannot be changed by using this application.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6668c-105">選項。</span><span class="sxs-lookup"><span data-stu-id="6668c-105">Options</span></span>  
 <span data-ttu-id="6668c-106">**二進位路徑**</span><span class="sxs-lookup"><span data-stu-id="6668c-106">**Binary Path**</span></span>  
 <span data-ttu-id="6668c-107">顯示這個服務使用之程式檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="6668c-107">Displays the location of the program files used by this service.</span></span>  
  
 <span data-ttu-id="6668c-108">**錯誤控制**</span><span class="sxs-lookup"><span data-stu-id="6668c-108">**Error Control**</span></span>  
 <span data-ttu-id="6668c-109">1 指出 "SERVICE_ERROR_NORMAL"。</span><span class="sxs-lookup"><span data-stu-id="6668c-109">1 indicates "SERVICE_ERROR_NORMAL".</span></span> <span data-ttu-id="6668c-110">如果在電腦啟動過程中，服務無法啟動，啟動程式就會記錄錯誤並顯示快顯訊息方塊，但是仍會繼續啟動作業。</span><span class="sxs-lookup"><span data-stu-id="6668c-110">If the service fails to start during computer start up, the startup program logs the error and displays a pop-up message box but continues the startup operation.</span></span> <span data-ttu-id="6668c-111">這項值不能被改變。</span><span class="sxs-lookup"><span data-stu-id="6668c-111">This value cannot be changed.</span></span>  
  
 <span data-ttu-id="6668c-112">**結束碼**</span><span class="sxs-lookup"><span data-stu-id="6668c-112">**Exit Code**</span></span>  
 <span data-ttu-id="6668c-113">發生錯誤時，錯誤號碼會在這個方塊中顯示。</span><span class="sxs-lookup"><span data-stu-id="6668c-113">When an error occurs, the error number appears in this box.</span></span> <span data-ttu-id="6668c-114">請使用這個號碼進行疑難排解，方法是在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 知識庫中搜尋該號碼，或者將號碼提供給技術支援人員。</span><span class="sxs-lookup"><span data-stu-id="6668c-114">Use this number to troubleshoot failures by searching for the number in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base or provide the number to your technical support staff.</span></span>  
  
 <span data-ttu-id="6668c-115">**Host Name**</span><span class="sxs-lookup"><span data-stu-id="6668c-115">**Host Name**</span></span>  
 <span data-ttu-id="6668c-116">顯示執行全文檢索搜尋之電腦或叢集的名稱。</span><span class="sxs-lookup"><span data-stu-id="6668c-116">Displays the name of the computer or cluster running the full text search.</span></span>  
  
 <span data-ttu-id="6668c-117">**名稱**</span><span class="sxs-lookup"><span data-stu-id="6668c-117">**Name**</span></span>  
 <span data-ttu-id="6668c-118">表示服務的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="6668c-118">Indicates the display name of the service.</span></span>  
  
 <span data-ttu-id="6668c-119">**處理序識別碼**</span><span class="sxs-lookup"><span data-stu-id="6668c-119">**Process ID**</span></span>  
 <span data-ttu-id="6668c-120">顯示 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="6668c-120">Displays the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows process ID.</span></span>  
  
 <span data-ttu-id="6668c-121">**SQL 服務類型**</span><span class="sxs-lookup"><span data-stu-id="6668c-121">**SQL Service Type**</span></span>  
 <span data-ttu-id="6668c-122">為呼叫處理序所提供的服務類型。</span><span class="sxs-lookup"><span data-stu-id="6668c-122">Type of service provided to calling processes.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6668c-123">會安裝數個服務。</span><span class="sxs-lookup"><span data-stu-id="6668c-123">installs several services.</span></span>  
  
 <span data-ttu-id="6668c-124">**啟動模式**</span><span class="sxs-lookup"><span data-stu-id="6668c-124">**Start Mode**</span></span>  
 <span data-ttu-id="6668c-125">將這個服務設定為下列選擇：</span><span class="sxs-lookup"><span data-stu-id="6668c-125">Set this service to the following choices:</span></span>  
  
-   <span data-ttu-id="6668c-126">手動：電腦啟動時，這項服務不會自動啟動。</span><span class="sxs-lookup"><span data-stu-id="6668c-126">Manual: This service does not automatically start when the computer starts.</span></span> <span data-ttu-id="6668c-127">您必須使用「 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 組態管理員」或其他工具來啟動服務。</span><span class="sxs-lookup"><span data-stu-id="6668c-127">You must start the service using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, or some other tool.</span></span>  
  
-   <span data-ttu-id="6668c-128">自動：這部電腦啟動時，這項服務會嘗試啟動。</span><span class="sxs-lookup"><span data-stu-id="6668c-128">Automatic: This service attempts to start when this computer starts.</span></span>  
  
-   <span data-ttu-id="6668c-129">停用：這項服務無法啟動。</span><span class="sxs-lookup"><span data-stu-id="6668c-129">Disabled: This service cannot be started.</span></span>  
  
 <span data-ttu-id="6668c-130">**State**</span><span class="sxs-lookup"><span data-stu-id="6668c-130">**State**</span></span>  
 <span data-ttu-id="6668c-131">表示這項服務為執行中、已停止或已停用。</span><span class="sxs-lookup"><span data-stu-id="6668c-131">Indicates whether this service is running, stopped, or disabled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6668c-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6668c-132">See Also</span></span>  
 [<span data-ttu-id="6668c-133">SQL Server 服務</span><span class="sxs-lookup"><span data-stu-id="6668c-133">SQL Server Services</span></span>](../../../2014/tools/configuration-manager/sql-server-services.md)  
  
  
