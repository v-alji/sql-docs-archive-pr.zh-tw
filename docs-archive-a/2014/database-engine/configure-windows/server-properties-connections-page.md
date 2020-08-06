---
title: 伺服器屬性 (連接頁面) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverproperties.connections.f1
ms.assetid: 33be8ac5-12dd-4b8a-99e0-68261c219dd2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 80943bc542209fd34cf83e8db7aa76becd04194a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706714"
---
# <a name="server-properties-connections-page"></a><span data-ttu-id="7818f-102">伺服器屬性 (連接頁面)</span><span class="sxs-lookup"><span data-stu-id="7818f-102">Server Properties (Connections Page)</span></span>
  <span data-ttu-id="7818f-103">使用此頁面來檢視或修改您的連接選項。</span><span class="sxs-lookup"><span data-stu-id="7818f-103">Use this page to view or modify your connection options.</span></span>  
  
## <a name="connections"></a><span data-ttu-id="7818f-104">連接</span><span class="sxs-lookup"><span data-stu-id="7818f-104">Connections</span></span>  
 <span data-ttu-id="7818f-105">**並行連接的最大數目 (0 = 無限制)**</span><span class="sxs-lookup"><span data-stu-id="7818f-105">**Maximum number of concurrent connections (0 = unlimited)**</span></span>  
 <span data-ttu-id="7818f-106">如果設定為零以外的值，則會限制 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 允許的連接數目。</span><span class="sxs-lookup"><span data-stu-id="7818f-106">If set to a value other than zero, limits the number of connections that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will allow.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="7818f-107">設定為較小的值，例如 1 或 2，可防止管理員連接管理伺服器；不過，專用管理連接仍可以隨時連接。</span><span class="sxs-lookup"><span data-stu-id="7818f-107">Setting this to a small value, such as 1 or 2, can prevent administrators from connecting to administer the server; however, the Dedicated Admin Connection can always connect.</span></span>  
  
## <a name="default-connection-options"></a><span data-ttu-id="7818f-108">預設連接選項</span><span class="sxs-lookup"><span data-stu-id="7818f-108">Default Connection Options</span></span>  
 <span data-ttu-id="7818f-109">**Default connection options**</span><span class="sxs-lookup"><span data-stu-id="7818f-109">**Default connection options**</span></span>  
 <span data-ttu-id="7818f-110">指定預設連接選項，如下表中所述。</span><span class="sxs-lookup"><span data-stu-id="7818f-110">Specifies the default connection options, as described in the following table.</span></span>  
  
