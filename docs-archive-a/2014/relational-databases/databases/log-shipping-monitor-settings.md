---
title: 記錄傳送監視器設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.logshipping.settings.monitor.f1
ms.assetid: 45e2ba7d-b3aa-4643-9451-bcb991572314
author: stevestein
ms.author: sstein
ms.openlocfilehash: 162fdc1b8b0ef850a7e58d1380c533426e16539c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709545"
---
# <a name="log-shipping-monitor-settings"></a><span data-ttu-id="04656-102">記錄傳送監視器設定</span><span class="sxs-lookup"><span data-stu-id="04656-102">Log Shipping Monitor Settings</span></span>
  <span data-ttu-id="04656-103">使用此頁面來設定和修改記錄傳送監視伺服器的屬性。</span><span class="sxs-lookup"><span data-stu-id="04656-103">Use this page to configure and to modify the properties of the log shipping monitor server.</span></span>  
  
 <span data-ttu-id="04656-104">如需記錄傳送概念的說明，請參閱 [關於記錄傳送 &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="04656-104">For an explanation of log shipping concepts, see [About Log Shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="04656-105">選項。</span><span class="sxs-lookup"><span data-stu-id="04656-105">Options</span></span>  
 <span data-ttu-id="04656-106">**監視伺服器執行個體**</span><span class="sxs-lookup"><span data-stu-id="04656-106">**Monitor server instance**</span></span>  
 <span data-ttu-id="04656-107">顯示目前設定為記錄傳送組態的監視伺服器之伺服器執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="04656-107">Displays the name of the server instance that is currently configured as the monitor server for the log shipping configuration.</span></span>  
  
 <span data-ttu-id="04656-108">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="04656-108">**Connect**</span></span>  
 <span data-ttu-id="04656-109">選擇和連接到做為監視伺服器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="04656-109">Choose and connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to be used as the monitor server.</span></span> <span data-ttu-id="04656-110">用來連接的帳戶必須是次要伺服器執行個體上的系統管理員 (sysadmin) 固定伺服器角色的成員。</span><span class="sxs-lookup"><span data-stu-id="04656-110">The account used to connect must be a member of the sysadmin fixed server role on the secondary server instance.</span></span>  
  
 <span data-ttu-id="04656-111">**藉由模擬作業的 Proxy 帳戶**</span><span class="sxs-lookup"><span data-stu-id="04656-111">**By impersonating the proxy account of the job**</span></span>  
 <span data-ttu-id="04656-112">連接到監視伺服器執行個體時，讓記錄傳送模擬 SQL Server Agent Proxy 帳戶。</span><span class="sxs-lookup"><span data-stu-id="04656-112">Have log shipping impersonate the SQL Server Agent proxy account when connecting to the monitor server instance.</span></span> <span data-ttu-id="04656-113">備份、複製與還原處理序必須能夠連接到監視伺服器，才能更新記錄傳送作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="04656-113">The backup, copy, and restore processes must be able to connect to the monitor server to update the status of log shipping operations.</span></span>  
  
 <span data-ttu-id="04656-114">**使用下列的 SQL Server 登入**</span><span class="sxs-lookup"><span data-stu-id="04656-114">**Using the following SQL Server login**</span></span>  
 <span data-ttu-id="04656-115">連接到監視伺服器執行個體時，允許記錄傳送使用特定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。</span><span class="sxs-lookup"><span data-stu-id="04656-115">Allow log shipping to use a specific [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login when connecting to the monitor server instance.</span></span> <span data-ttu-id="04656-116">備份、複製與還原處理序必須能夠連接到監視伺服器，才能更新記錄傳送作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="04656-116">The backup, copy, and restore processes must be able to connect to the monitor server to update the status of log shipping operations.</span></span> <span data-ttu-id="04656-117">如果您想要記錄傳送使用特定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入，請選擇此選項，然後指定登入與密碼。</span><span class="sxs-lookup"><span data-stu-id="04656-117">Choose this option if you want log shipping to use a specific [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and then specify the login and password.</span></span>  
  
 <span data-ttu-id="04656-118">**在此時間後刪除記錄**</span><span class="sxs-lookup"><span data-stu-id="04656-118">**Delete history after**</span></span>  
 <span data-ttu-id="04656-119">指定記錄傳送記錄資訊於刪除之前，在監視伺服器上保存的時間量。</span><span class="sxs-lookup"><span data-stu-id="04656-119">Specify the amount of time to retain log shipping history information on the monitor server before it is deleted.</span></span>  
  
 <span data-ttu-id="04656-120">**作業名稱**</span><span class="sxs-lookup"><span data-stu-id="04656-120">**Job name**</span></span>  
 <span data-ttu-id="04656-121">指出超過備份或還原臨界值時，記錄傳送用來引發警示的 SQL Server Agent 警示作業的名稱。</span><span class="sxs-lookup"><span data-stu-id="04656-121">Indicates the name of the SQL Server Agent alert job used by log shipping to raise alerts when backup or restore thresholds have been exceeded.</span></span> <span data-ttu-id="04656-122">第一次建立此作業時，您可以在方塊中輸入新的名稱。</span><span class="sxs-lookup"><span data-stu-id="04656-122">When first creating this job, you can change the name by typing in the box.</span></span>  
  
 <span data-ttu-id="04656-123">**[排程]**</span><span class="sxs-lookup"><span data-stu-id="04656-123">**Schedule**</span></span>  
 <span data-ttu-id="04656-124">指出 SQL Server Agent 警示作業的目前排程。</span><span class="sxs-lookup"><span data-stu-id="04656-124">Indicates the current schedule of the SQL Server Agent alert job.</span></span>  
  
 <span data-ttu-id="04656-125">**編輯**</span><span class="sxs-lookup"><span data-stu-id="04656-125">**Edit**</span></span>  
 <span data-ttu-id="04656-126">修改 SQL Server Agent 警示作業參數。</span><span class="sxs-lookup"><span data-stu-id="04656-126">Modify the SQL Server Agent alert job parameters.</span></span>  
  
 <span data-ttu-id="04656-127">**停用此作業**</span><span class="sxs-lookup"><span data-stu-id="04656-127">**Disable this job**</span></span>  
 <span data-ttu-id="04656-128">暫停 SQL Server Agent 警示作業。</span><span class="sxs-lookup"><span data-stu-id="04656-128">Suspend the SQL Server Agent alert job.</span></span>  
  
  
