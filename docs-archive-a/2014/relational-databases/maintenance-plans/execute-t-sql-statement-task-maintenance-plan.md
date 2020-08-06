---
title: 執行 T-SQL 陳述式工作 (維護計畫) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.tsql.f1
helpviewer_keywords:
- Execute T-SQL Statement Task dialog box
ms.assetid: fef3e259-0c47-4f6e-ade0-aee95e3d6c1a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 63738758ce228a51ab6c75eb11a681eec3b27352
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598357"
---
# <a name="execute-t-sql-statement-task-maintenance-plan"></a><span data-ttu-id="0420f-102">執行 T-SQL 陳述式工作 (維護計畫)</span><span class="sxs-lookup"><span data-stu-id="0420f-102">Execute T-SQL Statement Task (Maintenance Plan)</span></span>
  <span data-ttu-id="0420f-103">使用 [執行 T-SQL 陳述式工作]  對話方塊，即可將您選擇的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式加入此維護計畫，來自訂維護計畫。</span><span class="sxs-lookup"><span data-stu-id="0420f-103">Use the **Execute T-SQL Statement Task** dialog to customize your maintenance plan by adding [!INCLUDE[tsql](../../includes/tsql-md.md)] statements of your choice to this maintenance plan.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0420f-104">選項。</span><span class="sxs-lookup"><span data-stu-id="0420f-104">Options</span></span>  
 <span data-ttu-id="0420f-105">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="0420f-105">**Connection**</span></span>  
 <span data-ttu-id="0420f-106">選取執行此工作時要使用的伺服器連接。</span><span class="sxs-lookup"><span data-stu-id="0420f-106">Select the server connection to use when performing this task.</span></span>  
  
 <span data-ttu-id="0420f-107">**新增**</span><span class="sxs-lookup"><span data-stu-id="0420f-107">**New**</span></span>  
 <span data-ttu-id="0420f-108">建立新的伺服器連接，以便執行此工作時使用。</span><span class="sxs-lookup"><span data-stu-id="0420f-108">Create a new server connection to use when performing this task.</span></span> <span data-ttu-id="0420f-109">下面會描述 **[新增連接]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0420f-109">The **New Connection** dialog box is described below.</span></span>  
  
 <span data-ttu-id="0420f-110">**執行逾時**</span><span class="sxs-lookup"><span data-stu-id="0420f-110">**Execution time out**</span></span>  
 <span data-ttu-id="0420f-111">在逾時之前，等候工作完成的時間 (秒數) (結束工作)。</span><span class="sxs-lookup"><span data-stu-id="0420f-111">Time (seconds) to wait for task completion before timing out (terminating task).</span></span>  
  
 <span data-ttu-id="0420f-112">**T-SQL 陳述式**</span><span class="sxs-lookup"><span data-stu-id="0420f-112">**T-SQL statement**</span></span>  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="0420f-113">要執行的陳述式。</span><span class="sxs-lookup"><span data-stu-id="0420f-113">statements to execute.</span></span>  
  
 <span data-ttu-id="0420f-114">**檢視 T-SQL**</span><span class="sxs-lookup"><span data-stu-id="0420f-114">**View T-SQL**</span></span>  
 <span data-ttu-id="0420f-115">根據選取的選項，檢視此工作在伺服器上執行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="0420f-115">View the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements performed against the server for this task, based on the selected options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0420f-116">受影響的物件數目較為大量時，會多花一些時間才會顯示。</span><span class="sxs-lookup"><span data-stu-id="0420f-116">When the number of objects affected is large, this display can take a considerable amount of time.</span></span>  
  
## <a name="new-connection-dialog-box"></a><span data-ttu-id="0420f-117">新增連接對話方塊</span><span class="sxs-lookup"><span data-stu-id="0420f-117">New Connection Dialog Box</span></span>  
 <span data-ttu-id="0420f-118">**連線名稱**</span><span class="sxs-lookup"><span data-stu-id="0420f-118">**Connection name**</span></span>  
 <span data-ttu-id="0420f-119">輸入新連接的名稱。</span><span class="sxs-lookup"><span data-stu-id="0420f-119">Enter a name for the new connection.</span></span>  
  
 <span data-ttu-id="0420f-120">**選取或輸入伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="0420f-120">**Select or enter a server name**</span></span>  
 <span data-ttu-id="0420f-121">選取執行此工作時要連接的伺服器。</span><span class="sxs-lookup"><span data-stu-id="0420f-121">Select a server to connect to when performing this task.</span></span>  
  
 <span data-ttu-id="0420f-122">**[重新整理]**</span><span class="sxs-lookup"><span data-stu-id="0420f-122">**Refresh**</span></span>  
 <span data-ttu-id="0420f-123">重新整理可用的伺服器清單。</span><span class="sxs-lookup"><span data-stu-id="0420f-123">Refresh the list of available servers.</span></span>  
  
 <span data-ttu-id="0420f-124">**輸入要登入到伺服器的資訊**</span><span class="sxs-lookup"><span data-stu-id="0420f-124">**Enter information to log on to the server**</span></span>  
 <span data-ttu-id="0420f-125">指定如何對伺服器進行驗證。</span><span class="sxs-lookup"><span data-stu-id="0420f-125">Specify how to authenticate against the server.</span></span>  
  
 <span data-ttu-id="0420f-126">**使用 Windows 整合式安全性**</span><span class="sxs-lookup"><span data-stu-id="0420f-126">**Use Windows integrated security**</span></span>  
 <span data-ttu-id="0420f-127">使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 驗證連線到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0420f-127">Connect to an instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] with [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Authentication.</span></span>  
  
 <span data-ttu-id="0420f-128">**使用特定的使用者名稱和密碼**</span><span class="sxs-lookup"><span data-stu-id="0420f-128">**Use a specific user name and password**</span></span>  
 <span data-ttu-id="0420f-129">使用 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 驗證，連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0420f-129">Connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="0420f-130">無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="0420f-130">This option is not available.</span></span>  
  
 <span data-ttu-id="0420f-131">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="0420f-131">**User name**</span></span>  
 <span data-ttu-id="0420f-132">提供驗證時要使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。</span><span class="sxs-lookup"><span data-stu-id="0420f-132">Provide a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login to use when authenticating.</span></span> <span data-ttu-id="0420f-133">無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="0420f-133">This option is not available.</span></span>  
  
 <span data-ttu-id="0420f-134">**密碼**</span><span class="sxs-lookup"><span data-stu-id="0420f-134">**Password**</span></span>  
 <span data-ttu-id="0420f-135">提供驗證時要使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="0420f-135">Provide a password to use when authenticating.</span></span> <span data-ttu-id="0420f-136">無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="0420f-136">This option is not available.</span></span>  
  
  