|<span data-ttu-id="7818f-111">組態選項</span><span class="sxs-lookup"><span data-stu-id="7818f-111">Configuration option</span></span>|<span data-ttu-id="7818f-112">描述</span><span class="sxs-lookup"><span data-stu-id="7818f-112">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="7818f-113">**停用延遲條件約束檢查**</span><span class="sxs-lookup"><span data-stu-id="7818f-113">**disable deferred constraint checking**</span></span>|<span data-ttu-id="7818f-114">控制暫時的或延遲的條件約束檢查。</span><span class="sxs-lookup"><span data-stu-id="7818f-114">Controls interim or deferred constraint checking.</span></span>|  
|<span data-ttu-id="7818f-115">**隱含交易**</span><span class="sxs-lookup"><span data-stu-id="7818f-115">**implicit transactions**</span></span>|<span data-ttu-id="7818f-116">控制陳述式執行時是否隱含地啟動交易。</span><span class="sxs-lookup"><span data-stu-id="7818f-116">Controls whether a transaction is started implicitly when a statement is run.</span></span>|  
|<span data-ttu-id="7818f-117">**資料指標在認可時關閉**</span><span class="sxs-lookup"><span data-stu-id="7818f-117">**cursor close on commit**</span></span>|<span data-ttu-id="7818f-118">控制執行認可作業後資料指標的行為。</span><span class="sxs-lookup"><span data-stu-id="7818f-118">Controls behavior of cursors after a commit operation has been performed.</span></span>|  
|<span data-ttu-id="7818f-119">**Ansi 警告**</span><span class="sxs-lookup"><span data-stu-id="7818f-119">**ansi warnings**</span></span>|<span data-ttu-id="7818f-120">控制彙總警告中的截斷與 NULL。</span><span class="sxs-lookup"><span data-stu-id="7818f-120">Controls truncation and NULL in aggregate warnings.</span></span>|  
|<span data-ttu-id="7818f-121">**Ansi 填補**</span><span class="sxs-lookup"><span data-stu-id="7818f-121">**ansi padding**</span></span>|<span data-ttu-id="7818f-122">控制固定長度變數的填補。</span><span class="sxs-lookup"><span data-stu-id="7818f-122">Controls padding of fixed-length variables.</span></span>|  
|<span data-ttu-id="7818f-123">**Ansi Nulls**</span><span class="sxs-lookup"><span data-stu-id="7818f-123">**ansi nulls**</span></span>|<span data-ttu-id="7818f-124">控制使用相等運算子時 `NULL` 的處理方式。</span><span class="sxs-lookup"><span data-stu-id="7818f-124">Controls `NULL` handling when using equality operators.</span></span>|  
|<span data-ttu-id="7818f-125">**算術中止**</span><span class="sxs-lookup"><span data-stu-id="7818f-125">**arithmetic abort**</span></span>|<span data-ttu-id="7818f-126">查詢執行過程中發生溢位或除以零的錯誤時終止查詢。</span><span class="sxs-lookup"><span data-stu-id="7818f-126">Terminates a query when an overflow or divide-by-zero error occurs during query execution.</span></span>|  
|<span data-ttu-id="7818f-127">**算術忽略**</span><span class="sxs-lookup"><span data-stu-id="7818f-127">**arithmetic ignore**</span></span>|<span data-ttu-id="7818f-128">查詢過程中發生溢位或除以零的錯誤時傳回 NULL。</span><span class="sxs-lookup"><span data-stu-id="7818f-128">Returns NULL when an overflow or divide-by-zero error occurs during a query.</span></span>|  
|<span data-ttu-id="7818f-129">**引號識別碼**</span><span class="sxs-lookup"><span data-stu-id="7818f-129">**quoted identifier**</span></span>|<span data-ttu-id="7818f-130">評估運算式時區別單引號與雙引號。</span><span class="sxs-lookup"><span data-stu-id="7818f-130">Differentiates between single and double quotation marks when evaluating an expression.</span></span>|  
|<span data-ttu-id="7818f-131">**無計數**</span><span class="sxs-lookup"><span data-stu-id="7818f-131">**no count**</span></span>|<span data-ttu-id="7818f-132">關閉每個陳述式結束時傳回的訊息，這些訊息會說明有多少資料列受到影響。</span><span class="sxs-lookup"><span data-stu-id="7818f-132">Turns off the message returned at the end of each statement that states how many rows were affected.</span></span>|  
|<span data-ttu-id="7818f-133">**Ansi Null 預設開啟**</span><span class="sxs-lookup"><span data-stu-id="7818f-133">**ansi null default on**</span></span>|<span data-ttu-id="7818f-134">更改工作階段的行為，使 Null 屬性與 ANSI 相容。</span><span class="sxs-lookup"><span data-stu-id="7818f-134">Alters the session's behavior to use ANSI compatibility for nullability.</span></span> <span data-ttu-id="7818f-135">新定義的資料行若未明確定義 Null 屬性，就允許 Null。</span><span class="sxs-lookup"><span data-stu-id="7818f-135">New columns defined without explicit nullability are defined to allow nulls.</span></span>|  
|<span data-ttu-id="7818f-136">**Ansi Null 預設關閉**</span><span class="sxs-lookup"><span data-stu-id="7818f-136">**ansi null default off**</span></span>|<span data-ttu-id="7818f-137">更改工作階段的行為，使 Null 屬性與 ANSI 不相容。</span><span class="sxs-lookup"><span data-stu-id="7818f-137">Alters the session's behavior not to use ANSI compatibility for nullability.</span></span> <span data-ttu-id="7818f-138">新定義的資料行若未明確定義 Null 屬性，就不允許 Null。</span><span class="sxs-lookup"><span data-stu-id="7818f-138">New columns defined without explicit nullability are defined not to allow nulls.</span></span>|  
|<span data-ttu-id="7818f-139">**串連 Null 產生 Null**</span><span class="sxs-lookup"><span data-stu-id="7818f-139">**concat null yields null**</span></span>|<span data-ttu-id="7818f-140">將字串與 NULL 值串連時傳回 NULL。</span><span class="sxs-lookup"><span data-stu-id="7818f-140">Returns NULL when concatenating a NULL value with a string.</span></span>|  
|<span data-ttu-id="7818f-141">**數值捨入中止**</span><span class="sxs-lookup"><span data-stu-id="7818f-141">**numeric round abort**</span></span>|<span data-ttu-id="7818f-142">運算式中發生失去有效位數時產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="7818f-142">Generates an error when a loss of precision occurs in an expression.</span></span>|  
|<span data-ttu-id="7818f-143">**xact 中止**</span><span class="sxs-lookup"><span data-stu-id="7818f-143">**xact abort**</span></span>|<span data-ttu-id="7818f-144">如果 Transact- SQL 陳述式引發執行階段錯誤，就回復交易。</span><span class="sxs-lookup"><span data-stu-id="7818f-144">Rolls back a transaction if a Transact-SQL statement raises a run-time error.</span></span>|  
  
 <span data-ttu-id="7818f-145">如需連接選項的詳細資訊，請搜尋線上叢書的特定選項。</span><span class="sxs-lookup"><span data-stu-id="7818f-145">For more information on connection options, search Books Online for the specific option.</span></span>  
  
