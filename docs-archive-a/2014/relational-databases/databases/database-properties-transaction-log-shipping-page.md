---
title: 資料庫屬性 (交易記錄傳送頁面) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.logshipping.f1
ms.assetid: 72c4e539-fe11-4d57-b977-65b418d5916f
author: stevestein
ms.author: sstein
ms.openlocfilehash: dd36b3bc56bcd48c53871c9bc1e334d72c80ac78
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709586"
---
# <a name="database-properties-transaction-log-shipping-page"></a><span data-ttu-id="b14e7-102">資料庫屬性 (交易記錄傳送頁面)</span><span class="sxs-lookup"><span data-stu-id="b14e7-102">Database Properties (Transaction Log Shipping Page)</span></span>
  <span data-ttu-id="b14e7-103">使用此頁面即可設定和修改資料庫記錄傳送的屬性。</span><span class="sxs-lookup"><span data-stu-id="b14e7-103">Use this page to configure and modify the properties of log shipping for a database.</span></span>  
  
 <span data-ttu-id="b14e7-104">如需記錄傳送概念的說明，請參閱 [關於記錄傳送 &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="b14e7-104">For an explanation of log shipping concepts, see [About Log Shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="b14e7-105">選項。</span><span class="sxs-lookup"><span data-stu-id="b14e7-105">Options</span></span>  
 <span data-ttu-id="b14e7-106">**將此啟用為記錄傳送組態的主要資料庫**</span><span class="sxs-lookup"><span data-stu-id="b14e7-106">**Enable this as a primary database in a log shipping configuration**</span></span>  
 <span data-ttu-id="b14e7-107">啟用此資料庫為記錄傳送的主要資料庫。</span><span class="sxs-lookup"><span data-stu-id="b14e7-107">Enables this database as a log shipping primary database.</span></span> <span data-ttu-id="b14e7-108">先選取它，然後設定此頁面上的其他選項。</span><span class="sxs-lookup"><span data-stu-id="b14e7-108">Select it and then configure the remaining options on this page.</span></span> <span data-ttu-id="b14e7-109">如果您清除此核取方塊，就會卸除此資料庫的記錄傳送組態。</span><span class="sxs-lookup"><span data-stu-id="b14e7-109">If you clear this check box, the log shipping configuration will be dropped for this database.</span></span>  
  
 <span data-ttu-id="b14e7-110">**備份設定**</span><span class="sxs-lookup"><span data-stu-id="b14e7-110">**Backup Settings**</span></span>  
 <span data-ttu-id="b14e7-111">按一下 [備份設定] 即可設定備份排程、位置、警示及封存參數。</span><span class="sxs-lookup"><span data-stu-id="b14e7-111">Click **Backup Settings** to configure backup schedule, location, alert, and archiving parameters.</span></span>  
  
 <span data-ttu-id="b14e7-112">**備份排程**</span><span class="sxs-lookup"><span data-stu-id="b14e7-112">**Backup schedule**</span></span>  
 <span data-ttu-id="b14e7-113">顯示主要資料庫目前選取的備份排程。</span><span class="sxs-lookup"><span data-stu-id="b14e7-113">Shows the currently selected backup schedule for the primary database.</span></span> <span data-ttu-id="b14e7-114">按一下 **[備份設定]** 即可修改這些設定。</span><span class="sxs-lookup"><span data-stu-id="b14e7-114">Click **Backup Settings** to modify these settings.</span></span>  
  
 <span data-ttu-id="b14e7-115">**上次建立的備份**</span><span class="sxs-lookup"><span data-stu-id="b14e7-115">**Last backup created**</span></span>  
 <span data-ttu-id="b14e7-116">指出主要資料庫上次備份交易記錄的時間和日期。</span><span class="sxs-lookup"><span data-stu-id="b14e7-116">Indicates the time and date of the last transaction log backup of the primary database.</span></span>  
  
 <span data-ttu-id="b14e7-117">**次要伺服器執行個體與資料庫**</span><span class="sxs-lookup"><span data-stu-id="b14e7-117">**Secondary server instances and databases**</span></span>  
 <span data-ttu-id="b14e7-118">列出此主要資料庫目前設定的次要伺服器與資料庫。</span><span class="sxs-lookup"><span data-stu-id="b14e7-118">Lists the currently configured secondary servers and databases for this primary database.</span></span> <span data-ttu-id="b14e7-119">反白顯示資料庫，然後按一下 **[...]** 即可修改與次要資料庫相關聯的參數。</span><span class="sxs-lookup"><span data-stu-id="b14e7-119">Highlight a database, and then click **...** to modify the parameters associated with that secondary database.</span></span>  
  
 <span data-ttu-id="b14e7-120">**加入**</span><span class="sxs-lookup"><span data-stu-id="b14e7-120">**Add**</span></span>  
 <span data-ttu-id="b14e7-121">按一下 [加入]，即可將次要資料庫加入此主要資料庫的記錄傳送組態。</span><span class="sxs-lookup"><span data-stu-id="b14e7-121">Click **Add** to add a secondary database to the log shipping configuration for this primary database.</span></span>  
  
 <span data-ttu-id="b14e7-122">**移除**</span><span class="sxs-lookup"><span data-stu-id="b14e7-122">**Remove**</span></span>  
 <span data-ttu-id="b14e7-123">從這個記錄傳送組態中，移除選取的資料庫。</span><span class="sxs-lookup"><span data-stu-id="b14e7-123">Removes a selected database from this log shipping configuration.</span></span> <span data-ttu-id="b14e7-124">先選取資料庫，然後按一下 **[移除]** 。</span><span class="sxs-lookup"><span data-stu-id="b14e7-124">Select the database first and then click **Remove**.</span></span>  
  
 <span data-ttu-id="b14e7-125">**使用監視伺服器執行個體**</span><span class="sxs-lookup"><span data-stu-id="b14e7-125">**Use a monitor server instance**</span></span>  
 <span data-ttu-id="b14e7-126">設定此記錄傳送組態的監視伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="b14e7-126">Sets up a monitor server instance for this log shipping configuration.</span></span> <span data-ttu-id="b14e7-127">選取 **[使用監視伺服器執行個體]** 核取方塊，然後按一下 **[設定]** 即可指定監視伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="b14e7-127">Select the **Use a monitor server instance** check box and then click **Settings** to specify the monitor server instance.</span></span>  
  
 <span data-ttu-id="b14e7-128">**監視伺服器執行個體**</span><span class="sxs-lookup"><span data-stu-id="b14e7-128">**Monitor server instance**</span></span>  
 <span data-ttu-id="b14e7-129">指出此記錄傳送組態目前設定的監視伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="b14e7-129">Indicates the currently configured monitor server instance for this log shipping configuration.</span></span>  
  
 <span data-ttu-id="b14e7-130">**設定**</span><span class="sxs-lookup"><span data-stu-id="b14e7-130">**Settings**</span></span>  
 <span data-ttu-id="b14e7-131">設定記錄傳送組態的監視伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="b14e7-131">Configures the monitor server instance for a log shipping configuration.</span></span> <span data-ttu-id="b14e7-132">按一下 **[設定]** 即可設定此監視伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="b14e7-132">Click **Settings** to configure this monitor server instance.</span></span>  
  
 <span data-ttu-id="b14e7-133">**指令碼組態**</span><span class="sxs-lookup"><span data-stu-id="b14e7-133">**Script Configuration**</span></span>  
 <span data-ttu-id="b14e7-134">使用選取的參數，產生用來設定記錄傳送的指令碼。</span><span class="sxs-lookup"><span data-stu-id="b14e7-134">Generates a script for configuring log shipping with the parameters you have selected.</span></span> <span data-ttu-id="b14e7-135">按一下 **[指令碼組態]** ，然後選擇指令碼的輸出目的地。</span><span class="sxs-lookup"><span data-stu-id="b14e7-135">Click **Script Configuration**, and then choose an output destination for the script.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b14e7-136">您必須叫用 **[次要資料庫設定]** 對話方塊，才能編寫次要資料庫的指令碼設定。</span><span class="sxs-lookup"><span data-stu-id="b14e7-136">Before scripting settings for a secondary database, you must invoke the **Secondary Database Settings** dialog box.</span></span> <span data-ttu-id="b14e7-137">叫用此對話方塊將可連接至次要伺服器，並擷取產生指令碼所需之次要資料庫的目前設定。</span><span class="sxs-lookup"><span data-stu-id="b14e7-137">Invoking this dialog box connects you to the secondary server and retrieves the current settings of the secondary database that are needed to generate the script.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b14e7-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b14e7-138">See Also</span></span>  
 <span data-ttu-id="b14e7-139">[記錄傳送預存程序 &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/log-shipping-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b14e7-139">[Log Shipping Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/log-shipping-stored-procedures-transact-sql) </span></span>  
 [<span data-ttu-id="b14e7-140">記錄傳送資料表 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b14e7-140">Log Shipping Tables &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-tables/log-shipping-tables-transact-sql)  
  
  