## <a name="remote-server-connections"></a><span data-ttu-id="7818f-146">遠端伺服器連接</span><span class="sxs-lookup"><span data-stu-id="7818f-146">Remote Server Connections</span></span>  
 <span data-ttu-id="7818f-147">**允許此伺服器的遠端連接**</span><span class="sxs-lookup"><span data-stu-id="7818f-147">**Allow remote connections to this server**</span></span>  
 <span data-ttu-id="7818f-148">從遠端伺服器執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的執行個體，控制預存程序的執行。</span><span class="sxs-lookup"><span data-stu-id="7818f-148">Controls the execution of stored procedures from remote servers running instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7818f-149">選取這個核取方塊的效果與將 **sp_configureremote access** 選項設為 1 相同。</span><span class="sxs-lookup"><span data-stu-id="7818f-149">Selecting this check box has the same effect as setting the **sp_configureremote access** option to 1.</span></span> <span data-ttu-id="7818f-150">清除該核取方塊可避免從遠端伺服器執行預存程序。</span><span class="sxs-lookup"><span data-stu-id="7818f-150">Clearing it prevents execution of stored procedures from a remote server.</span></span>  
  
 <span data-ttu-id="7818f-151">**遠端查詢逾時 (以秒為單位，0 = 不會逾時)**</span><span class="sxs-lookup"><span data-stu-id="7818f-151">**Remote query timeout (in seconds, 0 = no timeout)**</span></span>  
 <span data-ttu-id="7818f-152">指定在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 逾時之前，遠端作業可以執行多久 (以秒為單位)。預設值是 600 秒，也就是允許等候十分鐘。</span><span class="sxs-lookup"><span data-stu-id="7818f-152">Specifies how long (in seconds) a remote operation may take before [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] times out. The default is 600 seconds, or a 10-minute wait.</span></span>  
  
 <span data-ttu-id="7818f-153">**需要伺服器對伺服器通訊的分散式交易**</span><span class="sxs-lookup"><span data-stu-id="7818f-153">**Require distributed transactions for server-to-server communication**</span></span>  
 <span data-ttu-id="7818f-154">透過 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散式交易協調器 (MS DTC) 交易，保護伺服器對伺服器程序的動作。</span><span class="sxs-lookup"><span data-stu-id="7818f-154">Protects the actions of a server-to-server procedure through a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) transaction.</span></span> <span data-ttu-id="7818f-155">如需詳細資訊，請參閱 [設定 remote proc trans 伺服器組態選項](configure-the-remote-proc-trans-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="7818f-155">For more information, see [Configure the remote proc trans Server Configuration Option](configure-the-remote-proc-trans-server-configuration-option.md).</span></span>  
  
## <a name="property-page-display-options"></a><span data-ttu-id="7818f-156">屬性頁面顯示選項</span><span class="sxs-lookup"><span data-stu-id="7818f-156">Property Page Display Options</span></span>  
 <span data-ttu-id="7818f-157">**設定的值**</span><span class="sxs-lookup"><span data-stu-id="7818f-157">**Configured Values**</span></span>  
 <span data-ttu-id="7818f-158">針對此窗格中的選項，顯示設定的值。</span><span class="sxs-lookup"><span data-stu-id="7818f-158">Displays the configured values for the options on this pane.</span></span> <span data-ttu-id="7818f-159">如果您變更這些值，請按一下 **[執行中的值]** ，即可查看變更是否已生效。</span><span class="sxs-lookup"><span data-stu-id="7818f-159">If you change these values, click **Running Values** to see whether the changes have taken effect.</span></span> <span data-ttu-id="7818f-160">如果沒有的話，就必須先重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7818f-160">If they have not, the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be restarted first.</span></span>  
  
 <span data-ttu-id="7818f-161">**[執行中的值]**</span><span class="sxs-lookup"><span data-stu-id="7818f-161">**Running Values**</span></span>  
 <span data-ttu-id="7818f-162">針對此窗格中的選項，檢視目前執行中的值。</span><span class="sxs-lookup"><span data-stu-id="7818f-162">View the currently running values for the options on this pane.</span></span> <span data-ttu-id="7818f-163">這些值是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="7818f-163">These values are read-only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7818f-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7818f-164">See Also</span></span>  
 <span data-ttu-id="7818f-165">[&#40;查詢執行的選項： SQL Server： Advanced Page&#41;](../options-query-execution-sql-server-advanced-page.md) </span><span class="sxs-lookup"><span data-stu-id="7818f-165">[Options &#40;Query Execution:SQL Server:Advanced Page&#41;](../options-query-execution-sql-server-advanced-page.md) </span></span>  
 [<span data-ttu-id="7818f-166">伺服器組態選項 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7818f-166">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
